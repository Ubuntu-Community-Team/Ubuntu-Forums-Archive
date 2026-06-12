---
title: "OpenOffice 3.1 Released!"
date: 2009-05-14
forum: The Cafe
---

### Post by gjoellee on 2009-05-14
OpenOffice 3.1 is released!

What's new? [http://www.openoffice.org/dev_docs/features/3.1/index.html](http://www.openoffice.org/dev_docs/features/3.1/index.html)

---

### Post by coldReactive on 2009-05-14
Just wondering, is there a PPA or something? I don't want to download and install EVERYTHING, I just want to update what I have.

I only use OpenOffice writer, so I don't need the whole package.

---

### Post by gjoellee on 2009-05-14
Information here: [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

---

### Post by timcredible on 2009-05-14
> **coldReactive said:**
> Just wondering, is there a PPA or something? I don't want to download and install EVERYTHING, I just want to update what I have.

I only use OpenOffice writer, so I don't need the whole package.

deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main

also, a how-to:
[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

---

### Post by coldReactive on 2009-05-14
According to the how-to I still have to re-install Openoffice.

---

### Post by gjoellee on 2009-05-14
You will have to remove the old version anyway

---

### Post by coldReactive on 2009-05-14
> **gjoellee said:**
> You will have to remove the old version anyway

Yeah, not going to happen.

---

### Post by miggols99 on 2009-05-14
OpenOffice has needed anti-aliasing for ages! It looks so horrible when there are jagged lines around everything. This is a much needed update :D

Also, the "shadow" with dragging text makes things look a lot better :)

Grammar checker also sounds good, but I hardly ever use it in Word...it's good anyway.

---

### Post by stwschool on 2009-05-14
I notice that it's doing a better job of opening some docx files 3.0 screwed up, I might deploy it at school once the crashing stops (it crashes a little too much for my liking).

[edit for typo]

---

### Post by SuperSonic4 on 2009-05-14
It seems pacman upgraded me to a SVN version of office 3.2 xD

---

### Post by sports fan Matt on 2009-05-14
gjoellee, is there any difference from 3.1.0?  (The one that has the splash screen at 3.0)

---

### Post by forrestcupp on 2009-05-14
> **miggols99 said:**
> 
Grammar checker also sounds good, but I hardly ever use it in Word...it's good anyway.

Well, they didn't really add a grammar checker.  All they did was make their current grammar framework more integrated.  All that means is that you can now use the LanguageTool 3rd party extension from the Tools menu.

No offense to the people who worked so hard on it, but LanguageTool is a poor alternative to Word's grammar checker.  It's hardly even worth using.

---

### Post by coldReactive on 2009-05-14
> **timcredible said:**
> deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main

also, a how-to:
[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

When i got to step 3 I noticed that I have openoffice installed already, meaning step 3 won't work.

it also reinstalled rhythmbox, which I now will have to uninstall.

---

### Post by sydbat on 2009-05-14
> **coldReactive said:**
> Yeah, not going to happen.I went into Synaptic -> Status -> "Installed (upgradeable)" which showed all the ppa OOo -> right clicked on Open Office Core -> chose the 'upgrade' option and it automatically removed the necessary files, uploaded and installed the upgraded files.

Badabing!

---

### Post by coldReactive on 2009-05-14
> **sydbat said:**
> I went into Synaptic -> Status -> "Installed (upgradeable)" which showed all the ppa OOo -> right clicked on Open Office Core -> chose the 'upgrade' option and it automatically removed the necessary files, uploaded and installed the upgraded files.

Badabing!

See reply number 13

---

### Post by sydbat on 2009-05-14
> **coldReactive said:**
> See reply number 13:D

I had noticed a couple of days ago that there was a release candidate in the ppa for 3.1. I chose not to do the 'partial upgrade' in the Update Manager because I was not sure I wanted an RC. 

A couple of days later I was looking for some app in Synaptic and looked at the Status section. There was the same 'upgrade' in "Installed (upgradeable)" and I figured why not. So I did what I described in reply #14 and it seems to have worked without all the extraneous steps from the tutorial.

---

### Post by tazz4vr on 2009-05-14
How is the docx convert working?  Does it still crash making the attempt?  I haven't upgraded just yet, if it still crashes, then I will keep what I have been using, I think, ah man, now not sure.  Not sure if the 'If it's not broken, why fix it approach' is a good one for my use.

---

### Post by coldReactive on 2009-05-14
> **tazz4vr said:**
> How is the docx convert working?  Does it still crash making the attempt?  I haven't upgraded just yet, if it still crashes, then I will keep what I have been using, I think, ah man, now not sure.  Not sure if the 'If it's not broken, why fix it approach' is a good one for my use.

You have a docx we can test it on?

---

### Post by tazz4vr on 2009-05-14
unfortunately what I have is not something I can send out, I am trying to have just a standard doc sent to me in the docx format.  Will get back to you shortly.

---

### Post by kevin11951 on 2009-05-14
I created two test documents for those who wanted to test it:

.docx for testing:[       http://kviero.com/Test.docx](       http://kviero.com/Test.docx)
.doc to compare it to:[   http://kviero.com/Test.doc](   http://kviero.com/Test.doc)

---

### Post by gjoellee on 2009-05-14
> **sox fan Matt said:**
> gjoellee, is there any difference from 3.1.0?  (The one that has the splash screen at 3.0)

I don't know, I am not using the stable verison of OpenOffice. I am also on Arch so I do't have the orange Ubuntu splash.

---

### Post by tazz4vr on 2009-05-14
> **coldReactive said:**
> You have a docx we can test it on?

Just a quick, how my day has gone....!  I finally received a response to my request for an attached doc in the docx format, what I received :roll: was a copy/pasted portion of a docx doc into an email!  ughhhhhhhhhhhhhhhh!  And they live in our world unsupervised! :shock:

---

### Post by coldReactive on 2009-05-14
> **kevin11951 said:**
> I created two test documents for those who wanted to test it:

.docx for testing:[       http://kviero.com/Test.docx](       http://kviero.com/Test.docx)
.doc to compare it to:[   http://kviero.com/Test.doc](   http://kviero.com/Test.doc)

I can open the docx, but I can't save it, as OpenOffice doesn't have the ability to save as docx.

---

### Post by tazz4vr on 2009-05-14
darn it Jim... I am sooooooooooo not going MS 07, i'll have to invest in converting options!  Thanks for the attempt coldreaction.

---

### Post by tazz4vr on 2009-05-22
After much debate and adamant denial, I finally had to use the Microsoft office Compatibility Service Pack for the 2007 issue w/docx- so far so good.  No crashes with the oo that I use, which is still the 2.4, haven't had the need to upgrade just yet, and also haven't noticed any major issue's with the formatting of converted docs, right now everything seems to be working, so we're good!

---

