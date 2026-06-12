---
title: "NFS Stale File Handle Problem"
date: 2012-10-30
forum: Server Platforms
---

### Post by baddestguy on 2012-10-30
Hi guys,
I have the files for a website on a central machine and mount this directory on several other small servers around using nfs. problem is, I have started to get some strange errors recently, the whole system gets frozen and I get this error:

Stale File Handle

I havent been able to get enough information for debugging from the server itself, but I am hoping there would be a way to resolve this issue, is there anything in particular that I have to bear in mind when mounting file for a website to a central server?

I there a better way to handle this situation? keeping the website files on one server and have all others share into same files?

thanks in advance

---

### Post by dannyboy79 on 2012-10-30
it sounds like changes are being made to the same files but on different clients.
The best solution is to remount directory from the NFS client. if it's a website, why do you need the files mounted on other clients?

---

### Post by baddestguy on 2012-10-31
Yes, its a website, so we have a loadbalancer at the top and one NFS server with the website files on it.

We have about 3 webservers and they are all mounted to the NFS file server, so that they can use thesame codebase - there is very minimal I/O, as it is typically lots of reading. the applications are popular ones such as wordpress e.t.c.

Is there an alternative to this setup?

 ================= HAPROXY ===================
 ====== WEB SERVER ======== WEB SERVER =======
==================FILESERVER =================

---

### Post by dannyboy79 on 2012-10-31
im honestly not sure, you'll have to wait for someone else? did you try to remount the NFS shares on the clients? did that result in error disappearing?

---

### Post by baddestguy on 2012-10-31
Well yes it does, I can always fix this problem by remounting the points affected, but I guess I am using the wrong solution for the problem (i need to prevent it rather than solve it).

Maybe a small background on what I am doing will help.

So i have a setup of subversion (svn) on a machine and I update my live webserver from the SVN server.

I realized i have same codebase on several webservers and considered this as creating unnecessary redundancy, So i moved the files to one central (file) server that is updated via SVN and created an NFS mount from the webservers to the central file server.

I thought this should work well (which it actually does) until the problem of "NFS Stale File Handle" started surfacing and its only rectified when I manually go to the central file server to reboot it or restart NFS, wondering if there is any walk around this or better way to avoid this problem perhaps by changing my current structure, using an alternative to NFS e.t.c

---

### Post by dannyboy79 on 2012-10-31
so the server with the common codebase is sharing a folder over NFS and each of the 3 webservers mounts that NFS share to ensure all 3 machines have the same files. I understand. Have you tried SAMBA although I think NFS is faster. 

When does the NFS Stale File Handle occur? What exactly are your client mount options? Show me the /etc/fstab mount for the NFS mounted share.

---

### Post by baddestguy on 2012-10-31
So my fastab is pretty much standard:

fileserver:/var/www/site/v1 /var/www/site/v1 nfs defaults 0 0


I do not add any extra, just the normal mount across all three web servers

---

### Post by dannyboy79 on 2012-10-31
and the /etc/exports file on the server?

---

### Post by baddestguy on 2012-10-31
/var/www/ 10.177.129.188/24(rw,async,no_root_squash) 10.177.159.115/24(rw,async,no_root_squash)

---

### Post by baddestguy on 2012-10-31
thats IP for the 2 machines (web servers)

---

### Post by rait07 on 2012-10-31
NFS doesn't install in my desktop..please help me...:(

---

### Post by dannyboy79 on 2012-10-31
> **baddestguy said:**
> So my fastab is pretty much standard:

fileserver:/var/www/site/v1 /var/www/site/v1 nfs defaults 0 0


I do not add any extra, just the normal mount across all three web servers

when you put "defaults", what exactly are those NFS mount options? I am not at home to check my fstab but will post later tonight.

---

### Post by dannyboy79 on 2012-10-31
> **rait07 said:**
> NFS doesn't install in my desktop..please help me...:(

please don't hijack threads. create your own and you'll get helped.

---

### Post by dannyboy79 on 2012-10-31
my client mounts the NFS share using these options
```
rsize=8192,wsize=8192,timeo=14,intr
```

my server /etc/exports file is
```
(rw,no_root_squash,async,no_subtree_check,anonuid=1000)
```

---

### Post by baddestguy on 2012-11-01
Thanks,
I have added these:

rsize=8192,wsize=8192,timeo=14,intr


