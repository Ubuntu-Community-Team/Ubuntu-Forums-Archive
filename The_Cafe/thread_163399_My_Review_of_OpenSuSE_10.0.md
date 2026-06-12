---
title: "My Review of OpenSuSE 10.0"
date: 2006-04-20
forum: The Cafe
---

### Post by xXx 0wn3d xXx on 2006-04-20
Well, since dpkg broke in my prior breezy installation, I installed Dapper. Then I couldn't get my wifi card to work in Dapper so I decided to install OpenSuSE 10.0.

**My Expericence:**
The OpenSuSE install cd has a nice GUI interface but that doesn't nessary mean that it is functional. I decided to do a net install because I didn't feel like downloading 5 cd isos and burning them. So I selected the mirror and all that and the install took about 2 1/2-3 hours because I had to download about 2.6 GB of packages, system files, and then install it. When I first booted into the desktop, the resolutions was huge and outdated drivers were being used for my card. I fixed the screen res but the drivers couldn't be fixed. I tried to install the ATi Drivers but it wouldn't work. I also have to say that the Redhat Package Management System is completly flawed. It has many issues and there were alot of dependency problems. Then I tried apt-get as my Package Management System. Of course, that didn't go well. It was not configured correctly and I couldn't get the sources.list to work. Then I decided to get my breezy cd and install it. I tried to resize the SuSE partition and make room, but it couldn't be resized. Novell's distro seems to be "Great looks and no Usability." Seriously, SuSE was horrible. Then I decided to put down my install cd and said, "hmmm...I'm going to configure my wireless card." So I tried ndiswrapper but of course - it didn't go too well. I also noticed that SuSE is very slow on my laptop and their community is not active/helpful. So here I am. Back on Breezy. The best Linux Distribution that I have ever used. SuSE is gone and it won't be back anytime soon. 

My Rating of SuSE:
5.7/10

---

### Post by htinn on 2006-04-20
I think apt-rpm was pretty much dropped about a year ago. It's too bad. I kind of liked it.

---

### Post by ComplexNumber on 2006-04-20
[quote=htinn]I think apt-rpm was pretty much dropped about a year ago. It's too bad. I kind of liked it.[/quote]it wasn't.  its still there now.


> 
I also have to say that the Redhat Package Management System is completly flawed. It has many issues and there were alot of dependency problems. how did you arrive at that conclusion? just curious. the dependency 'issues' exist as much for deb as for rpm.

---

### Post by xXx 0wn3d xXx on 2006-04-20
[QUOTE=ComplexNumber]no.  its still there now.


 how did you arrive at that conclusion? just curious.[/QUOTE]
It was just the dependency issues and how hard it was to get things done and installed.

---

### Post by ComplexNumber on 2006-04-20
[quote=MasterChief1234]It was just the dependency issues and how hard it was to get things done and installed.[/quote] i see. i've never had a problem. and neither has anyone else that i've heard about in that respect. i don't see what problems you could have had that aren't likely on ubuntu. if anything, the advantage of yast makes it considerably better.
i'm really not sure where you're coming from on this. anyone would think that there is no such thing as dependency hell on deb based systems when we all know that there is.
it doesn't seem like you've given suse or rpm a fair try.

---

### Post by htinn on 2006-04-20
Every distro has its ups and downs. I had to give FC5 about 2 weeks before I stopped thinking about chopping up my FC5 discs.

---

### Post by htinn on 2006-04-20
[QUOTE=ComplexNumber]it wasn't.  its still there now.[/QUOTE]

Ah, that's good. I guess it was just Fedora Core that stopped maintaining it in their repos.

---

### Post by briancurtin on 2006-04-20
[QUOTE=MasterChief1234]**My Expericence:**I also have to say that the Redhat Package Management System is completly flawed. It has many issues and there were alot of dependency problems.[/QUOTE]
why were you using this in SuSE?

[QUOTE=MasterChief1234]Then I tried apt-get as my Package Management System. Of course, that didn't go well. It was not configured correctly and I couldn't get the sources.list to work.[/QUOTE]
if it wasnt configured correctly, then why didnt you correctly configure it? 

[QUOTE=MasterChief1234]Novell's distro seems to be "Great looks and no Usability." Seriously, SuSE was horrible.[/QUOTE]
sounds like you didnt know what you were doing, so im not sure your rating of 4.3 and "horrible" hold much water. did you even use yast? you basically say that SuSE is horrible because RedHat's package manager didnt work and because you couldnt configure apt-get. whos fault is that? the resolution problems happen with lots of distros, its just a matter of taking a few minutes and finding out whats going on and what should happen in place of the defaults. 

i dont use SuSE, and im not a novell/SuSE fan boy, but im not sure you gave SuSE a proper "try" getting it to work.

---

### Post by ComplexNumber on 2006-04-20
[quote=htinn]Ah, that's good. I guess it was just Fedora Core that stopped maintaining it in their repos.[/quote] yes, [here]("http://rpm.pbone.net/index.php3/stat/4/idpl/2523907/com/apt-0.5.15cnc7-6.i586.rpm.html")'s proof that open suse has it. no. fedora 5 and fedora 4 have apt-get too ([click]("http://rpm.pbone.net/index.php3/stat/4/idpl/2680632/com/apt-0.5.15cnc7-61.rhfc5.at.i386.rpm.html")).

