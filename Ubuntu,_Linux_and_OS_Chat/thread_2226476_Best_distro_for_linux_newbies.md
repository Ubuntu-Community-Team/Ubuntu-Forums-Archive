---
title: "Best distro for linux newbies"
date: 2014-05-27
forum: Ubuntu, Linux and OS Chat
---

### Post by veddox on 2014-05-27
Hi guys,

a family I know are thinking about taking a shot at Linux, and I'm not sure what distro to recommend. Currently they have Windows 7, which is really slow on their 1GB RAM, 2GHz single core laptop. Therefore it would have to be a pretty light distro. Also they are not very computer-experienced, so it should be as user-friendly as possible, with a DE that's close to Windows (i.e. not Gnome Shell or Unity). The setup is not so much an issue, I would be doing that for them, but the actual usage should be easy and stable.

The options I have been considering are: Linux Mint 13 with MATE Desktop, Lubuntu 12.04, elementaryOS Luna.

Would you choose any of these, or something else?

---

### Post by LastDino on 2014-05-27
From what you've, I would go with Lubuntu.

With that config, Xubu would be pushing it but Lubu could work perfectly. If Ubuntu family is not what you want, you can go with Fedora 20 XFCE or PCLinuxOS XFCE. 

Debian could work too but I've no idea if they have mini version or minimum bare-bone install to work with that hardware. I've never tried Mint myself, but people coming from Windows usually like it, so I wont discredit it.

---

### Post by codingman on 2014-05-27
Newbies? Definetely Mint or Lubuntu. Lightweight? Lubuntu.

Sure, the MATE desktop is not terribly bloated, but just doesn't have the feather touch that I find with LXDE.

---

### Post by King Dude on 2014-05-27
Lubuntu or Xubuntu would be your best bet in my opinion.

---

### Post by RadicaX on 2014-05-27
Lubuntu out of box has a very familiar interface to Windows (With the taskbar on the bottom and such). Looks okay, and can run on very low amounts of RAM. Though mind you, with 1 GB of RAM I am running XFCE fine. The difference is I have a dual core processor, Single core processors are a big problem for computers. Believe me, if you can run 7 on it, you can handle Xubuntu and Lubuntu. But I would recommend Lubuntu in this case, and I would maybe recommend lightweight versions to certain browsers for added speed, and less cpu usage (I find Midori on a whole to be about 20% less in CPU usage compared to firefox, but I find it to be a bit clunky in the interface compared to Firefox out of the box). 

There are other Linux choices out their too, with super lightweight DEs and such, but for ease of use, Lubuntu is a great option. Debian is good... But it takes setting up. People do not like to read, nor learn about computers, they like to point and click often, so Lubuntu is really the way to go, I would think anyway. Try out a few flavors and see what they like. Linux Mint also has an XFCE version, and that is light weight... but still a single core processor might be better suited for WMs or LXDE.

---

### Post by monkeybrain20122 on 2014-05-27
> **LastDino said:**
> From what you've, I would go with Lubuntu.

With that config, Xubu would be pushing it but Lubu could work perfectly. If Ubuntu family is not what you want, you can go with Fedora 20 XFCE or PCLinuxOS XFCE. 

Debian could work too but I've no idea if they have mini version or minimum bare-bone install to work with that hardware. I've never tried Mint myself, but people coming from Windows usually like it, so I wont discredit it.

Actually I don't think there would be any performance difference between xbuntu and lubuntu for that kind of hardware, if you push it further to 512 G or ram then may be there is a difference, I don't know.
However, Lubuntu is considerably more buggy IMO. 

Out of the box Lubuntu does seem to have more stuffs installed comparing to xubuntu 14.04 (which seems to have trimmed down the default apps quite a bit comparing to previous releases), which may be a pro or con depending on your purpose. A strange choice of Xubuntu 14.04 is that it comes with Ubuntu Software Centre instead of synaptic and gdebi like it did before, that won't work well with weak machines. But that can be easily remedied. After testing out  both recently on a friend's laptop I think it is a lot more troublesome to google and implement the workarounds for a myriad o Lubuntu  bugs than to just install/change a few packages and settings in Xubuntu. Whatever small performance gain just doesn't make up for the troubles.

