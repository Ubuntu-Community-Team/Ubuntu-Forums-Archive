---
title: "Better uninstall feature"
date: 2008-04-11
forum: Ubuntu Brainstorm
---

### Post by Holonet on 2008-04-11
Obviously I don't mean this for Hardy, but the sooner the better, in my opinion.

I think we need an install logging feature, including one (or at least the *option*) for compiling from source.  In short, the purpose being to allow for completely uninstalling any program, whether compiled from source or installed via a package.  As of now, there is a misleading "completely remove" in synaptic, which does not do the job.  There are still hidden files in the home folder for some programs, traces left in other directories, etc...  You have to be pretty savvy to do a clean job removing something so that the condition of the system is the same as before it's installation.  Wine is especially wanting in this area.  I have had situations where I manually removed the traces I could find of Wine as well as other programs, and then when I reinstalled them, they did not appear in the Applications menu as they did the first time they were installed.

The short version of all this is that these issues are very similar (though not as bad) to issues in Windows.  I have reinstalled Ubuntu a number of times and just deleted all the hidden stuff in the home folder (the only way I know to do a completely clean install while putting /home on a separate partition), and noticed a speed increase because of said reinstall.  This is essentially the same mess we have to deal with with the Windows registry getting clogged, only in different form.

I apologize if this is partly because of my ignorance, but I do know computers more than the average Joe, and I believe facilitating this issue would be one of a few large improvements toward getting Windows users to see this OS as all-around better.

---

### Post by kidders on 2008-04-12
Hi there,

> **Holonet said:**
> I think we need an install logging feature, including one (or at least the *option*) for compiling from source.Both of these are already available. Ubuntu's package manager logs everything it does to /var/log (at least on *my* box!), and can also build apps from source.

> **Holonet said:**
> there is a misleading "completely remove" in synapticMost package managers never remove files they didn't create, or that don't exist in the form they created them in. My guess is that if the Ubuntu gods modified theirs to start rooting around in peoples' home directories for things it might like to erase, they would receive millions of complaints within minutes of even *suggesting* it.

Imagine, for instance, that despite the fact that I'd never used KDE on a particular Linux box, my home directory happened to contain a directory called ".kde". It would obviously be completely inappropriate for a package manager to delete it, simply because the Linux box's administrator decided to uninstall KDE.

Similarly, removing files from /etc, /var/log and other places when an application is being uninstalled would be considered outrageous by most Linux users.

Consider /home for example. Imagine an application you'd never heard of (and have no intention of ever using) creates a file on your desktop called "X" when it runs. That would create the potential for any user with an "X" on his desktop to wake up one morning and discover it had vanished, courtesy of someone trying out a few new applications they later decide to do a "complete" uninstall of. Multiplied up thousands of times, for every Linux application ever to be invented, there would be a massive list of similarly unpredictable "reserved" filenames, scattered throughout peoples' filesystems.

I mentioned /var for similar reasons. If I install MySQL, the last thing I expect (even if I explicitly request a _complete_ uninstall) is for my databases to vanish when I remove the application. Likewise, people take it as read that /var/log contains a complete record of activity since time immemorial ... unless of course they intentionally remove something. If the package manager could poke gaps & create inconsistencies, it would make log-keeping pointless.

Anyhow, I hope that helps. The idea of complete removal isn't misleading ... but it does get misunderstood, from time to time.

---

### Post by chrisccoulson on 2008-04-12
I definately wouldn't want *any* package manager removing files / folders that it didn't create from my home directory

---

### Post by Holonet on 2008-04-13
Hmm, good points indeed, but another misleading thing was my thread title hehe.  I still think something needs to be fixed here...just now I'm not sure who to blame, i.e. Ubuntu or its software.  My programming knowledge is limited to mostly conceptual at best, so I'm extrapolating here--that said:

I'm not entirely convinced the complete removal works.  Like my example with wine...  I uninstall it, remove the .wine directory myself, delete the menu in Applications...basically because the installation was corrupt and I was having unwarranted issues.  I then reinstalled it, and the menu did not reappear, plus I had a few weird configuration bugs like not detecting my DVD drive.  This has nothing to do with the need to remove the programs under wine or settings and files created (I feel I should have been able to leave the .wine directory and accomplish the goal).  Something definitely went wrong there.

