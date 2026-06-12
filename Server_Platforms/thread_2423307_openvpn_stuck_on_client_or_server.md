---
title: "openvpn stuck on client or server"
date: 2019-07-20
forum: Server Platforms
---

### Post by fredy50 on 2019-07-20
Hello People

I trying to setup a OpenVPN server and connect to server from client

[HTML]*Tunnelblick: macOS 10.14.5; Tunnelblick 3.7.9beta01 (build 5190)
2019-07-20 22:13:37 *Tunnelblick: Attempting connection with client6 using shadow copy; Set nameserver = 771; monitoring connection
2019-07-20 22:13:37 *Tunnelblick: openvpnstart start client6.tblk 57935 771 0 1 0 1065264 -ptADGNWradsgnw 2.4.6-openssl-1.0.2q
2019-07-20 22:13:37 *Tunnelblick: openvpnstart log:
     Warning: Tunnelblick is using 'openvpn-down-root.so', so the route-pre-down script will not be used. You can override this by providing a custom route-pre-down script (which may be a copy of Tunnelblick's standard route-pre-down script) in a Tunnelblick VPN Configuration. However, that script will not be executed as root unless the 'user' and 'group' options are removed from the OpenVPN configuration file. If the 'user' and 'group' options are removed, then you don't need to use a custom route-pre-down script.OpenVPN started successfully. Command used to start OpenVPN (one argument per displayed line):
     
          /Applications/Tunnelblick.app/Contents/Resources/openvpn/openvpn-2.4.6-openssl-1.0.2q/openvpn
          --daemon
          --log /Library/Application Support/Tunnelblick/Logs/-SUsers-Sfrederikfrandsen-SLibrary-SApplication Support-STunnelblick-SConfigurations-Sclient6.tblk-SContents-SResources-Sconfig.ovpn.771_0_1_0_1065264.57935.openvpn.log
          --cd /Library/Application Support/Tunnelblick/Users/frederikfrandsen/client6.tblk/Contents/Resources
          --setenv IV_GUI_VER "net.tunnelblick.tunnelblick 5190 3.7.9beta01 (build 5190)"
          --verb 3
          --config /Library/Application Support/Tunnelblick/Users/frederikfrandsen/client6.tblk/Contents/Resources/config.ovpn
          --setenv TUNNELBLICK_CONFIG_FOLDER /Library/Application Support/Tunnelblick/Users/frederikfrandsen/client6.tblk/Contents/Resources
          --verb 3
          --cd /Library/Application Support/Tunnelblick/Users/frederikfrandsen/client6.tblk/Contents/Resources
          --management 127.0.0.1 57935 /Library/Application Support/Tunnelblick/ohfjnkecnccmlcmgndpnhlhjokofddgckmkhnhog.mip
          --management-query-passwords
          --management-hold
          --script-security 2
          --up /Applications/Tunnelblick.app/Contents/Resources/client.up.tunnelblick.sh -9 -d -f -m -w -ptADGNWradsgnw
          --plugin /Applications/Tunnelblick.app/Contents/Resources/openvpn/openvpn-2.4.6-openssl-1.0.2q/openvpn-down-root.so /Applications/Tunnelblick.app/Contents/Resources/client.down.tunnelblick.sh -9 -d -f -m -w -ptADGNWradsgnw

2019-07-20 22:13:37 *Tunnelblick: openvpnstart starting OpenVPN
2019-07-20 22:13:37 *Tunnelblick: Established communication with OpenVPN
2019-07-20 22:13:37 OpenVPN 2.4.6 x86_64-apple-darwin [SSL (OpenSSL)] [LZO] [LZ4] [PKCS11] [MH/RECVDA] [AEAD] built on Nov 29 2018
2019-07-20 22:13:37 library versions: OpenSSL 1.0.2q  20 Nov 2018, LZO 2.10
2019-07-20 22:13:37 MANAGEMENT: TCP Socket listening on [AF_INET]127.0.0.1:57935
2019-07-20 22:13:37 Need hold release from management interface, waiting...
2019-07-20 22:13:37 MANAGEMENT: Client connected from [AF_INET]127.0.0.1:57935
2019-07-20 22:13:37 MANAGEMENT: CMD 'pid'
2019-07-20 22:13:37 MANAGEMENT: CMD 'auth-retry interact'
2019-07-20 22:13:37 >INFO:OpenVPN Management Interface Version 1 -- type 'help' for more info
2019-07-20 22:13:37 MANAGEMENT: CMD 'state on'
2019-07-20 22:13:37 MANAGEMENT: CMD 'state'
2019-07-20 22:13:37 MANAGEMENT: CMD 'bytecount 1'
2019-07-20 22:13:37 MANAGEMENT: CMD 'hold release'
2019-07-20 22:13:37 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
2019-07-20 22:13:37 PLUGIN_INIT: POST /Applications/Tunnelblick.app/Contents/Resources/openvpn/openvpn-2.4.6-openssl-1.0.2q/openvpn-down-root.so '[/Applications/Tunnelblick.app/Contents/Resources/openvpn/openvpn-2.4.6-openssl-1.0.2q/openvpn-down-root.so] [/Applications/Tunnelblick.app/Contents/Resources/client.down.tunnelblick.sh] [-9] [-d] [-f] [-m] [-w] [-ptADGNWradsgnw]' intercepted=PLUGIN_UP|PLUGIN_DOWN 
2019-07-20 22:13:42 MANAGEMENT: CMD 'password [...]'
2019-07-20 22:13:42 Outgoing Control Channel Authentication: Using 256 bit message hash 'SHA256' for HMAC authentication
2019-07-20 22:13:42 Incoming Control Channel Authentication: Using 256 bit message hash 'SHA256' for HMAC authentication
2019-07-20 22:13:42 MANAGEMENT: >STATE:1563653622,RESOLVE,,,,,,
2019-07-20 22:13:42 TCP/UDP: Preserving recently used remote address: [AF_INET]185.10.223.50:1194
2019-07-20 22:13:42 Socket Buffers: R=[786896->786896] S=[9216->9216]
2019-07-20 22:13:42 UDP link local: (not bound)
2019-07-20 22:13:42 UDP link remote: [AF_INET]x.x.x.x:1194
2019-07-20 22:13:42 NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
2019-07-20 22:13:42 MANAGEMENT: >STATE:1563653622,WAIT,,,,,,
2019-07-20 22:14:27 *Tunnelblick: Disconnecting; VPN Details&#8230; window disconnect button pressed
2019-07-20 22:14:27 *Tunnelblick: No 'pre-disconnect.sh' script to execute
2019-07-20 22:14:27 *Tunnelblick: Disconnecting using 'kill'
2019-07-20 22:14:28 event_wait : Interrupted system call (code=4)
2019-07-20 22:14:28 PLUGIN_CLOSE: /Applications/Tunnelblick.app/Contents/Resources/openvpn/openvpn-2.4.6-openssl-1.0.2q/openvpn-down-root.so
2019-07-20 22:14:28 SIGTERM[hard,] received, process exiting
2019-07-20 22:14:28 MANAGEMENT: >STATE:1563653668,EXITING,SIGTERM,,,,,
2019-07-20 22:14:28 *Tunnelblick: No 'post-disconnect.sh' script to execute
2019-07-20 22:14:29 *Tunnelblick: Expected disconnection occurred.[/HTML]

but i have follow this guide ([https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04))

Can some one help me ?

---

### Post by wildmanne39 on 2019-07-20
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by volkswagner on 2019-07-21
Your post is a bit light on information. It's great that you posted logging info.

You didn't even post the symptom. According to the logs, it says "you pressed the disconnect button" is this true?

Please post server config and client config.

When posting info on the Internet, you should be aware of exposure.
You posted the public ip of the server (in the logs). When possible you should
mask such info, so when you post your configs, you can mask the public ip.

One thing of interest is:

```
2019-07-20 22:13:37 *Tunnelblick: openvpnstart log:
     Warning: Tunnelblick is using 'openvpn-down-root.so', so the route-pre-down script will not be used. You can override this by providing a custom route-pre-down script (which may be a copy of Tunnelblick's standard route-pre-down script) in a Tunnelblick VPN Configuration. However, that script will not be executed as root unless the 'user' and 'group' options are removed from the OpenVPN configuration file. If the 'user' and 'group' options are removed, then you don't need to use a custom route-pre-down script.OpenVPN started successfully. Command used to start OpenVPN (one argument per displayed line):

```

You may want to research that error. 
I use Tunnelblick... I've never run into that. 
How are you launching the app? How did you install the app?

When connecting to the VPN please do an ifconfig on the client to see if it's getting an ip address.

Also please post the logs from the server when connecting.

---

### Post by fredy50 on 2019-07-22
Hello

I found a script to run this openVPN without pass, how can i add password to in ?
[https://raw.githubusercontent.com/Nyr/openvpn-install/a6048d509fff11c28cbabc36633f76c1ac5ce988/openvpn-install.sh](https://raw.githubusercontent.com/Nyr/openvpn-install/a6048d509fff11c28cbabc36633f76c1ac5ce988/openvpn-install.sh)

---

### Post by volkswagner on 2019-07-22
You've gone fractal @Fredy50.

---

### Post by TheFu on 2019-07-22
> **volkswagner said:**
> You've gone fractal @Fredy50.

Can't you read minds, volkswagner?

---

### Post by fredy50 on 2019-07-23
Hello people,

i found out i'm on 16.04 ubuntu.
  i found this script here:


[https://raw.githubusercontent.com/Nyr/openvpn-install/a6048d509fff11c28cbabc36633f76c1ac5ce988/openvpn-install.sh](https://raw.githubusercontent.com/Nyr/openvpn-install/a6048d509fff11c28cbabc36633f76c1ac5ce988/openvpn-install.sh)

so i can create a openVPN with this script but the problem with this are no security in that next step :)

That works for me :)

---

