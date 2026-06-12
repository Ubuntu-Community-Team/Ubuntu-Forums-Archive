---
title: "How to Install MariaDB Galera Cluster on Ubuntu 18.04 LTS"
date: 2019-09-06
forum: Tutorials
---

### Post by LHammonds on 2019-09-06
Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

Link to original post: [HammondsLegacy Forums]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=262") (best when viewed at original location due to custom formatting)

[SIZE=4]High-level overview[/SIZE]

MariaDB Galera is a multi-master cluster for MariaDB.  In MariaDB Galera Cluster, multiple database servers are interconnected with each other and keep synchronized to provide high availability redundancy.

This tutorial will cover how to setup a redundant database system.  This will provide high availability when a database server goes offline...such as for maintenance tasks.

MariaDB Galera needs a minimum of 3 nodes.  You can easily add more but make sure the total number of nodes in the cluster is an odd number (e.g. 3, 5, 7, 9, 11, etc.).

This is an overview image of a highly-available web server platform.
This article covers the setup of the database cluster.
[IMG]http://hammondslegacy.com/images/linux/design-ha-lamp-service.jpg[/IMG]
[SIZE=4]Tools utilized in this process[/SIZE]


[LIST]
[*][Ubuntu Server]("https://www.ubuntu.com/download/alternative-downloads#alternate-ubuntu-server-installer") 18.04.2 LTS, 64-bit 
[*][MariaDB]("http://www.mariadb.org/") 10.4.6 
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.71 
[*][VMware vSphere]("http://www.vmware.com/products/vsphere/overview.html") 6.0.0 
[*][VirtualBox]("http://www.virtualbox.org/") 6.0.10 
[/LIST]
 
[SIZE=4]Helpful links[/SIZE]

The list below are sources of information that was helpful in the creation of this document.


[LIST]
[*][MariaDB Package Repository Setup and Usage]("https://mariadb.com/kb/en/library/mariadb-package-repository-setup-and-usage/") 
[*][MariaDB Galera Documentation]("https://galeracluster.com/library/documentation/") 
[/LIST]
 
[SIZE=4]Assumptions[/SIZE]
 
This documentation will need to make use of some very-specific information that will most-likely be different for each person / location. And as such, this information will be noted in red in this section.

Under no circumstance should you use the actual values listed below. They are place-holders for the real thing. This is just a checklist template you need to have answered before you start the install process.

Wherever you see the values below in this document, you need to substitute it for you will use in your environment.


[LIST]
[*]Ubuntu Admin ID: [COLOR=red]administrator[/COLOR] 
[*]Ubuntu Admin Password: [COLOR=red]myadminpass[/COLOR] 
[*]Email Server Name (remote): [COLOR=red]srv-mail[/COLOR] 
[*]Email Server Internal IP (remote): [COLOR=red]192.168.107.25[/COLOR] 
[*]Database Server #1: Internal IP Address: [COLOR=red]192.168.107.101[/COLOR] 
[*]Database Server #2: Internal IP Address: [COLOR=red]192.168.107.102[/COLOR] 
[*]Database Server #3: Internal IP Address: [COLOR=red]192.168.107.103[/COLOR] 
[/LIST]
 
Database Servers - Setup three Ubuntu servers for use as the database servers.  This tutorial assumes the server was configured according to this tutorial: [How to install and configure Ubuntu Server]("https://ubuntuforums.org/showthread.php?t=2389846")

It is also assumed the reader knows how to use the VI editor. If not, you will need to [beef up your skill set]("http://www.washington.edu/computing/unix/vi.html") or use a different editor in place of it.

---

### Post by LHammonds on 2019-09-06
[size=4]Add MariaDB repositories[/size]

