---
title: "amsynth not running on 8.10"
date: 2008-10-31
forum: Ubuntu Studio
---

### Post by Capoeira on 2008-10-31
i've installed amsynth but can't execute. even worse since dssi-vst is not working too.
here is konsole-output:

------------------------

~$ amsynth
amSynth 1.2.0                  
Copyright 2001-2006 Nick Dowell and others.
amSynth comes with ABSOLUTELY NO WARRANTY  
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details   
loaded & initialised libjack.so :)                           
*** buffer overflow detected ***: amsynth terminated         
======= Backtrace: =========                                 
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7285558]
/lib/tls/i686/cmov/libc.so.6[0xb7283680]                     
/lib/tls/i686/cmov/libc.so.6[0xb7282d68]                     
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0xc8)[0xb71f8a18]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x133)[0xb71caac3]     
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xa7)[0xb7282e17]    
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0xb7282d5d]     
amsynth[0x806eb53]                                               
======= Memory map: ========                                     
08048000-08095000 r-xp 00000000 08:03 189562     /usr/bin/amsynth
08095000-080ba000 rw-p 0004c000 08:03 189562     /usr/bin/amsynth
080ba000-080bb000 rw-p 080ba000 00:00 0                          
09c0c000-0a006000 rw-p 09c0c000 00:00 0          [heap]          
b40d5000-b416a000 r--p 00000000 08:03 42611      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b416a000-b416e000 r-xp 00000000 08:03 8955       /usr/lib/libXtst.so.6.1.0                          
b416e000-b416f000 rw-p 00003000 08:03 8955       /usr/lib/libXtst.so.6.1.0                          
b416f000-b41ba000 r-xp 00000000 08:03 22798      /usr/lib/libQtSvg.so.4.4.3                         
b41ba000-b41bb000 r--p 0004b000 08:03 22798      /usr/lib/libQtSvg.so.4.4.3                         
b41bb000-b41bc000 rw-p 0004c000 08:03 22798      /usr/lib/libQtSvg.so.4.4.3                         
b41bc000-b41fe000 r-xp 00000000 08:03 77190      /usr/lib/libQtXml.so.4.4.3                         
b41fe000-b41ff000 r--p 00041000 08:03 77190      /usr/lib/libQtXml.so.4.4.3                         
b41ff000-b4200000 rw-p 00042000 08:03 77190      /usr/lib/libQtXml.so.4.4.3                         
b4200000-b420f000 r-xp 00000000 08:03 2373       /lib/libbz2.so.1.0.4                               
b420f000-b4210000 r--p 0000f000 08:03 2373       /lib/libbz2.so.1.0.4                               
b4210000-b4211000 rw-p 00010000 08:03 2373       /lib/libbz2.so.1.0.4                               
b4211000-b430d000 r-xp 00000000 08:03 22889      /usr/lib/libQtNetwork.so.4.4.3                     
b430d000-b4310000 r--p 000fb000 08:03 22889      /usr/lib/libQtNetwork.so.4.4.3                     
b4310000-b4311000 rw-p 000fe000 08:03 22889      /usr/lib/libQtNetwork.so.4.4.3                                                                                        
b4311000-b4312000 rw-p b4311000 00:00 0                                                                                                                                
b4312000-b4664000 r-xp 00000000 08:03 18245      /usr/lib/libkdeui.so.5.1.0                                                                                            
b4664000-b4676000 r--p 00351000 08:03 18245      /usr/lib/libkdeui.so.5.1.0                                                                                            
b4676000-b467c000 rw-p 00363000 08:03 18245      /usr/lib/libkdeui.so.5.1.0                                                                                            
b467c000-b467d000 rw-p b467c000 00:00 0                                                                                                                                
b467d000-b46e9000 r-xp 00000000 08:03 77178      /usr/lib/libQtDBus.so.4.4.3                                                                                           
b46e9000-b46ea000 r--p 0006b000 08:03 77178      /usr/lib/libQtDBus.so.4.4.3                                                                                           
b46ea000-b46eb000 rw-p 0006c000 08:03 77178      /usr/lib/libQtDBus.so.4.4.3                                                                                           
b46eb000-b48fa000 r-xp 00000000 08:03 18242      /usr/lib/libkdecore.so.5.1.0                                                                                          
b48fa000-b4901000 r--p 0020e000 08:03 18242      /usr/lib/libkdecore.so.5.1.0                                                                                          
b4901000-b4904000 rw-p 00215000 08:03 18242      /usr/lib/libkdecore.so.5.1.0                                                                                          
b4908000-b490c000 r-xp 00000000 08:03 73189      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so                                                                
b490c000-b490d000 r--p 00003000 08:03 73189      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so                                                                
b490d000-b490e000 rw-p 00004000 08:03 73189      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so                                                                
b490e000-b4918000 r--p 00000000 08:03 154102     /usr/share/locale-langpack/pt_BR/LC_MESSAGES/glib20.mo                                                                
b4918000-b4947000 r-xp 00000000 08:03 14553      /usr/lib/kde4/plugins/styles/oxygen.so                                                                                
b4947000-b4948000 r--p 0002e000 08:03 14553      /usr/lib/kde4/plugins/styles/oxygen.so                                                                                
b4948000-b4949000 rw-p 0002f000 08:03 14553      /usr/lib/kde4/plugins/styles/oxygen.so                                                                                
b4949000-b494f000 r--s 00000000 08:03 28604      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2                                                    
b494f000-b4952000 r--s 00000000 08:03 28578      /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2                                                    
b4952000-b4955000 r--s 00000000 08:03 28568      /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2                                                    
b4955000-b4956000 r--s 00000000 08:03 28539      /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2                                                    
b4956000-b4959000 r--s 00000000 08:03 22101      /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2                                                    
b4959000-b4960000 r--s 00000000 08:03 153533     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2                                                    
b4960000-b4963000 r--s 00000000 08Cancelado                                                                                                                            

