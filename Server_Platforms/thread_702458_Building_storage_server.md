---
title: "Building storage server"
date: 2008-02-20
forum: Server Platforms
---

### Post by Shaoline on 2008-02-20
I am building a storage server, and would like some thoughts about the hardware things that I've picked out..

Thoughts on the selection of distribution is also welcome.
The server is going to handle both Mac's and PC's in a office environment, as pure storage.

Case: - [**Link**]("http://www.antec.com/ec/productDetails.php?ProdID=00480")
HDD(raid): 4x Seagate 500Gb, 32Mb cache, Sata2
HDD(system): 1x Seagate 160Gb, 8Mb cache, Sata2
Raidcontroller: HP RocketRaid 2300 - [**Link**]("http://www.highpoint-tech.com/USA/rr2300.htm#top")
RAM: 2x1Gb Corsair PC-6400 - [**Link (PDF)**]("http://www.corsair.com/products/go.aspx?pn=TWIN2XP2048-6400C4")
M/B:Asus M2N-VM DVI mATX - [**Link**]("http://www.asus.com/products.aspx?l1=3&l2=101&l3=567&l4=0&model=1841&modelmenu=1")
CPU: AMD Athlon X2 Dual Core 5000+ 2x512Kb, Boxed
.. plus 1x Lian-Li 3x5.25" > 4x3.5" "converter with 120mm fan"

Guess that's relevant information.
Raid is most likely gonna be Raid 5, for security.

Any suggestions are most welcome..

---

### Post by faulkes on 2008-02-20
> **Shaoline said:**
> I am building a storage server, and would like some thoughts about the hardware things that I've picked out..

Thoughts on the selection of distribution is also welcome.
The server is going to handle both Mac's and PC's in a office environment, as pure storage.

Any suggestions are most welcome..

The only thing I can think of would be to perhaps add a secondary GB NIC for either l2 or l3 redundancy (depending how you plan to distribute the filesystems).

While I havent done something like that, I imagine it would be worth it to setup a heartbeat between the two so if one goes down, the other resumes operation.

Faulkes

---

### Post by sp0nge on 2008-02-20
> **faulkes said:**
> While I havent done something like that, I imagine it would be worth it to setup a heartbeat between the two so if one goes down, the other resumes operation.

Faulkes

Thats a very interesting suggestion. Shaoline, I hope you try this out. Please post any difficulties or issues encountered if you do.

---

### Post by Shaoline on 2008-02-20
Any suggestion on what filesystem to use? My personal guess would be to go with ext3, as it's designed for safety(?). And frankly, the only thing I've used so far..
The forced "fsck" once in 25isch boots is the only "negative" side I've come to think of, seeing the raid disc will be on about 1500Gb (seen timewise, not safetywise!).

From what I know, Samba will handle both of the protocols, from the Mac's and the PC's(?). (There is 1x OS X Mac, and 2x Mac OS 9(?), and 1x PC on the network)

EDIT:
Ah yes, the distro I'm aiming to use is either Ubuntu server edition (Hardy Heron?) with slim GUI, or if I'm able to set it up using CLI; Debian (that's allowed to say, right?) ;)

---

### Post by cdenley on 2008-02-20
> The forced "fsck" once in 25isch boots is the only "negative" side I've come to think of
Those settings can be configured.
```
man tune2fs
```

---

### Post by rickyjones on 2008-02-20
Nice specs!

I would just use ext3 personally to make it easier on yourself. Have the RAID array mount in a single folder and then use SAMBA and/or NFS to share this folder. That is what I would probably do.

-Richard

---

### Post by snek on 2008-02-20
I recently set up a similar system, it was my first real linux project, except with an Areca 8port sata controller, 3x500gb WD RE drives, and XFS as filesystem since it is primarly going to be used for large video files. So far, I am thrilled with the performance, it's pumping over 600Mbit over a cheap gbit switch. It shares to 5 different XP machines, and feels very fast compared to the servers we have at work. Gbit is definitely the way to go :)

That server gets backed up to someone's house over a 200KB/s upstream connection each night. At his house I used a very simple mobo, 3x500gb WD RE drives again, but software raid. Even this machine feels very fast.

Not bad for a nub straight off the Windows bandwagon :D

One thing you might want to look at is the make & model of the Gbit card. To be honest, I can't remember the make of the onboard cards on that pc (it's not mine) but it was picked up by Ubuntu without a hitch and works at great speeds. Although you would expect that from a SuperMicro board ;) 

