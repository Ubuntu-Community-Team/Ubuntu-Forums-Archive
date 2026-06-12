---
title: "Monitoring vsftpd (ftpwho, ftptop alike)"
date: 2008-07-30
forum: Server Platforms
---

### Post by rasemmi on 2008-07-30
Hiho,

I finally managed to get the very secure FTP server "vsftpd" doing almost what I need. The only thing I still missed was a tool to monitor its activities - at best in real-time. Since I couldn't find any ready-made solution, I tried myself to find one using common Linux commands. For my needs I elaborated three reasonable alternatives I can't prevent you from. ;)


1. Process Snapshot

1.1 Prerequisites
Directive in /etc/vsftpd.conf:
setproctitle_enable=YES

1.2 Console Command
watch ps -C vsftpd -o user,pid,stime,cmd

1.3 Comments
Edit your vsftpd.conf file to include the directive above. Restart vsftpd. Open a console and issue the command above.
You will get a list of current processes with the following filters applied:
a) Executed command (-C) vsftpd
b) Output columns (-o) user, pid, stime, cmd
"watch" refreshes this list every two seconds.
Once there is any vsftpd related action you will see it almost in real-time.


2. Log File Monitor

2.1 Prerequisites
Directive in /etc/vsftpd.conf:
xferlog_enable=YES

2.2 Console Command
sudo tail -n0 -f /var/log/vsftpd.log

2.3 Comments
Edit your vsftpd.conf file to include the directive above. Restart vsftpd. Open a console and issue the command above.
You will get a list showing the last zero (-n0) lines  of your vsftpd log file (0 = nothing - don't be surprised to see nothing at first!).
Once there is any vsftpd related action you will see it almost in real-time.


3. gPS - Graphical Process Stats

3.1 Prerequisites
a) Directive in /etc/vsftpd.conf:
setproctitle_enable=YES
b) Program package "gPS" installed from the ubuntu repos.

3.2 Program Start
Start gPS from the ubuntu main menu:
Applications > Accessories > gPS Process Monitor

3.3 Comments
I'm not quite sure about the correct English menu titles - sorry. My German main menu reads:
Anwendungen > Zubehör > gPS Process Monitor
In gPS:
a) Select: View > Show long process names
b) Select: View > Continuous Refresh
c) Select: Filter > Set filter...
Set filter: Name > Greater > vsftpd
d) Select: View > Settings
for desired visible fields.


4. References
- Tested successfully under ubuntu 7.04 and 8.04.
- Manpages: vsftpd.conf, watch, ps, tail

Best regards,
raLLi

PS: The commands from section 1 and 2 fit well in the ubuntu main menu - together with entries for the vsftpd init script. My personal vsftp comfort menu now looks like:
Applications > Internet > vsFTPd >
 Restart / Start / Stop / vsFTPlog / vsFTPtop

---

