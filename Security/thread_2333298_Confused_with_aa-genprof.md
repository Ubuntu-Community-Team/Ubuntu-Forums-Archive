---
title: "Confused with aa-genprof"
date: 2016-08-08
forum: Security
---

### Post by &amp;KyT$0P# on 2016-08-08
Trying to use aa-genprof to spin a VirtualBox AppArmor profile, but I'm not sure if it's working or not.  Basically I'm trying to run VirtualBox multiple times and with aa-genprof each time, until aa-genprof stops suggesting changes (meaning no more AppArmor complaints for VirtualBox).  I was then going to put it in complain mode for a while and see if anything else comes up in the logs, but I can't seem to get that far.
I've left the profile in complain mode for now, but given my experiences with aa-genprof, I'm not sure if the log entries it will create are meaningful or just noise...

1) Why are there different access violations logged at each run of aa-genprof - including some things that already allowed?
As far as I'm aware, I'm doing basically the exactly the same things with VirtualBox each time, yet it's trying to access different-but-overlapping sets of files...
 - start aa-genprof
 - start manager
 - start VM, make sure to make use of 3D acceleration and sound and networking
 - shutdown VM, restore snapshot
 - quit manager
 - see what aa-genprof thought of that

2) Why doesn't aa-genprof (or AppArmor?) seem to like the use of, say, @{HOME}, requiring /home/* instead?

3) What's all this and why don't these go away when I force-reload the AppArmor profiles?
```
   /usr/lib/virtualbox/VirtualBox//null-1
   /usr/lib/virtualbox/VirtualBox//null-2
   /usr/lib/virtualbox/VirtualBox//null-3
   /usr/lib/virtualbox/VirtualBox//null-4
   /usr/lib/virtualbox/VirtualBox//null-4//null-11
   /usr/lib/virtualbox/VirtualBox//null-4//null-11//null-12
   /usr/lib/virtualbox/VirtualBox//null-4//null-13
   /usr/lib/virtualbox/VirtualBox//null-4//null-13//null-14
   /usr/lib/virtualbox/VirtualBox//null-4//null-15
   /usr/lib/virtualbox/VirtualBox//null-4//null-17
   /usr/lib/virtualbox/VirtualBox//null-4//null-17//null-18
   /usr/lib/virtualbox/VirtualBox//null-4//null-17//null-21
   /usr/lib/virtualbox/VirtualBox//null-4//null-19
   /usr/lib/virtualbox/VirtualBox//null-4//null-19//null-1a
   /usr/lib/virtualbox/VirtualBox//null-4//null-1b
   /usr/lib/virtualbox/VirtualBox//null-4//null-1b//null-1c
   /usr/lib/virtualbox/VirtualBox//null-4//null-1d
   /usr/lib/virtualbox/VirtualBox//null-4//null-1d//null-1e
   /usr/lib/virtualbox/VirtualBox//null-4//null-1f
   /usr/lib/virtualbox/VirtualBox//null-4//null-1f//null-20
   /usr/lib/virtualbox/VirtualBox//null-4//null-5
   /usr/lib/virtualbox/VirtualBox//null-4//null-5//null-6
   /usr/lib/virtualbox/VirtualBox//null-4//null-7
   /usr/lib/virtualbox/VirtualBox//null-4//null-7//null-8
   /usr/lib/virtualbox/VirtualBox//null-4//null-9
   /usr/lib/virtualbox/VirtualBox//null-4//null-9//null-a
   /usr/lib/virtualbox/VirtualBox//null-4//null-b
   /usr/lib/virtualbox/VirtualBox//null-4//null-b//null-16
   /usr/lib/virtualbox/VirtualBox//null-4//null-b//null-c
   /usr/lib/virtualbox/VirtualBox//null-4//null-d
   /usr/lib/virtualbox/VirtualBox//null-4//null-d//null-e
   /usr/lib/virtualbox/VirtualBox//null-4//null-f
   /usr/lib/virtualbox/VirtualBox//null-4//null-f//null-10

```
EDIT I found a way to get rid of those: use aa-disable on the profile.  However, it doesn't un-disable unless the symlink in /etc/apparmor.d/disable is manually removed:
```
sudo aa-complain (profile)
sudo rm -fv /etc/apparmor.d/disable/(profile)
sudo aa-complain (profile)
```

4) Or am I just using aa-genprof wrong or misunderstanding how it works?


