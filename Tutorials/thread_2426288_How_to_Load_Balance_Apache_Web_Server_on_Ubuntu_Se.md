---
title: "How to Load Balance Apache Web Server on Ubuntu Server 18.04 LTS"
date: 2019-09-06
forum: Tutorials
---

### Post by LHammonds on 2019-09-06
Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

Link to original post: [HammondsLegacy Forums]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=260") (best when viewed at original location due to custom formatting)

[SIZE=4]High-level overview[/SIZE]

HAProxy is a free, very fast and reliable solution offering high availability, load balancing, and proxying for TCP and HTTP-based applications. It is particularly suited for very high traffic web sites and powers quite a number of the world's most visited ones

This tutorial will cover how to setup a redundant HAProxy system which will direct traffic to redundant web servers.  This will provide high availability when server goes offline...for such things as maintenance tasks.

The proxy servers will route both secured and unsecured web traffic to the web servers and let the web servers determine how they are going to handle SSL rules and certificates.  This will make issuing and renewing certificates much less complicated than handling them at the proxy level.

This is an overview image of a highly-available web server platform.
This article covers the web load balancers.
[IMG]http://hammondslegacy.com/images/linux/design-ha-lamp-service.jpg[/IMG]

[SIZE=4]Tools utilized in this process[/SIZE]

[LIST]
[*][Ubuntu Server]("https://www.ubuntu.com/download/alternative-downloads#alternate-ubuntu-server-installer") 18.04.2 LTS, 64-bit 
[*]HAProxy 1.8.8 
[*]Keepalived 1.3.9 
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.71 
[*][VMware vSphere]("http://www.vmware.com/products/vsphere/overview.html") 6.0.0 
[*][VirtualBox]("http://www.virtualbox.org/") 6.0.10 
[/LIST]

[SIZE=4]Helpful links[/SIZE]

The list below are sources of information that was helpful in the creation of this document.

[LIST]
[*][HAProxy Documentation]("http://www.haproxy.org/#docs") 
[*][Keepalived Documentation]("https://www.keepalived.org/manpage.html") 
[*][backreference.org - Load balancing and HA for multiple applications]("https://backreference.org/2012/04/25/load-balancing-and-ha-for-multiple-applications-with-apache-haproxy-and-keepalived/") 
[*][tecadmin.net - How to Setup HAProxy Load Balancer on Ubuntu 18.04 and 16.04]("https://tecadmin.net/how-to-setup-haproxy-load-balancing-on-ubuntu-linuxmint/") 
[/LIST]

[SIZE=4]Assumptions[/SIZE]
 
This documentation will need to make use of some very-specific information that will most-likely be different for each person / location. And as such, this information will be noted in this section. They will be highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using these "place-holder" values.

Under no circumstance should you use the actual values listed below. They are place-holders for the real thing. This is just a checklist template you need to have answered before you start the install process.

Wherever you see [COLOR=red]RED[/COLOR] in this document, you need to substitute it for you will use in your environment.

[LIST]
[*]Internet domain: [COLOR=red]mysite.mydomain.com[/COLOR] -> [COLOR=red]PublicIP[/COLOR] -> Firewall -> [COLOR=red]192.168.107.82[/COLOR] (VirtualIP) 
[*]Load Balancer #1 server name: [COLOR=red]srv-lb1[/COLOR] (master) 
[*]Load Balancer #1 Internal IP address: [COLOR=red]192.168.107.83[/COLOR] 
[*]Load Balancer #2 server name: [COLOR=red]srv-lb2[/COLOR] (slave) 
[*]Load Balancer #2 Internal IP address: [COLOR=red]192.168.107.84[/COLOR] 
[*]Ubuntu Admin ID: [COLOR=red]administrator[/COLOR] 
[*]Ubuntu Admin Password: [COLOR=red]myadminpass[/COLOR] 
[*]Email Server Name (remote): [COLOR=red]srv-mail[/COLOR] 
[*]Email Server Internal IP (remote): [COLOR=red]192.168.107.25[/COLOR] 
[*]Web Server #1: [COLOR=red]web1.mydomain.com[/COLOR], Internal IP Address: [COLOR=red]192.168.107.91[/COLOR] 
[*]Web Server #2: [COLOR=red]web2.mydomain.com[/COLOR], Internal IP Address: [COLOR=red]192.168.107.92[/COLOR] 
[*]Web Server #3: [COLOR=red]web3.mydomain.com[/COLOR], Internal IP Address: [COLOR=red]192.168.107.93[/COLOR] 
[/LIST]

