---
title: "A Home Server - Any help?"
date: 2008-12-16
forum: Server Platforms
---

### Post by tjasko12 on 2008-12-16
Hi Everyone,

I recently got my hands on a HP/Compaq ProLiant DL380 G2 Server... And I can say it's a great server for what I need it for...

I'm looking into running FreeBSD or Linux on it. Both Unix based... I really do not want to use Windows Server because Linux/Unix is faster... No one can argue that...

Right now, I'm having a hard trouble on what OS I should run on the server... I'm trying to debate between Ubuntu Server, CentOS, and FreeBSD... 

Those are pretty much the top server OS's... I've working with Linux before, but never BSD... I'm hearing the BSD is a bit of a pain to upgrade though...

When it comes to what I want, this is it:

1) Realibility. I want the server to be running, and while it's running, it's not going to crash/lockup.

2) Updates are a breeze. We all know why we want this one.

3) Easy application install. I guess this eliminates FreeBSD or any BSD based OS.

4) And last, great performance... The server is a bit old, so I would like to push the performance out of it...


What's funny is, I'll probably be using a wireless card in the server (PCI), so driver compatibly is very important... My network is very fast, so I'm not worried about that... 


I just want to use the server to store my files, music, applications, and everything I would like to backup to it... 



This might sound like a dumb question, but when you set up a server, would you access it from the networking and sharing center in Vista? It's technically a network share, so you should find it there. But what happens if I wanted to set it up so that if I was away from my network/house, I could access it up anywhere? I have no clue on how to do that... But with out it really hosting anything. Just for my personal use...

I'm new to servers, but not to Linux... So you can pretty much throw anything at me with Linux, and I'll understand it. I just want to set up a fast server, but choosing the OS is a hard part...

Any of you guys have experience with any of these OS's, or recommend another one to me. I know this is a Ubuntu forum, but all of you are so knowledgeable. ;)



Thanks!

Taylor Jasko

---

### Post by gtdaqua on 2008-12-16
> **tjasko12 said:**
> 

What's funny is, I'll probably be using a wireless card in the server (PCI), so driver compatibly is very important... My network is very fast, so I'm not worried about that... 


You may have to rely on forums to get your wireless working if you can't get it working straight out of the box. Ubuntu forums are very active and responsive.

> 
I just want to use the server to store my files, music, applications, and everything I would like to backup to it... 


Ubuntu is based on Debian so either of this would work very good. Debian is considered better by many admins (I run 2 of them). Its light-weight than ubuntu and generally packages are not frequently updated unless they address a critical issue. This has both ups and downs. Wanna just work without bothering updates, goto to Debian. Want somewhat-latest packages with greater coverage and all that stuff? Get Ubuntu.


> 
This might sound like a dumb question, but when you set up a server, would you access it from the networking and sharing center in Vista? It's technically a network share, so you should find it there. But what happens if I wanted to set it up so that if I was away from my network/house, I could access it up anywhere? I have no clue on how to do that... But with out it really hosting anything. Just for my personal use...


You can setup Samba on Ubuntu/Debian in seconds and have it accessible in XP/Vista or other linux machines. 

If you wanna access from anywhere, then simply install openssh-server and denyhosts packages. Forward the SSH port 22 on your router to the linux server. This is much better than opening Samba ports over the internet. From the remote client machine, you can use WinSCP (on Windows) to browse/download from the home server. If its a linux desktop, then you probably know how to access.

Remember, denyhosts becomes essential when your ssh port is open in the internet.

> 
I'm new to servers, but not to Linux... So you can pretty much throw anything at me with Linux, and I'll understand it. I just want to set up a fast server, but choosing the OS is a hard part...


Good to know that you already know linux. Choose an LTS (currently 6.06 or 8.04 in Ubuntu) if you don't want bother with release upgrades and non-essential updates. LTS are maintained for 5 years by Ubuntu. 
Other releases are maintained for 18 months. 

Debian etch is the current stable version. You won't notice a major difference, but Debian is compact. An excellent choice if you want to keep the administration to minimal.

