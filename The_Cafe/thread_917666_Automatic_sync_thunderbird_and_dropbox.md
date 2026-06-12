---
title: "Automatic sync thunderbird and dropbox"
date: 2008-09-12
forum: The Cafe
---

### Post by Glenn Jones on 2008-09-12
Hi 

So I recently signed up for dropbox (check it out if you haven't already) the otherday so that I can sync my email mailboxes on both my laptop and desktop. The only problem with this is that I have to manually rsync my to the correct directories. I would like to automate this process whereby when I open Thunderbird it automatically gets the mailboxes from the dropbox and when I close Thunderbird the mailboxes sync back to dropbox.
I would also like the automation script to work when I use the Thunderbird icon. Any one have any ideas on how to do this? 

Cheers

---

### Post by hessiess on 2008-09-12
make a shell script like:

```
#! /bin/sh
rsync (whatever) #retreve mail
thunderbird # BASH will wait here until you exit thunderbird
rsync (whaever) # this line will run when you quit
```

and make the icon run this script instead of running thunderbird directly

---

### Post by wandman on 2008-10-29
Glenn,

Did you have much luck with this? I would be very interested to try out this solution to sync emails between two computers. I know that it is possible with FireFox but wondered if with Thunderbird the profile.ini file is maybe too big for it to work quickly? I mean if one had thousands of emails would dropbox be uploading and downloading a file that is a few hundred megabytes for example?

Hope someone can shed some light here.

---

### Post by Renée Jade on 2009-10-20
I'm bumping this thread because I would *really* like to know how to do this. Thunderbird is the bomb - best thing ever for keeping track of three email addresses. But I use four different computers on a regular basis so it would be great to be able to use thunderbird's syncing ability with dropbox's sharing ability. Any ideas? I have no experience with scripting but I've done some programming so I'm not scared of it.

Thanks.

---

