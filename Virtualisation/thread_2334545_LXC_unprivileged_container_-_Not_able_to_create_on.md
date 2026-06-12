---
title: "LXC unprivileged container - Not able to create on Ubuntu 16.04"
date: 2016-08-20
forum: Virtualisation
---

### Post by vijayaragavalu on 2016-08-20
Hello Everyone,

I am new to LXC containers. I started experimenting  LXC containers from  few days on ubuntu 16.04 which is systemd based init system.
i have experimented without much of issue for most of the config in  privilege LXC container. now i just started unprivilage LXC. 
As i dont find exact steps for 16.04 for LXC un priv conatiner creation i just followed below link steps which is for 14.04 LTS

[http://www.cyberciti.biz/faq/how-to-...-ubuntu-linux/]("http://www.cyberciti.biz/faq/how-to-create-unprivileged-linux-containers-on-ubuntu-linux/")


when i do LXC-create i faced below error

 [TABLE="class: cms_table_outer_border, width: 800, align: left"]
[TR]
[TD]vijayusrlxc@test:~$  lxc-create -t busybox -n vijayunpriv
lxc-create: conf.c: chown_mapped_root: 3340 No mapping for container root
lxc-create:  lxccontainer.c: do_bdev_create: 1047 Error chowning   /home/vijayusrlxc/.local/share/lxc/vijayunpriv/rootfs to container root
lxc-create: conf.c: suggest_default_idmap: 4444 You must either run as root, or define uid mappings
lxc-create: conf.c: suggest_default_idmap: 4445 To pass uid mappings to lxc-create, you could create
lxc-create: conf.c: suggest_default_idmap: 4446 ~/.config/lxc/default.conf:
lxc-create: conf.c: suggest_default_idmap: 4447 lxc.include = /etc/lxc/default.conf
lxc-create: conf.c: suggest_default_idmap: 4448 lxc.id_map = u 0 165536 65536
lxc-create: conf.c: suggest_default_idmap: 4449 lxc.id_map = g 0 165536 65536
lxc-create: lxccontainer.c: do_lxcapi_create: 1511 Error creating backing store type (none) for vijayunpriv
lxc-create: lxc_create.c: main: 318 Error creating container vijayunpriv[/TD]
[/TR]
[/TABLE]













Can you please let me know whether i am missing any steps for creating unpriv LXC container 
or please suggest exact steps for creating un-priv LXC on ubuntu 16.04

Kindly note below my environment , please let me know if you need any more information to support me.
(I have also posted same query at [https://ubuntuforums.org/showthread.php?t=2321302](https://ubuntuforums.org/showthread.php?t=2321302))
[TABLE="class: cms_table_outer_border, width: 800, align: left"]
[TR]
[TD]**cat /etc/subgid**
vijayusrlxc@test:~$ cat /etc/subgid
test:100000:65536
test:100000:65536
vijayusrlxc:165536:65536
[B]
/etc/subuid[/B]
vijayusrlxc@test:~$ cat /etc/subuid
test:100000:65536
test:100000:65535
vijayusrlxc:165536:65536

[FONT=arial][B]/etc/network/interfaces
[/B][/FONT]vijayusrlxc@test:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

**default.config**
vijayusrlxc@test:~$ cat ~/.config/lxc/default.config
lxc.network.type = veth
lxc.network.link = lxcbr0
lxc.network.flags = up
lxc.network.hwaddr = 00:16:3e : xx : xx : xx
lxc.id_map=u 0 165536 65536
lxc.id_map=g 0 165536 65536

[B]lxc-checkconfig
[/B]vijayusrlxc@test:~$ lxc-checkconfig
Kernel configuration not found at /proc/config.gz; searching...
Kernel configuration found at /boot/config-4.4.0-34-generic
--- Namespaces ---
Namespaces: enabled
Utsname namespace: enabled
Ipc namespace: enabled
Pid namespace: enabled
User namespace: enabled
Network namespace: enabled
Multiple /dev/pts instances: enabled

--- Control groups ---
Cgroup: enabled
Cgroup clone_children flag: enabled
Cgroup device: enabled
Cgroup sched: enabled
Cgroup cpu account: enabled
Cgroup memory controller: enabled
Cgroup cpuset: enabled

--- Misc ---
Veth pair device: enabled
Macvlan: enabled
Vlan: enabled
Bridges: enabled
Advanced netfilter: enabled
CONFIG_NF_NAT_IPV4: enabled
CONFIG_NF_NAT_IPV6: enabled
CONFIG_IP_NF_TARGET_MASQUERADE: enabled
CONFIG_IP6_NF_TARGET_MASQUERADE: enabled
CONFIG_NETFILTER_XT_TARGET_CHECKSUM: enabled
FUSE (for use with lxcfs): enabled

--- Checkpoint/Restore ---
checkpoint restore: enabled
CONFIG_FHANDLE: enabled
CONFIG_EVENTFD: enabled
CONFIG_EPOLL: enabled
CONFIG_UNIX_DIAG: enabled
CONFIG_INET_DIAG: enabled
CONFIG_PACKET_DIAG: enabled
CONFIG_NETLINK_DIAG: enabled
File capabilities: enabled

Note : Before booting a new kernel, you can check its configuration
usage : CONFIG=/path/to/config /usr/bin/lxc-checkconfig
[/TD]
[/TR]
[/TABLE]

---

### Post by MAFoElffen on 2016-08-23
The link you posted... as DougS suggested, use the Ubuntu Server Guide for reference. There are also 2 wiki pages that go into more detail.

This is 2 points that I see right off from the instructions you linked to.
(1) When you think unprivileged, think of s container that can be used by some user who is not root, nor a member of sudoers/wheel group. Just a normal user. Form that concept, you can go 2 paths.

Path A, you have "a" special UserID, that everyone who wants to use a container, uses that UserID and the corresponding credentials. In this scenario, that one user has access to those specific containers. Some thing thsi si easy to manage. Users have to become that user before they can do anything with that container. I look at that from another perspective, in that now you have a user, that is not a real user, that people alias themselves as... and is now both a security and auditing loophole. Who (really) was the user who did this at that time? IMHO, I think if a user has to become someone else to do something, then they might as well be in the sudoers, using a privileged container, where their own UserID is going to be tracked. (This leads into Path B)

Path B, you have users who can start their own containers or containers in shared storage that they have access to via their own user rights and preventives. By my own preference, this technique for unprivileged containers makes more sense to me.

What you linked to, missed a point which either paths I mentioned would need to work: That to start an unpreviledged contaner, a user needs to have subuid's, subgid's and be able to access to /.local/share/lxc/ after it has switched to the mapped UIDs. What I used to do to run unpreviledged containers with early LXC was 
```

sudo usermod --add-subuids 100000-165536 $USER
sudo usermod --add-subgids 100000-165536 $USER
sudo chmod +x $HOME/.local/share/lxc/

```
You can see in the updated Ubuntu LXC section of the Ubuntu Server Guide ([https://help.ubuntu.com/lts/serverguide/lxc.html](https://help.ubuntu.com/lts/serverguide/lxc.html)), under the section "User Namspaces", that the above has been shortened to just one line:
```

sudo usermod -v 100000-200000 -w 100000-200000 $USER

```
To check that you have done that, please post the results of
```

grep $USER /etc/subuid
grep $USER /etc/subgid



```

---

### Post by vijayaragavalu on 2016-08-23
MAFoElffen,
Thanks for the explanation .
Today , i have done again freshly , that is, created new user id  with taking care your suggestion  on different machine which is VMBox + ubuntu 16.04 LTS, unfortunately still i get some error related to permission denied.
below are the steps followed, please let me know whether i missed anysteps or mistakenly understood your suggestion.

Step 1) 
vijay@vijay-VirtualBox:~/XXXXX$ sudo adduser 

Step 2) (optional)
vijay@vijay-VirtualBox:~/XXXXX$ sudo passwd usrlxc

Step 3)
> vijay@vijay-VirtualBox:~/XXXXX$ sudo grep usrlxc /etc/sub{gid,uid}
        /etc/subgid:usrlxc:165536:65536
        /etc/subuid:usrlxc:165536:65536
Noted this ids for adding in to ~/.config/lxc/default.conf file in step 7

Step 3a)
Since i could not able to login to new user id ,  i just refereed below link and added the user(not sure this is required or not)
     > vijay@vijay-VirtualBox:~/XXXXX$ sudo adduser usrlxc
                              [https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-16-04)

Step 4)
    > vijay@vijay-VirtualBox:~/XXXXX$ sudo vi /etc/lxc/lxc-usernet
    added this at the end
        ```
usrlxc veth lxcbr0 10
```
> vijay@vijay-VirtualBox:/home/vijay/XXXXX$ sudo usermod --add-subuids 165536-231072 usrlxc
vijay@vijay-VirtualBox:/home/vijay/XXXXX$ sudo usermod --add-subgids 165536-231072 usrlxc


