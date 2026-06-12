---
title: "Setting up pure-ftpd but getting an error after using the &quot;pure-pw useradd&quot; command"
date: 2023-06-06
forum: Server Platforms
---

### Post by husker12 on 2023-06-06
[COLOR=#000000]This is the script I'm following though I'm entering in the commands individually, one by one:[/COLOR]

[COLOR=#000000]Code:
groupadd ftpgroup
useradd -g ftpgroup -d /dev/null -s /usr/sbin/nologin ftpuser
pure-pw useradd husker -u ftpuser -d /ftphome
pure-pw mkdb
cd /etc/pure-ftpd/auth/ 
ln -s ../conf/PureDB 60pdb
mkdir -p /ftphome
chown -R ftpuser:ftpgroup /ftphome/
systemctl restart pure-ftpd[/COLOR]
[COLOR=#000000]This is the problematic command:[/COLOR]

[COLOR=#000000]Code:
pure-pw useradd husker -u ftpuser -d /ftphome[/COLOR]
[COLOR=#000000]It causes the following error to appear:[/COLOR]

[COLOR=#000000]Code:
Password: 
Enter it again: 
Error.
Check that [husker] doesn't already exist,
and that [/etc/pure-ftpd/pureftpd.passwd.tmp] can be written.[/COLOR]
[COLOR=#000000]I know for sure that neither the username husker nor the file pureftpd.passwd.tmp exist.[/COLOR]

[COLOR=#000000]How do I resolve this issue?[/COLOR]

---

### Post by coffeecat on 2023-06-07
Duplicate [here](https://ubuntuforums.org/showthread.php?t=2487495). Thread closed.

---

