---
title: "Ubuntu server, XP client won't connect"
date: 2009-03-03
forum: Server Platforms
---

### Post by rogere on 2009-03-03
I volunteer at a local charity and I offered (foolishly) to work toward implementing a web server.  I am less than a newbie at Linux, servers, everything.   Counselors use Windows XP Pro so the client machines are Windows XP Pro.  We want this server to be only intranet with no connection needed to the outside world.  (Our first use of this server would be to share a calendar).  All the computers, including the server, are connected to a Belkin 54g router.  I installed the latest Ubuntu server edition in a partition on a P4 desktop.

The virtual server section of the Belkin router is set to allow a private IP of 192.168.2.4 port 80, both inbound and outbound

In accordance with what I had read somewhere, I changed the interfaces file
sudo vi /etc/network/interfaces
I changed it from:
auto eth0
iface eth0 inet dhcp
to read:
auto eth0
iface eth0 inet static
        address 192.168.2.4
        netmask 255.255.255.0
 I ping that IP from another computer on the Belkin router and it works.  I open a browser on one of the client XP machines with [http://192.168.2.4](http://192.168.2.4) and it comes back with “It works!”

But when I try to setup a network place in Windows, it fails.  In the dialog box that asks for the internet or network address, I type [http://192.168.2.4/logs](http://192.168.2.4/logs)
Another dialog box opens that asks for username and password.  I input the username and password I used to setup Ubuntu.  Upon enter, the password is erased.  No go.  The access log file reads PROPFIND/logs HTTP 1.1 405 306 and I don’t know what that means.  The error log file lists nothing for that attempt.  I would greatly appreciate any help.

---

### Post by volkswagner on 2009-03-03
Try the following syntax in the address.

file://192.168.2.4///logs/

or

file://192.168.2.4///home/username/

Not http://


EDIT: Duh.... I just realized the above only works on local machines.  Sorry.

---

### Post by volkswagner on 2009-03-04
Sorry about my first post.

Does the folder or file /var/www/logs exist?

When you enter ip address of the server and get "it works", that is the default site, located in /var/www/

If you want to be able to browse folders you will need to move them to /var/www/ or change the config file to reflect the root folder of your choice.

```
sudo nano /etc/apache2/sites-available/default
```

DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>


After changing the DocumentRoot and <Directory /var/www/> then restart apache
```

sudo /etc/init.d/apache2 reload
```

There may be better ways for connecting to the server than http:, you could use ftp, or[ LDAP]("http://www.openldap.org/")


What functions are you looking for?

---

### Post by happyhacker on 2009-03-04
Surely, if you've accessed www folder the the reply is from Apache server. You don't want that for file sharing. Have you setup the workgroups?

---

