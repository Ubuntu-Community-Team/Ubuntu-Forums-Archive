---
title: "how to setup automatic updates using webmin"
date: 2008-08-01
forum: Server Platforms
---

### Post by kustomjs on 2008-08-01
Hi Guys
I would like to know how to setup automatic updates with webmin?

---

### Post by pytheas22 on 2008-08-01
Write a cronjob that runs this command:
```

apt-get upgrade
```

and the updates will be applied whenever the cronjob is run.

---

### Post by Mumbly on 2008-08-02
If you want, append pytheas22's command with a -y to automatically agree, and start the update. Be warned, if your sources.list file is set to many different repositories, then you may upgrade your entire system and break things. My suggestion would be to only do this for security upgrades.

---

### Post by pytheas22 on 2008-08-02
> If you want, append pytheas22's command with a -y to automatically agree

Good point...forgot about that.

---

### Post by kustomjs on 2008-08-02
when I go under Cluster Cron Jobs and type in sh apt-get update I get this error:
Running sh apt-get upgrade on selected servers ..

Output from this server ..

      sh: Can't open apt-get

---

### Post by pytheas22 on 2008-08-02
I think that's because webmin always wants to use bash (sh) to run cronjobs.  Maybe it's possible to tell it not to use bash but just to run apt-get itself as an executable binary.  Otherwise, a work-around would be to do this:

1. create a script somewhere on the system, like /root, called "system-update.sh," and tell it to call apt-get:
```

sudo -s
cd /root
echo 'apt-get -y upgrade' > system-update.sh
chmod +x system-update.sh
```

2. now write a cronjob that says:
```

sh /root/system-update.sh
```

This should work.

---

### Post by MtTime on 2009-02-21
Hello,
I'm a newbie to both Ubuntu and Webmin.  I have setup an Ubuntu server and would like to update/upgrade via Webmin.

When I setup the cron job as below, under the username <my name> rather than, say root, the cron job prompts me for my password three times and then the job fails.

I've looked around for how to pass or embed (probably a bad idea) my password into the cron job, but haven't found a viable solution.  

Any idea how to pass your user password in a cron job?

Thank you!

---

### Post by pytheas22 on 2009-02-21
MtTime: normal users can't upgrade the system.  Is there a reason you can't just specify 'root' as the user for the cron job in question?

When it asks you for your password, it's so that it can run the upgrade command as root--so essentially, the cron job will be run as root either way.  The simplest solution in this situation would just be to specify the user as root to begin with.  Any other method that I can think of would involve putting your password in a plaintext file, which is definitely not a good idea.

Also, if you have Gnome installed on the system, you can set it to auto-update itself by going to System>Administration>Software Sources and looking for the box about auto-updating under the 'Updates' tab.  I realize you probably don't have Gnome on the system, but I thought I'd mention this anyway.

---

### Post by MtTime on 2009-02-24
Thanks pytheas22!  I actually do have GNOME installed because I'm not proficient at the command line yet.
The option to auto-update is a good solution, thank you... but I would still like to be able to make it work from webmin because that is the kinda guy I am.

I have ran the webmin cron job as root, but it fails.  Could the text of the cron job be the problem:

system-update.sh:
sudo -s
cd /root
echo 'apt-get -y upgrade'> system-update.sh
chmod +x system-update.sh

In webmin, I then point the cron job at 'sh /root/system-update.sh' and when I run as <username> it asks for a password (which I can't enter from a cron job) and if I run as root it fails with an error:

/root/system-update.sh: 3: Syntax error: Unterminated quoted string.

This newbies' head hurts.  Can you help? ;-)

Thanks!

---

### Post by pdtpatrick on 2009-02-24
i dont think he meant for you to put all that code into the script. 

sudo -s --> this makes you root user
cd /root --> this changes you to the root directory
echo 'apt-get -y upgrade'> system-update.sh --> this puts: apt-get -y upgrade to the script named system-update.sh
chmod +x system-update.sh --> this makes the script executable


I would recommend putting this in the script instead:

> apt-get update; apt-get -y upgrade

only that line should be in the script.

---

### Post by pytheas22 on 2009-02-24
pdtpatrick got it.  Please modify the script so that it contains only:
```

#!/bin/bash

apt-get update; apt-get -y upgrade
```

---

### Post by freerkkalsbeek on 2009-02-24
To make the cronjob run once a day as user root, put it in /etc/cron.daily/update.sh

But be warned. Auto updating can harm your system without you knowing that something was updated at all. To be more safe, disable all repo's except the security repo's. 

Freerk

---

