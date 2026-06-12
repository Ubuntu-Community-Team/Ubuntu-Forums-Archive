---
title: "Do I have a good tor exit policy for minimizing abuse"
date: 2012-07-25
forum: Server Platforms
---

### Post by MechaMechanism on 2012-07-25
I'm running an exit relay on a consumer ISP line.  I need to make sure my torrc has a good exit policy to minimize the chance that my ISP will take notice (Not worried about TOS or AUP, just easer to avoid having to explain what tor is.).  Plus I want my tor server being used for legit needs and not bittorrent.

My exit policy:
ExitPolicy accept *:119 # accept nntp as well as default exit policy
ExitPolicy accept *:22  # ssh
ExitPolicy accept *:80 # www
ExitPolicy accept *:443 # www secure
ExitPolicy accept *:110 # pop3
ExitPolicy accept *:143 # imap
ExitPolicy accept *:995 # pop3 secure
ExitPolicy accept *:6660-6669 # irc
ExitPolicy accept *:6697 # irc ssl
ExitPolicy accept *:7000-7001 # irc ssl
ExitPolicy accept *:706 # silc
ExitPolicy accept *:1863 # msn
ExitPolicy accept *:5050 # yahoo messenger
ExitPolicy accept *:5190 # various im programs
ExitPolicy accept *:5222 # various im programs
ExitPolicy accept *:5223 # various im programs
ExitPolicy accept *:8300 # im
ExitPolicy accept *:8888 # www
ExitPolicy accept *:465 # smtps (SMTP over SSL)
ExitPolicy accept *:993 # imaps (IMAP over SSL)
ExitPolicy accept *:994 # ircs (IRC over SSL)
ExitPolicy reject *:* # no exits allowed

---

