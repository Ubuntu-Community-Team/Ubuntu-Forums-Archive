---
title: "will password be exposed to internet when encrypting iSCSI target"
date: 2008-04-22
forum: Security
---

### Post by say2sky on 2008-04-22
Now I setup an iSCSI target for storage RAID and hope to access my data on storage RAID anywhere through internet by using initiators. For security concerns, I use dmsetup/luks encrypting all data storage on RAID from initiators side, then all data can be thought  safe in both transmission though internet and on RAID if no other interface to access these data.

My question now is 

if or not the first password using to open luks volume will expose to internet unencrytedly?   I have read some about protocol used by iSCSI but I am still not clear about how the password be transfered encrypted or not. Thanks!

---

### Post by say2sky on 2008-04-22
Anyone can help me to answer this security question? Your idea is greatly appreciated. Thank you for your help!

---

### Post by scorp123 on 2008-04-22
> **say2sky said:**
> Now I setup an iSCSI target for storage RAID and hope to access my data on storage RAID anywhere through internet by using initiators. I fail to see why you would do that? Why not have a server and then access it via e.g. OpenVPN or SSH?

I definitely would not expose my storage directly to the Internet.

---

### Post by say2sky on 2008-04-22
> **scorp123 said:**
> I fail to see why you would do that? Why not have a server and then access it via e.g. OpenVPN or SSH?

I definitely would not expose my storage directly to the Internet.

Thanks for your suggestion. I indeed use SSH and VPN to access file and directory now and it work very well. 

Now I just hope to find if security access can be achieved by directly using block device iSCSI interface when all the data on it is already encrypted and if it will have same security strength and transmission speed. Any clue about  these aspect?

---

### Post by scorp123 on 2008-04-22
> **say2sky said:**
>  Now I just hope to find if security access can be achieved by directly using block device iSCSI interface when all the data on it is already encrypted  Still, I'd only use stuff like that via VPN or through a SSH tunnel and not expose more things to the Internet than what really needs to be exposed.

---

### Post by scorp123 on 2008-04-22
As I already wrote above ... I would not expose this directly to the Internet but rather establish SSH tunnels or do all of this via VPN. See below:

[http://en.wikipedia.org/wiki/ISCSI#Authentication](http://en.wikipedia.org/wiki/ISCSI#Authentication)
>  " ... iSCSI initiators and targets prove their identity to each other using the CHAP protocol, which includes a mechanism to prevent cleartext passwords from appearing on the wire. By itself, the CHAP protocol is vulnerable to dictionary attacks, spoofing, or reflection attacks ..." 

[http://en.wikipedia.org/wiki/ISCSI#Confidentiality_and_integrity](http://en.wikipedia.org/wiki/ISCSI#Confidentiality_and_integrity)
>  " ... For the most part, iSCSI is a cleartext protocol that provides no cryptographic protection for data in motion during SCSI transactions. As a result, an attacker who can listen in on iSCSI ethernet traffic can:

    * Reconstruct and copy the files and filesystems being transferred on the wire

    * Alter the contents of files by injecting fake iSCSI frames

    * Corrupt filesystems being accessed by initiators, exposing servers to software flaws in poorly-tested filesystem code.

These problems are not unique to iSCSI, but rather apply to any IP-based SAN protocol without cryptographic security. Though IPSec is frequently cited as a solution to the IP SAN security problem, performance and compatibility concerns retard its deployment ... 

"iSCSI over distance: how to avoid disappointment"
[http://www.thefreelibrary.com/iSCSI+over+distance:+how+to+avoid+disappointment-a0129357484](http://www.thefreelibrary.com/iSCSI+over+distance:+how+to+avoid+disappointment-a0129357484)

---

### Post by say2sky on 2008-04-22
> **scorp123 said:**
> As I already wrote above ... I would not expose this directly to the Internet but rather establish SSH tunnels or do all of this via VPN. See below:

[http://en.wikipedia.org/wiki/ISCSI#Authentication](http://en.wikipedia.org/wiki/ISCSI#Authentication)


[http://en.wikipedia.org/wiki/ISCSI#Confidentiality_and_integrity](http://en.wikipedia.org/wiki/ISCSI#Confidentiality_and_integrity)


"iSCSI over distance: how to avoid disappointment"
[http://www.thefreelibrary.com/iSCSI+over+distance:+how+to+avoid+disappointment-a0129357484](http://www.thefreelibrary.com/iSCSI+over+distance:+how+to+avoid+disappointment-a0129357484)

Thanks a lot for your info and link about performance problem for long distance iSCSI through TCP. 

In the past I already read wiki article iSCSI, but I am not very clear if implementing initiator encryption can overcome the weak aspect of iSCSI protocol.  

After think it again Now I know that initiator side encryption can not bypass CHAP protocol, so the security weakness is still there. 

Thanks again your info let me know a lot more about iSCSI. :KS

---

