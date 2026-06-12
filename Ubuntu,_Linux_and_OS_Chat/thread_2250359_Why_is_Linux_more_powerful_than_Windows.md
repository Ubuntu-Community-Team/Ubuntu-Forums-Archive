---
title: "Why is Linux more powerful than Windows ?"
date: 2014-10-28
forum: Ubuntu, Linux and OS Chat
---

### Post by flaymond on 2014-10-28
Why people say that Linux is more flexible and powerful than Windows? Can one of you help me explain why? Im a new user of Ubuntu (Greetings! ):P)

---

### Post by The Cog on 2014-10-28
I think it is because Linux is more configurable. I get the impression that a lot of Windows is locked down - tampering with the internals is not possible.

---

### Post by locustmage420 on 2014-10-28
windows severely handicaps its own command line. it doesnt have the out of the box power or the expandability bash has. windows also fuses their GUI to their backend to the point where most things cannot be done without a graphical user interface. in linux every configuration file can be opened and edited with a normal text editor. try doing that with window. lol youll get alot of " windows doesnt recognize this file type" Just a gimmick to ALSO sell you visual studios and other programming related applications

---

### Post by PondPuppy on 2014-10-28
Well, "powerful" is an ambiguous term. Windows has a more "powerful" application ecosystem in some ways -- at least at present, you can find better video editors, more games, and wider entertainment options (eg, Netflix) than on Linux. On the other hand, Linux is "powerful" because it can be tweaked to do a lot of stuff -- supercomputers are almost all Linux, a majority of webservers run Linux, and desktop computers options are, if not limitless, then very wide-ranging. You can view and edit Windows partitions and files, and even clean a virus-crippled Windows system by using Linux. Linux can be made very secure, and very reliable. Macs have their own "power" sweet spot -- the integration of excellent hardware and solid software makes them user-friendly. Macs have, in my opinion, a beautiful system that works consistently.

And each system has its weaknesses as well. If I could only run one OS, though, I'd run Linux.

---

### Post by wyliecoyoteuk on 2014-10-28
Linux is more scalable, mainly because it is modular.
It is possible to run it on a huge range of hardware,from the router in your house, to Raspberry PIs, right up to supercomputers.
This flexibility means that you can install only what you need.

For example, I use Mythbuntu as my home media server and PVR, which allows me to watch live TV on any device on my home network, and has the most comprehensive scheduling system available, allowing me to record or watch six or seven TVchannels simultaneously from 2 tuners in one PC. The same PC monitors my security cameras using Zoneminder, offers a private web site and and displays a slideshow on a screen in the kitchen. It uses about 25 watts of power.
It was actually much simpler to set this up with Linux than Windows (which I also did for a magazine article), partly because Windows has limitations due to licensing issues.

If you want an idea of how much Linux and BSD ( another Unix-alike OS) are used, go to any large company website and search for "open source software".
an example from Sony:
[http://www.scei.co.jp/psvita-license/](http://www.scei.co.jp/psvita-license/)

---

### Post by pfeiffep on 2014-10-28
Linux is NOT affected nor the target of the latest US Cert altert ... [https://www.us-cert.gov/ncas/alerts/TA14-300A](https://www.us-cert.gov/ncas/alerts/TA14-300A)
> "[COLOR=#333333][FONT=Arial]Since mid-October 2014, a phishing campaign has targeted a wide variety of recipients while employing the Dyre/Dyreza banking malware. Elements of this phishing campaign vary from target to target including senders, attachments, exploits, themes, and payload(s).[/FONT][/COLOR][[1]]("http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2013-2729")[[2]]("https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2010-0188")[COLOR=#333333][FONT=Arial] Although this campaign uses various tactics, the actor&#8217;s intent is to entice recipients into opening attachments and downloading malware."[/FONT][/COLOR]

---

### Post by /ADM on 2014-10-29
Why are we comparing a kernel to Windows? ;)

Seems 'Linux' now means a complete OS, whereas Linux itself is simply the kernel.  It isn't itself more powerful since you cannot use a raw kernel for anything, however what is more powerful is the combination of a kernel with other software (desktop environment, text editors, compilers etc) that makes up a complete Linux-based system.

Now that is more powerful :)

*teaching hat off*

---

### Post by buzzingrobot on 2014-10-29
> **InterProg said:**
> Why people say that Linux is more flexible and powerful thatn Windows? 

That's essentially an unanswerable question, even if everyone agrees on a definition of 'powerful' (which we won't).

Linux and Windows are different operating systems created for different reasons.

