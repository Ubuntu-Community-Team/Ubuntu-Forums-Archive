---
title: "Installation Diary: 5 days in."
date: 2008-02-24
forum: Testimonials &amp; Experiences
---

### Post by statto1977 on 2008-02-24
This Tuesday I installed 7.10 on my laptop. I'd tried dabbling with Linux before (dating back to Mandrake 7.0), but I'd always found myself booting into the Linux partition less and less as time went by. This latest attempt to migrate has been based on annoyances with Vista.

**Tuesday:** Had the day off work, so downloaded the 7.10 ISO and burnt a CD. I used Paragon Partition Manager to set up a 30GB partition on my laptop hard drive. Installed without a hitch (in about 20 minutes). My wireless connection was picked up no problem, in fact everything seemed fine except the sound. A quick search on the forums provided a solution via the command line. Now sound worked, but when I plugged headphones in the sound still came out the speakers. Another search and command line prompt and the problem was solved. I also came across a potentially catastrophic hard drive issue (HP530 problem). This involved a more complex procedure, but still done within ten minutes. At the end of the day I was fairly impressed with its usability, but still felt the initial problems I faced showed it had some way to go to catch up Windows.

**Wednesday:** I started having a proper look at what kind of software was installed. Open Office was just as I expected (I use it on my Windows installations), but it's nice to have it installed as standard, ditto The Gimp. I had a look at the add/remove programs list, and tried adding a few packages. The speed and simplicity of installation was a bit of a wow factor, and overall at the end of day two I was feeling more positive about the whole experience. On Wednesday I also added all the stuff I needed for mp3, flash and divx playback (I should also mention that as Firefox is my browser of choice on Windows there was no issue using it under Ubuntu).

**Thursday:** I added Wine, and installed a couple of programs that are exclusive to Windows that I need to use. I had to do a bit of Googling to find out how to get them running as I wanted, but there was nothing as complex to deal with as on day one. At this point I really began to grasp how powerful this OS is. I've also been impressed with the level of support available on the forums. :)

**Friday:** I started looking at tasks that I regularly work on in my Windows installation. Firstly, torrent downloads. BitTorrent worked straight away, no problems whatsoever. Next, CD ripping. Sound Juicer worked better than anything I've used in Windows. Task three, playing mp3 files. Totem was OK, but I found Audacious suited my needs best (not quite as good a Sonique for Windows, but not bad at all). Fourth, DVD ripping. I encountered a problem here, as my DVDs wouldn't even play. I soon realized I needed to install libdvdcss2. Once that was done, I was good to go. At that point i was flabbergasted to find out that my favourite video player, VLC, was available for Linux, so I installed that too. For the DVD ripping itself I came to the conclusion that if I needed something quickly then AcidRip was fine, but for more quality stuff Thoggen was the way to go.

**Saturday:** With most of the more mundane tasks done, I started messing about with the look of the desktop. I installed Compiz Advanced Effects and started messing around with it. Wow. That's all I have to say on this. I also installed VirtualBox in preparation for stuff I'll mention later.

**Sunday:** Today. Within five days I've gone from a tentative dual-boot, to wondering whether I'm going to have any reason to boot into Vista at all. I also downloaded an ISO for Puppy Linux today, and have managed to install it on a 256MB USB stick I had lying around. It works fine, though it's obviously a lot more unpolished than Ubuntu.

