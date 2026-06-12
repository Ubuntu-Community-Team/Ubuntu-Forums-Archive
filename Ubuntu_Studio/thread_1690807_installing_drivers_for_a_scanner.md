---
title: "installing drivers for a scanner"
date: 2011-02-19
forum: Ubuntu Studio
---

### Post by MFoxx on 2011-02-19
p { margin-bottom: 0.08in; }  Hello all “residents” of the forum. I like Ubuntu very much. I have Ubuntu Studio.  I'm  a newbie. I want to install drivers for my scanner:   
 [COLOR=#0000ff]brscan2-0.2.5-1.i386.deb[/COLOR] AND [COLOR=#0000ff][SIZE=3]brscan-skey-0.2.1-1.i386.[/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]deb[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]Unfortunately I fail every time I try to do it. That's what I can see in my terminal:[/SIZE][/COLOR]
 [COLOR=#008000]r@ubuntuPolich-34095:~/Desktop$ sudo apt-get install /Desktop/r/brscan2-0.2.5-1.i386.deb [/COLOR]
 [COLOR=#008000]Reading package lists... Done [/COLOR]
 [COLOR=#008000]Building dependency tree        [/COLOR]
 [COLOR=#008000]Reading state information... Done [/COLOR]
 [COLOR=#008000]E: Unable to locate package /Desktop/r [/COLOR]
 [COLOR=#008000][SIZE=3]r@ubuntuPolich-34095:~/Desktop$  [/SIZE][/COLOR]
 

 [COLOR=#008000][COLOR=#ff0000][SIZE=4]**r **[/SIZE][/COLOR][COLOR=#000000][SIZE=3]is my username.[/SIZE][/COLOR][/COLOR]
 

 [COLOR=#000000][SIZE=3]So, how can I create a valid dependency and what command should I write in a terminal?[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]*Just give me an example*[/SIZE][SIZE=3]. I know a little bit about creating dependencies but the only result I get :[/SIZE][/COLOR]
 [COLOR=#000000]“ [COLOR=#008000][SIZE=3]Unable to locate package[/SIZE][/COLOR][SIZE=3]”[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]Thanks in advance, [/SIZE][SIZE=3]friends.[/SIZE][/COLOR]

---

### Post by wojox on 2011-02-19
Just open your terminal again and go into your Desktop and run:

```
sudo dpkg -i brscan2-0.2.5-1.i386.deb
```

---

### Post by MFoxx on 2011-02-19
Thanks a lot. It worked like a Swiss watch. I mean I've managed to install both drivers. Then I checked the installation.
It seems to be right:

   @ubuntuPolich-34095:~$ dpkg -l | grep Brother

ii  brscan-skey                           0.2.1-3                                           Brother Linux scanner S-KEY tool

ii  brscan2                               0.2.5-1                                           Brother Scanner Driver

r@ubuntuPolich-34095:~$ dpkg -l | grep Brother

ii  brscan-skey                           0.2.1-3                                           Brother Linux scanner S-KEY tool

ii  brscan2                               0.2.5-1                                           Brother Scanner Driver

r@ubuntuPolich-34095:~$

But Xsane reads the following:
 Failed to open device "brother2;bus3;dev1/: invalid argument

Can anybody help me?

Thanks in advance.

---

