---
title: "Hacking attempts?"
date: 2008-01-15
forum: The Cafe
---

### Post by Mazza558 on 2008-01-15
My sister's running Windows XP (SP2) on her laptop, and 2 days ago, her Myspace account was hacked into and spam bulletins/posts that she didn't send were posted. She changed her password and made sure where her password was the same that it was changed there too, expect on some (unimportant) sites.

Today she went out and came home to find that while she'd been away, even though her PC was off, someone had been listening to music using her last.fm account details. It was (and still is) logging songs that she hasn't listened to, doesn't have on her computer and has never even heard of! She immediately changed her password on this, but the songs were still being logged despite needing to change the password on the last.fm website and the downloaded program. What I did was have a look at the packets being sent from her laptop, and it seems that something is sending packets out occasionally every few minutes. I'd assume these were just part of XP, but it could be anything.

Furthermore, I had a look at the router logs (Netgear), and there seemed to have been several DoS/Port Scan attacks on the router, all in the space of 3 minutes yesterday night. Odd, eh? :(

P.S: There's no point suggesting switching to Ubuntu as she's much prefer to stay on Windows unless she absolutely has to switch (e.g virus trashing her PC).

---

### Post by Mad_Dawg on 2008-01-15
Sounds like someone is using her laptop as a 'zombie' or has installed a keylogger.  If so, back everthing up, wipe the drive, and re-install an OS.

---

### Post by bufsabre666 on 2008-01-15
2:1 key logger
4:1 she posted a pasword some where
10:1 her password was qwerty

any one ganna play? come on one'll get you ten

---

### Post by Vadi on 2008-01-15
This isn't good enough of a reason to switch?

Well, if no, tell her to go out and buy firewalls, reinstall Windows, and so on...

---

### Post by Mazza558 on 2008-01-15
I'd just like to add thast she can't reinstall Windows as it's an OEM install.

---

### Post by ~LoKe on 2008-01-15
No format, no promises.  If she has a restore point, roll back to it (though it could be infected).  There's really no viable solution but to reformat and reinstall, to be sure it's clean.  Since she can't....well....she's screwed.

---

### Post by bufsabre666 on 2008-01-15
you can reinstall a oem, just put in a windows disc and install a hacked key and when it asks you to activate just put in her legit code and then call and get the activation number from windows

or install ubuntu and tell her to tough it out ((recommended))

---

### Post by p_quarles on 2008-01-15
> **Mazza558 said:**
> I'd just like to add thast she can't reinstall Windows as it's an OEM install.
An OEM installation should include either an installation disk or a recovery partition on the HDD. Are you sure that you don't have some way to reinstall?

---

### Post by lespaul_rentals on 2008-01-15
> **bufsabre666 said:**
> 2:1 key logger
4:1 she posted a pasword some where
10:1 her password was qwerty

any one ganna play? come on one'll get you ten

A keylogger wouldn't explain the packets he discovered when sniffing the network traffic, and it wouldn't explain the records in the logs.  I suspect a backdoor Trojan.  They're everywhere these days.  Here's what I would recommend:

Disconnect the Internet cable immediately.  The attacker will lose control of your computer if you do so.  Go into msconfig (Start, Run, msconfig) and go to the Startup tab.  Disable everything that looks suspicious.  If you find a suspicious filename that you know does not belong, do a file search (Windows key+F) for the name of the file(s) and delete them upon discovery.  Go into the Registry (Start, Run, regedit) and please browse to the following key:

HKEY_LOCAL_MACHINE/Software/Microsoft/Windows/CurrentVersion/Run

Do the same as you did in msconfig.  Delete all values that look suspicious, and search for any you haven't already deleted.

Restart your computer and back up all data.  Only plug the network cable back in if you have to.  I recommend using [Darik's Boot and Nuke](http://dban.sourceforge.net) to do a complete reformat, then reinstall Windows. Tell your sister to be smarter about what she opens.  I also have this feeling that she uses p2p software, which she is obviously not computer-smart enough to use.

---

### Post by ~LoKe on 2008-01-15
> **p_quarles said:**
> An OEM installation should include either an installation disk or a recovery partition on the HDD. Are you sure that you don't have some way to reinstall?

I think they stopped sending out the re-installation CD's ages ago.

---

### Post by rustybronco on 2008-01-15
> **Mazza558 said:**
> I'd just like to add thast she can't reinstall Windows as it's an OEM install.and there's no back up image on her laptop from the oem to reinstall?

---

### Post by p_quarles on 2008-01-15
About four years ago or so. But then they began shipping the recovery partitions, and many of those give you the option of creating a set of recovery CDs. 

I believe that OEM's are required to provide some sort of recovery medium.

---

### Post by Mazza558 on 2008-01-15
> Tell your sister to be smarter about what she opens. I also have this feeling that she uses p2p software, which she is obviously not computer-smart enough to use.

She's actually very competent with computers, though she does use p2p (not the popular ones, Soulseek). I guess it's harsh to assume she knows nothing about PCs, because she does (just Windows).

Oh, and the laptop is second hand, so has no recovery partition.

I'd like to add that Last.fm still shows her listening to music **even** when she's not connected and **even** when she's logged out of the service. Last.fm bug?

---

### Post by p_quarles on 2008-01-15
> **Mazza558 said:**
> She's actually very competent with computers, though she does use p2p (not the popular ones, Soulseek). I guess it's harsh to assume she knows nothing about PCs, because she does (just Windows).

Oh, and the laptop is second hand, so has no recovery partition.

I'd like to add that Last.fm still shows her listening to music **even** when she's not connected and **even** when she's logged out of the service. Last.fm bug?
She really needs to reinstall the system at this point. There's enough evidence to suggest that the PC was infected by something nasty, and nothing apart from wiping the drive is going to ensure that it's gone. There's no other good advice to be given.

I've heard there are good deals on second-hand copies of XP at E-bay.

---

### Post by FuturePilot on 2008-01-15
> **p_quarles said:**
> About four years ago or so. But then they began shipping the recovery partitions, and many of those give you the option of creating a set of recovery CDs. 

I believe that OEM's are required to provide some sort of recovery medium.
Yes, I know HP puts a recovery partition on their computers but they also include a tool to make recovery CDs or DVDs.

> **Mazza558 said:**
> 

I'd like to add that Last.fm still shows her listening to music **even** when she's not connected and **even** when she's logged out of the service. Last.fm bug?

If someone has the password to that account *they* might be logged in.

---

### Post by jrusso2 on 2008-01-15
Not only does she need to reinstall she needs to change the passwords on every website she uses.

Then she should stay off myspace.

Besides keeping your windows operating system up to date its very important to keep all your software up to date.

Many things such as flash, java, quicktime have had many exploits some of which were in use on myspace.

A good program to use to keep everything up to date is the secunia software inspector.

[https://psi.secunia.com/](https://psi.secunia.com/)

---

### Post by Mazza558 on 2008-01-15
> **FuturePilot said:**
> Yes, I know HP puts a recovery partition on their computers but they also include a tool to make recovery CDs or DVDs.



If someone has the password to that account *they* might be logged in.

She's just changed the password again on the internet account using her PC. We'll have to see what happens now - when they next log out, they should be locked out for good. I'd also like to add that she uses the downloadable Last.fm client as well (which is required for things like WMP and iTunes).

---

### Post by John.Michael.Kane on 2008-01-15
> **Mazza558 said:**
> She's just changed the password again on the internet account using her PC. We'll have to see what happens now - when they next log out, they should be locked out for good. I'd also like to add that she uses the downloadable Last.fm client as well (which is required for things like WMP and iTunes).

Why is she changing passwords to accounts using a machine that is obviously infected with something?

The machine needs to be taken off line, and fixed.

Also any password changes done from a clean machine eg: have her change her codes from your machine.

---

### Post by Mazza558 on 2008-01-15
My sister's been looking around on the Last.fm forums and she found that tracks can be scrobbled onto the wrong account if there's a lot of "user switching" on Windows. She only uses one user. :?

Oh, and she only changed passwords again to test whether the "other" user would be able to get in (thus confirming that she has a trojan/keylogger). Also, when she changed the password the first time on Last.fm, the other user still remianed logged in.

---

### Post by p_quarles on 2008-01-15
> **Mazza558 said:**
> My sister's been looking around on the Last.fm forums and she found that tracks can be scrobbled onto the wrong account if there's a lot of "user switching" on Windows. She only uses one user. :?

Oh, and she only changed passwords again to test whether the "other" user would be able to get in (thus confirming that she has a trojan/keylogger).
I see that you've decided to not take seriously the idea that the evidence here points to a keylogger.

---

### Post by Chipter on 2008-01-15
> **lespaul_rentals said:**
> Go into the Registry (Start, Run, regedit) and please browse to the following key:

HKEY_LOCAL_MACHINE/Software/Microsoft/Windows/CurrentVersion/Run

Do the same as you did in msconfig.  Delete all values that look suspicious, and search for any you haven't already deleted.


I wouldn't recommend editing the registry unless you know FOR FACT what shouldn't be there.
You can do a lot of damage in there and seriously screw up your Windows Partition.
One small error in the registry and its' FUBAR.


Reformat the sucker and reinstall Windows, or switch to Ubuntu.
Even if it's OEM, they should have given you an install CD. If not, call up whoever you got the PC from and tell them you need a CD.

If that doesn't work, let her know her remaining options:
1) Go out and purchase WinXP ($$$)
2) Download Ubuntu (Free)

---

### Post by Mazza558 on 2008-01-15
> **p_quarles said:**
> I see that you've decided to not take seriously the idea that the evidence here points to a keylogger.

How would she go about identifying and removing a keylogger? (short of reinstalling/formatting).

---

### Post by bufsabre666 on 2008-01-15
heres what id do, open up a live cd of ubuntu, get the linux version of avast anti virus, make sure its upto date, then do a full hard drive scan

virus scans go way faster through linux and they only look for windows viruses anyways

---

### Post by Mazza558 on 2008-01-15
Looks like it's a known bug:

[http://www.last.fm/forum/34905/_/368886/1#f5597492]("http://www.last.fm/forum/34905/_/368886/1#f5597492")

> There is a bug that may cause this. And like meldoicstorm asks, is there a chance that you left a client logged in on another computer somewhere?

The hacker suggestion is slightly more knee-jerk, and probably not the case.

> It would seem that if someone did have your pass, the changing of it (even if they do have a keylogger sending them your pass) should mean there is a break in scrobbling.

I think the staff wanted to try and debug this with someone who it was currently happening with, so I guess you wait for one of em to post here (or you can try to go on the irc channel and see if anyone is around).

...and now the Myspace problem?

---

### Post by Chipter on 2008-01-15
The myspace problem was quite common.
I used to have an account there about a year ago (before Facebook took over the universe).
I can remember at least 7 of my friends whose accounts were hacked and were used as spambots.

Either Myspace needs to improve their server security, or there is some sort of phishing scam going on.

Change the password (from a safe computer) and let the administrators at Myspace.com know of the situation.
Let her know that they might close her account, and she might have to open up a new account.

---

### Post by ~LoKe on 2008-01-15
> **Chipter said:**
> Either Myspace needs to improve their server security, or there is some sort of phishing scam going on.

MySpace just sucks.  I haven't been able to log in for months (that's a good thing).  I enter my e-mail and password, click submit, then get told "You need to be logged in to do that".  :confused:

---

### Post by lespaul_rentals on 2008-01-15
> **Mazza558 said:**
> She's actually very competent with computers, though she does use p2p (not the popular ones, Soulseek). I guess it's harsh to assume she knows nothing about PCs, because she does (just Windows).

Oh, and the laptop is second hand, so has no recovery partition.

I'd like to add that Last.fm still shows her listening to music **even** when she's not connected and **even** when she's logged out of the service. Last.fm bug?

I'm not trying to call your sister a moron, I'm just saying she probably got something from there.  And what do you mean, "not the popular ones, Soulseek"?  Soulseek has a huge number of users and an equally large number of viruses and malware.

Last.fm is always messing up, so I wouldn't worry about that too much.  Just follow the steps I suggested, at least the first part.  If you don't see anything suspicious in msconfig or the Registry I wouldn't worry too much.  She probably got phished and that's why her MySpace had issues, and Last.fm could just have a bug.

---

### Post by lespaul_rentals on 2008-01-15
> **Chipter said:**
> I wouldn't recommend editing the registry unless you know FOR FACT what shouldn't be there.
You can do a lot of damage in there and seriously screw up your Windows Partition.
One small error in the registry and its' FUBAR.

I wouldn't recommend you edit your xorg.conf file.  One small error and it's FUBAR.

:roll:

When using a computer you will sometimes have to go into advanced mode.  I gave him the exact path to the values he needed to look over.

---

### Post by Tristam Green on 2008-01-15
My MySpace profile was spoofed in late August 07 when mass-spoofings were daily occurrence; quick fix with a password change from a different  machine, and sending emails out to my (3) friends telling them "hey, disregard the BS, it's not me sending it".

---

### Post by chips24 on 2008-01-15
convience her to use ubuntu   LOL

---

### Post by Lostincyberspace on 2008-01-15
install a firewall app and have the run and block everything unless it has been cleared.

---

### Post by fatality_uk on 2008-01-15
It's a keylogger/rootkit for sure 
Visit here. A great site for windows users a BOOKMARK must [sysinternals]("http://technet.microsoft.com/en-gb/sysinternals/default.aspx")

---

### Post by Ripfox on 2008-01-15
> Then she should stay off myspace.

If you have a properly updated box and the correct anti-virus software myspace is completely safe. I have a band site for a looong time and my bassist (with his windows box) has never had a single problem. "Staying off myspace" is a little extreme...just learn how to protect yourself :lolflag:

---

### Post by macogw on 2008-01-15
If you have a legitimate Windows license key on a sticker on her computer, you can just call Microsoft, read them the number, and ask them to send you reinstallation media.  I think it's like $30 or so...which is the same as what the stores and OEMs charge if you want them to give you actual disks for reinstalling (since recovery partitions don't help when the partition table corrupts or you have bad sectors).

