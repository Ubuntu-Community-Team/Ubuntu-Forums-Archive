---
title: "Capabilities Mismatch with Server Problem"
date: 2009-10-29
forum: Ubuntu One (CLOSED)
---

### Post by donato roque on 2009-10-29
I filed a problem in Launchpad today about the error message i'm getting from Ubuntu One.  The error message said "capabilities mismatch with the server, i may have downloaded updates that are not yet supported by my client". 

After checking Launchpad I found a similar report and added mine.

I tried to figure out what the problem is.  Tried the terminal.  Updated:
sudo apt-get update and yes it wants to update my Ubuntu One client.  After I proceeded with the upgrade, I closed the Ubuntu One desktop client and started it again.  

It works now.

---

### Post by DishBreak on 2009-11-17
To clarify, open a terminal and type 
```
sudo apt-get update
```

Then, look for the Ubuntu One applet next to the clock. It should be showing an exclamation point inside a loop. Left-click it, and select quit.

Alternatively, you can go to the System Monitor (System -> Administration), and terminate the ubuntuone-client and ubuntuone-syncdaemon processes. 

Thanks for the tip!

---

### Post by Scooter_X on 2009-11-19
Okay, but then mine asks for:

[sudo] password for riley:

and I type in my password that I use to log in. And sorry, I'm new at this, but I'm thinking perhaps it's asking for a different password than what I'm using because it didn't work. Could someone point me in the right direction? I would really appreciate it. Thanks.

---

### Post by morchuboo on 2009-11-21
For those new to Ubuntu its easier to update graphically.
In the menu select System --> Administration --> Update Manager
You can then select the install updates button.

---

### Post by joshuahoover on 2009-11-24
> **morchuboo said:**
> For those new to Ubuntu its easier to update graphically.
In the menu select System --> Administration --> Update Manager
You can then select the install updates button.

Yes, and remember to restart the Ubuntu One client after running Update Manager. :-)

---

### Post by runescape1143 on 2009-11-28
I think it asks for the password for the keyring. It's the same password as you would need to use for a secured wireless connection.

---

