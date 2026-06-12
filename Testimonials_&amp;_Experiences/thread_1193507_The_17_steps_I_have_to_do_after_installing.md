---
title: "The 17 steps I have to do after installing"
date: 2009-06-21
forum: Testimonials &amp; Experiences
---

### Post by Jeema on 2009-06-21
I recently reinstalled Ubuntu on a new hard drive I bought.  This is the second time I've installed it, the first being 8.04 a while back.

Afterwards, I realized that it seemed like it was taking a really long time to get the system how I liked it, so I put together a list of all the annoying things I had to do after install.  And here it is!:

1) Activate root login capability
2) Create additional users (don't remember it asking during the install at any rate)
3) Grant additional users (and myself) permissions in the Users and Groups dialog
4) Change system permissions via the Authorizations GUI to allow users to mount drives
5) Modify fstab to automount NTFS partitions
6) Change annoyingly large system font (in 1024x768 at any rate) to be smaller.
7) Change default settings in nautilus to use list view, smaller icons, smaller zoom value, and get rid 
of the huge space-hogging navigation bar
8 ) Install nautilus-gksu and nautilus-terminal (or whatever it's called) so that I can right click and open stuff as administrator or right click and open a terminal
9) Change annoying white background color scheme in terminal window to black or dark gray
10) Change .bashrc to actually include the current directory on the path
11) Reinstall development library packages by looking through my old apt-get export file and manually picking them out in synaptic
12) Install compiz settings manager
13) Change all the annoying default compiz settings (i.e. wavy windows, window snapping)
14) Change the login screen to use the face browser
15) Resize login face icons to something consistant, i.e. 50x50
16) Create a 'My Documents' soft link on my desktop so that I can access the 'My Documents' folder easily on my NTFS partition
17) Change the GRUB boot menu order so that Windows is first instead of Ubuntu (for my wife's sake of course :) )

I like Ubuntu, and I think it's definitely worth the trouble to get it up and running, but some of these just seem like no-brainers to me from a usability standpoint, i.e. 2, 4, 5, 8, 16, 17.   Just my opinion though! (please don't flame me :) )...

Lastly, it's really really annoying in the installer to have to wait 2-3 minutes to switch between the manual and automatic partitioner screens.  It's also really annoying that my video card only works in 'video safe mode' in the installer.  Why doesn't the installer just use like a standard VESA VGA mode by default?

EDIT: maybe this post should go in 'Ubuntu Testimonials & Experiences' instead?  I'd move it, but... unfortunately I don't see how. :confused:

---

### Post by Soul-Sing on 2009-06-21
> 1) Activate root login capability

why?

---

### Post by aysiu on 2009-06-21
> **Jeema said:**
> 
1) Activate root login capability There's absolutely no reason to do this.
> 2) Create additional users (don't remember it asking during the install at any rate) This is a given on any operating system.
> 3) Grant additional users (and myself) permissions in the Users and Groups dialog Same deal here. A given.
> 4) Change system permissions via the Authorizations GUI to allow users to mount drives
5) Modify fstab to automount NTFS partitions Shouldn't be necessary. I never had to do this. My drives all mount automatically. External should mount automatically. Internal should mount when you click on it in Nautilus (and it should automatically prompt you for a password to authenticate the mount process). If that isn't happening, you should file a bug report on it. > 6) Change annoyingly large system font (in 1024x768 at any rate) to be smaller. Well, if you consider it large, that may be a personal preference issue. I have a 1024x576 screen resolution, and the default font sizes seem fine for me. > 7) Change default settings in nautilus to use list view, smaller icons, smaller zoom value, and get rid  of the huge space-hogging navigation bar Again, this is a personal preference. > 8 ) Install nautilus-gksu and nautilus-terminal (or whatever it's called) so that I can right click and open stuff as administrator or right click and open a terminal That's nice to have for power users, but in everyday use, you shouldn't need to edit system files on a regular basis. > 9) Change annoying white background color scheme in terminal window to black or dark gray I use a transparent black, but again that's personal preference. > 10) Change .bashrc to actually include the current directory on the path Not sure what that's for. > 11) Reinstall development library packages by looking through my old apt-get export file and manually picking them out in synaptic Not sure what that's for either. > 12) Install compiz settings manager I like the default settings and find the Compiz settings manager confusing, but if you want to tweak it, I guess that's what you have to install. > 13) Change all the annoying default compiz settings (i.e. wavy windows, window snapping) I hate wavy windows, but I guess you don't. > 14) Change the login screen to use the face browser What's the face browser? > 15) Resize login face icons to something consistant, i.e. 50x50 Okay. > 16) Create a 'My Documents' soft link on my desktop so that I can access the 'My Documents' folder easily on my NTFS partition Not all of us have My Documents folders or NTFS partitions. Guess that setup works for you. > 17) Change the GRUB boot menu order so that Windows is first instead of Ubuntu (for my wife's sake of course :) ) Not everyone wants Windows as the default, but you do have the freedom to change the order. Since Windows doesn't even acknowledge Ubuntu, I think it's perfectly fine for Ubuntu to default to being the boot-up in a dual-boot, especially since you can easily change the default order with StartUp Manager.

