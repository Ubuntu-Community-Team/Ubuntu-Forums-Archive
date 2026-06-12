---
title: "Problem with filter on Apache2"
date: 2012-08-11
forum: Server Platforms
---

### Post by rockroll20 on 2012-08-11
I'm running Ubuntu 12.04 LTS, Appache 2.2.22.

vmod_security and mod_evasive are not  instaled. I have a problem with installing Moodle and configuring LDAP.

Later I find the simplest html form handling if I for input, type in: **,ou=a** it doesn't execute php code but return error 404 message (file not found). All other inputs work just fine, even if I type in **,ou=** it works properly, but if I add any character (not just a) after **=** it returns 404 error message.

  This is case only on this server.

Now I made the simplest (only html, I have not assigned it with php)  form like this:  <form> name: <input type="text" name="name" /><br /> </form>  And if I type in anything else it works, I mean, in URL I see that the  value has been assigned, but if I type this ",ou=a" the connection to  server is interrupted 
  
In html file input type is "text". 

In apache log there is: [11/Aug/2012:22:31:23 +0200] "GET /testp.htm HTTP/1.1" 200 430 "-" "Mozilla/5.0 (Windows NT 6.1; rv:14.0) Gecko/20100101 Firefox/14.0.1"  

There is nothing in error log. 

Help would be appreciated.

---

### Post by rockroll20 on 2012-08-12
Problem wasn't in Apache2. 

VPN connection is filtered and that cause the problem.

---

