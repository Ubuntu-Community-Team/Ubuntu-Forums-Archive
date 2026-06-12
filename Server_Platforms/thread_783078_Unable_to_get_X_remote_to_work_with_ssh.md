---
title: "Unable to get X remote to work with ssh"
date: 2008-05-05
forum: Server Platforms
---

### Post by jbjoret on 2008-05-05
Hi,

I am trying to use xclock to work remotely, I am using 6.06LTS Server and connect over ssh with:

ssh -X [email]myname@myserver.com[/email]

I can start xclock, but  it returns with:

Error: Can't open display: localhost:10.0

My sshd_config file does contain "X11Forwarding yes", I am using my client to connect on other redhat/suse install and there is no issue with them, so I guess I am missing something on my 6.06LTS server.

---

### Post by bluefrog on 2008-05-05
try ssh -Y

and/or
export DISPLAY=:0.0
xhost +localhost

---

### Post by jbjoret on 2008-05-05
Thanx, I tried both solutions, seperatly and together. It won't change a thing. I just tried with a second laptop same thing. It has to be the server. But what else could be missing  ?

---

### Post by DA_uf on 2008-07-03
Check out [http://ubuntuforums.org/showthread.php?t=847643](http://ubuntuforums.org/showthread.php?t=847643) in the [RESOLVED] area.

---

