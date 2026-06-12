---
title: "Will linux distros ever.."
date: 2006-06-26
forum: The Cafe
---

### Post by drfalkor on 2006-06-26
be infected with viruses some day ? is it posible to do so ?

---

### Post by FISHERMAN on 2006-06-26
[QUOTE=drfalkor]be infected with viruses some day ? is it posible to do so ?[/QUOTE]
There are already virusses for GNU/Linux, but you shouldn't be to worried about them.

Only if most users start using Root as default(like in Windows) viruses will become a serious problem(an even then only the ones who run Root as default will suffer from them).

---

### Post by G Morgan on 2006-06-26
[QUOTE=FISHERMAN]There are already virusses for GNU/Linux, but you shouldn't be to worried about them.

Only if most users start using Root as default(like in Windows) viruses will become a serious problem(an even then only the ones who run Root as default will suffer from them).[/QUOTE]

A false perception a virus can destroy home quite easily even in a limited account. The best method is ensuring you use only trustworthy sources. If it doesn't come directly from an absolutely reputable source then you should only use source code. If Linux users take a few simple steps then we can maintain this position where the Windows car is easier to steal so more inviting to the crook.

---

### Post by woedend on 2006-06-26
I agree with G Morgan.  I make every file I plan on keeping unwriteable to anyone but root.  This way I can listen to songs, watch movies, read my term papers...but to delete them I must make an effort...and no short script will change that.
The one thing I fear about sudo is that it saves the PW for so long.  Just being paranoid, but what if you were to run a sudo command, then 2 minutes later run a script that called for sudo rm -rf /.... or even you run a sudo command, then get up and someone else runs to the comp.
it wouldn't ask for a password no?

---

### Post by Kvark on 2006-06-26
The administrator is more important to security then the operating system.

A good administrator will configure the security correctly, set up firewall, limited accounts everyday usage, antivirus and anything else thats needed to keep a system secure no matter if it is Windows or Linux.

A clueless administrator will give everyone admin accounts, share folders incorrectly so all internet has access to them, use "fart" as password everywhere and download "Free screensaver!", "Funny game!!", "Friendly virtual pet!!!" plus everything else that looks funny. That'll put any system at great risk no matter if it is Windows or Linux.

Edit: Oh, and even without root access a virus can still spy on the user to steal passwords and credit card numbers.

---

### Post by BoyOfDestiny on 2006-06-26
[QUOTE=woedend]I agree with G Morgan.  I make every file I plan on keeping unwriteable to anyone but root.  This way I can listen to songs, watch movies, read my term papers...but to delete them I must make an effort...and no short script will change that.
The one thing I fear about sudo is that it saves the PW for so long.  Just being paranoid, but what if you were to run a sudo command, then 2 minutes later run a script that called for sudo rm -rf /.... or even you run a sudo command, then get up and someone else runs to the comp.
it wouldn't ask for a password no?[/QUOTE]

Actually, if you are worried, just lock the screen if you are going to step away for a bit... 

(for the newer people :) ):
System -> Quit -> Lock Screen.

---

### Post by patrick295767 on 2006-06-26
[QUOTE=drfalkor]be infected with viruses some day ? is it posible to do so ?[/QUOTE]

[http://www.safenetworks.com/Linux/modules.html](http://www.safenetworks.com/Linux/modules.html)

---

### Post by G Morgan on 2006-06-26
[QUOTE=BoyOfDestiny]Actually, if you are worried, just lock the screen if you are going to step away for a bit... 

(for the newer people :) ):
System -> Quit -> Lock Screen.[/QUOTE]

I bound <Ctrl>+<Alt>+L to lock screen in System ->Preferences->Keyboard Shortcuts. Key bindings are great though you really have to use gconf-editor to get the most out of them.

---

### Post by bruce89 on 2006-06-26
It is very difficult, as there are loads of distributions, and with this new [GCC-SSP]("https://launchpad.net/distros/ubuntu/+spec/gcc-ssp") buffer overflow protection, it makes things even harder.

---

