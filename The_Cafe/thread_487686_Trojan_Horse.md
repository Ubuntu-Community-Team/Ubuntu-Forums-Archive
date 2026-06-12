---
title: "Trojan Horse?"
date: 2007-06-29
forum: The Cafe
---

### Post by @trophy on 2007-06-29
So, I've been wondering something for a while, and haven't seen it addressed anywhere else:

Since Novell made their deal with MS, the stated purpose of which was for interoperability between Windows and SLED, Novell almost certainly has access to official MS documentation of the latest versions of the SMB protocol, and can rewrite Samba using that information, thus making it magically work a whole lot better than it used to.  Since I doubt any distribution in their right mind would abandon Samba, that code (which would presumably *actually* infringe on MS's patents) would end up in ALL linux distros, and then MS would go "See?!  See?!  We told you Linux was infringing on our patents!!!" and sue corporate users of every distro other than SLED and Linspire.  From there it would be a simple matter of mopping up the remaining two Linux companies and calling it a day.  

At least, that's what I'd do if I were Microsoft.

So, a few questions:

[LIST]
[*]Has anybody seen anything unusually good coming out of Novell since the deal?
[*]If this is actually MS's plan, what should be our defense?  For instance, if Samba remains at GPL2 then GPL3 is of no help, because no distro is going to abandon Samba.  Nor will we have any indication that it even needs to be abandoned/forked/whatever, because it's not like the comments are going to say "*** This code here in an attempt to scuttle Linux.  Tee hee! ***"
[*]Or do we even need a defense?  Would "We liscensed these patents to Novell and they just gave them away to everybody!" even hold up in court?
[/LIST]

---

### Post by dca on 2007-06-29
OpenXML support in Novells' OpenOffice...
I think Samba will be the first to convert to GPLv3...
 
Corporations would NEVER be sued by MS.  Look at SCO...  Too many enterprise data centers consist of Unix, Linux, & MS.

---

### Post by Zzl1xndd on 2007-06-29
MS in the end doesn't wanna sue. To me there goal is simple and that is to use this divided in the Linux community to force the patent issue. What I mean is they will use the Linux community to try and have patent Law changed (becuase is MS does it them selves it looks bad) if it works then they no longer need to worry about being sued and wouldn't have to worry about Sun, IBM and so on who have a lot more patents then MS does.

---

### Post by @trophy on 2007-06-29
So if Samba benefits from this deal... and stays at GPL2, would you still use the new version?

---

### Post by saulgoode on 2007-06-29
Samba code is currently licensed under GPL 2 "or (at your option) any later version". This means that anyone can use a snapshot of its current release, make modifications, and release under the GPL 3. The likelihood is that the GPL 3 version would see more contributions than the original GPL 2 version. Over time the GPL 2 Samba would become less useful. 

The same effect would be seen by most GPL software released with the "any later version" clause in its licensing; particularly code where the copyrights were signed over to the FSF.

---

### Post by @trophy on 2007-06-29
Ok good.  So trying to inject some patent-infringing code into some part of Linux that we can't just drop and which would take a long time to rewrite isn't a viable attack option for MS?

---

