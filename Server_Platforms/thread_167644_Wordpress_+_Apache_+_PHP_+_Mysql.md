---
title: "Wordpress + Apache + PHP + Mysql"
date: 2006-04-28
forum: Server Platforms
---

### Post by pjebr on 2006-04-28
Hi i am new to Linux,

i want to install wordpress, so i run "sudo apt-get install wordpress" in the terminal. After downloaded all packges (including apache, php and mysql) i got some error messages like:

```

Setting up apache (1.3.33-8ubuntu1) ...
newaliases: fatal: open /etc/postfix/main.cf: No such file or directory
dpkg: error processing apache (--configure):
 subprocess post-installation script returned error exit status 1

```

```

Setting up wordpress (1.5.2-1) ...
Errors were encountered while processing:
 apache
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So, i will need to reinstall or these errors is not too bad? I tested my apche and php and its working (i tested with phpinfo() function).

---

### Post by Ensnared on 2006-04-28
Funny... the apache install-script runs newaliases, which is a utility used for postfix, which is an MTA (mail transport agent, or mailserver if you prefer).

Not sure why apache would need to do this - maybe it's for adding the "webmaster" mail-alias? It's stupid that this is a fatal error since not everyone are running a mailserver and a webserver on the same box - this looks very much like a bug with the apache install-script from where I'm sitting.

Oh well - you can fix this either by installing postfix:```
 sudo apt-get install postfix
```...or _maybe_ by creating the file it's trying to access just to get past the error, but that probably won't work since the newaliases-command - as far as I know - looks for the location of the actual aliases database which is defined in that file.

I suggest you simply install postfix, and if you don't need it, uninstall it afterwards:```
sudo apt-get remove --purge postfix
```

---

