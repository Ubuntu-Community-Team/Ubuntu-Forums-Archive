---
title: "Quick DJBdns setup using Ubuntu's .deb packages"
date: 2008-11-21
forum: Server Platforms
---

### Post by docplastic on 2008-11-21
**This procedure is deprecated**, please one of the procedures described bellow:

# install from ubuntu .deb packages
"**HowTo Install DJBdns with cache read/write to/from hard disk, in Ubuntu Linux**": [http://ubuntuforums.org/showthread.php?t=1445122]("http://ubuntuforums.org/showthread.php?t=1445122")

# install from the original sources:
"**HowTo Install a DJBdns cache in Ubuntu Linux**": [http://ubuntuforums.org/showthread.php?t=956864]("http://ubuntuforums.org/showthread.php?t=956864")

---

### Post by Mach1US on 2008-12-14
I have gotten DJBDNS up and running on 8.04 , i have copied Data file from tiny installation on another server( gentoo) which was configured about 5 years ago by admin which is no longer with us and to my surprise everything started working fine until i tried to update the data file with new entry .
I have issued make command like before but now any of new entries are just unreachable (everything else is working fine) from any machine using this new DNS.
But the same entry  upon make on the old server (running Gentoo) is resolving without a problem.
I did refreshed the cache , even did entire reboot but still nothing.

       Any ideas ???

---

### Post by docplastic on 2008-12-15
> **Mach1US said:**
> ...until i tried to update the data file with new entry.

Did you use the add-* utilities to do that or, did you edit the data file directly? Try both. If both fail then most probably you have non standard instructions in your original text data file.

> **Mach1US said:**
> But the same entry  upon make on the old server (running Gentoo) is resolving without a problem.

Perhaps the Gentoo's tinydns code or makefile were customized to have extra functionalities. If that was the case it could be producing a standard cdb data file from non standard text in the data file.


J.

---

### Post by Mach1US on 2008-12-18
> **docplastic said:**
> Did you use the add-* utilities to do that or, did you edit the data file directly? Try both. If both fail then most probably you have non standard instructions in your original text data file.

Perhaps the Gentoo's tinydns code or makefile were customized to have extra functionalities. If that was the case it could be producing a standard cdb data file from non standard text in the data file.


J.


Thanks for quick replay and thanks for this howto.

I have wiped out my previous install which was based on this site:
[http://www.howtoforge.com/perfect-djbdns-setup-on-ubuntu8.04-amd64](http://www.howtoforge.com/perfect-djbdns-setup-on-ubuntu8.04-amd64)
And followed your howto.
In step 10.Install tinydns it says :
```
# start tinydns (after a 5 second delay)
sudo ln -sf /etc/tinydns /etc/service
```
Just wondering if this shouldn't be :
```
# 
sudo ln -sf /etc/tinydns /service
```
Also when you say :
```
# subsitute IP for your server name IP (as in 123.123.123.123)
sudo tinydns-conf tinydns dnslog /etc/tinydns IP
```
Is this the ip of interface of a server on which dnscache is resideing or ip of tinydns ?
 (dnscache ip vs tinydns ip) ?

.

---

### Post by Mach1US on 2008-12-20
Latest update.
I have finally finished configuring it but the same problem occurred.
After install i'v copied the data file and issued make.
Everything was working exactly as expected unit i'v attempted to add yet another entry.
Any new entry are being ignored and tiny only refers to original data.cdb disregarding any of the new entries.
Every time i do any changes to data file and issue make i do svc -t /service/dnscahe , svc -t /service/tinydns .
Any ideas as to what could be holding binary data file or where ?

---

### Post by quonsar on 2009-02-28
Thanks for this! Now I'm no longer dependent on Comcast's often flaky resolvers!

---

### Post by docplastic on 2009-03-03
> **quonsar said:**
> Thanks for this! Now I'm no longer dependent on Comcast's often flaky resolvers!

You are welcome.

I would rather use the procedure described at <http://ubuntuforums.org/showthread.php?t=956864>. It avoids some troubles of the current Ubuntu's .deb package.

J.

---

