---
title: "Just installed 8.05 - but I need help to install bibles, commentaries, etc..."
date: 2008-11-25
forum: Ubuntu Christian Edition
---

### Post by brjoon1021 on 2008-11-25
I followed the instructions, and I installed e-sword into 1.1.9 Wine. However, I don't know how to add the bible translations, commentaries and all of the things that I want added.

By the way, would it be a huge undertaking to make a Linux compatible application that is LIKE e-sword and would be able to share add-ons, etc... back and forth to avoid this whole Wine thing?

B

---

### Post by david_kt on 2008-11-25
> **brjoon1021 said:**
> I followed the instructions, and I installed e-sword into 1.1.9 Wine. However, I don't know how to add the bible translations, commentaries and all of the things that I want added.

By the way, would it be a huge undertaking to make a Linux compatible application that is LIKE e-sword and would be able to share add-ons, etc... back and forth to avoid this whole Wine thing?

B

I am not sure about wine 1.1.9, I am using wine 1.1.7. First of all, how do you install e-Sword? Manually in wine? If manually, you could try to double click on any exe file of the addons, it might work now.

But if you use the installer I make on [this]("http://ubuntuforums.org/showthread.php?t=404042") thread, you could use that installer to install add on and other commentary.

DK

---

### Post by brjoon1021 on 2008-11-25
I used your installer. How do I install commentaries, other bibles and stuff ?

---

### Post by david_kt on 2008-11-25
> **brjoon1021 said:**
> I used your installer. How do I install commentaries, other bibles and stuff ?

You can used the installer as well. Please see the available option there, you could just tick whatever bibles and other stuff there, it will automatically download and install for you. It is very simple.

If what you want to install is not in the installer menu, you could download manually the stuff you want to install, and from the installer choose "manual" and navigate to the downloaded exe file to install it.

Or, you could let me know what stuff you want to install, and I will add it on the installer for you.

DK

---

### Post by poebae on 2008-11-25
It might be because you're using a highly irregular, unofficial release of Ubuntu 8.05 :P

