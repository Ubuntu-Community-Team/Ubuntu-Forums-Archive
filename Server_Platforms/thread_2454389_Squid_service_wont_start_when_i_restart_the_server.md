---
title: "Squid service wont start when i restart the server"
date: 2020-11-28
forum: Server Platforms
---

### Post by sergiocaimi on 2020-11-28
I use Squid 4.10 on ubuntu server 20.04.01 LTS
I configure ACL´s to the different sectors of the company. The machines names in the ACLS´s list, is in FQDN names of the windows domain.
When i ping to the FQDN name it works fine and also if i ping directly to the IP
The DNS and the DHCP service is in Windows server 2019 to the LAN machines.
**The problem occurs when i restart the server, the squid service wont start**. **But if i start the service manually, the service start and squid works fine.**

I found this in /var/log/syslog when i restart the server:

aclIpParseIpData: Bad host/IP: 'sist1.ad.mzzzzz' in 'sist1.ad.mzzzzz', flags=0 : (-3) Temporary failure in name resolution
FATAL: Bungled /etc/squid/squid.conf line 1429: acl sistemas "/etc/squid/ACL/sistemas"
Squid Cache (Version 4.10): Terminated abnormally.
squid.service: Control process exited, code=exited, status=1/FAILURE
squid.service: Failed with result 'exit-code'
Failed to start Squid Web Proxy Server 

many thanks

---

### Post by darkod on 2020-11-28
I don't know much squid but it looks like it can't resolve sist1.ad.mzzzzz.

What does it say if you do 'dig sist1.ad.mzzzzz' or 'nslookup sist1.ad.mzzzzz'. Does it resolve correctly?

Also, did you check line 1429 in squid.conf because it reports some error there. Not sure if that is related to the name resolution above.

---

### Post by sergiocaimi on 2020-11-28
The line 1429 in squid.conf is the entry where the acl is located. 
If i test squid.conf with squid -k parse, the squid.conf seemed fine
Nslookup resolve fine sist1.ad.mzzzzz
For some reason, the problem to resolve the names is in the restarting server process 
I insist, if is start the squid sercice manually its works fine.

---

### Post by darkod on 2020-11-28
Then it seems somehow during boot squid is started before the DNS is ready to resolve that host. Or maybe you add DNS settings later in the boot somehow.

You might be able to test by adding manual entry for that host sist1.ad.mzzzzz in /etc/hosts. That way it doesn't even depend on DNS resolving it. I guess squid should start correctly on boot then.

But if you don't want to depend on that manual entry in the future you will still need to find another solution. This might be only a temporary one.

---

### Post by sergiocaimi on 2020-11-28
The host sist1.ad.mzzzzz is the first of a list of hosts in ACL list. If i do that (/etc/hosts), the service wont start because there is another host in the ACL list that squid coul not resolve

---

### Post by sergiocaimi on 2020-11-28
I have trouble with squid service on ubuntu server 20.04.01 when i restart the server.
Is it possible to create a scrip which will check the status of the service after a server restart and start them automatically if found stopped? How ?
Many thanks.

---

### Post by wildmanne39 on 2020-11-28
Merged with this thread because it is about solving the same.

---

### Post by Tadaen_Sylvermane on 2020-11-29
I'm not sure if this is helpful but when I moved my squid to Docker with Snapd I had to create a shim script to hold it till the rest of the machine was ready else it failed to start every single time. I'm using systemd services for better or worse.

```
[Unit]Description = Starts Squid Container @ Boot & Stops
After = snapd.service snap.docker.dockerd.service
Requires = snap.docker.dockerd.service


[Service]
User = root
Group = root
Type = oneshot
ExecStartPre = /usr/local/bin/dockershim.source
ExecStart = /snap/bin/docker run \
    -id \
    -h squid \
    -p 3128:3128 \
    --rm \
    --mount source=squiddata,destination=/var/spool/squid \
    --mount source=squidconf,destination=/etc/squid \
    --name squid \
    squid
ExecStart = /snap/bin/docker exec -i squid /usr/local/bin/squidcert.source
ExecStart = /snap/bin/docker exec -i squid service squid start
ExecStop = /snap/bin/docker stop squid
RemainAfterExit = yes


[Install]
WantedBy = multi-user.target
```

```
#!/bin/sh
# tadaen sylvermane | jason gibson
# snapd docker shim


# begin script #


until [ -e /var/run/docker.sock ] ; do
    sleep 2
done
sleep 2


# end script #
```

Unsure of it you are using Docker at all so I'm not sure it's relevant. The point is maybe you just need to hold it off till something is started? systemd-resolved maybe?

---

### Post by TheFu on 2020-11-29
I haven't setup squid in about a decade.
For some reason, squid is being started before DNS is available, so you need to
a) determine which DNS you are using (systemd-resolved is likely)
b) make the startup of squid depend on the DNS setup/resolver in the squid.service file
That will fix this issue, but it won't fix any squid config issues.

It works manually, because by the time you ssh into the system, DNS + networking are up.

Squid should come with a systemd-service "Unit" definition.  Find that file .... I'd use 'locate squid.service', then ensure the 
```
After=
```
in the unit file points at the DNS service.
If you need to check the existance of a file, we can use:
```
ConditionPathExists=/etc/path/to/some file
```

Examples of both these settings are in the /etc/systemd/system/sshd.service file.
The network-online.target.wants/networking.service file has some interesting examples too and how multiple dependent services can be required.

---

### Post by sergiocaimi on 2020-11-30
> **TheFu said:**
> I haven't setup squid in about a decade.
For some reason, squid is being started before DNS is available, so you need to
a) determine which DNS you are using (systemd-resolved is likely)
b) make the startup of squid depend on the DNS setup/resolver in the squid.service file
That will fix this issue, but it won't fix any squid config issues.

It works manually, because by the time you ssh into the system, DNS + networking are up.

Squid should come with a systemd-service "Unit" definition.  Find that file .... I'd use 'locate squid.service', then ensure the 
```
After=
```
in the unit file points at the DNS service.
If you need to check the existance of a file, we can use:
```
ConditionPathExists=/etc/path/to/some file
```

Examples of both these settings are in the /etc/systemd/system/sshd.service file.
The network-online.target.wants/networking.service file has some interesting examples too and how multiple dependent services can be required.

**TheFu **thanks for the reply (also thanks to everyone) ...
I think this is maybe the solution ... but im noob and i need more info (if it possible)
I serch "squid.service" in all the disk, and i found it in many directories. Wich one i must modify? (i attach an immage)
My DNS service is in Windows Server 2019 (internal IP number 10.0.0.8)
I attach an immage of one the squid.service file i found.
Many thanks again.

---

### Post by TheFu on 2020-11-30
Modify the squid.service that is under under /etc/systemd/.... somewhere.

Please don't post images for text.

---

