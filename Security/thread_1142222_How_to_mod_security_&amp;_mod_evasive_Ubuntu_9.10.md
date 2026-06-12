---
title: "How to mod_security &amp; mod_evasive Ubuntu 9.10"
date: 2009-04-29
forum: Security
---

### Post by bodhi.zazen on 2009-04-29
[mod_security]("http://www.modsecurity.org/") and [mod_evasive]("http://www.zdziarski.com/projects/mod_evasive/") are Apache Modules targeted at increasing Apache Security and are sometimes thought of as "application firewalls".

mod_security is designed to screen out bad url requests (such as /etc/shadow) , mysql injection, etc.

mod_evasive is designed to mitigate DOS and brute force attacks.

Both modules were somewhat difficult to implement in the past, but are much easier in Ubuntu 9.04.

I wrote a pair of blogs reviewing the installation :

[How to mod_evasive]("http://blog.bodhizazen.net/linux/how-to-mod_evasive-ubuntu-904/")

[How to mod_security]("http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/")

:popcorn:

---

### Post by kevdog on 2009-04-30
Thanks! :)

---

### Post by ackbarr on 2009-05-14
Awesome set of tutorials! Thanks for sharing.

---

### Post by drubin on 2009-05-16
Although I agree using this code for 3rd party code that you install and in general all code you put on your server.

This being said it is no excuse for bad coding to allow such requests! All script/applications that sit in a webserver should never even allow such absolute pathing and should allow serve up requests relevant to the current running website. 

Please do not think that having these mods enabled allow for bad security on a users part. 

(Great tuts on how to set them up, thanks bodhi)

---

### Post by samiux on 2009-05-26
For the modsecurity, the package that provided by Ubuntu 9.04 has DOS flaw.  The up-to-date version of modsecurity is 2.5.9.  You can download the deb packages at the official site of modsecurity ([http://www.modsecurity.org/download/index.html]("http://www.modsecurity.org/download/index.html")).

The download site is [http://etc.inittab.org/~agi/debian/libapache-mod-security2/]("http://etc.inittab.org/~agi/debian/libapache-mod-security2/") 

_**Download the packages**_
> wget [http://etc.inittab.org/~agi/debian/libapache-mod-security2/mod-security-common_2.5.9-1_all.deb]("http://etc.inittab.org/~agi/debian/libapache-mod-security2/mod-security-common_2.5.9-1_all.deb")

_For 32-bit system :_
> wget [http://etc.inittab.org/~agi/debian/libapache-mod-security2/libapache-mod-security_2.5.9-1_i386.deb](http://etc.inittab.org/~agi/debian/libapache-mod-security2/libapache-mod-security_2.5.9-1_i386.deb)

_For 64-bit system :_
> wget [http://etc.inittab.org/~agi/debian/libapache-mod-security2/libapache-mod-security_2.5.9-1_amd64.deb](http://etc.inittab.org/~agi/debian/libapache-mod-security2/libapache-mod-security_2.5.9-1_amd64.deb)

_**Installation**_
_For 32-bit system :_
> sudo dpkg -i mod-security-common_2.5.9-1_all.deb libapache-mod-security_2.5.9-1_i386.deb

_For 64-bit system :_
> sudo dpkg -i mod-security-common_2.5.9-1_all.deb libapache-mod-security_2.5.9-1_amd64.deb

That's all!

---

### Post by buldozerceto on 2009-06-21
I read somewhere that mod security could affect much the server performance. Is it worth installing?

---

### Post by joycejohnson on 2009-09-24
anyone tried this on an intel x64 platform yet?

---

### Post by bodhi.zazen on 2009-09-24
> **joycejohnson said:**
> anyone tried this on an intel x64 platform yet?

I have run it on a 64 bit platform

---

### Post by im_an_elf on 2009-11-18
I followed this tutorial in a round about way and got to the application of the mod_security configuration rules and I get multiple errors.

Do I need to disable the mod before applying the rules?  In the directed tutorial on the blog the insecure file still produces the same information although my server says the mod was installed.  Is there any way to test further?  The dpkg seemed to work the most error free.

I figured it out.  Apache2.conf had to be reconfigured to allow for additional folders to be considered for the mod_security rules.

---

### Post by Orange Kingdom on 2010-02-14
Doesn't work here with 9.10 -64bit

---

### Post by bodhi.zazen on 2010-02-14
> **Orange Kingdom said:**
> Doesn't work here with 9.10 -64bit

What exactly does not work ?

---

### Post by Orange Kingdom on 2010-02-14
Well, the mod_security is loaded but i get this error in the error_log:

ModSecurity: Unable to retrieve collection

I am trying a rule to block ip's to prevent brute force attempts on ftp/www.

I found something to get rid of the error:
Which means your missing the SecDataDir directive. Run asl -s -f, and check /etc/httpd/modsecurity.d/modsecurity_crs_10_config.conf

for this directive:
SecDataDir /var/asl/data/msa


What does this mean?

---

### Post by bodhi.zazen on 2010-02-14
> **Orange Kingdom said:**
> Well, the mod_security is loaded but i get this error in the error_log:

ModSecurity: Unable to retrieve collection

I am trying a rule to block ip's to prevent brute force attempts on ftp/www.

I found something to get rid of the error:
Which means your missing the SecDataDir directive. Run asl -s -f, and check /etc/httpd/modsecurity.d/modsecurity_crs_10_config.conf

for this directive:
SecDataDir /var/asl/data/msa


What does this mean?

You need to open modsecurity_crs_10_config.conf and make sure it has the line:

(I think the file is in  /etc/apache2/conf.d/modsecurity/ )

SecDataDir /var/asl/data/msa

somewhere in it. 

Also, you may need to make the directory and check permissions.

If all you need to do is block ip from brute forcing, it may be easier to use fail2ban.

---

### Post by Orange Kingdom on 2010-02-14
I did that and the error is gone but
there is no such directory.

Do i have to make this directory?

thanks

---

### Post by bodhi.zazen on 2010-02-14
> **Orange Kingdom said:**
> I did that and the error is gone but
there is no such directory.

Do i have to make this directory?

thanks

Sounds like it =)

And watch the permissions, probably needs to be owned by www-data

---

### Post by Ereipio on 2010-05-30
Hi there i got a problem as i followed your guide.
I have 9.10 installed.

The command 
```
sudo a2enmod mod-security
```
doesnt work for me


In which folder did you mean to type it?

I have tried many but none had accepted it.


Second,
i put in the **modsecurity2.conf** inside **/etc/apache2/conf.d/** folder but when i restarted apache i
got an error about the **/etc/apache2/conf.d/modsecurity/modsecurity_crs_10_config.conf**  for the **SecRuleEngine** at line 53

Thanks for your time
Ereipio

---

