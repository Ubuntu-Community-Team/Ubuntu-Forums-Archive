---
title: "MS Works - install in wine"
date: 2011-03-09
forum: Wine
---

### Post by carusoswi on 2011-03-09
I am a long-time Ubuntu user, own version 7 of Crossover, and have recently upgraded to Ubuntu 10.10 . . . well, to me it is an upgrade, however, I performed a clean install of 10.10.

My understanding is that Crossover, no matter what version you run, is based upon older versions of Wine, so, I installed Wine, and successfully installed Pagemaker 6.5 from my CD.

The program I really use from Windows is the Works flat file database program.  I have it running (for years, now) in my XP system, but would prefer (and have run it) to run it in Ubuntu.

When I inserted the CD and tried to install using Wine, I received an error message that the .exe install file was not marked with executable permission.  If I go into properties/permissions to check that box, it will not stay checked.  Logging in as root does not solve the problem.

In frustration, I re-installed my old version of Crossover, and the installation sailed right through without a problem.

So, what is it that I'm doing wrong in wine?  Why would my old PM65 disc work fine while my MSMoney_Works disc choked in Wine?

I even tried copying the disc to my hard drive, but that made no difference in Wine (but I was able to install from the HD directory with no problem in Crossover).

Since I now have the program working in Crossover, this problem is not a burning one, but my curiosity forces me to seek a solution.  How would one install MSMoney/Works from the CD in the current iteration of Wine?  

For as long as I can remember, I always kept both Crossover and Wine installed for these sorts of situations, where something I wanted to run would work on one side and not the other.  I've never really understood what makes these wonderful aps work, but am very appreciative, nonetheless.

Thanks in advance for any advice.

Caruso

---

### Post by cogadh on 2011-03-09
You have run into a "security feature" of Ubuntu. All executables are marked as "no execute" by default and since CD/DVD is not a writable media, you can't change that through the GUI. There is an easy way to get around it: just run the install through Wine via the terminal. You don't need to change any permissions or anything, just open a terminal, then "wine" the install executable, like this:
```
wine /media/<CD-ROM mount>/setup.exe
```

---

### Post by carusoswi on 2011-03-11
Thanks for your response.  I was able to install Works, but, now when I try to start it, I get a message that the program cannot display the EULA, and cannot, therefore, be run - please reinstall.

So, I'm looking for that little check box to appear so I can click accept, then, I should be good to go.  How to make that happen is the question.

Have you any suggestions?

Thanks.

Caruso

---

### Post by carusoswi on 2011-03-11
Ok, a couple other problems.
You didn't show it, but I assume I have to either log in as root to run the code you posted or precede it with Sudo.

Logging in as root allowed the code to run, and Works was installed.

Unfortunately, when I log back in as user, Works does not appear on my Wine program menu.

If I run the code from my user account, I get a message that .wine is not owned by me.

Can you help? (sorry to be such a pest)

Thanks.

Caruso

---

### Post by carusoswi on 2011-03-11
One last comment.  I re-copied the disc to a folder on my HD, wet permissions on all folders to allow create/delete, then, on all .exe files as executable.

Wine will attempt to install, even finishes, but I still get that 'no EULA display' message, so the program will not run.

I guess I'm a bit puzzled why more recent versions of Ubuntu have to be so much more 'secure'.

I assume that most of us tinkerers who will spend hours trying to get an MS ap to run in wine know enough about 'security' that we can re-install Ubuntu if our tinkering breaks the system.  How useful is it, really, to be so hamstrung when you want to install some executable from a CD?

I find this level of security oppressive.

Give me back my freedom.

Caruso

---

