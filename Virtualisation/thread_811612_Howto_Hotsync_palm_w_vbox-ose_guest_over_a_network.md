---
title: "Howto: Hotsync palm w/ vbox-ose guest over a network"
date: 2008-05-29
forum: Virtualisation
---

### Post by abkrishna on 2008-05-29
Hello all,
Long time forum reader, but this is the first time I have an answer (however simple) rather than just find answers from way smarter people, so this is my first post. Apologies if it is in the wrong place.

_The Problem_: I have a Palm T|X, and want to hotsync it to a windows palm desktop because I use a few applications that require windows conduits and don't have linux alternatives (mostly medical applications). Of course, I don't have a windows machine running regularly and hate having to re-boot my server into XP just to hotsync. I have XP running beautifully under virtualbox-OSE, but without USB support it doesn't help me on the hotsync front.

_The Solution_: Fortunately, the T|X (and many other palm devices) allow hotsync over a network. Since I just got this set up and working (and didn't see any similar postings.. could be wrong about that.. big forum) I figured I'd post a little howto.

_The Hardware_: Dell M1330 laptop running Ubuntu Hardy (upgraded from an initial clean install of Gutsy, NOT the dell version). Virtualbox-OSE installed and running with a nearly clean install of Windows XP (just a few programs installed) using virtualbox's built in NAT networking, and shared folders to access my home directory. 

_The Setup_: From this point forward, all references to "XP" are referring to the guest operating system inside a virtualbox VM. I haven't tried this with any other version of windows, but since the modifications all all basically external to the guest os, it should still work. I'm going to assume the VM's name is "WinXP" in all relevant command lines, and that virtualbox's NAT networking is set up and functioning as the first network card (the default setup). I also assume (obviously) that you have a palm device that is capable of networking, and that you have that set up and running as well such that it is able to connect to your host computer over that network.

_The Steps_:
[LIST=1]
[*]Set up virtualbox to forward traffic on the hotsync ports through to your virtual machine. This must be done with the virtual machine OFF. Using 'vboxmanage' on the host, we will add commands to the virtual machine setup to tell vbox to forward TCP on ports 14237 and 14238 (the two used by hotsync). Note, according to Palm, it is TCP:14237 and UDP:14238, but I'm doing TCP on both and it seems to be working. Per virtualbox, UDP can be a bit unreliable, so I figure this is the more stable option so long as it works. The following commands will perform the setup necessary (taken with appropriate modifications from the virtualbox user's manual):
[FONT="Courier New"]
[LIST]
[*]vboxmanage setextradata WinXP "VBoxInternal/Devices/pcnet/0/LUN#0/Config/HotSync1/Protocol" TCP
[*]vboxmanage setextradata WinXP "VBoxInternal/Devices/pcnet/0/LUN#0/Config/HotSync1/GuestPort" 14237
[*]vboxmanage setextradata WinXP "VBoxInternal/Devices/pcnet/0/LUN#0/Config/HotSync1/HostPort" 14237
[*]vboxmanage setextradata WinXP "VBoxInternal/Devices/pcnet/0/LUN#0/Config/HotSync2/Protocol" TCP
[*]vboxmanage setextradata WinXP "VBoxInternal/Devices/pcnet/0/LUN#0/Config/HotSync2/GuestPort" 14238
[*]vboxmanage setextradata WinXP "VBoxInternal/Devices/pcnet/0/LUN#0/Config/HotSync2/HostPort" 14238
[/LIST]
[/FONT]
This forwards host tcp:14237 to guest tcp:14237 and the same for tcp:14238 for the virtual machine "WinXP" **Note the use of "HotSync1" in the first three lines and "HotSync2" in the second three.**. These are arbitrary labels, but do have to be different.

[*]If you are like me and have a restrictive linux firewall, you have to open both those ports on the INPUT chain of the host firewall. Note that (unlike what I recall of vmware) virtualbox handles it's networking independently of the host, so you don't have to do anything with the FORWARD chain:
[FONT="Courier New"]
[LIST]
[*]sudo iptables -A INPUT -p tcp --dport 14237 -j ACCEPT
[*]sudo iptables -A INPUT -p tcp --dport 14238 -j ACCEPT
[/LIST]
[/FONT]
You can obviously take whatever steps you'd like to make this permanent or activate / deactivate with the VM.

[*] Now, start up the VM, download and install palm desktop, skip the initial hotsync when hotsync manager first starts up. Whether you create a username or whatever depends on the state of your device. Ultimately, get Palm Desktop installed in the VM as you normally would in every way except doing the initial hotsync.

[*] Right-click on the hotsync icon and enable network hotsync (I also disabled local USB, but it doesn't really matter).

[*] On your device, enter hotsync. Select network hotsync and provide the IP address of your HOST computer. Hit go and you're off to the races. Hotsync manager on the XP VM should come up and ask for the username to synchronize and whatever else it needs for the initial hotsync, and you should be set.

[*] A note: when you are done, the hotsync manager on the palm device will show the name of the virtual machine. You **CAN NOT** sync to this, as it is associated with the INTERNAL IP of the guest OS. You'll need to pick your HOST computer's IP from the drop down menu each time you want to hotsync. To me, at least, that is a pretty insignificant price to pay to have everything else working.
[/LIST]

Okay, that's it. You hopefully should now have a full windows palm desktop running inside the VM whenever you need it that you can hotsync to for all those irritating conduits you can't sync from linux. Hope this is helpful to someone out there!

---

### Post by azulmarino on 2008-11-15
Just what I was looking for and found this right away and it works great. Thank you very much abkrishna :)

---

