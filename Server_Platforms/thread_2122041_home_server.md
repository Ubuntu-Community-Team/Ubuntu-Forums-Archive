---
title: "home server"
date: 2013-03-03
forum: Server Platforms
---

### Post by RobertKH on 2013-03-03
Hello everyone. I am building a home server and need a few questions answered before I decide on my OS. I am using a gigabyte E350N Mini ITX motherboard, 4 gigs of ram, 5TB of space on a hot swappable system. The box is a Chenbro SR30169T2 (not that it matters all that much but wanted to inform you fully). I have been going back and forth between Ubuntu Server and FreeNAS for the build. All I want to do is use it for file sharing and dumping. I am not planning on running a mail server or anything else on it, just simply need a place for networked storage and thought that since one of my desktops is Ubuntu and it works slick that the server software would work equally as great. I have 4 systems in my home that would be accessing the server; a PowerPC mac, my Ubuntu desktop and two windows laptops running Win7 Ultimate. The first question I have is would this be "difficult" to set up? I could probably just use the Samba file server to do what I need it to do right? I know that everyone's interpretation of difficult is completely different and I am no slouch to the IT world. I have some experience in Linux but I would say it's not my strong suit. I also wanted to know if I could use it to stream things like movies over my network? I have wifi capable TV and network attached blu-ray player that doesn't have a problem finding my 1TB external that is attached. Do you think that it is even necessary to run Ubuntu Server for such a small set up? What sort of RAID setups can I run with UServer? I don't want to over-complicate this as I need it to be easily accessed by my wife if I am away on business. Any help would be greatly appreciated.

---

### Post by RobertKH on 2013-03-03
I should also add that both of our iPhones need to be able to transfer data to this central source of data. Typically we would back up our finances to it as well as maybe store all of our iTunes media on it so as to free up all of our other computers internal storage. Thanks again.

---

### Post by RobertKH on 2013-03-03
Ok so one more thing to note. My reason for bringing up RAID is data redundancy. My hard drives are 2x WD Caviar green 2TB and 2x WD Caviar green 500gb. I know I can also add in two 2.5" drives, one for OS and another for log files and such. I do not want to lose my data as some is basic and others are complex work files. If I run RAID I can have multiple copies and restore a bad drive if necessary right? I know the best way is to run a backup off site, but I am curious if what I have mentioned could work. Remember I am looking for redundancy. Multiple copies of the same files so drives can be swapped and data recovered if needed.

---

### Post by andrewhamming on 2013-03-03
I would look into running Lubuntu. You can run a samba server. This has GUI for wife to use and is very lightweight.
I have personally used this setup for about 2 years. I had this setup in my lounge room running XBMC straight to the TV and serving files via samba.
All my kids and wife had no troubles using XBMC or lubuntu. I'm pretty sure you can stream using XBMC too.

I have no idea about iphones tho sorry

Another option would be to use ubuntu server then install lubuntu-core (This will give you the basic lubuntu without all the games etc).

Hammo

---

### Post by RobertKH on 2013-03-04
I have XBMC running on my laptop and I love it. I didn't think to run it on this. That has a pretty nice GUI and is easy to use. It also supports Air Play for iOS devices so that is something to think about. What about some sort of redundancy setup? Would RAID work with the drive setup I spoke about?

---

### Post by ranger12 on 2013-03-04
Here is a guide for RAID setup on Ubuntu Server 12.04 if you decide to go with it:
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

There is software in the App Store for accessing servers using the smb protocol. I tried one of them on my iPad 2 for connecting to my Ubuntu Server 12.04 file server and it worked pretty well. You might want to peruse in the App store and see if any of those might fit your bill for your iPhones. I seem to recall being able to stream movies and look at photos right off my server on my iPad after I logged in from my iPad but it has been awhile since I have done this. I don't have as many workstation as you but I have a file server, 1 workstation and a wireless network printer which supports Windows, Mac, Linux and printing from iPad and this has worked pretty nice. I also have the file server setup as a samba PDC for Windows machines that I tested with a Windows XP system last summer. I no longer have that box though.

---

### Post by RobertKH on 2013-03-05
Thanks for the link. It is pretty useful. I found a few apps on the App Store that may serve the purpose that I need. I wonder if I can use ReaddleDocs for the same thing. It allows me to connect to any FTP server via WIFI. I am curious about how to set up my server to send me emails if there is a drive failing or maybe if it gets hot? Can I do that? I am also interested in running a wifi enabled web cam so that I can see around my house when I am away. Would this setup be able to do such a thing?

---

### Post by ranger12 on 2013-03-06
1. I had never heard of ReaddleDocs, so I installed on my iPad to test. It found my ftp server and I was able to log into it under my account and view the folders and files on the ftp server. So it looks like it works fine.

2. I found this link here, it's a little outdated but it might fit the bill. I probably should set this up myself on mine:
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

3. I will do some searching about the webcam. I have never done this on my lan myself.

