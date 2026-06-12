---
title: "Win xp to Samba  .. winxp wont shut up..."
date: 2008-07-12
forum: Server Platforms
---

### Post by spuncut on 2008-07-12
Logged on to windows xp as useraa, I try to access userbb's homefolder on the Samba. I wil then be met with a login sign, where I give the credentials og useraa, and of course I won't get admittance because I'am trying to reach the homefolder of useraa with the credentials of userbb....?!??!

Windows 2000 does not tell which user actual is logged on to the windows and therefore it is possible to access any homefolder om the Samba...

Any way to make winxp shut up or to tell Samba not to listen to any windows rubbish..??

---

### Post by spuncut on 2008-07-14
Anyone..?

---

### Post by freebeer on 2008-07-14
You might want to post up your samba configuration so people can have a look at how you've set it up.

I'm a little unclear by what you mean by "won't shut up".  (I presume others who've read this are, too).

---

### Post by JordanCB on 2008-07-14
> Logged on to windows xp as useraa, I try to access userbb's homefolder on the Samba. I wil then be met with a login sign, where I give the credentials og useraa, and of course I won't get admittance because I'am trying to reach the homefolder of useraa with the credentials of userbb....?!??!

That looks backwards.. .. but please post your /etc/samba/smb.conf so we can see your security settings and share settings.  Then we might be able to tell you a little more.   Something with you user security is more than likely off.

---

### Post by spuncut on 2008-07-15
I've found a soulution :
[http://www.linuxquestions.org/questions/linux-server-73/windows-to-samba-share..only-with-the-windows-account-655369/#post3214515](http://www.linuxquestions.org/questions/linux-server-73/windows-to-samba-share..only-with-the-windows-account-655369/#post3214515)

---

