---
title: "Mysql &amp; dnydns domain name"
date: 2010-07-02
forum: Server Platforms
---

### Post by Thyagaraj on 2010-07-02
I want to connect to mysql server(located at dif. physical location) remotely via dyndns domain name 

My public ipaddres is dynamic ip address, as it changes every time I'll have to grant privileges to my mysql account(mysqluser@public-ip) on mysql server every time my ip changes.

So I created an dyndns account to get a domain name for mapping my dynamically changing public ip and on my local modem I've dyndns setup and I configured it properly and it could able to resolve my dyndns domain name to my public ip irrespective of ip changes(verified by using 'nslookup <dyndns-domainname>').

My problem is, I couldn't connect to my mysql server even after granting privileges to my dyndns domain(mysqluser@dyndnsdomain) but it work if I grant privileges using public ip.

Plz... need help!

---

### Post by Sanjeevtrip on 2010-07-02
What entry are you putting for dyndns, it should be A
also did you verify if it does forward lookup.

---

### Post by Thyagaraj on 2010-07-02
Yes, it could able to forward the dyndns domain name to my dynamically changing public ip.

Having granted permissions like,  
mysql>grant all on *.* to [email]mysqluser@'xyz.mine.nu[/email]' identified by 'password'; 
i could not connect to mysql server

---

### Post by cdenley on 2010-07-02
I think mysql uses reverse lookup. It doesn't resolve all hostnames you have in the user table every time you connect, then see if any IP's match. It does a reverse lookup, then checks the user table for matching hostnames or IP's. Using a dyndns record wouldn't work.

Why not just use an SSH server? Then you can either use the "mysql" command-line client, or tunnel port 3306 so you can connect on 127.0.0.1. Much more secure.

---

### Post by Thyagaraj on 2010-07-04
But every time we'll have to connect to that server via ssh for granting privileges to the public ip that dynamically changes.
Is there any other way so that having grated permissions to my remote mysql server only one time does not require permissions granted every time my ip changes. I dont want to use the wildcard '%' and it should only allow my local machine to connect to remote mysql server.

---

### Post by cdenley on 2010-07-05
When executing the mysql client within a SSH session, or tunneling port 3306 through the SSH tunnel, you connect from "127.0.0.1", not from your remote IP. There is no need to grant any mysql permissions besides 'user'@'localhost'. So, once again, why not just use an SSH server?

---

### Post by Thyagaraj on 2010-07-05
Please could you give me step by step guide...

---

### Post by cdenley on 2010-07-05
> **Thyagaraj said:**
> Please could you give me step by step guide...

For which of the two options I gave you? What kind of client system of are you using? Ubuntu?

Option 1: use mysql within SSH
[LIST=1]
[*]connect with ssh
```
ssh myuser@myhost
```
[*]use mysql client within ssh
```
mysql -u myuser -p
```
[/LIST]

Option 2: tunnel port 3306
[LIST=2]
[*]connect with ssh using port forwarding
```
ssh -L 3306:127.0.0.1:3306 myuser@myhost
```
[*]use any mysql client from the remote system not within SSH
```
mysql -h 127.0.0.1 -u myuser -p
```
[/LIST]

---

### Post by Thyagaraj on 2010-07-06
OF all the first I would like to thank you for your effort "cdenley"

Actually in my work place have some ubuntu clouds(some where else) and all the ubuntu systems will connect to mysql clouds via the graphical tools mysql query browser' and mysql administrator(mysql-server-5.1,mysql-client-5.1). For this clients I'll have to grant permissions every time our public ip changes. So i'm try to permanantly assing mysql permissons to our registered dyndns domain name on the clouds.

thank you... and looking for your more suggestions...

---

### Post by cdenley on 2010-07-06
> **Thyagaraj said:**
> OF all the first I would like to thank you for your effort "cdenley"

