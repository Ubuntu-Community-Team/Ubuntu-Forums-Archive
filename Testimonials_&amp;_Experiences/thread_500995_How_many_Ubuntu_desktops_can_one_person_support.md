---
title: "How many Ubuntu desktops can one person support?"
date: 2007-07-14
forum: Testimonials &amp; Experiences
---

### Post by Maxtorm on 2007-07-14
Here's what I love about installing Ubuntu on friends and family computers: I don't get phone calls.  Better still, they love it -- and I've been installing it since version 6.06 for novice and experienced computer users alike.

So, installing Ubuntu on their computers actually gives me more spare time and peace of mind because I'm not having to field the 9 PM "Um..  I was just on this web site and a pop up came up that said my computer was infected, so I clicked the button to ... uh.. disinfect and now nothing works.  Help!" calls.

In Canada, to buy a new computer the "normal" way is going to cost you about $500.  That will get you a computer running the blah version of Vi$ta and it will likely be a clone.  In turn, that clone will likely fail or start behaving erratically in short order.  And despite the fact that my friend or family member bought the computer at FutureShop or Best Buy or wherever, I get the call.  I now no longer accept these calls (thankfully, since I have been installing Ubuntu, I rarely receive them either).

For ~$300, I can get an off-lease tier 1 (usually IBM or HP/Compaq) computer.  These machines invariably will have the legit OEM version of Windows XP on them, so I'll use GParted and create a 4 GB partition for Windows XP -- just in case the user *has* to have Windows for some task.  I'll then install OpenOffice.org, Firefox and one of the available free antivirus products.  I suppose if I was really cruel and wanted to further demonstrate the difference between Windows and Ubuntu, I'd leave the anti-virus off the machine, but hey, I'm a nice guy.

Ubuntu, of course, is installed on the remainder of the hard disk.  We're talking P4 2.6 machines with at least 512 MB in them, so Ubuntu flies.  I'll set up Remote Desktop on one of the higher ports for troubleshooting purposes.  Usually Automatix gets installed so that they have a quick way to get the codecs they need to play DVDs and MP3s.  If they have an iPod, I'll install and configure Amarok.

I'm now "supporting" 10 of these installations and expect the trend to continue.  I also make sure they know how to get to ubuntuforums.org.  

One thing of note: despite these all being dual boot computers, every last one of them has said they no longer use the Windows partition.  One guy says he has to use Windows to connect to his corporate SonicWall VPN, but I'm looking into ways to break that requirement.

Ultimately, I don't suppose I have a real point, but wanted to share the experience in case there was anyone out there thinking about getting their feet wet installing Ubuntu for their friends, but wondering what kind of can of worms that would be opening. Trust me -- they'll love you for it!

---

### Post by Ralob on 2007-07-15
I got my sister to install it recently, and i am working on doing the same for my mom. I think I also got a few buddies of mine interested. The whole "no spyware" thing really got them pumped. I sent him some information, so we will see what he decides to do. :)

btw, thanks for sharing your experience. I love reading testimonials and good reviews. :popcorn:

---

### Post by Hendrixski on 2007-07-15
I've installed it for a lot of people, but haven't had the time to offer them support.  Rather I just point them to the forums and to IRC and they take it from there.  I feel like I'm doing my good deed for the day.

---

### Post by wolfen69 on 2007-07-15
step away from the computer

---

### Post by lancest on 2007-07-16
I often install Linux for people lately. When they have the ability to word/doc & print, burn & rip cd's download music safely, edit photo's in gimp they begin to love Linux. One new Linux guy was mistified because his mp3 player suddenly got so many viruses. This was after he downloaded tons of Music in Linux using Limewire then booted into Windows after. AVG caught 20 or more viri.  He now knows what I mean about Linux being pretty safe. Big smile!!! Now I am teaching him how to use some and great sound and media tools Linux comes freely with. k3b,Juicer,Amorak,etc etc.  He is really impressed. What a great way to get people going!!

