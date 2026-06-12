---
title: "why linux doesnt need an antivirus?"
date: 2007-05-07
forum: The Cafe
---

### Post by eldragon on 2007-05-07
ok. ive been wondering lately, why we dont need an av, other than spreading mail to windows users...

is it really because linux is more secure? or really because the linux userbase isnt big enough for virus/troyan/spam bot writes to care about?

can anyone explain in words everyone can understand, why we dont really need an antivirus? or if we need one, why and which is the better alternative?

---

### Post by bonzodog on 2007-05-07
For a virus to be really effective, it needs to infect the root tree;

In windows, this is easy - you do not need a password to write to the root area of the drive, and thus the system files.

In Linux, being a true multi-user system, this is by default protected by an encrypted password, and thus, if a virus was to download itself to your user account, it could not get into the root system without asking for you to enter the password first. Thus the viral effect is nullified. The only thing that could get around this is a rootkit, and they are generally much more complicated pieces of software, and harder to create. A rootkit typically expoits a security hole in the kernel to get access to the kernel space, and thus can really cause a lot of damage. However, these holes are patched very fast when found, often within hours, due to the open source nature of Linux.

---

### Post by euler_fan on 2007-05-07
I've seen a variety of reasons posted in response to this question over time:

1) There aren't enough of us for the black hats to care yet.
2) Linux is that much more secure
3) Linux is enough more secure that it is too much effort to hack the average Linux user when there are so many easy to hack Windows users out there
4) (3) and with multiple distributions using multiple package bases any virus targeted at Linux is a bit of a crap shoot in terms of effectiveness
5) (3) and by the time the community gets done reviewing a piece of software we've found many of the security holes that might have been left.

Please chime in if I have missed one.

---

### Post by rai4shu2 on 2007-05-07
Hackers are lazy and prefer to hit easier targets.

---

### Post by forrestcupp on 2007-05-07
> **bonzodog said:**
> 
In windows, this is easy - you do not need a password to write to the root area of the drive, and thus the system files.


This is one of the only things they did right in Vista.  They made each part of the OS it's own compartment that can't be violated by other compartments.  Where before, someone could write a virus that used the print driver to exploit the whole system, now that virus will be contained in the printer compartment.  So a virus can only mess up the compartment that it originates in.

I may be wrong, but I think in Linux, about all a virus could affect would be the home directory.

---

### Post by ssam on 2007-05-07
another possible reason

to make a virus you need to know a system very well.

by the time you know this much about windows you are probably very frustrated with it. you are up against the closed source wall. you can see bugs in windows but can't fix them. your urge to destroy rises.

to learn this much about linux, you are probably looking at the source code to the kernel, or server programs. your life is filled with joy of having full access to see the source and make changes to it.

---

### Post by DoctorMO on 2007-05-07
It's also worth noting that an AV program is really a bad excuse for good OS security and regular code fixes.

why have a program that removes infected code if the code never has a chance to run?

---

### Post by euler_fan on 2007-05-07
> **DoctorMO said:**
> It's also worth noting that an AV program is really a bad excuse for good OS security and regular code fixes.

why have a program that removes infected code if the code never has a chance to run?

I almost completely agree. While there is no substitute for code fixes and good OS security, there is a role for AV. Namely catching the stuff that gets past your regular security measures. The same goes, in my mind, for IDS.

---

### Post by samjh on 2007-05-07
Linux is vulnerable to viruses and trojans, but they need to be somewhat more sophisticated than those that affect early versions of Windws.

Windows runs the vast majority of the world's desktop computers, so it is the most obvious target for anyone who wishes to cause huge mayhem.  Hunting down Windows is also a fashionable thing to do for any computer nerd with nefarious desires, much more so than damaging Linux or Unix systems.

Linux is more secure, but the extra security is more due to the existence of controlled package distributions and the wide-spread use of code-reviewed open source software, rather than only due to Linux's technical merits.  Linux is as vulnerable as Windows when running as a super user (ie. su or sudo), which happens quite a lot.

---

### Post by Jonne on 2007-05-07
Not enough idiots are using Linux yet. That's why. An idiot with the root password will screw up his box, and if he doesn't have a root password, he'll manage to delete his home directory in some way. If I were to  put up a website with .debs that promise smileys or screensavers, which also contain a keylogger/spambot, there will be an idiot that installs it.

With any OS you'll have people that run whatever they get in their mailbox/through instant messages, apparently these people just won't learn, and ruin it for the rest. There are even viruses that pack themselves into a password protected zip file, with the password in the e-mail, and even those manage to spread.

