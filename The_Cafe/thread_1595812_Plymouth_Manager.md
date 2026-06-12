---
title: "Plymouth Manager"
date: 2010-10-13
forum: The Cafe
---

### Post by Mefrio on 2010-10-13
Hello everyone people!

I am an italian Ubuntu user and a member of my national community

maybe my English is not very good, but forgive me :)

I created a software wich can configure your plymouth! It is very easy and is localizated in english and italian!

Here there is the download
[https://sourceforge.net/projects/plymouthmanager/](https://sourceforge.net/projects/plymouthmanager/)

I hope you enjoy it :)

---

### Post by Mefrio on 2010-10-13
sorry, i post it in incorrect section! Sorry

---

### Post by cariboo on 2010-10-13
Moved to the Cafe.

---

### Post by praveenthivari on 2010-10-13
How to install this. Please provide documentation.

---

### Post by -Robert- on 2010-10-13
You can find a deb file on that page.
Direct link: [http://sourceforge.net/projects/plymouthmanager/files/plymouth-manager_0.5.3.deb/download](http://sourceforge.net/projects/plymouthmanager/files/plymouth-manager_0.5.3.deb/download)

---

### Post by nilarimogard on 2010-10-14
Your applications has text in both English and Italian (in the same time)... is there any chance you could make an English-only version?

---

### Post by NightwishFan on 2010-10-14
Actually that looks like a really cool program. With a little love it might turn out to be awesome. Nice job.

---

### Post by opendevlite on 2010-10-14
does this fix the plymouth problem in 10.04 my plymouth shows up a few seconds and disappears, comes back again with the plymouth and opens my desktop

---

### Post by chriswyatt on 2010-10-14
> **opendevlite said:**
> does this fix the plymouth problem in 10.04 my plymouth shows up a few seconds and disappears, comes back again with the plymouth and opens my desktop

Only thing I can see on it that might do that is the install v86d package button.  But I dunno.

Nice program though, just needs a fair bit of tidying up but a Plymouth Manager is definitely something that's needed.  I prefer using GUIs and find editing configs a bit of a pain.

A few criticisms which probably aren't helpful at this early stage of development:

Lots of white space
Mixture of two languages
And the general positioning of things, things on the left when I expect them on the right etc.

Otherwise really good.

---

### Post by NightwishFan on 2010-10-14
Perhaps take a look at this guide for reference on GUI layouts.
[http://library.gnome.org/devel/hig-book/](http://library.gnome.org/devel/hig-book/)

---

### Post by Mefrio on 2010-10-14
> **opendevlite said:**
> does this fix the plymouth problem in 10.04 my plymouth shows up a few seconds and disappears, comes back again with the plymouth and opens my desktop
no unfortunately the plymouth, sometimes, is very strange!


chriswyatt a my friend make me the new mockup for Plymouth Manager! An example here
[http://upload.centerzone.it/viewer.php?file=76346976484875367767.png](http://upload.centerzone.it/viewer.php?file=76346976484875367767.png)
and now i am at work

Can you make a screenshot of the PM in your computer? I would see the misture of language

EDIT
I have identified the "language bug" and i corrected it! In the new versione it won't be in the programm

---

### Post by Oxwivi on 2010-10-14
I added a bit of info and link about Plymouth Manager on [Plymouth's page at Wikipedia]("http://en.wikipedia.org/wiki/Plymouth_%28software%29"). :D

---

### Post by Mefrio on 2010-10-15
Thank you very much :)

---

### Post by Mefrio on 2010-10-17
I have released a new version of my software! It haven't the language bug ang it is better than the older version

---

### Post by nilarimogard on 2010-10-17
> **Mefrio said:**
> I have released a new version of my software! It haven't the language bug ang it is better than the older version

It still has 2 bugs:

1. The script you run to fix the Plymouth has some errors. See a fixed version [here]("http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html").

2. When installing Plymouth Manager in Ubuntu, each time you try to install a package you'll get an error like this:


```
Processing triggers for menu ...
In file "/usr/share/menu/plymouth-manager", at (or in the definition that ends at) line 4:
?package(plymouth-manager):needs="X11" section "Applications/System/Administration" title="Plymouth Manager" command="/usr/bin/plymouth-manager.gambas" icon="/usr/share/pixmaps/plymouth-manager.png"
                                               ^
Expected: "="
```

The fix is to edit /usr/share/menu/plymouth-manager and change:
```
section "Applications/System/Administration"\

```
to:
```
section="Applications/System/Administration"\

```

---

### Post by Mefrio on 2010-10-18
in the latest version, 0.5.5, some people tested my script and it functioned!

the second bug is very strange...nobody had this problem!

if there are new people who will have the same bug I'll try some solutions! Now you are only person whit this problem

---

### Post by nilarimogard on 2010-10-20
> **Mefrio said:**
> in the latest version, 0.5.5, some people tested my script and it functioned!

the second bug is very strange...nobody had this problem!

if there are new people who will have the same bug I'll try some solutions! Now you are only person whit this problem

The script does a lot of stuff so it may work for some. If you know a bit of bash, take a look at it and you'll see it cannot fully work (it doesn't do everything it's supposed to, only part of it because it's badly written). Use the script I wrote about...

---

### Post by nilarimogard on 2010-10-20
I see you also didn't fix the desktop file bug even though I told you exactly how to fix it... I'm giving up on this.

---

### Post by NightwishFan on 2010-10-20
> **nilarimogard said:**
> I see you also didn't fix the desktop file bug even though I told you exactly how to fix it... I'm giving up on this.

Fork it! :D

---

### Post by Mefrio on 2010-10-20
@nilarimogard

sorry but i don't understand what is the bug! I haven't any problem!

What is your script?
[This?]("http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html")

---

### Post by Lucradia on 2010-10-20
> **Mefrio said:**
> [http://upload.centerzone.it/viewer.php?file=76346976484875367767.png](http://upload.centerzone.it/viewer.php?file=76346976484875367767.png)

**[SIZE="5"]MySQL Driver Error[/SIZE]**

The requested page could not be loaded because a fatal error has occurred. 
Sometimes this error is temporary and will go away when you refresh the page. 

You can try to refresh the page by clicking here. 

If this error page continues to appear after refreshing, then try
contacting the server administrator at: [email]postmaster@upload.centerzone.it[/email].

---

### Post by Mefrio on 2010-10-21
> **Lucradia said:**
> **[SIZE="5"]MySQL Driver Error[/SIZE]**

The requested page could not be loaded because a fatal error has occurred. 
Sometimes this error is temporary and will go away when you refresh the page. 

You can try to refresh the page by clicking here. 

If this error page continues to appear after refreshing, then try
contacting the server administrator at: [email]postmaster@upload.centerzone.it[/email].
sorry but my friend removed the .png! I don't know why! I ask you it

---

### Post by NightwishFan on 2010-10-21
Keep up the work Mefrio I like your software. It could become a great tool. :)

---

### Post by Lucradia on 2010-10-21
> **Mefrio said:**
> sorry but my friend removed the .png! I don't know why! I ask you it

I'm not going to check it out until I can see a screenshot of what I'll be getting into.

---

### Post by Megaptera on 2010-10-21
I hope these screenshots work?

---

### Post by JOHNNYG713 on 2010-10-21
I seem to get an error that points to missing X11while updating, and the program crashes while trying to make my own Plymouth!

---

### Post by Lucradia on 2010-10-21
> **Megaptera said:**
> I hope these screenshots work?

Isn't restricted drivers a jockey thing, and not a plymouth thing? :-k

---

### Post by Megaptera on 2010-10-21
> **Lucradia said:**
> Isn't restricted drivers a jockey thing, and not a plymouth thing? :-k

No idea ..... I was just posting some piccies as you requested.

---

### Post by Lucradia on 2010-10-21
> **Megaptera said:**
> No idea ..... I was just posting some piccies as you requested.

One of the reasons why I don't use apps like these: No real definitive screenshots, useless features that other apps--that are already installed--provide, etc.

---

### Post by Megaptera on 2010-10-22
To be fair this is one person developing an app so it's only to be expected that the 'advertising' and presentation are a little less polished. I guess the developer is rightly concentrating mainly on the product for now?

I think the important thing is does it do what it's supposed to do (and un-do) safely and properly. So the more people that run it the more feedback there will be.

---

### Post by Mefrio on 2010-10-22
people i have only a real life:)

I release the 0.5.7 with the correction of the nilarimogard's bug

Now is only a manual soluction! 



> **Lucradia said:**
> One of the reasons why I don't use apps like these: No real definitive screenshots, useless features that other apps--that are already installed--provide, etc.

sorry but i don't understand you

---

### Post by Mefrio on 2010-10-22
EDIT:
bad post

---

### Post by Mefrio on 2010-10-22
...

---

### Post by Lucradia on 2010-10-22
> **Mefrio said:**
> sorry but i don't understand you

Remove the restricted drivers tab, and all related code to it, it's not needed; jockey-gtk provides us with this already, and is installed by default in ubuntu when you login.

---

### Post by Mefrio on 2010-10-22
the tab don't search the driver for my hardware but it can configure the Plymouth with the closed NVidia/ATI drivers

---

### Post by Lucradia on 2010-10-22
> **Mefrio said:**
> the tab don't search the driver for my hardware but it can configure the Plymouth with the closed NVidia/ATI drivers

Why is it named restricted drivers then? Name it "Compositing Effects"

---

### Post by Mefrio on 2010-10-23
> **Lucradia said:**
> Why is it named restricted drivers then? Name it "Compositing Effects"

Why? I don't understand you...probably you don't understand the main function of the tab

---

### Post by lightningfox on 2010-10-27
Hi 

Thanks for the Plymouth manager. I'm trying it.

I have some requests:


Is it possible to rewrite it in Python? Not everyone has Gambas installed whereas Python comes pre-installed with Ubuntu.

Also could you change it so it doesn't depend on Qt and KDE?

---

### Post by Mefrio on 2010-10-28
yes, it is possible but is not useful! The Plymouth Manager doen't request any dependencies! It doesn't requier the Gtk and it doesn't requir the Qt! For me, Gambas, for this, is the best solution ;)


People in the future versions of the PM there will be some news! An interesting news is the configuration editor! 

I write a simple editor to change manually the configuration of the plymouth...here a screenshot

[http://img35.imageshack.us/img35/8061/schermatamf.png]("http://img35.imageshack.us/img35/8061/schermatamf.png")

---

### Post by Mefrio on 2010-11-04
people the current versione of the PM is very complete!

Now the combobox in the first tab is "inteligent", there is a mini-software for the info about the resolution and there is a personal editor to configure the config file manually

---

### Post by NightwishFan on 2010-11-04
It sounds cool, I will have to give it a go. :)

---

### Post by Mefrio on 2010-11-05
ok thank you:)