However, at home it's a whole different story.. This mobo has a Marvell Yukon chipset and needs some hefty work to get working properly (read: real gbit speeds) which I don't have the patience for (kernel recompiling etc..)

So be careful of the hardware components if you want to crank every bit of performance out of it. I'm a bit iffy about the nvidia chipset tbh, as vga controller it is perfect, but the rest of the chipset might be a bit tricky in Linux.. Although I don't have any nvidia based mobo's myself, so take my advice with a grain of salt. The software raid at the guy's house is primarly the fault of the nvidia chipset in his homeserver... I tried both Debian & Ubuntu on both had problems with the onboard raid controller.. But you don't have that problem of course.

---

### Post by craigp84 on 2008-02-20
Looks like you've spent a bit of time getting together the components, and i'm sure you've made wise choices.

However, and this is the big one, there's no provision for backup device? This is the number 1 mistake people make when spec'ing a server on these forums.

Of course you might already have some backup solution in place (say a remote tape library, or a big blob of disks on some other server); although if you don't, it's gotta be priority 1 if the data to be stored on this server is not available in another location, or cannot be easily recreated in a financially viable way.

Tapes are dead as a dodo, and they're expensive for what you get. Hard disks are cheap, fast to recover from, and can be kept online (if mounted ro - to avoid the old "rm -rf /" gotcha!).

A simple solution would be to drop the raid idea, go for single disks, and setup rsnapshot or similar to duplicate to the other disks (that would be the raid mirrors).

Hope it helps,

-c

---

### Post by Shaoline on 2008-02-20
> **craigp84 said:**
> [...]

Tapes are dead as a dodo, and they're expensive for what you get. Hard disks are cheap, fast to recover from, and can be kept online (if mounted ro - to avoid the old "rm -rf /" gotcha!).

A simple solution would be to drop the raid idea, go for single disks, and setup rsnapshot or similar to duplicate to the other disks (that would be the raid mirrors).


Hm, that could work. I could use 2x Raid 0 setups aswell.. 1000Gb should be enough too. Then have one raid act as primary storage, and the other raid as a kind of backup raid. Using say.. daily or weekly backups with rsnapshot.
Comments on that?

---

### Post by snek on 2008-02-21
Hmm never thought of that, it could work very well. Keep in mind thought that you will not be able to expand a raid1 setup, whereas you can expand a raid5 setup. Also raid1 will be slower reading than raid5.

So I guess it really depends on what you are going to use it for.. But 2xraid1 sounds to me like paranoia unless you are storing bank transactions on it or something else involving silly amounts of money ;)

---

### Post by FakeOutdoorsman on 2008-02-21
> **Shaoline said:**
> Thoughts on the selection of distribution is also welcome.

It would be nice if you didn't have to deal with dist-upgrades and use a rolling-release like with Debian Lenny aka *testing*.  Despite the name, *testing* is usually quite stable, but Debian Etch is rock solid (but not rolling). Get the netinstall disc of one of those and build up from the bottom and install only what you need.  You'll end up with a quick and lean install.  Of course Ubuntu LTS would be great too, and I would also recommend just a command-line install plus whatever you need.  CentOS is considered by some to be a stable distro, but it is a bloated pig and even the base install is excessive in size.  Debian and Ubuntu seem to give much finer control over the installation.