Linux was created, in brief, because Linus Torvalds wanted to run Unix and could not afford to buy a Unix license. Unix, created at the famous Bell Labs research facility, dates to the late 1960's and early 1970's. 

Unlike Unix and Linux, Windows had always been a commercial product, and was initially created to provide a rudimentary GUI interface to Microsoft's DOS product. DOS, of course, has long been abandoned and Windows has been built around its own kernel since the NT days.

I'd argue that for ordinary folks, people who simply use a few applications, and shuffle back and forth between them, both Windows and a modern Linux distribution that targets ordinary users (like Ubuntu) are equally useful and 'powerful'.  The differences are going to be in the applications available for each platform, the aesthetics and appearance of the GUI itself, and other subjective things that usually come down to personal preference.

People who need to integrate their computer use with others (say, in an office) will find life easier if they use the same platform as everyone else, whether everyone else uses Windows or Linux or Macs. 

Users can more readily configure surface features -- themes, etc. -- in Linux than in Windows.  System level features in Linux also typically rely on textual config files, too.  Whether or not, on that level, Linux is more configurable via text files than Windows is via the Registry and other approaches is probably impossible to determine, since they are different platforms.

On the other hand, I'd argue that one important measure of a platform's usability is that its out-of-the-box configuration satisfies users without forcing them to spend time tweaking things. Configuration is great, but it can also be  required because designers abdicate their responsibilities to make choices and dump an unfinished product on users.

The tradional DOS-like command.com in Windows can't compare with the shell (usually Bash) in Linux.  Window's PowerShell, though, likely does these days.

---

### Post by SeijiSensei on 2014-10-29
I'll give you an example of the power of the command line.

A client had a mailing list of over 40,000 email addresses in a text file and wanted to (a) eliminate some domains from the list, (b) eliminate duplicates, then (c) sort them by domain.  He tried using a spreadsheet for this task, but I told him I could do it in a couple of seconds from the command prompt like this:
```
tr '[A-Z]' '[a-z]' < mailing_list | grep -v baddomain\.com | sort -t '@' -k 2 | uniq
```
That converts the file "mailing_list" to lower-case, excludes "baddomain.com", sorts by the domain part of the address, then eliminates duplicates.  Tasks like these are pretty easy if you know the basics of Unix utilities like grep, awk, tr, and the like.

As /ADM observed, this type of power is a feature of Unix in general, not just Linux.

---

### Post by grahammechanical on 2014-10-29
There is a sense in which Linux distributions are less powerful than a Microsoft operating system. 

Linux distributions run on less powerful hardware. I would not be surprised if the latest smartphones are more powerful than my desktop machine. And yet I am running the latest Linux-Ubuntu on it and having a good user experience. That is a different kind of power.

If I wanted the latest Apple or Microsoft operating system (which I do not) then I would have to buy the latest Apple or Windows machine. Not so with Linux distributions. Depending on how we look at it, it could be said that with Linux the user is more powerful. Or potentially more powerful.

Regards.

---

### Post by buzzingrobot on 2014-10-29
> **SeijiSensei said:**
> I'll give you an example of the power of the command line.

A client had a mailing list of over 40,000 email addresses...

The thing is, from my point of view, and to be devil's advocate, as soon as you said "client" you moved things away from the realm of the ordinary mainstream user.  I.e., people who would not have a 40,000-strong mailing list and who would not bring in outside help.

I'm not formulating an argument that the basic tool set is not powerful. Just that I think ordinary mainstream users ought to expect that they can do the things they need to do without resort to a shell and without resort to outside help. (Obviously, I'm excluding enterprise and other institutional users from my definition of 'mainstream'.)

The flip side, then, is that I think migrating to Linux because Bash and the rest of the tool set are there is not a very good reason to migrate to Linux *unless* someone wants to specifically learn Unix/Linux at that level.

The corollary, then, is that distributions that both target mainstream use and tout their command-line cred are working at cross-purposes.

---

### Post by pfeiffep on 2014-10-29
+1> **grahammechanical said:**
> There is a sense in which Linux distributions are less powerful than a Microsoft operating system. 

Linux distributions run on less powerful hardware. I would not be surprised if the latest smartphones are more powerful than my desktop machine. And yet I am running the latest Linux-Ubuntu on it and having a good user experience. That is a different kind of power.

If I wanted the latest Apple or Microsoft operating system (which I do not) then I would have to buy the latest Apple or Windows machine. Not so with Linux distributions. Depending on how we look at it, it could be said that with Linux the user is more powerful. Or potentially more powerful.

