---
title: "Live USB from infected windows machine"
date: 2011-09-26
forum: Security
---

### Post by neela on 2011-09-26
I have had someone attacked (this is what I am being told by my ISP: "e107 BBCode Arbitrary PHP Code Execution Vulnerability") from my public IP -- not sure if the attacks are going out from my windows machines or linux machines. If they are going from my linux machines, I don't seem to be able to detect it. chkrootkit gives my machine a clean bill of health. In the interest of abundant caution, I thought I'd reinstall linux (as well as windows -- but that is a separate problem).

In order to make a live linux USB (so that I can use it reload linux on the current linux machine), can I make it from a (potentially) infected windows machine using unetbootin?

Thanks

---

### Post by Clicksights on 2011-09-26
First turn all pc's off!
Don't let it spread! Every external drive attached must be checked too!

To avoid problems i would download the iso and burn it on a cd,
a cd can not get infected if you put it in your system. :p

If you are not sure you have an uninfected usb drive, go to a friend, burn a cd.
If you are sure you have a uninfected usb stick boot from it, and make a cd with unetbootin. 
!!back up your files from within the live boot!!

The chance that your linux pc is infected should be nominal though.
From what you say it is hard to say what happend, maybe you had a webserver running?
And your site/service got hacked or your pc has been used as a bot.

I would turn them one by one on, and do a network scan, sniff it.
Find out what pc is infected. Maybe burn a antivirus distro? 

For all installs after an infection, start with reformating all your drives.
start from scratch! repartition etc. use the live cd to format all pc's.
(formatting and partitioning is faster in linux anyway!)

I would do a encrypted install from the alternative cd, (very nice tuto here: [http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/](http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/) )

my 2 beans...

---

### Post by neela on 2011-09-27
Thank you. I seem to have visitors from Ukraine in my linux box (atleast) that I need to disinvite from the party.

---

### Post by Dangertux on 2011-09-27
First so you understand exactly what that "attack" means here is some information related to it : _[http://www.securityfocus.com/bid/40252](http://www.securityfocus.com/bid/40252)_

I am inclined to believe that your machine may have been used as an attack platform from said visitors from ukraine. This is pretty common. As far as letting it spread, I'm not really sure there is anything to spread. 

Did you have any services running on your network? SSH , VNC, any other remote administration tools in particular? Were you running a web server yourself? File Server? Any thing accessible from the outside?

Have you been downloading things from places you probably shouldn't have been? 

In any case to be on the safe side, I would reinstall from removable media such as CD-r or DVD-r.  However, realistically you would probably be reasonably safe in disabling internet connectivity to your system and making a liveUSB.

However, you can't really trust a compromised machine. The choice is yours, however I am hesitant to say that the source of the attack is viral in nature (meaning it can self propogate).

Hope this was helpful.

---

### Post by neela on 2011-09-27
Thanks. My original question was whether I could make a live linux USB from an alternate Windows machine that may have its own infection. If I could, that will be easiest. Otherwise it is a bit more trouble. The affected linux machine has ssh, vnc, don't know if skype is an issue. Moreover, my actiontec router appeared to have various kinds of outgoing permissions granted that I did not grant. It looks as if the intruder loogged into the router from my linux box. Currently (almost) all the boxes are offline, the router passwords changed, and outgoing permissions disabled.

Here is a related question -- when I tar my personal stuff to backup (before I reformat and reload), is there a risk of picking up any *infection* in the tar file?

Thanks again.
neela

---

