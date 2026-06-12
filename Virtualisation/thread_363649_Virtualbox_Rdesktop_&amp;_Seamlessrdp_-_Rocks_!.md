---
title: "Virtualbox Rdesktop &amp; Seamlessrdp - Rocks !"
date: 2007-02-17
forum: Virtualisation
---

### Post by mat_london on 2007-02-17
Has anyone managed to get the seamless windows effect with Virtualbox Rdesktop & Seamlessrdp ?

Friends and family who have seen my new laptop and edgy + Beryl are asking me to put Ubuntu on their laptop etc  Its amazing to see how taken people are with the current state of Ubuntu.
However they all take the request back when they realise that that won't be able to run a particular vital application.

As a result I''ve spent some time trying to get  XP applications running inside my fresh edgy install.

So when i came across this article:

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")

I was very keen to get it all working. I reckon that if this could be made to work smoothly, a large new userbase of Ubuntu switchers will appear.

Unfortunately I haven't managed to get Qemu or Kqemu running at any usable speed and I can't get KVM working at all.
It was after trying this that I discovered Virtualbox [http://www.virtualbox.org]("http://www.virtualbox.org")

Which I my system absolutely flies and is silky smooth, in fullscreen mode there is no sense that I am working in a virtualised environment.

The really neet thing I am trying to get done though is the rdesktop & seamlessrdp access. 
This means I or my new Ubuntu loving friends could ulitmately just click a link and get a full speed XP app running in Ubuntu in its own window. (explained in the WindowsXPUnderQemuHowTo link above)

Rdesktop & seamlessrdp access actually worked fine with Qemu using the command.

/usr/local/bin/rdesktop -A -s \ "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" -c "c:\seamlessrdp" 192.168.0.3

I've set up static host access in Virtualbox using a tap interface as per this page:

[http://www.happyassassin.net/2007/02/06/vmware-to-virtualbox/](http://www.happyassassin.net/2007/02/06/vmware-to-virtualbox/)

This works fine but I cannot get the rdesktop & seamlessrdp to work together, rdesktop logs in fine but I get the full desktop and not the seamless windows.

Has anyone managed to get the seamless windows effect with Virtualbox ?

Mat

---

### Post by llamakc on 2007-02-17
I'm doing something similar with VMWare. I have to make sure I am logged out of XP and at the Windows login screen if I want just one single application to run. I experimented with iTunes, which works perfectly for me.

---

### Post by mat_london on 2007-02-17
Could you give us the command you are using ?

I'm not familiar with Vmware, have you set up a bridged host network adaptor in Vmware or does VMware have an automatic RDP service. 

I had it working fine in Qemu too.

mat

---

### Post by llamakc on 2007-02-17
> **mat_london said:**
> Could you give us the command you are using ?

I'm not familiar with Vmware, have you set up a bridged host network adaptor in Vmware or does VMware have an automatic RDP service. 

I had it working fine in Qemu too.

mat

```

rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\iTunes\iTunes.exe" 192.168.0.XXX -u USER -p PASSWORD
```I had to create a password for my XP user to get rdesktop (Version 1.5.0-rc1) to work. My VMWare VM for XP is using a bridged network, and I installed SeamlessRDP on the Windows side.

I just made sure it was working (again). For some reason I have to run the command twice: the first time getting the full RDP session of the XP desktop, and after 'logging out', the second time getting iTunes to fire up on top of OpenBox.

---

### Post by mat_london on 2007-02-17
Thanks,

I've got full host networking going and can now do a proper terminal services type login, but for some reason Virtualbox is still ignoring the seamlessrdp instructions.

Virtualbox is very very fast on my laptop, shame I can't get this going.

Mat

---

### Post by llamakc on 2007-02-17
> **mat_london said:**
> Thanks,

I've got full host networking going and can now do a proper terminal services type login, but for some reason Virtualbox is still ignoring the seamlessrdp instructions.

Virtualbox is very very fast on my laptop, shame I can't get this going.

Mat

You've enabled remote access on the Windows side, correct?

---

### Post by Mike'sHardLinux on 2007-02-18
Thanks for the info! I just managed to get this to work with VMware Server on my server.

For some reason, the VMware server installed on my desktop won't work properly - with NAT Networking, the VM can connect to the net and to my fileserver, but then it doesn't have an ip address in the same subnet, so I can't RDP into the VM...I can't even ping it; with Bridged networking, I can ping and rdesktop into the VM, but can't connect the VM to the net or to any network resource.

Anyway, my real question is: How do you plan to deal with the saving/loading of files using SeamlessRDP into a VM? Are you going to map the My Documents in the VM to a samba share on the Linux host?

---

### Post by mat_london on 2007-02-20
Not sure about VMware, with Virtualbox I've set up a samba share on my laptop which I open from and save to on the VM.

---

### Post by veloce on 2007-02-21
I have several windoze vms running under vmware server (not necessarily all the time)  I too have found that rdp to them is great - though I haven't come across seamlessrdp.

The way I set it up was with a virtual firewall between the vms and the real world.  I have two virtual networks set up on the host, host only and bridged.  The vms are all on the host only network, the IPCop virtual firewall has two virtual network cards and is connected to the host only network and the bridged network to the real network.  

[LIST]
[*]I rdp to the vms over the host only network.

[*]Transfers between virtual machines and the host are accomplished using a samba share on the host.  

[*]I allow limited access to the real network from vms through the firewall.
[/LIST]

This sounds complicated but was really easy to set up and works really well.

---

### Post by Icarus3000 on 2007-03-08
Can anyone verify that they have Seamlessrdp/rdesktop working with virtualbox?

---

### Post by yursil on 2007-03-22
I had a similar problem as the originating poster (I'm a gentoo user though), I found out what it was. You have to actually log off (not just closing rdesktop) from the XP machine (virtual or not) in question for this to work.  You will still see a fullscreen for a moment and then it goes away as you become logged in.

---

### Post by Protoss on 2007-03-25
So you actually got VirtualBox and seamlessrdp to work together?

---

### Post by 7heCas on 2007-03-28
> **llamakc said:**
> I'm doing something similar with VMWare. I have to make sure I am logged out of XP and at the Windows login screen if I want just one single application to run. I experimented with iTunes, which works perfectly for me.

I tried this, but I can't get it to work.  I get the "Connection Refused" error.  My question is how do you have a 198.162...... IP if you are using Bridged connection?  When I ipconfig in CMD I just get localdomain.  If you could help me out I would really appreciate  it.  I feel that I am just doing something stupid wrong.

-cas

---

### Post by xidahs on 2007-10-14
Was just reading the posts and though maybe I could add somthing that could've been missed. When I was trying to set up samba on ubuntu I could not for the life of me get access to the shared folders on my vmware virtual machine. I knew it was the firewall in ubuntu cos when I turned it off the folders appeared. I eventually came accross somthing on the net which said in firestarter you needed to turn off under edit : preferences : Advanced options, Block Broadcasts from Internal network It may have been from external network can't quite remember. Anyway if this cured the problem of host - virtual machine communication for me then it may help for others.

---

### Post by klecu on 2008-02-07
I'm using VMWare server, but using an open source alternative would be nice. Like some of the others here, I'm not familiar enough with virtual networking, or even linux networking in general, to set up a vmnet between the virtual machine and the host. I feel this would be better, since the Remote Desktop connection is not going over the LAN. Anyone have specific commands to get the host and vm to talk?

---

### Post by prol on 2008-02-08
Check these articles guys!

[http://www.linux.com/feature/124908](http://www.linux.com/feature/124908)

[http://forums.fedoraforum.org/showthread.php?t=170641](http://forums.fedoraforum.org/showthread.php?t=170641)

> If you run it "as is," it will pop up the full Windows XP desktop (including the wallpaper, icons, and shortcuts on the desktop).

If that's too intrusive for you, you can hack the Windows registry to get rid of the desktop and keep only the menu bar. Once you're in Windows XP again, launch the Registry editor by going to Start -> Run and typing regedit. Search for HKEY_CURRENT_USER -> Software -> Microsoft -> Windows -> CurrentVersion -> Policies -> Explorer. Once there, right-click on the right panel and select New -> DWORD Value. Name it NoDesktop, then click on it and change the data value to 1. Close the Registry editor and restart Windows. 

---

### Post by Midnight_Sun on 2008-12-26
To the original problem:

I had the same experience: rdesktop to VirtualBox VM and unable to start semlessrdp.

The problem is - as far as I see - that VritualBox uses it's own rdp host, and actually rdesktop logs in to VirtualBox, and not to the guest OS. That means, You can not use the -s option of rdesktop, since VirtualBox can not give You a different shell (cmd.exe or seamlessrdpshell.exe, or whatever...)

(I was also unable to log in to the Vbox with IP address of the guest os, ONLY rdesktop localhost:3389 worked!)

Anyone has suggestions or a workaround?

---

### Post by f1r3br4nd on 2009-07-02
Bump!

(or BuHp as the case may be)

Same problem here, with VirtualBox 3.0. It has a seamless mode, but it's just eye candy. It's still the standard VBox GUI with the desktop hidden and the XP bar accross the bottom of your host screen. You still can't connect via rdesktop without getting the commands you specify in the -s argument completely ignored and getting the whole desktop every time.

This means you can't create scripts on your host for launching individual apps. Plus, VBoxHeadless is faster than the GUI (but has no native seamless mode and still cannot properly take commands from rdesktop).

---

### Post by HermanAB on 2009-07-03
You need this:
[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

It works with any kind of Windows system, Virtualbox, VMware, a real Windows machine, whatever.  It isn't a 'feature' of Virtualbox per se.

---

### Post by glymph on 2009-09-09
I get a similar problem: rdesktop connects and appears to start the application, but either doesn't display anything or segfaults - if I re-run the command it shows the application but with gnome's window decorations on it and any menus or tooltips.

I'm accessing a virtualbox headless installation of Windows XP (sp3) on a seperate system running i386 8.04[.2], my 64-bit client machine is running the following command with rdesktop 1.6.0-2ubuntu1 under Ubuntu 9.04:

```

rdesktop -u username -p -  -A -s  "C:\seamlessrdp\seamlessrdpshell.exe cmd.exe" servername
```

I'm running the headless virtual machine with the option -p 3391 so its graphical output (i.e. what would be displayed on the monitor) is accessible via a different port to the standard remote desktop port (3389), which is what rdesktop uses by default. 

They shouldn't conflict with each other, but it still only shows the login process happening and then no cmd.exe window is displayed or it segfaults at this point.

EDIT: Using the version of rdesktop from Debian Etch (1.5.0-1) seems to work ok

[http://packages.debian.org/etch/rdesktop](http://packages.debian.org/etch/rdesktop)

:D

---

### Post by f1r3br4nd on 2009-11-11
> **HermanAB said:**
> You need this:
[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

It works with any kind of Windows system, Virtualbox, VMware, a real Windows machine, whatever.  It isn't a 'feature' of Virtualbox per se.

Well, I downloaded it, unpacked it exactly as per instructions. Though rdesktop does connect...

```
 rdesktop -A -s 'c:\seamless\seamlessrdpshell.exe c:\windows\notepad.exe' localhost -u Administrator -p a
```

...the argument following -s is completely ignored no matter what it is or what kinds of quotes enclose it. It just connects you to the desktop. Please help someone?

---

