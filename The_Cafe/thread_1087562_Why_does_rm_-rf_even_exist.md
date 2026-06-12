---
title: "Why does rm -rf even exist?"
date: 2009-03-05
forum: The Cafe
---

### Post by NintendoTogepi on 2009-03-05
Why would anyone want to use it?

---

### Post by sisco311 on 2009-03-05
to remove files?

---

### Post by jacksaff on 2009-03-05
err, because rm alone doesn't recursively remove files (-r) and if you already know what your deleting you don't want to have rm keep prompting you to confirm (-f)...

---

### Post by seppl82 on 2009-03-05
Nice phil. Question.

Why does format c: on windows still exist :-)

---

### Post by gnomeuser on 2009-03-05
So competent people can quickly manage their files from the command line.

---

### Post by Vishal Agarwal on 2009-03-05
> **seppl82 said:**
> Nice phil. Question.

Why does format c: on windows still exist :-)

[COLOR="Blue"]To remove the virus from the drive at once :guitar:[/COLOR]

---

### Post by Eisenwinter on 2009-03-05
It exists because... it's useful? heh.

---

### Post by billgoldberg on 2009-03-05
Linux with the rm command would be like driving a car without brakes.

rm -fr can be dangerous if you don't know what the heck you're doing.

If you do know what you are doing, it a powerful tool.

---

### Post by saulgoode on 2009-03-05
Because it's easier to type than 'find -exec rm {} \;' (Note: only try this if you are Steve Jobs or you happen to be using his computer).

---

### Post by Giant Speck on 2009-03-05
I remember back when I was using Gutsy and Hardy, every now and then I'd try to empty the trash and it'd delete all but one or two files.  When I tried to delete those leftover files, it would give me permission errors.

So I'd just restore them to the desktop, fire up the terminal and use the rm -rf command (with sudo, of course) and delete the files.

It hasn't happened to me at all in Intrepid, so I'm thinking it was a bug in Gutsy and Hardy that was initially causing the problem.

---

### Post by Vince4Amy on 2009-03-05
So I can remove files/folders.

---

### Post by Skripka on 2009-03-05
> **NintendoTogepi said:**
> Why would anyone want to use it?

Because your GUI might someday get borked-and you need to delete some config files to see if you can get it back....

---

### Post by Rokurosv on 2009-03-05
Cause sometimes I want to delete a folder and I want to avoid getting a confirmation do delete it

---

### Post by Giant Speck on 2009-03-05
> **Skripka said:**
> Because your GUI might someday get borked-and you need to delete some config files to see if you can get it back....

I've had to [FONT=Courier New][COLOR=Gray]sudo rm -rf ~/.kde[/COLOR][/FONT] a few times and [FONT=Courier New][COLOR=Gray]s[/COLOR][COLOR=Gray]udo rm -rf ~/.gnome[/COLOR][/FONT] once, so I agree with the above.

---

### Post by Trail on 2009-03-05
I regularly use it.

---

### Post by vishzilla on 2009-03-05
I use it regularly at work..

---

### Post by notwen on 2009-03-05
> **billgoldberg said:**
> Linux with the rm command would be like driving a car without brakes.

rm -fr can be dangerous if you don't know what the heck you're doing.

If you do know what you are doing, it a powerful tool.

What bill said. *nod*

---

### Post by gjoellee on 2009-03-05
I use it to quickly delete files, and folders. It is good to have if your GUI crashes

---

### Post by Giant Speck on 2009-03-05
I've heard that Solaris has "rm -rf /" protection.

Why doesn't Linux have this?  Or do some distros actually have it?

---

### Post by JohnFH on 2009-03-05
That's like saying guns are dangerous and kill people - why do guns even exist?

---

### Post by igknighted on 2009-03-05
> **Giant Speck said:**
> I've heard that Solaris has "rm -rf /" protection.

Why doesn't Linux have this?  Or do some distros actually have it?

I'm pretty sure some do.  Or at least warn you that it is a really bad idea, and only do it if you know exactly what you are doing.

---

### Post by Giant Speck on 2009-03-05
> **igknighted said:**
> I'm pretty sure some do.  Or at least warn you that it is a really bad idea, and only do it if you know exactly what you are doing.

I believe that rm -rf is a very useful command, but I see absolutely no purpose in the command's continued ability to delete /.  That capability should have been removed long ago.

---

