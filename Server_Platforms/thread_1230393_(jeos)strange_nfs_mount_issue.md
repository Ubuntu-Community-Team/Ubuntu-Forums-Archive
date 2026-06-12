---
title: "(jeos)strange nfs mount issue"
date: 2009-08-03
forum: Server Platforms
---

### Post by upengan78 on 2009-08-03
Hi,

I have solaris 10 NFS server where I have given root and rw acess to a Jeos(ubunutu) client machine).

While NFS service is online and I am sure I have correct IP for the JEOS client as well as server. the nfs mount command on client shows access denied,

> mount.nfs: access denied by server while mounting <serverip>:/nfsshareon server,
> -               /nfsshare   rw=<client IP>   "" but if I change the dfstab on server to change <clientip> to @<clientip>/24 and restart nfs server then client can mount this nfs share.

I found this issue with jeos and ubuntu system because if I try mounting this share from other linux machine such as gentoo, it works without even adding @<clientip>/24  in server dfstab. this gentoo client is dhcp and does not even have any records in dns.

Is this known issue or some security feature on jeos? I don't get anything in the server log when client gets access denied. :confused:

Any idea?

Thanks.

---

### Post by upengan78 on 2009-08-03
I had to replace <client IP> in server's dfstab with the hostname of the client and restart NFS service then client could mount the nfs share. By using client's ip it still gives access denied for jeos. strange!

---

