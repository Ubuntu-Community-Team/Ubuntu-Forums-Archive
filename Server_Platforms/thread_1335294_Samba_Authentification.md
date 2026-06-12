---
title: "Samba Authentification"
date: 2009-11-23
forum: Server Platforms
---

### Post by TheGameAh on 2009-11-23
At my wit's end here.

Trying to setup samba.  File share is created.  The username exists in both the Linux OS and Samba.  The get the name/password prompt when trying to access the resource.  However, I simply cannot authenticate.  I'm guessing maybe it has something to do with it going across as DOMAIN\username instead of username.  But I can't confirm.  Can anyone offer tips here?  Nothing fancy at all.  Just a workgroup Samba box, no PDC or anything.

---

### Post by Denbert on 2009-11-23
> **TheGameAh said:**
> At my wit's end here.

Trying to setup samba.  File share is created.  The username exists in both the Linux OS and Samba.

Have you set the samba password with this code for e.g. tom?

```
sudo smbpasswd -a tom
```

---

### Post by ptn107 on 2009-11-23
What version of Ubuntu are you running?  Did you set up the share automatically via nautilus or manually via smb.conf (if so post smb.conf)?  Make sure the following packages are installed: samba, samba-common, samba-common-bin.  Is your firewall set to block samba?

---

### Post by TheGameAh on 2009-11-23
Yes, the user password has been set in samba.

Actually using webmin to setup.  Confirmed that the user exists in OS and in Samba.

I'll try to post smb.conf soon.

The server works if I set it basically to "public".  (Guest access with share level security).

It's only when I try to switch to user level that it doesn't seem to want to accept any users.

---

### Post by buntunoob on 2009-11-23
[SIZE=3][FONT=Times New Roman]I've had various problems with webmin this was one of them, I was able to set the share but couldn’t connect till I set user in samba, just as Denbert said. Another problem was I couldn’t set up jenzora after a webmin install, and I can’t add virtual host. I’m having to do it all manually (no big deal I am having to learn it.).[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]So..... im not Trusting webmin that much.:P[/FONT][/SIZE]

---

### Post by Denbert on 2009-11-24
> **buntunoob said:**
> ]So..... im not Trusting webmin that much.:P[/FONT][/SIZE]

I've been using webmin for years, and it has always done the job for me. remember to use the unix/samba password sync function.

---

