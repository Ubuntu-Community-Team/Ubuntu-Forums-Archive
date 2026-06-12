---
title: "Tired of typing passwords! help me fix sudoers!"
date: 2009-12-02
forum: Security
---

### Post by jessiebrownjr on 2009-12-02
Hey guys, my desktop at the house has only me and my wife with physical access. I would like to know how secure it is for me to make my sudoers file no longer require me to type any passwords (or as little as possible)?

I tried the variations of what I thought was correct, but it wasn't... one attempt left me staggering to reboot into safe mode to fix it :-)

Unless this opens me up to remote attacks, I'd like to do it. So if possible, please tell me how to change my sudoers and the limitations of doing such a thing. Thanks!

---

### Post by harry71194 on 2009-12-02
It's NEVER a good idea to require sudo to have no password. Anyone could break into your house and run sudo commands without a password. Sudo is a unique function, it does not need to be called every minute, or even hour. If you are requiring it a lot, then something is probably messed up.

I highly suggest against making sudo/root have a pre-entered password.

---

### Post by cdenley on 2009-12-02
Well, if you're worried about someone breaking into your house, encryption is the only protection from physical access. Still, requiring a strong password for privilege escalation does help prevent malicious software from escalating privileges, and forces you to think twice before doing something that can break your system. If you really want it, though, this is how you allow members of the admin group to sudo without a password:
```

sudo EDITOR=gedit visudo

```
Edit the last line to be
```

%admin ALL=NOPASSWD: ALL

```
save, close

Note that you will still need a password for policykit. I'm not sure how to make that not require a password.

---

### Post by jessiebrownjr on 2009-12-02
> **harry71194 said:**
> It's NEVER a good idea to require sudo to have no password. Anyone could break into your house and run sudo commands without a password. Sudo is a unique function, it does not need to be called every minute, or even hour. If you are requiring it a lot, then something is probably messed up.

I highly suggest against making sudo/root have a pre-entered password.

LOL. I hope to God that if somebody breaks into my house, they don't hack my desktop... lol. Anyway back to reality.. you funny guy...

---

### Post by jessiebrownjr on 2009-12-02
> **cdenley said:**
> Well, if you're worried about someone breaking into your house, encryption is the only protection from physical access. Still, requiring a strong password for privilege escalation does help prevent malicious software from escalating privileges, and forces you to think twice before doing something that can break your system. If you really want it, though, this is how you allow members of the admin group to sudo without a password:
```

sudo EDITOR=gedit visudo

```Edit the last line to be
```

%admin ALL=NOPASSWD: ALL

```save, close

Note that you will still need a password for policykit. I'm not sure how to make that not require a password.

Thanks! I'm going to be looking into the AppArmor program later as well. Just did a fresh install and time to tinker!

---

### Post by rookcifer on 2009-12-02
> **jessiebrownjr said:**
> Hey guys, my desktop at the house has only me and my wife with physical access. I would like to know how secure it is for me to make my sudoers file no longer require me to type any passwords (or as little as possible)?

I tried the variations of what I thought was correct, but it wasn't... one attempt left me staggering to reboot into safe mode to fix it :-)

Unless this opens me up to remote attacks, I'd like to do it. So if possible, please tell me how to change my sudoers and the limitations of doing such a thing. Thanks!

I recommend you use Windows if you don't care about security.  Not having a root password is the **worst** possible thing you can do for your PC security.  And no, someone doesn't have to have physical access in order to take advantage of no root password.

---

### Post by BkkBonanza on 2009-12-02
Perhaps a better compromise would be to extend your timeout period?
That is easy to do and gives somewhat more security then no password.
See [http://ubuntuforums.org/showthread.php?t=763142](http://ubuntuforums.org/showthread.php?t=763142)

---

### Post by jessiebrownjr on 2009-12-02
> **rookcifer said:**
> I recommend you use Windows if you don't care about security.  Not having a root password is the **worst** possible thing you can do for your PC security.  And no, someone doesn't have to have physical access in order to take advantage of no root password.


I did ask for examples on why this is bad, so tell me why it is bad :-)

I'm not going to be running code from people I don't trust for instance, although I'm sure somehow something could sneak in..

I don't have a root password persay, (my root acct is disabled)I have no need to type a password after a sudo command on my user's account(which isnt root).

That being said, are you still saying that its bad? I'd like to know how of it is, because I'm learning as I go.

---

### Post by jessiebrownjr on 2009-12-02
> **BkkBonaza said:**
> Perhaps a better compromise would be to extend your timeout period?
That is easy to do and gives somewhat more security then no password.
See [http://ubuntuforums.org/showthread.php?t=763142](http://ubuntuforums.org/showthread.php?t=763142)


This might be an option.. All these security discussions are moot if all this is about local access... If I have concerns on remote access due to no sudo passwords then I shall be concerned.

For instance I have my NFS shares setup on both computers as client/server with icons that mount/umount from a button push.. They require me to enter a password (because I was unable to modify sudeors properly)... This is what inspired me to ask THIS question.

I do have NFS set up. I also have gufw/hosts.allow/deny setup as well. They are basically open to local traffics only. My wifi is wpa2, not really insecure (even if it is, the worst they will find is my TXU bill info :-) ...)

---

### Post by cariboo on 2009-12-02
If your system somehow gets compromised while on the internet, the attacker won't need a root password to do anything, as you have basically disabled it.

There are enough threads in this subforum about systems being compromised either through ssh or vnc because of bad or missing passwords.

---

### Post by jessiebrownjr on 2009-12-02
> **cariboo907 said:**
> If your system somehow gets compromised while on the internet, the attacker won't need a root password to do anything, as you have basically disabled it.

There are enough threads in this subforum about systems being compromised either through ssh or vnc because of bad or missing passwords.

