---
title: "Some clarifications regarding NOPASSWD in sudoers"
date: 2012-04-04
forum: Security
---

### Post by Luca Borrione on 2012-04-04
Hello,

I've made a little modification to my /etc/sudoers adding the following line at the bottom

```
%nopwd ALL=(ALL) NOPASSWD: /bin/mount
```

I want all members of the group nopwd to mount without inserting sudo password.

It's working fine, however I've some doubts, since this is the first time I'm using this solution :

1. Normally a user in order to use sudo must be listed in admin group, right? I thought that using NOPASSWD wouldn't meant to ignore this rule: in my head putting foo user under nopwd group only avoid foo the task of inserting the sudo password, but it must be included in the admin group as well in order to use sudo.
I made some tests and it seems to me that, once that foo is under nopwd, having it or not also under admin produces no difference: foo will use mount without having to insert the password. 
Is it correct?

2. Since I'm interested in letting nopwd users avoid inserting the sudo password only when I execute a bash script I made, I was wondering if there's some param I can add in /etc/sudoers in order to tell ubuntu to let nopwd users use sudo without having to insert the password only in this case (when mount is used inside that bash script) while they have to insert the password in all the other cases as normal.

Thank you
BTW: I'm on lubuntu oneiric

---

### Post by nothingspecial on 2012-04-07
*Thread moved to **Security Discussions**.*

---

### Post by dfreer on 2012-04-07
> **Luca Borrione said:**
> Hello,

I've made a little modification to my /etc/sudoers adding the following line at the bottom

```
%nopwd ALL=(ALL) NOPASSWD: /bin/mount
```

I want all members of the group nopwd to mount without inserting sudo password.

It's working fine, however I've some doubts, since this is the first time I'm using this solution :

1. Normally a user in order to use sudo must be listed in admin group, right? I thought that using NOPASSWD wouldn't meant to ignore this rule: in my head putting foo user under nopwd group only avoid foo the task of inserting the sudo password, but it must be included in the admin group as well in order to use sudo.
I made some tests and it seems to me that, once that foo is under nopwd, having it or not also under admin produces no difference: foo will use mount without having to insert the password. 
Is it correct?

2. Since I'm interested in letting nopwd users avoid inserting the sudo password only when I execute a bash script I made, I was wondering if there's some param I can add in /etc/sudoers in order to tell ubuntu to let nopwd users use sudo without having to insert the password only in this case (when mount is used inside that bash script) while they have to insert the password in all the other cases as normal.

Thank you
BTW: I'm on lubuntu oneiric

1. Sort of. The idea is that members of the group admin (some distros use the wheel group I believe), have the ability to use sudo after authenticating themselves with their own password, and have unrestricted access to the system after authenticating. It isn't the ability to use sudo, it's more of a permissions to do things WITH sudo. Any user can *use* sudo, but if they are not part of any groups or have no permissions within the sudoer file, then they can't do anything with it. Hopefully that makes sense.

If you add a user to group nopwd, and set your sudoers file to allow them to mount drives without a password, that is all they will be able to do with sudo. Any other attempts will result in the same message that other unprivileged users get.

If you then also add them to the admin group, they will have two sets of permissions: 1, the ability to mount drives without needing a password, and 2, the ability to do ANYTHING as long as they authenticate themselves with their own password first.

I would not advise putting the user in both groups, unless you just want to avoid annoying password prompts.

2. You might be wanting to use the setuid and setgid bits. It's a bit confusing to explain what they do, but it is what allows your unprivileged user the ability to run ifconfig for example. That script performs some functions that require root privileges, so they have set the setuid/setgid bit to allow anyone with the ability to execute the file the ability to run it as root. I am doing a horrible job explaining it, and there is definitely some security concerns when using setuid or setgid.

---

