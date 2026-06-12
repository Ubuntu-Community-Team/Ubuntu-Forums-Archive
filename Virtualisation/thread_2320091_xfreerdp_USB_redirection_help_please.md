---
title: "xfreerdp USB redirection help please"
date: 2016-04-10
forum: Virtualisation
---

### Post by Lee_Nowell on 2016-04-10
Hi,

I am trying to set up a home virtual environment and my current setup is as follows....

Server         - Ubuntu 14.04 running virtualbox
VM               - Ubuntu 14.04
"Thin client" - Ubuntu 14.04 running xfreerdp (latest nightly build)

I am now trying to get my development environment up and running which requires me to be able to attach my development board (ESP8266) to the thin client via USB and being able to see it in the VM.  I have tried all of the following but I can not see the USB device in /dev on the VM.

```

sudo ./xfreerdp  /dvc:urbdrc,idev:1a86:7523 /sec:rdp /v:ibmserver:9001

sudo ./xfreerdp /usb:dbg,dev:1a86:7523 /sec:rdp /v:ibmserver:9001

sudo ./xfreerdp /usb:auto,dev:1a86:7523 /sec:rdp /v:ibmserver:9001

sudo ./xfreerdp /usb:rules:allow /sec:rdp /v:ibmserver:9001

```


The output I get from the console is the same except for the debug version gives some more information.  The debug one is

```

[17:23:21:423] [9993:9994] [INFO][com.freerdp.client.common.cmdline] - loading channel drdynvc
[17:23:21:523] [9993:9994] [INFO][com.freerdp.channels.drdynvc.client] - Loading Dynamic Virtual Channel urbdrc
[17:23:21:523] [9993:9994] [ERROR][com.freerdp.channels.urbdrc.client] - error processing arguments
[17:23:21:525] [9993:9994] [WARN][com.freerdp.channels.urbdrc.client] - bus:0 dev:0 not exist in udevman
[17:23:21:525] [9993:9994] [INFO][com.freerdp.channels.urbdrc.client] - VID: 0x1A86, PID: 0x7523
[17:23:21:526] [9993:9994] [DEBUG][com.freerdp.channels.urbdrc.client] -   Port: 1
[17:23:21:526] [9993:9994] [DEBUG][com.freerdp.channels.urbdrc.client] -   DevPath: 2-1
[17:23:21:526] [9993:9994] [DEBUG][com.freerdp.channels.urbdrc.client] -   Hub BUS/DEV: 2 1
[17:23:21:526] [9993:9994] [DEBUG][com.freerdp.channels.urbdrc.client] - libusb_open success!
[17:23:21:526] [9993:9994] [DEBUG][com.freerdp.channels.urbdrc.client] - Regist Device: Vid: 0x1A86 Pid: 0x7523 InterfaceClass = 0xFF
[17:23:21:526] [9993:9994] [WARN][com.freerdp.channels.urbdrc.client] - bus:2 dev:7 not exist in udevman
[17:23:21:526] [9993:9994] [DEBUG][com.freerdp.channels.urbdrc.client] - UDEVMAN device registered.
[17:23:21:526] [9993:9994] [TRACE][com.freerdp.channels.urbdrc.client] - 



```

Does anyone have an ideal about what I am doing wrong?

thanks

Lee.

---

### Post by MAFoElffen on 2016-04-10
Let's clear up some language between us so we have the same understanding ... So we can describe and talk the same language.

* You say you have Ubuntu Server Edition 14.04.0x LTS, that is running Oracle VirtualBox as an Application...
 Since VirtualBox is a GUI based application, and Server Edition is Text Console Based... 
- How are you running VirtualBox on Server?
- Do you have a GUI installed on your Server Edition?

* You say you are running Ubuntu Desktop Edition 14.04.0x LTS as a VM from within VirtualBox...
Okay... 
- This is where you say you have a problem, so I well address this at the end...

* You say you are running a thin-client. What you are describing is not a thin-client foundation, nor architecture. Because in the same line, you say that you are using freerdp... RDP stands for Remote Desktop Protocol. Mentioning that assumes that you are doing a remote desktop session from your VM to at least a fat client machine running the RDP client software to complete the connection. Confusion might be how they describe their releases. Releases... which stopped at a beta release over 2 years ago? I see some recent activity in their code... I know, as an OpenSource Project Leader and Dev Tester, that "dailies" are not releases... and are open for testing, (all bugs included at no additional cost). A daily is not even as stable as a beta release. They have their place, and are a necessary evil. But are fairly universally accepted as dev test code...

