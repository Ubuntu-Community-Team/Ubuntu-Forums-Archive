---
title: "Ajaxterm and https"
date: 2008-06-08
forum: Server Platforms
---

### Post by kenmiles on 2008-06-08
I have set up apache2 on Ubuntu 8.04 for SSL but when I try to connect I get the following error page on Firefox-

Secure Connection Failed
  An error occurred during a connection to kmiles.co.uk.
SSL received a record that exceeded the maximum permissible length.
(Error code: ssl_error_rx_record_too_long)

Can someone please point me in the right direction to fix this.

Thanks in advance, Kenneth.

---

### Post by quelx on 2008-06-08
From [http://www.mozilla.org/projects/security/pki/nss/ref/ssl/sslerr.html:](http://www.mozilla.org/projects/security/pki/nss/ref/ssl/sslerr.html:)
> SSL_ERROR_RX_RECORD_TOO_LONG 	-12263 	"SSL received a record that exceeded the maximum permissible length." 

This generally indicates that the remote peer system has a flawed implementation of SSL, and is violating the SSL specification.

Try this
[http://bug.gd/search/details/69648/ssl_error_rx_record_too_long](http://bug.gd/search/details/69648/ssl_error_rx_record_too_long)

If that doesn't work you need to recreate your apache certs.

---

### Post by kenmiles on 2008-06-08
> **quelx said:**
> From [http://www.mozilla.org/projects/security/pki/nss/ref/ssl/sslerr.html:](http://www.mozilla.org/projects/security/pki/nss/ref/ssl/sslerr.html:)


Try this
[http://bug.gd/search/details/69648/ssl_error_rx_record_too_long](http://bug.gd/search/details/69648/ssl_error_rx_record_too_long)

If that doesn't work you need to recreate your apache certs.

Thanks for that.
I think I have traced it after your reply to this in the error log -

kmiles.co.uk' does NOT match server name!

I have tried all different server names such as kenneth-desktop and localhost and my domain name but none work, so please where do I find the server name?

Regards, Kenneth.

---

### Post by quelx on 2008-06-08
What does **hostname -f** show?

EDIT: And if it's not right add a line in **/etc/hosts** with your IP address and fully qualified domain name.

```
192.168.1.102 myhostname.com
```

and restart apache

---

### Post by kenmiles on 2008-06-08
> **quelx said:**
> What does **hostname -f** show?

EDIT: And if it's not right add a line in **/etc/hosts** with your IP address and fully qualified domain name.

```
192.168.1.102 myhostname.com
```

and restart apache

/home/kenneth-->hostname -f
kenneth-desktop.gateway.2wire.net

[warn] RSA server certificate CommonName (CN) `kenneth-desktop.gateway.2wire.net' does NOT match server name!?

/etc/hosts
127.0.0.1 localhost
127.0.1.1 kenneth-desktop.kmiles.co.uk
213.123.183.61 kmiles.co.uk
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Does this information help, and thanks again for your time.
Regards, Kenneth.

---

### Post by quelx on 2008-06-08
change ```
127.0.1.1 kenneth-desktop.kmiles.co.uk
``` to ```
127.0.1.1 kmiles.co.uk
``` and restart apache (actually you may need to reboot because **hostname -f** will still show *kenneth-desktop.kmiles.co.uk*

---

### Post by kenmiles on 2008-06-08
> **quelx said:**
> change ```
127.0.1.1 kenneth-desktop.kmiles.co.uk
``` to ```
127.0.1.1 kmiles.co.uk
``` and restart apache (actually you may need to reboot because **hostname -f** will still show *kenneth-desktop.kmiles.co.uk*

[Sun Jun 08 17:48:02 2008] [warn] RSA server certificate CommonName (CN) `kmiles.co.uk' does NOT match server name!?

/etc/hosts
127.0.0.1 localhost
127.0.1.1 kmiles.co.uk
213.123.183.61 kmiles.co.uk
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

/home/kenneth-->hostname -f
kenneth-desktop.gateway.2wire.net

Sorry to be a pest but after a re-boot and changing the hosts file it still shows the above hostname.

Regards, Kenneth.

---

### Post by quelx on 2008-06-08
No worries, I want to figure this out too, I've done it in the past but never documented it, there is a hack of sorts to tell apache not to check the hostname variable but use the **ServerName** directive, but that really should only be used or virtual hosts, the primary webserver should *just work*. So I think...

What does ```
hostname -i
dig kenneth-desktop.kmiles.co.uk
dig kmiles.co.uk
cat /etc/hostname
``` show?

Try explicitly setting the hostname also.

```
echo kmiles.co.uk | sudo tee /etc/hostname
```

---

### Post by kenmiles on 2008-06-08
> **quelx said:**
> No worries, I want to figure this out too, I've done it in the past but never documented it, there is a hack of sorts to tell apache not to check the hostname variable but use the **ServerName** directive, but that really should only be used or virtual hosts, the primary webserver should *just work*. So I think...

What does ```
hostname -i
dig kenneth-desktop.kmiles.co.uk
dig kmiles.co.uk
cat /etc/hostname
``` show?

Try explicitly setting the hostname also.

```
echo kmiles.co.uk | sudo tee /etc/hostname
```

Here is all the output -
/home/kenneth-->hostname -i
213.123.183.61
/home/kenneth-->dig kenneth-desktop.kmiles.co.uk

; <<>> DiG 9.4.2 <<>> kenneth-desktop.kmiles.co.uk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 57077
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;kenneth-desktop.kmiles.co.uk.  IN      A

;; AUTHORITY SECTION:
kmiles.co.uk.           360     IN      SOA     ns1.everydns.net. hostmaster.kmiles.co.uk. 1212947007 1200 600 1209600 3600

;; Query time: 467 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Sun Jun  8 18:57:38 2008
;; MSG SIZE  rcvd: 109

/home/kenneth-->dig kmiles.co.uk

; <<>> DiG 9.4.2 <<>> kmiles.co.uk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64871
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;kmiles.co.uk.                  IN      A

;; ANSWER SECTION:
kmiles.co.uk.           300     IN      A       213.123.183.61

;; Query time: 223 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Sun Jun  8 18:58:12 2008
;; MSG SIZE  rcvd: 46

/home/kenneth-->cat /etc/hostname
kenneth-desktop
/home/kenneth-->echo kmiles.co.uk | sudo tee /etc/hostname
[sudo] password for kenneth:
kmiles.co.uk

Thanks again, Kenneth.

---

### Post by quelx on 2008-06-08
Does your webserver truly have a public ipaddress or is it sitting behind a firewall?

If it's behind a firewall */etc/hosts* needs to have the private **192.168.1.xxx** address.

```
192.168.1.xxx kmiles.co.uk
```

*and* your internal facing DNS needs to have **kmiles.co.uk** match **192.168.1.xxx** not the public address.  This won't affect anything outside your network.

After explicitly setting the hostname (the echo bit) and rebooting does **hostname -f** show the proper fqdn?

---

### Post by kenmiles on 2008-06-08
> **quelx said:**
> Does your webserver truly have a public ipaddress or is it sitting behind a firewall?

If it's behind a firewall */etc/hosts* needs to have the private **192.168.1.xxx** address.

```
192.168.1.xxx kmiles.co.uk
```

*and* your internal facing DNS needs to have **kmiles.co.uk** match **192.168.1.xxx** not the public address.  This won't affect anything outside your network.

this is from my router-

After explicitly setting the hostname (the echo bit) and rebooting does **hostname -f** show the proper fqdn?


		System 		Broadband Link 			Local Network 			Digital Voice 		Firewall 		Parental Controls 	
	
Site Map
Help
HomeHome
Summary
Wireless Settings
Fusion Settings
Advanced Settings
 
Edit Advanced Local Network Settings
WARNING
Modifying the settings on this page can impact the ability of computers on the local network to access your broadband connection. Modifications may also affect broadband-enabled applications and services running on the local network.
Settings
Help
Private Network

If you change the IP address range, you must renew the DHCP lease on all devices on the network.
				
	192.168.1.0 / 255.255.255.0 (default)
	172.16.0.0 / 255.255.0.0
	10.0.0.0 / 255.255.0.0
	Configure manually
	Router Address: 	
Warning
	Subnet Mask: 	
Warning
		Enable DHCP
	First DHCP Address: 	
Warning
	Last DHCP Address: 	
Warning
	Default DHCP Pool
Set DHCP Lease Time: 	
	hours
Help
Public Routed Subinterface
Enable
	Check ENABLE to create a route from the Internet to the public network specified below.
	Router Address: 	
Warning
	Subnet Mask: 	
Warning
	Auto Firewall Open
	Default DHCP Pool
Help
Public Proxied Subnet (NAT/Routed)
Enable
	This value will determine the public addresses available for using applications with your home network devices.

This information is provided by your ISP

	Broadband Network: 	213.123.183.61 / 255.255.255.252
	Subnet Mask: 	
Warning
	Auto Firewall Open
	Default DHCP Pool
Help
Display Settings
		Show inactive devices in network list
	
Current Settings
Private Network
Router Address: 	192.168.1.254
Subnet Mask: 	255.255.255.0
DHCP Range: 	192.168.1.64 - 192.168.1.253
	Allocated: 	2
	Available: 	188
Device List
PC 	kmiles.co.uk 	213.123.183.61

/home/kenneth-->hostname -f
kmiles.co.uk

Have amended host file with -
127.0.0.1 localhost
127.0.1.1 kmiles.co.uk
213.123.183.61 kmiles.co.uk
192.168.1.0 kmiles.co.uk

I am not sure about how to do this -
your internal facing DNS needs to have **kmiles.co.uk** match **192.168.1.xxx** not the public address.  This won't affect anything outside your network.

Regards, Kenneth.

---

### Post by quelx on 2008-06-08
What does **ifconfig eth0** show on the server?

---

### Post by kenmiles on 2008-06-08
> **quelx said:**
> What does **ifconfig eth0** show on the server?

/home/kenneth-->ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:16:ec:ea:d3:05
          inet addr:213.123.183.61  Bcast:213.123.183.63  Mask:255.255.255.252
          inet6 addr: fe80::216:ecff:feea:d305/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:997661 (974.2 KB)  TX bytes:1251572 (1.1 MB)
          Interrupt:19 Base address:0x2800

Regards, Kenneth.

---

### Post by quelx on 2008-06-08
First off, apologies, I though you had a private address on your server, oops.

*/etc/network/interfaces* should contain this line (or something like it, if it says dhcp change it to static and add the rest) leave the **lo** stuff at the top alone
cat */etc/hostname*
```
auto eth0
iface eth0 inet static
        address 213.123.183.61
        netmask 255.255.255.252
        gateway (not sure what this should be, if it's already set cool if not **route** should show a line *default  [COLOR="Red"]213.123.183.xxx[/COLOR]* use that number inplace of this comment)
        broadcast 213.123.183.63
        network 213.123.183.60
```

cat */etc/hosts*```

127.0.0.1 localhost
127.0.1.1 kmiles.co.uk
[COLOR="Red"]213.123.183.61 kmiles.co.uk[/COLOR]
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

cat */etc/hostname*
```
kmiles.co.uk
```

Reboot and let me know how it goes.

When you start apache it shouldn't complain about the hostname eg.
> apache2: Could not reliably determine the server's f...

---

### Post by quelx on 2008-06-08
Well if I haven't completely mucked up your apache installation I think I found the answer to the problems.

Apache is trying to serve ssl pages over port 80 and Firefox doesn't like that.  I assume you've already got your certs created, because apache2 is at least loading.  If not here is what you need to do.

create your certs if you havn't already (ignore the bit about **unable to write 'random state'** when you run **openssl x509 -req -days ...**)

**Common Name (eg, YOUR name) []:** is your fqdn **kmiles.co.uk**

**Generating a Certificate Signing Request (CSR)**
[https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html)

**HTTPS Configuration**
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

Edit /etc/apache2/sites-available/default under **<VirtualHost *>** add
```
SSLEngine on
SSLOptions +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key
```

then ```
sudo /etc/init.d/apache2 reload
```

---

### Post by kenmiles on 2008-06-09
I have had a lot of bother with mythtv when changing the hostname and I ended up starting from scratch with myth, so now that is working.
Here is my apache default file-

<VirtualHost *>
	ServerAdmin [email]mail@kmiles.co.uk[/email]
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
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



<VirtualHost *:443>
        ServerName ajaxterm.website.com
        HostnameLookups Double
        CustomLog /var/log/apache2/access.log combined env=!dontlog
        SetEnvIf Request_URI "^/u" dontlog
        ErrorLog /var/log/apache2/error.log
        Loglevel warn
        SSLEngine On
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key
        ProxyRequests Off
        <Proxy *>
                AuthUserFile /srv/ajaxterm/.htpasswd
                AuthName EnterPassword
                AuthType Basic
                require valid-user

                Order Deny,allow
                Allow from all
        </Proxy>
        ProxyPass / [http://localhost:8022/](http://localhost:8022/)
        ProxyPassReverse / [http://localhost:8022/](http://localhost:8022/)
</VirtualHost>

This is the output when I restart apache -
/home/kenneth-->sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                                                
Apache/2.2.8 mod_ssl/2.2.8 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide the pass phrases.

Server ajaxterm.website.com:443 (RSA)
Enter pass phrase:

OK: Pass Phrase Dialog successful.

But if I try to go to [https://kmiles.co.uk:8022](https://kmiles.co.uk:8022) I get -
Failed to Connect
The connection was refused when attempting to contact kmiles.co.uk:8022.

Can you tell from this what I am doing wrong, as it must be me!

Thanks again, Kenneth.

---

### Post by quelx on 2008-06-09
At the beginning of */etc/apache2/sites-enabled/default* change 

**<VirtualHost *>**
to 
**<VirtualHost *:80>**

and reload, retry

---

### Post by kenmiles on 2008-06-09
> **quelx said:**
> At the beginning of */etc/apache2/sites-enabled/default* change 

**<VirtualHost *>**
to 
**<VirtualHost *:80>**

and reload, retry

Same message, and this in the error log-
[Mon Jun 09 16:18:42 2008] [warn] RSA server certificate CommonName (CN) `kmiles.co.uk' does NOT match server name!?
[Mon Jun 09 16:18:42 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
Regards, Kenneth.

---

### Post by kenmiles on 2008-06-09
I have changed my default to this-

<VirtualHost *:443>
        ServerName kmiles.co.uk
  #      HostnameLookups Double
   #     CustomLog /var/log/apache2/access.log combined env=!dontlog
    #    SetEnvIf Request_URI "^/u" dontlog
     #   ErrorLog /var/log/apache2/error.log
      #  Loglevel warn
        SSLEngine On
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key
        ProxyRequests Off
        <Proxy *>
          #      AuthUserFile /srv/ajaxterm/.htpasswd
           #     AuthName EnterPassword
            #    AuthType Basic
             #   require valid-user

                Order Deny,allow
                Allow from all
        </Proxy>
        ProxyPass / [http://localhost:8022/](http://localhost:8022/)
        ProxyPassReverse / [http://localhost:8022/](http://localhost:8022/)
#	ProxyPass /ajaxterm/ [http://localhost:8022/](http://localhost:8022/)
 #      ProxyPassReverse /ajaxterm/ [http://localhost:8022/](http://localhost:8022/)

</VirtualHost>

and it works.

Thank you for all your help in staying with this problem and pointing me in the right direction.

All my thanks, Kenneth.

---

### Post by windependence on 2008-06-09
You guys are on a wild goose chase.

First off, he is behind a 2wire router, and he posted the router config page. His IPs and host file is all messed up.

He can call the server anything he wants but his hostname should be one single word. He should then set his domain to kmiles.co.uk. Then, change his hosts file to reflect the changes.

For example, if he calls the server "server", then his hostname should be just server. There should be no 127.0.1.1. His public IP should be natted back to his private IP on the network, so if his private IP is 192.168.0.2, then his hosts file should look something like this:

127.0.0.1     localhost  server
192.168.0.2   server.kmiles.co.uk

On the 2wire router there is a setting to forward your public IP back to the private one. 

He would also have to change his apache conf file so that his server name is server.kmiles.co.uk, he should have it listening on port 80 and 443.

If we start with that, I think we can get him up and running.

-Tim

---

### Post by quelx on 2008-06-09
I was on a goose chase until I realized his server does in fact have a public IP (it was running the entire time, despite my best efforts I never broke it)

```
inet addr:213.123.183.61 Bcast:213.123.183.63 Mask:255.255.255.252
```

Ubuntu adds *127.0.1.1* to */etc/hosts*, I don't know why (when apache2 is installed?), I'm sure there is a good reason for it.  It doesn't hurt since it's just a loopback address.

Setting the **ServerName** directive is not the proper way to fix this, I knew that would work from the beginning, but Apache (and all other Internet aware servers) for that matter should get the proper FQDN from **hostname -f** and the easiest way to get that done without setting up a DNS server of his own was to add it to */etc/hostname*.

If I'm mistaken well, let me know, for real.

---