Also, look at this [example of an os X virus](http://www.ambrosiasw.com/forums/index.php?showtopic=102379). Someone posted a virus on some board, and people were dumb enough to run it. 

I don't believe antivirus software is a solution, though. People just need to start *thinking* before running untrusted code. (I run Windows at work without an antivirus, and as admin, I've never had any problems because I don't use IE, and I don't run stuff that's obviously bad).

One thing that will probably become a bigger problem when Ubuntu (or Linux/BSD in general) becomes popular is the  constant dictionary attacks on ssh and vnc ports. IMHO Ubuntu should install and set up fail2ban or a similar thing if you install ssh/vnc. ssh and vnc aren't installed and active by default (luckily), but enough people enable it because it's damn convenient to get to your box from the net. All these people are at risk of getting 0wned by a brute force attack. And once they're 0wned, they become part of the botnet that attacks other hosts.

---

### Post by Tipo on 2007-05-07
I'm a fan of the view of the OS itself being more secure.... As stated eariler, *nix is a true multi-user system and it is difficult to gain access to the root to do some real damage.

That, combined with lightning fast response times in Linux development kills almost everything.  I've noticed this on OS X as well; when a (potentially dangerous) security hole is found, Apple is usually pretty good with creating a patch, ususally within a day or two. Linux is better in this respect, seeing as we have wonderful people figuring these things out in a matter of hours, not days :)

---

### Post by 3rdalbum on 2007-05-07
> **forrestcupp said:**
> This is one of the only things they did right in Vista.  They made each part of the OS it's own compartment that can't be violated by other compartments.  Where before, someone could write a virus that used the print driver to exploit the whole system, now that virus will be contained in the printer compartment. 

100 Reasons why Windows Vista is more secure than OS X:

#57  OS X runs its printing system (CUPS, with network access) as root, and Vista does it the Unix way with the printing system running under its own kind of account.

---

### Post by Jonne on 2007-05-07
One thing that is better in Linux (and BSD) compared to OS X and Windows, is that for Linux there are no managers that can push feature X into the system because the marketing dept. decided it would sell them more licenses, even though feature X is a bad idea from a security / stablity standpoint.

Examples are ActiveX (giving the browser access to the whole OS!), adding advanced scripting features/DRM in media container formats (wma/wmv/quicktime, each of those formats has had security issues).

But as I said before, no OS will protect you against PEBKAC...

---

### Post by jrusso2 on 2007-05-07
> **forrestcupp said:**
> This is one of the only things they did right in Vista.  They made each part of the OS it's own compartment that can't be violated by other compartments.  Where before, someone could write a virus that used the print driver to exploit the whole system, now that virus will be contained in the printer compartment.  So a virus can only mess up the compartment that it originates in.

I may be wrong, but I think in Linux, about all a virus could affect would be the home directory.

Well if you think about it most users store their Data in the /home.  So a virus there would be quite successful.

I think Linux is susceptible to a virus that is user activated just like Windows.  But maybe the users are not dumb enough to activate it.

Most people that use Linux get their software from a nice safe repository not all over the internet where it might be malicious software.

---

### Post by 3rdalbum on 2007-05-07
> **Tipo said:**
> I've noticed this on OS X as well; when a (potentially dangerous) security hole is found, Apple is usually pretty good with creating a patch, ususally within a day or two. Linux is better in this respect, seeing as we have wonderful people figuring these things out in a matter of hours, not days :)

And the distributions push fixes out to users within, at most, a couple of days; whereas OS X has had some critical problems unfixed for 4 months even though a fix actually exists.

---

### Post by macogw on 2007-05-07
I'm sure there are users dumb enough to activate it.  My family uses Ubuntu, so that's at least 2 kids and a mom.  The thing is, if they're dumb enough to activate a virus, they're probably too dumb to compile source they found on the web (actually, probably afraid to).  They'll use Synaptic's little checkboxes because they're easy.  Synaptic isn't full of viruses, so they're safe.

Jonne, if you don't have AV, how do you know your computer's not infected?  Viruses don't always make themselves known.  They might just keylog or send out spam.  It doesn't matter one bit if you use IE or download dubious things.  If you don't have a very well hardened firewall, you're toast on Windows.  There are viruses (ex: msblaster) which portscan bunches of computers at a time and install to any on which they find open ports, then use that computer as a host from which to scan and install on more computers.  You don't have to do anything but plug in the network cable.  Don't say "I looked at the process manager" or anything as stupid as that either.  Even userspace rootkits like Hacker Defender will make the process manager look normal, tell you that nothing's listening on any ports, report lower RAM usage than is real, report more free hard drive space than real (so you can't go "gee, there's 50mb of free space missing, what got installed?), hide malicious registry keys, etc.  A userspace rootkit detector should find Hacker Defender.  A kernelspace rootkit detector will definitely find it, but there are a myriad of them out there.  Some rootkits are kernelspace, and then kernelspace detectors will not tell you they are there.  They are the worst rootkits because they fly under the radar no matter what you do.

Windows' firewall by default is set up almost as poorly as Ubuntu's.  I think it is set to block most inbound traffic (except for common messaging and internet protocols), but it does not block outbound traffic at all.  Ubuntu's doesn't block anything by default (I'm serious, run "sudo iptables -L" and you'll see what I mean).  I used Firestarter set to "restrictive" and then opened up just what ports I need for IRC and XMPP and AIM, which is how a firewall is supposed to be set up.  My computer *should* be secure now, but I'm still going to try to get a friend to pen-test it.  Anyway, though, on Windows you'd better configure the firewall *by hand* so that it really does block things going in and out.  Blocking incoming only is NOT good enough.  Keyloggers can still send info out.  You can still spam people. Block both directions except for the specific protocols you need.

-------------------

To answer the question: 
Marketshare cannot explain Linux's lack of viruses.  Linux runs the internet.  Any hacker with a brain will try to take down a server and inconvenience 50,000 people instead of take down one box and inconvenience a family of 5 (though of course, get enough of these on a botnet and you can make a lot on "high volume email sales" or steal plenty of credit card numbers).  Still, one server to get a full database of that info in one shot is a better choice for your average black hat.  

Open source stuff gets patched more immediately than Windows does.  Windows users get patches on the 2nd Tuesday of the month.  Smart hackers release their stuff the 2nd Wednesday and get a full month with it.  Our patches get out ASAP so hackers can't count on a month.  They can hope for 3 or 4 days.  that discourages even bothering to tamper with our stuff.  It's not as worth it.

Next add in that random code cannot execute itself.  You have to initiate it.  If it does, it can get your files, but not the system (unless you run it as root for some stupid reason....Ubuntu does not allow this by default so yay).  Most people would rather the system go and they keep their files, so this isn't really so huge.  Still, passwords are stored in /etc not in /home, so if it gets in your /home, your password (in case you or another user on your computer likes to use the same password for everything) is safe from being stolen.  If you have a text document with your SSN, passwords, mother's maiden name, date of birth, and address sitting in your home drive, well...A) why? B) that's dumb C) they get that and you're screwed.

