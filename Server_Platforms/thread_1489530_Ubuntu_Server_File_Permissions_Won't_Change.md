---
title: "Ubuntu Server File Permissions Won't Change"
date: 2010-05-21
forum: Server Platforms
---

### Post by gggccc on 2010-05-21
On my server computer, I can't get it to change file settings. The way I know this is by wordpress saying "/var/www/wp-content is write-able. If you've finished installing the plugin, change the permissions back to the default: chmod 755 /var/www/wp-content," then me using the command ```
sudo chmod 755 /var/www/wp-content/*
```, which it tells me to use, and when I refresh the page, guess what's there. The same error. Do you need to restart apache after changing  the file permissions or what am I doing wrong?

---

### Post by trundlenut on 2010-05-21
I think you want to try this instead:

```
sudo chmod -R 755 /var/www/wp-content/
```

Assuming you want to change the permissions on the folder called wp-content and everything in it.

---

### Post by terazen on 2010-05-21
You can also use -R with chown, chown -R user:group /var/www/wp-content/, if needed.

---

### Post by gggccc on 2010-05-21
> **terazen said:**
> You can also use -R with chown, chown -R user:group /var/www/wp-content/, if needed.

I get the error ```
chown: invalid user: user:group
```

---

### Post by gggccc on 2010-05-21
If you go to my site, [gregsite.zapto.org]("http://gregsite.zapto.org/"), and make an account, and try to upload an avatar, it says "Upload Error: File upload failed," even though I tried all the ideas by the current replies.

---

### Post by arrrghhh on 2010-05-21
> **gggccc said:**
> I get the error ```
chown: invalid user: user:group
```

You need to change user to the user you want to own it, and the group for the group you want to own it.  For example my user 'bob' - it would be ```
sudo chown -R bob:bob /var/www
```

---

### Post by gggccc on 2010-05-21
> **arrrghhh said:**
> You need to change user to the user you want to own it, and the group for the group you want to own it.  For example my user 'bob' - it would be ```
sudo chown -R bob:bob /var/www
```

I got that to work, but it still gives me errors on the site.

---

### Post by arrrghhh on 2010-05-21
Are you changing ownership to www-data:www-data or what?

---