Samba is very slow for some, including me.  Make sure to tweak the Samba configs if you use it.
[slow gigabit transfers via samba]("http://ubuntuforums.org/showthread.php?t=531505")

Here's an interesting article that explains some pros and cons of rsync, tar, rsnapshot, rdiff-backup, etc:
[Backing up Linux and other Unix(-like) systems]("http://www.halfgaar.net/backing-up-unix")

---

### Post by Shaoline on 2008-02-21
> **FakeOutdoorsman said:**
> It would be nice if you didn't have to deal with dist-upgrades and use a rolling-release like with Debian Lenny aka *testing*.  Despite the name, *testing* is usually quite stable, but Debian Etch is rock solid (but not rolling). Get the netinstall disc of one of those and build up from the bottom and install only what you need.  You'll end up with a quick and lean install.  Of course Ubuntu LTS would be great too, and I would also recommend just a command-line install plus whatever you need.  CentOS is considered by some to be a stable distro, but it is a bloated pig and even the base install is excessive in size.  Debian and Ubuntu seem to give much finer control over the installation.

Samba is very slow for some, including me.  Make sure to tweak the Samba configs if you use it.
[slow gigabit transfers via samba]("http://ubuntuforums.org/showthread.php?t=531505")

Here's an interesting article that explains some pros and cons of rsync, tar, rsnapshot, rdiff-backup, etc:
[Backing up Linux and other Unix(-like) systems]("http://www.halfgaar.net/backing-up-unix")

Nice info, thanks! Will take your words into consideration.. I would really like to use Debian, since I use it here at home for my router/firewall computer. It's my limited CLI skills that causes me to, maybe, use a GUI, though slim.

Is there any negative effect using cron to update the server? (would get me off some "easy" work)

---

### Post by dirk_diggler on 2008-02-21
> **Shaoline said:**
> Any suggestion on what filesystem to use? My personal guess would be to go with ext3, as it's designed for safety(?). And frankly, the only thing I've used so far..


Interesting...  

I, too, am looking into building a file server, but mostly for music and video files.  I am currently backing up all of my DVDs onto my computer (for personal use, btw) so that I can access it through the net on tv, laptop, desktop, etc. The only problem I foresee is the size limitation by ext3 (if it is at all a problem).  Because I am saving the files as uncompressed single files (rather than broken down into 1GB files), they can get up to 7-8 GB large.  Will ext2 work for this, or will ext3 also handle this?  Currently, I am stuck with saving everything on an NTFS partition... which is fine (for now).

Any suggestions?

Thanks

---

### Post by FakeOutdoorsman on 2008-02-21
> **Shaoline said:**
> Is there any negative effect using cron to update the server? (would get me off some "easy" work)

Rarely a package can slip through that might cause problems for your server, but it does happen.  If stability and uptime are important then you may want to only automatically update the security updates and do everything else manually.  Another option is to automatically download all updates at night or a low bandwidth period and then manually perform an upgrade.

There are three packages in the Ubuntu repository that you should take a look at: unattended-upgrades, apticron, and cron-apt.  Take a look at their descriptions in Synaptic.

[Automatically update your Ubuntu system with cron-apt]("http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm")

As for your limited CLI skills, you'll learn so much by starting with a command-line install.  If you don't like it just install xorg or do a normal install.
[URL="https://help.ubuntu.com/community/Installation/LowMemorySystems"]
Installation / Low Memory Systems[/URL] at Ubuntu Wiki

---

### Post by igknighted on 2008-02-21
> **FakeOutdoorsman said:**
> It would be nice if you didn't have to deal with dist-upgrades and use a rolling-release like with Debian Lenny aka *testing*.  Despite the name, *testing* is usually quite stable, but Debian Etch is rock solid (but not rolling). Get the netinstall disc of one of those and build up from the bottom and install only what you need.  You'll end up with a quick and lean install.  Of course Ubuntu LTS would be great too, and I would also recommend just a command-line install plus whatever you need.  CentOS is considered by some to be a stable distro, but it is a bloated pig and even the base install is excessive in size.  Debian and Ubuntu seem to give much finer control over the installation.

