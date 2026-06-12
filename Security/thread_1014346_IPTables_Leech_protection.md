---
title: "IPTables Leech protection"
date: 2008-12-17
forum: Security
---

### Post by hivltg on 2008-12-17
Hi,
   I'm having a major problem with what seems to be an attack from someone in china CNCGroup or something. Anyways I have blocked individual IP's (using IPtables) that are causing the problem however they will keep coming back. My web server hosts large files and this attack is basicly downloading a 600MB file over and over again slowing down the server and going though my bandwidth fast (they must have a very fast connection the rate they are downloading). I was wondering if anyone knows of away to auto detect this type of attack and block the ip address. I.e block an IP that connects many times over a period of time. Or another solution is to stop direct traffic to the server as all traffic should come via another web server. Any known solutions (preferably using IPtables) would be relay helpful. 

Thanks

Dan

---

### Post by cdtech on 2008-12-17
What port are they using? 80. Here is a system I use for my "ssh port 22":
```
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds **60 --hitcount 5 --rttl** --name SSH -j DROP
```
This will rate-limit all incoming SSH connections to 5 within a one minute window. Normal users wont have any problems logging in, but the brute force attacks will be dropped, limiting the number of possible account combinations from unlimited, to 5.

You could use this technique or find the ip using "auth.log" file and just block that particular ip address.

Hope this helps ya, or gives you some idea on setting up the iptables....

---

### Post by cdenley on 2008-12-18
You could either configure fail2ban to audit your apache log for requests for that file, or create a download script which retrieves the actual file and logs all downloads, but fails if there have been too many downloads from that IP.

By the way, I think "leech protection" refers to external sites linking directly to your files, not a single user downloading the same file repeatedly to steal your bandwidth.

---

### Post by hivltg on 2008-12-23
Thanks for the advise. I have found a good solution that partly fixes the problem. For downloads I now use Download Sentinal ++ which is leech protection software. It uses tokens to ensure that a file can only be downloaded once per token. And also it enabled files to be sorted in a non public directory so there is no way a user can access them. This has already saved me a hell of a lot of bandwidth. However im still getting a few users repeatedly trying to download even the token becomes invalid after a few seconds. This causes them to repeatedly hit an error page again using bandwidth & resources (even though its only a fraction of previous attacks). So the next stage is flood protection to block users that repeatedly connect to the server 1000's of times.

---

### Post by hivltg on 2008-12-23
so fail2ban can monitor the apache access log to ban an ip that floods the server?....edit: yes it can

---

### Post by cdenley on 2008-12-23
> **hivltg said:**
> so fail2ban can monitor the apache access log to ban an ip that floods the server? I can only find info on the site about brute forcing passwords.

It filters based on any logged event with an IP address and time associated with it which you create a regex for. If you post an example of the apache event which you want to result in a ban if it happens too frequently, I might be able to walk you through it.

---

### Post by hivltg on 2008-12-23
Thanks. Here is an example of my apache access log. This is just a few lines. but i end up with 1000's of these in on session

