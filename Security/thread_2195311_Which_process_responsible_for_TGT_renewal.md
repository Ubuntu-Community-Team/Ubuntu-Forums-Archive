---
title: "Which process responsible for TGT renewal?"
date: 2013-12-23
forum: Security
---

### Post by vadim_omeltchenko on 2013-12-23
I am on an ubuntu 12.04, trying to figure out a way to force TGT (ticket granting ticket) renewal/request as soon as I login (via LightDM). TGT does get requested automatically, but it takes a while - from 1 to few minutes and in the meantime I get prompted for password by the first app that tries to access certain resources and I'd like to avoid any password prompts.

I know nothing about the process, so hope for some help here.

lightDM gets my password at login and either lightDM itself or some another process get the password in some way and initiates TGT request.. any idea which process does that? Any way to find out?

one possible approach I took was trying to get the login password myself (from lightDM somehow) and initiate TGT request myself, but I can't figure out how to get the password. I thought it would be stored in gnome keyring ~/.gnome/keyrings but seahorse is not showing anything in there... 

So I need help either figuring out where to extract my login password from (to initiate TGT request myself) or find out which process is responsible for initiating TGT request after login and try to call it myself right after login.

Thank you all in advance!!

PS: After I figure this out, next step will be to use VPN's "connection established" hook to refresh/request TGT w/o prompting for password. Basically, as you can see, the final goal is to use the password I enter in lightDM once to later take care of acquiring/renewing TGT in diff situations (switching networks, VPN in/out, laptop sleep/resume,etc)

---