---

### Post by ALMRev on 2007-07-16
I now have three desktops and one laptop running Ubuntu 7.04 in a small home-office. Everything just works.
I had to make some changes to my wife's computer running XP and I realized how much I really love Ubuntu. 
Starting to get other converts and not one has expressed any interest in going back to Windows.

Try it, You'll like it ! ! ! !

---

### Post by Alterax on 2007-07-17
I am currently supporting three servers (Fileserver, Web-application Server, and an LTSP server) and twenty-eight desktops (half of which are thin-clients using LTSP) at one of my client sites (of which I am there three days per week).   It is a mixed environment where the Linux OS is a recent addition, so I am sharing the glory with the Windows Sysadmin.

I'm not even breaking a sweat as I do this; my biggest problem with the users was one argument with one about installing Ubuntu on her desktop.  She saw others in the plant running it and was mad because I wasn't going to install it on hers.  (My reason:  Her job is currently dependent on a proprietary database that only runs on Windows, which we are currently in the process of porting over.)

The users at this site run the gamut of computer literacy.  Some know just enough to do their job; others are die-hard Windows power-users that are afraid of losing their "special" status.  The new people don't see what the big deal is; they have to learn to use the computers anyhow.  The more seasoned veterans of Windows tend to be apprehensive until they call complaining that they need a certain program, whereupon I SSH in, install the package, and tell them it's ready.  (Common response: "Then why don't I have to reboot?")  The WinAdmin?  He's impressed with a non-monolithic, multipurpose server where failure of one component does not usually mean failure of the others.

Personally, to go back from the fanboydom that comes from being comfortable with a great product, I am having very little trouble with supporting these users.  The migration plan is expecting me to be the primary Linux admin until the Windows admin is trained up; so I will be adding users in increments of 25 or so.  During this time I will not only be doing the admin work, but writing documentation, porting programs into web applets, and conducting training for the end users.  Were these things all put aside (except of course for documentation, which is always an admin's responsibility), I could easily manage a site of 200-350 users without the need to hire additional staff.

If you are interested in supporting a large number of users, here's some suggestions:
1.  Tackle switching users by small groups, based on task.  Put the easiest changes first.
2.  If you have to do it more than once, script it.
3.  If you have to compile it from source more than once, build a .deb package.
4.  It's easier to handle 30 users on thin clients/LTSP than it is to handle 10 users on individual machines.
5.  Take it slow and in steps.  Don't migrate a group until you are sure it can be done without a need for dual-booting (actually counter-productive since they have to stop and reboot.  Given the choice, most will stay in Windows--we even have one guy on our site that has a dual-boot XP/98 machine.  Guess which one he uses....)
6.   While preparing them for the changeover, replace IE with firefox and OpenOffice for MS Office. (One less thing to learn all at once)
7.  Users aren't to be punished by the upgrade, and shouldn't have to "deal with it."  They DESERVE the upgrade; it gets rid of so much of the BS that makes their jobs rough! (Get them enthusiastic; it will make it much easier on them, and their interest makes it easier on you)
8.  Don't duplicate your efforts.  Set up a wiki; when you fix something, write an article for it.  One for admin issues and one for user issues is better; make the user issue one something available to them so they can check the wiki without having to bother you (some would rather sit in silence than ask for help)
9.  Standardize your users.  

A lot to start from, but that's my experience in a nutshell.

--Alterax

---

### Post by 3rdalbum on 2007-07-17
I'm supporting one user in my city, who is teaching AND learning from, another friend who started using Ubuntu at the same time. Very satisfying.

---

### Post by MianoSM on 2007-07-17
I used to get weekly calls from my parents - as of July 1, I installed Fiesty Fawn, and aside from needing mp3 playback, and general questions - I would say that I have saved myself 90% of the time and frustration that was coming out of windows being on their computer.

---

