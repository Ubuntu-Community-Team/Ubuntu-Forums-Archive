---
title: "apple bug rant"
date: 2008-07-29
forum: The Cafe
---

### Post by decoherence on 2008-07-29
Hehehehe I love finding bugs in OS X Server... well, not really. As a school we do most of our upgrade during the summer. A few weeks ago I upgraded our 10.4 server to 10.5 and have had a good experience with it in general.

The other day a teacher came in to pick up his new MacBook, so I went in to Workgroup Manager (WGM... centralized network user management) to configure a roaming profile ('mobile account' in apple parlance) and found the user wasn't there!

In our LDAP server (provided by Novell's LDAP services for NDS) we have over 1200 user accounts. In Workgroup Manager only 904 show up.

I bashed my head against this for a while and the more I picked it apart, the stranger the behavior seemed. For instance, I tried setting the maximum number of LDAP users returned from the LDAP server (previously set to unlimited.) If I set it to 904, 500 or so accounts show up, if I set it to 905, 904 accounts show up. Confused yet? You can keep adjusting the LDAP server's maximum number of responses until WGM doesn't show anything (that's with a limit of 26 user records... if i put in 27 as the limit, WGM shows 26. So that one number difference on the LDAP server is causing 26 accounts to not show on OS X Server!)

This morning I installed 10.4 on a spare machine and configured it identically. Sure enough it recognized all the accounts without complaint. I have a bug report in to Apple which they've classified as a 'serious bug.' That's nice. But if I don't get a fix or a reasonable workaround, we'll be sticking with Tiger for the next school year.

I have a couple of theories on what might be happening. If I use the misbehaving server's command line to query the LDAP users, all the results are returned. Similarly, Workgroup Manager has an option to show the 'raw data' of the LDAP query. From this I can see that all of the result are returned.

Where it goes wrong is the nice, searchable list of users it generates (which also happens to be the ONLY way you can select a user to manage.) If I were to guess I would say the problem is either a buffer issue, in which case we'd probably hear more about it, or there is something odd with certain LDAP accounts that is causing Leopard to choke. If this is the case, whatever exception handling that was in Tiger may not be in Leopard, which is a more classical regression.

Ah, but it's closed source so I guess we'll never know!

Anyway, this was a long post. If you got all this way, thanks for bearing witness to my venting!

sean

---

### Post by billgoldberg on 2008-07-29
Some people are actually OSX server.

:lolflag:

---

