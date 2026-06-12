---
title: "Kerberos + LDAP + NFS"
date: 2011-02-07
forum: Server Platforms
---

### Post by danbishop on 2011-02-07
I've currently got Ubuntu server configured so that clients can login using LDAP user accounts that I've created using ldapadduser (from the ldapscripts package).

I've also got NFS exports working so that /home can be exported to clients. Kerberos authentication is enabled for NFS and clients require a nfs/clienthostname.domain principal to be able to mount the NFS share.

However, I now realise that for LDAP users to be able to access the mount they need their own Kerberos principal. If I run kinit [email]dan@DANBISHOP.ORG[/email] then I can access /home/dan as user dan otherwise I get permission denied.

My question then is how best to proceed... is there a way to configure the client/server so that once a client has mounted the nfs share using Kerberos, all users can access it without their own principal?

Reading around online, it seems more usual to create kerberos principles for all users, but then how does one manage users? Using ldapscripts is very easy, but if the admin then has to manually create kerberos principals everytime, it could become very tedious. Furthermore how do users change their password if kerberos is used for authentication?

I'm very confused about how best to proceed and woudl appreciate any advice anyone can give!

Thanks! :D

---

### Post by danbishop on 2011-05-11
I eventually figured it all out... should anyone with the same issue stumble across this post in the future, I wrote up everything I did here: [http://www.danbishop.org/2011/05/01/ubuntu-11-04-sbs-small-business-server-setup-part-1-%E2%80%93-dhcp-and-dns/]("http://www.danbishop.org/2011/05/01/ubuntu-11-04-sbs-small-business-server-setup-part-1-%E2%80%93-dhcp-and-dns/")

---

### Post by chenxiaolong on 2012-04-16
> **danbishop said:**
> I eventually figured it all out... should anyone with the same issue stumble across this post in the future, I wrote up everything I did here: [http://www.danbishop.org/2011/05/01/ubuntu-11-04-sbs-small-business-server-setup-part-1-%E2%80%93-dhcp-and-dns/]("http://www.danbishop.org/2011/05/01/ubuntu-11-04-sbs-small-business-server-setup-part-1-%E2%80%93-dhcp-and-dns/")

Thank you very much for the guide :)

---

