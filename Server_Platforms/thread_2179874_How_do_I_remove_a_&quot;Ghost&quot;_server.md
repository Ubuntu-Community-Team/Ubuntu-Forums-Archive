---
title: "How do I remove a &quot;Ghost&quot; server?"
date: 2013-10-10
forum: Server Platforms
---

### Post by JnPson on 2013-10-10
I have installed three AD DC in my Samba 4.0.9 domain just to make sure I know how to do it properly. During my testing I installed one server that failed and that I had to remove as DC. It is not showing up anywhere in the network or in Active Director Users and Computers, but it is still listed as a DC when I run
```
samba-tool drs showrepl
```
I wonder how to prevent the remaining DC's from trying to replicate to a "ghost"?
This is the result of *showrepl*
```
root@dc01:~# samba-tool drs showrepl
Default-First-Site-Name\DC01
DSA Options: 0x00000001
DSA object GUID: 4d66091e-2d47-4bc0-a255-188ac4d2e06b
DSA invocationId: b52977ef-b895-4b03-a1dc-b66f04f34f52

==== INBOUND NEIGHBORS ====

DC=DomainDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DC03 via RPC
        DSA object GUID: fe0f34f5-f726-4d04-a041-45ce9a6ce53a
        Last attempt @ Thu Oct 10 14:19:28 2013 CEST failed, result 2 (WERR_BADFILE)
        12446 consecutive failure(s).
        Last success @ NTTIME(0)

DC=DomainDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DFS01 via RPC
        DSA object GUID: 0e0f81cb-a45e-4191-9700-77ad90d111d3
        Last attempt @ Thu Oct 10 14:19:29 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Thu Oct 10 14:19:29 2013 CEST

DC=DomainDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DC02 via RPC
        DSA object GUID: 47dffc4a-db59-4221-9d7e-02ab58258c95
        Last attempt @ Thu Oct 10 14:14:47 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Thu Oct 10 14:14:47 2013 CEST

DC=ForestDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DC03 via RPC
        DSA object GUID: fe0f34f5-f726-4d04-a041-45ce9a6ce53a
        Last attempt @ Thu Oct 10 14:14:47 2013 CEST failed, result 2 (WERR_BADFILE)
        12444 consecutive failure(s).
        Last success @ NTTIME(0)

DC=ForestDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DFS01 via RPC
        DSA object GUID: 0e0f81cb-a45e-4191-9700-77ad90d111d3
        Last attempt @ Thu Oct 10 14:14:48 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Thu Oct 10 14:14:48 2013 CEST

DC=ForestDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DC02 via RPC
        DSA object GUID: 47dffc4a-db59-4221-9d7e-02ab58258c95
        Last attempt @ Thu Oct 10 14:14:49 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Thu Oct 10 14:14:49 2013 CEST

DC=pson,DC=lan
    Default-First-Site-Name\DC03 via RPC
        DSA object GUID: fe0f34f5-f726-4d04-a041-45ce9a6ce53a
        Last attempt @ Thu Oct 10 14:14:49 2013 CEST failed, result 2 (WERR_BADFILE)
        12444 consecutive failure(s).
        Last success @ NTTIME(0)

DC=pson,DC=lan
    Default-First-Site-Name\DFS01 via RPC
        DSA object GUID: 0e0f81cb-a45e-4191-9700-77ad90d111d3
        Last attempt @ Thu Oct 10 14:14:50 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Thu Oct 10 14:14:50 2013 CEST

DC=pson,DC=lan
    Default-First-Site-Name\DC02 via RPC
        DSA object GUID: 47dffc4a-db59-4221-9d7e-02ab58258c95
        Last attempt @ Thu Oct 10 14:14:50 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Thu Oct 10 14:14:50 2013 CEST

CN=Schema,CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DC03 via RPC
        DSA object GUID: fe0f34f5-f726-4d04-a041-45ce9a6ce53a
        Last attempt @ Thu Oct 10 14:14:51 2013 CEST failed, result 2 (WERR_BADFILE)
        12444 consecutive failure(s).
        Last success @ NTTIME(0)

CN=Schema,CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DFS01 via RPC
        DSA object GUID: 0e0f81cb-a45e-4191-9700-77ad90d111d3
        Last attempt @ Thu Oct 10 14:14:51 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Thu Oct 10 14:14:51 2013 CEST

CN=Schema,CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DC02 via RPC
        DSA object GUID: 47dffc4a-db59-4221-9d7e-02ab58258c95
        Last attempt @ Thu Oct 10 14:14:53 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Thu Oct 10 14:14:53 2013 CEST

CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DC03 via RPC
        DSA object GUID: fe0f34f5-f726-4d04-a041-45ce9a6ce53a
        Last attempt @ Thu Oct 10 14:14:53 2013 CEST failed, result 2 (WERR_BADFILE)
        12444 consecutive failure(s).
        Last success @ NTTIME(0)

CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DFS01 via RPC
        DSA object GUID: 0e0f81cb-a45e-4191-9700-77ad90d111d3
        Last attempt @ Thu Oct 10 14:14:53 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Thu Oct 10 14:14:53 2013 CEST

CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DC02 via RPC
        DSA object GUID: 47dffc4a-db59-4221-9d7e-02ab58258c95
        Last attempt @ Thu Oct 10 14:14:55 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Thu Oct 10 14:14:55 2013 CEST

==== OUTBOUND NEIGHBORS ====

DC=DomainDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DC03 via RPC
        DSA object GUID: fe0f34f5-f726-4d04-a041-45ce9a6ce53a
        Last attempt @ Thu Oct 10 14:19:27 2013 CEST failed, result 2 (WERR_BADFILE)
        697593 consecutive failure(s).
        Last success @ NTTIME(0)

DC=DomainDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DFS01 via RPC
        DSA object GUID: 0e0f81cb-a45e-4191-9700-77ad90d111d3
        Last attempt @ Thu Oct 10 14:13:51 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Thu Oct 10 14:13:51 2013 CEST

DC=DomainDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DC02 via RPC
        DSA object GUID: 47dffc4a-db59-4221-9d7e-02ab58258c95
        Last attempt @ NTTIME(0) was successful
        0 consecutive failure(s).
        Last success @ NTTIME(0)

DC=ForestDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DC03 via RPC
        DSA object GUID: fe0f34f5-f726-4d04-a041-45ce9a6ce53a
        Last attempt @ Thu Oct 10 14:19:27 2013 CEST failed, result 2 (WERR_BADFILE)
        696212 consecutive failure(s).
        Last success @ NTTIME(0)

DC=ForestDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DFS01 via RPC
        DSA object GUID: 0e0f81cb-a45e-4191-9700-77ad90d111d3
        Last attempt @ Wed Oct  9 23:54:18 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Wed Oct  9 23:54:18 2013 CEST

DC=ForestDnsZones,DC=pson,DC=lan
    Default-First-Site-Name\DC02 via RPC
        DSA object GUID: 47dffc4a-db59-4221-9d7e-02ab58258c95
        Last attempt @ NTTIME(0) was successful
        0 consecutive failure(s).
        Last success @ NTTIME(0)

DC=pson,DC=lan
    Default-First-Site-Name\DC03 via RPC
        DSA object GUID: fe0f34f5-f726-4d04-a041-45ce9a6ce53a
        Last attempt @ Thu Oct 10 14:19:28 2013 CEST failed, result 2 (WERR_BADFILE)
        696013 consecutive failure(s).
        Last success @ NTTIME(0)

DC=pson,DC=lan
    Default-First-Site-Name\DFS01 via RPC
        DSA object GUID: 0e0f81cb-a45e-4191-9700-77ad90d111d3
        Last attempt @ Wed Oct  9 23:54:19 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Wed Oct  9 23:54:19 2013 CEST

DC=pson,DC=lan
    Default-First-Site-Name\DC02 via RPC
        DSA object GUID: 47dffc4a-db59-4221-9d7e-02ab58258c95
        Last attempt @ NTTIME(0) was successful
        0 consecutive failure(s).
        Last success @ NTTIME(0)

CN=Schema,CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DC03 via RPC
        DSA object GUID: fe0f34f5-f726-4d04-a041-45ce9a6ce53a
        Last attempt @ Thu Oct 10 14:19:28 2013 CEST failed, result 2 (WERR_BADFILE)
        695466 consecutive failure(s).
        Last success @ NTTIME(0)

CN=Schema,CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DFS01 via RPC
        DSA object GUID: 0e0f81cb-a45e-4191-9700-77ad90d111d3
        Last attempt @ Wed Oct  9 23:54:22 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Wed Oct  9 23:54:22 2013 CEST

CN=Schema,CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DC02 via RPC
        DSA object GUID: 47dffc4a-db59-4221-9d7e-02ab58258c95
        Last attempt @ NTTIME(0) was successful
        0 consecutive failure(s).
        Last success @ NTTIME(0)

CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DC03 via RPC
        DSA object GUID: fe0f34f5-f726-4d04-a041-45ce9a6ce53a
        Last attempt @ Thu Oct 10 14:19:28 2013 CEST failed, result 2 (WERR_BADFILE)
        695035 consecutive failure(s).
        Last success @ NTTIME(0)

CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DFS01 via RPC
        DSA object GUID: 0e0f81cb-a45e-4191-9700-77ad90d111d3
        Last attempt @ Wed Oct  9 23:54:23 2013 CEST was successful
        0 consecutive failure(s).
        Last success @ Wed Oct  9 23:54:23 2013 CEST

CN=Configuration,DC=pson,DC=lan
    Default-First-Site-Name\DC02 via RPC
        DSA object GUID: 47dffc4a-db59-4221-9d7e-02ab58258c95
        Last attempt @ NTTIME(0) was successful
        0 consecutive failure(s).
        Last success @ NTTIME(0)

==== KCC CONNECTION OBJECTS ====

Connection --
    Connection name: 159b16d9-aa8c-4b10-9afb-d86acbfb834e
    Enabled        : TRUE
    Server DNS name : dfs01.pson.lan
    Server DN name  : CN=NTDS Settings,CN=DFS01,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=pson,DC=lan
        TransportType: RPC
        options: 0x00000001
Warning: No NC replicated for Connection!
Connection --
    Connection name: aee5a19a-d3f4-4d04-9a21-84d9ef96e1b5
    Enabled        : TRUE
    Server DNS name : DC03.pson.lan
    Server DN name  : CN=NTDS Settings,CN=DC03,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=pson,DC=lan
        TransportType: RPC
        options: 0x00000001
Warning: No NC replicated for Connection!
Connection --
    Connection name: bc717be9-c0e2-4bdc-aaa5-826202e43f58
    Enabled        : TRUE
    Server DNS name : DC02.pson.lan
    Server DN name  : CN=NTDS Settings,CN=DC02,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=pson,DC=lan
        TransportType: RPC
        options: 0x00000001
Warning: No NC replicated for Connection!


```

---

### Post by JnPson on 2013-10-14
Bump

---

