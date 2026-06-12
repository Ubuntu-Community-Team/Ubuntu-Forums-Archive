---
title: "Security noobie with questions and popcorn."
date: 2011-03-12
forum: Security
---

### Post by Azaz on 2011-03-12
:popcorn: See. Popcorn.

Hi I'm a new ubuntu user and I have a few security questions. This fourm has been incredibly helpful when it comes to my noobie questions so thanks in advance for your info.
(warning the following questions might be very simple or noobie)

1. Is it true that Linux is virus proof?

2. Do I need anti virus software or anything of that nature? 

3. Because I'm using duel boot can a virus I get on linux that would be for windows go to windows when I switch between the two or vice versa?

4. If 1 is true does that mean I can go crazy and click every (YOUR THE 1000 VISITOR CLICK HERE FOR PRIZE!!!!!) popup and all that junk? (not going to but just wondering)

5. Are there other things that can still screw up my computer on the web even though im still using Linux?
 
Thanks. :)

---

### Post by CandidMan on 2011-03-12
Hi, welcome to the forums
1) It should usually take deliberate effort to run an virus(is rm -fr a 'virus'?). 'Nothing auto-runs in Ubuntu'.
2) That's up to you, the current Linux offerings are inadequate (IMHO) for Linux. AV is very reactionary. You should be able to tell exactly what's running and what files are running with something like "lsof"
3) Whichever environment you run determines the rules. So if you boot windows with a virus and it decides to mount and sabotage a Linux partition it will
4) Technically whatever you do as a regular user will be confined to /home/<you>/ but I wouldn't advise tempting fate in case you come across an effective privilege escalation exploit. Have a look at Apparmor
So, technically yes
Actually no
5) See, 3. As mentioned above everyday activities technically don't affect the system but you only have to click on bad link to an effective 0-day
Hope that helps

---

### Post by BkkBonanza on 2011-03-12
Linux is not "virus proof" but there are currently no known viruses "in the wild" for Linux. 

That doesn't mean you can't have problems. New users tend to mess things up via their own mistakes. And with poor configuration hackers can still exploit the system and abuse things. The default Ubuntu install is quite resistant to virus related problems and less suspectible to attacks.

Windows viruses won't run in Linux but they could in theory cause damage to Linux partitions, though that seems unlikely. Viruses don't usually wipe disk partitions but instead they usually try to take over the system and use it as a node in a botnet, or install hooks to capture private data etc.

Keep your system up to date and don't install unknown programs not from the repositories (unless you know what you're doing).

---

### Post by COMPUTIAC on 2011-03-12
Hello, I use this add-on; (WOT)  Web of Trust:  

 [http://www.mywot.com/en/download](http://www.mywot.com/en/download)

Easy to install and use,_ will not_ let you go to bad site without warning you first !

  It block's the site, _until ***Y****ou*** insist to proceed._

---

