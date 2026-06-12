---
title: "Open dissusion: Huge security risks"
date: 2006-04-25
forum: Server Platforms
---

### Post by beniwtv on 2006-04-25
Hi,

I've created a page in the wiki to talk about two huge security risks in Ubuntu.
Feel free to join it: [https://wiki.ubuntu.com/BeniwtvHotmailCom](https://wiki.ubuntu.com/BeniwtvHotmailCom)

---

### Post by kabus on 2006-04-25
Sorry to be blunt, but I don't think you know what you are talking about.

---

### Post by tribaal on 2006-04-25
I think you misunderstand the way sudo works. You should read [this page]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo"), it has a "the benefits of sudo" section.

Cheers

- trib'

---

### Post by beniwtv on 2006-04-25
I know perfectly what I am talkin about.

The reason is, everyone who executes, in wathever manner, "sudo command" would be able to act as root, since sudo stores the password about 15 minutes.
Therefore, any program installed on your sytem IS able to sudo or gksudo, without asking your permission! I think that is, in fact, a great impact on security. At least, sudo shouldn't store the password (I always add after installing ubuntu timestamp_timeout=0) to do this.

Anyway, thanks for your comments.

---

### Post by nocturn on 2006-04-25
[QUOTE=beniwtv]I know perfectly what I am talkin about.

The reason is, everyone who executes, in wathever manner, "sudo command" would be able to act as root, since sudo stores the password about 15 minutes.
Therefore, any program installed on your sytem IS able to sudo or gksudo, without asking your permission! I think that is, in fact, a great impact on security. At least, sudo shouldn't store the password (I always add after installing ubuntu timestamp_timeout=0) to do this.

Anyway, thanks for your comments.[/QUOTE]


In the 15 minutes after you last sudo'ed, yes, any program that you *manually* installed and ran can use that privilege.

But you are addressing two issues here, which you must make clear:
1# Make sudo require a root password instead of user
2# Set sudo timeout to 0.

I strongly disagree with #1 because that would require a shared root password.   Using the user password has advantages as in you are more likely to update this regularly then a seperate root account and you only need to guard one password well.

Regarding #2, you are correct that this has security implications and setting it to 0 makes the system a little more secure.  Yet exploiting this would require a manual download and execution of malware and is very time dependant.

So, your title "huge security risk" is way out of line.

---

### Post by LordHunter317 on 2006-04-25
[QUOTE=beniwtv]I know perfectly what I am talkin about.[/quote]No, you do not.

Specifically:> Since Breezy (as far as I know), Ubuntu has made a strange progress: In sudo, we're using the user's password instead of the root's. THIS IS A BIG PROBLEM! Almost any virus or spyware could get into our system.**Sudo always, always uses the user's password.  That's intentional.**

I don't want to be giving my junior system administrator complete access to the system just so he can restart Apache.  I want to give him access to only restart Apache, and sudo allows for that.

> I think Ubuntu is going to do what M$ did long time ago: don't care about security on their system because of a moore easy desktop. That is bad! I don't like to see the same security issues with M$ software in Linux.No, that's clearly not the case.  You have no clue what they've done for security.  You have no clue what sudo is even used for.  Frankly, I feel after two errors this gross, you should drop your wiki page and apologize to everyone, but especially the Ubuntu developers.  You're being insulting.

> So, sudo should use the root's password. At install, we could ask the user to enter a password for root. For newbies to Linux, we could add a note why linux has "root", explaining in brief what the strange "root" is, why you should use another password for root as your user's password and why it is so important.Why?  This is a security loss: a second password doesn't make you more secure.  If I can get the user's regular password, I can just as easily get root in any scenario, if that's what I desire.   I may not.

Also, calling it winshit shows what an immature little baby you are, and how little respsect you deserve.  It's really just icing on your little cake. 

[quoite]The reason is, everyone who executes, in wathever manner, "sudo command" would be able to act as root, since sudo stores the password about 15 minutes.[/quote]And?  They can execute as root anyway, because presumably they know their own password.  And if they don't, this isn't an issue.  This statement is a logical fallacy: you're attempting to be alarmist by suggeting something fundamentally evil about having privilege.  The user is supposed to have it.

> Therefore, any program installed on your sytem IS able to sudo or gksudo, without asking your permission!No, they're not.  You don't understand how software works.  Most programs are completely and totally incapable of running arbitrary commands in the first place.

> I think that is, in fact, a great impact on security.No, it isn't.  THe password check in sudo isn't a serious security countermeasure.  Some of us would argue it sohuld be out-and-out removed for systems like the ones Ubuntu is targeting.

---

### Post by beniwtv on 2006-04-25
ok, I agree with you that this problem maybe is seen to huge by me. 

But, at least inflitration of sypware or virus is not impossible. Mac OSX has demonstrated this too. A few years ago someone made a virus for this system, showing this security issue. They don't even had to install it *manually*!, as you pointed out in your post.

Nowadays, we are save - normaly no viruses of spyware is programmed for Linux. But when Linux grows on the desktop, this will occour surely. Actually, virus programmers don't consider programming a virus for Linux because they think that Linux is not used by much people.

There is no risk today, but who knows what's going to happen tomorrow? I am not against sudo, sudo is a great tool that allows you to execute a command as root or another user. I am using it very much.

Many of the security issues on win***s are because M$ makes exceptions - eg. no app can do *some* task in win***s except m$ apps. This is why win***s is vulnerable. I think Linux should not have these exceptions and follow the original spec - "you don't have an user, nor a password for this user - you can't get in!"

It's only a thing to consider for the future - if we want to keep linux without virus and other nightmares we know of will arrive in the future.

---

### Post by nocturn on 2006-04-25
[QUOTE=beniwtv]
But, at least inflitration of sypware or virus is not impossible. Mac OSX has demonstrated this too. A few years ago someone made a virus for this system, showing this security issue. They don't even had to install it *manually*!, as you pointed out in your post.
[/quote]

Can you provide a link to details about this?  
MacOS is not Linux nor Ubuntu incidently.  MacOS has made some tradeoffs that make it less secure actually.

How do you propose a program can make use of the 15 minute window to do bad things unless you downloaded and ran said program?

> 
Nowadays, we are save - normaly no viruses of spyware is programmed for Linux. But when Linux grows on the desktop, this will occour surely. Actually, virus programmers don't consider programming a virus for Linux because they think that Linux is not used by much people.


That's an old argument and a logical fallacy.  Apache has always had a majority share of the webserver market, yet IIS with its niche market is the one being cracked the most.   
Linux and Unix do have a big chunk of the server market, but there you do not see the same issues.

> 
Many of the security issues on win***s are because M$ makes exceptions - eg. no app can do *some* task in win***s except m$ apps. This is why win***s is vulnerable. I think Linux should not have these exceptions and follow the original spec - "you don't have an user, nor a password for this user - you can't get in!"
[quote]

Linux and Unix are more secure because they were designed very differently from Windows.  There is room for improvment (PaX, SELinux, ...) but the current state is not exactly swiss-cheese.
Implementing your suggestions will not make things better.  The only thing that does make sense is the smaller timeout, but it still offers little gain.

[quote]
It's only a thing to consider for the future - if we want to keep linux without virus and other nightmares we know of will arrive in the future.

If we want to avoid that future, we need to look at implementing a MAC system on Linux instead of the current DAC system, we need stuff like SELinux to work out of the box and we need patches like PaX.
We do not need more accounts to protect.

---

### Post by beniwtv on 2006-04-25
*Wiki page has been updated to only my ubuntu history*

I give this threat for closed, because we have heard now good and bad answers, and a conclusion made by me.

There is just one thing to say: Im not insulting the ubuntu developers - they are doing great work developing ubuntu - (and dapper) as usual. I only don't want to hapen what M$ occoured. If someone has the feeling that I insulted him/her, then I apologise.

Thank for your collaboration!

---

### Post by LordHunter317 on 2006-04-25
[QUOTE=beniwtv]ok, I agree with you that this problem maybe is seen to huge by me.[/quote]You're creating a problem that doesn't even *exist*.

> But, at least inflitration of sypware or virus is not impossible.***Your solution doesn't preven that.***  Heck, not having root at all won't prevent that.  They don't need root to replicate.  They don't need root to cause trouble.

>  Actually, virus programmers don't consider programming a virus for Linux because they think that Linux is not used by much people.The number of worms in the wild would suggest you are wrong.

> I am not against sudo, sudo is a great tool that allows you to execute a command as root or another user. I am using it very much.Then why the hell did you do all this?  Your hypocrisy is overwhelming. 

> Many of the security issues on win***s are because M$ makes exceptions - eg. no app can do *some* task in win***s except m$ apps.No, they do not.  You have no clue how Windows security works.  

> I think Linux should not have these exceptions and follow the original spec - "you don't have an user, nor a password for this user - you can't get in!"It does.  Sudo doesn't change that.

> It's only a thing to consider for the future - if we want to keep linux without virus and other nightmares we know of will arrive in the future.No, this doesn't follow at all.  The only way to prevent viruses is to never accept foreign input.

[quote=nocturn]MacOS is not Linux nor Ubuntu incidently. MacOS has made some tradeoffs that make it less secure actually.[/quote]Such as?  I'm not aware of any.

> Apache has always had a majority share of the webserver market, yet IIS with its niche market is the one being cracked the most.You're umm, wrong about that now.  IISv6 has had *two* security issues since launch.  Let's not even talk about Apache.

> Linux and Unix are more secure because they were designed very differently from Windows. There is room for improvment (PaX, SELinux, ...) but the current state is not exactly swiss-cheese.No, they weren't, at least w.r.t. security.  Their fundamental security model is the same and in many ways, Windows implementation of certain features is far more superior.

> If we want to avoid that future, we need to look at implementing a MAC system on Linux instead of the current DAC system, we need stuff like SELinux to work out of the box and we need patches like PaX.MAC is deadweight on the desktop.  You can't provide any security without unreasonably enroaching on the user's freedoms.

---

### Post by nocturn on 2006-04-25
[QUOTE=LordHunter317]
No, they weren't, at least w.r.t. security.  Their fundamental security model is the same and in many ways, Windows implementation of certain features is far more superior.
[/QUOTE]

In most ways, yes the models are the same.  They both use a DAC system, both have access rights etc.

But even WinXP still carries the legacy of the Win95 days to maintain compatibility.  Linux was multiuser and had access restrictions from the beginning, windows was not.

---

### Post by LordHunter317 on 2006-04-25
[QUOTE=nocturn]But even WinXP still carries the legacy of the Win95 days to maintain compatibility.[/quote]No, it doesn't.  XP 64 does not, and cannot.

32-bit NT has always run 16-bit code in a special mode, *because it must*.  The *hardware* requires it.  The code does have some special access provisions to hardware (if you are sufficently privileged, if you're not, you cannot run it) so DOS applications don't break, but they don't suddenly get the whole shebang.  They still operate under the rules of the system.  They're still user-mode applications running under your user, with all the restrictions that implies.
 
>  Linux was multiuser and had access restrictions from the beginning, windows was not.You're totally wrong.  NT has always been multiuser.

---

### Post by nocturn on 2006-04-25
[QUOTE=LordHunter317]No, it doesn't.  XP 64 does not, and cannot.[/quote]

If I do a default install of XP, I can create folders under the root (c:\).  Why?

A lot of programs on XP still do not seperate their code "Program files" from Data (My Documents) because they haven't shifted to the new dogma despite XP being almost 6 years old.  In the same manner, XP (home at least) encourages people to run as root/administrator.

I'm not talking about the 64 bit version specificly BTW.

---

### Post by LordHunter317 on 2006-04-25
[QUOTE=nocturn]If I do a default install of XP, I can create folders under the root (c:\).  Why?[/quote]Why not?  What is the security risk there?

> A lot of programs on XP still do not seperate their code "Program files" from Data (My Documents) because they haven't shifted to the new dogma despite XP being almost 6 years old.That's been prelevant since Win2K.  That's not MS' fault either, it's not like the rules haven't been explained.

> In the same manner, XP (home at least) encourages people to run as root/administrator.Non-sequitur.  You arrived here on a slipperly slope, but I'll still address this: I'd prefer a reduced privilege model that was sane, but a limited account and an Admin account isn't the way to go about this.

> I'm not talking about the 64 bit version specificly BTW.Yes, but it proves you wrong.

---

### Post by beniwtv on 2006-04-25
I agree with you that programs do not need root to cause trouble. But at least, if they can't get into root, they cause less trouble.

> No, they do not. You have no clue how Windows security works. 

What do you know exactly about Windows security? I think you are pretty wrong thinking that windows and linux do the same at kernel level. 

If you develop a program on windows (only using kernel funcions (api)!!) and linux, you will see that it IS different. very different. Windows does not have control over its own apps - it can't even terminate a task without taking 3 hours. 

Linux kernel is different. Or maybe we are both wrong, noone I know has seen the code of windows.

> No, they weren't, at least w.r.t. security. Their fundamental security model is the same and in many ways, Windows implementation of certain features is far more superior.

Tell me one feature that is superior in windows - ??? Filesystem? Memory management? runs faster?  I don't think you know windows very well.

> In most ways, yes the models are the same. They both use a DAC system, both have access rights etc.


I can't see access rights in windows. Sorry. They are very bad implemented if the're any.

---

### Post by LordHunter317 on 2006-04-25
[QUOTE=beniwtv]I agree with you that programs do not need root to cause trouble. But at least, if they can't get into root, they cause less trouble.[/quote]They can still cause all sorts of useful trouble to the attacker, especially on a home desktop.

> What do you know exactly about Windows security? I think you are pretty wrong thinking that windows and linux do the same at kernel level. They are nearly identical, even at the kernel level.  They use the same concepts.  The implementations are different, Windows uses ACLs nearly everywhere, but it's still DAC with capabilities.

> If you develop a program on windows (only using kernel funcions (api)!!) and linux, you will see that it IS different. very different.No, it isn't.

>  Windows does not have control over its own apps - it can't even terminate a task without taking 3 hours. Yes, it can.  The delay that occurs when you attempt to kill a task with task manager is built into task manager and can be shortened.

> Linux kernel is different. Or maybe we are both wrong, noone I know has seen the code of windows.You're wrong because you don't understand how Windows works and you're creating myths in the process.

> Tell me one feature that is superior in windows - ???It's ACL system is infinitely superior to the abandoned POSIX standard, which is what Linux implements.

> Filesystem?It's more featureful than most Linux filesystems, but I won't say it's better.

>  Memory management?Yes, in several ways.  But it's not cut and dry, Linux has distinct positives in other places too.

> runs faster?  I don't think you know windows very well.I umm use it, adminster it and develop for it everyday.

> I can't see access rights in windows. Sorry.Yes, you can.  Even in XP home, you can go on the command line and run CACLS to view the ACLs on any file.

> They are very bad implemented if the're any.Actually, they're an inarguably superior implementation to everything else out there.  More "modern" ACL systems, like NFSv4, are bad copies of NTFS' ACLs.

---

### Post by RavenOfOdin on 2006-04-25
I think LordHunter is just a little bit biased.

---

### Post by LordHunter317 on 2006-04-25
[QUOTE=RavenOfOdin]I think LordHunter is just a little bit biased.[/QUOTE]I think if you'll review my posting history, you'll find it's nothing of the sort.

Now do you have something of value to contribute or should I jsut report you for trolling?

---

### Post by RavenOfOdin on 2006-04-27
[QUOTE=LordHunter317]I think if you'll review my posting history, you'll find it's nothing of the sort.

Now do you have something of value to contribute or should I jsut report you for trolling?[/QUOTE]

Calm the hell down.

Some people like to read what's been going on before they make any contributions, and not everyone is interested in getting their heads bitten off.

That being said, the capability of Windows 2K and up for multi-user support is IMHO fake at best.

---

### Post by LordHunter317 on 2006-04-27
[QUOTE=RavenOfOdin]Calm the hell down.[/quote]Then don't post personal attacks.

> Some people like to read what's been going on before they make any contributions,Then don't post personal attacks.

> and not everyone is interested in getting their heads bitten off.Then don't post personal attacks.

> That being said, the capability of Windows 2K and up for multi-user support is IMHO fake at best.Had you said Win NT 3.5 and eariler, you'd be correct in a sense there wasn't any way to have multiple interactive logins.  So you can't have multiple humans on at once.  

However, even the earliest versions of NT allowed for multiple accounts to be logged in at once, and used that ability.  System services ran under different accounts with higher privilege (e.g., LocalSystem).

But NT 4 and up support not only multiple logins (like all versions of NT) but multiple interactive ones through a nifty little product called 'Terminal Services'.  It's no different from having several people on a UNIX server.  Limited accounts are fully limited and cannot interact with each other's files or  programs unless given privilege to do so.

Citrix in fact, made tons of money in the NT 4 days selling products that enhanced the NT4 terminal server abilities, which were a little raw.

---

### Post by beniwtv on 2006-04-28
Yes, I agree with that. I used Windows NT 4 along with multiple logins.

By the way, I've found an interesting article about Windows Vista, from a man who has done for much time articles about M$ Win***s and isn't against windows in any way:

[http://www.winsupersite.com/reviews/winvista_5308_05.asp](http://www.winsupersite.com/reviews/winvista_5308_05.asp)

Have a look at it and tell me what you think. Hint: Pay special attention to how Vista will implement security.

---

### Post by LordHunter317 on 2006-04-28
[QUOTE=beniwtv]By the way, I've found an interesting article about Windows Vista, from a man who has done for much time articles about M$ Win***s and isn't against windows in any way:

[http://www.winsupersite.com/reviews/winvista_5308_05.asp](http://www.winsupersite.com/reviews/winvista_5308_05.asp)

Have a look at it and tell me what you think.[/quote]It has too many technical innaccuracies to even talk about, including several already brought up by others in this thread.

>  Hint: Pay special attention to how Vista will implement security.I know all about UAP.  I have the same fudamental issues with it that I do with sudo: repeated authentication of an already authenticated user doesn't add security in most cases.

It certainly *never* adds it in the console case: i.e., the user is logging in at the machine proper.  It can add it in the network case: i.e., a remote login service was compromised.  But the reality is that if an attacker can compromise a remote login service, they can probably get root/Administrator/whatever soon enough without the help of sudo or UAP, if they didn't get it already.  So the gain isn't clear-cut, it's questionable.  

The only advantage that is brings is it means that most desktop apps for an end-user won't be running privileged all the time, which is a good thing, as it means flaws in them (e.g., IE, firefox, GAIM) are mitigated to same degree that are on Ubuntu.  That's a worthwhile advantage, but that's it.  It gives no more, and it has all of the same flaws sudo has.  It's just a graphical implementation of the same concept in Windows, with some slight technical differences for those of us writing applications (because it's an API, not just an application, and the way the controls are applied is different).  But it's the same fundamental concept, with the same fundamental conclusions.

---

### Post by beniwtv on 2006-04-28
Yes. But I think asking you two times for permission to delete an shortcut on your (own!) Desktop isn't the way things should be. It doesn't makes sense to me. Maybe it's good that you can't delete files form an other user, but linux has this feature now for years. Anyway, I miss the virtual folders, too. Maybe it would be great if Ubuntu had those folders...

In my opinion, Vista isn't worth the upgarde. Maybe finally I get rid of windows when there's no more support for my legal XP copy.

---

### Post by Jimmey on 2006-04-28
Just to provide my opinion on the matter ( :rolleyes: )

Windows and Linux both support multiple users. Windows can, as well as any Linux based operating system, provide access restrictions.

I think that it's in the implementation of these restrictions, and permissions, that Windows and Linux begin to differ the most. 

On a default install of Windows, the user has unchallanged access to the whole of the system, and it's the down to the user to appropriately set up their accounts priveledges ( or lack of ), in order to secure their system. Most users don't bother.

Linux based systems, on the other hand, establish, right from the start, two user accounts: the root user, and the normal user ( where in Windows, I think that the first user of the system, the user specified during the install, automatically becomes the administrator ). 

It's not in the design of the user accounts and priveledges (etc ) that Windows and Linux differ so much, but rather the immidiate implementation.

I may not be correct in saying this, but I have read that, a non-administrative user of a Windows system that has been set up correctly can run into problems when trying to run programs, and so forth. But I'm not entirely sure.

Feel free to correct me where I'm wrong, LordHunter, and I'm sure you will.

Thanks

---

### Post by LordHunter317 on 2006-04-28
[QUOTE=beniwtv]Yes. But I think asking you two times for permission to delete an shortcut on your (own!) Desktop isn't the way things should be.[/quote]No, i it shouldn't be.  Presumably the worse offenses would be corrected by RTM, this is a beta after all.  The amount of progress MS can make in 4 months in nothing short of incredible.

> It doesn't makes sense to me. Maybe it's good that you can't delete files form an other user, but linux has this feature now for years.**So does Windows NT.  It *always* had it.**  Create two limited accounts if you don't believe me.  Try to have one delete the other's files or kill the other's processes.  You can't do it.  It's not possible.

> On a default install of Windows, the user has unchallanged access to the whole of the system,On XP, sure.

> and it's the down to the user to appropriately set up their accounts priveledges ( or lack of ), in order to secure their system. Most users don't bother.It's a simple as creating a second limited user account, or enabling Administrator and then removing the first account from 'Administrators' and placing it in 'Users' or 'Power Users' as one wishes.

> Linux based systems, on the other hand, establish, right from the start, two user accounts: the root user, and the normal user ( where in Windows, I think that the first user of the system, the user specified during the install, automatically becomes the administrator ).No, not all do.  Ubuntu does not.

> It's not in the design of the user accounts and priveledges (etc ) that Windows and Linux differ so much, but rather the immidiate implementation.It's a question of defaults really.  It's not even an implementation thing.

> I may not be correct in saying this, but I have read that, a non-administrative user of a Windows system that has been set up correctly can run into problems when trying to run programs, and so forth. But I'm not entirely sure.Yes, but this isn't Microsoft fault, but the application developer's.

---

### Post by Jimmey on 2006-04-28
[QUOTE=LordHunter317]No, not all do.  Ubuntu does not.[/QUOTE]

Admittedly, it doesn't create a user account that can be logged into, because by default, the root account isn't active. But it's there as a user, none the less.

I wasn't challenging XPs ability to create a user system similar to that of Linux based operating system. It's just that most users aren't forced to do so, and in most instances, don't.

---

### Post by beniwtv on 2006-04-28
> I may not be correct in saying this, but I have read that, a non-administrative user of a Windows system that has been set up correctly can run into problems when trying to run programs, and so forth. But I'm not entirely sure.


Yes, that is true. I ran into problems even installing some stuff. That is because som apps require the administrator account to install, or at least run (as it could be in Linux).

> Yes, but this isn't Microsoft fault, but the application developer's.

Surely. But the fault is not the code or that the app is buggy, rather any installer should advice the user that the program requires administrator privileges. If the OS denies some action is because that action isn't allowed for this user.

Anyway, being the administrator in windows doesn't let's you do anything. When I connect a TV to my video card, enable the second monitor, all good. But when I disconnect my TV prior to disabling TV out, I get an error telling me that I don't have permission to disable TV out. So, in order to disable it, I must re-connect it. Sounds silly, I know, but that's just what happens. ](*,)

---

### Post by RavenOfOdin on 2006-04-28
[QUOTE=LordHunter317]Try to have one delete the other's files or kill the other's processes.  You can't do it.  It's not possible.
.[/QUOTE]

Wrong.
I was ALWAYS able to do that on XP.

I can't count the times that I went in to task manager to kill processes running on another account -- both accounts had equal privileges.

And as for "delete files", that is quite honestly a laugh. Who the hell keeps all their installed files or files which may affect the system inside the "Documents and Settings" folders? 

Those are the ONLY folders on XP which work on a per-user basis - Bar none, full stop.

Unless that idea becomes more integrated into the system and program files folders - separation, as a reply further up the thread alluded to - I don't see any future for the "multiuser" capability on Windows.

---

### Post by LordHunter317 on 2006-04-28
[QUOTE=beniwtv]Anyway, being the administrator in windows doesn't let's you do anything. When I connect a TV to my video card, enable the second monitor, all good. But when I disconnect my TV prior to disabling TV out, I get an error telling me that I don't have permission to disable TV out. So, in order to disable it, I must re-connect it. Sounds silly, I know, but that's just what happens. ](*,)[/QUOTE]That sounds like a buggy driver to me.  In fact, I'm sure of it.

[quote=RavenOfOdin]Wrong.
I was ALWAYS able to do that on XP.[/quote]You're wrong, and I'll prove it.  Everyone at home can try this.  Start with an administrator account.  Create two *limited* accounts (according to the 'User Accounts' control panel applet, or in just the 'Users' group through Local Users and Groups via MMC).  Start firefox in every instance, using fast-user switching to switch accounts.  Then, in one of the limited user's accounts, run taskkill to attempt to kill the firefox processes.  You'll get output like this:```
C:\Documents and Settings\Test>taskkill /fi "IMAGENAME eq firefox.exe"
ERROR: The process with PID 2804 could not be terminated.
Reason: This process can only be terminated forcefully ( with /F option ).
ERROR: The process with PID 4692 could not be terminated.
Reason: This process can only be terminated forcefully ( with /F option ).
SUCCESS: The process with PID 5032 has been terminated.

C:\Documents and Settings\Test>taskkill /f /fi "IMAGENAME eq firefox.exe"
ERROR: The process with PID 2804 could not be terminated.
Reason: Access is denied.
ERROR: The process with PID 4692 could not be terminated.
Reason: Access is denied.
```Whoopsies.  Looks like a limited user cannot kill another limited user's process or kill an Administrator's process.

> I can't count the times that I went in to task manager to kill processes running on another account -- both accounts had equal privileges.The obvious correct conclusion is both accounts were members of the Administrators group.  This apparently, totally flew by you in your hasty attempt to prove me wrong.  Unfortunately, I know what I'm talking about, and I just proved it.

> And as for "delete files", that is quite honestly a laugh. Who the hell keeps all their installed files or files which may affect the system inside the "Documents and Settings" folders?All my personal data is in Documents and Settings save for a few games.   That's true of a overwhelming majority of corporations too.

> Those are the ONLY folders on XP which work on a per-user basis - Bar none, full stop.Nope, you're sooo totally wrong:```

C:\Documents and Settings\Test>cd "C:\Program Files"

C:\Program Files>mkdir RavenIsWrong
Access is denied.

C:\Program Files>cd C:\WINDOWS

C:\WINDOWS>mkdir RavenIsStillWrong
Access is denied.

C:\WINDOWS>
```Try again.  

> Unless that idea becomes more integrated into the system and program files foldersIt has been, since at least 2000.  I'm pretty sure it was in NT4 too (i.e., the privileges haven't changed one lick) but I'm in no easy position to verify that.

 > separation, as a reply further up the thread alluded toIt's perfectly and totally seperated.  NIST says NT has equal security to several Linux distributions, and they perform tests like I did on a much more thorough and complete scale, as well as performing several thereotical analysies I have not.

> - I don't see any future for the "multiuser" capability on Windows.Only because you're too narrow minded in your rather senseless quest to prove me wrong to actually know what you're talking about.

---

### Post by LordHunter317 on 2006-04-28
Also, I should point out that if a user has 'SeDebugPrivilege' they can kill any process on the system, whether they own it or not.  Only Administrators have it by default, though.

---

### Post by beniwtv on 2006-04-28
[QUOTE=LordHunter317]That sounds like a buggy driver to me.  In fact, I'm sure of it.[/QUOTE]

Yes, that's what I thought too. But is still strange. Can a driver prevent you from doing something so that windows wouldn't let you do it? Can a program give itself rights that windows will use????? Would be strange.

Note here: Disabling tv-out with nvidia tools works. Maybe windows bug? :mrgreen:

---

### Post by RavenOfOdin on 2006-04-28
[QUOTE=LordHunter317]You're wrong, and I'll prove it.  Everyone at home can try this.  Start with an administrator account.  Create two *limited* accounts . . .


Only because you're too narrow minded in your rather senseless quest to prove me wrong to actually know what you're talking about.[/QUOTE]

Oh my god. What the hell is WITH you?!?

I don't know what could have offended you in my post, but you are going WAY over the line and biting my head off -- just like you did in previous posts and have done to quite a few others.

I think you are the one with the senseless quest to be proven right.  You act like your entire life is at stake here, in some twisted and pathetic quest to prove that the security of Windows is not akin to Swiss cheese (see below paragraph) and get the most combative attitude when someone calls you on your posts. Everything here is like a debating competition to you.

The "limited" accounts are NOT THE ISSUE. If it were, then that would be a security problem. The issue is whether or not private accounts and files are private. Don't act like the issue at hand encompasses security in general.

People like you are so much fun to toy with, because they never, EVER, hold jobs for long. If I were you, I'd stop taking the words "You are wrong" as an insult to my intelligence.

Now:

[QUOTE=LordHunter317]
All my personal data is in Documents and Settings save for a few games. That's true of a overwhelming majority of corporations too.
[/quote]

You are confusing the OS layout with the whims of the user.

[QUOTE=LordHunter317]
It's perfectly and totally seperated. NIST says NT has equal security to several Linux distributions
[/quote]

Proof in the form of a link, please?

[QUOTE=LordHunter317]
, and they perform tests like I did on a much more thorough and complete scale, as well as performing several thereotical analysies I have not.
[/quote]

Don't we love to brag?
Who on here truly cares what analyses you've performed?

You can flame me or bitch at me or whatever, I'm done here, and I'm done with you. I'm going to search these forums for an ignore function.

---

### Post by Jimmey on 2006-04-28
> You can flame me or bitch at me or whatever, I'm done here, and I'm done with you. I'm going to search these forums for an ignore function.

You'll not find one that includes ingoring people's posts because they contain content that proves you wrong.

You openly said that he was wrong. He proved himself ( to a degree; some of it was a bit to technical for my liking :P ) to be right. It's what I'd've done in his situation.

I can't see anything in his post that could be considered as "biting someone's head off". 

> The "limited" accounts are NOT THE ISSUE.

They actually were.

> [quote=LordHunter317]All my personal data is in Documents and Settings save for a few games. That's true of a overwhelming majority of corporations too.

You are confusing the OS layout with the whims of the user.[/quote]

He's not.

> Who on here truly cares what analyses you've performed?

I do, you should.

You'll notice LordHunter didn't bite my head off, because I spoke politely, and only addressed the topics of which I was sure of. When I was wrong, I admitted it. If you, and the others that've come to this post had done the same, we'd not be facing this situation. 

There's very little justification for your last post, RavenOfOdin. 

Thanks.

---

### Post by LordHunter317 on 2006-04-28
[QUOTE=beniwtv]Yes, that's what I thought too. But is still strange. Can a driver prevent you from doing something so that windows wouldn't let you do it?[/quote]The driver is in kernel, so ultimately, it can prevent anything but the kernel from interacting with it, if it so chooses.  There's nothing in Windows' security model that compels the kernel to obey root (there's nothing in Linux's model either).

> Can a program give itself rights that windows will use????? Would be strange.I'm not sure what you mean?

[quote=RavenOfOdin]Oh my god. What the hell is WITH you?!?[/quote]Your continued and repeated attacks on my person, plus your continual spouting of mistruths and out-and-out lies, your refusal to admit when you're wrong, and your inability to accept blame that is yours.  I think that about sums it up, forgive me if I missed something.

> I don't know what could have offended you in my post, but you are going WAY over the line and biting my head offI never bit your head off until you personally attacked me, which was your first post in this thread.  I can be perfectly civil when people don't start discussions by insulting me, and when they discuss things in a civil manner and introduce facts after doing  a reasonable amount of checking to verify their correct.  Thus far, you've failed to do both, plus you're continually pinning the blame on me.  

> I think you are the one with the senseless quest to be proven right. No, I don't care if I'm right or not, I'm here to learn and teach others like hopefully everyone else is.  I'm wrong all the time.  I was just wrong 5 minuets ago on my Linear Algebra test, I suspect my homework I handed in today was wrong, and I suspect I'll write some bugs  in my code when I do my job tonite.   I've quite accepted the limits of my human nature and intelligence.

What I will not stand for in achieving tha goal is people who post incorrect statements about any operating system, including Windows.  You and others in this thread made several incorrect statements, and I corrected them.  This is simple.  Cease making incorrect statements and I'll cease correcting them.

> and get the most combative attitude when someone calls you on your posts.Again, had you not started with a personal attack, you'd find I have a different manner.

> The "limited" accounts are NOT THE ISSUE.Yes, they are.  You're claiming they do not exist.

>  If it were, then that would be a security problem.This statement is contradictory.  If the limited accounts are limited, there is a security problem?

> The issue is whether or not private accounts and files are private.They are.  You *admitted* they are. 

> Don't act like the issue at hand encompasses security in general.It clearly does.  The discussion has been about security in general, covering many specific topics in that realm.  Don't deflect.  

See?  That's right there is what upsets me: you're trying to claim we're not discussing something we clearly have been for the last several posts. You're just dancing around the issues, and that irks the hell out of me.  It's bullshit with no reason for it.

> People like you are so much fun to toy with, because they never, EVER, hold jobs for long.Every job I've held I've left of my own will and desire.  Most of my employeers would have preferred to keep me.

But see again? ***That right there is a personal attack.***  I'm not saying, "You can't hold a job."   There's no reason to say that.  There's no reason to even go there.  It's bullshit.  I may be blunt, but I try my hardest to be respectful.

> You are confusing the OS layout with the whims of the user.No, I'm not.  You brought up the claim that users put files all over the place.  I don't see how that's relevant to security seeing how they can't write to system areas in the first place, without privilege, but I answred your statement.  I keep as many files as I can under 'Documents and Settings', where they belong.  Just like you keep them under /home in Linux.

The issue here is you think your claim has some relation to the ongoing discussion about security, but it doesn't.  Had you said, "Limited user can write to system areas and put data there," you'd be on-topic, but wrong.

Letting users write files to arbitrary places in the file system (as long as they're not shared access) isn't a security concern.  We just normally choose to segregate it to a single place for other reasons.  On Linux, /home.  On Windows, 'Documents and Settings', though it doesn't have to be there for either OS.

> Proof in the form of a link, please?[http://www.commoncriteriaportal.org/public/expert/index.php?menu=7&orderindex=1&showcatagories=-1792](http://www.commoncriteriaportal.org/public/expert/index.php?menu=7&orderindex=1&showcatagories=-1792)

> Don't we love to brag?Here we go with the personal attacks again.  Gee, what a surprise.  And it's a non-sequitur anyway, because you took the statement out of context.  The point of the statement was that they've done far more testing than the two little tests I did to prove you wrong, and as such, are far more qualified to make statements about the security of the operating systems in question.  It wasn't bragging at all.  It was an appeal to a higher authoritity.

> Who on here truly cares what analyses you've performed?Anyone who's interested in the truth, as it clearly proves you don't know what you're talking about.

---

### Post by towsonu2003 on 2006-04-30
I felt the need to jump in, not bc of my tech info, but bc of my recent experience with XP. 

After sudoing this and that in ubuntu, I went to my xp (home edition) installation, created a limited user account, and changed my old account to Administrator with password. Logged off, logged in as limited user. To my surprise, nothing worked. firefox crashed once every hour, antihook got totally confused, firewall run away, and worst, "Run as" (su/do in linux) didn't work. 

Rebooted and went to my limited account without first going to administrator: antihook, antivirus, and firewall did not start, "run as" still not working. 

Rebooted (just to be cleaned up from the mess) and went to the administrator account: "run as" isn't there (it should have been), rest is ok although there is weird unstability...

Now, my school uses XP with limited user accounts, and they work (apart from a number of "access denied" errors on start up from HP stuff). But it seems to me that XP's implementation of multiuser does NOT work out of the box. it is more like making your wireless run with ndiswrapper in linux: luck, experience, and most importantly, tweaks are needed. 

So far, Linux' multiuser setup worked out of the box for me, even when I was a 0-day Linux user. On the other hand, I have been using Windows (the way they seemingly developed to be used: root as regular user) for 15 years. 

What am I saying? Linux is multi-user out of the box while Windows is just confused about what to do about it. I'm pretty sure Vista won't solve the solution either with its many numerous pop ups (a tendency MS likes in its products, which gets imported by other software -firefox, for instance, will keep popping up stupid info during first hour of usage-). 

Unfortunately, MS screwed the users when it first became the OS monopoly, by addicting everyone to the root scheme. Now, everyone have to give pop ups so users don't behave uber-stupidly...

---

### Post by LordHunter317 on 2006-04-30
[QUOTE=towsonu2003] To my surprise, nothing worked. firefox crashed once every hour, antihook got totally confused, firewall run away, and worst, "Run as" (su/do in linux) didn't work. [/quote]You have some other problem then.  I've run Firefox for literally days as a limited user professionally.  When I ran that test for RavenOfOdin, I left the second instance running for at least 3 hours before I rmembered to go kill it.

And 'runas.exe' isn't sudo, it's distinctly su.  An sudo for Windows XP exists, but it's a distinct command.

> But it seems to me that XP's implementation of multiuser does NOT work out of the box.Yes, it does.  I've clearly demonstrated it does.  Blaming third-party applications that attempt to run in all accounts and want Administrative privilege to function doesn't prove that claim.

> On the other hand, I have been using Windows (the way they seemingly developed to be used: root as regular user) for 15 years. As I've said in several thread, the corporate world clearly proves this statement is wrong.

> Linux is multi-user out of the box while Windows is just confused about what to do about it.No, it isn't.  Your gross inability to reason here, like others in this thread, is upsetting.  

> I'm pretty sure Vista won't solve the solution either with its many numerous pop ups(a tendency MS likes in its products,No, they don't.

>  which gets imported by other software -firefox, for instance, will keep popping up stupid info during first hour of usage-).No, it doesn't.

> Unfortunately, MS screwed the users when it first became the OS monopoly, by addicting everyone to the root scheme.No, they didn't.   Don't blame broken third-party applications.

---

### Post by towsonu2003 on 2006-04-30
[QUOTE=LordHunter317]Don't blame broken third-party applications.[/QUOTE]
Unfortunately, the failure of third party applications are to be blamed on MS for this instance. Bc of three possibilities:
either 
1. MS doesn't offer enough help (extensive documentation, corporate promotion, and so on) to third parties on how to operate in Windows without root privileges
or
2. No where does MS say (to its lay users) that they shouldn't run applications that do not operate correctly without root privileges. 
or
3. MS cannot reason that promoting non-root use of Windows among its lay users is profitable/useful. This is much like why we keep bashing the hell out of Linspire (non-free version) bc they make non-root account optional in their distro.  

If most of third party software is broken in an OS, that OS is to be blamed for not setting the standards rights. 

As for your denial of the statement "which gets imported by other software -firefox, for instance, will keep popping up stupid info during first hour of usage", I couldn't understand it. In the first hour of first usage, firefox will tell you what to do and what not to do extensively. It is like educating a first-time computer user. This is not firefox's fault though. MS failed miserably in educating its users, and that is an issue for all IT people in corporate world, as well as for your regular "Windows helper" who ends up having to clean up his/her friends' Windows computers. 

If MS was able to educate its users about how and why Windows gets hacked (i.e. viruses, trojans etc) so frequently, IT people in my work place wouldn't have to spend their time in staff meetings telling others not to open arbitrary files in Outlook, or not to install screensavers from unknown sites.

How come a Linux user knows very well that if sudo/su is used freely, the system will get screwed while a Windows user won't care whether s/he is runnig the OS as root? May be bc anytime we see a user playing around with sudo in the forums (any forums), we inform him/her that s/he'll get screwed very soon. On the other hand, such notices cannot be found in MS help documents or promotional material oriented for the lay user (which excludes Knowledge Base articles and such). 

And finally, for your "As I've said in several thread, the corporate world clearly proves this statement is wrong." statement, the actions of the corporate world to secure OSs can't be taken as signs of usability features of that OS. corporate ITs use extensive tweaking to make the OS work like they want it to work. If, on the other hand, you said "all my (not-computer-savvy) friends use limited accounts in their machines for as far as I have known them without any problems", I would have agreed that the OS is fine for out-of-the-box limited user account usage.

---

### Post by LordHunter317 on 2006-04-30
[QUOTE=towsonu2003]Unfortunately, the failure of third party applications are to be blamed on MS for this instance.[/quote]No, they're not.

> 1. MS doesn't offer enough help (extensive documentation, corporate promotion, and so on) to third parties on how to operate in Windows without root privilegesYes, they do.  You get access to MSDN with every copy of Visual Studio sold.  It's been available for free online for ages.  MS offers certification programs on how to properly develop applications for Windows.

You have no clue what you're talking about if really believe that.

> 2. No where does MS say (to its lay users) that they shouldn't run applications that do not operate correctly without root privileges. Nor is it their responsibility to do so.


> 3. MS cannot reason that promoting non-root use of Windows among its lay users is profitable/useful.No, forcing users to use two accounts isn't useful.  It doesn't help the problem.  That doesn't however, let you concluded that MS is promoting third-party developers to not care about security.

> If most of third party software is broken in an OS, that OS is to be blamed for not setting the standards rights. ***But it does set the rights.***  There's nothing stopping me from writing software that requries root on Linux, and plenty of software out there does.

Ultimately, are you going to blame Ubuntu if some third-party application requires root to run, even though it shouldn't?  No.  There's nothing Ubuntu can do about it, and MS has done as much, if not more, than the Linux distributions in documenting their security infrastructure.

> As for your denial of the statement "which gets imported by other software -firefox, for instance, will keep popping up stupid info during first hour of usage", I couldn't understand it.As in, they're not mimicing Microsoft.  I don't know where you ever got that idea.  Browser notifications when sending insecure data and such have been around since the beginning.  That's not an MS-ism in the least.

> In the first hour of first usage, firefox will tell you what to do and what not to do extensively.No, it doesn't.  It simply warns of you potential consequences of your actions that may not be apparent.

>  MS failed miserably in educating its users, and that is an issue for all IT people in corporate world,Education isn't the issue here.  It wouldn't be possible to educate the user as to every situation that will submit data. 

> If MS was able to educate its users about how and why Windows gets hacked (i.e. viruses, trojans etc) so frequently,They umm, do.  Go browse the knowledge base FFS.  There's plenty of stuff all over there.

> IT people in my work place wouldn't have to spend their time in staff meetings telling others not to open arbitrary files in Outlook, or not to install screensavers from unknown sites.If they secured their machines properly, they wouldn't have to do this at all.  Sounds like a competence problem to me, not an OS problem.

> How come a Linux user knows very well that if sudo/su is used freely, the system will get screwed while a Windows user won't care whether s/he is runnig the OS as root?You'll find many Linux users aren't aware of the consequences.  Your statment has a major excluded middle and extrema.  Your stereotypes aren't helping matters.

> May be bc anytime we see a user playing around with sudo in the forums (any forums), we inform him/her that s/he'll get screwed very soon.Umm, we do nothing of the sort.  Can you not read?

> On the other hand, such notices cannot be found in MS help documents or promotional material oriented for the lay user (which excludes Knowledge Base articles and such). No, you're wrong.  Portions of the KB are intended for end user consumption.  Your arbitrary exclusion of matters you don't understand isn't helping you.

>  the actions of the corporate world to secure OSs can't be taken as signs of usability features of that OS. Yes, they can.  It can't be taken as OOB usability, but the discussion was never about that.  This is a simple deflection.

> corporate ITs use extensive tweaking to make the OS work like they want it to work.No, they do not.  Virtually everything they do is documented.

> If, on the other hand, you said "all my (not-computer-savvy) friends use limited accounts in their machines for as far as I have known them without any problems", I would have agreed that the OS is fine for out-of-the-box limited user account usage.Fine, they use Administrator without any problems, clearly proving your basic premise wrong.  Obviously, you don't want me to use inductive evidence.  You won't like it.

---

### Post by beniwtv on 2006-05-02
The problem is not to educate users about security. We can't do that. There are so many situations out there that could happen. Instead M$ should not give you root access per default (as Ubuntu does).

Instead, we should educate (both Ubuntu and M$) users to understand access restriction (ok, only the basics). Why? Read this story:

"Yesterady my father asked me about making a web-page with php (he didn't know really what this is). I told him to use piensasolutions here in spain, wich gives you a linux server. He wanted tobe able to give someone out here an username and password, so that he can see only his own files (not the other user's files). It's like a user in linux, I said. You only have permission to use and/or modify your own files. What???? He didn't know how this is done. He didn't know, that per default you aren't able to access other user's files, since in Windows he'd never seen something like this. He said: Why is M$ hiding that this is possible? M$ isn't hiding this, I said, it only didn't tell you that this is possible."

The problem is user's don't know normally in win***s that they're using an administrator account or that in fact, they could use restricted access. They even don't know what access restriction actually is. Ubuntu, at least, asks you in the installation for an "username" not "root". I think this step could be improved to help users understand why we creating an user, not an administator. Why? See above. They don't know about users when they come from win***s. Ok, a lot of people do know. But many do not, and maybe this step is confusing.

---

### Post by duality on 2006-05-02
I dont see any issue here, plz do some research before making inaccurate statements.

Root access by default? Its your job to secure your system, not Microsofts.

and if your using linux,are you affraid of breaking your own system by having root access? use chroot

---

### Post by LordHunter317 on 2006-05-02
[QUOTE=beniwtv]The problem is not to educate users about security. We can't do that.[/quote]Yes, you can.  It's perfectly doable.

> "Yesterady my father asked me about making a web-page with php (he didn't know really what this is). I told him to use piensasolutions here in spain, wich gives you a linux server. He wanted tobe able to give someone out here an username and password, so that he can see only his own files (not the other user's files). It's like a user in linux, I said. You only have permission to use and/or modify your own files. What???? He didn't know how this is done. He didn't know, that per default you aren't able to access other user's files, since in Windows he'd never seen something like this. He said: Why is M$ hiding that this is possible? M$ isn't hiding this, I said, it only didn't tell you that this is possible."This is a false dichtonomy and an inducative fallacy.  The presence of a single user that doesn't understand privilege doesn't mean all users do.  I will admit there's a sizable class  that doesn't, but they have no reason to either.

> The problem is user's don't know normally in win***s that they're using an administrator account or that in fact, they could use restricted access. They even don't know what access restriction actually is.And frankly, why should they?

>  Ubuntu, at least, asks you in the installation for an "username" not "root".So does Windows XP.  The name is meaningless.

> I think this step could be improved to help users understand why we creating an user, not an administator.You are creating an Administrator, though.  The only difference is not all processes run with privilege.  Your ubuntu account can still do whatever it wishes to the system.

---

### Post by Jimmey on 2006-05-03
[QUOTE=LordHunter317]You are creating an Administrator, though.  The only difference is not all processes run with privilege.  Your ubuntu account can still do whatever it wishes to the system.[/QUOTE]

But, with relevance to the origional topic ( security risks ), the Ubuntu user would need a password to do whatever he/she wishes to the system. Although this still isn't ideal, it means that no-one can just, sit down at your system and screw things up. They'd need to know a password. It also means that no script can get onto your system and screw things up. It'd need to know a password.

---

### Post by beniwtv on 2006-05-03
Yes, indeed. You need a password to do something restricted. This is good.
But many users don't know what users are or why should they create an user, and in fact, why to use a password for their computers. Even if they know they could use a password, they don't.  (Just go out, at least here in Spain, to any small village out there and you will see).

But other users, the few we have here that use linux, are still asking us how to install an antivirus. Why install it? I can't see a reason. Maybe you install Firestarter, that's ok. 

That's what I can see here in Spain. Correct me if that doesn't apply in your region.

My company has about 30 linux and mac osx servers. We set the security up manually on these servers. In the 6 years we have them, we never got infected by a virus, nor we got hacked. Strange, but if you know what you're doing you're save. Even the one win***s-based server has had no mayor problems (ok, it's slow compared to the others).

What do you think about installing firestarter or clamav? (or another program from this category).

---

### Post by LordHunter317 on 2006-05-03
[QUOTE=Jimmey]But, with relevance to the origional topic ( security risks ), the Ubuntu user would need a password to do whatever he/she wishes to the system.[/quote]Which as I pointed out isn't really an effective security measure for local logins.

>  Although this still isn't ideal, it means that no-one can just, sit down at your system and screw things up. They'd need to know a password.They shouldn't be able to login or unlock your terminal without a password, coimpletly destroying any security sudo(1) provides over and above that.

> It also means that no script can get onto your system and screw things up. It'd need to know a password.But it doesn't mean that.  The script can wait for you to run sudo and then launch its attack.  And it can still screw plenty of stuff up, arguably far more important stuff, without being root.  Oh sure, it can't erase /usr or anything like that.  But it doesn't need root to read your home directory and mail off your gnucash files or your SSH private key or a million other things all worse than rendering the system inoperable.

[quote=beniwtv]Yes, indeed. You need a password to do something restricted. This is good.[/quote]But it's not good.  Imagine you have an intrance to a building with double doors.  A guard is posted at both doors.  Both ask you the password one after the other.  That's the situation you're describing.  It doesn't add any security *beause you can't get in the first door without a password anyway*.

> But many users don't know what users are or why should they create an user, and in fact, why to use a password for their computers.Again, false dilemma.  Education is still the correct solution, by someone.

---

### Post by Jimmey on 2006-05-03
> But it doesn't mean that. The script can wait for you to run sudo and then launch its attack. And it can still screw plenty of stuff up, arguably far more important stuff, without being root. Oh sure, it can't erase /usr or anything like that. But it doesn't need root to read your home directory and mail off your gnucash files or your SSH private key or a million other things all worse than rendering the system inoperable.

What you're arguing serves to suggest that there's no way to make any operating system 100% secure. Which's correct. But there're ways to make an operating system less insecure. 

Although, as you've said, Windows can operate in parrallel to any other Linux based operating system as far as user accounts and priveledges are concerned, the fact of the matter is that when you set up a Windows operating system for the first time ( I think, it's been a while since I've done it, or seen it done ), you're given the administrator status. You can do, what you want, unchallanged. It's then up to the user to establish other, less priveledged user accounts. An Ubuntu user can also do what (s)he wants to his/her system, but **is** challanged. The fact that sudo asks for a password only serves to make it harder to screw up your computer.

The stuff in my /home is easily ten times more valuble to me than what's in /usr, you're right. If I managed to screw up some none-/home folder that was needed in order for the computer to operate properly, I'd just re-install the operating system. Simple.

It's different for Windows. **C:\Windows has been payed for.** In some cases, if C:\Windows, or the registry, or something similarly important, gets corrupted, it may cost money to replace. And if a Windows operating system has been set up with just the one, administrative user ( as any non-technically minded person might ), it's easy for these things to become ruined. Any Ubuntu user can mess up their system. But the request of a password is one more hurdle for a script/rotten little git to overcome.

Hmm...That's about it.

---

### Post by LordHunter317 on 2006-05-03
[QUOTE=Jimmey]What you're arguing serves to suggest that there's no way to make any operating system 100% secure.[/quote]No, what I'm arguing is that sudo's password check adds no security for local interactive accounts.  Which is true.

> the fact of the matter is that when you set up a Windows operating system for the first time ( I think, it's been a while since I've done it, or seen it done ), you're given the administrator status.Yes, the first account is on Windows XP.  On 2000 and 2003 Server, you just start with the 'Administrator' account.  But this is no different from other operating systems, like very early versions of Red Hat, OpenBSD, etc.


> An Ubuntu user can also do what (s)he wants to his/her system, but **is** challanged.The challenge part isn't what makes it harder.  The fact you have to elevate privilege in the first place makes it harder.

>  The fact that sudo asks for a password only serves to make it harder to screw up your computer.**No, it doesn't. You have to enter a password *to use* the computer in the first place.**  I can't run sudo without already knowing how to prompt it.  Think about it.

Any arguments that say, "But that prompt will make you stop and think" aren't universally applicable and are therefore specious.  It might, but it's not something you're going to base policy on.

The only place the password adds more security is with remotely-exploitable programs run as your user . That means certain attacks against gaim and firefox can't be used to gain root, because the attacker does not know the password.  But they can still ruin plenty of other things.

That's the only benefit the password has.  But it doesn't stop an attacker with physical access to the console, and it the password doesn't prevent you from doing something dumb.  The fact you have to type sudo in the first place to explictly elevate privilege does.

> It's different for Windows. **C:\Windows has been payed for.**And?  It can be replaced.

>  In some cases, if C:\Windows, or the registry, or something similarly important, gets corrupted, it may cost money to replace.No, it doesn't.  Windows comes with a CD.  OEM installs come with some mechanism for restoring the originally installed system, be it CD, HDD rescue image, etc.  This is entirely false.

>  Any Ubuntu user can mess up their system. But the request of a password is one more hurdle for a script/rotten little git to overcome.But it's not necessarily the case.  I could send a email with a trjoan with instructions on how to download and run it with privilege claimg you'll get free XXX Porn or something when you do so.  You'd get a lot of hits.

It only helps when the attacker can't communicate with the user at all.  If they can talk to the user, they can potentially trick them into yielding the password.  And if they fork() off an attack process and wait, they can still bypass sudo due to password caching.

The fact default sudo policy is to cache passwords should tell you that in fact, it really isn't meant as a strong security measure.  The reality on any system is once an attacker gets in, it's only a matter of time before they get root, generally.

---

### Post by Jimmey on 2006-05-03
> [quote]
In some cases, if C:\Windows, or the registry, or something similarly important, gets corrupted, it may cost money to replace.
No, it doesn't. Windows comes with a CD. OEM installs come with some mechanism for restoring the originally installed system, be it CD, HDD rescue image, etc. This is entirely false.[/quote]

To say that this is entirey false is wrong.

I appreciate that normally, a PC bought with Windows pre-installed should also come with some means of re-installing Windows, like a CD, or a rescue image. That's why I said, > In some cases

because in other cases, they may not be some means by which re-installing Windows becomes a possibility.

> [quote]
The fact that sudo asks for a password only serves to make it harder to screw up your computer.
No, it doesn't. You have to enter a password to use the computer in the first place. I can't run sudo without already knowing how to prompt it. Think about it.[/quote]

Here, you're right. Allow me to correct myself. The fact that sudo asks for a password only serves to make it harder for something else to screw up your computer, on purpose.

> If they can talk to the user, they can potentially trick them into yielding the password.

This step isn't necessary if you're trying to attack the majority of computers running Windows. 

> it really isn't meant as a strong security measure.

But it's a measure, none the less. It's more than that on most Windows user's machines, who ( I must stress ) haven't adiquately established proper user accounts. Which is the majority.

---

### Post by LordHunter317 on 2006-05-03
[QUOTE=Jimmey]To say that this is entirey false is wrong.[/quote]It is.  If you receive an OEM PC without a license and a copy of some reinstall mechanism, the OEM is violating their agreement with MS.  They must give you a way to reinstall Windows (that does not mean a Windows CD).  If they don't give it to you in the box, they're supposed to provide it free of charge.

As such, any cases where it's not happening aren't interesting, as the vendor is already in a doubly-actionable position.

> because in other cases, they may not be some means by which re-installing Windows becomes a possibility.But what other cases?  If you buy windows retail, you have a CD.  If you have volume licensing, they'll ship you CDs even if you lose all of them at a nominal cost (you probably have 80 copies anyway).  We covered OEMs.  That's all the ways to legally get Windows and the scenario you describe doesn't occur.  

It's not real.  Certianly when it does happen, the user has means to acquire Windows legally, at no cost, so it's not worth talking about.

> The fact that sudo asks for a password only serves to make it harder for something else to screw up your computer, on purpose.In certain, limited scenarios.  It's not a uniform mechanism.

> This step isn't necessary if you're trying to attack the majority of computers running Windows. It will be with Vista.  The point is sudo asking for a password doesn't protect you because I can spoof it.  I can just do:```
#!/bin/sh

echo "Enter your password to get free XXX porn"
sudo rm -rf /
```Whoops.  Bringing up Windows here is a deflection, as I was talking specifically about Ubuntu.    If an attacker wanted to target Ubuntu, the extra work required to get a high success rate still isn't a lot.

> But it's a measure, none the less.It's clearly not an extremely useful one though.  As I said, you don't plan your security policy around it.

---

### Post by Jimmey on 2006-05-03
> ```
!/bin/sh echo "Enter your password to get free XXX porn" sudo rm -rf /
```

Whoops. Bringing up Windows here is a deflection, as I was talking specifically about Ubuntu. If an attacker wanted to target Ubuntu, the extra work required to get a high success rate still isn't a lot.

If an attacker wanted to target a machine running Ubuntu, operated by a person who'd like to get free XXX porn, then that'd surely work. But not all Ubuntu users do.

Bringing up Windows isn't a deflection. I'm doing it for comparative purposes. The step you described above wouldn't be necessary to target the marjority of Windows users, and wouldn't work against those Ubuntu users who either do not want to view 'free XXX porn', or who realise that there's usually a direct link between porn, and trouble.

Although the example you made before might have been an abstract one, it's true to say that not all users would reveal their passwords when prompted by something similar to it.

---

### Post by LordHunter317 on 2006-05-03
[QUOTE=Jimmey]If an attacker wanted to target a machine running Ubuntu, operated by a person who'd like to get free XXX porn, then that'd surely work. But not all Ubuntu users do.[/quote]Yes, but I'm sure a sizable portion do, otherwise viagra spams and the like wouldn't be so effective.

> Bringing up Windows isn't a deflection. I'm doing it for comparative purposes.There's nothing to compare.  We've already established that privilege seperation as provided by sudo yields more protection.  The question we're asking now is what feature of sudo provides that extra protection.   Windows can factor 

> it's true to say that not all users would reveal their passwords when prompted by something similar to it.Yes, but many users will, and sudo makes the situation worse.  Why?  Because it desensitizes them to password prompts.

---

### Post by aysiu on 2006-05-03
[QUOTE=LordHunter317]Yes, but I'm sure a sizable portion do, otherwise viagra spams and the like wouldn't be so effective.[/quote] You're saying a sizable portion of Ubuntu users would click on links from viagra spam? There goes your credibility...

---

### Post by LordHunter317 on 2006-05-03
[QUOTE=aysiu]You're saying a sizable portion of Ubuntu users would click on links from viagra spam? There goes your credibility...[/QUOTE]
Somebody's clicking on those links.  If Ubuntu had the marketshare of Windows then yes, a sizable portion of Ubuntu users would click on links from viagra spam.

Obviously, that may not be true at this very moment, but the Ubuntu-using computer population is far too small to make any inferences about the general computing population.

---

### Post by aysiu on 2006-05-03
[QUOTE=LordHunter317]Somebody's clicking on those links.  If Ubuntu had the marketshare of Windows then yes, a sizable portion of Ubuntu users would click on links from viagra spam.[/QUOTE] But people don't use Ubuntu because of what it might be like **if** it had the marketshare Windows has. Ubuntu would be an entirely different experience **if** it had the marketshare Windows has.

It would have more commercial applications ported to it. It would be the standard for Linux distros, so everyone who wrote software for Linux would have to create a binary just for Ubuntu. I mean... the other implications are mind-boggling if Ubuntu has the marketshare Windows has. 

Those "what if" situations aren't really important when talking about security. Yes, if my parents' neighborhood suddenly became as poor as South Boston, then, yes, there would be more crime, and their house might be broken into, and the schools may not have as many resources or offer small class sizes... but my parents live in an affluent neighborhood, and that's why they chose it.

Ubuntu, if it ever did achieve Windows' marketshare in desktops, would not do so for at least three years (and that's being *extremely* optimistic). By then, technology would have shifted a lot. Who knows if Ubuntu would suffer the same security vulnerabilities it does now? Who knows if Windows would?

There's no point in speculating about "what if." Compare Windows now to Ubuntu now. Compare Windows users now to Ubuntu users now. Compare Windows defaults now to Ubuntu defaults now. Anything else is speculation and an unfair comparison.

---

### Post by LordHunter317 on 2006-05-03
> **aysiu]But people don't use Ubuntu because of what it might be like **if** it had the marketshare Windows has.[/quote]Non-sequitur.  People who click on porn spam and viagra links will do so regardless of operating system.  The OS has nothing to do with it, which is my point.  If you can figure out what the user wants, you can trick them into giving them what you want.  This is the fundamental premise of social engineering.

> Ubuntu would be an entirely different experience **if** it had the marketshare Windows has.Do you mean from Windows or from the way it is now?  The obvious answer to both is yes, but it doesn't invalidate my statement above.

> It would have more commercial applications ported to it. It would be the standard for Linux distros, so everyone who wrote software for Linux would have to create a binary just for Ubuntu. I mean... the other implications are mind-boggling if Ubuntu has the marketshare Windows has.Non-sequitur.  How is any of that relevant to the security discussion at hand, and the ability of attackers to social engineer passwords?

> Those "what if" situations aren't really important when talking about security.Yes, they are.  They're very important since security is mostly a game of "what if".

> By then, technology would have shifted a lot. Who knows if Ubuntu would suffer the same security vulnerabilities it does now? Who knows if Windows would?Again, non-sequitur by irrelevance.

You originally attempted to suggest that the hypothetical scenario of stealing a password by asking for it in exchange for free porn showed I have no credibility.  Yet obviously, people will do that all the time said:**
> [*]Users who are savvy enough to know what's going on.  Uninteresting.[*]Users who will never respond despite not knowing what's going on, due to paranoia or the like.  Also unintersting.[*]Users who will always say yes, because they want the free porn or whatever.  They're not just interesting, we know from Windows they're a sizable population.   It's also easy to see this is a social beahvior and the OS has nothing to do with it.[/list]The correct way to counter this is through user education, so users in the latter two classes can be converted to the first class.

> There's no point in speculating about "what if."As I said, that's pretty much all security is, so it's disinegious to suggest it's fruitless to do so.

[quote]Compare Windows now to Ubuntu now. Compare Windows users now to Ubuntu users now. Compare Windows defaults now to Ubuntu defaults now.I made a more than safe assumption about what would happen if marketshare increased.   The point is simple: the peopel who will respond to such attacks are a constant, and the OS has nothing to do with those attacks.  

If they'll download and unzip a file with a trojan in it, they'll be happy to enter their password when prompted.  If they won't do that, then it doesn't matter.  But the point is the OS has nothing to do with it.   Sudo's password won't stop the attacker.  It's not a security measure in this case.  It's absolutely meaningless.

> Anything else is speculation and an unfair comparison.It's clearly not, unless you can show an error in my inference.

---

### Post by aysiu on 2006-05-03
Things are not "non-sequiturs" just because they don't fit into your worldview.

I'm sorry, but you throw around that word a lot, and it doesn't apply most of the time.

By "what if" situations, I'm speaking specifically about your particular "what if" situation--what if Ubuntu had the desktop marketshare Windows has.

I'm not talking about general "what if" situations like "what if someone tried to sniff packets on my network."

You're deliberately providing your own non-sequiturs. Yes, users in great numbers stupidly click on links. I'm just saying that right now users who use Ubuntu tend not to be those people. There's no point in speculating what kinds of people Ubuntu might attract in the future.

If you want to veer off on other tangents and call *my* points non-sequiturs, go ahead. That's what you always do, and it doesn't make you any more correct than if you didn't throw around fancy terms.

---

### Post by LordHunter317 on 2006-05-03
[QUOTE=aysiu]Things are not "non-sequitors" just because they don't fit into your worldview.[/quote]They are though.  **How is having more commerical software relevant to the discussion at hand?**

If you cannot answer that question, then it is a non-sequitur.  It does not follow the terms of the discussion.

> I'm sorry, but you throw around that phrase a lot, and it doesn't apply.
I fail to see what more commerical software has to do with the discussion.

> By "what if" situations, I'm speaking specifically about your particular "what if" situation--what if Ubuntu had the desktop marketshare Windows has.And?  You can't say it's irrelevant, because the attacks do happen.  Just because it's not presently happening in large numbers on a specific platform doesn't mean you don't do the analysis to figure out if they're worth mitigating, and how.

More importantly, as I clearly went and explained the basis for my statement, even if what you said above were true, it doesn't hold here.  More importantly, *you cannot accuse me of speculation without runining your own argument.*  

So it is indeed a non-sequitur.  It does not follow your own argument, because it's contradictory with the rest of it.  If you say, "Not many click and speculation is not allowed", you've invalidated the first half of the sentence unless you provide numbers. Numbers I'm sure you don't have.  As such, you're not allowed to say that.

> You're deliberately providing your own non-sequitors.Show the logical error in my statements then.  I pointed out yours were irrelevant.  What error did I commit?

> Yes, users in great numbers stupidly click on links. I'm just saying that right now users who use Ubuntu tend not to be those people.Wonderful.  The point of the statements were to simply show a manner of attack where sudo is totally ineffective and that the computing population will indeed respond to such attacks in a sufficent number.  No more, no less.  I don't know what will happen in the future for certain, nor do I really care.  Jimmey and I are in agreement here AFAICT.

Whether it's actually happening right now on Ubuntu or now in any quantity is totally irrelevant to my point, as it turns out.  I just have to show the attack vector exists and that it can be exploited.  Just because it's an unlikely occurance doesn't mean it's not something that's worthwhile to plan for.  That's an economics problem, and situationally dependent.

However, I do know that such users do exist on Ubuntu, will most likely increase in number as Ubuntu's marketshare increases, and it is a security problem for them.  Note "sufficent", that doesn't mean large, it just means large *enough*.  Large enough may be 0.01%, for example.  1 in 10 thousands.  It could be 1:1 million for all we know. 

Yes, what will happen in the future is tagential to the original course of discussion.  *But so was your original statement.*

Yes, whether it's a common occurance on Ubuntu or not is speculative.  *But so was your original statement.*

See?  You can't accuse me of any sins you didn't commit as well.

> That's what you always do, and it doesn't make you any more correct than if you didn't throw around fancy terms.Fine.  Your points were simply irrelevant.  Happy?  Doesn't change what they are.

---

### Post by beniwtv on 2006-05-04
> Posted by LordHunter317: 
I just have to show the attack vector exists and that it can be exploited.

Yes, that was the original intention of this thread. And you showed that, in fact, it's possible (as I said off the beginning).

What have we learned so far, then?

Sudo doesn't add much more security to our system. (Look at the bash script from LordHunter317), even if you use root's password.

Windows **does** have good access rights. It only doesn't sets up the users in a good way, if you do a default install. This belongs to the user. (Maybe Vista will?)

You are secure of remote attacks per default in Ubuntu. But, if someone gets into your system, he can in fact screw things up.

We should educate users more about security. Even in Linux, but we can't learn them 100% of the cases (beacuse they're so much).

Linux is still better than win***s :mrgreen: 

That's a first conclusion. Correct me if I'm wrong. Did I forgot something?

---

### Post by Jimmey on 2006-05-04
Would it be better, then, security wise, for the root account to be activated, with the use of sudo requiring the root account's password, instead of the user's?

---

### Post by beniwtv on 2006-05-04
No, it don't. See the code posted by LordHunter317.

Correct me if i'm wrong, but unless you ask the user for his password you can't get it elsewhere (you shouldn't!). Even if you use 'passwd' it asks you for your old password. 

Using the root's password only could make sense if someone knows your password and has physical access to your box.

---

### Post by LordHunter317 on 2006-05-04
> **beniwtv]Sudo doesn't add much more security to our system.[/quote]Well, not quite.  What I said was the password makes no sense for *local interactive* users.  Here are a few situations where the password is useful:[list][*]Exploits in e.g., Firefox, where the attacker can run code but cannot dispaly anything to the user and cannot fork() a daemon or spawn a child process.  Such attacks aren't impossible.  In that case, the password increases security immensely said:**
> Network users who don't use a password to login.  If my SSH keypair is stolen, you still can't elevate privilege directly.  This only really holds for some, not all, situations of keypair or authentication token theft.  It's not a complete countermeasure. [/list]

> (Maybe Vista will?)Vista will use UAP, which thus far seems to be a distinct misfeature.

[quote]You are secure of remote attacks per default in Ubuntu.Well you don't run any services that listen to the Internet.  But firefox and gaim are still exploitable, or anything else that receives malicious data over the Internet.  That includes a couple of remote execution bugs in Firefox.

[quote=Jimmey]Would it be better, then, security wise, for the root account to be activated, and the use of sudo would require the root account's password, instead of the users?[/quote]For a home user?  No.  If I can get their user password, it's pretty likely I can get their root password too.  For responsible users?  It doesn't matter because I shouldn't be able to get their password in the first place, otherwise they would be not responsible.

Unless you had some other reason or scenario in mind. :)

---

### Post by Jimmey on 2006-05-04
Yeah, that's true. I was thinking, for a multi-user Ubuntu system, if you set up a new user, would they automatically be able to use sudo? The situation I stated before would be idea if you'd like to set up an account for a child, say; or for someone you'd not like to have the ability to sudo.

---

### Post by beniwtv on 2006-05-04
[QUOTE=Jimmey]The situation I stated before would be idea if you'd like to set up an account for a child, say; or for someone you'd not like to have the ability to sudo.[/QUOTE]

Then you should use the root password for sudo. Do this by adding the corresponding option to the /etc/sudoers file, at the Defaults line (don't remember exactly: rootpw). You could also (since Hoary) go to users administration and uncheck System tasks line. This is useful only if the user's have a password and they know it, because they don't know the root's password.

---

### Post by LordHunter317 on 2006-05-04
> **Jimmey]Yeah, that's true. I was thinking, for a multi-user Ubuntu system, if you set up a new user, would they automatically be able to use sudo?[/quote]No.  If you create the account on the console you must explictly grant membership in the admin group said:**
> Then you should use the root password for sudo. Do this by adding the corresponding option to the /etc/sudoers file, at the Defaults line (don't remember exactly: rootpw). You could also (since Hoary) go to users administration and uncheck System tasks line. This is useful only if the user's have a password and they know it, because they don't know the root's password.I don't think this makes any sense.  He was asking about creating a second account.

---

### Post by beniwtv on 2006-05-04
[QUOTE=LordHunter317]I don't think this makes any sense.  He was asking about creating a second account.[/QUOTE]

I was talking about the second account and how to prevent it form using sudo. Sorry, if you misunderstood. That's what Jimmey wanted to know, if my English knowledge isn't going completely silly...

---

### Post by LordHunter317 on 2006-05-04
You don't have to do any of that, at least post Hoary (I forget about Warty).  By default, if they're not members of the admin group, they cannot do anything via sudo.  That's it.

---

### Post by beniwtv on 2006-05-04
[QUOTE=LordHunter317]You don't have to do any of that, at least post Hoary (I forget about Warty).  By default, if they're not members of the admin group, they cannot do anything via sudo.  That's it.[/QUOTE]

Yes, sorry. I didn't know that Ubuntu doesn't put you in the admin group by default. (I don't remember last time I've created a new user)

---

### Post by LordHunter317 on 2006-05-04
Well, I don't know what the GUI tool does by default but I do know it has the option.

---

### Post by airtonix on 2006-05-07
man have a bong and chill the hell out

---

### Post by Jimmey on 2006-05-07
[quote=airtonix]man have a bong and chill the hell out[/quote]

The thread had been pretty much dead for two days. And you post this.

** removed namecalling **

---

### Post by RavenOfOdin on 2006-05-07
[QUOTE=Jimmey]The thread had been pretty much dead for two days. And you post this.

You're an idiot.[/QUOTE]

Two months. . .stupid amount of time to wait between replies and/or before posting.
Two weeks. . a little less stupid.
Two days. . .No.

---

### Post by Jimmey on 2006-05-07
[QUOTE=RavenOfOdin]Two months. . .stupid amount of time to wait between replies and/or before posting.
Two weeks. . a little less stupid.
Two days. . .No.[/QUOTE]

If you're defending this post, ** removed namecalling **

---

### Post by RavenOfOdin on 2006-05-07
[QUOTE=Jimmey]If you're defending this post, then you too are an idiot.[/QUOTE]

It has nothing to do with the quality of the post - which I admit is lacking. 

I just stated, basically, that I've seen threads resurrected from a two-month period in which no one has posted -- and there haven't been any complaints even by an admin.  The longest I ever saw a thread go on any forum with this was just above a year and a half, and there was a rule in effect on the forums which stated "instead of making new posts, search for old ones" . . .

Moreover, saying someone is an idiot simply because they object to a senseless exchange borders on stupid.

---

### Post by Jimmey on 2006-05-08
[QUOTE=RavenOfOdin]I've seen threads resurrected from a two-month period in which no one has posted -- and there haven't been any complaints even by an admin. [/quote]

This was hardly a ressurection.

> Moreover, saying someone is an idiot simply because they object to a senseless exchange borders on stupid.

You're right. *Is sorry*

---

### Post by beniwtv on 2006-05-08
[QUOTE=airtonix]man have a bong and chill the hell out[/QUOTE]

If you don't have anything interesting to say, just don't post!

BTW, anyone has to add some more comments? Has someone read the wi***s vista article I've posted?

Let me know.

---

