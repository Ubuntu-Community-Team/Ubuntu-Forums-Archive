---
title: "Running Ubuntu on desktop. Do I need firewall or anti-virus software?"
date: 2013-06-04
forum: Security
---

### Post by postt on 2013-06-04
Right now I don't have any protection other than installing Ubuntu updates when they are available. Do I need to run firewall or anti-virus software? If so which software would you recommend?

---

### Post by BBQdave on 2013-06-04
[**GUFW**]("http://gufw.org/") is an easy Firewall program to use.

As far as anti-virus, the short answer is Linux has anti-virus protection built in. You should be cautious however, in loading any software that is not from Ubuntu's repos.

And set a strong pass word for your system :)

---

### Post by ahallubuntu on 2013-06-04
~

---

### Post by ahallubuntu on 2013-06-04
~

---

### Post by Bucky Ball on 2013-06-04
*Thread moved to **Security Discussions**.*

---

### Post by BBQdave on 2013-06-04
> **ahallubuntu said:**
> What do you mean????

Secure - Trusted Repos and Strong Admin - *sudo* - password help harden a Linux system. No extra *security* software needed to protect from malware and virus install, such as *Norton* Anti-Virus programs.

And as always, user behavior goes a long way toward how secure a system remains, regardless of what OS you use.

---

### Post by gordintoronto on 2013-06-04
If you are behind a router, and you trust the other computers on your network, skip the firewall.

The Linux anti-virus programs scan for *Windows* viruses, so you don't accidentally send malware as an email attachment. (Etc...) They do not add security for your computer.

---

### Post by uRock on 2013-06-04
> **ahallubuntu said:**
> What do you mean????

Probably in reference to the way downloaded files and such are not executable. The way AppArmor sandboxes applications.

I do believe in having a firewall running even though my router handles things well.

---

### Post by 3rdalbum on 2013-06-04
uRock: Running a personal firewall AND having one in your modem is like cutting the telephone cables to your property and then unplugging your phone from the wall socket and getting an unlisted number.

The last two steps are a waste of time.

By default, your router will block all incoming connections from the internet. All of them. Your personal firewall will see NOTHING. It will do exactly nothing.

---

### Post by uRock on 2013-06-05
I trust my Cisco router as far as I can throw it. Host based firewalls can stop outbound connections. Routers can be programmed to do the same, but every household router I have worked with crashes when I start creating ACLs. My software firewall stopped the nearly 100 Amazon connections ubuntu 13.04 in a VM tried to make when I first tested that release.

My network has a layered defense strategy to protect every host from each other. Last thing I need is someone with a phone riddled with malware connecting to my network and mapping it. I am not rude enough to tell people they can't connect. They are free to connect to my router and free to grab a beer.

I am also building a webcam server on my network and will be forwarding ports, so I can watch my house from work.

When I finally get my hands on a commercial router, which will let me create as many ACLs as I need for each host, I will lessen the efforts I put on my hosts being perimeters and end points.

[http://www.darkreading.com/end-user/fact-check-endpoints-are-the-new-perimet/240155722](http://www.darkreading.com/end-user/fact-check-endpoints-are-the-new-perimet/240155722)
[http://www.darkreading.com/end-user/endpoint-security/240155825?pgno=1](http://www.darkreading.com/end-user/endpoint-security/240155825?pgno=1)
[http://www.darkreading.com/management/3-lessons-from-layered-defenses-missed-a/240155697](http://www.darkreading.com/management/3-lessons-from-layered-defenses-missed-a/240155697)
(You can only read two a day without creating an account.)

---

### Post by postt on 2013-06-05
> **gordintoronto said:**
> If you are behind a router, and you trust the other computers on your network, skip the firewall.



My computer is plugged directly into the cable modem. There's no router, so I guess I should run a firewall?


> The Linux anti-virus programs scan for *Windows* viruses, so you don't accidentally send malware as an email attachment. (Etc...) They do not add security for your computer.

I see. Any way to protect against Linux viruses then? If I visit a webpage or download software outside of the official repositories, is there any way to scan for viruses and make sure my computer doesn't get infected?

---

### Post by Velnias on 2013-06-05
Linux way is white-listing.
No sane, educated, person trust any antivirus company, who proved many times to be incompetent and malicious ( naming as viruses benign illegal content ).

Learn about security and ignore that profit generating security theater. 

And yes, Canonical needs community involved security  analysts and advisers.

---

### Post by gordintoronto on 2013-06-06
> **postt said:**
> My computer is plugged directly into the cable modem. There's no router, so I guess I should run a firewall?

Any way to protect against Linux viruses then? If I visit a webpage or download software outside of the official repositories, is there any way to scan for viruses and make sure my computer doesn't get infected?

If you don't have a router, you need to run a Firewall.

There are currently no known Linux viruses "in the wild," so a Linux virus scanner would have nothing to scan for. There is a known Trojan:
See [http://askubuntu.com/questions/181930/what-to-do-regarding-backdoor-wirenet-1](http://askubuntu.com/questions/181930/what-to-do-regarding-backdoor-wirenet-1)

In short, if you don't have a WIFIADAPT folder, you don't have the trojan. If you create a read-only *file* with that name (in Home), the trojan can not be installed. (Note that the name is all upper-case.)

---

### Post by maglinu on 2013-06-06
A bit of googling suggests that BackDoor.Wirenet.1 is now detected by all the windows av scanners - including I would think, the Linux versions from clamav, comodo, bitdefender, avast etc.

It would be interesting to know how long they took to start detecting it.

---

### Post by HermanAB on 2013-06-09
This is still one of the best explanations of why you don't need anti-virus on Linux:
[https://www.gnu.org/fun/jokes/evilmalware.html](https://www.gnu.org/fun/jokes/evilmalware.html)

---

