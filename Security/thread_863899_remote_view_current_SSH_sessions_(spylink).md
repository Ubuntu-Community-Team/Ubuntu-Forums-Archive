---
title: "remote view current SSH sessions (spy/link)"
date: 2008-07-18
forum: Security
---

### Post by tuproxy on 2008-07-18
I was just informed that it is possible to install an app that allows you to either share an SSH session or to be able to view the current SSH session that you have rights to. 

Does anyone know what this command or process is called?

Thanks.  This makes me feel less secure, but I guess you have to know the password to view the share anyway.

---

### Post by Dr Small on 2008-07-19
I have never heard of this. Could you please provide a little bit more background information on it?

Dr Small

---

### Post by Gamma746 on 2008-07-19
That sounds like screen in multiuser mode.

---

### Post by tuproxy on 2008-07-19
> **Dr Small said:**
> I have never heard of this. Could you please provide a little bit more background information on it?

Dr Small

Ok.  I was told by a co-worker that if you are logged into one of our servers (we always log in as root :confused:) the session can be monitored/viewed, with an installed package, by another user with root access.  So both people have to know the root password so I guess security isn't much of an issue.  

I just don't like all of us using the same root access.  I don't want to get blamed for someone else's mistake.   What would be the benefit of everyone using the root account?

---

### Post by Gamma746 on 2008-07-20
> **tuproxy said:**
> What would be the benefit of everyone using the root account?
Do you mean that everyone has a normal account with su/sudo permissions, or that everyone logs in as root?  If it's the latter, then that's a terrible idea with no real benefits.

---

### Post by tuproxy on 2008-07-20
> **Gamma746 said:**
> Do you mean that everyone has a normal account with su/sudo permissions, or that everyone logs in as root?  If it's the latter, then that's a terrible idea with no real benefits.


Everyone logs in as root, even through remote - offsite SSH!  I was given full access the first day of work!  This blew my mind.  

I'm wondering what security and liability risks are opened up due to this type of action.  

Can someone please give me some comments about this and it's professionalism?

Thanks a lot.

---

### Post by scorp123 on 2008-07-21
> **tuproxy said:**
> Everyone logs in as root, even through remote - offsite SSH!  This is insane!! And totally unprofessional if it's true.

... Mind to share the login details? :twisted: :twisted: :twisted:

---

### Post by tuproxy on 2008-07-21
> **scorp123 said:**
> This is insane!! And totally unprofessional if it's true.

... Mind to share the login details? :twisted: :twisted: :twisted:

The only protection is that her has the default port changed and IPban (or whatever it is called) so people who repeatedly try to log in get banned.  I'm not sure of the rules but I'm told this is in effect.  I've seend a list of banned IP's and ISP...

Can you expand on your thoughts about Root login.  What is the worst part of it?  Why is it so bad?  

I'm the new guy who is just learning the system.  The 3 admins have been there for 6+ years and are very "good" with linux in their own minds..

PLEASE tell me the issues here so I can learn what and why not to do things.  

Thanks!

---

### Post by scorp123 on 2008-07-21
> **tuproxy said:**
>  Can you expand on your thoughts about Root login.  There is nothing to expand. "root" should only be used when you have admin work to do, and it definitely should not be possible to login directly as "root", especially not from outside. 

Whoever set this up is a moron, sorry to say so.

> **tuproxy said:**
>  What is the worst part of it?  I don't know where to begin .... This is horrible.

> **tuproxy said:**
>  Why is it so bad?  Having "root" access and therefore God-like infinite powers with nothing whatsoever stopping you from doing anything you want? Answer that one yourself. It should be obvious why this is bad.

> **tuproxy said:**
>  PLEASE tell me the issues here so I can learn what and why not to do things. It's simple: **Don't you ever type a command without 100% knowing what it does!!**

How did you get that job anyway?? :confused:
.
.
.
.

---

