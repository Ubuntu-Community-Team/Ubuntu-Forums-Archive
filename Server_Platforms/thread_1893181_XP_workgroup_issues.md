---
title: "XP workgroup issues"
date: 2011-12-09
forum: Server Platforms
---

### Post by kolofan on 2011-12-09
Hello, i am very new to ubuntu. i have installed samba and i can now see my windows XP shared folder on the ubuntu machine. 

However, i can't see the ubuntu machine on my xp machine. Any ideas? 

They are both in the same workgroup. 

I followed the guide here which got me this far. [http://www.liberiangeek.net/2011/04/connect-ubuntu-11-04-and-windows-systems-via-sambapart-one/](http://www.liberiangeek.net/2011/04/connect-ubuntu-11-04-and-windows-systems-via-sambapart-one/) 

Appreciate any help! 
BMC

---

### Post by arrrghhh on 2011-12-09
> **kolofan said:**
> Hello, i am very new to ubuntu. i have installed samba and i can now see my windows XP shared folder on the ubuntu machine. 

However, i can't see the ubuntu machine on my xp machine. Any ideas? 

They are both in the same workgroup. 

I followed the guide here which got me this far. [http://www.liberiangeek.net/2011/04/connect-ubuntu-11-04-and-windows-systems-via-sambapart-one/](http://www.liberiangeek.net/2011/04/connect-ubuntu-11-04-and-windows-systems-via-sambapart-one/) 

Appreciate any help! 
BMC

You have samba installed on Ubuntu, but have you setup any shares?

Are you running Ubuntu Server or Ubuntu Desktop?  Honestly samba is much easier to setup on the Desktop edition, but it's not impossible on the Server edition.  Just requires a little more effort/thought.

---

### Post by kolofan on 2011-12-09
i am running the desktop version. 
i did setup a shared folder but i'm not sure if i did it correctly.

---

### Post by arrrghhh on 2011-12-09
> **kolofan said:**
> i am running the desktop version. 
i did setup a shared folder but i'm not sure if i did it correctly.

This is the Server edition section.

I can try to point you in the right direction, but you might want to post a thread in the correct section.

[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)

Might be a little complex for your use.

[http://tinyhacker.com/hacks/share-files-between-ubuntu-windows-7-computers/](http://tinyhacker.com/hacks/share-files-between-ubuntu-windows-7-computers/)

That one should be a little easier to understand, and the concept should be the same for WinXP.

---

### Post by kolofan on 2011-12-09
thanks for the help, have now managed to get it into 'my network places' so i'm happy. 

Cheers

---

