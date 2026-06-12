---
title: "Apache2 userd module and ~/username"
date: 2009-02-16
forum: Server Platforms
---

### Post by Phlee on 2009-02-16
Hi all!
  I've just enabled the Apache2 userdir module.  I was wondering if anyone knew how to change the /~username to /username.  I would like to get rid of the '~' as it won't fit my current needs.  Any help would be greatly appricated as I've been all over the apache site as well as different forums.  I'm running Ubuntu 8.10.

  One solution is I've managed to add sym links to /var/www/username but I would like to steer clear of that if possible.  

Thanks in advance!

---

### Post by Phlee on 2009-02-16
Aww *bump!*

Maybe to help claify:

-----------------------------------------------------------------
It's a straight forward install of Apache2 MySQL and PHP. It's for our customers.

In the past we have setup apache with the userdir mod to host customer webpages with [www.example.com/~customer](www.example.com/~customer). Since then I've been wanting to deploy a better url theme so to speak. I.E
users.example.com/customer.

I've seen it done in the past many times. The new versions of Apache2.conf are slimed down and I can't find the examples online. The internal directory structure has "/home/user/public_html" Which translates to [www.example.com/~customer](www.example.com/~customer).

---

### Post by Phlee on 2009-02-16
Anyone?  *Bump*

---

### Post by Phlee on 2009-02-17
Blah:(  *Bump* again

---

### Post by rrll1977 on 2009-05-18
Hi all,

Has anybody ever worked with mod_rewrite and mod_userdir on LAMPP?

It appears that mod_rewrite doesn't work with the user's websites (located on /home/user/public_html), although it appears to work fine with the home server websites (on /opt/lampp/htdocs)

Regards

---

