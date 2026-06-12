---
title: "pam_setquota"
date: 2012-06-27
forum: Security
---

### Post by jringoot on 2012-06-27
I manage (among others) a group of workstations (7 in total) that are used 24/7 by about 25 persons, each using 1 or 2 of these at once, with each 12h shift a minimum of 4 workstations used by 2 people and maximum 7 by 4 people. (nights and holidays we have only 2 people onsite)

To reduce the chance that disks get full, I have set up (journaled) quota.

To reduce the manual work setting up everybody on all workstations
I found a big help in ldap authentication using sssd and the pam_mkhomedir.so module to get their homedir automaticly created when they login the first time.

Still I would need manual setting quota for all 25 persons on all workstations.
To avoid this and the need of custom scripting, I found  a pam module pam_setquota.so, see here: [http://www.knowplace.org/pages/howtos/automatic_user_quota_setup_with_pam_setquota.php](http://www.knowplace.org/pages/howtos/automatic_user_quota_setup_with_pam_setquota.php).
and here:
[http://code.google.com/p/pam-setquota/downloads/list](http://code.google.com/p/pam-setquota/downloads/list)

This works nice, really a cool tool.
 

Although 1  small remark, a quota of 0 is seen as an existing quota (even if it is not true), so I need to set the overwrite=1 like mentioned in the documentation.



What worries me however is that the module needs to be compiled and needs kernelheaders that ar not linked to the running kernel.

I had to link these includes myself
ln -s /usr/src/linux-headers-3.2.0-25-generic/include/linux/dqblk_v1.h /usr/include/linux/dqblk_v1.h
ln -s /usr/src/linux-headers-3.2.0-25-generic/include/linux/dqblk_v2.h /usr/include/linux/dqblk_v2.h
ln -s /usr/src/linux-headers-3.2.0-25-generic/include/linux/dqblk_qtree.h /usr/include/linux/dqblk_qtree.h

Thus when the kernel changes, I will probably not only need to recompile, but first make the correct links.

My question: To avoid some administrative burden for me as end user: Would the Ubuntu team please consider the inclusion of this module in the ubuntu main stream packages?
(or a ppa?)


Or suggest something better to set quota automagically on workstations.


Thanks,

Joost

---

### Post by Cheesemill on 2012-06-27
> **jringoot said:**
> My question: To avoid some administrative burden for me as end user: Would the Ubuntu team please consider the inclusion of this module in the ubuntu main stream packages?

This isn't the place to ask, the Ubuntu devs don't use these forums.

Instead you should post the idea on brainstorm:
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by cariboo on 2012-06-28
> **Cheesemill said:**
> This isn't the place to ask, the Ubuntu devs don't use these forums.

Instead you should post the idea on brainstorm:
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

Brainstorm only gets looked at by the dev team about twice a year, it woul better to create feature request bug on [https://bugs.launchpad.net](https://bugs.launchpad.net)

---

### Post by jringoot on 2012-06-29
Thanks guys, I decided to involve the developer into it, by contacting him via googleplus.

[https://plus.google.com/118206752464585514547/posts/WBjjVCw6HZB](https://plus.google.com/118206752464585514547/posts/WBjjVCw6HZB)

Because I feel that the module should best get first upstream integrated in the linux-pam project.

[http://www.linux-pam.org/](http://www.linux-pam.org/)

---

### Post by Cheesemill on 2012-06-29
Nice one, that is definitely the best way to go.

---

### Post by jringoot on 2012-07-11
The developer told me he stopped working on this and suggested a newer and more versatile pam module:
[pam_script]("http://manpages.ubuntu.com/manpages/precise/man7/pam-script.7.html")


For completeness, the complete answer from Russlan:
Hi Joost!

Thanks for the feedback, I don't receive mails like this often.

I'm glad you succeed in using pam_setquota. I wrote and used it 5
years ago and I haven't look at it since then. I think people use a
module named pam_script for tasks like setting quotas nowadays. But I
didn't try it myself and I don't remember if there was such a module
when I wrote pam_setquota. I think not.

As for the compilation problem, the other solution is to add
-I/usr/src/linux-headers-3.2.0-25/include/linux to the compilation
line in the Makefile. I don't know what ubuntu guys think should be in
the /usr/include/linux, Maybe kernel headers package maintainer can
provide you with the answer.


Good luck!
Ruslan


On Thu, Jul 5, 2012 at 6:45 AM, Joost Ringoot <joost@ringoot.org> wrote:
> Hi Ruslan,
>
>
> I have succefully used your pam_setquota.so module.
> (see also: [http://ubuntuforums.org/showthread.php?p=12057744](http://ubuntuforums.org/showthread.php?p=12057744))
>
> Thanks for creating/sharing it.
> (I used this guide:
> [http://www.knowplace.org/pages/howtos/automatic_user_quota_setup_with_pam_setquota.php](http://www.knowplace.org/pages/howtos/automatic_user_quota_setup_with_pam_setquota.php))
>
> However I have some questions:
> The compilation requires
> /usr/include/linux/dqblk_v1.h
> /usr/include/linux/dqblk_v2.h
> /usr/include/linux/dqblk_qtree.h
> These exist on my system but in the kernelheader directory:
> /usr/src/linux-headers-3.2.0-25/include/linux
> I worked around it with creating some symbolic links.
>
> That's not the best method I know.
> I am  quite unexperienced when it comes to compiling. I wonder now if
> this is due to a bug in the kernel header package of kernel 3.2.0-25
> on ubuntu 12.04 or should your source need a config script?
> What is your opinion?
>
> Secondly: did you ever submit the code for review by the pam project?
> [http://www.linux-pam.org/](http://www.linux-pam.org/)
> If you didn't, I think you should, since it fullfills a need, not met
> by any other module/project.
>
> Third: I like the idea for the patch that avoids forcing quota on
> people that have already quota set. Alas for my situation it didn't
> work well, since it considers a quota of 0 also as an already set
> quota. I would suggest forcing quota on users with quota 0.
>
> Thanks,
>
> Joost



--
Best regards,
Ruslan Savchenko

---