Fedora is ok if you are a bit experienced  but II won't recommend it for  Linux newbies. Also there are a lot less precompiled binaries comparing to Debian/Ubuntu.

Debian is hard to set up for newbies. The text based installer can be intimidating and also hardware that works with Ubuntu out o f the box may not work for Debian because 'non free' components have been removed/deactivated so some extra work would be needed. Also Debian stable is VERY old and outdated. Debian unstable would be too unstable. So I won't recommend that either.

Don't know about PCLinuxOS, the mere fact that it strives to reproduce a counterfeit Windows experience is enough to turn me off. :)


So basically it boils down to L/Xubuntu or Mint.

---

### Post by ian-weisser on 2014-05-27
> **veddox said:**
> it should be as user-friendly as possible, with a DE that's close to Windows

Those are conflicting goals.
Been there, set up non-technical users with...Unity.

Unity is designed and tested to be very user friendly.

Imprinting (on OSX in this case) took them about a week to overcome. For the last three years, they have been very happy with Unity. And I get almost no support calls from them anymore.

If your friends want a Windows experience, let them purchase Windows.
Don't sell Ubuntu as something that can be Windows-like. It can be close, but it's not a Windows clone. You are creating more work for yourself later, and setting them up for disappointment. Better to let them unlearn their Windows habits. And tell them that up front.

---

### Post by Leviata on 2014-05-28
undefined() method does not exist

---

### Post by sudodus on 2014-05-28
> **veddox said:**
> Hi guys,

a family I know are thinking about taking a shot at Linux, and I'm not sure what distro to recommend. Currently they have Windows 7, which is really slow on their 1GB RAM, 2GHz single core laptop. Therefore it would have to be a pretty light distro. Also they are not very computer-experienced, so it should be as user-friendly as possible, with a DE that's close to Windows (i.e. not Gnome Shell or Unity). The setup is not so much an issue, I would be doing that for them, but the actual usage should be easy and stable.

The options I have been considering are: Linux Mint 13 with MATE Desktop, Lubuntu 12.04, elementaryOS Luna.

Would you choose any of these, or something else?

Lubuntu 12.04 has passed end of life long ago. It had *no* long time support.

 Xubuntu 12.04 LTS is supported until April 2015. Other light-weight distros and re-spins based on Ubuntu 12.04 LTS promise support until April 2017: Bento, Bodhi, LXLE. These might work well for your friends.

