---
title: "Apache2 : Invalid command 'php_value'"
date: 2019-10-03
forum: Server Platforms
---

### Post by simsimpicpic on 2019-10-03
Hello...
When i do
```
service apache2 restart
Job for apache2.service failed because the control process exited with error code.
```

```
root@vmi296146:/etc/apache2/sites-enabled# service apache2 status
[COLOR=#ff0000]&#9679;[/COLOR] apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: [COLOR=#ff0000]failed [/COLOR](Result: exit-code) since Thu 2019-10-03 18:26:46 CEST; 22s ago
  Process: 10714 ExecStop=/usr/sbin/apachectl stop[COLOR=#ff0000] (code=exited, status=1/FAILURE)[/COLOR]
  Process: 10721 ExecStart=/usr/sbin/apachectl start [COLOR=#ff0000](code=exited, status=1/FAILURE)[/COLOR]
 Main PID: 10507 (code=exited, status=0/SUCCESS)


Oct 03 18:26:46 vmi296146.contaboserver.net systemd[1]: Starting The Apache HTTP Server...
Oct 03 18:26:46 vmi296146.contaboserver.net apachectl[10721]: AH00526: Syntax error on line 5 of /etc/apache2/sites-enabled/pterodactyl.conf:
Oct 03 18:26:46 vmi296146.contaboserver.net apachectl[10721]: Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration
Oct 03 18:26:46 vmi296146.contaboserver.net apachectl[10721]: Action 'start' failed.
Oct 03 18:26:46 vmi296146.contaboserver.net apachectl[10721]: The Apache error log may have more information.
Oct 03 18:26:46 vmi296146.contaboserver.net systemd[1]: apache2.service: Control process exited, code=exited status=1
Oct 03 18:26:46 vmi296146.contaboserver.net systemd[1]: apache2.service: Failed with result 'exit-code'.
Oct 03 18:26:46 vmi296146.contaboserver.net systemd[1]: [COLOR=#ff0000]Failed to start The Apache HTTP Server.[/COLOR]
```

Somebody can help me ?

---

### Post by SeijiSensei on 2019-10-03
Did you install PHP as well as Apache? The "php_value" directive lets you set [configuration values for PHP]("https://www.php.net/manual/en/configuration.changes.php") in the Apache configuration file.

The easiest one-step method is to use "sudo apt install lamp-server^" which will install Apache, PHP, and also MySQL.

---

### Post by LHammonds on 2019-10-04
Assuming you are using Ubuntu Server 18.04:

```
sudo apt install php7.2 libapache2-mod-php7.2
```

That will install PHP and the Apache to PHP connector.

Here are the steps I use when setting up an [Apache web server]("https://ubuntuforums.org/showthread.php?t=2426285").

LHammonds

---

