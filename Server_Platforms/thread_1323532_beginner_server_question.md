---
title: "beginner server question"
date: 2009-11-11
forum: Server Platforms
---

### Post by aikiko on 2009-11-11
Hello,

I have a little Thin Client (Via x86CPU 800MHz/128MBRam/4GB USB flash drive) where i have a Ubuntu 9.10 server installed. I nearly have no knowledge of php/mysql. 
What I want is to execute some commands via a webinterface. I have Lamp installed, and the apache and php are running fine. All this is more educational for me than real stuff, so please to not advise me to install a webinterface that have all the things already done.

An example of what I would like to do is :
<?php echo exec('sudo ufw status'); ?>
This is not secure at all and i know it ( actually it doesn't really matter if it is secure at all because it is in a local network, but it is always better to do it in a secure way).

So how to i execute command that require root privileges from php ? (please be as explicit as possible, what privilege to set)

---

