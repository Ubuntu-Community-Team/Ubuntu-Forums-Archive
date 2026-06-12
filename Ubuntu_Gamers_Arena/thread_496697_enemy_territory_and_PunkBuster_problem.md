---
title: "enemy territory and PunkBuster problem"
date: 2007-07-09
forum: Ubuntu Gamers Arena
---

### Post by GNUtoo on 2007-07-09
i have the following messages in enemy territory's console at startup(pressing ~ at startup):
PunkBuster Client: PunkBuster Client: (V1.152 | A0) Ebavked
PunkBuster Client: Gane Version [ET 2.60b linux-i386 May 8 2006]

_what's my problem:_
when i connect to a server it is fine until i join the game and play a bit
then i have this error:
Server Disconnected - has been kicked via PunkBuster (for 1 minute) ...
Violation (GAME INTEGRITY) #20004


_how did i install it:_
i followed this howto:[http://ubuntuforums.org/archive/index.php/t-5246.html](http://ubuntuforums.org/archive/index.php/t-5246.html)
i downloaded the enemy territory
i downloaded the zip file for upgrading to the b version
then i followed the PunkBuster update procedure

---

### Post by alterpinguin on 2007-07-19
> 
Integrity Violations:
When PunkBuster is unable to verify that a player's gaming environment is functioning properly and/or has not been alterred, an Integrity violation is raised. This also involves the detection of modified game or PunkBuster files. These violation numbers are between 10000 and 29999.

you should check some more pb-infos in the web like:
[http://www.punksbusted.com](http://www.punksbusted.com)
and its forums

---

### Post by go_beep_yourself on 2007-12-09
> **GNUtoo said:**
> 
Server Disconnected - has been kicked via PunkBuster (for 1 minute) ...
Violation (GAME INTEGRITY) #20004


I have the same problem. Did you figure out how to solve it?

---

### Post by ahaslam on 2007-12-17
*From linuX-gamers:*
> You might want to run the script pbweb.x86 in your ~/.etwolf/pb directory.

To be more precise:

```
cd [et-install-directory]/pb
wget [http://www.evenbalance.com/downloads/et/pbsec.htm](http://www.evenbalance.com/downloads/et/pbsec.htm)
wget [http://www.evenbalance.com/downloads/et/pbsecsv.htm](http://www.evenbalance.com/downloads/et/pbsecsv.htm)
chmod u+x pbweb.x86
./pbweb.x86
cp pbweb.x86 ~/.etwolf/pb/
cd ~/.etwolf/pb/
./pbweb.x86 
```


PS. It takes a while to update, get a coffee ;)

---

### Post by Tyler H on 2008-09-10
I'm getting no luck with this fix

---

### Post by go_beep_yourself on 2008-09-17
You could try updating your punkbusters with this.

[http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)

---

### Post by Zyphrexi on 2008-09-23
yeah someone posted something like that in a similar thread, which fixed it for me. +1 on updating pb.

---

### Post by NewJack on 2008-09-23
> **go_beep_yourself said:**
> You could try updating your punkbusters with this.

[http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)

After downloading this to the Desktop, do you just run it from there or do you need to place this in a "PB" folder for the game and then run it?

Don't mind me, I am new to gaming in Ubuntu.  :)

In windows, I just DL'ed the PB .exe file to the Desktop and ran it from there and just added which games I had installed on my system.  Is this the same for the Linux .run file?

---

### Post by enz1m3 on 2008-09-24
> cd [et-install-directory]/pb
wget [http://www.evenbalance.com/downloads/et/pbsec.htm](http://www.evenbalance.com/downloads/et/pbsec.htm)
wget [http://www.evenbalance.com/downloads/et/pbsecsv.htm](http://www.evenbalance.com/downloads/et/pbsecsv.htm)
chmod u+x pbweb.x86
./pbweb.x86
cp pbweb.x86 ~/.etwolf/pb/
cd ~/.etwolf/pb/
./pbweb.x86

Worked for me!

---

### Post by NewJack on 2008-09-24
Gonna give that a go when I get home tonight.  :)

---

### Post by NewJack on 2008-09-24
> **enz1m3 said:**
> 
cd [et-install-directory]/pb
wget [http://www.evenbalance.com/downloads/et/pbsec.htm](http://www.evenbalance.com/downloads/et/pbsec.htm)
wget [http://www.evenbalance.com/downloads/et/pbsecsv.htm](http://www.evenbalance.com/downloads/et/pbsecsv.htm)
chmod u+x pbweb.x86
./pbweb.x86
cp pbweb.x86 ~/.etwolf/pb/
cd ~/.etwolf/pb/
./pbweb.x86
Worked for me!

Thanks, it worked for me also. No kicks from servers now. 

One question though... Will PB update on it's own now, or do I have to go through the above steps again to update it?

---

### Post by frodon on 2008-10-24
Just jumping here to tell you that the right (and simple) way to update/re-install PB is just to use the tool they provide PBSetup :
[http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)

I believe pbweb is also unsupported now.

---

