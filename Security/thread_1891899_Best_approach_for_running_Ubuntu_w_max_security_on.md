---
title: "Best approach for running Ubuntu w/ max security on Macbook"
date: 2011-12-06
forum: Security
---

### Post by Rubicon421 on 2011-12-06
I have a Macbook Pro from work that I will be taking on a business trip and will be getting on public wifi. I don't have Linux installed natively on it (nor am I allowed to) but I do have an Ubuntu VM installed in VMWare. I'd like to make sure I have the most secure setup that I can (reasonably) achieve before I get on public wifi with my work computer. 

So, my question is, would there be a significant difference in security between running Linux in a VM and booting into a LiveCD of the same distro with the same configuration?All on line activity in the VM scenario would be from within the VM, (not the native OSX installed browser) but the traffic would be passed through the virtual adapter to the actual hardware.

I have my VM configured how I like it so it wouldn't be as convenient to use a LiveCD, but if it's significantly safer then I would still do it. What's the best option? I have also considered setting up a VPN server at home before I leave, but I've never set one up before and don't know what program to use. Any ideas?

---

### Post by Ms. Daisy on 2011-12-06
One of the problems with using a public wifi is a "man in the middle", which is a malicious person who intercepts your communication over the public wifi.    If you run a virtual box or a live CD, the traffic will still be sent  over the same wifi connection and it can still be intercepted. To prevent interception, you want to encrypt your traffic, use a secure shell (SSH) over virtual network computing (VNC), or create a VPN like you said.

However, they must be set up properly to secure the servers & machines themselves.  See the security sticky, [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) for important security measures on SSH & tunneling VNC in Ubuntu. To quote the sticky "The two most common cracks posted on these forums are SSH & vnc, both running with password authentication."  

I know next to nothing about Macs, but I'm sure they have similar features if you want to implement them in the Mac host instead of in your Ubuntu virtual machine.

edit: if you choose to set up a VPN in Ubuntu, see this [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

### Post by OpSecShellshock on 2011-12-06
Before planning anything else, be sure to check with the folks at work as to whether you're even allowed to connect the work computer to public wifi.

---

### Post by Dangertux on 2011-12-06
> **OpSecShellshock said:**
> Before planning anything else, be sure to check with the folks at work as to whether you're even allowed to connect the work computer to public wifi.


This and...

To answer your question about which is technically more secure, I would say the VM is more secure. Hypervisor escalation is much more difficult than mounting a filesystem and writing data to it, particularly if it's Mac OSX.

Just food for thought. 

Again, to reiterate what OpSecShellshock said make absolutely sure that it's acceptable to use public wifi, many companies have security policies against such things. Also you may wish to ask if there is a VPN you can use on your business trip while you're connecting over public wifi. Many sysadmins will be more than happy to provide you with that for at least a temporary duration.

---

### Post by Rubicon421 on 2011-12-06
> **OpSecShellshock said:**
> Before planning anything else, be sure to check with the folks at work as to whether you're even allowed to connect the work computer to public wifi.

I am, I'm just being extra cautious. We don't deal with any sensitive data at work. My main concern is protecting my personal data/traffic with the limited control I have over what I can change, being that it is my work computer. If it were mine, I would run Ubuntu natively and have it set up how I want.

---

### Post by wojox on 2011-12-06
Between Ubuntu VM installed in VMWare or a persistent flash drive.
I would go with persistent drive every time. :P

---

### Post by Rubicon421 on 2011-12-06
> **Dangertux said:**
> This and...

To answer your question about which is technically more secure, I would say the VM is more secure. Hypervisor escalation is much more difficult than mounting a filesystem and writing data to it, particularly if it's Mac OSX.

Just food for thought. 

Again, to reiterate what OpSecShellshock said make absolutely sure that it's acceptable to use public wifi, many companies have security policies against such things. Also you may wish to ask if there is a VPN you can use on your business trip while you're connecting over public wifi. Many sysadmins will be more than happy to provide you with that for at least a temporary duration.

Good point. I was more thinking along the lines that the VM would be less secure since all security settings could be rendered null and void if the native OSX settings weren't appropriate. But if the data I am concerned about protecting is outside the VM then that would make unwanted external access to it very difficult for someone to accomplish.

---

