---
title: "PHP Files in /var/www executes, but not under subdirectory"
date: 2009-08-19
forum: Server Platforms
---

### Post by yeswekey on 2009-08-19
Hi... I've decent experience Apache/MySQL/PHP in windows... but new to ubuntu (but not so dumb :P)

Any PHP files located in /var/www executes fine. But if i create symlink to a site that i had built already, and put [http://localhost/quiz](http://localhost/quiz) in my browser, it asks to download index.php 

The target files have 775 permission.

Plz help me!

I'm using apache2 and php5 :)

And by the way, I just installed KDE last night... i know that shouldn't affect... still... may be therez some relationship! :P

---

### Post by dmizer on 2009-08-19
Please post:
```
sudo ls -la /var/www
```

---

### Post by yeswekey on 2009-08-19
Here it is:
```
kaushik@kaushik-desktop:/var/www$ sudo ls -la /var/www
total 20
drwxr-xr-x  2 root root 4096 2009-08-19 15:52 .
drwxr-xr-x 16 root root 4096 2009-08-19 13:27 ..
-rw-r--r--  1 root root   45 2009-08-19 13:27 index.php
lrwxrwxrwx  1 root root   61 2009-08-19 15:52 quiz -> /media/WINDOWS XP/Documents and Settings/kaushik/Desktop/quiz
-rw-r--r--  1 root root   18 2009-08-19 13:45 test.php

```

---

### Post by yeswekey on 2009-08-19
Permission wrong??? (I dont think so as all hav rwxrwxrwx)

plz help :confused:

---

### Post by yeswekey on 2009-08-19
oops... this is wierd... 

[http://localhost/quiz/quiz/quiz](http://localhost/quiz/quiz/quiz) doesn't load
But
[http://127.0.0.1/quiz/quiz/quiz](http://127.0.0.1/quiz/quiz/quiz) works perfectly :confused:

Why doesn't localhost work??
Is my site insecure??

Like every1, i dont want others to be able to "Download" my php files in any way.

---

### Post by credobyte on 2009-08-19
Post the output of:
```
cat /etc/hosts

```

---

### Post by yeswekey on 2009-08-19
WTF!!! Bug was in firefox! Ooofff!!!!


* => Please read this:
This happens only in firefox
If i goto: [http://localhost/](http://localhost/)
 it works fine
If i goto: [http://localhost/quiz](http://localhost/quiz)
 it works fine
If i goto: [http://localhost/quiz/quiz](http://localhost/quiz/quiz)
 it works fine
If i goto: [http://localhost/quiz/quiz/quiz](http://localhost/quiz/quiz/quiz)
 it downloads the index.php file
But works fine if i put [http://127.0.0.1/quiz/quiz/quiz](http://127.0.0.1/quiz/quiz/quiz)
With opera, localhost also worked fine here.


I used tamperdata plugin to monitor http headers from firefox. It differed only in the host string. But the server's reply didn't change (I tried sending them manually using telnet @ port 80). The reply i got was same and as expected.

So its firefox which downloads the file under some circumstances which i donno*

I mapped 172.16.0.2 (My LAN IP) to 'localhost' in my brother's laptop (vista home basic).then tried [http://localhost/blabblah](http://localhost/blabblah) from there using firefox.

It did work fine.

So is the bug with Firefox 3.5.2 for Ubuntu??

Should i report it?

---

### Post by dmizer on 2009-08-19
Nope, misconfigured server: [http://ubuntuforums.org/showpost.php?p=5780073&postcount=12](http://ubuntuforums.org/showpost.php?p=5780073&postcount=12)

---

### Post by yeswekey on 2009-08-23
But it works fine from opera and konqueror! 

And only that particular "index.php" (in that particular directory) is getting downloaded, only by firefox.
But even in firefox, if i use "127.0.0.1" instead of "localhost", it works fine.
Other browsers seem to work anyway (127.0.0.1 or localhost).

I know the Host: header is changed if i change that... so i tried telneting and gave the following HTTP request :

```
GET /quiz/quiz/quiz/ HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0
```

and then:

```
GET /quiz/quiz/quiz/ HTTP/1.1
Host: 127.0.0.1
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0
```


The HTML sent by server was exactly same. So its a bug with firefox. Am i wrong??

Plz tell me the exact prob [-o<

---

### Post by yeswekey on 2009-08-23
> **credobyte said:**
> Post the output of:
```
cat /etc/hosts

```
```
kaushik@kaushik-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 kaushik-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by dmizer on 2009-08-23
> **yeswekey said:**
> But it works fine from opera and konqueror! 

The HTML sent by server was exactly same. So its a bug with firefox. Am i wrong??

Plz tell me the exact prob [-o<

I am fairly sure that the link above will fix your problem. Opera and Konqueror may be loading the page even though there is a problem on the server (in other words, they may be handling the error better).

Did you try the fix? It's not going to hurt anything if you do.

---

### Post by yeswekey on 2009-08-31
bump

---

### Post by dmizer on 2009-08-31
> **yeswekey said:**
> bump

> **dmizer said:**
> Did you try the fix? It's not going to hurt anything if you do.
Does the bump mean you've tried it and it didn't work?

Browsers are not created equal and don't handle pages with problems in the same way. I've seen a badly written PHP script work perfectly well in Firefox and fail completely in IE or Opera. It's just as likely to happen the other way around.

This is why web designers have to test their sites with multiple browsers.

---

