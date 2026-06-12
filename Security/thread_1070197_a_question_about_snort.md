---
title: "a question about snort"
date: 2009-02-14
forum: Security
---

### Post by Murth on 2009-02-14
So I've been reading the snort guide and have got it all up and running successfully. however checking the logs in BASE i get spammed with warnings for a connection I would like to allow.

(ftp_telnet) Telnet traffic encrypted 	 2009-02-14 20:27:12 	 64.127.116.163:23 	 192.168.15.2:50551 	 TCP

reading the forum posts and the snort's website just gets me a little bit more confused...

Could someone please enlighten me on how to properly allow this connection?

---

### Post by bodhi.zazen on 2009-02-15
Snort , by default, is a packet sniffer. It does not block traffic, just logs suspicious traffic based on rules.

You can either ignore that rule in base, modify the rule, delete the rule, or white list the ip address.

---

### Post by Murth on 2009-02-15
That's what I'm asking, I'm trying to figure out how to make a rule to ignore that false alarm as it spams about 2000+ an hour or so. reading the snort page and searching google just isn't helping me,

---

### Post by bodhi.zazen on 2009-02-15
easiest way is to identify the rule (they all have numbers) and manually edit the rules (in /etc/snort/rules) and add a # at the front of the rule.

---

### Post by Murth on 2009-02-15
GEN:SID  	 126:2
Message 	telnet_pp: Telnet data encrypted
Summary 	This event is generated when the ftp-telnet preprocessor detects anomalous network traffic.
Impact 	Unknown. This is an indication of anomalous behaviour between networked assets.
Detailed Information 	This event is generated when the ftp-telnet preprocessor detects anomalous network traffic.


is that the number you are speaking of? the 126.2?

I'm just wondering if disabling all ftp/telnet alerts is safe. I mean I'm always connected to that telnet server (a Mud game) but wouldnt ftp/telnet attempts on my machine be a rather vulnerable thing?

---

### Post by bodhi.zazen on 2009-02-15
Well you have a choice, fill your logs with false positives, modify the rule, white list the ip address, or comment out the rule.

I do not have the technical expertise to help much.

I suggest you file this with snort as a false positive.

Also, where did you get your rules ? Are you using the most up to date rule set from snort ?

I understand, snort is quite technical, try searching 

For example a google search results in this thread :

[http://www.snort.org/archive-5-3124.html](http://www.snort.org/archive-5-3124.html)

---

