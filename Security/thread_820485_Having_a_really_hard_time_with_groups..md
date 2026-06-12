---
title: "Having a really hard time with groups."
date: 2008-06-06
forum: Security
---

### Post by Geran on 2008-06-06
Hi,

I've been trying to set up groups properly for use, but I can't seem to get it right. Here's an example of what I'll do to open up a folder to a group and not to any user.

```


sudo mkdir something

sudo addgroup entry

sudo usermod -aGenty privilegeduser

sudo chgrp entry something

sudo chmod 770 something


```

Should be good for privilegeduser and all others in group entry, right? Well, it still returns this error.

bash: cd: something/: Permission denied.

So where am I going wrong?

Also, how can I list what groups a user is in and what users are in a group?

My OS is Hardy Heron.

---

### Post by nunki on 2008-06-06
> **Geran said:**
> Hi,

I've been trying to set up groups properly for use, but I can't seem to get it right. Here's an example of what I'll do to open up a folder to a group and not to any user.

```


sudo mkdir something

sudo addgroup entry

sudo usermod -aGenty privilegeduser

sudo chgrp entry something

sudo chmod 770 something


```

Should be good for privilegeduser and all others in group entry, right? Well, it still returns this error.

bash: cd: something/: Permission denied.

So where am I going wrong?

Also, how can I list what groups a user is in and what users are in a group?

My OS is Hardy Heron.

?

---

### Post by sisco311 on 2008-06-06
> **Geran said:**
> Hi,

I've been trying to set up groups properly for use, but I can't seem to get it right. Here's an example of what I'll do to open up a folder to a group and not to any user.

```


sudo mkdir something

sudo addgroup entry

sudo usermod -aGenty privilegeduser

sudo chgrp entry something

sudo chmod 770 something


```Should be good for privilegeduser and all others in group entry, right? Well, it still returns this error.

bash: cd: something/: Permission denied.

So where am I going wrong?

Also, how can I list what groups a user is in and what users are in a group?

My OS is Hardy Heron.

In order the usermod command take effect you need to log out and log in.

Use:
```
id
id *username*
```or
```
groups
groups *username*
```to list the groups.

---

### Post by HalPomeranz on 2008-06-06
Also there's a typo in one of your commands:

```

sudo usermod -aGenty privilegeduser

```

Notice you typed "-aGenty" instead of "-aGentry" (dropped the 'r' in "entry").

---

### Post by sisco311 on 2008-06-06
The correct command is:
```
[FONT=monospace]s[/FONT]udo usermod -aG entry privilegeduser
```
or
```
sudo usermod -a -G entry privilegeduser
```
or
```
sudo addgroup privilegeduser entry
```

-a = append
-G = group
entry = the group
privilegeduser = the user

---

### Post by Geran on 2008-06-06
Thanks to all, I'll try that out.

---

