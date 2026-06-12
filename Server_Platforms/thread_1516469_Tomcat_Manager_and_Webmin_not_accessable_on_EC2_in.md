---
title: "Tomcat Manager and Webmin not accessable on EC2 instance"
date: 2010-06-23
forum: Server Platforms
---

### Post by john4 on 2010-06-23
I've got my first EC2/cloud instance of Ubuntu up and running.  This is my first time really dealing with the server edition...

I've loaded Apache, Tomcat, PostgreSQL, and Webmin. I've got a public IP on the instance and it is working. I've opened, for now, ports 80, 8080, 443, and 10000 to 0.0.0.0/0.

I cannot get into Tomcat Manager or Webmin..... at all through a browser. For Tomcat, I've restarted, stop/started, and verified that Tomcat is running. I installed Webmin all through apt-get commands so any dependencies should have been installed (first time doing it this way), but cannot get to the login screen. But if I just go to the IP, Apache goes to the "It Works..." splash page.

Did I miss some set up? Is there an internal firewall in Ubuntu Server edition that needs to be set?

Thank you,

John

---

### Post by john4 on 2010-07-05
If I were a Loony Toon I'd turn into an *** right now. ID10T error....Helps when you uncomment the Tomcat Users and not user illegal characters in the passwords so and Tomcat will start. And it also helps to run the webmin start command (sudo /etc/init.d/webmin start).

---

