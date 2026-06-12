---
title: "Signature of the attack."
date: 2008-06-14
forum: Security
---

### Post by spike_strip on 2008-06-14
Hello--

I am attempting to establish a defensive posture w/ an Ubuntu LAMP server [Dapper]. 
I have installed Firestarter and OSSEC. 

I am running OSSEC ['local' install] on an Ubuntu LAMP server. Every thing went well during the install and I am receiving periodic e-mail notification. 

If the system were to experience an attack—OSSEC--is going to recognize the signature, of the attack, and then notifies me. Signatures can only exist if they are known, therefore, if a new attack vector is used it will not match a pattern and OSSEC will not detect it!

It also utilizes a Analysis Engine[?] that will notice differences between normal patterns and abnormal patterns; if configured to do so. 

Does anyone know what analysis method [pattern matching or anomaly matching] OSSEC uses?

Does anyone know how to properly configure OSSEC to recognize new attack signatures.

~Corbin

P.S. I have researched the OSSEC documentation to determine what detection methodologies are being used. Are the using a Pattern Statefull Matching Engine or Anomaly Based engine...no luck!

---

### Post by pytheas22 on 2008-06-14
As I understand it, OSSEC basically watches log files (by default, syslog, but you can add other logs to watch as well) and creates alerts when it notices certain strings.  The things that it looks for are specified in rules files (look in /var/ossec/rules).  For example, rule 5104, which looks like this:
```

<rule id="5104" level="8">
    <if_sid>5100</if_sid>
    <regex>Promiscuous mode enabled|</regex>
    <regex>device \S+ entered promiscuous mode</regex>
    <description>Interface entered in promiscuous(sniffing) mode.</description>
    <group>promisc,</group>
</rule>
```

causes an alert to be created whenever the strings (regexes really) "Promiscuous mode enabled" or "device \S+ entered promiscuous mode" are detected in the log files.

OSSEC comes with a comprehensive set of rules, but if you want to add your own you can put them in file local_rules.xml.  There's a bit of information on the OSSEC website about how to write rules, but I would recommend that you buy the OSSEC book if you really want to understand how to write rules.  It's too complex to explain here really, and unfortunately the online documentation for OSSEC is not as good as it should be.

Keep in mind that pattern matching is not OSSEC's only strategy.  It also periodically calculates file checksums in system directories to see if they've changed, and it checks for rootkits by looking for signatures...take a look /var/ossec/etc/shared/rootkit_files.txt and /var/ossec/etc/shared/rootkit_trojans.txt.  You can add custom signatures there as well.

So to answer your question, OSSEC uses both pattern matching and anomaly checking because it uses several different strategies for detecting intrusions.

---

### Post by The Cog on 2008-06-15
OSSEC also uses log entry counting to spot unusual increases in activity. For several weeks after we rolled out a new web service, OSSEC kept telling us we had done lots more apache log entries than the same hour last week.

---

### Post by spike_strip on 2008-06-15
Thanks for the information...

With regards to updates; is OSSEC keep up-to-date with most recent signatures of newly discovered attacks, via some OSSEC support[?] 
Tunning [OSSEC] and keeping it up-to-date might be a challenge! 

I will need to do more research; I would like to know if it is also capable of detecting Anomalies within a given Protocol [i.e. HTTP] some IDS, if the receive a packet that deviates from the protocol standards, it will notice different attributes and send an alert. 

Overall OSSEC appears to have a rather well defined baseline—when installed, and is a great addition to my local security.

---

### Post by pytheas22 on 2008-06-15
> With regards to updates; is OSSEC keep up-to-date with most recent signatures of newly discovered attacks, via some OSSEC support[?]
Tunning [OSSEC] and keeping it up-to-date might be a challenge!

I will need to do more research; I would like to know if it is also capable of detecting Anomalies within a given Protocol [i.e. HTTP] some IDS, if the receive a packet that deviates from the protocol standards, it will notice different attributes and send an alert.

Although OSSEC does have some capacity to detect some kinds of anomalies on its own, it's not designed to replace other programs.  If you want to have the most up-to-date signatures for rootkits and trojans, you should run an anti-rootkit/trojan program like chkrootkit and have it update and run periodically.  OSSEC will watch the chkrootkit logs and forward to you reports of malicious activity.

For packet inspection, you should use Snort, which is designed specifically for monitoring network activity.  Once you have Snort installed and point OSSEC to the location of the Snort logs, OSSEC will forward you alerts from Snort as well.

---

### Post by spike_strip on 2008-06-15
Good advice hear: 
> **pytheas22 said:**
> 
For packet inspection, you should use Snort, which is designed specifically for monitoring network activity.  Once you have Snort installed and point OSSEC to the location of the Snort logs, OSSEC will forward you alerts from Snort as well.

I have installed Snort and would like to point OSSEC to Snort logs. Do not know how to do this; I must edit the QSSEC cof file?

Please advise...thanks!

---

### Post by spike_strip on 2008-06-15
I added to ossec conf: ```
 <localfile>
    <log_format>snort</log_format>
    <location>/var/log/snort</location>
  </localfile>
```

Not sure the syntax is correct[?]

---

### Post by spike_strip on 2008-06-15
This did not work: 
> **spike_strip said:**
> I added to ossec conf: ```
 <localfile>
    <log_format>snort</log_format>
    <location>/var/log/snort</location>
  </localfile>
```

Not sure the syntax is correct[?]

Got this error when I restarted ossec: 
```
Starting OSSEC HIDS v1.5 (by Daniel B. Cid)...
2008/06/15 19:53:55 ossec-logcollector(1235): ERROR: Invalid value for element 'log_format': snort.
2008/06/15 19:53:55 ossec-logcollector(1202): ERROR: Configuration error at '/var/ossec/etc/ossec.conf'. Exiting.
2008/06/15 19:53:55 ossec-logcollector(1202): ERROR: Configuration error at '/var/ossec/etc/ossec.conf'. Exiting.
ossec-logcollector: Configuration error. Exiting
```

---

### Post by pytheas22 on 2008-06-15
> Not sure the syntax is correct[?]

Almost correct, but <log_format> tells OSSEC what kind of protocol the log file follows, not what kind of log it is.  Snort logs in Unix syslog format, so you just need to put 'syslog.'  Also I think the more precise location of the Snort alert log is /var/log/snort/alert.  Try this:```

<localfile>
	<log_format>syslog</log_format>
	<location>/var/log/snort/alert</location>
</localfile>
```

---

### Post by spike_strip on 2008-06-15
That worked...I was able to stop and re-start with no error. 

The feedback is much appreciated. 

Now; I guess I must configure Snort!

---

### Post by pytheas22 on 2008-06-15
No problem, glad you got it working.

The default install of Snort is not bad.  It will at least detect port scans and things.  But it does take a lot of work to get it really customized to your needs.  But there are plenty of guides you can read online for that.

---

