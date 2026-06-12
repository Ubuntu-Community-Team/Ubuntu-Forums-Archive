---
title: "SAMBA - ubuntu invisible in Windows &quot;Network Places&quot;"
date: 2011-08-24
forum: Server Platforms
---

### Post by pwydymus on 2011-08-24
Hello,

**UPDATE - Identical configuration for Samba on FreeBSD is working like a charm. :-/**

I'm working on it for couple of day for now and i'm little tired. Give me some tips, please...

Samba works well from Windows machines through IP addresses (shares accessible) but it isn't visible in Network Neighbourhood (Windows)

**smb.conf:**

[global]
domain master = no
preferred master = yes
local master = yes

workgroup = WORKGROUP
netbios name = biliskner
server string = Komputer w norce
browseable = yes
security = share
#wins support = yes
#name resolve order = wins host lmhosts bcast
interfaces = eth0 lo

[zdjecia]
comment = Zdjecia cyfrowe
path = /media/disk/zdjecia
create mask = 0777
directory mask = 0777
browseable = yes
writable = no
guest ok = yes


**root@biliskner:/etc/samba# findsmb**

                               *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION
---------------------------------------------------------------------
172.18.1.5      BILISKNER     +[WORKGROUP] [Unix] [Samba 3.5.8]

**LANscanner v1.3 - ScottiesTech.Info (runned on windows machine)**

Scanning LAN...

XPEN1             172.18.1.27  08-00-27-1F-B8-AE WORKGROUP   MASTER

Press any key to exit...

Workgroup is of course the same on every machine. Both machines are in the same subnet.

They can see each other, i can ping them both ways, shares are available and accessible. **Samba machine isn't visible in Network Neighbourhood**.

Pleeease... Help.




[B]nmbd Logfile:

[/B][2011/08/25 01:14:42.257620,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****

  Samba name server BILISKNER is now a local master browser for workgroup WORKGROUP on subnet 172.18.1.5

  *****
[2011/08/25 01:14:42.258210,  1] nmbd/nmbd_incomingrequests.c:327(process_node_status_request)
  process_node_status_request: status request for name WORKGROUP<1b> from IP 172.18.1.5 on subnet UNICAST_SUBNET - name not found.
[2011/08/25 01:14:48.264571,  1] nmbd/nmbd_incomingrequests.c:327(process_node_status_request)
  process_node_status_request: status request for name WORKGROUP<1b> from IP 172.18.1.5 on subnet UNICAST_SUBNET - name not found.
[2011/08/25 01:14:53.267197,  1] nmbd/nmbd_incomingrequests.c:327(process_node_status_request)
  process_node_status_request: status request for name WORKGROUP<1b> from IP 172.18.1.5 on subnet UNICAST_SUBNET - name not found.
[2011/08/25 01:14:58.272074,  1] nmbd/nmbd_incomingrequests.c:327(process_node_status_request)
  process_node_status_request: status request for name WORKGROUP<1b> from IP 172.18.1.5 on subnet UNICAST_SUBNET - name not found.
[2011/08/25 01:15:03.277435,  0] nmbd/nmbd_browsesync.c:247(domain_master_node_status_fail)
  domain_master_node_status_fail:
  Doing a node status request to the domain master browser
  for workgroup WORKGROUP at IP 172.18.1.5 failed.
  Cannot sync browser lists.[B]

Hmm... 172.18.1.5 is the local IP address... Why it is named "subnet"?[/B]

---

