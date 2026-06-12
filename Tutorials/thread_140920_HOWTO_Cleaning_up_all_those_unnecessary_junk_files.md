---
title: "HOWTO: Cleaning up all those unnecessary junk files..."
date: 2006-03-07
forum: Tutorials
---

### Post by WackToMack on 2006-03-07
**Hello everyone!  So, do you ever get the feeling that your system is being flooded with a bunch of junk files that you can't get rid of?  I know I do.  Well, I'm going to show you a few ways to get rid of most, if not all, of those annoying junk files.** \\:D/ 

**[COLOR="Red"]Please note[/COLOR]** : If doing any of this messes up your system, don't blame me.  Everything worked flawlessly on my machine.  Everthing should be beer 'n skittles for you if you follow this HOWTO step-by-step.  Good luck! :D

========================================================================================================================

_[SIZE="3"]**Tip #1 - Getting rid of Residual Config packages**[/SIZE]_ - In Synaptic Package Manger, there is a built-in feature that gets rid of old Residual Config packages.  Residual Config packages are usually dependency packages that are left behind after you uninstall a package from your machine.  To use this feature, go to **System > Administration > Synaptic Package Manager**.  On the bottom left hand corner of the window, click the **Status** button.  In the list above the **Sections**, **Status**, **Search**, and **Custom **buttons, you should see the following text:

> Installed
Installed (local or obsolete)
Not installed
Residual config
Click on the "Residual config" text. (If the "Residual config dialogue does not appear, that means you do not have any Residual Config packages on your machine and you can skip down to Tip #2.)  Do you see the packages that popped up in the window on the right?  Those are the Residual Config packages.  To get rid of these pests, click on the box to the left of the package name and select "Mark for Complete Removal".  After you have done that for all of the Residual Config packages, look at the top of the Synaptic Package Manger window.  Do you see the green check mark with the text "Apply" right under it?  Click that button, and you'll flush all those Residual Config packages down the toilet! :KS

========================================================================================================================

_[SIZE="3"]**Tip #2 - Getting rid of partial packages**[/SIZE]_ - This is yet another built-in feature, but this time it is not used in Synaptic Package Manager.  It is used in the Terminal.  To access the Terminal, go to **Applications > Accessories > Terminal**.  Now, in the Terminal, key in the following command (or you can just copy and paste from here):

```
sudo apt-get autoclean
```
Enter your password when prompted and press **Enter**.  See the package names that appeared in the Terminal?  Those were partial packages that have just been deleted.  Say goodbye!  That's it!  This command deletes the not-so-fully-downloaded packages that you acquire when a package that is being downloaded is suddenly cancelled.  This is my favorite little trick when it comes to getting rid of junk files. :p 

========================================================================================================================

_[SIZE="3"]**Tip #3 - Getting rid of unnecessary locale data**[/SIZE]_ - For this tip, you need to download the "localepurge" package found in Synaptic Package Manager.  "localepurge" is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.

To open Synaptic Package Manager, follow the instructions in Tip #1.  After opening up Synaptic Package Manager, click the **Sections** button on the bottom left hand corner of the window, if it is not already clicked.  Next, at the top of the Synaptic Package Manager window, click the **Search** button.  In the search window, key in the following text :

> localepurge

Did the "localepurge" package popup in the package window?  It probably did, unless you do not have the correct Repositories.  Now, click on the box next to the "localepurge" package name.  Click on **Mark for Installation**.  Now click the **Apply** button at the top of the window and wait for the downloading and installing of the "localepurge" package to finish.  Once it is done, a new window should popup that has a bunch of abbreviations on it.  for example: 

> en
fr
po
sp
ka
etc...
You want to select the abbreviation of the language that you speak, or use with Ubuntu, ignoring the capitalized ones.  For example, I speak english, so I would select the "en" abbreviation.  A french speaker would select the "fr" abbreviation.  So on and so forth...  Then click next.  All done! ;)

========================================================================================================================

_[SIZE="3"]**Tip #4 - Getting rid of "orphaned" packages**[/SIZE]_ - For this tip, you need to download the "deborphan" package found in Synaptic Package Manager.  "deborphan" finds "orphaned" packages on your system.  It determines which packages have no other packages depending on their installation, and shows you a list of these packages. It is most useful when finding libraries, but it can be used on packages in all sections...

To open Synaptic Package Manager, follow the instructions in Tip #1.  After opening up Synaptic Package Manager, click the **Sections** button on the bottom left hand corner of the window, if it is not already clicked.  Next, at the top of the Synaptic Package Manager window, click the **Search** button.  In the search window, key in the following text :

> deborphan
Did the "deborphan" package popup in the package window?  It probably did, unless you do not have the correct Repositories.  Now, click on the box next to the "deborphan" package name.  Click on **Mark for Installation**.  Now click the **Apply** button at the top of the window and wait for the downloading and installing of the "deborphan" package to finish.  Once that is done, open up the Terminal.  Instructions for doing that are located in Tip #2.  After you have gotten the Terminal open, key in the following command (or copy and paste from here):

```
sudo deborphan | xargs sudo apt-get -y remove --purge
```
Enter your password when prompted and press **Enter**.  See the package names that appeared in the Terminal?  Those were orphaned packages that have just been deleted.  Say goodbye!  This is my second favorite way of dealing with junk files. :cool:

========================================================================================================================

_[SIZE="3"]**Tip #5 - Adding a "Find orphaned packages" to Synaptic Package Manager**[/SIZE]_ - This is not really much of a tip on how to get rid of junk files.  It's more like adding a "deborphan" shortcut to Synaptic Package Manager so that you don't have to use the Terminal to find "orphaned" packages.

**[COLOR="Red"]Please note:[/COLOR]** You must have the "deborphan" package installed or else this will not work.

To start this out, open up Synaptic Package Manager with the instructions from Tip #1.  Now, at the top of the Synaptic Package Manager window, click  the **Settings** button, followed by the **Filters** button.  In the Filters window, on the bottom left hand corner, push the **New** button.  You can name the new Filter if you like, but it is not necessary.  I named mine "Orphaned".  With your new Filter selected, in the "Status" tab on the right, click the **Deselect All** button.  Next, check the "Orphaned" option under the "Other" category.  Then click the **OK** button.

To use this new filter, click the **Custom** button on the bottom left hand corner of the Synaptic Package Manager window.  You should see the following text, or something similiar :

> Broken
Marked Changes
(Whatever you named your "deborphan" Filter)
Package with Debconf
Search Filter
Click on the "(Whatever you named your "deborphan Filter)" text.  Do you see the packages that popped up in the window on the right?  Those are the "orphaned" packages.  To get rid of these buggers, click on the box to the left of the package name and select "Mark for Complete Removal".  After you have done that for all of the "orphaned" packages, look at the top of the Synaptic Package Manger window.  Do you see the green check mark with the text "Apply" right under it?  Click that button, and you'll get rid of all the "orphaned" packages forever (Probably)! :mrgreen: 

========================================================================================================================

Well, I hope all of you enjoyed my HOWTO and found it quite easy to follow.  Whew, this thing took me over an hour to make!  LOL!  If I have made any mistakes, just let me know.  Catch you later! :D

---

### Post by Ferio on 2006-03-08
"Autoclean" is not in the Ubuntu repositories, where could I find it?

---

### Post by alphazero on 2006-03-08
Autoclean is an extension of the "apt-get" command.

To use it type this in the terminal:
sudo apt-get autoclean

Great HOWTO WackToMack, I got rid of many unnecessary language files.

---

### Post by meborc on 2006-03-08
thanks man... i really love when someone gives a GIFT to fellow ubuntians... i'll use all of them :mrgreen:

---

### Post by NMUrugbysteve on 2006-03-08
Good howto, however I don't recommend using tip 4 because it may uninstall packages that one actually wants. For instance it tries to remove all of my gstreamer plugins.

---

### Post by Ferio on 2006-03-09
Yes, somebody replied me via private message; I understood that "autoclean" was a package instead of a parameter. But thanks, anyway!

---

### Post by Sokraates on 2006-03-09
Great HOWTO! And a big thumbs up for explaining readers how to use graphical tools instead of telling them to use the terminal.

Still, I recommend to merge tips 4 and 5 and tell users to take a look at their orphaned packages **before** deleting/purging them. As NMUrugbysteve already stated, people with external repos tend to have orphaned packages they acually need. Also, other packages may depend on an orphaned one.

Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

---

### Post by stalefries on 2006-03-09
Great stuf, although localepurge didn't want to configure correctly. Oh well, everything else worked fine.

---

### Post by Zeroangel on 2006-03-09
I rate this a truly excellent guide!

:KS :KS :KS :KS / 5

---

### Post by e2k on 2006-03-09
Thank you very much for this one, ever since I installed ubuntu I've been wondering if there's an equivalent to emerge --dep-clean (gentoo)! \\:D/

---

### Post by mcwtlg on 2006-03-09
Possibly add "apt-get clean" the list as a partner to autoclean?

---

### Post by henriquemaia on 2006-03-10
Cool Tips. Thanks a lot. I normally use aptitude to install packages to avoid leaving things unused on the system, but as I do sometimes use apt-get/synaptic, there are always things left behind. 

Thanks again.

---

### Post by shof2k on 2006-03-12
Cool guide.  You can also use deborphan with a GUI by installing GTKorphan.

---

### Post by xyz on 2006-04-05
Hi,
Thanks for the guide. It's great.
Would you guys have an explanation for this:

I go Custom > Orphaned (the name I gave it) and I get lots of stuff supposed to be removed. The pbm is when I righ-click on them I can't remove anything

I only  get: "Mark for installation". 

I'm a noob and I wonder:

What's all this stuff doing in my "Orphaned"?
Should I intall them and then remove them? (no doubt this is stupid).

Thanks for any help you give me.

---

### Post by missmoondog on 2006-04-08
nice little how to. 

quick question about tip#3. when selecting language, it pre-selected all the "en" in the list. i clicked next, and let it go. is that ok? if not, what do i need to do to correct it? remove and re-install?

also, the localepurge failed to configure correctly, but is installed. this has happened on 2 out of 5 systems. what's that mean? i see there is another posting on page 1 of this thread, about that doing the same on their system.

another also. when i try to remove the residual nvidia-glx, i get an error code 2 or 10 on those same 2 systems.

thanks

---

### Post by uantuzri on 2006-04-19
[QUOTE=xyz]
What's all this stuff doing in my "Orphaned"?
Should I intall them and then remove them? (no doubt this is stupid).
[/QUOTE]

Of course, that's not a good idea. I supose that the filter is not working well. Check in Settings>Filters, and Selecting Orphaned (the name you gave) that the only option checked is "orphaned"

Anyway, having this filter just makes things easier, but you can always use the command on Tip #4.

---

### Post by dcstar on 2006-04-20
If you want to reduce the risk of your system filling up with log files, install the following packages:

logrotate
anacron (for machines not left running 24/7)

You can also edit /etc/default/rcS and set:
```
TMPTIME=1
```
to only keep files in /tmp for one day (then a cron job should get rid of them).

---

### Post by xyz on 2006-04-21
[QUOTE=uantuzri]Of course, that's not a good idea. I supose that the filter is not working well. Check in Settings>Filters, and Selecting Orphaned (the name you gave) that the only option checked is "orphaned"

Anyway, having this filter just makes things easier, but you can always use the command on Tip #4.[/QUOTE]

> Check in Settings>Filters, and Selecting Orphaned (the name you gave) that the only option checked is "orphaned"

That was it! Thanks a lot for pointing it out to me.

---

### Post by Mishal on 2006-06-07
Another place we probably will overlook:
Trash folder in the Home directory.

I just found that 3.4GB of waste in that folder was eating my HD for months.

---

### Post by elemental666 on 2006-06-08
nice, good tips...  good job showing the gui tools too, however, I can see tips 1,2 & 4 being something to do regularly, or at least repeatedly.  So how about the command line equivalents for these?  Might could make a script and setup a cron job for it.

so:

TIP #1 - Residual Config Packages

dunno, looking it up, if you know it or find it before me please post.

---

### Post by Norradj on 2006-06-08
What about "Installed (local or obsolete)" in synaptic?
In a clean install this section is empty.
I think lots of the packages could be uninstalled.
(except sun-j2re1.5, win32codecs and flashplayer-mozilla and other "real" local install)
So how do I figure out which packages could be uninstalled?
For instance, I got a big bunch of python2.3 packages there as well as what I think outdated lib-packages.
Not essential, but when we talk about cleaning........

---

### Post by lapega on 2006-06-12
Hi, good tutorial, but....

I do the localepurge and all right, but now I opened mysql-query-browser and when I try to make a modification it exits and says:

"requested widget 'charset_combo' with the wrong type"

How can I put the locales back???

Thanx

PS: sorry about my bad english

---

### Post by Gr4v3 on 2006-06-25
great job man, nice how to

---

