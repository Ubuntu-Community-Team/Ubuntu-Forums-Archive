---
title: "UFW isn't blocking?"
date: 2010-09-11
forum: Security
---

### Post by bone2006 on 2010-09-11
I installed a fresh copy of ubuntu 10.04 and then issued

$sudo ufw enable && sudo ufw default deny && sudo ufw logging on && sudo ufw status

I then went on to install virtualbox and just assumed it wouldn't be able to get internet access, but it appears to have full access.  

Wondering why

---

### Post by hhlp on 2010-09-11
is better for tou using and GUI try to install this and test ufw firewall :

```
sudo aptitude install gufw
```

---

### Post by OpSecShellshock on 2010-09-11
It's not going to block outbound connections initiated from your local machine (there wouldn't really be a point to that under most usage conditions). All it's going to do is block incoming attempts from external hosts to initiate connections to your computer (which won't work even without ufw if there's nothing listening for such connections in the first place).

---

### Post by uRock on 2010-09-11
Installing GUFW will give you the needed power to block outgoing connections, such as blocking a virtual machine, though you would still have to find which port VBox uses as it will not use all of the different ports the way that the host uses them.

---

### Post by bone2006 on 2010-09-11
Isn't gufw just a graphical interface to ufw?  I'd prefer to learn how to do it on the command line, simply because I have a few servers that don't have any desktop environment.  I control them via ssh.   So for me the command line would be much better if I can learn something I'm not doing?

I looked at the man for ufw and see this entry
ufw [--dry-run] default allow|deny|reject [incoming|outgoing]

But everything i'm reading it appears ufw won't block outgoing.  Maybe I need to use appamor for the one I want to block outgoing.

---

### Post by CharlesA on 2010-09-11
If you ***really*** want to block outgoing traffic just use iptables (ufw is just a frontend for them).

As for not allowing VMs to access the internet, just don't give them a gateway or set them up on a seperate subnet.

---

### Post by bone2006 on 2010-09-12
ufw is pretty uncomplicated after all

$sudo ufw default deny outgoing

---

### Post by bodhi.zazen on 2010-09-12
Basically, ufw, by default, blocks NEW incoming connections, but allows outgoing connections and incoming RELATED and/or ESTABLISHED connections.

Managing outbound connections is a bit more complicated.

Virtualization is one step more complex. Are you using NAT or a bridged connection ? You need to consider firewalls on both host and guest.

I suggest you read up on iptables when you have time.

---

### Post by bone2006 on 2010-09-12
I could disable internet completely on my virtualbox, but I guess it's not the issue.  

I know most things are blocked based on ports instead of applications, which I have seen an easy tutorial on using iptables, but I was hoping that I could use ufw instead, since it's so much easier to use.

Blocking by ports isn't always ideal compared to per application.  First thing a person will say is know what your installing.  But sometimes apps try to update or do things online that you just don't want it to have internet access.

I originally thought it blocked out going, except for known installed apps like firefox...etc that came with the machine.  It's when I installed virtualbox and it had full access, it kind of surprised me.  I thought I was going to have to go into ufw and allow it.

I thought I would be able to create a profile here as well
/etc/ufw/applications.d/, which it appears again to be just based off ports.

I know there's a tutorial here for allowing per application using iptables.  This pretty much does what I'm looking for, it would just be nice to have an easy command line way of allowing or denying applications and not ports for outgoing
[http://ubuntuforums.org/showthread.php?t=1188099](http://ubuntuforums.org/showthread.php?t=1188099)

I didn't know much about apparmor, but found out quickly it's more of a sandbox type of protection. Really happy to learn more about it.

---

### Post by CharlesA on 2010-09-12
The firewalls in Linux don't operate the same as the ones in Windows (where if a new app tries to access the internet/networking, you are notified).

As far as I know, you can't block a specific application from accessing the internet, but I think you can limit what it can do by using AppArmor.

---

### Post by bone2006 on 2010-09-12
> **CharlesA said:**
> The firewalls in Linux don't operate the same as the ones in Windows (where if a new app tries to access the internet/networking, you are notified).

As far as I know, you can't block a specific application from accessing the internet, but I think you can limit what it can do by using AppArmor.

I wouldn't want it to warn me like most windows. 
I don't care about notification.  I'm not sure if you read all the posts, but there's a tutorial I posted the link that shows how to block per application.

---

### Post by CharlesA on 2010-09-12
> **bone2006 said:**
> I wouldn't want it to warn me like most windows. 
I don't care about notification.  I'm not sure if you read all the posts, but there's a tutorial I posted the link that shows how to block per application.

Thanks for the link. :)

---

### Post by bodhi.zazen on 2010-09-12
> **bone2006 said:**
> I know there's a tutorial here for allowing per application using iptables.  This pretty much does what I'm looking for, it would just be nice to have an easy command line way of allowing or denying applications and not ports for outgoing
[http://ubuntuforums.org/showthread.php?t=1188099](http://ubuntuforums.org/showthread.php?t=1188099)

I didn't know much about apparmor, but found out quickly it's more of a sandbox type of protection. Really happy to learn more about it.

That is an old thread, it would work, but apparmor is better (more secure).

Restricting per application is a very windows centric perspective, if there is a host or destination you wish to block, blacklist it, via iptables or /etc/hosts.deny or what have you.

If you want to know what an application is doing, use wireshark or strace.

Or relax and enjoy Linux. There is no known spyware in Linux.

---

