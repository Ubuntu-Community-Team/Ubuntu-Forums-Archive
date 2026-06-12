---
title: "nscd dies after 15 seconds"
date: 2006-10-06
forum: Server Platforms
---

### Post by eziegler on 2006-10-06
We have several clients running Linux with LDAP at our institute. Since we use SSl encryption the nscd is installed and running. Most of the machines run under SuSE 9.1-9.3 which works more or less well. After installing SuSE 10.0 the nscd kept on crashing making the computers unusable. Thus I changed to Dapper...

I have two machines with identical setup. On one everything works fine, on the other one nscd keeps on crashing as well (updated everything today using update-manager). If I start nscd it always crashes after exactly 15 seconds.

# time nscd -d
Segmentation fault

real    0m15.010s
user    0m0.000s
sys     0m0.008s

Sometimes there is some additional output if a request comes in. Nevertheless the result is always the same. GDB doesn't give any useful information on this either...

Thanks
Emanuel

---

### Post by eziegler on 2007-03-01
Although the thread is quite old already, I'd like to add the solution for dapper that I found in the meantime.

If you inlcude the edgy sources and install the edgy-versions of nscd and libc6 (maybe you'll want to install libc6-dev as well), the problem disappears. After that you can remove the edgy sources.

It's a shame that this annoying bug has obviously been fixed but there is no update for dapper (how about LTS?). In the beginning nscd was not even in the  repository although it's absolutely necessary for LDAP with encryption. This way ubuntu will never get into the companies...

As a side remark: suse had the same problem with 10.0 and that was for me one the reasons to change to ubuntu in the lab. LDAP still seems to be very badly supported by linux distributions although the capabilities are there.

Cheers,
    Emanuel

---

