---
title: "stunnel help needed"
date: 2009-02-12
forum: Security
---

### Post by madman100 on 2009-02-12
hi can any one help me configure Evolution to work with stunnel here is my stunnel conf 

; Sample stunnel configuration file by Michal Trojnara 2002-2006
; Some options used here may not be adequate for your particular configuration
; Please make sure you understand them (especially the effect of chroot jail)

; Certificate/key is needed in server mode and optional in client mode
cert = /etc/stunnel/stunnel.pem
key = /etc/stunnel/stunnel.pem

; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = all

; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside chroot jail
pid = /stunnel4.pi

; Some performance tunings
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1
;compression = rle

; Workaround for Eudora bug
;options = DONT_INSERT_EMPTY_FRAGMENTS

; Authentication stuff
;verify = 2
; Don't forget to c_rehash CApath
; CApath is located inside chroot jail
;CApath = /certs
; It's often easier to use CAfile
;CAfile = /etc/stunnel/certs.pem
; Don't forget to c_rehash CRLpath
; CRLpath is located inside chroot jail
;CRLpath = /crls
; Alternatively you can use CRLfile
;CRLfile = /etc/stunnel/crls.pem

; Some debugging stuff useful for troubleshooting
debug = 7
output = /var/log/stunnel4/stunnel.log

; Use it for client mode
client = yes

; Service-level configuration

[pop3s]
accept  = 995
connect = 110

[imaps]
accept  = 993
connect = 143

[ssmtp]
accept  = 465
connect = 25

[https]
accept  = 443
connect = 80
TIMEOUTclose = 0


Thanks 
madman100

---

### Post by Mister.Vash on 2009-02-14
What exactly are you trying to do?  You can configure encrypted connections in Evolution itself.  A little more details would be good, such as if the connection to your mail server is pop/imap/other, and if your mail server supports encryption for it.  Usually stunnel is used in association with an application that does not provide the encryption features, for example, you have a really old mail program that doesn't support encrypted pop, you would then setup stunnel and connect the old client to.  You way be wanting to do something else, like just testing it, so that's why I was asking for more details.  Your stunnel.conf file is basically missing the name of the server that it would be connecting to and associated protocol

---

### Post by madman100 on 2009-02-14
Hi Mister.Vash thanks for the quick reply in have manage to get stunnel setup and it working i only wanted to encrypt the mail because my ips email does not support encryption  and syslog witch i have done now 

Thanks 
madman100:

---

