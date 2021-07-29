소개
지금까지는 BoxGeometry 클래스 만 사용하여 큐브를 만들었습니다. 이 단원에서 우리는 다양한 기하학을 발견할 것이지만, 먼저 기하학이 실제로 무엇인지 이해해야 합니다.

기하학이란 무엇입니까?
Three.js에서 기하학은 정점(3D 공간의 점 좌표)과 면(표면을 만들기 위해 정점을 결합하는 삼각형)으로 구성됩니다.

우리는 기하학을 사용하여 메쉬를 만들지만, 기하학을 사용하여 입자를 형성할 수도 있습니다. 각 꼭짓점(꼭짓점의 단수)은 입자에 해당하지만 이는 향후 학습을 위한 것입니다.

정점의 위치보다 더 많은 데이터를 저장할 수 있습니다. 좋은 예는 UV 좌표 또는 법선에 대해 이야기하는 것입니다. 보시다시피 나중에 이에 대해 자세히 알아보겠습니다.

다양한 내장 지오메트리
Three.js에는 많은 내장 지오메트리가 있습니다. 각각을 인스턴스화하는 방법을 정확하게 알 필요는 없지만 존재한다는 것을 아는 것이 좋습니다.

우리가 보게 될 모든 내장 기하 도형은 BufferGeometry 클래스 에서 상속됩니다 . 이 클래스는 같은 방법으로 많은 구축하고 translate(...), rotateX(...), normalize(), 등 그러나 우리는이 강의에서 사용하지 않을 수 있습니다.

대부분의 기하학 문서 페이지에는 예제가 있습니다.

BoxGeometry 상자를 생성합니다.
PlaneGeometry 직사각형 평면을 생성합니다.
CircleGeometry 원형 차트와 같은 디스크 또는 디스크의 일부를 생성합니다.
ConeGeometry 원뿔 또는 원뿔의 일부를 생성합니다. 콘의 베이스를 열거나 닫을 수 있습니다.
CylinderGeometry 실린더 를 생성합니다. 원통의 끝을 열거나 닫을 수 있으며 각 끝의 반지름을 변경할 수 있습니다.
RingGeometry 평평한 링 또는 평평한 원의 일부를 생성합니다.
TorusGeometry 두께가 있는 링(도넛과 같은) 또는 링의 일부를 생성합니다.
TorusKnotGeometry 일종의 매듭 형상을 생성합니다.
DodecahedronGeometry 12면 구를 생성합니다. 둥근 구에 대한 세부 정보를 추가할 수 있습니다.
OctahedronGeometry 8면 구를 생성합니다. 둥근 구에 대한 세부 정보를 추가할 수 있습니다.
TetrahedronGeometry 4면 구를 생성합니다(세부 사항을 늘리지 않으면 구형이 아닙니다). 둥근 구에 대한 세부 정보를 추가할 수 있습니다.
IcosahedronGeometry 크기가 거의 같은 삼각형으로 구성된 구를 만듭니다.
SphereGeometry 면이 사각형처럼 보이는 가장 인기 있는 유형의 구를 만듭니다(쿼드는 두 삼각형의 조합일 뿐입니다).
ShapeGeometry 경로를 기반으로 모양을 만듭니다.
TubeGeometry 경로를 따라 튜브를 생성합니다.
ExtrudeGeometry 경로를 기반으로 돌출을 생성합니다. 경사를 추가하고 제어할 수 있습니다.
LatheGeometry 꽃병 또는 꽃병의 일부를 만들기 위해(더 많은 회전과 유사함).
TextGeometry 3D 텍스트를 생성합니다. 서체 json 형식으로 글꼴을 제공해야 합니다.
Three.js에서 지원하지 않는 특정 지오메트리가 필요한 경우 JavaScript에서 고유한 지오메트리를 만들거나 3D 소프트웨어에서 만들고 내보내고 프로젝트로 가져올 수 있습니다. 우리는 나중에 그것에 대해 더 배울 것입니다.

상자 예
우리는 이미 큐브를 만들었지만 매개변수에 대해 많이 이야기하지 않았습니다. 대부분의 기하 도형에는 매개변수가 있으며 사용하기 전에 항상 설명서를 살펴보아야 합니다.

BoxGeometry는 6 개 매개 변수가 있습니다 :

width: x축의 크기
height: y축의 크기
depth: z축의 크기
widthSegments: x축의 세분화 수
heightSegments: y축의 세분화 수
depthSegments: z축의 세분화 수
세분화는 면을 구성해야 하는 삼각형의 양에 해당합니다. 기본적으로 1면당 2개의 삼각형만 있음을 의미합니다. 세분화를 로 설정하면 2면당 8개의 삼각형이 생깁니다.

const geometry = new THREE.BoxGeometry(1, 1, 1, 2, 2, 2)
자바스크립트
문제는 이러한 삼각형을 볼 수 없다는 것입니다.

좋은 해결책은 wireframe: true자료 에 추가 하는 것입니다. 와이어프레임은 각 삼각형을 구분하는 선을 표시합니다.

const material = new THREE.MeshBasicMaterial({ color: 0xff0000, wireframe: true })
자바스크립트

보시다시피 면에 8개의 삼각형이 있습니다.

이것은 평면 큐브와 관련이 없지만 SphereGeometry를 사용할 때 더 흥미로워 집니다 .

