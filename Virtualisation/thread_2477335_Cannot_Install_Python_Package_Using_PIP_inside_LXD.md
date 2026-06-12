---
title: "Cannot Install Python Package Using PIP inside LXD or LXC, permission denied"
date: 2022-07-22
forum: Virtualisation
---

### Post by ckusumadewa2 on 2022-07-22
Hi Everyone.

I have installed LXD or LXC on Ubuntu 22.04. Then, I created an Ubuntu 18.04 container and then named it ros-melodic.

```
ckusumadewa@vector:~$ lxc list
+-------------+---------+------+------+-----------+-----------+
|    NAME     |  STATE  | IPV4 | IPV6 |   TYPE    | SNAPSHOTS |
+-------------+---------+------+------+-----------+-----------+
| ros-melodic | STOPPED |      |      | CONTAINER | 0         |
+-------------+---------+------+------+-----------+-----------+
```

Then, I can start the 'ros-melodic' container and login as the 'ubuntu' user as follows:

```
ckusumadewa@vector:~$ lxc start ros-melodic
ckusumadewa@vector:~$ lxc ubuntu ros-melodic
ubuntu@ros-melodic:~$
```

However, inside ros-melodic, I cannot install any python packages using pip, even when I add --user option. I got the following error:

```
ubuntu@ros-melodic:~$ pip install --upgrade --user pip

OSError: [Errno 13] Permission denied: '/home/ubuntu/.local/lib'

ubuntu@ros-melodic:~$ pip install --user scikit-learn

OSError: [Errno 13] Permission denied: '/home/ubuntu/.local/lib'
```

What should I do to solve this problem. Any helps will be apreciated. Thank you.



Chandra

---

### Post by The Cog on 2022-07-22
Try using sudo to gain root privileges:
```
sudo pip install --user scikit-learn
```
I could be wrong - not familiar with pip, but it's worth a try.

---

### Post by MAFoElffen on 2022-07-22
Reference: [https://scikit-learn.org/0.16/install.html](https://scikit-learn.org/0.16/install.html)
```

pip install --user --install-option="--prefix=" -U scikit-learn 

```

---

### Post by DuckHook on 2022-07-23
Try logging in using the following syntax:```
lxc exec ros-melodic -- sudo --user ubuntu --login
```
LXD is finicky and you may need to set sudoers properly for the session.

---

### Post by ckusumadewa2 on 2022-07-25
Dear All,

Thank you very much for your help. Especially for DuckHook, I finally can install the pip package **outside the LXD or LXC container** using the following syntax:

```
ckusumadewa@vector:~$ lxc exec ros-melodic -- pip install --user scikit-learn
```

By the way, how to mark this thread as [SOLVED]? I am new to this forum. Sorry.


Regards,

Chandra

---

### Post by DuckHook on 2022-07-26
Glad you found the solution. I should have mentioned that you can indeed install a package from outside lxd using lxc exec.

You can mark a thread "solved" using thread tools at the top of the first post in the thread. I have already done so for you.

Good luck and Happy Ubuntu-ing.

---

