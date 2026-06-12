---
title: "lxd - can I change containers owner (privacy?)?"
date: 2016-04-28
forum: Virtualisation
---

### Post by Ze Ha on 2016-04-28
I'd like to use lxd on Ubuntu 16.04, but as I see, every user who can  create containers, can connect to any other containers. I'd like to  prohibit this.
  For example, I have two users l1 and l2 both in group lxd If user l1 creates a container:

  ```
lxc launch ubuntu:16.04 ub1

```

 then user l2 can connect to it:

  ```
lxc exec ub1 bash

```  Is there any way to prevent this and separate these containers user  by user, without using tools other than lxc, which came with lxd,  lxd-client?
Or is it a stupid question? (This is the 5th forum, where I ask it, but still no answer)

---

### Post by MAFoElffen on 2016-04-30
hmmm, you are referring to if a user has superuser permissions they can start and priviledged container... then yes. On unpriviledged, then no, by user. 

But what you describe is container management and access to it's console through the hypervisor.. A user does not have to have hypervisor rights to have access to a container. Just as a user does not have to have server admin rights to be a normal user with access to network domain, local machine access or remote machine access.

There is a difference in creating a template, starting a container, managing the environment of a container... <versus> having access to that container as a user. That is just like if it was a server or any other machine on a network, Remote access rights are different that remote management rights. If you create users and groups in that "machine." If you want users to have remote access to a container, then think of that running container just like it was a VM or a remote physical node. The communications to and from would be the same. Why is Docker, LXC/LXD, nspawn and chroots included in the Virtualisation Section here, because that is what they are. ...and while running, they are a virtualized machine. User's just need rights (as a user in PAM) to have access rights and privileges. They gain access through verifying their credentials, via the methods allowed by the system.

So yes, you can create users and groups to a privileged container that a user can log into... but does not have any admin rights to that container. They would have the normal kind of user rights.

Scale with this is immaterial: This might be a machine that encapsulates all within itself, with it's virtual networking -or- An Enterprise infrastructure spread out across the world... The concepts are the same.

From an Enterprise or Network perspective: The view of virtualization from the perspective of a normal user, is that what it actual is (whether that system is on-metal or virtualized) should be transparent to the end user. (It's providing them with the services they need.) They should not be able to tell if the remote machine they are connecting to is physical or not.)

Does that make sense? Or am I misunderstanding your question?

---

### Post by Ze Ha on 2016-04-30
I apologize, if I misunderstand something, I'm not a native English (as you could see ;) )

Lxd client can create unprivileged containers by default. It is what I want to do. (and I don't want to manage lxd or the containers from a remote machine etc. I'm building a small home server for two users :) )

But... I thought, if a non-root user creates a container using command lxc (which is in the package lxd-client), the created container will be protected from other users (except the root, and perhaps lxd) or I can protect them later. I afraid, it was a big mistake. Instead of this, any containers created via lxd client, are accessible and manageable by all users which are in the group lxd, because they are the administrators of the hypervisor and the containers are belong to hypervisor, not to users.
So, if I want to separate them per user basis, then I need to use the original lxc in lxc1 package.
Am I right? Or...

---

### Post by MAFoElffen on 2016-05-01
Not really... That specific user can only create, start, access, thier own un-privileged templates and containers. (Except Root) Reason for this is that un-privileged creates ib their own Home directory. So they are the owner of what is in their home. Another user does not have access to someone else's Home directory.

If you wanted to do a shared, then create to a share directory, then change ownership to "nobody" and/or to a lxd type of group that you create for shared use of shared unprivileged containers.

---

### Post by Ze Ha on 2016-05-01
Are you sure? Are you talking about lxd's client in Ubuntu 16.04?
Just because...

On a freshly installed Ubuntu 16.04, I initialized lxd, and added two new users, and added them to group lxd:
```
root@ubuntu16:~# lxd init --storage-backend dir --auto
LXD has been successfully configured.
root@ubuntu16:~# adduser l1
Adding user `l1' ...
Adding new group `l1' (1001) ...
Adding new user `l1' (1001) with group `l1' ...
Creating home directory `/home/l1' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for l1
Enter the new value, or press ENTER for the default
        Full Name []:
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [Y/n]
root@ubuntu16:~# usermod -G lxd -a l1
root@ubuntu16:~# adduser l2
Adding user `l2' ...
Adding new group `l2' (1002) ...
Adding new user `l2' (1002) with group `l2' ...
Creating home directory `/home/l2' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for l2
Enter the new value, or press ENTER for the default
        Full Name []:
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [Y/n]
root@ubuntu16:~# usermod -G lxd -a l2

```

Then I logged in as the first user (l1), created a new container (ub1) and started it:
```
l1@ubuntu16:~$ lxc launch ubuntu:16.04 ub1
Generating a client certificate. This may take a minute...
If this is your first time using LXD, you should also run: sudo lxd init

Creating ub1
Retrieving image: 100%
Starting ub1
l1@ubuntu16:~$ lxc list
+------+---------+------+------+------------+-----------+
| NAME |  STATE  | IPV4 | IPV6 |    TYPE    | SNAPSHOTS |
+------+---------+------+------+------------+-----------+
| ub1  | RUNNING |      |      | PERSISTENT | 0         |
+------+---------+------+------+------------+-----------+
l1@ubuntu16:~$ lxc exec ub1 bash
root@ub1:~# ls -l
total 0

```

