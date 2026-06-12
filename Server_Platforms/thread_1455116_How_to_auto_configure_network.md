---
title: "How to auto configure network"
date: 2010-04-15
forum: Server Platforms
---

### Post by cbecker78 on 2010-04-15
I have been trying for a while to install some form of linux (other than puppy) on my old laptop with little sucess.  I was finally able to get ubuntu server installed, however, I did not have internet acess when I did this, so the auto-dchp and internet was not setup.

So my question is, what do I run from the command line to activate the "configure network" process and configure "apt" to download Xorg and gnome?  right now, there is no etc/network/interfaces file...  and I'm not sure what to put in it for my Belkin Wireless card.

Thanks for any suggestions~

---

### Post by cdenley on 2010-04-15
Configuring a wireless card is not so simple as telling it to use DHCP, especially if there is encryption (which I hope there would be). I have no idea how to configure a wireless card for a server. I'm sure it could be done, but might be a little difficult. I would suggest you start with a desktop install for easier wireless configuration and gnome, then add whatever server components you want. You might want to use 9.10 because I'm not sure what wireless support was like for 8.04, or wait a couple weeks for 10.04.

---

### Post by cbecker78 on 2010-04-15
Hi, and thanks.  I would LOVE to start with a desktop install.  Unfortunately, I cannot get a desktop install to finish installation, nor to even load as a live CD.  I have tried every variant of Ubuntu and several other distros as well- puppy and dsl work fine, but I need gnome.

OK, so if I want to just forgo wireless for now, what do I need to do to set up internet on eth0?  Is it as simple as creating my ect/network/interfaces file and filling it out to auto dchp, or is there another step involved?  <- because I tried that, but it doesn't seem to work.

Below is the contents of the file I created:

```
auto eth0
iface eth0 inet dhcp
```

I'm guessing that I am missing a step?

---

### Post by cdenley on 2010-04-15
I believe that should work after a reboot or...
```

sudo /etc/init.d/networking restart

```

verify you used the correct network interface, and that it received an IP
```

ifconfig -a

```

then verify DHCP configured your DNS servers
```

cat /etc/resolv.conf

```

---

### Post by cbecker78 on 2010-04-17
Thanks!  Turns out I was leaving the first foward slash off of my command to edit/create the interfaces file, and doing cntrl Z to save like a moron.  But now that that is all sorted out, I have sucessfully connected to the internet.  Thanks for the help and the handy commands above!

(If anyone else comes to this post with similar issues, you will also need to manually edit /etc/apt/sources.list to add repositories to get the apt-get bit working right)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

