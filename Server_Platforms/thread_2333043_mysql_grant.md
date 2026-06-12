---
title: "mysql grant"
date: 2016-08-06
forum: Server Platforms
---

### Post by Vegan on 2016-08-06
GRANT ALL ON database.* TO 'user'@'%' IDENTIFIED BY 'password';

where database is the created database and user is the assigned user to the new database

i get a warning and OK

what gives?

Ubuntu 16.04 as usual

---

### Post by Habitual on 2016-08-07
First off, 'user'@'%' is a Security Risk. The '%' is a wildcard and this user can connect from anywhere.
Consider the implications.

Try this:
```
GRANT ALL ON database.* TO 'user'@'localhost' IDENTIFIED BY 'password'; flush privileges; exit;
```
This will permit "user" to connect from the localhost only. Remote admins would need another or modified privilege.

Test with
```
mysql -u<user> -p
```

---

### Post by Vegan on 2016-08-07
can i grant to a specific URL? rather than IP address?

---

### Post by Habitual on 2016-08-07
> **Vegan said:**
> can i grant to a specific URL? rather than IP address?
No. [http://dev.mysql.com/doc/refman/5.7/en/grant.html](http://dev.mysql.com/doc/refman/5.7/en/grant.html)

---

### Post by Vegan on 2016-08-07
living in a datacenter means that my server moves around once in awhile as loads are balanced, the URL though means i can use PUTTY and get a console

this suggests the SQL standard is behind the curve slightly afar as a web appliance is concerned

wordpress can use a URL to connect to the database so this seems like a no brainer

guess MySQL was designed to be more bolted onto a LAMP stack instead of being part of a swarm of servers

sadly

DROP SERVER MySQL 

is not an option


WordPress is vendor locked, open source but they do not use any other database

---

### Post by Vegan on 2016-08-07
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%.example.com' 
    IDENTIFIED BY 'some_characters' 
    WITH GRANT OPTION;
FLUSH PRIVILEGES;

is more or less what I wanted, but I wanted to grant only to the specific web site or something like that

---

### Post by Habitual on 2016-08-08
> **Vegan said:**
> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%.example.com
Sorry, not possible.
You are confusing privileges in mysql to web server access privileges

---

### Post by Vegan on 2016-08-08
Guess some of these references i find are USELESS

This is why I developed a cryptographically secure password maker to protect the admin account, the database account etc

users are only granted their respective databases with general access, accounts are strongly protected

I was simply looking to secure my server as best i can as a public utility

I can use it for all web sites, anywhere, which is one benefit, not all ISPs have a big fat database to work with

---

### Post by Habitual on 2016-08-08
> **Vegan said:**
> 
I was simply looking to secure my server as best i can as a public utility
I can use it for all web sites, anywhere, which is one benefit, not all ISPs have a big fat database to work with
My example dealt with individual databases.

"Securing MySQL From Within" section at [https://www.digitalocean.com/community/tutorials/how-to-secure-mysql-and-mariadb-databases-in-a-linux-vps](https://www.digitalocean.com/community/tutorials/how-to-secure-mysql-and-mariadb-databases-in-a-linux-vps) deals specifically with your opening post.
 
I think you need Update instead of Grant since the user exists and may already have correct db permissions.
You're Welcome. by the way.
 Good Luck.

---

### Post by Vegan on 2016-08-08
How flexible is MySQL for update, I have spent more time on backup/restore as that seemed to be more useful

WP also has backup and restore so I was looking the capability there too

MySQL server is in Azure and it's now hosting several web sites but now I am wondering if I should up Apache2 so I can use storage for things like image server etc

[COLOR="#FF0000"]SELECT User,Host,Password FROM mysql.user;[/COLOR]

I was also wondering, does MySQL use a salt for passwords or should I consider encrypting the data disk?

---

### Post by Habitual on 2016-08-09
Not even a "Thank you."
I'm done here.

---

### Post by Vegan on 2016-08-09
sorry i have been real tired fixing problems with azure galore

---

### Post by Habitual on 2016-08-12
> **Vegan said:**
> I consider encrypting the data disk?
Format and encrypt...LVM...
Don't think you planned on downtime? Got backups?
> **Vegan said:**
> Guess some of these references i find are USELESS
Without quoting your sources, I can only agree with you.
And I don't agree with you. :)

Have you figured out the Update vs. Grant statement to be true, or not? You know, **the topic**?
You have to stay focused. Fix one thing at a time.

I think you may have made progress when you diverted to "mysql salting" and "encrypting the data disk".
Secure connections in secure environments if done correctly, could include some sort of salt/hash routine, but I would consider this task as secondary to securing access with proper privileges from pre-defined hosts/networks.
That is my opinion.

You may not understand it now, but I sense you are "asking the right kind of questions" but in a general sort  of way.
Nothing wrong with that.
As I said. Always quote what you've read, where you read it (links are great!)

Found this and I kept as a personal "Keeper".
[How to secure an Ubuntu 16.04 LTS server - Part 1 The Basics]("https://www.thefanclub.co.za/how-to/how-secure-ubuntu-1604-lts-server-part-1-basics")
It's the basics and the ***techniques*** discussed are valid.

Does not discuss mysql.
Never use 'user'@'%' for a user@host identifier. 
"Update" instead of grant for existing users.
Quote your references.

If Azure is anything like AWS, then you have to specifically open 3306?
It may even be installed and running "locally".
How are these users accessing the mysql host exactly?
"externally" from here, I'd check access with 
```
mysql -uhabitual -pmykung-fu -h<azure mysql ip>
```
GRANT ALL is a little excessive, but common. It is my opinion that ALL is a less secure GRANT option
If host access control is not controlled in at least 2 ways.

References:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[https://www.thefanclub.co.za/how-to/how-secure-ubuntu-1604-lts-server-part-1-basics](https://www.thefanclub.co.za/how-to/how-secure-ubuntu-1604-lts-server-part-1-basics)
[https://help.ubuntu.com/lts/serverguide/security.html](https://help.ubuntu.com/lts/serverguide/security.html)

And a "Thank you" is considered good manners.
Sorry, or not I cannot say, but there's no reason to be discourteous.

Have a Great Day!

---

### Post by Vegan on 2016-08-15
thanks for the references to read, always glad to have more manuals to consider

i noticed ufw is disabled by default with 16.04, bit the datacenter i am in does have a firewall, so I am using that instead

i have to use the default 3306 port for MySQL as WordPress expects that, not a big problem but I am alert to possible threats

All the short manuals suggest GRANT ALL and restrict to the user.* seems to be the catchall for any application beyond WP etc

I have lots more work with SQL to learn, probably an idea to mechanize some work with a shell script

any tools to generate passwords etc for a shell script etc?

---

### Post by Habitual on 2016-08-15
> **Vegan said:**
> thanks for the references to read, always glad to have more manuals to consider

i noticed ufw is disabled by default with 16.04, bit the datacenter i am in does have a firewall, so I am using that instead

i have to use the default 3306 port for MySQL as WordPress expects that, not a big problem but I am alert to possible threats

All the short manuals suggest GRANT ALL and restrict to the user.* seems to be the catchall for any application beyond WP etc

I have lots more work with SQL to learn, probably an idea to mechanize some work with a shell script
You're welcome.
My 3306 is closed to the world, and my Wordpress works just fine. :)

Ignore my "retentiveness". Grant ALL to user@ is fine.
I said it was common. I didn't say it was 'wrong'. :) 
Am I squirming in my "retentiveness"? Little bit.

> **Vegan said:**
> some work with a shell script
**Nuggets!**
8 Character random user for virgin copy of wp-config.php
```
sed -i -e 's@username_here@'$(<  /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c${1:-8};echo;)'@' /path/to/wp-config.php
```
12 Character random password for virgin copy of wp-config
```
sed -i -e 's@password_here@'$(<  /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c${1:-12};echo;)'@' /path/to/wp-config.php
```

Install the Wordpress Plugin [Wordfence]("https://www.wordfence.com/"). They are the "Good Guys".
It's free. I am not affiliated.

Have fun.
Automating Wordpress is a "chore" to get setup, but I enjoyed the challenge immensely.

---

### Post by Vegan on 2016-08-20
thanks for the nuggets 

i wrote a small program that can generate secure passwords, i made it to secure Wi-Fi etc, but it has also been useful for forums etc. I make it with C++ but its a windows program with clipboard support etc

thanks for the suggestions for a WP setup which can be useful for anyone who may want to mechanize setting up web sites

---

### Post by Habitual on 2016-08-20
Glad it worked out.

---

### Post by Vegan on 2016-08-20
you any good with postfix and dovcot?

---

