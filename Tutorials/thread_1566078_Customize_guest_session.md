---
title: "Customize guest session"
date: 2010-09-01
forum: Tutorials
---

### Post by Gunnar Hjalmarsson on 2010-09-01
***[SIZE=5]Note: This tutorial is deprecated and replaced by [CustomizeGuestSession]("https://help.ubuntu.com/community/CustomizeGuestSession").[/SIZE]***
[HR][/HR]
[COLOR=Red]**[SIZE=4]Important note[/SIZE]**[/COLOR]
[SIZE=2][COLOR=Red]**+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+**[/COLOR]
Up to Ubuntu 11.04 the guest session feature was provided by [gdm-guest-session]("http://packages.ubuntu.com/natty/gdm-guest-session"), an extension to the [GNOME Display Manager (GDM)]("http://packages.ubuntu.com/natty/gdm") which was the default display manager in Ubuntu. This changed in Ubuntu 11.10, where [LightDM]("http://packages.ubuntu.com/oneiric/lightdm") is the default display manager, and you can now launch a guest session through a built-in LightDM feature. Unlike before you don't need to first log in as a regular user; a guest session in Ubuntu 11.10 can optionally be launched directly from the login screen.

This tutorial was written with gdm-guest-session in mind. However, I have put together a new tarball file, so now there are two tarballs attached to this tutorial:

[LIST=1]
[*]**[FONT=Courier New][SIZE=3]guest-session-prefs-0.13.tar.gz[/SIZE][/FONT]** - for Ubuntu < 11.10 with GDM 
[*]**[FONT=Courier New][SIZE=3]guest-session-prefs-lightdm-0.12.tar.gz[/SIZE][/FONT]** - for Ubuntu >= 11.10 with LightDM 
[/LIST]
Even if the comments below refer to the first tarball, most of them apply to the new tarball as well. The names of some files and directories have been altered, but hopefully the [FONT=Courier New][SIZE=3]README[/SIZE][/FONT] file in [FONT=Courier New][SIZE=3]guest-session-prefs-lightdm-0.12.tar.gz[/SIZE][/FONT] contains sufficient guidance in that respect.
[COLOR=Red]**+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+**[/COLOR][/SIZE]

**[SIZE=4]Overview[/SIZE]**

Many Ubuntu users, me included, have posted ideas on minor changes to the [gdm-guest-session]("http://packages.ubuntu.com/natty/gdm-guest-session") behavior, and I'm happy to share the guest session related changes I have made. They include:

[LIST]
[*] Firefox preference setting 
[*] disabling login-sound 
[*] language selection [COLOR=Red][not in LightDM][/COLOR] 
[*] gettexted strings 
[*] folder for storing files permanently 
[*] info dialog at startup 
[*] icon on the desktop 
[/LIST]
Whether you want to make a couple or all of those changes, or there are other changes that you would like to see, I hope that the methods used for altering the guest session behavior may serve as useful examples.

The figure below shows the most important files, and gives you a schematic picture of the program flow. In the left column you find the core files in the gdm-guest-session package (green borders) together with a tiny file that I created, merely to have all the executables located in the same folder. The files in the right column are in effect configuration files, even if they contain shell commands. Computer owners and system admins may edit the files in [FONT=Courier New][SIZE=2][COLOR=black]/etc/guest-session[/COLOR][/SIZE][/FONT] to their liking, without worrying about the changes being overwritten when gdm-guest-session or other packages are updated.

[IMG]http://gunnar.cc/img/guest-session-model.jpg[/IMG]

Some of the commands in my code snippets need to be executed before the start of the launch process, while others are better executed in the middle or at the end of the process. I grouped my snippets accordingly, so that's why there are three files in the right column.

**[SIZE=4]Tarball: guest-session-prefs[/SIZE]**

There is a tarball file attached to this tutorial with both a README file and an install script, almost like a package. But since admins are *expected* to change and add things, guest-session-prefs is very different compared to an Ubuntu package. In the README file I call it a "convenience kit", a framework for configuring guest sessions.

I recommend that you download the tarball and run the install script. Rather than describing every detail, the comments below serve as a user guide focusing on a few edit possibilities.

**[SIZE=4]Install / uninstall[/SIZE]**

