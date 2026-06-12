---
title: "Help troubleshooting IRC Connection issue in Guest OS (Ubuntu) VMWare"
date: 2015-10-05
forum: Virtualisation
---

### Post by daveomcd on 2015-10-05
I'm using VMWare (Host: Win7, Guest: Ubuntu 15.04), and I'm unable to connect to irc.ubuntu.com.  I have Kaspersky on my host also.  I'm unable to connect to any IRC servers on the guest.  I get the following message:

```

11:19 -!- Irssi: Connecting to irc.freenode.net [185.30.166.37] port 666711:19 -!- Irssi: Connection to irc.freenode.net established
11:19 -!- Irssi: warning Connection reset by peer
11:19 -!- Irssi: Connection lost to irc.freenode.net

```

also from XChat...
```

* Looking up irc.ubuntu.com
* Connecting to chat.freenode.net (162.213.39.42) port 6667...
* Connected. Now logging in...
* Disconnected (Remote host closed socket).

```

Anyone know how I can attempt to troubleshoot this issue?

---

### Post by CharlesA on 2015-10-06
Are you able to connect from the host? There shouldn't be any difference as long as the network is working.

---

### Post by daveomcd on 2015-10-07
> **CharlesA said:**
> Are you able to connect from the host? There shouldn't be any difference as long as the network is working.

I am able to connect from the host with no problem.  Also the networking I have setup between the host/guest using VMWare is a bridged connection.

---

### Post by Habitual on 2015-10-07
> **daveomcd said:**
> I'm unable to connect to any IRC servers on the guest.  I get the following message:

```

11:19 -!- Irssi: Connecting to irc.freenode.net [185.30.166.37] port 666711:19 -!- Irssi: Connection to irc.freenode.net established

```

also from XChat...
```

* Connected. Now logging in...

```

Anyone know how I can attempt to troubleshoot this issue?

Clearly, it says "irc.freenode.net established" and "Connected. Now logging in..."
Are you trying to connect to irc as root?

---

### Post by daveomcd on 2015-10-07
> **Habitual said:**
> Clearly, it says "irc.freenode.net established" and "Connected. Now logging in..."
Are you trying to connect to irc as root?

I've tried opening the client with both "sudo", and no "sudo".  I get the same results both time.

---

### Post by daveomcd on 2015-10-12
Sorry to dig this back up, but doesn't anyone have any suggestions on where I could troubleshoot? Any network monitoring tools and what I could look for to see where I might try to look next?  Thanks for everyone that's help/read this so far. It's much appreciated!

---

### Post by Habitual on 2015-10-12
check your .xchat2/xchatlogs/FreeNode-.log for clues ?

---

### Post by daveomcd on 2015-10-12
> **Habitual said:**
> check your .xchat2/xchatlogs/FreeNode-.log for clues ?

Thanks but doesn't seem to be any more descriptive than the xchat window itself. Simply stating that the connection was reset by peer.

---

### Post by Habitual on 2015-10-12
Tell us more about the network setting in Virtualbox for the guest.
I use Bridged Adapter myself for all my guests.

---

### Post by daveomcd on 2015-10-12
Do these help? Or is there something else I could provide?

 [IMG]http://i.imgur.com/ZWhPvyR.png[/IMG]
[IMG]http://i.imgur.com/FA4Rxja.png[/IMG]

---

### Post by Habitual on 2015-10-12
My Virtualbox network preferences are displayed differently.
Looks ok, except for the "Replicate" option box.

What version of Vbox is this exactly and how was it installed?

The next thing I'd check the properties for FreeNode in .xchat
Here's  mine for comparison.
[ATTACH=CONFIG]264910[/ATTACH]

---

### Post by daveomcd on 2015-10-12
I'm using VMWare not VirtualBox.  Also looks like our XChat information is pretty much the same.

---

### Post by Habitual on 2015-10-12
Oh poop!
Sorry, I am not well versed enough to debug VMWare client.

---

