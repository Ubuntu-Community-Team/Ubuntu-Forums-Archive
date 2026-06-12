---
title: "Cascading Login System Helps Gurus With Security, Ease of Mind for Newbs"
date: 2007-12-09
forum: Ubuntu Brainstorm
---

### Post by nfox on 2007-12-09
I would like to have an (preferably GUI) easy option for auto-login to a desktop only authenticating (entering the user password) upon access to the user's folder while preserving the user/sudo user role.

**Intent:**
I run Flux on Xubuntu through KDE and it takes me 4 seconds after logging in to be fully up and running. I know we can auto login to an account but I want it protected with the same sudo permissions, etc. as if it were not auto logging in. The computer should be able to run predefined apps until access to the home folder or protected scripts are called. Then a password allows the user access for the rest of the session. This is not a root account but my actual profile.

**SUMMARY:** 
[LIST]
[*]]GUI/BASH that lets user choose login session (KDM,XDM,GDM,etc.)
[*]Configures auto-login for a new account
[*]Upon requiring access to home directory, etc. ask a password that grants access per session
[*]Still requires sudo for protected access
[/LIST]

This is all so that if someone steals my laptop, they too can log in within seconds but not be able to acces my files until authenticated for the session (like the login part of the window manager). This would allow users to delay a login while able to take full advantage of the speed of our creation without imposing speed bumps due to a specific way to run things.


Let me know if this seems feasible. I would love to add it to the next (highly anticipated) version of Ubuntu. I'm not sure where to start but I can get things going. Anyone interested in helping me to develop this will make things all the better.

---

### Post by daengbo on 2007-12-10
So, you want the person who steals your laptop to be able to use it but not access your files? That's a little odd, but ...

The only way to keep anyone from using your files is to encrypt the /home partition. Other than that, if I stole your laptop, I could just pull out your drive and mount it on my machine  in order to get access.

If you don't want to encrypt, you should just create a guest account and have autologin to that account. Make sure the file mask for your home doesn't allow all users to read your files. You can just fast-user switch to your account when you need it.

---