### Post by Brunellus on 2006-06-26
[QUOTE=patrick295767][http://www.safenetworks.com/Linux/modules.html](http://www.safenetworks.com/Linux/modules.html)[/QUOTE]
note that that's for 2.1.x kernels.  We're up to 2.6.x now;  I'm pretty sure this has been addressed?

If not, the lesson is once again:  DON'T RUN STRANGE PROGRAMS.  especially if they're kernel modules.

---

### Post by richbarna on 2006-06-26
"There are about 60,000 viruses known for Windows, 40 or so for the Macintosh, about 5 for commercial Unix versions, and perhaps 40 for Linux. Most of the Windows viruses are not important, but many hundreds have caused widespread damage. Two or three of the Macintosh viruses were widespread enough to be of importance. None of the Unix or Linux viruses became widespread - most were confined to the laboratory."

[Source of text]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/")

---

### Post by bruce89 on 2006-06-26
I like the scanning that Coverity is doing - [http://scan.coverity.com/](http://scan.coverity.com/) - [http://news.zdnet.co.uk/software/applications/0,39020384,39261434,00.htm](http://news.zdnet.co.uk/software/applications/0,39020384,39261434,00.htm)

---

### Post by aysiu on 2006-06-26
When people talk about security, there are several dangers that are not spoken about explicitly as separate categories:

1. Functionality
If some kind of malware renders your system unfunctional, that's a pain to fix, but at least you're immediately aware of the problem and can usually fix it with a reinstall.

It would be just as disastrous, though, for most single-user computers to have the entire /home directory deleted as the systemwide files corrupted or deleted somehow.

2. Time suckage
Likewise, some kind of program that slows your system down by adding in extra services or using your system as a zombie to send emails out does not need root privileges necessarily.

3. Privacy
Most private data (except your Ubuntu password) would probably live in your /home directory, so... again, root access is not required to make things annoying, either with people snooping through your private data or deleting it.

4. Archiving
Same deal. Your music may not be "private," but you don't want it erased or corrupted. I think woedend's approach is not very typical.

So, as you can see, someone or some program breaching your system can do serious damage to you--root privilege or not.

The only advantage to the root/user model from a virus security standpoint is that damage is contained--it may still damage **a lot**, but it won't damage everything.

And if you have a multi-user environment, if one user's compromised, the other users' data will probably be intact...

---

### Post by patrick295767 on 2006-06-27
[QUOTE=Brunellus]note that that's for 2.1.x kernels.  We're up to 2.6.x now;  I'm pretty sure this has been addressed?

If not, the lesson is once again:  DON'T RUN STRANGE PROGRAMS.  especially if they're kernel modules.[/QUOTE]
  
Is the risk higher since everthg is open sources based ? Is there some risks of having some intruders code ? Is there some policy in checkgin every single line code of all apps that are widely available on the net? :-k  (Trusting or Checking everythg ?)

Dont know...
  
This is nice indeed : [http://scan.coverity.com/](http://scan.coverity.com/)

---

### Post by bruce89 on 2006-06-27
[QUOTE=patrick295767]Is the risk higher since everthg is open sources based ? Is there some risks of having some intruders code ? Is there some policy in checkgin every single line code of all apps that are widely available on the net? :-k  (Trusting or Checking everythg ?)[/QUOTE]
Open source is not like a wiki.  Anyone can write a patch, and send it to the developers, but they check it prior to merging it with the trunk code.  Only a small handful of people get write access to the source repository, and the people who get this access will have to have contributed lots of time and code to the project.

---

### Post by G Morgan on 2006-06-27
Talking about saving your home directory. I'm going to buy a 500GB HDD and have a partition not mentioned in fstab as an archive. I think I will go for making it root only as well.

An interesting security setup I saw was someone using DSL and running everything in a VM. Firstly the DSL can be stripped down to such a level that there are few areas of attack and the resources it uses is minimal (prehaps Gentoo is a better option here) then run everything in a VM. The advantage of this is backing a VM up is as simple as copying a directory and by stripping down and hardening your host the chances of that being hacked is minimal. You could even go futher and put /home on a seperate HDD image so you only need backup that regularly and prehaps the entire system on a monthly basis.

---

### Post by hizaguchi on 2006-06-27
[QUOTE=woedend]I agree with G Morgan.  I make every file I plan on keeping unwriteable to anyone but root.  This way I can listen to songs, watch movies, read my term papers...but to delete them I must make an effort...and no short script will change that.[/QUOTE]
That's a really good idea.  Do you have any easy way of doing that?  A Nautilus script or anything?

---

### Post by patrick295767 on 2006-06-28
[QUOTE=hizaguchi]That's a really good idea.  Do you have any easy way of doing that?  A Nautilus script or anything?[/QUOTE]
  
I do similar thing too. I have specific folders for this. Hence, I would recommand you to do a daily reboot of ur server/pc/os & then start a daily script(s) taht will do update/upgrade, e2fsck, ... and also taking care of these rights via an appropriate chmod -R ... 
  
I am still thinking about making DVD backup's kind of periodically of the partition having the home or imprtt files/folders, ... still to be done... like the 1st of the month, you slot in a dvd before going to bed ... for instance.;-) 
  
[CENTER]**Linux Is Great !!**[/CENTER]

---

### Post by hizaguchi on 2006-06-28
I've got a laptop, so the daily script isn't really good for me.  I was thinking something like a Nautilus script that lets you right-click a file or group of files and move/chown them all at once by just putting in your root password.  This way, for example, when I copy new pictures from my digital camera I could just select them all and hit my script button to have them all moved to a protected pictures folder and become root property.  Hey, I like this.  I might have to go learn to write scripts now. :)

---

### Post by aysiu on 2006-06-28
A switch to KDE is probably a bit drastic, but in case anyone's curious, Konqueror does have this feature--you can right-click a file and select **Edit as root**.

---

### Post by hizaguchi on 2006-06-28
[QUOTE=aysiu]A switch to KDE is probably a bit drastic, but in case anyone's curious, Konqueror does have this feature--you can right-click a file and select **Edit as root**.[/QUOTE]
Blah, don't give me more reasons to love KDE.  I'm stuck with Gnome until Firefox and OpenOffice become QT apps.  Well, that or until my computer gets tired of being a piece of crap and uses my personal information to order itself some upgrades.

---

### Post by aysiu on 2006-06-28
You could run Konqueror in Gnome... though, that would be kind of ugly.

---

### Post by hizaguchi on 2006-06-28
Yeah, but when I start using Konqueror and Kate and Amarok and Kopete all at the same time things are going to get sluggish.  Same way as when I use Firefox, Gimp, and OpenOffice in KDE.  One app at a time isn't bad, but when are you ever just using one application?  I really wish they'd commonize the toolkits or something.

---

