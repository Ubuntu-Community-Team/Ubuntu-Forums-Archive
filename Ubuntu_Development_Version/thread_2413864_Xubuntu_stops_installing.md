---
title: "Xubuntu stops installing"
date: 2019-03-02
forum: Ubuntu Development Version
---

### Post by VMC on 2019-03-02
Trying to install Xubuntu disco on my Acer 885, it stops on "Updates and other software". There is a grayed out mention of secure boot at the bottom of the dialog.

Special attention: Ubuntu, budgie, Lubuntu, Deepin, and more can be installed without incident. Only Xubuntu. I unchecked Download updates. No change.


edit: I turned off Secure Boot, and on reboot, the configure Secure Boot was gone, but the install still hung up on  "Updates and other software".

New [BUG REPORT]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1818586")

---

### Post by kc1di on 2019-03-03
Hello VMC, 
Does the live session work ok?  If so in the live session install gparted if it's not already there and give us screen shot of your partitions.  I don't believe that it's actually hanging because of the software page, Unless you do not have an internet connection. But is hanging do to the partitioning which is the next step in the install sequence. 
Give us a look at your disk partitioning.

---

### Post by VMC on 2019-03-03
The live session works fine, network is on. Unsure what seeing partitions matter, as several other distros install without issue, but here it is :
[sda8 was where I wanted to store xubuntu]

---

### Post by VMC on 2019-03-03
I just installed a new empty hard drive. Xubuntu failed again. Ubuntu installed again without issue.

---

### Post by kc1di on 2019-03-03
I'm not sure what the problem with xubuntu is , if ubuntu installs xubuntu should as well.  Did you check the checksum on the download?
Is it possible you have a bad burn?

---

### Post by VMC on 2019-03-03
> **kc1di said:**
> I'm not sure what the problem with xubuntu is , if ubuntu installs xubuntu should as well.  Did you check the checksum on the download?
Is it possible you have a bad burn?
Several times. I just downloaded Fedora, and it too works without issue. Something with xubuntu.

---

### Post by PaulW2U on 2019-03-03
> **VMC said:**
> but the install still hung up on  "Updates and other software".
Same here installing today's Xubuntu image in KVM (GNOME Boxes). Unchecking the options to download updates or install 3rd party software makes no difference.