---

### Post by bluebell on 2006-04-20
[QUOTE=MasterChief1234]
The OpenSuSE install cd has a nice GUI interface but that doesn't nessary mean that it is functional.
[/quote]
Did you have any problem with the graphical installer?
It is functional and beautiful. It also offers more options than ubuntu's installer, for example, package selection.


>  I decided to do a net install because I didn't feel like downloading 5 cd isos and burning them. So I selected the mirror and all that and the install took about 2 1/2-3 hours because I had to download about 2.6 GB of packages, system files, and then install it. When I first booted into the desktop, the resolutions was huge and outdated drivers were being used for my card.
It you take a look at the hardware configurations summary during the install process and make changes by a few mouse clicks, you would not have the resolution problems. And sax is a convenient tool to configure your display, isn't it?

> 
 I fixed the screen res but the drivers couldn't be fixed. I tried to install the ATi Drivers but it wouldn't work.
As far as I know, ATI is notorious for its linux drivers. I have got a nvidia card and I installed the official driver with YaST online update. Some other non-oss drivers are also available in online update.


> 
 I also have to say that the Redhat Package Management System is completly flawed. It has many issues and there were alot of dependency problems. Then I tried apt-get as my Package Management System. Of course, that didn't go well. It was not configured correctly and I couldn't get the sources.list to work.
Well, RPM is not the problem. I can't see any big differences between rpm and deb. Both have dependeccy issues. It is the way you manage rpms or debs matters. In ubuntu people use apt to manage debs. In suse it is YaST package manager that does the same thing.

And many rpm-based distro users are happy with rpm-apt, yum, urpmi, smart or yast because all of them work. APT is not the only way to go.

> 
 Then I decided to get my breezy cd and install it. I tried to resize the SuSE partition and make room, but it couldn't be resized. Novell's distro seems to be "Great looks and no Usability." Seriously, SuSE was horrible. Then I decided to put down my install cd and said, "hmmm...I'm going to configure my wireless card." So I tried ndiswrapper but of course - it didn't go too well. I also noticed that SuSE is very slow on my laptop and their community is not active/helpful. So here I am. Back on Breezy. The best Linux Distribution that I have ever used. 
Did you try wifi in suse? It works out of the box for me in suse.

> 
SuSE is gone and it won't be back anytime soon. 
My Rating of SuSE:
4.3/10

My rating of SuSE 10.0:
9.5/10

---

### Post by htinn on 2006-04-20
[QUOTE=ComplexNumber]fedora 5 and fedora 4 have apt-get too ...[/QUOTE]

I know 3rd party repos have it, but I don't trust AT right at the moment. For 3rd party rpms, FreshRPMs works out nicely and Livna is great for kmods. It's really no big deal, but I'd rather not mess with it.

Last time I used Fedora Core with apt was in FC4, and although it wasn't that difficult to set up it soon complained constantly about this or that "dependency" and yum had no trouble at all (aside from crashing every now and then). Don't even get me started on up2date. ](*,) 

Much as loved using apt in FC4, I had to let it go because it was just too much of a headache, and everyone and their dog at the forums will tell you "just use yum". I decided to split the difference and use Smart, and I've been a happy camper ever since then. :)

---

### Post by ComplexNumber on 2006-04-21
> Don't even get me started on up2date fedora doesn't use up2date anymore.
> 

I decided to split the difference and use Smart, and I've been a happy camper ever since then.
in my opinion, Smart is among the best package manager front ends around.

---

### Post by dasunst3r on 2006-04-21
> I tried to install the ATi Drivers but it wouldn't work.Getting ATi drivers to work in any distro of Linux is a pain in the butt, period.  Did you install the kernel source and the build tools?
> I also have to say that the Redhat Package Management System is completly flawed. It has many issues and there were alot of dependency problems. Then I tried apt-get as my Package Management System. Of course, that didn't go well. It was not configured correctly and I couldn't get the sources.list to work.I haven't had experience with apt-get for SUSE, but YaST does a great job.  Similar to any other distribution I've used, I had to add a few repositories to get SUSE working the way I wanted it to.  Here's a list of them:[http://en.opensuse.org/Additional_YaST_Package_Repositories](http://en.opensuse.org/Additional_YaST_Package_Repositories)
> Novell's distro seems to be "Great looks and no Usability." Seriously, SuSE was horrible.SuSE was the best distro for my laptop (Dell Inspiron 6000d).  Kubuntu Breezy was taking its toll on my poor processor :'(  I should say, however, that Automatix is really cool! > So here I am. Back on Breezy. The best Linux Distribution that I have ever used. SuSE is gone and it won't be back anytime soon.Sorry you didn't like it, but when you see XGL, be sure to give Novell a few pats on the back because someone in there came up with that.

---

### Post by magomago on 2006-04-21
get ready for Dapper ;)  It is SUBSTANCIALLY Better than Breezy...even from flight 5 I feel it was a lot more polished.  Breezy was great, but could have been so much better.  Lets wish to a good Dapper, and hope Dapper+1 incorporates all those beautiful Compiz stuff by default :D

---

