---
title: "awstats.pl"
date: 2007-07-27
forum: Server Platforms
---

### Post by mutation on 2007-07-27
I have awstats installed but when ever i try and check them with [www.domain.com/stats/](www.domain.com/stats/) it ask to download or open with text editor, and idea what i have done wrong?

---

### Post by jtc on 2007-07-27
Sounds like your Apache isn't processing awstats.pl as a script. Do you have mod_cgi enabled? Are cgi:s allowed to be run from /stats/ ?

---

### Post by mutation on 2007-07-31
i now have awstats no longer asking to save awstats.pl but when it opens i have a blank page any idea where to look?

---

### Post by mutation on 2007-08-01
bump - could really use some help on this
:confused:

---

### Post by Mr. C. on 2007-08-03
Look in your apache web logs under /var/log.  You want the access.log and error.log files.

MrC

---

### Post by mutation on 2007-08-03
in the error.log i get

exit signal Segmentation fault (11)

every time i try and get to the stats
:(

---

### Post by Mr. C. on 2007-08-03
From the command line, what happens when you run:

```
perl /var/www-data/awstats/wwwroot/cgi-bin/awstats.pl -config=*config_name* -output 2>&1 | less -cs
```

[LIST]
[*]Change the path above as necessary to locate your awstats.pl
[*]Replace your *config_name* above with your configuration file name.  I don't know where you store it.
[/LIST]

MrC

---

### Post by mutation on 2007-08-03
<html><body>
<br /><span style="color: #880000">
Error: SiteDomain parameter not defined in your config/domain file. You must edi
t it for using this version of AWStats.
</span><br />
<br /><b>Setup ('/etc/awstats/awstats.conf' file, web server or permissions) may
 be wrong.</b><br />
Check config file, permissions and AWStats documentation (in 'docs' directory).
</body></html>

---

### Post by Mr. C. on 2007-08-03
Well, there's a start.

You need to run the command I gave as the web user:

```
sudo -u www-data perl /var/www-data/awstats/wwwroot/cgi-bin/awstats.pl -config=config_name -output 2>&1 | less -cs

```

Is SiteDomain defined in your config file ?

MrC

---

### Post by mutation on 2007-08-03
<html><body>
<br /><span style="color: #880000">
Error: SiteDomain parameter not defined in your config/domain file. You must edi
t it for using this version of AWStats.
</span><br />
<br /><b>Setup ('/etc/awstats/awstats.conf' file, web server or permissions) may
 be wrong.</b><br />
Check config file, permissions and AWStats documentation (in 'docs' directory).
</body></html>


i have a separate config file for each domain

---

### Post by mutation on 2007-08-03
ok changle the command to run from one of my configs 


<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html lang='en'>
<head>
<meta name="generator" content="AWStats 6.5 (build 1.857) from config file awsta
ts.************.ca.conf (http://awstats.sourceforge.net)">
<meta name="robots" content="noindex,nofollow">
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1">
<meta http-equiv="description" content="Awstats - Advanced Web Statistics for ah
olattafun.ca (2007-08)">
<title>Statistics for **************.ca (2007-08)</title>
<style type="text/css">
<!--
body { font: 11px verdana, arial, helvetica, sans-serif; background-color: #FFFF
FF; margin-top: 0; margin-bottom: 0; }
.aws_bodyl  { }
.aws_border { border-collapse: collapse; background-color: #CCCCDD; padding: 1px
 1px 1px 1px; margin-top: 0px; margin-bottom: 0px; }
.aws_title  { font: 13px verdana, arial, helvetica, sans-serif; font-weight: bol
d; background-color: #CCCCDD; text-align: center; margin-top: 0; margin-bottom:
0; padding: 1px 1px 1px 1px; color: #000000; }
.aws_blank  { font: 13px verdana, arial, helvetica, sans-serif; background-color
: #FFFFFF; text-align: center; margin-bottom: 0; padding: 1px 1px 1px 1px; }
.aws_data {


hope this helps

---

### Post by Mr. C. on 2007-08-03
Well, that's fine. But you have to select one of the configs, and you have to configure the file correctly.  Pick one domain, and let's get that to work.

MrC

---

### Post by mutation on 2007-08-03
here is what i get 


<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html lang='en'>
<head>
<meta name="generator" content="AWStats 6.5 (build 1.857) from config file awsta
ts.aholattafun.ca.conf (http://awstats.sourceforge.net)">
<meta name="robots" content="noindex,nofollow">
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1">
<meta http-equiv="description" content="Awstats - Advanced Web Statistics for **************.ca (2007-08)">
<title>Statistics for ****************.ca (2007-08)</title>
<style type="text/css">
<!--
body { font: 11px verdana, arial, helvetica, sans-serif; background-color: #FFFF
FF; margin-top: 0; margin-bottom: 0; }
.aws_bodyl  { }
.aws_border { border-collapse: collapse; background-color: #CCCCDD; padding: 1px
 1px 1px 1px; margin-top: 0px; margin-bottom: 0px; }
.aws_title  { font: 13px verdana, arial, helvetica, sans-serif; font-weight: bol
d; background-color: #CCCCDD; text-align: center; margin-top: 0; margin-bottom:
0; padding: 1px 1px 1px 1px; color: #000000; }
.aws_blank  { font: 13px verdana, arial, helvetica, sans-serif; background-color
: #FFFFFF; text-align: center; margin-bottom: 0; padding: 1px 1px 1px 1px; }
.aws_data {

---

### Post by Mr. C. on 2007-08-03
Good, so it is not crashing.  That's just a web page - if you redirect the output into a file, and change its permissions, you should be able to see some data.  Run the same command but add:

```
> /var/www-data/test.html
```

to the end of the file and

```
chmod a+r /var/www-data/test.html
```

Then browse to that file.

MrC

---

### Post by mutation on 2007-08-03
when i do that then i get the stats

p.s. thanx for all your help so far

---

### Post by Mr. C. on 2007-08-03
So now we know the script runs.  It now seems likely that either mod_perl or mod_cgi is crashing for some reason.

Do you have mod_perl installed ?
Do you have mod_cgi insttalled ?

If so, how were they installed?

MrC

---

### Post by mutation on 2007-08-03
they are both installed, they where installed using apt-get

---

### Post by Mr. C. on 2007-08-03
Try disabling mod_perl,restarting apache, and then running your script.

MrC

---

### Post by mutation on 2007-08-03
it is disabled but i still do not get a page

---

### Post by mutation on 2007-08-07
bump

---

### Post by Mr. C. on 2007-08-07
What do the logs show ?

I'm happy to help - but can't do so without data.  You have to take an active part in helping diagnose what is going wrong.

MrC

---

### Post by mutation on 2007-08-12
which logs would you like apache error logs?

---

### Post by Mr. C. on 2007-08-12
Any data from the apache access or error logs that show what is happening at the time you make the request is what we care about.

MrC

---

### Post by mutation on 2007-08-13
from error log

[Mon Aug 13 13:10:00 2007] [notice] child pid 6365 exit signal Segmentation fault (11)
[Mon Aug 13 13:10:00 2007] [notice] child pid 7745 exit signal Segmentation fault (11)

nothing out of the ordinary in the access log

---

### Post by Mr. C. on 2007-08-14
You might get more information if you enable DebugMessages.  See the awstats configuration documentation on this.

You might also get more assistance in the awstats forum.  Also search their forums for similar problems.  Without being able to reproduce your problem here, all I can suggest is to try to isolate the problem as much as possible.

MrC

---

