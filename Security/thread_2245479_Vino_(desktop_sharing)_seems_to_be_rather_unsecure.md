---
title: "Vino (desktop sharing) seems to be rather unsecure.  Should I submit a bug?"
date: 2014-09-23
forum: Security
---

### Post by em3raldxiii on 2014-09-23
I'll keep this brief.  Also, for what it's worth, I'm a long-time Ubuntu user.  Running Ubuntu 14.04, mostly fresh install.

1. Today, after I shut down a Steam game I was playing, I had the all-too-familiar message saying that Ubuntu had an internal error.  The difference this time was that it was *Vino* that was the source of the trouble.  (I did send the error report)
2. I opened the dash, typed in VINO and opened the Desktop Sharing application.  This made me realize that [B]remote desktop was enabled with full access, no password was entered, and no confirmation was required.
[/B]3. It's important to note that **I have never started desktop sharing on this machine; how was this started?**
4. When I de-selected, and re-selected, and de-selected the checkbox it never once asked me for my password.  Maybe I am wrong, but I sorta feel like this application should have the _unlock_ feature that is used in the users & groups application (etc).

In summary:  How was this application started, was it enabled by default?  I _guarantee_ that I have never started the application.  And why didn't the application require that I enter a password to make changes?  Isn't this a fairly significant security breech?  Should I pursue this further with a real bug report, etc?

---

### Post by sammiev on 2014-09-23
After reading your post I checked 4 installs of 14.04 and 4 installs of 14.10 and desktop sharing was off by default as I never used it. Something I will check on here and there.

---

### Post by Irihapeti on 2014-09-24
My understanding is that vino is disabled by default. However, it does seem to be perilously easy to enable. I don't understand why it's installed by default, and if I'm doing an installation from a liveCD (not all that often these days), it's one of the first applications I remove.

A few years back I tried bringing this point to the attention of the developers, but got dismissed rather rapidly. I'm not sure what it would take for them to consider that maybe it's a serious problem.

Certainly, vino and ssh are the two commonest breaches we see in this sub-forum.

---

### Post by cogset on 2014-09-25
> **Irihapeti said:**
> My understanding is that vino is disabled by default. However, it does seem to be perilously easy to enable. I don't understand why it's installed by default(...)

A few years back I tried bringing this point to the attention of the developers, but got dismissed rather rapidly. I'm not sure what it would take for them to consider that maybe it's a serious problem.

Certainly, vino and ssh are the two commonest breaches we see in this sub-forum.

I couldn't agree more,I really can't figure out why SSH and remote desktop are installed by default in all Ubuntu versions I've been using so far (the only exception that comes to mind being Lubuntu,which "only" has SSH):how can they be considered essential for an average home user,and how can the possible advantages of having them outweigh the potential safety issues,in the case of a normal user?

If someone really needs this stuff,will be certainly able to find and install it-there's really no point IMO in including it in a standard CD.

Also in light of all the recent disclosures about  security holes (the latest being the bash vulnerable to arbitrary code execution via SSH and other remote interactions),such decisions should be reconsidered.

---

### Post by Irihapeti on 2014-09-25
The SSH server isn't installed by default. Only the SSH _client,_ i.e. what you need to log into some other service - it doesn't let anyone access your machine.

The SSH hacks that we see here usually arise because someone installs SSH server and doesn't realise how to secure it properly.

---

### Post by cogset on 2014-09-26
> **Irihapeti said:**
> The SSH server isn't installed by default. Only the SSH _client,_ i.e. what you need to log into some other service - it doesn't let anyone access your machine.


Right,I always forget that.As I also forgot that telnet is installed by default,another issue that I can't understand.

I mean,SSH (even the client alone),telnet,remote desktop,they all are advanced tools:if you need them,you will surely know how to find and install them.
Why do they need to be included in a normal desktop install?

---

### Post by steeldriver on 2014-09-26
Same as for SSH, for telnet it is only the **client** that is installed. I don't see how that is any more of a problem than any other outgoing protocol - would you suggest removing all web (http) clients as well?

I agree about vino though - imho at the least, it should be configured by default to only allow SSH tunneled connections (interface = 'lo')

---

### Post by cogset on 2014-09-30
> **steeldriver said:**
> Same as for SSH, for telnet it is only the **client** that is installed. I don't see how that is any more of a problem than any other outgoing protocol - would you suggest removing all web (http) clients as well?


I don't expect everyone to agree,but I would in fact strip down the outgoing protocols in a default desktop installation to web browser,email client and package management (of course),and that's it.
Maybe also a torrent and chat client,but really no SSH,telnet,remote desktop or any other similar application.

Can you figure out a scenario where someone really needs to use SSH,telnet,or remote desktop,but can't even figure out where to find it or how to install it? Then he shouldn't use this stuff at all.

---

### Post by em3raldxiii on 2014-10-12
Wow, I didn't realize that I had stumbled upon a bit of a sore point!  I guess I'm not crazy after all.  Also, as an aside, I had forgotten to subscribe to my own thread, and so I didn't know anyone had replied.  

I agree that VINO should not be installed by default - because it's a server, and because it _obviously_ can be started without any security intervention (I *absolutely* guarantee that it was never started by a local user), it's clearly a very dangerous tool.

The rest, (telnet et al) could indeed be installed by the user post OS install; but I also agree with those suggesting that those don't present nearly as much of a security vulnerability.  I think we should take baby steps, and see about getting VINO removed from the default install.  It just seems far too vulnerable.

---

### Post by cariboo on 2014-10-12
If you are serious about getting vino removed from the default installation, the place to start is the [ubuntu-devel-discuss]("ubuntu-devel-discuss@lists.ubuntu.com") mailing. Be prepared to defend why you want it removed, as some of the developers can be quite obtuse.

---

### Post by bashiergui on 2014-10-12
Firstly, if you enable vino and are behind a router, no one can connect from the Internet unless you port forward on the router. 

IMHO it's overbearing to remove RDP, ssh, and telnet *clients* from default installations. Ubuntu is not my mom. I don't want it making decisions like it is.

Aside from that, removing the clients doesn't actually improve the security at all. It completely deflects from true security improvement like enabling apparmor, ufw, noscripts, and adblocker.

---

### Post by em3raldxiii on 2014-10-13
Bashiergui, while I agree that an outside attacker would be unlikely to be able to gain access to a machine that's behind a router, passing the buck for security to an upstream device is not a great policy.  The thing is, you and I both know that millions of people are behind routers with terribly security policies - everything from bad passwords (or none) to using DMZ and loose port forwarding rules in general.  I'm not terribly concerned about the *clients* but rather the fact that VINO allows pretty open access to much of a machine, especially if someone just wants to do a little surveillance.  Creepy stuff!

---

### Post by em3raldxiii on 2014-10-13
Also Cariboo, thanks for the link.  I'll bookmark it and sleep on it.

---

