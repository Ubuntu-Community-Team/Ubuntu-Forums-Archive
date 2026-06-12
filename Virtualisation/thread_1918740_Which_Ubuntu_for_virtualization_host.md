---
title: "Which Ubuntu for virtualization host"
date: 2012-02-01
forum: Virtualisation
---

### Post by Nick_C on 2012-02-01
Feel sure this has been asked many times but searches didn't reveal an answer.  What is the correct Ubuntu version to download to use as a workstation virtualization host only, standard or server?

As this is for workstation virtualization I assume it is going to need a GUI for displaying the virtual machines.  Need NTFS support, network configuration and some disk tools, thats about all I need installed.

Thanks

---

### Post by japzone on 2012-02-01
> **Nick_C said:**
> Feel sure this has been asked many times but searches didn't reveal an answer.  What is the correct Ubuntu version to download to use as a workstation virtualization host only, standard or server?

As this is for workstation virtualization I assume it is going to need a GUI for displaying the virtual machines.  Need NTFS support, network configuration and some disk tools, thats about all I need installed.

Thanks

Standard Desktop Install is a better idea since you're doing it all on one PC and not a PC connected to a Server. I'd recommend 11.04 for now since it has the Classic Gnome 2 GUI, which in my opinion, is more stable, functional, and mature then Unity at this time(Hopefully it gets better in 12.04LTS).

---

### Post by Nick_C on 2012-02-02
There seems to be two versions available:

ubuntu-11.10-dvd-amd64.iso
ubuntu-11.10-desktop-amd64.iso

What is the difference between them and which is the standard desktop install?

I know you said try 11.04 but I have already got these downloaded and it is only a test at the moment by the time I don a final install 12.04 may be with us.

---

### Post by xyzzyman on 2012-02-02
The DVD just adds additional packages and languages to the default install. I found it didn't add things that I had to pull from repo's, and instead just added alot that I had to uninstall (Hundreds of megs of languages, etc)

---

### Post by japzone on 2012-02-03
Yeah basically the "DVD" ISO is whatever they couldn't fit on a CD-ROM but would have liked to. It'd be cool if the DVD ISO was more Customizable at install. That way it'd be more convenient for making offline Installs. Like an Advanced mode where you can specifically choose which Packages you'd like installed. That way I wouldn't have to Connect a PC to the Net unless absolutly necessary and won't have to build an ISO myself if I need a Custom Configuration.

---

### Post by collisionystm on 2012-02-03
> **Nick_C said:**
> Feel sure this has been asked many times but searches didn't reveal an answer.  What is the correct Ubuntu version to download to use as a workstation virtualization host only, standard or server?

As this is for workstation virtualization I assume it is going to need a GUI for displaying the virtual machines.  Need NTFS support, network configuration and some disk tools, thats about all I need installed.

Thanks


you do not want to use Ubuntu-Desktop version because of the kernel. If you choose to go that route, install the server kernel post install.

If it were me I would

Install 10.04 LTS server

Install LXDE for a gui

sudo apt-get install lxde

Install Virtual machine manager

Have fun.

---

### Post by japzone on 2012-02-04
> **collisionystm said:**
> you do not want to use Ubuntu-Desktop version because of the kernel. If you choose to go that route, install the server kernel post install.

If it were me I would

Install 10.04 LTS server

Install LXDE for a gui

sudo apt-get install lxde

Install Virtual machine manager

Have fun.

Why do that when he's not going for a Server setup?

---

### Post by collisionystm on 2012-02-04
> **japzone said:**
> Why do that when he's not going for a Server setup?

Because the server kernel is optimised for virtualization. 
Virtualization uses a good amount of resources. Keep it light with LXDE.

It really does not matter to me which route is taken, I was just saying what I would do. If you want to learn virtualization the official ubuntu way then run a server with the proper tools. 

If you want to just run something on a desktop, just use virtualbox

---

### Post by dcstar on 2012-02-04
> **collisionystm said:**
> Because the server kernel is optimised for virtualization. 
........

If you use the Server kernel you will lose things like Audio from the VMs to the host that work in the Generic Ubuntu kernel. You may also lose things like Accelerated Video.

The current 10.04 LTS Ubuntu works fine for virtualising Workstations and allowing you to use most of their features.

---

### Post by japzone on 2012-02-04
I'm Running the x86 PAE kernal with Ubuntu Desktop 11.04 and Ubuntu Classic (No Effects) desktop. Booting OSs in VB works fine and everything including Audio works. I've been able to boot Windows 7 and Run a Veriety of PRorams plus watch Netflix in a Web Browser. The only thing I've had problems with is Direct3D so things like the OnLive Client won't work(Yes I installed VB GE via Safe Mode and checked the Driect3D option but still no luck). Other than that I'm a happy camper. Only thing I haven't tried yet is booting OSX, it's on my list of things to do.

