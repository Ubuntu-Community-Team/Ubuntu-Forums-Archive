---
title: "restrict users password changing to themself"
date: 2010-05-11
forum: Security
---

### Post by tekknokrat on 2010-05-11
I want the users to access servers via ssh public key only. By default they don't know their initial password and do need to change that when performing administrative tasks.

For changing their passwords without knowing the old they need to switch to root for this special case.

Therefore I configured a global alias in /etc/bashrc containing:

```
alias sudo="sudo "
alias passwd="passwd $USER"
```

Also, I added this to sudoers:

```
%admin ALL= NOPASSWD: /usr/bin/passwd
```

That means that users of the admin group do not need a password when using *sudo passwd*.

The only case it seems I don't have control is that users can not only change their password but also the password of other peoples. Does someone sees a solution (without apparmor/selinux and special /usr/bin/passwd.sh) to restrict users to only change their password?
I miss the feature of using environment variables in sudoers file.

---

### Post by voidzero on 2010-05-11
Actually I don't think that you need sudo for this. I think that you could reconfigure PAM, by setting something in /etc/pam/passwd so that passwd does not require an old password. But, this might be insecure. Maybe someone who knows pam better than I could elaborate on the approach and security implications .

---

### Post by tekknokrat on 2010-05-19
Thanks for your answer voidzero.

The reason I used sudo was that it was the only solution I know.
Also I like the idea that only users of a specific group should gain the benefit of changing their password without knowing the old.

If you or someone else knows a way to change pam's behaviour to not ask for a password I would like to know :) 
Perhaps its already implemented with some option to only allow for specific group but I didnt found any info on that.

---

### Post by teh_drizzle on 2010-05-19
I would say this is a bad idea. A user can easily:

export USER=otheruser

then run the script and change the password for another user. I'm not sure about the PAM suggestions (sounds like a possibility), I would explore that a bit.

To get the username it's better to use something like:

id | sed 's/uid=[0-9][0-9]*(\([^)]*\)).*/\1/'

---

### Post by tekknokrat on 2010-05-19
Thanks for pointing out the security implications. I'll go with ```
id -un
``` in the alias definition. Still interested in the pam way...

---

### Post by teh_drizzle on 2010-05-19
Haha, that works too

---

### Post by tekknokrat on 2010-05-20
I am wondering if there are not also implications when using the id command.

Just asking dumb...
What if someone puts a shell script "id" in it's home dir and modifies the $PATH Variable to $HOME:$PATH ? 
What command will have precedence /usr/bin/id or /home/user/id ?

---

### Post by scorp123 on 2010-05-20
> **tekknokrat said:**
>  By default they don't know their initial password  Sorry if this is a stupid question ... but why don't they know it?

You could autogenerate passwords with **pwgen** and then have the output stored in the user's home directory, e.g. a file like **YOUR-PASSWORD.txt**. The first time he connects via the SSH key he can take a look at what his initial password was and then change his own password without having to use "sudo". [B]In fact I think letting them use "sudo" is a very very risky idea.
[/B]

Example for "pwgen", generating a single password of 8 digits:
```
> pwgen 8 1

