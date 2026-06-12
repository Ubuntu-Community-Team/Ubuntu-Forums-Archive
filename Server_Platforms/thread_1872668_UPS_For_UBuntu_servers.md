---
title: "UPS For UBuntu servers"
date: 2011-10-31
forum: Server Platforms
---

### Post by sramm9 on 2011-10-31
Hai

Hope someone could help. I am using GE UPS, was hoping to have Auto/Reboot shutdown off all servers running Ubuntu but GE technical people says their Software does not support Autoshutdown/reboot for UBuntu.

Is there any alternatives i could use? other type of UPS in the market? 

Thanks a lot , much appreciated

---

### Post by trundlenut on 2011-10-31
I have an APC UPS on one of my Ubuntu servers with APCUPSD running on the server.  Pretty easy to set up and it turns off the server OK and notifies me by email when the power goes down.

---

### Post by 2WheelPenguin on 2011-10-31
APC will work, CyberPower has a Debian software package for their UPSs that works well with Ubuntu also.

---

### Post by Jonathan L on 2011-10-31
> **trundlenut said:**
> I have an APC UPS on one of my Ubuntu servers with APCUPSD running on the server.  Pretty easy to set up and it turns off the server OK and notifies me by email when the power goes down.

Hi

Before you spend your money, note that the APCUPSD people have a warning on their web site [http://www.apcupsd.org/](http://www.apcupsd.org/) that some more modern APC UPSs have a different protocol which isn't so good.

I write as someone whose already spent my (client's) money on an APC model which I don't know whether it works yet or not.   Caveat emptor as ever.

There is also [http://www.networkupstools.org/](http://www.networkupstools.org/)

 I'll update here with news in a few days with my model and details after I've had a chance to configure the software.

Kind regards,
Jonathan.

---

### Post by trundlenut on 2011-10-31
> **Jonathan L said:**
> Hi

Before you spend your money, note that the APCUPSD people have a warning on their web site [http://www.apcupsd.org/](http://www.apcupsd.org/) that some more modern APC UPSs have a different protocol which isn't so good.

I write as someone whose already spent my (client's) money on an APC model which I don't know whether it works yet or not.   Caveat emptor as ever.

There is also [http://www.networkupstools.org/](http://www.networkupstools.org/)

 I'll update here with news in a few days with my model and details after I've had a chance to configure the software.

Kind regards,
Jonathan.

I've had my UPS for about a year.  Bit of a pain that APC seem to be messing people about, one of the attractions of buying mine in the first place was that it would work pretty much out of the box with Ubuntu.  Next time APC send me an email trying to get me to buy another one I will complain.

---

### Post by Jonathan L on 2011-11-03
> **Jonathan L said:**
> I'll update here with news in a few days with my model and details after I've had a chance to configure the software.

Hi All

**_Re UPS Information_**

Information about Ubuntu and lots of UPSs is at the Network UPS Tools page.  In particular the hardware compatibility list: [http://www.networkupstools.org/stable-hcl.html](http://www.networkupstools.org/stable-hcl.html)

For [COLOR=Red]sramm9[/COLOR]: it appears to support at least the "EP Series" of GE UPS: perhaps yours is one of the supported models.

For APC UPS on various platforms, see [http://www.apcupsd.org/](http://www.apcupsd.org/)
But also [http://www.networkupstools.org/docs/man/apcsmart.html](http://www.networkupstools.org/docs/man/apcsmart.html)

[B][U]Re APC UPS:
[/U][/B] 
As well as apcupsd, the network ups tools seem extremely helpful.  In particular this page
[http://www.networkupstools.org/docs/man/apcsmart.html](http://www.networkupstools.org/docs/man/apcsmart.html), which explains:[INDENT]"microlink" models WARNING: these are not *natively* supported by apcsmart (or apcupsd for that     matter, if you&#8217;re wondering). Around 2007 APC (now APC Schneider) decided to     go back to its proprietry roots and all the new models (SMT, SMX, SURTD) use     completely different protocol and cables. If you purchased a new APC ups,     that uses cable with rj45 on the one end, and db-9 on the other - then you     have such model. Your only option to support it through NUT is to     purchase "legacy communications card" [...]
[/INDENT]**_Re My UPS:_**

Seems I was lucky!  My UPS is an (European) SUA1500RMI2U, and it appears to speak the "smart" protocol perfectly.  It is a 2-U rackmount model with a 9-pin female D-type for the serial and a USB socket (untested).  The RS-232 port is non-standard and requires a special cable.  Mine was supplied with a cable marked 940-0024E, which appears to be a normal 9-pin serial cable, male at one end, female at the other, but is wired (M1-F3, M2-F2, M9-F5, F1-F4, F7-F8, apparently identical to 940-0024C).

Following the very helpful protocol notes at [http://www.networkupstools.org/ups-protocols/apcsmart.html](http://www.networkupstools.org/ups-protocols/apcsmart.html) I manually found the following information.  (If you don't read the notes carefully, you'll miss the fact that you have to send 'Y' before it will speak to you!)[INDENT] Model string: "Smart-UPS 1500 RM"
Protocol version: 3
Firmware revision 667.18.I
Manufacturing date: "09/10/10"
[/INDENT]**_APC Partial Linux Support_**
APC supply software called PowerChute.  My UPS came with some software for "Powerchute Business Edition Agent" for Linux, as an RPM (which I understand is is installable on Ubuntu).  It says that[INDENT]NOTE: Your Linux download only includes the Agent component of the three PowerChute Business Edition software components. The other two components only run on Windows; all three are described below.
[/INDENT]I've no idea whether you can use this agent on its own, but it appears to communicate with the other parts over both TCP and UDP, so might be plausible to take a look at.



Hope that helps someone.

Kind regards,
Jonathan.

---

