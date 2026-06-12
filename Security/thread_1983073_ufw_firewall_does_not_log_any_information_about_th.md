---
title: "ufw firewall does not log any information about the network traffic."
date: 2012-05-19
forum: Security
---

### Post by kleenex on 2012-05-19
Hello, ufw firewall does not log any information about network traffic, blocked packets, etc., ufw seems to not have the capability to log network activity. Of course I turned on ufw logging options using the **[COLOR=SeaGreen]ufw logging on[/COLOR]** command and set the log level to **[COLOR=SeaGreen]high[/COLOR]**. I wrote a few rules with using e.g. [COLOR=SeaGreen]**ufw default deny**[/COLOR] command etc. The rest of the rules I put to the **/etc/apt/before.rule** file. Because I am still using iptables, ufw does not have too many rules, because ufw is only for testing purposes.   I thought, that maybe some informations will be included in **/var/log/message** file, but there is not such file. I am using Xubuntu 12.04 LTS with latest 3.2.0-24-generic kernel and ufw 0.31.1-1 version.

---

### Post by darkod on 2012-05-19
Did you check /var/log/ufw.log?

---

### Post by Ms. Daisy on 2012-05-20
I have to ask, did you enable ufw?

```
sudo ufw enable
```

---

### Post by kleenex on 2012-05-20
Hi *Ms. Daisy*, of course, I turned on **ufw**! It was the first thing, which I did when I decided to use this firewall. *Darkod* - I forgot to mention in my first post, that **/var/log/ufw.log** file is empty and still is.

---

### Post by Doug S on 2012-05-20
Yes in 12.04 there is no longer a default /var/log/messages file.
You would find iptables log entries in /var/log/syslog, by default.
 
Have a look at your resulting iptables with:```
sudo iptables-save -c

``` and see if there are any LOG entries. Example:```
[1203:68676] -A INPUT -i eth1 -m recent --update --seconds 5400 --hitcount 3 --name BADGUY_SSH --rsource -j LOG --log-prefix "SSH BAD:" --log-level 6
```I should have 1203 log entries from this iptables line (but not all are from today, and so would not appear in todays syslog file). Example (from yesterday, no entries so far today):```
doug@doug-64:~$ grep "SSH BAD" /var/log/syslog.1
May 19 09:03:49 doug-64 kernel: [3255329.378878] SSH BAD:IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:00:90:1a:a0:fd:73:08:00 SRC=117.135.160.172 DST=209.121.28.192 LEN=60 TOS=0x00 PREC=0x00 TTL=45 ID=12150 DF PROTO=TCP SPT=60544 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0
May 19 09:03:52 doug-64 kernel: [3255332.378221] SSH BAD:IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:00:90:1a:a0:fd:73:08:00 SRC=117.135.160.172 DST=209.121.28.192 LEN=60 TOS=0x00 PREC=0x00 TTL=45 ID=12151 DF PROTO=TCP SPT=60544 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0
May 19 09:03:58 doug-64 kernel: [3255338.378629] SSH BAD:IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:00:90:1a:a0:fd:73:08:00 SRC=117.135.160.172 DST=209.121.28.192 LEN=60 TOS=0x00 PREC=0x00 TTL=45 ID=12152 DF PROTO=TCP SPT=60544 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0
May 19 11:50:55 doug-64 kernel: [3265355.543270] SSH BAD:IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:00:90:1a:a0:fd:73:08:00 SRC=211.154.164.197 DST=209.121.28.192 LEN=60 TOS=0x00 PREC=0x00 TTL=49 ID=61572 DF PROTO=TCP SPT=42120 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0

```

---

### Post by darkod on 2012-05-20
And what about the /var/log/ufw.log Doug? Why would that be empty?

The OP says ufw is enabled which would take precedence over raw iptables. Yes, ufw is only a front end for iptables but once enabled the log file should be there. Not?

---

### Post by Doug S on 2012-05-20
> **darkod said:**
> And what about the /var/log/ufw.log Doug? Why would that be empty?
 
The OP says ufw is enabled which would take precedence over raw iptables. Yes, ufw is only a front end for iptables but once enabled the log file should be there. Not?
 
I have no clue, as I never use ufw, I only use iptables. I assumed, perhaps incorrectly, that ufw.log was for ufw execution issues or whatever.
I still recommend to look for actual "LOG" commands in the resulting iptables so as to know what to expect in the log file, whatever its name or location might be.

---

### Post by kleenex on 2012-05-21
[QUOTE=Doug S]You would find iptables log entries in /var/log/syslog, by default.
 [/QUOTE]

This file is also empty:

```
[COLOR=Blue]kleenex@[COLOR=Lime]S[/COLOR][/COLOR][COLOR=Lime]2H>[/COLOR] [COLOR=Black]sudo tail -f /var/log/syslog[/COLOR]
[COLOR=Blue]kleenex@[/COLOR][COLOR=Lime]S2H>
[/COLOR][COLOR=Blue]kleenex@[/COLOR][COLOR=Lime]S2H> [/COLOR][COLOR=Black]sudo cat /var/log/syslog
[/COLOR][COLOR=Blue]kleenex@[/COLOR][COLOR=Lime]S2H>[/COLOR]
```I can not find any **ufw** or **iptables** logs. That's strange.   **sudo iptables-save -c **shows **iptables** and **ufw** rules and it is similar to yours example *Doug S.*

---

### Post by Ms. Daisy on 2012-05-21
OK, something is amok if your syslog and ufw logs are truly empty.  Try listing the logs in /var/log, see what's in there and if any of them logged any information.

You could also try Log File Viewer, which is a GUI to view all the logs on your system.

---

### Post by SparTacux on 2012-05-21
I hacked you Kleenex.  Mr stealth they call me - left without a trace. The US Government don't call me the Fox for nothing ;-)

---

### Post by kleenex on 2012-05-21
OK* Ms. Daisy,*  so that is what /var/log/ directory looks like, with logs files[I];
[/I]```
[COLOR=Blue]kleenex@[/COLOR][COLOR=Lime]S2H> [/COLOR]ls /var/log/*.log
/var/log/alternatives.log  /var/log/boot.log       /var/log/dpkg.log        /var/log/kern.log          /var/log/ufw.log
/var/log/apport.log        /var/log/bootstrap.log  /var/log/fontconfig.log  /var/log/mail.log          /var/log/Xorg.0.log
/var/log/auth.log          /var/log/diskfree.log   /var/log/jockey.log      /var/log/pm-powersave.log

```Looks like a standard.  What is the best program for viewing the logs, but graphically? I can not find something like Log File Viewer or I'm blind ;-)
*SparTacux* I don't quite understand what you mean, really I don't. Should I be afraid?

---

### Post by darkod on 2012-05-21
So, you are sure the ufw.log is empty?

If you simply try to view it in terminal with:
cat /var/log/ufw.log

Does it show anything?

---

### Post by kleenex on 2012-05-22
Yes *darkod, ***ufw.log** file is still empty. Any attempt to display the contents of this file in a terminal, also shows nothing. I have no idea why this is happening. At this moment I cannot look up **iptables **and **ufw** logs.

---

### Post by Ms. Daisy on 2012-05-22
OK, let's do this Kleenex: ```
sudo ufw status
``` please post the output.

---

### Post by Soul-Sing on 2012-05-23
> **Ms. Daisy said:**
> OK, let's do this Kleenex: ```
sudo ufw status
``` please post the output.

When the status is =active=, please:
```
sudo ufw logging on
```

To monitor network activity better use tcpdump/wireshark.

---

### Post by SparTacux on 2012-05-23
> **kleenex said:**
> OK* Ms. Daisy,*  so that is what /var/log/ directory looks like, with logs files[I];
[/I]```
[COLOR=Blue]kleenex@[/COLOR][COLOR=Lime]S2H> [/COLOR]ls /var/log/*.log
/var/log/alternatives.log  /var/log/boot.log       /var/log/dpkg.log        /var/log/kern.log          /var/log/ufw.log
/var/log/apport.log        /var/log/bootstrap.log  /var/log/fontconfig.log  /var/log/mail.log          /var/log/Xorg.0.log
/var/log/auth.log          /var/log/diskfree.log   /var/log/jockey.log      /var/log/pm-powersave.log

```Looks like a standard.  What is the best program for viewing the logs, but graphically? I can not find something like Log File Viewer or I'm blind ;-)
*SparTacux* I don't quite understand what you mean, really I don't. Should I be afraid?

No Kleenex - just having fun - I'm in a very good mood :-)

Looking at the files above - your ufw.log file is there. Try opening it up with gedit: gedit ufw.log

If the file is empty then nothing is being logged. By default logging could be  set to low so that only blocked traffic is being logged and maybe no blocked traffic conditions have arisen yet. You have set some UFW Firewall rules haven't you? 

Other than that I'd be checking if you haven't been playing around with any of the system configuration files to do with controlling the LOG files such as /etc/rsyslog.d/50-default.conf and /etc/rsyslog.d/20-ufw.conf. Also check /etc/rsyslog.conf. All these files can control the logs in UFW.

---

### Post by jmore9 on 2012-05-23
I just ran gedit /var/log/ufw.log from terminal and it brought up the firewall log.  I have never turned on any logging it must have been done by ubuntu.  

Don't know if that helps or not.

---

### Post by darkod on 2012-05-23
> **jmore9 said:**
> I just ran gedit /var/log/ufw.log from terminal and it brought up the firewall log.  I have never turned on any logging it must have been done by ubuntu.  

Don't know if that helps or not.

If you have enabled ufw, logging is on by default with level LOW, which means it logs only BLOCKED traffic.

If ufw has never been enabled, I guess the log file should be empty, if it exists at all.

---

### Post by kleenex on 2012-05-23
*Ms. Daisy - ***ufw** status is marked as [COLOR=SeaGreen]active[/COLOR]. 
[I]
leoquant [/I]- as I already mentioned, I turned on logging with [COLOR=SeaGreen]HIGH[/COLOR] level after enabling **ufw** (after starting using **ufw** firewall, a couple days ago).
[I]
SparTacux [/I]-** /etc/rsyslog.d/20-ufw.conf **file contains an option for Log kernel generated UFW log messages to **/var/log/ufw.log** file. **/etc/rsyslog.d/50-default.conf **and **/etc/rsyslog.conf** files does not contain anything special for **ufw**. I think that turning on of the **ufw** logging (with [COLOR=SeaGreen]HIGH[/COLOR] level) should be sufficient. Also, I open the **ufw.log** file many times using e.g. leafpad - and is empty.

