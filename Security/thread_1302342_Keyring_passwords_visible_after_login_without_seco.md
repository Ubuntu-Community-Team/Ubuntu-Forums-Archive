---
title: "Keyring passwords visible after login without second password prompt"
date: 2009-10-27
forum: Security
---

### Post by humphreybc on 2009-10-27
Why is it that when I go to Applications > Accessories > Passwords and Encryption Keys I can click on Passwords, then expand 'login' and then I can see my passwords for my MSN account and wireless networks I connect to without once being prompted for my user password?

But then when I change CPU Frequency scaling, I'm prompted to enter my admin password? 

O.o

How to reproduce: 

1. Restart your computer and login. Do not enter any passwords after your desktop has loaded. 

2. Go to Applications > Accessories > Passwords and Encryption Keyrings 

3. Click on the 'Login' folder to drop down and view the programs that store data here. 

4. Double click on something you want to look at. 

5. Click Password to show some dots, then uncheck the box below the dots marked "Show password" 

6. Note that throughout this whole procedure, not once were you prompted* to enter in anything that verifies you are authorized to view this information. 

*The only prompt is asking if it's allowed access to the keyring, to which anyone can click allow.

**Links all in one place:**

[Bug report filed on Launchpad]("https://bugs.launchpad.net/seahorse/+bug/189774")
[OMG! UBUNTU! Blog Post]("http://www.omgubuntu.co.uk/2009/10/security-issue-in-gnome-lets-anyone-see.html")
[Gnome-keyring mailing list]("http://mail.gnome.org/mailman/listinfo/gnome-keyring-list")
[Gnome Keyring Security Philosophy]("http://live.gnome.org/GnomeKeyring/SecurityPhilosophy")
[Ubuntu Brainstorm Idea]("http://brainstorm.ubuntu.com/idea/22120/")

[[IMG]http://brainstorm.ubuntu.com/idea/22120/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22120/)


-------

---

### Post by TrueJournals on 2009-10-27
Because you already entered your password once?  Lock your screen when you leave your computer if you don't want others to see this information...

---

### Post by renkinjutsu on 2009-10-27
gksu and sudo have the 15 minute period where you don't have to type in a password for administrative tasks

---

### Post by Crunchy the Headcrab on 2009-10-27
> **renkinjutsu said:**
> gksu and sudo have the 15 minute period where you don't have to type in a password for administrative tasks
Is it that long?  That's too long for my tastes.  I'm gonna change my sudoers file.

---

### Post by michaelzap on 2009-10-27
> **TrueJournals said:**
> Because you already entered your password once?  Lock your screen when you leave your computer if you don't want others to see this information...
It does seem odd to me that you're not required to enter your password again here. I realize that this is not being done as a superuser and that's probably why, but perhaps viewing the password should require you to re-enter your user password. It doesn't seem like a good idea to allow anyone to view your entered passwords for things like email acounts and whatnot unless you lock your screen or logout.

---

### Post by TrueJournals on 2009-10-27
Regardless, this is something that requires physical access, which is the biggest security whole in the first place.  Why would you lave your computer without locking your screen if you're worried about security?

---

### Post by michaelzap on 2009-10-27
> **TrueJournals said:**
> Regardless, this is something that requires physical access, which is the biggest security whole in the first place.  Why would you lave your computer without locking your screen if you're worried about security?
Both true and irrelevant. It's reasonable to wonder why passwords for things other than your local computer can be viewed in clear text without entering a password. Even Windows doesn't allow that.

---

### Post by sliketymo on 2009-10-27
> **humphreybc said:**
> Why is it that when I go to Applications > Accessories > Passwords and Encryption Keys I can click on Passwords, then expand 'login' and then I can see my passwords for my MSN account and wireless networks I connect to without once being prompted for my user password?

But then when I change CPU Frequency scaling, I'm prompted to enter my admin password? 

O.o

*The only prompt is asking if it's allowed access to the keyring, to which anyone can click allow.
:popcorn: It's Your computer,isn't it? I am sure that if you are concerned about your personal information,your not going to leave your machine lying around,powered up,with your keyring open.

---

### Post by humphreybc on 2009-10-27
All valid points, but, regardless of individual situations I still think that you should not be able to view important passwords without first validating that you are indeed the owner of the accounts they belong to.

---

### Post by prshah on 2009-10-27
> **humphreybc said:**
> Why is it that when I go to Applications > Accessories > Passwords and Encryption Keys I can click on Passwords, then expand 'login' and then I can see my passwords for my MSN account and wireless networks I connect to without once being prompted for my user password?

This is big; you should file a bug report, I guess. No matter what the justifications offered, your keyring passwords should not be opened with prompting for a password. (I don't even get the prompt to allow the keyring to be opened).

---

### Post by talent03 on 2009-10-27
> **humphreybc said:**
> Why is it that when I go to Applications > Accessories > Passwords and Encryption Keys I can click on Passwords, then expand 'login' and then I can see my passwords for my MSN account and wireless networks I connect to without once being prompted for my user password?

But then when I change CPU Frequency scaling, I'm prompted to enter my admin password? 

O.o

*The only prompt is asking if it's allowed access to the keyring, to which anyone can click allow.

Although it does feel disconcerting at first, I got used to putting the system on guest or locking it before leaving the computer and/or handing it to someone. I suppose it is your machine so for me on laptops I do the above and on desktops I manage separate users.

---

### Post by humphreybc on 2009-10-27
> **prshah said:**
> This is big; you should file a bug report, I guess. No matter what the justifications offered, your keyring passwords should not be opened with prompting for a password. (I don't even get the prompt to allow the keyring to be opened).

Could someone else post a bug report for me please? Feel free to use my attached image as a demo. I would do it, but I'm a bit tied up with a [non-booting system.]("http://ubuntuforums.org/showthread.php?p=8173148")

---

### Post by DodgeV83 on 2009-10-27
Wow, blatant security flaw indeed!

---

### Post by the.lost.one on 2009-10-27
If the sudo command asks for password, accessing other partitions asks for password, update manager asks for password, if the wireless access point is turned off for a while it keeps asking for password (annoying since Windows can reconnect automatically when the access point becomes available), why cant accessing keyring and stored passwords require asking for password???

---

### Post by Bachstelze on 2009-10-27
> **michaelzap said:**
> Both true and irrelevant. It's reasonable to wonder why passwords for things other than your local computer can be viewed in clear text without entering a password. Even Windows doesn't allow that.

Orly? See attachment.

> **the.lost.one said:**
> If the sudo command asks for password, accessing other partitions asks for password, update manager asks for password, if the wireless access point is turned off for a while it keeps asking for password (annoying since Windows can reconnect automatically when the access point becomes available), why cant accessing keyring and stored passwords require asking for password???

Because accessing your personal data doesn't require administrator access. Protecting your personal data is *your* responsibility, not the system's.

---

### Post by the.lost.one on 2009-10-27
"Protecting your personal data is *your* responsibility, not the system's."

And I want to protect it by making the system ask for a password to access it. But the system provides no such option. It asks for a password to access other partition which neither has any linux system files nor any other OS files. I don't see much difference between the two from a user's perspective.

And shouldn't accessing system wide keyring be a higher privileged operation?

It's all about having layers of security.

---

### Post by TrueTom on 2009-10-27
> **Bachstelze said:**
> Orly? See attachment.

Trying to prove that Windows shows your passwords in cleartext by showing a screenshot of a third party application is somewhat stupid?

---

### Post by ad_267 on 2009-10-27
Even though I understand why this is the case, I'd agree with requiring a user to enter their password before showing their stored passwords.

---

### Post by imafatmess on 2009-10-27
> **Bachstelze said:**
> 
Because accessing your personal data doesn't require administrator access. Protecting your personal data is *your* responsibility, not the system's.

Lets just say someone had a computer which has automatic loggin on enabled (like me because karmics boot time is so slow) and then, without any password needing to be entered, WHATSOEVER, someone who decides they want to access my computer now can see all my passwords for every single program with just a few clicks. Yes, this is our own responsibility, but SURELY there should be an option to password protect our whole keyring? I know you will probably tell me there is a way, and feel free to tell me, but its not obvious

---

### Post by Bachstelze on 2009-10-27
> **TrueTom said:**
> Trying to prove that Windows shows your passwords in cleartext by showing a screenshot of a third party application is somewhat stupid?

Last I checked, Pidgin and NetworkManager were third-party applications, too. Also Gnome.

> **imafatmess said:**
> I know you will probably tell me there is a way, and feel free to tell me, but its not obvious

I have no idea. I use KDE.

---

### Post by MacUntu on 2009-10-27
Anyone care to share steps to reproduce?

Besides I'm totally with replies #2, #3, and #15.

---

### Post by humphreybc on 2009-10-27
> **MacUntu said:**
> Anyone care to share steps to reproduce?

Besides I'm totally with replies #2, #3, and #15.

1. Restart your computer and login, make sure you never enter any passwords after your desktop has loaded. Don't do any sudoing or anything.

2. Go to Applications > Accessories > Passwords and Encryption Keyrings

3. Click on the 'login' folder to drop down and view programs that store data here.

4. Double click on something you want to look at.

5. Click Password to show some dots, then uncheck the box below the dots marked "Show password"

6. Note that throughout this whole procedure, not once were you prompted to enter in anything that verifies you are authorized to view this information.

Ways to solve: Change how this data is stored or prompt to enter in your user password to view your user data.

---

### Post by MacUntu on 2009-10-27
I've asked because that's exactly what I did and I couldn't reproduce it. Do you have autologin enabled? Maybe an empty keyring password?

---

### Post by the.lost.one on 2009-10-27
Whats the point of having a keyring password when that password is never ever asked? 

Those who do not agree to having a choice for prompting for password, should remove their user passwords and remove even the option to have user login passwords. After all you guys are saying rely ONLY on physical security. Because according to your view, locking the screen is useless as well since anyone can access your data through a live CD/DVD.

---

### Post by the.lost.one on 2009-10-27
> **MacUntu said:**
> I've asked because that's exactly what I did and I couldn't reproduce it. Do you have autologin enabled? Maybe an empty keyring password?

Did it ask you to enter a password or just click the allow button?

---

### Post by MacUntu on 2009-10-27
Ha, got me - yes, I now can reproduce it. Autologin enabled, non-empty keyring password.

---

### Post by humphreybc on 2009-10-27
Hmm I don't have Auto login enabled. I'm pretty sure my keyring has a password, I just did a fresh install though... how to check?

---

### Post by Keyper7 on 2009-10-27
> **the.lost.one said:**
> Those who do not agree to having a choice for prompting for password, should remove their user passwords and remove even the option to have user login passwords. After all you guys are saying rely ONLY on physical security. Because according to your view, locking the screen is useless as well since anyone can access your data through a live CD/DVD.

The keyring only allows the user, logged in, to access the passwords. A live CD/DVD wouldn't work.

The Gnome keyring is based on three simple principles:

1) If someone is logged in as user X, he is user X and has already proved his identity at login.

2) If someone is not logged in as user X, he is not user X and cannot see the passwords of user X. That includes the live CD user.

3) In the unlikely event that someone logged in as user X is NOT user X and has malicious intentions, the mere fact that this person is using user X's account is already a massive security hole as far as personal info is concerned. Imposing security restrictions for this situation is sacrificing usability for minimal security gain.

For more info, see [the security philosophy of Gnome keyring](http://live.gnome.org/GnomeKeyring/SecurityPhilosophy).

If you disagree with this, go discuss in the keyring mailing list. But do not report bugs, this is by design.

---

### Post by humphreybc on 2009-10-27
> **Keyper7 said:**
> The keyring only allows the user, logged in, to access the passwords. A live CD/DVD wouldn't work.

The Gnome keyring is based on three simple principles:

1) If someone is logged in as user X, he is user X and has already proved his identity at login.

2) If someone is not logged in as user X, he is not user X and cannot see the passwords of user X. That includes the live CD user.

3) In the unlikely event that someone logged in as user X is NOT user X and has malicious intentions, the mere fact that this person is using user X's account is already a massive security hole as far as personal info is concerned. Imposing security restrictions for this situation is sacrificing usability for minimal security gain.

For more info, see [the security philosophy of Gnome keyring](http://live.gnome.org/GnomeKeyring/SecurityPhilosophy).

If you disagree with this, go discuss in the keyring mailing list. But do not report bugs, this is by design.

Thanks for clarifying. I guess this does make sense. But then why do I have to enter in my password for a whole host of other things, when I have already proved that it's me at login?

And also, Ubuntu can run for a long amount of time without being rebooted or logged in/out, so surely there should be some sort of timer, perhaps 3 hours, where the user needs to re-prove that it is still the correct user when he/she tries to access seahorse passwords in the keychain.

All I'm saying is that it would be simple to add in a prompt for you to enter in your user password before you are allowed to see the passwords for these things.

The email account and password in particular is very sensitive and important to most people, so more should be done to protect any access to these sorts of user details.

Just my opinion.

---

### Post by Peter09 on 2009-10-27
I find this to be poor security because it assumes that the security level of passwords stored on the machine relate to the level of security of the machine itself.

e.g. Lets say a user is working in an open environment where colleagues and passers by will have intermittent access - say while the person goes for a coffee. This is ok because a) the user is never away very long and b) there is no secure information on the actual machine.

However there may be times when the user accesses a more secure environment, say a particular WiFi network, located elsewhere, even his own personal network at home. Under these circumstances a casual viewer can easily gain access to passwords and keys.

---

### Post by handaxe on 2009-10-27
> **humphreybc said:**
> Thanks for clarifying. I guess this does make sense. But then why do I have to enter in my password for a whole host of other things, when I have already proved that it's me at login?

The password entry for "sudo" etc achieves an elevation of privileges to those you normally do not hold. Your login thus is no proof in the case of "root-like" powers.

Given all that is written here, I think a case can be made for a design change, motivated on the grounds that an OS should help a user and preventing a severe security breach during a few moments absence at the keyboard is both sensible and helpful.

my 0.02c...

HA

---

### Post by humphreybc on 2009-10-27
> **handaxe said:**
> The password entry for "sudo" etc achieves an elevation of privileges to those you normally do not hold. Your login thus is no proof in the case of "root-like" powers.

Given all that is written here, I think a case can be made for a design change, motivated on the grounds that an OS should help a user and preventing a severe security breach during a few moments absence at the keyboard is both sensible and helpful.

my 0.02c...

HA

Nicely summed up. Who/how do we poll for a design change? Or is there already a contributor to this thread who could alert someone or do something about it?

---

### Post by MacUntu on 2009-10-27
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

So your request is basically that the keyring gets closed after a user defined amount of time, right?

---

### Post by chrisccoulson on 2009-10-27
The behaviour described here is completely normal. By default, the "login" keyring is unlocked by your login password when you log in. The login keyring is used for storing things like WPA passphrases and passwords for email accounts. Without this, you would be prompted for a password each time you connected to a wireless network and each time you opened Evolution etc.

You can create extra keyrings which aren't unlocked automatically when you log in. I do this for my Evolution accounts. When you do this, any application which attempts to access the keyring will trigger a password prompt, to allow the application to authenticate and access the keyring. When you see this, you have the option of allowing the particular application to access the keyring only once, or forever (in which case, you won't get any further password prompts each time that application attempts to access the keyring - this only applies to the application you gave explicit permissions too, and you can revoke the permissions later on).

So, there really is no bug here. Passwords aren't stored in plain text anywhere on disk, so you can't just view them. And changing the default behaviour of the login keyring will really annoy users when they get a password prompt to unlock the keyring each time they reconnect to their wireless network.

Also, remember the Pidgin **stores your account passwords in plaintext on your hard disk**. Pidgin doesn't use the keyring, and AFAIR the Pidgin developers aren't interested in doing this either. Empathy **does** store your account passowrds correctly though

---

### Post by handaxe on 2009-10-27
Launchpad bugs has a "wishlist" category but that gets set by triagers and not the bug submitter (or has that changed?).  On Launchpad at the mo', "Wishlist" seems to mean "classify and forget". (Do devs ever pass on wishlist items upstream?). Seahorse is a gnome project ( [http://projects.gnome.org/seahorse/](http://projects.gnome.org/seahorse/) ) and you should try there (at source so to speak).

HA

---

### Post by humphreybc on 2009-10-27
Yeah but we're not asking for anything to be chained regarding how they are stored or how the keyring is unlocked.

Just for a password prompt when trying to view the saved passwords.

I'm not an expert on keyrings by any means, but from my perspective, it does seem a bit silly to have secure passwords accessible from the main menu! Regardless of anything else, this isn't ideal.

---

### Post by humphreybc on 2009-10-27
> **handaxe said:**
> Launchpad bugs has a "wishlist" category but that gets set by triagers and not the bug submitter (or has that changed?).  On Launchpad at the mo', "Wishlist" seems to mean "classify and forget". (Do devs ever pass on wishlist items upstream?). Seahorse is a gnome project ( [http://projects.gnome.org/seahorse/](http://projects.gnome.org/seahorse/) ) and you should try there (at source so to speak).

HA

I just fired off an email to the Seahorse mailing list with a link to this thread. We'll let the experts have a look at our argument and see what they have to say.

---

### Post by scaine on 2009-10-27
> **humphreybc said:**
> Yeah but we're not asking for anything to be chained regarding how they are stored or how the keyring is unlocked.

Just for a password prompt when trying to view the saved passwords.

I'm not an expert on keyrings by any means, but from my perspective, it does seem a bit silly to have secure passwords accessible from the main menu! Regardless of anything else, this isn't ideal.

Exactly true.  If anyone here has ever used the excellent KeePassx (password management) software, that's what it does.  You open your "keyring" of passwords, crucially by supplying a password.  It can also go one better though.  Not by default, but you can ask it to allow viewing of usernames only - and if you want to open the password view, it prompts for your password again to prove it's you.

This behaviour is absolutely vital in the corporate environment where although you might trust your colleagues, you certainly don't want any old passer-by spotting your (foolishly unlocked) PC while you grab a coffee, then popping on and grabbing all your passwords!

I'm astonished that the Seahorse behaviour is being defended on these forums.

---

### Post by scaine on 2009-10-27
I should add that Seahorse and Keepassx aren't really comparable products (although they sound similar), but the way they handle password viewing is an absolutely relevant comparison here.

Just in case someone suggests that if I love Keepassx so much, why don't I use it instead...  ;)

---

### Post by Keyper7 on 2009-10-27
> **handaxe said:**
> I think a case can be made for a design change, motivated on the grounds that an OS should help a user and preventing a severe security breach during a few moments absence at the keyboard is both sensible and helpful.

That feature already exists. It's called "locking the screen".

> **handaxe said:**
> This behaviour is absolutely vital in the corporate environment where although you might trust your colleagues, you certainly don't want any old passer-by spotting your (foolishly unlocked) PC while you grab a coffee, then popping on and grabbing all your passwords!

Then don't leave your PC "foolishly unlocked".

---

### Post by mcduck on 2009-10-27
> **Peter09 said:**
> I find this to be poor security because it assumes that the security level of passwords stored on the machine relate to the level of security of the machine itself.

e.g. Lets say a user is working in an open environment where colleagues and passers by will have intermittent access - say while the person goes for a coffee. This is ok because a) the user is never away very long and b) there is no secure information on the actual machine.

However there may be times when the user accesses a more secure environment, say a particular WiFi network, located elsewhere, even his own personal network at home. Under these circumstances a casual viewer can easily gain access to passwords and keys.

That's what locking your screen is for.

Remember, if you leave your computer running, unlocked an unattended, you are not only compromising your passwords but also all your files. If you do that, complaining about the passwords is a bit pointless.

Still, I'd have nothing against asking for your keyring password again to view saved passwords, but I must say I don't really find that as any significant change in security since the keyring is already unlocked anyway, so the actual keys are usable. And, like I said, computers left unattended are insecure anyway, and should at least be locked if you care even a bit about your security...

---

### Post by adalal on 2009-10-27
Well, like everyone mentions, it's best if you lock your screen if you want noone to access it.

If you're that worried, you might as well know that Firefox has the same policy where you can simply click on 'show passwords' somewhere under the preferences menu. True, you can lock it, but then you will need to enter the password each time you'd want the password to autofill, kinda counter-productive in that case....

---

### Post by handaxe on 2009-10-27
> **Keyper7 said:**
> That feature already exists. It's called "locking the screen".



Then don't leave your PC "foolishly unlocked".

I was referring to being helpful for those of us who are imperfect......;)

HA

---

### Post by michaelzap on 2009-10-27
> **Peter09 said:**
> I find this to be poor security because it assumes that the security level of passwords stored on the machine relate to the level of security of the machine itself.
Exactly! The keyring encrypts stored passwords for a reason (unlike Filezilla, Pidgin, and a number of other apps that take this less seriously). It makes no sense to me to display those passwords in clear text without requiring confirmation that you are the correct user.

The security of the keyring application could be easily improved by simply adding a password confirmation dialog in order to view them in clear text. It's that simple. Telling people they should lock their screen instead is allowing your pedantry to get in the way of improving Ubuntu's security in various real-life situations.

---

### Post by michaelzap on 2009-10-27
> **adalal said:**
> If you're that worried, you might as well know that Firefox has the same policy where you can simply click on 'show passwords' somewhere under the preferences menu. True, you can lock it, but then you will need to enter the password each time you'd want the password to autofill, kinda counter-productive in that case....

Actually, I believe that you only need to enter your password once per FF session, exactly as some of us are suggesting the keyring should work.

---

### Post by humphreybc on 2009-10-27
> **michaelzap said:**
> 
The security of the keyring application could be easily improved by simply adding a password confirmation dialog in order to view them in clear text. **It's that simple.** 

I know, I'm not sure why a few people are up in arms about it. It's not the *functionality* of the program that needs to change, it's the *accessibility* and *privacy.*

Also, relocating "Passwords and Encryption Keys" to the Administration menu would make much more sense. It could even be combined with the Authorizations program, after all, they both have the same icon O.o

As a temporary measure, i'm hiding Passwords and Encryption Keys from the menu... after all, who really clicks on it *that* often?! Obviously not many people, otherwise we would have found this flaw already!

---

### Post by mcduck on 2009-10-27
> **michaelzap said:**
> Exactly! The keyring encrypts stored passwords for a reason (unlike Filezilla, Pidgin, and a number of other apps that take this less seriously). It makes no sense to me to display those passwords in clear text without requiring confirmation that you are the correct user.

The security of the keyring application could be easily improved by simply adding a password confirmation dialog in order to view them in clear text. It's that simple. Telling people they should lock their screen instead is allowing your pedantry to get in the way of improving Ubuntu's security in various real-life situations.

You have already confirmed that you are the correct user. You do that at login time, and when you unlock the screen. (or when you type your keyring password, if you use automatic login.)

The keys are stored encrypted so that other users of the same machine can't access them even if they have read access to your home directory.

humphreybc: Actually moving it to Administration menu wouldn't make any sense at all, since nothing about the keyring is actually an admin task. Preferences-menu might actually be worth considering..

And still, it's not a flaw. Just lock your screen and both your passwords and your files will be safe. That's what you are supposed to do anyway when you leave a computer unattended. No matter what OS or desktop you are running. (if ypu can't bother to do that manually, you can set the power manager or screensaver to lock the computer automatically when idle)

---

### Post by chrisccoulson on 2009-10-27
> **michaelzap said:**
> The security of the keyring application could be easily improved by simply adding a password confirmation dialog in order to view them in clear text. It's that simple. 

That is called "security by obscurity". If the keyring is already unlocked, then applications can access it without a password anyway. Asking for a password to view an already unlocked keyring is pointless.

If you don't like the behaviour, then use a keyring which doesn't unlock automatically. You will get a password prompt when trying to view passwords then.

---

### Post by Keyper7 on 2009-10-27
> **handaxe said:**
> I was referring to being helpful for those of us who are imperfect......;)

Sorry, but if you tend to forget your screen unlocked and someone is interested in your secrets, a password over the keyring won't do much more than give you a false sense of security. If your machine is unlocked, in less than 30 seconds a user can quickly plug a pen drive, copy a keylogger, run it silently on the background, unplug the pen drive and leave.

---

### Post by michaelzap on 2009-10-27
> **chrisccoulson said:**
> That is called "security by obscurity".

No it's not. Security by obscurity would be something like hiding Seahorse in the Accessories menu.

> **chrisccoulson said:**
> If the keyring is already unlocked, then applications can access it without a password anyway. Asking for a password to view an already unlocked keyring is pointless.

If you don't like the behaviour, then use a keyring which doesn't unlock automatically. You will get a password prompt when trying to view passwords then.Allowing applications to access passwords is not the same as displaying them in clear text. I don't want to be asked for a password every time the keyring does its job, just when trying to view passwords in clear text. Why is this so hard for people to understand?

---

### Post by michaelzap on 2009-10-27
> **Keyper7 said:**
> Sorry, but if you tend to forget your screen unlocked and someone is interested in your secrets, a password over the keyring won't do much more than give you a false sense of security. If your machine is unlocked, in less than 30 seconds a user can quickly plug a pen drive, copy a keylogger, run it silently on the background, unplug the pen drive and leave.

And if they've copied your ENCRYPTED keyring, that's really no big whoop now is it?

There are plenty of other things that they could swipe, and many applications are less secure than Seahorse, but I expect better from the system password manager.

---

### Post by Keyper7 on 2009-10-27
> **michaelzap said:**
> And if they've copied your ENCRYPTED keyring, that's really no big whoop now is it?

I never said he could copy the keyring. I said he could install a keylogger.

> **michaelzap said:**
> There are plenty of other things that they could swipe, and many applications are less secure than Seahorse, but I expect better from the system password manager.

No, you expected something *different*. "Better" is a matter of opinion.

---

### Post by michaelzap on 2009-10-27
> **Keyper7 said:**
> I never said he could copy the keyring. I said he could install a keylogger.Only if you've entered your sudo password in the last 15 minutes, I expect.

The point is not that leaving your computer unlocked is a good idea or that not showing passwords in clear text is a security silver bullet. It's an incremental improvement, much like requiring the same (sudo) password to be reentered to install software. Most operating systems do not show stored passwords in clear text, so the argument could be made that this is also expected behavior (I certainly assumed that was the case before reading this thread).

---

### Post by the.lost.one on 2009-10-27
Finally some informative comments.

I don't understand why some people are so against having this option. Locking the screen solves the problem. But there can be several situations when you do NOT want to lock the screen:

For example, you are letting your say cousin or a friend use your laptop / netbook to check mail. It is normal to trust 'em not to do anything too dangerous (child porn etc) but being mischievous, they can see your passwords if the passwords are SO visible. (Creating a guest account is a hassle which through this option one can avoid. No they cant install a keylogger because they dont have the root password which is required for all installation).

OS native and third party applications encrypt user data files, which are only decrypted upon entering a password even though a user is signed in. Roboform is a third party app for Windows that encrypts the web passwords and asks for a main password if one wants to access it. So it is not unusual what we are asking.

It is not a bug, not a blatant security flaw but a feature or an extra layer of security we are asking for.

---

### Post by mcduck on 2009-10-27
> **the.lost.one said:**
> Finally some informative comments.

I don't understand why some people are so against having this option. Locking the screen solves the problem. But there can be several situations when you do NOT want to lock the screen:

For example, you are letting your say cousin or a friend use your laptop / netbook to check mail. It is normal to trust 'em not to do anything too dangerous (child porn etc) but being mischievous, they can see your passwords if the passwords are SO visible. (Creating a guest account is a hassle which through this option one can avoid. No they cant install a keylogger because they dont have the root password which is required for all installation).

OS native and third party applications encrypt user data files, which are only decrypted upon entering a password even though a user is signed in. Roboform is a third party app for Windows that encrypts the web passwords and asks for a main password if one wants to access it. So it is not unusual what we are asking.

It is not a bug, not a blatant security flaw but a feature or an extra layer of security we are asking for.
You don't have to create a guest account. Ubuntu already has a built-in guest login. All you need to use it. Just click the User Switcher applet in top right corner of your screen, and select "Guest Session". Problem solved and you don't need to compromise your files or your passwords by leaving the machine unlocked. :)