Or1ohJ3r
```

Now if you piped that into the text file, then the user would find their initial password without you having to go through the troubles to having tell it to them. They can change their password --and ONLY their own password-- all they wish and have never ever access to "sudo" anything.
```
> pwgen 8 1 > $USER/YOUR-PASSWORD.txt
```

All you have to do is to really set the user's password to whatever "pwgen" generated.

> **tekknokrat said:**
>  For changing their passwords without knowing the old they need to switch to root for this special case.  Why are they not allowed to know their old one? You could still block SSH access so that anyone without a proper key from you can't login via SSH even if they know their password.


> **tekknokrat said:**
>  Does someone sees a solution (without apparmor/selinux and special /usr/bin/passwd.sh) to restrict users to only change their password?  LDAP?

---

### Post by tekknokrat on 2010-05-20
> **scorp123 said:**
> Sorry if this is a stupid question ... but why don't they know it?
...
Now if you piped that into the text file, then the user would find their initial password without you having to go through the troubles to having tell it to them. 
...


You pointed out the reason. No fiddling with sending passwords around. Users can live without knowing their password on the server because they are pam authorized with ssh key authentication.

If they need a password (for performing administrational tasks) they change it and don't need to know the old one.

I see this as a solution for our devs/admins not for the normal user. Devs/admins use already sudo for some of their tasks so this is only a advanced usage.

Your solution sounds interesting too. How would I trigger the pwgen / passwd process?

Whats the benefit of using LDAP for this case? 
For general purpose its clear to me but can I configure ldap to allow password changing without knowing the old?

---

### Post by scorp123 on 2010-05-20
> **tekknokrat said:**
>  I see this as a solution for our devs/admins not for the normal user. Devs/admins use already sudo for some of their tasks so this is only a advanced usage.  OK ... But if you have such a large number of users so that sending out passwords isn't possible ... why not define a standard password for new accounts? e.g. every new employee / new user is told the same default password and is told to immediately change it upon first login. That's what I do. Worked OK so far ... 

> **tekknokrat said:**
>  Whats the benefit of using LDAP for this case?  People have the same logins everywhere. Same user ID everywhere. Same group ID's and permissions everywhere. So I don't have to configure dozens of systems manually. **/home** always gets mounted remotely via NFS so everyone always has access to their files no matter where they login. So I don't have to hear complaints such as "Duuuude, where are my files ... " -- all the files are always there. No need to transfer anything from anywhere, no SSH and SCP/SFTP orgies ... you just login. Your files are already there. Taddaaaa.

Getting "sudo" and "root" is a different story. I always configure one local account and local group (e.g. "sysadm") independent from LDAP and only that account can go into "root" using "su" or "sudo". Everybody else can't. And "su" has its group permissions changed so that not everybody can execute it. So in order to be able to use "su" so you could switch into user "sysadm" and do e.g. "sudo su -" your LDAP account would need to be a member of the local "sysadm" group first. Only then you can even execute "su". And then you'd still need to know the "sysadm" password which is different on each system. So even if certain people know how to "su" into the "sysadm" account on one system, they don't know the needed password on other systems. A few users are allowed to skip "sysadm" and they can execute specific commands via "sudo" (configured via the "sudoers" file).

> **tekknokrat said:**
>  can I configure ldap to allow password changing without knowing the old? Uhmmmm. I'm not sure to be honest.

---

### Post by BoneKracker on 2010-05-21
Not having a password set for a user is a very bad idea.  Until they set a password, anybody with a shell can screw with the account.

Setting all new users to the same default password is also a bad idea.  It is tantamount to giving all users the same password permanently, because anyone can access the account and do bad things, (e.g., alter permissions on user directories, or hide an executable named 'passwd' in the user's path that calls the real passwd but also tees the user's input to a file somewhere, and then maybe deletes itself).

The best way to do it is to either:

a) make the account inactive until the person calls the help desk to establish their initial password (assuming there's a way to confirm their identity)

b) issue the person their password (and cryptographic keys) during in-processing, when you force them to pass a quiz on the IT policy booklet they were issued and sign for their computer account.

Because you are the [BOFH]("http://en.wikipedia.org/wiki/Bastard_Operator_From_Hell")

---

### Post by tekknokrat on 2010-05-22
> **scorp123]OK ... But if you have such a large number of users so that sending out passwords isn't possible ... why not define a standard password for new accounts? e.g. every new employee / new user is told the same default password and is told to immediately change it upon first login. That's what I do. Worked OK so far ... 
[/QUOTE]

I also don't think its a good idea to have the same initial password for all users because this needs further work and can be misused in a lot of ways.

a) you need to make sure people change their passwords
b) if you don't care for a) people will never change their password
c) b) will lead to misuse of other accounts for own purposes...

Regarding the "sudo su -". Where is the difference to "sudo -s"?

Regarding the LDAP parts. Thanks for summarize LDAP advantages. It's still not done this way but I think it will be the next step. Btw. did you already have experience with the sudo ldap scheme?

[QUOTE=BoneKracker said:**
> Not having a password set for a user is a very bad idea.  Until they set a password, anybody with a shell can screw with the account.


This is not done. A password is of course set but scrambled and initially not known to the people.

Regarding a) This sounds like too much additional effort from my side.
Regarding b) Sounds interesting like the pw generation approach described by scorp123. But question is how is the password creation triggered and how is a new password created without the old one without root privileges?

This is our current policy regarding user accounts (in my case for developers/administrators). It should give you an idea of what I want:

[LIST=1]
[*]The initial passwords should not be communicated from super admin to admin. There are many reasons for this like unrealibility in communication, unsecure, uncomfortable (for the new user), ...uncool ;)

[*]The only step securing the account is (generating a ssh-key and) send the public key part to super admin so that he can put it in ~/.ssh/authorized_keys.

[*] Servers are accessible via keyauth only.

[*] Admin/devs ids are put by the superadmin to the appropriate sudo group.

[*] Admin/dev should only be able to change their own password and without knowing their old one (the question in origin thread).

[*] Admin/dev are only able to perform sudo commands in root- (or for developers in service-uid-) context but not in other-admins-uid-context.

[*] Admin/dev should not be able to modify the sudoers and group file.(This is still todo, ideas welcome)
[/LIST]

---

### Post by scorp123 on 2010-05-22
> **BoneKracker said:**
>  It is tantamount to giving all users the same password permanently No, because some time on their first day (depending on my other schedules) I am standing right behind the new guy and **he has to change his password right there** so I can see that he changed it. It's a very simple measure and yet a very effective one. And then I show the new guy where he can find his file shares, what file share is for what kind of documents, where the customer files have to go, and so on.

And it also helps to maintain a pleasant work atmosphere -- for me :twisted: : Because when the new guy sees that I am 1.92 m tall, have a  deep voice like Darth Vader and that I am wearing a shirt that says *"I will kill you if you ask me stupid questions"* then they really try hard and think before calling me for BS questions ... which makes my job really much more pleasant. Really, I can only recommend this method :D


> **BoneKracker said:**
>  because anyone can access the account and do bad things, (e.g., alter permissions on user directories, or hide an executable named 'passwd' in the user's path that calls the real passwd but also tees the user's input to a file somewhere, and then maybe deletes itself).  Such stuff could maybe happen in a kindergarten ... but in an office environment where supposedly everybody is an adult? Naah, I don't think so. Even if ... self-preservation usually prevents users from doing that. **They know we'd find out.** For one, all attempts with **"su"** get logged: **/var/log/auth.log** ... In Ubuntu this is the case per default, out of the box. Example from /var/log/auth.log, Host "frodo":
```
May 22 23:47:08 frodo su[24866]: pam_unix(su:session): session opened for user johndoe by frankp(uid=4891)
```

That log file belongs to the system account "syslog", so they can't mess with it, only "root" can.

Trust me ... it's easy to find out. 

> **BoneKracker said:**
>  a) make the account inactive until the person calls the help desk to establish their initial password (assuming there's a way to confirm their identity)  Except that neither I can wait for them to call me and neither can they wait until I have time for them. They arrive on their first day -- and they want to start working, answer the first few mails, familiarize themselves with our tools, and what not. 

> **BoneKracker said:**
>  b) issue the person their password (and cryptographic keys) during in-processing, when you force them to pass a quiz on the IT policy booklet they were issued and sign for their computer account. Too complicated :D

---

### Post by scorp123 on 2010-05-22
> **tekknokrat said:**
>  a) you need to make sure people change their passwords  That's why I take the time and on an employee's first day I pay them a visit. Just to make sure they know who I am and that it isn't a great idea to bother me with BS questions. :twisted: ... And yes, I force them to change their password right then and there. Just to make sure.

> **tekknokrat said:**
>  b) if you don't care for a) people will never change their password  I know. But it's easy to verify ...

> **tekknokrat said:**
>  c) b) will lead to misuse of other accounts for own purposes...  A user would need to use "su" for that, or to authenticate at some point (e.g. if they were accessing a file share under a different name). Trust me ... it's easy to see. So usually people's sense of self-preservation keeps them from doing that. What's the point of manipulating a new employee's account anyway? We have a good work atmosphere and people usually are happy when a new guy or a new gal starts working there, because that means two new pairs of helping hands ... Manipulating that guy's or that gal's account is shooting your own foot.

> **tekknokrat said:**
>  Regarding the "sudo su -". Where is the difference to "sudo -s"?  "su -" spawns a new login shell out of your login shell, complete with the target account's shell environment. But because on Ubuntu the 'root' account is locked (it has no password 'su' could ask about) you have to add a 'sudo' to it:

"ps -efH" after a 'sudo su -':
```
john     24430 24427  1 00:19 pts/0    00:00:00     bash
root     24562 24430  0 00:19 pts/0    00:00:00       su -
root     24570 24562  4 00:19 pts/0    00:00:00         -su
root     24626 24570  0 00:19 pts/0    00:00:00           ps -efH
```

The first "bash" is me, that's the one I got when I started the terminal application. The "su -" sub-process is triggered by 'sudo', the next "-su" sub-process is the 'root' shell triggered by "su -"; and at last we get the "ps -efH" process I triggered to get the above output. 'PS1' prompt I get here:
**[COLOR="Red"]root@frodo:[/COLOR][COLOR="Blue"][B]~**[/COLOR] #[/B]

"sudo -s" however does this according to the manual:
> The -s (shell) option runs the shell specified by the SHELL environment variable if it is set or the shell as specified in passwd(5).  If a command is specified, it is passed to the shell for execution.  Otherwise, an interactive shell is executed. ... So 'sudo -s' does not necessarily start a login shell but might be starting any shell application that you specify here, e.g. "pdksh" instead of "bash", and so on. So while ultimately performing the same thing (e.g. giving you a root shell) it takes a different path to achieve that.

"ps -efH" after a "sudo -s":
```
john     31436 31433  1 00:26 pts/0    00:00:00     bash
root     31535 31436  2 00:26 pts/0    00:00:00       /bin/bash
root     31618 31535  0 00:27 pts/0    00:00:00         ps -efH