Okay, here we go.[INDENT] Download [guest-session-prefs-0.13.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=174571&d=1288902423")
 Open a terminal window and go to the directory with the downloaded file
[COLOR=DarkRed]**[FONT=Courier New][SIZE=2]tar -xf guest-session-prefs-0.13.tar.gz[/SIZE][/FONT]**[/COLOR]
[COLOR=DarkRed]**[FONT=Courier New][SIZE=2] cd guest-session-prefs-0.13[/SIZE][/FONT]**[/COLOR]
[COLOR=DarkRed]**[FONT=Courier New][SIZE=2] sudo ./install.sh[/SIZE][/FONT]**[/COLOR]
[/INDENT]
Now you have exactly the same setup as I have (or at least had when I wrote this...). These are the installed files:

[FONT=Courier New][SIZE=2]/etc/guest-session/auto.sh
/etc/guest-session/prefs.sh
/etc/guest-session/prepare.sh
/etc/guest-session/sv/LC_MESSAGES/guest-session-prefs.mo
/usr/share/doc/gdm-guest-session/guest-session-prefs/README
/usr/share/doc/gdm-guest-session/guest-session-prefs/sample-translation.po
/usr/share/doc/gdm-guest-session/guest-session-prefs/uninstall.sh
/usr/share/gdm/guest-session/guest-session-auto.sh[/SIZE][/FONT]

You launch a guest session by calling[INDENT][COLOR=DarkRed]**[FONT=Courier New][SIZE=2]/usr/share/gdm/guest-session/guest-session-launch[/SIZE][/FONT]**[/COLOR]
[/INDENT]
or, as from Ubuntu 11.04, just[INDENT][COLOR=DarkRed]**[FONT=Courier New][SIZE=2]guest-session[/SIZE][/FONT]**[/COLOR]
[/INDENT]
If you, like me, display a list dialog with choices when a guest session is launched, you'll notice an odd behavior if you use the guest session menu item provided by the [indicator-session]("http://packages.ubuntu.com/maverick/gnome/indicator-session") package. The reason is that indicator-session locks the screen before calling [FONT=Courier New][SIZE=2]guest-session-launch[/SIZE][/FONT]. Creating your own launcher, e.g. via **System -> Preferences -> Main Menu**, solves that possible problem.

To uninstall guest-session-prefs you do:[INDENT][COLOR=DarkRed]**[FONT=Courier New][SIZE=2]cd /usr/share/doc/gdm-guest-session/guest-session-prefs[/SIZE][/FONT]**[/COLOR]
[COLOR=DarkRed]**[FONT=Courier New][SIZE=2] sudo ./uninstall.sh[/SIZE][/FONT]**[/COLOR]
[/INDENT]
**[SIZE=4]Comments[/SIZE]**

**[SIZE=2]Firefox[/SIZE]**

Maybe Firefox is the most used application by guests, and many admins want to be able to set some preferences. [FONT=Courier New][SIZE=2]/etc/guest-session/prefs.sh[/SIZE][/FONT] contains a code snippet that creates a Firefox profile, and given the commands in that snippet, one line of code in [FONT=Courier New][SIZE=2]prefs.sh[/SIZE][/FONT] is enough to change some aspect of Firefox.

```
echo 'user_pref("signon.rememberSignons", false);' >> $profiledir/user.js
```That code tells Firefox to not prompt about remembering passwords. At the page [Customizing Mozilla]("http://www.mozilla.org/unix/customizing.html") you find some other customizing hints.


**[SIZE=2]Disabling certain applications[/SIZE]**

[FONT=Courier New][SIZE=2]guest-session-setup.sh[/SIZE][/FONT] disables a few services that are unnecessary for guest sessions. Applying the same approach, [FONT=Courier New][SIZE=2]prefs.sh[/SIZE][/FONT] defines the function **disable_app()**. This is how I disable the login sound:

```
disable_app libcanberra-login-sound.desktop /usr/share/gnome/autostart
```[FONT=Courier New][SIZE=2]libcanberra-login-sound.desktop[/SIZE][/FONT] is the file that autostarts the login sound by default, and [FONT=Courier New][SIZE=2]/usr/share/gnome/autostart[/SIZE][/FONT] is the folder where that file resides.


**[SIZE=2]Language selection[/SIZE]** [COLOR=Red][not applicable to LightDM][/COLOR]

If you launch a guest session right after having installed guest-session-prefs, you are prompted to choose between English and Swedish.

[IMG]http://gunnar.cc/img/lang-select-screenshot.png[/IMG]

If you try the Swedish option, but still only see English on the screen, it's hopefully not a bug. A more likely explanation is that Swedish has not been installed on your system. You can set available languages via **System -> Administration -> Language Support**.

For those of you who want to be able to select language, the language related code ought to be useful. If one language (e.g. French) is enough, but the launching regular session might be run in some other language, the code in [FONT=Courier New][SIZE=2]/etc/guest-session/prepare.sh[/SIZE][/FONT] can be exchanged for:

```
echo "fr_FR" > /tmp/guest-session-lang
```Finally, if you have no interest in using more than one language, you can simply delete [FONT=Courier New][SIZE=2]prepare.sh[/SIZE][/FONT]. OTOH, commenting out the code or renaming the file are probably better options. For instance, there may be other preferences that you want to set on-the-fly when launching a session. 


**[SIZE=2]Gettexted strings[/SIZE]**

To the extent you make use of text strings that are displayed to the guest user, which for instance is the case with the info dialog box shown below, you may want the strings to be translated to the current language. guest-session-prefs shows how that can be done using GNU gettext. If you have not used the gettext tools before, I believe that my example may help you get started. Of course, reading parts of the [gettext manual]("http://www.gnu.org/software/gettext/manual/gettext.html") is advisable in any case.

If you are only dealing with one non-English language, and don't care about English, it's probably easiest to drop gettext and just hard code the strings in the language of choice.


**[SIZE=2]Folder for storing files permanently[/SIZE]**

I allow my guest users to store files permanently, and the install script creates the folder [FONT=Courier New][SIZE=2]/var/guest-data[/SIZE][/FONT] for the purpose and assigns the permissions 0777. If you are of another view, just remove that folder.


**[SIZE=2]Info dialog at startup[/SIZE]**

[FONT=Courier New][SIZE=2]/etc/guest-session/auto.sh[/SIZE][/FONT] contains code for displaying an info dialog box. While calling the guest users' attention to the temporary nature of a guest session, it informs about the dedicated folder [FONT=Courier New][SIZE=2]/var/guest-data[/SIZE][/FONT] for persistent file storage.

[IMG]http://gunnar.cc/img/guest-session-warning.png[/IMG]


[SIZE=2]**Icon on the desktop**[/SIZE]

[FONT=Courier New][SIZE=2]auto.sh[/SIZE][/FONT] also creates a shortcut icon to [FONT=Courier New][SIZE=2]/var/guest-data[/SIZE][/FONT]. You may want to add a few similar code snippets to [FONT=Courier New][SIZE=2]auto.sh[/SIZE][/FONT] that for instance place application shortcuts on the desktop.

**[SIZE=4]Alternative approach[/SIZE]**

In some respects, launching a guest session comes about similarly to creating a new regular user, so by default the files in the folder [FONT=Courier New][SIZE=2]/etc/skel[/SIZE][/FONT] are copied to the guest's home folder. As from Ubuntu 11.04, gdm-guest-session uses the files in [FONT=Courier New][SIZE=2]/etc/guest-session/skel[/SIZE][/FONT] if present. That way some of the above customization measures can be accomplished by editing in [FONT=Courier New][SIZE=2]/etc/guest-session/skel[/SIZE][/FONT] instead of using shell commands.

You enable this feature by copying [FONT=Courier New][SIZE=2]/etc/skel/*[/SIZE][/FONT] to [FONT=Courier New][SIZE=2]/etc/guest-session/skel/*[/SIZE][/FONT]:[INDENT][COLOR=DarkRed][B][FONT=Courier New][SIZE=2]sudo mkdir -p /etc/guest-session
sudo cp -ri /etc/skel /etc/guest-session[/SIZE][/FONT][/B][/COLOR][/INDENT]
In [comment #23]("http://ubuntuforums.org/showthread.php?p=11717490"), Paul has elaborated this approach by providing a step-by-step guide. Thanks, Paul!

**[SIZE=4]Related bug[/SIZE]**

I have submitted the bug [Premature lock when launching guest session]("https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/636693"), whose implementation would support this approach to customizing guest sessions.

---

### Post by tinche on 2010-12-01
That was very interesting and useful, thank you.

---

### Post by Gunnar Hjalmarsson on 2010-12-01
> **tinche said:**
> That was very interesting and useful, thank you.
Thanks, glad to hear you say that. :) You're welcome.
Please feel free to post your comments, other customization ideas, etc.

---

### Post by chmac on 2010-12-13
Thanks for sharing this. It's a nice idea to customise the session a little.

I stumbled upon this thread by searching for a soundless guest session. When I create a guest session any music or other sound that was playing on the system stops (or pauses) and continues once I log out of the guest session. I'd like to be able to play music while a guest session is logged in. Any idea if that's possible by customising your script slightly? I'm not sure why or how sound is related to the guest session, I'm really just guessing.

I have a guest computer connected to speakers and I'd like to play music remotely via cmus on that machine, but also let guests use it for internets. I found that cmus would freeze until the guest session was finished.

---

### Post by Gunnar Hjalmarsson on 2010-12-15
Hello,

> **chmac said:**
> When I create a guest session any music or other sound that was playing on the system stops (or pauses) and continues once I log out of the guest session.
I'm not able to reproduce that behavior. To me, music that was playing in a regular session keeps playing if I launch a guest session.

> **chmac said:**
> I'd like to be able to play music while a guest session is logged in. Any idea if that's possible by customising your script slightly?
No. That is I have no idea.

I noticed that there was an [audio related change]("http://bazaar.launchpad.net/%7Eubuntu-branches/ubuntu/natty/gdm-guest-session/natty/revision/20") not very long ago. If you are using 10.04 or older, you may want to try applying that change to your copy of [FONT=Courier New][SIZE=2]/etc/apparmor.d/gdm-guest-session[/SIZE][/FONT] and reboot.

You can also ask a question at [https://answers.launchpad.net/ubuntu](https://answers.launchpad.net/ubuntu)

> **chmac said:**
> I'm not sure why or how sound is related to the guest session, I'm really just guessing.
Me too, I'm afraid. ;)  Good luck!

---

### Post by chmac on 2010-12-23
Turns out adding myself to the audio group seemed to resolve the problems. I can now play music from a terminal whether or not the guest session is running or not. Happy days. :-)

---

### Post by carrett on 2011-01-27
Hi I have a couple of issues, and I'm wondering if this tarball will solve them?

1. Can I select a default layout? I use US Dvorak and would like guest's default to be US (QWERTY).

2. Is there a way to stop guest from inheriting my startup apps (like Gnome-Do and Docky?).

EDIT: I see these are both doable with the tarball. THANKS!

---

### Post by Gunnar Hjalmarsson on 2011-01-27
Yep, the examples in [FONT=Courier New][SIZE=2]/etc/guest-session/prefs.sh[/SIZE][/FONT] ought to cover what you were looking for. I'm glad that you found the examples useful, carret.

---

### Post by DeFrancoj on 2011-05-12
Very thoughtful post, thank you.

---

### Post by thefinn93 on 2011-05-23
Nice! This will be very helpful. I'm trying to figure out how to allow logging into a Guest session without logging in as anyone else first. ie. GDM would present you with the choice of Guest or Admin, or maybe just automatically log Guest in. Any ideas?

---

### Post by Gunnar Hjalmarsson on 2011-06-26
> **thefinn93 said:**
> I'm trying to figure out how to allow logging into a Guest session without logging in as anyone else first. ie. GDM would present you with the choice of Guest or Admin, or maybe just automatically log Guest in. Any ideas?

That's beyond the scope of [gdm-guest-session]("http://packages.ubuntu.com/natty/gdm-guest-session") and this tutorial. I have seen attempts to modify gdm-guest-session to do what you ask for, but unfortunately I don't remember where...

In any case you can of course create a passwordless user "guest".

---

### Post by chmac on 2011-06-27
The solution might be to create a user that auto-logs in and then add something to the startup scripts that launches a guest session. Not sure if you could set up a user to auto-login while also setting a password on that user. If you could, the guest user would be unable to exit to the parent session. I have a "guest" computer and I like the idea of someone being able to launch a guest session from boot time, without a user password, but as Gunnar said, I think that might be beyond the scope of gdm-guest-session.

---

### Post by Gunnar Hjalmarsson on 2011-11-03
> **Gunnar Hjalmarsson said:**
> 
[QUOTE=thefinn93;10851807]I'm trying to  figure out how to allow logging into a Guest session without logging in  as anyone else first. ie. GDM would present you with the choice of  Guest or Admin, or maybe just automatically log Guest in. Any  ideas?

That's beyond the scope of [gdm-guest-session]("http://packages.ubuntu.com/natty/gdm-guest-session") and this tutorial.[/QUOTE]

Ubuntu 11.10 brought good news in this respect. It's shipped with a new default display manager, LightDM, which allows you to launch a guest session directly from the login screen.

---

### Post by thefinn93 on 2011-11-03
That it did. Maybe I'll look into this again

---

### Post by chmac on 2011-11-03
> **Gunnar Hjalmarsson said:**
> Ubuntu 11.10 brought good news in this respect. It's shipped with a new default display manager, LightDM, which allows you to launch a guest session directly from the login screen.

Awesome, that's the single best reason I've heard to upgrade. Thanks for posting back here, I greatly appreciate it.

---

### Post by zorkerz on 2011-11-05
Having problems installing.
When I run ```
sudo ./install.sh
``` in a terminal it says > ./install.sh: 37: msgfmt: not foundI don't know what that means? Am I doing something wrong?

---

### Post by Gunnar Hjalmarsson on 2011-11-05
Hi zorkerz!

> **zorkerz said:**
> Having problems installing.
When I run ```
sudo ./install.sh
``` in a terminal it says> ./install.sh: 37: msgfmt: not foundI don't know what that means? Am I doing something wrong?

No, not at all. It means that the **msgfmt** program, which is currently needed to run the [FONT=Courier New][SIZE=2]install.sh[/SIZE][/FONT] script, is not installed on your computer.

Please run
```
 sudo apt-get install gettext
```Then you'll hopefully be able to run [FONT=Courier New][SIZE=2]install.sh[/SIZE][/FONT] without further interruptions.

Sorry about that. Think I'd better modify the tarball a bit.

---

### Post by toni93 on 2012-02-13
Hi, how can I customize wine in guest session? Is there a way to copy .wine folder into guest home directory permanently?

---

### Post by Gunnar Hjalmarsson on 2012-02-13
> **toni93 said:**
> Is there a way to copy .wine folder into guest home directory permanently?
Yes, I think there is. I would suggest that you use [FONT=Courier New]/etc/guest-session/skel[/FONT] as described in the section **Alternative approach** in the first post of this thread. If you try it, please let us know if you were successful.

---

### Post by Feppa on 2012-02-14
thanks for a great tutorial!

however i have some issues with some apps.

hope you can help me.

amsn shows an enoying info popup at first run
chrome prompts user to choose search engine at first run
skype shows a license agreement at first run that the user needs accept. 

Any idea on how to solv this?

---

### Post by Feppa on 2012-02-14
i manage to solve this.
 
i logged in with a guest session and launched for example Skype - then switched user to my regular account. In the terminal i used sudo nautilus and then i went into /tmp/guest-xxxxx/ folder. There i found a .Skype folder - i copied it and pasted it in the folder /etc/skel . Worked great!

However i also want to set the guest-session to automatic log out if system is idle for X minutes. How can i do that?

---

### Post by Gunnar Hjalmarsson on 2012-02-15
> **Feppa said:**
> ... There i found a .Skype folder - i copied it and pasted it in the folder /etc/skel . Worked great!
Well, unless you want that setting by default also for newly created *regular* users, you'd better use [FONT=Courier New]/etc/guest-session/skel[/FONT] instead. See the **Alternative approach** section in the tutorial.

> **Feppa said:**
> However i also want to set the guest-session to automatic log out if system is idle for X minutes. How can i do that?
I for one have no idea; I doubt that it can be done using the techniques mentioned in this tutorial.

---

### Post by p-dh on 2012-02-25
I appreciate all of the discussion about customizing the guest session. I have been looking for a way to have a easily cusomizable guest session for a kiosk-type setting under oneiric. After looking through everything, I have found that using a variant of the Alternate Method (above) has made it easy to customize the guest user using all of the regular gui controls (Ubuntu-Tweak, MyUnity, Startup App Prefs, etc.). Before logging out of the session, it is necessary to copy the files from the home directory of the temporary guest account to /etc/guest-session/skel. One advantage of this is that a guest session can be restarted, edited and saved as often as you would like. I realize that I haven't created anything new here; just put together the pieces differently from the posts in this thread.

Anyhow, the steps are as follows:
> 
[LIST=1]
[*]Create the directory /etc/guest-session/skel
[*]While logged on under an admin account, start a guest session
[*]Make any changes to the guest session that you want using whatever tools/utilities you wish
[*]Change back to admin account and open a terminal
[*]cd to /tmp and find the temporary guest home directory (guest-*XXXXX*).
[*]Copy the files in the temporary guest home directory to /etc/guest-session/skel using the command: ‘sudo cp -rT /tmp/guest-*XXXXX* /etc/guest-session/skel’.
[*]Log out of the guest session and login again to check.
[*]To update the settings, repeat steps 2-7 as necessary.
[/LIST]


I previously wrote: *I also have a question that you all might be able to help me figure out. I created a login user (luser) and attempted to edit the /usr/share/gdm/guest-session/guest-session-setup.sh file to copy /home/luser in step 6. However, it keeps defaulting to /etc/guest-session/skel/ Is there another file that I should be editing? It sure would be change things in an existing user rather than having to run (and rerun) a guest session.*

Thanks to Gunnar, I have included directions for using a regular user account on the system as the basis for the *guest-session* account. Although this is not as flexible as the system outlined by Gunnar, it has the advantage of ease. I have tried this with 11.10; it seems that there may be differences with previous versions. I have not addressed those.

> 
[LIST=1]
[*]Create a standard (non-administrator) account. 
Note: I will use the account name *luser* for this account in the rest of the instructions (*luser* means ***L**ogin **U**ser*. Really. ;) ).
[*]Log into the *luser* account and make any changes that you want using whatever tools/utilities you wish.
[*]Once you have made the desired changes, log out of the account and return to an administrative account.
[*]Edit the file /etc/guest-session/prefs.sh (if it doesn't exist, enter the command "sudo touch /etc/guest-session/prefs.sh") and add the following lines to the top of the file:
[B]cp -rT /home/luser "$HOME"
chown -R $USER:$USER "$HOME"[/B]
[*]Save the file.
[*]Log into the guest account (either from LightDM or from the *user-session* indicator) and check that all changes have been made.
[*]To update any settings, simply repeat steps 2&3.
Note: As a security measure, you may want to disable the *luser* account when not editing it.
[/LIST]


Please feel free to let me know if there are any further changes/instructions for these directions.

Peace,
Paul :cool:

BTW, I found out that Chrome won't run in a guest session due to needing suid for sandboxing. I have stuck with Firefox for the guest session.

---

### Post by Gunnar Hjalmarsson on 2012-02-27
Great example, Paul. Thanks! I added a link to your post from the "Alternate approach" section in the tutorial.

> **p-dh said:**
> I created a login user (luser) and attempted to edit the /usr/share/gdm/guest-session/guest-session-setup.sh file to copy /home/luser in step 6. However, it keeps defaulting to /etc/guest-session/skel/ Is there another file that I should be editing?
Please note that as from Ubuntu 11.10, the guest session code is included in the LightDM package; you may well remove the gdm-guest-session package. So it's probably [FONT=Courier New][SIZE=2]/usr/sbin/guest-account[/SIZE][/FONT] you want to edit.

> **p-dh said:**
> I found out that Chrome won't run in a guest session due to needing suid for sandboxing. I have stuck with Firefox for the guest session.
It would be great if you could file a bug report about that. It's [the LightDM package]("https://bugs.launchpad.net/ubuntu/+source/lightdm") such a bug should be filed against.

---

### Post by Gunnar Hjalmarsson on 2012-03-06
> **p-dh said:**
> 
Edit the file **/usr/sbin/guest-account** and change the line **gs_skel=/etc/guest-session/skel** to **gs_skel=/home/*luser***. (*sudo gedit /usr/sbin/guest-account*)


A disadvantage with editing a package file is that it needs to be redone after each upgrade. Probably better to create a symlink.

```
sudo ln -s /home/luser /etc/guest-session/skel
```

---

### Post by p-dh on 2012-03-09
Hey Gunnar,

I added the link as per your directions, but the files were not copied over. What am I missing?

Thanks for helping me get this to work.

Peace,
Paul :cool:

---

### Post by Gunnar Hjalmarsson on 2012-03-12
> **p-dh said:**
> 
I added the link as per your directions, but the files were not copied over. What am I missing?
Seems like I'm the one who missed things. :(

A working way to do what you want, without a need to redo it after each lightdm update, seems to be to create [FONT=Courier New]/etc/guest-session/prefs.sh[/FONT] and add these commands to it:

```
cp -rT /home/luser "$HOME"
chown -R $USER:$USER "$HOME"
```If [FONT=Courier New]/etc/guest-session/prefs.sh[/FONT] exists already, since you installed the tarball of this tutorial, those commands should be added to the top of the file.

---

### Post by p-dh on 2012-03-14
Gunnar, Thanks for the last post. I created the file and it works great! I found that the reason a simple link doesn't work is that /usr/sbin/guest-account has the line:
**gs_skel=/etc/guest-session/skel** and needs **gs_skel=/etc/guest-session/skel[COLOR="Red"]/[/COLOR]** for cp to work with a soft link. Weird. But, this meant that I had to edit the file after updating LightDM today. Aaargh..
Anyhow, I will include your additions to my post above. I have tried it out and it really works well.
Thanks for all of your work on this.

Paul :cool:

P.S.  Where can I find the documentation for LightDM and the files it uses for logging in?

---

### Post by Gunnar Hjalmarsson on 2012-03-14
> **p-dh said:**
> I will include your additions to my post above. I have tried it out and it really works well.
Thanks for all of your work on this.

You're welcome, and thank _you_.

> **p-dh said:**
> Where can I find the documentation for LightDM and the files it uses for logging in?

I'm not aware of any documentation besides the source code. And that's not easy to grasp. :neutral:

---

### Post by Gunnar Hjalmarsson on 2012-03-15
> **p-dh said:**
> I found that the reason a simple link doesn't work is that /usr/sbin/guest-account has the line:
**gs_skel=/etc/guest-session/skel** and needs **gs_skel=/etc/guest-session/skel[COLOR=Red]/[/COLOR]** for cp to work with a soft link. Weird. But, this meant that I had to edit the file after updating LightDM today. Aaargh..

Nice catch, Paul. I proposed that change of the source for lightdm in Ubuntu, and it was [just approved]("http://bazaar.launchpad.net/%7Eubuntu-desktop/lightdm/ubuntu/revision/1094/debian/changelog"). It means that next release will include such a trailing slash, so you may want to change comment #23 once again. ;)

---

### Post by psycato on 2012-03-27
Hi,

I've been browsing around the net trying to find a way to disable "everything" for a specific user account. That is, I only want the user to be able to start a single program as a shortcut on the desktop.

I have installed (fully installed) Ubuntu on a USB dongle and also installed gnome-session-fallback and made it boot directly into the gnome-classic interface as it's quite a bit easier to customize (as far as I know) the panels etc. compared to Unity. 

Now, by using your "disable_app()" would it be possible to disable every program that I don't want the user to be able to access? (i.e terminal, system monitor, system settings ++)

Obviously I would also have to remove right clicking, file system access, keyboard shortcuts, log out/switch user etc. I do think I have this covered, but Im at a loss as to how I can prevent the user from accessing system settings.

Basically, if only the desktop was shown (without menus) that would be perfect, but Im pretty sure that's not possible :)

Any pointers would be greatly appreciated!

regards,
Cato

---

### Post by Gunnar Hjalmarsson on 2012-04-19
> **psycato said:**
> ... by using your "disable_app()" would it be possible to disable every program that I don't want the user to be able to access? (i.e terminal, system monitor, system settings ++)
No. "disable_app()" prevents automatic startup of applications that otherwise would have been automatically launched at startup. It does not prevent the user from launching those applications 'by hand'.

---

### Post by gussug on 2012-05-15
does anyone know if i can access a nfs mounted directory from a guest session?
i can access to usb drives if i plug one with guest, but can't to a mounted nfs. loggin with an ordinary user works well.
my fstab entry is: ip://folder /media/folder ro,users 0 0
i tried putting uid and gid, but the guest uid seems to change dinamicaly.

[edit] running Ubuntu 12.04

---

### Post by elysithea on 2012-06-05
I have used the alternative method in #23 with some success but I am having issues with the Background. When in the guest session I select a picture that I have copied into the Pictures folder of the Guest account and it appears fine. After switching back to the Administrator account and copying the tmp guest user folder to the etc/guest-session/skel the picture is there. However when I log back into the guest account I get the blue background and not the picture, however the picture is there to select. I am using 12.04,

Does anyone have any ideas what is going on? Also does the tar at the beginning of this thread work in 12.04?

---

### Post by elysithea on 2012-06-05
I managed to fix the Background issue with this guide:

[http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594](http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594)

And I could not get the tar for lightDM to work in 12.04, it installs but then I couldn't get into the guest account ;), although the #23 post method works to change some simple stuff.

---

### Post by doce on 2012-06-24
Hello guys,

I have a problem with desktop launcher (for wine program) on guest session. My Ubuntu version is 12.04 LTS and Wine 1.4.1. So, when i want to run e.g Counter Strike game via desktop launcher, nothing is happening but when i run it via terminal, game works. Game is installed in /opt/games via standard user account named pc01-master and works on that and administrator account but on guest session I can run only via terminal when execute:

```
env WINEPREFIX="$HOME/.wine" wine z:\\opt\\games\\CS1.6\\Counter-Strike.exe
```

That is command from desktop launcher but launcher won't execute it. :S When I put in launcher command without wine prefix:

```
wine z:\\opt\\games\\CS1.6\\Counter-Strike.exe
```

I get wine error: 
```
Internal errors - Invalid parameters received
```

I have tried in many ways, but without success:

Remove .wine folder from guest-xxxxxx home folder, modify permissions, same user groups, auto chown and chmod 777 /opt and .wine folder (pc01-master) to guest-xxxxxx via /etc/guest-session/prefs.sh but without success unfortunately. :(

I noticed that when I remove .wine folder from pc01-master home folder and run desktop launcher from guest session, i get this error:

```
Failed to change to directory '/home/pc01-master/.wine/dosdevices/z:/opt/games/CS1.6/' (No such file or directory)
```

Also I noticed that is /home restricted for guest, I can't access via Nautilus and probably because it desktop launcher does not work.

Maybe I don't setup some permision correctly but i don't known what. :S Thanks in advance for your help.

---

### Post by Gunnar Hjalmarsson on 2012-09-07
> **gussug said:**
> does anyone know if i can access a nfs mounted directory from a guest session?
i can access to usb drives if i plug one with guest, but can't to a mounted nfs. loggin with an ordinary user works well.
my fstab entry is: ip://folder /media/folder ro,users 0 0

I think it's intentionally prevented via AppArmor.
```
$ grep /media /etc/apparmor.d/lightdm-guest-session
  owner /media/ r,
  owner /media/** rmwlixk,  # we want access to USB sticks and the like
$
```

---

### Post by Gunnar Hjalmarsson on 2012-09-07
> **doce said:**
> Also I noticed that is /home restricted for guest, I can't access via Nautilus ...
Guests are denied access to /home by design (via AppArmor).

---

### Post by Gunnar Hjalmarsson on 2012-09-07
> **elysithea said:**
> And I could not get the tar for lightDM to work in 12.04, it installs but then I couldn't get into the guest account ;), although the #23 post method works to change some simple stuff.
The tar **[FONT=Courier New]guest-session-prefs-lightdm-0.12.tar.gz[/FONT]** works fine on my 12.04. You may want to provide some more details about the nature of your problems.

---

### Post by Bezimeni on 2012-10-04
Hi guys, is there a way to disable authentication required for VPN so people using guest session can use internet?

---

### Post by m2xtreme on 2012-10-26
This is just what I needed!  Thanks to Gunnar Hjalmarsson and p-dh, you both have saved me a lot of time and effort.

---

### Post by leona on 2012-12-26
When I try the install script I get "Couldn't find /usr/share/gdm/guest-session/guest-session-launch".
I am using 12.04 Gnome with GDM.
Ops sorry I didn't realise I needed to install the gdm-guest=session package first from here [https://launchpad.net/ubuntu/precise/amd64/gdm-guest-session/0.27](https://launchpad.net/ubuntu/precise/amd64/gdm-guest-session/0.27)
but doing so gives me
> dpkg: dependency problems prevent configuration of gdm-guest-session:
 gdm (3.0.4-0ubuntu15) breaks gdm-guest-session and is installed.
dpkg: error processing gdm-guest-session (--install):
 dependency problems - leaving unconfigured
so it refuses to install.

---

### Post by xaviercomputers on 2013-01-31
Does anyone know if there is anything different I have to do to customize the guest account in ubuntu 12.04 and 12.10?  I run a all ubuntu computer lab and only allow the guest account to the general public.

---

### Post by ferrerojv on 2013-05-15
Thanks! I've been using Ubuntu since 11.10 and just recently turned on the guest account because my wife's Windows machine died. My poor daughter spent several hours yesterday typing up study notes and they are all gone now because we didn't realize the guest account didn't save files permanently. Fortunately she's one of the smartest people I've ever met and will probably retain most of it just from typing the notes, but I still felt like I let her down not knowing about it. So thank you for your work on this.

---

### Post by bcooperb on 2013-06-12
Greetings all! It seems you all have been busy since the last time I checked this out. You've needed some new features. My question is this:

My current project with OSS in Education. I currently have 1 Open Source Public Access computer in our University Library. It is running Ubuntu 13.04 with a great deal of educational and productivity software on it. I was just having people login with the Guest account so no mater what they did it would go back to normal when they logged out.

I now want to set one up in our Music/Art/Education building along with a donated Yamaha MIDI keyboard with Piano Booster on it. With downloading MIDI files and playing them in Piano Booster, I didn't want them to use guest because I didn't want someone to have to download them all over again.

Should I just make a public access user and let anyone just download anything, along with MIDIs files to use on that system? Please advise on a setup. Thank you!

---

### Post by Arjunanda on 2013-06-19
You can use this tarball setup given in the first post of this thread and advise the users to save the midi files in the /var/guest-data folder. You can even rename the folder to your liking, for instance /var/midi-files

You could also configure the pop-up dialog shown at the startup to inform users about that.

---

### Post by gunnarhj on 2013-12-08
> **gussug said:**
> does anyone know if i can access a nfs mounted directory from a guest session?

Possibly that requires editing of the AppArmor profile. In Ubuntu 13.10 it's located at /etc/apparmor.d/abstractions/lightdm, but if I recall it correctly, in Ubuntu 12.04 it was stored in some other file with "guest-session" in the file name.

*Edit:* I see now that I replied to this in September 2012. Sorry for the noise.

---

### Post by gunnarhj on 2013-12-08
> **elysithea said:**
> I could not get the tar for lightDM to work in 12.04

Please note that the tar that fits 12.04 is [guest-session-prefs-lightdm-0.12.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=212946&d=1329630310").

*Edit:* I see now that I replied to this in September 2012. Sorry for the noise.

---

### Post by coffeecat on 2014-01-29
As noted in the edited first post, this tutorial is now deprecated and has been replaced by the [CustomizeGuestSession]("https://help.ubuntu.com/community/CustomizeGuestSession") page on the Community Help Wiki. If you need help with this, please post in a support section of the forum.

Thread closed.

---

