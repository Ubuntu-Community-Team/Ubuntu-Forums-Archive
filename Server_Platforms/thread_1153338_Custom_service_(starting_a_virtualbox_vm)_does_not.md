---
title: "Custom service (starting a virtualbox vm) does not start"
date: 2009-05-08
forum: Server Platforms
---

### Post by vor_lord on 2009-05-08
I'm new to Ubuntu/Debian (but not to linux).  I'm coming from a long-time Arch linux background which eschews SysV style init scripts, so this may be a newbie question.

It also may be in the wrong forum--I apologize if that is the case.  The virtual machine I am starting is Ubuntu Server, but the host (and the system for the question here) is a Ubuntu Desktop.  It just seemed much more of a server type of question.

I want to start a Virtualbox virtual machine on boot.  I copied /etc/init.d/skeleton and modified it to start (and stop) the virtual machine.  My script works perfectly if run manually as:

/etc/init.d/homestar_vm start

I then ran update-rc.d to create the needed symlinks.  Essentially I wanted to have this be the last thing to start (it certainly needs to start after all filesystems are mounted) and the first thing to shutdown.

I think that I did it correctly, giving it a priority of 99 for both cases.  This has resulted in the following symlinks:

root@strongbad:/etc# find . -name "*homestar*"
./rc2.d/S99homestar_vm
./rc6.d/K99homestar_vm
./rc1.d/K99homestar_vm
./rc4.d/S99homestar_vm
./rc0.d/K99homestar_vm
./rc3.d/S99homestar_vm
./rc5.d/S99homestar_vm
./init.d/homestar_vm

My reading of the man page seems to indicate I have done things correctly, but being new to SysV init scripts I am not sure.

Do those look they will do what I want them to do.

What happens is that the virtual machine is not started.  With Ubuntu Desktop the service starting messages are not displayed, and I am having trouble seeing what is going wrong.  If I launch the service manually once I log in everything is fine.

Where does stdout/stderr from the init scripts get logged to (if anywhere)?  The only related error messages I am seeing in /var/log/messages are some problems with the shutdown (which does appear to be running on a shutdown).

Any help would be appreciated.

---

### Post by Alekz_ on 2009-05-08
I don't have a good "tip" for that.. But you may want to boot your system verbosily (without the splash), so you'll be able to see any start up error messages!

You also can take a look on the vbox log files... Maybe the problem is not with the start up script, but with the application it self!

---

### Post by vor_lord on 2009-05-08
I'll try Alekz_'s suggestion to boot without the splash (easy if you know that is called the 'splash' ;)

Is there no one here who can comment on the update-rc.d links to confirm if they look right?  If they are the last thing started, and I can launch the service script manually successfully, then I don't think it is the application.

---

### Post by markba on 2009-05-10
I'm investigating this also. As I'm the developer/author of vboxtool (see my sig), capable of auto starting and stopping sessions, this particular error came up, *after* I upgraded to Jaunty. The vboxtool scripts worked fine until then. 

It has something to do with starting VBox sessions out of context, i.e. through rc.local or (like vboxtool does), init.d.

So no solution yet, but many more people seem to have the same problem:

[http://forums.virtualbox.org/viewtopic.php?f=7&t=17195&p=75252#p75252](http://forums.virtualbox.org/viewtopic.php?f=7&t=17195&p=75252#p75252)
[http://bbs.archlinux.org/viewtopic.php?id=71267](http://bbs.archlinux.org/viewtopic.php?id=71267)

Thus, this might be a problem related to Jaunty, but, because other people with other distro's have the same problem, it is probable a kernel problem.

---

### Post by vor_lord on 2009-05-11
So this works at least some of the time, it just seems to take a long time for the vm to be up.  I'm not sure why that would be but I can confirm that at least some of the time the vm starts as expected.

---

### Post by markba on 2009-05-11
> **vor_lord said:**
> So this works at least some of the time, it just seems to take a long time for the vm to be up.

Well, not quite, at least in my case, VM's *never* go into a usable state.

---

### Post by Alekz_ on 2009-05-11
Hi again!

I found this thread:
[http://ubuntuforums.org/showthread.php?t=1144800](http://ubuntuforums.org/showthread.php?t=1144800)

It's probably some bug of Ubuntu 9.04 (I suppose you're using 9.04).

People are trying some workarround (nohup before the command)...

About your rc?.d, looks good! So I don't think the problem is there!

---

### Post by markba on 2009-05-11
> **Alekz_ said:**
> Hi again!

I found this thread:
[http://ubuntuforums.org/showthread.php?t=1144800](http://ubuntuforums.org/showthread.php?t=1144800)

People are trying some workarround (nohup before the command)...

It works!!! I preceded the command in my vboxtoolinit script with 'nohup' and now, it works as expected and as it always did.

---

### Post by Alekz_ on 2009-05-12
Nice! :)

I don't like the idea.. Workarround shouldn't be a good thing, but untill they fix the "bug", it may help!

---

### Post by markba on 2009-05-12
Yes, it's a workaround, but not a nasty one. I guess the nohup command does not introduce any other problems, so it's 'mostly harmless', free from "The Hitchhiker's Guide to the Galaxy" (Douglas Adams).

> nohup is a Unix command that is used to run another command while suppressing the action of the HUP (hangup) signal, enabling the command to keep running after the user who issues the command has logged out. It is most often used to run commands in the background as daemons.

[http://en.wikipedia.org/wiki/Nohup](http://en.wikipedia.org/wiki/Nohup)


---

### Post by Alekz_ on 2009-05-12
I agree! `nohup` isn't 'mostly harmless' :)

But the thing is: Why is there a HUP signal been sent to the rc* process?

Anyways... If it's working, it's good! :)

---