If you are very particular in things like 2.6.18 debian kernel is older than ubuntu's 2.6.24 kernel etc, then you can choose Ubuntu. But that won't improve anything on your file server. But because you mentioned a wireless card, then you would probably be interested in the latest kernels if you have problems with drivers. For the sake of this, you might probably want to choose Ubuntu.

---

### Post by albinootje on 2008-12-16
> **tjasko12 said:**
> 
I'm looking into running FreeBSD or Linux on it.

FreeBSD is indeed not so easy at all to upgrade compared to e.g. Ubuntu, although, if you've done that a few times, it gets much easier.

Since a while I prefer either Debian or Ubuntu on servers.
The installer in Debian Etch is really nice, compared to earlier Debian installers, and you have a good choice between bare boned or desktop installation.

If you think Debian doesn't have newer software that you think you need, you can take a look at Debian Lenny (testing).
[http://bugs.debian.org/release-critical/](http://bugs.debian.org/release-critical/)
[http://blog.schmehl.info/Debian/releasing-lenny](http://blog.schmehl.info/Debian/releasing-lenny)
and see whether you want to use it.
I'm using Debian Lenny in a VPS for nagios, and that's running without problems since a few months.

---

### Post by tjasko12 on 2008-12-16
> You may have to rely on forums to get your wireless working if you can't get it working straight out of the box. Ubuntu forums are very active and responsive.

I know you can get pretty much any card working... I'll just search for compatibility before I buy it... ;) I'm typically good with getting wireless working... Not that hard.


> 
Ubuntu is based on Debian so either of this would work very good. Debian is considered better by many admins (I run 2 of them). Its light-weight than ubuntu and generally packages are not frequently updated unless they address a critical issue. This has both ups and downs. Wanna just work without bothering updates, goto to Debian. Want somewhat-latest packages with greater coverage and all that stuff? Get Ubuntu.

Yes, I do know that Ubuntu is Debian based... :)

I've never used a Debian OS before with a server... I'll have to look into that.



> 
You can setup Samba on Ubuntu/Debian in seconds and have it accessible in XP/Vista or other linux machines. 


Yep, that'll set up a network share... I used Samba before...


> If you wanna access from anywhere, then simply install openssh-server and denyhosts packages. Forward the SSH port 22 on your router to the linux server. This is much better than opening Samba ports over the internet. From the remote client machine, you can use WinSCP (on Windows) to browse/download from the home server. If its a linux desktop, then you probably know how to access.


Remember, denyhosts becomes essential when your ssh port is open in the internet.

Wow, thanks!

Dennyhosts are important. ;)

> Good to know that you already know linux. Choose an LTS (currently 6.06 or 8.04 in Ubuntu) if you don't want bother with release upgrades and non-essential updates. LTS are maintained for 5 years by Ubuntu. 
Other releases are maintained for 18 months. 

I'm not that concerned by support. But the other releases (non lts) are fine for me...

> Debian etch is the current stable version. You won't notice a major difference, but Debian is compact. An excellent choice if you want to keep the administration to minimal.
I heard that before!

> If you are very particular in things like 2.6.18 debian kernel is older than ubuntu's 2.6.24 kernel etc, then you can choose Ubuntu. But that won't improve anything on your file server. But because you mentioned a wireless card, then you would probably be interested in the latest kernels if you have problems with drivers. For the sake of this, you might probably want to choose Ubuntu.

When you mentioned the kernel because of wireless drivers, I completely understand what you are saying! Ubuntu does have great driver support! 




Thanks for your awesome post! Really helped!

---

### Post by tjasko12 on 2008-12-16
> **albinootje said:**
> FreeBSD is indeed not so easy at all to upgrade compared to e.g. Ubuntu, although, if you've done that a few times, it gets much easier.

Since a while I prefer either Debian or Ubuntu on servers.
The installer in Debian Etch is really nice, compared to earlier Debian installers, and you have a good choice between bare boned or desktop installation.

