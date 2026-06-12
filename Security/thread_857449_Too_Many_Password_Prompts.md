---
title: "Too Many Password Prompts"
date: 2008-07-12
forum: Security
---

### Post by Ashejoe on 2008-07-12
To me, Ubuntu 8.04's endless insistence that a password be entered to do just about everything is a source of constant annoyance.  Is there any way to disable ALL password requests ?

I live alone .....

I don't share a computer with anyone ...

I'm the only person who ever uses this computer .....

All I want to do is get my email and get on to the internet without constantly having to enter my password, over, and over and over.

Just to get to my email (Evolution), I have to enter a password to log into Ubuntu;  Then I have to enter it again to access the internet;  Then I have to enter the very same password a third time to access my email.  This is ridiculous.  Even Window's Vista UAC isn't this annoying !

Passwords may have their role in business and in shared public computers, but to for a person who's the only user the system ever sees, I think it's over kill and would sincerely appreciate any advice as to how to disable ALL password prompts if it's possible ?

Thank You.

---

### Post by scottuss on 2008-07-12
Disabling all password prompts is not a good idea. The security system Ubuntu (and Linux in general) has built in is one of the main reasons we can rest assured we are highly unlikely to be the target of malware, viruses etc... Ubuntu should only ask for your password to do admin tasks, not check email/internet. What tasks are you trying to do that you don't want to be asked a password for?

Also I'm confused. You shouldn't need a password to access internet and email client. What software are you using?

---

### Post by SunnyRabbiera on 2008-07-12
The passwords are a nessasary evil, auto login and auto passwords are a very bad idea.

---

### Post by brian_p on 2008-07-12
> **Ashejoe said:**
> Passwords may have their role in business and in shared public computers, but to for a person who's the only user the system ever sees, I think it's over kill and would sincerely appreciate any advice as to how to disable ALL password prompts if it's possible ?

It's not something I'd do myself but auto login is possible. A Google search, or a search in these forums, on it together with 'Ubuntu' will point you in the the direction of passwordless logins.

I don't understand why you have to type passwords to access the internet and mail either.

---

### Post by scottuss on 2008-07-12
OK well other people have advised against it too now, but if you really want auto login:

System > Administration > Login Window > Click the security tab and then enable auto log in from there.

It should be OK since you say only you use the computer.

