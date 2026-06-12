---
title: "Samba configuration question"
date: 2006-09-24
forum: Server Platforms
---

### Post by Nadim on 2006-09-24
Trying to set up samba on my new Ubuntu (6.06.1) machine...in the past I've always set it up with the old shared security model, but I figured I would give "user" a try.  Problem is, I'm not sure I get how things are supposed to work exactly.  Looking at the smbpasswd docs, it seems that samba wants to maintain a separate password store, but all I really want is for it to just authenticate using the Unix passwords.  From the smb.conf man page, it says under step 1 of the Note About Username/Password Validation that it will validate a user's password against UNIX system's password programs.  Why then all the options for unix passwd sync?

Anyway, I wouldn't be asking these questions, except that I fired up samba, did minimal smb.conf editing (changed workgroup name to correspond to the same name as my Win machines, added a couple shares), and tried to connect to the machine from Windows (XP, SP2).  It finds the machine okay, but when I double-click, it asks me for name and password, and refuses to accept my Unix name/password credentials.

I figured I'd try smbpasswd, in case I did't understand/interpret the smb.conf man page correctly, but smbpasswd fails with: "Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE".  I haven't done anything in terms of editing hosts allow/deny in smb.conf, though...it's stock except for the mods above.

Any ideas?

---

### Post by chrisfay on 2006-09-24
You have many options for authentication for Samba...

The quickest way is to add a Samba user with the command:

```
sudo smbpasswd -a user
```
...replacing 'user' with a unix user on your system; follow the next two prompts for the password and you should be able to access the shares from Windows by entering this info in the login prompt. 

I was having the same problem unitll adding the Samba user.

---

### Post by neXenta on 2006-09-24
Hello, 

Can you tell me a good front-end graphical samba tool?

Thanx

---

### Post by chrisfay on 2006-09-24
SWAT - Samba Web Administration Tool 

[http://www.linuxsoft.cz/en/sw_detail.php?id_item=3831](http://www.linuxsoft.cz/en/sw_detail.php?id_item=3831)

You can get it from the repositories with:

```
sudo aptitude install swat
```

Here are some others as well:
[http://www.samba.org/samba/GUI/](http://www.samba.org/samba/GUI/)

---

### Post by neXenta on 2006-09-24
chrisfay, thank you for the reply! Now, my main chalage is sharing the resources in a home network with a win2000 server wich is a real pain in the..u now where.:D If you now a nice How to just for simply sharing file in a network please forward to me! I mention that both computers are in the same workgroup without a domain. What I want is just to access a public shared folder from my private network for someone who does not know nothing about computers, to have access to some docs or other resources.
Thank you!

---

### Post by neXenta on 2006-09-24
Ohh, I just downloaded swat from repo and install it but it the app get stuck when i start it. No error messages from the terminal.
!?

---

### Post by chrisfay on 2006-09-24
Check your logs...

/var/log/syslog
/var/log/debug
/var/log/messages

---

### Post by bluefrog on 2006-09-26
[http://samba.org](http://samba.org) menu "by example" should be your bible/coran/tora/etc (random order...) regarding questions about setting up samba.

James

---