Looks like bug [#1818285]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1818285")

---

### Post by VMC on 2019-03-03
> **PaulW2U said:**
> Same here installing today's Xubuntu image in KVM (GNOME Boxes). Unchecking the options to download updates or install 3rd party software makes no difference.

Looks like bug [#1818285]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1818285")
That header on the bug report "[disco desktop] Installation fails with parted_server: No data in infifo. parted_server: Line 2387. CRITICAL ERROR!!! EXITING.", is not what I'm getting. I get nothing, as the image above shows. No errors, just hangs and doesn't freeze.

edit: although post#5 of bug report, reflects what I'm getting.

---

### Post by PaulW2U on 2019-03-04
> **VMC said:**
> I get nothing, as the image above shows. No errors, just hangs and doesn't freeze.
I was confused by that at first. I don't think the error message was being quoted as something seen on screen but as a [result of automatic testing]("https://discourse.ubuntu.com/t/monday-4th-march-2019/10020/4?u=paulw2u") and can also be found in the logs.

---

### Post by kc1di on 2019-03-04
You both do know that disco is still in development and will not be stable.  But you should file bug reports so that it will help the Devs to sort it all out before the release date.

---

### Post by PaulW2U on 2019-03-04
> **kc1di said:**
> You both do know that disco is still in development and will not be stable.  But you should file bug reports so that it will help the Devs to sort it all out before the release date.
Yes, I've been running the development version of Ubuntu or one of it's flavours since Maverick Meerkat and have reported dozens of bugs against the development version since 2010. Some have been fixed within 24 hours. :D

However, before filing a **new** report it's often best to post here to see if anyone else if affected and to gather more information about the problem. Sometimes the filing a bug report isn't actually necessary if it is found to be a short term problem caused by the development process itself, e.g. unresolvable dependences awaiting a new or updated package.

Anyway, as an update, the issue that was reported in this thread, [bug #1818285]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1818285"), is now at 'Critical' importance and is currently being worked on so Xubuntu should be installable again soon.

---

### Post by makitso on 2019-03-04
The latest build broke ubiquity on all flavors. The 2/28 build works.

[URL="https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/1818285"]https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/1818285 [CENTER][COLOR=#919191]4[/COLOR][/CENTER]
[/URL]

---

### Post by VMC on 2019-03-04
> **PaulW2U said:**
> I was confused by that at first. I don't think the error message was being quoted as something seen on screen but as a [result of automatic testing]("https://discourse.ubuntu.com/t/monday-4th-march-2019/10020/4?u=paulw2u") and can also be found in the logs.
That's an interesting link you gave. Never been there b4. I am going to try again using 'ubiquity -d' and check the logs '/var/logs/installer'. I just checked the terminal for errors and nothing.

---

### Post by VMC on 2019-03-04
> **makitso said:**
> The latest build broke ubiquity on all flavors. The 2/28 build works.

[URL="https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/1818285"]https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/1818285 [CENTER][COLOR=#919191]4[/COLOR][/CENTER]
[/URL]

I didn't see your input so I added my own bug report on first post. But I have no issues with L or Ubuntu. Kubuntu same issue. My *ubiquity -d *output is different from there's.

---

### Post by VMC on 2019-03-05
> **makitso said:**
> The latest build broke ubiquity on all flavors. The 2/28 build works.

[URL="https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/1818285"]https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/1818285 [CENTER][COLOR=#919191]4[/COLOR][/CENTER]
[/URL]

Looks like fix released:  "[COLOR=#333333][FONT=monospace]This bug was fixed in the package ubiquity - 19.04.6.1" 2 hours ago, so I will mark this topic solved.[/FONT][/COLOR]

---

### Post by PaulW2U on 2019-03-05
> **VMC said:**
> Looks like fix released:
A new **Ubuntu** ISO was issued about an hour ago and I've just installed it in KVM. Today's earlier ISO wouldn't install so the problem is fixed. Presumably the releases for the flavours will follow at their normal times.

---

### Post by VMC on 2019-03-05
> **PaulW2U said:**
> A new **Ubuntu** ISO was issued about an hour ago and I've just installed it in KVM. Today's earlier ISO wouldn't install so the problem is fixed. Presumably the releases for the flavours will follow at their normal times.
I never had issue with Ubuntu. Only Xubuntu & Kubuntu.

---

### Post by mc4man on 2019-03-05
> **VMC said:**
> I never had issue with Ubuntu. Only Xubuntu & Kubuntu.

That's because the [Ubuntu image ]("http://cdimage.ubuntu.com/daily-live/current/disco-desktop-amd64.manifest")never went past ubiquity 19.04.5, the issue was with 19.04.6, fixed with 19.04.6.1

---

### Post by PaulW2U on 2019-03-05
> **VMC said:**
> I never had issue with Ubuntu.
I did.
> **mc4man said:**
> That's because the [Ubuntu image ]("http://cdimage.ubuntu.com/daily-live/current/disco-desktop-amd64.manifest")never went past ubiquity 19.04.5, the issue was with 19.04.6, fixed with 19.04.6.1

The Ubuntu image **did** receive Ubiquity 19.04.6 - images 20190304, [20190305]("http://cdimage.ubuntu.com/daily-live/20190305/disco-desktop-amd64.manifest") and probably a few more earlier but those images never moved from 'pending' to 'current'.

VMC, I think you downloaded the 'current' Ubuntu image but I downloaded or at least zsynced the latest image which was still shown as 'pending'. I picked up some bad images whereas you didn't.

---

### Post by VMC on 2019-03-05
I zsynced the latest ubuntu, and no change from the one I installed. Kubuntu is still not installing. Same issue as xubuntu. ubiquity 19.04.6

edit: Strange. I've been zsync'ing ubuntu amost everyday. And my latest shows "ubiquity-ubuntu-artwork 19.04.5". Dated Tue 05 Mar 2019 10&#8758;01&#8758;28 AM PST. I'll try again now.

edit2: I just zsynced ubuntu. Same date, same ubiquity. what world am i in that it won't give up latest ubic.
edit3: I think I found my problem. I zsync 'current' instead of 'pending' which is newer.
edit4: Its all good now. Both xubuntu & kubuntu install.

---

