---
title: "Hypothetical virus for Ubuntu"
date: 2006-10-15
forum: The Cafe
---

### Post by IYY on 2006-10-15
A user (who uses su or sudo, but is not root) downloads an executable program and runs it. The program creates a directory ~/.virus and adds it in the beginning of the path in his .bashrc. Now, the virus copies all (or just some of the most commonly used) programs that are often used with sudo to ~/.virus and modifies them (injection of binary code or adding something to the source and compiling a new binary) to record the sudo password. At this point, the password can be sent home to the attacker, or used by the virus automatically to do ... anything to the system.

My question: is this possible? Have I missed something? :-k

---

### Post by nalmeth on 2006-10-15
Sure, though I don't think the author of the virus would be so conspicuous to leave ~/.virus

The problem is the users use of su/sudo, as long as he/she is tricked into giving up the password, a cracker wouldn't have to be so clever to cause great harm. 

On a somewhat related note, wasn't there a bug in Breezy where the users password was stored in a file viewable by anyone? I'll post the link if I find it

---

### Post by IYY on 2006-10-15
Well, the point here is that the user will not actually enter the sudo password when running the untrusted program. (and .virus is just an example. It could be hidden deep inside .themes or something) Instead, he will run a program as a regular user, thinking that it's perfectly safe, and the program will later steal the sudo password.

---