### Post by jenkinbr on 2009-03-05
I use it all the time.  Beats opening nautilus if all I want to do is prune a limb off of my directory tree.

Nevertheless it is still a dangerous command, so be careful how you use it.  Triple-check your command before letting it run.

---

### Post by jdong on 2009-03-05
> **Giant Speck said:**
> I've heard that Solaris has "rm -rf /" protection.

Why doesn't Linux have this?  Or do some distros actually have it?

A lot of distros have it, including Debian/Ubuntu:

> 
[jdong@droptop:~]$ rm -rf /                                       (03-05 11:47)
rm: cannot remove root directory `/'


However, it **ONLY** protects the root directory itself and does not try to second guess you if you specifically listed /usr /var /bin ... or /*. If you don't know what you are passing into rm you probably shouldn't be deleting it.


Try this puzzler:

```

jdong@CLOSETMONSTER:~$ su -
Password: 
No directory, logging in with HOME=/
root@CLOSETMONSTER:/# rm -rf / --no-preserve-root
rm: cannot remove `//media': Permission denied
rm: cannot remove `//etc/ld.so.cache': Permission denied
rm: cannot remove `//etc/rpc': Permission denied
rm: cannot remove `//etc/bindresvport.blacklist': Permission denied
rm: cannot remove `//etc/rsyslog.conf': Permission denied
rm: cannot remove `//etc/defoma/config/pango.conf': Permission denied
rm: cannot remove `//etc/defoma/config/x-ttcidfont-conf.conf2': Permission denied
rm: cannot remove `//etc/defoma/config/x-ttcidfont-conf.conf': Permission denied
rm: cannot remove `//etc/defoma/csetenc-xenc.data2': Permission denied
rm: cannot remove `//etc/defoma/hints/ttf-dejavu-core.hints': Permission denied
rm: cannot remove `//etc/defoma/hints/ttf-dejavu-extra.hints': Permission denied
rm: cannot remove `//etc/defoma/ps-cset-enc.data': Permission denied
rm: cannot remove `//etc/defoma/loc-cset.data': Permission denied
rm: cannot remove `//etc/defoma/fontconfig.subst-rule': Permission denied
rm: cannot remove `//etc/defoma/xenc-cset.data': Permission denied
rm: cannot remove `//etc/gtk-2.0/im-multipress.conf': Permission denied
rm: cannot remove `//etc/localtime': Permission denied
rm: cannot remove `//etc/motd': Permission denied
rm: cannot remove `//etc/mke2fs.conf': Permission denied
rm: cannot remove `//etc/rc4.d/S23ntp': Permission denied
rm: cannot remove `//etc/rc4.d/README': Permission denied
rm: cannot remove `//etc/rc4.d/S20rsync': Permission denied
rm: cannot remove `//etc/rc4.d/S20nfs-common': Permission denied
rm: cannot remove `//etc/rc4.d/S89atd': Permission denied

```

---

### Post by Giant Speck on 2009-03-05
So, Ubuntu has the protection even if you try to run it with sudo?  If so, that's pretty cool.

---

### Post by jenkinbr on 2009-03-05
> **jdong said:**
> A lot of distros have it, including Debian/Ubuntu:



However, it **ONLY** protects the root directory itself and does not try to second guess you if you specifically listed /usr /var /bin ... or /*. If you don't know what you are passing into rm you probably shouldn't be deleting it.


Try this puzzler:

```

