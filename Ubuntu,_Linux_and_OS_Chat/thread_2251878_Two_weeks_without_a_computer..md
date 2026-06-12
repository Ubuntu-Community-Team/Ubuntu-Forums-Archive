---
title: "Two weeks without a computer."
date: 2014-11-07
forum: Ubuntu, Linux and OS Chat
---

### Post by irv on 2014-11-07
Laptop motherboard went out and had to send it in for repairs. Got it back two days ago. When I sent it in all I had on it was Ubuntu 14.04LTS. The techs would not work on it until they put it back to factory, (Win 8).
When I got it back I had to start from scratch. After setting up 8.0 and doing all the updates, I then had to download and install 8.1 Then had to get all my programs downloaded and installed. (my data is in the cloud). Took about 7 hours. Last night I installed Ubuntu 14.04 after splitting the drive in half. It took about 20 minutes to install and another 10 minutes to get a few programs I use. So glad to be back in Ubuntu again.

---

### Post by TheFu on 2014-11-07
7 hrs?!!
Think I'd look into a better backup/restore method that would take ... 45 min going forward.

---

### Post by pqwoerituytrueiwoq on 2014-11-07
i can confirm doing a windows 8 install takes all day

---

### Post by irv on 2014-11-07
I was doing the downloads and upgrading over the wifi, which is a 22 mb, it took so long I got a cable and increased the download speed to 56 mb. That helped a little.
I now have a nice clean install.
[ATTACH=CONFIG]257810[/ATTACH]

---

### Post by sports fan Matt on 2014-11-07
When I used to have Windows 8, (upgraded from 7) even on a 50/50 MB connection it took roughly 6 hours to install 8>8.1>updates so I feel your pain.

---

### Post by TheFu on 2014-11-07
> **TheFu said:**
> 7 hrs?!!
Think I'd look into a better backup/restore method that would take ... 45 min going forward.

If you had a good backup that can be restored to bare metal, this would have been 45 min.
Options: partimage, clonezilla, fsarchive .... there are lots of F/LOSS options and they work for Windows.
For Linux, I don't do image-based backups.

For example, was at a hacker CON last week playing on an extremely hostile network. Before I left, I made a last minute backup (have nightly, automatic, backups already) - wiped the Ubuntu partitions and spent 20 min installing a base server with openbox and my ansible based-packages-task. Didn't want to leak any data accidentally, but wanted remote access capabilies and nominal security settings.  Then patched the fresh OS completely. 

