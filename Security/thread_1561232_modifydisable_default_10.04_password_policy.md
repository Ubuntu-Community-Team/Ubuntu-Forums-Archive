---
title: "modify/disable default 10.04 password policy"
date: 2010-08-26
forum: Security
---

### Post by gamblor01 on 2010-08-26
Wow...I can't believe nobody has asked this question before.  So here goes...


<rant>
Is there a way to modify or disable the default password policy for Lucid?  I was just recently forced to change my password (and somehow got locked out in the process so I had to drop to a root shell just to get it changed.  Hold shift while your system is booting to get the grub menu, FYI).

I had to change my password to something I can't even remember it's so long and arbitrary.  Thus -- I wrote the thing down on a post-it note and put it inside my laptop...WHICH COMPLETELY DEFEATS THE PURPOSE OF HAVING A PASSWORD!!!

When I attempt to change my password this is the message I get:

> 
You can now choose the new password or passphrase.

A valid password should be a mix of upper and lower case letters,
digits, and other characters.  You can use an 8 character long
password with characters from at least 3 of these 4 classes, or
a 7 character long password containing characters from all the
classes.  An upper case letter that begins the password and a
digit that ends it do not count towards the number of character
classes used.

A passphrase should be of at least 3 words, 11 to 40 characters
long, and contain enough different characters.

Alternatively, if no one else can see your terminal now, you can
pick this as your password: "tea_lorry!attend".
Even when I try to type in a different password than the crazy things it suggests for me (which I could possibly remember, though I don't care to type because it's so long), I get an error message stating:

> Warning: your longer password will be truncated to 8 characters.Ok so -- you're telling me I have to use something that is at least 3 words and at least 11 characters, and when I enter a value which satisfies both of those requirements then I get a warning that it will be truncated?  Uhhh...WHAT?!?!?  Ok so one of the "words" was a name.  Does Ubuntu have some lexicon it's looking through to validate words?  Sheesh.

I also tried entering something that was 8 characters containing:
- an uppercase letter
- several lowercase letters
- several numbers
- a special character

It wouldn't accept that password either so the information it's telling me is flat out wrong.  And no, I didn't have the uppercase character as the first character, nor did I have a digit as the last character.

I tried messing around in /etc/pam.d/common-password and updating that file didn't help at all.  Can someone please tell me if there is a way to change this policy?  Right now I'm stuck with passwords I have to write down because I can't even remember them.

Usually I can get around password constraints by running passwd as root (an equivalent would be using sudo passwd).  I tried this and it still enforced the same policy.   I would prefer to just disable this stupid thing if possible.
</rant>

---

### Post by DavidOfLondon on 2010-08-26
This isn't a joke - have you checked the manual? The number of Linux users who don't look at the manual is stark. It's answered dozens of questions for me or enabled me to ask the correct question on Google.

The simple answer is that Lucid has no option to permanently turn off the root password function because doing so would turn Linux OSs into Windows - where once you're logged in as Admin you can inadvertently destroy your own life by accidentally removing a vital exec file and killing your PC in the process.

Linux is segregated in file structure. The sudo command gives you permission altering powers, as you already know. But it's time-limited for extra security.

You might find this frustrating but trust me, the segregation is the reason you can safely open any email and think "Hah! Trojan my ***, I am a Linux user!". I don't know how much you understand about Linux but the overwhelming majority of viruses and worms etc fail on Linux because it's the equivalent of trying to break into a prison - it's pointless. It's just door after door after door...with no key.

The password permissions issue is also the reason why you can crash a program without crashing your computer - it's segregated. If your video viewer decides to eat itself it won't eat your desktop too.

My password is 11 letters long and has no numerals and no characters and no uppercase - if someone wants to hack my computer then <snip> em, the OS is free and I can zero the pc and reload it all in 30 mins max as opposed to a whole day with windows. Seriously, maybe you should just reinstall the whole thing if it's causing you this much stress (and I've been there, believe me...I know the frustration well).

All I'd say is this - the obligatory root password structure is the reason your life won't be sucked into a blackhole by a worm.

---

### Post by BkkBonanza on 2010-08-26
I don't think the OP is complaining about having a password. I think he's complaining about the conformance policy regarding length and structure and being forced to change it.

I just upgraded to 10.4 and if it's now forcing periodic password changes then I'd also like to revise that policy. I have absolutely no desire to be forced to change my password - if that's some new policy, then kiss my a**. 

