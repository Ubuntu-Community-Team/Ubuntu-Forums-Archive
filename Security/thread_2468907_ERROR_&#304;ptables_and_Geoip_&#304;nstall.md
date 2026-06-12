---
title: "ERROR &#304;ptables and Geoip &#304;nstall"
date: 2021-11-14
forum: Security
---

### Post by mehmedgurbuz on 2021-11-14
Hi, My server is Ubuntu Server 18.04 and I want to block the entry of some countries from my server using iptables geoip, and I think the most logical solution is to use iptables and geoip, I'm getting a lot of errors when trying it, is there a helpful tool such as an article or installation guide that can help with this?




A few of the Mistakes I Received:
root@myserver:~# iptables -I INPUT -mzip --src-cc CA,US -j DROP
iptables: No chain/target/match by that name.


i have tried xtables-addons versions 2.3,2.13,3.0 they all have the same error but i don't have a problem when i try it on another server there is a problem related to the server but i couldn't solve it

I WROTE THIS ARTICLE USING TRANSLATION THERE MAY BE INCORRECT WORDS SORRY FOR THAT
TR:ÇEV&#304;R&#304; KULLANARAK BU YAZIYI YAZDIM HATALI KEL&#304;MELER OLAB&#304;L&#304;R BUNUN &#304;Ç&#304;N ÜZGÜNÜM

---