If you think Debian doesn't have newer software that you think you need, you can take a look at Debian Lenny (testing).
[http://bugs.debian.org/release-critical/](http://bugs.debian.org/release-critical/)
[http://blog.schmehl.info/Debian/releasing-lenny](http://blog.schmehl.info/Debian/releasing-lenny)
and see whether you want to use it.
I'm using Debian Lenny in a VPS for nagios, and that's running without problems since a few months.

Hmm. Now I have to pick Ubuntu or Debian...

This is going to be a hard one because Ubuntu is based off Debian... 


Yep, I knew the FreeBSD wasn't the friendliest OS out there...

---

### Post by albinootje on 2008-12-16
> **tjasko12 said:**
> 
Dennyhosts are important. ;)


I don't agree with this, denyhosts is only kind of important when you receive nightly log file summaries (FreeBSD has that by default), so that you don't have huge emails because of those random ssh login attempts.
And/or if you want to save some bandwidth ;-)

Do you really think that those brute-force attacks are gonna guess your username *and* your *difficult* password ?

What is really important concerning using an ssh-server is to choose a good password.

And i recommend using the AllowUsers option in /etc/ssh/sshd_config if that makes you sleep better at night. See : man sshd_config

---

### Post by tjasko12 on 2008-12-16
> I don't agree with this, denyhosts is only kind of important when you receive nightly log file summaries (FreeBSD has that by default), so that you don't have huge emails because of those random ssh login attempts.
And/or if you want to save some bandwidth ;-)
Saving bandwidth is important... :)

> Do you really think that those brute-force attacks are gonna guess your username *and* your *difficult* password ?
Not really... :) But you can always be secure. ;)

> 
What is really important concerning using an ssh-server is to choose a good password.

Trust me, my passwords are very secure... :)

> 
And i recommend using the AllowUsers option in /etc/ssh/sshd_config if that makes you sleep better at night. See : man sshd_config
I'm going to have to research this one... I haven't dealt much with SSH.




Just to throw this question out there, any one ever use any RPM-based distro for a server OS?

---

### Post by albinootje on 2008-12-16
> **tjasko12 said:**
> Hmm. Now I have to pick Ubuntu or Debian...

This is going to be a hard one because Ubuntu is based off Debian... 


You want a rock-solid server ? Then use Debian instead of Ubuntu, or go for an Ubuntu LTS release, YMMV

You want the latest software ? Choose Ubuntu.

> 
Yep, I knew the FreeBSD wasn't the friendliest OS out there...

Compared to OpenBSD and esp. NetBSD, the installation of FreeBSD is very easy. Upgrading FreeBSD is not so easy to do, but then again this doesn't need to happen so often, although sometimes you need to do a "make world" ;-)

---

### Post by tjasko12 on 2008-12-16
> You want a rock-solid server ? Then use Debian instead of Ubuntu, or go for an Ubuntu LTS release, YMMV

You want the latest software ? Choose Ubuntu.

I would honestly like a rock-solid server... So I might just use Debian... Besides, I hear Debian is very nice on servers.

> 
Compared to OpenBSD and esp. NetBSD, the installation of FreeBSD is very easy. Upgrading FreeBSD is not so easy to do, but then again this doesn't need to happen so often, although sometimes you need to do a "make world" ;-)
Yeah, I would like at least most of the OS in a GUI... :)

I'm fine with the terminal, but I don't want to be in it just to upgrade... :D I want some user friendliness to it...

Don't get me wrong, I love the terminal, but I just do want to be in it that much... like with upgrading.

---

### Post by albinootje on 2008-12-16
Okay. *** Welcome to Planet Debian *** :)

---

### Post by gtdaqua on 2008-12-16
> **albinootje said:**
> I don't agree with this, denyhosts is only kind of important when you receive nightly log file summaries (FreeBSD has that by default), so that you don't have huge emails because of those random ssh login attempts.
And/or if you want to save some bandwidth ;-)

Do you really think that those brute-force attacks are gonna guess your username *and* your *difficult* password ?

What is really important concerning using an ssh-server is to choose a good password.

And i recommend using the AllowUsers option in /etc/ssh/sshd_config if that makes you sleep better at night. See : man sshd_config

Denyhosts are not important?? They can not only block brute force on SSH port but on ANY port, ANY service.

Brute force attempts are possible. They are getting smarter and smarter. Just because they wont easily guess your password, doesnt mean they can't fiddle with port 22 using network tools or specially crafted packets or an undisclosed vulnerability causing a DoS. Shutting down the port entirely for banned users is safe rather than allowing them to experiment with the authentication mechanism of ssh.

