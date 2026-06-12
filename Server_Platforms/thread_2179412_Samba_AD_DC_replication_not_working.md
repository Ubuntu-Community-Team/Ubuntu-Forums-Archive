---
title: "Samba AD DC replication not working"
date: 2013-10-08
forum: Server Platforms
---

### Post by Abhijeet_Kumar on 2013-10-08
Hi

I am having issues with replication of samba DC servers. My setup is following. I had a Windows Server which had AD setup before and I copied and migrated that to a samba DC, named dc1(samba 4.0.3). Now i made a backup DC named dc2(samba 4.0.7). The first replication was successful and i am able to use the backup DC in case the primary failed. but in the mean time i have added a couple of new entries on the primary DC which are not showing on the backup. I ran the command "samba-tool drs showrepl" which gives me following error

root@dc1:~# samba-tool drs showrepl
Unknown resolve method 'hosts'
ERROR(<class 'samba.drs_utils.drsException'>): DRS connection to dc1.ftk.local failed - drsException: DRS connection to dc1.ftk.local failed: (-1073741772, 'NT_STATUS_OBJECT_NAME_NOT_FOUND')
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/drs.py", line 39, in drsuapi_connect
    (ctx.drsuapi, ctx.drsuapi_handle, ctx.bind_supported_extensions) = drs_utils.drsuapi_connect(ctx.server, ctx.lp, ctx.creds)
  File "/usr/local/samba/lib/python2.7/site-packages/samba/drs_utils.py", line 54, in drsuapi_connect
    raise drsException("DRS connection to %s failed: %s" % (server, e))


root@dc2:~# samba-tool drs showrepl
Unknown resolve method 'hosts'
ERROR(<class 'samba.drs_utils.drsException'>): DRS connection to dc2.ftk.local failed - drsException: DRS connection to dc2.ftk.local failed: (-1073741772, 'NT_STATUS_OBJECT_NAME_NOT_FOUND')
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/drs.py", line 39, in drsuapi_connect
    (ctx.drsuapi, ctx.drsuapi_handle, ctx.bind_supported_extensions) = drs_utils.drsuapi_connect(ctx.server, ctx.lp, ctx.creds)
  File "/usr/local/samba/lib/python2.7/site-packages/samba/drs_utils.py", line 54, in drsuapi_connect
    raise drsException("DRS connection to %s failed: %s" % (server, e))

The log files are filled with messages like this:

[2013/10/08 10:26:36,  0] ../source4/libcli/resolve/resolve_lp.c:43(lpcfg_resolve_context)
  Unknown resolve method 'hosts'
[2013/10/08 10:26:36,  0] ../source4/libcli/resolve/resolve_lp.c:43(lpcfg_resolve_context)
  Unknown resolve method 'hosts'

I googled and found that probably upgrading the samba on primary will help. Did the upgrade and the primary DC is running 4.0.9. 

anyone has any clues as to what this error is pointing to??

---

### Post by lingpanda on 2013-10-10
A couple things. Can you run the following and give me the output from your primary DC?

```
samba-tool fsmo show
```

As well as 

```
samba-tool drs kcc
```

---

### Post by Abhijeet_Kumar on 2013-10-14
Requested outputs: 

root@dc1:~# samba-tool fsmo show
InfrastructureMasterRole owner: CN=NTDS Settings,CN=DC1,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local
RidAllocationMasterRole owner: CN=NTDS Settings,CN=DC1,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local
PdcEmulationMasterRole owner: CN=NTDS Settings,CN=DC1,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local
DomainNamingMasterRole owner: CN=NTDS Settings,CN=DC1,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local
SchemaMasterRole owner: CN=NTDS Settings,CN=DC1,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local


root@dc1:~# samba-tool drs kcc
Unknown resolve method 'hosts'
ERROR(<class 'samba.drs_utils.drsException'>): DRS connection to dc1.ftk.local failed - drsException: DRS connection to dc1.ftk.local failed: (-1073741772, 'NT_STATUS_OBJECT_NAME_NOT_FOUND')
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/drs.py", line 39, in drsuapi_connect
    (ctx.drsuapi, ctx.drsuapi_handle, ctx.bind_supported_extensions) = drs_utils.drsuapi_connect(ctx.server, ctx.lp, ctx.creds)
  File "/usr/local/samba/lib/python2.7/site-packages/samba/drs_utils.py", line 54, in drsuapi_connect
    raise drsException("DRS connection to %s failed: %s" % (server, e))



well, i do not see my secondary DC in the first output. I sense apocalypse for my DCs :mad:  And am dreading if I would have to set it up again since it has hundreds of entries

---

### Post by JnPson on 2013-10-14
Check
```
/etc/krb5.conf
``` to see if you didn't miss this lines:
```
libdefaults]
        dns_lookup_realm =true
        dns_lookup_kdc = true
        default_realm = MYDOMAIN.LAN

```
I'm no expert on this, just a thought.

---

### Post by lingpanda on 2013-10-14
> **Abhijeet_Kumar said:**
> Requested outputs: 

root@dc1:~# samba-tool fsmo show
InfrastructureMasterRole owner: CN=NTDS Settings,CN=DC1,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local
RidAllocationMasterRole owner: CN=NTDS Settings,CN=DC1,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local
PdcEmulationMasterRole owner: CN=NTDS Settings,CN=DC1,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local
DomainNamingMasterRole owner: CN=NTDS Settings,CN=DC1,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local
SchemaMasterRole owner: CN=NTDS Settings,CN=DC1,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local


root@dc1:~# samba-tool drs kcc
Unknown resolve method 'hosts'
ERROR(<class 'samba.drs_utils.drsException'>): DRS connection to dc1.ftk.local failed - drsException: DRS connection to dc1.ftk.local failed: (-1073741772, 'NT_STATUS_OBJECT_NAME_NOT_FOUND')
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/drs.py", line 39, in drsuapi_connect
    (ctx.drsuapi, ctx.drsuapi_handle, ctx.bind_supported_extensions) = drs_utils.drsuapi_connect(ctx.server, ctx.lp, ctx.creds)
  File "/usr/local/samba/lib/python2.7/site-packages/samba/drs_utils.py", line 54, in drsuapi_connect
    raise drsException("DRS connection to %s failed: %s" % (server, e))



well, i do not see my secondary DC in the first output. I sense apocalypse for my DCs :mad:  And am dreading if I would have to set it up again since it has hundreds of entries

    You're not supposed to see your 2nd DC on the FSMO command unless your transferred roles. I just wanted to make sure you transferred the roles from your Old Windows DC. All is good. 

    The issue appears to be your Samba DC isn't able to resolve host names. What is the output of 

```
vi /etc/network/interfaces

```

---

