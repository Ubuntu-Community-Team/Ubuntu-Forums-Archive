---
title: "Cant find NFS V4"
date: 2013-01-12
forum: Server Platforms
---

### Post by chrisguk on 2013-01-12
Hi there,

I installed NFS using the command:

```
sudo apt-get update && upgrade
```

```
sudo apt-get install nfs-kernel-server
```

I then ran;

```
nfsstat
```

It shows ```
Server nfs v3:
```

How can I install Version 4?  I cant find it anywhere?

---

### Post by bab1 on 2013-01-12
> **chrisguk said:**
> Hi there,

I installed NFS using the command:

```
sudo apt-get update && upgrade
```

```
sudo apt-get install nfs-kernel-server
```

I then ran;

```
nfsstat
```

It shows ```
Server nfs v3:
```

How can I install Version 4?  I cant find it anywhere?
Does it really show this```
nfsstat
Server rpc stats:
calls      badcalls   badclnt    badauth    xdrcall
1          0          0          0          0       

[COLOR="Red"]**[B]Server nfs v3:**[/B][/COLOR]
null         getattr      setattr      lookup       access       readlink     
1       100% 0         0% 0         0% 0         0% 0         0% 0         0% 
read         write        create       mkdir        symlink      mknod        
0         0% 0         0% 0         0% 0         0% 0         0% 0         0% 
remove       rmdir        rename       link         readdir      readdirplus  
0         0% 0         0% 0         0% 0         0% 0         0% 0         0% 
fsstat       fsinfo       pathconf     commit       
0         0% 0         0% 0         0% 0         0% 

Client rpc stats:
calls      retrans    authrefrsh
0          0          0       

```
...this is normal response for this command on a NFSv4 install.  The package nfs-kernel-server on the latest Ubuntu (at least since 10.04) will always install NFSv4.  You can see the evolution of the package [**_[COLOR="Blue"]here[/COLOR]_**]("http://packages.ubuntu.com/precise/nfs-kernel-server").  Note the various versions of the packages are at the top right of the page.

---

### Post by chrisguk on 2013-01-13
> **bab1 said:**
> Does it really show this```
nfsstat
Server rpc stats:
calls      badcalls   badclnt    badauth    xdrcall
1          0          0          0          0       

[COLOR="Red"]**[B]Server nfs v3:**[/B][/COLOR]
null         getattr      setattr      lookup       access       readlink     
1       100% 0         0% 0         0% 0         0% 0         0% 0         0% 
read         write        create       mkdir        symlink      mknod        
0         0% 0         0% 0         0% 0         0% 0         0% 0         0% 
remove       rmdir        rename       link         readdir      readdirplus  
0         0% 0         0% 0         0% 0         0% 0         0% 0         0% 
fsstat       fsinfo       pathconf     commit       
0         0% 0         0% 0         0% 0         0% 

Client rpc stats:
calls      retrans    authrefrsh
0          0          0       

```
...this is normal response for this command on a NFSv4 install.  The package nfs-kernel-server on the latest Ubuntu (at least since 10.04) will always install NFSv4.  You can see the evolution of the package [**_[COLOR="Blue"]here[/COLOR]_**]("http://packages.ubuntu.com/precise/nfs-kernel-server").  Note the various versions of the packages are at the top right of the page.

Hi yes it does.  Thank you for improving my lack of knowledge ;)

All is well then I guess

---

