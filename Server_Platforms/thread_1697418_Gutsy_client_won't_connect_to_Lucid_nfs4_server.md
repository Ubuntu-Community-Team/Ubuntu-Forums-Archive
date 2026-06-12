---
title: "Gutsy client won't connect to Lucid nfs4 server"
date: 2011-02-28
forum: Server Platforms
---

### Post by pnunn on 2011-02-28
Hi folks,

I'm having some real problems here trying to get a Gutsy client to mount a share on a Lucid nfs4 server.

Lucid clients can mount the share just fine.

```
mount -v -t nfs4 -o proto=tcp,port=2049 192.168.123.82:/ /backup
mount.nfs4: timeout set for Tue Mar  1 11:43:56 2011
mount.nfs4: text-based options: 'proto=tcp,port=2049,addr=192.168.123.82,clientaddr=192.168.123.15'
mount.nfs4: internal error

```
In the logs I get an error 

```

Mar  1 11:35:24 mail kernel: [6997249.410231] nfs: server 192.168.123.8 not responding, timed out
Mar  1 11:45:26 mail kernel: [6997850.092153] nfs: server 192.168.123.8 not responding, timed out
```

Which is odd as its cut off the last octet of the IP address for some reason.

Anyone else seen this?  Have any ideas what the hell is going on??

Thanks.

Peter.

---