Step 5)
     su userlxc
     (entered the password)     
 > 
       usrlxc@vijay-VirtualBox:~/XXXXX$ chmod +x /home/usrlxc/.local/share/lxc/
(for the first time i got error as i dont have above path and same will be again during when we do lxc-create steps)

output for the same :
> usrlxc@vijay-VirtualBox:/home/vijay/XXXXX$ grep $USER /etc/subuid 
      usrlxc:165536:65536
usrlxc@vijay-VirtualBox:/home/vijay/XXXXX$ grep $USER /etc/subgid  
      usrlxc:165536:65536

step 6)
    
> usrlxc@vijay-VirtualBox:/home/vijay/XXXXX$ id
                     uid=1001(usrlxc) gid=1001(usrlxc) groups=1001(usrlxc)

Step 7)
> usrlxc@vijay-VirtualBox:/home/vijay/XXXXX$ mkdir -p ~/.config/lxc
usrlxc@vijay-VirtualBox:/home/vijay/XXXXX$ cp /etc/lxc/default.conf ~/.config/lxc/default.conf

  appended lxc.id_map for uid and gid as per step 3 
Please find the same for ~/.config/lxc/default.conf file
```

usrlxc@vijay-VirtualBox:~$ cat ~/.config/lxc/default.conf
lxc.network.type = veth
lxc.network.link = lxcbr0
lxc.network.flags = up
lxc.network.hwaddr = 00:16:3e:xx:xx:xx
lxc.id_map = u 0 165536 65536
lxc.id_map = g 0 165536 65536
```