Finally, it's harder to do auto-hacks on Linux because of how the systems are all configured differently.  Debian's file system hierarchy doesn't match Gentoo's which doesn't match Red Hat's.  The automatic thing would have to be specific to your distro's hierarchy to know what it's doing.  That means more manual hacking like running password crackers.  On most distro, you know to use "root" and then crack the password.  Since root is locked on Ubuntu, they can't just use "root" as the name and would have to crack your username AND your password, so Ubuntu gains some points there (to make up for the wide open firewall).

Note: please replace all instances of the word "hacker" with either "cracker" or "black hat" as you see fit.

---

### Post by slibuntu on 2007-05-07
> **ssam said:**
> another possible reason

to make a virus you need to know a system very well.

by the time you know this much about windows you are probably very frustrated with it. you are up against the closed source wall. you can see bugs in windows but can't fix them. your urge to destroy rises.

to learn this much about linux, you are probably looking at the source code to the kernel, or server programs. your life is filled with joy of having full access to see the source and make changes to it.

Thats an excellent, insightful point

---

### Post by Hendrixski on 2007-05-07
> **macogw said:**
> 
To answer the question: 
Marketshare cannot explain Linux's lack of viruses.  Linux runs the internet.  Any hacker with a brain will try to take down a server and inconvenience 50,000 people instead of take down one box and inconvenience a family of 5 (though of course, get enough of these on a botnet and you can make a lot on "high volume email sales" or steal plenty of credit card numbers).  Still, one server to get a full database of that info in one shot is a better choice for your average black hat.  

Open source stuff gets patched more immediately than Windows does.  Windows users get patches on the 2nd Tuesday of the month.  Smart hackers release their stuff the 2nd Wednesday and get a full month with it.  Our patches get out ASAP so hackers can't count on a month.  They can hope for 3 or 4 days.  that discourages even bothering to tamper with our stuff.  It's not as worth it.


Finally a smart answer.  I can't stand the people who think that desktop market share somehow impacts the number of viruses that are written for Linux.  That theory is R E T A R D E D! If it were true, then Linux would be a larger target seeing as how it holds a huge market share in the Server, supercomputer, and embedded systems, markets.  Those are much higher value targets than family desktops.

Linux is OPEN SOURCE, and THAT provides immeasurable security.  let me explain:

viruses are like criminals, they're unethical programs.  If a criminal wants to do something unethical they do it in the shadows, or where nobody can see them,  Viruses too, prefer to work out of plain sight.  If everything is transparent, if there are no walls, if everyone can see what you do, you will not do something wrong because you know it won't work, and you'll get punished.  If all of the code is transparent, the virus cannot do what it needs because it will be easily spotted, removed, and will not propagate.   

**To re-iterate.  Linux does not have unethical programs like Viruses, spyware, or DRM because Linux is an ETHICAL OPERATING SYSTEM.  Very simple.**

---

### Post by Jonne on 2007-05-07
> **macogw said:**
> Jonne, if you don't have AV, how do you know your computer's not infected?  Viruses don't always make themselves known.  They might just keylog or send out spam.  It doesn't matter one bit if you use IE or download dubious things.  If you don't have a very well hardened firewall, you're toast on Windows. 
First of all, even *if* you have a virus scanner, you can't be sure either, as they never catch everything. I can't even be sure if my Ubuntu box doesn't have a rootkit. The only way to be completely sure is to run the liveCD 24/7 ;) . I keep an eye on traffic, running processes, connections, etc, and I only install software that is widely used and preferibly open source.

As for Blaster and friends: I'm behind a NAT router, so these don't stand a chance. And Blaster was a worm that exploited a vulnerability that was *already* patched by M$, so if anyone got infected, they either had it coming, or they were installing Windows and got rooted before they were able to patch the machine.

I gave up on antivirus software after it became clear they don't protect you from obvious malware like Bonzi Buddy. Since spyware companies could sue antivirus vendors for blocking their software, the vendors didn't add protection for those.

Keep your machine patched, use a NAT router/firewall, don't use IE, and don't be an idiot. That keeps you safe on any OS.

AV software like Norton and McAfee are bloated, too invasive, they use tons of resources and don't protect you from everything anyway.

---

### Post by mech7 on 2007-05-07
> **Jonne said:**
> 
AV software like Norton and McAfee are bloated, too invasive, they use tons of resources and don't protect you from everything anyway.

Nod32 is great it is very little resources and very good protection.

---

### Post by NESFreak on 2007-05-07
> **samjh said:**
>  Linux is as vulnerable as Windows when running as a super user (ie. su or sudo), which happens quite a lot.

I'd say even more vulnerable. A simple "sudo rm -Rf /" would erase the whole system.

