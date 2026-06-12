---
title: "securing owncloud"
date: 2014-10-02
forum: Security
---

### Post by grier-devon on 2014-10-02
So I setup owncloud in a digitalocean droplet with Ubuntu 14.04 server. I have it set to work on a few of my computers and the wifes but now I am knowing that I need to lock down some security but I am unsure of how to do some of these things or worried it might mess somethings up.

1. I would imagine it would be smart to encrypt the owncloud folder as that is where pictures, documents and other stuff. If I encrypt the folder will everything still sync okay to my devices? What is the best encryption method?

2. when I setup my computer to link to the my owncloud I tried to connect using "https" but it wouldn't let me and said I needed to use "http" and it is not a secure connection. How can I setup a secure connection between my devices and my owncloud? 

Thanks.

---

### Post by sandyd on 2014-10-02
> **grier-devon said:**
> So I setup owncloud in a digitalocean droplet with Ubuntu 14.04 server. I have it set to work on a few of my computers and the wifes but now I am knowing that I need to lock down some security but I am unsure of how to do some of these things or worried it might mess somethings up.

1. I would imagine it would be smart to encrypt the owncloud folder as that is where pictures, documents and other stuff. If I encrypt the folder will everything still sync okay to my devices? What is the best encryption method?

2. when I setup my computer to link to the my owncloud I tried to connect using "https" but it wouldn't let me and said I needed to use "http" and it is not a secure connection. How can I setup a secure connection between my devices and my owncloud? 

Thanks.

2. You need to generate a SSL Certificate and Key for your (sub)domain. It would be best if you got it from a certified authority, but self-signed OpenSSL Certificates work fine too.
Depending on what webserver you are using, you can enable SSL with the instructions at [http://doc.owncloud.org/server/7.0/admin_manual/installation/installation_source.html#apache-web-server-configuration](http://doc.owncloud.org/server/7.0/admin_manual/installation/installation_source.html#apache-web-server-configuration)

---