Now perhaps the fault is more in wine and/or other programs, which store settings that can affect stability & functions in the /home folder.  At this point, I admit I'm getting a bit confused, but I feel the bottom line is that *something* needs to be done about the fact that however its doing it, Ubuntu is emulating the Windows behavior of getting bogged down and requiring reinstallation, or to be more accurate, file surgery beyond the simple--especially for someone used to Windows.

Like I said, perhaps it's the software more...  Part of the problem is, as someone relatively new to Linux, I don't even *know* where all the files relevant to any particular program go.  /bin, /share, /home/.hiddenthisandthat, etc...  I understand this facilitates things like running any command at the terminal without sifting through directories.  But to me, it also equates to hunting down registry entries and as such, really annoying.  I guess I don't have a complete enough understanding of just what Ubuntu is doing here to propose a cogent solution...but I do still think there's room for action on the subject.

---

### Post by smartboyathome on 2008-04-13
This could be better solved by the Gobolinux filesystem when it matures, since all programs go to one directory, but as it stands apt-get needs some hacks to get it to read the logs a program makes which would tell it which files it created after it was installed. The latter could run into the problem of it deleting items you created with it, not just its system files, and in the case of wine, it could run the risk of deleting your whole home directory, since it has a symlink to it.

---

### Post by Holonet on 2008-04-13
> **smartboyathome said:**
> This could be better solved by the Gobolinux filesystem when it matures, since all programs go to one directory, but as it stands apt-get needs some hacks to get it to read the logs a program makes which would tell it which files it created after it was installed. The latter could run into the problem of it deleting items you created with it, not just its system files, and in the case of wine, it could run the risk of deleting your whole home directory, since it has a symlink to it.

I realize that from the previous poster above, but it doesn't explain why the menus act up the way they did.  In addition, I've had icons disappear on me...Recently I installed audacity from synaptic, then discovered it was missing a few features.  I compiled it from source, intending to overwrite the original installation, which it did, and the icon disappeared.  I had to add it back by manually downloading it to the /usr/share/pixmaps directory.  All these weird little happenings, I've seen surrounding the process of installing and uninstalling programs.

I see now that the solution is probably not in removing all files created by the programs, but that does leave the potential for a machine getting bogged down as mine has.  That aside, the other problem I mentioned seems more glaring.  Several times, I've reinstalled a program every which way I can think of, and not gotten a clean functioning program which I had previously upon the first install.  Another example I can cite is fluidsynth/qsynth.  I tried updating qsynth to the present version by compiling from source, but something's up with that version.  It didn't detect alsa, and was a big bug I won't go into for time's sake here.  But I tried removing it...purging, etc...and reinstalled the original version from Synaptic...and the problem still remained...  I'm trying not to turn this into a troubleshooting thread, but I feel there's something in Ubuntu that needs to be addressed here.

I'm not familiar with the gobolinux system, would that also be part of this problem?

---

### Post by smartboyathome on 2008-04-13
The audacity problem is probably because the new .desktop file Audacity created didn't include a link to the icon. The second problem is an apt problem. That is why it wasn't supported, and isn't recommended to install debs from outside the repositories.

The gobolinux system changes the directory structure. It would create a /Programs directory which would hold all the program files in a specific folder, eliminating the problem package managers have now with not detecting programs installed from source (it can just remove the file like any other by removing the folder).

---

### Post by Holonet on 2008-04-13
Hmm, well that does sound like it would help the issue, however I'm a little nervous about the fact that with both the Audacity and wine problems stick around even after reinstallation.  If the Audacity icon was a link problem, then it must have stored it in a different directory, because it wasn't in the /usr/share/pixmaps at all.  Plus, like I said, reinstalling the Synaptic-supported version did not remedy the issue.

I guess it's fine if this would all be addressed by the gobolinux system.  Maybe it's just the fact that I didn't find certain files.

---

