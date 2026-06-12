---
title: "spamassassin (spamd) possible perl module error"
date: 2014-05-28
forum: Server Platforms
---

### Post by ryan87 on 2014-05-28
Hi all,

Could somebody please point me in the direction of where to start looking so I can solve this problem please. I've followed a series of articles on Ars Technica about setting up Postfix with spamassassin milter. I've been looking though the log files and have found the following:

```

[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]: Can't locate Net/DNS/RR/MX.pm: Permission denied at (eval 1274) line 2.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]:  RR at octet 27 corrupt/incomplete at /usr/share/perl5/Mail/DKIM/DNS.pm line 177.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]: Can't locate Net/DNS/RR/A.pm: Permission denied at (eval 1275) line 2.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]:  RR at octet 48 corrupt/incomplete at /usr/share/perl5/Mail/SpamAssassin/Dns.pm line 263.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]: Can't locate Net/DNS/RR/A.pm: Permission denied at (eval 1276) line 2.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]:  RR at octet 55 corrupt/incomplete at /usr/share/perl5/Mail/SpamAssassin/Dns.pm line 263.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]: Can't locate Net/DNS/RR/TXT.pm: Permission denied at (eval 1277) line 2.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]:  RR at octet 46 corrupt/incomplete at /usr/share/perl5/Mail/SpamAssassin/Dns.pm line 263.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]: Can't locate Net/DNS/RR/A.pm: Permission denied at (eval 1278) line 2.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]:  RR at octet 45 corrupt/incomplete at /usr/share/perl5/Mail/SpamAssassin/Plugin/URIDNSBL.pm line 1097.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]: Can't locate Net/DNS/RR/A.pm: Permission denied at (eval 1279) line 2.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]:  RR at octet 47 corrupt/incomplete at /usr/share/perl5/Mail/SpamAssassin/Dns.pm line 263.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]: Can't locate Net/DNS/RR/A.pm: Permission denied at (eval 1280) line 2.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]:  RR at octet 47 corrupt/incomplete at /usr/share/perl5/Mail/SpamAssassin/Dns.pm line 263.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]: Can't locate Net/DNS/RR/A.pm: Permission denied at (eval 1281) line 2.[/FONT]
[FONT=Menlo]May 28 21:21:04 nx01 spamd[14792]:  RR at octet 46 corrupt/incomplete at /usr/share/perl5/Mail/SpamAssassin/Plugin/URIDNSBL.pm line 1097.[/FONT]
[FONT=Menlo]May 28 21:21:05 nx01 spamd[14792]: Can't locate Net/DNS/RR/A.pm: Permission denied at (eval 1282) line 2.[/FONT]
[FONT=Menlo]May 28 21:21:05 nx01 spamd[14792]:  RR at octet 45 corrupt/incomplete at /usr/share/perl5/Mail/SpamAssassin/Plugin/URIDNSBL.pm line 1097.[/FONT]
[FONT=Menlo]May 28 21:21:05 nx01 spamd[14792]: Can't locate Net/DNS/RR/A.pm: Permission denied at (eval 1283) line 2.[/FONT]
[FONT=Menlo]May 28 21:21:05 nx01 spamd[14792]:  RR at octet 42 corrupt/incomplete at /usr/share/perl5/Mail/SpamAssassin/Plugin/URIDNSBL.pm line 1016.[/FONT]
[FONT=Menlo]May 28 21:21:06 nx01 spamd[14792]: Can't locate Net/DNS/RR/NS.pm: Permission denied at (eval 1284) line 2.[/FONT]
[FONT=Menlo]May 28 21:21:06 nx01 spamd[14792]:  RR at octet 29 corrupt/incomplete at /usr/share/perl5/Mail/SpamAssassin/Plugin/URIDNSBL.pm line 931.[/FONT]

``` 

I've check the modules any they are there. spamassassin --lint shows no errors and when I run with -D I get the following:

```

[FONT=Menlo]spamassassin -D --lint 2>&1 | grep -i failed[/FONT]
[FONT=Menlo]May 28 21:38:47.844 [14922] dbg: diag: [...] module not installed: Digest::SHA1 ('require' [COLOR=#c33720]**failed**[/COLOR])[/FONT]
[FONT=Menlo]May 28 21:38:48.985 [14922] warn: plugin: eval [COLOR=#c33720]**failed**[/COLOR]: Insecure dependency in sprintf while running with -T switch at /usr/share/perl5/Mail/SpamAssassin/Logger.pm line 241.[/FONT]
[FONT=Menlo]May 28 21:38:48.990 [14922] warn: plugin: eval [/FONT][COLOR=#C33720][FONT=Menlo]**failed**[/FONT][/COLOR][FONT=Menlo]: Insecure dependency in sprintf while running with -T switch at /usr/share/perl5/Mail/SpamAssassin/Logger.pm line 241.
[/FONT]
``` 

The SHA1 is OK as the package has been removed from Ubuntu starting from release 12.10 I think. 

Here is a link to part 4 of the Ars Technica article on running your own e-mail server for anybody who is interested. [http://arstechnica.com/information-technology/2014/04/taking-e-mail-back-part-4-the-finale-with-webmail-everything-after/](http://arstechnica.com/information-technology/2014/04/taking-e-mail-back-part-4-the-finale-with-webmail-everything-after/) Part 4, links back to parts 1, 2 and 3.

Many thanks for any pointers
Ryan

---

