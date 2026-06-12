---
title: "Don't do this at home (dist-upgrade...)"
date: 2010-10-29
forum: Testimonials &amp; Experiences
---

### Post by loldrup on 2010-10-29
I just tried to upgrade my 10.04 to 10.10

Halfway through the process the upgrade application froze.

I waited a couple of hours, then killed it and restarted. Now my computer is completely unable to boot. I just get a black screen. Also, I can't reinstall due to [this error]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1592355") and [this error]("https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779").

Mark Shuttleworth, I love you, but please stop lying to me. Dont pretend that upgrade works. If you hadn't, then I wouldn't have done it, and my computer would be saved. I trusted you, now I certainly dont.

Save the souls of naive, trusting people - please remove the dist-upgrade 'feature'.

---

### Post by stormchaser2063 on 2010-10-29
i wonder what happened, the upgrade feature worked fine for me, thankfully. hopefully you can get it fixed without too many issues.

---

### Post by psusi on 2010-10-29
Sucks for you, but I'm afraid the world is a little bigger than you and your computer.  You are wrong to assume that because you had a problem, everyone else will.  The fact is that it works just fine for pretty much everyone else.

---

### Post by CharlesA on 2010-10-29
I was able to upgrade fine.

Are you looking for support, or just needed to vent?

EDIT: Before you do anything with a working system, be it upgrades or installing new stuff, always have a good backup so that if something goes wrong, you don't lose yer data.

---

### Post by loldrup on 2010-10-29
> **psusi said:**
> Sucks for you, but I'm afraid the world is a little bigger than you and your computer. 

Guess you are right

> **psusi said:**
> You are wrong to assume that because you had a problem, everyone else will.  The fact is that it works just fine for pretty much everyone else.

Well, even if I'm the only one who have ever had an upgrade fail epically, it would still show that upgrades are not risk free. You actually risk ruining your computer big time. How well is this communicated? Is everyone upgrading aware of this risk?

How many people encounters failure is another question, but from talking to people at my school, I (now) know that ubuntus dist-upgrade has a bad reputation. So, Im not alone, and the risk is not diminuitively small and the consequences, when it fails, definitely isnt so either.

---

### Post by loldrup on 2010-10-29
> **CharlesA said:**
> I was able to upgrade fine.

Are you looking for support, or just needed to vent?

Just venting :)

> **CharlesA said:**
> EDIT: Before you do anything with a working system, be it upgrades or installing new stuff, always have a good backup so that if something goes wrong, you don't lose yer data.

