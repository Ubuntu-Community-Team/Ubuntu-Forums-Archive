---
title: "How could I set up multiple sites without a domain and one local IP?"
date: 2012-04-02
forum: Server Platforms
---

### Post by That Guy Is Here on 2012-04-02
Hi all,

I am currently a jr. high student and I am enrolled in a Tech class. This is the first time we've ever done something like this, and our teacher has no experience in this field. Our class is on track to develop either our own simple HTML/CSS/JScript sites or a WordPress site. With this I thought it would be fun to have all the students upload these to a small network server(an HP Proliant DL360 g3 or 4 Ill be bringing in) that doesn't receive any connections outside of our local network. I was going to set it up as a LAMP or maybe even a LEMP server, but the only problem is I don't know how to set it up so it doesn't use more than one IP and no Domain Registrar. Also our schools network is Windows Based and has a firewall, so I would need to get around that for it too. 

So if anyone has any better ideas or how to set this up that would be great!

Thanks, 
ThatGuyIsHere

---

### Post by SeijiSensei on 2012-04-03
Well, you could run multiple instances of Apache listening on separate ports.  The first website might have a URL like [http://10.10.10.10:8001/](http://10.10.10.10:8001/), the next [http://10.10.10.10:8002/](http://10.10.10.10:8002/), and so forth.  This is a pain in the neck though.

If your school's IT people can assign you a range of IP addresses, you can use virtualized adapters on the server and assign each IP address to a different adapter.  If, for instance, your main interface is eth0, you can create virtual adapters eth0:0, eth0:1, etc., and give them each a different IP address.  Then you'd have a bunch of Listen directives, one for each address, and a bunch of <VirtualHost> stanzas, like this:

```

Listen 10.10.10.10:80
Listen 10.10.10.11:80
etc.

<VirtualHost 10.10.10.10:80>
    stuff
</VirtualHost>

<VirtualHost 10.10.10.11:80>
    more stuff
</VirtualHost>

etc.

```

However I'd suggest an entirely different route.  Does your school's network have an DNS server?  If so, it's much easier to configure a bunch of CNAME directives that all point to the server's IP address.  Or, if the admin doesn't like that approach, you can ask to have a subdomain created on the server that points to your server.  You'd have to then learn how to use bind9 to create a DNS server.  Something like this:

On the main DNS server for example.com:

```

sites    IN    NS   websites.example.com.
websites IN    A    10.10.10.10
```

where "websites.example.com" is the name of your Linux server.  Then on the Linux server you could create a "zone file" for sites.example.com with entries like this:

```

@     IN    SOA   sites.example.com.  root.example.com. (
            stuff
            )

      IN    NS    websites.example.com.


joe   IN    CNAME websites.example.com.
sue   IN    CNAME websites.example.com.

etc.


```

In Apache you'd have separate <VirtualHost> stanzas for each name:

```

<VirtualHost *:80>
     ServerName  joe.sites.example.com
     stuff
</VirtualHost>

<VirtualHost *:80>
     ServerName sue.sites.example.com
     stuff
</VirtualHost>

etc.

```

Requests for joe's site would be [http://joe.sites.example.com/](http://joe.sites.example.com/), for sue's site, [http://sue.sites.example.com/](http://sue.sites.example.com/), and so forth.

---

### Post by That Guy Is Here on 2012-04-04
Wow! Thank you! Now how would you suggest I go about creating FTP acounts? I was thinking creating a bunch with only file access to their predefined folder

---

### Post by SeijiSensei on 2012-04-04
I'd avoid FTP and install [Samba]("http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/") instead. Either way you'll need to create user accounts for all the students.  

Before creating the accounts, I recommend adding a directory to /etc/skel called "website" or something like that.  Then when you create each account, a /home/username/website directory will be automatically created.  In Apache, regardless of which method you choose above, you'd set the DirectoryRoot for each student's website to /home/username/website.  You'll need to make sure that the Apache user, "www-data", can read these directories, which isn't true by default in Ubuntu.  To fix this, do the following:

```

cd /home
sudo chmod 711 *
sudo chmod 755 */website

```

Now if you install Samba, each student's home directory will be automatically shared and can be mounted in Windows, Mac OS X, or Linux.  For Windows, I recommend using the "map a network drive" feature; for the latter two, you can enter URLs of the form "smb://server/username" into the file manager application.

---

### Post by webservervideos on 2012-04-04
> **That Guy Is Here said:**
> Hi all,

I am currently a jr. high student and I am enrolled in a Tech class. This is the first time we've ever done something like this, and our teacher has no experience in this field. Our class is on track to develop either our own simple HTML/CSS/JScript sites or a WordPress site. With this I thought it would be fun to have all the students upload these to a small network server(an HP Proliant DL360 g3 or 4 Ill be bringing in) that doesn't receive any connections outside of our local network. I was going to set it up as a LAMP or maybe even a LEMP server, but the only problem is I don't know how to set it up so it doesn't use more than one IP and no Domain Registrar. Also our schools network is Windows Based and has a firewall, so I would need to get around that for it too. 

So if anyone has any better ideas or how to set this up that would be great!

Thanks, 
ThatGuyIsHere

 apache allows for namebased virtual hosts...so that one ipaddress can be used for all domains.  look up virtualhost name based and see how you can add a   full of directives for each site. They can all share the same use of php, mysql, apache, etc. Make a different mysql user and database for each site. A unique html directory for each site (like /var/www/html/site1, site2, site 3) You can even direct to the user's home directory if wished. Lots of options..  enjoy the fun...between all of you, you should all be able to wing it and get it done.

---

### Post by SeijiSensei on 2012-04-05
> **webservervideos said:**
> apache allows for namebased virtual hosts...so that one ipaddress can be used for all domains.

Yes but only if you have control over the domain name server, or else you're stuck with maintaining static hosts files on all the individual client machines.

---

### Post by webservervideos on 2012-04-05
> **SeijiSensei said:**
> Yes but only if you have control over the domain name server, or else you're stuck with maintaining static hosts files on all the individual client machines.

 you would only be able to go to the site via an ip and not a domain name...and no biggie there..as long as the machine has one ip going to it, you are in..  so instead of [www.example.com/wordpress](www.example.com/wordpress) you would go to 198.168.0.85/usersite1/wordpress  same way I use development sites with no domain going to them..works fine. All scripts need to be based on ip and not domain...or use the servername for all of it...if the server can be reached by servername, then that is your domain name.

---

### Post by SeijiSensei on 2012-04-05
> **webservervideos said:**
> you would only be able to go to the site via an ip and not a domain name

I'm sure you realize that's not what's meant by "name-based virtual hosts."  If not, I suggest reading [this](httpd.apache.org/docs/2.2/vhosts/name-based.html).

To use "name-based" hosting, the URL must include a server name that Apache can match against one of the ServerName or ServerAlias directives in the <VirtualHost> containers.  That requires either a DNS server to point the various names to the IP address or a CNAME, or a set of hosts files on all the client machines.

---

### Post by rubylaser on 2012-04-05
Are you trying to publish these sites to the internet or just on your LAN?  If you're trying to get these on the web, you're going to need to talk to the school's network admin to give setup NAT'ing and open all necessary ports.

If you're just trying to set this up in the computer lab, I'd just suggest you follow SeijiSensei's advice and setup named based hosts if you can get your network admin's to make the DNS entries for you.  

Another idea (although far fetched and highly unlikely in a school) would be to set your lab up on a separate subnet, and have your own DHCP server, and create your own DNS records for all of your vhosts.  All of your laptops or workstations would connect to this subnet.  Obviously, you'd want to make sure that the school's IT staff knew what you where planning and were okay with it, and two, that you are up to the task of setting this up.

---

### Post by webservervideos on 2012-04-05
> **SeijiSensei said:**
> I'm sure you realize that's not what's meant by &quot;name-based virtual hosts.&quot;  If not, I suggest reading [this]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html").

To use &quot;name-based&quot; hosting, the URL must include a server name that Apache can match against one of the ServerName or ServerAlias directives in the <VirtualHost> containers.  That requires either a DNS server to point the various names to the IP address or a CNAME, or a set of hosts files on all the client machines.

which is resolved on the local machine via dns....still accessable by the ipaddress of the server.  its how I do my development sites..as long as the ip goes to the server, or the servername gets to that server, you can used namedbased virtual host directives and it will resolve.

---

