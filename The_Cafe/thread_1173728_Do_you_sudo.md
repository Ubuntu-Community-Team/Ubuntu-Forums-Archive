---
title: "Do you sudo?"
date: 2009-05-30
forum: The Cafe
---

### Post by drokmed on 2009-05-30
How much do you rely on sudo?

---

### Post by jowilkin on 2009-05-30
To run commands that require it?  I don't get the poll.  You should only use sudo when it's required, and when it's required you have no choice but to use it...

---

### Post by Elfy on 2009-05-30
Moved to Cafe

---

### Post by lisati on 2009-05-30
I *sometimes* use sudo, and find myself in agreement with jowilkin - sudo isn't always necessary.

---

### Post by CJ Master on 2009-05-30
I think he means vs Su.

I personally use them 50/50, sudo if just using pacman - but su if working with config files.

---

### Post by drokmed on 2009-05-30
Hi all,

I apologize to the moderators.  I was looking for feedback from a more active topic group, but I should have thought better.  My bad.  Still, I'd appreciate your responses to this too!  How much do you rely on sudo?

Warmest regards,

Daryl

---

### Post by pbpersson on 2009-05-30
> **CJ Master said:**
> I think he means vs Su.

I personally use them 50/50, sudo if just using pacman - but su if working with config files.

Sue Who?  :o

---

### Post by CJ Master on 2009-05-30
--never mind this post :P --

---

### Post by drokmed on 2009-05-30
> **CJ Master said:**
> I think he means vs Su.

Yes.  Exactly.

Thank you for clarifying.  I should have been more specific.

---

### Post by Elfy on 2009-05-30
> **drokmed said:**
> Hi all,

I apologize to the moderators.  I was looking for feedback from a more active topic group, but I should have thought better.  My bad.  Still, I'd appreciate your responses to this too!  How much do you rely on sudo?

Warmest regards,

Daryl

Not a problem - probably more active here while people keep it on the forn page - it would get lost in general help anyway.

I use it when I need to.

---

### Post by gn2 on 2009-05-30
I much prefer crosswords to those annoying number grid things.

---

### Post by Eisenwinter on 2009-05-30
> **drokmed said:**
> How much do you rely on sudo?
I don't use sudo, I use su.

---

### Post by drokmed on 2009-05-30
> **CJ Master said:**
> You might try clarifying what you mean by how often we use sudo. :D

Sorry, my bad.  I should be more specific.  Let me rephrase this:

When you need to execute a command that requires root privileges, what do you TYPICALLY do, not what you prefer (be honest here):

1.  just drop into 'su -' and knock it out
2.  enforce the 'sudo' environment always, keep it safe

Sorry for the confusion!

---

### Post by drokmed on 2009-05-30
> **jowilkin said:**
> To run commands that require it?  I don't get the poll.  You should only use sudo when it's required, and when it's required you have no choice but to use it...

When it's required?  When is sudo required?  I can't think of even one example.  When do you consider sudo required?

I know what some of you are thinking.  I'm not trying to start some stupid flame war.  I 'su -' when I need to install something, or mod a system file such as /etc/resolv.conf.  The whole concept of sudo is "required" boggles me.

Start over.

The poll asked how much you RELY on sudo.  Either you use it or you don't.  Never?  Always?  Usually?  Sometimes?  Just looking for honest answers here.  Don't care about the philosophical gobbledygook!

---

### Post by drokmed on 2009-05-30
> **gn2 said:**
> I much prefer crosswords to those annoying number grid things.

You wasted our time reading that nonsense.  What exactly was your point?

---

### Post by gn2 on 2009-05-30
> **drokmed said:**
> You wasted our time reading that nonsense.  What exactly was your point?

Humour. 

This whole thread is nonsense, I was just trying to inject some light relief.

---

### Post by gjoellee on 2009-05-30
I use sudo when it is necessary

---

### Post by fatality_uk on 2009-05-30
> **gn2 said:**
> I much prefer crosswords to those annoying number grid things.

:lol:

That took a few seconds to reach the bit of my brain that was awake :D

---

### Post by lisati on 2009-05-30
> **fatality_uk said:**
> :lol:

That took a few seconds to reach the bit of my brain that was awake :D

LOL: I just got it too and I'd seen the reference some time back...... I think I'll say some crosswords to myself.

---

### Post by drokmed on 2009-05-30
> **gn2 said:**
> Humour. 

This whole thread is nonsense, I was just trying to inject some light relief.