Humor me here. I have VNC disabled and I think ssh too(i haven't enabled it )..
How can I check SSH? 

Basically the attacker needs a shell to do stuff to make use of me not having a sudo password, right?

I'm thinking I can use AppArmor profiles to keep bad code stuff from doing naughty things, but I'm looking into that too..

if I lengthen the timeout period on my sudoers... Does that matter to any attacker? If im logged in, and he shells in, does he need to enter it atleast once ?

---

### Post by BkkBonanza on 2009-12-02
Changing the sudo timeout just reduces the window of opportunity while also reducing the hassle you complain about of typing the password so often.

By extending the timeout it means you still have a password whereas disabling the password means that any process gaining access as any user in sudo group can hop to root fairly easily. It is exactly this assumed root ability that makes viruses and trojans so much trouble on Windows. 

Another thing to consider is why you need to sudo so much. Are you spending most of your time doing system maintenance? If so, then maybe you would be better served keeping a password but using a console and "sudo su" to keep it open for system maintenance (while you're at the machine).

---

### Post by jessiebrownjr on 2009-12-02
> **BkkBonaza said:**
> Changing the sudo timeout just reduces the window of opportunity while also reducing the hassle you complain about of typing the password so often.


Window of opportunity for WHO? Local attackers, or outside attackers, or what? Please speficy if you don't mind..
> 
By extending the timeout it means you still have a password whereas disabling the password means that any process gaining access as any user in sudo group can hop to root fairly easily. Did I disable the password literally by the afformentioned method for remote logins as well? or does it just turn off sudo's need and solely sudo commands need...
> 
Another thing to consider is why you need to sudo so much. Are you spending most of your time doing system maintenance? If so, then maybe you would be better served keeping a password but using a console and "sudo su" to keep it open for system maintenance (while you're at the machine).This part isn't relevant to why i'm asking, or the questions I asked earlier. I want to know if having SSH + VNC off, firewalls up, and AppArmor profiles in place, if im really at risk to having an outside attack... If ALL THAT above there REALLY leaves me WIDE open, then I'd put it back.. but once again, I don't have anything entirelly too crucial on my box... And I don't recall why I type sudo so much, but I do.. I am trying out new things often, and have two PCs, and like I said, matter of prefference if this isn't a super security breach.

---

### Post by BkkBonanza on 2009-12-02
Any attacker. Expected or unexpected. Security is about reducing attack surface. If I could tell you exactly how someone could get into your system I'd be better off showing you than talking about it. If you feel fine about giving up some level of protection for convenience, then go ahead and do it. No one here is going to worry about your system.

---

### Post by jessiebrownjr on 2009-12-02
What do you mean expected or unexpected?

I'm legitamately trying to find out if this is insecure to remote attackers. I know its insecure to local attackers, but nobody will be 1) on my keyboard or 2) on my lan.

lol, ugh. I'm aware im removing a small layer of security, but what im getting is it... isn't the sudo problem the last leg of the "attackers" race..? if my system is already breached, wouldn't that probably be the last of their problems?

---

### Post by Ms_Angel_D on 2009-12-02
> **jessiebrownjr said:**
> What do you mean expected or unexpected?

I'm legitamately trying to find out if this is insecure to remote attackers. I know its insecure to local attackers, but nobody will be 1) on my keyboard or 2) on my lan.

lol, ugh. I'm aware im removing a small layer of security, but what im getting is it... isn't the sudo problem the last leg of the "attackers" race..? if my system is already breached, wouldn't that probably be the last of their problems?

Whether it is the last leg or not it is ultimately the most important, the reason windows is so prone to malware and virus infection is because users are allowed to run as administrators all the time without being asked for a password or permission. When they did try to implement it (albeit poorly) most users we're annoyed by it because it wasn't what they we're used to. 

If you choose to disable the root password that's your decision, but no one on this forum can tell you how to do it, it's is a breach of the Code of conduct, if we do tell you we risk our own accounts being banned.

bye the way did you read these [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) & [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) ?

---

### Post by sisco311 on 2009-12-02
> **Ms_Angel_D said:**
> Whether it is the last leg or not it is ultimately the most important, the reason windows is so prone to malware and virus infection is because users are allowed to run as administrators all the time without being asked for a password or permission. When they did try to implement it (albeit poorly) most users we're annoyed by it because it wasn't what they we're used to. 



I disagree, 

IMHO, the reason windows is so prone to malware is the negligence of the users:
[list]
[*] a password prompt annoys users and doesn't prevent one to run malicious binaries.

[*] most windows user don't know anything about security

[*] they don't practice safe browser habits

[*] the lack of safe and secure repositories 

[*] the false sense of security (anti-virus, anti-spyware, anti-whatever, firewall softwares)

...
[/list]

---

### Post by BkkBonanza on 2009-12-02
Expected - you know how they would execute an attack.
Unexpected - you don't have enough knowledge and understanding to see how an attack would come about.

In my opinion only an experienced "black hat" attacker has any real understanding of how they would go about gaining access to your system, and from what we hear they are aware of vulnerabilities that we may not know about.

One could think up creative ways one may gain control of a system but the unexpected is that someone else may find ways you never thought of.

I do know that if you make a mistake one day and run some program containing trojan code then that password for elevating the privelages on your machine is likely going to be what stops the trojan from gaining root access, installing a root kit, and maintaining control of your machine.

---

### Post by jessiebrownjr on 2009-12-02
> **Ms_Angel_D said:**
> Whether it is the last leg or not it is ultimately the most important, the reason windows is so prone to malware and virus infection is because users are allowed to run as administrators all the time without being asked for a password or permission. When they did try to implement it (albeit poorly) most users we're annoyed by it because it wasn't what they we're used to. 

If you choose to disable the root password that's your decision, but no one on this forum can tell you how to do it, it's is a breach of the Code of conduct, if we do tell you we risk our own accounts being banned.

bye the way did you read these [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) & [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) ?


I'm sure you are trying to be helpful but you have made a few mistakes in your reading I guess.. my root password is disabled, as so is my root account. I am talking about me typing "sudo" and getting a password prompt or not after. These are not the same things. And yes if those are the warnings about root, I read them along time ago. Not what im asking for here. 

If what im doing is the very "inner peel of the onion", then yes, that is what I'm asking.. if this is like leaving the front door open to a house, that isn't what I want. If I left VNC up would be a big security risk to the outside world, but what nobody has shown me yet, is that this is a risk to the outside world...

---

### Post by sisco311 on 2009-12-02
> **BkkBonaza said:**
> Expected - you know how they would execute an attack.
Unexpected - you don't have enough knowledge and understanding to see how an attack would come about.

In my opinion only an experienced "black hat" attacker has any real understanding of how they would go about gaining access to your system, and from what we hear they are aware of vulnerabilities that we may not know about.

One could think up creative ways one may gain control of a system but the unexpected is that someone else may find ways you never thought of.

I do know that if you make a mistake one day and run some program containing trojan code then that password for elevating the privelages on your machine is likely going to be what stops the trojan from gaining root access, installing a root kit, and maintaining control of your machine.

Once you run a trojan your user account is compromised. If your account is admin account, then sooner or later you will run a command as root, then guess what, the whole system is compromised.

---

### Post by rookcifer on 2009-12-02
> **jessiebrownjr said:**
> I'm sure you are trying to be helpful but you have made a few mistakes in your reading I guess.. my root password is disabled, as so is my root account. I am talking about me typing "sudo" and getting a password prompt or not after. These are not the same things. And yes if those are the warnings about root, I read them along time ago. Not what im asking for here. 

They *are* the same thing.  What do you think the purpose of sudo is?  It's to give a user temporary **root** access.  Without requiring a sudo password for root stuff, you are essentially running your machine as root all the time.  This is the #1 no-no when it comes to Linux security.

The root account is disabled, yes, but that is to keep people from simply logging in as root all the time.  Sudo still gives you root access.

---

### Post by cdenley on 2009-12-02
Obviously, if your admin user is tricked into running malware, and sudo doesn't require a password, it would be possible for the attacker to use sudo to escalate privileges. However, malware is not the only way to attack a system. There is occasionally a way for attackers to trick legitimate software (such as a web browser) into doing something it shouldn't by executing arbitrary code. Creating AppArmor profiles minimizes this risk, but users rarely have an AppArmor profile for every application which processes some sort of data from untrusted sources. Then the other risk I can think of is that you install some server without configuring it properly.

User privilege separation is just one layer of security. When you sacrifice this layer of security, you make your system less secure. I can't give specific examples of how your system's root account will get compromised from simply removing this layer because the other layers are still in place.

---

### Post by jessiebrownjr on 2009-12-02
> **BkkBonaza said:**
> Expected - you know how they would execute an attack.
Unexpected - you don't have enough knowledge and understanding to see how an attack would come about.

In my opinion only an experienced "black hat" attacker has any real understanding of how they would go about gaining access to your system, and from what we hear they are aware of vulnerabilities that we may not know about.

One could think up creative ways one may gain control of a system but the unexpected is that someone else may find ways you never thought of.

I do know that if you make a mistake one day and run some program containing trojan code then that password for elevating the privelages on your machine is likely going to be what stops the trojan from gaining root access, installing a root kit, and maintaining control of your machine.

You are indeed right on that last part, that is why i'm going to check into AppArmor profiles regardless if I keep my sudoers the way it is :-)

---

### Post by jessiebrownjr on 2009-12-02
> **rookcifer said:**
> They *are* the same thing.  What do you think the purpose of sudo is?  It's to give a user temporary **root** access.  Without requiring a sudo password for root stuff, you are essentially running your machine as root all the time.  This is the #1 no-no when it comes to Linux security.

The root account is disabled, yes, but that is to keep people from simply logging in as root all the time.  Sudo still gives you root access.

If I infer correctly, its mainly to thwart brute force attacks on the root account... Not just to keep people like myself from logging in as root.

> **cdenley said:**
> Obviously, if your admin user is tricked into running malware, and sudo doesn't require a password, it would be possible for the attacker to use sudo to escalate privileges. However, malware is not the only way to attack a system. There is occasionally a way for attackers to trick legitimate software (such as a web browser) into doing something it shouldn't by executing arbitrary code. Creating AppArmor profiles minimizes this risk, but users rarely have an AppArmor profile for every application which processes some sort of data from untrusted sources. Then the other risk I can think of is that you install some server without configuring it properly.

User privilege separation is just one layer of security. When you sacrifice this layer of security, you make your system less secure. I can't give specific examples of how your system's root account will get compromised from simply removing this layer because the other layers are still in place.

This is a good answer. I am aware of these risks and will more then likely just fix certain commands like mounting etc to not require passwords.. 

Somebody above posted a message about once you run something as root you are then compromised.. is that true as well..?

If I run a game for instance... its bugged... will it wait in the shadows for me to run something as root, and do its dirty work then..?  if thats just as likely, then it almost doesn't matter about my sudo timer/password..

---

### Post by puzzler995 on 2009-12-02
> **jessiebrownjr said:**
> If I infer correctly, its mainly to thwart brute force attacks on the root account... Not just to keep people like myself from logging in as root.

Having a Sudo password is a good thing, its original purpose (before hackers) was to keep accidents from happening, eg. deleting your whole root folder. 

> If I run a game for instance... its bugged... will it wait in the shadows for me to run something as root, and do its dirty work then..? if thats just as likely, then it almost doesn't matter about my sudo timer/password..

Yes you are compromised for that run time. If the Trojan adds itself to the start-up, then you are compromised forever. If its just a program without that code, once you shut down that computer, the Trojan will turn off (until you start the game up again)
:popcorn:

---

### Post by cdenley on 2009-12-02
AppArmor will not protect you from arbitrary software you download until you create a profile for it. It is more for protecting you from unknown vulnerabilities which may exist in your legitimate applications.

With sudo timestamps, it is possible for malware which is already running as an admin user to wait for you to run sudo, then use your timestamp. I have posted about this before, and even written a proof-of-concept script. This is why I recommend disabling sudo timestamps. Still, this possibility wouldn't concern me as much as passwordless sudo. It is much easier to simply try using sudo than it is to wait for and use a timestamp for a specific tty.

---

### Post by jessiebrownjr on 2009-12-02
Interesting stuff... so my safest option would be to make sudo have a password and... time out immedietly :-)

---

### Post by BkkBonanza on 2009-12-02
> **cdenley said:**
> It is much easier to simply try using sudo than it is to wait for and use a timestamp for a specific tty.

And also less visible probably. I can imagine that a script that repeatedly attempted root but was denied would leave a trail in the logs until the point of gaining access. At that point the logs could be fixed.

One thing I do is use conky to put a bunch of system info on my desktop. Part of that is a brief tail of the messages log. This gives me some comfort in seeing events on my system from time to time. I do see pam messages when sudo is used, and hopefully would notice if unexpected attempts to gain access were logged.

---

### Post by jessiebrownjr on 2009-12-02
Lol, now i'm freaking out.. I just installed fresh on this guy, updated to newest updates, and fired up gufw. I have nothing else done to speak of... but MTA started to load out of nowhere for god knows what reason..Put like 2 minutes on my boot process..
 I killed a sendmail option I had for startup processes or something, but I dont know how or why it was enabled. Now what do I do.. you guys got me all scared :-)

I found a previous post that was a guy with my situation minus the sudoers deal, and there was a fix posted.. fix didn't apply to me because I didnt have the symlink they were speaking of.

Sighhhh

---

### Post by cdenley on 2009-12-03
> **BkkBonaza said:**
> And also less visible probably. I can imagine that a script that repeatedly attempted root but was denied would leave a trail in the logs until the point of gaining access. At that point the logs could be fixed.

Actually, the script I created constantly checks for a running instance of sudo, kills it, then steals that tty (killing shells if necessary), then runs sudo with a pre-scripted command. No need to try running sudo over and over, and you must run it with the tty matching the timestamp, anyway. If your shells are suddenly killed, though, it might be a little obvious something is wrong, but it would be too late at that point.

---

### Post by cdenley on 2009-12-03
> **jessiebrownjr said:**
> Lol, now i'm freaking out.. I just installed fresh on this guy, updated to newest updates, and fired up gufw. I have nothing else done to speak of... but MTA started to load out of nowhere for god knows what reason..Put like 2 minutes on my boot process..
 I killed a sendmail option I had for startup processes or something, but I dont know how or why it was enabled. Now what do I do.. you guys got me all scared :-)

