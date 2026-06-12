---
title: "Any people with fresh 11.10 installation having problems?"
date: 2011-10-17
forum: Testimonials &amp; Experiences
---

### Post by Meelad on 2011-10-17
I have noticed that a LOT (in fact most) of the threads about the 11.10 problems were made by people who UPGRADED to 11.10, and didn't do a fresh installation..

I for one did a fresh installation (because I'll never upgrade Ubuntu after a few lessons I learned in the past) and I don't seem to have all those horrible problems many seem to have.. So I was wondering if that was down to the fact that I did a fresh installation and didn't upgrade my existing system like many did here, or is it due to some other reasons..

Can I have some input please from people who did fresh 11.10 installation.. How did it go for you??

---

### Post by dave0109 on 2011-10-17
I actually did a fresh installation for the first time, well, second time to be pedantic.  Ever since 8.04 I've always done an upgrade and apart from the odd minor issue, I've not had many problems.

This time though, with the change from Gnome2 to 3, I decided a fresh install was probably for the best.  Once again I had wifi problems, which I seem to hit every 6 months, but other than that there was nothing major, a few UI issues, but I don't know if these were specific to my machine or general bugs.  I've gone right off the UI though, but that's another thread. ;)

---

### Post by mörgæs on 2011-10-17
I have been with Ubuntu from 5.10 to 10.10, and now I continue with Xubuntu. Have not had one successful online upgrade during the years, and now I don't even bother trying.

My schedule is 
[LIST]
[*]install every other release 
[*]install at least three months after the official day of release
[*]use wired internet access while installing
[/LIST]

Always works!

---

### Post by Frantic_Earthling on 2011-10-17
Fresh and smooth install here.
No particular problems on my Asus M70Vn.
Everything works, including function keys.
Only a minor hitch: I lost system sounds yesterday for no reason.
I have sound with audio and video, though.

---

### Post by Blodskaal on 2011-10-17
I've somehow ended up with something that is slower than my Windows 7. Which is quite an amazing feat. 
I shall share my login experience with you: 

[LIST=1]
[*]I type my password and hit enter.
[*] *Crickets*
[*](About 30 seconds in.) My background loads.
[*]My WiFi connection notification pops up saying that the connection to my home network has been established.
[*]*Crickets*
[*](Now about 45 seconds in.) A menu bar loads [File|Edit|View|Go|Bookmarks|Help]
[*]That's it.
[/LIST]
I can infer from hotkeys and graphical effects that Compiz must be running. However no shell is loaded. I tried to run Unity from command line, but it hangs and doesn't do anything. Also the infernal thing reverted my terminal hotkey to <Ctrl>+<Alt>+T. I can run everything I want from terminal perfectly fine, but I still find the lack of shell annoying. Mostly because I used to regularly check the CPU frequency scaling applet and System Monitor applet.

EDIT: I'm now running Gnome 3 shell which is good looking but ridiculously non-customisable.

---

### Post by aeronutt on 2011-10-17
Fresh install, working pretty good. Here's what didn't work out of the box, or still doesnt work:
- Had to add some kernel options to get the power down to where it was on 11.04. 
- None of the gnome-shell extensions that worked on 11.04 work on 11.10. 
- LibraOffice crashes when trying to copy, the fix is to turn off anti-aliasing.

Now, some things that have never worked on my laptop with Ubuntu, that I was hoping would get fixed in 11.10 but haven't:
- Can't switch between discrete graphics and integrated graphics, and can't use discrete graphics at all (ATI HD).
- trackpad works, but isn't recongized as a trackpad, so I can't change settings.
- screen brightness isn't persistent between reboots.
- no driver for finger print reader.
- hibernate doesn't work

---

### Post by 23dornot23d on 2011-10-17
> 
- None of the gnome-shell extensions that worked on 11.04 work on 11.10. 
Possible answer to this is the webupd8 PPA .... they updated 2 days back ......

[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

things are starting to work now ..... 

[http://www.webupd8.org/2011/10/gnome-shell-dock-and-alternative-status.html](http://www.webupd8.org/2011/10/gnome-shell-dock-and-alternative-status.html)

Some are working now .....

Mine is all up and running but I never use the automated upgrade

---

### Post by aeronutt on 2011-10-17
> **23dornot23d said:**
> Possible answer to this is the webupd8 PPA .... they updated 2 days back ......

[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

things are starting to work now ..... 

[http://www.webupd8.org/2011/10/gnome-shell-dock-and-alternative-status.html](http://www.webupd8.org/2011/10/gnome-shell-dock-and-alternative-status.html)

Some are working now .....

Thanks, I figured they'd be hot on the trail!
(Maybe these can help me debug some of the 'non-official' extensions I'd gathered up and were using on 11.04.)

---

### Post by D00mM4r1n3 on 2011-10-17
I did a fresh install in the latest version of VMWare Player, including the VMWare tools installation that Player prompts to do. During installation there was an error about sound hardware failing to be detected and when installation was done I was dumped at a command prompt asking for login.

Thankfully, I've had enough experience with Linux command lines to know to do "sudo reboot" to get it to reboot, I figure it must have simply needed to reboot to load whatever drivers VMWare had installed. Sure enough, after rebooting it loaded to a proper GUI login screen.

Once I was logged in I found that it had loaded a Realtek audio driver (presumably some VMWare default?) and all I had to do was tell VMWare to connect the sound hardware to get sound working. Everything was working fine. I was even amazed to see that running automatic updates didn't kill the installation the way it had the last two major Ubuntu releases (for me). 

The only real problem i'm having is Ubuntu One being slower to sync files than any dial-up modem connection I ever had. ](*,)

---

### Post by anton706 on 2011-10-17
I installed fresh ubuntu 11.10 and after a few hours I decided it was a mistake it is the most buggy linux version I have ever used.Unity feels very sluggish.while using Ccsm Unity crashed and I could not find a solution that would start unity again.I have tried to use gnome-shell and I was disappointed because I had to do a lot of googling to do simple things that should be there (like simply changing the theme),after that I better understood that gnome-shell just not ready yet maybe in 1 year from now it will be ok but today it is not something I would to someone recommend to use.
After all of that I decided to give linux mint 11 a second try(the first was a few month ago and it was horrible) and it was surprisingly good so I decided to stick for now.

---

### Post by Meelad on 2011-10-17
> **anton706 said:**
> I installed fresh ubuntu 11.10 and after a few hours I decided it was a mistake it is the most buggy linux version I have ever used.Unity feels very sluggish.while using Ccsm Unity crashed and I could not find a solution that would start unity again.I have tried to use gnome-shell and I was disappointed because I had to do a lot of googling to do simple things that should be there (like simply changing the theme),after that I better understood that gnome-shell just not ready yet maybe in 1 year from now it will be ok but today it is not something I would to someone recommend to use.
After all of that I decided to give linux mint 11 a second try(the first was a few month ago and it was horrible) and it was surprisingly good so I decided to stick for now.

[http://ubuntuforums.org/showpost.php?p=11358070&postcount=13](http://ubuntuforums.org/showpost.php?p=11358070&postcount=13)

---

### Post by thatguruguy on 2011-10-17
> **anton706 said:**
> while using Ccsm Unity crashed and I could not find a solution that would start unity again.

Try this:
[http://ubuntuforums.org/showthread.php?p=11344537#post11344537](http://ubuntuforums.org/showthread.php?p=11344537#post11344537)

---

### Post by Carborundum on 2011-10-17
I did a fresh install of Ubuntu 11.10, but almost immediately ran into bugs #832159, #837004 and #873482, none of which were present in Natty. This resulted in me installing Xubuntu 11.10 instead, since I had wanted to test it for a while anyway.

So far I like it, although a do miss Unity a little. And unfortunately #873482 is present in Xubuntu as well.

---