Thank you for the honest response.  This whole thread is nonsense?

LOL  You can't leave it at that.  I don't understand your disdain for the thread.  Please clarify.  Do NOT confuse your post count with knowledge.

You never dropped into 'su -' to get things done?  I do it all the time.  I drop into root, and tweak config files and restart services to get things working correctly.  sudo would be a waste of my time in that regard.  Any engineer worth his/her merit is comfortable with the command line.  Heard of man pages?

Again, when would you consider 'sudo' required for usage?  Hence the poll.  It's a simple question.

---

### Post by v8YKxgHe on 2009-05-30
sudo can do a lot more than just give you permission to run things as root, drokmed. 

Sudo is a very, very powerful tool when you want it to. Sure many people just use it to escalate their permissions to that of root, like the normal 'sudo apt-get update' etc, though you can fine tune which users can run what commands (even with what arguments), from what host, in what group, as which users, the list goes on. It is incredibly powerful.

I don't think it is fair to compare 'sudo' with 'su -', they do completely different things and so the poll is flawed from the start.

---

### Post by samjh on 2009-05-30
@ **drokmed**

Ubuntu has the root account disabled by default, so su is essentially useless.  The official method for invoking root privileges in Ubuntu is via sudo.

For me when using Arch or other distros, it depends on the situation.  If I expect to do several tasks which require root privileges, I'll use su.  If it's just one or two tasks, I'll use sudo.

Having said that, sudo is very handy if you are administering a multi-user system or a system with multiple admin-level users.  Sudo differentiates between users who have root privilges, so it's more useful for security auditing and access control than plain su.

---

### Post by drokmed on 2009-05-30
> **AlexC_ said:**
> I don't think it is fair to compare 'sudo' with 'su -', they do completely different things and so the poll is flawed from the start.

'sudo' and 'su -' do completely different things?  Are you kidding me?  Gee, I want this command to run as root, which way do I go?

Don't confuse technique with enabler.  From an implementation standpoint sure, that's the whole point.  Hence the poll!

The difference is the whole point of the poll.  The poll asks which do people prefer?  I don't understand the resistance to this poll.  Which do you typically use?  Is that such a bad question to ask?

Do you sudo?

Do you 'su -'?

What's your preference?

OMG your not allowed to ask that!  You evil wretched soul!

---

### Post by gn2 on 2009-05-30
> **drokmed said:**
> You never dropped into 'su -' to get things done? 

Not once ever.

sudo is just four letters that appear at the start of things that I very occasionally copy and paste into a terminal when there is no GUI option.

As for knowledge and post count, you're correct, post count is no measure of knowledge whatsoever.
But I would also point out that you have no idea what my knowledge is, nor I yours.

---

### Post by v8YKxgHe on 2009-05-30
> **drokmed said:**
> 'sudo' and 'su -' do completely different things?  Are you kidding me?  Gee, I want this command to run as root, which way do I go?

Do you sudo?

Do you 'su -'?

What's your preference?

OMG your not allowed to ask that!  You evil wretched soul!

No, I am not kidding you. If you would like to read up on those 2 commands, you will see that they are completely different. Do you even know what sudo can fully do? I don't think you do. All you seem to think it can do is run things as root, of which you're **very** wrong.

Yes, sudo can let you run things as root, and by default in Ubuntu it is setup so the first user can escalate their permissions to root. However sudo can do far, far, far more than this - so I highly suggest you read the man pages (like you suggested other users to do) on sudo, and look at the incredible flexibility and differences between 'sudo' and 'su -'.

I'm also not entirely sure why you're attacking and refusing to believe what people are telling you. Please, read up on sudo, and su -

---

### Post by lisati on 2009-05-30
I think I need to get my mind out of the gutter with all this talk of "root privileges"......

---

### Post by drokmed on 2009-05-30
Sorry boys and girls, I see where this is going.  I'm sure some of you do to.  Not all of us here administer networks with a mixture of hosts and servers, some of them UNIX/Linux based.

Give me one example where 'sudo' can do something where 'su -' cannot.  Yeah, yeah, it's quicker.  That's not the point.  Hence the poll.  Gee, it's a simple poll!  LOL whatever...

---

### Post by v8YKxgHe on 2009-05-30
> Give me one example where 'sudo' can do something where 'su -' cannot.

Limit user 'foobar' to run only the command '/bin/mv foo_[a-zA-Z]* /etc/foobar' as root, with or without password.

For details, 'man sudoers' has many examples

---

