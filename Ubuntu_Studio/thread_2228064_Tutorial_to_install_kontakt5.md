---
title: "Tutorial to install kontakt5"
date: 2014-06-05
forum: Ubuntu Studio
---

### Post by arthura56 on 2014-06-05
Hi All,

I have a clean install of ubuntustudio with kxstudio repos enabled. I've installed wine and kontakt5 but I have no sound. I think that my first problem is that in the wine configurator under audio my only option is pulseaudio. I see in one of the posts that I should have alsa and jack. How to I get those as options. If anyone knows of a current tutotial on this I would really appreciate it. If not, I'll just try to go one step at a time.

Thanks!

---

### Post by arthura56 on 2014-06-06
Okay, how about this one. I installed wineasio 64 from the kxstudio repositories and I ran this:
sorry, I'm new to this forum and I can't find a way to paste code, so here's the code without looking like it's code:

"a@StudioA:~$ regsvr32 wineasio.dll
Failed to load DLL wineasio.dll
a@StudioA:~$ regsvr64 wineasio.dll
regsvr64: command not found
a@StudioA:~$"

does anyone know what I'm doing wrong here?

Thanks

---

### Post by CrocoDuck on 2014-06-07
Hi! I stopped to use wineasio years ago... but I have found something you could try:

```
wine64 regsvr32 wineasio.dll
```

Have a look at here: [http://www.linuxmusicians.com/viewtopic.php?f=19&t=9666](http://www.linuxmusicians.com/viewtopic.php?f=19&t=9666) and here [http://wiki.cockos.com/wiki/index.php/Installing_and_configuring_WineASIO#Configuring_WineASIO](http://wiki.cockos.com/wiki/index.php/Installing_and_configuring_WineASIO#Configuring_WineASIO) .

---

### Post by arthura56 on 2014-06-07
Thanks CrocoDuck,

That did the trick. By the way, have you stopped doing music on linux.

---

### Post by CrocoDuck on 2014-06-08
> **arthura56 said:**
> By the way, have you stopped doing music on linux.

I will never stop! Down, on my signature, you find my soundcloud. I have very little time to play and record, so I update stuff very slowly, but I am always using my Linux box! I have stopped using wineasio because I stopped liking windows audio software. Too much commercial stuff, very low pro audio specs. I like native linux software much more, open source ones most but even commercial ones. For example:

[https://www.pianoteq.com/](https://www.pianoteq.com/)
[http://www.renoise.com/](http://www.renoise.com/)

Try the demos!

---