jdong@CLOSETMONSTER:~$ su -
Password: 
No directory, logging in with HOME=/
root@CLOSETMONSTER:/# rm -rf / --no-preserve-root
rm: cannot remove `//media': Permission denied
rm: cannot remove `//etc/ld.so.cache': Permission denied
rm: cannot remove `//etc/rpc': Permission denied
rm: cannot remove `//etc/bindresvport.blacklist': Permission denied
rm: cannot remove `//etc/rsyslog.conf': Permission denied
rm: cannot remove `//etc/defoma/config/pango.conf': Permission denied
rm: cannot remove `//etc/defoma/config/x-ttcidfont-conf.conf2': Permission denied
rm: cannot remove `//etc/defoma/config/x-ttcidfont-conf.conf': Permission denied
rm: cannot remove `//etc/defoma/csetenc-xenc.data2': Permission denied
rm: cannot remove `//etc/defoma/hints/ttf-dejavu-core.hints': Permission denied
rm: cannot remove `//etc/defoma/hints/ttf-dejavu-extra.hints': Permission denied
rm: cannot remove `//etc/defoma/ps-cset-enc.data': Permission denied
rm: cannot remove `//etc/defoma/loc-cset.data': Permission denied
rm: cannot remove `//etc/defoma/fontconfig.subst-rule': Permission denied
rm: cannot remove `//etc/defoma/xenc-cset.data': Permission denied
rm: cannot remove `//etc/gtk-2.0/im-multipress.conf': Permission denied
rm: cannot remove `//etc/localtime': Permission denied
rm: cannot remove `//etc/motd': Permission denied
rm: cannot remove `//etc/mke2fs.conf': Permission denied
rm: cannot remove `//etc/rc4.d/S23ntp': Permission denied
rm: cannot remove `//etc/rc4.d/README': Permission denied
rm: cannot remove `//etc/rc4.d/S20rsync': Permission denied
rm: cannot remove `//etc/rc4.d/S20nfs-common': Permission denied
rm: cannot remove `//etc/rc4.d/S89atd': Permission denied

```
I won't actually try that... (until the next time I want to hose my system)

[offtopic]Nice avitar - I can barly read the text[/offtopic]

---

### Post by sisco311 on 2009-03-05
> **Giant Speck said:**
> So, Ubuntu has the protection even if you try to run it with sudo?  If so, that's pretty cool.

yes, read the man page if you don't believe us :)

>  --preserve-root
              do not remove `/' (default)
;)

---

### Post by jdong on 2009-03-05
Haha that only works if you have a good SELinux policy preventing silly mistakes as such ;-)

---

### Post by Giant Speck on 2009-03-05
> **sisco311 said:**
> yes, read the man page if you don't believe us :)

;)


Wait. I'm getting confused now.  It's only protected if you type --preserve-root after it?

Basically, my question is: which of the following commands would result in root *not* being deleted in Ubuntu?

1. rm -rf /
2. sudo rm -rf /
3. sudo rm -rf / --preserve-root

If all three of those can be executed without destroying your Ubuntu system, then that is awesome.

---

### Post by jdong on 2009-03-05
> **Giant Speck said:**
> Wait. I'm getting confused now.  It's only protected if you type --preserve-root after it?

Basically, my question is: which of the following commands would result in root *not* being deleted in Ubuntu?

1. rm -rf /
2. sudo rm -rf /
3. sudo rm -rf / --preserve-root

If all three of those can be executed without destroying your Ubuntu system, then that is awesome.


All 3 of your commands do not work. 2 and 3 are identical. --preserve-root is assumed by default. But, don't take this protection as a false sense of security: the following ** EXTREMELY DANGEROUS COMMANDS** WILL do their damage:

```

sudo rm -rf /*
sudo rm -rf /usr /lib /bin /home /var
sudo rm -rf / --no-preserve-root
find / -print0 | xargs -0 sudo rm -rf

```

And so on. It is still no reason to be careless with rm -rf commands.

---

### Post by Giant Speck on 2009-03-05
> **jdong said:**
> All 3 of your commands do not work. 2 and 3 are identical. --preserve-root is assumed by default. But, don't take this protection as a false sense of security: the following ** EXTREMELY DANGEROUS COMMANDS** WILL do their damage:

```

sudo rm -rf /*
sudo rm -rf /usr /lib /bin /home /var
sudo rm -rf / --no-preserve-root
find / -print0 | xargs -0 sudo rm -rf

```And so on. It is still no reason to be careless with rm -rf commands.


Well, I certainly understand how accepting that sudo rm -rf / simply will not work could set up a false sense of security, I can honestly say that I'm not going to just run to a terminal to make sure.  I have absolutely no reason to run the rm -rf command unless it is absolutely necessary.