---

### Post by kleenex on 2012-06-10
Hi, sorry for double posts, but it gets even worse! At this point there is not even a **/var/log/ufw.log** file. A few days ago, I used a bleachbit application for general cleaning of the system - mainly logs, but so far (3 days after) the **ufw.log** file still did not appear. At this point in the **/var/log** directory is 5 logs files;

```
[COLOR=Blue]kleenex@[/COLOR][COLOR=Lime]SH2 >[/COLOR] ls /var/log/*.log
/var/log/alternatives.log  /var/log/dpkg.log          /var/log/Xorg.0.log
/var/log/boot.log          /var/log/pm-powersave.log
```There is not even the **syslog** file where I should be able to find **iptables** log entries. I have no idea what is happening. The only information related to the **ufw** log I found by filtering the output of [COLOR=SeaGreen]dmesg[/COLOR] command with [COLOR=SeaGreen]grep[/COLOR] utility.

```
[COLOR=Blue]kleenex@[/COLOR][COLOR=Lime]SH2 >[/COLOR] dmesg |grep UFW
[   19.936079] [UFW ALLOW] IN= OUT=eth0 SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=:0000:0000:0000:0000:0000:0000:0016 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=143 CODE=0 
[   98.976201] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0001 DST=0000:0000:0000:0000:0000:0000:0000:0001 LEN=68 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=44304 DPT=4101 WINDOW=32752 RES=0x00 SYN URGP=0 
```For **UFW ALLOW** there is a couple of entries, but I can not find anything for **iptables**, which generally I am using all the time. Maybe I should report a bug? 

Here are the steps that I took to make use of **ufw** firewall:

[LIST=1]
[*]Setting the default mode of **ufw **to Deny
[*]Enabling ufw ([COLOR=SeaGreen]sudo ufw enable[/COLOR] command)
[*]Adding some simple rules via terminal and **/etc/ufw/before.rules** file etc.
[*]Enabling logging with [COLOR=SeaGreen]sudo ufw logging on[/COLOR] command
[*]Setting logging level to [COLOR=SeaGreen]High[/COLOR]
[*][COLOR=SeaGreen][COLOR=Black]Checking **ufw** status ([/COLOR][/COLOR]status is marked as [COLOR=SeaGreen]active[/COLOR])
[/LIST]
That is all.

---

### Post by darkod on 2012-06-10
After you make changes to the /etc/ufw/before.rules you need to do ufw disable && ufw enable so that the changes take effect. Or restart the machine.

Not that it matters for logging, but just to mention it.

And since you are using ufw, I don't think you will find any entry in the logs for iptables, only for ufw. Besides, I don't think the iptables entries have 'iptables' in them by default, you need to configure it yourself if you want to use their logging. But none of this applies when ufw is used I think.

---

### Post by kleenex on 2012-06-11
Hi **darkod**, of course after make any changes in the **before.conf** file I disabled and enabled **ufw** again. Also machine was restarted many times.
[quote=darkod](...)iptables entries have 'iptables' in them by default, you need to configure it yourself if you want to use their logging(...)[/quote]
Honestly, do not quite understand what you mean. Do you mean the rules for **iptables**, which are responsible for logging? Besides logging for individual rules, I also have these rules, but probably it is not what you meant;
```
iptables -A INPUT -j LOG
iptables -A FORWARD -j LOG
```

---

