---
title: "[SOLVED] Apache2 setup with domain names..."
date: 2008-10-29
forum: Server Platforms
---

### Post by hockey97 on 2008-10-29
HI, I just found out  about the settings for apache2 not being right.

ok I have 2 domain names.

I want apache2 to host 2 domain names.

well I have a total of 4 zone names....

so for exacple  [www.domain1.com](www.domain1.com) and domain1.com  these 2  will direct anyone to domain1.

the same as follows with domain 2.

the problem I have is with apache2. 

for example I can get to domain one only by using domain1.com

my [www.domain1.com](www.domain1.com) would take to to the apache default setup.

how can I setup apache2 so that both [www.domain1.com](www.domain1.com) and domain1.com would both direct the user to domain 1???


thanks for the help.

---

### Post by canh_nguyen on 2008-10-29
Post your virtual host conf file.

---

### Post by hockey97 on 2008-10-29
well... 

what do you mean the virtuial host config??? I am guessing it's in the website config file???

where can I find it. I don't know if I config the virtual host right.

I been playing around with the apache config and today found my 2nd website domain yesterday I could get the [www.mydomain2.com](www.mydomain2.com) working. and not the mydomain2.com one.

now I can't get either of them to work. I get a page that shows It works.

the default page that came with apache2.

what should I do??



oh by the way here is the website config (tookenout)

---

### Post by hockey97 on 2008-10-29
ok, well I got frustrated and decided to delete all website configs.

So I then created new ones. Plus I also use webmin to do most of this stuff.

so not all domain names I have points to a IT WORKS!!!  page the default page.

I set the directory to where the files would be for the website.

I done all this using webmin.

here is the virtial config so far:(tookenout)

---

### Post by hockey97 on 2008-10-30
how would you setup apache2 to host 2 websites but allow for it to use 2 domain names for each websites.

like [www.mydomain.com](www.mydomain.com) and mydomain.com  like that which would direct the client to that certain website.

---

### Post by alienprdkt on 2008-10-30
this is the httpd.conf file:

NameVirtualHost *:80

