---
title: "help please is this a chkrootkit false positive - bindshell - not geek enough"
date: 2013-08-21
forum: Security
---

### Post by a-you on 2013-08-21
Hi all

chkrootkit is reporting for the first time ever something "INFECTED". Rkhunter is I believe saying that all is basically well. I have been searching the interwebs all morning and to me it *appears* to be a flase positive, but I'm not at all geek enough to really know. Can you please help clear this up?? (THANKS in advance)

I'll try to be brief, but the circumstances are a bit complicated:
I have a script that runs daily via anacron, which I have running after chkrootkit and rkhunter, which checks the chkrootkit log, which I have configured to report differences day to day (that is, my script checks the logs of chkrootkit and rkhunter instead of those emailing results to me); I *THINK* that yesterday NO issues were reported, though it is possible that it reported something and I didn't see it---I'm sorry but it would be a long story to explain why that is not certain, and I'm leary of making this long winded (tell me if you want the details). *But* last night I also happened to run "Software Updater", and so after that I updated rkhunter's DB by running rkhunter --propupd. 

Here I think I should interrupt this narative and show what's going on:

This from chkrootkit:
```
Checking `bindshell'...      INFECTED (PORTS:  4000)

```
Abridged output of chkroot -x showing the only lines that contained "4000":
```
### Output of: /bin/netstat -an
###
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
...
udp        0      0 0.0.0.0:4000            0.0.0.0:*                          
...
```


More info:
```
$ sudo netstat -pan|grep 4000
udp        0      0 0.0.0.0:4000            0.0.0.0:*                           3044/dhclient   
```

```
$ sudo lsof -i:4000
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
dhclient 3044 root   20u  IPv4  17802      0t0  UDP *:4000 
```

```
$ ps -F -p 3044
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
root      3044  1153  0  2548  3704   2 10:33 ?        00:00:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-eth1.pid -lf /var/lib/dhcp/dhclient-54df5c86-b0d6-46f4-9189-af6493b1be73-eth1.lease -cf /var/run/nm-dhclient-eth1.conf eth1
```


In case it's helpful here are lines excerpted from rkhunter's log running it just now (note that rkhunter --propupd was done last night so if something was compromised then it might not be showing it):
```
...
[13:07:28] Info: Starting test name 'deleted_files'
[13:07:30]   Checking running processes for deleted files    [ Warning ]
[13:07:30] Warning: The following processes are using deleted files:
[13:07:30]          Process: /sbin/init    PID: 1    File: /var/log/upstart/dbus.log.1
[13:07:30]          Process: /usr/bin/nautilus    PID: 24620    File: /home/samashley/.local/share/gvfs-metadata/home
...
[13:07:49]   Performing check for sniffer log files
[13:07:49]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[13:07:49]     Checking for file '/dev/prom/sn.l'            [ Not found ]
[13:07:49]     Checking for file '/dev/fd/.88/zxsniff.log'   [ Not found ]
[13:07:49]   Checking for sniffer log files                  [ None found ]
...
[13:07:49] Info: Starting test name 'trojans'
[13:07:49] Performing trojan specific checks
[13:07:49] Info: Using inetd configuration file '/etc/inetd.conf'
[13:07:49] Info: Found service 'imap': it is inetd whitelisted.
[13:07:49] Info: Found service 'pop3': it is inetd whitelisted.
[13:07:49]   Checking for enabled inetd services             [ OK ]
...
[13:08:03] Info: Starting test name 'packet_cap_apps'
[13:08:03]   Checking for packet capturing applications      [ Warning ]
[13:08:03] Warning: Process '/sbin/dhclient' (PID 3044) is listening on the network.
...
```


...Today I ran:
```
dpkg -S
```
and it reported several packages installed on my system that contained dhclient (do you want me to list them?)
Next I ran debsums on each of those packages and for each thing contained therein it returned "OK".

Is there anything else I should post? Thanks a lot for any help!!

Oops, edited because I almost forgot to say: this is a laptop running Ubuntu Studio 12.10 quantal 64 bit. I do have quite a few packages installed, and have lost track of which might conceivably be "listening" but I also have ufw and gufw and have installed some firewall rules that I got from a post somewhere in these forums (have forgotten exactly where), mainly I've tried to block most incoming traffic except what I use but don't block outgoing. In case it's important: I have to connect to the interwebs via a USB dongle broadband device (aka "surf stick").

---

### Post by a-you on 2013-08-21
bump...???

I realize the post was long; sorry. But if anybody knows I'd seriously appreciate it (thanks)

---

### Post by samiux on 2013-08-21
@a-you,

Don't worry, it is false positive.

Do you run ICQ or alike at your box?  If yes, it is normal.

Samiux

---

### Post by a-you on 2013-08-22
Whew. Thanks. Actually I don't have ICQ, nor other messaging app, but I do have various apps installed, probably too many.

I had searched for hours and come to the conclusion that it was most likely not a problem, but I had also read that rootkits often work by substituting a modified binary for some standard tool, and that's where I got stuck: I don't know enough to tell whether what dhclient is doing is what it's supposed to do, or whether it might be doing something else. So I thought it would be nice to have the opinion of somebody that was expert enough to know that. So thanks really a lot.

---

### Post by unspawn on 2013-08-24
IMHO you don't even have to launch into a treatise about raw sockets, broadcasting and such but saying "don't worry" without posting methods for an OP to verify things is not ever good. See ```
lsof -Pwlnp `pgrep dhclient` -ai
``` for port / process / user details, verify package contents against those from a trusted repo if unsure, check your distros bug tracker for similar or related bugs and maybe patch it with a white list ([https://www.linuxquestions.org/questions/blog/unspawn-2450/chkrootkit-0-49-modifications-and-notes-2531/](https://www.linuxquestions.org/questions/blog/unspawn-2450/chkrootkit-0-49-modifications-and-notes-2531/)). BTW in the case of ICQ its web site lists UDP port usage as "5190 and up" (5190-5200).

---

### Post by a-you on 2013-08-25
Thanks unspawn for that info. At this point there are no "INFECTED" warnings; I'd assume that's good, though best would be if I knew exactly why/why not. Anyway at this moment too
```
 lsof -Pwlnp `pgrep dhclient` -ai