### Post by tuproxy on 2008-07-22
> **scorp123 said:**
> There is nothing to expand. "root" should only be used when you have admin work to do, and it definitely should not be possible to login directly as "root", especially not from outside. 

Whoever set this up is a moron, sorry to say so.

 I don't know where to begin .... This is horrible.

 Having "root" access and therefore God-like infinite powers with nothing whatsoever stopping you from doing anything you want? Answer that one yourself. It should be obvious why this is bad.

 It's simple: **Don't you ever type a command without 100% knowing what it does!!**

How did you get that job anyway?? :confused:
.
.
.
.

You didn't tell me anything I didn't know. 
Maybe I didn't explain the situation clearly enough.
We are all admins.  I'm just the newest one. 

  We are in a Linux/MS server enviornment so we SSH into all machines.  BUT when we do access the local machine at the interface, we use root as well.  direct/local access is very rare as we SSH in 99% of the time.  

I'm just wondering if there isn't a standard where we use usernames and then sudo or su for administrative changes.  I just am wondering if all the admins log in as root, how can they tell which one ran what command or made what mistake.  

I'm not a linux admin.  95% of my time was with MS but I'm learning Linux now..

---

### Post by daleus on 2008-07-22
> **tuproxy said:**
> I'm just wondering if there isn't a standard where we use usernames and then sudo or su for administrative changes.


Yeah, this is how it should be done, but if everyone when using ssh to connect is using "root" then it has been setup horribly, mention it to them, if they have a good reason, then fine, but if its "Oh its easier" or "otherway was too difficult" you might wanna tell your bosses, because if something bad happens, all of you (even you, newguy) would get yourself fired.

---

### Post by cpetercarter on 2008-07-22
I think this misuse of root privileges is more common than you might think.

Six months ago, I needed to move my website to a private server. I signed a deal with one of the UK's major hosting providers. The server runs on Ubuntu. Everything is set up for you,they told me, and by the way if you need to make any changes, here is the root password.

I happily played around with the new server using ssh with the root password for several weeks before it dawned on me, from reading a book about Ubuntu and from this forum, that this was not a good idea! So I set up an admin user and started to use sudo, and have forgotten the root password!

---

### Post by scorp123 on 2008-07-22
> **tuproxy said:**
>  I'm just wondering if there isn't a standard where we use usernames and then sudo or su for administrative changes.  We do that here, so it's obvious from the system's log who did what and when and how. Every execution of "su" or "sudo" is recorded to /var/log/messages  ... if anything ever goes wrong it's fairly easy to reproduce the steps.

> **tuproxy said:**
>  I just am wondering if all the admins log in as root, how can they tell which one ran what command or made what mistake. If everybody logs in directly as "root" (= no login as ordinary user and then use of "su" or "sudo" ....) then this gets very hard. Maybe the IP address gets recorded, but that's about it.

---

### Post by scorp123 on 2008-07-22
> **daleus said:**
> Yeah, this is how it should be done, but if everyone when using ssh to connect is using "root" then it has been setup horribly, mention it to them, if they have a good reason, then fine, but if its "Oh its easier" or "otherway was too difficult" you might wanna tell your bosses, because if something bad happens, all of you (even you, newguy) would get yourself fired. Absolutely! 100% agree to what you wrote up there.

---

### Post by eentonig on 2008-07-22
Why not to use root (as default account or for ssh access):
--------------------

