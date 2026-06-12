---
title: "Need urgent help: Ruby on rails + LAMP(ubuntu, Apache, mySQL, PHP)"
date: 2011-09-01
forum: Server Platforms
---

### Post by KOHP0010 on 2011-09-01
Hello, everyone! I am a beginner to ubuntu and I require assistance in  installing the below applications. I have spent over a month researching  on just how to install them alone:lolflag:.
I need help with installing  and compiling( :sad:)Ruby on rails + LAMP(ubuntu, Apache, mySQL, PHP).. I have already installed Ubuntu 11.04 on my system. HELP HELP HELP!!!!!

Any help rendered would be greatly appreciated and popcorn would be given :popcorn::razz::razz::razz:

---

### Post by rubylaser on 2011-09-01
I would suggest using 10.04 LTS for a server rather than 11.04, but this should work either way.  This is all from my notes, and there are other configuration files that might need editing for your situation (php.ini, /etc/mysql/my.conf, etc), but this should get everything you asked for installed.

```
sudo -i
```

# Update your system
```
apt-get update && apt-get upgrade -y && apt-get dist-upgrade -y && reboot
```

# After Reboot
```
sudo -i
```
# Grab some packages
```
apt-get install build-essential bison openssl
libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev
libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3
libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev subversion
```


# Install RVM
```
bash < <(curl -s https://rvm.beginrescueend.com/install/rvm)
```

```
nano ~/.bashrc
```
# add this…
```
[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"
```

# Reload your profile
```
source ~/.bashrc
```

# Grab the latest version
```
rvm list known
```

# Then install (replace X with the number of the latest version)
```
rvm install 1.9.X
```

# Use that version
```
rvm --default use 1.9.X
```

# Update rubygems
```
gem update --system
gem update
```

# Install rails
```
gem install rails
```

# MySQL
```
apt-get install mysql-server mysql-client libmysqlclient-dev
```

 #Install Apache and Passenger

```
apt-get install apache2 apache2-prefork-dev
```

```
a2enmod ssl
a2enmod rewrite
a2enmod suexec
a2enmod include
a2enmod deflate
a2enmod expires
``` 

```
/etc/init.d/apache2 force-reload
```

# Restart Apache2
```
/etc/init.d/apache2 restart
```

# Install Passenger
```
gem install passenger
passenger-install-apache2-module
```

# Enable Passenger, Mod Deflate, and Mod Expires

After Passenger installs, you will see instructions to edit your Apache configuration file to add lines to the end of the file (they'll be different than what you see here).

```
nano /etc/apache2/apache2.conf
```

And paste this in...

```
# GZIP files
AddOutputFilterByType DEFLATE text/html text/css text/plain text/xml application/x-javascript
BrowserMatch ^Mozilla/4 gzip-only-text/html
BrowserMatch ^Mozilla/4\.0[678] no-gzip
BrowserMatch \bMSIE <img src="no-gzip" alt="" />gzip-only-text/html

# Expire Headers
ExpiresActive On
ExpiresDefault "access plus 10 years"

# Passenger **(change this section to match your passenger install)**
LoadModule passenger_module /usr/lib/ruby/gems/1.8/gems/passenger-2.0.3/ext/apache2/mod_passenger.so
PassengerRoot /usr/lib/ruby/gems/1.8/gems/passenger-2.0.3
PassengerRuby /usr/bin/ruby1.8
```

# Install PHP5
```
apt-get install php5
```

This is all from my notes the last time I did this, so some of the packages / version numbers may be different.  Also, this doesn't include creating mysql databases / setting permissions / editing your apache files / etc. But, it is a good start.

---

