---
title: "Help with proxy setup"
date: 2008-10-27
forum: Server Platforms
---

### Post by sadie8686 on 2008-10-27
Hi,
  I don't know if I'm in the right area of the forum, but I am trying to set up a proxy server on Ubuntu 8.04.  I am following a very reliable guide, but when I test it by going to my internet browser and putting a check in the HTTP and HTTPS boxes and putting my first IP in and the username & password with the port 3128. The browser can not navigate to any page with these settings.  I have started over 3 times and still can't get the IP's to work.  My hosting provider says my application might have its own channel, whatever that means.  I saw no mention of such in the guide.

This is what I am putting in the "sources.list" file:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security main restricted universe

I then created a new directory and put a new file named proxy.sh in it, see below:

#!/bin/sh
apt-get update
apt-get install apache2
apt-get install squid3
touch /etc/squid3/squid_passwd
chmod +r /etc/squid3/squid_passwd
/etc/init.d/apache2 stop
update-rc.d -f apache2 remove

I then run that command in the control panel and say yes when prompted twice.  Then I create my accounts using the appropriate command and type password twice for each and get no error.
Then I find the "ncsa_auth file", then I edit the squid.conf file with this below:

logfile_rotate 5
emulate_httpd_log yes
server_persistent_connections off
forwarded_for off

http_port 3128 

auth_param basic program /usr/lib/squid3/ncsa_auth /etc/squid3/squid_passwd
acl ncsa_users proxy_auth REQUIRED
auth_param basic children 5
auth_param basic realm Unblock
auth_param basic credentialsttl 1 hours

acl user1 proxy_auth account1
acl user2 proxy_auth account2

tcp_outgoing_address 14.131.41.146 user1
tcp_outgoing_address 14.131.41.147 user2


acl manager proto cache_object

http_access allow ncsa_users
http_access allow user1 user2
http_access allow all

request_header_access Allow allow all
request_header_access Authorization allow all
request_header_access WWW-Authenticate allow all
request_header_access Proxy-Authorization allow all
request_header_access Proxy-Authenticate allow all
request_header_access Cache-Control allow all
request_header_access Content-Encoding allow all
request_header_access Content-Length allow all
request_header_access Content-Type allow all
request_header_access Date allow all
request_header_access Expires allow all
request_header_access Host allow all
request_header_access If-Modified-Since allow all
request_header_access Last-Modified allow all
request_header_access Location allow all
request_header_access Pragma allow all
request_header_access Accept allow all
request_header_access Accept-Charset allow all
request_header_access Accept-Encoding allow all
request_header_access Accept-Language allow all
request_header_access Content-Language allow all
request_header_access Mime-Version allow all
request_header_access Retry-After allow all
request_header_access Title allow all
request_header_access Connection allow all
request_header_access Proxy-Connection allow all
request_header_access User-Agent allow all
request_header_access Cookie allow all
request_header_access All deny all


miss_access allow ncsa_users
http_reply_access allow ncsa_users


Then I make sure the "acl user1 proxy_auth account1" and such are all created, & the tcp_outgoing_address (insert IP) user1 is created for all.  Then the "http_access allow user 1 user 2, etc is created.  Then I save that & restart the squid from the control panel.

---

### Post by sadie8686 on 2008-10-27
Hi,
  I don't know if I'm in the right area of the forum, but I am trying to set up a proxy server on Ubuntu 8.04.  I am following a very reliable guide, but when I test it by going to my internet browser and putting a check in the HTTP and HTTPS boxes and putting my first IP in and the username & password with the port 3128. The browser can not navigate to any page with these settings.  I have started over 3 times and still can't get the IP's to work.  My hosting provider says my application might have its own channel, whatever that means.  I saw no mention of such in the guide.

This is what I am putting in the "sources.list" file:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security main restricted universe

I then created a new directory and put a new file named proxy.sh in it, see below:

#!/bin/sh
apt-get update
apt-get install apache2
apt-get install squid3
touch /etc/squid3/squid_passwd
chmod +r /etc/squid3/squid_passwd
/etc/init.d/apache2 stop
update-rc.d -f apache2 remove

I then run that command in the control panel and say yes when prompted twice.  Then I create my accounts using the appropriate command and type password twice for each and get no error.
Then I find the "ncsa_auth file", then I edit the squid.conf file with this below:

logfile_rotate 5
emulate_httpd_log yes
server_persistent_connections off
forwarded_for off

http_port 3128 

auth_param basic program /usr/lib/squid3/ncsa_auth /etc/squid3/squid_passwd
acl ncsa_users proxy_auth REQUIRED
auth_param basic children 5
auth_param basic realm Unblock
auth_param basic credentialsttl 1 hours

acl user1 proxy_auth account1
acl user2 proxy_auth account2

tcp_outgoing_address 14.131.41.146 user1
tcp_outgoing_address 14.131.41.147 user2


acl manager proto cache_object

http_access allow ncsa_users
http_access allow user1 user2
http_access allow all

request_header_access Allow allow all
request_header_access Authorization allow all
request_header_access WWW-Authenticate allow all
request_header_access Proxy-Authorization allow all
request_header_access Proxy-Authenticate allow all
request_header_access Cache-Control allow all
request_header_access Content-Encoding allow all
request_header_access Content-Length allow all
request_header_access Content-Type allow all
request_header_access Date allow all
request_header_access Expires allow all
request_header_access Host allow all
request_header_access If-Modified-Since allow all
request_header_access Last-Modified allow all
request_header_access Location allow all
request_header_access Pragma allow all
request_header_access Accept allow all
request_header_access Accept-Charset allow all
request_header_access Accept-Encoding allow all
request_header_access Accept-Language allow all
request_header_access Content-Language allow all
request_header_access Mime-Version allow all
request_header_access Retry-After allow all
request_header_access Title allow all
request_header_access Connection allow all
request_header_access Proxy-Connection allow all
request_header_access User-Agent allow all
request_header_access Cookie allow all
request_header_access All deny all


miss_access allow ncsa_users
http_reply_access allow ncsa_users


Then I make sure the "acl user1 proxy_auth account1" and such are all created, & the tcp_outgoing_address (insert IP) user1 is created for all.  Then the "http_access allow user 1 user 2, etc is created.  Then I save that & restart the squid from the control panel.

---

### Post by overdrank on 2008-10-27
Hi and welcome, Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by sadie8686 on 2008-10-28
I'm also using HyperVM control panel.

---

