---
title: "Shutdown Command Doesn't Act"
date: 2009-03-29
forum: Server Platforms
---

### Post by pgn674 on 2009-03-29
I have Ubuntu Server 8.10. I SSH in from either my Ubuntu machine at home, or from PuTTY on my Windows machine. From either place, when I run sudo reboot, it displays the normal output, then just gives me my prompt back and lets me do whatever. The system never actually reboots.```
ticsalsog@pgn674:~$ sudo reboot
[sudo] password for ticsalsog:

Broadcast message from ticsalsog@pgn674
        (/dev/pts/0) at 21:16 ...

The system is going down for reboot NOW!
ticsalsog@pgn674:~$
```The only way I can get the system to reboot is with reboot -f, which uses reboot itself instead of shutdown. I tried "shutdown -r now", and it does the same thing as reboot without the -f.

I checked last, and nothing new happens when I try reboot. In syslog, it looks like one new line is created on the first reboot attempt: "pgn674 init: rc2 main process (1110) killed by TERM signal".

I could just keep using reboot -f, but from what I can tell that's less graceful and kind on the system than reboot. I'm presently having trouble starting apache2 on boot, and I'd like to rule this out as a possible cause.

---

### Post by HermanAB on 2009-03-29
Check the logs - something doesn't want to unload when trying to shut down.  The answer is in there Sculley...

$ sudo tail -n 10000 /var/log/messages | less

---

### Post by pgn674 on 2009-03-30
messages doesn't record anything at all when I attempt the reboot. I checked out some of the other logs in the log directory, and I didn't notice anything happening at the time I try the reboot. I did notice that, on my second reboot attempt (after a successful forced reboot), syslog records something else: "pgn674 init: tty1 main process (1213) killed by TERM signal". On the third and subsequent reboot attempts, nothing new is recorded.

---

### Post by SuperSonic4 on 2009-03-30
I always use ```
sudo shutdown -hP now
```

-h     Halt or poweroff after shutdown.
-P     Halt action is to turn off the power.

That command will power off your pc.

---

### Post by pgn674 on 2009-03-30
Well, this server is a virtual machine over in Texas I think, or maybe on the Great Lakes somewhere. Anyways, if I shut it down, I'll have to ask the hosting company to virtually turn it on again.

Also, your shutdown -hP command uses Shutdown to do the stopping of services kindly. reboot also uses Shutdown. But, reboot -f uses Reboot, which is not very kind when asking processes to stop. For example, I loose my terminal's recent history (up arrow, or the history command) if I use reboot -f.

I imagine that if I tried to use shutdown -hP, it wouldn't work since that uses Shutdown and not Reboot. But, I don't want to risk it since I might loose my server for a while if it does power off.

---

### Post by tubezninja on 2009-03-30
> **pgn674 said:**
> Well, this server is a virtual machine over in Texas I think, or maybe on the Great Lakes somewhere. Anyways, if I shut it down, I'll have to ask the hosting company to virtually turn it on again.

Yeah, generally VMs and VPSes aren't going to respond well to the shutdown command, and prefer that you shcedule reboots and shutdowns through the hypervisor's control panel.  This is pretty common.

that said, the hosting company SHOULD provide you with some sort of web-based method for shutting down and starting up your VPS instance.

---

### Post by pgn674 on 2009-04-10
I checked the host's control panel on the web site, and found a VPS Management thing. For shutting down and rebooting, it allows "Shutdown: Same as sending a shutdown -p now command." I tried this, and it did nothing to my machine. Looking at the logs in the VPS Management, it acknowleges that I selected that option, but it says there was no result (it's blank).

I tried "sudo shutdown -P now" myself manually, but that still has the same effect of no action. So I don't think this is a virtual machine problem.

---

### Post by BkkBonanza on 2009-04-10
When I use Ubuntu 8.04 server under VirtualBox the reboot and poweroff both work fine.
I just do, **sudo reboot** or **sudo poweroff** and both the expected effect. 
Just for your info as I have no idea why yours doesn't.

---

