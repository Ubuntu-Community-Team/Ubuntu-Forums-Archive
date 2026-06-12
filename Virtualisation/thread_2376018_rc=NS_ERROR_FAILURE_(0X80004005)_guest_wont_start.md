---
title: "rc=NS_ERROR_FAILURE (0X80004005) guest wont start"
date: 2017-10-29
forum: Virtualisation
---

### Post by totla on 2017-10-29
Hi,  i have a ubuntu 14.04 server that has a virtualbox 4.3.36   installed. Couple days ago we had problems with one of our servers, due  to a filled up hard drive and during that time i rebooted the host  machine, after which i found that the whole virtualbox had dissapeared  from the host system. 

To fix this i simply reinstalled  virtualbox (sudo apt install virtualbox) and everything seemed to work fine after that. Later i  noticed that only 2 of the 3 guests on the host had started up, so i  tried to stat the 3rd guest manually with: VBoxManage startvm  <guest3> and the output i got was:
"Waiting for VM "guest3" to power on... VM "guest3" has been successfully started.
But  the guest3 did not start, i checked the Vbox.log and found this error:  Power up failed (vrc=VINF_SUCCESS, rc=NS_ERROR_FAILURE (0X80004005)).
This  is a very wierd prolem that i have not faced before, doing "VBoxManage  list vms", shows all 3 guests and 2 of them work just fine, it  is just  the 1 that isnt starting up no matter what i do.

Below is full VBox.log of the problematic guest:
VirtualBox VM 4.3.36_Ubuntu r105129 linux.amd64 (Jan 27 2016 12:09:06) release log
00:00:00.015292 Log opened 2017-10-29T10:57:17.837988000Z
00:00:00.015293 Build Type: release
00:00:00.015296 OS Product: Linux
00:00:00.015297 OS Release: 3.13.0-117-generic
00:00:00.015298 OS Version: #164-Ubuntu SMP Fri Apr 7 11:05:26 UTC 2017
00:00:00.015324 DMI Product Name: PowerEdge T620
00:00:00.015332 DMI Product Version: 
00:00:00.015427 Host RAM: 16001MB total, 10137MB available
00:00:00.015430 Executable: /usr/lib/virtualbox/VBoxHeadless
00:00:00.015430 Process ID: 1712
00:00:00.015431 Package type: LINUX_64BITS_GENERIC (OSE)
00:00:00.016279 Installed Extension Packs:
00:00:00.016287   VNC (Version: 4.3.36 r105129; VRDE Module: VBoxVNC)
00:00:00.031047 Power up failed (vrc=VINF_SUCCESS, rc=NS_ERROR_FAILURE (0X80004005))

After doing more digging i found a log file from at /home/vboxuser/.Virtualbox/VBoxSCV.log and in there:

48:42:21.473805  nspr-2   VD: error VERR_FILE_NOT_FOUND opening image file  '/mnt/VirtualBoxVMs/guest3/Snapshots/{803a76b8-1ae9-40b2-b628-72376bc73c46}.vmdk'  (VERR_FILE_NOT_FOUND)}, preserve=false

48:42:21.473960 nspr-2    ERROR [COM]: aRC=NS_ERROR_FAILURE (0x80004005)  aIID={05f2bbb6-a3a6-4fb9-9b49-6d0dda7142ac} aComponent={Medium}  aText={Could not open the medium  '/mnt/VirtualBoxVMs/guest3/Snapshots/{6ade3077-e966-4d63-bb24-1473fbf6832c}.vmdk'.

if  im reading/understanding this right, it is trying to open a VM  using  "{6ade3077-e966-4d63-bb24-1473fbf6832c}.vmdk" but there is no such  snapshot in the folder.. is this the problem? how can i change it to  look for the snapshot i actually have?

---

