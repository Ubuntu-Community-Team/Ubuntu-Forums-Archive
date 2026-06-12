---
title: "Black Screen After Grub on Startup"
date: 2017-01-18
forum: Ubuntu/Debian BASED
---

### Post by Clueless Wonder on 2017-01-18
Last night, I installed a lot of packages and dependencies for a printer that I was having problems getting recognized.and got the  printer to work.  In hind-sight, I don't think I needed to install as  much as I did, but will test that another time.  Here is my dilemma - I  turned on the computer and can't login.  I am not hugely surprised as I  figured I would probably muck something up with all of that package  installation.  When I go to Recovery in Grub, I chose DPKG to check  broken dependencies and found that it wants to remove  multiarch-support:i386 and install multiarch-support.  When I approve  for it to go ahead, it says "Could not download the upgrades.  The  upgrade has aborted."  Then it talks about checking the internet  connection (which was fine last night) or installation media.  "Failed  to fetch http'://us.archive.ubuntu.com/ubuntu/pool/  main/g/glibc/multiarch-support_2.23-0ubuntu3.amd64.deb.  Temporary  failure resolving 'us.archive.ubuntu.com'.  I tried to ping 8.8.8.8 and got connect:Network is unreachable.

I would be grateful for any suggestions as I am hoping not to have to do a reinstall after all of those package installations.

---

### Post by gdesilva on 2017-01-19
I haven't used Recovery option but it appears you are in a command line mode now. If this is the case, you would need to set up the network first before the downloads can be done. As you mention if you cannot ping 8.8.8.8 there is no network connection. The following might be useful in setting up the network in cli mode.

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

Once you can ping 8.8.8.8 then give it a try again. Hope this helps.

---

### Post by Bucky Ball on 2017-01-19
In recovery mode, choose 'Network' from the list of options and when that's finished choose 'Root' which will drop you to the shell, hopefully with networking.

This will/should work without issue if you plug in an ethernet cable. Wireless can be problematic.

---

### Post by Clueless Wonder on 2017-01-19
hi gdsilva - I looked at the page you suggested, and tried the suggestion about vi /etc/network/interfaces at the root prompt, but that took me to a page in terminal that didn't really make sense and then it started running lines of information and then took me back to the Recovery Menu, from which I couldn't choose anything at that point.  I had to do a hard shut down to start over.  If I didn't do something correctly, I am not sure what I was supposed to do.  Thanks for the suggestion....do you have any more information on exactly what I was supposed to type where?

Hey Bucky Ball - I did what you suggested, got to the Root prompt and did ifconfig and it looked like all was good.  I wasn't sure what to do from there and thought that I needed to get the packages fixed to be able to login.  So, I rebooted, went to Recovery mode, chose dpkg and chose Y to remove and install the necessary multi-arch packages.  It then gave me the original message of not being able to complete it.  Did I disconnect it by rebooting?  Thinking so, I went through the steps again, chose Network, went to Root and did iconfig and it appears I have a network connection, did ctrl-D to get back to the menu, chose dpkg, Y, and got the same failure.  I need more guidance if you have more ideas.  Thank you for helping me!

---

### Post by gdesilva on 2017-01-20
As I mentioned earlier, I have never used the Recover mode but my suggestion was to first check that you have got the network up and running before attempting to run dpkg. Bucky Ball's suggestion should have worked but do not reboot the machine after setting up the network! First set up the network, then ping 8.8.8.8 to make sure that you have a proper network connection. If you cannot ping 8.8.8.8 then there is no point in going any further with dpkg and you should try to find out why you cannot get the network connection going. Check the router, cables etc. If all looks good run 'netstat -r', 'ifconfig -a' and post the results.

---

### Post by Clueless Wonder on 2017-01-21
> **gdesilva said:**
> As I mentioned earlier, I have never used the Recover mode but my suggestion was to first check that you have got the network up and running before attempting to run dpkg. Bucky Ball's suggestion should have worked but do not reboot the machine after setting up the network! First set up the network, then ping 8.8.8.8 to make sure that you have a proper network connection. If you cannot ping 8.8.8.8 then there is no point in going any further with dpkg and you should try to find out why you cannot get the network connection going. Check the router, cables etc. If all looks good run 'netstat -r', 'ifconfig -a' and post the results.

Hi gdesilva - boy, I earned my tag user name on this one.  Sorry about forgetting to try the ping again.  I just re-did the procedure and got ping responses.  I then did netstat -r and got:

Destination                        Gateway                       Genmask                  Flags       MSS  Window  irtt  Iface
default                     192.168.1.254                 0.0.0.0                      UG        0         0         0    enp4s0
192.168.1.0                   *                            255.255.255.0              U           0        0          0    enp4s0

ifconfig -a

enp4s0  Link encap:Ethernet  HWaddr  00:13:72:12:b4:f0
            inet addr: 192.168.1.69   Bcast:192.168.1.255    Mask:255.255.255.0
             inet5 addr: fe80::97c0:2d02:4e1c:a4b0/64  Scope:Link
            UP BROADCAST RUNNING MULTICAST     MTU:1500  Metric:1
             RX packets:437 errors:0 dropped:0 overruns:0 frame:0
             TX packets:206 errors:0 dropped:0 overruns:0  carrier:0
             collisions:0  txqueuelen:1000
             RX bytes:35700 (35.7 KB)  TX bytes:20152 (20.1KB)
             Interrupt:17 Memory:fe3d0000-fe400000

There is also a reading for lo, but I am thinking you may not need that and I am having to type everything by hand so I thought I would wait and see.