----------------------------

---

### Post by thorgal on 2008-10-31
man, you seem to have tons of problems with 8.10. Have you considered switching to another distro ? If relevant, I can tell you that I tried Ubuntu Studio one year ago when I built up my linux DAW. Sure I have the habit of tweaking and upgrading my linux boxes outside the rigid path of APT, but it turned out Ubuntu was very unstable. I thought it was a user friendly debian. It's not. So I went back to my good old debian sid and forgot all about the "illusion" of safety and comfort Ubuntu can provide. I am sure it is not an illusion when it comes to ordinary desktop / laptop usage. But a DAW is another thing and requires various tweaks and maintenance that does not come out of the box. But that's just my experience and I am also sure many UStudio users out there are more than happy with it.

---

### Post by Capoeira on 2008-10-31
Well, didn't had that problems on hardy.
before installing intrepid i was searching for another distro ported for audioproduction but didn't find any wich i liked. I use Kubuntu. And i want a KDE4-Distro.

I am quite a beginner on Linux (6 month).
I started with Kurumin (brazilian Distro based on Debian-Stable (now based on Kubuntu))
But i wanted more aktualized Software, and switched to Kubuntu (wich is kind of a "testing"-Distro??)
But i am thinking now of going back to a "stable" Distro.

I am new in Audio-Produktion too. I have only one work wich i made last week. Who likes: [http://www.myspace.com/fabiocapoeiraes](http://www.myspace.com/fabiocapoeiraes) (the song is made only with Rosegarden, Hydrogen and ZynAddSubFX - microphone is really ****)

---

### Post by Capoeira on 2008-11-05
well, I forgot to thank you Thorgal. You made me try to find another distro for me.
I'm now on JackLab/openSuse11, and I'm verry happy with it. All my problems are gone, dssi-vst is even in the repositrys :-)

---

