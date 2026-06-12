---
title: "ltsp and qas from quest"
date: 2009-08-26
forum: Server Platforms
---

### Post by romulan on 2009-08-26
I'm currently working on a solution for an R&D department to use LTSP.
[URL="http://www.ltsp.org/%3Cbr"]
[/URL]What we want to be able to do its install a ubuntu 8.04 server with QAS to handle the ad accounts. And use thinclients to login with ad accounts to access the NFS areas (home/project)

First trial out of the box with ubuntu 8.04 and ltsp worked fine to boot a thinclient.

My second to just add the ltsp onto a working 8.04 qas installation did not work.
The thinclient locks down after you successfully logged in with your ad user account and password. You just get a black screen and mouse pointer.

After some googeling if found that that issue has to do with account handling.
So I was hoping that quest had done some testing regarding ltsp and maybe have some documentation regarding configuration.

Any type of information with be super.

qas = [http://www.quest.com/Authentication-Services/](http://www.quest.com/Authentication-Services/)
ltsp = [http://www.ltsp.org/](http://www.ltsp.org/)

//Erik

---

