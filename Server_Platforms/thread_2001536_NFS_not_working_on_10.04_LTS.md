---
title: "NFS not working on 10.04 LTS"
date: 2012-06-11
forum: Server Platforms
---

### Post by tomcatkzn on 2012-06-11
Hi, Any help will be greatly appreciated. I setup a 10.04LTS server on Hyper-V and had the NFS system working perfectly - as a trial. I have now done a reinstall of 10.04LTS on a Dell R610 standalone and have set up the exports etc exactly the same but I am unable to connect from a client machine. I get connection timed out.
I have disabled IPtables and ufw, so as far as I can tell there are no firewalls in the way.
If I enter showmount -p "serveripaddress" then the exported directories are listed correctly, but if I enter: sudo mount -t -o nolock "serveripaddres":/images/dev /test
then I get connection timed out.
Any ideas appreciated. Am pulling my hair out.

---

### Post by roelforg on 2012-06-11
Check if you can mount it on the server itself using 127.0.0.1 as ip.
Post your /etc/exports
Is it a local server or a remote one?
Server: Check your firewall logs and /var/log/syslog to see if it registers the nfs connection (it was a royal pain getting my server's firewall to allow nfs).
Post the dmesg entries from the client about the mount error.
What was the exact error?
Did you install the packages you need to mount nfs on the client?
 
My own nfs setup drove me to the brink of insanity with these errors until i noticed a small detail i forgot... I set my /etc/exports to allow connections from 192.168.0.0/8 (if you don't get it, look up what the /8 stands for)

---

### Post by tomcatkzn on 2012-06-11
thanks for the help roelforg.
 
[EMAIL="root@fogserver:/home/tim"]root@fogserver:/home/tim[/EMAIL]# sudo mount -t nfs 192.168.103.246:/images/dev /test
works. mount shows it as mounted.
Here is exports file:
/images       192.168.103.1/24(ro,sync,no_wdelay,insecure_locks,no_root_squash,insecure,no_subtree_check)
/images/dev   192.168.103.1/24(rw,sync,no_wdelay,no_root_squash,insecure,no_subtree_check)
Client has same setup as server. installed nfs-common portmap and nfs-kernel-server
rpcinfo shows:
[EMAIL="root@fogserver:/home/tim"]root@fogserver:/home/tim[/EMAIL]# rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  55285  status
    100024    1   tcp  54668  status
    100021    1   udp  45727  nlockmgr
    100021    3   udp  45727  nlockmgr
    100021    4   udp  45727  nlockmgr
    100021    1   tcp  54180  nlockmgr
    100021    3   tcp  54180  nlockmgr
    100021    4   tcp  54180  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  59018  mountd
    100005    1   tcp  51658  mountd
    100005    2   udp  59018  mountd
    100005    2   tcp  51658  mountd
    100005    3   udp  59018  mountd
    100005    3   tcp  51658  mountd

Am busy reinstalling client as it was running in Hyper-V and it crashed.  Will install in on virtualbox.
also tried connecting on windows using nfsaxe. It can see the shares but times out on cannection with message "Contact your system administrator" Dont you love it. I am the system administrator!

---

### Post by tomcatkzn on 2012-06-11
from client: (10.04LTS Server)
[EMAIL="tim@fog10:~$"]tim@fog10:~$[/EMAIL] sudo mount -t nfs 192.168.103.246:/images/dev /test
mount.nfs: mount system call failed

On client:
[EMAIL="tim@fog10:~$"]tim@fog10:~$[/EMAIL] showmount -a 192.168.103.246
All mount points on 192.168.103.246:
192.168.103.108:/images/dev
192.168.103.246:/images
192.168.103.246:/images/dev
192.168.103.92:/images/dev
[EMAIL="tim@fog10:~$"]tim@fog10:~$[/EMAIL] showmount -e 192.168.103.246
Export list for 192.168.103.246:
/images/dev 192.168.103.1/24
/images     192.168.103.1/24
 
On Client:
[EMAIL="tim@fog10:~$"]tim@fog10:~$[/EMAIL] sudo tail /var/log/messages
 svc: failed to register lockdv1 RPC service (errno 97)                   .
Jun 11 13:13:48 fog10 kernel: [   33.614849] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state                    recovery directory
Jun 11 13:13:48 fog10 kernel: [   33.627125] NFSD: starting 90-second grace period

Any ideas?

---

### Post by SeijiSensei on 2012-06-11
Are you sure you have the **nfs-common** package installed on the client?  What does "dpkg -s nfs-common" show?

---

### Post by roelforg on 2012-06-11
I think i found the problem:
```

/images       192.168.103.**1**/24(ro,sync,no_wdelay,insecure_locks,no_root_squash  ,insecure,no_subtree_check)
/images/dev   192.168.103.**1**/24(rw,sync,no_wdelay,no_root_squash,insecure,no_su  btree_check)

```

It should be:
```

/images       192.168.103.**0**/24(ro,sync,no_wdelay,insecure_locks,no_root_squash  ,insecure,no_subtree_check)
/images/dev   192.168.103.**0**/24(rw,sync,no_wdelay,no_root_squash,insecure,no_su  btree_check)

```

That way it will allow the entire 192.168.103.xxx net to connect.
Or use this one to allow everyone (not recommended, this would allow anyone who can get a incoming connection to your net on the right port to connect):
```

/images *(ro,sync,no_wdelay,insecure_locks,no_root_squash  ,insecure,no_subtree_check)
/images/dev *(rw,sync,no_wdelay,no_root_squash,insecure,no_su  btree_check)

```

---

