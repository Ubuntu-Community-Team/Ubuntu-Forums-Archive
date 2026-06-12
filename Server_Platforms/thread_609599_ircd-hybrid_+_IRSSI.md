---
title: "ircd-hybrid + IRSSI"
date: 2007-11-11
forum: Server Platforms
---

### Post by poisonmushroom on 2007-11-11
I installed ircd-hybrid (apt-get install ircd-hybrid) and after that i installed IRSSI (apt-get install irssi) so i can create an IRC server on my old box (OS: Ubuntu Server Edition)

After installing and doing small changes in the config files, i ran irssi through putty, then wrote /Connect <my box's LAN ip>  and it worked, gave me a MOTD and stuff, then i gave my WAN ip to a friend to try and connect and it also worked and we chatted.

the thing i wanted to ask was about the dynamic dns thing, i created a new account in [www.dy.fi](www.dy.fi), an created a new host: mushroom.gurut.be
(i did this because i have a Dynamic IP). After doing so i saw a text that says "point" i didnt know what it does but when i clicked it it showed me my WAN ip, and when i write the ip in the browser it takes me to my routers configuration page for some reason.

what i want to know is, how am i supposed to use this domain name so when people write it into their irc client they connect to my server?

(There was a tutorial on using CRON and adding commands to it that link to dy.fi and stuff but it didn't make any difference)

Thank you very much for reading! :)

**EDIT: I got it to work, nevermind ;) now i just need to change the configuration and MOTD to suit my needs.**

---

### Post by darkazurka on 2007-12-30
When you want to turn it off, do you uninstall the application or do you use a command on the commandline? So far I uninstall it since doing stuff like
```
ircd-hybrid stop
```
brings error messages. (although I'm trying to tell it to turn off just like you can tell an apache http server to turn off)

---

