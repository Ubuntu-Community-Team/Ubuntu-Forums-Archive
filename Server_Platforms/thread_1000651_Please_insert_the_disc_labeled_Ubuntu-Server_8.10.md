---
title: "Please insert the disc labeled: Ubuntu-Server 8.10"
date: 2008-12-03
forum: Server Platforms
---

### Post by Nicklas57 on 2008-12-03
Hi,

I have a Dell 470 and trying to install the Ubuntu server edition v8-10, it goes all fine with installing untill it is doing the part of installing the base system, it then comes up with the following message.

Please insert the disck labeled: 'Ubuntu-Server 8.10 _Intrepid Ibex_ - Release amd64 (20081028.1)' in the drive '/cdrom/' and press enter.

Then it comes in a loop of continues trying and no way to get any further.

I have used the CTRL-ALT-F2 and when in console i go to cdrom and do a ls-al and it shows folders and files.

Is there anyone out there who can give me some help to get it going? I have tested the cdrom and also the md5, i burned it with 1 speed and imgburn, I have no more ideas... :-((

i also tried to umount and mount again the cdrom, no result either.

Kind regards,

---

### Post by hictio on 2008-12-03
I had the same issue, on my case, it was slow/old hardware.
On my case, the workaround was to make a minimal install, and then proceed to download the rest of the desired install from internet.
This happened on a [fairly old box](http://oesediez.blogspot.com/2008/08/it-is-alive.html), with both 8.04 Server and 8.10.

---

### Post by Nicklas57 on 2008-12-03
Thanks for your reply, the mystery is that I have installed Kubuntu v7.10 with same cdrom player and had no problems.

Maybe a bug in this new server edition?


Downloading the version 8.04 now to see if that one is going to work, any idea of replacing the cd-rom player will be a good idea?

---

### Post by hictio on 2008-12-03
Not sure, as I didn't had that particular problem installing Server 8.10, *but* Server 8.04 and Intrepid (plain vanilla desktop) on the same box.
On both cases, I had to go with a minimal install.

---

### Post by jpwatts on 2008-12-04
The same thing happened to me.  After much frustration I eventually got it to work by installing from a USB DVD drive rather than the internal drive I had been using.

---

### Post by Nicklas57 on 2008-12-05
I was able to install the 8.04 tls from cd and also a few other linux flavours. I am quite sure that they have changed something in 8.10 as it seems a bit different aproach this installer. Any way I am just a starter and haven't got the knowledge to understand it all, but i will give it a try with a portable drive.

Keep you informed. 

And many thanks for support.

---

### Post by DoverDad on 2008-12-14
This is not a workaround, and I am only posting this in case it helps [anyone] to track down why the server doesn't install properly.

I had the same problem, described here, with a Dell Inspiron 5000, installing from a CD (a downloaded ISO image).

So fed up did I become that I installed a basic openSUSE Linux instead (accepting all its defaults). I quickly decided that that version of Linux was not for me, so I had a go with Ubuntu again.

Now, with the same CD and the same computer, the Ubuntu server installed without any problems. I do not know enough about Linux to explain why.

---

### Post by tgm0 on 2008-12-22
Got the same problem too and can't finish the install correctly.
tryed to reinstall, and tryed to fix a broken system too. with this last one i get to a shell prompt from which i will have to do everything by hand, but i'm not such an expert so i will say i'm stucked...

I think the problem in my case could be related with my system manage disks.
i am installing the server on a sata disk. my main disk drive controller it's still an ide controller, then there is also sata support. beeing the os hard disk a sata disk, it appears connected like  a 3rd IDE master disk...while the CD-ROM is secondary IDE master...may this be the problem????

regards:(

---

### Post by tgm0 on 2008-12-22
I actually solved the problem substituteing the dvd RW unit
the unit giving me the problem was a Sony NEC Optiarc model No. AD-7170A
substituted with an Philips CDRW 4800
...
still have to finish the installation toh...but well passed the point where i was getting stucked before...

---

### Post by atisss on 2009-01-11
I had exactly the same problem, in my case it was Sony NEC Optiarc AD-7173A. Seems that there's either bug in drivers for them, or they are just out of specs..

Btw, regarding the same DVD drive, i also got tons of errors when trying to install Ubuntu desktop on different machine.

---

### Post by the_flood502 on 2009-01-17
having the same issue... RIGHT NOW lol... guess i'll just download 8.04 for now.

And my box is fairly new (a year or so old) =/

---

### Post by atisss on 2009-01-17
> **the_flood502 said:**
> having the same issue... RIGHT NOW lol... guess i'll just download 8.04 for now.

And my box is fairly new (a year or so old) =/

I'm afraid it won't help. I had issues with my cdrom before, also on 8.04.

What model do You have?

---

### Post by teddy0409 on 2009-08-11
Hi,
I browsed this from another forum and works fine for me,
go to /etc/at/sources.list and comment the lines stating abt CD ROM (2 lines probably),
Regards,
ted

---

### Post by mortified_pengiun on 2011-06-10
I fixed this by creating a small partition (1gb) for swap.

---

