---
title: "Download Rate Limit broken"
date: 2010-05-07
forum: Ubuntu One (CLOSED)
---

### Post by louis_mallow on 2010-05-07
I found U1 was hogging lots of my bandwidth, so tried the 'Limit Bandwidth Usage' option. The panel remembers I want to limit upload speed (which I s'pose is all that matters), but download speed returns to 2048 KB/s as soon as I close the panel.  Any ideas?

---

### Post by duanedesign on 2010-05-08
Are you using ubuntuone-client 1.0.3 ? You can check with the command:
```
dpkg -l ubuntuone-client
```

There is a bug for this. [See bug 509740]("https://bugs.edge.launchpad.net/ubuntuone-client/+bug/509740")

WORK AROUND

1. Quit the Ubuntu One client
2. Delete the file: ~/.config/ubuntuone/syncdaemon.conf
    (If using Nautilus, make sure you do a Ctrl-H to view hidden files when in your home directory)
3. Start the Ubuntu One client

You can try resetting the bandwidth usage preferences but if you continue to run into problems, follow the steps above and don't turn the limit bandwidth usage on for the time being.

This has been fixed in Lucid so you might consider upgrading. Also you could upgrade to the Beta/PPA which is a newer version of ubuntu one. NOTE: The newer version of ubuntu one does not have the applet. It was replaced by Ubuntu One Preferences. In Lucid you can access this through the Me Menu. In Karmic you must access this by going to System > Preferences > Ubuntu One. If you wish to run the Beta/PPA in Karmic here is the command.

```
sudo add-apt-repository ppa:ubuntuone/beta && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by louis_mallow on 2010-05-08
> **duanedesign said:**
> 
This has been fixed in Lucid so you might consider upgrading. 

I'm on a clean-install of Lucid 10.04 LTS 

Will try the workarounds, though. Thanks.

---

### Post by joshuahoover on 2010-05-11
> **louis_mallow said:**
> I found U1 was hogging lots of my bandwidth, so tried the 'Limit Bandwidth Usage' option. The panel remembers I want to limit upload speed (which I s'pose is all that matters), but download speed returns to 2048 KB/s as soon as I close the panel.  Any ideas?

I think you're affected by the following bug: [http://launchpad.net/bugs/567562](http://launchpad.net/bugs/567562) 

I'm going to follow up on this bug and make sure we get a fix in.

Thank you,

Joshua

---