I found a previous post that was a guy with my situation minus the sudoers deal, and there was a fix posted.. fix didn't apply to me because I didnt have the symlink they were speaking of.

Sighhhh

Every MTA that I know of provides the sendmail command. What are you using? Postfix, courier, sendmail, nullmailer? If you are having trouble with an MTA, perhaps you should start a new thread in the "servers" section.

---

### Post by jessiebrownjr on 2009-12-03
> **cdenley said:**
> Every MTA that I know of provides the sendmail command. What are you using? Postfix, courier, sendmail, nullmailer? If you are having trouble with an MTA, perhaps you should start a new thread in the "servers" section.

The problem is that I'm not intentionally using any of them, and yeah, I hijacked my own thread.. :-)

its okay, im going to install off an alternate CD shortly with some disk encryption maybe.. not sure..

---

### Post by cdenley on 2009-12-03
If you don't need it, just remove it! This should tell you which package you installed has the sendmail command.
```

dpkg-query -S sendmail

```
It may have been installed as a dependency, though.

---

### Post by jessiebrownjr on 2009-12-03
Typed that, got this
```

sendmail-cf: /usr/share/sendmail/cf/ostype/solaris2.m4
sendmail-cf: /usr/share/sendmail/cf/domain/Berkeley.EDU.m4
sendmail-cf: /usr/share/sendmail/cf/cf
sendmail-base: /usr/share/sendmail/examples/network/if-post-down.d
sendmail-cf: /usr/share/sendmail/cf/ostype/solaris2.ml.m4
sendmail: /usr/share/doc/sendmail/NEWS.Debian.gz
sendmail-cf: /usr/share/sendmail/cf/cf/generic-sunos4.1.mc
sendmail-cf: /usr/share/sendmail/cf/ostype/openbsd.m4
sendmail-cf: /usr/share/sendmail/cf/cf/cs-hpux10.mc
sendmail-base: /usr/share/sendmail/examples/resolvconf
sendmail-base: /usr/share/sendmail/examples/db/sendmail.cM
sendmail-cf: /usr/share/sendmail/cf/cf/generic-hpux9.mc
sendmail-base: /usr/share/doc/sendmail-base/changelog.Debian.gz
sendmail-cf: /usr/share/sendmail/cf/feature/virtuser_entire_domain.m4
sendmail-cf: /usr/share/sendmail/cf/feature/msp.m4
sendmail-base: /usr/share/sendmail/examples/network/if-up.d/sendmail
sendmail-base: /usr/share/sendmail/update_conf
sendmail-cf: /usr/share/sendmail/cf/feature
sendmail-cf: /usr/share/sendmail/cf/ostype/aix3.m4
sendmail-base: /etc/resolvconf/update-libc.d/sendmail
sendmail-bin: /etc/init.d/sendmail
libmailtools-perl: /usr/share/perl5/Mail/Mailer/sendmail.pm
sendmail-cf: /usr/share/sendmail/cf/ostype/nextstep.m4
sendmail-cf: /usr/share/sendmail/cf/cf/cs-solaris2.mc
sendmail-base: /usr/share/doc/sendmail-base/copyright
sendmail-base: /usr/share/doc/sendmail-base/site.config.m4.gz
sendmail-cf: /usr/share/sendmail/cf/feature/no_default_msa.m4
sendmail-base: /usr/share/sendmail/parse_mc
sendmail-cf: /usr/share/sendmail/cf/mailer/cyrus.m4
sendmail-cf: /usr/share/sendmail/cf/feature/loose_relay_check.m4
sendmail-bin: /usr/share/man/man8/sendmail.8.gz
sendmail-cf: /usr/share/sendmail/cf/ostype/qnx.m4
sendmail-base: /usr/sbin/sendmailconfig
sendmail-base: /etc/ppp/ip-up.d/sendmail
sendmail-base: /usr/share/sendmail/examples/amavis/amavis-doc-7.html
sendmail-base: /usr/share/sendmail/examples/logcheck/ignore.d.paranoid
sendmail-cf: /usr/share/sendmail/cf/cf/generic-nextstep3.3.mc
sendmail-cf: /usr/share/sendmail/cf/m4/version.m4
sendmail-cf: /usr/share/sendmail/cf/cf/mailspool.cs.mc
sendmail-cf: /usr/share/sendmail/cf/ostype/aix5.m4
sendmail-cf: /usr/share/sendmail/cf/cf/generic-solaris.mc
sendmail-cf: /usr/share/sendmail/cf/cf/cs-hpux9.mc
sendmail-cf: /usr/share/sendmail/cf/feature/stickyhost.m4
sendmail-base: /usr/share/man/man8/checksendmail.8.gz
sendmail-base: /usr/share/sendmail/examples/db/aliases
sendmail-base: /usr/share/sendmail/examples/amavis/amavis-doc.html
sendmail-cf: /usr/share/sendmail/cf/feature/use_client_ptr.m4
sendmail-cf: /usr/share/doc/sendmail-cf
sendmail-cf: /usr/share/sendmail/cf/feature/ratecontrol.m4
sendmail-bin: /usr/share/doc/sendmail-bin/TODO.Debian
sendmail-cf: /usr/share/sendmail/cf/feature/domaintable.m4
sendmail-cf: /usr/share/sendmail/cf/m4/cf.m4
sendmail-cf: /usr/share/sendmail/cf/feature/genericstable.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/freebsd4.m4
sendmail-cf: /usr/share/sendmail/cf/hack/dnsblaccess.m4
sendmail-base: /usr/share/sendmail/examples/ppp/ip-down.d/sendmail.md5sum
sendmail-base: /usr/share/sendmail/examples/pam.d/smtp
sendmail-cf: /usr/share/sendmail/cf/siteconfig/uucp.ucbvax.m4
sendmail-base: /etc/dhcp3/dhclient-exit-hooks.d/sendmail
sendmail-cf: /usr/share/sendmail/cf/ostype/dgux.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/ultrix4.m4
sendmail-base: /usr/share/sendmail/examples/ldap/sendmail.schema.v1
sendmail-base: /usr/share/sendmail/examples/ldap/sendmail.schema.v2
sendmail-cf: /usr/share/sendmail/cf/m4
sendmail-cf: /usr/share/sendmail/cf/ostype/amdahl-uts.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/solaris8.m4
sendmail-base: /usr/share/doc/sendmail-base/README.gz
sendmail-base: /etc/logcheck/ignore.d.paranoid/sendmail
sendmail-cf: /usr/share/sendmail/cf/ostype/unicosmp.m4
sendmail-base: /usr/share/sendmail/examples/network/if-down.d
sendmail-cf: /usr/share/sendmail/cf/feature/preserve_local_plus_detail.m4
sendmail-cf: /usr/share/sendmail/cf/feature/use_ct_file.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/unixware7.m4
sendmail-base: /etc/network/if-up.d/sendmail
sendmail-cf: /usr/share/sendmail/cf/ostype/freebsd6.m4
sendmail-base: /usr/share/sendmail/examples/logcheck/ignore.d.server/sendmail
sendmail-base: /usr/share/sendmail/update_tls
sendmail-base: /usr/share/bug/sendmail
sendmail-cf: /usr/share/sendmail/cf/mailer/cyrusv2.m4
sendmail-cf: /usr/share/sendmail/cf/mailer/local.m4
sendmail-bin: /usr/share/doc/sendmail-bin/changelog.gz
sendmail-base: /usr/share/sendmail/examples/db/domaintable
sendmail-cf: /usr/share/sendmail/cf/m4/cfhead.m4
sendmail-cf: /usr/share/sendmail/cf
sendmail-cf: /usr/share/sendmail/cf/cf/clientproto.mc
sendmail-base: /usr/share/sendmail/examples/dhcp3
sendmail-cf: /usr/share/sendmail/cf/mailer/smtp.m4
sendmail-bin: /usr/share/man/man8/newaliases.sendmail.8.gz
sendmail-base: /usr/share/sendmail/examples/milter/Makefile
sendmail-cf: /usr/share/sendmail/cf/feature/accept_unqualified_senders.m4
sendmail-cf: /usr/share/sendmail/cf/sh
gnome-pilot-conduits: /usr/share/gnome-pilot/conduits/sendmail.conduit
sendmail-cf: /usr/share/sendmail/cf/domain/debian-mta.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/sinix.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/unknown.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/mpeix.m4
sendmail-cf: /usr/share/sendmail/cf/feature/nullclient.m4
sendmail-base: /etc/network/if-down.d/sendmail
sendmail-cf: /usr/share/sendmail/cf/ostype/darwin.m4
sendmail-base: /usr/share/sendmail/newaliases
sendmail-base: /usr/share/sendmail/examples/ppp/ip-down.d
sendmail-cf: /usr/share/sendmail/cf/ostype/bsd4.3.m4
sendmail-bin: /usr/share/doc/sendmail-bin/changelog.Debian.gz
sendmail-cf: /usr/share/sendmail/cf/feature/conncontrol.m4
sendmail-base: /usr/share/sendmail/examples/pam.d/smtp.md5sum
sendmail-base: /usr/sbin/checksendmail
sendmail-base: /usr/share/sendmail/update_auth
sendmail-cf: /usr/share/sendmail/cf/cf/ucbarpa.mc
sendmail-cf: /usr/share/doc/sendmail-cf/changelog.Debian.gz
sendmail-bin: /usr/share/man/man5/aliases.sendmail.5.gz
sendmail-bin: /var/run/sendmail
sendmail-cf: /usr/share/sendmail/cf/ostype/bsdi.m4
sendmail-cf: /usr/share/sendmail/cf/siteconfig
sendmail-cf: /usr/share/sendmail/cf/ostype/dynix3.2.m4
sendmail-cf: /usr/share/sendmail/cf/feature/local_procmail.m4
sendmail-base: /usr/share/sendmail/mailq
sendmail-cf: /usr/share/sendmail/cf/ostype/solaris2.pre5.m4
sendmail-base: /usr/share/sendmail/examples/amavis/amavis-doc-3.html
sendmail-cf: /usr/share/sendmail/cf/feature/drac.m4
sendmail-cf: /usr/share/doc/sendmail-cf/copyright
sendmail-base: /usr/share/sendmail/examples/network/if-up.d
sendmail-base: /usr/share/sendmail/examples/pam.d
sendmail-base: /usr/share/sendmail/examples/db/access
sendmail-cf: /usr/share/sendmail/cf/feature/authinfo.m4
sendmail-cf: /usr/share/sendmail/cf/cf/mail.cs.mc
sendmail-cf: /usr/share/sendmail/cf/ostype/ptx2.m4
sendmail-base: /usr/share/sendmail/examples/network
sendmail-base: /usr/share/lintian/overrides/sendmail-base
sendmail-base: /usr/share/sendmail/examples/logcheck/ignore.d.paranoid/sendmail
sendmail-cf: /usr/share/sendmail/cf/feature/preserve_luser_host.m4
sendmail-cf: /usr/share/sendmail/cf/hack/virthost_by_ip.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/bsdi2.0.m4
sendmail-base: /usr/share/sendmail/examples/sasl/sasl.m4
sendmail-base: /etc/logcheck/ignore.d.server/sendmail
sendmail-base: /usr/share/sendmail/update_authm4
sendmail-base: /usr/share/doc/sendmail-base
sendmail-cf: /usr/share/sendmail/cf/ostype/isc4.1.m4
sendmail-base: /usr/share/man/man8/runq.sendmail.8.gz
sendmail-cf: /usr/share/sendmail/cf/debian/sendmail.mc
sendmail-base: /etc/network/if-post-down.d/sendmail
sendmail-cf: /usr/share/sendmail/cf/feature/use_cw_file.m4
sendmail-cf: /usr/share/sendmail/cf/feature/relay_entire_domain.m4
sendmail-cf: /usr/share/sendmail/cf/cf/huginn.cs.mc
sendmail-cf: /usr/share/sendmail/cf/feature/require_rdns.m4
sendmail-cf: /usr/share/sendmail/cf/feature/allmasquerade.m4
sendmail-base: /usr/share/sendmail/examples/sasl
sendmail-base: /usr/share/sendmail/examples/logcheck
sendmail-cf: /usr/share/sendmail/cf/cf/mail.eecs.mc
sendmail-cf: /usr/share/sendmail/cf/mailer/phquery.m4
sendmail-base: /usr/share/sendmail/examples/logcheck/violations.ignore.d/logcheck-sendmail
sendmail-cf: /usr/share/sendmail/cf/cf/s2k-ultrix4.mc
sendmail-cf: /usr/share/sendmail/cf/domain/CS.Berkeley.EDU.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/dragonfly.m4
sendmail-cf: /usr/share/sendmail/cf/debian/submit.mc
sendmail-base: /usr/share/sendmail/examples/amavis/amavis-doc-6.html
sendmail-base: /usr/share/sendmail/examples/db/mailertable
sendmail-cf: /usr/share/sendmail/cf/ostype/irix4.m4
sendmail-cf: /usr/share/sendmail/cf/cf/python.cs.mc
sendmail-cf: /usr/share/doc/sendmail-cf/README.gz
sendmail-cf: /usr/share/sendmail/cf/debian/autoconf.m4
sendmail-base: /usr/share/sendmail/examples/ppp
sendmail-cf: /usr/share/sendmail/cf/ostype/linux.m4
sendmail-base: /usr/share/sendmail/examples/milter/sample.c
sendmail-cf: /usr/share/sendmail/cf/hack/msp_nullclient.m4
sendmail-cf: /usr/share/sendmail/cf/cf/generic-ultrix4.mc
sendmail-cf: /usr/share/sendmail/cf/feature/compat_check.m4
sendmail-cf: /usr/share/sendmail/cf/mailer
sendmail-cf: /usr/share/sendmail/cf/feature/generics_entire_domain.m4
sendmail-base: /usr/share/sendmail/update_notices
sendmail-base: /usr/share/sendmail/hoststat
sendmail-base, sendmail-cf: /usr/share/sendmail
sendmail-cf: /usr/share/sendmail/cf/ostype/irix6.m4
sendmail-cf: /usr/share/sendmail/cf/feature/ldap_routing.m4
sendmail-base: /usr/share/sendmail/examples/tls/starttls.m4
sendmail-base: /usr/share/sendmail/examples/logcheck/violations.ignore.d
sendmail-cf: /usr/share/sendmail/cf/mailer/usenet.m4
sendmail-base: /usr/share/doc/sendmail-base/NEWS.Debian.gz
sendmail-cf: /usr/share/sendmail/cf/feature/badmx.m4
sendmail-cf: /usr/share/sendmail/cf/cf/generic-bsd4.4.mc
sendmail-cf: /usr/share/sendmail/cf/feature/uucpdomain.m4
sendmail-bin: /usr/share/doc/sendmail-bin/copyright
sendmail-base: /usr/share/sendmail/examples/ppp/ip-up.d/sendmail
sendmail: /usr/share/doc/sendmail/copyright
sendmail-cf: /usr/share/sendmail/cf/feature/local_lmtp.m4
sendmail-cf: /usr/share/sendmail/cf/domain/EECS.Berkeley.EDU.m4
sendmail-base: /usr/share/sendmail/Parse_conf.pm
sendmail-cf: /usr/share/bug/sendmail-cf
sendmail-cf: /usr/share/sendmail/cf/feature/relay_based_on_MX.m4
sendmail-base: /usr/share/sendmail/update_db
sendmail-cf: /usr/share/sendmail/cf/mailer/uucp.m4
sendmail-cf: /usr/share/sendmail/cf/feature/accept_unresolvable_domains.m4
sendmail-base: /usr/share/sendmail/sendmail
sendmail-base: /usr/share/sendmail/runq
evolution-data-server: /usr/lib/evolution-data-server-1.2/camel-providers/libcamelsendmail.so
sendmail-cf: /usr/share/sendmail/cf/ostype/sunos4.1.m4
sendmail-cf: /usr/share/sendmail/cf/cf/submit.mc
sendmail-cf: /usr/share/sendmail/cf/ostype/gnu.m4
sendmail-cf: /usr/share/sendmail/cf/ostype
sendmail-cf: /usr/share/doc/sendmail-cf/NEWS.Debian.gz
sendmail-cf: /usr/share/sendmail/cf/domain/berkeley-only.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/hpux11.m4
sendmail-base: /usr/share/doc/sendmail-base/changelog.gz
sendmail-cf: /usr/share/sendmail/cf/feature/blacklist_recipients.m4
sendmail-base: /usr/share/sendmail/examples/ldap
sendmail-cf: /usr/share/sendmail/cf/ostype/riscos4.5.m4
sendmail-cf: /usr/share/sendmail/cf/feature/bestmx_is_local.m4
sendmail-bin: /usr/share/doc/sendmail-bin
sendmail-base: /etc/logcheck/violations.ignore.d/logcheck-sendmail
sendmail-cf: /usr/share/sendmail/cf/cf/cs-sunos4.1.mc
sendmail-cf: /usr/share/sendmail/cf/ostype/unicosmk.m4
sendmail-cf: /usr/share/sendmail/cf/feature/promiscuous_relay.m4
sendmail-cf: /usr/share/sendmail/cf/hack/debian_auth.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/svr4.m4
sendmail-base: /usr/share/sendmail/Parse_mc.pm
sendmail-cf: /usr/share/sendmail/cf/feature/relay_hosts_only.m4
sendmail-cf: /usr/share/sendmail/cf/domain/generic.m4
sendmail-bin: /usr/share/doc/sendmail-bin/README.gz
sendmail-base: /usr/share/sendmail/examples/logcheck/ignore.d.server
sendmail: /usr/share/doc/sendmail/README.gz
sendmail-cf: /usr/share/sendmail/cf/ostype/aix4.m4
sendmail-base: /usr/share/sendmail/examples/network/if-up.d/sendmail.md5sum
sendmail-cf: /usr/share/sendmail/cf/mailer/ssh.m4
sendmail-base: /usr/share/man/man8/sendmailconfig.8.gz
sendmail-cf: /usr/share/sendmail/cf/ostype/domainos.m4
sendmail-base: /usr/share/sendmail/examples/db/userdb
sendmail-base: /usr/share/sendmail/examples/amavis/amavis-doc-2.html
sendmail-base: /usr/share/sendmail/update_ldap
sendmail-bin: /usr/share/lintian/overrides/sendmail-bin
sendmail-base: /usr/share/sendmail/examples/logcheck/ignore.d.workstation/sendmail
sendmail-bin: /usr/share/bug/sendmail-bin
sendmail-cf: /usr/share/sendmail/cf/siteconfig/uucp.ucbarpa.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/maxion.m4
sendmail-cf: /usr/share/sendmail/cf/feature/block_bad_helo.m4
sendmail-base: /usr/share/sendmail/update_mc
sendmail-base: /usr/share/sendmail/update_mk
sendmail-cf: /usr/share/sendmail/cf/cf/vangogh.cs.mc
sendmail: /usr/share/doc/sendmail/changelog.Debian.gz
sendmail-cf: /usr/share/sendmail/cf/mailer/xagent.m4
sendmail-cf: /usr/share/sendmail/cf/cf/chez.cs.mc
sendmail-base: /usr/share/sendmail/examples/milter
sendmail-cf: /usr/share/sendmail/cf/ostype/sco-uw-2.1.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/hpux9.m4
sendmail-bin: /etc/cron.daily/sendmail
sendmail-cf: /usr/share/sendmail/cf/ostype/powerux.m4
sendmail-base: /usr/share/sendmail/qtool.pl
sendmail-cf: /usr/share/sendmail/cf/ostype/bsdi1.0.m4
sendmail-base: /usr/share/sendmail/examples/network/if-post-down.d/sendmail.md5sum
sendmail-base: /usr/share/sendmail/update_tcpd
sendmail-base: /usr/share/sendmail/buildvirtuser
sendmail-base: /usr/share/sendmail/examples/network/if-down.d/sendmail
sendmail-base: /usr/share/sendmail/examples/dhcp3/dhclient-exit-hooks.d/sendmail.md5sum
sendmail-cf: /usr/share/sendmail/cf/feature/domainmap.m4
sendmail-cf: /usr/share/sendmail/cf/domain
sendmail-base: /usr/share/sendmail/examples/sasl/Sendmail.conf.1
sendmail-base: /usr/share/sendmail/examples/sasl/Sendmail.conf.2
sendmail-cf: /usr/share/sendmail/cf/cf/generic-mpeix.mc
sendmail-base: /usr/share/sendmail/examples/ppp/ip-up.d
sendmail-cf: /usr/share/sendmail/cf/feature/smrsh.m4
sendmail-cf: /usr/share/sendmail/cf/cf/cs-osf1.mc
sendmail-cf: /usr/share/sendmail/cf/ostype/freebsd5.m4
sendmail-base: /usr/share/bug/sendmail/control
sendmail-cf: /usr/share/sendmail/cf/mailer/procmail.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/a-ux.m4
sendmail-base: /usr/share/sendmail/examples/network/if-post-down.d/sendmail
sendmail-cf: /usr/share/sendmail/cf/feature/redirect.m4
sendmail-base: /usr/share/sendmail/examples/amavis/amavis-doc-5.html
sendmail-cf: /usr/share/sendmail/cf/cf/generic-hpux10.mc
sendmail-base: /etc/ppp/ip-down.d/sendmail
sendmail-bin, sendmail: /usr/share/doc/sendmail
sendmail-cf: /usr/share/sendmail/cf/feature/nocanonify.m4
sendmail-base: /usr/share/sendmail/examples/db/genericstable
sendmail-cf: /usr/share/sendmail/cf/cf/cyrusproto.mc
sendmail-cf: /usr/share/sendmail/cf/feature/relay_local_from.m4
sendmail-base: /usr/share/doc/sendmail-base/examples
sendmail-cf: /usr/share/sendmail/cf/mailer/qpage.m4
sendmail-base: /usr/share/sendmail/mailstats
sendmail-bin: /usr/share/man/man1/vacation.sendmail.1.gz
sendmail-cf: /usr/share/sendmail/cf/feature/masquerade_envelope.m4
sendmail-cf: /usr/share/sendmail/cf/feature/always_add_domain.m4
sendmail-cf: /usr/share/sendmail/cf/hack/nodns.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/sco3.2.m4
sendmail-cf: /usr/share/sendmail/cf/hack/cssubdomain.m4
sendmail-cf: /usr/share/sendmail/cf/feature/access_db.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/osf1.m4
sendmail-cf: /usr/share/sendmail/cf/feature/lookupdotdomain.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/bsd4.4.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/uxpds.m4
sendmail-base: /usr/share/sendmail/update_sendmail
tiger: /usr/lib/tiger/scripts/check_sendmail
sendmail-cf: /usr/share/sendmail/cf/cf/cs-ultrix4.mc
sendmail-bin: /usr/share/man/man8/sendmail.sendmail.8.gz
sendmail-base: /usr/share/sendmail/examples/logcheck/ignore.d.workstation
sendmail-cf: /usr/share/sendmail/cf/hack/spamtrap.m4
sendmail-cf: /usr/share/sendmail/cf/feature/masquerade_entire_domain.m4
sendmail-base: /usr/share/sendmail/examples/db/relay-domains
sendmail-base: /usr/share/sendmail/examples/sasl/saslpasswd.conf.1
sendmail-base: /usr/share/sendmail/examples/sasl/saslpasswd.conf.2
sendmail-base: /usr/share/sendmail/examples/amavis/amavis-doc-8.html
sendmail-cf: /usr/share/sendmail/cf/cf/generic-osf1.mc
sendmail-cf: /usr/share/sendmail/cf/ostype/debian.m4
sendmail-base: /usr/share/sendmail/examples/tls
sendmail-cf: /usr/share/sendmail/cf/feature/relay_mail_from.m4
sendmail-cf: /usr/share/sendmail/cf/feature/delay_checks.m4
sendmail: /usr/share/doc/sendmail/changelog.gz
sendmail-cf: /usr/share/sendmail/cf/feature/notsticky.m4
sendmail-cf: /usr/share/sendmail/cf/cf/generic-linux.mc
sendmail-cf: /usr/share/sendmail/cf/cf/knecht.mc
sendmail-cf: /usr/share/sendmail/cf/mailer/fax.m4
sendmail-base: /usr/share/sendmail/examples/resolvconf/update-libc.d
sendmail-base: /usr/share/sendmail/doublebounce.pl
sendmail-cf: /usr/share/sendmail/cf/cf/s2k-osf1.mc
sendmail-cf: /usr/share/sendmail/cf/feature/mailertable.m4
sendmail-base: /usr/share/sendmail/update_tlsm4
sendmail-base: /usr/share/sendmail/examples/milter/strl.h
sendmail-cf: /usr/share/sendmail/cf/sh/makeinfo.sh
sendmail-base: /usr/share/doc/sendmail-base/Debian-specific.gz
sendmail-bin: /usr/share/doc/sendmail-bin/NEWS.Debian.gz
sendmail-base: /usr/share/sendmail/smcontrol.pl
sendmail-base: /usr/share/bug/sendmail-base
sendmail-base: /usr/share/sendmail/examples
sendmail-base: /usr/share/sendmail/examples/ppp/ip-down.d/sendmail
sendmail-cf: /usr/share/doc/sendmail-cf/changelog.gz
sendmail-cf: /usr/share/sendmail/cf/ostype/unicos.m4
sendmail-bin: /usr/share/doc/sendmail-bin/buildinfo.gz
sendmail-base: /etc/logcheck/ignore.d.workstation/sendmail
sendmail-cf: /usr/share/sendmail/cf/ostype/altos.m4
sendmail-cf: /usr/share/sendmail/cf/feature/dnsbl.m4
sendmail-base: /usr/share/sendmail/dynamic
sendmail-cf: /usr/share/sendmail/cf/feature/local_no_masquerade.m4
sendmail-cf: /usr/share/sendmail/cf/cf/README
sendmail-base: /usr/share/sendmail/examples/amavis/amavis-doc-1.html
sendmail-cf: /usr/share/sendmail/cf/hack
sendmail-base: /usr/share/sendmail/examples/dhcp3/dhclient-exit-hooks.d
sendmail-base: /usr/share/sendmail/examples/amavis
sendmail-cf: /usr/share/sendmail/cf/feature/virtusertable.m4
sendmail-cf: /usr/share/sendmail/cf/feature/mtamark.m4
sendmail-bin: /usr/share/man/man1/mailq.sendmail.1.gz
sendmail-bin: /usr/lib/sm.bin/sendmail
sendmail-cf: /usr/share/sendmail/cf/ostype/mklinux.m4
sendmail-cf: /usr/share/sendmail/cf/ostype/sunos3.5.m4
sendmail-base: /usr/share/sendmail/examples/resolvconf/update-libc.d/sendmail
sendmail-cf: /usr/share/sendmail/cf/cf/ucbvax.mc
sendmail-base: /usr/share/sendmail/status
sendmail-cf: /usr/share/sendmail/cf/feature/queuegroup.m4
sendmail-base: /usr/share/sendmail/update_smrsh
sendmail-base: /usr/share/bug/sendmail/script
sendmail-bin: /usr/lib/sm.bin/vacation.sendmail
sendmail-cf: /usr/share/sendmail/cf/ostype/irix5.m4
sendmail-base: /usr/share/sendmail/examples/db/virtusertable
sendmail-cf: /usr/share/sendmail/cf/cf/tcpproto.mc
sendmail-cf: /usr/share/sendmail/cf/m4/proto.m4
sendmail-base: /usr/share/sendmail/purgestat
sendmail-cf: /usr/share/sendmail/cf/domain/debian-msp.m4
sendmail-cf: /usr/share/sendmail/cf/feature/greet_pause.m4
sendmail-base: /usr/share/sendmail/examples/logcheck/violations.ignore.d/local.sendmail
sendmail-bin: /var/run/sendmail/msp
sendmail-cf: /usr/share/sendmail/cf/feature/nouucp.m4
sendmail-base: /usr/share/sendmail/examples/ppp/ip-up.d/sendmail.md5sum
sendmail-base: /usr/share/sendmail/examples/passwd-to-alias
sendmail-bin: /var/run/sendmail/mta
sendmail-cf: /usr/share/sendmail/cf/feature/enhdnsbl.m4
sendmail-cf: /usr/share/sendmail/cf/domain/S2K.Berkeley.EDU.m4
sendmail-base: /usr/share/sendmail/examples/dhcp3/dhclient-exit-hooks.d/sendmail
sendmail-cf: /usr/share/sendmail/cf/siteconfig/uucp.old.arpa.m4
sendmail-cf: /usr/share/sendmail/cf/feature/rhsbl.m4
sendmail-base: /usr/share/sendmail/examples/network/if-down.d/sendmail.md5sum
sendmail-cf: /usr/share/sendmail/cf/feature/vnet.m4
sendmail-cf: /usr/share/sendmail/cf/feature/limited_masquerade.m4
evolution-data-server: /usr/lib/evolution-data-server-1.2/camel-providers/libcamelsendmail.urls
sendmail-cf: /usr/share/sendmail/cf/mailer/mail11.m4
sendmail-bin: /var/lib/sendmail
sendmail-cf: /usr/share/sendmail/cf/debian
sendmail-bin: /var/run/sendmail/stampdir
sendmail-base: /usr/share/sendmail/examples/amavis/amavis-doc-4.html
sendmail-cf: /usr/share/sendmail/cf/feature/bitdomain.m4
sendmail-base: /usr/share/sendmail/update_sys
sendmail-base: /usr/share/sendmail/examples/db
sendmail-cf: /usr/share/sendmail/cf/siteconfig/uucp.cogsci.m4
sendmail-cf: /usr/share/sendmail/cf/mailer/pop.m4
sendmail-cf: /usr/share/sendmail/cf/cf/uucpproto.mc
sendmail-cf: /usr/share/sendmail/cf/ostype/hpux10.m4

```

