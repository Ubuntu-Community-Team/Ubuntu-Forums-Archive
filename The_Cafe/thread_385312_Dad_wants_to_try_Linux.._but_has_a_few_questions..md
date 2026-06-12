---
title: "Dad wants to try Linux.. but has a few questions."
date: 2007-03-15
forum: The Cafe
---

### Post by billdotson on 2007-03-15
Dad uses his Dell for work mainly.  He uses the Microsoft Office Suite for Excel, Word, Access and Powerpoint often and he also uses Quicken and TurboTax.  He also uses adobe reader for Palm OS+Documents to Go and syncs his smartphone w/ outlook for appointments.  He uses a 3D reach netopia USB wireless card for internet access.  He also has an Epson perfection 1650 scanner.

I have used OpenOffice and it seems to be compatible w/ everything but Access.  He also uses seamonkey mail and needs to be able to get all of his emails and his email accounts working.  He also uses iTunes but very rarely.  

Can I effectively get him setup for work on Ubuntu?  Mainly I need to be able to: get quicken, turbotax, microsoft office working correctly and import all his settings and data.  

I know the extreme is to use QEmu and run Windows in a virtual machine but I would like to get him setup w/o having to do that.

thanks.

---

### Post by Brunellus on 2007-03-15
> **billdotson said:**
> Dad uses his Dell for work mainly.  He uses the Microsoft Office Suite for Excel, Word, Access and Powerpoint often and he also uses Quicken and TurboTax.  He also uses adobe reader for Palm OS+Documents to Go and syncs his smartphone w/ outlook for appointments.  He uses a 3D reach netopia USB wireless card for internet access.  He also has an Epson perfection 1650 scanner.

I have used OpenOffice and it seems to be compatible w/ everything but Access.  He also uses seamonkey mail and needs to be able to get all of his emails and his email accounts working.  He also uses iTunes but very rarely.  

Can I effectively get him setup for work on Ubuntu?  Mainly I need to be able to: get quicken, turbotax, microsoft office working correctly and import all his settings and data.  

I know the extreme is to use QEmu and run Windows in a virtual machine but I would like to get him setup w/o having to do that.

thanks.
the USB wireless dongle is going to be trouble.  The smartphone sync is going to be trouble.  Quicken and TurboTax may be trouble, as might Office (depending on version).  

Crossover Office might mitigate the software problems, but the device problems might be tricky.  From his use profile, he seems like a poor candidate for migration--enough gadgets to be a problem, and committed to Windows enough to make retraining difficult.

---

### Post by aysiu on 2007-03-15
> **Brunellus said:**
> From his use profile, he seems like a poor candidate for migration--enough gadgets to be a problem, and committed to Windows enough to make retraining difficult. I agree with Brunellus. There seems to be an overdependence on Windows-only and/or proprietary software. Keep your dad on Windows.

---

### Post by billdotson on 2007-03-15
nooo!!!!!  Could he just run Windows in a virtual machine like QEmu?  When I was telling him about how defragging was not necessary for Linux he said he wanted to try it.  Btw he has Office2003.  

I have my Palm set to sync w/ my Ubuntu install and it works w/ Evolution.. dunno about smartphones though.  Also, yeah the wireless USB could be a problem.. I have heard of issues w/ that.

Do you think his scanner could work w/ Ubuntu?

I would like to get him setup but he absolutely needs Quicken, TurboTax, MS Office 2003 (unless Openoffice is compatible w/ access, excel, word and powerpoint) and a way to get his emails and accounts moved from seamonkey to thunderbird or something.

oh Windows.. you and your lock-ins.. if only companies made software like Quicken for Linux..

he is a Windows power-user (knows how to do what he needs to do, but not much outside of that) but I think he would be willing to learn enough to be able to operate a Linux distro.

Is there a way to use a boot floppy or something so I can boot Ubuntu from an external USB2.0 HDD so he can mess around w/ it? (as my PC is waiting for a replacement PSU to come back before I can put it back together)

---

### Post by Brunellus on 2007-03-15
> **billdotson said:**
> nooo!!!!!  Could he just run Windows in a virtual machine like QEmu?  When I was telling him about how defragging was not necessary for Linux he said he wanted to try it.  Btw he has Office2003.  

I have my Palm set to sync w/ my Ubuntu install and it works w/ Evolution.. dunno about smartphones though.  Also, yeah the wireless USB could be a problem.

Do you think his scanner could work w/ Ubuntu?

I would like to get him setup but he absolutely needs Quicken, TurboTax, MS Office 2003 (unless Openoffice is compatible w/ access, excel, word and powerpoint) and a way to get his emails and accounts moved from seamonkey to thunderbird or something.

