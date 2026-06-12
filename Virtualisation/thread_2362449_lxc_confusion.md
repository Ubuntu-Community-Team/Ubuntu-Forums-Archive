---
title: "lxc confusion"
date: 2017-05-28
forum: Virtualisation
---

### Post by scojopa on 2017-05-28
can someone help me figure this out:

sudo lxc-ls -f
my_container STOPPED

sudo lxc list
my_container RUNNING

so I stop my_container
I delete it

sudo lxc list
no container

sudo lxc-ls -f
my_container STOPPED


sudo find / -type d -name my_container
/var/lib/lxc/my_container
/var/log/lxd/my_container


I understand the commands lcx-ls (pre LXD) vs lcx list (LXD/LXC) but why is the container listed at stopped and not deleted?

---

### Post by KillerKelvUK on 2017-05-29
So I'm still learning myself but commands using lxc-xxx I believe use LXC 1.0 which has a different storage backend to LXD which uses a command of lxc only (for the most).  Do you have two directories one, /var/lib/lxc/ and one /var/lib/lxd?  If so is it possible you created a container with the same name using both commands?

---

### Post by scojopa on 2017-06-01
yes
thanks I am opening a new thread I cannot get it to work correctly.

---

