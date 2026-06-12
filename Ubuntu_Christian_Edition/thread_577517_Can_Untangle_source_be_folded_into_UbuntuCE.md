---
title: "Can Untangle source be folded into UbuntuCE?"
date: 2007-10-16
forum: Ubuntu Christian Edition
---

### Post by chris308 on 2007-10-16
I have been researching firewall/content filtering solutions for a small Christian school I do volunteer work for and ran across Untangle.  It's GUI for configuring the firewall, dansguardian, dhcp is amazing.  Since this is an open source project can UbuntuCE incorporate some of these features into our beloved distro?  It would be great if it can.  I see this leading to a perfect back end solution for small schools and church networks.  Perhaps a fork project called "UbuntuCE Server"??? 

Here is a link for more info:  [http://untangle.com]("http://untangle.com")

---

### Post by jonathonblake on 2007-10-16
[QUOTE=chris308]I see this leading to a perfect back end solution for small schools and church networks.  Perhaps a fork project called "UbuntuCE Server"?[/QUOTE]

Untangle is meant to run as a router, not a desktop.   That said, some functionality might be useful for a desktop.

If I was migrating an organization to Ubuntu Christian Edition, what I'd do is use Untangle as the router, and Ubuntu Christian Edition on all of the desktops.  (I'd also set up a server in the DMZ,to block web trackers and the like.  A second server would function for collaborative work, such as an internal wiki.)

xan

jonathon

---

### Post by chris308 on 2007-10-16
Thanks for the reply.  You're correct that the standard UbuntuCE is best suited for the desktop, but I was hoping that some of Untangle's additional features could be added or a script to easily install that functionality into UbuntuCE.  Wouldn't it be great to be prompted during the install to select a server/back end/proxy configuration or desktop? 

Also, I prefer to stick with a Ubuntu base for the server and Untangle is not from the best I can determine.

I guess I could try to roll my own distro, but my day job keeps me pretty busy.  I'm hoping there will be others that see the potential value to adding additional router functionality.

Cheers

---

### Post by jonathonblake on 2007-10-16
> **chris308 said:**
> that some of Untangle's additional features could be added or a script to easily install that functionality into UbuntuCE.  

Untangle has the following features:

# Web filter;
# Spam Blocker;
# Spyware Blocker;
# Virus Blocker;
# Phish Blocker;
# Intrusion Prevention;
# OpenVPN;
# Firewall;
# Router;

* Web filter:  Dansguardian
* Spam Blocker: email client dependent;
* Spyware Blocker: Dansguardian (?)
* Virus Blocker:  email client dependent;
* Phish Blocker:  email client dependent;
* Phish Blocker:  Web Browser  dependent;
* Intrusion Prevention: ?;
* OpenVPN: ?;
* Firewall: Firehol; (?)
* Router: ?;

I'd also add Tripwire to the list of programs to be installed by default. OTOH, that program should be installed, and run from somewhere unexpected/unobvious. 

Other than the router stuff, the tools are either email client or web browser dependent.

> Wouldn't it be great to be prompted during the install to select a server/back end/proxy configuration or desktop? 

For an experienced user, maybe. For a novice, it would be extremely confusing.   

>  I prefer to stick with a Ubuntu base for the server 

I was going to suggest Ubuntu Server Edition,but that is a LAMP solution. Information about configuring a router is at 
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router).

I thought that there was an Ubuntu Firewall/router edition/project,but I can't find info on it right now.  :(

xan

jonathon

---

### Post by tak1150 on 2007-10-17
[This thread]("http://ubuntuforums.org/showthread.php?t=553531") might be of interest...

If not, at least you got to see Bob the tomato!

---

