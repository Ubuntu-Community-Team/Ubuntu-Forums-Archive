---
title: "CSS permission denied"
date: 2017-06-10
forum: Server Platforms
---

### Post by zerobin on 2017-06-10
Hi,

The html is visible in my browser but the css file which is connected to the html isn't.
I think it has something to do with my permissions because I can't open it or edit it.
I'm quite new to Ubuntu so I don't know how to change the permission to make my CSS file interact with my html on my website.

I'm using a virtualBox on windows 10, below a screenshot of the folder.

[ATTACH=CONFIG]275568[/ATTACH]

---

### Post by jdelmoral on 2017-06-11
Open Bash and type:

```
sudo chown -R USER_NAME:USER_NAME /var/www
```

Where **USER_NAME** must be your login username.

---

