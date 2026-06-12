---
title: "Ubuntu 16.04.2 will not boot on HP Servers"
date: 2017-05-26
forum: Server Platforms
---

### Post by samgarth on 2017-05-26
Hi

I have downloaded Ubuntu Server 16.04.2 and installed it on two separate HP Servers, one with Ubuntu Desktop Gnome and one with just basic configuration. As soon as they boot they both freeze. The gnome version freezes on the logo unless I press escape in time and then they both freeze with blank screens. I have tried pressing shift when it boots but it does not give me any option other than to boot the OS.

Is there a reason it will not boot? I am new to Linux. One server is a HP DL380 G5 and the other is a DL380 G7. Both with over 40GB Memory.

Thanks

Sam

---

### Post by Michael_McKenney on 2017-05-26
I bought the Cisco Virtual Lab.  It had Lubuntu 14.04.  I could only install it on my HP DL380e Gen8 using the SATA ACPI controller.   I was told not to upgrade above 14.04 or it would break.   Did you get any version to load properly on those servers.    HP to be optimized needs their HP Proliant Support Pack installed on the OS.   Only Gen 9 HP servers support 16.04.   I checked the compatibility matrix for HP servers when I built my Cisco VIRL.  I would say a G5 and G7 would be 14.04.

---

### Post by samgarth on 2017-05-26
Thank you Michael I will give that a try. I have tried CENTOS and Ubuntu Desktop but not luck.

---

### Post by Michael_McKenney on 2017-05-26
HP I know.  I run a corporate Data Center filled with HP blades, servers, SAN and switches.  

Servers are only designed for the OS that is on their compatibility matrix.   I found trying to run Linux on them is usually hard to impossible.  Even my refurbed Gen 8 for my Cisco Virtual Lab or VIRL can only do 14.04.  It can't run the SAS drives that came with it because no SAS controller support.   It is not optimized because I can't run the support pack.   It works fine for Cisco VIRL.   Cisco VIRL team said it is working great by their standards.  

I did a lot of research before dropping $1500 on my server.   Returning it was not an option.   Even my Ubuntu box is going back to 16.04 because 17.04 SAMBA does not support my XP Pro x64 connection for backups.

---

### Post by darkod on 2017-05-26
If you want to use Ubuntu Desktop (with GUI) you might be finding issues with the graphics card... But Ubuntu Server is usually quite easy to work with many brands of servers, even if the manufacturer doesn't show the model as officially certified.

I have the small cube HP Proliant Microserver since like 2012/2013, and it was running clean install of 12.04 without issues. Later upgraded to 14.04, again running good. I haven't upgraded to 16.04 yet because I am considering building a new server in which case I will make new clean install. But I'm rather confident if I upgrade the Microserver to 16.04 it will work.

Be aware that you might run into other issues, not related to ubuntu actually. For example UEFI boot can give you issues. I still avoid using it and set my MBs to legacy only boot. Especially since linux doesn't need UEFI boot like windows does. Windows needs UEFI for GPT OS disks, while linux doesn't. And you need GPT on big disks if you want partitions over 2TB on the other hand.

But with ubuntu you can have big partitions, GPT disks and legacy boot all in one...

---

### Post by walterav on 2017-05-27
The HP DL380g5 16GB (newer motherboard revision capable of running 2 quadcores) is running fine on ubuntu mate 16.04 amd64 Desktop kernel 4.4.0-72 with onboard graphics card, without any graphic corruption on a 4x3 1600x1200 vga display. By inserting at a later moment a seperate Nvidia GPU (CasparCG Server opengl rendering), the onboard ati/amd gpu got deactivated and now its able to do some opengl rendering or probably run a heavy desktop environment. 

@samgarth
As you mention you are new to "Linux", be aware that most ubuntu desktop linux editions require some form of graphic acceleration which will be a problem for still a lot of hardware! If the installer was just textbased (low graphic ncurses) the problems arise after install like in your situation? I can only recommend you two types of install for beginners the "mini.iso" or the "ubuntu mate desktop iso". Stay with the LTS kernel versions unless you have bleeding edge new hardware use "non-LTS" editions like 17.04, or upgrade from within the LTS OS to a newer kernel and graphics stack via HWE. During the mini install "Tasksel" gives you the option to enable ssh or a desktop environment(choose carefully). Limit yourself to server only installs after more insight.

[http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/mini.iso)
[http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/ubuntu-mate-16.04.1-desktop-amd64.iso](http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/ubuntu-mate-16.04.1-desktop-amd64.iso)

As far as I understand you were able to install both ubuntu editions, probably in a low graphic mode ncurses based text/mode installer? 

But depending on the environment in the "tasksel" you choose some sort of desktop environment being initialized after install and now it hangs? 

Did you also install ssh during install, so you can check if the machines are really freezing or its just the graphics card?

---

### Post by Michael_McKenney on 2017-05-27
Darkod, you said run 16.04.1 on my build because it is stable.   When I went to 17.04 from 16.10, it broke.  I run HP in my data center.  So I know the HP break / fix team.  They were nice enough to research it for me.   They told me that 14.04 would work on my HP DL380E Gen8.  It is stable on the ACPI hard drive only.   Don't upgrade!  Do you want to take the risk of putting in 16.04 on earlier HP servers and risk downtime when it breaks?   What happens if you get it working and an upgrade breaks it?

---

### Post by darkod on 2017-05-27
@Michael, to be honest, there is no great risk in my case because I can simply reinstall the server when ever I want. It is my network storage (nothing that needs to run 24/7), and all data is on separate encrypted volume of 5TB. I can format the root as much as I like and by copying couple of config files I have my shares running again.

Plus, I lost my faith in big brands suporting linux long time ago. It might be a wrong approach but I don't put too much faith in officially certified linux lists simply because the manufacturers don't care about it and are forced to promote MS. For example, in my HP Microserver I have 3TB disks that didn't even exist when it was bought. Do they work, yes. Did I buy them as certified HP part number components? Of course not, they would cost 4x more... The same about the RAM. I stuck in there 4GB ECC Kingston ValueRAM, not any special brand certified model.

So when they say 16.04 would not work, why don't they sort it out? It has been released quite a while ago, plus they should work in paralell during it's development to prepare their HW. Which they don't, at least not officially... If we stick to their official lists we would need to (almost) always pay MS for their expencive licenses... And get stuck with their OS inefficiencies...

But all this is another topic, and not the point of this thread... :)

PS. I still stand by my point about non-LTS releases. I consider them as testing for the next LTS during its development. Which doesn't mean I don't encourage you to try the latest LTS on your server first, check if it works even if HP does not officially have it on its list. I just said I wouldn't rely on the non-LTS versions.

---

### Post by samgarth on 2017-05-31
Hi All

Thanks for your replies. 

Lubuntu 14.04 did work and it even let me upgrade it to 16.10 and still works! Thanks all.

Sam

---

