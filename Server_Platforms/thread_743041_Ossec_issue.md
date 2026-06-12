---
title: "Ossec issue"
date: 2008-04-02
forum: Server Platforms
---

### Post by skiamakhe on 2008-04-02
I downloaded ossec and installed it without incident. It works fine as a local installation. What I am trying is something a little unique. I read somewhere someone was doing this, so I thought I'd give it a try.

If possible, I want to be able to monitor remote devices without having to install an ossec agent. Things like network devices won't be able to install the agent, but can send syslog messages to a central server. Also, I'll have a much better chance of getting this deployed if I don't have to ask my IT guys to install stuff on their servers. This one guy's post I read somewhere (and for the life of me I can't find it again) said he basically set up his ossec box as a local installation along with syslog-ng running. Syslog would collect all the logs from the various devices, and ossec would process them as a local installation.

The initial install by itself works fine. I used winlogd to send syslog messages to my ossec box from my windows box. The messages are making it into the syslog file, but are not being processed by ossec. I checked the config file to make sure that the windows rules were being loaded and that ossec was monitoring the syslog file. 

I'm going to try the windows agent just to make sure it will process windows events, and I will also send this to the ossec people directly. Does anyone here have any thoughts?

---

### Post by evilghost on 2008-04-02
Are you using syslog-ng?  I'd be happy to share my configuration with you.

What messages specifically are you looking to redirect from Win32 to OSSEC?  I'm using NTSyslog to handle redirection of Eventlog messages to the syslog-ng server.

---

### Post by skiamakhe on 2008-04-02
Well, I was using winlogd. Every one of the events sent by winlogd to my ossec box was getting recorded in /var/log/syslog. Ossec was simply not doing anything with them.

Then I tried NTSyslog on your suggestion. Using tcpdump to verify that the packets were actually arriving, it seems that syslog-ng is not even recording a number of the packets. The ones it is recording, ossec hasn't done anything with.

I'm running ossec 1.4 on ubuntu 7.10 server. The ossec install is basically a default install without integrity checking, rootkit checking, or active response enabled. It is creating alerts for local events, just not for the syslog events from my windows box. I'm sending the defaults from NTSyslog, plus failures and info events for the security and system logs.

I just had a thought... do you have your ossec installed as a server or local install? I did mine local. Maybe it needs to be a server install to process syslog messages from other machines.

---

### Post by evilghost on 2008-04-02
Local install.  You need to be sure in your ossec.conf that you're actually looking at /var/log/syslog (in your case).

You should have a line similar to this in your ossec.conf:

```

  <localfile>
    <log_format>syslog</log_format>
    <location>/var/log/syslog</location>
  </localfile>

```

In my case I have syslog-ng directing incoming traffic to $hostname, in the format /var/log/$hostname/messages.  OSSEC is configured like so (notice the wildcard)

```

  <localfile>
    <log_format>syslog</log_format>
    <location>/var/log/*/messages</location>
  </localfile>

```

---

### Post by skiamakhe on 2008-04-02
That's what I did initially. No love. I even tried switching over to the server install, and that didn't help either. OSSEC just ignores all my windows events. Kind of disappointing. I don't have too much more time to spend on this if it's not going to work. :confused:

Do you remember having to do anything special to get this working, or did you just point your NTSyslog at ossec and watch the alerts fly?

---

### Post by evilghost on 2008-04-02
OSSEC needs to have a rule parser for the respective alerts.  What specifically are you looking for that you're not getting an alert on?  Reviewed the OSSEC alerts?  It works fine on my end, honestly.

---

### Post by skiamakhe on 2008-04-03
Right now, it's not doing *anything* with the windows logs. Nada. Bupkis. The msauth_rules.xml ruleset is loaded, and there are plenty of authentication events to process.

Can you post here your msauth_rules.xml, or send it to me? What version of ossec are you using? The syslog format between winlogd and NTSyslog are significantly different, and I think the problem lies with ossec simply not being able to parse the log entries in the format it is receiving.

I'm going to try to install an actual agent (i'm in server mode at the moment, having given up on the local installation). If that works, then maybe I'll have narrowed it down a bit. If not, then maybe there's another problem altogether.

---

### Post by skiamakhe on 2008-04-03
Well, the agent works like a champ. My guess at this point is that ossec doesn't like the syslog format being produced by either of my windows syslog clients. I'm going to try loading up ubuntu desktop on another machine and have it point some logs at ossec. Maybe a true syslog-ng format log entry will be recognized.

---

