---
title: "http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.lzma"
date: 2010-07-19
forum: Server Platforms
---

### Post by tbobker on 2010-07-19
I have a new ubuntu 10 server install on my VPS and I am trying to update it using sudo apt-get update however I am receiving some errors from this file as it does not exist:

[http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.lzma](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.lzma) 

My sources.list file only contains 2 lines:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main universe multiverse

For some reason the server is looking for an obsolete file and I dont know where or why it is trying to do this.

I have activated Ubuntu Fire wall in case this is effecting it in someway.

I was actually trying to install denyhosts and when I tried using sudo apt-get install denyhosts I get this error message:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/d/denyhosts/denyhosts_2.6-6.1ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/d/denyhosts/denyhosts_2.6-6.1ubuntu1_all.deb)  Temporary failure resolving 'us.archive.ubuntu.com'

However, if I enter in the address bar [http://us.archive.ubuntu.com/ubuntu/pool/universe/d/denyhosts/denyhosts_2.6-6.1ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/d/denyhosts/denyhosts_2.6-6.1ubuntu1_all.deb)  the file does exist?

Could someone please advise me?

---

### Post by FuturePilot on 2010-07-19
> Temporary failure resolving 'us.archive.ubuntu.com'
Your DNS is not working or is not set up correctly.

---

### Post by tbobker on 2010-07-20
Ah ok, in my resolv.conf file. Actually I did update this obviously not correct. Thanks I try this.

---