oh Windows.. you and your lock-ins.. if only companies made software like Quicken for Linux..
qEMU won't do anything for his USB wlan adaptor, nor for his smartphone syncing.  If it weren't for the devices, virtualization might even be an attractive solution (if he can live with the performance penalty).  But the hardware may be a dealbreaker.

My mother and fatehr have been migrated to Ubuntu, but they are not nearly as device dependent as your father.  My middle brother is almost completely dependent on Windows, and worse, is churlishly technophobic--he refuses to learn any other platform.  My youngest brother runs Linux as a matter of course, but moves from Linux to Windows at school.

Different users present different challenges.

---

### Post by billdotson on 2007-03-15
I have a plain Palm Z22 that I can sync w/ Evolution but are smartphones a bit harder for that?

---

### Post by Brunellus on 2007-03-15
> **billdotson said:**
> I have a plain Palm Z22 that I can sync w/ Evolution but are smartphones a bit harder for that?
the USB Wlan will be the dealbreaker.

---

### Post by H.E. Pennypacker on 2007-03-15
> **aysiu said:**
> I agree with Brunellus. There seems to be an overdependence on Windows-only and/or proprietary software. Keep your dad on Windows.

I agree with aysiu.  As others said, he's the type of person who is currently using Windows without any seemingly big problems, so its better he stays with Windows.  Switching to Linux will require him to learn an entirely new language, and for someone like him, it is not worth the time.  Everything works for him already on Windows, and as much as I may preach open source software, your father is not the right person.

The right person has the time to gradually move away from proprietary software.  Your dad does not seem to be the right person, and there is, at least for now, no reason for him to switch.

It is better for him to stick to his Windows headaches than deal with a new set of problems by switching to Linux.

Give him a LiveCD, and if he is very excited about it, let him dual boot Ubuntu.  If that works out well, he could move on to regularly using Ubuntu for anything but business related activities.  How things end up depend on him, but don't expect things to move quickly or that the transition goes well.

---

### Post by seijuro on 2007-03-15
fyi both quicken and turbotax have online versions that are accessible from linux.

however, I tend to agree with the above if he is happy with what he has and it works for him, it's probably best to not "fix it" if its not broken.

---

### Post by shareMenaPeace on 2007-03-15
Well maybe he is up to and 50:50 solution. Meaning dual booting ubuntu. To test it out and maybe he is impressed enough to get a new supported wlan adapter?

But hard to tell if he is in the mood for this but if he understands and agree to a small learning curve with your support he might find this idea tasty?

Importend is to tell him the advantages which would be mainly

free of charge 
alternatives 
open source stuff
et cetera

Cheers

---

### Post by Tomosaur on 2007-03-15
Why don't you just give him a LiveCD and let him make his own mind up? Explain to him how he will have to do things differently and lose some of the software he currently uses. You will not know if the devices will work until you try them.

---

### Post by billdotson on 2007-03-15
well I have been using Ubuntu for about 6 weeks or so and I feel I have learned a decent amount of stuff w/ Linux.  Dad was reading an article the other day in a local magazine about keeping your PC maintained and working well.  The article was like:

-Defrag your harddrive
-Run disk cleanup
-keep a firewall up
-have a good virus+spyware/adware scanner
-keep automatic updates on
-do a comprehensive clean every now and then w/ a program like WinClean ($20) to ungunk your registry, etc.
-keep your software updated

My dad isn't a computer novice.. he is more like a Windows power-user.  He started messing w/ PCs in the days of punchcards and punchcards turned him off from computers for the time.  So he ended up getting a degree in something else but when computers started using floppies and harddrives he got interested again.  He knows (knew.. I don't know if he remembers all about it) how to program in Cobol and knows how to keep a good, clean, and stable Windows install.  Although, outside of what he has actually had to know for a job.. like Cobol, spreadsheets, Windows, etc. he is not very knowledgeable in technical things of computers.  Not to say he isn't good w/ computers, he just isn't good w/ anything that he doesn't have to know how to do for his work, or for previous jobs.

He knows I like computer-related things and sends me articles in the email all the time and brings me IT magazines and such and so he naturally was like "hey son check this article in this magazine out"  I pulled out my pen and put an 'x' next to virus/spyware/adware, automatic updates, software updates, automatic updates, defragging, disk cleanup and then handed it back to him and said you don't have to do these things w/ Linux at all.  He then told me he would like to try Linux and asked me to research if he could effectively move to Linux.

