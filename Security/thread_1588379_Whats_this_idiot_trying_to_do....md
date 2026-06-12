---
title: "Whats this idiot trying to do?..."
date: 2010-10-04
forum: Security
---

### Post by VcDeveloper on 2010-10-04
Just checking my apache access.log and found a couple of idiot with a CHINA IP block address trying to do:

```

222.45.112.59 - - [04/Oct/2010:12:21:36 -0700] "GET http://218.10.111.119/check.php HTTP/1.1" 404 528 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"

58.218.204.110 - - [04/Oct/2010:16:41:19 -0700] "GET http://98.126.64.106/judge123.php HTTP/1.1" 404 530 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"


```what are they trying do run a MySql injection script?

....and can anyone tell me what apache is doing itself internally?  I have serveral of this sandwhich between lots of my own accesses from my development pc.
```
127.0.0.1 - - [04/Oct/2010:08:56:42 -0700] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.12 (Ubuntu) (internal dummy connection)"

```I'm running Drupal 6.19 on a 9.10 Karmic in a VM.  This is my DMZ Zone server and using it as a test site to configure my live servers before going live on the internet.

---

### Post by searchfgold6789 on 2010-10-05
According to the internet that IP address is "offensive"...
It is from a China railway system.

---

### Post by VcDeveloper on 2010-10-05
Oh yea! I installed IPBlock last night.  Excellent utility!  And, I see there IP in my IPBlock log and not showing up in my access.log.

I Suggest everyone getting this utility if not already!

---

### Post by BkkBonanza on 2010-10-05
It doesn't look like SQL injection but "hackers" will often try various default script names known to have vulnerabilities on the random chance that you are running whatever software. Once they get a hit on that they can log it and come back for more extensive exploration. 

A SQL injection attempt would typically have a long string of "special" characters in the GET request (or POST data, but that wouldn't be in the log).

A buffer overflow attempt would typically have a huge data string with lots of "weird" characters.

By doing a GET with known script name they can often figure out you're using some software and then later try known SQL/buffer overflow attacks on you that may work.

---

### Post by VcDeveloper on 2010-10-05
> **BkkBonanza said:**
> It doesn't look like SQL injection but "hackers" will often try various default script names known to have vulnerabilities on the random chance that you are running whatever software. Once they get a hit on that they can log it and come back for more extensive exploration. 

A SQL injection attempt would typically have a long string of "special" characters in the GET request (or POST data, but that wouldn't be in the log).

A buffer overflow attempt would typically have a huge data string with lots of "weird" characters.

By doing a GET with known script name they can often figure out you're using some software and then later try known SQL/buffer overflow attacks on you that may work.

Thanks for the knowledge about this!

---

### Post by BkkBonanza on 2010-10-06
These vulnerabilities can be serious so it's good reason to keep web site apps, like forums and such, up to date. There may be known problems that hackers target and if you are lazy about updating there's some chance they will find them. I read somewhere a while back that these types of "holes" are probably the most likely way that web servers get hacked.

---

### Post by OpSecShellshock on 2010-10-06
In addition to SQL injection, it may also be a good idea to look up Remote File Inclusion, which tends to get thrown at PHP constantly from the web. Best way to protect your site is to be running the current version, and also check the configurations prior to putting the server out on the web.

The quick way to check might be to try using the URL bar of a web browser to access a file that you know doesn't exist on that site, and see what kind of error you get. Then check the server logs again and see what the same traffic looked like from that end.

---

### Post by VcDeveloper on 2010-10-06
I shall do that!  Thank everyone, I appreciate the help!

---

### Post by Kinstonian on 2010-10-06
Looks like the check.php and judge123.php are ProxyJudge scripts used to test how anonymous a proxy is.  You say they're in China so they might be looking for open proxies to use to get around the censorship imposed by their government.

---

### Post by VcDeveloper on 2010-10-07
> **Kinstonian said:**
> Looks like the check.php and judge123.php are ProxyJudge scripts used to test how anonymous a proxy is.  You say they're in China so they might be looking for open proxies to use to get around the censorship imposed by their government.

Ok Thanks!

---

