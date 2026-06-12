---
title: "errors during compiling with g++"
date: 2016-01-05
forum: Ubuntu Application Development
---

### Post by lukasz17 on 2016-01-05
Hello,

I have some problems with g++ compiler. I tried simple helloWorld application:
```
#include <iostream>
using namespace std;


int main()
{
    cout << "Dziala?" << endl;


    return 0;
}
```

And the result is:

```
/tmp/cc5lzzsg.o: In function `main':HelloWorld.cpp:(.text+0xa): undefined reference to `std::cout'
HelloWorld.cpp:(.text+0xf): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
HelloWorld.cpp:(.text+0x14): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
HelloWorld.cpp:(.text+0x1c): undefined reference to `std::ostream::operator<<(std::ostream& (*)(std::ostream&))'
/tmp/cc5lzzsg.o: In function `__static_initialization_and_destruction_0(int, int)':
HelloWorld.cpp:(.text+0x4a): undefined reference to `std::ios_base::Init::Init()'
HelloWorld.cpp:(.text+0x59): undefined reference to `std::ios_base::Init::~Init()'
collect2: error: ld returned 1 exit status
```


I lost half of a day yesterday and i have no clue what is wrong. 
My g++ version:
```
Using built-in specs.COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/5/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 5.3.0-3ubuntu1~14.04' --with-bugurl=file:///usr/share/doc/gcc-5/README.Bugs --enable-languages=c,ada,c++,java,go,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-5 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=gcc4-compatible --disable-libstdcxx-dual-abi --enable-gnu-unique-object --disable-vtable-verify --enable-libmpx --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-5-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-5-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-5-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 5.3.0 20151204 (Ubuntu 5.3.0-3ubuntu1~14.04) 

```


Do you have any ideas?

---

### Post by spjackson on 2016-01-05
It looks like the link is being done by gcc not g++.
```

g++ -o HelloWorld HelloWorld.cpp

```
should work. What steps are you using to build?

---

