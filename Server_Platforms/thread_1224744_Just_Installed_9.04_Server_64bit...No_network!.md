---
title: "Just Installed 9.04 Server 64bit...No network!"
date: 2009-07-27
forum: Server Platforms
---

### Post by rayj00 on 2009-07-27
I've installed Ubuntu Desktop many times before as a Virtual Machine guest. I've never had a problem before. 

Now I have installed Ubuntu Server 64 bit.  The install was certainly bizarre to say the least.

Anyway, it comes up fine as a VMware guest. It has an assigned IP address (private 192.168.1.104) on my local lan.  However, I cannot ping anything. The VMware guest was configured as "bridged" as usual.

I would like to have a GUI. I know all of the arguments against a GUI on a server, but this is for home use only. I don't want to spend hours looking up commands.

Since I can't communicate outside, installing anything is not possible now.

How should I trouble shoot the network connection?
Pinging anything doesn't work.  Trying to ping Ubuntu from the Host times out...

Ideas?

Ray

---

### Post by littlegreiger on 2009-07-27
Can you ping out from the ubuntu guest? Try pinging google from the commandline. If you can't and you can't resolve the hostname you may not have gotten the correct dns servers set up. 
Try ```
cat /etc/resolv.conf
``` to see if you have any dns servers configured. 
I'm not sure why you can't ping it from the host but if it's getting an ip it's definitely on your network.

---

### Post by rayj00 on 2009-07-27
> **littlegreiger said:**
> Can you ping out from the ubuntu guest? Try pinging google from the commandline. If you can't and you can't resolve the hostname you may not have gotten the correct dns servers set up. 
Try ```
cat /etc/resolv.conf
``` to see if you have any dns servers configured. 
I'm not sure why you can't ping it from the host but if it's getting an ip it's definitely on your network.

I have the same information in resolv.conf as I do in the host when I do a ipconfig. My host, BTW, is Vista Home Premium 64 bit.
I don't think this matters.

Ray

---

### Post by littlegreiger on 2009-07-27
Can you ping your router? Also, do you have any sort of filtering on your router like MAC filtering or the like?

---

### Post by rayj00 on 2009-07-27
> **littlegreiger said:**
> Can you ping your router? Also, do you have any sort of filtering on your router like MAC filtering or the like?

Can't ping my router. No MAC filtering.

---

### Post by littlegreiger on 2009-07-27
Can you post the output of ifconfig. Also I just noticed in your original post that you said the install was a little bizarre, is there anything specific that you remember that was weird or seemed weird at the time. 
Also what VMware product are you using, server or workstation? And what versions?

---

### Post by rayj00 on 2009-07-27
> **littlegreiger said:**
> Can you post the output of ifconfig. Also I just noticed in your original post that you said the install was a little bizarre, is there anything specific that you remember that was weird or seemed weird at the time. 
Also what VMware product are you using, server or workstation? And what versions?

I have installed Server 9.04 64 bit.

My VMware is Server v2 64 bit.

I have attached a jpg of the ifconfig command.

Ray

---

### Post by rayj00 on 2009-07-27
> **littlegreiger said:**
> Can you post the output of ifconfig. Also I just noticed in your original post that you said the install was a little bizarre, is there anything specific that you remember that was weird or seemed weird at the time. 
Also what VMware product are you using, server or workstation? And what versions?

Oh forgot to mention the install.

The Ubuntu desktop installs were nothing like the server. It was
all menu driven from a cli.

I wasn't all sure I installed it correctly.  The only thing I actually picked to install was the SSH package.

To be honest, I'm not sure how valid the install is based on what I did.  Although I have not seen any errors yet.

---

### Post by littlegreiger on 2009-07-28
That's the way the server edition installs, it's all text-based. It's also pretty hard to screw up unless you didn't go with default options.
Your ifconfig seems good, can you post the exact error you get when you try to ping google?

Edit: Unfortunately I can't recreate your environment so I can't test and see if there's a problem with the setup or not.

---

### Post by rayj00 on 2009-07-28
> **littlegreiger said:**
> That's the way the server edition installs, it's all text-based. It's also pretty hard to screw up unless you didn't go with default options.
Your ifconfig seems good, can you post the exact error you get when you try to ping google?

Edit: Unfortunately I can't recreate your environment so I can't test and see if there's a problem with the setup or not.

Unknown host?

---

### Post by littlegreiger on 2009-07-28
Ok that unknown host is a dns problem, you should however be able to ping your local network, what happens when you ping your router using the ip address?

---

### Post by rayj00 on 2009-07-28
> **littlegreiger said:**
> Ok that unknown host is a dns problem, you should however be able to ping your local network, what happens when you ping your router using the ip address?

I get "Destination Host Unreachable".

Ray

---

### Post by littlegreiger on 2009-07-28
Ok, a couple more questions and things to run.
Do you use a separate DHCP server or does your router dole out the IP's? 
Did you set anything for the HTTP proxy when you installed the server?
If you could run and post the output of ```
route
``` and the output of ```
echo $http_proxy
```
Also if you've got the time and don't mind, you might try to install the server again on a different virtual machine.

---

### Post by rayj00 on 2009-07-28
> **littlegreiger said:**
> Ok, a couple more questions and things to run.
Do you use a separate DHCP server or does your router dole out the IP's? 
Did you set anything for the HTTP proxy when you installed the server?
If you could run and post the output of ```
route
``` and the output of ```
echo $http_proxy
```
Also if you've got the time and don't mind, you might try to install the server again on a different virtual machine.

Router deals out the IP addresse.
No proxy.

Here is the route output:

---

### Post by littlegreiger on 2009-07-29
Alright, I'm starting to run out of ideas.
It looks like you have an extra line in your routing table, however that might be do to with the way it displays and not how it's working.

I did however setup a similar environment to yours. I set up VMware server 2 on Vista Home Premium 32bit SP1 and Ubuntu 9.04 64 bit guest.
At first I had no network but that was due to the vm being bridged to the wrong network interface. I don't know if this is your problem but if you have more than one network interface in your host that could be a problem. To change this I had to run the "Manage Virtual Networks" as administrator (found on the start menu) and disable automatically choosing which interface to bridge to from the automatic bridging tab. Then go to the host virtual network mapping tab and choose which interface to bridge to. You'll have to reconfigure the interface in your guest by running```
sudo /etc/init.d/networking restart
``` or maybe restarting the guest.

If this doesn't work you can try running```
sudo ip route flush table main
``` to flush the routes and then reboot the guest and it should rebuild the default route table.

Hope something I posted helps.

---

### Post by rayj00 on 2009-07-29
Wow...the "sudo /etc/init.d/networking restart" seems to have done the trick! I can ping the world now!

However, I have to do this command after ever Ubuntu restart!
I didn't have to do this with Ubuntu desktop.

Is there a way to do this automatically when Ubuntu comes up?

Thanks for your help with this.

Ray

---

### Post by littlegreiger on 2009-07-29
I'm glad that that fixed your problem. You can make it run every time you start but that doesn't fix the underlying problem.
Have you tried installing ubuntu again? I think something might have happened when you installed it.

---

### Post by cariboo on 2009-07-30
To have networking start on boot, run at the prompt:

```
sudo update-rc.d networking defaults
```

This should add networking to /etc/rc0.d, /etc/rcS.d and /etc/tc6.d

---

### Post by littlegreiger on 2009-07-30
Shouldn't that have already been added when the server was installed?

---

