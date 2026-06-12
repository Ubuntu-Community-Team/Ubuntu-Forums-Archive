---
title: "Help with SPAM"
date: 2008-05-19
forum: Server Platforms
---

### Post by leewilson78 on 2008-05-19
Hi all, 

I recently switched servers, from a shared server to a dedicated one, my new dedicated servers runs Ubuntu.

The problem is that being a shared server, my old server had cPanel, which enabled me to easily configure SpamAssasin. I have tried to manually install SpamAssasin on my new server but there seems to be a conflict with the preinstalled software from my new hosting company. They even tried to install it, without any joy.

They have replied asking me for other software that they would like to try for me, so I was wondering if there is similar software to SA that I could ask them to try?

Thanks
Lee

---

### Post by hyper_ch on 2008-05-19
are you using Postfix? If so, it has several anti-spam measures available.

---

### Post by leewilson78 on 2008-05-19
Thanks for the fast response.

> are you using Postfix? If so, it has several anti-spam measures available. 

I am not sure to be honest. The server came preconfigured, I did gain root access, but wasn't too comfortable installing. 

Perhaps I should ask the hosting company to try configuring Postfix.


Is there an easy way to test if I am using Postfix, I do have shell access?

Here is my hosting company:


[http://www.123-reg.co.uk/dedicated-server-hosting/](http://www.123-reg.co.uk/dedicated-server-hosting/)

Thanks
Lee

---

### Post by hyper_ch on 2008-05-19
just run
```

ps aux | grep postfix

```

and post the result here

---

### Post by leewilson78 on 2008-05-19
Thanks for your help, here are the results:

```
admin@ds5091:~$ ps aux | grep postfix
postfix   4681  0.0  1.6  26408  8416 ?        Ssl  Apr21   0:00 /usr/sbin/dccifd
root      5516  0.0  0.1   6016   992 ?        Ss   Apr21   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam
root      5535  0.0  0.1   6016   592 ?        S    Apr21   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam
root      5536  0.0  0.1   6016   540 ?        S    Apr21   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam
root      5537  0.0  0.1   6016   540 ?        S    Apr21   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam
root      5538  0.0  0.1   6016   540 ?        S    Apr21   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam
admin    13700  0.0  0.1   1632   536 pts/0    R+   10:50   0:00 grep postfix
```

---

### Post by hyper_ch on 2008-05-19
you got postfix then :)

Have a look at this: [http://jimsun.linxnet.com/misc/postfix-anti-UCE.txt](http://jimsun.linxnet.com/misc/postfix-anti-UCE.txt)
and this: [http://www.howtoforge.com/block_spam_at_mta_level_postfix](http://www.howtoforge.com/block_spam_at_mta_level_postfix)
and this: [http://www.howtoforge.org/greylisting_postfix_postgrey](http://www.howtoforge.org/greylisting_postfix_postgrey)

That should give you some help... and don't forget to make a copy first of your main.cf file ;)

---

### Post by leewilson78 on 2008-05-19
Thanks for the help, does this mean that I am using it, or just that I have it installed? 

I will definitely take a look at the guides mentioned.

Thanks
Lee

---

