---
title: "How to Load Balance Galera/MariaDB Servers on Ubuntu Server 18.04 LTS"
date: 2019-09-06
forum: Tutorials
---

### Post by LHammonds on 2019-09-06
Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

Link to original post: [HammondsLegacy Forums]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=264") (best when viewed at original location due to custom formatting)

[SIZE=4]High-level overview[/SIZE]

HAProxy is a free, very fast and reliable solution offering high availability, load balancing, and proxying for TCP and HTTP-based applications. It is particularly suited for very high traffic web sites and powers quite a number of the world's most visited ones

This tutorial will cover how to setup a redundant HAProxy system which will direct traffic to redundant database servers.  This will provide high availability when a database or load balancing server goes offline...for things such as maintenance tasks.

This is an overview image of a highly-available web server platform.
This article covers the database load balancers.
[IMG]https://hammondslegacy.com/images/linux/design-ha-lamp-service.jpg[/IMG]

[SIZE=4]Tools utilized in this process[/SIZE]


[LIST]
[*][Ubuntu Server]("https://www.ubuntu.com/download/alternative-downloads#alternate-ubuntu-server-installer") 18.04.2 LTS, 64-bit 
[*]HAProxy 1.8.8 
[*]Keepalived 1.3.9 
[*]xinetd 2.3.15.3 
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
[*][How to setup HAProxy as Load Balancer for MariaDB on CentOS 7]("https://www.howtoforge.com/tutorial/how-to-setup-haproxy-as-load-balancer-for-mariadb-on-centos-7/") 
[/LIST]


[SIZE=4]Assumptions[/SIZE]
 
This documentation will need to make use of some very-specific information that will most-likely be different for each person / location. And as such, this information will be noted in this section. They will be highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using these "place-holder" values.

Under no circumstance should you use the actual values listed below. They are place-holders for the real thing. This is just a checklist template you need to have answered before you start the install process.

Wherever you see [COLOR=red]RED[/COLOR] in this document, you need to substitute it for you will use in your environment.


[LIST]
[*][COLOR=red]192.168.107.166[/COLOR] (VirtualIP) 
[*]Load Balancer #1 server name: [COLOR=red]srv-lbdb1[/COLOR] (master) 
[*]Load Balancer #1 Internal IP address: [COLOR=red]192.168.107.164[/COLOR] 
[*]Load Balancer #2 server name: [COLOR=red]srv-lbdb2[/COLOR] (slave) 
[*]Load Balancer #2 Internal IP address: [COLOR=red]192.168.107.165[/COLOR] 
[*]Ubuntu Admin ID: [COLOR=red]administrator[/COLOR] 
[*]Ubuntu Admin Password: [COLOR=red]myadminpass[/COLOR] 
[*]Email Server Name (remote): [COLOR=red]srv-mail[/COLOR] 
[*]Email Server Internal IP (remote): [COLOR=red]192.168.107.25[/COLOR] 
[*]DB Server #1 Internal IP Address: [COLOR=red]192.168.107.123[/COLOR] 
[*]DB Server #2 Internal IP Address: [COLOR=red]192.168.107.124[/COLOR] 
[*]DB Server #3 Internal IP Address: [COLOR=red]192.168.107.125[/COLOR] 
[/LIST]


Load Balancer Servers - Setup two Ubuntu servers for use as the HAProxy servers.  This tutorial assumes the server was configured according to this tutorial: [How to install and configure Ubuntu Server]("https://ubuntuforums.org/showthread.php?t=2389846")

Database Servers - Setup three Ubuntu servers for use as the database servers.  This tutorial assumes the servers were configured according to this tutorial: [How to Install MariaDB Galera Cluster on Ubuntu 18.04 LTS]("https://ubuntuforums.org/showthread.php?t=2426282")

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
echo "Adding Database Server rules"
ufw allow proto tcp to any port 3306 comment 'MariaDB' 1>/dev/null 2>&1
echo "Adding VRRP rules"
ufw allow to 224.0.0.18 comment 'VRRP Broadcast' 1>/dev/null 2>&1
ufw allow from 192.168.107.165 comment 'VRRP Router' 1>/dev/null 2>&1

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
echo "Adding Database Server rules"
ufw allow proto tcp to any port 3306 comment 'MariaDB' 1>/dev/null 2>&1
echo "Adding VRRP rules"
ufw allow to 224.0.0.18 comment 'VRRP Broadcast' 1>/dev/null 2>&1
ufw allow from 192.168.107.164 comment 'VRRP Router' 1>/dev/null 2>&1

```

Run the updated rules:

```
/var/scripts/prod/en-firewall.sh
```

[SIZE=4]Master Keepalive Config[/SIZE]

On the master server (srv-lbdb1), create the keepalive configuration file:

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
    192.168.107.166
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

On the slave server (srv-lbdb2), create the keepalive configuration file:

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
    192.168.107.166
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
    inet 192.168.107.164/24 brd 192.168.107.255 scope global ens32
       valid_lft forever preferred_lft forever
    inet 192.168.107.166/32 scope global ens32
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
    inet 192.168.107.165/24 brd 192.168.107.255 scope global ens32
       valid_lft forever preferred_lft forever
    inet6 fe80::250:56ff:febf:6a52/64 scope link
       valid_lft forever preferred_lft forever

```

