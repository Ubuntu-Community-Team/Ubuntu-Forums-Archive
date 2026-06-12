---
title: "phpbb3 on ubuntu server 9.04"
date: 2009-05-12
forum: Server Platforms
---

### Post by orudie on 2009-05-12
Just installed phpbb3 package with apt-get install phpbb3 , it asked me for admin mysql password and installation was completed without any errors. Now i'm trying myurl.com/phpbb and myrul/phpbb3 and nothing. I also tried restarting apache2 server. Any suggestions ?

---

### Post by cdenley on 2009-05-12
Do you receive a 404 response from the server?
```

echo -e "HEAD /phpbb HTTP/1.0\n"|nc myurl.com 80

```

What is this output?
```

cat /etc/apache2/conf.d/phpbb3.conf

```

---

### Post by daboroe on 2009-05-12
go into /var/www and see if there is a subfolder called phpBB3 or what not.If not that is why you can not get that to work.

---

### Post by cdenley on 2009-05-12
> **daboroe said:**
> go into /var/www and see if there is a subfolder called phpBB3 or what not.If not that is why you can not get that to work.

You are incorrect. phpbb3 installs an apache configuration file that creates an alias to another directory.

---

### Post by daboroe on 2009-05-14
I have tried to install it via the way you did and it did not work for me. If you go and download it and then intall it the way i stated should be the way it installs.

---

### Post by cdenley on 2009-05-14
> **daboroe said:**
> I have tried to install it via the way you did and it did not work for me. If you go and download it and then intall it the way i stated should be the way it installs.

I suggest you stick with software from the repos for security and reliability. If there is a problem with the ubuntu package, post a bug report, or start a thread here to make sure it's not a mistake on your part.

---