(And keyloggers and other malicious programs could be installed for the current user only, which wouldn't require a password if the session was left unlocked.)

---

### Post by the.lost.one on 2009-10-27
There is an option for having a password to access other partitions on teh drive. Why is that? Accessing a folder or partition is not an admin task. They must have put it there because it could be useful in some situations. Just like this feature we want.

---

### Post by the.lost.one on 2009-10-27
> **mcduck said:**
> You don't have to create a guest account. Ubuntu already has a built-in guest login. All you need to use it. Just click the User Switcher applet in top right corner of your screen, and select "Guest Session".

Wow. didnt know that.

> **mcduck said:**
> (And keyloggers and other malicious programs could be installed for the current user only, which wouldn't require a password if the session was left unlocked.)

Really? But it always asks me for a password whenever I install any application. It doesnt give any option to do a current user install?

---

### Post by mcduck on 2009-10-27
> **the.lost.one said:**
> There is an option for having a password to access other partitions on teh drive. Why is that? Accessing a folder or partition is not an admin task. They must have put it there because it could be useful in some situations. Just like this feature we want.

The password isn't asked for that if the partition is configured to be accessible by users.

If accessing it is allowed for normal users or not is decided by the administrator, and can definitely be a task that would require more than basic user privileges, depending on the purpose of that partition.

---

### Post by mcduck on 2009-10-27
> **the.lost.one said:**
> Wow. didnt know that.



Really? But it always asks me for a password whenever I install any application. It doesnt give any option to do a current user install?

You only need the password to install anything system-wide. But quite many programs are usable without installing, and could be simply extracted to your home directory and hidden there. Not to mention what can be done with just a simple script...

Also quite  a lot of nasty stuff could be simply done by creating aliases for commonly used commands (or by editing their launchers), to make them do something else than you'd expect. Like logging data to a file...

While malware/keylogger installed that way wouldn't be as well hidden as root access would allow, it would still be good enough to hide it from user who isn't suspecting anything.

---

### Post by the.lost.one on 2009-10-27
> **chrisccoulson said:**
> ... By default, the "login" keyring is unlocked by your login password when you log in. ...

You can create extra keyrings which aren't unlocked automatically when you log in. I do this for my Evolution accounts. When you do this, any application which attempts to access the keyring will trigger a password prompt, to allow the application to authenticate and access the keyring. .

Really? I have to check this out. This should solve the issue.

> **chrisccoulson said:**
> 
Also, remember the Pidgin **stores your account passwords in plaintext on your hard disk**. Pidgin doesn't use the keyring, and AFAIR the Pidgin developers aren't interested in doing this either. Empathy **does** store your account passowrds correctly though

Hahahaha. Damn. I use Pidgin. *sheepish smile*

---

### Post by emarkay on 2009-10-27
I was going to chime in, but I got reamed because I thought that the default listing of usernames at boot is a possible security risk.

I guess there's a more trust in the world by the  "powers that be" in the Ubuntu community.

It's not about "physical access": it's about remote observation and carefully planned  intrusion,  and,  common sense. The things you don't know about until it's too late.  Those that know COMSEC and those that have been violated before will just have to work a bit harder now.

---

### Post by michaelzap on 2009-10-27
> **emarkay said:**
> I was going to chime in, but I got reamed because I thought that the default listing of usernames at boot is a possible security risk.

I agree with you there as well. It's not a major issue imo, but I don't see why people would want to reveal this info at the login screen. I never use any of the user browser GDM themes for this reason.

---

### Post by Keyper7 on 2009-10-27
> **michaelzap said:**
> Only if you've entered your sudo password in the last 15 minutes, I expect.

A keylogger for the keypresses of the current logged user wouldn't require root access.

---

### Post by TrueJournals on 2009-10-27
Even having an extra password prompt in seahorse wouldn't change the situation.  The person would just have to make another program that DOESN'T prompt for the password an additional time.  The solution is already here: make another keyring that doesn't unlock at login.  Adding a password prompt to seahorse will not improve security at all, really...

---

### Post by DodgeV83 on 2009-10-27
> **humphreybc said:**
> I know, I'm not sure why a few people are up in arms about it. It's not the *functionality* of the program that needs to change, it's the *accessibility* and *privacy.*

Also, relocating "Passwords and Encryption Keys" to the Administration menu would make much more sense. It could even be combined with the Authorizations program, after all, they both have the same icon O.o

As a temporary measure, i'm hiding Passwords and Encryption Keys from the menu... after all, who really clicks on it *that* often?! Obviously not many people, otherwise we would have found this flaw already!

I wouldn't spend too much time arguing about it.  None of the people in this thread who claim it's **not** a big deal to display all your passwords with a few simple clicks from the main menu, have anything to do with the real decision making in Ubuntu.

The argument above (from a mod no less) with the Windows screenshot is embarrassing to say the least.  Showing a screenshot of a third-party application storing the password in cleartext != the operating system itself displaying **all** passwords across all programs from the main menu.

I can see the arguments already;

"Ubuntu is not the operating system, it's Linux!"

"No no, it's not Linux you noob.  It's GNU/Linux"

"You are both noobs, it's Gnome that's doing it, but it's not a big deal because everyone already knows to make 100% sure no one has even 5 seconds alone with your computer without signing on to a guest session first.  Even if you forget, what are the chances they'd click on an icon in the main manu that says "PASSWORDS" anyways?"

blahblahblah

Imagine the uproar if Windows 7 displayed all passwords across all programs, simply by clicking:

Start -> All Programs -> Accessories -> Passwords

But it's possible in Ubuntu and people **defend it?**

Seriously, no point in arguing, just wait for them to fix it.

---

### Post by michaelzap on 2009-10-27
> **dodgev83 said:**
> but it's possible in ubuntu and people **defend it?**

seriously, no point in arguing, just wait for them to fix it.

+1!

---

### Post by plasma-engineer on 2009-10-27
This argument is too long isn't it?  Its obvious that some of us users (yes including me) would like the option to require a password before our passwords are revealed in clear text.  And anyway - surely the precedent is already set in Firefox.  You can save your passwords in Firefox and have the option to set a master password if and only if you would like to.  Those who do not want the inconvenience have the option not to be asked.  Those who want one extra layer of security have the option to have it.

Revealing the passwords is not at all the same as the keyring allowing the passwords to be used by the way!  The former gives other people access to your private information forever and any time from any machine whether you are there or not, and whether or not your own keyboard is then locked.  The latter is for the few moments when you have forgotten to lock your keyboard or decided not to lock it so as not to seem suspicious.

And speaking of suspicious - let us read between the lines and guess that there are legit Ubuntu users who do not want to share ALL their passwords with all the people who they trust.  Fathers and mothers may not trust their children with everything.  Children may want their own privacy.  Have you known your girl/boy friend long enough to tell them all your intimate passwords?  Husbands might even want to hide things from wives and vice versa!  And who are we to judge.

Come on folks!  Let's at least have the option of a password!  Please??

And while I am writing, does anyone else think that it is a huge disadvantage that the new Karmic login screen shows the names of all the accounts on the machine?  I would love to be able to go back to having to type in my username and password.  The next step is to offer a pulldown menu of possible passwords that have been used in the past so that anyone can try them out!  These two topics seem to me not to be unrelated.

---

### Post by ST3ALTHPSYCH0 on 2009-10-27
Actually, I'm glad to have the user menu in Karmic... but could see why someone would want the option to have to type in the user name.

---

### Post by chrisccoulson on 2009-10-27
> **michaelzap said:**
> No it's not. Security by obscurity would be something like hiding Seahorse in the Accessories menu.

Allowing applications to access passwords is not the same as displaying them in clear text. I don't want to be asked for a password every time the keyring does its job, just when trying to view passwords in clear text. Why is this so hard for people to understand?

Yes it is the same. I could write an application in a couple of minutes which would get the password from the unlocked keyring and display it to me in plaintext, thus bypassing the extra password you seem to wish for in order to give yourself the illusion of better security.

Asking for an extra password before displaying a password from your already unlocked keyring (which everything else can already access, with a confirmation from the user) only makes you *think* it is more secure - therefore, it is security by obscurity!

---

### Post by novafluxx on 2009-10-27
> **plasma-engineer said:**
> And while I am writing, does anyone else think that it is a huge disadvantage that the new Karmic login screen shows the names of all the accounts on the machine?

I dislike the new GDM, and its lack of easy customizable options...

---

### Post by humphreybc on 2009-10-27
Here is the official reply from Adam Schreiber of Seahorse:

> 
I'm not going to read that entire thread, but I guess the gist is
someone's asking if providing access to the keyring without prompting
for the password.  Here's the official response regarding the
gnome-keyring security philosophy:
[http://live.gnome.org/GnomeKeyring/SecurityPhilosophy](http://live.gnome.org/GnomeKeyring/SecurityPhilosophy)

In short: lock your screen if you walk away and use the guest session
if someone asks to use your computer.

Cheers,

Adam


The debate is well out of my depth right now, and I think out of most peoples' depths. I think perhaps the issue now is that there isn't a clear understanding of the whole "keyring" system, that's completely new to people coming from a Windows background, like 90%* of Ubuntu users do. Perhaps, somewhere during installation or first login or something there could be an explanation of what the keyring is, how it works, what on earth PGP keys are, why you need them etc etc... heck, I *still* don't understand entirely about how it all works and I've been using Ubuntu full time for almost a year now.

I think perhaps an argument could be made for some adjustment so passwords are not visible in clear text from a **main menu** application. How this is fixed, is up to the experts... but I could think of a couple of solutions, either changing the location of the application to Preferences, or prompting for a password to view login details, or storing the passwords in an encrypted place that only trusted applications are allowed to access. (They get given the trusted status by you the first time they want to use the keyring). Or something like that, as you can see, i'm not really sure. :)

* Made up statistic, but, you know, the majority come from Windows. ;)

---

### Post by sgosnell on 2009-10-27
Have none of you read the security philosophy linked early in the thread?  That's the philosophy of the developers, and they aren't going to change it.  If you're really terrified of it, go to another OS.

Linux is designed as a multi-user system, where multiple users can log onto the same machine at different times.  Any authorized user has access to anything in his domain, or home directories, but no access to anything else.  No other user can access the passwords being complained about.  Also, no user can access any system files outside his home without becoming a superuser or root, by entering a password.  If you can log into your home, then you are presumed to have authorized access to everything there.  It's not just Ubuntu, it's Linux in general.  As for providing detailed explanation of how Seahorse and the keyring work in advance of installation - get real.  It's there if you want to do the research, but most don't want to, as is obvious from the posts on the thread.  It's your responsibility to inform yourself.  The keyring actions are a feature, not a bug.

That's the way it has always been, and I suspect the way it will always be, regardless of minor rebellions like this.  If you can't live with it, there is always Windows and Mac.

---

### Post by cornflake000 on 2009-10-28
I wouldn't change a thing.... but... forget the keyring.  Forget the passwords.  Forget afore said arguments.  If anyone knows how to get to recovery in grub... the game's over.

I love it though!

---

### Post by ElSlunko on 2009-10-28
Might have already been said a few times but to the OP, you have to type your password to log in to Ubuntu, correct? If that is the case then the keyring is unlocked for 15 minutes. If you walk away in those 15 minutes I suppose you are vulnerable.

If you have auto-login enabled you should be prompted for the keyring password. I really wish I could test this last statement but my ubuntu PC is in use for now and will be for most of the night :(

---

### Post by krimzonstarr on 2009-10-28
> **humphreybc said:**
> 
Ways to solve: Change how this data is stored or prompt to enter in your user password to view your user data.

Solutions already in place:
1. Log-Off.
2. Lock Screen.
3. Mindful of allowing access to your personal hardware.
4. Requiring password to log in during boot. (Disabling auto-log-in).

I agree with some of the others, this seems more of a PEBKAC issue, not a bug.

---

### Post by ad_267 on 2009-10-28
> **novafluxx said:**
> I dislike the new GDM, and its lack of easy customizable options...

Bah. It's new, of course it's not fully customisable yet. Get over it and be patient or go back to the old one if you need the customisability.

---

### Post by mcduck on 2009-10-28
> **cornflake000 said:**
> I wouldn't change a thing.... but... forget the keyring.  Forget the passwords.  Forget afore said arguments.  If anyone knows how to get to recovery in grub... the game's over.

I love it though!

If somebody gets free physical access to your computer, the game is over. Regardless of if there's recovery mode in Grub or not. Simply booting a live-CD will give full access to all unencrypted content on the machine, no matter what OS is installed on the computer. :)

---

### Post by humphreybc on 2009-10-28
Ahh gotta love the LiveCD huh. Hence why you encrypt your home directory and stick any important information in there :D

---

### Post by Space_Balls on 2009-10-28
> **mcduck said:**
> If somebody gets free physical access to your computer, the game is over. Regardless of if there's recovery mode in Grub or not. Simply booting a live-CD will give full access to all unencrypted content on the machine, no matter what OS is installed on the computer. :)

Well there are ways around that....
Password protected BIOS, locked PC Case, PW-protected Grub, no CD Drive in Boot order. At least that's what I'm running.

---

### Post by cornflake000 on 2009-10-28
no fun in that...

---

### Post by P4man on 2009-10-28
I dont understand anyone arguing "just lock your computer", or "physical access =  root access" etc. That might be true, but do tell me this, why on earth is there a timeout on sudo then? Why does it even ever prompt you for a password since you already proved your credentials when you logged in, and since you didnt lock the screen, it should just trust you?

This makes zero sense to me. If I leave my PC unattended >15min without locking it, I would know i would risk someone opening my files, reading my emails. I would never assume it would allow someone to read my PASSWORDS any more than I would assume it would allow someone to install a rootkit.

Now the problem seems limited to a few apps that show passwords in plain text, but that seems to include Empathy which is installed by default.

This is a clear security hole, and "locking the screen" is not an appropriate answer. There is a reason every app like firefox lets you save a password but not view it!

---

### Post by Keyper7 on 2009-10-28
> **chrisccoulson said:**
> Yes it is the same. I could write an application in a couple of minutes which would get the password from the unlocked keyring and display it to me in plaintext, thus bypassing the extra password you seem to wish for in order to give yourself the illusion of better security.

Asking for an extra password before displaying a password from your already unlocked keyring (which everything else can already access, with a confirmation from the user) only makes you *think* it is more secure - therefore, it is security by obscurity!

Exactly. It's the "security theater" the philosophy page talks about.

> **DodgeV83 said:**
> Imagine the uproar if Windows 7 displayed all passwords across all programs, simply by clicking:

Start -> All Programs -> Accessories -> Passwords

If the design was the same, the uproar would be wrong. This is not an argument.

> **DodgeV83 said:**
> Seriously, no point in arguing, just wait for them to fix it.

Waiting for them to "fix" a conscious design decision? You should find a chair to sit on, as this might take a while.

You are not happy with the current situation? Go to the mailing list and provide your reasoning there.

This "it's so obviously wrong that the developers will eventually see the light and fix the problem while I wait doing nothing besides complaining on a forum they don't read" attitude won't get you anywhere.

And no, filing a bug report is not "doing something" because "I disagree with it" is not the same as "it's a bug". If you want a design decision to be changed, you should be prepared to engage in a possibly lenghty discussion.

---

### Post by mcduck on 2009-10-28
> **Space_Balls said:**
> Well there are ways around that....
Password protected BIOS, locked PC Case, PW-protected Grub, no CD Drive in Boot order. At least that's what I'm running.

BIOS settings are really easy to reset (which solves both BIOS passwords and boot order), Grub password is nice but won't help a bit when booting a live system, and most case locks use the same key as all the others do. I think I must have at least 10 of those keys around. And in the end cases that would actually provide any resistance if you just grabbed the door and pulled are very rare..

---

### Post by DodgeV83 on 2009-10-28
Sadly, this issue has been around for quite a while

[https://bugs.launchpad.net/seahorse/+bug/189774](https://bugs.launchpad.net/seahorse/+bug/189774)

[http://ubuntuforums.org/showthread.php?t=1075456](http://ubuntuforums.org/showthread.php?t=1075456)

The official response has an eerily familiar ring to it, reminiscent of the Gnome/KDE security fiasco earlier this year.

[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

Follow-up

[http://www.geekzone.co.nz/foobar/6236](http://www.geekzone.co.nz/foobar/6236)

[http://lwn.net/Articles/319072/](http://lwn.net/Articles/319072/)

In short, it was possible to create a "some_text.odt.desktop" file, or "some_text.jpg.desktop" file, that when placed on the Gnome/KDE desktop, looked just like a normal openoffice or picture document.  The Desktop icon not only mirrored what it should look like if the file were legit (the icon made the document look like a standard picture/openoffice file), it even removed the .desktop from the name.

He could send the attachment to someone, they would save it thinking "Hey I'm on Linux, I don't get viruses, and this is just a normal .jpg file anyway" and it would be able to download a script from the internet and run any arbitrary code it was told to.

> The easiest solution to prevent this kind of problem is to not just blindly click on attachments that people have sent you. Does that sound like a sentence you have always heard in the context of Windows before? You bet. The point is: Even on Linux this advice should be taken serious.

A step that could be taken by the Gnome and KDE developers: Require launchers to have execute permissions. A saved attachment won't have those.

The developers refused to do this.  If I remember correctly, "Working as intended" was their response.  It wasn't until this article gave sufficient negative press that the developers fixed the problem.  This problem was around since 2006!

**Why is this relevant to the current thread?**  Because here we are again.  The developers refuse to password protect seahorse and now we have passwords in the clear within 5 seconds on a default Ubuntu install.

Someone above mentioned to create a keyring which doesn't unlock on install, I don't think this is a good solution, as people don't want to be constantly prompted for their password every time they switch routers...etc

Here is my solution for anyone still reading:

Rename /usr/bin/seahorse to something random.
Remove the Passwords icon from the main menu.

This way, you retain the full functionality of the program without the "CLICK HERE TO SEE ALL MY PASSWORDS" button in the main menu, and if you want to run seahorse, simply run the "something random" you renamed seahorse to.  You can also delete the seahorse file, or save it to a USB disk or something, to be used when needed.

Does this save me in all situations?  No.  Can someone come over and simply run their own seahorse file since I deleted mine?  Probably.  Is this better than allowing any Tom Dick and Harry who looks at my computer 3 click access to all my passwords?  Absolutely.

Issues like this, both the security issue and the community response, certainly contribute to the low adoption rate of Ubuntu and Linux in general.

This is what the developers of Pidgin say on their wiki regarding storing passwords in plaintext:

> Having our passwords in plaintext is more secure than obfuscating them precisely because, when a user is not misled by a false sense of security, he is likely to use the software in a more secure manner.  

Source: [http://developer.pidgin.im/wiki/PlainTextPasswords](http://developer.pidgin.im/wiki/PlainTextPasswords)

Here is the big thing people seem to be missing:  Making it easy to view passwords doesn't make your program more secure!  A raise of hands:  How many people here knew Pidgin stored passwords in plain text when first installing?  How many people knew Ubuntu allowed anyone to see all stored passwords in 5 seconds of clicking from the main menu?

**If users aren't aware of these issues, you are only making them less secure.**  Before today, I wouldn't think twice of letting a friend use my computer for a few minutes to check something, especially on Linux.  My friends don't have the sophistication to install a keylogger or similar malicious program on my machine, they wouldn't know where to acquire one, nor would they be so devious.  However, clicking the "passwords" button in your "Start menu", now that doesn't seem so devious.

This is the equivalent of a car manufacturer removing the car locks from your brand new Mercedes, with a note saying "We have removed your car locks.  You are now forced to carefully consider where you park your car.  Since your car can be broken into anyway, even with door locks, we find this is the only way you will feel compelled to protect yourself by not parking in dangerous areas."

The main difference here is I never got my note. 

I don't know about you, but the next time I see a Ubuntu user (I know a few at work), I'm going to ask if I can check a website "real quick".  I won't need the keyboard, only the mouse will do.  I will be sure to note their faces as I read aloud their Gmail password 5 seconds later.  I'm anticipating one of two responses:

1.  Blame Ubuntu for allowing a "Show me all your passwords" button in the main menu

or

2.  Blame themselves for allowing someone to touch their mouse for 5 seconds.

---

### Post by Keyper7 on 2009-10-28
> **DodgeV83 said:**
> Before today, I wouldn't think twice of letting a friend use my computer for a few minutes to check something, especially on Linux.

You might want to think about your definition of friendship. It's certainly not the same as mine.

> **DodgeV83 said:**
> This is the equivalent of a car manufacturer removing the car locks from your brand new Mercedes, with a note saying "We have removed your car locks.  You are now forced to carefully consider where you park your car.  Since your car can be broken into anyway, even with door locks, we find this is the only way you will feel compelled to protect yourself by not parking in dangerous areas."

It's not the same case. A more accurate analogy would be making the car ignition key to be the same as the car door key, thus allowing anyone who has the door key to turn on the car and steal it. I agree this is an absurd security flaw... oh, wait, **cars are exactly like that**.

> **DodgeV83 said:**
> I don't know about you, but the next time I see a Ubuntu user (I know a few at work), I'm going to ask if I can check a website "real quick".  I won't need the keyboard, only the mouse will do.  I will be sure to note their faces as I read aloud their Gmail password 5 seconds later.  I'm anticipating one of two responses:

1.  Blame Ubuntu for allowing a "Show me all your passwords" button in the main menu

or

2.  Blame themselves for allowing someone **they don't trust** to touch their mouse for 5 seconds.

Fixed the second one for you. This allows me to introduce a third one:

3. Blame themselves for trusting you.

---

### Post by rockin_goliath on 2009-10-28
Has anyone considered just locking the keyring, or perhaps making sure that the login keyring is locked by default?

Go to Accesssories -> Passwords and Encryption Keys. Right click on the "login" keyring and select "Lock." Now you are prompted for the keyring password whenever you try to view all the keys.

The only downside to this approach is that whenever an application tried to access the keyring, you are prompted to enter your password, which kind of defeats the purpose.

EDIT: I just discovered that if you logout and the log back in again, the keyring is unlocked again. I have to agree with the OP, this is kind of a security risk.

---

### Post by DodgeV83 on 2009-10-28
> **Keyper7 said:**
> It's not the same case. A more accurate analogy would be making the car ignition key to be the same as the car door key, thus allowing anyone who has the door key to turn on the car and steal it. I agree this is an absurd security flaw... oh, wait, **cars are exactly like that**.

Ok.  This should be more accurate.  I let my friends in my car all the time (letting them in the car, past the first line of defense, but not giving them the key = letting them use my computer after I've logged in for myself).  If I leave them in the car alone for a minute while I run to grab something, I don't expect them to have the ability to easily drive away without the key (my password).

Can they hotwire the car?  Yes.  Is that easy for them to do with no tools and a short amount of time before I return?  No.

Allowing people to view all my passwords with 5 seconds of clicking = my friend who I left in the car being able to drive away without my giving him the key in 5 seconds.

The whole "let's make it trivially easy to steal everything so people are more careful" argument just doesn't hold in the real world, where statistics definitively show that making something harder - though not impossible - to steal is an effective means in lowering it's likelihood of theft.

---

### Post by [h2o] on 2009-10-28
If you don't trust your friends when they use your computer unattended, let them use the guest account. And make sure that all passwords stored in the keyring are not top secret.

---

### Post by Keyper7 on 2009-10-28
> **DodgeV83 said:**
> Ok.  This should be more accurate.  I let my friends in my car all the time (letting them in the car, past the first line of defense, but not giving them the key = letting them use my computer after I've logged in for myself).  If I leave them in the car alone for a minute while I run to grab something, I don't expect them to have the ability to easily drive away without the key (my password).

Can they hotwire the car?  Yes.  Is that easy for them to do with no tools and a short amount of time before I return?  No.

The analogy is complete. You are relying on obscurity (fast hotwiring is hard for most people) instead of seeing the bigger picture (fast hotwiring is not impossible) and adopting better procedures (not leaving people you don't trust alone in your car in the first place).

If you really have "friends you can't trust" (quotes necessary as for me such thing is a oxymoron), don't let them use your account, period. Opening a terminal and doing a "rm -rf ~" is faster and allows a much shorter reaction time than opening the keyring manager. And it's probably far more dangerous: the amount of people who has so-sensitive-that-my-world-will-explode-if-people-read-it information is probably smaller than the amount of people who makes regular backups of their home directory.

---

### Post by Peter09 on 2009-10-28
A better analogy is - why bother having a steering lock and an ignition key - hell if the guy has got through the car door then all is lost anyway!

Its tough and your fault if you left the car unlocked or the kiddie left the passenger window open.


A lot of the people here are talking as 'security geeks' they believe we all go around thinking about protecting our computers. Most people don't, they expect to have some layers of security - ok if the bloke can sit down in front of the screen for 3 mins, well he should not be able to do much - right, and yes he might compromise this machine - but not every other password protected system I know.

---

### Post by [h2o] on 2009-10-28
> **Peter09 said:**
> A better analogy is - why bother having a steering lock and an ignition key - hell if the guy has got through the car door then all is lost anyway!
But someone who is stealing my car is not likely a friend of mine who I have borrowed the car keys.
If I borrow my car to a friend I will most likely give him the key to the steering lock as well. So this is a false analogy.

---

### Post by P4man on 2009-10-28
All analogies break down at some point lets not waste time with that.

No one defending this decision has answered me yet why there is a timeout on sudo? Why? Why is there  even a need to type a password for sudo when the only way to be safe is locking your screen anyhow?

---

### Post by [h2o] on 2009-10-28
> **P4man said:**
> No one defending this decision has answered me yet why there is a timeout on sudo? Why? Why is there  even a need to type a password for sudo when the only way to be safe is locking your screen anyhow?

Since sudo gives access to the entire machine, not just your personal data. If I share machine with other people I should be able to access my data, but not theirs. Nothing strange, really.
Also it gives some protection against malicious code since at least you have to explicitly give the administrator password before anything serious can take place.

---

### Post by P4man on 2009-10-28
> **'[h2o] said:**
> Since sudo gives access to the entire machine, not just your personal data. If I share machine with other people I should be able to access my data, but not theirs. Nothing strange, really.
Also it gives some protection against malicious code since at least you have to explicitly give the administrator password before anything serious can take place.

Most malicious code is designed to obtain your passwords. What could possibly be a worse security breach? A regular user is constantly annoyed having to enter his password to do about anything, just so  an attacker is not able to install malicious code, but he doesnt even have to!

---

### Post by SeanBlader on 2009-10-28
I've read every post in this entire thread, and I'm not going to go argue with coders about their security policy, but really this is lack of security policy.

What it's actually saying is that if I give you my car key you should have immediate access to the network of the company where I work since all the VPN passwords are visible in clear text in seahorse.

I took the advice above, removed the Passwords and Encryption Keys from the accessories menu, and I renamed seahorse itself, ironically after having to type in my password. In addition to that suggestion, make sure you go into your .bash_history file and remove the line that shows what you renamed it to.

There is a difference between someone who's a dedicated and prepared hacker taking advantage of an unlocked idle system, and a normal user who expects their linux system to be secure enough to not allow access to corporate VPN passwords within 5 seconds of walking up to a terminal. Same reasoning, there's a difference between a program or script having access to an unlocked keyring with my permission than there is for a user to have access to all my passwords. It's a matter of expertise, a dedicated professional with the right tools, can steal a car, break into your house, etc. but I don't expect that a normal person could get access to secure passwords with less effort than it would take for them to simply put a fingerprint on my car. Which it does now, it's farther to walk to get to my car than it is to get to my console.

Personally I don't even like to have a screensaver password because I hate having to type in my password if my laptop sits idle while I'm on the workstation, but I setup a screensaver password with a longer timeout and I setup <super>-l to lock the workstation similar to Windows. I'm not paranoid by any stretch, and I work in an environment where I feel safe leaving my wallet and personal laptop on my desk while I'm away from  my keyboard, but having clear text passwords visible at the console right at the applications menu is a bug. And I don't believe that to be a matter of opinion. Believe what you will.

---

### Post by krimzonstarr on 2009-10-28
> **P4man said:**
> All analogies break down at some point lets not waste time with that.

No one defending this decision has answered me yet why there is a timeout on sudo? Why? Why is there  even a need to type a password for sudo when the only way to be safe is locking your screen anyhow?

Some GNU/linux veterans would argue that normal users shouldn't even be using an account that has the same password as your sudo password. Sudo does not intend to provide for privacy, but for security. User A, once they login, has access to user A data only. User B, once they login, has access to user B data only. Administrator, either by logging in as root, or temporary elevating another User through sudo (if they are listed in sudoers), can access the entire system.

Sudo is there to provide Administrator access only. Functions that could bork your system, change major facets of your install or system. These things require a global Administrator account. Since it is dangerous to stay logged in as Admin constantly (I'm talking about something like accidentally running a script to rm Everything, or the like), Ubuntu uses User accounts with sudo ability.

Privacy is a human issue, not software, at this point. I have used a few distros now, and I see no issue with this problem. As User A, why should I not be able to go in to Keyring and see User A's passwords? This has always been the case under Gnome. Many programs, I can simply click the little checkbox "Show Password," and see what it is I typed or Keyring entered. When I lock my screen, or my screensaver triggers, my account cannot be accessed by others. Handing my laptop to another user, it takes 3 seconds to click "Guest Account," again locking my personal data. When I log out of User A, User A's passwords are not viewable, even with a LiveCD.

The comparison of one OS to another is pointless. I can easily borrow a friends laptop to check my flashdrive on any Windows release... and slip in a tiny program to copy all the saved passwords in plaintxt to my drive. It's free and readily available if people know where to look. With Hirams (sp?) Win Boot, installed to flash, I don't even need their computer on. At least with Ubuntu, my /home partition is automatically encrypted when I log-off.

As yet another paranoid computer user ;) I am pleased with the levelS of protection that Ubuntu, and GNU/linux provide me with. It's all about how you use it.

---

### Post by SeanBlader on 2009-10-28
> **krimzonstarr said:**
> As yet another paranoid computer user ;) I am pleased with the levelS of protection that Ubuntu, and GNU/linux provide me with. It's all about how you use it.

In this case it's about a lack of education and training for Linux users. If I'd known that someone could get access to sensitive stuff **that easily** I'd have made an effort to change something sooner. Again, it's the difference between someone LOOKING to steal your passwords, which really you can't stop no matter what you do, all they need to do is take your hard drive and they realistically have all the data you've saved, encryption is not unbreakable. But make it hard enough that it's not worth most people's effort and you're fine. Seahorse is WAY on the wrong side of that line.

---

### Post by snkiz on 2009-10-28
While I'm the last person to say the os should compensate for user stupidity. I have to agree that 4 clicks to see passwords is a little too easy. Sure you could write a script to retrieve passwords from the keyring. But the point is that someone who knows how to do that could get your info regardless. The op is just asking for protection from lookieloos, for whom the simple measure of not showing the passwords in clear text without confirmation would be effective. I think the sudo issue is confusing as well because your sudo password is the same as your user password. (Not good but, an argument for another thread.) Personally I try not to login to my sudo account directly, but through a terminal for that reason. The downside is I have to enter my password twice to use sudo.
```
su -c "sudo whatever" adminaccount
password: adminpass
(sudo)password: adminpass
whatever runs.
```
I guess removing the keyring from the menu would do the trick, but then a new user would probably never find it. A bigger security hole IMHO.

---

### Post by SeanBlader on 2009-10-28
> **snkiz said:**
> While I'm the last person to say the os should compensate for user stupidity.

I totally agree with this, but this isn't a stupidity issue, it's an education issue. And if you're not going to go to the steps to educate your users to protect themselves from "everyone" then you need to help them. Seahorse isn't helping. Of course there's no way you're going to protect yourself from Kevin Mitnick should he want to know your passwords, but at least you shouldn't have to worry about protecting your passwords from Paris Hilton. The current default setup doesn't even manage that.

---

### Post by sgosnell on 2009-10-28
Obviously a lot of people misunderstand the purpose of sudo, superuser, and administration.  Those are not for securing user passwords, they're for securing the entire system.  They prevent malware from infecting the entire machine, by requiring a password before altering system files.  They have nothing at all to do with user passwords.  These are entirely separate issues.  It's easy enough to not allow seahorse to access your user passwords, and you can remove it entirely if you like.  Things will be much more inconvenient, but if you're really worried about your passwords, that's the way to go.  I run a separate password safe on my system, and only allow seahorse access to a limited subset of my passwords, but then I've done a little research on the subject.  If you just suddenly discovered all this, then you need to take the time to learn what is going on, and why, before you jump up on your soapbox and proclaim your ignorance to the world.  Again, none of this is new, or even recent.  It's a design decision made long ago, and that decision will not be changed lightly, whether or not you agree with it.

---

### Post by anders_c_ on 2009-10-28
Personally i think the best way to solve this would be the exactly the same way as the other privileges are handled, for example if i change CPU frequency i get some key-icon in my tray saying i still have privileges and just clicking that icon will drop them.
would it be possible to have a tray-icon showing that your keyring is unlocked and locking it just by clicking that icon?

and btw, does anyone know the CLI command to lock default keyring? im thinking of adding a custom launcher that executes that command, that way i would never be more than one click away from having my passwords securely encrypted.

---

### Post by benj1 on 2009-10-28
> **SeanBlader said:**
> I totally agree with this, but this isn't a stupidity issue, it's an education issue. And if you're not going to go to the steps to educate your users to protect themselves from "everyone" then you need to help them. Seahorse isn't helping. Of course there's no way you're going to protect yourself from Kevin Mitnick should he want to know your passwords, but at least you shouldn't have to worry about protecting your passwords from Paris Hilton. The current default setup doesn't even manage that.

the point is if you protect your passwords from 'paris hilton', most users will think their computer is secure, ignoring the fact it is trivially easy for 'Kevin Mitnick' to get what he wants, at present if the system isnt secure the system makes no attempt to actually make it appear secure (anything else is security through obscurity), thus the user should be more likely to secure it properly. 
i dont think its an education issue, it should be fairly obvious that if you leave your computer logged in and unlocked it wont be secure. linux actually does a very good job in those circumstances by protecting everyone else, ie through sudo etc.

---

### Post by SeanBlader on 2009-10-28
Here's what it comes down to, I don't need to SEE my passwords, and I don't want anyone else with 30 seconds to spare to SEE them either if they walk up to my console. What is the best way can we make this happen?

---

### Post by benj1 on 2009-10-28
> **SeanBlader said:**
> Here's what it comes down to, I don't need to SEE my passwords, and I don't want anyone else with 30 seconds to spare to SEE them either if they walk up to my console. What is the best way can we make this happen?

log out when leaving your computer unattended

---

### Post by chrisccoulson on 2009-10-28
> **SeanBlader said:**
> Here's what it comes down to, I don't need to SEE my passwords, and I don't want anyone else with 30 seconds to spare to SEE them either if they walk up to my console. What is the best way can we make this happen?

Change your keyring password to not match your login password? It's easy, and it means the keyring won't be unlocked when you log in. But you'll have to enter the keyring password to unlock it when an application like NM, Evolution, Empathy etc wants to access it

---

### Post by SeanBlader on 2009-10-28
> **benj1 said:**
> log out when leaving your computer unattended

And if you forget? I don't think, "sucks to be you" is the message you want to send if you ever want to fix [this bug]("https://bugs.launchpad.net/ubuntu/+bug/1").

Let me put it this way, are you going to tell your CEO that if he wants to keep anyone from accessing all his passwords he has to log out of his machine every time he looks away from his computer for more than 30 seconds? I know for a fact that a certain CEO at a major encryption company would laugh in your face, with the comment, "my time is more important than that, you just need to make your software better."

---

### Post by DodgeV83 on 2009-10-28
> **benj1 said:**
> log out when leaving your computer unattended

This won't prevent him from seeing his password if he's logged in.  If you don't want to be able to see your password list from the main menu, you can remove the PASSWORDS entry from the menu and delete or rename the /usr/bin/seahorse program to something you will remember.

---

### Post by chrisccoulson on 2009-10-28
> **DodgeV83 said:**
> This won't prevent him from seeing his password if he's logged in.  If you don't want to be able to see your password list from the main menu, you can remove the PASSWORDS entry from the menu and delete or rename the /usr/bin/seahorse program to something you will remember.

And that won't prevent me from seeing your password. I'll just bring a copy of seahorse on my pendrive, or extract it from a deb i download on your machine, or bring another small utility i write which retrieves all your secrets from your unlocked keyring.

It seems weird that a bunch of people who seem to be paranoid about things like this can't even be bothered with pretty basic security such as locking your screen when you're away, or changing your keyring password to not unlock on log in etc.

---

### Post by benj1 on 2009-10-28
> **SeanBlader said:**
> And if you forget? I don't think, "sucks to be you" is the message you want to send if you ever want to fix [this bug]("https://bugs.launchpad.net/ubuntu/+bug/1").

Let me put it this way, are you going to tell your CEO that if he wants to keep anyone from accessing all his passwords he has to log out of his machine every time he looks away from his computer for more than 30 seconds? I know for a fact that a certain CEO at a major encryption company would laugh in your face, with the comment, "my time is more important than that, you just need to make your software better."

if you forget, they are unsecure. what would the ceo say when his passwords were taken from his computer that he thought was secure but in fact wasnt, it just gave the illusion of being so, if you prefer that security model go with windows. yes you could take the menu option away but the passwords still wont be secure, you could just do this [http://michael.susens-schurter.com/blog/2008/10/30/listing-all-passwords-stored-in-gnome-keyring/]("http://michael.susens-schurter.com/blog/2008/10/30/listing-all-passwords-stored-in-gnome-keyring/") 
if you want it actually secure logout or set your system to not unlock the keyring on login, and set up a time out.
the most secure method would to have every app have its own password keyrings with separate passwords etc, on time outs, but i would rather not have to log in to wifi then evolution and everything else that needs a password separately, that is why we have one app to do it all at once.

---

### Post by DodgeV83 on 2009-10-28
> **benj1 said:**
> the point is if you protect your passwords from 'paris hilton', most users will think their computer is secure, ignoring the fact it is trivially easy for 'Kevin Mitnick' to get what he wants, at present if the system isnt secure the system makes no attempt to actually make it appear secure (anything else is security through obscurity), **thus the user should be more likely to secure it properly. **
i dont think its an education issue, it should be fairly obvious that if you leave your computer logged in and unlocked it wont be secure. linux actually does a very good job in those circumstances by protecting everyone else, ie through sudo etc.

This is a computer geek's way of thinking which will never apply to the real world.

Regarding [this bug]("https://bugs.launchpad.net/ubuntu/+bug/1") which was mentioned earlier.  This is how the conversation will go down for any new user I setup a new computer with:

Windows/Mac computer: "Ok you're all setup.  Now a word of warning, always be careful who you let on your computer.  An expert computer hacker can have access to all your passwords if he knows what he's doing."

Ubuntu computer:  "Ok you're all setup.  Now a word of warning, always be careful who you let on your computer.  Ubuntu has a "PASSWORDS" button (ironically right next to the "search" button), which will provide anyone who can click a mouse with immediate access to all your passwords"

You may be thinking "Great!  Now the Ubuntu user will be extra super duper careful who they let on their computer and lock their computer 100% of the time!"

Reality - "Please give me my Windows back."

[IMG]http://imgs.xkcd.com/comics/security.png[/IMG]

---

### Post by benj1 on 2009-10-28
> **DodgeV83 said:**
> This won't prevent him from seeing his password if he's logged in.  If you don't want to be able to see your password list from the main menu, you can remove the PASSWORDS entry from the menu and delete or rename the /usr/bin/seahorse program to something you will remember.

which is security through obscurity

except removing seahorse, which would just lower usability, i personally dont want to have to enter my password every time i want to go on the internet.

---

### Post by ranch hand on 2009-10-28
I just tried this under Jaunty.  I was asked to grant permission (like the normal stupid MS system) but not to give a password.  I was able to get the password for our other computer from the ssh login entry.

This is not good at all.

---

### Post by benj1 on 2009-10-28
> **DodgeV83 said:**
> This is a computer geek's way of thinking which will never apply to the real world.

Regarding [this bug]("https://bugs.launchpad.net/ubuntu/+bug/1") which was mentioned earlier.  This is how the conversation will go down for any new user I setup a new computer with:

Windows/Mac computer: "Ok you're all setup.  Now a word of warning, always be careful who you let on your computer.  An expert computer hacker can have access to all your passwords if he knows what he's doing."

Ubuntu computer:  "Ok you're all setup.  Now a word of warning, always be careful who you let on your computer.  Ubuntu has a "PASSWORDS" button (ironically right next to the "search" button), which will provide anyone who can click a mouse with immediate access to all your passwords"

You may be thinking "Great!  Now the Ubuntu user will be extra super duper careful who they let on their computer and lock their computer 100% of the time!"

Reality - "Please give me my Windows back."

i personally would prefer it to be obvious if my pc is secure or not, just like if i lock my door i would rather it actually locks rather than just making a reassuring sound.
i also made the point in a previous post that if you dont like that security model you should go back to windows, but at the end of the day who has the better reputation on security?

---

### Post by DodgeV83 on 2009-10-28
> **benj1 said:**
> i personally would prefer it to be obvious if my pc is secure or not, just like if i lock my door i would rather it actually locks rather than just making a reassuring sound.
i also made the point in a previous post that if you dont like that security model you should go back to windows, but at the end of the day who has the better reputation on security?

Again, a computer geek's way of thinking (Don't be offended, I'm a geek too :))

Most people don't understand computers.  They click on the little 'e' to get internet and have no conception of what an OS is.  I just did a straw poll around the office (all Windows users) and gave both sides of the argument.  In the end, none of them felt comfortable using a system with a PASSWORDS button in the "Start Menu".

"That's ridiculous", "Doesn't make any sense", "And they **refuse** to simply password protect it?" were a few of the responses.

This, my friends, is why Ubuntu is a geek's system.

Mark my words, Ubuntu or any other Linux distro will **never** gain significant marketshare, as long as there is a PASSWORDS button in the "Start Menu".

---

### Post by snkiz on 2009-10-28
Com'on people this security through obscurity argument is silly. Its starting to sound like the pidgin mailing list in here. People just don't want passwords 4 clicks away. If the problem is education then how 'bout this:
"Your passwords have obscured to protect you from over-the-shoulder attacks, please be aware that as log as you are logged in your passwords are accessible to your desktop environment. Please Remember not to leave your session open and unattended."

Put that in the empty space in seahorse. now everyone is happy and informed.

---

### Post by the.lost.one on 2009-10-28
> **chrisccoulson said:**
> ...I could write an application in a couple of minutes which would get the password from the unlocked keyring and display it to me in plaintext, thus bypassing the extra password you seem to wish for in order to give yourself the illusion of better security.

You can write such an application, I can't, my family can't, my friends can't and 99% of all people who are likely to get physical access to my machine can't either.

Which is better:
a) 9 out of 10 people can successfully steal my passwords; or
b) 2 out of 10 people can successfully steal my passwords

> **Keyper7 said:**
> The analogy is complete. You are relying on obscurity (fast hotwiring is hard for most people) instead of seeing the bigger picture (fast hotwiring is not impossible) and adopting better procedures (not leaving people you don't trust alone in your car in the first place).

If you think any security measure is impossible to break, you know less about security than even what I do. **You cannot have any measure that is _impossible_ to break.** What about AES 128 bit encryption? Breaking it may require an insane number of years for a normal person today but 20 years from now it might be possible to break it easily. Forget 20 years, there is a good likelihood that the US or other govt might have some powerful secret supercomputer that can break it in a reasonable time. So according to your logic we shouldn't use SSL/TLS encryption because there could be someone who can break it.

**Security through obscurity is when obscurity is the ONLY security measure.** When there is obscurity in addition to fundamental security, it makes things a bit more secure. Steve Gibson  says that too.

---

### Post by the.lost.one on 2009-10-28
And oh on Windows, if I save the password in MSN or Yahoo, it can login automatically but is doesn't show passwords in clear text. The wifi password it does but not MSN and Yahoo. I suppose there must be a way of getting that as well but then again, I don't know it, my friends don't know it and most people likely to get physical access to my machine don't know it.

Why not make the Desktop background or wallpaper display all passwords? That would surely make us noobs lock our screens, eh?

---

### Post by benj1 on 2009-10-28
> **DodgeV83 said:**
> Again, a computer geek's way of thinking (Don't be offended, I'm a geek too :))

Most people don't understand computers.  They click on the little 'e' to get internet and have no conception of what an OS is.  I just did a straw poll around the office (all Windows users) and gave both sides of the argument.  In the end, none of them felt comfortable using a system with a PASSWORDS button in the "Start Menu".

"That's ridiculous", "Doesn't make any sense", "And they **refuse** to simply password protect it?" were a few of the responses.

This, my friends, is why Ubuntu is a geek's system.

Mark my words, Ubuntu or any other Linux distro will **never** gain significant marketshare, as long as there is a PASSWORDS button in the "Start Menu".
what was the question? "would you rather have a system where you can easily view passwords when logged in, but are secure when you aren't, or would you rather have a system that appears to be secure all the time, when in fact it never actually is?"

at the end of the day this thread is about whether this is a security flaw, it isnt. 
yes you could argue that people would prefer the illusion of security rather than actual security (most terminal cancer patients would probably prefer to be told they arent going to die), thats fine dont use ubuntu, which is the same answer to all "linux isnt windows" threads.
i for one prefer linux because it actually treats me like an intelligent adult instead of wrapping me up in cotton wool, patting me on the head and telling me everythings ok.

---

### Post by macgar32 on 2009-10-28
Why does it have an option to show the password in clear text...They are passwords you should already know them.  There should be no need for you to view your passwords once entered.  The keyring should not be used as a tool to jog your memory, if you are forgetful there are other options for logging your passwords.

I think the option to view your password in clear text should be removed completely.

---

### Post by benj1 on 2009-10-28
> **the.lost.one said:**
> And oh on Windows, if I save the password in MSN or Yahoo, it can login automatically but is doesn't show passwords in clear text. The wifi password it does but not MSN and Yahoo. I suppose there must be a way of getting that as well but then again, I don't know it, my friends don't know it and most people likely to get physical access to my machine don't know it.

do you need a password to access them? if not they arent encrypted so its less secure than seahorse, if they do they are as secure (depending on encryption method), just because you cant see the password doesnt mean its not trivially easy for someone else to find.

---

### Post by benj1 on 2009-10-28
> **macgar32 said:**
> Why does it have an option to show the password in clear text...They are passwords you should already know them.  There should be no need for you to view your passwords once entered.  The keyring should not be used as a tool to jog your memory, if you are forgetful there are other options for logging your passwords.

I think the option to view your password in clear text should be removed completely.

i personally cant remember all my wifi, email, forum etc etc passwords, i would much rather have the option of reading them from sea horse than writing them in a text file, or a piece of paper. and its still missing the point that if some one has access to your logged on system, your passwords, or anything else arent secure.

---

### Post by DodgeV83 on 2009-10-28
> **benj1 said:**
> what was the question? "would you rather have a system where you can easily view passwords when logged in, but are secure when you aren't, or would you rather have a system that appears to be secure all the time, when in fact it never actually is?"

at the end of the day this thread is about whether this is a security flaw, **it isnt**. 
yes you could argue that people would prefer the illusion of security rather than actual security (most terminal cancer patients would probably prefer to be told they arent going to die), thats fine dont use ubuntu, which is the same answer to all "linux isnt windows" threads.
i for one prefer linux because it actually treats me like an intelligent adult instead of wrapping me up in cotton wool, patting me on the head and telling me everythings ok.

In your opinion it isn't.

At the end of the day, this thread has shown there are people who do not regard 5 second of mouse clicks to your most important (credit card/VPN network protecting) passwords as a security flaw, and there are some who do.

I have no doubt this will be "fixed" eventually.  Just like the Gnome/KDE .desktop issue, once sufficient negative press is reported on the issue, it will be changed.  The devs will be dragged into it kicking and screaming, but it will be changed.  If Ubuntu ever wants to make it to the big leagues, it is inevitable.

I personally do not feel comfortable with a big [IMG]http://blog.tmcnet.com/blog/tom-keating/images/easy-button.jpg[/IMG] anyone can push to get access to my passwords.

To each his own.

---

### Post by P4man on 2009-10-28
> **benj1 said:**
> i personally cant remember all my wifi, email, forum etc etc passwords, i would much rather have the option of reading them from sea horse than writing them in a text file, or a piece of paper.

Sure. But that doesnt mean it shouldnt even ask you a password before **showing** them! What next? Why not have a button next to your login which says "Forgot your password?" and clicking it tells you" your password is *xyz123*. Physical access =  root access, so why not, hm? This is just as bad!

>  and its still missing the point that if some one has access to your logged on system, your passwords, or anything else arent secure.

If it wasnt for this blatant  security hole, how would my passwords not be secure, even if someone does get access to my logged in machine?

---

### Post by the.lost.one on 2009-10-28
> **benj1 said:**
> do you need a password to access them? if not they arent encrypted so its less secure than seahorse, if they do they are as secure (depending on encryption method), just because you cant see the password doesnt mean its not trivially easy for someone else to find.

Probably the applications encrypt their own passwords. But are you getting the point? It might be easy for you, but it is not for me, not for most people who are likely to get physical access to my machine.

---

### Post by SeanBlader on 2009-10-28
> **benj1 said:**
> but at the end of the day who has the better reputation on security?

Maybe after someone uses this method to break in and find out the medical records of a Seahorse developer can we get this fixed, because I promise you that could happen and this is an unacceptable security risk. Sure the risk is that someone might forget to lock their system when they step away, but giving away passwords at the click of a mouse isn't going to fly when you're looking for health insurance and can't get any because some private detective used someone's password to get into some hospital's network and found out that you were once admitted for appendicitis, and it was found that you had traces of marijuana in your blood, and now you're being prosecuted for insurance fraud because you didn't state the use of controlled substances on your insurance application. So now you're without health care, your family is without an income and out on the street, and you're in jail on fraud charges pending bail that you can't afford to pay. All because someone at some hospital forgot to lock their computer and someone else got paid $20 to look up all your passwords through seahorse.

At this point after learning that most users can find all my passwords with console access and no additional software, I'm thinking that my faith in Linux security is potentially unfounded.

---

### Post by benj1 on 2009-10-28
> **DodgeV83 said:**
> In your opinion it isn't.

At the end of the day, this thread has shown there are people who do not regard 5 second of mouse clicks to your most important (credit card/VPN network protecting) passwords as a security flaw, and there are some who do.

I have no doubt this will be "fixed" eventually.  Just like the Gnome/KDE .desktop issue, once sufficient negative press is reported on the issue, it will be changed.  The devs will be dragged into it kicking and screaming, but it will be changed.  If Ubuntu ever wants to make it to the big leagues, it is inevitable.

I personally do not feel comfortable with a big [IMG]http://blog.tmcnet.com/blog/tom-keating/images/easy-button.jpg[/IMG] anyone can push to get access to my passwords.

To each his own.

the security flaw is failing to logout or lock your session, not the human readable passwords.
to continue with the button analogy, all you are proposing is hiding it under you desk, instead of locking it in the safe.

---

### Post by SeanBlader on 2009-10-28
> **benj1 said:**
> the security flaw is failing to logout or lock your session, not the human readable passwords.

The security flaw is failing to tell users that they need to lock their systems if they're AFK for more than 30 seconds.

---

### Post by the.lost.one on 2009-10-28
Whats the difference between 16-bit encryption and 128 bit encryption? The latter would take more time to be broken.

Whats the difference between having a *show passwords* button and not having such button? The latter would require a person to have technical knowledge and more time to break it.

---

### Post by benj1 on 2009-10-28
> **P4man said:**
> Sure. But that doesnt mean it shouldnt even ask you a password before **showing** them! What next? Why not have a button next to your login which says "Forgot your password?" and clicking it tells you" your password is *xyz123*. Physical access =  root access, so why not, hm? This is just as bad!

your example is flawed, the keyring is unlock when you log in there fore you have already provided your password, is it a security flaw to have a 'forgotten you password?' button on the desktop?  pehaps but the bigger security flaw would be failing to lock the system.

@SeanBlader im sure the seahorse developers probably lock their system when they leave it unattended, because they understand that otherwise it isnt secure.

@the.lost.one i agree it might make it harder for alot of people to get hold of those passwords, the problem is those arent the people who will likely be looking for those passwords, in a previous post i posted a script to get all the passwords in seconds, it took 5 minutes of googling.
also if something is encrypted without requiring a password, its not secure, the encryption key needs to be stored somewhere.

---

### Post by P4man on 2009-10-28
> **SeanBlader said:**
> The security flaw is failing to tell users that they need to lock their systems if they're AFK for more than 30 seconds.

To me that sounds like a Windows apologist saying the only security flaw in windows is failing to disconnect from the internet before turning the machine on, and forgetting to put it back in its safe after you're done using it.

Its perfectly acceptable that someone sneaking behind your pc while you're on the phone or smoking a cigarette can read your emails if you got firefox or your mail client to remember it. Thats a tradeoff between useability and security. Asking your password every time you want to open an email would be nuts. But  its not acceptable he can read your bank or other **passwords** with the same ease, especially since avoiding it would have no  usability tradeoff. You open Seahorse how many times per month?

---

### Post by benj1 on 2009-10-28
> **SeanBlader said:**
> The security flaw is failing to tell users that they need to lock their systems if they're AFK for more than 30 seconds.
i agree. unfortunately it isnt just linux that is guilty of that, and i would hope that all companies (where this would mainly be an issue) would communicate this to staff anyway, aswell as automatically locking the screen after a certain time.

---

### Post by P4man on 2009-10-28
> **benj1 said:**
> your example is flawed, the keyring is unlock when you log in there fore you have already provided your password, is it a security flaw to have a 'forgotten you password?' button on the desktop?  **pehaps** but the bigger security flaw would be failing to lock the system.


Which brings us right back to my original  argument: what then is the point of timing out sudo?  If the only security risk is failing to lock the PC, why do I have to reenter my password 100x per day? Logging in unlocks the keyring, why not unlock sudo permanently as well then ?  If I cant leave my pc alone for 2 minutes without someone being able to rob my bank account, then why on earth do I need to enter my password again and again to mount a drive or change the clock?

---

### Post by snkiz on 2009-10-28
> **benj1 said:**
> what was the question? "would you rather have a system where you can easily view passwords when logged in, but are secure when you aren't, or would you rather have a system that appears to be secure all the time, when in fact it never actually is?"
you make it sound as tough this small change would somehow cripple the existing sucerity.
> **benj1 said:**
> 
at the end of the day this thread is about whether this is a security flaw, it isnt. 
yes you could argue that people would prefer the illusion of security rather than actual security (most terminal cancer patients would probably prefer to be told they arent going to die), thats fine dont use ubuntu, which is the same answer to all "linux isnt windows" threads.
What illusion? the system's security doesn't depend on seahorse *I hope* all were talking about is the clear text display. Hell even pidgin don't show passwords. (I know their clear text in a file somewhere, but where's that file? most don't know.) 90% of criminals are stupid, and wouldn't be able to coax the passwords through other means, the other 10%... locking you screen wont save you.
> **benj1 said:**
> 
i for one prefer linux because it actually treats me like an intelligent adult instead of wrapping me up in cotton wool, patting me on the head and telling me everythings ok.

And this is what Microsoft got right.. dev's are not designers. You need to figure out what people need/want/expect then get the dev's to do it securely.

---

### Post by snkiz on 2009-10-28
No sudo isn't the same P4man thats for admin tasks and that little keyring in the conner is for policykit.

sudo=switch user do <command>

---

### Post by P4man on 2009-10-28
> **snkiz said:**
> 
And this is what Microsoft got right.. dev's are not designers. You need to figure out what people need/want/expect then get the dev's to do it securely.

If this were a flaw in windows microsoft would be vilified over it, and rightfully so. I think MS stopped storing passwords in clear text when they introduced windows95, perhaps 2000.

---

### Post by P4man on 2009-10-28
> **snkiz said:**
> No sudo isn't the same P4man thats for admin tasks and that little keyring in the conner is for policykit.

sudo=switch user do <command>

I know what sudo is. You're missing the point. 
Elevated sudo privildges expire after 15 minutes by default. What good does that do when the privilege of reading my bank account password never expires? So a hacker cant change my clock or install a keylogger to read my passwords, which is great except he doesnt even need to ;)

---

### Post by emarkay on 2009-10-28
> **DodgeV83 said:**
>  Seriously, no point in arguing, just wait for them to fix it.

I disagree - there is much resistance to "those paranoid porn users" as we are called behind our backs.  As much as "gee whiz" features and other fluff have been added, Ubuntu has migrated away from security as one of the  key concepts. 

IMHO , too many developers want "pretty" over "practicality". Just look  look at some of the comments made here and elsewhere regarding wasted resources ("Throbbers", anyone),  removal of configuration options and other "dumbing down" choices that don't address stability (another key) and these security concerns.

Remember, "dumbing it down" just make it a bit easier for a "dumb criminal" to accomplish their craft, and the crafty ones to get away with even more.

Keep applying pressure both here and through Launchpad to ensure that Communications Security is addressed, and that those that want or need COMSEC  (Federal or private) can achieve it "out of the box".

---

### Post by snkiz on 2009-10-28
Because you bank account number isn't in the system files and therefore not under the protection of sudo. if seahorse acted like policykit that would kinda defeat the purpose

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
> 
What illusion? the system's security doesn't depend on seahorse *I hope* all were talking about is the clear text display. Hell even pidgin don't show passwords. (I know their clear text in a file somewhere, but where's that file? most don't know.) 90% of criminals are stupid, and wouldn't be able to coax the passwords through other means, the other 10%... locking you screen wont save you.

system security depends on seahorse in as far as without it you either have unencrypted passwords or each app implementing their own passwords.
im aware pidgin doesnt encrypt passwords, why? first because the system isnt secure unless you lock it when you leave, plus the passwords for your messenger client by and large arent hugely important, although i personally would prefer to see it use seahorse.

@P4man sudo is used to temporarily give you admin privileges, if you permanently want those privileges log on as root, on a more practical point, how would you differentiate when you want to run something as user and when as root? as well as controlling which users have access to what.

---

### Post by benj1 on 2009-10-28
> **P4man said:**
> If this were a flaw in windows microsoft would be vilified over it, and rightfully so. I think MS stopped storing passwords in clear text when they introduced windows95, perhaps 2000.

windows has a completely different system of security, its comparing apples and oranges, anyway linux would be vilified if it was as secure as windows.

---

### Post by mcduck on 2009-10-28
> **P4man said:**
> I know what sudo is. You're missing the point. 
Elevated sudo privildges expire after 15 minutes by default. What good does that do when the privilege of reading my bank account password never expires? So a hacker cant change my clock or install a keylogger to read my passwords, which is great except he doesnt even need to ;)

So you just simply can't lock your session when you are not using it? It takes 3 seconds max to do, and protects not only your passwords, but also your files, and stops anybody from installing any malware to your user.

Really. 3 seconds max and the whole issue is solved and everyhting really is secure 8at least to the level it can be with physical access to the machine).

Same applies to using the Guest session.

It's like complaining that somebody might easily open your desktop drawer and read your documents when you yourself refuse to lock your front door when you are not at home. The real security issue is that your front door is open and all your belongings are available for anybody to take, yet you still complain that your desk drawer doesn't have a lock. :D

---

### Post by benj1 on 2009-10-28
> **mcduck said:**
> so you just simply can't lock your session when you are not using it? It takes 3 seconds max to do, and protects not only your passwords, but also your files, and stops anybody from installing any malware to your user.

Really. 3 seconds max and the whole issue is solved and everyhting really is secure 8at least to the level it can be with physical access to the machine).

Same applies to using the guest session.

It's like complaining that somebody might easily open your desktop drawer and read your documents when you yourself refuse to lock your front door when you are not at home. The real security issue is that your front door is open and all your belongings are available for anybody to take, yet you still complain that your desk drawer doesn't have a lock. :d

+100 :-)

---

### Post by snkiz on 2009-10-28
So not starting an MS flamewar here, I'm just trying to illustrate that MS PAYS people to find stuff like this and report to the developers to fix it. But here sometimes the community has its say, and sometimes a stubborn dev says "I know whats best, you don't like it fork it." Its the wrong attitude. I understand the seahorse dev point of view, and their right. But clearly some things work better in theory than in practice.

---

### Post by snkiz on 2009-10-28
why do liquor cabinets have locks then? You may need to secure yourself from someone already in the house.

---

### Post by Peter09 on 2009-10-28
Security should consist of layers

door lock->car alarm->steering wheel lock->ignition key->GPS system.

If you talk to many security people they will tell you that having only one layer of security is really not good enough, each layer will never be impregnable but each additional layer delays the perpetrator to the point where it may not be practical to continue.

So the argument is really - is a single layer of security good enough.

In my case my machines are split into two types - secure and insecure. My laptop - which I take out and about is insecure because I realise that it can be easily stolen or compromised.(theoretically someone could grab it while I was working on it) I do not keep personal information on it.

I have a machine at home which is secure, and Internet facing. I keep personal information on it which can be accessed from my laptop through an ssh connection. Until now I belived that if someone did a runner with my laptop they would not be able to get to my personal data quickly enough before I changed the passwords etc. Now I'm not so sure.

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
> why do liquor cabinets have locks then? You may need to secure yourself from someone already in the house.
that analogy would hold if you were the only person who would be expected to use your house, and if some one were to come and visit you could summon a house out of the ether for them to use. it that case then yes it would be silly to lock your cabinet, you would just lock your house when you left it.

---

### Post by mcduck on 2009-10-28
> **snkiz said:**
> why do liquor cabinets have locks then? You may need to secure yourself from someone already in the house.

I don't let people I can't trust to stay in my house when I'm not around.

I don't let people I can't trust to use my computer when I'm not around. And definitely not my own user account.

Both situations are solved in the same way, by locking the front door (or my computer/session) to keep such people away.

---

### Post by benj1 on 2009-10-28
> **Peter09 said:**
> Security should consist of layers

door lock->car alarm->steering wheel lock->ignition key->GPS system.

If you talk to many security people they will tell you that having only one layer of security is really not good enough, each layer will never be impregnable but each additional layer delays the perpetrator to the point where it may not be practical to continue.

So the argument is really - is a single layer of security good enough.

the system does have multiple layers of security user password, root password, there are many other levels you can implement, bios passwords, hard drive encryption, case locks,putting your pc in a safe.
what some are advocating here though is hiding the radio facia in the glove box and leaving the car unlocked.

---

### Post by snkiz on 2009-10-28
one word... kids

---

### Post by Peter09 on 2009-10-28
Not quite, root password is not in the loop as its not needed here, physical security is not valid if you want to use the machine, unless you want to talk about a secure room. Disk encryption is negated by the user password, a bios password would not be in the loop either so I think we are back to one layer?

---

### Post by mcduck on 2009-10-28
> **Peter09 said:**
> Not quite, root password is not in the loop as its not needed here, physical security is not valid if you want to use the machine, unless you want to talk about a secure room. Disk encryption is negated by the user password, a bios password would not be in the loop either so I think we are back to one layer?

locking the session?

---

### Post by chrisccoulson on 2009-10-28
> **P4man said:**
> If this were a flaw in windows microsoft would be vilified over it, and rightfully so. I think MS stopped storing passwords in clear text when they introduced windows95, perhaps 2000.

Since when were my passwords on Ubuntu stored in cleartext?

---

### Post by Peter09 on 2009-10-28
> locking the session

sorry but are we not back to one layer of security - the user password? If thats compromised?

---

### Post by chrisccoulson on 2009-10-28
> **Peter09 said:**
> sorry but are we not back to one layer of security - the user password? If thats compromised?

The user password is the same as the keyring password, so if the user account password is compromised, your stored secrets are also compromised whether the attacker is prompted for a password or not - so, it's *still* only one level

---

### Post by Peter09 on 2009-10-28
> The user password is the same as the keyring password, so if the user account password is compromised, your stored secrets are also compromised whether the attacker is prompted for a password or not
Correct - thats why stored passwords should be held just like your user password - never to be seen in clear text again.

---

### Post by benj1 on 2009-10-28
> **Peter09 said:**
> Not quite, root password is not in the loop as its not needed here, physical security is not valid if you want to use the machine, unless you want to talk about a secure room. Disk encryption is negated by the user password, a bios password would not be in the loop either so I think we are back to one layer?
ignition lock and gps wouldnt be needed to get access to the car, all of it would be useless if you put expanding foam in the alarm siren and put tin foil over the gps transmitter, we can trade flaws in each others analogies all day, the point is you said security depends on layers, i was pointing out linux does support and has multiple layers of security also when you leave your computer you lock it or log out, just the same as if you leave your car, you lock it.

> one word... kids
again the analogy doesnt hold, it is easy to support multiple accounts for multiple users, its not so easy to build a new house for each member of your family.

---

### Post by snkiz on 2009-10-28
The reality is that I have four family members using the same less than new hardware. It takes time to logout and back in, and guest sessions are buggy without the horsepower. Some times we share.

The passwords being the same is definitely an issue even more so considering your sudo password is the same so the argument applies system-wide

---

### Post by chrisccoulson on 2009-10-28
> **Peter09 said:**
> Correct - thats why stored passwords should be held just like your user password - never to be seen in clear text again.

So how would an application such as Empathy access your stored secrets then?

---

### Post by benj1 on 2009-10-28
> **Peter09 said:**
> Correct - thats why stored passwords should be held just like your user password - never to be seen in clear text again.

but thats just security through obscurity. if you have the user password you have all the other passwords anyway.

---

### Post by emarkay on 2009-10-28
Hey you are missing the point!

It's Ubuntu here that is the fault,** not** the user, the government, the criminal nor the geek!

Bickering amongst ourselves about concepts and opinions aas well as tossing related facts like grenades does **not** solve the problem.

Some simple things have been changed in Karmic and there is evidence that this trend will intensify, to make it "easy" and "fun".  Those  that use Linux for real work will either suffer the potential consequences or pay someone their hard-earned cash to secure the OS; maybe just  to the point it may have been in Jaunty.

Ubuntu developers,  the facts mentioned about the "security" flaws are real, not opinions.  Let us identify and address these.  Leave the "dog and pony shows" for the masses, but address these issues with professional seriousness.

---

### Post by Peter09 on 2009-10-28
> ignition lock and gps wouldnt be needed to get access to the car, all of it would be useless if you put expanding foam in the alarm siren and put tin foil over the gps transmitter, we can trade flaws in each others analogies all day, the point is you said security depends on layers, i was pointing out linux does support and has multiple layers of security also when you leave your computer you lock it or log out, just the same as if you leave your car, you lock it.

Firstly I was talking about stealing the car not gaining access, secondly as I said no one layer is invincible, each layer adds to the difficulty of stealing the car. In this case you would have to come well prepared.

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
> The reality is that I have four family members using the same less than new hardware. It takes time to logout and back in, and guest sessions are buggy without the horsepower. Some times we share.

The passwords being the same is definitely an issue even more so considering your sudo password is the same so the argument applies system-wide
well thats your choice to balance the risks, you trust they wont do anything in the same way you trust they wont rifle though your bank statements and sell your details on ebay.

sudo permissions are something you can modify, sudo can be removed entirely

---

### Post by snkiz on 2009-10-28
I wouldn't classify myself as being very secure, like I said we sometimes share. But I just realized if I was paranoid I'd never store passwords with seahorse or anything else for that matter. So the issue is somewhat moot IMO. It just boggles the mind, the complete disregard for personal security once you login that this thread has relieved.

---

### Post by benj1 on 2009-10-28
> **emarkay said:**
> Hey you are missing the point!

It's Ubuntu here that is the fault,** not** the user, the government, the criminal nor the geek!

we arent missing the point, the user has to take responsibility eventually, ubuntu could be impregnable, it still wouldnt be able to protect the user from themselves, thats why most malware is spread through trojans, and not flaws in the os. 

[QUOTE=peter09]
Firstly I was talking about stealing the car not gaining access, secondly as I said no one layer is invincible, each layer adds to the difficulty of stealing the car. In this case you would have to come well prepared.
[/QUOTE]
first you cant equate stealing and car to just getting access to passwords on an already logged in system, a closer analogy, as ive already posted would be hiding the radio facia in the glove box and leaving the door unlocked.
i agree that no one layer is invicible, but why ignore the much stronger layer of logging off for the inferior layer of hiding the password. i refer you back to my previous car analogy, lock the car, dont hide the radio.

---

### Post by snkiz on 2009-10-28
> **benj1 said:**
> well thats your choice to balance the risks, you trust they wont do anything in the same way you trust they wont rifle though your bank statements and sell your details on ebay.
You trust your teens with your credit card? Better yet not to rifle through your filesystem? I remember being young. ;)
> **benj1 said:**
> 
sudo permissions are something you can modify, sudo can be removed entirely
How? I'd love to make my sudo password different than my login

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
> I wouldn't classify myself as being very secure, like I said we sometimes share. But I just realized if I was paranoid I'd never store passwords with seahorse or anything else for that matter. So the issue is somewhat moot IMO. It just boggles the mind, the complete disregard for personal security once you login that this thread has relieved.

is it a complete disregard for security to assume you are the actual user once you have supplied your password. to my mind its more of a disregard for security to make you think the system is secure, when in fact it isnt.

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
> 
How? I'd love to make my sudo password different than my login

you may be able to i dont know, i was referring to changing permissions so only certain users can install apps for example, you can also completely remove sudo so that no one can use it, you would have to log in as root to do admin tho.

---

### Post by Triggerhapp on 2009-10-28
Once you've logged in, its up to you to look after the security of your passwords.

You (or anyone logged in as you) can read the ones you supply to your system to allow access to always.

You also have the option of using a different set of passwords which ask you to give another password just to see them (which happens to machines with automatic login, I believe?)

If you are unhappy with the assumption that once you have proved its you, it assumes it is you, then change the way it is set up.

Edit : Oh and asking for your password to see your collection of already unlocked passwords is only a dud barrier. The applications and any other application will still be able to get all your passwords as plain text from seahorse, unless you change the way it is configured.

---

### Post by snkiz on 2009-10-28
> **benj1 said:**
> is it a complete disregard for security to assume you are the actual user once you have supplied your password. to my mind its more of a disregard for security to make you think the system is secure, when in fact it isnt.

No one said Don't be upfront about what your doing. When you use synaptic the first time a box comes up to explain what it does, with a little check to never show again. Why not do the same for seahorse when you click the "show passwords button"

---

### Post by Peter09 on 2009-10-28
My analogy of stealing a car just shows how we use multiple layers of security to protect things from being stolen. In the car analogy, even if I leave the door open it is still not simple to steal the car.

---

### Post by snkiz on 2009-10-28
> **benj1 said:**
> you may be able to i dont know, i was referring to changing permissions so only certain users can install apps for example, you can also completely remove sudo so that no one can use it, you would have to log in as root to do admin tho.

That I was aware of. But throwing out A good program because of a small issue doesn't make a lot of sense. Just improve what is already pretty good. Isn't that what Ubuntu did with Debian?

---

### Post by Triggerhapp on 2009-10-28
Ok going with the car analogy.

You are ok with letting your friends into your car, but you dont want to give them the items that are important to you.

You let them in the back seat, or the passenger front seat, but not the driving seat right?

Ie/ log them in as them, or as guest, but not as you.

---

### Post by snkiz on 2009-10-28
no more like you let your friends in, your too drunk to drive but your mistress phone number is in the glove box. you'd rather your friend didn't see that.

---

### Post by Triggerhapp on 2009-10-28
well that's your fault for putting it in an easy to access area.

But that analogy more resembles putting a file you dont want friends to see in your home directory. They can see that over your shoulder should you let on you dont want them to see it.

On the other hand, they still cant drive off with your car, until you give them the keys. (The proof that it is you, in Ubuntus case)

---

### Post by snkiz on 2009-10-28
lol I was about to say the glove box has a lock but its the same key isn't it? Ubuntu isn't the only one with debatable issues.

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
> No one said Don't be upfront about what your doing. When you use synaptic the first time a box comes up to explain what it does, with a little check to never show again. Why not do the same for seahorse when you click the "show passwords button"

i dont understand, a message to say logout when leaving your computer or else every man and his dog will have access to all you passwords and confidential information"?

i would suggest just a message on installation would do the job better.

[QUOTE=peter09]
My analogy of stealing a car just shows how we use multiple layers of security to protect things from being stolen. In the car analogy, even if I leave the door open it is still not simple to steal the car. 
[/QUOTE]
i get the analogy and i agree with multiple layers of security a car is not a computer, anyway a closer analogy is if i dont password secure the bios its still not simple to get access to the users passwords. 
infact my computer is more secure because i have to input a password to install something, does your car require a key to remove the wipers?
now can we stop with the analogy mincing

---

### Post by Peter09 on 2009-10-28
> lol I was about to say the glove box has a lock but its the same key isn't it? Ubuntu isn't the only one with debatable issues.

This is still valid, it means that if I defeat the external security, by smashing the window, I then cannot just grab something and run, I now have to spend more time breaking open the glovebox (while the alarms sounding). - Risks are too high best not to bother, especially when I do not know what the value of the stuff in the box is.

---

### Post by snkiz on 2009-10-28
Ok how 'bout this: 
I used to have a yahoo account. I login check my email, play some games, its all good. But if I try to change any of my user info yahoo confirms my password to make sure its me doing it. Sounds like a reasonable security measure to me.

---

### Post by snkiz on 2009-10-28
One more thing before I go make dinner. If its Ubuntu's security policy for personal information to say once your logged in thats good enough. Then why when I open the "about me" applet to change my password, does the system ask me for my password?

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
> That I was aware of. But throwing out A good program because of a small issue doesn't make a lot of sense. Just improve what is already pretty good. Isn't that what Ubuntu did with Debian?

i wasnt advocating throwing it out, im saying if you have multiple people using one user name, but you dont want all users to be able to use sudo, uninstall it that use the root account for admin


[QUOTE=snkiz]
Ok how 'bout this:
I used to have a yahoo account. I login check my email, play some games, its all good. But if I try to change any of my user info yahoo confirms my password to make sure its me doing it. Sounds like a reasonable security measure to me.
[/QUOTE]
youre accessing it remotely, which introduces security problems, plus they cant make assumptions about your os which may be a single user system.

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
> One more thing before I go make dinner. If its Ubuntu's security policy for personal information to say once your logged in thats good enough. Then why when I open the "about me" applet to change my password, does the system ask me for my password?

perhaps its to prevent users not locking/logging out of their system getting knackered by someone sneeking up and changing the password.
more likely though is that changing passwords requires root privileges, so you are using the sudo password, not your own.

---

### Post by snkiz on 2009-10-28
> **benj1 said:**
> perhaps its to prevent users not locking/logging out of their system getting knackered by someone sneeking up and changing the password.
more likely thought is that changing passwords requires root privileges, so you are using the sudo password, not your own.
no just tried as an unprivileged user it asked me for my user password. and the same argument can be used for seahorse. thanks good night.

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
> no just tried as an unprivileged user it asked me for my user password. and the same argument can be used for seahorse. thanks good night.
an unprivileged user that cant use sudo?
the same arguement cant be used for seahorse because the if youre logged in the passwords are already decripted, you would just be hiding them.

---

### Post by humphreybc on 2009-10-28
Just an update, i've been talking with Adam Schreiber.

I replied to his email:

> 
I would hope that you take into consideration the opinions of the Ubuntu users. That's the over-ruling philosophy of Ubuntu, and if the users have something to say, the developers should listen.

If you do not have the time, then please pass this on to someone who does.

Benjamin


And he replied:

> 
If you would care to summarize the thread and/or file a bug report
and/or ask a question, I'd appreciate it.  That's a really long thread
at 14 pages.  I care, but I don't want to have to respond to each
point separately.  Also, please note, we're GNOME developers not
Ubuntu developers and while we try to be responsive to users and
reasonable to requests please remember that we're mainly volunteers
and haven't signed on to an "over-ruling philosophy of Ubuntu."

Cheers,

Adam


So, I did my best to summarize the thread for him:

> 
Okay, i'll do my best to try and summarize:

Basically, users are worried that passwords for empathy, wireless networks and other programs that use Seahorse to store passwords can be seen in clear text from less than four clicks of the mouse button from a desktop.

The argument for changing it is to change the location of Passwords/Encryption to Preferences, remove the checkbox to show passwords in clear text (after all, you should know your own passwords) or prompt for you to enter in your user password to view them in clear text. Also many people say that even Windows does not show MSN passwords in plain text from the main menu.

The argument for leaving it how it is, is that people should learn to lock their computers when leaving them for more than 30 seconds, and if they don't, they've got more to worry about than people seeing their passwords (ie, rm -rf commands, rootkit installers etc).

The debate continues with many saying 90% of people using your computer won't know how to install rootkits or run rm -rf commands, but with a bit of thoughtless rummaging, quite easily access your passwords. As one person points out, most criminals are stupid, so therefore an easy option to show passwords would be more relevant to them.

There are other arguments put forward, such as it is the users responsibility to make sure untrustworthy people don't have physical access to your computer. The counter of that is that people such as co-workers, your family, teenagers that you trust to access your computer might stumble across your passwords easily. Teenagers could buy things using credit card details, co-workers and friends could use this information against you in the future if there was ever a fall out.

Among all this, there are a lot of posts debating analogies, with a car being used as the main analogy. If someone has access to your car door key, then the game is over - this key also starts the car. This equals one level of security, which is advised against in the security world. I haven't read the analogy posts in detail, but as you can imagine, there are arguments against this idea too.

Cheers,
Benjamin


---

### Post by benj1 on 2009-10-28
i think you could safely have left the car analogies out, although i think this thread could have done without them too :p

---

### Post by humphreybc on 2009-10-28
> **benj1 said:**
> i think you could safely have left the car analogies out, although i think this thread could have done without them too :p

lol well he asked for a summary of the thread, so a summary of the thread is what I tried to deliver :P

---

### Post by DodgeV83 on 2009-10-28
> **Triggerhapp said:**
> Ok going with the car analogy.

You are ok with letting your friends into your car, but you dont want to give them the items that are important to you.

You let them in the back seat, or the passenger front seat, but not the driving seat right?

Ie/ log them in as them, or as guest, but not as you.

And we are expecting people who have no concept of what an OS is, to be able to differentiate that for themselves?

-------------------
I have clients who thought they had to buy a new memory card every time their digital camera got filled up.  

Who have pictures on their digital camera for years, because they don't know how to get them off.  

Who didn't know their printer of 5 years also had a scanner.  

Who complain about their printer "not working" when they're out of ink.  

Who say their internet isn't working, when it's not plugged in.  

Who can't for the life of them figure out how to configure their wireless router.  

Who don't know how to reset their password-less router when the internet is out.  

Who are college professors and didn't understand the "keygen" someone gave them to install a piece of software was illegal and likely malware ridden.

Who think as long as they don't download anything on the internet, they are "safe".

Who don't consider it a security risk when some USB software auto-installs every time they plug their USB drive to a new computer.

Who bring up in casual conversation "Yea I hate those spam e-mails, but I clicked on one once and it was really interesting!  Did you know you could get Viagra for a dollar?"

Who ask "Where's the any key?!"

In case anyone hasn't seen it, Google took to the streets of New York City and asked people a simple question: "What is a browser?"

[http://www.youtube.com/watch?v=o4MwTvtyrUQ](http://www.youtube.com/watch?v=o4MwTvtyrUQ)

--------------------

The cases above are not of user stupidity, they are characteristic of a typical computer user.  Try explaining to these people that having an unprotected PASSWORDS button in the main menu, not only isn't a security flaw, but actually makes them **safer**.

The Ubuntu "Sucks to be you. If you don't like it, go back to Windows and learn how to use a computer noob" response I'm getting here, is only solidifying the fact that this system is for a niche audience only and will never appeal to the mass-market in it's current form.

---

### Post by DodgeV83 on 2009-10-28
No one here is arguing that locking the session isn't safer.  There is an absolute agreement on that.  We are simply contending that simply because there is some hacker software somewhere that allows people to see my passwords, doesn't mean people want the functionality installed by default in the main menu.

---

### Post by benj1 on 2009-10-28
> **DodgeV83 said:**
> No one here is arguing that locking the session isn't safer.  There is an absolute agreement on that.  We are simply contending that simply because there is some hacker software somewhere that allows people to see my passwords, doesn't mean people want the functionality installed by default in the main menu.

its not hacker software from some leet script kiddie site, the funtionality is easily available, somewhere i posted a link to a script some time back, which was the fifth link from google, it uses gnome supplied python APIs.
i appreciate some people might not want it on their menu, but thats personal preference, and the good thing about linux is that anything can be removed, just modify the menu.

---

### Post by benj1 on 2009-10-28
> **DodgeV83 said:**
> 
Who think as long as they don't download anything on the internet, they are "safe".

they are as far as the internet is concerned

> 
The cases above are not of user stupidity, they are characteristic of a typical computer user.  Try explaining to these people that having an unprotected PASSWORDS button in the main menu, not only isn't a security flaw, but actually makes them **safer**.

The Ubuntu "Sucks to be you. If you don't like it, go back to Windows and learn how to use a computer noob" response I'm getting here, is only solidifying the fact that this system is for a niche audience only and will never appeal to the mass-market in it's current form.
the problem with these examples is that it proves that its impossible to protect users from themselves, no matter how secure we make the os they will always defeat it, it also means that we dont need to hide the menus because these users will never be able to find it anyway.

ps i dont subscribe to the stupid user point of view, just that if you make the passwords impossible for _them_ to see they will think its impossible for everyone to see it, if they know its easily viewable they (if theyre at all bothered about theyre data) will lock it.

pps nice video by the way :D

---

### Post by SeanBlader on 2009-10-28
[QUOTE=benj1]if they know its easily viewable they (if they're at all bothered about their data) will lock it.[/QUOTE]

This statement just goes to show how out of touch Linux developers are with actual users. There's a technical manager here at the medical device company where I work who has access to just about every system in the company who used to leave his computer on, and email open overnight for the first 6 months I was in his group. At one point I finally walked over to his computer and setup a screen saver password, he never noticed.

Showing passwords on the screen anywhere is pretty dumb.

---

### Post by benj1 on 2009-10-28
> **SeanBlader said:**
> This statement just goes to show how out of touch Linux developers are with actual users. There's a technical manager here at the medical device company where I work who has access to just about every system in the company who used to leave his computer on, and email open overnight for the first 6 months I was in his group. At one point I finally walked over to his computer and setup a screen saver password, he never noticed.

Showing passwords on the screen anywhere is pretty dumb.

well i wouldnt count myself as a linux developer but in this case:
1. the company should be doing something about about security, in these circumstances a password protected screensaver should be standard. thats the companies fault not any os developers fault.
2. appreciation of security issues is separate from securing an os, this manager obviously doesnt realise his data could be important, again not the os developer fault
3. if you were that way inclined, would it have been beyond your abilities to recover all of his unencrypted passwords? because with seahorse on ubuntu it wouldn't regardless of whether there was a menu entry or not. 

what is with the 'stupid user' strawmen, if theyre that stupid just send them an email saying youre from some government department, and just ask for the passwords.

---

### Post by SeanBlader on 2009-10-28
> **benj1 said:**
> what is with the 'stupid user' strawmen, if theyre that stupid just send them an email saying youre from some government department, and just ask for the passwords.

It's been shown that Linux as a standard likes to protect users from themselves, hence the default use of sudo to do any system administration tasks. Following that methodology then getting into a Passwords and Encryption application should also require the user to enter a password. I don't think it's necessary to require a password for approved applications to get into the system's keyring, but non-approved apps, should require a password. That way when it says "never ask again" I can really be certain that's what I want do to. So connecting from my local machine to the VPN once I'm logged in is something I'm okay with, but I'm not okay with giving my VPN access to anyone who happens to walk up to my system while I'm in the break room getting a coffee or whatever.

---

### Post by benj1 on 2009-10-28
> **SeanBlader said:**
> It's been shown that Linux as a standard likes to protect users from themselves, hence the default use of sudo to do any system administration tasks. Following that methodology then getting into a Passwords and Encryption application should also require the user to enter a password.

i would say the opposite, linux makes very little attempt to save users from them selves, sudo privileges are in place because linux is designed as a multiuser system, administrator privileges are in place to stop every user of a system being able to install and delete at will, in addition its bad practice to run as root partly because linux doesnt try to save you from yourself, try sudo rm -rf /* ,linux wont try to save you then.
ps dont try ;)

>  I don't think it's necessary to require a password for approved applications to get into the system's keyring, but non-approved apps, should require a password. That way when it says "never ask again" I can really be certain that's what I want do to. 

but that indicates your installing apps on your system that you dont trust, if that happens youve already lost most of the battle, in addition im not even sure it would be able to with withhold the password, your user password, and the encrypted password would have to be stored somewhere, in addition the encryption algorithm is open source so if a program needed to it could just decrypt the password itself.
> 
So connecting from my local machine to the VPN once I'm logged in is something I'm okay with, but I'm not okay with giving my VPN access to anyone who happens to walk up to my system while I'm in the break room getting a coffee or whatever.

how would hiding passwords help?
locking your screen would help.

---

### Post by SeanBlader on 2009-10-28
> **benj1 said:**
> but that indicates your installing apps on your system that you dont trust, if that happens youve already lost most of the battle, in addition im not even sure it would be able to with withhold the password, your user password, and the encrypted password would have to be stored somewhere, in addition the encryption algorithm is open source so if a program needed to it could just decrypt the password itself.

how would hiding passwords help?
locking your screen would help.

I will address all your points because they are invalid.

The program I/we apparently numerous users have installed on our systems that we don't trust is Seahorse. Perhaps you didn't read the rest of the thread, please do so before continuing.

Hiding passwords would keep them from being ON THE SCREEN. You know where people can read them, where potentially unauthorized people can read them. Maybe you missed the first post in the thread, it's a good one.

Sure locking your screen would help, but what happens when someone forgets? I don't believe I ever got an answer to that question.

We are covering things again, how can we help you understand?

---

### Post by snkiz on 2009-10-28
Ok so "stupid user" isn't the right phrase. None the less Coddling users like the one dodge listed is annoying and ruins the os for everyone. That is a bigger issue than just seahorse. I'll never understand why people think its acceptable to sit down with the kind of power a computer affords in this day and age without some basic education in how things work and how to protect yourself. You would hand over you car keys to someone who's never been taught how to drive. (I know the car again.) 

The argument that **if** people know their passwords are available to their desktop, they will lock the screen. Hinges on that **if**. I've been using Linux for four years and never noticed that. (Never needed to actually open seahorse before.)

The argument that obscuring the password in any form is a false sense of security. Whats wrong with a little blurb explaining that? Ubuntu does it for other apps.

The quit complaining and file a bug argument. certainly a bug should be filed, with Ubuntu and upstream. Supported by healthy debate witch this is. Ubuntu sees fit to change gnome apps to suit their needs all the time, notiy-osd isn't part of gnome. So Ubuntu can and should come up with a solution thats sane and addresses it communities concerns.

The way I see it Ubuntu is almost there, seahorse does ask permission just no confirmation. And we do have the tools like gconf. And policykit, witch can handle non-root permissions and IMO is way under used.

Here's my idea, create a sane list of default apps that can access seahorse. The ability to change that list through gconf, and permission checks through policykit for unexpected apps, changing info or **viewing** passwords. And finally come up with a unified personal security policy for the desktop as a whole. (See above [post 182]("http://ubuntuforums.org/showpost.php?p=8183511&postcount=182"); you need **your** password to change your password and about me does not display clear text.)

I saw the email to the gnome dev's (Nice btw.)Has a bug report been started yet? if so post the link please.

---

### Post by humphreybc on 2009-10-28
Well, the first of the negative press has started. Joey-Elijah Alexithymia, The maintainer of the popular [omgubuntu blog]("omgubuntu.co.uk") is alarmed at this flaw and has made a blog post about it which you can read [here.]("http://www.omgubuntu.co.uk/2009/10/security-issue-in-gnome-lets-anyone-see.html")

Hopefully, with some negative press we can force the developers to change this, as much as I hate seeing negative press about Ubuntu, if the developers are going to be stubborn and not listen to the user community, I see no other option.

---

### Post by snkiz on 2009-10-28
I was thinking about that but wanted to give them a chance to slap it with a won't fix tag. No bug report?

---

### Post by benj1 on 2009-10-28
> **SeanBlader said:**
> I will address all your points because they are invalid.

The program I/we apparently numerous users have installed on our systems that we don't trust is Seahorse. Perhaps you didn't read the rest of the thread, please do so before continuing.

Hiding passwords would keep them from being ON THE SCREEN. You know where people can read them, where potentially unauthorized people can read them. Maybe you missed the first post in the thread, it's a good one.

apologies, i took your post to mean that you were advocating asking a users permission to use seahorse for a newly installed app to protect the existing passwords within seahorse from potential malware, rather than protecting the newly installed apps password from being displayed in the menu. 

> 
Sure locking your screen would help, but what happens when someone forgets? I don't believe I ever got an answer to that question.

We are covering things again, how can we help you understand?

i understand i just obviously take a different view to you. to answer your question yes if you dont lock your screen someone will be able to use your password and assuming they know where to look will easily be able to get your password.
although even if the menu wasnt there it would be *mildly* harder but take just as long (with a script) to get all the passwords, plus they still have full access to your system, so that would be autologon to what ever sites you have passwords stored for, all your non password data, plus rm -rf ~ can be quite effective.

and it still doesnt answer the other what ifs, what if the user sets his wallpaper and screensaver to display is username and password, what if he posts them on this forum, so if his hard disk fails he still has access to them, etc etc etc.
surely a better way would be to educate said user that his passwords arent safe unless his pc is locked.

---

### Post by Keyper7 on 2009-10-28
> **the.lost.one said:**
> If you think any security measure is impossible to break (...)

I never said that, so everything you said after is irrelevant.

> **SeanBlader said:**
> Sure locking your screen would help, but what happens when someone forgets?

What *does* happen I don't know. What *might* happen is something bad, regardless of seahorse behavior, as I mentioned before:

> **Keyper7 said:**
> Opening a terminal and doing a "rm -rf ~" is faster and allows a much shorter reaction time than opening the keyring manager. And it's probably far more dangerous: the amount of people who has so-sensitive-that-my-world-will-explode-if-people-read-it information is probably smaller than the amount of people who makes regular backups of their home directory.

---

### Post by humphreybc on 2009-10-28
> **snkiz said:**
> I was thinking about that but wanted to give them a chance to slap it with a won't fix tag. No bug report?

There is already a [bug report]("https://bugs.launchpad.net/seahorse/+bug/189774") on Launchpad, dated August last year. This problem has been around since the release of Hardy, and nothing's been done about it.

I found [this thread here,]("http://ubuntuforums.org/showthread.php?t=1075456") looks like this isn't an entirely new subject - but the first time it's been discussed this much.

---

### Post by snkiz on 2009-10-28
Ok found it [https://bugs.launchpad.net/seahorse/+bug/189774]("https://bugs.launchpad.net/seahorse/+bug/189774")
man I hate searching bugs though

---

### Post by Keyper7 on 2009-10-28
There's no point in complaining that nothing's been made about bug reports filed against [conscious design decisions](http://live.gnome.org/GnomeKeyring/SecurityPhilosophy).

---

### Post by humphreybc on 2009-10-28
An update for those of you not following the seahorse mailing list:

Note, *Me in italics,* Adam Schreiber (Seahorse dev) in normal font.

> 
Aside: Taking this back on the list as I must have hit reply instead
of reply all.  The interim emails are below for those playing along at
home.

[i]Okay, i'll do my best to try and summarize:
Basically, users are worried that passwords for empathy, wireless networks and other programs that use Seahorse to store passwords can be seen in clear text from less than four clicks of the mouse button from a desktop.[/i]

Technically, the passwords and secrets are stored in gnome-keyring, seahorse is just a manager/viewer.

*The argument for changing it is to change the location of Passwords/Encryption to Preferences, remove the checkbox to show passwords in clear text (after all, you should know your own passwords) or prompt for you to enter in your user password to view them in clear text.*

I think we've addressed prompting for the password before making it visible before but there's no really good way to "prompt" and check before displaying it.  We have to work within the gnome-keyring API.

[i]Also many people say that even Windows does not show MSN passwords in plain text from the main menu.
The argument for leaving it how it is, is that people should learn to lock their computers when leaving them for more than 30 seconds, and if they don't, they've got more to worry about than people seeing their passwords (ie, rm -rf commands, rootkit installers etc). 
The debate continues with people saying 90% of people using your computer won't know how to install rootkits or run rm -rf commands, but with a bit of thoughtless rummaging, quite easily access your passwords. As one person points out, most criminals are stupid, so therefore an easy option to show passwords would be more relevant to them.[/i]

I think our current approach is consistent with the security model I linked previously.  We don't want to give anyone the false impression that their data is more secure than it is.  Lock your screen and the key ring's locked, unlock your screen and it's unlocked.  If your screen is unlocked, they can just copy your keyring file and crack it at their leisure anyway.  You have a secure user password right?

[i]
There are other arguments put forward by people, such as it is the users responsibility to make sure untrusty worthy people don't have physical access to your computer. The counter of that is that people such as co-workers, your family, teenagers that you trust to access your computer might stumble across your passwords easily. Teenagers could buy things using credit card details, co-workers and friends could use this information against you in the future if there was ever a fall out.
Among all this, there are a lot of posts debating analogies, with a car being used as the main analogy. If someone has access to your car door key, then the game is over - this key also starts the car. This equals one level of security, which is advised against in the security world. I haven't read the analogy posts in detail, but as you can imagine, there are arguments against this idea too.[/i]

It all comes down to an opinion about consistency and trade-offs between usability and security. I agree with Stef on this one.  These are not new concerns and that's why we've discussed it in the past and posted an explanation as to our thought process.  I'd like to remind everyone that the problem of password's in the open is not specific to seahorse.  All someone with access to your user session and the ability to run a program would need to do is load a program and give it permission to query each secret on the keyring.  Without the architecture of gnome-keyring changing there's not much to do on this front and as the security philosophy indicates, some things in Linux and the desktop in general would have to change for that to happen.

Cheers,

Adam


And, here's my reply:

> 
That's fair enough, but I still think you're missing the point and not looking at it from an everyday user point of view. We're not asking for protection against people who can " load a program and give it permission to query each secret on the keyring" and then "copy your keyring file and crack it at their leisure." If the average Ubuntu user knew that there were guys out there trying to hack into their computer this way, i'm sure they would lock their computer.

We're trying to ask for measures to be put in place so that people who otherwise wouldn't go looking for your passwords might stumble across them in clear text out of plain curiosity.

Either way you look at it, it's still not acceptable to be able to view passwords in clear text this easily, and i'm sure something can be done to at least make it less obvious. Even a simple change of location to the Preferences menu would be a step in the right direction.

Cheers,
Benjamin


---

### Post by humphreybc on 2009-10-28
> **Keyper7 said:**
> Sigh...

I'll repeat it again: filing bug reports against [conscious design decisions](http://live.gnome.org/GnomeKeyring/SecurityPhilosophy) won't get you anywhere.

Hence why no one here has filed a bug, only linked to an existing one from last year.

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
>  And finally come up with a unified personal security policy for the desktop as a whole. (See above [post 182]("http://ubuntuforums.org/showpost.php?p=8183511&postcount=182"); you need **your** password to change your password and about me does not display clear text.)

without sudo permissions?

considering the only person on my system that has write permissions on the password files is root, you would obviously need to supply a password to modify it, although excluding that i hope you would agree you master password is an order of magnitude more important that any other password or anything else you may choose to store on the system

---

### Post by snkiz on 2009-10-28
> **Keyper7 said:**
> Sigh...

I'll repeat it again: filing bug reports against [conscious design decisions](http://live.gnome.org/GnomeKeyring/SecurityPhilosophy) won't get you anywhere.
I beg to differ, doob(Gnome guy) asked for one. And thats what the "wish list" tag is for. The mailing list is where you argue your point. the bug report informs the community there is a usability issue. (even if its by design.)

---

### Post by snkiz on 2009-10-28
You don't understand how policykit works. It **has** sudo permission. and grants access according to the rules set. Open about me or polkit and see for yourself.

and agreed the Master pass shouldn't even be on the system in the clear. EVER.

---

### Post by Keyper7 on 2009-10-28
> **humphreybc said:**
> Hence why no one here has filed a bug, only linked to an existing one from last year.

Yep, I edited my original post to:

> **Keyper7 said:**
> There's no point in complaining that nothing's been made about bug reports filed against [conscious design decisions](http://live.gnome.org/GnomeKeyring/SecurityPhilosophy).

> **snkiz said:**
> I beg to differ, doob(Gnome guy) asked for one. And thats what the "wish list" tag is for. The mailing list is where you argue your point. the bug report informs the community there is a usability issue. (even if its by design.)

"I disagree with the design" is not the same as "There is an issue with the design".

---

### Post by novafluxx on 2009-10-28
Thats right folks, blame gnome not seahorse or Ubuntu!

---

### Post by snkiz on 2009-10-28
> **Keyper7 said:**
> Yep, I edited my original post to:





"I disagree with the design" is not the same as "There is an issue with the design".

If you disagree that means you have an issue.

---

### Post by humphreybc on 2009-10-28
For those of you following along, I just edited my original post at the start of the thread to contain all the relevant links in one place... should make life a bit easier :)

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
> You don't understand how policykit works. It **has** sudo permission. and grants access according to the rules set. Open about me or polkit and see for yourself.

and agreed the Master pass shouldn't even be on the system in the clear. EVER.

ok i get ya, didnt realise it used policykit. although i think it would still be consistent to maintain the password for changing the password, because it is an administrative task, in line with using sudo for adminitrative tasks.

@humphreybc
thanks for posting the reply

---

### Post by Keyper7 on 2009-10-28
> **snkiz said:**
> If **you** disagree that means **you** have an issue.

The keyword here is "you".

Bugs are facts, not opinions.

---

### Post by benj1 on 2009-10-28
> **snkiz said:**
> If you disagree that means you have an issue.

"i disagree with the design" indicates you have a fundamental problem with the design, ie you disagree with seahorse showing passwords.

"There is an issue with the design" indicates that you think the design is fundamentally sound, but it could do with improvement, or has a bug.

---

### Post by snkiz on 2009-10-28
> **Keyper7 said:**
> The keyword here is "you".

Bugs are facts, not opinions.

Bugs are a deviation from expected or intended bhaviour, that by its very nature is subjective. IMO I expect the keeper of my passwords not to give them up without more than a simple please. hence its a bug.

---

### Post by DodgeV83 on 2009-10-28
> **snkiz said:**
> The argument that **if** people know their passwords are available to their desktop, they will lock the screen. Hinges on that **if**. I've been using Linux for four years and never noticed that. (Never needed to actually open seahorse before.)

Exactly!  I asked this earlier and never got a response from most of the people here:

> Here is the big thing people seem to be missing: Making it easy to view passwords doesn't make your program more secure! A raise of hands: How many people here knew Pidgin stored passwords in plain text when first installing? How many people knew Ubuntu allowed anyone to see all stored passwords in 5 seconds of clicking from the main menu?

**If users aren't aware of these issues, you are only making them less secure.**

If the people here don't know about it, what chance do the normal Ubuntu users have?

---

### Post by Keyper7 on 2009-10-28
> **snkiz said:**
> Bugs are a deviation from expected or intended bhaviour, that by its very nature is subjective.

Bugs are a deviation from expected or intended behavior **regardless of personal opinions**, which is **not** subjective.

> **snkiz said:**
> **IMO** I expect the keeper of my passwords not to give them up without more than a simple please. hence its a bug.

Keyword (actually, keyexpression) here is "IMO". This thread proves that your opinion is not an unanimity. Hence, the place to voice your thoughts is the mailing list, not a bug report.

---

### Post by humphreybc on 2009-10-28
Could we keep the thread on-topic? It's starting to waver a bit into the definition of a bug.

Also, I sent a PM to one of the forum moderators asking if he could relocate this thread to somewhere else so the discussion can continue even when the Karmic Testing Forum dies tomorrow. So, if it's disappeared tomorrow, then you'll know what happened :P

---

### Post by Keyper7 on 2009-10-28
> **humphreybc said:**
> Could we keep the thread on-topic? It's starting to waver a bit into the definition of a bug.

Which is **very** relevant to the discussion, since it's related to the fact that people are asking to "fix" a conscious design decision.

---

### Post by humphreybc on 2009-10-28
> **Keyper7 said:**
> Which is **very** relevant to the discussion, since it's related to the fact that people are asking to "fix" a conscious design decision.

Alright then, fair enough. Perhaps instead of a bug on launchpad, an idea should be filed on Brainstorm...

---

### Post by Keyper7 on 2009-10-28
> **humphreybc said:**
> Alright then, fair enough. Perhaps instead of a bug on launchpad, an idea should be filed on Brainstorm...

Brainstorm is not exactly an optimal place for discussions, either. The best course of action is to discuss this on the mailing list, because the devs themselves will read and reply.

---

### Post by cariboo on 2009-10-28
Instead of pm'ing one of us, use the report button, that way it will be seen sooner and acted upon.

This thread has been moved to the security forum.

---

### Post by benj1 on 2009-10-28
> **humphreybc said:**
> Alright then, fair enough. Perhaps instead of a bug on launchpad, an idea should be filed on Brainstorm...

you could do but not making users feel safer than they actually are is a pretty central design decision to the whole linux ecosystem.

i do agree its different to the windows approach of wrapping everything up in binary so the user *thinks* its secure, and it can take a bit of time to get your head around, it the same with alot of other areas of linux. 

Is it wrong? well linux has shown to be more secure than windows in general, plus i personally would like to know where i stand, if somethings secure, i would like to know it actually is secure, rather than just appearing to be secure, plus the nature of open source means we cant hide behind glorified rot13 encryption, in the same way that windows can.
Could communicating all of this to users be improved?, probably yes, especially in ubuntu which aims to attract new users, but never forget you will never, ever be able to save users from themselves, no matter how many confirmation boxes etc you put in, they will still be able to mess the system up. the answer to that is more education, not more confirmation boxes

---

### Post by humphreybc on 2009-10-28
Here's the brainstorm idea.

Click on the link below, show your support by adding a comment, or propose your solution to the problem.

[[IMG]http://brainstorm.ubuntu.com/idea/22120/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22120/)

---

### Post by DodgeV83 on 2009-10-29
As I said earlier, like the Gnome/KDE .desktop flaw, this won't get fixed without sufficient negative press on the subject.

Here is the first article on it:

[http://www.omgubuntu.co.uk/2009/10/security-issue-in-gnome-lets-anyone-see.html](http://www.omgubuntu.co.uk/2009/10/security-issue-in-gnome-lets-anyone-see.html)

It has just been dugg:

[http://digg.com/linux_unix/OMG_UBUNTU_Gnome_Lets_Anyone_See_Your_Passwords_GMAIL](http://digg.com/linux_unix/OMG_UBUNTU_Gnome_Lets_Anyone_See_Your_Passwords_GMAIL)

:popcorn:

---

### Post by sgosnell on 2009-10-29
The only passwords I have seahorse manage, or Firefox remember, are those for internet sites I don't care about.  My bank login, my email login, and anything else that is important to me simply isn't stored anywhere except in my password safe.  If you're ignorant enough to have your bank password stored in seahorse, or anywhere in Windows, then you deserve what you get.  Who cares if the password is visible, if having the keyring remember it means anyone who has access to your computer can log in to any site it has the password for, automatically?  With your bank password stored, anyone can just log in to the account without bothering to look for the password, encrypted or not.  It's convenient, of course, but it's not secure, even if the passwords are encrypted, and encrypting them will only give the illusion of security, because it's not necessary to see them.  

There is a lot of knee-jerk reaction to things lots of posters just don't understand.

---

### Post by michaelzap on 2009-10-29
> **sgosnell said:**
> The only passwords I have seahorse manage, or Firefox remember, are those for internet sites I don't care about...If you're ignorant enough to have your bank password stored in seahorse, or anywhere in Windows, then you deserve what you get...There is a lot of knee-jerk reaction to things lots of posters just don't understand.

I'll tell you what I don't understand: People who start off a comment saying that they don't even use the application being discussed, follow that by blaming people who do for whatever happens to them, and then finish by generically decrying the ignorance of the masses without having ever shared any useful knowledge.

---

### Post by DodgeV83 on 2009-10-29
> **sgosnell said:**
> The only passwords I have seahorse manage, or Firefox remember, are those for internet sites I don't care about.  My bank login, my email login, and anything else that is important to me simply isn't stored anywhere except in my password safe.  If you're ignorant enough to have your bank password stored in seahorse, or anywhere in Windows, then you deserve what you get.  Who cares if the password is visible, if having the keyring remember it means anyone who has access to your computer can log in to any site it has the password for, automatically?  With your bank password stored, anyone can just log in to the account without bothering to look for the password, encrypted or not.  It's convenient, of course, but it's not secure, even if the passwords are encrypted, and encrypting them will only give the illusion of security, because it's not necessary to see them.  

There is a lot of knee-jerk reaction to things lots of posters just don't understand.

Yea, I can tell you don't use the software, because you don't store your bank password directly into seahorse.  One way to get it, for example:

Seahorse integrates with IM clients who stores your Gmail...etc passwords and places them in the Main Menu (unknowingly to the standard user).

---

### Post by ElSlunko on 2009-10-29
Step 6 and step 1 are contradictory. Step 1 states enter password and step 6 you never enter a password throughout this procedure.

---

### Post by snkiz on 2009-10-29
All right I read the bug reports, and the security philosophy. This is what I have gathered from that.

1. Everyone on both sides of the fence agree the current state of the keyring (and by extension seahorse.) is not good.
2. Rather than shilling people into thinking they are secure, it preferable to teach the user good practices. Except the end user isn't taught the lesson unless its the hard way.
3. The solution is way more complicated than the problem. Package A needs package B to do this to package C to get everything to work in a truly secure fashion. So the answer for now is to do nothing.
4. Ubuntu is dependent on upstream to find a solution.
5. The dev's have a solution (very similar to what I suggested.) but due to point 3 are passing the buck between the affected packages.

In summary Gnome has admitted this is a flaw, and therefore a bug. But they can't fix it (Or don't want to.) even though other user sensitive applications in Gnome do not behave this way. The dev's believe that the same users who they say can't reasonably answer the question "Do you want network-manager to to have your wep key?" are supposed to just know without being told, that they need to lock their session to secure the keyring. And Ubuntu is only interested in innovations that are flashy and can grab headlines like notify-osd.

Agree, disagree, flame me, Whatever. The point is as a new user or worse yet a migrating user none of this is inherent knowledge. No one is doing anything to inform the user. All the while there the program sits, in the main menu, unprotected.

---

### Post by humphreybc on 2009-10-29
> **ElSlunko said:**
> Step 6 and step 1 are contradictory. Step 1 states enter password and step 6 you never enter a password throughout this procedure.

The first step is to log out and log back in, to make sure that you haven't inadvertently unlocked the keyring already.

Technically, the "procedure" doesn't start till step 2. The first step is just to make sure that everyone starts from the same place.

---

### Post by ElSlunko on 2009-10-29
> **humphreybc said:**
> The first step is to log out and log back in, to make sure that you haven't inadvertently unlocked the keyring already.

Technically, the "procedure" doesn't start till step 2. The first step is just to make sure that everyone starts from the same place.

For your arguments sake, yes. However you have to log in with the password anyways. When you log in the keyring gets unlocked because you typed your password in to log in. This makes your PC unsecure for 15 minutes. Logging in should not unlock this IMO.

Try your steps again, however enable auto-login for your account and open up the passwords application and see if it prompts you for a password then.

I'm not saying the current method is best, I'm just trying to make sure all the details of what is going on is apparent to anyone viewing this thread. When you type your password to log in it unlocks the keyring for the temporary duration. If you have auto-login, you'll be prompted for your first attempt at trying to run something that requires the keyring.

---

### Post by ad_267 on 2009-10-29
I think that logging in should unlock the password.

I set my parents computer to log in automatically, but then my mum complained that Evolution was "broken" because it was asking for the keyring password. The keyring isn't something that a lot of users understand.

---

### Post by ElSlunko on 2009-10-29
When you log out, and **log in** you inadvertenly unlock the keyring.

---

### Post by ElSlunko on 2009-10-29
My head is just exploding with the fact that you guys don't realize it either. I first noticed this behaviour when I set empathy to auto launch on login. When I had auto-login it would prompt me for my password as soon as the auto-login got to my desktop.

Since I reverted back to having to manually log in on boot and when I entered my password I was no longer prompted because the manual log in unlocked my keyring (and keeps it unlocked for the temporary amount of time it would unlock it if you had auto-login enabled anyways).

---

### Post by ElSlunko on 2009-10-29
Enter your keyring for synaptic and walk away. Go make a sammich or catch that TV show you like. After the allotted time (15 minutes I'm assuming honestly I'm not sure what the time-out is) and try to install something. You'll be prompted again. The timeout on login is a bad thing but the time out afterwards is a decent implementation.

A better one would be to have time outs coupled with closing the keyring when an application is closed.

---

### Post by DodgeV83 on 2009-10-29
> **ElSlunko said:**
> Enter your keyring for synaptic and walk away. Go make a sammich or catch that TV show you like. After the allotted time (15 minutes I'm assuming honestly I'm not sure what the time-out is) and try to install something. You'll be prompted again. The timeout on login is a bad thing but the time out afterwards is a decent implementation.

A better one would be to have time outs coupled with closing the keyring when an application is closed.

Unfortunately, the keyring time-out does not apply to the PASSWORDS button in the main menu (seahorse).

To test it, login to your machine and walk away for 15+ minutes.  Shoot walk away for an hour if you'd like :)  When you return, your passwords will still be accessible from the main menu without entering your password again.

---

### Post by ElSlunko on 2009-10-29
So the solution "seems" simple (I'm speaking from a noob-like perspective) in that the keyring should apply to the menu button (seahorse). I see now! Thanks for explaining.

---

### Post by mcduck on 2009-10-29
> **ElSlunko said:**
> Enter your keyring for synaptic and walk away. Go make a sammich or catch that TV show you like. After the allotted time (15 minutes I'm assuming honestly I'm not sure what the time-out is) and try to install something. You'll be prompted again. The timeout on login is a bad thing but the time out afterwards is a decent implementation.

A better one would be to have time outs coupled with closing the keyring when an application is closed.

You are confusing several different passwords.

Synaptic has nothing to do with the keyring. The password you give to start Synaptic and other administration tasks is your user password, used for sudo/policykit, not keyring password.

The 15-minute timeout applies for _sudo password_ and policykit passwords, not for keyring (which, one unlocked, stays unlocked until you lock it manually, or log out). There is no timeout on log in. Keyring has no timeout, and neither has login password (why would it, you already logged in and are not going to do it again once already logged in).

---

### Post by P4man on 2009-10-29
> **sgosnell said:**
> T  Who cares if the password is visible, if having the keyring remember it means anyone who has access to your computer can log in to any site it has the password for, automatically? 


Its a huge difference. Having the password means the intruder has permanent access to these accounts (until you change the pw, but we all know how often we change our pw for our email and the like) and not just for the 5 min you went for a smoke. Its one thing someone can sit behind my pc and see my empathy contacts or even chat history, its something entirely else if he can log in at night pretending to be me.

Then there is the fact many people use the same password for more than one service. Most people probably only have 2 or 3 passwords and use them for a dozen services.

Sure, blame the user for reusing his pw and not changing it every 3 days, but thats not an excuse for this flaw. I dont know who to blame for this, whether it is seahorse developers, gnome or ubuntu. Probably it IS a the result of some fundamental issue, but the result is downright stupid and blaming the user doesn't change that. Its really like blaming the user for all of windows security holes "you shouldnt open attachements you cant trust, you should run a firewall, you should not log in as administrator, you should apply all patches every day"  yada yada yada. All true but no excuse.

---

### Post by revanb on 2009-10-29
The fact remains...When you are logged in, you are assumed to be sitting in front of the screen. You should set your screensaver to say 5min or even shorter and set it to lock your account when it is activated should you forget to lock your screen or log out.

Even the home folder encryption option will mean nothing if you leave your logged in computer unattended.

So the only thing the developers of seahorse and Ubuntu are maybe quilty of is not explaining this issue  to all users straight away with a nice message up front!

Should your car confirm your identity every time you stop at an intersection? Or just after you've locked it?

(Almost all websites assume you and only you have access to your email...So even if the passwords in seahorse where not visible in your logged in account, anybody having access to your logged in account could use the "Forgot password" option on most website which will have them send a confirmation email to your inbox with a clickable link wich would reset the passwords anyway!)

---

### Post by P4man on 2009-10-29
> **revanb said:**
> The fact remains...When you are logged in, you are assumed to be sitting in front of the screen. You should set your screensaver to say 5min or even shorter and set it to lock your account when it is activated should you forget to lock your screen or log out.

Then why oh why does sudo have a time out ?

> Should your car confirm your identity every time you stop at an intersection? Or just after you've locked it?

Lets not lose ourselves in endless and pointless analogies. 

> (Almost all websites assume you and only you have access to your email...So even if the passwords in seahorse where not visible in your logged in account, anybody having access to your logged in account could use the "Forgot password" option on most website which will have them send a confirmation email to your inbox with a clickable link wich would reset the passwords anyway!)

Most websites will NOT email you the password for all of the above reasons, they will send you a link that lets you **reset** the password (and often on top of that requiring additional proof of identity like answering some secret question). Thats a huge difference. You might be able to change my password but at least I would be instantly informed someone was stealing my identity.

---

### Post by snkiz on 2009-10-29
Lets not confuse the issue even more than it is. Ubuntu has two security policies. One for the system using sudo and policykit, and One for personal data using the keyring. Its unfortunate that your sudo password is the same as your login password. Its only enforces the confusion. login with an unprivileged user and its become clear where the line is.

---

### Post by revanb on 2009-10-29
Sudo times out because you are not root. While it is active you are working as root. If you don't know yet why this is not a good idea then you don't seem to know much about security. 

Just putting up mindless password prompts everywhere doesn't mean you have good security. Maybe you should keep your computer in a locked room and switch it off. Then it will almost be secure.

---

### Post by P4man on 2009-10-29
> **snkiz said:**
> Lets not confuse the issue even more than it is. Ubuntu has two security policies. One for the system using sudo and policykit, and One for personal data using the keyring.

Point is, if you follow revanb's logic then both make different assumptions about who is behind the keyboard. That makes a lot of sense. 
not.

Either the sudo policy is nonsensical that it times out, since it should assume its the user who is (still) behind the kb, or seahorse should not make that assumption by showing passwords without renewed authentication.

---

### Post by P4man on 2009-10-29
> **revanb said:**
> Sudo times out because you are not root. 

No. The reason i have to run sudo is because im not root. That doesnt explain why it times out. Once I elevated my privileges not everything I run runs as root! Only tasks I decide to run as root.

> While it is active you are working as root. If you don't know yet why this is not a good idea then you don't seem to know much about security. 

No! if I run something as sudo, that doesnt mean all other actions I take are as root! I just dont have to prove my identity for 15 minutes, I **still** need to type "sudo" to run something as root. Perhaps you are the one who doesnt quite understand

edit: let me rephrase it. Sudo *authentication* times out after 15 minutes. If not because its unsafe to assume the identity of the person behind the keyboard, then why? It could safely never expire, while still requiring me to either type in sudo to run root tasks or confirm apps to run as root. It would just not require a password, since it can assume its the user behind the kb. (Ironically thats how windows does it). You understand the difference now? Sudo doesnt assmue, seahorse does. One of them makes no sense.

---

### Post by Keyper7 on 2009-10-29
> **DodgeV83 said:**
> As I said earlier, like the Gnome/KDE .desktop flaw, this won't get fixed without sufficient negative press on the subject.
Here is the first article on it:

[http://www.omgubuntu.co.uk/2009/10/security-issue-in-gnome-lets-anyone-see.html](http://www.omgubuntu.co.uk/2009/10/security-issue-in-gnome-lets-anyone-see.html)

It has just been dugg:

[http://digg.com/linux_unix/OMG_UBUNTU_Gnome_Lets_Anyone_See_Your_Passwords_GMAIL](http://digg.com/linux_unix/OMG_UBUNTU_Gnome_Lets_Anyone_See_Your_Passwords_GMAIL)

:popcorn:

The article is sensationalist and misleading. Bullying the developers because you can't convince them through arguments is not the right course of action.

Luckily, several comments in the blog and the first comment in Digg seem to have noticed the sensationalism.

---

### Post by revanb on 2009-10-29
Like I said in my initial post..If you want you user account to time out set your screensaver to lock your account. End of argument.

If sudo didn't time out it leaves large windows of opportunity for scripts ( while you are in front of your screen ) to destroy your system in many ways. The only reason it has the 15min period is because it assumes you are the same person behind the keyboard so that you don't have to type in your password with every command you issue. (And you may run a script with hundreds of commands)

The issue is entirely different and entire clear.

---

### Post by P4man on 2009-10-29
> **revanb said:**
> Like I said in my initial post..If you want you user account to time out set your screensaver to lock your account. End of argument.


A locked screen also protects against sudo abuse. You're arguing in circles.

> If sudo didn't time out it leaves large windows of opportunity for scripts ( while you are in front of your screen ) to destroy your system in many ways. 

Of course not! Only tasks I decide to run as root would run as root even if *sudo authentication* never runs out.

> The only reason it has the 15min period is because i**t assumes you are the same person behind the keyboard** so that you don't have to type in your password with every command you issue. (And you may run a script with hundreds of commands)

It assumes so for 15 minutes. Then it no longer makes that assumption. You're still not getting it. 5 seconds after doing anything as root I will again need to type SUDO to run another task as root. I just dont have to prove my identity again, i still have to elevate my privileges. Never timing out sudo is absolutely not the same as running a root account, and would only have ONE security risk: that is if you are no longer the person behind the keyboard.

---

### Post by mcduck on 2009-10-29
Does it really come as this big surprise to people that if you leave your desktop unattended and unlocked at hands of people you can't trust your personal information might be compromised? :D

Still, everybody complaining about the keyring seems to ignore the fact that not locking your session leaves _all_ your files and information vulnerable, and completely compromises your user's security (since malware such as keyloggers can be easily installed to that user account).

If you are afraid that you don't remember to lock the session yourself, you can set that to happen automatically. Both gnome-screensaver and the power manager have that option.

If you forget to lock your car doors it's unlikely that your insurance company would pays you anything if somebody steals everything from your car (and perhaps the car itself). If you yourself let the person in your car, the situation is even worse.

Is it really that hard to accept that yes, the user *does* have a part in maintaining the system's security. Compromising the security at larger scale yourself (your whole user account) and then complaining that the system doesn't protect some minor component (passwords stored inside that account) seems quite backwards to me.

Perhaps complaining about small details is easier than admitting that you are yourself causing the larger-scale security issue...

---

### Post by revanb on 2009-10-29
Look, scripts can be run when your screen is locked.

Also, when sudo is compromized it affects all system users. If someone doesn't lock their own account only their own account is compromized.

Back to my car analogy:
If you leave your car unlocked with your keys available inside - oops.

If you leave your garage unlocked with everybodys keys and cars inside - oops again.

I'm done with this argument. It's silly.

---

### Post by P4man on 2009-10-29
> **mcduck said:**
> Does it really come as this big surprise to people that if you leave your desktop unattended and unlocked at hands of people you can't trust your personal information might be compromised? :D

Still, everybody complaining about the keyring seems to ignore the fact that not locking your session leaves _all_ your files and information vulnerable, and completely compromises your user's security (since malware such as keyloggers can be easily installed to that user account).

If you are afraid that you don't remember to lock the session yourself, you can set that to happen automatically. Both gnome-screensaver and the power manager have that option.

If you forget to lock your car doors it's unlikely that your insurance company would pays you anything if somebody steals everything from your car (and perhaps the car itself). If you yourself let the person in your car, the situation is even worse.

Is it really that hard to accept that yes, the user *does* have a part in maintaining the system's security. Compromising the security at larger scale yourself (your whole user account) and then complaining that the system doesn't protect some minor component (passwords stored inside that account) seems quite backwards to me.

Perhaps complaining about small details is easier than admitting that you are yourself causing the larger-scale security issue...

Sigh.. those car analogies. 

Anyway if locking the screen is the only safe way and mandatory to have any sort of protection, then sudo authentication should not time out. I should not have to type in my password a million times per day, a solution like in windows where you just chose to run something as administrator or click an "ok" button should suffice. IOW, sudo would still be required but the password should not.

If thats what you're advocating, then perhaps, but having AND the annoyance of sudo passwords timing out and the huge security threat when you dont lock your screen we got the worst of both worlds now. The inconvenience and the security threat.

---

### Post by snkiz on 2009-10-29
mcduck I don't believe anyone has forgotten that. And  a locked screen wouldn't stop someone who knows what their doing. <ctl><alt>f1 and your at a console wheres Gnome security then? Your back to one layer, a single password. Then let the hack begin.

The point of the thread is the keyring is to accessible for comfort. Not how good it is, or how it should be used, or even how to protect it. Just why is it 4 clicks away? Many users are not comfortable with that.

---

### Post by P4man on 2009-10-29
> **revanb said:**
> Look, scripts can be run when your screen is locked.

how? I mean how would an intruder abuse an unlocked sudo while the screen is locked? If that somehow does provide a security threat then unlocking sudo would itselve constitute an unacceptable security threat. There is no point being safe 23 hours per day.

> 
Also, when sudo is compromized it affects all system users. If someone doesn't lock their own account only their own account is compromized.


How would sudo be *compromised*? You are the one saying an unlocked screen is inherently insecure if you are afk, so that it could also affect other users is what makes it unacceptable? So its okay if your own security is compromised, but that of other accounts you find unacceptable. I dont understand the logic.
> 
Back to my car analogy:

Im done reading car analogies. If you cant make the argument without resorting to cars then perhaps you dont have one.

---

### Post by P4man on 2009-10-29
BTW, locking the screen doesnt work on my Karmic. It does nothing. I guess I should file a bug report and mark it critical and delay the release now ;)

---

### Post by mcduck on 2009-10-29
> **P4man said:**
> Sigh.. those car analogies. 

Anyway if locking the screen is the only safe way and mandatory to have any sort of protection, then sudo authentication should not time out. I should not have to type in my password a million times per day, a solution like in windows where you just chose to run something as administrator or click an "ok" button should suffice. IOW, sudo would still be required but the password should not.

If thats what you're advocating, then perhaps, but having AND the annoyance of sudo passwords timing out and the huge security threat when you dont lock your screen we got the worst of both worlds now. The inconvenience and the security threat.

If you don't want a car analogy, I can definitely make some other analogy for you if you need one. (I've already made a fairly nice comparison in this thread between locking you home door to keep unwanted people out and protect your belongings and locking your user session to protect your belongings) :D

Here you go: "If you forget to lock your *home* doors it's unlikely that your insurance company would pay you anything if somebody steals everything from your *home*. If you yourself let the person in your *home*, the situation is even worse."


It's also already been mentioned here that there's a different level of security policy for protecting one user account and the whole system. And suggested that you can easily try using a non-admin user account yourself to easily see the difference between protecting the whole system and one user account.

And, no matter what kind of policy you use to protect the keyring, or no policy at all, it's still compromised when you leave your session unlocked and the machine unattended. Adding a password to see the keys would only bring an illusion of security when the reality wouldn't change all and all your files and keys would still be unsecure.

---

### Post by snkiz on 2009-10-29
I like sudo timing out thank you. if a script with sudo runs on my system while sudo is unlocked it doesn't ask for a password. so if for some insane reason I download a script and run it without realizing it has sudo in it bad things may happen. With the timeout That window of oppportunity is limited.

One more time for those in the back. sudo is root access seahorse is user access, an important distinction.

---

### Post by P4man on 2009-10-29
> **mcduck said:**
> If you don't want a car analogy, I can definitely make some other analogy for you if you need one. (I've already made a fairly nice comparison in this thread between locking you home door to keep unwanted people out and protect your belongings and locking your user session to protect your belongings) :D

Its not the cars that bother me, its the fact you have to resort to analogies to argue the point. The rest of your post is a repitition of what has already been said a dozen times but doesnt address my points.

If you dont like the illusion of security, then having 500x popups per day asking your password would be the first thing to eliminate. Not only does it give the same illusion its also pretty annoying (unlike having to type a pw once every 6 months when you open seahorse).

---

### Post by P4man on 2009-10-29
> **snkiz said:**
> I like sudo timing out thank you. if a script with sudo runs on my system while sudo is unlocked it doesn't ask for a password. so if for some insane reason I download a script and run it without realizing it has sudo in it bad things may happen. With the timeout That window of oppportunity is limited.


Yes Sudo should ask permission to run as root, or you should manually launch it as root (with sudo or otherwise). But why would it need to re authenticate you? If the person behind the screen is to be trusted as being the same sudoer that logged in 5 hours earlier? Why a password when a simple popup as in windows would achieve the same?

---

### Post by mcduck on 2009-10-29
> **P4man said:**
> Its not the cars that bother me, its the fact you have to resort to analogies to argue the point. The rest of your posts is a repitition of what has already been said a dozen times but doesnt address my points.

If you dont like the illusion of security, then having 500x popups per day asking your password would be the first thing to eliminate. Not only does it give the same illusion its also pretty annoying (unlike having to type a pw once every 6 months when you open seahorse).

I have already explained the same pouints thout using analogies, but it seems that the points were not understood. hence the use of an analogy to try to explain the situation to those who didn't undertand the pount when it was described directly.

I don't know what you are doing if you get 500 password popups per day, but I can tell you you are definitely doing somehting wrong if that's the case. try using "sudo -i" and "gksudo nautilus"and you don't have to do that any more.

And yes, I also answered your point about the sudo timeout. You just ignored it. Since you dislike repetition (and so do I) I'm not going to repeat the answer to you. :)

---

### Post by mcduck on 2009-10-29
> **snkiz said:**
> mcduck I don't believe anyone has forgotten that. And  a locked screen wouldn't stop someone who knows what their doing. <ctl><alt>f1 and your at a console wheres Gnome security then? Your back to one layer, a single password. Then let the hack begin.

The point of the thread is the keyring is to accessible for comfort. Not how good it is, or how it should be used, or even how to protect it. Just why is it 4 clicks away? Many users are not comfortable with that.

Ctrl-Alt-F1 won't do anything unless you have password for the user account. If you do, the account is already compromnised and the security breach has happened already, somewhere else.

Using TTY, locked screen, logging out of session or even shutting down the machine completely or whatever, the security is in protecting your user account by use of user password. If you fail to do that, all your files and the whole account is compromised anyway. Small change in the keyring management won't change that. The security is already broken before the point when somebody is able to access the Keyring Manager.

---

### Post by the.lost.one on 2009-10-29
[LIST]
[*]Those who are rigidly against any change have not been able to answer this simple question:
[/LIST]
[INDENT] What is relatively more secure:
[/INDENT][INDENT] a) 9 out of 10 people can steal my passwords
b) 2 out of 10 people can steal my passwords
[/INDENT]
[LIST]
[*]Those who say "don't let them use it, if you don't trust" fail to appreciate the fact in real life an extremely large number of people are NEITHER absolutely trustworthy nor absolutely untrustworthy. We may trust a person with one thing (e.g. they wont install keyloggers) but not with another (e.g. if a password is right in front of them they might be tempted to use it). Also, you guys fail to realise that there is a big difference in professional thieves or determined hackers and opportunists. Opportunists can be everywhere but most people don't have people with scripting knowledge around them.
[/LIST]
 
[LIST]
[*]It would be security through obscurity if it were the ONLY measure. It is an additional layer that we want that would protect us from 90% of the people. Thinking that a user would never ever forget to lock the screen is seriously flawed. We want a system where in the rare case we forget to lock the screen, we would still be protected from 90% of the people. Currently, our passwords are vulnerable to almost 9 out of 10 people, in case we forget to lock screen.
[/LIST]

[LIST]
[*]I hate the car analogy here (lol) but I have to say this. Some thieves are professionals and some are opportunists. Some professionals have jammers that would render the tracker you have installed useless. Does it mean tracking is useless just because a few can get past it? On top of that there are thieves:
[/LIST]
[INDENT]- who steal cars
- who steal only music systems from the cars
- who only steal the side mirrors
- who only steal CNG kits
- and a few other types

We have different security measures for all these types and not JUST for the most advanced and professional thief.


[/INDENT]
[LIST]
[*]If you think the *show passwords button* is  there to make the user lock the screen, why not have the passwords displayed ON the desktop background. That is thousand times more likely to make a person lock the screen. Seriously, tell me?
[/LIST]

---

### Post by P4man on 2009-10-29
> **mcduck said:**
> 

I don't know what you are doing if you get 500 password popups per day, but I can tell you you are definitely doing somehting wrong if that's the case. try using "sudo -i" and "gksudo nautilus"and you don't have to do that any more.


500x is an exaggeration of course, but its more than once, and more than once per session would be pointless if you can indeed assume the person behind the unlocked screen to be the same user that logged in. Thats the assumption seahorse/keyring/gnome makes. Its one I disagree with and sudo policy seems to disagree as well.

---

### Post by mcduck on 2009-10-29
> **the.lost.one said:**
> 
Those who are rigidly against any change have not been able to answer this simple question:
What is relatively more secure:
[LIST]
[*] a) 9 out of 10 people can steal my passwords
[*]b) 2 out of 10 people can steal my passwords
[/LIST]

That's because there's a third alternative we've been trying to tell you:

[LIST]
[*]0 of 10 people can steal my passwords, and in addition all my files are safe as well and my user account stays uncompromised.
[/LIST]

That way, those people able to access the passwords would truly have to be skilled, instead of just fairly cunning which is all it takes to get your keys from the keyring even if the keyring manager won't show them. And I really mean that a bit of cunningness is all it takes, no programming skills required or any advanced stuff like that.

What comes to people not being absolutely trustworthy or absolutely untrustworthy, I don't see what that has to do with you letting them use your personal user account when there's the Guest Session available. That way you don't even have to try to decide if you can trust those people or not. Even better, that would be quite a polite thing to do anyway since perhaps the person using your computer doesn't quite trust *you* and might like to keep his browsing history secured from you.. Letting him use the guest session instead of your own brings security to both, you and the guest.

---

### Post by snkiz on 2009-10-29
the.lost.one
 That is the difference between a  developer/geek(no offence intended.) train of thought and a users. I've seen this a few times since going down the FLOSS path. The dev's have stubbornly set their position and sadly only a large public outcry will cause any action to be taken.

---

### Post by the.lost.one on 2009-10-29
I would also like to know why is it that Empathy, Pidgin use keyring but aMSN does not? If the Ubuntu developers can make some applications use keyring, why not make the applications encrypt passwords themselves?

Currently, as some people have mentioned that all applications have access to keyring once a user is logged in. Why not have a system where ONLY the applications a user authorise can access keyring? And no it wont be a bother because one has to type the password the first time one is saving it. After that only the "xyz" application i have authorised would automatically access the password.

That way even if someone tries to run a script to get all my passwords, they wont be able to because their script wont be authorised to access keyring.

Someone also said that a keylogger could be installed without the sudo password? It that really true? Does someone _actually know_? Because in Windows you cannot install a keylogger without admin elevation.

---

### Post by the.lost.one on 2009-10-29
> **mcduck said:**
> That's because there's a third alternative we've been trying to tell you:

[LIST]
[*]0 of 10 people can steal my passwords, and in addition all my files are safe as well and my user account stays uncompromised.
[/LIST]

That way, those people able to access the passwords would truly have to be skilled, instead of just fairly cunning which is all it takes to get your keys from the keyring even if the keyring manager won't show them. And I really mean that a bit of cunningness is all it takes, no programming skills required or any advanced stuff like that.

What happens if you forget to lock screen? Are you telling me there is no chance you would ever forget? In the system we are suggesting you'd still be protected from most if you forget. It is a measure to minimise damage. 

It is not advanced for you, but I dont know how to, and a lot of people don't.

---

### Post by mcduck on 2009-10-29
> **the.lost.one said:**
> What happens if you forget to lock screen? Are you telling me there is no chance you would ever forget? In the system we are suggesting you'd still be protected from most if you forget. It is a measure to minimise damage. 

It is not advanced for you, but I dont know how to, and a lot of people don't.

I really need to repeat this once again? I've mentioned this at least 5 times in this thread now:

Both Gnome-screensaver and the power manager allow you to set the session to lock automatically. Just enable that if you feel that you might not remember to lock the session yourself.

(so yes, there's no change that my session would ever be left unlocked. It locks automatically if I for some reason would forget to do it myself)

I'm not really into targeting for minimizing damage and creating illusion of security when there's the option of trying to completely prevent the damage in the first place and creating some level of real security. False illusion of security is even worse than no security at all.

---

### Post by snkiz on 2009-10-29
> **mcduck said:**
> I really need to repeat this once again? I've mentioned this at least 5 times in this thread now:

Both Gnome-screensaver and the power manager allow you to set the session to lock automatically. Just enable that if you feel that you might not remember to lock the session yourself.

(so yes, there's no change that my session would ever be left unlocked. It locks automatically if I for some reason would forget to do it myself)

Is your timeout set for 30 seconds? if not your unprotected until the screensaver kicks in.
> **mcduck said:**
> 
I'm not really into targeting for minimizing damage and creating illusion of security when there's the option of trying to completely prevent the damage in the first place and creating some level of real security. False illusion of security is even worse than no security at all.
lap belts in cars can cause injury,by your logic your better off not being straped in?
FAIL

---

### Post by P4man on 2009-10-29
> **mcduck said:**
> I really need to repeat this once again? I've mentioned this at least 5 times in this thread now:

Both Gnome-screensaver and the power manager allow you to set the session to lock automatically. Just enable that if you feel that you might not remember to lock the session yourself.

While its certainly a good idea to enable that, using your logic its another false sense of security, since anyone could move the mouse to restart those 15 minutes endlessly. In the real world you also often expect to return to your pc instantly but while walking back with your cup of coffee you get called away, meet someone, you stumble and break a leg. 
Not too mention opening seahorse and printing a printscreen would take less than 1 minute. No too mention the fact my "lock screen" doesnt work for some reason :)

For all those cases it would be nice if seahorse did not make it so blatantly easy to obtain my passwords.

---

### Post by the.lost.one on 2009-10-29
> **mcduck said:**
> What comes to people not being absolutely trustworthy or absolutely untrustworthy, I don't see what that has to do with you letting them use your personal user account when there's the Guest Session available. 

Quite a bit of people don't think that it has nothing to do with it. If I, say, make my hypothetical new girl friend log in as guest, that sends her the signal that I don't trust her. I might trust her with using my computer but I don't want her to know every single password in keyring. You can say thats normal, she should understand and I should try to change how she thinks. But you know what? I'd rather change how my passwords are stored instead of how the girl friend thinks.

This is just one if the many scenarios in which it will be useful to have this feature or security layer, whichever way you wanna look at it.

> **mcduck said:**
>  Even better, that would be quite a polite thing to do anyway since perhaps the person using your computer doesn't quite trust *you* and might like to keep his browsing history secured from you.. Letting him use the guest session instead of your own brings security to both, you and the guest.

Is that true? Because it appears that if I have sudo password I can install malicious software for all users including guests?

---

### Post by mcduck on 2009-10-29
> **snkiz said:**
> Is your timeout set for 30 seconds? if not your unprotected until the screensaver kicks in.

lap belts in cars can cause injury,by your logic your better off not being straped in?
FAIL

It's 2 minutes. At least that's a lot better than letting anybody always to have a free access to the system. And pretty much enough to make sure nobody has enough time to find that my machine is unattended and unlocked and access it, at least in the time that's left after I've left the room...  Still, this far I haven't forgotten to lock the machine myself, and even if I would I wouldn't blame it on anybody else than myself..

And FAIL yourself. As long as you know that some system is not secure you know that you are *yourself* responsible, and know to take required actions to prevent damage. With the false security you imagine that the system is secure enough that you don't need to take any responsibility yourself.

Your seat belt analogy might be correct if using seatbelts woud actually create very little extra safety (or no safety at all) but were still marketed as something that would protect you ~100% in case of accidents. If that was the case then yes, I wouldn't bother strapping myself in. (In reality seat belts actually bring considerably more security than cause damage, so I'm using them).

---

### Post by scorp123 on 2009-10-29
> **michaelzap said:**
> It's reasonable to wonder why passwords for things other than your local computer can be viewed in clear text without entering a password. Even Windows doesn't allow that. There is a tool called "SnadBoy Revelation". Go and Google it. With it you can unmask any password Windows is "protecting". So even if Windows doesn't show the password it's easy for a user-space application such as "SnadBoy" to find it in the RAM and reveal it.

At least with Linux you know right away what you're dealing with.

---

### Post by the.lost.one on 2009-10-29
Quote:
                                                                      [SIZE=2]Originally Posted by **mcduck**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8187496#post8187496")[/SIZE]                 
                 [I][SIZE=2]I really need to repeat this once again? I've mentioned this at least 5 times in this thread now:

Both Gnome-screensaver and the power manager allow you to set the session to lock automatically. Just enable that if you feel that you might not remember to lock the session yourself.[/SIZE] [/I]
                                 
How inconvenient it would be if I have to unlock the screen after every 5 minutes! Plus, for for those 5 minutes, even a noob can get my passwords.

Edit:
If I am a reporter in a war zone I would wear a helmet and bullet proof vest and not when I am going shopping in a peaceful area.

---

### Post by mcduck on 2009-10-29
> **the.lost.one said:**
> 
Is that true? Because it appears that if I have sudo password I can install malicious software for all users including guests?
Of course you can, if you are the admin of the machine. 

If we must be this pedantic about details then let me put it this way: letting guest users use guest account instead of your own will bring you considerably better security, and the guest user better security than using your account would. Still, the guest user is using your computer and thus must have some level of trust towards you and accept the fact that the machine is still yours and runs software you have installed and configured.

---

### Post by mcduck on 2009-10-29
> **the.lost.one said:**
> Quote:
 	 	 		 			 				 					[SIZE=2]Originally Posted by **mcduck** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8187496#post8187496")[/SIZE] 				
 				[I][SIZE=2]I really need to repeat this once again? I've mentioned this at least 5 times in this thread now:

Both Gnome-screensaver and the power manager allow you to set the session to lock automatically. Just enable that if you feel that you might not remember to lock the session yourself.[/SIZE] [/I]
 			 		 	 	 
How inconvenient it would be if I have to unlock the screen after every 5 minutes! Plus, for for those 5 minutes, even a noob can get my passwords.
Then perhaps you could try to lock them machine yourself? Most peoople don't really have any problems remebering to lock their home doors, their cars, remeberign to take their ATM cards out of the ATM machine after withdrawing some money etc.. I don't see how remebering to lock your computer would be som much harder than those things are.

And even if the machine would only unlock after those 5 minutes, it would still be more secure than not unlocking it at all. I once again need to repeat myself, but getting the keys out of the keyring on an unlocked session doesn't require any programming skills, just a bit of cunning. (I'd rather not start describing the ways the keys can actually be accessed without using the keyring manager and writing any programs. Besides, at least one method has already been mentioned in this thread. The point is that the keys are still accessible as plain text through the programs that already exist in your system and use those keys.)

---

### Post by benj1 on 2009-10-29
> **the.lost.one said:**
> I would also like to know why is it that Empathy, Pidgin use keyring but aMSN does not? If the Ubuntu developers can make some applications use keyring, why not make the applications encrypt passwords themselves?

pidgin doesnt use the keyring, it stores its files in plain text
[http://developer.pidgin.im/wiki/PlainTextPasswords]("http://developer.pidgin.im/wiki/PlainTextPasswords")
you can have applications encrypt the passwords them selves, unfortunately, because most of the apps we use are open source the encryption method is on show, so either you require another password, or you have a useless encryption method.
 
> 
Currently, as some people have mentioned that all applications have access to keyring once a user is logged in. Why not have a system where ONLY the applications a user authorise can access keyring? And no it wont be a bother because one has to type the password the first time one is saving it. After that only the "xyz" application i have authorised would automatically access the password.

That way even if someone tries to run a script to get all my passwords, they wont be able to because their script wont be authorised to access keyring.

first does that mean you wouldnt allow seahorse access to the passwords?
second this indicates that you have an app on your system that you dont trust, that is a bigger security flaw than having passwords on show, again the apps are open source the app can just rip all the stuff out of  trusted app to make it appear that it is a trusted app.

---

### Post by snkiz on 2009-10-29
> **mcduck said:**
> 

And FAIL yourself. As long as you know that some system is not secure you know that you are *yourself* responsible, and know to take required actions to prevent damage. With the false security you imagine that the system is secure enough that you don't need to take any responsibility yourself.

First off, the timer resets if you touch the keyboard or mouse so thats a false sense of security. second most don't know the system is **that** insecure. Ubuntu and Gnome has done nothing to inform the user. Third it would be far easier for me to just remove the keyring altogether then to stay here arguing the function of seahorse. so I am taking responsibility, for newbies that don't know any of this.

---

### Post by snkiz on 2009-10-29
> **benj1 said:**
> pidgin doesnt use the keyring, it stores its files in plain text
[http://developer.pidgin.im/wiki/PlainTextPasswords]("http://developer.pidgin.im/wiki/PlainTextPasswords")
you can have applications encrypt the passwords them selves, unfortunately, because most of the apps we use are open source the encryption method is on show, so either you require another password, or you have a useless encryption method.
Not true open source encryption depends on a random key. even with the source for the encryption method you still need that key.

---

### Post by mcduck on 2009-10-29
> **snkiz said:**
> First off, the timer resets if you touch the keyboard or mouse so thats a false sense of security. second most don't know the system is **that** insecure. Ubuntu and Gnome has done nothing to inform the user. Third it would be far easier for me to just remove the keyring altogether then to stay here arguing the function of seahorse. so I am taking responsibility, for newbies that don't know any of this.

Yes. I set the timeout to short enough that It's unlikely that I'd have left the room before the system gets locked. And as long as Im in the room nobody will not be able to touch the keyboard or mouse unnoticed.

Lets turn this issue around. Here's a question for everybody who wants this change in the keyring manager:

Are you now locking your session when you leave it unattended? Have you set any timeout for automatic locking? Are you using the Guest Session for guest users instead of letting them access your personal user account? If not, then why are you demanding for extra security when you don't even bother to use the (really easy and simple) security measures you already have available?

edit: or are you perhaps only interested in security as long as it happens automatically, without you having to take any personal action or responsibility? Cause complaining about things in Internet is easier than learning to press a simple keyboard shortcut (or two clicks from the menu) when leaving your computer unattended?

---

### Post by snkiz on 2009-10-29
Answer yes I lock the screen yes I have a timeout. and no I don't use the guest session due to ram limitations. Fianly yes every member of my family and even some of my friends have a user name on my computer. that doesn't change the fact that some times these measures are not used.

---

### Post by the.lost.one on 2009-10-29
```
My post:
Currently, as some people have mentioned that all applications have access to keyring once a user is logged in. Why not have a system where ONLY the applications a user authorise can access keyring? And no it wont be a bother because one has to type the password the first time one is saving it. After that only the "xyz" application i have authorised would automatically access the password.

That way even if someone tries to run a script to get all my passwords, they wont be able to because their script wont be authorised to access keyring
```
> **benj1 said:**
> 

first does that mean you wouldnt allow seahorse access to the passwords?
second this indicates that you have an app on your system that you dont trust, that is a bigger security flaw than having passwords on show, again the apps are open source the app can just rip all the stuff out of  trusted app to make it appear that it is a trusted app.

I only stated what I want. I cant design it. I am not a coder.

No, it is not about whether you trust an app. Why would anyone WANT an app to have access to passwords it is not supposed to use? I am an auditor and I know that Auditing standards require limiting access to information to only that is needed. Plus that was in reply to  those who said anyone can write an app and get your password even if it is not visible. It will protect it from that.

Are you a developer or technical guy? Can you please tell me why in the world a keylogger could be installed on Ubuntu without root password, if that is true as some has suggested. In Windows you need admin level access to install keyloggers.

---

### Post by benj1 on 2009-10-29
> **snkiz said:**
> Not true open source encryption depends on a random key. even with the source for the encryption method you still need that key.
that key still needs to be stored somewhere, with a password its in your head, if not it has to be stored somewhere.

---

### Post by P4man on 2009-10-29
> **mcduck said:**
> 
Are you now locking your session when you leave it unattended? 

I would if I could
[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/436724](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/436724)
A *low priority* bug prevents me from protecting my passwords. 

> Have you set any timeout for automatic locking? 
yes, but its not working. Same bug

> Are you using the Guest Session for guest users instead of letting them access your personal user account? 

Of course. unless Im there sitting next to them.

> edit: or are you perhaps only interested in security as long as it happens automatically, without you having to take any personal action or responsibility? 

No, not ONLY, but yes of course Im interested in more security that doesnt depend on my forgetfulness or (in)ability to lock my screen. Are you not?

---

### Post by snkiz on 2009-10-29
I hear you on that. Its a question of how far you want to take it. You could keep you encrypted keys on a flash drive or memorize them. (I'm sure their are people out there that can do it.) Whatever all encryption really is is a very long password so the same rules would apply.

---

### Post by the.lost.one on 2009-10-29
Woah! That bug P4man has pointed out should end the discussion. Only it would not

---

### Post by mcduck on 2009-10-29
> **the.lost.one said:**
> Woah! That bug P4man has pointed out should end the discussion. Only it would not

Did you read the bug report? It only happens if you have *autologin* enabled. So much for security when even the user session is configured to be accessible without a password...

---

### Post by P4man on 2009-10-29
> **mcduck said:**
> Did you read the bug report? It only happens if you have *autologin* enabled. So much for security when even the user session is configured to be accessible without a password...

Read it again. Most users (me including) have it turned OFF

---

### Post by benj1 on 2009-10-29
> **the.lost.one said:**
> 
I only stated what I want. I cant design it. I am not a coder.

not wanting to be rude, but if you want to make a suggestion you need to understand the issues involved, or at least listen to the developers that do understand the issues, the developers dont think there is a problem, or at least dont think theres a way to make it more secure.

> 
No, it is not about whether you trust an app. Why would anyone WANT an app to have access to passwords it is not supposed to use? I am an auditor and I know that Auditing standards require limiting access to information to only that is needed. Plus that was in reply to  those who said anyone can write an app and get your password even if it is not visible. It will protect it from that.

i know my point is, it would be fairly easy at present to make one app look like another, if firefox is trusted, another app could just appear to be firefox to gain access to your firefox passwords.
> 
Are you a developer or technical guy? Can you please tell me why in the world a keylogger could be installed on Ubuntu without root password, if that is true as some has suggested. In Windows you need admin level access to install keyloggers.
i wouldnt call my self a developer, but i do program, you dont need root access to install a program, i wouldnt have thought you would need root access for a keylogger, but ive never tried making one so its more of a guess then anything, but the issue is a bit moot anyway in my mind, if some one has physical access they could physically intercept input before the keyboard even reaches the pc.

---

### Post by mcduck on 2009-10-29
> **P4man said:**
> Read it again. Most users (me including) have it turned OFF

Sorry, my bad. I just read through the end of the report and that's true. Besides, I have one machine running 9.10 with autologin enabled and it locks the display just as fine as others so the problem clearly is somewhere else. :)

---

### Post by P4man on 2009-10-29
Thats okay, and bugs happen, its not because this particular bug prevents me from locking my screen that it really changes the issue. I got a problem with the fundamental concept that allows anyone to view my passwords with am absolute  minimum of effort or knowledge while Im expected to do a considerable effort typing my long and secure password God knows how often each day to perform fairly trivial tasks.  

If my unlocked desktop is going to be fundamentally insecure at least Id like it to be convenient. If its gonna be inconvenient at least it should provide SOME protection from undetectable password/identity theft when I turn my back for 30 seconds.

---

### Post by mcduck on 2009-10-29
By the way, it takes exactly as many mouse clicks to view wireless passwords (for example) through the Network Manager applet as it takes to read them through Seahorse...

But I must say that I hope they fix that session locking bug pretty soon, I'd hate to see that happening on any of my computers.. That would pretty much mean having to log out every time I leave my computer unattended. :/

---

### Post by P4man on 2009-10-29
> **mcduck said:**
> By the way, it takes exactly as many mouse clicks to view wireless passwords (for example) through the Network Manager applet as it takes to read them through Seahorse...

Each will have different concerns. Personally I dont care about the wifi password. At home I even got one unsecured AP for guests or neighbors or anyone really since I dont mind anyone within range using my wifi (its unlimited and I dont live in a city or apartment block with people I dont know). I got a second AP with WPA protection, but even that I dont really care much if the password leaks. At work everyone knows the password anyway.

Im much more concerned about email/IM passwords being visible. Far more than I am about someone quickly glancing over my email behind my back. Or if one day Skype supports the keyring that would potentially be disastrous (you can be logged in to skype on more than 1 location simultaneously, with no way of knowing if someome else is logged in as you.  Not too mention the money it might cost you).

---

### Post by DodgeV83 on 2009-10-29
> **mcduck said:**
> By the way, it takes exactly as many mouse clicks to view wireless passwords (for example) through the Network Manager applet as it takes to read them through Seahorse...

But I must say that I hope they fix that session locking bug pretty soon, I'd hate to see that happening on any of my computers.. That would pretty much mean having to log out every time I leave my computer unattended. :/

Since the Network Manager screen showed me the same dummy "click here to allow access to keyring" screen as seahorse did before showing my wireless passwords in clear-view, I see the issues as being the same.  The keyring should require elevated access (simply re-confirming your username and password) before allowing a password to be shown.

Funny how people complain about having to type in password to change CPU Scaling, but when it comes to my passwords...naaaaaaaaaaaaaah that's ok!  You already confirmed it's you 8 hours ago when you logged in! ](*,)

---

### Post by the.lost.one on 2009-10-29
> **benj1 said:**
> i know my point is, it would be fairly easy at present to make one app look like another, if firefox is trusted, another app could just appear to be firefox to gain access to your firefox passwords.

Is that possible and easy? I really doubt. I can't recall the exact details but I what I remember is that in Windows this particular issue of apps presenting as another has been dealt with. I think that there was an issue with software firewall in Windows that allowed a malicious program to say, "Hey, I am Firefox.exe, please allow me" and then it could run. But something changed in Windows or firewalls so that this is not the case anymore.

> **benj1 said:**
> i wouldnt call my self a developer, but i do program, you dont need root access to install a program, i wouldnt have thought you would need root access for a keylogger, but ive never tried making one so its more of a guess then anything, but the issue is a bit moot anyway in my mind, if some one has physical access they could physically intercept input before the keyboard even reaches the pc.


If keylogger cannot be installed without sudo, it means that keyring's *show password button* (or its willingness to give access to all passwords to every app) is the only way for the person to get the passwords. As far as physical keylogger or devices are concerned, those are obviously no where as stealthy and free as software keylogger.

---

### Post by scaine on 2009-10-29
> **benj1 said:**
> not wanting to be rude, but if you want to make a suggestion you need to understand the issues involved, or at least listen to the developers that do understand the issues, the developers dont think there is a problem, or at least dont think theres a way to make it more secure.

Why is there such animosity towards the obvious solution of requiring an additional password to view the password in plaintext?  As I posted originally, that's what KeepassX does (if you ask it).

It would certainly solve the issue being raised here.

Please don't argue why doing so isn't necessary - that's already been argued over 290 odd posts.  All I'm interested in is "why all the resistance to a seemingly common-sense fix?".

---

### Post by scaine on 2009-10-29
> **the.lost.one said:**
> 
If keylogger cannot be installed without sudo, it means that keyring's *show password button* (or its willingness to give access to all passwords to every app) is the only way for the person to get the passwords. As far as physical keylogger or devices are concerned, those are obviously no where as stealthy and free as software keylogger.

This isn't about stopping keyloggers, hackers, thieves or such.  This is about forgetting to lock your PC/laptop, say at work, while you pop away for a coffee.  Then a subordinate/malicious staff member can't resist temptation and fires up seahorse and memorises your gmail account.  Now he can sit for the next 6 months/however long until your change your gmail password, at home, reading all your e-mail and you'll never, ever know.

[edit : Keylogging without sudo appears to be possible : [http://distrojockey.com/2005/ultimate-linux-keylogger-uberkey.190.linux](http://distrojockey.com/2005/ultimate-linux-keylogger-uberkey.190.linux), but reports on Uberkey appear to suggest that it's just not very reliable]

---

### Post by benj1 on 2009-10-29
> **scaine said:**
> Why is there such animosity towards the obvious solution of requiring an additional password to view the password in plaintext?  As I posted originally, that's what KeepassX does (if you ask it).

It would certainly solve the issue being raised here.

Please don't argue why doing so isn't necessary - that's already been argued over 290 odd posts.  All I'm interested in is "why all the resistance to a seemingly common-sense fix?".

because doing so wouldnt make the system inherently any more secure, it would just make it seem so. keepassx (i assume)unencrypts the password when you enter the password, then when you exit, it re encrypts it, that fine, you cant do that with the passwords seahorse looks after because they are needed all the time, so it has to remain unlocked all the time, the only way to re encrypt them is to log out or lock the screen.

---

### Post by DodgeV83 on 2009-10-29
> **scaine said:**
> Please don't argue why doing so isn't necessary - that's already been argued over 290 odd posts.  All I'm interested in is "why all the resistance to a seemingly common-sense fix?".

There is resistance because of an "I'm smarter than you, I'm not giving you the option because I know what's best." attitude.  Non-techie people I speak to regarding this denounce the attitude as "paternal" and are shocked at the stated argument against this request.

Quote: "So they're trying to teach you a lesson, so you'll know better to lock your screen next time?  I guess identity theft isn't that big a deal to them."

---

### Post by the.lost.one on 2009-10-29
> **scaine said:**
> This isn't about stopping keyloggers, hackers, thieves or such.  This is about forgetting to lock your PC/laptop, say at work, while you pop away for a coffee.  Then a subordinate/malicious staff member can't resist temptation and fires up seahorse and memorises your gmail account.  Now he can sit for the next 6 months/however long until your change your gmail password, at home, reading all your e-mail and you'll never, ever know.

Haha. Thats what I am saying. No clear text passwords. That is effective against a lot of people.

My reply was to those who said, "Oh, why are you worrying about show passwords button. Even if there were no clear passwords the person could install a keylogger." And I said that you need sudo password to do that which that person would not have. So some people said you dont need sudo to install keylogger. I find that odd since in windows you need admin level access.

---

### Post by the.lost.one on 2009-10-29
> **benj1 said:**
> because doing so wouldnt make the system inherently any more secure, it would just make it seem so. keepassx (i assume)unencrypts the password when you enter the password, then when you exit, it re encrypts it, that fine, you cant do that with the passwords seahorse looks after because they are needed all the time, so it has to remain unlocked all the time, the only way to re encrypt them is to log out or lock the screen.

I don't think Yahoo and MSN and other messenger services and webmails need it ALL the time. You need password ONLY when you log in.

---

### Post by mcduck on 2009-10-29
> **the.lost.one said:**
> 
If keylogger cannot be installed without sudo, it means that keyring's *show password button* (or its willingness to give access to all passwords to every app) is the only way for the person to get the passwords. As far as physical keylogger or devices are concerned, those are obviously no where as stealthy and free as software keylogger.

They can be installed without "sudo" or any administrative privileges. Lots of software can be installed that way, the difference is that without such privileges the programs are installed *for that user only*, while installing anything system-wide requires root privileges.

Many programs don't require any specific installing and can simply be extracted somewhere and run that way. Logging key presses is simple and easy, and user level programs are able to read from keyboard so there's nothing preventing such program from working even if it's not installed system-wide.

Still, keylogger for your account only would be a rather nasty thing anyway, which is exactly the reason why i've been saying that protecting your session is high priority, and whatever the keyring manager does is pretty much just a small detail compared to that. Compromised session means that the passwords are compromised as well.

Of course it's been argued that installing a keylogger or reading the passwords through other means is too hard for most of the people and thus it's not a concern (I disagree, although based on how many times a week I need to help somebody on these forums to change their keyring password I'm starting to feel that accessing the passwords through the Keyring Manager is too hard for most of the people.. :D)

---

### Post by P4man on 2009-10-29
> **the.lost.one said:**
> Haha. Thats what I am saying. No clear text passwords. That is effective against a lot of people.

My reply was to those who said, "Oh, why are you worrying about show passwords button. Even if there were no clear passwords the person could install a keylogger." And I said that you need sudo password to do that which that person would not have. So some people said you dont need sudo to install keylogger. I find that odd since in windows you need admin level access.

I just googled around a bit and found a keylogger. From its webpate:
> LKL is a **userspace** keylogger that runs under Linux on the x86 architechture. LKL sniffs and logs everything that passes through the hardware keyboard port (0x60). It translates keycodes to ASCII with a keymap file.

Sounds like it doesnt require root to run, but I cant install it without putting sudo before the make install command

---

### Post by scaine on 2009-10-29
> **benj1 said:**
> because doing so wouldnt make the system inherently any more secure, it would just make it seem so. keepassx (i assume)unencrypts the password when you enter the password, then when you exit, it re encrypts it, that fine, you cant do that with the passwords seahorse looks after because they are needed all the time, so it has to remain unlocked all the time, the only way to re encrypt them is to log out or lock the screen.

Fundamentally disagree - doing so would make the system slightly more secure.  Not "secure", but "slightly more secure" and would remove this thread from relevance because it fixes the scenario I posted about just there (about passerby seeing all your passwords while you're at the water cooler).

But back to my my question - why all the animosity?  Nearly 300 posts of argument?  Over something easily fixed?  I've read EVERY post.  It's soul destroying to read and it's bad for the image of Ubuntu when an easily fixed security issue is defended to the death like this.

I just wanted to understand where all that defending is coming from.

---

### Post by mcduck on 2009-10-29
> **the.lost.one said:**
> Haha. Thats what I am saying. No clear text passwords. That is effective against a lot of people.

My reply was to those who said, "Oh, why are you worrying about show passwords button. Even if there were no clear passwords the person could install a keylogger." And I said that you need sudo password to do that which that person would not have. So some people said you dont need sudo to install keylogger. I find that odd since in windows you need admin level access.

You don't need admin level access in Windows either, believe me. Only if you want to install one system-wide (as opposed to only the user account you have accesss to), or hide it very well, which is exactly the same as it's in Linux

---

### Post by scaine on 2009-10-29
> **P4man said:**
> I just googled around a bit and found a keylogger. From its webpate:


Sounds like it doesnt require root to run, but I cant install it without putting sudo before the make install command


LKL needs sudo to install, because it logs everything to /var/log by default.  The Uberkey software I posted about only writes to std out, so it's a different story.

Google them though and you'll find that both are horrendously choppy in every day use unless you really know what you're doing.

Again, this thread isn't about keylogging, compromises, hacking or the like.  It's about temptation and opportunism of someone noticing an unlock PC and thinking "I wonder...?".  Seahorse could easily resolve this with a password prompt, but chooses not to.

I wonder why?

---

### Post by benj1 on 2009-10-29
> **the.lost.one said:**
> Is that possible and easy? I really doubt. I can't recall the exact details but I what I remember is that in Windows this particular issue of apps presenting as another has been dealt with. I think that there was an issue with software firewall in Windows that allowed a malicious program to say, "Hey, I am Firefox.exe, please allow me" and then it could run. But something changed in Windows or firewalls so that this is not the case anymore.

i suppose if you built it into the kernel, it would be able to stop one app masquerading as another, but seahorse/gnome keyring just uses an api and i dont see how you could prevent it, having said that i dont know how windows does it so i dont know, anyway the work around would just be to read the unencrypted keys directly 

> 
If keylogger cannot be installed without sudo, it means that keyring's *show password button* (or its willingness to give access to all passwords to every app) is the only way for the person to get the passwords. As far as physical keylogger or devices are concerned, those are obviously no where as stealthy and free as software keylogger.
a keylogger can be installed without sudo, im not as sure whether it would run without sudo (as i say ive never tried making one, i fairly sure tho that the reason sudo doesnt echo anything on password input is to defeat keyloggers).regarding the physical keylogger, how often do you check behind you pc? all you need is something to intercept the signal inbetween the keyboard and pc, regardless if someone really wanted to they could just reboot your pc into rescue mode to get root access and install a keylogger that way,and get your passwords etc.

---

### Post by P4man on 2009-10-29
> **scaine said:**
> LKL needs sudo to install, because it logs everything to /var/log by default.  The Uberkey software I posted about only writes to std out, so it's a different story.

Google them though and you'll find that both are horrendously choppy in every day use unless you really know what you're doing.

Again, this thread isn't about keylogging, compromises, hacking or the like.  It's about temptation and opportunism of someone noticing an unlock PC and thinking "I wonder...?".  Seahorse could easily resolve this with a password prompt, but chooses not to.

I wonder why?

I completely agree with you. 
Its like some weird "linux is perfect but its users suck" attitude.

---

### Post by the.lost.one on 2009-10-29
> **mcduck said:**
> They can be installed without "sudo" or any administrative privileges. *....**for that user only*, while installing anything system-wide requires root privileges.

Many programs don't require any specific installing and can simply be extracted somewhere and run that way. Logging key presses is simple and easy, and user level programs are able to read from keyboard so there's nothing preventing such program from working even if it's not installed system-wide.



I am very new to Linux so I don't understand its way of doing things yet. But I had the impression that ubuntu or linux would have every relevant security measure that Windows has and some more. If Windows can restrict installation of keylogger to admin level, why can't Ubuntu? Or rather, why it doesnt?


> **mcduck said:**
> Of course it's been argued that installing a keylogger or reading the passwords through other means is too hard for most of the people and thus it's not a concern (I disagree, although based on how many times a week I need to help somebody on these forums to change their keyring password I'm starting to feel that accessing the passwords through the Keyring Manager is too hard for most of the people.. :D)

Haha

---

### Post by benj1 on 2009-10-29
> **scaine said:**
> Fundamentally disagree - doing so would make the system slightly more secure.  Not "secure", but "slightly more secure" and would remove this thread from relevance because it fixes the scenario I posted about just there (about passerby seeing all your passwords while you're at the water cooler).

in that case lock the screen before you leave, they can still easily get the passwords another way, they still have access to all you private files.
you can come up with a what if scenario for everything, if the developers did something about every one, you would most likely have an unusable system that nobody would use

> 
But back to my my question - why all the animosity?  Nearly 300 posts of argument?  Over something easily fixed?  I've read EVERY post.  It's soul destroying to read and it's bad for the image of Ubuntu when an easily fixed security issue is defended to the death like this.

I just wanted to understand where all that defending is coming from.
its not animosity, its just a pretty central design decision of linux is not to make things appear more secure than they are, hiding the password would not make the system more secure, its security through obscurity, read the link i posted about pidgin, or the reply from the seahorse
dev they both say the same. if you want it to be actually secure, lock the screen, if windows hides its passwords, its not anymore secure, they may have an advantage of closed source and use lots of obfuscation but it isnt secure.

---

### Post by DodgeV83 on 2009-10-29
> **the.lost.one said:**
> I am very new to Linux so I don't understand its way of doing things yet. But I had the impression that ubuntu or linux would have every relevant security measure that Windows has and some more. If Windows can restrict installation of keylogger to admin level, why can't Ubuntu? Or rather, why it doesnt?

Their reasoning might be "If someone can get a keylogger on your system, they can probably also [insert something ridiculous here] so we won't lead you to believe your system is secure because [blahblahblahblahblah] lock your screen."

](*,)

---

### Post by DodgeV83 on 2009-10-29
> **benj1 said:**
> if the developers did something about every one, you would most likely have an unusable system that nobody would use

I doubt the system would break down if a password prompt were given any time someone wants to view the saved passwords.

:roll:

I believe the answer to the question was already given early on.  This is how the developers made it, if you don't like it, don't use their software.

*looks at recent marketshare numbers*

Looks like the people have made their choice

=D>

---

### Post by Keyper7 on 2009-10-29
> **the.lost.one said:**
> Those who are rigidly against any change have not been able to answer this simple question:
[INDENT] What is relatively more secure:
[/INDENT][INDENT] a) 9 out of 10 people can steal my passwords
b) 2 out of 10 people can steal my passwords
[/INDENT]

Because the question is misleading and does not consider the bigger picture. Of course the second answer sounds better, but you are conveniently ommiting the fact that the context is: such people are already logged in as *you*.

I can make the following question, what is relatively more secure:

a) people take 1 minute to steal your passwords
b) people take 10 minutes to steal your passwords

Following your logic, (b) is obviously the correct answer and thus we have a case for requiring 120 different passwords before opening up the keyring.

> **the.lost.one said:**
> Those who say "don't let them use it, if you don't trust" fail to appreciate the fact in real life an extremely large number of people are NEITHER absolutely trustworthy nor absolutely untrustworthy. We may trust a person with one thing (e.g. they wont install keyloggers) but not with another (e.g. if a password is right in front of them they might be tempted to use it). Also, you guys fail to realise that there is a big difference in professional thieves or determined hackers and opportunists. Opportunists can be everywhere but most people don't have people with scripting knowledge around them.

You are confusing "trustworthy" with "technically capable". One has nothing to do with the other. I have several friends who I'd let use my computer for five minutes and know that, if I had a file named my_bank_password.txt in the desktop, they would **not** open it. *That's why I consider them my friends in the first place*.

On the other hand, if I thought, even for a second, that a person would open that file, I would never let him use my account, period. I don't care if he's the most stupid, retarded, technically incapable person in the world who doesn't know how to double-click to open a file. He would not touch my account. End of story.

There is no such thing as "half-trustworthy". That's the concept I'm having more difficult to grasp when I see someone complaining about the current policy. Why doesn't anyone seem to have a problem with anyone being capable of *nuking your entire home directory with "rm -rf ~" (or better, opening nautilus, selecting everything, pressing del and emptying the trash)* if you leave your computer without locking your screen?

> **the.lost.one said:**
> It would be security through obscurity if it were the ONLY measure. It is an additional layer that we want that would protect us from 90% of the people. Thinking that a user would never ever forget to lock the screen is seriously flawed. We want a system where in the rare case we forget to lock the screen, we would still be protected from 90% of the people. Currently, our passwords are vulnerable to almost 9 out of 10 people, in case we forget to lock screen.

Bogus statistics. It's 9 out 10 people *who would be interested in it*.

> **the.lost.one said:**
> I hate the car analogy here (lol) but I have to say this. Some thieves are professionals and some are opportunists. Some professionals have jammers that would render the tracker you have installed useless. Does it mean tracking is useless just because a few can get past it? On top of that there are thieves:

(...)

We have different security measures for all these types and not JUST for the most advanced and professional thief.

And all of those are useless if you give the thief the key.

> **the.lost.one said:**
> If you think the *show passwords button* is  there to make the user lock the screen, why not have the passwords displayed ON the desktop background. That is thousand times more likely to make a person lock the screen. Seriously, tell me?

There's a difference between "it's that way because the user should lock the screen" and "it's that way to make the user lock the screen". You are missing the point.

---

### Post by the.lost.one on 2009-10-29
> **benj1 said:**
> i suppose if you built it into the kernel, it would be able to stop one app masquerading as another, but seahorse/gnome keyring just uses an api and i dont see how you could prevent it, having said that i dont know how windows does it so i dont know, anyway the work around would just be to read the unencrypted keys directly 

Only authorised apps should be able to access encrypted passwords. They should be allowed to access to only the passwords associated with them. Apps should not be allowed to masquerade as another. Since the passwords are required by apps only at the time of sign in of respective apps, the passwords should get encrypted again.

You may or may not know how to do it, I certainly don't. But I am sure can be done because I know some of it has been done elsewhere.

> **benj1 said:**
> a keylogger can be installed without sudo, im not as sure whether it would run without sudo (as i say ive never tried making one, i fairly sure tho that the reason sudo doesnt echo anything on password input is to defeat keyloggers).regarding the physical keylogger, how often do you check behind you pc? all you need is something to intercept the signal inbetween the keyboard and pc, regardless if someone really wanted to they could just reboot your pc into rescue mode to get root access and install a keylogger that way,and get your passwords etc.

Thats the point, how many people are roaming around carrying physical keyloggers in their pockets. Thats the whole point of our wanting this feature. Because most people can click a show passwords button and get passwords but are not able to do other stuff like keyloggers.

---

### Post by benj1 on 2009-10-29
> **the.lost.one said:**
> I am very new to Linux so I don't understand its way of doing things yet. But I had the impression that ubuntu or linux would have every relevant security measure that Windows has and some more. If Windows can restrict installation of keylogger to admin level, why can't Ubuntu? Or rather, why it doesnt?

as mcduck posted previously windows only needs a password to install it system wide, the same with linux.
linux does have every relevant security measure that windows has, it just doesnt consider security through obscurity to be relevant.

[QUOTE=P4man]
I completely agree with you.
Its like some weird "linux is perfect but its users suck" attitude. 
[/QUOTE]
its not a users suck attitude, it just credits them with some intelligence, if something isnt secure, it wont tell you it is.

how about i swap this around, windows doesnt show passwords, does that make it more secure? well you cant see it in the menu, but some one who know what they doing can see it.
result, people think their passwords are secure and so will happy enough to leave their system unlocked, yes it may stop 8/10 people snooping but what happens when the 5th person comes along who knows what theyre doing? yes youve lost your passwords.
linux on the other hand doesnt try to hide it the user knows its not secure so hopefully they lock it, then it is secure from everybody.
yes you could argue "but they dont know you can see passwords" the answer to that is education, plus if you say that then you have to accept that many others wont know either, so you back to the 8/10 people argument.
you could also say "what if they forget to lock it", what if i forget to lock my car, my house, shred my bank statements?

---

### Post by mcduck on 2009-10-29
> **the.lost.one said:**
> I am very new to Linux so I don't understand its way of doing things yet. But I had the impression that ubuntu or linux would have every relevant security measure that Windows has and some more. If Windows can restrict installation of keylogger to admin level, why can't Ubuntu? Or rather, why it doesnt?

Like I said, you can install one in Windows as well. You only need admin privileges to install one system-wide (to be bale to monitor all user accounts and the login password). Or if you want  to hide it so well that it can't be seen in the process list, for example.

For all basic keylogging tasks all you need is access to unlocked session: No matter if the OS is Linux, OSX or any Windows version.

Besides, you don't really even need to install anything for basic keylogging. I just tried, out of pure interest, if it's possible to log keyboard input with the basic tools already available by default. Seems quite easy, actually, and I'm not even a programmer and only have very basic shell scripting skills.. ( I used xev to read the keyboard, and xwininfo to get the window id of Firefox window to tell Xev what window to monitor. I'm sure there's more efficient ways to do this but these were the first tools that came to my mind and they were enough to log all keyboard and mouse input in Firefox into a text file. Enough to get all your website passwords..)

---

### Post by Keyper7 on 2009-10-29
> **DodgeV83 said:**
> I believe the answer to the question was already given early on.  This is how the developers made it, if you don't like it, don't use their software.

Trollishly distorting what people said won't get you anywhere.

The mailing list was pointed out several times, and developers are replying to questions there. The list is open to anyone who is interested in contributing to the discussion.

---

### Post by P4man on 2009-10-29
[QUOTE=benj]
how about i swap this around, windows doesnt show passwords, does that make it more secure? well you cant see it in the menu, but some one who know what they doing can see it.
result, people think their passwords are secure and so will happy enough to leave their system unlocked, yes it may stop 8/10 people snooping but what happens when the 5th person comes along who knows what theyre doing? yes youve lost your passwords.
linux on the other hand doesnt try to hide it the user knows its not secure so hopefully they lock it, then it is secure from everybody.
yes you could argue "but they dont know you can see passwords" the answer to that is education, plus if you say that then you have to accept that many others wont know either, so you back to the 8/10 people argument.
you could also say "what if they forget to lock it", what if i forget to lock my car, my house, shred my bank statements?[/QUOTE]

Im all for solving this problem fundamentally. But until such a solution is even on the horizon, a pragmatic approach to make stealing passwords a lot harder, if not impossible for 99% of the potential identity thieves out there, gets my vote.

If you dont want to give users a false sense of security then add a simple popup saying "warning, you need to enter you password to view your passwords, but that doesnt mean they are secure from keyloggers or other means. Always lock your screen blablablabl"

I find that a far better compromise than allowing easy identity theft by anyone.

---

### Post by benj1 on 2009-10-29
> **the.lost.one said:**
> Only authorised apps should be able to access encrypted passwords. They should be allowed to access to only the passwords associated with them. Apps should not be allowed to masquerade as another. Since the passwords are required by apps only at the time of sign in of respective apps, the passwords should get encrypted again.

You may or may not know how to do it, I certainly don't. But I am sure can be done because I know some of it has been done elsewhere.

the seahorse keyring is decrypted when you log in using your login password, so they arent encrypted whilst youre logged in

> 
Thats the point, how many people are roaming around carrying physical keyloggers in their pockets. Thats the whole point of our wanting this feature. Because most people can click a show passwords button and get passwords but are not able to do other stuff like keyloggers.
they dont need a keylogger to get passwords
its this simple [http://michael.susens-schurter.com/blog/2008/10/30/listing-all-passwords-stored-in-gnome-keyring/]("http://michael.susens-schurter.com/blog/2008/10/30/listing-all-passwords-stored-in-gnome-keyring/"), plus how would this feature defeat keyloggers, keyloggers log keys, not scrape screens.

---

### Post by Slim Odds on 2009-10-29
> **chrisccoulson said:**
> Also, remember the Pidgin **stores your account passwords in plaintext on your hard disk**. Pidgin doesn't use the keyring, and AFAIR the Pidgin developers aren't interested in doing this either. Empathy **does** store your account passowrds correctly though

pidgin stores the plaintext password in a file that is **only accessible to the user of the password**.

Just what type of problem do you have with that?

---

### Post by Keyper7 on 2009-10-29
> **Slim Odds said:**
> pidgin stores the plaintext password in a file that is only accessible to the user of the password.

Just what type of problem do you have with that?

There is a subtle yet important difference: the machine admin or a user with a live CD is able to read Pidgin passwords (if the home is not encrypted).

That does not happen with passwords in the keyring because they are encrypted.

That's why Pidgin devs recommend not to save passes at all.

---

### Post by benj1 on 2009-10-29
> **P4man said:**
> Im all for solving this problem fundamentally. But until such a solution is even on the horizon, a pragmatic approach to make stealing passwords a lot harder, if not impossible for 99% of the potential identity thieves out there, gets my vote.

If you dont want to give users a false sense of security then add a simple popup saying "warning, you need to enter you password to view your passwords, but that doesnt mean they are secure from keyloggers or other means. Always lock your screen blablablabl"

I find that a far better compromise than allowing easy identity theft by anyone.

the problem has been fundamentally solved, locking the screen.

plus i dont see how popping up a message when you want to view passwords would help if they dont intend to view them, a message on installation, or first login would be better.

plus why do you keep making reference to keyloggers, no amount of not showing passwords will help

---

### Post by DodgeV83 on 2009-10-29
> **Keyper7 said:**
> Trollishly distorting what people said won't get you anywhere.

Quote below:

> Have none of you read the security philosophy linked early in the thread?  That's the philosophy of the developers, and they aren't going to change it.  If you're really terrified of it, go to another OS.

---

### Post by benj1 on 2009-10-29
> **Keyper7 said:**
> There is a subtle yet important difference: the machine admin or a user with a live CD is able to read Pidgin passwords (if the home is not encrypted).

That does not happen with passwords in the keyring because they are encrypted.

That's why Pidgin devs recommend not to save passes at all.

plus the fact that if someone has that much access to your pc anyway, unless its properley secured they basically have access to anything they want anyway, including your keyring.

---

### Post by Keyper7 on 2009-10-29
> **DodgeV83 said:**
> Quote below: > Have none of you read the security philosophy linked early in the thread? That's the philosophy of the developers, and they aren't going to change it. If you're really terrified of it, go to another OS.

Nice try. But that person wasn't the only one who has replied to you. Trollishly *selecting* what *some* people said **is** trollishly distorting what people, *as a whole*, said.

---

### Post by the.lost.one on 2009-10-29
> **Keyper7 said:**
> Because the question is misleading and does not consider the bigger picture. Of course the second answer sounds better, but you are conveniently ommiting the fact that the context is: such people are already logged in as *you*.

I can make the following question, what is relatively more secure:

a) people take 1 minute to steal your passwords
b) people take 10 minutes to steal your passwords

Following your logic, (b) is obviously the correct answer and thus we have a case for requiring 120 different passwords before opening up the keyring.



Duh! It is always a matter time!!! What are you suggesting? Pray tell? To have either 120 passwords or just one? We want something in between.

By your logic one should have either one letter sudo passwords or 120. But the fact is that something in between like 8 to 16 are reasonable.

> **Keyper7 said:**
> You are confusing "trustworthy" with "technically capable". One has nothing to do with the other. I have several friends who I'd let use my computer for five minutes and know that, if I had a file named my_bank_password.txt in the desktop, they would **not** open it. *That's why I consider them my friends in the first place*.

On the other hand, if I thought, even for a second, that a person would open that file, I would never let him use my account, period. I don't care if he's the most stupid, retarded, technically incapable person in the world who doesn't know how to double-click to open a file. He would not touch my account. End of story.

There is no such thing as "half-trustworthy". That's the concept I'm having more difficult to grasp when I see someone complaining about the current policy.

Thats the whole point. Real life is different from the text book of computing. 

Extremely large number of people are not "absolutely trustworthy for absolutely everything". Different situations, objects etc involved and the levels of risk one is willing to take with regard to the situation, object and the person being evaluated, could mean different evaluations of trustworthiness. 

For example, I could trust a coworker with my pen but if I give it to a stranger I would keep him in my sight lest he runs away. Still, I would not trust just any coworker with 1,000 dollars. My close friend, I can. And yet, I might not want that friend to know about my sensitive family issues. I could trust all of this with my family and yet I might not want them to know about something very naughty that only my closest buddy knows.

> **Keyper7 said:**
> Why doesn't anyone seem to have a problem with anyone being capable of *nuking your entire home directory with "rm -rf ~" (or better, opening nautilus, selecting everything, pressing del and emptying the trash)* if you leave your computer without locking your screen?


Because that is much harder to get away with. Plus it is not as tempting as stealing passwords and then stalking mails.

---

### Post by P4man on 2009-10-29
> **benj1 said:**
> the problem has been fundamentally solved, locking the screen.

Thats hilarious.

> 
plus i dont see how popping up a message when you want to view passwords would help if they dont intend to view them, a message on installation, or first login would be better.

**You** were the one saying linux doesnt want to give a false impression of security. Fine, I can live with that. If putting a password on seahorse gives that false impression (which would be *your* point against setting one, or did I misunderstand you?) then add the popup to undo that false impression. Then what is the problem? You are happy, I am happy and a lot less identity thefts will occur.

> 
plus why do you keep making reference to keyloggers, no amount of not showing passwords will help

Again, because that is* your argument* against a password on seahorse. Its true a password on seahorse doesnt save you from keyloggers or other means, and its not a substitute to locking your screen, so again add that message to the seahorse password popup (or elsewhere too if you want) to avoid that false impression. Im not against educating users at all (especially in a popup one would see no more than a few times per year,)

---

### Post by scaine on 2009-10-29
300+ posts in two days is animosity.  This thread is horrendously off-topic now with talk of keyloggers and such and it's being kept alive by about 4 posters with utterly opposing and completely blinkered points of view, my own included.

There is not one argument you can present that makes me comfortable about this utter lack of security in Ubuntu.  Someone already posted earlier that the same is true of network-manager - true.  Worse, since I use PEAP for my wireless here at work, anyone with 45 second of access to my unlocked laptop here at work will now have my considerably powerful active directory password!

Completely and utterly shocking.  There is simply NO DEFENCE for such an utter lack of basic security.

To summarise,

No, adding a password prompt to view stored passwords on my system won't fully protect me if I'm stupid enough to leave my work laptop unlocked at my desk for 5 minutes, but it WILL add another layer of security and remove temptation from the vast majority of those who might otherwise have a go.

Now, thanks to this thread, I have to go and remove Seahorse and ensure that Network Manager doesn't remember my PEAP WIFI password.

Why?  Because I live in the real world and there's a small risk that I might just be stupid/distracted enough to leave my laptop open unlocked.

Diabolical.  And to those defending this?  Please stop.

---

### Post by DodgeV83 on 2009-10-29
> **Keyper7 said:**
> Nice try. But that person wasn't the only one who has replied to you. Trollishly *selecting* what *some* people said **is** trollishly distorting what people, *as a whole*, said.

/sigh

:roll:

Here is my quote again:

> I believe the answer to the question was already given early on.

Please show me, where in this quote did I imply this was the answer given by the *whole*, or even the *majority* of respondents in this thread?

I simply said this was the *correct* one.

I usually loathe correcting people on simple mistakes, but you are inferring things which simply weren't said and I refuse to be attacked because you misread a sentence.

Can we get back on topic please? :popcorn:

---

### Post by the.lost.one on 2009-10-29
Lets just agree to disagree. At any rate, I am out of here.

---

### Post by DodgeV83 on 2009-10-29
> **the.lost.one said:**
> Lets just agree to disagree. At any rate, I am out of here.

Me too, but I reserve the right to come back with a "!Boom Baby!", when this is finally fixed :)

---

### Post by scaine on 2009-10-29
> **DodgeV83 said:**
> Me too, but I reserve the right to come back with a "!Boom Baby!", when this is finally fixed :)

I'm also unsubscribing.  I think someone posted a discourse with the developer list earlier on?  I'll maybe check back from time to time to see if there's been any movement with that.

---

### Post by benj1 on 2009-10-29
> **P4man said:**
> Thats hilarious.

how ???
> 
**You** were the one saying linux doesnt want to give a false impression of security. Fine, I can live with that. If putting a password on seahorse gives that false impression (which would be *your* point against setting one, or did I misunderstand you?) then add the popup to undo that false impression. Then what is the problem? You are happy, I am happy and a lot less identity thefts will occur.

putting a password in seahorse is secure, in as far as its encrypted when you arent logged in, when you are logged in it isnt, it is available to everything, in that case pretending it isnt available is giving a false sense of security
> 
Again, because that is* your argument* against a password on seahorse. Its true a password on seahorse doesnt save you from keyloggers or other means, and its not a substitute to locking your screen, so again add that message to the seahorse password popup (or elsewhere too if you want) to avoid that false impression. Im not against educating users at all (especially in a popup one would see no more than a few times per year,)
i didnt start the conversation on key loggers, as i have posted before a keylogger logs keys, it doesnt read your screen, in the case that i had a keylogger, i would prefer to have the passwords easily available so i can copy and paste them rather than typing them in.

---

### Post by P4man on 2009-10-29
> **benj1 said:**
> how ???

putting a password in seahorse is secure, in as far as its encrypted when you arent logged in, when you are logged in it isnt, it is available to everything, in that case pretending it isnt available is giving a false sense of security

Sigh. how can it pretend being safe when it tells you in a big popup its NOT safe? This is getting ridiculous. You're promoting deliberately decreasing the security of the identity of the majority of people in the majority of scenarios just to avoid misleading a tiny minority that makes wrong assumptions and cant read the contents of a dialogue. Thats a GREAT approach to security.

Ill tell you this, your avatar is fitting.

Im out of this discussion too, might as well argue with a brick wall

---

### Post by snkiz on 2009-10-29
This is my farewell as well this thread is out of hand. I'll leave with this:
[http://live.gnome.org/GnomeKeyring/SecurityPhilosophy]("http://live.gnome.org/GnomeKeyring/SecurityPhilosophy")
To summarize Gnome has two classes of attack passive and active. The way things are now will protect you from passive attack while preventing a "security theater" Gnome considers this issue an active attack witch they admit we the user are not protected against. Gnome claims that there is no real way currently to protect against active attacks without creating a "security theater" The issue is not an easy fix.

I believe that the aforementioned message with the password prompt would satisfy the requirement without creating a "security theater" in the interim while a hardened solution is being worked on.

---

### Post by Keyper7 on 2009-10-29
> **the.lost.one said:**
> Duh! It is always a matter time!!! What are you suggesting? Pray tell? To have either 120 passwords or just one? We want something in between.

Eh, no. You missed the point entirely.

I was merely pointing out that giving two choices without giving the full context is pointless.

The full context in my case: without considering the fact that I'm proposing 120 passwords, option (b) is obvious. Considering it, it's not.

The full context in your case: without considering the fact that you are only talking about people *already logged in as you* in the first place, option (b) is obvious. Considering it, it's not.

> **the.lost.one said:**
> Extremely large number of people are not "absolutely trustworthy for absolutely everything". Different situations, objects etc involved and the levels of risk one is willing to take with regard to the situation, object and the person being evaluated, could mean different evaluations of trustworthiness.

I agree. And in the current case, it simply means locking the screen or not.

> **the.lost.one said:**
> For example, I could trust a coworker with my pen but if I give it to a stranger I would keep him in my sight lest he runs away. Still, I would not trust just any coworker with 1,000 dollars. My close friend, I can. And yet, I might not want that friend to know about my sensitive family issues. I could trust all of this with my family and yet I might not want them to know about something very naughty that only my closest buddy knows.

This all applies to the current policy. You trust, let them use your account. You don't trust, create a guest account. Can you forget to lock the screen? Sure. As you can forget money over the table, you can forget your diary open in an embarassing page and you can fail to notice someone overhearing when confiding to a friend. But I doubt you get all paranoid over that.

> **the.lost.one said:**
> Because that is much harder to get away with. Plus it is not as tempting as stealing passwords and then stalking mails.

In your opinion and in your case. If you want to claim you are worried about security, treat data and passwords with equal importance because for a lot of people data is *more* important than passwords. Otherwise you are being unfair.

---

### Post by Keyper7 on 2009-10-29
> **DodgeV83 said:**
> Please show me, where in this quote did I imply this was the answer given by the *whole*, or even the *majority* of respondents in this thread?

I simply said this was the *correct* one.

And it was *not*, as evidenced by *other* responses. That's my point.

> **DodgeV83 said:**
> I usually loathe correcting people on simple mistakes, but you are inferring things which simply weren't said and I refuse to be attacked because you misread a sentence.

You were claiming something that isn't true, and insulting the developers in the process.

---

### Post by michaelzap on 2009-10-29
> **P4man said:**
> If you dont want to give users a false sense of security then add a simple popup saying "warning, you need to enter you password to view your passwords, but that doesnt mean they are secure from keyloggers or other means. Always lock your screen blablablabl"

I find that a far better compromise than allowing easy identity theft by anyone.

+1

This a) solves the real-life situations that many people have described where non-technical snoopers view passwords in clear text, b) takes the opportunity to educate users as to appropriate security measures, and c) is entirely consistent with the much-cited security philosophy of not engaging in "security theater".

This does not have to be a zero-sum game, folks. A solution like this takes everyone's viewpoint into account and makes Ubuntu better and its users more informed in the process. Isn't that what we should be striving for, instead of "winning" the argument?

---

### Post by scorp123 on 2009-10-29
> **scaine said:**
>  There is not one argument you can present that makes me comfortable about this utter lack of security in Ubuntu. And you think any other OS is better??? Just give me 5 minutes alone with your running Windows desktop and I will have all the passwords from there too, no matter if they were protected by "********" fields or not.

It's a simple fact: As soon as someone has physical access they can pretty much do whatever they want. If you are so "nice" and leave your desktop unlocked .... even better. And the OS doesn't even matter.

> **scaine said:**
>  anyone with 45 second of access to my unlocked laptop here at work will now have my considerably powerful active directory password!  Of course. Duh. And it doesn't even matter if Linux or Windows: Someone with the right knowledge will also easily get those passwords out of a Windows session. Been there, done that.


> **scaine said:**
>  Completely and utterly shocking. There is simply NO DEFENCE for such an utter lack of basic security.  There is no defence for leaving your laptop unlocked when you walk away. Ctrl+Alt+L ... taddaaaa, Screensaver + screen is locked. What's so hard about that? You don't go out of your house and leave it unlocked? How shocking: Unlocked houses are insecure and might invite intruders!! Big news, LOL.

> **scaine said:**
>  Now, thanks to this thread, I have to go and remove Seahorse and ensure that Network Manager doesn't remember my PEAP WIFI password.  I will simply walk to your laptop, use the "killall" command plus a few extra-parameters and send your Network-Manager a few nice signals and make it drop a memory dump .... and while you're away I will upload that memory dump to "somewhere else". You will return to your laptop and not even realise what just happened. In the meantime I will sieve through that memory dump and obtain your password that way .... **So removing seahorse won't make you safer than before. Leaving your laptop open would still compromise you and it would still be a very stupid thing to do. ** An intruder would just have to change their attack vector, but that's about it. With the laptop being open they can pretty much do what they want.

> **scaine said:**
>  Because I live in the real world  Me too. I always lock my laptop. **[COLOR="Red"]ALWAYS.[/COLOR]** [COLOR="Red"]Whenever I catch my IT apprentices leaving their machines unlocked I _FORMAT_ those machines so they have to reinstall.[/COLOR] So far I only had to do this once. Those youngsters are quick learners. Why aren't you?

> **scaine said:**
>  and there's a small risk that I might just be stupid/distracted enough to leave my laptop open unlocked. Well ... if you trust your colleagues then this probably isn't a problem. And if you don't have an admin like myself who would mercilessly format your laptop in order to punish and educate you .... Even better. But then again: Maybe you should work on your concentration issues and focus more on what you're doing and why in the here and now?

---

### Post by humphreybc on 2009-10-29
Damn!! There have been over ten pages of replies since I last looked before I went to bed last night. I'm not going to read them, but it seems that the debate has gone waaayy downhill.

Putting all arguments about sudo/security philosophy/linux/windows and everything else aside, I do believe that just a simple change of location for the Passwords and Keyrings application (Seahorse) to Preferences would hopefully make it less obvious.

If nothing else is going to be done, then that's the least they can do. At least everyone's happy then.

---

### Post by P4man on 2009-10-30
Rather than arguing endlessly here, I wrote the below email to the seahorse mailing list. I did so before I subscribed to it, so can anyone who is also subscribed confirm he or she received it? This is what I sent:

> Hello everyone,

First of all allow me to express a big THANK YOU for all the hard work you guys put into making gnome one the best desktop environments out there.

But even the best can be improved. You are probably aware there is some controversy over the fact seahorse allows a user to view clear text passwords without any authentication. There is a 300+ post on the topic on the ubuntu forums which I would advice you not too read unless you're terribly bored and like reading circular arguments about car analogies. Instead, let me try and summarize the relevant arguments I have been able to find, and humbly propose a solution.

People defending the current implementation have a few valid arguments. They claim hiding passwords that reside on disk unencrypted does not add real security, only perceived security. They argue such false sense of security ("security theatre" seems to be the popular phrase) actually diminishes security and users should be taught to lock their screens instead. They also argue physical access =  root access anyway, and apps like pidgin store passwords in clear text by design for the above reasons. Some add more nonsensical arguments that I will spare you.

People who object to the current implementation (which includes yours truly) argue that the current implementation makes it far too easy for anyone even with no computer skills to obtain someone's identity. It takes less than 10s to click a few menu's and reveal someone's wifi or email password, which is a great security breach (far more than just being able to read emails while the owner is away from his screen). Locking the screen is a good habbit but in real life people will not always do this, and even a screensaver / auto lock is not a good solution as that would take several minutes during which a curious collegue could grab your mouse in your absense and obtain your passwords without you ever knowing.

Now, I can  appreciate the philosophy of not giving false sense of security and security through obscurity is not a solution either.  Requiring a password to view clear text passwords stored in the keyring does not protect a user from more sophisticated attacks and could indeed increase the perceived secuity. Therefore I would suggest a pragmatic solution that I think should satisfy everyone. I would suggest passwords in seahorse are not visible without re authentication of the user, but at the same time I would use the password dialogue box to warn the user that despite this authentication request, his passwords are NOT secure or encrypted as long as he is logged in, and he should lock his screen and/or close the keyring to avoid identity theft.

To me this sound like a fairly simple solution that will render identity theft by regular desktop users a whole lot less likely, while at the same time educating the user how to protect himself from more skilled potential identity thieves who know how to install a keylogger or where to find on unscramble stored passwords. It secures users against the majority of potential identity thieves, it provides no false sense of security (quite on the contrary) and it educates the users. Everyone wins :)

I hope you will consider this solution,

Bob.

I hope the seahorse developers are more prone to reason and pragmatism then some posters here.

---

### Post by snkiz on 2009-10-30
P4man this is for you not here to argue any more. I just got this from the mailing list

> 
 This is really a gnome-keyring question. Seahorse is no different than
> any other application on the Desktop when it comes to accessing
> passwords in the keyring.
>
> gnome-keyring-daemon has a very hard time differentiating between
> different applications.
>
> FWIW, I'm sure you've already read the security philosophy here:
> [http://live.gnome.org/GnomeKeyring/SecurityPhilosophy](http://live.gnome.org/GnomeKeyring/SecurityPhilosophy)
>
> The first and foremost 'real' thing we can do, to make all these
> security dreams a reality, is help Linux get a concept of signed
> applications (think iPhone, Mac OS) ... Or some other way to
> differentiate between applications, or at least applications running in
> different security contexts.
>
> Vertigo wrote:
>> I would suggest passwords in seahorse are not
>> visible without re authentication of the user, but at the same time I would
>> use the password dialogue box to warn the user that despite this
>> authentication request, his passwords are NOT secure or encrypted as long as
>> he is logged in, and he should lock his screen and/or close the keyring to
>> avoid identity theft.
>
> Who does this reauthentication? Should seahorse lock and then try to
> unlock the keyring? Or is gnome-keyring supposed to somehow identify
> seahorse and treat it differently?
>
> Obviously anything done in seahorse would be of absolutely no
> consequence to any other password manager.
>
> Cheers,
>
> Stef

see its not a simple problem hopefully they see the wisdom of an interim solution, I'm going to try to reason it out with them as well.

---

### Post by P4man on 2009-10-30
Yeah Im getting it too as Im subscribed now. 

FWIW I never claimed the technical implementation was easy (I got no clue), but thats no reason to trivialize the issue or ridicule a possible solution or pretend there is no issue because linux is perfect and its all the users' fault for not locking the screen.

Anyway Ill reply on the mailing list and perhaps repost it on the gnome-keyring mailing list if it turns out that is the better place to implement such a concept.

---

### Post by snkiz on 2009-10-30
This was my response:
>  
 After a lot of reading I can see this is a real concern for gnome,
and a truly secure solution will require a lot of work. How you guys
decide to do that is way over my head. (though references to that
locked down piece of crap the iphone send chills.)
 I can tell you this though Gnome's policy of education as a first
line of defense, while noble and probably the best solution. Has not
been implemented very well to this point. As an example I can tell you
I've been using gnome for four years and I just found out (after
participating in the debate on Ubuntu forms.) what seahorse is and how
it works.
 I and a number of people believe that while confirming your password
to view passwords in seahorse is by no means secure or a permanent
fix. It will accomplish two things, one it will stop identity theft by
opportunists who have no real technical knowledge beyond point and
click. Two it would give Gnome an opportunity to educate the user on
best practices with security in a gnome environment.
 Until we have a unified security solution I believe its imperative
that we do everything we can to meet the users expectations while
still adhering to the Gnome philosophy.

---

### Post by P4man on 2009-10-30
FYI: the reply to my mail, which you quoted, was CC'ed to the gnome-keyring mailinglist. you may want to subscribe there as well.

---

### Post by snkiz on 2009-10-30
Thats the one I signed up to in the first place. not sure how I ended up there Truth be told I'm new to mailing lists, never had a need before now.

---

### Post by Keyper7 on 2009-10-30
I applaud you both, P4man and snkiz, for taking a more active instance in this issue. As you already know, this is a not a security issue for me, but if it's for you, by all means *keep talking to the developers*. This is what community development is about. Much better than a "since this is obviously a bug, I won't discuss with the developers because they will eventually see the light" approach. I'll read the threads as well and hopefully everyone will be satisfied at the end.

---

### Post by talent03 on 2009-10-30
This thread is a joke. I am sorry so many of you are uncomfortable keeping your computer in your own hands. Here is what I do with my computers.

laptop - lock screen when leaving or set to standby(close the computer) which also locks the screen. Someone comes and says hey can I use your computer... sure *click on guest*. Gf has her own account.

Desktop - lock screen when leaving or set to standby which also locks the screen. Someone comes and says hey can I use your computer... sure *click on guest*. Gf has her own account. When I am away and people use my computer, I leave an account sticky on the monitor.

BIG DEAL. I am really sorry many of you can not be masters of your own computer. If security really mattered to you, this wouldn't be that hard. Welcome to the world of linux, where we actually use the accounts unlike windows users.

/trolling

---

### Post by jonthysell on 2009-10-31
It's a matter of options, gnome-keyring giving you the option of saving certain passwords for convenience. Issues arise when people either explicitly tell a program it can save the password, or when a program just assumes that it can and does so silently.

I knew for years that pidgin saved passwords in clear-text, so I took the OPTION of not saving my account passwords. I understood it meant the inconvenience putting it in every time I started the app.

Almost every app I use that CAN save passwords, gnome-keyring or not, asks me at some point whether I want to save my password. Evolution, SSH in Nautilus, wireless network keys, firefox. It's an option I can choose not to use.

But now that Empathy is the default im app in 9.10, I thought I'd give it a whirl instead of pidgin. But I don't recall ever giving Empathy permission to save my passwords, but it keeps doing so. Maybe I did at some point, so my question is, how can I get it to stop? Other programs have easy preferences for clearing saved passwords, some box to uncheck, something, anything! But with Empathy I can't get it to stop remembering.

The other issue I see (at least according to the current design supporters) is that the focus is on a single machine with multiple users: each user has their own silo of very important data stored locally, and operations that could affect the other users are given more security hoops to jump through (requiring elevated privledges, etc).

And that's a good model, if all you do is run apps installed on your machine, keeps documents locally, and have very important files locally. Then Linux excels, with disk encryption, and sudo/root, etc. It's a good model for keeping the machine running and keeping the other users from being naughty with each other's stuff.

But this is crazy to me:

[QUOTE="mcduck"]Is it really that hard to accept that yes, the user does have a part in maintaining the system's security. Compromising the security at larger scale yourself (your whole user account) and then complaining that the system doesn't protect some minor component (passwords stored inside that account) seems quite backwards to me.[/QUOTE]

Who on here is so important that the "whole user account" on their local machine is more important and the passwords stored inside that account are just "some minor component"? I'm sorry, but my online banking password, hell even my email password, is way more important IRL than any files I have on my computer.

I think for 90% of casual users, the files may have sentimental value at best. I know I would be pissed if someone messed with my "oh so precious files", but really, it's a localized issue. A good hard drive crash can ruin your files. You backup, or it's on you.

And for actual important documents, on or off the computer, people are responsible for their security. Means using encryption, or a locked filing cabinet. But again, it's on you. Really, anything that is important I take the time to store securely.

But I use a lot of services on and offline. Now I'm more careful than most (no apps save passwords, no password used twice, all long gibberish strings, all saved in keepass), but that's because I recognize that my accounts are what could really screw with my life. if someone else got a hold of them.

And the issue is that screw the local machine security, who cares if some hacker can steal my hard drive and get my files, as long as my actually precious passwords are as safe as possible, that's what I want out of a secure OS.

Steal my laptop, and I'll know right away to start making calls and putting blocks on things. Take my bank password, and you can go away from my local machine, and at your leisure, take my money and screw me up in real life, and I won't even know I've been compromised until you've got it all planned out.

No security is impossible to break, it's just a matter of time. So I want to raise the bar. To stop the guys with intent (the guy who hacks my system, runs an app or script while I forgot to lock my screen, or jacks my laptop), I use encryption, cause that's the best coverage I can hope for when my machine is that compromised.

The problem that the OP states I think is still a valid one, because even if I'm covered the best I can from bad guys with the intent to get my info, the bar for "lookie-loos" may be much lower, but it's not null. I don't care that this whole seahorse issue doesn't stop people with intent and know what they're doing, but right now it leaves the bar at null for when you forget to lock that screen, and any idiot can see what I've saved in the keyring (which is nothing, now that I know about it, but that's the issue, education).

I say that people need to be better educated on what assumptions and expectations linux makes (like that once you're logged in, it's you, so we won't hide the passwords you've saved in your keyring). Maybe it's to undo the obscurity that they're used to when coming from another OS.

And maybe that means being a little more explicit about telling users that when they check that box to save the password, that a person with intent, on your logged in box, can get those passwords in a snap.

But at no point should we have to say to the average user: "Netbook stolen (by pro theives or opportunists) yet locked: you're out $300 and any files you didn't encrypt (your fault, we made it easy in the installer), but you at least know about it, and can work to preserve yourself. Netbook left logged in an unattended for less than 30 seconds, and any idiot who can read the word 'password' and recognizes what a key looks like can have at your credit, your life savings, and all as a surprise to you in the future. Sorry we didn't explain to you what saving your passwords meant, but really, it's more secure that way, even if you can't pay your rent now."

(Yes, I recognize there are holes in what I've said, particularly regarding keyloggers and such, but at this point, I imagine this post has wandered for too long and no one's going to read it anyway.)

---

### Post by aikiwolfie on 2009-11-01
There's a lot being discussed in this thread, some of which seems to be going way off in a wild tangent.

[list][*]First and foremost. Can another user see my passwords when I'm logged out?


[*]Secondly. Will adding another prompt for a another password make the system that much more secure? Remember Windows Vistas constant nagging? Are we going down that road?


[*]Thirdly. Will this new password prompt use the users existing account password or a new password for the Gnome Key Ring?
[/list]
Security is important. Unfortunately security needs to be balanced with usability. At this point in time I would suggest not using the Gnome Key Ring app and just remember your user names and passwords for things like MSN and Yahoo Messenger. It really would be a lot safer. No matter how secure these password managers are. They're never going to be impenetrable.

It also seems to me that the level of security being asked for in this thread could be achieved by simply following what has long been considered best practice. Do things like locking the screen when you step away from the PC. It's such a simple thing to do.

Don't let other people use your account. Ubuntu supports multiple user accounts by virtue that it's a Linux based multi-user OS. Use it to it's potential. Create accounts for the other people that share the PC.

---

### Post by Agent ME on 2009-11-01
> **aikiwolfie said:**
> [list][*]First and foremost. Can another user see my passwords when I'm logged out?[/list]
No, the password files have permissions set so they're completely exclusive to your user account.
And even if someone booted into the system with a LiveCD or otherwise got around the permissions - I believe the passwords are encrypted by your user account password, so they still won't be able to get into them.

> **aikiwolfie said:**
> Security is important. Unfortunately security needs to be balanced with usability. At this point in time I would suggest not using the Gnome Key Ring app and just remember your user names and passwords for things like MSN and Yahoo Messenger. It really would be a lot safer. No matter how secure these password managers are. They're never going to be impenetrable.
What does "secure" mean for a password manager? I believe it encrypts your passwords so they're only accessible when you're logged on. That's what secure is to me at least.

I guess to the topic creater, not being able to read the passwords out of it equals secure, but that's rubbish because the programs that use the keyring need to read the passwords out. That's the whole point of the password manager. Not giving a user interface to directly deal with the passwords is just silly obscurity, making users think they're more invulnerable than they really are.

> **aikiwolfie said:**
> It also seems to me that the level of security being asked for in this thread could be achieved by simply following what has long been considered best practice. Do things like locking the screen when you step away from the PC. It's such a simple thing to do.

Don't let other people use your account. Ubuntu supports multiple user accounts by virtue that it's a Linux based multi-user OS. Use it to it's potential. Create accounts for the other people that share the PC.
Exactly. Ubuntu can even be set to lock your screen automatically when the screensaver comes on. Ctrl+Alt+L is the quick key combo to lock your screen.

---

### Post by P4man on 2009-11-01
> **aikiwolfie said:**
> There's a lot being discussed in this thread, some of which seems to be going way off in a wild tangent.

[*]First and foremost. Can another user see my passwords when I'm logged out?

No. No one claimed otherwise.


> [*]Secondly. Will adding another prompt for a another password make the system that much more secure? Remember Windows Vistas constant nagging? Are we going down that road?

define "much more secure". Against a skilled or motivated hacker? No, not at all. Will it help take away an open invitation for an opportunist college to steal your identity? Yes, I think so. I've railed against analogies, but to make one myself: a burglar alarm or locked front door doesnt protect against professional thieves, but that's hardly a reason to leave the front door unlocked and put your savings on the dinner table. A locked front door is no real security, but it decreases the likelyhood of an opportunity thief walking in.
> 
[*]Thirdly. Will this new password prompt use the users existing account password or a new password for the Gnome Key Ring?

How often do you view the clear text passwords in seahorse? Probably never. lets be generous and say once per month. Entering a password once per month extra compared to the fact most of us do it at leat 10x per day anyhow seems like a very small price to pay. Heck, I dont even see a real need for seahorse to display the passwords *at all*. If it lets you change them thats good enough.



> Security is important. Unfortunately security needs to be balanced with usability. At this point in time I would suggest not using the Gnome Key Ring app and just remember your user names and passwords for things like MSN and Yahoo Messenger. It really would be a lot safer. 

And how does that affect usability? Having to enter 2 or 3 passwords every boot or login vs once per month.
> 
No matter how secure these password managers are. They're never going to be impenetrable.


As long as they dont pretend to be, thats fine by me. But if the best use of a password manager a la seahorse is to steal someone else's passwords rather than managing your own, I think something ought to change.

> It also seems to me that the level of security being asked for in this thread could be achieved by simply following what has long been considered best practice. Do things like locking the screen when you step away from the PC. It's such a simple thing to do.

No its not. First of all, a bug in Karmic prevents me from locking my screen currently. But that aside, the usability trade off gets tremendously worse here since you are asking probably a dozen or more times per day to lock the screen manually **and** re enter your password when you get back. Im asking for once per month (if that much). 

Now you may argue that not locking the screen still provides a window for the skilled hacker, and I agree, so lets educate the user to not rely on a password on seahorse to protect his identy, but lets lock that door anyhow.

Lastly the reality is sometimes you dont think of locking the screen, or you dont have the time as you react to something urgent or panic or you expect not to be away from your screen as long or far as you thought.

The weakest link in security is almost always the user and depending entirely on the user doing something no one does all the time is per definition bad security.

anyway we can argue this ad infinitum. Im just happy that the gnome developers seem to acknowledge this is indeed a problem and not just "user error". unfortunately a solution seems fairly difficult, but that is not a reason to trivialise the problem or blame the end user

---

### Post by Locke_99GS on 2009-11-02
I agree with P4man ^^^ completely. I don't have anything to add to this thread that hasn't already been mentioned. My opinion is known.

---

### Post by witeshark17 on 2009-11-02
When my system is prompted from sleep or booted up, there is no desktop; there is only a password entry field and some options such as "leave message" "switch user". Maybe some settings need a look. Also, my system has a guest user option with very low permissions for when you may be suddenly asked to loan a look at something on the system called "guest session".

---

### Post by snkiz on 2009-11-02
> **witeshark17 said:**
> When my system is prompted from sleep or booted up, there is no desktop; there is only a password entry field and some options such as "leave message" "switch user". Maybe some settings need a look. Also, my system has a guest user option with very low permissions for when you may be suddenly asked to loan a look at something on the system called "guest session".

man 36 pages of posts and *that* is *all* you have to add? what are you 12?

---

### Post by witeshark17 on 2009-11-02
> **snkiz said:**
> man 36 pages of posts and *that* is *all* you have to add? what are you 12? It's a statement of fact, so that's all you can be critical of; that would make your post the pointless one...

---

### Post by Locke_99GS on 2009-11-02
Calm down guys; this thread has been mentioned in several blogs, Linux Magazine, and elsewhere. It is getting a lot of attention. Could we please keep this on topic?

---

### Post by bigsuccess on 2009-11-02
From a usability perspective I can almost see why you would want another password there, however this is a misconception of the dynamics of the security practice that *nix based systems are based on and is an anxiety stemming from Windows' ad-hoc security approach based on a single-user environment. That is to say it's not in itself a bad idea to password seahorse, it's just that it's ineffective and useless at best and dangerous and mis-leading at worst.

In the single-user world everyone has access to the same base security structure, the same computer, the same hardware. So you put passwords on sensitive things so only the admin persona can access them. This is the Windows styled kind-of UAC approach..

In the multi-user world everyone is different. The user logged in is master of their own stuff, not other peoples. The keychain manager is invented so the user doesn't have to re-type their passwords and instead has a master password on the keychain manager itself to be able to access it. Everything (or most things) are encrypted. In this environment, not surprisingly, when you login to the operating system you also login to this keychain manager and unlock all your passwords so your applications can use them; wifi connector, email, etc etc.



So, with that in mind the reason seahorse shows the passwords is it simply reflects what your applications can see when you're authenticated (logged in). In other words when you're logged in your passwords are available. Now, if I'm a power user and my apps have access to my passwords, I do too. As the user I want to see what my apps can see at the very least and sometimes more. So if my keychain is unlocked because I've logged on I want to see the passwords my applications can see.

This is where it gets tricky, because I don't want other people to see them and steal them, but I don't want to type them in every time either. I think this is the crux of the argument that has developed in this thread.


What the coders/more computer savvy people here are saying is that it's pointless to put a password on seahorse because once you're logged in, any app has access to those passwords because you've already proved you're you. So to put a password on seahorse is not effective, simply because at the security level those passwords are still available to you and your applications.

The result of that is that you get asked for a password when admin-ing things but the guy who's stealing your passwords with a script doesn't (because you've already logged in). The by product is that the legitimate user has less explicit/visible access to their system than what the security allows for. That's inherently bad, as you want to keep the representation of security to the legitimate user the same as it is in actuality/availability.

I think it's telling that the seahorse developer said he's not reading the thread and put the link to the keychain philosophy. In my view, because it's an ignorant argument. By linking the philosophy he was saying if you understand this you will understand why it's an ignorant argument.

Once the environment is clear the real options in the *nix environment are also clear - (and have been mentioned); use another keychain for those passwords, type in all your passwords manually, or lock your computer.

When in rome... ..

---

### Post by prshah on 2009-11-03
> **bigsuccess said:**
> seahorse shows the passwords is it simply reflects what your applications can see <snip> So if my keychain is unlocked because I've logged on I want to see the passwords my applications can see.

once you're logged in, any app has access to those passwords because you've already proved you're you. <snip> those passwords are still available to you and your applications.


I don't think (I am not sure) that all/any applications are allowed access to ALL passwords in the keyring. To get a password from the keyring, they need to ask for a specific resource; I don't believe there is any way to enumerate and access all stored passwords.

Again, I am not sure about this; if in fact, applications can access/enumerate ALL passwords in the keyring then this is a (IMHO) major security risk; while currently linux does not have malware, I don't believe that it is risk-free; it simply has not generated enough interest in the hacker/malware community. This will change, and linux will be just as badly (if not more) affected as windows; since current malware depends more on social engineering than hack-bypassing security restrictions. If such a malware application is developed, it can just store a password in the keyring to gain access to all a user's passwords. So, I doubt that applications have access to ALL passwords stored in a keyring.

---

### Post by scaine on 2009-11-03
Once again, this isn't about passwording Seahorse, nor the keyring, nor is it about a dedicated hack attack and how to protect yourself against such.  It's been said before and it's largely true - if someone has physical access to your machine, you've lost.

This is about Seahorse NOT showing passwords in the first place, as P4man asserts above.

It's about making life difficult for an opportunistic over-the-shoulder situation, or when you've got your back turned from your (perhaps stupidly) unlocked machine.

I've relayed such to the relevant mailling lists.  All this talk of ultimate security, hacking, loggers, or UAC is absolutely spurious.

This could be a simple fix and if done correctly, one that NO-ONE will notice, but that will render opportunistic threats much more difficult.

Neil.

---

### Post by QPrime on 2009-11-03
An unlocked keyring does not imply that all applications will have access to all passwords.  There are security controls to prevent this and access to keyring elements are protected on a per-application basis (remember the "Deny", Allow Once", " Always Allow" dialogue that pops up?).  Access by applications can be controlled via the Applications tab for each keyring element.

The original poster and many others have (I believe correctly) pointed out an issue that **needs** addressing.  Specifically the ease with which passwords are reveled to a casual user.  It's clear that **someone** thought that casually revealing the passwords "in-the-clear" was a bad idea, hence the bullet obfuscation and the need to select "Show password" to expose the clear text password.  A requirement to enter the keyring master password to show a clear text version of the stored password is a good idea here.

I will admit that when I first started reading this thread I thought to myself... "self, what does the OP expect... he/she unlocked the keyring at login - of course elements of the keyring will be available!".  But within a few minutes of reading the responses, I came to the conclusion that other people (an initially I) were misunderstanding the issue here.  The argument that unlocking the keyring "opens up" access by all applications is false and a total red-herring.  The fact that elements of the keyring are blocked with application level ACLs tells us all we need to know about the intent of the keyring system.  We are primarily talking about an **authorization** issue here, and only marginally an **authentication** issue.  Simply put... If I have to explicitly authorize an application to access elements of my keyring then I also want to explicitly authorize (via an authentication password check) the clear text password being thrown out on to my display.  Please, let's fix this issue and not give up clear text passwords to a casual browser so easily.

p.s. I normally limit my posts to launchpad debugging.  I actually registered a forum account just to comment on this issue.  Hopefully that gives the gnome-keyring and seahorse devs an idea of just how important this issue may be among the user base.

---

### Post by P4man on 2009-11-03
> **QPrime said:**
> An unlocked keyring does not imply that all applications will have access to all passwords.  There are security controls to prevent this and access to keyring elements are protected on a per-application basis (remember the "Deny", Allow Once", " Always Allow" dialogue that pops up?).  Access by applications can be controlled via the Applications tab for each keyring element.


If I understand it correctly (and thats a mighty big IF), what you suggest is roughly whats being talked about on the gnome-keyring mailinglist today. Have a look here:

[http://mail.gnome.org/archives/gnome-keyring-list/2009-November/msg00002.html](http://mail.gnome.org/archives/gnome-keyring-list/2009-November/msg00002.html)

The reply by Stef (gnome keyring developer) hasnt made it to the website yet, but is here:
> 
So what you're suggesting is to have the keyrings live in a daemon
running as root, essentially another security context, which then uses
policykit or gksudo for permisions? An interesting idea. Certainly
non-trivial, and needs a lot more thought, but interesting

At least the concept of having the keyrings live in another security
context is interesting. I haven't thought about this much, so I don't
know whether it would cause more problems than it would solve. But this
bears thinking about in the long term.

Cheers,


Anyway I would suggest you sign up for gnome-keyring mailing list and participate in the debate there, as its much more likely to yield any results than this thread.

---

### Post by bigsuccess on 2009-11-03
> **prshah said:**
> Again, I am not sure about this; if in fact, applications can access/enumerate ALL passwords in the keyring then this is a (IMHO) major security risk; <snip>

Sorry I was generalising in my post. I was trying to explain why it occurs for those who weren't grasping it but I can see why it's mis-leading...

> **QPrime said:**
> An unlocked keyring does not imply that all applications will have access to all passwords.  <snip>

I will admit that when I first started reading this thread I thought to myself... "self, what does the OP expect... he/she unlocked the keyring at login - of course elements of the keyring will be available!".  But within a few minutes of reading the responses, I came to the conclusion that other people (an initially I) were misunderstanding the issue here.  The argument that unlocking the keyring "opens up" access by all applications is false and a total red-herring.  The fact that elements of the keyring are blocked with application level ACLs tells us all we need to know about the intent of the keyring system.  We are primarily talking about an **authorization** issue here, and only marginally an **authentication** issue.  Simply put... If I have to explicitly authorize an application to access elements of my keyring then I also want to explicitly authorize (via an authentication password check) the clear text password being thrown out on to my display. 
<snip>


... looks like I misunderstood too ^ the above makes the distinction clear - cheers.

bS

---

### Post by snkiz on 2009-11-03
> **P4man said:**
> If I understand it correctly (and thats a mighty big IF), what you suggest is roughly whats being talked about on the gnome-keyring mailinglist today. Have a look here:

[http://mail.gnome.org/archives/gnome-keyring-list/2009-November/msg00002.html](http://mail.gnome.org/archives/gnome-keyring-list/2009-November/msg00002.html)

The reply by Stef (gnome keyring developer) hasnt made it to the website yet, but is here:


Anyway I would suggest you sign up for gnome-keyring mailing list and participate in the debate there, as its much more likely to yield any results than this thread.
Thats what I was trying to get across, but guess I couldn't explain my thoughts right. Ah well, they get it now thats what matters :) Go team squeaky wheel! \\:D/

---

### Post by Keyper7 on 2009-11-04
My position on this issue is clear already: I don't consider it a security flaw and I don't care about it.

That said, I've been thinking... Who, among both complainers and defenders in this thread, uses Seahorse anyway? The more I think about it and analyse it, the more I see it as a power user tool. When the average user wants to manage a password, he intuitively goes to the application that uses it. A cool thing that Seahorse does is synchronizing remote keys, which is definitely something that average users are not very interested in.

I'm wondering if all this discussion would be solved if Seahorse simply wasn't installed by default, as is the case with a lot of power user tools.

---

### Post by scaine on 2009-11-04
Marc Deslauriers has blogged about this, annoyingly taking the side of the "lock your PC, there is no security issue" argument.

[http://mdeslaur.blogspot.com/2009/11/gnome-keyring.html](http://mdeslaur.blogspot.com/2009/11/gnome-keyring.html)

P4man, thanks for posting that about Stef's reply - was going to do that myself.  I think he's still making this issue too complex.  All I'm asking is that since the app to change your password in "About me" asks you to re-authenticate before changing your password, Seahorse would benefit from the same mechanism before revealing your passwords.

I'm surprised that the people who argue this isn't an issue haven't logged a bug report about that app - after all, why is it asking me who I am before I change my password?  What gives??  ;)

I'll reply to Stef when I get home tonight.

Cheers,
Neil.

---

### Post by Keyper7 on 2009-11-04
> **scaine said:**
> All I'm asking is that since the app to change your password in "About me" asks you to re-authenticate before changing your password, Seahorse would benefit from the same mechanism before revealing your passwords.

I'm surprised that the people who argue this isn't an issue haven't logged a bug report about that app - after all, why is it asking me who I am before I change my password?  What gives??  ;)

Logical fallacy.

"This isn't an issue" is not the same as "the opposite is an issue".

---

### Post by scaine on 2009-11-04
> **Keyper7 said:**
> My position on this issue is clear already: I don't consider it a security flaw and I don't care about it.

That said, I've been thinking... Who, among both complainers and defenders in this thread, uses Seahorse anyway? The more I think about it and analyse it, the more I see it as a power user tool. When the average user wants to manage a password, he intuitively goes to the application that uses it. A cool thing that Seahorse does is synchronizing remote keys, which is definitely something that average users are not very interested in.

I'm wondering if all this discussion would be solved if Seahorse simply wasn't installed by default, as is the case with a lot of power user tools.

Not quite true - I'm pretty sure Gnome-do uses gnome-keyring for all it's google plug-in apps, so there's your gmail password again.  All GVFS shares are stored there for sure, so anytime you type smb:\\servername\share into Nautilus, you're creating entries (assuming to choose to allow access) too.

Up to you if you want to call that "power user" material though.

Removing Seahorse from the default install would surely hurt the Seahorse developers though in terms of bugs found/fixed.  I, for one, wouldn't particluarly mind though.

---

### Post by Keyper7 on 2009-11-04
> **scaine said:**
> Not quite true - I'm pretty sure Gnome-do uses gnome-keyring for all it's google plug-in apps, so there's your gmail password again.  All GVFS shares are stored there for sure, so anytime you type smb:\\servername\share into Nautilus, you're creating entries (assuming to choose to allow access) too.

Yes, those applications use **gnome-keyring**. But do they use **Seahorse**?

---

### Post by scaine on 2009-11-04
Triple post.  Sorry, but each post is unrelated to the last.

I earlier posted that I was unhappy that Network Manager also uses gnome-keyring and as such Seahorse will show you my PEAP password for my work account, which obviously (due to the nature of PEAP) is my active directory password too.

You can kind of obfusticate this by asking Network Manager to make your PEAP protected wifi entry "available to all users".  For some reason, Network Manager doesn't store these passwords in the users gnome-keyring (perhaps it creates a root keyring, which would make sense).

Sadly, Network Manager itself still insists on showing you the password if you ask it to.  One hurdle down, one to go.  I'm not a WICD fan, but I wonder if it has the same issue?

---

### Post by scaine on 2009-11-04
> **Keyper7 said:**
> Yes, those applications use **gnome-keyring**. But do they use **Seahorse**?

See for yourself - anything stored in gnome-keyring, is, I think, available in Seahorse.  All my gnome-do and gvfs shares show up for sure.  Plus, my wifi accounts that aren't set to "available to all users".

My understanding is that Seahorse is a graphical tool for manipulating the gnome-keyring.  I'm not sure that you can store anything in gnome-keyring that doesn't show up.

The "available to all users" thing is stored in another keyring.

I think that's what Stef was getting at in P4man's post above?

---

### Post by P4man on 2009-11-04
I wouldnt miss it  (seahorse that is). Ive used it twice I think over the last years, to change or reset my keyring pw.  But I think people using autologin or thinkfinger might miss it. And its odd to have apps ask permission and store passwords but not having a way to revoke those permissions. Also at the very least there ought be an alternative to change the keyring password without installing anything extra.

---

### Post by Keyper7 on 2009-11-04
> **scaine said:**
> My understanding is that Seahorse is a graphical tool for manipulating the gnome-keyring.

Exactly. As far as I know, it isn't more needed for the keyring to work than Nautilus is needed for the filesystem to work.

I got curious enough to set up a [poll](http://ubuntuforums.org/showthread.php?t=1314284).

---

### Post by FuturePilot on 2009-11-04
Good explanation here. [http://mdeslaur.blogspot.com/2009/11/gnome-keyring.html]("http://mdeslaur.blogspot.com/2009/11/gnome-keyring.html")

---

### Post by P4man on 2009-11-04
> **FuturePilot said:**
> Good explanation here. [http://mdeslaur.blogspot.com/2009/11/gnome-keyring.html]("http://mdeslaur.blogspot.com/2009/11/gnome-keyring.html")

same arguments that we hear everywhere else, I can hear it a million times I will still not change my opinion. The argument is still based on the IMHO flawed argument that only a locked desktop is truly secure, and *therefore* anything else is pointless,  I agree with the first, not the latter because we dont live in a perfect world where everybody can and does lock his desktop 50x per day, and the chance of someone downloading a "gnome keyring password stealer app" and running it on an unlocked desktop seems at least an order of magnitude less likely than someone running a default installed app to obtain those same passwords.

I guess it boils down to this: If you cant have perfect security, is there such a thing as smaller or greater risk? I think there is, others apparently dont. (I wonder if those same ppl shut down their machines on every report of a possible security vulnerability)...

---

### Post by scaine on 2009-11-04
> **FuturePilot said:**
> Good explanation here. [http://mdeslaur.blogspot.com/2009/11/gnome-keyring.html](http://mdeslaur.blogspot.com/2009/11/gnome-keyring.html)

Thanks Future, except that it's the same post I linked to in reply 367 and I don't agree that it's a good explanation... no wonder this thread's over 350 posts now.  I must account for about 30 of them.

---

### Post by FuturePilot on 2009-11-04
> **scaine said:**
> Thanks Future, except that it's the same post I linked to in reply 367 and I don't agree that it's a good explanation... no wonder this thread's over 350 posts now.  I must account for about 30 of them.

Sorry, this thread is too long for me to read the entire thing.

---

### Post by snkiz on 2009-11-04
> **FuturePilot said:**
> Sorry, this thread is too long for me to read the entire thing.
so you can't be bothered to skim the thread to see if someone has said what you want to say. But you'll scour the web for links to backup your opinion? And that's why this thread is so frikin long.

---

### Post by FuturePilot on 2009-11-04
> **snkiz said:**
> so you can't be bothered to skim the thread to see if someone has said what you want to say. But you'll scour the web for links to backup your opinion? And that's why this thread is so frikin long.

I said it was too long for me to read the **entire thing**, I never said I didn't skim any of it over. Anyways, apparently this thread has turned into attacking people because of their views. I'm done with this thread.

---

### Post by scaine on 2009-11-04
I wouldn't take it personally, Future, always seems to happen when threads get this big.  The same is said over and over by so many people, frustrations boil over.  If there's any updates on the dev mailling list, I'm sure P4man or myself (or anyone else following the list) will update here.

Or follow it yourself via the archive :
[http://mail.gnome.org/archives/seahorse-list/2009-November/thread.html](http://mail.gnome.org/archives/seahorse-list/2009-November/thread.html)

Neil.

---

### Post by plasma-engineer on 2009-11-04
This thread is ridiculously long!  And no - I haven't read all 39 pages but only about 25 of them and I get a flavour of the opinions being expressed.  All of it makes sense.  Some of it is just geeks showing off too.  (I can break any password that you can create! etc. etc.)   But I think I mentioned about 35 pages ago that the Firefox solution would solve the problem for 99% of us.  I'm sure that it isn't completely secure, but asking for the password before revealing the passwords in clear text is not very much to ask - is it??  Please?

---

### Post by the.lost.one on 2009-11-05
Oh still being discussed! 
Although I'm glad this issue has been acknowledged by some developers.

---

### Post by Fran89 on 2009-11-23
This is true, I don't like or have ever realized this, I solved a problem with a simple solution: I went to Edit Menus, and added gksu -u <Username> seahorse, this stops anyone from entering the GUI way, but the fact that this (seahorse) can still be ran from any terminal still bothers me.

---

### Post by ad_267 on 2009-11-24
> **Fran89 said:**
> This is true, I don't like or have ever realized this, I solved a problem with a simple solution: I went to Edit Menus, and added gksu -u <Username> seahorse, this stops anyone from entering the GUI way, but the fact that this (seahorse) can still be ran from any terminal still bothers me.
If it bothers you that much,
```
sudo apt-get remove seahorse
```

---

### Post by Agent ME on 2009-11-24
Don't do that, you'll remove the ubuntu-desktop package too doing that.

And even if you could remove it without removing the ubuntu-desktop package, that (rightly) still doesn't stop someone from downloading the seahorse package and running the binary manually -- which can be done in a single line in a terminal (safe to run to test, only writes to a temp folder):
```
cd `mktemp -d` && wget "http://mirrors.kernel.org/ubuntu/pool/main/s/seahorse/seahorse_2.28.1-0ubuntu1_$(if [ "`arch`" = "x86_64" ]; then echo "amd64"; elif [ "`arch`" = "x86" ]; then echo "i386"; fi).deb" && ar xv seahorse*.deb && tar -xvzf data.tar.gz && usr/bin/seahorse
```
Edit: Never mind, above requires a few of the package files to be already strewn about on the system, so the above will only work if 'seahorse' is installed already (guess it could be useful if someone only removed the seahorse binary).

---

### Post by Fran89 on 2009-11-24
It doesn't bother me THAT much, I mean not a lot of people are Linux savvy enough to think about it, much less my friends or anyone that I know of, but still you know, its there in the back of your head, staring at you..., always... :shock: :P

---

### Post by scaine on 2009-11-25
> **ad_267 said:**
> If it bothers you that much,
```
sudo apt-get remove seahorse
```

Well since the discussion on the subject is pretty much dead and the Seahorse devs aren't taking on the idea of a password before showing your passwords in cleartext, that's exactly what I did.

Ubuntu desktop is just a meta package.  It's only mainly useful during the dev cycle to add/remove packages in a consistent fashion.  No real risks in removing it.

I'll maybe try again on the Seahorse dev mailing list (I'm still subscribed - it's a quiet list) during Lucid, but being honest, I'm a little Ubuntu'd out at the moment.  It's been a disappointing cycle in terms of my personal experience with Karmic and I'll need to recharge the batteries before partaking in a rant-thread like this one again!

---

### Post by ad_267 on 2009-11-26
> **Agent ME said:**
> Don't do that, you'll remove the ubuntu-desktop package too doing that.

As scaine said, there's no harm in removing the ubuntu-desktop package. You can install it again later if you really need it. I'd check that "apt-get autoremove" didn't want to remove anything useful though. If it does you can just "apt-get install" whatever apt wants to remove.

---

### Post by VioletsPie on 2009-11-27
Am I paranoid or is this entire thread mostly the same person generating conversation? It's mostly meaningless babble and the posts between the 4-5 users seem to be at the same time.

---

### Post by agrouo on 2009-12-14
> **snkiz said:**
> I'd love to make my sudo password different than my login
There should be pam settings.
AFAIK via /etc/pam.d/sudo it should be possible to change the way authentication works for sudo only - hopefully somebody else can give some details.

---

### Post by snkiz on 2009-12-15
> **agrouo said:**
> There should be pam settings.
AFAIK via /etc/pam.d/sudo it should be possible to change the way authentication works for sudo only - hopefully somebody else can give some details.

Really? Curious how you came by this info, that file is pretty bare. Got my attention :shock: Maybe a new thread to express your thoughts?

---

### Post by bodhi.zazen on 2009-12-15
> **snkiz said:**
> Really? Curious how you came by this info, that file is pretty bare. Got my attention :shock: Maybe a new thread to express your thoughts?

To configure sudo , see [http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

You may be interested i nseveral of the options, including

**rootpw and **[B]targetpw


[/B]You will need to decide for yourself the security implications of setting a root pw.

Personally, when I do this, I set root's shell to /bin/false. Take care not to lock yourself out ;)

---

### Post by snkiz on 2009-12-15
I had a feeling you would have to enable the root account in some way to get the different password. I never really looked into that option much, because of the whole root account is BAD thing. Doesn't setting the environment to /bin/false prevent a user from running commands though?

---

### Post by bodhi.zazen on 2009-12-15
> **snkiz said:**
> Doesn't setting the environment to /bin/false prevent a user from running commands though?

No, it does not, it prevents the user from loging in or automatically starting a shell with sudo -i.

you may still sudo <insert command here>

including sudo bash, lol

---

### Post by snkiz on 2009-12-15
> **bodhi.zazen said:**
> 
including sudo bash, lol
Thats a little silly, but hey I've ssh'd into another user on my desktop before so why not. 

Aside form locking yourself out, are there other issues? For example could you still get in under recovery/single-user mode?

---

### Post by bodhi.zazen on 2009-12-15
> **snkiz said:**
> Thats a little silly, but hey I've ssh'd into another user on my desktop before so why not. 

Aside form locking yourself out, are there other issues? For example could you still get in under recovery/single-user mode?

Well, again in recovery mode you would need to specify /bin/bash, but I have not tried it, so yes, you might well lock out recovery mode.

---

### Post by scaine on 2009-12-16
It remains much, much simpler to un-install Seahorse.  For the once a year I might find myself wanting to use Seahorse, I can always install it again briefly.

---

### Post by scaine on 2010-02-23
Evening all.  Thought I'd resurrect this thread (which I notice has now been renamed - thank goodness), since there's been a new version of Seahorse released in the last day or so which might well fix this issue.

[http://mail.gnome.org/archives/seahorse-list/2010-February/msg00005.html](http://mail.gnome.org/archives/seahorse-list/2010-February/msg00005.html)

Quote :
Details between 2.29.90 and 2.29.91:
==================================

* Change default key lengths for subkey generation. [Adam Schreiber]
    * Remove unused variables [Pablo Castellano]
    * Revoking subkey now works again. Also minor documentation
changes. [Pablo Castellano]
    [COLOR=Red]* Don't show the passphrase in plaintext. [Pablo Castellano][/COLOR]
    * Check the OpenPGP engine only [nobled]
    * Fixed wrong variable names in comments [Pablo Castellano]
    * Clean up version constants [nobled]
    * Fixed two warnings at compile time [Pablo Castellano]
    * Unescape URI's before presenting them to the user. [Adam Schreiber]
    * Updated year in the copyright string of the about dialog [Pablo
Castellano]
    * Fixed incorrect signal name [Pablo Castellano]
    * Fixed bug in the public key properties GUI. [Pablo Castellano]
I'm not running Lucid yet, but if anyone is, can you do a quick Help/About and if you're running this version, see if it fixes what started this whole thread in the first place.

(In case you've forgotten, it was about the fact that when you go to the "passwords" tab in Seahorse, you can view any unlocked "login" passwords in plaintext without being prompted for your password.)

---

### Post by snkiz on 2010-02-23
Well almost 400 posts and about dozen people attacking the seahore mailing list got a simple problem fixed! yea us! I have to wonder though why this wasn't fixed at distro level then passed upstream. Heaven forbid we question our gnome overlords I guess.

EDIT:
Wow that was a little snippy. Sorry all just a little bitter.

---

### Post by FuturePilot on 2010-02-23
> **snkiz said:**
> Well almost 400 posts and about dozen people attacking the seahore mailing list got a simple problem fixed! yea us! I have to wonder though why this wasn't fixed at distro level then passed upstream. Heaven forbid we question our gnome overlords I guess.

EDIT:
Wow that was a little snippy. Sorry all just a little bitter.

Probably because there wasn't a clear consensus on how it should be fixed or if it should be fixed at all. Let the Seahorse devs decide the best way to handle it. Otherwise you're wasting your time trying to implement something that might not be acceptable by upstream.

---

### Post by bodhi.zazen on 2010-02-23
> **FuturePilot said:**
> Probably because there wasn't a clear consensus on how it should be fixed or if it should be fixed at all. Let the Seahorse devs decide the best way to handle it. Otherwise you're wasting your time trying to implement something that might not be acceptable by upstream.

+1 I was about to draft a similar response.

---

### Post by Karl1982 on 2010-05-16
Trying to teach the world to lock their computers by making their passwords clearly visible is an inappropriate viewpoint for an operating system developer to take.  They should be more concerned about Ubuntu being a secure platform than trying to lock the world's computers, especially considering the fact that average Linux users are far more security conscious than average Windows users in the first place.  You're preaching to the choir.

Not every situation calls for advanced security.  What if I want to let a family member use my laptop for an hour or two to see if they want to try Ubuntu on their computer?  I shouldn't have to wonder if they might be nosy enough to click on Passwords and Encryption Keys in the menu and look at my passwords.  They simply shouldn't be able to do it.  You can't even change your network settings or install updates without sudo stepping in, so why should my secrets be a few nosy clicks away?

And keep in mind that security is not a black-and-white issue.  It's not either you have security, or you don't; Security comes in varying levels in all instances.  I feel that with my secrets being readily available from the menu, the bar is a little low for my taste.

There are several relatively simple ways to handle this, and please also keep in mind that "you should lock your computer anyway" is not an end-all argument against having reasonable security on an unlocked computer.  Should Ubuntu allow root priviledges for any action automatically after a user is logged in?  Why don't we just do away with sudo completely since if you lock your computer, nobody can screw with it?  ...  I doubt you would agree with that.

1.) Each individual keyring could have an option to automatically lock after X minutes of being unlocked.  Then you could have two or three keyrings with varying levels of security.  Maybe network and Empathy secrets could stay unlocked, but more sensitive or infrequently-used items lock again after 15 minutes.  **If it's a reasonable security measure for sudo, it's a reasonable security measure for seahorse.**

2.) Automatically lock all keyrings when seahorse is opened.  Then you don't have the hassle of repeatedly unlocking keyrings, but no one can just wander into the accessories menu and look at them.

3.) Require sudo to open seahorse.  Or just lock the console when opening seahorse.  Require the user's logon password to open seahorse by whatever means are available.  That will be just as much a deterrent as access to any other part of the system.

---

### Post by FuturePilot on 2010-05-16
> **Karl1982 said:**
> 

Not every situation calls for advanced security.  What if I want to let a family member use my laptop for an hour or two to see if they want to try Ubuntu on their computer?  I shouldn't have to wonder if they might be nosy enough to click on Passwords and Encryption Keys in the menu and look at my passwords.  They simply shouldn't be able to do it.  You can't even change your network settings or install updates without sudo stepping in, so why should my secrets be a few nosy clicks away?



That's what the guest session is for.

---

### Post by DarkTide on 2011-04-12
i think the best way to solve this would be the exactly the same way as  the other privileges are handled, for example if i change CPU frequency i  get some key-icon in my tray saying i still have privileges and just  clicking that icon will drop them.

---

### Post by Locke_99GS on 2011-04-12
```

sudo chmod o-x /usr/bin/seahorse

```

In alacarte, edit the seahorse entry and preface the command with sudo. (not gksudo)


Also, I thought this discussion had long died out. Meh...

---

### Post by cariboo on 2011-04-12
> **Locke_99GS said:**
> ```

sudo chmod o-x /usr/bin/seahorse

```

In alacarte, edit the seahorse entry and preface the command with sudo. (not gksudo)


Also, I thought this discussion had long died out. Meh...

The problem doesn't exist anymore, in Maverick and newer.

---

### Post by Locke_99GS on 2011-04-12
Well excellent then. :) Please disregard my previous post.

---

### Post by oldmankit on 2011-04-26
I'm running a fully updated system (10.10) and I can still sea passwords in seahorse in plain text (without being asked to re-enter my user password or any other passwords).  I thought people said it had been 'fixed'.  Am I just waiting for something to filter down to end-user level?  When might I expect it?

---

### Post by cariboo on 2011-04-26
I'm running a fairly fresh Natty install on three different systems, On one I don't see any passwords, on the system I'm on right now, It doesn't show my login password, but it does show passwords for pdf's and forum logins. It seems to only list saved passwords. On the system that doesn't show any passwords, I don't have any saved passwords.

---

### Post by oldmankit on 2011-04-26
> **cariboo907 said:**
> I'm running a fairly fresh Natty install on three different systems, On one I don't see any passwords, on the system I'm on right now, It doesn't show my login password, but it does show passwords for pdf's and forum logins. It seems to only list saved passwords. On the system that doesn't show any passwords, I don't have any saved passwords.
So it sounds like the 'old' behaviour.  I don't believe it ever showed your login password, just saved passwords for forums etc.

I was just interested because a few people said this behaviour had changed, which it clearly hasn't for the end user. But maybe it has upstream somewhere.

---

### Post by scaine on 2012-07-30
> **oldmankit said:**
> 
I was just interested because a few people said this behaviour had changed, which it clearly hasn't for the end user. But maybe it has upstream somewhere.

Just tried this on fresh Ubuntu 12.04, still shows passwords in clear text with no prompt for 'sudo' password.

<sigh>

Epic fail.

```
sudo apt-get remove seahorse
```Still annoys me that ubuntu-desktop relies on this weak package though.

---

### Post by wildmanne39 on 2012-07-31
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

