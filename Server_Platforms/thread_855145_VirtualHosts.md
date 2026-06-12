---
title: "VirtualHosts"
date: 2008-07-10
forum: Server Platforms
---

### Post by antilog on 2008-07-10
I am setting up virtualhosts.  
given:
ubuntu 8.04.1
apache2
virtualhosts > 3 domains
DNS resolution successful

Say I am running foo1.com, foo2.com and foo3.com.
foo2 and foo3 are displaying foo1's index.

The first lines of all my sites-available files (including default):
```
#NameVirtualHost *
<VirtualHost *>
```

The bottom of my apache2.conf:
```

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

ServerName myserver.local


```

```
ls /etc/apache2/sites-enabled
000-default  foo1 foo2 foo3

```
```
ls /etc/apache2/sites-a*
antilog  foo1 foo2 foo3

```

Any ideas?

---

### Post by carcdrcdr on 2008-07-10
> I am setting up virtualhosts.
given:
ubuntu 8.04.1
apache2
virtualhosts > 3 domains
DNS resolution successful

Say I am running foo1.com, foo2.com and foo3.com.
foo2 and foo3 are displaying foo1's index.

Well I think you want this in your apache2.conf:
```
Listen 80
NameVirtualHost *:80

<VirtualHost *:80>
DocumentRoot /www/foo1
ServerName www.foo1.com
#blaw balw balw
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /www/foo2
ServerName www.foo2.com
#blaw balw balw
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /www/foo3
ServerName www.foo3.com
#blaw balw balw
</VirtualHost>

```
ok dude.  Now all we do is set up /etc/apache2/sites-available/foo1.com you are going to want something like this: (do this for foo1-3)
```
<VirtualHost *>
ServerName www.foo1.com
ServerAlias foo1.com
DocumentRoot /home/www/html/foo1.com/html
CustomLog logs/foo1-access_log common
</VirtualHost>
```

Ok now we need to enable the sucker by symlinking to /etc/apache2/sites-enabled
```
ln -s /etc/apache2/sites-available/foo1.com /etc/apache2/sites-enabled/foo1.com
```

Thats as far as i'll go... If your VHost setup is IP based you are going to want to change the <VirtualHost *:80> in my examples to your configuration. (So for IP based change the '*' to your ip and port based ':80' enjoy ;)

---

### Post by comandrei on 2008-07-10
Have you set the server name in every host file?
For example: in foo1 You need to have
```

<VirtualHost>
ServerName foo1.com
</VirtualHost>

```
Oops,carcdrcdr was faster. You can always
```

sudo a2ensite site_name

```
To enable sites. It's a shortcut for symlinking them

---

### Post by antilog on 2008-07-10
> **comandrei said:**
> Have you set the server name in every host file?
For example: in foo1 You need to have
```

<VirtualHost>
ServerName foo1.com
</VirtualHost>

```
Oops,carcdrcdr was faster. You can always
```

sudo a2ensite site_name

```
To enable sites. It's a shortcut for symlinking them

Yes.

---

### Post by antilog on 2008-07-10
> **carcdrcdr said:**
> Well I think you want this in your apache2.conf:
```
Listen 80
NameVirtualHost *:80

<VirtualHost *:80>
DocumentRoot /www/foo1
ServerName www.foo1.com
#blaw balw balw
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /www/foo2
ServerName www.foo2.com
#blaw balw balw
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /www/foo3
ServerName www.foo3.com
#blaw balw balw
</VirtualHost>

```
ok dude.  Now all we do is set up /etc/apache2/sites-available/foo1.com you are going to want something like this: (do this for foo1-3)
```
<VirtualHost *>
ServerName www.foo1.com
ServerAlias foo1.com
DocumentRoot /home/www/html/foo1.com/html
CustomLog logs/foo1-access_log common
</VirtualHost>
```

Ok now we need to enable the sucker by symlinking to /etc/apache2/sites-enabled
```
ln -s /etc/apache2/sites-available/foo1.com /etc/apache2/sites-enabled/foo1.com
```

Thats as far as i'll go... If your VHost setup is IP based you are going to want to change the <VirtualHost *:80> in my examples to your configuration. (So for IP based change the '*' to your ip and port based ':80' enjoy ;)

I'll try it, I just don't understand why it seems like each article and tutorial I read say something different.  So you are saying I should ADD 

```
Listen 80
NameVirtualHost *:80

<VirtualHost *:80>
DocumentRoot /www/foo1
ServerName www.foo1.com
#blaw balw balw
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /www/foo2
ServerName www.foo2.com
#blaw balw balw
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /www/foo3
ServerName www.foo3.com
#blaw balw balw
</VirtualHost>

```

to /etc/apache2/apache2.conf ?  Doesn't the Include /etc/apache2/sites-enabled/ take care of this?

Thanks

---

### Post by carcdrcdr on 2008-07-10
> Doesn't the Include /etc/apache2/sites-enabled/ take care of this

Either way should do it... Im at work late being bored...  Kinda gave you two ways at once haha ;)

Go with the bottom one.

---

### Post by antilog on 2008-07-10
> **carcdrcdr said:**
> Either way should do it... Im at work late being bored...  Kinda gave you two ways at once haha ;)

Go with the bottom one.

Ah, the problem was that I had setup a /sites-available/foo config, copied it to the other sites, replaced the domain names, but missed replacing some of the directory names.

All is working now, and Apache2 restarts with no errors (!)

Thanks!

---

