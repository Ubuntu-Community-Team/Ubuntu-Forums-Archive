---
title: "FreeRadius radclient: no response from server for ID 51 socket 3"
date: 2011-01-05
forum: Server Platforms
---

### Post by sentinelace on 2011-01-05
I am getting this error after I run this command:
 
radtest testuser password localhost 1812 testing123

I have searched over and over with nothing.  Any help appreciated.

---

### Post by terazen on 2011-01-07
Have you tried using 127.0.0.1 instead of "localhost"?  Do you see any good information when running freeradius with "freeradius -X"?

---

### Post by sentinelace on 2011-01-12
Yes that worked.  My problem is, I think I need more of an updated guide since it's different in Ubuntu 10.10.  Is there anything current out there on freeradius?

---

### Post by terazen on 2011-01-12
The best information is between the deployingradius.com site and the files that come with freeradius I've found.  

If you run `apt-cache search freeradius` you can see how some of the packages are organized.  Like for ldap you'll need freeradius-ldap etc.

---

### Post by sentinelace on 2011-01-13
there are no guides on that site.  Any other advice on how to get this running?

---