Dropbox is my friend :)
But I still miss my computer :(

---

### Post by CharlesA on 2010-10-29
I've run into stuff failing for no good reason before and usually just roll back to my backup and try it again.

Of course, that being said - I make drive images of my machines before doing anything major, so it's easy to roll back if something doesn't work.

---

### Post by loldrup on 2010-10-29
> **CharlesA said:**
> 
Of course, that being said - I make drive images of my machines before doing anything major, so it's easy to roll back if something doesn't work.

How do you do make drive images? (and how do you roll them back?)

---

### Post by CharlesA on 2010-10-29
I use [Clonezilla]("http://clonezilla.org/") to do drive images, and just restore them if I need to.

---

### Post by ventrical on 2010-10-29
Hi loldrup,

 Yes , I have had this happen to me during an upgrade from 8.4 to 10.04 Lucid on a Sony Vaio netbook. Of course i was experimenting - just to see what would happen and I got the blackscreen on reboot.

  So I just hooked up that HD to my USB to ATA converter and  installed 10.4 on  the HDD through my Acer Aspire. I was sort of aggravated at first but then I had to realize that I'm working with a netbook that was ready for the recycle bin .. so I'm not complaining.

  There is always a chance that if a person is upgrading from one distro to another (online) that it could be that the  existing distro could be a hacked image from another site and that the updater is doing a bogus update.or it could also just be hardware incompatibility.

  I hope it gets worked out for ya.

---

### Post by Zzl1xndd on 2010-10-29
> **loldrup said:**
> 
Well, even if I'm the only one who have ever had an upgrade fail epically, it would still show that upgrades are not risk free. You actually risk ruining your computer big time. How well is this communicated? Is everyone upgrading aware of this risk?

How many people encounters failure is another question, but from talking to people at my school, I (now) know that ubuntus dist-upgrade has a bad reputation. So, Im not alone, and the risk is not diminuitively small and the consequences, when it fails, definitely isnt so either.

Although I understand where your coming from, this should be common knowledge by now. No matter what OS Windows, Mac, Linux, etc. Upgrades can go wrong. Personally I always advocate making a back up (or having a separate home partition) and doing a clean install.

---

### Post by cubsfan53 on 2010-10-29
I had this same problem with the upgrade from 10.04 to 10.10.

Upgrade started ok, but was getting GTk errors, but the upgrade continued. First thing I said was "OK, don't panic." Did a hard shutdown, and restarted choosing safe mode and command line. thought to myself, "Let's try this -- sudo apt-get upgrade && sudo apt-get install."

Tried it and what do you know the upgrade continued and now I have a fully functional 10.10.

I am no expert, just a reader of the forum's ABT & General Help.

Rick


the best thing I learned from the forums is -- Don't panic, there are answers to problems and a great community to help.

---

### Post by Paul820 on 2010-10-29
> **CharlesA said:**
> I use [Clonezilla]("http://clonezilla.org/") to do drive images, and just restore them if I need to.

That looks good, thanks for pointing it out.

---

### Post by Omnomnom on 2010-10-29
In the tutorial section, there's a way to back up your whole linux install using TAR, then you can just put it onto an external HDD. Also, sucks for you mate.

---

### Post by blur xc on 2010-10-29
I've done a handful of successful upgrades, and had one epic failure.  In my experience, if you have ordinary well supported hardware, upgrades are a safe bet.  If you've got odd-ball crap that takes forever to get working right after a clean install- steer away from upgrades.  But that's just my personal, very limited, experience.

But considering the wide variety of computers out there, I can't imagine it would ever be possible to come up with an upgrade scheme that worked 100% of the time w/o problems.

Also, in my experience (for whatever weird reason) upgrades take WAY longer than a clean install.  Why does it take hours when downloading the iso, buring a disk, and doing a clean install only takes 30 - 40 mins?

BM

---

### Post by TBABill on 2010-10-29
I think what a lot of people fail to realize is that the upgrade process is not simply installing a few files already on your hard drive. Because you download so much from the Internet to upgrade, a failure anywhere between a server and the user's computer (the net itself) can cause a corruption or multiple corruptions in those files being downloaded. So when the upgrade runs it cannot always handle the errors. 

It is much safer to have a known good .iso to work from and put in a Live CD or DVD. It's not always possible for people to do so, but trusting the upgrade process is inherently risky. How often do people use Skype or another home telephone VOIP service and encounter packet loss? And then if the machine itself glitches during the process another entire set of errors is possible.

Lots to go wrong, but Ubuntu itself may or may not be the cause of each individual failure. I'm certainly not saying it is a perfect process, but many more people upgrade successfully than those who do not or the forums would be overwhelmed with similar posts.

---

### Post by Omnomnom on 2010-10-29
And remember, you should never, EVER, do anything that could be potentially system-threatening without backing up first! It's common sense!!

---

### Post by johntaylor1887 on 2010-10-29
In most computer "circles" upgrading via the net or by upgrade disc, is usually not the recommended way of running the latest and greatest. It goes for all platforms. Clean install will always be the best choice in *most* cases.

---

### Post by johntaylor1887 on 2010-10-29
> **Omnomnom said:**
> And remember, you should never, EVER, do anything that could be potentially system-threatening without backing up first! It's common sense!!

That's why I just install the latest version of any distro on a separate hard drive, test it, *then* decide. Easy.

---

### Post by arunb on 2010-10-30
even windows upgrades may go wrong sometimes, I suppose its a risk you accept while upgrading.

To the OP.
Why did you upgrade to 10.10, 10.04 is more stable.

---

### Post by cariboo on 2010-10-30
Pre-Karmic, the upgrade process was known to have problems. Since Karmic, with the update-manager automagically disabling ppas, many of the problems people upgrading ran into are no longer valid.

You really only need to do three things before upgrading:

[list=1]
[*] Backup your important files
[*] Make sure you are fully up-to-date
[*] find the fastest mirror
[/list]

---

### Post by Swagman on 2010-10-30
I bit the bullet and did an upgrade 10:04 -> 10:10  (32 bit) and it went fine. Only glitch is Evolution layout b0rked.

For backups I [**Ping**](http://ping.windowsdream.com) the Penguin

---

### Post by loldrup on 2010-11-02
I managed to get ubuntu 10.04 back on my computer. The aid was to create the usb boot stick from a ubuntu 10.04 computer instead of my companion ubuntu 10.10 computer.

Quote from:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Common%20Desktop%20Applications](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Common%20Desktop%20Applications)

"It is not possible to create Ubuntu 10.04 USB disks from the Startup Disk Creator in Ubuntu 10.10 due to a backwards incompatibility in the syslinux program."

---

### Post by Tamlynmac on 2010-11-02
Since becoming a member of the forums. I can't count how many times it's  been stated that one should never attempt an online upgrade. Good , bad  or otherwise. When upgrading something as important as an OS why risk doing it on line? Simply download the file and assure said file is not  corrupted, then just create a startup disk, stick, etc.

I did two online upgrades on three of our systems and both upgrades went  without issue (8.04 & 8.10). However, I did imaged my drives prior to  said upgrade. Even when imaging one's system, there's an associated risk  of potential failure (data loss, etc.). Since that time I've never  upgraded without testing. One quick test is to simply run the bootable  stick/disc to assure audio, video, wifi, etc. Unless of course specific  drivers or applications are required.

I use a spare usb hdd to test all 5 of our systems prior to upgrade. I  assure that said upgrade is compatible with all systems and test  anything that may require a specific driver/application. I use a  standardized testing procedure and to date have experienced zero  failures after testing. If a system fails testing, I endeavor to  identify the failure and attempt to find a solution. If no solution is  available the system remains undisturbed and completely functional. I  simply unplug the usb hdd and boot back to the primary hdd.

Logic might suggest when upgrading (with the number of new releases),  that a testing procedure and a spare HDD (or other device) be  implemented to assure compatibility and functionality. It minimizes  the potential for failure and doesn't require a significant investment  in time or costs. Since 8.10 I've never installed an upgrade prior to testing and  all our systems have remained extremely stable/reliable.

If a new release fails testing and a solution isn't available, I wait  for a solution or the next release. A wise person once shared with me  their theory of NAA: "Never Assume Anything". More failures have  resulted from assumption, than almost any other cause. At least that was  their theory and to date - I've found it hard to argue. :smile:

---

### Post by uRock on 2010-11-02
I always run clean installs. 

One of the main reasons is the fact that there is no easy to use software for defragmenting EXT4, therefore cleaning up the files systems and guaranteeing a fully functional install in less than an hour.

Upgrading has bricked one of my machines in the past and has crashed to a point of forcing a clean install on all other attempts.

To the OP, thanks for sharing your experience and hopefully you have less problems in the future.

---

### Post by JaradT on 2010-11-03
> **loldrup said:**
> 
Well, even if I'm the only one who have ever had an upgrade fail epically, it would still show that upgrades are not risk free.
*Every* upgrade is not risk free. It goes for every OS.
Sorry to hear about the risk, but make sure you make a backup of everything you want.

---

