---
title: "LAMP + WordPress"
date: 2008-12-14
forum: Server Platforms
---

### Post by CM-Mitch on 2008-12-14
So I'm trying to setup a WordPress blog for testing on an extra PC I have. Here is a rundown of what I've done:

Installed Ubuntu 8.10 server 32-bit with the LAMP and OpenSSH server options.  Everything seems to work fine thus far, I can ssh to the server just fine.  I can http to the servers IP address and get the default apache "It Works!" Page.  I can create a new php page with some php commands and it works just fine.  I even installed vsftpd so I can ftp to /var/www (I did not change the default website location) for file editing/uploading purposes.

All good so far.  Now, for the wordpress install I've been following the instructions on this page:  [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

I installed wordpress with this command:

```
sudo apt-get install wordpress
```

Command executed fine.  Following the instructions further I ran this command:

```
sudo ln -s /usr/share/wordpress /var/www/wordpress
```

This command also executed fine.  But my next command returned this error:

```
sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n root localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=2.88 ms

--- localhost ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 2.888/2.888/2.888/0.000 ms
/usr/share/doc/wordpress/examples/setup-mysql: 180: Bad substitution

```

Any ideas on what I'm doing wrong?  I assume this is trying to setup a mysql database for use with wordpress, is that correct?  If so, would this mean I did not get mysql installed properly?  I'm not familiar with mysql enough to know how to test and troubleshoot myself.

When I http to the wordpress directory of my default website I get this error:

```
404 Not found
Warning: require_once(/etc/wordpress/config-192.168.1.111.php) [function.require-once]: failed to open stream: No such file or directory in /etc/wordpress/wp-config.php on line 16

Fatal error: require_once() [function.require]: Failed opening required '/etc/wordpress/config-192.168.1.111.php' (include_path='.:/usr/share/php:/usr/share/pear') in /etc/wordpress/wp-config.php on line 16
```

Any help would be appreciated, thanks.

---

### Post by CM-Mitch on 2008-12-15
I still haven't figured it out.  Searches for "180: Bad substitution" don't turn up any related results.  I tried looking for an Ubuntu install guide on WordPress.org but I didn't manage to find anything usefull.  I even loaded a fresh install of Ubuntu 8.10 on a different machine and got the same error when trying to configure wordpress.  Maybe I'll go back to 8.4 and see if it produces different results.

---

### Post by CrucifiedEgo on 2008-12-15
Instead of using the version of wordpress in apt, try downloading it from wordpress.org.  it will be a newer(more secure) version anyway.

---

### Post by CM-Mitch on 2008-12-15
I'll try that.  I don't know why but I just assumed the apt version would be up to date.  Thanks!

---

### Post by Coreigh on 2008-12-15
Which version ofUbuntu are you using?

Can you log in to MySQL?```
mysql -u username -p
```

If you can  the show databases:```
mysql> show databases;
```

Does the wordpress database exist? I don't know if your script is supposed to create it or configure it.

If you can't log in then that is probably the problem, perhaps root does not have access or you need to use a password with the script.

Using the newest version direct from WordPress will give you the latest features and updates but will not likely solve your problem.

---

### Post by CrucifiedEgo on 2008-12-15
Sure it will solve his problem.  He's running into a bizarrely clunky ubuntu-ized version of wordpress.  the normal installer is much more user friendly.

---

