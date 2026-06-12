---
title: "Samba LDAP Drives"
date: 2009-05-28
forum: Server Platforms
---

### Post by richard2137 on 2009-05-28
I am using samba as a PDC with ldap so that my clients can authenicate to my domain and login. I have the H: drive set to there home directory. I was wondering if I could make more drives so that I can make a global share. (ex. P: for public). When the user is loged in it showes there H: dirve and the P: drive. How would I go about doing that? Any help is useful... Thanks! Also when I create new smbldap users they can't change there password? Even though sambaCan..Passwd is defined. Any information for that is awesome!

---

### Post by ghen on 2009-05-28
to make sure the users always have access (like if they delete/unmount the network drive) its best to set them up in a login script that runs every time they log into the machine. You could do that in the startup menu of every xp machine or one time in samba.

here's the first google link for "samba login script"
[http://oreilly.com/catalog/samba/chapter/book/ch06_06.html](http://oreilly.com/catalog/samba/chapter/book/ch06_06.html)

I'm not to that point in my implementation so I don't have any pointers yet sorry :)


by the way, what version of Ubuntu are you using?

---

