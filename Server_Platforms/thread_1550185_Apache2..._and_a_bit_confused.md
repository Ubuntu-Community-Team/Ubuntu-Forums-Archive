---
title: "Apache2... and a bit confused"
date: 2010-08-10
forum: Server Platforms
---

### Post by rwslippey on 2010-08-10
Okay, I applogies if this doesn't fit or if this is right in from of my face but, I'm a bit confused....

I'm trying to configure a few VirtualHost in apache2....

I currently a default virtualhost and 2 other sites....

No matter which domain I visit I still get the default page..

My Confusion is, I've been reading and some places seem to say that my virtual hosts should be in /etc/apache2/sites-enabled/*Config File*    and other seem to say it should be in /etc/apache2/httpd.conf     

What the awsner... I've tried both ways with no success .... If I put NameVirtualHost in httpd.conf I get an error saying their are no virtual hosts....

any help is greatly appricaited as always...

Rob

---

### Post by rwslippey on 2010-08-10
Okay, Looks like I have it worked out... heres what I got for anyone else with this confusion....


httpd.conf 

```
ServerName <Your Host Name Here>
NameVirtualHost *:80
```

For each host have a file in your /etc/apache2/sites-available directory.....

***Apparently what I was doing wrong was I was putting  NameVirtualHost *:80 at the beginning of the file... Which is apparently wrong...

Also I was adding <VirtualHost www.example.com:80> or similuar, which is incorrect...  Your virtualhost directive must match your NameVirtualhost directive... Example being Namevirtualhost *:80      == VirtualHost *:80

And the last issue I ahd was.. Don't forget the ServerName....   Which is your domain name
[CODE]
<VirtualHost *:80> 
ServerName domain.example.com
ServerAdmin webmaster@localhost
ServerAlias alias.example.com
DocumentRoot /var/www/website_1
</VirtualHost>
[CODE]

Their are a heck of a lot more options for this but that was what I used for basics to get it up...

If anyone has an extra advice or if I made a big security hole for myself Please let me know ... I take critasim well...

thanks 

rob

---

### Post by Ryan Dwyer on 2010-08-10
It goes in sites-available, not sites-enabled.

```

cd /etc/init.d/apache2/sites-available
sudo cp default myhost
sudo nano myhost # add ServerName myhostnamehere, change the DocumentRoot and modify other config to your liking
sudo a2ensite myhost # this creates the symlink in sites-enabled
sudo /etc/init.d/apache2 reload # this applies the new configuration

```

Then, if myhostnamehere resolves to the IP of your webserver, you should be able to visit [http://myhostnamehere/](http://myhostnamehere/) and view your new host.

---

