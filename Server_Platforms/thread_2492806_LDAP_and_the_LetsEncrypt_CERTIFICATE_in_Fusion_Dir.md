---
title: "LDAP and the LetsEncrypt CERTIFICATE in Fusion Directory..."
date: 2023-11-23
forum: Server Platforms
---

### Post by civilpolisen on 2023-11-23
I've been fiddeling around with all kinds of more or less working ideas...!
Here's where I am at now!
Our OpenLDAP server has stopped to work and it's because the certificates has exprired... 
However, the certificate will be renewed and they expire after 90 days. The certificate created at November 5 should still be valid as of today! (Nov. 23)

I have some questions about the log files!

```
root@ldap-srv:/etc/letsencrypt/archive# ls -l fd*
fd.url.topdomain
total 120
-rw-r--r-- 1 root     root 1505 Nov 23 12:21 cert10.pem
-rw-r--r-- 1 openldap root 1838 Mar  9  2023 cert5.pem
-rw-r--r-- 1 root     root 1834 May  8  2023 cert6.pem
-rw-r--r-- 1 root     root 1757 Jul  8 01:01 cert7.pem
-rw-r--r-- 1 root     root 1757 Sep  6 04:16 cert8.pem
-rw-r--r-- 1 root     root 1757 Nov  5 11:14 cert9.pem
-rw-r--r-- 1 root     root 3749 Nov 23 12:21 chain10.pem
-rw-r--r-- 1 openldap root 3749 Mar  9  2023 chain5.pem
-rw-r--r-- 1 root     root 3749 May  8  2023 chain6.pem
-rw-r--r-- 1 root     root 3749 Jul  8 01:01 chain7.pem
-rw-r--r-- 1 root     root 3749 Sep  6 04:16 chain8.pem
-rw-r--r-- 1 root     root 3749 Nov  5 11:14 chain9.pem
-rw-r--r-- 1 root     root 5254 Nov 23 12:21 fullchain10.pem
-rw-r--r-- 1 openldap root 5587 Mar  9  2023 fullchain5.pem
-rw-r--r-- 1 root     root 5583 May  8  2023 fullchain6.pem
-rw-r--r-- 1 root     root 5506 Jul  8 01:01 fullchain7.pem
-rw-r--r-- 1 root     root 5506 Sep  6 04:16 fullchain8.pem
-rw-r--r-- 1 root     root 5506 Nov  5 11:14 fullchain9.pem
-rw------- 1 root     root  241 Nov 23 12:21 privkey10.pem
-rw------- 1 openldap root 1704 Mar  9  2023 privkey5.pem
-rw------- 1 root     root 1704 May  8  2023 privkey6.pem
-rw------- 1 root     root 1704 Jul  8 01:01 privkey7.pem
-rw------- 1 root     root 1704 Sep  6 04:16 privkey8.pem
-rw------- 1 root     root 1704 Nov  5 11:14 privkey9.pem

```

```
root@dirvish-server:/srv/backup/ldap-srv/20230903/tree/etc/letsencrypt/archive# ls -l fd*
total 120
-rw-r--r--  6 usbmux root 1834 sep  9  2022 cert2.pem
-rw-r--r-- 14 usbmux root 1834 nov  8  2022 cert3.pem
-rw-r--r-- 30 usbmux root 1834 jan  8  2023 cert4.pem
-rw-r--r-- 30 usbmux root 1838 mar  9  2023 cert5.pem
-rw-r--r-- 29 root   root 1834 maj  8  2023 cert6.pem
-rw-r--r-- 27 root   root 1757 jul  8 01:01 cert7.pem
-rw-r--r--  6 usbmux root 3749 sep  9  2022 chain2.pem
-rw-r--r-- 14 usbmux root 3749 nov  8  2022 chain3.pem
-rw-r--r-- 30 usbmux root 3749 jan  8  2023 chain4.pem
-rw-r--r-- 30 usbmux root 3749 mar  9  2023 chain5.pem
-rw-r--r-- 29 root   root 3749 maj  8  2023 chain6.pem
-rw-r--r-- 27 root   root 3749 jul  8 01:01 chain7.pem
-rw-r--r--  6 usbmux root 5583 sep  9  2022 fullchain2.pem
-rw-r--r-- 14 usbmux root 5583 nov  8  2022 fullchain3.pem
-rw-r--r-- 30 usbmux root 5583 jan  8  2023 fullchain4.pem
-rw-r--r-- 30 usbmux root 5587 mar  9  2023 fullchain5.pem
-rw-r--r-- 29 root   root 5583 maj  8  2023 fullchain6.pem
-rw-r--r-- 27 root   root 5506 jul  8 01:01 fullchain7.pem
-rw-------  6 usbmux root 1704 sep  9  2022 privkey2.pem
-rw------- 14 usbmux root 1704 nov  8  2022 privkey3.pem
-rw------- 30 usbmux root 1704 jan  8  2023 privkey4.pem
-rw------- 30 usbmux root 1704 mar  9  2023 privkey5.pem
-rw------- 29 root   root 1704 maj  8  2023 privkey6.pem
-rw------- 27 root   root 1704 jul  8 01:01 privkey7.pem

```

A few questions about these log files.
1. The owner has changed... but we assume it shall be that way, becasue it was earlier.
2. The certificate from November 5 was re-newed and would obviously work to this date, November 23.
3. No cronjob was foud... We don't know how the certificates were renewed for the past.

---