Windows was designed to be run root. Therefore it contains more security measurements than Linux on root level. Try for instance as admin formating your C: drive. You can't. Windows is constantly monitoring all your actions, and a soon as it detects something it doesn't you (or a virus) to do, it doesn't allows it. The trick for viruswriters is to do things the OS does allow, mask things or install back doors. This way windows won't detect it. This won't be possible in Linux since you need to be root for this. So within linux the trick would be to get root-access by means of social-engineering. Which as linux becomes more widespread could become a mayor problem. Something like offering an update through email. A simple gksudo and most people would just enter their password, without ever getting to know what crashed their desktop/slowed their internet connection.

You may never believe people could be so stupid, but if you look how many 'send this mail or the holy internet spirit will kill you'  I get. (3 last week from people I unfortunately know).

I think even some Microsoft dude said it once. The user is the weakest link of an OS.
And personally i think that since sudo gives you total control, Linux has the weakest defenses.

This could be partly solved by not letting everybody be full root. (--> allow everybody to install updates, and use ubuntu install/remove thing. But don't allow root-access by other applications, like synaptic. a sort of semi-root)

NESFreak

---

### Post by Nikron on 2007-05-07
In my humble opinion, it's probably because Linux users, in general are just more computer literate than Windows users.  That and the obvious benefits of being open source have always made the system more secure.  But if/when linux starts expanding and gaining more market share, we'll have a big problem.  Because linux was built on the assumption that the user is competent.  Linux's root really is _root_god_of_the_computer_ while the Windows admin is a 2 or 3 levels below root(don't know, it's been a while).  And so the user has great potential to royally screw up his computer.

---

### Post by DoctorMO on 2007-05-07
> This could be partly solved by not letting everybody be full root. (--> allow everybody to install updates, and use ubuntu install/remove thing. But don't allow root-access by other applications, like synaptic. a sort of semi-root)

I don't think you understand how linux works well enough to propose a solution to a problem that does not yet exist.

In answer to your social engineering, it's more likely that ubuntu and other linux varients will create an account that isn't in /etc/sudoers set that up by default while having a setting to allow users into sudoers.

Your also forgetting about SELinux and various other security solutions which are not installed by default at the moment but which could be in the future.

---

### Post by Mateo on 2007-05-07
why do people act like destroying your home directory is no big deal.  it's a huge deal!  if you use a finance application, all of your financial information would be destroyed (or stolen).  That could be very verybad.

---

### Post by dasunst3r on 2007-05-07
It is also interesting to note that there are probably many servers that run Linux and contain boofloads of information.  If hackers want to get all our info in one shot, why not hit a goldmine?

---

### Post by Nikron on 2007-05-07
> **dasunst3r said:**
> It is also interesting to note that there are probably many servers that run Linux and contain boofloads of information.  If hackers want to get all our info in one shot, why not hit a goldmine?

I'm going to venture to say that 1. the average server administer will probably not fall victim to social engineering 2.  that server security configurations > desktop configurations

---

### Post by eldragon on 2007-05-07
ahhh ok....so thats what i feared...

multiuser aproach, intelligent user, and root password :)
of course open sourced software gets lots of reviews too..

cheers everyone ;)

---

### Post by jputman01 on 2007-05-07
so if a virus could be made that would in effect only attack the /home directory, since it doesnt have permission to go anywhere else, where is a good place to store and sensative information. I currenty have 20-25 passwords and I try to use different ones and i change them often, but if I did have a list or something where could one store personal info in order to keep it safe?

---

### Post by Nikron on 2007-05-07
> **jputman01 said:**
> so if a virus could be made that would in effect only attack the /home directory, since it doesnt have permission to go anywhere else, where is a good place to store and sensative information. I currenty have 20-25 passwords and I try to use different ones and i change them often, but if I did have a list or something where could one store personal info in order to keep it safe?

There's a key chain utility.  I don't use it though, so I can't really tell you more than that.

---

### Post by Barrius on 2007-05-07
> **mech7 said:**
> Nod32 is great it is very little resources and very good protection.

I'' second that recommendatino for ESET/NOD32.  Our company WAS using Norton's corporate AV, yet we were plagued by virii.   We swapped to NOD32 and have yet to get another (over 2 years virus free).   And it's fast!

---

### Post by goumples on 2007-05-07
I use an anti-virus on Linux anyway.  Maybe windows made me paranoid (due to all the times I had to restore due to Mal-ware infections), but I'd rather be safe than lose an afternoon trying to rescue my system. AVG is one of the best free anti-virus programs I've seen, if anyone is interested.

---

### Post by christhemonkey on 2007-05-07
I use clamwin AV and it suits me fine, found and got rid of everything (admitadly only 2 viri, both probs from running windows XP on the internet without a firewall) that its had thrown at it so far!!

---

### Post by macogw on 2007-05-07
> **Jonne said:**
> First of all, even *if* you have a virus scanner, you can't be sure either, as they never catch everything. I can't even be sure if my Ubuntu box doesn't have a rootkit. The only way to be completely sure is to run the liveCD 24/7 ;) . I keep an eye on traffic, running processes, connections, etc, and I only install software that is widely used and preferibly open source.

As for Blaster and friends: I'm behind a NAT router, so these don't stand a chance. And Blaster was a worm that exploited a vulnerability that was *already* patched by M$, so if anyone got infected, they either had it coming, or they were installing Windows and got rooted before they were able to patch the machine.

I gave up on antivirus software after it became clear they don't protect you from obvious malware like Bonzi Buddy. Since spyware companies could sue antivirus vendors for blocking their software, the vendors didn't add protection for those.

