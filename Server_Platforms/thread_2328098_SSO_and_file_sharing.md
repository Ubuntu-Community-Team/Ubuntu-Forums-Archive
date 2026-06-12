---
title: "SSO and file sharing"
date: 2016-06-17
forum: Server Platforms
---

### Post by Sam_Williams on 2016-06-17
Hello,

I'm after a bit of advice here, rather than with a question about a particular difficulty - I hope this is OK?

What I would like to accomplish in a SOHO office setting is synchronisation of user accounts between machines, and automatic mounting of a shared file system with the correct user permissions whenever someone logs in.

 I have three users, one server and five laptops to contend with: the server is running Ubuntu server and the laptops run either Ubuntu desktop (16.10), Win 10 (home) or Win 8 (home) as required to support various software. 

I was thinking about setting up the server as a samba AD DC until I read the Wiki which strongly advises against serving file shares from the Domain Controller. As I only have one server this seems to rule that out (unless I run two VMs on the server?). Also, reading up I don't think the home versions of Win10 / Win8 will play well with active directory. I think that NT workgroups are about as sophisticated as they will handle.

So, will setting up the server as a NT4 PDC and file server (on one box) work well? I know this solution is hardly cutting edge, but think that it would satisfy my needs for now. Or are there better alternatives, such as NFS / LDAP? 

Sorry if this is a bit rambling, I need to work out the best tools to achieve my goal before I can start to go into the detail of setting them up.

Thanks in advance,

Sam

---

### Post by TheFu on 2016-06-17
Check out SSSD. [https://wiki.ubuntu.com/Enterprise/Authentication/sssd](https://wiki.ubuntu.com/Enterprise/Authentication/sssd)
If I were starting all over again, I'd begin with FreeIPA as an authentication VM and work out from there.

Think you are stuck with home versions of Windows. Need Pro or higher.

---

### Post by Sam_Williams on 2016-06-17
Thanks, will take a look at sssd.

---

