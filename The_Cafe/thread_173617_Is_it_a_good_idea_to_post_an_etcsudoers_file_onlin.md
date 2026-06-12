---
title: "Is it a good idea to post an /etc/sudoers file online?"
date: 2006-05-10
forum: The Cafe
---

### Post by aysiu on 2006-05-10
I was thinking that occasionally people have situations where their /etc/sudoers file gets corrupted, and they have to boot into recovery mode to fix it.

Would it make sense to have a copy of the standard /etc/sudoers file online so people can just use a *wget* command to replace their current one?

I have a few follow-up questions to this, too:

1. Does everyone, in fact, have the same default /etc/sudoers file? It's the /etc/group file that's different for each installation, right?

2. Is it mainly that people somehow get a corrupt /etc/sudoers file, or is it more often the problem that they accidentally remove themselves from the *admin* group?

3. Is the problem not widespread enough to worry about/ is this a poor solution?

---

### Post by cgjones on 2006-05-10
Right off the top of my head, that doesn't sound like a bad idea. I think sudoers and group are both pretty generic on a default install.

---

### Post by aysiu on 2006-05-10
[QUOTE=cgjones]Right off the top of my head, that doesn't sound like a bad idea. I think sudoers and group are both pretty generic on a default install.[/QUOTE] Okay. Well, /etc/group can't really be generic, though, right? Doesn't it tack on your actual username to the *admin* group?

---

### Post by cgjones on 2006-05-10
That is correct.

---

### Post by red_Marvin on 2006-05-10
Why not just backup it onto a floppy or cd?

---

### Post by nanotube on 2006-05-10
well, from what i have seen, a large bulk of the problems with sudo arises out of people using the expert install, which creates a root user, as well as a regular user without sudo privileges. so then it is a matter of them adding themselves to the admin group - or their username explicitly to the sudoers file.

so... i don't see a problem with posting the default sudoers file or group file - but the sudoers is just two lines, (one for root, and one for group admin), and the group file is pretty obvious in its construction - so i don't see it as being extremely useful.

---

### Post by RavenOfOdin on 2006-05-10
Not useful.

---

### Post by aysiu on 2006-05-10
Okay. It looks as if it's just not getting a lot of support. Well, I threw the idea out there. It was worth a shot.

---

### Post by nanotube on 2006-05-10
[QUOTE=aysiu]Okay. It looks as if it's just not getting a lot of support. Well, I threw the idea out there. It was worth a shot.[/QUOTE]
well, it's not that it was a bad idea or anything. in fact, "in general" it would probably be a good idea to have a place with a bunch of default config files up on the web somewhere (maybe on your website, aysiu?). /etc/group, /etc/sudoers, /etc/hosts, /etc/fstab, and other things like that (i'm probably missing a few good ones). with helpful comments, if necessary. that way, if some conf file is hosed, one could go and look around there.
it's just that /etc/sudoers itself is not the most useful thing to have out there - but "a bunch of common config files that could get hosed one way or another" would i think be a pretty useful thing to have on a website.

---

### Post by aysiu on 2006-05-10
[QUOTE=nanotube]"a bunch of common config files that could get hosed one way or another" would i think be a pretty useful thing to have on a website.[/QUOTE] Food for thought. Wouldn't it not work to have /etc/group on there, though, as each person's would have her own unique username tacked on to each group?

---

### Post by briancurtin on 2006-05-11
edit: im talking about /etc/group in this post

you could toss one up there just as a reference, it wouldnt hurt. just make some kind of note saying that its purely a reference, and you shouldnt just copy/paste the whole thing.

you cant plagarize that file, the system will know you cheated and give you an F.

---

### Post by aysiu on 2006-05-11
Well, just for reference, here's the /etc/sudoers file: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
``` And here's the /etc/group file ```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:*firstuser*
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:*firstuser*,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:*firstuser*,haldaemon
floppy:x:25:*firstuser*,haldaemon
tape:x:26:
sudo:x:27:
audio:x:29:*firstuser*
dip:x:30:*firstuser*
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:*firstuser*
sasl:x:45:
plugdev:x:46:*firstuser*,haldaemon
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
*firstuser*:x:1000:
lpadmin:x:104:*firstuser*
scanner:x:105:*firstuser*,cupsys
admin:x:106:*firstuser*
crontab:x:107:
ssh:x:108:
messagebus:x:109:
haldaemon:x:110:
slocate:x:111:
```

---

### Post by nanotube on 2006-05-11
[QUOTE=aysiu]Food for thought. Wouldn't it not work to have /etc/group on there, though, as each person's would have her own unique username tacked on to each group?[/QUOTE]
heh well, that's where the "with helpful comments, if necessary" bit comes in. :) something like "replace blabla with your actual username" should do the trick.
edit: i see you already did the equivalent with the italicized 'firstuser'. cool. :)

---

### Post by GreyFox503 on 2006-05-11
Even simpler solution:  instead of posting a copy of the sudoers file *online*, why not just store it locally on a default Ubuntu install?  Something like /etc/defaultsudoers .

Then you could tell everyone the same command to restore their /etc/sudoers file.

The only reason it wouldn't work is if they deleted their entire /etc folder, in which case they have much bigger problems.

---

### Post by aysiu on 2006-05-11
That is a great idea. In fact, I've implemented it myself on my computer. How would we suggest it to the developers for Edgy?

---

### Post by nanotube on 2006-05-11
hmm, well this is not Quite it, but there is a "sample" sudoers file located in /usr/share/doc/sudo/examples/sudoers
it is not the same as the default sudoers (it sets up some more complicated schemes as examples), but... there it is, fwiw.

---

### Post by jdong on 2006-05-11
Well, let's start by saying it's **not** safe, downright reckless to post /etc/**shadow** online. This file contains encrypted hashes of your passwords. With this information, someone can use a brute forcing tool to determine your passwords in a matter of days (at worst)

As far as /etc/passwd, /etc/group, and /etc/sudoers, these do not contain passwords or other private information. However, they do reveal a deal of information about how user accounts are set up on your system. (it's no different than me saying "I have an account jdong on my system with sudo access"). Sure, there might be some way that this serves as useful information (a piece of the puzzle, so to speak) in a complex attack, but I can't see anything like that happening.


In short, I think it is a safe file to post. Sometimes posting a file like this is the fastest way to get assistance, especially if you made a silly typo (extraneous character, for example) that the experienced eye would catch but a newer user would skip right over

---

### Post by GreyFox503 on 2006-05-13
[quote=aysiu]How would we suggest it to the developers for Edgy?[/quote]

Now that you mention it, I really don't know.  Bugzilla is great for some feedback, but this isn't a bug.  Anyone know where the Ubuntu suggestion box is?

---

### Post by aysiu on 2006-06-12
FYI: I've created a *sudo* recovery tutorial on my Psychocats website.

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

