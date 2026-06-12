---
title: "web server user permissions"
date: 2009-03-14
forum: Server Platforms
---

### Post by lunaz on 2009-03-14
i've had my own webserver @ home for quite a while, used only by me for testing stuff. i have no experience in sharing it with others.

i want to give my friend a user account on my web server. how do i allow for this w/o him having full access to my server's filesystem?

i use sftp over ssh (filezilla) so i have no ftp server setup. i made a test user & it was able to even get into my samba shares & download things.

not really even sure what to search for :P

---

### Post by nelskurian on 2009-03-14
Are you talking about ACL's...You can set ACl's for various permission settings.You can set up a user with only limited access using that.Or setup a group whicha has limited priveleges with ACL's..

---

### Post by hyper_ch on 2009-03-14
lunaz: 

you have already setup openssh-server it seems.

If it's just one friend then

(1) install mysecureshell
(2) add your friend as system user
(3) change his shell to mysecureshell
(4) alter his home to the location you want
(5) edit the mysecureshell config in such a way that shell access is forbidden and that he can't leave his home.

---

### Post by nelskurian on 2009-03-14
Thanks for the information..:D

---

### Post by daboroe on 2009-03-14
> **hyper_ch said:**
> lunaz: 

you have already setup openssh-server it seems.

If it's just one friend then

> 
(1) install mysecureshell

This is just sudo apt-get install mysecureshell?

[QUOTE]
(5) edit the mysecureshell config in such a way that shell access is forbidden and that he can't leave his home.This is just done with permissions?

If i am wrong sorry had to get up early for blood work this morning and tired as heck and wanted to check the forums.

thanks

---

### Post by hyper_ch on 2009-03-14
> **daboroe said:**
> This is just sudo apt-get install mysecureshell?
Did you try it?

> **daboroe said:**
> This is just done with permissions?
--> (5) edit the mysecureshell config in such a way that shell access is forbidden and that he can't leave his home.

---

### Post by daboroe on 2009-03-14
i run things in a vm. i dont have my hard drive with my vms since i am on spring break that is up on campus. 

i will try though.

---

### Post by lunaz on 2009-03-14
hm well i installed mysecureshell; but i cant configure it since there is no /etc/ssh/sftp_config

i was using this guide but with the latest version off sourceforge
[http://www.howtoforge.com/mysecureshell_sftp_debian_etch](http://www.howtoforge.com/mysecureshell_sftp_debian_etch)

---

### Post by hyper_ch on 2009-03-15
the sftp_config exists on my lenny server... haven't tried it on ubuntu... btw, you still use edgy?

---

### Post by lunaz on 2009-03-15
oops i forgot to update my profile :) i use intrepid or hardy :)

i updated the server to intrepid, will give that a try with ssh + chroot when i get time

---