I honestly feel like I've been walking through a desert for the past year and I've finally found water... more than I can drink. I haven't got everything set up yet, and I've still got things to do, but I'm very positive about it. I need to get my Palmpilot m515 running, but I can't use that properly in Vista anyway, and a check on the forums reveals it shouldn't be too hard. My digital camera (a Fuji F20) isn't installed yet, but posts here indicate I shouldn't have a problem. My mp3 player will be harder thanks to Sony's SonicStage (which won't work with Vista either), but XP running virtually should do the trick. I've gone from a viewpoint of "It doesn't work - oh never mind" to "It's not working yet - what can I do to solve that".

Sorry this has been such a long post, but I thought it was worth putting in writing what I've done, and this seemed like a better place than some random blog somewhere. I'll probably post here from time to time when I make any significant progress. Thanks to everyone here for making any problem just one search away from solved. :grin:

---

### Post by azimuth on 2008-02-24
> **statto1977 said:**
>  I've gone from a viewpoint of "It doesn't work - oh never mind" to "It's not working yet - what can I do to solve that".


You have just found the key to success with GNU/Linux, it's all attitude. Welcome to the world of free and open source computing.

---

### Post by CaptainCabinet on 2008-02-24
it may be a long post but i enjoyed reading it. :)

---

### Post by wolfen69 on 2008-02-25
welcome aboard. glad to hear you like it.
> At the end of the day I was fairly impressed with its usability, but still felt the initial problems I faced showed it had some way to go to catch up Windows.
i have the opposite view. i have done many, many, many installs of ubuntu and windows. i can honestly say that as far as problems, windows has many more. i go to customers houses day after day to fix win machines. it is far from a joy. hunting down drivers and setting up security programs and agreeing to EULA's. ubuntu has been nothing short of spectacular when setting up for someone. i rejoice when someone wants linux installed. it's so much easier.

---

### Post by statto1977 on 2008-02-25
> **wolfen69 said:**
> i have the opposite view. i have done many, many, many installs of ubuntu and windows. i can honestly say that as far as problems, windows has many more. i go to customers houses day after day to fix win machines. it is far from a joy. hunting down drivers and setting up security programs and agreeing to EULA's. ubuntu has been nothing short of spectacular when setting up for someone. i rejoice when someone wants linux installed. it's so much easier.

I only posted the comment to illustrate how my attitude changed over the course of the week. I would probably be willing to recommend Ubuntu to a complete beginner as long as they had someone to handle the initial installation (the same as I would for Windows).

Slight update: My camera would only work on Vista with the installed software, but in Ubuntu it recognised it immediately, imported the photos, and even told me the make and model of the camera! Obviously that would be far easier for a beginner. I've also got XP running in a virtualbox now. :)

---

### Post by hyper_ch on 2008-02-26
regarding virtualizing and USB devices I found, that VmWare handles those better... if you don't succeed with VBox you might want to try VmWare then.

---

### Post by statto1977 on 2008-02-27
> **hyper_ch said:**
> regarding virtualizing and USB devices I found, that VmWare handles those better... if you don't succeed with VBox you might want to try VmWare then.

VMWare won't install on my machine. I get a not supported comment in the add/remove programs box. I've managed to get access to USB devices by setting it up as a shared folder, but that's no good for Sonicstage, as it doesn't recognise that a USB device has been connected. I've got two desktops I'm going to install to, so hopefully one of those will support VMWare. If not then I'll probably use XP on my oldest PC and put all my music on that.

---

### Post by hyper_ch on 2008-02-27
Did you add the Canonical Parter repositories? VmWare Server is available there.

---

### Post by statto1977 on 2008-02-27
I'm not sure, but the software appears in my add/remove list. This is the exact comment I get:

VMware Player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by azimuth on 2008-02-27
I am just guessing, but a dual core processor is probably necessary to properly run a virtual machine. My Athlon gets the same message while my Turion 64 x2 shows VMware is available.

---

### Post by freebeer on 2008-02-27
I don't know what you might mean by "run properly", but I ran VMWare on a single processor without issue.

---

### Post by azimuth on 2008-02-27
> **freebeer said:**
> I don't know what you might mean by "run properly", but I ran VMWare on a single processor without issue.

I don't doubt it. I just know that VMware is not available to my 32 bit install, but is available for my 64 bit install. I've never found a need for it. The two programs I wanted from Windows work just fine in Wine.

---

### Post by hyper_ch on 2008-02-28
vmware runs fine on a single core.... but as said, add the canonical partner repos and install vmware server.

---