Load Balancer Servers - Setup two Ubuntu servers for use as the HAProxy servers.  This tutorial assumes the server was configured according to this tutorial: [How to install and configure Ubuntu Server]("https://ubuntuforums.org/showthread.php?t=2389846")

Web Servers - Setup three Ubuntu servers for use as the web servers.  This tutorial assumes the server was configured according to this tutorial: [How to Install Apache Web Server on Ubuntu Server 18.04 LTS]("https://ubuntuforums.org/showthread.php?t=2426285")

It is also assumed the reader knows how to use the VI editor. If not, you will need to [beef up your skill set]("http://www.washington.edu/computing/unix/vi.html") or use a different editor in place of it.

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Install Keepalived[/SIZE]

Run this command on both load balance servers:
```
sudo apt install keepalived
```

[SIZE=4]Master Load Balancer Firewall Rules[/SIZE]

Edit the firewall script that was created during the initial setup of the server (if you [followed my instructions]("https://ubuntuforums.org/showthread.php?t=2389846&page=2&p=13758735#post13758735")):
```
vi /var/scripts/prod/en-firewall.sh
```

Add (or enable) the following:

NOTE: If you have more than 1 backup load balancer (VRRP Router), be sure to add their IP addresses as well.

```
echo "Adding Web Server rules"
ufw allow proto tcp to any port 80 comment 'HTTP' 1>/dev/null 2>&1
ufw allow proto tcp to any port 443 comment 'HTTPS' 1>/dev/null 2>&1
echo "Adding VRRP rules"
ufw allow to 224.0.0.18 comment 'VRRP Broadcast' 1>/dev/null 2>&1
ufw allow from 192.168.107.84 comment 'VRRP Router' 1>/dev/null 2>&1

```

Run the updated rules:

```
/var/scripts/prod/en-firewall.sh
```

[SIZE=4]Slave Load Balancer Firewall Rules[/SIZE]

```
vi /var/scripts/prod/en-firewall.sh
```

Add the following:

```
echo "Adding Web Server rules"
ufw allow proto tcp to any port 80 comment 'HTTP' 1>/dev/null 2>&1
ufw allow proto tcp to any port 443 comment 'HTTPS' 1>/dev/null 2>&1
echo "Adding VRRP rules"
ufw allow to 224.0.0.18 comment 'VRRP Broadcast' 1>/dev/null 2>&1
ufw allow from 192.168.107.83 comment 'VRRP Router' 1>/dev/null 2>&1

```

Run the updated rules:

```
/var/scripts/prod/en-firewall.sh
```

[SIZE=4]Master Keepalive Config[/SIZE]

On the master server (srv-lb1), create the keepalive configuration file:

```
sudo touch /etc/keepalived/keepalived.conf
sudo chown root:root /etc/keepalived/keepalived.conf
sudo chmod 600 /etc/keepalived/keepalived.conf
```

Edit the configuration file:
```
sudo vi /etc/keepalived/keepalived.conf
```

Add the following to the file (substituting for your own values):
```
global_defs {
  notification_email {
    my_email@mydomain.com
  }
  notification_email_from keepalived@mydomain.com
  smtp_server 192.168.107.25
  smtp_connect_timeout 30
}
vrrp_script chk_haproxy {
  script "/usr/bin/killall -0 haproxy"
  interval 1            # check every second
  weight 2              # add 2 points of priority if OK
}
vrrp_instance VI_1 {
  interface ens32
  state MASTER
  smtp_alert
  virtual_router_id 51  # Should be same on all LBs
  priority 101          # 101 on master, 100 on slaves
  advert_int 1
  authentication {
    auth_type PASS
    auth_pass 1111
  }
  virtual_ipaddress {
    192.168.107.82
  }
  track_script {
    chk_haproxy
  }
}

```

Restart the service:
```
sudo systemctl restart keepalived
```

[SIZE=4]Slave Keepalive Config[/SIZE]

On the slave server (srv-lb2), create the keepalive configuration file:

```
sudo touch /etc/keepalived/keepalived.conf
sudo chown root:root /etc/keepalived/keepalived.conf
sudo chmod 600 /etc/keepalived/keepalived.conf
```

Edit the configuration file:
```
sudo vi /etc/keepalived/keepalived.conf
```

