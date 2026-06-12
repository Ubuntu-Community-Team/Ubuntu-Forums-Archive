---
title: "ubuntu 2204 scap workbench error"
date: 2022-05-05
forum: Security
---

### Post by lance bermudez on 2022-05-05
Im getting an error that i do not understand when trying to build the gui for openscap.

have installed
```

sudo apt install libopenscap-dev libopenscap8 libopenscap8-dbg python3-openscap build-essential cmake lxqt-openssh-askpass qtdeclarative5-dev libqt5xmlpatterns5 libqt5xmlpatterns5-dev asciidoc

```

error I get
```

scap-workbench-1.2.1$ mkdir build ; cd build 
scap-workbench-1.2.1/build$ cmake ../
scap-workbench-1.2.1/build$ make
/home/lance/temp/OpenScapWorkBench/scap-workbench-1.2.1/src/MainWindow.cpp: In member function ‘void MainWindow::openFile(const QString&, bool)’:
/home/lance/temp/OpenScapWorkBench/scap-workbench-1.2.1/src/MainWindow.cpp:412:28: error: loop variable ‘path’ creates a copy from type ‘const QString’ [-Werror=range-loop-construct]
  412 |         for (const QString path : mScanningSession->getOriginalClosure())
      |                            ^~~~
/home/lance/temp/OpenScapWorkBench/scap-workbench-1.2.1/src/MainWindow.cpp:412:28: note: use reference type to prevent copying
  412 |         for (const QString path : mScanningSession->getOriginalClosure())
      |                            ^~~~
      |                            &
cc1plus: all warnings being treated as errors
make[2]: *** [CMakeFiles/scap-workbench.dir/build.make:202: CMakeFiles/scap-workbench.dir/src/MainWindow.cpp.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:86: CMakeFiles/scap-workbench.dir/all] Error 2
make: *** [Makefile:156: all] Error 2

```

---

