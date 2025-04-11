## CSC 435 Programming Assignment 2 (Spring 2025)
**Jarvis College of Computing and Digital Media - DePaul University**

**Student**: TO-DO-write-student-name (TO-DO-write-email-address)  
**Solution programming language**: TO-DO-write-solution-programming-language (Java or C++)

### Requirements

If you are implementing your solution in C++ you will need to have GCC 14.x and CMake 3.28.x installed on your system.
On Ubuntu 24.04 LTS you can install GCC and set it as default compiler using the following commands:

```
sudo apt install build-essential cmake g++-14 gcc-14 cmake
sudo update-alternatives --remove-all gcc
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-13 130
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-14 140
sudo update-alternatives --remove-all g++
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-13 130
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-14 140
```

If you are implementing your solution in Java you will need to have Java 21.x and Maven 3.8.x installed on your systems.
On Ubuntu 24.04 LTS you can install Java and Maven using the following commands:

```
sudo apt install maven openjdk-21-jdk
```

### Setup

There are 3 datasets (dataset1, dataset2, dataset3) that you need to use to evaluate the indexing performance of your solution.
Before you can evaluate your solution you need to download the datasets.
You can download the datasets from the following link:

https://depauledu-my.sharepoint.com/:f:/g/personal/aorhean_depaul_edu/Ej4obLnAKMdFh1Hidzd1t1oBHY7IvgqXoLdKRg-buoiisw?e=SWLALa

After you finished downloading the datasets copy them to the dataset directory (create the directory if it does not exist).
Here is an example on how you can copy Dataset1 to the remote machine and how to unzip the dataset:

```
remote-computer$ mkdir datasets
local-computer$ scp dataset1.zip cc@<remote-ip>:<path-to-repo>/datasets/.
remote-computer$ cd <path-to-repo>/datasets
remote-computer$ unzip dataset1.zip
```

### C++ solution
#### How to build/compile

To build the C++ solution use the following commands:
```
cd app-cpp
mkdir build
cmake -S . -B build
cmake --build build --config Release
```

#### How to run application

To run the C++ solution (after you build the project) use the following command:
```
./build/file-retrieval-engine
> <index | search | quit>
```

#### Example

```
./build/file-retrieval-engine
> index ../datasets/dataset1
Completed indexing 134321105 bytes of data
Completed indexing in 10.386 seconds
> search the
Search completed in 0.4 seconds
Search results (top 10 out of 0):
> search child-like
Search completed in 2.1 seconds
Search results (top 10 out of 15):
* folder7/Document10926.txt:4
* folder3/Document10379.txt:3
* folder6/Document10866.txt:2
* folder8/Document1108.txt:1
* folder7/folderD/Document11050.txt:1
* folder6/Document10848.txt:1
* folder6/Document1082.txt:1
* folder4/Document10681.txt:1
* folder4/Document10669.txt:1
* folder3/Document10387.txt:1
> search vortex
Search completed in 2.8 seconds
Search results (top 10 out of 27):
* folder5/folderB/Document10706.txt:6
* folder5/folderB/Document10705.txt:4
* folder7/Document1091.txt:3
* folder4/Document10681.txt:3
* folder6/Document1082.txt:2
* folder4/Document1051.txt:2
* folder3/folderA/Document10422.txt:2
* folder2/Document1033.txt:2
* folder8/Document11159.txt:1
* folder8/Document11154.txt:1
> search moon AND vortex
Search completed in 3.8 seconds
Search results (top 10 out of 19):
* folder5/folderB/Document10706.txt:26
* folder4/Document10681.txt:19
* folder3/Document1043.txt:19
* folder4/Document10600.txt:17
* folder8/Document11154.txt:13
* folder3/folderA/Document10422.txt:6
* folder3/Document10379.txt:6
* folder3/folderA/Document10421.txt:6
* folder5/folderB/Document10705.txt:5
* folder4/Document1033.txt:5
> search distortion AND adaptation
Search completed in 3.27 seconds
Search results (top 10 out of 4):
* folder7/folderC/Document10998.txt:6
* folder4/Document10516.txt:3
* folder8/Document11159.txt:2
* folder8/Document11157.txt:2
> quit
```

### Java solution
#### How to build/compile

To build the Java solution use the following commands:
```
cd app-java
mvn compile
mvn package
```

#### How to run application

To run the Java solution (after you build the project) use the following command:
```
java -cp target/app-java-1.0-SNAPSHOT.jar csc435.app.FileRetrievalEngine
```

#### Example

```
java -cp target/app-java-1.0-SNAPSHOT.jar csc435.app.FileRetrievalEngine
> index ../datasets/dataset1
Completed indexing 134321105 bytes of data
Completed indexing in 10.386 seconds
> search the
Search completed in 0.4 seconds
Search results (top 10 out of 0):
> search child-like
Search completed in 2.1 seconds
Search results (top 10 out of 15):
* folder7/Document10926.txt:4
* folder3/Document10379.txt:3
* folder6/Document10866.txt:2
* folder8/Document1108.txt:1
* folder7/folderD/Document11050.txt:1
* folder6/Document10848.txt:1
* folder6/Document1082.txt:1
* folder4/Document10681.txt:1
* folder4/Document10669.txt:1
* folder3/Document10387.txt:1
> search vortex
Search completed in 2.8 seconds
Search results (top 10 out of 27):
* folder5/folderB/Document10706.txt:6
* folder5/folderB/Document10705.txt:4
* folder7/Document1091.txt:3
* folder4/Document10681.txt:3
* folder6/Document1082.txt:2
* folder4/Document1051.txt:2
* folder3/folderA/Document10422.txt:2
* folder2/Document1033.txt:2
* folder8/Document11159.txt:1
* folder8/Document11154.txt:1
> search moon AND vortex
Search completed in 3.8 seconds
Search results (top 10 out of 19):
* folder5/folderB/Document10706.txt:26
* folder4/Document10681.txt:19
* folder3/Document1043.txt:19
* folder4/Document10600.txt:17
* folder8/Document11154.txt:13
* folder3/folderA/Document10422.txt:6
* folder3/Document10379.txt:6
* folder3/folderA/Document10421.txt:6
* folder5/folderB/Document10705.txt:5
* folder4/Document1033.txt:5
> search distortion AND adaptation
Search completed in 3.27 seconds
Search results (top 10 out of 4):
* folder7/folderC/Document10998.txt:6
* folder4/Document10516.txt:3
* folder8/Document11159.txt:2
* folder8/Document11157.txt:2
> quit
```
