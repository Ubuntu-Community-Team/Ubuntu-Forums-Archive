---
title: "SMART monitoring with Munin fails - &quot;-nan&quot;"
date: 2010-12-30
forum: Server Platforms
---

### Post by oli_ on 2010-12-30
I've been using Munin for quite a while now and after i set up my new homeserver it was one of the first things I installed.
However the smart plugin is giving me trouble.
(This is using Ubuntu 10.04 Server x64)
What I did was:
- install smartmontools
- activated smart for sda and the smartd in /etc/defaults/smartmontools ```
enable_smart="/dev/sda"
start_smartd=yes

```
- ln -s /usr/share/munin/plugins/smart_ /etc/munin/plugins/smart_sda
- in /etc/munin/plugin-conf.d/munin-node: ```
[smart_*]
user root
group disk
env.smartpath /usr/sbin/smartctl

```
- restart munin-node

now smartd is running and i get correct values with smartctl -a /dev/sda - good so far.
Unfortunately, while all other plugins look fine, all the smart graph does is this
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=179690&stc=1&d=1293721077[/IMG]

So I went ahead and did `munin-test smart_sda` only to find out that it reports correct values (and smartctl_exit_status 0 aswell).

What could be the problem?

---

### Post by oli_ on 2010-12-30
Permissions were the problem. Even though i configured the plugin to run as root, it didnt.

---

