---
title: "Before nuking firestarter, I got questions."
date: 2010-01-03
forum: Security
---

### Post by teward on 2010-01-03
Alright, for a while I've been using Firestarter because its easy to use and it programs iptables.

Now, knowing that it programs iptables, I thought, "I'll nuke Firestarter and program iptables manually."

Now, questions.  
(1) How do I go about nuking Firestarter?  I've also seen conflicting information regarding having to reset iptables.  Do I need to do that?

(2) I run an SSH server on my computer on port X.  how do I allow incoming traffic to port X using iptables?  Also, how do I deny incoming access on all other ports?

(3) I wish to block site XYZ and do not want to provide the IP address for blocking.  How do I deny outgoing traffic to site XYZ using iptables?

(4) I would like to enable ICMP filtering, and to deny any ICMP protocol activity, essentially denying any ICMP packets (this includes the following: Echo request, Echo reply, Timestamping, MS Traceroute, Traceroute, Unreachable, Address Masking, Redirection, Source Quenching.  these were listed on Firestarter).

Also, is there something I have to do to make the configuration persistient, or will it work automatically on boot all the time?

Please note I'd like to code this with only iptables and the command line, so any help would be GREATLY appreciated, as I like to not mess with things using the CLI unless I can avoid it, but in this case it helps to only use CLI.

Thanks.

**EDIT: Added questions to the list. **

---

### Post by teward on 2010-01-03
Also, and I keep having to append this, is there a program that I can use that replaces Firestarter and does the same thing of programming IP tables in an easy to use interface, just in case I dont want to use the CLI all the time?

---

### Post by sliketymo on 2010-01-03
Gufw

---

### Post by teward on 2010-01-03
okay, with that question answered, what about getting rid of Firestarter?  how do I do that and switch the firewall configuration program over to Gufw or something else?

Also, will iptables remain persistent each time I boot if I use Gufw or plain old iptables?

---

### Post by FuturePilot on 2010-01-03
> **TrekCaptainUSA said:**
> okay, with that question answered, what about getting rid of Firestarter?  how do I do that and switch the firewall configuration program over to Gufw or something else?

Also, will iptables remain persistent each time I boot if I use Gufw or plain old iptables?

```
sudo apt-get remove --purge firestarter
``` will completely remove it.

If you use UFW or GUFW the settings will be persistent across reboots. But if you're using Iptables directly you will have to come up with a way to have your rules get loaded on bootup. See this for a good overview of iptables [http://bodhizazen.net/Tutorials/iptables/]("http://bodhizazen.net/Tutorials/iptables/")

---

### Post by teward on 2010-01-03
will purging firestarter erase the data in iptables right now?  will I have to reprogram it?

---

### Post by FuturePilot on 2010-01-03
> **TrekCaptainUSA said:**
> will purging firestarter erase the data in iptables right now?
IIRC no. You will have to reboot or manually flush iptables.

> will I have to reprogram it?
Eventually, yes.

---

### Post by teward on 2010-01-03
alright, so make note of what I need to configure.  Thanks for the help.

---

