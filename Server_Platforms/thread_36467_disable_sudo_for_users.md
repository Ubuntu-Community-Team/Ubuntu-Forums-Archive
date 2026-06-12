---
title: "disable sudo for users"
date: 2005-05-23
forum: Server Platforms
---

### Post by doni on 2005-05-23
Hi there...

one thing i don't really get in ubuntu is the sudo thing....i mean it's probably nice for a user to set up any administration action - but in my eyes it's a loss of security.
anyway this shouldn't be the discussion :-)

i just wanted to ask how i can disable sudo for my user, e.g. "admin" ?

thanks very much
doni

---

### Post by camp on 2005-05-23
Hi doni,

You shouldn't, but if you want to... here is how.

Run visudo on a terminal, as root.

sudo visudo

And just put a # in front of the "%admin" line... BUT BE AWARE!
It is better to just don't put your users in the admin group. As k/ubuntu is not configured for root login, you will loose root capabilities, if you don't fix this first. Specially if you just have one single user!

Have a nice day!
/JC

---

### Post by doni on 2005-05-23
thanks!

but what do you exactly mean by "ubuntu is not configured for root login" ? that the root account is diabled?

i've already fixed that with "sudo su, passwd"....

i mean, if i've got a server, i need another user beside of root to make login in with ssh more secure, but i would realy like if this user wouldn't have "root" access (using sudo)....

what do you other server administrators mean? is this not important ?

i'm currently writing a tutorial about setting up a ubuntu server/client network....security is not the main topic in the sheet but it should be important to it...

thanks everyone

---

### Post by LordHunter317 on 2005-05-23
[QUOTE=doni]one thing i don't really get in ubuntu is the sudo thing....i mean it's probably nice for a user to set up any administration action - but in my eyes it's a loss of security.[/quote]We had a long thread about this recently.  You really should read it and think about this some more.

> i mean, if i've got a server, i need another user beside of root to make login in with ssh more secure, but i would realy like if this user wouldn't have "root" access (using sudo)....You do realize that having an account with sudo access to gain privilege temporarily is a world different from the root account that's privileged all the time, right?

>  what do you other server administrators mean? is this not important ?Seeing as the general enterprise way is to disable the root account entirely and give people the access they need via sudo (admittedly using a stricter policy than Ubuntu's default) it is obviously important.

---

### Post by vague- on 2005-05-23
[QUOTE=doni]i mean, if i've got a server, i need another user beside of root to make login in with ssh more secure, but i would realy like if this user wouldn't have "root" access (using sudo)....[/QUOTE]

If somebody manages to gain access to this account, all they have to do is alias "su" and wait.  You'll save them the trouble of trying to crack root's password.  Swapping from "sudo" to "su" does not really eliminate the issue you have.  That is, as soon as you give a user the ability to elevate their privileges, you pretty much have to assume that: a) they can do anything - common mistakes include allowing tasks such as make or text editors via "sudo", but there are lots of other ways; b) that a compromise on that account is near parallel to a compromised "root" account, it is just a matter of time (the window in which you may stop complete compromise of the system). 

Of course, the funny thing is that many people set their log permissions in such a manner that they have to authenticate to "root" in order to view them.  So, their password will be intercepted before they even start to look at logs.  If you are a bit more sensible, you can hope that your log monitor catches the activity and reports it to you in a non-privileged or remote format.

The whole single command or deliberate escalation of privilege protects your server from you, not from Mr Nefarious Cracker.  If you really think your accounts are that weak that they may be defeated in this manner, you may want to look into use of hardening mechanisms and enforce a better public key + passphrase policy so the account should not become compromised in the first place.

By the way, sorry if I rambled.  I got started and you know how it is...

---