### Post by drokmed on 2009-05-30
> **gn2 said:**
> Not once ever.

sudo is just four letters that appear at the start of things that I very occasionally copy and paste into a terminal when there is no GUI option.

As for knowledge and post count, you're correct, post count is no measure of knowledge whatsoever.
But I would also point out that you have no idea what my knowledge is, nor I yours.

Sorry to hear that.  Linux is capable of some pretty powerful stuff.  Some day, you'll get the urge to build a server such as this:

[http://www.howtoforge.com/perfect-server-centos-5.2-ispconfig-3](http://www.howtoforge.com/perfect-server-centos-5.2-ispconfig-3)

No sudo there, just plain getting it done.  You'll see.

---

### Post by gn2 on 2009-05-30
> **drokmed said:**
> Some day, you'll get the urge to build a server such as this:

Now you would have us believe you can predict the future!
Where will the hilarity end.

---

### Post by drokmed on 2009-05-30
> **AlexC_ said:**
> Limit user 'foobar' to run only the command '/bin/mv foo_[a-zA-Z]* /etc/foobar' as root, with or without password.

For details, 'man sudoers' has many examples

Alex, I'm starting to like you :)  Send me your resume.

Yes, sudo has it's uses.  As the IT Director, I've authorized sudo permissions for my lead engineers, mainly when they tell me so ;), one example is to update databases on our servers.  That's not the point.  You people kill me!

I thought the poll was simple!  Do you sudo?

My god, all this philosophical crap is boring.  People just don't get it.  Do you sudo?

---

### Post by fatality_uk on 2009-05-30
> **drokmed said:**
> My god, all this philosophical crap is boring.  **People just don't get it**.  Do you sudo?

We might not get it, I sure as heck don't. Unless I am missing some really deeply hidden punch line here, your question "Do you sudo? is like asking, "Do you click?" It's pointless.

---

### Post by dragos240 on 2009-05-30
Yep. All the time, when I need to partition a USB or something, or do something that requires root privileges.

---

### Post by anarchyinc on 2009-05-30
Sudo isn't even installed on my computer, and it never will be.

---

### Post by caravel on 2009-06-01
> **fatality_uk said:**
> We might not get it, I sure as heck don't. Unless I am missing some really deeply hidden punch line here, your question "Do you sudo? is like asking, "Do you click?" It's pointless.
It's pretty obvious that the question is "sudo vs su"?  Sudo was never really intended to be used how it is in Ubuntu.  The whole idea of sudo was to give a few chosen normal users *certain specific* root privileges for running certain tasks and not to give a user full root access with a time out.  Most other distros don't have sudo set up in this way, or at all and users simply open a terminal, su to root, enter their password, enter commands and close the terminal.

With Debian if anyone ever compromises your user account password that's all they've got.  Without root privileges there's not a lot they can do.  With Ubuntu once they've got account password they can "sudo" as much as they like or even "sudo passwd root" and the system is compromised.

The reason why many Ubuntu users use sudo instead of su is because Canonical tell them to and most don't seem to question it.  This is probably because they want a more windows-like feel without all of the security and permissions "getting in the way".

---

### Post by runningwithscissors on 2009-06-01
No, I do not. Mostly because nobody other than me uses my computer really, so I don't need it.
And Debian doesn't come with sudo installed, and I'm too lazy to install and configure it.

---

### Post by bizhat on 2009-06-01
When i was using fedora, i always use su -. I like "su -" more than sudo, i need to type my complicated password always (ubuntu are uers expected to use simple pasword ?).

I have enabled root account on ubuntu. I do use both "su -" and "sudo". I have done the same thing when i was using FreeBSD, enable direct root access. If you have a secure password, thats all. 

May be i am wrong because i am new to sudo

---

### Post by monsterstack on 2009-06-01
I use sudo quite a bit on Ubuntu, but never bother with it on Debian. Can anyone tell me the difference between running these two commands?

```
sudo -s
su
```

---

### Post by sisco311 on 2009-06-01
> **bizhat said:**
> When i was using fedora, i always use su -. I like "su -" more than sudo, i need to type my complicated password always (ubuntu are uers expected to use simple pasword ?).

I have enabled root account on ubuntu. I do use both "su -" and "sudo". I have done the same thing when i was using FreeBSD, enable direct root access. If you have a secure password, thats all. 

May be i am wrong because i am new to sudo

By default, in Ubuntu, the pam authentication rules for su are way to permissive. Basically any user can use su. On a single user system with a locked root password this is not a big security issue.

