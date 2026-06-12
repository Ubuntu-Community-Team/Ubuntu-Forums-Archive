---
title: "Exclamation Logwatch handler seems to not work correctly"
date: 2022-08-11
forum: Server Platforms
---

### Post by Anquietas on 2022-08-11
Hello,

I have a wierd problem with Logwatch.

I've installed a VSFTPd server on my server machine for a few days now, because it is needed internally in our organization by some printers that can only scan to FTP folders.

The only time I got a report from Logwatch for the VSFTPD Service was today, when in fact, there is ongoing FTP activity for a few days now !

```

scpej-hga [/var/log] # date
Thu 11 Aug 2022 09:41:11 AM EEST

```

I've got a Report for August 10th, which is OK.
Logwatch is set up and vsftpd is loaded in the services sections of Logwatch.


**The issue is somewhat strange, and let me explain how:**

For a few days ago, I have constant activity in VSFTPD logs:

Here is a sample of logs for Aug 10th, Aug 9th, Aug 8th:
(the logfile also contains Downloads/Uploads, and so on, I only grepped "Connect" in order to shorten the Code Section in this post) - you get the ideea, I have valid logs, so no problems here.

```

scpej-hga [/var/log] # cat /var/log/vsftpd.log |grep "Aug 10" |grep -m 1 CONNECT
Wed Aug 10 09:10:26 2022 [pid 2066663] CONNECT: Client "XXX.XXX.XXX.XXX"
scpej-hga [/var/log] # cat /var/log/vsftpd.log |grep "Aug  9" |grep -m 1 CONNECT
Tue Aug  9 07:24:01 2022 [pid 1796243] CONNECT: Client "XXX.XXX.XXX.XXX"
scpej-hga [/var/log] # cat /var/log/vsftpd.log |grep "Aug  8" |grep -m 1 CONNECT
Mon Aug  8 05:51:05 2022 [pid 1527613] CONNECT: Client "XXX.XXX.XXX.XXX"

```

**Now, the problem is defined like this:**
I am curious WHY didn't Logwatch report me the activites Yesterday, and the day before, and so on...
(Logwatch is set to send me emails on a daily basis with "Range: Yesterday" and "Detail Level: Low")

I want to check if Logwatch did really see those activities in vsftpd.log a few days ago.

