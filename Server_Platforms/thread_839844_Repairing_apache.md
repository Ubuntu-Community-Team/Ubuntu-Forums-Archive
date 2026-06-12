---
title: "Repairing apache"
date: 2008-06-24
forum: Server Platforms
---

### Post by Geran on 2008-06-24
Before I say thing potentially boring, if anyone has a way for me  to completely remove and re install apache from the terminal, that would be great, but read on and maybe someone will see another solution. (And I mean completely, totally re-install everything to do with apache.

Hi, I'm having some trouble with my apache server and it's fairly important that I get it fixed. 

The error first started when I went to edit my php.ini file to increase the memory limit in /etc/php5/apache2/php.ini. When I tried to restart my server the next time, the errors started. It reported that it could not load a php module.

After that, I thought it would work fine if I restored a backup copy of my apache2 directory. This seemed to solve one problem but generate another, now my apache system gives this error when I try to start it.

```

 * Starting web server apache2
Syntax error on line 143 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration

```

If anyone has a fix for this, that would be great, otherwise, like I said, if there is a way to completely remove and re-install apache, that'll be fine.

---

### Post by bikeboy on 2008-06-24
What does line 143 of /etc/apache2/apache2.conf say?

If you want to completely remove then reinstall try this:
```
sudo apt-get --purge remove apache2 && sudo apt-get install apache2
```

---

### Post by Geran on 2008-06-24
<Files ~ "^\.ht">
    Order allow,deny      <--- line 143
    Deny from all
</Files>

I'll hold off on your complete re install advice for now.

---

### Post by bikeboy on 2008-06-24
Hmm, that section doesn't seem to have any connection to php. However, an easy way to check is to comment out that whole area and restart apache. If it works, you know there's an issue with that section.
```

#<Files ~ "^\.ht">
#Order allow,deny <--- line 143
#Deny from all
#</Files>

```

---

### Post by Geran on 2008-06-24
Sorry, I wasn't clear, the issue is no longer just php, but my whole apache system fails. Yes, when I comment out that section, everything comes back online, but the problem is that none of my files seem to exist, like my entire document root got erased.

---

### Post by bikeboy on 2008-06-24
Okay, I've had proplems with Order statements before. It would be worth checking the apache2 documentation online (google gives good results in my experience), however it should work if you just comment out that second line.

---

### Post by Geran on 2008-06-24
Ok, but why would my apache server suddenly be unable to recognize a perfectly valid script?

---

### Post by Geran on 2008-06-24
And how is this possible?

Not Found

The requested URL / was not found on this server.
Apache/2.2.8 (Ubuntu) Server at xx.xxx.xxxx.xxx Port 80


??

---

