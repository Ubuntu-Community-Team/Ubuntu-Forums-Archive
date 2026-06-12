---
title: "Build my kids an Ubuntu laptop"
date: 2010-09-11
forum: The Cafe
---

### Post by jrowland on 2010-09-11
The wife and I have settled on the kids' Christmas presents this year - they're each going to get a netbook.  We have 4 teenagers who are all tired of sharing the single, hand-me-down laptop that used to be mine; and we're tired of all the bickering over who's turn it is, how much time the others hogged, etc.  The wife wants to spend a few extra hundred bucks and get some Win7 licenses for these things... I'm all for loading Ubuntu.  She demands that there be parental controls, and she's happy with the Win7 parental controls on the current laptop.  Parental controls, in this case, mostly just refers to restricting their access to the internet based on times, not necessarily content filtering.  So, to save myself some money, here's what I'm trying to figure out....

I'd like to be able to configure each system to allow the kids to be able to install software, run system updates, etc,. while at the same using something like timekpr (maybe?) to restrict their internet usage.  This "internet restriction" needs to be something like: allow 2 hours per day total usage on weekdays between 5pm and 9pm, and 3 hours per day on weekends between noon and midnight.  They can chose when to use their allotted time, but they can't get online before school, and they must be off by 9pm on school nights.  At the same time, they should be able to use their computers whenever they want for local music, movies, games, whatever - just not the internet.

My current thought process is something along the lines of this:  install the OS with the account "Parents", which will have the administrative control of the whole shebang.  Create a user account (KidsName) which has access to the internet, but this account will be restricted by the timekpr program.  Create a 3rd account (KidsName-Offline) that doesn't have internet access, but has access to all of their programs, games, music, etc.

This seems kinda clunky.  So... my question to the masses is: is there a better way to do what I want?  It needs to be easy enough so that my non-computer savy wife can maintain order while I'm not home (I travel a lot), which is why she wants Windows 7.  It needs to be "secure" enough so that the kids can't get around the restrictions, but still be able to install software/updates.

I appreciate any advice and thoughts on the matter.
Jimmy

---

### Post by HermanAB on 2010-09-11
The new HP/Compaq minis come with Win7 Home edition.  Works OK out of the box.  Just make a copy of the HD for easy maintenance.  I got one for my Mother in Law.

---

### Post by GregBrannon on 2010-09-11
Mr. Obvious checking in:

Buy at least one of the new netbooks NOW and have the setup all figured out early, tested, confident that it does as you want.  Let the wife play with it, configure it, fix it, etc., so that she won't be faced with marriage-stressing challenges while you're away.  You can spend some time trying to circumvent the restrictions to determine if there are vulnerabilities that need shoring up.

---

### Post by miggols99 on 2010-09-11
For me timekpr works perfectly. It does everything you want but I experienced a few problems with it not starting up sometimes...

---

### Post by ronnielsen1 on 2010-09-11
Hide the live cd's too. If they figure that out, they can bypass everything

---

### Post by rocknrollmouse on 2010-09-11
I use edubuntu for my kids (I loved the latest version so much I installed it on one of my machines too!)

setting up kids as users and parents as admins is also a very good idea.

also look at freeDNS for another family friendly internet control (simple and effective, if your ISP allows you to set your router to an independent DNS server).

also (if your router supports it) putting your allowed internet access times on the router will remove a level of complexity form the allowed/unallowed users you describe (using your method syncing files and environments (eg dictionary for homework assignments) can become complex, both to setup and to administrator.)

---

### Post by matthewbpt on 2010-09-11
An easy way to restrict internet access if your router is capable of it is set up MAC based access control for internet from there, which should be applicable on whatever OS they are running, so it would even work using a live cd. (MAC spoofing can bypass this quite easily ... how tech savy are your kids?)

---

### Post by ssam on 2010-09-11
give them locked down windows. at some point they will figure out how to boot an ubuntu live cd to get unrestricted access. they will consider themselves clever and rebellious, learn to value the freedom of open source, and end up at talented linux programmers.

or if you really need to stop them, then implement the control on the router.

or have a search for linux based parental control.

---

### Post by jrowland on 2010-09-11
Thanks for the replies so far.  I guess that I also should have specified... I'm a fairly new Ubuntu user, so... I could also use some tips on *how* I might make it work.  For example: can I give them "enough" administrative access to install software, but not so much that they can override the parents account stuff? All I need is a "rebelious teenager" learning to use [FONT=Courier New][COLOR=Navy]passwd -l parents[/COLOR].[/FONT]