Keep your machine patched, use a NAT router/firewall, don't use IE, and don't be an idiot. That keeps you safe on any OS.

AV software like Norton and McAfee are bloated, too invasive, they use tons of resources and don't protect you from everything anyway.
Norton & McAfee suck anyway :p AVG is very good.  A combination of Spybot S&D and AdAwareSE can get the usual malware issues, but I think Bonzai Buddy is more of a "bundling" problem ("by clicking I Agree you agree to these terms of service...allow us to install software which shows advertising based upon...." sort of thing).  Those things are annoying.  AV doesn't protect you from anything usually, this is true.  It'll alert you to problems so you can repair whatever is letting the viruses get in though.  Norton & McAfee actually do have one thing over AVG, and that's their real-time scanning which means they can tell when something is "up to no good" while AVG just scans daily and tells you if something bad is installed.  I'd still prefer AVG because the system runs without problems when you use it.

---

### Post by Jonne on 2007-05-07
I only picked Norton and McAfee because by now everyone knows they suck. But every AV app uses resources one way or another.

---

### Post by mech7 on 2007-05-07
> **Jonne said:**
> I only picked Norton and McAfee because by now everyone knows they suck. But every AV app uses resources one way or another.

Yeah and if you turn your pc off it doesn't use any resources ::lolflag:

---

### Post by hsweet on 2007-05-07
In linux you have to give permission to a file to be run as an executable. In winx you click on a .exe, com, .whateverelseruns and it run.  Click.... too late.

That slows things down in the email virus dept a bit.  If you are enough of an idiot to try to run a program  from an  email, you probably are also dumb enough not to know how to give executable permission to that script (unless the email gives you step by step directions and you go ahead and to it.)  Even then you can't do too much damage if you are not root.

I did once (twice) get hacked on an old redhat system running as a webserver, but that was not a virus, some kind of stack overflow via irc.  (a while ago so i forget the details.)  That went away after a firewall was set up.

---

### Post by aysiu on 2007-05-07
> **hsweet said:**
> In linux you have to give permission to a file to be run as an executable. In winx you click on a .exe, com, .whateverelseruns and it run.  Click.... too late. The advent of gDebi by default to Ubuntu installations negates that argument. All people need is a .deb attachment for "cool program"--double-click it, enter your password, you're screwed.

---

### Post by jiminycricket on 2007-05-07
> **Mateo said:**
> why do people act like destroying your home directory is no big deal.  it's a huge deal!  if you use a finance application, all of your financial information would be destroyed (or stolen).  That could be very verybad.

Like Doctor MO said, SELinux and other mandatory access control policies (like AppArmor, although that has a bit of controversy) seek to solve that problem.  I believe that it's integrated into Fedora 7 and RHEL 4 right now, if you want to test it out.

[http://en.wikipedia.org/wiki/Mandatory_access_control](http://en.wikipedia.org/wiki/Mandatory_access_control)

---

### Post by Pdennis on 2007-05-07
because virus writers use Linux and they don't want to pee in their own bathtub, so to speak.

I'm just kidding.. Linux users have better things to code :)

---

### Post by hsweet on 2007-05-07
good point

---

### Post by eldragon on 2007-05-07
> **jputman01 said:**
> so if a virus could be made that would in effect only attack the /home directory, since it doesnt have permission to go anywhere else, where is a good place to store and sensative information. I currenty have 20-25 passwords and I try to use different ones and i change them often, but if I did have a list or something where could one store personal info in order to keep it safe?

well, im actually having a backup being run under root privileges to a root read/write only folder on a second drive every night.... it works really great, and its incremental using hardlinks.......never had the chance to eventually restore anything, but seems like a nice idea if you ask me....

if you have sensitive information on your computer, being osx, windows, or linux, you should backup, its your fault if you lose it, not virus writers, who actually care more on spamming than deleting your mariah carey mp3s

i found backing up on linux much more hassle free than on windows....i dont do a full backup, id rather reinstall....but pictures, mails and FF's bookmarks are a must.

the rest is expendable........

---

### Post by jiminycricket on 2007-05-08
Great automatic, incremental web-based backup server, for anyone interested in this topic; much better than Windows Home Server that MS is coming out with:

[http://www.howtoforge.com/linux_backuppc](http://www.howtoforge.com/linux_backuppc)

---

### Post by PartisanEntity on 2007-05-08
Correct me if I am wrong, but if you have folders in your /home that contain data and files that you would like to give some added protection, would it not be wise to change their ownership to root?

Then, whenever you need to access those folders you first change their ownership to your log-in profile, use them/edit them, then when you are done you change the ownership back to root.

That way your sensitive files in /home are protected from any code that might be programmed to wipe your /home directory clean. Or from some remote hacker who managed to gain access to /home.

Would this be a good idea to implement?

---

### Post by eldragon on 2007-05-08
> **PartisanEntity said:**
> Correct me if I am wrong, but if you have folders in your /home that contain data and files that you would like to give some added protection, would it not be wise to change their ownership to root?

Then, whenever you need to access those folders you first change their ownership to your log-in profile, use them/edit them, then when you are done you change the ownership back to root.

That way your sensitive files in /home are protected from any code that might be programmed to wipe your /home directory clean. Or from some remote hacker who managed to gain access to /home.

Would this be a good idea to implement?

that would be extremely cumbersome.....
it will end up being neglected by the user, and never switching back to root privileges.....

thats why i decided to run the backup under root, only way i need to access the backups is if i have a mishap, which i dont plan to...... :)

in the future, my backup drive will be a usb drive hidden under the desktop to protect me from computer theft. :) (in some way)

