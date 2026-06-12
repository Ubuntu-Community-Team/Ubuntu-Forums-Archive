---
title: "Guarddog for an idiot?"
date: 2009-01-28
forum: Security
---

### Post by Another Monkey on 2009-01-28
I just installed Kubuntu (been playing with Ubuntu) and I wanted to get File Sharing working as I did in Ubuntu.  I have Samba installed and configured.

Guarddog is tripping me up.  I know this is a GUI to iptables, but as a newbie it is easier to use.  Well, I thought it would be.  When I tell Guarddog to enable the firewall, all networking dies.  File sharing, HTTP, the lot.

As a test I allowed HTTP Internet->Local and Local->Internet, but even that didn't work.  I am probably missing something really obvious here.

Is there a "Guarddog for total morons guide"?  Or does anyone have an idea why it seems to be stuck in "total lockdown", even if I allow the protcols?

---

### Post by Nepherte on 2009-01-28
I'm afraid I don't have an answer to your problem, but perhaps you should consider using ufw (or gufw). It is very easy to use. It hardly requires an explanation.

---

### Post by Another Monkey on 2009-01-29
I got HTTP going, I had to add DNS as well Internet -> Local.  I can't belive I forgot that.

I also got file-sharing working by making sure that "Micorsoft SMB over TCP" and "NetBIOS" as allowed Local -> LAN Zone and LAN Zone -> Local.  I am sure I had that last night.  Ah well.

My current problem is that Guarddog is blocking adept and I can't find any information on what ports to allow.  Best start that in a clean thread I think.

gufw seems to want to install half of Gnome into KDE.  I have different Ubuntu box I can play on, so I think I will try to get to grips with Guarddog.  Thanks for the tip though, I may use that on the Ubuntu machine in place of Firestarter.

---

### Post by birkopf on 2009-02-17
> **Another Monkey said:**
> I got HTTP going, I had to add DNS as well Internet -> Local.  I can't belive I forgot that.


I have similar problem with guarddog. I managed to have everything working except of ktorrent and straming in amarok. I also need help. Anyone good with guarddog ?

---

### Post by terabyte1 on 2009-02-17
I have a better time of it with Firestarter (which works with Ubuntu and Kubuntu. To use it follow the instructions in the help menu and you won't go far wrong.


I hope that helps!


Cheers


Terabyte1;)

---

### Post by birkopf on 2009-02-17
> **terabyte1 said:**
> I have a better time of it with Firestarter (which works with Ubuntu and Kubuntu. To use it follow the instructions in the help menu and you won't go far wrong.
Terabyte1;)

switching to another program is not what i am looking for.

---

