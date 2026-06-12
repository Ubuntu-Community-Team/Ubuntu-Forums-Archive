---
title: "Log Out"
date: 2012-04-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Miykel on 2012-04-30
G'Day; Still having trouble with  "log Out" when i try I just get a black screen, no curser, nothing, have to hit restart to log in again, any thoughts would be appreciated.
Regards Miykel

---

### Post by dino99 on 2012-05-01
python3 will push some headaches with this early alpha; better to stay with Precise if you're afraid with breakages

---

### Post by Miykel on 2012-05-02
I was under the impression that the whole point of the exercise was to break something then report it, plus I had the same problem with Precise and couldn't get any answer, the whole OS just went bang when I tried to boot, tried recovery mode etc. so I guess a new install is called for, I'll see how I get on with  log out  with the new install.
Regards Miykel

---

### Post by ventrical on 2012-05-02
> **Miykel said:**
> I was under the impression that the whole point of the exercise was to break something then report it, plus I had the same problem with Precise and couldn't get any answer, the whole OS just went bang when I tried to boot, tried recovery mode etc. so I guess a new install is called for, I'll see how I get on with  log out  with the new install.
Regards Miykel

Hi Miykel,

What type of PC hardware do you have?

---

### Post by Miykel on 2012-05-02
G'Day;  The mobo is a Gigabyte, the pcu is an i5 intel quadcore, the graphics card is a gigabyte 2 gig. with gt 4800 nVidia drives. 2 X 500 gig HDD's
Regards Miykel

---

### Post by ventrical on 2012-05-02
> **Miykel said:**
> G'Day;  The mobo is a Gigabyte, the pcu is an i5 intel quadcore, the graphics card is a gigabyte 2 gig. with gt 4800 nVidia drives. 2 X 500 gig HDD's
Regards Miykel

The reason I  ask is that it sounds like an ACPI problem. I have had some older machines behave is this exact way but apparently you have a newer machine - but I am just suggesting that this may be  a problem and enabling or disabling ACPI might be a remedy and/or of course it may be another config problem with graphics driver.

---

### Post by Miykel on 2012-05-02
G'Day; I have no idea why it's like this, it worked fine in 11.** but from the time I went to 12.04, fresh install from disc, I've had no log out. now I'm not sure what's going on, when I tried to boot earlier, after being away most of the day, got just a black screen so I done a fresh install, which was fine then I done an upgrade to QQ and now I just get the bash screen, will delete the partition and try again, have W7 & W8 on other partitions and they work fine, all very peculiar.
Regards Miykel

---

### Post by ventrical on 2012-05-02
> **Miykel said:**
> G'Day; I have no idea why it's like this, it worked fine in 11.** but from the time I went to 12.04, fresh install from disc, I've had no log out. now I'm not sure what's going on, when I tried to boot earlier, after being away most of the day, got just a black screen so I done a fresh install, which was fine then I done an upgrade to QQ and now I just get the bash screen, will delete the partition and try again, have W7 & W8 on other partitions and they work fine, all very peculiar.
Regards Miykel


There was a big problem with a new QQ update. The libxfont1.  Did you get that fix? If not .. here it is..