You could additionally block the IPs for ALL services with denyhosts.

---

### Post by Ferret-Simpson on 2008-12-16
> **tjasko12 said:**
> Hi Everyone,

I recently got my hands on a HP/Compaq ProLiant DL380 G2 Server... And I can say it's a great server for what I need it for...

1) Realibility. I want the server to be running, and while it's running, it's not going to crash/lockup.

2) Updates are a breeze. We all know why we want this one.

3) Easy application install. I guess this eliminates FreeBSD or any BSD based OS.

4) And last, great performance... The server is a bit old, so I would like to push the performance out of it...

Thanks!

Taylor Jasko

1 DL360 G1,
3 DL360 G2's.

What I'm running is Server 2003 on my internal (File) server, and Ubuntu * Hardy * on everything else.

Hardy works out of the box, is solid as a rock, great wireless support (Especially Atheros cards) and most importantly has the great support these forums offer. I hear the Debian community has slightly shorter thrift. *Shrugs* It's what I heard.

Intrepid won't install on your hardware, there's a problem with Grub that prevents it. Hence why I use hardy. :D

If you're a student, [www.dreamspark.com](www.dreamspark.com) and get a free copy of Windows Server 2003. For doing nothing but file sharing on an internal network it's simply the better choice. Especially if you want Graphics. Unfortunately, X11 is about as subtle as the British Army - so on Linux, you choose server performance or graphics. In the long run, it won't do you any good anyway. AGPart barely supports your chipset, and as far as updates go, Hardy installs critical updates automagically & anything else, well..

```

sudo apt-get update
<password>
sudo apt-get upgrade
y
```

Since you're using a rack mount machine, you'll be better off using ssh to control it any way (Since most of what you want to do will be command line), and just run it from your nice iMac or Asus EeePC in a pretty translucent green and black command line window.

Debian's great, don't get me wrong - but for something that's going to do one reasonably simple task - I think Ubuntu is the easy bet for configuration.

---

### Post by tjasko12 on 2008-12-16
> **albinootje said:**
> Okay. *** Welcome to Planet Debian *** :)

Thanks. ;)

---

### Post by tjasko12 on 2008-12-16
> **gtdaqua said:**
> Denyhosts are not important?? They can not only block brute force on SSH port but on ANY port, ANY service.

Brute force attempts are possible. They are getting smarter and smarter. Just because they wont easily guess your password, doesnt mean they can't fiddle with port 22 using network tools or specially crafted packets or an undisclosed vulnerability causing a DoS. Shutting down the port entirely for banned users is safe rather than allowing them to experiment with the authentication mechanism of ssh.

You could additionally block the IPs for ALL services with denyhosts.
I never said they weren't... Some people choose to use them, or not... I'm more of a secure type of guy, so I'll probably use it... ;)

---

### Post by tjasko12 on 2008-12-16
> Intrepid won't install on your hardware, there's a problem with Grub that prevents it. Hence why I use hardy. :D

Hmm, I'm wondering why it will not install. I could try it... ;) But, it probably will not install.

> If you're a student, [www.dreamspark.com](www.dreamspark.com) and get a free copy of Windows Server 2003. 
I am a student, but I'm only in High School. Besides, I already own Windows Server 2008... ;) The thing is, I persoanlly think Linux is faster than Windows... People can argue, but on old hardware, I think Linux is the way to go.

> For doing nothing but file sharing on an internal network it's simply the better choice. Especially if you want Graphics. 
Graphics? Linux has Compiz and all the other cool desktop managers out there! Besides, a server doesn't need fancy graphics. :D


> Unfortunately, X11 is about as subtle as the British Army - so on Linux, you choose server performance or graphics. In the long run, it won't do you any good anyway. 
In a server, I'll anyways go for performance... You're not going to need graphics on a server. Besides, Windows Server 2003/2008 doesn't look the best either... ;) It's not supposed to.

> AGPart barely supports your chipset, and as far as updates go, Hardy installs critical updates automagically & anything else, well..
AGPart, as far as I know, is a Linux kernel module... I'll just stick with the installed default... I'm not sure if I'm going to need to install any drivers in it... Typically, Linux handles all of that.


