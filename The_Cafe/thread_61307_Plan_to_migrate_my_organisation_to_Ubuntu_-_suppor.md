---
title: "Plan to migrate my organisation to Ubuntu - support needed!"
date: 2005-08-31
forum: The Cafe
---

### Post by darkfox on 2005-08-31
[font=Verdana]I am coming towards the end of a contract as IT Manager for a reasonably
affluent not-for-profit organisation, the British Small Animal
Veterinary Association.  Part of my remit is to develop an IT strategy
for the next 3-5 years.

CURRENT SET-UP

The organisation runs 3 Windows 2000/2003 servers in-house providing:
 - File and Print
 - Financial system (Microsoft Great Plains)
 - Bespoke VBA administrative system
 - Terminal Services
 - Mail (Microsoft Exchange)
 - Firewall and Proxy (Microsoft ISA)

In addition there is a .NET based website hosted remotely that links
back to the admin system and Microsoft Great Plains.

We have 25 desktops all running Windows XP and a varying number of
volunteers accessing via Windows laptops.

CHANGE EVALUATION

I have been a Linux user for around 6 years and Ubuntu evangelist since
October 2004. I have now completed an evaluation which leads me to
believe the correct course of action for this organisation is migrate
all desktops and services to Ubuntu with commercial support from
Canonical.  A phased approach is obviously required, summarised as:

[1] Desktop application migration to FOSS equivalents, retaining MS
Windows (OOo, Firefox, GiMP, etc.)

[2] Server migration to Ubuntu and FOSS applications for
   - File and Print
   - Firewall and Proxy
   - Domain control
   - Mail
Retention of a Windows server for financial and administrative systems
and Terminal Services

[3] Desktop migration to Ubuntu, with TSclient access to financial and
administrative systems

[4] Replacement of financial and administrative systems with
Linux-compatible FOSS (or possibly commercial) alternatives, and removal
of Terminal Services

HELP ME PLEASE!

Firstly, I would appreciate your advice on whether the above outline is,
generally speaking, a recommended course of action and in a general
sense whether there are alternatives worth considering.  Secondly, and I
guess more importantly, I need to supplement the strategy with a
comprehensive set of convincing arguments for migrating over to Linux
(and where possible FOSS), and this is where I really need help.

Do you have material you could supply me with, or point me to resources
that have proved successful?  If I write these myself they will just
sound biased and may well miss important points, so I'd rather access
established existing material.  The material should try to achieve the
[color=Black]following:
[/color][/font]                                                            [font=Verdana][color=Black] - An overview of what the Linux-based (preferably FOSS) options are[/color][/font][font=Verdana][color=Black]
 [/color][/font][font=Verdana][color=Black]- Reasons for considering Microsoft alternatives[/color][/font][font=Verdana][color=Black]
 [/color][/font][font=Verdana][color=Black]- Benefits and risks of migrating over[/color][/font][font=Verdana][color=Black]
 -  [/color][/font][font=Verdana][color=Black]Guidelines on cost estimation - both eventual savings if any and costs[/color][/font][font=Verdana][color=Black]
for getting there
  [/color][/font] [font=Verdana][color=Black]- Support structures that can help the journey[/color][/font][font=Verdana][color=Black]
  [/color][/font][font=Verdana][color=Black]- Advisable plans and timescales[/color][/font][font=Verdana][color=Black]
[/color]
In other words, something that evangelises and de-bunks myths without
evangelising (if you know what I mean)!!

Any help at all that you can give me in this area would be highly
appreciated.

Thanks[/font]

---

### Post by davmac on 2005-08-31
In think the phasing looks OK, although 2, 1, 3, 4 order would be equally suitable. Without a doubt the most ambitious and risky phase is number 3. 

I'd suggest a pause after the first two stages. By then the organisation is going to be getting more comfortable with FOSS in general. The state of the Linux desktop will have improved. The biggest threat to this phase though is going to be your users. Have a look at the thread about converting windows users to ubuntu ([http://www.ubuntuforums.org/showthread.php?t=58862&highlight=convert)](http://www.ubuntuforums.org/showthread.php?t=58862&highlight=convert)). I've a suspicion that the majority of your users will fall into the most difficult to convert category... 

As well as Canonical, I'd also be looking towards Red Hat, Suse, and the more established vendors for a job like this. I'd be contacting them now too. It is in their interests to have great resources available to help you put your case together, along with case studies of successful migrations.

---

### Post by KingBahamut on 2005-08-31
Marketplace Support area. 

Go there. 