Add the following to the file (substituting for your own values):
```
global_defs {
  notification_email {
    my_email@mydomain.com
  }
  notification_email_from keepalived@mydomain.com
  smtp_server 192.168.107.25
  smtp_connect_timeout 30
}
vrrp_script chk_haproxy {
  script "/usr/bin/killall -0 haproxy"
  interval 1            # check every second
  weight 2              # add 2 points of priority if OK
}
vrrp_instance VI_1 {
  interface ens32
  state MASTER
  smtp_alert
  virtual_router_id 51  # Should be same on all LBs
  priority 100          # 101 on master, 100 on slaves
  advert_int 1
  authentication {
    auth_type PASS
    auth_pass 1111
  }
  virtual_ipaddress {
    192.168.107.82
  }
  track_script {
    chk_haproxy
  }
}

```

Restart the service:
```
sudo systemctl restart keepalived
```

[SIZE=4]Test Keepalived[/SIZE]

You should be able to ping the virtual IP address at this point.  If you reboot srv-lb1 while continuously pinging the virtual IP, you should only see 1 or maybe 2 drops in the ping when the slave takes over for the master.  When the master comes back, another 1 or 2 drops in the ping will occur again as the virtual IP moves back from the slave to the master.

This is what the master NIC should look like (while active):

```
# ip addr show ens32
```
```
2: ens32: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:50:56:bf:27:cc brd ff:ff:ff:ff:ff:ff
    inet 192.168.107.83/24 brd 192.168.107.255 scope global ens32
       valid_lft forever preferred_lft forever
    inet 192.168.107.82/32 scope global ens32
       valid_lft forever preferred_lft forever
    inet6 fe80::250:56ff:febf:27cc/64 scope link
       valid_lft forever preferred_lft forever

```

This is what the slave NIC should look like (while inactive):

```
# ip addr show ens32
```

```
2: ens32: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:50:56:bf:6a:52 brd ff:ff:ff:ff:ff:ff
    inet 192.168.107.84/24 brd 192.168.107.255 scope global ens32
       valid_lft forever preferred_lft forever
    inet6 fe80::250:56ff:febf:6a52/64 scope link
       valid_lft forever preferred_lft forever

```

When the slave NIC is active with the virtual IP, you will see the virtual IP on it just like the master.

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Install HAProxy[/SIZE]

Run this command on both load balance servers:
```
sudo apt install haproxy
```

[SIZE=4]Name Resolution[/SIZE]

You can modify your host file for name resolution and just use the names of servers in your configuration files rather than the IP addresses. If a server IP changes in the future, you only need to modify the host which is much easier than tracking down various application configuration files.  You could do this with an internal DNS server but I prefer using the local host file for fastest resolution.

Edit the local host file (on all load balance servers):
```
sudo vi /etc/hosts
```

Add the web servers (substituting for your own values):
```

192.168.107.103 srv-web1
192.168.107.104 srv-web2
192.168.107.105 srv-web3

```

[SIZE=4]Allow Virtual IP Binding[/SIZE]

If you try to bind the inactive proxy to an IP it is not currently using (because the other proxy is using it) then it will fail to load the service.  We need to modify the system to allow binding to a non-local IP that is not currently active.

On both load balance servers, edit the sysctl.conf file:
```
sudo vi /etc/sysctl.conf
```

Add the following to the end of the file:
```
net.ipv4.ip_nonlocal_bind=1
```

Activate the change:
```
sysctl -p
```

[SIZE=4]HAProxy Configuration[/SIZE]

This is the default ownership and file permission settings of the configuration file:
```
sudo chown root:root /etc/haproxy/haproxy.cfg
sudo chmod 644 /etc/haproxy/haproxy.cfg
```

Backup the original configuration file (on both servers):

```
sudo cp /etc/haproxy/haproxy.cfg /etc/haproxy/haproxy.bak
```

Edit the configuration file (on all load balance servers):
```
sudo vi /etc/haproxy/haproxy.cfg
```