---

### Post by Nick_C on 2012-02-05
Now I am getting a bit confused, does KVM work fully on Ubuntu Server install or not?

Seems to me I have various choices but don't know what the differences are between them:

1). Install from Minimal CD - but does this allow the option to actually do a minimal install or does it just do the same as full install except downloading all the accessories at install time, this is unclear from the documentation.

2). Install Command Line Interface from desktop CD (ubuntu-11.10-desktop-amd64.iso)

3). Install Command Line Interface from full DVD (ubuntu-11.10-dvd-amd64.iso)

4). Ubuntu Server

After any of these I will then need to install a GUI to get started.  So which is the best option or are they all the same?

What does 'Expert mode' do during install, that doesn't allow deselection of components does it?

---

### Post by jerrrys on 2012-02-05
I run 11.10 and vBox.

Want to keep it (host) a little lite and still have a good desktop to work with?

Do a terminal install (CLI) and:

sudo apt-get install --no-recommends ubuntu-desktop && sudo apt-get install gnome-session-fallback

[http://packages.ubuntu.com/oneiric/ubuntu-desktop](http://packages.ubuntu.com/oneiric/ubuntu-desktop)

Edit: will your box support KVM?  In terminal enter:

kvm-ok

Edit#2:  Also check BIOS (intel looks like this):

[ATTACH]212097[/ATTACH]

---

### Post by Nick_C on 2012-02-06
> **collisionystm said:**
> you do not want to use Ubuntu-Desktop version because of the kernel. If you choose to go that route, install the server kernel post install.

If it were me I would

Install 10.04 LTS server

Install LXDE for a gui

sudo apt-get install lxde

Install Virtual machine manager

Have fun.

ok have now done

[INDENT]Install 11.10 server

sudo apt-get install lxde
[/INDENT]

All boots up fine into Lxde desktop.  However the most obvious thing I notice is no apparent support for dual monitors, they are both just cloned no way that I can see to spread the desktop across both monitors.

---

### Post by Nick_C on 2012-02-06
Now gone back to standard ubuntu desktop

[INDENT]sudo apt-get remove lxde

sudo apt-get install --no-install-recommends ubuntu-desktop[/INDENT]

As mentioned in a different thread this now freezes at:
[INDENT]Stopping System V runlevel compatibility [ok][/INDENT]

So have installed nVidia driver

[INDENT]sudo apt-get install nvidia-current[/INDENT]

but same problem freezes at
[INDENT]Stopping System V runlevel compatibility [ok][/INDENT]

So tried adding nomodeset to Linux calling line in grub, no goes further but freezes at
[INDENT]PulseAudio configured for per-user sessions[/INDENT]

Any ideas where I can go from here or do I just conclude that for the moment, at least in my case, Ubuntu just doesn't work so I will have to look elsewhere for an OS to be the virtualization host.

---

### Post by Rebelli0us on 2012-02-06
Running host 64-bit Ubuntu 10.10 vanilla Desktop installation. Guests are Win7 x64, Win8 Preview x64, Windows 2000 Professional. All guests work very well -- sometimes all 3 guests simultaneously.

---

### Post by japzone on 2012-02-06
> **Nick_C said:**
> Now gone back to standard ubuntu desktop

[INDENT]sudo apt-get remove lxde

sudo apt-get install --no-install-recommends ubuntu-desktop[/INDENT]

As mentioned in a different thread this now freezes at:
[INDENT]Stopping System V runlevel compatibility [ok][/INDENT]

So have installed nVidia driver

[INDENT]sudo apt-get install nvidia-current[/INDENT]

but same problem freezes at
[INDENT]Stopping System V runlevel compatibility [ok][/INDENT]

So tried adding nomodeset to Linux calling line in grub, no goes further but freezes at
[INDENT]PulseAudio configured for per-user sessions[/INDENT]

Any ideas where I can go from here or do I just conclude that for the moment, at least in my case, Ubuntu just doesn't work so I will have to look elsewhere for an OS to be the virtualization host.

I'd recomend just giving Ubuntu Desktop a try(You may want to use 11.04 for the Classic Gnome UI) Just make sure you select "Ubuntu Classic (No Effects)" while logging in to cut out Eye Candy that slows things down. I run 11.04 and VB works fine. 

Server Installs are always more of a headache to Setup and get working right as they're pretty bare bones and can be missing many drivers and binaries that the Programs you want to run need. Hence the need to figure out what's needed and install it all manually. Many times it's not worth it unless you sepcifically need a Server or are trying to use an Old outdated PC.

---

### Post by Nick_C on 2012-02-07
Problem is I just can't see how to do a plain Desktop install without the associated rubbish - Office, Browser, media accessories etc. For a virtualization host we need to minimize the attack area by only installing the minimum necessary.

If only there were a way of choosing what additional non-essential components to install.

---

### Post by japzone on 2012-02-07
If you're still having problems you should look into using another Distribution. If you really want Light-Weight but want to stick with the Ubuntu core, I'd recommend [**Lubuntu**]("http://lubuntu.net/"). It is very Low-Resource and only includes Light-Weight Programs like Abiword, Chromium, and a few others. Leaving them Installed won't hurt you but you can uninstall what you don't want/need. Lubuntu is very Low-Resource, I've installed it on an Old Windows95 PC and it was running smoother than Windows95 did, playing Youtube and Hulu Videos, Downloading Torrents, and Playing Standard Def videos no problem(Obviously there's no way a 15 year old Graphics card could play HD). I'd Imagine it'll run like Lightning on a more recent Computer but I have yet to install it on one. I've run it in LiveCD mode for my repair Jobs(Works great for that) on Computers that came with Windows 7 and it ran real fast and smooth even then. VirtualBox should Install no Problem in it and you can use any Ubuntu Repository or DEB to get anything else you need.