/rant on
Actually I'm getting a bit fed up with Ubuntu shifting policy around on each upgrade and moving things around and generally thinking they have a right to force change on users. I should have stayed with 9.10 as several things got messed up during the upgrade. CUPS no longer prints properly any more. blah blah blah. progress=regression.
/rant off

---

### Post by mailc on 2010-08-26
I have had the same password (8 characters , 3 classes) and was never asked to change it.

 But  you are saying that if I type in a terminal :   ' sudo passwd {USERNAME} '  , it does not let me change the password for that particular USERNAME  to anything I want?  And it insists that I have 8 or a minimum of 7 with conditions? And if I type a 20 character password, it tells me that it will be truncated to 8? 

I am not going a try it now but somehow it makes no sense.

---

### Post by gamblor01 on 2010-08-26
> **DavidOfLondon said:**
> This isn't a joke - have you checked the manual? The number of Linux users who don't look at the manual is stark. It's answered dozens of questions for me or enabled me to ask the correct question on Google.

The simple answer is that Lucid has no option to permanently turn off the root password function because doing so would turn Linux OSs into Windows - where once you're logged in as Admin you can inadvertently destroy your own life by accidentally removing a vital exec file and killing your PC in the process.

Linux is segregated in file structure. The sudo command gives you permission altering powers, as you already know. But it's time-limited for extra security.

You might find this frustrating but trust me, the segregation is the reason you can safely open any email and think "Hah! Trojan my ***, I am a Linux user!". I don't know how much you understand about Linux but the overwhelming majority of viruses and worms etc fail on Linux because it's the equivalent of trying to break into a prison - it's pointless. It's just door after door after door...with no key.

The password permissions issue is also the reason why you can crash a program without crashing your computer - it's segregated. If your video viewer decides to eat itself it won't eat your desktop too.

My password is 11 letters long and has no numerals and no characters and no uppercase - if someone wants to hack my computer then f**k em, the OS is free and I can zero the pc and reload it all in 30 mins max as opposed to a whole day with windows. Seriously, maybe you should just reinstall the whole thing if it's causing you this much stress (and I've been there, believe me...I know the frustration well).

All I'd say is this - the obligatory root password structure is the reason your life won't be sucked into a blackhole by a worm.
There are so many things wrong in this that I don't even know where to begin, but I'll try:

- If you are going to invite me to thoroughly read the manual then I invite you to thoroughly read my post.  You missed the whole point of the post which has nothing to do with me complaining about the sudo command.  In fact, I actually prefer using sudo over using a root shell.

- You are incorrect when you say there is no possible option to enable root login on Ubuntu.  It's actually really easy to to do, though posting the instructions on the forums here is against the rules (yes -- I have read them).

