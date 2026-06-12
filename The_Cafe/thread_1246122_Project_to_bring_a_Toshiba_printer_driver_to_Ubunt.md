---
title: "Project to bring a Toshiba printer driver to Ubuntu"
date: 2009-08-21
forum: The Cafe
---

### Post by Johnsie on 2009-08-21
I've registered a blueprint to get a driver for a Toshiba-Tec printer to Linux:

[https://blueprints.launchpad.net/ubuntu/+spec/toshiba-tecb-sx4-printer-support](https://blueprints.launchpad.net/ubuntu/+spec/toshiba-tecb-sx4-printer-support)


I've sent the following email to Toshiba-Tec to try and get help with this:

> 
Hi, 
    I'm working on an Ubuntu project to get the TOSHIBA TEC B-SX4  label printer working on Linux so that our users can use your printers. We would appreciate any driver specifications or source code your company can provide so that we can develop this.


More information is available at:
 [https://blueprints.launchpad.net/ubuntu/+spec/toshiba-tecb-sx4-printer-support](https://blueprints.launchpad.net/ubuntu/+spec/toshiba-tecb-sx4-printer-support)

There is also running a forum thread about this at:

Please get in contact to let us know what you can provide. We're looking forward to your response.

Thanks,

John McCourt




It'll be interesting to see what they can come up with...

---

### Post by 23meg on 2009-08-28
> **Johnsie said:**
> I've registered a blueprint to get a driver for a Toshiba-Tec printer to Linux:

[https://blueprints.launchpad.net/ubuntu/+spec/toshiba-tecb-sx4-printer-support](https://blueprints.launchpad.net/ubuntu/+spec/toshiba-tecb-sx4-printer-support)


I've sent the following email to Toshiba-Tec to try and get help with this:




It'll be interesting to see what they can come up with...

Why exactly have you registered a blueprint for this? [Blueprints]("https://help.launchpad.net/Blueprint") are for [feature specifications]("https://wiki.ubuntu.com/FeatureSpecifications") and coordinating them, and you don't have one. 

If you want to involve Toshiba, the place to do it is [upstream]("http://www.linuxfoundation.org/collaborate/workgroups/openprinting") (the [Linux Driver Project]("http://www.linuxdriverproject.org") may be suitable), not Ubuntu; Ubuntu does not develop device drivers , and you can't "add support for Ubuntu" without developing a Linux driver.

---

### Post by pkong on 2009-09-02
Hi,
I have developped a cups driver for tec printers under gnu/gpl licencing.
:D
It's not perfect but it works on any TPCL2 printer accepting compressed graphics.
You need to have 9.04 version

---

### Post by Johnsie on 2009-09-02
Thanks, I'll give that a shot.

---

### Post by pkong on 2009-09-11
> **Johnsie said:**
> Thanks, I'll give that a shot.
Did you have any problem to have the driver working?
:confused:

---

### Post by wally_west on 2010-05-06
Hi!

For those who are interested: I just found out, that Toshiba Tec driver development is outsourced to Seagull Scientific. Seagull Scientific is a subcompany of Microsoft (at least that's what the printer technician told me). So don't expect much help from their side. ;)

---

### Post by pkong on 2010-05-06
Hi,
As far as the driver is concerned, I have developped this cups driver from the sources available from [www.cups.org](www.cups.org).

What I need to know is the problems encountered if you want to have releases.

No feed back means everything is working fine.

As fas as seagullscientific is concerned, thats years that Toshiba has asked them to develop the driver and in the windows world they are one of the best available for free download from their site.

best regards
pkong:guitar:

---

### Post by samlown on 2010-05-17
Hi pkong,

Do you have the source code available for your rastertotec program?

I'll be testing a Toshiba TEC SX4 printer, initially with ZPL Emulation, but if that fails I would like to try your solution.

I don't think I'd be willing to put a program from an unknown source into production without the source code though.

Cheers,
sam

---

### Post by pkong on 2010-05-17
Hi sam,
I'm willing to give you the sources for free as it's under Gnu gpl
There's just one condition.
I don't want the source to be sent to my ancient associate who is the same business as me.
You must give me your private mail adress and agree to not send or make avaible the sources in any circunstances to the company  I'll give you the name :P
I am willing to give much but not to people who have once stolen my work.
My mail is :ske.kong@orange.fr

---

