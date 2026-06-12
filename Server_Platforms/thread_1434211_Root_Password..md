---
title: "Root Password."
date: 2010-03-20
forum: Server Platforms
---

### Post by NiGhtMarEs0nWax on 2010-03-20
hey,

So i have a fresh install of the server edition of Karmic, i'm running the Xfce desktop.  


When I attempt to manage users and groups through the GUI, I am prompted for what I think is the root password, the reason I say this is because the account I am currently logged in has sudo privileges and it does not accept that password at all, but I read that by default the root account is 'locked,' (to be honest it was so long ago since I last installed Ubuntu I completely forgot if it is or isn't, my current desktop installation has su access)


is it asking for the root password? why doesn't my current user account password work if the root account is 'locked'? I can perform all other administrative tasks with sudo no problem.


the funny thing is, I have the exact same setup in a virtual machine, the same problem happens, except for some strange reason after changing the password on the **only** account (besides root), the password required to administer users and groups stayed the same after the change.  (at the time of installation I just put both the user and root password the same and now that it is setup), i'm now ready to change the passwords.  except now I read that the root account is locked by default, but this strange problem occurs.

i can't su at all.

---

### Post by jrssystemsnet on 2010-03-20
"The Ubuntu way" (actually, the Debian way, which Ubuntu inherits) is to eschew actually using the root account, including su-ing to root.  Typically, there IS no root password.

When a GUI app asks you for a password, it's asking for *your* password.  *If you're a member of the admin group*, either gksudo (what GUI apps use) or sudo (what you use from the command line) will elevate you to root, with your *own* password (not root's, which generally doesn't exist, and sudo/gksudo don't want even if it DOES exist).

You may need to [get into single-user mode](http://www.noah.org/wiki/Single_User_Mode) to fix this.  Your /etc/sudoers (which MUST BE edited with visudo, not with a regular editor) should have a line that says ```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```, and your account should be a member of the admin group.  (**adduser yourname admin** will do the trick... from single-user mode.)

---

### Post by NiGhtMarEs0nWax on 2010-03-20
Thanks for the reply, i am aware of the difference bewteen the root account and being in the admin group.

the account i setup initially was set to be in the admin group, i have done administrative tasks with it using sudo. although, when i'm prompted for a password in users & groups, it does not accept my accounts password at all. the account is in the admin group, my sudoers file is up to scratch. hence why i can't explain what is going on.



like i said before, when i changed my password in my virtual machine, i could only use my old password when prompted at users and groups, even though i just changed it...   and on my host machine, none of the passwords i have set work at all, but i can run other administrative tasks no problem.

---

