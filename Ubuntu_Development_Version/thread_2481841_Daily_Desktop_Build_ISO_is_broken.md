---
title: "Daily Desktop Build ISO is broken"
date: 2022-12-10
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2022-12-10
The Lunar Desktop daily build was broken today. It just gets to the initial desktop where the try or install popup should come up... but doesn't. I dl'ed it twice just to make sure it wasn't on my end.

Will try to test again tomorrow.

I still have earlier VM's up to check what the updates were... (For both Server and Desktop Editions)

---

### Post by ajgreeny on 2022-12-10
I havent updated my virtual install of Xubuntu for a few days now so I wonder if you are talking only of the .iso downloads being faulty or if updated installs have problems as well, though different problems, obviously.

I'll upgrade tomorrow and see what happens; so far it has run faultlessly but currently it is probably still very much almost still **kinetic** on my KVM virtual system.

I will report back ASAP after updating.

---

### Post by guiverc on 2022-12-10
@MaFoleffen   have you reported it on the ISO tracker? and filed a bug report.

All I see for today is [https://bugs.launchpad.net/ubuntu/+source/gnome-initial-setup/+bug/1999298](https://bugs.launchpad.net/ubuntu/+source/gnome-initial-setup/+bug/1999298) which maybe your issue.  If so I'll suggest please clicking the '*affects me too*'.

ISO tracker for lunar can be found here - [http://iso.qa.ubuntu.com/qatracker/milestones/441/builds](http://iso.qa.ubuntu.com/qatracker/milestones/441/builds)

---

### Post by MAFoElffen on 2022-12-11
> **guiverc said:**
> @MaFoleffen   have you reported it on the ISO tracker? and filed a bug report.

All I see for today is [https://bugs.launchpad.net/ubuntu/+source/gnome-initial-setup/+bug/1999298](https://bugs.launchpad.net/ubuntu/+source/gnome-initial-setup/+bug/1999298) which maybe your issue.  If so I'll suggest please clicking the '*affects me too*'.

ISO tracker for lunar can be found here - [http://iso.qa.ubuntu.com/qatracker/milestones/441/builds](http://iso.qa.ubuntu.com/qatracker/milestones/441/builds)

Now I know where that page is and how to get to it. I understant using ubuntu-bug and apport, but how do you report a bug from a 'non-functioning' ISO image? I could get to a TTY but was not able to login to get to a prompt. I tried all the usual suspects... (combinations)

---

### Post by MAFoElffen on 2022-12-11
I edited the grub menu to boot it into rescue mode to get to a root prompt. 

I joined that bug as "Affects me."

---

### Post by guiverc on 2022-12-12
> **MAFoElffen said:**
> Now I know where that page is and how to get to it. I understand using ubuntu-bug and apport, but how do you report a bug from a 'non-functioning' ISO image? I could get to a TTY but was not able to login to get to a prompt. I tried all the usual suspects... (combinations)

Sorry I missed the reply @MAFoElffen

I just file online using a  +FileBug *type of* link that exists somewhere on the page  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs), fill in as many details  as I can, then link it to the ISO (entering launchpad bug ID) in an entry on iso.qa.ubuntu.com for the ISO/daily you're testing  (so it enters the ISO tracking QA reports & they have that failure recorded against the ISO you had issues with).  Shortly after this you'll receive an email telling you the two are linked.

---

### Post by MAFoElffen on 2022-12-12
The past 3 days, the ISO are all broken in the same way. Since it is a "daily", should I have filed 3 bugs? Yesterday I added an entry into the Bug I joined the day earlier noting is was still broken.

---

### Post by guiverc on 2022-12-12
Nah, you file a bug when the bug is first encountered (*or hit affects me too* *on an existing bug*), later reports are made only on the ISO.QA tracker.

eg. the bug report I first provided was [https://bugs.launchpad.net/ubuntu/+source/debian-cd/+bug/1999298](https://bugs.launchpad.net/ubuntu/+source/debian-cd/+bug/1999298)

where you can see what ISOs were reported as being affected by following the *link* to [https://iso.qa.ubuntu.com/qatracker/reports/bugs/1999298](https://iso.qa.ubuntu.com/qatracker/reports/bugs/1999298) which shows reports for ISOs 20221210, 20221211, & 20221212 currently..

ie. subsequent reports were filed on iso.qa.ubuntu.com & reported as FAILURES and that bug report was used as linked cause.

That bug was reported against the Ubuntu Desktop amd64 ISO for *lunar*, so the Ubuntu Desktop Team will receive it in their listing of current issues automatically tracked (*from data gained from iso.qa.ubuntu.com*).  They'll adjust as necessary, which you can note with [Seb128's last comment]("https://bugs.launchpad.net/ubuntu/+source/debian-cd/+bug/1999298/comments/8")

>      Thanks, it's not an issue with debian-cd but with the switch to the new canary image and invalid kernel option.

 Adding layerfs-path=minimal.standard.live.squashfs to the kernel parameter should workaround it

 The issue has also been fixed in debian-cd now which is what sets the default so the next ISO build should work again


                  
Thank you all for your QA testing & reporting of issues. It helps make Ubuntu better.

---

### Post by leok2 on 2022-12-13
Now working again...

---

### Post by leok2 on 2022-12-13
Tested agin today 2022-12-13 daily ISO Ubuntu Lunar and now a new bug - unable to login after install -  [https://bugs.launchpad.net/ubuntu/+bug/1999506](https://bugs.launchpad.net/ubuntu/+bug/1999506) - 

Has anyone else encountered this?

---

### Post by MAFoElffen on 2022-12-13
> **leok2 said:**
> Tested agin today 2022-12-13 daily ISO Ubuntu Lunar and now a new bug - unable to login after install -  [https://bugs.launchpad.net/ubuntu/+bug/1999506](https://bugs.launchpad.net/ubuntu/+bug/1999506) - 

Has anyone else encountered this?
Coffee is on and waiting on my DL's to finish. Getting ready... Caffeine first.

EDIT:
gnome-initial-setup starts. I get the language selection with two buttons mostly cutoff on the bottom... Enough that you cannot read what they are for. If I select the left button, nothing. Right button brings up the "Try / Install" chooser. Where the outline on them changes, depending what you choose, but goes nowhere from there. I at least get the Run on <Alt-F2>, and can get to gnome-terminal, where I read the syslog... I can see where I select either button control, then it gets and "unconfined" exception from snap package ubuntu-desktop-installer... [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/1999560](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/1999560) (i9-10900) This had new ubuntu-desktop-installer UI. 

EDIT2: KVM (i7-2760QM) finished successfully. First startup, logged in, but gnome-initial setup was only 3"x1". Just large enough to show the skip buttons. LOL This showed with the old ubuntu-desktop-installer UI. All subsequent new users, the UI was fine(???) (Taught me to take screenshots as problems arise...)

Same ISO image for both above...

---

### Post by MAFoElffen on 2022-12-13
@leok2

I got past my bug, and then it evolved into your bug. I killed Xorg, which got the resolution fixed and repainted the UI. I could then saw that there were buttons at the bottom (that had been cutoff previously). Successful install messaging, but did not result in an actual successful install. I quit the first boot process at 30 minutes. There it was hung on a boot process cleanup job. I tied both bugs together.

---

### Post by guiverc on 2022-12-13
I believe I saw reference to the latest issue ([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1999506](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1999506)) yesterday, so probably someone asked on IRC, or a bug passed by on #ubuntu-bugs-announce   (*which may mean a duplicate as you've already had confirmation - I'll look for it soon*)

---

### Post by MAFoElffen on 2022-12-15
[https://bugs.launchpad.net/ubuntu/+bug/1999506](https://bugs.launchpad.net/ubuntu/+bug/1999506) ... Note #10. I found a fix where "the problem was" in the installed image.  I have a working (fixed)  install image from today.

Hopefully they will take that and run with it.

---

### Post by MAFoElffen on 2022-12-16
Installer builds a working install image today. I had 2 good installs. 1 each Intel and AMD hosts. Noticed leak2 had 2 good installs...

I did notice that even though the installs went fast, that I had 2 vCPU's allocated with 4GB RAM, and the installer pegged both. Disk utilization was low during that. But successful from daily-lunar-desktop-20221216-amd64.iso

And the new UI still shows as oversized on the first two panels for me, until I exit to the desktop and restart the installer. So that bug is still not resolved.

---

### Post by guiverc on 2022-12-16
I'm thankful for your testing @MAFoElffen.  Thank you. :P

It's after 11am local & I've not even finished scanning my inbox/askubu/UF/etc feeds for what occurred *as I slept* or *stuff *I didn't get to yesterday... (*and I started this scanning at ~8:20 when I'd completed with my bird feed*).

My QA testing is a *fraction* of what it used to be, as I'm spending time elsewhere now.  For Lubuntu I'm not worried though, as [Leó]("https://launchpad.net/~leok") *expertly *covers our [Lubuntu] *install *testing (*some of other flavors & main Ubuntu too!*), and [David (KGIII/uninvolved)]("https://launchpad.net/~uninvolved") covers Lubuntu QA extremely well as regards our UI & apps.  I've very much relied on their QA in my decision to spend my time elsewhere in the Ubuntu world  

*I still do QA when I have time on the older hardware I have, but still haven't started with lunar yet; the new installer needs it as I've not had much luck with it for non-full disk installs regularly, but I need the time*.

---

### Post by MAFoElffen on 2022-12-19
Build 20221219 has a bad memory leak. My rerun at 18GB RAM was successful, but pegged that 18GB during the install. leok2's successful instal was with 32GB of RAM...

I got picky on the UI of the new installer and problems in it. (I have 4 open bugs on the UI.)

---

### Post by guiverc on 2022-12-20
:( on memory leak...

My most used boxes for QA test installs have 4GB & 5GB, so I suspect I'd not have much luck if I tried.
I'll endeavor to give it a try when I can.

---

### Post by MAFoElffen on 2022-12-25
Manual partition on ZFS filesystem is no-go. Instant Installer failure.

LVM2 with encryption, (work-around) use <Down-Arrow> after it stops booting to get to the text console dm-crypt console unlock dialog... The graphical unlock dialog does not appear at all.

---

