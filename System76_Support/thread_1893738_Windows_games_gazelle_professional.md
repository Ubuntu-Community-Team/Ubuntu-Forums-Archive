---
title: "Windows games gazelle professional?"
date: 2011-12-10
forum: System76 Support
---

### Post by ramus313 on 2011-12-10
so if i had the gazelle professional(i5 2.4ghz, 8 gb ram, NVidia getforce, 500 4gb SSD hybrid), do you guys think i would be able to actually play windows games on a vm on the laptop? if not i guess i could use wine, but i would definitely need to be able to run windows 7 on a vm for academic reasons, would it be almost as smooth as if i was  running windows 7 natively on the laptop? thanks!!

---

### Post by cbennett926 on 2011-12-11
I would consider upgrading to the Serval and throw in some more RAM. That is really what will dictate how well you can run windows. The graphics card will be fine, just expect minimal graphics.

---

### Post by Noah0504 on 2011-12-11
I don't think I would attempt to play any serious Windows games in a VM.  You're not going to have great 3D support.  If anything, I would try Wine or even a dual boot environment.  Having said that, I think the specs you listed would be more the adequate.  And if you're not trying to do 3D, you would be able to run Windows 7 very smoothly in a VM.

---

### Post by Bufke on 2011-12-11
Indeed VM's will not do games. Don't waste you time and money.

Skyrim plays well in wine on my Gazelle. Don't expect anywhere close to the performance you would get in native Windows though.

---

### Post by gman16000 on 2011-12-11
Guess it would depend on what kind of games.  I have the gazelle and I'm using a dual boot and it works great for intense first person shooters that require major graphics processing.  This would not work on a VM because of the 3D graphics.

The problem is, you will not be able to run the Nvidia drivers in the guest vm and this will limit the kinds of games you can play. [http://communities.vmware.com/message/1253409](http://communities.vmware.com/message/1253409)

---

### Post by ramus313 on 2011-12-11
> **gman16000 said:**
> Guess it would depend on what kind of games.  I have the gazelle and I'm using a dual boot and it works great for intense first person shooters that require major graphics processing.  This would not work on a VM because of the 3D graphics.

The problem is, you will not be able to run the Nvidia drivers in the guest vm and this will limit the kinds of games you can play. [http://communities.vmware.com/message/1253409](http://communities.vmware.com/message/1253409)

how did you dual boot with windows? did system 76 do it for you? i thought it was difficult to dual boot when ubuntu was installed first

---

### Post by Noah0504 on 2011-12-11
Well, you can easily reinstall Windows on the entire drive, then install Ubuntu and have it do the dirty work for you.  However, if you don't want to go that route, you can follow the guide here: [http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

That will allow you to install Windows after Ubuntu is already installed.  System76 will not do it for you.

---

### Post by Lee_Machine on 2011-12-12
Depending on the game don't bother with WINE, and running games in a VM is out of the question. 

Just dual boot with Win7. It's quite easy to do. It would make it much easier if the Windows MBR didnt erase GRUB. Follow the OP link for directions on reinstalling GRUB. 

I've dual booted with all my S76 laptops. Was playing Skyrim on a Panp7. 

Back to WINE, I used it for years playing various games, mostly WoW, but I got tired of the performace loss, and/or not working. For gaming dual boot is the only way.

---

### Post by gman16000 on 2011-12-12
> **ramus313 said:**
> how did you dual boot with windows? did system 76 do it for you? i thought it was difficult to dual boot when ubuntu was installed first

i'm using two separate physical drives. but if you did stay on one drive, i dont think it would be hard. you could just resize the partition and install it. i bought my gazelle with 11.04 on there. when i did the normal 11.10 upgrade, it messed up my computer so i 100% blew away whatever system76 had on there and just treated the computer like a normal linux install.  worked great.

---

