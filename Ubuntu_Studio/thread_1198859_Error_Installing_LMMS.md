---
title: "Error Installing LMMS"
date: 2009-06-28
forum: Ubuntu Studio
---

### Post by thetimewarp on 2009-06-28
First off, let me say that I'm a total n00b with Ubuntu and Linux (as in, this is my second day using it), so be patient with me.  Also, I'm sorry if there's a better place for me to post this; since I'm new with Ubuntu, I don't really know the 'places to go', per se.  Just let me know and I'll delete this post.

Anyway, about 87% through the intial install of LMMS, I get this message:
[ 87%] [COLOR=Green]Building CXX object plugins/midi_import/CMakeFiles/midiimport.dir/midi_import.o[/COLOR]
/home/jess/lmms/plugins/midi_import/midi_import.cpp: In member function ‘virtual bool midiImport::tryImport(trackContainer*)’:
/home/jess/lmms/plugins/midi_import/midi_import.cpp:97: error: ‘class configManager’ has no member named ‘defaultSoundfont’
make[2]: *** [plugins/midi_import/CMakeFiles/midiimport.dir/midi_import.o] Error 1
make[1]: *** [plugins/midi_import/CMakeFiles/midiimport.dir/all] Error 2
make: *** [all] Error 2

What should I do to fix this?

---

### Post by mcduck on 2009-06-28
Simple, you should be using LMMS from Ubuntu's repositories, or install it with a .deb package instead of trying to compile it from source code.

[Click to install LMMS]("apt://lmms")

Or open a terminal and run this command:
```
sudo apt-get install lmms
```
..or go to Applications->Add/Remove... or System->Administration->Synaptic Package Manager, search for LLMS & install it.

You may also want to read this: [Installing software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")

edit: If you want newer version of LMMS than what is available in Ubuntu's own repositories, try this: [https://launchpad.net/~tobydox/+archive/ppa]("https://launchpad.net/~tobydox/+archive/ppa")

---

