---
title: "Virus for Linux and Windows?"
date: 2005-07-05
forum: The Cafe
---

### Post by sonny on 2005-07-05
Does anyone have more information about the virus colled W32/Linux.Winux, or W32/Lindose, it was suppose to be created in 2001 by Benny/29A; the same cracker that wrote the first virus for Win2k (before it was relased). The reason I'm asking this is that in many threads here in the forum touch this topic, saying that there's no virus for Linux, and then I found out about this virus. This virus is multiplatform, it infects windows and Linux machines. Did it really affected Linux machines or it was just the theory?

For those who speak spanish here's the [link](http://www.diarioti.com/gate/n.php?id=2433) , if you don't speak spanish I think that altavista will do a nice job.

---

### Post by N'Jal on 2005-07-05
This is an interesting thread. Since i do wonder if we will ever see linux virus's in the wild. The first virus w32/Linux I will reserch them all. First w32/Linux

> {Win32,Linux}/Simile.D is a very complex virus that uses entry-point obscuring, metamorphism, and polymorphic decryption. It is the first known polymorphic metamorphic virus to infect under both Windows and Linux. The virus contains no destructive payload, but infected files may display messages on certain dates. It is the fourth variant of the Simile family. This variant introduces a new infection mechanism on Intel Linux platforms, infecting 32-bit ELF files (a standard Unix binary format). The virus infects Portable Executable (PE) files as well as ELFs on both Linux and Win32 systems. So far Symantec has not received any submissions of this virus from customers.

NOTE: The {Win32,Linux} reference follows the CARO (Computer Anti-virus Researchers Organization) standard naming convention. This is meant to imply that a threat can infect across multiple platforms, Win32 and Linux. Another such example would be {Win32,W97M}.

Also Known As: 	W32.Simile, {Win32, Linux}/Simile.D, {Win32, Linux}/Etap.D
	
Type: 	Virus
Infection Length: 	variable
	
	
	
Systems Affected: 	Windows 95, Windows 98, Windows NT, Windows 2000, Windows XP, Windows Me, Linux
Systems Not Affected: 	Windows, Microsoft IIS, Macintosh, UNIX 

Ok so, no reports of it nor is it actually deadly, i think this is a lab virus, there have been virus's written for linux in lab's to see if it is theoretically possible to write linux virus's and it is... but there are little or none in the wild. See the report [here](http://securityresponse.symantec.com/avcenter/venc/data/linux.simile.html) 

Your second virus is in fact graphical interface to the loadlin boot loader, don't worry about that. [Winux](http://www.linux-france.org/prj/winux/English/) 

Finaly, i'm no expert but the third name matche's the first name though the detail's are a bit scetchy it sounds like the infection is the same. Details [here](http://www.sophos.com/virusinfo/analyses/w32lindose.html) 

If someone in the know could confirm what i found it would be helpful

---