after this  when i do un priv lxc create as below (without any sudo or root user id), i faced permission denied error 

error: 
> usrlxc@vijay-VirtualBox:~$ lxc-create -t busybox -n lxc_unprvil
lxc-create: utils.c: mkdir_p: 253 Permission denied - failed to create directory '/run/user/1000/lxc/'
failed to create lock
Failed to create lxc container.


Please let me know if i missed anyting ( sorry, i am new to LXC)

---

### Post by vijayaragavalu on 2016-08-23
adding to above , i noticed this when i do on sudo user
```

vijay@vijay-VirtualBox:~/XXXXX$ sudo grep $USER /etc/subuid
vijay:100000:65536
vijay:165536:65537

vijay@vijay-VirtualBox:~/XXXXX$ sudo grep $USER /etc/subgid
vijay:100000:65536
vijay:165536:65537

```
does gid and uid look fine for sudo user and lxc user which i created ?, please also confirm this point while you provide any suggestion for above mentioned lxc-create failure.
Thanks

---

### Post by MAFoElffen on 2016-08-23
Please, as per forums policy, go back to your posts and edit them to enclosed all output and/or commands within code tags. I note about changing the fonts type or sizes of fonts within a post, is that some user's see that as distracting (or offensive). I have edited your last post as an example. 

