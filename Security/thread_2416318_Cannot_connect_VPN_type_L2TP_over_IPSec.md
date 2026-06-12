---
title: "Cannot connect VPN type L2TP over IPSec"
date: 2019-04-08
forum: Security
---

### Post by augustym on 2019-04-08
I followed thus tutorial to how to connect to a vpn [https://help.vpntunnel.com/support/solutions/articles/5000782608-vpntunnel-l2tp-installation-guide-for-ubuntu-18-04-](https://help.vpntunnel.com/support/solutions/articles/5000782608-vpntunnel-l2tp-installation-guide-for-ubuntu-18-04-) but I did not succeed...
I've tried so many things but it did not work... :(
Do you guys have any sugestions?
I've already run ike-scan and got this as result:
```
Enc=3DES Hash=SHA1 Group=2:modp1024 Auth=PSK
```
So, i know the phase algoritms are correct.
(It worked perfectly on windows)

```
Apr  8 19:42:00 Trabalho NetworkManager[904]: <info>  [1554763320.3277] audit: op="connection-activate" uuid="7b586978-5738-4f2c-bf8e-5d2a345ac888" name="MyVPN" pid=1681 uid=1000 result="success"Apr  8 19:42:00 Trabalho gnome-shell[1030]: JS ERROR: TypeError: item is undefined#012setActiveConnections/<@resource:///org/gnome/shell/ui/status/network.js:1518:17#012setActiveConnections@resource:///org/gnome/shell/ui/status/network.js:1515:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_syncVpnConnections@resource:///org/gnome/shell/ui/status/network.js:1853:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
Apr  8 19:42:00 Trabalho NetworkManager[904]: <info>  [1554763320.3392] vpn-connection[0x55e42d35a2d0,7b586978-5738-4f2c-bf8e-5d2a345ac888,"MyVPN",0]: Started the VPN service, PID 4609
Apr  8 19:42:00 Trabalho NetworkManager[904]: <info>  [1554763320.3507] vpn-connection[0x55e42d35a2d0,7b586978-5738-4f2c-bf8e-5d2a345ac888,"MyVPN",0]: Saw the service appear; activating connection
Apr  8 19:42:00 Trabalho NetworkManager[904]: <info>  [1554763320.5240] vpn-connection[0x55e42d35a2d0,7b586978-5738-4f2c-bf8e-5d2a345ac888,"MyVPN",0]: VPN connection: (ConnectInteractive) reply received
Apr  8 19:42:00 Trabalho nm-l2tp-service[4609]: Check port 1701
Apr  8 19:42:00 Trabalho NetworkManager[904]: Stopping strongSwan IPsec failed: starter is not running
Apr  8 19:42:02 Trabalho NetworkManager[904]: Starting strongSwan 5.6.2 IPsec [starter]...
Apr  8 19:42:02 Trabalho NetworkManager[904]: Loading config setup
Apr  8 19:42:02 Trabalho NetworkManager[904]: Loading conn '7b586978-5738-4f2c-bf8e-5d2a345ac888'
Apr  8 19:42:02 Trabalho NetworkManager[904]: found netkey IPsec stack
Apr  8 19:42:02 Trabalho charon: 00[DMN] Starting IKE charon daemon (strongSwan 5.6.2, Linux 4.18.0-17-generic, x86_64)
Apr  8 19:42:02 Trabalho charon: 00[CFG] loading ca certificates from '/etc/ipsec.d/cacerts'
Apr  8 19:42:02 Trabalho charon: 00[CFG] loading aa certificates from '/etc/ipsec.d/aacerts'
Apr  8 19:42:02 Trabalho charon: 00[CFG] loading ocsp signer certificates from '/etc/ipsec.d/ocspcerts'
Apr  8 19:42:02 Trabalho charon: 00[CFG] loading attribute certificates from '/etc/ipsec.d/acerts'
Apr  8 19:42:02 Trabalho charon: 00[CFG] loading crls from '/etc/ipsec.d/crls'
Apr  8 19:42:02 Trabalho charon: 00[CFG] loading secrets from '/etc/ipsec.secrets'
Apr  8 19:42:02 Trabalho charon: 00[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-49152f88-09ed-4033-be2e-98350ffb8994.secrets'
Apr  8 19:42:02 Trabalho charon: 00[CFG]   loaded IKE secret for %any
Apr  8 19:42:02 Trabalho charon: 00[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-4c017eb8-47e0-4134-9686-42a039ecc6ef.secrets'
Apr  8 19:42:02 Trabalho charon: 00[CFG]   loaded IKE secret for %any
Apr  8 19:42:02 Trabalho charon: 00[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-7b586978-5738-4f2c-bf8e-5d2a345ac888.secrets'
Apr  8 19:42:02 Trabalho charon: 00[CFG]   loaded IKE secret for %any
Apr  8 19:42:02 Trabalho charon: 00[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-b59c7db3-c02b-49d5-b403-47c74e9b8153.secrets'
Apr  8 19:42:02 Trabalho charon: 00[CFG]   loaded IKE secret for %any
Apr  8 19:42:02 Trabalho charon: 00[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-d2d9948e-db17-4160-a206-3dfa00bb9b86.secrets'
Apr  8 19:42:02 Trabalho charon: 00[CFG]   loaded IKE secret for %any
Apr  8 19:42:02 Trabalho charon: 00[LIB] loaded plugins: charon aesni aes rc2 sha2 sha1 md4 md5 mgf1 random nonce x509 revocation constraints pubkey pkcs1 pkcs7 pkcs8 pkcs12 pgp dnskey sshkey pem openssl fips-prf gmp agent xcbc hmac gcm attr kernel-netlink resolve socket-default connmark stroke updown eap-mschapv2 xauth-generic counters
Apr  8 19:42:02 Trabalho charon: 00[LIB] dropped capabilities, running as uid 0, gid 0
Apr  8 19:42:02 Trabalho charon: 00[JOB] spawning 16 worker threads
Apr  8 19:42:02 Trabalho charon: 06[CFG] received stroke: add connection '7b586978-5738-4f2c-bf8e-5d2a345ac888'
Apr  8 19:42:02 Trabalho charon: 06[CFG] added configuration '7b586978-5738-4f2c-bf8e-5d2a345ac888'
Apr  8 19:42:03 Trabalho charon: 07[CFG] rereading secrets
Apr  8 19:42:03 Trabalho charon: 07[CFG] loading secrets from '/etc/ipsec.secrets'
Apr  8 19:42:03 Trabalho charon: 07[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-49152f88-09ed-4033-be2e-98350ffb8994.secrets'
Apr  8 19:42:03 Trabalho charon: 07[CFG]   loaded IKE secret for %any
Apr  8 19:42:03 Trabalho charon: 07[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-4c017eb8-47e0-4134-9686-42a039ecc6ef.secrets'
Apr  8 19:42:03 Trabalho charon: 07[CFG]   loaded IKE secret for %any
Apr  8 19:42:03 Trabalho charon: 07[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-7b586978-5738-4f2c-bf8e-5d2a345ac888.secrets'
Apr  8 19:42:03 Trabalho charon: 07[CFG]   loaded IKE secret for %any
Apr  8 19:42:03 Trabalho charon: 07[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-b59c7db3-c02b-49d5-b403-47c74e9b8153.secrets'
Apr  8 19:42:03 Trabalho charon: 07[CFG]   loaded IKE secret for %any
Apr  8 19:42:03 Trabalho charon: 07[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-d2d9948e-db17-4160-a206-3dfa00bb9b86.secrets'
Apr  8 19:42:03 Trabalho charon: 07[CFG]   loaded IKE secret for %any
Apr  8 19:42:03 Trabalho charon: 10[CFG] received stroke: initiate '7b586978-5738-4f2c-bf8e-5d2a345ac888'
Apr  8 19:42:03 Trabalho charon: 11[IKE] initiating Main Mode IKE_SA 7b586978-5738-4f2c-bf8e-5d2a345ac888[1] to 143.121.23.5
Apr  8 19:42:03 Trabalho charon: 11[ENC] generating ID_PROT request 0 [ SA V V V V V ]
Apr  8 19:42:03 Trabalho charon: 11[NET] sending packet: from 192.168.25.218[500] to 143.121.23.5[500] (236 bytes)
Apr  8 19:42:03 Trabalho charon: 12[NET] received packet: from 143.121.23.5[500] to 192.168.25.218[500] (112 bytes)
Apr  8 19:42:03 Trabalho charon: 12[ENC] parsed ID_PROT response 0 [ SA V V ]
Apr  8 19:42:03 Trabalho charon: 12[ENC] received unknown vendor ID: 5b:36:2b:c8:20:f6:00:08
Apr  8 19:42:03 Trabalho charon: 12[IKE] received NAT-T (RFC 3947) vendor ID
Apr  8 19:42:03 Trabalho charon: 12[ENC] generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
Apr  8 19:42:03 Trabalho charon: 12[NET] sending packet: from 192.168.25.218[500] to 143.121.23.5[500] (244 bytes)
Apr  8 19:42:04 Trabalho charon: 13[NET] received packet: from 143.121.23.5[500] to 192.168.25.218[500] (276 bytes)
Apr  8 19:42:04 Trabalho charon: 13[ENC] parsed ID_PROT response 0 [ KE NAT-D NAT-D No V V V ]
Apr  8 19:42:04 Trabalho charon: 13[ENC] received unknown vendor ID: 40:4b:f4:39:52:2c:a3:f6
Apr  8 19:42:04 Trabalho charon: 13[IKE] received XAuth vendor ID
Apr  8 19:42:04 Trabalho charon: 13[IKE] received DPD vendor ID
Apr  8 19:42:04 Trabalho charon: 13[IKE] local host is behind NAT, sending keep alives
Apr  8 19:42:04 Trabalho charon: 13[ENC] generating ID_PROT request 0 [ ID HASH ]
Apr  8 19:42:04 Trabalho charon: 13[NET] sending packet: from 192.168.25.218[4500] to 143.121.23.5[4500] (68 bytes)
Apr  8 19:42:04 Trabalho charon: 14[NET] received packet: from 143.121.23.5[4500] to 192.168.25.218[4500] (76 bytes)
Apr  8 19:42:04 Trabalho charon: 14[IKE] queueing TRANSACTION request as tasks still active
Apr  8 19:42:08 Trabalho charon: 05[IKE] sending retransmit 1 of request message ID 0, seq 3
Apr  8 19:42:08 Trabalho charon: 05[NET] sending packet: from 192.168.25.218[4500] to143.121.23.5[4500] (68 bytes)
Apr  8 19:42:08 Trabalho charon: 06[NET] received packet: from 143.121.23.5[4500] to 192.168.25.218[4500] (92 bytes)
Apr  8 19:42:08 Trabalho charon: 06[ENC] payload type ID_V1 was not encrypted
Apr  8 19:42:08 Trabalho charon: 06[ENC] could not decrypt payloads
Apr  8 19:42:08 Trabalho charon: 06[IKE] integrity check failed
Apr  8 19:42:08 Trabalho charon: 06[ENC] generating INFORMATIONAL_V1 request 851551089 [ HASH N(INVAL_HASH) ]
Apr  8 19:42:08 Trabalho charon: 06[NET] sending packet: from 192.168.25.218[4500] to 143.121.23.5[4500] (68 bytes)
Apr  8 19:42:08 Trabalho charon: 06[IKE] ID_PROT response with message ID 0 processing failed
Apr  8 19:42:13 Trabalho NetworkManager[904]: Stopping strongSwan IPsec...
Apr  8 19:42:13 Trabalho charon: 00[DMN] signal of type SIGINT received. Shutting down
Apr  8 19:42:13 Trabalho charon: 00[IKE] destroying IKE_SA in state CONNECTING without notification
Apr  8 19:42:13 Trabalho NetworkManager[904]: initiating Main Mode IKE_SA 7b586978-5738-4f2c-bf8e-5d2a345ac888[1] to 143.121.23.5
Apr  8 19:42:13 Trabalho NetworkManager[904]: generating ID_PROT request 0 [ SA V V V V V ]
Apr  8 19:42:13 Trabalho NetworkManager[904]: sending packet: from 192.168.25.218[500] to 143.121.23.5[500] (236 bytes)
Apr  8 19:42:13 Trabalho NetworkManager[904]: received packet: from 143.121.23.5[500] to 192.168.25.218[500] (112 bytes)
Apr  8 19:42:13 Trabalho NetworkManager[904]: parsed ID_PROT response 0 [ SA V V ]
Apr  8 19:42:13 Trabalho NetworkManager[904]: received unknown vendor ID: 5b:36:2b:c8:20:f6:00:08
Apr  8 19:42:13 Trabalho NetworkManager[904]: received NAT-T (RFC 3947) vendor ID
Apr  8 19:42:13 Trabalho NetworkManager[904]: generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
Apr  8 19:42:13 Trabalho NetworkManager[904]: sending packet: from 192.168.25.218[500] to 143.121.23.5[500] (244 bytes)
Apr  8 19:42:13 Trabalho NetworkManager[904]: received packet: from 143.121.23.5[500] to 192.168.25.218[500] (276 bytes)
Apr  8 19:42:13 Trabalho NetworkManager[904]: parsed ID_PROT response 0 [ KE NAT-D NAT-D No V V V ]
Apr  8 19:42:13 Trabalho NetworkManager[904]: received unknown vendor ID: 40:4b:f4:39:52:2c:a3:f6
Apr  8 19:42:13 Trabalho NetworkManager[904]: received XAuth vendor ID
Apr  8 19:42:13 Trabalho NetworkManager[904]: received DPD vendor ID
Apr  8 19:42:13 Trabalho NetworkManager[904]: local host is behind NAT, sending keep alives
Apr  8 19:42:13 Trabalho NetworkManager[904]: generating ID_PROT request 0 [ ID HASH ]
Apr  8 19:42:13 Trabalho NetworkManager[904]: sending packet: from 192.168.25.218[4500] to 143.121.23.5[4500] (68 bytes)
Apr  8 19:42:13 Trabalho NetworkManager[904]: received packet: from 143.121.23.5[4500] to 192.168.25.218[4500] (76 bytes)
Apr  8 19:42:13 Trabalho NetworkManager[904]: queueing TRANSACTION request as tasks still active
Apr  8 19:42:13 Trabalho NetworkManager[904]: sending retransmit 1 of request message ID 0, seq 3
Apr  8 19:42:13 Trabalho NetworkManager[904]: sending packet: from 192.168.25.218[4500] to 143.121.23.5[4500] (68 bytes)
Apr  8 19:42:13 Trabalho NetworkManager[904]: received packet: from 143.121.23.5[4500] to 192.168.25.218[4500] (92 bytes)
Apr  8 19:42:13 Trabalho NetworkManager[904]: payload type ID_V1 was not encrypted
Apr  8 19:42:13 Trabalho NetworkManager[904]: could not decrypt payloads
Apr  8 19:42:13 Trabalho NetworkManager[904]: integrity check failed
Apr  8 19:42:13 Trabalho NetworkManager[904]: generating INFORMATIONAL_V1 request 851551089 [ HASH N(INVAL_HASH) ]
Apr  8 19:42:13 Trabalho NetworkManager[904]: sending packet: from 192.168.25.218[4500] to 143.121.23.5[4500] (68 bytes)
Apr  8 19:42:13 Trabalho NetworkManager[904]: ID_PROT response with message ID 0 processing failed
Apr  8 19:42:13 Trabalho NetworkManager[904]: destroying IKE_SA in state CONNECTING without notification
Apr  8 19:42:13 Trabalho NetworkManager[904]: establishing connection '7b586978-5738-4f2c-bf8e-5d2a345ac888' failed
Apr  8 19:42:13 Trabalho nm-l2tp-service[4609]: g_dbus_method_invocation_take_error: assertion 'error != NULL' failed
Apr  8 19:42:13 Trabalho NetworkManager[904]: <info>  [1554763333.6991] vpn-connection[0x55e42d35a2d0,7b586978-5738-4f2c-bf8e-5d2a345ac888,"MyVPN",0]: VPN plugin: state changed: stopped (6)
Apr  8 19:42:13 Trabalho NetworkManager[904]: <info>  [1554763333.7022] vpn-connection[0x55e42d35a2d0,7b586978-5738-4f2c-bf8e-5d2a345ac888,"MyVPN",0]: VPN service disappeared
Apr  8 19:42:13 Trabalho NetworkManager[904]: <warn>  [1554763333.7034] vpn-connection[0x55e42d35a2d0,7b586978-5738-4f2c-bf8e-5d2a345ac888,"MyVPN",0]: VPN connection: failed to connect: 'Message recipient disconnected from message bus without replying'
```

---

### Post by dkosovic on 2019-04-09
Regarding the "payload type ID_V1 was not encrypted" error, see :
[LIST]
[*][https://kevinlocke.name/bits/2017/08/26/strongswan-sonicwall-payload-type-id-v1-was-not-encrypted/](https://kevinlocke.name/bits/2017/08/26/strongswan-sonicwall-payload-type-id-v1-was-not-encrypted/)
[/LIST]
If the [FONT=monospace]/etc/strongswan.d/charon.conf[/FONT] modification workaround doesn't fix it, try replacing strongswan with libreswan which can be done with:

```
sudo apt install libreswan
```

I would also recommend removing the [FONT=monospace]/etc/ipsec.d/nm-l2tp-ipsec-*.secrets[/FONT]  transient files that weren't deleted and can have an impact, e.g:

```
sudo su -
rm -f /etc/ipsec.d/nm-l2tp-ipsec-*.secrets

```

---

### Post by augustym on 2019-04-12
> **dkosovic said:**
> Regarding the "payload type ID_V1 was not encrypted" error, see :
[LIST]
[*][https://kevinlocke.name/bits/2017/08/26/strongswan-sonicwall-payload-type-id-v1-was-not-encrypted/](https://kevinlocke.name/bits/2017/08/26/strongswan-sonicwall-payload-type-id-v1-was-not-encrypted/)
[/LIST]
If the [FONT=monospace]/etc/strongswan.d/charon.conf[/FONT] modification workaround doesn't fix it, try replacing strongswan with libreswan which can be done with:

```
sudo apt install libreswan
```

I would also recommend removing the [FONT=monospace]/etc/ipsec.d/nm-l2tp-ipsec-*.secrets[/FONT]  transient files that weren't deleted and can have an impact, e.g:

```
sudo su -
rm -f /etc/ipsec.d/nm-l2tp-ipsec-*.secrets

```

The first one didn't work, but the second one works fine.
Thank you! :)

---

### Post by lambertone on 2019-11-15
> **dkosovic said:**
> 
I would also recommend removing the [FONT=monospace]/etc/ipsec.d/nm-l2tp-ipsec-*.secrets[/FONT]  transient files that weren't deleted and can have an impact, e.g:

```
sudo su -
rm -f /etc/ipsec.d/nm-l2tp-ipsec-*.secrets

```

This helped me out today.  Thank you.

---