When the slave NIC is active with the virtual IP, you will see the virtual IP on it just like the master.

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Install xinetd[/SIZE]

Run this command on all database nodes in the cluster:
```
sudo apt install xinetd
```

[SIZE=4]Firewall Rules[/SIZE]

On each database node in the cluster, edit the firewall script that was created during the initial setup of the server (if you [followed my instructions]("https://ubuntuforums.org/showthread.php?t=2389846&page=2&p=13758735#post13758735")):
```
vi /var/scripts/prod/en-firewall.sh
```

Add the following:

```
echo "Adding xinetd rules"
ufw allow from 192.168.107.0/24 proto tcp to any port 9200 comment 'clustercheck' 1>/dev/null 2>&1

```

Run the updated rules:

```
/var/scripts/prod/en-firewall.sh
```

[SIZE=4]Install Cluster Check Script[/SIZE]

Run these commands on all database nodes in the cluster:
```
cd /tmp
wget https://raw.githubusercontent.com/olafz/percona-clustercheck/master/clustercheck -O /tmp/clustercheck.sh
sudo chown root:root /tmp/clustercheck.sh
sudo chmod 755 /tmp/clustercheck.sh
sudo mv /tmp/clustercheck.sh /var/scripts/prod/clustercheck.sh
```

[SIZE=4]Modify Cluster Check Script[/SIZE]

We need to make some slight changes in the code so it will work correctly with the built-in credentials and reference the correct my.cnf file.

On each database node, edit the script:
```
sudo vi /var/scripts/prod/clustercheck.sh
```

Change the following lines (lines 40, 41, 42):
```

MYSQL_USERNAME="${MYSQL_USERNAME:=-clustercheckuser}"
MYSQL_PASSWORD="${MYSQL_PASSWORD-clustercheckpassword!}"
DEFAULTS_EXTRA_FILE=${DEFAULTS_EXTRA_FILE:-/etc/my.cnf}

```
to these:
```

MYSQL_USERNAME="${MYSQL_USERNAME:=clustercheckuser}"
MYSQL_PASSWORD="${MYSQL_PASSWORD:=clustercheckpassword!}"
DEFAULTS_EXTRA_FILE=${DEFAULTS_EXTRA_FILE:-/etc/mysql/my.cnf}

```

If you want the output to include the name of the node, you can change these lines (lines 29,86,98,109):
```

    echo -en "Percona XtraDB Cluster Node is manually disabled.\r\n"
            echo -en "Percona XtraDB Cluster Node is read-only.\r\n"
    echo -en "Percona XtraDB Cluster Node is synced.\r\n"
    echo -en "Percona XtraDB Cluster Node is not synced.\r\n"

```
to these:
```

    echo -en "MariaDB Cluster Node ${HOSTNAME} is manually disabled.\r\n"
            echo -en "MariaDB Cluster Node ${HOSTNAME} is read-only.\r\n"
    echo -en "MariaDB Cluster Node ${HOSTNAME} is synced.\r\n"
    echo -en "MariaDB Cluster Node ${HOSTNAME} is not synced.\r\n"

```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Configure xinetd[/SIZE]

Run these SQL commands on just one database node in the cluster:
```

mysql -u root -p
GRANT PROCESS ON *.* TO 'clustercheckuser'@'localhost' IDENTIFIED BY 'clustercheckpassword!';
FLUSH PRIVILEGES;
exit

```

Run these commands on all database nodes in the cluster:
```

sudo touch /etc/xinetd.d/mariadbchk
sudo chown root:root /etc/xinetd.d/mariadbchk
sudo chmod 644 /etc/xinetd.d/mariadbchk
sudo vi /etc/xinetd.d/mariadbchk

```

Add the following to the file:
```

# default: on
# description: mariadbchk
service mariadbchk
{
  disable = no
  flags = REUSE
  socket_type = stream
  port = 9200
  wait = no
  user = nobody
  server = /var/scripts/prod/clustercheck.sh
  log_on_failure += USERID
  only_from = 0.0.0.0/0
  per_source = UNLIMITED
}

```

Run the following commands on each database node in the cluster:

```

sudo touch /lib/systemd/system/mariadbchk.socket
sudo touch /lib/systemd/system/mariadbchk@.service
sudo chown root:root /lib/systemd/system/mariadbchk*
sudo chmod 644 /lib/systemd/system/mariadbchk*

```

Edit the socket file on each database node in the cluster:
```
vi /lib/systemd/system/mariadbchk.socket
```

Add the following to the file:
```

[Unit]
Description=MariaDB Galera Cluster node check socket

[Socket]
ListenStream=9200
Accept=yes

[Install]
WantedBy=sockets.target
```

