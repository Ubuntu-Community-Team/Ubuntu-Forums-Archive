---
title: "setting up my own Web Server - Need help"
date: 2007-08-27
forum: Server Platforms
---

### Post by stabface on 2007-08-27
I have been trying to setup  a ubuntu server from the office i work for. I am lucky and they granted me access to  my own IP address on the static T1 line. 

 - I have installed ubuntu  and everything is fine
 - i have installed ssh 
 - and webmin 
 - i have some experience with  apache and seems like its running right. 
 -  I have a domain registered through godaddy.com. 
 - I have created  custom name servers through godaddy's control panel that point to my IP Address. 
 - all of this is behind a  linksys router with ports 21, 22, 80 and 443 open and pointing at my server. 


- i can browse my server  if i enter the ip address.  it brings me the basic default  folder for apache. 

seems like everything is working right except  no matter what i do i can't domains to work. 
if i go to [www.mysite.com](www.mysite.com) then i get nothing but a bad page error. 

my question is do i need configure BIND9 or  is that what  godaddy.com is doing  when they create the ns1.mydomain.com 

i can provide any information to help get this fixed. i am sure it will help someone i the future  when they are setting up there server.

---

### Post by KCPokes on 2007-08-27
What part do you need help with?  If you have Ubuntu up and running, have you gone through setting up your basic LAMP architecture (linux, apache, mysql, and php)?

---

### Post by frego on 2007-08-28
sounds like you need to edit your /etc/hosts file and add an entry for your website, mapping it to your local IP address.  I assume you are using your ISP's DNS servers.  And it will resolve to the external IP adress of your modem, but this is only an issue for you on your LAN.  Those on the internet will likely see it just fine.  Your line would look something like this:

192.168.1.101     www.mynewdomain.com

Obviously substitute the correct values in your hosts file!

---

### Post by wirelessmonkey on 2007-08-28
What frego said, plus you need to make sure your apache config has the proper aliases and/or vhosts set up.

---

### Post by stabface on 2007-08-28
thanks for the posts, 

i am using my ISP's DNS servers. I think i might have my apache server setup wrong 

i am getting a strange error when i restart apache 

 sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of web server (apache2)...                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


could this be my problem? 

also  do i need to setup bind?   or will apache  do it on its own?

---

### Post by williehowe on 2007-08-28
If you're running your own DNS server you need port 53 forwarded to your Ubuntu box on that linksys.  <- Strike that

---

