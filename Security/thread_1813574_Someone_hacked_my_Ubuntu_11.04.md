---
title: "Someone hacked my Ubuntu 11.04"
date: 2011-07-27
forum: Security
---

### Post by suang on 2011-07-27
When I was reading Google search results, suddenly someone out there clicked on one of the Google results link, and it opened in a new tab.
I browsed the net using Firefox 5.
Before that, When I opened my MS office document, I found that a few senteces have been moved to the left. 
Is this because I configured my modem to use DHCP?
When I used Windows Xp, this problem also happened. I thought It would not happen again in Ubuntu.
Should i use firestater?

---

### Post by Thewhistlingwind on 2011-07-27
Turn off remote desktop, because I guarantee if theres remote access going on thats the cause.

Firestarter is deprecated, please use UFW, GUFW, or IPtables.

---

### Post by HermanAB on 2011-07-28
Hmm, don't play with VNC (remote desktop).  It is an eeeeevulll POS and it is the main (only?) reason Ubuntu users get hacked.  These forums are full of tales of woe...

---

### Post by suang on 2011-07-28
Thanks for replying.
I have activated the ufw using Terminal: sudo ufw enable
How to use the GUFW and IPtable?
How to turn off remote desktop in Ubuntu 11.04?
Sorry, asking too much, I never used Ubuntu before.
Thanks in advance.:D:popcorn:

---

### Post by jerome1232 on 2011-07-28
> **suang said:**
> 
How to turn off remote desktop in Ubuntu 11.04?


It's off by default, you would've had to turn it on yourself, out of curiosity are you actually running any services?

```
sudo netstat -tlnp
```

Please post the output of that command.

The way to turn off remote desktop if it is on, click the ubuntu logo at top left, search for "remote desktop" make sure "allow other users to view your desktop" is unchecked.

---

### Post by suang on 2011-08-08
Sorry, for late reply. I am watching for whether is there any more impact on my computer.
The result from netstat -tlnp is tcp 127.0.0.1,port 8118, tcp6 port 631.
I have deleted all remote desktop installed but still when i clicked a link in google search results to open in new tab, suddenly it switched back to current tab & immediately opened a cached version of that link i have clicked from google search results.
After that i removed all file sharing from ubuntu software center and also samba & smb.
Before i installed ubuntu, i have formatted all partition.
my usb flash disk was once infected when i still used window xp but has been removed. I still using that flash disk.
What is the best antivirus that scan ubuntu virus, not only windows xp virus?
Thanks alot. *_^

---

### Post by suang on 2011-08-08
Sorry, for late reply. I am watching for whether is there any more impact on my computer.
The result from netstat -tlnp is tcp 127.0.0.1,port 8118, tcp6 port 631.
I have deleted all remote desktop installed but still when i clicked a link in google search results to open in new tab, suddenly it switched back to current tab & immediately opened a cached version of that link i have clicked from google search results.
After that i removed all file sharing from ubuntu software center and also samba & smb.
Before i installed ubuntu, i have formatted all partition.
my usb flash disk was once infected when i still used window xp but has been removed. I still using that flash disk.
What is the best antivirus that scan ubuntu virus, not only windows xp virus?
Thanks alot. *_^

---

### Post by Thewhistlingwind on 2011-08-08
> **suang said:**
> 
What is the best antivirus that scan ubuntu virus, not only windows xp virus?
Thanks alot. *_^

clamAV, but theres no Linux viruses in the wild. If your sure VNC is off, theres no SSH server, and no listening services installed AT ALL. Then something else is the problem.

---

### Post by mikewhatever on 2011-08-08
Is there any evidence that you got hacked, other then your imagination? Try clearing the browser cache, and relax, there was probably nothing apart from some javascript trickery.

---

### Post by suang on 2011-08-08
I have set my Firefox 5 to "Never Remember History"
so, I don't have to clear any cookies, cache or history.
In windows xp, there is a tool for cleaning up the temp folder, and other unused files. What about ubuntu?
It's not my imagination that my Ubuntu got hacked.
No one want their computer being hacked, and i don't want to create a sensation here either!

---

### Post by mikewhatever on 2011-08-08
History and cache are not the same, also, firefox doesn't use the /tmp folder.
In firefox, Tools-> Clear Recent History (ctrl+shift+del), and only tick the cache box. For the record, firefox's cache is in '~/.mozilla/firefox/*.default/Cache'. Run
**du -h ~/.mozilla/firefox/*.default/Cache** to check its size.

---

### Post by cbruce8 on 2011-08-08
The result from netstat -tlnp is tcp 127.0.0.1,port 8118, tcp6 port 631 says to me you have not been 'hacked'.

-c

---

### Post by wacky_sung on 2011-08-08
> **Thewhistlingwind said:**
> clamAV, but theres no Linux viruses in the wild. If your sure VNC is off, theres no SSH server, and no listening services installed AT ALL. Then something else is the problem.

BTW there is no Linux viruses in the wild does not hold much longer anymore at this present day.In fact, i have seem countless XSS script, java script,etc which work on Microsoft Operation System, Mac and Linux as well in those underground hacking forums.

---

### Post by Thewhistlingwind on 2011-08-08
> **wacky_sung said:**
> BTW there is no Linux viruses in the wild does not hold much longer anymore at this present day.In fact, i have seem countless XSS script, java script,etc which work on Microsoft Operation System, Mac and Linux as well in those underground hacking forums.

Right, almost forgot.

@ the op, you ARE using noscript, right?

---

### Post by wacky_sung on 2011-08-08
> **Thewhistlingwind said:**
> Right, almost forgot.

@ the op, you ARE using noscript, right?

Noscript is good but it has become an annoyance to me.:guitar:

---

### Post by Ad1217 on 2011-08-08
Google link: you may have accidentally hit the middle mouse button, which opens links in a new tab
Office Document: sometimes files display differently between Windows and Ubuntu. they can also slightly change after a save and reload.

Anyway, what makes you think that anyone would go through this kind of trouble to do these two random tasks? they have not harmed you in any way.

---

### Post by jerome1232 on 2011-08-09
You aren't running any listening services, so the only other way you could have been exploited by my knowledge is via firefox. The issues you are reporting sounds more like buggy or incorrectly configured software more than someone having exploited your machine.

---

