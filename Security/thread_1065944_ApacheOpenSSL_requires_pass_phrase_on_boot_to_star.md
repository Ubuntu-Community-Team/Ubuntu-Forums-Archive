---
title: "Apache/OpenSSL requires pass phrase on boot to start and I'd like to automate it."
date: 2009-02-10
forum: Security
---

### Post by sand0z on 2009-02-10
I installed Apache2 and OpenSSL on Ubuntu server 8.10 using the instructions in this link:

[http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/](http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/)

Everything works just fine but when the system reboots, the server does not start and the local console displays:

Apache/2.2.9 mod_ssl/2.2.9 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide the pass phrases.

Entering the pass phrases allows the boot process to continue and Apache starts.

This is fine if someone is there to enter the pass phrase, but if the server goes down unattended I'm hosed until I get to the console. I tried to recreate the keys using the same instructions, but a pass phrase is mandatory (no surprise) and trying to undo the pass phrase encryption by editing and renaming the files mentioned in the article didn't help. I restored my changes, created a new key and it's back up and working.

The question is 1) how can I bypass the need for console action, 2) set up an unencrypted key that won't prompt me, 3) control the process through an SSH session that I can establish at that point?

While I can live with what I have, the occasional power outage creates a problem (yes, I have a UPS). I'd really appreciate any solutions I can use. My knowledge level at this time is that I can follow instructions from articles, but I'm still low on the learning curve in being able to troubleshoot problems like this. Thanks in advance.

Sand0z

---

### Post by cdenley on 2009-02-10
I think if you leave the passphrase blank, then it will not be password-protected, if I remember correctly. I believe there is also a command to remove a password.
[http://www.insivia.com/performance/ideas/removing-a-pass-phrase-from-a-ssl-certificate](http://www.insivia.com/performance/ideas/removing-a-pass-phrase-from-a-ssl-certificate)

I believe you can start apache from ssh with a simple "/etc/init.d/apache2 start", but you would need to either kill the apache process already running on the local console, or disable it from starting at boot.

I think having your key password protected prevents an attacker who retrieves your key from spoofing your server (unless they guess your password).

---

### Post by bodhi.zazen on 2009-02-10
> **sand0z said:**
> I installed Apache2 and OpenSSL on Ubuntu server 8.10 using the instructions in this link:

[http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/](http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/)

Everything works just fine but when the system reboots, the server does not start and the local console displays:

Apache/2.2.9 mod_ssl/2.2.9 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide the pass phrases.

Entering the pass phrases allows the boot process to continue and Apache starts.

This is fine if someone is there to enter the pass phrase, but if the server goes down unattended I'm hosed until I get to the console. I tried to recreate the keys using the same instructions, but a pass phrase is mandatory (no surprise) and trying to undo the pass phrase encryption by editing and renaming the files mentioned in the article didn't help. I restored my changes, created a new key and it's back up and working.

The question is 1) how can I bypass the need for console action, 2) set up an unencrypted key that won't prompt me, 3) control the process through an SSH session that I can establish at that point?

While I can live with what I have, the occasional power outage creates a problem (yes, I have a UPS). I'd really appreciate any solutions I can use. My knowledge level at this time is that I can follow instructions from articles, but I'm still low on the learning curve in being able to troubleshoot problems like this. Thanks in advance.

Sand0z

You make a .pem file.

Sorry I can not give you exact directions at the moment, try google on how to ssl .pem file

---

### Post by sand0z on 2009-02-10
Thanks for the replies. I'll take a look at all the options you gave me and see what I turn up. I saw a similar thread from some time back but none of the solutions offered worked for me. A lot of this security stuff is way over my head, but I need to understand it.

---

### Post by bodhi.zazen on 2009-02-10
> **sand0z said:**
> Thanks for the replies. I'll take a look at all the options you gave me and see what I turn up. I saw a similar thread from some time back but none of the solutions offered worked for me. A lot of this security stuff is way over my head, but I need to understand it.

I found the link I was referring to 

[http://www.xenocafe.com/tutorials/linux/centos/openssl/self_signed_certificates/index.php](http://www.xenocafe.com/tutorials/linux/centos/openssl/self_signed_certificates/index.php)

Scroll down to the "Remove the PassPhrase From Your Private Key" section

---

