---
title: "Apache not working..please help"
date: 2012-12-03
forum: Server Platforms
---

### Post by lollylegs on 2012-12-03
i have done everything possible and looked at many tutorials regarding
setting up apache.
A year ago i set it up easily with same system except now i have new motherboard (know this might be irrelevant but I tried everything). i am still with same isp so not being blocked.
have disabled firewall.

ihave tried to set it up on both windows7(aag!) & ubuntu 12.04 using lamp while installing'.

PROBLEM: can't access apache index.html 'It Works' 

this time i haven't changed anything trying to make it work. because i will rely on one of you kind people to help.

apache running OK & listening on port 80
hosts file ok

the only query i have is what do i put ServerName as? localhost or marea-pc the name of my computer during set up

Hope someone can help me
Regards Marea
AUstralia

---

### Post by lisati on 2012-12-03
Is port 80 properly forwarded to the correct machine on your router?

---

### Post by lollylegs on 2012-12-03
thank you for answering my query.
I didn't know i had to. How do I do this please.

---

### Post by lollylegs on 2012-12-04
I accidently found out that apache is using my machine ip 10.0.0.1 instead of localhost or 127.0.0.1.
What can I do to rectify it, because I am new to ubuntu's file system as well as not really knowing how to setup Apache.
Thank you for any help
Regards Marea

---

### Post by Rakeshvijayan on 2012-12-04
Dont worry dear 

it will work for you .

I am not working with lamp .I manually install all packages separately for my server ,I hope I can help you to resolve this issuse 

1 st check apache configured correctly by using 127.0.0.1 on your browser (if it show index page works ) your apache configuration is correct 

2nd check the virtual host file on apache that uses port 80  and httpd.conf file on apache port 80 is enabled there 

3rd you need to add your system ip address on hostname with you desired name of webpage

---

### Post by lollylegs on 2012-12-04
Thank you Rakeshvijayan for helping;
I have done all that you said, but still cannot get apaches 'Its working'
with localhost or 127.0.0.1 only with 10.0.0.1 which is my machine gateway address.

Because I ame new to both ubuntu and apache dont know how to solve it.

regards Marea
Australia

---

### Post by Toriku on 2012-12-04
As Lisati pointed out, you need to have Port 80 forwarded to the machine running Apache, this will make your apache websites visible to the internet, you need to configure the Port Forwarding on your router to do this.
 Before you do this however, it should be possible to view your website from another computer on the network, by putting the local IP address to the machine with the apache server, into the address bar in the web browser.

 If you can access it from another computer on the network your apache is working fine, are you running Ubuntu server or are you running a Desktop version?

---

### Post by Rakeshvijayan on 2012-12-04
> **Toriku said:**
> As Lisati pointed out, you need to have Port 80 forwarded to the machine running Apache, this will make your apache websites visible to the internet, you need to configure the Port Forwarding on your router to do this.
 Before you do this however, it should be possible to view your website from another computer on the network, by putting the local IP address to the machine with the apache server, into the address bar in the web browser.

 If you can access it from another computer on the network your apache is working fine, are you running Ubuntu server or are you running a Desktop version?

let me know one thing 

Do you want to publish your site on web or lan ? 
if you want to publish this on your lan ,just type the ip address of your apache server on other machine .
  [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp) use this site to configure apache 

virtual host file is main thing for call web site in specified  port 

ok see you 2moro

---