---

### Post by grahammechanical on 2010-11-05
Mefrio

I wish you well. Something like your program/utility is very useful. Some of us are not confident about editing configuration files that work directly on loading the operating system. I am not confident about doing this. We need utilities that do all the work for us. Thank you for your efforts on behalf of the community.

Regards

---

### Post by Mefrio on 2010-11-05
I hope that this is a compliment:)

sorry if my english isn't very well

---

### Post by NightwishFan on 2010-11-05
It is. Keep it up and get the software into Ubuntu universe repository! :)

---

### Post by Mefrio on 2010-11-06
it is my dream:)

how can I send a request to the Ubuntu developers to include Plymouth Manager into the universe repository?

---

### Post by NightwishFan on 2010-11-06
I am not sure, perhaps you can ask someone on launchpad.net.

---

### Post by Mefrio on 2010-11-07
ok but i don't know who is an ubuntu developer..is there Mark on Launchpad?:P

---

### Post by inobe on 2010-11-07
> **Mefrio said:**
> ok but i don't know who is an ubuntu developer..is there Mark on Launchpad?:P

[http://www.ubuntu.com/community](http://www.ubuntu.com/community)

[https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment)

---

### Post by Mefrio on 2010-11-07
thank you....I found Mark Shuttleworth on Launchpad and i wrote a little email to him

---

### Post by NightwishFan on 2010-11-07
To be honest I think that is not prudent as he does not manage all the requests himself. Though the correct answer is above.

---

### Post by Oxwivi on 2010-11-07
Start with a PPA.

---

### Post by Mefrio on 2010-11-07
the work for a ppa is in progress

---

### Post by Mefrio on 2010-11-10
people i have released the version 0.7.3! In this version i corrected some bugs and i add the "online support" with the new official blog of the project

Here the blog
[http://plymouthmanager.wordpress.com/](http://plymouthmanager.wordpress.com/)

---

### Post by NightwishFan on 2010-11-10
Hey thats pretty cool, you are doing a nice job. :) I have not had time to check it out lately myself though because of working on my music.

---

### Post by Mefrio on 2010-11-10
oh you are a musician:)good!

