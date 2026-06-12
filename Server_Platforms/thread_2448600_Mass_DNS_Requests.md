---
title: "Mass DNS Requests"
date: 2020-08-10
forum: Server Platforms
---

### Post by jacobokanta on 2020-08-10
I run a PiHole dns server, I keep seeing mass dns requests for the domain mariadb from my Ubuntu Server. About 50,000 a day, 3 A and 3 AAAA every 10 seconds. I can't seem to find a way to identify the program that is sending them. I've tried setting the entry manually to a non existant ip in /etc/hosts and that stopped the requests for a while but then they came back and there was still no way to identify what program was sending them. Looking for a way to identify the program doing this. I've checked configs and temporarily stopped almost every program I can think of and the requests have continued.

---

### Post by slickymaster on 2020-08-10
Thread moved to **Server Platforms** for a better fix

---

### Post by jacobokanta on 2020-08-17
Solved with some help from the askubuntu forums [https://askubuntu.com/questions/1267549/mass-dns-requests-from-an-unknown-program-how-to-identify](https://askubuntu.com/questions/1267549/mass-dns-requests-from-an-unknown-program-how-to-identify) turned out to be a stray docker container.

---