### Post by lingpanda on 2013-10-14
> **JnPson said:**
> Check
```
/etc/krb5.conf
``` to see if you didn't miss this lines:
```
libdefaults]
        dns_lookup_realm =true
        dns_lookup_kdc = true
        default_realm = MYDOMAIN.LAN

```
I'm no expert on this, just a thought.

He is having a DNS issue so this could be the cause.

---

### Post by Abhijeet_Kumar on 2013-10-15
> **JnPson said:**
> Check
```
/etc/krb5.conf
``` to see if you didn't miss this lines:
```
libdefaults]
        dns_lookup_realm =true
        dns_lookup_kdc = true
        default_realm = MYDOMAIN.LAN

```
I'm no expert on this, just a thought.

I looked into the krb5.conf on the primary and backup server and they both seem to be as you mentioned. Thanks for your thought though. It seems to have DNS issue yes. it somehow is not able to make DRS connection to the server which i have no idea what it means. Below is my output for /etc/network/interfaces

**auto eth0**
**iface eth0 inet static**
**    address 192.168.111.8**
**    netmask 255.255.255.0**
**    gateway 192.168.111.1**
**    dns-nameservers 192.168.111.8**
**    dns-search ftk.local**

Output on secondary DC

**# The primary network interface**
**auto eth0**
**iface eth0 inet static**
**  address 192.168.122.160**
**  netmask 255.255.255.0**
**  gateway 192.168.122.1**
**  broadcast 192.168.122.255**
**  network 192.168.122.0**


  dns-nameservers 192.168.111.8
  dns-search ftk.local


In this setup, I am using the internal DNS server of Samba and not BIND or anything else. Before I was using a windows DNS on a windows server. The Samba primary DC eventually copied the DNS content of the Windows Server and started running it. That is the reason I have mentioned the primary DC as the DNS server. Well, I have been having trouble with the DNS internal server of Samba which i would also like to discuss, maybe in another thread. But the problem in short is that I am not able to add or edit or even see the DNS entries. The moment i shut the Windows DNS down, I have never been able to add any new entries or edit or do whatever using Windows Administrative tools or even the command line.

---

### Post by JnPson on 2013-10-15
I would put both DC's as dns-nameservers in both dc1 and dc2* /etc/network/interfaces* as this
```

dns-nameservers 192.168.111.8 192.168.122.160

```
This is how I have set up my servers as both are DNS by default installation. This is if you have chosen to use SAMBA_INTERNAL as DNS.
//I missed the last part where you're saying you use internal DNS.

---

### Post by lingpanda on 2013-10-15
> **Abhijeet_Kumar said:**
> I looked into the krb5.conf on the primary and backup server and they both seem to be as you mentioned. Thanks for your thought though. It seems to have DNS issue yes. it somehow is not able to make DRS connection to the server which i have no idea what it means. Below is my output for /etc/network/interfaces

**auto eth0**
**iface eth0 inet static**
**    address 192.168.111.8**
**    netmask 255.255.255.0**
**    gateway 192.168.111.1**
**    dns-nameservers 192.168.111.8**
**    dns-search ftk.local**

Output on secondary DC

**# The primary network interface**
**auto eth0**
**iface eth0 inet static**
**  address 192.168.122.160**
**  netmask 255.255.255.0**
**  gateway 192.168.122.1**
**  broadcast 192.168.122.255**
**  network 192.168.122.0**


  dns-nameservers 192.168.111.8
  dns-search ftk.local


In this setup, I am using the internal DNS server of Samba and not BIND or anything else. Before I was using a windows DNS on a windows server. The Samba primary DC eventually copied the DNS content of the Windows Server and started running it. That is the reason I have mentioned the primary DC as the DNS server. Well, I have been having trouble with the DNS internal server of Samba which i would also like to discuss, maybe in another thread. But the problem in short is that I am not able to add or edit or even see the DNS entries. The moment i shut the Windows DNS down, I have never been able to add any new entries or edit or do whatever using Windows Administrative tools or even the command line.

    DRS stands for **Directory Replication System**. Samba is unable to perform this function. Can you connect to your samba DNS on DC1 using the Windows DNS Manager? If not can you provide me with the following output on your DC's?

```
/usr/local/samba/bin/samba-tool dns serverinfo DC1 -Uadministrator
```
and
```
/usr/local/samba/bin/samba-tool dns query samba4pdc DC1 @ ALL -Uadministrator
```

    I do see you defined your network on DC2 but not on DC1. I for example use different subnets but I use 192.168.0.0 on all DC's. As well as broadcast 192.168.0.255. Can you provide me with the output of

```
/etc/resolv.conf
```

---

### Post by Abhijeet_Kumar on 2013-10-15
> **JnPson said:**
> I would put both DC's as dns-nameservers in both dc1 and dc2* /etc/network/interfaces* as this
```

dns-nameservers 192.168.111.8 192.168.122.160

```
This is how I have set up my servers as both are DNS by default installation. This is if you have chosen to use SAMBA_INTERNAL as DNS.
//I missed the last part where you're saying you use internal DNS.

I did as you said and provided both the ip addresses as DNS servers. But i think it is just scratching the surface and not getting beneath the underlying problem.

---

### Post by Abhijeet_Kumar on 2013-10-15
> **lingpanda said:**
> DRS stands for **Directory Replication System**. Samba is unable to perform this function. Can you connect to your samba DNS on DC1 using the Windows DNS Manager? If not can you provide me with the following output on your DC's?

```
/usr/local/samba/bin/samba-tool dns serverinfo DC1 -Uadministrator
```
and
```
/usr/local/samba/bin/samba-tool dns query samba4pdc DC1 @ ALL -Uadministrator
```

    I do see you defined your network on DC2 but not on DC1. I for example use different subnets but I use 192.168.0.0 on all DC's. As well as broadcast 192.168.0.255. Can you provide me with the output of

```
/etc/resolv.conf
```

Oh btw, before going ahead with providing the outputs, i feel i should provide little background of my setup. The DC1 is located internally in the local network while DC2 is hosted as a guest on a physical machine at a remote location. The physical machine has a global address and hence is connected with an ipsec tunnel to the internal network and in order to differentiate the networks, i have setup different subnets. The local subnet is 192.168.111.0 and the remote subnet is 192.168.122.0  ... also, while setting up the ipsec tunnel, the remote subnet of 192.168.122.0 in the ipsec configuration did not work which forced me to use NAT. So, DC2 is locally known as 192.168.160.160 and gets translated to 192.168.122.160 on remote physical machine. 


And yes, I am unable to connect to samba DNS using Windows DNS Manager which is another issue that I have to address. And BTW, I am using SAMBA_INTERNAL as the DNS which is the internal built in DNS of samba.

**Output on primary DC:**

