---
title: "ClamTk"
date: 2007-04-12
forum: Server Platforms
---

### Post by gesy on 2007-04-12
Hi,

I have installed ClamAV and ClamTK on my Ubuntu Feisty 64, yesterday, from synaptic.

When I start ClamTk, I get the message: "unable to view ClamAV's information file".

Have you an idea how to fix this problem?

Thanks a lot.

---

### Post by cywhale on 2007-04-13
Same problem here, found a filed bug about this, any solution known?

---

### Post by garion on 2007-04-16
it was working for me a few days ago on feisty, but then i had this problem too after some updates...

i installed avscan for now, another gui that seems to work fine.




> **gesy said:**
> Hi,

I have installed ClamAV and ClamTK on my Ubuntu Feisty 64, yesterday, from synaptic.

When I start ClamTk, I get the message: "unable to view ClamAV's information file".

Have you an idea how to fix this problem?

Thanks a lot.

---

### Post by cywhale on 2007-04-16
Hrm...worked for me until yesterday, too. Tested again a few minutes ago - does not work anymore ?!? Nothing updated, nothing changed?

---

### Post by thecure on 2007-04-16
I get the same error. It asks to run "freshclam -v" as root but doesnt correct the problem. Freshclam shows the data base is good/up to date.

---

### Post by harp2812 on 2007-04-16
Looks like it's been reported... [https://bugs.launchpad.net/ubuntu/+source/clamtk/+bug/96272](https://bugs.launchpad.net/ubuntu/+source/clamtk/+bug/96272)

Unfortunately, I'm not good enough with the perl debugger to track it down... :/

---

### Post by gobbles414 on 2007-04-22
Hi all. I was able to get clamtk working by doing the following...

1: [http://www.linuxquestions.org/linux/answers/Security/Antivirus_Desktop_protection_for_Linux/](http://www.linuxquestions.org/linux/answers/Security/Antivirus_Desktop_protection_for_Linux/)
2: Right click on the Ubuntu symbol in your menu bar and select EDIT MENUS. Go to ACCESSORIES on the left to see a list of programs. Then right-click on VIRUS SCANNER and select properties. Insert the following COMMAND: gksu clamtk %F

I still have two questions:

1) Since the Ubuntu version of clam is always a little behind, is it possible to turn off the virus definitions warning in clamtk?
2) What does the %F do?

---

### Post by St. Coin on 2007-04-22
I had the same problem, I removed and reinstalled all the clamav files and now it is running fine.

---

### Post by sirclaudio on 2007-04-23
Just copy daily.cvd from /usr/share/doc/clamav-freshclam/examples/daily.cvd to /var/lib/clamav/daily.cvd, chown clamav:clamav /var/lib/clamav/daily.cvd, run freshclam again and you're set to go.

---

### Post by sirclaudio on 2007-04-25
>  	Just copy daily.cvd from /usr/share/doc/clamav-freshclam/examples/daily.cvd to /var/lib/clamav/daily.cvd, chown clamav:clamav /var/lib/clamav/daily.cvd, run freshclam again and you're set to go.

And then, maybe not..
The day after, started ubuntu, daily.cvd is gone again, clamtk's error appears again.

---

### Post by sirclaudio on 2007-04-28
It seems that is a glitch of clamtk 2.31 and clamav 0.90, you can see it [[COLOR="Red"]here[/COLOR]]("http://clamtk.sourceforge.net/").

---

### Post by cywhale on 2007-04-28
Works fine here :) Thanks.

---

### Post by jeffrash on 2007-05-04
Thanks for the info, sirclaudio.  That did the trick for me.  Here's a link directly to the test release of 2.32 that fixed the problem for me.

[http://clamtk.sourceforge.net/dev/clamtk-2.32-testing.tar.gz]("http://clamtk.sourceforge.net/dev/clamtk-2.32-testing.tar.gz")

---

### Post by mike g on 2007-06-22
I also obtained the following from clamtk.  I believe this is the same as posted above and it seemed to work well for me. 

wget clamtk.sf.net/clamtk-2.32.gz
gzip -d clamtk-2.32.gz
chmod +x clamtk-2.32
sudo mv clamtk-2.32 /usr/bin/clamtk
(y to overwrite) 


Thank you Dave.


Mike g.

---

