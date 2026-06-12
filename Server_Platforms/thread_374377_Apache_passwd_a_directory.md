---
title: "Apache passwd a directory"
date: 2007-03-02
forum: Server Platforms
---

### Post by lmcdougall on 2007-03-02
I am trying to make a directory private that can be access vi user/passwd.
This is what I have done so far but I do not see the results I am looking. (Login)[http://ubuntuforums.org/images/smilies/confused.gif:confused:](http://ubuntuforums.org/images/smilies/confused.gif:confused:) 

1. created the directory.
2. created a .htpasswd in the directory.
3.create a .htaccess in the directory:
    AuthType Basic
    AuthUserFile /path/.htpasswd
    AuthGroupFile /dev/null
    require user user
I am using Apache 2.xx Ubuntu 6.10

Thanks
-L

---

### Post by tr333 on 2007-03-03
not sure if this will help, but the line "AuthGroupFile /dev/null" looks incorrect.  if you don't have a group file then remove this line.  with this line, you are telling apache to read from the file /dev/null which can't be done since /dev/null is not a regular file.

---

### Post by scxtt on 2007-03-03
i haven't used this in a while, but i think you need to add users to the whole htpasswd convention ... additionally, i don't think "require user user" will work, you'd need to do something like:

#> htpasswd -c /home/doe/public_html/.htpasswd jane

---

### Post by tr333 on 2007-03-03
take a look at [http://httpd.apache.org/docs/2.0/howto/auth.html]("http://httpd.apache.org/docs/2.0/howto/auth.html").
htaccess files shouldnt be used unless you can't access the main apache config file.  if you need more info on htaccess, look at [http://httpd.apache.org/docs/2.0/howto/htaccess.html]("http://httpd.apache.org/docs/2.0/howto/htaccess.html").

---

### Post by Luis McDOugall on 2007-03-04
Just, in case you're wondering I am reading your posts and working on it.
Still not "FUN" yet.
Thanks.:)

---

