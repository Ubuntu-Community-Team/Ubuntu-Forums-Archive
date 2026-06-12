---
title: "Server 12.04 encrypted home + decrypt via Samba + dropbox"
date: 2014-10-15
forum: Server Platforms
---

### Post by darren14 on 2014-10-15
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]I have windows only users who login to their server home directories and I would now like to have these home directories encrypted so that the data is safe from physical theft... can these encrypted homes be automounted via SAMBA _ONLY_ login from windows?

One of these home directories is used for communal work, shared by SAMBA dictated by group membership. Will any automount via SAMBA work here in this case (when there is no exclipict user (only group members) who login?)

Finally each of the homes use dropbox for backing up - any issues here?

What I've tried:
The encrypted home option from the ubuntu server installation setup - I couldn't get encrypted home directory to automount via SAMBA login (not without first opening a session in say, Putty)

I've also tried encryptfs package installation and found that if I move dropbox into private folder - dropbox stops working... The moving the dropbox folder instructions/install I found online didn't help solve the issue[/TD]
[/TR]
[/TABLE]
I thought about trying full disk encryption then manually mounting a volume at boot, but, as I'm not always physically on site, I would no doubt get the call whenever the server reboots, or worse  - I'd have to pass on instructions and heck I'm still new to it all.

Just for info - the Server setup is mostly whatever the defaults are at install - as I say I'm new and haven't delved too deeply. Any help or thoughts would be greatly appreciated  :p

---