> **ssam said:**
> give them locked down windows. at some point they will figure out how to boot an ubuntu live cd to get unrestricted access. I'm not sure how locked-down windows will stop a live cd?  No matter the OS, standard procedure will be to disable all boot devices in the BIOS (except the hdd) and password the BIOS.  >  they will consider themselves clever and rebellious, learn to value the freedom of open source, and end up at talented linux programmers. Ahhh, yes... I would be proud.  If they can get around it all, more power to 'em.

> **ronnielsen1 said:**
> Hide the live cd's too. If they figure that out, they can bypass everything Yes, actual parenting will also need to be involved.  That, plus a passworded BIOS. ;)

> **HermanAB said:**
> The new HP/Compaq minis come with Win7 Home  edition.  Works OK out of the box.  Just make a copy of the HD for easy  maintenance.  I got one for my Mother in Law.Ooops, I failed to mention that I've already purchased all 4.  We had one hell of a coupon at the local electronics store during their promotional "scratch and save" event - we scratched off a 50% off everything coupon. Christmas shopping is done, btw! :p
 
 > **GregBrannon said:**
> Mr. Obvious checking in:
  Buy at least one of the new netbooks NOW and have the setup all figured  out early, tested, confident that it does as you want.  Let the wife  play with it, configure it, fix it, etc., so that she won't be faced  with marriage-stressing challenges while you're away.  You can spend  some time trying to circumvent the restrictions to determine if there  are vulnerabilities that need shoring up. That's what I'm doing now.  Been searching around for "ubuntu parental controls" for a week, and I'm ready to install and test.

---

### Post by Someone uk on 2010-09-11
don't forget to set a bios password, with ubuntu if your kids got the live cd they would pretty much have root access

---

### Post by Old_Grey_Wolf on 2010-09-11
> **rocknrollmouse said:**
> ...also (if your router supports it) putting your allowed internet access times on the router will remove a level of complexity form the allowed/unallowed users you describe (using your method syncing files and environments (eg dictionary for homework assignments) can become complex, both to setup and to administrator.)

That is what I was thinking. Attached is a screenshot from my router.

---

### Post by mamamia88 on 2010-09-11
I don't know why someone hasn't mentioned this yet but why don't you just be clear about how they use their computers and the consequences for using them when not using them the way you intended?

---

### Post by gzarkadas on 2010-09-12
First of all, giving your kids the ability to install software (that is allowing sudo) is equal to allowing them to bypass all security measures, since you are giving them root privileges. So don't do it. Let you and your wife to install software, so that you can check whether it is appropriate; this is also a great opportunity for discussion/education (when an inappropriate program request appears ;)).

