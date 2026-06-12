---
title: "amd k6b 650mhz 160mb ram 40 gig hd"
date: 2005-11-14
forum: Server Platforms
---

### Post by blu.gecko on 2005-11-14
I am currently running breezy 5.10 with gnome, I did a full desktop install and then weeded out things like gnome-games and all the music and media and office, and so forth, I run at like a 65% level on ram and 4% CPU, if I did a server install and did a openbox or blackbox install and re installed samba and ftp server would it run less ram processes or would it be about the same?

blu.gecko

---

### Post by drogoh on 2005-11-14
You would see a decrease if you got rid of Gnome altogether, so yes.

---

### Post by blu.gecko on 2005-11-14
If I got rid of gnome, and replaced it with openbox or something along those lines, would it use less ram, my hnome is on non icon mode right now, and its very minimal, I deleted alot of the applications. I dont know the terminal well enough to set up a samba file server and ftp file server straight out of the terminal, im a gedit guy still. my box doesnt have mail or browser functions, just servers my network and some ftp.

blu.gecko

---

### Post by mcewen98 on 2005-11-14
yes, fluxbox or any of those light weight window managers will use less ram than gnome.  Deleting applications won't do anything in terms of making gnome use less resources.

If you are uncomfortable with the terminal, it would be most beneficial to learn either VI or Emacs, (I prefer emacs, just do a google search for basic emacs commands). You can always set up webmin and get the samba and ftp plugins.  Then you could administer the machine from another with a browser.

I think by default webmin only accepts connections from localhost.  In the setup there is a way to change this, but i'm not sure how it's done from the command line.  I'm sure either searching google or somebody else on this forum has an answer

---

### Post by blu.gecko on 2005-11-14
ok,

so from a terminal would I type in "sudo apt-get install openbox" ? and I am guessing it would tell me that it needs dependencies......

---

### Post by blu.gecko on 2005-11-14
and how would I log in xstart?

---

### Post by blu.gecko on 2005-11-14
i did a search in ubuntu package search and webmin, isnt listed. do you mean like cpanel?
I installed emacs21 no problem through the terminal, that wont be an issue but they removed openbox,fluxbox and blackbox from the source, so you can no longer install it.....

---

### Post by mcewen98 on 2005-11-14
you may have to edit /etc/apt/sources.list and uncomment the 2 lines for the universe repository.  That is, remove the # from the front of these lines:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

Fluxbox is in the universe repository so it would show up after you uncomment the above mentioned lines and do: sudo apt-get update 

I am not sure which, if any GDM gets installed with fluxbox.  If worst came to worse, I think you would just get a text login, after which you could type startx

---

