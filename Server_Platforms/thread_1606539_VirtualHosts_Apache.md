---
title: "VirtualHosts Apache"
date: 2010-10-26
forum: Server Platforms
---

### Post by Humza on 2010-10-26
[FONT=Georgia][SIZE=4][COLOR=Sienna]Hi All, [/COLOR][/SIZE][/FONT]

[FONT=Georgia][SIZE=3]Im new to Ubuntu Server and Linux Servers, i have managed to set up LAMP sucessfuly. 

I have only one ip and server, but would like to host multiple domains, i know that apaches VirtualHosts does that but i dont know how exactly. Ive changed the "[FONT=Courier New][SIZE=2]NameVirtualHost my.ip[/SIZE][/FONT]", ive put the virtual hosts into the thingey- "[FONT=Courier New][SIZE=2]sudo a2ensite uk.humza.co.cc[/SIZE][/FONT]" but when i restart apaches config the following message comes 

"[FONT=Courier New][SIZE=2][Tue Oct 26 21:31:22 2010] [warn] NameVirtualHost you.cant.guess.my.ip.lol:80 has no VirtualHosts[/SIZE][/FONT]"

 when i have put 1 virtual host, when i access uk.humza.co.cc it goes to my main [FONT=Courier New][SIZE=2]/var/www[/SIZE][/FONT] index when its meant to go to [FONT=Courier New][SIZE=2]/var/www/uk.humza.co.cc[/SIZE][/FONT]  , i have pointed the domain via and A record to my ip address. Is that sufficient, any hosts changes required if so how? I am a new guy to ubuntu servers. 
[COLOR=DarkOliveGreen]
Im running it on a VMware Workstation, im using it as a proper server. 

Ive tried to make this post as user friendly as i can to welcome people to read it, thanks in advance!
[/COLOR][/SIZE][/FONT]

---

### Post by Ryan Dwyer on 2010-10-26
Revert the change you made to the NameVirtualHost. Then change your opening VirtualHost tag for uk.humza.co.cc to <VirtualHost *:80>. Reload Apache and test.

Also, if you're accessing your server using a private IP then you need to remember to set your DNS to the public IP. This means you won't be able to access it locally unless you add an entry in your /etc/hosts file which points to the private IP.

---

