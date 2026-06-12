---
title: "Domain Migration Advice"
date: 2009-02-17
forum: Server Platforms
---

### Post by faustcoder on 2009-02-17
I'm in the process of rebuilding a network and would like some advice on migration strategies. Currently 60-70 users are on a Windows Workgroup w/ no central authentication. Since the users are running Windows platforms I plan on using Active Directory, however a great amount of internal servers and a few workstations run Ubuntu.

I know that items such as Likewise exists but the 'free' versions I feel would add extra complexity. 

Basically I want a way to use AD for my users because nothing can manage Windows users better, as far as desktop policies go. But what about my Ubuntu servers? The only thing I want to have w/ them is mainly permissions and possibly 'SSO', (Single Sign On).

Would using Samba be enough or should I look into Likewise?

---

### Post by faustcoder on 2009-02-18
Hmmm maybe I can tie OpenLDAP in w/ AD. There has to be a simple way to have linux and windows in the same environment.

---

### Post by rickyjones on 2009-02-18
> **faustcoder said:**
> I'm in the process of rebuilding a network and would like some advice on migration strategies. Currently 60-70 users are on a Windows Workgroup w/ no central authentication. Since the users are running Windows platforms I plan on using Active Directory, however a great amount of internal servers and a few workstations run Ubuntu.

I know that items such as Likewise exists but the 'free' versions I feel would add extra complexity. 

Basically I want a way to use AD for my users because nothing can manage Windows users better, as far as desktop policies go. But what about my Ubuntu servers? The only thing I want to have w/ them is mainly permissions and possibly 'SSO', (Single Sign On).

Would using Samba be enough or should I look into Likewise?

I recommend a canned approach to enable authentication for the Linux servers. My workplace invested in Centrify - works great against our Active Directory infrastructure. 

The free-ish version like Likewise should do what you want without issue.

Thanks,
Richard

---

### Post by faustcoder on 2009-02-18
Thanks, I'll take a look. Never heard of Centrify, but if you've managed to get it working then at least I know it works. I'll update ASAP.

---