const geometry = new THREE.SphereGeometry(1, 32, 32)
자바스크립트

더 많은 세분화를 추가할수록 얼굴을 구분할 수 없습니다. 그러나 정점과 면이 너무 많으면 성능에 영향을 미칩니다.

나만의 버퍼 지오메트리 생성
때때로 우리는 우리 자신의 지오메트리를 생성해야 합니다. 지오메트리가 매우 복잡하거나 정확한 모양을 가진 경우 3D 소프트웨어에서 생성하는 것이 더 좋지만(이에 대해서는 향후 강의에서 다룰 예정입니다), 지오메트리가 너무 복잡하지 않은 경우 다음을 사용하여 직접 만들 수 있습니다. 버퍼 지오메트리 .

고유한 버퍼 지오메트리를 만들려면 먼저 빈 BufferGeometry 를 인스턴스화합니다 . 우리는 간단한 삼각형을 만들 것입니다:

// Create an empty BufferGeometry
const geometry = new THREE.BufferGeometry()
자바스크립트
BufferGeometry 에 정점을 추가하려면 Float32Array로 시작해야 합니다 .

Float32Array 는 기본 JavaScript 유형 배열입니다. 내부에는 float만 저장할 수 있으며 해당 배열의 길이는 고정되어 있습니다.

Float32Array 를 생성하려면 길이를 지정한 다음 나중에 채울 수 있습니다.

const positionsArray = new Float32Array(9)

// First vertice
positionsArray[0] = 0
positionsArray[1] = 0
positionsArray[2] = 0

// Second vertice
positionsArray[3] = 0
positionsArray[4] = 1
positionsArray[5] = 0

// Third vertice
positionsArray[6] = 1
positionsArray[7] = 0
positionsArray[8] = 0
자바스크립트
또는 배열을 전달할 수 있습니다.

const positionsArray = new Float32Array([
0, 0, 0, // First vertex
0, 1, 0, // Second vertex
1, 0, 0 // Third vertex
])
자바스크립트
보시다시피 정점의 좌표는 선형으로 지정됩니다. 이 배열은 사용자가 지정을 1 차원 배열이며 x, y및 z에 의해 따르는 제 정점의 x, y및 z상기 제 정점 등.

해당 배열을 BufferGeometry로 보내기 전에 BufferAttribute 로 변환해야 합니다 .

첫 번째 매개변수는 입력된 배열에 해당하고 두 번째 매개변수는 하나의 정점 속성을 만드는 값의 양에 해당합니다. 앞에서 보았듯이 이 배열을 읽으려면 정점 위치가 3개의 값( x, y및 z) 으로 구성되어 있기 때문에 3 x 3으로 이동해야 합니다 .

const positionsAttribute = new THREE.BufferAttribute(positionsArray, 3)
자바스크립트
그런 다음 메서드를 사용하여 이 속성을 BufferGeometry에 추가할 수 있습니다 setAttribute(...). 첫 번째 매개변수는 이 속성의 이름이고 두 번째 매개변수는 값입니다.

geometry.setAttribute('position', positionsAttribute)
자바스크립트
'position'Three.js 내부 셰이더가 정점을 배치하기 위해 해당 값을 찾을 것이기 때문에 이름으로 선택했습니다 . 우리는 쉐이더 수업에서 이에 대해 더 많이 볼 것입니다.

정점의 순서에 따라 면이 자동으로 생성됩니다.

모두 함께:

// Create an empty BufferGeometry
const geometry = new THREE.BufferGeometry()

// Create a Float32Array containing the vertices position (3 by 3)
const positionsArray = new Float32Array([
0, 0, 0, // First vertex
0, 1, 0, // Second vertex
1, 0, 0 // Third vertex
])

// Create the attribute and name it 'position'
const positionsAttribute = new THREE.BufferAttribute(positionsArray, 3)
geometry.setAttribute('position', positionsAttribute)
자바스크립트

우리는 또한 여러 개의 무작위 삼각형을 만들 수 있습니다.

// Create an empty BufferGeometry
const geometry = new THREE.BufferGeometry()

// Create 50 triangles (450 values)
const count = 50
const positionsArray = new Float32Array(count _ 3 _ 3)
for(let i = 0; i < count _ 3 _ 3; i++)
{
positionsArray[i] = (Math.random() - 0.5) \* 4
}

// Create the attribute and name it 'position'
const positionsAttribute = new THREE.BufferAttribute(positionsArray, 3)
geometry.setAttribute('position', positionsAttribute)
자바스크립트

유일한 어려움은 count _ 3 _ 3부품일 수 있지만 설명하기는 매우 간단합니다 50. 삼각형이 필요합니다 . 각 삼각형은 3꼭짓점으로 구성되고 각 꼭짓점은 3값( x, y, 및 z)으로 구성됩니다.

색인
BufferGeometry의 한 가지 흥미로운 점 은 index속성을 사용하여 정점을 상호화할 수 있다는 것 입니다. 큐브를 고려하십시오. 여러 면은 모서리에 있는 것과 같은 일부 정점을 사용할 수 있습니다. 그리고 자세히 보면 모든 정점은 다양한 이웃 삼각형에 의해 사용될 수 있습니다. 그러면 속성 배열이 더 작아지고 성능이 향상됩니다. 그러나 우리는 그 수업에서 이 부분을 다루지 않을 것입니다.
