---
title: "www.mysite.com works but not mysite.com - unable to create sub domains too"
date: 2011-08-03
forum: Server Platforms
---

### Post by Terwax1 on 2011-08-03
I followed this tutorial: [http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/]("http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/")

But the links i created are not accessible. Is it to do with mysite.com not working?

I was doing stats.mysite.com and forums.mysite.com, but didnt work :(

---

### Post by new_tolinux on 2011-08-03
What did you do exactly, as I read that there is the article itself, and a few commands which also seem to be useful.

---

### Post by Terwax1 on 2011-08-03
```
$ORIGIN mysite.com.
$TTL 86400

@       IN      SOA     ns1.mysite.com.      admin.mysite.com. (
                                2010011801      ; serial number
                                28800           ; Refresh
                                7200            ; Retry
                                864000          ; Expire
                                86400           ; Min TTL
                                )

                NS      ns1.mysite.com.

                MX      10 mail.mysite.com.

ns1             IN      A       my ip
www             IN      A       my ip
tomato          IN      A       my ip
mail            IN      A       my ip
*               IN      A       my ip
forums          IN      A       my ip
stats           IN      A       my ip

```

as well as "/etc/apache2/sites-available/stats"

> <VirtualHost myip:80>
    DocumentRoot /var/www/stats/
    ServerName stats.localhost
    <Directory /var/www/stats/>
        Options Indexes FollowSymLinks MultiViews +Includes
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>



also sent: 
nsdc rebuild
/etc/init.d/nsd3 restart

---

### Post by Terwax1 on 2011-08-03
```
127.0.0.1       localhost.localdomain   localhost
127.0.0.1       stats.localhost.localdomain   localhost
127.0.0.1       forums.localhost.localdomain   localhost
myip  gdghdrh.drhdrhd.com    gdghdrh

```

That under etc/hosts

---

### Post by new_tolinux on 2011-08-03
I have a look at it later today, since I recognize my English starts to fail (I actually meant "comments" instead of "commands") and it's already light out here (7:30AM) ;)

---

### Post by Terwax1 on 2011-08-03
also do i need to put it under /var/stats folder for sub domain or /var/www/stats?

i really want to make mysite.com to be working.

---

### Post by Doug S on 2011-08-03
Hi,
I am only commenting on the mysite.com part herein, not the sub domains part:
I had the same problem where [www.mysite.com]("http://www.mysite.com") would work but mysite.com did not.
It was a posting by SeijiSensei that gave me the information to fix the problem, ( [http://ubuntuforums.org/showthread.php?t=1739173](http://ubuntuforums.org/showthread.php?t=1739173) posting number 6) however I only had to do the changes in the bind files not the server alias changes in the apache virtualhost stuff. Actually you can find many posts, by very experienced and knowledgable users, that say the server alias stuff is needed, but I don't have it and it works fine. I would very much like to understand if I am not understanding something. Anyway, I digress...
I think if you change this line:```
 
@       IN      SOA     ns1.mysite.com.      admin.mysite.com. (
 

```
To this:```
 
@       IN      SOA     mysite.com.      admin.mysite.com. (

```
It will work (of course only after you restsart after the edit)

---

### Post by Terwax1 on 2011-08-03
bump

---

### Post by Terwax1 on 2011-08-03
restarted apache after following your suggestion, didn't work...

---

### Post by Doug S on 2011-08-04
It is not apache that needs to be re-started, it is the name stuff.
In my case "sudo /etc/init.d/bind9 restart". Based on your earlier posting, it seems you are using something different (nsd3), so re-start that.
Also, I forgot to mention you need to also edit the serial number line from 2010011801 to 2011080401.
The only other obvious difference I see in our files, is that I don't have the $ORIGIN line that you have. If it still doesn't work for you, then try the server alias stuff that the link I gave mentions.

---