Source of information: [MariaDB](https://downloads.mariadb.org/mariadb/repositories/) (NOTE: Your flavor of Linux and download location may vary and that page will help)

Perform these steps on each database server.


[list=1]
[*]Connect to the server using PuTTY and login with your administrator credentials.
[*]Type the following to add the MariaDB repositories:
```

sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xF1656F24C74CD1D8
sudo add-apt-repository 'deb [arch=amd64,arm64,ppc64el] http://mirror.rackspace.com/mariadb/repo/10.4/ubuntu '$(lsb_release -cs)' main'
sudo apt update

```
[/list]


[size=4]Install MariaDB[/size]

Perform these steps on each database server.


[list=1]
[*]Install the database server and required dependencies by typing the following:
```
sudo apt -y install mariadb-server
```
[*]When installation is completed, the database service should automatically start.  It is also configured to automatically start upon reboot.
[/list]


[size=4]Verify database service is running[/size]

Verify the service is running by typing any of the following commands:
```
systemctl status mariadb
```
or
```
netstat -tap | grep mysql
```
or
```
sudo mysqladmin status
```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Tighten Security[/SIZE]

MariaDB comes with a script to tighten-down security for a production server.

Perform these steps on each database server.


[LIST=1]
[*]Connect to the server using PuTTY. 
[*]Start the secure install script:
```
sudo mysql_secure_installation
``` 
[*]Enter current password for root: Just press ENTER here since default install does not set a password. 
[*]Switch to unix_socket authentication? Select N 
[*]Change the root password? Select Y and set your password. 
[*]Remove the anonymous users?  Select Y 
[*]Disallow root login remotely?  Select Y 
[*]Remove test database and access to it?  Select Y 
[*]Reload privilege tables now?  Select Y
[/LIST]
 
On production servers, It is a good idea to disable SQL command history which can expose database user accounts, passwords and encryption keys.  The following commands will remove the history file if it exists and then link it to a non-existing (null) file...thus never recording anything in the future.

```

sudo rm /root/.mysql_history
sudo ln -s /dev/null /root/.mysql_history

```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Firewall Rules[/SIZE]

For each database server, edit the firewall script that was created during the initial setup of the server (if you [followed my instructions]("https://ubuntuforums.org/showthread.php?t=2389846&page=2&p=13758735#post13758735")):
```
vi /var/scripts/prod/en-firewall.sh
```

Add the following (adjusting for your specific environment):

```
echo "Adding Database Server rules"
ufw allow proto tcp to any port 3306 comment 'MariaDB' 1>/dev/null 2>&1
ufw allow from 192.168.107.0/24 proto tcp to any port 4444 comment 'DB SST' 1>/dev/null 2>&1
ufw allow from 192.168.107.0/24 proto tcp to any port 4567 comment 'DB Cluster' 1>/dev/null 2>&1
ufw allow from 192.168.107.0/24 proto udp to any port 4567 comment 'DB Cluster' 1>/dev/null 2>&1
ufw allow from 192.168.107.0/24 proto tcp to any port 4568 comment 'DB IST' 1>/dev/null 2>&1

```

NOTE: The above allows only servers on the 192.168.107.xxx network to communicate on the cluster ports.  You can remove this limit or limit it even further to specific IPs.  It just depends on how you want to manage the scope of accessibility.  The 3306 port is left wide open so anything can connect to it that can access the internal IP.  You could limit this as well but be sure to include all application servers and clients that will need it.

Run the updated rules:

```
/var/scripts/prod/en-firewall.sh
```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Galera Configuration[/SIZE]

On each database server, type these commands:

```

sudo touch /etc/mysql/conf.d/galera.cnf
sudo chown root:root /etc/mysql/conf.d/galera.cnf
sudo chmod 644 /etc/mysql/conf.d/galera.cnf

```

On srv-db1, edit the config file:
```
sudo vi /etc/mysql/conf.d/galera.cnf
```

Add the following for srv-db1:

NOTE: It is best practice to add all nodes in the cluster to the **wsrep_cluster_address** line but only one server address is mandatory.  This allows any node in the cluster to respond to any other node wanting to join the cluster.  You can even include the nodes own address and Galera is smart enough to ignore it.

```

[mysqld]
# binlog_format=STATEMENT (statements are stored)
# binlog_format=ROW (rows changed by a statement are stored)
# binlog_format=MIXED (statements stored unless not safe for replication, then rows stored)
binlog_format=ROW
default-storage-engine=innodb
innodb_autoinc_lock_mode=2
bind-address=0.0.0.0
# Galera Provider Configuration
wsrep_on=ON
# wsrep_sync_wait
#    0=Disabled
#    1=READ
#    2=UPDATE and DELETE
#    3=READ, UPDATE and DELETE
#    4=INSERT and REPLACE
#    5=READ, INSERT and REPLACE
#    6=UPDATE, DELETE, INSERT and REPLACE
#    7=READ, UPDATE, DELETE, INSERT and REPLACE
#    8=SHOW (9-15 = 1-7 + SHOW)
wsrep_sync_wait=0
wsrep_provider=/usr/lib/galera/libgalera_smm.so
# Galera Cluster Configuration
wsrep_cluster_name="galera_cluster"
wsrep_cluster_address="gcomm://192.168.107.101,192.168.107.102,192.168.107.103"

# Galera Synchronization Configuration
wsrep_sst_method=rsync

# Galera Node Configuration
wsrep_node_address="192.168.107.101"
wsrep_node_name="srv-db1"
# wsrep_node_incoming_address - provides the IP:port from which the node
#    should expect client connections. Mainly used with load balancers.
#wsrep_node_incoming_address="192.168.107.164:3306"
wsrep_node_incoming_address="AUTO"

```

On srv-db2, edit the config file:
```
sudo vi /etc/mysql/conf.d/galera.cnf
```

Copy/paste the configuration from srv-db1 and modify these lines:
```

wsrep_node_address="192.168.107.102"
wsrep_node_name="srv-db2"

```

On srv-db3, edit the config file:
```
sudo vi /etc/mysql/conf.d/galera.cnf
```

Copy/paste the configuration from srv-db1 and modify these lines:
```

wsrep_node_address="192.168.107.103"
wsrep_node_name="srv-db3"

```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Start the Galera Cluster[/SIZE]

On each database server, stop the database using this command:

```
sudo systemctl stop mariadb
```

On srv-db1 (Node1), start the cluster with this command:

```
sudo galera_new_cluster
```

Check to see if the cluster started and has one node active:

```
mariadb -u root -p -e "show status like 'wsrep_cluster_size'"
```

Output:
```

+--------------------+-------+
| Variable_name      | Value |
+--------------------+-------+
| wsrep_cluster_size | 1     |
+--------------------+-------+

```

On srv-db2, start the database service:

```
sudo systemctl start mariadb
```

Make sure the service started and is active:

```
systemctl status mariadb
```

Check to see if the cluster has two nodes active:

```
mariadb -u root -p -e "show status like 'wsrep_cluster_size'"
```

Output:
```

+--------------------+-------+
| Variable_name      | Value |
+--------------------+-------+
| wsrep_cluster_size | 2     |
+--------------------+-------+

```

On srv-db3, start the database service:

```
sudo systemctl start mariadb
```

Make sure the service started and is active:

```
systemctl status mariadb
```

Check to see if the cluster has two nodes active:

```
mariadb -u root -p -e "show status like 'wsrep_cluster_size'"
```

Output:
```

+--------------------+-------+
| Variable_name      | Value |
+--------------------+-------+
| wsrep_cluster_size | 3     |
+--------------------+-------+

```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Test Replication[/SIZE]

On srv-db1, create a new database:

```

mariadb -u root -p -e "CREATE DATABASE testrep;CREATE TABLE testrep.test ( id INT NOT NULL AUTO_INCREMENT, name VARCHAR(50), PRIMARY KEY(id));INSERT INTO testrep.test (name) VALUES ('srv-db1');SHOW DATABASES;"

```

```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| testrep            |
+--------------------+
4 rows in set (0.001 sec)
```

On srv-db2 (and srv-db3), check and make sure you see the testrep database:

```

mariadb -u root -p -e "SHOW DATABASES;"

```

On srv-db2, insert another record into the table:

```

mariadb -u root -p -e "INSERT INTO testrep.test (name) VALUES ('srv-db2');"

```

On srv-db3, insert another record into the table:

```

mariadb -u root -p -e "INSERT INTO testrep.test (name) VALUES ('srv-db3');"

```

On srv-db1, look at all the records in the table:

```

mariadb -u root -p -e "SELECT * FROM testrep.test;"

```

```

+----+---------+
| id | name    |
+----+---------+
|  2 | srv-db1 |
|  3 | srv-db2 |
|  4 | srv-db3 |
+----+---------+
3 rows in set (0.000 sec)

```

On srv-db1 (or any of the db servers), remove the database (which should also remove it from all other nodes):

```

mariadb -u root -p -e "DROP DATABASE testrep;SHOW DATABASES;"

```

```

+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
3 rows in set (0.001 sec)

```

---

### Post by LHammonds on 2019-09-06
Reference: [Introducing the "Safe-To-Bootstrap" feature in Galera Cluster]("https://galeracluster.com/2016/11/introducing-the-safe-to-bootstrap-feature-in-galera-cluster/")

[SIZE=4]Shutdown Cluster[/SIZE]

The procedure to shutdown an entire cluster is as follows:


[LIST=1]
[*]Work from the last node to the 1st node such as srv-db3, then srv-db2 and finally srv-db1. 
[*]Make sure the node you are working on is in sync by running these commands:
```

mariadb -u root -p -e "show status like 'wsrep_local_state_comment';"

```
```
+---------------------------+--------+
| Variable_name             | Value  |
+---------------------------+--------+
| wsrep_local_state_comment | Synced |
+---------------------------+--------+
``` 
[*]If the node is synced, then stop the database service:
```
sudo systemctl stop mariadb
``` 
[*]Once all nodes are down, the cluster is effectively destroyed and a new one can be started when bringing them back online. 
[/LIST]


[SIZE=4]Startup Cluster[/SIZE]

To start a cluster after performing a clean shutdown, follow the steps in the prior section called [Start the Galera Cluster]("https://ubuntuforums.org/showthread.php?t=2426282&p=13886177#post13886177")

[SIZE=4]Reboots[/SIZE]

The cluster state will survive if at least 1 node remains online while other nodes are rebooted and as such, no intervention will be necessary.

[SIZE=4]Crash Recovery[/SIZE]

If all servers are offline at the same time (such as during a power outage), then the cluster will need to be re-created following a crash procedure.


[LIST=1]
[*]Check each node and see if they all have a zero in the "safe_to_bootstrap" value.  If any have a 1 as the value, that is the server you start first.
```
cat /var/lib/mysql/grastate.dat
```
```

# GALERA saved state
version: 2.1
uuid:    d89c79f4-b308-11e9-9931-8f96b3cc57b2
seqno:   -1
safe_to_bootstrap: 0

``` 
[*]If they all have an invalid seqno of -1 and none have a value of 1 in "safe_to_bootstrap" then you need to temporary start the database service on each server with a recovery option so you can see the number associated to the "Recovered Position"
```
sudo -u mysql mysqld --wsrep-recover
```
srv-db1 shows position is 31:
```
2019-08-05 18:53:55 0 [Note] WSREP: Recovered position: d89c79f4-b308-11e9-9931-8f96b3cc57b2:31
```
srv-db2 shows position is 29:
```
2019-08-05 18:49:16 0 [Note] WSREP: Recovered position: d89c79f4-b308-11e9-9931-8f96b3cc57b2:29
```
srv-db3 shows position is 30:
```
2019-08-05 18:49:23 0 [Note] WSREP: Recovered position: d89c79f4-b308-11e9-9931-8f96b3cc57b2:30
``` 
[*]In this example, srv-db1 has the highest transaction number of 31 and should be the 1st node to be started in the cluster.  Modify the grastate.dat and change "safe_to_bootstrap" to 1.
```
sed -i 's/safe_to_bootstrap: 0/safe_to_bootstrap: 1/' /var/lib/mysql/grastate.dat
``` 
[*]Now you can follow normal procedure to start a new Galera cluster using this server as the starting node by following the steps in the prior section called [Start the Galera Cluster]("https://ubuntuforums.org/showthread.php?t=2426282&p=13886177#post13886177") 
[/LIST]

If there are other issues preventing the cluster from starting, you should continue to research the various solutions on the Internet.  There are too many potential scenarios for me to try and document them all here.

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Nagios Monitoring[/SIZE]

If you run a Nagios server to monitor your servers, you can use this script to monitor the health of your cluster.

Create the script and set permissions on each database node in the cluster:
```

sudo touch /usr/lib/nagios/plugins/check_galera_cluster.sh
sudo chown root:root /usr/lib/nagios/plugins/check_galera_cluster.sh
sudo chmod 755 /usr/lib/nagios/plugins/check_galera_cluster.sh

```

Edit the script:
```
sudo vi /usr/lib/nagios/plugins/check_galera_cluster.sh
```

Copy this into the script:
```

#!/bin/bash
# Name: check_galera_cluster
# Source: https://exchange.nagios.org/directory/Plugins/Databases/MySQL/check_galera_cluster/details
# Modified by: LHammonds (2019-09-06) (Version 1.1.4a)
PROGNAME=`basename $0`
VERSION="Version 1.1.4a"
AUTHOR="Guillaume Coré <fridim@onfi.re>, Ales Nosek <ales.nosek@gmail.com>, Staf Wagemakers <staf@wagemakers.be>"

ST_OK=0
ST_WR=1
ST_CR=2
ST_UK=3

warnAlerts=0
critAlerts=0
unknAlerts=0

print_version() {
   echo "$VERSION $AUTHOR"
}

print_help() {
  print_version $PROGNAME $VERSION
  echo ""
  echo "$PROGNAME is a Nagios plugin to monitor Galera cluster status."
  echo ""
  echo "$PROGNAME [-u USER] [-p PASSWORD] [-H HOST] [-P PORT] [-m file] [-w SIZE] [-c SIZE] [-s statefile] [-f FLOAT] [-0]"
  echo ""
  echo "Options:"
  echo "  u)"
  echo "    MySQL user."
  echo "  p)"
  echo "    MySQL password."
  echo "  H)"
  echo "    MySQL host."
  echo "  P)"
  echo "    MySQL port."
  echo "  m)"
  echo "    MySQL extra my.cnf configuration file."
  echo "  w)"
  echo "    Sets minimum number of nodes in the cluster when WARNING is raised. (default is same as critical)."
  echo "  c)"
  echo "    Sets minimum number of nodes in the cluster when CRITICAL is raised. (default is 2)."
  echo "  f)"
  echo "    Sets critical value of wsrep_flow_control_paused (default is 0.1)."
  echo "  0)"
  echo "    Rise CRITICAL if the node is not primary"
  echo "  s)"
  echo "    Create state file, detect disconnected nodes"
  exit $ST_UK
}

# default values
crit=2
fcp=0.1

check_executable() {
  if [ -z "$1" ]; then
    echo "check_executable: no parameter given!"
    exit $ST_UK
  fi

  if ! command -v "$1" &>/dev/null; then
    echo "UNKNOWN: Cannot find $1"
    exit $ST_UK
  fi
}

check_executable mysql
check_executable bc

while getopts “hvu:p:H:P:w:c:f:m:s:0” OPTION; do
  case $OPTION in
    h)
      print_help
      exit $ST_UK
      ;;
    v)
      print_version $PROGNAME $VERSION
      exit $ST_UK
      ;;
    u)
      mysqluser=$OPTARG
      ;;
    p)
      password=$OPTARG
      ;;
    H)
      mysqlhost=$OPTARG
      ;;
    P)
      port=$OPTARG
      ;;
    m)
      myconfig=$OPTARG
      ;;
    w)
      warn=$OPTARG
      ;;
    c)
      crit=$OPTARG
      ;;
    f)
      fcp=$OPTARG
      ;;
    0)
      primary='TRUE'
      ;;
    s)
      stateFile=$OPTARG
      ;;
    ?)
      echo "Unknown argument: $1"
      print_help
      exit $ST_UK
      ;;
  esac
done

if [ -z "$warn" ]; then
  warn=$crit
fi

create_param() {
  if [ -n "$2" ]; then
    echo $1$2
  fi
}

param_mysqlhost=$(create_param -h "$mysqlhost")
param_port=$(create_param -P "$port")
param_mysqluser=$(create_param -u "$mysqluser")
param_password=$(create_param -p "$password")
param_configfile=$(create_param --defaults-extra-file= "$myconfig")
param_mysql="$param_mysqlhost $param_port $param_mysqluser $param_password $param_configfile"

#
# verify the database connection
#

mysql $param_mysql -B -N  -e '\s;' >/dev/null 2>&1 || {
  echo "CRITICAL: mysql connection check failed"
  exit $ST_CR
}

#
# verify that the node is part of a cluster
#

rClusterStateUuid=$(mysql $param_mysql -B -N -e "show status like 'wsrep_cluster_state_uuid'; "|cut -f 2)

if [ -z "$rClusterStateUuid" ]; then
  echo "CRITICAL: Node is not part of a cluster"
  exit $ST_CR
fi

rClusterSize=$(mysql $param_mysql -B -N -e "show status like 'wsrep_cluster_size'"|cut -f 2)
rClusterStatus=$(mysql $param_mysql -B -N -e "show status like 'wsrep_cluster_status'"|cut -f 2) # Primary
rFlowControl=$(mysql $param_mysql -B -N -e "show status like 'wsrep_flow_control_paused'"|cut -f 2) # < 0.1
rReady=$(mysql $param_mysql -B -N -e "show status like 'wsrep_ready'"|cut -f 2)  # ON
rConnected=$(mysql $param_mysql -B -N -e "show status like 'wsrep_connected'"|cut -f 2)  # ON
rLocalStateComment=$(mysql $param_mysql -B -N -e "show status like 'wsrep_local_state_comment'"|cut -f 2)  # Synced
rIncommingAddresses=$(mysql $param_mysql -B -N -e "show global status like 'wsrep_incoming_addresses';"|cut -f 2)
         
if [ -z "$rFlowControl" ]; then
  echo "UNKNOWN: wsrep_flow_control_paused is empty"
  unknAlerts=$(($unknAlerts+1))
fi

if [ $(echo "$rFlowControl > $fcp" | bc) = 1 ]; then
  echo "CRITICAL: wsrep_flow_control_paused is > $fcp"
  critAlerts=$(($criticalAlerts+1))
fi

if [ "$primary" = 'TRUE' ]; then
  if [ "$rClusterStatus" != 'Primary' ]; then
    echo "CRITICAL: Node is not primary (wsrep_cluster_status)"
    critAlerts=$(($criticalAlerts+1))
  fi
fi

if [ "$rReady" != 'ON' ]; then
  echo "CRITICAL: Node is not ready (wsrep_ready)"
  critAlerts=$(($criticalAlerts+1))
fi

if [ "$rConnected" != 'ON' ]; then
  echo "CRITICAL: Node is not connected (wsrep_connected)"
  critAlerts=$(($criticalAlerts+1))
fi

if [ "$rLocalStateComment" != 'Synced' ]; then
  echo "CRITICAL: Node is not synced - actual state is: $rLocalStateComment (wsrep_local_state_comment)"
  critAlerts=$(($criticalAlerts+1))
fi

if [ $rClusterSize -gt $warn ]; then
  # only display the ok message if the state check not enabled
  if [ -z "$stateFile" ]; then
    echo "OK: Number of NODES = $rClusterSize (wsrep_cluster_size)"
  fi
elif [ $rClusterSize  -le $crit ]; then
  echo "CRITICAL: Number of NODES = $rClusterSize (wsrep_cluster_size)"
  critAlerts=$(($criticalAlerts+1))
elif [ $rClusterSize -le $warn ]; then
  echo "WARNING: Number of NODES = $rClusterSize (wsrep_cluster_size)"
  warnAlerts=$(($warnAlerts+1))
else
  exit $ST_UK
fi

#
# detect is the connection is lost automatically
#

if [ ! -z "$stateFile" ]; then
  touch $stateFile
  if [ $? != "0" ]; then
    echo "UNKNOWN: stateFile \"$stateFile\" is not writeable"
    unknAlerts=$(($unknAlerts+1))
  else
    if [ "$rConnected" = "ON" ]; then
      # get the current connected Nodes
      currentNodes=$(echo $rIncommingAddresses | tr "," "\n" | sort -u)
      if [ -f "$stateFile" ]; then
        # get the nodes added to the cluster
        newNodes=$(echo $currentNodes | tr " " "\n" | comm -2 -3 - $stateFile)
        # get the nodes that were removed from the cluster
        missingNodes=$(echo $currentNodes | tr " " "\n" | comm -1 -3 - $stateFile)
        if [ ! -z "$newNodes" ]; then
          # add the new nodes to the cluster to the state file
          echo $newNodes | tr " " "\n" >> $stateFile
        fi
      else
        # there is no state file yet, creating new one.
        echo $currentNodes | tr " " "\n" > $stateFile
      fi # -f stateFile
      # get the numeber of nodes that were part of the cluster before
      maxClusterSize=$(cat $stateFile | wc -l)
      if [ $maxClusterSize -eq  $rClusterSize ]; then
        if [ $maxClusterSize -eq 1 ]; then
          if [ $crit -eq 0 -a  $warn -eq 0 ]; then
            echo "OK: Running single-node database cluster"
          fi
        else
          echo "OK: Running redundant $rClusterSize online / $maxClusterSize total"
        fi
      else
       echo "WARNING: Redundant  $rClusterSize online / $maxClusterSize  total, missing peers: $missingNodes" 
       warnAlerts=$(($warnAlerts+1))
      fi
    fi # rConnected
  fi # -w stateFile
fi # -z stateFile

#
# exit
#

[ "$critAlerts" -gt "0" ] && exit $ST_CR
[ "$unknAlerts" -gt "0" ] && exit $ST_UK
[ "$warnAlerts" -gt "0" ] && exit $ST_WR

exit 0

```

Modify Nagios on each database node in the cluster so it can use the custom script:

```
sudo vi /etc/nagios/nrpe_local.cfg
```

Add the following line:

```

command[check_galera_cluster]=/usr/lib/nagios/plugins/check_galera_cluster.sh

```

Reload the plugin for changes to take effect:
```
sudo systemctl reload nagios-nrpe-server
```

Run the script manually to ensure it works:
```
sudo /usr/lib/nagios/plugins/check_galera_cluster.sh
```

If the cluster is online and working properly, it should display something like the following:
```
OK: number of NODES = 3 (wsrep_cluster_size)
```

On your Nagios server, add the following service line to the database nodes you are monitoring which will specifically test the cluster status on each of them.  In this example, we are modifying the existing srv-db1 node which already monitors apt updates, cpu/ram/hd usage, etc.

```
sudo vi /etc/nagios/servers/srv-db1
```

Add this section and customize it to fit your environment:
```

define service{
        use                     critical-service
        host_name               srv-db1
        service_description     Galera Cluster
        check_command           check_nrpe!check_galera_cluster
        check_period            24x7
        check_interval          10
        notification_options    c
        notification_period     24x7
        contact_groups          database-admins
        }

```

On the Nagios server, reload the Nagios service for changes to take effect:

```
sudo systemctl reload nagios
```

---

### Post by LHammonds on 2019-09-06
[SIZE=4]Status Scripts[/SIZE]

If you want some custom scripts to check various settings, you can obtain the status in variables such as the following bash code snippets (run as the root user which has access to the database):

Here is a database command to obtain the friendly name of the current state:
```
mysql -u root -e "show status like 'wsrep_local_state_comment';"
```

Example output of the above command:
```
+---------------------------+--------+
| Variable_name             | Value  |
+---------------------------+--------+
| wsrep_local_state_comment | Synced |
+---------------------------+--------+
```

We can use that command to strip out the extraneous characters and just get to the crux of the data using grep and awk:
```
mysql -u root -e "show status like 'wsrep_local_state_comment';" | grep wsrep | awk {'print $2'}
```

Example output of the above command:
```
Synced
```

If we were to put this into a bash script, we can then take the output and put it into a variable like this:

```

#!/bin/bash
localstatecomment=`/usr/bin/mysql -u root -e "show status like 'wsrep_local_state_comment';" | /bin/grep wsrep | /bin/awk {'print $2'}`
echo "The current state for ${HOSTNAME} is ${localstatecomment}"

```

Example output from the above script:
```
The current state for test-db1 is Synced
```

Now we can expand that script to include other settings such as:
```

#!/bin/bash
localstatecomment=`/usr/bin/mysql -u root -e "show status like 'wsrep_local_state_comment';" | /bin/grep wsrep | /usr/bin/awk {'print $2'}`
clusterstatus=`/usr/bin/mysql -u root -e "show status like 'wsrep_cluster_status';" | /bin/grep wsrep | /usr/bin/awk {'print $2'}`
clustersize=`/usr/bin/mysql -u root -e "show status like 'wsrep_cluster_size';" | /bin/grep wsrep | /usr/bin/awk {'print $2'}`
connected=`/usr/bin/mysql -u root -e "show status like 'wsrep_connected';" | /bin/grep wsrep | /usr/bin/awk {'print $2'}`
clusteruuid=`/usr/bin/mysql -u root -e "show status like 'wsrep_cluster_state_uuid';" | /bin/grep wsrep | /usr/bin/awk {'print $2'}`
lastcommitted=`/usr/bin/mysql -u root -e "show status like 'wsrep_last_committed';" | /bin/grep wsrep | /usr/bin/awk {'print $2'}`
/bin/echo "The current state for ${HOSTNAME} is:"
/bin/echo "  Status: ${clusterstatus}, ${localstatecomment}"
/bin/echo "  Size: ${clustersize}"
/bin/echo "  UUID: ${clusteruuid}"
/bin/echo "  Last Commit: ${lastcommitted}"

```

Example of script output:
```
The current state for test-db1 is:
  Status: Primary, Synced
  Size: 3
  UUID: d89c79f4-b308-11e9-9931-8f96b3cc57b2
  Last Commit: 293
```

---