This is the (slightly-altered) current state of the profile (way more permissive than I'd like but hoping to change that):
```
# Last Modified: xxx xxx xx xx:xx:xx 2016
#include <tunables/global>

/usr/lib/virtualbox/VirtualBox flags=(complain) {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/kde>
  #include <abstractions/lightdm>
  #include <abstractions/nameservice>

  capability net_raw,
  capability sys_admin,

  network inet raw,

  @{HOME}/** r,
  @{HOME}*/.config/VirtualBox/** rw,
  @{HOME}*/.config/pulse/cookie rk,
  @{HOME}*/Documents/share*/** rw,
  "@{HOME}*/VirtualBox VMs/" rw,
  "@{HOME}*/VirtualBox VMs/**" rw,
  @{PROC}/** r,
  /tmp/** mrwlkix,
  /var/tmp/** mrwlkix,

}

```

---

### Post by &amp;KyT$0P# on 2016-08-09
Now I'm even more confused.  I just cleaned up the stray wildcards and tried again exactly what I did before, but this time actively watching syslog, and it worked exactly as I expected? :confused:

How to get AppArmor logs out of syslog and into a dedicated log file?  The configuration (logprof.conf) looks to be set up to use a dedicated log, however it's not doing that
```
  logfiles = /var/log/audit/audit.log /var/log/syslog /var/log/messages
```

I'd like to force it to use a dedicated logfile so that manually rotating AppArmor-related logs won't interfere with other stuff.  I suspect aa-genprof might be slightly buggy at reading syslog.

---

### Post by &amp;KyT$0P# on 2016-08-14
bump

And why aa-logprof doesn't say anything about these complain-mode entries?
```
type=1400 audit(**********.***:***): apparmor="ALLOWED" operation="ptrace" profile="/usr/lib/virtualbox/VirtualBox" pid=**** comm="nspr-2" requested_mask="read" denied_mask="read" peer="unconfined"
```
Looks like normal activity to me, given that I use a host-only network, so would like to allow it in the AppArmor profile :-k

---

### Post by &amp;KyT$0P# on 2016-08-15
> **halogen2 said:**
> How to get AppArmor logs out of syslog and into a dedicated log file?  The configuration (logprof.conf) looks to be set up to use a dedicated log, however it's not doing that
```
  logfiles = /var/log/audit/audit.log /var/log/syslog /var/log/messages
```

I'd like to force it to use a dedicated logfile so that manually rotating AppArmor-related logs won't interfere with other stuff.  I suspect aa-genprof might be slightly buggy at reading syslog.
So I'm not sure that AppArmor is able to do any logging of its own?  Apparently it only use /var/log/audit/audit.log if the auditd is installed, so I installed auditd as a test, no idea what exactly it does yet 8-[ but it looks like it's for more than just AppArmor.  Whatever it's logging does look interesting though so will read about it a bit more, might be a keeper for other reasons :-k

Anyway, is it even possible to make AppArmor logs go to a dedicated logfile?

---

### Post by anoda on 2016-10-10
Hello. According to your - **halogen2** - first post and a message containing: 

```
/usr/lib/virtualbox/VirtualBox//null-1
/usr/lib/virtualbox/VirtualBox//null-4//null-11
(...)
``` 

And so on, this means you will need additional exec rules - one or more than one rule. Generally, **null-*** are temporary profiles for execs, that are not permitted in the profile for now. And it seems it will be created for profiles in a complain mode. I think we will need a bigger part of an audit log message etc. (Something with: **operation="exec"** **profile="/usr/lib/virtualbox/VirtualBox"** but without any **//null-*** in the profile name).

One more thing: please see this link: [https://ubuntuforums.org/showthread.php?t=2048028&p=12196840#post12196840](https://ubuntuforums.org/showthread.php?t=2048028&p=12196840#post12196840) There is a VBox profile, so maybe it will help you somehow.

---

### Post by &amp;KyT$0P# on 2016-10-10
Thanks anoda, it does help me somehow!  This line looks like one I need -
```
capability sys_ptrace,
```
Will try it, thank you.

---

### Post by &amp;KyT$0P# on 2016-10-18
I've been running in complain mode with the suggested change, and went to check the logs, but I discovered a problem with apparmor logging.  Half of the apparmor messages are in syslog, the other half are in audit.log, and I can't figure out how to get [FONT=Courier New]ausearch[/FONT] to show the apparmor messages from audit.log.

I've looked at audit.log "manually", and it does contain stuff that looks apparmor-related.  Here's the latest such message -
```
type=AVC msg=audit(1476836712.095:264): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" name="/etc/ld.so.preload" pid=**** comm="nm-dhcp-client." requested_mask="r" denied_mask="r" fsuid=0 ouid=0
```

And the most recent VirtualBox-related entry -
```
type=AVC msg=audit(1476836700.399:261): apparmor="ALLOWED" operation="ptrace" profile="/usr/lib/virtualbox/VirtualBox" pid=**** comm="nspr-2" requested_mask="read" denied_mask="read" peer="unconfined"
```

The problem with doing it manually is that those messages don't contain a human-readable timestamp.  Thus, I don't know if this is from before or after adding that line to my apparmor profile, and thus, I don't know whether I still have a problem with it.


So how to collect apparmor log messages, such that they all include a human-readable timestamp?

---

### Post by anoda on 2016-10-21
Hi **halogen2**. I don't know which AppArmor version you're running, but you can try something like this:

```
ptrace (read) peer=@{profile_name},

## or
ptrace peer=@{profile_name},
``` 

It's about "*the most recent VirtualBox-related entry*". More informations about ptrace (see **PTrace rules**) etc.: [http://manpages.ubuntu.com/manpages/xenial/en/man5/apparmor.d.5.html](http://manpages.ubuntu.com/manpages/xenial/en/man5/apparmor.d.5.html) Maybe here you will find something useful: [https://debian-handbook.info/browse/stable/sect.apparmor.html](https://debian-handbook.info/browse/stable/sect.apparmor.html) And the first message (about [COLOR=#008000]/etc/ld.so.preload[/COLOR]) - have you tried to add such rule?:

```
/etc/ld.so.preload r,
```

Now, AppArmor logs: frankly I don't even have [COLOR=#008000]audit.log[/COLOR] file. I've always use [COLOR=#008000]/var/log/kern.log[/COLOR] file to check what AppArmor is doing etc. And there is everything, including timestamp. Also, maybe try to add an audit flag to some rules? It specifies that permissions requests that match the rule should be recorded to the audit log. (This can make noise in logs files such as syslog etc.) 

```
## an example of audit
audit deny /etc/passwd r,
```

One more thing: please see this one - [https://wiki.ubuntu.com/DebuggingApparmor#Debugging_procedure](https://wiki.ubuntu.com/DebuggingApparmor#Debugging_procedure) - especially **IMPORTANT**. There are notes about 'audit' entries and so on. Just for an information: "*<abstractions/base> includes read-only access to a lot of libraries and some accesses that are just so common that it makes sense to include them everywhere by default*". Maybe you need to add more <abstraction/*>? At last: you can see - [http://manpages.ubuntu.com/manpages/xenial/en/man7/apparmor.7.html](http://manpages.ubuntu.com/manpages/xenial/en/man7/apparmor.7.html) - and** ERRORS **point. There are some informations about log messages reported to audit etc. (I think you're using auditd(8) daemon, but maybe I'm wrong). If that's true, maybe try to disable auditd daemon, restart AppArmor and see, for example, in [COLOR=#008000]/var/log/kern.log [/COLOR]for a logged messages. Here is auditd man page: [http://manpages.ubuntu.com/manpages/xenial/en/man8/auditd.8.html](http://manpages.ubuntu.com/manpages/xenial/en/man8/auditd.8.html) But it's for a Xenial release![COLOR=#008000][/COLOR]

That's all what I can write now. Sorry.

---

### Post by &amp;KyT$0P# on 2016-10-21
> **anoda said:**
> I don't know which AppArmor version you're running, 
I'm running stock AppArmor of Lubuntu 14.04

> you can try something like this
That first ptrace line looks right for me.  Based on the information you've given, I'm also removing that [FONT=Courier New]capability sys_ptrace[/FONT] line.
Thanks! :KS

> And the first message (about [COLOR=#008000]/etc/ld.so.preload[/COLOR]) - have you tried to add such rule?:
It doesn't seem to affect anything, so I'm just letting that be.

> Also, maybe try to add an audit flag to some rules?
AppArmor **is** logging everything.  After reloading AppArmor profiles a few times, I think I've figured out why the split.

Looks like the messages that go to syslog are from during system boot, before auditd is loaded.  The rest are sent to [FONT=Courier New]auditd[/FONT].

So I only need to think about what's in audit logs.

> I think you're using auditd(8) daemon, 
You think correctly.  I left it installed.

I would like to keep auditd, so how to obtain AppArmor messages from audit logs?

By the way, I tried a slightly different type of search, but only found [this old page]("https://www.novell.com/support/kb/doc.php?id=7015244") describing exactly the same problem, but no answer.

> That's all what I can write now. Sorry. 
No problem, you are very helpful.  Thanks again. :)

---

### Post by &amp;KyT$0P# on 2016-10-24
Logs part of this question is solved, for me.  I just threw up my hands and wrote my own script to read audit.log, grab and format AppArmor messages.  For others who look to do the same, here's the key.  Let's take another look at this message -
> **halogen2 said:**
> And the most recent VirtualBox-related entry -
```
type=AVC msg=audit(1476836700.399:261): apparmor="ALLOWED" operation="ptrace" profile="/usr/lib/virtualbox/VirtualBox" pid=**** comm="nspr-2" requested_mask="read" denied_mask="read" peer="unconfined"
```
See the [FONT=Courier New]audit(1476836700.399:261)[/FONT] part of the message?  The timestamp is [FONT=Courier New]1476836700.399[/FONT] i.e. the number in parentheses before the colon.  Use [FONT=Courier New]date[/FONT] to convert it to human readable format -
```
date -d @1476836700.399
```


As for marking this thread solved, I'll come back and do that when I feel comfortable putting my VirtualBox profile in enforce mode.

---

### Post by &amp;KyT$0P# on 2016-11-16
I've set the profile in enforce mode, so time to mark this as solved.

I should say one other thing though.  Saw these log messages -
```
type=AVC msg=audit(xxxxxxxxxx.xxx:132): apparmor="ALLOWED" operation="mknod" profile="/usr/lib/virtualbox/VirtualBox" name="/home/xxxxx/.kde/share/config/kdeglobalsLE4043.new" pid=4043 comm="VirtualBox" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
type=AVC msg=audit(xxxxxxxxxx.xxx:132): apparmor="ALLOWED" operation="open" profile="/usr/lib/virtualbox/VirtualBox" name="/home/xxxxx/.kde/share/config/kdeglobalsLE4043.new" pid=4043 comm="VirtualBox" requested_mask="wc" denied_mask="wc" fsuid=1000 ouid=1000
type=AVC msg=audit(xxxxxxxxxx.xxx:133): apparmor="ALLOWED" operation="chown" profile="/usr/lib/virtualbox/VirtualBox" name="/home/xxxxx/.kde/share/config/kdeglobalsLE4043.new" pid=4043 comm="VirtualBox" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
type=AVC msg=audit(xxxxxxxxxx.xxx:134): apparmor="ALLOWED" operation="chmod" profile="/usr/lib/virtualbox/VirtualBox" name="/home/xxxxx/.kde/share/config/kdeglobalsLE4043.new" pid=4043 comm="VirtualBox" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
type=AVC msg=audit(xxxxxxxxxx.xxx:135): apparmor="ALLOWED" operation="open" profile="/usr/lib/virtualbox/VirtualBox" name="/home/xxxxx/.kde/share/config/kdeglobalsLE4043.new" pid=4043 comm="VirtualBox" requested_mask="wc" denied_mask="wc" fsuid=1000 ouid=1000
type=AVC msg=audit(xxxxxxxxxx.xxx:136): apparmor="ALLOWED" operation="chmod" profile="/usr/lib/virtualbox/VirtualBox" name="/home/xxxxx/.kde/share/config/kdeglobalsLE4043.new" pid=4043 comm="VirtualBox" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
type=AVC msg=audit(xxxxxxxxxx.xxx:137): apparmor="ALLOWED" operation="rename_src" profile="/usr/lib/virtualbox/VirtualBox" name="/home/xxxxx/.kde/share/config/kdeglobalsLE4043.new" pid=4043 comm="VirtualBox" requested_mask="wd" denied_mask="wd" fsuid=1000 ouid=1000
```

I'm not sure what happened there.  Looks like a one-off, but nothing out of line, so I decided to allow it anyway.  Not sure completely on how to, as apparmor doesn't accept letters c or d in the mask.  Some searching suggests that the fix would be -
```
owner @{HOME}/.kde{,4}/share/config/kdeglobals*.new rwk,
```
Stuck that in [FONT=Courier New]abstractions/kde[/FONT] and hoping it'll do.

Now, with that said, here's my VirtualBox profile -
```
#include <tunables/global>

/usr/lib/virtualbox/VirtualBox {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/kde>
  #include <abstractions/lightdm>
  #include <abstractions/nameservice>


  capability net_admin,
  capability net_raw,
  capability sys_admin,

  ptrace (read),

  network inet raw,

  /tmp/** mrwlkix,
  /var/tmp/** mrwlkix,
  @{HOME}/** r,
  @{HOME}/.config/VirtualBox/** rw,
  @{HOME}/Documents/share*/** rw,
  "@{HOME}/VirtualBox VMs/**" rw,
  @{PROC}/** r,

}

```

Thanks agin anoda for the help. :KS

---

