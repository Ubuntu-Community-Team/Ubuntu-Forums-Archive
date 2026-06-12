---
title: "could someone paste to a reply a screenshot of GUFW with samba/win netbios correctly"
date: 2010-06-07
forum: Security
---

### Post by swimfish on 2010-06-07
could someone paste to a reply a screenshot of GUFW with samba/win netbios correctly configured

I just need access to and from windows machines on our lan and may wish to share files via samba.  

i'd rather use a firewall behind my router, if any of you are using firestarter, i'd consider using that as an alternative.  

screenshots is what i'm hoping for i use GUFW.  i really appreciate the help, and i'm sure it would help others as well.

---

### Post by bodhi.zazen on 2010-06-07
> **swimfish said:**
> could someone paste to a reply a screenshot of GUFW with samba/win netbios correctly configured

I just need access to and from windows machines on our lan and may wish to share files via samba.  

i'd rather use a firewall behind my router, if any of you are using firestarter, i'd consider using that as an alternative.  

screenshots is what i'm hoping for i use GUFW.  i really appreciate the help, and i'm sure it would help others as well.

Is your Ubuntu machine going to be a server or client ?

---

### Post by swimfish on 2010-06-07
strictly a client

i may share a couple of samba folders on our internal lan.  

i may also share my printer with the house.

---

### Post by bodhi.zazen on 2010-06-07
Neither ufw or gufw (same application) should be blocking your samb clinet, are you sure UFW is the problem ?

The ports used by samba (server) are:

UDP ports 137 and 138 

TCP  ports 139 and 445 

So allow connections on those 4 ports. I believe clients need less ports, but honestly I am not sure which ones (my  guess is UDP ports 137 and 138 ).

---