wth?

---

### Post by jessiebrownjr on 2009-12-03
I did a purge of sendmail and tiger, then it told me I could use autoremove to remove some stuff too...
nonz@desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sendmail-bin linux-headers-2.6.28-11 sendmail-base m4 john-data procmail
  sensible-mda linux-headers-2.6.28-11-generic sendmail-cf chkrootkit john
The following packages will be REMOVED:
  chkrootkit john john-data linux-headers-2.6.28-11
  linux-headers-2.6.28-11-generic m4 procmail sendmail-base sendmail-bin
  sendmail-cf sensible-mda
0 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
After this operation, 83.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 126090 files and directories currently installed.)
Removing chkrootkit ...
Removing john ...
Removing john-data ...
Removing linux-headers-2.6.28-11-generic ...
Removing linux-headers-2.6.28-11 ...
Removing sensible-mda ...
Removing sendmail-bin ...
Removing sendmail-cf ...
Removing sendmail-base ...
Removing m4 ...
Removing procmail ...
Processing triggers for man-db ...
anonz@desktop:~$ 

Did this john tiger rootkit checker I got from the forums activate this mail stuff?

---

### Post by BkkBonanza on 2009-12-03
That sounds plausible.
I know on my system sendmail was not installed but exim was, and mapped to sendmail using links. I'm not sure if exim is the default, or if I chose it during install, but it is normal for another MTA to be linked in as sendmail since so many older scripts refer to sendmail as standard.

