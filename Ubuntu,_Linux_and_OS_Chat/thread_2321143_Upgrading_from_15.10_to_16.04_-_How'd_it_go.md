---
title: "Upgrading from 15.10 to 16.04 - How'd it go?"
date: 2016-04-20
forum: Ubuntu, Linux and OS Chat
---

### Post by frogotronic on 2016-04-20
Hi All,

  If you've done the upgrade from 15.10 to 16.04, how'd it go?

---

### Post by RobGoss on 2016-04-20
I was on 14.04 and just did a fresh install of 16.04, I did not have much to loose so I went this route and everything is smooth going.

---

### Post by oldfred on 2016-04-20
I also am a clean install fan.

I upgraded from 6.06 thru 9.04 every 6 months, but back then major issues with nVidia and editing files to get it to work.
With 9.10 I had to do a clean install to convert from 32bit to 64bit and absolutely no issues. So I always allocate another 25GB and install to a new / (root) partition. I keep old install as long as I have room on drive, so I can go back if necessary.

I have been running 16.04 on a new Skylake SFF system I built to replace laptop. Did not need a portable system anymore.
And I just did a new install of 16.04 over my older 16.04 install on my main Desktop Haswell based system, just to houseclean most of the many updates during development. No issues at all, so far. But still have 14.04 to go back to if necessary.

---

### Post by frogotronic on 2016-04-20
> **oldfred said:**
> I also am a clean install fan.

I upgraded from 6.06 thru 9.04 every 6 months, but back then major issues with nVidia and editing files to get it to work.
With 9.10 I had to do a clean install to convert from 32bit to 64bit and absolutely no issues. So I always allocate another 25GB and install to a new / (root) partition. I keep old install as long as I have room on drive, so I can go back if necessary.

I have been running 16.04 on a new Skylake SFF system I built to replace laptop. Did not need a portable system anymore.
And I just did a new install of 16.04 over my older 16.04 install on my main Desktop Haswell based system, just to houseclean most of the many updates during development. No issues at all, so far. But still have 14.04 to go back to if necessary.

Does 16.04 offer the ZFS as default on a clean install?

---

### Post by Bucky Ball on 2016-04-20
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not support.

---

### Post by oldfred on 2016-04-20
Do not know about ZFS. I always partition with ext4 in advance with gparted. Primarily still reusing 25GB partitions with old installs.

---

### Post by vasa1 on 2016-04-21
I know you asked about 15.10 > 16.04 but I upgraded from 14.04 > 16.04 yesterday and absolutely no complaints.

---

### Post by Bucky Ball on 2016-04-21
> **vasa1 said:**
> I know you asked about 15.10 > 16.04 but I upgraded from 14.04 > 16.04 yesterday and absolutely no complaints.

That's excellent news! Standard Ubuntu desktop version?

---

### Post by vasa1 on 2016-04-21
> **Bucky Ball said:**
> That's excellent news! Standard Ubuntu desktop version?
No, Lubuntu 14.04 > Lubuntu 16.04.

Upgrading wasn't my first choice or what I had planned at all. But, for whatever reason, I just couldn't get net connectivity which is essential even for the clean install. When I booted back from my hard disk and my existing OS, connectivity was fine. So I took a chance and went the upgrade route.

---

### Post by Tanker Bob on 2016-04-22
I upgraded from 15.10 to 16.04 with no problems. NVidia driver updated fine. VMWare Workstation 12 even still works. Very smooth upgrade.

---

### Post by maglin2 on 2016-04-24
15.10 to 16.04 apparently went smoothly here. Haven't discovered anything that isn't working yet.

---

### Post by SantaFe on 2016-04-24
Ubuntu-MATE 15.10 to Ubuntu-MATE 16.04.  No Problems.  Think I'll leave it on LTS updating this time around, unless 16.10 has something I just GOTTA have. ;)

---

