---
title: "Configuring Samba to /var/www/"
date: 2009-09-02
forum: Server Platforms
---

### Post by redyouch on 2009-09-02
I am quite the noob when it comes to Linux, so I am reaching out to you guys for some help. I am in the process of setting up an Apache server, which is not causing me a problem. BUT, I want to make /var/www/ accessible as a network share so I can quickly and easily manage the website from my Windows box. I am able to create the share using Samba and see it when I browse to the server, but I cannot open it.
 
I have changed the smb.conf file with the following entry:
```

[web]
comment = webserver share
read only = no
locking = no
path = /var/web/
valid users = chris
browsable = yes

```
 
I have used smbpasswd to set a password for user "chris". I also use the same username/password combo for the main user account.
 
I have also run chown on /var/www/ configuring "chris" as the owner.
 
I am not the most well-versed with linux permissions by themselves, let alone with Samba, so I was hoping you guys could lead me in the right direction.

---

### Post by TwiceOver on 2009-09-02
Just to be sure you are pointing samba at /var/www and not /var/web right?

Also, did you restart samba services after making the changes?

---

### Post by redyouch on 2009-09-02
> **TwiceOver said:**
> Just to be sure you are pointing samba at /var/www and not /var/web right?
 
Also, did you restart samba services after making the changes?
 
That fixed it.  Thanks.
 
*facepalm*

---

