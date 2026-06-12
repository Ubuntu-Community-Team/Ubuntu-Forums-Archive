---
title: "Apache2 won't start due to SSL cert not existing when it does"
date: 2018-01-25
forum: Server Platforms
---

### Post by qwensdai on 2018-01-25
Hi everyone,

I've been running a file server using owncloud for a while and it was  working swimmingly. Then I stopped using the server for a while and  today I found I can no longer connect to the server. After looking into  it (by connecting to it through ssh) I found out that Apache2 wasn't  running and when I tried to start apache I got this error
"AH00526: Syntax error on line 35 of /etc/apache2/sites-enabled/default-ssl.conf:
SSLCertificateKeyFile: file '/etc/ssl/private/apache-seflsigned.key' does not exist or is empty"
When I looked in the specified directory I found that the cert DID exist  and it wasn't empty (no surprise to me as I hadn't changed anything  since I last connected) I did some searching online and have found  basically bumpkiss. I did try changing permissions to see if that was  the issue but even when i gave the folder 777 it didn't work. Has anyone  else had an issue similar to this and any suggestions?

OS: Ubuntu 14.04.4 LTS (GNU/Linux 4.2.0-42-generic x86_64)

Thanks in advance!

---

### Post by darkod on 2018-01-25
That message complains about the .key file. You say you checked the folder and the CERT existed. That's not the same...

Best to post the content of the folder:
```
ls -lh /etc/ssl/private/
```

And undo any changes in ownership/permissions you did, sometimes especially when using certificates, changing the permissions might be reported as error too. I'm not sure about apache, I know ssh doesn't like changing permissions of the keys.

---

### Post by qwensdai on 2018-01-25
```
ls -lh /etc/ssl/private
total 8.0K
-rwxrwxrwx 1 root root     1.7K Oct 31 14:18 apache-selfsigned.key
-rwxrwxrwx 1 root ssl-cert 1.7K Jun 29  2016 ssl-cert-snakeoil.key
```

it's there, my mind often equates as cert=key

---

### Post by darkod on 2018-01-25
If you copied the error message exactly as it was, you have a typo in the conf file. The message says the file apache-seflsigned is missing which is true because the filename is apache-selfsigned.
Double check and modify the conf file, then restart apache.

---

### Post by LHammonds on 2018-01-25
On my server, both the certificate and the private key are owned by root:root.   Obfuscated example:

```
-rw-r--r-- 1 root root 1497 Aug 29 15:55 /etc/apache2/ssl/certs/owncloud.crt
-rw-r--r-- 1 root root 1704 Aug 29 15:55 /etc/apache2/ssl/private/owncloud.key
```

In my apache config file for the SSL site:

```
                SSLCertificateFile /etc/apache2/ssl/certs/owncloud.crt
                SSLCertificateKeyFile /etc/apache2/ssl/private/owncloud.key
```

The command I used to create my self-signed cert that is good for 3 years was done like this:

```
openssl req -x509 -nodes -days 1095 -newkey rsa:2048 -keyout /etc/apache2/ssl/private/owncloud.key -out /etc/apache2/ssl/certs/owncloud.crt
```

To verify the certificate, I use this command:
```
openssl x509 -in /etc/apache2/ssl/certs/owncloud.crt -text -noout
```

To verify the private key, I use this command:
```
openssl rsa -in /etc/apache2/ssl/private/owncloud.key -check
```

LHammonds

---

### Post by qwensdai on 2018-01-26
> **darkod said:**
> If you copied the error message exactly as it was, you have a typo in the conf file. The message says the file apache-seflsigned is missing which is true because the filename is apache-selfsigned.
Double check and modify the conf file, then restart apache.

That was the issue thank you! My brain switches letters and numbers time to time(idk if its dyslexia or what) and I couldn't see the issue until you pointed that out. It's working now so thanks!

---