```
115.132.6.161 - - [23/Dec/2008:04:11:59 -0800] "GET /dsplus/ds.php?p=MechCommander2.zip&t=YTo0OntzOjQ6InRpbWUiO2k6MTIyOTk5MjAwODtzOjQ6Imhhc2giO3M6NDA6ImNmNTczYjc0M2ExOWI2NDA3NGQ5ZDE4YmMzMWE2MDk2ZjE1N2Y2YTQiO3M6NjoiY3Rva2VuIjtzOjMyOiIwZGQyYWExOGI4OGU3MDlkZGM1ZmY2N2RmNmZmNmI3NiI7czo2OiJzdG9rZW4iO3M6MzI6ImNlM2U1YTdmMDJiZWRlODlkNzMwZWFmZGVlNGMzZTUyIjt9 HTTP/1.1" 416 492 "http://85.17.58.187/dsplus/m.php?p=MechCommander2.zip" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/525.19 (KHTML, like Gecko) Chrome/1.0.154.36 Safari/525.19"
115.132.6.161 - - [23/Dec/2008:04:12:00 -0800] "GET /dsplus/ds.php?p=MechCommander2.zip&t=YTo0OntzOjQ6InRpbWUiO2k6MTIyOTk5MjAwODtzOjQ6Imhhc2giO3M6NDA6ImNmNTczYjc0M2ExOWI2NDA3NGQ5ZDE4YmMzMWE2MDk2ZjE1N2Y2YTQiO3M6NjoiY3Rva2VuIjtzOjMyOiIwZGQyYWExOGI4OGU3MDlkZGM1ZmY2N2RmNmZmNmI3NiI7czo2OiJzdG9rZW4iO3M6MzI6ImNlM2U1YTdmMDJiZWRlODlkNzMwZWFmZGVlNGMzZTUyIjt9 HTTP/1.1" 416 492 "http://85.17.58.187/dsplus/m.php?p=MechCommander2.zip" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/525.19 (KHTML, like Gecko) Chrome/1.0.154.36 Safari/525.19"
115.132.6.161 - - [23/Dec/2008:04:12:00 -0800] "GET /dsplus/ds.php?p=MechCommander2.zip&t=YTo0OntzOjQ6InRpbWUiO2k6MTIyOTk5MjAwODtzOjQ6Imhhc2giO3M6NDA6ImNmNTczYjc0M2ExOWI2NDA3NGQ5ZDE4YmMzMWE2MDk2ZjE1N2Y2YTQiO3M6NjoiY3Rva2VuIjtzOjMyOiIwZGQyYWExOGI4OGU3MDlkZGM1ZmY2N2RmNmZmNmI3NiI7czo2OiJzdG9rZW4iO3M6MzI6ImNlM2U1YTdmMDJiZWRlODlkNzMwZWFmZGVlNGMzZTUyIjt9 HTTP/1.1" 416 492 "http://85.17.58.187/dsplus/m.php?p=MechCommander2.zip" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/525.19 (KHTML, like Gecko) Chrome/1.0.154.36 Safari/525.19"
115.132.6.161 - - [23/Dec/2008:04:12:00 -0800] "GET /dsplus/ds.php?p=MechCommander2.zip&t=YTo0OntzOjQ6InRpbWUiO2k6MTIyOTk5MjAwODtzOjQ6Imhhc2giO3M6NDA6ImNmNTczYjc0M2ExOWI2NDA3NGQ5ZDE4YmMzMWE2MDk2ZjE1N2Y2YTQiO3M6NjoiY3Rva2VuIjtzOjMyOiIwZGQyYWExOGI4OGU3MDlkZGM1ZmY2N2RmNmZmNmI3NiI7czo2OiJzdG9rZW4iO3M6MzI6ImNlM2U1YTdmMDJiZWRlODlkNzMwZWFmZGVlNGMzZTUyIjt9 HTTP/1.1" 416 492 "http://85.17.58.187/dsplus/m.php?p=MechCommander2.zip" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/525.19 (KHTML, like Gecko) Chrome/1.0.154.36 Safari/525.19"
115.132.6.161 - - [23/Dec/2008:04:12:00 -0800] "GET /dsplus/ds.php?p=MechCommander2.zip&t=YTo0OntzOjQ6InRpbWUiO2k6MTIyOTk5MjAwODtzOjQ6Imhhc2giO3M6NDA6ImNmNTczYjc0M2ExOWI2NDA3NGQ5ZDE4YmMzMWE2MDk2ZjE1N2Y2YTQiO3M6NjoiY3Rva2VuIjtzOjMyOiIwZGQyYWExOGI4OGU3MDlkZGM1ZmY2N2RmNmZmNmI3NiI7czo2OiJzdG9rZW4iO3M6MzI6ImNlM2U1YTdmMDJiZWRlODlkNzMwZWFmZGVlNGMzZTUyIjt9 HTTP/1.1" 416 492 "http://85.17.58.187/dsplus/m.php?p=MechCommander2.zip" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/525.19 (KHTML, like Gecko) Chrome/1.0.154.36 Safari/525.19"

```

---

### Post by cdenley on 2008-12-23
First, you obviously have to install fail2ban.
```

sudo apt-get install fail2ban

```

then, create your filter
/etc/fail2ban/filter.d/leech.conf
```

[Definition]
failregex = ^<HOST> -.*\] "GET /dsplus/ds.php\?p=
ignoreregex =

```
This filter will match all "GET" requests for a URI starting with "/dsplus/ds.php?p=". Next you need to implement this filter by adding this to the file /etc/fail2ban/jail.conf
```

[leech]
enabled = true
port    = http,https
filter  = leech
logpath = /var/log/apache2/access.log
bantime  = 600
maxretry = 3

```
Now, simply restart fail2ban, and you're ready to go.
```

sudo /etc/init.d/fail2ban restart

```

---

### Post by hivltg on 2008-12-23
That was surprisingly easy to do. Thank you very much. I will let you know if I no longer get problems in a few days.

---

### Post by HermanAB on 2008-12-23
This is what the rate limit module in iptables is for:


# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit
-burst 5 -j ACCEPT


I have that on all my servers.


Cheers,

Herman

---

### Post by cdenley on 2008-12-23
> **HermanAB said:**
> This is what the rate limit module in iptables is for:


# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit
-burst 5 -j ACCEPT

Since he wants to block people who download files too many times, I don't think that would work. The user's browser would re-use the same connection for each download. If he wanted to stop a script which kept trying to establish a new connection then download the file, then that would work. As far as I can tell, that is not the case.

---

