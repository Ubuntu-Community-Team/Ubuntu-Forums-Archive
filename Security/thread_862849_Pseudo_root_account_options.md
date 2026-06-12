---
title: "Pseudo root account options?"
date: 2008-07-17
forum: Security
---

### Post by tuproxy on 2008-07-17
I want to create a more secure computer and would like to know if it is possible to create an account that is "almost" root. I don't want them to be able to get access to certain folders but I want them to be able to do upgrades and make some config modifications. Is there something like a "junior-root" account:)

Also, is there a way to change "root" to another name to increase security?  

Basically what options do I have in modifying the superuser account?

Thanks

---

### Post by hyper_ch on 2008-07-18
[http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/sudo.htm](http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/sudo.htm)

---

### Post by lisati on 2008-07-18
Nice play on words with the thread title.....

---

### Post by tuproxy on 2008-07-18
You like that?:)

> **lisati said:**
> Nice play on words with the thread title.....

---

### Post by tuproxy on 2008-07-18
> **hyper_ch said:**
> [http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/sudo.htm](http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/sudo.htm)

This is very close to what I'm looking for. Maybe I can explain it a little better.  Can I set up privileges for certain commands with ACL's?  Like if I only wanted root and one other user to be able to run nmap and tcpdump how do I do that?  do I make a group and put that user in a group or do I just grant individual access through ACL's?

---

### Post by Oldsoldier2003 on 2008-07-20
> **tuproxy said:**
> This is very close to what I'm looking for. Maybe I can explain it a little better.  Can I set up privileges for certain commands with ACL's?  Like if I only wanted root and one other user to be able to run nmap and tcpdump how do I do that?  do I make a group and put that user in a group or do I just grant individual access through ACL's?

Edit /etc/sudoers and give that user or group access to the commands.

```
sudo visudo
```


see [uhelp]/community/Sudoers[/uhelp]

---

