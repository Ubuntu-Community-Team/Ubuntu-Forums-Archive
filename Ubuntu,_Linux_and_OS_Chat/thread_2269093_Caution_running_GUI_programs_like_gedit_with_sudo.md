---
title: "Caution running GUI programs like gedit with sudo"
date: 2015-03-13
forum: Ubuntu, Linux and OS Chat
---

### Post by TheFu on 2015-03-13
Last weekend, I was helping someone very new to Linux troubleshoot an issue.
He had just loaded Ubuntu and followed a guide somewhere that had him run 

```
sudo gedit
``` to modify some file in /etc. The file didn't matter.

Since this was one of the first commands he ever ran, it created the ~/.gnome or ~/.gnome2 directory - AS ROOT.  **sudo cmd** doesn't alter the environment to be safe, so $HOME was left to the userid, not /root/. Seems at least 1 gnome-based program will crash if it can't save settings into those directories, firefox. I suspect there are many others. I haven't looked at the gnome-settings code to know if the problem with crashing is there or in the application's implementation.

Since it was a new installation, we wiped all the prior settings - ~/.[a-z]* - that fixed it.

Sadly, this sort of advice is all over the internet, so only a strong education campaign to stop will work. As much as it pains me to say, could we please be consistent and suggest using nano for all system-level file edits? ```
sudo nano
``` won't break things and it works on desktops and servers. I purge nano from my installs - **sudo vim** works great, but vim is highly selective about which users it is friendly towards, so **sudo nano** is less evil.

Or is there a better option?
sudo -i gedit will work on desktops, since it loads the settings for root, but it will fail on servers without X/Windows.

---

### Post by Elfy on 2015-03-13
Since the demise of gksu(do) in default installs, there should be pkexec profiles, so pkexec gedit. 

But I tend to when I can sudo nano too, if nothing else people get the opportunity to use it BEFORE they've got to use it in recovery mode.

---

### Post by slickymaster on 2015-03-13
> **Elfy said:**
> Since the demise of gksu(do) in default installs, there should be pkexec profiles, so pkexec gedit. 

But I tend to when I can sudo nano too, if nothing else people get the opportunity to use it BEFORE they've got to use it in recovery mode.
+1

---

