---
title: "Serverguide - Kernel differences"
date: 2012-04-03
forum: Server Platforms
---

### Post by Doug S on 2012-04-03
Background: Over the past several weeks, I have been helping with the Ubuntu Server guide edits for the pending 12.04 release. The deadline for completion was March 22nd, but an extra week was added, which has also gone by. Due to some translation issues, there might still be time to fit in another couple of changes.
 
There is no longer different kernel versions for server and desktop, and I don't think there was for 11.10 either. There definately was for 10.10. Although that doesn't mean they might not have different runtime configuration parameters.
 
There is a small segment near the start of the installation chapter called "Server and desktop differences" with a sub-section called "Kernel Differences":
> 
 
[SIZE=3][FONT=Times New Roman][SIZE=3][FONT=Times New Roman]The Server Edition uses the [/FONT][/SIZE]
[LEFT][/FONT][/SIZE]*[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3]Deadline [/SIZE][/FONT][/SIZE][/FONT]*[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3]I/O scheduler instead of the [/SIZE][/FONT][/SIZE][/FONT]*[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3]CFQ [/SIZE][/FONT][/SIZE][/FONT]*[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3]scheduler used by the[/SIZE][/FONT][/SIZE][/FONT][/LEFT]

[SIZE=3][FONT=Times New Roman][LEFT][SIZE=3][FONT=Times New Roman]Desktop Edition.[/FONT][/SIZE]
[LEFT][SIZE=3][FONT=Times New Roman]• [/FONT][/SIZE][/FONT][/SIZE][/LEFT]
[/LEFT]
[SIZE=3][FONT=Times New Roman]
 
[LEFT][/FONT][/SIZE]*[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3]Preemption [/SIZE][/FONT][/SIZE][/FONT]*[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3]is turned off in the Server Edition.[/SIZE][/FONT][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman][SIZE=3][FONT=Times New Roman]• The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.[/FONT][/SIZE][/FONT][/SIZE][SIZE=3][FONT=Times New Roman][/LEFT]
[/FONT][/SIZE]
[LEFT]Now, I know for certain that the basic server tick rate is 250 Hertz, and I already have a pending edit proposal to delete that line. (Actually the default kernels are tickless now, so the whole statement wasn't really correct anyhow.)[/LEFT]
 
[LEFT]I am looking for authoritative information about the other two lines. Should they be deleted also? Can anyone say for certain, or point me to someone that can?[/LEFT]
 
[LEFT]Thanks.[/LEFT]
 
[LEFT]References: [11.10 guide.]("https://help.ubuntu.com/11.10/serverguide/C/preparing-to-install.html") [12.04 notes]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Ubuntu_Kernel")[/LEFT]

---

### Post by CharlesA on 2012-04-03
I can't help much, but maybe contact someone in the kernel team or in the Ubuntu +1 forum. They seem to know a bit about it. ;)

Sidenote: Thanks for the link with the info about the kernel. I was wondering why I wasn't able to find the "server" version of the kernel in 12.04 beta.

---

### Post by Doug S on 2012-04-03
Thanks for the suggestion. I contacted a member of the kernel team and got the authoritative answer I was looking for.

---

### Post by CharlesA on 2012-04-03
> **Doug S said:**
> Thanks for the suggestion. I contacted a member of the kernel team and got the authoritative answer I was looking for.
Good to know.

Thanks!

---

