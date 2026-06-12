---
title: "MiniDLNA with 18.04"
date: 2018-11-13
forum: Server Platforms
---

### Post by miheex on 2018-11-13
So I decided to try 18.04.1 since my latest broke down.
I installed it perfectly, but apparently decided to also install miniDLNA which can be selected with 18.04 installation. Now I have the problem, because I can not find any config files, nor directory where it should be installed. It also says MiniDLNA is not installed, but when i go to my IP:8200, it runs (MiniDLNA 1.2.1) - but no files, since i can't find config.
Then decided to install deb after all. I got the config and everything right, but didn't work since one instance of MiniDLNA is alredy running on that ip. So apparently I must find config for miniDLNA that came with 18.04 installation to work it out. Kinda lost here.
Any help, did I miss something here?

If it is in any help, how I see miniDLNA from other PCs (not in URL but explorer - name) is: *myservername*:root

---

### Post by SeijiSensei on 2018-11-13
The Ubuntu version of minidlna creates the configuration /etc/minidlna.conf.

I don't really understand your post.  You say you installed it once then installed it again from the .deb.  Where did the first instance come from?  If you run this
```

sudo updatedb
locate minidlnad

```
How many copies of minidlnad do you have?  The standard installation puts it in /usr/sbin/.

After editing minidlna.conf, try running "sudo systemctl restart minidlna".  If that fails try "sudo service minidlna restart".

---

### Post by miheex on 2018-11-13
Exactly, I know, but as I said: it seems that minidlna is installed (installation that goes with server install), but does not have /etc/minidlna.conf
Yes, I installed it with server, which is not by terminal but checked it within the installation (like DHC server, LAMP etc.). When I install from the .deb, I have conf. But it seems after that I have two minidlna which is weird, because .conf is for the .deb version that can not be run, because the one that came with installation is always running. Even after I purged minidlna .deb, one minidlna (the one that came with server installation) is still installed. And as before - no /etc/minidlna.conf.
Seems like it has this weird path: /snap/minidlna-escoand/19/sbin/minidlnad
And no operations are possibe with the one that came with installation because minidlna service is not found. So no restart, no force refresh, can't even purge it.

Tried:
```
sudo service minidlna stop
sudo rm -rf /var/cache/minidlna/*
sudo minidlnad -R -d
sudo service minidlna start
```

nothing.

I mean, it runs fine, the only problem is I can't configure it.

EDIT: found .conf in /snap/minidlna-escoand/19/etc/minidlna.conf (how the heck?), but can't edit it since it's read-only filesystem, apparently.
EDIT2: found another .conf in /var/snap/minidlna-escoand/19/minidlna.conf

---

### Post by ajgreeny on 2018-11-13
I suggest you remove the snap version of minidlna then reinstall, if necessary, the normal repository version; snap packages often seem to create more problems than they solve as far as I can make out, and in my Xubuntu 18.04 I have minidlna installed and working perfectly.

Do you run your installation as a server and not as a desktop?  
If so this thread will be better served if it is moved to the server section of the forum, but it is only really appropriate if this is a server and not a desktop machine that happens to run that minidlna server application so let us know and we can then move it if needed.

The commands you need to start and stop minidlna are ```
sudo systemctl start **(or stop)** minidlna.service
```

---

### Post by miheex on 2018-11-14
Uh, I didn't notice I'm on desktop forum. Yes it's a server I'm running, not desktop.

Can you help me with the command to remove snap version of minidlna? Because purge doesn't find the package.

Thanks

---

### Post by ajgreeny on 2018-11-14
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit as I spoke of in my last post #4.

To remove snap packages first check what is installed with command ```
snap list
``` then you can remove what you do not want with ```
snap remove snap-package-name
``` I am uncertain whether this needs to be run as administrator using sudo as I have not used any snap packages so try first without sudo; **snap list** does not need sudo.
See man snap for all details of using snap packages.

---

