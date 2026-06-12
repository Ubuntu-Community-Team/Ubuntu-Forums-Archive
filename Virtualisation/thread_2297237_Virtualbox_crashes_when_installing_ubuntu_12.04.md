---
title: "Virtualbox crashes when installing ubuntu 12.04"
date: 2015-10-02
forum: Virtualisation
---

### Post by Kilarin on 2015-10-02
My computer: HP Pavilion a1600n AMD Athlon 64 X2 Dual core Processor 3800+ 2.00 GHz 2965MB of Ram, NVIDIA GeForce 6150LE graphics card
I'm running Xubuntu 14.04.3
I have VirtualBox 4.3.30 r101610
I'm trying to create a virtual machine with Ubuntu 12.04 precise installed.  I have download
09eb43dcfce2b7246bdd6e8108e755df  ubuntu-12.04.5-desktop-i386.iso
and
48b4edf237c489eebbfef208c2650d11  ubuntu-12.04.5-desktop-amd64.iso
(md5 sums included to show that my iso images are just fine)

I followed a process just like it indicates here: [https://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox](https://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox)
new/type=linux/version=ubuntu 64bit
memory=1000mb
create a virtual hard drive/vdi/dynamically allocated/12GB
start
select ubuntu-12.04.5-desktop-amd64.iso
start

And I get the purplish window with nothing on the screen except at the bottom the "keyboard = the little man in the circle".  It stays there for about 10 seconds, then suddenly switches to a wider black screen with a flashing cursor for a few seconds.  
then it dies.

my VBoxSVC.log shows:
```
00:32:39.732597 nspr-4   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:39.735651 nspr-4   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:40.307439 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:40.311508 nspr-5   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:40.360247 nspr-4   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:40.387868 nspr-3   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:40.391954 nspr-5   Load [/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86/VBoxHostWebcam.so] rc VINF_SUCCESS
00:32:40.414839 nspr-4   ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={480cf695-2d8d-4256-9c7c-cce4184fa048} aComponent={SessionMachine} aText={Saved screenshot data is not available (VERR_NOT_SUPPORTED)}, preserve=false
00:32:40.418783 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:40.468206 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:52.752853 nspr-2   NetIfAdpCtlOut: VBoxNetAdpCtl: Error while retrieving link status for vboxnet0: VBoxNetAdpCtl: ioctl failed: Operation not supported
00:32:53.031107 nspr-5   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:53.117870 nspr-4   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:53.120241 nspr-4   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:53.601588 nspr-6   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:32:53.604577 nspr-6   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
--
00:33:17.392786 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:33:17.395567 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:33:17.670462 Watcher  Reaper: Pid 8047 (1f6f) was signalled: 11 (0xb)

```

With the -- being right before the crash occurred.  I don't find this log to be particularly helpful. :)

I've tried the same thing with the 32bit install (selecting the i386 iso and ubuntu 32bit), with exactly the same results.
I even tried downloading some pre-made ubuntu 12.04 virtual machines, and they crash almost as soon as I start them.

Strange thing is, I have a windows xp virtual machine that I run in virtual box all the time, and it works just fine.

If anyone can help me through this, I would be VERY grateful.

---

### Post by SeijiSensei on 2015-10-02
> You can change this by adding your user to the 'vboxusers' group.
On the host, run the command
```
sudo adduser username vboxusers
```
replacing "username" with your login name.  Any better?

---

### Post by Kilarin on 2015-10-02
[quote="SeijiSensei"]On the host, run the command
sudo adduser username vboxusers
replacing "username" with your login name. Any better? [/quote]
Thanks for the help, but no luck. 
```

$ sudo adduser donald vboxusers
[sudo] password for donald: 
Adding user `donald' to group `vboxusers' ...
Adding user donald to group vboxusers
Done.

```

Same crash.  odd thing, it didn't even get rid of the usb warning.  After adding my username to vboxusers I still get:
```
0:05:36.229302 nspr-5   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:05:36.232340 nspr-2   WARNING [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={93269330-48ca-4096-b4a2-1189df336267} aComponent={Host} aText={VirtualBox is not currently allowed to access USB devices.  You can change this by adding your user to the 'vboxusers' group.  Please see the user manual for a more detailed explanation}, preserve=true 
00:05:36.303315 Watcher  Reaper: Pid 3130 (c3a) was signalled: 11 (0xb)

```
I hadn't bothered with trying to fix the usb problem yet because I wasn't actually trying to hook the virtualbox up to a usb device.  I didn't even have the virtualbox up and running yet.  Do you think that is actually related?  Like I said, I can STILL bring up my windows xp virtual box and operate it without any problems whatsoever.

---

### Post by SeijiSensei on 2015-10-02
Have you checked the integrity of the ISO file?  Maybe it is corrupted.

I assume you're running 64-bit Xubuntu, yes?  You cannot install a 64-bit guest on a 32-bit host.

Also make sure you have enabled VT-x and any other virtualization features in the BIOS.

---

### Post by Kilarin on 2015-10-03
[quote="SeijiSensei"]Have you checked the integrity of the ISO file? Maybe it is corrupted.[/quote]
Yep, thats why I included the md5checksums above.  The iso files check out exactly as they should.

[quote="SeijiSensei"]I assume you're running 64-bit Xubuntu, yes? You cannot install a 64-bit guest on a 32-bit host.[/quote]
I didn't know that, thank you for the info!  I'm running 32bit xubuntu, but I DID test with the 32bit guest and iso, and it still crashes.  log output below:

```
00:01:48.442024 nspr-5   Load [/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86/VBoxHostWebcam.so] rc VINF_SUCCESS
00:01:48.464096 nspr-3   ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={480cf695-2d8d-4256-9c7c-cce4184fa048} aComponent={SessionMachine} aText={Saved screenshot data is not available (VERR_NOT_SUPPORTED)}, preserve=false
00:02:06.527907 nspr-3   NetIfAdpCtlOut: VBoxNetAdpCtl: Error while retrieving link status for vboxnet0: VBoxNetAdpCtl: ioctl failed: Operation not supported
00:03:03.828807 Watcher  Reaper: Pid 3019 (bcb) was signalled: 11 (0xb)

```

[quote="SeijiSensei"]Also make sure you have enabled VT-x and any other virtualization features in the BIOS. [/quote]
Since I can open and run my windows xp virtualbox wouldn't that indicate that everything is set fine in the bios already?  Or am I misunderstanding something important?

---

### Post by Kilarin on 2015-10-18
My other virtualbox machine crashed, and would not restart.  In desperation, I finally reinstalled virtualbox:

sudo sh -c 'echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" >> /etc/apt/sources.list.d/virtualbox.list'

wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

(I then had to do: sudo vi /etc/apt/sources.list.d/virtualbox.list
and remove the line:
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty contrib non-free
that had been there previously.  So the end result was the same as if I had just edited virtualbox.list and removed "non-free" from the end.
)

sudo apt-get update; sudo apt-get install virtualbox

AND, now I've got version 4.3.10_Ubuntu

its actually an older version than I had before, but apparently this one runs fine.
I was able to restore my windows virtual machine, and get the ubuntu precise machine up and running.

thanks for the help!

---

