---
title: "Web interface problem with Eucalyptus on ubuntu 12.04"
date: 2012-08-22
forum: Ubuntu Cloud and Juju
---

### Post by ghfm on 2012-08-22
Hi All,

     We have installed eucalyptus 3.1.0 on ubuntu server 12.04 64 bit. But we are unable to open the web interface.

    It gives the message it works but we are unable to open the web interface.

Gerald H. Fernandes

---

### Post by sanderj on 2012-08-22
It would help if you would tell what you have tried, including technical some details. For example: which URL did you try?

Oh, and run this:

```
netstat -apon | grep -i listen | grep -vi listening

```

and post the output here.

---

### Post by ghfm on 2012-08-22
Thank you for your reply.  My url is [https://172.16.6.246:8443](https://172.16.6.246:8443) 

netstat -apon | grep -i listen | grep -vi listening

tcp        0      0 0.0.0.0:8777            0.0.0.0:*               LISTEN      1836/postgres    off (0.00/0/0)
tcp        0      0 172.16.6.246:43148      0.0.0.0:*               LISTEN      1692/eucalyptus-clo off (0.00/0/0)
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      1692/eucalyptus-clo off (0.00/0/0)
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1591/apache2     off (0.00/0/0)
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      1692/eucalyptus-clo off (0.00/0/0)
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      906/sshd         off (0.00/0/0)
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      4674/postgres    off (0.00/0/0)
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1514/master      off (0.00/0/0)
tcp        0      0 0.0.0.0:8443            0.0.0.0:*               LISTEN      1692/eucalyptus-clo off (0.00/0/0)
tcp        0      0 0.0.0.0:3260            0.0.0.0:*               LISTEN      1064/tgtd        off (0.00/0/0)
tcp        0      0 0.0.0.0:8773            0.0.0.0:*               LISTEN      1692/eucalyptus-clo off (0.00/0/0)
tcp        0      0 0.0.0.0:8774            0.0.0.0:*               LISTEN      1208/apache2     off (0.00/0/0)
tcp6       0      0 :::8777                 :::*                    LISTEN      1836/postgres    off (0.00/0/0)
tcp6       0      0 :::22                   :::*                    LISTEN      906/sshd         off (0.00/0/0)
tcp6       0      0 :::25                   :::*                    LISTEN      1514/master      off (0.00/0/0)
tcp6       0      0 :::3260                 :::*                    LISTEN      1064/tgtd        off (0.00/0/0)
 
Regards

Gerald H. F.

---

### Post by sanderj on 2012-08-22
Well, can you reach any of the other services, for example [http://172.16.6.246/](http://172.16.6.246/) ?

I can't reach that URL ... EDIT: it's an RFC1918 private address, so I can't test it for you.

EDIT:

Tips:

Can you reach [http://127.0.0.1/](http://127.0.0.1/) when logged on on the machine?
what's the output of "sudo iptables -L"
can you ping 172.16.6.246

---

### Post by ghfm on 2012-08-22
Hi,

    Now I am able to access my web interface after making modifications in eucalyptus.conf file with MANAGED NO-VLAN mode. 

   Now I want to register my components i.e. CC, Walrus, SC & NC. Please help.

   I am getting error while registering. the error is as follows :


/usr/sbin/euca_conf --register-walrus 172.16.6.246
No credentials found, attempting local authentication
RESPONSE true

Trying rsync to sync keys with 172.16.6.246
The authenticity of host '172.16.6.246 (172.16.6.246)' can't be established.
ECDSA key fingerprint is 68:61:3f:a5:e0:f0:27:67:9d:f5:1e:e3:a1:18:ee:b4.
Are you sure you want to continue connecting (yes/no)? no      
failed.

Trying scp to sync keys with 172.16.6.246 (user eucalyptus)
The authenticity of host '172.16.6.246 (172.16.6.246)' can't be established.
ECDSA key fingerprint is 68:61:3f:a5:e0:f0:27:67:9d:f5:1e:e3:a1:18:ee:b4.
Are you sure you want to continue connecting (yes/no)? ^C


   However, my status of walrus showing as enable. Will I get any problem later. 


   Thanks for your support  

Gerald

---

### Post by sanderj on 2012-08-22
I know nothing about eucalyptus itself (only about web interfaces), so I can't help you there.

---

