---
title: "cupsd authentication issues over time"
date: 2011-05-19
forum: Server Platforms
---

### Post by frio on 2011-05-19
Hi all.

For months I've searched high and low for a solution to this but have gotten nowhere. Here is a summary:

PC1 = WinXP Pro serving printers and files for home network
PC2 = Ubuntu Server Edition 10.04.2 LTS serving web, backuppc, ftp
Both behind a Netgear home router

My setup is such that I have a printer physically attached to PC1 that I want to share over HTTPS. I map to it from PC2 and all is good. I can do everything through the CUPS web interface including manage print jobs, print test pages, etc.

I share this printer as https://[my printer domain] and can connect to it AND print to it over the net as well as manage it from the CUPS web interface. No problems so far. The issue comes in after some amount of time; sometimes hours, sometimes minutes. The issue is that I start getting authentication errors and once this happens, I cannot even log into the CUPS web interface. The only solution I have found that works is to restart cupsd. Once cups is restarted, all is good again, for a while.

Here is what turns up in the logs after one authentication failure:

```
**/var/log/user.log**
May 19 13:57:15 linux1 cupsd: Unable to open log file "/var/log/cups/error_log" - Too many open files

**/var/log/auth.log**
May 19 13:57:15 linux1 cupsd: PAM _pam_init_handlers: no default config /etc/pam.d/other
May 19 13:57:15 linux1 cupsd: PAM error reading PAM configuration file
May 19 13:57:15 linux1 cupsd: PAM pam_start: failed to initialize handlers
May 19 13:57:15 linux1 cupsd: PAM _pam_init_handlers: no default config /etc/pam.d/other
May 19 13:57:15 linux1 cupsd: PAM error reading PAM configuration file
May 19 13:57:15 linux1 cupsd: PAM pam_start: failed to initialize handlers
May 19 13:57:15 linux1 cupsd: PAM _pam_init_handlers: no default config /etc/pam.d/other
May 19 13:57:15 linux1 cupsd: PAM error reading PAM configuration file
May 19 13:57:15 linux1 cupsd: PAM pam_start: failed to initialize handlers
May 19 13:57:15 linux1 cupsd: PAM _pam_init_handlers: no default config /etc/pam.d/other
May 19 13:57:15 linux1 cupsd: PAM error reading PAM configuration file
May 19 13:57:15 linux1 cupsd: PAM pam_start: failed to initialize handlers

**/var/log/syslog**
May 19 13:57:15 linux1 cupsd: Unable to open log file "/var/log/cups/error_log" - Too many open files
May 19 13:58:30 linux1 cupsd: last message repeated 8 times
```I should note (although I believe it to be unrelated) that I am reverse proxying apache so all traffic comes through standard ports, (eg. 443 for https). So this means that https://[my printer domain] is proxied to http://localhost:631 for cups. Port 631 is not open on my router.

Any suggestions or pointers are welcome (and begged for). I am out of ideas and pretty frustrated.

Thanks in advance!

---

### Post by frio on 2011-06-09
bump... I'm guessing based on the lack of responses that no one else has, or is having, this problem?

---

