---
title: "VMware WS 9 on Ubuntu 12.10 Desktop x64 - Breaks LightDM?"
date: 2012-11-04
forum: Virtualisation
---

### Post by oxseyn on 2012-11-04
Help!

I'm having the following problem.  On a fresh installation of Windows 12.10 Desktop x64, fully updated, I've installed VMware Workstation 9.  I try to run it - it tells me I need some specific linux headers.  I install those headers via apt.

I reboot - and LightDM is broken.  I can see my mouse (x is partially working?) but I see a console with the following messages:

Virtual ethernet done
VMware Authentication Daemon done
Shared Memory Available done
speech-dispatcher disabled: edit /etc/default/speech-dispatcher
saned disabled; edit /etc/default/saned

Starting Workstation Server: done
* Checking batter state... [ OK ]

And at this point it hangs.  If I switch to tty1 I can login on the console, but if I try to 'startx' it fails:

Fatal server error:
no screens found

The first time this happened, I mucked around for a bit, finally gave up and reinstalled the entire OS and then vmware again.  In both cases, same exact problem.  Any ideas?

---

### Post by oxseyn on 2012-11-04
So I installed GDM using apt and selected it as the default.  It then immediately kicked me into lightDM and I was able to login (lol).  I rebooted and GDM came up this time and I'm now able to login.  I'd much prefer to use lightDM though.

---

### Post by cybergalvez on 2012-11-04
> **oxseyn said:**
> So I installed GDM using apt and selected it as the default.  It then immediately kicked me into lightDM and I was able to login (lol).  I rebooted and GDM came up this time and I'm now able to login.  I'd much prefer to use lightDM though.


have you tried to reinstall lightDM? just wondering if VMWare messed with some of the lightDM libraries.

---

### Post by Cheesemill on 2012-11-06
12.10 isn't a supported host OS for VMware Workstation 9.0.

Either use 12.04 or wait until VMware have had time to add support for 12.10.

---

### Post by dcstar on 2012-11-11
> **Cheesemill said:**
> 12.10 isn't a supported host OS for VMware Workstation 9.0.

Either use 12.04 or wait until VMware have had time to add support for 12.10.

VMware Player/Workstation was just officially updated for 12.10 support a couple of days ago.

Upgrade your existing installation or download and use the new version.

---

### Post by LinuxMan92 on 2012-11-21
I just gave up trying to install it in Workstation 9. Everything would install but the GUI wouldn't load right. Just updated it today and it looks like its fixed.

VMware needs to be prepared ahead of time for these updates especially with how much money they charge for Workstation these days.

---

### Post by dcstar on 2012-11-22
> **LinuxMan92 said:**
> 
.........
VMware needs to be prepared ahead of time for these updates especially with how much money they charge for Workstation these days.

VMware is a commercial company and the Linux user base is small, and no serious Linux users immediately use the latest and greatest flavour of a particular distro.

VMware get around to making their products compatible for Linux in direct relation to the importance of it to their company.

---

### Post by shhammer5634 on 2013-02-06
> **oxseyn said:**
> Help!
 
I'm having the following problem. On a fresh installation of Windows 12.10 Desktop x64, fully updated, I've installed VMware Workstation 9. I try to run it - it tells me I need some specific linux headers. I install those headers via apt.
 
I reboot - and LightDM is broken. I can see my mouse (x is partially working?) but I see a console with the following messages:
 
Virtual ethernet done
VMware Authentication Daemon done
Shared Memory Available done
speech-dispatcher disabled: edit /etc/default/speech-dispatcher
saned disabled; edit /etc/default/saned
 
Starting Workstation Server: done
* Checking batter state... [ OK ]
 
And at this point it hangs. If I switch to tty1 I can login on the console, but if I try to 'startx' it fails:
 
Fatal server error:
no screens found
 
The first time this happened, I mucked around for a bit, finally gave up and reinstalled the entire OS and then vmware again. In both cases, same exact problem. Any ideas?
 
I had a similar issue this week installing VMWare WS 9 on Ubuntu 12.04.  On a fresh install, installed VMWare, rebooted, and either X didn't start at all or X would start but LightDM wouldn't.  If I reinstalled LightDM and then rebooted, everything would work fine once.  Then when I rebooted the whole thing started over again.  On a hunch, I went into rc2.d and deleted the 3 SXX links to the vmware startups in init.d.  Reinstalled LightDM again, rebooted.  And it worked.  Rebooted again, and it worked.  Rebooted several times, worked every time.  On a couple of the reboots, manually started the vmware processes, in the order they should have been after LightDM had started up and I was logged in.  Rebooted, and everything was fine.
 
So it appears something that VMWare is running when it starts up it's processes in rc2.d is interfering with X/LightDM.  I'm currently looking for a way to start the vmware processes after LightDM is up and stable.  If I find a goot place to do that, I'll post back here.  Hope to resolve this soon.  Need the whole setup for work.

---

