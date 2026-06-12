---
title: "suphp, is it enough with aptitude?"
date: 2006-03-24
forum: Server Platforms
---

### Post by danf_1979 on 2006-03-24
Hi:
I have installed libapache-mod-suphp with the command:
```

# aptitude install libapache-mod-suphp

```
Everything went ok, but now what? Do I have to edit something? I did a search in /etc/apache/httpd.conf for some suphp stuff, but could'nt find anything. How can I tell if I am using already suphp? I'm lost... thanks.

---

### Post by dermotti on 2006-03-24
Does it show up in <? phpinfo(); ?>

---

### Post by danf_1979 on 2006-03-24
It says:

Loaded Modules
mod_python, **mod_suphp**, mod_php4, mod_setenvif, mod_expires, mod_auth, mod_access, mod_rewrite, mod_alias, mod_userdir, mod_cgi, mod_dir, mod_autoindex, mod_status, mod_negotiation, mod_mime, mod_mime_magic, mod_log_config, mod_macro, mod_so, http_core

So I guess I'm OK?

---

### Post by Horndog on 2006-03-24
Have a look [here.]("http://www.debian-administration.org/articles/84")

---

### Post by danf_1979 on 2006-03-24
But, correct me If I am wrong. For what I had understood this should not had happened?
I tried to create a file, but could not do it. Why? I have /var/www/web8/web/test.php owned by some user, and I thought that if I created a file with touch, the resulted file would have been owned by the same user. Instead I got an error:

touch("./test.test");

It gets:

Warning: touch() [function.touch]: Unable to create file ./test.test because Permission denied in /var/www/web8/web/test.php on line 3

---

### Post by danf_1979 on 2006-03-24
I'm reading the link now, thanks.

---

### Post by danf_1979 on 2006-03-24
Thank you Horndog!!!!! That was it! :):):):)

---

