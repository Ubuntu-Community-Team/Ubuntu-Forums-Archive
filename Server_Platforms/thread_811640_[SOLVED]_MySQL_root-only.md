---
title: "[SOLVED] MySQL root-only ?"
date: 2008-05-29
forum: Server Platforms
---

### Post by Korijn on 2008-05-29
I have installed Apache, PHP and MySQL together a while ago on 8.04. Yesterday I accidentically deleted root, so I reinstalled MySQL today. Now I can only use MySQL with root! I cannot login with any other users in phpMyAdmin or the shell mysql program. Nor can they log in through the php mysql_connect() command.

What's up?

---

### Post by Monicker on 2008-05-29
Did you purge the previous install of mysql?  Are there any other users listed in the mysql.user table?  You may have to recreate any other users that you had made previously.

```
mysql -u root -p

select User from mysql.user;
```

---

### Post by hyper_ch on 2008-05-29
did you add new users to mysql?

---

### Post by Korijn on 2008-05-29
Guess I forgot to mention that. Yes I've purged every package there was to purge. I had to fill in a new root password when I reinstalled it.

I created a new user through phpMyAdmin with the root account, granted it all global privileges available. Yet it won't log in!

Root logs in just fine, my new account receives this error:
```
Fout
#1045 - Access denied for user 'korijn'@'localhost' (using password: YES)
```

Here, they have the same priviliges:
```
 	user 	host 		pass 	priviliges 	grant	edit
<debian-sys/each here>
 	korijn  % 	 	Yes  	ALL PRIVILEGES  Yes  	Edit
	root 	127.0.0.1 	Yes	ALL PRIVILEGES 	Yes 	Edit
	root 	korijn 		Ja 	ALL PRIVILEGES 	Yes 	Edit
	root 	localhost 	Yes 	ALL PRIVILEGES 	Yes 	Edit
```

---

### Post by quelx on 2008-05-29
log in as root (**mysql -uroot -p**)

and ```
FLUSH PRIVILEGES;
```

---

### Post by Korijn on 2008-05-29
> **quelx said:**
> log in as root (**mysql -uroot -p**)

and ```
FLUSH PRIVILEGES;
```
Nope, doesn't solve the problem.

I do have three users which are called "Each", they're marked red and they have the privilege "USAGE" which is NOT granted. Maybe I should toggle that?

---

### Post by Korijn on 2008-05-30
It turned out to be a misconfiguration of my localhost domain/ip settings. So, fixed it.

Thanks all.

---