```

root@dc1:~# /usr/local/samba/bin/samba-tool dns serverinfo DC1 -UadministratorUnknown resolve method 'hosts'
Unknown resolve method 'hosts'
Password for [FTK-LOCAL\administrator]:
  dwVersion                   : 0xece0205
  fBootMethod                 : DNS_BOOT_METHOD_DIRECTORY
  fAdminConfigured            : FALSE
  fAllowUpdate                : TRUE
  fDsAvailable                : TRUE
  pszServerName               : DC1.ftk.local
  pszDsContainer              : CN=MicrosoftDNS,DC=DomainDnsZones,DC=FTK,DC=local
  aipServerAddrs              : ['192.168.111.8 (53)']
  aipListenAddrs              : ['192.168.111.8 (53)']
  aipForwarders               : []
  dwLogLevel                  : 0
  dwDebugLevel                : 0
  dwForwardTimeout            : 3
  dwRpcPrototol               : 0x5
  dwNameCheckFlag             : DNS_ALLOW_MULTIBYTE_NAMES
  cAddressAnswerLimit         : 0
  dwRecursionRetry            : 3
  dwRecursionTimeout          : 8
  dwMaxCacheTtl               : 86400
  dwDsPollingInterval         : 180
  dwScavengingInterval        : 0
  dwDefaultRefreshInterval    : 168
  dwDefaultNoRefreshInterval  : 168
  fAutoReverseZones           : FALSE
  fAutoCacheUpdate            : FALSE
  fRecurseAfterForwarding     : FALSE
  fForwardDelegations         : TRUE
  fNoRecursion                : FALSE
  fSecureResponses            : FALSE
  fRoundRobin                 : TRUE
  fLocalNetPriority           : FALSE
  fBindSecondaries            : FALSE
  fWriteAuthorityNs           : FALSE
  fStrictFileParsing          : FALSE
  fLooseWildcarding           : FALSE
  fDefaultAgingState          : FALSE
  dwRpcStructureVersion       : 0x2
  aipLogFilter                : []
  pwszLogFilePath             : None
  pszDomainName               : FTK.local
  pszForestName               : FTK.local
  pszDomainDirectoryPartition : DC=DomainDnsZones,DC=FTK,DC=local
  pszForestDirectoryPartition : DC=ForestDnsZones,DC=FTK,DC=local
  dwLocalNetPriorityNetMask   : 0xff
  dwLastScavengeTime          : 0
  dwEventLogLevel             : 4
  dwLogFileMaxSize            : 0
  dwDsForestVersion           : 2
  dwDsDomainVersion           : 2
  dwDsDsaVersion              : 4
  fReadOnlyDC                 : FALSE

root@dc1:~# cat /etc/resolv.conf
nameserver 192.168.111.8
search ftk.local


```

**Output on backup DC**

```
root@dc2:~# /usr/local/samba/bin/samba-tool dns serverinfo DC1 -UadministratorUnknown resolve method 'hosts'
ERROR(runtime): uncaught exception - (-1073741772, 'NT_STATUS_OBJECT_NAME_NOT_FOUND')
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/__init__.py", line 175, in _run
    return self.run(*args, **kwargs)
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/dns.py", line 701, in run
    dns_conn = dns_connect(server, self.lp, self.creds)
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/dns.py", line 37, in dns_connect
    dns_conn = dnsserver.dnsserver(binding_str, lp, creds)

root@dc2:~# cat /etc/resolv.conf
nameserver 192.168.111.8
search webservices.ftk.de ftk.local

```


I also thought that this output would be of some help. It shows same on both servers which according to the setup guide is perfect.

```
root@dc2:~# ldbsearch -H /usr/local/samba/private/sam.ldb '(invocationid=*)' --cross-ncs objectguid
# record 1
dn: CN=NTDS Settings,CN=DC2,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local
objectGUID: 43960ec7-1fe1-45fa-83f0-629f02e115ad


# record 2
dn: CN=NTDS Settings,CN=DC1,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local
objectGUID: 5d8d6fb0-6658-4b76-863d-baebc3c28c2b


# record 3
dn: CN=NTDS Settings,CN=EXCHANGE03,CN=Servers,CN=Standardname-des-ersten-Standorts,CN=Sites,CN=Configuration,DC=FTK,DC=local
objectGUID: f61ebbbf-34f7-4e62-89b4-3163c532e59d


# returned 3 records
# 3 entries
# 0 referrals

```
The point here is that it still shows the old Microsoft AD DC as one of the entries, which actually should not be a problem, but when things dont work, people get skeptic about everything and i really want to get rid of that thing.

---