/* --- The actual problem you seem to be describing  --- */
*** In VirtualBox, depending on what version you are running, you need to install VirtualBox'es Extension Pack ... that is closed source, free dl from Oracle, to extend it enough for a VM guest to be able to see the Host's USB ports. Next, from a terminal session from the Ubuntu VM
```

sudo lsusb

```
Will display all the usb ports that the VM Guest sees. (and what it thinks it sees connected to those usb ports.)

Is that enough info to start? I'm away from home and will check on this later for your additional info.

---

### Post by Lee_Nowell on 2016-04-11
Hi

Firstly thank you got getting back to me and apologies for the lack of clarity. To clarify the setup...

**Server**
As you described ([COLOR=#000000] Ubuntu Server Edition 14.04.0x LTS, that is running Oracle VirtualBox as an Application)[/COLOR].  I have installed VirtualBox as a headless install by following these steps

[http://www.liberiangeek.net/2014/09/install-virtualbox-headless-ubuntu-14-04-server-manage-phpvirtualbox/](http://www.liberiangeek.net/2014/09/install-virtualbox-headless-ubuntu-14-04-server-manage-phpvirtualbox/) 

There is no GUI installed on the server.

**VM**
As you describe ([COLOR=#000000]Ubuntu Desktop Edition 14.04.0x LTS as a VM from within VirtualBox).  [/COLOR]I have installed the extension pack within the guest OS but I don't believe I have installed it on the host OS (will check when I get home)...  Will also need to check exact versions of VirtualBox I am running.  From memory the specific version mentioned in the guide above was not available to I selected the latest cut of 4.3 (I think this is 4.3-36)  together with the corresponding extension pack.  Will confirm when I get home.
[COLOR=#000000]
[/COLOR]"**Thin client"**
Sorry this was my sloppy use of the term.....    It is actually a 14.04 LTS desktop install on my laptop and I am running a xfreerdp session to connect to the Ubuntu VM.  The idea being that anyone can RDP from any device to their VM running on the server.

In terms of the xfreerdp version, the reason I went to the latest nightly is because the stable version I had installed had the old format command line options and all the posts on the various forums about the USB redirection seemed to have the new format so hard for me to test out their suggestions.  I couldn't find a newer stable version.  

As it happens, I am not really wedded to xfreerdp so if there is something better, very happy to switch.  I just need a Ubuntu RDP client that enables me to do the following
- specify the resolution size and open in full screen mode
- USB redirection
- Audio redirection
- Camera/ Microphone redirection

I will check the output of 

```
lsusb
```

when I get home.  To check if I could see the USB device on the Ubuntu VM guest I was looking in /dev/ttyU* and nothing was mapped.  

I also did one further test late last night.  I tried connecting the USB device to the server to see if that showed up in the VM (i.e. /dev/ttyU* showed it) and that didn't work either.  I assume this means there is an issue with my VM setup?  I switched on USB 2 support and EHCI and added a blank rule (which I believe means that all will be passed through to the guest)?

Thanks once again for your help and I will post an update later when I get home

thanks

Lee.

---

### Post by MAFoElffen on 2016-04-11
Not with the VM setup. You queried the VM, and it confirmed that the Virtual Machine does not see the USB port that has your "external device"as hardware. So there is no hardware passthrough of your USB in the hypervisor (in your case VirtualBox Headless) running on your host to your VM guest.

The Oracle Extension Pack installs to the Host. It is actually an VirtualBox associated filetype. So when running VirtualBox Standard (with GUI), you open the file with VirtualBox and it installs itself as an extension of VirtualBox. I guess the reason for that is VirtualBox itself is opensource code, but the Extension Pack is closed source, proprietary code. Even though the binary is provided free, the source code is a guarded technology...

Yes, old-school VirtualBox, prior to v4.x, you used the Guest Additions ISO, which you mounted to the guest to get additional capabilities. Since version 4.0, is now the extension pack, which since it installs to the hypervisor itself, you then only have to install once. (much simpler).

... SO, once you install that to your host, restart the host (because it involves restarting the linux kernel vboxdrv module) to pick up the update, then recheck what your VM sees as USB devices.

---

### Post by Lee_Nowell on 2016-04-11
Hi,

Thanks for this... I have some progress.  I have installed the guest additions on the host server and now when I plug in the USB device into the server I can see it in the VM.... :D:D

However when I plug it into the laptop and run the following xfreerdp command, I can not see the device using lsusb nor is there a /dev/ttyU* :(

Extra info as promised....

Virtualbox version on server - 4.3.36r105129Guest Additions installed on the server - Oracle_VM_VirtualBox_Extension_Pack-4.3.36-105129.vbox-extpack

```
xfreerdp client command - sudo ./xfreerdp  /usb:dbg,dev:1a86:7523 /sec:rdp /v:ibmserver:9001 /sound:sys:alsa

```

Output in console

```

[19:37:22:250] [20968:20969] [INFO][com.freerdp.client.common.cmdline] - loading channel rdpdr
[19:37:22:250] [20968:20969] [INFO][com.freerdp.client.common.cmdline] - loading channel rdpsnd
[19:37:22:250] [20968:20969] [INFO][com.freerdp.client.common.cmdline] - loading channel drdynvc
[19:37:22:250] [20968:20969] [INFO][com.freerdp.client.x11] - No user name set. - Using login name: lee
[19:37:22:352] [20968:20969] [INFO][com.freerdp.channels.drdynvc.client] - Loading Dynamic Virtual Channel urbdrc
[19:37:22:352] [20968:20969] [ERROR][com.freerdp.channels.urbdrc.client] - error processing arguments
[19:37:22:352] [20968:20971] [INFO][com.freerdp.channels.rdpsnd.client] - Loaded alsa backend for rdpsnd
[19:37:22:353] [20968:20969] [WARN][com.freerdp.channels.urbdrc.client] - bus:0 dev:0 not exist in udevman
[19:37:22:353] [20968:20969] [INFO][com.freerdp.channels.urbdrc.client] - VID: 0x1A86, PID: 0x7523
[19:37:22:355] [20968:20969] [DEBUG][com.freerdp.channels.urbdrc.client] -   Port: 1
[19:37:22:355] [20968:20969] [DEBUG][com.freerdp.channels.urbdrc.client] -   DevPath: 2-1
[19:37:22:355] [20968:20969] [DEBUG][com.freerdp.channels.urbdrc.client] -   Hub BUS/DEV: 2 1
[19:37:22:355] [20968:20969] [DEBUG][com.freerdp.channels.urbdrc.client] - libusb_open success!
[19:37:22:355] [20968:20969] [DEBUG][com.freerdp.channels.urbdrc.client] - Regist Device: Vid: 0x1A86 Pid: 0x7523 InterfaceClass = 0xFF
[19:37:22:355] [20968:20969] [WARN][com.freerdp.channels.urbdrc.client] - bus:2 dev:8 not exist in udevman
[19:37:22:355] [20968:20969] [DEBUG][com.freerdp.channels.urbdrc.client] - UDEVMAN device registered.
[19:37:22:355] [20968:20969] [TRACE][com.freerdp.channels.urbdrc.client] - 



```

```

xfreerdp --version
```

gives "This is FreeRDP version 1.0.2"

In virtualbox I have tried it with the blank filter (remote is set to "any") as well as without a filter and no change.

Any ideas?

thanks

Lee.

---

### Post by Lee_Nowell on 2016-04-12
Hi 

I tried to establish whether the issue is with xfreerdp or virtualbox....  So,  I tried installing virtualbox on the laptop so I could see whether their rdesktop-vrdp client would work instead.  I installed virtualbox using

```

sudo apt-get install virtualbox

```

but it did not seem to install the RDP client.  I tried Googling to see how to install it on its own but no joy.  Anyone have any ideas?

thanks

Lee.

---

### Post by MAFoElffen on 2016-04-12
So the remote node is a laptop running Ubuntu? Why not use the included Vino RDP between both? Nothing to install... Included with Ubuntu Desktop suite...

---

### Post by Lee_Nowell on 2016-04-12
Yes. The end device will be a Ubuntu build (ie either laptop or desktop).  Not sure what you meant by 'between both' but do you mean to replace xfreerdp with Vino RDP and use it to connect to the VM?

Thanks

Lee.

---

### Post by MAFoElffen on 2016-04-13
You don't have to replace or even add... It's a default application in the desktop suite. (just as Windows Remote Desktop is a part of Windows). 

You just have to start is up and configure both sides. Lots of tutorials out on the web to do that... But here are the Ubuntu Wiki Doc's:
[https://help.ubuntu.com/community/VNC/Clients](https://help.ubuntu.com/community/VNC/Clients)
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

