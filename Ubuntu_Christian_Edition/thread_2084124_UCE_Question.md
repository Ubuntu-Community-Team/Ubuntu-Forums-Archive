---
title: "UCE Question"
date: 2012-11-14
forum: Ubuntu Christian Edition
---

### Post by offgridguy on 2012-11-14
Hello;  Now have UCE installed,  First question,  how do i disable
edit or uninstall dansguardian?
    I can't even access the firefox download page.
Can't see dansguardian in Apps.?

---

### Post by offgridguy on 2012-11-14
Found dansguardian in the software center and removed it,  in doing so also lost the use
of google browser although it will still access gmail.
   It only makes sense that the two would be connected.  i wasn't expecting this though.
I really prefer firefox as my default browser, but don't even have the option of going to 
their site anymore.    Any suggestions?   I am using 12.04 for this current activity.
    I do like the appearance of UCE and would like to get it configured to my satisfaction.
Thanks for looking.

---

### Post by offgridguy on 2012-11-14
Re-installed dansguardian, have  found firefox in apps. apparently included in the software pkg.
     Anyway i am up and running again,  i am liking this better with firefox.
   I haven't found any way to access dansguardian to configure it to my preferences,  any help here would
be gratefully appreciated.

---

### Post by prism01 on 2012-11-15
LOL

Yep! If you go to the DansGuardian site and try the link on how to remove Dansguardian...

Dansguardian won't let you get to the site! lol

Anyhow, there are no "non-hidden" files to which one can easily obtain access. They are all "hidden" files.

a) You don't know me and I don't know you and since there is an overarching concern about security and either you or I could be a nefarious person ..then I'll just let it go that the files are "hidden".

b) If an admin does not mind discussing where the files are then such a person might so post in the clear.

c) Soooo if one wants to research "hidden" files in Linux then one could, indeed, find the files.

d) However, even finding the "hidden" files is not the thing of concern in removing it.  The problem is that the actual binary is not just named "dansguardian", for obvious reasons, and has another name.  Given that one is an administrator for the particular machine then one can sudo to remove it with apt. 

e) However, again, since you "reinstalled" FF then you were able to uninstall it and one can also use the same method to uninstall Dansguardian, if you can read between the lines. :)

Or...one can get into another browser and follow the info at Dansguardian,  :)   however, again, one will probably have to have administrator rights to so do.

Sorry that I can't be of more help, but again, some "nefarious person" who wants to go around parental desires might be reading this.

prism01

---

### Post by offgridguy on 2012-11-15
I appreciate your efforts to help,  this answer does not satisfy though.
    The info in the software center re; dansguardian says very clearly that  it can be modified by the user.
  Certainly it can be uninstalled, I've done it, but how to rectify the problem that creates
with the browser ? 

Update i have decided to uninstall UCE.

---

### Post by prism01 on 2012-11-16
Hi
ok, I didn't understand the question, let me think on it, but someone that knows more will probably pop in to answer the question.

prism01

---

### Post by offgridguy on 2012-11-16
Not an issue anymore, i uninstalled ubuntu CE,  I won't mark it as solved though as it
wasn't solved.

---

### Post by prism01 on 2012-11-16
Hi
I'm sorry that I was not able to resolve your situation.

I'm kinda new to UbuCE but have been around Linux for a while.

I'll fiddle with the settings and such, and if I come up with a solution, I'll post it.

Or, as I posted, somebody else will pop in.

So, come back and check when you have time! 

prism01

---

### Post by offgridguy on 2012-11-16
> **prism01 said:**
> Hi
I'm sorry that I was not able to resolve your situation.

I'm kinda new to UbuCE but have been around Linux for a while.

I'll fiddle with the settings and such, and if I come up with a solution, I'll post it.

Or, as I posted, somebody else will pop in.

So, come back and check when you have time! 

prism01

No problem; I appreciate your attempt anyway, there is never much response in this
particular forum.

---

### Post by prism01 on 2012-11-16
hi
I agree about the "responses" and that is too bad.  It is possible that people just don't feel like they will be respected and shy away.

