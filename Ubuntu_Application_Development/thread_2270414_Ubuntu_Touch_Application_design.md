---
title: "Ubuntu Touch Application design"
date: 2015-03-22
forum: Ubuntu Application Development
---

### Post by schankame on 2015-03-22
I am a student and for a final project I am trying to create an application for my Ubuntu tablet running 15.04. I am trying to create a simple application to start with but two things keep happening. One my emulator keeps locking up and my entire machine locks up. The other I keep getting these errors: 


[LIST]
[*][COLOR=#000000][FONT=Arial]warning: desktop_Exec (app-test): found unexpected Exec with architecture 'all': ./qtc_device_debughelper.py[/FONT][/COLOR]
[/LIST]

[LIST]
[*][COLOR=#000000][FONT=Arial]warning: security_policy_groups_safe_app-test (debug): (REJECT) reserved policy group 'debug': not for production use [/FONT][/COLOR]
[/LIST]
[COLOR=#000000][FONT=Arial]            The debug policy group is automatically injected and should only be used for development. [/FONT][/COLOR][COLOR=#000000][FONT=Arial]To create a package for the store use the publish tab![/FONT][/COLOR]

[LIST]
[*][COLOR=#000000][FONT=Arial]error: security_policy_groups_webapp (app-test.apparmor): found unusual policy groups: debug[/FONT][/COLOR]
[/LIST]
[COLOR=#000000][FONT=Arial]

[/FONT][/COLOR]I also included the show output file. Does anyone have any suggestions or can pint me in the right direction?

Thank you!!

---

### Post by bittner on 2015-08-08
> **schankame said:**
> I am a student and for a final project I am trying to create an application for my Ubuntu tablet running 15.04. I am trying to create a simple application to start with but two things keep happening. One my emulator keeps locking up and my entire machine locks up.

I can confirm I have the same or a very similar problem. The Desktop version of my webapp runs fine in the Ubuntu SDK (Qt Creator), but when I try to upload the webapp to my phone for running it, first the Qt Creator locks up, then soon after the whole notebook blocks itself. I thought this may just be because I'm using an elderly [HP Compaq 6735s](http://www.hp.com/hpinfo/newsroom/press_kits/2008/connecting/ds_bn_6735s.pdf) notebook with 2 GB RAM, but who knows.

> **schankame said:**
> The other I keep getting these errors: 

[LIST]
[*][COLOR=#000000][FONT=Arial]warning: desktop_Exec (app-test): found unexpected Exec with architecture 'all': ./qtc_device_debughelper.py[/FONT][/COLOR]
[/LIST]

[LIST]
[*][COLOR=#000000][FONT=Arial]warning: security_policy_groups_safe_app-test (debug): (REJECT) reserved policy group 'debug': not for production use [/FONT][/COLOR]
[/LIST]
[COLOR=#000000][FONT=Arial]            The debug policy group is automatically injected and should only be used for development. [/FONT][/COLOR][COLOR=#000000][FONT=Arial]To create a package for the store use the publish tab![/FONT][/COLOR]

[LIST]
[*][COLOR=#000000][FONT=Arial]error: security_policy_groups_webapp (app-test.apparmor): found unusual policy groups: debug[/FONT][/COLOR]
[/LIST]
[COLOR=#000000][FONT=Arial]


I made the *security_policy_groups_** warnings go away as follows below. The problem is in the *.click* package, which is (I believe) generated in the course of walking through the Create Project wizzard.

[LIST=1]
[*]In the Ubuntu SDK (Qt Creator) open your project.
[*]Visit your project's *.apparmor* file and make sure *debug* is not listed in the "Security Policy Groups", save the file.
[*]In the menu bar choose  *Build* -> *Ubuntu* -> *Create Click package*.
[/LIST]

Afterwards, all build errors vanished.

However, I noticed the menu bar is not always there in the Ubuntu SDK, this may be a bug of the IDE, I don't know.

---

