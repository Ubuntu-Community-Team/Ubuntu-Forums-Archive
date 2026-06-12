---
title: "MOTD issues + reported package update - issues?"
date: 2014-09-22
forum: Server Platforms
---

### Post by Coder68 on 2014-09-22
I am accessing a new build of Ubuntu 64bit LTS 14.04.1 via VMWares web interface which connects on the back end using port 9443.  

Two issues.

1. MOTD.tail is not showing. I have seen some SSH issues related to this, but I am not sure if this is SSH. I do not have a way of capturing packets on these servers, so it might be using SSH. VMWare site no help, but I am guessing it is SSH.

2. The stock MOTD shows that there are 7 packages that can be updated and there are 7 security updates. Running a manual update shows no updates (3 not upgraded). I do not want to get off the LTS version.
I rebooted but that did not help - it still shows there are updates. 

So, what gives?

I have installed the following software with these commands:


[LIST=1]
[*]Sudo apt-get install openssh-server 
[*]Sudo apt-get install apache2 
[*]Sudo apt-get install php5 libapache2-mod-php5 
[/LIST]

I then ran all of the updates until it said there were none. 

Thank you,

C68

---

### Post by tgalati4 on 2014-09-22
*motd* used to be a simple message.  Now it is a complicated banner that is assembled from piece parts.  Sometimes those parts get broken.

```
man update-motd
```

There are a few bug reports filed against *motd*.  Certain Use Cases can cause issues with repeating messages or out-of-date messages which can cause confusion.

*motd* is just a suggestion.

Try logging into the server directly--dig out a monitor and keyboard--and see if *motd* reflects reality.

---

### Post by Coder68 on 2014-09-22
I knew about the SSH issue, but I did not realize that updates were also an issue.

Thank you.

---

### Post by tgalati4 on 2014-09-22
I think once you log in locally and verify that *motd* is correct, then it should remain correct until the next time you perform a remote operation which does not correctly update motd.  I'm sure there is a reason why this is not fixed.  I do not know this reason.

I would add your own customization to motd (following the documentation carefully) as a work-around.  For instance, I have one of my servers ping other devices during login to make sure they are up before I try to push data to them.  If they are down, then I have to troubleshoot.  Normally, this is not an issue--unless it becomes an issue.  Same with updates.

Add your custom scripts to /etc/update-motd.d and behold the power of open source.

When I encounter these problems in linux:

> 1.  Light Candle
or
2.  Curse Darkness

Note that the above are mutually exclusive--or should be.

---

### Post by Coder68 on 2014-09-22
I can't log in locally... it is a VM on ESX.

---

### Post by tgalati4 on 2014-09-22
I remember the reason why this is not fixed:  [http://ubuntuforums.org/showthread.php?t=2230444&highlight=motd](http://ubuntuforums.org/showthread.php?t=2230444&highlight=motd)

There are some Uses Cases where updating motd during ssh can cause you to be locked out of your system--checking updates can take some time.  So a switch was added to ssh logins to turn on/off motd updates during ssh sessions.  If you do get locked out of your server after changing this behavior, then you will know why it was changed.

A Haiku:

Bad remote motd?
Could be updates are turned off.
Change at your own risk.

---

### Post by Coder68 on 2014-09-22
The MOTD is not that big of deal. It was just a message to not do a distro upgrade, unless it was to the next LTS.

Thanks!

---

