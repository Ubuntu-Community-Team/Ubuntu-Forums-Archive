---
title: "[SOLVED] Apache2 + Mysql + php5 problem"
date: 2008-08-04
forum: Server Platforms
---

### Post by tekguy on 2008-08-04
I followed [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") to install Apache2, Mysql, and php5. Everything seems to work for the most part. 

On my local machine everything works fine. I have a domain set up and I can access my web server through my domain name. The problem that I am running into is when I log into phpmyadmin or try to launch a wiki I installed that is pointed to the database, it tries to load pages from my local IP.

For example, I go to [www.mydomain.com/phpmyadmin/](www.mydomain.com/phpmyadmin/) and I get to a login box. Once I log in I see in bottom left hand corner of my browser it is opening my local IP address. If I go back to my address bar it still says [www.mydomain.com/phpmyadmin/(bunch](www.mydomain.com/phpmyadmin/(bunch) of stuff) I can just hit enter and it will refresh with my domain name and open. I can't figure out why it is even loading the local IP to begin with.

Also on the wiki after it tells me it can't open, I can change the IP back to my domain and it works. It just seems on these initial start ups of the pages it is loading an IP.

Any ideas?

---

### Post by 3rods on 2008-08-04
What DNS servers are you using for your FQDN? 

What happens if you go to [http://localhost/phpmyadmin?](http://localhost/phpmyadmin?)

---

### Post by tekguy on 2008-08-04
> **3rods said:**
> What DNS servers are you using for your FQDN? 

What happens if you go to [http://localhost/phpmyadmin?](http://localhost/phpmyadmin?)

I use Zoneedit. I will have to test the localhost again when I get home in an hour. I'm pretty sure it was working yesterday.

---

### Post by 3rods on 2008-08-04
So this is a home box? 

While your 'outside' the network, see if you can get to phpmyadmin before you get home.

---

### Post by tekguy on 2008-08-04
From outside the network I can go to [http://www.mydomain.com/phpmyadmin/](http://www.mydomain.com/phpmyadmin/) and I get to the page. When I hit Go on the login page is when it tries to load my local IP. 

I have set up test pages in both html and php just to make sure it wasn't doing that on anything that was linked. They all work fine. It just seems to be with the 2 programs that use mysql, such as phpmyadmin and mediawiki.

From home, when I do localhost/phpmyadmin/ it goes to localhost and loads fine. From my other machine it works too because I'm on the same IP.

---

### Post by tekguy on 2008-08-05
Removed

---

### Post by cariboo on 2008-08-05
Do I understand correctly that your server and your other computer have the same ip address, or are they the same computer? Is your server facing the internet without the benefit of a router?

Do you have the ip address of your server mapped in /etc/hosts as:

```
192.168.1.100 mydomain.com mydomain
```

or are you using the external address

Sorry for all the questions but it is a little tough to understand your situation

Jim

---

### Post by tekguy on 2008-08-05
> **cariboo907 said:**
> Do I understand correctly that your server and your other computer have the same ip address, or are they the same computer? Is your server facing the internet without the benefit of a router?

Do you have the ip address of your server mapped in /etc/hosts as:

```
192.168.1.100 mydomain.com mydomain
```

or are you using the external address

Sorry for all the questions but it is a little tough to understand your situation

Jim

I removed my note about the hosts file. It didn't seem to work. I have a machine that sits under a router at my house. I can get to my web server via my domain name. All of my html and php pages work fine. As soon as I log into anything that is related to mysql like phpmyadmin or mediawiki, I see it opening the local IP and then it times out. I will then have to replace the IP in my address bar with my domain name to get to the page.

---

### Post by windependence on 2008-08-05
So when you try to log in from the outside, you are seeing your natted LAN IP on your home network is that correct?

Do you have a static external IP?

-Tim

---

### Post by tekguy on 2008-08-05
> **windependence said:**
> So when you try to log in from the outside, you are seeing your natted LAN IP on your home network is that correct?

Do you have a static external IP?

-Tim

Yes I am seeing it try to use the natted LAN IP when I'm logging into anything mysql related from the outside.

I do have a static external IP.

---

### Post by tekguy on 2008-08-05
Maybe I have stumbled on to something. I set up a php script with the following code. When I browse to it, it stays at my domain name and updates my DB properly. So maybe I need to hack my phpmyadmin to load my domain name instead of my local ip....


```

<?php
$dbhost = 'localhost';
$dbuser = 'root';
$dbpass = 'password';

$conn = mysql_connect($dbhost, $dbuser, $dbpass) or die
                     ('Error connecting to mysql');

mysql_query("create database testing_database");
mysql_query("use testing_database");
mysql_query("create table my_record(name varchar(60))");
mysql_query("insert into my_record(name) values ('John Doe')");

$sql_query = mysql_query("select * from my_record");
while ($row = mysql_fetch_array($sql_query))
{
print ("Added record: ".$row[name]."<br>");
}
mysql_close();
?>

```

---

### Post by tekguy on 2008-08-06
Okay, I think I got it figured out for phpmyadmin. I had to add $cfg['PmaAbsoluteUri'] = 'http://www.mydomain.com/phpmyadmin/'; in my config.inc.php for phpmyadmin because of the port forwarding on my network.

Web requests come into my roommates web server and then forward to mine for my domain. So I think that is where the problem was happening.

---