I am a pianist :guitar:

---

### Post by Mefrio on 2010-11-13
people in the version 0.7.4 there is the fix of the bug of the /usr/share/menu/plymouth-manager file

[http://plymouthmanager.wordpress.com/2010/11/13/plymouth-manager-0-7-4/](http://plymouthmanager.wordpress.com/2010/11/13/plymouth-manager-0-7-4/)

---

### Post by Vu1kan on 2010-11-14
Hiya-
I just installed your manager...looks spiffy, but have you updated it for grub2?  I get this error when i run it: "file /etc/default/grub non trovato, sei sicuro che stai utilizzando grub?" = file /etc/default/grub not found, you're sure you're using grub? (translated via google translate)

---

### Post by NightwishFan on 2010-11-14
/etc/default/grub is grub2.

---

### Post by Vu1kan on 2010-11-14
my bad, i ment to say, is it compatible with grub/grub1.5(the grub you get when you update to 10.04 from pre 9.1 releases)?

---

### Post by Jechem on 2010-11-14
> **Mefrio said:**
> people i have released the version 0.7.3! In this version i corrected some bugs and i add the "online support" with the new official blog of the project

Here the blog
[http://plymouthmanager.wordpress.com/](http://plymouthmanager.wordpress.com/)

I've tried your software. Its better than having to edit the scripts. I've includedmitto my blog in case some people read my other post on how to change the splash.
[http://jechem.blogspot.com/2010/11/cool-plymouth-manager-for-ubuntu-with.html](http://jechem.blogspot.com/2010/11/cool-plymouth-manager-for-ubuntu-with.html)

---

### Post by Mefrio on 2010-11-14
> **Jechem said:**
> I've tried your software. Its better than having to edit the scripts. I've includedmitto my blog in case some people read my other post on how to change the splash.
[http://jechem.blogspot.com/2010/11/cool-plymouth-manager-for-ubuntu-with.html](http://jechem.blogspot.com/2010/11/cool-plymouth-manager-for-ubuntu-with.html)

thank you

people the PM is compatible with grub 1 and grub 2! It, sometimes, can work with burg too...

---

### Post by Yougo on 2010-11-18
Plymouth manager sounds great!

does it sort out plymouth-nvidia troubles in Maverick too? i've tried all i can think of, and there's just no love between them it seems...

---

### Post by Jechem on 2010-11-18
I read this fix for nvidia drivers for 10.10
[http://www.*****************/driver/articles/fix-nvidia-graphics-driver-problems-in-ubuntu-10-10.html](http://www.*****************/driver/articles/fix-nvidia-graphics-driver-problems-in-ubuntu-10-10.html)
I'm not sure if this is helpful to you.

---

### Post by Yougo on 2010-11-18
not very helpful since you x-ed out the actual URL, but thanks for the gesture :P

---

### Post by Jechem on 2010-11-18
*****************/driver/articles/fix-nvidia-graphics-driver-problems-in-ubuntu-10-10.html
website is downloadatoz(dot)com

---

### Post by Yougo on 2010-11-18
thanks, but that site tells about disabling kernel mode setting to allow ubuntu to boot up after installing NVIDIA drivers.

my computer boots fine, NVIDIA works great. the problem here is Plymouth not playing nice. 

the only remotely useful thing i'd get out of that site is the nomodeset option, which is both old and the least of the problems.

---

### Post by Jechem on 2010-11-18
> **Yougo said:**
> thanks, but that site tells about disabling kernel mode setting to allow ubuntu to boot up after installing NVIDIA drivers.

my computer boots fine, NVIDIA works great. the problem here is Plymouth not playing nice. 

the only remotely useful thing i'd get out of that site is the nomodeset option, which is both old and the least of the problems.

Sorry my bad.;) 
Here is another one which deals with 10.04 but could be applicable to 10.10 and lists specific problem encountered
[Problems/Symptoms/Why-Are-You-Here]
Plymouth splash screen…
is in low res mode.
has corrupted graphic
is decent but can’t switch to virtual terminal or VT is horribly in low res mode
is decent but the splash screen only appears for a brief 1-2 second ( you are missing the dots moving  ), before that you only see a black/blank screen

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by Yougo on 2010-11-19
^that one is old and wrong too, sorry. i've been googling across the intarwebz for a week now, i've seen all that stuff...

...the good news is, the right stuff is -ofcourse- right here in the forums :)

this link tells a very easy setup, that doesn't require multiple obscure 00_header and /modprobe.d/... files (ok just one) and such junk:

[http://ubuntuforums.org/showthread.php?t=1498221](http://ubuntuforums.org/showthread.php?t=1498221)

it worked for me anyways.

---

### Post by Mefrio on 2010-11-21
people I am very engaged in this period but I am working for you :)

With the OpenGL and a friend's help I put in the program a coverflow effect for the themes...

[here]("http://dl.dropbox.com/u/11004864/Plymouth_Manager.gambas") a preview of the next version

---

### Post by NightwishFan on 2010-11-21
Plymouth Manager featured on omgubuntu! :)

[http://www.omgubuntu.co.uk/2010/11/plymouth-manager-lets-you-change-boot-theme-resolution-in-ubuntu/](http://www.omgubuntu.co.uk/2010/11/plymouth-manager-lets-you-change-boot-theme-resolution-in-ubuntu/)

---

### Post by Oxwivi on 2010-11-21
I think I may know the culprit behind this article... ;)

---

### Post by Mefrio on 2010-11-21
the culprit isn't Mefrio :D

---

### Post by Oxwivi on 2010-11-21
I was referring to an OMG! Ubuntu! editor. :)

---

### Post by Mefrio on 2010-11-22
> **Oxwivi said:**
> I added a bit of info and link about Plymouth Manager on [Plymouth's page at Wikipedia]("http://en.wikipedia.org/wiki/Plymouth_%28software%29"). :D

the Plymouth Manager isn't on Wikipedia now...why?

---

### Post by Oxwivi on 2010-11-22
Someone removed it, saying it's unreferenced. [http://en.wikipedia.org/w/index.php?title=Plymouth_(software)&action=history](http://en.wikipedia.org/w/index.php?title=Plymouth_(software)&action=history)

---

### Post by Oxwivi on 2010-11-22
Maybe I'll try referring to the OMG! Ubuntu! article later.

---

### Post by Yougo on 2010-11-25
when i try to make a custom theme, i go to that tab, but clicking on anything in that tab just crashes the plymouth manager :(

the Gnome-Orange theme that came with it was broken for me, but i managed to pull it off of Gnome-Look i believe.

also, will it be able to take downloaded packaged themes and install it for me? maybe drag and drop the package into the preview field, just like in gnome-appearance properties (don't know how hard that is to make, but would be sweet) 

other than that, great stuff! keep it up =D>

---

### Post by TheWitchdoktor on 2010-11-28
It worked great in one of my two computers. However, the other one freezes the whole time and I must reboot. Is there a way to undo all the changes and restore the defaults?

---

### Post by ArunavAm on 2010-11-28
Can anyone say.. I've been facing a problem. I first installed the SPACE SUNRISE theme (Awesome I must say) for plymouth from the plymouth manager.. where it finally asked for choosing between 3 options (Normal Ubuntu boot (auto), *Space Sunrise (1), Ubuntu boot (2)).. I hit ENTER cuz the default 'Space Sunrise' was already selected.. I can now see the beautiful boot.. ***But my problem is.. ***now I want to change the plymouth theme, I install a theme (e.g. SOLAR).. but the new theme is not shown in the plymouth theme selection menu! :O The NORMAL UBUNTU BOOT theme and my first downloaded SPACE SUNRISE theme exists there.. How can I remove the SPACE SUNRISE theme and add a new theme? Not to mention, the pop-up console shows that the new theme is being downloaded, then installed.. and finally.. the theme selection menu. But not the one I am installing.. HELP.. :(

---

### Post by Mefrio on 2010-12-01
TheWitchdoktor

install the default theme


ArunavAm

remove Space Sunrise from Plymouth Manager

---

### Post by Mefrio on 2010-12-04
Hi pleople, I release the Plymouth Manager 0.8.2

Download it;)

you can find the changelog on the project's blog

---

### Post by Mefrio on 2010-12-20
I release the new 0.9.1 version! The changelog is on the the blog

---

### Post by Mefrio on 2010-12-20
I create a ppa for the project...now you can install Plymouth Manager with
```
sudo apt-add-repository ppa:mefrio-g/plymouthmanager && sudo apt-get update && sudo apt-get install plymouth-manager
```

---

### Post by TheWitchdoktor on 2010-12-21
> **Mefrio said:**
> TheWitchdoktor

install the default theme


I've done that but didn't work. Disabling compiz avoids freezing, has it something to do with the changes made by Plymouth Manager?

---

### Post by Mefrio on 2010-12-21
It is very very strange...install the PM with the download of the .deb and remove the ppa

---

### Post by DodgeThis on 2010-12-31
Hi people!

After some system updates(apt-get dist-upgrade) the plymouth manager doesn't load no more... any ideas?

---

### Post by Mefrio on 2011-01-01
do you have some errors?

can to start it in a gnome-terminal with Plymouth_Manager.gambas

---

### Post by DodgeThis on 2011-01-06
> **Mefrio said:**
> do you have some errors?
 
can to start it in a gnome-terminal with Plymouth_Manager.gambas
 
Hi Mefrio! thks for your reply.
 
When i run Plymouth_Manager.gambas under root it gives this error;
```
 
Exist
Segmentation fault 

```
 
any idea?

---

### Post by Mefrio on 2011-01-07
try to start the source code with the gambas IDE because it give you the line with the error!

---

### Post by DodgeThis on 2011-01-10
Hello Mefrio

Unfortunatel my Gambas IDE stops working when debugging the source.( The programa has stopped unexpectedly by raising signal#11).

Is there any log file on the system or plymouth manager that can help?

I'm using virtuallbox and ubuntu 10.10
Thx for your support Mefrio:D

---

### Post by Mefrio on 2011-01-10
probably the problem is virtualbox! Plymouth Manager has an OpenGL animation and it probably don't work with the video driver of the VBox

---

### Post by DodgeThis on 2011-01-10
i'm using compiz effects and plymouth runs space sunrise without problems  on virtualbox so open-gl is not a problem(i think8-[). 
(guest editions and other modules instaled for 3d suport)

---

### Post by Mefrio on 2011-01-11
can you use PM on you pc without use VBox?

---

### Post by pickarooney on 2011-01-16
I installed this earlier on XFCE and set the resolution to 1280x1024 (same as my normal screen resolution). I enabled Plymouth and gave it compatibility ith closed drivers. I then chose the Space Sunrise theme.

When I rebooted I got 5 minutes worth of messages on the screen and then a blue recovery console. Going past that, X failed to start and I got a CLI login. I was able to start X with **startx** but it booted to GNOME instead of XFCE. Same on the next reboot. I can't logout normally. I reopened Plymouth Manager and disabled Plymouth but the problem persists. What can I do to go back to a normal boot?

---

### Post by Mefrio on 2011-01-16
can you post your /etc/default/grub?

---

### Post by Mefrio on 2011-01-16
People I am happy to announce that the version 1.0 of Plymouth Manager is released :D
[Here]("http://plymouthmanager.wordpress.com/2011/01/16/plymouth-manager-1-0-is-here/") the official announcement

---

### Post by Mefrio on 2011-03-08
Hi people I am working on a PyGtk porting of the project! You can find more info [here]("http://plymouthmanager.wordpress.com/2011/03/06/plymouth-manager-1-3-rc/")

---

### Post by Mefrio on 2011-04-14
[LEFT]I released the version 1.5...enjoy it
[/LEFT]

---

### Post by NightwishFan on 2011-04-14
> **Mefrio said:**
> [LEFT]I released the version 1.5...enjoy it
[/LEFT]

Thanks Mefrio, any chance we will see this in the Main repository of Debian?

---

### Post by mpsz on 2011-04-19
Hi, I installed your software from the PPA but I can't start it.
It's not in the menu, how do you run it?
I'm using Ubuntu 10.04 64 bits.

---

### Post by trazalca on 2011-04-23
Me too!! i have maverick 10.10 64 bit, nothing in the main menu...:(

---

### Post by ubun2geek on 2011-09-05
Are all bugs removed? :)
I'd love to give it a second shot provided it doesn't kill me ;)

---

### Post by pierocol on 2011-11-03
Congratulations for this nice tool which makes it much easier to change splash screen.
I hope you can help me. I would like to use the PAW-OSX theme, but it is all stretched because I have a 16:9 display and it is made for 4:3. The resolution of my display (a Samsung LED TV) is 1360x768. What should I do?
Thanks a lot

---

