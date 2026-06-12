---
title: "running with 18.04 now?"
date: 2017-11-06
forum: Ubuntu Development Version
---

### Post by Kris_M on 2017-11-06
on 17.10 I did

> **ventrical said:**
> P-I-H shares with us that this is an easier way to upgrade to new develoment cycle, avoiding software-properties-gtk crash.

```


sudo sed -i 's/artful/bionic/g' /etc/apt/sources.list
sudo sed -i 's/artful/bionic/g' /usr/share/python-apt/templates/Ubuntu.info
sudo apt-get update
sudo apt-get upgrade
sudo reboot

```

and 15 minutes later I was running 18.04 per lsb_release -a . Easiest upgrade ever. 

Had no problems - everything worked - but didn't know if I should stay there so clonezilla-ed back to 17.10.

So, my question is, is it safe to just run 18.04 now, and if I do will I wind up in the same place in late April as I would if I waited until then and upgraded the release?

Thanks!
Note: my 17.10 (from 17.04, from 16.04.3) has been running darn clean - guess I'm bored... :)

---

### Post by dino99 on 2017-11-06
New Beta Testers Warnings

Bionic Beaver is the codename for the new development cycle. If you are a new Beta tester and want to upgrade your repositories to the new development cycle then you must be advised that there are certain risks of breakage that could take place on your system(s). it is always advised that you have an extra system (hardware) or an extra harddrive to experiment with. If you are not familiar with experimenting with computer hardware or software then U+1 is not the forum for you, however, if you are willing to be on the cutting edge of Ubuntu release and understand that there could be breakage and want to contribute then the Ubuntu community welcomes you and your valued contributions.

---

### Post by harry332 on 2017-11-06
Maybe you want to open a bit more what did you mean by "is it safe". ;)
Note, there is no 18.04 yet, you have to wait until April 26th 2018 until that.
There is a pre-alfa daily product right now, which only contains some ABI bumbs.

People who use these development version are commonly testers only. :popcorn:

Certainly you should not have a development version of Ubuntu as an only product version.

---

### Post by Kris_M on 2017-11-06
Thanks! And thanks for the normal testing warnings!

@dino99 - understood. Those 5 commands above seem to upgrade the repositories to BB, so I assume Software Updater would update it as things come down the pike. I have not done bug reporting for Ubuntu and this seems a good time to learn, should I run into something. I expect catastrophic breakage. I clonezilla the entire SSD offsite (only has about 16GB of stuff plus grub) - that way even if grub changes I can always return within 5 minutes to a workable system - either earlier 18.04, or 17.10 and lose virtually no time and no data. Things like email, linux setups, phone flash stuff, etc are all on other spindles/SSDs. As to extra hardware, I build my own so if something goes sideways it's a trip across town to MicroCenter to get it going again.  I run about 9 partitions and back them all up. Again, I expect catastrophic failure. 10 minutes later and I'm up again.

@harry332 (just read your bug on DNS and chuckled because I actually used those commands (similar) to get internet to run after upgrade from 17.04 to 17.10 .) "Is it safe" means "on Dec 31 (or some unknown date) are you suddenly going to throw it all away and start over..." - LOL If it's really going to proceed, I will jump on and report bugs if I find any.  I will also keep my 17.10 relatively current as an easy fallback.  Why not dualboot, you may ask. In the past I have run into too many situations of needing to restart something and having grub get confused and rescatux not being able to fix it. BTDT. 

It's also the way I run my phone - I have been flashing my phones for years and spend a lot of time on XDA forums trying to help others do that - currently running an alpha of Oreo quite successfully, but I can easily test that and other things simply by flashing different ROMs, or different backups of a specific ROM. So while I need my phone to work, I have found ways to assure that with testing and backups. Basic bleeding edge. I also report bugs with doc and logs as I find them and help others to do the same. Unfortunately that ROM just works so I guess I am getting bored :) Same way 17.10 just works :)

---

### Post by amano on 2017-11-06
At the moment 17.10. and (pre-)18.04 are still mostly the same and pretty stable. That will change at some point of time during the development cycle.

And make sure that you disable the proposed pocket. It is not designed to be used during the development cycle.

---

### Post by Kris_M on 2017-11-06
> **amano said:**
> At the moment 17.10. and (pre-)18.04 are still mostly the same and pretty stable. That will change at some point of time during the development cycle.

_And make sure that you disable the proposed pocket. It is not designed to be used during the development cycle._

explain please. - edit - oh, pocket in launchpad. - [https://launchpad.net/ubuntu/bionic/+queue](https://launchpad.net/ubuntu/bionic/+queue)

---

### Post by privacydude on 2017-11-06
I'm running the ARM64 version of 18.04 on my Raspberry Pi 3B right now. Think you need to do an apt-get dist-upgrade or apt full-upgrade to get everything though. apt-get works better in scripts and apt is better interactively since it has a progress bar.

---

### Post by Kris_M on 2017-11-06
> **privacydude said:**
> I'm running the ARM64 version of 18.04 on my Raspberry Pi 3B right now. Think you need to do an apt-get dist-upgrade or apt full-upgrade to get everything though. apt-get works better in scripts and apt is better interactively since it has a progress bar.

Thanks - just for fun I tried both of those but got 0 things updated. The first one did give me a list of stuff to remove so I autoremoved that. The commands in my first post apparently are sufficient.

It's great to hear that you got 18.04 running on a Pi!!! Love it!!!!!

---

