---
title: "Best Ubuntu Server version to use for VMWare Server host?"
date: 2008-09-10
forum: Virtualisation
---

### Post by plonka2000 on 2008-09-10
Hi all,

I've been looking into virtualising most of my tasks for my home server environment into a single Ubuntu virtualised server. I'm quite decided on how I want the system configured, but I would really appreciate some advice and/or opinions as to the best way to go about it.

Personally, I'm competently experienced setting up and running VMWare Server and Microsoft Virtual Server x64 in my own Windows workplace environment, but my personal use I wish to use Ubuntu x64.

Ok, here is what I want to accomplish...

Basically, I wish to nearly completely virtualise everything except storage, which I intend to run as an 'growable' mdadm RAID5 array on the host machine for reasons of basic SMB file sharing on my local home network (Home LAN backup and centralised storage). I wish to run on top of this all of my own 'project servers' which would basically be 1 Windows 2003 x32 guest, 1 Windows Vista x32 guest and potentially 1 or 2 Linux guests. I also intend to use Webmin on the host for management. I also wish to thin my host to as much as possible as I want to run it of an SSD drive, which will hopefully do regular complete system backups to the RAID5 or another LAN machine, for recovery purposes.

I have varying reasons for the requirement of each virtual machine, but I want to virtualise them for the prime reason of I want the best out of each platform and I'm quite tired of having separate hardware for each requirement.

I guess the main thing I am wondering about is, I need to know if there is a specialised or cut-down version of Ubuntu server which is optimised for VMWare server usage? I have looked at jeOS but I dont know how well suited that is to my purpose.

Is there anyone that can provide any help, as this would be my first foray into Linux VM hosting. I've read various guides and tips on this very forum amongst other places via the uses of google, but I still cannot set my mind at ease for a suitable Ubuntu host distrobution.

Thanks in advance.

*Edit: I just read back and thought I'd mention, when I mean use Webmin for management, I mean using Webmin primarily for managing and monitoring only the hosts local LAN shares and mdadm RAID array. For managing VMWare, I would use VMWare's tools.*

---

### Post by PilotJLR on 2008-09-11
Ubuntu Server is, by default, very sparse in what packages get installed, so I'm not sure if you can really get much thinner on this distribution. Even OpenSSH Server, for example, is NOT installed by default!
You will definitely be adding packages from there, not removing them!

---

### Post by plonka2000 on 2008-09-11
Thanks for your response, my main concern is because I want a small footprint. My main concerns spawn from my intent to install the OS itself on an SSD (Hoping to use an 4/8GB SSD), separate from the main RAID array used for storage.

I did once install and get an Ubuntu 7.04 server running on a 1GB USB flash drive, which was fun and I think where I ultimately got my ideas from for this project.
The problem I had with that was after updating and configuring the OS with services, the 1GB limit soon crept up.

I figured one way was to flush the apt cache regularly, but I never actually did that in testing so I cant verify the validity of that idea.

---

### Post by veloce on 2008-09-11
If installed size is your constraint, then the 32bit server version will give the best results.

It's a little difficult to tell, but I think my server is using about 1.5 Gb for the system.

---

### Post by plonka2000 on 2008-09-11
Is the x64 version a lot bigger in size or does it just generate more system data via updates, logs, etc?

I was hoping to install the x64 Ubuntu Server for some extra performance and also for the added benefit that I can potentially run 64-bit guests in VMWare Server 2.0 R2.

Is there a big difference in size between x32 and x64?

---

### Post by lazyart on 2008-09-11
You might want to look into Debian for servers-- It's what I've done anyway.  Ubuntu is fantastic with the 6 month development cycle, but I don't really want that for server platform.  My mail server and web server are both virtualized Debian.  On top of that it's more lean than Ubuntu.

If you're really adventurous, look into ESXi.  At 32mb, there is no fat anywhere.

---

### Post by PilotJLR on 2008-09-12
The size difference with 64 bit simply comes from the fact that some 32 bit libraries may be installed... you can control that as much as you want.
I have a 64 bit desktop, for example, with tons of 32 bit libraries, since I'm using 32 bit firefox.
It's less an issue with minial server apps...

You don't HAVE to do a 6 month upgrade. To keep the workload very low, I would just stick with LTS releases.

---

### Post by plonka2000 on 2008-09-12
Thanks guys,
I really appreciate your help and advice. As it stands, I've decided I'm going to use 4GB as the size to shoehorn the OS into and I'll try 64-bit and if that proves too large over time I'll re-do to 32-bit.