### Post by kleenex on 2012-06-24
OK, problem solved. Log file for the **ufw** firewall is now full of information. Became apparent that some time ago, I edited the **/etc/init/rsyslog.conf** file and set **#** before these two options:
```
start on filesystem
stop on runlevel [06]
```So it was not possible to log anything what was related to **ufw** firewall. After restart everything was okay.  I just forget about this, because some time ago I tested some management services by editing the files in the **/etc/init/** directory. That's all.

---

### Post by SparTacux on 2012-06-29
> **kleenex said:**
> OK, problem solved. Log file for the **ufw** firewall is now full of information. Became apparent that some time ago, I edited the **/etc/init/rsyslog.conf** file and set **#** before these two options:
```
start on filesystem
stop on runlevel [06]
```So it was not possible to log anything what was related to **ufw** firewall. After restart everything was okay.  I just forget about this, because some time ago I tested some management services by editing the files in the **/etc/init/** directory. That's all.

Sounds good to me. I did give you advice to check that file on the 23rd May ;-)

......

Other than that I'd be checking if you haven't been playing around with  any of the system configuration files to do with controlling the LOG  files such as /etc/rsyslog.d/50-default.conf and  /etc/rsyslog.d/20-ufw.conf. Also check /etc/rsyslog.conf. All these  files can control the logs in UFW.

---

### Post by SparTacux on 2012-06-29
The only problem with UFW logs is that that UFW logs the Firewall audit data to a number of files such as syslog, kern, messages and ufw.log. This can make those other files hard to read. I created a nice little configuration file to direct UFW to only log to ufw.log. It also created a separate browser log for logging internet browsing activity and a second log file for logging just blocked traffic. Replace /etc/rsyslog.d/20-ufw.conf with the following file:

#****************************************************#
#       LOG BROWSER TRAFFIC USING GUFW             
#                                                   
# ALSO STOPS UFW LOGS GOING TO SYSLOG, MESSAGES AND  
# KERNAL LOGS. IT CREATES ANOTHER LOG FILE FOR    
# VIEWING BLOCKED TRAFFIC AND IGNORES UFW AUDIT DATA 
#                                                    
#****************************************************#
    
# LOG UFW BLOCKED TRAFFIC TO SEPARATE LOG FILE 
:msg ,contains, "UFW BLOCK" /var/log/ufwblocks.log

# LOG HTTP 80 AND HTTPS 443 TO SEPARATE BROWSER LOG 
:msg, regex, "UFW ALLOW.*DPT=80" /var/log/ufwbrowser.log
:msg, regex, "UFW ALLOW.*DPT=443" /var/log/ufwbrowser.log

# DON'T WRITE AUDIT DATA TO UFW LOGS 
:msg ,contains, "UFW AUDIT" ~
&~

#KEEP UFW DATA TO UFW LOGS ONLY
:msg ,contains, "[UFW" /var/log/ufw.log
&~

#****************************************************
#                   NOTES                       
#                                                    
# This file replaces  /etc/rsyslog.d/20-default.conf 
#          and handles all UFW data.                 
#                                   
# IF USING GUFW TO ADD YOUR OWN FIREWALL RULES THEN  
# MAKE SURE YOU SET EACH RULE TO LOG ITS OUTPUT BY   
# SELECTING THE ADVANCED RULE OPTIONS AND SELECTING  
# SHOW EXTENDED ACTIONS.                             
#                                                    
# ALSO SET GUFW LOG LEVELS TO HIGH OR FULL ( GUFW    
# PREFERENCES ) TO GET THE BEST OUT OF THIS UFW      
# UTILITY. YOU CAN OPEN "ufwbrowser.log" AND         
# "ufwblocks.log" WITH UBUNTU'S LOG FILE VIEWER                 
#                                                    
#****************************************************#

---

### Post by kleenex on 2012-07-13
Hello, again, unfortunately, [COLOR=Green]ufw[/COLOR] does not log anything. [COLOR=Green]ufw.log[/COLOR] file is empty. [COLOR=Blue]@[/COLOR][COLOR=Blue]SparTacux    [COLOR=Black]I must try Your way. [/COLOR][/COLOR]Thank You for creating this file. I hope this helps. 

An interesting fact: When I shut off the [COLOR=Green]ufw[/COLOR] firewall, [COLOR=Green]iptables[/COLOR] default policy for [COLOR=Purple]INPUT[/COLOR] and [COLOR=Purple]FORWARD[/COLOR] chains changed to **[COLOR=Black]Accept[/COLOR]**, which is pretty strange, because I wrote default policy for these two chains to **[COLOR=Black]Drop[/COLOR]**. Other rules in these chains have not changed. After enabling [COLOR=Green]ufw[/COLOR], everything returned to normal.

Really have no idea why there are such problems with [COLOR=Green]ufw[/COLOR] and logging.

---

