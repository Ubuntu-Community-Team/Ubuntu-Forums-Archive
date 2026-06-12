---
title: "iptables openvpn killswitch 2 - QNAP LXC VM - NordVPN"
date: 2020-12-22
forum: Server Platforms
---

### Post by oner-erol on 2020-12-22
Hi,

Merry Christmas 2020! :-)

I have been trying to recreate this on a QNAP NAS: I used Container-Station to create an LXC Ubuntu 18.04 VM.
[https://ubuntuforums.org/showthread.php?t=2399250](https://ubuntuforums.org/showthread.php?t=2399250)

Here is the error I am getting on connection:
> 
[COLOR=#000000][I]write UDP: Operation not permitted (code=1)
[/I][/COLOR]

IF I QUOTE THE FOLLOWING IN "[COLOR=#000000]iptable.sh" [/COLOR]IT WORKS.
So I guess there is an OUTPUT that I should allow?
> 
#iptables -P OUTPUT DROP


Could you please help me understand what I am doing wrong?
Thanks a lot

Here is iptable.sh
> 
#!/bin/bash
# Flush
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X

# Block All
iptables -P OUTPUT DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP

# allow Localhost
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# Make sure you can communicate with any DHCP server
iptables -A OUTPUT -d 255.255.255.255 -j ACCEPT
iptables -A INPUT -s 255.255.255.255 -j ACCEPT

# Make sure that you can communicate within your own network
iptables -A INPUT -s 192.168.1.0/24 -d 192.168.1.0/24 -j ACCEPT
iptables -A OUTPUT -s 192.168.1.0/24 -d 192.168.1.0/24 -j ACCEPT

# Allow established sessions to receive traffic:
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow TUN
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A FORWARD -o tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE
iptables -A OUTPUT -o tun+ -j ACCEPT

# allow VPN connection
iptables -I OUTPUT 1 -p udp --destination-port 1194 -m comment --comment "Allow VPN connection" -j ACCEPT

# Block All
iptables -A OUTPUT -j DROP
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP

# Log all dropped packages, debug only.
iptables -N logging
iptables -A INPUT -j logging
iptables -A OUTPUT -j logging
iptables -A logging -m limit --limit 2/min -j LOG --log-prefix "IPTables general: " --log-level 7
iptables -A logging -j DROP

echo "saving"
iptables-save > /etc/iptables.rules
echo "done"


Here is my connection script:
> 
# I put this as apparently there is a problem with tun in LXC VM
# I get connection when not using iptable
mkdir -p /dev/net
mknod /dev/net/tun c 10 200
chmod 600 /dev/net/tun

sudo openvpn --config "/etc/openvpn/ovpn_udp/au709.nordvpn.com.udp.ovpn" --auth-user-pass /etc/openvpn/auth.txt


Here is au709.nordvpn.com.udp.ovpn
> 
client
dev tun
proto udp
remote 217.138.205.251 1194
resolv-retry infinite
remote-random
nobind
tun-mtu 1500
tun-mtu-extra 32
mssfix 1450
persist-key
persist-tun
ping 15
ping-restart 0
ping-timer-rem
reneg-sec 0
comp-lzo no


remote-cert-tls server


auth-user-pass
verb 3
pull
fast-io
cipher AES-256-CBC
auth SHA512
<ca>
-----BEGIN CERTIFICATE-----
MIIFCjCCAvKgAwIBAgIBATANBgkqhkiG9w0BAQ0FADA5MQswCQYDVQQGEwJQQTEQ
MA4GA1UEChMHTm9yZFZQTjEYMBYGA1UEAxMPTm9yZFZQTiBSb290IENBMB4XDTE2
MDEwMTAwMDAwMFoXDTM1MTIzMTIzNTk1OVowOTELMAkGA1UEBhMCUEExEDAOBgNV
BAoTB05vcmRWUE4xGDAWBgNVBAMTD05vcmRWUE4gUm9vdCBDQTCCAiIwDQYJKoZI
hvcNAQEBBQADggIPADCCAgoCggIBAMkr/BYhyo0F2upsIMXwC6QvkZps3NN2/eQF
kfQIS1gql0aejsKsEnmY0Kaon8uZCTXPsRH1gQNgg5D2gixdd1mJUvV3dE3y9FJr
XMoDkXdCGBodvKJyU6lcfEVF6/UxHcbBguZK9UtRHS9eJYm3rpL/5huQMCppX7kU
eQ8dpCwd3iKITqwd1ZudDqsWaU0vqzC2H55IyaZ/5/TnCk31Q1UP6BksbbuRcwOV
skEDsm6YoWDnn/IIzGOYnFJRzQH5jTz3j1QBvRIuQuBuvUkfhx1FEwhwZigrcxXu
MP+QgM54kezgziJUaZcOM2zF3lvrwMvXDMfNeIoJABv9ljw969xQ8czQCU5lMVmA
37ltv5Ec9U5hZuwk/9QO1Z+d/r6Jx0mlurS8gnCAKJgwa3kyZw6e4FZ8mYL4vpRR
hPdvRTWCMJkeB4yBHyhxUmTRgJHm6YR3D6hcFAc9cQcTEl/I60tMdz33G6m0O42s
Qt/+AR3YCY/RusWVBJB/qNS94EtNtj8iaebCQW1jHAhvGmFILVR9lzD0EzWKHkvy
WEjmUVRgCDd6Ne3eFRNS73gdv/C3l5boYySeu4exkEYVxVRn8DhCxs0MnkMHWFK6
MyzXCCn+JnWFDYPfDKHvpff/kLDobtPBf+Lbch5wQy9quY27xaj0XwLyjOltpiST
LWae/Q4vAgMBAAGjHTAbMAwGA1UdEwQFMAMBAf8wCwYDVR0PBAQDAgEGMA0GCSqG
SIb3DQEBDQUAA4ICAQC9fUL2sZPxIN2mD32VeNySTgZlCEdVmlq471o/bDMP4B8g
nQesFRtXY2ZCjs50Jm73B2LViL9qlREmI6vE5IC8IsRBJSV4ce1WYxyXro5rmVg/
k6a10rlsbK/eg//GHoJxDdXDOokLUSnxt7gk3QKpX6eCdh67p0PuWm/7WUJQxH2S
DxsT9vB/iZriTIEe/ILoOQF0Aqp7AgNCcLcLAmbxXQkXYCCSB35Vp06u+eTWjG0/
pyS5V14stGtw+fA0DJp5ZJV4eqJ5LqxMlYvEZ/qKTEdoCeaXv2QEmN6dVqjDoTAo
k0t5u4YRXzEVCfXAC3ocplNdtCA72wjFJcSbfif4BSC8bDACTXtnPC7nD0VndZLp
+RiNLeiENhk0oTC+UVdSc+n2nJOzkCK0vYu0Ads4JGIB7g8IB3z2t9ICmsWrgnhd
NdcOe15BincrGA8avQ1cWXsfIKEjbrnEuEk9b5jel6NfHtPKoHc9mDpRdNPISeVa
wDBM1mJChneHt59Nh8Gah74+TM1jBsw4fhJPvoc7Atcg740JErb904mZfkIEmojC
VPhBHVQ9LHBAdM8qFI2kRK0IynOmAZhexlP/aT/kpEsEPyaZQlnBn3An1CRz8h0S
PApL8PytggYKeQmRhl499+6jLxcZ2IegLfqq41dzIjwHwTMplg+1pKIOVojpWA==
-----END CERTIFICATE-----
</ca>
key-direction 1
<tls-auth>
#
# 2048 bit OpenVPN static key
#
-----BEGIN OpenVPN Static key V1-----
e685bdaf659a25a200e2b9e39e51ff03
0fc72cf1ce07232bd8b2be5e6c670143
f51e937e670eee09d4f2ea5a6e4e6996
5db852c275351b86fc4ca892d78ae002
d6f70d029bd79c4d1c26cf14e9588033
cf639f8a74809f29f72b9d58f9b8f5fe
fc7938eade40e9fed6cb92184abb2cc1
0eb1a296df243b251df0643d53724cdb
5a92a1d6cb817804c4a9319b57d53be5
80815bcfcb2df55018cc83fc43bc7ff8
2d51f9b88364776ee9d12fc85cc7ea5b
9741c4f598c485316db066d52db4540e
212e1518a9bd4828219e24b20d88f598


Here is the error I am getting
> 
sudo bash connect.sh 
mknod: /dev/net/tun: File exists
Wed Dec 23 02:08:04 2020 WARNING: file '/etc/openvpn/auth.txt' is group or others accessible
Wed Dec 23 02:08:04 2020 OpenVPN 2.4.4 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on May 14 2019
Wed Dec 23 02:08:04 2020 library versions: OpenSSL 1.1.1  11 Sep 2018, LZO 2.08
Wed Dec 23 02:08:04 2020 WARNING: --ping should normally be used with --ping-restart or --ping-exit
Wed Dec 23 02:08:04 2020 Outgoing Control Channel Authentication: Using 512 bit message hash 'SHA512' for HMAC authentication
Wed Dec 23 02:08:04 2020 Incoming Control Channel Authentication: Using 512 bit message hash 'SHA512' for HMAC authentication
Wed Dec 23 02:08:04 2020 TCP/UDP: Preserving recently used remote address: [AF_INET]217.138.205.251:1194
Wed Dec 23 02:08:04 2020 Socket Buffers: R=[1048576->1048576] S=[1048576->1048576]
Wed Dec 23 02:08:04 2020 UDP link local: (not bound)
Wed Dec 23 02:08:04 2020 UDP link remote: [AF_INET]217.138.205.251:1194
Wed Dec 23 02:08:04 2020 write UDP: Operation not permitted (code=1)
Wed Dec 23 02:08:06 2020 write UDP: Operation not permitted (code=1)
Wed Dec 23 02:08:10 2020 write UDP: Operation not permitted (code=1)


---

### Post by darkod on 2020-12-23
IMHO you are shooting yourself in the foot by being too strict with the OUTPUT chain. If you use a DROP policy then you have to chase up every single outgoing traffic that you need to allow as rule. You need to protect your server from someone coming in from the outside. Not going out from the inside.

I use ACCEPT policy usually for OUTPUT and have never seen issues.

Having said that, I see you don't have a rule for the established traffic in the OUTPUT chain. I think that is needed when using DROP policy. Try adding a rule similar to this one but for OUTPUT chain:
```
# Allow established sessions to receive traffic:
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

---

### Post by oner-erol on 2020-12-25
Muchas Gracias darkod

I think I found the solution.
I don't fully understand how it work but I think the LXC ubuntu on QNAP is very light and as far as I understand the "comment" module of iptables is not there so I was getting an error for the line:
iptables -I OUTPUT 1 -p udp --destination-port 1194 -m comment --comment "Allow VPN connection" -j ACCEPT

So I changed it to:
iptables -I OUTPUT 1 -p udp --destination-port 1194 -j ACCEPT

and it works with "iptables -P OUTPUT DROP" at start and end.I don't understand if the comments are really useful?

---

