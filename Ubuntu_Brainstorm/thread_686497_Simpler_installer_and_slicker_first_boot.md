---
title: "Simpler installer and slicker first boot"
date: 2008-02-03
forum: Ubuntu Brainstorm
---

### Post by jrothwell97 on 2008-02-03
The Ubuntu boot sequence is pretty good: GRUB only appears for a few seconds, usplash is very pretty and getting to the login screen takes less than a minute (sometimes less than half a minute).

However, I can't help but think that installation, followed by the first boot, would be somewhat confusing for new users. Are they likely to know what the master boot record is? Or what a GUID partition table is?

I think there should be a 'simple' installation method. This asks if you want to keep your other operating system (if it detects the presence of one, such as Windows) and then takes care of everything else automatically. You're offered the opportunity to switch between the two at all times.

Also, IMO, the first boot is a bit iffy: sometimes packages have to be configured, which might seem a bit scary to Joe Public. I'd like to suggest a sort of 'almost there...' boilerplate that appears to tell you that the packages are being configured and that Ubuntu will start shortly. (An idea might be a 'show details' button which shows the terminal output when it configures the packages'.

Also, I'm a bit concerned about users being created during installation: most OSes out there create the user on the first boot, and users might forget their passwords during the installation. It might be more practical to do this on first boot.

Finally, what about an introduction movie, *á la* Mac OS X? It might sound a bit gimmicky, but it would create a good impression on the user, and probably look nice too.

I've rabbeted on for quite a bit, and for that I am sorry. However, here's a sequence of what I think the installer/firstboot experience should be like, for an average user who has just downloaded and burned Ubuntu to a CD.

[LIST=1]
[*]Puts in Live CD and boots from it. A dialogue box greets him, giving him the option to install Ubuntu immediately. It reminds him that he can always do it later on.
[*]Our user clicks 'install Ubuntu immediately', at which point the installer starts and offers him the 'simple' or 'advanced' installer. He clicks the 'simple' button.
[*]Does our user want to keep Windows? Yes. He clicks the button.
[*]Does our user want Windows or Ubuntu to start automatically? He wants to start Ubuntu automatically, so he selects that and clicks Go.
[*]The installer shrinks his Windows partition by a set margin of, say, 20% of the disk size. It then partitions / and the swap in that, and mounts them.
[*]Ubuntu is installed as usual. Joe User is allowed to play around on the Live CD for a while.
[*]The installer finishes, and Joe is asked to save his work and hit the big 'RESTART' button. The CD ejects and the computer reboots.
[*]The computer spends around two minutes configuring the packages. On the screen, our user sees a caption reading 'One moment please... Ubuntu will start in just a few minutes' or something along those lines. Music is played in the background while this happens.
[*]The 'hang on' plate fades out, and the user watches the intro movie. (Possible idea: flying through a busy city at dusk, with billboards and shop signs saying 'welcome' in different languages.) The user sees a caption reading 'Welcome to Ubuntu', before being presented with the getting started wizard.
[*]The user sets up his username, password, real name, Email address, WLAN key, and several other details. He is asked if he wants to use this data to fill out the Ubuntu Forums registration form. He accepts.
[*]The user can, if he wants, set up other people's accounts here. If he does so, the user names are automatically chosen, and passwords are automatically generated. He can also choose whether to have a face browser at the login prompt.
[*]The user is offered the opportunity to download MPEG2 (DVD) and MP3 immediately. He can do it later if he wants, but then it is more complicated. He accepts. The download starts automatically, and a notification will pop up when it completes.
[*]The user chooses a colour scheme, and presses the 'go' button. The codecs he downloaded are installed, and the package mess is cleaned up (the machine plays some more music and displays another boilerplate while this is happening) and then the login prompt appears. (If he only set up one user, then the desktop appears immediately.)
[/LIST]

The idea behind this is to make the installation process as unbewildering as possible to the end user, and to make it a little prettier. I can't see this being a quick project, but I would imagine the results would be worth it.

Your thoughts, please.

---

### Post by smartboyathome on 2008-02-03
I do not agree with step 5. What if the Windows partition has used up more than 80% of the disk? Also, what about if the user doesn't have a big hard drive, and wants to give more space to Ubuntu than 20%? Also, step 8 reminds me of being on hold with a phone company. I like how packages are configured during the installation process, as you can mess around with the livecd while you wait. The intro movie would be annoying (as stated in another thread on a welcome wizard) for those who already used it, and most users would just skip it anyway. I don't like the idea of doing the username/password after the install, as no settings can be imported from another Ubuntu install or Windows (a good feature imo). Automatically generating another person's username is not a good idea, as this makes it more susceptable to forgetting it. Why would the user want to download an mpeg movie and mp3? That step isn't very clear. Also, this pretty much eliminates the "live" part of the livecd, as it does pretty much all configuration post install.

