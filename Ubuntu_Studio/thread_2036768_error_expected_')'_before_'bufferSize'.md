---
title: "error: expected ')' before 'bufferSize'"
date: 2012-08-02
forum: Ubuntu Studio
---

### Post by Gusss on 2012-08-02
Hi all,
Im getting this error when compiling an audio program called "wonder" :

```
src/render/fwonder/complexdelayline.h:40:30: error: expected ')'
before 'bufferSize'
src/render/fwonder/complexdelayline.h:50:5: error: 'size_t' does not name a type
src/render/fwonder/complexdelayline.h:51:5: error: 'size_t' does not name a type
src/render/fwonder/complexdelayline.cpp:38:1: error: prototype for
'ComplexDelayLine::ComplexDelayLine(size_t, size_t)' does not match
any in class 'ComplexDelayLine'
src/render/fwonder/complexdelayline.h:48:5: error: candidate is:
ComplexDelayLine::ComplexDelayLine(const ComplexDelayLine&)
src/render/fwonder/complexdelayline.cpp: In member function 'FftwBuf*
ComplexDelayLine::operator[](int)':
src/render/fwonder/complexdelayline.cpp:57:54: error: 'noBuffers' was
not declared in this scope
src/render/fwonder/complexdelayline.cpp: In member function 'void
ComplexDelayLine::clearCurrentBufferAndAdvance()':
src/render/fwonder/complexdelayline.cpp:75:34: error: 'noBuffers' was
not declared in this scope
scons: *** [obj/render/fwonder/complexdelayline.o] Error 1
scons: building terminated because of errors.
```

This is the code from the files it mentions :

complexdelayline.h :

```

#ifndef COMPLEXDELAYLINE_H
#define COMPLEXDELAYLINE_H

#include <vector>

class FftwBuf;

class ComplexDelayLine
{

public:
    ComplexDelayLine( size_t bufferSize, size_t noBuffers );
    ~ComplexDelayLine();

    FftwBuf* operator[]( int noBuffer );

    void clearCurrentBufferAndAdvance();

private:
    ComplexDelayLine( const ComplexDelayLine& other );

    size_t bufferSize;
    size_t noBuffers;
    int    currentBuffer;

    std::vector< FftwBuf* > buffers;

};

#endif
```


and complexdelayline.cpp :

```

#ifndef COMPLEXDELAYLINE_H
#define COMPLEXDELAYLINE_H

#include <vector>

class FftwBuf;

class ComplexDelayLine
{

public:
    ComplexDelayLine( size_t bufferSize, size_t noBuffers );
    ~ComplexDelayLine();

    FftwBuf* operator[]( int noBuffer );

    void clearCurrentBufferAndAdvance();

private:
    ComplexDelayLine( const ComplexDelayLine& other );

    size_t bufferSize;
    size_t noBuffers;
    int    currentBuffer;

    std::vector< FftwBuf* > buffers;

};

#endif
```


any ideas ?
cheers,
Gus

---

### Post by spjackson on 2012-08-03
You seem to have pasted complexdelayline.h twice. Could you please
paste complexdelayline.cpp? Also, what compiler flags are being used?

---

### Post by lisati on 2012-08-03
Just as an aside, using [NOPARSE]```

``` often formats better than > [/NOPARSE] when copying and pasting code snippets.

---

### Post by Gusss on 2012-08-03
> **spjackson said:**
> You seem to have pasted complexdelayline.h twice. Could you please
paste complexdelayline.cpp? Also, what compiler flags are being used?


here : 

```

#include "complexdelayline.h"
#include "fftwbuf.h"

#include <iostream>

using std::cerr;
using std::endl;


ComplexDelayLine::ComplexDelayLine( size_t bufferSize, size_t noBuffers ) : bufferSize( bufferSize ), noBuffers( noBuffers ), currentBuffer( 0 )
{
    for( unsigned int i = 0; i < noBuffers; ++i )
        buffers.push_back( new FftwBuf( bufferSize ) );
}


ComplexDelayLine::~ComplexDelayLine()
{
    while( ! buffers.empty() )
    {
        delete buffers.back();
        buffers.pop_back();
    }
}


FftwBuf* ComplexDelayLine::operator[]( int noBuffer )
{
    int bufferIndex = ( noBuffer + currentBuffer ) % noBuffers;

    if( bufferIndex < 0 )
    {
        cerr << "[Fwonder Error]: negative index into ComplexDelayLine, using first buffer instead." << endl;
        bufferIndex = 0;
    }

    return buffers[ bufferIndex ];
}


void ComplexDelayLine::clearCurrentBufferAndAdvance()
{
    buffers[ currentBuffer ]->clear();
    ++currentBuffer;

    // warp aroung if last buffer was already reached
    if( currentBuffer >= ( int ) noBuffers )
        currentBuffer = 0;
}


ComplexDelayLine::ComplexDelayLine( const ComplexDelayLine& other )
{
    // just preventing copying
}
```

---

### Post by steeldriver on 2012-08-03
maybe try adding

