---
title: "Installed Dansguardian, lost my LAN"
date: 2007-01-25
forum: Ubuntu Christian Edition
---

### Post by Ennead on 2007-01-25
I loaded Dansguardian to my Ubuntu 6.06, and now I can't see my LAN.  It was working before I installed DG.  My lan consists of my Ubuntu, one xp, and 2 98 boxes.  The windows boxes can all see each other, I can ping the windows machines from Ubuntu, but I can't ping my Ubuntu from the windows machines.  Also, I have a network printer that I CAN print to from my favorite computer, and the internet works just fine now that I'm protected from the scum of the universe.

I've tried a few things, like adding "server samba accept" to firehol, adding "allow 192.169.10.0/24" to Tinyproxy, but no lan so far.  When I go to Places>Network Servers I see the Windows Network icon, but when I click on it, I come up with a blank screen (and F5 update doesn't help).

I'm surprised that there aren't any threads that directly address this problem.  I guess It's not as widespread a problem as I had hoped. :)   I've posted this in the CE forum because I thought there might be more experience with DG installs here.  Any suggestions, links, etc would be greatly appreciated.

---

### Post by mhancoc7 on 2007-01-26
Did you use any of the Ubuntu CE scripts to install dansguardian or did you do it manually?

I am not sure, but you might try using one of our scripts and see if the configuration that we use works. Keep in mind that I have never tested this so it would be at **your own risk**.

God Bless, Jereme

---

### Post by Ennead on 2007-02-07
I finally found the cause of this problem, in case anyone might be helped by this.  It is Firehol that was causing the problem.  The unidirectional pinging was the clue that finally steered me in the right direction.  Here's what I've done so far:

> version 5

# Accept all client traffic on any interface
interface any world
client all accept

Uncommenting the last two lines (interface and client) did the trick (i.e. removing the # signs).  WARNING: I don't know if this makes the computer or the LAN vulnerable to attack or not.  I am still learning how to configure Firehol.  But if you're stuck like I was, this may get you going, and then you can do what I'm doing: add/remove the comments as required to access your LAN when needed and to keep your system secure at other times, until the configuration is done right.  The info at [http://firehol.sourceforge.net/](http://firehol.sourceforge.net/) is helping me toward that end.

---

### Post by tonhou on 2007-02-07
Its worth doing a search on the Ubuntu forums.

This thread probably has all the info you need:

[http://www.ubuntuforums.org/showthread.php?t=207008](http://www.ubuntuforums.org/showthread.php?t=207008)


--Tony

---

