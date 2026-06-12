---
title: "problem installing duplicity on dapper 6.06 lts server"
date: 2009-02-02
forum: Server Platforms
---

### Post by I_M_smbody on 2009-02-02
I'm trying to install duplicity on a dapper server lts install but i'm having trouble using apt-get.

I've been runningthe following commands

apt-get update
apt-get upgrade
apt-get install duplicity

when i run the install command the system asks for the install cd labeled

'Ubuntu 6.06 _Dapper Drake_ -release i386 (20060531)'

I don't have the original cd and it won't accept the  most recent download of the cd for dapper 6.06 lts server. 

My question is how do I complete my install?

I've been thinking about it.

I assume it wants the cd to figure out where to download duplicity since it is on a server I didn't have running for  updates. Does that make sense?


can I manually enter the server data in a configuration file?

what files would I need to modify?

Should I try a manual install? or a different installer?

---

### Post by I_M_smbody on 2009-02-11
binbash told me to "remove the cds at sources.list so it wont ask the cds" 

It worked. I now have duplicity and the other appts installed without the cd. 

Hopes that helps someone else.

I_M_smbdy

---

