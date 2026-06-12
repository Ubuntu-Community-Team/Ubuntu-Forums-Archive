---
title: "webmin iptables rules NOT the same as system rules."
date: 2014-03-05
forum: Server Platforms
---

### Post by cylent on 2014-03-05
this is very very very frustrating.

i am trying to use webmin to manage my linux firewall (iptables rules).

however if i dare enter a rule in via the CLI (CommandLineInterface - ssh) it will NOT update in webmin.

So i edited the module config for webmin to say:

[TABLE="width: 100%"]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, width: 30%, align: right"]**IPtables save file to edit**[/TD]
[TD="class: ui_form_value, colspan: 1"] Use operating system or Webmin default  /etc/iptables/rules.v4

[/TD]
[/TR]
[/TABLE]
that seemed to have work for a minute. i rebooted to test and guess what? now my rules.v4 file is junked with a version of what appears to be default.

What gives?

---

### Post by guptesh on 2014-03-05
You could add a line to /etc/rc.local like :

iptables-restore < /path/to/iptables/save-file

The location of the same file depends on your Linux distro - it might
be at /etc/sysconfig/iptables or /etc/webmin/firewall/iptables.save

---

### Post by cylent on 2014-03-05
well according to the /etc/webmin/firewall/config file its pointing to the right file.

```
root@ak-us:/etc/webmin/firewall# cat configforce_init=0
comment_mod=0
direct=1
view_condition=1
view_comment=1
cluster_mode=0
save_file=/etc/iptables/rules.v4
before_cmd=
before_apply_cmd=
after_apply_cmd=
after_cmd=



```

---

### Post by guptesh on 2014-03-05
chk for updates or try reinstalling webmin for quick fix...!!!

---

### Post by cylent on 2014-03-05
thanks.

that's a rather frustrating method and no one would want to edit iptables rules by hand.

still.. i have to keep backing up my rules JUST incase my server reboots.

very frustrating.

---

### Post by Lars Noodén on 2014-03-05
Can webmin be set to work with [UFW](https://help.ubuntu.com/community/UFW)?  That would manipulate iptables indirectly but one way to allow your changes to persist across reboots.

---