---

### Post by rai4shu2 on 2007-05-08
Sensitive files anywhere on your computer should be encrypted and the password made strong and kept safe.

---

### Post by eldragon on 2007-05-08
> **rai4shu2 said:**
> Sensitive files anywhere on your computer should be encrypted and the password made strong and kept safe.

and then write that strong 2048bit password with lemon juice on a white paper, and hide it on a secure safe, and drop it into the ocean...
:lolflag:

---

### Post by ali4949 on 2007-05-08
In general people using Linux as OS are more savy than your average windows user, which explains the lack of viruses on linux. People think a little bit more before they start clicking and installing crapware on linux machines. That I think is the biggest reason for LInux OS not infected with viruses.

---

### Post by az on 2007-05-08
> **DoctorMO said:**
> It's also worth noting that an AV program is really a bad excuse for good OS security and regular code fixes.

why have a program that removes infected code if the code never has a chance to run?

As has been said, open source can turn on a dime.

> **euler_fan said:**
> I almost completely agree. While there is no substitute for code fixes and good OS security, there is a role for AV. Namely catching the stuff that gets past your regular security measures. The same goes, in my mind, for IDS.

Your OS should be able to update/adapt as quickly as your virus list.

The big reason that Windows cannot adapt is because of binary compatibility.  Binary compatibility enables anyone to click on an exe written for windows 95 and it should still run well on Vista.  When you make a product that is committed to being binary compatible on such a big scale, you are bound to lose performance, scalability and flexibility to innovate.

Free-libre open souce does not make such a promise.  Does that mean that users need to compile stuff from source all the time?  No, but they can't click on stuff willy-nilly like windows users.  That's why there are distros.  You pick your distro and you rely on it to provide you with your software from a centralized repository.

> **macogw said:**
> Next add in that random code cannot execute itself.  You have to initiate it.  If it does, it can get your files, but not the system (unless you run it as root for some stupid reason....Ubuntu does not allow this by default so yay).  Most people would rather the system go and they keep their files, so this isn't really so huge.  Still, passwords are stored in /etc not in /home, so if it gets in your /home, your password (in case you or another user on your computer likes to use the same password for everything) is safe from being stolen.  If you have a text document with your SSN, passwords, mother's maiden name, date of birth, and address sitting in your home drive, well...A) why? B) that's dumb C) they get that and you're screwed.

The theory that user priviledges protect your system and that a cracker can only access your home drive is false.  There are lots of ways for a cracker to become root.

Regardless of what permissions the desktop user has, a cracker can exploit a vulnerability and become root.  Ideally, there would be no vulnerabilities to exploit, but there always are.  Even code that is years old can still get audited and patched for potential security risks.  There is no metric to accurately assess whether the open source developement model is more efficient at finding and fixing exploits than proprietary software.

> **macogw said:**
> 
Finally, it's harder to do auto-hacks on Linux because of how the systems are all configured differently.  Debian's file system hierarchy doesn't match Gentoo's which doesn't match Red Hat's.  The automatic thing would have to be specific to your distro's hierarchy to know what it's doing.  That means more manual hacking like running password crackers.  On most distro, you know to use "root" and then crack the password.  Since root is locked on Ubuntu, they can't just use "root" as the name and would have to crack your username AND your password, so Ubuntu gains some points there (to make up for the wide open firewall).


The distros are disparate, but I don't think that contributes a lot to safety.  I think the lack of binary compatibility counts for a lot, but regarding how a distro is configured is pretty trivial.  The toolchain is the same everywhere, as is the filesystem. Most of the time, a Suse desktop will be running the same apps (same upstream versions) as Ubuntu or Fedora.

> **ali4949 said:**
> That I think is the biggest reason for LInux OS not infected with viruses.

Maybe, but it doesn't hold true in the opposite sense.  Even if you are a savvy user, you *cannot* plug your windows computer into the net without a virus scanner, malware scanner and firewall.  How do people live like that?

---

### Post by Blondie on 2007-05-08
> **euler_fan said:**
> I've seen a variety of reasons posted in response to this question over time:

1) There aren't enough of us for the black hats to care yet.
2) Linux is that much more secure
3) Linux is enough more secure that it is too much effort to hack the average Linux user when there are so many easy to hack Windows users out there
4) (3) and with multiple distributions using multiple package bases any virus targeted at Linux is a bit of a crap shoot in terms of effectiveness
5) (3) and by the time the community gets done reviewing a piece of software we've found many of the security holes that might have been left.

Please chime in if I have missed one.

Possibly also

6) Linux users are probably more likely to have the skills to detect and deal with such a threat, though since Linux virii have so far been as visible as yetis this is rather hypothetical.

---

### Post by slimdog360 on 2007-05-08
BSD rocks

---

### Post by euler_fan on 2007-05-08
I completely agree with the above posts that between secure repositories and an oft-updated OS there is little need for AV.  There is no substitute for not being vulnerable in the first place. And I must agree that an OS with two remote execution exploits in the kernel in 10 years (OpenBSD) is a pretty amazing feat and to be aspired to by all.

Let me just say I also am pessimistic enough to believe in defense in depth. I think of the historical analogy of a castle: every time someone invented a new way to build a castle, someone else came up with a new way to attack them.