To restrict time usage you can use the _pam_time_ module (it must be included by default, type in a terminal `man pam_time' to see if it is). You will have to:

[LIST]
[*]Uncomment a relevant line from file _/etc/pam.d/login_ (and from _/etc/pam.d/su_ if you want to time restrict su usage also).
[*]Create the file _/etc/secutiry/time.conf_ and edit it to supply the desired time restrictions. See [this article]("http://articles.techrepublic.com.com/5100-10878_11-1055269.html") for startup info and also the man page of _pam_time_.
[/LIST]
I haven't used the module yet (but I will, now that have found it) so I do not now if it supports restrictions to groups in addition to users. 

[LIST]
[*]If it _does_, restricting Internet can be done as follows: make your kids members of a group (say kidinternet) and restrict this group only.
[*]If it does _not_ then you will need to put a line for each Internet service and add your kids' accounts to these.
[/LIST]
The same of course applies for all other restrictions (login, other services, etc.).

Another useful module is _pam_limits_. It enforces resource limits without regard to time of day but it may be useful in this respect: There is a _cpu_ setting that limits the maximum cpu time of a user or group. It can be used to forcibly end a user's/group's processes after a specified period. You could use it to allow a kid to login between say 18:00-22:00 any time he/she wants, but have only two hours usage within this time frame.

To restrict limit usage with the _pam_limits_ module (it must be included by default, type in a terminal `man pam_limits' to see if it is) you will have to - because I do not remember if it is activated by default :-k, it has been a year since I tweaked it:

[LIST]
[*]Uncomment any relevant line(s) from file in _/etc/pam.d_. Use this code inside a terminal to check:
[/LIST]
```

cd /etc/pam.d
grep -Hn 'pam_limits' *

```[INDENT]and them open the relevant files with an editor and maybe modify them (it is as easy as to delete a single # to activate an option or change a `optional' setting to `required'. See the man page for details and also the link supplied below.
[/INDENT]
[LIST]
[*]Create the file _/etc/secutiry/limits.conf_ and edit it to supply the desired limit restrictions.
[/LIST]
 Be sure to **test everything**; login with your kid accounts and see if restrictions are actually enforced. 

It is better to do all the setup in one machine and then clone your entire hard disk to the others; it will save a lot of time and since all are same it will be extremely easy to do so. Just:


[LIST]
[*]Remove the hdd of the other computer and attach it to your configured laptop.
[*]Boot the laptop with a liveCD, so that both hdds are **unmounted**.
[*]Find with Gparted what device is your source and target hdds. Write them down. Make sure that you written them correctly; double check. You must specify the entire hdd (such as /dev/sdb) and not a partition (i.e. **not** /dev/sdb1).
[*]Then, when you are completely sure, execute this command in a terminal:
[/LIST]
```

sudo dd if=<source-device> of=<target-device>

```

[LIST]
[*]Put the hdd back in the target laptop and boot it.
[/LIST]

[B] Related links:
[/B][http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_limits.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_limits.html)
[http://susefaq.sourceforge.net/howto/pam.html](http://susefaq.sourceforge.net/howto/pam.html)

Also bear in mind that restricting the time spent on the Internet does not solve the problem of _what_ your kids will do on the Internet during the allocated time. For this really there is no better "weapon" than educating them. There are so many threats, most of them on the semantic rather than the technical level,  that only proper education can help to not become a problem in the future. I will just briefly list below some `hints' on basic things that need to be discussed:

[LIST]
[*]People do often lie to appear better than they are, aiming to gain various advantages or to just plainly decieve you and steal, kidnap, abuse or whatever else do to you or someone else you know (family, friends, colleagues).
[/LIST]

[LIST]
[*]There is a lot of scam in the Internet, simply because it allows the scamers to perfom their operations massively and from remote locations. Don't trust anything that you cannot verify; if it looks too good, it is certainly a lie; leave immediately if something looks suspicious; don't react to offences / threats / desperate calls to go somewhere and help / etc., but instead seek immediate parent advice.
[/LIST]

[LIST]
[*]Do not install software from untrusted parties, nor forward emails from people you don't know, nor type commands you do not understand, nor copy and paste scripts which you did not first read and comprehend, nor change configuration settings without first consulting the man pages and googling to find relevant documentation to find what are the implications.
[/LIST]

[LIST]
[*]Do not be deceived by the amount of scam in the Internet and the fact that nobody is in front of you when you use your computer; you are ***not*** anonymous. Your IP identifies you in the entire world, without any doubt (because you ISP logs your access and keeps the logs for a long time). If you do something silly, you ***will*** face the consequences.
[/LIST]

[LIST]
[*]Do not give sensitive information to others (credit card numbers, financial data, identity data, logs of personal activities, intended actions, leave out schedules, even thoughts and feelings about personal/family life events) without first thinking about the consequences - someone may be probing you or intends to proxy your input to others; stop the conversation if someone asks such things or -even worse- insists; seek immediate parent advice.
[/LIST]

[LIST]
[*]Do not publish the above sensitive information to public sites; _this is a *serious* thing_; they will be stored there and cached in search engines for an indefinitely long time (may be longer than you'll last) and will be accessible by anyone in the world; there are companies that scan those data to make profiles of people - because many other companies want the profiles to decide whether they will hire them, promote them, or fire them (to mention just this). Be very cautious with what you publish.
[/LIST]
You can, if you still don't feel safe enough after doing this, to setup a proxy like squid and enforce all http to go through it, so that you can review the logs and see what sites your kids visit and how often. This [article]("http://blog.bodhizazen.net/linux/how-to-transparent-proxy/") may be of help, as well as this one for [web content filtering]("http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/"). 

This does not solve the issue with other protocols such as ftp or irc or peer-to-peer file sharing; you can limit them though (and log them) with [ufw]("https://help.ubuntu.com/community/UFW") or iptables. The later is a catch-all solution but requires setup and will result in a large amount of logs; without proper tools it will be simply hard to get anything useful from it.  The [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") sticky has a lot of information for configuring your firewall (and your system in general). For peer-to-peer filesharing either disable it or use [MoBlock]("https://help.ubuntu.com/community/MoBlock"). In any case discuss with your kids the legal implications and the threats that your entire family may face from using it.

---

### Post by Windows Nerd on 2010-09-12
Remember, though, even setting a BIOS password can be bypassed. And disable booting into a recover shell or single-user-mode.

Depends how good your kids are with computers. If they are as knowledgeable as I (I'm a teenager), physical access is Root access.

---

### Post by v1ad on 2010-09-12
yes they could get past the bios password by removing the battery for 10 seconds.

another thing. make sure they never see this thread :D

---

### Post by Legendary_Bibo on 2010-09-12
Jeezus, most of these posters seem to think your kids can hack into the CIA or something. Although when push comes to shove kids will find a way to bypass your parental controls so you might need to have all this set up. Well you have netbooks, so using a Live CD is out of the question, so they'll have to make live USBs which isn't as easy. I'm sure some basic parental controls and edubuntu should be good enough.

---

### Post by Windows Nerd on 2010-09-12
> **Legendary_Bibo said:**
> Jeezus, most of these posters seem to think your kids can hack into the CIA or something. Although when push comes to shove kids will find a way to bypass your parental controls so you might need to have all this set up. Well you have netbooks, so using a Live CD is out of the question, so they'll have to make live USBs which isn't as easy. I'm sure some basic parental controls and edubuntu should be good enough.
I cannot hack into the CIA, but if I have physical access to your computer, I would most likely be able to read and write to all of your files on that harddrive.

Even if people claim "I have a VERY strong password, lock my BIOS, and have a physical lock on the computer side panel"

    Most computer locks are puny little things that my 5-year old cousin could break with pliers. Any bigger locks can be broken with pliers/a bolt-cutter. Locks big enough not to be broken this way often do not work on the computer.

1) Break lock
2) Open side panel
3) Take out CMOS battery/reset CMOS jumper
4) Boot LiveCD
5) Access files as root.

Did that take much technical knowledge?

---

### Post by v1ad on 2010-09-12
encrypt the drive :]

---

### Post by renkinjutsu on 2010-09-12
for restricting internet based on time, here's a nice guide using IPtables

[http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html]("http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html")

---

### Post by TriBlox6432 on 2010-09-12
Or you could just, y'know do it the old fashion way and tell them to get off the computer.  ):P

---

### Post by gzarkadas on 2010-09-12
> **Windows Nerd said:**
> ...
1) Break lock
2) Open side panel
3) Take out CMOS battery/reset CMOS jumper
4) Boot LiveCD
5) Access files as root
...

Even simpler / no need to break anything: 
1.Remove the hdd panel with a screwdriver
2.Take out the hdd
3.Mount the hdd to another machine as second drive
4.Do whatever

As I said, the most important is proper education. 
Then a clear and fair set of rules. 
Then the technical measures, to aid understanding when the rules are about to be broken and also to reduce the need for daily enforcement.

---

### Post by qwerty2009 on 2010-09-12
or....

you could just install gnome-nanny from the software center. 

software center blurb:
> **An easy way to control what your kids are doing in the computer. You can limit how much time a day each one of them is browsing the web, chatting or doing email. You can decide at which times of the day the can do this things as well. Nanny filters what web pages are seen by each user, so you can block all undesirable webs and have your kids enjoy the internet with ease of mind, no more worries!**

this would require restricting there access to sudo so they cannot change the settings, or hiding the menu entry and hope they dont find it

---

### Post by Windows Nerd on 2010-09-12
> **v1ad said:**
> encrypt the drive :]

That's the only defense. Against most all people. (surely there must be some genius cracker who does know how.)

But still, nothing is stopping me from reinstalling a distro on the hard drive, with your own options.

---

### Post by Legendary_Bibo on 2010-09-12
> **gzarkadas said:**
> Even simpler / no need to break anything: 
1.Remove the hdd panel with a screwdriver
2.Take out the hdd
3.Mount the hdd to another machine as second drive
4.Do whatever

As I said, the most important is proper education. 
Then a clear and fair set of rules. 
Then the technical measures, to aid understanding when the rules are about to be broken and also to reduce the need for daily enforcement.

Uhhh...most kids don't know how to do this, and they won't open up the computer at all out of fear of breaking it. Of all the people in the world to be paranoid of, your children are not one of them.

---

### Post by drawkcab on 2010-09-12
how would gnome nanny prevent the kids from using web-based proxy servers?

---

### Post by barbedsaber on 2010-09-12
> **TriBlox6432 said:**
> Or you could just, y'know do it the old fashion way and tell them to get off the computer.  ):P

so simple, so elegent

---

