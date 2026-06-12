---
title: "Gaim2.0 Guification theme for Dapper"
date: 2006-03-23
forum: The Cafe
---

### Post by krusbjorn on 2006-03-23
Hey all,

The libnotify plugin for Gaim2.0 made it crash alot, so I made some modifications to an already [existing guifications theme]("http://sourceforge.net/tracker/index.php?func=detail&aid=1447892&group_id=92888&atid=676821"), to make it go better with the default colours of the Dapper human theme. 

I installed the guifications plugin for gaim2.0 by adding:
> deb [http://idefix.eup.uva.es/paquetes/gaim2.0/](http://idefix.eup.uva.es/paquetes/gaim2.0/) ./ to my /etc/apt/sources.list and then did:
> sudo apt-get update
sudo apt-get install gaim2.0-guifications
After gaim2.0 is restarted, guifications should appear in the plugins list.

Unpack the attached archive to ~/.gaim/guifications/themes
By the way, I believe this theme works for guifications for gaim 1.x too.

Credit to [Antonio]("http://sourceforge.net/users/antonioriva/") for the original theme.

---

### Post by dcraven on 2006-03-23
Nice work. I'm using gaim-libnotify from CVS currently and haven't experienced any crashes as of yet though. What version were you using prior to your new guification?

~djc

---

### Post by krusbjorn on 2006-03-23
[QUOTE=dcraven]Nice work. I'm using gaim-libnotify from CVS currently and haven't experienced any crashes as of yet though. What version were you using prior to your new guification?

~djc[/QUOTE]

The one in the repos, which would be 0.6 I believe.

---

### Post by Stereotypical Rage on 2006-03-23
0.8 made it crash alot, using the deb. I found.

simplyw00x, one of the devs for gaim-libnotify told me to not use the 0.8 deb. He said to compile it using his instructions provided in the thread about GAIM2.0beta2 in the dapper forums.

However the one in the repos, is 0.6(0.8reverted0.6), along with 0.8-2, 0.8-1.

I haven't compiled gaim-libnotify, yet, I'm still using 0.6 :P

---

