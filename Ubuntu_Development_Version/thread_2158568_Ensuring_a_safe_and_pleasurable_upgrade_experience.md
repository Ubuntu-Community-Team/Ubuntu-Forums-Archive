---
title: "Ensuring a safe and pleasurable upgrade experience"
date: 2013-06-29
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-06-29
Some of you know that I've been involved in iso/upgrade testing since Hardy, but to those of you not aware - I simply love Ubuntu :D

ATM I'm focusing mostly on Lubuntu because I maintain a lot of PC's that can't run either Ubuntu or Ubuntu GNOME, so you'll see a lot of references and screenshots relating to Lubuntu, but the general info should apply to all flavors of Ubuntu :)

The upgrade path offered by Ubuntu has been pretty darn good to me down through the years but we often see complaints of users encountering problems either during or after upgrades so I want to increase my focus on upgrade testing and documentation. One member of the Lubuntu dev team has even expressed interest in trying to automate the upgrade testing process:

[https://lists.launchpad.net/lubuntu-qa/msg03043.html](https://lists.launchpad.net/lubuntu-qa/msg03043.html)

If it's possible he can do it! But on to business.

There are actually two upgrade paths now. Certainly the old standard upgrade offered through the update-mangler (software-updater), but also an upgrade path using the Live CD/DVD/USB that only appears during installation if you have only one Ubuntu installed previously.

I'll provide more screenshots and documentation later regarding the upgrade  using the live image but I'm going to need to be able to post a lot of screenshots to explain things as this goes on. Like I made an improper statement here:

[https://lists.launchpad.net/lubuntu-qa/msg03046.html](https://lists.launchpad.net/lubuntu-qa/msg03046.html)

Specifically, "The whole story is long and I had to butt heads with a member of the installer-team, and I lost!"

It appears that I was wrong :oops:

I thought they were dropping the "replace" option but it appears it was just renamed:

[ATTACH=CONFIG]244259[/ATTACH]

I mean obviously Saucy -> 13.10 is not an actual upgrade, so I guess "replace" does still exist.

I also need to get this fixed:

[ATTACH=CONFIG]244260[/ATTACH]

IMHO it should NOT be called an "error" ............... because it's NOT an error. It's simply not possible to reinstall packages that no longer exist in the updated repos.

This will be a grueling task but please jump on board if you have plenty of hair to pull out :lolflag:

---

### Post by ventrical on 2013-06-29
The Grub Rescue disk uses LDXE desktop. It has  been a really great tool.  I like Lubuntu on older machines (and I too have been testing since Hardy)  I have a  Lubuntu persistive drive will boot on any machine.  Unfortunately there are time constraints with testing. As always, if I have the extra time I'll jump in when I can.

regards,

ventrical

---

### Post by kansasnoob on 2013-07-01
> **ventrical said:**
> The Grub Rescue disk uses LDXE desktop. It has  been a really great tool.  I like Lubuntu on older machines (and I too have been testing since Hardy)  I have a  Lubuntu persistive drive will boot on any machine.  Unfortunately there are time constraints with testing. As always, if I have the extra time I'll jump in when I can.

regards,

ventrical

I may very well ask for some help :)

Right now I'm trying to check the existing documentation regarding Lubuntu/Ubuntu dist-upgrades against actual Quantal -> Raring upgrades. I have enough "release-upgrader" tests done now so the next step is to try a bunch of upgrade tests using the live image  ................... because documentation for the live image upgrades is totally nonexistent :(

---

### Post by grahammechanical on 2013-07-01
There is a lot of confusion regarding names in Linux/Ubuntu. We see Update and Upgrade to mean a certain something but apt-get uses upgrade = download and install updates. There is similar confusion between a distribution upgrade and dist-upgrade.

It is a pity the we cannot put an argument to dist-upgrade that directs the dist-upgrade command to the CD/DVD to fetch stuff from the CD. Or would that be even more confusing? A dist-upgrade that upgrades a distribution. If you know what you are doing. Yes, clear instructions are needed.

Regards.

---

### Post by kansasnoob on 2013-07-01
> **grahammechanical said:**
> There is a lot of confusion regarding names in Linux/Ubuntu. We see Update and Upgrade to mean a certain something but apt-get uses upgrade = download and install updates. There is similar confusion between a distribution upgrade and dist-upgrade.

It is a pity the we cannot put an argument to dist-upgrade that directs the dist-upgrade command to the CD/DVD to fetch stuff from the CD. Or would that be even more confusing? A dist-upgrade that upgrades a distribution. If you know what you are doing. Yes, clear instructions are needed.

Regards.

ATM I intend to focus on the GUI end of things :)

So I think we'd be OK in that regard:

[ATTACH=CONFIG]244298[/ATTACH]

That is of course a screenshot of what a user would see using the release-upgrader GUI, but I already posted a shot of what the ui looks like using the live images.

---

### Post by ventrical on 2013-07-01
> **kansasnoob said:**
> I may very well ask for some help :)

Right now I'm trying to check the existing documentation regarding Lubuntu/Ubuntu dist-upgrades against actual Quantal -> Raring upgrades. I have enough "release-upgrader" tests done now so the next step is to try a bunch of upgrade tests using the live image  ................... because documentation for the live image upgrades is totally nonexistent :(



  Whats the link to the live-daily Lubuntu .iso?

thanks


k' got it...

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)


I'll try mir+btrfs on that ..

should be interesting..


or err .. I'll find it ..

---

### Post by ventrical on 2013-07-01
Mir works seamlessly (one cursor now) on Lubuntu Saucy.

```

ventrical@ventrical-P4M266A-8237:~$ ps afx | grep unity-system-compositor
 2619 pts/0    S+     0:00      \_ grep --color=auto unity-system-compositor
ventrical@ventrical-P4M266A-8237:~$ ps aux | grep unity-system-compositor
1000      2634  0.0  0.0   5664   816 pts/0    S+   17:54   0:00 grep --color=auto unity-system-compositor
ventrical@ventrical-P4M266A-8237:~$ grep -i xmir /var/log/Xorg.0.log
[   175.289] xorg-server 2:1.13.3+xmir1-0 (For technical support please see http://www.ubuntu.com/support) 
ventrical@ventrical-P4M266A-8237:~$ ls -l /var/log/lightdm/unity-system-compositor.log
-rw------- 1 root root 110 Jul  1 17:48 /var/log/lightdm/unity-system-compositor.log
ventrical@ventrical-P4M266A-8237:~$ 

```

edit* Or at least all the code say it does.

Anways ... my comment .. looks like sombody in the Lubuntu camp is eating and breathing and sleeping Lubuntu Ubiquity because ti sure installed very smoothly.

---

