---
title: "Isolating a Windows PC on a Linux network?"
date: 2015-02-17
forum: Security
---

### Post by greg69 on 2015-02-17
Other than getting an entirely different network and IP for the windows machine, Is there any way that I can seal off the windows PC from the other devices on the network, But still allow it access to the internet?
For example, If a cross platform virus attacked the windows PC I can prevent it spreading through the network?
I would also be running Ubuntu on the same PC as the windows partition. I don't need contact with the network on that partition either, Just a connection to the internet. I'd also like as little a delay as possible. For example if I had to force it through 10 firewalls and it caused a +50 ping spike, That wouldn't be ideal.

I would also be running daily ClamAV scans on the partition, As well as running BullGuard AntiVirus on the partition.

I know a determined cracker can get through a lot of stuff, But how difficult can I make it?

---

### Post by SeijiSensei on 2015-02-17
On your local network, machines communicate with broadcasts, so there's no single point where you can install filtering rules. You could add a simple iptables rule to /etc/rc.local on each Linux machine to block the Windows one.  Let's say it has IP address 192.168.1.50.  Then on each Linux box you could add the rule
```
/sbin/iptables -A INPUT -s 192.168.1.50 -j DROP
```
If these machine are already running a firewall, you'd need to integrate the rule into your current ruleset.

That said, a rogue Windows PC can do little damage to an Ubuntu desktop with a vanilla configuration.  By default Ubuntu desktops have no open ports and no running services, so they can't "hear" anything sent from the Windows PC.  If you share the disk on the Windows machine, and access files from it using some type of SMB or CIFS connection, then you could transfer infected files that way.  Again, though, nearly all Windows exploits expect to find Windows, not Linux, so there is little they can do.

Got any examples of a "cross-platform virus?" Other than browser-based exploits, what other ones do you know of?  Windows and Linux have very different architectures so it's hard to imagine a binary that would work equivalently on both platforms.  A lot of Windows malware expects to hide itself in the Windows registry, but Linux doesn't have anything like that.

---

### Post by greg69 on 2015-02-17
> [COLOR=#000000]Got any examples of a "cross-platform virus?"[/COLOR]
As far as I'm aware, Heartbleed was a major one, Affecting windows servers alongside linux ones.
Providing that it can't attack the Linux computers on the network, How about general vulnerabilities such as exposing the IP for DDoS attacks, broadcasting information about the network or acting as a 'Stepping stone' for a linux specific trojan, virus or rootkit to be injected into the other partition and, by extention, the network?

---

### Post by SeijiSensei on 2015-02-18
Heartbleed exploited a flaw in the OpenSSL stack.  Servers using OpenSSL on any platform were thus vulnerable.  That's not what I think of when it comes to a "cross-platform virus," which I see as an exploit that would be installed by opening a file or email.  Heartbleed was not that.  Nor would most be people be running an HTTPS server on their desktops that is open to the public Internet.

As for the other types of "network discovery" attacks you mention, they're certainly possible, but not because of your platform.  A denial-of-service attack is going to be mounted against your external IP address, regardless of what you have running behind the router. 

And, again, those hypothetical Linux attacks would be pretty hard to propagate from a Windows machine to one running Linux.  They're also pretty rare in the wild.  If you were sharing the Windows hard drive across the network and mounting it on Linux with CIFS, that would be one method. However I doubt there are many exploits for Linux that are hiding in Windows software.  I'd be putting Windows exploits in that.

I've run Linux on the desktop for nearly two decades without any additional protections beyond my firewall router.  I have a couple of Windows system on my home network as well.  The closest I ever came to getting any sort of malware infection on Linux was when The New York Times inadvertently distributed the bogus "Antivirus 2010" Javascript.  I could only laugh when my computer suddenly appeared to look like Windows and the program "found" dozens of infected .dll files on my "C: drive."  Of course Linux has no C: drive and no DLL files either.

---