They really need to diable the capability to rm -rf /*, in my opinion.

---

### Post by MaxIBoy on 2009-03-05
I have, in fact, had a reason to nuke a hard drive before. I friend of mine was putting a fresh install of OS X on his old MacBook so he could sell it. For some reason, the installer disk was saying "You don't have enough space" instead of showing an option to format the drive. Weird. I knew we could probably look up on the Internet how to format the drive from the OS X installer disk, but I had a better plan. I just booted the computer back up from the hard drive, ran "sudo rm -rf /" and let him type in his password. Ten minutes later it was done and the installer disk worked perfectly.

---

### Post by Therion on 2009-03-05
As usual, it seems I'm late for the party.  Still, I must be confused... 

Is there some reason this command sequence (rm -rf et al) *shouldn't* exist?

Surely no one is arguing that because it's a powerful command that it shouldn't be made available?  

Because that would make my head asplode.

---

### Post by Kareeser on 2009-03-05
> **Giant Speck said:**
> I believe that rm -rf is a very useful command, but I see absolutely no purpose in the command's continued ability to delete /.  That capability should have been removed long ago.

It's not a feature.

rm -rf does exactly what it's supposed to do, no questions asked. It's not like someone specifically programmed rm -rf to be **able** to delete /

---

### Post by jdong on 2009-03-05
> **Giant Speck said:**
> Well, I certainly understand how accepting that sudo rm -rf / simply will not work could set up a false sense of security, I can honestly say that I'm not going to just run to a terminal to make sure.  I have absolutely no reason to run the rm -rf command unless it is absolutely necessary.

They really need to diable the capability to rm -rf /*, in my opinion.

Well it's not really a capability you can remove. How do you circumvent, say:

```

mount -o bind / /media/root
rm -rf /media/root

```

In which case, what if I had a root of another device like an external hard drive which I DID want to wipe out?


The command does a very simple job (remove everything underneath the path you give it), and does it well. It is, in my opinion, the user's fault if he points the command at something he regrets. It is no different from any other command that can cause permanent damage to the system like "echo hello world > /dev/hda".

---

### Post by Sporkman on 2009-03-05
I use it all the time.

---

### Post by mister_pink on 2009-03-05
Why on earth would you want to not have it? There's no way you could accidentally do it, and if a malicious program wanted to do it there's a million other ways to hose your system, for example using fdisk or dd.

Of course, malicious programs don't even ever want to hose your system, that doesn't gain them anything.

---

### Post by maybeway36 on 2009-03-05
I never "rm -r" anymore. I always "rm -rv" so it tells me what it's doing. It still does it, of course. And I've rarely if ever had to use "-f".

---

### Post by Simian Man on 2009-03-05
If you want to destroy your system, no amount of coddling will prevent you from doing so.  That is Windows stuff :).

---

### Post by jdong on 2009-03-05
> **Simian Man said:**
> If you want to destroy your system, no amount of coddling will prevent you from doing so.  That is Windows stuff :).

Even if someone wanted it, it's virtually asking the computer to solve a halting problem every time you remove a file ;-)

If there's one thing that irks me it's a computer program trying to be smarter than it should.

---

### Post by rajeev1204 on 2009-03-05
Hi jdong


As an admin,shouldnt you be locking this thread? You yourself are posting dangerous commands which might be a bad idea.I actually missed reading the 'DANGEROUS WARNING' in bold.





regards
rajeev

---

### Post by Simian Man on 2009-03-05
> **rajeev1204 said:**
> 
As an admin,shouldnt you be locking this thread? You yourself are posting dangerous commands which might be a bad idea.I actually missed reading the 'DANGEROUS WARNING' in bold.


If you copy & paste random commands from the internet, you deserve to have / wiped.

---

### Post by ghindo on 2009-03-05
I've heard that "rm -rf /" isn't POSIX compliant, or some such thing.

---

### Post by jdong on 2009-03-05
> **ghindo said:**
> I've heard that "rm -rf /" isn't POSIX compliant, or some such thing.

Indeed that is the explanation that got them to add --preserve-root: Because a full removal of / recursively will inevitably evaluate .. and ., which is an illegal traversal-up-from-root, the whole operation will inevitably fail and hence we should just fail it at the beginning.

---

### Post by jdong on 2009-03-05
> **rajeev1204 said:**
> Hi jdong


As an admin,shouldnt you be locking this thread? You yourself are posting dangerous commands which might be a bad idea.I actually missed reading the 'DANGEROUS WARNING' in bold.





regards
rajeev

No, so far this looks to me like a reasonable educational discussion of dangerous commands. It's better to be informed about this stuff than ignorant and assuming because there's a flag that you can now use rm to your heart's content.

Everyone is explicitly stating that the commands they are talking about are extremely dangerous; if they were being misrepresented then it would be a completely different concern.

---

### Post by Pijits_1 on 2009-03-05
I've always found it really useful for removing a directory and takes less typing then doing an rmdir --ignore-non-empty. I'm just careful when I use it. Great power needs great responsibility :P

---

### Post by mkendall on 2009-03-05
> **JohnFH said:**
> That's like saying guns are dangerous and kill people - why do guns even exist?

No, you silly man. Guns don't kill people. *Bullets* kill people.

---

### Post by saulgoode on 2009-03-05
> **mkendall said:**
> No, you silly man. Guns don't kill people. *Bullets* kill people.
But only if they are moving really, really fast.

---

### Post by MaxIBoy on 2009-03-05
What if you swallowed one and died of lead poisoning? Or choking, for that matter.



Anyway, there's a simple way of preventing users from doing stupid stuff like this unless they want to. It's called "not running around as root all the time." (Yeah, I'm looking at *you*, Puppy.)

---

### Post by NintendoTogepi on 2009-03-05
I meant 'rm -rf /' :D why does that (VERY DANGEROUS, DO NOT USE) command exist? Why hasn't it been disabled?

---

### Post by Giant Speck on 2009-03-05
> **NintendoTogepi said:**
> I meant 'rm -rf /' :D why does that (VERY DANGEROUS, DO NOT USE) command exist? Why hasn't it been disabled?

Because it is still useful in extremely rare and specific circumstances.

---

### Post by jdong on 2009-03-05
> **NintendoTogepi said:**
> I meant 'rm -rf /' :D why does that (VERY DANGEROUS, DO NOT USE) command exist? Why hasn't it been disabled?

The -rf invocation of rm is required to delete a directory and all of its contents, just like highlighting a directory in Nautilus and hitting the delete key on it.

The point is, locking out this one command doesn't really do anything to protect the user from screwing up his computer with careless dangerous commands because there are infinitely as many ways of doing the same thing. To ask for a computer to stop all of them would be an impossible to solve halting problem, and to be honest would get in the way of the user more than it would help. On my systems there have been many cases where I had legitimate reason to rm -rf a directory of 1.5 million files, and I would not have liked the OS trying to warn me that I was going to remove a bunch of files.

---

### Post by jfernyhough on 2009-03-05
> **NintendoTogepi said:**
> I meant 'rm -rf /' :D why does that (VERY DANGEROUS, DO NOT USE) command exist? Why hasn't it been disabled?Why does "format /y c:" exist? :P

---

### Post by MaxIBoy on 2009-03-05
DO NOT ATTEMPT ANY OF THESE!

These will delete things cleanly:

[LIST]
[*]rm -rf /
[*]find / -name '*' -exec rm { } ; #this one leaves all your directories, but everything will be empty
[/LIST]

These cause hard drive corruption, which will be probably unrecoverable:

[LIST]
[*]echo "any text at all" > /dev/*d* #where *d* includes sda, sdb, hda, hdb, fd0, fd1, etc.
[*]cat "any text at all" > /dev/*d*
[*]cat any_file_at.all > /dev/*d*
[*]<file.txt > /dev/*d*
[*]dd -if=/dev/amything -of=/dev/anything
[*]cp /dev/zero /dev/anything
[/LIST]

I've only ever used the first one, but I'm pretty sure they'll all work.


You're talking about an awful lot of useful functionality that will need to be sacrificed to stop users from ever messing things up.

---

### Post by doorknob60 on 2009-03-05
> **MaxIBoy said:**
> 
Anyway, there's a simple way of preventing users from doing stupid stuff like this unless they want to. It's called "not running around as root all the time." (Yeah, I'm looking at *you*, Puppy.)

What would you rather lose, all your important Documents, Pictures, Music, and Videos, or easily replacable system files? Hell, I'd almost rather lose my system files than all my config files like .kde and .openbox :-P My system files aren't important and can be replaced in under an hour. You can still hose all your personal stuff without root and without sudo.

---

### Post by jenkinbr on 2009-03-05
> **MaxIBoy said:**
> DO NOT ATTEMPT ANY OF THESE!

These will delete things cleanly:

[LIST]
[*]rm -rf /
[*]find / -name '*' -exec rm { } ; #this one leaves all your directories, but everything will be empty
[/LIST]

These cause hard drive corruption, which will be probably unrecoverable:

[LIST]
[*]echo "any text at all" > /dev/*d* #where *d* includes sda, sdb, hda, hdb, fd0, fd1, etc.
[*]cat "any text at all" > /dev/*d*
[*]cat any_file_at.all > /dev/*d*
[*]<file.txt > /dev/*d*
[*]dd -if=/dev/amything -of=/dev/anything
[*]cp /dev/zero /dev/anything
[/LIST]

I've only ever used the first one, but I'm pretty sure they'll all work.


You're talking about an awful lot of useful functionality that will need to be sacrificed to stop users from ever messing things up.
A lot of functionality, mind you, that other programs may or may not depend on, in order to save a bit of space.

---

### Post by jenkinbr on 2009-03-05
> **doorknob60 said:**
> What would you rather lose, all your important Documents, Pictures, Music, and Videos, or easily replacable system files? Hell, I'd almost rather lose my system files than all my config files like .kde and .openbox :-P My system files aren't important and can be replaced in under an hour. You can still hose all your personal stuff without root and without sudo.
I've actually been there and done that.  You don't need root permissions to modify files that belong to you.

In my opinion, I would rather hose my system, but still have /home intact, as you said, rather than hose my /home and still have my system intact.  The system is recoverable by re-installing the OS and packages, your data, if not backed up, is irrecoverable, unless you can memorize it all, but 1. That's crazy-talk, and 2. we wouln't need a computer if we could memorize it all, would we?

---

### Post by jdong on 2009-03-05
> **doorknob60 said:**
> What would you rather lose, all your important Documents, Pictures, Music, and Videos, or easily replacable system files? Hell, I'd almost rather lose my system files than all my config files like .kde and .openbox :-P My system files aren't important and can be replaced in under an hour. You can still hose all your personal stuff without root and without sudo.

I wish I still had a thank button for posts like this. You've hit the nail on the head -- kudos.

On a single user system, I bet to you that "rm -rf ~/" is **JUST** as catastrophic as losing everything, or even worse. The OS is easily replaceable from install discs, package lists, or even a 5-month-old pseudo-backup, but your files probably change from day to day and most of your customization happens in your home directory.

Fundamentally if you want to try stupid things that might hurt the system, do it under a limited user account that is not your primary account. This includes running untrusted code, etc.

---

### Post by jenkinbr on 2009-03-05
> **jdong said:**
> I wish I still had a thank button for posts like this. You've hit the nail on the head -- kudos.

On a single user system, I bet to you that "rm -rf ~/" is **JUST** as catastrophic as losing everything, or even worse. The OS is easily replaceable from install discs, package lists, or even a 5-month-old pseudo-backup, but your files probably change from day to day and most of your customization happens in your home directory.

Fundamentally if you want to try stupid things that might hurt the system, do it under a limited user account that is not your primary account. This includes running untrusted code, etc.
Even better - set up a virtual machine that has no access to your system.  Then play all you want, sudo whatever this, sudo whatever that.

---

### Post by MarblePanther on 2009-03-05
> **Giant Speck said:**
> I've heard that Solaris has "rm -rf /" protection.

Why doesn't Linux have this?  Or do some distros actually have it?

That's a great idea!  Those smart people at SUN :)

--

rm -rf  is very handy for removing directories.  The FUD about it being evil is to prevent noobies from following malicious "advice".  It is absolutely essential to a unix-like or POSIX environment.

---

### Post by jdong on 2009-03-05
> **jenkinbr said:**
> Even better - set up a virtual machine that has no access to your system.  Then play all you want, sudo whatever this, sudo whatever that.


I think that definition of "no access to your system" is a lot less warm-and-fuzzy than you might think. I would not trust half of my friends with a virtual machine running on one of my primary systems.

---

### Post by jenkinbr on 2009-03-05
> **jdong said:**
> I think that definition of "no access to your system" is a lot less warm-and-fuzzy than you might think. I would not trust half of my friends with a virtual machine running on one of my primary systems.
You could always set up a spare 'test' machine, but not everyone has one of those...

---

### Post by linuxisevolution on 2009-03-05
So I can remove my windows parititon.

---

### Post by jenkinbr on 2009-03-05
That's what dd is good for...

---

### Post by cardinals_fan on 2009-03-05
I rm -rf a directory almost every day.  Just not my root directory.

---

### Post by adamlau on 2009-03-06
I feel that mkfs is more dangerous than rm -rf.

---

### Post by barbedsaber on 2009-03-06
I used it a couple of times to delete stuff.
made me feel almighty and powerful.

---

