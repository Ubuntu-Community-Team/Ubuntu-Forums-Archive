---
title: "Problema al compilar Linux Multimedia Studio"
date: 2009-02-25
forum: Software
---

### Post by MPx1 on 2009-02-25
Hola, gente.. bueno me baje la version 0.4.3 del LMMS y a la hora de compilarlo con el CMake me sale este error..

-- The CXX compiler identification is unknown
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error: Internal CMake error, TryCompile configure of cmake failed
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND -- broken
CMake Error at /usr/share/cmake-2.6/Modules/CMakeTestCXXCompiler.cmake:25 (MESSAGE):
  The C++ compiler "CMAKE_CXX_COMPILER-NOTFOUND" is not able to compile a
  simple test program.

  It fails with the following output:

   

  

  CMake will not be able to correctly generate this project.
Call Stack (most recent call first):
  CMakeLists.txt:3 (PROJECT)


CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done


no tengo idea de que pasa... 

los pasos a seguir fueron estos:

* loguearme como root.
* ir al directorio en donde esta LMMS.
* ejecutar el siguiente codigo:

mkdir build

cd build

cmake ../ -DCMAKE_INSTALL_PREFIX=/usr (*)

make

sudo make install


(*) Aca es en donde me sale ese error..

probe con el CMake visual pero me sale lo mismo.. alguna ayuda?

---

### Post by simtaalo on 2009-02-25
try

```
sudo apt-get install cmake && sudo apt-get build-dep lmms
```

---

### Post by MPx1 on 2009-02-25
> **simtaalo said:**
> try

```
sudo apt-get install cmake && sudo apt-get build-dep lmms
```



:biggrin:
Thanks..  I learned something new today.. :thumbsup:

---

### Post by simtaalo on 2009-02-25
:)

that build-dep command is mega useful

---

### Post by MPx1 on 2009-02-25
> **simtaalo said:**
> :)

that build-dep command is mega useful

hahaha XD

---

### Post by miorda on 2009-04-15
hola
yo la mejor manera que encontré de instalar ese programa fue via 
- Sistema/Administración/Origenes del Software
- Soft de Terceros (pestaña)
- Añadir link:

 deb [http://ppa.launchpad.net/tobydox/ppa/ubuntu](http://ppa.launchpad.net/tobydox/ppa/ubuntu) intrepid main

y, si querés modificarlo el src es:

 deb-src [http://ppa.launchpad.net/tobydox/ppa/ubuntu](http://ppa.launchpad.net/tobydox/ppa/ubuntu) intrepid main

Saludos!

Fuente: [https://launchpad.net/~tobydox/+archive/ppa](https://launchpad.net/~tobydox/+archive/ppa)

---

