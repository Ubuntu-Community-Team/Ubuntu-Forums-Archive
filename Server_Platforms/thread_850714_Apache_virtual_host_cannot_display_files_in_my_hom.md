---
title: "Apache virtual host cannot display files in my home directory"
date: 2008-07-05
forum: Server Platforms
---

### Post by ctc on 2008-07-05
I'm trying to test some websites locally, and I'm having a problem with virtual hosts.

The following is the contents of /etc/apache2/sites-available/default on my machine. When I use the file as listed below, I can access both of these sites without a problem.

```

NameVirtualHost 127.0.0.1

<VirtualHost 127.0.0.1>
   ServerName localhost-pennridgebbb.com
   DocumentRoot /var/www/pennridgebbb.com/
</VirtualHost>

<VirtualHost 127.0.0.1>
   ServerName localhost-christophertcressman.com
   DocumentRoot /var/www/christophertcressman.com/
</VirtualHost>

```

When I change the DocumentRoot to directories within my home directory, as listed below, I get 403 Forbidden errors when trying to access the sites.

```

NameVirtualHost 127.0.0.1

<VirtualHost 127.0.0.1>
   ServerName localhost-pennridgebbb.com
   DocumentRoot /home/chris/projects/pennridgebbb.com/
</VirtualHost>

<VirtualHost 127.0.0.1>
   ServerName localhost-christophertcressman.com
   DocumentRoot /home/chris/projects/christophertcressman.com/
</VirtualHost>

```

How can I make the second example work? Thanks in advance for your help with this.

---

### Post by windependence on 2008-07-05
This is because of ownership and permissions issues with that directory. You wuld probably be better off creating a symlink to /home/chris/projects/pennridgebbb.com/ and /home/chris/projects/christophertcressman.com/ in your normal apache root directory, typically /var/www.

Do it like this:

```
ln -s /home/chris/projects/christophertcressman.com /var/www//home/chris/projects/christophertcressman.com

ln -s /home/chris/projects/pennridgebbb.com /var/www//home/chris/projects/pennridgebbb.com
```

You still need to change ownership of the link to the ownership of the Apache files and also change your permissions to something like 775.

-Tim

---

### Post by elithrar on 2008-07-06
> **ctc said:**
> 
When I change the DocumentRoot to directories within my home directory, as listed below, I get 403 Forbidden errors when trying to access the sites.


Apache is running as the user [FONT="Courier New"]www-data[/FONT] in the group [FONT="Courier New"]www-data[/FONT], by default. I'm going to hazard a guess and say that the permissions on your [FONT="Courier New"]/home/chris/projects/pennridgebbb.com/[/FONT] & [FONT="Courier New"]/home/chris/projects/christophertcressman.com/[/FONT] directories are something like [FONT="Courier New"]chris:chris[/FONT] (user:group). Try this from your home directory: [FONT="Courier New"]sudo chown -R chris:www-data projects/ [/FONT]- which will give Apache the permissions it needs to serve files in both your [FONT="Courier New"]DocumentRoot[/FONT]s.

---

### Post by ctc on 2008-07-06
@windependence and @elithrar:
Thanks for your responses. Both helped to create my solution. I decided to keep my website files in /var/www, where everything works, and then add a symlink in my home directory to make the files easier to access and back up.

---

### Post by mbeach on 2008-07-06
I know you have a solution thats working for you, but if you wanted to go the debian way, you would have two files in your /etc/apache2/sites-available folder.  One named default (which was there when you installed Apache) and another one named whatever you like, say ctc.com

in default you'd have the parts for pennridgebbb:
<VirtualHost 127.0.0.1>
   ServerName localhost-pennridgebbb.com
   DocumentRoot /home/chris/projects/pennridgebbb.com/
</VirtualHost>

and in ctc.com you'd have the parts for locahost_ctc.com
<VirtualHost 127.0.0.1>
   ServerName localhost-christophertcressman.com
   DocumentRoot /home/chris/projects/christophertcressman.com/
</VirtualHost>

then, you'd enable the ctc.com site by doing
sudo a2ensite ctc.com

you would have to still change the permissions or ownership of the files in /home/chris/projects/christophertcressman.com/ so www-data can read them as provided in elithrar's post.  I'd do it like:
sudo chown -R chris:www-data /home/chris/projects/
sudo chmod -R g+r /home/chris/projects/

the last statement will ensure that the group can read the files.  Since www-data is the group, and assuming that www-data is the user running apache you should be good to go.

some reference:
[http://www.debian-administration.org/articles/207](http://www.debian-administration.org/articles/207)

---

