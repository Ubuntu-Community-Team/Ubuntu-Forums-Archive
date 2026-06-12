---
title: "AIM or MSN"
date: 2009-01-22
forum: Server Platforms
---

### Post by jairom70 on 2009-01-22
can i use AIm or MSN or Xfire on Ubuntu server edition 8.10? preferably Xfire? if so how could i install it.

---

### Post by aaron.d on 2009-01-22
I don't know squat about xfire, but I use finch (text based client using libpurple engine from pidgin) to access msn, and aim.

---

### Post by aaron.d on 2009-01-22
this is, of course, in 8.04 server, with no X server. It is super useful since I use IM at work, I run finch in a screen that I can connect to from anywhere via ssh. that way logs etc stay in one place, and im always logged in to receive msgs.

---

### Post by jairom70 on 2009-01-23
is there a guide on installing this? what are the steps i need to follow?

---

### Post by Ein2015 on 2009-01-24
> **jairom70 said:**
> is there a guide on installing this? what are the steps i need to follow?

None that I can find... basically "sudo apt-get install finch" should work.  I've used it before and it's really straight-forward.

I think gfire is xfire for Linux... [http://gfire.site40.net/](http://gfire.site40.net/)

---

### Post by aaron.d on 2009-01-24
yeah

```
sudo apt-get install finch

```

and i think you need dbus too:

```
sudo apt-get install dbus
```

---

### Post by Thirtysixway on 2009-01-24
If you're using a text-based IM client, there's also naim which can sign on aim/aol.

---

### Post by MikeBrown on 2009-01-24
I recommend Pidgin. You can use AIM, MSN, xfire, facebook, myspace and more accounts on it! 

AIM, MSN (and myspace I believe) are available by default. For xfire and Facebook, you need to go here: [http://developer.pidgin.im/wiki/ThirdPartyPlugins](http://developer.pidgin.im/wiki/ThirdPartyPlugins)
Each page has links to explain how to install them in Pidgin, but I believe the easiest way to do so is to download the plugin to your desktop, and then click plugins on pidgin, install plugins, and then select the plugin you need.

---

### Post by aaron.d on 2009-01-24
> **MikeBrown said:**
> I recommend Pidgin. You can use AIM, MSN, xfire, facebook, myspace and more accounts on it! 

AIM, MSN (and myspace I believe) are available by default. For xfire and Facebook, you need to go here: [http://developer.pidgin.im/wiki/ThirdPartyPlugins](http://developer.pidgin.im/wiki/ThirdPartyPlugins)
Each page has links to explain how to install them in Pidgin, but I believe the easiest way to do so is to download the plugin to your desktop, and then click plugins on pidgin, install plugins, and then select the plugin you need.

some good info, but keep in mind this is a server install. I assumed no gui in this case.

Like I said above, 'finch' is the cli version of pidgin (both use libpurple) and I can attest that aim/msn/myspace work out of the box.
I also just tested the gfire plugin, a simple dpkg -i and a restart of finch and xfire seems to be working now as well (i dont have an account but 'xfire' is in the drop down options for setting up accounts now).
Set this bad boy up in a screen and you are good to go from just about anywhere you can use ssh.

naim is a bit more mature, but it's support for protocols blocks, from my experience.

pidgin/finch ftw!

---

