---
title: "Problem arising out of multiple jack installations--right way to resolve this?"
date: 2012-07-04
forum: Ubuntu Studio
---

### Post by OccamsChainsaw on 2012-07-04
I think this will be a fairly easy question for someone who knows their way around linux & synaptic, but I'm new to all of this and made a few rookie mistakes.
Here goes:
 I recently installed FFADO and learned that I needed to build jackd after FFADO installation to get FFADO support with jack (already had the version of jack installed that came with the distribution). So I downloaded a tar for Jack2 and compiled and installed from the source, with flag --prefix= /usr (I thought this would overwrite the version of jack that was already installed).  Later I did a fresh configuration flagging the option to enable firewire support and again installed to usr/bin (again thinking that I was overwriting). When I came to suspect that my inability to start jack was due to multiple installations, I opened up synaptic and lo and behold, saw that I had jackd, jackd2, jackd2-firewire, and libjack-jackd2-0 all installed, which looks to me like I've just been installing new jacks right and left and ensuring that none of them work. (I should also mention that when I look in usr/bin i only see jackd, not jackd2 or -firewire. Perhaps someone can explain this to me, since this is why I didn't pick up on the multiple installations sooner. Also there is an executable there called "jackdbus" which I am not sure if I compiled myself, and whether I will need to get rid of it or not.)

So now i need to either get rid of the original jackd + 1 of the self-compiled jacks, or both of the self-compiled jacks and then figure out how to rebuild the one that came installed. Firstly, Is there any reason to prefer one route over the other (afaik jack1 or jack2 should be ok for my needs, i chose jack2 arbitrarily)? When I tried "apt-get purge jackd2", it tried deleting jackd, jackd2, and jackd2-firewire, and scads of others (including qjackctl, which I *think* I still want?) and installing jackd1 in its place. I aborted because I wasn't sure if this was what I wanted and thought I should check with someone who knows better first.

Thanks in advance, any advice is appreciated.

---

### Post by sgx on 2012-07-04
Hi, I have had a few odd mixups over the years, so I look in
/usr/lib and /usr/bin, noting all items that are jackd
related. (libjack0 jack_connect etc )

Use synaptic to completely uninstall all the items, and agree to include a few dependencies, if they are proposed.

(Now if synaptic proposed deleting what amounts to
your whole system, when removing jackd items, just manually delete all you can find, then reboot, and have synaptic reinstall qjackctl,
which will build a matching set.)

Make sure to remove .jackdrc, and patchage if they exist.

If synaptic worked to remove just the needed files, and a few others,  reboot, and install qjackctl, as this will pull in
a matching jackd, as one of its dependencies.

.jackdrc is a textfile in /home/username, saved by qjackctl when changes to your settings are made.

The large number of jackd files in /usr/bin, are probably
all part of the single jackd installer, unless you installed
jamin, jack-rack eyc etc. Probably good to removethem now,
and reinstall after the drama has subsided :wink:

/home/username/.config/rncbc.org/ is where some qjackctl files may
be deleted. The unmatched name refers
to the gifted authors initials. RNCBC would be
a cool name for a band! :guitar:

jackd 1.97 and greater = jackd2, numbers lower, are jackd1
The need for one Vs the other, is not clear, because your hardware,
and your normal usage may determine which is better suited. If the one you choose is unstable after proper configuration, switch to the
other one. I'll hazard a guess, that for motherboards that are
less than 3 years old, jackd2 is a better choice, but let experience
be your science, each setup is unique,
and there is no giant pool of manpower for massive beta testing.

Cheers

---

### Post by OccamsChainsaw on 2012-07-05
hey sgx, thanks for the reply. I did as you suggested and purged all the  jacks and most related files I could find, rebooted, then went back to  synaptic to install qjackctl. When I mark it for install though it, it  says that it will install all the things I previously uninstalled  (jackd, jackd2, jackd2-firewire, etc). I think that installing all 3 of these will just take me back to the problem i was having previously.  Is this some kind of a linking issue I'm looking at?

---

### Post by sgx on 2012-07-06
those should be fine. Having two different libjack
type of files is where the problems can happen, and now if
you check, there is probably none.

If there is one, I would remove it/them, then reinstall qjackctl,
and the proper files should then come in.

In /usr/lib, I have one libjack, and one libjackserver,
plus and a link to each one, with a slightly different name
(probably to insure compatibility)
Cheers

---

### Post by OccamsChainsaw on 2012-07-06
EDIT: Did some searching, it seems this was a known problem that arose from FFADO, but was supposed to be fixed with the most recent svn release (which I have). Will try reinstalling FFADO and see if this keeps happening.