### Post by Abhijeet_Kumar on 2013-10-15
Fortunately, I was able to resolve the [COLOR=#000000]**samba-tool drs showrepl** problem. The problem was that in DC2, the /etc/hosts file had following

```
192.168.160.160 dc2.ftk.local dc2
```

it wasnt able to recognize the ip address since DC2 has ip address of 192.168.122.160..... and the 160.160 is the IP address from the local network as mentioned in the above post. 
But the problem remains that it is not copying or replicating from primary server DC1. On DC1, there is still error message like

[/COLOR]```
root@dc1:~# samba-tool drs kcc
ERROR(runtime): DsExecuteKCC failed - (-1073610723, 'NT_STATUS_RPC_PROTOCOL_ERROR')
root@dc1:~#

```
atleast its not the big **unable to recognize hosts** error. This works perfectly on DC2 now,

```
root@dc2:~# samba-tool drs kcc
Consistency check on dc2.ftk.local successful.
root@dc2:~#



```

---

### Post by lingpanda on 2013-10-15
> **Abhijeet_Kumar said:**
> [COLOR=#000000]
it wasnt able to recognize the ip address since DC2 has ip address of 192.168.122.160..... and the 160.160 is the IP address from the local network as mentioned in the above post. 
But the problem remains that it is not copying or replicating from primary server DC1. On DC1, there is still error message like

[/COLOR]```
root@dc1:~# samba-tool drs kcc
ERROR(runtime): DsExecuteKCC failed - (-1073610723, 'NT_STATUS_RPC_PROTOCOL_ERROR')
root@dc1:~#

```
atleast its not the big **unable to recognize hosts** error. This works perfectly on DC2 now,

```
root@dc2:~# samba-tool drs kcc
Consistency check on dc2.ftk.local successful.
root@dc2:~#



```

Verify Samba is running on DC1. 

```
#service samba4 status
```

Can you connect to shares on DC1?

```
/usr/local/samba/bin/smbclient -L localhost -U%
```

---

### Post by lubomir.fedor on 2013-10-30
What is "name resolve order" in your smb.conf? It's possible (well... quite probable) you have set it to hosts instead of host. Example of my working configuration:
```
name resolve order = wins host bcast
```

---

### Post by Abhijeet_Kumar on 2013-11-11
> **lingpanda said:**
> Verify Samba is running on DC1. 

```
#service samba4 status
```

Can you connect to shares on DC1?

```
/usr/local/samba/bin/smbclient -L localhost -U%
```

Hi

It is running and i can see my shares

samba4 start/running, process 17586
root@dc1:~# /usr/local/samba/bin/smbclient -L localhost -U%
Domain=[FTK-LOCAL] OS=[Unix] Server=[Samba 4.1.0]


        Sharename       Type      Comment
        ---------       ----      -------
        netlogon        Disk
        sysvol          Disk
        profiles        Disk
        public          Disk
        projekte        Disk
        user            Disk
        IPC$            IPC       IPC Service
Domain=[FTK-LOCAL] OS=[Unix] Server=[Samba 4.1.0]


        Server               Comment
        ---------            -------


        Workgroup            Master
        ---------            -------
root@dc1:~#

---

### Post by Abhijeet_Kumar on 2013-11-11
> **lubomir.fedor said:**
> What is "name resolve order" in your smb.conf? It's possible (well... quite probable) you have set it to hosts instead of host. Example of my working configuration:
```
name resolve order = wins host bcast
```

Lubomir

The name resolve order was
**name resolve order = host wins bcast**before.

I changed it to 
**name resolve order = wins host bcast**and re run the samba...still getting this error...

Also there is another problem with the DNS MMC for this server. I am able to edit or add or do anything in DNS on this server using samba-tool but while using the microsoft DNS MMC tool to administer, it shows only so much as in the figure below. I tried testing if it is able to interact with the samba server and added a test zone using MMC. When i look at the entries using Apache Directory Studio, it is showing me the zone as well as using **samba-tool dns zonelist dc1 **shows the added test zone. any idea anybody why this is happening??

**  pszZoneName                 : test.ftk**
**  Flags                       : DNS_RPC_ZONE_DSINTEGRATED DNS_RPC_ZONE_UPDATE_SECURE**
**  ZoneType                    : DNS_ZONE_TYPE_PRIMARY**
**  Version                     : 50**
**  dwDpFlags                   : DNS_DP_AUTOCREATED DNS_DP_DOMAIN_DEFAULT DNS_DP_ENLISTED**
**  pszDpFqdn                   : DomainDnsZones.FTK.local**




[ATTACH=CONFIG]247764[/ATTACH]

---

### Post by lingpanda on 2013-11-11
How easy is it for you to transfer the roles to DC2 and demote DC1? Rebuild the server and join again? Is this production? One last command that may help
```

#samba-tool drs kcc dc1 -d 10
```

---

### Post by Abhijeet_Kumar on 2013-11-13
> **lingpanda said:**
> How easy is it for you to transfer the roles to DC2 and demote DC1? Rebuild the server and join again? Is this production? One last command that may help
```

#samba-tool drs kcc dc1 -d 10
```
```
root@dc1:~# samba-tool drs kcc dc1 -d 10INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
lpcfg_load: refreshing parameters from /usr/local/samba/etc/smb.conf
params.c:pm_process() - Processing configuration file "/usr/local/samba/etc/smb.conf"
Processing section "[global]"
Processing section "[netlogon]"
Processing section "[sysvol]"
Processing section "[profiles]"
Processing section "[public]"
Processing section "[projekte]"
Processing section "[user]"
pm_process() returned Yes
ldb: ldb_trace_request: SEARCH
 dn: @MODULES
 scope: base
 expr: (@LIST=*)
 attr: @LIST
 control: <NONE>


ldb: ldb_trace_request: (tdb)->search
ldb: Added timed event "ltdb_callback": 0x2f96a40


ldb: Added timed event "ltdb_timeout": 0x2f96b00


ldb: Running timer event 0x2f96a40 "ltdb_callback"


ldb: ldb_trace_response: ENTRY
dn: @MODULES
@LIST: samba_secrets






ldb: Destroying timer event 0x2f96b00 "ltdb_timeout"


ldb: Ending timer event 0x2f96a40 "ltdb_callback"


ldb: ldb_trace_request: REGISTER_CONTROL
1.2.840.113556.1.4.1413
 control: <NONE>


ldb: ldb_asprintf/set_errstring: unable to find module or backend to handle operation: request
ldb: ldb_trace_request: SEARCH
 dn: <rootDSE>
 scope: base
 expr: (objectClass=*)
 attr: rootDomainNamingContext
 attr: configurationNamingContext
 attr: schemaNamingContext
 attr: defaultNamingContext
 control: <NONE>


ldb: ldb_trace_request: (rdn_name)->search
ldb: ldb_trace_next_request: (tdb)->search
ldb: Added timed event "ltdb_callback": 0x2fb4be0


ldb: Added timed event "ltdb_timeout": 0x2f98540


ldb: Running timer event 0x2fb4be0 "ltdb_callback"


ldb: ldb_asprintf/set_errstring: NULL Base DN invalid for a base search
ldb: Destroying timer event 0x2f98540 "ltdb_timeout"


ldb: Ending timer event 0x2fb4be0 "ltdb_callback"


ldb_wrap open of secrets.ldb
ldb: ldb_trace_request: SEARCH
 dn: cn=Primary Domains
 scope: sub
 expr: (&(flatname=FTK-LOCAL)(objectclass=primaryDomain))
 attr: <ALL>
 control: <NONE>


ldb: ldb_trace_request: (rdn_name)->search
ldb: ldb_trace_next_request: (tdb)->search
ldb: Added timed event "ltdb_callback": 0x2fb54d0


ldb: Added timed event "ltdb_timeout": 0x2fb5590


ldb: Running timer event 0x2fb54d0 "ltdb_callback"


ldb: ldb_trace_response: ENTRY
dn: flatname=FTK-LOCAL,cn=Primary Domains
msDS-KeyVersionNumber: 2
objectClass: top
objectClass: primaryDomain
objectClass: kerberosSecret
objectSid: S-1-5-21-3499643746-1985428922-642895725
privateKeytab: secrets.keytab
realm: FTK.local
saltPrincipal: host/dc1.ftk.local@FTK.LOCAL
samAccountName: DC1$
secret: lP$nLCF.;I=C,gWLZc]ZBkDP>sX%dEjj
secureChannelType: 6
servicePrincipalName: HOST/dc1
servicePrincipalName: HOST/dc1.ftk.local
objectGUID: 79b49c92-1e90-44a4-8bd2-f01ff90b9fc6
whenCreated: 20130214141315.0Z
whenChanged: 20130214141315.0Z
uSNCreated: 7
uSNChanged: 7
name: FTK-LOCAL
flatname: FTK-LOCAL
distinguishedName: flatname=FTK-LOCAL,cn=Primary Domains






ldb: Destroying timer event 0x2fb5590 "ltdb_timeout"


ldb: Ending timer event 0x2fb54d0 "ltdb_callback"


GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'schannel' registered
GENSEC backend 'spnego' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Using binding ncacn_ip_tcp:dc1[,seal,print]
Mapped to DCERPC endpoint 135
added interface eth0 ip=192.168.111.8 bcast=192.168.111.255 netmask=255.255.255.0
added interface eth0 ip=192.168.111.8 bcast=192.168.111.255 netmask=255.255.255.0
Socket options:
        SO_KEEPALIVE = 0
        SO_REUSEADDR = 0
        SO_BROADCAST = 1
        Could not test socket option TCP_NODELAY.
        Could not test socket option TCP_KEEPCNT.
        Could not test socket option TCP_KEEPIDLE.
        Could not test socket option TCP_KEEPINTVL.
        IPTOS_LOWDELAY = 0
        IPTOS_THROUGHPUT = 0
        SO_SNDBUF = 212992
        SO_RCVBUF = 212992
        SO_SNDLOWAT = 1
        SO_RCVLOWAT = 1
        SO_SNDTIMEO = 0
        SO_RCVTIMEO = 0
        Could not test socket option TCP_QUICKACK.
        Could not test socket option TCP_DEFER_ACCEPT.
Queueing nbt packet to 127.0.0.1:137
     request: struct nbt_name_packet
        name_trn_id              : 0x19ab (6571)
        operation                : 0x0100 (256)
            0x00: NBT_RCODE                 (0)
               0: NBT_FLAG_BROADCAST
               0: NBT_FLAG_RECURSION_AVAIL
               1: NBT_FLAG_RECURSION_DESIRED
               0: NBT_FLAG_TRUNCATION
               0: NBT_FLAG_AUTHORITATIVE
            0x00: NBT_OPCODE                (0)
               0: NBT_FLAG_REPLY
        qdcount                  : 0x0001 (1)
        ancount                  : 0x0000 (0)
        nscount                  : 0x0000 (0)
        arcount                  : 0x0000 (0)
        questions: ARRAY(1)
            questions: struct nbt_name_question
                name: struct nbt_name
                    name                     : 'DC1'
                    scope                    : NULL
                    type                     : NBT_NAME_SERVER (0x20)
                question_type            : NBT_QTYPE_NETBIOS (0x20)
                question_class           : NBT_QCLASS_IP (0x1)
        answers: ARRAY(0)
        nsrecs: ARRAY(0)
        additional: ARRAY(0)
        padding                  : DATA_BLOB length=0
Received nbt packet of length 68 from 127.0.0.1:137
     packet: struct nbt_name_packet
        name_trn_id              : 0x19ab (6571)
        operation                : 0x8580 (34176)
            0x00: NBT_RCODE                 (0)
               0: NBT_FLAG_BROADCAST
               1: NBT_FLAG_RECURSION_AVAIL
               1: NBT_FLAG_RECURSION_DESIRED
               0: NBT_FLAG_TRUNCATION
               1: NBT_FLAG_AUTHORITATIVE
            0x00: NBT_OPCODE                (0)
               1: NBT_FLAG_REPLY
        qdcount                  : 0x0000 (0)
        ancount                  : 0x0001 (1)
        nscount                  : 0x0000 (0)
        arcount                  : 0x0000 (0)
        questions: ARRAY(0)
        answers: ARRAY(1)
            answers: struct nbt_res_rec
                name: struct nbt_name
                    name                     : 'DC1'
                    scope                    : NULL
                    type                     : NBT_NAME_SERVER (0x20)
                rr_type                  : NBT_QTYPE_NETBIOS (0x20)
                rr_class                 : NBT_QCLASS_IP (0x1)
                ttl                      : 0x00000000 (0)
                rdata                    : union nbt_rdata(case 0x20)
                netbios: struct nbt_rdata_netbios
                    length                   : 0x000c (12)
                    addresses: ARRAY(2)
                        addresses: struct nbt_rdata_address
                            nb_flags                 : 0x4600 (17920)
                                   1: NBT_NM_PERMANENT
                                   1: NBT_NM_ACTIVE
                                   0: NBT_NM_CONFLICT
                                   0: NBT_NM_DEREGISTER
                                0x02: NBT_NM_OWNER_TYPE         (2)
                                   0: NBT_NM_GROUP
                            ipaddr                   : 192.168.111.8
                        addresses: struct nbt_rdata_address
                            nb_flags                 : 0x4600 (17920)
                                   1: NBT_NM_PERMANENT
                                   1: NBT_NM_ACTIVE
                                   0: NBT_NM_CONFLICT
                                   0: NBT_NM_DEREGISTER
                                0x02: NBT_NM_OWNER_TYPE         (2)
                                   0: NBT_NM_GROUP
                            ipaddr                   : 192.168.111.8
        nsrecs: ARRAY(0)
        additional: ARRAY(0)
        padding                  : DATA_BLOB length=0
rpc request data:
[0000] 01 00 00 00 00 00 00 00   00 00 00 00 00 00 00 00   ........ ........
[0010] 00 00 00 00 02 00 00 00   4B 00 00 00 4B 00 00 00   ........ K...K...
[0020] 05 00 13 00 0D 35 42 51   E3 06 4B D1 11 AB 04 00   .....5BQ ..K.....
[0030] C0 4F C2 DC D2 04 00 02   00 00 00 13 00 0D 04 5D   .O...... .......]
[0040] 88 8A EB 1C C9 11 9F E8   08 00 2B 10 48 60 02 00   ........ ..+.H`..
[0050] 02 00 00 00 01 00 0B 02   00 00 00 01 00 07 02 00   ........ ........
[0060] 00 00 01 00 09 04 00 00   00 00 00 00 00 00 00 00   ........ ........
[0070] 00 00 00 00 00 00 00 00   00 00 00 00 00 00 00 00   ........ ........
[0080] 01 00 00 00                                       ....
rpc reply data:
[0000] 00 00 00 00 00 00 00 00   00 00 00 00 00 00 00 00   ........ ........
[0010] 00 00 00 00 01 00 00 00   01 00 00 00 00 00 00 00   ........ ........
[0020] 01 00 00 00 03 00 00 00   4B 00 00 00 4B 00 00 00   ........ K...K...
[0030] 05 00 13 00 0D 35 42 51   E3 06 4B D1 11 AB 04 00   .....5BQ ..K.....
[0040] C0 4F C2 DC D2 04 00 02   00 00 00 13 00 0D 04 5D   .O...... .......]
[0050] 88 8A EB 1C C9 11 9F E8   08 00 2B 10 48 60 02 00   ........ ..+.H`..
[0060] 02 00 00 00 01 00 0B 02   00 00 00 01 00 07 02 00   ........ ........
[0070] 04 00 01 00 09 04 00 00   00 00 00 00 00 00 00 00   ........ ........
Mapped to DCERPC endpoint 1024
added interface eth0 ip=192.168.111.8 bcast=192.168.111.255 netmask=255.255.255.0
added interface eth0 ip=192.168.111.8 bcast=192.168.111.255 netmask=255.255.255.0
Socket options:
        SO_KEEPALIVE = 0
        SO_REUSEADDR = 0
        SO_BROADCAST = 1
        Could not test socket option TCP_NODELAY.
        Could not test socket option TCP_KEEPCNT.
        Could not test socket option TCP_KEEPIDLE.
        Could not test socket option TCP_KEEPINTVL.
        IPTOS_LOWDELAY = 0
        IPTOS_THROUGHPUT = 0
        SO_SNDBUF = 212992
        SO_RCVBUF = 212992
        SO_SNDLOWAT = 1
        SO_RCVLOWAT = 1
        SO_SNDTIMEO = 0
        SO_RCVTIMEO = 0
        Could not test socket option TCP_QUICKACK.
        Could not test socket option TCP_DEFER_ACCEPT.
Queueing nbt packet to 127.0.0.1:137
     request: struct nbt_name_packet
        name_trn_id              : 0xea44 (59972)
        operation                : 0x0100 (256)
            0x00: NBT_RCODE                 (0)
               0: NBT_FLAG_BROADCAST
               0: NBT_FLAG_RECURSION_AVAIL
               1: NBT_FLAG_RECURSION_DESIRED
               0: NBT_FLAG_TRUNCATION
               0: NBT_FLAG_AUTHORITATIVE
            0x00: NBT_OPCODE                (0)
               0: NBT_FLAG_REPLY
        qdcount                  : 0x0001 (1)
        ancount                  : 0x0000 (0)
        nscount                  : 0x0000 (0)
        arcount                  : 0x0000 (0)
        questions: ARRAY(1)
            questions: struct nbt_name_question
                name: struct nbt_name
                    name                     : 'DC1'
                    scope                    : NULL
                    type                     : NBT_NAME_SERVER (0x20)
                question_type            : NBT_QTYPE_NETBIOS (0x20)
                question_class           : NBT_QCLASS_IP (0x1)
        answers: ARRAY(0)
        nsrecs: ARRAY(0)
        additional: ARRAY(0)
        padding                  : DATA_BLOB length=0
Received nbt packet of length 68 from 127.0.0.1:137
     packet: struct nbt_name_packet
        name_trn_id              : 0xea44 (59972)
        operation                : 0x8580 (34176)
            0x00: NBT_RCODE                 (0)
               0: NBT_FLAG_BROADCAST
               1: NBT_FLAG_RECURSION_AVAIL
               1: NBT_FLAG_RECURSION_DESIRED
               0: NBT_FLAG_TRUNCATION
               1: NBT_FLAG_AUTHORITATIVE
            0x00: NBT_OPCODE                (0)
               1: NBT_FLAG_REPLY
        qdcount                  : 0x0000 (0)
        ancount                  : 0x0001 (1)
        nscount                  : 0x0000 (0)
        arcount                  : 0x0000 (0)
        questions: ARRAY(0)
        answers: ARRAY(1)
            answers: struct nbt_res_rec
                name: struct nbt_name
                    name                     : 'DC1'
                    scope                    : NULL
                    type                     : NBT_NAME_SERVER (0x20)
                rr_type                  : NBT_QTYPE_NETBIOS (0x20)
                rr_class                 : NBT_QCLASS_IP (0x1)
                ttl                      : 0x00000000 (0)
                rdata                    : union nbt_rdata(case 0x20)
                netbios: struct nbt_rdata_netbios
                    length                   : 0x000c (12)
                    addresses: ARRAY(2)
                        addresses: struct nbt_rdata_address
                            nb_flags                 : 0x4600 (17920)
                                   1: NBT_NM_PERMANENT
                                   1: NBT_NM_ACTIVE
                                   0: NBT_NM_CONFLICT
                                   0: NBT_NM_DEREGISTER
                                0x02: NBT_NM_OWNER_TYPE         (2)
                                   0: NBT_NM_GROUP
                            ipaddr                   : 192.168.111.8
                        addresses: struct nbt_rdata_address
                            nb_flags                 : 0x4600 (17920)
                                   1: NBT_NM_PERMANENT
                                   1: NBT_NM_ACTIVE
                                   0: NBT_NM_CONFLICT
                                   0: NBT_NM_DEREGISTER
                                0x02: NBT_NM_OWNER_TYPE         (2)
                                   0: NBT_NM_GROUP
                            ipaddr                   : 192.168.111.8
        nsrecs: ARRAY(0)
        additional: ARRAY(0)
        padding                  : DATA_BLOB length=0
Starting GENSEC mechanism spnego
Starting GENSEC submechanism gssapi_krb5
Error reading smb_krb5 reply packet: NT_STATUS_CONNECTION_REFUSED from 192.168.111.10
Received smb_krb5 packet of length 248
Error reading smb_krb5 reply packet: NT_STATUS_CONNECTION_REFUSED from 192.168.111.10
Received smb_krb5 packet of length 1195
Error reading smb_krb5 reply packet: NT_STATUS_CONNECTION_REFUSED from 192.168.111.10
Received smb_krb5 packet of length 1212
Error reading smb_krb5 reply packet: NT_STATUS_CONNECTION_REFUSED from 192.168.111.10
Received smb_krb5 packet of length 1228
../librpc/rpc/dcerpc_util.c:140: auth_pad_length 0
gensec_gssapi: credentials were delegated
GSSAPI Connection will be cryptographically sealed
../librpc/rpc/dcerpc_util.c:140: auth_pad_length 0
     drsuapi_DsBind: struct drsuapi_DsBind
        in: struct drsuapi_DsBind
            bind_guid                : *
                bind_guid                : e24d201a-4fd6-11d1-a3da-0000f875ae0d
            bind_info                : *
                bind_info: struct drsuapi_DsBindInfoCtr
                    length                   : 0x0000001c (28)
                    info                     : union drsuapi_DsBindInfo(case 28)
                    info28: struct drsuapi_DsBindInfo28
                        supported_extensions     : 0x0fefff7f (267386751)
                               1: DRSUAPI_SUPPORTED_EXTENSION_BASE
                               1: DRSUAPI_SUPPORTED_EXTENSION_ASYNC_REPLICATION
                               1: DRSUAPI_SUPPORTED_EXTENSION_REMOVEAPI
                               1: DRSUAPI_SUPPORTED_EXTENSION_MOVEREQ_V2
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHG_COMPRESS
                               1: DRSUAPI_SUPPORTED_EXTENSION_DCINFO_V1
                               1: DRSUAPI_SUPPORTED_EXTENSION_RESTORE_USN_OPTIMIZATION
                               0: DRSUAPI_SUPPORTED_EXTENSION_ADDENTRY
                               1: DRSUAPI_SUPPORTED_EXTENSION_KCC_EXECUTE
                               1: DRSUAPI_SUPPORTED_EXTENSION_ADDENTRY_V2
                               1: DRSUAPI_SUPPORTED_EXTENSION_LINKED_VALUE_REPLICATION
                               1: DRSUAPI_SUPPORTED_EXTENSION_DCINFO_V2
                               1: DRSUAPI_SUPPORTED_EXTENSION_INSTANCE_TYPE_NOT_REQ_ON_MOD
                               1: DRSUAPI_SUPPORTED_EXTENSION_CRYPTO_BIND
                               1: DRSUAPI_SUPPORTED_EXTENSION_GET_REPL_INFO
                               1: DRSUAPI_SUPPORTED_EXTENSION_STRONG_ENCRYPTION
                               1: DRSUAPI_SUPPORTED_EXTENSION_DCINFO_V01
                               1: DRSUAPI_SUPPORTED_EXTENSION_TRANSITIVE_MEMBERSHIP
                               1: DRSUAPI_SUPPORTED_EXTENSION_ADD_SID_HISTORY
                               1: DRSUAPI_SUPPORTED_EXTENSION_POST_BETA3
                               0: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREQ_V5
                               1: DRSUAPI_SUPPORTED_EXTENSION_GET_MEMBERSHIPS2
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREQ_V6
                               1: DRSUAPI_SUPPORTED_EXTENSION_NONDOMAIN_NCS
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREQ_V8
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREPLY_V5
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREPLY_V6
                               1: DRSUAPI_SUPPORTED_EXTENSION_ADDENTRYREPLY_V3
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREPLY_V7
                               1: DRSUAPI_SUPPORTED_EXTENSION_VERIFY_OBJECT
                               0: DRSUAPI_SUPPORTED_EXTENSION_XPRESS_COMPRESS
                               0: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREQ_V10
                               0: DRSUAPI_SUPPORTED_EXTENSION_RESERVED_PART2
                               0: DRSUAPI_SUPPORTED_EXTENSION_RESERVED_PART3
                        site_guid                : 00000000-0000-0000-0000-000000000000
                        pid                      : 0x00000000 (0)
                        repl_epoch               : 0x00000000 (0)
rpc request data:
[0000] 00 00 02 00 1A 20 4D E2   D6 4F D1 11 A3 DA 00 00   ..... M. .O......
[0010] F8 75 AE 0D 04 00 02 00   1C 00 00 00 1C 00 00 00   .u...... ........
[0020] 7F FF EF 0F 00 00 00 00   00 00 00 00 00 00 00 00   ........ ........
[0030] 00 00 00 00 00 00 00 00   00 00 00 00              ........ ....
../librpc/rpc/dcerpc_util.c:140: auth_pad_length 0
     drsuapi_DsBind: struct drsuapi_DsBind
        out: struct drsuapi_DsBind
            bind_info                : *
                bind_info: struct drsuapi_DsBindInfoCtr
                    length                   : 0x0000001c (28)
                    info                     : union drsuapi_DsBindInfo(case 28)
                    info28: struct drsuapi_DsBindInfo28
                        supported_extensions     : 0x2fffff6f (805306223)
                               1: DRSUAPI_SUPPORTED_EXTENSION_BASE
                               1: DRSUAPI_SUPPORTED_EXTENSION_ASYNC_REPLICATION
                               1: DRSUAPI_SUPPORTED_EXTENSION_REMOVEAPI
                               1: DRSUAPI_SUPPORTED_EXTENSION_MOVEREQ_V2
                               0: DRSUAPI_SUPPORTED_EXTENSION_GETCHG_COMPRESS
                               1: DRSUAPI_SUPPORTED_EXTENSION_DCINFO_V1
                               1: DRSUAPI_SUPPORTED_EXTENSION_RESTORE_USN_OPTIMIZATION
                               0: DRSUAPI_SUPPORTED_EXTENSION_ADDENTRY
                               1: DRSUAPI_SUPPORTED_EXTENSION_KCC_EXECUTE
                               1: DRSUAPI_SUPPORTED_EXTENSION_ADDENTRY_V2
                               1: DRSUAPI_SUPPORTED_EXTENSION_LINKED_VALUE_REPLICATION
                               1: DRSUAPI_SUPPORTED_EXTENSION_DCINFO_V2
                               1: DRSUAPI_SUPPORTED_EXTENSION_INSTANCE_TYPE_NOT_REQ_ON_MOD
                               1: DRSUAPI_SUPPORTED_EXTENSION_CRYPTO_BIND
                               1: DRSUAPI_SUPPORTED_EXTENSION_GET_REPL_INFO
                               1: DRSUAPI_SUPPORTED_EXTENSION_STRONG_ENCRYPTION
                               1: DRSUAPI_SUPPORTED_EXTENSION_DCINFO_V01
                               1: DRSUAPI_SUPPORTED_EXTENSION_TRANSITIVE_MEMBERSHIP
                               1: DRSUAPI_SUPPORTED_EXTENSION_ADD_SID_HISTORY
                               1: DRSUAPI_SUPPORTED_EXTENSION_POST_BETA3
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREQ_V5
                               1: DRSUAPI_SUPPORTED_EXTENSION_GET_MEMBERSHIPS2
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREQ_V6
                               1: DRSUAPI_SUPPORTED_EXTENSION_NONDOMAIN_NCS
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREQ_V8
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREPLY_V5
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREPLY_V6
                               1: DRSUAPI_SUPPORTED_EXTENSION_ADDENTRYREPLY_V3
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREPLY_V7
                               1: DRSUAPI_SUPPORTED_EXTENSION_VERIFY_OBJECT
                               0: DRSUAPI_SUPPORTED_EXTENSION_XPRESS_COMPRESS
                               1: DRSUAPI_SUPPORTED_EXTENSION_GETCHGREQ_V10
                               0: DRSUAPI_SUPPORTED_EXTENSION_RESERVED_PART2
                               0: DRSUAPI_SUPPORTED_EXTENSION_RESERVED_PART3
                        site_guid                : 22dc777d-b15f-4758-80a1-82d346d62424
                        pid                      : 0x00000000 (0)
                        repl_epoch               : 0x00000000 (0)
            bind_handle              : *
                bind_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 84771aa3-18ee-4200-9a19-806e9cdce8ed
            result                   : WERR_OK
rpc reply data:
[0000] 08 00 02 00 1C 00 00 00   1C 00 00 00 6F FF FF 2F   ........ ....o../
[0010] 7D 77 DC 22 5F B1 58 47   80 A1 82 D3 46 D6 24 24   }w."_.XG ....F.$$
[0020] 00 00 00 00 00 00 00 00   00 00 00 00 A3 1A 77 84   ........ ......w.
[0030] EE 18 00 42 9A 19 80 6E   9C DC E8 ED 00 00 00 00   ...B...n ........
     drsuapi_DsExecuteKCC: struct drsuapi_DsExecuteKCC
        in: struct drsuapi_DsExecuteKCC
            bind_handle              : *
                bind_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 84771aa3-18ee-4200-9a19-806e9cdce8ed
            level                    : 0x00000001 (1)
            req                      : *
                req                      : union drsuapi_DsExecuteKCCRequest(case 1)
                ctr1: struct drsuapi_DsExecuteKCC1
                    taskID                   : 0x00000000 (0)
                    flags                    : 0x00000000 (0)
                           0: DRSUAPI_DS_EXECUTE_KCC_ASYNCHRONOUS_OPERATION
                           0: DRSUAPI_DS_EXECUTE_KCC_DAMPED
rpc request data:
[0000] 00 00 00 00 A3 1A 77 84   EE 18 00 42 9A 19 80 6E   ......w. ...B...n
[0010] 9C DC E8 ED 01 00 00 00   01 00 00 00 00 00 00 00   ........ ........
[0020] 00 00 00 00                                       ....
rpc fault: WERR_EPT_S_CANT_PERFORM_OP
ERROR(runtime): DsExecuteKCC failed - (-1073610723, 'NT_STATUS_RPC_PROTOCOL_ERROR')
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/drs.py", line 232, in run
    self.drsuapi.DsExecuteKCC(self.drsuapi_handle, 1, req1)



```

It is a production system and i have already force demoted the windows server. So basically i do not have a reliable source or a backup but two defective production servers. So, I am afraid that any demotion or promotion would lead to unwanted behavior which i would not be able to afford :(:(

well i have attached and am expecting any help from you guys..I have just finished testing new installation of samba for DNS and AD on a test server with a 3 workstations attached and If nothing works out, I might as well install a new server, although considering 100s of entries, it requires a lot of manual work and patience :( :(

---

### Post by lingpanda on 2013-11-13
I'm not sure I can help you any further. It looks like you have socket errors. I do not get any of this output on my end.


```
Socket options:
        SO_KEEPALIVE = 0
        SO_REUSEADDR = 0
        SO_BROADCAST = 1
        Could not test socket option TCP_NODELAY.
        Could not test socket option TCP_KEEPCNT.
        Could not test socket option TCP_KEEPIDLE.
        Could not test socket option TCP_KEEPINTVL.
        IPTOS_LOWDELAY = 0
        IPTOS_THROUGHPUT = 0
        SO_SNDBUF = 212992
        SO_RCVBUF = 212992
        SO_SNDLOWAT = 1
        SO_RCVLOWAT = 1
        SO_SNDTIMEO = 0
        SO_RCVTIMEO = 0
        Could not test socket option TCP_QUICKACK.
        Could not test socket option TCP_DEFER_ACCEPT.
Queueing nbt packet to 127.0.0.1:137
     request: struct nbt_name_packet
        name_trn_id              : 0x19ab (6571)
        operation                : 0x0100 (256)
            0x00: NBT_RCODE                 (0)
               0: NBT_FLAG_BROADCAST
               0: NBT_FLAG_RECURSION_AVAIL
               1: NBT_FLAG_RECURSION_DESIRED
               0: NBT_FLAG_TRUNCATION
               0: NBT_FLAG_AUTHORITATIVE
            0x00: NBT_OPCODE                (0)
               0: NBT_FLAG_REPLY
        qdcount                  : 0x0001 (1)
        ancount                  : 0x0000 (0)
        nscount                  : 0x0000 (0)
        arcount                  : 0x0000 (0)
        questions: ARRAY(1)
            questions: struct nbt_name_question
                name: struct nbt_name
                    name                     : 'DC1'
                    scope                    : NULL
                    type                     : NBT_NAME_SERVER (0x20)
                question_type            : NBT_QTYPE_NETBIOS (0x20)
                question_class           : NBT_QCLASS_IP (0x1)
        answers: ARRAY(0)
        nsrecs: ARRAY(0)
        additional: ARRAY(0)
        padding                  : DATA_BLOB length=0
Received nbt packet of length 68 from 127.0.0.1:137
     packet: struct nbt_name_packet
        name_trn_id              : 0x19ab (6571)
        operation                : 0x8580 (34176)
            0x00: NBT_RCODE                 (0)
               0: NBT_FLAG_BROADCAST
               1: NBT_FLAG_RECURSION_AVAIL
               1: NBT_FLAG_RECURSION_DESIRED
               0: NBT_FLAG_TRUNCATION
               1: NBT_FLAG_AUTHORITATIVE
            0x00: NBT_OPCODE                (0)
               1: NBT_FLAG_REPLY
        qdcount                  : 0x0000 (0)
        ancount                  : 0x0001 (1)
        nscount                  : 0x0000 (0)
        arcount                  : 0x0000 (0)
        questions: ARRAY(0)
        answers: ARRAY(1)
            answers: struct nbt_res_rec
                name: struct nbt_name
                    name                     : 'DC1'
                    scope                    : NULL
                    type                     : NBT_NAME_SERVER (0x20)
                rr_type                  : NBT_QTYPE_NETBIOS (0x20)
                rr_class                 : NBT_QCLASS_IP (0x1)
                ttl                      : 0x00000000 (0)
                rdata                    : union nbt_rdata(case 0x20)
                netbios: struct nbt_rdata_netbios
                    length                   : 0x000c (12)
                    addresses: ARRAY(2)
                        addresses: struct nbt_rdata_address
                            nb_flags                 : 0x4600 (17920)
                                   1: NBT_NM_PERMANENT
                                   1: NBT_NM_ACTIVE
                                   0: NBT_NM_CONFLICT
                                   0: NBT_NM_DEREGISTER
                                0x02: NBT_NM_OWNER_TYPE         (2)
                                   0: NBT_NM_GROUP
                            ipaddr                   : 192.168.111.8
                        addresses: struct nbt_rdata_address
                            nb_flags                 : 0x4600 (17920)
                                   1: NBT_NM_PERMANENT
                                   1: NBT_NM_ACTIVE
                                   0: NBT_NM_CONFLICT
                                   0: NBT_NM_DEREGISTER
                                0x02: NBT_NM_OWNER_TYPE         (2)
                                   0: NBT_NM_GROUP
                            ipaddr                   : 192.168.111.8
        nsrecs: ARRAY(0)
        additional: ARRAY(0)
        padding                  : DATA_BLOB length=0
```

---

