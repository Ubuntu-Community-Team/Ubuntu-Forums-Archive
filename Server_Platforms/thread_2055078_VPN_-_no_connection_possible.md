---
title: "VPN - no connection possible"
date: 2012-09-08
forum: Server Platforms
---

### Post by SeaKing on 2012-09-08
Hello,

I've tried to set up a simple VPN Server on my router using this [page]("http://www.hermann-uwe.de/blog/howto-using-openvpn-on-debian-gnu-linux") but I get those error messages:

client log:
```

Sep  8 18:42:31 nightmare ovpn-client[12170]: WARNING: you are using user/group/chroot/setcon without persist-tun -- this may cause restarts to fail
Sep  8 18:42:31 nightmare ovpn-client[12170]: NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sep  8 18:42:31 nightmare ovpn-client[12170]: Re-using SSL/TLS context
Sep  8 18:42:31 nightmare ovpn-client[12170]: LZO compression initialized
Sep  8 18:42:31 nightmare ovpn-client[12170]: Control Channel MTU parms [ L:1544 D:168 EF:68 EB:0 ET:0 EL:0 ]
Sep  8 18:42:31 nightmare ovpn-client[12170]: Socket Buffers: R=[87380->131072] S=[16384->131072]
Sep  8 18:42:31 nightmare ovpn-client[12170]: Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Sep  8 18:42:31 nightmare ovpn-client[12170]: Local Options hash (VER=V4): 'ee93268d'
Sep  8 18:42:31 nightmare ovpn-client[12170]: Expected Remote Options hash (VER=V4): 'bd577cd1'
Sep  8 18:42:31 nightmare ovpn-client[12170]: Attempting to establish TCP connection with [AF_INET]192.168.1.1:5555 [nonblock]
Sep  8 18:42:32 nightmare ovpn-client[12170]: TCP connection established with [AF_INET]192.168.1.1:5555
Sep  8 18:42:32 nightmare ovpn-client[12170]: TCPv4_CLIENT link local: [undef]
Sep  8 18:42:32 nightmare ovpn-client[12170]: TCPv4_CLIENT link remote: [AF_INET]192.168.1.1:5555
Sep  8 18:42:32 nightmare ovpn-client[12170]: TLS: Initial packet from [AF_INET]192.168.1.1:5555, sid=eff41b02 0dcf9d7c
Sep  8 18:42:32 nightmare ovpn-client[12170]: VERIFY ERROR: depth=1, error=**certificate is not yet valid**: /C=xx/ST=xx/L=xxg/O=xx/CN=xx/emailAddress=xx
Sep  8 18:42:32 nightmare ovpn-client[12170]: TLS_ERROR: BIO read tls_read_plaintext error: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:**certificate verify failed**
Sep  8 18:42:32 nightmare ovpn-client[12170]: TLS Error: TLS object -> incoming plaintext read error
Sep  8 18:42:32 nightmare ovpn-client[12170]: TLS Error: TLS handshake failed
Sep  8 18:42:32 nightmare ovpn-client[12170]: Fatal TLS error (check_tls_errors_co), restarting
Sep  8 18:42:32 nightmare ovpn-client[12170]: TCP/UDP: Closing socket
Sep  8 18:42:32 nightmare ovpn-client[12170]: SIGUSR1[soft,tls-error] received, process restarting
Sep  8 18:42:32 nightmare ovpn-client[12170]: Restart pause, 5 second(s)

```I set up another pair of keys but it didn't changed anything.
I also tried openvpn plugin for gnome-network-manager but it also failed. Where's the mistake?

---

### Post by SeaKing on 2012-09-09
I googled a bit and other seem to have the same problem and they fixed it by synchronizing the time of server and client. I did so but the problems still appears.

---

### Post by SeijiSensei on 2012-09-10
> **SeaKing said:**
> I googled a bit and other seem to have the same problem and they fixed it by synchronizing the time of server and client. I did so but the problems still appears.

Do you still get "error=certificate is not yet valid" after fixing the clocks?  Maybe you should regenerate the certificate.

---

