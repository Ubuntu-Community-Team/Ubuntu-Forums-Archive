---
title: "Karmic Apache+Passenger+RoR Application Server Howto"
date: 2010-09-03
forum: Server Platforms
---

### Post by tbdfm01 on 2010-09-03
I needed a production Apache server setup on Ubuntu Karmic for serving Ruby on Rails apps. The server I was implementing was an existing production server running PHP and apache. The problem was, after a few days of picking through google results trying to figure out just what to do, I was not finding a lot of good options for a production RoR server.

Some of the options require the developer to edit Apache configuration files, or add a virtual host for every RoR application deployed. From an Administrator standpoint this is not a great solution (for reasons which belong in a different thread).

The option I wanted was one which allowed the developer to place his/her application in an application directory and then allow Apache to serve up the RoR content. Seems pretty simple, but every link I clicked ended up with either outdated documentation, or solutions which did not fit my needs. I did eventually put together a solution but it was not straightforward, nor was it all documented in one place, nor was the documentation up-to-date. Hence the reason for this thread.

The options available for serving ruby apps at this time (09/03/2010) are:

[LIST=1]
[*]  WEBrick
[*]  Mongrel
[*]  Mongrel_cluster
[*]  Fast CGI
[*]  Passenger
[/LIST]
  
[LIST]
[*]     WEBrick is a standalone web server for RoR which typically runs on a different port on the developer's workstation so they can stop/restart/test/invent and create without having to worry about interrupting a server everyone else is using. It works well, but is not scalable for production.
[/LIST]
  
[LIST]
[*]     Mongrel is about the same in functionality as WEBrick but has more configuration options and some consider it more efficient and stable. To add more applications, you start more mongrel services or add your application to a mongrel_cluster configuration.
[/LIST]
  
[LIST]
[*]     Apache load balancing+proxying+Mongrel_cluster allows Mongrel to play with apache in a scalable fashion.
[/LIST]
  
[LIST]
[*]     FastCGI seems to be on it's way out. I found conflicting info: some said they hate it, some said they loved it. I stayed away from it.
[/LIST]
  
[LIST]
[*]Passenger is a module for Apache which, if configured correctly, allows RoR apps to be served much in the same way PHP apps are served. One caveat with Passenger is that it works well with the Apache Prefork mpm but the Worker mpm is more memory efficient. The conflict however is that Worker mpm is not compatible with mod_php at this point. So, if you need PHP support, you are stuck with Prefork for PHP , and possible memory issues with Passenger. Life is a tradeoff. The issues will get worked out eventually because Open Source people fix things which suck and this sucks.
[/LIST]
 
Be aware of version numbers for ruby, gem and passenger. There is WAY too much pain involved when getting this wrong so if things don't work, double check your versions. The version numbers I have for a working Passenger+RoR+PHP application server are as follows. If you have any of these installed, you may want to un-install them and go through the steps below to make sure you have the same versions. Another important note to make is DO NOT install gem through ubuntu's package manager. For whatever reason, it will cause you much grief. Download gem and build it as shown in the steps below. It's easy, and will save you pain:

```
# dpkg -l | egrep -i '(ruby|sqlite|apache|irb)' | awk '{printf ("%-30s %s\n", $2, $3);};'
apache2 2.2.12-1ubuntu2.2
apache2-mpm-prefork 2.2.12-1ubuntu2.2
apache2-prefork-dev 2.2.12-1ubuntu2.2
apache2-suexec 2.2.12-1ubuntu2.2
apache2-utils 2.2.12-1ubuntu2.2
apache2.2-bin 2.2.12-1ubuntu2.2
apache2.2-common 2.2.12-1ubuntu2.2
irb1.8 1.8.7.174-1ubuntu1
libapache2-mod-php5 5.2.10.dfsg.1-2ubuntu6.4
libapr1 1.3.8-1
libapr1-dev 1.3.8-1
libaprutil1 1.3.9+dfsg-1ubuntu1
libaprutil1-dbd-sqlite3 1.3.9+dfsg-1ubuntu1
libaprutil1-dev 1.3.9+dfsg-1ubuntu1
libaprutil1-ldap 1.3.9+dfsg-1ubuntu1
libopenssl-ruby 4.2
libopenssl-ruby1.8 1.8.7.174-1ubuntu1
libreadline-ruby1.8 1.8.7.174-1ubuntu1
libruby1.8 1.8.7.174-1ubuntu1
libsqlite3-0 3.6.16-1ubuntu1
libsqlite3-dev 3.6.16-1ubuntu1
libsqlite3-ruby1.8 1.2.4-2
rdoc1.8 1.8.7.174-1ubuntu1
ri1.8 1.8.7.174-1ubuntu1
ruby1.8 1.8.7.174-1ubuntu1
ruby1.8-dev 1.8.7.174-1ubuntu1
sqlite3 3.6.16-1ubuntu1

```So, let's get on with it. I execute everything as root in the examples but if you find it better form to use sudo, feel free.

First, install ruby and supporting software

