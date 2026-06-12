---
title: "Changing hostname - question"
date: 2006-11-24
forum: Server Platforms
---

### Post by kwambus on 2006-11-24
Hi,

I have a quick question I would like to check out before I perform a hostname change on my server.

I realise so far that to change the "hostname" on Ubuntu I do two things.

1) Edit /etc/hosts to include the new hostname
2) Edit /etc/hostname to refer to my new host name.

I wanted to check whether this is all I need to do? Last time I tried this the change worked but it appeared to break the package manager and "apt-get" seemed to refuse to work after the change. This may be a coincidence but I wanted to check before I went ahead.

On a further note, I wondered how to setup my domain name as my hostname, so instead of "ubuntu" it would be "example.com", how would I refer to this in /etc/hosts? as 127.0.0.1 or its real internet address?

Thank you for your time and understanding, I am still pretty new to Ubuntu but the romance is going strong! ;)

---

### Post by tturrisi on 2006-11-24
> On a further note, I wondered how to setup my domain name as my hostname, so instead of "ubuntu" it would be "example.com", how would I refer to this in /etc/hosts? as 127.0.0.1 or its real internet address?
on my etch system:
hostname = server (which is what is in my /etc/hostname)
domain name = turrisi.org  (which is in my /etc/hosts)

/etc/hosts:
127.0.0.1 localhost server
192.168.1.99 server.turrisi.org server

---

### Post by kwambus on 2006-11-26
Thank you for your reply, nice to have it confirmed. I tried the hostname changes and all seems well with apt-get. Maybe it was a mistake I made on the first attempt.

---

