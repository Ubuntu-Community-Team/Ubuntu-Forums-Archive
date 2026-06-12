---
title: "Issues with Setting up a Samba/Bind Server"
date: 2008-09-16
forum: Server Platforms
---

### Post by jessecgross on 2008-09-16
Hi everyone. I have been following this [http://ubuntuforums.org/showthread.php?t=640760]("http://ubuntuforums.org/showthread.php?t=640760") how-to for testing purposes on a home network and have run into an issue. Granted I used Debian as my server and Ubuntu as my client, but hopefully because they are so similar someone can still assist me.


I have installed everything and configured everything without fault so far upon until the step of mounting a drive on my client machine. I have come to find that the client machine can not resolve the server by it's FQDN, but can with it's flat name. I further discovered that when pinging or using nslookup the flat name will resolve the FQDN and the correct ip, but still can not ping the full name. In addition I did determine that the client will mount the drive using the IP of the server (so I know that is working).

So I believe it is fairly obvious that it is a DNS issue, but because this is my first time with Bind I am fairly lost. Any help would be great. I have included the connectivity testing below. Let me know if you would like to see any conf file settings.

```
jesse@scottsummers:~$ sudo mount charlesxavier.cerebros.local:/ldaphome /ldaphom                                                                             e
[sudo] password for jesse:
mount.nfs: can't get address for charlesxavier.cerebros.local

jesse@scottsummers:~$ ping charlesxavier
PING charlesxavier.cerebros.local (192.168.1.40) 56(84) bytes of data.
64 bytes from 192.168.1.40: icmp_seq=1 ttl=64 time=0.121 ms
64 bytes from 192.168.1.40: icmp_seq=2 ttl=64 time=0.118 ms

--- charlesxavier.cerebros.local ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 5043ms
rtt min/avg/max/mdev = 0.118/0.119/0.121/0.011 ms
jesse@scottsummers:~$ ping charlesxavier.cerebros.local
ping: unknown host charlesxavier.cerebros.local
jesse@scottsummers:~$ ping cerebros.local
ping: unknown host cerebros.local
jesse@scottsummers:~$ nslookup charlesxavier
Server:         192.168.1.40
Address:        192.168.1.40#53

Name:   charlesxavier.cerebros.local
Address: 192.168.1.40

```

---

