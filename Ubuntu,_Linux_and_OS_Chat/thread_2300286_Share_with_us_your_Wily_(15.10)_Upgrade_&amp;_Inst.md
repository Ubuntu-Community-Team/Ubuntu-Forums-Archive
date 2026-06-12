---
title: "Share with us your Wily (15.10) Upgrade &amp; Installation Experiences"
date: 2015-10-24
forum: Ubuntu, Linux and OS Chat
---

### Post by cariboo on 2015-10-24
It's that time again, Wily (15.10) was released October 22, 2015 Please tell us about your experience upgrading, or doing a fresh install of Wily Werewolf.

Keep in mind that this thread is only for your experience, if you are having problems, please create a thread in the support forums.

Poll and thread for the previous release:

[http://ubuntuforums.org/showthread.php?t=2275836](http://ubuntuforums.org/showthread.php?t=2275836)

---

### Post by qamelian on 2015-10-24
I did a fresh install on my new laptop, but I had to edit GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub to get it to shutdown properly.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modeprobe.blacklist=dw_dmac,dw_dmac_core"
```

---

### Post by SantaFe on 2015-10-24
Upgraded Ubuntu-MATE 15.04 to 15.10.  No problems at all.  In fact I had totally forgotten to stop the Folding@Home client 7 I'm running on this laptop & started the upgrade.  Wasn't till it got to the re-boot phase when I remembered.  Not only did the upgrade go smooth, Folding@Home started folding right where it left off. ;)

---

### Post by gordintoronto on 2015-10-25
Xubuntu 15.04 to 15.10, download and install took about an hour on my six-year-old AMD "high performance computer." Seems to be working fine.

---

### Post by mikodo on 2015-10-26
Many of us remember the excitement around upcoming new Ubuntu releases and the whirl of activity here at the Ubuntu Forums, soon after.

I haven't gone looking for user experiences much. I peeked in Installation & Upgrades a few times and other typical help forums and, have seen very little.

I haven't left 14.04 so, I haven't an experience to share.

I do wonder what others might have experienced.

Do you feel like sharing?

---

### Post by night_sky2 on 2015-10-26
> **mikodo said:**
> I haven't left 14.04 so, I haven't an experience to share.
It's hard to leave the comfort and stability of a LTS release for a short term one that doesn't seem to have a lot of new features.

---

### Post by Kale_Freemon on 2015-10-27
Well, I upgraded from 15.04 to 15.10 using the update manager. Working well on my System76 Lemur with no problems. In fact, I really don't see any real changes. Feels like the same system to me. But, it works great.

---

### Post by mikodo on 2015-10-27
I'm glad the upgrade worked so well for you Kale.

Hey, there still may be some that might want to Upgrade to the Newest Release and see this.

Here are a couple of Wiki's on Release Upgrading. There is more information suggestions to better ones' chances of Upgrading Releases Successfully, that can be found online. Try a web-search term like this to start:  Ubuntu Release Upgrade.


I almost forgot this Current Sticky Thread in the Ubuntu Forums, Installation & Upgrades: [http://ubuntuforums.org/showthread.php?t=1946145](http://ubuntuforums.org/showthread.php?t=1946145)


Ubuntu Official Wiki on upgrading:  [http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)
 

 Ubuntu Community Help Wiki on upgrading: [URL="https://help.ubuntu.com/community/Upgrades"]https://help.ubuntu.com/community/Upgrades


[/URL]

---

### Post by kagashe on 2015-10-27
> **mikodo said:**
> Many of us remember the excitement around upcoming new Ubuntu releases and the whirl of activity here at the Ubuntu Forums, soon after.

I haven't gone looking for user experiences much. I peeked in Installation & Upgrades a few times and other typical help forums and, have seen very little.

I haven't left 14.04 so, I haven't an experience to share.

I do wonder what others might have experienced.

Do you feel like sharing?
Already shared [here]("http://ubuntuforums.org/showthread.php?t=2299395") and you might have read it but just in case you did not.

Kamalakar

---

### Post by mikodo on 2015-10-27
Thank you, Kamalakar.

Yes, I had read that detailed post of yours and I must add the sage advice about how to contend with newer hardware problems!

:)

---

### Post by Irihapeti on 2015-10-27
I did some install testing on my desktop PC. For the most part, it was uneventful.

The main thing I noticed is how much quicker installation is than it used to be. And, no, my current machine is no faster than my old one, though it does have more memory.

I'm still using 14.04 as my workhorse, however.

---

### Post by mikodo on 2015-10-27
Uneventful and quicker is good. Just like what Snappy-Core with Snaps will be soon!

---

### Post by grahammechanical on 2015-10-27
Ubuntu 14.04 has Unity 7 and so does 15.04 and 15.10 and so will 16.04. So, it is true that we do not see any real changes. And so I do not expect to see any real changes when 16.04 comes out. And try as I might I cannot come up with any ideas about needed visual changes to Unity. It does what it does and it does it well on my machine with a core2 duo CPU, 1GB RAM and a Nvidia GT220 with 1GB memory.

On another hard disk I have installed Ubuntu Personal. It is snappy Ubuntu core with Mir and Unity 8. It is still very much the phone OS but it is most definitely visually different. It has the top panel with indicators and the launcher on the left but workplace switching is different. Move the mouse to the right screen edge and all the open apps vertically cascade and we can select which app to use. It is very slick at doing this.

Oh, yes, if Ubuntu Personal is pre-installed on laptops and notebooks for retail or released as an installable ISO image, then we will see some changes. It is Ubuntu. But not as we know it.

Regards.

---

### Post by Frogs Hair on 2015-10-27
I upgraded during the Beta phase and uneventful describes it best. I&#8217;ve seen no reason for a clean installation.

---

### Post by QDR06VV9 on 2015-10-27
I also have to agree with Frogs Hair!
14.04 for me at least is just hard to beat.
But I crave the excitement of testing the new releases. (Like a moth to flames)
Kind Regards

---

### Post by mikodo on 2015-10-27
Thanks everyone.

Capturing shared insights and experiences. 

Seems, the old days of huge changes per new releases are gone as we know it. In upcoming new releases we can expect to see huge changes again albeit, in a different fashion. Then possibly, the new changes coming expected with Ubuntu-core and snappy updates may, bring us back to "uneventful" changes, for the end-user's experience. With that, end-users quite possibly will have, steady "uneventful" changes that might be, very progressive. 

Huh, what did I just say?

:)

---

### Post by coldraven on 2015-10-28
Last weekend my hard drive started to fail (it went read only) so I swapped it for another. I had been running Ubuntu 14.04 64 bit. The only USB stick that I had lying around was a Linux Mint 17 32 bit live installer. So I installed that but was not happy because Firefox was about 20 versions out of date and I could not view certain web-site with it. Then I decided to get Ubuntu 15.10 and install that over the whole drive. 
  Firstly the installer did not detect the Linux Mint install. This did not worry me because I wanted to delete it anyway. 
 When it got to the partitioning screen all sorts of strange messages appeared so I backed out of the install and ran gparted. 
In the Mint install I had selected "use LVM" and gparted was not able to delete anything other than the small (boot?) partition. Even after searching for answers I could not get rid of the main partition.  
At this point I gave up trying and ran the 15.10 installer again. Success! This time the partitioner just created the usual /dev/sda1, /dev/sda2/ and /dev/sda5 swap.  
So far everything is working well, it automatically enabled my usually troublesome Broadcom BCM4311 wifi card (which Mint did not).  
I think that the dash is now faster to load and switching between workspaces is smoother.  
This is an old HP laptop with the ATI RS690M [Radeon Xpress 1200/1250/1270] video card using the Gallium 0.4 driver and it all looks good.

Edit: My keyboard does not work after resuming from suspend. 
Edit2: The keyboard stops working after shutting the lid even though it's setting is to "Do nothing". It can be reactivated by logging out and back in.

---

### Post by bob120 on 2015-10-28
I have installed it by upgrade twice. End up with problems that I cannot fix, so I reinstall 15.04, the problems never end. Yesterdays upgrade prod suckered me into 15.10 again. My reason is there never was a search box in "software" and sd does not work anymore (does, doesn't, does, now don't). Read my topic on this search box problem I posted earlier today.

---

### Post by cbennett926 on 2015-10-28
Upgraded from 15.04 to 15.10, upgrade went smoothly albeit my Nvidia drivers were borked; after fighting with it among performance issues with getting Optimus/Prime working I downgraded back to 14.04.3 and lo-and-behold I am back to the Ubuntu I fell in love with.

---

### Post by mikodo on 2015-10-28
> **bob120 said:**
> I have installed it by upgrade twice. End up with problems that I cannot fix, so I reinstall 15.04, the problems never end. Yesterdays upgrade prod suckered me into 15.10 again. My reason is there never was a search box in "software" and sd does not work anymore (does, doesn't, does, now don't). Read my topic on this search box problem I posted earlier today.
I hope you receive knowledgeable replies to your question(s). 

[http://ubuntuforums.org/showthread.php?t=2300799](http://ubuntuforums.org/showthread.php?t=2300799)

> **cbennett926 said:**
> Upgraded from 15.04 to 15.10, upgrade went smoothly albeit my Nvidia drivers were borked; after fighting with it among performance issues with getting Optimus/Prime working I downgraded back to 14.04.3 and lo-and-behold I am back to the Ubuntu I fell in love with.

So, still problems with Release Upgrades. 

By the by, which process did you use to downgrade. Pinning possibly?




For myself, I had started a file for Release Upgrading thinking, I might try it for the next LTS with this box. Just for the experience.

This is a recent informed post from mcduck on using apt, and its abilities. I added it to my file:   [http://ubuntuforums.org/showthread.php?t=2299589&p=13379167&highlight=release+upgrade#post13379167](http://ubuntuforums.org/showthread.php?t=2299589&p=13379167&highlight=release+upgrade#post13379167)

"The command to actually update to next release version is *do-release-upgrade*  (although manually editing your sources.lst to point to new version's  repositories and then running a dist-upgrade would also get you to next release version. But the *do-release-upgrade* command does some checks, disables PPA repositories and other things to make sure the upgrade goes smoothly.

---

### Post by SantaFe on 2015-10-28
No problems updating to 15.10.  Still trying to figure out what the heck's different, as everything works like it did in 15.04. :D

---

### Post by echotech2 on 2015-10-29
I'm with SantaFe. Got the Update icon - clicked on it - clicked on Install - entered password - went to make a coffee - came back - clicked on Restart Now.  Rebooted and everything is working as advertised and as SantaFE said, no obvious differences.

---

### Post by DougieFresh4U on 2015-10-29
Thank you UBUNTU!!
The 2 previous releases I tried on my newer Windows 10 machine with much failure.
I have been without using Linux for over a year (machine came with Win 8.1) I had to do a recovery
every time I tried an UBUNTU DVD
Well this morning I tried a 'live' run, 15.10 and it was great. So I did a little reading/research
and decided to try a dual boot. It went without any issues. Was presented with grub when I rebooted.
Upon a second reboot I had to press f10 and select Ubuntu as grub didn't show. 
I am so glad they have worked out the issue with newer hardware and Windows locking
out other operating systems.
Machine seems to be doing quite well with 15.10
Thanks again and I am quite happy again!!:D:D

---

### Post by Astarroth on 2015-10-29
I did the upgrade two days ago now and it went as smooth as could be. I have not had any problems. This has been a great upgrade.

---

### Post by Swagman on 2015-10-29
I decided to build an entire new machine for 15:10 as my previous build was getting on and after buying a new 28 inch monitor running at 4K  it was starting to struggle & glitch.

Here's the old setup with new monitor (AMD Phenom II 965 Black Edition X4core with GTX 460 and 8mb RAM) ... [http://i.imgur.com/RIxwad9.jpg](http://i.imgur.com/RIxwad9.jpg) 
If you look under the table you'll see the "still Boxed" GTX 970 waiting for the rest of the bits to arrive.
Here's the bits for the new build.... [http://i.imgur.com/PlIAdKD.jpg](http://i.imgur.com/PlIAdKD.jpg) 

and up  and running on a Fresh install of 15:10 onto SSD

[http://i.imgur.com/Iw425Zk.jpg](http://i.imgur.com/Iw425Zk.jpg) 

All these are links only because they are BIG pictures.

The only issues I had were a lack of knowledge of new Secure boot Bioses (UEFI) and I got an "Upstart" crash a couple of times. I haven't done anything and that error doesn't seem to have come back.

All in all - Success

---

### Post by Cecil on 2015-11-01
My experience, having switched from Windows 10, has been mostly good, with a few problems that I had to sort out. First, the audio from my Fiio e07k was garbled. It was fixed by switching from the front-panel USB ports to a rear port. Then it wouldn't recognize any of my gamepads, though for some reason restarting the computer with the gamepad plugged in fixed that. Also, been trying to get Wildstar running under Wine, every time I try to run the installer it gives me an error message (that I can't remember the contents of right now), despite following a bunch of tips from other users. However, I realized that I'm not even planning on actually playing, I just wanted to see if I could get it to work.

Other than that, most other things work great. My Windows 7 VM, for one thing, runs a lot better under a Linux host than it did under Windows 10. The VM boots so fast it doesn't even have time to finish the Windows logo. As for the few Windows programs I still want to run, they work fine under the VM, so I'm pretty much set.

---

### Post by mikodo on 2015-11-01
> **Cecil said:**
> -All that you said-

Other than that, most other things work great. My Windows 7 VM, for one thing, runs a lot better under a Linux host than it did under Windows 10. The VM boots so fast it doesn't even have time to finish the Windows logo. As for the few Windows programs I still want to run, they work fine under the VM, so I'm pretty much set.

1. I'm really happy to hear of your success!

2. Seems, you have been thoughtful in your transition from Windows to Ubuntu base-install. Much of the advice on transitioning from MS Windows suggests dual-booting, Ubuntu and Windows initially, or/then with > to Ubuntu host with Windows "guest", to allow the continual usage of Windows when needed. Some, (probably most), transition from there to only Ubuntu and Linux. Sometimes with wine etc, for some things still needed.

Doing the transition thoughtfully and, with a plan for using what one needs is helpful as, you outlined.

Thanks, for sharing.

---

### Post by angusk on 2015-11-02
Upgraded two machines from 15.04 to 15.10 and one from 14.04 to 15.10. Encountered a minor problem with VirtualBox on one machine and am having issues accessing non-audio media on CD/DVDs. Other than that all went smoothly. :)

---

### Post by malspa on 2015-11-02
I installed Ubuntu 15.10. Only problem I've seen so far, I added Synaptic but Synaptic's History doesn't work. Bug reports:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1487890](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1487890)
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1471445](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1471445)

---

### Post by windwalker2 on 2015-11-02
I installed 15.10 7 days ago and it installed flawlessly dual boot older machine (5 years). Only issue is when I just try to "log off" it hangs with it waiting for Plymouth? still working on that. It detects and installs the codecs needed great!

---

### Post by bapoumba on 2015-11-02
Threads merged.

---

### Post by SteveTyrer on 2015-11-04
Updated from 15.04 to 15.10 on a Lenovo yoga 30011IBY, time taken less than one hour all went well with no errors, touch screen now works and boot time looks to be faster

---

### Post by billgoldberg2 on 2015-11-27
My Windows 10 installation became infected with malware after I left a family member unattended for 25 minutes (he tried to download Word and obviously it was malware) and I was unable to remove it so I said screw this, let's try out Linux again. I had some experience with LInux in the late 00's.

I searched for my usb disk, downloaded Ubuntu 15.10 and 20 minutes later I booted into Ubuntu. Straight away I didn't like it. My Belkin USB Wifi dongle didn't work so I had to break out the 15m ethernet cable. The GUI is a mess and I had constant errors about language packs and I was unable to fix it. I tried out the store thing but it crashed during installation. 

Not liking what I saw I installed the kubuntu desktop instead. I got some errors and APT broke. It looks really awesome but it was unstable, apps kept crashing and I had screen flickers. I got a prompt to update my system (including a kernel update I believe), rebooted the pc and voila, the installation was borked. The login was a black screen but typing my password blind and hitting enter got me to the desktop but instead of seeing the desktop I got a rainbow of colors in what seemed like a driver issue.

Luckely I have a smartphone so I could start up my google fu. I managed to get into recovery mode and spent a good while fixing apt that wasn't working and then following about a dozen guides to be able to start a low graphics mode ubuntu desktop, having to reset my pc multiple times because of a wrong turn that made the entire thing freeze up.

In the end I managed to create a bootable Linux Mint usb and have been using it without issues for over a day now, impressive as I believe it's based on Ubuntu. 

Not a good experience compared to the Ubuntu versions I tried in 07-09. Mint is wonderfull though, I even got LoL to work and about half my steam library is playable.

---

### Post by brianewalsh2 on 2015-11-30
My upgrade went smooth, the only trouble I have now that I haven't fixed yet is that the update broke shutdown and I have to press the button to shut down. I get a shutdown halted message?

---

### Post by Wade_Fogarty on 2015-12-17
My Windows 10 installation was on the "fast track" & died hard after an update in October.  I'm pretty good with Windows but every attempt to repair the installation or use restore points failed with errors & then, to add insult to injury, the reinstall didn't like my upgraded Windows 8 license.  Rather than reinstall Win 8 and upgrade again, I thought I'd try dual booting Linux again.

I did _absolutely no research_.  I figured I'd try Ubuntu and just downloaded the latest version from the website.

After finishing the install, I researched Ubuntu and found a few articles of "first things to do after install".  It was then that I realized that 15.10 had come out **the day before I installed i**t.:o

I did some recommended first steps, getting Unity-Tweak, the Arc theme and Numix circle icons installed as well as Google Chrome.  Then I started checking off the boxes for things I needed working from Windows.

1. Pithos fixed my Pandora itch immediately
2. Spotify was a pain to get working. I found the answer after launching from the command line and researching the launch error online to find out that it needed a older library installed for it's dependency to work properly.
3. Teamviewer works great and let me continue providing IT support to the family
4. Adobe Digital Editions is needed to check-out books from the library to my Nook.  It was a real pain to get working, but with a combination of playonlinux, winetricks, and online answers about forcing the Nook to mount as a floppy drive, it's working

I was in absolute shock that both the printing and scanning features of my wireless Deskjet printer "just worked" after simply discovering the printer through System Settings.  I absolutely love the Variety wallpaper changer now that I've set it displaying landscapes with superimposed custom quotes (Bible verses in my case). 

It's been almost two months now.  I've removed the Windows 10 installation and am exclusively using Ubuntu.  My PC is running better than before and I'm able to do almost everything I would do under Windows. My Unity theme + Variety is stunning.  I can't see myself switching back :)

---

### Post by wepbep on 2016-01-18
lenovo yoga 500 15isk:

Windows 10 uefi + last upgrade
Ubuntu...out of the box (on 14lts was a wifi problem)
(W10-user and Ubuntu Home on same nfts partition, firefox and thbird use the same profiles on both OS)
Exept brightness and flip screen everything works
Brightness did work for a bit...

Thanks Ubuntu :)

---

### Post by Johnny Clocks on 2016-01-18
Dualing Win 10 Pro and 15.10, machine is an Athlon II X4 640, Radeon HD 6570, Gigabyte GA-78LMT-USB3 and 4 GB RAM.

Tried Ubuntu MATE first, did not have a good time, ran into issues where the OS just plain wouldn't load on occasion, sitting me at a black screen with no monitor output at all.
Tried stock Ubuntu after and is running excellent, aside from my current endeavor of getting WDNA3100v2 drivers installed for a wifi dongle.

---

### Post by Christopher_Stayne on 2016-01-23
I had some issues.  Im not really sure what was going on, but I had to reinstall 4 times to get it to finally work.  Before it would install but wouldnt boot.  The 4th time was the charm and has worked great since.

---

### Post by itpro007ca on 2016-01-23
I recently installed Ubuntu 15.10 on an old Emachines e627-5974 laptop that previously had Windows 7 on it.

The install went well.


* Bootup and Shutdown good
*wifi and ethernet both work.
*Sound is good.
*Not snappy,but better than under Windows 7 .

One problem:

*No 3D ATI graphics

---

### Post by abhilabh on 2016-02-21
Hello, I recently shifted from Windows 07 to Ubuntu for various reason from viruses to windows crashing on its own   , First I installed 14.04 LTS 64-bit version and then Upgraded to 15.10 . With 14.o4 everything worked well but after upgrading OS to 15.10 I faced following issues. 

1> Took almost 6-7mins to boot first time 

2> Automatically It went into CLI mode (tty1) after I entered my Login details . Evey attempt to update Display Drivers failed . Tried 2-3 suggestions that were on ASkMe and few other forums . Tried sudo ubuntu-drivers autoinstall but it too failed :(

Overall experience with 15.10 upgrade was bad :( 

hence from 15.10 I shifted back to 14.04 and its been wonderful experience since then . 14.04 works flawless on my PC. 

System Config 

AMD FX 6300 six core processor 

ASUS M5A78L-M  

8gb RAM . and tons of storage space :D

---

### Post by brandon48 on 2016-04-12
On 4/11/16 i installed Ubuntu on a 2GB USB. I launched it and installed it with no issues. The thing that i disliked was how i had to get an add-on for mp3 which took a while with no internet adapters with the PC I was working on. Once i got that i relaxed and felt great that I just installed a OS.

---