I'm not familiar with that rootkit checker you say you got from the forums. Probably it's fine or maybe not. One thing to consider though is that there is already two rootkit checkers in the repos (chkrootkit and rkhunter). It is a good idea to use the repo version as they have been checked, built and signed by a reliable source. Unless you intend to verify code from a forum or have a high level of trust in it's origin it's exactly the type of code you wouldn't want to install. It's fairly common on the web for people to promote security checking software which is trojan'd.

I don't think this is necessarily what you have here, just something to consider. It's not so nice that it would install sendmail when a sendmail alternate was likely already present. Usually there is a sendmail equivalent present since some system utils need to send mail under some conditions. Notably cron sends emails to the user running a cronjob.

(edit: I see that tiger and john are both repos software, so discount my comment about that. Just not software I've used in the past.)

---

### Post by doas777 on 2009-12-03
tiger is a little more than just a rootkit checker. think of it more as a general security scanner.

---

### Post by jessiebrownjr on 2009-12-03
What would be considered safe things to make me not have to type passwords to, vs the entire system? What about my NFS system? I assume installing things (if you can even bypass just that) would be a terrible idea.

---

### Post by cdenley on 2009-12-03
> **jessiebrownjr said:**
> What would be considered safe things to make me not have to type passwords to, vs the entire system? What about my NFS system? I assume installing things (if you can even bypass just that) would be a terrible idea.

Generally, anything which is considered safe to allow without requiring a password doesn't require a password. Things which require root privileges but aren't really considered dangerous are already handled in a way which doesn't require sudo. For example, shutting down your system or mounting a USB drive.

---

### Post by TenPlus1 on 2009-12-03
Hi, go here and follow the instructions to install the medibunto repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then search for Skype in your Synaptic Package Manager and do a re-install to the Karmic edition...  This hopefully should fix your problem, if not then you could disable/remove Pulseaudio to make things work properly...

---

### Post by jessiebrownjr on 2009-12-03
> **TenPlus1 said:**
> Hi, go here and follow the instructions to install the medibunto repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then search for Skype in your Synaptic Package Manager and do a re-install to the Karmic edition...  This hopefully should fix your problem, if not then you could disable/remove Pulseaudio to make things work properly...


lol 1) I have no idea what this post is in reference to, 2) isn't Skype voice chat? 3) Are you spying on me? If you were, you would know both my computers are in fact allergic to Karmic and I'm stuck with jaunty..4) I have medibuntu though, i loves it.

