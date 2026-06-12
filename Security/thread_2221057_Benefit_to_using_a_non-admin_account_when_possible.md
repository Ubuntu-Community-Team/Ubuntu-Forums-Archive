---
title: "Benefit to using a non-admin account when possible?"
date: 2014-04-30
forum: Security
---

### Post by jon43 on 2014-04-30
So, I'm wondering if there is a security advantage to using an account without admin privileges for daily computing, while leaving a second account with a different password there for times you might need to be admin/sudo?
 
I know that Ubuntu/Linux is much different from Windows, in that an admin account doesn’t just walk around with admin access the entire time it’s logged in, but is there still some benefit here to be had? 

Thanks!

---

### Post by ian-weisser on 2014-04-30
Well, if you leave your logged-in system unsecured and walk away a lot, I can see some benefit.
If you need to ssh in to do user work instead of admin work, then I can see some benefit.
I just don't see *much* benefit.

---

### Post by buzzingrobot on 2014-04-30
That's the standard approach on Ubuntu and a number of other Linux distributions. Running as root, either temporarily via sudo in Ubuntu, or by just logging in as root on systems that enable that account,  allows you to change, move or delete any files on the system, whether you want to or not.  So, unless you are perfect, the root account is best approached as a tool to be leveraged when needed, not a place to settle down in.

As someone mentioned, if you are logged in as root and walk away, anyone with access can do anything they want to your machine, including rather easily wiping out all the files.

---

### Post by jon43 on 2014-04-30
I get why you would never log in with the "root" account. What I am talking about is loggin in with the first account you create on a new install- the "admin" account that can sudo to root level for commands. If you use a "non-admin" account, you can't even sudo to root p[FONT="Calibri"][COLOR=#000000]rivilege. [/COLOR][/FONT]

---

### Post by nothingspecial on 2014-04-30
If you have a password that people know or can guess for your admin account and walk away from it without logging out or locking it often,  then this is a good idea. Otherwise it doen't matter. That's kind of the whole idea of how it's set up.

---

### Post by Warren Hill on 2014-04-30
Providing you have set a reasonable password I don't see any point in having a separate admin and normal user account on systems like Ubuntu where **sudo** has been set up properly.  I certainly only ever use one user for my self and use **sudo** and **gksudo** as necessary when I need elevated privileges.

I do have a separate non-admin account on my Ubuntu laptop but that's for my daughter and I don't want her to be able to play with any setting or add/remove any software.  

I have another non-Ubuntu Linux box which needs me to be logged on as **root** in able perform admin tasks and I definitely have a separate user account for that.  It's just too easy to mess things up when logged in as **root**  especially if you are using a GUI.  It also means that everything I'm running as **root** as elevated privileges so I try to keep my time logged in as root to an absolute minimum.

Ubuntu even locks the root account, so you can't login as root - though this can be changed but I've never seen a reason why you would want to login as root on a system with sudo set up correctly.

---

### Post by HermanAB on 2014-05-01
Some distributions use completely separated user and root accounts by default and some use sudo.  It is also easy to change yourself to the way you prefer.  I prefer not using sudo, since it is yet another damned thing that can go wrong.

---

