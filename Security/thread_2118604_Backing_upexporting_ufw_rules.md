---
title: "Backing up/exporting ufw rules"
date: 2013-02-21
forum: Security
---

### Post by cogset on 2013-02-21
Hi there,I'd like to get advice about the best way to export ufw rules from one installation to another,according to this bug report [https://bugs.launchpad.net/ufw/+bug/916961/comments/1](https://bugs.launchpad.net/ufw/+bug/916961/comments/1)
this would be copying /lib/ufw , /etc/ufw and /etc/default/ufw .
I've done this and it works - well sort of...
Rules are working in the new installation,but I have to disable logging or it will throw errors when activating the firewall,with logging disabled everything is OK,I can enable/disable/reload the firewall at will,not so with logging on:any ideas on what may cause this issue with logging ?
Also,are there other ways to backup/export these firewall rules ?

---

### Post by wildmanne39 on 2013-02-21
*Thread moved to **Security Discussions**.*

---

