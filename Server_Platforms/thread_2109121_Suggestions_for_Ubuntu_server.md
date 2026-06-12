---
title: "Suggestions for Ubuntu server"
date: 2013-01-26
forum: Server Platforms
---

### Post by Eyeball114 on 2013-01-26
Hello. I am building a small server at home that will be used to host mostly Minecraft servers and a few VOIP servers. I am by no means a Ubuntu or Linux user but I would really like to learn more. I just installed Ubuntu Desktop on an old laptop Ive had for a bit and instantly fell in love. So I am playing around with that while I wait for some hardware for the physical server. I have just a few questions to ask some of the pros if they wouldn't mind helping out a sec. I currently host 3 minecraft servers on my windows 7 gaming rig. I'm tired of processes building up throughout the day and taking up RAM and having to restart my game servers so I decided to build a dedicated machine. 

- With already having multiple servers running on my machines, how difficult would it be to transfer the file information over to a Ubuntu based machine? What anything like, run.bat or any .jar need to be changed or converted in anyway?


- How difficult would it be to have multiple servers running? I have plans for 2 more MC servers at least 2 VOIP servers and possibly a DayZ server. Is it possible to run all of these at the same times with no conflicts? If configured correctly of course.


- Based on the info I've given what version of ubuntu server should I use to best suit my needs? 


- Best options for remote desktop from windows to the ubuntu machine? 


I honestly appreciate any help that is thrown my way. I am really eager to learn more of Ubuntu/Linux in the coming time.

---

### Post by prodigy_ on 2013-01-26
Here's Minecraft server [HOWTO](http://www.minecraftwiki.net/wiki/Tutorials/Setting_up_a_server#Ubuntu). Not sure if you can have multiple instances running on the same machine.

Transferring files shouldn't be hard. You can [enable SSH server](https://help.ubuntu.com/12.04/serverguide/openssh-server.html) on your Ubuntu installation and then use any SFTP client (e.g. FileZilla) to upload/download anything. Alternatively you can [install Samba](https://help.ubuntu.com/community/Samba/SambaServerGuide) and get Windows-like shared folders.

I'd suggest sticking with the lastest LTS release (currently 12.04) for server installations.

