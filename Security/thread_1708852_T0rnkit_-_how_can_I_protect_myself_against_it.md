---
title: "T0rnkit - how can I protect myself against it?"
date: 2011-03-17
forum: Security
---

### Post by Netaro on 2011-03-17
Ok, so here's the problem, somehow my computer got rooted with the aforementioned rootkit. I've purged everything, and now I'm reinstalling the system. 
Question is, I don't know how it got there. I believe I've set up my security good enough not to let anything like that happen (on the other side, I'm not experienced enough to say whether what I've done was good enough). Only thing that I could find on google was > -Login to WHM as root
-Click Tweak Settings and please remove the tick from
[ ] Allow cPanel users to reset their password via email

But, I don't have WHM on my computer, at least I think so (can't find it there). 

So, what should I do then? I don't want to move all my data back and forth evey time this happens.

---

### Post by cariboo on 2011-03-17
If you actually where rooted, it's obvious that someone gained root access to your system. It's to late now, but if you had checked /var/log/auth.log, you may have found a clue as to who gained access to your system. If you are only using the system as a print and file server, there shouldn't be any services open to the internet.

---

### Post by rookcifer on 2011-03-18
What kind of server were you running on this box?  Most likely you were the victim of a brute-force on some sort of server password or an unpatched exploit on some daemon.

At any rate, the only thing to do is reformat and reinstall and then figure out how to stop this from happening again.

---

### Post by brian_p on 2011-03-18
> **Netaro said:**
> Ok, so here's the problem, somehow my computer got rooted with the aforementioned rootkit. I've purged everything, and now I'm reinstalling the system. 

How do you know you were rooted?

---

### Post by Netaro on 2011-03-18
> **rookcifer said:**
> What kind of server were you running on this box?  Most likely you were the victim of a brute-force on some sort of server password or an unpatched exploit on some daemon.

At any rate, the only thing to do is reformat and reinstall and then figure out how to stop this from happening again.

It was running LAMP, BOINC, torrent client, vnc, ssh, ftp. Nothing more that I'm aware of. I wasn't using ssh keys, instead I was manually entering password every time I wanted to connect. vnc was passworded, ftp was locked to user's home.  
I had forwarded port 80, ftp, ssh, vnc, torrent on my router. 
I don't believe it would be possible to brute-force my passwords. I'll set up harder passwords anyway. 

I've already purged the disk, but next time it happens, I'll post any logs You'll ask to see how in the hell it got there.

[QUOTE=brian_p]How do you know you were rooted? [/QUOTE]
I've noticed that top had a libncurses problem. top > libncurses not found or something like that. One google away, and I've got a bad feeling about that. So I've installed rkhunter and chkrootkit. And voila, I have to reinstall it.

---

### Post by brian_p on 2011-03-18
> **Netaro said:**
> 
I don't believe it would be possible to brute-force my passwords. I'll set up harder passwords anyway.

If your passwords were a decent number of characters and not a common word (>>myloginisreallysafe!<<, say) your belief is soundly based.

> I've noticed that top had a libncurses problem. top > libncurses not found or something like that. One google away, and I've got a bad feeling about that. So I've installed rkhunter and chkrootkit. And voila, I have to reinstall it.

I'd not trust rkhunter or chkrootkit to tell you anything of importance about your system.

---

### Post by Netaro on 2011-03-18
> **brian_p said:**
> 
I'd not trust rkhunter or chkrootkit to tell you anything of importance about your system.
Why? I think (I've thought) that these are rather reliable.

---

### Post by pricetech on 2011-03-18
FTP passes credentials in the clear.  I'd find an alternative for file access.
VNC is inherently insecure also.  Again, find an alternative.  I'd recommend NX from nomachine dot com.  They have a windows client too in case you need one.
Consider also using non standard ports, just to annoy the invaders.

---

### Post by brian_p on 2011-03-18
> **Netaro said:**
> Why? I think (I've thought) that these are rather reliable.

What is enormously more reliable is (to answer your initial question):

[LIST]
[*]Keeping your sytem updated.

[*]Configuring daemons correctly.

[*]Obtaining software from trusted sources.
[/LIST]

You'll be malware free and have no need for programs of dubious value.

---