The same goes for computers. Ergo, AV and especially IDS are ways to see if anyone slipped something past the usual defenses. It simply pays to be careful. No one bats 100% on security. If I catch one security breach ever then I will consider the time and effort spent learning and using ClamAV, OSSEC-HIDS and SNORT to be worth the effort.

---

### Post by euler_fan on 2007-05-08
> **Blondie said:**
> Possibly also

6) Linux users are probably more likely to have the skills to detect and deal with such a threat, though since Linux virii have so far been as visible as yetis this is rather hypothetical.

I would hope so, but as Linux continues to build market share this will slowly erode. I wish it would not, but that's life I'm afraid. ](*,)

---

### Post by NESFreak on 2007-05-09
> **DoctorMO said:**
> I don't think you understand how linux works well enough to propose a solution to a problem that does not yet exist.

In answer to your social engineering, it's more likely that ubuntu and other linux varients will create an account that isn't in /etc/sudoers set that up by default while having a setting to allow users into sudoers.

Your also forgetting about SELinux and various other security solutions which are not installed by default at the moment but which could be in the future.

As ubuntu becomes more widespread, more people will start using it. This will (if everything goes the way we want it to) in the end include many users who cannot judge for themselves, what program to and what program not to give root access. If one of those people would start using linux right now, they could easily find themselves destroying important system dependencies and stuff. (Or let a virus do it for them, if there would be any in the future) If ubuntu becomes linux for the masses i think such a thing should therefore be included.

For example: my dad for instance would need to be able to do basic administrative tasks on the system, though i would never thrust him a root account. A separate account (as you said) that does has full root access, would just make many people log in to that one, just as some security-update-mail commands them. Like you said, SElinux could also be a possible solution, but i believe it isn't really well supported by ubuntu. SElinux installed ' out of the box' with an easy ('average Joe' proof) user interface would be nice.

Yes, i know linux is based upon freedom, and i think everybody should have the ability to become a full root. Only not out of the box, not if users who don't really understand the risks are to use it. I even think that if you don't want such security measurements, if you think 'that would never happen to me' (thats also the way i think xD), ubuntu may in the future not be the linux distribution for you. If you feel ready to go oldskool linux, start using debian or slackware.

It's better to prevent than to heal. (especially when it comes down to personal data)

NESFeak

---

### Post by El Viejo Lobo on 2007-05-09
> **eldragon said:**
> ok. ive been wondering lately, why we dont need an av, other than spreading mail to windows users...

is it really because linux is more secure? or really because the linux userbase isnt big enough for virus/troyan/spam bot writes to care about?

can anyone explain in words everyone can understand, why we dont really need an antivirus? or if we need one, why and which is the better alternative?

You better browse a bit on Google/Yahoo, you can find the answers in the web.
[http://www.desktoplinux.com/articles/AT3307459975.html](http://www.desktoplinux.com/articles/AT3307459975.html)

---

### Post by eldragon on 2007-05-09
> **NESFreak said:**
> As ubuntu becomes more widespread, more people will start using it. This will (if everything goes the way we want it to) in the end include many users who cannot judge for themselves, what program to and what program not to give root access. If one of those people would start using linux right now, they could easily find themselves destroying important system dependencies and stuff. (Or let a virus do it for them, if there would be any in the future) If ubuntu becomes linux for the masses i think such a thing should therefore be included.

For example: my dad for instance would need to be able to do basic administrative tasks on the system, though i would never thrust him a root account. A separate account (as you said) that does has full root access, would just make many people log in to that one, just as some security-update-mail commands them. Like you said, SElinux could also be a possible solution, but i believe it isn't really well supported by ubuntu. SElinux installed ' out of the box' with an easy ('average Joe' proof) user interface would be nice.

Yes, i know linux is based upon freedom, and i think everybody should have the ability to become a full root. Only not out of the box, not if users who don't really understand the risks are to use it. I even think that if you don't want such security measurements, if you think 'that would never happen to me' (thats also the way i think xD), ubuntu may in the future not be the linux distribution for you. If you feel ready to go oldskool linux, start using debian or slackware.

It's better to prevent than to heal. (especially when it comes down to personal data)

NESFeak


i dont agree with the 'everyone should have a root account', that account is for administrative tasks only, only the more computer-literate member of the family should have one, and if there isnt any, then pay for off the house support with ssh access to the box through the internet, which should be in charge of applying updates, and fixing problems. 

my experience here at home: everyone used a windows box, to check mail, surf the web, and doing the ocasional word typing. i had to format that computer EVERY month. i got tired, and slammed xubuntu there. that was about 6 monthes ago. since then , i only log in once or twice a month to apply updates. im even confident enough to share my music collection there :)

i wont deny it: everyone complained......for a week.......or two......
now they are happy with it, it just works.....and its not a mac ;) and it works faster too

---

### Post by NESFreak on 2007-05-09
> **eldragon said:**
> i dont agree with the 'everyone should have a root account',
I meant every computer owner should be free to have a root account. It's his PC. Although not every computer owner needs to have full root access by default. If he's computer-literated enough to know what a root account is, then he'd probably also know / find out what to do in order to get it.

---

