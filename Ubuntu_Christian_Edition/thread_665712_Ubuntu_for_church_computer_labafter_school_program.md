---
title: "Ubuntu for church computer lab/after school program"
date: 2008-01-12
forum: Ubuntu Christian Edition
---

### Post by twin_57103 on 2008-01-12
Hi folks,
  I'm going to set up a demo machine for our church's computer lab to see I can interest them in Linux/Ubuntu.  I'm not an administrator there - just a geek who helps out occasionally.  I have a borrowed system that I'm going to set up for this.

  The system I'm going to be setting up is a decent one - 1.8 GHz, but most of the machines in this lab are sub 1 GHz, with one or two as low as 500 MHz, so performance is key.  I'm debating between a couple configuration options, and I'd like to have the demo system as close to what I'd actually use as possible, despite the fact that it is considerably faster.

  Here's my question: I know that Ubuntu CE is basically a flavor of Ubuntu with different software selections, which can always be installed on a different *buntu.  I'm considering using Xubuntu and installing various educational and Christian packages vs. using Ubuntu CE and adding educational packages.

  I will also need to add a networked printer, whichever way I go.  If this gets off the ground, I may need to install mainline office software via Wine since they may want more standard options than Open Office (not my preference, but if it gets it off the ground, why not?).

  Would you suggest programs for inclusion (including ones that are included in CE, since I may end up using a different version)?  I'd like to make a good impression since I will probably only get one shot.

Thanks and God bless!
twin_57103

---

### Post by jcwmoore on 2008-01-12
> **twin_57103 said:**
> most of the machines in this lab are sub 1 GHz, with one or two as low as 500 MHz

Visit [http://en.wikipedia.org/wiki/List_of_Ubuntu-based_distributions]("http://en.wikipedia.org/wiki/List_of_Ubuntu-based_distributions") because if the systems that slow I would think you would want something even lighter than Xubuntu, i.e. Elbuntu or Fluxbuntu.  But if most the Systems are are near the 1GHz mark then Xubuntu would probably work fine for you.

> I will also need to add a networked printer
That is very simple to do, I just did it last night as a matter of fact.  I have a local printer installed on one machine and I "Shared" it.  Then to set up the printer on a second machine I just punched in the IP address and it found the printer and did the rest for me.  This probably isn't the more secure way, but was insanly easy to do.

As far as software... well there's a lot, I would do what you said, use some of the CE packages and then I would also look into some of the Edubuntu packages as well.  Best wishes with this project.

---

### Post by polmir on 2008-01-12
[http://www.knopper.net/knoppix/index-en.html]("http://www.knopper.net/knoppix/index-en.html")
[http://www.knopper.net/knoppix-mirrors/index-en.html]("http://www.knopper.net/knoppix-mirrors/index-en.html")

---

### Post by cjm5229 on 2008-01-13
Check out Edubuntu, you may be able to combine features from both, so that you can use the slower machines as workstations and use the faster ones as a server. I have never tried it, so I can't really tell you how to do it but I'm sure the Edubuntu Forum can help.

If you wish to demonstrate the superiority of OpenOffice over Microsoft office just have them try to save a file to PDF in Office, then show them how well OpenOffice does it. 

I don't know if that will help or not but it's worth a try.
God bless you, Carl

---

### Post by at0myx on 2008-01-13
What do they do in MSOffice that they can't do in OpenOffice?

If you can explain that everything they do now, they will still be able to do, I think that should be good enough.

Or...

Instead of using Wine, what about remote desktop.  I always used Quicken on my laptop and after putting Ubuntu on my desktop I was unable to correctly bring over the files to Gnucash.  So I decided to use remote desktop to run quicken until I can find an alternative.  You can just have one computer with MSOffice, and if they *really* need to use it, they can remote desktop to it and run it there.

The reason I say that is sometimes it can be a pain to install and run a Windows program on Wine (and you wouldn't want to show them you are having trouble).

---

### Post by twin_57103 on 2008-01-13
Thanks everyone for the ideas.  I'd like to stay with a mainline *buntu (Xubuntu, Ubuntu CE, Edubuntu) for several reasons, especially support, and the fact that others may eventually need to maintain this.  I've downloaded a CE image and will do so with Edubuntu as well.

I've never done a server setup and I'm not sure if I have the skill, time or energy right now to try.  It's a great idea, I'm just not sure it's achievable right now.

I'll play around with a couple of these versions and see how it turns out.  Thanks for your help.  God bless!

---

### Post by twin_57103 on 2008-01-13
> **at0myx said:**
> What do they do in MSOffice that they can't do in OpenOffice?

If you can explain that everything they do now, they will still be able to do, I think that should be good enough.

Or...

Instead of using Wine, what about remote desktop.  I always used Quicken on my laptop and after putting Ubuntu on my desktop I was unable to correctly bring over the files to Gnucash.  So I decided to use remote desktop to run quicken until I can find an alternative.  You can just have one computer with MSOffice, and if they *really* need to use it, they can remote desktop to it and run it there.

The reason I say that is sometimes it can be a pain to install and run a Windows program on Wine (and you wouldn't want to show them you are having trouble).

I have yet to put this idea to the ones who will be making the decisions, but a friend who helps with this lab feels that they will probably want MS Office for teaching purposes - to teach MS Office specifically.  He may or may not be right on this one.  My first goal would be to convince them of Open Office; MS Office via Wine is plan B.

If and when they use these systems for teaching software, they'd need quite a few concurrent Office instances.  I haven't worked with remote desktop much, but I believe this would only give access for one?

Thankfully, setup will be on my own time and they won't see that part.  There are some old games that I hope to set up on Wine for this, too.  This group has resisted moving  to Windows 2000 (from '98) because it won't run some of their software (tried to use compatibility modes without success).

---

### Post by chris308 on 2008-01-14
I'm working with a nearby Church/Private School right now to setup an Internet filter for their lab.  I selected Linux as my OS  specifically Untagle on a 1GHz PIII box w/512MB & 40 GB HD.  Amazingly simple to setup and manage.

I plan to demonstrate more OSS options for them as time progresses.  Fortunately, for me most of their workstations are >1.5 GHz P4's.  Personally, I would do my best to solicit local businesses for some donated computers to upgrade this lab.  You would be surprised at what they discard or upgrade.  For example, our public school just received from our local I.R.S office Dell 2.2 GHz P4's and network printers!  Also, they are supposedly going to donated some 17" LCD monitors too. :-)

I wish you the best with this project and thank you for donating your time to assist them.

Chris

---

### Post by cjm5229 on 2008-01-15
If you have trouble with installing Office in Wine, try crossover office. I believe they have a trial version you can use to test it. It is one of the apps that Automatix will install if you want to use it, It should be easy to install on it's own though. I have not had much luck using the latest Wine update. I don't know what they did but several apps I had installed quit working and I have had trouble trying to install anything into it. eSword is my main app that I use in Wine and it hasn't worked since about two weeks after Gutsy went final. Good Luck. Carl

---

