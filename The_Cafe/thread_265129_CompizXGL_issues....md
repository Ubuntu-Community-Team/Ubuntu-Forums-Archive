---
title: "Compiz/XGL issues..."
date: 2006-09-25
forum: The Cafe
---

### Post by stooo on 2006-09-25
I know there's a Beryl release due soon, but I was basically wondering if anyone with an ATI 9800 Pro has had as much of a problem as I have trying to get Compiz to work.

I understand it's alpha software, but I've yet to see anyone else completely failing to get it to work.

I've tried the official ATI drivers and generic ones. The generic ones in my experience got the fglrx enabled easily.

I've tried multiple tutorials on getting Compiz to work. Most current ones seem to be based around this one: [http://www.tectonic.co.za/view.php?id=1153](http://www.tectonic.co.za/view.php?id=1153)

All is okay untill I modify the /etc/gdm/gdm.conf-custom file, then when rebooting I get the xserver start, login window appears, then xserver starts again, then login window, then it loops once more so I get a corrupted looking display.

I know of many other people that have done this blissfully with no problems. Any ideas what on earth I can do to get compiz working successfully.

I have a Pentium 4 2.4Ghz, 1Ghz RAM and a HIS Digital 9800 Pro. Any help would be greatfully appreciated.

I have all the .deb files relating to the above link downloaded so I can easily re-install them.

Thanks.

Stoo

---

### Post by maniacmusician on 2006-09-25
this is so far into the wrong section, it really is not even funny. please look around before posting.

---

### Post by hanzomon4 on 2006-09-25
I don't have an ati so I can't help much, but I would suggest posting at [beryl-project.org formerly known as compiz.net]("http://forum.beryl-project.org/"). 

I'm quiet sure that you can find good help there, also you should know that compiz-quinn is undergoing a fork.. Its all explained at [beryl-project.org]("http://forum.beryl-project.org/") 

One more tip look in your X log files mine is /var/log/Xorg.93.log or Xorg.93.log.old ,if you restored your gdm.config-custom backup file, for errors.

I would also ask for this thread to be moved somewhere it would get more "attention" ;)

Oh , and um Welcome to ubuntuforums

---

### Post by prizrak on 2006-09-25
It's beta software you are supposed to have problems :)

---

### Post by hanzomon4 on 2006-09-25
True, but trust me you can get it working. I've borked X in so many ways trying different stuff, and most times it wasn't the software.. Miss read directions or not adding a few lines in some config file somewhere was usually the culprit.

But I would have to agree with prizrak, You will have some problems that are related to the software.. If you can spend the time working them out great, if not save your self some unnecessary headaches.  

So you can get to work but like others here will tell you it might be "frustrating" at times.

---

### Post by maniacmusician on 2006-09-25
i have an ati card too, and i have to say that it does suck. with the proprietary drivers i can't even enable composite, and the open source drivers work fairly well but composite still doesn't work...so i didnt have the heart to try for xgl. i didnt really get many replies when i posted on here ([http://www.ubuntuforums.org/showthread.php?t=245592](http://www.ubuntuforums.org/showthread.php?t=245592) ), so i'm going to assume its the drivers. I hope that edgy and aiglx will fix some of my problems.

ps: wasnt trying to spam my thread, its really old, just an example of ati woes.

---

