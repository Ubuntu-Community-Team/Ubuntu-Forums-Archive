---
title: "Error when setting up openvpn-server using gadmin tools"
date: 2010-12-20
forum: Server Platforms
---

### Post by quadra on 2010-12-20
Hi there

Ubuntu 10.04; I made a fresh install of gadmin-openvpn-server, the GUI tool for configuring OpenVPN server. In the "Server settings" tab, I configured my server. When trying to activate the server, I get the following error. What shall I do?

> Mon Dec 20 15:37:36 2010 OpenVPN 2.1.0 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Mon Dec 20 15:37:36 2010 NOTE: when bridging your LAN adapter with the TAP adapter, note that the new bridge adapter will often take on its own IP address that is different from what the LAN adapter was previously set to
Mon Dec 20 15:37:36 2010 WARNING: using --duplicate-cn and --client-config-dir together is probably not what you want
Mon Dec 20 15:37:36 2010 NOTE: your local LAN uses the extremely common subnet address 192.168.0.x or 192.168.1.x.  Be aware that this might create routing conflicts if you connect to the VPN server from public locations such as internet cafes that use the same subnet.
Mon Dec 20 15:37:36 2010 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Mon Dec 20 15:37:36 2010 PLUGIN_INIT: POST /usr/lib/openvpn/openvpn-pam-auth.so '[/usr/lib/openvpn/openvpn-pam-auth.so] [login]' intercepted=PLUGIN_AUTH_USER_PASS_VERIFY 
Mon Dec 20 15:37:36 2010 Diffie-Hellman initialized with 1024 bit key
Mon Dec 20 15:37:36 2010 WARNING: file 'certs/key.pem' is group or others accessible
Mon Dec 20 15:37:36 2010 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Mon Dec 20 15:37:37 2010 Control Channel Authentication: using 'certs/ta.key' as a OpenVPN static key file
Mon Dec 20 15:37:37 2010 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Dec 20 15:37:37 2010 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Dec 20 15:37:37 2010 TLS-Auth MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ]
Mon Dec 20 15:37:37 2010 TUN/TAP device tap0 opened
Mon Dec 20 15:37:37 2010 TUN/TAP TX queue length set to 100
Mon Dec 20 15:37:37 2010 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
**Mon Dec 20 15:37:37 2010 Open error on pid file /var/run/openvpn/openvpn.pid: No such file or directory (errno=2)**
Mon Dec 20 15:37:37 2010 Exiting

(Note that I already solved a first problem, initially in this log I got an error about a missing file called **openvpn-auth-pam.so**, the expected file was in the same directory but it had another name, so I created a symlink to solve)

From the above log, it seems that the pid file of the openvpn process is either not created or not found. Maybe it's created at another place? Any help would be welcome.

---