If I specify with range:
```

scpej-hga [/var/log] # logwatch --range "-2 days" --output stdout --service vsftpd
scpej-hga [/var/log] # logwatch --range "-3 days" --output stdout --service vsftpd
scpej-hga [/var/log] #

```
it gives me EMPTY content ! (so Logwatch doesn't seem to parse the logs correctly)

Reporting with "ALL" in Range, gives me all the logs, correctly, INCLUDING those missed by Logwatch for a few days now:

```

scpej-hga [/var/log] # logwatch --range "All" --output stdout --service vsftpd
 
 ################### Logwatch 7.5.2 (07/22/19) #################### 
        Processing Initiated: Thu Aug 11 09:38:35 2022
        Date Range Processed: all
        Detail Level of Output: 0
        Type of Output/Format: stdout / text
        Logfiles for Host: scpej-hga
 ################################################################## 
 
 --------------------- vsftpd-messages Begin ------------------------ 
 [HERE IS A TON OF INFORMATION, EVERYTHING IS CHECKED AND IS OK !]
 ---------------------- vsftpd-messages End ------------------------- 

 
 ###################### Logwatch End ######################### 


```
So this works perfectly !

I wonder why Logwatch doesn't report with "-X days" interval.

Also, I don't think that it's a problem with "-X days", since Yesterday, it should have reported for "it's Yesterday" which was, from today's point of view, "-2 days ago".
So it's not a SYNTAX problem.

It's rather that Logwatch doesn't seem to detect LOG activity in those days (Aug 8 and Aug 9) in normal "Yesterday" mode and also in specifying "-X days" parameters.

The only keyword that seems to be working is "All".

Anyone have a guess, or should I file a bug report ?...

God knows how many other logs did I miss...

Thank you !

---

### Post by LHammonds on 2022-08-12
For those familiar with LogWatch, it might be helpful to provide more information about what you are working with.

From the snippet of the log, Logwatch is version 7.5.2

What version of Ubuntu are you using?  What is the kernel version?  What version of vsftpd?

And since we are talking about a very-specific log, what are the log-specific options in your vsftpd.conf file that are responsible for populating what goes into your log file?

LHammonds

---

### Post by Anquietas on 2022-08-12
Ubuntu Server 20.04.4 LTS

Kernel: 5.4.0-122-generic

1. Logwatch.conf:

```

########################################################
# This was written and is maintained by:
#    Kirk Bauer <kirk@kaybee.org>
#
# Please send all comments, suggestions, bug reports,
#    etc, to kirk@kaybee.org.
#
########################################################

# NOTE:
#   All these options are the defaults if you run logwatch with no
#   command-line arguments.  You can override all of these on the
#   command-line.

# You can put comments anywhere you want to.  They are effective for the
# rest of the line.

# this is in the format of <name> = <value>.  Whitespace at the beginning
# and end of the lines is removed.  Whitespace before and after the = sign
# is removed.  Everything is case *insensitive*.

# Yes = True  = On  = 1
# No  = False = Off = 0

# Default Log Directory
# All log-files are assumed to be given relative to this directory.
LogDir = /var/log

# You can override the default temp directory (/tmp) here
TmpDir = /var/cache/logwatch

#Output/Format Options
#By default Logwatch will print to stdout in text with no encoding.
#To make email Default set Output = mail to save to file set Output = file
Output = stdout
#To make Html the default formatting Format = html
Format = text
#To make Base64 [aka uuencode] Encode = base64
Encode = none

# Input Encoding
# Logwatch assumes that the input is in UTF-8 encoding.  Defining CharEncoding
# will use iconv to convert text to the UTF-8 encoding.  Set CharEncoding
# to an empty string to use the default current locale.  If set to a valid
# encoding, the input characters are converted to UTF-8, discarding any
# illegal characters.  Valid encodings are as used by the iconv program,
# and `iconv -l` lists valid character set encodings.   
# Setting CharEncoding to UTF-8 simply discards illegal UTF-8 characters.
#CharEncoding = ""

# Default person to mail reports to.  Can be a local account or a
# complete email address.  Variable Output should be set to mail, or
# --output mail should be passed on command line to enable mail feature.
MailTo = root
# WHen using option --multiemail, it is possible to specify a different
# email recipient per host processed.  For example, to send the report
# for hostname host1 to user@example.com, use:
#Mailto_host1 = user@example.com
# Multiple recipients can be specified by separating them with a space.

# Default person to mail reports from.  Can be a local account or a
# complete email address.
MailFrom = Logwatch

# if set, the results will be saved in <filename> instead of mailed
# or displayed. Be sure to set Output = file also.
#Filename = /tmp/logwatch

# Use archives?  If set to 'Yes', the archives of logfiles
# (i.e. /var/log/messages.1 or /var/log/messages.1.gz) will
# be searched in addition to the /var/log/messages file.
# This usually will not do much if your range is set to just
# 'Yesterday' or 'Today'... it is probably best used with Range = All
# By default this is now set to Yes. To turn off Archives uncomment this.
#Archives = No

# The default time range for the report...
# The current choices are All, Today, Yesterday
Range = yesterday

# The default detail level for the report.
# This can either be Low, Med, High or a number.
# Low = 0
# Med = 5
# High = 10
Detail = Low


# The 'Service' option expects either the name of a filter
# (in /usr/share/logwatch/scripts/services/*) or 'All'.
# The default service(s) to report on.  This should be left as All for
# most people.
Service = All
# You can also disable certain services (when specifying all)
Service = "-zz-network"     # Prevents execution of zz-network service, which
                            # prints useful network configuration info.
Service = "-zz-sys"         # Prevents execution of zz-sys service, which
                            # prints useful system configuration info.
Service = "-eximstats"      # Prevents execution of eximstats service, which
                            # is a wrapper for the eximstats program.
# If you only cared about FTP messages, you could use these 2 lines
# instead of the above:
#Service = ftpd-messages   # Processes ftpd messages in /var/log/messages
#Service = ftpd-xferlog    # Processes ftpd messages in /var/log/xferlog
# Maybe you only wanted reports on PAM messages, then you would use:
#Service = pam_pwdb        # PAM_pwdb messages - usually quite a bit
#Service = pam             # General PAM messages... usually not many

# You can also choose to use the 'LogFile' option.  This will cause
# logwatch to only analyze that one logfile.. for example:
#LogFile = messages
# will process /var/log/messages.  This will run all the filters that
# process that logfile.  This option is probably not too useful to
# most people.  Setting 'Service' to 'All' above analyzes all LogFiles
# anyways...

#
# By default we assume that all Unix systems have sendmail or a sendmail-like MTA.
# The mailer code prints a header with To: From: and Subject:.
# At this point you can change the mailer to anything that can handle this output
# stream.
# TODO test variables in the mailer string to see if the To/From/Subject can be set
# From here with out breaking anything. This would allow mail/mailx/nail etc..... -mgt
mailer = "/usr/sbin/sendmail -t"

#
# With this option set to a comma separated list of hostnames, only log entries
# for these particular hosts will be processed.  This can allow a log host to
# process only its own logs, or Logwatch can be run once per a set of hosts
# included in the logfiles.
# Example: HostLimit = hosta,hostb,myhost
#
# The default is to report on all log entries, regardless of its source host.
# Note that some logfiles do not include host information and will not be
# influenced by this setting.
#
#HostLimit = myhost

#
# By default /var/adm is searched after LogDir.
#AppendVarAdmToLogDirs = 1

#
# By default /var/log is to be searched after LogDir and /var/adm/ .
#AppendVarLogToLogDirs = 1

#
# By default the current working directory is searched last after LogDir, /var/adm/, and /var/log/ .
#AppendCWDToLogDirs = 1

# vi: shiftwidth=3 tabstop=3 et

```

2. There are no error messages

3. Specifying Range=Yesterday and Range=Today works fine.

4. Because today is another day (Aug 12th), now, specifying "-2 days" also works. But specifying "-3 days" still doesn't work.

Basically, it's NOT a problem with the Syntax or with the ranges ! No problem with "-X days" or with "yesterday" or with "today".
The problem is that Logwatch doesn't pick up logs for a specific day, EVEN IF those logs are present in "vsftpd.conf" !

An example for today:

My vsftpd.log starts on Aug 8th:
```

scpej-hga [~] # head -3 /var/log/vsftpd.log
Mon Aug  8 05:51:05 2022 [pid 1527613] CONNECT: Client "192.168.1.182"
Mon Aug  8 05:51:05 2022 [pid 1527612] [scanhe] OK LOGIN: Client "192.168.1.182"
Mon Aug  8 05:51:05 2022 [pid 1527614] [scanhe] FAIL DOWNLOAD: Client "192.168.1.182", "/20220808043919693.pdf", 0.00Kbyte/sec
scpej-hga [~] #

```
So, normally, logwatch should pick up Aug 8, right ?

Doing interogation on Logwatch, as per following:
```

scpej-hga [~] # logwatch --range 'today' --output stdout --service vsftpd |head -10
 
 ################### Logwatch 7.5.2 (07/22/19) #################### 
        Processing Initiated: Fri Aug 12 10:29:45 2022
        Date Range Processed: today
                              ( 2022-Aug-12 )
                              Period is day.
        Detail Level of Output: 0
        Type of Output/Format: stdout / text
        Logfiles for Host: scpej-hga
 ################################################################## 
scpej-hga [~] # logwatch --range 'yesterday' --output stdout --service vsftpd |head -10
 
 ################### Logwatch 7.5.2 (07/22/19) #################### 
        Processing Initiated: Fri Aug 12 10:29:54 2022
        Date Range Processed: yesterday
                              ( 2022-Aug-11 )
                              Period is day.
        Detail Level of Output: 0
        Type of Output/Format: stdout / text
        Logfiles for Host: scpej-hga
 ################################################################## 
scpej-hga [~] # logwatch --range '-1 days' --output stdout --service vsftpd |head -10
 
 ################### Logwatch 7.5.2 (07/22/19) #################### 
        Processing Initiated: Fri Aug 12 10:30:00 2022
        Date Range Processed: -1 days
                              ( 2022-Aug-11 )
                              Period is day.
        Detail Level of Output: 0
        Type of Output/Format: stdout / text
        Logfiles for Host: scpej-hga
 ################################################################## 
scpej-hga [~] # logwatch --range '-2 days' --output stdout --service vsftpd |head -10
 
 ################### Logwatch 7.5.2 (07/22/19) #################### 
        Processing Initiated: Fri Aug 12 10:30:07 2022
        Date Range Processed: -2 days
                              ( 2022-Aug-10 )
                              Period is day.
        Detail Level of Output: 0
        Type of Output/Format: stdout / text
        Logfiles for Host: scpej-hga
 ################################################################## 
scpej-hga [~] # logwatch --range '-3 days' --output stdout --service vsftpd |head -10
scpej-hga [~] # logwatch --range '-4 days' --output stdout --service vsftpd |head -10
scpej-hga [~] #

```

-3 days would have been 2022-Aug-09
-4 days would have been 2022-Aug-08

No report from Logwatch for those days !
Even if I have logs for those days !:

```

scpej-hga [~] # cat /var/log/vsftpd.log |grep "Aug  8" |head -1
Mon Aug  8 05:51:05 2022 [pid 1527613] CONNECT: Client "192.168.1.182"
scpej-hga [~] # cat /var/log/vsftpd.log |grep "Aug  9" |head -1
Tue Aug  9 07:24:01 2022 [pid 1796243] CONNECT: Client "192.168.1.55"
scpej-hga [~] # cat /var/log/vsftpd.log |grep "Aug 10" |head -1
Wed Aug 10 09:10:26 2022 [pid 2066663] CONNECT: Client "192.168.1.110"
scpej-hga [~] # cat /var/log/vsftpd.log |grep "Aug 11" |head -1
Thu Aug 11 05:39:04 2022 [pid 2273949] CONNECT: Client "192.168.1.173"
scpej-hga [~] # cat /var/log/vsftpd.log |grep "Aug 12" |head -1
Fri Aug 12 08:38:41 2022 [pid 2570774] CONNECT: Client "192.168.1.166"
scpej-hga [~] #

```

However, if I issue the command:
```

logwatch --range 'all' --output stdout --service vsftpd

```
It reports everything !

I really hope I have explained it all to the best of my abilities...

---

### Post by LHammonds on 2022-08-12
> **Anquietas said:**
> I really hope I have explained it all to the best of my abilities...You were clear about the symptoms.  This is clearly not a user-training issue.  Software bugs need to be replicated and for anyone trying to help you, the situation needs to be replicated which typically means the exact same software...starting with logwatch in this case and what it is manipulating....vsftpd logs...which are configurable in the .conf file.   Knowing the OS version and kernel can also be helpful especially if you simply installed everything via official repositories.

For informational purposes, ***apt search*** shows the following in official repositories:
 * Ubuntu Server 18.04.6 LTS - LogWatch 7.4.3 and vsftpd 3.0.3
 * Ubuntu Server 20.04.4 LTS - LogWatch 7.5.2 and vsftpd 3.0.3
 * Ubuntu Server 22.04.1 LTS - LogWatch 7.5.6 and vsftpd 3.0.5

I don't use logwatch and no longer have a vsftpd server so I'm not gonna be much help but hopefully there won't need to be anything else posted for clarification to get help from those that can.

LHammonds

---

### Post by Anquietas on 2022-08-12
```

scpej-hga [~] # logwatch --version
Logwatch 7.5.2 (released 07/22/19)
scpej-hga [~] # vsftpd -v
vsftpd: version 3.0.3

```

These are my versions.

---

