---
title: "Remote account/pass management in Linux"
date: 2014-07-28
forum: Security
---

### Post by vperaino on 2014-07-28
I work as a grunt-level techie for a small-ish company and we have a LOT of user accounts to manage. Typically we just assign a computer to a particular person and set their account up as such, so whenever we hire or fire someone, we have to go through the whole process of removing their account from their computer and setting up a new account for someone else - which is a major pain in the butt, especially since a lot of our work happens one state over where I can't just walk into the next office over and do what I need to do. 

I've been trying to find out if there's a way that I can configure peoples' accounts and desktop environments from a central server here at the corporate office. We already have a server running for reverse tunneling so the "infrastructure" is there so to speak. I'd come across something about LDAP being ideal for this kind of situation but LDAP seems to be really complicated and I'm not quite at "pick up on any piece of software out there" level of competency yet. 

Any suggestions? 

I'd have to be able to pre-set panel items, user preferences (like startup applications), and browser bookmarks. Otherwise I might as well just keep doing what I'm doing now.

---

### Post by TheFu on 2014-07-29
LDAP is ideal for this, but the interfaces into it suck for the most part.  I cheat and use Zimbra's LDAP for centralized user management.  People on CentOS or RHEL can easily use FreeIPA, but it hasn't/can't be ported to Debian/Ubuntu.  Another option, I suppose is to setup a Samba4 "domain" - like AD.  I know next to nothing about that, sorry.

So - in the old days we would use NIS and NIS+ to manage users, global machine settings and other things like that. These days, the poor security of NIS and fact that NIS+ is only for Solaris sorta leaves us stuck on that side.

Ok - so what are you (and I) to do in our Ubuntu-loving environments?  I do not have a definitive answer, but I can guess.
* Setup LDAP and use that for centralized authentication and user management. "passwords" - I'd love to learn about a nice, Ubuntu-friendly, non-Java LDAP management tool. If you do not already run Zimbra, it is overkill just for this - as it is a complete replacement for MS-Exchange. All our other servers/apps use the Zimbra LDAP for authentication.
* Setup something like Ansible to maintain settings on groups of workstations.  Should take about 30 minutes to get started. They have a great [ansible quick-start video]("http://docs.ansible.com/quickstart.html") that explains much. This can be made to setup users, settings for servers and HOMEs easily.  Ansible is the easiest tool like Puppet, chef, cfengine, salt, rex or writing your own bash management scripts.

That's all I got. Sorry it isn't better.

I look forward to reading the way that other people have solved this too. I suspect a hybrid solution is best in the end.

---

### Post by vperaino on 2014-07-29
Thanks, this is pretty helpful. :) I'll give all these suggestions a shot and see what works best for me.

---

