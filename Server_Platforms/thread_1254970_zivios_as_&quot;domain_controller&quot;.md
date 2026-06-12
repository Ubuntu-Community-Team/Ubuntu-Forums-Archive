---
title: "zivios as &quot;domain controller&quot;"
date: 2009-08-31
forum: Server Platforms
---

### Post by Tutigan on 2009-08-31
Hi guys!

I work in a services organisation as a techie in the technology & integration department... Recently a client of ours decided that their few semi-networked PC's needed a boost, as well as their network. Immediately my boss suggested a windoze small business server and upgrade of all their PC's...
The client however, wants to convert their PC's to Ubuntu (only two or three PC's are still windoze... their staff are eager for the change!).
It was then put to me to find something like a domain controller...

I found zivios, which is toted as a domain controller replacement, but am wondering if anyone has used it and if they have any suggestion/compliments/complaints/warnings about it???

---

### Post by Tutigan on 2009-09-01
Has no-one had anything to do with zivios?

---

### Post by frk2 on 2009-12-03
> **Tutigan said:**
> Has no-one had anything to do with zivios?

You want to use it as a Windows AD replacement?  You can - however the samba stuff is still a bit crude

---

### Post by kewlrichie on 2009-12-04
You can make a simple NT based PDC using samba3 there are alot of guides out there it is also pretty easy to do using eBox. Check howtoforge.com for that guide. There is also samba4 which is a windows 2000 style AD Domain controller. I'm not sure what versions they are up to but check the samba4 wiki page there is a howto on there. Also google samba4 ubuntu 9.04 and there is also a guide. I think I am going to do a simple NT based auth using ubuntu ebox solution there is also a way to inforce some NT group policy but it will have to be preconfigured on a windows box first. Let me know of your interested and I will try and digg up some links. Off the top of my head I think it's from opensourcehowto.org

---

