---
title: "Ubuntu One with no GUI"
date: 2009-11-18
forum: Ubuntu One (CLOSED)
---

### Post by slyngshede on 2009-11-18
Hi, 

I'm trying to get Ubuntu One working, one a remote machine, that doesn't have Gnome/KDE or any other GUI running. 

The first issue I seem to run into is that u1sync --authorize won't run, because theres no Gnome keyring, obviously I don't want a Gnome keyring, I just want Ubuntu One for backup. 

In the man pages for u1sync the --oauth is described and indicate that I can use that option for autorizing, if I don't want to use the keyring. What key is it that I'm suppose to use here?

The documentation for Ubuntu One is really poor, if you have no wish to have X11 running. Is it at all possible to do what I want?

---

### Post by duanedesign on 2010-01-28
Currently they dont support running U1 without Gnome-keyring but i think it is possible. This was taken from a conversation in #ubuntuone, hope it helps.

> i think it may work with that. but you have to get the keys by hand from another machine and use them to start syncdaemon with the keys in the cmd line (i think that putting them in the config file may also work)

 i think in that case we dont call gnome keyring

yes, passing the oauth token and secret via CLI args should work

you might want to hop onto IRC freenode and visit #ubuntuone and ask in there. Usually between 14:00 - 19:00 GMT you can find someone.

---

