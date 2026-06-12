---
title: "Which the Better SSh or OpenVPN ?!!"
date: 2010-05-26
forum: Security
---

### Post by haggar11 on 2010-05-26
Hello 

I am trying to acheive simple secure connection between 2 servers, allocated in different places. 

Server1 has static IP and openssh server, has X application using port 1000. 
Server2 on remote location, without static ip, Y application is to exchange data from X application at server1.

I would like to ask which is the best and simple soluation for me to link those servers in order, for X,Y to work securely over the internet. 

I came a cross OpenVPN but it looks for me its too advanced for such a simple connection, as my setup is simple, only 2 servers, OpenVPN is i think is to server bigger network. 

My question is can i use simple SSh connection?, if yes how can i setup this and any issues i must be aware of... 

if this can be done through ssh, how can i make ssh client on server2 start the connection automatically on startup and connect server1 in case of restarting events.

Many thanks for your help in advance.....
Regards

---

### Post by spynappels on 2010-05-26
I would have to suggest that you look at OpenVPN again. It can work for massive deployments, but can just as easily be used between 2 machines. The beauty is that you can use iptables rules to prohibit traffic through the Public channels on the ports you need but only accept connections on the tun0 interface. It will also allow you to grow your system if required in the future.

I would suggest using Server 1 as the OpenVPN server, and using iptables or the service's own config to bind the listening port to the VPN interface only. On the Client, then you connect to the VPN and use the VPN interface to communicate with the Server.

Once it is set up, it is foolproof and secure, and even setting it up is not difficult, you just have to get your head around creating certs and keys, but there are lots of great guides on the net for this.

---

### Post by haggar11 on 2010-05-26
Many thanks for your valuable advice, indeed i have already start reading through openvpn, if i face any problem i will call again here... 

Regards

---

### Post by The Cog on 2010-05-26
I agree with spynappels. SSH is prone to disconnects if it's left idle for a while. With OpenVPN the network connection is always there, and in my experience it has bombproof reliability. Setting it up is a little complicated, mainly the certificate bit but I think it's worthwhile. You just have to follow the howto step by step. 

You will need to arrange for the router at the server end to forward the appropriate UDP port to the server.

---

### Post by bodhi.zazen on 2010-05-26
These are tools, so it depends on what task you are wanting.

IMO SSH is a better option for ssh (shell access) and data transfer (scp / sshfs).

I have not had a problem with dropped connections (use keep alive).

Simple tunnels are "OK" over ssh - VNC, port forwarding, forwarding X applications etc.

You can VPN over ssh :

[http://bodhizazen.net/Tutorials/VPN-Over-SSH/](http://bodhizazen.net/Tutorials/VPN-Over-SSH/)

So for "simple" needs ssh is sufficient.

For your needs you could use ssh, scp, and sshfs.

---

### Post by haggar11 on 2010-05-27
Dears

Thanks all for your contribution, 

I have try to use Openvpn, manage to do all stuff, but still having problem, hence i am newbee, 

followed this interesting youtube simple tut 
[http://www.youtube.com/watch?v=BfZV4MnGfkk](http://www.youtube.com/watch?v=BfZV4MnGfkk) 

VPS (Server32 8.04) (Openvps-server)site reports error as follows: 

Fri May 28 04:12:25 2010 Diffie-Hellman initialized with 1024 bit key
Fri May 28 04:12:25 2010 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Fri May 28 04:12:25 2010 TLS-Auth MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Fri May 28 04:12:25 2010 Note: Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)
Fri May 28 04:12:25 2010 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Fri May 28 04:12:25 2010 Cannot allocate TUN/TAP dev dynamically
Fri May 28 04:12:25 2010 Exiting

Server2 (Server32 10.04) (Openvps-client) reports: 

Fri May 28 01:21:02 2010 OpenVPN 2.1.0 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jan 26 2010
Fri May 28 01:21:02 2010 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Fri May 28 01:21:02 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Fri May 28 01:21:02 2010 Cannot load certificate file ~/openvpn/client1.crt: error:02001002:system library:fopen:No such file or directory: error:20074002:BIO routines:FILE_CTRL:system lib: error:140AD002:SSL routines:SSL_CTX_use_certificate_file:system lib
Fri May 28 01:21:02 2010 Exiting

I am wondering if this tut worked with anyone!

Regards

---

### Post by kevdog on 2010-05-28
I like running OpenVPN with the linksys router running ddwrt firmware as the server.  Its very reliable, and with the little router box, I don't really have to worry about it powering off, locking up, etc.  Its very reliable.

However ssh is the poor man's VPN, however its extremely fast.  Depending on what you want to do, it might be the better option since its ridiculously simple and fast.

---

### Post by The Cog on 2010-05-28
> Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)is probably because you need to launch OpenVPN with root privileges. Try putting **sudo** in bront of the command.
> 
Cannot load certificate file ~/openvpn/client1.crt: error:02001002:system library:fopen:No such file or directory: indicates a configuration error - you've named the wrong file in your config file.

---

### Post by teejaybee on 2010-05-30
I use a combination of SSH and VTUN. Using VTUN by itself will probably satisfy your needs, especially if you need it to automagically reconnect etc. The only problem I have now is if the connection dies the SSH tunnel doesn't know how to reconnect, so I have to do it manually until I can be bothered automating it.

I got it all together using the following tutorial:

[http://etutorials.org/Networking/network+security+hacks/Chapter+6.+Secure+Tunnels/Hack+78+Tunnel+with+VTun+and+SSH/](http://etutorials.org/Networking/network+security+hacks/Chapter+6.+Secure+Tunnels/Hack+78+Tunnel+with+VTun+and+SSH/)

But substituted the real IP's he's using with private addresses - it's done as a point-to-point link. Having the default VTUN config handy (keep a backup) will help as it explains all the variables and their uses.

---