Lubuntu and Xubuntu 14.04 LTS have long time support until April 2017. Both might work well for your friends, particularly since you will set up the system (and work around a couple of bugs in Lubuntu, for example the Network Manager Applet (to make it easy to connect to wifi).

The selection between a system based on 12.04 and 14.04 depends on the hardware drivers. Install a system that works well. If you select Xubuntu 12.04 LTS, you should be prepared to replace it within a year.

-o-

Linux Mint is also a good choice for beginners.

---

### Post by mastablasta on 2014-05-28
then again Kubuntu has the look and feel of windows and should work well on that setup. it does many things the same way while there are also plenty of improvements. many thing there work out of the box, although the 12.04 was a better version in my opinion.

Xubuntu is easy to use and can be easy to modify to look more windows like. but like people said it is no clone. no linux is. eventhough some pretend to be such as ZorinOS. bu then again if people want windows they should just go with windows.

by the way why would single core processor be a problem? i am manintaining 3 - they are not as fast as new mashcines, but they are not that slow either.. in fact less GPU intensive new games work just fine on some of them (on those PC that are not too old)...

---

### Post by LastDino on 2014-05-28
> **monkeybrain20122 said:**
> Actually I don't think there would be any performance difference between xbuntu and lubuntu for that kind of hardware, if you push it further to 512 G or ram then may be there is a difference, I don't know.
However, Lubuntu is considerably more buggy IMO. 

Out of the box Lubuntu does seem to have more stuffs installed comparing to xubuntu 14.04 (which seems to have trimmed down the default apps quite a bit comparing to previous releases), which may be a pro or con depending on your purpose. A strange choice of Xubuntu 14.04 is that it comes with Ubuntu Software Centre instead of synaptic and gdebi like it did before, that won't work well with weak machines. But that can be easily remedied. After testing out  both recently on a friend's laptop I think it is a lot more troublesome to google and implement the workarounds for a myriad o Lubuntu  bugs than to just install/change a few packages and settings in Xubuntu. Whatever small performance gain just doesn't make up for the troubles.

Fedora is ok if you are a bit experienced  but II won't recommend it for  Linux newbies. Also there are a lot less precompiled binaries comparing to Debian/Ubuntu.

Debian is hard to set up for newbies. The text based installer can be intimidating and also hardware that works with Ubuntu out o f the box may not work for Debian because 'non free' components have been removed/deactivated so some extra work would be needed. Also Debian stable is VERY old and outdated. Debian unstable would be too unstable. So I won't recommend that either.

Don't know about PCLinuxOS, the mere fact that it strives to reproduce a counterfeit Windows experience is enough to turn me off. :)


So basically it boils down to L/Xubuntu or Mint.
I've P4 3.0Ghz and 4gb ram.

I've Xubu installed in one of my partitions, it does start to take considerable amount of RAM with longer session up time and resource hungry bad habits.
I often find myself running this command to clear it, which was picked from google.
```
sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"
```
I haven't used Lubuntu to comment on its buggy nature, but you're absolutely right, if it is that troublesome, I might pick Xubu.

Fedora XFCE is currently my main OS, I dunno, I've absolutely no problems with it and I've done things to it which have broke both Xubu and Arch variant Manjaro in past. I doubt that your average  user would recognize the difference tbh, even I'm not sure which are these binaries you speak of (pardon this humble ex-windows user) :P

I'm planning to install Debian as my next experiment so I'll see about it. From what I've read up, my hardware should work with it out of the box. 

PCLinuxOS is based on Mandriva and have capacity to update itself after only one install. And like you said, its UI is considerably similar to Windows, which might be turn off for us it is usually what those windows migrants are looking for. Though, I usually settle for this only if Ubuntu family and Fedora are not an option. 


Did someone just suggest Arch? :eek:

---

### Post by veddox on 2014-05-28
OK, from the sound of things, I think I'll just stick with Mint :-)

I was going to go with Lubuntu, but if it is indeed buggy, then that is definitely not what I want. I just fired up Mint (with MATE) on my old Laptop and had a look at its stats: with 11 programs open (which is more than they will ever use, most likely), it's still sitting comfortably at 600MB RAM usage. That's quite acceptable. And considering that I have a little Mint experience, but none with L/Xubuntu, I think that tips the scales for me.

I do have one question left, however: I'm planning to install Linux alongside their Windows for a start, while they're getting used to it. Should it turn out that they don't like it after all, can I just erase the Linux partition with GParted and Windows will take over booting again, or do I have to go through a special procedure there?

---

### Post by LastDino on 2014-05-28
Safest way to remove Linux is to use OS remover/uninstaller from Linux secure remix or just install one on Ubutunu bootable and use. 
Read this 
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by sudodus on 2014-05-28
The dual boot system will boot from grub, which sits in the linux root partition (unless you have a separate /boot partition). So if you wipe linux, you will have to reinstall the Windows bootloader. It can be done from a Windows install disk.

---

### Post by veddox on 2014-05-28
> So if you wipe linux, you will have to reinstall the Windows bootloader. It can be done from a Windows install disk.

Just stick in the disk and choose "Repair installation"?

Or does the OS-Uninstaller lastDino mentioned automatically restore the Windows bootloader?

---

### Post by sudodus on 2014-05-28
It is not too difficult to use the Windows disk. I will let [LastDino]("http://ubuntuforums.org/member.php?u=1919686") answer for the other method.

---

### Post by monkeybrain20122 on 2014-05-28
> **LastDino said:**
> I've P4 3.0Ghz and 4gb ram.

I've Xubu installed in one of my partitions, it does start to take considerable amount of RAM with longer session up time and resource hungry bad habits.
I often find myself running this command to clear it, which was picked from google.
```
sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"
```.


That is weird, I have just converted two XP laptops to xubuntu, both have barely 1 G of ram and they run really smooth. Tried Lubuntu first, but got rid of it because I was fed up with working around bugs, performance wise there is no difference. Of the two machines one has fairly decent cpu I even put compiz on and make it looks like Ubuntu, why? Just because I can. :) It still runs fast and much faster than XP even with Compiz and this thing is so old that you can't even install Win7 on it, let alone running.

