---
title: "Help please!!!"
date: 2008-05-09
forum: Virtualisation
---

### Post by quackquack on 2008-05-09
yeah everyone just ignored my other thread so i am making a new one exactly the same as the last. Please can someone reply this time. 

-----------------------------------------------------------------------------Hello,

I have an Olivetti Any_Way Photo Wireless Plus printer and it doesn't work in Ubuntu. I have virtualbox and i have installed windows 2000 to a virtual machine. I wondered if it would be possible to install the printer in windows 2000 and share it to ubuntu so as i can print to it while the virtual machine is running. I have tried installing the printer (the printer is set up correctly) and the install wizard doesn't detect the printer on the network (i want to install it wirelessly). I use NAT for my virtual machine and the internet works fine. I thought that maybe the problem was that NAT only gives access to a virtual network to my host and then my host connects to the internet which would explain why it can't access network resources outside of my computer. I wondered if using host interface instead would solve the problem, but i can't figure out how to do it.

I have tried this guide:
[http://ubuntuforums.org/showthread.php?t=346185]("http://ubuntuforums.org/showthread.php?t=346185")

and changed the ip addresses and network interface names to what they are on my computer and followed the guide properly and when its done i can't start the virtual machine, I have this error message:


Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code:
0x80004005
Component:
Console
Interface:
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


Also, it is worth noting that when i run the commands in the thread it gives me a bunch of error messages for a lot of them.

Is host interface what i need to set up to use the printer? Would it work in the way i explained at the top of the post? If so, can somebody please explain (or link me somewhere that explains) how to set up host interface.

Thanks in advance

---

### Post by ACMarina on 2008-05-09
I've mostly given up on virtualbox but I can guess at this..

Have you configured your virtual machine to use USB??  I wouldn't think you'd need to do anything with IP addresses or anything to get it working - I didn't have to..

---

### Post by quackquack on 2008-05-09
thanks for replying

that probably would work, but i would really like to have it working wirelessly. 

anybody else got any ideas?

---

### Post by Siph0n on 2008-05-09
The title of your thread s**ks. That could be one reason why people aren't answering it. Try using a more descriptive title next time. Does VirtualBox OSE support USB devices? I thought I read somewhere that only the closed source version did.

---

### Post by quackquack on 2008-05-10
no. the thread was actually "Sharing a printer" which is relavent to the problem. Of course, people would know that if they actually looked at it. To be honest, i dont care that the thread title sucks. If nobody bothered to look at the first one, why should i bother to name the next one properly?

and i just said i wanted it to work WIRELESSLY. that means no wires. not even a USB one, because a usb cable is a wire, which would make the WIRELESS statement false. 

anyone else got any ideas? (preferably not rude ones that critisize my thread)

---

### Post by Nampla on 2008-05-14
I think your problem is mutli-fold. Have you looked at vmware?  I have had little sucess with virtualbox.  I can get wireless printers working and netowrk sharing done easily with vmware server, player, and desktop.  I also would reccomend using XP cuz 2000 probably doesnt support your printer. WIn 2000 is pretty short on drivers. 
If you insist on staying with virtualbox try getting to your router web page with ie in your win vm.  If you cant then you are in need of network tuning. Make sure your virtual network adapter is bound and set to your correct real network hardware. 
good luck

---

### Post by quackquack on 2008-06-10
thankyou for your reply :)

i have my printer connected in virtualbox and shared, and i can get to it from ubuntu, but the thing is it wants a driver, which doesn't exist for ubuntu. I guess ill just have to print from virtualbox.

---