---

### Post by sisco311 on 2009-12-03
> **cdenley said:**
> For example, shutting down your system or mounting a USB drive.

and [ping]("http://en.wikipedia.org/wiki/Ping"), newgrp, mtr, polkit-agent-helper-1... ;)


@OP
at the end of the day, this is a security v.s. usability question.

You have to ask yourself:

Do I understand from what can the authentication password protect my system?

Disabling it will decrease my security, but will it increase my productivity as well?

Why the hell I have to type my password so often? :)

---

### Post by jessiebrownjr on 2009-12-03
> **sisco311 said:**
> and [ping]("http://en.wikipedia.org/wiki/Ping"), newgrp, mtr, polkit-agent-helper-1... ;)


@OP
at the end of the day, this is a security v.s. usability question.

You have to ask yourself:

Do I understand from what can the authentication password protect my system?

Disabling it will decrease my security, but will it increase my productivity as well?

Why the hell I have to type my password so often? :)

hehe, to point 3 about why I type my password often.. I'm usually changing and updating 2 computers.. one of them is a laptop that I have to power on like 5-10 times a day for school/fun work and network manager wants a password.

---

### Post by doas777 on 2009-12-04
> **jessiebrownjr said:**
> lol 1) I have no idea what this post is in reference to, 2) isn't Skype voice chat? 3) Are you spying on me? If you were, you would know both my computers are in fact allergic to Karmic and I'm stuck with jaunty..4) I have medibuntu though, i loves it.

