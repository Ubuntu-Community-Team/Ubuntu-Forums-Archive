---
title: "boxy output when using pstree remotely"
date: 2012-07-20
forum: Server Platforms
---

### Post by Habitual on 2012-07-20
the dreaded boxes shows up (non-printable ASCII?) when I type pstree on a remote Ubuntu 12.04 LTS host.

For now I have set
```
alias pstree="pstree -G" 
```and I don't have the issue when I use host aliases remotely like so,
```
db1 pstree
``` where "db1" is 
```
alias db1='ssh -qi /path/to/some/keyfile  root@xx.xx.121.73'
```

pstree (PSmisc) 22.15 on the server.
Xfce Terminal Emulator v.0.4.6

I'd like to fix this since it affects htop's Tree mode and the alias did nothing for that.

Thanks.

---

### Post by Habitual on 2012-07-22
edited my local /etc/profile.d/lang.sh and changed
from
```
export LANG=en_US
```to
```
export LANG=en_US.UTF-8
```log*out|in*.

Done.

Credit to [tty13]("http://www.linuxquestions.org/questions/slackware-14/terminal-fonts-are-messed-up-4175417996/#post4735080") over at linuxquestions.org / [Slackware forum]("http://www.linuxquestions.org/questions/slackware-14/")

---

