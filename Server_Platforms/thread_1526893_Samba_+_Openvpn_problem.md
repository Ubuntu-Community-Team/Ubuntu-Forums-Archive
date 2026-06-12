---
title: "Samba + Openvpn problem"
date: 2010-07-08
forum: Server Platforms
---

### Post by mrhub on 2010-07-08
Hi!

I have recently got problem with accessing my samba share through openvpn. It has worked before but I have update the server and changed some settings on my workstation and now it have gone down the drain...

The server has 10.0.0.1 and the workstations has 10.0.0.2 (win7).

I can access the server through openvpn with ping and www, meaning that the server responds on ping 10.0.0.1 and I see my transmission webinterface at [http://10.0.0.1:9091](http://10.0.0.1:9091).


On the server I can access samba shares with smbclient for localhost but not with openvpns ip:
```
hub@familjenhuss:~$ smbclient //10.0.0.1/Root
Enter hub's password:
Connection to 10.0.0.1 failed (Error NT_STATUS_CONNECTION_REFUSED)
hub@familjenhuss:~$ smbclient //127.0.0.1/Root
Enter hub's password:
Domain=[FBI] OS=[Unix] Server=[Samba 3.4.7]
smb: \> exit
hub@familjenhuss:~$ smbclient //localhost/Root
Enter hub's password:
Domain=[FBI] OS=[Unix] Server=[Samba 3.4.7]
smb: \> exit
```

Relevant lines from smb.conf:
```
interfaces = 127.0.0.0/8 10.0.0.0/8 tun0
bind interfaces only = true
hosts allow = 127.0.0.1, 10.0.0.1, 10.0.0.2
hosts deny = 0.0.0.0/0
```

What should I do? I have tried to disable the firewall on the workstation (win7) but it dont make any difference.

Thankful for any input.

---

### Post by mrhub on 2010-07-10
I have reinstalled the client on my workstation, and reinstalled and reconfigured according to [http://openvpn.net/index.php/open-source/documentation/howto.html#pki .]("http://openvpn.net/index.php/open-source/documentation/howto.html#pki")
Same problem!
Can ping and access though www, but still no file access! :(
Anyone got any idea?

---

### Post by Mustard007 on 2010-12-07
Same trouble here....

I've put my hostallow and interfaces config in smb.conf, but no files accessibles from samba.
It's a simple TUN setup. (samba and openvpn on the same machine)

Thanks !

---

