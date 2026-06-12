---
title: "Postgres in VM  became slow after upgrade 14"
date: 2016-04-11
forum: Virtualisation
---

### Post by vadim12 on 2016-04-11
Hello I use servers Ubuntu 14.04 LTS with KVM+libvirt. Last time I had strange situation.
First I had node [COLOR=#333333][FONT=Arial]Ubuntu 14.04.2 LTS with kernel 3.13.0-46-generic, and VM [/FONT][/COLOR][COLOR=#333333][FONT=Arial]Ubuntu 14.04.2 LTS with kernel 3.13.0-46-generic + [/FONT][/COLOR][COLOR=#333333][FONT=Arial]postgresql-9.3 9.3.6-0ubuntu0.14.04.
Next I upgraded node and VM to Ubuntu 14.04.4 LTS with kernel [/FONT][/COLOR][COLOR=#333333][FONT=Arial]3.19.0-58-generic, and [/FONT][/COLOR][COLOR=#333333][FONT=Arial]postgresql-9.3_9.3.4-1.
And I saw my Database Server became too slow. I had high load average on the same load profile.
Then I rolled back only my VM to Ubuntu 14.04.2 and my DB server started working normally.

I didn't have time for deep research, may be this post will be helpful.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-04-11
That's not the the same version number I get on my 14.04 server installation.  I ran "sudo update; sudo dist-upgrade" then checked with "dpkg -s postgresql".  It reports 9.3+154ubuntu1 as the current PostgreSQL version.  Are you using the stock packages from the Ubuntu repositories or from a PPA or compiled from source?

---

### Post by vadim12 on 2016-04-14
I use  PostgreSQL and OS Ubunutu in my VM from ubuntu repositories.
I see many differences between configs 3.13 and 3.19 kernel

---

### Post by SeijiSensei on 2016-04-14
What version is reported if you run "dpkg -s postgresql"?

I've found the single biggest performance issue in Postgres is a lack of query-specific indexes.  If you have SELECTs with WHERE clauses that reference multiple fields, you need to build a corresponding index that includes those same fields.  That wouldn't explain why performance changes across upgrades, but you should nevertheless review the types of queries your database routinely receives and create the necessary indexes.  Certanly if you use views, you should have an index for each view you create.

---

### Post by vadim12 on 2016-04-19
After upgrade [COLOR=#333333][FONT=Arial] [/FONT][/COLOR][COLOR=#333333][FONT=Arial]postgresql-9.3 9.3.6-0ubuntu0.14.04
Before upgrade  [/FONT][/COLOR] [FONT=Arial][COLOR=#333333]postgresql-9.3_9.3.4-1[/COLOR][/FONT]
[FONT=Arial][COLOR=#333333]Our analitics use this database, and sometimes they make strange things :) But in those  days they didn't deploy new things.[/COLOR][/FONT]

[FONT=Arial][COLOR=#333333]PS.[/COLOR][/FONT]
[FONT=Arial][COLOR=#333333]Two days ago I saw that my host machine started using swap.  It began after upgrade. [/COLOR][/FONT]
[FONT=Arial][COLOR=#333333]Host mashine has 64 GB RAM, and VM has 32 GB RAM. Although vm.swappinnes=0, swap is used. When swap usage more than about 10GB, IO performance drops/[/COLOR][/FONT]
[FONT=Arial][COLOR=#333333]I found big buffers size 27GB in /proc/meminfo, and had to disable swap (swapoff). Today I'm successfully working with old image VM, and upgraded host machine without swap. [/COLOR][/FONT]

---