### Post by vague- on 2005-05-23
[QUOTE=LordHunter317]Seeing as the general enterprise way is to disable the root account entirely and give people the access they need via sudo (admittedly using a stricter policy than Ubuntu's default) it is obviously important.[/QUOTE]

It is worth mentioning that a large part of this is because "sudo" leaves better logs.  It leaves you an audit trail of who did what as "root" and when - when configured properly.  The accounts are basically considered "root" accounts, as they only require their own password to be entered to gain "root" privileges.  The problem stems from the use of UID 0 and issues with having multiple users of the same UID, I believe.

In fact, you do not even need the account password to use "sudo".  Due to the caching, you can steal a session that another user has created (ever noticed the amount of time "sudo" keeps your credentials for you?).  There are workarounds for this issue, however.  However, most people enjoy the convenience of caching too much to bother with them.

You have to be very strict to not create a root account.  Most command line tools will allow you to some how get a root shell via "sudo", it just might require some lateral thinking.

---

### Post by LordHunter317 on 2005-05-23
[QUOTE=vague-]If somebody manages to gain access to this account, all they have to do is alias "su" and wait. You'll save them the trouble of trying to crack root's password.[/quote]Assuming the user of the compromised account has root access.  Which may/may not be presumptious.

> That is, as soon as you give a user the ability to elevate their privileges, you pretty much have to assume that: a) they can do anythingIf you're making this assumption with sudo, your policy is wrong.  End of story.

>  that a compromise on that account is near parallel to a compromised "root" account, it is just a matter of time (the window in which you may stop complete compromise of the system). Once again, not necessarily true with sudo.

> Of course, the funny thing is that many people set their log permissions in such a manner that they have to authenticate to "root" in order to view them.And with good cause.  Those contain information you don't want everyone on the system (or even most people) seeing.

> t is worth mentioning that a large part of this is because "sudo" leaves better logsThat's part, but I wouldn't call it even a large part.

It's the whole you can greatly restrict what command a user can and cannot run priveleged that's the major part.

> The accounts are basically considered "root" accounts,No, they're accounts that can elevate their privileges for a limited-time in limited-ways.  Unless you gave them permission to run everything elevated, of course.

> Due to the caching, you can steal a session that another user has created (ever noticed the amount of time "sudo" keeps your credentials for you?).Yeah, if you compromise their account.  And if it's really so much of an issue, switching it off is a single option in the sudoers(5) file.

> Most command line tools will allow you to some how get a root shell via "sudo", it just might require some lateral thinking.No, most don't.

---

### Post by Burgundavia on 2005-05-23
The other thing that is not mentioned is that by default, only the first user is in the admin group.

All users created after have to be manually added to the admin group.

And trust me, sudo is far far safer and more secure than root.

Corey

---

### Post by vague- on 2005-05-24
Here, read this from somebody who knows a bit more than I (it is actually where a few of the comments I have made come from).  He is better at writing than me, though, so it might be more clear.

[http://marc.theaimsgroup.com/?l=owl-users&m=109830229500062&w=2](http://marc.theaimsgroup.com/?l=owl-users&m=109830229500062&w=2)

You may find the rest of the discussion useful, also.

---

### Post by gruepig on 2005-05-24
I have a concern about sudo that I don't think has been addressed in this thread.

I think sudo is great for multi-admin systems where you want accountability and for specifying limited root privileges to individual users.  However, in some usage cases involving, say, a single admin system with remote login (e.g., SSH), I suspect the sudo model (specifically, with sudo configured so that at least one account has full root access) may do as much harm as good (when compared with su).

Rationale follows: I ssh (as myself) in to systems that I have root access/privileges on.  Usually I do so from one of my other (trusted) systems, but occassionally I ssh in from a less-trusted system.  In doing so, I'm aware that I'm potentially compromising my unprivileged account password (because the untrusted system may have a keystroke logger, password sniffer, trojaned ssh client, or other malware; and yes, this seems to be far-too-common these days).  However, I would like to be able to do so (however ill-advised) without potentially compromising a *privileged password*.  

There are some obvious workarounds (I could avoid using ssh from untrusted systems, I could create a separate account to ssh to when needed, etc.).  But what I'd really like is to have all the advantages of sudo, but to have sudo (or something sudo-like) prompt for a separate password -- that is, neither my unprivileged password, nor root's password -- to gain privileged access.  

Thoughts?  Is this possible with sudo, and I just don't know it?  Am I worrying about an unlikely scenario?  Is there an obvious reason why I shouldn't be concerned about my account and sudo using the same password?

---

### Post by LordHunter317 on 2005-05-24
No, I have to say Solar is wrong.

su(1) and sudo(1) aren't meant to be a defense against an attacker; in the end, the fact that you can interactively raise privelege is a boon to them.

So what can you do then?  One of two things:
[list=1]
[*]Not use them at all, which is Solar's approach.  I disagree with this, because I think letting users have privilege all the time is more dangerous, even if they need it (because that's how costly accidents happen, e.g., rm -rf /)   
[*]Do your best to limit and enforce access to those commands only to people you trust.  You operate under the assumption that once an attacker gets in, your policy has already failed.  At that point, everything else is just damage control. 
[/list] Like it or not, 2. is the only correct policy under the default UNIX/Linux security model.  Think long and hard for a second, and you realize why.  Linux doesn't have a track record nor a design where I'd feel comfortable with people I don't trust (to some degree) having access.  And your security policy must take that fact into account.

