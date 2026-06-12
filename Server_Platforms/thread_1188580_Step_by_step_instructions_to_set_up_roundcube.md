---
title: "Step by step instructions to set up roundcube"
date: 2009-06-15
forum: Server Platforms
---

### Post by jmaryinchina on 2009-06-15
The package roundcube doesn't work out of the box. Some warning at install and then [http://localhost/roundcube](http://localhost/roundcube) is mute, or send insults.

```
sudo apt-get install roundcube roundcube-mysql
sudo gedit /etc/roundcube/apache.conf
```

uncomment the lines starting by "Alias", then save.

```
sudo /etc/init/d/apache2 restart
```Then 

```
sudo gedit /usr/share/roundcube/program/include/iniset.php
```add the line :
[php]
$include_path.= '/usr/share/php' . PATH_SEPARATOR;[/php]after the line 46 :

[php]$include_path.= INSTALL_PATH . 'program/include' . PATH_SEPARATOR;[/php]then save and go to [http://localhost/roundcube](http://localhost/roundcube)

---

### Post by Cheesemill on 2009-06-16
I've never installed it from the repos before, I just download it from the roundcube website and follow the instructions here:

[http://trac.roundcube.net/wiki/Howto_Install](http://trac.roundcube.net/wiki/Howto_Install)

I've never had any issues installing, these instructions should work fine if you install from the repos as well.

---

### Post by jmaryinchina on 2009-06-21
Before it was not in the repositery. Now it is, and it is buggy.

---

### Post by kustomjs on 2009-06-22
I had roundcube installed on my email server and I don't like it and there is a known issue with roundcube about sending large attachments so I have removed roundcube and replaced it with squirrelmail and I am much happier with squirrelmail then roundcube.

---

### Post by cwall64 on 2009-07-17
I still just get a blank page after a user logs on...  I guess I will try the non-packaged version!

EDIT: changed memory_limit=16M to 512M (from roundcube forums) in "/etc/php5/apache2/php.ini" then restart apache and all is working.

---

### Post by ruark1 on 2010-08-17
Thanks for the walk through!

also:
your second code should read
sudo /etc/init.d/apache2 restart

---

### Post by andrias6274 on 2013-02-23
i've installed roundcube but always show ".phtml" 

how to solve the problem ?

tks

---

### Post by howefield on 2013-02-23
Old thread closed.

Feel free to start afresh.

---

