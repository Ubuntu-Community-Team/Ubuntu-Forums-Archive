---
title: "VMware Server + USB + Smartphone/Active Sync(WM5)"
date: 2007-12-23
forum: Virtualisation
---

### Post by TechMansoor on 2007-12-23
Ubuntu Gutsy
3.0 p4 - hyperthreaded
1 gig memory
Windows XP VmwareServer Share


OK. So from what I can tell, VMwareServer recognizes my usb device. At the top when you go to 'VM', and then you click on 'Removable Devices', finally you click on usb(its typically blank first), I unplug my device then re-plug the device(moto q - wm5) and it shows. Ater this I can click on the now shown windows mobile ndis device  and you can see the device being somewhat recongized by Windows XP(vmwareserver im running from gutsy). I mean if you guys aren't use to these smart devices, it typically shows like a network finding an ip address in the bottom right hand corner.

Ok so, now ActiveSync is running on the vmware share but it can't find my device for some reason.

Things I've done:

Gone into device manager, and I don't see my device anywhere.
-It actually should come up as a network adapter(windows mobile device #2 - or whatever number).

So ultimately I believe my device still is not being reconigzed on  the VmwareServer(free edition) share.

Can you advanced brothers suggest anything? I heard from somewhere that VmwareServer doesn't support usb 2.0 devices, but that couldn't be true if it is somewhat recognizing my device at least in the console interface right?

Also just to let you guys know...no matter what anyone says...

VirtualBox Ose does not have an option for usb!!!! :(

---

### Post by TechMansoor on 2007-12-23
Ok. So to sort of bring some solidification to the problem, my device is being recognized. But, it's only being recongized for a second. In the VMware Server console it shows my device under 'usb', and then it leaves. Under the XP Vmware Server install, when I hook my device up to it, it pops up in device manager and then leaves as well. So essentially, I'm only getting it to be recognized for a short second via the VMServer Console as well as the VMware Server Insall....

Anyone?

Thanks a billion guys in advance...:)

---

### Post by basotl on 2007-12-23
> TechMansoor wrote:
Ubuntu Gutsy
3.0 p4 - hyperthreaded
1 gig memory
Windows XP VmwareServer Share


OK. So from what I can tell, VMwareServer recognizes my usb device. At the top when you go to 'VM', and then you click on 'Removable Devices', finally you click on usb(its typically blank first), I unplug my device then re-plug the device(moto q - wm5) and it shows. Ater this I can click on the now shown windows mobile ndis device and you can see the device being somewhat recongized by Windows XP(vmwareserver im running from gutsy). I mean if you guys aren't use to these smart devices, it typically shows like a network finding an ip address in the bottom right hand corner.

Ok so, now ActiveSync is running on the vmware share but it can't find my device for some reason.

Things I've done:

Gone into device manager, and I don't see my device anywhere.
-It actually should come up as a network adapter(windows mobile device 2 - or whatever number).

So ultimately I believe my device still is not being reconigzed on the VmwareServer(free edition) share.

Can you advanced brothers suggest anything? I heard from somewhere that VmwareServer doesn't support usb 2.0 devices, but that couldn't be true if it is somewhat recognizing my device at least in the console interface right?


Which version of VMware Server are you using? It only began support for **USB 2.0 with VMware Server 2.0 Beta**. This maybe a simple issue of upgrading to the next version. Then again it is in it's beta stage for USB 2.0 support, so if you have the beta version and getting those errors, it **may** improve as they clean up the code. 


> TechMansoor wrote:
Also just to let you guys know...no matter what anyone says...

VirtualBox Ose does not have an option for usb!!!! :(

VirtualBox **OSE** does not support USB 2.0. I haven't heard of anyone saying it does.

On the other hand the **regular non OSE** version of VirtualBox supports USB 2.0. I use it all the time with my Linksys CIT200 with Skype on Windows XP.

---

### Post by TechMansoor on 2007-12-23
I was close, but I think this issue is officially beyond my knowledge now. Ok, so I found an article that directly corresponds to my issue:

[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=2&docTypeID=DT_KB_1_1&dialogID=37744067&stateId=0%200%2037738712](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=2&docTypeID=DT_KB_1_1&dialogID=37744067&stateId=0%200%2037738712)


So now, it turns out to be officially a mounting usb issue with gutsy  and a few others. When I try both methods, it finds my moto q/usb/wm5 device,but then it keeps finding it. Meaning, it constantly is disconnecting and reconnecting as if I'm plugging and unplugging the device. :(:(:(:(:(:(

I'm officially stumped since their only possible solution still doesn't work for me..:(:(

Has anyone ever ran into a problem where you had problems mounting usb/proc?

Thank you and good day..

---

### Post by basotl on 2007-12-24
Well the issue related to that article has some related help docs in Virtual Box. I think some of the same fixes might help you with VMware.

[http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04]("http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04")

[http://www.blog.arun-prabha.com/2007/10/26/usb-not-working-with-virtualbox-in-ubuntu-7-10-gutsy-gibbon/]("http://www.blog.arun-prabha.com/2007/10/26/usb-not-working-with-virtualbox-in-ubuntu-7-10-gutsy-gibbon/")

---

### Post by TechMansoor on 2007-12-24
VirtualBox or Vmwareserver do not work with smartphones or usb..point blank and period!!!!!!!!!!!!!!!!!!!!!!!!If you can by some miracle get it to work, I gurantee you would have needed to work at least 3 days to make it work.....

I never thought I say this, even in an instance where my primary workstation and my job was concerned but, im so seriously considering moving back to Windows.....Definitely considering it for my workstation and possibly for my laptop...

I honestly never thought I'd say that again...

We can beat up Windows all we want,but when it comes to clear, clean, crisp, most of the time solidified answers to problems, they have it....You can't put that past those guys....

I'm honstly crying inside after fighting so long with this issue..Gutsy suppose to be the number 1 distro in Linux and it's basically having problems mounting usb ports...how ridiculous is that??????????????????????????!!!!!!!!!!!!!!!?????????????

---

### Post by bcorpus_jr on 2007-12-30
I'm a new Ubuntu user. I just recently installed Ubuntu 7.10, the Gutsy Gibbon.I've been using redhat flavor before Ubuntu. I'm also using vmware to access my Samsung blackjack smartphone. After I installed ubuntu, I found out that I cannot synchronize anymore with my smartphone. In vmware, the VM->Removable Devices->USB Devices does not list any usb devices. In the logs I find that when I plug in my smartphone, I get the following logs:

Dec 30 21:19:22 vulcan kernel: [ 1656.469948] usb 1-2.1: new full speed USB device using ohci_hcd and address 4
Dec 30 21:19:22 vulcan kernel: [ 1656.584161] usb 1-2.1: configuration #1 chosen from 1 choice
Dec 30 21:19:23 vulcan kernel: [ 1657.044931] usbcore: registered new interface driver cdc_ether
Dec 30 21:19:23 vulcan kernel: [ 1657.177322] eth1: register 'rndis_host' at usb-0000:00:02.2-2.1, RNDIS device, 80:00:60:0f:e8:00
Dec 30 21:19:23 vulcan kernel: [ 1657.178057] usbcore: registered new interface driver rndis_host


In the vmware.log, I find the following:

[FONT="Courier New"]The specified device appears to be claimed by another driver (rndis_host) on the host operating system which means that the device may be in use. To continue, the device will first be disconnected from its current driver.[/FONT]

The rndis_host driver has claimed the device first before the vmware did. In order to prevent rndis_host driver to be loaded, i put the following lines in the /etc/modprobe.d/blacklist:

blacklist cdc_ether
blacklist rndis_host

After this, i restarted my pc and restarted my smartphone. When i plugged-in my smartphone, i got this in the logs:

Dec 30 21:52:46 vulcan kernel: [  209.291152] usb 1-2.1: new full speed USB device using ohci_hcd and address 3
Dec 30 21:52:47 vulcan kernel: [  209.405320] usb 1-2.1: configuration #1 chosen from 1 choice

I then started vmware and I found my device was automatically detected and listed under VM->Removable Devices->USB Devices.

Synchronization now works and I'm back in business :) Editing the blacklist file is about the only thing i did to make vmware detect my smartphone using Ubuntu 7.10.


Bobby

---

### Post by TechMansoor on 2007-12-30
That is awesome for you brother. Congratulations. Can I  assume you had your smart phone successfully synced prior to installing ubuntu with Red Hat?

I actually tried what you mentioned worked for you in disabling those services or whatever. Still did the same f***ing thing! Constantly plugging and un-plugging my device. It basically would recognize my device, then unrecognize it in and endless loop. :(...

What would you suggest I do or what materials would you suggest I get in helping me understand this usb issue as a whole? I got a "A practical Guide to LInux" and I'm about to make some room for that in my schedule. But what would you suggest?

If you got your smart phone, (WM5 device?) working then I should be able to get my motoq(also wm5 device) to work as well!!!!!!!

---

### Post by bcorpus_jr on 2008-01-02
> **TechMansoor said:**
> That is awesome for you brother. Congratulations. Can I  assume you had your smart phone successfully synced prior to installing ubuntu with Red Hat?

I actually tried what you mentioned worked for you in disabling those services or whatever. Still did the same f***ing thing! Constantly plugging and un-plugging my device. It basically would recognize my device, then unrecognize it in and endless loop. :(...

What would you suggest I do or what materials would you suggest I get in helping me understand this usb issue as a whole? I got a "A practical Guide to LInux" and I'm about to make some room for that in my schedule. But what would you suggest?

If you got your smart phone, (WM5 device?) working then I should be able to get my motoq(also wm5 device) to work as well!!!!!!!

Yes i was using CentOS 4 before i installed ubuntu. In that distro i did not have this problem. 

If my setup worked, then there is a big probability that your motoq should also be synchronizing with the vmware. I'm using the following versions:

Ubuntu 7.10
VMWare 6.02 for Linux
Windows 2000 sp4
WM5 (Samsung blackjack)

Maybe the first thing to do is to backup your present configuration and revert them to their original settings (at least the part that has something to do with this problem). 

Insert your device to your computer and tail on the /var/log/messages. Can you also paste that portion of the log file that was added when you inserted your device?

How do you invoke vmware? I do 

sudo /usr/bin/vmware

this is to make sure i  don't have permission problems. Perhaps later, i can tinker with the permissions but at the moment I only want to make my smartphone  syncing work.

can you also tail the vmware.log and paste the relevant addition to the logs?

Bobby

---

### Post by TechMansoor on 2008-01-28
Jan 28 11:06:02 CSSMA kernel: [ 7251.677216] usb 6-2: new full speed USB device using ohci_hcd and address 21
Jan 28 11:06:02 CSSMA kernel: [ 7251.892639] usb 6-2: configuration #1 chosen from 1 choice
Jan 28 11:06:02 CSSMA kernel: [ 7251.895617] ipaq 6-2:1.0: PocketPC PDA converter detected
Jan 28 11:06:02 CSSMA kernel: [ 7251.899112] usb 6-2: PocketPC PDA converter now attached to ttyUSB0
techmansoor@CSSMA:~$


This is what happens when I plug up my wm5 device(motoq) to my ubuntu box. This is without vmwareserver running.

------------------------------------------------------------------------------------------


After doing a 'tail /var/log/messages -f' this is what I get:

Jan 28 11:11:30 CSSMA kernel: [ 7579.308371] usb 6-2: new full speed USB device using ohci_hcd and address 28
Jan 28 11:11:30 CSSMA kernel: [ 7579.523634] usb 6-2: configuration #1 chosen from 1 choice
Jan 28 11:11:30 CSSMA kernel: [ 7579.526607] ipaq 6-2:1.0: PocketPC PDA converter detected
Jan 28 11:11:30 CSSMA kernel: [ 7579.530121] usb 6-2: PocketPC PDA converter now attached to ttyUSB0
Jan 28 11:11:30 CSSMA kernel: [ 7579.566125] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Jan 28 11:11:30 CSSMA kernel: [ 7579.566160] ipaq 6-2:1.0: device disconnected
Jan 28 11:11:35 CSSMA kernel: [ 7584.912291] usb 6-2: USB disconnect, address 28
Jan 28 11:11:37 CSSMA kernel: [ 7586.461705] usb 6-2: new full speed USB device using ohci_hcd and address 29
Jan 28 11:11:37 CSSMA kernel: [ 7586.677213] usb 6-2: configuration #1 chosen from 1 choice
Jan 28 11:11:37 CSSMA kernel: [ 7586.680184] ipaq 6-2:1.0: PocketPC PDA converter detected
Jan 28 11:11:37 CSSMA kernel: [ 7586.683773] usb 6-2: PocketPC PDA converter now attached to ttyUSB0
Jan 28 11:11:37 CSSMA kernel: [ 7586.714179] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Jan 28 11:11:37 CSSMA kernel: [ 7586.714214] ipaq 6-2:1.0: device disconnected
Jan 28 11:11:42 CSSMA kernel: [ 7592.170708] usb 6-2: USB disconnect, address 29
Jan 28 11:11:44 CSSMA kernel: [ 7593.722976] usb 6-2: new full speed USB device using ohci_hcd and address 30
Jan 28 11:11:44 CSSMA kernel: [ 7593.938691] usb 6-2: configuration #1 chosen from 1 choice
Jan 28 11:11:44 CSSMA kernel: [ 7593.941650] ipaq 6-2:1.0: PocketPC PDA converter detected
Jan 28 11:11:44 CSSMA kernel: [ 7593.945314] usb 6-2: PocketPC PDA converter now attached to ttyUSB0
Jan 28 11:11:44 CSSMA kernel: [ 7593.975873] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Jan 28 11:11:44 CSSMA kernel: [ 7593.975908] ipaq 6-2:1.0: device disconnected
Jan 28 11:11:50 CSSMA kernel: [ 7599.368738] usb 6-2: USB disconnect, address 30
Jan 28 11:11:51 CSSMA kernel: [ 7600.920274] usb 6-2: new full speed USB device using ohci_hcd and address 31
Jan 28 11:11:51 CSSMA kernel: [ 7601.136305] usb 6-2: configuration #1 chosen from 1 choice
Jan 28 11:11:51 CSSMA kernel: [ 7601.139187] ipaq 6-2:1.0: PocketPC PDA converter detected
Jan 28 11:11:51 CSSMA kernel: [ 7601.142879] usb 6-2: PocketPC PDA converter now attached to ttyUSB0
Jan 28 11:11:51 CSSMA kernel: [ 7601.174353] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Jan 28 11:11:51 CSSMA kernel: [ 7601.174389] ipaq 6-2:1.0: device disconnecte


***Do you notice the loop in the kernel. Doesn't look like its explaining anything,but maybye one of you guys can tell. Bobby, thanks for the help so far, and I'm sorry I'm getting back to you so late. I'm ready to ink this problem if at all possible.

I'll do one more reply showing with vmware shows under its logs..

---

### Post by bcorpus_jr on 2008-01-29
Hi,

Based on the log file that you posted, I think the problem lies in the fact that LINUX grabs your motoq device before the vmware does. BTW, i'm not familiar with vmware server. I'm using vmware-player so I hope this discussion also applies to your case. 

It just so happened that I have an IPAQ 5450 pda and I can simulate your situation. When i plugged my ipaq to my desktop, this is the log snippet i got:
[INDENT][FONT="Courier New"]
Jan 29 23:04:40 vulcan kernel: [ 4496.439306] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
Jan 29 23:04:40 vulcan kernel: [ 4496.444985] ipaq 1-2.3:1.0: PocketPC PDA converter detected
Jan 29 23:04:40 vulcan kernel: [ 4496.469396] usb 1-2.3: PocketPC PDA converter now attached to ttyUSB0
Jan 29 23:04:40 vulcan kernel: [ 4496.470254] usbcore: registered new interface driver ipaq[/FONT][/INDENT]

Notice that it is very similar to the log snippet you posted. What the log file tells us is that LINUX recognized your motoq as an ipaq device and correspondingly installed the ipaq driver. 

We must prevent LINUX from doing this. We can go about this by "blacklisting" the ipaq driver in /etc/modprobe.d/blacklist. Edit this file by doing the following:

[INDENT][FONT="Courier New"]sudo vi /etc/modprobe.d/blacklist[/FONT][/INDENT]

and append the following line: 

[INDENT][FONT="Courier New"]blacklist ipaq[/FONT][/INDENT]

Here is a tail of my /etc/modprobe.d/blacklist file:

[INDENT][FONT="Courier New"]# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist cdc_ether
blacklist rndis_host
blacklist usblp
blacklist ipaq[/FONT][/INDENT]

Notice the entry on ipaq above. 

Now you need to reboot your machine for changes to take effect. You also reboot your motoq to initialize it.

Now it's time to plug in your motoq. But before that, open a console and do:

[INDENT][FONT="Courier New"]tail -f /var/log/messages[/FONT][/INDENT]

Plug your motoq device to the usb and see the logs. Here is a snippet of my log file when i plugged my device:

[INDENT][FONT="Courier New"]Jan 29 23:14:44 vulcan kernel: [  138.340867] usb 1-2.3: new full speed USB device using ohci_hcd and address 4
Jan 29 23:14:44 vulcan kernel: [  138.852211] usb 1-2.3: new full speed USB device using ohci_hcd and address 5
Jan 29 23:14:44 vulcan kernel: [  138.954307] usb 1-2.3: configuration #1 chosen from 1 choice[/FONT][/INDENT]

As you can see, LINUX detected the device BUT did not install the ipaq driver. 

The next thing I did was to launch vmware. It was able to detect my IPAQ device and it appeared in my list of devices. I have to click a button to enable my IPAQ in vmware. After that, i was able to synchronize my device.

I hope this will help you connect your motoq.

Bobby

---

### Post by TechMansoor on 2008-01-29
I really appreciate the help brother that I do...It just has to be something within the phone now. I blacklisted my ipaq as well as  tailed the var log messages like you suggested and I literally saw the loop recurring. These are the results I got. Looks very similar to yours until it starts looping . From a general standpoint, I dont see how much more different a device could be if it suppose to be a smart phone. It uses a usb(atob) syncing method just like most smart phones and its a windows media 5 device...but who knows...:) :) Again I really appreciate the help!!!



Jan 29 10:31:43 CSSMA kernel: [  264.018729] usb 8-2: new full speed USB device using ohci_hcd and address 3
Jan 29 10:31:44 CSSMA kernel: [  264.233855] usb 8-2: configuration #1 chosen from 1 choice
Jan 29 10:32:15 CSSMA kernel: [  295.709269] usb 8-2: usbfs: interface 0 claimed by usbfs while 'vmware-vmx' sets config #1
Jan 29 10:32:19 CSSMA kernel: [  299.697304] usb 8-2: USB disconnect, address 3
Jan 29 10:32:21 CSSMA kernel: [  301.250086] usb 8-2: new full speed USB device using ohci_hcd and address 4
Jan 29 10:32:21 CSSMA kernel: [  301.473262] usb 8-2: configuration #1 chosen from 1 choice
Jan 29 10:32:26 CSSMA kernel: [  306.717027] usb 8-2: USB disconnect, address 4
Jan 29 10:32:28 CSSMA kernel: [  308.263985] usb 8-2: new full speed USB device using ohci_hcd and address 5
Jan 29 10:32:28 CSSMA kernel: [  308.479014] usb 8-2: configuration #1 chosen from 1 choice
Jan 29 10:32:34 CSSMA kernel: [  314.112356] usb 8-2: USB disconnect, address 5
Jan 29 10:32:35 CSSMA kernel: [  315.665410] usb 8-2: new full speed USB device using ohci_hcd and address 6
Jan 29 10:32:35 CSSMA kernel: [  315.881342] usb 8-2: configuration #1 chosen from 1 choice
Jan 29 10:32:41 CSSMA kernel: [  321.185984] usb 8-2: USB disconnect, address 6
Jan 29 10:32:42 CSSMA kernel: [  322.739233] usb 8-2: new full speed USB device using ohci_hcd and address 7
Jan 29 10:32:42 CSSMA kernel: [  322.955132] usb 8-2: configuration #1 chosen from 1 choice
Jan 29 10:32:47 CSSMA kernel: [  327.667205] usb 8-2: USB disconnect, address 7
Jan 29 10:32:49 CSSMA kernel: [  329.221553] usb 8-2: new full speed USB device using ohci_hcd and address 8
Jan 29 10:32:49 CSSMA kernel: [  329.425256] usb 8-2: configuration #1 chosen from 1 choice
Jan 29 10:32:54 CSSMA kernel: [  335.013480] usb 8-2: USB disconnect, address 8
Jan 29 10:32:56 CSSMA kernel: [  336.591119] usb 8-2: new full speed USB device using ohci_hcd and address 9
Jan 29 10:32:56 CSSMA kernel: [  336.794644] usb 8-2: configuration #1 chosen from 1 choice
Jan 29 10:33:01 CSSMA kernel: [  341.477785] usb 8-2: USB disconnect, address 9
Jan 29 10:33:02 CSSMA kernel: [  343.029429] usb 8-2: new full speed USB device using ohci_hcd and address 10
Jan 29 10:33:03 CSSMA kernel: [  343.244979] usb 8-2: configuration #1 chosen from 1 choice
Jan 29 10:33:03 CSSMA kernel: [  344.023478] usb 8-2: USB disconnect, address 10
Jan 29 10:33:50 CSSMA kernel: [  390.942598] device eth0 left promiscuous mode
Jan 29 10:33:50 CSSMA kernel: [  390.942624] audit(1201624430.713:5): dev=eth0 prom=0 old_prom=256 auid=4294967295
Jan 29 10:33:50 CSSMA kernel: [  390.942630] bridge-eth0: disabled promiscuous mode
Jan 29 10:34:08 CSSMA kernel: [  408.471956] usb 8-2: new full speed USB device using ohci_hcd and address 11
Jan 29 10:34:08 CSSMA kernel: [  408.687055] usb 8-2: configuration #1 chosen from 1 choice

---

### Post by cyberco on 2008-02-05
What solved this issue for me is changing the connection settings on my WM5 device. What I did:

On the WM5 device:
- go to settings/connections
- click 'usb to pc'
- turn off  'enable advanced network functionality'

---

### Post by TechMansoor on 2008-02-05
> **cyberco said:**
> What solved this issue for me is changing the connection settings on my WM5 device. What I did:

On the WM5 device:
- go to settings/connections
- click 'usb to pc'
- turn off  'enable advanced network functionality'


Wow. I truly wish it was that simple indeed. :(. Thanks for the response though. But yeah, I tried that first before anything and still a no go..:(  Who manufactured your device, motorola, or another company perhaps?

---

### Post by hoggy on 2008-02-15
After trying everything on this thread I thought that I'd report back what actually worked.

[http://ubuntuforums.org/showthread.php?t=591732](http://ubuntuforums.org/showthread.php?t=591732)

> 1 - USB not working: VM > Removable Devices > USB > BLANK
From: [http://ubuntuforums.org/showthread.php?t=588225](http://ubuntuforums.org/showthread.php?t=588225)

Issue the following command:
gksudo gedit /etc/init.d/mountdevsubfs.sh

Before:
Code:

	#
	# Magic to make /proc/bus/usb work
	#
	#mkdir -p /dev/bus/usb/.usbfs
	#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	#ln -s .usbfs/devices /dev/bus/usb/devices
	#mount --rbind /dev/bus/usb /proc/bus/usb

Uncomment the lines as below:

After:
Code:

	#
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

Restart and your usb devices will be recognised

This worked like a charm.  No blacklisting required, USB 2.0 support in tact (outside of VMWare...)

Enjoy!

---

### Post by TechMansoor on 2008-02-15
Well the good sir above came the closet in helping me figure it out...but it still didn't work..:(:( The moto q just doesn't work with vmware server...

I've tried this solution a few months back(the on you posted hobby). I realy appreciate the help though.

but yeah, it just will not work with this phone for some reason...

---

### Post by fjgaude on 2008-02-15
Have you tried putting this is your fstab file:

```
gksudo gedit /etc/fstab
```

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Add as your last line in the fstab file.

---

### Post by TechMansoor on 2008-02-15
> **fjgaude said:**
> Have you tried putting this is your fstab file:

```
gksudo gedit /etc/fstab
```

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Add as your last line in the fstab file.

Thanks for the response. I really appreciate it that I do. :)

Yeah I had that in there a while back as well. You see I just wonder if its somethihng with certain phones. My mp3 player, printer, other devices, work fine with my gutsy install and most of the time with my vwmare server as well. But, it just doesn't work with my smart phone. I think i stated this earlier, its being recognized by VMWare server as a motorola q device indeed,but it doesn't work properly. It literally freaking gets recognized, then unrecognized in a constant loop. 

I just don't understand..:(

But I thoroughly appreciate the help so far....Hell I thought this post was dead..

Thanks to everyone who responded indeed!

---

### Post by djbon2112 on 2008-03-15
Hey guys I have a problem.

Using Ubuntu Gutsy, VMWare Workstation 6.0.0, running Windows XP Pro SP2 in the Workstation.

I connect my Motorola Q, and it shows up as an option in the "USB Devices" tab in the VM menu. I enable it, and this is what happens:

"Device Connected" sound in XP.
MotoQ screen turns on.
Entry for MotoQ disappears from the "USB Devices" tab.
"Device Disconnected" sound in XP.
MotoQ screen turns off.
Entry for MotoQ appears in the "USB Devices" tab (still checked from before).

Repeat until I disconnect it or turn it off (when it appears in the menu).

Before it was telling me that a service called "ipaq" was locking it in the host, but after blacklisting that, it still does this only that message no longer pops up. Does anyone have a suggestion? I've done everything fjgaude said. It's not an issue of the MotoQ being detected by Ubuntu, it's gotta be something with VMWare.

---

### Post by tchoklat on 2008-03-29
My issue is the ssame. I run PCLOS (Gnome edition) with VMWare Server. I have Xp running as a guest. I can get a USB memory stick to be recopgnised OK,but not a USB printer or USB connected WM6 device. Actaully they are recognised through enabling them in the menu (removable devices) but I cannot read access the PDA usuing activesync or anything else nor can I print to the prointer, even though windoze accepts the printer is there AND loads the correct drivers, the printer page just goes away!!!!!

---

### Post by fjgaude on 2008-03-29
Did you load the Windows drivers for the devices into your VM?

---

