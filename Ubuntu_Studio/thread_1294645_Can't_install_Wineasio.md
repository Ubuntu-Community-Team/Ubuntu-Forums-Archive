---
title: "Can't install Wineasio"
date: 2009-10-18
forum: Ubuntu Studio
---

### Post by lavadisco on 2009-10-18
I downloaded the ASIO SDK from steinberg, and put the asio.h file in the wineasio folder as instructed. But here's what I get when I try to *make* it:

```
lavadisco@lavadisco:~/Desktop/wineasio$ sudo make
gcc -c -I. -I/usr/include -I/usr/local/include -I/usr/local/include/wine -I/usr/local/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
asio.c:32:33: error: wine/windows/windef.h: No such file or directory
asio.c:33:34: error: wine/windows/winbase.h: No such file or directory
asio.c:34:34: error: wine/windows/objbase.h: No such file or directory
asio.c:35:35: error: wine/windows/mmsystem.h: No such file or directory
asio.c:41:26: error: wine/library.h: No such file or directory
asio.c:42:24: error: wine/debug.h: No such file or directory
asio.c:49: warning: data definition has no type or storage class
asio.c:49: warning: type defaults to ‘int’ in declaration of ‘WINE_DEFAULT_DEBUG_CHANNEL’
asio.c:49: warning: parameter names (without types) in function declaration
asio.c:55: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CALLBACK’
asio.c:58: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘const’
asio.c:98: warning: return type defaults to ‘int’
asio.c: In function ‘DECLARE_INTERFACE_’:
asio.c:99: warning: implicit declaration of function ‘STDMETHOD_’
asio.c:99: error: ‘HRESULT’ undeclared (first use in this function)
asio.c:99: error: (Each undeclared identifier is reported only once
asio.c:99: error: for each function it appears in.)
asio.c:99: error: ‘QueryInterface’ undeclared (first use in this function)
asio.c:99: error: ‘THIS_’ undeclared (first use in this function)
asio.c:99: error: expected ‘)’ before ‘REFIID’
asio.c:99: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:99: error: expected ‘;’ before ‘PURE’
asio.c:100: error: ‘ULONG’ undeclared (first use in this function)
asio.c:100: error: ‘AddRef’ undeclared (first use in this function)
asio.c:100: error: ‘THIS’ undeclared (first use in this function)
asio.c:100: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:100: error: expected ‘;’ before ‘PURE’
asio.c:101: error: ‘Release’ undeclared (first use in this function)
asio.c:101: error: called object ‘STDMETHOD_(<erroneous-expression>,  <erroneous-expression>)’ is not a function
asio.c:101: error: expected ‘;’ before ‘PURE’
asio.c:102: error: expected expression before ‘ASIOBool’
asio.c:102: error: expected ‘)’ before ‘void’
asio.c:102: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:102: error: expected ‘;’ before ‘PURE’
asio.c:103: error: expected expression before ‘void’
asio.c:103: error: expected ‘)’ before ‘char’
asio.c:103: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:103: error: expected ‘;’ before ‘PURE’
asio.c:104: error: expected expression before ‘long’
asio.c:104: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:104: error: expected ‘;’ before ‘PURE’
asio.c:105: error: expected expression before ‘void’
asio.c:105: error: expected ‘)’ before ‘char’
asio.c:105: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:105: error: expected ‘;’ before ‘PURE’
asio.c:106: error: expected expression before ‘ASIOError’
asio.c:106: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:106: error: expected ‘;’ before ‘PURE’
asio.c:107: error: expected expression before ‘ASIOError’
asio.c:107: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:107: error: expected ‘;’ before ‘PURE’
asio.c:108: error: expected expression before ‘ASIOError’
asio.c:108: error: expected ‘)’ before ‘long’
asio.c:108: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:108: error: expected ‘;’ before ‘PURE’
asio.c:109: error: expected expression before ‘ASIOError’
asio.c:109: error: expected ‘)’ before ‘long’
asio.c:109: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:109: error: expected ‘;’ before ‘PURE’
asio.c:110: error: expected expression before ‘ASIOError’
asio.c:110: error: expected ‘)’ before ‘long’
asio.c:110: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:110: error: expected ‘;’ before ‘PURE’
asio.c:111: error: expected expression before ‘ASIOError’
asio.c:111: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:111: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:111: error: expected ‘;’ before ‘PURE’
asio.c:112: error: expected expression before ‘ASIOError’
asio.c:112: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:112: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:112: error: expected ‘;’ before ‘PURE’
asio.c:113: error: expected expression before ‘ASIOError’
asio.c:113: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:113: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:113: error: expected ‘;’ before ‘PURE’
asio.c:114: error: expected expression before ‘ASIOError’
asio.c:114: error: expected ‘)’ before ‘ASIOClockSource’
asio.c:114: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:114: error: expected ‘;’ before ‘PURE’
asio.c:115: error: expected expression before ‘ASIOError’
asio.c:115: error: expected ‘)’ before ‘long’
asio.c:115: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:115: error: expected ‘;’ before ‘PURE’
asio.c:116: error: expected expression before ‘ASIOError’
asio.c:116: error: expected ‘)’ before ‘ASIOSamples’
asio.c:116: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:116: error: expected ‘;’ before ‘PURE’
asio.c:117: error: expected expression before ‘ASIOError’
asio.c:117: error: expected ‘)’ before ‘ASIOChannelInfo’
asio.c:117: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:117: error: expected ‘;’ before ‘PURE’
asio.c:118: error: expected expression before ‘ASIOError’
asio.c:118: error: expected ‘)’ before ‘ASIOBufferInfo’
asio.c:118: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:118: error: expected ‘;’ before ‘PURE’
asio.c:119: error: expected expression before ‘ASIOError’
asio.c:119: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:119: error: expected ‘;’ before ‘PURE’
asio.c:120: error: expected expression before ‘ASIOError’
asio.c:120: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:120: error: expected ‘;’ before ‘PURE’
asio.c:121: error: expected expression before ‘ASIOError’
asio.c:121: error: expected ‘)’ before ‘long’
asio.c:121: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:121: error: expected ‘;’ before ‘PURE’
asio.c:122: error: expected expression before ‘ASIOError’
asio.c:122: error: called object ‘STDMETHOD_(<erroneous-expression>)’ is not a function
asio.c:122: error: expected ‘;’ before ‘PURE’
asio.c: At top level:
asio.c:145: error: expected ‘:’, ‘,’, ‘;’, ‘}’ or ‘__attribute__’ before ‘*’ token
asio.c:200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c:210: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c:235: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c: In function ‘set_clientname’:
asio.c:278: error: ‘IWineASIOImpl’ has no member named ‘client_name’
asio.c:262: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
asio.c:266: warning: ignoring return value of ‘getline’, declared with attribute warn_unused_result
asio.c: In function ‘read_config’:
asio.c:289: warning: implicit declaration of function ‘TRACE’
asio.c:308: warning: implicit declaration of function ‘isspace’
asio.c:315: error: ‘IWineASIOImpl’ has no member named ‘client_name’
asio.c:286: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
asio.c: In function ‘get_numChannels’:
asio.c:338: error: ‘IWineASIOImpl’ has no member named ‘client_name’
asio.c:342: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
asio.c: In function ‘set_portname’:
asio.c:355: error: ‘IWineASIOImpl’ has no member named ‘client_name’
asio.c:361: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
asio.c:365: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
asio.c:366: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
asio.c: At top level:
asio.c:371: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_init’
asio.c:371: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_init’
asio.c:498: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getDriverName’
asio.c:498: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getDriverName’
asio.c:504: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getDriverVersion’
asio.c:504: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getDriverVersion’
asio.c:510: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getErrorMessage’
asio.c:510: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getErrorMessage’
asio.c: In function ‘get_targetname’:
asio.c:521: error: ‘IWineASIOImpl’ has no member named ‘client_name’
asio.c:525: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
asio.c: At top level:
asio.c:533: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_start’
asio.c:533: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_start’
asio.c:643: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_stop’
asio.c:643: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_stop’
asio.c:682: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getChannels’
asio.c:682: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getChannels’
asio.c:698: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getLatencies’
asio.c:698: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getLatencies’
asio.c:712: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getBufferSize’
asio.c:712: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getBufferSize’
asio.c:734: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_canSampleRate’
asio.c:734: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_canSampleRate’
asio.c:745: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getSampleRate’
asio.c:745: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getSampleRate’
asio.c:758: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_setSampleRate’
asio.c:758: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_setSampleRate’
asio.c:769: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getClockSources’
asio.c:769: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getClockSources’
asio.c:788: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_setClockSource’
asio.c:788: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_setClockSource’
asio.c:803: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getSamplePosition’
asio.c:803: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getSamplePosition’
asio.c:825: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getChannelInfo’
asio.c:825: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getChannelInfo’
asio.c:860: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_disposeBuffers’
asio.c:860: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_disposeBuffers’
asio.c:894: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_createBuffers’
asio.c:894: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_createBuffers’
asio.c:1025: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_controlPanel’
asio.c:1025: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_controlPanel’
asio.c:1032: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_future’
asio.c:1032: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_future’
asio.c:1058: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_outputReady’
asio.c:1058: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_outputReady’
asio.c:1065: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WineASIO_Vtbl’
asio.c:1093: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘asioCreateInstance’
asio.c: In function ‘getNanoSeconds’:
asio.c:1114: warning: implicit declaration of function ‘timeGetTime’
asio.c: In function ‘jack_process’:
asio.c:1130: error: ‘IWineASIOImpl’ has no member named ‘state’
asio.c:1133: error: ‘IWineASIOImpl’ has no member named ‘client’
asio.c:1136: error: ‘IWineASIOImpl’ has no member named ‘client_state’
asio.c:1137: error: ‘IWineASIOImpl’ has no member named ‘client_state’
asio.c:1139: error: ‘IWineASIOImpl’ has no member named ‘sample_position’
asio.c:1142: error: ‘IWineASIOImpl’ has no member named ‘active_inputs’
asio.c:1144: error: ‘IWineASIOImpl’ has no member named ‘input’
asio.c:1146: error: ‘IWineASIOImpl’ has no member named ‘input’
asio.c:1146: error: ‘IWineASIOImpl’ has no member named ‘block_frames’
asio.c:1146: error: ‘IWineASIOImpl’ has no member named ‘toggle’
asio.c:1147: error: ‘IWineASIOImpl’ has no member named ‘input’
asio.c:1158: error: ‘IWineASIOImpl’ has no member named ‘semaphore1’
asio.c:1161: error: ‘IWineASIOImpl’ has no member named ‘semaphore2’
asio.c:1164: error: ‘IWineASIOImpl’ has no member named ‘num_outputs’
asio.c:1166: error: ‘IWineASIOImpl’ has no member named ‘output’
asio.c:1168: error: ‘IWineASIOImpl’ has no member named ‘output’
asio.c:1168: error: ‘IWineASIOImpl’ has no member named ‘block_frames’
asio.c:1168: error: ‘IWineASIOImpl’ has no member named ‘toggle’
asio.c:1169: error: ‘IWineASIOImpl’ has no member named ‘output’
asio.c:1177: error: ‘IWineASIOImpl’ has no member named ‘toggle’
asio.c:1177: error: ‘IWineASIOImpl’ has no member named ‘toggle’
asio.c: At top level:
asio.c:1189: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CALLBACK’
make: *** [asio.o] Error 1

```