```
# aptitude install build-essential ruby1.8-dev ruby1.8 ri1.8 rdoc1.8 irb1.8 libreadline-ruby1.8 libruby1.8 libopenssl-ruby sqlite3 libsqlite3-ruby1.8
...
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
```Next, setup symlinks for everything
```

# ln -s /usr/bin/ruby1.8 /usr/bin/ruby; ln -s /usr/bin/ri1.8 /usr/bin/ri; ln -s /usr/bin/rdoc1.8 /usr/bin/rdoc; sudo ln -s /usr/bin/irb1.8 /usr/bin/irb

```Now prepare to build rubygems by creating a source directory under root's home directory and change to it.
```
# mkdir ~/sources && cd ~/sources
```Download rubygems-1.3.7 using wget.
```
# wget http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz
...
2010-09-02 14:23:15 (279 KB/s) - `rubygems-1.3.7.tgz' saved [290986/290986]

```Untar rubygems, cd to the rubygems directory and run setup.rb
```
# tar xvfz rubygems-1.3.7.tgz && cd rubygems-1.3.7 && ruby setup.rb
...
RubyGems installed the following executables:
/usr/bin/gem1.8
```create a symlink for rubygems
```
# ln -s /usr/bin/gem1.8 /usr/bin/gem

```Now, using the new gem, install rails, passenger and rack-mount. rack-mount will allow you to use *RackBaseURI* which you will need later.   I do now know why *File not found: lib* comes up.
```
# gem install rails rack-mount passenger --include-dependencies
...
4 gems installed
Installing ri documentation for rails-3.0.0...
File not found: lib


```Update gem 
```
# gem update
Updating installed gems
Nothing to update

```Update gem system
```

# gem update --system
Updating RubyGems
Nothing to update

```Install Apache2 prefork and apr development software
```

# aptitude install apache2-prefork-dev libapr1-dev libaprutil1-dev 
Reading package lists... Done
Building dependency tree       
...
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

```Now run the[FONT=Courier New] passenger-install-apache2-module[/FONT] program.  This is included with when you install passenger and is an important step and one which can cause you grief if you go the package manger route.  There is a [FONT=Courier New]libapache2-mod-passenger[/FONT] package but like the rest of the ubuntu ruby/gem packages,  it didn't work for me.  Upon succesful install of Passenger, your output should look something like this
```


# passenger-install-apache2-module 
Welcome to the Phusion Passenger Apache 2 module installer, v2.2.15.
...
Press Enter to continue, or Ctrl-C to abort.
...
The Apache 2 module was successfully installed.                                                                                                                                   
                                                                                                                                                                                  
Please edit your Apache configuration file, and add these lines:                                                                                                                  
                                                                                                                                                                                  
   LoadModule passenger_module /usr/lib/ruby/gems/1.8/gems/passenger-2.2.15/ext/apache2/mod_passenger.so                                                                          
   PassengerRoot /usr/lib/ruby/gems/1.8/gems/passenger-2.2.15                                                                                                                     
   PassengerRuby /usr/bin/ruby1.8                                                                                                                                                 
                                                                                                                                                                                  
After you restart Apache, you are ready to deploy any number of Ruby on Rails                                                                                                     
applications on Apache, without any further Ruby on Rails-specific                                                                                                                
configuration!                                                                                                                                                                    
                                                                                                                                                                                  
Press ENTER to continue.  

--------------------------------------------                                                                                                                                      
The Apache 2 module was successfully installed.                                                                                                                                   
                                                                                                                                                                                  
Please edit your Apache configuration file, and add these lines:                                                                                                                  
                                                                                                                                                                                  
   LoadModule passenger_module /usr/lib/ruby/gems/1.8/gems/passenger-2.2.15/ext/apache2/mod_passenger.so                                                                          
   PassengerRoot /usr/lib/ruby/gems/1.8/gems/passenger-2.2.15                                                                                                                     
   PassengerRuby /usr/bin/ruby1.8                                                                                                                                                 
                                                                                                                                                                                  
After you restart Apache, you are ready to deploy any number of Ruby on Rails                                                                                                     
applications on Apache, without any further Ruby on Rails-specific                                                                                                                
configuration!                                                                                                                                                                    
                                                                                                                                                                                  
Press ENTER to continue.      


--------------------------------------------                                                                                                                                      
Deploying a Ruby on Rails application: an example                                                                                                                                 
                                                                                                                                                                                  
Suppose you have a Rails application in /somewhere. Add a virtual host to your                                                                                                    
Apache configuration file and set its DocumentRoot to /somewhere/public:                                                                                                          
                                                                                                                                                                                  
   <VirtualHost *:80>                                                                                                                                                             
      ServerName www.yourhost.com                                                                                                                                                 
      DocumentRoot /somewhere/public    # <-- be sure to point to 'public'!                                                                                                       
      <Directory /somewhere/public>                                                                                                                                               
         AllowOverride all              # <-- relax Apache security settings                                                                                                      
         Options -MultiViews            # <-- MultiViews must be turned off                                                                                                       
      </Directory>                                                                                                                                                                
   </VirtualHost>                                                                                                                                                                 
                                                                                                                                                                                  