### Post by recurringvisitor on 2016-04-24
Upgraded from 14.04 to 15.10 first because it was the only distribution offered through software updates (forum helped lots with helping me understand this). I got a black screen (amd radeon) during the upgrade but fixed that and went straight to 16.04 without any problems so far.

---

### Post by Bucky Ball on 2016-04-25
For future travelers: 14.04 LTS *does* go directly to 16.04 LTS right now. You just won't get offered that option by the GUI and need to upgrade to 16.04 LTS manually via a terminal. You don't need to go through 15.10. 

The option to upgrade from 14.04 to 16.04 will be offered through the GUI after the first point release in a few months (16.04.1 LTS). 

@ recurringvisitor: Glad it all worked out for you anyway. :)

---

### Post by n3on-samurai on 2016-04-25
> **Tanker Bob said:**
> I upgraded from 15.10 to 16.04 with no problems. NVidia driver updated fine. VMWare Workstation 12 even still works. Very smooth upgrade.


Lucky, on a clean install the only thing i cant get working atm is VMware workstation 12.1.1 :(

Im really wanting to upgrade too.

---

### Post by Shobuz99 on 2016-04-25
> **vasa1 said:**
> I know you asked about 15.10 > 16.04 but I upgraded from 14.04 > 16.04 yesterday and absolutely no complaints.

I'm planning on doing the same thing: 14.04 LTS to 16.04 LTS. 
I don't anticipate any problems, unless I make a mistake at how I'm doing this.
I get the distinct impression that a "clean" upgrade is better than risking a 14.04 that has a large amount of my own data files. 
But I'm choosing to upgrade over 14.04 LTS and all my data files, that should remain untouched.
I'm planning on backing up the 14.04 with Clonezilla, to an empty HDD, for safety.
Then I will attempt to upgrade from 14.04 LTS to 16.04 LTS and simply wait to see if I run into any issues.
I don't expect any. I've already "tried" 16.04 LTS from live disk and it looks and works really good for me.

Since this is Not a support-help question, I hope to come back when I've finished and give a full report.
It would be helpful to me if someone here, reports on the same upgrade process that I'm using, before I do.
Maybe I'll see a clearer path, before I actually Press Enter.... :o 
I've been an Ubuntu user since 6.10, in 2006 and Windows older versions are just a distant memory for me...:D

Shobuz99

---

### Post by echotech2 on 2016-04-26
Upgraded 15.10 when Software Updater showed 16.04 available.  Only problem: For some unknown reason Thunderbird failed to keep it's profile and mail.  Restored .Thunderbird directory from backup and all is well.

---

### Post by pauljw on 2016-04-26
> **Shobuz99 said:**
> I'm planning on doing the same thing: 14.04 LTS to 16.04 LTS. 
I don't anticipate any problems, unless I make a mistake at how I'm doing this.
I get the distinct impression that a "clean" upgrade is better than risking a 14.04 that has a large amount of my own data files. 
But I'm choosing to upgrade over 14.04 LTS and all my data files, that should remain untouched.
I'm planning on backing up the 14.04 with Clonezilla, to an empty HDD, for safety.
Then I will attempt to upgrade from 14.04 LTS to 16.04 LTS and simply wait to see if I run into any issues.
I don't expect any. I've already "tried" 16.04 LTS from live disk and it looks and works really good for me.

Since this is Not a support-help question, I hope to come back when I've finished and give a full report.
It would be helpful to me if someone here, reports on the same upgrade process that I'm using, before I do.
Maybe I'll see a clearer path, before I actually Press Enter.... :o 
I've been an Ubuntu user since 6.10, in 2006 and Windows older versions are just a distant memory for me...:D

Shobuz99

Just my opinion now, but I don't understand your rush to move to 16.04.  14.04 is stable and supported until 2019.  Why not wait at least until the .1 release where the major bugs will be worked out and it will be relatively safe to upgrade.  

I don't know what your system capabilities are, but I'm currently using 16.04 in a virtual machine on my 14.04 laptop.  I like it, it seems to run well and if a bug comes along and screws it up, my 14.04 host is safe and secure.

Just a thought...

Paul

---

### Post by Shobuz99 on 2016-04-26
> **pauljw said:**
> Just my opinion now, but I don't understand your rush to move to 16.04.  14.04 is stable and supported until 2019.  Why not wait at least until the .1 release where the major bugs will be worked out and it will be relatively safe to upgrade.  

I don't know what your system capabilities are, but I'm currently using 16.04 in a virtual machine on my 14.04 laptop.  I like it, it seems to run well and if a bug comes along and screws it up, my 14.04 host is safe and secure.

Just a thought...

Paul
Thanks for that pauljw!
I guess I'm not in a *big* rush; but I just bought a new 250GB SATA drive for my Dell Inspiron 1525, because the 160GB is giving warnings
that it will fail soon. ([COLOR="#FF0000"]DISK IS LIKELY TO FAIL SOON [/COLOR](45° C / 113° F)).
I thought that if I was going to put an image of my current 14.04.3 on the new drive, I might as well upgrade to 16.04 now that it's at LTS.
You DO make a good point though about the .1 release. What is the average timeline for a .1 release to come out?
Maybe I'll take your advice on the upgrade and then just clone the 14.04 image to the new drive, as I planned and wait for the .1 release
for 16.04 LTS... I appreciate your opinion. It makes sense. Thank you. :)