### Post by euler_fan on 2007-05-09
> **El Viejo Lobo said:**
> You better browse a bit on Google/Yahoo, you can find the answers in the web.
[http://www.desktoplinux.com/articles/AT3307459975.html](http://www.desktoplinux.com/articles/AT3307459975.html)

Thanks for posting that.

---

### Post by rai4shu2 on 2007-05-10
Here's an interesting security issue I've been thinking about:

Third-party repos/CDs: As far as I know, package managers do not verify the authenticity of packages beyond simply verifying the GPG key of the source itself and then verifying the hash of the package. This does not certify that the package itself is without malware. There is no repository of verified hashes that package managers can rely on, so they assume that if the user trusts the source, then the source must be trustworthy.

It's therefore highly desirable for the sake of security to reduce reliance on third-party repos and expand as much as possible the number of official maintainers. This is something that Debian and Ubuntu have been doing since the beginning.

---

### Post by Jonne on 2007-05-10
> **El Viejo Lobo said:**
> You better browse a bit on Google/Yahoo, you can find the answers in the web.
[http://www.desktoplinux.com/articles/AT3307459975.html](http://www.desktoplinux.com/articles/AT3307459975.html)
Ah yes,
ask someone who *sells* antivirus software for Linux if you need antivirus. Good idea. How about asking F-Secure if I really need an antivirus on my cellphone? I'm sure they'll be completely honest with their answer...
</sarcasm>

The truth is, if you know what you're doing (hw firewall, patched box, a brain) you don't need antivirus software. The antivirus software vendors have been able to spread FUD to make people think you absolutely *need* antivirus software, but it's not true. The whole concept of it is flawed to begin with (trying to remove a program *after* it got on your system, Scanning for signatures that might match innocent apps, ...).

---

### Post by rai4shu2 on 2007-05-10
If you work in an open environment with lots of users (like a school, for example), you will encounter a need for AV software simply because a lot of untrusted storage media will likely find its way in there.

---

### Post by BuffaloX on 2007-05-10
Linux IS the virus, and it's spreading. :)

---

### Post by JessicaW on 2007-05-10
Can anybody tell me a Good Antivirus which take low Space in memory

---

### Post by eldragon on 2007-05-10
> **Jonne said:**
> Ah yes,
ask someone who *sells* antivirus software for Linux if you need antivirus. Good idea. How about asking F-Secure if I really need an antivirus on my cellphone? I'm sure they'll be completely honest with their answer...
</sarcasm> 

that was exactly my thought after reading the article...not knowing who the interviewed was, i figured he belonged to an AV company...

---

### Post by az on 2007-05-10
> **rai4shu2 said:**
> Here's an interesting security issue I've been thinking about:

Third-party repos/CDs: As far as I know, package managers do not verify the authenticity of packages beyond simply verifying the GPG key of the source itself and then verifying the hash of the package. This does not certify that the package itself is without malware. There is no repository of verified hashes that package managers can rely on, so they assume that if the user trusts the source, then the source must be trustworthy.


Package signatures only provide one thing:  a signature assures you that the package is indeed by the person whom you think it's from.  It's an authentification of the package signer.  It is not an assurance of quality, nor a stamp of approval.  The GPG signature is not meant to tell the user that a particular package is okay, it only means that it is from a particular person.

> **rai4shu2 said:**
> If you work in an open environment with lots of users (like a school, for example), you will encounter a need for AV software simply because a lot of untrusted storage media will likely find its way in there.

So what?  Tell me exactly how this puts my Ubuntu OS at risk?

---

### Post by rai4shu2 on 2007-05-10
In a computer lab, for example, it's not uncommon for students to smuggle in warez on USB sticks or SD cards. It's not inconceivable that said warez contain malware.

---

### Post by CSMatt on 2007-05-13
I tried ClamWin with Winpooch for real-time scanning and it actually made my system run even slower than it did when it was running Symantec Corporate Edition.  I inevidably had to switch back to Symantec because it took so long to boot Windows ("boot" meaning "from startup to idle", i.e. the hard drive LED stops lighting up).

Oh crud.  I just realized how old this thread was.  Apparently I was loading the cache when I kept restoring my browsing session.  Sorry.

---

### Post by eldragon on 2007-06-02
yes, well, although computer labs trend to have lots of untrusted software being run.....its well known that a user with no administrative priviledges cant damage the whole system....so a simple deletion of the infected user should fix your malware problem. instead of hoaxing the whole system like what would happen with a windows xp install. or maybe im way off. and even without admin priviledges, a user can write the boot partition installing a rootkit that would hoax the whole system. any light in this subject please?

of cousre booting from a livecd is out of the question, of course you can always damage a system with a livecd ;)

---

### Post by DalekClock on 2007-06-02
> **forrestcupp said:**
> This is one of the only things they did right in Vista.  They made each part of the OS it's own compartment that can't be violated by other compartments.  Where before, someone could write a virus that used the print driver to exploit the whole system, now that virus will be contained in the printer compartment.  So a virus can only mess up the compartment that it originates in.

True but not true. I know the Windows user base. They're generally the same, and will get so annoyed by the security features that they disable them, quite easily through the Control Panel, opening their computer to a wide range of attacks.

The Linux user base, however, are generally a lot more tame and security-concious. And any Windows user who switches to Linux will probably not understand how to disable these security features.

---

### Post by the_darkside_986 on 2007-06-02
One problem with Windows NT is that some developers, for no good reason at all, decide to design their software to be only run as Admin.  I can even name two problematic software that do this: Grand Theft Auto: San Andreas and the stupid e-mail client written by Earthlink. Both of those, when installed on Windows XP, only allow themselves to be run by root. And since they are both closed-source, the security holes could be a serious problem--at least with the e-mail client. GTA:SA isn't really an online game so it might be less of a problem.

Fortunately, I replaced my Windows installation with Ubuntu and FreeBSD so I don't have to worry about that mess.

---

