---
title: "Uid/Gid privileged LXC container : systemd lxc-start failed on ubuntu 16.04"
date: 2016-08-24
forum: Virtualisation
---

### Post by vijayaragavalu on 2016-08-24
Hi Everyone ,


I would like to create & start LXC container for specific UID & GID for below purpose.

Login  to root user(sudo user) , Do lxc-create of container, then do lxc-start of the  container with same  root user id. while staring container i need to  start all the process inside the container with low privilege(un-priv)  user id in which access to the user is restricted to only container and  not to host.basically when i say ps -axu , i should be able to see low privilege  user id for all the container process.

PS : my host which is VM with ubuntu 16.04 LTS is systemd init system and my container(type busybox) will be started with systemd services . for that i have modified busybox template as below 
```
lxc.init_cmd=/lib/systemd/systemd
```
and also removed all rcS & inittab related scripts in the busybox default template 

and for user id map , i have changed as below in my template 
```
   lxc.id_map=u 0 165536 65536
   lxc.id_map=g 0 165536 65536  
```

after that i just followed below comments

Container created normally with below comment (and i cross checked config file at /var/lib/lxc/testecho_uid/config to make sure that all my template changes are reflected or not, found ok) 
```
  sudo lxc-create -n testecho_uid -t busybox_systemd_uid
```

Entered below command to start the container with foreground  
```
  sudo lxc-start -n testecho_uid -F
```

Error is :
> 
vijay@vijay-VirtualBox:~$ sudo lxc-start -n testecho_uid -F
lxc-start: cgfsng.c: cgfsng_create: 1072 No such file or directory - Failed to create /sys/fs/cgroup/systemd//lxc/testecho_uid: No such file or directory
                                         lxc-start: cgfsng.c: cgfsng_create: 1072 No such file or directory - Failed to create /sys/fs/cgroup/systemd//lxc/testecho_uid-1: No such file or directory
                                                                                    newuidmap: uid range [0-65536) -> [165536-231072) not allowed
                                 lxc-start: start.c: lxc_spawn: 1161 failed to set up id mapping
                                                                                                lxc-start: start.c: __lxc_start: 1353 failed to spawn 'testecho_uid'
                                                    newuidmap: uid range [0-65536) -> [165536-231072) not allowed
lxc-start: conf.c: userns_exec_1: 4315 Error setting up child mappings
lxc-start: cgfsng.c: recursive_destroy: 983 Error destroying /sys/fs/cgroup/systemd//lxc/testecho_uid-2
newuidmap: uid range [0-65536) -> [165536-231072) not allowed
lxc-start: conf.c: userns_exec_1: 4315 Error setting up child mappings
lxc-start: cgfsng.c: recursive_destroy: 983 Error destroying /sys/fs/cgroup/perf_event//lxc/testecho_uid-2
newuidmap: uid range [0-65536) -> [165536-231072) not allowed
lxc-start: conf.c: userns_exec_1: 4315 Error setting up child mappings
lxc-start: cgfsng.c: recursive_destroy: 983 Error destroying /sys/fs/cgroup/hugetlb//lxc/testecho_uid-2
newuidmap: uid range [0-65536) -> [165536-231072) not allowed
lxc-start: conf.c: userns_exec_1: 4315 Error setting up child mappings
lxc-start: cgfsng.c: recursive_destroy: 983 Error destroying /sys/fs/cgroup/cpu//lxc/testecho_uid-2
newuidmap: uid range [0-65536) -> [165536-231072) not allowed
lxc-start: conf.c: userns_exec_1: 4315 Error setting up child mappings
lxc-start: cgfsng.c: recursive_destroy: 983 Error destroying /sys/fs/cgroup/memory//lxc/testecho_uid-2
newuidmap: uid range [0-65536) -> [165536-231072) not allowed
lxc-start: conf.c: userns_exec_1: 4315 Error setting up child mappings
lxc-start: cgfsng.c: recursive_destroy: 983 Error destroying /sys/fs/cgroup/pids//lxc/testecho_uid-2
newuidmap: uid range [0-65536) -> [165536-231072) not allowed
lxc-start: conf.c: userns_exec_1: 4315 Error setting up child mappings
lxc-start: cgfsng.c: recursive_destroy: 983 Error destroying /sys/fs/cgroup/blkio//lxc/testecho_uid-2
newuidmap: uid range [0-65536) -> [165536-231072) not allowed
lxc-start: conf.c: userns_exec_1: 4315 Error setting up child mappings
lxc-start: cgfsng.c: recursive_destroy: 983 Error destroying /sys/fs/cgroup/cpuset//lxc/testecho_uid-2
newuidmap: uid range [0-65536) -> [165536-231072) not allowed
lxc-start: conf.c: userns_exec_1: 4315 Error setting up child mappings
lxc-start: cgfsng.c: recursive_destroy: 983 Error destroying /sys/fs/cgroup/net_cls//lxc/testecho_uid-2
newuidmap: uid range [0-65536) -> [165536-231072) not allowed
lxc-start: conf.c: userns_exec_1: 4315 Error setting up child mappings
lxc-start: cgfsng.c: recursive_destroy: 983 Error destroying /sys/fs/cgroup/devices//lxc/testecho_uid-2
newuidmap: uid range [0-65536) -> [165536-231072) not allowed
lxc-start: conf.c: userns_exec_1: 4315 Error setting up child mappings
lxc-start: cgfsng.c: recursive_destroy: 983 Error destroying /sys/fs/cgroup/freezer//lxc/testecho_uid-2
lxc-start: lxc_start.c: main: 344 The container failed to start.
lxc-start: lxc_start.c: main: 348 Additional information can be obtained by setting the --logfile and --logpriority options.


