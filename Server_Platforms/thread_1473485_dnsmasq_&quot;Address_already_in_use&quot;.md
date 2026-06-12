---
title: "dnsmasq &quot;Address already in use&quot;"
date: 2010-05-05
forum: Server Platforms
---

### Post by cong06 on 2010-05-05
I have a squid and apt-cacher running on a transparent server, and I'm trying to set up net booting.

I'm following the guide: [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

Unfortunately, when I tried to start dnsmasq, I got the error:
```

dnsmasq: failed to create listening socket: Address already in use

```

Following internet advice, I tried:
```

root@kimende-s:~# netstat -anlp | grep -w LISTEN
```
and found that dnsmasq was listed even though it was throwing this error.

So I decided to purge it.

After purging (and then restarting, to try and clear any problems) I noticed that it was still listed:
```

root@kimende-s:~# netstat -anlp | grep -w LISTEN
tcp        0      0 0.0.0.0:3142            0.0.0.0:*               LISTEN      2388/perl
tcp        0      0 10.42.43.1:53           0.0.0.0:*               LISTEN      4489/dnsmasq
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2375/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2723/cupsd
tcp        0      0 0.0.0.0:3128            0.0.0.0:*               LISTEN      2655/(squid)
tcp6       0      0 :::22                   :::*                    LISTEN      2375/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      2723/cupsd

```

Does anyone know why it's still listed even though it's uninstalled?
Last time I was having problems with named...

This is a brand new install... only changes were those mentioned: installing squid and apt-cacher.

Note: I'm using Network Manager as my router. I think this comes with named? I'm not sure...

---

### Post by cdenley on 2010-05-05
Someone or something probably started it without using the init scripts.
```

sudo ps -f -p 4489
sudo kill 4489

```

---

### Post by cong06 on 2010-05-05
ok. So as soon as I killed it, the eth0 connection died.

It seems Network Manager running a "dnsmasq" program (even though dnsmasq isn't installed) on port 53 for my "shared to other computer" eth0 connection.

Is there any easy way to use NetworkManager along with a netbooting server?


I'd rather not drop NetworkManager as it's handling my ppp connections...

---

### Post by cdenley on 2010-05-05
/usr/sbin/dnsmasq is provided by dnsmasq-base which is a dependency of network-manager.

---

### Post by cong06 on 2010-05-05
huh. so it seems that I don't need dnsmasq, just dnsmasq-base

However, the configuration isn't provided with dnsmasq-base, so I installed dnsmasq, just for the config to finish the walkthrough.

That's rather messy...

Edit:
I just noticed that when I turn on my computer, with dnsmasq installed, dnsmasq successfully starts, so when network manager wants to run it's own version, it fails.
To fix this, I ran:
```

chmod -x /etc/init.d/dnsmasq

```
Now dnsmasq will only start with network manager and will still use the config.

It's possible that uninstalling the package will work (but not purging) but I'll stick to this.

---

### Post by Truthiswithin on 2011-07-22
Great to find this thread!  I uninstalled dnsmasq and sure enough, the /etc/dnsmasq.d directory disappears.  But, there is still the /etc/dnsmasq.conf which is enough.

---

### Post by mpd2 on 2012-06-07
I got around this by replacing dnsmasq-base with dnsmasq.  Because of dependencies on it, I did the following:
[LIST=1]
[*]sudo apt-get remove dnsmasq-base (this removes network manager...)
[*]sudo apt-get install dnsmasq
[*]sudo apt-get install network-manager network-manager-gnome
[/LIST]

---

### Post by cong06 on 2012-06-07
> **mpd2 said:**
> I got around this by replacing dnsmasq-base with dnsmasq.  Because of dependencies on it, I did the following:
[LIST=1]
[*]sudo apt-get remove dnsmasq-base (this removes network manager...)
[*]sudo apt-get install dnsmasq
[*]sudo apt-get install network-manager network-manager-gnome
[/LIST]

One liner:
```

sudo aptitude install dnsmasq dnsmasq-base-

```

It should take less time this way, and be less likely to remove files you want. You'll need to `sudo apt-get install aptitude` though.

The minus at the end of dnsmasq-base tells it to remove, instead of installing. this is the same:
```

sudo aptitude remove dnsmasq+ dnsmasq-base

```

---

### Post by mpd2 on 2012-06-07
Thanks for pointing that out, cong06.

---

### Post by sffvba[e0rt on 2012-06-07
*Old thread **closed**.*


404

---