- You are also incorrect about malware being unable to penetrate "locked" files if the malware is run by a regular, user account.  A very common practice for malware is to exploit a user account and then use privilege escalation to gain root access.  A common way of doing this was a bug in ptrace.  There is also a null pointer flaw that has existed in every 2.4/2.6 kernel since 2001 which could allow the same thing.  Privilege escalation is quite common.  Someone could even modify your $PATH variable to include the current working directory (maybe it's your home directory), and then put a new sudo script in there (which is a trojan, and will echo your password to a file and then invoke the real sudo command).  Simple as that...they now have root access on your machine.

Take that one step further and look at SubVirt and BluePill.  They are rootkits for virtual machines.  They can both allow a rootkit running on a virtual machine to actually install malware at the hypervisor level.  If rootkits can get beyond the bounds of a VM then certainly malware can get beyond the bounds of a user account to the root account (I gave you three examples above).

Also, take a look at the "Morris Worm" -- it was a worm that wreaked havoc on *UNIX* (not Windows) systems back in the 80's.  It used a vulnerability in the finger command to spread and crashed systems across the United States.  This is just an example -- one of many.   If you think that malware cannot infect Unix/Linux systems then you are sorely mistaken.

- Reloading the whole OS just to get around a password policy?  Really?  That seems like it's a bit too much trouble.  It's also the lazy/novice way out of things.  There is a setting somewhere that controls what I want -- I just have to find it.  Reloading the OS, installing all of the packages, copying over all of my files, etc. is too much work.  This is my work laptop and requires significantly more effort to get everything installed than you might think.


> 
I don't think the OP is complaining about having a password. I think  he's complaining about the conformance policy regarding length and  structure and being forced to change it.

I just upgraded to 10.4 and if it's now forcing periodic password  changes then I'd also like to revise that policy. I have absolutely no  desire to be forced to change my password - if that's some new policy,  then kiss my a**. 
That is correct -- thank you for reading my post.  You can check your current password policy with the following command:

```
sudo chage -l <your_username>
```You can then change the policy (for example, to increase the password expiration interval, or set it to never) by running the same command without the -l option:

```
sudo chage <your_username>
```You can set the maximum password age to -1 if you never want to expire.  Or you can just set it to like 3000 days (which probably means you will have reinstalled by then).

> I have had the same password (8 characters , 3 classes) and was never asked to change it.

 But  you are saying that if I type in a terminal :   ' sudo passwd  {USERNAME} '  , it does not let me change the password for that  particular USERNAME  to anything I want?  And it insists that I have 8  or a minimum of 7 with conditions? And if I type a 20 character  password, it tells me that it will be truncated to 8?That is all correct.  I tried changing my password using "sudo passwd <username>" and it still forced me to enter the password conforming to those rules.  Oddly enough, even though it told me that the password I entered was truncated to 8 characters, it clearly wasn't.  If I attempt to login using the first 8 characters then I get an error.  If I type out the whole string then I can login just fine.

I'm still looking for a way to change this policy so I can go back to my old password(s).  The one I was using before was 11 characters from 3 different character classes -- pretty strong in my opinion.  I was allowed to set it as such when I first created the account (during installation) but can't seem to use any "weak" password like that now.  :(

---

### Post by cariboo on 2010-08-26
I've been using the same password since Dapper, and I've never seen a notice to change or modify it. I'm currently running Maverick, during the install process it asks you if you would like to set your own password, or allow the OS to create one. It's probably been in other versions, but I've never noticed it before.

The install suggested an 8 character password, with a combination of upper, lowercase and numbers. The thing I don't understand is that Maverick states that it's a strong password, yet when I use a password strength checker, I'm told that the password is of medium strength.

As far as policy goes, I like that Ubuntu is strengthening security, as there were quite a few little things that were left wide open to make it easier for Windows users to convert. The one thing I've never liked is setting permissions on users home directorys to 755 by default. I don't want other users snooping through my home directory, so I always set the permissions to 700 on all home directories.

I get the following output when I run chage -l

```

sudo chage -l cariboo
[sudo] password for cariboo: 
Last password change					: Aug 20, 2010
Password expires					: never
Password inactive					: never
Account expires						: never
Minimum number of days between password change		: 0
Maximum number of days between password change		: 99999
Number of days of warning before password expires	: 7
```

---

### Post by georgemc on 2010-08-26
Going out on a limb here.  It's been awhile since I messed with security settings, i.e. configuring systems to comply with company policies.  And I know there are more knowledgeable people in these forums.
 

 I suggest you might want to look into the man pages for:
 

 man passwd
 man shadow
 man login.defs
 

 I did a really quick scan on those pages and started to get flash backs for the olde Unix days (mid 80s and 90s).  The shadow and login.defs pages describe in gruesome detail how to manipulate most if not all of those password settings.
 

 I think part of what you are looking for is in the login.defs.  There is a section called “Password aging controls:”, see if that does what you need.



For Cariboo: FYI right above the “Password aging controls:" section in login.defs is the “UMASK” definition.
 

 Hope this can point you in a direction that helps.
 

 George

---

### Post by gamblor01 on 2010-08-26
Thanks georgemc -- I looked at /etc/login.defs and it defines essentially the same information that the chage command controls:

> 
#
# Password aging controls:
#
#       PASS_MAX_DAYS   Maximum number of days a password may be used.
#       PASS_MIN_DAYS   Minimum number of days allowed between password changes.
#       PASS_WARN_AGE   Number of days warning given before a password expires.
#
PASS_MAX_DAYS   90
PASS_MIN_DAYS   1
PASS_WARN_AGE   7
That's all well and good for people that haven't been prompted to change their password yet but in my case, I have already had to change it.  :(


However, the good news is that reviewing the man page for passwd got me back around to reviewing the pam file (specifically /etc/pam.d/common-password).  I was trying to change lines in this file before but what I didn't realize until now is that the file seems to be automatically updated when you run pam-auth-update.  And to be fair, I had conflicting password policies  (it looks like the default policies conflicted with those imposed by my employer) and needed the --force option.  So I just disabled the "passwdqc password strength enforcement" option and viola!  Now I can use my old password again.

So to summarize, here is what I did:

1. Run the command:  **sudo pam-auth-update --force**

2. Use tab/spacebar/arrows to navigate the menu, and disable the "passwdqc password strength enforcement" option.  Click on OK to save the changes.

3. Run the password command as root and I can set the password to whatever I want:  **sudo passwd <username>**



Hooray!  Problem solved -- I'll change the subject to mark it as such.

---

### Post by OpSecShellshock on 2010-08-26
I haven't modified any of the password defaults since installation and I got the same output as cariboo907. I suspect that if a password change requirement is in place, it's a non-default setting. On a single-user home computer there's really no reason I can think of to regularly change passwords at all. In the enterprise it tends to be more about standards compliance than actual risk management.

---

### Post by BkkBonanza on 2010-08-26
Thanks gamblor01 for updating with solution.
I checked my "chage" and it has the same defaults as cariboo907. So presumably they haven't changed anything in Lucid by default, but your employer must have customized things. Good to know a bit more about this.

---

### Post by gamblor01 on 2010-08-26
Yeah once I found that info I figured it was something imposed by the package layer that work installed.  My current password already meets their security policy so I'm not too worried about it.  Cheers everyone.

---

### Post by OpSecShellshock on 2010-08-27
While I really don't like to encourage circumvention of workplace security policies, what I dislike even more are stupid policies that basically say "here, have full administrative access to the computer--but don't use it." What's the point of having certain password requirements if users are just able to go in and edit them to their liking? I suppose they should have been a bit more granular with their access controls before deploying the systems (for it's certainly possible to do so). Anyway, not the OP's problem. However, going forward the fact that it was relatively easy to do might adversely affect wider enterprise penetration for the OS unless there's a good place to find enterprise-oriented access control tutorials.

---

### Post by gamblor01 on 2010-08-27
> **OpSecShellshock said:**
> While I really don't like to encourage circumvention of workplace security policies, what I dislike even more are stupid policies that basically say "here, have full administrative access to the computer--but don't use it." What's the point of having certain password requirements if users are just able to go in and edit them to their liking? I suppose they should have been a bit more granular with their access controls before deploying the systems (for it's certainly possible to do so). Anyway, not the OP's problem. However, going forward the fact that it was relatively easy to do might adversely affect wider enterprise penetration for the OS unless there's a good place to find enterprise-oriented access control tutorials.
To be fair though, this is my own laptop which I administer.  I personally installed Ubuntu on this machine and then applied a "layer" which essentially installed a large amount of packages to get all of the work-related programs.  Thus, I am the admin of the system and obviously in the list of sudoers.  The rules would certainly be changed if someone else had installed the system for me and my id was not in the sudoers list.

There are certainly users that have their OS installed for them and do not have admin access.  It happens in the enterprise quite often, even with Windows workstations so I don't see why it couldn't also happen with Ubuntu or any other flavor of Linux.  Though I do software support -- and drives me crazy when I need the user to install something in order to resolve their problem and they can't!  ;)

I think it's more the lack of support for certain pieces of software that prevents Linux from being widely used as workstations in the enterprise such as no Outlook, no Office support (not without Wine anyway, which isn't a pay-for-support model), in-house programs that were all originally designed for Windows, etc.  I could really care less what other people want to run as long as the necessary tools exist for me to perform my job on Ubuntu though  :D

> 
You know, you can act like an angry a*hole if you want to, it won't  endear you to anyone in this life though. You're not the first person on  earth to have a password issue.

If it bothers you that much then take the " lazy/novice way out of  things" and stop being so snotty to people still getting their own head  around this thing. 
Sorry you feel like I'm being rude -- I suppose I could have reworded some things.  I appreciate you took the effort to post but was really just trying to set things straight.  I constantly hear people stating things that simply aren't true.  This information propagates at an exponential rate when posted on the Internet, especially when it's posted on a site as prevalent as this one.

---

### Post by DavidOfLondon on 2010-08-27
Actually I was sitting watching videos on YouTube and eating Reese's Pieces quite calmly. The guy wanted to beef out on someone because he couldn't change a password. He used the phrase "lazy/novice way out of things".

....I love it when people pick sides with bad information.

Ciao.

---

### Post by cycling-rod on 2010-08-27
Thanks to everyone who took part in this "Discussion", I found it very interesting and informative!

---

### Post by dmackenzie on 2013-01-29
Thanks @gamblor01 for the information regarding the sudo pam-auth-update command. It helped fix my issue.

---

### Post by howefield on 2013-01-29
Old thread closed.

---

