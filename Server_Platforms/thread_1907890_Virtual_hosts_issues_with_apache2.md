---
title: "Virtual hosts issues with apache2"
date: 2012-01-12
forum: Server Platforms
---

### Post by peprex on 2012-01-12
Hi,
 
I have already started working with virtual hosts, and everything seemed to be alright. Actually I have only two vhosts, the default one and the one I created. I removed from them every Indexes option I found, because I dont want apache to browse my folders, and it works. It's the only change I made in the default config file. You can see how my sites-available files look like down here :
 
**default**
 
<VirtualHost *:80>
        ServerAdmin [EMAIL="webmaster@localhost"]webmaster@localhost[/EMAIL]
        DocumentRoot /var/www/virtuals
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/virtuals>
                Options FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
ErrorLog ${APACHE_LOG_DIR}/error.log
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>
 
You can see how I removed the Indexes options, and make the default to point /var/www/virtuals, I like to work there. Let me show you mydomain.com sites-available config file :
 
**mydomain.com**
 
<VirtualHost *:80>
        ServerName mydomain.com
        DocumentRoot /var/www/virtuals/mydomain.com
        <Directory /var/www/virtuals/mydomain.com/>
                Options FollowSymLinks MultiViews
                AllowOverride All
        </Directory>
</VirtualHost>

This works great when I put an index.html file in /var/www/virtuals/mydomain.com. The point is that I want to create one more level, httpdocs. So I want the path to be like this : /var/www/virtuals/mydomain.com/httpdocs , so I can put my html inside httpdocs folder. I put an index.html there and change mydomain.com config file, it looks like this now :
 
**mydomain.com**
 
<VirtualHost *:80>
        ServerName mydomain.com
        DocumentRoot /var/www/virtuals/mydomain.com/httpdocs
        <Directory /var/www/virtuals/mydomain.com/httpdocs/>
                Options FollowSymLinks MultiViews
                AllowOverride All
        </Directory>
</VirtualHost>

The problem : **I get 403 forbidden in the browser**. Why ? What should I have to modify for this configuration to work ? I think I'm not understanding quite well the way default config file works ....
 
Please help, thanks in advance.

---

### Post by volkswagner on 2012-01-12
Did you check back on your original thread?

What are the permissions for the folder and documents in the folder?

```
ls -alt  /var/www/virtuals/mydomain.com/httpdocs/
```

Apache needs permission to read your index.html.


What are you entering in the address bar?

If you are developing locally, the simplest is to add sides in sub folders and keep your default vhost file as is.

You will then be able to access site one (mydomain.com) like:

[http://localhost/mydomain.com](http://localhost/mydomain.com)

Then site to like, [http://localhost/mydomain2.com](http://localhost/mydomain2.com)  and so on.

Where mydomain.com and mydomain2.com are subfolders in your virtuals folder all operating under the default vhost file.  This way there is no need to reload apache when making a new site.

You will just need to make sure all your subfolders and .html are readable by apache2.

---

### Post by peprex on 2012-01-12
Hi , I've already checked the permissions and the folder is accesible by apache. Even to make sure this is true, I made 777 ....
 
But I'm still having the same error. 
 
I dont want to check the virtual from localhost. If my ip is 40.40.40.40, I want to access my virtual by doing [http://40.40.40.40/mydomain.com](http://40.40.40.40/mydomain.com).
 
Any ideas ?
Thanks !

---

### Post by volkswagner on 2012-01-12
You can substitute your ip for localhost for the same results.

As previously asked, please post the output of the following;
```
ls -alt  /var/www/virtuals/mydomain.com/httpdocs/
```

Also what did you enter in the url to get the 403 error?

You may find more detailed information in the logs.

```
less /var/log/apache2/access.log
```

and

```
less /var/log/apache2/error.log
```

Also important to realize when you access the server via ip address, apache will be using the default vhost file since it comes alphabetically before mydomain.com.  So in your scenario mydomain.com vhost file does not even come into play.

When you have proper permissions, you can access the site via   [http://40.40.40.40/mydomain.com/httpdocs](http://40.40.40.40/mydomain.com/httpdocs)

---

### Post by peprex on 2012-01-12
Hi,
in first place, thanks for your support. I show you my outputs :
```
ls -alt /var/www/virtuals/mydomain.com
```
 
```
total 12
drwxrwxrwx 2 root root 4096 2012-01-12 23:32 httpdocs
drwxrwxrwx 3 root root 4096 2012-01-12 23:32 .
drwxrwxrwx 3 root root 4096 2012-01-12 23:32 ..

```
 
Then I check on my browser the [http://40.40.40.40/mydomain.com](http://40.40.40.40/mydomain.com) and get to the apache access logs :
 
```
2.138.129.166 - - [12/Jan/2012:23:49:24 +0100] "GET /mydomain.com HTTP/1.1" 301 570 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:8.0.1) Gecko/20100101 Firefox/8.0.1"
2.138.129.166 - - [12/Jan/2012:23:49:24 +0100] "GET /mydomain.com/ HTTP/1.1" 403 505 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:8.0.1) Gecko/20100101 Firefox/8.0.1"
2.138.129.166 - - [12/Jan/2012:23:53:33 +0100] "GET /mydomain.com/ HTTP/1.1" 403 506 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:8.0.1) Gecko/20100101 Firefox/8.0.1"

```
 
And then to the error log :
```
[Thu Jan 12 23:49:14 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Jan 12 23:49:24 2012] [error] [client 2.138.129.166] Directory index forbidden by Options directive: /var/www/virtuals/mydomain.com/
[Thu Jan 12 23:53:33 2012] [error] [client 2.138.129.166] Directory index forbidden by Options directive: /var/www/virtuals/mydomain.com/
```
 
But I became pretty sorprised when I get to [http://40.40.40.40/mydomain.com/httpdocs](http://40.40.40.40/mydomain.com/httpdocs) in my browser ... it works ! But I want to get there only by [http://40.40.40.40/mydomain.com](http://40.40.40.40/mydomain.com) ...
 
About what you told me of the default config file. It appears first in the sites-enabled with the 000-default symlink, before my domain.com symlink. So what do you mean that apache checks it first and doesn't gets to my domain.com config file ? Shall I remove de default config file ?
 
I did a2dissite default and reload apache and it did not work. The I a2ensite it again.
 
What do you think about this mess ? :S Thanks again !

---

### Post by volkswagner on 2012-01-12
Virtual hosts, or more specifically "NameVirtualHosts" expects a domain in the url to identify which site to display ie "ServerName mydomain.com".

Instead you are inserting the ip address in the url, not the domain name.

[http://mydomain.com](http://mydomain.com) = a domain name but [http://40.40.40.40/mydomain.com](http://40.40.40.40/mydomain.com) does not qualify as a domain name, therefore apache will not be able to search for "serverName" in a vhost file.

This is why I say apache will use the directive in the first alphabetical vhost file.

Take a look at the server docs at the sticky on this server forum, in particular, [Apache2]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html").

If you want to continue using the ip in the url the simplest method would be have the default vhost file as in your original post.

```
DocumentRoot /var/www/virtuals
```

Then you put all your sites inside /var/www/virtuals folder.

Each site will have a new directory like mydomain.com

Site0 can have its root directory here, this would be a good place for a welcome page
with links to all your sites.
```
/var/www/virtuals/index.html
```

Site1
```
/var/www/virtuals/mydomain.com
```

Site2
```
/var/www/virtuals/mydomain2.com
```

Site3
```
/var/www/virtuals/mydomain3.com
```


Again since you are using the ip, individual host files wont't help.

If you want to go several folder deep like

```
/var/www/virtuals/mydomain.com/httpdocs/
```

You will need to include all the folders after "virtuals" as part of your url, as mentioned earlier.  This is why you were able to see the site with my last url of

```
http://40.40.40.40/mydomain.com/httpdocs 
```

What you need to understand is DocumentRoot.

If your document root is /var/www/virtuals and you have an index.html inside the virtuals folder you will not need anything after the ip address in the url to access that index.html ie:
```
http://40.40.40.40/ 
```

is the same as

```
http://40.40.40.40/index.html 
```

Any sites that are sub folders of virtuals, will need to have those folders as part of the url.

Again this all stems from using the ip address, because NameVirtual hosts don't run on ip's.

I hope this clears some things.

---

### Post by peprex on 2012-01-12
It seems I was wrong on my comprehension of vhosts... I will have a look to the documents you told me. 
 
The thing is that I dont want to use the ip ... I thought it was necessary ! Because when I use mydomain.com in my browse, at home, I go to a page that is not the one I have in the vhost mydomain.com who is in my vps ! So I thought, using the ip, that is not a problem for me because that server is for developing, I could access to my project and do my stuff ....
 
If I look in the /etc/hosts I can see that my server has a "reverse" name (I read it somewhere...) :
 
```
127.0.0.1       localhost.localdomain localhost
40.40.40.40   vps40404.ovh.net vps40404
40.40.40.40   mydomain.com

```
 
Maybe using the vps40404 in the mydomain.com config file ServerName definition, would work (vps40440.mydomain.com for example)? Or do you think I need some dns stuff for that ....
 
I'm going to check that, and read those documents. Thanks again!

---

### Post by volkswagner on 2012-01-12
Explain your development environment so I may suggest a solution.

Do you have apache2 installed on the same machine as your workstation?  Are you running a virtual machine for Ubuntu Server?  Is your sever physically separate from your workstation?


There really is no need to mask your LAN ip address when posting in this forum.  I'm just curious why you write 40.40.40.40?

Do other machines on your LAN need to view your development sites?

---

### Post by peprex on 2012-01-13
> **volkswagner said:**
> Explain your development environment so I may suggest a solution.
 
Do you have apache2 installed on the same machine as your workstation? Are you running a virtual machine for Ubuntu Server? Is your sever physically separate from your workstation?
 
 
There really is no need to mask your LAN ip address when posting in this forum. I'm just curious why you write 40.40.40.40?
 
Do other machines on your LAN need to view your development sites?
 
Hi volkswagner,
I'm going to talk about my scenario. I bought a VPS to [www.ovh.es]("http://www.ovh.es") . That means , they virtualize the OS you want in a machine and give you parameters for ssh connection as root, so you can administrate the server as you want. You can also buy plesk or cpannel, but i just wanted to learn, so I played alone with ssh, and no services installed.
 
So my idea was : 
- create my "mirror" projects in vhosts folders in the vps server (46.105.20.100 , i was masking it, dont know really why ), so i can upload there my home projects and say to my clients: "hey check in this url your beta project and give me feedback". Also I need to access my projects from outside to test paypal payment processes (i cant do it at my home working station)
 
Then, I have a virtualized ubuntu server on a machine (I can access only my virtualized part, because I bought a vps) which may be accesible from outside, and i work at home in localhost. When satisfied or need certain tests, i upload my files there.
 
When working locally at home, i'm used to the /var/www/virtuals/mydomain.com/httpdocs scenario, that's why i wanted to repeat it in the vps. So at home i can do : [http://localhost/mydomain.com](http://localhost/mydomain.com). I wanted something like this in the server, that's because i thought i had to use the ip or the reverse name that shows my server /etc/hosts.
 
What do you think then ? Thanks, you are helping me a lot !

---

### Post by satanselbow on 2012-01-13
If you want to be able to sent your clients a link such as 

"http://yourdomain.com/clientname" you might do better setting it up as **aliases**

You might also want to consider sub domains such as "http://clientdomain.youdomain.com" <-- which in your setup could be configured as virtualhosts.

Are you planning on hosting your future customers websites on your vps?

A good business strategy (locks 'em in) can be to get the domain your client wants to use on their live site registered and setup on your server early in the development cycle. That way you can send them a secure link (login/password)to a sandbox subdomain, such as "dev.clientdomain.com" whilst using the "real" domain for a quick "super duper bling stuff website will be launching soon" page (with a brief description - nothing fancy) which will give you some search engine visibility ready for the site proper to go live when you've knocked out the project... and hopefuilly been paid ;)

---

### Post by peprex on 2012-01-13
> **satanselbow said:**
>  
A good business strategy (locks 'em in) can be to get the domain your client wants to use on their live site registered and setup on your server early in the development cycle. That way you can send them a secure link (login/password)to a sandbox subdomain, such as "dev.clientdomain.com" whilst using the "real" domain for a quick "super duper bling stuff website will be launching soon" page (with a brief description - nothing fancy) which will give you some search engine visibility ready for the site proper to go live when you've knocked out the project... and hopefuilly been paid ;)
 
Thanks for your strategy advice. That's what exactly i have done in most projects, the thing is that in earlier works all the enviroment was set up by others, now it's my turn to do the job, and it's beeing painful.
 
> **satanselbow said:**
>  
You might also want to consider sub domains such as "http://clientdomain.youdomain.com" <-- which in your setup could be configured as virtualhosts.
 
 
That would be great ! So i modified my /etc/hosts :
 
```
127.0.0.1       localhost.localdomain localhost
46.105.20.100   vps16625.ovh.net vps16625
46.105.20.100   mydomain.vps16625.ovh.net

```
 
And also mydomain.com sites-available configfile :
 
```
<VirtualHost *:80>
        ServerName mydomain.vps16625.ovh.net
        DocumentRoot /var/www/virtuals/mydomain.com/httpdocs
        <Directory /var/www/virtuals/mydomain.com/httpdocs>
                Options FollowSymLinks MultiViews
                AllowOverride All
        </Directory>
</VirtualHost>

```
 
The path in virtuals is already setted and with 777 permissions. Restart apache service and ... it wont work because the browser sais it can not find the server :( 
 
P.D : A ping to vps16625.ovh.net works ....
 
Did i miss something ? Thanks !

---

### Post by volkswagner on 2012-01-13
This is getting more confusing while talking about two server locations.  I thought we were strictly talking about your local environment on your LAN to serve several test sites.

I did suggest not masking your LAN address, but you have now exposed your public address.  It is not a big deal, but I just did not want any further confusion.

There are many ways to accomplish the same goal, therefore you may receive many options while asking.   This is the beauty of Linux, group help, and free thinking.

My best advice is to get intimately familiar with NameVirtual hosts.

I think you edited you /etc/hosts file on your server rather than your workstation.  In order to access a name virtual host for a site that has no DNS available, your /etc/hosts file should be edited on the machine you are using to browse.

On your workstation add a line for your local server with all you dev sites


/etc/hosts
```

127.0.0.1	localhost
127.0.1.1	workstation

192.168.1.65	mydomain.com mydomain2.com mydomain3.com


```


My local server LAN ip is 192.168.1.65 so anytime I navigate to mydomain.com it points to my local server even if mydomain.com exists on the Internet.

On my local server I just need a vhost file with the "serverName" mydomain.com for this to work.

If you need to access mydomain.com on your VPS then just comment out the line in your /etc/hosts file like this.

```

127.0.0.1	localhost
127.0.1.1	workstation

#192.168.1.65	mydomain.com mydomain2.com mydomain3.com


```

I don't think you even have to restart networking, the change should be immediate.

---

### Post by peprex on 2012-01-13
> **volkswagner said:**
> This is getting more confusing while talking about two server locations. I thought we were strictly talking about your local environment on your LAN to serve several test sites. 

 
No sorry, i have two environments : 1- My home, with a pc with internet access. I develope locally on my computer. 2 - A vps with a public address where i want to upload the projects i started at home to show to my clients with an elegant mydomain.vps16626.ovh.net, so they can be viewed from any point.
 
 
>  
My best advice is to get intimately familiar with NameVirtual hosts.
 
 
I'm trying I promise, I thought I understood that well, but it seems I was wrong :S
 
>  
I think you edited you /etc/hosts file on your server rather than your workstation. In order to access a name virtual host for a site that has no DNS available, your /etc/hosts file should be edited on the machine you are using to browse.
 
 
Right ! I edited the /etc/hosts of the vps server, not the one in my home pc. But I cant say to my client : "please, edit your /etc/hosts so you can see how the project is going, so write down an entry to my vps in your file" , because they even know less than me, that could be embarassing. I'm trying to find the way to tell them : "hey look to mydomain.vps16626.ovh.net , and check how the project is going on" (and that domain should respond to a vhost configurated in the vps server)
 
 
>  
On your workstation add a line for your local server with all you dev sites
 
 
/etc/hosts
```

127.0.0.1    localhost
127.0.1.1    workstation
 
192.168.1.65    mydomain.com mydomain2.com mydomain3.com
 

```
 
 
My local server LAN ip is 192.168.1.65 so anytime I navigate to mydomain.com it points to my local server even if mydomain.com exists on the Internet.
 
On my local server I just need a vhost file with the "serverName" mydomain.com for this to work.
 
If you need to access mydomain.com on your VPS then just comment out the line in your /etc/hosts file like this.
 
```

127.0.0.1    localhost
127.0.1.1    workstation
 
#192.168.1.65    mydomain.com mydomain2.com mydomain3.com
 

```
 
I don't think you even have to restart networking, the change should be immediate.

 
You were completely right. I test it and that worked ! But that's not exactly the point as i tried to explain earlier. Please forgive me if i dont explain it properly, can you understand it ? What do you suggest ? Meanwhile, i'll keep studying !

---

### Post by volkswagner on 2012-01-13
Do you own a domain name?

In my opinion it is easiest to put your beta sites on your VPS using a folder/subfolder structure.  This is easier because it does not rely on DNS servers being updated.  If you make a subdomain for beta1.youVPS.com then your specific DNS provider and your clients DNS provider will have to be updated for the resolution to work.  This can be 30 minutes to 24-48 hours depending on what DNS providers your clients use.  I recall an annoying instance when my home isp (timewarner) had such slow DNS updates, that I mistakenly thought my server was not working.

Anyway, the choice is yours.

Go with a simple sub folder for each site or sub domain.  Either approach for the solution your customers will not need to edit their /etc/hosts file.

I suggest spending a few dollars and get your own domain to point at your vps.  This way you can do things like
[http://coolwebdesign.com/beta1](http://coolwebdesign.com/beta1), [http://coolwebdesign.com/beta2](http://coolwebdesign.com/beta2), [http://coolwebdesign.com/beta3](http://coolwebdesign.com/beta3) or
[http://beta1.coolwebdesign.com/](http://beta1.coolwebdesign.com/), [http://beta2.coolwebdesign.com/](http://beta2.coolwebdesign.com/), [http://beta3.coolwebdesign.com/](http://beta3.coolwebdesign.com/)

Again the choice is yours.  If you use subfolders there is no need to mess with vhost files and no need to rely on DNS propagation. 

If you go the subdomain route, you will need vhost files for each beta site and an A record at your DNS control panel.

I'm not sure how much control you will get with mydomain.vps16626.ovh.net 

It seem to me like your VPS provider gives you "vps16626.ovh.net"  but I'm not sure they will allow yet another subdomain from that like you mention "mydomain.vps16626.ovh.net"

But with my folder suggestion you can offer as many beta sites as you like by using the sub folders 
```
vps16626.ovh.net/beta1
```

So does your VPS provider allow subdomains as you mention?

```
mydomain.vps16626.ovh.net
```

---

