---
title: "404 Error when getting rules for snort"
date: 2010-01-25
forum: Security
---

### Post by projectX on 2010-01-25
Hello every one,  I know no one know me but I've been using Ubuntu for some time and have ran into an issue trying to get the rules for snort (from this [thread]("http://ubuntuforums.org/showthread.php?t=919472") and this is the error I've been getting  ```
 root@michael:~# wget http://www.snort.org/the_rules_you_wish_to_use --2010-01-25 03:15:53--  http://www.snort.org/the_rules_you_wish_to_use Resolving www.snort.org... 68.177.102.20 Connecting to www.snort.org|68.177.102.20|:80... connected. HTTP request sent, awaiting response... 404 Not Found 2010-01-25 03:15:54 ERROR 404: Not Found.  root@michael:~# cd snort-2.8.3 -bash: cd: snort-2.8.3: No such file or directory root@michael:~# tar zxvf ../snortrules* 
```  I have also looked it up online with no answer to be found to this but have found that every one else is having the same issue, I was wondering if any one know of a new set of rules or could point me in the right direction? I've done my research and has been nothing but a dead end some far. I was able to get this one to work with out issues and if it's needed I will post the out come of the bleedingthreats.com.  ```
 cd /usr/src/snort-2.8.3/rules wget http://www.bleedingthreats.net/rules/bleeding-all.rules 
```  Outcome:  ```
 mjl08@michael:~$ cd /usr/src/snort-2.8.3/rules bash: cd: /usr/src/snort-2.8.3/rules: No such file or directory mjl08@michael:~$ wget http://www.bleedingthreats.net/rules/bleeding-all.rules --2010-01-25 03:18:15--  http://www.bleedingthreats.net/rules/bleeding-all.rules Resolving www.bleedingthreats.net... 84.200.234.232 Connecting to www.bleedingthreats.net|84.200.234.232|:80... connected. HTTP request sent, awaiting response... 301 Moved Permanently Location: / [following] --2010-01-25 03:18:15--  http://www.bleedingthreats.net/ Reusing existing connection to www.bleedingthreats.net:80. HTTP request sent, awaiting response... 200 OK Length: unspecified [text/html] Saving to: `index.html'      [                                    ] 5,600       34.1K/s   in 0.2s      2010-01-25 03:18:16 (34.1 KB/s) - `index.html' saved [5600] 
```

---

### Post by Sarmacid on 2010-01-25
> **projectX said:**
> ```
 root@michael:~# wget http://www.snort.org/the_rules_you_wish_to_use
--2010-01-25 03:15:53--  http://www.snort.org/the_rules_you_wish_to_use
Resolving www.snort.org... 68.177.102.20 Connecting to www.snort.org|68.177.102.20|:80... connected. HTTP request sent, awaiting response... 404 Not Found 2010-01-25 03:15:54 ERROR 404: Not Found.
root@michael:~# cd snort-2.8.3 -bash: cd: snort-2.8.3: No such file or directory root@michael:~# tar zxvf ../snortrules* 
```

You need to change the "the_rules_you_wish_to_use" part for the adequate URL.

---

### Post by bodhi.zazen on 2010-01-25
See this page :

[http://www.snort.org/start/rules](http://www.snort.org/start/rules)

---

### Post by projectX on 2010-01-25
> **Sarmacid said:**
> You need to change the &quot;the_rules_you_wish_to_use&quot; part for the adequate URL.

  Guess that's what I get when I try to do this at 4am in the morning >

---

