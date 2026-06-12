---
title: "Auditd issues"
date: 2017-12-20
forum: Security
---

### Post by mark.constant on 2017-12-20
In my audit.rules file I have entered what is below

-w /usr/bin/docker -k docker
-w /var/lib/docker -k docker
-w /etc/docker -k docker
-w /usr/lib/systemd/system/docker.service -k docker
-w /usr/lib/systemd/system/docker.socket -k docker
-w /etc/default/docker -k docker
-w /etc/docker/daemon.json -k docker
-w /usr/bin/docker-containerd -k docker
-w /usr/bin/docker-runc -k docker
-w /var/log/faillog -p wa -k logins
-w /var/log/lastlog -p wa -k logins
-w /var/log/tallylog -p wa -k logins
-e 2

Even after reboot all I get is
sudo auditctl -l
-w /usr/bin/docker -p rwxa -k docker
-w /var/lib/docker/ -p rwxa -k docker
-w /etc/docker/ -p rwxa -k docker

Then I try something like
systemctl restart auditd and then the output changes to
-w /usr/bin/docker -p rwxa -k docker
-w /var/lib/docker/ -p rwxa -k docker
-w /etc/default/docker -p rwxa -k docker
-w /etc/docker/daemon.json -p rwxa -k docker
-w /usr/bin/docker-containerd -p rwxa -k docker
-w /usr/bin/docker-runc -p rwxa -k docker
-w /var/log/faillog -p wa -k logins
-w /var/log/lastlog -p wa -k logins
-w /var/log/tallylog -p wa -k logins

Any reason for the inconsistent behavior of auditd?

---