### Post by Humza on 2010-10-27
My Server has gone from bad to worse.  for some very odd reason, today i turned it on and tried accessing it via SSH no response, tried accessing local url (192.168.2.10), timed out, tried accessing from my ip (used to work but today :-( ). I tried restarting to no avail. 

Any ideas?

---

### Post by Humza on 2010-10-27
Ok, 

ive just installed a fresh copy of ubuntu 10.04.1 LTS, all is fine (not really), i installed webmin and created a virtual host , but it still does not work apahce gives error, could not determine hostname : uk.humza.co.cc 

Any ideas?

---

### Post by Vegan on 2010-10-27
I have cut the block for my developer site frrom my httpd.conf file in /etc/apache2/httpd.conf file

<VirtualHost *:80>
    DocumentRoot "/www/developer"
    ServerName contract-developer.tk
    ServerAlias [www.contract-developer.tk](www.contract-developer.tk)
    <Directory "/www/developer">
	allow from all
	Options +Indexes
    </Directory>
</VirtualHost>

Simply replace the name of the server and the path to your site folder.

It is that simply when you have an example to work with.

---

### Post by Humza on 2010-10-27
> **Vegan said:**
> I have cut the block for my developer site frrom my httpd.conf file in /etc/apache2/httpd.conf file

<VirtualHost *:80>
    DocumentRoot "/www/developer"
    ServerName contract-developer.tk
    ServerAlias [www.contract-developer.tk]("http://www.contract-developer.tk")
    <Directory "/www/developer">
    allow from all
    Options +Indexes
    </Directory>
</VirtualHost>

Simply replace the name of the server and the path to your site folder.

It is that simply when you have an example to work with.

It stilldoes not work, my conf file is below (the main bits)


<VirtualHost *:80>
DocumentRoot /var/www/humza.co.cc
ServerName uk.humza.co.cc
<Directory /var/www/humza.co.cc>
allow from all
Options +Indexes
</Directory>
</VirtualHost>
ServerName uk.humza.co.cc:80

still no avail.

ive restarted apache, restarted the server. How do i point uk.humza.co.cc to my webserver, any hosts file changes?

---

### Post by SeijiSensei on 2010-10-27
The server appears firewalled off from the outside.  I can resolve uk.humza.co.cc to its IP address, but I can't connect to port 80 at that address.  Do you have an external router?  Have you opened port 80 and told the router to forward traffic from that port back to your server?

---

### Post by Humza on 2010-10-28
oh thats normal, i turnit off at night, im doing that until i can get it working, it saves power, and it heats my room up too much and the lights are annoying at night and makes too much noise, ill move it in the atic once i can get it working, im turning it on now!

---

### Post by CharlesA on 2010-10-28
I was able to connect fine using [http://uk.humza.co.cc/](http://uk.humza.co.cc/) - got the "It works!" page. (but not now)

Try adding an alias in virtualhosts and see if that works.

---

### Post by Humza on 2010-10-28
an alias for what?

Also, how do i point uk.humza.co.cc, eg. via A record or how.

if you do reply to this thread keep it open (in a different tab), it is most likely that you will get a reply from me within a minute.

<VirtualHost *:80>
DocumentRoot /var/www/humza.co.cc
ServerName uk.humza.co.cc
ServerAlias ww2.humza.co.cc
<Directory /var/www/humza.co.cc>
allow from all
Options +Indexes
</Directory>
</VirtualHost>
ServerName uk.humza.co.cc:80


current config^

---

### Post by Humza on 2010-10-28
im getting a bit nutty, i need a reply soon.

Just to let you know, ive got webmin, and no firewall on ubuntu but a router firewall, i have the ssh, 80, webmin ports open, thats it.

---

### Post by CharlesA on 2010-10-28
Just to test, can you connect locally if you add the hostname you want to use to the /etc/hosts file?

What does the index.html file look like in:

```
/var/www/humza.co.cc
```

---

### Post by Humza on 2010-10-28
ive added it to my hosts, but i dont know how to test, the server has no desktop interface, i am accessing via ssh. 

as for index.php it says

Moved To : <a href="default.php">default.php</a>, there is an index.html that says exactly the same, and the directoryindex is set to index.php

---

### Post by CharlesA on 2010-10-28
You can either install links on the server and see if you can access the page you want locally or just add an entry to the hosts file on your local machine and go from there.

It really sounds like virtualhosts isn't configured correctly tbh.

So you want [http://uk.humza.co.cc/](http://uk.humza.co.cc/) to have it's root directory in /var/www/humza.co.cc, right?

---

### Post by Humza on 2010-10-28
yes!

yeah, i think virtualhosts is not configured properly.

---

### Post by CharlesA on 2010-10-28
Can you post the output of this please:

```
cat /etc/apache2/httpd.conf
```

I checked on my LAMP server and it worked fine for me.

Here's what my httpd.conf file looks like:
```
<VirtualHost *:80>
DocumentRoot /var/www/humza.co.cc
ServerName uk.humza.co.cc
</VirtualHost>

```

The hosts file looks like this:

```
192.168.1.34	uk.humza.co.cc
```

I'd check the DNS record first and see what happens.

EDIT: I put the IP address of that machine into my hosts file and it still pulls up the It Works! page.

---

### Post by Humza on 2010-10-28
Its apache2.conf BTW.
```

#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
##

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# event MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being
# viewed by Web clients.
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., [www.apache.org]("http://www.apache.org/") (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

ServerTokens Prod

<VirtualHost *:80>
DocumentRoot /var/www/humza.co.cc
ServerName uk.humza.co.cc
ServerAlias ww2.humza.co.cc
<Directory /var/www/humza.co.cc>
allow from all
Options +Indexes
</Directory>
</VirtualHost>
ServerName uk.humza.co.cc:80
humzabobat@InfinityServer2:~$

```thats the most my ssh client gives

i need it to give me a page that says exactly "[FONT=Times New Roman][SIZE=3](Moved To : [default.php]("http://aerocrash.co.cc/default.php"))[/SIZE][/FONT]"

---

### Post by CharlesA on 2010-10-28
Did you configure the virtualhosts in webmin by chance?

It shouldn't really matter (outside of neatness) if they are in apache2.conf or httpd.conf.

Try moving the virtualhosts part to httpd.conf and then restarting apache2. See what happens.

---

### Post by Humza on 2010-10-28
at first i did, but then it messed it up, so i went to manual and deleted everything webmin did and started fresh.

ok, ill try.

---

### Post by CharlesA on 2010-10-28
You can also check the logs to make sure that the virtualhost is working:

```
tail /var/log/apache2/other_vhosts_access.log
tail /var/log/apache2/error.log

```

---

### Post by Humza on 2010-10-28
the log file is empty!

please look at the pictures below!, the first thumbnail is lynx btw.

---

### Post by CharlesA on 2010-10-28
Interesting. There should be something in there if it's using a virtualhost.

I think the problem might have to do with this being after the </VirtualHosts> tag:

```
<VirtualHost *:80>
DocumentRoot /var/www/humza.co.cc
ServerName uk.humza.co.cc
ServerAlias ww2.humza.co.cc
<Directory /var/www/humza.co.cc>
allow from all
Options +Indexes
</Directory>
</VirtualHost>
[COLOR="Red"]ServerName uk.humza.co.cc:80[/COLOR]

```

I copied and pasted everything except that part into my httpd.conf file and restarted apache2 and was able to get a directory listing of the humza.co.cc folder.

---

### Post by Humza on 2010-10-28
ill try removing "[COLOR=Red]ServerName uk.humza.co.cc:80[/COLOR]".

still same old problem!

do i need to put anything into : /etc/apache2/sites-enabled/uk.humza.co.cc ?

---

### Post by Humza on 2010-10-28
--

---

### Post by CharlesA on 2010-10-28
I'm not too good with apache stuff and wouldn't want to break anything.

What you could try is purging apache2 and reinstalling it, then start from scratch.

The only thing you need to add to httpd.conf are these:

```
<VirtualHost *:80>
DocumentRoot /var/www/humza.co.cc
ServerName uk.humza.co.cc
ServerAlias ww2.humza.co.cc
<Directory /var/www/humza.co.cc>
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

If you want me to take a look, PM me the info and I'll see if there's anything out of the ordinary.

---

### Post by Humza on 2010-10-28
ok, its just a virtual  machine, ill revert to the snapshot i made just after install.

**Progress Report**
Updating system [doing]
Install Apache, php, etc. [still to do]
VirtualHosts [still to do]

I have to revert to the snapshot i made while installing.

How annoying, im back installing the os.

--
**Whats On My Screen**
Installing the base system - 90%

**What Am I Going To Do**
All im going to do is sudo

---

### Post by CharlesA on 2010-10-28
Best of luck. :)

At least you know it works, but there's something wrong with the virtualhosts setting.

---

### Post by Humza on 2010-10-28
Dont Leave!, look at my progress report above!

---

### Post by CharlesA on 2010-10-28
Here's some info as to how to set up name-based virtualhosts:

[http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)

Are you going to be serving muliple sites from the same VM or just one site?

---

### Post by Humza on 2010-10-28
multiple (2)

---

### Post by Humza on 2010-10-28
woops!, forgot to install lamp server, ill have to do it manually!

```
sudo tasksel install lamp-server
```

---

### Post by CharlesA on 2010-10-28
Did you already install the LAMP stack during the install?

EDIT: That answers that.

Make a snapshot after everything is installed and go from there. :)

---

### Post by Humza on 2010-10-28
installing LAMP now

im not going to do anything else but add these lines to httpd.conf

```
 	<VirtualHost *:80>
DocumentRoot /var/www/humza.co.cc
ServerName uk.humza.co.cc
ServerAlias ww2.humza.co.cc
<Directory /var/www/humza.co.cc>
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

---

### Post by Humza on 2010-10-28
Baa. I think im doing something wrong. Its still not working.

---

### Post by CharlesA on 2010-10-28
Okie dokie.

That'll let us know if virtual hosts are working or not.

Try it locally, by setting up a hosts files like I did above and see if it connects. With no index.html file, you should just get a directory listing.

Try it locally first and make sure it works.

Are you serving one site, or multiple sites on one server?

---

### Post by Humza on 2010-10-28
Yay!!!

Sucess, all it takes is a simple restart!

Thanks so much for your help and time CharlesA

---

### Post by CharlesA on 2010-10-28
It works for me now. I see the <h1> text. :)

---

### Post by Humza on 2010-10-28
Yay!!!

Sucess, all it takes is a simple restart!

Thanks so much for your help and time CharlesA

---

### Post by CharlesA on 2010-10-28
No problem. Don't forget to mark the thread as solved from the thread tools menu. :)

---