Oh and I checked w/ him and he does NOT sync his smartphone w/ outlook.. he only syncs it at work.  So.. the only programs he must have are Quicken, TurboTax, and Microsoft Office.  I showed him openoffice a few weeks ago and so when he said he would like to try he wanted to know if he could save the openoffice files in the MS Office formats.  He uses access, word, excel and powerpoint.  He wants to know if he can use openoffice to be compatible w/ all of those formats.  From what I have seen openoffice isn't compatible w/ access.. but I could be wrong.

So really apart from getting Quicken, TurboTax and a MS Office compatible office suite the only thing holding a switch back is that USB wireless adapter.  I told him that he would most likely have to run TurboTax and Quicken inside a virtual machine and his response was "So if I am using Linux why should I still have to use Windows?  Why can't I run my programs in Linux and not use Windows @ all?"  I just told him that if he needed to use Quicken or Turbotax he could just open Windows like he would a program to do his work and do everything else in Linux, but I don't know if he really wants to do that.

So all I need to do is find a solution to that USB wireless adapter and talk him into how a virtual machine isn't that bad and he only uses Windows when he has to use Quicken or Turbotax.

Btw.. you say Quicken and Turbotax can be accessed online?  If that is so and he can have all his current data that would surely ease the transition.  Not having to run a virtual machine would be much more appealing to him.

---

### Post by LookTJ on 2007-03-15
As for word and excel, he could use writely.com if he has google account. If he doesn't, I could send an invite.

---

### Post by maniacmusician on 2007-03-15
> **Taylor said:**
> As for word and excel, he could use writely.com if he has google account. If he doesn't, I could send an invite.
Zoho.com is better than writely. And writely does not exist anymore, it is now "docs.google.com"

As for your father, if you're really determined to switch him over, then there's a simple solution; test everything he'll need first on your computer. Try to get the USB wireless working on your computer, make sure his stuff is compatible with OO, see how the VM thing works out, try out the online versions of Quicken/Turbotax, etc. 

Do a dummy test on your Linux box with all the stuff he'll need.

Also, consider the fact that his computer may not have the specs to run a VM; does it?

---

### Post by sdowney717 on 2007-03-15
can you run XP virtualized inside of ubuntu?

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

looks like you can do this!

---

### Post by billdotson on 2007-03-15
Well he says he wants to try Linux, but he would really just like to get completely rid of Windows instead of having to rely on Windows.  I told him if he wants to do that he shouldn't use proprietary Windows only software but he says that a lot of people use TurboTax and Quicken and there really isn't another option for financial work.
  
His PC is a bit old.. a ~5 year old Dell w/ a P4 1.6GHz and 512MB of RAM (whatever bus speed RAM Dell's had ~5 years ago)

He has stated that he does not want to try the online versions of TurboTax or Quicken @ all because he wants to keep his financial statements on his PC.. not a server out somewhere else.  That is unless the company that does Quicken +TurboTax allows you to use the online versions and save the data back to your hard drive.  Also, he said that he had the general idea that these online versions were stripped down and wouldn't be as useful to him as the hard drive versions.

I know OpenOffice is compatible w/ Excel, Word and Powerpoint but I am not sure about Access.. maybe a simple search of openoffice site would clear that one up.

I do not know if his PC would be capable of running a virtual machine or not as it isn't that powerful PC, but that seems to be the only way right now.  

Also, is there a way to get his Epson scanner working.. as that is the only device other than his HP printer (which I hear HP is good for helping w/ printers)?

Hmm now the big thing is that wireless USB adapter.. isn't there something called ndiswrapper for that?

---

### Post by maniacmusician on 2007-03-15
Your dad doesn't really sound like an ideal Linux user to be honest. I'm not saying he's not good enough or knowledgable enough or something, but he relies on a lot of proprietary technology and he's not willing to let go of it. I know it seems like you want to switch everyone to Linux because it's a superior system, but in reality, if you tried to switch your dad, he'd probably end up having a **bad** experience, and that's worse than any other scenario. 

If he's willing to live with the fact that some things may not work in Linux, then sure, let him try. For instance, a dual-boot sounds ideal for his situation (computer won't be able to run a virtual machine very well). Also, you've got to get that USB wireless thing working for him or he'll feel like he's in a nightmare. Those things are awful.

---

### Post by sdowney717 on 2007-03-15
I say try the virtualization, what have you got to lose except some time?
I think it would be an interesting experience and I am thinking of it for myself. Why cant you dump the USB device that wont work and replace with something that will work?

---

### Post by billdotson on 2007-03-15
our ISP put the USB wireless adapters in so he will definitely not change any of them out.  He says if he still has to boot into Windows he doesn't want to bother w/ it.  His reasoning is if I have to boot into Windows to use that stuff why don't I use it all of the time.