---

### Post by LastDino on 2014-05-28
> **veddox said:**
> Just stick in the disk and choose "Repair installation"?

Or does the OS-Uninstaller lastDino mentioned automatically restore the Windows bootloader?

I've only tried this with Linux systems since I only use those on my PC. But I doubt it will restore Windows bootloader automatically as it is separate process than removing Linux OS itself, I would imagine that you need to run boot repair from same Linux-seucure-remix or  run  ''fixmbr'' from WindowsXP rescue  CD at least. I suggest you keep these tool at your disposal. My windows days were full of problems and I kept Hiren boot CD around.

> **monkeybrain20122 said:**
> That is weird, I have just converted two XP laptops to xubuntu, both have barely 1 G of ram and they run really smooth. Tried Lubuntu first, but got rid of it because I was fed up with working around bugs, performance wise there is no difference. Of the two machines one has fairly decent cpu I even put compiz on and make it looks like Ubuntu, why? Just because I can. :) It still runs fast and much faster than XP even with Compiz and this thing is so old that you can't even install Win7 on it, let alone running.

Well, I keep like 2 dozen tabs open with resource heavy stuff like audio/video playing and there is always something getting downloaded in back. Occasionally, I also run VM with 45% of my RAM. It can really get run over by cache even if actual usage is around 1GB. Under normal usage of just browsing with 6 tabs in ff it is around 600-700 MB.

---

### Post by kira_belka2 on 2014-05-28
In my honesty opinion.. it's mint (mate/cinnamon)

---

### Post by monkeybrain20122 on 2014-05-28
> **ian-weisser said:**
> Those are conflicting goals.
Been there, set up non-technical users with...Unity.

Unity is designed and tested to be very user friendly.

Imprinting (on OSX in this case) took them about a week to overcome. For the last three years, they have been very happy with Unity. And I get almost no support calls from them anymore.

If your friends want a Windows experience, let them purchase Windows.
Don't sell Ubuntu as something that can be Windows-like. It can be close, but it's not a Windows clone. You are creating more work for yourself later, and setting them up for disappointment. Better to let them unlearn their Windows habits. And tell them that up front.

+1
I feel physically sick when I see ugly screenshots like those in post #8 below you. :) If one loves Windows so much then use Windows, nothing easier than that. 

I have never met any request from people for making their Linux desktops look like Windows. If I do I will flatly refuse. :)  (I just converted two old xp laptops for my friend, he was actually quite disappointed that his laptops don't have the specs to run Unity. Instead I installed xubuntu and on the more powerful one put on compiz, docky and an ambience theme to make it look like Unity, much better looking and a lot more functional than any Windows can be on that machine)

---

### Post by LastDino on 2014-05-29
> **monkeybrain20122 said:**
> 

I have never met any request from people for making their Linux desktops look like Windows.

I can second this, plus IMO, making Linux look like WIndows is sending a wrong massage to that new user. All of sudden, these new users start to expect things to happen in Linux as they do on WIndows and that only spells trouble. When I migrated my biggest worry was not looks but keeping my favourite windows applications and for that I experimented with Wine and PlayonLinux quite a bit, then came a day when I thought that was not worth the trouble and searched for Linux alternatives, which by the way, are keeping me quite happy.  And personally speaking, I thought both Unity and XFCE desktop are better organized than windows and it was a breeze to get used to it. :p

---

### Post by stalkingwolf on 2014-05-29
I have installed Mint13 mate for several "newbies" including 2 11 yrolds and a 10 year old.  none have had any problem running with it after being shown where to find things.

As I recall Zorin has a win7 "look" for the desktop.

---

