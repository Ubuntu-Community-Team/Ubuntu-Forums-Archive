---
title: "Basic home network traffic monitoring, recommendation?"
date: 2010-05-09
forum: Security
---

### Post by bobnutfield on 2010-05-09
Hello Everyone,

I was reading a magazine article today which was a discussion of internet detective work for tracking down ip addresses which attempt an ssh login to your machine.  I have never really paid much attention to network security since I only run a small home network.  I have WPA encryption and a firewall on my router.  But while reading this article, I remembered that I myself has seen log files in the past that inidicated someone somewhere had attempted to log into my machine (attempts all failed).  This had happened a few times, but I never really considered it a threat.

But, the more I read about home computers becoming "zombies" for criminals, I guess I am getting a little paranoid in my old age, particularly since my wife does quite a bit of business on the net with credit cards.  I have four computers connected to the net and each other on this network, and would like to be able to easily detect attempted log ins and deal with them quickly.

So my reason for posting is to ask if someone could recommend a novice-friendly application for monitoring traffic to check this intermittently.  I have read bodhi.zazen's excellent tutorial on snort, but I it appears to be written for large lan's or web servers and is over-kill for a small home network.

I am a seasoned Ubuntu/Linux user, but not an expert.  So if someone could offer a recommendation, I would appreciate it.  GUI preferable, but not mandatory.

Any thoughts appreciated.

---

### Post by Kinstonian on 2010-05-09
It sounds like you're a lot more familiar with Linux than network traffic.  So for now, you'd probably be better off using something like a HIDS like OSSEC to monitor logs and system activity/integrity, rather than all the software you'd need to properly analyze the communication and investigate suspicious network events.

---

### Post by OpSecShellshock on 2010-05-09
The "zombie" computers that get incorporated into botnets are not acquired through network-based attacks. If you set up a network monitoring tool and watch for incoming attempts to access devices on your network, you aren't going to see much of value. Servers get logged into and controlled remotely. Desktops/workstations are compromised through a combination of web browser activity and the download and installation of malicious software. In those cases, the malware manipulates or replaces files associated with legitimate processes and disguises itself as normal traffic.

---

### Post by jetsam on 2010-05-09
Nethogs is a very simple to use command line tool that will let you know if a running process is using more bandwidth than it should.

Wireshark is good to look at in real time for much more detailed information.  Quiet your network, close the browser, and run Wireshark on your machine of concern and tell it to sniff the main interface.  Things should be appearing there: packets.  You can delve as deeply into this as time and attention allow.

So those are two real time tools that can give you some insight into what your network is doing behind the scenes.  They both need to be run with sudo or gksu from a terminal to have permission to do their jobs.

As for long term monitoring...  I need more info on this myself, but there should be a way to set open ssh up to email you if it detects suspicious login attempts.

---

### Post by bobnutfield on 2010-05-09
> **Kinstonian said:**
> It sounds like you're a lot more familiar with Linux than network traffic.  So for now, you'd probably be better off using something like a HIDS like OSSEC to monitor logs and system activity/integrity, rather than all the software you'd need to properly analyze the communication and investigate suspicious network events.

This is quite true, but since starting this thread I have installed Wireshark and have been reading the tutorials and experimenting with it.  It does provide an awful lot of information.  I am amazed at what this application can find.  I have also learned that it can be used for bad things as well.

However, Wireshark is probably only of any use for this when it is running, so unless it is running all the time (which is silly on a home network), I could only catch a problem if it occured during a running session.  I think you are correct in that it would be much more useful to understand the log files that already exist.

This all very good information to know, and I appreciate the response of everyone.

---

### Post by bobnutfield on 2010-05-09
> **OpSecShellshock said:**
> The "zombie" computers that get incorporated into botnets are not acquired through network-based attacks. If you set up a network monitoring tool and watch for incoming attempts to access devices on your network, you aren't going to see much of value. Servers get logged into and controlled remotely. Desktops/workstations are compromised through a combination of web browser activity and the download and installation of malicious software. In those cases, the malware manipulates or replaces files associated with legitimate processes and disguises itself as normal traffic.

That is good to know.  My download activity is limited to the repositories and the occassional PDF.  I know that the risk of virus is low, but my knowledge of root kits and how they operate needs to be improved.  Are they a threat?  Who is most vulnerable to root kits?

---

### Post by OpSecShellshock on 2010-05-09
> **bobnutfield said:**
> That is good to know.  My download activity is limited to the repositories and the occassional PDF.  I know that the risk of virus is low, but my knowledge of root kits and how they operate needs to be improved.  Are they a threat?  Who is most vulnerable to root kits?

Rootkits are mostly a risk on servers, since servers allow for the initiation of remote connections in order to function. When combined with a vulnerable web application, this can allow for the creation of the access needed in order to install a rootkit.

On a desktop system, a user with administrative privileges would need to be convinced to install it, then it would also need backdoor properties that would enable it to "call home," and on top of that the firewall would still need to be reconfigured such that an incoming connection would be successful (though arguably it could be written to retrieve commands automatically instead--but every time it did so during a user-level session it would require escalation to install or reconfigure anything at the system level).

The main purpose of a rootkit is to remove evidence of unauthorized behavior from an already compromised system. It's only really dangerous in combination with a backdoor (which is an academic distinction at this point since any decent malware will have the properties of both). On a desktop configuration, such a thing couldn't install itself automatically, though the risk increases greatly if remote desktop is enabled and there are ports forwarded on the router.

---

### Post by bobnutfield on 2010-05-09
Thanks for that.  I don't think I am at too much risk for that then.  Linux has the reputation for being a secure operating system, I guess I have never spent enough time actually thinking about it until recently.  I am just a normal desktop user, but I do enjoy experimenting and I have a number machines on my home network. My wife is the only one who uses Windows.

But, you've given me enough information to study on...

Thank you.

---

### Post by OpSecShellshock on 2010-05-09
No problem. I think it's tricky at first to conceive of the differences between operating systems when it comes to matters of security. For example, while Linux on the desktop does have a reputation for being "(more) secure" than others, I think it's more accurate to say that it's less insecure. From a functional standpoint alone they mean basically the same thing, but from a design perspective there's a subtle difference between something being "secure" and something being "not-insecure." To a large extent, it's simply a matter of elegance. But the elegance of the design feeds directly into the risk level, and you have to honestly and carefully assess your risks before you can choose how best to implement a security strategy. I mean, if enough "non-insecurity" is built in, then less "security" needs to be added on, right?

---