Shobuz99

---

### Post by kevdog on 2016-04-27
It was on 14.04 and went the upgrade route through the terminal however it stuck me on 15.10 and then I upgraded to 16.04.  I had a problem with dns resolution, and the upgrade would fail at that point.  I had to change my dns servers to google dns servers and then all worked well from that point on.  I running Ubuntu Mate, however I'm probably guessing this would have happened in any Ubuntu spin since the problem isn't Mate specific.  Honestly since I run the machine as basically a file server, I don't see a lot of difference.  When trying to upgrade through the terminal, I tried doing it over ssh, which was neat at first since it opened up an alternative port 1022 since the main ssh port was closed sometime during the installation.  The only issue however was when I ran into the DNS resolution problem, there was no error produced and there wasn't any feedback. In fact when I went to the main machine the monitor wouldn't come out of sleep.  I had to kill the installation from the ssh command line and then when the system was rebooted, it booted into a command line without any gui.  I was able to fix the problem from that point (or let's hope I was -- all seems well).

---

### Post by mholmes on 2016-04-27
Has anybody upgraded a desktop system with disk or partition encryption yet? I have a 15.10 system using full-disk encryption that I'm thinking about upgrading, but it's the first system I ever set up with disk encryption so I'm a little wary of a release upgrade.

---

### Post by maglin2 on 2016-04-27
I have full disk encryption and the upgrade went smoothly.

---

### Post by pauljw on 2016-04-27
> **Shobuz99 said:**
> Thanks for that pauljw!
I guess I'm not in a *big* rush; but I just bought a new 250GB SATA drive for my Dell Inspiron 1525, because the 160GB is giving warnings
that it will fail soon. ([COLOR="#FF0000"]DISK IS LIKELY TO FAIL SOON [/COLOR](45° C / 113° F)).
I thought that if I was going to put an image of my current 14.04.3 on the new drive, I might as well upgrade to 16.04 now that it's at LTS.
You DO make a good point though about the .1 release. What is the average timeline for a .1 release to come out?
Maybe I'll take your advice on the upgrade and then just clone the 14.04 image to the new drive, as I planned and wait for the .1 release
for 16.04 LTS... I appreciate your opinion. It makes sense. Thank you. :)

Shobuz99

Well, I just hate to see someone with a stable system risk it on an upgrade.  Been there and it's not fun.  I think I read July is when the .1 is expected.  I hope whatever you decide works out for you.  Be sure to backup your important files before the upgrade.

