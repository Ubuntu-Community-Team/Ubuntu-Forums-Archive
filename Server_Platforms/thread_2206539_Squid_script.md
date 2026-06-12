---
title: "Squid script"
date: 2014-02-19
forum: Server Platforms
---

### Post by iebo on 2014-02-19
hello , 

how i could  get this auto squid proxy run without password authentication 


```

echo " "
echo "*****************************************************"
echo "WELCOME TO THE SQUID PROXY SERVER INSTALLATION SCRIPT"
echo "-----------------------------------------------------"
echo " "
echo " This script will set up a password protected, elite"
echo "             proxy on your target server"
echo " "
echo "*****************************************************"
echo " "
echo " "
echo "Please enter a user name for Squid:"
read u
echo " "
echo "Please enter a password (will be shown in plain text while typing):"
read p
echo " "

clear

a="`netstat -i | cut -d' ' -f1 | grep eth0`";
b="`netstat -i | cut -d' ' -f1 | grep venet0:0`";

if [ "$a" == "eth0" ]; then
  ip="`/sbin/ifconfig eth0 | awk -F':| +' '/inet addr/{print $4}'`";
elif [ "$b" == "venet0:0" ]; then
  ip="`/sbin/ifconfig venet0:0 | awk -F':| +' '/inet addr/{print $4}'`";
fi

apt-get update
apt-get -y install apache2-utils
apt-get -y install squid3

rm /etc/squid3/squid.conf

cat > /etc/squid3/squid.conf <<END
acl ip1 myip $ip
tcp_outgoing_address $ip ip1

auth_param basic program /usr/lib/squid3/ncsa_auth /etc/squid3/squid_passwd
acl ncsa_users proxy_auth REQUIRED
http_access allow ncsa_users

acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32
acl SSL_ports port 443
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl CONNECT method CONNECT

http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny all
http_port 3128

hierarchy_stoplist cgi-bin ?
coredump_dir /var/spool/squid3
cache deny all

refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern .        0    20%    4320

icp_port 3130

forwarded_for off

request_header_access Allow allow all
request_header_access Authorization allow all
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
END

htpasswd -b -c /etc/squid3/squid_passwd $u $p

service squid3 restart

clear

echo " "
echo "***************************************************"
echo "   Squid proxy server set up has been completed."
echo " "
echo "You can access your proxy server at $ip"
echo "on port 3128 with user name $u"
echo " "
echo "***************************************************"
echo " "
echo " "
```

every time i try to remove the lines from config  i guess they are responsible for authentication-
.
..the proxy come up with this  error 

[PHP]error 
the requested url could not be retrieved [/PHP]

i'm not able to access websites :mad:

thank u :popcorn:

---

### Post by SeijiSensei on 2014-02-19
Don't use that script.  Install Squid manually with the apt-get commands it uses:
```

sudo apt-get update
sudo apt-get -y install apache2-utils
sudo apt-get -y install squid3

```
then edit /etc/squid3/squid.conf to meet your local requirements.  The default installation has no authentication.

---