Also, I did think about ESXi server but I want to have a large local RAID system for wider storage of my various LAN computers... So I need something a little more general purpose (Linux with mdadm is my plan). Out of interest, if I create my RAID array in 64-bit and then reinstall to 32-bit, can I assume that I will be able to import my software RAID array that was created in a 64-bit environment?

Ultimately, the server I'm going to be building, as per my requirements I stated at the beginning of this thread, will mean I wont be installing very much at all besides the OS, any requirements for RAID and Samba, Webmin and VMWare Server 2.0 RC2. Indeed, the server itself will be totally lacking any X Server also. It will only be hosting the VM's (Which will sit on the RAID array) so I can manage them from my main system using VMWare remote tools. The plan is to have the base system as stable as possible and run any project services on my VM(s).

I think I'll kick this one off tommorow and start experimenting with my setup and messing with building the empty RAID array before I settle on my final outcome. I'll post back here and let you know how I'm getting on if you like.

Thanks so far. :)

---

### Post by lazyart on 2008-09-12
If "stable as possible" is your requirement, I'd suggest you wait at least for the final version of VMware Server 2.0.

---

### Post by plonka2000 on 2008-09-13
Is that because there are known stability issues with VMWare Server 2.0 RC2? I have checked their FAQs and some of their known issues announcements, but I cant seem to find any major show stoppers.

The reason I wanted to use 2.0 is I want 64-bit guest support.

---

### Post by robgolding63 on 2008-09-13
I'm doing exactly what you plan to with my home server. I'm running Hardy 64-bit Server, with 3 Virtual Machines (all Windows Server 2003). The host has 4GB of RAM, and I have a couple of RAID1 arrays using mdadm.

I have spend a lot of time tweaking the server to perfection, with virtual memory settings, and vmware config alterations - to get the best out of the server. I have got the load average down to about 0.2 now when the server is ticking over, which to say it started out at about 1.5 isn't too bad!

I've written a little document with most of the things I've done, so if you're interested just PM me and I'll go through it with you.

Rob

---

### Post by robgolding63 on 2008-09-13
I've just beefed up the document a bit - there was a lot of things I did to my default ubuntu install that would help anyone else doing the same thing greatly. I've incorporated startup scripts and tweaks into it so hopefully it should come in very handy indeed!

Rob

---

### Post by plonka2000 on 2008-09-13
Ok, I'm getting to the point soon when I'm going to be creating the RAID array, but I have a question which I cant seem to answer about 'chunk size'. I know its not specifically a Virtualisation-specific subject BUT it does afftect it.

I've searched the ubuntu forums and googled about 'chunk size', which I know is basically allocation unit size for the RAID volume but cant find anything more than a few people saying "You might want to experiment with chunk size".

The way I think this affects the VM is because VMs can grow quite large, the disk access can be an important factor in performance. Is it worth adjusting my chunk size to reflect the need for using a VM?

Also, I'm going to be storing a lot of large media files like HD movie backups and such for my media center in the living room. Will adjusting my chunk size up or down help with disk efficiency and/or performance?

Anyone that could help please let me know.

Thanks again.

---

### Post by plonka2000 on 2008-09-13
Robgolding63, I would really LOVE a copy of that doc to rifle through. Out of interest, have you had the same thoughts about 'chunk size' for your RAID volume?

Thanks.

[I]Edit:
Also, did you consider using the cut-down jeOS Ubuntu server distrobution?
I'm wondering if the no-fat jeOS version will be good for my uses.
Link to jeOS here: [http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)[/I]

---

### Post by robgolding63 on 2008-09-13
I heard a lot about altering the chunk size of the RAID array, and indeed the block size of the file system itself, but never got round to trying it. The performance seems to be fine as it is though, so I left it all at defaults.

One thing that has made me remember though, that I haven't included in the document, is that I added **noatime** to the mount options on my system and VMware drives (system because it holds the VMEM files for the VMs when you turn UseNamedFile off in the VMware config).

