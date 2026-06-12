---
title: "Ubuntu Server"
date: 2008-04-30
forum: Server Platforms
---

### Post by winsane on 2008-04-30
What is the best way to change the computer name on Ubuntu server? I have heard that the /etc/hosts and /etc/hostname must be changed at exactly the same time or sudo will break. This makes no sense to me. Can anyone verify this?

---

### Post by bluefrog on 2008-04-30
this is correct, you need to change /etc/hosts and /etc/hostname

---

### Post by hyper_ch on 2008-04-30
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3) : have a look at step 7.... change it manually in the host, do it for the hostname was written there.

---

### Post by Monicker on 2008-04-30
Yes, it will break.  For some reason sudo cares about the hostname of the computer.  I have never run into this problem using any other distro of linux.

You can change the settings by going to System -> Network.  Change the host name on the General tab, and at the Hosts tab change the entry for 127.0.1.1 to match the host name.

---

### Post by hyper_ch on 2008-04-30
> **Monicker said:**
> You can change the settings by going to System -> Network.

A server usually does not have that ;)

---

### Post by Monicker on 2008-04-30
> **hyper_ch said:**
> A server usually does not have that ;)

Perhaps, but I have seen several recommendations by other posters, who for some unknown reason, suggest installing a GUI environment on servers.  :(

---

### Post by hyper_ch on 2008-04-30
that is windows thinking... a server (usually) runs headless and no gui is required...

---

### Post by winsane on 2008-04-30
A do not like the idea of using a GUI on a production linux server either. I will if I must. However, I have to ask this question.  Why not just download /etc/hostname and /etc/hosts and change them offline? Then they could be brought back onto the server via wire or disk and overwrite the original by using a simple cp command?
Am I just dreaming here or would that work?

---

### Post by hyper_ch on 2008-05-01
changing on the fly does not matter I think... only when you reboot it does

---

### Post by winsane on 2008-07-31
Recently, I had to do this again.  This time I made changes to the firewall and set to a different static IP.  When I entered the new info using sudo, I got hanging, inabilty to nano etc/hosts file and general slowness when typing certain basic commands.  However, if I log straight in as root(gasp), it allowed me to edit my files with no problem.

---

### Post by jerome1232 on 2008-07-31
huh strange, I just changed my servers hostname by doing
```
sudo hostname newhostname
sudo vim /etc/hostname
sudo vim /etc/hosts
```

deleted the old name typed in the new one hit ZZ 

did a sudo reboot, and she chirped on happily, ssh'd in a few minutes later, sudo isn't broken and I haven't seen any performance issues. :) maybe I'm just lucky (this is on 8.04)

---

### Post by cariboo on 2008-08-01
There are times when you have to log in a root to accomplish some task that can't be done any other way. It is just on this board that we tell the newbies that there is no other way but sudo. :)

Jim

---

### Post by windependence on 2008-08-01
This is not normal and has nothing to do with changing it on the fly, that is perfectly OK.

After you edit your hostname file, just do a 

```
sudo hostname <newhostname>
```

and it will be changed in real time, no boot necessary.

Please note, you can always change the hostname with the 'hostname' command, but it will not survive a reboot unless you edit /etc/hostname.

-Tim

---

### Post by gtdaqua on 2008-08-01
> **windependence said:**
> This is not normal and has nothing to do with changing it on the fly, that is perfectly OK.

After you edit your hostname file, just do a 

```
sudo hostname <newhostname>
```

and it will be changed in real time, no boot necessary.

Please note, you can always change the hostname with the 'hostname' command, but it will not survive a reboot unless you edit /etc/hostname.

-Tim

The proper way to set hostnames is:

```

sudo echo milky.com > /etc/hostname

```

and edit the /etc/hosts to modify:
```

10.1.1.113  milky.com milky

```

(where 10.1.1.113 is the ip of the server)
and RESTART. Always restart after changing hostnames.

Then the commands:

```

hostname
hostname -f

```

should both return the same value which is "milky.com"

---

### Post by windependence on 2008-08-01
Agreed gtd. :) This is certainly the preferred way.

-Tim

---

