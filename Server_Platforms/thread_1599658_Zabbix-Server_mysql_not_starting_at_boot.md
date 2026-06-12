---
title: "Zabbix-Server mysql not starting at boot"
date: 2010-10-18
forum: Server Platforms
---

### Post by maxxer on 2010-10-18
I recently installed an Ubuntu 10.04LTS server.
I have zabbix-server on that machine, and I noticed that after reboot it won't start.
Probabily, the mix of upstart and old init.d scripts result in zabbix starting when mysql is not active yet, in fact in zabbix-server.log I see it cannot reach db.

How can I make sure zabbix-server waits for mysql?
thanks

---

### Post by dspano on 2010-11-22
I did the following to get it to work correctly. 
[COLOR=#000000][FONT=Times New Roman][FONT=verdana]
sudo update-rc.d -f mysql remove
sudo update-rc.d mysql defaults
The first command removes all mysql start up scripts and the second one recreates them.[/FONT][/FONT][/COLOR]

I found this listed at this forum post:
[http://ubuntuforums.org/archive/index.php/t-1053774.html](http://ubuntuforums.org/archive/index.php/t-1053774.html)

In my case, the symlinks for the rcX.d directories were not created. Creating them with those series of commands fixed my problem.  

I hope this helps.

---

### Post by troffasky on 2010-12-15
I have this problem too. All the rcX directories and symlinks have been created [that's how the zabbix server service gets started], but it happens before MySQL has started. 

When upstart and init are mixed together, what determines the order in which services are started?

---

### Post by honeydew on 2011-02-09
dunno if your still looking, but would this be the fix [http://www.zabbix.com/forum/showthread.php?t=19781](http://www.zabbix.com/forum/showthread.php?t=19781)

---

### Post by maxxer on 2011-02-10
> **honeydew said:**
> dunno if your still looking, but would this be the fix [http://www.zabbix.com/forum/showthread.php?t=19781](http://www.zabbix.com/forum/showthread.php?t=19781)

great, thanks!

---

### Post by gnagnibu on 2011-05-31
Hi all!
This problem affected me too, but I'm in trouble with upstart configuration.

As zabbix forum says, I've created 

[I]/etc/init/zabbix-server.conf
[/I]```

# zabbix-server - Start zabbix server description     "Zabbix Server" 
author          "S. CANCHON"  
pre-start script          
ZabbixConfig=/etc/zabbix/zabbix_server.conf         
DBuser=""         
DBpassword=""           
if [ -f $ZabbixConfig ]         
then                 
DBuser=`cat $ZabbixConfig | grep '^DBUser='`                 
DBuser="${DBuser##*=}"                 
DBpassword=`cat $ZabbixConfig | grep '^DBPassword='`                 
DBpassword="${DBpassword##*=}"                  
if [ -n "$DBuser" ] && [ -n "$DBpassword" ]                 
then                         
i=0                          
while [ i -le 5 ]                        
do                         
Test=`mysqladmin -u$DBuser -p$DBpassword ping|grep alive|wc -l`                                  
if [ $Test=1 ]                                 
then                                         
i=100                                 
else                                         
sleep 5                                         
i=`expr $i + 1`                                
fi                         
done                 
fi         
fi  
end script          

start on (runlevel [2345] and started mysql)         
stop on runlevel [016]         
respawn         
expect daemon         
exec /usr/sbin/zabbix_server

```and  [I]/etc/init/zabbix-agent.conf
[/I]```

# zabbix-agent - Start zabbix agent 
description     "Zabbix Agent" 
author          "S. CANCHON"         
start on runlevel [2345]         
stop on runlevel [016]         
respawn         
expect daemon         
exec /usr/sbin/zabbix_agentd

```Next I removed zabbix-* scripts from /etc/rc.* with
```

update-rc.d -f zabbix-server remove
update-rc.d -f zabbix-agent remove

```

but next reboot, Zabbix-* don't start

Any ideas?

---

### Post by gnagnibu on 2011-05-31
/var/log/syslog says:

```

May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process (2003) terminated with status 255
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process ended, respawning
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process (2007) terminated with status 255
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process ended, respawning
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process (2011) terminated with status 255
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process ended, respawning
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process (2015) terminated with status 255
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process ended, respawning
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process (2019) terminated with status 255
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process ended, respawning
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process (2023) terminated with status 255
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process ended, respawning
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process (2027) terminated with status 255
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process ended, respawning
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process (2031) terminated with status 255
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process ended, respawning
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process (2035) terminated with status 255
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process ended, respawning
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process (2039) terminated with status 255
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process ended, respawning
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server main process (2043) terminated with status 255
May 31 10:48:07 SAERUBUNTU003 init: zabbix-server respawning too fast, stopped

```

---

### Post by gnagnibu on 2011-05-31
Both /var/log/zabbix-server/zabbix_server.log and /var/log/zabbix-server/zabbix_agentd.log say that processes were unable to create PID.

The solution is to modify /etc/init/zabbix-server.conf and /etc/init/zabbix-agent.conf in order to create pids directory.

For right configurations files see attchments

Bye!

---

### Post by RayVad on 2011-06-01
Many thanks gnagnibu. Running fine here too!

---

### Post by gnagnibu on 2011-06-01
Great!

---

### Post by gnagnibu on 2012-06-22
I improved my zabbix-server.conf file to check if MySQL can accept connections before starts zabbix:

```

description     "Zabbix Server"
author          "Vecchi Giovanni"

pre-start script

	if [ ! -d /var/run/zabbix-server ]; then
        	mkdir -p /var/run/zabbix-server
    		chown zabbix:zabbix /var/run/zabbix-server
    		chmod 755 /var/run/zabbix-server
	fi

	ZabbixConfig=/etc/zabbix/zabbix_server.conf
	DBUser=""
	DBPassword=""
	DBName=""


	if [ -f $ZabbixConfig ]
	then
		DBUser=`cat $ZabbixConfig | grep '^DBUser='`
		DBUser="${DBUser##*=}"
		DBPassword=`cat $ZabbixConfig | grep '^DBPassword='`
		DBPassword="${DBPassword##*=}"
		DBName=`cat $ZabbixConfig | grep '^DBName='`
		DBName="${DBName##*=}"

		if [ -n "$DBUser" ] && [ -n "$DBPassword" ]
		then

			while [ ! -S /var/run/mysqld/mysqld.sock ]
			do
				sleep 1
			done

			i=0

			while [ $i -le 5 ]
			do
			mysql -u$DBUser -p$DBPassword $DBName -e "SELECT \"1\"" &> /dev/null
			MYSQL_EXIT_CODE=$?

				if [ $MYSQL_EXIT_CODE=0 ]
				then
			        	i=6
		        	else
			        	sleep 5
			        	i=`expr $i + 1`
		        	fi
			done
    		fi
  	fi

end script

start on (runlevel [2345] 
	  and started mysql)
stop on runlevel [016]
respawn
expect daemon
exec /usr/sbin/zabbix_server

```

It works on Ubuntu 10.04.4

---

