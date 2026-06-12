---
title: "blury graphics after chooseing the installation language."
date: 2011-08-29
forum: Ubuntu Studio
---

### Post by drebbs on 2011-08-29
hi everyone i have studio and i realy want to have it running on my machine. i have xp reinstalled and i have left 15 GB of unpartitoned space on my hard drive to install studio onto. after the dvd boots i get the select language option as soon as i hit a key the hole screen goes all distorted with graphics, the dvd spins at full speed and not alot happens. is there a bios setting or something i have mist? any help from the community would be amazing as i am new to linux but have already fallen for mint 
 
Andy
 
intel core 2 duo E8200
P5N-mx
nvidia geforce 7050
nvidia nfore 610i
2gb ddr

---

### Post by drebbs on 2011-08-29
Hi I've just tried mint and that boots up ok. I still have no idea what's going on. The anyone?

---

### Post by mwinthrop on 2011-08-29
I don't know exactly what is happening, but maybe the boot DVD is corrupt in some way.  I suggest running the scan DVD option if possible (an option right when you boot up, maybe before it asks you about languages and such - I can't remember) and maybe it will detect an error.  Another thought is maybe there was something wrong with the ISO when it downloaded.  There is something like checksum numbers for Ubuntu Studio that could be used to verify the integrity of the ISO file after it is downloaded (see [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)).  I know I had trouble burning a DVD initially, but did not know there was trouble initially.  The first time both the ISO file and the DVD burn of the ISO  were bad for me and it caused a problem part way through the install process, though I got much further than you did.  I ended up throwing my DVD out and burning a new one (after re-downloading the ISO).  The second time I was very careful and succeeded.  However, maybe you did all of this, in which case, I am not sure what might be wrong.

---

### Post by drebbs on 2011-08-30
ive used the same disk to install it onto my dell but ill give i another got. Yeah i cant select the option to check the  checksum or anything as soon as a touch the keyboard i get a weird blurry graphics that fills the hole screen. ill try re burning the DVD anyway. thanks for ur advise

---

### Post by jejeman on 2011-08-30
It's the best to test dvd on drive which will be used to do instalation.
If you have running linux on that machine, live or installed, you can test dvd with md5sum. Just open terminal and go to dvd. Than start the test with
```
md5sum -cw md5sum.txt
```

---

### Post by drebbs on 2011-08-30
Ok ill install mint nd run the terminal for studio and get back to you this afternoon %-)

---

### Post by drebbs on 2011-08-30
OK I burnt another disc at 1x and that didn't work. I ran the code you gave me on the dvd and everything is saying ok %-( its for my music recording. Is there another linux you can think of that's geared towards music or another version? The thanks agin for ur replys

Andy

---

### Post by jejeman on 2011-08-30
Don't know which version you tried, but try 10.04. it works good.
Also, did you tried just to press enter on that blured menu and enter the setup, or computer hangs?
You can always install plain ubuntu and then instal ubuntustudio meta package, or just the apps that you need. Ubuntu studio is absolutley same as ubuntu.

---

### Post by mwinthrop on 2011-08-30
One other crazy idea - if you are able to install Ubuntu Studio on another computer, you could consider pulling the hard drive from the system giving you the blurry graphics and either insert it on the other system (if the connectors are the same) or maybe get a hard disk enclosure and install it.  Maybe that would allow you to complete the installation.  I have been successful in installing Ubuntu Studio on a thumb drive, too, so maybe that would help.

---

### Post by drebbs on 2011-08-31
I was trying 11.04 ill try 10.04 when I get home. As for swapping hdds round that myt b an issue for me as the hdd is partitioned with windows nd a few other things %-( if 10.04 dosnt work ill try Ubuntu on it own and try and download that apps and studio addon. I'm quite new to all this but I'm sure we can figure it out

---

### Post by drebbs on 2011-09-02
It worked! 10.04 went on just fine thank you all for ur input I'm now gona learn how to record music %-)

---