Add the following to the bottom (substituting your own values)
```

frontend fe-www-http
  ## Bind to port 80 on the virtual IP
  bind 192.168.107.82:80
  ## http mode allows access to http-specific options when not using SSL.
  mode http
#  mode tcp
  ## Might not want to do this if web servers limit access to just load balancer
  default_backend be-www-http

frontend fe-www-https
  ## Bind to port 443 on the virtual IP
  bind 192.168.107.82:443  #ssl crt ./haproxy-cert.pem
  ## tcp mode is required if encrypting with SSL since headers cannot be read.
  mode tcp
  ## Must use tcplog when using tcp mode.
  option tcplog
  ## Ensure the forwarded request includes the actual client IP address.
  ## Might not want to do this if web servers limit access to just load balancer
  default_backend be-www-https

## Balance between the various backend servers (unencrypted).
backend be-www-http
  ## http mode allows access to http-specific options when not using SSL.
  mode http
  ## Various policies for determining how to route traffic to the servers.
#  balance first
#  balance leastconn
  balance roundrobin
#  balance source
#  balance static-rr
  ## Ensure the forwarded request includes the actual client IP address.
  ## NOTE: This is not possible when packets are encrypted with SSL.
  option forwardfor
#  http-request set-header X-Forwarded-Port %[dst_port]
#  http-request set-header X-Client-IP %[src]
  server http-01 srv-web1 weight 1 check port 80 rise 2 fall 3 inter 2000 fastinter 1000 downinter 5000
  server http-02 srv-web2 weight 1 check port 80 rise 2 fall 3 inter 2000 fastinter 1000 downinter 5000
  server http-03 srv-web3 weight 1 check port 80 rise 2 fall 3 inter 2000 fastinter 1000 downinter 5000

## Balance between the various backend servers (encrypted).
backend be-www-https
  ## tcp mode is required if encrypting with SSL since headers cannot be read.
  mode tcp
  ## Various policies for determining how to route traffic to the servers.
#  balance first
#  balance leastconn
  balance roundrobin
#  balance source
#  balance static-rr
  server https-01 srv-web1 weight 1 check port 443 rise 2 fall 3 inter 2000 fastinter 1000 downinter 5000
  server https-02 srv-web2 weight 1 check port 443 rise 2 fall 3 inter 2000 fastinter 1000 downinter 5000
  server https-03 srv-web3 weight 1 check port 443 rise 2 fall 3 inter 2000 fastinter 1000 downinter 5000

## HAProxy stats web gui - This entire section is optional.
listen stats
  ## Setup listener on port 9000 on any interface.
  bind *:9000
  ## http mode so a web browser can be used to access it.
  mode http
  ## Enable metrics to be recorded.
  stats enable
  ## Configure the URI.  Example: http://192.168.107.83:9000/stats
  stats uri /stats
  ## How long the browser waits before refreshing the page.
  stats refresh 30s
  ## Title for popup window.
  stats realm HAProxy\ Statistics
  ## Hide the HAProxy version. Ex: version 1.8.8-1ubuntu0.4, released 2019/01/24
  stats hide-version
  ## Define user credentials.
  stats auth haproxy:haproxy
  stats auth viewer:viewer
  ## Allows taking down and bringing up backend servers.
  stats admin if TRUE

```

Validate the changes to the configuration files:
```
sudo haproxy -f /etc/haproxy/haproxy.cfg -c
```

On both servers, restart the proxy service:
```
sudo systemctl restart haproxy
```

Verify that the service started and is running (active):
```
systemctl status haproxy
```

You can also verify it is listening on the expected ports:
```
sudo netstat -ntlp | grep haproxy
```

Output:
```
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      20102/haproxy
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      20102/haproxy
tcp        0      0 0.0.0.0:9000            0.0.0.0:*               LISTEN      20102/haproxy
```