Later:
You might want to take a look at zoneminder and see if that might fit your needs:
[http://www.zoneminder.com](http://www.zoneminder.com)

There is a build for Ubuntu in the Software Center.

---

### Post by grunge09 on 2013-03-06
I actually have both setup on 2 different machines.  I can tell you Freenas was easy to setup and configure.  You can share files via samba, have ftp, setup raid on disks.   And last time I checked you could run Freenas off a flash drive.  It took me without much Linux experience about 10 minutes and I was up and running.  (setup of devicename, eth0, groing to another pc on nethwork and running gui to setup raid/shares/services.

Freenas Box:

5U rackmount - 16 bay Nas w/ 16 250gb sata Drives.  2 3ware raid controllers using two raid 5 arrays with 1 hot spare drive (each array about 1.3tb)  Bought it at an auction.  Its LOUD when running.  

Ubuntu Server:

Full Tower PC using onboard Sata ports (no raid card) 3x2tb WD green drives (one 2tb drive on the way) booting off a 8gb flash drive (it works but it slows booting down and sudo apt-get stuff).   I will be able to use 2 more 2tb drives before I have to get a card for more raid ports.   Its quiet.  I often forget its running.  

Now you don't NEED a raid controller BUT I would recommend it.  

I just setup Ubuntu Server 12.10, Mdadm (software / fakeraid), smart monitoring, ssmtp, samba, webmin (from a novice point of view it took me 4 days to get it working right).   Some people frown on webmin but it made adding users/shares simple.  

That being said I would say that Mdadm has the ability to "grow" RAID array size especially in RAID5.   Freenas at this time does not.  Sure Freenas has ZFS pools where you can add a drive to the existing pool.  

But mdadm has a few simple commands to add a drive to an array and "grow" it.   Or replace smaller existing array drives with bigger ones (one at a time) then resize array to use new max hdd space. 

Best thing I can offer you is to install virtual box on a machine and download both Freenas and Ubuntu Server and mess with them in a virtual drive and see what you like.

With either way you choose you can use RSYNC to backup data to either Freenas or Ubuntu Server.

---

### Post by ranger12 on 2013-03-06
I agree, it might be a good idea to download both and set it up in a virtual machine and see which one you prefer.

---

### Post by ranger12 on 2013-03-06
Another option you might want to look into is Zentyal. The 3.0 version is based on ubuntu server 12.04 lts.
[Http://www.zentyal.org](Http://www.zentyal.org)

---

### Post by RobertKH on 2013-03-07
Great info guys! Thanks for the replies! Alas you've hit a low spot in my computing knowledge. I know just about nothing when it comes to setting up virtual boxes. Anyone have a link? 

Another question I have is on RAID and hot swappables. When I run out of room (hopefully that doesn't happen) do I need to replace my 2tb and 500g or the entire 5tb worth of space? Would it just rebuild my existing data or would it overwrite what was on the mirrored drives? 

Yet another question would be about backup. I have no idea how I would run a backup. Would it have to be to another 5tb server? If so what's the point? Wouldn't I have the same problem on my backup as I would have on my home server? How large would the backup space have to be? Could I just plug in a 5tb external and have it backup nightly to that? If you have any questions on my setup please see my original posts. 

Really though, thanks for all the info it's helping out quite a bit!

---

### Post by ranger12 on 2013-03-08
On the question of backup, ubuntu 12.04 server does come with a program called bacula. There is a section dedicated to it in the server guide. I have not tried it myself although I should install it and start doing backups on my server. I am going to look into it more myself. Here is the link to the bacula website if you want to check it out: [http://www.bacula.org/en/](http://www.bacula.org/en/)
With the question about RAID; I do not know about that since I do not have RAID setup but maybe someone else who has experience with that can chime in and help.

---

### Post by mobo on 2013-03-09
After just setting up a Ubuntu server with Raid I found this Video to be an absolute no brainer. I use Plex on the server for the home media side and it runs very well, IOS, PC's, and TV's all talk to it fine.

[http://www.youtube.com/watch?v=vQtUBp5aad8](http://www.youtube.com/watch?v=vQtUBp5aad8)

---

### Post by lykwydchykyn on 2013-03-10
You might want to look at ClearOS; it's got a really slick web-based interface.  Based on CentOS.  But freeNAS is good too.

Not that Ubuntu is bad, but nothing in particular commends it as a file server over anything else.

---

### Post by RobertKH on 2013-03-13
Ok so a slight change in plans. I decided to go with 2 1tb drives due to the fact that the box allows me to add 2 more quickly when needed. 

Now on to the new questions. I have a 1tb external laying around (Seagate 7200rpm FreeAgent) and was thinking I could use it for a backup. Is this possible? 
How do I set it up to stripe the drives, or use them in a pool, an backup to my external? 

I'd also like to setup OpenVPN on this server so I can access my data from anywhere. Anyone know any good tutorials? I am so-so with Linux so you'll have to bear with me. I'm also looking at setting up FTP and samba for my windows laptops. Would openVPN allow my PowerPC Mac to access the drives? 

As I've said the motherboard/CPU comes with a HDMI port so ill likely have it plugged into my tv which shouldn't be a problem. I'm wondering if I can stream from my server to my Blu Ray though. It recognizes my laptop but I haven't tried using Ubuntu with it. 

Another question I have is should I install a small HDD to run the OS? If I am planning on striping, shouldn't both drives be the same size exactly? Can I stripe and run the backup I've described? 

I plan on documenting this entire build and posting it on my blog for the rest of the noobs out there. Thanks for the help and insight so far. Keep it coming!

---

### Post by RobertKH on 2013-03-15
So I am still trying to figure this whole remote log in stuff out. I want to be able to be on the road and basically dial into my NAS for file viewing. These files could be pictures, videos, spreadsheets or whatever else I have stored on there. Does anyone know any good ways to log in remotely. I've searched the forums (maybe not enough) and it seems as though everyone is ssh'ing into their servers while on the same wifi. I understand how to use putty or filezilla, but I don't understand how to go about finding the address for my box. Does this make sense to any of you? Can I do such a thing? I know openVPN will probably be the best way and I will probably go that route. I just need to be able to access the entire server while on the road or possibly abroad on a business trip (it can get pretty boring sitting in meetings all day without being able to access the pictures or files on my server). 

On a side note my stuff should be here Thursday so I'll start buildling it next weekend!:biggrin::biggrin:

---

### Post by RobertKH on 2013-03-15
Ha, just found a decent write up in the middle of this lifehacker thread. So disregard my last posting. Anyone wanting to figure this out themselves check it out here. 
[http://m.lifehacker.com/5553789/what-settings-should-i-change-on-my-wi+fi-router](http://m.lifehacker.com/5553789/what-settings-should-i-change-on-my-wi+fi-router)

It's for the linksys wrt54g but you get the gist.

---

### Post by RobertKH on 2013-03-18
So I just found some information on virtualbox and I plan on doing some testing when I get home with setting it up. I do have some questions on it though. Can I use ubuntu server and install virtualbox for a gui? Or is that not a great idea? When using virtualbox, if I wanted to see what creating a volume was like, wouldn't that create a volume out of my physical HDD's? If so, that's no big deal as I don't need to try it. 

On a side note, if I were to run straight up Ubuntu and not server edition, what is really the difference from setting up windows on a 2.5' drive and just sharing the entire thing? I get the added security and CLI, but in all reality isn't the same thing? This box has all the pieces of a normal desktop, just more drives added into it. 

Could I set up to boot to Ubuntu and then run Ubuntu Server in a virtual box? Or is that a poor way to go about it?

---

### Post by darkod on 2013-03-18
Too much going on. :) I can't even follow the questions. :)

So, right now what do you want to know? Accessing from the internet? Something like SFTP (secure FTP). Opening your server to the internet for any other kind of access would be quite dangerous.

SSH can work from internet but with SSH you access the command like, it's not quite like (S)FTP.

I wouldn't run ubuntu server in VBox for any serious task. It's one thing if you only want a quick check for something, but running the server in VBox full time is not what I would do.

As far as I know you can install text version of VBox on ubuntu server with no GUI, but I'm not familiar how easy the management is. I think it does have a web GUI you can access from another machine on the same LAN so that you can set up your VMs more easily. VBox should create a VDI file for the VM, it doesn't partition your physical disks.

I didn't understand the question about installing ubuntu desktop and running windows from a 2.5" disk.

---

### Post by gordintoronto on 2013-03-18
Ubuntu Desktop can do everything Ubuntu Server can do, and it provides familiar tools to help you along the way, such as sharing folders by simply right-clicking on them in Nautilus. It requires a bit more memory, but you have far more than you need.

If you're going to set up remote access over the Internet, you should plan on spending dozens of hours educating yourself on security. Remote access is not difficult, *secure* remote access is a different story.

---

### Post by RobertKH on 2013-03-18
My question was on the premise that I need to have 2 identical sized drives in order to stripe properly right? Since my box has a spot for 2x 2.5" drives I thought I should have my OS installed on that right? FreeNAS runs off a USB stick, and I don't really want to do that. Probably something like a 32g SSD would be great. Only around 50$ on newegg. So should I be installing Ubuntu desktop on that? I should right?

Btw I played with Vbox some tonight, but its doggy as hell. I imagine its because my windows laptop only has 2g ram and I had to dedicate half to the Vbox. I'll do some more testing with raid set-ups and the like soon.

---

### Post by lykwydchykyn on 2013-03-18
I would not stripe the drives.  If either drive has a fault, it's all gone.   
I'm not sure Linux or Windows supports installing the OS to striped drives, unless you do it using hardware RAID, though I could be wrong.   I've put Linux on software RAID 5, which is probably better if you can scare up a third drive.  This can all be set up in the Ubuntu server (text-mode) installer.  I don't think the desktop installer can do this.

I don't understand where virtualbox fits into all this, or why you'd want to mess with that on a home server.  Just a waste of resources.  If you really want to virtualize ubuntu on top of ubuntu, you're better off using containers.

---

### Post by RobertKH on 2013-03-19
My only reason for playing with vbox is that i wanted to try out different configurations before putting them into place on my box. Working on setting up a mdadm setup right now actually. Although I am just using small 1gb virtual disks to see how it behaves. I think that I can pick up another drive. Those WD reds are somewhat cheap at only 85$ for a 1TB. I appreciate all the info. I think that I will go with a RAID setup rather than striping. I don't really want to lose everything because a drive fails. 

Can I have the desktop version of Ubuntu send me an email when a drive starts to fail? I'd assume that I can install the mail server on the desktop, but I am not 100% yet. 

On a side note, I can run FreeNAS on a virtual disk so it doesn't take up an entire drive or have to keep a usb plugged in. I could run it on a SSD, however the smallest would be a 32gb and that would be way to much room for such a small program.

Keep the replies coming. I enjoy reading every one.

---

### Post by darkod on 2013-03-19
If for raid you plan mdadm SW raid, you can install the OS on raid0 with the condition that you create small raid1 md device for /boot. When the boot files are outside the raid0 you can have the OS on it.

If you want the OS on totally separate disk, yes, you will need to add a third one. Whether it's 2.5" hdd, 2.5" ssd or even a CF card with CF-to-SATA adapter, it doesn't matter much. Compared to buying a small ssd another interesting idea is the CF card, especially if you don't need much space like with FreeNAS. It would be ideal for FreeNAS actually, and even for Ubuntu Server if you don't keep much data in /. The server default install with SSH and samba takes only about 2GB.
The main data will be on your array anyway.

As for the array type, have in mind that if one disk fails in raid0 you lose all the data, so it's your choice whether you will use raid0 or raid1.

---

### Post by lykwydchykyn on 2013-03-19
> **RobertKH said:**
> 
Can I have the desktop version of Ubuntu send me an email when a drive starts to fail? I'd assume that I can install the mail server on the desktop, but I am not 100% yet. 


You can set up anything on Ubuntu desktop that you can set up on the server.  Unlike Windows, there's no fundamental difference between server and desktop editions, it's just a question of default packages and configurations.  They both pull from the same repositories and use the same set of packages.

Sending an email means setting up an MTA; I prefer postfix myself.  You'll need to have an SMTP server you can relay off of to send email outside your own network.  You will need to talk to your ISP about that, I don't think most ISPs let you relay because of spammers.

---

### Post by RobertKH on 2013-03-21
So how do I setup postfix? I've installed mdadm on my boot disk and skipped over the postfix stuff. So how do I change it now?

---

### Post by darkod on 2013-03-21
If you want to call up the task selector (roles selector) that appears during the install, you can always do it at the command line with:
sudo tasksel

But since you know exactly what you want to install, you can simply do:
sudo apt-get install postfix

That will install it with all dependent packages.
[https://help.ubuntu.com/12.04/serverguide/postfix.html](https://help.ubuntu.com/12.04/serverguide/postfix.html)

---

### Post by RobertKH on 2013-03-22
Well last night I installed Ubuntu 12.10 x64 on my hard drive that'll run it all. To ought I built my box and at least got the disks formatted. However I need to go pik up a better power supply. This one was loud. Took it apart to find the shrouds weren't even stuck to anything. I'll continue tomorrow night. The box is extremely tight. I found it easier to plug everything in with the power supply and motherboard removed. Made install quick and painless. I'll post some pics tomorrow.

---

### Post by RobertKH on 2013-03-23
Sorry, haven't had the chance to upload pics yet. However I am having a slight problem with the audio. I have an HDMI cable plugged in to my tv directly from my box. However i can watch the videos, but there is no sound. I have a disk from Gigabyte, however i have no CDROM drive attached. I did manage to rip the .iso off the cd and create a boot usb using unetbootin, however i cant seem to figure out which druve it is. Also its mostly windows .exe files that dont open on the U. Any ideas? Oh, btw I picked up a new power supply and its "whisper quiet". I can hardly tell its running. In fact my laptop makes more fan noise than the server.

---

### Post by darkod on 2013-03-23
Those disks are mainly targeted for windows, I wouldn't waste my time with them. But for reference, after plugging in a stick you can check all existing disks and partitions (including not mounted ones) with:
cat /proc/partitions

After knowing the partition of the stick you can mount it and use that mount point to copy or execute files.

Most audio works fine but if your isn't I would start by checking the chipset and then googling how to make it work on ubuntu. Usually the audio is PCI too and you can list all PCI / PCI-X devices with:
lspci

That gives modem, manufacturer, chipset (which sometimes has nothing to do with manufacturer name), etc.

PS. I might be wrong but isn't the HDMI only for video? Or it transfers audio too?

---

### Post by RobertKH on 2013-03-23
If I understand right, the HDMI cable is for both audio and video. Same sort if setup for my blu-ray player. One cord for audio and video. According to the gigabyte manual I need to enable audio out on some sort of bios setting that I can't find. The disk that came with the mobo says it has the audio drivers or whatever. I'll play with it tomorrow and see what I can do. I'll try listing the chipsets as you stated above. I've mounted the USB bootable drive, but I keep getting errors when it try's to run a .exe file. Something about archiver ran into a problem. Maybe I should try to open it with something else? Any ideas? Thanks for the help!

---

### Post by darkod on 2013-03-24
You can't run the .exe on linux, that's a windows program. You could only use the disk if it has linux drivers included which I doubt.

Enabling audio options in bios is another thing, check the manual of the board. It should be on the cd or you can find it on Gigabyte website.

---

### Post by RobertKH on 2013-03-24
Ok so I can't seem to get the audio to work. No big deal for right now. However I am having quite the issue with setting up mdadm raid1. When I created the array one drive disappeard, which I would expect, however it only lists one drive in the array. Is that normal? Currently I have deleted the array and will rebuild shortly. I do have a question about it. Do I have to have my boot drive on the array? Currently I have my boot drive on a smaller HDD (320gb) and I want to build the array from my 2 1TB drives that are attached. I was using the mdadm cheat sheet that I found here [http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/](http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/) however I seem to be running into a problem. I thought I read somewhere that I needed to create logical volumes first, but I can't seem to be able to find that in any of the mdadm tutorials. Does anyone have a good build link? The end result should be 1 array (probably /dev/md0) with the 2 1TB drives. 

I also have another question in relation to the array. Can i move my documents, video, and photo folders to be on the array? I assume that they have to stay on the drive with the /boot on it, but I am not really sure the limitations. 

Another problem I am having is sharing via FTP. I can access my drives from my Win7 laptop no problem, however I want to have complete access to all the folders and drives. I have run some RDP stuff, however with windows RDP i end up with the blank desktop unless I use vino, which is incredibly slow. 

Hopefully I can get this array stuff done then work on OpenVPN. 

Thanks for all the help here guys. I appreciate it.

---

### Post by darkod on 2013-03-24
mdadm SW raid arrays are assembled by the OS so there should be no disks disappearing. When you run fdisk or parted you should still see all disks, sda, sdb, sdc, etc a d on top of them you should also see the md0, md1, etc devices you have.

When you say /boot do you mean only a /boot partition or the whole / partition? Because there is a big difference.

Yes, you can put /home as separate partition/md device on the raid, but take into account that if you put files that are accessed regularly you won't be able to put the big disks to sleep. If they only hold data that is not accessed regularly, you can put them to sleep after inactivity of 15mins or 30mins or similar. It's up to you.

What is the exact purpose of sharing through FTP? You want to do it from outside the local network? For inside the local network you would simply use samba shares for access from windows machines.

To start with make sure no disks go missing. If it does, check the cables for loose connections, and SMART data for errors/failures of the disk itself.

---

### Post by RobertKH on 2013-03-24
When I say disappeared I mean from the dock. It still appears in gparted and disks utility. I would expect this to be normal behavior as in RAID1 it is simply a mirror and isn't directly written to. Am I correct? 

As far as FTP goes I would like to enable outside my network access, however it's mainly for my iPhone. I have created an FTP server from my Mac that allows file browsing and would like the same from my phone. That way if I need to move a file I can simply download it to my phone and head out. Does this make sense or would OpenVPN be a better solution?

---

### Post by RobertKH on 2013-03-24
As far as the /boot I don't mean moving the actual /boot as that will stay on my 320g 2.5" drive. I just mean moving those folders in the home directory for ease of organization. No big deal, I can simply make these same folder types in my raid array. 

Remember this is just a simple NAS for all the photos and videos of my kids and all our adventures. It doesn't need to be over complicated. Lol. Thanks for your support.

---

### Post by darkod on 2013-03-24
If you plan all of your family to have access, I wouldn't use your Photos, Videos, Music, etc folders inside your Home folder. They are limited only to your user.

I would create folders/shares on the data md device and use the data there. In that case you might as well leave root and Home within it on the small hdd.

Yeah, now that you have SW raid you use the /dev/md0 device, not the disks direclty. To be exact, you use the mount point where md0 is mounted, not even the md0 directly.

It shouldn't be a problem configuring FTP, but you definitely need secure FTP. Expect instant stealing of your data if you allow unsecure FTP access from the internet. You can find plenty of tutorials on google about secure ftp server. I believe most would use something like vsftp or proftp, etc.

---

### Post by RobertKH on 2013-03-24
Well I said I would post some photos, so here is a link to them. [https://plus.google.com/photos/103673259868295406008/albums/5859096037058982113](https://plus.google.com/photos/103673259868295406008/albums/5859096037058982113)
I am still working on the RAID. I'm also working on setting up the mail server to let me know if a drive is failing. This tutorial is helping... some ( [http://ubuntuforums.org/showthread.php?t=1185134](http://ubuntuforums.org/showthread.php?t=1185134) ). I also need to figure out how to set up my icloud account, but I think that I have gmail working via this link [http://www.jacmoe.dk/how-to-send-emails-with-msmtp-on-windows-or-linux-or-mac-os-x](http://www.jacmoe.dk/how-to-send-emails-with-msmtp-on-windows-or-linux-or-mac-os-x)
Darkod - I did install vsftp earlier, I just can't seem to figure it out. Any ideas of any tutorials for it?
Thanks again for all your help. I am progressing slowly but surely. It doesn't help that my wife is only 8 weeks away from giving birth to my second daughter. Things couldn't be too much more hectic around here lately.

---

### Post by RobertKH on 2013-03-24
Ok so here is the problem I am running into with creating my array. Maybe I just need to start from scratch, but I don't actually know how to do this. When I type in mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb2 I wind up with this problem

root@server-box:/home/server# mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdd1
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid0 devices=0 ctime=Wed Dec 31 19:00:00 1969
mdadm: partition table exists on /dev/sda1 but will be lost or
       meaningless after creating array
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid0 devices=0 ctime=Wed Dec 31 19:00:00 1969
mdadm: partition table exists on /dev/sdd1 but will be lost or
       meaningless after creating array
mdadm: size set to 976629568K
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

However now both of my 1TB drives have disappeard from the taskbar (or whatever it's called in Ubuntu)
Do I just have to put them back on manually? Did I really lose them and have to start over again? If it says that /dev/sdd1 is already in an array with 0 devices how can that be?

---

### Post by RobertKH on 2013-03-24
I also found this, but I am having a hard time figuring out what is important here...
[http://www.linuxsa.org.au/mailing-list/2003-07/1270.html](http://www.linuxsa.org.au/mailing-list/2003-07/1270.html)

---

### Post by RobertKH on 2013-03-24
Here is what happened after I created my /dev/md0 array
[ATTACH=CONFIG]240516[/ATTACH]

Note there should be 4 drives in my status bar on the left. After creating two of them disappeared. Is this normal? Is there a line I missed here?

Also I've read that the array won't automatically start back up after a reboot. How do I get it to do that? What's that command look like?

---

### Post by darkod on 2013-03-25
OK, lets go step by step.

1. Those /dev/mapper/... devices look like LVM. Do you want to keep it or destroy it? Or redo it again from scratch?
2. When creating mdadm array from partitions that were once members of another array, you have to destroy the superblock info so that it won't interfere. I think the --create command destroyed it, but you wouldn't get those errors and warnings.
3. What status bar on the right are you exactly talking about, where you expect to see 4 disks? In the Disks application you can see 4 separate disks, plus one external usb (it looks like that). How many physical disks and of which sizes do you have?

To see which arrays are present in the configuration you can look into /etc/mdadm/mdadm.conf. All ARRAY definitions there will assemble at boot. Now, whether an assembled array will mount automatically or not that is a question of /etc/fstab, not mdadm. But all of that is easy to do later, lets first figure out what do you expect to have in your configuration/system and are you getting that.

Because honestly I don't understand it much. You have a mix of mdadm raid and LVM which seem unrelated. You would usually use them in relation, if you want to use LVM at all.

For example, you create one or mode mdadm md devices to give you raid redundancy protection, and then you configure LVM on top of those md devices. They will serve as base, foundation, for the LVM.

In your case, they seem unrelated.

---

### Post by darkod on 2013-03-25
One more thing. The discussion got quite large and many things were mentioned. I think it's time to summarize what you actually want to do, in order to have a clearer path forward.

So, as mentioned in my previous post, it would be nice to specify how many disks you have and their sizes, and to tell us what you want to configure: like how many arrays, what raid level, number of disks, etc. That could help so we can provide exact commands.

The software like FTP, mail, etc, that's for later. Lets start with HW configuration first because I believe that part is not done yet too.

---

### Post by RobertKH on 2013-03-25
Ok so let's start with drives. Right now I have 2 WD Red 1TB drives that I want to have in a single RAID1 array. I haven't done anything with the LVM so I am not so sure how they became logical. I also have a 500gb WD green for extra storage of movies or whatever that I don't need redundant (mirrored). Attached through USB is my 1TB Seagate FreeAgent Desk external HD. I was planning on backing up the RAID array to this for a little extra security. So if we just move forward with my 2x 1TB WD Red drives that might be a little more precise. 

Let's start with what I have done based on what I wanted in mind. I have gone through already once and created this array. When I did that one of the drives on the dock disappeared, which looking back should have been normal. I could see /dev/md0 in the disks utility. Then I was thinking that something must have been wrong so I manually failed a drive in order to remove it. I went through this whole problem with /dev/md127 (which I found out in the disks utility)and finally figured out how to remove it. I also ran what I think was the zero superblock command. My array seemed to go away and after a restart I had both of my drives back. Then yesterday I started to rebuild the array and that is how we got to where we are... I think. 

When I say status bar I meant dock. I am not actually sure what you call it in Ubuntu, but on a Mac it's the dock. On the left... not the right. I think I might be a bit dyslexic. <-- But I spelled that right!

So currently I can see the /dev/md0 in the disks utitility, but I do not know how to mount it or even move files to it as I can't seem to find the place to do so. Does that make sense?

---

### Post by RobertKH on 2013-03-25
Oops forgot to mention the 320gb Seagate that my OS is running on. That is the 2.5" drive in the pictures.

---

### Post by darkod on 2013-03-25
OK, I would like to address the possible LVM first. Add the lvm2 package (you might already have it, so if you do just continue), and scan for Physical Volume (partition used in LVM):
```
sudo apt-get install lvm2
sudo pvscan
```

Let us know if it finds a PV or not.

Another thing is the mdadm raid. To see what you have right now, post the output of these commands:
```
cat /proc/mdstat
cat /etc/mdadm/mdadm.conf
df -h
```

That should help us for a start.

---

### Post by RobertKH on 2013-03-25
OK so running pvscan I get this
PV /dev/sdc5   VG ubuntu   lvm2 [297.85 GiB / 16.00 MiB free]
  Total: 1 [297.85 GiB] / in use: 1 [297.85 GiB] / in no VG: 0 [0   ]
server@server-box:~$ 

When I run the mdadm stats I get the following
server@server-box:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdd1[1] sda1[0]
      976629568 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
server@server-box:~$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays


# This file was auto-generated on Wed, 20 Mar 2013 23:47:41 -0400
# by mkconf $Id$
ARRAY /dev/md0 metadata=1.2 name=server-box:0 UUID=f89f6f39:5fba213b:8237f121:d8f1b86a
server@server-box:~$ df -h
df: `/root/.gvfs': Permission denied
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root  292G  6.4G  271G   3% /
udev                     1.8G   12K  1.8G   1% /dev
tmpfs                    715M  1.2M  714M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     1.8G  284K  1.8G   1% /run/shm
none                     100M   56K  100M   1% /run/user
/dev/sdc1                228M   54M  163M  25% /boot
/dev/sde1                932G  439G  493G  48% /media/server/1TB External
/dev/sdb1                466G  114G  352G  25% /media/server/B684-12A0





Does that help at all?

---

### Post by RobertKH on 2013-03-25
So here is my newest problem. I restarted my server and when I did so I ran into this /dev/md127 problem again. Why would it rename my array from md0 to md127?
 [ATTACH=CONFIG]240567[/ATTACH]

---

### Post by RobertKH on 2013-03-25
I found out how to restart my /dev/md0 raid although I don't want to have to run this every time.
server@server-box:~$ sudo mdadm --stop /dev/md127
mdadm: stopped /dev/md127
server@server-box:~$ sudo mdadm --assemble --scan
mdadm: /dev/md0 has been started with 2 drives.
so it changed back to /dev/md0 from the /md127 but I want it to boot that way. 

I know I am getting ahead of where we just were, however I needed to rebuild after that restart.

---

### Post by RobertKH on 2013-03-25
Ok so I think that I figured it out. I got it to rebuild the array correctly using the update initramfs. I also realized that I needed to format the disk in the Disks utility. After doing that it shows up on my dock and allows file transfer. I'm going to try to reboot and see what happens now.

**Update**
It works like a charm now. [CENTER][COLOR=#000000]\\:D/[/COLOR][/CENTER] Rebuilds the array correctly and is available on the dock as I suspected. Did I do this all right? Honestly this would have been way easier if I had just done this earlier [CENTER][COLOR=#000000]:oops:

[/COLOR][/CENTER]

---

### Post by darkod on 2013-03-26
OK, glad you got it working. Yes, you need to format the md0 device before it can be used. The assembled array is just a "blank" device, until you put a filesystem on it it's worthless. :)

For reference, you are running LVM on your 320GB disk. You OS is installed as LVM using the 320GB disk. Don't forget this when in future making changes.

The update-initramfs is needed after certain type of changes, you probably needed to do this since the array was not present at install. If you make an array during installation of the OS it knows about it and configured everything. If you add it later it you would need to update the initramfs.

Are you mounting md0 at a specific mount point, or only clicking on it in the Unity Launcher (the left side icon launcher)? You should make a mount point of your liking and then make an entry in /etc/fstab that will mount the md0 at boot evey time. If you don't do that, you will have to mount manually by clicking on it and often it uses the UUID as mount point which is not very user friendly to work with.

You can make something like /data for example with:
sudo mkdir /data

If you made ext4 filesystem on it, open fstab for editing with:
gksu gedit /etc/fstab

and add this lines at the end for example:
```
# my mount point for /dev/md0
/dev/md0   /data   ext4   defaults   0   2
```

That will mount it as /data on boot and you can use it in terminal or the Nautilus file browser as /data.

---

### Post by RobertKH on 2013-03-26
So my next step is to make /dev/md0 available via samba and FTP. Do I just have to create a folder? Or is there a way of sharing the entire drive?

---

### Post by darkod on 2013-03-26
That depends on whether you created a mount point as I sugegsted above, and how would you like to organize the data location and sharing. For example, if you mount md0 at /data, you might create few folders for organizing data:
/data/photos
/data/videos
/data/music
/data/personal
etc

After that you create samba shares, usually separate share for each folder. That way you can also control permissions and access.

If you share the whole /data for example, if you put a folder in it that only you want to access, it will be available to all users that have permissions for /data.

In linux on filesystem level you work with the mount points. Forget about drives any more, that's the physical device. So, you either share the mount point where md0 is, or the subfolders you created.

Post again the output of:
df -h

---

### Post by RobertKH on 2013-03-26
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root  292G  6.1G  271G   3% /
udev                     1.8G  4.0K  1.8G   1% /dev
tmpfs                    715M  1.2M  714M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     1.8G  288K  1.8G   1% /run/shm
none                     100M   64K  100M   1% /run/user
/dev/sdc1                228M   54M  163M  25% /boot
/dev/sde1                932G  439G  493G  48% /media/server/1TB External
/dev/md0                 931G  792M  931G   1% /media/server/RAID

---

### Post by RobertKH on 2013-03-26
Grrr I am still getting hung up on this sound thing. It's pretty irritating. I know I'm a step ahead but when something bothers me I can't stop until I get it fixed. Here is the page for the mobo that I have: [http://www.gigabyte.com/products/product-page.aspx?pid=4379#ov](http://www.gigabyte.com/products/product-page.aspx?pid=4379#ov) I can't seem to find the driver for the audio portion and I can't enable it through any settings. Any idea on this one darkod?

The website for the board has this:
[COLOR=#3D3D3D][FONT=Arial]1. Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=Arial]2. Most hardware/software vendors may no longer offer drivers to support Win9X/ME/2000/XP SP1/SP2. If drivers are available from the vendors, we will update them on the GIGABYTE website.

[/FONT][/COLOR] I can't seem to find anywhere that has these drivers for linux.

---

### Post by RobertKH on 2013-03-26
So I seem to be having a problem with mounting at boot. I actually went and changed the name to exactly like your example just to see if I could get it to work. HOWEVER the problem I think that I'm having is that I formatted my /dev/md0 as fat32 so when I copy in your text it looks like this now
Code:
# my mount point for /dev/md0
/dev/md0   /data   fat32   defaults   0   2

the only problem is that it says it doesn't recognize the file format. "Maybe you mean vsfat?" Or something of the like. Could the format be the problem? Can I use the ext4 with samba? Or is the Linux only designation only if I pulled the drive and tried to put it in another machine?

---

### Post by darkod on 2013-03-27
Oh man, why would you format md0 as FAT32??? It's inside a linux box, it will work just fine with linux filesystem. On top of that, you need linux filesystem to keep track of permissions and ownership. Of course you can use it with ext4, in fact it's recommended.

Apart from that, I think for fat32 the correct filesystem name to use is vfat. You can try with vfat but I strongly suggest reformatting md0 as ext4 before you have too much data on it.

And don't forget you need to create the folder /data if it doesn't exist right now. You only do that once.

---

### Post by RobertKH on 2013-03-27
Ok ok ok... I did reformat /dev/md0 last night as ext4. However do I need to reformat each individual drive that way as well? I formatted almost all of them as fat32 only because I thought... nevermind that part. I was being a dummy. I created a folder but didn't call it /data its more like /raid is that ok? I wouldn't think it matters what it's called just that i create a point to mount. 

Another question. Can i add a line to mount my 500gb as well? something like 
[COLOR=#000000]# my mount point for /dev/sdc[/COLOR]
[COLOR=#000000]/dev/sdc /data ext4 defaults 0 2

Almost exactly like mounting my raid device only for the other HDD that is on my box?[/COLOR]

---

### Post by darkod on 2013-03-27
1. No, you don't format the physical disks. They are part of mdadm and that's it, you don't manipulate the disks directly. You are working with /dev/md0 from now on.

2. Yes, you can use any mount point (folder) you wish, as long as you create it first and as long as the name doesn't clash with some existing system folder. /raid will work just fine. Only don't forget that in that case the line you need to add to fstab will be like:
```
/dev/md0   /raid   ext4   defaults   0   2
```

3. Yes, you can do the same for the 500GB disk. But you need to mount the partition, like sdc1, not /dev/sdc. If the partition is also formatted as ext4, it would be like:
```
/dev/sdc1   /mount-point   ext4   defaults   0   2
```

---

### Post by RobertKH on 2013-03-27
Sounds good. I'll give it a shot as soon as I get home from work. Thanks for your help darkod

---

### Post by RobertKH on 2013-03-27
Should it take this long to boot normally? It has been about 10-15 minutes waiting for it to boot after I modified the /etc/fstab

---

### Post by RobertKH on 2013-03-28
I screwed something up. Lol. I went ahead before reading not to try to format a drive, but only the array. I went through and deleted the array and even removed mdadm however now I have some lost and found files that I can't even get rid of with nautilus. Any ideas? I was able to rebuild the array, but still have that folder on the drive. How can I get rid of it?

---

### Post by darkod on 2013-03-28
I think that is just a folder created on any partition. Since you made ext4 partition, it shows it now.

Since you are making the raid all over, I suggest to remake the partitions you formatted. Just make them with parted at the command line because parted only creates partitions, not a filesystem. Or if you are using Gparted for the GUI, I assume you need to create the partition as RAW or something similar. I've never tried to create a partition without a format in Gparted, I use parted mainly since it does that by default.

After you have the partitions without any filesystem again, make a new array.

---

### Post by RobertKH on 2013-03-28
By raw do you mean unallocated? I formatted both drives with new partitions, but for some reason I kept getting an error on /dev/sda1 but not on /dev/sdd1. I'll post some screenshots later when I get home. For now, can you tell me how to erase and create a partition using cli? I don't know how to do that, only through the GUI. thanks

---

### Post by RobertKH on 2013-03-28
I also keep getting an error when running gparted. "Could not stat /dev/md/0" I have no idea what that is supposed to mean.

---

### Post by darkod on 2013-03-28
No, by RAW I mean creating a partition but without any filesystem on it. In Gparted when you create a partition and select the Use As to be ext4, it creates it as ext4 directly. There should be option to create a partition but now a filesystem.

Unallocated space is usually space that doesn't belong to any partition, it's not the same. For mdadm you actually need a partition, but no filesystem on it.

The basic commands to use parted in CLI are:
Open a disk with parted:
sudo parted /dev/sda

Once oyu are in the parted> prompt, to print table:
print

To delete partition:
rm <number>

To create partition:
mkpart primary/logical <start> <end> (for msdos partitions, the start/end depend on the unit type set)
mkpart <label> <start> <end> (for gpt partitions, you must enter a label, and gpt partition do not have difference between primary/logical)

To set unit size:
unit <unit> (for example I most commonly use MiB which is MibiByte 1 MiB = 1024 KiB, while 1 MB = 1000 KB)

To write new blank msdos or gpt table:
mklabel msdos/gpt

To set a flag on or off:
set <partition-number> <flag-name> on/off (for example, set 2 raid on)

To exit the parted prompt:
quit

be very careful with parted, since the changes are done immediately. It's not like Gparted that waits until you hit the green button. Gparted is actually just a GUI front of parted.

The mkpart command makes only partitions, no filesystem, which is very useful when you want to create a partition for raid without any filesystem. The unit command is also useful since it allows you to work with exact units, and set the start/end points of a partition exactly as you want.

To format a partition/array later in CLI with ext4 for example, you could use something like:
sudo mkfs.ext4 /dev/sda1
sudo mkfs.ext4 /dev/md0
etc

---

### Post by RobertKH on 2013-03-28
Thanks for the quick reply. This will be super useful. I'll try it as soon as I get home.

---

### Post by darkod on 2013-03-28
> **RobertKH said:**
> I also keep getting an error when running gparted. "Could not stat /dev/md/0" I have no idea what that is supposed to mean.

It looks like it's trying to read md0 but it can't, maybe because you deleted the partitions. Did you stop the array before that? Don't forget, now that you have an array running, to manipulate the underlying partitions you better stop it first:
sudo mdadm --stop /dev/md0

But with deleting the partitions the info about md0 is gone, there might be traces left in mdadm though. There was a command in mdadm to delete an array I think. You can look for it. The cat /proc/mdstat will tell you the current mdadm status.

---

### Post by darkod on 2013-03-28
One more thing, the print command in parted lists the filesystems on all partitions when it outputs the list. If you are after a partition with no filesystem, after you create it the printed list should have no filesystem specified in the Filesystem column. That's how you know if it has a filesystem or not on it.

---

### Post by RobertKH on 2013-03-28
Did all that. For some reason it seems to still be hanging. I also even went as far as to remove mdadm completely and then reinstall after formatting the drives in hopes of removing the lost and found as well as the hook with mdadm.conf, but no such luck. 

And just to clarify I think I know what that lost and found is. I had moved a single folder over to test out the array. It was about 14gb but didn't think anything of it when I tried to simply reformat the drive. Stupid me, I am used to windows and it automatically deleting all data on the disk. Not Linux running fsdks ( I think that's what keeps catching it) and putting that data back on the drive. However I have no idea how to delete it. I read that the best way is to enter nautilus sudo gksu nautilus and head over to the drive and delete it. When I do that the file goes away, however as soon as I reformat it comes right back. Does this make a little more sense? I really just wanted to completely wipe the drive and start over. I am half tempted to just reload 12.10 on my OS disk and erase everything that is on it right now.

---

### Post by darkod on 2013-03-28
The mklabel msdos command in parted will write a new blank table. Is this folder shown on the physical disk or the md0 array?

If you write new tables on both sda and sdd, then create new partitions for the raid as before but using parted if possible. That will make sure the partitions are created clean and with no filesystem.

After that create a new md0 device, and format it as ext4. At this point there should be no files left from before, but note that the lost+found folder might show up, I'm not sure if it's equivalent to the recycle bin in windows.

---

### Post by RobertKH on 2013-03-28
It is shown on the physical disk. I don't think it's shown on the array. So if I create new blank partitions on each disk individually and then format them after creating my array I should be all set?

---

### Post by darkod on 2013-03-28
Yeah, new clean table doesn't keep any old partition info or files. I don't see a way for a file to remain on it.

To clarify, when you say "format them". You don't format the partitions directly. You create md0 from sda1 and sdd1 for example, and then you format md0. Once you create md0 you work only with that (format, mount, etc), you forget that sda1 and sdd1 exist. mdadm is taking care to mirror the data using the physical partitions, you are working with md0. Never with the partitions directly.

So, it should be "format it" (one array), not "format them".

---

### Post by RobertKH on 2013-03-28
So should I jot format them at all prior to building my array? Maybe this was the problem before?

---

### Post by RobertKH on 2013-03-28
The problem I have is that even after I have stopped the array it won't allow me to remove it. Looking at /etc/mdadm/mdadm.conf I still see /dev/md0 listed. When I try to remove it, even as su, I get 
mdadm: error opening /dev/md0: No such file or directory
Like I said when I look at /etc/mdadm/mdadm.conf I see the following
# definitions of existing MD arrays


# This file was auto-generated on Wed, 20 Mar 2013 23:47:41 -0400
# by mkconf $Id$


ARRAY /dev/md0 metadata=1.2 name=server-box:0 UUID=752814a3:f149d489:b65e90e1:c3d69a72

I can't seem to get this drive to be removed. Or am I doing something wrong?
I have stopped the array, opened gparted (for the GUI because it's a little easier for me right now) and then created an unformatted partition on both the drives. There shouldn't be anything hooking to it. I even re-ran initramfs last night and it doesn't seem to get it to go away.

---

### Post by darkod on 2013-03-28
Don't worry about that raid definition. Put a # at the front of the line, and it will be ignored. Anything with a # in front is considered as comment only. Save and close the file.

When you have the new md0 running you will automatically add it to mdadm.conf with:
```
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

That will write all detected arrays, in this case the new md0.

---

### Post by RobertKH on 2013-03-28
So the problem that I seem to be having after re-creating my array is that I cannot seem to get it to mount at boot. It keeps telling me that the drive is not ready or present and to press either s to skip or m to manually fix. Should I be waiting all that long for it to be ready? I don't really think that these WD Red drives are a slouch, but could they really be taking that long to spin up? Or am I missing something? I ran: sudo update-initramfs as well as: sudo mdadm --detail --scan >>/etc/mdadm/mdadm.conf is there something else to do here? I copied the text for creating a mount point from your post and simply pasted it in and modified it to my liking by changing what I had called the mount points (/storage and /500gb respectivly) but they still don't seem to be mounting. Any ideas?

---

### Post by RobertKH on 2013-03-29
[SIZE=3][SIZE=2]Ok so now I am wicked confused here. I was reading through and some people said that you should use the UUID instead of the /dev/md0 so I tried that with the 500gb i wanted to mount as well as the array that I wanted to mount. I got the whole drive is not ready or present at boot for the array, but the 500gb mounted just fine.[/SIZE] [CENTER][COLOR=#000000]](*,)  What am I doing wrong here? No matter what I try I can't seem to get the array to mount at boot. Now keep in mind if this thing is going to be on 24/7 I suppose it wouldn't be that much trouble to just open up Disks and mount it from there as that works just fine, 
but I would like it to mount without any input from me just in case I am away and my wife needs to mount the drive.

On a side note it sucks that we have this giant time difference between Spain and the East Coast. Every time I am home and working on this you are probably not awake and no one else seems to want to comment on this thread. Thanks again for your continued support 
[/COLOR][/CENTER][/SIZE]

---

### Post by RobertKH on 2013-03-29
I lied. I just tried to mount the raid array manually and got the following error:
Error mounting /dev/md0 at /media/server/Raid: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/md0" "/media/server/Raid"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


 (udisks-error-quark, 0)

No idea why.... so I will go edit fstab and change it back to /dev/mdo but leave the 500gb alone.

Edit: that didn't work either. When I ran the dmesg i got the following at the bottom (don't know what it means)
[ 1022.155933] EXT4-fs (md0): no journal found
[ 1167.367856] EXT4-fs (md0): no journal found



last edit for the night I promise: I ran the sudo cat /proc/mdstat and it said it was only 32% done with resync. Does that matter? I am currently watching it with: sudo watch cat /proc/mdstat to see how long this will take. I'll try one more time then I'm going to bed. This seems to be taking me way to long.

---

### Post by darkod on 2013-03-29
I'm not sure if you can start working with it before it's completely synced, but I would let it finish the sync first.

After that, try reformatting it as ext4, it seems it has some issues with the filesystem. I assume there is still no data on it since it's a new array now, so formatting should be OK. Even the manual mount you tried mentioned "bad fs type, bad option or bad superblock".

So, after the sync of /dev/md0 is 100% done, try:
```
sudo mkfs.ext4 /dev/md0
```

That will change the UUID (an UUID is assigned on formatting), so if you want to keep using UUID in fstab you will have to edit it and put the new one in. Also, if using UUID with mdadm remember that the physical partitions still have different unique UUIDs, and /dev/md0 has a different one. You need to use the UUID of /dev/md0 since that's what you are mounting.

Double check the entry in fstan anyway, make sure there are no typing errors, etc:
```
/dev/md0   /mount   ext4   defaults   0   2
```

It worked for you last time, right? You must be doing something wrong now. You say that even the 500GB disk doesn't want to mount with fstab which has nothing to do with mdadm, just with the entry you are putting in fstab.

---

### Post by confusedstingray on 2013-03-29
> **lykwydchykyn said:**
> You can set up anything on Ubuntu desktop that you can set up on the server.  Unlike Windows, there's no fundamental difference between server and desktop editions, it's just a question of default packages and configurations.  They both pull from the same repositories and use the same set of packages.

Sending an email means setting up an MTA; I prefer postfix myself.  You'll need to have an SMTP server you can relay off of to send email outside your own network.  You will need to talk to your ISP about that, I don't think most ISPs let you relay because of spammers.

here is a link that might help [http://www.postfix.org/BASIC_CONFIGURATION_README.html](http://www.postfix.org/BASIC_CONFIGURATION_README.html)

---

### Post by RobertKH on 2013-03-29
Ok so I just got it to mount after reformatting it as you said darkod. Now I am going to restart and see if I can get it to mount at startup. 

One other thing. Why is it that I can't seem to make folders in those drives that I automatically mounted? I don't think that part is the issue, but for some reason it wouldn't let me create folders there unless I was SU. Is that normal? Do I have to launch in nautilus in order to make any modifications to folders? Remember this is for photo and other media storage, so I will probably have folders full of specific dated items within it. I want to be able to create quickly. Although I can do all this through RDP so it doesn't matter that much right now.

---

### Post by darkod on 2013-03-29
By default you create the mount point as root (using the sudo prefix) so it's owned by root and no other users are given permissions by default.

You can always change permissions later, it depends what type of permissions you want. For example, to give RW access to all users, including any existing subfolders, you would do:
```
sudo chmod -R a+rw /mount
```

That gives RW to all, and using the -R makes it recursive to include all subfolders. After you execute that, any users should be able to use all data, including making folders, etc.

If you want specific access for some users to some folders, you need to plan the folder structure and specify the permissions correctly. Linux is very strict with permissions, that's part of why it's safe. Unless you give people access, it will be denied.

On samba shares you have also permissions as specified in the share definition, which can allow or deny access. You can give access to certain shares to certain users only, using the share definition.

---

### Post by RobertKH on 2013-03-29
Success! Server is working like a champ as of this morning. Thanks for all your help. Now on to trying to set up postfix or something simliar in order to let me know if a drive is failing. I also need to figure out if I want to use OpenVPN or not. Any chance you have any experience with it darkod? You've been quite the help in setting this up so far. I do have a question on OpenVPN. I understand VPN services, however normally they are only to relay your information request to a website and then return the results. It serves as a middle man alone. However as I understand OpenVPN I can access my computer like a remote desktop. Is that the case here or was someone just blowing smoke up... you get it. Any ideas?

---

### Post by darkod on 2013-03-30
No, I don't have experience with OpenVPN directly. VPN is like a "middle man" but in a way that it serves to create a secure connection to the remote network. Once you are connected, it's the same as if you are inside that remote network. You can open network shares, applications, remote desktop connections, websites that are not accessible over the internet, etc. If a website for example is accessible over internet, you don't need VPN to access it, right?

So, yes, with VPN connection you should be able to easily open a remote desktop connection to any computer in the remote network that has remote connection enabled.

---

### Post by RobertKH on 2013-04-02
Truly I am astonished that I got this all working. Thanks again for all your help darkod. Do you mind if I use some of your instructions in my blog to document my progress? I want to write up something that will help other future home server builders to get their Ubuntu machine working. The only think that I have left to do is the VPN thing, some sort of email notifications and some sort of media server so that my blu-ray can find the files. I will mark this thread as solved as you have done an excellent job of helping me out and I feel that everything from here can go to another thread.

---

### Post by darkod on 2013-04-02
Yeah, feel free to use the instructions.

For media server I have Twonky but that is because I already had paid the license. There is an open source program called MiniDLNA if I'm not mistaken which should work with any DLNA enabled device. As second choice the Twonky license is not expensive either.

---

### Post by spynappels on 2013-04-02
Hi Robert,

You mentioned way back that you were often away on business, and running an OpenVPN server may help you in several ways.

Firstly, it will allow you to access other nodes on your home network when away, this can be extremely useful when something has gone wrong and you need to fix it (voice of experience speaking here...). I also found it very helpful for communicating with my family when I was away from home as I was running a VoIP PBX at home and using a Softphone on my laptop connecting to my PBX, I could call any phone in my home for free, no matter where I was.

Secondly, it may help you maintain security while you are away. You can set up your VPN to carry all traffic from your remote workstation and relay it through your home ISP. This can be useful for accessing services which are locked to geographical areas when you're away, but it's potentially most important use is encrypting all traffic from your laptop to your home network. This would make it much more secure to transmit information when you are in a location where the security of the network cannot be guaranteed, such as public Wi-Fi hotspots, hotel internet access etc. I'd never do some things like internet banking unless I was VPN'd to a known secure network, or using a SSH tunnel.

Setting up OpenVPN is not particularly difficult either, but if you have some specific questions, please don't hesitate to ask.

Regards,
Stefan

---

### Post by RobertKH on 2013-04-03
Minidlna did the trick! I can now stream my media to my blu-ray player. Thanks for the tip. However I have some converting to do with mkv files downloaded from XBMC. Apparently they aren't supported. 

As far as openvpn I am still trying to figure it out, but rest assured I will get it. Any chance you could email me your configuration Stefan? Feel free to X out the important stuff.

---

### Post by RobertKH on 2013-04-05
So I have a question on expanding my drives (already). If i am running RAID1 on my 2 1TB drives and I wanted to add another 2TB drive to the array, would that work? I understand the commands and all that, but would my system know enough to take one of the 1TB (the mirror) and then move all the data to the 2TB? Or would I have to set up 2 seperate partitions on the 2TB drive in order to set it up that way? Does this make sense?

---

### Post by darkod on 2013-04-05
If you simply add it to the existing raid1 array, you don't gain anything, except a third disk on top of the two already there.

What is the idea of adding the 2TB disk, what do you want to end up with?

Making raid from disks with different sizes is tricky, it depends what you want to achieve.

If you want to end up with 2TB of usable space instead of the 1TB you have now, the only way I see that is making a 2TB raid0 device from the two 1TB disks first, then use that raid device as physical partition for raid, and make a raid1 device with it and the 2TB disk.

But you will have to move the data first since making the new raid0 array will destroy all data on it.

---

### Post by RobertKH on 2013-04-07
So I am having a problem setting up OpenVPN. I can't seem to copy the .crt file or the .key file anywhere. I tried to copy it to a local storage so I can move it over my network, but that didnt work. I then tried to copy it to some sort of a thumb drive but that didn't work either. Any ideas here? I keep getting permission denied no matter where I try to copy it.

---

### Post by RobertKH on 2013-04-07
Darkod, I think that I will just say screw it and leave the setup as it is. I will be adding a 320gb to the box itself just for my itunes media as I made both of my pc's share the .itl file. I didn't really want to have to mess with raids over raids. Doesn't really sound like that much fun to me. Thanks for pointing that out.

---

### Post by darkod on 2013-04-08
For copying the keys I suppose you need sudo rights. If you are doing it in terminal put sudo in front of the command.

If you want to do it in the Nautilus GUI don't open it the standard way, open it from terminal with:
```
gksu nautilus
```

That will open it with sudo rights and you should be able to copy where you want it. Remember, in linux almost all system files/operations are protected. That's what makes it extremely secure. :)

---

### Post by RobertKH on 2013-04-08
Nautilus was still telling me that I didn't have permissions....odd. However I got it to work using:
sudo cp /etc/openvpn/server.key /500gb/openvpn stuff 
Seemed to work just fine. The only problem that I've run into now is on the windows side of things. Well, windows and iOS. I think I need to do my windows pc before I can do the iOS. Openvpn says that in order to get the phone to connect I need a .opvn file but I can really figure out how to do that. I'll do some more testing tonight, but if anyone has any ideas.....

---

### Post by RobertKH on 2013-04-08
So I just bought a SSD to run my OS on. However I can't seem to find a good tutorial on how to do so. Any ideas? I know I can't use dd because you have to have equal drive sizes whereas I am moving from a 320 down to a 120 ssd just for boot and response speeds. I am freshly installing ubuntu 12.10 on it right now, however I am not sure if I have copied all the right files here. I will be moving things around in a minute and post on the outcome. 

I did copy my fstab file, my mdadm file and quite a few other random config files in order to try and retain what I have so far. I just need to run the initramfs. Wish me luck.

---

### Post by RobertKH on 2013-04-09
Crap... that didn't work as planned. I did copy over my config files however after installing the SSD and unplugging the original boot drive it keeps hanging on boot and then tells me that /boot is unavailable or something like that. I did an update to initramfs, but what am I missing? I also am having a problem with samba. I copied my config file, however it won't let me share any of the already shared drives unless I run nautilus or something. I changed the owner to my username while in nautilus rather than root, but that didn't seem to help. I'm going to bed and I'll give it a shot tomorrow.

---

### Post by darkod on 2013-04-09
You seem quite bored these days, aren't you? You can't seem to settle down. :)

Lets see. If you installed 12.10 clean on the ssd there should be no issue booting it at least. You can deal with the config files, samba, etc, later, first thing is that it boots fine.

Depending how you instaleld it, all should be on the ssd, i don't get it why would it look for /boot on the other disk. What can happen is if the bootloader is on the other disk so it can't boot without it, but that is easily solved.

Can you boot into live mode and post the /etc/fstab from the ssd?
 
Also, did you already add the array to the new OS or not yet? Be careful, don't --create it again, that will destroy the data. Never run mdadm --create on existing array if you want to keep the data.

And don't rush in changing ownership and permissions, I don't think it has something to do with that.

---

### Post by RobertKH on 2013-04-09
You are right, never a dull moment in my life. 

The clean install not only boots, but will mount my array as well as my 500gb. However for some reason it hangs when I am booting unless it keep the drives unplugged. Luckily they are just on trays so it makes it easier. I will copy the fstab here later tonight when I get home. I did rush in and change ownership to server rather than root already, however that still didn't fix it so maybe we can figure something else out.

Wait... when you say in Live mode, should I be doing it from the install disk or stick? Or just on the server itself?

---

### Post by darkod on 2013-04-09
I thought it doesn't boot at all, so the only option would have been live mode (from cd or usb, doesn't make a difference).

But since it boots (with tricks), boot it and simply post the content. It might be beficial to post the UUIDs at the same time:
```
sudo blkid
```

---

### Post by RobertKH on 2013-04-09
Will do. One quick question. It was much easier to install the OS on the SSD if I had it in my laptop. Should I not have done that? I don't really have a problem with unplugging all the drives and leaving only the ssd plugged in. Then I can just copy those .conf files and paste them in the appropriate places. Would that be a better idea?

---

### Post by darkod on 2013-04-09
Hmm, not sure. There will be some difference in drivers, but it should be OK now that the ssd is inside the server. However, I'm not sure whether during the install process activates some drivers and later doesn't do it when moved to another machine. I always install with the hardware it's supposed to work with, so I don't have much experience with installing into another machine then moving the disk.

I don't get the idea of unplugging the other drives but then copying config files. Yes, you can copy most config files and it should work provided the setup is identical (mount points, arrays, etc). What do you mean not having a problem unplugging all drives? You mean only so that it can boot? Otherwise where is your data if you can leave the drives unplugged?

---

### Post by RobertKH on 2013-04-09
No I meant only for boot. Until it tells me that the disks aren't ready. I did copy the config files onto a usb stick so I could just paste them into place and change the name on the originals. Maybe I'll just redo it tonight and paste them back in. However it does work right now so why screw with it?

---

### Post by darkod on 2013-04-09
Don't redo it, no problem. But you have to find out what prevents it booting, probably something in fstab. Because depending on the current setup, some changes might be needed in the config files too.

---

### Post by RobertKH on 2013-04-09
So here is sudo blkid
/dev/sda1: UUID="97367b29-515d-4a46-85c6-48372b077e7c" TYPE="ext4" 
/dev/sda5: UUID="ec663f69-e79e-412a-9fd0-466d70856b35" TYPE="swap" 
/dev/sdb1: UUID="699fb6a2-2156-4cad-944d-f90539f04398" TYPE="ext4" 
/dev/sdc1: UUID="752814a3-f149-d489-b65e-90e1c3d69a72" UUID_SUB="a31f9fa1-1ab3-149e-c11a-b5817e11f331" LABEL="server-box:0" TYPE="linux_raid_member" 
/dev/sdd1: UUID="752814a3-f149-d489-b65e-90e1c3d69a72" UUID_SUB="dfadd2c0-ed56-3862-4140-2877021686d1" LABEL="server-box:0" TYPE="linux_raid_member" 
/dev/md0: UUID="8ebf67b5-19b1-4790-b012-24e5dde24030" TYPE="ext4" 
/dev/sde1: LABEL="1TB External" UUID="A08EF6D68EF6A3C6" TYPE="ntfs" 

Obviously sda1 is my boot drive. I still don't have my original boot drive on there. I am going to go back and look at the fstab and see if it lists the UUID. If so then I will change it to match my new boot drive.
 
(Had to change it. It still was calling out the previous drive. Let's see how it works at boot now. Wish me luck)

I also read somewhere that I need to enable TRIM. Does anyone know anything about that?

---

### Post by RobertKH on 2013-04-09
BOOM worked like a champ. Booted without any sort of hangups and at least twice as fast as the 5400rpm drive. Love it. Good call on checking the UUID's. So now I will go on and try to enable the TRIM and see if it improves at all. I think it just has to do with writes but I am not sure.

---

### Post by RobertKH on 2013-04-09
The problem I am having with my samba share is the following message:
'net usershare' returned error 255: net usershare add: failed to add share randoms. Error was Operation not permitted
No idea what that is supposed to mean. Any ideas?

---

### Post by RobertKH on 2013-04-09
Ok so I said screw it and just deleted the entire partition on my original OS and set it up for another 320gb raid device matched with another 320gb. So now I have to go back and look to figure out how I got my smb to work. Not really looking forward to this at all....

---

### Post by darkod on 2013-04-10
There might be some difference in the OS so it can't work with the old smb.conf if you had it copied.

Since the samba setup was not too complicated (too many options), you can try setting it up from scratch, with new empty smb.conf. Just add the options you need.

Also, it could have something to do with the changed ownership. It's still changed, right?

What exactly did you change, the ownership of which folder to what?

---

### Post by RobertKH on 2013-04-10
Output of my original samba file. I don't remember what it was that I changed. I still cannot share my folders by right clicking and selecting share. For some reason it is not allowing it. I get that user 255 error. 
```
## Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#


#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).
   max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user


# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam


   obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user


########## Domains ###########


# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g


########## Printing ##########


# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes


# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap


# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY


# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &


# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes


# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom



```

---

### Post by RobertKH on 2013-04-10
What's odd is that this was copied from my other drive and for some reason it worked then. Doesn't that seem odd? I don't even think that I ever changed a single thing on it and I was able to share....

---

### Post by darkod on 2013-04-10
This is what happens when you want to work only in the GUI. :) When you said right-click now, it hit me.

That smb.conf file looks like the default one to me. You never changed it, you never created the samba shares like that, you only used right-click in Nautilus. I don't know how things work in that case.

Even if you are using the Desktop OS for a server, it's not difficult to use the terminal for some tasks, and often it's much better option.

I'm not sure what to do now, you can keep trying with the GUI if you want to.

In your place, I would confirm first the array is mounted and the mount point (folder). After you reinstalled the OS did you make the same folder and used it as mount point for the array? Do you have an entry in fstab for it?

After you post where you mount the data array, and explain what type of shares you want to make, we can help with the modifications you need in smb.conf.

Lets go step by step, explain the mounting of the data array first.

---

### Post by RobertKH on 2013-04-10
Mount point is the same. I copied over the mdadm config file and that works like a champ. Mounts every time at boot. There is an entry in fstab as well for all of it. I had to go and change the UUID of my boot drive as I had stated previously. One question on that. With a SSD what should my boot line look like? Should I be adding the noatime to it? for example UUID="xxxxxxxxxxxxxxxxxxxxxxxxxxx" /boot  noatime,remount=xxxxxxxxxxxxxxxxxxx or whatever it looks like?

---

### Post by darkod on 2013-04-10
Yeah, I think for ssd it's better to add 'discard,noatime'. The discard does the TRIM function. Just make sure you append it to the existing option and you DO NOT leave a space between them.

Remind me then, what is the array mount point, and explain little bit what type of access you want.

1. Only one single share?
2. Open RW access to all, or different users with different rights?

---

### Post by RobertKH on 2013-04-10
the mount point for the array is at /storage and the mount point for my 500gb drive is /500gb. I really want to open up RW to just about everyone on my network. 

So you mean to add discard,noatime to just before remount without any spaces? I can do that.

---

### Post by darkod on 2013-04-10
OK. First to give RW access to all for those folders (mount points), you need to do in terminal:
```
sudo chmod a+rw /storage
sudo chmod a+rw /500gb
```

After that make a backup of the original smb.conf file:
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.original
```

After that in terminal open a new blank smb.conf file and start entering the text in the attached image (see note below about the file content):
```
sudo nano /etc/samba/smb.conf
```

When you are done save the file with Ctrl+O and exit nano with Ctrl+X.

Restart samba (or the whole server):
```
sudo service samba restart
```

After that you should see the shares you set up.

NOTE about the file content, and attached image: The attached image is an example from my home server. The [global] section has the workgroup name (that all windows machines belong to, although this is not necessary for the shares to work correctly). It has the machine name and also the allowed range of hosts. Only hosts from this range will be allowed to use the shares (you can drop this line if you want to). The option security = share is important since it allows open access.

The share definition you can call what you want instead of [network], this is how it will show to the clients (the share name). You don't need the comment option if you don't want to, and make sure the path is correct for both shares you specify, in your case /storage and /500gb. You will create two separate share definitions each with the correct path.
The options guest ok and read only are also important since they help with open access, so make sure you leave them as they are.

After doing this and restarting samba, you should be able to see the shares from any machine and read-write to them.

---

### Post by RobertKH on 2013-04-10
Ok. I can skip the samba config file as I already have one that is named .original, but I will try the rest when I get home tonight.

---

### Post by RobertKH on 2013-04-10
Ok so those settings go near where the printers are right? So it looks like this
```

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


[network]
	path = /storage
	guest ok = yes
	read only  = no	


[network]
	path = /500gb
	guest ok = yes
	read only  = no	

```

---

### Post by darkod on 2013-04-10
Anywhere you want, put them at the end for better overview. But I thought you will create new empty file, that way there is no bunch of text that's not used.

You can create new empty smb.conf and put only those lines in.

---

### Post by RobertKH on 2013-04-10
Didn't work. I can't see my shared drives from my laptop nor my wife's on windows 8.

---

### Post by RobertKH on 2013-04-10
grrrr this is so irritating. I can't even share it by right clicking them. I ran the chmod but it didn't seem to do anything

---

### Post by RobertKH on 2013-04-10
So I know this is more than you really need to see, however this is what I did.
```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#


#======================= Global Settings =======================




## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).
   max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user


# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam


   obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user


########## Domains ###########


# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g


########## Printing ##########


# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes


# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap


# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY


# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &


# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


[network]
	path = /storage
	guest ok = yes
	read only  = no	


[network]
	path = /500gb
	guest ok = yes
	read only  = no	


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes


# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom




```

Now what the heck did I do wrong? I restarted the server, but maybe that didn't manage to re-read the smb.conf file? I am clue less here.

---

### Post by RobertKH on 2013-04-10
I think that is because mostly I keep getting this every time I try to restart samba
root@server-box:/home/server# sudo service samba restart
samba: unrecognized service

Why is that? I know I have samba installed....

---

### Post by darkod on 2013-04-10
My mistake, the daemon (service) might have been smbd, not samba.
sudo service smbd restart

As for your smb.conf, you named both shares [network]. I said to name them as you wish, different names. Not sure if it can work with same names for two shares. Just make them [raid] and [disk] or whatever.

Again, I suggest you delete you smb.conf file and make a new small one, only with the [global] section I posted and your two shares. The default smb.conf includes some options that could be messing it up for you. Like read-only access to shares, which is not what we want. You can see in the Shares Definitions section it mentions for security it will set read-only access to shares by default.

By removing all from smb.conf and putting only what you need, you make it small, easily viewable, and most important you avoid having some option that you don't want.

---

### Post by RobertKH on 2013-04-10
Ok. Let me try that.

---

### Post by RobertKH on 2013-04-10
Ok this still isn't working for me. This is my entire smb.conf file
```

[global]
	workgroupd = WORKGROUP
	netbios name = server-box
	security = share


[RAID]
	path = /storage
	guest ok = yes
	read only = no


[500gb]
	path = /500gb
	guest ok = yes
	read only = no

```

again, what can I be missing?

---

### Post by RobertKH on 2013-04-10
So let me just tell you what I just did and maybe you can help me out a little. I followed this post here (the last post): [http://ubuntuforums.org/archive/index.php/t-770643.html](http://ubuntuforums.org/archive/index.php/t-770643.html)
just to see if it would fix it. I was, after running through it and rebooting, allowed to share via the right click method. However I didn't do it for all my folders or a single drive. I just wanted to see if it would work. I then went and created a brand new folder, with nothing in it and tried to share that... that didn't show up on my windows machine either. I know there has to be something simple... but I can't seem to figure it out.
Even with nautilus permissions I am allowed to share the folders, but nothing shows up on my windows machine. Is something not right on my windows machine? I don't quite understand here as I haven't done anything out of the ordinary here...

---

### Post by CharlesA on 2013-04-10
How are you accessing the shares from the windows machine?

Last I checked samba shared and nautilus shares conflicted with each other, so you need to pick one or the other if you are going to be sharing files with a Windows machine.

You can find a decent tutorial on how set setup Samba classic in standalone mode here:
[http://charlesa.net/tutorials/ubuntu/samba3-ubuntu.php](http://charlesa.net/tutorials/ubuntu/samba3-ubuntu.php)

---

### Post by RobertKH on 2013-04-10
I am accessing them through the network tab on my home drive. The only reason why I have been trying both is that neither will work in any way. I looked through your tutorial and nothing that I have is any different than what you have suggested. If you read back through my previous posts (bear with me as there are many) I have tried multiple things since switching from a conventional 320gb seagate drive that had my OS on it, to a fresh install on my Kingston 120gb SSD. This has helped on my server a bit, as well as almost all of my other config files work great. My arrays build just fine, all my drives mount at boot just fine. My minidlna even shows up and shares those files. However I need to be able to see more than just photos and videos and I would also like to control them from my windows machine. I have tried as darkod has suggested with the chmod and all that, however it doesn't seem to be changing anything for me. I have also tried the link in my last post, but that didn't do anything for me either. The only thing that I did get from your post was adding another user to my samba share called laptop and giving it a password. I know that on my previous sertup, windows originally asked me for a password and username and I used an account that I had created on my server in order to access my files as it wouldn't let me do so with my root account. Both accounts are admins just as a FYI. How can I change permissions and delete the shares? I will go in via nautilus and uncheck sharing as well as anything else I could have changed just to see if that changes anything. As I said before the first time I just right clicked and said share the drive. However for some reason this time I got the user share 255 error and it won't let me do it that way. It would seem like the smb.conf file is completely useless to me right now for whatever reason. Could it be because I called this build the same thing as my active build at the time? What I mean is that my server was called server-box and was still on the network when I installed the OS on the SSD. It gave me a warning, but didn't do anything about it. I would have thought that since it was going to be erased it wouldn't matter anyways.

---

### Post by RobertKH on 2013-04-10
This is my entire smb.conf file. I even just tried to right click and share my /home/Public folder and I got nothing on a windows machine. It's like it's not even on the network. However checking the IP shows me that it is and the fact that I am sending these posts from it seems pretty likely that it is connected to my network. 

[global]
    workgroup = WORKGROUP
    netbios name = server-box                           <-----I should add that I am not entirely sure about what this line should say. I just guessed and made it my machine name, but it didn't seem to do anything for me.
    security = share
    usershare owner only = false


usershare path = /var/lib/samba/usershare
usershare max shares = 100
usershare allow guests = yes
usershare owner only = no


[RAID]
    path = /storage
    guest ok = yes
    read only = no


[500gb]
    path = /500gb
    guest ok = yes
    read only = no

---

### Post by CharlesA on 2013-04-10
It still looks like you are trying to combine the two kinds of sharing into one file and that's going to cause problems.

Run this from the server please:

```
smbtree
```

You might need to install something if it isn't already installed.

---

### Post by RobertKH on 2013-04-10
What exactly are you looking for? This is the output
```

WORKGROUP
	\\SERVER-BOX     		Samba 3.6.6
	\\MAC000D9336B4DA		TheKerinHerricksComputer
	\\KERINHERRICK1  		
	\\BETHANYSLAPTOP 		
server@server-box:~$ 




```

---

### Post by CharlesA on 2013-04-10
Alright, it sees the server, but it doesn't see any shares.

It should look like this:

```

WORKGROUP
        \\THOR                          Thor server (Samba, Ubuntu)
                \\THOR\Charles          Charles' Folder
                \\THOR\Music            Music Folder
                \\THOR\Shared           Shared Folder
                \\THOR\Software         Software Folder
                \\THOR\IPC$             IPC Service (Thor server (Samba, Ubuntu))
        \\LUNA
                \\LUNA\Users
                \\LUNA\IPC$             Remote IPC
                \\LUNA\C$               Default share
                \\LUNA\ADMIN$           Remote Admin

```

Here's my smb.conf if you want to compare it .
```
[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = /dev/null
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        printing = bsd
        print command = lpr -r -P'%p' %s
        lpq command = lpq -P'%p'
        lprm command = lprm -P'%p' %j

[Charles]
        comment = Charles' Folder
        path = /array/charles
        invalid users = htpc
        write list = charles
        create mask = 0660
        directory mask = 0770

[Music]
        comment = Music Folder
        path = /array/music
        read list = htpc
        write list = charles
        create mask = 0664
        directory mask = 0775

[Shared]
        comment = Shared Folder
        path = /array/shared
        write list = charles
        create mask = 0664
        directory mask = 0775

[Software]
        comment = Software Folder
        path = /array/software
        invalid users = htpc
        write list = charles
        create mask = 0664
        directory mask = 0775

```

It might also help to run testparm on your smb.conf file. :)

---

### Post by RobertKH on 2013-04-10
So here is the output:
```

sudo testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[RAID]"
Processing section "[500gb]"
WARNING: The security=share option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
	security = SHARE
	usershare allow guests = Yes
	usershare owner only = No
	usershare path = /var/lib/samba/usershare
	idmap config * : backend = tdb


[RAID]
	path = /storage
	read only = No
	guest ok = Yes


[500gb]
	path = /500gb
	read only = No
	guest ok = Yes
server@server-box:~$ 

```

So should I be saying to share every single folder that I want to share? Really, ideally I would be sharing the top level folder and allowing my windows PC to modify, create, delete and whatever else inside of that container. Does that make sense?

---

### Post by CharlesA on 2013-04-10
> **RobertKH said:**
> 
So should I be saying to share every single folder that I want to share? Really, ideally I would be sharing the top level folder and allowing my windows PC to modify, create, delete and whatever else inside of that container. Does that make sense?

Depends on how you have it setup. On my server, /array is where my raid array is mounted and charles, music, etc are subfolders of that array.

This might be causing issues:

**WARNING: The security=share option is deprecated**

Try using user shares or setting them up to be accessible via guests at least until you can connect and see your shares.

---

### Post by RobertKH on 2013-04-10
I wish that I could show you the blank stare on my face right now.... how do I set up what you are talking about?

---

### Post by CharlesA on 2013-04-10
> **RobertKH said:**
> I wish that I could show you the blank stare on my face right now.... how do I set up what you are talking about?

Just replace your current smb.conf file with this and restart smbd and nmbd.

```
[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = /dev/null
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        printing = bsd
        print command = lpr -r -P'%p' %s
        lpq command = lpq -P'%p'
        lprm command = lprm -P'%p' %j

[RAID]
path = /storage
guest ok = yes


[500gb]
path = /500gb
guest ok = yes

```

---

### Post by RobertKH on 2013-04-10
Is it odd that when I just did that I got this message in terminal:
```

server@server-box:~$ sudo nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: info_fn: file /var/lib/samba/usershares/random shared docs is not a well formed usershare file.
info_fn: Error was Path is not a directory.




```

---

### Post by CharlesA on 2013-04-10
That's because you were mixing classic samba and nautilus's user share (right click > share).

can you go to the sharing definitions and disable them all ?

---

### Post by RobertKH on 2013-04-10
I should have also pointed out that making that my entire smb.conf file did nothing for me. I am still unable to see anything in windows.

---

### Post by RobertKH on 2013-04-10
sure. Do I just do that via right click? Because I did that part already. I went through and cancelled all the "Share this folder" options. (or at least I think that I did all of them)
Or do you mean to do it elsewhere?

---

### Post by RobertKH on 2013-04-10
Ok so is it odd that I have one called usershare and one called usershares? I don't see why that would ever be?
[ATTACH=CONFIG]241192[/ATTACH]

---

### Post by CharlesA on 2013-04-10
> **RobertKH said:**
> sure. Do I just do that via right click? Because I did that part already. I went through and cancelled all the "Share this folder" options. (or at least I think that I did all of them)
Or do you mean to do it elsewhere?

That should be all you need to do.

If it still isn't showing anything, are you blocking any ports with a firewall?

---

### Post by RobertKH on 2013-04-10
No firewall being blocked. As I said before the first time I did this it worked like a charm. However after switch boot drives with a fresh install it doesn't seem to like it. What could I be missing? I don't get it. Should I just delete all the files in the usershare and usershares folder? will that do anything for me? after restarting smbd won't it just rewrite them?

---

### Post by RobertKH on 2013-04-10
Ok so I just double checked and there is nothing being shared, with the exception of my /home/public folder. I still have all those share definitions and some even say version #2. Does that make sense?

---

### Post by CharlesA on 2013-04-10
I don't know what else to tell you. I guess you could try booting a livecd, installing samba and configuring smb.conf and then seeing it you can see the shares. That would rule out a bad network configuration.

---

### Post by RobertKH on 2013-04-10
So how do i essentially "start over" here? How can I uninstall all my samba data and start fresh? Or is that even possible? Could I delete all the definitions? Or would a reboot automatically build them?

---

### Post by CharlesA on 2013-04-10
> **RobertKH said:**
> So how do i essentially "start over" here? How can I uninstall all my samba data and start fresh? Or is that even possible? Could I delete all the definitions? Or would a reboot automatically build them?

Outside of a reinstall, I don't know because I don't use that usershares thing in nautilus.

Before you do anything on the actual machine, it would probably be a good idea to try it on a livecd to see if it shows the same symptoms.

---

### Post by darkod on 2013-04-11
I don't know what to tell you either. I wasn't even aware samba and nautilus shares are in conflict, I always used only samba and never even tried the right-click in nautilus.

To be sure you start from scratch, your really have to start from scratch I guess. It means a new install. And forget the right-click in nautilus from now on. I understand sometimes the GUI has its appeals, but come on man, samba is not that difficult to configure. Nautilus is just messing it up for you. At the end of the day, if you intend to use nautilus shares why are you installing samba at all? Stick to samba, install it, make the short simple smb.conf and it works. Never touch anything about shares in nautilus.

Also, on the windows client side, if it doesn't show the share right away, don't blame samba always. Maybe the windows can't see the server at all? Have you tried accessing it by the IP on your LAN? Hit the windows logo + R, type \\192.168.1.x (example, put your server IP there), and see if it shows the samba shares.

And don't name two machines the same on the network. It shouldn't be the issue here but you never know. Shared folders include the machine name in them so having two machines with the same name even for a little while could have confused things. Just speculating here. When it warned you, you should have listened to it. :)

That short smb.conf I posted should do the job just fine, I have it running on Server 12.04.2 LTS in my living room. And I'm not samba expert also, I just followed some tutorials, put the bare minimum I needed in smb.conf and it works from day 1.

Also to answer one of your previous questions, you don't need to share each subfolder if you already have the top folder shared. The /storage and /500gb are different locations/mounts/folders, so you need to share them separately. But apart from that, you don't need separate share for any folder inside them.

---

### Post by RobertKH on 2013-04-11
Well I do know that I can access the IP inside my LAN. However maybe what I am doing it not a true test? I can remote in from my phone to do anything with a VNC viewer type application. So I know it's there, however I haven't tried going through run. I'll have to try that tonight. I already removed all of my nautilus shares so I don't see why samba isn't working out for me. I still have that short conf file that you gave me darkod and I'll revert back to that tonight to see if it works. Maybe the one part that I was missing was trying to run it through the command, but I was trying to access it through my network "tab" if you will on Win7. I am in the process right now of re-downloading ubuntu 12.10, unetbootin and the md5 checker in order to verify the download before I create my bootable USB. Maybe I'll skip out on lunch just to try it. Hopefully I can get this thing to work. 

However even with a fresh install, won't my file permissions be the same? These files aren't on my boot disk but on my array and other added drive. So that shouldn't change at all right? I plan on unplugging all the drives so that when I install I only have the one selection and don't screw anything up. That makes sense right?

---

### Post by darkod on 2013-04-11
There have been cases where the shares don't show up in Network in windows. Some of them unexplained.

It might have something to do with the workgroup option (are all your windows machines members of the default WORKGROUP workgroup?). Because some people change that and it might be the reason shares not showing up in Network.

In any case, by IP it should show if shares are available or not, that's the best and most direct way.

Try that first, you might not need to reinstall again.

If you did the chmod a+rw on /storage and /500gb that took care of the permissions, so you don't need to do that again.

As for unplugging hardware when installing an OS, I'm personally against it because my firm belief is that the OS needs to see all hardware as present during the install. It might even show you that it's not recognizing something, so you will be able to see that right away during the install.
But with multiple disks, that does mean you have to be extra careful where you install things, what you delete, etc.

Many people don't want to bother so simply disconnect disks.

Also, I don't know how much data you already put on the array, but playing too much with it (connecting/disconnecting) might also mess something up if things go wrong.

It's all a personal preference and it's up to you. :)

---

### Post by CharlesA on 2013-04-11
For what it's worth, I've been using the default smb.conf for a long time. I don't think I changed anything except adding the share definitions this time. The snippet I posted above should get you started. :)

---

### Post by RobertKH on 2013-04-11
Darkod you are a genius. I was able to run to the address, however for some reason I cannot view it as a place on my network. Does that make sense? So if you look at the attached jpg it shows how my network looks after running windows +r and typing in the address as you see it. However it doesn't show up under computer. Why is that? Do you have any ideas as to what I can do on the windows side for it to show up? Here is another odd thing. I was able to connect using \\server-box just like I was before. However for some reason it doesn't want to stay and I can't ask it to connect at log on. Did I forget a step on the windows side of things?
  [ATTACH=CONFIG]241228[/ATTACH]

So after I just restarted the location disappeared, however I am able to connect to it again. Why doesn't my computer recognize it as it did before? It new the name and everything without having to do anything to connect.

---

### Post by CharlesA on 2013-04-11
Did you set the netbios name in smb.conf?

I ran into something like that before I put a DNS server on my network.

---

### Post by RobertKH on 2013-04-11
Yes I did. This is the output of my entire smb.conf file
```

[global]
	workgroup = WORKGROUP
	netbios name = SERVER-BOX 
	security = share
	
	usershare path = /var/lib/samba/usershare
	usershare max shares = 100
	usershare allow guests = yes
	usershare owner only = no




[RAID]
	path = /storage
	guest ok = yes
	read only = no




[500gb]
	path = /500gb
	guest ok = yes
	read only = no

```

However I still get that "WARNING: The security=share option is deprecated" when I run testparm. I disabled all the right click shares, so any ideas as to why I keep getting this?

---

### Post by CharlesA on 2013-04-11
> **RobertKH said:**
> Yes I did. This is the output of my entire smb.conf file

However I still get that "WARNING: The security=share option is deprecated" when I run testparm. I disabled all the right click shares, so any ideas as to why I keep getting this?

The warning is because you are using share level security instead of user level security, but it should still work.

---

### Post by darkod on 2013-04-11
I also think what Charles said about DNS has something to do with it.

Not only that the workgroup needs to be set exactly the same for all machines, they should also use same DNS server.

If your clients on the LAN are receiving the router IP as DNS (most probable scenario at home), but on your server static settings you put another DNS server, it might not show it in Network because of that I think.

Are the DNS servers different or the same?

At the end of the day, I wouldn't bother too much. You can map the shares so they will show in Computer always as long as the server is running. Doesn't really matter if the server is shown in Network or not.

I don't know if it's a 100% proof, but I just checked and on both my server and my desktop wi-fi network adapter I have static DNS the google servers: 8.8.8.8 8.8.4.4

And in Computer on the desktop it does show my server under Network.

---

### Post by CharlesA on 2013-04-11
If you don't have a local DNS server (usually a router) or a host cannot be found via DNS, Windows will do a broadcast via netbios and find the machine that way. It's not pretty, but it works "ok" for the most part.

If you are able to access the shares, it should be ok now.

---

### Post by RobertKH on 2013-04-11
Right but I want it to be accessible via the desktop Computer folder under Network. I do have a router, but I don't think I am using DNS. I am not the greatest at routing. As I said before though nothing has changed since the last time, with the exception of the nautilus shares. This is truly odd. I think that I can add them as a library location, but I am not entirely sure. Also the other problem is that my iTunes uses the library that I have located on the server itself. after searching for it and then opening up iTunes it worked just fine. I haven't tried to do it without searching for the server first. I'll try that later...

---

### Post by CharlesA on 2013-04-11
I just map the shares as drives on my win7 box.

Otherwise, it's a Windows +R > \\name\share

---

### Post by RobertKH on 2013-04-11
That seemed to work just fine. I just mapped the top level folder (/500gb and /storage respectivly) and it seemed to work. I will just have to try after restart and see if it works.

---

### Post by RobertKH on 2013-04-11
Wow...

Honestly sometimes I'm surprised I can find the toilet in the bathroom <---funny analogy I know but really I've been stupid for the last two days. Remember that I said I renamed it the same thing as an existing build? Well that made my router go haywire. I unplugged my router and modem and after a restart it worked like a charm. Wow....what a dummy. Sorry for wasting your time guys. However without your DNS comments I wouldn't have thought about that. Solved my issue!!!! Thanks a ton guys!! Only one thing left to do, but that's easy. Just have to build another array with 2x 320gb's for my iTunes database. Seriously though....what a pain.

---

### Post by CharlesA on 2013-04-11
Heh. Don't forget to document everything. ;)

---

