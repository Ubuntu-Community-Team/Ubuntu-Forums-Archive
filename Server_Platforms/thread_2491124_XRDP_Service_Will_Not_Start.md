---
title: "XRDP Service Will Not Start"
date: 2023-09-26
forum: Server Platforms
---

### Post by jderosa32 on 2023-09-26
Following this guide: [https://www.ubuntumint.com/install-xrdp-ubuntu/](https://www.ubuntumint.com/install-xrdp-ubuntu/)


On step 3 to activate the service it fails:

```
× xrdp.service - xrdp daemon
     Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2023-09-26 18:55:22 EDT; 2h 33min ago
       Docs: man:xrdp(8)
             man:xrdp.ini(5)
        CPU: 8ms

Sep 26 18:55:22 web-server systemd[1]: Starting xrdp daemon...
Sep 26 18:55:22 web-server xrdp[15164]: [INFO ] address [0.0.0.0] port [3389] mode 1
Sep 26 18:55:22 web-server xrdp[15164]: [INFO ] listening to port 3389 on 0.0.0.0
Sep 26 18:55:22 web-server xrdp[15164]: [ERROR] g_tcp_bind(7, 3389) failed bind IPv6 (errno=98) and IPv4 (errno=22).
Sep 26 18:55:22 web-server xrdp[15164]: [ERROR] trans_listen_address failed
Sep 26 18:55:22 web-server xrdp[15164]: [ERROR] Failed to start xrdp daemon, possibly address already in use.
Sep 26 18:55:22 web-server systemd[1]: xrdp.service: Control process exited, code=exited, status=1/FAILURE
Sep 26 18:55:22 web-server systemd[1]: xrdp.service: Failed with result 'exit-code'.
Sep 26 18:55:22 web-server systemd[1]: Failed to start xrdp daemon.

```

```
four_half@web-server:~$ journalctl -xeu xrdp.service
Sep 26 18:55:22 web-server xrdp[15164]: [ERROR] Failed to start xrdp daemon, po>
Sep 26 18:55:22 web-server systemd[1]: xrdp.service: Control process exited, co>
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit xrdp.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Sep 26 18:55:22 web-server systemd[1]: xrdp.service: Failed with result 'exit-c>
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit xrdp.service has entered the 'failed' state with result 'exit-code'.
Sep 26 18:55:22 web-server systemd[1]: Failed to start xrdp daemon.
&#9617;&#9617; Subject: A start job for unit xrdp.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit xrdp.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 10455 and the job result is failed.

```



Any help you can provide would be helpful. Thanks!

---

### Post by MAFoElffen on 2023-09-26
I will not even attempt to answer this until you edit your first post in the Advanced Editor > Highlight your text, and Select the "#" Icon to wrapped your output within CODE Tags... Then select the very first ICON, which will show any formatting, and clean the output up to make it readable.

Sorry, but I can't read that.

Tip... While extracting output from systemctl, to get clean output that is postable, do something similar to this...
```

sudo systemctl status xrdp.service | grep .

```
It will output it to the screen without paging and without any formatting...

---

### Post by jderosa32 on 2023-09-26
My apologies. I am still learning. 

```
× xrdp.service - xrdp daemon
     Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2023-09-26 18:55:22 EDT; 2h 33min ago
       Docs: man:xrdp(8)
             man:xrdp.ini(5)
        CPU: 8ms

Sep 26 18:55:22 web-server systemd[1]: Starting xrdp daemon...
Sep 26 18:55:22 web-server xrdp[15164]: [INFO ] address [0.0.0.0] port [3389] mode 1
Sep 26 18:55:22 web-server xrdp[15164]: [INFO ] listening to port 3389 on 0.0.0.0
Sep 26 18:55:22 web-server xrdp[15164]: [ERROR] g_tcp_bind(7, 3389) failed bind IPv6 (errno=98) and IPv4 (errno=22).
Sep 26 18:55:22 web-server xrdp[15164]: [ERROR] trans_listen_address failed
Sep 26 18:55:22 web-server xrdp[15164]: [ERROR] Failed to start xrdp daemon, possibly address already in use.
Sep 26 18:55:22 web-server systemd[1]: xrdp.service: Control process exited, code=exited, status=1/FAILURE
Sep 26 18:55:22 web-server systemd[1]: xrdp.service: Failed with result 'exit-code'.
Sep 26 18:55:22 web-server systemd[1]: Failed to start xrdp daemon.

```

```
four_half@web-server:~$ journalctl -xeu xrdp.service
Sep 26 18:55:22 web-server xrdp[15164]: [ERROR] Failed to start xrdp daemon, po>
Sep 26 18:55:22 web-server systemd[1]: xrdp.service: Control process exited, co>
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit xrdp.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Sep 26 18:55:22 web-server systemd[1]: xrdp.service: Failed with result 'exit-c>
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit xrdp.service has entered the 'failed' state with result 'exit-code'.
Sep 26 18:55:22 web-server systemd[1]: Failed to start xrdp daemon.
&#9617;&#9617; Subject: A start job for unit xrdp.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit xrdp.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 10455 and the job result is failed.

```

I am wondering if this is happening because I have Remote Desktop enabled in the sharing settings. That already uses port 3389 I assume, but again I am still learning. I appreciate you providing help.

---

### Post by MAFoElffen on 2023-09-27
> **jderosa32 said:**
> My apologies. I am still learning. 

I am wondering if this is happening because I have [COLOR=#ff0000]Remote Desktop enabled in the sharing settings.[/COLOR] That already uses port 3389 I assume, but again I am still learning. I appreciate you providing help.
Wait... 

So the VM Host is Windows OS and the Hosting VM service the VM Guest is running in is Hyper-V? That type of information would be good to know to fill in the blanks with this. LOL

Yes. Windows 10 and 11 uses Port 3389 for RDP...

---

### Post by jderosa32 on 2023-09-27
Looks like I am going to get schooled here... I will explain my setup further.

I have a small form factor Dell Optiplex 7080 Micro that I have reformatted and put only Ubuntu Server 22.04 on it. After installing this OS and installed the Desktop Environment. I did this for my initial ease of use as I am still learning the terminal and other things. This machine is in my basement and away from view as it is tucked away with all other network hardware.

I am accessing this machine via the MS Remote Desktop app on my MacBook Pro as I use that to manage other machines at work. However, I could potentially use anything else. It doesn't have to be this application specifically.

Having said that I want to be able to RDP (or VNC) to the machine when it is locked. I realized that after first boot I may have to unlock the machine locally, but upon locking the device and going back to the login screen. I want to be able to remote to the machine.

This is my only goal on this post. Is this possible? Thanks for your continued help.

---

### Post by MAFoElffen on 2023-09-27
Yes it is possible. Usually for Server, it does not have a GUI, so is accessed remotely via ssh. MAC OS has a terminal and is based on a type of Linus/Unix like based under it's GUI covers... MAC OS X comes with ssh client installed as a part of the OS... You can conect to your remote server with only havig to install openssh-server on your server.
```

sudo apt install -y openssh-server

```
No further configuration of that needed to make that work on either machine.

RDP is not native to either MAC OS or Ubuntu Server Edition, so you have to install the client on MAC OS and a GUI Desktop and a XRDP server service on the Server... Configured on both ends...

Installing a Desktop on an Ubuntu Server Edition changes a few things on the powerprofile... Mainly is that, then says it is a Desktop Edition. With Servers, you do not want them to go to sleep or hibernate. Users that use a Desktop want screen savers, screen locks, and worry about how much power it is using so they want them to go to sleep or hibernate. See where that starts to affect whether something is accessible and where you had to physically interact with the machine and unlock it? That is not what you want if it is miles away (remotely).

But first, the daemon is not working... If you really want to use it with a GUI, instead of just ssh and commandline, then we need to work out some things. Just warning you that with a GUI, it isn't just going to be configuring xrdp server to get it to work 'correctly'.

First: Which method of remote access is your goal?

---

### Post by MAFoElffen on 2023-09-27
As for your xrdp daemon start error... I think if you did
```

sudo lsof -i tcp:3389

```
That is probably going to tell you that there is already an instance of xrdp running, listening on that port. You have to kill that instance to start the daemon, via
```

sudo kill xrdp
sudo systemctl restart xrdp
sudo systemctl status xrdp

```
Then post the output of the last command within CODE Tags...

---

### Post by jderosa32 on 2023-09-27
I will install SSH as well. I just wanted to have remote access to the GUI as well. 

I plan on installing a GUI for working with MySQL database so when the SSH session will not cut it for needing a visual representation I have it avaible. Let me try your suggestions and see if I can get it running. I will report back after I try your suggestions.

---

### Post by jderosa32 on 2023-09-27
I am marking this solved, because I am going a different route. I am setting up a Hyper-V and using this to setup a few VMs of Ubuntu that I will manage that way. It completely gets around this issue and works for me. I believe you advice would have got me through the rest of the way. I appreciate the help.

---

### Post by MAFoElffen on 2023-09-28
You are welcome. If you have any other questions. Feel free to ask any questions. I help support in the Virtualization Section also.

---