For me, is is hard to read and follow what are your comments and what was output... Also, as you san see, the forums software, if things are not enclosed in code tags, your text got interpreted as emogi's, not left as literal. If you have questions on how to do that, please ask.

As long as you've done your prepe work to point things to your own default.conf file in your own personal lxc directory, such as this:
```

echo "lxc.id_map = u 0 100000 65536" > ~/.config/lxc/default.conf
echo "lxc.id_map = g 0 100000 65536" >> ~/.config/lxc/default.conf
echo "lxc.network.type = veth" >> ~/.config/lxc/default.conf
echo "lxc.network.link = lxcbr0" >> ~/.config/lxc/default.conf


# As root...
echo "saas veth lxcbr0 10" >> /etc/lxc/lxc-usernet

```
Then to solve any other permission errors, try this:
```

unset XDG_SESSION_ID XDG_RUNTIME_DIR
sudo cgm create all $USER
sudo cgm chown all $USER $(id -u) $(id -g)
cgm movepid all $USER $$

```

---

### Post by vijayaragavalu on 2016-08-23
as per your input, I edited with tags for my post , thanks for the same.

For error, i will try your suggestion and check.
 however, I have just referred below link and understood the reason for the failure 
[https://gist.github.com/julianlam/4e2bd91d8dedee21ca6f](https://gist.github.com/julianlam/4e2bd91d8dedee21ca6f)

based  on that , i just logged out from " vijay user(sudo user) to su-usrlxc"  and logged in directly as usrlxc, then i could not see this error
i am able to create, start, attach in new low privileged user( usrlxc). thanks 

Now i will try your two path to achieve my goal.

also, can you please comment below is achievable which is my ultimate goal.
Login  to root user , Do lxc-create of container(either privilege or un-priv  whichever is suitable for my goal), then do lxc-start of the container with same  root user id. while staring container i need to start all the process inside the container with low privilege(un-priv) user id in which access to the user is restricted to only container and not to host.basically when i say ps -ax , i should be able to see un-priv user id for all the container process.

---

### Post by vijayaragavalu on 2016-08-24
Hi MAFoElffen,

With your suggestion , the issue is resolved now , Thanks a lot. 
Can you please provide your suggestion or input for above comment mentioned goal. 
Is this achievable?

---

### Post by vijayaragavalu on 2016-08-29
Hi MAFoElffen,

I have provided my understanding below forum link for my question .  
[https://ubuntuforums.org/showthread.php?t=2334953](https://ubuntuforums.org/showthread.php?t=2334953)

and now i have tried your one more suggestion related cgroups and facing error  
your suggestion was, 
```
unset XDG_SESSION_ID XDG_RUNTIME_DIR
sudo cgm create all $USER
sudo cgm chown all $USER $(id -u) $(id -g)
cgm movepid all $USER $$
```

I faced below error for 
```
sudo cgm chown all $USER $(id -u) $(id -g)
```

Error:
> call to cgmanager_chown_sync failed : invalid argument 

Please let me know what could be issue in my setup.

Please note , original error will not be seen if i do login directly to un-priv user instead of su or ssh from sudo user
Original Error:
> usrlxc@vijay-VirtualBox:~$ lxc-create -t busybox -n lxc_unprvil
lxc-create: utils.c: mkdir_p: 253 Permission denied - failed to create directory '/run/user/1000/lxc/'
failed to create lock
Failed to create lxc container.

output for /proc/self/cgroup
```
vijay@vijay-VirtualBox:~$ cat /proc/self/cgroup
11:pids:/user.slice/user-1000.slice
10:cpuset:/
9:devices:/user.slice
8:perf_event:/
7:freezer:/user/vijay/1
6:memory:/user/vijay/1
5:cpu,cpuacct:/user.slice
4:blkio:/user.slice
3:hugetlb:/
2:net_cls,net_prio:/
1:name=systemd:/user.slice/user-1000.slice/session-c2.scope
```

---

