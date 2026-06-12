---
title: "ssh problem"
date: 2008-04-22
forum: Security
---

### Post by sjm-ec on 2008-04-22
I'm having trouble with sshd not responding to login attempts from outside the local subnet.  I am trying to log into a machine at a different site across a VPN connection.  

I try ssh directly and it times out.

I ssh into another (RedHat based) machine at the site and use that to ssh into the target machine and it works.

There is no firewall on the target machine (iptables is completely open).

The routing is fine (after sshing through the other machine into the target machine I can ping back to the box I am on.)

It looks like someone else had this problem, but there was no resolution:
[http://ubuntuforums.org/showthread.php?t=547726](http://ubuntuforums.org/showthread.php?t=547726)

Do you have any pointers as to where to look for the restriction?

---

### Post by Joeb454 on 2008-04-22
It could be the restrictions on the machine you are using, I have to use a similar method at University - ssh to the server to ssh to my home server :)

---

### Post by sjm-ec on 2008-04-22
I don't think it's my machine.

From my machine (192.168.129.13) I can ping the target (192.168.138.203) but have to first ssh into another remote machine (192.168.138.3) before jumping from there to the target machine.  

On my machine I have an open OUTPUT chain for iptables and a general ACCEPT for RELATED and ESTABLISHED connections in the INPUT chain.

---

### Post by sjm-ec on 2008-04-22
Well, I think it was the VPN firewall on the remote end.  I was able to move the target machine to another IP in the same range as the one I was able to have direct access to and can now ssh directly to that machine.  Thanks.

---

### Post by aallxx on 2009-09-29
hi, 

have you tried 'ssh -vvv targethost' from both origins and
compare the resulting logs? in this verbose mode, ssh will
inform you about every step it is going to do and give you a
very good ideia on where in the process it hangs

hope it helps,
alex

---

### Post by mohnkern on 2009-09-29
Always start by looking at your /etc/hosts.allow and /etc/hosts.deny file.  Make sure you're not blocking it there.

While there isn't a firewall on your machine, is there one that is covering your local subnet?  perhaps its blocking connections?    

Also, are you doing NAT behind a firewall?



> **sjm-ec said:**
> I'm having trouble with sshd not responding to login attempts from outside the local subnet.  I am trying to log into a machine at a different site across a VPN connection.  

I try ssh directly and it times out.

I ssh into another (RedHat based) machine at the site and use that to ssh into the target machine and it works.

There is no firewall on the target machine (iptables is completely open).

The routing is fine (after sshing through the other machine into the target machine I can ping back to the box I am on.)

It looks like someone else had this problem, but there was no resolution:
[http://ubuntuforums.org/showthread.php?t=547726](http://ubuntuforums.org/showthread.php?t=547726)

Do you have any pointers as to where to look for the restriction?

---