### Post by pcolamar on 2006-07-07
WackToMack - Thanks a lot

Great stuff, well needed for a 8GB HD

---

### Post by PingunZ on 2006-07-07
Great guide but its a little to difficult to follow













JK :KS 

Grtz PingunZ

---

### Post by metaltailz on 2006-07-10
Thanks, I didn't get rid of much; but then again I did just install this.

Since I'm running Xubuntu, I give it the Xubuntu OK!:D

---

### Post by jikanter on 2006-07-12
Excellent, been looking for something distro-specific like this for a while.... Now just to bundle a couple of them using a perl script.....

---

### Post by iGama on 2006-07-12
thanks for the guide , really helpfull.

Just one question, do you mind if i translate it to portuguese? ;)

---

### Post by drtpw on 2006-07-26
Thank you.  I am new to the Linux/Ubuntu thing and am elated to find something besides the "other 2".  I really appreciate your thoughtful, concise, yet thorough and easy-to-follow tips.  I understand how experienced users don't like some of the 'newbie' questions but I also don't like thoughtless, flippant, replies that don't work.  Well done.

---

### Post by beameup on 2006-08-02
So should I heed the warning for localpurge????

> Automagically remove unnecessary locale data
This is just a simple script to recover diskspace wasted for unneeded
locale files and localized man pages. It will automagically be invoked
upon completion of any apt installation run.

[COLOR="Red"]Please note, that this tool is a hack which is *not* integrated with
Debian's package management system and therefore is not for the faint
of heart. This program interferes with the Debian package management
and does provoke strange, but usually harmless, behaviour of programs
related with apt/dpkg like dpkg-repack, debsums, reportbug, etc.
Responsibility for its usage and possible breakage of your system
therefore lies in the sysadmin's (your) hands.[/COLOR]

Please definitely do abstain from reporting any such bugs blaming
localepurge if you break your system by using it. If you don't know
what you are doing and can't handle any resulting breakage on your own
then please simply don't use this package.

---

### Post by ounas on 2006-08-02
Thanks WackToMack

-Ounas:D

---

### Post by Epperly on 2006-08-02
Thanks, I freed up a whole .1 gigs from steps 1-3.

---

### Post by nu2this on 2006-08-03
=D>  Thank you x10 =D>

---

### Post by alyson on 2006-08-06
If you like GUI tools, and want to see a visual representation of your HD space, Filelight, a program that can be installed from Synaptic, might prove useful.  I use it regularly to make sure that directories (like hidden trash cans) aren't filling up with stuff.

---

### Post by sapo on 2006-08-06
Nice Howto!

very very usefull :)

---

### Post by pennyminstrel on 2006-08-16
Thanks for this. Having only had ubuntu for about 2 weeks I keep getting this feeling I might be accumulating all sorts of rubbish but don't know where to look for it so I feel much better now.

And thanks for the really clear step by step instructions that I think event the newest user could cope with.

---

### Post by snooze on 2006-08-17
Thanks for the easy-to-follow tips.
I removed almost 2 gigs.

---

### Post by rjz35 on 2006-10-15
Thanks for this perfect how to, realy liked it, i can use ubuntu only because of these kinds of posts. thanks again.

---

### Post by Koori23 on 2006-10-15
I think this is the same thing as the gui method for clearing the old .deb packages out of synatic. I use it often.

