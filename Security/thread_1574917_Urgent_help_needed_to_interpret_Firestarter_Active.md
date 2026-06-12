---
title: "Urgent help needed to interpret Firestarter Active Connections"
date: 2010-09-14
forum: Security
---

### Post by Hagler on 2010-09-14
Hello all.  I've been using the Firestarter gui for the past few months, without any problems, and I'm currently using Firefox 3.6.9.  The Firestarter Blocked Events list reports quite a few different hits every day, but as they are reported as blocked I haven't really worried about them.  I have however tried to keep a sharp eye on the Active Connections list Firestarter produces, and as I only generally use the same 3 or 4 websites, I've become familiar with the hostnames listed as Active Connections ie 1e.100.net for Google, and others such as the ones used by my IP and the usual pages I visit.  There will usually be between 4 and 8 listings in the Active Connections area, when 2 or 3 windows are  open.

My problem is that this evening Firestarter has begun to display many Active Connections (more than 20) when just going to my home page (Google).  I'm very worried as most of them come from a numbered prefix followed by ash2.facebook.com, and the rest from numbered prefixes followed by intermap.com, amazonaws.com and mojofarm.snv.mediaplex.com.  There seem to be other entries which are "greyed out" and upon clicking Lookup Hostnames these will just disappear.  I have never seen these entries before and they don't correspond to the sites I visit.

I'm not very IT literate and I've tried to be as security conscious as I possibly can be - it was the main reason I left the Windows environment, and I'd like to ask if it's likely that my system is under threat.  Does the Active Connections list mean that my system is definately sharing information with these other hostnames that have previously not been linked to my system?  If so, then how might this problem have arisen, and what can I do to sort it out.

Thank you, and I apologize for the long post and my lack of knowledge.

---

### Post by CharlesA on 2010-09-15
Looking at logs makes you paranoid. A blocked connection, is a blocked connection.

Also: Firestarter is no longer in development, so you'd be better off using something like ufw/gufw.

---

### Post by Hagler on 2010-09-15
Thanks for your reply.  As I say I'm not concerned with Blocked Connections list, it is the ***Active Connections*** list that worry me.  I would be very grateful for any help.

Thanks

---

### Post by cariboo on 2010-09-15
I haven't looked at all of them, but they look like ad servers.

Firestarter, isn't meant to be run all the time, the correct usage is to start it up, set your firewall rules, and them shut it down. You only need to run it once, after that it will restart automagically in the background every time you reboot.

If you are worried about security, keep in mind that Firestarter runs as root, which could possibly leave your system at risk.

---

