---
title: "Could someone test this script? For sever configuration"
date: 2006-07-22
forum: Server Platforms
---

### Post by danf_1979 on 2006-07-22
[Dont test this, is full of bugs]

Hi, I'm developing a python script based on the Perfect Ubuntu 6.06 setup. Could someone beta/alpha test this?
Till now the script installs and configures:
-------------------
1: MySQL5 with utf-8 support
2: Apache2 and PHP5
3: Proftpd
-------------------
I'm working on the script right now to complete the Perfect Setup, postfix, courier, etc...

Dont use in production , I have not test it much because I already have a configured server, and my qemu machine doesn't have internet access...

---

### Post by paul.maddox on 2006-07-23
I recently had to do something very similar to this for automating the servers our LAMP developers at work use (we use a very customised build with lots of addin modules). I've found the easiest way to test install scripts like this is to install VMWare and have a virtual server that you can install Ubuntu Server to and test with.

I've attached my script just in case it's of any use to you, although it's bash and not python.

---