In a multiuser environment, I would force users to be a member of a group before they can use "su". I prefer the "traditional" *wheel* group for this purpose.

For this, I have to create the group (one could use any available gid):
```
sudo addgroup --gid 11 wheel
```
then edit the /etc/pam.d/su file to something like this:
```
auth       sufficient pam_rootok.so
auth       required   pam_wheel.so group=wheel
...
```
oh, and add my user to the wheel group:
```
sudo adduser username wheel
```





And to answer the OP's question, yes I do use sudo. My main os is Arch and I only use my root password to login in single user mode. But sulogin is patched in Ubuntu to handle the default case of a locked root password.

---

### Post by wurm on 2009-06-01
how would i be able to allow su to login?

---

### Post by Regenweald on 2009-06-01
Sudo aptitude update and sudo gedit /etc/'something'. The gnome and kde gui's are coming along in leaps and bounds, so the terminal is there for for those who chose.

---

### Post by y6FgBn)~v on 2009-06-01
When it is required I always use it.

---

### Post by fatality_uk on 2009-06-01
> **Regenweald said:**
> Sudo aptitude update and sudo gedit /etc/'something'. The gnome and kde gui's are coming along in leaps and bounds, so the terminal is there for for those who chose.

Just a wee point:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by doas777 on 2009-06-01
well, not to sound trite, but I use sudo/gksu exactly as often as i need it. no more, no less.

---

### Post by z0mbie on 2009-06-01
I use sudo with password disabled.

---

### Post by Neheb on 2009-06-01
gotten into a bad habit of login into root lately when installing arch, but I try to use sudo instead.

---

### Post by swoll1980 on 2009-06-01
I don't think I've ever used su in Ubuntu. I always use sudo. I don't even think I have su set up.

---

### Post by sisco311 on 2009-06-01
> **swoll1980 said:**
> I don't think I've ever used su in Ubuntu. I always use sudo. I don't even think I have su set up.
su is installed by default in Ubuntu. it's safe because (by default) the root password is locked, so you can't su to root.

---

### Post by swoll1980 on 2009-06-01
> **sisco311 said:**
> su is installed by default in Ubuntu. it's safe because (by default) the root password is locked, so you can't su to root.

Yeah, but you have to set the su password, and I haven't even done it yet.

---

### Post by sisco311 on 2009-06-01
> **swoll1980 said:**
> Yeah, but you have to set the su password, and I haven't even done it yet.
su prompts for the target user's password. 

i.e.
```
su sisco311 -
```
will prompt for sisco311's password. 

you can still use su to change your user ID to a non-root user (which has a password set)

---

### Post by Simian Man on 2009-06-01
I think su is better.  It should say something that Ubuntu is the only major distro that uses that weird sudo setup.

---

### Post by sisco311 on 2009-06-01
> **Simian Man said:**
> I think su is better.  It should say something that Ubuntu is the only major distro that uses that weird sudo setup.
i would say that both su and sudo are useful commands/tools.

sudo is much more flexible than su, it has far more configuration options then su.

so, why do you think that su is better?

---

### Post by Odemia on 2009-06-02
I used su exclusively before ubuntu.  Then when I started working and ubuntu was the OS of choice at work I started using 'sudo' when I just need to run one or two lines.  When I have a bunch of work to do that needs higher privelages I use 'sudo su'.

So, does 'sudo su' count as sudo, su or both?

---

### Post by monsterstack on 2009-06-02
> **Odemia said:**
> I used su exclusively before ubuntu.  Then when I started working and ubuntu was the OS of choice at work I started using 'sudo' when I just need to run one or two lines.  When I have a bunch of work to do that needs higher privelages I use 'sudo su'.

So, does 'sudo su' count as sudo, su or both?

I'd like to know that too. And whether either of those are equivalent to running "sudo -s" as well.

---

### Post by sisco311 on 2009-06-02
> **Odemia said:**
> 

So, does 'sudo su' count as sudo, su or both?

> **monsterstack said:**
> I'd like to know that too. And whether either of those are equivalent to running "sudo -s" as well.

[thread=983645]Difference between sudo su and sudo -s[/thread]

---

### Post by monsterstack on 2009-06-02
> **sisco311 said:**
> [thread=6188826]Difference between sudo su and sudo -s[/thread]

Ah very informative. Thanks for that!

---

