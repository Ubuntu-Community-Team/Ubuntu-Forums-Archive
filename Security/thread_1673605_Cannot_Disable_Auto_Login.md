---
title: "Cannot Disable Auto Login"
date: 2011-01-22
forum: Security
---

### Post by coronacolada on 2011-01-22
Greetings,

I have tried everything to disable automatic login from the login screen (gdm). I've changed my password, I've changed the settings in System -> Admin ->Login Screen, and I've edited /etc/gdm/custom.conf (gdm.conf doesn't exist, but I created it just in case!). 

No auto login is set up, but I can't get it to ask for my password. 

This is affecting my ability to switch sessions, as I can't switch sessions without clicking on my name in gdm, and because it's set to auto login, it just logs in without giving me the chance...

-tom

sic luceat lux

---

### Post by cariboo on 2011-01-22
You don't need /etc/gdm/custom.conf if you don't have auto-login set, so just remove it.

I don't have have a gdm.conf on either Maverick or Natty, so you might just as well remove it too

---

### Post by coronacolada on 2011-01-23
Done.

The problem persists, though.

---

### Post by Dave_L on 2011-01-23
There's also a setting (Ask / Don't Ask for Password on Login) in

System -> Admin -> Users and Groups

---

### Post by coronacolada on 2011-01-23
Bloody brilliant. I don't know how I kept missing that. Thank you.

---

### Post by redkirk on 2012-01-01
> **Dave_L said:**
> There's also a setting (Ask / Don't Ask for Password on Login) in

System -> Admin -> Users and Groups

This worked great for me! :P Thanks, Dave_L!

---

### Post by richgreene on 2012-04-01
I'm having a bizarre problem here which I have had no luck fixing...

I also set this "Don't ask for password" box from users-admin and now I get automatically into XBMC, which is what I wanted but now I can't change it back to a different session (like gnome-classic).

And I can't get to the users-admin tool anymore within XBMC, so I can't uncheck this box.

So in summary, I have 2 problems:

1) How did I get XMBC to be the default session?  It's not in the /etc/lightdm/lightdm.conf.  It keeps overwriting my ~/.dmrc file no matter what I put there!

2) How do I disable the autologin now?

Any help would be appreciated...  Thanks in advance.

---

### Post by richgreene on 2012-04-01
OK, solved my own problem.

Just created a new user using "adduser" from a shell (logged into server from another PC), and now I get the option to select user at startup.   Here, you can change the session to be used and then I could log in and turn off the "Don't ask for password" setting.

Hopefully this can help someone else who runs into the same issue..

---