I think someone was using more than one tab, and accidentally got them mixed up. no medibuntu has little to do with your current conundrum. good codecs though

---

### Post by cariboo on 2009-12-04
If network-manager asking for a password every time you start up is the biggest problem, why not fix that problem instead of trying to work around it?

Make sure **Available to all users** is ticked, it should ask you for a password one more time, and you should never see it again.

See screenshot.

---

### Post by doas777 on 2009-12-04
> **cariboo907 said:**
> If network-manager asking for a password every time you start up is the biggest problem, why not fix that problem instead of trying to work around it?

Make sure **Available to all users** is ticked, it should ask you for a password one more time, and you should never see it again.

See screenshot.

ahh, is that what that does.  I never would have guessed. I had always assumed that entries that applied to all users, would appear in network-manager, on every users desktop.

---

### Post by bodhi.zazen on 2009-12-04
> **jessiebrownjr said:**
> Humor me here. I have VNC disabled and I think ssh too(i haven't enabled it )..
How can I check SSH? 

Basically the attacker needs a shell to do stuff to make use of me not having a sudo password, right?

I'm thinking I can use AppArmor profiles to keep bad code stuff from doing naughty things, but I'm looking into that too..

if I lengthen the timeout period on my sudoers... Does that matter to any attacker? If im logged in, and he shells in, does he need to enter it atleast once ?

I have been holding off chastising you for far too long as I have watched this thread for the last 2 days.

It is amazing how people stubbornly hold onto the idea that they are somehow the only one with access to their system or that they have to install a server (such as VNC, ssh, or other) to be vulnerable.

There are alarmingly frequent security advisories for Firefox , see ;

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

And on the front page, at the time of this post, look, [s]2[/s] **56** vulnerabilities for Firefox , here is one :

[http://www.ubuntu.com/usn/USN-853-1](http://www.ubuntu.com/usn/USN-853-1)

Note : > If a user were tricked into viewing a malicious website, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program.Now, in your delusion that you are the only person with access to your computer, you have gone and disabled the password requirement for sudo, this means root access via Firefox.

[B][SIZE=4][COLOR=darkred]Please do not disable security features without understanding the implications of what you are doing.

Please do not encourage others to disable security features without understanding the implications of what you are advising.[/COLOR][/SIZE][/B]

Sudo and the requirement for a password are there for your protection. Now it is true that with shell access root access is not far behind, at least a password on sudo will slow them down.

Personally I advise you confine all network aware applications with Apparmor. Starting with Ubuntu 9.10 there is *finally* a profile for Firefox in the Ubuntu repos. Apparmor is not fool proof, but it goes a long ways =)

EDIT: Along those lines I am guessing you did not feel the need to read the stickies at the top of these forum either. If this assumption is true, please read them when you have time and before you go making additional changes in your security settings.

---

### Post by jessiebrownjr on 2009-12-04
Bodhii! I was waiting for you to jump in, I turned my sudoers back on. I did read the stickies, but I guess I misunderstood about firefox being that insecure. I'll keep reading into it, regardless of the sudoers file.  Believe it or not i want to learn about all of this stuff in depth and incorporate it into a profession :-) I've been busy with school work the past two days..  I guess what I have been asking for for DAYS now is a reason why it was so insecure and the firefox vulnerabilities would have stopped this thread days ago for me. I also have found out since I started this post about wine running code--which I thought was confined virtually, but was mistaken. Im learning as I go!

---

### Post by bodhi.zazen on 2009-12-04
Yes, I know you are learning, and that is part of why I waited, I did not want my post to detract from your learning and I wanted to wait until I felt you would appreciate the message.

It is not as if Firefox is cracked left and right mind you, and it would take a sophisticated cracker, but all the same ;)

