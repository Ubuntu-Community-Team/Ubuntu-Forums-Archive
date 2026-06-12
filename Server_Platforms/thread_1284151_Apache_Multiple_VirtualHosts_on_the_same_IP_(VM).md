---
title: "Apache Multiple VirtualHosts on the same IP (VM)"
date: 2009-10-06
forum: Server Platforms
---

### Post by BassKozz on 2009-10-06
I am running 64bit Ubuntu 9.04 Server, in Virtual Box.  I have installed the LAMP stack, and I am having a hard time getting VirtualHosts to work.  I have given the VM it's own static IP address (192.168.1.105) and I have given it the hostname "LAMPVM" via my router, and when I try to access it from my browser it only goes to 1 domain at a time.

I have "vhost_alias" & "rewrite" enabled.

I have my /etc/apache2/httpd.conf setup as follows:
```
<Directory "/home/USER/workspace">
        Options FollowSymLinks
        AllowOverride All

        Order allow,deny
        Allow from all
</Directory>

NameVirtualHost *
ServerName localhost
```

I have the following sites-enabled:
localhost:
```
<VirtualHost *>
        ServerName localhost
        ServerAlias localhost *.localhost
        VirtualDocumentRoot /home/USER/workspace/%1/
</VirtualHost>
```
test1:
```
<VirtualHost *>
        ServerName test1
        ServerAlias test1 *.test1
        DocumentRoot /home/USER/workspace/test1/
</VirtualHost>
```
test2:
```
<VirtualHost *>
        ServerName test2
        ServerAlias test2 *.test2
        DocumentRoot /home/USER/workspace/test2/
</VirtualHost>
```

And I enter "LAMPVM" into my browser it only goes to the most recent domain I added (test2).
If I enter "test1.LAMPVM" into my browser it doesn't find the address.
I realize this is because my DNS on my browsers machine (not the VM) is not configured to recognize what "test1.LAMPVM" means.  But when I enter the following into my /etc/hosts file:
```
127.0.0.1       localhost
127.0.1.1       my-machine

#LAMPVM
192.168.1.105 test1.lampvm
192.168.1.105 test2.lampvm
```
By browser goes to the address "test2.lampvm", but it thinks "test1.lampvm" is the same as "test2.lampvm" (or "test1.lampvm" is being routed to the most recently added domain [which happens to be test2]).
Again, I kinda get why this isn't working because both "test1.lampvm" and "test2.lampvm" are pointing to the same address (192.168.1.105), but that is the address of the VM, and I don't know how else to get access to multiple domains on the same VM/IP?

My guess is I probably need to make some adjustments in my Router, but not sure exactly what?
Any/All Help, Comments, Suggestions will be greatly appreciated.
-BassKozz

---

### Post by cdenley on 2009-10-06
First of all, you shouldn't be using httpd.conf. You should create vhost configurations in /etc/apache2/sites-available, then enable them with a2ensite. The default vhost should be /etc/apache2/sites-available/default. If your server is ubuntu 9.04, NameVirtualHost should only be used in /etc/apache2/ports.conf.

You seem to have the server names configured as test1, test2, etc., so why are you configuring your hosts file with test1.lampvm, test2.lampvm, etc.?

If you don't want to edit /etc/hosts or worry about browser caching or routing, you could use netcat to have full control over the http headers.
```

echo -e "GET / HTTP/1.0\nHost: test1\n"|nc localhost 80

```
Of course, make sure you reload apache after changing any vhost configuration.

Get apache working properly, then figure out routing.

---

