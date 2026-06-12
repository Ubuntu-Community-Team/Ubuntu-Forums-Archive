---
title: "Apache and Posix ACLs"
date: 2009-09-24
forum: Server Platforms
---

### Post by wiggsfly on 2009-09-24
We have our ACLs set up like we want, and they work fine except for when Apache creates a file (upload, etc) in which case they are not applied. Any suggestions?

---

### Post by t3r0 on 2009-09-24
> **wiggsfly said:**
> We have our ACLs set up like we want, and they work fine except for when Apache creates a file (upload, etc) in which case they are not applied. Any suggestions?

Hi,

Apache doesn't create any files ;) (except for logs and pids) so I think you mean files created for example by php script? 

If this is the case, they will always be owned by the same user that the script is run as. So if you run just plain php the files created by it will be owned by www-data (ubuntu default apache user). 

This is a common (security) issue with many shared hosting environments and running php via mod_suphp ([http://www.suphp.org](http://www.suphp.org)) is highly recommended. 

suPHP will run the php script with the permissions of their owners so any file created by that process is then owned by the same user.

So take a look at suPHP if it solves your problem :) 


- Tero

---

### Post by wiggsfly on 2009-09-24
You got me on the PHP part (frustration leads to mixed words). Will suPHP apply the default ACL however?

---

### Post by t3r0 on 2009-09-24
> **wiggsfly said:**
> You got me on the PHP part (frustration leads to mixed words). Will suPHP apply the default ACL however?

suPHP will check to owner of the php file and run the script as that user. And any filesystem changes made will be like as that user made them. So yes, any lower level filesystem permissions will apply.


- Tero

---

### Post by wiggsfly on 2009-09-24
Sounds perfect. Thanks!

---

