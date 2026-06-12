---
title: "Server Help"
date: 2009-10-12
forum: Server Platforms
---

### Post by thescubadude on 2009-10-12
I have set up an old laptop with Ubuntu... I have installed Apache, MySql and phpMyAdmin...

I am just trying to figure out how I can set up the webserver so that I can access it through my network with my two other pc's. One with Win XP, one with Vista. I want to be able to access and external drive on the Ubuntu pc and access the server through my web browser. i am new to both Ubuntu and networking so any help, preferable in laymans terms, with step by step explanations /help would be great. 

I would also like to be able to access MySQL with Query Browser through the two windows pcs.

thanks in advance.

---

### Post by BQAggie2006 on 2009-10-12
> I am just trying to figure out how I can set up the webserver so that I can access it through my network with my two other pc's.Since you already installed Apache, this should already be working. All you have to do is point a browser on your PCs to the IP address of the laptop/webserver. If you are not sure what the IP address of your laptop is, go to the command line on the laptop and run the following command:

```
ifconfig -a
```and look for the inet addr assigned to eth0.

> I want to be able to access and external drive on the Ubuntu pcCould you please clarify this? Is the external drive attached to the Ubuntu machine and you would like to share it over your network or is it attached to another computer on your network and you would like to access it from the Ubuntu machine?

> I would also like to be able to access MySQL with Query Browser through the two windows pcs.Just configure the connection for the Query Browser with the laptop's IP address from above and the username and password you configured for MySQL when you installed it.

---

### Post by kpholmes on 2009-10-12
you said you installed phpadmin, but make sure to install php its self, 

have you looked into the possibilities of a samba server?

but if you want to use a browser, then just install ftpd server on the machine that will have the external hd, share it 
(hd) with samba, and use firefox to log in to the network via ftp, or just that one computer, and get your files.



that might help, dont know though. theres a lot you can do with linux. 
just got to find out what works for you :P

---

### Post by thescubadude on 2009-10-13
The external drive will be attached to the Ubuntu machine. I would ideally like to create virtual hosts  in apache on the external drive and then have the two pc's work off this drive.

Also how would I set up a static ip for the server. I have a linksys router that is assigning ip's but would like to ensure the server always has the same ip.

---

### Post by BQAggie2006 on 2009-10-14
Here are a few guides to help you set up virtual hosts in apache:
[https://help.ubuntu.com/9.04/serverguide/C/httpd.html](https://help.ubuntu.com/9.04/serverguide/C/httpd.html)
[http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)
 
Here is a guide to help you set a static IP address:
[https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html)

---

### Post by thescubadude on 2009-10-14
thanks for all the help and links.

---

### Post by SteveHillier on 2009-10-18
> **thescubadude said:**
> I have set up an old laptop with Ubuntu... I have installed Apache, MySql and phpMyAdmin...

I am just trying to figure out how I can set up the webserver so that I can access it through my network with my two other pc's. One with Win XP, one with Vista. I want to be able to access and external drive on the Ubuntu pc and access the server through my web browser. i am new to both Ubuntu and networking so any help, preferable in laymans terms, with step by step explanations /help would be great. 


I have come to this thread late and you may well be up and running by now but this is something I have done recently.

It does not matter whether your host is on a Linux box or a Windows box because this is something you might have to do on your windows machines.

Similar to Linux these also have a hosts file.

On XP it can be found on [%SYSTEMROOT]\drivers\etc where %systemroot is normally C:\Windows\System32.

The hosts file is a simple text file and you need to add lines at the end of the file (using your local ip addresses obviously), (the first line will already be there)

```
127.0.0.1       localhost
77.76.100.82    test2.hcdemo.net
77.76.100.82    test3.hcdemo.net
77.76.100.81    store.hcdemo.net
```

The IP addresses can equally be local addresses rather than public addresses.

I am just being lazy here.  I don't want to register my test domains but they exists on a remote server so this kludge gets round that for me.

On Vista machines the hosts file is in a similar place but you have to be logged on as an administrator and even allowing for UAC to permit access or even clicking on the 'notepad' icon and running as administrator you will not be able to write your amended file back to the original location so make sure you LOGON as administrator.

For the Linux help I bow to the greater minds than mine who have already responded.

---

### Post by thescubadude on 2009-10-31
[FONT=Arial][SIZE=2]Thanks everyone for all the help! I thought I'd let you know what I did. Putting everything in one place.

The first thing was to set up apache, php, mysql and phpmyadmin

Install LAMP Server 

[/SIZE][/FONT]**sudo tasksel install lamp-server**

I got this error when restarting apache: 
*apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for [ServerName]("https://help.ubuntu.com/community/ServerName")*

to fix it I had to do the following:
**echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn**This info came from here:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[FONT=Arial][SIZE=2] I then also installed imagemagick

[B]sudo aptitude update
sudo aptitude install imagemagick
[/B][/SIZE][/FONT]**sudo /etc/init.d/apache2 restart**
[FONT=Arial][SIZE=2] Install phpmyadmin

[B]sudo apt-get install phpmyadmin

[/B]My phpmyadmin was not working at this point and I had to do the following:[/SIZE][/FONT][B]
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
sudo /etc/init.d/apache2 reload[/B]

Found this info here:
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)
[FONT=Arial][SIZE=2] 
I thought I needed a fixed IP but I discovered I did not need a fixed ip address as I am only accessing my server internally and the router always assigns the server the same ip address.

