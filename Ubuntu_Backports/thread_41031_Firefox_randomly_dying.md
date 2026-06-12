---
title: "Firefox randomly dying"
date: 2005-06-11
forum: Ubuntu Backports
---

### Post by kassetra on 2005-06-11
Firefox 1.0.4-1ubuntu2~5.04ubp2 has started randomly shutting itself down.  It usually comes back up relatively well, but sometimes it dumps all of my saved tab sessions as well.

This just started happening after I did the upgrade to ubp2 (thursday, I think.)

---

### Post by desdinova on 2005-06-11
[QUOTE=kassetra]Firefox 1.0.4-1ubuntu2~5.04ubp2 has started randomly shutting itself down.  It usually comes back up relatively well, but sometimes it dumps all of my saved tab sessions as well.

This just started happening after I did the upgrade to ubp2 (thursday, I think.)[/QUOTE]
 Is it perhaps plugin related - I have real issues with Java freezing my browser?

---

### Post by jdong on 2005-06-11
hmm. Please upgrade to ~5.04ubp5 while you're at it. It should start showing up on mirrors soon.

Run Firefox at a terminal, and try to get it to crash. Do you get any terminal output afterwards?

---

### Post by desdinova on 2005-06-11
[QUOTE=jdong]hmm. Please upgrade to ~5.04ubp5 while you're at it. It should start showing up on mirrors soon.

Run Firefox at a terminal, and try to get it to crash. Do you get any terminal output afterwards?[/QUOTE]
 I'm on 1.0.4-1ubuntu2~5.04ubp2 - cool thanks for that - will keep my eyes open - many thanks!

---

### Post by desdinova on 2005-06-11
[QUOTE=desdinova]I'm on 1.0.4-1ubuntu2~5.04ubp2 - cool thanks for that - will keep my eyes open - many thanks![/QUOTE]
 This looks a Java issue as Epiphany/Galeon/FF/Moz all show on my system the same behavior - a java app causes java_vm to suck up all load and > 250 mb of memory and do nothing - attempting to close the tab/window of the applet freezes the browser until you pkill it...

(Just updated to the newest j2sdk and ff above)

---

### Post by skoal on 2005-06-11
hmm...thx for the post.  I'm faced with a tough decision now: stay with current version 1.0.4 w/spoof vulnerability or upgrade to random whackiness.  Hmm...I like a little spice and unpredicatability every now and then, so...1.0.4-1ubuntu2~5.04ubp2 it is!

\\//_

---

### Post by jdong on 2005-06-11
That's really weird guys, I'm using the latest backports FF along with the staging Java JDK, and I don't have any Java applet issues.

---