---

### Post by collisionystm on 2012-02-07
> **Nick_C said:**
> Problem is I just can't see how to do a plain Desktop install without the associated rubbish - Office, Browser, media accessories etc. For a virtualization host we need to minimize the attack area by only installing the minimum necessary.

If only there were a way of choosing what additional non-essential components to install.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Rebelli0us on 2012-02-07
> **japzone said:**
> If you're still having problems you should look into using another Distribution. If you really want Light-Weight but want to stick with the Ubuntu core, I'd recommend [**Lubuntu**]("http://lubuntu.net/"). It is very Low-Resource and only includes Light-Weight Programs like Abiword, Chromium, and a few others. Leaving them Installed won't hurt you but you can uninstall what you don't want/need. Lubuntu is very Low-Resource, I've installed it on an Old Windows95 PC and it was running smoother than Windows95 did, playing Youtube and Hulu Videos, Downloading Torrents, and Playing Standard Def videos no problem(Obviously there's no way a 15 year old Graphics card could play HD). I'd Imagine it'll run like Lightning on a more recent Computer but I have yet to install it on one. I've run it in LiveCD mode for my repair Jobs(Works great for that) on Computers that came with Windows 7 and it ran real fast and smooth even then. VirtualBox should Install no Problem in it and you can use any Ubuntu Repository or DEB to get anything else you need.

I tried Lubuntu in VM, it's lean and mean but I couldn't install it in my old Thinkpad:

[http://ubuntuforums.org/showthread.php?t=1895696]("http://ubuntuforums.org/showthread.php?t=1895696")

any ideas?

---

### Post by japzone on 2012-02-07
> **Rebelli0us said:**
> I tried Lubuntu in VM, it's lean and mean but I couldn't install it in my old Thinkpad:

[http://ubuntuforums.org/showthread.php?t=1895696]("http://ubuntuforums.org/showthread.php?t=1895696")

any ideas?
That Model of Thinkpad had a Maximum of 128mb of RAM and had a 266MHz processor. Thinkpads were designed for Buisness and not much else. The PC I installed Lubuntu on had some slightly better specs because it wasn't limited by the Laptop CPUs of the Time. The default ISO for most Distributions doesn't support the Specs of that Laptop. Instead follow the Directions below to try an Alternative way of Installing Lubuntu on Low-End PCs. 

First go [**Here**]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A11.10") and Download the "Alternate" ISO. Burn it to a CD-R(Not RW) and Install using that. If that doesn't work try the "Minimal" ISO. 

If you still have trouble you'll need to go for an even more Light-Weight OS like PuppyOS or read this Article:[http://www.makeuseof.com/tag/6-lightweight-linux-distributions-give-pc-lease-life/]("http://www.makeuseof.com/tag/6-lightweight-linux-distributions-give-pc-lease-life/")

---

### Post by Pengwyn44 on 2012-02-08
I am running the standard Desktop 11.10 version loaded from the  Linux Format magazine DVD. Virtual Box works fine as long as you download the program from the Oracle web site and not from the Software Center. Install with dpkg. The extension package is also from Oracle and must be the same version number. It is installed by the VBox program. There is a mismatch between the Oracle extension package and the Virtual Box supplied by the Software Center.

---

### Post by Nick_C on 2012-02-08
> **collisionystm said:**
> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Just tried installing from mini.iso.
At software select I select:
[INDENT]Virtual Machine Host
Ubuntu-desktop[/INDENT]

Unfortunately that fails with
[INDENT]Installation step failed - Select and install software[/INDENT]
Tried rerunning that step a few times but same error everytime.
...
Now decided to uncheck the Virtual Machine Host option and install is now continuing.

---

### Post by linux6994 on 2012-02-08
I found Lubuntu only used 169mb of ram running lean, then using VBox for VMs worked really well.:)

---

### Post by collisionystm on 2012-02-08
> **Nick_C said:**
> Just tried installing from mini.iso.
At software select I select:[INDENT]Virtual Machine Host
Ubuntu-desktop[/INDENT]Unfortunately that fails with[INDENT]Installation step failed - Select and install software[/INDENT]Tried rerunning that step a few times but same error everytime.
...
Now decided to uncheck the Virtual Machine Host option and install is now continuing.


Another distro to consider...

Zentyal.

You can handle your VM's from a web interface. It is ubuntu server 10.04. It install with LXDE as the GUI and includes the web interface. Its pretty slick.

---

### Post by Nick_C on 2012-02-08
> **Nick_C said:**
> Just tried installing from mini.iso.
At software select I select:
[INDENT]Virtual Machine Host
Ubuntu-desktop[/INDENT]

Unfortunately that fails with
[INDENT]Installation step failed - Select and install software[/INDENT]
Tried rerunning that step a few times but same error everytime.
...
Now decided to uncheck the Virtual Machine Host option and install is now continuing.

Install complete, boots to desktop ok.

But minimal install doesn't actually mean minimal install, just means network install!  I have ended up with not just ubuntu-desktop but stacks of unwanted accessoried as well: firefox, libre office etc.

Any idea how to get rid of these additions and just get a plain basic desktop installed without all of this unwanted crap.

---

### Post by CharlesA on 2012-02-08
I have done a basic gui on Lucid server before by doing a server install and running this:

```
sudo apt-get install xorg
```

```
sudo apt-get install gnome-core
```

Not sure if that works on the newer version though.

See here: [http://www.microswamp.com/?p=articles/technotes/article&rn=48](http://www.microswamp.com/?p=articles/technotes/article&rn=48)\

Also check here:
[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by japzone on 2012-02-08
> **Nick_C said:**
> Install complete, boots to desktop ok.

But minimal install doesn't actually mean minimal install, just means network install!  I have ended up with not just ubuntu-desktop but stacks of unwanted accessoried as well: firefox, libre office etc.

Any idea how to get rid of these additions and just get a plain basic desktop installed without all of this unwanted crap.

-Install Synaptic Manager if running 11.10+
```
sudo apt-get install synaptic
```
-Open Synaptic Manager
-Find any unwanted packages and Right-Click-->Select for Uninstall
-Once you've finished selecting all unwanted programs click the above Apply button.

I would recommend going with Lubuntu at this point if your PC has so much trouble with Ubuntu. Lubuntu has much less included even when doing a Full Install and includes Synaptic Manager.

---

### Post by Nick_C on 2012-02-09
> **japzone said:**
> -Install Synaptic Manager if running 11.10+
```
sudo apt-get install synaptic
```
-Open Synaptic Manager
-Find any unwanted packages and Right-Click-->Select for Uninstall
-Once you've finished selecting all unwanted programs click the above Apply button.

I would recommend going with Lubuntu at this point if your PC has so much trouble with Ubuntu. Lubuntu has much less included even when doing a Full Install and includes Synaptic Manager.

Ok thanks for that.  Synaptic now installed and working fine.  However there are literally hundreds of packages installed.

Any idea if there is a list anywhere of what packages are installed by default in Server?  If so I can try to stick to that and remove everything else.

Thanks

---

### Post by CharlesA on 2012-02-09
You did a minimal install of Ubuntu desktop then?

You could try either purging ubuntu-desktop and installing just the packages I mentioned above or reinstalling with the server version and running everything headless.

Are you going to be accessing the VMs from this machine or from over the network?

---

### Post by japzone on 2012-02-09
Just uninstall anything you don't think you need. Synaptic will have discriptions for most apps so if it doesn't seem important you can uninstall it. Just try to avoid things like lib*, ect...

Another option is to just try Lubuntu instead. You'd probably have a better time if you did.

---

