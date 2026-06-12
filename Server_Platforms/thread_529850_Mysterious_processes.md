---
title: "Mysterious processes"
date: 2007-08-19
forum: Server Platforms
---

### Post by JamesMintram on 2007-08-19
Hello everyone, I am currently using a Ubuntu 6.06 LTS server which is a dedicated server I am hiring from 123-reg.co.uk.

There seem to be mysterious processes running which I cant seem to find anything on apart from doing a ps aux:

Here is an example of one:

71        5281  0.0  0.0    120    44 ?        S    Aug19   0:00 tcpserver -v -R -l 0 -x /etc/qmail/tcp.qmqp.cdb -c 20 -u 71 -g 71 0 628 qmail-qmqpd

Other processes which start themselves up include Xinetd and Proftpd - this is unwanted as I would like FTP software of my choice running amongst other things.

I have done a search through the whole hard driver to see if I can find where the processes are instantiated from including a file contents search but I have had no luck. Even more frustrating is in the example above it refers to an /etc/qmail/ directory, this doesn't exist!

I have tried killing the above process manually but it keeps being re spawned instantly, and I cant find anything about the tcpserver in the output above.

If anyone could give me any help it would be much appreciated.

---

### Post by K.Mandla on 2007-08-19
I don't know enough about server processes to answer intelligently, but I'm going to shift your thread to the server forum, where there are some highly experienced Ubuntunuts who should be able to help.

Please fasten your seat belt. ... ;)

---

### Post by Mr. C. on 2007-08-20
tcpserver is a master tcp service program, that listens on ports for incoming connections.  The process you are showing is qmail-qmqpd, which is a qmail component.  Remove qmail if you do not want it.

xinetd is also a master network connection service program - it too launches programs when a connection attempt is made to your system on a given port, and xinetd is enabled for that port.  It never starts itself - it must be started by one of the system startup scripts in the /etc/init.d/ directory.

Some server software can either run on its own, in standalone mode, where it runs in the background listening for connections, or it can run under the control of a master internet daemon such as xinetd or inetd.

You have to configure how you want your services to start.  See /etc/xinetd* for xinetd's configuration files.

MrC

---

### Post by JamesMintram on 2007-08-20
Thank you for your reply.

I have tried looking for those files, I have tried removing qmail (using apt-get remove). There is no trace of them on my filesystem anywhere.

/etc/xinetd doesnt exist
/etc/qmail doesnt exist

