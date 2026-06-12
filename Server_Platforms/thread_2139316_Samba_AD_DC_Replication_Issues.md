---
title: "Samba AD DC Replication Issues"
date: 2013-04-26
forum: Server Platforms
---

### Post by lingpanda on 2013-04-26
Receiving the following when running /samba-tool drs showrepl from my primary DC.

DC=ForestDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4FODC via RPC
                DSA object GUID: 53dea995-70f5-4a10-9860-06953437e4bd
                Last attempt @ Fri Apr 26 12:42:45 2013 EDT failed, result 87 (WERR_INVALID_PARAM)
                4503 consecutive failure(s).
                Last success @ Thu Apr 11 11:34:04 2013 EDT


This is the same for inbound and outbound neighbors. However on the backup DC it looks fine.

CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4PDC via RPC
                DSA object GUID: 7b17a9d9-7dc9-4998-a969-b0bb5f721bf5
                Last attempt @ Fri Apr 26 12:57:24 2013 EDT was successful
                0 consecutive failure(s).
                Last success @ Fri Apr 26 12:57:24 2013 EDT

Why is replication giving errors from the primary but not the backup? Any help is appreciated.

---

### Post by Toxic64 on 2013-04-27
What version of Samba 4 are you using?

---

### Post by lingpanda on 2013-04-27
> **Toxic64 said:**
> What version of Samba 4 are you using?

4.0.3 on primary. 4.0.5 on backup.

---

### Post by Toxic64 on 2013-04-28
Looks like a Kerberos/RPC error. In my opinion, you should upgarde you primary to 4.0.5. 