Regards.Another aspect of power is the amount of time one invests in fully incorporating the hardware / os / productivity software. One might argue that a Windows solution is more straight forward , albeit costly. I prefer to apply my time incorporating rather than my money.

---

### Post by sffvba[e0rt on 2014-10-30
> **/ADM said:**
> Seems 'Linux' now means a complete OS, whereas Linux itself is simply the kernel.

Call me (and most people you will find on this forum) "negative in the freedom dimension" but when we say linux we do mean a complete distribution of linux and not just the kernel.  But I will also except GNU/Linux to mean the same thing ;)

---

### Post by Warren Hill on 2014-10-30
> **buzzingrobot said:**
> ... distributions that both target mainstream use and tout their command-line cred are working at cross-purposes.

While I agree that the majority of mainstream computer users don't want to know about the command line or creating Python, Pearl or using Bash scripting I don't agree here it depends who we are targeting.

We can target the power user by extolling the values of the command line in Linux over the equivalent in Windows while simultaneously targeting the mainstream user by pointing out most of the software they are currently paying for has free equivalents they can install from the software centre.  They don't have to worry about viruses anywhere as much as you do with Windows.  You can use an older machine.  That if they get into trouble there are excellent web sites such as the Ubuntu Forums that are full of people who are happy to give them help.

The command line is very powerful and while I may ask a newb to run certain commands in a terminal to help me diagnose their particular problem I don't expect casual users to have much (if any) knowledge of the command line.  Power users however will often use the command line in both Windows so it's fair to compare the two environments.

The question is asking why Linux is more powerful than Windows so I think SeijiSensei is making a valid point.

If the question was asking why should we encourage mainstream users to ditch Windows and migrate to Linux then it would be less valid; but that's not the question.

---

### Post by SagaciousKJB on 2014-10-31
> **/ADM said:**
> Why are we comparing a kernel to Windows? ;)

Seems 'Linux' now means a complete OS, whereas Linux itself is simply the kernel.  It isn't itself more powerful since you cannot use a raw kernel for anything, however what is more powerful is the combination of a kernel with other software (desktop environment, text editors, compilers etc) that makes up a complete Linux-based system.

Now that is more powerful :)

*teaching hat off*

GNU is better than Windows.  But I definitely think there is MUCH more support for Linux than for HURD or FreeBSD/OpenBSD.  I know a guy who is a Minix freak though.


I think the BIGGEST thing about GNU/Linux is the ability to use a transparent operating system.  Windows deliberately cripples part of the transparency in order to use proprietary code.  Meanwhile if you use Linux, simply as a user with basic coding knowledge you can use "strace" on a buggy program to discover what specifically the problem is, and even modify the source code of the offending program to fix the program yourself.  Basically with enough knowledge and research most problems on Linux are solvable.

In contrast, on Windows, if you have enough money to study various premium Microsoft documentation you might be able to gleam the same type of operational insight but even then you're not really going to have the same level of control.  I like the distinction between kernel and operation system, because with GNU/Linux users have the ability to patch and modify their own kernel, basically updating in place what takes Windows years between each release to do.

Other people here make really good points about the user interface being much more powerful with Linux than with Windows.  There is essentially nothing that you cannot script, automate and fully control on your system with the command line.  Beyond that, there's usually more straight-forware systems that offer you greater levels of control than Windows would.  Remember "scheduling a a task" and how annoying that point and click setup was?  Take a look at cron jobs, you can basically setup a completely automated system.  On top of that, the bash envronment offers a HUGE amount of power with scripting, I've done some pretty wild things.  I had ad CGI code that range up a script that would set off the "beep" command on my PC so that my friends could wake me up lol

It is not really easy to describe why to stick with a *nix OS after switching from Windows.  Once you get use to a system where you are "free" to do anything you want to it, provided you have the knowledge to do so, it really sucks to go back to an operating system that is basically "You get what you get when you get it and you're screwed until that happens."

The truly amazing thing with a GNU/Linux envrionment is that even if YOU don't have the knowledge to fix a problem, chances are that someone else did and has already fixed it for you.  It may seem like I'm suggesting that if you learned how to program and could fix bugs in intriciate programs yourself, but most of the times it's WAY simpler.  Basically down to following a tutorial on how to patch and upgrade a particular module or MAYBE if things get really scary your kernel, but window doesn't even offer 1/8th of that control and that's not even 1/100th of the control that a *nix operating system offers.

@buzzingroot

