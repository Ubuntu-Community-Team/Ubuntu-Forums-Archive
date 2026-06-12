---
title: "Customised mini Ubuntu distro including fullscreen C64 emulator, audio and LAN"
date: 2014-07-29
forum: Ubuntu, Linux and OS Chat
---

### Post by mariusz-ciszewski on 2014-07-29
Hello


There are dedicated distribution including C64 emulator on the board: 
[http://en.wikipedia.org/wiki/Commodore_OS](http://en.wikipedia.org/wiki/Commodore_OS) 


Unfortunately, it weighs more than 3 GB - which means that its loading via the server (PXE booting over LAN) takes at least several minutes (and maybe more). 


I would like to create my own Ubuntu distribution with as minimal as possible GUI, but with a working network environment (so that was the access to the network location where the roms are available - applications for C64). It would be best, if instead of loading the desktop could be immediately ran the emulator (package [b] vice [/ b]) in full screen mode. 


Targets: 


- The smallest image iso / system loading as soon as possible 
- The smallest hardware requirements 
- Working network environment (access to files rom available on the local network)
- The ability to run via PXE (booting over LAN) 


PS. I read about solutions such as: 
[https://launchpad.net/ubuntu-builder](https://launchpad.net/ubuntu-builder) 
[http://www.linux.com/learn/tutorials/739139-roll-your-own-customized-ubuntu-with-uck](http://www.linux.com/learn/tutorials/739139-roll-your-own-customized-ubuntu-with-uck)


But perhaps they are not the optimum solution ?


Thanks in advance for your help. 


Mariusz

---

### Post by tgalati4 on 2014-07-29
Or, go the other way.  Start with a small distribution and then add the elements needed for C64.  [http://tinycorelinux.net/welcome.html](http://tinycorelinux.net/welcome.html)

A search for C64 in [http://distrowatch.com](http://distrowatch.com) reveals a lot of options.  Which is the smallest?

---