[http://www.ubuntulinux.org/support/supportoptions/marketplace/europe](http://www.ubuntulinux.org/support/supportoptions/marketplace/europe)

Youll find many resources there.

---

### Post by phen on 2005-08-31
the only argument for a switch, a company/organisation understands is money. But now it gets complicated: you can save money by: 

administration/infrastructure:
spend less for licenses
spend less for administration (by saving time=money)
spend less for hardware
...

every-day work:
make processes faster for the employees (on the it side: by using better fitting software)
use software to automate robot-tasks
provide stable systems with ->100% uptime
spend less time(=money) with learning of new programs that do the same things like known ones!
...


you really have to calculate on your own. i think the oss-support-companies will help you hereby.

why do you want to switch? if new windows licenses have to be bought, it might be a good reason. but as long as everything works, don't change a running system.

one argument in all these discussions i can't understand is the windows-user argument. when working in a company, you never install software or do any admin work. i think it really doesnt matter whether you have to click the blue e or a red fox! a relearning phase shouldn't take longer than a week. BUT you have to know what applications are used in which ways, and have to provide them with replacements AND easy step-by-step guides (maybe printed on every desk).

well, i am working in a kinda high-tech company, so maybe the employees are faster in learning to use a new os than people from other businesses... but there are economists and lawyers, too

last point: the user-satisfaction can be poor in windows environments,too! when there is a new printer server set up, which needs totally different configuration than the old one, and the howto is lying somewhere on the intranet. maybe Linux can make some of these things even easier, because of its great flexibility! 

i remember the pdf-output procedure. (why do i have to PRINT my document over the intranet on a wierd PRINTER to SAVE my pdf on a Z: network drive???)

---

### Post by poofyhairguy on 2005-08-31
Best links I can find:

[http://www.google.com/url?sa=t&ct=res&cd=18&url=http%3A//www.kbst.bund.de/Anlage304428/Migration_Guide.pdf&ei=PPEVQ47XE5eW-gHJ7636DQ](http://www.google.com/url?sa=t&ct=res&cd=18&url=http%3A//www.kbst.bund.de/Anlage304428/Migration_Guide.pdf&ei=PPEVQ47XE5eW-gHJ7636DQ)

[http://www.linuxmigration.com/](http://www.linuxmigration.com/)

[http://www.troubleshooters.com/linux/w2l.htm](http://www.troubleshooters.com/linux/w2l.htm)

[http://publib-b.boulder.ibm.com/redbooks.nsf/RedbookAbstracts/sg246380.html?Open](http://publib-b.boulder.ibm.com/redbooks.nsf/RedbookAbstracts/sg246380.html?Open)

[http://enterprise.linux.com/article.pl?sid=04/07/23/2219257](http://enterprise.linux.com/article.pl?sid=04/07/23/2219257)

Hope that helps.

---

### Post by darkfox on 2005-08-31
Top links poofyhairguy - thank you

---

### Post by phen on 2005-08-31
wow, you found a nice one with the first! Chapter 4 adresses what i tried to explain above... I am impressed by the german administration (this does not happen regularly :-)

I think you have to check for any benefits before you try to convince others...

---

### Post by drizek on 2005-08-31
[QUOTE=phen]wow, you found a nice one with the first! Chapter 4 adresses what i tried to explain above... I am impressed by the german administration (this does not happen regularly :-)

I think you have to check for any benefits before you try to convince others...[/QUOTE]
 security and increased uptime could be some major factorsin wanting to use linux. also, server 2000 is now obsolete, you must purchase a license for that if you want to stay current, which will cost money. 

also, check this app out. [http://kde-apps.org/content/show.php?content=19008](http://kde-apps.org/content/show.php?content=19008)

---

### Post by poofyhairguy on 2005-08-31
[QUOTE=darkfox]Top links poofyhairguy - thank you[/QUOTE]

If we can help in another way please ask. That sounds exciting!

---

### Post by occy8 on 2005-08-31
Find one person first to play with openoffice. To check all important documents if they open correctly and if not redesign them.
That will stop a lot of nagging once everybody is testing.

Policy change?! Documents sent to external persons should only be pdf's. It's more secure and of course others most likely can't read the OOo files

---

### Post by ssck on 2005-08-31
Hi,

Take a look at how Singapore's Ministry of Defence and other asian governments are moving to open source.Getting your end users to start off on open source software is good.

[http://www.zdnetasia.com/insight/specialreports/0,39044853,39230757-5,00.htm](http://www.zdnetasia.com/insight/specialreports/0,39044853,39230757-5,00.htm)

Regards. :)

---

### Post by az on 2005-08-31
My advice would be to find someone close to you (from the ubuntu marketplace) who can not only support the OS, but personaly address your needs.  That is what these companies are for.

---

### Post by Nightwind on 2006-02-05
Personally I like Ubuntu and UNIX but I have the time and the energy to devote to working out problems.
I found that the users in a corporate or business environment do not adapt well to changes in their workstations. They have learned on Windows and to some extent are "comfortable" in the way that it works and they expect that not to change to a great degree. Employees as well as management do not care how what or why just so it works with little or no thought on their part.
If all the hardware is compatible, that's a plus, if not add the expense of new hardware to the migration cost.
Also expect IT support and cost to triple simply because of the learning curve and unforeseen issues that will happen. This will wan over time in most cases, but until it does you will have to justify to the bean counters why IT expenses are up during the migration.
I manage 3 physically separate networks total of 80 workstations with users of various skill levels and any time there was a change, their were issues. Staff just wants to get their work done with the least amount of stress and go home. 
At the least be sure to add the additional expense of re-training the staff over a period of time as well as any new staff that are hired because 99 times out of 100 they will come from a Windows environment.
The laptops will be an issue unless they are all perfectly identical. There are issues with shut down and hibernation, function keys and other quirks that haven't been de-bugged. Check the hardware list to make sure your equipment will work with any Linuxes.
There are still issues with the I686 kernel (Ubuntu) in power management. So do your homework and as the rest of them have suggested in this post. Good luck.

---