> I like Ubuntu, and I think it's definitely worth the trouble to get it up and running, but some of these just seem like no-brainers to me from a usability standpoint, i.e. 2, 4, 5, 8, 16, 17.   Just my opinion though! (please don't flame me :) )... Actually, none of those are no-brainers from a usability standpoint. Yes, it is just your opinion and personal preferences.

> It's also really annoying that my video card only works in 'video safe mode' in the installer.  Why doesn't the installer just use like a standard VESA VGA mode by default? Perhaps you should file a bug report on it.

> EDIT: maybe this post should go in 'Ubuntu Testimonials & Experiences' instead?  I'd move it, but... unfortunately I don't see how. :confused: I've moved it.

If you really are doing all these customizations every time you install Ubuntu, you should consider making your own Ubuntu remix. It's quite simple and will save you a lot of trouble down the line (you'll still have to add additional users after installation, but most of the rest of the stuff can be taken care of in advance).

[Remastersys](http://www.geekconnection.org/remastersys/ubuntu.html) is an easy-to-use tool that allows you to make a live/installer CD out of your current Ubuntu installation.

Here are the basic steps:

1. Customize Ubuntu exactly the way you want (but with only one user, for now)

2. Copy the user configuration settings (all the hidden files) from /home/*username* to /etc/skel and make sure root owns those copied folders and files.

3. Install Remastersys

4. Run Remastersys

5. Keep the .iso somewhere handy or burn it to CD

---

### Post by jocko on 2009-06-21
> **Jeema said:**
> I recently reinstalled Ubuntu on a new hard drive I bought.  This is the second time I've installed it, the first being 8.04 a while back.

Afterwards, I realized that it seemed like it was taking a really long time to get the system how I liked it, so I put together a list of all the annoying things I had to do after install.  And here it is!:

1) Activate root login capability
2) Create additional users (don't remember it asking during the install at any rate)
3) Grant additional users (and myself) permissions in the Users and Groups dialog
4) Change system permissions via the Authorizations GUI to allow users to mount drives
5) Modify fstab to automount NTFS partitions
6) Change annoyingly large system font (in 1024x768 at any rate) to be smaller.
7) Change default settings in nautilus to use list view, smaller icons, smaller zoom value, and get rid 
of the huge space-hogging navigation bar
8 ) Install nautilus-gksu and nautilus-terminal (or whatever it's called) so that I can right click and open stuff as administrator or right click and open a terminal
9) Change annoying white background color scheme in terminal window to black or dark gray
10) Change .bashrc to actually include the current directory on the path
11) Reinstall development library packages by looking through my old apt-get export file and manually picking them out in synaptic
12) Install compiz settings manager
13) Change all the annoying default compiz settings (i.e. wavy windows, window snapping)
14) Change the login screen to use the face browser
15) Resize login face icons to something consistant, i.e. 50x50
16) Create a 'My Documents' soft link on my desktop so that I can access the 'My Documents' folder easily on my NTFS partition
17) Change the GRUB boot menu order so that Windows is first instead of Ubuntu (for my wife's sake of course :) )

I like Ubuntu, and I think it's definitely worth the trouble to get it up and running, but some of these just seem like no-brainers to me from a usability standpoint, i.e. 2, 4, 5, 8, 16, 17.   Just my opinion though! (please don't flame me :) )...

Lastly, it's really really annoying in the installer to have to wait 2-3 minutes to switch between the manual and automatic partitioner screens.  It's also really annoying that my video card only works in 'video safe mode' in the installer.  Why doesn't the installer just use like a standard VESA VGA mode by default?

EDIT: maybe this post should go in 'Ubuntu Testimonials & Experiences' instead?  I'd move it, but... unfortunately I don't see how. :confused:
1. That's your choice. But since you are complaining about everything you have to do every time you reinstall, why not skip this step the next time, and maybe you won't break your system as easily and won't have to reinstall so often...
2, 3, 8, 11, 12. So?
4 & 5. During the partitioning part of the install, you get to choose where everything will get mounted, even ntfs drives. Just set up mount points for all drives you want to be accessible, and they will be automatically added to fstab.
6, 7, 9, 10, 13 & 16. Make a separate /home partition to keep your user accounts settings between install. You still have to create the user accounts, but once they are created, they will automatically use their old home directory with all settings intact.

---

### Post by HappyFeet on 2009-06-21
It's still easier than setting up a windows machine. ;)

BTW, that's the price you pay for wanting an ultra customized computer. All I do is change the theme, add a few apps and codecs, and I'm done.

---

### Post by aufan19 on 2009-06-21
Why do you need root login?

---

### Post by ngsupb on 2009-06-21
I am afraid to reinstall, because I will have to do such things too :D

---

### Post by aysiu on 2009-06-21
> **ngsupb said:**
> I am afraid to reinstall, because I will have to do such things too :D
So don't.

As I said before, you can use Remastersys to make a remixed Ubuntu live/installer CD that has all your customizations (except GDM and extra users).

---

### Post by ad_267 on 2009-06-21
Why add the current directory to your path? It's not in there for a reason. It's also not very hard to remember to use ./filename to execute a file in the current directory.

---

### Post by ngsupb on 2009-06-22
> **aysiu said:**
> So don't.

As I said before, you can use Remastersys to make a remixed Ubuntu live/installer CD that has all your customizations (except GDM and extra users).

In case I do re-installation every week, I would use Remastersys, but in my case I am planning to reinstall it when 9.10 comes and I want to upgrade my hdd to ssd. It shouldn't be hard to spend addition day or two for configuration everything like I like, it is ok for me. I don't complain, but the post of Jeema makes sense.

Anyway thanks for the Remastersys, didn't know about it.

---

### Post by caravel on 2009-06-22
With the all the changes you're having to do, you'd be better off with Debian.  The root login is enabled by default in Debian so there's none of this sudo nonsense.  Canonical have a weird policy about sudo/su which comes up in this forum, time and time again.  Users here seem to blindly repeat it with an almost fanatical regularity.

All I can say to the "sudoers" here is that Ubuntu cannot simply be *right* and the rest of the UNIX/Linux world *wrong*.  Sudo has it's uses - it's desgnied to give normal users administrative rights for *certain specific tasks*.  It should not be used as a replacement for su as it is in Ubuntu.

---

### Post by lisati on 2009-06-22
1) - the preferred way of elevating your root privileges in Ubuntu is with "sudo": see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ad_267 on 2009-06-22
> **lisati said:**
> 1) - the preferred way of elevating your root privileges in Ubuntu is with "sudo": see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Yup, and if you want to get a root session use "sudo -i"

---

### Post by armandh on 2009-06-22
I'm lucky my wife prefers ubuntu
and the only thing I "need to do" 
is visit adobe for flash and [www.medibuntu.org](www.medibuntu.org) for the rest.

what I want is extra

---

### Post by JiggyMan on 2009-06-22
> **aysiu said:**
> [Remastersys]("http://www.geekconnection.org/remastersys/ubuntu.html") is an easy-to-use tool that allows you to make a live/installer CD out of your current Ubuntu installation.
Thank you for that gem! I don't do a LOT of customizing after install but it's still nice to have this option. Also, I can use it on my mom's computer in case she ever needs to reinstall and I'm not around. Thanks!

---

### Post by caue.rego on 2009-06-22
Thanks for the **Remastersys**, everyone! I was looking for something like that for some time. Now I just have to port it to my pendrive. :)

---

### Post by aysiu on 2009-06-22
> **ngsupb said:**
> In case I do re-installation every week, I would use Remastersys, but in my case I am planning to reinstall it when 9.10 comes and I want to upgrade my hdd to ssd. It shouldn't be hard to spend addition day or two for configuration everything like I like, it is ok for me. I don't complain, but the post of Jeema makes sense.

Anyway thanks for the Remastersys, didn't know about it.
If you like doing fresh reinstalls at new releases instead of just upgrading, you can also look into having a separate /home partition so that little settings changes like the terminal background color don't need to be redone every time.

---

### Post by starcannon on 2009-06-24
> **Jeema said:**
> I recently reinstalled Ubuntu on a new hard drive I bought.  This is the second time I've installed it, the first being 8.04 a while back.

Afterwards, I realized that it seemed like it was taking a really long time to get the system how I liked it, so I put together a list of all the annoying things I had to do after install.  And here it is!:

Its always cool seeing how others set up their gear. Lets take a look-see...
> 
1) Activate root login capability

Its your security, I do not see any advantage here, only disadvantage (I have not read the thread yet, I will though, this is just my response to the initial post)
> 
2) Create additional users (don't remember it asking during the install at any rate)

Yep gotta get everyones accounts up and running. Now or later, either way no biggy.
> 
3) Grant additional users (and myself) permissions in the Users and Groups dialog

I stick with default permissions, I find that works for me 100% of the time. I set up an account to do administration, then set everyone else, my everyday account as well, as a "Desktop User" this just keeps Admin stuff very safe and sane for me.
> 
4) Change system permissions via the Authorizations GUI to allow users to mount drives
 
I haven't had issues with USB Keys or other external media, though I have read about those who have. 
> 
5) Modify fstab to automount NTFS partitions

I add those partitions during install, but I use the manual partition editor and it lets me do that; I also use it so that I can have a separate /home. 
> 
6) Change annoyingly large system font (in 1024x768 at any rate) to be smaller.

Yeah, gotta get the gui all tuned up for personal tastes, I go straight to Appearance and turn on Subpixel Smoothing myself.
> 
7) Change default settings in nautilus to use list view, smaller icons, smaller zoom value, and get rid 
of the huge space-hogging navigation bar

Aye more customizing the gui, love that we can do that.
> 
8 ) Install nautilus-gksu and nautilus-terminal (or whatever it's called) so that I can right click and open stuff as administrator or right click and open a terminal

I just Alt+F2 gksu nautilus on those rare occasions.
> 
9) Change annoying white background color scheme in terminal window to black or dark gray

Me to, black back w/green text.
> 
10) Change .bashrc to actually include the current directory on the path

I never bothered, I just use nautilus-open-terminal and can right click in any folder and open a terminal here, or I use cd if I'm to lazy to open nautilus lol.
> 
11) Reinstall development library packages by looking through my old apt-get export file and manually picking them out in synaptic

I just grab them as needed. What can I say, why do today what you can do tomorrow.
> 
12) Install compiz settings manager

I used to, but I find I keep making my gui simpler and simpler. Just the features I need, eyecandy costs too much and compiz always feels a bit less than stable when I start tweaking the bejezus out of it.
> 
13) Change all the annoying default compiz settings (i.e. wavy windows, window snapping)

I turn off the constrain_y element using gconf-editor, other than that I don't fuss with compiz too much.
> 
14) Change the login screen to use the face browser

Yeah I like that as well.
> 
15) Resize login face icons to something consistant, i.e. 50x50

I'm to lazy lol
> 
16) Create a 'My Documents' soft link on my desktop so that I can access the 'My Documents' folder easily on my NTFS partition

I just bookmark it in my Places tab.
> 
17) Change the GRUB boot menu order so that Windows is first instead of Ubuntu (for my wife's sake of course :) )

My wife hates Windows, so I don't have to bother.
> 
I like Ubuntu, and I think it's definitely worth the trouble to get it up and running, but some of these just seem like no-brainers to me from a usability standpoint, i.e. 2, 4, 5, 8, 16, 17.   Just my opinion though! (please don't flame me :) )...

No flames intended on mypart; I don't agree with creating a root account, but hey, its your machine, make it work for you; as long as you know and understand what your doing, then your not doing it wrong.
> 
Lastly, it's really really annoying in the installer to have to wait 2-3 minutes to switch between the manual and automatic partitioner screens.  It's also really annoying that my video card only works in 'video safe mode' in the installer.  Why doesn't the installer just use like a standard VESA VGA mode by default?

I never have to wait more than a few seconds when switching to manual partition mode. I don't expect the generic vid drivers to look good, just work good enough to make ubiquity go; I set up my gpu after updates and second boot have taken place.
> 
EDIT: maybe this post should go in 'Ubuntu Testimonials & Experiences' instead?  I'd move it, but... unfortunately I don't see how. :confused:
Its where I found you.

I'll add that I also add the OpenOffice3 ppa, Medibuntu, and a few other of my favorite software latest greatest ppa repo's to my 3rd party software; that way I'm always up to date, and I don't have to do anything but let the update manager handle it for me.

GLAHF
theres no place like ~/

---

### Post by raymondvillain on 2009-06-25
My changes are not so grand, but it is annoying to have to track everything down for re-installing.

A lot of my commands after initial boot up are from a terminal window.  Is there a way to have all of your terminal window sessions logged to a file?  I think I remember being shown how to do that once but now I've forgotten how.

Then I could just go back to that file and copy (or run it there) exactly what I went through before.

---

### Post by aysiu on 2009-06-25
All the terminal commands are logged to /home/*username*/.bash_history

You can easily copy that file and change it to a script you run.

---

### Post by HappyFeet on 2009-06-26
If you just go to your home folder and do ctrl-h, you will see your hidden configuration files. Just copy and paste the ones you use most onto another drive of some sort. Then after a reinstall, just plug them back in.

---

### Post by aysiu on 2009-06-26
> **HappyFeet said:**
> If you just go to your home folder and do ctrl-h, you will see your hidden configuration files. Just copy and paste the ones you use most onto another drive of some sort. Then after a reinstall, just plug them back in.
Or... use a separate /home partition.

---

### Post by HappyFeet on 2009-06-26
> **aysiu said:**
> Or... use a separate /home partition.

Same thing. I've never needed to have an official home folder. I backup mozilla and thunderbird at least once a week. That's all I need. All of my main files are kept on 2 different drives. Yes, redundancy. I also have it backed up to a DVD Dual layer. And on another flash drive. I take NO chances.

---

### Post by HappyFeet on 2009-06-26
> **aysiu said:**
> Or... use a separate /home partition.

The truly free and wild can't be burdened by such limitations. :D

Where is home anyway?

Peace.

---

### Post by ceciliaFX on 2009-06-27
> **HappyFeet said:**
> The truly free and wild can't be burdened by such limitations. :D

Where is home anyway?

Peace.
home is whatever your name is logged in

mine is - strangely enough - "cecilia"

---