4.0.5 has an impressive list of corrected bugs:[http://www.samba.org/samba/history/samba-4.0.5.html](http://www.samba.org/samba/history/samba-4.0.5.html)

---

### Post by lingpanda on 2013-04-28
> **Toxic64 said:**
> Looks like a Kerberos/RPC error. In my opinion, you should upgarde you primary to 4.0.5. 

4.0.5 has an impressive list of corrected bugs:[http://www.samba.org/samba/history/samba-4.0.5.html](http://www.samba.org/samba/history/samba-4.0.5.html)

Updated but still the same issue.

---

### Post by Toxic64 on 2013-04-28
ok could you please test kerberos with kinit + klist -e commands on both DCs and show results?

---

### Post by lingpanda on 2013-04-28
> **Toxic64 said:**
> ok could you please test kerberos with kinit + klist -e commands on both DCs and show results?

PDC:
kinit = command prompt
klist = Ticket cache: FILE:/tmp/krb5cc_0
Default principal: [EMAIL="administrator@CIMGLOCAL.LOCAL"]administrator@CIMGLOCAL.LOCAL[/EMAIL]
Valid starting    Expires           Service principal
28/04/2013 17:44  29/04/2013 03:44  [EMAIL="krbtgt/CIMGLOCAL.LOCAL@CIMGLOCAL.LOCAL"]krbtgt/CIMGLOCAL.LOCAL@CIMGLOCAL.LOCAL[/EMAIL]
        renew until 29/04/2013 17:44, Etype (skey, tkt): arcfour-hmac, arcfour-hmac

BDC:
kinit = command prompt
klist =
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: [EMAIL="administrator@CIMGLOCAL.LOCAL"]administrator@CIMGLOCAL.LOCAL[/EMAIL]
Valid starting    Expires           Service principal
28/04/2013 17:48  29/04/2013 03:48  [EMAIL="krbtgt/CIMGLOCAL.LOCAL@CIMGLOCAL.LOCAL"]krbtgt/CIMGLOCAL.LOCAL@CIMGLOCAL.LOCAL[/EMAIL]
        renew until 29/04/2013 17:48, Etype (skey, tkt): arcfour-hmac, arcfour-hmac


Looks identical.

---

### Post by Toxic64 on 2013-04-28
Well then no problem with kerberos it seems.
most likely a problem with RPC which I yet don't know how to test on Samba4.

could you provide full replication test result please?

---

### Post by lingpanda on 2013-04-28
> **Toxic64 said:**
> could you provide full replication test result please?



```
==== INBOUND NEIGHBORS ====
DC=ForestDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4FODC via RPC
                DSA object GUID: 53dea995-70f5-4a10-9860-06953437e4bd
                Last attempt @ Sun Apr 28 21:14:46 2013 EDT failed, result 87 (WERR_INVALID_PARAM)
                5184 consecutive failure(s).
                Last success @ Thu Apr 11 11:34:04 2013 EDT
DC=ForestDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4SOL via RPC
                DSA object GUID: 9fc181a3-5361-4848-bf6e-3223c7395d9f
                Last attempt @ Sun Apr 28 21:14:46 2013 EDT was successful
                0 consecutive failure(s).
                Last success @ Sun Apr 28 21:14:46 2013 EDT
DC=ForestDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4DUN via RPC
                DSA object GUID: e2f4f8e3-5b79-4d25-84bb-e0a0a96f65ea
                Last attempt @ Sun Apr 28 21:14:47 2013 EDT was successful
                0 consecutive failure(s).
                Last success @ Sun Apr 28 21:14:47 2013 EDT
DC=DomainDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4FODC via RPC
                DSA object GUID: 53dea995-70f5-4a10-9860-06953437e4bd
                Last attempt @ Sun Apr 28 21:14:48 2013 EDT failed, result 87 (WERR_INVALID_PARAM)
                5183 consecutive failure(s).
                Last success @ Thu Apr 11 11:34:05 2013 EDT
DC=DomainDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4SOL via RPC
                DSA object GUID: 9fc181a3-5361-4848-bf6e-3223c7395d9f
                Last attempt @ Sun Apr 28 21:14:48 2013 EDT was successful
                0 consecutive failure(s).
                Last success @ Sun Apr 28 21:14:48 2013 EDT
DC=DomainDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4DUN via RPC
                DSA object GUID: e2f4f8e3-5b79-4d25-84bb-e0a0a96f65ea
                Last attempt @ Sun Apr 28 21:14:49 2013 EDT was successful
                0 consecutive failure(s).
                Last success @ Sun Apr 28 21:14:49 2013 EDT
DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4FODC via RPC
                DSA object GUID: 53dea995-70f5-4a10-9860-06953437e4bd
                Last attempt @ Sun Apr 28 21:14:49 2013 EDT failed, result 87 (WERR_INVALID_PARAM)
                5187 consecutive failure(s).
                Last success @ Thu Apr 11 11:34:07 2013 EDT
DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4SOL via RPC
                DSA object GUID: 9fc181a3-5361-4848-bf6e-3223c7395d9f
                Last attempt @ Sun Apr 28 21:14:50 2013 EDT was successful
                0 consecutive failure(s).
                Last success @ Sun Apr 28 21:14:50 2013 EDT
DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4DUN via RPC
                DSA object GUID: e2f4f8e3-5b79-4d25-84bb-e0a0a96f65ea
                Last attempt @ Sun Apr 28 21:14:51 2013 EDT was successful
                0 consecutive failure(s).
                Last success @ Sun Apr 28 21:14:51 2013 EDT
CN=Schema,CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4FODC via RPC
                DSA object GUID: 53dea995-70f5-4a10-9860-06953437e4bd
                Last attempt @ Sun Apr 28 21:14:52 2013 EDT failed, result 87 (WERR_INVALID_PARAM)
                5183 consecutive failure(s).
                Last success @ Thu Apr 11 11:34:09 2013 EDT
CN=Schema,CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4SOL via RPC
                DSA object GUID: 9fc181a3-5361-4848-bf6e-3223c7395d9f
                Last attempt @ Sun Apr 28 21:14:53 2013 EDT was successful
                0 consecutive failure(s).
                Last success @ Sun Apr 28 21:14:53 2013 EDT
CN=Schema,CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4DUN via RPC
                DSA object GUID: e2f4f8e3-5b79-4d25-84bb-e0a0a96f65ea
                Last attempt @ Sun Apr 28 21:14:54 2013 EDT was successful
                0 consecutive failure(s).
                Last success @ Sun Apr 28 21:14:54 2013 EDT
CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4FODC via RPC
                DSA object GUID: 53dea995-70f5-4a10-9860-06953437e4bd
                Last attempt @ Sun Apr 28 21:14:54 2013 EDT failed, result 87 (WERR_INVALID_PARAM)
                5183 consecutive failure(s).
                Last success @ Thu Apr 11 11:34:11 2013 EDT
CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4SOL via RPC
                DSA object GUID: 9fc181a3-5361-4848-bf6e-3223c7395d9f
                Last attempt @ Sun Apr 28 21:14:55 2013 EDT was successful
                0 consecutive failure(s).
                Last success @ Sun Apr 28 21:14:55 2013 EDT
CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4DUN via RPC
                DSA object GUID: e2f4f8e3-5b79-4d25-84bb-e0a0a96f65ea
                Last attempt @ Sun Apr 28 21:14:56 2013 EDT was successful
                0 consecutive failure(s).
                Last success @ Sun Apr 28 21:14:56 2013 EDT
==== OUTBOUND NEIGHBORS ====
DC=ForestDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4SOL via RPC
                DSA object GUID: 9fc181a3-5361-4848-bf6e-3223c7395d9f
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)
DC=ForestDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4DUN via RPC
                DSA object GUID: e2f4f8e3-5b79-4d25-84bb-e0a0a96f65ea
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)
DC=ForestDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4FODC via RPC
                DSA object GUID: 53dea995-70f5-4a10-9860-06953437e4bd
                Last attempt @ Sun Apr 28 21:15:26 2013 EDT failed, result 87 (WERR_INVALID_PARAM)
                7 consecutive failure(s).
                Last success @ NTTIME(0)
DC=DomainDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4SOL via RPC
                DSA object GUID: 9fc181a3-5361-4848-bf6e-3223c7395d9f
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)
DC=DomainDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4DUN via RPC
                DSA object GUID: e2f4f8e3-5b79-4d25-84bb-e0a0a96f65ea
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)
DC=DomainDnsZones,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4FODC via RPC
                DSA object GUID: 53dea995-70f5-4a10-9860-06953437e4bd
                Last attempt @ Sun Apr 28 21:15:26 2013 EDT failed, result 87 (WERR_INVALID_PARAM)
                7 consecutive failure(s).
                Last success @ NTTIME(0)
DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4DUN via RPC
                DSA object GUID: e2f4f8e3-5b79-4d25-84bb-e0a0a96f65ea
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)
DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4SOL via RPC
                DSA object GUID: 9fc181a3-5361-4848-bf6e-3223c7395d9f
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)
DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4FODC via RPC
                DSA object GUID: 53dea995-70f5-4a10-9860-06953437e4bd
                Last attempt @ Sun Apr 28 21:15:27 2013 EDT failed, result 87 (WERR_INVALID_PARAM)
                7 consecutive failure(s).
                Last success @ NTTIME(0)
CN=Schema,CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4SOL via RPC
                DSA object GUID: 9fc181a3-5361-4848-bf6e-3223c7395d9f
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)
CN=Schema,CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4DUN via RPC
                DSA object GUID: e2f4f8e3-5b79-4d25-84bb-e0a0a96f65ea
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)
CN=Schema,CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4FODC via RPC
                DSA object GUID: 53dea995-70f5-4a10-9860-06953437e4bd
                Last attempt @ Sun Apr 28 21:15:27 2013 EDT failed, result 87 (WERR_INVALID_PARAM)
                7 consecutive failure(s).
                Last success @ NTTIME(0)
CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4DUN via RPC
                DSA object GUID: e2f4f8e3-5b79-4d25-84bb-e0a0a96f65ea
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)
CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4SOL via RPC
                DSA object GUID: 9fc181a3-5361-4848-bf6e-3223c7395d9f
                Last attempt @ NTTIME(0) was successful
                0 consecutive failure(s).
                Last success @ NTTIME(0)
CN=Configuration,DC=cimglocal,DC=local
        Default-First-Site-Name\SAMBA4FODC via RPC
                DSA object GUID: 53dea995-70f5-4a10-9860-06953437e4bd
                Last attempt @ Sun Apr 28 21:15:27 2013 EDT failed, result 87 (WERR_INVALID_PARAM)
                7 consecutive failure(s).
                Last success @ NTTIME(0)
==== KCC CONNECTION OBJECTS ====
Connection --
        Connection name: 116087a6-30e1-4b58-be92-a1639d39da9d
        Enabled        : TRUE
        Server DNS name : SAMBA4DUN.cimglocal.local
        Server DN name  : CN=NTDS Settings,CN=SAMBA4DUN,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=cimglocal,DC=local
                TransportType: RPC
                options: 0x00000001
Warning: No NC replicated for Connection!
Connection --
        Connection name: 38dbd7d9-a301-401d-b5ed-6b24113ae732
        Enabled        : TRUE
        Server DNS name : SAMBA4FODC.cimglocal.local
        Server DN name  : CN=NTDS Settings,CN=SAMBA4FODC,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=cimglocal,DC=local
                TransportType: RPC
                options: 0x00000001
Warning: No NC replicated for Connection!
Connection --
        Connection name: ccca925e-ee8d-48ac-b48f-7db07abc41fd
        Enabled        : TRUE
        Server DNS name : SAMBA4SOL.cimglocal.local
        Server DN name  : CN=NTDS Settings,CN=SAMBA4SOL,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=cimglocal,DC=local
                TransportType: RPC
                options: 0x00000001
Warning: No NC replicated for Connection!



```

---

### Post by Toxic64 on 2013-04-29
Ok check kcc please.

```
samba-tool drs kcc -Uadministrator SAMBA4FODC.cimglocal.local 
```

---

### Post by lingpanda on 2013-04-29
> **Toxic64 said:**
> Ok check kcc please.

```
samba-tool drs kcc -Uadministrator SAMBA4FODC.cimglocal.local 
```


Password for [CIMGLOCAL\Administrator]:
Consistency check on SAMBA4FODC.cimglocal.local successful.

---

### Post by Toxic64 on 2013-04-30
Well I'm sorry to tell but I don't have a single clue what's wrong with your replication problem for this DC.

---

### Post by lingpanda on 2013-04-30
> **Toxic64 said:**
> Well I'm sorry to tell but I don't have a single clue what's wrong with your replication problem for this DC.

Toxic I appreciate the assistance so far. Looking in log.samba I get this.


```
[2013/04/24 15:48:15,  0] ../source4/librpc/rpc/dcerpc_util.c:660(dcerpc_pipe_auth_recv)
  Failed to bind to uuid e3514235-4b06-11d1-ab04-00c04fc2dcd2 for e3514235-4b06-11d1-ab04-00c04fc2dcd2@ncacn_ip_tcp:53dea995-70f5-4a10-9860-06953437e4bd._msdcs.cimglocal.local[1024,seal,krb5] NT_STATUS_INVALID_PARAMETER
[2013/04/24 15:48:15,  0] ../source4/librpc/rpc/dcerpc_util.c:660(dcerpc_pipe_auth_recv)
  Failed to bind to uuid e3514235-4b06-11d1-ab04-00c04fc2dcd2 for e3514235-4b06-11d1-ab04-00c04fc2dcd2@ncacn_ip_tcp:53dea995-70f5-4a10-9860-06953437e4bd._msdcs.cimglocal.local[1024,seal,krb5] NT_STATUS_INVALID_PARAMETER
[2013/04/24 15:48:16,  0] ../source4/librpc/rpc/dcerpc_util.c:660(dcerpc_pipe_auth_recv)
  Failed to bind to uuid e3514235-4b06-11d1-ab04-00c04fc2dcd2 for e3514235-4b06-11d1-ab04-00c04fc2dcd2@ncacn_ip_tcp:53dea995-70f5-4a10-9860-06953437e4bd._msdcs.cimglocal.local[1024,seal,krb5] NT_STATUS_INVALID_PARAMETER
[2013/04/24 15:48:17,  0] ../source4/librpc/rpc/dcerpc_util.c:660(dcerpc_pipe_auth_recv)
  Failed to bind to uuid e3514235-4b06-11d1-ab04-00c04fc2dcd2 for e3514235-4b06-11d1-ab04-00c04fc2dcd2@ncacn_ip_tcp:53dea995-70f5-4a10-9860-06953437e4bd._msdcs.cimglocal.local[1024,seal,krb5] NT_STATUS_INVALID_PARAMETER
[2013/04/24 15:48:19,  0] ../source4/librpc/rpc/dcerpc_util.c:660(dcerpc_pipe_auth_recv)
```

Any idea how to correct? This looks to be the issue.

---

### Post by Toxic64 on 2013-04-30
I'd say RPC authentication request failing because of KDC registration inconcistency but I don't know how to solve that.

How did you install and join your DC's?

You might want to increase the debug level to see if we can get more informations.
it seems kerberos negociation fails between your 2 Dc's for whatever reason....

One thing you could do is install a windows server DC and run DCdiag for your failing server. results would help a lot I'm sure.

---

### Post by lingpanda on 2013-04-30
> **Toxic64 said:**
> I'd say RPC authentication request failing because of KDC registration inconcistency but I don't know how to solve that.

How did you install and join your DC's?

Via. tarball from [http://ftp.samba.org/pub/samba/](http://ftp.samba.org/pub/samba/) Join command from wiki guidelines(# bin/samba-tool domain join samba.example.com DC -Uadministrator --realm=samba.example.com)

I'm sure I broke something while trying to setup rsync between the two DC's. Was trying to replicate the sysvol folder. I also tried to demote the machine but that also fails.

---

### Post by Toxic64 on 2013-04-30
Finally here is your reason...you do not replicate sysvol....th AD services replicate sysvol content...no need for rsync...

I think you 'll have to reinstall cause now you sure have inconsistent data in your sysvol..

---

### Post by lingpanda on 2013-04-30
> **Toxic64 said:**
> Finally here is your reason...you do not replicate sysvol....th AD services replicate sysvol content...no need for rsync...

I think you 'll have to reinstall cause now you sure have inconsistent data in your sysvol..
My understanding is samba doesn't replicate the sysvol folder yet. Per the wiki:

"Currently the replication of the SysVol share isn't implemented. If you make any changes on that share, you have to keep the shares on all your DCs in sync manually (e. g. with an rsync cronjob)."

What am I missing? Do you know how to force a demote of the server?

---

### Post by Toxic64 on 2013-05-01
Your understanding is partial I think. 
MS Active Directory replicates logon scripts and Group Policy object files to other domain controllers (which are in the sysvol folder).

Keep in mind the wiki is not up-to-date it was written around v4 probably alpha versions it's possible sysvol replication works out of the box now.
best thing you can do to test it is create a GPO or logon script and force replication between your two DC's then take the DC's you replicated from offline and check whether your GPO or logon script still applies.
It would be better with a logon script as (for security reasons) GPO parameters are stored in windows client registry and will apply whether the DC where it was pulled from is missing or not.
still you could also have a clean windows client (not yet domain joined) and join it to your domain after you took that first DC' is offline if GPO your applies, it means the sysvol has been replicated.

---

### Post by lingpanda on 2013-05-01
> **Toxic64 said:**
> Your understanding is partial I think. 
MS Active Directory replicates logon scripts and Group Policy object files to other domain controllers (which are in the sysvol folder).

Keep in mind the wiki is not up-to-date it was written around v4 probably alpha versions it's possible sysvol replication works out of the box now.
best thing you can do to test it is create a GPO or logon script and force replication between your two DC's then take the DC's you replicated from offline and check whether your GPO or logon script still applies.
It would be better with a logon script as (for security reasons) GPO parameters are stored in windows client registry and will apply whether the DC where it was pulled from is missing or not.
still you could also have a clean windows client (not yet domain joined) and join it to your domain after you took that first DC' is offline if GPO your applies, it means the sysvol has been replicated.

So I created a new server and joined to the domain. Sysvol does not replicate. :( Thanks for your help on this issue. At least I have an adequate backup at the moment.

---

### Post by Toxic64 on 2013-05-01
I would not go for rsync again. Keep in mind Samba4 is not fully operationnal. surely a proper replication mechanism will come in future versions.

---