It sounds like he is locked into Windows w/ too much proprietary stuff that can't easily work in Linux.. dangit.

---

### Post by Detonate on 2007-03-15
Kmymoney is a very good personal finance program that will use Quicken files.  I have been using TurboTax for 20 years, and I hope next year to be able to use the online version instead of the windows version.  My taxes are not complicated, so i should be able to make the switch.  If you father has a lot of prior years data that needs to be carried into next years program, that might be  a problem.  If he amortizes business equipment or has a lot of Schedule D stuff,  or Schedule E stuff, he will probably want to stay with the full program.

---

### Post by daynah on 2007-03-15
The way I see it, if you put someone on Linux who really does need to be on Windows (for example, business uses specific programs), that person is going to get a bad image of Linux. We know it's not Linux's fault, but as you've seen in many many whiney threads started on the forums, people who are new to linux, if they can't just do what they need to do, they blame what changed: Linux. Not the complicated legal mumbo jumbo behind the scenes.

If he really wants linux, dual boot. Give him some pointers on maybe how he miiight be able to solve some of those work problems, but just let him know that you're not sure he'll be able to do it. I think that the majority of us use linux at home, and then go to work where we have to use Windows on our work computers, so he shouldn't feel dirty about that. :)

---

### Post by Brunellus on 2007-03-16
> **billdotson said:**
> our ISP put the USB wireless adapters in so he will definitely not change any of them out.  He says if he still has to boot into Windows he doesn't want to bother w/ it.  His reasoning is if I have to boot into Windows to use that stuff why don't I use it all of the time.

It sounds like he is locked into Windows w/ too much proprietary stuff that can't easily work in Linux.. dangit.
This makes him a less than ideal candidate. 

He uses the computer, and is dependent on a lot of 'black box' devices and programs which he did not configure himself and likely does not know how to configure himself.  The fact that he doesn't know how his networking was set up (ISP installed USB Wlan adaptor) is a BIG WARNING FLAG.  Dumping him to Linux and potentially stripping him of his devices is a losing proposition.

He is also dependent on at least two software packages (Quicken and TurboTax) whose Linux functionality is questionable at the very best.  Moving him to Linux will strip him of these, too.

To the poster that suggested virtualization:  Virtualization is an imperfect solution, and certainly not an elegant one.  As OP's father noted "If I have to run Windows for those things--why not just keep running Windows all the time?"  Why not, indeed, when you consider that VMs consume very real system resources and run with a considerable performance penalty. 

A migration of this type might require a phased migration--first, away from proprietary software while running Windows.  Then, once the user is 'dependent' on Free Software packages (as my own parents became dependent upon Firefox and OpenOffice), it is easier to nudge the user to a totally free operating system.  THe second phase might never happen, though, unles a crisis forces it.

---

### Post by jdong on 2007-03-16
I have a WM5 smartphone and setting it up for syncing took me quite some hours, and was actually "quick" for me only because I've had to deal with RNDIS/PPP VPN under Linux before.

It's not a process I would ever recommend to anyone except to prove their networking, compiling, debugging, etc skills.

Your dad sounds like someone who should dual-boot Ubuntu and Windows, until his hardware is totally supported under Linux.


I wouldn't automatically dismiss USB networking as Linux incompatible. Try booting a LiveCD and seeing if the networking works (it'll be easier to assess that once Feisty comes out, it 'll have a much better networking stack)

---

### Post by motin on 2007-04-15
I'd recommend installing VMWare Server on Windows and let him try out Ubuntu from there

---

### Post by Rich43 on 2007-04-15
> **billdotson said:**
> Dad uses his Dell for work mainly.  He uses the Microsoft Office Suite for Excel, Word, Access and Powerpoint often and he also uses Quicken and TurboTax.  He also uses adobe reader for Palm OS+Documents to Go and syncs his smartphone w/ outlook for appointments.  He uses a 3D reach netopia USB wireless card for internet access.  He also has an Epson perfection 1650 scanner.

I have used OpenOffice and it seems to be compatible w/ everything but Access.  He also uses seamonkey mail and needs to be able to get all of his emails and his email accounts working.  He also uses iTunes but very rarely.  

Can I effectively get him setup for work on Ubuntu?  Mainly I need to be able to: get quicken, turbotax, microsoft office working correctly and import all his settings and data.  

I know the extreme is to use QEmu and run Windows in a virtual machine but I would like to get him setup w/o having to do that.

thanks.

Put the Ubuntu CD into his dell.. it should boot into linux from the CD WITHOUT installing it. You can test hardware etc from there! I recommend waiting a few days for feisty too and try that.. Feisty should support more hardware.

---

