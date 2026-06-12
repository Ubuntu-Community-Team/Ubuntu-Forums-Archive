---
title: "Apache Default stopped working on 8.10"
date: 2009-04-13
forum: Server Platforms
---

### Post by jwf1 on 2009-04-13
I installed the apache2 server and enabled SSL. The default web page displayed ok on the first day, but not on any day after that. I tried reinstalling but that did not make any difference.

(I noticed my situation is very similar to another post, but there are some differences and therefore I created a separate post.)


Results from a restart command:

```
 /etc/apache2/sites-enabled$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                      apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```   

I noticed that there are no logs created in /var/log/apache2 with todays date. Only logs for the date that I installed apache2.
My "apache.conf" does contain an error log directive:
   **ErrorLog /var/log/apache2/error.log**
   


```
NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
```

And my 000-default code:
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
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

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```



Appreciate any help in this.

Thank you in advance.

---

### Post by cdenley on 2009-04-13
Sounds like you already have a server listening on port 80. Post the output from this command.
```

sudo netstat -tlnp

```

---

### Post by jwf1 on 2009-04-13
Thanks for your reply
Here's the output

```
~$ sudo netstat -tlnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      4649/cupsd      
tcp6       0      0 :::80                   :::*                    LISTEN      5116/apache2    
tcp6       0      0 :::443                  :::*                    LISTEN      5116/apache2    

```

---

### Post by cdenley on 2009-04-13
Do/did you have your SSL certificate password-protected so apache prompts you for a password when it is started? It appears apache is already listening on port 80/443, yet when you restart apache, it doesn't kill the original instance of apache. I have only seen this when the apache startup script is waiting for you to enter the password for the SSL certificate on the local console after the server has been rebooted. If this is the case, you can either enter the password on the local console, or kill apache manually, then start it.
```

sudo killall apache2
sudo /etc/init.d/apache2 restart

```

---

### Post by jwf1 on 2009-04-13
Ok, I think you are correct. It looks as though apache2 is waiting for the certificate password, but there is no console per se displayed waiting for a reply. 
If I kill the apache2 process, then restart, all is well. 
So, now I'm wondering, because I have an encrypted certificate how is it that there is no dialog prompting me for a password. (I dont' know what the normal operation should be). 
The basic installation instruction I followed had me create a certificate and a key. Should there be some other instructions or configuration settings that would start apache2 and, either post the dialog for passkey entry, or automatically start the the apache server authenticating the password upon reboot?    

I noticed in the error.log the following line:
```
[Mon Apr 13 18:52:19 2009] [warn] RSA server certificate CommonName (CN) `XXXXXXX' does NOT match server name!?
```

Does this mean if I recreate the certificate and match the server name with the RSA CN common name, the server will come up without any key prompt?

---

### Post by cdenley on 2009-04-13
If I remember correctly, when you create the key, you have the option to create a password for the key. If you don't set a password, then you will not be prompted for one. If you do set a password, then you should be prompted for one when the computer is first booted on tty1. I don't think the warning you posted is related. When you killed apache, then restarted apache, were you prompted for a password? Are you able to reproduce the original problem, or does it work correctly now?

---

### Post by jwf1 on 2009-04-14
Apache starts working correctly after I perform the kill/restart.   
.. and yes I am prompted for my password after the restart.

>  Are you able to reproduce the original problem
Yes. On any subsequent reboot apache starts, (netstat shows the process) but never displays a password prompt, so I guess never completely initializes. I can try to recreate the certificate without a password to see if apache will initialize fully after a reboot.

By the way cdenley, thanks for your assistance on this.

---

### Post by cdenley on 2009-04-14
> **jwf1 said:**
> Apache starts working correctly after I perform the kill/restart.   
.. and yes I am prompted for my password after the restart.


Yes. On any subsequent reboot apache starts, (netstat shows the process) but never displays a password prompt, so I guess never completely initializes. I can try to recreate the certificate without a password to see if apache will initialize fully after a reboot.

By the way cdenley, thanks for your assistance on this.

It probably does prompt you for a password, you just don't see it. Are you physically sitting in front of the server? Maybe other init scripts were running in parallel, and the prompt is no longer on the screen, but is still waiting for your input. If there actually isn't a password prompt on the local console, I would file a bug report.

---

### Post by jwf1 on 2009-04-14
OK, I think I am missing something here.

I am sitting in front of the machine. I am running this (apache2) on my desktop machine. When you say 'console', is that a different display than my desktop display? I kill and restart apache from a terminal session and that is where I see the prompt for a password, but on a reboot, there is no terminal session open, only my desktop display. do I need to 'log in' to the apache server with a session to see the prompt?

