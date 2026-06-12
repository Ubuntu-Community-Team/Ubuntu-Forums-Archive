---
title: "Safe to install fpm?"
date: 2012-12-03
forum: Server Platforms
---

### Post by matimont on 2012-12-03
Hi,

How can I determine if I have php-fpm installed? It is safe to install it on a working server with more than 18 web sites already in place?

Thank you.

---

### Post by Ms. Daisy on 2012-12-03
You can find out if it's installed by using dpkg
```
dpkg -l | fpm*
```

---

### Post by matimont on 2012-12-05
> **Ms. Daisy said:**
> You can find out if it's installed by using dpkg
```
dpkg -l | fpm*
```

I ran the command and I get this:

No command 'fpm*' found, did you mean:
 Command 'fpm2' from package 'fpm2' (universe)
fpm*: command not found


So I guess is not installed.. It is safe to install it on my VPS that has already 18 websites running with Apache2?

Thank you!

---

### Post by samiux on 2012-12-06
> **matimont said:**
> I ran the command and I get this:

No command 'fpm*' found, did you mean:
 Command 'fpm2' from package 'fpm2' (universe)
fpm*: command not found


So I guess is not installed.. It is safe to install it on my VPS that has already 18 websites running with Apache2?

Thank you!

The command should be the following :

```
dpkg -l php5-fpm
```

Samiux

---

### Post by matimont on 2012-12-06
When I run the command above I get this:

**> dpkg -l php5-fpm** 
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
||/ Name                             Version                                 Description
+++-================================-=======================================-================================================================================================================= 
un  php5-fpm                         <none>                                  (no description available)

---

### Post by samiux on 2012-12-06
> **matimont said:**
> When I run the command above I get this:

**> dpkg -l php5-fpm** 
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
||/ Name                             Version                                 Description
+++-================================-=======================================-================================================================================================================= 
un  php5-fpm                         <none>                                  (no description available)

That means the php5-fpm is not installed in your system.

Samiux

---

### Post by matimont on 2012-12-06
So it is safe to install now?

I have 18 sites running under /home..

Thanks!

---

### Post by samiux on 2012-12-06
> **matimont said:**
> So it is safe to install now?

I have 18 sites running under /home..

Thanks!

It is safe to install it but to make it works is another question.

Samiux

---

### Post by matimont on 2012-12-06
Thanks,

I think I will leave it as it is, I just needed to make newrelic.com recognize my 18 sites in their monitoring dashboard.

---

### Post by samiux on 2012-12-06
> **matimont said:**
> Thanks,

I think I will leave it as it is, I just needed to make newrelic.com recognize my 18 sites in their monitoring dashboard.

php5-fpm is a kind of fastcgi or alike.  Make sure you need it or not.

Samiux

---