Thanks!

---

### Post by Bucky Ball on 2017-01-21
Well, that looks like you're online so go ahead and try to do what you want to do. ;)

---

### Post by Clueless Wonder on 2017-01-21
> **Bucky Ball said:**
> Well, that looks like you're online so go ahead and try to do what you want to do. ;)

Hey Bucky Ball - I tried the dpkg again and was still getting the same message, Failed  to fetch http'://us.archive.ubuntu.com/ubuntu/pool/   main/g/glibc/multiarch-support_2.23-0ubuntu3.amd64.deb.  Temporary   failure resolving 'us.archive.ubuntu.com'.  I am now looking at doing journalctl to see if I can sort out anything else that is going on.

I ran the following:
nano /var/log/boot.log 
and the first FAILED I see is with Failed to start Show Plymouth Boot  Screen.  See 'systemctl status plymouth-start.service' for details.   Then I get another line of that.  Then everything is OK until the end.   The end says Starting Terminate Plymouth Boot Screen......Starting Hold  until boot process finishes up......

I appreciate your thoughts and understand if you are tired of dealing with this.  Thanks!

---

### Post by Clueless Wonder on 2017-01-21
I am making progress!  After a couple more reboots, I was able to run the dpkg and fix the multi-arch situation.  However, I still can't boot.  I then ran dpkg again and it looks clear.  I am now running journactl and it gets the following errors:

Kernal: [drm:radeon_init [radeon]]  *ERROR* No UMS support in radeon module!
Kernal: blk_update_request: I/O error, dev fd0, sector 0
Kernal: ERROR @wl_clfg80211_detach : NULL ndev-> ieee80211ptr, unable to deref wil
NetworkMnager[834] nm_device-get-device-type: assertion 'NM_IS_Device (self)' failed
systemd-hostnamed{846}:Failed to run event loop: Transport endpoint is not connected

---

### Post by Bucky Ball on 2017-01-21
Ah. That looks like a known issue with the graphics, perhaps. Please give full details of Ubuntu release and flavour you are using. Make and model of machine could also be handy. While you are in recovery mode, run this in a terminal.

```
lshw -C video
```

... and post the output here, please. (Just take a note of the exact card details and post here.)

There is a known issue with the Radeon driver for some cards in the newer releases of Ubuntu. It will apparently be rectified as people are working on it, but for now, not sure. I don't have the problem and not my area, but with those details requested, we'll know more and people that know about this may be able to advise.

---

### Post by Clueless Wonder on 2017-01-22
Hey Bucky! I am running WattOS R10, which is based on Ubuntu 16.04.1 LTS and ships with the LXDE desktop.  Everything was fine until I tried to install a series of packages to get a Dell Printer working....

I ran the command you said, but the output runs and then only stays for a few seconds.  Then a bunch of code runs by that says OK before each line and then it dumps me back at the Recovery Menu, or, after trying again, ended with Stopping with Emergency Shell....and froze.  I saw the output for a little bit and could probably see it again.  Are there particular lines it would be good to focus on?  Would it be better to just reinstall?  I am really enjoying everything I am learning, but wondering if it is a lost cause because of the package installations I did....

---

### Post by wildmanne39 on 2017-01-22
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by Bucky Ball on 2017-01-22
Sorry, never heard of that OS and never used it.

Always best to start threads making it clear which distro, release and flavour you are using to avoid confusion and time wastage. Good luck. ;)

---

### Post by Clueless Wonder on 2017-01-22
Hi Bucky - thank you for all your help.  As it is very similar to Lubuntu, I didn't realize it was going to be an issue.  I apologize for not being clear ahead of time and thanks for the heads-up about doing that in the future.

I think you were right that my current issue is with the Radeon part.  Just did a Boot Repair and here is the result [https://paste.ubuntu.com/23849749/](https://paste.ubuntu.com/23849749/). It looks like the problem is with this line:

lspci: Unable to load libkmod resources: error -12

I will do some more research.  Please let me know if anyone has any thoughts. 

Thanks!

---

### Post by Bucky Ball on 2017-01-22
The bit relevant to video from Boot Repair output for future travellers:

```
*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300] [1002:5b60]
Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300] [1002:0602]
Kernel driver in use: radeon
01:00.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300 SE] [1002:5b70]
*******
```

See [here]("https://help.ubuntu.com/community/RadeonDriver#Unsupported_chips"). Look for 'RV370'. That card appears to be fully supported in 16.04 by the open-source Radeon driver, **_NOT_** the flgrx driver that was commonly used for many AMD cards. You appear to have the correct 'radeon' driver installed ...

This is doubtfully the problem. Carry on. ;)

---

### Post by Clueless Wonder on 2017-01-23
> **Bucky Ball said:**
> The bit relevant to video from Boot Repair output for future travellers:

```
*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300] [1002:5b60]
Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300] [1002:0602]
Kernel driver in use: radeon
01:00.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300 SE] [1002:5b70]
*******
```

See [here]("https://help.ubuntu.com/community/RadeonDriver#Unsupported_chips"). Look for 'RV370'. That card appears to be fully supported in 16.04 by the open-source Radeon driver, **_NOT_** the flgrx driver that was commonly used for many AMD cards. You appear to have the correct 'radeon' driver installed ...

This is doubtfully the problem. Carry on. ;)

Thanks Bucky.  I think it is time to reinstall.  I have really enjoyed everything I have learned and appreciate all of the assistance from people here.  I don't know if this should be marked "solved" as I wasn't able to solve the specific problem, but my need will be taken care of by the reinstall.

---

