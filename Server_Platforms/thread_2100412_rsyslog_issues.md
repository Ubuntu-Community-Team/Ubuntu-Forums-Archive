---
title: "rsyslog issues"
date: 2013-01-01
forum: Server Platforms
---

### Post by nariub on 2013-01-01
I am having a little issue with rsyslog.  But first some history

same machine was running 10.04 and syslog-ng
I had syslog-ng redirecting my local router and access points to it's own router.log file.

I upgraded from 10.04 to 12.04 in Sep, and obviously did not notice that I was no longer logging anything.. 

I had syslog-ng installed, it now says it isn't there.. rsyslog wasnt running.. 

after trying **sudo apt-get install syslog-ng** to no avail.

started rsyslog with **sudo service rsyslog start**

and began configuring rsyslog..
enabled udp in the rsyslog.conf file and now my routers are reporting into **/var/log/syslog**  

for the last 3 hours I have been trying to redirect these to my router.log file and out of my syslog file with no success..

I went into **/etc/rsyslog.d/50-default.conf**
and added

```
$RuleSet remote
*.*           /var/log/router.log
# only messages not from 192.0.2.1 make it past this point

# bind ruleset to tcp listener
$InputTCPServerBindRuleset remote
# and activate it:
$InputTCPServerRun 514

# switch back to the default ruleset:
$RuleSet RSYSLOG_DefaultRuleset
```


above the existing text
no love
so deleted that and 

```
$RuleSet remote
*.*           /var/log/router.log
# only messages not from 192.0.2.1 make it past this point

# bind ruleset to tcp listener
$InputTCPServerBindRuleset remote
# and activate it:
$InputTCPServerRun 514
```

at the bottom
no love
so deleted that

```
if $fromhost-ip isequal '192.168.10.1' then /var/log/router.log
& ~
if $fromhost-ip isequal '192.168.10.2' then /var/log/router.log
& ~
if $fromhost-ip isequal '192.168.10.3' then /var/log/router.log
& ~
if $fromhost-ip isequal '192.168.10.4' then /var/log/router.log
& ~
```

at the top of the file
no love
deleted that

replaced it with

```
:source, isequal, "192.168.10.1"  /var/log/router.log
:source, isequal, "192.168.10.1"  ~
:source, isequal, "192.168.10.2"  /var/log/router.log
:source, isequal, "192.168.10.2"  ~
:source, isequal, "192.168.10.3"  /var/log/router.log
:source, isequal, "192.168.10.3"  ~
:source, isequal, "192.168.10.4"  /var/log/router.log
:source, isequal, "192.168.10.4"  ~
```

and still no love..
All I have succeeded in doing is being able to suppress the routers entries into the syslog file but nothing is added to the router.log

I realize that in the end I will probably create a new rule file called 40-routers.conf or something rather than directly manipulate the default file  but any ideas what I am doing wrong on the redirection?

---

### Post by chadk5utc on 2013-01-01
Heres a couple lines from my config that I use here
> 
#Netopia
if ($fromhost-ip == '192.168.2.1') then -/var/log/router
& ~
#WirelessAP
if ($fromhost-ip == '192.168.2.2') then -/var/log/wireless
& ~


---

### Post by nariub on 2013-01-01
Thanks

tried 
> if ( $fromhost-ip == '192.168.10.1' ) then -/var/log/router.log
& ~
if ( $fromhost-ip == '192.168.10.2' ) then -/var/log/router.log
& ~
if ( $fromhost-ip == '192.168.10.3' ) then -/var/log/router.log
& ~
if ( $fromhost-ip == '192.168.10.4' ) then -/var/log/router.log
& ~

with and without spaces between the parens and the expression
with and without the dash before /var
with single and double quotes around the ip address

Put it into a separate file named 40-router.conf in /etc/rsyslog.d/

outcome is the same same..
when I enable redirection (with or without the "& ~")
it stops logging to the syslog file but does not log to the router.log file..  

comment out the lines in the 40-router.conf file and I get syslog entries again..   

seems I am missing something fundamental here.. started looking for spurious files in /var/log/ incase i misspelled the file name somewhere..?

curious..

---

### Post by chadk5utc on 2013-01-02
ok seems I had this same issue at one time I believe what I ended up doing on ubuntu to get it logging was to leave all 10.*-xx* alone and place those lines directly into rsyslog.conf at the bottom of the file. I know this is not as most suggest but was the only way I could get it logging. I now use another os for central logging.

---

### Post by koenn on 2013-01-02
> **nariub said:**
> T
seems I am missing something fundamental here.. 

yes, twice. 

1-
you don't really  need a rule set here. It can be done without Ruleset declarations, just by doing the filtering correctly
So I'd focus on getting the filtering right; you can implement RuleSets later if you think they still have added value for what you're trying to do


2- 
The order in which config statements are seen by rsyslog actually matters. That's why the files in the conf directory are numbered : so that you can follow (and manipulate) in what order rules (aka selectors) will be applied. 
You give the impression that you are randomly adding stuff to any file within reach - you need a lot of luck to get it right that way.


I suggest :

Get rid of your Ruleset and filters; For now, they're probably getting in the way 

Then get back to the point that your routers log to the syslog of your logging server

Now find the (default) rule that makes that happen, likely something like
*.* /var/log/syslog or *.notice  /var/log/syslog

add a filter just before it; if you did it right , the log entries from your routers will show up both in syslog and the dedicated log.
If that works, you can add a discards (&~) action to avoid spamming your syslog. 


A very basic filter  should be sufficient; eg I know that my switches report ip addresses as their hostname so I log them like so:
```

## 30-switches.conf
:hostname, isequal, "192.168.66.6"	/var/log/enterprise/switch.log
:hostname, isequal, "192.168.66.7"	/var/log/enterprise/switch.log

```
but it's something you need to make sure of, it's not given that ''source'' you use actually contains an IP address, ....

When you have all of that working, you can expand and organize.

I'm doing this on Debian, I suppose Ubuntu should work just the same.

---

