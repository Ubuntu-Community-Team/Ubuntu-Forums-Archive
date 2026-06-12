---
title: "Bind9 runs but doesn't resolve"
date: 2008-08-29
forum: Server Platforms
---

### Post by corralejo on 2008-08-29
I loaded bind9 on my Ubuntu 8.04 server.  I have played with it for a while and it runs but doesn't resolve.  Can anyone help me with this?  I have read all the previous posts and how-to articlse without success.  Below are detailed file examples of what I have set up.  Please read through them as I have taken a lot of time to be complete.

/etc/hosts

127.0.0.1    localhost.localdomain localhost
127.0.1.1    server1
192.168.1.5  localhost.localdomain localhost posterstore.local

-----------------------------------
/etc/apache2/httpd.conf

ServerName  server1

------------------------------------

the /etc/bind/named.conf file has not been modified from default

-----------------------------------
/etc/bind/named.conf.local

zone "posterstore.local" {
    type master;
    file "/etc/bind/zones/posterstore.local.db";
    notify no;
};

zone "1.168.192.in-addr.arpa" {
    type master:
    notify no;
    file "/etc/bind/reverse/192.168.1";
};

-------------------------------------

/etc/bind/named.conf.options

options {

  directory "/var/cache/bind";

  forwarders {
    68.87.77.130;
    68.87.72.130;
  };

  auth-nxdomain no;  # conform to RFC1035
  listen-on-v6 { any: };
}

----------------------------------

/etc/bind/zones/posterstore.local.db

$TTL 1500
posterstore.local.  IN  SOA  server1.posterstore.local. (
  200808134
  2880
  3600
  604800
  38400
)
posterstore.local.  IN  NS  server1.posterstore.local.
server1             IN  A   192.168.1.5

--------------------------------------

/etc/bind/reverse/192.168.1

@  IN           SOA  server1.posterstore.local. (
   200808132    ;serial, todays date + todays serial #
   28800        ;refresh
   604800       ;retry
   604800       ;expire
   86400        ;minimum TTL
)
   IN           NS   server1.posterstore.local.
5  IN           PTR  posterstore.local

-------------------------------------

/etc/resolv.conf

search posterstore.local

nameserver  192.168.1.5
nameserver  68.87.77.130
nameserver  68.87.72.130

--------------------------------------

/etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

-------------------------------
I am on a local network behind a Linksys WRT54GS router that conects to comcast broad band.  The router provides my computers DHCP but my ubuntu server sits at static 192.168.1.5.  The router has the following DNS order

192.168.1.5
68.87.77.130
68.87.72.130

when I use the dig command as follows I get SERVFAIL
#dig posterstore.local

When I do an nslookup on my vista machine, >nslookup posterstore.local  I get "can't find posterstore.local, server failed.

No errors occur when I start my server and bind9 seems to be running it just doesn't work.  I have read about every help file I can find and have not been able to fix this.  Please let me know where I went wrong.  It's as if the DNS isn't even running.  I've seen other people in the forums with the same problem but no answers.

---

### Post by windependence on 2008-08-30
Unless you have hundreds of PCs on your network, you probably don't even need a DNS server running on your network. External DNS lookups can be done by inserting some public DNS servers in your /etc/resolv.conf file. I like to use the ones from OpenDNS.com.

For LAN name resolution, just insert entries for your server alias in the hosts file of your network PCs. On Windoze, the file is located at C:\windows\system32\drivers\etc\hosts. In most linux distros it is at /etc/hosts.

For your web sites, use the DNS control panel provided by your domain name registrar. No need for your own authoritative DNS server.

-Tim

---

### Post by corralejo on 2008-08-30
windependence,

Thanks for the advice.  I have found this information using google and it works fine.  The problem is that my DNS server still does not work.  Can anyone look over my files and tell me how to trouble shoot this problem I am having with bind9?  I put a lot of time into this project and would like to see it work.  I am testing several sites on the same server and would like to set them up in the DNS server.

Thanks
corralejo

---

### Post by windependence on 2008-08-30
I certainly understand your reasons for wanting to learn. I'll help you out tonight when I get to work if you still don't have it solved. ;)

-Tim

---

### Post by corralejo on 2008-08-30
Tim,

I would greatly appreciate any help I can get on this project.  I built the lamp server and it works great.  I even have Samba running on it.  No dice on the bind9 service though, it's just killing me.

Thanks
Nathan

---

### Post by corralejo on 2008-08-30
Tim,

Also I forgot to include the file in /etc/apache2/sites-available.  This is the file for the site that I have a symbolic link in /etc/apache2/sites-enabled

NameVirtualHost posterstore.local:80
<VirtualHost posterstore.local:80>
	ServerAdmin webmaster@localhost
	ServerName posterstore.local
	DocumentRoot /home/httpd/webapps/www/posterstore/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/httpd/webapps/www/posterstore/>
		Options Indexes FollowSymLinks MultiViews
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

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by corralejo on 2008-09-01
I worked on this on the weekend and it's still not working.  Can any gurus help me out?

Thanks
Nathan

---

### Post by corralejo on 2008-09-02
Still waiting on an answer on this.  I bought a book called Pro DNS and Bind for lack of feedback on this.  If anyone can help me out in the mean time I would appreciate it.

Thanks

---

### Post by windependence on 2008-09-02
I'm not free enough here to work on this for you right at the moment, but when I free up some time, I'll give it a shot. BIND isn't one of my fortes but it will do me good to help you troubleshoot it. Benefits us both. ;)

-Tim

---

### Post by corralejo on 2008-09-14
Ok now I've read the book Pro DNS and BIND.  I've tried several different setups. It still doesn't work.  There has to be some little thing I'm doing wrong.  Can someone help me with this?

Thanks

---

