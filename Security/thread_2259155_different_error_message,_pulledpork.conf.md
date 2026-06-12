---
title: "different error message, pulledpork.conf"
date: 2015-01-02
forum: Security
---

### Post by QutoSo on 2015-01-02
[FONT=arial]Hi Forum Users,[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]my Problem is with Snort in the Version 2.9.7.0 and I this try to Install this with:[/FONT]
[FONT=arial]
[/FONT][FONT=arial]Setup Guide: &#8222;Snort 2.9.6.2 on Ubuntu 12 LTS and 14 LTS&#8220;  [/FONT]
[FONT=arial]
[/FONT][FONT=arial](from the Site: [www.snort.org]("http://www.snort.org/"))[/FONT]
[FONT=arial]
[/FONT][FONT=arial]My System is a Ubuntu 14.04 Operating System.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I'm about the Chapter 11 with the headline &#8222;Rulesets and a Snort Code&#8220;.[/FONT]
[FONT=arial]
[/FONT][FONT=arial]After editing the &#8222;/etc/snort/pulledpork.conf&#8220; like the guide,[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I run following command:[/FONT]
[FONT=arial]
[/FONT][FONT=arial]sudo /usr/local/bin/pulledpork.pl -c /etc/snort/pulledpork.conf -l[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Now I get the error message:[/FONT]
[FONT=arial]
[/FONT][FONT=arial]Checking latest MD5 for snortrules -2970.tar.gz.....[/FONT]
[FONT=arial]
[/FONT][FONT=arial]Error 422 when fetching [https://www.snort.org/]("https://www.snort.org/reg-rules/snortrules-snapshot-2970.tar.gz.md5")[reg-rules/snortrules-snapshot-2970.tar.gz.md5]("https://www.snort.org/reg-rules/snortrules-snapshot-2970.tar.gz.md5") at /usr/local/bin/pulledpork.pl line 463[/FONT]
[FONT=arial]
[/FONT][FONT=arial]main::md5file('<XXX>', 'snortrules &#8211; snapshot-2970-tar.gz' ,' /tmp/' , '[https://www.snort.org/reg-rules/](https://www.snort.org/reg-rules/)') called at /usr/local/bin/pulledpork.pl line 1847


[/FONT][FONT=arial]Now I found following text more times:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]&#8222;So,once it is working on the snort.org<[http://snort.org/](http://snort.org/)> website, the new rule_url line should be as you specified[/FONT][FONT=arial] below, with no |, ignoring the rules specified?

&#8220;[/FONT][FONT=arial]So I removed the Pipe- Symbols in the three lines with insert my <oinkcode>.[/FONT][FONT=arial]
Then the upper errormessage disappeared but a new come in additon:[/FONT][FONT=arial]

&#8222;You need to define an oinkcode, please review the rule_url section of the
pulledpork config file! &#8220;[/FONT][FONT=arial] at  /usr/local/bin/pulledpork.pl line 1801. 
[/FONT]
[FONT=arial]If I try the configuration of the pulledpork.conf from this Website:[/FONT][FONT=arial][https://code.google.com/p/pulledpork/issues/detail?id=157](https://code.google.com/p/pulledpork/issues/detail?id=157)[/FONT][FONT=arial]
I get the same error message which is there described.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]What can I do now? My search days and hours are not sucessful.  [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thanks to all,[/FONT]
[FONT=arial]QutoSo[/FONT]

---

### Post by mike281 on 2015-01-12
Hey,

I'm curious, but did you try setting up pulledpork on an earlier version of Ubuntu? Like Ubuntu 12.10 ?

I'm having an issue myself using snort with base, and I'm going to try doing the setup again on Ubuntu 12.10 32bit, instead of Ubuntu 14.04 64bit . Since I can't find anything on the internet about the error I'm getting. 

Good luck resolving your issue.

---

### Post by frank96 on 2015-03-07
Was there a solution to this problem?  I am having the exact same issue.

---

### Post by hiepsykiemcun on 2015-04-01
me, too !  HEPL ..HELP 
Nobody know fix ???

---

### Post by Bucky Ball on 2015-04-01
> **frank96 said:**
> Was there a solution to this problem?  I am having the exact same issue.

> **hiepsykiemcun said:**
> me, too !  HEPL ..HELP 
Nobody know fix ???

Obviously not as this thread has been dormant for nearly three months. Perhaps post a new one outlining your issues exactly and in the appropriate forum section (are you both using the server version?).

---

### Post by hiepsykiemcun on 2015-04-01
hi all !
[COLOR=#000000]You do not have to include the <> characters in the line.[/COLOR]

---

### Post by tancr3d on 2015-08-23
> **hiepsykiemcun said:**
> hi all !
[COLOR=#000000]You do not have to include the <> characters in the line.[/COLOR]


Hi Guys,

I had the same problem. I guess it comes from installing an older snort version and not the bleeding edge version from source.
For me helped changing the pulledpork.conf rule_url:
```
rule_url=https://www.snort.org/reg-rules/|snortrules-snapshot-2975.tar.gz|<OINKCODE>
```

Because version 2970 did not exist.

---

