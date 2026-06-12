---
title: "ulimit always resets to default"
date: 2006-05-31
forum: Server Platforms
---

### Post by el3ktro on 2006-05-31
Hi,
the server in my company has some login problems with Windows clients, the clients say they can't connect because the server doesn't accept any new connections due to limited resources. It seems we have solved the problem by setting the limit for open files to a higher value. ulimit -n was 1024, and we've set it to 16383. This works fine, but somehow this limit is always reset to the default value of 1024. I don't know when, because I'm not here overnight. Any ideas?

Tom

---

### Post by linuchsan on 2006-05-31
you can set it in /etc/profile, but take a look at man bash first, section ulimit.

---

### Post by el3ktro on 2006-05-31
[QUOTE=linuchsan]you can set it in /etc/profile, but take a look at man bash first, section ulimit.[/QUOTE]

Uhm wait, this means this is a per-shell limit? Hmm. Well our problem is as follows: We have one Samba server, and around 70 WinXP + a few Win2k clients connecting to it. Everything works fine, except when I create a new user on the server (we have roaming profiles) and I try to log this user in at any of the clients, I always get an error that the domain is not available. Sometimes when I try to connect to the server with "net use" etc. it says that the max. connections to the serbver has been reached, because there are no more resources on the server.

The server is a Quad-Xeon machine with 2gigs of RAM and plenty of HD, and _exisiting_ users work flawlessly. A new user works just after a while when I try and try again to log in.

Somebody told me there may be a limit on the server about max. open files, some memory limit or whatever - I thought this would have to do with ulimit.

Do you have any ideas? What kind of limit could prevent new users from logging in?

Tom

---

### Post by linuchsan on 2006-05-31
Than you have to set it in /etc/security/limits.conf

*	soft	nofile	16383
*	hard	nofile	16383

---

### Post by el3ktro on 2006-05-31
[QUOTE=linuchsan]Than you have to set it in /etc/security/limits.conf

*	soft	nofile	16383
*	hard	nofile	16383[/QUOTE]

Thanks a lot for your help. Two small questions remain: _Could_ this be causing the problems we have. lsof says that the server right now hasabout 6900 files open, thats certainly a lot. And the 2nd question: How can I activate these new limits without rebooting?

Tom

---

### Post by linuchsan on 2006-05-31
It will reset after reboot...you can put a ulimit string before the daemon starts in the samba init script

---

