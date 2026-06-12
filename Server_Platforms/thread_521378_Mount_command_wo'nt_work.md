---
title: "Mount command wo'nt work"
date: 2007-08-09
forum: Server Platforms
---

### Post by ncwalker on 2007-08-09
I am trying to set-up a NFS on a P3. I am using Ubuntu 7.04 Server on the server and Ubuntu 7.04 Desktop on the Desktop. Using the instructions at [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I followed the instructions and changed my /etc/exports to the following


```
/home 192.168.0.0/255.255.255.0(rw,sync)
/usr/local 192.168.0.0/255.255.255.0(rw,sync)
```

When I export the shares the terminal responds like this: 



```
exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.0.0/255.255.255.0:/home".
Assuming default behaviour ('subtree_check'). 
NOTE: this default will change with nfs-utils version 1.1.0
exportfs: /etc/exports [3]: Neither 'subtree_check' or 'no_subtree_check' specified for export " 192.168.0.0/255.255.255.0:/usr/local".
Assuming default behaviour ('subtree_check').
NOTE: this default will change with nfs-utils version 1.1.0
```

Is this O.K.?

When I try to mount :

```
sudo mount 192.168.0.100:/home /home/ncwalker/networkh
```

the terminal appears to get stuck.

What can I do to make it work? 

Many thanks!

---

### Post by bodhi.zazen on 2007-08-09
What is the ip of your router ?

Try 

/home 192.168.0.0/24(rw,async)

Or if your router is 192.168.0.1 :

/home 192.168.0.1/24(rw,async)

And with mount :

mount **-t nfs** 192.168.0.100:/home /home/ncwalker/networkh

Do you have a firewall configured on the server ?

---

### Post by ncwalker on 2007-08-09
Thanks for the help.  The router is 192.168.0.1

Do you want me to put the following in /etc/exports on the server?

```
/home 192.168.0.1/24(rw,async)
```

I have tried specifying the kind of mount like you suggested:

```
mount -t nfs 192.168.0.100:/home /home/ncwalker/networkh
```

But it didn't help.  

I do have a Linux Firewall blocking all except SSH and IDENT on external interface...


....cripes...

When I take down the firewall it works.  GRRR:lolflag:

O.K. new question.

I am running webmin ver. 1.350 and the firewall options are as follows: 

Allow all traffic
Do network address translation on external interface eth0
Block all incoming connections on external interface eth0
Block all except SSH and IDENT on external interface eth0
Block all except SSH and IDENT ping and high ports on interface eth0

which one should I choose?

Thanks for the help too!

---

### Post by bodhi.zazen on 2007-08-10
Not sure how to do it via webmin, I use firestarter :(

You should likely choose "Do network address translation on external interface eth0" but now you have to allow nfs via NAT ...

I am afraid I do not know enough to guide you through NAT for nfs shares

---

