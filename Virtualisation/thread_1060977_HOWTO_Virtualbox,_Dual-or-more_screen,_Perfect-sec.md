---
title: "HOWTO: Virtualbox, Dual-or-more screen, Perfect-security rdesktop, internal network"
date: 2009-02-05
forum: Virtualisation
---

### Post by Ng Oon-Ee on 2009-02-05
Hi all,

Been 2 days I've been looking into a way to get my Virtualbox virtual machine (VM) working on a separate-x-screen laptop. Now I can fire up Powerpoint and use presenter mode with a projector!

**_[SIZE="5"]INTRODUCTION[/SIZE]_**

So, to begin, here's the specific use-case I'm addressing:-
1. Running a single virtual machine (Windows XP)
2. Separate-x-screen setup within Ubuntu (will also work with twinview or different sides of a cube, but is REQUIRED for separate-x-screen)
3. Laptops (which normally don't have only one interface to the Internet), but works fine for desktops as well

Here's what you WON'T be able to do:-
1. Run any sort of hardware-accelerated tasks (not available on headless vrdp), including 3D GAMES
2. Seamlessly have windows and ubuntu apps side-by-side (there's a better guide for it, referred below)
3. That's about it, really.

**_[SIZE="5"]SOURCES[/SIZE]_**

I've "referred to" (read, copied unashamedly) from the following sources:-
1. [Seamless MS Windows on Hardy with VirtualBox and Beryl by ashmew2]("http://ubuntuforums.org/showthread.php?t=821461") - If you want seamless operation (just a start menu, with your Ubuntu desktop intact, and each window appears almost like an Ubuntu app), go to this guide.
2. [HOWTO: Perfect VirtualBox Integration (auto start, rdesktop on workspace 2, etc) by edmondt]("http://ubuntuforums.org/showthread.php?t=939183") - My HOWTO is similar to his, but has some improvements, and some things that are unimportant to me (auto-start and shutdown, etc.) I've skipped
3. [VBox 1.6 with XP guest multiple monitor]("http://forums.virtualbox.org/viewtopic.php?p=23324&sid=daeb5034c784f82237b2d408118b61d9") - Actually found information I needed from the person asking a question! The OP.
4. [Problem rotating cube with rdesktop/tsclient in fullscreen]("http://ubuntuforums.org/showthread.php?t=602442") - Post 5, by DasFx, mentions how to 'emulate' full-screen, but I've expanded on it
5. [host-only networking for VirtualBox by Giannis Tsakiris]("http://www.giannistsakiris.com/index.php/2007/11/01/host-only-networking-for-virtualbox/") - Exactly what the title says. I've added a Windows-based security tip.

**_[SIZE="5"]WHAT YOU'LL NEED[/SIZE]_**

I won't try to cover the simple stuff. Specifically, you'll need:-
1. A working Ubuntu (other Linux would be fine) install. Specifically, your wireless works (if you use it), your audio plays fine (preferably with Pulseaudio, 'cause that's what I use). If networking/audio does not work on host don't expect it to work in a VM.
2. A working VirtualBox install (OSE or PUEL is fine, both work the same for this purpose, though I think OSE may have different *lower-cased* commands than PUEL). VBox 2.1 is much better than anything older. Hint:- Kernel updates means "/etc/init.d/vboxdrv setup" needed. EDIT:- You may need to downgrade, read the 'fixes' section.
3. A working Windows XP VM (I'm sure it'll work with other Windows, but since I haven't tested them, YMMV).
4. Compiz working, if you're using this guide to have multiple monitors mapped to sides of your cube. No compiz = no cube, of course :p
4. Google. Searching Google will give you results much faster and with less effort from both you and others compared to posting a question here. That said, please post if you're unsure on something, just know that it'll take a while for replies to be forth-coming.

**_[SIZE="5"]THE HOWTO ITSELF[/SIZE]_**

So, you want dual-screen VirtualBox? Here's the possible situations:-

SITUATION A - I use two separate x-screens, and my VBox is limited to only one of them.
SITUATION B - I use TwinView, and my VBox sees the whole thing as one screen if I maximize it. This means full-screen apps don't work properly (cover both screens) and I can't maximize just to one screen easily.
SITUATION C - I may or may not use dual-screen, but wouldn't it be cool if VBox could see some of my cube-sides (or virtual desktops) as separate screens?

So, the VirtualBox solution for all these situations is what's called a headless VM. Basically, your VM runs, and that's it, no GUI (that you can see), its just running. This, in combination with the Remote Desktop protocol used in Windows XP (and others), means you can log in 'remotely' to the headless VM, in much the same way you'd use Remote Desktop to control a PC through a LAN or over the internet. VirtualBox even does virtual dual-screens, if you connect remotely twice with slightly different parameters. VMWare what? :lol:

[SIZE="3"]**Setting up the virtual interface**[/SIZE]

First, let's setup a virtual network interface within Ubuntu, so that there's a totally private network without any other machines through which the Remote Desktop connection can be channeled. Activating Remote Desktop can be a security risk over a network where other machines can potentially access yours freely.

You'll need the uml-utilities package.
```
sudo apt-get install uml-utilities
```

Then, you'll have to create the interface itself. Replace my name (ngoonee) with your own user-name, the one you use to login to your machine.
```
sudo tunctl -t tap0 -u ngoonee
```

Assign an IP address to your virtual interface. It should NOT clash with the LAN IP address you have in your home network or office network. Use the below, changing the THIRD number if needed (don't change the first or second).
```
sudo ifconfig tap0 10.0.1.1
```

You'll need to assign proper permissions to the interface to all users of virtualbox
```
sudo chgrp vboxusers /dev/net/tun
sudo chmod 660 /dev/net/tun
```

Make sure you're a member of the vboxusers group, by going to System->Administration->Users & Groups. Click 'Unlock' and 'Manage Groups', find the vboxusers group, click 'Properties' and make sure you're listed there.

The 'tap0' interface will disappear after you logoff from Ubuntu. To make it come back every login, you need to edit rc.local:-
```
sudo gedit /etc/rc.local
```

You'll see from the comments that this file normally does nothing. If you've tweaked before you may have something here. In any case, just add these lines somewhere after the comments and before the 'exit 0'. Once again, replace my name (ngoonee) with your user name.
```
echo "Setting up tap0 interface..."
tunctl -t tap0 -u ngoonee
ifconfig tap0 10.0.1.1
```

[SIZE="3"]**VM Settings**[/SIZE]

Next, let's setup the VM itself so that Remote Desktop (vrdp) is allowed. First, startup VirtualBox (Applications->System Tools-> Sun xVM VirtualBox). Remember, you have to have an existing VM, if you don't, go create one (and find another HOWTO for that).

Here's the settings you'll need:-
General
[INDENT]->Basic
[INDENT]->Base Memory Size = enough to comfortably run the VM. At least 500MB for WinXP
->Video Memory Size = put this one high, each extra monitor costs some video memory. I just max it.
->Enable 3D Acceleration = off or on is fine, but you won't be able to use it in headless mode[/INDENT][/INDENT]
Audio
[INDENT]->Enable Audio = tick it, of course
[INDENT]->Host Audio Driver = I use PulseAudio, you should too. Go [here]("http://ubuntuforums.org/showthread.php?t=843012") if you have problems with this. However, ALSA/OSS should still work.[/INDENT][/INDENT]
Network (You have up to 4 adapters. Use one for each of your wireless/LAN that is used to connect to the Internet. Use one more for your private connection within your machine. The order is NOT important, but take note of it.)
[INDENT]->Adapter 1 (I'm assuming you'll assign this to your ethernet connection)
[INDENT]->Enable Network Adapter = tick this
->Adapter Type = PCnet-FAST III (Am79C973), I've found this to work well with WinXP, and its the default
->Attached to = Host Interface
->Cable Connected = tick this
->Host Interfaces = select eth0, that's normally your ethernet card[/INDENT]
->Adapter 2 (I'm assuming you'll assign wireless here)
[INDENT]->Enable Network Adapter = tick this
->Adapter Type = as above
->Attached to = Host Interface
->Cable Connected = tick this
->Host Interfaces = select wlan0, or eth1, or ath0, whichever is your wireless card[/INDENT]
->Adapter 3 (virtual internal connection)
[INDENT]->Enable Network Adapter = tick this
->Adapter Type = as above
->Attached to = Host Interface
->Cable Connected = tick this
->Host Interfaces = select tap0[/INDENT][/INDENT]
Shared Folders
[INDENT]->Just add whatever folders your machine will need to access, its the easiest way (easier than using SAMBA, of course). Please note that some users have reported bugs with deleting files from within the VM, but I've not had any problems yet. Make it permanent, since you don't really want to be adding it again and again.[/INDENT]
Remote Display
[INDENT]->Enable VRDP Server = tick this
[INDENT]->Server Port = 3389 (the default). You can use something else, but what I'm setting up is perfectly secure anyway, details later. Windows MAY need registry-hacking if you want to use something besides 3389 though, I haven't tried.[/INDENT][/INDENT]

To enable multiple monitors within the VM, run the following commands. The first command has no uppercase if you're using OSE, these commands are from my VBox which is PUEL. Replace 'WinXP' with the name of your VM. The first line allows multiple Remote Desktop connections (else a new connection kills the old one), the second allows 2 monitors, make more if you want.
```
VBoxManage modifyvm WinXP -vrdpmulticon on
VBoxManage modifyvm WinXP -monitorcount 2
```

[SIZE="3"]**Testing and setting up guest OS**[/SIZE]

So, that's the settings for your VM all done. Now, we need to start up our VM to do the following:-
1. Test that networking isn't not-working (geddit? ;))
2. Enable Remote Desktop.
3. Setup Windows Firewall to prevent any other access.
4. Setup the third virtual LAN's fixed IP address.
5. Extend your windows desktop to the additional monitors.
6. Optionally allow 32-bit remote desktop access.

You can test networking just using a browser to any webpage, or by pinging from command-line. If you have multiple possible network connections, try disabling them from the Control Panel one by one to make sure each of them allows you to access the Net. I'm assuming your network assigns settings via DHCP etc., if you need special settings then I assume you know how to do that yourself. Please do not touch Local Area Connection 3 as yet (the one for the virtual internal LAN).

To enable Remote Desktop, right-click on 'My Computer' (either on the Desktop or in Windows Explorer) and click Properties. Select the 'Remote' tab and click 'Allow users to connect remotely to this computer".

Go to your Control Panel and double-click 'Windows Firewall'. Make sure 'On (recommended)' is selected. Go to the 'Exceptions' tab, the item 'Remote Desktop' should be there and ticked. Click on it (make sure you don't un-tick it) and click the 'Edit' button. On the pop-up window, click 'Change scope'. Then, select 'Custom list' and input the following
```
10.0.1.0/255.255.255.0
```

Next, go to 'Network Connections' in the Control Panel, right-click and select 'Properties' on Local Area Connection 3. In the 'General' tab, scroll down to find 'Internet Protocol (TCP/IP)', select it (don't un-tick it), and click the 'Properties' button. Select the 'Use the following IP address' button, enter an IP address of 10.0.1.2 and Subnet mask of 255.255.255.0, the rest can be left blank.

Now, go to 'Display' in the Control Panel. Under the 'Settings' tab, you should see the additional monitors you previously added. Just click on monitors 2 and later, and select 'Extend my Windows desktop onto this monitor' individually.

Finally, if you want to, Windows defaults to 16-bit colour to save bandwidth for Remote Desktop. Unless your processor is crappy slow (in which case you shouldn't even be virtualizing Windows, of all things), this won't concern you, but the ugliness of 16-bit colour WILL. So, click on Start->Run, type in "regedit", and browse to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Contro l\Terminal Server\WinStations\RDP-Tcp. In the right hand pane, select the ColorDepth key and the right-click on it. Select Modify and change the “Value Data” field to 4.

You're done with your guest VM, now shut it down.

[SIZE="3"]**Scripts for running headless and accessing it**[/SIZE]

Now, having fully setup your guest and host OS, here's what needs to be done everytime you want to use your machine.
1. Start your headless VM.
2. Wait for login to finish (you should hear the 'login' sound from Windows), you can't connect to it before that.
3. Connect to the VM via rdp.
4. Connect to the VM AGAIN via rdp (for the 2nd desktop, once more for every desktop).

Here's a script I took from my sources (listed above) and modified pretty heavily. The script needs nmap installed, so first run:-
```
sudo apt-get install nmap
```
I have two copies, one for launching the VM (and creating the first connection), the second for creating the second connection to the VM, monitor two. Name the first one launchXP, the second one launchXPmon2. Of course, you can change to names to Godzilla and Obama, if you want....

launchXP.sh
```
#!/bin/bash
# launchXP.sh by waspbloke September 2008
# modified by ngoonee Feb 2009
#
# requires nmap (sudo apt-get install nmap)
#
# ORIGINAL SCRIPT FROM: http://ubuntuforums.org/showthread.php?t=904379&highlight=bash+ping
# edited by edmondt in: http://ubuntuforums.org/showthread.php?t=939183

# change these vars to reflect your own setup
GuestIP="10.0.1.1" #The external ip of the Virtual Machine
VMName="WinXP"
ScreenRes=$(xrandr -q| grep "*" |awk '{print $1;}')
RDPport="3389"

# check if VM is already running

# if no VMs running start the VM and wait for some time
if [ $(VBoxManage -nologo list runningvms | wc -l) = 0 ]; then
	VBoxHeadless -startvm $VMName -vrdp on &
	echo "Please wait, starting" $VMName "..."
	sleep 25
fi

# check if VM's RDP port is ready to connect
echo "VM started, scanning RDP port" $RDPport "..."

until [  "$RDPstate" = "open" ]
do
	# scan port 3389 and send output to file
	nmap -p $RDPport $GuestIP > ~/NMAPout
	# set RDPstate var if NMAP scan is successful
	RDPstate=$(awk '$RDPport && /(open)/ {print "open"}' ~/NMAPout)
	if [ ! $RDPstate ]; then RDPstate="closed"; fi
	echo "...RDP port is currently $RDPstate..."
	sleep 5
done

# now we can fire up rdesktop
echo "Launching rdesktop session..."
#You can launch in seamlessrdp mode if you want to...
rdesktop localhost:$RDPport -D -g $ScreenRes -z -x l -d @1 -K &


# clean up before exit
rm ~/NMAPout

exit 0
```

launchXPmon2
```
#!/bin/bash
# launchXPmon2.sh by ngoonee Feb 2009
# Based off launchXP by waspbloke Sep 2009
#
# requires nmap (sudo apt-get install nmap)
#

# change these vars to reflect your own setup
GuestIP="10.0.1.1" #The external ip of the Virtual Machine
VMName="WinXP"
ScreenRes=$(xrandr -q| grep "*" |awk '{print $1;}')
RDPport="3389"

# check if VM is already running

# if no VMs running start the VM and wait for some time
if [ $(VBoxManage -nologo list runningvms | wc -l) = 0 ]; then
	echo "No running VMs, please run launchXP script first"
else
	# check if VM's RDP port is ready to connect
	echo "VM started, scanning RDP port" $RDPport "..."

	until [  "$RDPstate" = "open" ]
	do
		# scan port 3389 and send output to file
		nmap -p $RDPport $GuestIP > ~/NMAPout
		# set RDPstate var if NMAP scan is successful
		RDPstate=$(awk '$RDPport && /(open)/ {print "open"}' ~/NMAPout)
		if [ ! $RDPstate ]; then RDPstate="closed"; fi
		echo "...RDP port is currently $RDPstate..."
		sleep 5
	done

	# now we can fire up rdesktop
	echo "Launching rdesktop session..."

	#You can launch in seamlessrdp mode if you want to...
	#Second monitor always launched full-screen
	rdesktop localhost:$RDPport -D -g $ScreenRes -z -x l -d @2 -K &
	
	# clean up before exit
	rm ~/NMAPout
fi

exit 0
```

So, if you're already tired of reading, all you have to do is make the scripts executable, like this:-
```
chmod +x [/path/to/the/script]
```
Do this once for each script. Then run launchXP.sh in the workspace/monitor where you want the primary monitor to show, and launchXPmon2.sh in the workspace/monitor where you want the second monitor to show. The rdesktop window will be pseudo-full-screen, and will not be decorated by compiz. Always remember to SHUT DOWN windows yourself before closing the last rdesktop window, or when you shut down Ubuntu you'll just be pulling the plug on poor windows. And you know what happens when you do that too often, virtual machine or no...

If you want to know what's going on, or change how it works, read on....

[SIZE="3"]**The scripts explained**[/SIZE]

The first part (after the introductory comments) contains the variables for the program. GuestIP really should be 10.0.1.2, the IP of the guest OS, but that doesn't work on my system where 10.0.1.1 does. Funny, but I suppose there is an explanation. Only change this if you used different IPs previously, remember both IPs must be on the same subnet (the host/guest). VMName is "WinXP" for me, put your VM's name there. ScreenRes takes the form "1280x800" or "1024x768". The command there is simply to take the resolution of the current display. I'm not sure how it works on TwinView displays, it may not work so well in those cases, if someone could test it out I'll edit this. RDPport is 3389 by default, you can change it if you want but shouldn't need to bother.

So, first we check whether the VM is running by listing the running VMs and counting them. If the count is 0, no VMs are found. In this case, the VM is launched by the first script. The second script just exits. After launching a 'sleep' is put in, because Windows takes time to boot (25s is too short, but no harm in being optimistic I say! Depends on your processor/IO).

Next, nmap is used to scan the particular IP and port, the 'awk' basically checks if the port is open. If its not, then the loop loops back on itself, after a 5-second sleep. This loops infinitely till the port opens. I really should modify it to quit after a certain number of times, anyone know how to do that? I'm lazy :)

The final launching of rdesktop has quite a few options. "man rdesktop" should explain them all, with a lot of extras, but here goes my simple explanations:-

-D -> this option tells your window manager (metacity/compiz/kwin) not to decorate the window. Meaning, it doesn't get a border or titlebar etc. This is because the VM gets the resolution of your screen, so an additional border/titlebar means a bit of it is off the bottom and can't be accessed. Normally the same bit that contains your 'Start' button... :p So, with -D and the full-screen resolution, your entire monitor looks like its running Windows. Good or bad, I won't say.

-g <resolution> -> Obviously, sets the resolution of the rdesktop window. You'll need to manually set the resolution within the guest OS to match this, though. If you set this resolution too small it might make things hard (hard to click on something you can't see).

-z -> The man-page says 'enables compression of the RDP datastream'. Compression = less bandwidth required = good, case closed.

-x l -> Changes bandwidth performance to 'lan', the fastest (highest bandwidth), meaning the Themes, Animations, Incremental dragging, all show as if you were in the OS itself. Which you are, actually.

-d @1 -> This is the line which specifies which monitor you're accessing. If you have a RDP domain, append @1 after that name. Most users won't, so just put @1 to access the first monitor, @2 for the second, etc.

-K -> Do not override window manager key bindings. Doesn't work too well, rdesktop keeps grabbing my focus anyway. Workaround for this in the 'fixes' section. (EDIT: works with downgrade to the appropriate version. Seems this is a recent regression)

[SIZE="5"]**_Fixes_**[/SIZE]

So, so far I have two issues with this setup.

Firstly, a general VirtualBox issue. The reason I'm using separate x-screens is because I want different resolutions across my screens. VirtualBox doesn't seem to play very nicely with this though, there's no way to individually adjust the available resolutions within the guest OS. However, running the line below (replace WinXP with your VM name):-
```
VBoxManage controlvm "WinXP" setvideomodehint 1280 800 32 0
```
makes the 1280x800 mode available, and my other monitor resolutions are easily available (1024x768, 1280x1024). Your windows monitors CAN have different resolutions, but different CUSTOM resolutions prove a bummer. One thing you can do using this is to define a resolution which covers all but your gnome-panel. You'll have to modify the rdesktop lines above, as well, but the result would be quite 'good' integration. Not as good as the method using 'seamlessrdp' in the Sources section though.

EDIT: The original text here is shown in the quote below. However, I just read[this bug report]("https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/270997") and it appears that this particular problem is a regression with the VBox version currently downloadable from Sun. Go to the bug report and read up on it, or download one of these files depending on your architecture. Use this in place of the previous installation (remember to uninstall first).
[i386 version]("http://ubuntu.interlegis.gov.br/ubuntu/pool/main/r/rdesktop/rdesktop_1.6.0-0ubuntu2_i386.deb")
[amd64 version]("http://ubuntu.interlegis.gov.br/ubuntu/pool/main/r/rdesktop/rdesktop_1.6.0-0ubuntu2_amd64.deb")

Now, alt-tab and ctrl-alt-arrow key work as if you're in Ubuntu. The only downside is that alt-tab does not work within the guest OS, so if you're running a lot of programs there, I suggest disabling alt-tab for Ubuntu (your host), it will then be passed to the guest OS.

> Secondly, sometimes you're 'trapped' in your VM. There's three workarounds. First, the easier, but less reliable one, is to press Ctrl-Alt-Enter (fullscreen) twice, which makes it full-screen and then cancels full-screen. After that, try to Ctrl-Alt-Right for your cube turn or similar. Just get out of that cube face =). Second, the easiest, perfectly reliable, but not always possible one is simply to move your mouse to your other monitor, click on something, then move it back, DON'T click, and spin your cube however you want. Or alt-tab. This doesn't always work, for example you may have two full-screen rdesktop windows, one in each monitor.

The third, harder, and perfectly reliable workaround is to bind some combination of mod-keys and mouse behaviour to the 'window minimize' behaviour in Compiz. In the Compiz Configuration Settings Manager (sudo apt-get install compizconfig-settings-manager), go to General, the Key-bindings tab, and add something to the Minimize Window shortcut (the mouse-driven one, not the keyboard-driven). I use <Super>Button3, meaning if I hold my Windows (Super) key down and right-click, the rdesktop window minimizes.

The problem here is that rdesktop does not have a 'release focus' shortcut (there's a patch for it though, I have not tried that yet, will wait for it to be incorporated in the repos if ever), and once you start typing in the VM, all your normal Alt-tab or Ctrl-Alt-something shortcuts are sent to your guest instead of your host. However, mod-keys+mouse buttons still get processed by your host first before going to guest, meaning we can use them to get back to the host OS.




So, that's my guide. Hope you enjoyed it. Please ask if you have any questions (first to Mr. Google, then to me, if you please).



Edit on 09-02-2009 - Added regression notice and download link to previous version prior to regression

---

