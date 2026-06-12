---
title: "Error installing wordpress on Ubuntu Server 8.04.4 LTS"
date: 2013-02-16
forum: Server Platforms
---

### Post by TriBobbyJones on 2013-02-16
I've tried doing searches on google and these forums to help me answer this, so any help (whether a solution to the problem or advice on better searching in the future) is much appreciated.

I'm trying to install wordpress on my ubuntu server 8.04.4 (which I have installed on an old HP desktop tower).

I'm using this guide to install WP:
[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

For starters, when I get to the point of :
> sudo gzip -d /usr/share/doc/wordpress/examples/setup-mysql.gzI get the error: No such file or directory

Moving forward with the guide, though, I'm able to setup the mysql (I believe that's what happening) with:

> sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress localhostThis seems to go successfully as the terminal tells me to "Goto [http://localhost](http://localhost) to setup Wordpress."

Now, here's where the real error (seems) to be starting. When I navigate in firefox from my macbook to [http://](http://)[mydynamicipaddress]/wordpress, I get the following displayed in the browser:
> 
404 Not found
**Warning**:  require_once(/etc/wordpress/config-[mydynamicipaddress].php) [[function.require-once]("http://192.168.1.125/wordpress/function.require-once")]: failed to open stream: No such file or directory in **/etc/wordpress/wp-config.php** on line **16**

**Fatal error**:  require_once() [[function.require]("http://192.168.1.125/wordpress/function.require")]: Failed opening required '/etc/wordpress/config-[mydynamicipaddress].php' (include_path='.:/usr/share/php:/usr/share/pear') in **/etc/wordpress/wp-config.php** on line **16**I've tried purging wordpress and reinstalling, updating and upgrading ubuntu, and still end at this message. Anyone have any suggestions?

Thanks!

---

### Post by snowpine on 2013-02-16
Welcome to the forums!

First, are you aware you are using the April 2008 release of Ubuntu, there have been 9 new releases since 8.04, and support ends in 2 months?

Anyway, in Ubuntu we typically install apps from the repos whenever possible, so have you tried simply:

```
sudo apt-get update
sudo apt-get install wordpress
```

---

### Post by TriBobbyJones on 2013-02-16
Thanks for the quick reply, snowpine.

I've run sudo apt-get update and when I check lsb_release -a, I'm still seeing that I've got release 8.04. Am I able to update to 12.04 through my command line, or would I need to download the ISO to a cd and boot from that?

---

### Post by snowpine on 2013-02-16
'sudo apt-get update' doesn't do what you think it does; it simply refreshes the list of available packages from the Ubuntu repo server, allowing you to easily install applications (such as wordpress) with the 'apt-get install' command.

"How do I upgrade from 8.04 to 12.04?" doesn't have a 1-or-2 sentence answer. I suggest you start by reading these links: 

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

Personally I would do a clean reinstall and start my new Wordpress site on a totally fresh platform. :)

---

### Post by TriBobbyJones on 2013-02-17
Updated (thanks for that suggestion), and got the wp up and running by renaming a conf file to match with my ip address.

Thanks!

---