Curious about respect....it should maybe oughta go both ways. :(

prism01

---

### Post by offgridguy on 2012-11-17
Hello again;   You could be right,   i wonder though if it's just that not many people use
ubuntu CE  ?  Kind of sad if thats the case as the Christian theme of uce is like a breath of
fresh air in the computer world, at least for me.
      I appreciate the obvious effort the developers went to, to make it happen,  i will give it another try when i can spend some more time on it.
   I am not an advanced user, only 4 1/2 months with linux, so i ask a lot of questions in these forums trying to learn it well enough to have it become a useful working tool for me.   Thanks for the interest,  if you find out any thing more on the web filter i do check
in here regularly, please let me know.

---

### Post by offgridguy on 2012-11-20
An update here, I have reinstalled 12.04 CE after  12.04 crashed, thought i would give it
another try.
  I have found that the dansguardian web filter runs from the terminal.  So i have been
looking at that, i haven't seen any way to edit the settings yet though, any ideas?
    Ubuntu 12.04 CE does run slower than 12.04, likely in part to the web filter.

---

### Post by stlsaint on 2012-12-12
Hello. Sorry for my absence. New addition to family. New home. New job. New state. But I am getting back backinto backintothe swing of things. To address your issue. dg is controlled via conference files. We are building a frontend for it which will be included in our next release. Also dg is configured strongly out the box and yes is tied directly into the internet handling via proxy. So yes removing DC without first turning off firewall will cause problem which is what you felt with.the goal is to not make it a overly simple task for our tech savvy kids these days. Again sorry for the issue and better documentation is coming to to aid.

---

### Post by offgridguy on 2012-12-13
stlsaint; Thank you for the reply,  Any idea on the time frame of the next release?

---

### Post by Freedomeagle1967 on 2013-01-03
***Google is your Friend***
My belief any one with admin rights should be able to do anything with there systems. Linux in ***NOT*** the hidden world of Windows (tm). 
:o
With great power come great responsibly. 
:o
To remove   dansguardian
```

sudo apt-get remove dansguardian tinyproxy firehol

```

---

### Post by nixblog on 2013-01-03
Whilst I would run DG (or Squid/SquidGuard) on a server for clients, I think that running DG on an individual machine is beginning to get a bit outdated and can be an issue where a machine does not have a lot of resources to begin with. I'm more in favour of using a cloud based service like OpenDNS - very simple to use and no doubt could be configured automatically once the user signs up for an account with them.

---

### Post by offgridguy on 2013-01-03
> **Freedomeagle1967 said:**
> ***Google is your Friend***
My belief any one with admin rights should be able to do anything with there systems. Linux in ***NOT*** the hidden world of Windows (tm). 
:o
With great power come great responsibly. 
:o
To remove dansguardian
```

sudo apt-get remove dansguardian tinyproxy firehol

```
Thank you for the input. Actually removing dansguardian is easy, I have done it using the
software center, the problem is to remove it and not totally mess up the browser, I do
have instructions sent to me via private message on how to do this,  as yet I have not
made the attempt to try.
 
I totally agree with your post by the way, as admin I should be able to control my
system, not the other way around.:D

---

### Post by offgridguy on 2013-01-03
> **nixblog said:**
> Whilst I would run DG (or Squid/SquidGuard) on a server for clients, I think that running DG on an individual machine is beginning to get a bit outdated and can be an issue where a machine does not have a lot of resources to begin with. I'm more in favour of using a cloud based service like OpenDNS - very simple to use and no doubt could be configured automatically once the user signs up for an account with them.
My problem is not lack of resource on my machine rather I am very
much a beginner at using the command line, anyone with a bit of
skill in that area would probably have no problem configuring
dansgaurdian to their liking.  I am trying to learn the CLI but
it is a big learning curve for me, and thank you for the reply.:)

---

### Post by Freedomeagle1967 on 2013-01-04
> **offgridguy said:**
> Thank you for the input. Actually removing dansguardian is easy, I have done it using the
software center, the problem is to remove it and not totally mess up the browser, I do
have instructions sent to me via private message on how to do this,  as yet I have not
made the attempt to try.
 
I totally agree with your post by the way, as admin I should be able to control my
system, not the other way around.:D

