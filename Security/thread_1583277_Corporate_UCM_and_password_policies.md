---
title: "Corporate UCM and password policies"
date: 2010-09-27
forum: Security
---

### Post by Tsu on 2010-09-27
Corporate UCM and password policies

Hi there,

I am currently reviewing what it means to switch over to Ubuntu and I have the following scenario. Which I hope Ubuntu has a solution for.

If I was to switch all the windows servers over to an Ubuntu solution. I already understand that file servers/ mail servers and resources can be provided Ubuntu 10.04.

The issue comes with the user accounts access and control. In a windows environment, I have a domain with sub domain sites. I am able to control passwords in each site separately thought Active directory. So at this point your saying what is the problem?

I need the instructions on how to setup an LDAP server so that I can control access rights to different services located on different servers.

Example 1.

I have 5 mail servers and on the HR side, I have 2 email administrators.

I wish to provide them access to only the relevant resources centrally. With out having to add users to different users repeatedly. For example, if I wanted to grant the two administrators access to all five servers. As I understand it, I would have to create the same user on every server and add a public key on every server, as well as set the administration rights for that user on each server individually.

I want to be capable of doing this like I am in a windows environment from some sort of domain controller equivalent.

Things that I must be able to do, manage users public keys on each server centrally. Add and remove user’s access to each server centrally. Finite control on what each user can do on each server. (i.e., add them to the sudo group or any other group for specific servers/server class I specify). 

To a lesser extent of requirement, I also need to be able to inform users they have to change there password every 3 months from when they change it. As well as enforce password rules, such as characters complication.

Is there such a solution within Ubuntu? Or Linux as a whole?

I hope you can help.

---

### Post by bodhi.zazen on 2010-09-27
You should look at Kerberos and LDAP.

[http://www.opinsys.fi/en/setting-up-openldap-on-ubuntu-10-04-alpha2](http://www.opinsys.fi/en/setting-up-openldap-on-ubuntu-10-04-alpha2)

[https://help.ubuntu.com/10.04/serverguide/C/kerberos-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/kerberos-ldap.html)

For password requirements you want to look at PAM

[https://help.ubuntu.com/10.04/serverguide/C/user-management.html](https://help.ubuntu.com/10.04/serverguide/C/user-management.html)

---

### Post by Tsu on 2010-09-28
Hi bodhi.zazen,

Thank you for the information you linked.

I have a few questions as I viewed the documentation linked below.

[https://help.ubuntu.com/10.04/serverguide/C/user-management.html](https://help.ubuntu.com/10.04/serverguide/C/user-management.html)

PAM system – This seams to be per server, and can not be controlled centrally from what I have read.

PAM also does not take effect if I use SSH keys which is a major requirement.

LDAP, Kerberos infrastructure does not allow you to manage SSH keys on multiple servers.

---

### Post by bodhi.zazen on 2010-09-28
You can use Kerberos to authenticate to a ssh server, so with Kerberos you would not need ssh keys.

From your posts I think Kerberos is what you want, with or without LDAP (probably with).

---

