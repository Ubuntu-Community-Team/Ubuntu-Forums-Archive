---
title: "Super User lost"
date: 2008-01-07
forum: Server Platforms
---

### Post by mjmogo on 2008-01-07
Hello all,

I came into work tonight and found that my Ubuntu FTP server no longer thinks that I am a super user. I didn't really think this would be all that big of a deal, and I only had one super user created, and now I can't seem to gain access to root through this account.

Does anyone have any suggestions about getting this back? While I know that I can reformat and all, I just don't know if I want to actually do that just yet.


Thanks for your assistance.


Mike McGonagle

---

### Post by koenn on 2008-01-07
reboot and select 'recovery mode' from the grub menu
then, 
```

useradd -G admin <your account name>

```
this adds your account to the admin group, giving it sudo rights

you can also edit the sudoers file directly, with
```

visudo

```

That's the easy part. The tricky part is: finding out how your account suddenly got demoted. I'd worry, if I were you. .

---

### Post by mjmogo on 2008-01-07
> **koenn said:**
> reboot and select 'recovery mode' from the grub menu
then, 
```

useradd -G admin <your account name>

```
this adds your account to the admin group, giving it sudo rights

you can also edit the sudoers file directly, with
```

visudo

```

That's the easy part. The tricky part is: finding out how your account suddenly got demoted. I'd worry, if I were you. .

Thank you, Koenn, I found this stuff on another site, as I wanted to get this fixed ASAP!!! And yes, I am a little worried about what is going on. There are  only 2 other people who I work with who MIGHT have the ability, and I don't think either of them are vindictive at all...

So, I guess it is time to start looking through logs, as this is an FTP server, and that might be trouble...

Thank you again, I appreciate your help very much.

---

### Post by koenn on 2008-01-08
> as this is an FTP server, and that might be trouble...
my thoughts exactly

---