Actually in my work place have some ubuntu clouds(some where else) and all the ubuntu systems will connect to mysql clouds via the graphical tools mysql query browser' and mysql administrator(mysql-server-5.1,mysql-client-5.1). For this clients I'll have to grant permissions every time our public ip changes. So i'm try to permanantly assing mysql permissons to our registered dyndns domain name on the clouds.

thank you... and looking for your more suggestions...

I don't think this is possible. I don't think it is a good idea, either. I'm not very familiar with the security specifics of mysql, but I wouldn't establish a mysql connection over the internet without tunneling through a secure protocol. You can create a script to change the hostname in your mysql permissions every time your DNS record changes, but I wouldn't go that route.

If you used option 2, as I said, you can connect using any client (such as the graphical query browser).

---

### Post by Thyagaraj on 2010-07-11
Please I need help on this...

---

### Post by new_tolinux on 2010-07-11
Let's see if I get the above correct....

There is a server on location A, which has a static IP.
There is a bunch of possible clients on location B, which has dynamic IP.
There is a hostname provided by dyndns, which is always the same and routes to the IP on location B.
If one or more aren't correct, forget the rest of this post.

I'm not the best in linux-commands and it's a bit early in the morning to me to do the proper reading myself, so I'll leave the commands for the other experts to provide, but this is what I think:
* Have a cron-job running on the mysql-server which (in some way) is able to resolve the IP of location B. Because you probably don't know when the IP of location B is changing, run it for example once every five minutes (or more, or less, just according to your needs).
* Check the found IP-adress against the current know IP-address.
* If old-IP differs from new-ip -> do a query which updates the IP for the user( s) that you'll specify in that query.

If nobody else replies, I'm going to do the proper reading in a few hours when I'm really awake :P

Edit: It would be nice for me to know if using php-cli is an option, since I know a lot more of PHP than I know of bash

---

### Post by cdenley on 2010-07-12
> **cdenley said:**
> I'm not very familiar with the security specifics of mysql, but I wouldn't establish a mysql connection over the internet without tunneling through a secure protocol. You can create a script to change the hostname in your mysql permissions every time your DNS record changes, but I wouldn't go that route.

[PHP]
#!/usr/bin/php
<?php
$hostname='dynamic.hostname.com';
$mysql_remote_user='my_remote_user';
$mysql_root_user='root';
$mysql_root_pass='my_root_password';

$ip=gethostbyname($hostname);
if($ip==$hostname) die("Failed to resolve \"$hostname\"\n");
$link = mysql_connect('localhost', $mysql_root_user, $mysql_root_pass)
    or die('Could not connect: ' . mysql_error()."\n");
mysql_select_db('mysql') or die('Query failed: ' . mysql_error()."\n");
$query = "UPDATE user SET Host='";
$query.= mysql_real_escape_string($ip);
$query.= "' WHERE User='";
$query.= mysql_real_escape_string($mysql_remote_user);
$query.= "' AND Host<>'localhost'";
mysql_query($query) or die('Query failed: ' . mysql_error()."\n");
mysql_close($link);
?>
[/PHP]

Install that script, make it executable, then schedule it to run about every 5 minutes. As I already said, I don't think this is the best approach, though.

---

### Post by Thyagaraj on 2010-07-16
First of all I would like to ThankYou.

I modified the script to the following and saved it with .php extention


#!/usr/bin/php
<?php
$hostname='mycompany.mine.nu';
$mysql_remote_user='mysql1';
$mysql_root_user='root';
$mysql_root_pass='myrootpassword';

$ip=gethostbyname($hostname);
if($ip==$hostname) die("Failed to resolve \"$hostname\"\n");
$link = mysql_connect('localhost', $mysql_root_user, $mysql_root_pass)
    or Error('Could not connect: ' . mysql_error()."\n");
mysql_select_db('mysql') or Error('Query failed: ' . mysql_error()."\n");
$query = "UPDATE user SET Host='";
$query.= mysql_real_escape_string($ip);
$query.= "' WHERE User='";
$query.= mysql_real_escape_string($mysql_remote_user);
$query.= "' AND Host<>'localhost'";
mysql_query($query) or Error('Query failed: ' . mysql_error()."\n");
mysql_close($link);