Can anyone please tell me whether i am missing anything here.

below are setup for uid & gid 
```
vijay@vijay-VirtualBox:~$ sudo cat  /etc/subgid
vijay:100000:65536
usrlxc:165536:65536
vijay:165536:65537
```

```
vijay@vijay-VirtualBox:~$ sudo cat  /etc/subuid
vijay:100000:65536
usrlxc:165536:65536
vijay:165536:65537
```


I have also discussed similar topic on below , but that subject was for un-privilage conatiers and now it is not specific to priv or un-priv , it is just related to UID and GID for systemD init system.

[https://ubuntuforums.org/showthread.php?t=2334545](https://ubuntuforums.org/showthread.php?t=2334545)

---

### Post by vijayaragavalu on 2016-08-25
if above my question is not clear , please see below one more question similar to same above scenario.
Is there a way to access(lxc start & attach) unprivileged container from root user or sudo user . 
That is , I have created , started and attached un-priv container using lxc user(not sudo user/root user) by login into lxc user without any issue. Now i would like to start & attach the lxc user created un-priv container from root user or sudo user. 

Is that possible? if yes please let me know how to do that?. 
I checked lxc-ls from sudo/root user and it just listed only the  containers created by sudo user and does not display the container  created by lxc user. 

or 

All the processes/threads of Privilege container can be executed/run for specific UID(eg: lxc user) by root/sudo user while doing lxc-start or by any means?
I also tried by giving below lxc user uid & gid in config(ultimately changing busybox template).  it gave above comment error.
   ```
 lxc.id_map=u 0 165536 65536
  lxc.id_map=g 0 165536 65536
```
 
I tried all the possible way , but no luck , please  educate me this topic.

Below are user detail in my ubuntu desktop 
> lxc user --> "usrlxc" which i have created as part of un-priv container creation experiment.
Sudo user --> "vijay" - this is sudo user in my ubuntu 16.04 Virtual box machine.
root user --> # which all of you aware

Please let me know if any information from my ubuntu setup or lxc config

---

### Post by vijayaragavalu on 2016-08-29
I dont find any option to map UID/GIP for privileged container with  so far experiment wrt LXC . 
From that i can understand ,UID/GID mapping can be done for non-priv  container only.Correct me if i am wrong. 

In other-way , we cannot access un-priv container from root user(or sudo  user) , that is if we do  sudo lxc-ls , it will only list the root/sudo user created container and  will not display un-priv container created by low-privileged  user(usrlxc in my case). 
So , we can not do lxc-start/attach un-priv  container from root/sudo user.


Now, I am trying to manage using systemD service files to achieve.not  fully finished yet.  i could do lxc-create /stop . 
But facing problem  to do lxc-start from systemD service for specific user which i am trying to resolve by my own . if i am not able to resolve , i will post error msg here to get help from you.

Please anyone let me know if you have better solution to start un-priv  container from root/sudo login other than systemD service method

---

