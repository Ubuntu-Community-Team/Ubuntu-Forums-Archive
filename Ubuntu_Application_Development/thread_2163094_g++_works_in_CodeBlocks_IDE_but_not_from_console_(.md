---
title: "g++ works in CodeBlocks IDE but not from console (unrecognized option '--sysroot=/')"
date: 2013-07-17
forum: Ubuntu Application Development
---

### Post by Achronon on 2013-07-17
Hi there,
I've written a lot of code in the past, all on Solaris or Fedora GNU/Linux, but never had so many problems just getting a basic script running as with Ubunutu. (I'm using Kubuntu raring x86_6 arch).

All src tarballs I've installed in the past have compiled fine, as do Perl modules and so forth.  But gfortran, gcc and g++ seem broken for me, but I have no idea how or why.

Even if I compile a minimal "Hello World" script, I can do it in CodeBlocks, but not from console. I've looked for ENVARS settings that are different.  Result none.  Looked at linkage and compile settings differences: result none.  Tried scrutnizing `g++ -v ...`  output, it's all the same with CodeBlokcs as on cmdline with the sole annoying exception that from the cmdl I get:
```

ls: unrecognized option '--sysroot=/'
Try 'ls --help' for more information.
collect2: error: ld returned 1 exit status

```
Why the hell is the --sysroot option not recognised???  It's a standard ption, plus it's automated, I do not need to set it.  SO why is the configuration of g++/gcc so boken?

Ha!, obviously it's not really "broken" since i've got CodeBlocks working fine.  Question really is : What's the difference between my console settings and CodeBlocks?

These are some relevant envars:
```

CPLUS_INCLUDE_PATH=/usr/include:/usr/include/c++/4.7
C_INCLUDE_PATH=/usr/include/x86_64-linux-gnu
LIBRARY_PATH=/usr/lib/x86_64-linux-gnu

```
But as you can see, the compiler adds to these.  The end result seems all the same to me whether run from CodeBlocks or cmdl.  It just fails at "ls: unrecognised option --sysroot=/"

I mean, why the heck is the `ls' utility being handed this option anyway???  

This is so infuriating, such a mystery, since I cannot find any source of why this leads to linkage failure with cmdl but not inside CodeBlocks. Cannot find any help with Google or searching the forums. Has no one else suffered these problems?

BTW: comp[ile & link does not work in kdevelop either. Weird huh?

Please help.. any tips?

Here's the script and the verbose output from g++:
FIrst I need:
```
export CPLUS_INCLUDE_PATH=/usr/include:/usr/include/c++/4.7
```
then
```

$ cat main.cpp
#include <iostream>

using namespace std;

int main()
{
    cout << "Hello world!" << endl;
    return 0;
}
```
then
```
g++ -c main.cpp -o main.o
```
no problems up to here.

Then,
```
g++ -o hello main.o -v
```
and get this:
```
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.7/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.7.3-1ubuntu1' --with-bugurl=file:///usr/share/doc/gcc-4.7/README.Bugs --enable-languages=c,c++,go,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.7 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.7 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --with-system-zlib --enable-objc-gc --with-cloog --enable-cloog-backend=ppl --disable-cloog-version-check --disable-ppl-version-check --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) 
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.7/:/usr/lib/gcc/x86_64-linux-gnu/4.7/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.7/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.7/:/usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.7/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.7/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-o' 'hello' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.7/collect2 --sysroot=/ --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu --as-needed -dynamic-linker /lib64/ld-linux-x86-64.so.2 -z relro -o hello /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/crt1.o /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.7/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/4.7 -L/usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/4.7/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.7/../../.. main.o -lstdc++ -lm -lgcc_s -lgcc -lc -lgcc_s -lgcc /usr/lib/gcc/x86_64-linux-gnu/4.7/crtend.o /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/crtn.o
ls: unrecognized option '--sysroot=/'
Try 'ls --help' for more information.
collect2: error: ld returned 1 exit status
```

Thing is, that's all verbatim the same messages as I see within CodeBlocks (the IDE), with the sole exception of the "ls: unrecognized option '--sysroot=/'" error.  So whereas CodeBlocks has ext status "0" and produces a fine working binary, the cmdl linking does not. Also hard to believe CodeBlocks works fine but not KDevelop.  

I'm stupified.

Never been so stumped with such basic things before... maybe that's my problem. Never had to dig deep before for answsers to suhc basic programming questions.

PS. Why do I bother with cmdl scripting?  Because I'm a physics/maths teacher and do not want to tie my studnets to any particualr IDE early on.  I hope they'll learn to use the cmdl at least for a few weeks.

---

### Post by steeldriver on 2013-07-17
**ld** has a --sysroot option - **ls** doesn't ... it looks like somehow the ld binary that is being found from g++ is actually ls?

---

### Post by Achronon on 2013-07-18
[SOLVED]
ha, a clear case of shooting oneself in the foot proverbially.

Thanks to 'steeldriver' I just had to do some proverbial navel gazing at my bin paths, and I had stupidly created a script some donkeys years ago named $HOME/bin/ld for some sort of math.  Renamed that and linking is good to go.

---

