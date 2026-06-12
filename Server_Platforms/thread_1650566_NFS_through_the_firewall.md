---
title: "NFS through the firewall"
date: 2010-12-21
forum: Server Platforms
---

### Post by joeaura7 on 2010-12-21
I have installed kernel-nfs-server and successfully set it up and it worked without a firewall enabled. I have followed a guide, [http://www.buro9.com/blog/2009/12/07/nfs-static-ports/](http://www.buro9.com/blog/2009/12/07/nfs-static-ports/) , to make ports used by nfs static so they can be used through the firewall. Everything worked except[FONT=Microsoft Sans Serif] nlockmgr works which still gives random ports when I type [/FONT][FONT=Microsoft Sans Serif]rpcinfo -p. I have researched on other ways to do it but all of the documentation is too old (can not locate the files they have mentioned).[/FONT]

---

### Post by gmargo on 2010-12-21
Not sure if this will make the difference for you, but here's what I use for STATDOPTS and RPCMOUNTDOPTS, which are slightly different from that tutorial

Try this for STATDOPTS in **/etc/default/nfs-common**:
```

STATDOPTS="--port 4000 --outgoing-port 4001"

```And this for RPCMOUNTDOPTS in **/etc/default/nfs-kernel-server**:
```

RPCMOUNTDOPTS="--port 4002"

```

---

### Post by joeaura7 on 2010-12-21
I just tried it and there was no effect ](*,)

---

### Post by elico on 2010-12-22
did you restarted the nfs-kernel process?
and also you should use tcpdump to see your packets flow to now what is causing the problem.

---