### Post by koenn on 2014-02-19
what sensei said, 
and read the (f...) manual: you will have to set an ACL. usually one simply allows a specific network range the  use of  the proxy. 
[https://help.ubuntu.com/12.04/serverguide/squid.html](https://help.ubuntu.com/12.04/serverguide/squid.html)  - item 3 and following.

---

### Post by iebo on 2014-02-19
> **SeijiSensei said:**
> Don't use that script.  Install Squid manually with the apt-get commands it uses:
```

sudo apt-get update
sudo apt-get -y install apache2-utils
sudo apt-get -y install squid3

```
then edit /etc/squid3/squid.conf to meet your local requirements.  The default installation has no authentication.

hey  thank u for the post 

but i'm  always doing  something wrong with the config  setting ...  and the squid proxy never worked for me

maybe because i don&#8217;t know  what the basic required lines in   /etc/squid3/squid.conf  to make squid run smoothly 

the script above does work though :P 

its debian vps

---

### Post by iebo on 2014-02-19
> **koenn said:**
> what sensei said, 
and read the (f...) manual: you will have to set an ACL. usually one simply allows a specific network range the  use of  the proxy. 
[https://help.ubuntu.com/12.04/serverguide/squid.html](https://help.ubuntu.com/12.04/serverguide/squid.html)  - item 3 and following.

sorry ,i'm not sure about this rules  :confused: no matter what i try 

thanks

---

### Post by koenn on 2014-02-19
don't use that script.
squid comes with a default config file* that works * . That script *replaces it *.

the only caveat is that the default conf lacks an acl, so you need to add that - eg
```

acl  fortytwo_network src 192.168.42.0/24
http_access allow fortytwo_network

```

replace the network number with something appropriate for your environment.

---

### Post by SeijiSensei on 2014-02-19
I wonder if by "auto squid proxy" you mean a "transparent" proxy, one that does not require any settings in the browser to make use of it.  If so, that requires additional things like iptables rules to redirect outbound HTTP traffic through the proxy. 

To begin with, did you configure your browser to use the proxy?  In Firefox, use Edit > Preferences >Network > Settings.

---

### Post by iebo on 2014-02-19
my computer network ... the one trying to connect not the vps right ?

i tried  

acl  fortytwo_network src 192.168.1.0/16  http_access allow fortytwo_network

 then restart squid its not working  :(

dont know much more

  "Access  control configuration prevents your request from being allowed at this  time. Please contact your service provider if you feel this is  incorrect.

  Your cache administrator is webmaster"

 

> **koenn said:**
> don't use that script.
squid comes with a default config file* that works * . That script *replaces it *.

the only caveat is that the default conf lacks an acl, so you need to add that - eg
```

acl  fortytwo_network src 192.168.42.0/24
http_access allow fortytwo_network

```

replace the network number with something appropriate for your environment.

---

### Post by iebo on 2014-02-19
> **SeijiSensei said:**
> I wonder if by "auto squid proxy" you mean a "transparent" proxy, one that does not require any settings in the browser to make use of it.  If so, that requires additional things like iptables rules to redirect outbound HTTP traffic through the proxy. 

To begin with, did you configure your browser to use the proxy?  In Firefox, use Edit > Preferences >Network > Settings.

i meant auto installation ,

yes i'm using  http proxy on firefox to point the server ip and squid port 3128

---

### Post by SeijiSensei on 2014-02-20
The order of rules in squid.conf is critical.  If you added your rules below the default "http_access deny all" rule, then your rules will never be reached.  All the allow rules must come above any deny rules.

---

### Post by iebo on 2014-02-20
> **SeijiSensei said:**
> The order of rules in squid.conf is critical.  If you added your rules below the default "http_access deny all" rule, then your rules will never be reached.  All the allow rules must come above any deny rules.

hello seiji thanks, i have just got it work  .. what i did is allowing my public ip like this

acl stupidsingleip src myip
http_access allow stupidsingleip

 "http_access deny all" was commented #

---

### Post by SeijiSensei on 2014-02-21
If the proxy is visible over the Internet, you'll want to uncomment that deny rule.  Otherwise it will be discovered and exploited by people wanting to hide their tracks while downloading dodgy items by using your public IP.

---

### Post by iebo on 2014-02-22
> **SeijiSensei said:**
> If the proxy is visible over the Internet, you'll want to uncomment that deny rule.  Otherwise it will be discovered and exploited by people wanting to hide their tracks while downloading dodgy items by using your public IP.


its not commented now ,when i visit my ip address on browser i only see

 " it works ! This is the default web page for this server.
The web server software is running but no content has been added, yet."  exactly like lamp server  homepage  ..but cant find any html/php file inside the root of my server that might store this text :confused: 


ps: if i need to setup transparent proxy with iptables will this rules added to vps only or both systems ?

tnx :popcorn:

---

### Post by SeijiSensei on 2014-02-23
You must not have any virtual hosts defined.  The "It works!" is the default index.html in /var/www, the default DocumentRoot.  See /etc/apache2/sites-available/default.

---

### Post by iebo on 2014-02-24
> **SeijiSensei said:**
> You must not have any virtual hosts defined.  The "It works!" is the default index.html in /var/www, the default DocumentRoot.  See /etc/apache2/sites-available/default.

okay understand

---