After this, I opened a new terminal session with the second user (l2) and tried to use the container (ub1) created by l1:
```
l2@ubuntu16:~$ lxc list
Generating a client certificate. This may take a minute...
If this is your first time using LXD, you should also run: sudo lxd init

+------+---------+------+------+------------+-----------+
| NAME |  STATE  | IPV4 | IPV6 |    TYPE    | SNAPSHOTS |
+------+---------+------+------+------------+-----------+
| ub1  | RUNNING |      |      | PERSISTENT | 0         |
+------+---------+------+------+------------+-----------+
l2@ubuntu16:~$ lxc exec ub1 bash
root@ub1:~# ps
  PID TTY          TIME CMD
  261 ?        00:00:00 bash
  271 ?        00:00:00 ps
root@ub1:~# ls
root@ub1:~# touch l2.txt
root@ub1:~# ls -l
total 0
-rw-r--r-- 1 root root 0 May  1 09:07 l2.txt
root@ub1:~# exit
l2@ubuntu16:~$

```

After the above, I switched back to l1's session and checked if the file l2.txt in the home of container's root is visible, accessible etc. :
```
l1@ubuntu16:~$ lxc exec ub1 bash
root@ub1:~# ls -l
total 0
-rw-r--r-- 1 root root 0 May  1 09:07 l2.txt
root@ub1:~#

```

Though I expected, ub1 container will be accessible only for l1 (and perhaps root and lxd).
If I leave out lxd (exactly: lxd-client binary, called lxc) and use the original lxc, then it works as I want. Unprivileged containers created by l1 (lxc-create -t download ...) will be accessible by others, only via network, but not directly (lxc-attach etc.)

---

### Post by MAFoElffen on 2016-05-01
You set the users to goup "lxd," where the group permissions had permissions to have access to privileged containers. Those are shared by the group. Being shared, yes they are shared with members of that group and using group permissions.

Remember that I was talking about un-privileged user containers... un-privileged are local / private. Apples and oranges.

It would be the same if we were not talking lxd (rwx), but rather to files in a network directory share. If 2 users are in the same group, and that group has read/write rights to that directory, then both users can read/write to the files within that directory. Right?

---

### Post by Ze Ha on 2016-05-01
Actually I don't understand you...
The command lxc works only for members of group lxd. If I create a user which is not member of lxd, then:
```
root@minipc:~# adduser l3
Adding user `l3' ...
Adding new group `l3' (1003) ...
Adding new user `l3' (1003) with group `l3' ...
Creating home directory `/home/l3' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for l3
Enter the new value, or press ENTER for the default
        Full Name []:
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [Y/n]
root@minipc:~# su - l3
l3@minipc:~$ id
uid=1003(l3) gid=1003(l3) groups=1003(l3)
l3@minipc:~$ lxc list
Generating a client certificate. This may take a minute...
If this is your first time using LXD, you should also run: sudo lxd init

error: Get [http://unix.socket/1.0:](http://unix.socket/1.0:) dial unix /var/lib/lxd/unix.socket: connect: permission denied
l3@minipc:~$ lxc launch ubuntu:16.04 mycont
error: Get [http://unix.socket/1.0:](http://unix.socket/1.0:) dial unix /var/lib/lxd/unix.socket: connect: permission denied
```

But the container, created by user l1 is an unprivileged container (IMHO):
```
l3@minipc:~$ ps -eO "%u %U %g %G" | grep init
    1 root     root     root     root     S ?        00:00:04 /sbin/init
 1706 100000   100000   100000   100000   S ?        00:00:00 /sbin/init

```
Pid 1706 is the container's init process. Inside the container it looks as 0/0 uid/gid.
Earlier I've tried lxc (without lxd) on Debian Jessie, and I can't use unprivileged containers on it, but I can privileged ones. They were run under uid 0 and gid 0 without uid and gid mappings. I think, unprivileged container = runs under non-root uid and gid as you can see above.

Do I think or do something wrong? I missed something out, when I've read the documentation?
(only the default packages were installed on this server: lxd and lxd-client, without lxc* packages)

---

### Post by Jan07 on 2016-10-25
> **MAFoElffen said:**
> Not really... That specific user can only create, start, access, thier own un-privileged templates and containers. (Except Root) Reason for this is that un-privileged creates ib their own Home directory. So they are the owner of what is in their home. Another user does not have access to someone else's Home directory.

If you wanted to do a shared, then create to a share directory, then change ownership to "nobody" and/or to a lxd type of group that you create for shared use of shared unprivileged containers.

This is only a solution for LX**C **containers. But the question is the access management for LX**D** containers. 

AFAIK there is no way to way to create unprivileged containers with LXD, because to use the LXD interface you have to be in the LXD group -- and then you automatically gain rights to access the container files (because they are created with permissions for this group).
I am searching for the same solution to control the access to this containers in the same way as described here, but i think there is no way to control the access to the containers. If you have access to one container you have also the rights to access all other containers.

So maybe the only solution is allowing the container-users to connect to the host via SSH and then connect to the container. Therefore every container-admin (and user) needs an user account on your host system, but must not be in the lxd group. So to control the container (in a way like creating snapshots or stop the container stateful) there has to be a different user, a container root who as access to all the containers.

---