In the terminal I typed: ifconfig -a

I then looked for etho0, inetaddress and got the ip address assigned to the linux pc. I found that if I restart either my pc or the router the ip address always remained the same.

As my network is only 3 pc's I've done the following.

On my windows pc's I've adjusted the host file (windows>system32>drivers>etc) to point to my linux box.

so linux ip: 
192.168.1.8       webserver
192.168.1.8       testsite1.ex

etc

This way when I type webserver or testsite1.ex into my browser I get my web pages. I do this for each virtual site I am creating.

For the sharing I used SAMBA - I didn't use a static ip but just point my pc at the samba share!

To set up the samba share this tutorial was excellent:

[/SIZE][/FONT][http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[FONT=Arial][SIZE=2]
To access or share my external I needed to access /media/nameofmydrive/ then when I access through windows I look for the network pc/myfiles. I shared the entire drive but I could easily share just a specific folder by /media/mydrivename/myfoldername/

[MyFiles]
 path = /media/samba/
 browseable = yes
 read only = no
 guest ok = no
 create mask = 0644
 directory mask = 0755
 force user = YOUR_USERNAME
 force group = YOUR_USERGROUP


To set up the virtual hosts (do this for each virtual host):

[B]cd /etc/apache2/sites-available
[/B]**sudo gedit testsite1.ex.conf**

Add this to the conf file & save:

[/SIZE][/FONT]     [FONT=Arial][SIZE=2]<VirtualHost *:80>[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]      ServerName testsite1.ex[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]        DocumentRoot /media/myexternaldrivename/myrootfoldername/mysitefoldername[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]        <Directory />[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]                Options FollowSymLinks[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]                AllowOverride All[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]        </Directory>[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]        <Directory /media/myexternaldrivename/myrootfoldername/mysitefoldername>[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]                Options Indexes FollowSymLinks MultiViews[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]                AllowOverride All[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]                Order allow,deny[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]                allow from all[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]        </Directory>[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]</VirtualHost>[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]

**sudo gedit /etc/hosts**

127.0.0.1        localhost 
127.0.0.1  webserver 
127.0.0.1  testsite1.ex

Enable the new virtual host:

**sudo a2ensite [B]testsite1.ex.conf**[/B]

Reload apache:

[B]sudo /etc/init.d/apache2 reload

[/B]If I need to disable a virtual host:[B]

sudo a2dissite [/B][/SIZE][/FONT][FONT=Arial][SIZE=2]**[B]testsite1.ex.conf**[/B][/SIZE][/FONT][FONT=Arial][SIZE=2]

I think that's it.

[/SIZE][/FONT]

---

