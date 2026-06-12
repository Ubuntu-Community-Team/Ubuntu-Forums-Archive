---
title: "cant install vista or win 7"
date: 2010-06-19
forum: Virtualisation
---

### Post by Gipsy25 on 2010-06-19
Hello, 

I have a brand new instalation of Ubuntu Lucid (10.04) I decided to install virtualbox and install win7. About 75%-90% (I tried 4 times). I get an error message:

The virtual machine execution may run into an error condition as described below. We suggest that you take an appropriate action to avert the error.
The I/O cache encountered an error while updating data in file "/media/VERBATIM/Virtual machines/virtualbox/defaultVB/HardDrives/windows 7.vdi" (rc=VERR_FILE_TOO_BIG). Make sure there is enough free space on the disk and that the disk is working properly. Operation can be resumed afterwards..
Details:

Error ID: 
CACHE_IOERR
Severity: 
Warning


I cant pass that error ... So I tried 
1) reinstalling ubuntu (no go)
2) I choose a different hdd (no go)
3) got me a 1Tb external hdd (no go)
4) canceled installation, booting from cd and tried to repair ... (no go)

setup:
HDD: 50gb
Ram: 1000mb (1 gb) 
video mem: 20mb (could this be the problem???)


SATA Port 0:
windows 7.vdi (Normal, 50.00 GB)

The same problem with vista ... I was able to install XP and another version of linux .... So I dont know what i'm doing wrong ...

I really dont know what else to do here ... any ideas will be appreciated.

---

### Post by wilee-nilee on 2010-06-19
Your trying to install W7 in a virtual on Lucid with 1 gig of ram, its not going to happen. Not sure of the errors but my version of W7 uses more then half that amount of ram sitting idle.

Really your description is hard to decipher.

---

### Post by Gipsy25 on 2010-06-20
Hi again 

I followed the steps here ... 
[http://twoguystech.com/blog/art/installing-windows-7-beta-suns-virtualbox](http://twoguystech.com/blog/art/installing-windows-7-beta-suns-virtualbox)

[http://www.ioncannon.net/system-administration/82/installing-windows-7-on-virtualbox/](http://www.ioncannon.net/system-administration/82/installing-windows-7-on-virtualbox/)

and they are using 512mb of ram and 20gb for the disk ... the same error I see when trying to install vista ... (32bits) .... 

I will try to add more memory ... maybe thats the problem ... thanks for the TIP ...

---

### Post by wilee-nilee on 2010-06-20
They may say their using 512mb memory, but even lucid runs slower at 512, and this is the important line,**Windows 7 recommend 1 gig of memory**
Stick with XP until you can get another gig of memory, also really to use the virtual you want to set the video memory to 128. 

You might be able to use nlite to get a W7 setup that works.
[http://www.nliteos.com/index.html](http://www.nliteos.com/index.html)

You also are using a link to the beta version of W7 it may have used less memory to run.

You would be better dual booting W7 you have a terabyte HD why are you trying to run this with to little memory it makes no sense.

A 50 gig hd in the computer would allow you to dual boot with no problems and then use the external for back up and for data.

To be honest I suspect this is a cracked W7 anyway, if it was legit you wouldn't be going about it this way, but I am assuming here.

---

### Post by Gipsy25 on 2010-06-20
OK, let me say that i do appreciate the help you provided .... i really do, but I dont think that it should really matter if the software is cracked or not ... at least not to you .. forgive me for saying but i feel like you are lecturing me and there is no reason for that ... 

I asked a question and if you (or anyone else) feels like answering ... go for it ... (i am just trying to learn and gain knowledge ...)

Like you said .. you don't know the kind of software i have or the reasons why i am doing it this way, so because of that you shouldn't even brought it up ... but once again ... thanks for the information I really appreciate the time you are taking to help me and (as i am sure) to others that want to learn here like myself. 

I will take your advice in consideration ... 

Respectfully 

X

---

### Post by wilee-nilee on 2010-06-20
I wasn't lecturing you, on this forum if the mods suspect your working with pirated or illegal software they will close your thread and they will lecture you.

So be careful what you say in defense of using such a thang.

---

