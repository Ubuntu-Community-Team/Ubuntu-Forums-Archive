---
title: "NIS-users can't log in"
date: 2006-07-10
forum: Server Platforms
---

### Post by seraphim on 2006-07-10
Hi there :)

I'm in an office with 5 clients and a server. Before I arrived, everything was running on SuSe. Now I'm trying to change the first client to Ubuntu.
I installed nis and configured it as described on so many websites. Everything **seems** to be alright, but the nis-users just can't log in from the Ubuntu-Box. "ypcat -k passwd" gives me the users which are imported:

> [...]
marci marci:x:1020:100::/home/marci:/bin/bash
sera sera:x:1021:100::/home/sera:/bin/bash
[...]

the files /etc/passwd /etc/group /etc/shadow and /etc/gshadow all got a new line with a + and several ::

the error-message from auth.log is:
> Jul 10 13:12:57 ubuntu-desktop1 login[5908]: FAILED LOGIN (1) on `tty2' FOR `sera', Authentication failure

i hope anybody can help me here. i'm at a loss with it.

---

### Post by seraphim on 2006-07-11
help!
i still didn't find a solution. i found out that ypcat -x doesn't show up a shadow-map, but that's the same at the other clients.
playing around with "compat" and "files nis" in /etc/nsswitch.conf also didn't help.
any suggestions please? :-k

---

### Post by pclancy on 2006-07-11
I had a long fight with NIS and ubuntu, eventually what I ended up doing was completely starting over.  I used this guide: [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

Now, it's working perfectly.  My only suggestion is to print out the instructions, and fill in the variables before you do anything.  I found that this made me think equally hard about each piece to make sure everything was correct.

---

### Post by Soleil-Raid on 2006-07-11
At the risk of inviting flames... Any particular reason you're using NIS instead of LDAP?

My last attempt at an NIS... well, lets just say I gave up and went back to manually keeping uids and passwords in sync (granted, for two competent users on three boxes).

My attempts at an LDAP installation (two years later on a completely different network mind) were much more successful.

LDAP appears to be much more robust, and intergrates more cleanly with the NSS/PAM setup that most installations use, without requiring requiring the user to modify passwd/shadow/group files. It also runs over a single TCP port and lets you use SSL or TLS, thus being safe enough for general Internet usage, rather than that god-awful portmap. Plus there's LDAP->NIS adaptors, for those applications that just won't work with LDAP

I just can't help feeling that NIS is one of those outdated technologies that really really just needs to die.

Any thoughts?

---

### Post by seraphim on 2006-07-13
of course the ubuntu help was one of my first resources, no luck with it.

i didn't start using nis here, but what you say sounds good, and i read a lot about security issues with nis.
i will ask if i can change the whole network to ubuntu/LDAP now :cool:

---

### Post by compbrain on 2006-07-15
> **seraphim said:**
> of course the ubuntu help was one of my first resources, no luck with it.

i didn't start using nis here, but what you say sounds good, and i read a lot about security issues with nis.
i will ask if i can change the whole network to ubuntu/LDAP now :cool:

Hi,

Did you modify you nsswitch.conf to include nis? 
Did you see if there is different behavior when logging in via gdm/console?
Any relevant logs in syslog or /var/log/messages?

---

