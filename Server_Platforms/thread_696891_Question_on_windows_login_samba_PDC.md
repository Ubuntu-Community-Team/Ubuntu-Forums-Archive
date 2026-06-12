---
title: "Question on windows login samba PDC?"
date: 2008-02-14
forum: Server Platforms
---

### Post by cpthk on 2008-02-14
I have a samba server, and many windows based client. I realized that if windows successfully log in samba once. It will then remember the username and password. So next time even though I completely shutdown the samba server, windows can still login using that username and password. It's just it couldn't retrieve the user profile, but it can still log in and surf internet or anything. I tried to restart windows, but still.  Is it my samba server setting problem or windows setting? I trying to have windows check username and password each time.

---

### Post by bmorency on 2008-02-14
> **cpthk said:**
> I have a samba server, and many windows based client. I realized that if windows successfully log in samba once. It will then remember the username and password. So next time even though I completely shutdown the samba server, windows can still login using that username and password. It's just it couldn't retrieve the user profile, but it can still log in and surf internet or anything. I tried to restart windows, but still.  Is it my samba server setting problem or windows setting? I trying to have windows check username and password each time.

I am pretty sure that is the way windows works. once you login windows saves the username and password locally incase the server is not available.  it will do that with a windows server also. you can unplug the network cable and it will still login.

---

### Post by astrotech226 on 2008-02-14
Something doesn't make sense.  If you log out and a user types in a correct username and password, shouldn't hey get access to those things?  If they didn't know the user name or password, they couldn't get a desktop, even with the network cable unplugged.

Is this an older version of windows or something XP home where there no true domain support?

---

### Post by bmorency on 2008-02-14
> **astrotech226 said:**
> Something doesn't make sense.  If you log out and a user types in a correct username and password, shouldn't hey get access to those things?  If they didn't know the user name or password, they couldn't get a desktop, even with the network cable unplugged.

Is this an older version of windows or something XP home where there no true domain support?

the user needs to login the first time so windows can save the username and password.  if the user logs out and types the username or password wrong if the server is not available it will not login. but if they type it in right they can login but they would not have access to the server if it is unavailable.

xp home has no domain support.

---

### Post by cpthk on 2008-02-14
> **bmorency said:**
> the user needs to login the first time so windows can save the username and password.  if the user logs out and types the username or password wrong if the server is not available it will not login. but if they type it in right they can login but they would not have access to the server if it is unavailable.

Yes, exactly as bmorency said. You will need to have the right username and password for the first time for windows to memorize it. But I was wondering what if on the samba server side that I changed the password??

---

### Post by bmorency on 2008-02-14
> **cpthk said:**
> Yes, exactly as bmorency said. You will need to have the right username and password for the first time for windows to memorize it. But I was wondering what if on the samba server side that I changed the password??

if you change the password on the samba server and the network is not available windows will only use the old password if you have not connected to the samba server since you changed it.

---

