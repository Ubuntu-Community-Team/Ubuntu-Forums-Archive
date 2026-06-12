---
title: "Alleged Ubuntu security mistake"
date: 2014-08-04
forum: Security
---

### Post by welshmike on 2014-08-04
I read in the talkback of: 
[http://www.zdnet.com/six-clicks-how-hackers-use-employees-to-break-through-security-walls-7000027755/](http://www.zdnet.com/six-clicks-how-hackers-use-employees-to-break-through-security-walls-7000027755/)

&#8220;Just say no to privileged user accounts
Privileged user accounts represent a big target

A large part of the blame belongs to Microsoft. There has never been an explanation during installation along the lines of "create an admin account and only use it for installing software and configuration; create regular accounts and use them for surfing, Office, email, etc." 8 actually made things worse by allowing people to use Hotmail/Live/Outlook email accounts for admin logon.

Ubuntu made the same mistake, but Fedora and other Linux distributions which mimic Unix with respect to root are okay.
saucymugwump
27 March, 2014 13:55 &#8220;


My question is &#8220;what Ubuntu mistake is the writer referring to?&#8221;

---

### Post by SeijiSensei on 2014-08-04
Giving the first user admin privileges via sudo I'd imagine.  The traditional *nix approach uses only the root account with its own password.

That said, the article is talking about businesses here.  Any business that doesn't have a well-developed security plan for its computer networks is asking for trouble.  I wouldn't grant admin privileges to anyone on a business network except for a small group of system administrators.  If I were using Ubuntu on a business network, I'd change the security model to the one described above with only administrators having root access to users' workstations.

---

### Post by welshmike on 2014-08-04
Thank you for the reply and explanation.

---

### Post by ajgreeny on 2014-08-04
> **welshmike said:**
> I read in the talkback of: 
[http://www.zdnet.com/six-clicks-how-hackers-use-employees-to-break-through-security-walls-7000027755/](http://www.zdnet.com/six-clicks-how-hackers-use-employees-to-break-through-security-walls-7000027755/)

&#8220;Just say no to privileged user accounts
Privileged user accounts represent a big target

A large part of the blame belongs to Microsoft. There has never been an explanation during installation along the lines of "create an admin account and only use it for installing software and configuration; create regular accounts and use them for surfing, Office, email, etc." 8 actually made things worse by allowing people to use Hotmail/Live/Outlook email accounts for admin logon.

Ubuntu made the same mistake, but Fedora and other Linux distributions which mimic Unix with respect to root are okay.
saucymugwump
27 March, 2014 13:55 &#8220;


My question is &#8220;what Ubuntu mistake is the writer referring to?&#8221;
I believe that quote is not giving the full story and is misunderstanding the Ubuntu security model.

The last MS system I used was XP and in that the users on the system, any of them, could install software, delete files from the system as well as their own user files, and could easily, therefore, totally mess up the whole OS if not careful.

In Ubuntu by default only the first user added is an admin user, all the ones added later are, in windows speak, non-privileged users, so they can not install software etc etc, only use it.  Even that one admin user can not do anything such as installing software without using the password set at installation.  If a business gives all its employees the ability to run admin tasks on their computers it is asking for trouble

So my question is, why is using sudo the Ubuntu way, more risky than having either a root account like Fedora, or having the new (note "new", or relatively) MS security model, about which I admit I know very little.

I think the writer, saucymugwump, should try to understand the Ubuntu security model a bit better, as we can not use Hotmail/Live/Outlook, or any other email accounts, or a web-browser with an admin logon; we can't even have an admin logon to a GUI.

---

### Post by bab1 on 2014-08-04
> **ajgreeny said:**
> ...

So my question is, why is using sudo the Ubuntu way, more risky than having either a root account like Fedora, or having the new (note "new", or relatively) MS security model, about which I admit I know very little.

There is no security difference.  Old unix habits are hard to break.  I will say that folks should have multiple "admin".  Either 2 sudo accounts  or a root that is active.  It's relatively easy to lock yourself out of your sudoers rights with misconfiguration.  Think /etc/hostname.  
> 

I think the writer, saucymugwump, should try to understand the Ubuntu security model a bit better, as we can not use Hotmail/Live/Outlook, or any other email accounts, or a web-browser with an admin logon; we can't even have an admin logon to a GUI.
I agree, but remember that a lot of folks with admin acccounts use gksudo to accomplish a root GUI desktop.  :-(

---

### Post by ajgreeny on 2014-08-04
> **bab1 said:**
> There is no security difference.  Old unix habits are hard to break.  I will say that folks should have multiple "admin",  either 2 sudo accounts  or a root that is active.  It's relatively easy to lock yourself out of your sudoers rights with misconfiguration.  Think /etc/hostname.  That is one of the uses that the recovery mode is for, or use a live system for the repair.  I have never had a second user on my computer and have not had a problem since starting with Ubuntu in 2005.  Perhaps I'm just lucky, or careful, or more importantly, I know what I'm doing.

> **bab1 said:**
> I agree, but remember that a lot of folks with admin acccounts use gksudo to accomplish a root GUI desktop.  :-(Yes, as do I sometimes, but I make sure the application in use is closed down straight away after doing whatever I need it for, and I would **NEVER** use a web-browser or email app in that way.

---

### Post by SeijiSensei on 2014-08-04
> **ajgreeny said:**
> In Ubuntu by default only the first user added is an admin user, all the ones added later are, in windows speak, non-privileged users, so they can not install software etc etc, only use it.  Even that one admin user can not do anything such as installing software without using the password set at installation.  If a business gives all its employees the ability to run admin tasks on their computers it is asking for trouble

Well since sudo relies on the user's own password, he or she can almost certainly install software or make any other changes to the operating system and its file systems.

I see the decision to adopt sudo as largely one of convenience.  Ordinary users working on their own machines chafe at having too much security between them and what they want to do.  So having a separate root password was probably seen as an unnecessary inconvenience.  That's why I limited my earlier remarks to businesses.  In that setting sudo makes no sense to me.  For people sitting in their living rooms a weaker security model may be more appropriate.

---

### Post by bab1 on 2014-08-04
> **ajgreeny said:**
> That is one of the uses that the recovery mode is for, or use a live system for the repair.  I have never had a second user on my computer and have not had a problem since starting with Ubuntu in 2005.  Perhaps I'm just lucky, or careful, or more importantly, I know what I'm doing.

Rebooting doesn't work to well with headless remote servers.  I've been involved in unix and Linux for 25+ years.  I'm not lucky, but I am experienced.  Experienced enough to know that mistakes happen at the most inopportune times. Have I made mistakes?  You bet.  On 10,000+ user systems.  It sure helps when you want to repair a mistake hours after you should be on your way home. 
> 
Yes, as do I sometimes, but I make sure the application in use is closed down straight away after doing whatever I need it for, and I would **NEVER** use a web-browser or email app in that way.
There is no reason to use a root enabled GUI interface.  It may be easier, but it is misuse of the system.

---

### Post by bab1 on 2014-08-04
> **SeijiSensei said:**
> Well since sudo relies on the user's own password, he or she can almost certainly install software or make any other changes to the operating system and its file systems.

I see the decision to adopt sudo as largely one of convenience.  Ordinary users working on their own machines chafe at having too much security between them and what they want to do.  So having a separate root password was probably seen as an unnecessary inconvenience.  That's why I limited my earlier remarks to businesses.  In that setting sudo makes no sense to me.  For people sitting in their living rooms a weaker security model may be more appropriate.
I worked at a university when SUN introduced sudo.  We adopted sudo for 2 reasons.
[LIST]
[*]For limited root access to certain processes (e.g. backup)
[*]For root access to users who moved between our machine room and the system management room
[/LIST]
The last one reason is what I used sudo for.  I had the root account login, but most of the time I was not sitting at my desk.  Sudo allowed me to not have to worry about whether I logged out of a root session when I was away.

I agree with @SeijiSensei.  It is always a battle between users and administrators over convenience vs security.  As an admin on a large system I don't really care about convenience of the user.  If they don't like the security they can talk to the CIO about it.  If you allow users to install applications you have lost control of that host.  It is a rogue host.

---

### Post by bashiergui on 2014-08-04
> As an admin on a large system I don't really care about convenience of the user. If they don't like the security they can talk to the CIO about it. If you allow users to install applications you have lost control of that host. It is a rogue host.Couldn't have said it better myself.

---

### Post by bab1 on 2014-08-04
> **bashiergui said:**
> Couldn't have said it better myself.

I forgot to mention; I'm not in charge of changing your printer cartridge either.  ;-)

---

