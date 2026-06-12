---
title: "Ubuntu Studio Software Center Stopped Working"
date: 2016-10-10
forum: Ubuntu Studio
---

### Post by gccradio2016 on 2016-10-10
I am having a problem with the Ubuntu Studio Software Center.  It worked good last night after I did a new installation of Ubuntu Studio 16.04.1 LTS, but when I fell asleep, and left the laptop on, it still worked 
ok during when I was a sleep.  When woke up and opened up the laptop, I went to Ubuntu Studio Software Center and typed in Bleach Bit ,then when I clicked on Install, the software said it was pending, so I realized that my laptop was offline for some odd reason.  So I did a  reboot, logged in, and went to Ubuntu Studio Software Center, and the sad thing is that it won't open or start. So I went to Synaptic Package Manager, and keyworded Bleach Bit, and I was able to install from that package manager, but still I am not able to open up Ubuntu Studio Software center, and I wish I can get the Software Center reinstalled with some solution that would help me get it back.   I have noticed that Ubuntu Studio Software center runs quite slow than other applications on Ubuntu Studio.  

Is there anything that be done to get this fixed? 

Adam Ebel  
Virginia Beach, Virginia

---

### Post by CrocoDuck on 2016-10-12
> **gccradio2016 said:**
> 
Is there anything that be done to get this fixed? 


Not sure about it. You could try to [purge]("http://askubuntu.com/questions/231562/what-is-the-difference-between-apt-get-purge-and-apt-get-remove") software center through apt-get, but I think the system will not like it much. The idea would be to purge it and reinstall it, but I am afraid [software-center]("http://packages.ubuntu.com/xenial/software-center") might be part of some meta package or similar. If you want to try:
```

sudo apt-get purge software-center

```

Reinstall with (after a reboot):
```

sudo apt-get install software-center

```

During the purge phase _have a look at the console messages_: if the purge means that other packages you think you need will be removed, maybe you are better not to purge.

I think ti will be safer to try to reinstall software-center without purging it first, but probably not effective. In this case, just run the second command.

 Software center has always been slow and buggy in my experience. I once risked to have the package database corrupted because of it, during Matlab compatibility package installation. I am afraid it is not much of a workaround, but for the time being I would suggest to stick to Synaptic or the good old terminal and avoid Software Center altogether.

---