I hear what you're saying and I agree.  However, ask yourself this... When is the last time you actually paid for Windows?  You don't have to answer that here, but just ask yourself.  That's one reason that I love Linux, beacuse I NEVER had the money to actually buy Windows, and even if I did I never would.  The fact is that most of the things that Windows can do, Linux can do for free--and a lot of times way better.

The only thing that Windows actually has a grip on still is the grahpical video game market.  Because of DirectX there's going to continue to be a marginal difference in the gamiing experience between Linux and Windows, and with that being one of the sole remainding things that fuels the deskop/laptop computer market that's kind of the crux of a lot of things.

---

### Post by MartyBuntu on 2014-10-31
> **SagaciousKJB said:**
> However, ask yourself this... When is the last time you actually paid for Windows?  You don't have to answer that here, but just ask yourself.  That's one reason that I love Linux, beacuse I NEVER had the money to actually buy Windows, and even if I did I never would.  The fact is that most of the things that Windows can do, Linux can do for free--and a lot of times way better.

What about users wishing to pay for Linux based products?

Crossover? Paid Redhat support? Paid Canonical support?

---

### Post by buzzingrobot on 2014-10-31
Well, you pay for Windows everytime you buy a machine with Windows preinstalled.

In the 1990's, Red Hat, Suse and some other vendors did sell their Linux distributions in retail outlets, in nice shrinkwrapped boxes. The fact that users have a right to the source code meant, of course, that their only sales hook was the convenience of avoiding a great deal of compilation and setup time. Moving to a business that sells support subscriptions to enterprise users was a much better idea.

---

### Post by SagaciousKJB on 2014-10-31
> **buzzingrobot said:**
> Well, you pay for Windows everytime you buy a machine with Windows preinstalled.

In the 1990's, Red Hat, Suse and some other vendors did sell their Linux distributions in retail outlets, in nice shrinkwrapped boxes. The fact that users have a right to the source code meant, of course, that their only sales hook was the convenience of avoiding a great deal of compilation and setup time. Moving to a business that sells support subscriptions to enterprise users was a much better idea.

I actually bought Redhat 7 in those nice shrink-wrap setups.  I had dial-up so I didn't really have much other choice lol  Man that seems like forever ago, Linux desktop world has defintely come a LONG way since then.

---

### Post by fballem on 2014-11-01
I think that 'powerful' is a loaded word. Having been, at one time, a Windows guru and now being an Ubuntu desktop user (and having been so for several years), I'd like to share some thoughts:

[LIST=1]
[*]I recently had to do a re-installation of Windows 7 on to one of the machines that I own. It was an installation to bare metal, with Windows 7 and Microsoft Office 2010. I had the data saved on to an external drive, so once the installation was done, I could copy the data into the appropriate directories from the External drive.
[LIST=1]
[*]Windows 7 and Microsoft Office took the better part of a day, because after I installed, I had to update, and do more updates, and ...
[*]I also ended up going to the nVidia site for the graphics drivers, the Logitech site for the drivers for my webcam, keyboard, mouse, and trackpad, Adobe for the Flash Player and PDF Reader, Oracle for Java, and a few other sites.
[*]I also had to install anti-virus software, which is not commonly needed in Linux.
[*]Restore the data.
[*]Major components of a Windows installation, such as Windows, Microsoft Office, Adobe Flash, Adobe Reader, nVidia graphics, and the Logitech drivers, are updated from individual sites and the update process is different for each.
[*]Because the code for Windows, Office, and most other programs is closed, there are relatively few people who are capable to correct any defects or security issues that are discovered.
[/LIST]
[*]Each Linux distribution is different. I have primarily worked with Ubuntu, so that is what I am most comfortable with. I can do a bare metal installation, including data restore and all updates, in about 4 hours.
[LIST=1]
[*]With Linux, you set up your repositories (I set up repositories for LibreOffice, VLC, Gimp, Themes, and Oracle Java). Once these are setup, the Ubuntu update process captures them all.
[*]I happen to like the Unity desktop. There are a lot of people who don't. If you don't like Unity, then you can opt for GNOME, KDE, and quite a few others. It depends on what you chose to install, but the updates are done in the same way as Ubuntu.
[*]For an average user, there is sufficient flexibility in the various Linux distributions, to accommodate whatever they are most likely to require. Some distros are easier than others, some are more highly polished than others, but there are a number of options.
[*]In terms of defects, there are so many people with access to the source code that someone will know how to fix it and be able to introduce a patch. The process, these days, is well controlled, but the size of the population who are experts and can fix the problem is so much larger than Microsoft or Apple could afford.
[/LIST]
[/LIST]

