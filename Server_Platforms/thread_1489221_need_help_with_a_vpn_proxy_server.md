---
title: "need help with a vpn proxy server"
date: 2010-05-20
forum: Server Platforms
---

### Post by linkshift on 2010-05-20
I have set up a VPS ubuntu webserver (9.04) for the first time...
apache,mysql,php work great! thanks!

now i do lots of traveling, use public wi-fi lots of time am behind firewall or proxies that do content filtering and a proxy/vpn should make transmissions a bit secure... ultravpn or hot spot shield type products work for windows but are a pain in the butt third party solutions with adware and bandwidth limits.

so i need something easy and light weight that runs on this server (only for me and a couple of other people... i know i can can use a squid proxy (but would skype work?) and not sure if packet inspection would catch it (since its not encrypted) even if i use a different port and voip or sip wouldn't work with squid atleast not without heavy configuration of each application.

so, a vpn sounds like the solution for me... ya well not so quick...
i tries pptpd (poptop)... its just a bunch of poo... keeps giving me 10 million errors w/ the windows client trying to connect to it...

L2PT/IPSEC ... well i tries installing openswan ... which installs but tells me, 
"the kernel does not seem to have ipsec support." i use webmin/virtual min for most of my admin work and im not ssh shy but no way im recompiling my kernel for this.

So.. any suggestions, ideas would be greatly appreciated. I hear ubuntu has great support... Lets see!... Thanks in advance.

---

### Post by linkshift on 2010-05-21
bump

---

### Post by benderisgreat on 2010-05-21
Checkout openvpn. It's secure, not that hard to configure and can be configured to work through any firewall.

---

### Post by linkshift on 2010-05-21
correct me if im wrong... but does open vpn require ipsec? I looked it up before but couldnt find any evidence that it did... just the key making looks complicated...

---

### Post by benderisgreat on 2010-05-21
No it doesn't. Openvpn makes use of openssl to create an ssl tunnel over either udp or tcp. You can configure it to connect over the https port (tcp/443). Key making isn't that difficult. The openvpn package in ubuntu comes with scripts (easy-rsa) to help with key creation. There are plenty of how-to's out there. Just remember to use 'sudo su' for the key creation. just 'sudo' won't work.

---

### Post by linkshift on 2010-05-22
ok, installed open vpn... created the keys with easy-rsa/2.0/vars
configured my vpn... put it in the openvpn config to atostart ... my vpnfile is simply "openvpn"... 
now when i issue the command to start the vpn

/etc/init.d/openvpn restart
or
/etc/init.d/openvpn start openvpn

i get the same error, open vpn start .................. [fail]

i did name it differently too before same error...
the problem is the error just doesnt tell me anything aside from the fact its not working..
.. any log files i can look though... ?

-----------------------------------------------
and on a side note noob ubuntu question... how can i remove and make sure everything and the old config files completly removed so when i reinstall vpn, its on default config.

-thanks-

---

### Post by benderisgreat on 2010-05-22
Try to run it manually like this:
```
# openvpn --config <pathtoyourconfig>
```

---

### Post by benderisgreat on 2010-05-22
by the way if your config file is just openvpn with no extension the scripts in /etc/init.d/ won't pick it up. it looks for files in the /etc/openvpn directory wich end in ".conf":

> CONFIG_DIR=/etc/openvpn
..
start vpn () {
if grep -q '^[       ]*daemon' $CONFIG_DIR/$NAME.conf ; then
..

if you run openvpn in a shell as i described in my previous post it will be easier to determine if your config actually works.

---

### Post by koenn on 2010-05-22
openvpn logs to syslog.
If you get a 'fail' when starting openvpn, syslog will contain info of what happened

try
```
grep openvpn /var/log/syslog 
```

---

### Post by linkshift on 2010-05-22
this is what i get when try starting open vpn using the suggested command

root@linkshift:/etc/openvpn# openvpn --config /etc/openvpn/openvpn.conf

```

root@linkshift:/etc/openvpn# openvpn --config /etc/openvpn/openvpn.conf
Sun May 23 00:51:57 2010 OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL]                   [PKCS11] built on Mar  9 2009
Sun May 23 00:51:57 2010 WARNING: --keepalive option is missing from server conf                  ig
Sun May 23 00:51:57 2010 Cannot open /etc/openvpn/easy-rsa/keys/dh1024.pem for D                  H parameters: error:02001002:system library:fopen:No such file or directory: err                  or:2006D080:BIO routines:BIO_new_file:no such file
Sun May 23 00:51:57 2010 Exiting
```

and syslogger tells me
```
root@linkshift:/etc/openvpn# grep openvpn /var/log/syslog
May 21 20:32:49 linkshift ovpn-openvpn[1931]: OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Mar  9 2009
May 21 20:32:49 linkshift ovpn-openvpn[1931]: WARNING: --keepalive option is missing from server config
May 21 20:32:49 linkshift ovpn-openvpn[1931]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
May 21 20:32:49 linkshift ovpn-openvpn[1931]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
May 21 20:32:50 linkshift ovpn-openvpn[1931]: Note: Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)
May 21 20:32:50 linkshift ovpn-openvpn[1931]: Note: Attempting fallback to kernel 2.2 TUN/TAP interface
May 21 20:32:50 linkshift ovpn-openvpn[1931]: Cannot allocate TUN/TAP dev dynamically
May 21 20:32:50 linkshift ovpn-openvpn[1931]: Exiting

```

now ls of differnet dirs
```
root@linkshift:/etc/openvpn# ls
clients  easy-rsa  keys  openvpn-ssl.cnf  openvpn.conf  servers
root@linkshift:/etc/openvpn# ls easy-rsa/
Makefile     build-key-pass    inherit-inter         revoke-full
README.gz    build-key-pkcs12  keys                  sign-req
build-ca     build-key-server  list-crl              vars
build-dh     build-req         openssl-0.9.6.cnf.gz  whichopensslcnf
build-inter  build-req-pass    openssl.cnf
build-key    clean-all         pkitool
root@linkshift:/etc/openvpn# cd easy-rsa/
root@linkshift:/etc/openvpn/easy-rsa# cd keys
root@linkshift:/etc/openvpn/easy-rsa/keys# ls
01.pem  ca.key       client2.csr  index.txt           serial.old
02.pem  client1.crt  client2.key  index.txt.attr      server.crt
03.pem  client1.csr  client3.crt  index.txt.attr.old  server.csr
04.pem  client1.key  client3.csr  index.txt.old       server.key
ca.crt  client2.crt  client3.key  serial
root@linkshift:/etc/openvpn/easy-rsa/keys#

```

*contents of openvpn.conf* in /etc/openvpn: [INDENT]```
dev tun
proto tcp
port 1194
 ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key
dh /etc/openvpn/easy-rsa/keys/dh1024.pem
 user nobody
group nogroup
server 10.8.0.0 255.255.255.0
 persist-key
persist-tun
 #status openvpn-status.log
#verb 3
client-to-client
 push "redirect-gateway def1"
 #log-append /var/log/openvpn
comp-lzo 

```[/INDENT]any ideas?:confused:

---

### Post by linkshift on 2010-05-22
amm... i just realized i actually dont know what
```
dh /etc/openvpn/easy-rsa/keys/dh1024.pem
```
is for? and why is it in my config?

---

### Post by dipeshmehta on 2010-05-23
> **linkshift said:**
> amm... i just realized i actually dont know what
```
dh /etc/openvpn/easy-rsa/keys/dh1024.pem
```
is for? and why is it in my config?

The "Diffie Hellman Parameters" govern the method of key exchange and authentication used by the OpenVPN server.  More information on dh found here: [http://www.rsa.com/rsalabs/node.asp?id=2248](http://www.rsa.com/rsalabs/node.asp?id=2248)

Dipesh

---

### Post by koenn on 2010-05-23
> **linkshift said:**
> this is what i get when try starting open vpn using the suggested command
...
and syslogger tells me


now ls of differnet dirs

...


any ideas?:confused:

my fist impression is your key mechanism isn't working right. I'm not sure if this would prevent the tun interface from being created.

I'd suggest you clean up the authentication stuff and try this simple static key approach : [http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html](http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html)

if that works, you'll at least know that openvpn is working, and you can have another look at the CA stuff. 
If not, you'll know you need to diagnose openvpn further.

---

### Post by benderisgreat on 2010-05-23
The diffie-helmann parameters are there to make it possible to encrypt a connection without presharing any secret.

> Sun May 23 00:51:57 2010 Cannot open /etc/openvpn/easy-rsa/keys/dh1024.pem for DH parameters: error:02001002:system library:fopen:No such file or directory: err                  or:2006D080:BIO routines:BIO_new_file:no such file
This error indicates that you either have not created the dh1024.pem file, that it's not in the specified directory or is named differently.
Create it as per some howto and try again. There no need to start all over.

#edit
reading your previous post with your ls of /etc/openvpn/easy-rsa/keys shows that you have in fact no file named dh1024.pem in that directory.

this is why i suggested running openvpn in a shell; it does actually tell you what's wrong.

---

### Post by gaoshan88 on 2010-05-24
I've been struggling with getting OpenVPN to route all internet traffic for me so I can use it for all web and mail activities and I am stuck (though I can get VPN running fine) but in your instance I see that in your conf file you have the route for dh1024.pem set to: 
```
/etc/openvpn/easy-rsa/keys/dh1024.pem
```
but the file is not present there or indeed anywhere in your lists. This means you most likely didn't create it. Most instructions I ran across have you creating it at the same time as the other server certificates. The command is: ```
./build-dh
```

So actually the error messages you have tell you exactly what is wrong by telling you they can't find dh1024.pem. Your conf says it is in one specific location but it isn't so...

---

### Post by linkshift on 2010-05-27
using @gaoshan88 suggestion, i have used .vars to generate a dh1024.pem file with the ./build-dh command... so thats resolved and the error i get now is

```
Fri May 28 02:55:54 2010 OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Mar  9 2009
Fri May 28 02:55:54 2010 WARNING: --keepalive option is missing from server config
Fri May 28 02:55:54 2010 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Fri May 28 02:55:54 2010 Note: Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)
Fri May 28 02:55:54 2010 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Fri May 28 02:55:54 2010 Cannot allocate TUN/TAP dev dynamically
Fri May 28 02:55:54 2010 Exiting

```

as suggested by @KOENN im trying out the static key instructions but the above error sound like some sort of a networking/permissoion issue... 

Let me point out, IPsec dint work for me becuase my kernel dint support it (similar support issue here, sorry i dont know open VPN)

Thanks for you help!

---

### Post by benderisgreat on 2010-05-28
did you run it with sudo?```
sudo openvpn --config yourconfig
```

---

### Post by linkshift on 2010-05-28
> **benderisgreat said:**
> did you run it with sudo?```
sudo openvpn --config yourconfig
```

i have enabled root (su) for this server installation
and i ran it using root... and its failed and i got the above error (see previous post)

i just have this gut feeling (not based on anything) that this might be an issue of virtualization... as mentioned before, its a VPS (virtual private server) but then again its shouldnt make a difference cuz the ubuntu thinks its on real hardware... but maybe networking is done differently, i dont know where too look though...

the error lines
Note: Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)
Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Cannot allocate TUN/TAP dev dynamically

what do they mean?

---

### Post by linkshift on 2010-05-28
my suspicion was right...
[http://wiki.vpslink.com/TUN/TAP_device_with_OpenVPN_or_Hamachi](http://wiki.vpslink.com/TUN/TAP_device_with_OpenVPN_or_Hamachi)

according to this page, its def an issue of visualization... not sure should i run the suggested commands on the me server OS or ask my webhost to run it on the HOST OS?
i ran them on my ubuntu server any way and this is what i got

```
**> mkdir -p /dev/net**
**> mknod /dev/net/tun c 10 200**
mknod: `/dev/net/tun': File exists
**> chmod 600 /dev/net/tun**
**> cat /dev/net/tun**
cat: /dev/net/tun: Permission denied

```

all commands were ran while logged in as root (so no need to sudo)
why permission denied? im now sure, this is the culprit!

---

### Post by spynappels on 2010-05-29
You need to check what VPS platform your VPS is running on. Ours run on Xen and we have no problems whatsoever, but the other platform metioned needs the commands run on the VPS platform rather than on the client machine.

---

### Post by linkshift on 2010-06-03
thanks guys, the problem was in deed on my hosts end
(they had to enable tap/tun for my account)
anyhow, this fixes my server side issue
now i have some client issues, but i have started a separate thread for that..

Thanks for your help!:popcorn:

---

