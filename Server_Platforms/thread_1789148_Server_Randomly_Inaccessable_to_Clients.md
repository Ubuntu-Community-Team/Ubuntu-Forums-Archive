---
title: "Server Randomly Inaccessable to Clients"
date: 2011-06-23
forum: Server Platforms
---

### Post by famulusmercury on 2011-06-23
I have Ubuntu Server 10.04.02 on a Dell Power Edge T310 using Samba mainly, along with Spark and proftp. The server was set up brand new a few months ago and has had networking problems ever since. At first it seemed to happen a couple of weeks after installation, but now it is happening at least twice a week. The server will become inaccessible to windows clients as if it was turned off. It doesn't reply to pings either. I have tried using the second, spare, NIC and get the same results. During this same time frame of no Samba I can sometimes ssh in remotely and sometimes I can't. Up until recently just rebooting the server would "fix" the problem, now that's not necessarily the case. The last time I was at the location I restarted the server and it was still not available on the network. So, I tried ifconfig -a and saw eth0 had no IP (it's static.) I then went into the networking file and everything looked okay (I had eth1 commented out since it wasn't being used.) and then restarted with the /etc/init.d/networking restart command and it threw an error in red letters: can't read networking file or something like that. I went back into the networking file and uncommented eth1 and it's static configuration (it's still physically disconnected from the network) saved the changes and then tried the same restart command and then the server was available to the Win clients (Samba and Spark they don't use ftp much.)  This was two days ago, today they couldn't access samba again (I could access vis ssh remotely.) I restarted the server and they still couldn't access samba. We then used the /etc/init.d/networking restart command (no errors this time) and it works now, but I can't ssh in remotely. Any suggestions?

---

### Post by capscrew on 2011-06-24
> **famulusmercury said:**
> I have Ubuntu Server 10.04.02 on a Dell Power Edge T310 using Samba mainly, along with Spark and proftp. The server was set up brand new a few months ago and has had networking problems ever since. At first it seemed to happen a couple of weeks after installation, but now it is happening at least twice a week. The server will become inaccessible to windows clients as if it was turned off. It doesn't reply to pings either. I have tried using the second, spare, NIC and get the same results. During this same time frame of no Samba I can sometimes ssh in remotely and sometimes I can't. Up until recently just rebooting the server would "fix" the problem, now that's not necessarily the case. The last time I was at the location I restarted the server and it was still not available on the network. So, I tried ifconfig -a and saw eth0 had no IP (it's static.) I then went into the networking file and everything looked okay (I had eth1 commented out since it wasn't being used.) and then restarted with the /etc/init.d/networking restart command and it threw an error in red letters: can't read networking file or something like that. I went back into the networking file and uncommented eth1 and it's static configuration (it's still physically disconnected from the network) saved the changes and then tried the same restart command and then the server was available to the Win clients (Samba and Spark they don't use ftp much.)  This was two days ago, today they couldn't access samba again (I could access vis ssh remotely.) I restarted the server and they still couldn't access samba. We then used the /etc/init.d/networking restart command (no errors this time) and it works now, but I can't ssh in remotely. Any suggestions?


You will get more response if you describe the problem concisely.  I doubt anyone will want to follow your long rambling unfocused story.

Have you looked at the logs?  They are at /var/log.  Look in dmesg and kern to start with.  You can use the command _*tail*_ to look at the last part of each log/

---

### Post by famulusmercury on 2011-06-24
> **capscrew said:**
> You will get more response if you describe the problem concisely.  I doubt anyone will want to follow your long rambling unfocused story.


How was it unfocused? Did I start talking about my car or something...I must have blacked out!?

If I had left any part of the post out you would be asking if I had tried it.

---

### Post by famulusmercury on 2011-06-24
No indication of problems in the logs.

---

### Post by doas777 on 2011-06-24
do you have IPList\IPBlock running? I've had a simmilar bug on my server over the last 2 months, and it always seems to start when ipblock starts to update its lists.

---

### Post by famulusmercury on 2011-06-24
I don't see it running under processes. Is it part of apparmor? I tried stopping apparmor earlier today but I didn't see a difference.

Right now samba, openfire, ftp, and ssh are accessible locally. Remotely, I can't see anything open with a port scan even though I have the server temporarily sitting in DMZ.
I also replaced the Ethernet cable and router today and can't access anything remotely. On the LAN it's okay. 

It's like the server is specifically blocking the LAN IP of the router right now and occasionally blocking other local IP's when the workstations can't connect.

---

### Post by famulusmercury on 2011-06-25
Rebooted and can now access remotely and on LAN.

---

### Post by famulusmercury on 2011-06-30
And here we go again. Samba, Openfire  went off-line suddenly for about 5 minutes and then magically came  backup. I can't access remote via ssh now. But I can from a local  workstation. Here is a pic of dmesg.

---

### Post by famulusmercury on 2011-07-26
It seems that there might be a bug in the kernel or driver for the on board Broadcom NetXtreme II BCM57710 XGb. I have installed a [FONT=arial, helvetica][SIZE=2]Intel 82574L and everything seems better so far. I'll wait another week before I consider it resolved.
[/SIZE][/FONT]

---

### Post by famulusmercury on 2011-08-14
After a month or so, and having to pay a nominal fee, I found what seems to have been the root of the issue. Here is what the humble engineer had to say after he looked at the issue: 

"There seems to be a bug with the tickless feature in some of the newer (linux) kernels. It can cause issues like you described where the server goes to "sleep" and it takes several seconds to several minutes to wake up. You need to compile your own kernel and disable the tickless feature. I have done this on several servers with great results."

Thanks again noci. You are the man!:D

---

