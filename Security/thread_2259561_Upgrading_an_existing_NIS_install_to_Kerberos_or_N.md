---
title: "Upgrading an existing NIS install to Kerberos or NIS+"
date: 2015-01-05
forum: Security
---

### Post by acpuck1 on 2015-01-05
Hey everyone,

I've been looking through documentation for NIS+ and Kerberos and thought I would ask to hear from people with experience. I have an existing NIS login system with 100+ users. Obviously, I need to upgrade my security. Which of these two would work best to keep my users intact? Or will I have to start over and recreate all these users?

Thanks in advance!

---

### Post by TheFu on 2015-01-05
I thought NIS+ servers were for Solaris only. Is there an NIS+ server for linux?

There's a thread here (in the last 2 months) with a developed script on using LDAP+Kerberos+NFS to handle the things that NIS did. Think it is in the Server sub-forum.

---

### Post by schragge on 2015-01-05
You can forget about NIS+. The Linux NIS+ client is unmaintained since like ten years or so. Last time I successfully used it was in Debian Etch around 2008. I coudn't make it work in Debian Lenny and migrated my infrastructure to LDAP then. LDAP, with or without Kerberos, is your only viable option by now. You may find [this page]("https://wiki.debian.org/LDAP/Kerberos") on Debian Wiki useful.

@**TheFu**: No there never was a NIS+ server for Linux, only NIS+ client.

---

### Post by acpuck1 on 2015-01-06
Thank you both for the quick replies! When setting up Kerberos on my server, I assume I will have to recreate all the users. I cannot find any way to port them from NIS to Kerberos. Am I correct in this assumption?

---

### Post by TheFu on 2015-01-06
> **acpuck1 said:**
> Thank you both for the quick replies! When setting up Kerberos on my server, I assume I will have to recreate all the users. I cannot find any way to port them from NIS to Kerberos. Am I correct in this assumption?

You need to go from NIS to LDAP.  Kerberos provides system-to-system authentication, right?

---

### Post by acpuck1 on 2015-01-06
Well, I don't know much about it so I could be wrong. The specific vulnerability I am trying to fix is if a root user connected to my nis server, creates a user with the same uid as me, they get my file permissions. I think that I need Kerberos for this fix. LDAP is more for authenticating particular machines, right?

---

### Post by TheFu on 2015-01-06
> **acpuck1 said:**
> Well, I don't know much about it so I could be wrong. The specific vulnerability I am trying to fix is if a root user connected to my nis server, creates a user with the same uid as me, they get my file permissions. I think that I need Kerberos for this fix. LDAP is more for authenticating particular machines, right?

Uh - no. You are backwards. [https://en.wikipedia.org/wiki/Kerberos_%28protocol%29](https://en.wikipedia.org/wiki/Kerberos_%28protocol%29)

NIS is fairly trivial to hack. Bad idea to have used it since around the late-1990s.

---

### Post by acpuck1 on 2015-01-07
I agree, it was a bad idea. I wish I knew better when I was building this system.

Looks like I'm setting up LDAP on my server then when students are gone for the Summer I am rebuilding with Kerberos ASAP. LDAP should fix my multiple users same uid problem, right?

---

### Post by TheFu on 2015-01-07
> **acpuck1 said:**
> I agree, it was a bad idea. I wish I knew better when I was building this system.

Looks like I'm setting up LDAP on my server then when students are gone for the Summer I am rebuilding with Kerberos ASAP. LDAP should fix my multiple users same uid problem, right?

Why do the same work twice?  LDAP+Kerberos isn't THAT hard and without Kerberos, I don't know that you are any more secure than NIS.

---

### Post by acpuck1 on 2015-01-07
That's a good point. My only worry is losing the NIS users I have and having to recreate since there is such a large number.

BTW: Thank for taking the time to help someone new to Linux admin.

---

### Post by TheFu on 2015-01-07
> **acpuck1 said:**
> That's a good point. My only worry is losing the NIS users I have and having to recreate since there is such a large number.

BTW: Thank for taking the time to help someone new to Linux admin.

Sorry if I'm confused.  How does creating 10 or 20,000 LDAP accounts differ?  Same thing. Just more information for the script.  Don't you dare do it manually. Script it.  Once the script is done, it is done. No need to re-invent the wheel ever again.

---

### Post by acpuck1 on 2015-01-07
The only reason I don't want to recreate the user accounts is that the accounts are in use and I would rather not interrupt service more than reseting their passwords along with a day or two of down time.

---

