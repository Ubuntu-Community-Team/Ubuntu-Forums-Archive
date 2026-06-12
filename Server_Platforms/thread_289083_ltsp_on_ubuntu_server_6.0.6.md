---
title: "ltsp on ubuntu server 6.0.6"
date: 2006-10-30
forum: Server Platforms
---

### Post by hortimech on 2006-10-30
I have got this running on my server and got a client to boot to the grey 
screen with the cross, I have extensively googled and all I can find is one 
posting saying that I do not need to be running X on the 
server and that I need to install x-this and x-that and a desktop and 
manager.
can anyone tell me where to find anymore info on installing all the X 
components without installing X on my server?

I have also tried posting this to ltsp-discuss mailing list but because my ISP does not have a postmaster address they are refusing my emails:confused:

---

### Post by Aearenda on 2006-10-30
This sounds like a name-resolution problem on the server - it has to be able to connect outwards to the 'terminal' for you to see anything more on the screen. The LTSP installation should have set up your /etc/hosts file on the server to include all the workstation names and their addresses - check this, see if you can ping the client from your server by name.

Presumably you've seen [www.ltsp.org;](www.ltsp.org;) also look at [www.k12ltsp.org](www.k12ltsp.org), the latter if focused on Fedora but still useful.

---

### Post by hortimech on 2006-10-31
I think you misunderstood me, I do not run X on my server and I do not want to. I just want to run an X desktop, preferably KDE on the LTSP clients, so what do I load and where?

---

### Post by Aearenda on 2006-10-31
Oh I see - in that case I can't offer definite advice, not having done that. I *think* your best route would be to install kubuntu-desktop (this metapackage will install the standard kubuntu kde environment including kdm) as if you were going to use it on the server, and prove it works on the terminals too, and then look at preventing kdm from starting on the server's screen. I don't think you'll release much memory by not running X on the server, since it all has to be running for the clients anyway. I've never tried to use kdm as a login manager with LTSP, only gdm. I suspect Skolelinux uses KDE on Debian - maybe you could see what they do. Sorry I can't help further.

---

### Post by fnjordy on 2006-10-31
You have to install X because all the desktop packages depend on it, but you do not have to run it, you will have to run a display manager like GDM, XDM, etc and some have an option to not start a local console (X11 server).  See the --no-console option for GDM for an example.

So basically install kubuntu-desktop meta-package, check that everything works, then disable the local console.

I do this when testing LTSP in VMware Server, it makes the desktop a little faster.

---

### Post by hortimech on 2006-11-01
Thanks for that, installed KDE (after long download) everythings working now, but how do I turn kde off on my server? I ran ltspcfg and answered yes to the question about do want to turn off the desktop on the server but kde still loads, or in other words how do I get back to text logins on the server?

---

### Post by fnjordy on 2006-11-02
According to [an article on userful]("http://userful.com/products/dm-config"):

#  Disable/remove current local server(s) by prepending # to Xservers

#:0 local /usr/X11R6/bin/X 

The Xservers file is the configuration files for KDM. The common locations for the Xservers file are /etc/X11/xdm/, /etc/kde3/kdm/, /usr/share/config/kdm/ or /etc/opt/kde3/share/config/kdm/, but this is different for each Linux distribution.

---

### Post by hortimech on 2006-11-02
I tried to find Xservers, only one was in my ltsp chroot, so left this alone.
Googled, found something that said change run level to 2, this did not work either.
Googled more, found that if you changed /etc/rc*.d/S99kdm (where * = 1 to 5) to not.S99kdm, KDE does not start and you are back to the text login.
Great, I thought, booted a terminal and I was back to the grey screen with the X cursor, restarted KDE on the server(/etc/init.d/kdm start) and the terminal changed to the kubuntu splash screen and I can login.
Does anybody know a way of not running KDE on the server and having X on the terminals? or am I stuck with kde running on my server?

---

### Post by fnjordy on 2006-11-02
> **hortimech said:**
> I tried to find Xservers, only one was in my ltsp chroot, so left this alone.
Googled more, found that if you changed /etc/rc*.d/S99kdm (where * = 1 to 5) to not.S99kdm, KDE does not start and you are back to the text login.

KDM has to still run, disabling it means remote clients cannot login.  Xservers should be in host not the chroot.  I'll have a look at Kubuntu Dapper.

---

### Post by fnjordy on 2006-11-03
Ok, I installed Kubuntu to test, simply edit /etc/kde3/kdm/kdrmrc and remove the static server:

#StaticServers=:0
StaticServers=

---