Also, I don't know why Solar's babbling about TTYs.  Unless there's some famous attack I've missed, I don't see how any compromise could occur unless the user wasn't being cautious.  Which is a requirement in any high-security situation.

Basically, I think Solar's out to solve an unsolvable problem.  Once an account's been compromised, anything that account can do (including raise privilege) must be treated as compromised.  There's nothing you can do about that.  As a result, you must decide whether allowing privilege raising is a valid risk for your systems.  Solar doesn't think so.  I do.  Your free to choose for yourself, but it isn't a fundamental flaw in su or sudo; it's a fundamental flaw in UNIX's crappy security model.

---

### Post by vague- on 2005-05-24
[QUOTE=gruepig]I think sudo is great for multi-admin systems where you want accountability and for specifying limited root privileges to individual users.  However, in some usage cases involving, say, a single admin system with remote login (e.g., SSH), I suspect the sudo model (specifically, with sudo configured so that at least one account has full root access) may do as much harm as good (when compared with su).

Rationale follows: I ssh (as myself) in to systems that I have root access/privileges on.  Usually I do so from one of my other (trusted) systems, but occassionally I ssh in from a less-trusted system.  In doing so, I'm aware that I'm potentially compromising my unprivileged account password (because the untrusted system may have a keystroke logger, password sniffer, trojaned ssh client, or other malware; and yes, this seems to be far-too-common these days).  However, I would like to be able to do so (however ill-advised) without potentially compromising a *privileged password*.[/QUOTE]

As I stated previously, if somebody has compromised an account that you use "su" from, then it is likely that your next invocation of "su" will give them the root account.  I would advise to frequently check the results of commands such as "last" - if they have only compromised your account, barring a flaw in the logging mechanism having been exploited, then they should not have been able to edit the information held here.

It is good to have a little "routine" that you go through on each login.  This is probably the best you can do if you are forced to sometimes use hosts that you do not have complete trust in.  Basically, everywhere you are currently leaving a trace, the attacker left a trace.  This is where having logs available via authentication, but not owned by root can help (the reason I flagged this earlier):  you can authenticate to an account that only compromises the future integrity of certain logs, which I think is better than a root account compromise and allows you to read some of the less critical, but preferably private logs in this context.

If you find anything suspicious from utilities like "last" or in the logs, I would advise you to enact your policy for a machine compromise.  Where possible take the machine down and begin forensic analysis.  I would not advise you to probe the extent of the compromise while the machine is still running.  Follow basic procedure on this (for example, pull the plug instead of shutting down).

In answer to your "sudo with full root access", I would say that you have to have an extremely limited account in order for "sudo" to not grant this.  For instance, you have to make sure that programs executed cannot (and this list is by no means exhaustive) invoke external processes or move or edit files that are in important places.  You will tend to find that a lot of commands are subvertible.  If you see Solar Designer's comment, you will notice he mentions about environmental variable black-listing in "sudo"; this is pertinent here, as even if you manage to invoke a risky command in a manner that you believe negates the problems an environmental variable can still end the game.