Samba is very slow for some, including me.  Make sure to tweak the Samba configs if you use it.
[slow gigabit transfers via samba]("http://ubuntuforums.org/showthread.php?t=531505")

Here's an interesting article that explains some pros and cons of rsync, tar, rsnapshot, rdiff-backup, etc:
[Backing up Linux and other Unix(-like) systems]("http://www.halfgaar.net/backing-up-unix")

I must strongly disagree with your CentOS analysis.  CentOS defaults to having lots of stuff installed, yes.  But unchecking a few boxes at install tweaks it to only having what you want.  Once installed, the Red Hat service features are a godsend when admin-ing servers.  And of course it is just as stable as Debian, with all the benefits of being 100% compatible with applications written for Red Hat.

---

### Post by FakeOutdoorsman on 2008-02-21
> **igknighted said:**
> I must strongly disagree with your CentOS analysis.  CentOS defaults to having lots of stuff installed, yes.  But unchecking a few boxes at install tweaks it to only having what you want.  Once installed, the Red Hat service features are a godsend when admin-ing servers.  And of course it is just as stable as Debian, with all the benefits of being 100% compatible with applications written for Red Hat.

I use CentOS too and I never said it wasn't stable.  Compared to a netinstall or minimum install of Debian though, CentOS can be considered big, even when unchecking everything.  This is all my opinion, of course, and It all depends on what you consider a heavy install.

---

### Post by Shaoline on 2008-02-22
> **FakeOutdoorsman said:**
> Rarely a package can slip through that might cause problems for your server, but it does happen.  If stability and uptime are important then you may want to only automatically update the security updates and do everything else manually.  Another option is to automatically download all updates at night or a low bandwidth period and then manually perform an upgrade.

There are three packages in the Ubuntu repository that you should take a look at: unattended-upgrades, apticron, and cron-apt.  Take a look at their descriptions in Synaptic.

[Automatically update your Ubuntu system with cron-apt]("http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm")

As for your limited CLI skills, you'll learn so much by starting with a command-line install.  If you don't like it just install xorg or do a normal install.
[URL="https://help.ubuntu.com/community/Installation/LowMemorySystems"]
Installation / Low Memory Systems[/URL] at Ubuntu Wiki

Those are nice links, will probably go with the security updates you mentioned, tthen from time to time, do a dist-upgrade, either on site or from my computer at home.
I will probably choose the Debian stable version, as there won't be any need for fancy new stuff of any kind. It just needs to be reliable and slim (what a waste of a grand 160 Gb disc).. :)
Think I'll do a search later today after work, and post some of the links I likely will be needing when setting it up (for others to learn from aswell).

---

### Post by hkgonra on 2008-02-22
I like that raid card but if you plan to use debian or ubuntu you ARE going to have issues with that card if you even can get it to work at all.

---

### Post by Shaoline on 2008-02-22
> **hkgonra said:**
> I like that raid card but if you plan to use debian or ubuntu you ARE going to have issues with that card if you even can get it to work at all.

Hm, that sounds.. bad?
I've made some quick research on the matter, and it seems most people use the 1720 model. Mine is 2300..
I don't know if that'll make a huge difference, if any, but I won't settle with "not working" since there are drivers for linux on their page. :)