sudo rm -f /var/cache/apt/archives/*.deb

---

### Post by xyz on 2006-10-16
> **Koori23 said:**
> I think this is the same thing as the gui method for clearing the old .deb packages out of synatic. I use it often.

sudo rm -f /var/cache/apt/archives/*.deb

Yes me too! I go in there (/var/cache/apt/archives) quite often...but thanks again for the howto.

The first time I used **WackToMac's** how to I ran

```
sudo deborphan | xargs sudo apt-get -y remove --purge
```

as indicated in Tip #4 but never did dare again ever since because, as I recall, it messed things up for me.

---

### Post by hikaricore on 2006-10-16
localepurge: Disk space freed in /usr/share/locale: 50116K

/me hugs localepurge

---

### Post by d3v1ant_0n3 on 2006-10-26
Lovely:D  Ran 1-3, cleared out a ton of space:D :D  Thank you!

---

### Post by civilian on 2006-11-18
Great guide, I removed a bunch of things I wasn't used, it freed 300mb of space. Thanks!

---

### Post by hady on 2006-12-01
Thanks great guide...

---

### Post by Enzo386 on 2006-12-01
Great guide, it really helped me out. Thanks!

---

### Post by esaym on 2006-12-01
> **NMUrugbysteve said:**
> Good howto, however I don't recommend using tip 4 because it may uninstall packages that one actually wants. For instance it tries to remove all of my gstreamer plugins.
so now how do I get gstreamer back:???:

---

### Post by baalthazar on 2006-12-02
some1 should compile a script or a program to make this automatic

---

### Post by rodrigo666 on 2006-12-22
Great how to, thanks for sharing all of this tips!

---

### Post by swigrid on 2006-12-25
something wrong with my dapper 6.06...

i cant use apt-get autoremove
```

apt-get autoremove
E: Invalid operation autoremove

```
](*,)

---

### Post by wildnr1 on 2007-01-04
**Deborphan** has a **graphical** friend in Synaptic 
quote:

A graphical tool to find and remove orphaned libraries
**GtkOrphan** is a graphical tool which scans your debian system, looking for
orphaned libraries. It implements a GUI front-end to deborphan, but adds the
package removal capability.
A detailed documentation on the program can be found at:
[http://www.marzocca.net/linux/gtkorphan.html](http://www.marzocca.net/linux/gtkorphan.html).

---

### Post by raintheory on 2007-01-11
> **swigrid said:**
> something wrong with my dapper 6.06...

i cant use apt-get autoremove
```

apt-get autoremove
E: Invalid operation autoremove

```
](*,)

**sudo** apt-get autoremove

---

### Post by swigrid on 2007-01-12
m8 thanx for your replay, but I use su - for system operation (installing, removing, upgrading and everything). there isn't problem with sudo. There is problem ,that dapper hasn't got autoremove option. It has just ubuntu edge 6.10.

---

### Post by carla on 2007-03-11
deborphan--don't forget its super-helpful cousin, debfoster. :)

localepurge--how do you manage that shell GUI it uses for configuration? I cannot seem to successfully choose my language. Is it a right-click trick, something I should type in the chosen boxes...?

---

### Post by carla on 2007-03-12
> **xyz said:**
> Yes me too! I go in there (/var/cache/apt/archives) quite often...but thanks again for the howto.

The first time I used **WackToMac's** how to I ran

```
sudo deborphan | xargs sudo apt-get -y remove --purge
```as indicated in Tip #4 but never did dare again ever since because, as I recall, it messed things up for me.

I'd suggest installing deborphan's companion, debfoster, because it tells you what each package is keeping installed, and inquires individually about each package's deletion.

```
sudo apt-get install debfoster
sudo debfoster
```

Then just slow down, read each inquiry, and answer each question with yes or no. The script does the rest of the work, confirms what it's about to delete before it continues with its Final Solution :), and lets you know how much diskspace you've saved.

---

### Post by HolyJoe on 2007-03-31
that is a great guide for me.
thanks.

---

### Post by silentsunami on 2007-04-04
nice guide. you rocks dude

---

### Post by BLTicklemonster on 2007-04-08
> **carla said:**
> deborphan--don't forget its super-helpful cousin, debfoster. :)

localepurge--how do you manage that shell GUI it uses for configuration? I cannot seem to successfully choose my language. Is it a right-click trick, something I should type in the chosen boxes...?

Me, too. I can't get past that. I can't believe that you aren't given a clue in the text, either.


*edit: for what it's worth: [http://bluev.wordpress.com/2005/12/27/how-to-use-localepurge/](http://bluev.wordpress.com/2005/12/27/how-to-use-localepurge/)

---

### Post by ksryno on 2007-04-13
push space to select locales- I would keep all US and generic loacles if I were you.

---

### Post by Tundro Walker on 2007-04-13
Someone asked for a quickie script to "automate" some of this command-line stuff, so I thought I'd post the one I made for personal use.  I'm still new to Linux / Ubuntu, so I may have tossed in some unnecessary command-line switches or what-not, but it works for me.

**GET IT...**

We'll start with installing what he talked about...(run from terminal)

```
sudo apt-get install deborphan localepurge
```Deborphan is a silent install...you don't have to give any feedback.  (I'll go into more detail about it further down).

Localepurge, on initial install, will prompt you for your languages to KEEP (everything you don't check will get bumped off).  After that, localpurge will fire off after any other apt-get (Synaptic, Aptitude, Adept, etc) sessions, bumping off new locale / language stuff that isn't for the language you want to keep (EG: man pages in another language).  With a GUI, like Synaptic, you won't see it in action, but if you use command-line apt-get, you'll notice it show up at the end stating how much room it just freed up by purging locale files.  Sometimes an insignificant amount, sometimes quite a bit.  Pennies turn into dollars, though, so every little bit NOT purged can add up over time.  However, as others have stated, it may cause problems with other things.  When picking the language, be sure to pick the basic (EG: en for English), as well as your locale (EG: en_US for United States English).  This may help alleviate some problems.

**USE IT...**

Next, we'll chain together some apt-get commands for a quick update, upgrade and clutter control script

```
sudo apt-get update && apt-get -y dist-upgrade && apt-get remove --purge && apt-get -y autoremove --purge && apt-get clean --purge && apt-get autoclean --purge
```Note, instead of normal "upgrade" we use "dist-upgrade" which is the "smart upgrade".  Normal upgrade will just look for new versions of packages and update them.  Dist-Upgrade checks if those newer versions have any new dependancies, and installs necessary packages for them.

[COLOR=Purple]_EDIT (4/14/2007): _

I modified the apt-get refresh script to also purge the /tmp directory when it's done...

```
sudo apt-get update; apt-get dist-upgrade; apt-get remove; apt-get autoremove; apt-get clean; apt-get autoclean; rm -r /tmp/*
```In chaining the commands together, I used ";" instead of "&&" just to make it cleaner looking.  The...

```
rm -r /tmp/*
```...at the end of the script uses the rm with the -r (recursive) switch to purge files and sub-folders from the /tmp directory.  If you want to run just the rm part by itself, you'll need to put "sudo" in front of it, or else you'll get errors saying rm can't remove stuff (because you don't have the admin rights to do so...only root/sudo does).

I also wanted to mention, running this script is like the "System Update" function in Ubuntu   That feature is basically a CRON / ANACRON scheduled task that periodically checks for updates, notifying you via your "notifications" section on your panel if any are found.  You click on it, and a GUI pops up showing you what's going to update.  

If you run this script, or, if you check and update through Synaptic, Adept, Aptitude, etc, the System Updater won't find anything very often, since you're already updating everything yourself.  I guess this script does a bit more (a little more cleanup and purging the /tmp folder), and does it a bit faster since you don't have the GUI overhead slowing it down.  You can schedule it as a CRON / ANACRON job, but if you do, I don't see a point in keeping the System Updater running to check for updates, too.  

For folks paranoid of the terminal, or are just more comfortable doing things through GUI, I recommend sticking with Synaptic and System Updater.  IE: On your own computer, you can be as much of a svelt Linux-geek power-user as you want, but don't set up this script on your dear Grand-ma'ma's computer, and expect her to click it occasionally (because she won't).  And don't set it up as a CRON / ANACRON job, because it'll fire off a terminal asking for "Password" to which she'll call you up while you're in the middle of doing something important with lots of questions thinking someone's trying to hack into her computer.  Let her use Synaptic, and keep the System Updater running on her computer, since it's more user-friendly.

Side note, in Synaptic, you can get it to do some cleanup work by going into "Settings > Preferences > Files (Tab)".  Under the "Temporary Files" heading, click the option "Delete downloaded packages after installation".  This will help cleanup the binaries after they install.  For windows folks, you can think of it as deleting the executable installation file after you've ran it to install the software.  For folks on dial-up with large hard-drives, you may want to keep them, just in case you want to re-install the package, but don't want to wait forever for it to download again.  I personally haven't had any problems with things I've gotten from the repo's, so I choose to purge the install packages.  If I did have a problem with something, not only would I uninstall it, but I'd purge the install binaries, too (LOL!)[/COLOR]


**PRACTICAL USE...**

Ok, you've got this faboo script, but it's a pain to open the terminal and run when you want, especially since you'll forget (seriously, we have more important things to worry about).  Someone mentioned setting it up as a CRON job, letting it periodically auto-run.  I haven't used CRON, and personally I get a little paranoid of auto-running things, especially something like this.  So, I just tossed the script in an .sh file, and created a desktop launcher / shortcut to run it.  Since it's on my desktop, I remember to do it every so often.

1) Open your fav text editor (mousepad, gedit, kate, vim, nano, whatever...)

2) Copy/paste the script text in

3) Save the file to wherever you want to stash it and call it whatever you want...I tossed mine in my home directory ... /home/tw1/apt-get_refresh.sh

4) Go to your desktop

5) Right-click and select to create a new launcher (in Ubnuntu-GNOME, I left mine as "Application" launcher, named "Apt-Get Refresh")

6) For the "command", fill in "sudo sh <path to file>/<name of file>".  For instance, on my comp it was...

```
sudo sh /home/tw1/apt-get_refresh.sh
```7) Pick an icon then "OK", and you have a new clutter control tool


**IS AUTO-RUNNING THIS STUFF SAFE?...**

Heck no, it's reckless and dumb, but you're only young and stupid once in life, so who cares.

Actually, I haven't had any problems; you're basically doing stuff you do in Synaptic, just through the command-line...faster...and all at once (hehe).  Auto-updating your repositories (sudo apt-get update) is very safe.  All it's doing is pinging the repositories to refresh the catalog of pacakges (this lets you know if anything new or updated has shown up).  

Of all the commands, the auto-upgrading (apt-get dist-upgrade) probably has the most potential to mess things up.  The Ubuntu MOTU go to great pains to make sure stuff in the Ubuntu repo's are stable and safe (and if it's not, they put big red flags on it like "devel...used for development" or "test only...unstable" or "warning, will slap your wife and kick your dog, use at own risk".  So it's safe to avoid breakers there.  But, you never know what folks running non-Ubuntu repo's are doing, so you may end up with an occasional breaker (package that breaks). 

Don't fret.  It can happen through Synaptic "Mark All Upgrades" as well, so who cares.  If something breaks, you just use Synaptic's broken package filter, click to fix/reinstall them, and/or roll-back to stable versions (Synaptic > Help > Contents > Managing Packages > 3.11. To Force the Installation of a Specific Version...)

Everything else -- clean, remove, etc -- is safe.  You're just removing excess junk left behind by the uninstall, which, in the past when space was at a premium, was necessary to leave behind as programs were swapped in and out of computers.  But these days, folks know what they want, and don't want anything left from what they don't.  Hard drives are so huge you don't have to worry about swapping programs in and out, because you're hurting for space.

    
**DEBORPHAN...USE CAUTION...**

We installed it, but haven't gotten around to using it yet.  Why?  Because one poster said DebOrphan bumped off some gstreamer plugins he wanted to keep.  Yes, this can happen.  The command the original poster gave...

```
sudo deborphan | xargs sudo apt-get -y remove --purge
```....basically runs deborphan, and then passes whatever shows up in its list to apt-get for automatic removal/purging (-y auto-yes'es it all).  

Before diving into that and finding out it just purged all your useful plugins and such that Automatic2 or EasyUbuntu installed (that it thought were worthless), I'd recommend just starting with...

```
sudo deborphan
```This provides a list of what it thinks are useless packages.  You can then open Synaptic and hunt down specific ones you feel are useless, and keep the ones that aren't.  Deporphan also has a "keep" list, where you can maintain a list of packages it should never recommend getting rid of.  You can read up about that in the deborphan man page...

```
man deborphan
```However, since I only use deborphan to "recommend" potentially useless stuff, then hunt for it in Synaptic, I prefer to use his Synaptic "Orphaned" custom filter idea instead (didn't know about it until I read his post, and it's pretty cool!).  I'm already in Synaptic killing things off, so it's just easier hunting for Human-Decision-Required orphans, too.

I don't recommend automating deborphan to auto-purge stuff, since it may be stuff you want to keep, but, if you insist you can chain it together with the apt-get script as follows....

```
sudo apt-get update && apt-get -y dist-upgrade && apt-get remove --purge && apt-get autoremove --purge && apt-get clean --purge && apt-get autoclean --purge && deborphan | xargs sudo apt-get -y remove --purge
```...that'll run through the apt-get obstacle course, then wipe out deborphan's at the end, too.  

Note that in purging orphans, either through DebOrphan or Synaptic, you may want to have a couple goes at it.  I found that once I bumped off some junk, other packages turn up as junk / orphaned since they were dependancies of previous junk / orphans.  Not sure if I'm correct on this, just noticed that after I removed some useless Palm Pilot stuff orphans from Synaptic, a few more showed up, which I bumped off, too.  


**NOTES...**

*"OMG!  What is all that cryptic command-line stuff and what's it doing to my computer?!"*

_&&..._ This is a basic Linux command-line function that lets you chain commands together, to be done one after the other.  So, for the apt-get script, we're literally just running the gambit of apt-get commands, starting with updating your repositories, upgrading anything necessary, then cleaning/removing leftover junk....all ran one after the other from just one command-line execution.

_(APT-GET) --PURGE..._ The apt-get "--purge" command-line switch forces apt-get to (you guessed it) purge any clutter along with the main package...config files mostly.  I can understand the purpose of keeping config files around -- in case you ever install the package again and don't want to hassle with setting it up --, but a lot of folks moving to Ubuntu from Windows are pretty sure that when they get rid of something, it's for good (probably because they were trying something out and didn't like it, so what's the point of keeping config files for it).  MS Windows was (still is?) really bad about this kind of stuff.  You'd uninstall things and old .ini and such were left around, leaving you to play garbage man by hunting down folders and such to manually delete after install.  Top that off with RegClean'ing, Defragging, virus-scanning, adware / spyware scanning...sheesh.  You could literally waste an entire afternoon cleaning up after MS Windows.  Sure, you could do some crappy DOS batch files to automate a little bit of it, but seriously those don't have the robust scripting capability of the Linux command-line.  And if you tried to use WinScript (MS's answer to more robust command-line scripting), you'd get a migraine and quit in frustration before doing anything useful.  At least with Linux, you can just run a little script periodically and let it do the work. 

_(APT-GET) -Y..._ The apt-get -y command-line switch auto-yes'es any Y/N prompts that come up with apt-get.  I usually only use it for things I know I want to "Y" to, like remove / autoremove.


**POST-SCRIPT ... FRESH INSTALL CLEANUP?...**

I created this as occasional clutter control script, but got curious about using it during fresh installs.  I like Ubuntu, but don't use some of the software pre-installed with it.  So, in Synaptic, I remove the "unbuntu-desktop" meta package (as recommended by others), which removes the dependancy of a lot of the other software (Open Office, Ekiga, etc), letting me remove it as needed.  I only remove main packages, not libraries, since the apt-get script will find and remove those for me.  After I remove what I don't need, I run the apt-get script to clean up.  

Now, anyone who's done an install / update will know where I'm going with this...  If I fresh install, then pre-purge all kinds of stuff and run the clutter control script, I could save time with the mass-update afterward since it's less stuff to check/update.  However, I'm paranoid that if I don't let Ubuntu do a full update after install, it may bork something up with my pre-purging a lot of things before letting the update run.  

It's up to you if you want to try pre-purging stuff or not.  Caveat Emptor...

---

### Post by brennydoogles on 2007-04-13
> **Tundro Walker said:**
> Someone asked for a quickie script to "automate" some of this command-line stuff, so I thought I'd post the one I made for personal use.  I'm still new to Linux / Ubuntu, so I may have tossed in some unnecessary command-line switches or what-not, but it works for me..  
 Caveat Emptor...

Great Update Thanks!

---

### Post by Copperblade on 2007-04-17
Ok... but which apt-get command does the "remove residual config" from synaptic?  I'm sure I have packages that have been removed but the configs were left behind.

---

### Post by c@rc@ss on 2007-04-18
excellent, thanks to you I cleaned over 44 MB of junk.

I recommend using orphaned a few times as deleting orphans also creates more orphans.

:guitar:

---

### Post by volksolwagen57 on 2007-04-18
awesome!! i gor rid of a lot of junk!

---

### Post by vsandz on 2007-04-26
Sweeet guide mate! Got rid of loads of unwanted stuff ... thanks.

I have a couple of questions though:

1. What would this do 'sudo apt-get autoremove' ? Is it recommended?

2. I installed Amarok (on Gnome) and then uninstalled it via Synaptic ... It installed like 100+MB of stuff n I'm sure it hasnt removed all of it and the methods here ... well i'm not 100% sure it has removed all of the junk ... pls help!

Cheerio!!!

---

### Post by Ghost|BTFH on 2007-05-30
> **Mishal said:**
> Another place we probably will overlook:
Trash folder in the Home directory.

I just found that 3.4GB of waste in that folder was eating my HD for months.

You actually use "remove to trash" for an option??? o_O

I just delete with confirmation, saves me the extra step of emptying my trashcan every time. ;)

Cheers,
Ghost|BTFH

---

### Post by Contrast on 2007-05-31
Excellent guide; it's much appreciated. I have one question though. I followed all the steps in the tutorial, and upon looking through the hidden files in my home folder, there are still config files, logs, and folders for programs which I've uninstalled. Is there any way to quickly and easily get rid of all of these in one or two steps, or do I have to manually inspect my home folder every time I uninstall something just to make sure it's not leaving junk behind?

---

### Post by Contrast on 2007-05-31
> **vsandz said:**
> Sweeet guide mate! Got rid of loads of unwanted stuff ... thanks.

I have a couple of questions though:

1. What would this do 'sudo apt-get autoremove' ? Is it recommended?

2. I installed Amarok (on Gnome) and then uninstalled it via Synaptic ... It installed like 100+MB of stuff n I'm sure it hasnt removed all of it and the methods here ... well i'm not 100% sure it has removed all of the junk ... pls help!

Cheerio!!!

"sudo apt-get autoremove --purge" should get rid of all of those packages that were installed along with Amarok (assuming you don't have any other applications that depend on them; e.g., if you have any other KDE applications installed, it won't get rid of the essential KDE libraries). That command is for getting rid of all of the automatically installed packages (those in the list of packages to be installed when Synaptic asks, "Mark additional changes?") that are no longer necessary on your system.

To save yourself from this step, you can always use the terminal to remove packages you no longer want, assuming you know their name (or at least the first few characters, given tab-completion). Just do "sudo apt-get autoremove --purge nameofpackage" and it will also remove the packages that were installed with that one, assuming they're no longer needed.

---

### Post by waggygee on 2007-06-02
Cool! Thanks

---

### Post by tombiz on 2007-06-03
I found this guide through Lifehacker. Worked great on my Ubuntu 7.04.

---

### Post by tL0z on 2007-06-04
The "Find orphaned packages" listed some important packages (such as  "add user"). Isn't it a bit dangerous to use it?

---

### Post by Kobalt on 2007-06-04
It can be... adventurous I'd say, since it is unlikely to remove vital packages and break your system, but it can remove such things as video/audio codecs. 
You should use this feature with precaution indeed.

---

### Post by mrwasabi on 2007-06-04
Sweet, I just made the switch to Ubuntu from winblows and had no clue how to maintain my system's health, thanks very much for sharing this!!!!!!!!!!!!!:KS

---

### Post by chris_504 on 2007-06-12
Thanks for some much needed cleaning advice..i thought in linux, cleaning was in autopliot mode.

---

### Post by huygens on 2007-06-13
> **chris_504 said:**
> i thought in linux, cleaning was in autopliot mode.

With Linux you are in power of your system, so you tell him what to do or not :-) but at least it does not do things in your back that you weren't expected.
In addition, with such cleaning you can upgrade from an Ubuntu release to another and have your system almost clean like a fresh install (I say almost, because some of your configuration files in your home directory might not be "clean").

---

### Post by ankush on 2007-06-14
This Is an Excellent HOWTO

---

### Post by BugoK on 2007-06-21
A very helpful howto. 
Many thanks.

---

### Post by H.E. Pennypacker on 2007-06-28
Seriously, there is no GUI to handle all this?  A single application that can do all of those steps from a single place?  I don't want to run around just to maintain packages, going from Synaptic to localepurge to apt-get clean.  

I am guessing there isn't.

---

### Post by Shpongled303 on 2007-07-19
Excellent HOWTO, I will be using this very soon. I have had a few partially-downloaded packages that I cancelled for one reason or another.

This site is wonderful, very helpful, thanks for taking the time to write this and share your knowledge with us!

---

### Post by Tuan Tran on 2007-07-30
wow thx soo much. my ubuntu system is running alot smoother without the junk in the trunk :)

---

### Post by likemindead on 2007-08-21
Score.

8-)

Thanks.

---

### Post by 5h4rk on 2007-08-30
Wow, thanks for the guide, now I feel, well, my Ubuntu feels like it has lost a couple of kilos... :)

---

### Post by NOOBYNOOB on 2007-09-15
Bookmarked :-)

What's the difference between deborphan and KleanSweep?

It appears (to mee) that KleanSweep tracks more orphaned files than deborphan, or?

---

### Post by gOLdenHaWK3D on 2007-09-15
Quite impressive. :)

---

### Post by Deepak K on 2007-09-26
Absolutely Fantastic and Great.

---

### Post by maestrobwh1 on 2007-10-29
> **NMUrugbysteve said:**
> Good howto, however I don't recommend using tip 4 because it may uninstall packages that one actually wants. For instance it tries to remove all of my gstreamer plugins.

Install GTKorphan, which is a frontend for deborphan and you can see and select what orphaned packages to delete.

If someone already mentioned this in this thread, sorry.

Peace

---

### Post by likemindead on 2007-10-29
Has any of this changed for Gutsy?

---

### Post by tyfn on 2007-10-29
this gide excellent thank you...

---

### Post by KhaaL on 2007-11-07
the OP seems to be inactive, but there's two things that's not covered in this guide, and that is apt-get can now remove unused packages by itself (sudo apt-get autoremove). But there's still hidden folders with configurations that will clutter the home folder from various programs, if there was only a tool to autoremove them too...

---

### Post by Tankerdog2002 on 2007-11-17
Thank You WacktoMack.

It's a heartfelt relief to see easy to use instructions such as these.

So often in these forums us newbies are run through the fodder mill and lambasted. Or...we're given a slew of scripted gobblley-gook and told to make the best of it.

Kudos to you sir!

It's people like you that will draw people to LINUX in lieu of pissing them off or scaring them away.

Keep up the great work!   (Woo-Hoo)

---

### Post by kahrn on 2007-11-18
Not sure if anyone has covered this before, but it is also possible to remove locale data from .desktop files, which are used for shortcuts in the applications menu.

I made a little script to make it easy which on a default install can clear anything up to 200kb of data, and more if you have installed new applications.

You can find the script at [http://kahrn.pastebin.com/f1bf15aba]("http://kahrn.pastebin.com/f1bf15aba").

---

### Post by Cariboo1938 on 2007-11-29
I just read through this very interesting thread and I  have one question before I try to use the Howto.
What is the difference between 

" sudo apt-get autoclean " and 
" sudo apt-get autoremove"

???:confused:

---

### Post by smartboyathome on 2007-11-29
I think Autoclean just cleans up files you don't need, while autoremove deletes unneded files..

---

### Post by Cariboo1938 on 2007-11-29
> **smartboyathome said:**
> I think Autoclean just cleans up files you don't need, while autoremove deletes unneded files..
Thanks for the response...you are right...see [HERE!]("http://ubuntu-tutorials.com/2007/01/04/package-management-with-apt-ubuntu-all-versions/")
:)

---

### Post by prosper927 on 2007-12-04
thank you so much for this!!! keep it up bro! :guitar:

---

### Post by jake3988 on 2007-12-06
To continue the 'junk files' discussion (GREAT How-To by the way!)... look for .core files in your home directory.

If you run programs in beta or just have programs that like to crash, sometimes they'll leave a .core file that you can use to parse through to debug it.  However, it's really only useful to programmers.

Not only that, they're ENOURMOUS.  Once in freebsd mozilla left some core files.  Turns out, they totalled over a gigabyte.  Yes, an entire gigabyte.

So, look for those.

Also /apt/cache/archives/  (I probably got that wrong, I'm in a lab right now on windows).  That contains all the downloaded packages that sudo apt-get autoclean removes (Just for reference).  You can manually cd and delete all the packages from there using rm * in that directory as well.

This also is the response to the different between 'autoclean' and 'autoremove'.  Autoclean cleans up the downloaded archives (.gz or .tar) files used to install things.  Autoremove cleans libraries that are no longer needed.

---

### Post by PRoPAiN! on 2007-12-18
> **jake3988 said:**
> Also /apt/cache/archives/  (I probably got that wrong, I'm in a lab right now on windows).

It's /var/cache/apt/archives/ .  And thanks for the tip/reminder: I freed up another 36MB!

---

### Post by BobSongs on 2007-12-20
Listen: Since Breezy Badger I've wondered about this. Not that it's kept me up at night. But Ubuntu was a decision because I felt I had more control of this system. But unnecessary files were a niggling question.

I haven't finished your set of instructions and each one removes only so many files (I've come to know some of the shortcuts before hand). But I thought I'd stop and say: Thanks.

---

### Post by bred on 2008-02-25
thank you very much for the tips, works really great guys!!!
way to go boys!

---

### Post by Jose Catre-Vandis on 2008-02-27
> **smartboyathome said:**
> I think Autoclean just cleans up files you don't need, while autoremove deletes unneded files..

and the difference between```
unneeded files
``` and ```
files you don't need
``` is? :lolflag:

---

### Post by ellalan on 2008-02-29
Hi
It is a brilliant tutorial and very useful, Thanks a lot.

---

### Post by fetisha on 2008-03-04
Very useful. Thanks for all the tips.

---

### Post by Exonimus on 2008-03-09
Great tutorial! I removed over 250 packages with the first command =) I was busy selecting them all until I realized I could, of course, just use the shift key and do it all in two clicks.. :D
Also freed another 100mb of space.. not bad. not bad at all! :) 
Also, the system feel more responsive somehow

---

### Post by Aliby on 2008-03-12
> **swigrid said:**
> something wrong with my dapper 6.06...

i cant use apt-get autoremove
```

apt-get autoremove
E: Invalid operation autoremove

```
](*,)

Firstly you need **sudo** permision and the package you want to remove (uninstall)

**Note:**
This is to remove a package AND all the packages it is dependant on (if they are not used anymore). eg.
```
sudo apt-get autoremove winedev
```
 will also remove the following if they are not needed else where.
[LIST]
[*]wine
[*]libc6-dev
[/LIST]

You may be wanting (note the addition of **sudo**)
```
sudo apt-get autoclean
```

This removes all the packages downloaded in the archive that are no longer in the repository lists (i.e they're gone or there is a newer version)

---

### Post by Aliby on 2008-03-12
> **Koori23 said:**
> I think this is the same thing as the gui method for clearing the old .deb packages out of synatic. I use it often.

sudo rm -f /var/cache/apt/archives/*.deb

This is basically the same as the following:
```
sudo apt-get clean
```

Except that in the latter case apt knows 
[LIST]
[*]where the configured archives folder is (it may not be the default linux location)
[*] the files are now gone. In any case it will simply download them again if necessary.
[/LIST]

---

### Post by Aliby on 2008-03-12
Does anyone know how the "Temporary Files" settings under **Synaptic  | Settings | Preferences** work?

[IMG]http://avbaty.myweb.absamail.co.za/Synaptic_Prefs.png[/IMG]
[Screen shot of the "Synaptic | Preferences"]("http://avbaty.myweb.absamail.co.za/Synaptic_Prefs.png")

I was hoping that it automates the "cleaning" processes in varying degrees:

[LIST=1]
[*]```
"Does Nothing"
```
[*]```
sudo apt-get clean
``` 
[*]```
sudo apt-get autoclean 
```
[/LIST]

However, I don't know how to "trigger" the action?
:confused:

---

### Post by Aliby on 2008-03-12
**_Better AutoClean_**
:KS
Another "valuable to me" trick I found was to remove the "CD-Rom/DVD" repositories from the sources lists before doing:
```
sudo apt-get autoclean
```

You can do it by unticking them in Synaptic

**autoclean** seems to look at what is in the package lists and delete was is not there and the CD's often have old versions.

I then "check" them again to add these repos so I don't have to download anything that current and is on them already.

I have posted it as a "Wishlist" in Launchpad
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/200536]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/200536")

> I actually can't think of a reason to keep ANY packages in the archive that are listed on a CD-ROM/DVD repository?

It would be great to have the default, or an option/ flag, to ignore CD-ROM/DVD repositories when performing "apt-get autoclean"

WHY?
1. I autoclean to keep delete old packages to reduce storage space
2. These packages are available on the CD anyway (I don't have to keep them on the hard drive)
3. It seems apt-get sees the "old" files in the CD-ROM lists thus does not delete them.
4. Most of the time online REPOS are also included, which have the latest packages listed anyway. (One option would be to ingore the CD-ROM repos, unless they are the only repos?)

I thought it would delete ALL old versions, but it deletes unlisted versions. So I currently achieve the above by:
* Temporarily removing the "CD-ROM/DVD" repositories from the lists
* Then doing a "apt-get autoclean". Older versions are now deleted from the archive (they no longer appear in active package lists)
* Adding the "CD-ROM/DVD" repositories again so new installs can access these packages if they are the latest versions and doesn't need to download them - saving bandwidth.

------------
Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015)
apt 0.7.6ubuntu14 0

We'll see whether anything comes of it

---

### Post by takmsdsm on 2008-03-12
Well. this program has officially pissed me off. I ran it, it found a couple orphaned files ~40ish. I have it clean out the files. Not only did it clean out those files, it also cleaned out and deleted conky, figlet, a couple of my games, envy, and a couple other programs that i didnt tell it to do. 


hell, conky  was even running at the time!

:unamused:

the best part? it deleted its own GUI out when it was all finished.

---

### Post by juky on 2008-04-03
Thanks for this HOWTO, everything went fine with me!

---

### Post by nebu on 2008-04-03
thnx a lot..... a very helpful howto...

---

### Post by cor2y on 2008-04-11
Thank you for the Helpful how to

---

### Post by ghindo on 2008-05-05
Great, great How-To.  Thanks, OP!

---

### Post by Ejas12 on 2008-05-12
Thanks It was very helpfull.

---

### Post by meazz1 on 2008-05-20
Great work!!

Thanks

---

### Post by BlueSkyNIS on 2008-05-22
Thanks!

This was very useful. =D>

---

### Post by 5735guy on 2008-06-06
Thanks for this. Tidied things up nicely :)

---

### Post by prabath_fun on 2008-06-18
Thanks and great and useful Thread.

---

### Post by Liv3dN8as on 2008-06-19
Awesome! I did them all!! Thanks!!!

---

### Post by jm101dm on 2008-06-20
Thanks, very helpful.
Jeff

---

### Post by blackmachine on 2008-06-21
excellent tutorial WackToMack!
saves me lots of disk space \\:D/

---

### Post by ebutton on 2008-06-23
Wow!  Your HOWTO is still going strong!  I just recovered 1.5 Gigabytes using it.

Thank you, thank you, thank you!

EdB

[http://ubuntuforums.org/images/smilies/eusa_dance.gif](http://ubuntuforums.org/images/smilies/eusa_dance.gif)

---

### Post by Foster Grant on 2008-06-29
> **NMUrugbysteve said:**
> Good howto, however I don't recommend using tip 4 because it may uninstall packages that one actually wants. For instance it tries to remove all of my gstreamer plugins.

This bug continues to exist. When I opened an MP4 video clip as a test, I had to reinstall the Mediubuntu-sourced Gstreamer plug-in.

---

### Post by Nullack on 2008-06-30
I dont have residual config as a list under status? :confused::confused:

---

### Post by M4rotku on 2008-07-04
Tyvm Wack for this amazing thread.  I've been looking for a way to get rid of those junk packages.

Also, that "sudo apt-get cow" line was HILARIOUS!!

---

### Post by M4rotku on 2008-07-06
I did this a few days ago and now when I try to install something, I get the following error from either gdeb or the add/remove app:

Could not download all repository indexes

> Archive directory /var/cache/apt/archives/partial is missing.

How would I go about fixing this?

---

### Post by Bob66 on 2008-07-06
Thank you! everything worked Great.

---

### Post by DonnieP on 2008-07-07
This "How To" is pitifully in need of updating to explain (without having to fish through the comments) that gstreamer plugins, etc. are going to be deleted if you follow the thing "step by step".  Shame on 'Tutorial of the Week' for not pointing this out.

---

### Post by RavUn on 2008-07-09
This tutorial is great.  It cleaned up a lot of files I didn't know about.

I agree, though, that the section about orphaned packages should be updated.  Luckily, it didn't remove any plugins for me, but it'd be a good update.  Maybe take out section #4 and just have #5.

---

### Post by milky2313 on 2008-07-11
gtkorphan is a graphical interface for using deborphan to find and remove orphaned packages.  It's a little easier to use than the method in tip #4 in that you can look over all of the orphaned packages that it finds, and then simply check the ones that you want to remove...

---

### Post by Ingenue on 2008-08-01
This was justs what I was looking for, Thanks OP.

---

### Post by arturieto on 2008-08-02
thanks for the howtos.  i did all the tips. but how do i know the effect of this cleaning.  does my ubuntu works faster? what do those junks have in effect to the system? slow down.  if so, then i did the right move.


art
/home/art/Desktop/Ubuntu User

---

### Post by estebandido on 2008-08-05
Very helpful. Better than Google, in fact!

---

### Post by InfinityCircuit on 2008-08-05
FYI the first command can be much shortened:

sudo apt-get remove --purge -y $(dpkg -l | grep ^rc | awk '{print $2}' | xargs)

---

### Post by lik2writ on 2008-08-15
everything worked fine, thank you!

---

### Post by Uchiha_madara on 2008-09-05
very nice guide thanks a lot

---

### Post by mrreality13 on 2008-09-21
Nice How
 To thank You
:popcorn:

---

### Post by Therion on 2008-09-21
Nice guide!

Personally I find it easier to simply use [QuickStart](http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop) though.

---

### Post by defri on 2008-09-21
Thanks for the tips. It's also work flawlessly dor me! I can't wait for your next tips!

---

### Post by lisati on 2008-09-21
Unashamed plug: for a couple of Windows tools (e.g. for when you're preparing Windows for a dual boot system) check [here]("http://geocities.com/rjv_soft/ssc.html"). The "more information" link is possibly incorrect, it should point [here]("http://www.geocities.com/rjv_soft/sc32.txt").

---

### Post by martin91 on 2008-09-29
Thanks, tons of packages were removed... more free space now:popcorn:

---

### Post by winkygizer on 2008-11-13
Thanks for your post!
I found nice tool that can do all cleaning job - 

[COLOR="Blue"]**Junk Files Cleaner**[/COLOR]: **[http://www.digeus.com/products/junkcleaner]("http://www.digeus.com/products/junkcleaner/index.html")**

I use it every day, it helps me to clean all junk information from my disc. It do saves time!!

___________________________
[Junk Files Cleaner]("http://www.digeus.com/products/junkcleaner/index.html")

---

### Post by winterblues on 2008-11-14
Just came across this thread. Very useful guide. Thanks!

---

### Post by dlfreem on 2008-11-19
Thanks for the info.  I just crossed over from Windows XP and had no idea how to clean my computer.  These tools were very helpful.

d-free

---

### Post by Mrs on 2008-11-30
thank you, this was very helpful

---

### Post by Cariboo1938 on 2008-11-30
My Installation is: 
	Ubuntu 8.04.1 Codename:	hardy

After the last update the system runs under :
	Linux kernel 2.6.24-**[COLOR="Magenta"]22[/COLOR]**-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64 GNU/Linux

Synaptic Package Manager shows that a few "linux 2.6.24-***[COLOR="Magenta"]21[/COLOR]*** - packages" (linux-headers, linux-image, linux-restricted-modules)
are still installed and I wonder what they are needed for and if I could un-install them to save space  
on the 4 GB partition I have left for the Ubuntu OS. :confused:

---

### Post by sheepdogj15 on 2008-12-04
I know this is an old howto, but I had some suggestions for additions.

you can remove .deb files that are left over from installs. you only want to keep these around for if you need to reinstall, and even then apt/synaptic can re-download them.

```
sudo rm -v /var/cache/apt/archives/*.deb
```

after a while this directory gets full of stuff. i think at one time i had over 300 MB in package files.


you can also remove old log files. logrotate (installed by default in Ubuntu) archives log files as gunzip files. you might want to keep these in case you need to do some deep troubleshooting. I've never needed them though.

```
sudo rm -v /var/log/*.gz
```


/tmp and /var/tmp can regularly be cleaned out. I'd be careful about /var/tmp though, if Gnome/KDE is running and you clear out that directory, crazy things can happen. Maybe on every reboot?

---

### Post by sheepdogj15 on 2008-12-04
> **Cariboo1938 said:**
> My Installation is: 
	Ubuntu 8.04.1 Codename:	hardy

After the last update the system runs under :
	Linux kernel 2.6.24-**[COLOR="Magenta"]22[/COLOR]**-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64 GNU/Linux

Synaptic Package Manager shows that a few "linux 2.6.24-***[COLOR="Magenta"]21[/COLOR]*** - packages" (linux-headers, linux-image, linux-restricted-modules)
are still installed and I wonder what they are needed for and if I could un-install them to save space  
on the 4 GB partition I have left for the Ubuntu OS. :confused:

if 22 runs fine, you are safe to remove any old kernels and related packages. you only want them if there is something wrong with the newest kernel.

i've done this before. i used to have a 100MB /boot drive, which kept getting filled up. you'd be surprised how much space 3 or 4 kernels take up.

---

### Post by Stamat on 2008-12-04
Awesome tutorial! Thy! 

Never use ```
sudo apt-get autoremove
``` lol!

---

### Post by sheepdogj15 on 2008-12-04
"sudo apt-get autoclean" is safe though

for that matter autoremove is safe, just pay attention to the output and read *everything* before you confirm.

---

### Post by sheepdogj15 on 2008-12-04
one more tip, anything you want to run everytime ubntu boots up can be put in /etc/rc.local

---

### Post by ttoolin on 2008-12-06
Thaank you for the very helpful information!

---

### Post by zivley on 2008-12-09
If you want to be even more sure, you can run any "apt-get" command predeccesed by the "-s" (simulate) switch, this way aptitude will tell you exactly what it's going to do, but won't do it for real, only simulate it.
You can run
```
sudo apt-get -s autoremove
```
Nothing will happen, but you'll get the chance of seeing what exactly will be done if you don't use "-s"

---

### Post by Col-1023 on 2008-12-11
Thank you, a very useful tutorial.

---

### Post by lsd on 2008-12-22
Have you tried installing "fslint"? It has a nice GUI.

---

### Post by Raynman37 on 2008-12-23
Awesome how-to!  Wish I saw it before instead of wasting space in Absolute Beginners with a thread asking about everything you answered here!

---

### Post by rrob on 2008-12-28
I dont read whole discusion but i use apt-get clean too. It clean lot of space. Im using ubuntu on eee with 4GB ssd, i need each bite.
```
sudo apt-get clean
```
---
Have you tried his apt-get moo ? Try this apt-get install sl && sl .)

---

### Post by brookie on 2009-01-05
Thanks. I cleaned some stuff up and also installed fslint and kleansweep and compared the two apps. 
The problem is that both apps find so many things I don't know which files are safe to delete. I cannot find too much help for either. 

In fslint the options are:
Duplicates
Installed packages
Bad names
Name clashes
Temp files
Bad symlinks
Bad IDs
Empty directories
Non stripped binaries
Redundant Whitespace

Any help on this would be great. Thanks, brook

---

### Post by BilliShere on 2009-01-06
there is a program called bleach bit that works very much like crapcleaner / ccleaner for windows...

[http://freshmeat.net/projects/bleachbit/?branch_id=77067&release_id=291152](http://freshmeat.net/projects/bleachbit/?branch_id=77067&release_id=291152)

---

### Post by lsd on 2009-01-06
Things that fslint must and must NOT do:

Duplicates (safe for deleting)
Installed packages (DON'T REMOVE THIS!)
Bad names (non UTF8 compliant names, usually from fat32)
Name clashes (no idea)
Temp files (safe for deleting)
Bad symlinks (DON'T REMOVE THIS! a lot of icons use them)
Bad IDs (no idea)
Empty directories (they doesn't oversize our disk)
Non stripped binaries (no idea)
Redundant Whitespace (safe for deleting)

Be careful with bleachbit, it has more options (and so more insecure ones).

---

### Post by brookie on 2009-01-06
Thanks lsd! :)

---

### Post by -jay- on 2009-01-19
thank you  for the tips :)

---

### Post by johnamberg70 on 2009-01-31
To know and not to do is not yet to know-Zen proverb. Thanks for the info!

---

### Post by emnii on 2009-02-02
Thanks for this!

---

### Post by RedSingularity on 2009-02-08
Thanks!  Just what i needed!

---

### Post by mmck on 2009-02-11
thanks,for your patience in explaining step by step, in a quite simple way... very usefull... aprreciated...

---

### Post by thor790 on 2009-02-22
Worked great! thanks.

---

### Post by casmok on 2009-02-24
"localpurge" is not showing up when I key it into search in synaptic package manager. How do I find it??
Thanks

---

### Post by derklempner on 2009-02-24
Thanks for the tips, although I do have one question: how does one re-add locales to their system?

I ran **localepurge** and am now realizing that I didn't want to remove all the other locales.  I need to add German language support to my system again.  Please help!

---

### Post by derklempner on 2009-02-24
> **derklempner said:**
> Thanks for the tips, although I do have one question: how does one re-add locales to their system?

I ran **localepurge** and am now realizing that I didn't want to remove all the other locales.  I need to add German language support to my system again.  Please help!

Ah, I found the answer in another thread:
```
sudo dpkg-reconfigure localepurge
```

---

### Post by k3lt01 on 2009-02-25
> **casmok said:**
> "localpurge" is not showing up when I key it into search in synaptic package manager. How do I find it??
ThanksThats cause its "localepurge"

---

### Post by WOOHOOHOO on 2009-03-14
great help, thanks

---

### Post by ranch hand on 2009-03-15
I ran across this thread when hunting space saving ideas.  Just installed 8.10 on an old HP pavilion w/10Gb HDD.

This has freed up a little space.  A little space is GREAT.

Thanks a bunch.

---

### Post by spike_naples on 2009-04-01
Love this!:popcorn:

---

### Post by icejack_outlaw on 2009-04-03
thanks alot bro

---

### Post by Grievous on 2009-04-12
I was just wondering about how to remove some unnecessary files from my computer then I came across this article.  Thanks!

---

### Post by j8a on 2009-04-25
I think that whether you install or upgrade packages is usefull write:
apt-get autoclean
apt-get autoremove
apt-get purge *

Then, you could maintain the system clean.
Also, you can run synaptic before and uninstall older linux-headers, etc.

---

### Post by markitoxs on 2009-04-26
thank you for the guide.

---

### Post by spike_naples on 2009-04-29
Thank you Thank you Thank you!

---

### Post by goldblattster on 2009-05-15
A note-for the remove orphaned packages thing to work, you need to close Synaptic. Great how-to!

---

### Post by rpwdh on 2009-05-15
Thanks!

YOU ROCK!!!:guitar:

---

### Post by k3lt01 on 2009-05-15
> **goldblattster said:**
> A note-for the remove orphaned packages thing to work, you need to close Synaptic.Actually you don't, it will refresh itself and show even more Orphaned packages if they occur without closing it.

---

### Post by owl1 on 2009-06-21
Thank-you, Mr. Awesome!

---

### Post by ceciliaFX on 2009-06-22
> **sheepdogj15 said:**
> I know this is an old howto, but I had some suggestions for additions.

you can remove .deb files that are left over from installs. you only want to keep these around for if you need to reinstall, and even then apt/synaptic can re-download them.

```
sudo rm -v /var/cache/apt/archives/*.deb
```

after a while this directory gets full of stuff. i think at one time i had over 300 MB in package files.


you can also remove old log files. logrotate (installed by default in Ubuntu) archives log files as gunzip files. you might want to keep these in case you need to do some deep troubleshooting. I've never needed them though.

```
sudo rm -v /var/log/*.gz
```


/tmp and /var/tmp can regularly be cleaned out. I'd be careful about /var/tmp though, if Gnome/KDE is running and you clear out that directory, crazy things can happen. Maybe on every reboot?
thank you!

---

### Post by meazz1 on 2009-06-22
Very helpful thread.
Thanks

---

### Post by floydv on 2009-07-25
Great thread very helpful in keeping the computer clean, thanks for all the good reading here I am a newbie to this so I have been reading quite a bit and so far I do like this better than windows, not to mention Ubuntu has some of the best forums  out there.:D

---

### Post by Mightylink on 2009-08-12
Hello WackToMack, I know this thread is old but I wanted to provide my thanks for helping my get every megabyte of free space for my system. I have had a bit of bad luck lately and my 400gig drive has just fried, I have installed ubuntu on an old 4gig drive now and your tutorial has given me enough to at least watch videos and listen to music wile my replacement drive is being shipped to me.

Thank you for the great tutorial for getting more free space out of ubuntu, all your tips helped me very much.

---

### Post by Murdoc_of_puts on 2009-08-27
Just a quick question.  I was wondering if I had some funky setup or something, or if there was a way that I didn't know of to automatically get rid of all the extra linux headers, and old kernels without manually going in through synaptic and removing them?  I thought Something in here would have done that, but it didn't.  Either I did something wrong or I missed something.  Thanks.

---

### Post by ceciliaFX on 2009-08-29
is this for linux?? and not just for windows??

link and more details please

---

### Post by kevinguillorytraining on 2009-10-10
I rate this a truly excellent guide!

:KS :KS :KS :KS :KS :KS :KS :KS / 10

---

### Post by nooblot on 2009-10-11
> After installing anything with apt-get install, localepurge will remove all translation files and translated manpages in languages you cannot read.


so how to purge (for me) EXISTING non-EN files ?

edit: never mind, figured out:

[COLOR="Blue"]nooblot@ubuntu:/$ sudo localepurge
localepurge: Disk space freed in /usr/share/locale: 40124K
localepurge: Disk space freed in /usr/share/man: 2880K

Total disk space freed by localepurge: 43[/COLOR]004K

---

### Post by nooblot on 2009-10-11
> **ceciliaFX said:**
> 
> Originally Posted by sheepdogj15: [COLOR="Red"]sudo rm -v /var/cache/apt/archives/*.deb[/COLOR]

thank you!

well that is what "[COLOR="Red"]apt-get clean[/COLOR]" is for.....

---

### Post by ceciliaFX on 2009-10-14
> **nooblot said:**
> > After installing anything with apt-get install, localepurge will remove all translation files and translated manpages in languages you cannot read.


so how to purge (for me) EXISTING non-EN files ?

edit: never mind, figured out:

[COLOR="Blue"]nooblot@ubuntu:/$ sudo localepurge
localepurge: Disk space freed in /usr/share/locale: 40124K
localepurge: Disk space freed in /usr/share/man: 2880K

Total disk space freed by localepurge: 43[/COLOR]004K
I tried that and i got

sudo: localepurge: command not found

---

### Post by nooblot on 2009-10-14
> **ceciliaFX said:**
> I tried that and i got

sudo: localepurge: command not found

install it

```

sudo apt-get install localepurge

```

---

### Post by ssulaco on 2009-10-17
Ive had real good luck with Bleachbit.....mainly use Fslint for dups
read instructions for Bleachbit "carefully", Don't "check" (places) under "firefox"or you will nuke your bookmarks

---

### Post by ceciliaFX on 2009-10-20
> **nooblot said:**
> install it

```

sudo apt-get install localepurge

```

thanks

ok, so if i understand this I pick "en" from this huge list (for what I imagine is English) and that means everything else is deleted?

don't want to risk deleting until I know what I'm doing  :)

---

### Post by k3lt01 on 2009-10-20
> **ceciliaFX said:**
> thanks

ok, so if i understand this I pick "en" from this huge list (for what I imagine is English) and that means everything else is deleted?

don't want to risk deleting until I know what I'm doing  :)Yes thats it, if you tick "en" only the various English translations are kept on your machine. Everything else like French, Spanish, Swahili etc are deleted.

---

### Post by ssulaco on 2009-10-20
Murdoc,You can use startup manager to limit the number of Kernels to keep..recommend keeping at least 2.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by mtub on 2009-10-27
I found [this ]("https://help.ubuntu.com/community/StartUpManager")regarding StartUp-Manager.

**Limit the number of kernels** / **Number of kernels to keep**:
"This setting does not change the number of kernels kept on the system - only the number *displayed*."

---

### Post by ssulaco on 2009-10-27
> **mtub said:**
> 
"This setting does not change the number of kernels kept on the system - only the number *displayed*."
you are correct,mtub,my mistake.verify the kernel you want to dump and run
```
sudo apt-get remove --purge 9.6.28-XX-*
```
where XX is the kernel you want to remove.
make sure as to not remove the 2 most current kernels

---

### Post by johnnybirdman on 2009-10-28
> **ssulaco said:**
> you are correct,mtub,my mistake.verify the kernel you want to dump and run
```
sudo apt-get remove --purge 9.6.28-XX-*
```
where XX is the kernel you want to remove.
make sure as to not remove the 2 most current kernels

I'm not sure exactly what you are trying to do but if you want to remove old kernels there is a script that can make it easy for you, i've been using it for a while without problems.
Check out [[COLOR="DarkOrange"]**_this post here_**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8039958&postcount=7").
Run the script, then run just 'rmkernel' and it will take care of the rest.

J.

---

### Post by BlastXng on 2009-12-06
Worked really well!
:popcorn:

Excellent!

---

### Post by ravisghosh on 2009-12-12
> Tip #4 - Getting rid of "orphaned" packages 

With this tip, I removed lot of packages using Synaptic. Then I ran the upgrade using aptitude and it installed all the packages that I had removed previously. **Does that mean "orphaned" packages are not really orphaned?**

Also, "Installed (local and obsolete)" sections shows googleearth which I do use. Why it is in Obsolete?

---

### Post by k3lt01 on 2009-12-12
> **ravisghosh said:**
> Also, "Installed (local and obsolete)" sections shows googleearth which I do use. Why it is in Obsolete?It's not "Obsolete", it's "Local" because it's from the Medibuntu repository.

---

### Post by samijildeh on 2009-12-23
> **Ferio said:**
> "Autoclean" is not in the Ubuntu repositories, where could I find it?


just type "sudo apt-get autoclean" (withput "") , and it's autoclean not Autoclean [small letters].

---

### Post by Cabs21 on 2010-01-05
This is exactly what I am looking for.  Thanks I needed help with this and will def try it soon.

---

### Post by cabby2litre on 2010-02-24
Thank you for this thread!!!! Very helpful for a newbie like myself!!

---

### Post by daasdingo on 2010-02-26
thanks for the tutorial,
always wondered how to get rid of the config files

---

### Post by shafin on 2010-03-01
Thanks a lot.
BTW, can you please update the tutorial with reference to Computer Janitor?

---

### Post by tommark on 2010-03-01
Thank you!  And to think that I was just beginning to learn all those languages just so I could use their language files.

---

### Post by linxuser14 on 2010-03-20
Thanks for this very useful info. I'd installed a OEM image and ended up having to delete languages galore. ;)

---

### Post by freegeeky on 2010-03-22
I tried the steps here: [http://panupongsk.blogspot.com/2010/03/once-in-while-you-may-want-to-do-some.html](http://panupongsk.blogspot.com/2010/03/once-in-while-you-may-want-to-do-some.html) and cleared a little over a gig. 

Yet, I am still at 87% capacity ... is this the reason for the occasional freezes?

---

### Post by rcktsingh on 2010-05-08
Thank you so much. I was looking for one like this. Awesome tut.:guitar:

---

### Post by HoKaze on 2010-05-08
Thanks for the howto. 
I decided that these tasks were important enough to do on a semi-regular basis and that newbies may benefit from having it all in a GUI, so I wrote a script for it, which can be found [here]("http://gtk-apps.org/content/show.php/filecleaner+script?content=124401"). 
It requires zenity to run (so sudo apt-get install zenity) and allows you to do everything mentioned in this howto except deal with orphaned files (I may add that later). It also includes apt-get clean for cleaning apt's cache.

---

### Post by zl1ogx on 2010-05-16
Hi

Thanks for this one, I use a eeepc with only 4gb of main h/d space with a 8gb SD card for data, so keeping the main partitions clean helped me clear nearly a 1gb.

Thnaks again

---

### Post by krogmank on 2010-05-30
Wow.  Fast, simple cleanup for Ubuntu.  Better than the method I had been using.

Thanks for this, 

Karl

---

### Post by waynemeat on 2010-06-12
Just what I was looking for. Awesome thank you.:KS

---

### Post by rcktsingh on 2010-06-22
I am not sure if the following link has been posted before in this thread, but I feel its worthy enough to put it again:


[https://help.ubuntu.com/community/Diet%20Ubuntu](https://help.ubuntu.com/community/Diet%20Ubuntu)

Nice stuffs about cleaning your system.

Enjoy:guitar:

---

### Post by jfbooth on 2010-06-27
> **HoKaze said:**
> Thanks for the howto. 
I decided that these tasks were important enough to do on a semi-regular basis and that newbies may benefit from having it all in a GUI, so I wrote a script for it, which can be found [here]("http://gtk-apps.org/content/show.php/filecleaner+script?content=124401"). 
It requires zenity to run (so sudo apt-get install zenity) and allows you to do everything mentioned in this howto except deal with orphaned files (I may add that later). It also includes apt-get clean for cleaning apt's cache.

Very considerate.  I assume part of your intent was to help out noobs .. so you might give execution instructions and dependencies (ZENITY)at your link:

[http://gtk-apps.org/content/show.php/filecleaner+script?content=124401](http://gtk-apps.org/content/show.php/filecleaner+script?content=124401)

Being a noob myself, took me hours to find out how to execute the script .. emphasis **NOOB**. I was told ./filename would do it, though have not tried it yet.  JUST A SUGGESTION.

---

### Post by jschmeau on 2010-07-24
I recommend UbuntuTweak.  
You can download and install the .deb from the website.  Google 'ubuntutweak'.  
Among the numerous useful features, it includes a package cleaner that will clean unneeded packages, package cache, confg files, and old kernels.  
I've been using it for over a year and have never had any issues.  It's a "must-have".

---

### Post by k3lt01 on 2010-07-24
> **jschmeau said:**
> I recommend UbuntuTweak.  
You can download and install the .deb from the website.  Google 'ubuntutweak'.  
Among the numerous useful features, it includes a package cleaner that will clean unneeded packages, package cache, confg files, and old kernels.  
I've been using it for over a year and have never had any issues.  It's a "must-have".Unfortunately I have seen a few noobs break their system with UT simply because they don't understand, and the people who are recommending it on the forum don't explain, how to use it. It is like any tool, it has its uses but if you don't know what your doing you can cause yourself problems.

I recommend using the tools Ubuntu comes with Ubuntu and that are in the Repositories. Learn how to use them properly by using tutorials such as this one then move onto other things like UT.

Nothing is a "must have". If you feel like recommending something please explain how to use it. Better still start your own thread giving a detailed explanation of it just like the OP has done on this thread.

---

### Post by jschmeau on 2010-07-28
> **k3lt01 said:**
> Unfortunately I have seen a few noobs break their system with UT simply because they don't understand, and the people who are recommending it on the forum don't explain, how to use it. It is like any tool, it has its uses but if you don't know what your doing you can cause yourself problems.

I recommend using the tools Ubuntu comes with Ubuntu and that are in the Repositories. Learn how to use them properly by using tutorials such as this one then move onto other things like UT.

Nothing is a "must have". If you feel like recommending something please explain how to use it. Better still start your own thread giving a detailed explanation of it just like the OP has done on this thread.

Thanks for the advice.  I posted what I considered to be information that was useful and in accordance with the thread title and the original post.  I did not just enter some random thread and suggest UbuntuTweak as your post seems to imply.  Furthermore... Surely you can't be serious about posting instructions on using UbuntuTweak???? I'll do that when you post instructions on how to use linux.:p   Anyone can go to the UT website.  There you can view instructions on its proper usage and installation.  True, like any tool it could cause trouble in the wrong hands, but so can synaptic, apt, gparted, and a host of others.  I would say it is at least as safe if not safer for a noob than directly removing packages from synaptic or apt.

Also, in the spirit of the above poster, all users of this forum should recognize that the information presented here comes as-is, without warranty, buyer beware.  In that regard we agree... be careful what you sudo :-)

---

### Post by k3lt01 on 2010-07-28
> **jschmeau said:**
> Thanks for the advice.  I posted what I considered to be information that was useful and in accordance with the thread title and the original post.  I did not just enter some random thread and suggest UbuntuTweak as your post seems to imply.  Furthermore... Surely you can't be serious about posting instructions on using UbuntuTweak???? I'll do that when you post instructions on how to use linux.:p   Anyone can go to the UT website.  There you can view instructions on its proper usage and installation.  True, like any tool it could cause trouble in the wrong hands, but so can synaptic, apt, gparted, and a host of others.  I would say it is at least as safe if not safer for a noob than directly removing packages from synaptic or apt.

Also, in the spirit of the above poster, all users of this forum should recognize that the information presented here comes as-is, without warranty, buyer beware.  In that regard we agree... be careful what you sudo :-)
Hmmmm. Did you not say "It's a "must-have"? This is something I really doubt to be true as I don't use it and many people I know don't use it as they are happy with the tools Ubuntu installs as standard. This is the Official Ubuntu forum, it isn't the UT forum. If UT is the "must-have" that you say it is then why isn't it part of a standard install?

Read [Eight Fatal Mistakes]("http://sites.google.com/site/easylinuxtipsproject/fatalmistakes") to see just a couple of the issues UT can cause if people don't understand what they are doing.

---

### Post by jschmeau on 2010-07-28
> **k3lt01 said:**
> Hmmmm. Did you not say "It's a "must-have"? This is something I really doubt to be true as I don't use it and many people I know don't use it as they are happy with the tools Ubuntu installs as standard. This is the Official Ubuntu forum, it isn't the UT forum. If UT is the "must-have" that you say it is then why isn't it part of a standard install?

Read [Eight Fatal Mistakes]("http://sites.google.com/site/easylinuxtipsproject/fatalmistakes") to see just a couple of the issues UT can cause if people don't understand what they are doing.

Ok. You're right. People should definitely understand what they are doing before they do it.  Hard to disagree with that.  I regret saying it is a "must-have", although I DID put it in qoutes. :-)  I honestly don't quite understand your hostility towards a perfectly fine third-party app though.  All applications should be used with caution.  Any file browser with sudo priveledges  can allow you to damage your system.  Do you have a list of the fatal mistakes that can be caused by not understanding what your keyboard can do? 

So to hopefully put an end to this discussion that is now completely off topic...
now that I've been educated, **I WOULD RECOMMEND THAT NO ONE *EVER* USE ANY SOFTWARE THAT IS NOT IN THE REPOSITORIES.**

In the future, I would also recommend NOT talking down to people when responding to another's post... don't let your arrogance seep through the keyboard.

Cheers!

---

### Post by k3lt01 on 2010-07-28
I realise I seem arrogant but having said that alot of things are how we perceive the other person to be reacting.

I'm not hostile towards UT, I have used it and find it to be a decent application if the person using it understands what it can do. I no longer us it because I have slowly become more proficient with the terminal and actually find it more rewarding because I am learning the insides of my favourite OS in the process.

Anywhoooooo, have a great day my friend :)

---

### Post by cpcpcp on 2010-08-03
Thanks** worked well with my version 10.04.**

I would add that after seeing the warning with the localepurge routine I ran it and then then un-installed it afterwards.
good stuff

chris

---

### Post by cpcpcp on 2010-08-03
> **jfbooth said:**
> Very considerate.  I assume part of your intent was to help out noobs .. so you might give execution instructions and dependencies (ZENITY)at your link:

[http://gtk-apps.org/content/show.php/filecleaner+script?content=124401](http://gtk-apps.org/content/show.php/filecleaner+script?content=124401)

Being a noob myself, took me hours to find out how to execute the script .. emphasis **NOOB**. I was told ./filename would do it, though have not tried it yet.  JUST A SUGGESTION.

As they did not give this help and you have spent hours on it have you the answer to share or should I too just blunder around trying to get it to work?

I do like the idea of a simple script although following the instructions one by one was easy enough - a good clear "how to"

Chris

---

### Post by Denis Krajnc on 2010-08-06
Thank you very much!

---

### Post by ParadoxBlue on 2010-09-13
> **k3lt01 said:**
> I realise I seem arrogant but having said that alot of things are how we perceive the other person to be reacting.

I'm not hostile towards UT, I have used it and find it to be a decent application if the person using it understands what it can do. I no longer us it because I have slowly become more proficient with the terminal and actually find it more rewarding because I am learning the insides of my favourite OS in the process.

Anywhoooooo, have a great day my friend :)
Good posts by all and I personally I agree on erring on the side of caution. I'm new to Linux/Ubuntu but have been using Windows for close to 20 years although I'm Windows-free now and I have yet to miss it. I appreciate the link to the 8 Fatal Mistakes. I do have Tweak installed on my system but only to see what all it can do and then figure out how to do it for myself. The Applications section of Tweak is particularly useless as everything can be done through Ubuntu without the use of any 3rd party program. As far as I can tell pretty much anything Tweak does can be accomplished with the software included with Ubuntu. A lot of it is just a matter of fiddling with Gconf and Compiz or other settings.

I've just had Ubuntu 9.10 installed on my system since May 29th although I ran it from the LiveCD for about 6 weeks before committing  to it. And speaking of being cautious I believe I've figured out my upgrade routine for new Ubuntu releases. Upgrade to the most current release about 2-4 weeks before the next release comes out. That means I'll be upgrading to Lucid Lynx 10.04 by the end of this month and hey maybe this coming March or so I might just give Meerkat a shot.

---

### Post by AlexanderDGreat on 2010-09-13
I read the 8 fatal mistakes it says,

> In System - Administration - Software Sources - tab "Other Software", you can enable the ubuntu lucid partner  repository **(it's not enabled by default).** This gives you access to certain software from companies (the partners) that have entered into an agreement with Canonical. 

BUT it is Enabled By Default when I installed my Ubuntu. So do I need to uncheck this?

---

### Post by asavik on 2010-09-20
Any thoughts on all the files that are automatically added to /usr/share/doc?

The must be a gazillion changelogs and copyright files there. Do any of them serve any *practical* purpose whatsoever? I've never accessed one of them, and I tinker around a lot with my system.

---

### Post by Eskobar on 2010-09-20
Worked flawlessly on 10.04, thank you kindly!

---

### Post by asavik on 2010-09-21
To answer my own question about the changelog et al. files. They serve no purpose (except, of course if want to read them, which you don't), so you can safely remove them.

I removed **2,000** folders with **10,000** files that way...

---

### Post by aliceinchains on 2010-10-01
Thank you ! Excellent post and very well written.

---

### Post by nanogopi on 2010-10-15
Thank You so much., It was a really helpful How-to., Long live the spirit of linux community.,:guitar:

---

### Post by baraka607 on 2010-10-16
Hey <sudo apt-get autoclean> works great for me. thanks

---

### Post by mp5shooter on 2010-10-25
> **asavik said:**
> To answer my own question about the changelog et al. files. They serve no purpose (except, of course if want to read them, which you don't), so you can safely remove them.

I removed **2,000** folders with **10,000** files that way...

That sounds like a good idea actually, thanks!

---

### Post by Thras0 on 2010-11-27
thank you for all this useful tips.i love having a clean system :)

---

### Post by shubhamearth on 2010-12-11
well in my computer it ai'nt showing any option of residual config in the status tab:confused:

---

### Post by sairam2000 on 2010-12-19
as said in #1, i removed two entries in uninstalled (residual config) and it uninstalled vlc player and many other softwares. oh my God!

---

### Post by k3lt01 on 2011-01-04
Another item that is probably not needed by everyone is ALL the xserver-xorg-video-xxxxx (xxxx being the name of the driver) driver modules.

To find out what one you need, and therefor what ones you don't need, run 

```
lspci
```in a teminal. It should come up with an output like this
```
root@michael-laptop:/home/michael# lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
[B]00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)[/B]
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Ethernet controller: InProComm Inc. IPN 2220 802.11g
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
root@michael-laptop:/home/michael# 

```Taking note of the line I have highlighted it tells me I have an 82852/855GM Integrated Graphics Device so I look at the xserver.xorg entries in synaptic and carefully uninstall (meaning I look to make sure it doesn't uninstall things I do still need) any entries that are not Intel.

This does not free up much space in comparison to other hints in the OP but once you have done the OP and want to make your machine leaner this is another option.

---

### Post by OrionCristopher on 2011-02-03
Great Post!! Instant Bookmark..  Ubuntu is proving to be very user friendly and the community is great...

---

### Post by batharoy on 2011-02-19
This is the code I use to clean it all at once.
Cleans out the download cache, autoremove files and leftover config files, it then prints it into the terminal as it runs and a text file in your home folder.

```
sudo apt-get clean && sudo apt-get autoremove --purge -y $(dpkg -l | grep '^rc' | awk '{print $2}') >remove.txt
```

And heres a sample of the printout.

> Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be REMOVED:
  liblinebreak1* libzlcore-data* libzlcore0.10* libzltext-data* libzltext0.10*
  libzlui-qt4*
0 upgraded, 0 newly installed, 6 to remove and 3 not upgraded.
After this operation, 3,502kB disk space will be freed.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 133714 files and directories currently installed.)

Removing libzltext0.10 ...

Purging configuration files for libzltext0.10 ...

Removing liblinebreak1 ...

Purging configuration files for liblinebreak1 ...

Removing libzlui-qt4 ...

Removing libzlcore0.10 ...

Purging configuration files for libzlcore0.10 ...

Removing libzlcore-data ...

Removing libzltext-data ...

Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

---

### Post by donniezazen on 2011-03-02
This is a really old post. Is this still relevant for natty? What do you guys think of bleachbit?

---

### Post by rvchari on 2011-03-02
> **WackToMack said:**
> **Hello everyone!  So, do you ever get the feeling that your system is being flooded with a bunch of junk files that you can't get rid of?  I know I do.  Well, I'm going to show you a few ways to get rid of most, if not all, of those annoying junk files.** \\:D/ 

**[COLOR="Red"]Please note[/COLOR]** : If doing any of this messes up your system, don't blame me.  Everything worked flawlessly on my machine.  Everthing should be beer 'n skittles for you if you follow this HOWTO step-by-step.  Good luck! :D

========================================================================================================================

_[SIZE="3"]**Tip #1 - Getting rid of Residual Config packages**[/SIZE]_ - In Synaptic Package Manger, there is a built-in feature that gets rid of old Residual Config packages.  Residual Config packages are usually dependency packages that are left behind after you uninstall a package from your machine.  To use this feature, go to **System > Administration > Synaptic Package Manager**.  On the bottom left hand corner of the window, click the **Status** button.  In the list above the **Sections**, **Status**, **Search**, and **Custom **buttons, you should see the following text:


Click on the "Residual config" text. (If the "Residual config dialogue does not appear, that means you do not have any Residual Config packages on your machine and you can skip down to Tip #2.)  Do you see the packages that popped up in the window on the right?  Those are the Residual Config packages.  To get rid of these pests, click on the box to the left of the package name and select "Mark for Complete Removal".  After you have done that for all of the Residual Config packages, look at the top of the Synaptic Package Manger window.  Do you see the green check mark with the text "Apply" right under it?  Click that button, and you'll flush all those Residual Config packages down the toilet! :KS

========================================================================================================================

_[SIZE="3"]**Tip #2 - Getting rid of partial packages**[/SIZE]_ - This is yet another built-in feature, but this time it is not used in Synaptic Package Manager.  It is used in the Terminal.  To access the Terminal, go to **Applications > Accessories > Terminal**.  Now, in the Terminal, key in the following command (or you can just copy and paste from here):

```
sudo apt-get autoclean
```
Enter your password when prompted and press **Enter**.  See the package names that appeared in the Terminal?  Those were partial packages that have just been deleted.  Say goodbye!  That's it!  This command deletes the not-so-fully-downloaded packages that you acquire when a package that is being downloaded is suddenly cancelled.  This is my favorite little trick when it comes to getting rid of junk files. :p 

========================================================================================================================

_[SIZE="3"]**Tip #3 - Getting rid of unnecessary locale data**[/SIZE]_ - For this tip, you need to download the "localepurge" package found in Synaptic Package Manager.  "localepurge" is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.

To open Synaptic Package Manager, follow the instructions in Tip #1.  After opening up Synaptic Package Manager, click the **Sections** button on the bottom left hand corner of the window, if it is not already clicked.  Next, at the top of the Synaptic Package Manager window, click the **Search** button.  In the search window, key in the following text :



Did the "localepurge" package popup in the package window?  It probably did, unless you do not have the correct Repositories.  Now, click on the box next to the "localepurge" package name.  Click on **Mark for Installation**.  Now click the **Apply** button at the top of the window and wait for the downloading and installing of the "localepurge" package to finish.  Once it is done, a new window should popup that has a bunch of abbreviations on it.  for example: 


You want to select the abbreviation of the language that you speak, or use with Ubuntu, ignoring the capitalized ones.  For example, I speak english, so I would select the "en" abbreviation.  A french speaker would select the "fr" abbreviation.  So on and so forth...  Then click next.  All done! ;)

========================================================================================================================

_[SIZE="3"]**Tip #4 - Getting rid of "orphaned" packages**[/SIZE]_ - For this tip, you need to download the "deborphan" package found in Synaptic Package Manager.  "deborphan" finds "orphaned" packages on your system.  It determines which packages have no other packages depending on their installation, and shows you a list of these packages. It is most useful when finding libraries, but it can be used on packages in all sections...

To open Synaptic Package Manager, follow the instructions in Tip #1.  After opening up Synaptic Package Manager, click the **Sections** button on the bottom left hand corner of the window, if it is not already clicked.  Next, at the top of the Synaptic Package Manager window, click the **Search** button.  In the search window, key in the following text :


Did the "deborphan" package popup in the package window?  It probably did, unless you do not have the correct Repositories.  Now, click on the box next to the "deborphan" package name.  Click on **Mark for Installation**.  Now click the **Apply** button at the top of the window and wait for the downloading and installing of the "deborphan" package to finish.  Once that is done, open up the Terminal.  Instructions for doing that are located in Tip #2.  After you have gotten the Terminal open, key in the following command (or copy and paste from here):

```
sudo deborphan | xargs sudo apt-get -y remove --purge
```
Enter your password when prompted and press **Enter**.  See the package names that appeared in the Terminal?  Those were orphaned packages that have just been deleted.  Say goodbye!  This is my second favorite way of dealing with junk files. :cool:

========================================================================================================================

_[SIZE="3"]**Tip #5 - Adding a "Find orphaned packages" to Synaptic Package Manager**[/SIZE]_ - This is not really much of a tip on how to get rid of junk files.  It's more like adding a "deborphan" shortcut to Synaptic Package Manager so that you don't have to use the Terminal to find "orphaned" packages.

**[COLOR="Red"]Please note:[/COLOR]** You must have the "deborphan" package installed or else this will not work.

To start this out, open up Synaptic Package Manager with the instructions from Tip #1.  Now, at the top of the Synaptic Package Manager window, click  the **Settings** button, followed by the **Filters** button.  In the Filters window, on the bottom left hand corner, push the **New** button.  You can name the new Filter if you like, but it is not necessary.  I named mine "Orphaned".  With your new Filter selected, in the "Status" tab on the right, click the **Deselect All** button.  Next, check the "Orphaned" option under the "Other" category.  Then click the **OK** button.

To use this new filter, click the **Custom** button on the bottom left hand corner of the Synaptic Package Manager window.  You should see the following text, or something similiar :


Click on the "(Whatever you named your "deborphan Filter)" text.  Do you see the packages that popped up in the window on the right?  Those are the "orphaned" packages.  To get rid of these buggers, click on the box to the left of the package name and select "Mark for Complete Removal".  After you have done that for all of the "orphaned" packages, look at the top of the Synaptic Package Manger window.  Do you see the green check mark with the text "Apply" right under it?  Click that button, and you'll get rid of all the "orphaned" packages forever (Probably)! :mrgreen: 

========================================================================================================================

Well, I hope all of you enjoyed my HOWTO and found it quite easy to follow.  Whew, this thing took me over an hour to make!  LOL!  If I have made any mistakes, just let me know.  Catch you later! :D

i think package "AILURUS" takes care of all this with interactive gui interface, it also removes old unused kernel images and headers on one go

---

### Post by VMC on 2011-03-03
> **soham_1207 said:**
> This is a really old post. Is this still relevant for natty? What do you guys think of bleachbit?

bleachbit is all I use. Natty, Lucid, Mint, etc.

---

### Post by k3lt01 on 2011-03-03
> **soham_1207 said:**
> This is a really old post. Is this still relevant for natty? What do you guys think of bleachbit?It is relevant for Linux in general thats the beauty of Linux.

Bleachbit has its purpose and so does this method. This method cleans up Linux in general, bleachbit will clean everything you tell it to including Firefox etc. Just be aware that ticking every box on bleachbit can destroy information you may want later so you really need to know and understand each and every feature that bleachbit offers before you go ahead and use it.

---

### Post by jfbooth on 2011-03-06
> **batharoy said:**
> This is the code I use to clean it all at once.
Cleans out the download cache, autoremove files and leftover config files, it then prints it into the terminal as it runs and a text file in your home folder.

```
sudo apt-get clean && sudo apt-get autoremove --purge -y $(dpkg -l | grep '^rc' | awk '{print $2}') >remove.txt
```

And heres a sample of the printout.

Did not work for me.  Ran the code from terminal .. no output .. just a new prompt.  No file saved in HOME folder.  No output displayed in terminal.

Xubuntu 10.10, Maverick Meerkat

Edit:  OOOOPS .. remove.txt appeared on Desktop.  Here is its content:

Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by KoRnKloWn on 2011-05-01
For a simpler way to delete orphaned packages, in the Ubuntu repository there is a program called gtkorphan, or in the Software Center simply "Remove Orphaned Packages", it gives you the choice to just view the orphaned packages in the libraries folders so that you don't have a huge list of programs that aren't required by the OS.

---

### Post by lifetonjoyu on 2011-05-22
nice one buddy....its v.cumbersome to remove such packges for new users......this command helps.....

---

### Post by ByTheNine on 2011-05-22
Help! Tip #1 isn't working for me! It will not let me click "apply". I can click on packages for removal and all that, but the "apply" button is unclickable. This JUST happened after I upgraded from 10.10 to 11.04.

---

### Post by hackedhacker on 2011-05-26
nice share man...
But somehow, it seems like when I do tip #1 to tip #4, only tip #1 did remove some unused package for me...
Maybe coz I'm still new in Ubuntu, n haven't tried everything yet...

By the way, Like ur sig WackToMack...
:guitar:

---

### Post by unadulterated on 2011-06-26
I am using NATTY and facing the same problem with Tip # 1.. there are lot of entries in the list of residual config.. but after selecting all the apply button is not working?? any ideas?

---

### Post by avengery on 2011-06-27
nice one thanks for the tricks

---

### Post by bishop379 on 2011-07-09
I'm glad I found this, thanx again to WacktoMack, I especially like the...

sudo apt-get moo

---

### Post by Patsfriend on 2011-11-27
Thanks for these excellent Tips 
Very helpful and well done!
:D

---

### Post by boazjones on 2011-12-06
Thank you!  :KS

---

### Post by kappel79x64 on 2011-12-07
hi all, 

thx for the cleaning instructions !

my 11.10 kubuntu system is 6 days old and had allready over 2gb trash , maybe because i changed to a kubuntu/ppa.

cheers

---

### Post by Gremlinzzz on 2012-02-20
> **WackToMack said:**
> **Hello everyone!  So, do you ever get the feeling that your system is being flooded with a bunch of junk files that you can't get rid of?  I know I do.  Well, I'm going to show you a few ways to get rid of most, if not all, of those annoying junk files.** \\:D/ 

**[COLOR="Red"]Please note[/COLOR]** : If doing any of this messes up your system, don't blame me.  Everything worked flawlessly on my machine.  Everthing should be beer 'n skittles for you if you follow this HOWTO step-by-step.  Good luck! :D

========================================================================================================================

_[SIZE="3"]**Tip #1 - Getting rid of Residual Config packages**[/SIZE]_ - In Synaptic Package Manger, there is a built-in feature that gets rid of old Residual Config packages.  Residual Config packages are usually dependency packages that are left behind after you uninstall a package from your machine.  To use this feature, go to **System > Administration > Synaptic Package Manager**.  On the bottom left hand corner of the window, click the **Status** button.  In the list above the **Sections**, **Status**, **Search**, and **Custom **buttons, you should see the following text:


Click on the "Residual config" text. (If the "Residual config dialogue does not appear, that means you do not have any Residual Config packages on your machine and you can skip down to Tip #2.)  Do you see the packages that popped up in the window on the right?  Those are the Residual Config packages.  To get rid of these pests, click on the box to the left of the package name and select "Mark for Complete Removal".  After you have done that for all of the Residual Config packages, look at the top of the Synaptic Package Manger window.  Do you see the green check mark with the text "Apply" right under it?  Click that button, and you'll flush all those Residual Config packages down the toilet! :KS

========================================================================================================================

_[SIZE="3"]**Tip #2 - Getting rid of partial packages**[/SIZE]_ - This is yet another built-in feature, but this time it is not used in Synaptic Package Manager.  It is used in the Terminal.  To access the Terminal, go to **Applications > Accessories > Terminal**.  Now, in the Terminal, key in the following command (or you can just copy and paste from here):

```
sudo apt-get autoclean
```
Enter your password when prompted and press **Enter**.  See the package names that appeared in the Terminal?  Those were partial packages that have just been deleted.  Say goodbye!  That's it!  This command deletes the not-so-fully-downloaded packages that you acquire when a package that is being downloaded is suddenly cancelled.  This is my favorite little trick when it comes to getting rid of junk files. :p 

========================================================================================================================

_[SIZE="3"]**Tip #3 - Getting rid of unnecessary locale data**[/SIZE]_ - For this tip, you need to download the "localepurge" package found in Synaptic Package Manager.  "localepurge" is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.

To open Synaptic Package Manager, follow the instructions in Tip #1.  After opening up Synaptic Package Manager, click the **Sections** button on the bottom left hand corner of the window, if it is not already clicked.  Next, at the top of the Synaptic Package Manager window, click the **Search** button.  In the search window, key in the following text :



Did the "localepurge" package popup in the package window?  It probably did, unless you do not have the correct Repositories.  Now, click on the box next to the "localepurge" package name.  Click on **Mark for Installation**.  Now click the **Apply** button at the top of the window and wait for the downloading and installing of the "localepurge" package to finish.  Once it is done, a new window should popup that has a bunch of abbreviations on it.  for example: 


You want to select the abbreviation of the language that you speak, or use with Ubuntu, ignoring the capitalized ones.  For example, I speak english, so I would select the "en" abbreviation.  A french speaker would select the "fr" abbreviation.  So on and so forth...  Then click next.  All done! ;)

========================================================================================================================

_[SIZE="3"]**Tip #4 - Getting rid of "orphaned" packages**[/SIZE]_ - For this tip, you need to download the "deborphan" package found in Synaptic Package Manager.  "deborphan" finds "orphaned" packages on your system.  It determines which packages have no other packages depending on their installation, and shows you a list of these packages. It is most useful when finding libraries, but it can be used on packages in all sections...

To open Synaptic Package Manager, follow the instructions in Tip #1.  After opening up Synaptic Package Manager, click the **Sections** button on the bottom left hand corner of the window, if it is not already clicked.  Next, at the top of the Synaptic Package Manager window, click the **Search** button.  In the search window, key in the following text :


Did the "deborphan" package popup in the package window?  It probably did, unless you do not have the correct Repositories.  Now, click on the box next to the "deborphan" package name.  Click on **Mark for Installation**.  Now click the **Apply** button at the top of the window and wait for the downloading and installing of the "deborphan" package to finish.  Once that is done, open up the Terminal.  Instructions for doing that are located in Tip #2.  After you have gotten the Terminal open, key in the following command (or copy and paste from here):

```
sudo deborphan | xargs sudo apt-get -y remove --purge
```
Enter your password when prompted and press **Enter**.  See the package names that appeared in the Terminal?  Those were orphaned packages that have just been deleted.  Say goodbye!  This is my second favorite way of dealing with junk files. :cool:

========================================================================================================================

_[SIZE="3"]**Tip #5 - Adding a "Find orphaned packages" to Synaptic Package Manager**[/SIZE]_ - This is not really much of a tip on how to get rid of junk files.  It's more like adding a "deborphan" shortcut to Synaptic Package Manager so that you don't have to use the Terminal to find "orphaned" packages.

**[COLOR="Red"]Please note:[/COLOR]** You must have the "deborphan" package installed or else this will not work.

To start this out, open up Synaptic Package Manager with the instructions from Tip #1.  Now, at the top of the Synaptic Package Manager window, click  the **Settings** button, followed by the **Filters** button.  In the Filters window, on the bottom left hand corner, push the **New** button.  You can name the new Filter if you like, but it is not necessary.  I named mine "Orphaned".  With your new Filter selected, in the "Status" tab on the right, click the **Deselect All** button.  Next, check the "Orphaned" option under the "Other" category.  Then click the **OK** button.

To use this new filter, click the **Custom** button on the bottom left hand corner of the Synaptic Package Manager window.  You should see the following text, or something similiar :


Click on the "(Whatever you named your "deborphan Filter)" text.  Do you see the packages that popped up in the window on the right?  Those are the "orphaned" packages.  To get rid of these buggers, click on the box to the left of the package name and select "Mark for Complete Removal".  After you have done that for all of the "orphaned" packages, look at the top of the Synaptic Package Manger window.  Do you see the green check mark with the text "Apply" right under it?  Click that button, and you'll get rid of all the "orphaned" packages forever (Probably)! :mrgreen: 

========================================================================================================================

Well, I hope all of you enjoyed my HOWTO and found it quite easy to follow.  Whew, this thing took me over an hour to make!  LOL!  If I have made any mistakes, just let me know.  Catch you later! :D

These commands bring back memories do they still work?

---

### Post by jfbooth on 2012-02-20
> **Gremlinzzz said:**
> These commands bring back memories do they still work?

I still use these tips .. on Xubuntu 11.10.  Work great.  There are a couple of omissions in the tips but easy to work around.

---

### Post by purgeinator on 2012-05-02
I am having problem with "Synaptic Package Manager", I have added many custom filter but can't remove them. When I go to Settings>>Filters select any filter and try to delete it nothing happens. Does anyone else facing same problem? I tried to remove using "sudo apt-get purge synaptic" cmd to remove any config file, but when I reinstall its still there. How do I get rid of those filters?

---

### Post by jfbooth on 2012-05-02
> **purgeinator said:**
> I am having problem with "Synaptic Package Manager", I have added many custom filter but can't remove them. When I go to Settings>>Filters select any filter and try to delete it nothing happens. Does anyone else facing same problem? I tried to remove using "sudo apt-get purge synaptic" cmd to remove any config file, but when I reinstall its still there. How do I get rid of those filters?

This is a KNOWN bug in Synaptics.  Developer's know about it.  It has a LOW PRIORITY for a fix however.  I reported it about a week ago, .. and got an email that it was a known bug.  I have searched for it so I can show you, but I cannot find it with google.  Don't know how to find it.

EDIT:  here is a link to the bug as listed in Launchpad:  [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/779756](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/779756)

---

### Post by purgeinator on 2012-05-04
Thanks, but as I asked earlier how can I remove config files for synaptic, since 'apt-get purge' didn't work. I want to remove synaptic config files, so that on reinstall there is no custom filter created by me.

---

### Post by michaelam on 2012-12-20
Great tips...thanks

---

### Post by DestructiveLabs on 2013-06-20
BOOM! Clean) thanks for that quick tutorial!

---

### Post by RavenLX on 2013-06-25
Great tips! I agree about the orphaned files though. You may want to do the Synaptic Package Manager one and just go through and click on each one and read what it does. Some you may want to keep after all.

---

### Post by invictuschamp on 2013-07-07
Great thanks!  I had to get the synaptic to apply localepurge/deborphan. Once input the install, I have seen them operating :).

---