[http://ubuntuforums.org/showpost.php?p=11894273&postcount=3](http://ubuntuforums.org/showpost.php?p=11894273&postcount=3)

---

### Post by Miykel on 2012-05-02
G'Day;  Thanks for that Ventrical, I've just got the OS reloaded, upgraded the Xorg server and Nvidia drivers, I'll see if I can do the QQ upgrade tomorrow, midnight here now, 
Regards Miykel

---

### Post by cariboo on 2012-05-02
Have you tried using GDM instead of lightdm?

---

### Post by Miykel on 2012-05-02
I tried GDM just before the whole thing went bang, made no difference, just tried log out again with this fresh install but still no good, now I just get a black screen for a few minutes then the PC shuts down ???  one of lifes little mysteries I guess. It's not important, as far as it goes, just something doesn't work correctly so it's like a sore tooth  LOL.
  BTW. I'm just about to do the QQ upgrade, that fix you posted, I assume I run that after the upgrade/update before I reboot. ??
Regards Miykel

---

### Post by ventrical on 2012-05-02
> **Miykel said:**
> I tried GDM just before the whole thing went bang, made no difference, just tried log out again with this fresh install but still no good, now I just get a black screen for a few minutes then the PC shuts down ???  one of lifes little mysteries I guess. It's not important, as far as it goes, just something doesn't work correctly so it's like a sore tooth  LOL.
  BTW. I'm just about to do the QQ upgrade, that fix you posted, I assume I run that after the upgrade/update before I reboot. ??
Regards Miykel


 Yes .. you can do it that way.  Apparently it has been fixed.  I just blocked it in synaptic and then updated an upgraded Quantal system.  I am just about to do another upgrade on a Dell Dimension 3100.

  I'll be back to explain what I did but the conventional solution posted by pressurman was the best workaround..

---

### Post by Miykel on 2012-05-02
G'Day;  Just did the upgrade/reboot worked fine

miykel@miykel:~$  lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu quantal (development branch)
Release:    12.10
Codename:    quantal
miykel@miykel:~$ 

I noticed when I was poking round the Xorg edgers page there is a release there for QQ have you looked at that ??

Regards Miykel

 Just looked in my sources.list and I found

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) quantal main
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) quantal main

Cruisin'     <M>

---

### Post by ventrical on 2012-05-02
> **Miykel said:**
> G'Day;  Just did the upgrade/reboot worked fine

miykel@miykel:~$  lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu quantal (development branch)
Release:    12.10
Codename:    quantal
miykel@miykel:~$ 

I noticed when I was poking round the Xorg edgers page there is a release there for QQ have you looked at that ??

Regards Miykel

 Just looked in my sources.list and I found

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) quantal main
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) quantal main

Cruisin'     <M>

Haven't looked at that at the ppa  but the current one is still buggered up quite a bit.  I got black screen from the Dell upgrade and now I have to manually enter that downgrade code :)

Edit:

Ok .. I'm back in the saddle again .. now uprgading to the 3.4 .x-x kernel. So thats 4 machines now with the Quantal conversion.

---

### Post by Miykel on 2012-05-03
How, where and when did you enter the downgrade code, when mine went bang I just got a black screen and no way of entering anything,
 BTW , re; the point of this post, log out still doesn't do anything. 
Regards Miykel

---

### Post by ventrical on 2012-05-03
> **Miykel said:**
> How, where and when did you enter the downgrade code, when mine went bang I just got a black screen and no way of entering anything,
 BTW , re; the point of this post, log out still doesn't do anything. 
Regards Miykel


  When I rebooted  I just held down the shift-key and then I got the GRUB menu and was able to choose the recovery option. Were you able to get the GRUB menu on your black-screen previously (or had you tried that)?

From there you can drop to root (or choose resume as which I did and it bumped me to a terminal prompt).[I had to print out the code because the Dell is across the room at another workstation] , gives me an excuse to use my printer :)

---

### Post by ventrical on 2012-05-03
> **Miykel said:**
> G'Day;  Just did the upgrade/reboot worked fine

miykel@miykel:~$  lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu quantal (development branch)
Release:    12.10
Codename:    quantal
miykel@miykel:~$ 

I noticed when I was poking round the Xorg edgers page there is a release there for QQ have you looked at that ??

Regards Miykel

 Just looked in my sources.list and I found

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) quantal main
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) quantal main

Cruisin'     <M>

Yes . I had seen that harry33 had posted the link to that fix. Thanks.

---

### Post by Miykel on 2012-05-03
When everything went bang, I could get into the recovery mode but I don't know what the codes are to downgrade, sure would appreciate it if you could let me know what they are, no doubt they will come in handy.
 Those Xorg ppa's in my previous post, I only added the precise ppa's, to my sources.list and they seemed to be updated with the upgrade, bit handy.   Had another game with adding ppa's to my sources.list to install SIR and it worked fine...damn Something new...
Regards Miykel

---

