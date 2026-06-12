---
title: "Cannot search for images in UEC Store tab"
date: 2011-09-02
forum: Ubuntu Cloud and Juju
---

### Post by herrvendil on 2011-09-02
Hi

I have been trying to install UEC (both 10.04 and now 11.04) for a couple of days but when following the installation guide and want to search for an image in the Store in the Web UI I get the error:

'Error 60: server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none'

Anyone got a hint on how to resolve this?

---

### Post by herrvendil on 2011-09-02
I have checked what is called by the server when clicking och the Search button on the 'Store' tab by using tcpdump and it seems that it tries to connect to [https://barbadine.canonical.com/](https://barbadine.canonical.com/).

This works great when trying  with a mozilla browser on my desktop but when trying with wget on the server I get. 
  Verify return code: 21 (unable to verify the first certificate)

No-one else with the same problem?

---

### Post by Stryderking on 2011-09-05
I am having the same issue. I don't even know where to start! but here is a extra bump.:guitar:

i get this

Error 60: server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none

---

### Post by johngreth on 2011-09-05
Same here. I've only tried 11.04. Installing updates didn't help.

---

### Post by jruiz@tecsisa.com on 2011-09-06
Try updating godaddy certificates:

```
sudo wget -P /usr/local/share/ca-certificates/ --no-check-certificate https://certs.godaddy.com/repository/gd-class2-root.crt https://certs.godaddy.com/repository/gd_intermediate.crt https://certs.godaddy.com/repository/gd_cross_intermediate.crt
sudo  update-ca-certificates

```

---

### Post by jruiz@tecsisa.com on 2011-09-06
**Quick and insecure fix**
WARNING: the change disables certificate validation. Use at your own risk!!

Until PycURL is fixed you can edit file /usr/lib/python2.7/dist-packages/imagestore/lib/fetch.py
on fetch method after the line 142
add

```
curl.setopt(pycurl.SSL_VERIFYPEER, 0)
curl.setopt(pycurl.SSL_VERIFYHOST, 0)

```
Restart the image-store-proxy

---

### Post by johngreth on 2011-09-06
That second fix allowed me to see the available images, but then when I try to install one I get: "Proxy failed to retrieve Eucalyptus credentials".

Any ideas?

---

### Post by johngreth on 2011-09-06
I got it to download. I had to register the localhost as the walrus server. Could that have been the problem all along?

---

### Post by piogomez on 2011-09-14
@johngreth

I've been following this thread for some time because i've been having the same trouble. could you please elaborate on setting localhost on walrus as a solution? thanks.

---

### Post by johngreth on 2011-09-14
Under the configuration tab in the web interface there is a Walrus box. In that box you can set the address to "localhost" or 127.0.0.1. I've given up working on it for a while so I don't have it running. Otherwise I would be more specific.

---

### Post by tetsuharu on 2011-09-28
I realize this is several months late.

The problem is definitely with Walrus, but you can't set it to localhost or 127.0.0.1

Once I set the Walrus server to the interface's IP address that Walrus is running on everything went smoothly. 

Walrus apparently does not listen on the loopback interface.

---

### Post by xueliangfei on 2011-10-17
> **johngreth said:**
> Under the configuration tab in the web interface there is a Walrus box. In that box you can set the address to "localhost" or 127.0.0.1. I've given up working on it for a while so I don't have it running. Otherwise I would be more specific.
 
 
Can you elaborate any good solutions to the problem?
Thanks. I have got the same problem.

---

### Post by galbatrox on 2011-10-19
I would also like to see a solution for this problem. Cannot enter store.

---

### Post by vimb on 2011-12-13
Okay, I ran into this exact same problem with a vanilla install of UEC from 11.04 x64 server CD.

Short answer on how to fix it - rebuild/reinstall python-pycurl using libopenssl rather than libgnutls:
[URL="http://osdir.com/ml/debian-bugs-dist/2009-05/msg06613.html"]http://osdir.com/ml/debian-bugs-dist/2009-05/msg06613.html
[/URL]
Note that those directions are for an older version of python-pycurl, so update version numbers appropriately. But all of the steps are the same. Once you do this and restart everything, the store should work.

Basic problem is that there is something wonky about the godaddy CA cert that imagestore.canonical.com is signed with.
You can isolate the issue with:
```
gnutls-cli --x509cafile /etc/ssl/certs/ca-certificates.crt imagestore.canonical.com
```

It appears gnutls (as of some recent update) became a little more picky about which CA certs it accepts than openssl. 

An alternative client-side fix (which I have not tried) might be to enable the GNUTLS_VERIFY_ALLOW_X509_V1_CA_CRT option for libcurl, however this also requires modifying packages. 

I think the proper server-side fix would be for imagestore.canonical.com to get a new server cert that is signed by a newer godaddy CA cert that doesn't trigger the gnutls issues. But I have no control over this.

---

