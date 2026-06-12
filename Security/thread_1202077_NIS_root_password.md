---
title: "NIS root password"
date: 2009-07-01
forum: Security
---

### Post by altmiket on 2009-07-01
hey all,

i'm trying to configure ubuntu server 9.04 to use an NIS root password, but also to allow me to use netgroups to only allow certain NIS users to log on.

typically, this is done by setting up /etc/nsswitch.conf as:

[FONT="Courier New"]passwd:         compat
group:          compat
shadow:         compat[/FONT]

and putting a +user at the end of the /etc/passwd file, and a + at the beginning of the /etc/shadow file  (at least that's how it works on solaris)

however if i do that, i get locked out of the box, and no passwords, NIS or local, for root or other users work.  the + at the top of the /etc/shadow file appears to screw things up.

i've also tried setting the shadow line in /etc/nsswitch.conf to be "nis files" in hopes that that would have root pick up the NIS root password, but no dice.

i can't use 'nis files' in the passwd line in /etc/nsswitch.conf, as that will let all NIS users log into this box.  i need to use compat.

but for some reason, i can't get this working.  any ideas?

---

### Post by scorp123 on 2009-07-02
Sorry to say so, but nobody is using NIS anymore. NIS is soooo horribly outdated and has sooo many security holes.

Why not use LDAP?

[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

---

### Post by altmiket on 2009-07-02
because LDAP sucks.

---

### Post by scorp123 on 2009-07-02
> **altmiket said:**
> because LDAP sucks. Very informative. :lolflag: Can you present any reasons for your statement or is this all just based on a gut feeling of your's?

But to use your own wording: NIS sucks even more. In a NIS environment every user can download the complete password hash tables of all the other user accounts. And that stuff is only encrypted with DES, so: happy password-cracking.

Hence why nobody is using NIS anymore. LDAP is much much faster and safer.

As for restricting users from logging in ... Why not work with the SSHD config file? You can use statements such as "DenyUsers" and "DenyGroups" and thus prevent them from logging in via SSH.

See here:
[http://www.security.ku.edu/docs/doc-viewer.jsp?id=26](http://www.security.ku.edu/docs/doc-viewer.jsp?id=26)
[http://www.cyberciti.biz/tips/openssh-deny-or-restrict-access-to-users-and-groups.html](http://www.cyberciti.biz/tips/openssh-deny-or-restrict-access-to-users-and-groups.html)

NIS vs. LDAP aside -- I suppose this is what you want?

---

### Post by altmiket on 2009-07-03
i'm not going to go into the years of BS i've gone through with LDAP vs NIS, and why i prefer NIS over LDAP - mainly because that's completely off topic from my question, which i need a resolution to.

i need to use an NIS root password, along with 'compat' so i can use netgroups at work.

this appears to be broken in ubuntu.

---

### Post by scorp123 on 2009-07-03
> **altmiket said:**
>  this appears to be broken in ubuntu. Hmmm ... you could open a bug report if you really think that this stuff is broken. Maybe it would at least cause someone to answer your question on how this is supposed to be configured on Ubuntu ... ?

---

