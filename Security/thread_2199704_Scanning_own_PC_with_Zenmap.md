---
title: "Scanning own PC with Zenmap"
date: 2014-01-15
forum: Security
---

### Post by linuxyogi on 2014-01-15
Hi,

This is the first time I am using Zenmap so I dont fully understand the results. 

I have only 1 PC at home so I am scanning 127.0.0.1 using Zenmap's "Intense Scan"  profile. The command used is

 ```
nmap -T4 -A -v 127.0.0.1
```.

The results :

_Ports/Hosts_

139/tcp open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
631/tcp open  ipp         CUPS 1.7


I am using ipkungfu and configured it as mentioned [here ]("https://help.ubuntu.com/community/firewall/ipkungfu")

I installed ipkungfu recently so I dont know much about it.

BTW at grc.com all the ports were shown as closed. I am not behind a router. I am using my router as a modem and using network manager to configure my DSL connection.

---

### Post by CharlesA on 2014-01-15
You would need to scan your machine from another machine on the same network because scanning the loopback address will show services listening that are only listening locally.

---

### Post by linuxyogi on 2014-01-15
> **CharlesA said:**
> You would need to scan your machine from another machine on the same network because scanning the loopback address will show services listening that are only listening locally.

I got only one PC. Is there any other way of doing this ?

> **CharlesA said:**
> Grc is pointless because it'll only scan your router for open ports. If you really want to check for vulnerabilities, learn about nmap.

Other than keeping all ports closed, updating system what else should a user do to keep the PC secure ?

---

### Post by CharlesA on 2014-01-15
> **linuxyogi said:**
> I got only one PC. Is there any other way of doing this ?
You could check to see which services are listening on 127.0.0.1 or ::1 and compare those from the list that nmap showed you.

IIRC, cups listens on 127.0.01, so it would be local only. Samba, on the other handle should be listening on the external interface and be accessible to everyone assuming you have not added firewall rules to block outside access.


> Other than keeping all ports closed, updating system what else should a user do to keep the PC secure ?

You should be fine.

Read this:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by cariboo on 2014-01-15
You can use one of the many free online port scanners to see if you have anything leaking. I have to ask, why are you running Samaba if you only have a single computer system? It could be a problem if you are out and about using other free wifi services.

---

### Post by linuxyogi on 2014-01-15
> **cariboo907 said:**
> You can use one of the many free online port scanners to see if you have anything leaking. I have to ask, why are you running Samaba if you only have a single computer system? It could be a problem if you are out and about using other free wifi services.

I did get the system scanned at grc.com before then for the 3 specific ports that Zenmap listed as open I went to [this site]("http://www.yougetsignal.com/tools/open-ports/") and it looks like all three of them are closed.

A friend of mine sometimes visits me and I sometimes connect to his laptop (NIC to NIC) using a crossover cable and transfer some files.

---

### Post by CharlesA on 2014-01-16
I would disable the Samba server when you aren't using it.

---

### Post by linuxyogi on 2014-01-16
Done.

---

