---
title: "blocking sites"
date: 2008-05-09
forum: Security
---

### Post by Dude Guadalupe on 2008-05-09
I work at a hotel, and against my will, have been put in charge of keeping up with the guest computer. It is curently running XP and is loaded with viruses and spyware everytime time I come back from my two days off.

My boss has given me permission to use Linux, but I need to know if there is anyway to block certain sites since this is a public computer and kids are ussually around.

Is there a program, or is there a fuction already in OS?

---

### Post by cdenley on 2008-05-09
If you have certain domains in mind, the easy solution would be to add entries to your hosts file.
```

127.0.0.1 www.bad-domain.com

```
Anyone looking up [www.bad-domain.com](www.bad-domain.com) would be connecting to the local webserver, or get a "Failed To Connect" error if you're not running one. This solution would work on Linux, Windows, or Mac.

The hosts file is located at:
/etc/hosts

or for windows:
c:\windows\system32\drivers\etc\hosts

---

### Post by Dude Guadalupe on 2008-05-09
The thing is, so many people use this machine at many different times for many different things. It would take forever to track down all the different sites. Is there anything that can cover most  of it for me and I could pick up the rest myself?

---

### Post by hsweet on 2008-05-09
Thanks.. I'm going to use the last suggestion on my students..:)  Monday.

Another thing you can do is set up a white or black list fire-wall wise.  Firestarter makes that pretty simple.  ```
sudo apt-get install firestarter
```

You might also check out opendns.com  You can quickly set up a proxy server and block categories.

---

### Post by Dude Guadalupe on 2008-05-09
These look like good places to start. I think I'm going to try each one to see what happens.

---

### Post by brian_p on 2008-05-09
> **Dude Guadalupe said:**
> I work at a hotel, and against my will, have been put in charge of keeping up with the guest computer. It is curently running XP and is loaded with viruses and spyware everytime time I come back from my two days off.

My boss has given me permission to use Linux, but I need to know if there is anyway to block certain sites since this is a public computer and kids are ussually around.

Is there a program, or is there a fuction already in OS?

I've never used dansguardian but it is the package which always seems to be recommended for this sort task.

---

### Post by Monicker on 2008-05-10
> **brian_p said:**
> I've never used dansguardian but it is the package which always seems to be recommended for this sort task.

Yes, dansguardian would work well.  There are several free blacklists which can be loaded into it; they had links to them at the dansguardian web site the last time I checked.  Dansguardian can also filter based on keywords in the content of the page itself, and then block when a certain threshold of unwanted keywords is reached.  It has several predefined categories - violence, sex, drugs, etc.  Of course, you can also tweak those yourself, or create your own categories.  This give you the ability block unwanted sites even if the domain is not specifically blacklisted.

---