### Post by cogadh on 2011-03-11
It was not necessary to use sudo or root to do that. In fact, you should never run Wine using root or sudo. First of all, everything in Wine should run fine as a normal user (if it doesn't, you're either doing something wrong or the application itself just doesn't work in Wine). Secondly, it is potentially very bad. Using super user permissions like that gives Wine full access to your entire system, rather than just restricted access to certain files in your home directory, which gives Windows applications, including bad things like viruses and other malware, the ability to alter and break your Linux system. Additionally, using root or sudo permissions changes the ownership of the .wine directory where your Windows applications are installed, preventing you from running them as a normal user and producing that "wine is not owned by you" message.

As for your problems, I probably should have suggested this from the start, but you should check Wine's Application Database to see if Works... works in Wine, which it doesn't: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=380](http://appdb.winehq.org/objectManager.php?sClass=application&iId=380)

On the security front, Linux, unlike Windows, takes the stance that it is usually better to be secure than convenient, hence why Linux is generally "safer" to use than Windows. In this particular circumstance, that security only affects Windows applications, since Linux applications on CD will already have the necessary permissions set to run normally (or already require root/sudo permission to run in the first place). The general rule with Linux is it is always better to use a native application whenever possible over "shoehorning" a Windows application into Linux with Wine, which means the vast majority of Linux/Ubuntu users are probably never going to run into the security problems that we Wine tinkerers have to deal with, so it's really not much of a concern for the Ubuntu devs.

---

### Post by mark bower on 2011-03-11
I ran into the EULA problem the same as you.  There is an "O.K." at the bottom of the EULA pop-up, but clicking on it does nothing.  I had to close the window/terminal.  However, without apparently accepting the agreement, everything worked just fine.

mark bower

---

### Post by carusoswi on 2011-03-12
Cogadh:
I really do appreciate your replies and efforts to help, but, as I said from the start, I've been using Linux (in general)and Ubuntu (specifically) for a long time, now (my first upgrade was to 6.10, so, I guess that means I started with 6.04, although, for some reason, 6.06 seems to creep into my memory, correctly or not, but it doesn't really matter . . . I've been working with Ubuntu that long).

I also have worked with Windows since before that time, and have a costing routine that I developed for MS Works when that program was supplied on 5" floppies.  What I developed works for me and my business, I've refined it over the years, and, for as long as I can run Works, I'll be using that routine.

The reason I've tried to install it in Wine with 10.10 is because it has always worked flawlessly for me in previous versions of Ubuntu, statements to the contrary notwithstanding (I will head over and have a look at the info provided in your link, thanks).

I have broken enough Ubuntu installations to know that it's always possible when resorting to root to tinker with something.  That's a risk I am more than willing to take.  I also feel quite capable of measuring my own level of risk when it comes to OS's, and, while I appreciate the virus resistance inherent in all versions of Ubuntu, I don't appreciate what appears to me a new and more aggressive attempt by later versions of Ubuntu to protect me from my own dabbling interests.  If I've managed to develop enough curiosity to go in and try to set the permission switch on some .exe file, Ubuntu ought to leave me to my own devices with respect to the risk involved in running the file.  We are already prompted for our user password.  That should be enough.  I feel the same about using root (which I had never needed before version 10.10).  If I feel I need to go there, then, I've no one to blame but myself if my installation becomes broken.

I am sufficiently confident that my OEM MS Works w/ Money disc is virus free that I am willing to balance the risk of having to reinstall Ubuntu (not a huge inconvenience by any stretch . .  . one of the many Ubuntu features about which I brag daily) against the convenience of being able to set the switch on the discs .exe files without undue inconvenvience.

In later versions of Ubuntu (10.04 and 10.10) my computing has run into more than one complication due to what I perceive as a more aggressive security scheme.  For example, no amount of fiddling would allow me to grant read/write permission to an externally mounted photo card.  I had to first empty the card and format it from Ubuntu before I could exchange files freely from my Ubuntu machine to the card and back (not a complicated chore, but one that consume more than a little time).  Now, a wine-installed program that I've used consistently over the years isn't working in this version of Ubuntu/wine.  I am not happy about that, whatever the cause (Ubuntu or wine), but I am especially frustrated at having to spend time learning how to fix something that really wasn't broken in earlier versions of Ubuntu (probably previous to 10.04), namely, the setting of permissions, or, probably more precise, having to fiddle with permissions at all on an inserted disc (I used to just pop in the disc and install with wine).

I do understand that I may simply be paying the price for progress in Ubuntu on many other fronts, but remain annoyed by the enhanced security built into later Ubuntu versions.

I cannot possibly know all the reasons behind the thinking that brought this level of security into Ubuntu, but, for me, it has an MS flavor, a taste for which I do not care (protect the user from him/herself, as he/she has not the knowledge or wisdom to exercise due caution).

This irritation is not earth-shattering for me nor, likely, anyone else.  I'll run my little flat-file from Windows or an earlier version of Ubuntu (or some other Distro), but felt I should make my feelings known.  Now, enough of my rantings, I'm off to check out that link you provided, and then, on to something else.

Thanks again.

Caruso



> **cogadh said:**
> It was not necessary to use sudo or root to do that. In fact, you should never run Wine using root or sudo. First of all, everything in Wine should run fine as a normal user (if it doesn't, you're either doing something wrong or the application itself just doesn't work in Wine). Secondly, it is potentially very bad. Using super user permissions like that gives Wine full access to your entire system, rather than just restricted access to certain files in your home directory, which gives Windows applications, including bad things like viruses and other malware, the ability to alter and break your Linux system. Additionally, using root or sudo permissions changes the ownership of the .wine directory where your Windows applications are installed, preventing you from running them as a normal user and producing that "wine is not owned by you" message.

As for your problems, I probably should have suggested this from the start, but you should check Wine's Application Database to see if Works... works in Wine, which it doesn't: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=380](http://appdb.winehq.org/objectManager.php?sClass=application&iId=380)

On the security front, Linux, unlike Windows, takes the stance that it is usually better to be secure than convenient, hence why Linux is generally "safer" to use than Windows. In this particular circumstance, that security only affects Windows applications, since Linux applications on CD will already have the necessary permissions set to run normally (or already require root/sudo permission to run in the first place). The general rule with Linux is it is always better to use a native application whenever possible over "shoehorning" a Windows application into Linux with Wine, which means the vast majority of Linux/Ubuntu users are probably never going to run into the security problems that we Wine tinkerers have to deal with, so it's really not much of a concern for the Ubuntu devs.

---

### Post by carusoswi on 2011-03-12
> **cogadh said:**
> 

As for your problems, I probably should have suggested this from the start, but you should check Wine's Application Database to see if Works... works in Wine, which it doesn't: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=380](http://appdb.winehq.org/objectManager.php?sClass=application&iId=380)


. . . and I probably should have been more clear that running MSWks 2001 from Ubuntu was not new for me, only new in versions 10 of Ubuntu.  I never had a problem before.

The link still seems like a mixed bag to me, but, whatever.
Thanks again.

Caruso

---

### Post by carusoswi on 2011-03-12
> **mark bower said:**
> I ran into the EULA problem the same as you.  There is an "O.K." at the bottom of the EULA pop-up, but clicking on it does nothing.  I had to close the window/terminal.  However, without apparently accepting the agreement, everything worked just fine.

mark bower

Just guessing, but there probably is some .exe buried in there somewhere that isn't 'permissioned'.  I'm going to keep fiddling to see if I can get it to work.

Caruso

---

