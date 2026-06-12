---
title: "Antimalare tools for Ubuntu Server"
date: 2010-09-29
forum: Server Platforms
---

### Post by Vegan on 2010-09-29
So what options are there for Ubuntu Server for security?

---

### Post by sinclair86 on 2010-09-30
id like to piggy back on this as well because i maintain an email server for my job and my bo9ss like to open everything. needless to say im tired of cleaning up his computer. clamav doesnt really seem to do much....

---

### Post by SeijiSensei on 2010-09-30
> **sinclair86 said:**
> id like to piggy back on this as well because i maintain an email server for my job and my bo9ss like to open everything. needless to say im tired of cleaning up his computer. clamav doesnt really seem to do much....

I recommend [MailScanner]("http://www.mailscanner.info/"), a wonderful perl application that manages virus and spam scanning for you.  You can install it from the repositories.  

I've scanned literally thousands upon thousands of email messages using MailScanner with ClamAV as the virus scanner.  (It also supports the gamut of commercial virus scanners.)  It's been very effective at keeping viruses out of my clients' networks.  MailScanner gives you a lot of options for blocking messages for other reasons as well.  It also can invoke spamassassin and process messages based on the score SA returns.

One growing problem is emails that point to off-site links that download infections to Windows.  (Messages offering access to alleged nude celebrity photos are a common enticement.)  Virus scanners can do little about this infection vector since there's no payload in the message to scan.  If you want to protect against things like this, you need to install something like the Squid web proxy on a Linux firewall and use Squid's rules to block downloads of executables from the Internet.  

As for the OP, are you concerned about malware for Linux?  That's not really a serious problem yet.  I've run Internet-facing Linux servers for over a decade and had just one instance where someone exploited a hole in Apache 1.1 and started an IRC relay on my server.  (As much my fault because I was behind on security updates.)  Most of the key server applications like BIND, Apache, sendmail, postfix, and the like have been progressively hardened against exploits over the years.  The types of malware common to Windows computers like viruses and worms have little traction in the Linux space. 

Things may change as Linux usage becomes more widespread, but it's not really a major concern at the moment.

---

### Post by Vegan on 2010-09-30
I am using the command like only server of Ubuntu. So I was inquiring about options for that interface.

---

