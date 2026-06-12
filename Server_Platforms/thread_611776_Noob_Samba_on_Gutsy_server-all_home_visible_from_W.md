---
title: "Noob: Samba on Gutsy server-all /home/ visible from WinExplorer"
date: 2007-11-13
forum: Server Platforms
---

### Post by avlewis@gmail.com on 2007-11-13
Hello all,
I've successfully (?) installed Gutsy as a LAMP server, and configured Samba so that the three users can access their files from Windows XP (Pro & Home).
Problem is, everyone can see & access all accounts, and when typing in \\server\useracct in the Address box in Windows Explorer, there is no user/pass prompt.
Obviously I've done something (or things) wrong, and my O'Reilly Samba book hasn't arrived yet;-)
I've looked around online, and all the shares are set to Browsable = no; at least the ones I can find. I don't understand all the Global options under 'Browsing'.
Any ideas, other than read the book?
Also, does anyone have any suggestions on books to read to really learn Ubuntu from the ground up. I am less interested in GUI apps than I am in CLI administration.
I'm hoping to use Ubuntu as a LAMP server here at work, but I'm going to need to know a lot more than I do before I suggest rolling this out to the bossman.
Many thanks,
Vic

---

### Post by solar george on 2007-11-13
Try 
```
;   valid users = %S
```

> # By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S


---

