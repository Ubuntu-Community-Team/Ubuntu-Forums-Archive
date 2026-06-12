---
title: "user nobody with lampp"
date: 2011-10-07
forum: Security
---

### Post by tanoloco on 2011-10-07
Hello,

I recently installed lampp and have no experience with that yet.

I noticed it doesn't create an /etc/apache2 folder at all but it puts directly httpd.conf in /opt/lampp/etc

As I have no time now to understand how to make virtual hosts in this case, I decided simply to create a symbolic link for /opt/lampp/htdocs pointing to a folder I wanted to create in a different partition like /media/data/htdocs

Now .. to protect my data I always used root:users 770 on /media/data and all its subdirs

Once I ended with lamp I tried reaching localhost with a browser and received a Forbidden error.
After some tests I found that lampp uses nobody user instead of www-data that means that if I use nobody:users 770 on /media/data and all its subdirs (included htdocs) I can reach localhost trough the browser, otherwise I have to use root:users 755 on the same paths

Now: in your opinion is it more safer to use
1: root:users 775 on /media/data and /media/data/htdocs
or
2: nobody:users 770 on the same?

Accordingly to [https://wiki.ubuntu.com/nobody]("https://wiki.ubuntu.com/nobody") it seems it might be safer the second choice (use nobody)

Which is your opinion?
Thanks in advance

pd: last question, I cannot understand one thing: can an intruder be a nobody user?

---

### Post by bodhi.zazen on 2011-10-07
Sounds as if you installed apache from source.

I suggest you use the repositories.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

Ubuntu uses www-data for apache (and other http servers).

Most of your other questions are "basic" linux permissions. Apache can not access a directory if it (www-data) does not have permission.

---

### Post by tanoloco on 2011-10-07
Thank you for sharing those links.
I will look at them.

Actually I used xampp
[http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html")

I never heard it before and nevere used it.
I've always used repositories as you suggested.

Two days ago at work they asked me to use xampp instead,
so all the workers are obliged to use the same version
of things.

I think it is supposed to make installation easier,
but actually it does a completely different installation.

Apache doesn't use www-data user but nobody user surprisly!
Then everything is stored under /opt/lampp
(there's no /etc/apache2 for example)
and I cannot understand how to make virtual hosts!

By the way my basic question is about nobody user.
I will face other things step by step.
I never used the nobody user before .. so I don't have a real idea about it.

Is it safe to use nobody:users 770 on a folder?
I have to use this because, as I said, Apache use
nobody user and not www-data in this configuration, and
I don't know where I can change it (and if I can)

The name *nobody* worries me a littel bit,
sounds like anyone can have complete access to my folder.

Thank you for explaining me that.

---

### Post by bodhi.zazen on 2011-10-07
You should be fine with the user "nobody".

---

### Post by tanoloco on 2011-10-07
I know you since a while and you have my complete trust!
Thank you.

---

### Post by Dangertux on 2011-10-07
Just another note , it will likely be covered in the links you were given, but I would not recommend using permissions 770 in your web root.  You shouldn't need more than 644, MAYBE 755, but that is pushing it still  

In short the reasoning behind this is many services use nobody:nobody as their username:group (basic unprivileged user) you don't really want other services being able to write in your web root it can cause problems if a compromise occurs on one of those services. You also certainly don't want anything  executing in there either.

As far as nobody is concerned it's essentially the same concept as www-data, both are just non-privileged users without a shell.

---

### Post by tanoloco on 2011-10-14
> **Dangertux said:**
> I would not recommend using permissions 770 in your web root.  You shouldn't need more than 644, MAYBE 755, but that is pushing it still 

Thank you for your advice.
I set my web-root as
<my-user>:nogroup :: 755

That's because I need full access,
both nobody and www-data need read access.
I don't know if they need execute for now .. I will test it later on.

Thank you

---

