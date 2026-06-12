---
title: "How to use SSH(Secure Shell) Service in linux?"
date: 2010-06-11
forum: Security
---

### Post by jeremy28 on 2010-06-11
Hi all
 
I want to learn using SSH (Secure Shell) service in linux and connect to SSH server with PuTTY to test some commands, but I
have not worked with it yet;
I have Ubuntu 9.04 on my "Virtual Machine" and my host OS is Win.XP and I have installed "OpenSSH server" and "PuTTY" from the ubuntu repository,
Is this action rational?
I mean I want to connect from PuTTY on linux(on VM) to the SSH Server on linux?
(Meanwhile, I have no work with the host Windows and just wanna test it on the linux!)
 
If so, please tell me where should I see the "Host Name/Ip Address" of the SSH Server to enter in the PuTTy's dialog?
In windows we can use "ipconfig" command to see the IP Addresses, but I don't know what is the command in linx for this purpose?
 
Please help me with this to use SSH Service in ubuntu correctly, I'm so hurry?!!!
TIA

---

### Post by The Cog on 2010-06-11
The equivalent command in Linux is **ifconfig** - it shows a little more than the windows ipconfig but you should be able to figure it out. Ignore interface lo which has an address of 127.0.0.1 - it's probably eth0 you want.

---

### Post by Peter09 on 2010-06-11
You can test ssh by doing it on the 'local' machine as well.
 
```
ssh <username>@localhost
```
 
should give you a terminal if the ssh-server is working.

---

### Post by telorbuduk on 2010-06-11
try check if your SSH server is running with

user$ps -ax | grep ssh

if the server running well it should be a ssh word in the result

---

### Post by rookcifer on 2010-06-11
You don't need PuTTY if on Linux.  Just open the terminal to execute the commands.

---

### Post by pricetech on 2010-06-11
Putty is for use under windows as a Secure Shell client.  You won't use it under Ubuntu.

Are you trying to connect from your VM to another computer, or back to the VM ??

A little clarification of what you hope to accomplish would be helpful.

---

### Post by FuturePilot on 2010-06-11
> **pricetech said:**
> Putty is for use under windows as a Secure Shell client.  You won't use it under Ubuntu.

Are you trying to connect from your VM to another computer, or back to the VM ??

A little clarification of what you hope to accomplish would be helpful.

I believe the OP is trying to connect to the VM from the host.

---

### Post by The Cog on 2010-06-11
> **FuturePilot said:**
> I believe the OP is trying to connect to the VM from the host.

Good point. If the VM is using NAT networking then you will not be able to connect to it from outside, only from the VM outwards. If the VM is using bridging then you should be OK either direction.

---

### Post by bodhi.zazen on 2010-06-11
> **pricetech said:**
> Putty is for use under windows as a Secure Shell client.  You won't use it under Ubuntu.

Are you trying to connect from your VM to another computer, or back to the VM ??

A little clarification of what you hope to accomplish would be helpful.

You can use Putty on Linux if you wish. Putty is in the ubuntu repos.

Most people do not use it, but it can be done. If you like putty go ahead and use it on Linux.

---

### Post by anomie on 2010-06-11
@jeremy28: Just curious whether you've ever bothered responding to (or reading) any of the [multiple](http://www.linuxquestions.org/questions/linux-security-4/how-to-use-ssh-secure-shell-service-in-linux-813502/#post3999870) [identical](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-use-ssh-secure-shell-service-in-linux-813501/#post3999869) [threads](http://www.linuxquestions.org/questions/linux-networking-3/how-to-use-ssh-secure-shell-service-in-linux-813503/#post3999871) you [post](http://ubuntuforums.org/showthread.php?p=9444349#post9444349). 

And that's only one topic on two forums I frequent. Please stop - it's rude.

-------

Holy smokes. A google query for "How to use SSH(Secure Shell) Service in linux?" turns up a whole lot more hits. So are you a spam bot or what?

---

### Post by pricetech on 2010-06-11
More like a "spam human".  He has another thread which I just reported that includes links which ostensibly point to "his" system's specs, but actually go to some junk mail site of some kind as best I can tell.

Someone is trying to get banned maybe ???

---

### Post by bodhi.zazen on 2010-06-11
With those last two posts in mind I am going to close this thread now.

If you see dup threads please report them.

---

