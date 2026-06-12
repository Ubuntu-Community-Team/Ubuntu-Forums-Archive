---
title: "Lucid vs. Karmic, 5 mos. after release"
date: 2010-09-13
forum: Testimonials &amp; Experiences
---

### Post by perspectoff on 2010-09-13
Lucid vs. Karmic, 5 mos. after Lucid release

Conclusion: Except for the newest hardware, datacenters, and distributed computing needs, Lucid is currently more of a headache and not yet worth the upgrade.

What is worse in Lucid:

1) Plymouth splashscreen manager.

I would guess that about 1/5 problems in Ubuntu forums regarding bootup (blank screens, no bootup progress) is due to incompatibilities between the Plymouth splashscreen manager and either integrated Intel graphics or nVidia graphics cards.

While there are workarounds, tweaks, and fixes (and now all my computers will successfully boot), it took me a few months to figure them all out. Many users have spent months believing their hard drives, motherboards, or some other component was responsible for errant booting, when it is almost always due to Plymouth and graphics cards incompatibilties.

Although I can finally successfully boot all my computers, not a single one actually displays the splashscreen (only a blank screen when Plymouth is running). I'm happy enough that they all boot, so this is very trivial to me, but it is still a bit of an absurd situation.

I have no such problems in Karmic, which boots up equally fast (and on 3 computers much faster) than Lucid.

2) Network Manager. I have always hated Network Manager. It has never done static IP addressing properly, and it still doesn't, even in Lucid.

It didn't do wireless connections right in the beginning, but in Karmic had at least become stable for wireless (as long as DHCP was used). In Lucid, though, it has again become unstable with wireless. I have no idea why, since my wireless hardware hasn't changed.

I ended up removing Network Manager from every computer that runs Lucid and replacing it with Wicd, especially for wireless connections. Wicd does static IP addresses better, and I have never had a problem with wireless with Wicd.

3) PHP 5.3 vs. PHP 5.2. Lucid uses PHP 5.3 and does not have PHP 5.2 in the repositories. Big mistake. Drupal, one of the most widely used CMS / website platforms, requires PHP 5.2 for many of its modules. To get Drupal to work in Lucid I had to manually revert to PHP 5.2, which was no fun at all. 

For any server running Drupal, I ended up sticking with Karmic to avoid the hassles.

4) Grub2. Ok, Karmic has Grub2 as well. I hate Grub2 over Grub Legacy, but have generally learned to live with it. However, something in the version in Lucid has been updated so that whenever I change the Grub2 configuration files and then do a grub-update, the system gets changed out of recognition and then won't boot properly until I revert the changes. (I can use grub-mkconfig --output=/boot/grub/grub.cfg
instead of grub-update and things work ok, but that took me weeks to figure out.) 

What is apparently better in Lucid:

1) The BigBlueButton teleconferencing server (assembled by Google Code out of a variety of open source packages) has been made compatible with Lucid Lynx, and this is the only component that tempted me to upgrade. However, I am happier putting that single server in a Lucid virtual machine (or on its own isolated Lucid server) and leaving everything else in Karmic.

For me, nothing else works better in Lucid. I understand that it is better for those with the newest hardware, distributed (cloud) computing needs, and datacenters, but I have found no advantages for my SOHO (I run medical clinic computers) uses at this time.

Bottom line: Because of the numerous bootup problems from Plymouth and the wireless problems with network manager in Lucid, at this time I recommend that newbies to Ubuntu use Karmic. Hopefully by Christmas the Lucid graphics-and-bootup problems will be ironed out, Drupal will be able to catch up to PHP 5.3, and Network Manager will again be stable.


Perspective:
I personally manage about 15 computers, at work and at home, and peripherally manage another 30. The oldest ones only have Linux (Ubuntu derivatives, mostly of Hardy vintage, and Puppy Linux). The newest ones have multiple OS's, including multiple versions of Windows, OS X, and multiple Linux distros, including several versions of Ubuntu. I also run Virtualbox and VMWare virtual machines. I run about 20 servers, including groupware, websites, wikis, DNS servers, network monitors, teleconferencing servers, etc., etc. I use both Gnome and KDE, but mostly KDE (Kubuntu). Every hard drive (except the very oldest computers) has multiple partitions and multiple instances of an OS: one for production and one for upgrades and/or backups. I never upgrade a production system directly. I always create a testing copy of the OS (in a separate partition) and upgrade that copy. Only when it works 100% do I put it into production. On two of my server computers (each with 5 servers on them) I have not put Lucid into production, for the reasons stated above. (I have left them at Karmic.)

---

### Post by borth92 on 2010-09-13
i am a very happy Lucid user since it came out. I ran Karmic on a virtual machine and the upgrade to lucid was really what made me install it as a secondary partition...and it has now become my primary partition. I have had no major issues at all

---

### Post by jaycee23 on 2010-09-13
> **perspectoff said:**
> Lucid vs. Karmic, 5 mos. after Lucid release

Conclusion: Except for the newest hardware, datacenters, and distributed computing needs, Lucid is currently more of a headache and not yet worth the upgrade.

What is worse in Lucid:

1) Plymouth splashscreen manager.

I would guess that about 1/5 problems in Ubuntu forums regarding bootup (blank screens, no bootup progress) is due to incompatibilities between the Plymouth splashscreen manager and either integrated Intel graphics or nVidia graphics cards.

While there are workarounds, tweaks, and fixes (and now all my computers will successfully boot), it took me a few months to figure them all out. Many users have spent months believing their hard drives, motherboards, or some other component was responsible for errant booting, when it is almost always due to Plymouth and graphics cards incompatibilties.

Although I can finally successfully boot all my computers, not a single one actually displays the splashscreen (only a blank screen when Plymouth is running). I'm happy enough that they all boot, so this is very trivial to me, but it is still a bit of an absurd situation.

I have no such problems in Karmic, which boots up equally fast (and on 3 computers much faster) than Lucid.


Have to agree about Plymouth. Can't really see the reason for its existence - I'm sure someone will enlighten me.

All it seems to do is create a whole lot of problems we didn't use to have!

---

### Post by rrashkin on 2010-09-13
Granted I'm a very basic user but I found Lucid to be the best release so far (since Intrepid).  It seems faster (whether it is or not).  It seems to have more rational application access (whether it does or not). 
I've had no problems, but then I didn't with Karmic either.

---

### Post by Elfy on 2010-09-13
Not a support request - moved to testimonials

---

### Post by mastablasta on 2010-09-14
> **perspectoff said:**
>  On two of my server computers (each with 5 servers on them) I have not put Lucid into production, for the reasons stated above. (I have left them at Karmic.)
 
wouldn't using a stable debian be a better choice for server?

---

