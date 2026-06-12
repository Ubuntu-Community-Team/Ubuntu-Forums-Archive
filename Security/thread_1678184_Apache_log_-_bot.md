---
title: "Apache log - bot?"
date: 2011-01-29
forum: Security
---

### Post by ene_dene on 2011-01-29
Hello, I have a small site on my computer and recently I wanted to check how many people connect, and I found this strange part:
```
79.170.40.180 - - [18/Jan/2011:10:11:58 +0100] "POST /index.php HTTP/1.0" 200 4831 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:12:00 +0100] "POST /index.php HTTP/1.0" 200 4929 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:12:00 +0100] "POST /index.php HTTP/1.0" 200 4930 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:12:00 +0100] "POST /index.php HTTP/1.0" 200 4930 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:12:25 +0100] "POST /index.php HTTP/1.0" 200 4831 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:12:26 +0100] "POST /index.php HTTP/1.0" 200 4929 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:12:26 +0100] "POST /index.php HTTP/1.0" 200 4930 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:12:26 +0100] "POST /index.php HTTP/1.0" 200 4929 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:13:29 +0100] "POST /index.php HTTP/1.0" 200 4831 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:13:29 +0100] "POST /index.php HTTP/1.0" 200 4929 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:13:30 +0100] "POST /index.php HTTP/1.0" 200 4930 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:13:30 +0100] "POST /index.php HTTP/1.0" 200 4930 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:14:33 +0100] "POST /index.php HTTP/1.0" 200 4831 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:14:33 +0100] "POST /index.php HTTP/1.0" 200 4928 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:14:33 +0100] "POST /index.php HTTP/1.0" 200 4929 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:14:34 +0100] "POST /index.php HTTP/1.0" 200 4930 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:14:41 +0100] "POST /index.php HTTP/1.0" 200 4831 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:14:41 +0100] "POST /index.php HTTP/1.0" 200 4929 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:14:41 +0100] "POST /index.php HTTP/1.0" 200 4930 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:14:41 +0100] "POST /index.php HTTP/1.0" 200 4930 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:15:16 +0100] "POST /index.php HTTP/1.0" 200 4830 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:15:16 +0100] "POST /index.php HTTP/1.0" 200 4928 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:15:16 +0100] "POST /index.php HTTP/1.0" 200 4929 "-" "Snoopy v1.2.4"
79.170.40.180 - - [18/Jan/2011:10:15:16 +0100] "POST /index.php HTTP/1.0" 200 4929 "-" "Snoopy v1.2.4"
```
This appears every few hours, and it lasts for couple of minutes. For two weeks now. Now I've banned the IP. Is that some kind of a bot, for what purpose? I didn't feel any connection troubles.

---

### Post by uRock on 2011-01-29
Snoopy 1.2.4 does appear to be a bot. The question is, "How did it get installed?"

The code for this bot is listed here. [http://www.indomp3z.us/showthread.php/104469-Snoopy-1.2.4-The-PHP-Grabber-Script](http://www.indomp3z.us/showthread.php/104469-Snoopy-1.2.4-The-PHP-Grabber-Script)

The code is present for download via sourceforge.com. [http://sourceforge.net/projects/snoopy/files/Snoopy/](http://sourceforge.net/projects/snoopy/files/Snoopy/)

---

### Post by clasificados on 2011-01-30
route add 
route add 79.170.40.180 gw 127.0.0.1 lo
banned

---

### Post by ene_dene on 2011-01-30
"Snoopy is a PHP class that simulates a web browser. It automates the task of retrieving web page content and posting forms, for example."

I can't understand what is its purpose on my web site? It has only few forms where you put numbers and it calculates the results back, it's a very simple site.

You can check it:
[http://asicalculator.no-ip.info](http://asicalculator.no-ip.info)

It obviously uses my domain name, because I have dynamic IP address.

---

### Post by OpSecShellshock on 2011-01-30
> **ene_dene said:**
> "Snoopy is a PHP class that simulates a web browser. It automates the task of retrieving web page content and posting forms, for example."

I can't understand what is its purpose on my web site? It has only few forms where you put numbers and it calculates the results back, it's a very simple site.

You can check it:
[http://asicalculator.no-ip.info](http://asicalculator.no-ip.info)

It obviously uses my domain name, because I have dynamic IP address.

Every site on the open web potentially has value to attackers. A compromised page can be used to spread malware, host phishing pages, advertise, or even attack other servers. One of the main attack vectors when someone wants to compromise a site are user input fields. Basically there are some insecure setups that don't validate user inputs properly and as such allow, for example, SQL code to be parsed, or allow code from a specified remote site to be executed within the context of the victim site's web application. My guess is that's what your friends are trying to do. Of course, another possibility is that someone is using your application via an automated script to perform a bunch of calculations. Can't really tell without seeing the content of packet captures.

---

### Post by ene_dene on 2011-01-30
OK,thank you for your answers. I've banned the IP in my firewall.

I don't think there is much he can do, it's just some simple php, few functions that multiply numbers, no database.

---

### Post by Delerium69 on 2011-02-01
> **OpSecShellshock said:**
> Of course, another possibility is that someone is using your application via an automated script to perform a bunch of calculations. Can't really tell without seeing the content of packet captures.

Nail on the head, Im now embarrassed to say im the guy thats behind this. I hadn't realised that it had caused some issues for your site, im truley sorry. I've sent you a PM explaining the purpose of the scripts. Again, apologies for the panic this may have caused.

James

---

### Post by ene_dene on 2011-02-01
It's a story with happy ending. It's not a bot but a script from a user that automated the process. No harm done, IP ban was removed.

---

