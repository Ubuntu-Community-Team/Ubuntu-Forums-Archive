---
title: "How to access samba server from different network?"
date: 2016-10-11
forum: Server Platforms
---

### Post by minda2 on 2016-10-11
[COLOR=#333333]I set up a SAMBA server to share files between computers. I can connect to the server from the same network (e.i: a.b.x.*). But when I am on another network (a.b.y.*), I cannot connect to the server. Running [/COLOR]*smbstatus *returns the following:[I]```

Samba version 4.2.4-21.3     Username      Group         Machine            Protocol Version       
------------------------------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED




Service      pid     machine       Connected at
-------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED
Failed to traverse sessions: NT_STATUS_ACCESS_DENIED




No locked files

```

[/I]Running *telnet myserver 139 or 445 *from the other network returns:[COLOR=#000000][FONT=Ubuntu Mono]NT_STATUS_ACCESS_DENIED
[/FONT][/COLOR]And this is my [COLOR=#000000][FONT=Menlo]smb.conf [/FONT][/COLOR]file:
[I]
```

[COLOR=#CD7923][FONT=Menlo][global][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]workgroup[/COLOR] = WORKGROUP[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]passdb[/COLOR] [COLOR=#34bc26]backend[/COLOR] = tdbsam[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]printing[/COLOR] = cups[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]printcap[/COLOR] [COLOR=#34bc26]name[/COLOR] = cups[/FONT][/COLOR]
[COLOR=#34BC26][FONT=Menlo]        printcapcachetime[COLOR=#000000] = 750[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]cups[/COLOR] [COLOR=#34bc26]options[/COLOR] = raw[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]map[/COLOR] [COLOR=#34bc26]to[/COLOR] [COLOR=#34bc26]guest[/COLOR] = Bad User[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]include[/COLOR] = /etc/samba/dhcp.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]logon[/COLOR] [COLOR=#34bc26]path[/COLOR] = \\[COLOR=#d53bd3]%L[/COLOR]\profiles\.msprofile[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]logon[/COLOR] [COLOR=#34bc26]home[/COLOR] = \\[COLOR=#d53bd3]%L[/COLOR]\[COLOR=#d53bd3]%U[/COLOR]\.9xprofile[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]logon[/COLOR] [COLOR=#34bc26]drive[/COLOR] = P:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        usershare [COLOR=#34bc26]allow[/COLOR] guests = [COLOR=#c33720]No[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]security[/COLOR] = user[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]add[/COLOR] [COLOR=#34bc26]machine[/COLOR] [COLOR=#34bc26]script[/COLOR] = /usr/sbin/useradd  -c Machine -d /var/lib/nobody -s /bin/[COLOR=#c33720]false[/COLOR] [COLOR=#d53bd3]%m[/COLOR]$[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]domain[/COLOR] [COLOR=#34bc26]logons[/COLOR] = [COLOR=#c33720]Yes[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]domain[/COLOR] [COLOR=#34bc26]master[/COLOR] = [COLOR=#c33720]Yes[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]wins[/COLOR] [COLOR=#34bc26]support[/COLOR] = [COLOR=#c33720]No[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        usershare [COLOR=#34bc26]max[/COLOR] shares = 100[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]local[/COLOR] [COLOR=#34bc26]master[/COLOR] = [COLOR=#c33720]Yes[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]os[/COLOR] [COLOR=#34bc26]level[/COLOR] = 65[/FONT][/COLOR]
[COLOR=#34BC26][FONT=Menlo]        preferredmaster[COLOR=#000000] = [/COLOR][COLOR=#c33720]Yes[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]wins[/COLOR] [COLOR=#34bc26]server[/COLOR] =[/FONT][/COLOR]
[COLOR=#CD7923][FONT=Menlo][homes][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]comment[/COLOR] = Home Directories[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]valid[/COLOR] [COLOR=#34bc26]users[/COLOR] = [COLOR=#d53bd3]%S[/COLOR], [COLOR=#d53bd3]%D[/COLOR]%w[COLOR=#d53bd3]%S[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]browseable[/COLOR] = [COLOR=#c33720]No[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]read[/COLOR] [COLOR=#34bc26]only[/COLOR] = [COLOR=#c33720]No[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]inherit[/COLOR] [COLOR=#34bc26]acls[/COLOR] = [COLOR=#c33720]Yes[/COLOR][/FONT][/COLOR]
[COLOR=#CD7923][FONT=Menlo][profiles][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]comment[/COLOR] = Network Profiles Service[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]path[/COLOR] = [COLOR=#d53bd3]%H[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]read[/COLOR] [COLOR=#34bc26]only[/COLOR] = [COLOR=#c33720]No[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]store[/COLOR] [COLOR=#34bc26]dos[/COLOR] attributes = [COLOR=#c33720]Yes[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]create[/COLOR] [COLOR=#34bc26]mask[/COLOR] = 0600[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]directory[/COLOR] [COLOR=#34bc26]mask[/COLOR] = 0700[/FONT][/COLOR]
[COLOR=#CD7923][FONT=Menlo][users][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]comment[/COLOR] = All users[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]path[/COLOR] = /home[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]read[/COLOR] [COLOR=#34bc26]only[/COLOR] = [COLOR=#c33720]No[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]inherit[/COLOR] [COLOR=#34bc26]acls[/COLOR] = [COLOR=#c33720]Yes[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]veto[/COLOR] [COLOR=#34bc26]files[/COLOR] = /aquota.user/groups/shares/[/FONT][/COLOR]
[COLOR=#CD7923][FONT=Menlo][groups][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]comment[/COLOR] = All groups[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]path[/COLOR] = /home/groups[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]read[/COLOR] [COLOR=#34bc26]only[/COLOR] = [COLOR=#c33720]No[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]inherit[/COLOR] [COLOR=#34bc26]acls[/COLOR] = [COLOR=#c33720]Yes[/COLOR][/FONT][/COLOR]
[COLOR=#CD7923][FONT=Menlo][printers][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]comment[/COLOR] = All Printers[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]path[/COLOR] = /var/tmp[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]printable[/COLOR] = [COLOR=#c33720]Yes[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]create[/COLOR] [COLOR=#34bc26]mask[/COLOR] = 0600[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]browseable[/COLOR] = [COLOR=#c33720]No[/COLOR][/FONT][/COLOR]
[COLOR=#CD7923][FONT=Menlo][print$][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]comment[/COLOR] = Printer Drivers[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]path[/COLOR] = /var/lib/samba/drivers[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]write[/COLOR] [COLOR=#34bc26]list[/COLOR] = @ntadmin root[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]force[/COLOR] [COLOR=#34bc26]group[/COLOR] = ntadmin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]create[/COLOR] [COLOR=#34bc26]mask[/COLOR] = 0664[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]directory[/COLOR] [COLOR=#34bc26]mask[/COLOR] = 0775[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#CD7923][FONT=Menlo][netlogon][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]comment[/COLOR] = Network Logon Service[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]path[/COLOR] = /var/lib/samba/netlogon[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]write[/COLOR] [COLOR=#34bc26]list[/COLOR] = root[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#CD7923][FONT=Menlo][Shared][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]guest[/COLOR] [COLOR=#34bc26]ok[/COLOR] = [COLOR=#c33720]Yes[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]inherit[/COLOR] [COLOR=#34bc26]acls[/COLOR] = [COLOR=#c33720]Yes[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]path[/COLOR] = /home/myusername/Shared[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        [COLOR=#34bc26]read[/COLOR] [COLOR=#34bc26]only[/COLOR] = [COLOR=#c33720]No[/COLOR][/FONT][/COLOR]
```

[/I]BTW the firewall is off.
Thanks.

---

### Post by TheFu on 2016-10-11
Routers blocking? - this assumes it is over an internal LAN, not over the internet.  CIFS isn't safe to use over the internet without a full VPN.

---

### Post by minda2 on 2016-10-11
Yeah, probably the routers are blocking. I'll contact the network admin. Hopefully problem will be solved. 
I'm not using it over the internet. Basically I'm trying to connect from another building through the internal network.
What do you mean by [COLOR=#000000]> [/COLOR][COLOR=#000000] this assumes it is over an internal LAN, not over the internet[/COLOR][COLOR=#000000]?[/COLOR]

---

### Post by bab1 on 2016-10-11
> **minda2 said:**
> Yeah, probably the routers are blocking. I'll contact the network admin. Hopefully problem will be solved. 
I'm not using it over the internet. Basically I'm trying to connect from another building through the internal network.
What do you mean by [COLOR=#000000]?[/COLOR]

Regardless of your router firewall configuration, you will need to configure a WINS server to browse the two subnets in your LAN. 

The internet uses public addresses while the internal IP addresses can use private addresses that are not routable via the internet.  Your internal LAN subnets should be firewalled from the internet in either case.

---

### Post by volkswagner on 2016-10-11
I would try using the ip address to navigate shares. Using netbios or DNS hostname will likely not traverse the two routers between machines.

Try telnet ip.add.of.srv 139

Or directly navigate to the ip address. Are you using Windows as client or other?

\\10.0.1.22 or smb://10.0.1.22 (substitute actual server ip)

---

### Post by minda2 on 2016-10-12
I talked to the network admin. He said they block SMB ports for security reasons. And I guess this was the reason why I could not connect from different network. Thank you guys.

---

### Post by TheFu on 2016-10-12
Is CIFS the only choice?  If they are *nix systems, you have many other options - sftp, scp, rsync, ssh ...

---

### Post by minda2 on 2016-10-13
They are UNIX like systems (mac & opensuse). Right now I'm using ssh/scp. I tried to set up NFS server, but again I could not access it from some of the networks in different buildings. I want something easily accessible from file manager and synchronize files authomatically. FTP is another option, but in Mac when you connect to an FTP server (by using built in app) you cannot modify files. There are apps available, but I wanted it to be inside Finder for ease of access.

I might just use a cloud storage service. But I don't wanna store my files on somewhere else, even though there is nothing confidential...

BTW: what about WebDAV? Do you recommend it?

---

### Post by TheFu on 2016-10-14
Never use plain FTP. That protocol should have died except for things you want published to the world, without any credentials. It is bad for security.

If ssh works, then sftp/scp works.  In Linux, almost any file manager will support ssh:// or sftp:// URLs.

I wouldn't use webdav, unless it is completely locked down at the router to prevent unwanted IPs (just the IPs you need, period).  For example, I have a few personal servers running and one is NextCloud, which can use webdav. Rather than have it open to the world, when I'm on travel, I'll setup a VPN back home to access it.  It is HTTPS already, but I feel that isn't sufficient security (HTTPS has been badly broken for about a decade).  Out of the 4billion IPs, only my internal subnet has access.  It has a public connection because smartphones are stupid. It has a public HTTPS cert (Let's Encrypt), so in theory, the connection is secure.  I do not use the NextCloud auto-sync.

I can't recommend anything for OSX. Have only seen that OS for a few weeks - long enough to learn it didn't fit my needs - gave the Mac away to someone who ended up making it into a Kodi box (he was a gamer).

To synchronize files automatically, I use ssh + rsync.  In my mind, there is a "system of record" for all files.  That is my desktop at home.  Not my laptop. Not my tablet, not any other server.  When on travel, certain files on the laptop will become the "record", until I return home and push them back to the desktop. The sync time is only once a day for me. That is sufficient for my needs.  I avoid using cloud services. Simply don't trust them.  There is a project for people like me who want to avoid using cloud services - sovereign.  I actually don't use sovereign, but do use many of the tools they provide.  Just spun up a wallabag server about a month ago. It has completely changed the way and where I read webpages.  It is not publicly available, though it is secured with SSL/Cert and has a public facing IP ... which is blocked for all outside access (well, almost all).

---

