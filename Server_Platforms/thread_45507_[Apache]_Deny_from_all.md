---
title: "[Apache] Deny from all"
date: 2005-06-30
forum: Server Platforms
---

### Post by EcliptuX on 2005-06-30
Hi,

I try to setting up my apache server but I can't do a simple thing.

Apache2 is running and when I go to [http://192.168.0.1](http://192.168.0.1) (my apache server) from another computer (192.168.0.2), the Apache presentation page load.
OK :)

Now, I wan't to deny access from all !
In the documentation, I find this : edit the /etc/apache2/apache2.conf file and insert at the end theses ligns :
 ```
<Directory /var/www/>
order deny,allow
deny from all
</Directory>
``` 
I did it, but nothing appends :(
The access from 192.168.0.2 still working :(
What's wrong ?

---

### Post by LordHunter317 on 2005-06-30
Did you reload the apache configuration after making the change?
On the client, Did you hit F5 to force a page refresh?

---

### Post by EcliptuX on 2005-06-30
[QUOTE=LordHunter317]Did you reload the apache configuration after making the change?
On the client, Did you hit F5 to force a page refresh?[/QUOTE]
Yes for the both

---

### Post by LordHunter317 on 2005-06-30
Oh, heh, I'm a retard.  It's being overriden by the vhost configuration.

Remove it from /etc/apache2/apache2.conf and place it in /etc/apache2/sites-enabled/000-default.

---

### Post by EcliptuX on 2005-06-30
[QUOTE=LordHunter317]Oh, heh, I'm a retard.  It's being overriden by the vhost configuration.

Remove it from /etc/apache2/apache2.conf and place it in /etc/apache2/sites-enabled/000-default.[/QUOTE]
Thank a lot !
In fact, the good file to edit was /etc/apache2/sites-enabled/000-default

That's working now ;)

---