```

sudo apt-get update
<password>
sudo apt-get upgrade
y
```

> Since you're using a rack mount machine, you'll be better off using ssh to control it any way (Since most of what you want to do will be command line), and just run it from your nice iMac or Asus EeePC in a pretty translucent green and black command line window.
Yes, I was going to use SSH anyways. It's not that much of command line based... Just set it up, and let it run... ;)

> 
Debian's great, don't get me wrong - but for something that's going to do one reasonably simple task - I think Ubuntu is the easy bet for configuration.
Hmm, many people have different opinions here. Which, don't get me wrong, but that's a good thing... ;)

I've always been an Ubuntu fan. But as albinootje said, if you want a rock solid server, use Debian; for latest software, use Ubuntu... This is going to take a while to see what I really want to use.

---

### Post by tjasko12 on 2008-12-16
Okay, I have a bit of a problem... My server cannot detect my hard drives...

6 X 18.2 GIG Ultra SCSI 

There's no error(s) on POST (except for the no hard drive notification), so I'm not sure what is wrong. I know this is very vague, but I cannot find anything to help fix it...

I know the hard drives are plugged in... I wonder if it's the Smart Array 5I controller...

I'm typically great with hardware, but this one just looses me...


I don't get what's up... I'm pretty sure every hard drive is working... I just might need to set it up. But I don't know how to because the computer cannot even see the hard drive... There most be something to help me diagnose... I already RAN the SmartStart software, and it said it could not find the hard drive either... Not even GParted found it...

---

### Post by albinootje on 2008-12-16
In that case you might want to try a FreeBSD install-cdrom to see whether it recognises it.

---

### Post by tjasko12 on 2008-12-16
> **albinootje said:**
> In that case you might want to try a FreeBSD install-cdrom to see whether it recognises it.
The system cannot find it. It's not the OS... Something could be loose, or I didn't set it up correctly... I have no clue.

---