### Post by statto1977 on 2008-02-28
All of this is a non-issue, given the fact that my laptop *is* dual core.

---

### Post by azimuth on 2008-02-28
> **hyper_ch said:**
> vmware runs fine on a single core.... but as said, add the canonical partner repos and install vmware server.

Ok, now the question is what is the difference between the VMware Player and VMware Server?


edit: This bug report [https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/135358](https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/135358)  may explain the problem OP is having.

---

### Post by ukripper on 2008-02-28
You might also want to try Ktorrent for torrents, really good app runs fine in gnome too.

---

### Post by hyper_ch on 2008-02-28
with vmware player you cannot create virtual machines... with the server you can.

rTorrent for torrent files rocks ;)

---

### Post by statto1977 on 2008-02-28
I've managed to load VMWare Server Console via Synaptic, though my restricted drivers manager is now telling me that proprietary drivers are being used to make the VMWare kernel driver work properly. Haven't got too much time to mess about, but I'll try to get my XP installation up and running in the next day or two.

---

### Post by azimuth on 2008-02-28
> **hyper_ch said:**
> with vmware player you cannot create virtual machines... with the server you can.

rTorrent for torrent files rocks ;)

What use is VMware Player and why bother with it in the repositories?

---

### Post by hyper_ch on 2008-02-29
> **statto1977 said:**
> I've managed to load VMWare Server Console via Synaptic, though my restricted drivers manager is now telling me that proprietary drivers are being used to make the VMWare kernel driver work properly. Haven't got too much time to mess about, but I'll try to get my XP installation up and running in the next day or two.
Strange, it should automatically do that when you take the version in the repos. The only thing you need to do is go to vmware's site, sign up for vmware server and get your free serial(s)


if you have an existing vm you can load it into the player... there are also web-generating tools for creating a vm.

---

### Post by statto1977 on 2008-04-01
Bit of an update a month or two on.

It's been over a month now since I've booted into Vista. I have the Ubuntu installation tweaked just the way I want it now. Things have gone so well that today I wiped my desktop hard drive and installed Ubuntu (no dual-booting for that PC!). I've also been messing around with other distros, and have got a Puppy Linux install booting from a 256MB USB stick. In the next few months my work will be selling off some old laptops for around £50 (about $100), so I'm planning on picking up a few to experiment with a few other distros.

All in all, it's been a good few weeks. :)

---

### Post by ukripper on 2008-04-03
puppy linux should work perfectly fine anything above 50+ MB RAM and 200Mhz + processor. Old laptops should be happier.

---

### Post by hyper_ch on 2008-04-03
> **statto1977 said:**
> today I wiped my desktop hard drive and installed Ubuntu (no dual-booting for that PC!).

I hope you run first the DesktopCD to check how your hardware is recognized?

---

### Post by statto1977 on 2008-04-04
> **hyper_ch said:**
> I hope you run first the DesktopCD to check how your hardware is recognized?

Of course! :)

---

### Post by statto1977 on 2008-04-17
Another update:

I've finally got to a point where I saw absolutely no need for Vista whatsoever, so I started looking at getting rid of the Vista partition of my hard drive. I got gparted, and was planning to delete the Vista portion, then move the Ubuntu partition left, ans resize the partition to fill the drive. Managed to delete the Vista partition no problem, but the procedure moving left failed about a third of the way through. I was a bit nervy about trying again, as I've heard horror stories about people losing all their data, so I decided to just format the partition and use it for all my media. That worked fine.

Now I have a problem though. No matter what I format the drive as, I'm unable to rename it, create folders in it, or delete files I copy to it. If I format it as ext2 or ext3 then I also have a folder called Lost and Found, and I lose 4GB of drive space. If anyone could offer any suggestions then I'd appreciate it. Would I be better off trying what I did originally and hoping it works this time?

EDIT: Sorted the read/write issue by using chown, as it turned out the owner was root, limiting my access. I still have 4.1GB of lost space for some reason.

---