I think if the person who got her passwords didn't turn off whatever program is scrobbling, it doesn't matter if she changes her password.  I don't think it'd automatically kick them out.  I think it authorizes when you start scrobbling, and then until that program is closed and re-opened, the Last.fm stays active.

---

### Post by macogw on 2008-01-15
> **Chipter said:**
> 
Either Myspace needs to improve their server security, or there is some sort of phishing scam going on.

There's a ton of phishing.  MySpace took to reminding people with little notices on the site to always check the URL and make sure it's myspace.com before logging in to try to get people to wise up.  They didn't.

---

### Post by bufsabre666 on 2008-01-15
or like i said and use a pirated serial and then just change it when you register it

---

### Post by DarkDancer on 2008-01-15
> MySpace just sucks. I haven't been able to log in for months (that's a good thing). I enter my e-mail and password, click submit, then get told "You need to be logged in to do that". 

Sounds like a cookie problem. Have you tried clearing them?

---

### Post by 3rdalbum on 2008-01-15
There's a kind of phishing virus on Myspace. When it takes over your account, it posts comments to all your friends' profiles giving them a link to a page which looks like the Myspace "You must be logged in to do that!" login page, but is actually hosted in China. When it gets the victim's password, it takes over their account.

It's not too difficult to imagine that they do something else with the passwords too.