What you need to understand is that apart from some edge cases, "sudo" when applied to non-root administrative accounts usually creates another root account.  That is, you may not give away another privileged password, but you have already given away one.  Obvious exceptions to this are if you let the user use wrapper programs.  For example, if you wanted a user to be able to create new email users.  You could give them write access to the aliases file and the ability to tell the daemon.  Or, you could write a program/script that does all of that and takes a few well-checked arguments to fill in the blanks with.  Wrapper programs need to be well-written.  They should sanitise the environment before launching other programs, they should be aware of the effect of various characters on the programs they invoke (for example, does a globbed argument still do something despite the fact that we are not invoking the programs via a shell?) and so on.

For your purposes, gruepig, you could make sudo authenticate against a different authority than the passwd files.  I am not sure how much you really gain from this, mainly due to the reasons I have given against the "sudo" concept in general.  A useful tool when you believe that somebody might be listening in is One Time Passwords (OTP).  Everytime you login requires a different authentication token, the worst that can happen is that you get out of track with the tokens (but, you can always use your private key and passphrase from a secure system to reset this).  You could use this combined with a separate authority for "sudo" to never use a password that is of use in getting access to the system (the OTP is invalidated on usage, the "sudo" password only works from your account - which they do not possess credentials for).  There may be a problem with this that I have not noticed, so I cannot ensure you it is safe - particularly, you must pick a good OTP system, as a predictable algorithm would mean that there may be very few variations for the next password in the sequence.  Notably, this does not help if they are relaying your SSH account through a channel they can read from or with a trojaned SSH client.  In either of those cases, they could prevent the shell from exiting when you attempt to logout.  A good rule of thumb is the old phrase, "a chain is only as strong as it's weakest link."  Your system's security is the chain, it's weakest link is the least trustworthy system that you access it from.

LordHunter317, from your last post I don't think we disagree much on the arguments for and against, just which side of the fence they put us on.  He is referring to TTY hijacking, by the way.  I too agree that the traditional security model is not all it's cracked up to be.  However, I prefer using stronger systems when I want users to escalate privileges (RSBAC, for example).  The traditional system is not fine-grained enough to create truly limited accounts.  I suspect you agree with that.

---

### Post by ssam on 2005-05-24
i think the fear is that in a traditional system you have a

root, user1, user2 ...
and only root can do anything

in an sudo system you could have

user1, user2, user3 etc
and they could all do stuff as root

but the way it is by default is that only user1 would have sudo priviliges.

now if you treat user1 as a normal accound to do everyday stuff, then maybe yes, it could be less secure in some circumstances.

but if you treat user1 as root (ie, only log in as user1 when traditionally you would log in as root), then you have a very secure system. you also have better logging.

if i want to 'own' your box using a dictionary (or some other) password guess attack, then i also have to guess the username of your priviaged user.

the other use of sudo is to be flexible. say i want to give certain privilages to certain users on a machine, with sudo and groups you can set up a very flexible system.

sam

---

### Post by LordHunter317 on 2005-05-24
> **vague-]As I stated previously, if somebody has compromised an account that you use "su" from, then it is likely that your next invocation of "su" will give them the root account.[/quote]Again, only if the user is not cautious.    Such blanket assumptions are bad things.  They don't help improve security, and they cause people to come up with bad policy in response to them.

>  This is where having logs available via authentication, but not owned by root can help (the reason I flagged this earlier):  you can authenticate to an account that only compromises the future integrity of certain logs,But it doesn't.  Go read up on race attacks said:**
> If you find anything suspicious from utilities like "last" or in the logs, I would advise you to enact your policy for a machine compromise.  Where possible take the machine down and begin forensic analysis.No, if you suspect a machine is compromised, you do not wait. You shut it down immediately.  If the machine is important enough to not be able to have unscheduled downtime, then it should have a redundant spare anyway. 

> In answer to your "sudo with full root access", I would say that you have to have an extremely limited account in order for "sudo" to not grant this.Which isn't hard to setup.