1. You loose one layer of security. To gain access, hackers need to know 2 things. A username and a password. You've just given them one of those, so they only have to concentrate on the password.
2. If someone leaves the company, you need to inform everybody about the new root password (or leave a huge hole if you don't change it).
3. You have no audit trail if something happens. It was 'root' to blame (or better, ask what/why something changed).
4. If everybody uses root for everything, even testing (scripts, programs, ...) will be done as root. I hope nobody ever screws up.

If you use sudo (and root password disabled):
- root access via ssh can be blocked. Only allow ssh access for people who are supposed to log in (thus making it harder for hackers to guess usernames as well).
- Everybody is accountable for what he did. Saves you a lot of time when you need to find why something was changed.
- People can still become root if needed, by issuing 'sudo su'.

---

### Post by mikejen on 2008-07-22
Hi

Seems to me that someone doesnt understand why we dont use root unless absolutely neccessary. For most things sudo will suffice, its usage should be logged (if it isnt then it should be for traceability).
Root allows a simple typo to do a lot of damage and thats not considering the malicious individual who is using root to hide their activities.
It might be an idea to make root nologin and force the use of sudo.

---

### Post by moonpup on 2008-07-22
You should stop root from logging in directly over ssh and use your own login and then su to root. Read the link below on how to setup a way to keep seperate history files for each user who su's to root and the commands they ran.

[http://moonpup.blogspot.com/2007/11/keeping-separate-history-files-for.html](http://moonpup.blogspot.com/2007/11/keeping-separate-history-files-for.html)

---

### Post by hennotaht on 2010-01-08
> **tuproxy said:**
> ...the session can be monitored/viewed, with an installed package, by another user with root access...
I really would like to get an answer for that original question. Anyone knows such a package?

I know that it is possible to this:
[http://www.jms1.net/ssh-record.shtml](http://www.jms1.net/ssh-record.shtml)

But I really wouldn't want to disable password login.

---

### Post by BkkBonanza on 2010-01-08
There are two ways that come to mind.

1. Replace the bash shell with a modified version that has code to create a tap in point allowing monitoring via some side connection. You can try to verify your shell is authentic by checking it's hash against what you think it should be for that version in the repos.

2. Some tricky stuff done with pseudo terminal pairs. I don't really understand this but it appears that a program can be made to pair up to a pseudo terminal like the ssh logins would use. I haven't found a definitive how-to on this, just stuff that sounds like it may work. The ssh session runs on the master and another program can be paired to it as a slave. That's about all I've come across.

Actually a third way would be to force the ssh session to run "screen" at login without a user knowing (maybe as restricted command, or using ~/.ssh/rc). If that was done then another user could attach to it easily enough I believe, with "screen -x".

However, with root access any of these tricks should be detectable.

---

### Post by Sarmacid on 2010-01-08
I would think it was done with screen, you can see how in the link [http://www.ibm.com/developerworks/linux/library/l-10sysadtips/index.html?ca=drs-#T3](http://www.ibm.com/developerworks/linux/library/l-10sysadtips/index.html?ca=drs-#T3)

---

### Post by bodhi.zazen on 2010-01-08
Use screen + ssh keys with forced commands.

[http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/](http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/)

If the shared screen session is terminated, the user is logged out.

Of course, if they are running as root they can cause all kinds of problems and if you do not trust you users, do not let them log in as root, lol

---

### Post by BkkBonanza on 2010-01-08
I did some checking with screen as an automated hidden monitoring method. It doesn't work using ~/.ssh/rc because it hasn't connected at the time it runs - so that method doesn't work. 

Screen itself does work of course but I found it left many tracks behind that would make it hard to deploy as a hidden method. It shows up in ps output so anyone wanting to know if they are being watched could simply look there, and it initially displays a banner screen, though that could likely be disabled. You can type "screen -ls" to see a list of current screens.

I still think with some tricky code changes to screen and ssh this could be accomplished. It would be quite a bit of work to setup unless someone out there has provided a ready-to-go package to do it. I've neve come across that but it sounds possible.

Again, one could verify these binaries against the repo versions with hash checks to be sure they weren't being messed with. In an environment where you don't trust your co-workers I'd say it would be reasonable to verify your tools for you own peace of mind. This kind of deceptive fiddling is similar to installing a rootkit as you're working with tools when you have no idea what they're really doing.

On the other hand your co-worker could just be messing with your mind to try and make sure you don't do anything they wouldn't like.

---

