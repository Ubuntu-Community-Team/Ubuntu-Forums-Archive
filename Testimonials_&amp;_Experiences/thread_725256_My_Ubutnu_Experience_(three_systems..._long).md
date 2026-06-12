---
title: "My Ubutnu Experience (three systems... long)"
date: 2008-03-15
forum: Testimonials &amp; Experiences
---

### Post by Calmor on 2008-03-15
I've always been rather interested in Linux, but never had the time or opportunity to sit down and learn.  I like knowing how things work.  I grew up on a C64 and started with BASIC at 4 years old.  I dabbled in Linux here and there, installing a different distro every few years on a spare machine just to see where the state of Linux was at the time.  My previous adventure, before my foray into Ubuntu, was a Gentoo install on a VIA mini-ITX that I hoped would run MythTV... but the hardware was a bit too slow to do what I wanted.

Anyway, I installed Gutsy on my main PC as a dual-boot OS.  I use it mostly for Quicken and won't give it up, but I wanted to play with Ubuntu on the side.  It was easy to set up, but getting my knockoff ATI 7500 to work was difficult, and it's still not functioning as I'd hoped.  (GLX gears works great for a while, but after some time running, something happens and any 3D display gets choppy - some screen savers barely run).  All told, though, I enjoyed using it but saw no real need to use it as an every day OS - the only things I do on that machine are Quicken and some audio editing with software not available in Linux right now.

Fast forward a year.  My girlfriend's laptop has a failing HDD.  It's a Dell D410.  As I try to reinstall Windows XP Pro on another drive, I get fed up with little problems (having a flash drive in when installing causes the primary HDD to be marked as the D: drive, and it's difficult to change back).  She needs the computer right away, so I install Gutsy (though I'm still a noob myself) and ask if she'd be willing to give it a try until at least the permanent replacement HDD arrives.

The install goes perfectly.  Everything just works.  Wireless, Audio, Compiz full effects, everything.  She likes the way it looks and how easily customized the GUI is.  I mentioned when we get the new HDD we can dual-boot with Ubuntu as primary, and she asks "Why would I need to have Windows?"  She stuck with Ubuntu and I copied over all of her settings.  It's rock solid, save for Hibernate mode, but Standby works perfectly.  She loves it.

Inspired by the success and ease of installing on the D410, I tried Gutsy dual-boot on my work laptop - a D630.  After backing up Windows XP Pro, I GParted and resized partitions.  Installation went flawlessly.  The audio is a problem on the D630, but was easily corrected.  I went about trying to do some of the more geeky things - configuring my Verizon Wireless card, getting the Aventail VPN to work, etc.  Evolution connects to my OWA e-mail.  Things are going well, but there is always something odd.  Evolution locks.  Sometimes the system stops responding altogether.  My video card is blacklisted so I get no love from Compiz.  Today, domain name resolution stopped working for no reason, and I think it's a hardware problem because Windows XP isn't working either, but I almost think Ubuntu caused the problem because when NetworkManager was configuring the card, the light would flash rapidly - when it stopped working even the hardware switch wouldn't turn the light off.  Oddly, it'll connect to any address if I know the IP.

So, it's been a love-hate thing.  It's amazing how easily everything falls into place when it works right.  I don't know if I could talk my girlfriend back into Windows, even if it was free.  I love the open source model and the ease of customization, the tighter security and stability (on her machine at least).  I can do many things in Ubuntu that don't work quite right in Windows, even things based on IE proprietary formats.

Update - after playing around in Windows, the hardware disabled itself.  After manually enabling it, DNS lookups worked and all was right with the world... for no apparent reason.

---

### Post by freebios on 2008-03-15
wait until you use hardy heron you'll be amazed at its compatibility with hardware, other operating systems, and its fresh GUI.  I am using the alpha build and works great if you can't wait a month for the stable release check it out!  hope you like it.

---

### Post by Calmor on 2008-03-15
> **freebios said:**
> wait until you use hardy heron you'll be amazed at its compatibility with hardware, other operating systems, and its fresh GUI.  I am using the alpha build and works great if you can't wait a month for the stable release check it out!  hope you like it.

I'm cautiously looking forward to Hardy.  I heard a lot of the people who went from Feisty to Gutsy had issues.  Maybe when it moves to beta I'll put it on another machine/partition and give it a whirl.

Do you know if Hardy plans to support the Verizon Wireless cards (or if NetworkManager will recognize a ppp connection through one)?  Just curious - I have it kinda working in Gutsy now, just wondered if there was more support.  If I knew anything about Python, I'd try to contribute.  My knowledge of C and Java are limited at best..

---

### Post by freebios on 2008-03-15
I am similar to you in regards about my concern with hardware compatibility on new releases.  Since its a long term release package there are significant improvements.  i have worked with at&t express cards and to get it to work in gusty is a challenge because you have to set up all the settings manually.  with hardy heron besides downloading the driver all you have to is enable the card to get it working.  so from that sense getting hardy heron is better in my case.

---

### Post by Calmor on 2008-03-15
Getting the Verizon card to work in Gutsy was a little bit of a challenge.  I finally got it to where I can use NetworkManager to do the connection, instead of using the command line.  The only real issue for me is that nm-applet doesn't show me being online, and some other apps (Pidgin, for example) rely on it.

A GUI with a status (connected/disconnected) and signal strength would be great, though.  Currently, I bash Firefox until I get a page to load, then go about the rest of my business.

---