---

### Post by DizzyTech on 2008-02-03
I believe an even-simpler installer combined with user creation on first boot would be very beneficial.  As I've said before, a first boot wizard could not only include and introduction and first user creation, but it could also include very simple hardware configuration (e.g., test sound, network connection, enabling Compiz) and easy package adding (would you like to install a note-taking software?  photo-organizing software, etc?).

---

### Post by smartboyathome on 2008-02-03
> **DizzyTech said:**
> I believe an even-simpler installer combined with user creation on first boot would be very beneficial.  As I've said before, a first boot wizard could not only include and introduction and first user creation, but it could also include very simple hardware configuration (e.g., test sound, network connection, enabling Compiz) and easy package adding (would you like to install a note-taking software?  photo-organizing software, etc?).

Ubuntu won't be doing package addition any time soon, as they give you a stable system and then let you add packages easily afterwards.

---

### Post by jrothwell97 on 2008-02-04
> **smartboyathome said:**
> I do not agree with step 5. What if the Windows partition has used up more than 80% of the disk? Also, what about if the user doesn't have a big hard drive, and wants to give more space to Ubuntu than 20%? Also, step 8 reminds me of being on hold with a phone company. I like how packages are configured during the installation process, as you can mess around with the livecd while you wait. The intro movie would be annoying (as stated in another thread on a welcome wizard) for those who already used it, and most users would just skip it anyway. I don't like the idea of doing the username/password after the install, as no settings can be imported from another Ubuntu install or Windows (a good feature imo). Automatically generating another person's username is not a good idea, as this makes it more susceptable to forgetting it. Why would the user want to download an mpeg movie and mp3? That step isn't very clear. Also, this pretty much eliminates the "live" part of the livecd, as it does pretty much all configuration post install.

I should have made it clearer that I meant 'downloading the MPEG2 and MP3 *codec packages*.' 

Step 8... yes, maybe without the music, but it's mainly to make it a bit less scary to someone who doesn't understand raw apt or shell TUI output.

I don't see what would be so annoying about an intro movie. The idea is to create a good impression on the user, to make him think 'wow, this is way better than any of the cr*p I get with Vista'. If you wanted to be really fancy and if the user had a powerful enough graphics card, the movie could be rendered on-the-fly. As it might be annoying to more experienced users, it might only activate if the 'simple' installation mode is selected. And either way, there'd probably be a 'skip' button in the corner.

Obviously contingency plans would be put in place for automatic partitioning. Perhaps an additional step might be to ask 'how much space do you want to take from Windows and give to Ubuntu?' with plain-English explanations of what these gigabyte things are, and how Ubuntu doesn't do NTFS and you might need to install extra software to get Windows to do ext3. If there's simply not enough space, the installer could simply say 'sorry' and explain there isn't enough hard disk space.

Generating the username would be something along the lines of 'jsmith', 'pbrown', etc. The password would be set to something memorable (12345, notapassword, changemeplease), or even as a blank, but the user would be asked to change it at first logon.

While I respect your points, my point is that the installer could be a little more aesthetically pleasing and less bewildering to the novice.

@DizzyTech: I like the idea a lot. As you'd be allowed to add stuff *after booting into your new stable system*, I don't see the problem with it.

---

### Post by DizzyTech on 2008-02-04
smartboyathome:  You make a good point.  Maybe an explanation of how to get the package manager (by which I mean gnome-app-install) could be introduced.  What I simply want is slimming down the install process and making it easier for everybody; an accessory to that is probably a first boot wizard.

I do still stand by the idea that hardware configuration needs to be presented to the users (graphics card warnings, a not-so-scary prompt for the Restricted Manager, etc.) Another possibility would be an online-enabled database of hardware for both post-release and in-between releases (i.e., you have an Intel ICH8 sound card; would you like to install the packages to make it work?).

---

### Post by Trail on 2008-02-05
Hmm, an average Joe Windows user might not be able to handle installing an OS, but I believe that an average Joe Linux user should.

I myself would rather that effort was spent on things other than easing the mitigation of Windows users (because that's the point, isn't it?). The installer is simple as it is. Besides, how often do you actually install GNU/Linux?

---

