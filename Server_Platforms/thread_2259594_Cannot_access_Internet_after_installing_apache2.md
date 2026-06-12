---
title: "Cannot access Internet after installing apache2"
date: 2015-01-05
forum: Server Platforms
---

### Post by Penguin360 on 2015-01-05
After I installed Apache2, I noticed that I cannot access the Internet any more. I can load Apache welcome message when typing [http://localhost](http://localhost). I thought it is because the port 80 is used by Apache,  and that is why I cannot access the Internet. So I change the default listening port to 8080 by editing /etc/apache2/ports.conf and also /etc/apache2/sites-enabled/000-default.conf, then restarted Apache, but I still cannot access the Internet. I was able to access the Internet before I installed Apache2.

Thanks.

---

### Post by Penguin360 on 2015-01-05
Never mind. It turned out that restarting Apache is not enough and I had to reboot my computer to make it effective. Now I can access Apache locally via [http://localhost:8080](http://localhost:8080) and also the Internet normally.

Sorry I don't know how to delete a post, or even there is an option to delete my own post.

---

### Post by ajgreeny on 2015-01-05
You can't delete a thread or post yourself, other than editing the post to remove the written text from it, but you can not leave the box empty as it will not save.

You have now marked the thread as solved so it may be useful for others who have the same problem; that is the whole idea of the forum - to help others.

---

