---
title: "Subdomain Configuration on Ubuntu nginx Server"
date: 2014-05-23
forum: Server Platforms
---

### Post by emrah3 on 2014-05-23
Hi,
  First of all, I'm sorry for my bad English. I'll try to explain my aim as much as possible.
  I'm using a 2 Core and 2 GB memory VPS with 1  dedicated ip address from Digital Ocean for my project. I'm using nginx  as a webserver, MySQL as a database server and bind as a dns server.
  My project is a free hosting platform for educational  purposes. I'll be teaching PHP and MySQL to students from my  neighbourhood and i want them to practice on their own subdomain with a  PHP and MySQL support.
  For example, my main domain name is : example.com I'll also setup a wildcard SSL for my domain.
  For example, student subdomain should be like this : student1.example.com
  Students will be able to activate their web space  with the subdomain they choose automatically using my setup script which  is writtern in PHP (a simple page).
  How can i achive this setup without using any control  panel like cPanel or zPanel? How can any subdomain which is choosen by a  student resolve my main domain?
  Can students use their own TLD domain on a setup like this?
  Do you have any suggestions for this kind of setup?
  Any help would be very much appreciated regarding this project.
  Kind Regards.

---

### Post by sandyd on 2014-05-24
> **emrah3 said:**
> Hi,
  First of all, I'm sorry for my bad English. I'll try to explain my aim as much as possible.
  I'm using a 2 Core and 2 GB memory VPS with 1  dedicated ip address from Digital Ocean for my project. I'm using nginx  as a webserver, MySQL as a database server and bind as a dns server.
  My project is a free hosting platform for educational  purposes. I'll be teaching PHP and MySQL to students from my  neighbourhood and i want them to practice on their own subdomain with a  PHP and MySQL support.
  For example, my main domain name is : example.com I'll also setup a wildcard SSL for my domain.
  For example, student subdomain should be like this : student1.example.com
  Students will be able to activate their web space  with the subdomain they choose automatically using my setup script which  is writtern in PHP (a simple page).
  How can i achive this setup without using any control  panel like cPanel or zPanel? How can any subdomain which is choosen by a  student resolve my main domain?
  Can students use their own TLD domain on a setup like this?
  Do you have any suggestions for this kind of setup?
  Any help would be very much appreciated regarding this project.
  Kind Regards.
Few things

You can setup bind9 to do wildcard, for example, use
```

*.example.com     IN      CNAME     example.com.
```
in a zone

Few things - would anyone be allowed to sign up? If so, the script would mean that anyone could sign up - even the bored hacker/abuser that may live next door to you or half a content away.

That being said, the script would have to do a few things
- Add a new user
- Create a php5-fpm pool for the user
- Create user home folder
- Add a subdomain for user in /etc/nginx.

---

