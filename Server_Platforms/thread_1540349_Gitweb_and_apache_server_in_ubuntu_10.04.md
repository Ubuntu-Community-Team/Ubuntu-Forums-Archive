---
title: "Gitweb and apache server in ubuntu 10.04"
date: 2010-07-27
forum: Server Platforms
---

### Post by VictorRodriguez on 2010-07-27
Hi this is a simple problem  that I had with Ubuntu 10.04  , git 1.7.1.1, git web and apache http server 2.2.16. las week.

The main problema was that I couldn't implement a local server for and internal project in a LAN network and then public the Git repositories in a gitweb template and that any one inside the LAN could clone them by http . 

Well there are many pages of how to do this and they were very helpful you will find them in the end of this comment but I hope this detailed guide could help someone else if you follow this steps 

fist you should have installed in your computer the latest version of git  ( [http://git-scm.com/](http://git-scm.com/) ) or tipe 

    $sudo apt-get install git-core 
 
Install the apache server 2 

    $sudo apt-get install apache2-utils apache2-common

Then after doing this you should be able to type in your browser  [http://localhost/](http://localhost/) and it should appear

 It works!
This is the default web page for this server.
The web server software is running but no content has been added, yet.

Well done you have a local server on your LAN wasn't so hard really ? So try it  type your IP in the web browser 

    $ifconfig 

will show your IP 

NOW THE HARDEST PART FOR ME sorry if it isn't for some one else. But I am new in linux and was hard. 

VIRTUAL HOST     

imagine that this is not a computer instead a server, as you want well it should have the capability to handle different  web pages or hosts

Virtual Hosting allow web servers to host more than one website on a single  machine. This is how sharing hosting works. It will allow you to access to your local repository using addresses such as [http://dev.mysite.com](http://dev.mysite.com) instead of [http://localhost/~myuser/myproject/](http://localhost/~myuser/myproject/) :) .

First of all, you need an apache server ready to run on your machine (like we said before), if it is not yet install, open a terminal and type
Once the server is installed, it is time to get into apache 2 configuration.
Let's open apache's main configuration file, name /etc/apache2/apache2.conf. A search for the word virtual bring us to the following line:
    
    Include /etc/apache2/sites-enabled/[^.#]*

This mean that when starting apache, it will look for files in /etc/apache2/sites-enabled/.
Lets go there and see what is in.
$cd /etc/apache2/sites-enabled/
$ls -l
total 1
lrwxrwxrwx 1 root root 36 2005-12-27 01:42 000-default -> /etc/apache2/sites-available/default
Well, this only links to the file in directory /etc/apache2/sites-available/ . You might wonder what is the point in doing such. Well, this simply allows you, mainly when you are using your box as a web server, to:
1.Have a simple main configuration file
2.Do be able to edit or create a new host by creating/editing a file from /etc/apache2/sites-available/
3.In case your web server doesn't restart because of misconfiguration, you can simply remove the link from the file in /etc/apache2/sites-enabled/ pointing to the malformed file in /etc/apache2/sites-available/
Now let say you want to be able to map the domain name dev.example.com to you local machine, using the code file in /home/myuser/public_html/example.com/.
While in /etc/apache2/sites-available, create a new file (let say example.com.conf)
$sudo vi example.com.conf
Now add the following lines:
<VirtualHost dev.example.com>
ServerAdmin webmaster@localhost
#We want to be able to access the web site using [www.dev.example.com](www.dev.example.com) or dev.example.com
ServerAlias [www.dev.example.com](www.dev.example.com)
DocumentRoot /home/myuser/public_html/example.com  
#if using awstats
ScriptAlias /awstats/ /usr/lib/cgi-bin/
#we want specific log file for this server
CustomLog /var/log/apache2/example.com-access.log combined
</VirtualHost>
Now, we specified a new host to apache but it is not yet linked to the repertory where apache actually look for virtual hosts. Let go to:
$cd /etc/apache2/sites-enabled/
and create a link to the file we just created:
$sudo ln -s /etc/apache2/sites-available/example.com.conf example.com.conf
Now apache is almost ready to restart, but before doing so, we must inform our linux system that dev.example.com and [www.dev.example.com](www.dev.example.com) are not to be looked for on the net, but on the local machine instead.
To do so, simply edit /etc/hosts and add the new host names at the end of the line beginning by 127.0.0.1, which is localhost.

In the end, your file should look like:
127.0.0.1 localhost.localdomain localhost dev.example.com [www.dev.example.com](www.dev.example.com)
And now we are done, simply reload apache:
sudo /etc/init.d/apache2 reload
Open your web browser and enter the following address dev.example.com. And will bring your web page. 

CLONING YOUR PROJECT BY YOUR VIRTUAL HOST

If it works well there are just one single thing to do in order to work with static IP addresses  
if your IP is FOR EXAMPLE 197.12.2.0 
<VirtualHost 197.12.2.0:80>
    ServerAdmin webmaster@localhost
    #We want to be able to access the web site using [www.dev.example.com](www.dev.example.com) or dev.example.com
    ServerAlias [www.dev.example.com](www.dev.example.com)
    DocumentRoot /home/myuser/public_html/example.com  
    #if using awstats
    ScriptAlias /awstats/ /usr/lib/cgi-bin/
    #we want specific log file for this server
    CustomLog /var/log/apache2/example.com-access.log combined
</VirtualHost>
and thats all, try to put your IP address in other computer ant it will work with out touching the /etc/hosts file. 

Now lets check if this work in git repositories, that is what we want. 

Imagine that you have a Git project like project1, we need to clone it with –bare option in order to put it like public, this topic is well described in the progit book ([http://progit.org/book/](http://progit.org/book/)) on the public server chapter ([http://progit.org/book/ch4-5.html](http://progit.org/book/ch4-5.html)) when you have your git  repositories like project1.git in the example directory /home/yourname/yourrepos/  and you can clone it successfully with the instruction 

    git clone /home/yourname/yourrepos/project1.git 

in any place of your computer, it means that you just need to  do this

    $ cd project1.git
    $ mv hooks/post-update.sample hooks/post-update
    $ chmod a+x hooks/post-update


Next, you need to add a VirtualHost entry to your Apache configuration with the document root as the root directory of your Git projects. ( This was the part that I was stook for a week ) 
We already have a virtual host working ( that was why I decided to first implement the Visrtual Host in apache ) 
<VirtualHost 197.12.2.0:80> 
    ServerAdmin webmaster@localhost 
    ServerName git.example.com 
    ServerAlias [www.git.example.com](www.git.example.com) 
    DocumentRoot   /home/yourname/yourrepos
    ScriptAlias /awstats/ /usr/lib/cgi-bin/ 
    CustomLog /var/log/apache2/example.com-access.log combined 
</VirtualHost> 

You’ll also need to set the Unix user group of the drectories to www-data so your web server can read-access the repositories, because the Apache instance running the CGI script will (by default) be running as that user:
    $ chgrp -R www-data  /home/yourname/yourrepos/
Now reload your apache and try to check your IP address in your web browser it will show your files, not in the way we want. 
Try to clone your project 
    $git clone [http://197.12.2.0/project1.git](http://197.12.2.0/project1.git)

If it works, perfect you can keep on this tutorial.
 
GITWEB 

Install git web 
    $sudo apt-get install gitweb

clone the git project 

    $ git clone git://git.kernel.org/pub/scm/git/git.git

generate the custom CGI script

$cd git/
$ make GITWEB_PROJECTROOT=" /home/yourname/yourrepos/" prefix=/usr gitweb/gitweb.cgi
$ sudo cp -Rf gitweb /var/www/
now check the /etc/gitweb.conf file , it shoul be something like this 

# path to git projects (<project>.git)    #### CHANGE TO YOUR PROJECTROOT###
$projectroot = "/home/yourname/yourrepos/"; 
 # directory to use for temp files 
$git_temp = "/tmp"; 
 # target of the home link on top of all pages 
#$home_link = $my_uri || "/"; 
 # html text to include at home page 
$home_text = "indextext.html"; 
########CHANGE TO YOUR LAST VIRTUAL HOST ####
 @git_base_url_list = ('http://git.example.com'); 
 # file with project list; by default, simply scan the projectroot dir. 
$projects_list = $projectroot; 
 # stylesheet to use 
$stylesheet = "/gitweb/gitweb.css"; 
 # logo to use 
$logo = "/gitweb/git-logo.png"; 
 # the 'favicon' 
$favicon = "/gitweb/git-favicon.png";

Now we should make another Virtual Host like we did above  in the VIRTUAL HOST section
but it should be like this 

<VirtualHost 197.12.2.0:80> 
ServerName dev.example.com 
ServerAlias [www.dev.example.com](www.dev.example.com) 
DocumentRoot /var/www/gitweb 
    <Directory /var/www/gitweb> 
        Options ExecCGI +FollowSymLinks +SymLinksIfOwnerMatch 
        AllowOverride All 
        order allow,deny 
        Allow from all 
        AddHandler cgi-script cgi 
        DirectoryIndex gitweb.cgi 
    </Directory> 
#if using awstats 
ScriptAlias /awstats/ /usr/lib/cgi-bin/ 
#we want specific log file for this server 
CustomLog /var/log/apache2/example.com-access.log combined 
</VirtualHost> 

If you reload your apache it will tell you to use the name virtual host option, here is the best of apache the capabilityto handle more that one virtual host just. Here we've setup two different directory trees, one for each site. If you wanted to have identical content it might make sense to only create one, and then use symbolic links instead.
The next thing to do is to enable virtual hosts in your Apache configuration. The simplest way to do this is to create a file called /etc/apache2/conf.d/virtual.conf and include the following content in it:
#
#  We're running multiple virtual hosts.
#
NameVirtualHost *
(When Apache starts up it reads the contents of all files included in /etc/apache2/conf.d, and files you create here won't get trashed on package upgrades.)

To enable the sites that we have created simply run as root :
  # a2ensite git.example.com 
and the same for all the sites enabled

At finally thats all, it  wasn't soo difficult but take some time to fix this problem  now when you load your web page it should look like [http://git.kernel.org/](http://git.kernel.org/) and you should be able to clone like your web page said. 
#################IMPORTANT #################

IF YOU HAVE A PROXY IN YOUR NETWORK YOU SHOULD DESEABLE COMPLETELY IF NOT SOME ERRORS LIKE 504 OR 500 WILL APEAR IN YOUR TERMINAL WHEN YOU TRIE TO CLONE THE PROJECTS 
TRY WITH unset http_proxy
 it could work it depends how you had configure your proxy 
if some one else find another way to do this please feel free to contribute whit this long post 
Hope it could help someone trying to do implement gitweb in ubuntu 10.04 and apache 2 
Thanks for all 
Sincerely yours 
Victor Rodriguez 

Bibliography 
[http://progit.org/book/](http://progit.org/book/)
[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)
[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

### Post by arrrghhh on 2010-07-27
I'm guessing this is a how-to and you don't really have a question/problem...

Assuming that's the case, I would edit your post for a couple of things that will improve readability.  First, put any code/configuration stuff in ["code"] ["/code"] brackets.  Second, change the title of your post to include the words "how-to" somewhere, that way we know it's a step-by-step guide instead of a question :D

---

### Post by airtonix on 2010-08-10
at first i was interested in reading your guide, but I found that your monologue was hard to separate from your code examples and terminal examples.

Please use the CODE bbcode wrappers for your terminal and code examples.

And would also be REALLY nice if you formatted the page into sections with headings.(having a common style)


Corrections you should make to your post : 

1. format it nicely... it currently takes ALOT of effort to read it.
2. creating and enabling apache vhosts is as simple as : 
```

 cd /etc/apache2/sites-available/
 sudo cp ./default ./new-vhost
 sudo a2ensite new-vhost
 sudo service apache2 restart

```
3. you might like to mention that using avahi aliases instead of modifying the /etc/hosts file allows other machines on the local network to make use of your sub-domain virtualhost. (other wise you need to edit each workstations /etc/hosts file separately). I'm working on some [helper scripts to manage the avahi aliases](http://airtonix.net/wiki/linux/avahi-aliases) that a machine would want to publish/broadcast on a local network (in addition to its own avahi hostname)

---

### Post by airtonix on 2010-12-31
Much easier and legible guide available here : 

[https://help.ubuntu.com/community/Git](https://help.ubuntu.com/community/Git)

---

