---
title: "SSH On Same IP - Different Machines?"
date: 2007-02-12
forum: Server Platforms
---

### Post by CyberAngel on 2007-02-12
**_Here is my status:_**

I have a server that is doing a PPPoE internet Connection.
Behind that server of course there is a LAN :)

The server has the SSH service running so that I can connect to this machine remotely from everywhere I can have internet access.
Behind that server (On the LAN) a few more Linux systems with the ssh service active exists.

From the server now, I have port forward some random ports to the ssh ports of the LAN Machines with the following iptables rule.
e.g.
```
iptables -t nat -I PREROUTING -i ppp0 -p tcp --dport 12345 -j DNAT --to 192.168.10.100:22
```

So whatever request is coming from the internet side (ppp0) on port 12345 (or whatever) to be forwarded on a LAN machine (in this case 192.168.10.100) on port 22.

The above are all OK.

**_Here is my problem:_**

If I connect the first time on the server I am getting the classic message:
```
The authenticity of host 'xxx.xxx.xxx.xxx' can't be established.
RSA key fingerprint is 11:22:33:44:55:66:77:88:99:aa:bb:cc:dd:ee:ff:00.
Are you sure you want to continue connecting (yes/no)?
```

now if I try to connect using ssh on port 12345 that it is forwarded on a machine inside the LAN I get the following error:

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
00:22:33:44:55:66:bb:88:99:aa:77:cc:dd:ee:ff:11.
Please contact your system administrator.
Add correct host key in /home/cyberangel/.ssh/known_hosts to get rid of this message.
Offending key in /home/cyberangel/.ssh/known_hosts:1
RSA host key for xxx.xxx.xxx.xxx has changed and you have requested strict checking.
Host key verification failed.

```

As it says in the last line "you have requested strict checking". Can I disable strict checking?
How can get rid of this message and let me connect?
I know that I can remove ~/.ssh/known_hosts and then I can connect normally but that is not a solution because I need to always removing the ~/.ssh/known_hosts before I try to connect on a different machine.

Thanks.

---

### Post by jtc on 2007-02-12
You can disable strict checking by setting the StrictHostKeyChecking option in ~/.ssh/config

```
man ssh_config
```

But if you are going to muck around with your ssh configuration, you might as well bit a bit more creative :) Simple add entries like this for every computer you are going to connect to behind the external ip.

```

host computeraliasname
     hostname your.external.ip.number
     Port 12345
     UserKnownHostsFile ~/.ssh/uniqefilename

```

That way you get a (short) alias for each computer, you won't have to specify their port numbers each time and since they all have their own "known_hosts" you can still have Strict Checking without the different hashes interfering with each other.

---

### Post by CyberAngel on 2007-02-12
Thank you very much!!!
It works now with
```
host computeraliasname
     hostname your.external.ip.number
     Port 12345
     UserKnownHostsFile ~/.ssh/uniqefilename
```

---

