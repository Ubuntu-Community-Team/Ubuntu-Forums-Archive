---
title: "Ubuntu Server Automatic Updates - is it working?"
date: 2009-04-16
forum: Server Platforms
---

### Post by theRick on 2009-04-16
I'm setting up a webserver for the first time without a control panel and am using Ubuntu Server 8.10 on a VPS with linode.com

My website and database are working and that is great. I have a question about the Automatic Updates from the server quide.

[https://help.ubuntu.com/8.10/serverguide/C/automatic-updates.html](https://help.ubuntu.com/8.10/serverguide/C/automatic-updates.html)

> The unattended-upgrades package can be used to automatically install updated packages, and can be configured to update all packages or just install security updates. First, install the package by entering the following in a terminal: 

sudo apt-get install unattended-upgrades

I also did the next part of the guide...

>  Another useful package is apticron. apticron will configure a cron job to email an administrator information about any packages on the system that need updated as well as a summary of changes in each package.

To install the apticron package, in a terminal enter:

sudo apt-get install apticron


I am getting emails from the apticron package letting me know what packages need upgrading - but as far as I can tell unattended-upgrades isn't doing anything.

I have not received any email notifications from it and it doesn't look like any upgrades have happened.

Am I missing some step not outlined in the server guide? Or does it perhaps not run as frequently as I'm anticipating?

Any help will be appreciated.

---

### Post by theRick on 2009-04-21
5 day bump

---

### Post by Spikerok on 2009-04-21
unattended-upgrades  - should be installing updates which you want it to install.
for example if you want to install all updates in file "/etc/apt/apt.conf.d/50unattended-upgrades" change some lines..
[PHP]
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu intrepid-security";
        "Ubuntu intrepid-updates";
};
[/PHP]

if you want to automatically to install only updates then use next type of code
[PHP]
Unattended-Upgrade::Allowed-Origins {
//      "Ubuntu intrepid-security";
        "Ubuntu intrepid-updates";
};
[/PHP]

---

### Post by Spikerok on 2009-04-21
their might be a problem with updating configurations

---

### Post by mr_skater99 on 2009-07-04
I've just set this up - so i'll give it a few days and see how it goes.

How often does it check for updates?  Daily?  Is that bit configurable?

---

### Post by juancarlospaco on 2009-07-04
*By default are not automatic, istead are manual, you need to configure it.*

---

### Post by mr_skater99 on 2009-07-04
I un-commented both options in the config file - anything else i need to do?

---

### Post by snowman386 on 2009-07-29
according to the readme file, you have to add this to the 50unattended-upgrades file:

```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";
```

You would think that installing the package would configure this automatically. Why else would you install the unattended-upgrades package if you dont want unattended upgrades? Oh well, just my 2c

---