Paul

---

### Post by jimc2 on 2016-04-28
I put 15.10 on an old windows machine and tried to do an upgrade from there to 16.04 LTS. Didn't work with my limited knowledge of Ubuntu. I use Rufus tool to put 16.04 on a thumb drive. Booted to it and it all went well. I have tried Ubuntu a few times in the past, would always dual boot it. I have gotten further with this 16.04 that any older version. I use windows and Mac's to, but I'm getting tiered of all the BS they are handing out with their new OS's. I built this machine 7 years ago, hope it holds up a few more.

---

### Post by lukeiamyourfather on 2016-05-11
> **cement_head said:**
> Does 16.04 offer the ZFS as default on a clean install?

No but it's possible to do ZFS as the root file system with a few extra steps.

---

### Post by Christopher_Waldon on 2016-05-15
I did an upgrade from 15.10 to 16.04 that had many issues. I documented the problems [here.]("http://ubuntuforums.org/showthread.php?t=2324040") It's all kinda working now, though I get many error messages on boot.

---

### Post by RichardET on 2016-05-16
As far as going from 14.04 to 16.04, I would think before you switch - 14.04 is the last great systemd free OS, still standing.

---

### Post by blaze24-matrix on 2016-05-16
I upgraded from 15.10 to 16.04, and for me the difference is bigger. 16.04 takes to long to load, plus some problems with the video driver...

---

### Post by RichardET on 2016-05-16
> **blaze24-matrix said:**
> I upgraded from 15.10 to 16.04, and for me the difference is bigger. 16.04 takes to long to load, plus some problems with the video driver...


I upgraded from 15.10 to 16.04 last week, things were not as I expected and I ended up rolling back to 14.04;  At this point I will probably wait for 16.10;  In general I like the LTS releases, but the broadcom wireless seems to work best, for whatever reason, with the code base in the xx.10 releases.

---

### Post by Bucky Ball on 2016-05-16
> **RichardET said:**
> As far as going from 14.04 to 16.04, I would think before you switch - 14.04 is the last great systemd free OS, still standing.

Noted but as this thread is intended for users to post their experience of 15.10-16.04 upgrades and doesn't concern 14.04 -16.04 upgrades, not sure how helpful that will be. There is another thread around dealing with how you went with 14.04-16.04, from memory. ;)

---

### Post by Robert_Cline on 2016-05-17
I just upgraded from 14.04 to 16.04, on my laptop & HTPC, no problems, except Totem/Videos is now completely different... works great for streaming Netflix & YouTube with the proprietary drivers from NVIDIA.

---

### Post by sritacco on 2016-05-18
On Lenovo Yoga 3 Pro... 15.10 -> 16.04 NOT SO SMOOTH!  No Broadcom Wireless driver had to resolve that by connecting up to wired ethernet download the driver, etc.
It still doesn't shutdown :-(

---

### Post by monkeybrain20122 on 2016-05-22
I don't do upgrade, always fresh install. Installed xenial on a Toshiba Satellite the other day. Wow I am impressed. Everything works (except for a problem with appstream which was fixed in proposed) Boot in 3 seconds!

---

### Post by RichardET on 2016-05-23
I finally made a clean break from earlier versions, and now have a clean install of Xubuntu 16.4, and it seems pretty good.   Xubuntu will always be my main laptop OS for my non-Windows systems.

---

### Post by RichardET on 2016-05-23
> **sritacco said:**
> On Lenovo Yoga 3 Pro... 15.10 -> 16.04 NOT SO SMOOTH!  No Broadcom Wireless driver had to resolve that by connecting up to wired ethernet download the driver, etc.
It still doesn't shutdown :-(

This Lenovo B590 always has issues with Broadcom.  Broadcom must be cheap or something.

---

### Post by alex542 on 2016-05-23
I was using 15.10 with absolutley no problems. On 16.04 had sound proble as I posted earlier. Trying to solve it.

---

