---
title: "Upgrade Ubuntu 9.10 (Karmic) -&gt; 10.04 LTS (Lucid): Never Again!"
date: 2012-03-12
forum: Testimonials &amp; Experiences
---

### Post by JSeymour on 2012-03-12
I'm trying for "cautionary tale," but it may come across as a bit of a rant.  My apologies, if so.  I'm just a little >< annoyed.

Against my better judgment, because "major" upgrades have *never* worked for me or anybody I know, yesterday attempted to upgrade my 9.10 combined desktop/server to 10.04 LTS.

Had a nightly rsync-based backup at hand, but, to make sure, cloned /dev/sda1 to /dev/sda2.  (They're identical partitioning.)  It's a good thing, too.  (Tho that didn't save me 100%.)  Also made sure my laptop could get on the 'net w/o the home network's server (DNS, DHCP, all of it's on the machine I was trying to upgrade) in case Something Went Wrong.

Ran do-release-upgrade.  After all was said and done, ended up with GRUB telling me "error: you need to load the kernel first" and something about not being able to find something.  (Sorry, don't have my notes with me atm.  Forgot to bring them with me to work.)  Handy.

Research. Research some more.  And some more.  Find out GRUB problems are pretty common.  Well isn't that just wonderful?  Find a YannUbuntu boot repair disk.  Download, burn and run.  (Good thing I made sure the laptop would be functional, eh?)

Ah, got a GRUB menu now :)

What's this?  It says it cannot find the new kernel for which the boot repair made an entry?  Ok, try boot to the one version of the old kernel the upgrade left.  That boots, but ... the login takes *forever* to complete (as in multiples of minutes) and nearly all of my services (DNS, Dovecot, NTP, you-name-it) are either not running at all or are non compos mentis.

It's late.  I'm tired.  I'm exceedingly annoyed.  I have to work tomorrow.  Never. Fracking. Mind!

Reboot into the 10.04 "Live" boot on the 10.04 install CD, start the restore of the backup (previously working) image back into the normal root partition (dd if=/dev/sda2 of=/dev/sda1 bs=32M) and go to bed.

Next morning, get up, get ready for work.  The "dd" is done.  Open a terminal, find the MBR backup, and restore it to /dev/sda.  Reboot.  What's this?  Can't find some-or-another grub_blurfl_char_yadda thing?

Back to the boot repair disk.  It reports success.  Reboot.

Ahhh... this looks good :)

Alas, it was not to be.  After the old 9.10 spash initially comes up, some ugly two-tone yellow background replaces it, a black & white login selector appears and...

Both keyboard and mouse are **dead**?!?!

What. The. Hell???  Did the brain-dead upgrade mess with something in the unmounted partition?  Maybe it messed with stuff in /var (separate filesystem on this machine)?  Who knows?

I managed to get the thing running as a server, but it's trashed as a desktop.  I guess tonight I'll just install 10.04 LTS from scratch, re-install everything else I need from scratch and re-configure all of the services, etc. All. Over. Again.

Last time I'll ever let anybody talk me into trying to upgrade an Ubuntu box across major revisions ever again, that's for darn sure.

Jim

---

### Post by nothingspecial on 2012-03-12
*Thread moved to **Ubuntu Testimonials & Experiences**.*

---

### Post by mastablasta on 2012-03-12
what major revisions?
 
9.10 to 10.04 should be smooth ride since 10.04 is basically a more stable 9.10.
 
why grub repair disk? you oculd have used live 10.04 Cd to update/upgrade grub if necessary.

---

### Post by Frogs Hair on 2012-03-12
9.10 to 10.04 was the only upgrade I attempted and have never tried again. I only work with clean installations. 

I think the fact that 9.10 hasn't been supported for almost a year may have contributed to your problems .

---

### Post by Version Dependency on 2012-03-12
Upgrading from 9.10?  That version reached end of life awhile back.  If you are wanting to use an LTS to avoid the hassle of upgrading for awhile, the new 12.04 LTS comes out next month and will be supported for five years.

---

### Post by JSeymour on 2012-03-12
> **mastablasta said:**
> 9.10 to 10.04 should be smooth ride since 10.04 is basically a more stable 9.10.
That was the impression I had, which was why I tried the upgrade path.
 
> **mastablasta said:**
> why grub repair disk? you oculd have used live 10.04 Cd to update/upgrade grub if necessary.
Tried that.  Was not successful.  Doesn't matter: It probably would've left me where I got via the boot repair disk, anyway.

> **Version Dependency said:**
> Upgrading from 9.10?  That version reached end of life awhile back.
And now you can see why I'm still on 9.10.

