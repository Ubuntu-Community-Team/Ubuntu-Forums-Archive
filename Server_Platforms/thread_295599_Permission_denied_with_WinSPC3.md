---
title: "Permission denied with WinSPC3"
date: 2006-11-08
forum: Server Platforms
---

### Post by brakmaren on 2006-11-08
Hi
Just got my LAMP (6.06) up and running. ssh through Putty works fine.
Would like to tranfer files to and from the server with WinSPC3.
But every time i try i get...
```
Permission denied.
Error code: 3
Error message from server: Permission denied
Request code: 3
```
I can't find a way to sudo in WinSPC3.
Can it be solved by adding myself to a group or something ?
Thank's

---

### Post by MJN on 2006-11-08
It's simply saying that the user you're logging in as doesn't have the permission to do what you're trying to do...

What is it you're trying to do? And what user are you logged in as?

If it's a case of doing something that only root can do (e.g. write to root-owned files) then you'll have to enable root access (i.e. give root a password using **sudo passwd root** however do bear in mind there that it doesn't have one enabled by default for security reasons - see the archives for discussions why). You may also need to configure sshd to allow root logins (**permitrootlogin yes**). Alternatively, if the files you need access to an specific (and non-system critical/relevant) then you could arrange the permissions on these files accordingly.

Before adopting any particular 'solution' it might be worth us exploring exactly what you're trying to do (and the context you're doing it in).

Mathew

---

### Post by brakmaren on 2006-11-09
Thank's MJN
I just want to transfer files to and from the www server to edit on another box.
i.e get - edit - put :)
I know i dont have permission. I just don't know the best (most secure) way to solve it. The box is exposed to www, so i woul'd not whant to just figure a solution out for my self.
And invite (badboy) by leaving the frontdoor open.
Still think that security is the hardest part to NOT ruin.

---

