---
title: "why is eth0 running in promiscuous mode?"
date: 2008-04-02
forum: Security Discussions
---

### Post by pytheas22 on 2008-04-02
I set up a Gutsy machine about two weeks ago to test some IDS software.  It has pretty much everything on it that comes by default, with the addition of arpwatch, OSSEC server, snort and the twm desktop environment.  OSSEC reported today that, based on an entry in the system log, the ethernet device in the machine entered promiscuous mode this morning at about 7 am.  I am the only one with an account on the machine and was not using it at that time.  This is the first time that such an incident has been reported since OSSEC started monitoring the machine a week or so ago.

I am trying to figure out if there's some legitimate reason for the device to have entered promiscuous mode--do snort or arpwatch for instance ever do this?  Right now, both of these programs (which I installed via apt-get from the official repositories) are using the default settings, with a couple of minor adjustments.

If anyone can offer any suggestions for tracking down the source of the promiscuous mode entry, I would really appreciate it, as I am trying to figure out whether there could be a system compromise.

---

### Post by HermanAB on 2008-04-02
tcpdump or wireshark will do that.

---

### Post by pytheas22 on 2008-04-02
Thanks for the reply.  Unfortunately Wireshark isn't installed and no one was running tcpdump (at least, no one should have been).  Is there anything else installed by default on Ubuntu that would do this?

---

### Post by netlogic on 2008-04-02
it could be your any network monitoring tools or utilities. Some will launch with a promiscuous mode if the driver supports it. No need to worry.

---

### Post by pytheas22 on 2008-04-02
Thanks again for the reply.  I realized that the device was only in promiscuous mode for a total of less than two seconds, according to the log--not really enough time to sniff anything worthwhile.  Also, no one deleted the relevant lines from the log, which you'd think any decent intruder would do.  So I'll assume that the system is still safe for now.  Thanks for the help.

---

### Post by netlogic on 2008-04-02
It is the apps you installed launching in the background. Since, you haven't said anything about you removed them... If you already uninstalled your IDS tools, you need to start scanning through your configuration.

---

### Post by The Cog on 2008-04-02
> No need to worry.
I have to disagree with that. I would be concerned to find that an interface had gone promiscuous without my doing anything. It is not a normal thing to happen. I just don't know how to find out what is doing it, and if your machine has been broken into, you can't trust the tools you would normally rely on like ps, netstat etc.

---

### Post by netlogic on 2008-04-02
do you know any IDS tools that don't want to listen to any traffic?

---

### Post by dannyboy79 on 2008-04-02
here's a post from someone else just recently (march 12, 2008) that says he installed snort and that it keeps entering and then leaving promiscuous mode. maybe check with snort mailing list of website?

---

### Post by pytheas22 on 2008-04-02
I haven't uninstalled anything yet or made any changes.  I think I am going to wait to see if eth0 goes promiscuous again; maybe then I can figure out which conditions seem to trigger it and be able to determine its legitimacy.

I would be really surprised if this box is compromised, as it's behind a pretty strong firewall, the system is less than two weeks old and I'm the only one who has touched (which means I'm pretty sure that I haven't done anything to expose it to intrusion, and I think I more or less know what I'm doing in terms of security).  Plus it's surrounded by Windows machines being used by people who don't necessarily know anything about security (i.e. corporate office workers), so you'd think they'd be the obvious targets before a Linux box.

Anyway, I'll post if I get any answers, and thanks for all the help.

---

### Post by The Cog on 2008-04-02
> **netlogic said:**
> do you know any IDS tools that don't want to listen to any traffic?

Yes - OSSEC HIDS. Read the manuals - it's a log analysis tool.

---

### Post by netlogic on 2008-04-02
You are right, but It also depends on how you define IDS.
The marketing term can even define anti-virus, screensavers, and malware detection as IDS.  There are many tools that don't listen to the traffic.

Anyway, I don't want to discuss what defines IDS. If we only go by the definition of acronyms, we can even say TPM is part of IDS if it is used conjunction with other applications.

---

### Post by The Cog on 2008-04-02
The point is - it's not OSSEC that's putting his interface into promiscuous mode. I dnon't know of any normal process that would do that.

---

### Post by netlogic on 2008-04-02
> **The Cog said:**
> The point is - it's not OSSEC that's putting his interface into promiscuous mode. I dnon't know of any normal process that would do that.

I took your advise and read the manual. The answer is snort.

---

### Post by pytheas22 on 2008-04-02
> I took your advise and read the manual. The answer is snort.

But snort is only supposed to monitor traffic coming to the machine on which it's installed.  Why would snort want to be in promiscuous mode?  And why only for a couple seconds?

---

### Post by netlogic on 2008-04-02
It is not a security risk to run in a promiscuous mode. If you don't run in a promiscuous mode, apply -p option. However, you will not able to monitor other devices. There is a certain case such as a standalone machine, it sounds logical to run with  a -p option.

I never had issues with going on/off. I have to assume it is something to do with the Ethernet card or driver.  Certain cards don't work well in a promiscuous mode.

---

