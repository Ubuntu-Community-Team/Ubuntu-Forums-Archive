---
title: "How installations work"
date: 2006-07-21
forum: Testimonials &amp; Experiences
---

### Post by jrleighton on 2006-07-21
There's a fairly self-explanatory Wikipedia article on the standard folders: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

I have a couple of questions though, being new to all this and (like most people I should think) more familiar with the workings of Windows.

Q1.  Why does Ubuntu have an additional directory structure over and above the standard folders - I refer to all of the hidden directories installed in the users home directory. This is "non-standard" (when compared with the aforementioned Wikipedia article).  Or is this just normal and how most linux distributions work ?   Question: if it's an Ubuntu only thing, then why ?

Q2. When software packages get installed (either via Synaptic Package Manager or similar; or even when I compile and install myself) then what is the logic for files being installed in various directories.  The logic applied in the Wikipedia article referred to above doesn't seem to hold strictly true, plus there's the hidden folders (see Q1) too.  I'm confused - I'm looking for logic, but I can see my PC getting very messy now.  Having learnt to keep order to my Windows PCs in the past, keeping everything in the one Program Files directory, the methodology for Ubuntu isn't clear at all to me.  What is it ? If there are standards, why aren't they being adherred to that strictly ?  Is there a software package to "clean" and tidy my PC up ?  Does it matter ? 


That was really more than 2 questions, but never mind. I'd really appreciate it if somebody in the know could help point me in the right direction for some answers.  I'd help me make the mental transfer from Windows a lot less painful for me, and I suspect many others too.  Thanks in advance.

---

### Post by nalmeth on 2006-07-21
The bonus is that the package management system knows where everything is, and you don't have to go hunting down program files and deleting them.

The hidden folder's in your /home are where configuration files for your applications are kept. This way, you have permission's to change application settings, and you can preserve your configuration's even after you uninstall an app.

Basically, package management is extremely organized. 

I think it might just be your Windows instincts that confuse you here, unless you're compiling some funky apps (in which case use checkinstall), or unless you REALLY NEED TO KNOW where everything is, you will need to look no further than Synaptic to handle all your applications.

I should point out, config's for apps aren't deleted with the app unless you want them to.

A huge advantage of this, is that you can throw your /home on a seperate partition, and if thru a lot of tinkering you corrupt your install, you can reinstall the OS, and save all the old configurations!

---