It is a matter of choice, but I could make the argument that Linux (or more properly GNU/Linux) is more 'powerful' for most people than either Windows or Apple.

Hope this helps,

---

### Post by wyliecoyoteuk on 2014-11-01
> **pfeiffep said:**
> +1Another aspect of power is the amount of time one invests in fully incorporating the hardware / os / productivity software. One might argue that a Windows solution is more straight forward , albeit costly. I prefer to apply my time incorporating rather than my money.

Depends on the task some tasks are more time consuming and fiddly on one Platform compared to another.
Try changing the Display settings on a Mac when it mis-configures a HDTV.
Windows is not always the simplest solution.
I can have a Linux web server up and running on LAMP far more quickly than a Windows one on IIS and MSSQL, and the basic setup is more complex.
A lot of obstacles in Windows are artificial, i.e. due to licensing restrictions, and at the whim of the vendor.
E.g. SBS2003 insisted on 2 network cards, SBS2008 refused to use more than one.
The labyrinthine Licensing structure is a big failing of Windows, you can often spend more time trying to figure out which version and how many licenses you need than actually installing the software.

---

### Post by flaymond on 2014-11-02
So..the conclusion is if an OS loaded up with important softwares and others need...it will become a powerful..machine....and...from what i see...you guys said that Linux is kinda 'powerful' because the Terminal (can save hundreds hours with just typing a single command line). I'm learning C++ now (well...8 of 10 peoples suggest me to use the language because the new features and slightly easy understand to learn it). Well, if im wrong....explain to md...e please....i'm new to ubuntu and Linux-like OS...its very confusing..and complicated...and...if someone that kind to teach me...to use ubuntu and programming.....please..I really need help...(I need to fix my grammar)...All help are greatly appreciated! and Thx for discussing in this thread....i got a lot of knowledge just from reading your replies. :)

---

### Post by pfeiffep on 2014-11-02
> **InterProg said:**
> So..the conclusion is if an OS loaded up with important softwares and others need...it will become a powerful..machine....and...from what i see...you guys said that Linux is kinda 'powerful' because the Terminal (can save hundreds hours with just typing a single command line). I'm learning C++ now (well...8 of 10 peoples suggest me to use the language because the new features and slightly easy understand to learn it). Well, if im wrong....explain to md...e please....i'm new to ubuntu and Linux-like OS...its very confusing..and complicated...and...if someone that kind to teach me...to use ubuntu and programming.....please..I really need help...(I need to fix my grammar)...All help are greatly appreciated! and Thx for discussing in this thread....i got a lot of knowledge just from reading your replies. :)
It all depends on exactly what you really want to use the computer for; and how much you want to spend.
Installing the desktop version of Ubuntu comes with most of the productivity software packages required - for free. Generally Ubuntu will run on hardware that is a bit older and just might perform as wall as brand new hardware with proprietary operating systems. IMO this make Linux more powerful.
If you want to learn programming for administering web servers the choice is less clear.
On the other hand, if you want to learn programming to support end users the sheer number of Windows users might help make your decision.
Bottom line is you need to decide your focus and refine your question so that the answers are also more focused.

---

### Post by buzzingrobot on 2014-11-02
> **InterProg said:**
> ...you guys said that Linux is kinda 'powerful' because the Terminal (can save hundreds hours with just typing a single command line...

I don't believe anyone who actually uses Linux would make that claim.

In Linux, the command line -- more correctly, the program running in a terminal, usually Bash -- is a shell that takes input from a user and acts on it.  The GUI's in use in Linux, and in OS X and Windows, are also shells that do exactly that: take input from the user and act on it. GUI's are typically easier because they present a visual display of the options available to a user, while using a command line requires you to know the option, or, more usually, know where to look them up.

We can write scripts that can be executed by Bash.  That's something that GUI's can't offer. (Although OS X does permit results generated by one GUI tool to become input to another GUI tool, if using the Automator tool.)

Windows has two command-line shells.  The first is the tradition command.com, which emulates and expands on the capabilties of MSDOS. The second is the newer Powershell, which, I understand, is quiet powerful and scriptable.

There are many reasons to switch from Windows to Linux.  A desire to learn and use the Bash shell can be one of them.  But, we do not need to use the command line to successfully use Linux. Likewise, if someone just wants to explore using a shell and is otherwise satisfied with Windows, it has two on offer.

---