### Post by albinootje on 2008-12-16
This page talks about a Smart Array 5I
[http://ubuntuforums.org/archive/index.php/t-255335.html](http://ubuntuforums.org/archive/index.php/t-255335.html)
mentioning using a smartstart cd to set it up.

---

### Post by gtdaqua on 2008-12-16
> **tjasko12 said:**
> 

There's no error(s) on POST (except for the no hard drive notification)....

??!! Is that the BIOS saying that it can't see the drive?

---

### Post by tjasko12 on 2008-12-16
> **gtdaqua said:**
> ??!! Is that the BIOS saying that it can't see the drive?
Yes, the BIOS is saying that...


Can you please take a look at this guys? I actually think I'm missing the cable from the SCSI board (where the CD drive, SCSI hard disks, and floppy connect to) to the Smart Array 5i controller... or the cable that connects my hard drive(s) to the Smart Array 5i...

[http://techcores.com/MyServer/SCSI Cable Missing.zip](http://techcores.com/MyServer/SCSI Cable Missing.zip)

(And yes, that is my hand in one photo...)
I did include some other shots of the server... just in case.

It's a big file (16MB). But that's because I kept the images at full resolution. It's a motherboard, there's a lot of details!


Look at the photo entitled "Look here for more detail.JPG" first please.


If anyone owns this same server (or very close), I would appreciate it if you checked. I'm looking right below and a little down from the PCI Riser Cage... This is when the hard drives are facing you the closest.

I contacted the guy I bought it off of. I'll see what he says... But for now, I would like to see what you guys think also...


Although I do think this is the source for my problems... ;)

I'm not that great with servers, but when I can see something that isn't connected, I'm suspicious...



Thanks!

---

### Post by gtdaqua on 2008-12-17
I suspect you have not connected the SCSI cable at all. The SCSI port is empty. Without connecting this, your BIOS wont see the HDD. Also I did not see ANY scsi cable running just an IDE cable. How did you get this server?

---

### Post by jerome1232 on 2008-12-17
I use an Ubuntu Home server at home but I'm seconding the Debian crowd.

On a side note my Ubuntu server seems very solid, it only get's rebooted when kernel updates roll out.

If I really felt like reconfiging it (and I don't) I'd probably be putting Debian on it though.

---

### Post by tjasko12 on 2008-12-17
> **gtdaqua said:**
> I suspect you have not connected the SCSI cable at all. The SCSI port is empty. Without connecting this, your BIOS wont see the HDD. Also I did not see ANY scsi cable running just an IDE cable. How did you get this server?


I know! I didn't see any cable at all! Apparantly, I was right... I didn't see any IDE (wouldn't know why there would be an IDE cable for a SCSI hard drive though) cable either... Those are the only SCSI ports on the whole motherboard. And ironically, one is on the SCSI backplane, and one is on the controller... That's a bit obvious that they need to be connected.

I actually got this server for pretty cheap... This is probably because it wasn't shipped out, it was in the area for me... The guy I bought the server off of said he checked (scandisk) all the hard drives. And right now, I thinking that that was a lie. Because how would he check it if I have no cable?

I'll see what he says today... I think he'll be sending me a cable anyways. It was not listed in the ad when I bought it, and he didn't inform me of anything like this. And no, it's not "As-is". So basically, I have a good chance that I'll get a cable from him.

Just wanted to see what you guys think. Because I'm almost sure that's the problem.

---

### Post by tjasko12 on 2008-12-17
> **jerome1232 said:**
> I use an Ubuntu Home server at home but I'm seconding the Debian crowd.

On a side note my Ubuntu server seems very solid, it only get's rebooted when kernel updates roll out.

If I really felt like reconfiging it (and I don't) I'd probably be putting Debian on it though.
Why would you want to put Debian on it? I'm just asking because I would like to get the most opinions here...

I love Debain based distros... Right now, I am thinking about using Debian. This is because Debian is pretty much built for servers... I really do not see people run it on a Desktop PC/Laptop.


Edit:
[http://www.computercablesource.com/scsi-cable-hd68-male-to-hd68-male-006-foot-u320-lvdsehvd-820.html](http://www.computercablesource.com/scsi-cable-hd68-male-to-hd68-male-006-foot-u320-lvdsehvd-820.html)

Yep, that's the cable I need (it's an example. I don't need a 6 foot cable for this tiny job. :D). A HD68 cable... I can pretty much conclude that this is the problem.

---

### Post by gtdaqua on 2008-12-17
LOL!

So basically you were trying gparted and other disk utilities to detect the disks even before connecting them!

---

### Post by tjasko12 on 2008-12-17
> **gtdaqua said:**
> LOL!

So basically you were trying gparted and other disk utilities to detect the disks even before connecting them!

Haha, that was exactly what I was trying to do.

But the thing was, I didn't know the hard drives were not connected from the SCSI Backplane to the controller... 

I might need that cable. :D

---

### Post by tjasko12 on 2008-12-17
Okay, he's sending me the cable now... (of course for free)

He actually didn't ask any questions. I guess the photo(s) did speak 1,000 words. ;)


Thanks guys! I'll probably be installing Ubuntu Server or Debian very soon here... :)


Thanks!

---

### Post by jerome1232 on 2008-12-17
> **tjasko12 said:**
> Why would you want to put Debian on it? I'm just asking because I would like to get the most opinions here...

Mostly to try it out, and see if I like it any better; I think the main difference's are the release schedules, Debian being on a rolling release schedule and Ubuntu does version freezing and patches in the security updates. I believe every release of Ubuntu is a snapshot of Debian unstable?

---

### Post by tjasko12 on 2008-12-17
> **jerome1232 said:**
> Mostly to try it out, and see if I like it any better; I think the main difference's are the release schedules, Debian being on a rolling release schedule and Ubuntu does version freezing and patches in the security updates. I believe every release of Ubuntu is a snapshot of Debian unstable?
I'm not sure if it's a snapshot of Debian unstable.

Yeah, trying something new is always something great to do. ;)

---

### Post by tjasko12 on 2008-12-27
Well it appears to be that the person I bought the server off of, sold me a broken server!

For some reason, it doesn't like any RAID setups I set up. And I tried all of them. None of the hard drives are broken, and I just think that the RAID controller is broken. It could be the SCSI backplane also, but I'm not sure on that one... :)

Well, I'm never buying from this company again...

---

