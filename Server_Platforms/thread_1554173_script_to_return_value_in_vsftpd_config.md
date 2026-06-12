---
title: "script to return value in vsftpd config?"
date: 2010-08-16
forum: Server Platforms
---

### Post by artheus on 2010-08-16
Hey!

I've been searching around for a way to add a value to an attribute of the /etc/vsftpd.conf by script.

Such as:

```

*/etc/vsftpd.conf*

local_root= /scripts/userpath.sh $USER

```

Thanks for any help!

//Artheus

---

### Post by artheus on 2010-08-18
I've been searching my a* off.. but I really can't find any answer to this.. Maybe it's my search keywords that are not optimal.

But I would really like help with this ASAP!

Thanks!

//Artheus

---

### Post by surfer on 2010-08-18
why not use sed?
```

$ sed 's/local_root=.*/local_root=your_desired_root/' /etc/vsftpd.conf 

```

---

### Post by artheus on 2010-08-18
**sed** is for replacing text in the config file by regexp, right?

What I want is that the local_root changes depending on the $USER that logs in. Some way maybe having the path-setting in a database or something.

So I would like to maybe write a script that will echo out a path depending on the username given. Or if there is some way of doing this with sed, I would really like to know how to do that.

Using sed. Would that mean that I would have to set up vsftpd to load a "seded" version of the vsftpd.conf each time a user logs in on ftp? Or how will I do this?

Cheers,
Artheus

---

### Post by surfer on 2010-08-18
hmmm. i don't think that what you have in mind will work: the config file is read when the vsftpd server is started. only then. it will not be reread when a user logs in; the server just keeps running.

---

### Post by artheus on 2010-08-18
Okay. That's what I thought.

And that is why I would like to assigt a script to return the local_root to vsftpd depending on the $USER.

Is that possible?

Cheers,
Artheus

---

### Post by surfer on 2010-08-18
```
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES

```

isn't that enough?

---

### Post by artheus on 2010-08-18
> **surfer said:**
> ```
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES

```

isn't that enough?

No, unfortunately not. As I am using a htpasswd file for authentication instead of local users, that is not enough. Cause from what I can see I can't make the htpasswd point to homedirectories?

Would be perfect if I could use the htpasswd file somewhat like this :

```

*auth.htpasswd*

user1:23Dsi3d9!:/var/ftpusers/user1
someotheruser:dfl23Ofe2E:/home/sam
root:dkl324/SJ3k:/mnt/hdd1/path/to/some/folder

```

Is there a way, without having to rewrite the source code?

Cheers,
Artheus

---

### Post by surfer on 2010-08-18
htaccess? can that be used with anything but a web server? sorry, i can't help there...

---

### Post by artheus on 2010-08-18
> **surfer said:**
> htaccess? can that be used with anything but a web server? sorry, i can't help there...

No. Not htaccess, but I'm using the htpasswd file to create users. Very smart way if there will be many users.

Fast tutorial :
[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)

But in the standard /etc/pam.d/vsftpd, does PAM somehow read the users home-directory and send it to vsftpd? Or is the home-directory read by some other code?
Feels like I'd have to customize vsftpd by source code, and compile my own version..

Would be awesome if anyone could give me a better solution for this!

Cheers,
Artheus

---