Open a web browser and have a look at the statistics page at [http://192.168.107.82:9000/stats/](http://192.168.107.82:9000/stats/)

[IMG]http://hammondslegacy.com/images/linux/haproxy-web.jpg[/IMG]

---

### Post by LHammonds on 2019-09-06
Configure Apache servers to only allow traffic from the internal subnet where the load balance servers exist.  You can also restrict access further by specifying just the load balancer IP addresses directly

Edit the website's configuration file:
```
sudo vi /etc/apache2/sites-available/mysite.mydomain.com-ssl.conf
```

Modify the Directory section like this to allow all IP addresses on the internal subnet:
```
  <Directory /var/www/mysite.mydomain.com/>
    <IfModule mod_authz_core.c>
      <RequireAny>
        ## Only allow access from the internet network (Proxy)
        Require ip 192.168.107.0/24
      </RequireAny>
    </IfModule>
  </Directory>

```

Modify the Directory section like this to specifically allow just the load balancer IP addresses:
```
  <Directory /var/www/mysite.mydomain.com/>
    <IfModule mod_authz_core.c>
      <RequireAny>
        ## Only allow access from the internet network (Proxy)
        Require ip 192.168.107.82
        Require ip 192.168.107.83
        Require ip 192.168.107.84
      </RequireAny>
    </IfModule>
  </Directory>

```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Logging Client IP[/SIZE]

When the web server is behind a proxy or load balancer, the frontend server's IP will always show up as the client IP accessing the website.  To address this, we will make some changes to utilize the "X-Forwarded-For" header.

NOTE: This only works for the non-encrypted sites (no SSL)

Edit the haproxy configuration file on all load balance servers:
```
sudo vi /etc/haproxy/haproxy.cfg
```

Add this line to each of your non-ssl frontend sections:
```
 option forwardfor
```

Restart the service:
```
sudo systemctl restart haproxy
```

Enable Apache's remoteip mod on each web server:
```
sudo a2enmod remoteip
```

Edit Apache's configuration file:
```
sudo vi /etc/apache2/apache2.conf
```

Add this:
```
RemoteIPHeader X-Forwarded-For
```

Find this:
```
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
```
Replace with this:
```
LogFormat "%a %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
```

The %a comes from the remoteip mod and records the client IP instead of the hostname.

Restart the service:
```
sudo systemctl restart apache2
```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Test via PHP[/SIZE]

If you already have your database cluster ready to use, let's setup a test to show what web server the browser hits as well as which database was used in the backend.

The web server will not know anything about the backend database servers because they look like a single database from the perspective of the web application.  In order to tell what database server we are using, we will create a trigger upon insert that will cause the database server to append its hostname into the data stream.

[SIZE=4]Step #1 - Create a test database[/SIZE]

Connect to one of the database nodes in the cluster and run the following commands:

```

#mysql -u root -p
CREATE DATABASE testdb CHARACTER SET utf8 COLLATE utf8_bin;
USE testdb;
CREATE TABLE testdb.testtbl (id INT NOT NULL AUTO_INCREMENT, web VARCHAR(100) NOT NULL, db VARCHAR(100) NULL, datecreated TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP, PRIMARY KEY ( id ));
DELIMITER $$
CREATE TRIGGER dbname_before_insert BEFORE INSERT ON testtbl FOR EACH ROW BEGIN select variable_value INTO @dbname FROM information_schema.global_variables WHERE variable_name = 'hostname'; SET NEW.db = @dbname; END$$
DELIMITER ;
GRANT ALL PRIVILEGES ON testdb.* TO 'testdbuser'@'%' IDENTIFIED BY 'testdbuserpass!';
FLUSH PRIVILEGES;
exit

```

[SIZE=4]Step #2 - Create the PHP web page[/SIZE]

On all of the web servers, create the test page:
```

sudo touch /var/www/mysite.mydomain.com/testsql.php
sudo chown www-data:www-data  /var/www/mysite.mydomain.com/testsql.php
sudo chmod 644  /var/www/mysite.mydomain.com/testsql.php
sudo vi  /var/www/mysite.mydomain.com/testsql.php

```

Add the following code to the file:
```

HTML CODE BLOCKED
SEE ORIGINAL SITE IN FIRST POST FOR THE HTML CODE HERE

```

[SIZE=4]Step #3 - Access the page from a browser[/SIZE]

Open a browser and access the test page from your load balancer's virtual IP:

```
https://mysite.mydomain.com
```

Press CTRL+F5 a few times to force a reload of the page.  Each time you do this, it will insert another record into the database.

Example output when all servers are configured for round-robin connectivity:
```

Connected successfully

INSERT INTO testtbl (web) VALUES ('srv-web3')

Records just inserted in database: 1

Total records in the table: 6

SELECT id, web, db, datecreated FROM testtbl ORDER BY id DESC;
id    web server    db server    date created
6    srv-web3    srv-db3    2019-08-09 16:23:40
5    srv-web2    srv-db2    2019-08-09 16:23:39
4    srv-web1    srv-db1    2019-08-09 16:23:38
3    srv-web3    srv-db3    2019-08-09 16:02:31
2    srv-web2    srv-db2    2019-08-09 16:02:30
1    srv-web1    srv-db1    2019-08-09 16:02:29

```

Example output when web servers are configured for source and databases have round-robin connectivity:
```

Connected successfully

INSERT INTO testtbl (web) VALUES ('srv-web3')

Records just inserted in database: 1

Total records in the table: 6

SELECT id, web, db, datecreated FROM testtbl ORDER BY id DESC;
id    web server    db server    date created
6    srv-web1    srv-db3    2019-08-09 16:23:40
5    srv-web1    srv-db2    2019-08-09 16:23:39
4    srv-web1    srv-db1    2019-08-09 16:23:38
3    srv-web1    srv-db3    2019-08-09 16:02:31
2    srv-web1    srv-db2    2019-08-09 16:02:30
1    srv-web1    srv-db1    2019-08-09 16:02:29

```

[SIZE=4]Step #4 - Remove test[/SIZE]

Run this command on each web server to remove the PHP file:
```
sudo rm /var/www/mysite.mydomain.com/testsql.php
```

Run these commands from one of the database nodes in the cluster:
```

#mysql -u root -p
DROP USER testdbuser;
DROP DATABASE testdb;
exit

```

---

