---
title: "Howto change console character set?"
date: 2007-04-04
forum: Server Platforms
---

### Post by archonon on 2007-04-04
I've just installed Ubuntu server edition, but apparently it's character set is configured as UTF-8. How do i change it to ISO-8859-1? 

Server will be used as ssh-box and putty's default charset is ISO-8859, resulting wrong ASCII chars. It wouldn’t be a problem if there weren't any other users, but since there is, I don't want to cause unnecessary problems after server switch.

Thanks.

---

### Post by djf_jeff on 2007-04-04
Edit the file : /etc/default/locale and set it to the locale you want.

---

### Post by fakie_flip on 2007-06-06
> **djf_jeff said:**
> Edit the file : /etc/default/locale and set it to the locale you want.

I tried that. 

```
chris@ubuntu:~$ cat /etc/default/locale
LANG="ISO-8859-1"
chris@ubuntu:~$ 
```

Then I rebooted , and I had still have weird characters with midnight commander and pidgin.

[http://img183.imageshack.us/img183/9026/hpim1001bh8.jpg](http://img183.imageshack.us/img183/9026/hpim1001bh8.jpg)

[http://img183.imageshack.us/img183/9010/hpim1007zv2.jpg](http://img183.imageshack.us/img183/9010/hpim1007zv2.jpg)

---

### Post by fakie_flip on 2007-06-06
Here is how.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_locales_to_Ubuntu_the_command_line_way](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_locales_to_Ubuntu_the_command_line_way)

But you may still have problems. To see how this is fixed, read my thread.

[http://ubuntuforums.org/showthread.php?p=2794728#post2794728](http://ubuntuforums.org/showthread.php?p=2794728#post2794728)

---

### Post by fakie_flip on 2007-06-08
mc was messed up again after I rebooted, so I added this to my root user's crontab.

@reboot /etc/init.d/console-setup reload

I'll reboot soon and see if that fixes it.

---