Also, I tried to create the certificate without a passphrase and it seems that is not allowed:  
(When asked for the pass phrase, I just hit a enter) 

Result:
```
 sudo openssl genrsa -des3 -out server.key 1024
Generating RSA private key, 1024 bit long modulus
.++++++
.....++++++
e is 65537 (0x10001)
Enter pass phrase for server.key:
6296:error:28069065:lib(40):UI_set_result:result too small:ui_lib.c:849:You must type in 4 to 8191 characters
Enter pass phrase for server.key:
```

---

### Post by cdenley on 2009-04-14
Before you receive a login prompt on tty1, the apache init scripts runs and prompts you for your password. At least that is how it worked on 8.04. I think that it may continue with the boot process, though, which will result in output from other scripts being printed after the prompt for your SSL key's password. If you hit enter, though, it should re-print apache's prompt, since it is still waiting for your input. Do you successfully login to the first TTY on your server locally before killing apache? You will not see the initial password prompt from another TTY (ctrl+alt+f2, etc) or a remote terminal like an SSH session.

[http://madboa.com/geek/openssl/#key-removepass](http://madboa.com/geek/openssl/#key-removepass)

---

### Post by jwf1 on 2009-04-14
Ok, after a kill/restart, apache working normally,, then I reboot again, apache will not display a webpage, Netstat says it is operational.
Looking at tty1 shows normal startup,, no evidence of any password prompt.

e.g. (ctl-alt-f1)

```
Boot from (hd0,3) ext3
Starting up ...
Loading please wait ...
(some more lines here then,)
kinit: no resume image, doing normal boot... 
```

Also checking the syslog shows nothing about apache

---

### Post by cdenley on 2009-04-14
Aren't your init scripts displayed anywhere?
```

* Starting web server apache2
apache2: Could not reliably determine the server fully qualified domain name,
using 127.0.0.1 for ServerName
Apache/2.2.9 mod_ssl/2.2.9 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide the pass phrases.

hostname:443 (RSA)
Enter pass phrase: 

```
I configured an encrypted key on my 8.10 desktop computer, and when I press ctrl+alt+f1 after the computer finishes booting, that is what I have a the bottom of the screen.

You can either find where that prompt is, decrypt your key using the instructions I linked to, or prevent apache from attempting to start at boot.

---

### Post by jwf1 on 2009-04-14
Hmm. No, I do not see my init scripts anywhere.
I see the output script you show only when I perform a restart after I've killed the current apache process. 

I've just rebooted again,(because of an unrelated problem).

My tty1 shows what I have listed previously (no mention of apache) 

my netstat results:

```
xxx@ubuntu-desktop:~$ sudo netstat -tlnp
[sudo] password for xxx: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      4652/cupsd      
tcp6       0      0 :::80                   :::*                    LISTEN      5120/apache2    
tcp6       0      0 :::443                  :::*                    LISTEN      5120/apache2 
```


So apache2 is pid 5120


If I look at the apache2 script, I attempt "sud0 /etc/init.d/apache2 stop"

Result:
```
xxx@ubuntu-desktop:~$ sudo /etc/init.d/apache2 stop
 * Stopping web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
```

The script suggests that it cannot shutdown apache2 normally.

The output message "*stopping web server Apache2" suggest that in the init script that tests for htcacheclean, the test is not successful. 


Could my init script may be corrupt? The check_htcacheclean() function looks incomplete. My values are:
HTCACHECLEAN_MODE=daemon  
HTCACHECLEAN_RUN=auto

**Notice: there is no closing brace for HTCACHECLEAN_RUN"  = "auto" line.**

```
check_htcacheclean() {
	[ "$HTCACHECLEAN_MODE" = "daemon" ] || return 1

	[ "$HTCACHECLEAN_RUN"  = "yes"    ] && return 0

	[ "$HTCACHECLEAN_RUN"  = "auto" \
	  -a -e /etc/apache2/mods-enabled/disk_cache.load ] && return 0
	
	return 1
```
}

Ok,, on further investigation, I see another test in the script fails because my sever.key is empty.

I'll recreate and copy the key to the correct location, and restest.



Update:  The 'other' thing I was checking on was, I get an error on command  "apache2 configtest"
 
```
xxx@ubuntu-desktop:/etc/apache2/mods-enabled$ apache2ctl configtest
Syntax error on line 52 of /etc/apache2/sites-enabled/default-ssl:
SSLCertificateKeyFile: file '/etc/ssl/private/server.key' does not exist or is empty 
```

I thought this may have something to do with the apache2 script failing

I verified there is no syntax error on line 52
and also verified that file /etc/ssl/private.server.key exists and is not empty.

---

