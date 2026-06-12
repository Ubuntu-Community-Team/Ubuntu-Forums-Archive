---
title: "[SOLVED] how to set phpmyadmin to listen only local"
date: 2008-08-27
forum: Security
---

### Post by qstraza on 2008-08-27
Hello. I have phpmyadmin installed, but its globally available.
I want to set it up so it will only appear in local network.

Few years ago i solved this by make a subdomain and point it to 192.168.2.1 and i made a virtualhost on that domain which pointed to phpmyadmin.

---

### Post by rogeriopvl on 2008-08-27
Well, I'm not sure if there is any option in phpmyadmin to make it behavior like that.

Although it might look like a weird solution, you could edit the PHP code in phpmyadmin to reject any access from non local IP addresses.

---

### Post by brian_p on 2008-08-27
> **qstraza said:**
> Hello. I have phpmyadmin installed, but its globally available.
I want to set it up so it will only appear in local network. 

[http://wiki.contribs.org/Phpmyadminmulti](http://wiki.contribs.org/Phpmyadminmulti)

---

### Post by qstraza on 2008-08-27
```
To limit access to local network :

db configuration setprop phpmyadminmulti access private
signal-event console-save

```

this is not working, what is the "db" command?

---

### Post by brian_p on 2008-08-27
> **qstraza said:**
> 

this is not working, what is the "db" command?

Let's move on; that link doesn't appear particularly useful. Is

[http://www.factsandpeople.com/facts-mainmenu-5/18-php/65-allowing-only-local-users-to-phpmyadmin](http://www.factsandpeople.com/facts-mainmenu-5/18-php/65-allowing-only-local-users-to-phpmyadmin)

any better?

---

### Post by alecz20 on 2010-08-27
What I did was to add this directive to /etc/apache2/httpd.conf

```

<Directory /usr/share/phpmyadmin>
Allow from 192.168.0.0/24
Deny from all
</Directory>

```

---

### Post by cariboo on 2010-08-28
@alecz20 adding info to an old solved thread, isn't going to help many people, as most users will look at the post date, even though it is marked solved, and pass it by. With a 6 month release cycle, Ubuntu has changed quite a bit since the release of hardy (April, 2008), many solutions that worked then, don't work now.

---

### Post by mtron on 2010-08-30
Still a thread with a valid (and useful!) answer is better than a SOLVED without a useable Response ;)

---

### Post by alecz20 on 2010-08-30
@cariboo907

I get your point, however, I was very unsatisfied with all the solutions provided.

I often look at many solved threads, and the solutions are not relevant anymore.

In my case, I believe (as mtron was also saying) **that this solution is applicable to any system that uses apache with phpmyadmin, regardless of OS version.**

Plus it's elegant, and can be used in other similar circumstances.

---

### Post by anomie on 2010-08-30
FWIW, I completely agree with cariboo907 in that digging up old threads is usually in poor taste. 

On the other hand, alecz20's solution is (IMO) the simplest / best and it's *baffling* that it was not mentioned earlier in the thread. (I guess it's possible someone could be using nginx instead of Apache web server, but if they can't figure out how to restrict access at the IP level, I suspect they're working from a phpMyAdmin + Apache howto anyway...)

---