Edit the service file on each database node in the cluster:
```
vi /lib/systemd/system/mariadbchk@.service
```

Add the following to the file:
```

[Unit]
Description=MariaDB Galera Cluster node check service

[Service]
ExecStart=-/var/scripts/prod/clustercheck.sh
StandardInput=socket

```

Run these commands on each of the database nodes in the cluster:
```

sudo systemctl enable mariadbchk.socket
sudo systemctl start mariadbchk.socket

```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Test xinetd[/SIZE]

On each of the database nodes in the cluster, run the script manually:
```
sudo /var/scripts/prod/clustercheck.sh
```
```
CONTENT BLOCKED
PLEASE SEE ORIGINAL SITE IN FIRST POST FOR CONTENT
```

Access the port locally via telnet and see if it responds as expected:
```
telnet 127.0.0.1 9200
```
```
CONTENT BLOCKED
PLEASE SEE ORIGINAL SITE IN FIRST POST FOR CONTENT
```

Now stop the database node on one of the servers and test the port again:
```
sudo systemctl stop mariadb
```
```
telnet 127.0.0.1 9200
```
```
CONTENT BLOCKED
PLEASE SEE ORIGINAL SITE IN FIRST POST FOR CONTENT
```

Do not forget to start the database node:
```
sudo systemctl start mariadb
```

On each of the load balance servers (srv-lbdb1 and srv-lbdb2), make sure you can telnet to each database node and get the status (this tests your database firewall rules):
```

telnet srv-db1 9200
telnet srv-db2 9200
telnet srv-db3 9200

```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Install HAProxy[/SIZE]

Run this command on both load balance servers:
```
sudo apt install haproxy
```

[SIZE=4]Name Resolution[/SIZE]

You can modify your host file for name resolution and just use the names of servers in your configuration files rather than the IP addresses.  If a server IP changes in the future, you only need to modify the host which is much easier than tracking down various application configuration files.  You could do this with an internal DNS server but I prefer using the local host file for fastest resolution.

Edit the host file:
```
sudo vi /etc/hosts
```

Add the database servers (substituting for your own values):
```

192.168.107.123 srv-db1
192.168.107.124 srv-db2
192.168.107.125 srv-db3

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

[SIZE=4]HAProxy Database Users[/SIZE]

Create the status check user for the load balance virtual IP on just one of the database nodes in the cluster (the change will replicate to the others).  We need to set the host IP for every load balancing server IP we have (including the virtual IP):
```

mysql
CREATE USER 'haproxy_check'@'192.168.107.164';
CREATE USER 'haproxy_check'@'192.168.107.165';
CREATE USER 'haproxy_check'@'192.168.107.166';
FLUSH PRIVILEGES;
exit

```

[SIZE=4]HAProxy Configuration[/SIZE]

This is the default ownership and file permission settings of the configuration file:
```
chown root:root /etc/haproxy/haproxy.cfg
chmod 644 /etc/haproxy/haproxy.cfg
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

## Galera Cluster Frontend configuration
frontend galera_cluster_frontend
  ## Galera Cluster uses TCP connections.
  mode tcp
  ## Setup listener on port 3306 on the virtual IP.
  bind 192.168.107.166:3306
  ## Override the default log method to match tcp mode.
  option tcplog
  default_backend galera_cluster_backend

## Galera Cluster Backend configuration
backend galera_cluster_backend
  ## Galera Cluster uses TCP connections.
  mode tcp
  ## Enable keepalive function to maintain TCP connections.
  option tcpka
  ## Various policies for determining how to route traffic to the servers.
#  balance first
#  balance leastconn
#  balance roundrobin
  balance source
#  balance static-rr
  ## Defined backend database server check.
  option httpchk
  ## Node definitions for routing to database servers.
  server srv-db-cluster1 srv-db1:3306 check port 9200 rise 2 fall 3 inter 2000 fastinter 1000 downinter 5000
  server srv-db-cluster2 srv-db2:3306 check port 9200 rise 2 fall 3 inter 2000 fastinter 1000 downinter 5000
  server srv-db-cluster3 srv-db3:3306 check port 9200 rise 2 fall 3 inter 2000 fastinter 1000 downinter 5000

## HAProxy stats web gui - This entire section is optional.
listen stats
  ## Setup listener on port 9000 on any interface.
  bind *:9000
  ## http mode so a web browser can be used to access it.
  mode http
  ## Enable metrics to be recorded.
  stats enable
  ## Configure the URI.  Example: http://192.168.107.164:9000/stats
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
tcp        0      0 0.0.0.0:9000            0.0.0.0:*               LISTEN      19475/haproxy
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      19475/haproxy
```

Open a web browser and have a look at the statistics page at [http://192.168.107.166:9000/stats/](http://192.168.107.166:9000/stats/)

[IMG]https://hammondslegacy.com/images/linux/haproxy-db-cluster.jpg[/IMG]

---

