---
title: "LDAP for integrated login for a website?"
date: 2007-12-27
forum: Server Platforms
---

### Post by AaronLS on 2007-12-27
I have noticed many website CMS's, forums, and other components offer LDAP integration.  This makes me think it is a way for multiple web applications to share the same user base, so that a visitor to my site can use all aspects of the site with the same username and password they created once.  (Instead of having one for the forums, and one for the bug tracking tool, etc.)

I'm having a little trouble determining if this is what LDAP is intended for though.  From it's description, it makes me think of Domain accounts on a Windows network.  I see lots of references to it being used for intranets.

Is LDAP only intended for intranets where the users are "trusted" or at the least somehow accountable?

Let's say I used LDAP on a WWW viewable site, and create a php self registration page(i.e. the classic create an account and verify by email), and have that create the entries in the LDAP.  By putting these "strangers" into LDAP, am I giving them any sort of privilaged access to my linux box?

---

### Post by rickyjones on 2007-12-27
> **AaronLS said:**
> 
Let's say I used LDAP on a WWW viewable site, and create a php self registration page(i.e. the classic create an account and verify by email), and have that create the entries in the LDAP.  By putting these "strangers" into LDAP, am I giving them any sort of privilaged access to my linux box?

Only if your Linux box is configured to authenticate against that exact same LDAP database.

-Richard

---

### Post by jtc on 2007-12-28
In simple terms you can look at a LDAP-server as a database in which you can use to store any information you'd like. By design it is generally a lot easier to read from LDAP then it is to write to it, therefor LDAP often used to store userinfo and other data which read a lot more then it is changed.

---