### Post by Mistrblank on 2009-06-02
When you go to an enterprise level setup with clusters of servers, it is far easier to modify the sudoers file and allow users access to a command, group of commands or access to another user id.  I currently restrict users on my hosts to log in via their user id and use sudo to execute commands as oracle on our databases.  Similarly we do this with our web administrator account.  So we use it for far more than just root access.  

The primary reason we do this is that there are multiple administrators for every host.  Sudo provides a very convenient log of who is doing what and where as well as allowing us to keep all of the passwords restricted.  

So, yes if someone gets a user's password, they have access to other permissions, but that's why you enforce strict password policies.   It's much easier to make users remember their passwords and make them change it every few weeks than it is to change root password on 50, 100 or 1000's of systems at one time and distribute that password safely.  Someone will inevitably not get the memo and be locked out.    

And Ubuntu is by far not the only distribution that uses sudo by default.  Ubuntu  still provides privelege separation so the user isn't required to be root for everything or expose the root password through overuse.  This is good.  If you're worried about someone getting the password and hacking your box, I think you need to evaluate how you think that will happen.  I would turn off all remote logins (ssh, vnc, remote X sessions, etc), examine your firewall and perhaps create an alternative authentication mechanism to allow you to have a separate password to login from the system password to authenticate sudo.

---

### Post by doas777 on 2009-06-02
> **sisco311 said:**
> [thread=6188826]Difference between sudo su and sudo -s[/thread]

links no longer valid. says no thread specified

---

### Post by khelben1979 on 2009-06-02
I never need to do this in Debian. To be honest, I experienced it to be irritating the last time I did it with Ubuntu (last year). I didn't like it at all.

---

### Post by aysiu on 2009-06-02
> **doas777 said:**
> links no longer valid. says no thread specified
Don't use *sudo -s*

That's the bottom line. If you need a persistent root prompt, use ```
sudo -i
```

---

### Post by doas777 on 2009-06-02
> **aysiu said:**
> Don't use *sudo -s*

That's the bottom line. If you need a persistent root prompt, use ```
sudo -i
```

Thank you!

---

### Post by sisco311 on 2009-06-02
> **doas777 said:**
> links no longer valid. says no thread specified

sorry.

[thread=983645]Difference between sudo su and sudo -s[/thread]

---

### Post by lisati on 2009-06-02
<chit-chat>Maybe I've been fortunate or just cautious, but in the 2 years I've been using Ubuntu, I think I've only used a persistent root, e.g. **sudo -i**, only once or twice.</chit-chat>

---

### Post by doas777 on 2009-06-02
> **lisati said:**
> <chit-chat>Maybe I've been fortunate or just cautious, but in the 2 years I've been using Ubuntu, I think I've only used a persistent root, e.g. **sudo -i**, only once or twice.</chit-chat>

agreed. I did it like once in the long-long-ago, because a tutorial told me too. at the time i didn't realize it was optional. was I ever that much of a noob?

---

### Post by billgoldberg on 2009-06-02
> **drokmed said:**
> How much do you rely on sudo?

I answered "never" just to say **useless poll**.

Everyone sudo (or gksu) to get anything done that requires root access.

Or they use a root account.

---

### Post by sisco311 on 2009-06-02
> **billgoldberg said:**
> 
Everyone sudo (or gksu) to get anything done that requires root access.

Or they use a root account.

or su
or they use PolicyKit ;)

---

### Post by Odemia on 2009-06-03
Didn't know about "-i", looks like it is better than su.  Learn something new every day.

---

### Post by glotz on 2009-06-03
> **drokmed said:**
> Yes.  Exactly.

Thank you for clarifying.  I should have been more specific.

You know, you still can edit that first post.

---

### Post by [S2] on 2009-06-03
I usually ```
sudo su
```

---

### Post by infoseeker on 2009-06-03
I created an alias in ~/.bashrc
```
alias su='sudo -i'
```
Works for me.

---

### Post by WatchingThePain on 2009-06-03
Do I sudo?..:oops:

Pardon me, Ahm a Lady.

---

### Post by Dark Aspect on 2009-06-03
I voted usually but it really depends on the OS, on Ubuntu I use sudo in most cases. On other Linux OSes I use su simply because sudo isn't always installed. For example, if I created a user on Puppy Linux or DSL that is not root (yes its possible) than I would use su.

---

### Post by b4k4 on 2009-06-06
sudo irritates the hell out of me. nothing worse than having to keep using up arrow, home, type bloody sudo, press enter
Sudo is good for
[INDENT]sudo passwd root[/INDENT]
give me control - its my computer.

---