>   For instance, you have to make sure that programs executed cannot (and this list is by no means exhaustive) invoke external processes or move or edit files that are in important places.This isn't that hard to do, it's a matter of policy.  It's just harder to do than the other solution: don't use sudo at all.

> If you see Solar Designer's comment, you will notice he mentions about environmental variable black-listing in "sudo"; this is pertinent here, as even if you manage to invoke a risky command in a manner that you believe negates the problems an environmental variable can still end the game.Once again, it's a matter of policy.  It's not like most of this isn't documented or anything.

Is it a non-trivial task?  Yes.  Is it hard?  No.  It just requires reading a lot of documentation, thinking, planning, and testing.  But it's certainly doable.  He's wrong about the enviroment thing anyway.  You can force -i to be the default.  A reading of the sudoers(5) manpage would teach you that.

A simpler solution would be better, I'll admit.  But that's not likely to happen for sometime.

> What you need to understand is that apart from some edge cases, "sudo" when applied to non-root administrative accounts usually creates another root account.No, it doesn't.  Not if you do it **properly**.  It's the properly part that's admittedly hard, but crucial.  

> He is referring to TTY hijacking, by the way.TTY hijacking isn't the issue it used to be, on Linux anyway.  Any real policy isn't safe with sudo on regular TTYs anyway (because wrapper scripts aren't safe), so it's a moot point.

>  The traditional system is not fine-grained enough to create truly limited accounts.  I suspect you agree with that.No, it's not.  But done properly, sudo can carry you a long way to it, as long as you're careful.  Which requires quite a bit of work, I'll admit.  But it's not impossible.  You just have to think things through.

---

### Post by vague- on 2005-05-25
> **LordHunter317]Again, only if the user is not cautious.    Such blanket assumptions are bad things.  They don't help improve security, and they cause people to come up with bad policy in response to them.[/QUOTE]

The whole point of the statement is about whether the user is cautious.  I have seen far to many people log directly in from potentially unsafe systems and *instantly* authenticate to a privileged account.  I am sorry, the original statement was not clear in this regard.  The assumption I should not have made is that they will be "su"-ing to "root".  However, that is where our discussion is focused, so it is fair to assume that is the situation I mean.  I should have noted as an aside that that only applies in certain situations, and possibly listed those situations.

[QUOTE=LordHunter317]But it doesn't.  Go read up on race attacks said:**
> 

Except, I did not say that you needed write access to logs.  Further, I should think everybody in here understands race conditions, I do not understand why you try and offend me, to be honest - I am not trying to offend you.

[QUOTE=LordHunter317]No, if you suspect a machine is compromised, you do not wait. You shut it down immediately.  If the machine is important enough to not be able to have unscheduled downtime, then it should have a redundant spare anyway.

By "where possible", I mean where you are capable of doing so.  If you are not capable of physically powering down the machine (for example, it is on another continent, let alone if it is three hours away), the best you can do is to enact your policy and tell the local team to take it down.  You may not be able to receive the media for analysis for a week.  Again, it is my fault for lacking clarification.

[QUOTE=LordHunter317]Is it a non-trivial task?  Yes.  Is it hard?  No.  It just requires reading a lot of documentation, thinking, planning, and testing.  But it's certainly doable.  He's wrong about the enviroment thing anyway.  You can force -i to be the default.  A reading of the sudoers(5) manpage would teach you that.[/QUOTE]

I have read the manual page, I do not know why you would assume that I have not.  There are two main problems.  First, you will note that certain variables are left unchanged from the old environment - admittedly, this is a much reduced attack vector.  Second, sometimes it is necessary to allow other environmental variables through due to the way programs work.  Though, you can just not use those programs.

[QUOTE=LordHunter317]A simpler solution would be better, I'll admit.  But that's not likely to happen for sometime.[/QUOTE]

I agree fully, I just choose a different interim solution.

[QUOTE=LordHunter317]No, it's not.  But done properly, sudo can carry you a long way to it, as long as you're careful.  Which requires quite a bit of work, I'll admit.  But it's not impossible.  You just have to think things through.[/QUOTE]

