---
title: "[IDEA] Automatic password request for system file editing or moving"
date: 2007-04-15
forum: Ubuntu Brainstorm
---

### Post by goethe on 2007-04-15
When the user is trying to do something only the root is allowed to (e.g. editing a configuration file), it would be fine if ubuntu automatically asked for the root-password instead of showing an error message.

---

### Post by viciouslime on 2007-04-15
Editing a configuration file wouldn't show an error, it would just open it as read-only. This is a good thing as you might only want to view the file and so don't have to risk opening ti with root privileges.

---

### Post by aysiu on 2007-04-15
**There are two parts to this:**

1. _Gedit_ (or other text editor): If you are an *admin* user and try to save a system file, you should be allowed the option to save it with a nice little *gksudo* authentication... or to just close it without saving, of course.

2. _Nautilus_ (or other file browser): If you're an *admin* user and try to move or copy a file to a system folder, rather than getting an error that you're not allowed to move or copy the file, you should get a *gksudo* authentication to perform the action... or to cancel the action.

**@goethe,** I've retitled your thread to be a bit more descriptive. Can you edit your post and formalize the specification in accordance with [the guidelines PriceChild has laid out?](http://ubuntuforums.org/showthread.php?t=409519)

**History of this request**:
Someone started a thread on this topic in September, 2006 entitled [Super User Prompt for Nautilus, Good Feature Or No?](http://ubuntuforums.org/showthread.php?t=409519) (don't know why it's in the Backyard)

There is also a bug in Launchpad about it. It's labeled a wishlist item right now.
[https://bugs.launchpad.net/nautilus/+bug/12154](https://bugs.launchpad.net/nautilus/+bug/12154)

---

### Post by viciouslime on 2007-04-15
Ah ok, I get it now. Still not sure though, makes it sound a bit like vista, I think lots of people would just enter their password and do whatever it was without thinking and could cause quite some damage. Though at the same time it could be very convenient... hmmm

---

### Post by aysiu on 2007-04-15
If you make something really inconvenient, though, then you get those people who are just turned off by the whole thing and decide they want to enable a graphical root login and just use that instead of doing things the proper *sudo* or *gksudo* way.

I've seen it many times. The angry (yes, really--*angry*) new users who say, "What the &$##!? This is my computer? Why don't I have the right to do ____? How do I just log in as root?"

If people are going to be dumb and just click "okay" to anything, they're going to screw up their system eventually anyway. That can't be helped. And the idea is that they actually have to authenticate with a password (as you would normally do with *gksudo nautilus*), not just click a button.

---

### Post by =0verlord= on 2007-04-15
Regarding gedit, there have been plenty of times where I don't notice that I'm editing read-only and get the rejection dialogue when I go to save.  It happens in vim too, and is never fun.  Really, I don't know about automatic password requests - maybe an additonal item on the save dialogue and on the file menu.  "Save as other user" maybe?  While this could be implemented for Ubuntu, taking it up with the respective editor packages is also a good idea.

With nautilus, I'm actually on the fence.  I don't do any admin work from a file manager window, and whenever I come across a file that's not under my current user I drop to the CLI.  Whether the benefits outweigh the (previously noted) risks I have no idea and since it's already in the nautilus/gnome system I'm just going to sit back and watch.

---

### Post by salsafyren on 2007-04-15
Wouldn't it be easier to be able to right click "Run as root"?

Then gedit wouldn't have know anything about gksudo.

---

### Post by aysiu on 2007-04-15
> **salsafyren said:**
> Wouldn't it be easier to be able to right click "Run as root"?

Then gedit wouldn't have know anything about gksudo.
Even that right now requires some tweaking or a Nautilus script.

I'm not 100% sure, but I think that's available in Kubuntu by default. If not, it's a Konqueror plugin that can be installed.

The problem is really with new users, though. I mean, if you're going to learn workarounds, you might as well create a launcher for ```
gksudo nautilus
``` which many people do. But if a new users drags an extracted theme to /usr/share/themes and gets an error message saying she's not allowed to perform that action, it just confuses the user. It's not "running as root" or "launching as root." That won't solve the problem. The error message is unhelpful--that's the real issue. And it frustrates and confuses a lot of new users who think, "How could I not have permission to move that file? I'm the only one on this computer!"

---

### Post by salsafyren on 2007-04-15
Ok, I see the point now.

However, this should be optional, since hard core nix people probably wouldn't like it (they would probably just use the terminal).

---

### Post by aysiu on 2007-04-15
I'm just saying that it should allow you to authenticate or cancel... or at least give a more helpful error message.

Instead of saying > You don't have permission it could say something like > You're operating the file browser as a user now, so you will not be able to modify system folders or files. If you want to use the file browser to modify system folders, please launch it with *gksudo nautilus* instead Alternatively, it could say (if you're an admin user) > You are about to modify a system folder or file. Are you sure you want to do this? *Modify*, *Don't modify* If you click *modify*, you'll be prompted for your password, and *sudo* will be invoked in the background to temporarily elevate your privileges.

---

### Post by BungaMan on 2007-04-17
Often I'm editing xorg.conf for tweaking, deleting logs because I want to start with a fresh list... doing file manipulation that requires admin rights basically.

In Nautilus it would be nice to have an option that under "open" says "open with administrative rights" or "open as admin", something clearly understandable like that.  Otherwise you have to go to cli and do gksudo gedit filetomanipulate or sudo vi something or sudo rm whatever.  I know the cli but I don't want to be forced to go there.  And I don't want to start a nautilus window with administrative rights either (too dangerous for mistakes).  Being in one application that can open files but then still have to go to an other application to open that same file with sufficient permissions is an annoyance.  I also don't see the fun in making shortcuts "like gksudo gedit", then I still have to browse for the file.

---

### Post by 23meg on 2007-04-17
[Here]("http://ubuntuforums.org/showthread.php?t=409852") is a very similar thread; a merge is in order. Please do a search before posting an idea thread.

---

### Post by BungaMan on 2007-04-17
You can close this thread, I'm adding my post to the other thread

---

### Post by BungaMan on 2007-04-17
Quoting my post in an other thread:
> Often I'm editing xorg.conf for tweaking, deleting logs because I want to start with a fresh list... doing file manipulation that requires admin rights basically.

In Nautilus it would be nice to have an option that under "open" says "open with administrative rights" or "open as admin", something clearly understandable like that. Otherwise you have to go to cli and do gksudo gedit filetomanipulate or sudo vi something or sudo rm whatever. I know the cli but I don't want to be forced to go there. And I don't want to start a nautilus window with administrative rights either (too dangerous for mistakes). Being in one application that can open files but then still have to go to an other application to open that same file with sufficient permissions is an annoyance. I also don't see the fun in making shortcuts "like gksudo gedit", then I still have to browse for the file.
What it comes down to is simple to implement.
Rightclick on a file and below the "Open" command you have an option "Open as admin".  No need for any fancy message display.  KISS!
All that is needed for integration is the same command but with gksudo in front of it!

---

### Post by orb9220 on 2007-04-17
For me I have a launcher on panel that launches a gksudo nautilus.

Which is the only file browser I use for the simply fact I do not want to remember if I have the rights or not.

Yes it can be dangerous but, I have never had a problem with it. And I always backup system critical files (xorg,fstab,etc..) and save them to a seprate HD to later restore If need be.

---

### Post by amano on 2007-04-17
I second this idea. It annoys the hell out of me to edit a file and noticing afterwards that it is a system one which cannot be saved. There should be an option in the gedit menu that is called "Save as root..." which calls gksudo.

---

### Post by r3m0t on 2007-04-17
> **BungaMan said:**
> Quoting my post in an other thread:

What it comes down to is simple to implement.
Rightclick on a file and below the "Open" command you have an option "Open as admin".  No need for any fancy message display.  KISS!
All that is needed for integration is the same command but with gksudo in front of it!

1) Why do I have to decide before I look inside the file, whether I will need to open it as an admin?

2) There are two options: always show "Open as admin", or show "Open as admin" only when the user doesn't have write privileges (and needs to use sudo). If you do the first, then sometimes the option is redundant (and hence confusing). If you do the second, the muscle memory of the right-click menu will be gone (i.e. should my arm move my mouse three or four spaces down?) and people will wonder why "Open as admin" appears only occasionally.

---

### Post by BungaMan on 2007-04-18
> **r3m0t said:**
> 1) Why do I have to decide before I look inside the file, whether I will need to open it as an admin?
To prevent stupidity.  Default to "Open" for everybody and if you want to do more than just read then you are probably an advanced user and should consciously select to open it as admin.  If you are not an advanced user and decide to manipulate the file (delete, edit) then you should be made conscious that it is an important file.

> **r3m0t said:**
> 2) There are two options: always show "Open as admin", or show "Open as admin" only when the user doesn't have write privileges (and needs to use sudo). If you do the first, then sometimes the option is redundant (and hence confusing). If you do the second, the muscle memory of the right-click menu will be gone (i.e. should my arm move my mouse three or four spaces down?) and people will wonder why "Open as admin" appears only occasionally.
Nautilus of course only has to show "Open as admin" when you are not the owner.  You make it sound as a problem that people would think about why the option is there and somethimes not.  If that teaches them the basics between regular user and administrative tasks then that's even better!  It's an essential part of working with linux.  And I doubt that "muscle memory" is an argument here.  A file opens with double click by default, you only go to the right click menu to do something besides that default task.

---

### Post by simplyw00x on 2007-04-18
This is already possible, and imo shouldn't be a default.
```
vim () {
    for i in "$@" ; do
        if [ -f "$i" -a ! -w "$i" ] ; then precommand="sudo " ; break ; fi
    done

    ${precommand}/usr/bin/vim "$@"
}
```
Just adapt that for your favourite programs, and if you want to use it on the desktop as well, move /usr/bin/gedit to something else and make a /usr/bin/gedit with similar functionality to the snippet above.

---

### Post by BungaMan on 2007-04-18
Yes, a lot of the suggestions can be done but we're talking about improving the default setup of ubuntu.  You can script almost anything but not all ubuntu users can, even assuming they know what a script is.

---

### Post by simplyw00x on 2007-04-18
Yes but my point is that there is no-one who would benefit from this being the default - think about it.

**New users/non-tech users**
Shouldn't be editing config files. If they are, there will be someone telling them how, hence the intructor/mentor can also tell them how to open the file as root.

**Users who need to edit config files a lot**
...can follow instructions, and work it out, and do it themselves.

---

### Post by aysiu on 2007-04-18
> **simplyw00x said:**
> 
**Users who need to edit config files a lot**
...can follow instructions, and work it out, and do it themselves. No. They can't. That's why this is an issue. Read the Absolute Beginner forums if you don't believe me.

And saying you don't have permission to move a file (when you do) is just vague and erroneous feedback. If you try to move a file to a system location and you are part of the *admin* group, you should be able to do this provided you authenticate with your password. Don't play games with the end-user (*you didn't say the magic word*). The system should be working with the user, not against the user.

I don't see what the harm in > You're moving/copying a file to a system folder that affects all users. Are you sure you want to do this?" is. If the person sees that warning, still wants to continue, and then enters her *sudo* password, how is that any different from "following instructions"? And if the person sees the warning and decides not to continue, she'll have that option, too. Why is that bad?

Of course, sometimes people run into that problem because the documentation is poorly written (in which case, we can improve the documentation), but other times it's because the documentation is not for Ubuntu. Other distros use root instead of *sudo*. And some documentation is outside our control. If some theme needs to be extracted to /usr/share/themes in order to be installed for all users, the theme README file isn't going to say > And if you're using Ubuntu, remember to press Alt-F2 and type ```
gksudo nautilus
``` to launch Nautilus as root Here are a couple examples of frustrated/confused users who don't fit into either of your categories:
[http://ubuntuforums.org/showthread.php?t=315177](http://ubuntuforums.org/showthread.php?t=315177)
[http://ubuntuforums.org/showthread.php?p=2089998#post2089998](http://ubuntuforums.org/showthread.php?p=2089998#post2089998)

---

### Post by Nicks Spleen on 2007-04-19
I think it is a good idea. I know I forget plenty of times to open something with sudo only to get told I can't save it after I had make all my changes. Its just annoying to have to open up the cli and gksuo nautilus.

I would have an option in nautilus to allow the "Open as root" dialog on the right click or "Save as root" ability. Make this option unchecked by default and put a nice little warning message about enabling it. I think that would prevent a lot of people from enabling if they don't know what it is.

---

### Post by desperado666 on 2007-04-19
> **simplyw00x said:**
> This is already possible, and imo shouldn't be a default.
```
vim () {
    for i in "$@" ; do
        if [ -f "$i" -a ! -w "$i" ] ; then precommand="sudo " ; break ; fi
    done

    ${precommand}/usr/bin/vim "$@"
}
```
Just adapt that for your favourite programs, and if you want to use it on the desktop as well, move /usr/bin/gedit to something else and make a /usr/bin/gedit with similar functionality to the snippet above.

Please make a howto i would really appreciate that.

---

### Post by iKs on 2007-04-19
+1

Having an Open as root & a Save as root is a great idea.

---

### Post by simplyw00x on 2007-04-19
> No. They can't. That's why this is an issue. Read the Absolute Beginner forums if you don't believe me.
I'm sorry, we seem to have wires crossed. I'm under the impession that 'Absolute Beginners' are *precisely* the people who **shouldn't** be editing vital config files. If they need to at all, this should be under heavy guidance that would tell them the (simple) process of editing these files. 

The response to one of those linked threads you mentioned:
> LOL welcome to Ubuntu. This is done for security reasons. Linux != windows.
Damn straight. 

> You're moving/copying a file to a system folder that affects all users. Are you sure you want to do this?"
Users are always sure. [http://ubuntuforums.org/showthread.php?t=315177](http://ubuntuforums.org/showthread.php?t=315177) wants to be able to freely move about every file on his hard drive. Users don't self-medicate their changes to the system. It'll just annoy people who think they should be able to edit these files without 'that annoying prompt' and screw-over those users who have no idea what they're doing, but assume that as long as they **can** do something, it's ok to do that.

> I would have an option in nautilus to allow the "Open as root" dialog on the right click or "Save as root" ability.
A better idea. But still slightly redundant... if you edit your config files *that* much, you're not really Ubuntu's 'target user' any more.

---

### Post by aysiu on 2007-04-19
> **simplyw00x said:**
> 
Users are always sure. No, they're not. People accidentally move, delete, rename files all the time. That's why confirmations exist (for example, when you try to empty the trash). > if you edit your config files *that* much, you're not really Ubuntu's 'target user' any more. Considering almost all Ubuntu users install and configure their own systems, you'd be hard-pressed to find a "target user" who hasn't edited her own config files.

In any case, you're missing the point. The error saying you can't edit such-and-such file because you don't have permission isn't correct (well, it is from a system perspective, but not from a user one). The user does have permission but needs to invoke a temporary escalation of privileges with a password authentication.

Imagine if you went to System > Administration > Synaptic Package Manager and instead of getting an authentication dialogue, you got "You don't have permission to install programs." That'd be silly. And that's exactly the kind of implementation we have with Nautilus and system files right now--silly.

Users who don't need to edit system files wouldn't be involved in this proposal anyway. The ability to escalate privileges would apply to only those in the *admin* group. If a user is truly an end-user and not a system administrator, she would get the regular "you don't have permission" error.

---

### Post by simplyw00x on 2007-04-19
> No, they're not. People accidentally move, delete, rename files all the time. That's why confirmations exist (for example, when you try to empty the trash).
I've done this too, using command-line tools, and graphical ones, and can safely say that the mechanical process of hammeing 'ok' that develops all-too-quickly has prevented nothing in graphical terms.

> Considering almost all Ubuntu users install and configure their own systems, you'd be hard-pressed to find a "target user" who hasn't edited her own config files.
You'd be hard-pressed to find one that edits their own config files sufficiently frequently, and with sufficient independence, to need the requested 'feature'.

> The error saying you can't edit such-and-such file because you don't have permission isn't correct (well, it is from a system perspective, but not from a user one).
From a user perspective, I don't think I should own files that relate to the safe running of the system. This is a paradigm problem, not a software one. People need to stop thinking that they know best. Sure, change the dialog to be more 'correct' as the user sees it, but there need to be more levels between selecting /boot/grub/menu.lst and pressing 'delete' and your grub being hosed.

> The ability to escalate privileges would apply to only those in the admin group. 
And which users wouldn't place themselves in this group? By default all Ubuntu users are 'admin', and anything different is like expecting people to choose 'limited' accounts on windows XP.

---

### Post by aysiu on 2007-04-19
> **simplyw00x said:**
> I've done this too, using command-line tools, and graphical ones, and can safely say that the mechanical process of hammeing 'ok' that develops all-too-quickly has prevented nothing in graphical terms. That's why you would get a password authentication instead of just "hammering 'ok.'"

> You'd be hard-pressed to find one that edits their own config files sufficiently frequently, and with sufficient independence, to need the requested 'feature'. If you have to edit your own config files even once, I'd say the feature's worth it. A "permission denied" error gives no helpful information to the user and serves only to frustrate instead of educate.

At least changing the error message to say, > System files are critical to the proper functioning of your computer. If you are sure you want to edit system files, press Alt-F2 and type ```
gksudo nautilus
``` At least this *educates* users.

Mandating that users get frustrated and have to get help on the forums in order to move a system file is ridiculous. What is this--hazing?

> From a user perspective, I don't think I should own files that relate to the safe running of the system. I'm not talking about a change of ownership. I'm talking about invoking *sudo* when it appears to be what the user wants. What ends up happening when you frustrate the user enough is she demands to have a root login and then just logs and uses root all the time.

> Sure, change the dialog to be more 'correct' as the user sees it, but there need to be more levels between selecting /boot/grub/menu.lst and pressing 'delete' and your grub being hosed. And yet even with your great "permission denied" dialogue (which offers no helpful information), new users still manage to hose their systems and delete Grub entries.

> And which users wouldn't place themselves in this group? By default all Ubuntu users are 'admin', and anything different is like expecting people to choose 'limited' accounts on windows XP. Only the first user defaults to being in *admin*. Every new user created after that has to be manually added to the *admin* group.

---

### Post by simplyw00x on 2007-04-19
> That's why you would get a password authentication instead of just "hammering 'ok.'"
Unless you'd recently made a change and the password was cached.

> If you have to edit your own config files even once, I'd say the feature's worth it. A "permission denied" error gives no helpful information to the user and serves only to frustrate instead of educate.
I agree; change the error message to be more informative. Though I'm still not sure one should be letting users loose on a root-priviledged nautilus without instruction or guidance.

> And yet even with your great "permission denied" dialogue (which offers no helpful information), new users still manage to hose their systems and delete Grub entries.
Yup. Users also sometimes delete important documents, or even *all* their documents. But Ubuntu doesn't go out of its way to encourage this, which is what declaring open-season on /etc and /boot would do.

> Only the first user defaults to being in admin
The first user per computer, sure. But that's still a lot of users, as was my point.

---

### Post by | MM | on 2007-04-19
I also think this is a good idea.  We more or less trust 'admins' to install *anything* these-days with the easy package installer... why not trust them to edit read-only config files?

Although it should come with a warning;

[SIZE="3"]'Please consider with care: This is a system critical file.  If you do not fully understand the ramifications of your changes it is recommended that you ***do not*** continue.'[/SIZE]

Have a little countdown from 5 before the user can click continue, like what firefox has in its add-ons manager.

---

### Post by simplyw00x on 2007-04-19
> Have a little countdown from 5 before the user can click continue
This part I like.

> If you do not fully understand the ramifications of your changes]
This part I do not. *I* don't *fully* understand what I'm doing. Other people who know the same as me might think they do. People who know almost nothing might think they understand what they're doing. I occasionally think I kno what I'm doing, when I don't.

---

### Post by aysiu on 2007-04-19
> **simplyw00x said:**
> Unless you'd recently made a change and the password was cached. Well, seeing as how I've never been a fan of the *sudo* timeout, I have to agree with you there.

> I agree; change the error message to be more informative. Though I'm still not sure one should be letting users loose on a root-priviledged nautilus without instruction or guidance. What instructions? What guidance? While right now it's usually necessary for new users to go to the forums and other online documentation to get some basic functioning after an installation, this isn't what should be happening. What better guidance than the dialogue? Why not just educate them on the spot? I've seen some pretty crappy advice given on these forums all the time. I'd trust the developers' guidance over some random person on the forum saying, "Why don't you log in as root?" or "Just use *sudo kate*."

> Yup. Users also sometimes delete important documents, or even *all* their documents. But Ubuntu doesn't go out of its way to encourage this, which is what declaring open-season on /etc and /boot would do. This isn't "open season." We're talking about a warning, a confirmation, and a password authentication (with the *sudo* timeout exception noted above)

> 
The first user per computer, sure. But that's still a lot of users, as was my point. No, that wasn't really. The whole point we were discussing was "if you aren't an admin, you shouldn't be editing those files anyway." My point was that some users (apart from the one installing and configuring the system) could be non-admin users. You then went on to say that all users default to being in the *admin* group.

This is the real deal here.

A) Jill installs and configures Ubuntu. She is the only user on the machine. She needs to edit system files. Even with guidance, she may not know what the hell she's doing. She will probably screw up her system even with guidance (I've seen it happen in many a thread--there's only so much you can do to help someone if you're not looking directly over her shoulder). A password authentication, a confirmation, and an educational warning are pretty damn good for her as opposed to a "you can't do that" error, which just serves to frustrate her. I mean, even if I buy your "she needs guidance" line, the current error doesn't even do that much. It doesn't say, "You could do that, but we're not letting you. Get some guidance before you edit system files." It just says you can't do that. Lame.

B) Phillipa installs and configures Ubuntu. Her family also uses it, but they are not very computer-savvy. Phillipa edits system files all the time. Why should she have to remember to right-click or use *gksudo nautilus* when a simple three-tier process (confirmation, authentication, warning) that's part of her workflow already could let her edit those system files? No one in her family can get that three-tier process, since they are not in the *admin* group.

A well-designed system should allow you to use it without constantly having to refer to outside documentation. Yes, there may be sometimes, especially if you're trying to do a relatively obscure task, when you may need to refer to outside documentation, but this isn't supposed to be Gentoo here.

---

### Post by simplyw00x on 2007-04-19
> What instructions? What guidance?
The same instructions, the same guidance telling the user to edit these files in the first place. People editing files on intuition and guesswork are not a recipe for success.

> This isn't "open season." We're talking about a warning, a confirmation, and a password authentication (with the sudo timeout exception noted above)
We're talking about bringing a potentially dangerous task into the specturm of lowest-common-denominator users' ability, when it is far outside these users' ability to edit, even to understand, these files.

> My point was that some users (apart from the one installing and configuring the system) could be non-admin users.
And my point was that the group of users classified 'admin' simply by being first user on the computer rather than 'admin' skill, or users on single-user systems (and hence admin by default) is huge. The number of non-admin-class users using Ubuntu in a home environment is negligible.

> the current error doesn't even do that much
And I'll yet again heartily endorse changing the wording of the error message.

> educational warning
Saying what? Saying 'unless you're in the context of a tutorial, you shouldn't be doing this! Go away!'? Because that's the content, if not the tone, of what they should be told.

> Phillipa installs and configures Ubuntu... Why should she have to remember to right-click or use gksudo nautilus...?
Because someone who has installed and configured ubuntu themselves should be sufficiently tech-aware to know how to edit system files.

---

### Post by BungaMan on 2007-04-20
A lengthy discussion while it's soo simpel...
Working with Nautilus is _exactly_ (in terms of file manipulation) the same as working on the command line.  If you want to work with root owned files in the cli, you just put sudo in front of the command.  In Nautilus ... there is no such option.  

You'd have to start a second Nautilus as an admin, in the same way as you would start a terminal as an admin.  Of course this is not preferred bBecause then all files that you create in your home directory will become owned by root and you have free access to all the files disregarding any permissions set on it.

So all that is needed is a way to replicate this possibility.

This has no relevance to beginners, advanced or die-hard users.  If priveledges are needed then Nautilus should ask for it by showing the password prompt.  The same way as it is done in Synaptics.  It doesn't get any simpler and doesn't need, what seems to be, a philosophical discussion.  Be a bit more pragmatic!

---

### Post by ButteBlues on 2007-10-21
Without spending too much time focusing on other, more minor details, PolicyKit and PackageKit are two libraries that offer extremely well-designed control from an administrative perspective, as well as offer a distribution and desktop-agnostic abstraction layer to interact with all of the major package management systems.

Other distributions, like openSuse and Fedora are already integrating or are planning to integrate these two items as high priority because they are well-designed for their purpose, and fill a niche that was cludgey before at best.

Ubuntu should work with PackageKit to help finalize the apt backend, and then focus on adding it and PolicyKit to Ubuntu.

---

### Post by amano on 2007-10-23
**Summary: **
Add a sudo dialog to nautilus, fileroller and gedit error messages

**Scope and Use cases:**
Arad edits a system file for half an hour, but then cannot save it.
Amadäus wants to copy a file, but nautilus doesn't let him do it.
Irmi wants to extract a file from an archive, to  /usr/, but just an error pops up. 

**Rationale:**
Actions that require superuser powers are hard to be done currently in the GUI. E.g. for editing a system file, gedit doesn't warn you. It lets you edit the file, but then  not save it. You would have to save the file to a temporary other location, open gedit in the console with "gksu gedit", open the file in the temporary location and then save the file to the intended one. This should be improved. 

**Implementation Plan:**
 One solution would be to add a "sudo" button to the superuser rights related error diaolgs, or replace them with something more interactive. This should cover nautilus errors, fileroller errors and gedit errors - and possibly errors from other GNOME applications that I am not be thinking of at the moment.

---

### Post by altonbr on 2007-10-23
I completely agree. Only more advanced users how how to use 'sudo' and 'gksudo' to edit certain files (all from the command line I might add).

We need to step away from the command line by default, but still allow power users their beautiful black and white screen.

---

### Post by gnomeuser on 2007-10-23
I'm 100% behind this, I use PackageKit on my Fedora box and it's a really nice interface - it would greatly benefit the average user if the same tools were used on all distros for simple tasks like system updates.

---

### Post by Bou on 2007-10-23
I would give this a thumbs up.

---

### Post by aamukahvi on 2007-10-24
Me too. Now if only someone would write up a spec and drive it.

---

### Post by amano on 2007-10-24
And don't forget that this can be annoying for advanced users as well: You probably don't have memorized the rights for every single text file on your harddisk. After editing the file with gEdit and then realizing that it cannot be saved without superuser rights can be annyoing even for the experienced user, I guess.

---

### Post by yelo3 on 2007-10-24
since ubuntu added the "command not found magic" it should be simple to do this. The thing that is difficult is to understand when an operation fails because of wrong privileges.
hsve you got an idea?

---

### Post by Vadi on 2007-10-24
+1.

I get around this by having a nautilus script to edit a file with sudo privs, but I'd definitely like something built-in.

---

### Post by el_itur on 2007-10-24
+1 for this one. I've following packagekit's development for a while and it is quite mature and interesting. Foresight is shipping it for some time and, as has been said, major distributors as suse and fedora are planning to ship this.
Some question though:
  How would it play with add/remove?
  It would replace synaptic and update-notifier?
  How straightforward would be writing an apt backend?

I mean, we already have tools like this, why will we want to use something not-invented-here?

Even when I'm in favor of such approach (replacing the debian/ubuntu specific tools in favor of one more desktop agnostic) I think this are questions that matters for developers.

---

### Post by ButteBlues on 2007-10-25
> **el_itur said:**
> 
  How would it play with add/remove?
  It would replace synaptic and update-notifier?

It would replace all of the above, as the new GUI for PackageKit is simple enough for anyone to use.

>   How straightforward would be writing an apt backend?

Fairly straightforward. It's reportedly about half-way complete as-is.

> I mean, we already have tools like this, why will we want to use something not-invented-here?

Because it provides a desktop-agnostic way of handling things that isn't dependent on a single distribution. Simply put, standards are good for the users.

---

### Post by smartboyathome on 2007-10-25
> **ButteBlues said:**
> It would replace all of the above, as the new GUI for PackageKit is simple enough for anyone to use.



Fairly straightforward. It's reportedly about half-way complete as-is.



Because it provides a desktop-agnostic way of handling things that isn't dependent on a single distribution. Simply put, standards are good for the users.

I may install it and try it on my Gutsy box just too see how it looks, but I like my Synaptic Package Manger. :(

---

### Post by billguy on 2007-10-26
> **Vadi said:**
> +1.

I get around this by having a nautilus script to edit a file with sudo privs, but I'd definitely like something built-in.

Would you be willing to post said script?

---

### Post by Vadi on 2007-10-26
Heh it's not mine, I got it off the ubuntu help files wiki ([click]("https://help.ubuntu.com/community/NautilusScriptsHowto?highlight=%28nau%29#head-c98b1bcd55585c16f4f6a8e7c6f5bb2a10b4edae")) :)

---

### Post by amano on 2007-10-28
Ah. That's great. I will have a look at this link.

In any way a solution should be found. It simply isn't nice that the GUI just tells you that you are not allowed to do this and that and you have to go to the CLI to solve the problem.

---

### Post by 23meg on 2007-10-28
[QUOTE=amano]In any way a solution should be found. [/QUOTE]

PolicyKit is the (way to the) proper solution.

---

### Post by Vadi on 2007-10-28
Ooh. Is it approved for Heron and all?

And can test it out if what?

---

### Post by 23meg on 2007-10-28
As far as I know, no.

*(Edit: [Yes]("https://blueprints.edge.launchpad.net/ubuntu/+spec/policykit-integration")!)*

---

### Post by kragen on 2007-10-28
+1 from me as well - opening / making changes to open files shouldnt need a gksu box (unless its unreadable obviously), and to save you should simply have to enter in your password when prompted.

gedit is the obvious one, but I'm sure there are a whole host of other programs that could benefit from the same behaviour.

I suppose having an option to open a file as administrator would also work, but having to enter your password in only once you've decided you want to save changes would be more user friendly.

---

### Post by 23meg on 2007-10-30
[Looks like]("http://www.glatzor.de/blog/blog-details/select_category/1/article/first-day-over/?tx_ttnews%5BbackPid%5D=4&cHash=1b81131ed1") Sebastian Heinlein is working on PackageKit integration, for Hardy +1.

---

### Post by ButteBlues on 2007-10-30
> **23meg said:**
> [Looks like]("http://www.glatzor.de/blog/blog-details/select_category/1/article/first-day-over/?tx_ttnews%5BbackPid%5D=4&cHash=1b81131ed1") Sebastien Heinlein is working on PackageKit integration, for Hardy +1.
Fantastic!

---

### Post by smartboyathome on 2007-10-30
> **ButteBlues said:**
> It would replace all of the above, as the new GUI for PackageKit is simple enough for anyone to use.

Please leave synaptic! I like it! :(

---

### Post by ButteBlues on 2007-10-30
> **smartboyathome said:**
> Please leave synaptic! I like it! :(
Synpatic is not distribution agnostic. For the sake of not confusing users and not making more work for each distribution's developers, having one unified system that is the same across all distributions is the best model.

Here are some screenshots: [http://www.packagekit.org/pk-screenshots.html](http://www.packagekit.org/pk-screenshots.html)

---

### Post by dumbsnake on 2007-11-04
Sorry to bump this feature up, but I was reading over it and let me tell you....  This is seriously a must if ever Ubuntu is going to cross past the 1% mark.  This is probably about the only thing that really does bother me right now about Ubuntu.  I give it +1 too...


BTW, I've been using only Ununtu for over a year now and this is probably my only gripe about it.

---

### Post by aysiu on 2007-11-17
Still no progresss on this bug. I'm a bit disheartened that the devs seem to think this is a wishlist item. This is a serious impediment to new users adopting Ubuntu. I can't tell you how many "I'm not the owner? But this is my computer!!!" posts I've seen in the Absolute Beginner section over the years.

Is there any way to make developers aware of this?

A bug for Ubuntu has already been filed (way back in January, 2005):
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/12154](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/12154)

An upstream bug for Gnome was filed in November, 2001:
[http://bugzilla.gnome.org/show_bug.cgi?id=65058](http://bugzilla.gnome.org/show_bug.cgi?id=65058)

And a specification was written in April, 2006:
[https://wiki.ubuntu.com/privileged-nautilus](https://wiki.ubuntu.com/privileged-nautilus)

Seriously, what can be done?

---

### Post by Jay_Bee on 2007-11-17
This is a very good idea, I used to install Automatix in Edgy just so I could install script to open file/directory as root trough right-click menu... 
It probably isn't too hard to implement at least this kind of menu on right-click.

---

### Post by 23meg on 2007-11-17
[QUOTE=aysiu]Seriously, what can be done?[/QUOTE]

PolicyKit can, and will be, integrated.

---

### Post by aysiu on 2007-11-17
> **23meg said:**
> PolicyKit can, and will be, integrated.
I found this through a Google search:
[http://gitweb.freedesktop.org/?p=PolicyKit.git;a=summary](http://gitweb.freedesktop.org/?p=PolicyKit.git;a=summary)

But I still don't know what PolicyKit does. It fixes this problem of just getting access denied? People can actually authenticate when they try to modify root-owned files?

---

### Post by 23meg on 2007-11-22
[https://blueprints.edge.launchpad.net/ubuntu/+spec/policykit-integration](https://blueprints.edge.launchpad.net/ubuntu/+spec/policykit-integration)

PolicyKit seems to be on the way for Hardy.

---

### Post by smartboyathome on 2007-11-22
Is there a package for policykit anywhere? I would really like to try it and packagekit, but can't find the policykit package.

---

### Post by 23meg on 2007-11-22
When you run an application with gksu, you run the whole thing as root. With PolicyKit, you can run applications as a normal user, and have them get just a particular subset of extra privileges for certain operations, and thus have more fine grained control over who can do exactly what, and arguably, better security.

Here's the relevant blueprint for Hardy: [policykit-integration]("https://blueprints.edge.launchpad.net/ubuntu/+spec/policykit-integration")

---

### Post by 23meg on 2007-11-22
It's in Hardy. I'm not sure that all the changes that are needed for you to do meaningful testing are in place, though.

---

### Post by castrojo on 2007-11-23
There was a PackageKit session at FOSSCamp where this was discussed. Notes are here:

[https://wiki.ubuntu.com/PackageKit](https://wiki.ubuntu.com/PackageKit)

---

### Post by 23meg on 2007-11-23
Sebastian Heinlein has more PackageKit news (as well as a PPA with new packages):

[http://www.glatzor.de/blog/blog-details/select_category/1/article/packagekit-is-landing/?tx_ttnews%5BbackPid%5D=4&cHash=67b11324cf](http://www.glatzor.de/blog/blog-details/select_category/1/article/packagekit-is-landing/?tx_ttnews%5BbackPid%5D=4&cHash=67b11324cf)

---

### Post by 23meg on 2007-11-23
Alexander Larsson, the main developer of Nautilus, has been working on replacing GnomeVFS with GVFS, which is a new userspace virtual filesystem. In [his latest blog post]("http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/"), he excitedly reports about about just the thing we're looking for: coupling GIO (the I/O library used in GVFS) with PolicyKit to enable the user to authenticate to perform certain tasks in Nautilus.

> 
...

**PolicyKit vs Nautilus**

But all that is not whats got me most excited right now. Instead its this idea I got about using PolicyKit and gio in order to implement system administrator features in Nautilus. Basically, you&#8217;d do a file operation on some system file, which gives you an error dialog saying you don&#8217;t have permissions to do this. But the error dialog has a button that lets you authenticate (with e.g. the root password) and continue the operation with root rights.

This is quite simple to implement in nautilus-gio, because all I/O operations go through the GFile interface. You just create an implementation of GFile that proxies all operations to a setuid helper program (which uses PolicyKit to authenticate). With this done, all the Nautilus code will work unmodified with this new backend, all you have to do is make sure it uses this new GFile implementation.

This is much better than running your entire Nautilus process (or even desktop) as root, for multiple reasons. First of all your Nautilus application will integrate nicely with your desktop (using your theme/prefs/etc instead of the root ones). Secondly a lot less code is running as root, which means that the risk for a security breach or accidents as root are much smaller. Third, you can configure this to use sudo-style authentication which means you don&#8217;t need to give out the root password (or even have one) .

Still, this work will have to wait, as the main priority right now is getting the gio-branch into a useful shape so that it can be merged into svn HEAD. I think this will happen soon. Maybe next week even.

---

### Post by aysiu on 2007-11-24
That sounds great, 23meg.

What do you think the odds are of this making it into Hardy?

---

### Post by 23meg on 2007-11-24
Quite high, seemingly. GIO and GVFS have been proposed for inclusion in GNOME 2.22, and the goal looks attainable, even though they lack some essential features and backends at this point. Since the GNOME world is showing lots of interest in PolicyKit, I'd expect the GIO branch of Nautilus to be PolicyKit-enabled by this release as well. The fact that the main developer is enthusiastic about it is a good sign.

For those looking to contribute, Larsson has a [TODO list]("http://live.gnome.org/GioToDo").

---

### Post by ayenack on 2007-11-24
aysiu. Do you think it'd be OK for me to put a little script on here to make it possible for people to right click any file and open it as root or do you think it'll be irresponsible to do so?

---

### Post by aysiu on 2007-11-24
> **ayenack said:**
> aysiu. Do you think it'd be OK for me to put a little script on here to make it possible for people to right click any file and open it as root or do you think it'll be irresponsible to do so?
Such a script already exists:
[http://ubuntu-tutorials.com/2006/12/29/right-click-to-launch-custom-scripts-with-nautilus-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/29/right-click-to-launch-custom-scripts-with-nautilus-ubuntu-6061-610/)

---

### Post by ayenack on 2007-11-24
> Originally Posted by **aysiu**
[I]Such a script already exists:
[http://ubuntu-tutorials.com/2006/12/...untu-6061-610/](http://ubuntu-tutorials.com/2006/12/...untu-6061-610/)[/I]

Ah cool. Well here's what I've done on my system.

In terminal.

**gksudo gedit .gnome2/nautilus-scripts/Right\ click\ root**

Added this to the empty file.

[B]for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do

          gksudo "gnome-open $uri" &

          done[/B]

Saved and closed. Then.

**sudo chmod +x .gnome2/nautilus-scripts/Right\ click\ root**

Rebooted.

Can now right click on a file go to Scripts and select Right click root. Name can easily be changed  just change /Right\ click\ root to whatever you want in both instances.

---

### Post by 23meg on 2007-11-24
An update, from the replies Larsson posted to comments to his blog post:

> **Alexander Larsson]I can&#8217 said:**
> 

And about undoing file operations, which is another long standing shortcoming:

[QUOTE=Alexander Larsson]Specifically about undo. There is someone working on that, and it seems to be progressing. Its a lot of work though to get a solid implementation of it though, so we&#8217;ll have to see when is finished.

This all means that things are moving forward, but that there's no guarantee for GNOME 2.22, and thus Hardy. However, if we help out and contribute, the chances will be greater.

---

### Post by amano on 2007-11-26
EDIT:
- huh? thread merged, while I posted to both of them?

---

### Post by amano on 2007-11-26
People!

This actually might come to your favourite GNOME install next to you:
[http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/](http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/) (Chapter "PolicyKit vs Nautilus").

Keep your fingers crossed that Alex can implement that in time for 2.22!

:guitar:

---

### Post by aysiu on 2007-11-26
> **amano said:**
> EDIT:
- huh? thread merged, while I posted to both of them?
Yes.

---

### Post by 23meg on 2007-11-27
[policykit-integration]("https://blueprints.edge.launchpad.net/ubuntu/+spec/policykit-integration") has just been approved.

---

### Post by Vadi on 2007-11-27
Happy happy people. Thank you!

---

### Post by Ralphie on 2008-03-07
What do people think of setting it up in such a way that instead of simply being denied, you are prompted with a warning to the likes of: 
"Warning, are you sure you know what you are doing blah blah blah...."
and root password to enter, thus saving the changes you made to the file via your text editor of choice?

I find it quite annoying having browsed to a restricted area without thinking, opening a file in the text editor, editing it, just to later have it deny my save. I then have to log into the root nautilus, re-find the file, and copy and paste all my edits.

maybe there is a better way? but i don't see why this shouldn't work the same as, say, installing or uninstalling new software.

ideas, fixes, all welcome! :D

---

### Post by locosmurf on 2008-03-07
I agree with you. I hate it when I'm editing my config files just to find out that I didn't open it as root like I should have. If I knew more about coding I would fix it myself but as I don't I have to rely on the wonderful community here to do this for me ^_^

But anywho I think it would be great if a file that needs to be edited as root automatically prompts you for the password and allows you to do what you need...

However, and I just thought of this, what if a person who is not the admin just wants to look at the file and not change it? then the whole point of it prompting you for a password is pointless.... now I'm undecided lol

---

### Post by Ralphie on 2008-03-08
well maybe it should only prompt you when you try to make a change, thats what i would prefer, becasue it would be a pain to type my password just to see something. 

I would like to see this as an actual ubuntu feature in a future release rather than just a quick fix, which, if anyone could figure it out, would be awesome for now! haha 

maybe if it were done this way we would have less people wanting to just fully log in as root. back when i was a beginning user of linux this was my main frustration, and my main reason to want to log in as root. 

then i discovered the nautilius root way, which is what i currently use, but still see it as a work around to something that could be done a little better.

---

### Post by Meson on 2008-03-08
There's gotta be some VI settings that will throw it in your face if you've opened a read-only file.  As for gedit, just keep a different color scheme.

---

### Post by astrotech226 on 2008-03-09
> **Meson said:**
> There's gotta be some VI settings that will throw it in your face if you've opened a read-only file.  As for gedit, just keep a different color scheme.

Vi does tell you that.  It's not *real* obvious, but it's there.  If you try to vi /etc/passwd as a regular user, look on the bottom left:
```

"passwd" [readonly] 30L, 1374C
```

This idea of popping up a message is in any text editor is going to be extremely hard to do.  If not impossible unless you decide on a single text editor and figure out how to use it.  Vi can do some scripting.  Emacs can do even more.

There's even some simple workarounds.  In vi, lets say you spent 30 minutes modifying a file only to discover it's read only.  If you are the owner and it's set to read only, do a ":w!".

If you aren't the owner, save the file as a different name and then mv the new file to the original.

```
:w newfile.txt
:q!
sudo mv newfiles.txt oldfile.txt
```

It's not optimal, but it does work and ensures you don't waste a lot of time.

---

### Post by Ralphie on 2008-03-20
> This idea of popping up a message is in any text editor is going to be extremely hard to do. If not impossible unless you decide on a single text editor and figure out how to use it.

I am not sure what all this "VI" talk is about, but to me it seams like the message would come up no matter what application you are opening it with, because it would just be set somewhere in the system that *any* file that is privileged only to root would make the message appear. maybe the message would run some script that would take whatever application wanting to open it, and add gksudo before it so that you can simply type in your root password and there you go.

I have absolutely no clue on how to code, so maybe this is impossible, or maybe it is a good idea, either way I'm throwing the idea out there :D

---

### Post by HermanAB on 2008-03-20
Hmm, well, it is only a problem for people who don't know what they are doing and that is the whole idea actually...

---

### Post by Diabolis on 2008-03-20
> Hmm, well, it is only a problem for people who don't know what they are doing and that is the whole idea actually...

I agree completely and I love it that way. I hope that something like this never gets implemented.

---

### Post by Ralphie on 2008-03-20
Well what I'm saying is if someone wants to do something with these files they will find a way to do it, or throw the OS out the window because they don't want to learn how to, or don't want to hear about how wrong it is to log in as root.
How many "linux sucks I'm going back to windows" or "tell me how to log in as root" threads are there? A ton. For reasons like this.

If you do it this way a proper warning could pop up, and you won't have people trying to fully just log in as root anymore. 

I just remember it being a huge frustration at first, causing me to go back to windows once before. Now that I've fully "made the switch", I have no intents of going back, but I still do find this to be a frustration when, like stated above, I forget to gksudo nautilus. 

Yes I like to do it all graphical because I, as well as many others, are comfortable doing it that way, and no I have not completely messed up my system once.

---

### Post by smartboyathome on 2008-03-20
This should be possible now that Ubuntu decided to go with PolicyKit. Some things like this have already popped up in GNOME 2.22, and this may be in 2.24. :D

---

### Post by Ralphie on 2008-03-20
Nice, good to hear

---

### Post by Ralphie on 2008-12-25
Sadly this this hasn't changed with the latest gnome or ubuntu :(

Is there a place I can more officially submit this request for future releases?

---

### Post by gnomeuser on 2008-12-25
> **Ralphie said:**
> Sadly this this hasn't changed with the latest gnome or ubuntu :(

Is there a place I can more officially submit this request for future releases?

bugzilla.gnome.org - polite requests are good, polite requests with patches even better.

---

### Post by Ralphie on 2008-12-25
Thanks for the information. Sadly I won't be able to provide the patches, but hopefully someone is interested ;)

***EDIT***
AH, it looks like I'm not alone in this want!
Here is the request (not posted by me):
[http://bugzilla.gnome.org/show_bug.cgi?id=352886](http://bugzilla.gnome.org/show_bug.cgi?id=352886)
If anyone here is willing to help.

---