When I ran this script on my server, I got the following errors:

./php.php: line 2: ?php: No such file or directory
./php.php: line 3: =mycompany.mine.nu: command not found
./php.php: line 4: =mysql1: command not found
./php.php: line 5: =root: command not found
./php.php: line 6: =myrootpassword: command not found
./php.php: line 8: syntax error near unexpected token `$hostname'
./php.php: line 8: `$ip=gethostbyname($hostname);'

---

### Post by cdenley on 2010-07-16
The extension doesn't matter. I forgot to include the "?>" closing tag. Also, you need to install the php command-line interpreter.
```

sudo apt-get install php5-cli

```

---

### Post by Thyagaraj on 2010-07-17
Hi denley!

I'm getting following error after the modification. I installed php5-cli


PHP Fatal error:  Call to undefined function mysql_connect() in /dyndns on line 10

---

### Post by new_tolinux on 2010-07-17
I guess you'll need to install php5-mysql in order to connect to mysql with PHP.

```
sudo apt-get install php5-mysql
```

---

### Post by Thyagaraj on 2010-07-19
On one of my server I'm getting following error. php5-cli & php5-mysql is installed

Fatal error: Call to undefined function Error() in /dyndns on line 18

The 18th line is,
18: mysql_query($query) or Error('Query failed: ' . mysql_error()."\n");

---

### Post by new_tolinux on 2010-07-19
Error isn't a PHP-statement.
Replace it with:
```
mysql_query($query) or die('Query failed: ' . mysql_error()."\n");
```or
```
mysql_query($query) or exit('Query failed: ' .  mysql_error()."\n");
```Both are the same functions, only different names.

Edit:
I had a look at the code and I saw that the Error()-function isn't only on line 18, so I place an edited version of the code below (tested on my own MySQL server with google, removed the password ofcourse ;)):
[php]#!/usr/bin/php
<?php
$hostname='www.google.nl';
$mysql_remote_user='remoteuser';
$mysql_root_user='root';
$mysql_root_pass='yourrootpassword';

$ip=gethostbyname($hostname);
if ($ip==$hostname) die("Failed to resolve \"$hostname\"\n");
$link = mysql_connect('localhost', $mysql_root_user, $mysql_root_pass)
    or die('Could not connect: ' . mysql_error()."\n");
mysql_select_db('mysql') or die('Query failed: ' . mysql_error()."\n");
$query = "UPDATE user SET Host='";
$query.= mysql_real_escape_string($ip);
$query.= "' WHERE User='";
$query.= mysql_real_escape_string($mysql_remote_user);
$query.= "' AND Host<>'localhost'";
mysql_query($query) or die('Query failed: ' . mysql_error()."\n");
mysql_close($link);
?>
[/php]

---

### Post by cdenley on 2010-07-19
Sorry, I copied the mysql code from another script, didn't realize I had used a user function for that.

---

### Post by Thyagaraj on 2010-07-22
Any other way denley?

---

### Post by cdenley on 2010-07-22
> **Thyagaraj said:**
> Any other way denley?

No. You must allow either an IP, or the hostname that the IP resolves to with reverse lookup. You can either keep your mysql permissions updated with the current dynamic IP, connect through a tunnel so the mysql connection can be coming from 127.0.0.1, or connect from a static IP.

---

### Post by new_tolinux on 2010-07-22
> **Thyagaraj said:**
> Any other way denley?

All other options are less secure.
- Allow % as a hostname in MySQL for that specific user (% = access from any IP allowed)
- Create a webpage/script that verifies a password and replace the currently allowed IP with the IP of the visitor running that webpage.

Both are insecure, because it's possible for anyone to gain access to the MySQL server if your connection isn't encrypted (or by simply guessing which password is needed ;))

---

