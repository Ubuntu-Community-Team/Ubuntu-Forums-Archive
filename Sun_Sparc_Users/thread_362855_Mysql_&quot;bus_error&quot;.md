---
title: "Mysql &quot;bus error&quot;"
date: 2007-02-16
forum: Sun Sparc Users
---

### Post by jimflip on 2007-02-16
Hi

I have installed ubuntu server 6.10 onto my dual processor Ultra 60.
I have two 36 Gig scsi hard drives, one drive has 1gig swap space, the other 1gig /boot (bootable) partition; the rest of the space on these hard drives are setup up as a raid-1 device which is used for the / partition.

I have followed the instructions from here : 

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

A problem occurs when i try to do the following command:

mysqladmin -h myserver.mydomain.tv -u root password myrootpassword

it returns : Bus Error

Without mysql working my system is useless :(

mysql -V reveals: Ver 14.12 Distrib 5.0.24a

5.0.24a makes me think it is an alpha version, obviously not great.

Any help in fixing this would be great or information on getting a more stable version of mysql.

Thanks,
Jim.

---

### Post by jimflip on 2007-02-17
I'd imagine most sparc ubuntu systems have mysql running, if someone could confirm they have and what version that would be a useful start.

I have come to ubuntu as I was sick of so many problems like this with solaris, it's not looking much better with ubuntu so far.

---

### Post by jimflip on 2007-02-18
Some more information:

ltrace mysqladmin -h myserver.mydomain.tv -u root password myrootpassword

gives:

__libc_start_main(74004, 7, 0xff4cda54, 79980, 79964 <unfinished ...>
_init(0, 0, 0, 0, 0 <unfinished ...>
<... __libc_start_main resumed> )                = 71048
Segmentation fault

---

### Post by jimflip on 2007-02-22
Please can someone confirm they have mysql running on a sparc machine?

Also which version if possible.

Thanks,
James.

---

### Post by Sektion9 on 2007-04-13
Jim, 

Have you received any help with this issue yet?  I am running an Ultra 5 and experiencing the exact same error with the exact same command.

-S9-

---

### Post by nfld.republic on 2007-05-24
I have the same error but with Ubuntu 6.06 LTS on dual processor  UltraSPARC-II 360MHz Ultra 60.  I also have 1 GB RAM and 1 GB swap.

If I try to run 
   [FONT="Courier New"]#mysqladmin -h myservername.mydomain.com -u root password newpassword[/FONT]
it will crash with a "Bus error"

An ltrace gives the results:
[FONT="Courier New"]__libc_start_main(73800, 7, 0xffbd9aa4, 79552, 79680 <unfinished ...>
_init(0, 0, 0, 0, 0)                             = 0
my_init(1, 0, 0xffbd9a30, 0, 0)                  = 0
mysql_init(0xffbd8df8, 0, 0xffbd9a30, 0, 0)      = 0xffbd8df8
load_defaults(82600, 158736, 0xffbd9a04, 0xffbd9a08, 0) = 0
handle_options(0xffbd9a04, 0xffbd9a08, 157008, 72340, 0) = 0
signal(2, 0x1171c)                               = NULL
signal(15, 0x1171c)                              = NULL
mysql_options(0xffbd8df8, 0, 0xffbd99b4, 0, 158756) = 0
mysql_real_connect(0xffbd8df8, 0xffbd9b9f, 296264, 0, 0 <unfinished ...>
--- SIGBUS (Bus error) ---
+++ killed by SIGBUS +++[/FONT]

Anyone have any fix?

Thanks
Mike

---

### Post by yordin on 2007-05-29
All: I have the same issue on a U2 + a U60 dual cpu.
If i use the IP of the local or remote system, it works so I'm happy for now.
However, if anyone comes up with a way to use names, I would like that very much.
Rgrds:
/Y

---

### Post by werdz on 2008-01-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/179905](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/179905) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm having hte same problem on a Niagara T1 Ultrasparc running dapper. I've submitted a bug to launchpad, as nobody else seems to have...

[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/179905](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/179905)

---

### Post by werdz on 2008-01-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/179905](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/179905) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi all,

I've found a solution to the problem, but for now you'll have to compile your own mysql :)

When running configure, set CFLAGS=DUNDEF_HAVE_GETHOSTBYNAME_R and CXXFLAGS=DUNDEF_HAVE_GETHOSTBYNAME_R .

This will disable calls to gethostbyname_r, which is the function that resolves domain names.This fixes the problem - I'm not sure if the bug lies in gethostbyname_r or the way mysql calls it, but either way this solves the immediate problem.

I've submitted details of the fix (and a patch for a later version of mysql) to launchpad. Hopefully this will be fixed in upcoming revisions of the binary.

---

