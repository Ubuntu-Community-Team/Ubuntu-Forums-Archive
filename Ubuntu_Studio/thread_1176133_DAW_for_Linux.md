---
title: "DAW for Linux?"
date: 2009-06-02
forum: Ubuntu Studio
---

### Post by brncao on 2009-06-02
I was wondering if there are any DAW software that is made for Linux. Whether it be open source or commercial. And do I have to worry about latency?

---

### Post by logos34 on 2009-06-02
[Ardour]("http://ardour.org/download") (2.3 in the ubuntu repo)

sudo apt-get install ardour
> 
And do I have to worry about latency?

not if you use ubuntustudio with linux-rt kernel

it's what I use (64-bit)

---

### Post by brncao on 2009-06-02
Ubuntu Studio huh? Gonna go download it then :) But what's the difference between Ubuntu Studio and the regular Ubuntu besides the included software? Will I lose out on anything (from regular Ubuntu) if I just stick with Ubuntu Studio?

---

### Post by logos34 on 2009-06-02
diff is mainly the real-time/low-latency kernel, the extra a/v, graphics pkgs, + diff desktop theme.  Basically, not much...you can even upgrade from regular ubuntu to studio, choosing either just the theme, and/or the extra pkgs

[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

---

### Post by brncao on 2009-06-02
Thanks for your help. I've checked out other distros as well. Musix GNU/Linux, JackLab Audio, and 64 Studio.

---

### Post by Becker-BR on 2009-06-02
Well.
I am new in the world of the linux in audio, but I already noticed that:
I already installed all the distros that you mentioned.  
  
- Musix  
It is a good distro, the more it completes, meantime of difficult installation, in my case the system didn't not recognize my keyboard of the notebook, but the version this to suffer a new version and I intend to test soon;  
- JAD - Jack Lab Áudio:  
It is an old distribution 2007, it seems that this discontinued, it is of the line opensuse, it good resources, but the softwares are old;  
- Studio 64  
It is a very light and functional distribution, but with few softwares;  
  
Of the whole research that I already did, including Dynebolic, Purebolic, the most current and functional distro is the one of Ubuntu Studio.  
However I would recommend first to install normal Ubuntu, and to install all the programs that you want, for later tranformer in Ubuntu Studio.  
The important in any distribution is Kernel-RT (realtime), because normal Kernel of Linux, is not good for the audio production, because most of the programs only works using the jackcontrol that demands a kernel with RT. 
Jack control is a type of bridge that is to connect the several audio programs.
It is a program of difficult configuration, and the measure that you are going connecting more softwares the system it is slow and the problem of the latencia appears. 
One of the few programs of Linux for audio, that doesn't demand Kernel-RT, and that works satisfactorily in normal Kernel it is LMMS (Linux Multimedia Studio, that gets to be almost a DAW.
Which your operating system now in use?

---

### Post by brncao on 2009-06-02
Under Distrowatch, it lists JAD as still active. I'm running the regular Ubuntu (off the live CD) as I'm typing this. I'm still using Windows Vista.

Edit: oh wait you're right. I went on their forums and the guy is closing JAD down this month. I'm gonna have to cross JAD off the list (until someone picks it up). So that leaves 3 distros.

---