I cant find it anywhere on the filesystem. Another strange thing, I have now installed proftpd with apt-get (according to apt-get it wasn't installed before even though there was a proftpd process running after a reboot ) but it seems there are 2 versions of it now, the one I mentioned before gets loaded before the version I installed with apt-get so I have to manually kill the process running then call "/etc/init.d/proftpd start" to get the version I installed running.

I think I may not be running on a truly dedicated server, and these programs are loading from another filesystem before I get chrooted into my root directory.

If this is the case is it possible to find out whether I am renting a virtual dedicated server or a truly dedicated server? 

I could be talking rubbish but this is doing my screw now!!

If anyone else has used a dedicated server from 123-reg.co.uk maybe they could shed some light on this  matter?

Thank you,

---

### Post by Mr. C. on 2007-08-20
The /etc/* directories are generally configuration directories; binaries (programs) are not located there.  Try:

```
locate qmail
locate xinet
```

I have no info with respect to your hosting company and the service you are getting.

MrC

---

### Post by JamesMintram on 2007-08-20
Ok I've done locate with both of those, xinetd came up with nothing whilst qmail came up with this:

```

/usr/share/perl5/Mail/Mailer/qmail.pm
/usr/share/squirrelmail/locale/lt_LT/LC_MESSAGES/qmailadmin_login.mo
/usr/share/squirrelmail/locale/sv_SE/LC_MESSAGES/qmailadmin_login.mo
/var/cache/apt/archives/local-qmail_1.2_all.deb
/var/qmail
/var/qmail/control
/var/qmail/control/defaultdomain
/var/qmail/control/locals
/var/qmail/control/me
/var/qmail/control/plusdomain
/var/qmail/control/rcpthosts

```

From what i can gather there are no config files for configuring qmail when it loads!

---

### Post by Mr. C. on 2007-08-20
It seems likely then that there are other processes outside your purview.  Contact your hosting company.

MrC

---

### Post by JamesMintram on 2007-08-20
Ok, thank you very much for your help!

---

### Post by oliver341 on 2007-10-19
> **JamesMintram said:**
> If anyone else has used a dedicated server from 123-reg.co.uk maybe they could shed some light on this  matter?
Hi James,

I also have a 123-reg dedicated server running Ubuntu 6.06 LTS. I too have noticed these strange processes which do not appear to exist on the server.

As far as I can make out, the server is partitioned in such a way that there is a partition we do not have access to. This is the partition that holds the boot images, the kernel, and essential processes.

Once the server has booted off this "untouchable" partition, the boot process is continued on another partition, i.e. the partition we have access to. The scripts from /etc/rc3.d/ are then executed from this second partition.

I think they do this so it is harder for their customers to break stuff. On the other hand it makes it impossible for us to upgrade our kernels and run certain commands such as "df" and "reboot" (although "reboot -f" will reboot it uncleanly).

My solution is to run 2 scripts in /etc/rc3.d/ - one to shut down all the processes loaded up by the untouchable partition, and the second one starts the processes I want to run. Most of the processes can be killed with "killall" although a couple do respawn when killed. I use sleep delays inside the scripts so that the process killing script doesn't clash with the process loading script! Be very careful if you attempt this because 123-reg will flat-out refuse to help you if you break the server with root access (although they did help me once when I messed up SSH).

I might move away at some point so I can rent a server with full control. But for the time being I'm staying because the server is fast and cheap (by UK prices).

Hope that helps,
Oliver.

---

### Post by Rmantingh on 2008-03-29
To get access to the 'hidden' areas on your dedicated server have a look at this thread:-
[http://ubuntuforums.org/showthread.php?t=723132](http://ubuntuforums.org/showthread.php?t=723132) (post #9)

---

### Post by Oldsoldier2003 on 2008-03-30
Bad idea. this would be justification for your contract to be terminated without a refund in 99.99% of cases. Even in England :)

---

### Post by oliver341 on 2008-03-30
> **Rmantingh said:**
> To get access to the 'hidden' areas on your dedicated server have a look at this thread:-
[http://ubuntuforums.org/showthread.php?t=723132](http://ubuntuforums.org/showthread.php?t=723132) (post #9)

I can't test this as I moved to a dedicated server provider who allow full control over the whole server, 1&1 Internet. It's £10 + vat more per month than 123-reg, but for me it's worth it as I can upgrade the kernel. In addition it has software RAID and an off-server FTP backup, along with 1 GB RAM and an unmetered 100 mb connection, so the extra cost is more than worth it (I have no commercial connection to 1&1, I'm just a satisfied customer).

Only one downside, the servers are in Germany, so UK users will see a little bit of lag on things like SSH.

> **Oldsoldier2003 said:**
> Bad idea. this would be justification for your contract to be terminated without a refund in 99.99% of cases. Even in England :)

Why would they? It's a **dedicated** server, one is fully entitled to hack one's own server.

---

### Post by Oldsoldier2003 on 2008-03-30
> **oliver341 said:**
> I can't test this as I moved to a dedicated server provider who allow full control over the whole server, 1&1 Internet. It's £10 + vat more per month than 123-reg, but for me it's worth it as I can upgrade the kernel. In addition it has software RAID and an off-server FTP backup, along with 1 GB RAM and an unmetered 100 mb connection, so the extra cost is more than worth it (I have no commercial connection to 1&1, I'm just a satisfied customer).

Only one downside, the servers are in Germany, so UK users will see a little bit of lag on things like SSH.



Why would they? It's a **dedicated** server, one is fully entitled to hack one's own server.
Dedicated server is not the same as "owned". I don't have a copy of the ToS for that company, and tbh could care less- but its bad form and very likely will end you in a no support situation at the very least. Breaking the chroot security configuration of the server may very well get the user booted if the ToS of the host says so.

Bottom line he doesn't own the machine so its a risky proposition. Best to just find a host thats worth a crap...

Edit... after further thought i decided to look at their AUp. Fact is if he does it he's hosed should they choose to do pursue the matter.
here its is:
Attempted security breaches

Any attempt to breach the security of any machine is forbidden. Attempting to do so will result in immediate account termination and possible further legal action. Users may not run any program that monitors network packet data or any program that compromises the privacy of network traffic.

---

### Post by oliver341 on 2008-03-30
> **Oldsoldier2003 said:**
> Dedicated server is not the same as "owned". I don't have a copy of the ToS for that company, and tbh could care less- but its bad form and very likely will end you in a no support situation at the very least. Breaking the chroot security configuration of the server may very well get the user booted if the ToS of the host says so.
Breaking the chroot security configuration (if that's what's in effect) wouldn't damage the hardware which is all 123-reg would be concerned about. Also, 123-reg could be sued for selling a server with "full control" when in fact you do not get "full control" at all.

As for "no support", 123-reg automatically give you no support when you opt for "root access". In order to get root access you have to tick a box to say you agree that you will no longer be entitled to any support. It's not one of the cheapest dedicated servers in the UK for no reason!

> Bottom line he doesn't own the machine so its a risky proposition. Best to just find a host thats worth a crap...

As indeed **I** did.

---

### Post by Oldsoldier2003 on 2008-03-30
> **oliver341 said:**
> Breaking the chroot security configuration (if that's what's in effect) wouldn't damage the hardware which is all 123-reg would be concerned about. Also, 123-reg could be sued for selling a server with "full control" when in fact you do not get "full control" at all.

As for "no support", 123-reg automatically give you no support when you opt for "root access". In order to get root access you have to tick a box to say you agree that you will no longer be entitled to any support. It's not one of the cheapest dedicated servers in the UK for no reason!



As indeed **I** did.

Apparently he didn't opt for root access. A reply in one of the other threads on this subject says that you can get true root access from the company. I guess they have a "managed" dedicated server option... strange huh?

---

### Post by oliver341 on 2008-03-30
> **Oldsoldier2003 said:**
> Edit... after further thought i decided to look at their AUp. Fact is if he does it he's hosed should they choose to do pursue the matter.
here its is:
Attempted security breaches

Any attempt to breach the security of any machine is forbidden. Attempting to do so will result in immediate account termination and possible further legal action. Users may not run any program that monitors network packet data or any program that compromises the privacy of network traffic.

Sounds relevant to shard hosting, as you would be affecting others. It seems one has to hack the server to gain "full control" as the sales information promises.

---

### Post by oliver341 on 2008-03-30
> **Oldsoldier2003 said:**
> Apparently he didn't opt for root access. A reply in one of the other threads on this subject says that you can get true root access from the company. I guess they have a "managed" dedicated server option... strange huh?

Basically by default the dedicated server comes with a basic web hosting control panel. This is very limiting, it doesn't even have SSH, but it is supported by 123-reg. The OP must have opted for "root access" as he is issuing SSH commands, but in doing so you must tick a box to say you will not be entitled to any more support.

It doesn't even have a re-imaging option, so if you do mess something up after 1 month, you could be stuck with 11 months on your contract and an unusable server.

---

