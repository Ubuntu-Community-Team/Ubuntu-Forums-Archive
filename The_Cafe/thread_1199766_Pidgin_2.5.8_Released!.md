---
title: "Pidgin 2.5.8 Released!"
date: 2009-06-29
forum: The Cafe
---

### Post by Kosimo on 2009-06-29
[www.pidgin.im](www.pidgin.im)

Changelog:

>     * ICQ
          o Fix misparsing a web message as an SMS message. (Yuriy Kaminskiy) 

    * MSN
          o Increase NS command history size to prevent crashes on buddy lists that have a lot of buddies on other networks like Yahoo! 

    * MySpace
          o Accounts with empty buddy lists are now properly marked as connected.
          o Fix receiving messages from users of MySpace IM's web client. 

    * Yahoo
          o Fixed phantom online buddies. They should now properly disappear when signing out.
          o Fixed the crashes some users were seeing with cn.scs.msg.yahoo.com in 2.5.7.
          o Fixed compiling on systems with glib 2.4.x or older.
          o Fixed an issue with file transfers. This may not resolve all issues, but it should resolve at least some of the most common ones.
          o The pager server will automatically update to scsa.msg.yahoo.com if the user empties the field or if it is scs.msg.yahoo.com. This should ease the pain of transition to the new login method. 

    * XMPP
          o Fix an incompatibility betweeen Prosody and libpurple clients. 

---

### Post by kevdog on 2009-06-29
Hmm not a lot of features that interest me in the new release.  I wonder how the beta voice and video test build is doing???

---

### Post by kc3 on 2009-06-29
Pidgin seems to have everything except one VERY basic feature, mass messaging lol, I could never get it, idk, it's been a while though

---

### Post by kevdog on 2009-06-29
Mass messaging as in group messaging??  There is a purple plugin for this -- its deactivated by default.  You need to compile the purple plugin from source and specifically turn on the feature when running ./configure -- but the feature is there!!1

---

### Post by Georgia boy on 2009-06-29
I just upgraded to 2.5.7 so that I could be able to sign in to the Yahoo account and not have it dump on me all the time. With having done that will I have the fixes to the file transfer problem that I'm having? 
See this following post I created:

[http://ubuntuforums.org/showthread.php?t=1199336&highlight=pidgin+files](http://ubuntuforums.org/showthread.php?t=1199336&highlight=pidgin+files)

Will I have the fixes automatically done to my 2.5.7 or will it upgrade to 2.5.8 instead? I mean, looks like they would send an update to correct the system that you are using instead of having to go to another version.

Thanks 

Tom

---

### Post by kc3 on 2009-06-29
Is there really? lol, well at the time I was using it on Windows at work, did use it for a bit on Linux though until I got aMSN up and running

> **kevdog said:**
> Mass messaging as in group messaging??  There is a purple plugin for this -- its deactivated by default.  You need to compile the purple plugin from source and specifically turn on the feature when running ./configure -- but the feature is there!!1

---