### Post by desdinova on 2005-06-11
[http://www.walter-fendt.de/ph11e/index.html](http://www.walter-fendt.de/ph11e/index.html)

How do those apps behave for you ? They freeze all my browsers solid?

---

### Post by jdong on 2005-06-11
Yes, they all work for me.

Can you give me your sun-j2re1.5 and/or sun-j2sdk1.5 versions? Also, output of **ls -al /etc/alternatives/firefox-javaplugin.so**

---

### Post by desdinova on 2005-06-11
[QUOTE=jdong]Yes, they all work for me.

Can you give me your sun-j2re1.5 and/or sun-j2sdk1.5 versions? Also, output of **ls -al /etc/alternatives/firefox-javaplugin.so**[/QUOTE]
 ls -al /etc/alternatives/firefox-javaplugin.so

lrwxrwxrwx  1 root root 62 2005-06-11 20:33 /etc/alternatives/firefox-javaplugin.so -> /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

Both j2re and j2sdk listed as 1.50+update03

BTW tried using FF as another user in case it was a profile issue - same behaviour ;-(

---

### Post by jdong on 2005-06-11
Try running **sudo ln -sf /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so**

That might fix it.

---

### Post by desdinova on 2005-06-11
[QUOTE=jdong]Try running **sudo ln -sf /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so**

That might fix it.[/QUOTE]
 Different behaviour

With the j2sdk plugin, I get the sun ray effect but I can swap tabs etc
With the k2re, I can't swap tabs - it just sits there

---

### Post by jdong on 2005-06-11
can you:

1) uninstall + purge both the SDK and JRE
2) remove the /etc/alternatives/*java* entries
3) reinstall the **JRE FIRST**
4) reinstall the SDK.

---

### Post by desdinova on 2005-06-11
[QUOTE=jdong]can you:

1) uninstall + purge both the SDK and JRE
2) remove the /etc/alternatives/*java* entries
3) reinstall the **JRE FIRST**
4) reinstall the SDK.[/QUOTE]
 Doing that now!

---

### Post by desdinova on 2005-06-11
[QUOTE=desdinova]Doing that now![/QUOTE]
 Could I get away with just the jre? I don't know why I installed the j2sdk (I think it was just to test!)

---

### Post by jdong on 2005-06-11
Sure.

---

### Post by desdinova on 2005-06-11
Cool

In approximately 7 mins I'll have an answer for you ;-)!

---

### Post by desdinova on 2005-06-11
Odd

Just noticed the download is getting update02 not 03 - reckon thats an issue?



(using mirrormax.net)

---

### Post by jdong on 2005-06-11
No, that's normal. Backports has JRE 02 and JDK 03. JRE 02 was bug-free, while JDK 02 had the symlink problem. JDK 03 fixes the symlink problem for NEW INSTALLS.

---

### Post by desdinova on 2005-06-11
Thanks - ;-)

---

### Post by jdong on 2005-06-11
BTW, also make sure you're running ~5.04ubp5, which was synced to mirrormax about 2 hours ago.

---

### Post by desdinova on 2005-06-11
[QUOTE=jdong]BTW, also make sure you're running ~5.04ubp5, which was synced to mirrormax about 2 hours ago.[/QUOTE]
 Yep I am - however for some reason the install of j2re didn't put the java entries in /etc/alternatives..... is there a quick way of doing this or should I just ln -sf?

---

### Post by jdong on 2005-06-11
Just ln it.

---

### Post by desdinova on 2005-06-11
Nope no difference - ANY java apps show the pulsating sun-ray logo in the space of the applet - and firefox freezes . I've even tried again after emptying my profile....

Confused now ;(

---

### Post by desdinova on 2005-06-11
Sorry for the delay - my DSL line threw a wobbler for a second

I have a strace available - but the last part of it fills out as

select(33, [32], NULL, NULL, {0, 0})    = 0 (Timeout)
select(33, [32], NULL, NULL, {0, 0})    = 0 (Timeout)
select(33, [32], NULL, NULL, {0, 0})    = 0 (Timeout)
select(33, [32], NULL, NULL, {0, 0})    = 0 (Timeout)
select(33, [32], NULL, NULL, {0, 0})    = 0 (Timeout)
select(33, [32], NULL, NULL, {0, 0})    = 0 (Timeout)
select(33, [32], NULL, NULL, {0, 0})    = 0 (Timeout)
select(33, [32], NULL, NULL, {0, 0})    = 0 (Timeout)
select(33, [32], NULL, NULL, {0, 0})    = 0 (Timeout)
select(33, [32], NULL, NULL, {0, 0} <unfinished ...>

---

### Post by desdinova on 2005-06-11
We have progress

In epiphany and Galeon (yet to test in FF) the app EVENTUALLY loads - its as if I'm back on dialup - and returns control to the browser.....

I'm going to test it tonight with FF with loading an app an dleaving it overnight to see if FF wakes up

---

### Post by desdinova on 2005-06-11
[QUOTE=desdinova]We have progress

In epiphany and Galeon (yet to test in FF) the app EVENTUALLY loads - its as if I'm back on dialup - and returns control to the browser.....

I'm going to test it tonight with FF with loading an app an dleaving it overnight to see if FF wakes up[/QUOTE]
 Nope FF just sits there dead - I'l go back to using Galeon - at least I can use it whilst a java app is loading and it doesn't kill my machine with high loads ;-)

---

### Post by kassetra on 2005-06-12
Last few lines of the strace when ff shut down going to a seemingly random site:
 ```

open("/var/lib/defoma/fontconfig.d/T/TrebuchetMS-Bold.ttf", O_RDONLY) = 45
fcntl64(45, F_SETFD, FD_CLOEXEC)		= 0
fstat64(45, {st_mode=S_IFREG|0644, st_size=123828, ...}) = 0
mmap2(NULL, 123828, PROT_READ, MAP_PRIVATE, 45, 0) = 0xb37df000
close(45)							   = 0
munmap(0xb3696000, 286620)			  = 0
gettimeofday({1118620968, 64894}, NULL) = 0
gettimeofday({1118620968, 65349}, NULL) = 0
gettimeofday({1118620968, 65396}, NULL) = 0
futex(0xb56018a4, FUTEX_WAKE, 1)		= 1
futex(0xb5601894, FUTEX_WAKE, 1)		= 1
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
unlink("/home/kassetra/.mozilla/firefox/dlkf01cy.default/lock") = 0
rt_sigaction(SIGSEGV, {SIG_DFL}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [SEGV], NULL, 8) = 0
tgkill(9298, 9298, SIGSEGV)			 = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

```

---

### Post by jdong on 2005-06-12
Other than these guys, is anyone else having problems with their Firefox?

---

### Post by bored2k on 2005-06-12
[QUOTE=jdong]Other than these guys, is anyone else having problems with their Firefox?[/QUOTE]
 Nope.

---

### Post by jdong on 2005-06-12
hmm, I'll try to rebuild with Hoary GCC, and see where we can get... reverse a few gcc-4 specific patches...

---

### Post by desdinova on 2005-06-12
[QUOTE=jdong]hmm, I'll try to rebuild with Hoary GCC, and see where we can get... reverse a few gcc-4 specific patches...[/QUOTE]
 Thanks mate

---

### Post by kassetra on 2005-06-13
[QUOTE=jdong]hmm, I'll try to rebuild with Hoary GCC, and see where we can get... reverse a few gcc-4 specific patches...[/QUOTE]

Ok, can't even start - segfault on start.

---

### Post by electroglas on 2005-06-13
Mine locked up twice and then killed Evolution!!!

After that it started working...

[http://www.bodo.com/javame.htm](http://www.bodo.com/javame.htm)

---

### Post by kassetra on 2005-06-13
Ahhhh, and Azureus won't stay up for more than three minutes or so (now that I downgraded FF from the staging version) ....

Java?

---

### Post by jdong on 2005-06-13
whoa, Java's affected, too?

---

### Post by jdong on 2005-06-13
**UPDATE**

After a debug session (err, interrogation) with Kassetra, it seems like her problem is hardware/RAM related, since Java and VMWare both exhibit segfaults.


I don't think her problem is related to the other problem being discussed in this thread (Java hangs, new tab hangs).

desdinova, others: Is the new FF in staging (~ubp6) working any better?


Also, are there any stack traces or oopses in your dmesg?

---

### Post by jdong on 2005-06-13
It seems, coincidentally, that all these reports of Firefox issues have come after Ubuntu's recent kernel updates. Could these be the culprit?

Are the victims here using Ubuntu kernels, and pulled the latest update?

---

### Post by kassetra on 2005-06-13
[QUOTE=jdong]whoa, Java's affected, too?[/QUOTE]

Downgrading to the original Hoary kernel has *seemed* to fix the problem, completely.

---

### Post by kassetra on 2005-06-13
[QUOTE=jdong]It seems, coincidentally, that all these reports of Firefox issues have come after Ubuntu's recent kernel updates. Could these be the culprit?

Are the victims here using Ubuntu kernels, and pulled the latest update?[/QUOTE]

After downgrading from the .2 upgrade to the hoary original kernel, all of my issues seem to be completely fixed.

---

### Post by desdinova on 2005-06-13
I'm using

Linux ubuntu 2.6.10-5-k7 #1 Tue Jun 7 10:08:19 UTC 2005 i686 GNU/Linux

---

### Post by kassetra on 2005-06-13
[QUOTE=desdinova]I'm using

Linux ubuntu 2.6.10-5-k7 #1 Tue Jun 7 10:08:19 UTC 2005 i686 GNU/Linux[/QUOTE]

Right, that's the package name, can you tell me the version?  In synaptic, the version number is located just to the right of the package name.  :)

---

### Post by desdinova on 2005-06-13
[QUOTE=kassetra]Right, that's the package name, can you tell me the version?  In synaptic, the version number is located just to the right of the package name.  :)[/QUOTE]
 oops ;-)

Kernel Image is 2.6.10-34.2 (Is that what you mean - I get a few Kernel hits in Synaptic

---

### Post by kassetra on 2005-06-13
[QUOTE=desdinova]oops ;-)

Kernel Image is 2.6.10-34.2 (Is that what you mean - I get a few Kernel hits in Synaptic[/QUOTE]

That's *exactly* what I mean.  Let me walk you through a downgrade.

1. Open Synaptic.
2. Do a search for Linux.
3. Click the little button above the boxes that show you what's been installed.
4. You should see one or two "linux-headers-2.6.10-5" (one with an extra -k7 after it as well, if you're on an athlon.)  You should also see one or two "linux-image-2.6.10-5" (one with -386, possibly, and another with -k7)
5. Click on the first one in the list (for me, it's linux-headers-2.6.10-5) so that it is highlighted.
6. Go to Package->Force Version...
7. In the drop-down box, choose 2.6.10-34 (hoary)
8. Click on the "Force Version" button.
9. Do the same thing for the other ones in this list, "linux-headers-2.6.10-5-k7," "linux-image-2.6.10-5-386," "linux-image-2.6.10-5-k7."  Until all of them are marked with a "downgrade" box (little arrow pointing down.)
10. Click Apply.
11. When finished, reboot.

---

### Post by desdinova on 2005-06-13
Done - but FF still behaves the same = frozen solid when trying to run a Java app - Galeon/Epiphany work aok, if a little slow loading the applet

---

### Post by desdinova on 2005-06-13
I'm a dirty liar ;-)

Whilst typing this in Epihany FF woke up - so it is working - just very very slow....!

---

### Post by desdinova on 2005-06-13
Another change

loading subsequent java apps loads full speed - so its the initial launch thats a problem

---

### Post by kassetra on 2005-06-13
[QUOTE=desdinova]Another change

loading subsequent java apps loads full speed - so its the initial launch thats a problem[/QUOTE]

Right.  I have that issue as well, but I'm guessing that you no longer have any FF dumps?

---

### Post by desdinova on 2005-06-13
Nope behaving like a charm !

(PS Thanks for the synaptic tip - first time with an apt based distro - I've been rpm for a long long while ;-) )

---

### Post by aisowner on 2005-06-13
i just installed ubuntu for the first time yesterday and i noticed that firefox kept dying .. 

noticing something amiss, i decided to update my system. 
things i did included : 

1) used the sources.list from [www.ubuntuguide.org](www.ubuntuguide.org)
2) apt-get update
3) apt-get upgrade
4) apt-get install firefox ( where i could see firefox 1.04 being installed ) 
5) apt-get install linux-686
6) reboot

somehow firefox still dies randomly .. it even died once while I only browsing through this thread.  Another thing i noticed is that if i go to Help.. About Firefox , i see version 1.02 instead of 1.04 .. could that be a reason ? 


I haven't setup Java at all, but I'm sure that isn't the problem.


updated : 

i tried running firefox through a terminal, and when it died, the error was only
"Illegal instruction"

---

### Post by kassetra on 2005-06-13
[QUOTE=aisowner]noticing something amiss, i decided to update my system. 
things i did included
5) apt-get install linux-686[/QUOTE]

It's very possible that you're suffering from the same kernel upgrade issue that we were just talking about on this thread.

---

### Post by desdinova on 2005-06-13
Well so far its been behaving - its definitely still an "initial" issue as shutting down FF and restarting it shows the same slow first load for java, then its fine.

Thanks for this tho - I don't use Java a lot, but its a real pain when occasionally a small applet freezes FF

---

### Post by jdong on 2005-06-13
ok,

1: A bug has been filed in Bugzilla for the kernel upgrade issue. I hope to see it resolved soon. For now, downgrade your kernels :)

2: The slow initial loading: is your hard drive light on during this time? Anything weird in the last few lines of dmesg?

---

### Post by chz on 2005-06-18
[QUOTE=jdong]Other than these guys, is anyone else having problems with their Firefox?[/QUOTE]
 yes...i ran FF through terminal..as it crashed i got this at the terminal...

Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-iso8859-1" to type FontStruct
Segmentation fault

---

### Post by notos on 2005-06-18
[quote=kassetra]That's *exactly* what I mean.  Let me walk you through a downgrade.

1. Open Synaptic.
2. Do a search for Linux.
3. Click the little button above the boxes that show you what's been installed.
4. You should see one or two "linux-headers-2.6.10-5" (one with an extra -k7 after it as well, if you're on an athlon.)  You should also see one or two "linux-image-2.6.10-5" (one with -386, possibly, and another with -k7)
5. Click on the first one in the list (for me, it's linux-headers-2.6.10-5) so that it is highlighted.
6. Go to Package->Force Version...
7. In the drop-down box, choose 2.6.10-34 (hoary)
8. Click on the "Force Version" button.
9. Do the same thing for the other ones in this list, "linux-headers-2.6.10-5-k7," "linux-image-2.6.10-5-386," "linux-image-2.6.10-5-k7."  Until all of them are marked with a "downgrade" box (little arrow pointing down.)
10. Click Apply.
11. When finished, reboot.[/QUOTE]

It Woked for me like a charm but will test it a bit more a report results :)

---

### Post by sapo on 2005-06-18
[QUOTE=jdong]Other than these guys, is anyone else having problems with their Firefox?[/QUOTE]


Same problems here, now i m using opera cause firefox is crashing too often... btw..

My firefox used to crash in flash movies (just stopped and i had to kill the process)and sometimes just to right click and "save target" it crashes and closes everything...

it started when i upgraded to the backports version too...

but i dont have any problems with java applications... just flash and some random crashes  ](*,)

---

### Post by Grimmy on 2005-06-18
I was having problems with Firefox (Segmentation Fault) when looking at hotmail...

Following the instructions by kassetra to downgrade the kernel on the previous page fixed the problem.

---

### Post by jdong on 2005-06-18
**ATTENTION ALL WHO ATTRIBUTE THEIR PROBLEMS WITH THE KERNEL**:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=11824](https://bugzilla.ubuntu.com/show_bug.cgi?id=11824)

A bugreport has been filed, but more information is needed. If you have this problem and would like to help solve it, please respond to the bugzilla.

---

### Post by jahLux on 2005-06-21
[QUOTE=jdong]Other than these guys, is anyone else having problems with their Firefox?[/QUOTE]
Please add my voice to the choir - I'm also experiencing the same F/F issues and am watching the boards for the solution.
U B U N T U still rocks . . . . . . .

---

### Post by jdong on 2005-06-21
Have you tried the kernel downgrade yet? That seems to fix it for practically everyone involved :)

---

### Post by jahLux on 2005-06-21
[QUOTE=jdong]Have you tried the kernel downgrade yet? That seems to fix it for practically everyone involved :)[/QUOTE]
Yea, just finished trying it - and nope, didn't work for me. I continue to wait . . . . .

---

### Post by Technoviking on 2005-06-22
[QUOTE=jdong]Other than these guys, is anyone else having problems with their Firefox?[/QUOTE]
One of my boxes is having this problem.

Mike

---

### Post by bgstratt on 2005-06-24
I'm having this same problem as well, even in other distro's, and before the upgrades, firefox will randomly die with the segmentation fault.  I've read some other threads and some have had success with clearing the cache and other temp files, for me it usually takes a bit before firefox will crash with the segmentation fault as I generally clear it out when I'm done with it, not sure if that has anything to do with it though, I haven't really tested it to see if it is the cache or some other problem.

---

### Post by skoal on 2005-06-24
I've been using kernels 2.6.{8,10,11,12} and firefox 1.04 still pukes every so once and a while...and with no rhyme or reason.  It's not so bad really.  It's forced me to start using this "bookmark" doodad more often now, which is good.  In fact, I just bookmarked this form box reply window I'm typing in right now, just in case I don't get to finish typi...

\\//_

---

### Post by Grimmy on 2005-06-25
[QUOTE=jdong]**ATTENTION ALL WHO ATTRIBUTE THEIR PROBLEMS WITH THE KERNEL**:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=11824](https://bugzilla.ubuntu.com/show_bug.cgi?id=11824)

A bugreport has been filed, but more information is needed. If you have this problem and would like to help solve it, please respond to the bugzilla.[/QUOTE]

I would like to help, but i'm not sure about how to respond?

Looking at the link it looks like I need to add a description of the problem and an attachment of the dmesg output?  I am assuming this is the output when you type dmesg in a terminal (or do I have to do something extra?).  Is this correct?

---

