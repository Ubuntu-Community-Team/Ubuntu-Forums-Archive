---
title: "can't access MySQL remotely via phpMyAdmin"
date: 2011-01-03
forum: Server Platforms
---

### Post by steve_c on 2011-01-03
One server is a dedicated MySQL server. After upgrading that one to Ubuntu 10.04 (from an ancient Suse 9.2), both servers are running Ubuntu 10.04 LTS.

I have another server that I use to administer the database server via phpMyAdmin. However since the upgrade it is not able to connect. I get an error #1130 Cannot log in to the MySQL server. The same happens if I try to connect remotely from the command line with: mysql -u root -h 129.79.137.121 -p

I'm not sure if this is an iptables/ports problem or a configuration problem on the MySQL end or something else entirely.

I've searched and tried the suggestions I've found in various places but none seems to have fixed it.

Thanks for the help!

---

### Post by steve_c on 2011-01-03
Ok, I seem to have figured it out, at least in theory. My problem was I needed to specifically allow connections via the mysql prompt, like so:

```
grant all on foo.* to admin@'php.MyAdmin.IP' identified by 'password';
```

I feel as though there's some nuance here I'm not fully understanding and I'm worried when I reimport my mysqldump'd database (all tables) I'll lose these specific permissions and have to recreate them. Can anyone verify that?

And can anyone recommend to me a good MySQL administration guide?

Thanks!

---

### Post by Vegan on 2011-01-03
Go visit mysql.org and read the manuals there. Make sure you have lots of coffee.

mysql is easy enough to administrate.

I keep mine locked to localhost to prevent most problems, but with a strong password its possible to expose it to the internet for outside access.

You might be happier with Webmin to manage a server from the internet.

I find Webmin can manage mysql easily

---