### Post by aysiu on 2006-10-15
[Here's that link,](http://ubuntuforums.org/showthread.php?t=143334) Nalmeth.

I don't know all the technical details, but my feeling is that if you're running random executables from untrusted sources, your computer is going to be compromised sooner or later.

---

### Post by GeneralZod on 2006-10-15
I see nothing wrong with your analysis, and it's a pretty hard vector to guard against.  In fact, the only thing I can think of is that sudo be modified to check your current $PATH to make sure that "common" root-only executables (e.g. apt-get) are not "hidden" by identically-named executables that reside in a path writable by non-root users, and to issue a warning if such a "shadow" executable is found.  This is far from elegant/ foolproof, though.

---

### Post by DoctorMO on 2006-10-15
hmmm, we basicly have a list of known safe software and all the files involved in those programs. if someone where to come up with a stupid user computer checker that could be run on computers via a cron job just to check for things such a .bashrc modifications, cron modifications and files which don't belong to any packages and are executable.

That wouldn't stop damage being done by a virus but it would stop one from remaining in the system. the biggest threat is when it goes into the cron because those system crons run as root unlike .bashrc which runs as the user and they'd have to type in their password all the time to allow the virus to do more harm or send more spam.

Obviously the programs outlines above wouldn't be useful to a technical user whos compiling things but they should know better.

---

### Post by nalmeth on 2006-10-15
I see, I misunderstood the sentence.

Here is that thread, stickied in the Security & Servers section:
[http://ubuntuforums.org/showthread.php?t=143334](http://ubuntuforums.org/showthread.php?t=143334)

I don't quite understand how this virus would work though, can you explain in greater detail?

---

### Post by IYY on 2006-10-15
Well, the virus can work in two ways once it's set up:

1. have its own version of, say, gnome-terminal which grabs the password when it is typed.

2. have its own versions of commands commonly run with sudo (things as simple as apt-get) and add to them viral code that will be executed as root as soon as the user tried to run these programs.

---

### Post by DoctorMO on 2006-10-15
nah, I'd just alias sudo in .bashrc then you just capture the password from the command line.

but then thats going to be limited to advanced users anyway.

---

### Post by argie on 2006-10-15
> **IYY said:**
> Well, the virus can work in two ways once it's set up:

1. have its own version of, say, gnome-terminal which grabs the password when it is typed.

2. have its own versions of commands commonly run with sudo (things as simple as apt-get) and add to them viral code that will be executed as root as soon as the user tried to run these programs.
Neither of these should work, in my opinion.

1. When the user opens the terminal, he'll be running /usr/bin/gnome-terminal, and the virus won't have permissions to modify that until it has the sudo password. 

2. As above.

I can think of a third way though. It modifies the script that runs at startup (which is in the home directory?) to run another part of itself which logs all keys entered (a normal keylogger), then poof?

Fortunately, the way package management is in ubuntu (and I guess other debian based OSes), you have trusted repositories. So you use the trusted repositories :)

---

### Post by IYY on 2006-10-15
> nah, I'd just alias sudo in .bashrc then you just capture the password from the command line.

but then thats going to be limited to advanced users anyway.

That, I believe, is actually guarded against.

---

### Post by aysiu on 2006-10-15
> **DoctorMO said:**
> hmmm, we basicly have a list of known safe software and all the files involved in those programs. if someone where to come up with a stupid user computer checker that could be run on computers via a cron job just to check for things such a .bashrc modifications, cron modifications and files which don't belong to any packages and are executable. Isn't that what a rootkit hunter does? Or does that not do that for the /home directory, too--only systemwide files?

---

### Post by Bloodfen Razormaw on 2006-10-15
> My question: is this possible? Have I missed something?
You missed the fact that on a good OS you install software from a secure, trusted repository, rather than downloading it from an arbitrary web site.  There is no need to download and run an arbitrary executable.

---

### Post by prizrak on 2006-10-15
SELinux and all your worries are gone

---

### Post by aysiu on 2006-10-15
> **Bloodfen Razormaw said:**
> You missed the fact that on a good OS you install software from a secure, trusted repository, rather than downloading it from an arbitrary web site.  There is no need to download and run an arbitrary executable.
What you're describing isn't the OS--it's the user, who's smart enough to use what the OS has offered.

---

### Post by IYY on 2006-10-15
> You missed the fact that on a good OS you install software from a secure, trusted repository, rather than downloading it from an arbitrary web site. There is no need to download and run an arbitrary executable.

`Here, just grab automatix from this URL'

---

### Post by aysiu on 2006-10-15
Let's not have this turn into an Automatix-bashing thread.

I'm not saying it has--I'm just telling people not to make it one.

---

### Post by Bloodfen Razormaw on 2006-10-15
> **aysiu said:**
> What you're describing isn't the OS--it's the user, who's smart enough to use what the OS has offered.
A user smart enough to open a Terminal and type sudo <command> is smart to click Add/Remove Programs.  In fact, since the later is discoverable while sudo is not discoverable at all, he is almost certain to stumble upon the later first.

---

### Post by aysiu on 2006-10-15
I don't agree.

A user smart enough to open a terminal and type *sudo <command>* has the skills necessary to click Add/Remove Programs but may not actually be smart enough to use only Add/Remove Programs and not additionally download and try to install potentially sketchy software.

I'm talking "street smarts" here--not "book smart."

---

### Post by Bloodfen Razormaw on 2006-10-15
If you assume that, given two options, he is also willing to install software in a substantially more tedious, difficult, and slow manner.  There are just too many conditions that have to be met for an average user to fall for this.  I think you are arguing whether or not this *can* work; my point is that it is not likely to.  You won't get more than a small percentage of people.

---

### Post by red_Marvin on 2006-10-15
> **IYY said:**
> That, I believe, is actually guarded against.
I made a test and put an alias for sudo in .bashrc and it worked.

A fix (I think) would be to edit the /etc/sudoers file to not allow regular users to execute alias with sudo as a parameter.

This is something I believe the developers should be made aware of, maybe they could change the default sudoers file to include such a fix...

---

### Post by IYY on 2006-10-15
> I made a test and put an alias for sudo in .bashrc and it worked.

A fix (I think) would be to edit the /etc/sudoers file to not allow regular users to execute alias with sudo as a parameter.

This is something I believe the developers should be made aware of, maybe they could change the default sudoers file to include such a fix...

Can you show me your alias? Because I tried making one in my .bashrc and it didn't work.

---

### Post by Bloodfen Razormaw on 2006-10-15
> A fix (I think) would be to edit the /etc/sudoers file to not allow regular users to execute alias with sudo as a parameter.
 
 This is something I believe the developers should be made aware of, maybe they could change the default sudoers file to include such a fix...
That doesn't do anything.  sudoers doesn't know that when sudo is executed whether or not it was done through an alias.  You would have to edit bash to stop that.  And even then, such a malicious program could, since it has root privileges, link any such random program to sudo and call that instead.  And it certainly does nothing to stop PATH manipulation, or injection of malicious code into the actual sudo binary.  The bottom line is that if you are running untrusted executables with root privileges, the best you can do to stop it is some SELinux policy-making.

---

### Post by red_Marvin on 2006-10-15
Bloodfen Razormaw:
What I meant wasn't to put a stopper on who and what uses sudo in which way but who and what uses the alias command with wich parameters.

IYY:
alias foobar='echo some stuff'

---

### Post by aysiu on 2006-10-15
> **Bloodfen Razormaw said:**
> If you assume that, given two options, he is also willing to install software in a substantially more tedious, difficult, and slow manner.  There are just too many conditions that have to be met for an average user to fall for this.  I think you are arguing whether or not this *can* work; my point is that it is not likely to.  You won't get more than a small percentage of people.
That I can agree with.

We're talking about what's possible, not probable.

---

### Post by IYY on 2006-10-15
> IYY:
alias foobar='echo some stuff'

oh, I see. You mean to alias not sudo itself, but some programs that are commonly run as admin. That wouldn't really work. For example:
```

$ alias top='echo hi'
$ top

hi

$ sudo top

<the regular output of top>
```

---

### Post by DoctorMO on 2006-10-15
yes and now do alias sudo='~/malicous.app' and now run sudo ls

---

### Post by red_Marvin on 2006-10-15
Bloodfen Razormaw:
I can't find alias in the ordinary places for linux binaries and no manpage either. Is alias built in into bash? If so then I understand what you mean, which makes this an even more urgent problem.

IYY:
No I that wasn't what I meant but I didn't want to write the exact command I used because of the security risk (public forum)

---

### Post by Ramses de Norre on 2006-10-15
Yes, alias is indeed a bash built-in.

---

### Post by IYY on 2006-10-15
> **DoctorMO said:**
> yes and now do alias sudo='~/malicous.app' and now run sudo ls

```

ilya@muddy:~$ alias sudo='rm -f /etc/somefile'
ilya@muddy:~$ sudo ls
rm: cannot remove `/etc/somefile': Permission denied

```

The alias is not executed as root.

---

### Post by Ramses de Norre on 2006-10-15
Try with sudo in front of the alias command.
```
ramses@icarus:~$ touch test
ramses@icarus:~$ alias sudo='sudo rm -rf /home/ramses/test'
ramses@icarus:~$ sudo
ramses@icarus:~$ ls test
ls: test: No such file or directory
ramses@icarus:~$

```

Note: I didn't get a passwd prompt because it was still cached in sudo.

EDIT: any way to unalias a command??:D Rather then restarting the shell.

---

### Post by red_Marvin on 2006-10-15
IYY:
No of course it isn't, but that isn't the intention either.
Don't make me regret this, but
alias sudo='~/badstuff &&'
where badstuff is an application that imitates the password prompt and records the input = the password(!) and then uses it.

Now the question is if the real password prompts are locked so that it can only get input from a direct physical keyboard or if it can be redirected to get input from another program. If it can be redirected we're in trouble... EDIT: DOH It can...

---

### Post by IYY on 2006-10-15
unalias to remove an alias.

And yes, this method does work... [-(

---

### Post by IYY on 2006-10-15
red_Marvin: how did you manage to read password from a pipe?

---

### Post by DoctorMO on 2006-10-15
You don't have to do the thing the user wants with the sudo ;-) make a script which provides a fake password prompt.

---

### Post by IYY on 2006-10-15
I wrote that already, and I can indeed get a password. However, I am wondering whether or not it is possible to use this recorded password to automatically do things as root: install programs, add users... This is what will make the virus really dangerous, on a mass scale.

---

### Post by chaosgeisterchen on 2006-10-15
Hmh.. virusses.

What about some script startet as sudo which simply does **sudo rm -rf /***?

---

### Post by IYY on 2006-10-15
Everybody already knows that if you run something with sudo it can do anything. The scary thing here is that you can run something without sudo and still get fscked up!

---

### Post by chaosgeisterchen on 2006-10-15
This is propably the main problem. And if this type of vulnerability is not fixed Linux could get bad problems..

Propably Windows is such a maze of code because of all the attempts to keep virusses out?

---

### Post by Alpha_toxic on 2006-10-15
I just want to mention that even if you make an alias of a program
like that
```
alias ls=free
```
then
```
sudo ls
```
does not care about the alias and runs the original command (so no problem here). Though you realy can "alias sudo=sth_bad".
sth_bad could be a script that does sth like that:
get the args, get the pass, send the pass *somewhere*, "sudo args...pass" (so the user will not notice anything strange).
even better the sript may install ssh and create another user with root previlages...

/obveous way to fix - make sudo unaliasable (does this word exist? :tongue:)

---

### Post by Ramses de Norre on 2006-10-16
@Alpha_toxic: it's logic that "sudo ls" wont run the alias because the command is ran as root and the alias is set as regular user. So you need to set the alias explicit for root or you need to alias "sudo ls" to "sudo free" to get your example to work.

---

### Post by red_Marvin on 2006-10-16
My suggestion for how to solve this vulnerability would be to let the administrator set up a file for commands not allowed to alias, much like /etc/sudoers.
To do this one would have to patch bash, but I don't know who to contact...

---

### Post by Seq on 2006-10-16
The vector for attack does not just need to be a user carelessly installing things. Firefox often has "remote code" exploits found, though none to my knowledge have ever been used. The payoff for creating some sort of firefox/linux attack would be small, I think.

Anyway, I was more curious about possible issues with gksudo, as even non-experienced users use this from time to time (System\Administration\*). I had a look at the entries in the Administration menu, and gdmsetup appears to not use path information (synaptic, for example, is called using the full path). Already having a user-writable folder in my $PATH (~/bin), I did not add a special one, though a malicious script could. I created a gdmsetup here, logged out, and logged back in. 

This did not work, which is good, but I am curious as to what the exact circumstances are. Does gnome-panel not process ~/.bash_profile? Does it process ~/.profile? Is there another place that one can place path information that gnome-panel will use?

My other thought was what about adding a misleading item to run on session start?

gksudo -D "System Update" "zenity --info --text 'Type \'ps aux\' in a terminal before closing this notice to determine which user \'zenity\' belongs to.'"

If you have an already active sudo token, type `sudo -k` to clear it and see the prompt -- although an already active token skipping the password is still dangerous.

**Update:** Now that I've wound down from work, I realized that the $PATH issues encountered with my first gksudo test (with gdmsetup) are similar to attempting to the earlier attempts to sudo an aliased command -- root does not have the required $PATH...

---

### Post by Seq on 2006-10-16
> **red_Marvin said:**
> I made a test and put an alias for sudo in .bashrc and it worked.

A fix (I think) would be to edit the /etc/sudoers file to not allow regular users to execute alias with sudo as a parameter.

This is something I believe the developers should be made aware of, maybe they could change the default sudoers file to include such a fix...

I think the problem is that it would need to be bash that disallows a sudo alias, not sudo. As far as sudo knows, it is called normally.

Modifying bash would cause problems as well for users that actually do want to alias sudo, or to run sudo through an alias, though the first of these two would be, I am assuming, uncommon at most. Also, please ignore the fact that the second alias is actually longer than the command...

alias sudo="sudo -H /some/dir"
alias sudokill="sudo -k"

---

### Post by MrWizard on 2006-11-08
Sorry for posting in a dead thread.  But the conversation seemed to stop mid-stream, with no resolution.  Plus, I'm curious and new to Linux/Ubuntu and trying to learn :)

So, my question is this.  Wouldn't the simplest solution be to change the owner of ~/.bashrc to root (and maybe make this the default for new users?)?  That way, a malicious program would need to be run with sudo or as root to modify the .bashrc file.  This would protect against FireFox exploits, for example.  If a user installed a malicious program intentionally, with sudo, of course this would still be a problem - but that is probably always going to be the case to some extent.  The focus should be protecting the user against unseen exploits and vulnerabilities rather than the "Do you want to install this virus?" variety of "vulnerabilities", yes?

So did I miss something, or is this about right-ish?

---

### Post by thibeaz on 2006-11-08
why are you asking this question? Are you trying to design a virus for linux? what good is that going to achive? If your going to make a virus just design one for windows....Actually design one that would change windows to linux...*drool* I'd like that virus

---

### Post by IYY on 2006-11-08
> Sorry for posting in a dead thread. But the conversation seemed to stop mid-stream, with no resolution. Plus, I'm curious and new to Linux/Ubuntu and trying to learn

So, my question is this. Wouldn't the simplest solution be to change the owner of ~/.bashrc to root (and maybe make this the default for new users?)? That way, a malicious program would need to be run with sudo or as root to modify the .bashrc file. This would protect against FireFox exploits, for example. If a user installed a malicious program intentionally, with sudo, of course this would still be a problem - but that is probably always going to be the case to some extent. The focus should be protecting the user against unseen exploits and vulnerabilities rather than the "Do you want to install this virus?" variety of "vulnerabilities", yes?

So did I miss something, or is this about right-ish?

Yes, this will solve the problem but will take away quite a lot of freedom from the user. Modifying the bashrc file gives you the power to change the execute path, which is a very basic thing Linux users expect to be able to do.

If Ubuntu does not allow this, it cannot possibly be seen as a serious distribution.

> why are you asking this question? Are you trying to design a virus for linux? what good is that going to achive? If your going to make a virus just design one for windows....Actually design one that would change windows to linux...*drool* I'd like that virus

The reason that Linux is so secure is that most hypothetical hacks and exploits have been found by friendly hackers rather than malicious ones, and have been fixed before any harm was done. Ignoring such exploits is what Windows developers do.

---

### Post by thibeaz on 2006-11-08
That Much I do know. Appearently there is a why though to hack in a linux system to cause havoc. But I think that was just to scare people. but yes I most definetly agree with you.

---

### Post by MrWizard on 2006-11-09
> **IYY said:**
> Yes, this will solve the problem but will take away quite a lot of freedom from the user. Modifying the bashrc file gives you the power to change the execute path, which is a very basic thing Linux users expect to be able to do.

If Ubuntu does not allow this, it cannot possibly be seen as a serious distribution.
It doesn't take that freedom away.  It just means you'll have to type in your password if you're going to modify the file.  It wouldn't take away your ability to change the path, or add aliases, etc., unless I'm missing something (which is entirely possible, btw - like I said, I'm new at this).

In fact, I tried it and it seems to work fine.  I did the following:
```
garfield@wobl:~$ ls -l .bash*
-rw------- 1 garfield garfield 10303 2006-11-08 00:57 .bash_history
-rw-r--r-- 1 garfield garfield   220 2006-10-20 17:56 .bash_logout
-rw-r--r-- 1 garfield garfield   414 2006-10-20 17:56 .bash_profile
-rw-r--r-- 1 garfield garfield  2227 2006-10-20 17:56 .bashrc
garfield@wobl:~$ sudo chown root:root .bashrc
garfield@wobl:~$ ls -l .bash*
-rw------- 1 garfield garfield 10303 2006-11-08 00:57 .bash_history
-rw-r--r-- 1 garfield garfield   220 2006-10-20 17:56 .bash_logout
-rw-r--r-- 1 garfield garfield   414 2006-10-20 17:56 .bash_profile
-rw-r--r-- 1 root     root      2227 2006-10-20 17:56 .bashrc
garfield@wobl:~$ sudo vi .bashrc
```
Then I uncommented the "ll" alias, saved, closed vi, closed the terminal, and reopened the terminal, and ll worked fine.

---

### Post by Jussi Kukkonen on 2006-11-09
> It doesn't take that freedom away. It just means you'll have to type in your password if you're going to modify the file. It wouldn't take away your ability to change the path, or add aliases, etc., unless I'm missing something (which is entirely possible, btw - like I said, I'm new at this).
Do not assume all users have sudo rights.

---

### Post by boban on 2006-11-09
It think it would work...:rolleyes: 

In .bashrc you add alias sudo='script'. script first runs sudo _your_command, then run sudo install_malware, unalias, then removes malicious alias from .basrc.

I hope there is something wrong with my logic here... :)

---

### Post by MrWizard on 2006-11-09
> **Jussi Kukkonen said:**
> Do not assume all users have sudo rights.
Oh.  Good point.  Arg.  Well, at least it is a nice easy fix for me, since I'm the only one using my computer.  I suppose the choice would be between this security hole and a user's ability to modify their bashrc script.  My assumption was that someone who knows enough to do that would probably have sudo rights.  But you're right, that is just an assumption, and probably inaccurate in some situations :p

---

### Post by red_Marvin on 2006-11-09
If I knew how to contact the bash developers I would suggest that they made a it possible for root to set up a list for which commands are aliasable by which user (or something like that).
Much like /etc/sudoers.

- Process .bashrc...
- Compare found alias entries commands+uid+gid with /etc/aliasers...
- If user/group is allowed to make the specific alias, then add it to the list...

The man page lists a bug-bash47gnu.org for bug reporting would that be the right way to contact them?

**EDIT: the vulnerability has already been posted at [http://groups.google.com/group/gnu.bash.bug/browse_thread/thread/a6af5d26eda84a4c/627b100e7c1d65bb?lnk=gst&q=alias+security&rnum=1#627b100e7c1d65bb](http://groups.google.com/group/gnu.bash.bug/browse_thread/thread/a6af5d26eda84a4c/627b100e7c1d65bb?lnk=gst&q=alias+security&rnum=1#627b100e7c1d65bb)**
Seems that they're not going to do anything against it...

---

### Post by Jussi Kukkonen on 2006-11-09
red_Marvin, think it through before submitting a bug report. I'm not convinced this is just a bash/alias issue -- couldn't you do this kind of sudo-tricks in many other ways too (assuming the user runs a trojan)? Like this:
```
mkdir ~/.evil-bin
echo "echo doing evil stuff here.." > ~/.evil-bin/sudo
chmod +x ~/.evil-bin/sudo
PATH="~/.evil-bin/:"$PATH

```
Try running sudo after that... I'm guessing there are even more ways to do this.


EDIT: the google groups answer pretty much summed it up: 
[QUOTE=Bob Proulx]
This is not practical.  You are trying to enumerate all possible
evils.  That set is too large.  It is infeasible to enumerate a
complete list of possible attacks.[/QUOTE]

---

### Post by red_Marvin on 2006-11-09
Yeah, I didn't send anything after I read the answer on usenet...

Oh well I guess we just have to be catious about which programs we trust...

Another thing is that only the _admin_ should get in a position where [s]he is asked about the terminal, and hopefully [s]he is smart enough :) ...

---

### Post by MrWizard on 2006-11-09
[quote=red_Marvin]Oh well I guess we just have to be catious about which programs we trust...[/quote]
The problem I have is if an exploit in, say, Firefox would allow the editing of the bashrc script.  If this is possible, then it would not take the installation of untrusted software for the bash script vulnerability to become a problem.

---

### Post by red_Marvin on 2006-11-09
I see your point, however, then it would be a problem with *that* program though...

---

### Post by picpak on 2006-11-09
Could a virus store a local copy of fakeroot in your home folder, and control your computer like that?

---

### Post by MrWizard on 2006-11-09
> **red_Marvin said:**
> I see your point, however, then it would be a problem with *that* program though...
Quite true - I don't at all disagree.  My point is simply that Ubuntu (or whatever OS you're using) should do its best to minimize the impact that can be made by somone exploiting a security hole in a valid piece of software.

Edit:  Oh, and please don't take this as a criticism of the Ubuntu devs.  I'm a huge fan and am amazed by what they've put together (I made the switch 3 weeks ago from XP and haven't looked back).

---

### Post by AlphaMack on 2007-02-04
I didn't want to bring back a dead thread, but...
[http://www.ubuntuforums.org/showthread.php?p=2101235](http://www.ubuntuforums.org/showthread.php?p=2101235)

...in light of [MOAB 21-01-2007](http://projects.info-pull.com/moab/MOAB-21-01-2007.html).

---

### Post by Sunnz on 2007-02-04
> **Jussi Kukkonen said:**
> Do not assume all users have sudo rights.

Why would you worry about non-sudoers running a script that relies on... sudo!!:lolflag:

Anyway, you can disable alias all together and it won't do anything. A malicious script can still add ~/.evil_dir into the path, and put a script called sudo in there and hack away.

However if you are paranoid you can always do /usr/bin/sudo instead of sudo and none of the path/alias hack will work.

---

### Post by Rick 1 on 2007-02-04
> **GeneralZod said:**
> I see nothing wrong with your analysis, and it's a pretty hard vector to guard against. In fact, the only thing I can think of is that sudo be modified to check your current $PATH to make sure that "common" root-only executables (e.g. apt-get) are not "hidden" by identically-named executables that reside in a path writable by non-root users, and to issue a warning if such a "shadow" executable is found. This is far from elegant/ foolproof, though.
Yes but this does not eliminate the ability to hijack sudo itself. sudo performs an inordinate number of sanity checks but if a trojan sudo is running instead?
[http://rixstep.com/2/20070204,00.shtml](http://rixstep.com/2/20070204,00.shtml)

---

### Post by Rick 1 on 2007-02-04
> **Sunnz said:**
> Why would you worry about non-sudoers running a script that relies on... sudo!!:lolflag:

Anyway, you can disable alias all together and it won't do anything. A malicious script can still add ~/.evil_dir into the path, and put a script called sudo in there and hack away.

However if you are paranoid you can always do /usr/bin/sudo instead of sudo and none of the path/alias hack will work.
/usr/bin/sudo only guards against sudo being hijacked. /usr/bin/sudo ls - what if there's a trojan ls? Then you go right into a root shell and it's game over. The issue isn't with sudo - it's with $PATH and the ability to corrupt it.
[http://rixstep.com/2/20070201,00.shtml](http://rixstep.com/2/20070201,00.shtml)

---

### Post by Rick 1 on 2007-02-04
> **argie said:**
> Neither of these should work, in my opinion.
Oh but they do. They've been tested on Dapper Drake and the results are impeccable. It's not about Ubuntu or any system: it's about how the shells (bash et al) can be corrupted.

---

### Post by Rick 1 on 2007-02-04
> **Bloodfen Razormaw said:**
> You missed the fact that on a good OS you install software from a secure, trusted repository, rather than downloading it from an arbitrary web site. There is no need to download and run an arbitrary executable.
So someone else gets roasted instead of you? [img]http://ubuntuforums.org/images/smilies/icon_smile.gif[/img] There is no such thing as software that's trusted before it's run. There have been trojans and pranks put in software from commercial vendors; there's ken's famous trick with the C compiler; there's the attack Debian discovered a few years ago. There is no such thing as software that's 'always' been trusted. You're just passing the buck - and sidestepping the issue.

---

### Post by Rick 1 on 2007-02-04
> **aysiu said:**
> What you're describing isn't the OS--it's the user, who's smart enough to use what the OS has offered.
The user is innocent here. It's the shell and sudo running together that create the cock-up. Your alternative is to run consistency checks every five minutes and each time you want to run any command with sudo in it. Each time.

---

### Post by Sunnz on 2007-02-04
> **Rick 1 said:**
> /usr/bin/sudo only guards against sudo being hijacked. /usr/bin/sudo ls - what if there's a trojan ls? Then you go right into a root shell and it's game over. The issue isn't with sudo - it's with $PATH and the ability to corrupt it.
[http://rixstep.com/2/20070201,00.shtml](http://rixstep.com/2/20070201,00.shtml)
/usr/bin/sudo /bin/ls; just like it is said in that article.

---

### Post by Rick 1 on 2007-02-04
> **Bloodfen Razormaw said:**
> A user smart enough to open a Terminal and type sudo <command> is smart to click Add/Remove Programs. In fact, since the later is discoverable while sudo is not discoverable at all, he is almost certain to stumble upon the later first.
I'm sorry but this is the third idiotic comment you've posted on the same page. After this I am outta here. Either take the time to know your subject matter as IVY who started this thread (and who is thinking very clearly indeed) or watch what others have to offer.

'Smart enough' to open a Terminal? If you consider opening a Terminal as requiring intelligence, I think you've said too much about your general abilities and computer use in particular.

You have to understand that admins who are going to use a Terminal all the time have to have the same protections as you do - or more. And they cannot be expected to continually be looking over their shoulders for every fricking command they issue - open all the profile files, echo $PATH, etc. How would you like it if for every command you issued you had to manually inspect the output from echo $PATH? Hello?

Your cockamamie logic - I appreciate you're trying to work through it with the (severely) limited knowledge and experience you have, but don't you think you might try to learn something before you go off on a tangent with your half baked speculations?

---

### Post by Rick 1 on 2007-02-04
> **Bloodfen Razormaw said:**
> There are just too many conditions that have to be met for an average user to fall for this.
Then I sincerely hope some nasty soul picks on you so you learn your lesson. Not that they harm you - just that you wake up. You have attack vectors all over the place. You're trying new code all the time. Unless you actually inspected every line of code in your OS and compiled and linked everything yourself, you can never know. And as ken demonstrated, even then it might not be possible to know. You need a rude awakening. I hope it's not too rude, but it has to be a shaking of an awakening. Your rose coloured glasses are going to net you a world of trouble if you don't get a clue and fast.

---

### Post by argie on 2007-02-04
> **Rick 1 said:**
> 
[quote=argie]Neither of these should work, in my opinion.
Oh but they do. They've been tested on Dapper Drake and the results are impeccable. It's not about Ubuntu or any system: it's about how the shells (bash et al) can be corrupted.[/QUOTE]

Just for the recordL That post was in ignorance, you need not waste your energy trying to convince me I'm wrong ;)

---

### Post by xhaan on 2007-02-04
I just figured out a way to use a bashrc alias to run very nasty commands without the user even knowing about it...

It basically abuses the sudo password timeout. I'm NOT going to say how to do it here but an attacker would need no special permissions to do this... just a simple shell script hidden somewhere.

I made it so when I did sudo ANYTHING, it used my password for a second -hidden- sudo command to delete a test fille that I had set up to verify that it works.

this is scary.

---

### Post by Sunnz on 2007-02-04
Can you guard against it by running /usr/bin/sudo every time?

It is better to elaborate it so others can come up with possible solutions. The essence of security of FLOSS is provided by how security exploits are quickly discovered and fixed.

---

### Post by xhaan on 2007-02-04
> **Sunnz said:**
> Can you guard against it by running /usr/bin/sudo every time?

Actually, yes you could now that I think of it... maybe. I need to test that thoroughly.
Basically what it is, you make an alias which runs a script that forks and delays itself and then runs sudo with the argument that you originally inteded to give it.

---

### Post by SunnyRabbiera on 2007-02-04
well no OS is immune to viruses, it would be quite easy to create a virus to kill a linux system.
But i dont think many would deliver one as most of your virus coders are linux users as its great for programming viruses.

---

### Post by xhaan on 2007-02-04
> **SunnyRabbiera said:**
> well no OS is immune to viruses, it would be quite easy to create a virus to kill a linux system.
But i dont think many would deliver one as most of your virus coders are linux users as its great for programming viruses.

Problem is, it doesn't take a coder. It only takes some kid that knows how to read a howto on scripting and wants to wreck systems.
I just figured out a way to extend it so running from /usr/bin/sudo every time wont guard against it... you just ailias against something else that could possibly be run within minutes after /usr/bin/sudo runs and it would have the same effect.

---

### Post by AlphaMack on 2007-02-04
And this is not just limited to sudo.  One can easily poison find, cat, ls...whatever the attacker wants it to be.

Just as xhaan pointed out, it's not rocket science.  All one has to do is poison the $PATH environment and it's game over.

---

### Post by xhaan on 2007-02-04
> **alphasubzero949 said:**
> And this is not just limited to sudo.  One can easily poison find, cat, ls...whatever the attacker wants it to be.

Just as xhaan pointed out, it's not rocket science.  All one has to do is poison the $PATH environment and it's game over.

Yeah it could be done with other stuff but sudo is worse because it's suid root. Other stuff still has to get by permissions.

---

### Post by Sunnz on 2007-02-04
> **xhaan said:**
> Problem is, it doesn't take a coder. It only takes some kid that knows how to read a howto on scripting and wants to wreck systems.
I just figured out a way to extend it so running from /usr/bin/sudo every time wont guard against it... you just ailias against something else that could possibly be run within minutes after /usr/bin/sudo runs and it would have the same effect.
As I said before... like it is said in the article:
/usr/bin/sudo /bin/ls

or

/usr/bin/sudo /insert/path/to/program/here

or

/usr/bin/sudo /usr/bin/su -
and do your admin stuff from here.

or

Just don't execute random programs you download from the net... if you have to, either check the source or use absolute path name when you need sudo.

---

### Post by xhaan on 2007-02-04
> **Sunnz said:**
> As I said before... like it is said in the article:
/usr/bin/sudo /bin/ls

or

/usr/bin/sudo /insert/path/to/program/here

or

/usr/bin/sudo /usr/bin/su -
and do your admin stuff from here.

or

Just don't execute random programs you download from the net... if you have to, either check the source or use absolute path name when you need sudo.

I think not executing random programs would be best because using full paths can be gotten around unless you use full paths for EVERYTHING...

For example, just a bit ago I made it so where trying to run ls would hijack sudo if sudo had been run earlier. So if I did:
```
/usr/bin/sudo chmod +x somefile
```
and then did
```
ls -l
```
sudo would still be hijacked and run the command I had hidden... 
Using full paths protects you a bit more but unless you use full paths to everything an alias can still hijack sudo.

I'm thinking in addition to not running strange programs, chown root:root your .bashrc, chmod it to 444 and set timestamp_timeout to 0 in sudoers.

---

### Post by Brainfart on 2007-02-04
> **Sunnz said:**
> 
/usr/bin/sudo /usr/bin/su -
and do your admin stuff from here.
Any form of sudo su should be frowned upon.  Yes, there's probably a time when you need it, but it should be avoided on general principle.  It's too easy to do something that can't be undone (but would be stopped if a user tried it).  

I've heard that a properly configures /etc/sudoers can be pretty secure, but I've not looked into it myself.

On the topic of Linux viruses, I thought I'd throw in [this link]("http://www.gnu.org/fun/jokes/evilmalware.html"). :lol:

---

### Post by xhaan on 2007-02-04
> **Brainfart said:**
> Any form of sudo su should be frowned upon.  Yes, there's probably a time when you need it, but it should be avoided on general principle.  It's too easy to do something that can't be undone (but would be stopped if a user tried it).  

I've heard that a properly configures /etc/sudoers can be pretty secure, but I've not looked into it myself.

On the topic of Linux viruses, I thought I'd throw in [this link]("http://www.gnu.org/fun/jokes/evilmalware.html"). :lol:

I personally don't like to run as root unless I really need to, I like sudo.
I find it funny how people have made fun of me and Ubuntu for using sudo, but I hate being in root for too long... I probably won't screw anything up myself but what if I forget and leave it open, or I want to run something that will take a while and come back to it later... it would be open to anyone who wants to mess with it locally and I have a few people that come in and out of my place that could.

That link is pretty funny btw :0

---

### Post by Sunnz on 2007-02-04
Here's an excellent link that I recommend everyone to read: [http://www.osxbook.com/blog/2006/11/05/on-mac-os-x-viruses](http://www.osxbook.com/blog/2006/11/05/on-mac-os-x-viruses)

It first talks about virus on Mac OS X then generalises to to UNIX systems itself to the history of virus on UNIX systems. The gist of it is: unix(like) systems is very capable of running virus, there are no magic code in the system that identifies a virus and somehow make them not run.

---

### Post by Brainfart on 2007-02-04
> **xhaan said:**
> I personally don't like to run as root unless I really need to, I like sudo.
I find it funny how people have made fun of me and Ubuntu for using sudo, but I hate being in root for too long... I probably won't screw anything up myself but what if I forget and leave it open, or I want to run something that will take a while and come back to it later... it would be open to anyone who wants to mess with it locally and I have a few people that come in and out of my place that could.

That link is pretty funny btw :0
I also don't like to be root.  Messed things up once or twice and that's once or twice too many.  What's really ironic IMHO is that people bash Ubuntu for relying on sudo, but they all provide 1) a root account (knowing a username is 1/2 the battle), and 2) sudo.  I use sudo all the time.  Any time I invoke a package manager, I have to sudo it.  Sure, it's an extra 5 characters to type, but at least I'm consciously double checking that what I'm doing is what I want to do.

---

### Post by xhaan on 2007-02-04
> **Sunnz said:**
> Here's an excellent link that I recommend everyone to read: [http://www.osxbook.com/blog/2006/11/05/on-mac-os-x-viruses](http://www.osxbook.com/blog/2006/11/05/on-mac-os-x-viruses)

It first talks about virus on Mac OS X then generalises to to UNIX systems itself to the history of virus on UNIX systems. The gist of it is: unix(like) systems is very capable of running virus, there are no magic code in the system that identifies a virus and somehow make them not run.

This is true, I think however that people have been under the impression that linux is more secure than it actually is...

With what I found today, I could make myself an actual useful program  for Ubuntu that people would like to use.. It wouldn't require sudo to install, no special permissions, there would be no suspicious paths, no suspicious code (that you could actually look at).. it could appear to be a benign media player or anything else, and on the average Ubuntu setup it could make a timebomb that waits for the proper conditions to install a trojan which could be suid root or anything else and the user wouldn't know about it unless they were really vigilant.

---

### Post by Phatfiddler on 2007-02-04
It is actually very easy to get someone's password in Ubuntu.  For users used to password prompts, it is remarkably easy.

To prove my point, I wrote a script using python and Glade that mimics a useful application.  The name of the application is Sys-Admin Scanner.  It supposedly scans your computer for open ports and security vulnerabilities.  Because of it's nature, it obviously needs root access.  When you click the desktop icon for Sys-Admin, it spoofs a password prompt that you would normally see for root access.  After entering your password, you click Continue.  The prompt disappears, and your password is stored, in plain text, in a text file.

That is completely harmless, but what if someone wanted to replace the code that stores your password with code that uploads it to a database along with your IP address, or perhaps stores it in a hidden file so that the real virus has access.

_My point is, no matter how tight your security may be, it can all be defeated by the user._

I have included some screenshots of the prompt so that you may see how accurate it is.  One image is the prompt in KDE, and the other in Gnome.  The prompt adjusts itself to your window decorations, so it looks very legit.

In KDE
[IMG]http://cutlersoftware.com/images/kde-shot.png[/IMG]

In Gnome
[IMG]http://cutlersoftware.com/images/gnome-shot.png[/IMG]

Any comments on this?

---

### Post by IYY on 2007-02-04
Phatfiddler: the original point was that you could get the user's password without ever displaying a prompt. It's obvious that if you prompt the user for a password, the password can be stolen.

---

### Post by Phatfiddler on 2007-02-04
I understand that, but my point is, why go through all the effort to circumvent the operating system, when you can simply get the user to hand you their password?

---

### Post by xhaan on 2007-02-04
> **Phatfiddler said:**
> I understand that, but my point is, why go through all the effort to circumvent the operating system, when you can simply get the user to hand you their password?

It would probably be just as easy to make a program that waits for a successful legitimate sudo command so that it's primed to run its own sudo command without a password, and it would be less obvious what's happening.

---

### Post by Phatfiddler on 2007-02-04
^Very true.  I was simply providing a sample of what someone could do.  Took less than 30 minutes to design and write that entire program.  It could easily be added to the startup of a legitimate program, and the user would know no less.

---

### Post by LKRaider on 2007-02-04
This all assumes the malicious code finds its way into the system.

IMO, what has to be controlled are the entrypoints. You have to trust the code source, verify it's authenticity and only then carry on to execute it. Even then, you could rely on chroot jails to protect the main system from the 0,1% probability of that code containing malicious routines.

The whole set of malicious activities is impossible to enumerate and/or detect, but you can control which sources to trust.

---

### Post by Phatfiddler on 2007-02-04
^Exactly

---