```
#include <cstddef>
using std::size_t;

```

to your complexdelayline.h file ?

---

### Post by Gusss on 2012-08-03
hmm thanks I think thats better. This program uses scons to compile. Now ~I have the following error

```
scons: warning: The Options class is deprecated; use the Variables class instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 148, in <module>

scons: warning: The BoolOption() function is deprecated; use the BoolVariable() function instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 150, in <module>

scons: warning: The EnumOption() function is deprecated; use the EnumVariable() function instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 163, in <module>

scons: warning: The PathOption() function is deprecated; use the PathVariable() function instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 164, in <module>

scons: warning: BuildDir() and the build_dir keyword have been deprecated;
	use VariantDir() and the variant_dir keyword instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 176, in <module>
pkg-config installed? (cached) yes
sndfile installed? yes
fftw3f installed? yes
libxml++-2.6 installed? (cached) yes
liblo installed? (cached) yes
svn: '.' is not a working copy
Wonder library	[Yes]

scons: warning: The env.Copy() method is deprecated; use the env.Clone() method instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 359, in <module>
jackpp library	[Yes]
cwonder		[Yes]
twonder		[Yes]
fwonder		[Yes]
xwonder		[Yes]

scons: warning: QTDIR variable is not defined, using moc executable as a hint (QTDIR=None)
File "/home/dew/Desktop/wonder3.1.0/tools/qt4tool/qt4.py", line 203, in _detect
scoreplayer	[Yes]
jfwonder	[Yes]
tracker		[Yes]
qfwonder	[Yes]

scons: warning: QTDIR variable is not defined, using moc executable as a hint (QTDIR=None)
File "/home/dew/Desktop/wonder3.1.0/tools/qt4tool/qt4.py", line 203, in _detect
build		[release]
scons: done reading SConscript files.
scons: Building targets ...
g++ -o obj/jfwonder/jfwonder_config.o -c -Wall -O3 -march=native -msse -msse2 -msse3 -mfpmath=sse -DNDEBUG -Isrc/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/i386-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/i386-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include src/jfwonder/jfwonder_config.cpp
src/jfwonder/jfwonder_config.cpp: In member function 'void jfwonderConfig::parse_args(int, char**)':
src/jfwonder/jfwonder_config.cpp:133:51: error: 'printf' was not declared in this scope
src/jfwonder/jfwonder_config.cpp:149:46: error: 'printf' was not declared in this scope
scons: *** [obj/jfwonder/jfwonder_config.o] Error 1
scons: building terminated because of errors.

```

I only need to install the "wfs" (wavefield synthesis) part of this program but when I try and install that I get :

```
dew@dew-PA65-UD3-B3:~/Desktop/wonder3.1.0$ scons wfs=1
scons: Reading SConscript files ...

========== WONDER 3.1.9 ========== 

scons: warning: The Options class is deprecated; use the Variables class instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 148, in <module>

scons: warning: The BoolOption() function is deprecated; use the BoolVariable() function instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 150, in <module>

scons: warning: The EnumOption() function is deprecated; use the EnumVariable() function instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 163, in <module>

scons: warning: The PathOption() function is deprecated; use the PathVariable() function instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 164, in <module>

scons: warning: BuildDir() and the build_dir keyword have been deprecated;
	use VariantDir() and the variant_dir keyword instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 176, in <module>
pkg-config installed? (cached) yes
libxml++-2.6 installed? yes
liblo installed? yes
svn: '.' is not a working copy
Wonder library	[Yes]

scons: warning: The env.Copy() method is deprecated; use the env.Clone() method instead.
File "/home/dew/Desktop/wonder3.1.0/SConstruct", line 359, in <module>
jackpp library	[Yes]
cwonder		[Yes]
twonder		[Yes]
fwonder		[No]
xwonder		[Yes]

scons: warning: QTDIR variable is not defined, using moc executable as a hint (QTDIR=None)
File "/home/dew/Desktop/wonder3.1.0/tools/qt4tool/qt4.py", line 203, in _detect
scoreplayer	[Yes]
jfwonder	[Yes]
tracker		[No]
qfwonder	[No]
build		[release]
scons: done reading SConscript files.
scons: Building targets ...
g++ -o obj/jfwonder/jfwonder_config.o -c -Wall -O3 -march=native -msse -msse2 -msse3 -mfpmath=sse -DNDEBUG -Isrc/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/i386-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/i386-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include src/jfwonder/jfwonder_config.cpp
src/jfwonder/jfwonder_config.cpp: In member function 'void jfwonderConfig::parse_args(int, char**)':
src/jfwonder/jfwonder_config.cpp:133:51: error: 'printf' was not declared in this scope
src/jfwonder/jfwonder_config.cpp:149:46: error: 'printf' was not declared in this scope
scons: *** [obj/jfwonder/jfwonder_config.o] Error 1
scons: building terminated because of errors.
dew@dew-PA65-UD3-B3:~/Desktop/wonder3.1.0$ 

```

---

