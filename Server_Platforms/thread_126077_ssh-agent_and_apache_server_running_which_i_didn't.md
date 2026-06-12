---
title: "ssh-agent and apache server running which i didn't put there :("
date: 2006-02-05
forum: Server Platforms
---

### Post by ice60 on 2006-02-05
please tell me this is normal for Ubuntu. firstly should i have ssh-agent running? and how can i have a 195.xx.xx.xx connection on a standalone PC? i went to the address and it was something to do with apache. i can't do a reinstall i have no backups.

---

### Post by ice60 on 2006-02-06
i was hoping someone could tell me if the ssh-agent is supposed to be running when you look at running processes. or at least if you have it too.

i thought the 195.xxx.xxx.xxx address was in the local range but it's not so i'm not so worried about that now.

---

### Post by Peter76 on 2006-02-06
Don't worry, the ip address you probably got from your internet provider and ssh-agent needs to be running for your x-server. Check man ssh-agent for more info.

---

### Post by ice60 on 2006-02-06
[QUOTE=Peter76]Don't worry, the ip address you probably got from your internet provider and ssh-agent needs to be running for your x-server. Check man ssh-agent for more info.[/QUOTE]
thanks for the help, Peter. what happened is my connection was slow so i looked to see what connections i had. i had that 195 connection and i was downloading something from it through port 80. when i went to the IP it was a generic apache page so i thought i'd been rooted through a ssh connection and a server was being setup :cry: 

then i remembered i had been downloading a file from [here](http://www.betterdesktop.org/wiki/index.php?title=Data) and cancelled it. but instead of doing ctrl/c to stop the wget download i just closed terminal so the download was downloading in the background.

so, i'm not worried about the running ssh-agent now. but the 195 address i'm still alittle unsure about, i want to be 100% sure that what i saw was the download i didn't stop. how can i check the wget log? i can't find it. i  CDed to my desktop then started wget where would the log be for it from yesterday? thanks.

---

### Post by ardchoille on 2006-02-07
[QUOTE=Peter76]Don't worry, the ip address you probably got from your internet provider and ssh-agent needs to be running for your x-server. Check man ssh-agent for more info.[/QUOTE]
ssh-agent does not need to be running for the x server. The first thing I do after a new install is "sudo mv /usr/bin/ssh-agent /usr/bin/ssh-agent-original && sudo killall ssh-agent". I reboot, ssh-agent never starts again and x works just fine.

---

### Post by LordHunter317 on 2006-02-07
That's silly, and a poor way to do it.  Don't ever move a program to disable it without verifying that's the only way to do it.  In this case, you can edit /etc/X11/Xsession.options and disable the automatic starting of ssh-agent.

---

### Post by ardchoille on 2006-02-07
[QUOTE=LordHunter317]That's silly, and a poor way to do it.  Don't ever move a program to disable it without verifying that's the only way to do it.  In this case, you can edit /etc/X11/Xsession.options and disable the automatic starting of ssh-agent.[/QUOTE]
Well, thank you for the info, I did not know about that. However, the way you phrased your post made it sound disrespectful. In the future is it possible for you to post in a more acceptable manner? Something like?:

"You can edit /etc/X11/Xsession.options and disable the automatic starting of ssh-agent. This is better than moving an app to keep it from starting."

If people take your posts as being disrespectful, the only thing you are going to succeed in is being added to their ignore list.

Just my $0.02

---

### Post by LordHunter317 on 2006-02-07
[QUOTE=ardchoille]Well, thank you for the info, I did not know about that. However, the way you phrased your post made it sound disrespectful.[/quote]I apologize, but your actions were rather silly.  Moreover, it's bad, because people could construe that as an acceptable course of action, when it really should be a last resort.  Which was the motivation for pointing it out not to do it so strongly.

We all do silly things (I do them everyday, like being late for class, and watching TV instead of writing papers).  It's only a big deal if you make it one.  I do apologize, however.

> If people take your posts as being disrespectful, the only thing you are going to succeed in is being added to their ignore list.No offense, but this is just biting the hand that's feeding you.

---

### Post by ardchoille on 2006-02-07
[QUOTE=LordHunter317]I apologize, but your actions were rather silly.  Moreover, it's bad, because people could construe that as an acceptable course of action, when it really should be a last resort.[/QUOTE]
That's a very good point. I did this because someone else I trusted had given me this advice. I will try to utilise these forums more often so I don't end up giving bad advice to others. Thank you for bringing this to my attention.

[QUOTE=LordHunter317]We all do silly things (I do them everyday, like being late for class, and watching TV instead of writing papers).  It's only a big deal if you make it one.  I do apologize, however.[/QUOTE]
Thank you. It's nice to see people who are both knowledgable **and** curteous, I feel that is rare.

---

### Post by ice60 on 2006-02-07
hi, i don't want ssh running if i don't need it. here is my Xsession.options can you show me what i should comment out, please?

```
# /etc/X11/Xsession.options
#
# configuration options for /etc/X11/Xsession
# See Xsession.options(5) for an explanation of the available options.
allow-failsafe
allow-user-resources
allow-user-xsession
use-ssh-agent
use-session-dbus

```

i don't need to use encrypted connections is it safe to uninstall the whole thing, or is it needed else where? if i can uninstall it what do i remove, is it the Openssh-Client? thanks.

---

### Post by ardchoille on 2006-02-07
I took LordHunter317's advice and made the following changes to my /etc/X11/Xsession.options file (I commented the "use-ssh-agent" line):

```

# /etc/X11/Xsession.options
#
# configuration options for /etc/X11/Xsession
# See Xsession.options(5) for an explanation of the available options.
allow-failsafe
allow-user-resources
allow-user-xsession
# use-ssh-agent
use-session-dbus

```

My system works fine.

---

### Post by ice60 on 2006-02-07
[QUOTE=ardchoille]I took LordHunter317's advice and made the following changes to my /etc/X11/Xsession.options file (I commented the "use-ssh-agent" line):

```

# /etc/X11/Xsession.options
#
# configuration options for /etc/X11/Xsession
# See Xsession.options(5) for an explanation of the available options.
allow-failsafe
allow-user-resources
allow-user-xsession
# use-ssh-agent
use-session-dbus

```

My system works fine.[/QUOTE]
OK thanks i'll do that.

---

