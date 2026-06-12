---
title: "Make ssh accept only public keys, not password?"
date: 2009-07-30
forum: Security
---

### Post by SoftwareExplorer on 2009-07-30
Is there a way to make ssh only allow public keys for authentication, and not accept passwords?

---

### Post by Dr Small on 2009-07-30
> **SoftwareExplorer said:**
> Is there a way to make ssh only allow public keys for authentication, and not accept passwords?
Edit /etc/ssh/sshd_config and change "PasswordAuthentication" from "yes" to "no"

---

### Post by SoftwareExplorer on 2009-07-30
Do I need to take the # away from the start of the line?
I also set PermitRootLogin to no, that's a sane thing to do right?

By the way, thanks.

---

### Post by bodhi.zazen on 2009-07-31
See also : [AdvancedOpenSSH - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AdvancedOpenSSH")

---

### Post by The Cog on 2009-07-31
> **SoftwareExplorer said:**
> Do I need to take the # away from the start of the line?
Yes you do.
> I also set PermitRootLogin to no, that's a sane thing to do right?Yes it is. Although Ubuntu ships with the root account login disabled, so the question is moot unless you re-enable root login yourself.

---

### Post by bodhi.zazen on 2009-07-31
> **The Cog said:**
> Although Ubuntu ships with the root account login disabled, so the question is moot unless you re-enable root login yourself.

+1

This simple fact is mis-understood by people who state you need to change the default settings in Ubuntu to disallow root logins. 

Since the root account is locked root can not log in with a password.

---

### Post by SoftwareExplorer on 2009-07-31
Thanks for the help, I got it to do what I want. I figured that you couldn't log in to root through ssh if root has no password, but while I was there, what could it hurt to turn it off?

---

### Post by bodhi.zazen on 2009-07-31
> **SoftwareExplorer said:**
> Thanks for the help, I got it to do what I want. I figured that you couldn't log in to root through ssh if root has no password, but while I was there, what could it hurt to turn it off?

It will not hurt.

If it is on root can log in via other means, typically (ssh) keys.

---

### Post by SoftwareExplorer on 2009-07-31
I changed the port also, so when I ssh in, I need to do [email]user@websitename.us.to[/email]:port? Or is it some other format?

Edit:The reason I am asking is I can't try it yet, I locked myself out because I need to set up port forwarding.

---

### Post by bodhi.zazen on 2009-07-31
ssh -p 1234 user@server

See man ssh ;)

---

### Post by The Cog on 2009-08-01
> **bodhi.zazen said:**
> It will not hurt.

If it is on root can log in via other means, typically (ssh) keys.

Doh! That never even crossed my mind. There are times when that could be useful.

---

### Post by SoftwareExplorer on 2009-08-02
Thanks for the help, though you can go on rambling between yourselves if you wish...

---