I am a Gentoo User and run virtual machines for various reason ( Freedos, WinXP,Dedian). I decided to try Ubuntu Christian Edition again (it's been several years) . Anyways I ran that command and it did not damage the web browser or any other part of the system in any way shape or form. The software center most likely did not get the other two packages. ( ***note*** even if you selected complete removal)  

It would be a good idea to run this command to clean up orphan packages that might be on your system.

```
 apt-get autoremove 
```
Peace

PS. Do not be afraid of the command line, it can be imitating, however, it is the best way to admin your system. You can copy and past into your terminal.

---

### Post by offgridguy on 2013-01-04
> **Freedomeagle1967 said:**
> I am a Gentoo User and run virtual machines for various reason ( Freedos, WinXP,Dedian). I decided to try Ubuntu Christian Edition again (it's been several years) . Anyways I ran that command and it did not damage the web browser or any other part of the system in any way shape or form. The software center most likely did not get the other two packages. ( ***note*** even if you selected complete removal)  

It would be a good idea to run this command to clean up orphan packages that might be on your system.

```
 apt-get autoremove 
```

Peace
Thank you for the help. Much appreciated.

---

### Post by offgridguy on 2013-01-20
An update here, i did remove dansguardian web filter as described  here.

```
sudo apt-get remove dansguardian tinyproxy firehol
```


It did remove and totally messed up the browsers in the process, now i can only
access https sites.  I don't recommend doing this.  I will remove this version of
ubuntu and reinstall regular 12.04.

---

### Post by axy_david on 2013-01-21
> **offgridguy said:**
> An update here, i did remove dansguardian web filter as described  here.

```
sudo apt-get remove dansguardian tinyproxy firehol
```
It did remove and totally messed up the browsers in the process, now i can only
access https sites.  I don't recommend doing this.  I will remove this version of
ubuntu and reinstall regular 12.04.
hahah u can acces https without removing dansguardian, reinstall it
then start your browser as sudo, problem solved
(make sure you don't use the same profile as root because all addons and history will be gone if using the browser as user again)

---

### Post by offgridguy on 2013-01-21
> **axy_david said:**
> hahah u can acces https without removing dansguardian, reinstall it
then start your browser as sudo, problem solved
(make sure you don't use the same profile as root because all addons and history will be gone if using the browser as user again)
I realize i can access https without removing DG, that was never the issue, mainly
i don't have enough computer savvy to configure  dansguardian, i was content to leave it but was following some advice i received prior in this thread.
Firefox works much better in regular ubuntu 12.04.  Another user has given me
private instructions on how to remove dansguardian without disrupting the
browser but i haven't tried it yet.

---

### Post by offgridguy on 2013-01-27
I have tried further instructions to remove dansguardian, by first changing the proxy
settings in Firefox, then removing dansguardian.   This also failed ,it did remove 
dansguardian but still disrupted the browser.  So i have reinstalled DG {again}.

> **stlsaint said:**
> Also dg is configured strongly out the box and yes is tied directly into the internet handling via proxy. So yes removing DC without first turning off firewall will cause problem which is what you felt with.the goal is to not make it a overly simple task for our tech savvy kids these days. 
Looking again at this reply from stlsaint, how do i turn off firewall?

Okay i have found it here.:D:D

[https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall)

---

### Post by offgridguy on 2013-01-31
Update;  I have removed the dansguardian web filter, first by changing the firefox proxy
settings to , no proxy, then using the ufw method here.

[https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall)

Here i disabled firewall, then removed dansguardian with

```
sudo apt-get remove dansguardian tinyproxy firehol
```

Then used.

         ```
 sudo apt-get autoremove
```
To remove no longer needed packages. Restart computer and Voila.:D

Thanks Prim01, Freedomeagle1967 and stlsaint.

In case your wondering, this means no firewall enabled.

---

### Post by offgridguy on 2013-01-31
As much as i like UCE, i find this whole issue to be  to much of a hassle, re-enabling the
firewall without dansguardian renders the browser inoperable.](*,)
But 'Hey' i tried.

---

### Post by offgridguy on 2013-02-20
Update; Reinstalled UCE yet again, trying to get some help from 
the dansguardian  support forum regarding a tutorial, no luck yet.

Tried to update firefox but unable to as access was denied, so I 
have once again disabled firewall and removed dansguardian. Downloaded google chrome and using that, removed firefox as well.

May try to enable firewall, to see what happens. I realize that
dansguardian is an integral part of UCE, but for someone who doesn't want it or is unable to configure it, it is an annoyance.

edit; have enabled firewall and all seems to be working, success so far, which is why I removed firefox, to start over with a different browser.:D

---

### Post by parkernathan on 2013-03-30
Hey OffGridGuy,

Check out my thread on configuring DansGuardian:

[http://ubuntuforums.org/showthread.php?t=2126079](http://ubuntuforums.org/showthread.php?t=2126079)

I'm getting the hang of it better now. I'm leaving it installed, just tweaking the files when I need to allow something. That way I have the security of DansGuardian with the flexibility of being able to approve legit sites and file types.

Hope it helps!

---

### Post by davidkennedy85 on 2013-04-02
You have the power to configure DansGuardian however you like it. In fact, Linux users are given so much power that it can be overwhelming. In Linux, there is rarely a "just open program x and press button y" solution to a problem. Such convenience tends to take power away from the user. Some people prefer it that way, and if that sounds like you then you might try a different operating system.

In order to get the most out of a complex tool like DansGuardian, you must be willing to put in some time to understand how to use it. The best way to learn how DansGuardian works is to simply read the configuration files, which typically reside in /etc/dansguardian. In particular, there are two files in this directory that you should be familiar with:

**/etc/dansguardian/dansguardian.conf** - this file contains settings related to logging, reporting, network and performance. Most of these settings have sensible defaults, but you should read it anyways in case you want to tweak anything. It is documented very well, but with a little patience you will be able to get through it and have a much better understanding of how DansGuardian works.

**/etc/dansguardian/dansguardianf1.conf** - this file contains settings for the first (and default) user group. (You can set up multiple user groups in DansGuardian, in which case there would be multiple files named dansguardianfn.conf, where n is the group number.) It contains a number of important settings for the user group, such as naughtynesslimit. It also contains hard references to a bunch of other files referred to in DansGuardian as "lists", like this one:

    [FONT=courier new]bannedphraselist = "/etc/dansguardian/lists/bannedphraselist"[/FONT]

Lists can contain website addresses (in the form of domains or fully qualified URLs), phrases, words, file extensions, etc., or they can contain references to other lists. They can also contain both:

    [FONT=courier new]# /etc/dansguardian/lists/bannedphraselist

    # This line blocks pages containing the word "flabbergasted"
    <flabbergasted>

    # This line references a list of gambling-related phrases
    .Include</etc/dansguardian/lists/phraselists/gambling/banned>[/FONT]

Anyways, I could spend a day telling you about every list, but you'd learn as much in as little time by reading the files.

I suspect your specific problem is related to the bannedextensionlist, which lists file extensions that DansGuardian should block. You could try commenting out the entry for .exe files (or .zip files or .tar files or whatever).

Even better, you could check the DansGuardian log, usually located at /var/log/dansguardian/access.log. The entry related to Firefox Update should point you towards the right list to edit.

The Ubuntu CE community is not the most active group of people who use DansGuardian. Since DansGuardian is on many distributions of Linux, you could try any of these places:

[http://www.askubuntu.com/]("http://askubuntu.com/")
[http://bbs.archlinux.org/]("https://bbs.archlinux.org/")
[http://www.fedoraforum.org/](http://www.fedoraforum.org/)
[http://forums.debian.net/](http://forums.debian.net/)
[http://unix.stackexchange.com/](http://unix.stackexchange.com/)

Also, don't forget the DansGuardian Wiki. It's quite good: [http://contentfilter.futuragts.com/wiki/doku.php](http://contentfilter.futuragts.com/wiki/doku.php)

Hope that helps.

---

### Post by jonnierocks on 2013-05-14
I've also got a question that I'm hoping y'all can answer. I'm fairly new to Ubuntu and have version 12.04 but want to switch to CE. The problem I am having is that I can download Ubuntu CE but I don't know how to install it. Any suggestions?

---

### Post by parkernathan on 2013-05-16
Burn it to a CD (or I can give you the instructions on how to create a Flash drive as well) and reboot your PC. It'll ask you to install Ubuntu and walk you through the process. If you need more help, let us know.

---