### Post by mtron on 2005-07-05
i know only of one virus really "seen in the wild"
[http://math-www.uni-paderborn.de/~axel/bliss/](http://math-www.uni-paderborn.de/~axel/bliss/)

None of the Unix or Linux viruses became widespread - most were confined to the
laboratory. That these worms work, you need to run an old unpatched system, some specific software (e.g. lynx), and do really stupid things (e.g. work as root the whole time  [-X ). 

and just for fun  ;-)  
[http://os.newsforge.com/article.pl?sid=05/01/25/1430222](http://os.newsforge.com/article.pl?sid=05/01/25/1430222)

---

### Post by sonny on 2005-07-05
> **mtron]and just for fun   said:**
> http://os.newsforge.com/article.pl?sid=05/01/25/1430222[/url]
I also think wine has a long way to go to make windows viruses run under Linux.  :grin: That's a good joke. But seriously, it seemes like no Linux virus has left the lab, except for the Bliss, but I think that to say a virus actually works it has to infect more than one user, at least 1,000 from my point of view.

Is the virus thing becomming a myth, an almost forgotten memory of something that could've happen?

---

### Post by WildTangent on 2005-07-05
[QUOTE=sonny]Is the virus thing becomming a myth, an almost forgotten memory of something that could've happen?[/QUOTE]
ask any windows network admin if he or she still has nightmares about blaster, mydoom, sasser and the like, the answer will be yes for most of them :P

-Wild

---

### Post by RastaMahata on 2005-07-06
So is linux able to have viruses? This was one of the main reasons I switched from Windows :(

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=RastaMahata]So is linux able to have viruses? This was one of the main reasons I switched from Windows :([/QUOTE]

Any OS could possibly get a virus. No software is immune. From what I understand..the only viruses made for old Linux are made just so there are some. There are no viruses for Ubuntu yet...

---

### Post by mtron on 2005-07-06
[QUOTE=RastaMahata]So is linux able to have viruses?[/QUOTE]

theoretical yes. Every mistake in a code can be used to do something bad...
But this is also one of the big advatnage of open source software. When the source is avaiable everybody can help to find and fix mistakes. 

I am also not really happy with the new "package" system to install software de - centralized. One of the advantages of the apt-get system is the secureness of the code, if you only install from the official repositories.

---

### Post by sonny on 2005-07-06
[QUOTE=mtron]But this is also one of the big advatnage of open source software. When the source is avaiable everybody can help to find and fix mistakes. [/QUOTE]
It can also be a disadvantge.. cus any cracker would look up to the code and then made a more lethal virus... perhaps the problem wll be solve faster in OSS, but still, some damage will be done... right?

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=sonny]It can also be a disadvantge.. cus any cracker would look up to the code and then made a more lethal virus... perhaps the problem wll be solve faster in OSS, but still, some damage will be done... right?[/QUOTE]

Well...its not like people haven't tried (in a lab). Linux/Unix is designed to be secure with its multiuser system. For a virus to really cause havok...it would have to ask for your password!

---

### Post by Kvark on 2005-07-06
Linux is safe against viruses. But there is a lot of programs for linux. So it is possible that some versions of some programs out there contains security holes that can be used by viruses. For example if a bug in an email program would causes it to auto open attachments then only those who use that program are at risk and only until the bug is fixed.

Also some viruses, like the classical email attachment approach could work well even without security holes, users tend to open unexpected attachments that they don't know what it is.

"how fun! my coworker Olga who always talks to me in russian and barely knows how to use a keyboard sent me an email in english to show a fun executable file she made! I gotta try it!"

But since linux viruses will have to rely either on specific programs or on user stupidity they will have only limited spread.

---

### Post by N'Jal on 2005-07-06
Also will the binarys work if compiled on a different system, say someone is using real bleeding edge gcc and libc etc would that binary work on a system that has been compiled against different librarys?

---

### Post by az on 2005-07-06
[QUOTE=sonny]It can also be a disadvantge.. cus any cracker would look up to the code and then made a more lethal virus... perhaps the problem wll be solve faster in OSS, but still, some damage will be done... right?[/QUOTE]

What you are describing is "security by obscurity".  Microsoft uses it.  It does not work.

---

### Post by NeoSNightmarE on 2005-07-06
I have argued this many times with Windows users and we always come to the same conclusion. And that would be that although it's impossible to make anything completely immune to viruses, there is a much greater chance of a closed source OS that runs like crap to start with to get one than the alternative (linux as the alternative)

---

### Post by mtron on 2005-07-08
so most of the people in this thread agree that open source is better for security than "closed source" not a big surprise in a linux forum. ;-) 

But i am really interrested to hear what you think about this new "package" system in terms of security? 

When you use (or are forced to use) de - centralized sources for your software, isn't the possibillity much larger to get bad code on your system? and i understand that it is not good for huge software archives to use the apt system, but it proofed itself to be a very reliable and secure way to get the software you want up-and-running.

I tried some .package files to install, but it has really problems to recognize all the dependencies ( i tried it with  tuxracer) other experiences? 

cheers mtron

---

### Post by N'Jal on 2005-07-08
Isn't .package an autopackage format? I don't have a problem with autopackage, from what i see it's just an executible bash script, albeit very advanced, i am playing with autopackage not found a problem with it really.

---

