---
title: "Cannot install slapd 2.2 on intrepid 8.1"
date: 2009-01-12
forum: Server Platforms
---

### Post by vsushil@serebrum.com on 2009-01-12
Hello All,
I am a total newbie to linux; using intrepid 8.0.

When I install slapd (openldap), it is installs version 2.4. I want to use slapd 2.2. I found it in the dapper-updates repository. I added the following to /etc/apt/sources.list, AND COMMENTED ALL INTREPID repositories

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

Then I did
apt-get update
apt-get install slapd

I get an error message that says slapd depends on libdap-2.2-7, libperl5.8(>=5.8.7) and libdap-2.2-7(=2.2.26-5ubuntu2.8).

I am sure I am missing something....please help.

Thanks,
Sushil

---