Sorry, I wish I could be of more help than just childishly pointing out a typo :(

Actually, I'm aware of a couple of programs out there called GnomeSword and Bibletime.

---

### Post by david_kt on 2008-11-25
> **poebae said:**
> It might be because you're using a highly irregular, unofficial release of Ubuntu 8.05 :P

Sorry, I wish I could be of more help than just childishly pointing out a typo :(

Actually, I'm aware of a couple of programs out there called GnomeSword and Bibletime.

No. What he meant is e-sword 8.0.5, not ubuntu. It is new e-Sword, just launched recently.

DK

---

### Post by brjoon1021 on 2008-11-26
Thanks.

"If what you want to install is not in the installer menu, you could download manually the stuff you want to install, and from the installer choose "manual" and navigate to the downloaded exe file to install it."

Yeah, I typically install just about every commentary, dictionary, map and about 6 bibles if I am using e-sword in Windows. That is what I would like to do here, in Linux / Wine. I am not sure what you mean about choosing "manual" from the installer. I don't see that option. Or, are you talking about installing from within, e-sword?

---

### Post by david_kt on 2008-11-26
> **brjoon1021 said:**
> 
Yeah, I typically install just about every commentary, dictionary, map and about 6 bibles if I am using e-sword in Windows. That is what I would like to do here, in Linux / Wine. I am not sure what you mean about choosing "manual" from the installer. I don't see that option. Or, are you talking about installing from within, e-sword?

No, it is using the installer script I make. Double click and it will give you choice to install:

esword 
upgrade
localize
manual
asv   
etc

What you have to do is just click/tick on it. You can see the manual option is no 4 on the menu.

DK

---

### Post by brjoon1021 on 2008-11-26
It does not give me those options. e-sword installed, but I have no text in the bible whatsoever. I selected several things to install and none of them installed. There is only the KJV bible and it has no text.

To be honest, I don't think that I like the solution of installing e-sword with Wine. I would like to completely uninstall e-sword and Wine. How do I do that ?

---

### Post by david_kt on 2008-11-26
> **brjoon1021 said:**
> To be honest, I don't think that I like the solution of installing e-sword with Wine. I would like to completely uninstall e-sword and Wine. How do I do that ?

Well, the installer has this function as well. Launch the script and on the menu, choose option 2 from the last:

remove_esword    To remove e-Sword installed using this installer

But why you don't like it? May be because you are using wine 1.1.9 so that it has some fonts issue? You could try wine 1.1.7. If wine 1.1.9 cause fonts issue for you, I will blacklist wine 1.1.9 in the installer as there is already one user inform me that wine 1.1.9 causing font error, I have not tested it yet though.

DK

---

### Post by brjoon1021 on 2008-11-26
I uninstalled e-sword and wine. I may try again tomorrow, but with 1.1.7 I will let you know how it goes if I do.

Thanks for your courteous and helpful responses. The installer actually looked different in KDE than it did in Gnome. I originally installed via Gnome log-in and I think I messed the installation up. I have both the 32 bit and 64 bit of Ubuntu. The installation went well into the 64 bit with the 1.1.9 Wine but it failed as I have threaded here with the 32 bit OS. I will try again tomorrow. 

It is a shame that the Quran has such an awesome program that runs really well in Linux, called Zekr, and the bible really lacks something like that. This all feels very unstable to me - having to select the right version of Wine and all of the fiddling to get e-sword to work right. I wish someone (I don't know how to do it) would write a program like, but better than, e-sword for Linux that could use the e-sword add-ons natively.

B

---

### Post by brjoon1021 on 2008-11-26
Question:

Wine-doors which is in the ubuntu repository sounds really easy and better than Wine itself. Have you tried it to install e-sword?

Secondly, I have several other windows bible software packages that I would like to install like a Zondervan, a Quickverse and a few others. They are all at least 3 years old. What do you think my best and easiest route to having them installed properly would be ?

Thanks,

b

---

### Post by david_kt on 2008-11-26
> **brjoon1021 said:**
> Question:

Wine-doors which is in the ubuntu repository sounds really easy and better than Wine itself. Have you tried it to install e-sword?

Secondly, I have several other windows bible software packages that I would like to install like a Zondervan, a Quickverse and a few others. They are all at least 3 years old. What do you think my best and easiest route to having them installed properly would be ?

Thanks,

b

It is rather difficult to say as wine is continuously progressing. What you could do is check in the appdb.winehq.org for any application you want to install.

Wine-doors or playonlinux try to help run wine easier, but it is not perfect and may applications they could not cover yet. So, you should check what they have covered as well.

If you want the easy way, that is to use crossover (paid version of wine), they will give you support to run your particular program:

[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)

DK

---

### Post by lisati on 2008-11-26
As much as I like e-sword (I have a paid-for disk of v7.7.7 installed on my Windows machines) I tend to use GnomeSword2 on Ubuntu. It doesn't have the same set of features as e-sword, but it's better than nothing!

---

### Post by david_kt on 2008-11-26
> **lisati said:**
> As much as I like e-sword (I have a paid-for disk of v7.7.7 installed on my Windows machines) I tend to use GnomeSword2 on Ubuntu. It doesn't have the same set of features as e-sword, but it's better than nothing!

Have you try to install e-sword using installer script I make? Using my script, it is even easier to install e-sword in linux as compared to in windows, if you use gnome (ubuntu). Just make sure you wine version is wine 1.1.7. Check it out [here]("http://ubuntuforums.org/showthread.php?t=404042").

DK

---

### Post by Daniel G on 2009-01-02
If you have access to e-sword installed in windows it is easy to copy installed bibles, dictionarys and commentaries. (i am refering to ones that are free to copy)

In windows by default Bibles will be in the e-Sword folder in the Program Files folder. they will have extentions like .bbl  or .cmt  commentary or .dct  dictonary. you can copy them all at once with the file browser or to USB memory or CD.

Using Gnome, to find where to put them, go to your home folder in Ubuntu.  In the View menu select show hidden files. (.wine is a hidden folder) Open .wine/drive_C/Program Files/e-sword. Paste your .bbl  .cmt and  .dct files in this folder.  The next time you open e-Sword your files will be there.  You might not be able to read the tabs due to font problems but they work anyway. 

I am running Ubuntu intrepid with wine1.1.11 and e-Sword 8.05   I tried to install books from .exe files with no success.  It is easier to copy the installed .bbl files than to install the .exe files one at a time any way.

Hope this helps
Daniel

I also have Gnomesword2 installed but there are different books and features on each program.

---

### Post by david_kt on 2009-01-02
> **Daniel G said:**
> You might not be able to read the tabs due to font problems but they work anyway. 

I am running Ubuntu intrepid with wine1.1.11 and e-Sword 8.05   I tried to install books from .exe files with no success.

Try using my script, it will help you to install e-Sword 8.06 in no time, including selected bibles and others. Please see the first post of this thread:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

DK

---

### Post by Daniel G on 2009-01-03
David thanks for your script.  It might be helpfull for someone who is skilled in running linux from a terminal or someone who does not have access to e-sword installed under windows. 

If one has access to an e-sword windows instalation it is faster to copy books from the windows instalation than to read install and run your scripts. 

Daniel

---

### Post by david_kt on 2009-01-04
> **Daniel G said:**
> David thanks for your script.  It might be helpfull for someone who is skilled in running linux from a terminal or someone who does not have access to e-sword installed under windows. 

If one has access to an e-sword windows instalation it is faster to copy books from the windows instalation than to read install and run your scripts. 

Daniel

You do not need to know any terminal thing to use my script. Just download the script, double click it and it is completely GUI.

It is true if you have windows installation is faster to copy the bibles. But you still need to do some tweak in order to make it run. My suggestion is to use the script to install the main program only, it include the neccesary tweaks, including downloading msls31.dll from microsoft. It will make e-Sword run perfectly.

After that, you could copy the bibles from windows.

The script also has other functions such as backing up your e-Sword and restoring it. As such, installing to multiple computers would be a breeze using that functions. Again, no terminal things involved, just point and click.

DK

---

### Post by jonathonblake on 2009-01-05
> **david_kt said:**
> My suggestion is to use the script to install the main program only, 

If one wants to use *any* of the e-Sword utility programs, install them using that script.  
Select  Manual installation,and then select the installation executable.

>  As such, installing to multiple computers would be a breeze using that functions. Again, no terminal things involved, just point and click.

FWIW, somebody has ported that script to Windows.    I haven't tried the Windows version yet. (My winbox doesn't have an Internet connection.)(When I can figure out exactly what license it uses,I'll list it at e-sword-users.org.)


jonathon

---

### Post by lupabone on 2009-01-06
> **brjoon1021 said:**
> I used your installer. How do I install commentaries, other bibles and stuff ?

Hi!
I am new in Linux, do not understand The Linux language yet, either English. But i will try to help you. I will tell you the steps.
If you have the GNOME SWORD install already, go to SYSTEM-ADMINISTRATION-SYNAPTIC PACKAGE MANAGER. when window open:
1-Write in the search bar BIBLE.
2.And you will see all the applications under the name ESWORD mark each one
  and follow the instructrions. Good luck!

---

### Post by jonathonblake on 2009-01-07
> **lupabone said:**
> 
If you have the GNOME SWORD install already,

GnomeSword and e-Sword are two completely unrelated projects.  Resources that can be opened in one, can not be opened in the other.[/quote]

>  go to SYSTEM-ADMINISTRATION-SYNAPTIC PACKAGE MANAGER. when window open:

Do _NOT_ use Sybaptic to install resources for GnomeSword, BibleTime,or any other front end for The Sword Project.  Use the tool that is built into the front end, to add new resources.

> 
2.And you will see all the applications under the name ESWORD 

If either e-Sword or its resources shows up in synaptic, then somebody (or a lot of somebodies) are going to be receiving"cease and desist letters".

jonathon

---

