---
title: "PHP pages getting prompted for downloading/Cant bind to add 80"
date: 2006-08-31
forum: Server Platforms
---

### Post by barrmulio on 2006-08-31
I have a feeling that a botchy ssl install may have screwed up a perfectly working server (apache2 and php5 - in Dapper), but now when i hit a phtml(?) or php page firefox and IE prompt to download the page rather than loading it.  There was also a patch update to libapache2-mod-php5

I reinstall apache2, php5, the libapache2-mod-php5 files, etc after a --purge remove (of apache2 apache2common and php5), i can hit a localhost basic html file, but firefox prompts to download testphp.php.  

when attempting to restart apache2, i also get 
```

(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

```

and not sure if those are related, but i can resolve to my server via the internet

thanks in advance for any help

---

