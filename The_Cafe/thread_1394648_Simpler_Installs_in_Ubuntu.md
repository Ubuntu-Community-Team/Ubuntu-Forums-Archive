---
title: "Simpler Installs in Ubuntu?"
date: 2010-01-30
forum: The Cafe
---

### Post by Joseph Schwenker on 2010-01-30
Hey all!  Way back in the day (like, five months ago) I used Windows.  One of the things that really annoyed me about Windows was its incredibly annoying and long installs.  I contrasted this with Mac OS X's click and drag installs.  One day, I became so frustrated that I made [this mockup]("http://lh6.ggpht.com/_Ed2WX_IXHtg/SmOxGxb7ArI/AAAAAAAAAxs/eJ1ULPxkiSo/Prism%20Install.png") of a simpler install in Windows.  Upon switching to Ubuntu, I really liked its simpler installs.  They were simpler than Windows, but not quite to the point of OS X's simplicity.  In Mac OS X, regular third party applications (games, programs, etc) are installed by dragging them to Applications, the universal location for applications.  This directory is owned by the user (I think, as you don't have to enter a password to drag the file there).  You download .dmg files (similar to ISO), mount them, and open them.  This displays a folder with a custom background and two files.  You drag the application to the Applications folder, and it is copied.  Simple, right?  The primary exceptions to this are system updates, and programs that affect the root system.  For instance, X11.  The installer for X11 requires you to go through a Windows-like setup assistant.  You also have to enter your password, and a small box pops up and asks you for it.  It does not lock the whole screen, unlike Ubuntu.  I guess that the primary reason for me writing this is because I want a simpler Application install system in Ubuntu.  Yes, Synaptic is great, but it may confuse the average user.  I, an experienced user, did not even know that Synaptic existed until a week into 9.04.  This had kept me using Windows for years.  If there had been a simple application management system in place, I probably would have known about it.  Currently, applications are all kept in /usr/share/applications/, which is root-owned.  What if there was a user-owned Applications directory in Ubuntu, and instead of entering their passwords for applications that do not need to use root permissions while running, and do not modify system files, they could just drag ONE FILE into an Applications directory.  This would make managing applications very easy, as users could manage their applications right from Nautilus, and not need root permissions.  For other "weird" packages, Synaptic should probably be used.  The user's Application directory would be just for regular applications, and dependencies would not be here.  They would, instead, be kept in a folder within Applications, called Dependencies (which should be owned by root), or in some weird directory that is one level below /.  The point is, users should only have to deal with the packages that they care about: things that they can see, things that they use every day, and should not have to worry about mixing other weird things (that confuse them!) in with their regular applications.  Synaptic would also be available if they wanted to manage all of their packages at once.  So, this is my idea for Ubuntu.  What does everyone else think?

PS, the word "applications" was stated 15 times in this post, not counting the tags or any uses of it in this sentence.  XD

---

### Post by dolphinaura on 2010-01-30
> **Joseph Schwenker said:**
> Hey all!  Way back in the day (like, five months ago) I used Windows.  One of the things that really annoyed me about Windows was its incredibly annoying and long installs.  I contrasted this with Mac OS X's click and drag installs.  One day, I became so frustrated that I made [this mockup]("http://lh6.ggpht.com/_Ed2WX_IXHtg/SmOxGxb7ArI/AAAAAAAAAxs/eJ1ULPxkiSo/Prism%20Install.png") of a simpler install in Windows.  Upon switching to Ubuntu, I really liked its simpler installs.  They were simpler than Windows, but not quite to the point of OS X's simplicity.  In Mac OS X, regular third party applications (games, programs, etc) are installed by dragging them to Applications, the universal location for applications.  This directory is owned by the user (I think, as you don't have to enter a password to drag the file there).  You download .dmg files (similar to ISO), mount them, and open them.  This displays a folder with a custom background and two files.  You drag the application to the Applications folder, and it is copied.  Simple, right?  The primary exceptions to this are system updates, and programs that affect the root system.  For instance, X11.  The installer for X11 requires you to go through a Windows-like setup assistant.  You also have to enter your password, and a small box pops up and asks you for it.  It does not lock the whole screen, unlike Ubuntu.  I guess that the primary reason for me writing this is because I want a simpler Application install system in Ubuntu.  Yes, Synaptic is great, but it may confuse the average user.  I, an experienced user, did not even know that Synaptic existed until a week into 9.04.  This had kept me using Windows for years.  If there had been a simple application management system in place, I probably would have known about it.  Currently, applications are all kept in /usr/share/applications/, which is root-owned.  What if there was a user-owned Applications directory in Ubuntu, and instead of entering their passwords for applications that do not need to use root permissions while running, and do not modify system files, they could just drag ONE FILE into an Applications directory.  This would make managing applications very easy, as users could manage their applications right from Nautilus, and not need root permissions.  For other "weird" packages, Synaptic should probably be used.  The user's Application directory would be just for regular applications, and dependencies would not be here.  They would, instead, be kept in a folder within Applications, called Dependencies (which should be owned by root), or in some weird directory that is one level below /.  The point is, users should only have to deal with the packages that they care about: things that they can see, things that they use every day, and should not have to worry about mixing other weird things (that confuse them!) in with their regular applications.  Synaptic would also be available if they wanted to manage all of their packages at once.  So, this is my idea for Ubuntu.  What does everyone else think?

PS, the word "applications" was stated 15 times in this post, not counting the tags or any uses of it in this sentence.  XD
the mac osx installs work without administrative privelages becasue the user accounts work differently than linux. It is more like a windows privileges system. By default, the first user that creates an account there has administrative rights. Which means they can install applications and such. Take a look at my desktop for example. 

[[IMG]http://img191.imageshack.us/img191/5762/applications.th.png[/IMG]](http://img191.imageshack.us/i/applications.png/)
The terminal window that ive opened is a ls of the folder where all the applications are installed (/Applications)
You can see that although that directory should require admin privelages to write into, ive installed applications in there....

however, most macbooks are mostly used by one person anyways, so there is not really any use for a "permissions required" dialog when the admin user is installing something.

p.s. I also notice that on my mac osx installation, apps use WAY more space on the hD and are larger in size to download.

---

### Post by Joseph Schwenker on 2010-01-30
Although the user accounts work differently in OS X, so does my proposal mentioned in my first post.  Only everyday applications are installed in my proposed applications directory.  Games, web browsers, word processors, terminals, etc.  In the Mac Applications folder, there is a Utilities folder, which is similar to what my "Dependencies" folder will be.  Dependencies will be full of all of the crap that no one cares about except developers.  :twisted:

Unless what you are saying is that you still want the permissions system in place so that those applications cannot be installed in the first place...
What does Mac OS X do when a non-admin user tries to drag a .app file to Applications?

---

### Post by dolphinaura on 2010-01-30
> **Joseph Schwenker said:**
> Although the user accounts work differently in OS X, so does my proposal mentioned in my first post.  Only everyday applications are installed in my proposed applications directory.  Games, web browsers, word processors, terminals, etc.  In the Mac Applications folder, there is a Utilities folder, which is similar to what my "Dependencies" folder will be.  Dependencies will be full of all of the crap that no one cares about except developers.  :twisted:

Unless what you are saying is that you still want the permissions system in place so that those applications cannot be installed in the first place...
What does Mac OS X do when a non-admin user tries to drag a .app file to Applications?

I believe that the application installation process/permissions  is different because most people who have a mac at all, is the only person who uses it. The fact that mac osx by default logs in the user confirms that. If their the only person whos using it, there is not really much reason to require them to enter a password is there?

> **Joseph Schwenker said:**
> <snip>
Unless what you are saying is that you still want the permissions system in place so that those applications cannot be installed in the first place... And no, i meant that the mac osx does not need a permissions system for application installation, see above.

When a non-admin user drags some stuff into there?
never tried. But I assume it will pop up a message similar to the screenshot I have below.
Also another note: if you notice, ive pulled down one of the Finder Menus. This is because when it requires permissions, it, instead of locking the entire system, like ubuntu, it locks only finder.
[[IMG]http://img59.imageshack.us/img59/1471/authenticate.th.png[/IMG]](http://img59.imageshack.us/my.php?image=authenticate.png)

---

### Post by Psumi on 2010-01-30
By the way, applications you install are stored in /usr/bin.

Since firefox sometimes doesn't know how to handle filetypes, I need to know this directory by heart.

---

### Post by Joseph Schwenker on 2010-01-30
Ah, so that is where they are stored!  I thought that they were stored in /usr/share/applications, but I guess that that is just a collection of .desktop files that are only shortcuts, er, commands.

---

### Post by perce on 2010-01-30
Being able to install applications without a password is not advisable for security reasons. 

Doing installations by drag-and-drop of a directory would be possible to implement I think, but probably it would need to change the standard Unix directory structure, which would be a major headache for a very little gain.

---

### Post by Joseph Schwenker on 2010-01-30
Hmm... so, maybe if my proposed "Applications" folder was a universal folder, like /usr/share/applications, then it could be owned by the users that had permissions to use it.  It would not be owned by root, but by the user.  This way, only users who owned the folder could modify it, thus forming a simple permission system.

---

### Post by Psumi on 2010-01-30
> **Joseph Schwenker said:**
> Hmm... so, maybe if my proposed "Applications" folder was a universal folder, like /usr/share/applications, then it could be owned by the users that had permissions to use it.  It would not be owned by root, but by the user.  This way, only users who owned the folder could modify it, thus forming a simple permission system.

Not possible. That would break our secure system.

/usr/share/applications is also owned by root, and I like it this way.

---

### Post by Joseph Schwenker on 2010-01-30
> **perce said:**
> Being able to install applications without a password is not advisable for security reasons. 

Doing installations by drag-and-drop of a directory would be possible to implement I think, but probably it would need to change the standard Unix directory structure, which would be a major headache for a very little gain.

Little gain?  It would simplify the entire Linux project!  No more confusion on how to install everyday applications, just drag and drop into your applications.  There would be no more .debs, which confuse users about where to uninstall the file from.  This system is simple.  Users would know where they put the file in the first place, and thus would know how to remove it.

---

### Post by Psumi on 2010-01-30
> **Joseph Schwenker said:**
> Little gain?  It would simplify the entire Linux project!  No more confusion on how to install everyday applications, just drag and drop into your applications.  There would be no more .debs, which confuse users about where to uninstall the file from.  This system is simple.  Users would know where they put the file in the first place, and thus would know how to remove it.

Try BSD then? MacOS is based off of BSD.

---

### Post by Joseph Schwenker on 2010-01-30
> **Psumi said:**
> Not possible. That would break our secure system.

/usr/share/applications is also owned by root, and I like it this way.

Have you read my original post?  Or my signature?  In my proposed system, only everyday, simple applications are put into the non-root owned folder.  Why should you need root permissions to install something like Amarok or AbiWord?  You could just drag them into a folder, making them easier to manage.  Their preferences would be stored elsewhere.  There would be another directory in the applications folder, called Dependencies, which would contain all of the stuff that only developers care about, and would be owned by root.  The average user only cares about his applicatons, not about libj-malloc, or some other random file.

---

### Post by Psumi on 2010-01-30
A complete binary system for ubuntu like MacOS... interesting.

I could put my apps on my flash drive finally by dragging and dropping them! *gasp*

Oh wait.

---

### Post by Joseph Schwenker on 2010-01-30
> **Psumi said:**
> Try BSD then? MacOS is based off of BSD.

But I'm trying to improve UBUNTU, not BSD.  Ubuntu has already come INCREDIBLY FAR in terms of stability and ease of use.  However, it is not ready for the average user yet.  There are still many flaws and bugs.  It's almost there.  I think that if we make it more intuitive, whether it is done by simplifying Synaptic, or making an Applications folder, more people will use Linux.

---

### Post by dolphinaura on 2010-01-30
> **Joseph Schwenker said:**
> Have you read my original post?  Or my signature?  In my proposed system, only everyday, simple applications are put into the non-root owned folder.  Why should you need root permissions to install something like Amarok or AbiWord?  You could just drag them into a folder, making them easier to manage.  Their preferences would be stored elsewhere.  There would be another directory in the applications folder, called Dependencies, which would contain all of the stuff that only developers care about, and would be owned by root.  The average user only cares about his applicatons, not about libj-malloc, or some other random file.

what if i did this to your app?

cat " " > /path/to/application

that is one of the problems.

The second is about trusted sources.
If you use a single applications folder that you can drag and drop into, it means that you can be installing a illigimate app thats hiding something such as a backdoor without knowing it.
That is one of the main points of the repos in ubuntu : for quality control, and to provide a place for people to download software that you can know doesnt have the bad stuff in it.
Which is one of the reasons we tell people to install the app from the repos instead of downloading a DEB from an untrusted source. 

If the average user screws up the system by installing something illgitimate, they will have noo idea how to fix it. Although maybe you and I know that by appending -x to the mac osx startup options and using the recovery mode of ubuntu, we can likely reach a terminal, or a gui where we can fix the problem, the average Joe user is clueless on how to do this. 

Which means that there will be more crashing, and complaints from newbies. which is NOT good for someone who is just starting a new OS.

---

### Post by Psumi on 2010-01-30
> **dolphinaura said:**
> what if i did this to your app?

cat " " > /path/to/application

haha

---

### Post by Joseph Schwenker on 2010-01-30
And that command does what?  Let me try to figure it out...
Cat reads a text file, and outputs it to the terminal.  No idea what the > does, though.  Probably something bad.

---

### Post by Joseph Schwenker on 2010-01-30
> **dolphinaura said:**
> what if i did this to your app?

cat " " > /path/to/application

that is one of the problems.

The second is about trusted sources.
If you use a single applications folder that you can drag and drop into, it means that you can be installing a illigimate app thats hiding something such as a backdoor without knowing it.
That is one of the main points of the repos in ubuntu : for quality control, and to provide a place for people to download legitimate, non-malware software.

And most people also download .debs and grant them root permissions, thus allowing those applications to hide backdoors as well.  What if the app ran as a low-level user, without permission to modify any of the end-user's files?  It would be similar to Google Chrome's security model.  There is the user, and the dog below him.

---

### Post by dolphinaura on 2010-01-30
> **Joseph Schwenker said:**
> And that command does what?  Let me try to figure it out...
Cat reads a text file, and outputs it to the terminal.  No idea what the > does, though.  Probably something bad.

cat will take the stuff in the quotes and replace the entire app with its contents.
so a cat with one ">" will replace the entire file with the stuff inside the quotes
and a cat with two ">>" will append to the file.

---

### Post by dolphinaura on 2010-01-30
> **Joseph Schwenker said:**
> And most people also download .debs and grant them root permissions, thus allowing those applications to hide backdoors as well.  What if the app ran as a low-level user, without permission to modify any of the end-user's files?  It would be similar to Google Chrome's security model.  There is the user, and the dog below him.

which is, as i said why we ask users to install applications from the repos, not random debs that they find on the net.

And that sitll doesnt cover quality control.
Let me provide an example....

Newbie installs software X on his/her system.
he/she runs it.
Due to a memory leak, software X quickly gobbles up the RAM and as a result crashes the entire system.
Newbie says: this stuff is junk, doesnt even work... and whips out the windows cd....

although I would have stayed and wrestled with the app until it worked, the average Joe user just needs/wnats the stuff to work Out Of The Box without wrestlling around with it.

---

### Post by Joseph Schwenker on 2010-01-30
I'm starting to think that using Google Chrome's security model would be better.  [http://www.google.com/googlebooks/chrome/med_26.html]("http://www.google.com/googlebooks/chrome/med_26.html")

[http://www.google.com/googlebooks/chrome/med_28.html]("http://www.google.com/googlebooks/chrome/med_28.html")

What do you guys think?

---

### Post by Psumi on 2010-01-30
> **Joseph Schwenker said:**
> I'm starting to think that using Google Chrome's security model would be better.  [http://www.google.com/googlebooks/chrome/med_26.html]("http://www.google.com/googlebooks/chrome/med_26.html")

[http://www.google.com/googlebooks/chrome/med_28.html]("http://www.google.com/googlebooks/chrome/med_28.html")

What do you guys think?

"As long as you close the bad tab it won't affect you."

but what if you like what's on the bad tab?

just give the user the "cold shoulder"? Oh wait, all support teams do that, not just linux!

If we can't write to our documents, what good is a harddrive or flash drive? The program can't save to a flash drive, so... yeah? What good is backing up? You can't do it.

And you're basing all of this on a program that has spyware... **built-in**?!

---

### Post by Joseph Schwenker on 2010-01-30
> **Psumi said:**
> "As long as you close the bad tab it won't affect you."

but what if you like what's on the bad tab?

just give the user the "cold shoulder"? Oh wait, all support teams do that, not just linux!

If we can't write to our documents, what good is a harddrive or flash drive? The program can't save to a flash drive, so... yeah? What good is backing up? You can't do it.

And you're basing all of this on a program that has spyware... **built-in**?!

What?  Google Chrome does not have spyware!  I am using Google Chrome's security model.  The user is the highest level.  All applications run on a level lower than the user.  They do not have access to any of the user's files, unless the user gives them access.  The user is the only person who has permission to move files around.  With your inquiry on "bad tabs", I was referring to applications.  If all applications are confined to their own processes, and not allowed to do anything outside of their process without the end-user's permission, then they cannot be harmful.

---

### Post by Psumi on 2010-01-30
> **Joseph Schwenker said:**
> What?  Google Chrome does not have spyware!

see this: [http://www.srware.net/en/software_srware_iron_chrome_vs_iron.php](http://www.srware.net/en/software_srware_iron_chrome_vs_iron.php)

---

### Post by cariboo on 2010-01-30
> **Joseph Schwenker said:**
> But I'm trying to improve UBUNTU, not BSD.  Ubuntu has already come INCREDIBLY FAR in terms of stability and ease of use.  However, it is not ready for the average user yet.  There are still many flaws and bugs.  It's almost there.  I think that if we make it more intuitive, whether it is done by simplifying Synaptic, or making an Applications folder, more people will use Linux.

Remember Ubuntu is a Linux distribution, there many other distributions using the same files. Your "simple to change" would probably mean a complete rewrite of the kernel and all of the applications.

It seems to me the way to install programs on the Mac is not very safe, there is no central place to download software from, unless you include the Apple store, this means you have to go to some random web site to download anything useful, you really have no way of knowing if the software is actually malware or not

Most Linux distributions use a software repository for almost everything you need, there is no need to go to some random web site to download software. There are enough checks and balances in place that the repositories are very safe to install packages from.

I can't see the Mac way of installing software is an easier than the Linux way. Go to synaptic/yum whatever, search for the software you need, once it is found right click to select and then click the apply button. You've already entered your password when you started the package installer so there is no need to do it again.

---

### Post by Joseph Schwenker on 2010-01-31
I guess that my way just isn't "safe" enough.  I still want to be able to drag and drop into an "applications" folder, though.  Also, many users download software from third party sources, as the repository (hint, hint, hint!) is often outdated!  This puts a lot of trust into a third-party source, and since the user has no idea what they are installing, they usually just enter their password and give the program root permissions.  This is not secure.  But, if we can create a way to isolate processes and give them no permissions, we could create a more secure system.  THEN, we could have those nice little drag and drops into the Applications folder.  ;)

---

### Post by aysiu on 2010-01-31
I think it's interesting that when Apple sets up a software repository (the iTunes App Store), no one complains that it's difficult to use, but when Ubuntu sets up a software repository (Ubuntu Software Center), it's suddenly difficult.

Centralized package management means you can install what's available in the repository. At least with Ubuntu, you can add repositories as needed. With the iTunes App Store, not so much (unless you jailbreak your iPhone and then use Cydia).

What might be interesting, since this suggestion comes up quite often, is if someone created another graphical frontend for *dpkg* (right now we have Update Manager, Add/Remove, Synaptic, and Ubuntu Software Center--which is supposed to eventually take the place the former three, as I understand it), which involved dragging and dropping repository applications to an "Applications folder" (which isn't really a folder at all but just what appears to be one.

Applications "in" the "Applications folder" *dpkg* would mark as installed, and applications dragged "out" of the "Applications folder" would be uninstalled.

---

### Post by Joseph Schwenker on 2010-01-31
> **aysiu said:**
> I think it's interesting that when Apple sets up a software repository (the iTunes App Store), no one complains that it's difficult to use, but when Ubuntu sets up a software repository (Ubuntu Software Center), it's suddenly difficult.

Centralized package management means you can install what's available in the repository. At least with Ubuntu, you can add repositories as needed. With the iTunes App Store, not so much (unless you jailbreak your iPhone and then use Cydia).

What might be interesting, since this suggestion comes up quite often, is if someone created another graphical frontend for *dpkg* (right now we have Update Manager, Add/Remove, Synaptic, and Ubuntu Software Center--which is supposed to eventually take the place the former three, as I understand it), which involved dragging and dropping repository applications to an "Applications folder" (which isn't really a folder at all but just what appears to be one.

Applications "in" the "Applications folder" *dpkg* would mark as installed, and applications dragged "out" of the "Applications folder" would be uninstalled.

But your proposal does not facilitate the installation of third-party packages.  (debs downloaded from a website, not PPAs)  My proposal has an actual folder from which you can launch the applications.  The thing is, not every piece of legit software can be in the repositories instantly.  Songbird STILL isn't.  You also have outdated software, which makes people download the latest version from the developer's website.  I like your frontend for dpkg idea, though.  I really would like for it to run from Nautilus, though.

---

### Post by perce on 2010-01-31
> **Psumi said:**
> 

I could put my apps on my flash drive finally by dragging and dropping them! *gasp*



You can, if the application compiled in a certain way. For example I've run skype from a usb pen once.

---

### Post by Xbehave on 2010-01-31
User should not be able to install software only administrators should, however what you are suggesting will be easy to setup in future releases using policykit (however i really hope it's never that way by default). 

user installs are bad because:
[LIST]
[*]If a program gets exploited it can modify itself and be permanently "owned"
[*]Most malware doesn't need root, so if it can install itself as a user, it can still steal your CC details
[*]Privilege escalation vulnerabilities do happen out there so if malware can sit and wait as a user till one pops up, bamn goes your root account.
[/LIST]

---

### Post by aysiu on 2010-01-31
[Songbird is in the GetDeb repository](http://www.getdeb.net/updates/Ubuntu/9.04/?q=songbird):
> Use the following instructions:

   1.

      Install the getdeb package.
   2.

      Or configure the repository manually:

      Go to System-Administration-Software Sources, Third-Party Software tab, Add:
      deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps

      Add the repository GPG key, open a terminal window and type:
      wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
   3.

      Click the "Install this now" button below the screenshot of the desired application. And who cares if software is "outdated"? I *love* that I don't have to manually update each individual program. Security updates happen automatically, and **everything** gets updated every six months.

If you want a different filesystem hierarchy, use GoboLinux. If you want a rolling release distro, use PCLinuxOS or Debian unstable.

Ubuntu updates software every six months by design.

---

### Post by Joseph Schwenker on 2010-01-31
> **aysiu said:**
> [Songbird is in the GetDeb repository](http://www.getdeb.net/updates/Ubuntu/9.04/?q=songbird):
 And who cares if software is "outdated"? I *love* that I don't have to manually update each individual program. Security updates happen automatically, and **everything** gets updated every six months.

If you want a different filesystem hierarchy, use GoboLinux. If you want a rolling release distro, use PCLinuxOS or Debian unstable.

Ubuntu updates software every six months by design.

Who CARES if software is outdated?!  The version of Nexuiz in the Ubuntu 9.04 repository is so old that I can't even join any servers with it.  I need to download the version from their website.  If applications are not using the latest version, then they are more vulnerable to security flaws and exploits.

---

### Post by perce on 2010-01-31
> **aysiu said:**
> I think it's interesting that when Apple sets up a software repository (the iTunes App Store), no one complains that it's difficult to use, but when Ubuntu sets up a software repository (Ubuntu Software Center), it's suddenly difficult.

Centralized package management means you can install what's available in the repository. At least with Ubuntu, you can add repositories as needed. With the iTunes App Store, not so much (unless you jailbreak your iPhone and then use Cydia).

What might be interesting, since this suggestion comes up quite often, is if someone created another graphical frontend for *dpkg* (right now we have Update Manager, Add/Remove, Synaptic, and Ubuntu Software Center--which is supposed to eventually take the place the former three, as I understand it), which involved dragging and dropping repository applications to an "Applications folder" (which isn't really a folder at all but just what appears to be one.

Applications "in" the "Applications folder" *dpkg* would mark as installed, and applications dragged "out" of the "Applications folder" would be uninstalled.

As usual, you are the best!

---

### Post by Xbehave on 2010-01-31
> **Joseph Schwenker said:**
> If applications are not using the latest version, then they are more vulnerable to security flaws and exploits.
That's the point of the repositories they give you security updates e.g firefox 3.0->3.0.x, etc but not feature updates firefox 3.0->3.5. 

I suggest you go learn about the repositories, how they work and why they work the way they do, it's pretty fundamental to the ubuntu design that you get security updates but not feature updates. As aysiu said if you don't like this design there are other distros that have different designs and your free to use them.

---

### Post by ciborium on 2010-01-31
> **Joseph Schwenker said:**
> Who CARES if software is outdated?!  The version of Nexuiz in the Ubuntu 9.04 repository is so old that I can't even join any servers with it.  I need to download the version from their website.  If applications are not using the latest version, then they are more vulnerable to security flaws and exploits.


Wait...  You're whining about old packages and your example has to do with the PREVIOUS version of Ubuntu?

You might try upgrading to Karmic if you want newer packages.

---

### Post by Joseph Schwenker on 2010-01-31
> **ciborium said:**
> Wait...  You're whining about old packages and your example has to do with the PREVIOUS version of Ubuntu?

You might try upgrading to Karmic if you want newer packages.

And if I upgraded to Karmic, then I would be whining about why WINE doesn't work, why OpenArena doesn't work, why audio in Blender doesn't work, why audio in Glest doesn't work, why audio in Nexuiz doesn't work, why audio in almost every single application DOESN'T WORK.  I would also be whining about why there is no volume control applet when I kill PulseAudio.  I tried Karmic.  PulseAudio sucks.  It's not my fault that I use a distribution of Ubuntu that ACTUALLY WORKS.  If the latest packages won't work in 9.10, I guess that 9.04 can't have them either, even though THEY WORK PERFECTLY IN JAUNTY.  I guess they just don't want to make Karmic look bad.

---

### Post by zipperback on 2010-01-31
> **Joseph Schwenker said:**
>  
 I guess that the primary reason for me writing this is because I want a simpler Application install system in Ubuntu.  Yes, Synaptic is great, but it may confuse the average user.  


Synaptic isn't the only method you have available for installing software.
You  can also use the &#8220;Ubuntu Software Center&#8221; application which is installed by default.
The Ubuntu Software Center application is a very simple to use application.
Even a brand new user should be able to figure out how to use it in a very short time.

For those who are little more experience there is always compiling from source, or using aptitude or apt-get.


> **Joseph Schwenker said:**
>  
I, an experienced user, did not even know that Synaptic existed until a week into 9.04.  This had kept me using Windows for years.  


Synaptic is talked about quite regularly on the ubuntuforums, and really, pretty much any Linux website that has information about package management will talk about synaptic. When I install a new operating system that I haven't used before, I generally go through and look at all the applications which are available for preferences and system administration in general. 



> **Joseph Schwenker said:**
>  
If there had been a simple application management system in place, I probably would have known about it.  Currently, applications are all kept in /usr/share/applications/, which is root-owned.  What if there was a user-owned Applications directory in Ubuntu, 

Nothing is stopping you from doing that actually.

Open a terminal window and type the following command.
```

mkdir ~/Applications

```

That will create a directory called Applications.

I have a directory on my system for things that I compiled from source and run from within my user account quite regularly. Of course I'm the only user on my desktop, but it doesn't matter because even if there were multiple users, the applications within my Applications directory belong to my user account only because of system wide access rights.

> **Joseph Schwenker said:**
> 
and instead of entering their passwords for applications that do not need to use root permissions while running, and do not modify system files, they could just drag ONE FILE into an Applications directory.


If you have a compiled executable you can put it in your Applications directory and launch it.

What you're talking about is just installing an application at the user level for an individual user account. That's nothing new really.

Personally though, as a network administrator I would prefer that the end user not be installing things at all. In a business situation it's better not allow end user software installations. It's a business computer and they're suppose to be using it for work related tasks only.

In a home environment It might be similar as well though, because it might be that some parents want to restrict what their children can run from the family computer. So again, requiring a password is a good thing in this instance.

> **Joseph Schwenker said:**
>  The point is, users should only have to deal with the packages that they care about: things that they can see, things that they use every day, and should not have to worry about mixing other weird things (that confuse them!) in with their regular applications.  Synaptic would also be available if they wanted to manage all of their packages at once.  So, this is my idea for Ubuntu.  What does everyone else think?


I think the package managers we have in Ubuntu are pretty easy to use even for a brand new user.
 
zipperback

---

### Post by Ginsly on 2010-01-31
I think the OP should take time to learn the Linux filesystem and directory structure before making suggestions it should be re written, along with permissions to make it easier to install software in a more OSX way. Aptitude, Synaptic, and all the rest, really aren't that difficult to use.

The repo's are designed in such a way to keep your system secure and free of virus's, and linux is secure because of the way it is designed. Period.
It is unfortunate however that the software you require is not up to date enough for your needs. But there are always other distributions, or compiling from source as the above person has suggested. Also, BTW, Wine has its own Ubuntu repo if the version in Karmic doesn't work for you.

---

### Post by k64 on 2010-01-31
There is the Ubuntu Software Center, which is a more detailed Synaptic that's easier to interpret. It currently replaces the "Applications > Add/Remove" window in Ubuntu 9.10 Karmic Koala, and is expected to replace Synaptic and Update Manager in Lucid Lynx (10.04 LTS, the next release slated for April). Here's a screenshot of it:

---

### Post by Joseph Schwenker on 2010-01-31
> **Ginsly said:**
> Also, BTW, Wine has its own Ubuntu repo if the version in Karmic doesn't work for you.

It doesn't matter what version in Karmic.  It will always have either terrible sound or no sound because of PulseAudio.

---

### Post by Khakilang on 2010-01-31
I find installation simple enough with the Software center. Instead going around looking for software and spend time to test I just look at the Software center and download what I like and if I don't like it I just remove it and its free. Thanks to GNU/Linux and Canonical that make it this way.

---

### Post by cariboo on 2010-01-31
There already is a place for self compiled software and scripts called /usr/local/bin. Another directory is /opt this is where various Google and Adobe plus other apps get automagically installed from the install scripts.

The one thing I would suggest is to spend some time learning your operating system, after all nobody was born knowing how to use a computer. Many people have spent years learning how to use Windows, why not do the same thing with a Linux distribution.

---

### Post by k64 on 2010-01-31
> **Joseph Schwenker said:**
> It doesn't matter what version in Karmic.  It will always have either terrible sound or no sound because of PulseAudio.

Here's my advice:

Personally, alpha testing Lucid since A1, I have to say it looks like Karmic, but fixes most of the flaws. PulseAudio is by far the most harrowing audio utility out there, I agree. That's because Pulse actually uses its own driver instead of ALSA. Personally, I find it much better than ALSA (it recognized my Creative SoundBlaster Audigy SE sound card without any issues, in contrast ALSA didn't). However, not everybody likes Pulse, because of its bugs.

If anything, you would have more luck with Pulse if you have a newer card. Otherwise, stick with ALSA.

However, back to Lucid. It works very diligently on both of my computers without any driver issues, with the exception of my TV tuner. If I had to say something, I say test out Lucid and see if it works. It is LTS, IMHO, and it has the ease of Software Center. Jaunty, in contrast, didn't.

I have to warn you, though, Software Center is quite buggy in Lucid. Crashed on me many times. If you can, wait until at least Beta 1, due out March 18th.

---

### Post by 3rdalbum on 2010-01-31
What you describe is:

a. A major, documented, unsolvable security problem on Mac OS X
b. Perfectly possible to implement on Ubuntu - but no application developers on Linux want to do this because they know what a problem it is.

---

### Post by 3rdalbum on 2010-01-31
> **Joseph Schwenker said:**
> Little gain?  It would simplify the entire Linux project!  No more confusion on how to install everyday applications, just drag and drop into your applications.  There would be no more .debs, which confuse users about where to uninstall the file from.  This system is simple.  Users would know where they put the file in the first place, and thus would know how to remove it.

Yeah? And what about daemons that you want to install? They can't just be dropped into some applications folder.

What about where precompiled binaries are not available, for instance on architectures other than i386 and amd64?

Sorry... Mac OS X has its own semi-official method of installing software, that is completely inappropriate for Linux. It's actually a holdover from the Mac OS 7 days before the Macintosh had protected memory, pre-emptive multitasking, or a multi-user system. It's a hack to implement on a modern operating system. Just forget the idea and move on; there are several well-known reasons why Windows and Linux-based developers don't adopt this method.

---

### Post by koenn on 2010-01-31
> **cariboo907 said:**
> There already is a place for self compiled software and scripts called /usr/local/bin. Another directory is /opt this is where various Google and Adobe plus other apps get automagically installed from the install scripts.

The one thing I would suggest is to spend some time learning your operating system, ...

> **Ginsly said:**
> I think the OP should take time to learn the Linux filesystem and directory structure before making suggestions it should be re written, a ...
That sums it up.

---

### Post by 3rdalbum on 2010-01-31
> **Joseph Schwenker said:**
> It doesn't matter what version in Karmic.  It will always have either terrible sound or no sound because of PulseAudio.

Let's stop the Pulseaudio hate, eh? It works very well here. As does OpenArena, incidentally (if you turn off OpenAL, which has caused problems since before Pulseaudio was in Ubuntu).

---

### Post by koenn on 2010-01-31
> **Joseph Schwenker said:**
> And if I upgraded to Karmic, then I would be whining about why WINE doesn't work, why OpenArena doesn't work, why audio in Blender doesn't work, why audio in Glest doesn't work, why audio in Nexuiz doesn't work, why audio in almost every single application DOESN'T WORK.  I would also be whining about why there is no volume control applet when I kill PulseAudio.  I tried Karmic.  PulseAudio sucks.  It's not my fault that I use a distribution of Ubuntu that ACTUALLY WORKS.  ....

so you propose to fix a problem regarding quality control / regression bugs by changing the directory tree, the file permission system, user rights, the mechanism to deliver and install software, ... everything *except* the actual problem.
Interesting approach.

---

### Post by SushiR on 2010-01-31
> **Joseph Schwenker said:**
> And if I upgraded to Karmic, then I would be whining about why WINE doesn't work, why OpenArena doesn't work, why audio in Blender doesn't work, why audio in Glest doesn't work, why audio in Nexuiz doesn't work, why audio in almost every single application DOESN'T WORK.  I would also be whining about why there is no volume control applet when I kill PulseAudio.  I tried Karmic.  PulseAudio sucks.  It's not my fault that I use a distribution of Ubuntu that ACTUALLY WORKS.  If the latest packages won't work in 9.10, I guess that 9.04 can't have them either, even though THEY WORK PERFECTLY IN JAUNTY.  I guess they just don't want to make Karmic look bad.

To be honest, I found your initial idea unacceptable, because a) it is pretty easy to install software in Ubuntu via Software Center, Add/Remove, synaptic, apt-get or aptitude (whatever fits you best), and b) because of security reasons as mentioned above.

Besides that, what let you think Pulse Audio would work better if you'd drop'n'install?

---