As you can see from previous posts, I do understand some conditions when "sudo" is safer than when it is not.  I understand some conditions when it is not safe, though I would not claim that I have given an exhaustive list.  I prefer to not work on this limited knowledge.  With security policy, I prefer to know.  Where you choose to use the unknown factors in your policy is up to you (for example, I have to use the kernel, despite any bugs it may have - and I cannot read the entire kernel source, nor do I possess the skill to remove all the bugs if I did - if I did, I would be doing what Paul Starzetz is).

By the way, an interesting aside can be seen in "vudo".  An old article, admittedly - but, similar bugs could happen again.  Note that was not a bug in "sudo", and not a bug in "sudoers".  I believe that "sudo" can help some situations.  I believe that "sudo" a solution to the common problem we have.

Please if you wish to address do not make assumptions about my knowledge.  I have been courteous enough to steer clear of doing so with you.  I find it quite offensive that you assume I would not have done things as simple as reading a manual page or knowing of race conditions.  Please do not degrade your otherwise intelligent posts with thinly-veiled insults.

---

### Post by LordHunter317 on 2005-05-25
[QUOTE=vague-]The whole point of the statement is about whether the user is cautious.[/quote]That's not something sudo can control either.  Hence my original statement about sudo policy being damage control during an attack, not prevention.

User cautiousness is a social/network problem.  Something that has to be addressed in different ways.  Hence my original comment: "Once an account is compromised, it's over".  Modern machines have too many entry vectors to reliably cover all those bases.

> Except, I did not say that you needed write access to logs.No, you didn't.  I assumed and I apologise.  However, I still think it's an incredible amount of complexity gain for almost zero benefit.

> Further, I should think everybody in here understands race conditions,No, I suspect the vast majority of people on this forum do not understand race conditions, let alone know what those words mean. 

>  I do not understand why you try and offend me,I'm not trying to offend you, but your original statement didn't look like you'd considered many possible attack vectors.


> If you are not capable of physically powering down the machine (for example, it is on another continent, let alone if it is three hours away), the best you can do is to enact your policy and tell the local team to take it down.And if you can't do this with one phone call and have the box off in 5 minutes, you're doing something wrong.


>   First, you will note that certain variables are left unchanged from the old environmentYeah, TERM if you use env_reset.  Everything else is cleared.

>  Second, sometimes it is necessary to allow other environmental variables through due to the way programs work.Yes, it doesn't cover this solution.  My point is is that Solar Designer was wrong when he said you couldn't make -i the default.  

You in that paragraph wasn't referring to you personally.  It was the inpersonal second-person.  


>  I understand some conditions when it is not safe, though I would not claim that I have given an exhaustive list.The exhaustive list of conditions you can do anything about is pretty small.  Environment variables, commands that have interactive portions (i.e., can spawn a shell or run commands) are the two things you really have to worry about.  The third is what arguments are allowed to run, and that can be solved with wrapper scripts.  Whether you need that much security is up to you.

I'd like to reiterate that the UNIX security model is so fundamental flawed that once an attacker has compromised any account, you really ahve to treat the whole box as compromised.  Your sudo policy is just damage control once a box is compromised.

Which is why most people/groups write their policy based on how much they trust the users who will be using sudo and don't worry excessively about someone breaking in to their box.  It's just not a cost-effective way to deal with an attacker.  And in the real-world, time==money, so you tend to select the solution that gives you the most gain for the time spent on it.  Which generally isn't make your sudoers policy perfect so it doesn't specify anything more than what is strictly allowed.

> I find it quite offensive that you assume I would not have done things as simple as reading a manual pageYou misinterpreted my post.

>  or knowing of race conditions.While I was making a false assumption, if that was assumption was true, it's plainly obvious that you hadn't considered a race condition as an attack on your solution.

>   Please do not degrade your otherwise intelligent posts with thinly-veiled insults.They're not insults.  If I was going to insult you, I'd make it perfectly and plainly clear.  Really.

---