```
is not returning anything at all. I'm not sure if that's good, but I doubt it's bad. I'll assume it's fine unless I hear otherwise from you or others here. Anyway thanks really a lot to you and to samiux.

I did try to verify the contents of relevant packages by doing
```
 dpkg -S
```
to determine which contained "dhclient", and then checking those with debsums.

---

### Post by a-you on 2013-08-25
Oh damn. Now again I don't know if I should be worrying, because I just ran across this:

"Quote:
This utility [bindshell] allows users to open an interactive shell over a port, bypassing all system logging, thus making it possible for users to stealthy administer a machine.

Because of the mere definition of this, and the function of this, you can't trust ANY of the system binaries at this point. Bindshell does just what it's supposed to do, it provides a shell for users to do whatever they want with your system, INCLUDING replacing system binaries and the like.

The not so good part to this is this also can be run as a perl script, which means it doesn't ALWAYS have to listen to the port, it can simply listen to the port when the end user calls this."

This is nutty. If only I had a better idea of what to look for...

As I posted just above I *did* try to verify the packages that contained "dhclient" anywhere in them, and they checked out fine according to debsums. A real paranoid worry would be that this can be faked somehow, and the quote I pasted above mentions that it doesn't always have to be listening. So the tip from unspawn
```
lsof -Pwlnp `pgrep dhclient` -ai
```
would be then presumably also not be able to give useful results at the moment(??)

If any experts (including unspawn and/or samiux) might care to comment, and to explain why it's a false positive (assuming it is that) I'd much appreciate it! At the very least it would be nice to learn something new :-)

---

### Post by unspawn on 2013-08-25
> **a-you said:**
> As I posted just above I *did* try to verify the packages that contained "dhclient" anywhere in them, and they checked out fine according to debsums.  
If the state of the system isn't known, if security was lax to begin with, if there's tell-tale signs of a breach of security or if you're generally speaking unsure that what you see is what you run you can always boot a Live CD and then check hashes. 


> **a-you said:**
> A real paranoid worry would be that this can be faked somehow, and 
Hashes are generated by debsums locally and after package installation. Still subverting a system requires recon and a point of entry be it physical access, a service with weak authentication or vulnerable web stack application. Often that'll leave traces, like replacing an item in /bin or /sbin requires action and root privileges, so IMHO this isn't about paranoia but about allaying fears by knowing how the system works and knowing how to verify system integrity.


> **a-you said:**
> the quote I pasted above mentions that it doesn't always have to be listening. So the tip from unspawn
```
lsof -Pwlnp `pgrep dhclient` -ai
```
would be then presumably also not be able to give useful results at the moment(??)
There's two things: talking and doing. Talking *about* an issue gets you opinions and speculation while *investigating an issue* provides facts. In this case running lsof would tell you if dhclient is running and which port it uses and auditing the system should show you if there's reason for concern. Your distribution wiki (I always forget the URI) provides information on how to check things (package content hashes, user login records, system and service logs, files not owned by packages, user, process and network connection listings, etc, etc) and the [CERT Intruder Detection Checklist](http://web.archive.org/web/20080109214340/http://www.cert.org/tech_tips/intruder_detection_checklist.html), while decidedly ancient and generic, offers some instructions should you have no clue where to begin. Indeed you probably don't have a thing to worry about. The thing however is not that you should worry or not but *know how to act when you do*.

*Maybe also ponder ditching Chkrootkit (hasn't seen updates since 2009) for other better maintained auditing applications.

---

### Post by a-you on 2013-08-25
Unspawn your points are all well taken. Honestly I do try to be informed, but understanding how to do that accumulates over some time.

Actually I use integrit as well for keeping a snapshot of the state of the / file system. The curious lessen learned in this case---in case anybody else reads this and might benefit---was this:

Rkhunter and chkrootkit are run by anacron in my case, which is configured such that it tends to run pretty much immediately after the computer starts; integrit I have running (to generate the DB) only manually, which I do anytime I do a system update.

Then, typically, after anacron has run rkhunter and chkrootkit I do lots of stuff with the computer (work).

Then maybe sometime during the day I see that oh, Software Updater says an update is due, and I might run that.

So you see the obvious-in-retrospect flaw: that there were several hours of work, that certainly included lots of  interwebs, between the runs of rkhunter and chkrootkit  in the AM and the point in the  evening when I updated the DBs of rkhunter and integrit. The easy fix---for the future anyway---is  that from now on I'll do a system update only in the AM before  doing anything else.

It's a twisted lesson learned, because now I had/have this sort of large extra work load just trying to be sure it was a false positive. Really looking back I think it was that, but I won't take it for granted. Thanks again for your expert thoughts.

BTW I had another idea in this case, and I think it helped: in Synaptic I reinstalled all of the packages that dpkg -S had said contained "dhclient", plus some others that seemed to me anyway possibly relevant,. Then I ran a check with integrit, and of course it reported that those very items had changed. But what was good (I think) was that the hashes it stored for them were not different, only their mtimes and ctimes had changed. To me that said that unless I had been pwned so severely that this whole process could be faked, that those (new) binaries were identical to the ones from a few days before, when there were definitely no reports of "infection". This might not be conclusive of course, but it helped I think.

---

### Post by unspawn on 2013-08-25
> **a-you said:**
> Actually I use integrit as well for keeping a snapshot of the state of the / file system.  Back when I ran AIDE I tended to run separate databases at different intervals. For example monitoring directories containing binaries could be run quickly and should generally yield no changes unless the system was updated. Nowadays I run Samhain because it runs as a daemon process, can run any checks at different intervals and watches for changes via Inotify which is efficient.   > **a-you said:**
> Thanks again for your expert thoughts. Thanks. I'm not an expert though.   > **a-you said:**
> (..) I ran a check with integrit, (..) the hashes it stored for them were not different, only their mtimes and ctimes had changed. To me that said that unless I had been pwned so severely that this whole process could be faked, that those (new) binaries were identical to the ones from a few days before, when there were definitely no reports of "infection". This might not be conclusive of course, but it helped I think. Yes, that helps. Next time please tell us earlier on though. I suggest you keep a copy of your Integrit database with your other off-line backups.

---

### Post by a-you on 2013-08-25
"Yes, that helps. Next time please tell us earlier on though."

Good point. If something like this happens again I'll do that.

"I suggest  you keep a copy of your Integrit database with your other off-line  backups"

Yes I plan to start doing that of course, now. I guess in the scenario that I experienced I could have run integrit twice, a check with each database, and then compared the results to get an idea of what was different and why.

May I ask you: if you think I'm being too quick to decide that it was a false positive then please tell me (I'll look at this thread), because I have the impression that you and also Samiux think it was; I think so, but I'm not anywhere near as well informed as you both. If I see a post like that from you then I won't mark it solved until I do more checking. But if the main ordeal is done then I think it might help others if I mark it solved.

Thanks again.

---

### Post by unspawn on 2013-08-26
> **a-you said:**
> I guess in the scenario that I experienced I could have run integrit twice, a check with each database, and then compared the results to get an idea of what was different and why.
Yes!


> **a-you said:**
> if the main ordeal is done then I think it might help others if I mark it solved.
Now you know how to check things. So please mark the thread solved, yes.

---

### Post by a-you on 2013-09-03
In all fairness I think I understand *how* to approach the process of checking :-). It's just that for those of us that are relatively new to GNU/linux there's so much that we're not *familiar* with in OS, that's all. In the above situation it seemed likely that that somebody more familiar could look at the symptoms and right away recognize either that it was a false positive, or that it might not be. It's kind of a digression, so I'll be real brief, but as a firm believer in the principles that ubuntu aspires to uphold, I certainly help people in areas that are lets say my field of expertise, so I didn't feel like it was excessive to ask for OS help in this situation.

Anyway seriously unspawn, your advice was much appreciated and I'm truly grateful. It was nice of you to modestly say you're "no expert" but compared to those of us that are relative n00bs, you're way ahead. Thanks again, and to Samiux too!!!

---

### Post by unspawn on 2013-09-03
> **a-you said:**
> In all fairness I think I understand *how* to approach the process of checking :-). It's just that for those of us that are relatively new to GNU/linux there's so much that we're not *familiar* with in OS, that's all. 
That I can understand.


> **a-you said:**
> (..) as a firm believer in the principles that ubuntu aspires to uphold, I certainly help people in areas that are lets say my field of expertise, so I didn't feel like it was excessive to ask for OS help in this situation.
No such thing as excessive questions. Asking questions isn't stupid but NOT asking is.


> **a-you said:**
> In the above situation it seemed likely that that somebody more familiar could look at the symptoms and right away recognize either that it was a false positive, or that it might not be. 
I don't want to come across as lecturing so I'll try and keep it brief. One of the UNIX mantras is "everything is a file" from which (for me at least) naturally follows "measuring is knowing". What personally irks me are "don't worry" one-liners. They're not helpful because *they teach the OP nothing* and consequently keep the OP from verifying things her/himself. And anyone can make mistakes or misread things leading to improper analysis. Combine that with not asking *exactly why* it's fine and you'll see what a disservice saying "don't worry" actually is when it comes to responsibility, sharing information and creating self-reliance. 

*If this was too long then just think Fish vs Fishing Rod :-]

---

### Post by a-you on 2013-09-06
"I don't want to come across as lecturing so I'll try and keep it brief. One of the UNIX mantras is "everything is a file" from which (for me at least) naturally follows "measuring is knowing". What personally irks me are "don't worry" one-liners. They're not helpful because they teach the OP nothing and consequently keep the OP from verifying things her/himself. And anyone can make mistakes or misread things leading to improper analysis. Combine that with not asking exactly why it's fine and you'll see what a disservice saying "don't worry" actually is when it comes to responsibility, sharing information and creating self-reliance."

I think you are very right in this. And well said. I can say that I do appreciate the "don't worry" comments too though, in a situation where one doesn't know where to start looking it's helpful when they come from somebody that knows from whence they speak. But really I (and I think most of us) especially appreciate the "how to fish" suggestions, vs just "here's a fish".

So thanks again.

---

