---
title: "SUID and SGID permissions"
date: 2007-06-06
forum: Server Platforms
---

### Post by meman63 on 2007-06-06
OK,  I was just going through my SUID and SGID perms files and noticed that feisty has a pretty robust upfront policy.

But there were a few things I found I could improve for my situation.

Now since at my home box I don't use any kind of remote SSH,I chmod -s this:/usr/lib/openssh/ssh-keysign

Also if I use other machines to print,I chmod -s this:/usr/lib/cups/backend-available/lpd
I also don't need,as a home user,chsh... so I chmod -s /usr/bin/chsh

In addition to chsh,which is ChangeShell....basically,if you want to use a different shell(BSH,CSH,ZSH,etc)there is another that I like to take SUID away from,that is  /usr//bin/chfn.


Include these if you're an average Joe at home :/usr/bin/traceroute6
                                                                                      /usr/bin/newgrp
                                                                                      /usr/lib/pt_chown
                                                                                     
There are many more that may fit your needs and I won't elaborate too far here.

The command to find your own SUID & SGID files are:SUID: sudo find / -type f -perm -04000 -ls

                                                                                                 SGID:sudo find / -type f -perm -02000 -ls

See what you really need and be free!

Regards,
          Scott

---

