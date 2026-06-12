---
title: "libreoffice 3.6.5"
date: 2013-02-01
forum: The Cafe
---

### Post by aspergerian on 2013-02-01
When will libreoffice 3.6.5 be in the Ubuntu Software Center? Apparently, the new build fixes many bugs.
[https://wiki.documentfoundation.org/Releases/3.6.5/RC2#List_of_fixed_bugs](https://wiki.documentfoundation.org/Releases/3.6.5/RC2#List_of_fixed_bugs)

---

### Post by Paddy Landau on 2013-02-01
Probably not until 13.04.

I installed directly from the [Libre Office download page]("http://www.libreoffice.org/download/"). It works better than the previous versions, but the Quickstart function is not available.

---

### Post by monkeybrain2012 on 2013-02-01
> **Paddy Landau said:**
> Probably not until 13.04.

I installed directly from the [Libre Office download page]("http://www.libreoffice.org/download/"). It works better than the previous versions, but the Quickstart function is not available.


Me too. After configuring memory usage of LO it starts fast, really no need for quickstart any more.

---

### Post by aspergerian on 2013-02-01
> **Paddy Landau said:**
> Probably not until 13.04. I installed directly from the [Libre Office download page]("http://www.libreoffice.org/download/"). It works better than the previous versions, but the Quickstart function is not available.
 blurr
I don't have full LO installed. Is there a safe but thorough way to uninstall such LO compnents as my computer has so that I can do a clean install of the new LO?

Sorry for blurring into support. I'll post into a support forum.

---

### Post by Paddy Landau on 2013-02-01
> **monkeybrain2012 said:**
> After configuring memory usage of LO it starts fast, really no need for quickstart any more.
What specifically did you configure? I'd like to try whatever you did.

> **aspergerian said:**
> Is there a safe but thorough way to uninstall such LO compnents as my computer has so that I can do a clean install of the new LO?
Yes. Uninstall every package that begins with [FONT=Lucida Console]libreoffice[/FONT].
```
sudo apt-get remove 'libreoffice*'
```

---

### Post by monkeybrain2012 on 2013-02-01
> **aspergerian said:**
> blurr
I don't have full LO installed. Is there a safe but thorough way to uninstall such LO compnents as my computer has so that I can do a clean install of the new LO?

Sorry for blurring into support. I'll post into a support forum.

```
sudo apt-get autoremove libreoffice*

```

To make sure nothing is left you can check synaptic.

---

### Post by Paddy Landau on 2013-02-01
> **monkeybrain2012 said:**
> ```
sudo apt-get autoremove libreoffice*

```
We posted at the same time (almost)! I didn't realise that [FONT=Lucida Console]autoremove[/FONT] could take a parameter.

---

### Post by monkeybrain2012 on 2013-02-01
> **Paddy Landau said:**
> What specifically did you configure? I'd like to try whatever you did.


You probably know this already. See the screenshot.

Edited: Hmmm...I used to put "number of objects" to be 20. Don't know when did it become 590. But doesn't seem to make a difference.

---

### Post by grahammechanical on 2013-02-01
I am using 13.04 right now and it has Libreoffice 3.6.2. So, libreoffice 3.6.5 is not yet in the Raring Ringtail repositories.

---

### Post by monkeybrain2012 on 2013-02-01
> **grahammechanical said:**
> I am using 13.04 right now and it has Libreoffice 3.6.2. So, libreoffice 3.6.5 is not yet in the Raring Ringtail repositories.

LO's ppa has 3.6.4 rc1 for Precise and 3.6.4 for Quantal. It will probably be updated to 3.6.5.

---

### Post by Paddy Landau on 2013-02-01
> **monkeybrain2012 said:**
> You probably know this already. See the screenshot.Ah, thanks, you're right, I did know it. I didn't realise that it would affect the start-up time, though. I've made a few changes now.

However, come to think of it, this version of LibreOffice does seem to start faster than 3.6.4.

> **monkeybrain2012 said:**
> LO's ppa … will probably be updated to 3.6.5.Eventually. I decided that I didn't want to wait.

---

### Post by aspergerian on 2013-02-01
Regarding LO: "Version 4.0 is scheduled for release on 10 February 2013"
[http://en.wikipedia.org/wiki/LibreOffice](http://en.wikipedia.org/wiki/LibreOffice)

---

### Post by Paddy Landau on 2013-02-02
> **aspergerian said:**
> Regarding LO: "Version 4.0 is scheduled for release on 10 February 2013"
[http://en.wikipedia.org/wiki/LibreOffice](http://en.wikipedia.org/wiki/LibreOffice)
Wow, that's so soon after 3.6.5! I see that development on 3.6 will still continue, with the release of 3.6.6 due 14 April. But that will be the last 3.6 release.
[https://wiki.documentfoundation.org/ReleasePlan](https://wiki.documentfoundation.org/ReleasePlan)
The Wiki page notes that the dates are flexible.

I'm looking forward to trying 4.0. I hope the support for Microsoft's [FONT=Lucida Console].docx[/FONT] documents has been improved.

---

### Post by Peter Maunder on 2013-02-02
LibreOffice 4.0.3. RC3 is available now for the adventurous. If there are no major problems RC3 will become LibO4.0. Lib4.0 can co-exist with 3.6 so you can try one and revert if you have problems. Otherwise, it will be available in a few days.
LibO4.0 has added Firefox Personas support for those who like eye candy, in addition to the functional improvements.

---

### Post by aspergerian on 2013-02-02
I seem to have installed LO 3.6.5 on my Acer 1410 running Xubuntu 12.04.1.

I used
sudo apt-get remove 'libreoffice*'
[thnx Paddy]

Then from [http://handytutorial.com/install-libreoffice-3-6-5-in-ubuntu-12-04-12-10/](http://handytutorial.com/install-libreoffice-3-6-5-in-ubuntu-12-04-12-10/)
I used:
sudo add-apt-repository ppa:libreoffice/libreoffice-3-6
sudo apt-get update
sudo apt-get install libreoffice

Thnx to all who responded.

---

### Post by Paddy Landau on 2013-02-02
That repository is OK, but you could find beta versions appearing there, so be prepared for that. If you wish to stick with what you have, disable the PPA until the next Libre Office release.

If this thread has solved your problem, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by monkeybrain2012 on 2013-02-02
> **aspergerian said:**
> I seem to have installed LO 3.6.5 on my Acer 1410 running Xubuntu 12.04.1.

I used
sudo apt-get remove 'libreoffice*'
[thnx Paddy]

Then from [http://handytutorial.com/install-libreoffice-3-6-5-in-ubuntu-12-04-12-10/](http://handytutorial.com/install-libreoffice-3-6-5-in-ubuntu-12-04-12-10/)
I used:
sudo add-apt-repository ppa:libreoffice/libreoffice-3-6
sudo apt-get update
sudo apt-get install libreoffice

Thnx to all who responded.

Hmmmm... interesting. I didn't know about that ppa. The supposedly official one also by the LBO package team hasn't been upgraded for some time. Don't know how many ppas they have around. Are they going to make a new one when LBO4 comes out (this one says 3.6.x:))

It is quite easy to install directly from LBO, but as Paddy Landau says a small catch is that you don't get the quickstarter.

---

### Post by mike acker on 2013-02-02
> **monkeybrain2012 said:**
> LO's ppa has 3.6.4 rc1 for Precise and 3.6.4 for Quantal. It will probably be updated to 3.6.5.

how do i get on the IP list ?

---

### Post by zerubbabel on 2013-02-02
I've been running the 4.0rc* series on 12.10 for the past couple of weeks and have had no problems with it. I installed it early because it has a fix for a long-standing bug in Base that made tables extremely slow to traverse. For my database of only 5000 records, it went from about 24 seconds under LO 3.x to 3 seconds under LO 4.0rc* to jump to the last record. What a relief!

---

### Post by Asatru9 on 2013-02-03
I plan on installing Libre Office 4.0 when it arrives.

---

### Post by Paddy Landau on 2013-02-03
> **mike acker said:**
> how do i get on the IP list ?
What is an IP list?

---

### Post by Paddy Landau on 2013-02-07
[LibreOffice 4.0]("http://www.libreoffice.org/") has been released today!

I have installed it (it installs alongside LibreOffice 3.6, so you can run them at the same time).

So far, it works well. There are [some exciting additions]("https://www.libreoffice.org/download/4-0-new-features-and-fixes"). The one that doesn't work for me is the Unity Integration :(. I shall try to find out how to fix it and post back here.

---

