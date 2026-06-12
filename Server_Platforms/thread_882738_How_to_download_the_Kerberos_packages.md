---
title: "How to download the Kerberos packages"
date: 2008-08-07
forum: Server Platforms
---

### Post by pmc64 on 2008-08-07
Hi everyone

I have just installed Ubuntu Server 8.04 and am currently setting up Samba with Kerberos in order for this server to join our Windows 2003 Active Directory domain. However I do not have the Kerberos packages installed on this server and so I need to download them. I cannot seem to know how to do this. Can someone show me how to download the Kerberos packages and from where as well as the commands to use?

Thanks!

---

### Post by windependence on 2008-08-07
```
sudo apt-get install kerberos
```

-Tim

---

### Post by pmc64 on 2008-08-07
Hi Tim

Thanks for your post. But I got the following error message after entering the statement:
Couldn't find package kerberos

Thanks

---

### Post by windependence on 2008-08-07
Oops!

```
sudo apt-get update
sudo apt-get install krb5-kdc krb5-admin-server
```

-Tim

---

### Post by pmc64 on 2008-08-07
When I ran the sudo apt-get update I got error messages such as:
An error occurred during the signature verification
Some index files failed to download
What could be the cause of such errors?

Thanks!

---

### Post by windependence on 2008-08-07
It just means the signature on some packages wasn't what it expected. You should be able to run the install command for Kerberos without problems.

-Tim

---

### Post by pmc64 on 2008-08-07
I keep getting Couldn't find package krb5-kdc when I try installing :-(

---

