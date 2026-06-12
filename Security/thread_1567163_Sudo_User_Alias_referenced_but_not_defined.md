---
title: "Sudo User_Alias referenced but not defined"
date: 2010-09-03
forum: Security
---

### Post by djcrash1981 on 2010-09-03
Good day.

I'm trying to configure my SUDO entries, for this I've added the next lines:

[I]User_List ADM = username

ADM     ALL=(ALL) NOPASSWD: ALL[/I]

When I close and save the file sends me the following warning

[I]>>> /etc/sudoers: syntax error near line 12 <<<
visudo: Warning: User_Alias `ADM' referenced but not defined
What now?
[/I]

Someone can explain to me what is wrong???

Thanks in advance.

Regards.

---

### Post by bodhi.zazen on 2010-09-03
Your syntax is off.

Syntax is covered in 

[http://www.sudo.ws/sudo/sudoers.man.html](http://www.sudo.ws/sudo/sudoers.man.html)

IMO you should review the above link ;)

---

