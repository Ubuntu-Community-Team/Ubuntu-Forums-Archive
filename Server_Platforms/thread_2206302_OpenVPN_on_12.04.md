---
title: "OpenVPN on 12.04?"
date: 2014-02-18
forum: Server Platforms
---

### Post by d4m1r on 2014-02-18
Something is not right here....Not able to generate the certificates so I can't continue with setting up OpenVPN on a Ubuntu 12.04 VPS :confused:

```
damir@d4m1r:/etc/openvpn/easy-rsa$ cp openssl-1.0.0.cnf openssl.cnf
cp: cannot create regular file `openssl.cnf': Permission denied
damir@d4m1r:/etc/openvpn/easy-rsa$ sudo cp openssl-1.0.0.cnf openssl.cnf
damir@d4m1r:/etc/openvpn/easy-rsa$ sudo nano vars
damir@d4m1r:/etc/openvpn/easy-rsa$ source vars
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/keys
damir@d4m1r:/etc/openvpn/easy-rsa$ sudo source vars
sudo: source: command not found
damir@d4m1r:/etc/openvpn/easy-rsa$ ./clean-all
mkdir: cannot create directory `/etc/openvpn/easy-rsa/keys': Permission denied
damir@d4m1r:/etc/openvpn/easy-rsa$ sudo ./clean-all
Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.
damir@d4m1r:/etc/openvpn/easy-rsa$ source ./vars
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/keys
damir@d4m1r:/etc/openvpn/easy-rsa$ sudo ./clean-all
Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.

```

And yes, I have already editing the vars file (for location, cn, etc) so I don't know whats wrong...

---

### Post by sandyd on 2014-02-18
> **d4m1r said:**
> Something is not right here....Not able to generate the certificates so I can't continue with setting up OpenVPN on a Ubuntu 12.04 VPS :confused:

```
damir@d4m1r:/etc/openvpn/easy-rsa$ cp openssl-1.0.0.cnf openssl.cnf
cp: cannot create regular file `openssl.cnf': Permission denied
damir@d4m1r:/etc/openvpn/easy-rsa$ sudo cp openssl-1.0.0.cnf openssl.cnf
damir@d4m1r:/etc/openvpn/easy-rsa$ sudo nano vars
damir@d4m1r:/etc/openvpn/easy-rsa$ source vars
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/keys
damir@d4m1r:/etc/openvpn/easy-rsa$ sudo source vars
sudo: source: command not found
damir@d4m1r:/etc/openvpn/easy-rsa$ ./clean-all
mkdir: cannot create directory `/etc/openvpn/easy-rsa/keys': Permission denied
damir@d4m1r:/etc/openvpn/easy-rsa$ sudo ./clean-all
Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.
damir@d4m1r:/etc/openvpn/easy-rsa$ source ./vars
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/keys
damir@d4m1r:/etc/openvpn/easy-rsa$ sudo ./clean-all
Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.

```

And yes, I have already editing the vars file (for location, cn, etc) so I don't know whats wrong...
copy to your own home folder and chown to your user, and then run the scripts without sudo

---

### Post by d4m1r on 2014-02-18
Thanks, I figured it was permissions related :)

Now new issue....

```

failed to update database
TXT_DB error number 2

```

Seems to be related to creating keys/certificates with duplicate data in some fields BUT I've tried to scrap all the keys I've created so far to start again (running vars, clean-all, removing keys folder, etc) but I am getting this regardless of how many times I retry...

---

### Post by nerdtron on 2014-02-18
Run all related commands as root. Or perhaps login as root temporarily.
I have just setup an OpenVPN server with certificates for our mikrotik routers. Would you like to see my manual on setting up OpenVPN?

---

### Post by d4m1r on 2014-02-19
No thanks :P

I don't think it is advisable to install OpenVPN as root. As someone previously mentioned, my non-root user should be the owner for security purposes.

---

### Post by d4m1r on 2014-02-20
> **d4m1r said:**
> 
Now new issue....

```

failed to update database
TXT_DB error number 2

```

Seems to be related to creating keys/certificates with duplicate data in some fields BUT I've tried to scrap all the keys I've created so far to start again (running vars, clean-all, removing keys folder, etc) but I am getting this regardless of how many times I retry...

Any other suggestions on how to correct this?

---

### Post by amish_otaku on 2014-03-05
I believe this might have something to do with the index.txt or index.html file in one of the subfolders. Also can you point me to where you're going to do all of the certs and everything... I'd like to see how your process is to provide better help.

---