<VirtualHost *:80>
   ServerName [http://site1.com](http://site1.com)
   ServerAdmin webmaster@localhost
   DocumentRoot "/var/www/site1"
</VirtualHost>

<VirtualHost *:80>
   ServerName [http://site2.com](http://site2.com)
   ServerAdmin webmaster@localhost
   DocumentRoot "/var/www/site2"
</VirtualHost>

<VirtualHost *:80>
   ServerName [http://site3.com]("http://ohmniverse.dyndns.tv")
   ServerAdmin webmaster@localhost
   DocumentRoot "/var/www/site3"
   </VirtualHost>

---

### Post by stickboy2642 on 2008-10-30
You can have the site listen for both domains by using the ServerAlias command.  Your config would look something like this:

```

<VirtualHost my external ip:80>
DocumentRoot /home/linuxuser/websites/mydomain.com
ServerName mydomain.com
**ServerAlias www.mydomain.com**

```

Note that doing it this way will NOT redirect all traffic to [www.mydomain.com](www.mydomain.com), but will simply display the same page regardless of which URL you type.

---

### Post by alienprdkt on 2008-10-30
sorry had to edit (double post>

---

### Post by hockey97 on 2008-10-30
ok thanks  guys.

I currently  use the address with my domain names and it works now.

I am going to try that alias thing. 

I will see what happens thanks.

---

### Post by hockey97 on 2008-10-30
well, I got one domain working but the other is working half way.


ok I own 2 domain names. one is domain1  and domain2

now my domain1 works fine now.

if you type (wiped) or (wiped) it takes you to the right page.

now the problem I face is with the (blank).

if you type (wiped) or (wiped)

it will take you to the (wiped) page.

I checked the config to see if by mistake I put the wrong directory which is not the case.

I have config the (wiped)domain right and it points to it's own folder for the html document.

what can I do to try and debug this??

I don't understand how it gat this way.

Here is the config for domain: (tookenout)

---

### Post by alienprdkt on 2008-10-30
> **hockey97 said:**
> 
Here is the config for domain: xxx.com: ```
<VirtualHost xxx.com:80>
DocumentRoot /home/xxx/websites/xxx.com
<Directory "/home/xxx/websites/xxx.com">
allow from all
Options +Indexes
</Directory>
ServerName xxx.com
ServerAlias xxx.com www.xxx.com
DirectoryIndex index2.html
</VirtualHost>
```
Think you configured the wrong file !!!!

copy paste this into your 
_**/etc/apahe2/httpd.conf**_ file:

NameVirtualHost *:80

<VirtualHost *:80>
   ServerName xxx
   ServerAdmin webmaster@localhost
   DocumentRoot "/home/xxx/websites/xxx.com"
ServerAlias xxx xxx
DirectoryIndex index2.html
</VirtualHost>

first test xxx

then test your alias
xxx

(the reason I said this way, I personally never got Alias to work for me)
if this dosn't work i'd try naming your DirectoryIndex file to just index.html and removing the DirectoryIndex line, because that is default and I know that works)

---

### Post by stickboy2642 on 2008-10-31
First off, you should be using the IP address you want the site to listen on in your VirtualHost directive rather than the domain name.

```
<VirtualHost 10.20.30.40:80>

as opposed to 

<VirtualHost xxx.com:80>

```Secondly, did you create a separate file in /etc/apache2/sites-available for the second site?  If not, where did you put the configuration?  The best way to set multiple sites up is to create individual .conf files in /etc/apache2/sites-available with only the configurations for the site.  Then you create a symlink in /etc/apache2/sites-enabled that points to at file.

```

ln -sf /etc/apache2/sites-available/xxx.com.conf /etc/apache2/sites-enabled/xxx.com.conf

```Setting it up this way makes it easier to change things for each site.  It also makes it easier to disable a site should you need to.

---

### Post by stickboy2642 on 2008-10-31
Two more things I noticed:

Remove the http:// from the server name.  It is not needed;  Also, the server alias should not have both names in it, just the one that is NOT in the ServerName.  See the modified configuration file below:

```

<VirtualHost *:80>
[B]ServerName xxx.com
ServerAlias www.xxx.com[/B]
ServerAdmin webmaster@localhost
DocumentRoot "/home/xxx/websites/xxx.com"
DirectoryIndex index2.html
</VirtualHost>

```

---

### Post by hockey97 on 2008-10-31
Closed post!!!

---

### Post by alienprdkt on 2008-10-31
> **hockey97 said:**
> well... the website config works.

The problem is that it's grabbing my other domains index file so if I go to xxx I would see the same page as my xxx 

ya I have files created in that website available.

I use webmin which does this. I used that to config apache ect.

I mean I got the xxx.com domain to work how I wanted it.

It's just xxx.com is using the same html page as xxx.com even though I made a index.html for both domains.

I then decided to rename the xxx.com index file to index2.html.

what you guys said I already done it. The recommendations above.

I even looked at the root directory and could tell I configured the right folder for the domain.

would it really matter??? if I used the domain address or the ip address for the address???
Well by default Apache is set to look at index.*
try moving second domain to new directory.


DocumentRoot "/home/xxx/websites/xxx.com"


and for the other

DocumentRoot "/home/xxx/websites/xxx.com

---

### Post by hockey97 on 2008-11-01
Closed post!!!!

---

### Post by alienprdkt on 2008-11-01
> **hockey97 said:**
> what do you mean???


those DocumentRoot "/home/xxx/websites/xxx.com"
 and DocumentRoot "/home/xxx/websites/xxx.com .

are what I am using. I got the index file for xxx in that sites own folder and xxx index file with it's own folder.


I thought if I have 2 indext files one for xxx domain and the other for xxx and have a folder for both of the domains not combied by have their own folders.

and then put their own index files in those folders that is should be right.

I am not understanding how this would happen.

could it also be a problem with the bind9 config??? I have both domain names pointing to my external ip address.

and I have config my hosts file and put those domain names with the  internal ip address.

What else should I try to look at???
  Ok then it should be woeking? I don't know, I thought you had it named 

index.html
and index2.html

rather then them both being index.html in there own directory.
but if thats how you have it set up with them each being index.* then it should work and maybe someone else can help you out with this.

---

### Post by hockey97 on 2008-11-02
Closed post!!!!

---

### Post by alienprdkt on 2008-11-02
Can't help you with this one, I don't ahve bind, or a dns server, I just use dyndns.org, and I didn't change my sites-avail / default page either, from default... only changes I have made were to the httpd.conf file to add <VirtualHost>. Thats all I had to do to get all my virual hosts running on 2 ubuntu / 2 mac osx pcs going, on the the one Ubuntu I have it as site.com - site5.com / on the other ubuntu i have it set to test.site.com - test.site5.com / on the macs i have them set to test1-5.site1-5.com and so on... all of these the only file i had to configure for virtual hosting was the httpd.conf file.

But I had to configure Apache on all machines, I couldn't get it to work by just changing the ip from one machine to point to others, its suppose to work but gave up after 2 hrs. of configuring, thought it would judst be easier to install and configure apache for all machines

---

### Post by hockey97 on 2008-11-02
thanks for the help. 

If anyone else can give me suggestions. I am like frustrated.

I seriously don't see any problem with the configs.

I don't really know what else to try.

Should I ask on the programming area???

---

### Post by eighto2 on 2008-11-03
Doing it in httpd.conf *does* work... but its not really the best method, because if one of those sites starts going crazy,or you need to make a specific site configuration you basically have to restart your entire apache service, taking down both sites...
Here's how I have my server setup:
the only thing in my httpd.conf is:
```
ServerName vlx1
```

Your best bet is to keep these site's files in /etc/apache2/sites-available
So just make sure you have something like this at the bottom of your apache2.conf
```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```
and just make one file per site. eg website1.com and website2.com

Here's a simple example, but would work if  updated accordingly

```
<VirtualHost *:80>
ServerName website1.com
ServerAlias www.website1.com
DocumentRoot /some/folder/public_html
DirectoryIndex index.html index.htm index.php index.php4 index.php5
</VirtualHost> 
```

After you make this file you type the following
```
sudo a2ensite website1.com
```
then
```
sudo /etc/init.d/apache2 reload
```
rinse and repeat for site2 just make sure your server name is set to *website2.com* of course

and if you ever need to you can disable a site by typing the following
```
sudo a2dissite website1.com
```
followed by the reload command

---

### Post by hockey97 on 2008-11-03
Thanks for the help. I decided to go on the apache IRC and they lol at me.

I was also called stupid....lol:lolflag:


well in the config I forgot NameVirtualHost *:80
 

you need this if you have more then one virtual host. 

if you don't have this apache would default to your first virtual host.

this is what happend.

so if anyone has a problem refer them to this post.


they have to go in their website configs and manually edit with a text editor.

and just add NameVirtualHost *:80  too the top.  that is if you have one ip address.

if you have 2 or more external ip address then instead where * is you type those ip addresses for each website.

hope this helps anyone that had the same problem as me.

thanks for the help though.

---

### Post by hockey97 on 2008-11-03
well... I give permission for ubuntunu  forms  to delete this new forum post. ):P

---

