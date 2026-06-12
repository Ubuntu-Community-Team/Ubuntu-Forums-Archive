---
title: "Upgrading to Jaunty (Daru3)  - Configuring LiLo"
date: 2009-04-23
forum: System76 Support
---

### Post by arepaking on 2009-04-23
Hello experts,
My upgrade installation just started and is asking me about Configuring Lilo. The question is:

"Do you want to add the large-memory option?"

What should I choose? I am using a Daru3.

Regards,
-AK

---

### Post by thomasaaron on 2009-04-23
I've not seen that before. We do not use Lilo. We use grub.

---

### Post by arepaking on 2009-04-23
So what should I do? Here is a screen shot.

If System76 uses Grub.. then could it be that my system was delivered improperly? I don't even know what Lilo is???? =(

---

### Post by jdb on 2009-04-23
> **arepaking said:**
> So what should I do? Here is a screen shot.

If System76 uses Grub.. then could it be that my system was delivered improperly? I don't even know what Lilo is???? =(

Was there a screen that asked if you wanted lilo or grub??

I you decide on lilo you'll want the large memory model:

[https://bugs.launchpad.net/ubuntu/+source/lilo/+bug/260059]("https://bugs.launchpad.net/ubuntu/+source/lilo/+bug/260059")

jdb

---

### Post by arepaking on 2009-04-23
I did not see any options to select either Grub or Lilo. As far as I know I am using Grub. 

The upgrade installation process started by asking me to increase the memory.

How could I know what am I using?

---

### Post by thomasaaron on 2009-04-23
The computer wasn't delivered improperly. We image from an imaging server. All of the computers basically get the same image. Everybody would have had Lilo.

Something had to have gone wrong in the upgrade process.

Or Lilo somehow got installed by accident. It is pretty bizarre, though.

---

### Post by Cygnia on 2009-04-23
I had the same event happen to me during the upgrade; I chose the option for the "large memory" whatsit and then proceeded. Later I got a dialogue asking whether I wanted to keep the Lilo that was locally installed, or wanted the newer package-maintainers version. I frankly assumed that System76 had installed a custom version so I reasoned that I should choose to keep the local version. I ended up getting an error message at the conclusion of the upgrade saying that Lilo had failed to either upgrade or install. I haven't had any problems and have restarted my Pangolin twice since the upgrade, but I was rather worried that something had gone wrong.

Is the gist of the earlier posts here that we don't need Lilo installed at all? If so should I remove it if it is? I was about to post about this when I saw this thread already here, so any pointers would be great. Thanks.

---

### Post by jARLAXL on 2009-04-23
Looks like somehow it is related to this:
[https://bugs.launchpad.net/ubuntu/jaunty/+source/ubiquity/+bug/314004](https://bugs.launchpad.net/ubuntu/jaunty/+source/ubiquity/+bug/314004)
but there it says fix released hmmm.
definately lilo is not the ubuntu default.
My reccomendation: Uninstall lilo in synaptic BEFORE upgrade.

---

### Post by Eldera on 2009-04-24
Arepaking
> I don't even know what Lilo is????

LILO and GRUB are bootloaders. 

As a Newbie, I copy out information I think useful and had the following in my files:

> **Wikipedia]&#8220 said:**
> 
Full article at
[http://en.wikipedia.org/wiki/Bootloaders](http://en.wikipedia.org/wiki/Bootloaders)

[quote=LILO and GRUB: Boot Loaders Made Simple
by Judith Myerson 
01/22/2008]Which Is Better? GRUB or LILO

LILO is older and less powerful. Originally LILO did not include a GUI menu choice (but did provide a text user interface). To work with LILO an administrator has many tasks to perform in addition to editing the configuration files.
GRUB is a bit easier to administer because the GRUB loader is smart enough to locate the /boot/grub/grub.conf file when booting. An administrator only needs to install GRUB once, using the "grub-install" utility. Any changes made to grub.conf will be automatically used when the system is next booted. In contrast, any changes made to lilo.conf are not read at boot time. The MBR needs to be "refreshed."

Full Article [http://www.linuxdevcenter.com/pub/a/linux/2008/01/22/lilo-and-grub-boot-loaders-made-simple.html](http://www.linuxdevcenter.com/pub/a/linux/2008/01/22/lilo-and-grub-boot-loaders-made-simple.html)

Myerson's article is slightly out of date. She says LILO is standard for most Distros. GRUB is standard in Unbuntu.

As a Newbie, on the basis of this info, I would say you need one or the other, not both, but TA or JBD or somebody else is going to have to explain 

1. How to find out what is really on your computer.

2. How to get LILO off and GRUB back, if that is what you need to do.

Don't get discouraged. Stuff happens. Sincerely, Eldera

---

### Post by arepaking on 2009-04-24
Thank you very much Eldera for your dedicated answer. I really appreciate it.

Thomas, could you please help me to find out what is on my system installed? 

One more thing, when I boot my computer prior loading Ubuntu says: GRUB Stage Load and counts 2 seconds. I thought I was always using GRUB until I saw the LiLo option in the Jaunty upgrade process.

Basically, I just want to find out if I have lilo installed and how to safely remove it from my system so GRUB can be the only bootloader.

Thanks again for your support,
-AK

---

### Post by jdb on 2009-04-24
> **arepaking said:**
> Thank you very much Eldera for your dedicated answer. I really appreciate it.

Thomas, could you please help me to find out what is on my system installed? 

One more thing, when I boot my computer prior loading Ubuntu says: GRUB Stage Load and counts 2 seconds. I thought I was always using GRUB until I saw the LiLo option in the Jaunty upgrade process.

Basically, I just want to find out if I have lilo installed and how to safely remove it from my system so GRUB can be the only bootloader.

Thanks again for your support,
-AK

Lilo & Grub are both tools that prepare, install and administer configuration files for a chunk of code that resides in the mbr (master boot record).

You can have both on your computer just like you can have several text editors & it won't hurt a thing.

The only time they do anything is when you explicitly run them.

It's the code they put in the mbr that boots the computer.


If it says "GRUB Stage Load" on bootup, then your mbr has grub code in it.

You can remove lilo with Synaptic.
Open "Synaptic Package Manager" from the System menu.
Search for lilo, right click on it, select "Mark for Complete Removal", & click on Apply.

jdb

---

### Post by wibge on 2009-04-25
I had the same problem on a system76 wildcat desktop. I started the upgrade, and it said it needed to run something lilo related in the middle of it, then at the end it said the upgrade failed due to lilo. 

Now my machine is stuck somewhere between 8.10 and 9.04. The update manager is still checking intrepid respositories, and grub says 8.10.  But I have the new gnome. I uninstalled lilo and ran restore/dpkg. Lots of small things are wrong, screen resolution, raided drives won't mount...

Highly recommend doing something about lilo before upgrading.

---

### Post by Aaris on 2009-04-26
I am also experiencing the same problem as the other users above. I have a Pangolin laptop like the OP, but I have not tried to uninstall LiLo yet. I think that I will follow the instructions to do so and report back (assuming that I can) shortly.

---

### Post by thomasaaron on 2009-04-26
I'm pretty surprised at the number of folks seeing this. When I get back in the office tomorrow, I'll load jaunty on a computer and upgrade it to see if I can figure out what's going on.

You guys might want to hold off on deleting anything (despite me advising it) until I test it.

---

### Post by Aaris on 2009-04-26
I followed the uninstall directions and restarted my laptop. It *seems* that things are running fine and that it has taken care of all of the error messages related to LiLo. I need to fix some of the other tweaks that I had made to the previous version, but I'm *pretty sure* that those issues are unrelated to this.

---

### Post by arepaking on 2009-04-26
Thomas, 

I think my system got messed up at some point during the upgrade. I've been thinking to do a fresh install but plz I need some guidance on this.

How could I achieve this without loosing the /HOME directory? Does system76 laptops comes with /HOME in a different partition right?

What about setting up the System76 Drivers option in the System->Administration menu?

Please feel free to provide any information you think I should know after doing a fresh install.

Thanks in advance,
-AK

---

### Post by thomasaaron on 2009-04-27
Hi, arepaking.

Your computer does come with a separate home partiton. In order to do a fresh install without overwriting it, you will need to manually partition your hard drive. Shoot me an email, and I'll provide more specific instructions.

And I can provide you with instructions for re-installing the System76 drivers.

Probably the best way, depending on the amount of info you have on your hard drive is to just back up your data and wipe the disk. This will reduce the risk of some corrupted config in your home dir causing problems in your new install.

---

### Post by eddietours on 2009-04-27
funny l first try to upgrade and l also got to see the Lilo pop up l then  just Backup my Data did a clean install

---

### Post by ProfDecoy on 2009-04-28
I got the Lilo notice when updating my system from 8.10 to 9.04 as well.  What I did before rebooting was to reopen synaptic and uninstall lilo and reinstall grub.

From the following entry in the 9.04 release notes, it appears that from the original 8.10 Desktop CD the package for lilo was installed along side of grub in the initial install, but was not configured.

[http://www.ubuntu.com/getubuntu/releasenotes/904#Upgrades%20from%20Ubuntu%208.10%20may%20have%20lilo%20installed](http://www.ubuntu.com/getubuntu/releasenotes/904#Upgrades%20from%20Ubuntu%208.10%20may%20have%20lilo%20installed)

---

### Post by thomasaaron on 2009-04-28
Profdecoy,

Your absolutely right on that. Why they installed it with grub in intrepid, I don't know. I also don't know why everybody upgrading isn't getting the error.

But the best workaround we've found is just uninstalling lilo.

---