The rest is up to you to Google etc. (although I'm still curious about needing password for email / internet)

---

### Post by hyper_ch on 2008-07-12
for half of the things you say above you don't need to enter a password... so plz don't exaggerate.

---

### Post by kwilliam on 2008-07-12
> **scottuss said:**
> Ubuntu should only ask for your password to do admin tasks, not check email/internet.

Perhaps the user's wireless password and email password are stored in a wallet/keyring program. (I know in Kubuntu, applications like KNetworkManager, Konqueror, KMail, and Kopete all store their passwords in the KDE Wallet.)

**[SIZE="2"]Ashejoe: Here are some things that might help![/SIZE]**
I found these by googling "gdm auto login" and "gnome-keyring unlock". They're all from 2007, but hopefully they'll still be useful.

Auto-login for GDM, so you don't have to type in your password each time you boot the computer: [http://tuxicity.wordpress.com/2007/03/02/some-gdm-basics-for-ubuntu-and-xubuntu-theming-and-auto-login/](http://tuxicity.wordpress.com/2007/03/02/some-gdm-basics-for-ubuntu-and-xubuntu-theming-and-auto-login/)

Unlock the Gnome-keyring (probably what stores the Internet and Evolution passwords) when you login: [http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/) The article applies to Feisty, which is two Ubuntu versions ago, but hopefully the tutorial will still work, or at least get you started in the right direction. I'm using Kubuntu so I don't have a GNOME keyring to test with, but I reckon the only difference is the package "libpam-keyring" appears to be called "libpam-gnome-keyring" now.

At least for the people of 2007, the auto-unlocking GNOME Keyring trick didn't work when GDM auto-login was enabled. However, some users posted workarounds that worked for them, such as this one: [http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring+auto+login&page=7#postcount2524785](http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring+auto+login&page=7#postcount2524785)

To those who say that enabling auto-logins like these are a security breach, I disagree. In this case, the user says he lives alone and is the only person with physical access to the computer. In that case, probably the best thing you can do for security is to make sure you are behind a wireless router or have a firewall (such as Firestarter or Guarddog) installed, since the only threat would be from bots on the Internet. And of course, not fall for "social hacking" tricks, like following suspicious links in emails, or running code you find in forums that you don't understand.

That should take care of most passwords, I think, except for programs that are run as root with sudo. It is possible to edit the sudoers file (by running sudo visudo) so that sudo does not ask for passwords either, but that may be overkill... and unlike the other tweaks presented, would allow a hacker to get root and destroy your computer. A safer thing would be to edit the timeout value; normally, sudo remembers your password for 5 minutes after you run a command with sudo, but you can change that to a higher value (like an hour) if entering your sudo password gets to be too annoying. If you don't know what sudo is, you can probably ignore this paragraph. :-) Otherwise, search for "passwordless sudo" or "sudo timeout" with google or in the forums.

---

### Post by Ashejoe on 2008-07-12
Thank You all for the sincere replies to my inquiry on too many passwords.

And while I can certainly agree with what most of you had to say,  in my particular case, most are not relevant. (in "my" situation that is... not in every situation.) 

All I do is turn my computer on to check for email, retrieve my email, then shut the computer off and go on my way.  Occasionally, I do access the internet for information on local establishments.  But that's about it.  My computer is not on 24/7. On a typical day, it may be turned on for less than 1/2 hour.


Here's the way it typically plays out for me each morning when I go to see if I received any email messages:


**_PASSWORD NUMBER 1_**:  Logging into Ubuntu initially.  I prefer Gnome, but decided to try KDE4 from the Ubuntu software repository using the "ADD/REMOVE SOFTWARE" function inside of Ubuntu 8.04.  

I (think), I unloaded KDE4, but, it still boots up into the KDE4 splash screen prompting me for my log in password.  Then when I enter my first password, the system proceeds to load Gnome.  Why do I need to "identify myself" to this computer if I live alone and I'm the only one who uses it ??  23.5 hours per day, the unit is shut off.

**_PASSWORD NUMBER 2_**:  I don't know if I accidentally checked something or not, but, before I can access the internet, I get another screen (similar to the one you get when trying to install software from the Ubuntu repository), again asking me for my password to access the network.  Again, to me, in my situation, this is not necessary as no one else uses this computer.

**_PASSWORD NUMBER 3_**:  When I go to retrieve my email with Evolution Mail, I again get prompted to enter my password.  This time, it appears to be Evolution that wants my password.  Perhaps I should switch to Mozilla Thunderbird ???

In an ideal world, I'd like to get up in the morning, turn my computer on, and when I come back with my morning coffee the desktop is ready to go.  Not sitting there waiting for me to spend several minutes entering the same passwords three times.

Yes, I can definitely concur with what several of you said about system security, but in my case, it's just not relevant given the way I use this old system. 

Thank you all once again for taking the time to respond to me.  I appreciate it.

---

### Post by LeoSolaris on 2008-07-12
Definitely strange that it isn't storing the passwords. It does appear to me atleast that you've managed to either keep it from remembering the password, or you've somehow secured it behind your root password. Either way, it's not standard. It should ask you for your login password  at GDM, but that can be removed easily enough through the Login Window gui in Administration.

Leo

---

### Post by Ashejoe on 2008-07-12
KEYRING..... YES... that's what the SECOND password prompt I get says on the screen... something about "keyring".  Once I enter the password, I can proceed to the internet.

---

### Post by Ashejoe on 2008-07-12
KWILLIAM... YOU ARE AWESOME...... I followed your advice, and it seems to be exactly what I was looking for !!!

I owe you one !!!

Thanks

---

### Post by kwilliam on 2008-07-12
> **Ashejoe said:**
>  I prefer Gnome, but decided to try KDE4 from the Ubuntu software repository using the "ADD/REMOVE SOFTWARE" function inside of Ubuntu 8.04.  

I (think), I unloaded KDE4, but, it still boots up into the KDE4 splash screen prompting me for my log in password.  

Oh! In that case, you're probably using KDM instead of GDM. That doesn't really hurt anything, but the auto-login settings for KDM would be configured somewhere else. If you want to switch back to using the Gnome login screen, run:
```
sudo dpkg-reconfigure gdm
```
On the other hand, if you're satisfied with the way it's working now, I wouldn't change it. :-)

> **Ashejoe said:**
> KWILLIAM... YOU ARE AWESOME...... I followed your advice, and it seems to be exactly what I was looking for !!!

I owe you one !!!

Thanks

No problem! If you want, you can thank people for helpful posts by clicking on the yellow star at the bottom right of the post. (Why they didn't make a button that said "Thank You!" instead of a small yellow star next to the QuickReply button, I have no idea.)

---

### Post by HHelsinger on 2008-07-25
There is another recent thread, which I found searching for Evolution Unlock Keyring, suggesting that the request for a password when opening Evolution is a security change new with 8.04.  

A solution is offered in that thread.

I am surprised and appalled that when someone says they are being asked for a password, some replies assert that it can't be happening.  Politeness would be nice to see.

---

### Post by Ashejoe on 2008-07-25
Hi Hhelsinger:
... **AMEN BROTHER** to your remark on politeness !!!!

Over the years I've dabbled on and off trying to teach myself Linux.  Mepis / SuSe / Mandrake / Fedora / Knoppix / plus about another half dozen or so lesser known distribution.  And almost exclusively, when I would post a question on one of their user  forums, I'd get some smart a __ __  that would attempt to belittle me and use my question as some sort of (sic) proof of how superior they were relative to me or anyone else ! 

Needless to say, I moved on rather than put up with such online immaturity !  As a matter of fact, once I even snail mailed Mepis Founder, Warren Woodard, a personal letter asking him how he expected Mepis to prosper if people get treated like dogs on his Mepis User's Forum.  He never replied one way or another.  (And have you noticed that Mepis is all but dead ?)

One of the primary reasons I've come to love and admire Ubuntu is the sincere and polite help I receive from 98% of the Ubuntu community.  It has inspired me to strongly recommend Ubuntu to others, as well as become more involved where I can in the Ubuntu Community myself.

KWilliam is a good example of what I'm talking about.  Instead of trying to belittle me for my question, he looked at it sincerely and recognized what was happening with the "KeyRing".  I put his advice into action... and I'm glad to say... the problem was resolved !  Now I can turn on my computer and get straight to email without having to enter 3 passwords to get there !  KWilliam has become my role model of what a Community Member is all about !  I hope I can follow in his foot-steps !!

So thank Hhelsinger for your response.  I really do appreciate it.

---

### Post by asbesto on 2008-07-25
> **Ashejoe said:**
> Thank You all for the sincere replies to my inquiry on too many passwords.

And while I can certainly agree with what most of you had to say,  in my particular case, most are not relevant. (in "my" situation that is... not in every situation.) 


**_PASSWORD NUMBER 1_**:  Logging into Ubuntu initially.  I prefer 

**_PASSWORD NUMBER 2_**:  I don't know if I accidentally checked something or not, but, before I can access the internet, I get another screen (similar to the one you get when trying to install software from the 

**_PASSWORD NUMBER 3_**:  When I go to retrieve my email with Evolution Mail, I again get prompted to enter my password.  This time, it 



And you forget password number 4 when installing software, number 5 when modifying configurations ... and so on!!!

this is really annoying, I wrote time ago a sort of FAQ on this, here's my post:

[http://ubuntuforums.org/showthread.php?t=435906]("http://ubuntuforums.org/showthread.php?t=435906")

with this you can solve the damn passwords problem. :)

---

### Post by DJ_Peng on 2008-07-26
> **HHelsinger said:**
> There is another recent thread, which I found searching for Evolution Unlock Keyring, suggesting that the request for a password when opening Evolution is a security change new with 8.04.  

A solution is offered in that thread.
May we get a link please? I've seen several threads and I'm not sure which one you're referring to. I saw one that had a script that could be autoran, but it had no clue as to what to call it, etc., and every time my brain looks at it it's been a little too "offline" to figure things out by itself. 

I think several of us need a "for dummies" post, especially when it's on a single-user computer with autologin. Even I need it from time to time and I'm the guy most of my friends come to with Linux questions.

+1 on the thanks for the comment about politeness. Too many people feel "it's just online" and don't think there's any need to use common civility.

---

### Post by kwilliam on 2008-07-30
Wow! I'm a role model now! And I thought I was just being polite. :-) Seriously though, I'm flattered, Ashejoe. It's appreciative comments like that, and the polite, helpful responses that *I've* gotten on many occasions, that inspire me to occasionally browse through new posts and see if I can help. Admittedly, I'm not a frequently visitor of the forums, but I've posted my share of questions here, and now that I've got some experience I try to answer a few as well!

For the record, I have no idea about the Evolution thing, so hopefully somebody else can explain that.

---