I almost fell to that particular phish.

---

### Post by mikewhatever on 2008-01-15
> **Mazza558 said:**
> How would she go about identifying and removing a keylogger? (short of reinstalling/formatting).

Since your sister is on Windows, you'd get better help here [http://www.theeldergeek.com/forum/index.php?showforum=29](http://www.theeldergeek.com/forum/index.php?showforum=29)
She'll need to get registed to get help with scanning logs. The guys there used to be very good and helpful.

---

### Post by ~LoKe on 2008-01-15
> **DarkDancer said:**
> Sounds like a cookie problem. Have you tried clearing them?

That wasn't it.  Turns out I was using an incorrect password.  Very useful error message they've got there.... :confused:

---

### Post by M$LOL on 2008-01-16
Supposing she does get the problem sorted by either reinstalling Windows or clearing up the malware, what's to say that she won't get into the same mess again? Obviously she doesn't realize what she did to get infected in the first place, so the chances are that the exact same thing will just happen again.

As for wanting to keep windows, I would have thought that something like this would be a good enough reason to change...

---

### Post by Linuxratty on 2008-01-16
Once she's cleaned up that mess,she might want to get this from firefox:

[https://addons.mozilla.org/en-US/firefox/addon/3383](https://addons.mozilla.org/en-US/firefox/addon/3383)

---

### Post by Dale61 on 2008-01-17
When did this become a Windows Help forum?  Shouldn't this be in the 'Other OS Talk' forum?

I had to keep double checking the URL to make sure I was still on Ubuntu Forums!

---

### Post by Thanoulis on 2008-01-17
When you use windows, there is *always* a chance to get infected. So, if she doesn't want to be infected she must move to another OS.
If she wants to continue using windows, she'd better get used to it and live with that. ;)

---

### Post by LauraSakura on 2008-01-17
I would say the problem is probably from MySpace. I have had countless friends have their accounts/computers hacked from it, and they end up being spambots before they even know it. A lot of keyloggers and phishing scams go through there. Once you get it all sorted out and reinstall whatever you need to, make sure you have a GOOD firewall, antivirus and antispyware program.

---

### Post by lespaul_rentals on 2008-01-17
> **Thanoulis said:**
> When you use windows, there is *always* a chance to get infected. So, if she doesn't want to be infected she must move to another OS.
If she wants to continue using windows, she'd better get used to it and live with that. ;)

There's a chance of being infected on any operating system, whether it's Windows or Linux-based.  Even BSD and its variants, which are commonly esteemed as the most secure operating systems ever, are still vulnerable to tactics such as social engineering.  Social engineering is probably how your sister's computer got in trouble.  It's definitely how her MySpace got phished.

I know people who run phishing servers.  It's not that hard to do, and the best part about it is the fact that there is not patch for morons.  Not a patch that Microsoft can release, not AVG or McAfee running 24/7, **nothing** can prevent people from being stupid, other than training and education (which is unforeseeable).  Now, I will agree with you that Linux is harder to infect, but with some precautions Windows can be fairly secure as well.

---

