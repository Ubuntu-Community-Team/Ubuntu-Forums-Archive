---
title: "Apache2 suexec issue"
date: 2008-05-24
forum: Server Platforms
---

### Post by tymewyse on 2008-05-24
I have been using my LAMP server with Webmin and have installed Virtualmin which has made life easier until now. I have found that Virtualmin requires the Apache mod suexec to be turned on. The only problem is that I can not get the cgi-bin to work under the virtual public_html folders since suexec is hard coded to run from the default location.
 While researching this I find that I am not the only one with this. Aside from recompiling Apache, suexec etc. is there a simple workaround that anyone has found so users can use their .cgi, .pl scripts.

---

### Post by bradmurmz on 2008-06-12
I am having the same problem... I guess the only solution that I have found is to recompile apache configuring suexec with a docroot of "/home/"

A simple work around would be very nice! I would hate to have to recompile apache manually every time I wanted to update it...

---

### Post by etorvinen on 2009-01-29
I also have the same issue.

also another question

how do you make php run as CGI in the default LAMP installation

---