As for remote desktop, you can use RDP or VNC. There are many [HOWTOs](http://www.youtube.com/watch?v=KY3V79t5tKA), just google for them.

---

### Post by frank604 on 2013-01-26
First of all, I'm not sure what the purpose of running 2-3 servers at once.  If it is for world map reasons I'd just run 1 server with 3 world maps and use a portal for players to port into each world.

Minecraft is very demanding for upstream bandwidth and speed.  I was on a residential plan with Shaw Cable paying $100 a month and I only had 15 MBPS up speed.  Still was hard to host 8-10 players on a large world.

I am here not to lend answers to your question but to give some insight on something cool.  I ran my minecraft server a year or two ago with MineOS.  It is unsupported but MineOS Crux is actively developed and is the successor to MineOS (according to the wiki).

[http://www.minecraftwiki.net/wiki/MineOS_CRUX](http://www.minecraftwiki.net/wiki/MineOS_CRUX)

It's based on tiny linux and the whole OS is less than 50 mb in size.  It is tailored only for minecraft serving and has a LOT of great addons for remote administration as well as for maintenance of bukkits (mods) and maps.

Regarding the other servers you want to add, alternatively you can run mineos in a virtualbox in ubuntu as the host.  I really like the interface and options of mineos, just give it a check through.

---

### Post by Eyeball114 on 2013-01-26
Well I host several servers for a gaming communtiy. I understand everything about my bandwith, what my rates are, and anything I'm limited to. 

I have 52 down and 32 up with verizon fios. I have been succesfully hosting 3 modded MC servers with no connection issues and little to no lag at any time. Players connect from all of the world to my servers and I have heard no complaints. Large worlds with max number of players being 30 and prime time had these servers filled. 

The server Im looking to put together isn't just for MC but that is its main purpose. 

I did try hosting multiple servers on Ubuntu desktop on my laptop and with no issues at all had 2 very smooth running servers with no issues I could see. So running multiples should't be an issue for me. 

Thank you both for your helpful information :)

---

### Post by frank604 on 2013-01-26
I was speaking more on a maintenance point of view.  If you run 3 MC servers at the same time, if you upgrade the bukkits and server you have to do it 3 times.  In comparison, without knowing the real purpose for 3 MC servers, I was suggesting it would be easier to run 1 MC server and update 1 MC server.  If you want 3 worlds, you can link them into 1 server.  You can have as many worlds as you want.  I just use a portal gate in the form of a nether portal to port between each world map.

If the portal gates aren't your thing, I think it is possible to run 1 server and host it into different ports creating 3 unlinked worlds. Just tossing out some ideas for you although they are off topic :)

---

### Post by bigmonmulgrew on 2013-01-26
I recently did this myself.

Firstly you copy all of your files form your windows box to a folder on the ubuntu server. If you have a lot of files (you probably do) it might be worth zipping them and then extracting them on the server. Even on a local connection the small files slow the transfer.

Secondly if you have any mods that refer to a directory like backup folder you need to change this in the configuration file before booting the server.

For example my backups were stored in D:/minecraft/backup.
I had to change this to /var/www/minecraft/backup (or wherever your storing your files.

Next you need to get java installed. This is mentioned on the minecraft wiki.

Lastly you dont use a bat file on linux. You use a bash script to start it. Again this is mentioned on the minecraft wiki.

I found my server ran much smoother on a ubuntu server and I have a huge number of mods. I have a 10mb upload on a fibre connection. Runs a dream. Most players I've had is 10 and that was smooth.

---

### Post by Eyeball114 on 2013-01-26
Great info big! Thanks for your help.


Frank these are 3 separate servers. I run a decent sized minecraft community. They aren't the same server. One is a Vanilla, one is a Tekkit, and one is a Feed the Beast Mindcrack. None of these are linked in anyway and a portal plugin is not what Im worried about. 
Just looking to run all of my separate unique servers from the same machine. 

I have been running these servers for about a year now. All my ports are opened up and working fine. Being new to Linux I was just wondering if there was any issues with running them all at the same time. After playing around with the terminal and making a few test servers I've found no issues with doing it so far. 

Thanks for everyone's input so far.

---

### Post by frank604 on 2013-01-26
Ah I see. Didn't realize you had different plugs for each server.  Just wanted to help :) good luck on your journey.  I've had fun hosting MC but back then the multiplayer was very rough(sluggish).  :(  I guess in the two years that passed there were a lot of improvements.

---

### Post by bigmonmulgrew on 2013-01-26
as long as you have the resources it shouldnt be a problem.

My server is heavily modded and I give my users limited access to worldedit and that tends to boost the ram usage when they make large edits.

The wiki will explain how to assign amounts of RAM. with 3 servers I'd be going for 4GB ram as a minimum unless they are partucularly lightweight.

Also there is a portal plugin that acts like a link between servers. User steps through a portal like in multiverse and is suddenly on a different server. Sorry but I cant remember its name.

---

### Post by sandyd on 2013-01-26
**Moved to server Platforms**

---

### Post by Eyeball114 on 2013-01-26
Yeah big like I said Ive hosted these for some time now and Im pretty much on the up and up of administrating and running the servers. Most of that is all cross platform and applies to any OS.
Im running my more modded servers like tekkit and FTB on 4 and vanilla servers on 2. They all seem to run pretty good and I am excited to see how they perform on Linux. Really loving linux so far and I wish I found it earlier :/

No worries Frank. Optimization really has come a long way since the early days. I remember playing on my friends home hosted server during alpha. Good times lol. 


I apologize for the mis-posting of the thread Sandyd.

---

### Post by Derek Karpinski on 2013-01-26
Not that I know anything about running minecraft servers, but why wouldn't you run 3 virtual machines each running a minecraft server?

---

### Post by Eyeball114 on 2013-01-26
> **Derek Karpinski said:**
> Not that I know anything about running minecraft servers, but why wouldn't you run 3 virtual machines each running a minecraft server?

Is their an easier, simpler way to do it? Like the OP stats, Im a complete noob with Ubuntu and Linux.

---

### Post by Derek Karpinski on 2013-01-26
I'd hate to send you down the wrong road because I know nothing about minecraft servers, but.....

Creating virtual machines is easy and there are some benefits to them.  You can create snapshots and restore snapshots in case changes you made screw up your vm.  You can run several different vm's without worrying about software conflicting.  You can run multiple separate vm's on the same box provided you have the horsepower to do so.  You can reboot one vm while keeping the others running, etc.  Think of it as running 3 different computers in one physical computer.

Download virtualbox:
[https://www.virtualbox.org/](https://www.virtualbox.org/)

Download your minecraft server OS:
[http://minecraft.codeemo.com/](http://minecraft.codeemo.com/)

Create a generic Minecraft server virtual machine.  Then clone it to create your other 2.  Customize each virtual machine how you want it.  Easy peasy!

To take it a step further, after you're done making all your vm's, I'd save all the virtual machine files on an external drive, wipe Ubuntu desktop off and install Ubuntu server.  That is more advanced though.

The above is just my personal opinion on how to easily manage what you're trying to accomplish.

---

### Post by Eyeball114 on 2013-01-26
Thank you so much I will definitely be looking into this!

---

### Post by Derek Karpinski on 2013-01-26
[http://minecraft.codeemo.com/mineoswiki/index.php/Main_Page](http://minecraft.codeemo.com/mineoswiki/index.php/Main_Page)

Looks like this page will walk you through installing MineOS in a virtual machine.

Another great thing about virtual machines is their portability.  Say you get a new PC, or you need to reinstall ubuntu.  Your virtual machines, and all the software/settings inside them, are contained in one file.....a full working computer in one file!  Back it up, reinstall your 'host' OS, copy the vm files back to the 'host' os, and you're done!

---

### Post by bigmonmulgrew on 2013-01-27
Really don't think the virtual PC thing is necessary. I'm only hosting one minecraft server but I'd put it along the same lines as hosting multiple websites with apache.

It just runs as a java process, no customisation of ubuntu is necessary outside of installing java

Running 3 virtual machines would triple your OS overheads and the inevitable inefficiency virtualization gives (admitedly minor these days)

---

### Post by Eyeball114 on 2013-01-27
Just another quick question.

Im messing around "hosting" test servers from Ubuntu desktop 12.04.
When I build my server next week and put Ubuntu server on it will anything be different? Are the successful results I am seeing now conflict in any way when I put them on the Ubuntu server?



Also if anyone has the answer to this

Running a Feed the Beast mod pack. Copied over the files from my windows pc and got the server running. Everything looks great in the terminal and is exactly what I have been seeing on my pc. 

Except I can't connect to the server. All version are correct but next the ping bar is red and shows 'No Connection'

It seems like somewhere in the middle the connection is being blocked?
Correct ports are open as well.

---

### Post by Derek Karpinski on 2013-01-27
> **Eyeball114 said:**
> Just another quick question.

Im messing around "hosting" test servers from Ubuntu desktop 12.04.
When I build my server next week and put Ubuntu server on it will anything be different? Are the successful results I am seeing now conflict in any way when I put them on the Ubuntu server?



Also if anyone has the answer to this

Running a Feed the Beast mod pack. Copied over the files from my windows pc and got the server running. Everything looks great in the terminal and is exactly what I have been seeing on my pc. 

Except I can't connect to the server. All version are correct but next the ping bar is red and shows 'No Connection'

It seems like somewhere in the middle the connection is being blocked?
Correct ports are open as well.

Ubuntu server is command line only.  No GUI.  Makes it much more lightweight, and less prone to bugs, crashes, and security issues.  If you need a GUI, I'd use a more lightweight distro, lubuntu probably.

For the ports being blocked, install Gufw from the software center or command line, and open the ports you need.

---

### Post by Eyeball114 on 2013-01-27
kk Ill try that. Strange that I was able to test 2 other vanilla servers with no issues. Hope this works though.
EDIT: This worked. Feel like a huge noob for not even thinking about the fire wall.. Thanks again. 

Also a GUI can be installed on the server right? I know its not recommended by most but this is mostly for MC servers so I dont think it will add any issues. 
Thanks

---

### Post by Eyeball114 on 2013-02-25
Sorry to revive this old thread but I have finally gotten my server up last night and have a a questions or two.


So I made the mistake of saying to myself "Its just minecraft servers Ill run Ubuntu desktop" So I did that and ran and set it all up and I saw the lovely Ubuntu task bar yada yada...than decided I had made a mistake and wanted to put Ubuntu server on it. I loaded the iso off a thumb drive and it booted up and ubuntu server ran,installed, and looked great. Installed a GUI because I am new at this lol I just feel more comfortable with it right now. 

So first question. 

Why did ubuntu desktop boot this morning when I had already installed and was messing about with the server version the night before? Did it not format the drive? There is only the option to boot Ubuntu or the various memory tests so It didn't look like a dual boot was in place to me. 

Second question.

Can someone explain briefly how I can save files to one hard drive or another? I have the SSD in there now as boot and 2 1 TB WD greens that I may put in Raid 1. Regardless I do not want the game server data to be saved to the SSD by default.  



Thanks for any help. Again it is insanely appreciated. I do hope to be going to school for network admin as soon as my military tuition assistance papers get worked out finally...I find this all really exciting and anything I can do to see this project finished and running is really going to make me appreciate the help I have been given so far even more.

---

### Post by bigmonmulgrew on 2013-02-25
dont be afraid to just open a new topic for a different problem we wont mock you if 10 of the top 20 issues all belong to you. I was like that a couple of years ago.

I would guess its booting ubuntu desktop because you have set the boot device differently, I would guess you installed on the wrong device.

You didnt accidentally install it to the memory stick did you?

When you do go for RAID you will find linux generally ignores motherboard raid.

I wrote a guide for setting up a server to run Drupal on ubuntu server. The installation step shows how to install RAID
check it out
[http://foreverythingit.co.uk/content/installing-server-os-ubuntu]("http://foreverythingit.co.uk/content/installing-server-os-ubuntu")

Understand you installing the GUI but really it would be better in the long run if you learn to use the terminal. You will find yourself using reference a lot for the spellings of commands but its better in the long run to learn the command line.

---

### Post by Eyeball114 on 2013-02-25
Wow...I may have I changed the boot order to the usb stick first. Would that install it to the stick? I have only ever installed from a disc before. I think to install the iso to the SSD I need to change it to USB UEFI? 

I do see your point with the terminal. I understand getting used to it may hurt me later on but without knowing where to start I thought it was best for the moment. 

Thanks for the guide I will definitely be checking it out.

---

### Post by bigmonmulgrew on 2013-02-25
Its hard to say without knowing exactly what you did when installing but plug the stick in and see if it boots to ubuntu server and you will know what happened. Plug the stick back in and have a play with boot options, you might even have installed it on one of your green drives but installed GRUB on your memory stick.

I used to hate the terminal. Despite using DOS from a young age I prefer a GUI for most things but as you get better with the terminal most of the simple stuff gets much more efficient, its worth the practice.

The parts of the guide that refer to Drupal are incomplete but as your not setting up a webserver then that wont be an issue.

I direct linked you the page that refers to RAID but its worth reading from the start. I've tried to give a simple explanation of what each command does as its encountered for the first time so if your a new to the terminal its worth a read

---

### Post by Eyeball114 on 2013-02-25
I got it working. Thanks for the help. I had the USB set as the boot drive, I guess it read the iso off it and installed it to itself. I changed the boot to USB.UEFI and it installed from the stick to the SSD. I haven't hooked the green up yet so that wasnt an issue. Thanks again for all your help everything seems to be in its place right now and running smooth.


Any recommended program to remote from my pc to the server to manage my minecraft terminals? Using Putty give me just the terminal look so should I use something like a remote access program to manage the several terminals using the gui?

---

### Post by LHammonds on 2013-02-26
For my minecraft server, I manage everything through putty and share files to and from the server using a samba share.  I also have my server hosting multiple minecraft servers which use different ports.  Each minecraft instance is also run using a different linux user id so I can manage them individually using screen sessions or using cron to send messages to the screen's console to notify users of events such as schedule reboots, backups, etc.

Anything else is simply wasting resources and taking away from your Minecraft instances.

I wrote an article some time ago on how I did it here: [Bukkit Forums](http://forums.bukkit.org/threads/how-to-setup-a-trickd-out-craftbukkit-server-1-3-1-r2-0.100406/)  It does not cover the multi-server aspect but it was the basis for it.

LHammonds

---

### Post by Eyeball114 on 2013-03-07
> **LHammonds said:**
> For my minecraft server, I manage everything through putty and share files to and from the server using a samba share.  I also have my server hosting multiple minecraft servers which use different ports.  Each minecraft instance is also run using a different linux user id so I can manage them individually using screen sessions or using cron to send messages to the screen's console to notify users of events such as schedule reboots, backups, etc.

Anything else is simply wasting resources and taking away from your Minecraft instances.

I wrote an article some time ago on how I did it here: [Bukkit Forums]("http://forums.bukkit.org/threads/how-to-setup-a-trickd-out-craftbukkit-server-1-3-1-r2-0.100406/")  It does not cover the multi-server aspect but it was the basis for it.

LHammonds


I am having great success so far running my 4 servers and a mumble server through 4 terminals. This doesnt feel like the best way to do it but its working and I am very new to linux in general. I feel as if this would of all been easier if I just had ran them off a copy of windows like I was doing when I hosted from my PC. But I am determined to learn Ubuntu server and I enjoy working with it.

I am running into some problems as of lately. So I am just using windows remote desktop and connecting to my ubuntu server as Console. (I do use a GUI) When this fails to connect I know whats waiting for me when I plug in the monitor by the server. I get a message saying something like [h=2]Filesystem root" has only x Mb disk space remaining[/h]When this happens I have to stop all my minecraft servers, reboot the server, and than I can run my mumble server again and remote desktop again from my pc. 

I've google all of this and have read through the hours of posts and fixes with no luck. Im using a 60gb SSD for boot and a 1tb HDD for storage. I mounted the HDD and can see I have 931.17GiB with 3.39 used. 3.39 Doesnt sound right. I know for a fact all my minecraft servers together equals more than 3.39 GiB. I ran into the issue for the first time and realized all the file editing I did and sent to trash was built up. Since than its been empty. It ran fine for 3 or 4 days before getting the error again tonight. 

I am looking at Disk Usage Analyzer and it shows / usage 100% (Size is 50.8) GB and it shows my home usage at 84.9% and 43.1 GB used. 

Even though I am saving my server files to the mounted HDD it seems like they are just saving to my boot drive. Did I mount it wrong? Or am I just sounding like an idiot because I made an obvious oversight somewhere? lol.

Any help is appreciated. I'd love to find out why this is and how to fix it even just for my own knowledge.

---