```

So "sudo -s" jumps into root's priviledges and spawns a shell running under his name ... but look at this PS1 prompt:
[COLOR="RoyalBlue"]**root@frodo:**[/COLOR][COLOR="Red"]**~[/COLOR] >**

... that's still the PS1 prompt configuration of my ordinary user account, root's own configuration looks different (see above). So it's a safe bet that "sudo" did _not_ load root's shell environment configuration (shell prompts, paths, etc.), it just opened a shell running under root's priviledges, but that's it. It did not load the everything a proper login shell would have.


Both ways *can* make sense ... depending on the scenario. But ultimately they achieve the same thing and it's just a matter of personal preference.

I prefer "sudo su -" simply because the different shell prompt colors will make sure I remain aware that whatever I am typing will be executed as "root" (that's why I picked red color for root's shell prompt ... red works tip top as a warning sign)... if root's shell has the same friendly blueish color like my normal (and harmless) shell ... that's dangerous :D


> **tekknokrat said:**
>  did you already have experience with the sudo ldap scheme?  Not sure to be honest. Our current LDAP servers are running on Novell SLES 10 (and they worked tip top so far!) and there you don't need to bother about such details. It just works. Both OpenLDAP and SAMBA are super-easy to setup here. You just tell SAMBA to use the LDAP password back-end. Done. So the same logins will work on both Linux and Windows machines.

We are in the process of migrating these servers. Our next LDAP/SAMBA servers will be running Sun/Oracle Directory Server Enterprise Edition (aka Sun DSEE) on top of Solaris. And we're moving all the file shares onto ZFS-formatted storage. Yay, filesystem cloning and snapshotting!! (with this my life will get even easier; if anyone loses a file or accidentally deletes it I can just get it back from a previous ZFS snapshot ... )

What I do know so far is that the internal structures of DSEE and OpenLDAP differ quite a bit, so I will probably have to adjust several of our LDAP-enabled applications and web-based self-help tools to become aware of the changes ... but that shouldn't be too hard.

No idea about "sudo" yet. For the Windows users this doesn't matter anyway, and for the Linux users I think we will keep our current scheme ... which will hopefully work as well with DSEE instead of OpenLDAP in the back-end. No idea to be honest, I have not yet looked into this.

---

### Post by BoneKracker on 2010-05-22
> **scorp123 said:**
> Such stuff could maybe happen in a kindergarten ... but in an office environment where supposedly everybody is an adult? Naah, I don't think so. Even if ... self-preservation usually prevents users from doing that. **They know we'd find out.** For one, all attempts with **"su"** get logged: **/var/log/auth.log** ... In Ubuntu this is the case per default, out of the box. Example from /var/log/auth.log, Host "frodo":
```
May 22 23:47:08 frodo su[24866]: pam_unix(su:session): session opened for user johndoe by frankp(uid=4891)
```
Su has got nothing to do with it.  If somebody logs in as that new user, all your logs will show you is that the new user logged in, and what pseudo-terminal they logged in from.

You should get somebody to give you a security audit, for your own good.

---

### Post by scorp123 on 2010-05-24
> **BoneKracker said:**
> Su has got nothing to do with it.  If somebody logs in as that new user, all your logs will show you is that the new user logged in And so? That gets logged too, you know. And the other ordinary users don't even know what the new guy's user name will be, so they'd be filling the log with login attempts for non-existing users, and then their IP address would show up again and again and again. LDAP queries get logged too you know? So even if someone tried to avoid remote logins altogether and tried to login on a local machine with the new guy's or gal's yet unknown name ... I'd know that too.

Last but not least: Most ordinary users have a Sun Ray ultra-thin client on their desk. So there is hardly much left that they could try and manipulate.

> **BoneKracker said:**
> You should get somebody to give you a security audit  We do that regularly :lolflag:

---

### Post by BoneKracker on 2010-05-24
> **scorp123 said:**
> And so? That gets logged too, you know.
I'm confused.  I said, "If somebody logs in as that new user, all your logs will show you is that the new user logged in."  And you said, "That gets' logged too."  That comment doesn't make any sense.

> **scorp123 said:**
> And the other ordinary users don't even know what the new guy's user name will be, so they'd be filling the log with login attempts for non-existing users, and then their IP address would show up again and again and again.
In every organization I've been a part of, standard naming conventions are used.  People don't get to just pull their userid out of thin air.  Furthermore, only an idiot would attempt such from an IP that is somehow traceable to them.  This is especially true in a thin client architecture, where lots of shared machines exist.  All they need to do is log in from anywhere else than the one or two IPs that might be loosely associated with them (i.e., somebody else's machine, a machine that's not assigned to an individual, a general purpose workstation, a general purpose terminal, etc.).  If they know anything about networking they can probably spoof a MAC and/or arp an address.  Are you seriously going to tell me you are 100% confident there is absolutely no way for a person to operate on your network with an IP address that is not traceable to them?  That's a pretty big (and unsafe) assumption to make.

> **scorp123 said:**
> LDAP queries get logged too you know? So even if someone tried to avoid remote logins altogether and tried to login on a local machine with the new guy's or gal's yet unknown name ... I'd know that too.
You'd know what?  You'd know squat.  You'd know that it happened, and this is not an anomaly.  You wouldn't even notice.  New user logs in.  Not an issue.

> **scorp123 said:**
> Last but not least: Most ordinary users have a Sun Ray ultra-thin client on their desk. So there is hardly much left that they could try and manipulate.
Irrelevant.  If the account is not password-protected, they can still do exactly the sort of thing I talked about.

> **scorp123 said:**
> We do that regularly :lolflag:
I don't what "that" refers to here, but assuming you're talking about leaving accounts unprotected by a password, then you fail at information security.  Yeah, that's real "lol".  Any auditor would tear you guys a new orifice for this.  It's a fundamentally bad practice.  Do yourself a favor and look into this if you don't believe me, and fix it before somebody else points it out.  "We've always done it this way and haven't had any problems." is not a sound rationale for a practice, and some might even characterize that statement as "famous last words".

Don't waste your breath trying to tell me how it's all fine and not a risk.  It's your butt, not mine; I have no issue with it.  If your organization is fine with such risks, then so be it.

---

### Post by scorp123 on 2010-05-25
> **BoneKracker said:**
>  I said, "If somebody logs in as that new user, all your logs will show you is that the new user logged in."  And you said, "That gets' logged too."  That comment doesn't make any sense.  Let me expand on that: The new guy hasn't even started and yet I see a log entry that he has logged in somewhere somehow? Whoever did that: I'd have their IP address and could nail them with that. Nobody is stupid enough for that.

And again: that's like shooting your own feet. When we employ somebody new the last thing you want to do is to sabotage that person's account. That's just plain silly.

Different story if somebody leaves (or maybe: has to leave?) ... depending on the circumstances they might be angry and try something and not really care about any consequences.

> **BoneKracker said:**
>  All they need to do is log in from anywhere else than the one or two IPs that might be loosely associated with them (i.e., somebody else's machine, a machine that's not assigned to an individual, a general purpose workstation, a general purpose terminal, etc.). Only few people have access to these things. Tracing these things back would be easy. And again: Hacking a new guy's account?? That's silly.

Different story when someone leaves the company / has to leave the company, etc. That's where I'd worry. 

> **BoneKracker said:**
>  If they know anything about networking they can probably spoof a MAC and/or arp an address. If a guy has that level of knowledge then he'd probably be admin anyway. :D

> **BoneKracker said:**
>  Are you seriously going to tell me you are 100% confident there is absolutely no way for a person to operate on your network with an IP address that is not traceable to them? I didn't say that. I and a few other people of course know where the weak spots are :D

But you are making an elephant out of a mosquito here, sorry to say so. You're way offtopic.

We're not discussing general network design, general security, or anything like that, although these topics would be surely interesting.

What we're discussing here is what to do with new user accounts. OP is using SSH keys and doesn't tell them their password, so they have to change it if they want to get anywhere. I take the time and introduce myself to the new guys on their first working day and I make them change the password after their first login; I give them some quickie explanations about the file shares, what they can do or not do, where to place which files, etc. .... and then I am on my way again. Only costs me a few minutes of my precious time, it helps create a nice atmosphere for the new guy, we get to know each other a little bit, and I know for 100% sure that he did change his password because I was standing right there when he did it. It's a simple and stupid method that has worked tip top so far.

So if you have suggestions regarding what to do with new guys without having to mail their password to each of them ... please stay on-topic and make such suggestions, but please stop with those wannabe scary stories, OK?

> **BoneKracker said:**
> 
You wouldn't even notice. Riiight. If you say so. LOL.

> **BoneKracker said:**
>  Irrelevant.  If the account is not password-protected, they can still do exactly the sort of thing I talked about. Sure. And they can also fake token cards (Sun Rays use those, you know?) by pulling them out of their rear end, I am sure. :D  And even if they could: Seriously, what moron would try and sabotage a new guy's or new gal's account?? That's shooting your own foot. And even if anyone did that: So what?? I takes me a few mouse clicks and just a few seconds to have a new user's desktop setup regenerated.

Our storage and our shares are on Solaris servers, so we have ZFS snapshots of everything. If someone manipulates something I simpy rollback to the previous good version ... taddaaa, done. And we still do regular backups onto a LTO-4 tape library which happens to be some kilometers away. Even if someone managed to pull an EMP device out of his rear end and delete all ZFS snapshots on a new guy's first working day ... I'd still get my stuff back. :D

Now you're gonna tell me somebody could steal a nuke and try and detonate that? Good thing then that we are based in Switzerland where most buildings have nuke shelters already built-in. :D

> **BoneKracker said:**
>  you're talking about leaving accounts unprotected by a password, then you fail at information security. You fail at common sense and basic reading skills then. We're talking about new employees and how to get them change their password on their first working day. Nothing more, nothing less.

> **BoneKracker said:**
>  It's your butt, not mine; I have no issue with it.  If your organization is fine with such risks, then so be it. Yes, we are fine :D

Relax and try to panic less, yes? :D

---

### Post by BoneKracker on 2010-05-25
Like I said -- fine.

I do think, however, that you fail to understand why someone would hack a new guy's account.  There are many compelling reasons to do so (corporate espionage probably first among them).  That might sound unlikely to you, but it happens all the time in competitive scenarios.  When your competitors will pay one of your employees more than a year's salary to find out what you are bidding on a contract, somebody is eventually going to try to find out (and this may cost your company millions of dollars in lost revenue each time it happens).  That's just one scenario, there are dozens of others involving product development, marketing, promotion, private customer data, financials, etc., etc., etc.

But you're a seasoned business guru and apparently an expert on all the reasons nobody would ever do such a thing -- and since nobody would ever do such a thing, then that means you are fine.  So no worries.  Maybe your "enterprise" is just 50 people in a non-profit who's mission is processing used clothing donations for the poor (maybe your risk profile is actually very low).

(And this isn't off-topic at all; it is central to the question of whether to password-protect (or disable) new accounts by default, which you don't do because you claim it's safe.)

---

### Post by scorp123 on 2010-05-25
> **BoneKracker said:**
>  I do think, however, that you fail to understand why someone would hack a new guy's account. Yes. Really. Because it's utterly pointless. It takes but a mouse click to reset any manipulations, especially in a VDI environment where each user gets their own virtualised desktop instance, usually an Ubuntu desktop. Those work tip top on those Sun Rays, cloning from the master snapshot takes just a few seconds.

> **BoneKracker said:**
>  There are many compelling reasons to do so (corporate espionage probably first among them). That might sound unlikely to you, but it happens all the time in competitive scenarios. Seriously. What kind of "advantage" can you gain from a guy on his first working day who doesn't even know zip yet about your customers, about your contracts, etc. ????   :lolflag:

Industrial espionage is an issue ... but not in this ridiculous scenario you so hard try to convince me of. Where it is an issue: when people leave the company ... either because they want to work as freelance consultants (and thus become competitors to us) or because they got a better paid job from one of our other competitors ... _This_ is where I'd worry about industrial espionage, because *"taking customers with you"* when someone leaves is not unheard of. Not at all. It's in fact very common. People keep trying that all the time. When they leave ... not when they start on their first day, though. :)


> **BoneKracker said:**
>  When your competitors will pay one of your employees more than a year's salary to find out what you are bidding on a contract Such a scenario could work in a third-world country ... but in Switzerland wages are already pretty high. A one year's salary --we're talking at least CHF 100'000.-- == USD 86'166.-- for a skilled IT administrator-- wouldn't go unnoticed. No way. Swiss banks will report any unusual money transfer to the authorities. Getting CHF 100'000.-- when usually you only get around CHF 8000.-- every month definitely is unusual. So yes, whoever received that money would get a lot of attention all of a sudden. Swiss banks only remain silent about large transfers if you already are filthy rich (isn't that wonderful? :( ). A transfer of CHF 100'000.-- onto a millionaire's account where already millions and millions are deposited will not alert them. CHF 100'000.-- onto an account of someone who is supposed to belong to the "worker class" ... oh yes, that will alert them. Of course that money could be deposited on foreign banks ... but then again there will be the problem of accessing it without the authorities noticing.

Sorry ... but nope, I just don't see this working here. Corruption of this magnitute is totally unknown here. Bribes here and there are not completely unheard of, but not in this size.

And most bid processes are public anyway, especially when you're dealing with anything that is funded by tax money: hospitals, universities, schools, authorities ... whatever. Most of their bids are pretty much public. So by this very nature you sooner or later will know in any case which company got involved into which bid process and even if you don't know the exact details, just by the Q&A that gets sent around to all competitors you get a pretty good clue what they are up to and what they are going to try their luck with.

This makes industrial espionage on such a scale pointless and on the other hand it thus becomes pretty much fair and transparent to everybody else why a certain company was chosen for a contract and the others weren't.

> **BoneKracker said:**
>  But you're a seasoned business guru and apparently an expert on all the reasons nobody would ever do such a thing  I didn't say that. I just don't see anyone doing that on the very first day of employment, LOL :)

Different story if someone leaves, wants to leave, hints at leaving, or has to leave ... That's where I'd worry. :)


> **BoneKracker said:**
>  and since nobody would ever do such a thing Not on a new guy's first working day, LOL :)

> **BoneKracker said:**
>  it is central to the question of whether to password-protect (or disable) new accounts by default, which you don't do because you claim it's safe.) Can you show me where I wrote that please? :)

---

### Post by bapoumba on 2010-05-25
Closed for a while :)

---