I am glad you have learned a little as IMO people take security for granted, so I am trying to teach when and where I can.

---

### Post by jessiebrownjr on 2009-12-04
> **bodhi.zazen said:**
> Yes, I know you are learning, and that is part of why I waited, I did not want my post to detract from your learning and I wanted to wait until I felt you would appreciate the message.

It is not as if Firefox is cracked left and right mind you, and it would take a sophisticated cracker, but all the same ;)

I am glad you have learned a little as IMO people take security for granted, so I am trying to teach when and where I can.

I read over those posts you showed me on the firefox vulns... I'm guessing if I avoid the porn and torrent/warez sites, there is a good shot I would rarely even see one of those xploits on a web page? You *ALMOST* made me scared to get on google :-)

---

### Post by bodhi.zazen on 2009-12-04
So long as you practice "safe browsing" you should be fine. I advise you take a look at NoScript and Adblock. 

NoScript in particular *should* help with those malignant scripts.

---

### Post by jessiebrownjr on 2009-12-05
> **bodhi.zazen said:**
> So long as you practice "safe browsing" you should be fine. I advise you take a look at NoScript and Adblock. 

NoScript in particular *should* help with those malignant scripts.

I downloaded this scripts.... is it okay to log in as root now?
KIDDING:popcorn: anyway, good functionality in them!

---

### Post by thync on 2010-02-06
Hi, I'm trying to figure out how to remove the password prompt when accessing a hard drive (not the installation drive). I store all my  media on the drive and my media programs won't recognise the drive.

It's more of a nuisance than anything else but its also not a security risk. Can anyone help?

Thanks

---

### Post by bodhi.zazen on 2010-02-07
> **thync said:**
> Hi, I'm trying to figure out how to remove the password prompt when accessing a hard drive (not the installation drive). I store all my  media on the drive and my media programs won't recognise the drive.

It's more of a nuisance than anything else but its also not a security risk. Can anyone help?

Thanks

It depends on the file type, NTFS and FAT are different then linux native file systems.

You need an entry for your partition in /etc/fstab

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

