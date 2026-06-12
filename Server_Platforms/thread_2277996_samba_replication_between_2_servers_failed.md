---
title: "samba replication between 2 servers failed"
date: 2015-05-13
forum: Server Platforms
---

### Post by toby7 on 2015-05-13
I have two zentyal servers, one as PDC and one as additional DC. It was  working perfectly until last week. Now if I add a new computer to the  domain it appears on one of our DCs but not on the other one. Same with  users, if I deactivate one it doesn't get deactivated on the other DC. I  was waiting more than a day to make sure it's not syncing .
If I execute 'sudo samba-tool drs showrepl' command on my PDC this is what I see:
```
ldb_wrap open of secrets.ldb
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'schannel' registered
GENSEC backend 'spnego' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Using binding ncacn_ip_tcp:zentyal-p.irinyi.lan[,seal]
Default-First-Site-Name\ZENTYAL-P
DSA Options: 0x00000001
DSA object GUID: a68a14de-80aa-4e07-bee2-307f5d684e4d
DSA invocationId: 09be6995-9931-470a-9183-5f01d287f259

==== INBOUND NEIGHBORS ====

DC=ForestDnsZones,DC=irinyi,DC=lan
        Default-First-Site-Name\ZENTYAL-M via RPC
                DSA object GUID: 0a989f75-b8b8-4ae4-a6d3-b1a66fa1f895
                Last attempt @ Wed May 13 07:44:27 2015 CEST was successful
                0 consecutive failure(s).
                Last success @ Wed May 13 07:44:27 2015 CEST

DC=DomainDnsZones,DC=irinyi,DC=lan
        Default-First-Site-Name\ZENTYAL-M via RPC
                DSA object GUID: 0a989f75-b8b8-4ae4-a6d3-b1a66fa1f895
                Last attempt @ Wed May 13 07:44:28 2015 CEST was successful
                0 consecutive failure(s).
                Last success @ Wed May 13 07:44:28 2015 CEST

DC=irinyi,DC=lan
        Default-First-Site-Name\ZENTYAL-M via RPC
                DSA object GUID: 0a989f75-b8b8-4ae4-a6d3-b1a66fa1f895
                Last attempt @ Thu Apr 30 07:16:08 2015 CEST failed, result 121 **(WERR_SEM_TIMEOUT)**
                7 consecutive failure(s).
                Last success @ Wed Mar 18 12:49:14 2015 CET

```

Everything else is successfull after this.
Same command on secondary DC:
```
==== OUTBOUND NEIGHBORS ====

DC=ForestDnsZones,DC=irinyi,DC=lan
        Default-First-Site-Name\ZENTYAL-P via RPC
                DSA object GUID: a68a14de-80aa-4e07-bee2-307f5d684e4d
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)

CN=Schema,CN=Configuration,DC=irinyi,DC=lan
        Default-First-Site-Name\ZENTYAL-P via RPC
                DSA object GUID: a68a14de-80aa-4e07-bee2-307f5d684e4d
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)

DC=irinyi,DC=lan
        Default-First-Site-Name\ZENTYAL-P via RPC
                DSA object GUID: a68a14de-80aa-4e07-bee2-307f5d684e4d
                Last attempt @ Wed May 13 07:24:53 2015 CEST was successful
                0 consecutive failure(s).
                Last success @ Wed May 13 07:24:53 2015 CEST

DC=DomainDnsZones,DC=irinyi,DC=lan
        Default-First-Site-Name\ZENTYAL-P via RPC
                DSA object GUID: a68a14de-80aa-4e07-bee2-307f5d684e4d
                Last attempt @ Wed May 13 07:56:32 2015 CEST failed, result 29** (WERR_WRITE_FAULT)**
                68 consecutive failure(s).
                Last success @ NTTIME(0)


```

running 'samba-tool drs replicate zentyal-p zentyal-m DC=irinyi,DC=lan -U administrator' on my PDC outputs this:
```
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'schannel' registered
GENSEC backend 'spnego' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Using binding ncacn_ip_tcp:zentyal-p[,seal]
Password for [IRINYI\administrator]:
ERROR(<class 'samba.drs_utils.drsException'>): DsReplicaSync failed - drsException: DsReplicaSync failed (-1073610723, 'NT_STATUS_RPC_PROTOCOL_ERROR')
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/drs.py", line 345, in run
    drs_utils.sendDsReplicaSync(self.drsuapi, self.drsuapi_handle, source_dsa_guid, NC, req_options)
  File "/usr/lib/python2.7/dist-packages/samba/drs_utils.py", line 83, in sendDsReplicaSync
    raise drsException("DsReplicaSync failed %s" % estr)

```

What could go wrong with my servers? Any help is appreciated.

---

