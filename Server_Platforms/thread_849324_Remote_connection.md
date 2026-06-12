---
title: "Remote connection"
date: 2008-07-04
forum: Server Platforms
---

### Post by Nirva on 2008-07-04
Hay,

I have a little problem.
I have a LAMP server running on my Ubuntu-box.
Untill some days I could connect to both my apache-server and my MySQL-Database from other computers on our LAN.  But today I can't do this anymore.  The server is running, because I can connect to apache through [http://localhost](http://localhost)
I don't know why, I haven't changed anything that I know of.
Can someone please help me ?

Thanks

---

### Post by jombeewoof on 2008-07-04
is your server DHCP?
check ifconfig to see if the IP has changed.

If not that, make sure apache is still set to use eth0 (or whatever your interface is) and that the server can access (via ping) the internet.

---

### Post by Nirva on 2008-07-04
The server is DHCP, but the IP-adress is OK.
The server is connected to the internet, but I'm not sure if it is set to listen to eth1 ( as it should be ) where can I check this ?

---

### Post by jombeewoof on 2008-07-04
in /etc/apache2/ports.conf

you will see
```
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

```
Try changing that to 

```
Listen 192.168.0.1:80

<IfModule mod_ssl.c>
    Listen 192.168.0.1:443
</IfModule>

```
assuming 192.168.0.1 is your IP

got this info from [http://httpd.apache.org/docs/2.0/bind.html](http://httpd.apache.org/docs/2.0/bind.html)

---

### Post by Nirva on 2008-07-04
Thanks for helping me, but that didn't work out to well.
I tried changing my ports.conf, but when I did ( as you told ) apache couldn't restart anymore.
This was the error-message : 

apache2: Syntax error on line 192 of /etc/apache2/apache2.conf: Syntax error on line 4 of /etc/apache2/ports.conf: Expected </IfModule> but saw </IfModule>/etc/apache2/ports.con>

---

### Post by furlabs on 2008-07-05
Apache is telling you what the problem is. It's expecting </IfModule> but instead the file says </IfModule>/etc/apache2/ports.con>.  You probably right-clicked by accident and pasted what was in your clipboard.

Edit /etc/apache2/ports.conf again and go to line 192 (if you are using vim, press ESC :192 ENTER)

Make sure this line says </IfModule> and nothing else, save and quit, then restart apache.

---

