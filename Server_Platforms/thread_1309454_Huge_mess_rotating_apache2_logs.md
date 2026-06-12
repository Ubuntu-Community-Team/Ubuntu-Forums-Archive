---
title: "Huge mess rotating apache2 logs"
date: 2009-11-01
forum: Server Platforms
---

### Post by ngmachado on 2009-11-01
I desperately need help with rotating Apache2 Virtual Hosts log files.

Here's my config, located in /etc/logrotate.d/apache2

```

/var/log/apache2/*.log {
	weekly
	missingok
	rotate 8
	compress
	delaycompress
	notifempty
	create 640 root adm
	sharedscripts
	postrotate
		if [ -f "`. /etc/apache2/envvars ; echo ${APACHE_PID_FILE:-/var/run/apache2.pid}`" ]; then
			/etc/init.d/apache2 reload > /dev/null
		fi
	endscript
}

# virtual hosts
/home/machado/www/*/log/*.log {
	olddir old
	weekly
	missingok
	rotate 5200
	compress
	delaycompress
	notifempty
	create 644 root root
	sharedscripts
	postrotate
		if [ -f "`. /etc/apache2/envvars ; echo ${APACHE_PID_FILE:-/var/run/apache2.pid}`" ]; then
			/etc/init.d/apache2 reload > /dev/null
		fi
	endscript
}


```

The first rule is the original one, all I've done was adding the rule for my 3 virtual hosts located in /home/machado/www/

The above config is working. The problem is, after rotation, Apache keeps writing in the old logs (access.1.log), instead of the newly created.

I thinks it's something related to the postrotate script, because if I restart Apache manually after rotation, everything gets back to normal.

Thank you.

---