### Post by Lars Noodén on 2015-03-13
[s]Actually [visudo](http://manpages.ubuntu.com/manpages/trusty/en/man8/visudo.8.html) is even safer.  It makes a copy of the file first and then runs the editor as the unprivileged user.  It will run nano if so decided.  A further advantage of vi or nano is that the edits can be done remotely.  [/s]

I'm sad though to hear about pkexec over sudo.  2016 and then with finality  2019 will soon be here.  It was good while it lasted.

EDIT: Ugh.  I should read what I type.  I meant to write [sudoedit](http://manpages.ubuntu.com/manpages/trusty/en/man8/sudoedit.8.html) instead of visduo.  I don't multitask.

---

### Post by TheFu on 2015-03-13
[https://help.ubuntu.com/community/gedit](https://help.ubuntu.com/community/gedit) is not clear where they say > 
To edit system files such as sources.list and fstab, open it with administrative privileges. Note graphical applications use gksudo rather than sudo. 
This is not emphasized and the note is not strongly worded enough to make it clear what the risks are if sudo gedit is used to edit system files.

I would change some of these documents, but can't figure out how in 5 minutes or less.

[https://help.gnome.org/users/gedit/stable/gedit-edit-as-root.html.en](https://help.gnome.org/users/gedit/stable/gedit-edit-as-root.html.en) - ouch - they aren't helping!
[http://www.unixmen.com/how-to-change-the-default-boot-order-for-grub2-in-ubuntu-1004-and-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/how-to-change-the-default-boot-order-for-grub2-in-ubuntu-1004-and-ubuntu-1010-maverick-meerkat/) - a reputable site gets this wrong.

Most new-to-Unix users are confused by sudo already and will miss the subtle difference between gksudo vs sudo.  I see this all the time at local LUGs.

---

### Post by tgalati4 on 2015-03-13
You have pointed out an important issue.  *Gedit* provides a graphical environment for those who think the command line is too scary or that entering commands in a DOS-like window is too retro, but it can lead to problems.

I usually give command line advice because I have no idea what environment is being run.  Often new users don't give enough information in the first post anyway, so I try to find out more using command line tools like *dmesg*, *free*, or catting log files to see what is going on.  I don't use *gedit* because I run MATE and that has been replaced with *pluma*, so not every system has *gedit* installed. 

*Nano* is installed as the default Raspbian text editor and a lot of new folks are getting exposed to GNU/Linux so *nano* is a good recommendation.

---

### Post by rrnbtter on 2015-03-13
Greetgings,
sudo -H

---

### Post by ajgreeny on 2015-03-13
It seems to be safe to use sudo with a suffix such as **sudo -H** or **sudo -i** rather than just sudo to open GUI applications, but it is possible to use pkexec already, with an alias as I have made, and use when I remember, to do so.  The alias needed is ```
alias pkx='pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY'
``` but I accept that doing this is probably beyond the inexperienced user of Ubuntu.

Even more complicated is the possibility to make new pkexec policy files specifically for applications that you might want to use with root permissions. Such files need the following content:-
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
  "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
  "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>

  <action id="com.ubuntu.pkexec.thunar">
    <message gettext-domain="gparted">Authentication is required to run thunar</message>
    <icon_name>thunar</icon_name>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/thunar</annotate>
    <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
  </action>

</policyconfig>
```
and in Xubuntu are put added to **/usr/share/polkit-1/actions/** with names in form of **com.ubuntu.pkexec.thunar.policy**

I have the above file for thunar and another for mousepad (I just replaced the word **thunar** with **mousepad**) and both seem to work with no problems or faults.  Again, probably not something for new users, but at least it proves it can be done.

---

### Post by rrnbtter on 2015-03-13
Greetings,
@ajgreeny  +1, but
I just don't like the name pkexec (too Windows-ish). They should change the name to something Linux-ish!

---

### Post by TheFu on 2015-03-13
Ajgreeny - that doesn't seem like an intuitive answer for the issue.

The person I was helping found lots of "outdated" how-tos and decided to follow one of them.  sudo won't be gone for many more years.  We **can** do something about this today and it is simple.
**sudo nano**

Programs that behave differently - like magic - seem like a really bad idea to me.

OTOH, I've used gksudo maybe 2 times in my life. Sorta don't see the point.

---

### Post by Lars Noodén on 2015-03-13
Sorry. :/ I meant to write [sudoedit](http://manpages.ubuntu.com/manpages/trusty/en/man8/sudoedit.8.html) instead of visduo. I've edited my post above to reflect this.

---

### Post by TheFu on 2015-03-13
> **Lars Noodén said:**
> Sorry. :/ I meant to write [sudoedit](http://manpages.ubuntu.com/manpages/trusty/en/man8/sudoedit.8.html) instead of visduo. I've edited my post above to reflect this.

I like this the best!  Is is already on "server" - nothing new to install.  Honors EDITOR, so it can be customized following the 40+ yr Unix history. Won't trash personal settings ... 

**sudoedit** ... nice.

---

### Post by kevdog on 2015-03-13
Sorry for thread hijack -- however I wasn't aware sudo was going away, nor did I realize gksu wasn't installed by default.  Man -- am I behind the times!! When did this happen?

---

### Post by TheFu on 2015-03-13
> **kevdog said:**
> Sorry for thread hijack -- however I wasn't aware sudo was going away, nor did I realize gksu wasn't installed by default.  Man -- am I behind the times!! When did this happen?

If there isn't any GUI,  gksu* does not get installed.
If you start with a server install and add only select GUI programs, it isn't installed either.

Many people are learning Linux because they are using a VPS, not a desktop. All the instructions that use gedit or any GUI-based editor are often confusing to those people, since the command won't work.

---

### Post by polki@mac.com on 2015-03-14
If there isn't any GIU then you won't be able to use gksu? Sounds fair to me. Why try to bring up a gui in a non-gui environment??? I don't get it...

---

### Post by TheFu on 2015-03-14
> **polki@mac.com said:**
> If there isn't any GIU then you won't be able to use gksu? Sounds fair to me. Why try to bring up a gui in a non-gui environment??? I don't get it...

That is correct. gksu/gksudo require gnome libraries which aren't loaded on server installs.
```
$ gksu
The program 'gksu' is currently not installed. You can install it by typing:
sudo apt-get install gksu

```

People follow instruction online all the time.  The person creating those instructions means well, but often they aren't much more than a noob themselves. The writer simply doesn't know better.  We all have blind spots in our knowledge. I do. Never heard of pkexec before. I'm still unhappy about systemd trying to fix a problem I never had - and don't get me started about resolvconf doing the same thing.

People new to Linux don't always start at the beginning in their learning - they google for an answer, find a slick website and start copy/pasting.  Something doesn't work, so clearly it is Linux at fault - nothing should be that hard.  They google again, find different steps and it works this time, but the failed steps in the first set of instructions are left behind (for better or worse).

The more you try to help new linux users, the more you see this same issue. I was helping a self-proclaimed "IT professional with 20+ years of experience."  He had less than 3 weeks of Unix experience. He wanted to change the boot up image and found instructions that said sudo gedit /etc/grub.d/ something. Since it was the first command he ran, it screwed the ownership of this config directories. This was the beginning of his issues and why I posted this thread. He was a smart guy, but just didn't have enough experience to recognize the multi-user issues. His 20+ yrs of Windows experience in a small business environment didn't help.

---

### Post by SeijiSensei on 2015-03-14
As a long-standing KDE user, I'll just observe that any suggestions requiring GNOME libraries will cause pain and gnashing of teeth.  That's why I almost always provide solutions that rely on the terminal.  The only time I make GUI-based suggestions is when someone is also using Kubuntu and looking to change something like an item in SystemSettings.

---

### Post by mc4man on 2015-03-14
I've been suggesting for some time that people in this forum stop suggesting sudo gedit, some pay attention, some don't.

As far as online  - until recently (maybe < 12.10 in Ubuntu terms) the use of sudo gedit was perfectly fine in a Desktop install. It would use root's config & caused no issues whatsoever. So online suggestions to use sudo gedit weren't wrong or misinformed in those cases. 
Now anyone on a current Ubuntu or similar gnome based install would be wrong suggesting as sudo gedit now uses the user's config & can create a couple of side issues.

Policykit works fine but it's better if the policy is installed with the app, at least in terms of gedit & nautilus. If manually added by the user then many times what noted in post 8 comes into play..

nano seems the best option overall  but if gedit is desired then sudo -H gedit or sudo -H nautilus is currently best choice.
(source installed policy's for gedit & nautilus aren't available from Debian/Ubuntu & likely won't be, they are in a ppa or 2..

---

### Post by TheFu on 2015-03-14
Actually the best idea from that other thread is to use **sudoedit**.  It uses the default $EDITOR and copies the file somewhere, runs the editor as the normal userid, then copies the modified file back to the location where the permissions are retained.

The real issue with using GUI tools and sudo together are:
a) often times it just isn't necessary - the current userid is fine. Pure laziness for lack in understanding file/directory permissions.
b) GUI programs tend to write config files based off the $HOME - sudo doesn't modify HOME, **sudo -i** will. If the program wasn't already run as a normal user, then root will own the config file and perhaps the parent directory and perhaps the parent directory of that as well. Some programs refuse to run if they cannot create a config file.

They also said something about sudo going away - being replaced by **pkexec**. Meh.

I find it easier to recommend that new users NEVER run any GUI program as root. Keeps them out of all sorts of problems. ;)

---

### Post by mc4man on 2015-03-14
> **TheFu said:**
> 

They also said something about sudo going away - being replaced by **pkexec**. Meh.


who ever said that?

---

### Post by ajgreeny on 2015-03-15
> [QUOTE]Originally Posted by **TheFu**[INDENT]
They also said something about sudo going away - being replaced by **pkexec**. Meh.

 			 		
 	
 
who ever said that? 						[/INDENT] 					
  					 				
 			
[/QUOTE]I think it is just gksu and gksudo going away, isn't it, not sudo?

---

### Post by slickymaster on 2015-03-16
> **ajgreeny said:**
> I think it is just gksu and gksudo going away, isn't it, not sudo?
You're right ajgreeny. Gksudo and others are deprecated now and not recommended any more. Pkexec is the new proposed approach.

Discussion here: [http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832)

---

### Post by Lars Noodén on 2015-03-16
> **slickymaster said:**
> Discussion here: [http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832)

Is there an authoritative source on any decision, past or pending?  I don't care about gksu or gksudo, those are doable with -H on sudo.  But looking at pkexec, I see that its configuration is way too difficult and complicated to be able to recommend its use to any beginner or intermediate users.  Extended Backus-Naur Form (EBNF) used by sudoers is much simpler and thus less prone to error.  It's doable for even casual users and sysadmins.

---

### Post by slickymaster on 2015-03-16
> **Lars Noodén said:**
> Is there an authoritative source on any decision, past or pending? I don't care about gksu or gksudo, those are doable with -H on sudo. But looking at pkexec, I see that its configuration is way too difficult and complicated to be able to recommend its use to any beginner or intermediate users. Extended Backus-Naur Form (EBNF) used by sudoers is much simpler and thus less prone to error. It's doable for even casual users and sysadmins.
According to its [changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/g/gksu/gksu_2.0.2-6ubuntu2/changelog"), it was dropped as it wasn't ported to Gnome 3 and that was blocking the transition to Nautilus 3.

---

### Post by Lars Noodén on 2015-03-16
> **slickymaster said:**
> According to its [changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/g/gksu/gksu_2.0.2-6ubuntu2/changelog"), it was dropped as it wasn't ported to Gnome 3 and that was blocking the transition to Nautilus 3.

Ok.  Thanks.  Again, losing gksudo or gksu is not a big deal, but it was sounding like [sudo](http://changelogs.ubuntu.com/changelogs/pool/main/s/sudo/sudo_1.8.9p5-1ubuntu5/changelog) might have been in danger.  I see that sudo is still available.

---

### Post by TheFu on 2015-03-16
@Slickymaster - thanks for that link. Explains much.

Seems there are 2 use-cases for gksu.
* editing files
* running GUI programs

If **sudoedit** hasn't been deprecated, seems that is a simple answer for the main use-case with a few excellent reasons to use it.
The 2nd doesn't apply in this thread which was only about editing.

Do people really run file managers as root?  I don't use file managers very often, so it is completely outside my knowledge.

---

### Post by mastablasta on 2015-03-16
I use nano on server. it is also not really that friendly. I am comparing it with the old MS-DOS edit.exe (not edlin which was horrible) and edit is far easier to work with (can even handle a mouse propperly). not sure is edit actualyl a command line editor or would it fall under GUI in linux. anyway since nano isn't that nice  sometimes I use the editor available on server's webGUI. 

on desktop I use Kubuntu so I use kdesudo. I guess this is not deprecated then?! I use it often for editing in kate editor but even more often with dolphin when I am moving files arround into system folders. it just a lot easier and faster to do that in GUI than to type all those files in cli. and have them copied into correct folder. but that's about the only two times I touch the graphical sudo interface.

---

### Post by TheFu on 2015-03-16
@master - just set your EDITOR environment variable to the editor you want on each system, then use **sudoedit** and be happy.

Drop **export EDITOR=/usr/bin/vim** or **export EDITOR=/usr/bin/geany** or any favorite editor into your ~/.profile or ~/.bashrc and forget it. sudoedit will do what you want.

---

### Post by mc4man on 2015-03-16
It wasn't dropped as in not available, it was dropped from the default Ubuntu images, period.
 Still available, still works, still used by some packages, still inc. by some like lubuntu

---

### Post by ajgreeny on 2015-03-17
As nano is the default terminal text editor in Ubuntu I find it hard to see a real practical difference between **sudoedit** and **sudo nano** apart from the way sudoedit first copies the file to tmp, then edits then copies it back, replacing the original (I think it does, anyway).

@TheFu
Can you change that line you mention to a GUI text editor, eg **export EDITOR=/usr/bin/mousepad **and thus use a GUI instead of terminal editor.
[COLOR=#ff0000]EDIT:  I have just tried it and the answer to that question is - Yes, it will work with a GUI application, but only if in an xsession, of course.  I have no wish to use it but was simply interested to know.[/COLOR]

I often use nano for text edits but never have used vi or vim -just too unintuitive to my way of thinking; powerful? Yes, but too cumbersome by far for a simple text file edit.

---

### Post by SeijiSensei on 2015-03-17
I grew up using Emacs and now use John Davis's [jed]("http://www.jedsoft.org/") in its default Emacs mode.  If you know the Emacs control-key sequences it's pretty efficient, but jed also includes a menu in case you need to access the more obscure functions.  It's in the repositories.

---

### Post by TheFu on 2015-03-17
> **ajgreeny said:**
> 
[COLOR=#ff0000]EDIT:  I have just tried it and the answer to that question is - Yes, it will work with a GUI application, but only if in an xsession, of course.  I have no wish to use it but was simply interested to know.[/COLOR]

As most end users who would run gedit would never be in a non-GUI environment, it probably doesn't matter if a GUI editor or one that works in a terminal is specified.  Until they are told to ssh into the machine remotely and asked to edit a system file and all they see is an X11 error. To the informed, that error happens enough to be exactly understood. Can't say what a newer Linux user would think of it.

---

### Post by ajgreeny on 2015-03-17
> **TheFu said:**
> As most end users who would run gedit would never be in a non-GUI environment, it probably doesn't matter if a GUI editor or one that works in a terminal is specified.  Until they are told to ssh into the machine remotely and asked to edit a system file and all they see is an X11 error. To the informed, that error happens enough to be exactly understood. Can't say what a newer Linux user would think of it.But if they can't make use of the relatively simple nano text editor to edit and save a file I think using ssh would be way beyond their abilities.

However, I think what this shows is exactly how remarkably flexible Linux is and how easily it is possible to change almost anything you want to change, even if, as in my case, it was simply to test whether or not it was possible.

---

### Post by TheFu on 2015-03-17
At a weekly LUG where we cater to complete beginners, one of the first things we teach is remote access using ssh, sftp and scp using key-based authentication.  

Why? For the WOW factor.  Plus ssh is amazing and something they probably never did with other OSes.  Explaining that they can securely access file from anywhere in the world this way is a huge selling point for our 398+ members.  We've been growing 2-4 members every week WITHOUT any clear programs or presentations.  Folks just come, sit, listen, ask questions, and have a meal and a drink on a Sunday afternoon. We have members from all walks of life - total beginner thru to kernel devs, debian maintainers, IETF members, etc.   
If a user has a specific question AND they've tried to solve it themselves already, we'll use that as the topic for the session. They have to have made an effort.  If they haven't made any effort, then they should pay for support, period. **We aren't free support, we are free learning.**

Flexibility is something we stress along with learning the command line for long-term users.  Sadly, we also teach google-fu more than I'd like.  People will drive 90 min each way to our meetings, but they won't bother to google for an answer and try it first. I don't get it.

You might recall that this entire thread was started because an IT Pro, but Linux noob, ran sudo gedit following a guide and appeared to have broken his system. He's been back a few times with interesting questions. Nice guy and helping him teaches me things that I'd otherwise never learn.  I suppose that is part of the reason we are all here - we are addicted to learning AND helping.

---

### Post by sudodus on 2015-03-18
> **TheFu said:**
> ... I suppose that is part of the reason we are all here - we are addicted to learning AND helping.

A big [SIZE=4]+1[/SIZE] :-)

---

### Post by Morbius1 on 2015-03-18
> **mc4man said:**
> It wasn't dropped as in not available, it was dropped from the default Ubuntu images, period.
 Still available, still works, still used by some packages, still inc. by some like lubuntu
> **rrnbtter said:**
> Greetgings,
sudo -H
Well, I suppose if we don't have gksu installed by default on some desktops and for some reason we don't want to install it we can always make an alias .... and call it ... oh I don't know ... gksu ...  and have it set to "sudo -H"

Then again that's basically what gksu is:
> morbius@vub14:~$ gksu -d gedit
No ask_pass set, using default!
xauth: /tmp/libgksu-I9UxUZ/.Xauthority
STARTUP_ID: gksu/gedit/3993-0-vub14_TIME2133890
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: -GNOME_SUDO_PASS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...



---

### Post by philinux on 2015-03-18
Nice little how to here from webupd8.org

[http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html](http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html)

---

### Post by Morbius1 on 2015-03-18
Nope, the title of this thread is: "Can we stop sudo gedit recommendations?"

Are we to suggest to new users that they hack the "Linux Registry"?

Seriously, If you look at the contents of /tmp/org.gnome.gedit.policy from that howto it sorta kinda resembles a Windows Registry hack: [http://www.howtogeek.com/167579/how-to-make-your-own-windows-registry-hacks/](http://www.howtogeek.com/167579/how-to-make-your-own-windows-registry-hacks/)

Maybe it's just me.

I know ... I know.... adapt or perish ...

---

### Post by philinux on 2015-03-18
Maybe the ubuntu devs need to include the needed files so that pkexec works out the box.

---

### Post by sudodus on 2015-03-18
> **philinux said:**
> Maybe the ubuntu devs need to include the needed files so that pkexec works out the box.

That's a good idea. I would add ***zenity*** to that wish-list for policy files.


[LIST=1]
[*]gedit
[*]nautilus
[*]zenity
[*]... (?)
[/LIST]

I think many new and average linux users will be frustrated if most system tasks must be done with command line tools within a few years. It is rather easy to wrap a command line tool in a zenity GUI, and make such users happy.

Don't get me wrong, I'll manage, but I grew up with text based terminals and proprietary text based systems, later on VMS, DOS (before Windows), UNIX, ... I'm thinking of the next generation, where most people are used to GUI tools.

---

### Post by Lars Noodén on 2015-03-18
> **sudodus said:**
> I would add ***zenity*** to that wish-list for policy files.

I took a look at it.  The file format for the policy files seems undocumented.  There's nothing in man5 that looks related, nor is anything in man5 referenced in the manual page for pkexec.  However, the manual page does contain the gem, 

"[Note that pkexec does no validation of the ARGUMENTS passed to PROGRAM.](http://manpages.ubuntu.com/manpages/trusty/en/man1/pkexec.1.html)"  

Nor does it protect against shell escapes, at least from my one test.  So pkexec falls about a mile short of [sudo and sudoedit](http://manpages.ubuntu.com/manpages/trusty/en/man8/sudoedit.8.html), both of which can run validation on the parameters being passed to the program being run as another user.   The whole point of sudo is to provide a high level of granularity of the control of both programs and their parameters.  If that's getting thrown away, we might as well go to "su" or even just reenable the root account.  So, lacking any link to any authoritative source on a decision, I'd consider any rumor of ascendency for pkexec to be a rumor. 

As mentioned above, "sudo gedit" can and should be replaced by [s]"sudoedit gedit",[/s] *sudoedit* it takes advantage of the simplicity and flexibility  "sudoers".  "sudoedit" in particular can run any program, graphical or normal, because the program is run by the current user and then the file swapped out as the other user only after the edit is finished.  That prevents not only the permissions problems mentioned in #1 above, but also prevents shell escapes and similar tricks that "sudo -H" would miss (unless configured beyond the defaults).

---

### Post by Morbius1 on 2015-03-18
> **TheFu said:**
> Last weekend, I was helping someone very new to Linux troubleshoot an issue.
He had just loaded Ubuntu and followed a guide somewhere that had him run 

```
sudo gedit
``` to modify some file in /etc. The file didn't matter.
pkexec or gksu we are still left with the same original problem.

Someone somewhere is going to suggest "sudo gedit". 

Make it so that "sudo some-gui" doesn't run. And in the error message suggest gksu or pkexec.

Also might want to explore an entire paradigm shift and look at how OSX does does this sort of thing most of the time.

If you try to do something only root can do in Linux you'll get an error message telling you that.
If you try to do something only root can do in OSX you'll get prompted for sudo's password.

---

### Post by Elfy on 2015-03-18
At the end of the day it's only ever going to be local, and only ever going to be people that know not to tell people sudo gedit.

Good luck getting devs to do anything - one of the reasons I read as a basis for the loss of gksu(do) from default - was basically why are people not sudo 'cli edit' of choice for system files.

---

### Post by TheFu on 2015-03-18
> **Morbius1 said:**
>  Are we to suggest to new users that they hack the "Linux Registry"?

I miss the days of simple .ini files in Windows.  Heck, I even miss OS/2 (which was a great OS with $650 to get 8MB of RAM).

If that is the direction here ... hello BSD for me!
I still have a SPARC IPX (slower than a Pentium90, but ), please don't make me use it!  PLEASE, Please, please?

> **Morbius1 said:**
> Make it so that "sudo some-gui" doesn't run. And in the error message suggest gksu or pkexec.
Shouldn't be too hard - just check the **ldd** dependencies quickly - if X11 (or whatever new thing) is in that list - kick out the warning.
```
$ ldd  /usr/bin/leafpad |grep -i X11
        libgtk-x11-2.0.so.0 => /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0 (0xb7325000)
        libgdk-x11-2.0.so.0 => /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0 (0xb7276000)
        libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xb6c96000)
```
Simple.

Ah ... but it might break code for lazy commercial devs.  I've seen some Oracle Enterprise products require xvfb to start - even for only CLI stuff. A bunch of geniuses mandate that on huge DB servers, I say.

---

### Post by DuckHook on 2015-03-19
As much as I admire and respect all you gurus, there is an air of unreality to this thread that really must be pointed out. Asking most novices to use nano as their config file editor is tantamount to driving them back to Windows. Not all of them, I concede; some will stick around because they are so fed up with Windows that they would rather wrestle alligators than switch back. But such are clearly not the majority.

I don't have to go far. Ask my wife to use nano? She'll sarcastically tell me to go whip up a Chateaubriand for dinner tonight (I've got her entirely switched to Linux now, BTW).

Most of us on these forums have been Linux hounds for so long that the CLI is an old friend and we've forgotten what it looks like to the novice Windows refugee. In case we've forgotten, to most such novices, it looks like a rabid wolverine or at best an angry porcupine. If they run into issues that require messing with config files, they are already feeling like dummies who are six inches (cm for our metric friends) tall. The last thing they need while already feeling so helpless is to be told that they've got to manhandle this mad wild beast of a command line in order to solve their problem. I may have indulged in some hyperbole just now, but not a whole lot.

I get TheFu's initial post and can commiserate with his frustrations. We've all had to unravel the misdirection of some well meaning but ill-informed know-it-all who thinks he can help the universe by posting a youtube video to the world demonstrating his ignorance. But that's just the way it is. We can't stop people giving bad advice if we value our freedom to give good advice. It's the yin and the yang of the internet.

I don't pretend to have a solution. But asking novices to use nano instead of gedit ain't it.

---

### Post by TheFu on 2015-03-19
> **DuckHook said:**
> I don't pretend to have a solution. But asking novices to use nano instead of gedit ain't it.

I think you've missed the point.  

It isn't about the editor. It is about providing the best, clearest, help possible that doesn't also break the system for the user with unexpected side-effects.

For some situations, using *sudo gedit* CAN BREAK THINGS on the system making it behave strangely for that userid. We aren't talking about an editing mistake. We've been talking about side effects just from running the program (and many other GUI programs have the same issue).

The best answer I've seen so far is to train people to use **sudoedit file.txt**.

---

### Post by Morbius1 on 2015-03-19
I'm afraid that Elfy probably has the correct assessment of this issue:
> **Elfy said:**
> At the end of the day it's only ever going to be local, and only ever going to be people that know not to tell people sudo gedit.

Good luck getting devs to do anything - one of the reasons I read as a basis for the loss of gksu(do) from default - was basically why are people not sudo 'cli edit' of choice for system files.
Conceptually, if you want to prevent the user from doing something dangerous to his OS then the OS needs to change to prevent him from doing so. That isn't something Linux does since it always assumes the user knows what he's doing.

[COLOR=#0000cd][I]Side note: Think about it. Windows creates a cache of all important system files. If the user gets drunk and disorderly and deletes some important dll somewhere Windows just replaces it with the one in cache because it assumes it's user is an idiot. OSX has a different approach in that it doesn't even allow the user to view any system files unless he knows how and most OSX users don't even know they have a terminal. ...... Linux allows it's users to delete away ...
[/I][/COLOR]
The rest of this discussion of the technical superiority of gksu vs pkexec vs nano vs vi .... vs whatever ... is too late for the user that just issued a "sudo gedit".

---

### Post by Lars Noodén on 2015-03-19
> **Morbius1 said:**
> OSX has a different approach in that it doesn't even allow the user to view any system files unless he knows how. Linux allows it's users to delete away ...

We're talking about the user's own configuration files here, the ones that get munged if sudoedit is not run or plain sudo is run without -H on graphical programs.  On OS X those would be the files in ~/Library/

FWIW I wrote last week to the feedback address listed in the Gnome link that TheFu posted but have not heard back.  Their page still advises "sudo gedit" instead of "sudo -H gedit" or "sudoedit"

---

### Post by Morbius1 on 2015-03-19
What?

I'm talking about system files ... you know ... /etc/hosts in OSX.

Finder doesn't show it unless you go through "Go to Folder". This effectively prevents the user form doing something silly since the average OSX user doesn't even know there is a /etc folder.

---

### Post by TheFu on 2015-03-19
There is an easy answer for the issue I encountered.  Run **gedit** without sudo first.

* gedit (change a preference)
* sudo gedit

That should prevent the issue and only needs to be run once - AND only for people who insist on using a GUI editor.

---

### Post by ajgreeny on 2015-03-19
> **TheFu said:**
> There is an easy answer for the issue I encountered.  Run **gedit** without sudo first.

* gedit (change a preference)
* sudo gedit

That should prevent the issue and only needs to be run once - AND only for people who insist on using a GUI editor.
You have lost me totally with this suggestion; I do not understand what you mean so please explain in clearer terms.

@Lars Noodén
You say in a previous post "As mentioned above, **sudo gedit** can and should be replaced by "**sudoedit gedit**".

No, I'm afraid that does not work in the way I suspect you think it does; all it does is create and open a new file called **gedit** with no content, it does not actually open gedit with root permissions as I think you expected it to.  In order to open gedit using sudoedit you need to change the editor environment variable as mentioned by TheFu, above with the addition of a line **export EDITOR=/usr/bin/gedit** in your own .profile or .bashrc file. Then using command **sudoedit /etc/fstab** will open fstab as root in gedit instead of the default of text-editor nano.

---

### Post by Lars Noodén on 2015-03-19
> **ajgreeny said:**
> 
@Lars Noodén
You say in a previous post "As mentioned above, **sudo gedit** can and should be replaced by "**sudoedit gedit**".


It should be sufficient to just type **sudoedit** and then let it sort out the editor.  There are several ways to get sudoedit to run gedit.

Thanks for catching that.  I'm too full of typos in this thread.  I'lll just watch for a while instead.

---

### Post by TheFu on 2015-03-19
> **ajgreeny said:**
> You have lost me totally with this suggestion; I do not understand what you mean so please explain in clearer terms.

This issue is that gedit creates ~/.gnone2/ and subdirectories the first time it is run. If that happens to be with sudo gedit THE FIRST TIME - before any other gnome2 program is run as the userid, then those directories are owned by root. The userid doesn't have create permissions, so no other gnome2 programs that need to write or create settings will work.  So ... running 
gedit - 1st run as normal user.
sudo gedit - 2nd run as root
will solve this issue. Assuming gedit is mandatory as the selected editor.  After this is done once - that's it - at least for that single userid. If any new sudo-capable userids are created, those would need to run gedit to create the ~/.gnome2/ dirctories there too.

Steps to reproduce the issue:
[LIST=1]
[*]Create a new account (or just use the first one post-install w/ nothing in ~/ yet )
[*]Make it sudoable (add to the sudo/wheel/admin) group - I'd have to check which.
[*]Login with that account
[*]Before doing anything else, run **sudo gedit**
[*]Try to launch different applications - see which fail to start.
[*]Check the permissions on ~/.gnome* - owned by root?
[/LIST]

This isn't anything about the specific editor. It is about programs crashing because the directory where settings should be stored isn't writable after sudo {some gui program} is used too early in the new-userid's life.  It isn't every GUI program, just some.  I suppose some CLI programs might create directories and setting files too - just don't see it as much.  Seems like a GUI issue to me.

---

### Post by sudodus on 2015-03-19
Thanks for explaining, ***TheFu*** :KS

---

### Post by DuckHook on 2015-03-19
Perhaps it's my fault for not being clear enough... I'm not entirely disagreeing with you. In fact, I agree 100% with your assessment of the problem and the severity of its consequences.

However (without going to the trouble of highlighting the actual quotes), as a solution, many posters suggested restricting config file edits to nano. My point&#8213;and this is where we diverge&#8213;is that nano is not a real-world solution. Yes, it's a *technically* workable solution, but it is not a *practically* workable one. So, I'm not talking about simple editing mistakes either. Just because Linux acolytes are happy with command line tools does not mean that such tools can be generalized into solutions across the larger community. We too often lose sight of this.

This has real world implications. For example, it leads to my disagreeing with the sudoedit solution as a universal fix. In a default install of Ubuntu, sudoedit automatically invokes nano. My contention is that this will send a certain contingent of new users screaming for the hills. I get it that a broken system resulting from improperly invoking gedit with sudo will likewise send them screaming. I agree with you that this needs to be fixed. However, my point is that proposing a "fix" that drives users away, albeit for a different reason, does not constitute a real fix.

The solutions I've gleaned from this very instructive thread are as follows:

1. I would recommend sudoedit to people who are comfortable (or at least willing to try) command line tools.
2. I would recommend sudo -H gedit to those who are absolutely allergic to the command line.

While #2 is not ideal (for reasons that Lars has laid out), it gets the job done without unacceptable collateral damage.

A design consideration would be to have the system pre-generate ~/.gnome2 etc with the proper ownerships/permissions at the moment of each initial user setup. But trying to get the developers to change things is a whole 'nuther ball game and the topic for a separate thread.

---

### Post by sudodus on 2015-03-19
> **DuckHook said:**
> ...
The solutions I've gleaned from this very instructive thread are as follows:

1. I would recommend sudoedit to people who are comfortable (or at least willing to try) command line tools.
2. I would recommend sudo -H gedit to those who are absolutely allergic to the command line.

While #2 is not ideal (for reasons that Lars has laid out), it gets the job done without unacceptable collateral damage.

A design consideration would be to have the system pre-generate ~/.gnome2 etc with the proper ownerships/permissions at the moment of each initial user setup. But trying to get the developers to change things is a whole 'nuther ball game and the topic for a separate thread.

I think the developers expect us to communicate via launchpad bug reports - what about making a bug report describing [SIZE=3]**[FONT=courier new]'sudo gedit[/FONT]**[/SIZE]' as a trap for beginners and suggest this solution (to pre-generate ~/.gnome2 etc with the proper ownerships/permissions)?

---

### Post by mc4man on 2015-03-19
> **philinux said:**
> Maybe the ubuntu devs need to include the needed files so that pkexec works out the box.

There has been some bugs regarding such over time (nautilus), there is this recent one concerning gedit
(basically just pushed to 'get gnome to add', ect.
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1433657](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1433657)

As far as the mentioned ~/.gnome2 dir., that's not common to a recent Ubuntu install, don't see it here in 14.04 & don't expect to.
The most likely result in a **default 14.04 Ubuntu install **when using sudo gedit - 
creates a root owned ~/.gvfs dir.  - unfortunate but doesn't really matter as not used
creates a root owned ~/.cache/dconf dir. - same as above
takes temporary root  ownership of ~/.local/share/recently-used.xbel 

So generally not the worst thing but certainly not to be advised.
nautilus & gedit are just fine with pkexec though here preferred method for that is thru alt+F2 or a context menu option

---

### Post by TheFu on 2015-03-19
It isn't just gedit - **any GUI program** that creates application settings in files could have/cause the same issue, just with different directories.

gedit is just an easy example of the problem, but not the entire issue.  Any program that fails to work with a read-only ~/ is the real root cause, right? This is a new test scenario to be added for every GUI program on every distro.

We need to fix the root cause, not just 1 symptom from a single scenario.

Also, I don't know exactly which version of Ubuntu the initial guy was running. Sorry. He may have been running a derivative - i dunno.
Don't recognize any of the *buntu GUIs anymore. Been using a simplified openbox-only setup here for a while, so my view is warped.

I tested a similar scenario with** sudo lxterminal** -  the result inside ~/.config/: 
```
drwx------ 2 root root 4096 Mar 19 18:45 lxterminal/
```

Running lxterminal later without sudo didn't crash even if I tried changing preferences (which couldn't be saved).  Just look in your ~/.config/ directory - those are the programs of concern.

---

### Post by mc4man on 2015-03-19
> **TheFu said:**
> It isn't just gedit - **any GUI program** that creates application settings in files could have/cause the same issue, just with different directories.

gedit is just an easy example of the problem, but not the entire issue.  Any program that fails to work with a read-only ~/ is the real root cause, right? This is a new test scenario to be added for every GUI program on every distro.

We need to fix the root cause, not just 1 symptom from a single scenario.

Then maybe change your thread title...
(- as is could be taken 2 ways anyway. 
1. stop recommending sudo gedit 
2. stop sudo gedit that was used from a recommendation from running

---

### Post by TheFu on 2015-03-19
> **mc4man said:**
> Then maybe change your thread title...
(- as is could be taken 2 ways anyway. 
1. stop recommending sudo gedit 
2. stop sudo gedit that was used from a recommendation from running

I'm not an admin here - don't see how to change the title.

"Caution running GUI programs like gedit with sudo" - is what I'd call it now.

---

### Post by Elfy on 2015-03-19
I've changed it now.

But you should have been able to Edit - (then Advanced perhaps) not sure atm, then change thread title.

---

### Post by grahammechanical on 2015-03-19
I started using pkexec in Utopic but switched to sudo -H when pkexec stopped working in Vivid. This is what I get

> graham@sdb8-Roll-Dev:~$ pkexec gedit
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused


(gedit:5340): Gtk-WARNING **: cannot open display: 




which is weird because although I do have unity8-desktop-session-mir installed I am not at the moment running it. I do agree that new users are not being helped by some of the tutorials they find on the web. They usually come here after they have followed some tutorial and messed things up. And not before.

Regards.

---

### Post by DuckHook on 2015-03-19
> **TheFu said:**
> ...We need to fix the root cause, not just 1 symptom from a single scenario....the "root cause" being that Linux is designed such that system level changes are intended to be done via CLI and not via some graphical app. Therefore, trying to use a GUI app, whether gedit, nautilus, zenity, hplip-setup or anything, as root, will always involve a kludge of some sort, with greater or lesser severity of drawbacks. This is at the heart of the conundrum with using graphical apps and I truly get why you are advocating sticking with the CLI. It's the cleanest, least problematic solution&#8213;for Linux adepts.

Well, I suppose this means that we have to live with the kludges, whether it is pkexec or sudo -H or manually reinstalling a deprecated gksu (as I've done).

On a related note, for new users especially, there are times when a GUI tool is better than its CLI counterpart, and as much as I enjoy the command line, I'm forced to acknowledge this. Example: have lost count of the times some poor soul has joined this forum imploring how to recover from a horribly misjudged rm -rf. If they had instead used Nautilus and "Move to Trash", they wouldn't have ruined their day&#8213;or quite possibly their entire month.

---

### Post by mc4man on 2015-03-19
> **TheFu said:**
> I'm not an admin here - don't see how to change the title.

"Caution running GUI programs like gedit with sudo" - is what I'd call it now.
At least here I can change the Title of any thread I started by going to the 1st. (orig) post  > Edit Post > Go Advanced & simply changing the thread Title there

---

### Post by kurt18947 on 2015-03-19
Coming from a "I can copy/paste with the best of 'em" CLI user, I agree with DuckHook that novice Ubuntu users/Windows refugees are gonna freak the first time they see a Nano screen. Every bad thing they've heard about Linux is true.

---

### Post by mc4man on 2015-03-19
Ultimately it's up to a source dev or package maintainer to provide an alt. means to run gui apps as root if they feel it's useful or appropriate. So in that regard there are alot of apps using policykit, shortlist of  those I have here.
> com.canonical.controlcenter.datetime.policy           
org.freedesktop.accounts.policy
com.ubuntu.pkexec.gedit.policy  
com.ubuntu.pkexec.nautilus.policy                      
com.ubuntu.pkexec.synaptic.policy 
com.canonical.controlcenter.user-accounts.policy       
org.freedesktop.color.policy
com.canonical.indicator.sound.AccountsService.policy   
org.freedesktop.hostname1.policy
com.canonical.xdiagnose.policy                         
org.freedesktop.locale1.policy
com.hp.hplip.policy                                    
org.freedesktop.login1.policy
com.ubuntu.apport.policy                               
org.freedesktop.NetworkManager.policy
com.ubuntu.languageselector.policy                     
org.freedesktop.policykit.pkexec.run-plainbox-job.policy                     
org.freedesktop.RealtimeKit1.policy
com.ubuntu.pkexec.synaptic.policy                      
org.freedesktop.timedate1.policy
com.ubuntu.release-upgrader.policy                    
org.freedesktop.udisks2.policy
com.ubuntu.softwareproperties.policy                  
org.freedesktop.udisks.policy
com.ubuntu.systemservice.policy                        
org.freedesktop.upower.policy
com.ubuntu-tweak.daemon.policy                        
org.freedesktop.upower.qos.policy
com.ubuntu.unity-settings-daemon.plugins.power.policy  
org.gnome.controlcenter.datetime.policy
com.ubuntu.unity-settings-daemon.plugins.wacom.policy  
org.gnome.controlcenter.user-accounts.policy
com.ubuntu.update-notifier.policy                      
org.gnome.gconf.defaults.policy
com.ubuntu.usbcreator.policy                           
org.gnome.gnome-system-monitor.policy
com.ubuntu.whoopsiepreferences.policy                  
org.gnome.settings-daemon.plugins.power.policy
org.debian.apt.policy                                  
org.gnome.settings-daemon.plugins.wacom.policy
org.debian.aptxapianindex.policy                       
org.opensuse.cupspkhelper.mechanism.policy
org.debian.pkexec.gnome-system-log.policy
org.freedesktop.policykit.policy

So that's where it should be addressed if a source could benefit but doesn't have policykit enabled. In the case of nautilus & gedit the gnome dev's have stated they don't support their use as root (any method),  so odds aren't great for them to add unless there is a change of heart there.
As far as advising other users that could depend on the context of what's to be done & who is doing it.

---

### Post by Morbius1 on 2015-03-20
I'm afraid you are probably correct.

It's sad really since gksu put the responsibility on it rather than adding anything to the Linux Registry at the application level. Of course gksu at least at the moment still works.

In case anyone is interested in some background on this thing you might find this old Gnome ( and it's Gnome not Ubuntu ) bug report entertaining: [https://bugzilla.gnome.org/show_bug.cgi?id=654184](https://bugzilla.gnome.org/show_bug.cgi?id=654184)

Selective quotes just to be irritating:
> You shouldn't run nautilus as root. Whats _[COLOR=#0000cd]probably[/COLOR]_ happening here is that not only is
nautilus getting started, but also a session bus for root, and diverse session 
services, etc etc.
Probably? You don't know?
> Average users could switch the user and log in as root if tutorials recommend using GUI
apps like Nautilus (not-advanced users I'd say) for something,
The PCLinuxOS ( " We don't need no stinkin' sudo here" ) approach. Problem solved.

---

