---
title: "Not thrilled with Ubuntu server so far."
date: 2006-08-15
forum: Testimonials &amp; Experiences
---

### Post by acolic on 2006-08-15
Hi,

not quite happy with Ubuntu Server so far. Its gone wacky with dependency problems that prevent the installation of any programs. I can't reinstall or uninstall the broken stuff and I can't fix it.

I was going to use the server to showcase what Ubuntu can do to my boss and right now it is pretty unusable. So this wknd I either have to install Windows 2000 server or rebuilding the server with Ubuntu. Yes I know that Windows 2000 is going to cost more then Ubuntu but you have to factor in the down time of a server in your cost analysis. 

I've used Ubuntu for a couple of months. On my desktop and server installation went great, and all my hardware was recognized properly. Installation of software went well via aptitude. But then the dependency problem started and there does not look to be any way to fix it. So I'm concerned about the stability. I have to wonder what would have happened if this was a production box, what are the odds of this happening again?

People were great on this list providing suggestion but the problem seems to be too far gone. What bugs me is I have no idea how the dependency problem happened. I only installed software via aptitude.

Anyway maybe I'll keep Ubuntu on my desktop and try something else on my server.

Alex

---

### Post by %hMa@?b&lt;C on 2006-08-15
Well, you could try again with ubuntu on the server, or maybe ubuntu on the server is just not for you. You could try another distro, or fork out the cash for Windows Server.  Persionally Ubuntu works excellently as my home server ( [http://theironknuckle.com/](http://theironknuckle.com/) ) but trying something else may work better for you.  Please let us know what you end up using!

---

### Post by acolic on 2006-08-15
Hi,

I like Ubuntu and I like'd learning how to set it up and to use Linux in general but I'm ticked off that hours of work went out the window and there seems to be no way to fix it. If I knew what went wrong I'd make sure it did not happen again. 

Maybe I expected too much from Linux. I subscribed to the belief that it was super stable compared to windows. Maybe I set the bar too high.

I'll vent for a bit this week and figure out what to do Saturday;)

---

### Post by Tomosaur on 2006-08-15
Perhaps a little more clarity would help people help you. What exactly are the errors you're getting / what programs are you trying to install etc?

---

### Post by linuxpenguin on 2006-08-15
Hmm, ubuntu Server works great for me!  Then again, I just clicked the "Install LAMP Server" button and let it do its thing. . .  Only complaint I have is that they should've included Webmin as part of the install process - it's such a handy tool!

---

### Post by halfvolle melk on 2006-08-15
You could use Debian stable. It's indestructible (unless you really put forth the effort offcourse :)).

---

### Post by acolic on 2006-08-15
Hi,

the problems I had were posted here:

[http://www.ubuntuforums.org/showthread.php?t=228662&highlight=alex](http://www.ubuntuforums.org/showthread.php?t=228662&highlight=alex)
[http://www.ubuntuforums.org/showthread.php?t=226660&highlight=alex](http://www.ubuntuforums.org/showthread.php?t=226660&highlight=alex)

Yes I clicked the install LAMP button as well and it worked great. It was only after using the server for a while that I had the problems.

I thought I'd try Suse 10.1 out on the server. It seems like a decent distribution.

Thanks

Alex

---

### Post by DoctorMO on 2006-08-16
As a perl developer myself I can relate, perl is a nasty install, fortunatly it comes with most distros, unfortunatly it's still a twit when it comes to installing modules wich require compiling.

If you want to install perl on Ubuntu (as per first thread) you need to use the correct use flags, you also have to understand what is installed on your system and what isn't. admins who use Gentoo in this regard come out with far more background on the kinds of fun and games required sometimes.

As for windows, well I've always laughed at the way it loads a GUI into memory for a server and dosn't even have ssh. it's not a serious server for me because it's a desktop by design which was made to act servish (reminds me of ubuntu in this regard)

BSD is aparently the best OS for servers, Apache is a darn sight faster and Perl shouldn't be a problem.

---

### Post by pessimist on 2006-08-16
My sympathy with your Ubuntu problems with your server.  I like Ubuntu and have recently standardised on it for the dektop.

We use Fedora for servers and have found it to be rock solid across several servers.

Ubuntu has much better hardware recognition for the dektop though.

Just my opinion.

---

### Post by cptnapalm on 2006-08-17
Ubuntu server might still be a bit too new for production work for everyone.  Debian stable is probably one of the two or three most stable OSes on the planet.

I've rarely run into deb problems, but when I have, they are never nice.  :(

I do have bad memories of dealing with Perl installations for slashcode a long time ago.... I hope I don't have nightmares from remembering it.

---

### Post by dca on 2006-08-17
I got Ubuntu server to work on an old IBM xServer...  It's quirky, hate to say it but IMO Fedora is a little better...  not by much, though.

---

### Post by .t. on 2006-08-20
Works fine for me. I just SSH in once it's set up, and do everything over the network. I don't really see how anything could be better. You've got a good base, and the powerful apt system to get other programs. Simple as pie.

---

### Post by acolic on 2006-08-21
Thanks all,

I installed Debian over the wknd and the server is back up. It was a pretty cool install. I used their network install CD with was about 40 megs to install the base system and the rest from the network.

The rest of the install we pretty similar to Ubuntu. The desktop looked the same.

I'll stick with Debian on my server and Ubuntu on my desktop for now.

Alex

---

### Post by PanzerMKZ on 2006-08-21
As a complete newbie Ubuntu server was my first install.  I like it.  Runs on my old dual 500 cel with 400meg ram.  no GUI to have to worry with.  As someone said just load up SSH and do everything over the network.  Right now the machine is stable and does everything that I ask of it.  



Panzer

---

