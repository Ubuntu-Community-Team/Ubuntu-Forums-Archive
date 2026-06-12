---
title: "Does root need to be part of any groups?"
date: 2011-09-08
forum: Security
---

### Post by jwcalifo on 2011-09-08
Hello, I have two questions regarding group membership in Ubuntu.
 
I noticed that root is not a member of very many, if any, groups.  Is that because it doesn't need to be?  Will there be loopholes if I add root to the root group?  Or to the admin group?  or any others for that matter?  :confused:

I want to disallow the regular user account from being about to SUDO.  Do I just remove the user account from the ADMIN group?  Is there any harm in adding ROOT to the ADMIN group?  :confused:
 
Thank you very much everyone.  Ubuntu ROCKS!  :guitar:

---

### Post by sisco311 on 2011-09-08
Adding root to any group is pointless, because root can do anything regardless of file permissions. 

By default only users from the admin group are allowed to use sudo.

Please check out: [uhelp]community/RootSudo[/uhelp]

[thread=1132821]HowTO: Sudoers Configuration[/thread]

and

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by jwcalifo on 2011-09-08
Mmkay thanks for that. Did anyone else actually read both my questions? I need to know if removing the user from the admin group is all that I need to do to prevent that user from using sudo. Are there any other steps involved? 
 
Also, please don't point me to FAQs, I've read them. I'm preparing this computer for a school and I need to make sure it's secure so I don't get sued. Thank you.

---

### Post by sisco311 on 2011-09-08
> **jwcalifo said:**
> 
Also, please don't point me to FAQs, I've read them.


> **jwcalifo said:**
> Are there any other steps involved? 



Yes, you have to understand the them.

---