Got to the conference, hopped on the CTF (Capture the Flag) competition network and started monitoring other teams (I'm not a competitor, just a judge).  About 2 hrs in, I noticed my box behaving funny. Read-only file system, different (completely) passwd and group files ... the box had been popped, pwned, taken. It wasn't under my complete control anymore, so cannot be trusted. I hadn't expected that, but no great loss either. I think they got me through a DHCP hole.

Later that night, I booted off a bootable USB drive and wiped everything again, installed a fresh based server with openbox again using the hotel wifi (different hotel than the conference), loaded up my presentations from non-internal storage (all HTML-based). The next day I had a few presentations to give. I didn't get on any network that day at the conference.  Presentations worked perfectly, as expected.

Getting back home on Monday, it was time to go back to my personalized version of the machine with all my data.  Loaded the base server with openbox (my standard, if you haven't guessed), put my settings, and data back where it belonged, the used a list-of-installed packages from the backup process and told aptitude to install them all. 45 min from wipe to done.  It is a netbook with only 26G of data. I don't keep much data on that box on purpose. For more details about the backup/restore method and the commands used: [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview)

Of course, for Windows, an image-based backup seems to be the only method that works. Plus it must be performed **before** needed.  For me, quarterly seems to be enough, but I don't use Windows much.

---

### Post by sports fan Matt on 2014-11-07
I boot into Windows rarely these days as well, it will be more so around March (storm chaser) so i'll need it for my GR 2 Analyst (Gibson Ridge high resolution radar). I spend more time with my Mac Yosemite in VMware then Windows these days, but 90 percent of the time I'm in Ubuntu.

---

### Post by irv on 2014-11-07
After installing all the updates in 8.0 and before installing 8.1 it rebooted 4 times and the last time it came up with a message something like this:
> Some updates failed to load, re-installing old files, do not shutdown computer.
This took over two hours, and then I had to start all over again.

---

### Post by sports fan Matt on 2014-11-07
Irv, I always had issues with Windows 8.1 as well.

---

### Post by taipan4000 on 2014-11-07
About 6 months I had to reinstall Windows 7 onto a laptop after the hard drive failed. The reinstallation from disks was quick & easy, but getting all the updates from the web took about 7 hours. Then all the user data had to be reinstalled from backups. A week ago I had to reinstall Ubuntu 14.10. It was so much quicker! I much prefer Linux to Windows.

---

### Post by Bucky Ball on 2014-11-07
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by irv on 2014-11-08
I am not a fan of Chrome OS, but I like how easy it is to use for my wife. She is on her second Chromebook and I never had to re-install anything because everything run on the Internet. The OS is always up-to-date. All settings are saved in a person's account. I have a login for her and one for myself if I ever have to jump on it. When I was without a computer for that two weeks I jumped on it a few times to check email etc. I got her the 13" 1920X1080 Samsung. I think it is the nicest one out; light wt. nice feel, nice keyboard, 8 hour battery life. If all you do is Internet you can't go wrong. I like it better then any tablet I've used.
I wish someone would come up with Ubuntu-on-line OS just like Chrome. I think everyone would be using it.

---

### Post by oldrocker99 on 2014-11-08
ChromeOS is a cut-down version of a full Linux distribution, and, given Google's reliance on Ubuntu (it's the standard Google OS onsite, slightly forked and called Googlebuntu, although workers are welcome to bring their own devices), it's at least likely that that was the starting point.

And, by the way, after 5 years of using Ubuntu and attempting to make a dual-boot machine (on which I deleted the Windows partition last summer, hating its various annoyances, especially a frozen mouse pointer, which worked in Safe Mode, and then was frozen upon reboot), I was astonished at just how long a Windows installation takes. After the OS is installed, driver installation and rebooting after every driver's installation, it can take upwards of two hours, and that doesn't count Windows updates.

One of my other [sarcasm mode] favorite features of Windows is its insistence on rebooting your machine after an update, whether an important program is running or not. Compare that to Ubuntu's "The computer must be restarted to complete updates. Do you want to reboot now, or later?" [paraphrasing here.]

Not to mention that Linux stops processes that are being upgraded, and then starts them again. "Windows cannot install upgrades while the system is running." **SO** advanced. 

Also there's the viruses. I recently saw a commercial for some anti-virus program, which touted its 93% score at detecting and removing viruses, which was better than the other a-v programs they named. 7% of all the viruses out there is still a boatload of viruses, and even the best a-v program cannot possibly remove or even detect them all.

Viruses on Linux? No such thing. Yes, there were two vulnerabilities found in the last year (openSSL, which was vulnerable to Heartbleed, and bash more recently) and they were fixed the same day. How long can a virus infect a Windows installation before it's fixed? More than one day, that's for sure.

The only reason I installed Windows in the first place was to play games. After The Witcher 2, CIV V, X-COM, and Borderlands coming to Steam for Linux, what the fred do I need Windows for? Now I just have extra storage!

---

### Post by JayKay3OOO on 2014-11-08
Joli Cloud is what you were thinking of. Based on ubuntu it loaded a web interface with apps, but you could install a few local apps like libreoffice and get access to your hard disk and local files in one of the cleanest UIs I ever used. You can still get the app interface in chrome as an extension and with the amount of web apps for office, etc you can pretty much just load ubuntu and never use any of the local storage or applications.

[http://www.jolicloud.com/our-story](http://www.jolicloud.com/our-story)

R.I.P.

---

### Post by irv on 2014-11-08
Joli OS is no longer available. Even the links on Distro watch are no longer good.

---

### Post by user1397 on 2014-11-08
I second the long update times on windows 8/8.1.  I couldn't understand why they took so long, and just like you, sometimes the updates would fail and I've have to do them all over again.  Took me several hours, not sure how many exactly but it was way too long.  Thank god ubuntu doesn't have that problem :)

---

### Post by irv on 2014-11-17
Okay, it's been a week since I went into Win8. So this morning I had a little time and thought I would check to see if I had any updates so I rebooted and went into Windows. I went to check for updates and found a bunch of them. I selected the install button but it said there was an error because it was doing updates already. I waited until it was done and it force me to do a reboot. When I checked again all the updates were still there so I downloaded and install them. The computer reboot again and when I checked it had two more updates. Well after almost an hour (Short of 3 minutes) and 4 reboots I got them all installed.
I check my Linux server once a week for updates and it takes me about 4 or 5 minutes to download and install them. And the only time I need to do a reboot is if the kernel is updated, and that is not that often.

---

### Post by /ADM on 2014-11-18
The 'techs' refused to work on it until it was reset to default?!  I would have gone somewhere else.

---

### Post by kurt18947 on 2014-11-18
I'm not familiar with Windows 8 and UEFI.  How does restoring images work in that case? Copy or image the boot partition?  I have a Win 7 image that is pretty quick and easy to restore on an old-timey MSDOS partitioned machine.

---

### Post by irv on 2014-11-18
/ADM, I sent it back to the manufacture (Asus), and was trying to get it fixed under warranty but it turns out it was 3 months over a year and I got stuck with the bill anyway. (The motherboard failed after 15 months). All my other laptops have lasted 5+ years. I have a couple of real old one still running.

The problem with finding just the right hardware you want (the spec and price) you end up with a Windows computer. I don't like and don't want to use it, but I guess I keep it because I figure I paid for it. The only way around This is buy a Linux machine or build your own. I have done that a few times.

I think when I go to 15.04 next April I am going to wipe everything (get rid of Windows) and run only Linux. Before windows 8 came out I was Windows free for about 3 years. The only three OS' I had in the house was Chrome, Android and Ubuntu. I can live with that.

---