EDIT:
Drivers page:
[http://www.highpoint-tech.com/USA/bios_rr2300.htm](http://www.highpoint-tech.com/USA/bios_rr2300.htm)

---

### Post by hkgonra on 2008-02-22
Do a search here for rocketraid and look at some of the results. Not real promising. 
I have 2 1820's and a 2220 and have had no luck with any version of linux, tinkered for days and got it working on suse once but the next time I ran updates it broke it.

---

### Post by Shaoline on 2008-02-28
> **FakeOutdoorsman said:**
> It would be nice if you didn't have to deal with dist-upgrades and use a rolling-release like with Debian Lenny aka *testing*.  Despite the name, *testing* is usually quite stable, but Debian Etch is rock solid (but not rolling). Get the netinstall disc of one of those and build up from the bottom and install only what you need.  You'll end up with a quick and lean install.  Of course Ubuntu LTS would be great too, and I would also recommend just a command-line install plus whatever you need.

As far as I understand, these drivers I've installed now for the controller card; they will break as soon as I change my kernel version, correct?

I've made an install now, and grabbed a few extra packages (Alien etc) to get my drivers into .deb files. Then uploaded them to my domain. Later tonight I'm gonna reinstall and use the deb's.. that way I'll have a real smooth installation, and then I'll toss in the needed users and smbusers.
(Not really that experienced as to delete all the packages it grabbed along the mentioned packages..)

Should work, right?

EDIT:
Oh ye, and I'll use the testing version of Debian tonight.

---

### Post by FakeOutdoorsman on 2008-02-28
> **Shaoline said:**
> As far as I understand, these drivers I've installed now for the controller card; they will break as soon as I change my kernel version, correct?

I think so, but I have little experience with kernel patching.

> **Shaoline said:**
> I've made an install now, and grabbed a few extra packages (Alien etc) to get my drivers into .deb files. Then uploaded them to my domain. Later tonight I'm gonna reinstall and use the deb's.. that way I'll have a real smooth installation, and then I'll toss in the needed users and smbusers.
(Not really that experienced as to delete all the packages it grabbed along the mentioned packages..)

Should work, right?

HighPoint has the "vanilla" source code available at the bottom of the [driver page]("http://www.highpoint-tech.com/USA/bios_rr2300.htm"). You can use the plain source code and [checkinstall]("https://help.ubuntu.com/community/CheckInstall") to make a .deb for you instead of using Alien.  With checkinstall you enter "sudo checkinstall" instead of "sudo make install".

---

### Post by Shaoline on 2008-02-28
> **FakeOutdoorsman said:**
> I think so, but I have little experience with kernel patching.

Hm, don't know if I even meant patching? :confused:
I just have a vague memory of getting different kernels to choose from on my firewall/router, in the GRUB menu. But maybe I'm wrong..

> **FakeOutdoorsman said:**
> HighPoint has the "vanilla" source code available at the bottom of the [driver page]("http://www.highpoint-tech.com/USA/bios_rr2300.htm"). You can use the plain source code and [checkinstall]("https://help.ubuntu.com/community/CheckInstall") to make a .deb for you instead of using Alien.  With checkinstall you enter "sudo checkinstall" instead of "sudo make install".

Hm, well, I didn't know that, so thanks for new info! :)
Though, I already got the .deb's for the driver and the "WebGUI". So problem solved already, for my part.

I'm just gonna burn that netinst iso now, and be on my way with the new installation..

---

### Post by Shaoline on 2008-02-28
I've run into a bit of trouble on this late hour..

All this stuff about users etc gives me headache.(!)
And at this moment, it makes no sense to me.. :)

I've made it as far as I've been able to edit and create folders and files etc on the server from my computer.. but when I do a 

```
ls -l
```

it says the owner is "nobody" from "nogroup".. (and I'm pretty sure I've set it up as to restrict login to users with a local account, since I cant reach the server if I remove the users again).
Shouldn't the ownership be, in this case, "thomas", since thats the username on my computer and the user I've added on the server? :confused:

Could someone maybe point me in a direction where I can read up on this issue?

I also have a strange issue going on first time I open a file on the server, over the network, in this case a text file, it says internal error, and shows a blank document, I re-open it and it shows my little jibberish text. This is a minor problem at the moment, but I'm thinking it may be linked with all this ownership thingy.. time will tell.

---

