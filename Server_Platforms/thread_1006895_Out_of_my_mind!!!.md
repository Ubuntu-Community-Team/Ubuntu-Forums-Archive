---
title: "Out of my mind!!!"
date: 2008-12-09
forum: Server Platforms
---

### Post by sdnelson on 2008-12-09
Folks, here's the story. I am running 8.4.1 server version with the latest packages. I am running SpamAssassin, Procmail and Postfix which is giving me a load of grief. 

Here is the scenario:

1. Using /etc/aliases file I place an include into the file like this:
   
   staff_all: :include:/groups/staff_all.txt 

   In staff_all.txt there are approximately 30 email addresses
   in a list which look like this:

   [email]steve@myschool.org[/email]
   [email]fred@myschool.org[/email]

   etc...

2. If I use the scenario above, Spamassasin segfaults three or four time in the kern.log file. Mind you this does work and folks are receiving email. Now, If I remove the :include: section and place email address in the file like this:

   staff_all: steve, fred, ....

   No more segfaults.. :confused:

Has anyone seem or heard of this issue before? I have the correct permissions on the file and I made sure the postfix knows about the include in the aliases file.

Thanks in advance,
Steve


=================================================================

Just a quick update for everyone. First off, my server had a bad memory module (Thanks Memtest !!), however, it didn't stop the Spamassassin segfaults from happening. What I did was to install "spamc" and use this as a filter in postfix master.cf, totally bypassing Procmail altogether. No more segfaults. Here's a sample:

In the master.cf - change this:

smtp      inet  n       -       -       -       -       smtpd

to this:

smtp      inet  n       -       n       -       -       smtpd -o content_filter=spamassassin

Then add an entry at the bottom of your master.cf file that looks like this:

spamassassin unix   -    n    n    -    -    pipe 
   flags=R user=spamuser argv=/usr/bin/spamc -e /usr/sbin/sendmail -oi -f $

Once complete. Start and Stop Spamassassin and then postfix.

If you use procmail, remove or comment the "mailbox_command = /usr/bin/procmail" command and restart postfix.

Good Luck.

---

