---
title: "Self compiled FFADO /and JACK won't start with firewire"
date: 2014-10-09
forum: Ubuntu Studio
---

### Post by Bedlore on 2014-10-09
I've compiled FFADO and JACK 1.9.10 but when I try and start jack I get Unknown driver "firewire".  I need help please.

Compiling FFADO worked fine, running ffado-test is able to find my firewire device correctly.

Compiling Jack appeared to work fine, ie.

```
$ sudo ./waf configure --firewire --alsa --prefix=/usr/
[sudo] password for bedlore: 
Setting top to                           : /home/bedlore/JACK/jack-1.9.10 
Setting out to                           : /home/bedlore/JACK/jack-1.9.10/build 
Checking for 'g++' (c++ compiler)        : /usr/bin/g++ 
Checking for 'gcc' (c compiler)          : /usr/bin/gcc 
Linux detected 
Checking for header samplerate.h         : yes 
Checking for program pkg-config          : /usr/bin/pkg-config 
Checking for 'alsa' >= 1.0.18            : yes 
Checking for 'libfreebob' >= 1.0.0       : not found 
Checking for 'libffado' >= 1.999.17      : yes 
Checking for 'gtkIOStream' >= 1.4.0      : not found 
Checking for 'eigen3' >= 3.1.2           : yes 
Checking for header samplerate.h         : yes 
Checking for header sndfile.h            : yes 
Checking for 'celt' >= 0.5.0             : yes 
Checking for library readline            : yes 
Checking for 'celt' >= 0.11.0            : yes 
Checking for 'opus' >= 0.9.0             : yes 
Checking for header opus/opus_custom.h   : not found 

==================                      
JACK 1.9.10 svn revision will checked and eventually updated during build
Build with a maximum of 64 JACK clients
Build with a maximum of 768 ports per application
Install prefix                           :  /usr 
Library directory                        :  /usr/lib 
Drivers directory                        :  /usr/lib/jack 
Build debuggable binaries                :  no 
C compiler flags                         :  ['-Wall'] 
C++ compiler flags                       :  ['-Wall'] 
Linker flags                             :  [] 
Build doxygen documentation              :  no 
Build Opus netjack2                      :  no 
Build with engine profiling              :  no 
Build with 32/64 bits mixed mode         :  no 
Build standard JACK (jackd)              :  yes 
Build D-Bus JACK (jackdbus)              :  no 
Autostart method                         :  classic 
Build with ALSA support                  :  yes 
Build with FireWire (FreeBob) support    :  no 
Build with FireWire (FFADO) support      :  yes 
Build with IIO support                   :  no 

'configure' finished successfully (0.468s)
```

Can someone please help me get this working.

Thank you

---