Any idea what the problem is here?

---

### Post by Sandsound on 2009-10-19
> **lavadisco said:**
> I downloaded the ASIO SDK from steinberg, and put the asio.h file in the wineasio folder as instructed. But here's what I get when I try to *make* it:

```
lavadisco@lavadisco:~/Desktop/wineasio$ sudo make
gcc -c -I. -I/usr/include -I/usr/local/include -I/usr/local/include/wine -I/usr/local/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
asio.c:32:33: error: wine/windows/windef.h: No such file or directory
asio.c:33:34: error: wine/windows/winbase.h: No such file or directory
asio.c:34:34: error: wine/windows/objbase.h: No such file or directory
asio.c:35:35: error: wine/windows/mmsystem.h: No such file or directory
..........
```

..snip..

I'm no expert, but maybe wine-dev ?

I have a quick how-to here : [http://www.sandgreen.dk/index.php?side=linux_wineasio]("http://www.sandgreen.dk/index.php?side=linux_wineasio")

And python-script here : [http://www.sandgreen.dk/index.php?side=python_wineasio]("http://www.sandgreen.dk/index.php?side=python_wineasio")
Just in case you don't wanna strain your fingers on the terminal :-)

---

### Post by sgx on 2009-10-19
can't you just install it with synaptic/apt-get?
Weird.  If its not in the repositories, convert a
wineasio .rpm using alien, which should be in the repositories
too. If you need some specialty only found in the latest compiled
version of wineasio, ignore this.

Cheers

---

### Post by AutoStatic on 2009-10-20
wine-asio is not in the repo's because it depends on the Steinberg SDK. Besides the package wine-dev you probably also need the asio.h header file. I think it's included in the wine-asio 0.5 tarball, not sure. Later versions do not include the asio.h file anymore AFAIK.

---

### Post by lavadisco on 2009-10-20
Thanks for all the advice guys. I will try installing wine-dev and making a deb file and see if that works. I have already DL'd the asio.h file from Steinberger.

---

### Post by Sandsound on 2009-10-20
> **lavadisco said:**
> Thanks for all the advice guys. I will try installing wine-dev and making a deb file and see if that works. I have already DL'd the asio.h file from Steinberger.

If you make a deb-package, I hope you'll post it here :-)

---

### Post by Sandsound on 2009-10-20
> **AutoStatic said:**
> wine-asio is not in the repo's because it depends on the Steinberg SDK. Besides the package wine-dev you probably also need the asio.h header file. I think it's included in the wine-asio 0.5 tarball, not sure. Later versions do not include the asio.h file anymore AFAIK.

I know it's a touchy subject... but isn't it ok to to distribute a deb with wineasio ? some other distros are doing this, and it would be a big plus to Ubuntu/UbuntuStudio if this where included.

---

### Post by lavadisco on 2009-10-20
> **Sandsound said:**
> If you make a deb-package, I hope you'll post it here :-)

If I can make it work, I'll post it!

---

### Post by lavadisco on 2009-10-20
Just tried to install wine-dev, but it only works with the 1.0.1 stable version, and I have 1.1.24 installed. Considering I just spent hours getting a bunch of stuff installed and working in WINE, including Office 2007 which was a pain, I am just going to wait until wine-dev works with 1.1.24.

---

### Post by sgx on 2009-10-20
> **lavadisco said:**
> Just tried to install wine-dev, but it only works with the 1.0.1 stable version, and I have 1.1.24 installed. Considering I just spent hours getting a bunch of stuff installed and working in WINE, including Office 2007 which was a pain, I am just going to wait until wine-dev works with 1.1.24.
I've never had to install wine-dev for the wineasio to work, I've used it in at least 7 distros with

dpkg -i wineasioxxx.deb  or the rpm equivelent. Then run the commands

regsvr32 wineasio.dll
winecfg

I thought the vestige replacement headers were
being widely used these days, making Steinbergs corporate versions optional.  Cheers

If guilt overcomes you, buy a nice Yamaha product, and call it even.:)

---

### Post by zetanuxi on 2009-11-04
Not meaning to hijack, but I'm trying to install wineasio also and I keep getting errors.
```
pkg-config --exists jack
make: *** [jack] Error 1 
```I uninstalled jack and I still get this error. :cry:

---

### Post by AutoStatic on 2009-11-05
> **Sandsound said:**
> I know it's a touchy subject... but isn't it ok to to distribute a deb with wineasio ? some other distros are doing this, and it would be a big plus to Ubuntu/UbuntuStudio if this where included.Those other distro's are breaking in on Steinberg's licence and can get sued but they're probably so small that they're not on Steinberg's radar. If Canonical would include things like wineasio they would surely get problems.
But there are wineasio debs for Ubuntu scattered around the forums, you could try one of those.

---

### Post by XVampireX on 2009-11-05
folks, to install wineasio, you need several packages:

wine
wine-dev
libjack0.100.0
libjack0.100.0-dev
qjackctl

anyway just follow this guide: [http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio](http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio)

I installed wineasio just fine.

---

### Post by rytmisk on 2009-11-17
a quick checkinstall package if anyone needs it. Remember to 

sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0

and

regsvr32 wineasio.dll

And hopefully you're set.

Ketil

---

### Post by kgi on 2009-11-18
I've got wineasio 0.7.5 working on an amd64 system. Here's what you'll need. Bear in mind that the 64-bit install is harder than the 32-bit install. Note that there USED to be separate forks of wineasio for 64-bit use (called "wineasio-x" or "wineasio-64"). These are NO LONGER NEEDED: wineasio and jack can run fine on a 64-bit system.

Here's the easy version for a 32-bit install:

First of all, install the prerequisites:

```

sudo apt-get install wine1.2 wine1.2-dev libjack0 libjack-dev checkinstall

```

(if you have no build environment, you'll need that; try something like:

```

sudo apt-get install build-essential pkg-config

```

as a starting point).

Next, get asio.h from the Steinberg SDK. When you've got this, hold on to it, as it's a pain to keep on having to re-download.

Next, download wineasio-0.7.5.tar.bz2 from sourceforge. Untar it using the command:

```

tar jxvf wineasio-0.7.5.tar.bz2

```

cd into the directory, and type:

```

make
sudo checkinstall make install

```

Answer a few questions for checkinstall (like the version) and it will build a nice ad-hoc .deb for you, which you can install using "dpkg -i" and uninstall using "dpkg -P".

Now for the harder part. If you're on amd64, you will need a few additional steps. I forget the exact soup of 32-bit libs I had to install; try:

```

sudo apt-get install libc6-dev-i386 lib32stdc++6 ia32-libs gcc-multilib g++-multilib

```

(The reason I'm unsure is that I was also building jackdmp, and I'm not 100% sure which was required for which).

Then, in the Makefile, make the following changes:

In the line starting "wineasio_dll_LDFLAGS" (line 31, in version 0.7.5),
add the directive:

```

-m32

```

In other words, the lines that originally look like this:

```

wineasio_dll_LDFLAGS  = -shared \
                        $(wineasio_dll_MODULE:%=%.spec) \
                        -mnocygwin

```

should read something like:

```

wineasio_dll_LDFLAGS  = -m32 -shared \
                        $(wineasio_dll_MODULE:%=%.spec) \
                        -mnocygwin

```

In the "install:" stanza at the bottom, change the install command
from:

```

    cp wineasio.dll.so $(PREFIX)/lib/wine

```

to:

```

    cp wineasio.dll.so $(PREFIX)/lib32/wine/

```

(Notice the trailing slash: this is good practice as if the directory doesn't exist an error will be raised, whereas without it, the Makefile will silently copy your .so file to a new file called "/usr/lib32/wine").

Now you can make and install as before, and run:

```

regsvr32 wineasio

```

(Note that this shouldn't be done as root)

This version of wineasio works great for me; I can run Reaper and the Native Instruments Kontakt Player demo.

Hope this helps.

Enjoy!

---

### Post by bluesscream on 2009-11-21
Tx kgi, following your guide for the first time I successfully compiled a wineasio_amd64.deb myself. :)
But different from wine-x with jackbridge i.E. in reaper I now only get 2 inputs and 2 outputs of my devices 8/8. With jackbridge I had them all. Any hints?


Just solved this too. Should have read "readme" to the end... had to create a file  home/user/.wineasiocfg with the lines: 
ASIO_INPUTS=8
ASIO_OUTPUTS=8

---

### Post by thorgal on 2009-11-21
read the README.txt that came with the source code. It explains how you can configure wineasio w.r.t number of IOs.

[quote="wineasio README"]
2. USER INSTRUCTIONS
--------------------

The driver can be configured in two ways: either using environment variables or
using a configuration file.

The configuration file can be set per user in ".wineasiocfg".  As a fallback, a
site-wide file can be provided in "/etc/default/wineasiocfg" if desired.

The format for the configuration file is simply "var=val".

If using the shell, either include the assignment on the command line:
    ASIO_INPUTS=0 ~/bin/reaper.exe
or ensure the variable has been exported:
    export ASIO_INPUTS=0
    ~/bin/reaper.exe

The available variables are as follows:
ASIO_INPUTS
ASIO_OUTPUTS
ASIO_INPORTNAME<n>
ASIO_OUTPORTNAME<n>
ASIO_INPORT<n>
ASIO_OUTPORT<n>
<clientname>

The last entry allows you to change the client name from the default, which is
constructed from the program name prefixed by "ASIO_".  For example,
    ASIO_reaper=REAPER
All of the entries beginning ASIO_ can also have entries specific to a client,
using the assigned client name.  For example,
    ASIO_reaper_INPUTS=0
or (if the client name has been re-assigned as above),
    REAPER_INPUTS=0

INPUTS and OUTPUTS
------------------
These let you limit the number of JACK ports allocated to this client.  The
default value for both is 2.

INPORTNAME and OUTPORTNAME
--------------------------
These allow you to rename the input and output ports for the client.  The
default names are "input_<n>" and "output_<n>".  For example,
    REAPER_OUTPORTNAME0=left
    REAPER_OUTPORTNAME1=right

INPORT and OUTPORT
------------------
These allow you to connect the client to JACK ports of your choice.  The
default is to connect JACK's "hardware" inputs to your client's inputs and your
client's outputs to JACK's "hardware" outputs.  You might be running some other
application, e.g. an icecast server, and want to send output to that.  For
example,
    ASIO_OUTPORT0=idjc-mx:aux_lt
    ASIO_OUTPORT1=idjc-mx:aux_rt
[/quote]

---

### Post by lavadisco on 2009-11-26
> **kgi said:**
> I've got wineasio 0.7.5 working on an amd64 system. Here's what you'll need. Bear in mind that the 64-bit install is harder than the 32-bit install. Note that there USED to be separate forks of wineasio for 64-bit use (called "wineasio-x" or "wineasio-64"). These are NO LONGER NEEDED: wineasio and jack can run fine on a 64-bit system.

Here's the easy version for a 32-bit install:

First of all, install the prerequisites:

```

sudo apt-get install wine1.2 wine1.2-dev libjack0 libjack-dev checkinstall

```

(if you have no build environment, you'll need that; try something like:

```

sudo apt-get install build-essential pkg-config

```

as a starting point).

Next, get asio.h from the Steinberg SDK. When you've got this, hold on to it, as it's a pain to keep on having to re-download.

Next, download wineasio-0.7.5.tar.bz2 from sourceforge. Untar it using the command:

```

tar jxvf wineasio-0.7.5.tar.bz2

```

cd into the directory, and type:

```

make
sudo checkinstall make install

```

Answer a few questions for checkinstall (like the version) and it will build a nice ad-hoc .deb for you, which you can install using "dpkg -i" and uninstall using "dpkg -P".


This is an excellent tutorial, however, I get to this point and get an error:

```
Installing with make...Installing with install...

========================= Installation results ===========================
cp wineasio.dll.so /usr/lib/wine
cp: cannot stat `wineasio.dll.so': No such file or directory
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

How can I fix this?

Also, when you say "it will build a nice ad-hoc .deb for you, which you can install using "dpkg -i" and uninstall using "dpkg -P"" do you mean to say that one *could* do that, perhaps at a later time, or is "dpkg -i" a required step here to install wineasio?

---

### Post by bluesscream on 2009-11-26
@ lavadisco:
Checkout where your wine directory which contents a lot of *.dll.so files is - /usr/lib/wine or /usr/lib32/wine.
consequently edit last line in makefile: 
cp wineasio.dll.so $(PREFIX)/lib/wine/ 
or
cp wineasio.dll.so $(PREFIX)/lib32/wine/.
on top of makefile ensure PREFIX=/usr, not PREFIX=usr/local
sudo checkinstall again.
If this does not work too, but you find wineasio.dll.so in the compile directory, as a dirty solution copy this file by hand as root into the wine directory you found, make sure it's executable and run as user, not as root regsvr32 wineasio.
I could help out with a 64bit deb, compiled above way.

---

### Post by lavadisco on 2009-11-27
A deb would be great! I already have a 0.7.4 deb, so hopefully you've got the 0.7.5 deb?

---

### Post by abbot on 2009-12-01
any news on a deb file?  i'm 32 bit though.  i don't know if you guys are just working on 64.

---

### Post by sgx on 2009-12-01
> **abbot said:**
> any news on a deb file?  i'm 32 bit though.  i don't know if you guys are just working on 64.
You can google for an .rpm, and use the alien command to convert that to a .deb. Then install it with dpkg -i. I even used alien to convert a wine
.rpm once! Cheers

---

### Post by falkTX on 2009-12-07
> **sgx said:**
> You can google for an .rpm, and use the alien command to convert that to a .deb. Then install it with dpkg -i. I even used alien to convert a wine
.rpm once! Cheers

I do have it, in my PPA
[https://launchpad.net/~falk-t-j/+archive/music/](https://launchpad.net/~falk-t-j/+archive/music/)

There's also other good things there if you want

---

### Post by Capoeira on 2010-02-15
> **falkTX said:**
> I do have it, in my PPA
[https://launchpad.net/~falk-t-j/+archive/music/](https://launchpad.net/~falk-t-j/+archive/music/)

There's also other good things there if you want

Not allowed here

Sorry, you don't have permission to access this page. 



-------------


i can't even download the source....severs down?

---

### Post by AutoStatic on 2010-02-15
No, this PPA has been taken down a while ago: [http://ubuntuforums.org/showpost.php?p=8530033&postcount=86](http://ubuntuforums.org/showpost.php?p=8530033&postcount=86)

---

### Post by Capoeira on 2010-02-15
> **AutoStatic said:**
> No, this PPA has been taken down a while ago: [http://ubuntuforums.org/showpost.php?p=8530033&postcount=86](http://ubuntuforums.org/showpost.php?p=8530033&postcount=86)

ok, thanks


but can you download the source from here? [http://sourceforge.net/projects/wineasio/](http://sourceforge.net/projects/wineasio/)

i cant

---

### Post by AutoStatic on 2010-02-15
Yes. Maybe you could try another mirror.

---

### Post by Capoeira on 2010-02-15
> **AutoStatic said:**
> Yes. Maybe you could try another mirror.

it's strange, i tried a lot of mirros, always the same strange behavier: the dialogue-box opens where yu choose between "open file" or "download file" (firefox) - "open" results in an error - "download" results in "nothing", nothing happens when the "safe file to" dialouge should be opened. i tried other downloads and it works.

---

### Post by Sandsound on 2010-02-15
> **Capoeira said:**
> it's strange, i tried a lot of mirros, always the same strange behavier...

Download works fine for me.

I have a backup on my website (just in case) : [http://www.sandgreen.dk/xt2/files/wineasio-0.7.5.tar.bz2]("http://www.sandgreen.dk/xt2/files/wineasio-0.7.5.tar.bz2")

---

### Post by Capoeira on 2010-02-15
> **Sandsound said:**
> Download works fine for me.

I have a backup on my website (just in case) : [http://www.sandgreen.dk/xt2/files/wineasio-0.7.5.tar.bz2]("http://www.sandgreen.dk/xt2/files/wineasio-0.7.5.tar.bz2")


wtf, i can't download it from you site, too.......i also tried it with wget, nothing.....must be the bz2 ending


EDIT: was kind of a bug in firefox

EDIT2: found a RPM here, didn't work for me though: [http://www.openmamba.org/distribution/distromatic.html?tag=devel&pkg=wineasio](http://www.openmamba.org/distribution/distromatic.html?tag=devel&pkg=wineasio)

---

### Post by Sandsound on 2010-02-15
> **Capoeira said:**
> wtf, i can't download it from you site, too.......i also tried it with wget, nothing.....must be the bz2 ending

Sorry if this is an obvious question, but did you check your download-folder? (I assume that you are using Firefox)

Alternatively you could try another browser.

---

### Post by Capoeira on 2010-02-15
> **Sandsound said:**
> Sorry if this is an obvious question, but did you check your download-folder? (I assume that you are using Firefox)

Alternatively you could try another browser.

edited my post.....checked my folder, but it was checked the "always ask"-option as always. but i found out that firefox tried to download to the folder wich was greyed out, wich is a folder wich doesn't exist anymore. so i changed the folder....but it was indeed a bug as it was always checked the "always ask" option.

---

### Post by falkTX on 2010-02-16
I package v0.7.4 some time ago, you'll find both 32bits and 64bits in this forum.

---

### Post by mango42 on 2010-06-01
Perhaps this is tangential but I've hit a brick wall trying to get **Reaper (x64)** to start up on UbuntuStudio 10.04 + latest WINE and wineasio in Synaptic. I've used the search engine here and on startpage.com but the only reference I have come up with so far is how to install it in 8.04.

I suspect it's something to do with the gaps in pathnames (eg 'Program Files' & 'Reaper (x64)' ). The Reaper icon appears on the Desktop but the WINE command has too many /..\\./...\...\'s for me to puzzle out, with not a '*' in sight ;-)

Would some kind soul post a *working* commandline / directory pointer for me?

Oh yes, I did the 'regsvr' thing on wineasio.dll...

A **howto** comparable to the FLStudio one on this forum would be nirvana.

---

### Post by sgx on 2010-06-02
Hi, I always install reaper in my /home directory, so its there ready
after reinstalls. (I rename the .wine folder to oldwine before installing a wine update, or new system install, and drag back the needed folders.

I run
wineprefixcreate     (message says its deprecated, but I'm not a trusting soul)

winecfg  (choose alsa for sound)

regsvr32 wineasio.dll  (if its 64bit, must this command change the 32 to 64? Seems likely)

wine reaper351-install.exe

The reaper folder is self-contained, you can move it, preferably before projects have been written. 

Spaces in windows paths must be modified when containing blank spaces.

Program Files
either
Program\ Files
Program*Files

paths from a windows file nested on a CD could have many spots to fill in, like files from an 8gig  ComputerMusicMagazine dvd. 

(this * is a wildcard symbol in linux, use accordingly. No 'nuke me' options exist for the wine command by itself, but when used in other commands, things  could get dicey fast :) )

Cheers

---

### Post by sgx on 2010-06-02
> **falkTX said:**
> I package v0.7.4 some time ago, you'll find both 32bits and 64bits in this forum.

regsvr64 wineasio.dll   is this correct to register the 64 bit version?
(yeah, looks like a pretty dumb question, the shoe fits, so I wear it)
Cheers

---

### Post by mango42 on 2010-06-02
Thanks for the pointers, **sgx** but what does yer actual commandline look like for **Reaper (x64)**?

It would help if there were error msgs but I haven't found any yet...

---

