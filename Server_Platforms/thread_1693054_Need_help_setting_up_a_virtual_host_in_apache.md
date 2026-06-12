---
title: "Need help setting up a virtual host in apache"
date: 2011-02-22
forum: Server Platforms
---

### Post by m-smit on 2011-02-22
I am trying to set up an Apache2 virtual host to test sites I make from my own computer.

[LEFT]I used [_this_ ]("http://www.andyhawthorne.net/2010/10/setting-up-a-lamp-server-on-ubuntu-10-10/")guide to set up my LAMP and vHost, The LAMP stack seems to be working great, but I run into some problems when I try to set up a vHost 

As described in the guide I 

1. made a new directory in my home folder /home/[myname]/www/test.dev to put my site in (it currently contains a simple index.html file as a test).

2. In /etc/apache2/sites-available I copied the file "default" and renamed it "test.dev"

3. I edited the content of "test.dev" to look like this:

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    serverName test.dev

    DocumentRoot /home/[myname]/www/test.dev
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /home/[myname]/www/test.dev/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>
```

4. I enabled the site using the command "sudo a2ensite test.dev". I then restarted apache "sudo /etc/init.d/apache2 reload".

5. I edited the hosts file: "sudo gedit /etc/hosts" to look like this:

```
192.168.0.*    [myname]-System-Product-Name    # Added by NetworkManager
127.0.0.1    localhost.localdomain
::1    [myname]-System-Product-Name    localhost6.localdomain6    localhost6
127.0.1.1    [myname]-System-Product-Name
127.0.0.1    altserver
127.0.0.1    test.dev

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

6. I restarted apache "sudo /etc/init.d/apache2 reload".

Now if I enter "http://test.dev" in my firefox's adress bar I just get the apache2 "It works!" site. What is going wrong to cause firefox to show the "It works!" page rather then my own test site?
[/LEFT]

---

### Post by m-smit on 2011-02-22
Awesome, my problem is solved.

I figured I may have screwed something up in the process and in order to reset Apache to default I completely removed and reinstalled it. I repeated the process of configuring my vHost and now it seems to work perfectly.

---