Anyway, I've posted it on my blog so it's easier to get at: [http://www.robgolding.com/index.php/2008/09/13/ideal-ubuntu-server-configuration-for-vmware-host/](http://www.robgolding.com/index.php/2008/09/13/ideal-ubuntu-server-configuration-for-vmware-host/)

Hope it helps, keep me informed!

Rob

[I]Edit for your edit: No I didn't, the JeOS install is, if I understand correctly, designed for running as a guest under a virtualisation platform such as VMware, so I saw Ubuntu Server as the most suitable host O/S. It isn't particularly bloated at all if you don't choose to install lots of extra rubbish - it installs in about 15-20 minutes.

Edit 2: I remembered another point, so I've uploaded a modified version of the document. Sorry I had to zip it up but my webserver won't allow the download of .docx files :(. The extra point was using XFS as the file system for the VM drives.[/I]

---

### Post by plonka2000 on 2008-09-13
Rob, thanks for your upload. I'm reading through it now.
There was something I noticed about your hardware setup that I wanted to ask you in relation to your VMWare performance.

I noticed in your doc that you use an E2220 Intel CPU, which is all well and good, as I'm using a E2160 in my current build.

What I wanted to know specifically about was your experiences using virtualisation and why you have not used a CPU with in-built VM technology enhancements.
I ask this mostly because I have a E6300 in another machine that would be the same level of performance but with VM extensions. I was considering swapping the E6300 out to my server to take advantage of the Intel VM extensions. Do they even work and if they do, in your experience, is it a big deal being without it?

Thanks.

[I]Edit:
Found out some more info while searching online regarding VMWare Server 2.0 and V-Enabled CPUs.
From a review of Server 2.0 Beta at: [http://www.pcw.co.uk/personal-computer-world/software/2207528/vmware-server-3685033](http://www.pcw.co.uk/personal-computer-world/software/2207528/vmware-server-3685033)
"VMware Server 2.0 can be used by small businesses looking to both consolidate physical servers and host business desktops. It&#8217;s available in the same two formats as the previous version - for use on either Windows or Linux hosts and the hardware requirements are much the same as before. That means support for both 32-bit and 64-bit processors (Intel or AMD) including those with Intel-VT and AMD-V virtualisation extensions.

Unlike some other virtualisation tools, processors with virtualisation extensions are not an absolute prerequisite. However, they are needed if you want to take advantage of the support for 64-bit guest operating systems plus, of course, you&#8217;ll need 64-bit processors in the host server. A utility is also available to check that your processors meet these requirements."

Also found an interesting 'tip article' about finding out how V-capable your CPU is (And a little tip, pasted below).
Found at: [http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/](http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/)
"From my research, VT is required in order to run 64-bit guests under the free VMware server for linux&#8230; so it would logically follow that if you can do so, VT is enabled.

32-bit VT is not enabled by default under VMware server. If you want to enable it, you need to add the following line to your *.vmx file for your virtual machine:

    monitor_control.vt32 = TRUE

VMware does not recommend that you use VT for 32-bit guests, because they say it will actually hurt performance."[/I]

---

### Post by robgolding63 on 2008-09-13
I chose that CPU because quite simply, it was much cheaper than a full-blown Core 2 Duo (with the VT extensions). So far, I have had no problems whatsoever with performance, it has been very speedy with 3 VMs running - as mentioned in the document I have a DC/File Server, Exchange server and Web server running, and I have attached a CPU graph from Cacti - as you can see it's basically idling. Note that the spikes are the backups during the night.

I must say that I didn't choose this chip knowing it didn't have the extensions - I found out after I bought it, but that said it's not been a problem for me at all so far. Obviously if your budget allows then a CPU with the extensions would probably perform even better. I specifically chose this socket however, as it is extremely upgradable - if I find I am lacking in performance, I can upgrade to a Core 2 Quad if I wish - as it is exactly the same socket (LGA775). Also my motherboard has space for another 4GB of RAM so I can push this box very far if needs be. If you want a list of parts I used to build this server (which is now about a month old), then just let me know.

Rob

---

### Post by plonka2000 on 2008-09-13
What else can I say but 'Wow, nice performance!" Thanks for the graph, makes things a lot easier to see what you mean.

I'm assuming your backups push to your external USB you mentioned before? If you dont mind my delving, do you push them down onto your host from your guest VM by means of a virtual linked directory/share or over your LAN or simply to your external USB virtualised to your VM?
I was wondering myself how best to perform my backups to my soon-to-be backup/VM server and you've given me new ideas.

I also added some edits to my last post regarding the Intel-VT extensions if you're interested. Apparently (According to these sources and a few others I've seen) its required for 64-bit guest support.

I think I will swap out the E6300 from my other (Vista) workstation (currently where my VMs sit) to this server for testing. I'd like to run some performance and file management tests with and without the extensions bios-enabled as I cant seem to find any online.

---

### Post by robgolding63 on 2008-09-13
I had no idea about that VT info - I didn't know you needed it for 64-bit guests, but seeing as I'm not running any, and it would hurt performance of my 32-bit guests, I accidentally made the right choice!

If I upgrade to Exchange 2007 however, I will need 64-bit guest support, but this is where my socket decision comes in - I can buy a C2D with VT, and I will have only lost the £40 it cost me for the E2220 :)

---

### Post by robgolding63 on 2008-09-13
Oh, and about the backups:

I have shared the external USB drive using Samba, and the Virtual Machines backup to this over the network. I have found this to be the fastest, and easiest method to backup - as VMware Server 1.x only supports USB 1.1, so the speeds would be horrendous if I mapped the USB drive onto a guest via USB.

Using this method, I am able to backup about 35GB in 2 hours - which is just fine for what I need to do!

Rob

---

### Post by plonka2000 on 2008-09-13
Thanks for letting me know.
I'm pretty sure VMWare Workstation for Windows has a 'Virtual Folder' option, which is like a single directory thats located on your host and linked to your VM...

I'm guessing the Linux variant doesnt have such a feature so backing up over LAN would indeed be the way forward.

With the advent of VMWare Server 2.0 and added support for USB 2.0, that may be a helping factor in the future.

Well, all seems well for my server build so far. Today I did a test install and had a basic x64 system running. As it stands right now, I just got back from a night out with my friends and I'm pretty baked (I'm surprised I'm so coherent). Tommorow I'm going to rummage around for my tiny tube of Arctic Silver and do thew CPU swap and subsequent final OS build. Needless to say, I'm impressed by your performance and I cant wait to see if there is any distinct advantage to all this much-hyped Intel-VT malarkey.

Roll on Sunday!

[I]Edit:
Wait, it's already sunday![/I]

---

### Post by robgolding63 on 2008-09-14
Great, let me know how it goes! I'd love to know if it would be worth upgrading to a more powerful CPU - not only for the 64-bit guest support but if the performance gain is anything worth shouting about.

Good luck with the build!

Rob

---

### Post by veloce on 2008-09-14
> **plonka2000 said:**
> Is that because there are known stability issues with VMWare Server 2.0 RC2? I have checked their FAQs and some of their known issues announcements, but I cant seem to find any major show stoppers.

The reason I wanted to use 2.0 is I want 64-bit guest support.

I had quite a few problems with server 2.0 and switched back to 1.0.X.  My vms would lock up regularly and the web interface was really slow.  Some of this may have been to do with using vms created under v1.0.X. so YMMV.

---

### Post by plonka2000 on 2008-09-15
Thanks guys, the build is been going well so far except for 1 snag.
Unfortunately, my weekend is turned out to be busier than I anticipated and I've only had today to really knuckle down to it.

veloce, I'll keep your issues in mind for testing.
I have a VMWare 1.0.x VM that I could port over, but for the first while I think I will be creating new VMs in 2.0 and running them.
What I will do, though, when the server is finally running is copy one of my 1.x VMs over and see how it behaves. Thanks for the heads up.

Rob, I did my CPU swap over last night and the system is liking it as we all knew it would. When VMWare is running I'm gonna do some Intel-VT with and without tests to see how it affects 32-bit VMs.

Anyhows, the issue I mentioned at the beginning is one of drive mapping. Not really something for the Virtualisation forum, which is why I've latched onto this thread here:
[http://ubuntuforums.org/showthread.php?p=5792821](http://ubuntuforums.org/showthread.php?p=5792821)
Just to stop myself repeating, I posted this is the other thread:
> **plonka2000 said:**
> I'm trying to find a solution to this same issue.
I'm setting up my new server and I've run into a bit of a wall when it comes to setting up my RAID array (which I plan to expand in future.)

I'm booting off a USB disk, for my OS and using internal drives for the RAID.

Problem is my USB was mapped as **/dev/sda** while setting up the system. Now the system is done and I've plugged the drives in, my USB system drive is changed to **/dev/sdd**.

Does anyone know a workaround for this to force a device to a particular /dev mapping?

Thanks all.

[i]Edit:
The reason this is such an issue for me is that I plan to add more drives to my RAID array in future.
So I can see that when I plug more drives in my system drive will become **/dev/sde** then **/dev/sdf** etc...[/i]

Thanks guys.

---

### Post by plonka2000 on 2008-09-15
Think I found a fix for my issue using the **_devlabel_** tool.
Its all in the other thread. :)

---