And that's it! You may also want to check the Users Guide for security and                                                                                                        
optimization tips, troubleshooting and other useful information:                                                                                                                  
                                                                                                                                                                                  
  /usr/lib/ruby/gems/1.8/gems/passenger-2.2.15/doc/Users guide Apache.html                                                                                                        
                                                                                                                                                                                  
Enjoy Phusion Passenger, a product of Phusion (www.phusion.nl) :-)                                                                                                                
http://www.modrails.com/                                                                                                                                                          
                                                                                                                                                                                  
Phusion Passenger is a trademark of Hongli Lai & Ninh Bui.     

```Note the comments in the VirtualHost block above; For whatever reason, Apache does not see them as comments and will not start if they remain where they are.  Move them to the top of the file, or delete them altogether.

Next, create a [FONT=Courier New]passenger.conf[/FONT] file for Apache to use.  You will need to paste in the values spit-out by the [FONT=Courier New]passenger-install-apache2-module[/FONT] program, so take note.
```

# vi /etc/apache2/mods-available/passenger.conf

   PassengerRoot /usr/lib/ruby/gems/1.8/gems/passenger-2.2.15                                                                                                                     
   PassengerRuby /usr/bin/ruby1.8 

```And create a passenger.load file for Apache to use
```

# vi /etc/apache2/mods-available/passenger.load

   LoadModule passenger_module /usr/lib/ruby/gems/1.8/gems/passenger-2.2.15/ext/apache2/mod_passenger.so  

```Now tell Apache to enable the passenger module. We won't restart Apache yet because there is more editing to do.
```

# a2enmod passenger
Enabling module passenger.
Run '/etc/init.d/apache2 restart' to activate new configuration!

```Now add a single virtual host entry for your rails apps under Apache's sites-available directory.  You will need an IP address, or a CNAME in DNS for this to work correctly.  We will be using an [FONT=Courier New].htaccess[/FONT] file to add applications to the application server, so we need *AllowOverride* All for this directory.
```

# vi /etc/apache2/sites-available/apps.mydomain.tld

   <VirtualHost *:80>
      ServerName apps.mydomain.tld
      DocumentRoot /var/www/applications
      
      <Directory /var/www/applications>
         AllowOverride all
         Options -MultiViews
      </Directory>
   </VirtualHost>

```Once that's done, enable the new virtualhost with a2ensite
```


# a2ensite apps.mydomain.tld
Your choices are: apps.mydomain.tld default default-ssl
Which site(s) do you want to enable (wildcards ok)?
apps.mydomain.tld
Enabling site apps.mydomain.tld
Run '/etc/init.d/apache2 reload' to activate new configuration!

```Ok, now restart apache
```

# service apache2 restart
 * Restarting web server apache2  ... waiting [ OK ]

```we need an easy way for developers to deploy new applications.  We do this thorough the use of a [FONT=Courier New].htaccess[/FONT] file in the ruby application directory.  Root will own the file, but the developers will be given write access through the *webdevel* group which was previously setup on this server.  We also set the sticky bit on the application directory so people with write access cannot delete files they do not own (the [FONT=Courier New].htaccess[/FONT] file).
```

# mkdir -p /var/www/applications && \
chown root:webdevel /var/www/applications && \
chmod 1775 /var/www/applications && \
chmod g+w+s /var/www/applications

```Double-check your developer is in the webdevel group (or whatever other shared group you have them in)
```

# groups dude888
dude888 : users user-land webdevel

```Now, change to the app directory and create the .htaccess file with appropriate permissions
```

# cd /var/www/applications/
# touch .htaccess && chown root:webdevel .htaccess && chmod 664 .htaccess

```I happen to have a very simply RoR application to deploy so I will use rsync to do that.  In actuality, the developer would use *Capistrano* here or another code deployment utility.
```

# rsync -av /home/public_html/ruby/blah.app/ blah.app

```Now an important step here is to symlink the application's public directory to the name of the app you want to deploy. Again, the developer would do this part normally, hence the need for developer write access.  Important to note is that Passenger will NOT serve an app symlink'd from outside the directory tree.  Everything must be underneath the [FONT=Courier New]applications[/FONT] directory.
```

# ln -s blah.app/public blah

```Now edit the .htaccess file and add the *RackBaseURI* path for Passenger.  The *RailsEnv* is a left-over from testing; I don't know if it's needed or not. Some people reported Passenger would not work without it.
```

# vi .htaccess
   RailsEnv        development
   RackBaseURI     /blah

```When you add other apps, it would look like this
```

   RailsEnv        development
   RackBaseURI     /blah
   RackBaseURI     /foobar
   RackBaseURI     /another

``` That's it!  Now point your browser at [http://apps.mydomain.tld/blah](http://apps.mydomain.tld/blah) you should get your RoR app!

---