I did end up going ahead and installing qjackctl plus the recommended dependencies yesterday. Since you mention it, I checked the contents of usr/lib/i386-linux-gnu (synaptic stuck them here instead of usr/lib/) after I reinstalled. I'm curious to know if this looks similar to what you have:

```
jmb /usr/lib/i386-linux-gnu $ find . -name '*jack*'
./jack
./jack/jack_dummy.so
./jack/jack_firewire.so
./jack/jack_netone.so
./jack/jack_loopback.so
./jack/jack_alsa.so
./jack/jack_net.so
./libjack.so.0.1.0
./libjackserver.so.0.1.0
./libjackserver.so.0
./libjack.so.0
```Unfortunately, jack still does not connect and is giving me the same errors as before. I probably should have posted this sooner, but here's the bash output and backtrace i get when trying to start jackd: 

```
jmb /usr/lib/i386-linux-gnu $ qjackctl
Connection failure: Connection refused
Warning: no translation found for 'en_US' locale: /usr/share/qt4/translations/qt_en_US.qm
Warning: no translation found for 'en_US' locale: /usr/share/locale/qjackctl_en_US.qm
*** glibc detected *** /usr/bin/jackd: free(): invalid pointer: 0x008890bc ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x6ff22)[0x21df22]
/lib/i386-linux-gnu/libc.so.6(+0x70bc2)[0x21ebc2]
/lib/i386-linux-gnu/libc.so.6(cfree+0x6d)[0x221cad]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_ZdlPv+0x1f)[0xa3a80f]
/usr/local/lib/libffado.so.2(_ZN11DebugModuleD0Ev+0x2a)[0x7779aa]
/usr/local/lib/libffado.so.2(_ZN18DebugModuleManagerD2Ev+0xa8)[0x777a68]
/usr/local/lib/libffado.so.2(+0x73ec3)[0x774ec3]
/lib/ld-linux.so.2(+0x1312c)[0x6d412c]
/lib/ld-linux.so.2(+0x13b98)[0x6d4b98]
/lib/i386-linux-gnu/libdl.so.2(+0xcf2)[0x447cf2]
/lib/ld-linux.so.2(+0xe61f)[0x6cf61f]
/lib/i386-linux-gnu/libdl.so.2(+0x133a)[0x44833a]
/lib/i386-linux-gnu/libdl.so.2(dlclose+0x28)[0x447d28]
/usr/lib/i386-linux-gnu/libjackserver.so.0(+0x46b84)[0x156b84]
/usr/lib/i386-linux-gnu/libjackserver.so.0(+0x47ba0)[0x157ba0]
/usr/lib/i386-linux-gnu/libjackserver.so.0(jackctl_server_create+0x815)[0x15b165]
/usr/bin/jackd[0x8049c6a]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0x1c7113]
/usr/bin/jackd[0x804a5f1]
======= Memory map: ========
00110000-0018b000 r-xp 00000000 fd:00 2104815    /usr/lib/i386-linux-gnu/libjackserver.so.0.1.0
0018b000-0018d000 r--p 0007b000 fd:00 2104815    /usr/lib/i386-linux-gnu/libjackserver.so.0.1.0
0018d000-0018e000 rw-p 0007d000 fd:00 2104815    /usr/lib/i386-linux-gnu/libjackserver.so.0.1.0
0018e000-0018f000 rw-p 00000000 00:00 0 
0018f000-00193000 r-xp 00000000 fd:00 2105064    /usr/lib/libsigc-2.0.so.0.0.0
00193000-00194000 r--p 00003000 fd:00 2105064    /usr/lib/libsigc-2.0.so.0.0.0
00194000-00195000 rw-p 00004000 fd:00 2105064    /usr/lib/libsigc-2.0.so.0.0.0
00195000-00198000 r-xp 00000000 fd:00 2105775    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
00198000-00199000 r--p 00002000 fd:00 2105775    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
00199000-0019a000 rw-p 00003000 fd:00 2105775    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
0019a000-0019f000 r-xp 00000000 fd:00 2097695    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
0019f000-001a0000 r--p 00004000 fd:00 2097695    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
001a0000-001a1000 rw-p 00005000 fd:00 2097695    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
001ad000-001ae000 r-xp 00000000 00:00 0          [vdso]
001ae000-00326000 r-xp 00000000 fd:00 4325481    /lib/i386-linux-gnu/libc-2.13.so
00326000-00328000 r--p 00178000 fd:00 4325481    /lib/i386-linux-gnu/libc-2.13.so
00328000-00329000 rw-p 0017a000 fd:00 4325481    /lib/i386-linux-gnu/libc-2.13.so
00329000-0032c000 rw-p 00000000 00:00 0 
0033a000-00347000 r-xp 00000000 fd:00 2111240    /usr/local/lib/libiec61883.so.0.1.1
00347000-00348000 r--p 0000c000 fd:00 2111240    /usr/local/lib/libiec61883.so.0.1.1
00348000-00349000 rw-p 0000d000 fd:00 2111240    /usr/local/lib/libiec61883.so.0.1.1
00349000-00367000 r-xp 00000000 fd:00 2105068    /usr/lib/libxml++-2.6.so.2.0.7
00367000-00368000 ---p 0001e000 fd:00 2105068    /usr/lib/libxml++-2.6.so.2.0.7
00368000-00369000 r--p 0001e000 fd:00 2105068    /usr/lib/libxml++-2.6.so.2.0.7
00369000-0036a000 rw-p 0001f000 fd:00 2105068    /usr/lib/libxml++-2.6.so.2.0.7
0036a000-003b7000 r-xp 00000000 fd:00 2105774    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
003b7000-003b8000 r--p 0004d000 fd:00 2105774    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
003b8000-003b9000 rw-p 0004e000 fd:00 2105774    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
003c4000-003d3000 r-xp 00000000 fd:00 2103252    /usr/local/lib/libraw1394.so.11.0.1
003d3000-003d4000 r--p 0000e000 fd:00 2103252    /usr/local/lib/libraw1394.so.11.0.1
003d4000-003d5000 rw-p 0000f000 fd:00 2103252    /usr/local/lib/libraw1394.so.11.0.1
003d5000-00437000 r-xp 00000000 fd:00 2102641    /usr/lib/libglibmm-2.4.so.1.3.0
00437000-00438000 r--p 00061000 fd:00 2102641    /usr/lib/libglibmm-2.4.so.1.3.0
00438000-00439000 rw-p 00062000 fd:00 2102641    /usr/lib/libglibmm-2.4.so.1.3.0
00447000-0044a000 r-xp 00000000 fd:00 4325515    /lib/i386-linux-gnu/libdl-2.13.so
0044a000-0044b000 r--p 00002000 fd:00 4325515    /lib/i386-linux-gnu/libdl-2.13.so
0044b000-0044c000 rw-p 00003000 fd:00 4325515    /lib/i386-linux-gnu/libdl-2.13.so
0045a000-00482000 r-xp 00000000 fd:00 4325516    /lib/i386-linux-gnu/libm-2.13.so
00482000-00483000 r--p 00028000 fd:00 4325516    /lib/i386-linux-gnu/libm-2.13.so
00483000-00484000 rw-p 00029000 fd:00 4325516    /lib/i386-linux-gnu/libm-2.13.so
00484000-0057b000 r-xp 00000000 fd:00 4333849    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
0057b000-0057c000 r--p 000f6000 fd:00 4333849    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
0057c000-0057d000 rw-p 000f7000 fd:00 4333849    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
00589000-005d0000 r-xp 00000000 fd:00 4325394    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
005d0000-005d1000 r--p 00046000 fd:00 4325394    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
005d1000-005d2000 rw-p 00047000 fd:00 4325394    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
005d2000-005e5000 r-xp 00000000 fd:00 4325612    /lib/i386-linux-gnu/libz.so.1.2.3.4
005e5000-005e6000 r--p 00012000 fd:00 4325612    /lib/i386-linux-gnu/libz.so.1.2.3.4
005e6000-005e7000 rw-p 00013000 fd:00 4325612    /lib/i386-linux-gnu/libz.so.1.2.3.4
0064c000-00655000 r-xp 00000000 fd:00 2491522    /usr/lib/i386-linux-gnu/jack/jack_firewire.so
00655000-00656000 r--p 00008000 fd:00 2491522    /usr/lib/i386-linux-gnu/jack/jack_firewire.so
00656000-00657000 rw-p 00009000 fd:00 2491522    /usr/lib/i386-linux-gnu/jack/jack_firewire.so
006c1000-006df000 r-xp 00000000 fd:00 4325446    /lib/i386-linux-gnu/ld-2.13.so
006df000-006e0000 r--p 0001d000 fd:00 4325446    /lib/i386-linux-gnu/ld-2.13.so
006e0000-006e1000 rw-p 0001e000 fd:00 4325446    /lib/i386-linux-gnu/ld-2.13.so
006e3000-006ff000 r-xp 00000000 fd:00 4325490    /lib/i386-linux-gnu/libgcc_s.so.1
006ff000-00700000 r--p 0001b000 fd:00 4325490    /lib/i386-linux-gnu/libgcc_s.so.1
00700000-00701000 rw-p 0001c000 fd:00 4325490    /lib/i386-linux-gnu/libgcc_s.so.1
00701000-0087e000 r-xp 00000000 fd:00 2156077    /usr/local/lib/libffado.so.2.0.1
0087e000-00886000 r--p 0017c000 fd:00 2156077    /usr/local/lib/libffado.so.2.0.1
00886000-0088a000 rw-p 00184000 fd:00 2156077    /usr/local/lib/libffado.so.2.0.1
008dc000-008e3000 r-xp 00000000 fd:00 4325859    /lib/i386-linux-gnu/librt-2.13.so
008e3000-008e4000 r--p 00006000 fd:00 4325859    /lib/i386-linux-gnu/librt-2.13.so
008e4000-008e5000 rw-p 00007000 fd:00 4325859    /lib/i386-linux-gnu/librt-2.13.so
0094d000-0098a000 r-xp 00000000 fd:00 4325473    /lib/i386-linux-gnu/libpcre.so.3.12.1
0098a000-0098b000 r--p 0003c000 fd:00 4325473    /lib/i386-linux-gnu/libpcre.so.3.12.1
0098b000-0098c000 rw-p 0003d000 fd:00 4325473    /lib/i386-linux-gnu/libpcre.so.3.12.1
0098d000-00a6b000 r-xp 00000000 fd:00 2105853    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00a6b000-00a6c000 ---p 000de000 fd:00 2105853    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00a6c000-00a70000 r--p 000de000 fd:00 2105853    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00a70000-00a71000 rw-p 000e2000 fd:00 2105853    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00a71000-00a78000 rw-p 00000000 00:00 0 
00a78000-00bbf000 r-xp 00000000 fd:00 2097433    /usr/lib/libxml2.so.2.7.8
00bbf000-00bc3000 r--p 00147000 fd:00 2097433    /usr/lib/libxml2.so.2.7.8
00bc3000-00bc4000 rw-p 0014b000 fd:00 2097433    /usr/lib/libxml2.so.2.7.8
00bc4000-00bc5000 rw-p 00000000 00:00 0 
00d69000-00d80000 r-xp 00000000 fd:00 4325855    /lib/i386-linux-gnu/libpthread-2.13.so
00d80000-00d81000 r--p 00016000 fd:00 4325855    /lib/i386-linux-gnu/libpthread-2.13.so
00d81000-00d82000 rw-p 00017000 fd:00 4325855    /lib/i386-linux-gnu/libpthread-2.13.so
00d82000-00d84000 rw-p 00000000 00:00 0 
00f12000-00f16000 r-xp 00000000 fd:00 2105776    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
00f16000-00f17000 r--p 00003000 fd:00 2105776    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
00f17000-00f18000 rw-p 00004000 fd:00 2105776    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
08048000-0804d000 r-xp 00000000 fd:00 2101859    /usr/bin/jackd
0804d000-0804e000 r--p 00004000 fd:00 2101859    /usr/bin/jackd
0804e000-0804f000 rw-p 00005000 fd:00 2101859    /usr/bin/jackd
086c7000-086e8000 rw-p 00000000 00:00 0          [heap]
b6c00000-b6c21000 rw-p 00000000 00:00 0 
b6c21000-b6d00000 ---p 00000000 00:00 0 
b6d55000-b6d56000 ---p 00000000 00:00 0 
b6d56000-b7757000 rw-p 00000000 00:00 0 
b7770000-b7775000 rw-p 00000000 00:00 0 
b778d000-b7790000 rw-p 00000000 00:00 0 
bfa28000-bfa49000 rw-p 00000000 00:00 0          [stack]

```This is the readout from qjackctl's message/status window in case it's any help:

```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]20:17:26.815 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]20:17:26.825 Statistics reset.[/COLOR]
 [COLOR=#cccc99]20:17:26.828 ALSA connection change.[/COLOR]
 [COLOR=#999999]20:18:16.883 D-BUS: Service not available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#999999]20:18:16.901 JACK is starting...[/COLOR]
 [COLOR=#990099]20:18:16.906 /usr/bin/pasuspender -- /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n3[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Connection failure: Connection refused
 [COLOR=#66cc99]20:18:17.016 ALSA connection graph change.[/COLOR]
 Cleaning up leftover debug module: DeviceManager
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2011 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 WARNING: Child process terminated by signal 6
 [COLOR=#999999]20:18:17.305 JACK was started with PID=5667.[/COLOR]
 [COLOR=#999999]20:18:17.613 JACK was stopped with exit status=1.[/COLOR]
 [COLOR=#ff0000]20:18:19.413 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

```

---

### Post by sgx on 2012-07-06
Maybe start both qjackctl, and a sound maker, with sudo,
in case of some permissions mixup in firewire support.

phasex synth, and timemachine recorder are here:

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

Cheers

---

### Post by OccamsChainsaw on 2012-07-08
The problem seems to have been solved after I reinstalled FFADO and then Jackd again. I'm now trying to work through some other issues with jackd, but since they don't pertain to this problem i'll close this thread and make a new one later if need be. Thanks for all your help sgx, i hugely appreciate it.

---

