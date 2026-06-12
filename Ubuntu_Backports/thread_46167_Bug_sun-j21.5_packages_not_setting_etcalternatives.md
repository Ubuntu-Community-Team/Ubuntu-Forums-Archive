---
title: "Bug?: sun-j2*1.5 packages not setting /etc/alternatives/mozilla-javaplugin.so"
date: 2005-07-03
forum: Ubuntu Backports
---

### Post by Jaime on 2005-07-03
Hi.

I'm trying to get the java (applet) plugin working under hoary, and I've tried both sun-j2re1.5 (version 1.5.0+update02) and sun-j2sdk1.5 (version 1.5.0+update03), but neither seem to work - the url "about:plugins" in both epiphany and firefox do not list java anywhere.

I've had a look around and as far as I can tell, I think it's a problem with the link:
/etc/alternatives/mozilla-javaplugin.so
In both case (i.e. with both the j2re and the j2sdk), this file is a link  to:
/usr/lib/j2sdk1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
but this file never exists.

Please excuse me: I don't understand how update-alternatives really works, and I'm not sure that libjavaplugin_oji.so really is the plugin itself: could someone please tell me whether this is a bug (or am I missing some part of the procedure to set up the applet plugin)?

Many thanks,

Jaime :-)

---