I do IT for a living.  At work, just w/in the last few months, I've upgraded a web/FTP server, a mail server, a (FBSD) firewall/VPN server, and several desktops/laptops--incl. my own.  The *last* thing I want to do when I get home is more of the same.  But I wasn't getting updates any more, so it had to be done.

> **Version Dependency said:**
> If you are wanting to use an LTS to avoid the hassle of upgrading for awhile, the new 12.04 LTS comes out next month and will be supported for five years.
Unfortunately that bollixed-up upgrade attempt forced my hand.  I can't wait.  I now have no desktop at home, and my little tablet can carry me only so far.

Besides... 12.04 follows 11.x, and 11.x has Gnome3, and  I haven't heard a **single** positive word about Gnome3 yet.  Not from anybody.  Plus some people have been experiencing trouble with pilot-xfer/JPilot on 11.x. Until I can afford to upgrade from my Palm platform (which may be never, with what they charge for data plans), I've got to keep that stuff working.

Thanks for the follow-ups, everybody.

Jim

---

### Post by mastablasta on 2012-03-14
well it seems from the post that upgrade wors really well, but only in more or less vanilla *buntu.
 
that is why i am a bit scared of it (i have 10.10 which will soon be EOL and i also need newer verison of progs to be compatible with winxp mashcine). i have a bunch of PPA installed though i have only printer driver via PPA. so i am really hoping it will be possible to do 10.10->11.04->11.10-12.04LTS. if LTS works ok i might even stick to it. previous one (10.04) was a P.I.T.A on this maschine.

---

### Post by Holdolin on 2012-03-14
I normally only do clean installs.  Tends to save a lot of headaches for me.  Just make sure your data is backed up (regular backups are a good idea) and then intall the newer Ubuntu.

---

### Post by mastablasta on 2012-03-15
does in your case clean install mean a disk reformat? or just install over previous version?
 
becuase if you have a lot of programmes to "reinstall" and libraries to hunt down... well let's say it can take well over the time you would install windows (instead of 20 minutes or so...). i used PPA to get newer versions of programmes. when i upgrade i would liek to have those programmes installed. 
 
however if i choose clean install (with disk reformat) i would have to reinstall them all over again. which might take a while...probably an afternoon at least if not more.

---

### Post by blindenvy on 2012-03-17
ughhh. I love that I found and started reading this post after I already started the same upgrade path. Hopefully mine goes smoothly.

---

### Post by Tamlynmac on 2012-03-17
> JSeymour
Last time I'll ever let anybody talk me into trying to upgrade an Ubuntu  box across major revisions ever again, that's for darn sure.

I'll go ahead and say what some may be thinking. The upgrade process can  fail (for multiple reasons). Should one  invest a little time in searching history in this section of the  forums, they would find that the upgrade process has been discussed here many  times before. If I recall correctly, often the consensus was to "not" use the upgrade process - advising a live install. IMHO It's not a topic that Ubuntu/Linux user  enjoy discussing, as it's been questioned for quite some time.

I've been Ubuntu only since 7.04 and after having a failed upgrade to  8.04, I never again used the upgrade process. That's not say, that  others haven't had success with it. I'm just the type of user that  prefers to error on the side of caution.

I recommend to all users that  prior to installing a new version they **"test"** said version. One nice thing about using the live install procedure, is the ability to  test a release prior to simply installing. Which could help assure  functionality and expectations. I keep a spare HDD to test all new  releases, on all our systems prior to replacing existing versions. Or, you could use a  separate partition for testing, etc.

I can't count how many times family, friends and associates that use  Ubuntu/Linux have come to me frustrated, because they either used the  upgrade process or installed the newest release without testing. Only to find, that the upgrade failed or the new version is unacceptable for their use. #-o

Just my $0.02

---

### Post by JSeymour on 2012-03-19
> **mastablasta said:**
> does in your case clean install mean a disk reformat? or just install over previous version?
I re-formatted and re-installed from scratch, keeping /var, /tmp, /usr/local and /home as-was (save for what was installed/created in /var, of course).
 
> **mastablasta said:**
> becuase if you have a lot of programmes to "reinstall" and libraries to hunt down... 
Indeed.  Particularly since the machine is a combined network server (DNS, DHCP, mail, web, NTP, DLNA, etc., etc.) *and* my desktop.  But it is what it is.

> **Tamlynmac said:**
> I recommend to all users that  prior to installing a new version they **"test"** said version.
I have said version running on two servers at work (mail and web) and on my laptop.  That, and its similarity with 9.10, which I've been running on the machine in question, gave me a high degree of comfort.

And, indeed, starting with a clean install: Everything's running swimmingly... so far.  As yet untested: Jpilot (on this machine--I tested it on my laptop) and Serviio.

It was worth the headache for the new Radeon driver alone.  Don't have to wire-frame on window moves anymore and no more herky-jerky videos :)

---

