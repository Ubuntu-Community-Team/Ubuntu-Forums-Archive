---
title: "apt-get update won't update"
date: 2010-10-17
forum: Server Platforms
---

### Post by disconap on 2010-10-17
Hey--sorry if this is a repeated thread, I searched a couple variants and didn't find anything.  So when I run apt-get update, it runs like normal but nothing updates.  No errors, just nothing happens other than checking the repositories.  I DID run aptitude safe-upgrade at one point, could that have caused a conflict?  I know aptitude and apt-get don't necessarily play well, but neither will update my system currently...

---

### Post by K. Hendrik on 2010-10-17
perhaps you're just already up to date.
Or are you trying to upgrade from an lts like 10.04 to 10.10 (didn't really get you're problem) then you would have to enable Normal Releases in the Software Sources application like this:
[https://help.ubuntu.com/community/MaverickUpgrades]("https://help.ubuntu.com/community/MaverickUpgrades")

---

### Post by disconap on 2010-10-17
No, there are definitely updates (running 9.01)--the login screen says:


28 packages can be updated.
13 updates are security updates.


This has increased several times over the past couple weeks.  Have tried rebooting and running it in any way I can think of and still nothing.  It's not a huge deal, though I'm concerned about the security ones obviously...

---

### Post by ian dobson on 2010-10-17
> **disconap said:**
> No, there are definitely updates (running 9.01)--the login screen says:


28 packages can be updated.
13 updates are security updates.


This has increased several times over the past couple weeks.  Have tried rebooting and running it in any way I can think of and still nothing.  It's not a huge deal, though I'm concerned about the security ones obviously...

Hi,

Ignore these messages, there seems to be a bug in motd which doesn't update this information. Wait for the next update, hopefully that'll fix it.

Regards
Ian Dobson

---

### Post by disconap on 2010-10-17
Edit:  Ah, thanks Ian, that's EXTREMELY relieving.  :)

Also, I am very tired, running 10.04.

---