On the exportfs, I do you think this bit really does alot/??


anonuid=1000

Or perhaps to allow anonymous access to certain files? do you know what it does?

---

### Post by dannyboy79 on 2012-11-01
> **baddestguy said:**
> Thanks,
I have added these:

rsize=8192,wsize=8192,timeo=14,intr


On the exportfs, I do you think this bit really does alot/??


anonuid=1000

Or perhaps to allow anonymous access to certain files? do you know what it does?
Investigating your issue I happened to take a look at my dmesg output and it is filled with errors like this
```
[103754.328162] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[104251.751080] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[104251.751109] nfsd: peername failed (err 107)!
[104251.751297] nfsd: peername failed (err 107)!
[104251.751715] nfsd: peername failed (err 107)!
[104251.751734] nfsd: peername failed (err 107)!
[104251.751751] nfsd: peername failed (err 107)!
[104251.751766] nfsd: peername failed (err 107)!
[104251.751783] nfsd: peername failed (err 107)!
[104251.751798] nfsd: peername failed (err 107)!
[104251.751814] nfsd: peername failed (err 107)!
[104251.751829] nfsd: peername failed (err 107)!
[104775.000715] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[104973.608276] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[105207.912921] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[105478.147780] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[105729.636163] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[105729.636189] __ratelimit: 9 callbacks suppressed
[105729.636193] nfsd: peername failed (err 107)!
[106168.048283] rpc-srv/tcp: nfsd: got error -104 when sending 8324 bytes - shutting down socket
[106502.776388] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[106502.776416] nfsd: peername failed (err 107)!
[107754.973160] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[107754.973186] nfsd: peername failed (err 107)!
[107754.973280] nfsd: peername failed (err 107)!
[107754.973804] nfsd: peername failed (err 107)!
[107754.973824] nfsd: peername failed (err 107)!
[107754.973840] nfsd: peername failed (err 107)!
[107754.973872] nfsd: peername failed (err 107)!
[107754.973888] nfsd: peername failed (err 107)!
[107754.973904] nfsd: peername failed (err 107)!
[107754.973919] nfsd: peername failed (err 107)!
[107754.973935] nfsd: peername failed (err 107)!
[107871.297883] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[107871.297910] __ratelimit: 41 callbacks suppressed
[107871.297914] nfsd: peername failed (err 107)!

```
so my option may not be good! Sorry about this. I am investigating this now, so you may not want to use those options within your /etc/exports file IF your dmesg never had the above errors.

I also note these errors on the client within dmesg
```
Oct 31 22:03:41 core2duo kernel: [86071.584564] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584584] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584603] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584626] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584647] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584666] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584684] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584702] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584721] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584738] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584759] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584768] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584771] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584774] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:41 core2duo kernel: [86071.584777] nfs: server 192.168.0.5 not responding, still trying
Oct 31 22:03:42 core2duo kernel: [86072.306238] nfs: server 192.168.0.5 OK
Oct 31 22:03:42 core2duo kernel: [86072.306399] nfs: server 192.168.0.5 OK
Oct 31 22:03:42 core2duo kernel: [86072.306521] nfs: server 192.168.0.5 OK

```

So I am looking into it.


What the anonuid=1000 does is map requests to the UID (user id) to 1000, which is my users ID on both the server and the client.

Here's what the man page says
```
anonuid and anongid
These options explicitly set the uid and gid of the anonymous account. This option is primarily useful for PC/NFS clients, where you might want all requests appear to be from one user. As an example, consider the export entry for /home/joe in the example section below, which maps all requests to uid 150 (which is supposedly that of user joe).
```

I'll post back if I find out more info on the options I am using and about the errors.

---

### Post by SeijiSensei on 2012-11-02
If you're running with no_root_squash and mounting the NFS share as root on the web server, there's no reason to use anonuid.

I'd also suggest bumping up the rsize and wsize parameters on the clients to values like 32768 or even 65536 if they are connected with something like 100BaseT or gigabit Ethernet.  Also try adding "async" to the list of options on the servers since it doesn't sound like the clients will be writing very much to the shared directory.  (Things like Wordpress read and write to the SQL database.)  

Still, if the problem persists, and the codebase on the various machines is stable, I suggest simply running multiple copies of the website code rather than sharing one copy with NFS.  You can keep them synchronized with periodic rsync runs.

---

