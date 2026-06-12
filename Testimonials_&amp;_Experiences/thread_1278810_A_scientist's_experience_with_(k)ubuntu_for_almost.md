---
title: "A scientist's experience with (k)ubuntu for almost a year (typing this from windows)"
date: 2009-09-30
forum: Testimonials &amp; Experiences
---

### Post by ssri on 2009-09-30
Hi everyone,

I installed intrepid last year, and I thought some of you would like to hear my experiences with it.

System (current): HP Compaq 6910p, running Kubuntu Jaunty, KDE 4.3.1

What works and what doesn't:

audio: check (after ripping out the horrendous pulseaudio that came with medibuntu and reinstalling alsa)

video: check (after downgrading to xserver 1.5.2 and installing catalyst 9.3)

compositing: check (after installing compatible proprietary drivers for my card.  The opensource ati drivers that came with jaunty, or the ones checked out from git, had redraw bugs when moving menus around, unacceptable)

suspend/resume: nope (when the weather is right or when I'm feeling lucky.  Translation: a crapshoot)

freezing: every once in awhile when playing an audio file.  Again, this is unacceptable.

multimedia experience: horrific out of the box.  Installing mediabuntu was a snap, especially since I've done it before.  However, the rest was poor.  Amarok 2.x was just plain bad, so I had to install 1.4.10.  FLACs did not work with the xine engine due to a regression, so I had to downgrade it to intrepid's version.  MPlayer froze constantly, taking down X along with it until I installed a svn build from a ppa *sigh*

Hardware peripherals: Printer support has been excellent mainly due to the fact that my laboratory uses HP printers exclusively.

Office productivity: Fair, as openoffice replicated most of the functionality of MSOffice 2003.  However, when sharing documents from my research group who uses MSOffice 2007, Openoffice rendered data graphs incorrectly.  Thus, it disrupted collaborative projects.  Again, for my interests, this was unacceptable.  In addition, I had to resort to using foxit in wine in order to read and markup scientific papers due to lack of column recognition/support ([https://bugs.kde.org/show_bug.cgi?id=161324](https://bugs.kde.org/show_bug.cgi?id=161324)), a problem that is exacerbated by the rude maintainer, and the fact that acrobat-gtk is extremely sluggish in a qt environment, duh.

Research: Tried to use openoffice as long as I could until I ran into problems stated earlier.  Furthermore, I could not find anything that matched the duopoly of Word+Endnote.  Openoffice+zotero was okay, but it lacked style formats for bibliographies of several journals, formats that are necessary for publication.  Still, the zotero team did a fantastic job in integrating zotero with firefox and openoffice writer.  Thankfully, the formatting issue is one that is being actively worked on and will improve in the future.

As for why I'm typing this message from windows?  Well, I'm currently writing a grant and I found out that the feature sets of Openoffice and Zotero, in their current state, are unacceptable for this task.  Furthermore, everything in Windows just works.  All of my laptop drivers are listed on a single webpage from HP, which I downloaded and burned to a cd.  No random freezes or BSODs.  Themeing in winxp is fairly easy after installing a hacked uxtheme.dll.  I kind of grew tired with the constant tinkering I had to do in order to make my kubuntu system work in a fairly reasonable manner.  After booting into my windows partition for the first time in several months, I was amazed at the stability of its environment.  Also, I can enjoy some of the bash_aliases I made when using cygwin.  I still cannot let go of the terminal.  So for now, I'll be staying with Windows.  At least until I get bored with it again and try out something new ;).  Hopefully future editions of (k)ubuntu will fix/improve some of the OS-specific issues I listed above along with improvements in several of the opensource productivity software by their respective teams.  Hopefully they will reach feature parity with their proprietary software counterparts.  

PS.  Before the zealots come in and wish me luck with my future virus infestations, I would like to say that I've ran Windows since 3.1, and have yet to experience any virus infections *knock on wood*.  All it takes is some common sense, a virus scanner, a firewal and, at least in winxp, running the common usage account as a limited user.  As such, the only maintenance issue I've had with windows so far was simply running the defragger from time to time.  Also, I've enjoyed playing around in a unix before, using SCO Unix's version of SystemV back in 1992; yes, they actually turned out OSs before morphing into the patent troll we have come to know and hate today.

---

### Post by chrispche on 2009-09-30
Have you had any experience with other flavours of Linux?

---

### Post by mysteriousdarren on 2009-09-30
google aps?

---

### Post by ssri on 2009-09-30
> **mysteriousdarren said:**
> google aps?

AFAIK, Endnote does not work with google apps, nor am I aware of any citation manager that is compatible as well.

---

### Post by j7%&lt;RmUg on 2009-09-30
> **ssri said:**
> 
No random freezes or BSODs.


Your one of the lucky few then. =)

---

### Post by GodLikeCreature on 2009-09-30
Quite honestly, I think a lot of what is listed here by the original poster is mostly related to user issues and not the OS...

Having said so, most people know that Kubuntu is unfortunately not the best KDE distro.  There are others like OpenSuse and Mandriva which are much more mature and solid.  I think you should have done a bit of research and start on the right foot.

I am pretty sure most of your claims are down to user issues because I have the exact same PC model and have had not a single issue with Mandriva nor Ubuntu (I have dual boot and have installed other distros just for fun).

More over, it is hard for me to understand why you add claims about OpenOffice incompatibility with MS Office.  OpenOffice is a Sun product, nothing to do with Ubuntu or Linux for that matter.  If you don´t like OO, then I think there must be forums on their site where your complaints will make more sense and perhaps help to improve the product...

On the other hand, have you asked yourself what the compatibility is the other way?  Will your co-workers using MS office be able to open an ".odt" doc, for example?  I feel your claims are a bit unfair.  OpenOffice is a product by itself.  The idea is that you use it instead of MS office, not as a different application to use MS office docs.  In other words, what would make sense is that your whole team turn to OO and work in its native format.  I can assure you that will go smoothly...

Like I was saying, I think some of the inconsistencies and freezes from Kubuntu are legitimate.  To be honest, you would have none of those with Ubuntu, as it is VERY WELL integrated with Gnome, but Debian and KDE don´t get along all that well, and it shows in Kubuntu.  

If you are happy back at Windows, I think that says a lot, and I honestly think you should stay there.  Ubuntu or Linux are by no means perfect (neither is any other OS)but it just makes sense to use what fits your needs best.  For computer people like me, Linux and specially Ubuntu offers so much more than Windows that there is no contest.

About the virus thing you mention, I believe what you are saying is that you have not experienced any virus infestation to your knowledge.  That doesn´t really prove much, to be honest...  But it´s just not about infestation, it´s the whole thing.  Just a few hates...  ;-)

- I hate connecting to the internet and having the connection take about a minute to behave correctly because there is an AV update going on in the background.  
- I hate the performance loss that is implied when an AV is scanning all traffic or harddrive contents.  
- I hate the heavy performance degradation that is experience after you install and uninstall a bunch of things over time.  
- I hate installing an OS that every single release is claimed to have thousands of vulnerabilities.
- I hate that if something doesn´t work, you have no idea what to do about it, and even if you had an idea, chances are you can´t fix it.
- Oh, and quite important...  I would not be able to afford the functionality my machine currently has if I was using propietary software.

Those are just a few high level ideas...

---

### Post by 3rdalbum on 2009-09-30
Freezing = bad RAM. Ubuntu uses more of your RAM as cache than Windows (it's there to be used) so bad RAM is more noticable and more likely to cause crashes than on Windows.

Pulseaudio works perfectly, you just have to configure a program's inputs and outputs.

Suspend and resume work perfectly here.

I don't use KDE, but for the couple of weeks when I tried it I didn't have any problems with audio files. Try Gnome?

It sounds like you would have a better experience on Intrepid; since you're running Windows XP I assume you don't mind using obsolete operating systems.

---

### Post by rafita on 2009-09-30
I think you should have stated at the beginning what kind of scientist you are. I am a mathematician, and it is my experience that the colleagues that have more computing problems are the ones using Windows.

---

### Post by HappyFeet on 2009-09-30
> **ssri said:**
> Furthermore, everything in Windows just works.  All of my laptop drivers are listed on a single webpage from HP, which I downloaded and burned to a cd.

Why is it that people only consider buying computers with windows preinstalled, and not linux? Had you bought one with linux, everything would have worked perfectly. Your argument is weak. But I guess you can't wrap your scientific mind around that concept. 


Secondly, you can run MS office in ubuntu via virtualbox in seamless mode. It runs as if it were natively installed in linux. I don't expect you to understand any of what I said though. Goodbye and good luck.
[IMG]http://www.monkeyboobies.com/gallery/d/801-1/FacePalm.jpg[/IMG]

---

### Post by running_rabbit07 on 2009-09-30
> **ssri said:**
> multimedia experience: horrific out of the box.  Installing mediabuntu was a snap, especially since I've done it before.  However, the rest was poor.  Amarok 2.x was just plain bad, so I had to install 1.4.10.  FLACs did not work with the xine engine due to a regression, so I had to downgrade it to intrepid's version.  MPlayer froze constantly, taking down X along with it until I installed a svn build from a ppa *sigh*

I see you didn't use VLC which works great.

> **ssri said:**
>  when sharing documents from my research group who uses MSOffice 2007, Openoffice rendered data graphs incorrectly.  Thus, it disrupted collaborative projects.  Again, for my interests, this was unacceptable.

Ever noticed that when you open a document from MS Office 2003 in Office 2007, you have the same problem?

> **ssri said:**
> As for why I'm typing this message from windows?  Well, I'm currently writing a grant and I found out that the feature sets of Openoffice and Zotero, in their current state, are unacceptable for this endeavor.

Ever heard of Abiword?

> **ssri said:**
> Furthermore, everything in Windows just works.  All of my laptop drivers are listed on a single webpage from HP, which I downloaded and burned to a cd.  No random freezes or BSODs.  Themeing in winxp is fairly easy after installing a hacked uxtheme.dll.  I kind of grew tired with the constant tinkering I had to do in order to make my kubuntu system work in a fairly reasonable manner.  After booting into my windows partition for the first time in several months, I was amazed at the stability of its environment.  Also, I can enjoy some of the bash_aliases I made when using cygwin.  I still cannot let go of the terminal.  So for now, I'll be staying with Windows.  At least until I get bored with it again and try out something new ;).  Hopefully future editions of (k)ubuntu will fix/improve some of the OS-specific issues I listed above, as well as several of the opensource productivity software reaching feature parity with their proprietary counterparts.  

PS.  Before the zealots come in and wish me luck with my future virus infestations, I would like to say that I've ran Windows since 3.1, and have yet to experience any virus infections *knock on wood*.  All it takes is some common sense, a virus scanner, a firewal and, at least in winxp, running the common usage account as a limited user.  As such, the only maintenance issue I've had with windows so far was simply running the defragger from time to time.  Also, I've enjoyed playing around in a unix before, using SCO Unix's version of SystemV back in 1992; yes, they actually turned out OSs before morphing into the patent troll we have come to know and hate today.

If Windows works so well for you, then use it.

(Deleted line being it is obvious the OP has tried to get help. And other people are replying to the beginning of the thread instead of reading the whole thing.)

BTW, Are we not all scientists here? Why add that to your title?

---

### Post by HappyFeet on 2009-09-30
> **running_rabbit07 said:**
> 
BTW, Are we not all scientists here? Why add that to your title?

Perhaps he feels that stating he is a scientist will add clout to his post.

---

### Post by ssri on 2009-09-30
> **HappyFeet said:**
> Why is it that people only consider buying computers with windows preinstalled, and not linux? Had you bought one with linux, everything would have worked perfectly. Your argument is weak. But I guess you can't wrap your scientific mind around that concept. 


Secondly, you can run MS office in ubuntu via virtualbox in seamless mode. It runs as if it were natively installed in linux. I don't expect you to understand any of what I said though. Goodbye and good luck.

Yawn, I ran vbox 3.0.6 here with winxp sp3 and msoffice 2003.  I just did not like the performance hit from running two operating systems at the same time.  Since I was using msoffice 2003 more and more in vbox, I figured why suffer the performance hit?  I'm sorry, but your assumption does not hold water.

---

### Post by ssri on 2009-09-30
> **HappyFeet said:**
> Perhaps he feels that stating he is a scientist will add clout to his post.

No, to provide life scientists, like myself, a single perspective on running kubuntu as the main OS while trying to write grants and publications.  They are my opinions, so you can take it or leave it.

---

### Post by HappyFeet on 2009-09-30
> **ssri said:**
> Yawn, I ran vbox 3.0.6 here with winxp sp3 and msoffice 2003.  I just did not like the performance hit from running two operating systems at the same time.

I can run 3 OS's with no performance hit. As a matter of fact, I could guarantee you would not even know you were using windows inside of linux. (with guest additions, you can have true full screen and not even see the linux part) If you were having performance issues, it speaks for *your* hardware. I have no such issues.

---

### Post by ssri on 2009-09-30
> **running_rabbit07 said:**
> I see you didn't use VLC which works great.

I use vlc, but it comes up short with other programs, like opensource sopcast (see the discussion I had with the author)


> **running_rabbit07 said:**
> Ever noticed that when you open a document from MS Office 2003 in Office 2007, you have the same problem?

I do not use msoffice 2007, nor do I feel the need to when msoffice 2003 works perfectly fine.  Docx and xlsx files open up fine in msoffice 2003 after installing FileFormatConverters.exe

> **running_rabbit07 said:**
> Ever heard of Abiword?

Getting further away from having an editor with an appropriate citation manager for the myriad of different journal formats in the life sciences field.



> **running_rabbit07 said:**
> If Windows works so well for you, then use it and quit trolling here.

Trolling would be if I simply denounced linux outright without offering any reasons whatsoever.  Nowhere did I say or imply that.  I just offered reasons why 

> **running_rabbit07 said:**
> Most of your problems have a workaround, yet I doubt you started many threads asking for advice to find them.

I opened up a thread regarding the suspend/response issue, where it garnered little or no replies.  I've chatted with the devs on some of them.  I've opened up bugs in bugs.kde.org over usability issues, some of which were fixed.  Please do not think that I did not do my due diligence in trying to solve some of the problems I had.  Furthermore, I helped out many others with their ATI issues, and even posted a howto on playing flacs with amarok 1.4.10 in Jaunty.  Still, I do not think that the content or tenor of my OP is approaching anywhere near of it being labeled as trolling.     

> **running_rabbit07 said:**
> BTW, Are we not all scientists here? Why add that to your title?

I meant scientist by training, of which I know that many are here.  I just want add an additional perspective from a life scientist.  No more, no less.

---

### Post by ssri on 2009-09-30
> **HappyFeet said:**
> I can run 3 OS's with no performance hit. As a matter of fact, I could guarantee you would not even know you were using windows inside of linux. (with guest additions, you can have true full screen and not even see the linux part) If you were having performance issues, it speaks for *your* hardware. I have no such issues.

I had guest additions installed correctly, ran in seamless mode, etc, etc.  I guess my 2-year old core2duo laptop is not up to the task.  I'm glad to see that the Worksforme(tm) solution is alive and well. ;)

---

### Post by HappyFeet on 2009-09-30
> **ssri said:**
> I had guest additions installed correctly, ran in seamless mode, etc, etc.  I guess my 2-year old core2duo laptop is not up to the task.  I'm glad to see that the Worksforme(tm) solution is alive and well. ;)

I also see the "it doesn't work for me, therefore is no good" attitude is alive and well also. Btw, sopcast works for me. There is a .deb that makes installation very easy.

---

### Post by ssri on 2009-09-30
> **HappyFeet said:**
> I also see the "it doesn't work for me, therefore is no good" attitude is alive and well also. Btw, sopcast works for me. There is a .deb that makes installation very easy.

I never said the software was no good.  It just was not suitable for my purposes, which is not the same for many others out there.  I compiled  sopcast from source one time and installed it by deb at another.  It worked fine with vlc 0.9.8 and 0.9.9a, but not with 1.0.x.  I had a discussion with its dev in the sopcast thread regarding some problems with sopcast and vlc 1.0.x.

---

### Post by running_rabbit07 on 2009-09-30
> **ssri said:**
> Yawn, I ran vbox 3.0.6 here with winxp sp3 and msoffice 2003.  I just did not like the performance hit from running two operating systems at the same time.  Since I was using msoffice 2003 more and more in vbox, I figured why suffer the performance hit?  I'm sorry, but your assumption does not hold water.

Kinda funny being most anti-virus programs eat more ram and CPU than running VBox. Just my observation. When you have to wait 30 minutes after turning the machine on everyday because of Windows Updates and Anti-virus Updates, then you have to wait on the initial startup virus scan to finish. During that time I can write a paper and check my email and maybe even enter a few posts on UF on Ubuntu.

It is sad when I was running Windows XP, I felt the need to turn my system on when I got up to snooze the alram clock, that way by the time I made it to the system, it was ready to work.

---

### Post by ssri on 2009-09-30
> **running_rabbit07 said:**
> Kinda funny being most anti-virus programs eat more ram and CPU than running VBox. Just my observation. When you have to wait 30 minutes after turning the machine on everyday because of Windows Updates and Anti-virus Updates, then you have to wait on the initial startup virus scan to finish. During that time I can write a paper and check my email and maybe even enter a few posts on UF on Ubuntu.

I setup my vbox to run with 1.2G of memory, which is necessary when having photoshop, word and excel opened up all of the time (CPU ramps up to 60-79C).  So, on my machine, I can safely say that vbox eats up more CPU and RAM than my virus scanner (~19M). 

I never had that happen to me (long startups), which does not eliminate the possibility that it happens to others.  I'm sorry that you had to go through with that though.  Even more sorry if it was Norton AV that did it.  

On my system, there is a discernible performance hit when running vbox within kubuntu jaunty.  As for Windows, maybe it helped that I immediately wiped any windows install that comes with my computer.  Also, maybe it helped that I used nlite to remove all of the cruft when making my Windows install CD from an XP Pro CD I have lying around.  In fact, it boots just as fast, if not faster, than my Kubuntu install.  Granted I still use ext3 on my kubuntu boot partition for stability purposes.  All in all, it takes quite a bit of tinkering in order to get a lean, fast system that *I* like.  Unfortunately, I tinker kubuntu a little bit more (performance-wise) to get it to a state that I'm semi-satisfied with.

---

### Post by Tibuda on 2009-09-30
> **ssri said:**
> In addition, I had to resort to using **foxit in wine** in order to read and markup scientific papers due to lack of column recognition/support ([https://bugs.kde.org/show_bug.cgi?id=161324](https://bugs.kde.org/show_bug.cgi?id=161324)), a problem that is exacerbated by the rude maintainer, and the fact that acrobat-gtk is extremely sluggish in a qt environment, duh.
Have you tried [Foxit Reader Linux version]("http://www.foxitsoftware.com/pdf/desklinux/") before using wine?

---

### Post by ssri on 2009-09-30
> **danielrmt said:**
> Have you tried [Foxit Reader Linux version]("http://www.foxitsoftware.com/pdf/desklinux/") before using wine?

I tried it, but its markup features severely lag behind its windows counterpart.

---

### Post by Chronon on 2009-09-30
I'm really surprised that you use an office suite for publication.  I guess this is maybe a difference between physical sciences and life sciences?  I consider LaTeX and Jabref to be a great combination for writing.  Jabref does a great job at maintaining a database of my citations even offering fast \cite{bibtex-key} copy/paste into my document.

At least you have the freedom to use this combination in Windows too if you so choose.  Portability is often a nice side effect of free software, don't you agree?

---

### Post by lykwydchykyn on 2009-09-30
Other than writing grants, were there any work-specific things you tried on it?  Just curious.

---

### Post by Tamlynmac on 2009-09-30
[> ]("http://ubuntuforums.org/member.php?u=335139")[HappyFeet]("http://ubuntuforums.org/member.php?u=335139")
 	Quote:
 	 	 		 			 				 					Originally Posted by **running_rabbit07** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8031139#post8031139") 				
 				*BTW, Are we not all scientists here? Why add that to your title?*
 			 		 	 	 
Perhaps he feels that stating he is a scientist will add clout to his post.

Yawn...

Why do you think that was put in the title?

IMHO
One should always question the motives of anyone who would attempt a comparison without predefined objectives and under controlled conditions with appropriately designed systems. Benchmarks anyone....

The observations presented by the OP are fundamentally nothing more than their opinion and shouldn't carry anymore weight than others. Regardless of title.

Yawn.... Excuse me while I unsubscribe.

Just my $0.02

---

### Post by running_rabbit07 on 2009-09-30
> **Tamlynmac said:**
> [url="http://ubuntuforums.org/member.php?u=335139"]

Yawn...

Why do you think that was put in the title?

IMHO
One should always question the motives of anyone who would attempt a comparison without predefined objectives and under controlled conditions with appropriately designed systems. Benchmarks anyone....

The observations presented by the OP are fundamentally nothing more than their opinion and shouldn't carry anymore weight than others. Regardless of title.

Yawn.... Excuse me while I unsubscribe.

Just my $0.02

Darn, now I am yawning.

---

### Post by dave WB3DWE on 2009-10-01
[SIZE=3][FONT=Lucida Sans Unicode]I'm glad you've never had a virus. I said the same thing until five weeks ago.  Despite one of the top three Windows security programs, which I had just updated 2 months previously, a root-key malware got through from a college bulletin board.[/FONT][/SIZE]
[SIZE=3][FONT=Lucida Sans Unicode]My system has never been the same. I admit I was complacent and had not backed-up.  A technician said the disk
was unsalvagable. I bought a new drive and reinstalled XP.
This was the first time in 25 years of computing, but it takes only one shot to kill you.
Most shocking was the cavalier attitude of the IT department.
At first they claimed their "blackboard" was clean. One of them admitted they had the same malware on their laptop. The head of the dept. refused to shut down the system.
My son, a computer programmer, uses Linux/Unix and has never had such a problem on his systems. I've installed Ubuntu as dual boot. Now I do most of my Internet communication with Firefox on Ubuntu.
[/FONT][/SIZE]

---

### Post by tgalati4 on 2009-10-01
The OP's opinions are valid.  Work productivity in Linux with a mixed Windows environment is a challenge.

I'm sure the granting institutions are Window's centric and therefore have windows-specific templates to follow.  These would be difficult to replicate in OpenOffice.

OpenOffice doesn't have the markup/collaboration tools that MS Office 2007 has.  If you have to work in that environment, then it's difficult to replace that functionality.  If you are in an all-Linux shop, then the point is moot because you would be using markup wikis or other collaborative tools.  You would get the job done, but with a different set of tools.

Zotero is a great tool and it's improving all the time.  I hope the OP will provide feedback to the zotero folks for what is missing.

Also, try Koala for the next year and post again.  I would be interested in how things will change over the next year.

---

### Post by mdsmedia on 2009-10-01
> **tgalati4 said:**
> The OP's opinions are valid.  Work productivity in Linux with a mixed Windows environment is a challenge.

I'm sure the granting institutions are Window's centric and therefore have windows-specific templates to follow.  These would be difficult to replicate in OpenOffice.

OpenOffice doesn't have the markup/collaboration tools that MS Office 2007 has.  If you have to work in that environment, then it's difficult to replace that functionality.  If you are in an all-Linux shop, then the point is moot because you would be using markup wikis or other collaborative tools.  You would get the job done, but with a different set of tools.

Zotero is a great tool and it's improving all the time.  I hope the OP will provide feedback to the zotero folks for what is missing.

Also, try Koala for the next year and post again.  I would be interested in how things will change over the next year.
Nicely put, and agree almost 100%. A mixed Windows shop, with reliance on Windows-based software, with a single Linux machine trying to collaborate, indeed throws up challenges.

I believe it's not Linux throwing up the challenges, but the reliance on Windows based tools. The catch-22 lock in.

---

### Post by moe_syzlak on 2009-10-01
ssri, you have to understand that fanbois are very present on these forums. Some of these forums users on here may be even 14 years old. You never know. And like any other forum on the internet, DO NOT FEED THE TROLLS. It's best to walk away and be a bigger person.

Okay now on to your issues of Office 2007 interoperability with Open Office, suspend resume, and freezing issues.

First the Office 2007 issue. Open Office 3.x is mostly compatible with MS Office 2007. The file format the 2007 uses is SUPPOSED TO BE OOXML ([http://en.wikipedia.org/wiki/Office_Open_XML](http://en.wikipedia.org/wiki/Office_Open_XML)). OOXML is an open format for office documents, in the same category as ODF (odt, odf, odp, etc), but some people say that OOXML is inferior to ODF. Microsoft published Office 2007 before the OOXML standard was defined. So, OOo is not compatible with MS' version of OOXML (an open standard). OOo is only partly compatible with MS' version of OOXML. However, OOo is nearly 100% compatible with Office 2003 file formats like .doc, .xls, and .ppt. Microsoft Office 2007 uses .docx, .xlsx, and .pptx -- OOXML-ish file formats.

So by Microsoft publishing it's flagship software, MS Office 2007, before the OOXML standard became official, Microsoft was able to smite and gain a lead on Open Office, in the realm of OOXML. By doing so, MS would NOT have to be bound by the same standard, OOXML, that it is a major franchiser of. Microsoft was one of the main backers of OOXML, then it pulled a fast one and now you're here, and leaving OOo (and its users) out to dry in terms of OOXML (MS version) file format compatibility with Office 2007.

Novell has an edition of OOo that is MORE compatible with Office 2007 than OOo in terms of it's OOXML (MS version), and Novell claims that it's borderline on par with the document rendering with MS Office '07. Novell calls it "OpenOffice.org Novell Edition." Here is a quote I pulled from the information site abot SLED. Novell even includes commons MS fonts like Calibri to aide with compatibility.

***The Novell Edition of OpenOffice.org is based on the latest version of the community project&#8212;OpenOffice.org 3.0&#8212;with significant enhancements. In the Novell Edition, you get a host of leading productivity features not found in the upstream project. It comes with improved compatibility with Microsoft Excel, stronger Visual Basic macro support, and richer file import capabilities (e.g., ability to read Microsoft Works, WordPerfect, and scalable vector graphics files). The Novell Edition also supports built-in 3D transitions in slide presentations and stronger forms support.***

Link for above quote is here, [http://www.novell.com/products/desktop/features/ooo.html](http://www.novell.com/products/desktop/features/ooo.html) .

If you all know your Linux history, SUSE (prior) to being bought by Novell is one of the top Linux OS makers. It's right after Red Hat (aka "BIG LINUX") on the Linux time line, according to Stallman's **Revolution OS** documentary. So, I think Novell can be trusted when they make a claim.

Now your second problem, suspend resume. Ubuntu boots in less than 25 seconds on my year 2004 computer (the one I'm on now). XP took a little over like 3 minutes, and sometimes longer if the virus scanner starts up, on this same computer. And Karmic Koala is supposed to have even faster boot times. My year 2007 laptop running vista takes a little bit less than 20 seconds to come back from resume, and that's a fast machine. The reason I'm on the family computer now and not my laptop is because the cheap ram I put in my laptop is now corrupt and I need to buy some new sticks of 2GBx2 :( Until then, I'll be on the slow family computer. The family comp was so slow with XP that I had to install Ubuntu on it. So just because your computer can't suspend/resume doesn't mean despair on Linux, that just means you can start up faster than in 'doze.

For applications, GNOME (and KDE) can remember what programs and documents you had open when you shutdown. So, the next time you fast boot, you will have your desktop pretty much like you had it before reboot. I think GNOME calls that "remember sessions" or something similar to that. KDE has the technology too, the last time I checked.

Your third problem, freezing issues. That is most likely caused by your graphics card. The graphics cards on laptops are different than on desktops. The g-cards in lappies were modified radically to make them fit the power consumption profile of a notebook, and it had to be retrofitted to the laptops body. All of that required changes that affect the laptops ability to use the drivers, even directly from ATI/Nvidia. I would disable 3D driver modules in order to have a working system. Without graphics card support, you can still have some eye-candy in Ubuntu, but your CPU must be able to take the load. I recommend a fresh vanilla install of Ubuntu. No offense to you, but n00bs should not be fiddling around with the internals of a stable desktop / "work machine." Do that on an "beta machine."

Many various compatibility issues can be solved simply by using a distro like SLED, or Mandriva. I don't mean the free versions like openSUSE or Mandriva One, I'm talking "Big Linux." Novell has a program where you can try SLED for six months for free. Believe me, there is a quality difference between "free as in beer" and "free as in speech" Linux. Trolls may disagree, but I don't care.

Nonetheless my friend, I wish you well on your journeys with Linux. Some people leave, but they all come back. If you leave know I know you'll be back sooner or later. It's the lure of Linux -- "catnip for nerdz."

---

### Post by moe_syzlak on 2009-10-01
It's great to see a scientist using Linux. I plan on being a doctor one day. Right now I'm 1st year nursing student.

---

### Post by mdsmedia on 2009-10-01
> **moe_syzlak said:**
> snip
I have to assume you are serious with that post.

---

### Post by darrenn on 2009-10-01
> 
audio: check (after ripping out the horrendous pulseaudio that came with medibuntu and reinstalling alsa)

video: check (after downgrading to xserver 1.5.2 and installing catalyst 9.3)

compositing: check (after installing compatible proprietary drivers for my card. The opensource ati drivers that came with jaunty, or the ones checked out from git, had redraw bugs when moving menus around, unacceptable)

suspend/resume: nope (when the weather is right or when I'm feeling lucky. Translation: a crapshoot)

freezing: every once in awhile when playing an audio file. Again, this is unacceptable.

multimedia experience: horrific out of the box. Installing mediabuntu was a snap, especially since I've done it before. However, the rest was poor. Amarok 2.x was just plain bad, so I had to install 1.4.10. FLACs did not work with the xine engine due to a regression, so I had to downgrade it to intrepid's version. MPlayer froze constantly, taking down X along with it until I installed a svn build from a ppa *sigh*


I agree with some of the other poster's. If you had spent five minutes checking to see if your hardware was supported before you installed you wouldn't have had bothered in the first place.

Well we have all learned a valuable lesson. Make sure your hardware is supported before you attempt to install Ubuntu.

---

### Post by ssri on 2009-10-01
> **darrenn said:**
> I agree with some of the other poster's. If you had spent five minutes checking to see if your hardware was supported before you installed you wouldn't have had bothered in the first place.

Well we have all learned a valuable lesson. Make sure your hardware is supported before you attempt to install Ubuntu.

It is quite funny that you neglect the fact that all of my hardware on my 6910p (like with one other poster) is supported out of the box by jaunty.  The question is that is it supported well?  Well enough to serve as a general purpose machine?  Sadly, from my OP, the answer is no.  I had to do quite a bit of tweaking (see my guide on how to play 24-bit FLACs for amarok 1.4.10 in Jaunty for example) that entailed mostly using CLI (apt pinning, mixing intrepid repos, etc) and compiling some programs that I makes my life easier, enough CLI-work to make an ubuntu neophyte's face blanch.  In fact, I mainly use apt to manage my packages, as I prefer its flexibility and control over gui frontends for it.  Furthermore, I complained about the some of the packaging, especially how medibuntu packages are improperly maintained for kubuntu (pulseaudio, hello?).  After all of that work, Kubuntu Jaunty became a very nice general purpose/light work machine.  However, in my profession (mainly in my discipline), publish or perish is the law of the land, and, in my situation, when the rubber met the road, Kubuntu was not equipped to handle it.  However, that does not negate that Kubuntu served as a nice system for everyday use.  

As long as powerplay and TV-out worked for my ATI x2300 (which they don't in the current opensource drivers), I am happy.  That is why I had to rip some of the guts out from Jaunty's default install, such as downgrading X-server to Intrepid's version and installing the ATI's legacy proprietary driver for my graphics chip.  This did not cause any additional instability, as I suffered from far more X session freezes when using the opensource drivers.  Again, it takes quite a bit of tweaking, far beyond what a neophyte can handle, in order to get a system that I can happily use.  However, like I said, in the business end of things for my profession, Kubuntu in its current state just falls short.      

As for the poster who recommended Novell's openoffice implementation, thanks.  I'll try it in a few weeks after the grant submission deadline.

---

### Post by jperez on 2009-10-02
ssri, don't mind the real trolls, the elitist on these forums.  Making legitimate complaints about your experience while still showing that you got some things to work with a little elbow grease shows you tried.  Like the good people of Linux say, "Linux isn't for everyone."

Look at my signature.  I use Windows on my PC, Ubuntu on my laptop and, as of about a week ago, own a Mac.  I also have a Linux-powered Internet Tablet. :p

Anyway, you have some good points.  Using Kubuntu Jaunty, I couldn't go into Suspend/Hibernate without going to a black screen and it just staying there.  It was not nice.  Luckily, Ubuntu (not Kunutu) Karmic fixed that for me. :)  So I know about your type of issue since I had it.  I can't really speak on the OOo issue as I don't use that for work.  I wish I could have used it for college, but they were specific about what I had to use, which was MSO2007.  So, I know that it can be frustrating when it comes to program file format interchangeability and compatibility.  Sometimes, you are left with no choice.

I know the horrors of all three systems that I own, Windows, Mac and Linux.  Windows I've been using for 14 years, since the days of Win3.11 WFW and this was when I was 9.  I know the ins and outs of the OS and it can be a pain and I'm sure you know that too.  Mac can be flaky at times, but as I recently found out, since I was a Mac hater with no real reason, it's a decent enough system.  There are places where it can use improvement, but it's good for what it can excel at.  Linux is the same.  There are some things that Linux can't excel at and other things it can.  Other times, Linux will break due to a simple user mistake and then frustration and anger will ensue, but that's not to say that the other two systems don't suffer from the same problem.

Now, I'm sure by now that some of you zealots are thinking I'm a Windows fan, but in reality, I'm not.  I root for my champion, Linux, even though I'm a lot more versed in fixing a Windows machine.  Why?  Years more experience with that OS as opposed to Linux, only having learned about it a few years ago and actively using it only about 2 years ago.  I have my issues with Linux, but I also have my issues with Mac and Windows.  No one is excluded.

Anyway, moe_syzlak said that Karmic claims a faster boot time, which I can attest is true.  My laptop, prior to Karmic, running Kubuntu Jaunty, booted up at a "decent" speed, but nothing noticeably faster than when I had Vista installed on this machine.  Mind you, Intrepid was faster, but I must say that Karmic REALLY impressed me here.  The boot time was, at most, 10 seconds from the GURB text to the login screen, which makes me very happy.  Keep in mind, on my PC, it would probably be almost instant.  Here's what I'm running on my laptop for specs to gain a good understanding of the boot speed:

CPU: Pentium Dual Core 1.6Ghz (not Core 2 Duo)
RAM: 1GB
Graphics: Intel GM965/GL960 Integrated Graphics Controller

Now look at my graphics card.  As you can tell, my experience with (K)ubuntu (yes, both desktops) was degraded even with the workarounds mentioned in Jaunty as opposed to Intrepid and now Karmic.  Karmic, I think, will turn the tables for quite a few user that had issues with the OS itself in terms things that stopped working/got broken with the arrival of Jaunty.  That's just mentioning the OS itself.

I believe you when you say that you asked for help yet either few people or no one helped you out.  Unfortunately, some of the "pros" around here are too busy bashing others or working on something that they usually don't help those looking for it.  Mind you, not everyone is like that.  I have received help and so has my girlfriend when she was installing Ubuntu on an external USB hard drive.  All got sorted out and she's happily working on her new Ubuntu laptop and her Windows PC.  Her and I are gamers, so it's hard to let go of Windows when your favorite games don't work under Linux, even with WINE/Cedega/CrossOver.  I know, I've checked and even tried them myself.

Anyway, this post has gotten much longer than I wanted, but I wanted to provide my point of view here.  I hope your endeavors are fruitful and even if Linux isn't for you, I at least wish you luck in your career and with everything you do.  As for me, I have more bugs to find and more crashes to take care of in Karmic and Windows. :lolflag:

Have a good one ssri! :D

---

### Post by fela on 2009-10-02
Every human is a scientist in his or her own way.

It's part of being human, and for me it's pretty much what constitutes being human: making sense of the world around you in a rational manner (and sometimes irrational).

Back to reality, most of your arguments about windows 'just working' don't add up.

Why is it that openoffice breaks up your workflow? Because everyone forces you to use MS office. I betcha if everyone was running openoffice and you wanted to use MS office, you'd have a very hard time. Also what has openoffice got to do with Linux? They're two totally different things (and openoffice is but one of many office suites for Linux).

And the fact that you mention a hardware issue amongst all of this just proves that you were just trying to find valid points - and often failing. How is it Linux's fault if your RAM is dud? Go get yourself some working RAM, make sure it works, then blame Linux when it freezes.

I'm not gonna bother remembering what all the other so called arguments were.

EDIT: I agree that Linux certainly isn't for everyone, but your arguments just don't make sense.

---

### Post by running_rabbit07 on 2009-10-02
> **jperez said:**
> I couldn't go into Suspend/Hibernate without going to a black screen and it just staying there.

Never had a problem with Suspend in any version of Ubuntu and I only had a problem with hibernating when I didn't have a Swap partition.

---

### Post by darrenn on 2009-10-02
> After all of that work, Kubuntu Jaunty became a very nice general purpose/light work machine. However, in my profession (mainly in my discipline), publish or perish is the law of the land, and, in my situation, when the rubber met the road, Kubuntu was not equipped to handle it. However, that does not negate that Kubuntu served as a nice system for everyday use.

I hope that one day Kubuntu will meet the needs for your profession. It's good to hear that at least it's good enough for everyday use.

---

### Post by jperez on 2009-10-02
> **running_rabbit07 said:**
> Never had a problem with Suspend in any version of Ubuntu and I only had a problem with hibernating when I didn't have a Swap partition.

I have a swap partition (straight default installation with extended and swap partitions included) and I had issues, but hey, not everyone's computer is ideal for *buntu nor does everyone's computer run perfectly even with some fixes. ;)

It's the same with Windows PC's and so on.  Only saying that was my experience.  It didn't make me quit using Linux.  Far from it.  Not only am I typing this on the same laptop with Ubuntu, but I'm still saying Linux is my champ above Windows and Mac. :mrgreen:

So, not everyone will be able to run *buntu perfectly, but we all have our reasons for going back to/staying while using Windows.  I still use it for some games and programs I can't run on Linux even with all three major WINE-related projects (WINE being one of them).  Now, virtualization would not be an option on this laptop as it's too slow for it and I know because I've tried, but again, not everyone's system, unlike HappyFeet, aren't perfect and can run everything all at once.  I just get by.  Still, I don't need all those things running on my laptop as many of the programs I do use on my PC I use with a mouse and keyboard combo and don't really have the real need to connect a mouse to my laptop when the touchpad works fine for everyday use.

My whole point was not to strike him down so quickly.  Hey, if Windows works for him and he did try to get Kubuntu working properly (which he did; check his list again), then that's fine.  Last time I checked, using Linux, or any OS for that matter, was a choice.  Flaming someone for making a choice of operating systems they are using/going to use/have a better experience using/etc., is no reason to call them a troll.  He made his point, told his story, gave his reasons and that's that.  The least we can do is tell him "Sorry that you couldn't get it to work, but I hope in the near future it will be a more viable option for you" and the most we can do is help him as best we can.

If Linux is community driven, going by this thread alone, it has some issues that needs addressing.  So please, don't flame.  It's not right and it's not warranted. :)

If this thread offends you, please don't read or reply to it.  It's as simple as just pressing the back button and going to a new thread.  ;)

Jesse~

---

### Post by running_rabbit07 on 2009-10-02
> **jperez said:**
>  Now, virtualization would not be an option on this laptop as it's too slow for it and I know because I've tried, but again, not everyone's system, unlike HappyFeet, aren't perfect and can run everything all at once. 

Virtualization can be an issue. I have a slow CPU but I have added RAM to get me up to 2 Gigs which is needed to happily run VBox.

> **jperez said:**
> If Linux is community driven, going by this thread alone, it has some issues that needs addressing.  So please, don't flame.  It's not right and it's not warranted. :)

If this thread offends you, please don't read or reply to it.  It's as simple as just pressing the back button and going to a new thread.  ;)

Jesse~

I am not sure this last part was aimed at me, but I'll throw in 2 pennies just in case. This thread does not offend me. After a few posts, I have seen that the OP did do his homework, unlike many people who decide to quit before trying.

In your first post you said do not feed the trolls, yet by judging that people are offended by the OP's post and that being they replied, you are calling them trolls.

---

### Post by ssri on 2009-10-02
> **fela said:**
> How is it Linux's fault if your RAM is dud? Go get yourself some working RAM, make sure it works, then blame Linux when it freezes.

EDIT: I agree that Linux certainly isn't for everyone, but your arguments just don't make sense.

I ran Memtest86+ overnight when these problems manifested themselves, with no errors found.  Sorry, your assumption does not hold up.  I wonder why a few of you try to prop that up or use it as a basis of your critiques.  To clarify, kde 4.1.2 (intrepid) had freezing problems and kde 4.2.x (intrepid) did not for several months.  However, the freezing problems returned with kde 4.3.x (jaunty).  On a side note, there were QT regressions I've found and posted on bugs.kde.org.  Am I angry for this?  Not really, as the mods on forums.kde.org have been understanding and helpful in trying to sort these problems out.  There is a level of civility there that is lacking with some, not all, of the posters here.  However, I digress.  Anyways, regardless of the null result from running memtest, the pattern does not hold up with it being defective RAM.  I've seen freezing and BSODs from bad RAM on different laptops I've owned, and it happens quite suddenly.  Windows is certainly not immune to this problem, as I have seen it before and diagnosed quickly.  No big deal, as I have lifetime warranties on those kingston sticks.  Nothing I've experienced (and proved) with Jaunty would suggest that it was bad memory that led to the freezing issue.  Thanks for relying on that trope though.

Also, I've been following lkml, and it seems Linus declared that suspend/resume issues should be cleared up by 2.6.30 (or 2.6.31?).  I would test it, however I will have to compile the opensource radeon drivers, which are not where I want them to be just yet IMHO.  Still, the devs have been busy for the past several months, and new features are being added constantly.  Here's hoping for OpenGL 2, GLSL, powerplay and TV-out (proper) support in the near future.  From my posts here, I've complimented Jaunty for quite a few things.  In fact, listing all of the things I like about Kubuntu (i.e. dolphin) would be too long to list.  However, some of the posters here do not seem to understand or comprehend that Jaunty was not the end all be all for one person, and thus brought their tired cliches (noob, worksforme, bad hardware, etc) to the fore without parsing through my post.

---

### Post by jperez on 2009-10-02
For a guy without much money at the moment, I can't afford more RAM for this dinky laptop of mine, but one day, I will.  Still, who knows, I may try my luck again with some other programs when VBox a little more mature than it already is.

Also, not really pointed at you, but at anyone bashing on him or calling on him a troll just for expressing his views in general.  Mind you, although you did call him a troll, I can say that yes, you did see that he did try and are now contributing in a more constructive way.  Thus, my comment isn't really that much pointed at you as it is towards the others.  Anyone offended by this thread (or at least the first post and come in here to flame him without helping in any way) and posts negatively and critically without helping is indeed a troll, but not those that offer real points, valid arguments and the such.  This topic does not offend you, you offered your opinion, maybe a little harshly, but all in all, it could have been worse.  The simple fact that you're conversing with me about this and offering good points and showing you'd like to help him if he asks for it means you are in fact a good poster and my comment, again, is not really aimed at you.

Hope you didn't take what I said in the wrong way. :)

To the OP, again, take a look at some of the suggestions (if you haven't already) from other posters and see if they can help you a little more with your issues.  I can't say you'll find everything you need in Ubuntu, but then again, not everyone can.  Good luck though.

Jesse~

---

### Post by ssri on 2009-10-02
> **fela said:**
> Why is it that openoffice breaks up your workflow? Because everyone forces you to use MS office. I betcha if everyone was running openoffice and you wanted to use MS office, you'd have a very hard time. Also what has openoffice got to do with Linux? They're two totally different things (and openoffice is but one of many office suites for Linux).

Sorry, but when I'm collaborating with three different research teams that span three different universities, it is difficult to stand up and tell them to use openoffice when they and their other collaborators in non-related projects use MSOffice.  For swapping simple spreadsheet data, openoffice is fine.  However, the mixed ecosystem falters when trying to create publication quality figures or track manuscript changes, as one other poster alluded to earlier.  When MSOffice is already the de facto standard in the life sciences field, especially with the groups I collaborate with, then outside of very compelling reasons it is very hard for them to change.  I'm sorry, but openoffice being free is not one of them since our grants often cover software expenditures, especially office productivity software.

---

### Post by running_rabbit07 on 2009-10-02
> **jperez said:**
> Lots-a-words.

I agree, and I think the OP knows what route he wants to take to get around his problems. I updated my RAM right before deciding to give Linux a try. Now, if I didn't extensively use VBox to test Ubuntu and Xubuntu Karmic along with MS XP Pro and Debian Lenny, I'd be able to get away with 1 gig of RAM easily. The only other program that pushes me over using 1 gig is Google Earth, which I haven't reinstalled yet. 
I prefer to help people (when I can) and wish I seen a lot of the people that claim to be on their way out of the door in a help thread instead flaming Ubuntu, such as the one you and I have both posted in with his DVD burner issues. He never asked for help, but instead, siad Ubuntu isn't ready for the desktop, then he got mad at a Mod for moving his thread.

---

### Post by jperez on 2009-10-03
> **running_rabbit07 said:**
> I agree, and I think the OP knows what route he wants to take to get around his problems. I updated my RAM right before deciding to give Linux a try. Now, if I didn't extensively use VBox to test Ubuntu and Xubuntu Karmic along with MS XP Pro and Debian Lenny, I'd be able to get away with 1 gig of RAM easily. The only other program that pushes me over using 1 gig is Google Earth, which I haven't reinstalled yet. 
I prefer to help people (when I can) and wish I seen a lot of the e people that claim to be on their way out of the door in a help thread instead flaming Ubuntu, such as the one you and I have both posted in with his DVD burner issues. He never asked for help, but instead, siad Ubuntu isn't ready for the desktop, then he got mad at a Mod for moving his thread.

Lots-a-words :lolflag:

That truly made my night.

Anyway, aside from that, I might try some of your suggestions when I have a little more money to spend.  Thanks for the hearty tip. ;)

And I agree with you on the OP of the DVD burner issue.  Hopefully my newest post will help straighten things out and help him out a bit so we can help him.

Jesse~

---

### Post by Jerold on 2009-10-03
Just a comment about everything just works in Windows. I have a Vista notebook for work that came with factory pre-installed OS. From the factory my computer would BSOD every time the screensaver would activate. I cannot use suspend at all because most of the time it crashes when I attempt to awake the computer. 

Out of the box, my computer took 140 seconds to boot until I started removing preinstalled demo-ware. Now it will boot just under 50 seconds. Explorer crashes almost daily. Other colleagues experience similar issues. Rebooting daily is absolutely necessary. 

I still continue to blue screen and I know where the problem lie, but the manufacture has tweaked the hardware just enough where I cannot use OEM chipset drivers. I must go through Sony. They have assured me that there is not a problem with any of the drivers even though Microsoft sends me crash reports pointing out which drivers are out of date and defective. 

While I find the translation with OpenOffice fairly good, I have never seen perfect conversions between two different file formats with any competing products. Heck, I even see formatting problems when loading older files with newer version of Office. If you save a document in Word with any complexity in a different format you will see problems when viewing with the native application. I know that doesn't help your collaboration efforts, but at least realize that interoperability between application is difficult especially when Microsoft only has a motive to hold on to their monopoly.
 

 I know that Linux gets a lot of flack for driver support; however, realize that you have to choose hardware and chip sets where the manufactures make some effort to support an operating system.


(Lets not mention worms, spyware, security, disk fragmentation and viruses.)



You have to choose the right tools for the job. For me, my personal Ubuntu system can accomplish immensely more that a Windows OS can accomplish with fewer resources and greater stability. And that includes running multiple virtual Windows machines.

---

### Post by solwic on 2009-10-03
@OP:

1)  Ignore the people calling you a "troll".  That's just their insecurities leaking through (the thought that someone might not like Ubuntu kills them).

2)  It's Kubuntu.  You can't expect much.  

3)  Use what works.  I know that sounds like a cop out, but really, what can we do?  I appreciate that you took the time to report your experience, but all you can do is file bug reports, find the solutions to the issues, or use a different OS.  While I understand the frustration of wanting to use Ubuntu and not being able to (I was here for the pre 8.04 days...back then, it was ugly), there comes a point when you simply have to decide which you want to do:  fix Ubuntu to your standards, or go to Windows or OS X.  

4)  Good luck, whatever you decide.  :biggrin:

---

### Post by jrothwell97 on 2009-10-04
> **running_rabbit07 said:**
> I see you didn't use VLC which works great.
To me, the OP's issue sounds like a driver problem and not a problem with VLC.

> **running_rabbit07 said:**
> Ever noticed that when you open a document from MS Office 2003 in Office 2007, you have the same problem?
Nonsense. MS made a special effort to make Office 2007 work with 2003, and it works very well - although the .doc and .docx formats are incompatible and there are a couple of quirks, OpenOffice.org's handling of other file formats is *far* worse.

> **running_rabbit07 said:**
> Ever heard of Abiword?
> **ssri said:**
> As for why I'm typing this message from windows?  Well, I'm currently writing a grant and I **found out that the feature sets of Openoffice and Zotero, in their current state, are unacceptable for this task**.
If OpenOffice.org doesn't have the feature set the OP requires, how the hell will AbiWord?

> **running_rabbit07 said:**
> If Windows works so well for you, then use it and quit trolling here.
The OP was not trolling, but was using the forum for its required purpose: that is, posting about his (or her) experiences with Ubuntu. S/he had a negative experience: **it is still an experience**.

> **running_rabbit07 said:**
> Most of your problems have a workaround
Apart from OpenOffice.org's incompetence with handling alternate file formats, the pulseaudio/alsa mess, poor drivers, etc. etc.

To the OP: Intrepid was a bad release. Jaunty was better, and Karmic is another improvement, but it appears to me that Ubuntu probably isn't for you at this stage. Sorry to hear about your bad experience.

---

### Post by running_rabbit07 on 2009-10-04
> **jrothwell97 said:**
> To me, the OP's issue sounds like a driver problem and not a problem with VLC.

I was recommending VLC not saying he had a problem with it. What is wrong with offering alternatives?

> **jrothwell97 said:**
> Nonsense. MS made a special effort to make Office 2007 work with 2003, and it works very well - although the .doc and .docx formats are incompatible and there are a couple of quirks, OpenOffice.org's handling of other file formats is *far* worse.

Why did my professor have problems with opening a .doc from 2003 in 2007 then? I have known many people that have had these problems with MS Office.

> **jrothwell97 said:**
> If OpenOffice.org doesn't have the feature set the OP requires, how the hell will AbiWord?

Abiword works better than O.O, for me. Again, is there something wrong with offering alternatives? I don't think I have ever seen you posting in help threads, why is that? You are always criticizing others, yet you do nothing to help?

If you are going to put your 2 cents in, at least do it when the conversation is happening and not days later.

---

### Post by jrothwell97 on 2009-10-04
> **running_rabbit07 said:**
> Why did my professor have problems with opening a .doc from 2003 in 2007 then? I have known many people that have had these problems with MS Office.
As I said, .doc support in 2007 isn't perfect, but it is *far* better than Openoffice.org's support of both complex .doc files and any .docx files.

> **running_rabbit07 said:**
> Abiword works better than O.O, for me. Again, is there something wrong with offering alternatives?

*However...* the fact remains that if OpenOffice.org does not have the feature set the OP requires, AbiWord almost certainly will not.



> **running_rabbit07 said:**
> If you are going to put your 2 cents in, at least do it when the conversation is happening and not days later.

Apologies for reading down the page and not noticing the post time.

> **running_rabbit07 said:**
> I don't think I have ever seen you posting in help threads, why is that?

<snip>

You are always criticizing others, yet you do nothing to help?

*[cough](http://ubuntuforums.org/showthread.php?t=1282347)* *[cough](http://ubuntuforums.org/showthread.php?t=1274494&page=2)* *[cough](http://ubuntuforums.org/showthread.php?t=1259628)*

I help when I can, and I find this comment in particular rather insulting and somewhat hypocritical since in the post I was responding to, you told the OP (before you edited the post in question, which I certainly don't blame you for) to

> quit trolling

Now, if it's all the same with you, I'd rather leave this thread to sink down the forum as dozens of topics appear gushing with praise for Karmic.

---

### Post by running_rabbit07 on 2009-10-04
> **jrothwell97 said:**
> Now, if it's all the same with you, I'd rather leave this thread to sink down the forum as dozens of topics appear gushing with praise for Karmic.

That I agree with.

---

### Post by meho_r on 2009-10-04
> **Chronon said:**
> I'm really surprised that you use an office suite for publication.  I guess this is maybe a difference between physical sciences and life sciences?  I consider LaTeX and Jabref to be a great combination for writing.  Jabref does a great job at maintaining a database of my citations even offering fast \cite{bibtex-key} copy/paste into my document.

At least you have the freedom to use this combination in Windows too if you so choose.  Portability is often a nice side effect of free software, don't you agree?

I second that. 

@OP: You really should consider using LaTeX for your work and [Jabref](http://jabref.sourceforge.net/) or [Mendeley Desktop](http://www.mendeley.com/) for managing your references. MS Office, OpenOffice.org and all other word-processing apps are just little silly toys comparing to LaTeX (not to mention that no matter how careful you are, no matter if you're using styles and advanced features, you'll never get high-quality output with Office suites; that's why many schools, universities... insist on using LaTeX when submitting thesis, dissertations and other material).

As for (K)ubuntu issues, just do as many suggested: try some other distros (starting with Debian which is rock solid and arguably most stable distro out there). So, if you want stability, Debian is a good choice, and Gnome too (much more stable than KDE). If you really want KDE, than try Mandriva or openSUSE (or, of course, Slackware).

---

### Post by Dullstar on 2009-10-04
I must ask - have you tried using Ubuntu (not Kubuntu)?  It works fine for me...
I'm typing this from Windows...  just before closing a bunch of crud, and reaching for the restart button.

---

### Post by HappyFeet on 2009-10-04
Wow. I'm like one of the biggest geeks on earth, i see other people are kinda the same

---

### Post by Lightstar on 2009-10-07
yep... I also have to go to windows for a few things, games and some document formatting...  

But you know, windows is not better, linux is not better, they're both good.  Most of the problems we encounter are caused by companies that decide to do things exclusively for windows, not by linux itself.

If ATI worked on drivers for linux as hard as they do for windows, there would be no ATI video card problems.
If game companies made games for both linux and windows, there would be no wine problems.
If everyone used the same open format for documents, there'd be no formatting problems.

When I'm on the computer for myself, I'm on linux.
When I have to use the computer for other people, I'm often on Windows.

---

### Post by meho_r on 2009-10-08
> **Lightstar said:**
> ...
When I'm on the computer for myself, I'm on linux.
When I have to use the computer for other people, I'm often on Windows.

My condolence :P I guess I'm the lucky one who doesn't need Windows no matter am I using computer for me or for others, at home or at work...

---

### Post by loderunner99 on 2009-10-09
> **ssri said:**
> When MSOffice is already the de facto standard in the life sciences field, especially with the groups I collaborate with, then outside of very compelling reasons it is very hard for them to change.

Windows and MS Office is the defacto standard for world-wide business use, period. This is the biggest hurdle Linux has got to overcome for mainstream uptake.

It's not a case of i'm using Open Office so you are all going to have to switch over to meet my needs. More a case of we are all using MS Office and if you want to keep your job you will use it too and comply with our standards, whether you like it or not.

I think the kids that post and the fanbois don't seem to grasp that point. Wait till you get out of school...

---

### Post by kiranmatrixlee on 2009-10-09
haiiiii

---

