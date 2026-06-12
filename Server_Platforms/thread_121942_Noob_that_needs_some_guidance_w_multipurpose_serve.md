---
title: "Noob that needs some guidance w/ multipurpose server"
date: 2006-01-26
forum: Server Platforms
---

### Post by DigitalDuality on 2006-01-26
I'm still no linux expert by any means, only really been on it for under a month now, but i seem to be getting the hang of it from the desktop perspective.  I've got the basic command line down and can now do all my daily, weekly, and monthly functions on my PC that i would normally do on my mac or win boxes.

I'm pretty well trained on the windows side of things, even in the server arena, so server technology isn't too strange to me.

But networking and server technology with linux is a bit alien.

First off, I have an older machine i'm testing this on.  i'd let to set up an e-mail server, just to handle 1-3 addresses.  Pop3 preferably, with Clam and Spamassassin.

Secondly, i want my PC (w/ ubuntu 5.10) to authenticate against this server in order to log in to the machine (other than local root acct of course).

Third, (which wouldn't be so hard) i want either Terminal Services or VNC remote connection from the server to the client.

Fourth, I want to run a print server hosting one printer.


This is all for testing purposes.  I would like to run my own e-mail for home.  But this is more of a practice exercise for me.  If i can familiarize myself with the system in general, I'll be more likely to implement this in my work place which would cut down expenses incredibly much.  I'm looking to replace every client workstation and every server eventually with a *nix OS of some kind.  Everything but the webserver, i will probably make Ubuntu. Webserver.. i'll probably go the fBSD route.

So any starting points for the above would be greatly appreciated.  Basically i'm looking for the most user friendly way in which to do these things, but i don't want user friendliness totally wiping out the amount of control i have either.

---

### Post by DigitalDuality on 2006-01-26
Oh, and i would like a GUI, preferably xfce.  Fluxbox would work too, but i currently already have Ubuntu Server installed with xfce ready to go.

---

### Post by Glut on 2006-01-26
There's a few HOW-TOs running around on this type of setup, you probably want Postfix for the email and Courier is a very popular POP server. SAMBA can handle authentication and printing for you, although on a reduced basis compared to a windows AD server. 

Check out the customization tips & tricks forum - it's a bunch of howtos and most of what you ask is on the first page.

---

### Post by MJN on 2006-01-27
I would recommend using IMAP as opposed to POP if you have any intent to access your mail remotely (e.g. via a webmail interface or even a normal mail client) as the former will allow full and seamless 'synchronised' views of your inbox along with any folder you may have (sent items, archives etc). It's also good for low-bandwidth access (e.g. PDA/phone) as you don't have to download every message from the server (and can even just get the headers if you like).
 
Mathew

---

