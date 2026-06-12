---
title: "crl.pem permission denied for Openvpn Server"
date: 2018-01-24
forum: Server Platforms
---

### Post by secoonder on 2018-01-24
i am Using Ubuntu 14.04 . i installed OPen Vpn Server three year ago. i am using site to site Vpn.it works properly.
Server.conf is
> port 1194tun-mtu 1400tls-serverproto tcpdev tunca  /etc/openvpn/easy-rsa/keys/ca.crtcert /etc/openvpn/easy-rsa/keys/firewall.crtkey /etc/openvpn/easy-rsa/keys/firewall.keydh /etc/openvpn/easy-rsa/keys/dh2048.pemserver 10.2.1.0 255.255.255.0ifconfig-pool-persist ipp.txt 600push "route 192.168.x.0 255.255.255.0"client-config-dir /etc/openvpn/ccdpush "dhcp-option DNS m.n.o.p"push "dhcp-option DNS d.e.f.g"client-to-clientkeepalive 20 60comp-lzomax-clients 100user nobodygroup nogrouppersist-keypersist-tunstatus /var/log/openvpn-status.loglog-append  /var/log/openvpn.logverb 3


i want to revoke certificates that they left the company.
i added server.conf

> crl.pem /etc/openvpn/easy-rsa/keys/

i revoke the one certificate.

>   source ./vars
./revoke-full user1
Revoking Certificate 03.
Data Base UpdatedWhen i restart openvpn, i took an error
> CRL: cannot read: /etc/openvpn/easy-rsa/keys/crl.pem: Permission denied (errno=13)

i set chmod777 crl.pem.but i took an error.
> drwx------ 2 root root  4096 Oca 22 22:17 keys



i dont want to add below command
> sudo chown -R nobody /etc/openvpn/easy-rsa/keys
Because this command create a security problem .Because all vpn files owned nobody ,not root.

Do you have any idea ?
Thank you very much for your help

---

### Post by darkod on 2018-01-24
Why are you using the crl.pem parameter in the server.conf? I haven't worked with it, but according to the Ubuntu Server instructions it is not needed.
[https://help.ubuntu.com/14.04/serverguide/openvpn.html](https://help.ubuntu.com/14.04/serverguide/openvpn.html)

There is no mention or crl.pem in the default config.

Have you tried without that line?

I think it works without that parameter.

---

### Post by secoonder on 2018-02-02
[COLOR=#212121][FONT=arial]To Cancel the certificate of someone who has left the job.And then for security.
i solved the problem .
When i canceled the someone certificated, i used  the commands.
./revoke-full client1
cd /etc/openvpn/easy-rsa/keys
cp cerl.pem /etc/openvpn/

Thank you.[/FONT][/COLOR]

---

