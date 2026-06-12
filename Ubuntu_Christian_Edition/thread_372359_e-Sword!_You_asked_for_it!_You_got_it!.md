---
title: "e-Sword! You asked for it! You got it!"
date: 2007-02-28
forum: Ubuntu Christian Edition
---

### Post by mhancoc7 on 2007-02-28
One of the main requests for Ubuntu CE has been the inclusion of [e-Sword]("http://www.e-sword.net"). I did not think this would be easy to implement using wine since it requires so much user configuration to get it to work. Well, after successfully building the [Internet Explorer .deb]("http://www.ubuntuforums.org/showthread.php?t=370705&highlight=internet+explorer+.deb") package I decide to give [e-Sword]("http://www.e-sword.net/") another look.
 
I used the following thread along with some other bits and pieces of info on the web for the configuration.
[http://www.ubuntuforums.org/showthread.php?t=332566&highlight=e-sword](http://www.ubuntuforums.org/showthread.php?t=332566&highlight=e-sword)
 
I have also built an [e-Sword]("http://www.e-sword.net/") Module Manager to go along with it. It allows you to install many of the free modules available from the [e-Sword]("http://www.e-sword.net/") site with one click.
 
I have packaged the whole thing as a .deb package for a super easy installation. It should be considered "beta" for now. So USE AT YOUR OWN RISK!
 
I really would like to get some feedback on this. The more feedback I get the more likely that [e-Sword]("http://www.e-sword.net/") w/ the Module Manager will be included in the next release of Ubuntu CE.
 
You can download the latest version below.
**Edgy:**
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html)
**Dapper:**
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-dapper.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-dapper.html)
 
Once you have installed the .deb package you can find the [e-Sword]("http://www.e-sword.net/") and the Module Manager under Applications>Accessories in the main menu.
 
I hope you all enjoy and I am anxiously awaiting any and all feedback.
 
***Edit: I have removed the package pending response from Rick Meyers, the developer of e-Sword. There is some concern about the legality of the package.***
 
***Edit: The new e-Sword package is back up. I have contacted Rick Meyers and he has given his blessing with a few modifications. The program will now download the e-Sword setup program and run it automatically then configure it for Wine. :)***
 
***Edit: [COLOR=red]Be sure to disable dansguardian or at least modify your Banned Extensions to allow for .exe files. You can get the latest beta version of the dansguardian GUI at [http://www.ubuntuforums.org/showthread.php?t=355935](http://www.ubuntuforums.org/showthread.php?t=355935) .[/COLOR]***
 
***Edit: v1.2 now includes an alert****** to remind Ubuntu CE users to disable dansguardian before running e-Sword Installer.***
 
***Edit: v1.3 has been cleaned up even more. Now all the necessary M$ files are downloaded from the appropriate servers to avoid any legal issues with distributing them.***
 
 
***Edit: v1.4 fix for permissions error on internet connection test.***
 
***Edit: v1.5 added manual module install option and fixed the problem with the Module Installer closing after each module installation.***
 
***Edit: v1.6 has some significant changes. I found that the setup from previous versions did not allow other users to use e-Sword. This required the e-Sword Wine directory to be moved. So when you install the new version you will need to move the contents of the ".esword/******drive_c/Program Files/e-Sword******" folder in your home directory to "/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword". This change was neccesary to get the package ready for inclusion into Ubuntu CE.***
 
You can download the latest version below.
**Edgy:**
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html)
**Dapper:**
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-dapper.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-dapper.html)

God Bless, Jereme

---

### Post by shane2peru on 2007-02-28
Jereme,

That is great!!!  When I get my computer back, (it is in for repairs)  I'm going to have to give that a try!  Excellent!

Shane

---

### Post by mhancoc7 on 2007-02-28
> **shane2peru said:**
> Jereme,

That is great!!!  When I get my computer back, (it is in for repairs)  I'm going to have to give that a try!  Excellent!

Shane

Thanks, I am testing the Module Manager now. So far so good. I have found a few bugs, but they are all easy fixes.

I am starting to see what all the fuss was about. e-Sword is pretty awesome!

Let me know how it goes when you try it.

God Bless, Jereme

---

### Post by Beastboy26 on 2007-02-28
Jereme, 
      This is great!  I am downloading the .deb file now to install and test it out!  My mom always raves on how much she loves [e-sword]("http://www.e-sword.net/"), so this will give me a chance to compare it to the gnomesword and see if it is better.  Thanks again for all of your hard work, it is appreciated.

---

### Post by happypup on 2007-03-01
I do not have linux on all my computers yet and this is why e-sword!

e-sword has the strongs greek and hebrew and strongs numbers in kjv as well as hebrew greek and latin texts.

I am running Ubuntu 6.06 how do I install the .deb package EDIT: saw that you took the link down

---

### Post by mhancoc7 on 2007-03-02
> **happypup said:**
> I do not have linux on all my computers yet and this is why e-sword!

e-sword has the strongs greek and hebrew and strongs numbers in kjv as well as hebrew greek and latin texts.

I am running Ubuntu 6.06 how do I install the .deb package EDIT: saw that you took the link down

Well, sorry about that. :)

A new version is now up. You can read the OP for the most up to date details. 

You can download the latest version below.
[http://www.ubuntulabs.devubuntu.com/deb/esword-ubuntu_1.1_all.deb](http://www.ubuntulabs.devubuntu.com/deb/esword-ubuntu_1.1_all.deb)

The filesize is now only 1.2mb and will definitely be in the next release of Ubuntu CE!!!

I would love to hear your feedback.

God Bless, Jereme

---

### Post by stalker145 on 2007-03-02
Now **THAT** is &#973;&#1016;&#7952;&#344; cool!!

This is one of the very few things that I have missed about Winders and I couldn't see running a VM just for this one program. Thank you mhancoc7 for your hard work.

Be careful, all... I found out that it's not like Winders where you can run a bunch of the module installs at once and all will be well. With each install opening up E-Sword after completion, the ones that are still running seem to error out. Better to stay on the side of caution and patience and do them one at a time.

mhancoc7, I hate to ask more from you, but is there a way to make the module manager remain open and possibly return to the module list so that one can install another module after the previously selected one is completed? It's a small convenience (read laziness :lolflag: ) thing on my part since the manager was one of the most refined I've seen in a long time.

Also a question: is the module listing within the manager updated from somewhere or is it populated with only the items that were available when the .deb was created?

Thank you again for the excellent coding. I now have more ammunition to bring my friends over into the light ;)

---

### Post by mhancoc7 on 2007-03-02
> **stalker145 said:**
> Now **THAT** is &#973;&#1016;&#7952;&#344; cool!!

This is one of the very few things that I have missed about Winders and I couldn't see running a VM just for this one program. Thank you mhancoc7 for your hard work.

Be careful, all... I found out that it's not like Winders where you can run a bunch of the module installs at once and all will be well. With each install opening up E-Sword after completion, the ones that are still running seem to error out. Better to stay on the side of caution and patience and do them one at a time.

mhancoc7, I hate to ask more from you, but is there a way to make the module manager remain open and possibly return to the module list so that one can install another module after the previously selected one is completed? It's a small convenience (read laziness :lolflag: ) thing on my part since the manager was one of the most refined I've seen in a long time.

Also a question: is the module listing within the manager updated from somewhere or is it populated with only the items that were available when the .deb was created?

Thank you again for the excellent coding. I now have more ammunition to bring my friends over into the light ;)

Thanks so much!!

So did the install and everything work for you? Did the Module Manager work as well?

Yes, I am working to get the Module Manager to remain open. It is a pain to have reopen it. I have had some issues with getting it to stay open. For now I at least wanted to get everything functioning.

The items in the Module Manager are just ones that I selected. They do not get populated from the site. I plan to add more of the available modules in the future, again just trying to get everything working. :)

Please let me know what is working and what is not and any other comments or suggestions that you might have.

God Bless, Jereme

---

### Post by kingdomworker on 2007-03-02
Jeremy great job in getting e-sword for Ubuntu CE!! I know a ton of people will love having it on the system! 
I'm having a hard time installing it. The package downloads nice and the package shows it's self in the Module Manager under Applications>Accessories in the main menu. When I open up e-sword it start the install but when it gets to the window saying that it will ask you for the password I click Ok and then it's gone and I cant reopen it again. The e-sword module manger seems to be running fine and installing modules but I can't install or reopen e-sword it's self. I tried to reinstall the package and it worked fine up until that same window about the password and then crashes. Any ideas?

---

### Post by kingdomworker on 2007-03-02
I got e-sword up and running! My Bad I dansguardian blocking '.exe' files.:) Anyways it looks great, runs greats and, I'll be putting it on all our laptops for sure. Thanks for all your hard work Jeremy!

---

### Post by mhancoc7 on 2007-03-03
> **kingdomworker said:**
> I got e-sword up and running! My Bad I dansguardian blocking '.exe' files.:) Anyways it looks great, runs greats and, I'll be putting it on all our laptops for sure. Thanks for all your hard work Jeremy!

Thanks for letting me know that you got it working. I didn't even think about dansguardian blocking it. duh :) I will add that to the OP.

I really appreciate your kind words. Please keep me updated on your experience with it. What work, and what does not or any suggestions or comments. I am planning to include it in the next release of Ubuntu CE so I want to squash as many bugs as possible before then.

God Bless, Jereme

---

### Post by shane2peru on 2007-03-03
> **stalker145 said:**
> Now **THAT** is &#973;&#1016;&#7952;&#344; cool!!

This is one of the very few things that I have missed about Winders and I couldn't see running a VM just for this one program. Thank you mhancoc7 for your hard work.

Be careful, all... I found out that it's not like Winders where you can run a bunch of the module installs at once and all will be well. With each install opening up E-Sword after completion, the ones that are still running seem to error out. Better to stay on the side of caution and patience and do them one at a time.

mhancoc7, I hate to ask more from you, but is there a way to make the module manager remain open and possibly return to the module list so that one can install another module after the previously selected one is completed? It's a small convenience (read laziness :lolflag: ) thing on my part since the manager was one of the most refined I've seen in a long time.

Also a question: is the module listing within the manager updated from somewhere or is it populated with only the items that were available when the .deb was created?

Thank you again for the excellent coding. I now have more ammunition to bring my friends over into the light ;)


This is kind of a hack, but it will work great for getting your already installed modules into e-Sword.  If you want to transfer them from Windows to your Ubuntu e-Sword.  

In Windows, double click on my computer.  Next click on "Program Files"  now fine e-Sword and double click that folder.  Now you can see all the e-Sword files.  Copy all the .bbl files and .cmt .top .map .dct files and paste them somewhere you have access to with Ubuntu (a usb drive, or pendrive, or something a fat32 partition)  Now boot into Ubuntu.  In Ubuntu use Nautilus to open the location of the copied files from e-Sword.  Got to home in nautilus, and click **View -> see hidden files**  Now click on the .wine folder then "drive_c" now on Program Files and then e-Sword, and paste all those files into e-Sword.  It is a bit of an easier way to get your modules into your Ubuntu edition if you have a lot.  

  On the other hand keep trying the module manager to help Jereme debug it, and post your error messages so it will work great!  Another week and I am looking forward to giving the deb a try and seeing how it looks and works.  :)  

Shane

---

### Post by stalker145 on 2007-03-04
> **mhancoc7 said:**
> Thanks so much!!

So did the install and everything work for you? Did the Module Manager work as well?

Yes, I am working to get the Module Manager to remain open. It is a pain to have reopen it. I have had some issues with getting it to stay open. For now I at least wanted to get everything functioning.

The items in the Module Manager are just ones that I selected. They do not get populated from the site. I plan to add more of the available modules in the future, again just trying to get everything working. :)

Please let me know what is working and what is not and any other comments or suggestions that you might have.

God Bless, Jereme

Everything so far is working splendidly. As mentioned in my previous, they were just little nitpicks. I was very impressed with the polished appearance of the manager and everything  worked perfectly for me from the start. Thank you for making this for we users ;)

---

### Post by mhancoc7 on 2007-03-04
> **stalker145 said:**
> Everything so far is working splendidly. As mentioned in my previous, they were just little nitpicks. I was very impressed with the polished appearance of the manager and everything  worked perfectly for me from the start. Thank you for making this for we users ;)

Awesome! Glad to hear it. Thanks for your kind words and feedback.
Jereme

---

### Post by alaaji on 2007-03-05
Thanks for your hard work.  That is one program that I loved from Windows but could not get to work in Linux.  Good job!

---

### Post by mhancoc7 on 2007-03-06
I have just updated the .deb package.

The new v1.3 has been cleaned up even more. Now all the necessary M$ files are downloaded from the appropriate servers to avoid any legal issues with distributing them.

See OP for download link.

Jereme

---

### Post by twowheeler on 2007-03-06
> 
A connection to the server could not be made.  Please check your internet connection and try again.
:( 

Here is the detail from the terminal:
> 
--07:10:47--  [http://www.whatwouldjesusdownload.com/.online.key](http://www.whatwouldjesusdownload.com/.online.key)
           => `.online.key'
Resolving [www.whatwouldjesusdownload.com](www.whatwouldjesusdownload.com)... 70.86.39.210
Connecting to www.whatwouldjesusdownload.com|70.86.39.210|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32 [text/plain]
.online.key: Permission denied

Cannot write to `.online.key' (Permission denied).


Where is it trying to write .online.key?  Not sure why it has a permission problem, as it should just be in my home directory.  Any suggestions?

---

### Post by mhancoc7 on 2007-03-06
> **twowheeler said:**
> :( 

Here is the detail from the terminal:


Where is it trying to write .online.key?  Not sure why it has a permission problem, as it should just be in my home directory.  Any suggestions?

Opps, I just updated the .deb packge to v1.4 to fix this. Let me know how it goes.
Jereme

---

### Post by twowheeler on 2007-03-06
Hey, that works!  Thank you!

---

### Post by mhancoc7 on 2007-03-06
> **twowheeler said:**
> Hey, that works!  Thank you!

Great! Let me know how things work for you.
Jereme

---

### Post by gusjones on 2007-03-06
This is superb! and the first time Wine has worked properly for me with any application and what I like about it best of all is that you really feel you are running it as part of ubuntu and not through the WINE interface.

Keep up the great work.

many many thanks.

---

### Post by twowheeler on 2007-03-06
Hmm, well, I spoke too soon.  Upon start up I am getting:

> 
Error encountered opening bible file: c:\Program Files\e-sword\jps.bbl


One of these messages pops up for each downloaded file.  E-sword then starts but with no files open.  The bible files and commentaries etc. have been written into the e-sword folder, under ~/.esword/drive_c/Program Files.  The permissions are 644 with my user name as owner.  So I don't see anything wrong.

Any ideas?

---

### Post by mhancoc7 on 2007-03-06
> **twowheeler said:**
> Hmm, well, I spoke too soon.  Upon start up I am getting:



One of these messages pops up for each downloaded file.  E-sword then starts but with no files open.  The bible files and commentaries etc. have been written into the e-sword folder, under ~/.esword/drive_c/Program Files.  The permissions are 644 with my user name as owner.  So I don't see anything wrong.

Any ideas?

I am not sure what is going on there. I just re-tested the JPS module. It works great. You might try changing the permissions to 777 on the file and see if it works then. Mine is 644 and is working great with no errors.

You might also just try installing the module again. Is this the only module that you have had a problem with?

Jereme

---

### Post by wesley_of_course on 2007-03-06
Wesley here ;

   Jereme , does this install Wine ? , E-Sword has been on our computer since we found it ! I love it and find it very useful .  Thank You for your timely reply .

---

### Post by mhancoc7 on 2007-03-06
> **wesley_of_course said:**
> Wesley here ;

   Jereme , does this install Wine ? , E-Sword has been on our computer since we found it ! I love it and find it very useful .  Thank You for your timely reply .

It requires that Wine is installed. It will not however make any changes to your existing Wine configuration. The e-Sword installer uses its own Wine directory.

Let me know if you have any questions.

Jereme

---

### Post by twowheeler on 2007-03-06
> **mhancoc7 said:**
> I just re-tested the JPS module. It works great. You might try changing the permissions to 777 on the file and see if it works then. Mine is 644 and is working great with no errors.

Ok, did that, and no change in behavior.

> 
You might also just try installing the module again. Is this the only module that you have had a problem with?

No, all of my downloaded modules pop up the same error message when the program starts. I downloaded them again, and there is no change.  I have seven or eight modules now, and all give the error.

I opened up the Options --> Resource...  box in the menus, and it is pointing to c:\program files\e-sword\ in lower case.  Maybe it is case-insensitive 'cause it is windows?  I dunno.  Anyway it does not see any files at all.  I then tried to navigate through the directory tree to the correct directory, but it won't let me do that.  The OK button becomes grayed out when I get to the e-Sword (with the capital) directory.  So it is not seeing my files, but they are there.  Its very weird, I don't understand what is going on.  :confused:

---

### Post by eric_n_va on 2007-03-06
Hey guys.  I just installed e-sword and a module and it went off without a hitch.  If there is anything I could check on my machine that may help determine what's different or causing the problem on yours let me know...

BTW - awesome job on the installer Jeremy!  It looks super clean!  I haven't used e-sword before, but with all of the positive comments I just had to see for myself.

---

### Post by mhancoc7 on 2007-03-06
> **twowheeler said:**
> Ok, did that, and no change in behavior.


No, all of my downloaded modules pop up the same error message when the program starts. I downloaded them again, and there is no change.  I have seven or eight modules now, and all give the error.

I opened up the Options --> Resource...  box in the menus, and it is pointing to c:\program files\e-sword\ in lower case.  Maybe it is case-insensitive 'cause it is windows?  I dunno.  Anyway it does not see any files at all.  I then tried to navigate through the directory tree to the correct directory, but it won't let me do that.  The OK button becomes grayed out when I get to the e-Sword (with the capital) directory.  So it is not seeing my files, but they are there.  Its very weird, I don't understand what is going on.  :confused:

Strange? Did you use the default settings during the e-Sword setup? I would probably try to completely uninstall the .deb package in synaptic then reinstall it. Then start fresh.

Jereme

---

### Post by mhancoc7 on 2007-03-06
> **eric_n_va said:**
> Hey guys.  I just installed e-sword and a module and it went off without a hitch.  If there is anything I could check on my machine that may help determine what's different or causing the problem on yours let me know...

BTW - awesome job on the installer Jeremy!  It looks super clean!  I haven't used e-sword before, but with all of the positive comments I just had to see for myself.

Great! Thanks!

Just let me know how it works for you. If you find anything not working or if you have ideas for how it could be improved just let me know.

Jereme

---

### Post by twowheeler on 2007-03-06
What should be the user, group and permissions on the /usr/local/apps/esword4linux stuff?  Mine are all set to user=1000, group=dan.  I don't have a user 1000 and there is nobody in group dan.  Wondering if that could be the problem.

---

### Post by mhancoc7 on 2007-03-06
> **twowheeler said:**
> What should be the user, group and permissions on the /usr/local/apps/esword4linux stuff?  Mine are all set to user=1000, group=dan.  I don't have a user 1000 and there is nobody in group dan.  Wondering if that could be the problem.

They shoud be set to your username/group. Just to be sure are you using the latest version (v1.4)? Also have you tried to completely remove it and then reinstall?

Jereme

---

### Post by twowheeler on 2007-03-07
Yes to both questions, twice.  Here is the terminal output.

> 
dan@ubuntu:~/Desktop/Downloads$ sudo dpkg -r esword-ubuntu
(Reading database ... 147399 files and directories currently installed.)
Removing esword-ubuntu ...
dpkg - warning: while removing esword-ubuntu, directory `/usr/local' not empty s o not removed.
dan@ubuntu:~/Desktop/Downloads$ sudo dpkg -i esword-ubuntu_1.4_all.deb
Selecting previously deselected package esword-ubuntu.
(Reading database ... 147220 files and directories currently installed.)
Unpacking esword-ubuntu (from esword-ubuntu_1.4_all.deb) ...
Setting up esword-ubuntu (1.4) ...
dan@ubuntu:~/Desktop/Downloads$ ls -l /usr/local/apps
total 1
drwxr-xr-x 5 1000 dan 544 2007-03-07 07:12 esword4linux
dan@ubuntu:~/Desktop/Downloads$ ls -l /usr/local/apps/esword4linux
total 240
-rwxr-xr-x 1 1000 dan    384 2007-03-06 03:24 configure
-rwxr-xr-x 1 1000 dan    614 2007-03-06 19:57 dgmm_question
-rwxr-xr-x 1 1000 dan    559 2007-03-06 19:56 dg_question
-rwxr-xr-x 1 1000 dan    396 2007-03-06 03:24 esmm_first_run
drwxr-xr-x 2 1000 dan     80 2007-03-07 07:12 esword4linux
-rw-r--r-- 1 1000 dan  88659 2007-03-05 07:24 esword4linux-1.3.tar.gz
-rw-r--r-- 1 1000 dan    170 2007-03-06 03:21 esword4linux.desktop
-rw-r--r-- 1 1000 dan    188 2007-03-06 03:21 esword4linuxmm.desktop
drwxr-xr-x 9 1000 dan    288 2007-03-07 07:12 esword4linux_module_manager
-rw-r--r-- 1 1000 dan 106740 2007-03-05 07:23 esword4linux_module_manager-1.3.tar.gz
-rw-r--r-- 1 1000 dan   4741 2007-02-27 04:15 esword.png
-rwxr-xr-x 1 1000 dan   5215 2007-03-06 07:57 install
-rwxr-xr-x 1 1000 dan    150 2007-03-05 19:51 runesword
drwxr-xr-x 2 1000 dan     80 2007-03-07 07:12 winereg
dan@ubuntu:~/Desktop/Downloads$ sudo chown -R dan:users /usr/local/apps
dan@ubuntu:~/Desktop/Downloads$ ls -l /usr/local/apps/esword4linux
total 240
-rwxr-xr-x 1 dan users    384 2007-03-06 03:24 configure
-rwxr-xr-x 1 dan users    614 2007-03-06 19:57 dgmm_question
-rwxr-xr-x 1 dan users    559 2007-03-06 19:56 dg_question
-rwxr-xr-x 1 dan users    396 2007-03-06 03:24 esmm_first_run
drwxr-xr-x 2 dan users     80 2007-03-07 07:12 esword4linux
-rw-r--r-- 1 dan users  88659 2007-03-05 07:24 esword4linux-1.3.tar.gz
-rw-r--r-- 1 dan users    170 2007-03-06 03:21 esword4linux.desktop
-rw-r--r-- 1 dan users    188 2007-03-06 03:21 esword4linuxmm.desktop
drwxr-xr-x 9 dan users    288 2007-03-07 07:12 esword4linux_module_manager
-rw-r--r-- 1 dan users 106740 2007-03-05 07:23 esword4linux_module_manager-1.3.tar.gz
-rw-r--r-- 1 dan users   4741 2007-02-27 04:15 esword.png
-rwxr-xr-x 1 dan users   5215 2007-03-06 07:57 install
-rwxr-xr-x 1 dan users    150 2007-03-05 19:51 runesword
drwxr-xr-x 2 dan users     80 2007-03-07 07:12 winereg
dan@ubuntu:~/Desktop/Downloads$


As you can see I manually changed the owner of the /usr/local/apps tree.  I will try the user install again and let you know.

Edit: Ok, the re-install did not eliminate the errors.  It still cannot find the bible, dictionary, etc. files.  But they are there:

> 
dan@ubuntu:~$ ls -l .esword/drive_c/Program\ Files/e-Sword
total 28870
-rw-r--r-- 1 dan users    81920 2007-03-07 07:29 Bookmarks.lst
-rw-r--r-- 1 dan users    24309 2001-12-07 11:48 custom.dic
-rw-r--r-- 1 dan users    73728 2000-02-16 17:49 Does Our Shepherd Lose His Sheep.lst
-rwxr-xr-x 1 dan users  4956160 2007-01-01 08:09 e-Sword.exe
-rw-r--r-- 1 dan users   279241 2003-04-14 13:31 e-Sword.hlp
-rw-r--r-- 1 dan users     8591 2004-07-07 15:57 e-Sword.tip
-rw-r--r-- 1 dan users 14680064 2006-11-14 08:49 kjv+.bbl
-rw-r--r-- 1 dan users    19096 2006-12-21 13:01 License.pdf
-rw-r--r-- 1 dan users    94208 2007-03-07 07:29 markup.ovl
-rw-r--r-- 1 dan users    65863 2006-12-26 20:09 Readme.pdf
-rw-r--r-- 1 dan users   524339 2001-02-09 13:12 riched20.dll
-rw-r--r-- 1 dan users   237568 2005-02-08 10:19 RichEdit.ocx
-rw-r--r-- 1 dan users   204800 2006-12-30 13:59 robertson.har
-rw-r--r-- 1 dan users  5163008 2002-03-27 11:53 strong.dct
-rw-r--r-- 1 dan users  1331200 2007-03-07 07:29 study.not
-rw-r--r-- 1 dan users    86016 2007-03-07 07:29 topic.top
-rw-r--r-- 1 dan users  1344475 1999-09-17 06:44 vssp_ae.dic
-rw-r--r-- 1 dan users   342910 1999-08-30 11:44 vsth_ae.the
dan@ubuntu:~$



---

### Post by mhancoc7 on 2007-03-07
> **twowheeler said:**
> Yes to both questions, twice.  Here is the terminal output.


As you can see I manually changed the owner of the /usr/local/apps tree.  I will try the user install again and let you know.


Ok try this.

sudo apt-get remove esword-ubuntu
rm -rf /usr/local/apps/esword4linux/
rm $HOME/.esword

Now that should have removed everything to do with the installation.

Now double click on the .deb package and use the gdebi package installer to install esword-ubuntu. This is how I normally install .deb packages. This way we are doing it the same way. If it installs then we can see that there was a problem installing from the command line.

I am really stumped here so I am kind of grasping at straws.

Jereme

---

### Post by kingdomworker on 2007-03-07
twowheeler
Make sure dansguardian is off. I got a lot of weird stuff like that when I tried install e-sword with dasguardian on worked fine when it was off, that was with the 1.1v so I'll try the 1.4 and see what I get.
J

---

### Post by kingdomworker on 2007-03-07
I removed 1.1v and installed 1.4v with dansguardian running but letting .exe through. It seamed to work but after running the installer I got a window saying that there was a missing module .dll file type. But I have dansguardian set up to let .dll file through? I removed 1.4v and reinstalled it with dansgaurdian off and it ran and set up great!:) I would say that if your having any trouble installing e-Sword just double check that dansguarian is disabled.
Jereme, Great job everything is running good but I'm trying to install bibles from the e-sword site. No go? Have you tried and if so how did you get them install?
J

---

### Post by mhancoc7 on 2007-03-07
> **kingdomworker said:**
> I removed 1.1v and installed 1.4v with dansguardian running but letting .exe through. It seamed to work but after running the installer I got a window saying that there was a missing module .dll file type. But I have dansguardian set up to let .dll file through? I removed 1.4v and reinstalled it with dansgaurdian off and it ran and set up great!:) I would say that if your having any trouble installing e-Sword just double check that dansguarian is disabled.
Jereme, Great job everything is running good but I'm trying to install bibles from the e-sword site. No go? Have you tried and if so how did you get them install?
J

Thanks for letting me know how it is working for you.

Are you using the e-Sword Module Manager to install Bibles? If so what is happening?

Thanks, Jereme

---

### Post by gusjones on 2007-03-07
All of it is working fine for me.

The only thing I notice is that I have to keep relaunching the module manager before each additional module is installed - as someone mentioned earlier in the thread - no big deal really.

Where I have had problems with WINE before it tended to be because I had attempted install plus removal of WINE more than once. For esword I pretty much put on a clean WINE install from automatix2 before going straight to use your .deb by simply using the gui installer and not the command line.

Then I launched the emulated windows install and everything worked fine. A few tweaks such as increasing the Bible text size and then launching the module manager several times to include a few plugins - again no problems encountered.

I am running a pretty clean build of Ubuntu; not CE but an up to date Edgy Echt, not that that should make any difference. My main reason for jumping to esword was that gnomesword now will not install from synaptic for me due to an unresolved dependancy. Of course esword with all the extra plugins is loads better.

Don't know if my happy tale is of any use... <'())<<

GBY.

---

### Post by twowheeler on 2007-03-07
> **kingdomworker said:**
> twowheeler
Make sure dansguardian is off. I got a lot of weird stuff like that when I tried install e-sword with dasguardian on worked fine when it was off, that was with the 1.1v so I'll try the 1.4 and see what I get.
J

Yeah, no worries there, I never heard of dansguardian before arriving in this thread.  It is not installed.

But thanks for the thought.

---

### Post by twowheeler on 2007-03-07
> **mhancoc7 said:**
> Ok try this.

sudo apt-get remove esword-ubuntu
rm -rf /usr/local/apps/esword4linux/
rm $HOME/.esword

Now that should have removed everything to do with the installation.

Now double click on the .deb package and use the gdebi package installer to install esword-ubuntu. This is how I normally install .deb packages. This way we are doing it the same way. If it installs then we can see that there was a problem installing from the command line.


Actually I used gdebi the first couple of times, and only switched to the terminal so I could capture the output and post it. Removed the directories too. Makes no difference.

> 
I am really stumped here so I am kind of grasping at straws.


Me too.  But thank you for spending time on it, I really appreciate the attempt.

---

### Post by kingdomworker on 2007-03-07
> **mhancoc7 said:**
> Thanks for letting me know how it is working for you.

Are you using the e-Sword Module Manager to install Bibles? If so what is happening?

Thanks, Jereme

Jereme, the e-Sword Module Manager is running great and installs modules easy. I'm talking about other Bibles namely the pay for ones as well as ones in other languages. I can download them but when I goto run them in wine, it doesn't do anything? Not sure why it won't even come up to a setup or install screen in Wine?
J

---

### Post by mhancoc7 on 2007-03-07
> **kingdomworker said:**
> Jereme, the e-Sword Module Manager is running great and installs modules easy. I'm talking about other Bibles namely the pay for ones as well as ones in other languages. I can download them but when I goto run them in wine, it doesn't do anything? Not sure why it won't even come up to a setup or install screen in Wine?
J

Oh, ok. I plan to possible add the ability to install your own Bible modules in the Module Manager.

For now you can do this.

Put the YOURMODULE.exe file in the following directory.
/home/YOURUSERNAME/.esword/drive_c/Program Files/e-Sword/

Then run the following in a terminal

```
WINEPREFIX="$HOME/.esword" wine "$HOME/.esword/drive_c/Program Files/e-Sword/YOURMODULE.exe"
```

The e-Sword installation has its own dedicated Wine directory so the code above will install it to the correct directory.

Let me know if you have any questions. Also let me know how it goes.

Jereme

---

### Post by kingdomworker on 2007-03-07
Jereme,  worked great! Thanks for all the help. God Bless:) 
J

---

### Post by mhancoc7 on 2007-03-08
> **kingdomworker said:**
> Jereme,  worked great! Thanks for all the help. God Bless:) 
J

Great! Thanks for letting me know. I am working on the next version now. It will include the option to install modules from your hard drive.

Jereme

---

### Post by mhancoc7 on 2007-03-09
> **kingdomworker said:**
> Jereme, the e-Sword Module Manager is running great and installs modules easy. I'm talking about other Bibles namely the pay for ones as well as ones in other languages. I can download them but when I goto run them in wine, it doesn't do anything? Not sure why it won't even come up to a setup or install screen in Wine?
J
> **mhancoc7 said:**
> Oh, ok. I plan to possible add the ability to install your own Bible modules in the Module Manager.

For now you can do this.

Put the YOURMODULE.exe file in the following directory.
/home/YOURUSERNAME/.esword/drive_c/Program Files/e-Sword/

Then run the following in a terminal

```
WINEPREFIX="$HOME/.esword" wine "$HOME/.esword/drive_c/Program Files/e-Sword/YOURMODULE.exe"
```The e-Sword installation has its own dedicated Wine directory so the code above will install it to the correct directory.

Let me know if you have any questions. Also let me know how it goes.

Jereme

Ok, thanks to the discussion above I have made some changes to the Module Manager. The newest version (v1.5) now has an option to manually install modules locally. So if you have purchased one of the non-free modules from e-sword.net then you can easily install it with just a few clicks. The problem with the Module Manager closing after each module install has now been fixed. This makes it much easier to add all of the desired modules faster and without the hassle of opening the Module Manager again and again.

Thanks for all the feedback. Keep it coming!!

See OP for download link for latest version.

Jereme

---

### Post by kingdomworker on 2007-03-09
Jereme, Great job!!! It is 98% perfect:) ! The installer works great and it is so much faster to install modules now that the Module Manger stays open after installing a module. The only thing I can see that would make the Module Manger easier to use would be away to see which packages you have installed on your system. Gnome Sword just has a simple check mark next to the package if it's installed. This is a big plus when your setting up more then one more machine. Even if you left the package tab highlighted in the Module Manger after install would be a big help. Thanks again for all your hard work on this!
J

---

### Post by mhancoc7 on 2007-03-10
> **kingdomworker said:**
> Jereme, Great job!!! It is 98% perfect:) ! The installer works great and it is so much faster to install modules now that the Module Manger stays open after installing a module. The only thing I can see that would make the Module Manger easier to use would be away to see which packages you have installed on your system. Gnome Sword just has a simple check mark next to the package if it's installed. This is a big plus when your setting up more then one more machine. Even if you left the package tab highlighted in the Module Manger after install would be a big help. Thanks again for all your hard work on this!
J

Thank you very much for your feedback. You idea is a good one. I am not sure that the current design will allow for it, but you never know. :)

Did you try the new Manual Install option tab. I really like that addition since many e-Sword users have probably purchases some non-free modules.

God Bless, Jereme

---

### Post by mhancoc7 on 2007-03-11
Just released v1.6. There are some significant changes to the installation directory. See OP for full details. This change was needed to prepare the package for inclusion into Ubuntu CE.

Jereme

---

### Post by Hedghg88 on 2007-03-14
[B]This is great..... With the update to the install mamager, you can download the files that are not listed on it, and still install them without a problem, I did this with the "In His Steps" book I was reading when I had windows on my computer. Now I can finish the book, lol. Thanks again.

God Bless you.[/B]
You can find me at myspace with the same name.

---

### Post by mhancoc7 on 2007-03-14
> **Hedghg88 said:**
> [B]This is great..... With the update to the install mamager, you can download the files that are not listed on it, and still install them without a problem, I did this with the "In His Steps" book I was reading when I had windows on my computer. Now I can finish the book, lol. Thanks again.

God Bless you.[/B]
You can find me at myspace with the same name.

Thanks for letting me know how it is working for you. I appreciate your kind words and I hope you continue to enjoy it.

God Bless, Jereme

---

### Post by ronald_stall on 2007-03-14
mhancoc7 your link in OP to your newest release is broken.

I did find verision 1.6 here though thanks!

[http://www.ubuntulabs.devubuntu.com/deb/esword-ubuntu_1.6_all.deb](http://www.ubuntulabs.devubuntu.com/deb/esword-ubuntu_1.6_all.deb)

---

### Post by mhancoc7 on 2007-03-14
> **ronald_stall said:**
> mhancoc7 your link in OP to your newest release is broken.
 
I did find verision 1.6 here though thanks!
 
[http://www.ubuntulabs.devubuntu.com/deb/esword-ubuntu_1.6_all.deb](http://www.ubuntulabs.devubuntu.com/deb/esword-ubuntu_1.6_all.deb)
 
Thanks for letting me know. I have fixed the link.
Jereme

---

### Post by iMav on 2007-03-15
I run vanilla Ubuntu, but recently installed ies4linux (just v.6) and e-sword based on info and links from the UCE forum.  Was able to install my premium (pay version) NET module for e-sword as well without issue.  Thanks!

I'm a big GnomeSword fan, but it is nice to have e-sword easily available as well.

I'm currently in Iraq and have Ubuntu installed on my trusty ol' T23 (thinkpad).  I just pulled the trigger on a new X60s and hope to pick it up when I am on vacation home next month.  While I am home, I definitely plan on installing UCE on at least one machine to check it out.  :)

Keep up the good work!

---

### Post by mhancoc7 on 2007-03-15
> **iMav said:**
> I run vanilla Ubuntu, but recently installed ies4linux (just v.6) and e-sword based on info and links from the UCE forum.  Was able to install my premium (pay version) NET module for e-sword as well without issue.  Thanks!

I'm a big GnomeSword fan, but it is nice to have e-sword easily available as well.

I'm currently in Iraq and have Ubuntu installed on my trusty ol' T23 (thinkpad).  I just pulled the trigger on a new X60s and hope to pick it up when I am on vacation home next month.  While I am home, I definitely plan on installing UCE on at least one machine to check it out.  :)

Keep up the good work!

Awesome, thanks for letting me know how it worked for you.
God Bless, Jereme

---

### Post by tgrisier on 2007-03-16
This is fantastic!  Thanks a million

---

### Post by jonathonblake on 2007-03-16
> **kingdomworker said:**
> The only thing I can see that would make the Module Manger easier to use would be away to see which packages you have installed on your system. 

That is a feature that users of e-Sword on Windows have requested a plethora of times,  to no avail.  If Jereme provides it, that means that running e-Sword on Linux has features  that aren't available for Windows users --- which is a good thing.

> Gnome Sword just has a simple check mark next to the package if it's installed. This is a big plus when your setting up more then one more machine.

GnomeSword has a built-in utility to download and install new resources. e-Sword does  not.  There are both more resources, and more places from which one can download them, for e-Sword, than for GnomeSword.

xan

jonathon

---

### Post by kc1di on 2007-03-17
Thank you , great job and great program use it every day.
In Christ, 
David

---

### Post by vissfam on 2007-03-18
[FONT="Book Antiqua"][COLOR="DarkOrchid"]:popcorn: [/COLOR][/FONT] Greetings. 
I got the wine emulator to work fine for E-Sword, however it takes a long time for the modules to install, even though I moved them to the directory on the main drive. 

My next question is rather complex possibly, but I have a registered version of the Amplified Bible, bought legally, and wish to use it. Do I set it up the same way?

Also, does anyone have a clue how to set up Adobe GoLive in this? I have several versions and would love to abandon windows completely if I can get Golive to work. I have all the versions up to CS as well as a registered copy of menumachine. 

Ken

---

### Post by mhancoc7 on 2007-03-18
> **vissfam said:**
> [FONT=Book Antiqua][COLOR=DarkOrchid]:popcorn: [/COLOR][/FONT] Greetings. 
I got the wine emulator to work fine for E-Sword, however it takes a long time for the modules to install, even though I moved them to the directory on the main drive. 

My next question is rather complex possibly, but I have a registered version of the Amplified Bible, bought legally, and wish to use it. Do I set it up the same way?

Also, does anyone have a clue how to set up Adobe GoLive in this? I have several versions and would love to abandon windows completely if I can get Golive to work. I have all the versions up to CS as well as a registered copy of menumachine. 

Ken

Are you using the e-Sword Installer available here?
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html)

If not I would suggest you give it a try. As for your purchased modules. You can simply move the .bbl file(s) to your e-Sword directory. Then when you run e-Sword it should recongnize them.

God Bless, Jereme

---

### Post by Billy McCann on 2007-03-27
Great work, Jereme.  Just installed and am perusing through e-Sword.  It was extremely simply to setup.  Just keep clicking OK. ;)  

On another note ...

Does anyone know how to search the Greek texts?  For instance, say I wanted to find every usage of the phrase "en XristW".  How would I go about doing that?

---

### Post by Sir Frederic on 2007-03-27
e-Sword on Linux is now pretty much as perfect as a wine program can be - thanks very much.

Now to give us even more ease of use than the windows users maybe if you could have the option of adding a .bbl and also whatever extension the other modules have straight to the e-Sword directory via the Module Manager.

So for example you open the Module Manager and select the 'Manual install' there could be one more option. This should be something like 'install bare module' or 'add module without installer'

I hope my suggestions are useful.

In Christ, 
         Caleb.

P.S. Printing doesn't work and it used to when I used crossover office but that's no big issue.

---

### Post by shane2peru on 2007-03-27
> **Sir Frederic said:**
> e-Sword on Linux is now pretty much as perfect as a wine program can be - thanks very much.

Now to give us even more ease of use than the windows users maybe if you could have the option of adding a .bbl and also whatever extension the other modules have straight to the e-Sword directory via the Module Manager.

So for example you open the Module Manager and select the 'Manual install' there could be one more option. This should be something like 'install bare module' or 'add module without installer'

I hope my suggestions are useful.

In Christ, 
         Caleb.

P.S. Printing doesn't work and it used to when I used crossover office but that's no big issue.

This is a good suggestion.  I don't know how difficult it would be.  Here are a list of the extensions:
.bbl
.cmt
.dct
.top
.map
.dev

These are all that I noticed, and I have a pretty comprehensive collection of e-Sword files.  Also there are many user made modules that have made there own installers (like one I made) and it is an .exe file, that automagically extracts the file to 'C:\Program Files\e-Sword\'  It does ask if that is where you want to install it first, and I don't know if there is any kind of provision for that.  I'm still waiting on my laptop to be repaired, so I have yet to try this very nice installer!  I'm anxious to give it a whirl.

Shane

---

### Post by Sir Frederic on 2007-03-28
Hi Shane, if wine can run your installer than you're set as the module manager makes your installer think that the e-Sword directory in Linux is C:/Program Files/e-Sword.
That is so long as you install it with the 'Manual Install' tab in the settings manager.

---

### Post by mhancoc7 on 2007-03-29
> **Billy McCann said:**
> Great work, Jereme.  Just installed and am perusing through e-Sword.  It was extremely simply to setup.  Just keep clicking OK. ;)  

Thank you very much! I am very glad to hear that you are enjoying it.

> **Sir Frederic said:**
> e-Sword on Linux is now pretty much as perfect as a wine program can be - thanks very much.

Now to give us even more ease of use than the windows users maybe if you could have the option of adding a .bbl and also whatever extension the other modules have straight to the e-Sword directory via the Module Manager.

So for example you open the Module Manager and select the 'Manual install' there could be one more option. This should be something like 'install bare module' or 'add module without installer'

I hope my suggestions are useful.

In Christ, 
         Caleb.

P.S. Printing doesn't work and it used to when I used crossover office but that's no big issue.

Thanks for your kind words and suggestions. I am actually planning on adding that option to the next release of the e-Sword Installer. I should be fairly easy.

Also thanks for letting me know about the printing issue. I will look into it.


> **shane2peru said:**
> This is a good suggestion.  I don't know how difficult it would be.  Here are a list of the extensions:
.bbl
.cmt
.dct
.top
.map
.dev

These are all that I noticed, and I have a pretty comprehensive collection of e-Sword files.  Also there are many user made modules that have made there own installers (like one I made) and it is an .exe file, that automagically extracts the file to 'C:\Program Files\e-Sword\'  It does ask if that is where you want to install it first, and I don't know if there is any kind of provision for that.  I'm still waiting on my laptop to be repaired, so I have yet to try this very nice installer!  I'm anxious to give it a whirl.

Shane

Thanks for the list. That will be very helpful when I get started with this addition. Your .exe installer should work just fine with the current Module Manager.

God Bless, Jereme

---

### Post by Sir Frederic on 2007-03-29
Thanks Jereme!
You guys are wonderful. You listen and talk civilly. I like that.

---

### Post by lwalper on 2007-03-30
WOW!! That installation was FLAWLESS. I'm a Linux (Ubuntu) nooby idiot and have been struggling to get basic needed software / hardware to run for the past couple of weeks. Thankfully there have been numerous knights on white horses who have come to my rescue, but this, **THIS** installation was perfect. Other developers should come to your house for lessons.

---

### Post by mhancoc7 on 2007-03-30
> **lwalper said:**
> WOW!! That installation was FLAWLESS. I'm a Linux (Ubuntu) nooby idiot and have been struggling to get basic needed software / hardware to run for the past couple of weeks. Thankfully there have been numerous knights on white horses who have come to my rescue, but this, **THIS** installation was perfect. Other developers should come to your house for lessons.

Thanks very much. I am so glad that you have had success with it. 

I assure you that I am not that good at developing. I just keep trying until something works. :)

Jereme

---

### Post by Livin4him on 2007-03-30
none of my (.bb .cmt .dct .top .map .dev) work help!!!

---

### Post by Sir Frederic on 2007-03-31
> **Livin4him said:**
> none of my (.bb .cmt .dct .top .map .dev) work help!!!

You need to place them manually in the e-Sword installation folder.
This is placed here:
/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword

now sometimes it is hard to navigate here due to account restrictions.

The way I get around this is to type in the Terminal (Applications->Accessories->Terminal)
"sudo nautilus" 

It will ask for your password. Give it.

press the up button in Nautilus (the file manager) to get to the base of the file system.

You should see only 3 folders thats because the rest are hidden.
Press Ctrl+H          This shows the hidden files.

now navigate to /usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword

Copy and paste your modules into this directory.


In Christ, Caleb.

p.s. I assume you are new to linux/ubuntu. you may not be but I write it as simple as possible anyway.

---

### Post by shane2peru on 2007-03-31
Jereme,

Well, I just got my Linux computer back.  Love the e-Sword installer, that is incredible!!!  Runs very nice.  I did notice that now, however anytime I want to install a windows program, my wine has been modified, and no longer in the same spot it was.  Not a big deal on a new setup, buy may want to include a warning about that in case someone already has wine installed.  Really nice installer though, and excellent for newbies!!!  I believe this adds super extra value to UCE!  Excellent!  Keep up the good work.  
Consequently I now have 2 working editions of e-Sword, I was comparing them to see if there were any differences.  I noticed you got the maps working too, wonderfull, plus the strongs numbers pop ups, excellent!  I noticed too that my installation is a little darker gray in color as far as the window, and the deb installation is a little lighter in gray.  That was wierd, but not a problem.  I also installed another Bible program that I already had installed too, [The Word]("http://theword.gr") to see if it worked better, and it does work better with your wine installation!  Wow, a double plus for me.  How can I see what was done with that wine installation?  It is a excellent work.

Shane

> **Sir Frederic said:**
> You need to place them manually in the e-Sword installation folder.
This is placed here:
/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword

now sometimes it is hard to navigate here due to account restrictions.

The way I get around this is to type in the Terminal (Applications->Accessories->Terminal)
"sudo nautilus" 

It will ask for your password. Give it.

press the up button in Nautilus (the file manager) to get to the base of the file system.

You should see only 3 folders thats because the rest are hidden.
Press Ctrl+H          This shows the hidden files.

now navigate to /usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword

Copy and paste your modules into this directory.


In Christ, Caleb.

p.s. I assume you are new to linux/ubuntu. you may not be but I write it as simple as possible anyway.

Thanks Caleb!  This was fixing to be my next question.  I just keep a back up file of all my e-Sword modules and copy them instead of installing them all.  Plus I have many user made modules.  

Shane

---

### Post by mhancoc7 on 2007-03-31
> **shane2peru said:**
> Jereme,

Well, I just got my Linux computer back.  Love the e-Sword installer, that is incredible!!!  Runs very nice.  I did notice that now, however anytime I want to install a windows program, my wine has been modified, and no longer in the same spot it was.  Not a big deal on a new setup, buy may want to include a warning about that in case someone already has wine installed.  Really nice installer though, and excellent for newbies!!!  I believe this adds super extra value to UCE!  Excellent!  Keep up the good work.  
Consequently I now have 2 working editions of e-Sword, I was comparing them to see if there were any differences.  I noticed you got the maps working too, wonderfull, plus the strongs numbers pop ups, excellent!  I noticed too that my installation is a little darker gray in color as far as the window, and the deb installation is a little lighter in gray.  That was wierd, but not a problem.  I also installed another Bible program that I already had installed too, [The Word]("http://theword.gr") to see if it worked better, and it does work better with your wine installation!  Wow, a double plus for me.  How can I see what was done with that wine installation?  It is a excellent work.


Thanks so much for your kind words. I am glad that you are enjoying it. The e-Sword Installer should not have any affect on your default wine installation. The e-Sword Installer creates a dedicated wine directory for e-Sword. So I am not sure what is going on there. Could you give me a bit more details of your problem.

The .deb installer uses your system theme. The actual e-Sword program is using a Ubuntu-ish theme set to look like Edgy. It is not quite perfect, but I thought it looked better than the default wine look.

You can look at the all of the scripts that are used to configure the dedicated wine directory in the /usr/local/apps/esword4linux directory. To look at the actual e-Sword wine directory open the /usr/local/apps/esword4linux set nautilus to Show Hidden files. Then open the .esword folder.

I noticed that you sayed you installed The Word. Did you actually install it to the e-Sword wine directory using the WINEPREFIX= code?

Let me know if you have any questions or suggestions.

God Bless, Jereme

---

### Post by shane2peru on 2007-04-01
> **mhancoc7 said:**
> Thanks so much for your kind words. I am glad that you are enjoying it. The e-Sword Installer should not have any affect on your default wine installation. The e-Sword Installer creates a dedicated wine directory for e-Sword. So I am not sure what is going on there. Could you give me a bit more details of your problem.

The .deb installer uses your system theme. The actual e-Sword program is using a Ubuntu-ish theme set to look like Edgy. It is not quite perfect, but I thought it looked better than the default wine look.

You can look at the all of the scripts that are used to configure the dedicated wine directory in the /usr/local/apps/esword4linux directory. To look at the actual e-Sword wine directory open the /usr/local/apps/esword4linux set nautilus to Show Hidden files. Then open the .esword folder.

I noticed that you sayed you installed The Word. Did you actually install it to the e-Sword wine directory using the WINEPREFIX= code?

Let me know if you have any questions or suggestions.

God Bless, Jereme

Jereme,

No, no problem.  I thought it did, but it was my imagination.  All works great.  Thanks!  I used it to re-setup my new computer, and just copied all my modules into the directory.  Thanks again.

Shane

---

### Post by skooge on 2007-04-02
Does one need Ubuntu CE to install e-sword, or will it work on dapper drake?

---

### Post by mhancoc7 on 2007-04-02
> **skooge said:**
> Does one need Ubuntu CE to install e-sword, or will it work on dapper drake?

You do not have to run Ubuntu CE to have the e-Sword Installer.

See: [http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-dapper.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-dapper.html)

Jereme

---

### Post by Huggy on 2007-04-02
I have installed the e-sword and even a couple of Bibles, but everytime I click on the e-sword button to run it...nothing happens. What can I do to fix this problem? E-sword was the only thing keeping me on Windows.

---

### Post by mhancoc7 on 2007-04-02
> **Huggy said:**
> I have installed the e-sword and even a couple of Bibles, but everytime I click on the e-sword button to run it...nothing happens. What can I do to fix this problem? E-sword was the only thing keeping me on Windows.

Are you using e-Sword in a language other than English? If so there is an issue with the path to the e-Sword exe file. Let me know if this is the case and I can help you fix it.

I will put together a post to address this as soon as I get a chance.

God Bless, Jereme

---

### Post by Huggy on 2007-04-02
Nope it's in all english. Can I send you any files so you might be able to see what's going on?

---

### Post by mhancoc7 on 2007-04-02
> **Huggy said:**
> Nope it's in all english. Can I send you any files so you might be able to see what's going on?

Ok, try this and post the terminal output.

Open Terminal
Run Code Below:

```
/usr/local/apps/esword4linux/./dg_question
```

Jereme

---

### Post by tgrisier on 2007-04-17
Don't know what went wrong, but after I upgraded to feisty this is what I get.

Any suggestions as to a fix?

---

### Post by mhancoc7 on 2007-04-17
What version of wine are you using?

This should be fixed with the latest wine release.

Jereme

---

### Post by tgrisier on 2007-04-17
> **mhancoc7 said:**
> What version of wine are you using?

This should be fixed with the latest wine release.

Jereme



It says 0.9.35

---

### Post by shane2peru on 2007-04-17
> **tgrisier said:**
> Don't know what went wrong, but after I upgraded to feisty this is what I get.

Any suggestions as to a fix?

I also upgraded to Fiesty, and mine works fine.  I'm using wine version: wine-0.9.34.  Maybe try disabling your Beryl and see if that fixes it.  Did you have beryl running before the upgrade?  Beryl didn't agree with my adesklets and they displayed wrong.  run this in a terminal and see if there are any errors that you can post:
```
wine /usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword/e-Sword.exe 
```  Just run it and then close it and paste the results from the terminal here, that will enable us to help you a little better too.  

Shane

---

### Post by tgrisier on 2007-04-17
> **shane2peru said:**
> I also upgraded to Fiesty, and mine works fine.  I'm using wine version: wine-0.9.34.  Maybe try disabling your Beryl and see if that fixes it.  Did you have beryl running before the upgrade?  Beryl didn't agree with my adesklets and they displayed wrong.  run this in a terminal and see if there are any errors that you can post:
```
wine /usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword/e-Sword.exe 
```  Just run it and then close it and paste the results from the terminal here, that will enable us to help you a little better too.  

Shane



Well, I disabled Beryl and it still did it.  So then I ran the command as you suggested and this is what it returned:

tony@tony-desktop:~$ wine /usr/local/apps/esword4linux/.esword/drive_c/Program\ Files/e-Sword/e-Sword.exe
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\usr\\local\\apps\\esword4linux\\.esword\\drive_c\\Program Files\\e-Sword\\e-Sword.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\usr\\local\\apps\\esword4linux\\.esword\\drive_c\\Program Files\\e-Sword\\e-Sword.exe" failed, status c0000135
tony@tony-desktop:~$


Edit:  I forgot to add that Esword was running alright with Beryl before my upgrade to Feisty. 

Edit 2:  Kind of off-topic but I see from your web page that your home church is in Massillon.  I'm only a couple of hours away from there in extreme northwest Ohio (about 50 miles west of Toledo).

---

### Post by shane2peru on 2007-04-17
> **tgrisier said:**
> Well, I disabled Beryl and it still did it.  So then I ran the command as you suggested and this is what it returned:

tony@tony-desktop:~$ wine /usr/local/apps/esword4linux/.esword/drive_c/Program\ Files/e-Sword/e-Sword.exe
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\usr\\local\\apps\\esword4linux\\.esword\\drive_c\\Program Files\\e-Sword\\e-Sword.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\usr\\local\\apps\\esword4linux\\.esword\\drive_c\\Program Files\\e-Sword\\e-Sword.exe" failed, status c0000135
tony@tony-desktop:~$
My guess is that you are going to need to find MSVBVM60.DLL and put it in this folder
**/usr/local/apps/esword4linux/.esword/drive_c/windows/system32/**  That is my guess.  I would try and re-install e-Sword by grabbing the deb for edgy and running it.  It may not work since it was not developed for Fiesty, but it is worth a try.

> **tgrisier said:**
> 
Edit 2:  Kind of off-topic but I see from your web page that your home church is in Massillon.  I'm only a couple of hours away from there in extreme northwest Ohio (about 50 miles west of Toledo).
I know that territory rather well, we go past Toledo all the time heading to MI when we are in the USA.  Maybe some day we will cross paths.  :)

Shane

---

### Post by tgrisier on 2007-04-17
> **shane2peru said:**
> My guess is that you are going to need to find MSVBVM60.DLL and put it in this folder
**/usr/local/apps/esword4linux/.esword/drive_c/windows/system32/**  That is my guess.  I would try and re-install e-Sword by grabbing the deb for edgy and running it.  It may not work since it was not developed for Fiesty, but it is worth a try.


I know that territory rather well, we go past Toledo all the time heading to MI when we are in the USA.  Maybe some day we will cross paths.  :)

Shane


hmmm, tried it and it didn't work.  One thing I have noticed is that when I go to the Bible Font preferences there are no fonts available.

---

### Post by mhancoc7 on 2007-04-17
This sounds exactly like the issue I had in Edgy when wine updated to 0.9.34. All was fixed with 0.9.35. I will have to keep an eye on this.

Jereme

---

### Post by shane2peru on 2007-04-17
> **tgrisier said:**
> hmmm, tried it and it didn't work.  One thing I have noticed is that when I go to the Bible Font preferences there are no fonts available.

ok, that isn't good.  The next thing I would do is grab the deb and give that a whirl.  That could do 1 of three things.  1.  Fix it!  We hope.  2.  Break it (beyond repair, we aren't wanting this)  or 3.  Could leave you in the same situation (no worse or better).  Let me know if you want to try that, if not, I will have to think on it a bit.  I'm not a programmer, just like computers and am proficient at using them.

Shane

---

### Post by tgrisier on 2007-04-18
> **shane2peru said:**
> ok, that isn't good.  The next thing I would do is grab the deb and give that a whirl.  That could do 1 of three things.  1.  Fix it!  We hope.  2.  Break it (beyond repair, we aren't wanting this)  or 3.  Could leave you in the same situation (no worse or better).  Let me know if you want to try that, if not, I will have to think on it a bit.  I'm not a programmer, just like computers and am proficient at using them.

Shane


Well, I've installed using the .deb package and by downloading the install directly from esword.net and both result in the problem which leaves me to think that this is a Feisty problem. Especially since E-sword worked without flaw in Edgy.

Tony

---

### Post by shane2peru on 2007-04-18
Tony,

   Could very well be a fiesty problem.  It is just odd that it works fine on my machine.  I got one more idea.  If you are wanting to give it a try.  What happens on a re-install it is overwrites files, but I'm not sure it overwrites all the config files.  It usually only creates them when they are not there, and then uses them if they are not there.  (This is not factual, just my speculation).  So here is what I'm thinking.  We are going to rename the folder so that  it is not recognized by the installer as existing and it sets up a new setup brand new.  That will replace all the files and give you a truly new installation.  In the terminal paste this:
```

sudo mv /user/local/apps/esword4linux /user/local/apps/eswordbackup

```
This will rename that folder to eswordbackup.  Next with the deb, we will want to re-install e-Sword again.  This should create a new folder in the same location to install e-Sword.  If this doesn't fix the problem than we have a problem with Fiesty.  Which still boggles my mind because mine worked fine.  

Shane

---

### Post by tgrisier on 2007-04-18
> **shane2peru said:**
> Tony,

   Could very well be a fiesty problem.  It is just odd that it works fine on my machine.  I got one more idea.  If you are wanting to give it a try.  What happens on a re-install it is overwrites files, but I'm not sure it overwrites all the config files.  It usually only creates them when they are not there, and then uses them if they are not there.  (This is not factual, just my speculation).  So here is what I'm thinking.  We are going to rename the folder so that  it is not recognized by the installer as existing and it sets up a new setup brand new.  That will replace all the files and give you a truly new installation.  In the terminal paste this:
```

sudo mv /user/local/apps/esword4linux /user/local/apps/eswordbackup

```This will rename that folder to eswordbackup.  Next with the deb, we will want to re-install e-Sword again.  This should create a new folder in the same location to install e-Sword.  If this doesn't fix the problem than we have a problem with Fiesty.  Which still boggles my mind because mine worked fine.  

Shane


Still a no-go.  I guess I'll have to stick with GnomeSword although Esword is much better.

What I find really odd is that I can set the font in all categories except the Bible.  Really really odd.


EDIT:  Well what do you know, I got it working!!!  I had to go to [www.winehq.com](www.winehq.com) and download version 0.9.3.5 for Feisty.  Once I installed it Esword ran like a champ!

---

### Post by shane2peru on 2007-04-18
> **tgrisier said:**
> Still a no-go.  I guess I'll have to stick with GnomeSword although Esword is much better.

What I find really odd is that I can set the font in all categories except the Bible.  Really really odd.

Ok, if your not tired of this yet, I have yet one more suggestion.  Try installing it outside of the deb.  First I would in the terminal ```
sudo aptitude purge wine
```  If you don't use it for other things.  If you use it for other things, you may not want to do that.  This should get rid of everything.  Then ```
sudo apt-get install wine
```  This will re-setup wine for you to make it a clean installation, then you can follow this [guide here]("http://ubuntuforums.org/showthread.php?t=332566&highlight=e-sword") for installing e-Sword out side of the deb file.  It is a how to that I wrote.  That is my last suggestion honest.  If that don't work it is certainly a Fiesty problem.  I'm hoping not though, or a wine problem.  I wish I knew what the problem was.  

Shane

---

### Post by tgrisier on 2007-04-18
> **shane2peru said:**
> Ok, if your not tired of this yet, I have yet one more suggestion.  Try installing it outside of the deb.  First I would in the terminal ```
sudo aptitude purge wine
```  If you don't use it for other things.  If you use it for other things, you may not want to do that.  This should get rid of everything.  Then ```
sudo apt-get install wine
```  This will re-setup wine for you to make it a clean installation, then you can follow this [guide here]("http://ubuntuforums.org/showthread.php?t=332566&highlight=e-sword") for installing e-Sword out side of the deb file.  It is a how to that I wrote.  That is my last suggestion honest.  If that don't work it is certainly a Fiesty problem.  I'm hoping not though, or a wine problem.  I wish I knew what the problem was.  

Shane



Thanks for all of your help.  Installing the Feisty version of Wine did the trick. :)

---

### Post by shane2peru on 2007-04-18
> **tgrisier said:**
> Thanks for all of your help.  Installing the Feisty version of Wine did the trick. :)

Hey, glad we got it.  Does the other e-Sword work the one that was installed via the deb?  I don't know if that uses the wine that is already installed and just configures it, or if it installs another wine.  Any rate glad we got it running.

Shane

---

### Post by tgrisier on 2007-04-18
> **shane2peru said:**
> Hey, glad we got it.  Does the other e-Sword work the one that was installed via the deb?  I don't know if that uses the wine that is already installed and just configures it, or if it installs another wine.  Any rate glad we got it running.

Shane



Yeah, the Esword that I'm running now is the .deb install.

---

### Post by Bodizzle on 2007-04-18
I was able to install e-sword but the text is unreadable.  Has this happened to anyone else.

Brett

[http://www.mathinfo.net/files/themes/screenshot3.png]("http://www.mathinfo.net/files/themes/screenshot3.png")

---

### Post by tgrisier on 2007-04-18
> **Bodizzle said:**
> I was able to install e-sword but the text is unreadable.  Has this happened to anyone else.

Brett

[http://www.mathinfo.net/files/themes/screenshot3.png](http://www.mathinfo.net/files/themes/screenshot3.png)


I had to chuckle when I saw your screen shot because that is the exact problem I just overcame today.  

The way I solved it was to go to [this link]("http://wine.budgetdedicated.com/archive/index.html") and install the Feisty version of 0.9.3.5

Let me know how it turns out.

---

### Post by shane2peru on 2007-04-18
> **tgrisier said:**
> Yeah, the Esword that I'm running now is the .deb install.

OK, great, so it is just a matter of uninstalling and installing wine.  Or better said, purging wine and then re-installing it.  That is good, makes further fixes easier.

Shane

---

### Post by Bodizzle on 2007-04-19
Since I am still fairly new to linux, how do I install the updated version?

Brett

---

### Post by Bodizzle on 2007-04-19
Nevermind, I figured it out and it is working fine now.  

Brett

---

### Post by markupstart on 2007-04-19
Flawless installer, it worked great!

---

### Post by tgrisier on 2007-04-19
> **shane2peru said:**
> OK, great, so it is just a matter of uninstalling and installing wine.  Or better said, purging wine and then re-installing it.  That is good, makes further fixes easier.

Shane



Actually I didn't purge the existing wine installation, I just installed the Feisty version over it.

---

### Post by tgrisier on 2007-04-19
> **markupstart said:**
> Flawless installer, it worked great!

Fantastic, glad it worked for you too!

---

### Post by shane2peru on 2007-04-19
> **tgrisier said:**
> Actually I didn't purge the existing wine installation, I just installed the Feisty version over it.

Even easier then.  :)

Shane

---

### Post by tekguy on 2007-04-28
Excellent job. I just ran the 1.6 installer on my Feisty install. Went very smooth and works great! Thanks for this package. Love the module manager as well.

---

### Post by girlfreddy on 2007-05-14
Sweet! Thanks so much. All works great.

---

### Post by cwmoser on 2007-05-25
I still have no words showing in eSword.  I tried the downgrade to Wine - the Feisty version - still no joy.

I tried setting the Bible Font - nothing.

Any other setting?

Carl

---

### Post by mhancoc7 on 2007-05-25
> **cwmoser said:**
> I still have no words showing in eSword.  I tried the downgrade to Wine - the Feisty version - still no joy.

I tried setting the Bible Font - nothing.

Any other setting?

Carl

I am not sure why you are having this issue. It works great for me with the latest version of Wine in Feisty.

Jereme

---

### Post by shane2peru on 2007-05-25
> **cwmoser said:**
> I still have no words showing in eSword.  I tried the downgrade to Wine - the Feisty version - still no joy.

I tried setting the Bible Font - nothing.

Any other setting?

Carl

Carl,

Sorry to hear about the problem try purging wine and re-installing it.  Or better yet in a terminal type:
```
/usr/local/apps/esword4linux/runesword
```  let it open up and then open a Bible and passage and then exit out of the program.  Paste the results from the terminal here and we will see what we can work up.

Shane

---

### Post by david_kt on 2007-05-26
> **cwmoser said:**
> I still have no words showing in eSword.  I tried the downgrade to Wine - the Feisty version - still no joy.

I tried setting the Bible Font - nothing.

Any other setting?

Carl

You could try to install using below installation method, should run on any ubuntu version or distro with wine. 

[http://ubuntuforums.org/showpost.php?p=2418830&postcount=1](http://ubuntuforums.org/showpost.php?p=2418830&postcount=1)

DK

---

### Post by shane2peru on 2007-05-26
> **david_kt said:**
> You could try to install using below installation method, should run on any ubuntu version or distro with wine. 

[http://ubuntuforums.org/showpost.php?p=2418830&postcount=1](http://ubuntuforums.org/showpost.php?p=2418830&postcount=1)

DK

This method can be used, however if you have other programs you run in wine I found that installing the riched20.dll messed up all my other applications that I used in wine.  If e-Sword is the only application you run in wine than by all means go for it.  :)

Shane

---

### Post by david_kt on 2007-05-27
> **shane2peru said:**
> This method can be used, however if you have other programs you run in wine I found that installing the riched20.dll messed up all my other applications that I used in wine.  If e-Sword is the only application you run in wine than by all means go for it.  :)

Shane

Actually it is easy to install it in separate bottle for each windows application so that it will not affect each other. To help those that do not know how to install in separate bottle, I have edited this [how to ]("http://ubuntuforums.org/showpost.php...30&postcount=1")to use separate bottle (.wine_Esword) so that installation of Esword wll not affect default .wine directory.

If you have "all other applications" in one bottle (.wine default directory), may be it is time for you to learn to install in new bottle for new application so that it will not mess up your other applications.

Please inform me if any of you are still unable to install Esword using generic installation with separate bottle I just edited. It should run on any ubuntu version or any distro with wine.

DK

---

### Post by shane2peru on 2007-05-28
> **david_kt said:**
> Actually it is easy to install it in separate bottle for each windows application so that it will not affect each other. To help those that do not know how to install in separate bottle, I have edited this [how to ]("http://ubuntuforums.org/showpost.php...30&postcount=1")to use separate bottle (.wine_Esword) so that installation of Esword wll not affect default .wine directory.

If you have "all other applications" in one bottle (.wine default directory), may be it is time for you to learn to install in new bottle for new application so that it will not mess up your other applications.

Please inform me if any of you are still unable to install Esword using generic installation with separate bottle I just edited. It should run on any ubuntu version or any distro with wine.

DK

Now that is a very nice trick!  Good idea.

Shane

---

### Post by dmacbanay on 2007-06-04
I installed the deb for esword-ubuntu and installed it under fiesty 7.04 but couldn't run the program and the module installer wouldn't install the modules.  After looking at the config files I finally figured out what was wrong. 

/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-sword

should be renamed as 

/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword

The capital 's' makes all the difference.

Also, the menu items are put under the Utilities menu.

---

### Post by gusjones on 2007-06-05
Any chance of a Fiesty Debian soon? At the moment when I get home I haven't got the energy to kill off an evening doing it all manually, esp. with my two young sons to entertain!

I am toying with setting aside Ubuntu CE on a dedicated PC, but for now Fiesty suits me and I just add what I need. e-sword is far more developed than gnomesword IMO.

---

### Post by mhancoc7 on 2007-06-05
> **gusjones said:**
> Any chance of a Fiesty Debian soon? At the moment when I get home I haven't got the energy to kill off an evening doing it all manually, esp. with my two young sons to entertain!

I am toying with setting aside Ubuntu CE on a dedicated PC, but for now Fiesty suits me and I just add what I need. e-sword is far more developed than gnomesword IMO.

The current e-Sword deb should work on Feisty. The only issue is with the Wine version. You need to run 0.9.37. This will hopefully be fixed with Wine 0.9.39.

[http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html)

Jereme

---

### Post by dmacbanay on 2007-06-05
i'm running with wine 0.9.38 and it's working fine on feisty ubuntu 7.04 except that i needed to rename the e-sword directory to e-Sword.

---

### Post by shane2peru on 2007-06-05
> **dmacbanay said:**
> i'm running with wine 0.9.38 and it's working fine on feisty ubuntu 7.04 except that i needed to rename the e-sword directory to e-Sword.

did you install wine .9.38 before or after installing e-Sword?  That is really interesting.!

Shane

---

### Post by dmacbanay on 2007-06-05
wine 0.9.38 was installed prior to my installing the debs for esword

---

### Post by mgc1952 on 2007-09-09
Hi

I was using CE 3.3 and loved it. The plus of e-sword was awesome. I jumped to gutsy with a clean install as I just couldn't get my wireless working and gutsy does it with ease out of the box.

I tried your conversion script but of course, it wanted me to update back to feisty which for the above reason I was remiss to do. Is the conversion script for gutsy available yet?

Thanks for your work

Mark

---

### Post by mhancoc7 on 2007-09-09
> **mgc1952 said:**
> Hi

I was using CE 3.3 and loved it. The plus of e-sword was awesome. I jumped to gutsy with a clean install as I just couldn't get my wireless working and gutsy does it with ease out of the box.

I tried your conversion script but of course, it wanted me to update back to feisty which for the above reason I was remiss to do. Is the conversion script for gutsy available yet?

Thanks for your work

Mark

We will not release the convert_me script for Gutsy until it is officially released.

Thanks, Jereme

---

### Post by mgc1952 on 2007-09-10
Quite understandable - thanks again

Mark

---

### Post by octotom on 2007-10-09
Hi,

The other day when I found out that I could have e-Sword for Ubuntu, I was stoked!  I installed it immediately and it's worked awesome!  

When I had it on Windows, I bought the NLT addon on for it and now when I try to install it with the manual install method, it freezes after I put in the unlock code.  It only happens to this module.  Anything other of the modules I try to manually install works fine.  (IT happens to be the only non free one too)

Thanks for your help and the program too!

Tom

---

### Post by tak1150 on 2007-10-10
> **octotom said:**
> Hi,

The other day when I found out that I could have e-Sword for Ubuntu, I was stoked!  I installed it immediately and it's worked awesome!  

When I had it on Windows, I bought the NLT addon on for it and now when I try to install it with the manual install method, it freezes after I put in the unlock code.  It only happens to this module.  Anything other of the modules I try to manually install works fine.  (IT happens to be the only non free one too)

Thanks for your help and the program too!

Tom

Hi Tom,
I had the same problem as well and it seems it has not been resolved.
The workaround is to go to the Windows partition (if you still have it) and go to (I might remember this wrong):

```
C:\Program Files\e-Sword\
```

And copy the NLT file to a USB stick or email it to yourself; it's probably called "nlt.bbl" (I bought NKJV and it's called nkjv.bbl) 

In Ubuntu, go to this directory:

```
/usr/local/apps/esword4linux/.esword/drive_c/Program\ Files/e-Sword
```

and paste the "nlt.bbl" file there (using Nautilus). Or you can do it from the commandline:

```
mv /location/of/nlt.bbl /usr/local/apps/esword4linux/.esword/drive_c/Program\ Files/e-Sword/
```

That should do it. So the question is, what do we do when we buy another Bible translation later? (for those of us who don't have Win partitions any more)

I have gotten my WinXP virtual machine to work. So I guess I can install it first there and repeat what I've written here. For others, buy all the Bible translations you want before you erase your Win partitions!

Tak

---

### Post by octotom on 2007-10-10
Thanks for the reply!

Regrettably, when I install Ubuntu, I didn't keep my windows partition.  Urg.

Tom

---

### Post by jonathonblake on 2007-10-10
> **tak1150]
The workaround is to go to the Windows partition (if you still have it) and go to (I might remember this wrong):

```
C:\Program Files\e-Sword\
```

And copy the NLT file to a USB stick or email it to yourself said:**
> 

That is in *The e-Sword Utility Program FAQ*, but I doubt that anybody but the most hard core users of e-Sword have waded through the entire document. Or should I say set of documents.:)

As people migrate from Windows to Ubuntu Christian Edition, this will become more of an issue. I don't know how to address it, beyond mentioning it in *The e-Sword Utility Program FAQ: Linux*.  A document that I suspect will be read after the Windows partition has been deleted.  :(

[quote]That should do it. So the question is, what do we do when we buy another Bible translation later? (for those of us who don't have Win partitions any more)

AFAIK, both eStudySource and Equipping Ministries are aware of this issue. They don't have any viable alternatives.  (Neither of those organizations has any experience with Linux at the user level.)

Oh, and it isn't just Bible Translations.  As negotiations with various publishers progress, all resources types will be affected.(Commentary, Dictionary, Topical file, Map, Memory, and Harmony. Maybe also Bible Reading Plans, Verse Lists, and Study Notes,)

xan

jonathon

---

### Post by tak1150 on 2007-10-11
Ouch. Been there too.
> Regrettably, when I install Ubuntu, I didn't keep my windows partition. Urg.

If you have the time and motivation for NLT, which I do like that translation a lot, then you can probably do virtual machine for windows fairly easily. Did your computer come with a CD for Windows XP? If so, you can get it working with Virtualbox pretty easily. Just type in

sudo apt-get install virtualbox

Then click on "New" button and follow the instruction to set up a virtual machine. Then pop in the Win CD and ... done. Installation goes quicker on VM (at least in my case) than the actual installation. Once you're done installing it, you can call Microsoft to give you a new activation code.

Hope this helps :)

Edit: You don't have to call Microsoft if you don't need the win VM for more than 30 days.

---

### Post by octotom on 2007-10-17
Thanks for that virtual machine tip.  I just noticed that you had replied so I haven't tried it yet.  I'll get on that right away.  With the virtual machine, do I need to install windows or no?  Anyway, thanks for your help!

I have another question.  I was planning on installing Gutsy in the next few days.  Will e-Sword work on it?  Hopefully it will!!!

Thanks again!

Tom

---

### Post by jonathonblake on 2007-10-17
> **tak1150 said:**
>  then you can probably do virtual machine for windows fairly easily.

What is the advantage to using a Virtual machine,instead of dual booting?

xan

jonathon

---

### Post by tak1150 on 2007-10-17
Before trying VM approach, make sure that you have Windows installation CD as opposed to Rescue CD. Sometimes those rescue CD's that PC makers ship your PC with do not work with VM. But I guess it won't hurt to try it (unless you erase your windows partition).

I erased my Windows partition ~6 months ago because of the VM prospect. With the "seamless" mode for virtualbox, I can seamlessly have Windows programs open on my Ubuntu Desktop. I can copy and paste between Win programs and Ubuntu programs, etc. It is memory and CPU hungry since you're essentially running 2 OS's at the same time. The best part for me is that I don't have to reboot to use Windows programs.

There is one WIn program that will not run on Wine and I really need it for my work. So that's what I do: VM. Hope this helps.

Gotta go to the Bible study now,
Tak

---

### Post by octotom on 2007-10-20
Incase anyone in the future asks or anyone else just wants to know, e-Sword will install on Gutsy.

---

### Post by tak1150 on 2007-10-21
> Incase anyone in the future asks or anyone else just wants to know, e-Sword will install on Gutsy.
through which method? I tried the .deb installer for Feisty and it didn't (the installer) install. Thanks.

---

### Post by octotom on 2007-10-21
I did a search for e-Sword for ubuntu went to the first site and downloaded it from this link:

[http://www.ubuntulabs.devubuntu.com/deb/]("http://www.ubuntulabs.devubuntu.com/deb/")

From then I just clicked on the file and it installed.  It took a little longer than it did on Fiesty though.  I just now discovered that the module manager doesn't work.  Hopefully this will get resolved!

Tom

---

### Post by MrDonnie on 2007-10-21
I have just downloaded e-sword during the install, it asked for a destination folder, with 'c/' as the default.  I am still running windows which is on c,  Is it possible that linux only recognizes the drive it is on as c or do i need to change the destination folder?

---

### Post by MrDonnie on 2007-10-21
disregard, i used the default location of c and it works.  Good job, God bless you.

---

### Post by redfox on 2007-11-13
In the first post, the .deb for e-Sword was made for Dapper and Edgy.  Does this work fine for Gutsy?

Also, I just tried to straight install e-Sword using wine.  e-Sword works, but it's not displaying the text.  Is that something that can be tweaked?

---

### Post by tak1150 on 2007-11-13
> **redfox said:**
> In the first post, the .deb for e-Sword was made for Dapper and Edgy.  Does this work fine for Gutsy?

Also, I just tried to straight install e-Sword using wine.  e-Sword works, but it's not displaying the text.  Is that something that can be tweaked?

[http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html]("http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html")
The above link (made for feisty) should work for you. I've confirmed it works in Gutsy.

---

### Post by gusjones on 2007-11-16
> **tak1150 said:**
> [http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html)
The above link (made for feisty) should work for you. I've confirmed it works in Gutsy.

I just tried it for Fiesty and it all installs fine, but at the end it gives a message that I may have to enter my password, and then it stops. So I then assume everything went ok, however when I try to launch Esword nothing happens.

So if I open the command prompt and run it from there, I get a message about some missing path on what appears to be a Wine windows exe path. (I can report the exact message, but since I'm at work I can't do it just at the moment).

Oh and I had a similar problem when I installed "the word" package .deb. It again appeared to install OK but I cannot launch it.

I already had wine installed before I started, any ideas on what might have have gone wrong??

---

### Post by mhancoc7 on 2007-11-16
> **gusjones said:**
> I just tried it for Fiesty and it all installs fine, but at the end it gives a message that I may have to enter my password, and then it stops. So I then assume everything went ok, however when I try to launch Esword nothing happens.

So if I open the command prompt and run it from there, I get a message about some missing path on what appears to be a Wine windows exe path. (I can report the exact message, but since I'm at work I can't do it just at the moment).

Oh and I had a similar problem when I installed "the word" package .deb. It again appeared to install OK but I cannot launch it.

I already had wine installed before I started, any ideas on what might have have gone wrong??

Sounds like it is hanging up on running gksu. Are you using Kubuntu? If not are you using a language other than English? Those are the only two things that I can think of. If you can post the exact message you get in the terminal that might help.
Thanks, Jereme

---

### Post by gusjones on 2007-11-16
> **mhancoc7 said:**
> Sounds like it is hanging up on running gksu. Are you using Kubuntu? If not are you using a language other than English? Those are the only two things that I can think of. If you can post the exact message you get in the terminal that might help.
Thanks, Jereme

Hi, I'm using english and Ubuntu. Here is the message I get when I run from the terminal

rob@rob-desktop1:/usr/local/apps/esword4linux$ ./runesword
chmod: cannot access `/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword': No such file or directory
wine: cannot find '/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword/e-Sword.exe'
chmod: cannot access `/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword': No such file or directory

Any thoughts?

---

### Post by mhancoc7 on 2007-11-16
> **gusjones said:**
> Hi, I'm using english and Ubuntu. Here is the message I get when I run from the terminal

rob@rob-desktop1:/usr/local/apps/esword4linux$ ./runesword
chmod: cannot access `/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword': No such file or directory
wine: cannot find '/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword/e-Sword.exe'
chmod: cannot access `/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword': No such file or directory

Any thoughts?
I would try to run the installer in the terminal so you so you can see what is actually happening during install. Then you can post the terminal output of that. It looks like it is getting stopped at the last stage of installation to me.

Thanks, Jereme

---

### Post by th1bill on 2007-12-11
In Gutsy I have installed esword4linux 1.6 and it did just exactly like it should have and when I clicked the e-Sword Install in the menu it installed the program just perfectly.  I installed several modules and all went well.  When I click the e-Sword launcher in the menu or when I use the command line it will not run.  If I sign in to the root or superuser account it operates perfectly.  I have used the chmod 755 from the terminal to no affect.  Is there a way around this?  I do not want my grandchild operating in the root.

---

### Post by mattman on 2007-12-25
I've been having similar trouble installing e-sword in Gutsy. So I ran the install script from the command line and noticed that when the script tries to download the e-sword installation file it downloads a download.html file instead. I tried the download link from within Firefox and it works fine. The install script looks fine so i relly don't know how to solve this. E-sword worked great in Feisty.

---

### Post by mattman on 2007-12-25
One way to fix this is by manually downloading the esword binary and putting it in /usr/local/apps/esword4linux/.esword/download/

---

### Post by mattman on 2007-12-25
This problem also applies to the module manager. You can circumvent the problem by manually downloading the modules you want to use and choose the manual install in the module manager. Hope this helps everyone out until there is an official fix for the problem.

Ron Paul '08 :)

---

### Post by cafluegg on 2007-12-25
Another way to get around the root issue is to use the tutorial found in this forum for installing e-sword manually through the terminal. I have successfully used the tutorial on both UCE and churchpup.

As far as the modules are concerned, I simply went to my dad's machine - a windows XP machine - and copied all the module files from his e-sword folder to my flash drive and then pasted them into my e-sword folder in UCE.

---

### Post by ggaines1 on 2007-12-29
Morning Guys,

    I am very new to ubuntu gutsy.  I have installed esword using crossover and works great, cannot get modules added.  I have tried install, install from flash, install from web site, no matter what hangs.  i have then copied all bll, doc, map files and tried to paste them here, but there is no here

ow navigate to /usr/local/apps/esword4linux/.esword/drive_c/Progr am Files/e-Sword

I get all the way down to program files/  looking for e-sword and there is not an esword there.  so i created a new folder and pasted files, but no luck.  I also have all the biles in exe files but cannot get them to load

apprecaited any direction, i am definately a beginner

Thanks and god bless
greg

---

### Post by mattman on 2007-12-29
> **ggaines1 said:**
> Morning Guys,

   
ow navigate to /usr/local/apps/esword4linux/.esword/drive_c/Progr am Files/e-Sword

I get all the way down to program files/  looking for e-sword and there is not an esword there.

These folders are only going to exist if you used the esword4linux deb package provided by UbuntuCE. You used crossover so you will also need to install modules using crossover. Make sure you install the modules to the same bottle that you installed esword.

---

### Post by ggaines1 on 2007-12-29
Thanks, I have tried installing with wine will not load, tried the deb package and same thing, will not work at all with those installers.  Crossover installed without a problem at all, but will not install modules, it hangs on screen that says this bible version is a add on.  It does try but hangs, just tried to install in bottle esword with crossover installer,   in it still hangs and does not install

thanks greg

---

### Post by ggaines1 on 2007-12-29
I found this thread, if someone can tell me which folder to install files in.  I have them copied from my XP program and on ubuntu now, just need to understand which file that is mentioned here

Thanks Greg

"Extra modules as packaged on the e-Sword website will not install in either crossover or wine - the installer just hangs: the solution to this is to copy the modules from an existing windows installation into the installation folder in crossover office - this sounds hard but isn't too difficult. Many e-Sword users already know how to do this in windows due to many third party modules not having installers anyway. "

---

### Post by Wayfarer58 on 2008-01-12
Greetings All!

Today I installed the esword package. Everything went smoothly but when I click on the esword icon under applications\accessories absolutely nothing happens!

I'm new to Ububtu. What am I missing?

Thanks!

---

### Post by father_je on 2008-01-15
hello I'm having problem with esword I'm using Ubuntu CE after installation I cannot run the esword application, I have the esword icon  in the accessories but it won't launch, have already downloaded esword-ubuntu_1.6_all.deb and reinstalled it but still the same it won't work, pls help thank you

---

### Post by jonathonblake on 2008-01-16
> **father_je said:**
>  I cannot run the esword application, 

a)  In what directory did you install e-Sword?
(Full path)

b) What permissions did you give it;

c) Did you install any other resources;

xan

jonathon

---

### Post by ChrisNZ on 2008-01-26
I believe I have the same issue.
I'm running Gutsy 7.10, I downloaded the same file as the previous person.
Then went to Accessories and clicked on eSword Modules, this then downloaded the eSword Files and put them into the
 /usr/local/apps/esword4linux
 Also in this path was esword4linux(2) possibly through the module manager I had working some weeks ago. So all the modules are there.
The updated menu Accessories/eSword links to script "runesword"
When clicked, nothing runs at all! :(
Another noob here. Program runs fine on the dual boot windoz 98, just trying to end my last remaining attachment to windoz! Help!
TIA

Chris

---

### Post by david_kt on 2008-01-28
> **ChrisNZ said:**
> I believe I have the same issue.
I'm running Gutsy 7.10, I downloaded the same file as the previous person.

Chris

You can try below link "how to" to install latest version of esword (794) and using latest wine (0.9.54). It could install e-sword and even it's modules without any problem. Furthermore, you could install it on any distro you want, as long as it could run wine:

[http://ubuntuforums.org/showthread.php?t=404042]("http://ubuntuforums.org/showthread.php?t=404042")
If any of you have any issue, send PM to me.

DK

---

### Post by evan.rotert on 2008-01-29
I'm having the same issue as those above, using the 1.6 version (.deb) it doesn't seem to actually install e-sword at all, nor does the module manager install the actual modules.  Of course, when I click the E-Sword item in my system menu, nothing happens.  I've installed it the usual way using Wine, but using Compiz once I maximize the window I can't un-maximize it again.  I'm not sure if this problem would be mitigated by using the .deb installer, but for the time being I'm stuck with this.

Also- does anyone know of an ftp site or something where I can snag all the .bbl, .cmt, etc. files in one place? The module manager doesn't work and all I have are the .exe files leftover from installing in Windows, not the .bbl and .cmt files themselves.  Thanks!

~Evan

---

### Post by david_kt on 2008-01-29
> **evan.rotert said:**
>  I've installed it the usual way using Wine, but using Compiz once I maximize the window I can't un-maximize it again.  I'm not sure if this problem would be mitigated by using the .deb installer, but for the time being I'm stuck with this.~Evan

What usual way did you use? If you use below way, you should not have any problem with maximize and minimize, and also you would be able to install addons using the exe file:

```
http://ubuntuforums.org/showthread.php?t=404042
```

I have tested it using wine 0.9.54 and E-sword 794.

DK

---

### Post by jonathonblake on 2008-01-29
> **evan.rotert said:**
> 
Also- does anyone know of an ftp site or something where I can snag all the .bbl, .cmt, etc. files in one place?  

It is a copyright violation for the resources at e-sword.net to be distributed elsewhere on the Internet.

It is a copyright violation for the resources at estudysource.com to be redistributed.

Which is a long way of saying that you won't find a legal copy of those resources on the net as anything other than executable files.

xan

jonathon

---

### Post by notepad on 2008-01-30
[http://www.christianubuntuukmirror.co.uk/ubuntuce/debs/esword-ubuntu_1.6_all.deb](http://www.christianubuntuukmirror.co.uk/ubuntuce/debs/esword-ubuntu_1.6_all.deb)

this does not work in gutsy.

i think im going to have to rebuild my partition table and my operating system just so i can make virtualbox work just so i can run windoze just so i can use esword just so i can read the bible with strongs numbers.

bless the day that a linux bible application starts doing it so i can relieve M$ of the satisfaction of keeping a stranglehold on one more user.

---

### Post by david_kt on 2008-01-30
> **notepad said:**
> [http://www.christianubuntuukmirror.co.uk/ubuntuce/debs/esword-ubuntu_1.6_all.deb](http://www.christianubuntuukmirror.co.uk/ubuntuce/debs/esword-ubuntu_1.6_all.deb)

this does not work in gutsy.

i think im going to have to rebuild my partition table and my operating system just so i can make virtualbox work just so i can run windoze just so i can use esword just so i can read the bible with strongs numbers.

bless the day that a linux bible application starts doing it so i can relieve M$ of the satisfaction of keeping a stranglehold on one more user.

Before repartition you harddisk, why don't you try below "how to",  it could run all features of e-sword in gutsy gibbon using latest wine (wine 0.9.54):

```
http://ubuntuforums.org/showthread.php?t=404042
```

You must have wine installed though.

DK

---

### Post by jonathonblake on 2008-01-30
> **notepad said:**
> [http://www.christianubuntuukmirror.co.uk/ubuntuce/debs/esword-ubuntu_1.6_all.deb](http://www.christianubuntuukmirror.co.uk/ubuntuce/debs/esword-ubuntu_1.6_all.deb)

this does not work in gutsy.

a) e-Sword has undergone some major changes since that was created. (From 7.83.5 to 7.9.5)

b) e-Sword.net has had a major website redesign.  One of the more significant changes is that bots are usually dropped, when they attempt to download a file.

> bless the day that a linux bible application starts doing 
*The Sword Project* has a couple of fronts ends for Linux that display Strong's Numbers.

xan

jonathon

---

### Post by father_je on 2008-01-31
hi, i've the same problem as yours, how did you fix it, i have been trying to install e-sword but after the installation, when i get to the window saying it will ask for my password i click ok then nothing happens, and all i have is the e-sword icon in the accessories, and i can't open it.thank you

---

### Post by father_je on 2008-01-31
jonathon, thank you for your time, i don;t know the exact path where e-sword swas installed, i'm using ubuntu ce, and it has a e-sword installer, i don't know about "permision" i just added some bible with the module manager...thank you very much for your help..

---

### Post by david_kt on 2008-02-01
> **father_je said:**
> hi, i've the same problem as yours, how did you fix it, i have been trying to install e-sword but after the installation, when i get to the window saying it will ask for my password i click ok then nothing happens, and all i have is the e-sword icon in the accessories, and i can't open it.thank you

Father_je and all,

why don't all of you that haveing problem with the deb package try below generic "how to" while waiting for Jeremy to resolve those issues:

[http://ubuntuforums.org/showthread.php?t=404042]("http://ubuntuforums.org/showthread.php?t=404042")

And please let me know the result and I will try to help you if you still face some issues.

DK

---

### Post by k51 on 2008-04-18
HI, i've installed e-sword from the .deb file on ubuntu labs and there were no errors, the install file ran fine and all seemed to be well except, e-sword doesn't actually run when I start it, but e-sword module manager runs just fine.

Here's the error:
```
/usr/local/apps/esword4linux$ ./runesword
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject no class object {66833fe6-8583-11d1-b16a-00c0f0283628} could be created for context 0x3
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject no class object {66833fe6-8583-11d1-b16a-00c0f0283628} could be created for context 0x3
```

I've tried some of the solutions stated in here but none are working, please advise.

Thanks

---

### Post by david_kt on 2008-04-18
> **k51 said:**
> HI, i've installed e-sword from the .deb file on ubuntu labs and there were no errors, the install file ran fine and all seemed to be well except, e-sword doesn't actually run when I start it, but e-sword module manager runs just fine.

I do not know about the deb file. But I can guide you to install using normal installation. Please follow below instruction carefully:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

and let me know if you have problem.

DK

---

### Post by k51 on 2008-04-18
> **david_kt said:**
> I do not know about the deb file. But I can guide you to install using normal installation. Please follow below instruction carefully:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

and let me know if you have problem.

DK

Oh wow, thanks david_kt, it worked just fine following your install guide.
Thanks

---

### Post by jgt157 on 2008-04-19
I just tried it on Kubunt Hardy Heron and got it to install, but I don't see any text in the Bible, commentary, and dictionary areas.  I've installed this on Gutsy with no problems.  I made sure that the riched20.dll and the oleaut32.dll were set to windows native and still no text.  Any help would be appreciated.

Thx,

Jim :confused:

---

### Post by david_kt on 2008-04-19
> **jgt157 said:**
> I just tried it on Kubunt Hardy Heron and got it to install, but I don't see any text in the Bible, commentary, and dictionary areas.  I've installed this on Gutsy with no problems.  I made sure that the riched20.dll and the oleaut32.dll were set to windows native and still no text.  Any help would be appreciated.

Thx,

Jim :confused:

Did you installed it using deb package or normal wine? Which wine version uou are using?

DK

---

### Post by jgt157 on 2008-04-24
I used wine to install it and the version of wine installed on Hardy Heron is 0.9.59.  I used the same steps in gutsy as I used in hardy heron and it worked fine in gutsy.  Any ideas?

Jim

---

### Post by david_kt on 2008-04-24
> **jgt157 said:**
> I used wine to install it and the version of wine installed on Hardy Heron is 0.9.59.  I used the same steps in gutsy as I used in hardy heron and it worked fine in gutsy.  Any ideas?

Jim

Do you mean you use below instruction:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

If yes, it should work. Otherwise, you could try to copy the riched20.dll from e-sword folder to system32.

DK

---

### Post by jgt157 on 2008-04-24
Yes, those are the instructions I used.  They worked fine in gutsy, but not hardy heron.  

Jim

---

### Post by david_kt on 2008-04-29
> **jgt157 said:**
> Yes, those are the instructions I used.  They worked fine in gutsy, but not hardy heron.  

Jim

Make sure you run the winecfg from terminal, not from menu. Open terminal, and run below code

```
env WINEPREFIX=~/.wine_Esword winecfg
```

Press the Libraries tab > type riched20.dll > press add > press edit > choose Native (windows).
Do the same for oleaut32.dll.

You should see the text. If still could not see the text, try to copy riched20.dll from ~/.wine_Esword/drive_c/program files/e-sword/ to ~/.wine_Esword/drive_c/windows/system32/

DK

---

### Post by jesse100 on 2008-05-28
> **shane2peru said:**
> This is kind of a hack, but it will work great for getting your already installed modules into e-Sword.  If you want to transfer them from Windows to your Ubuntu e-Sword.  

In Windows, double click on my computer.  Next click on "Program Files"  now fine e-Sword and double click that folder.  Now you can see all the e-Sword files.  Copy all the .bbl files and .cmt .top .map .dct files and paste them somewhere you have access to with Ubuntu (a usb drive, or pendrive, or something a fat32 partition)  Now boot into Ubuntu.  In Ubuntu use Nautilus to open the location of the copied files from e-Sword.  Got to home in nautilus, and click **View -> see hidden files**  Now click on the .wine folder then "drive_c" now on Program Files and then e-Sword, and paste all those files into e-Sword.  It is a bit of an easier way to get your modules into your Ubuntu edition if you have a lot. 

So, if I just copy those files from my windows version to the one in ubuntu they will work? Sounds almost to good to be true. Especially since I only have dial-up working on my ubuntu.

Jesse

---

### Post by david_kt on 2008-05-28
> **jesse100 said:**
> So, if I just copy those files from my windows version to the one in ubuntu they will work? Sounds almost to good to be true. Especially since I only have dial-up working on my ubuntu.

Jesse

For the modules, yes, it is absolutely working, as long as you have installed e-Sword main program successfully. On the other hand, you could install the modules using the instruction I gave earlier as well if you already downloaded the exe file.

DK

---

### Post by jesse100 on 2008-05-30
I used the deb for the esword and used it to install the modules from exe files. I have some others and wanted to try this way... but I do not see a wine file anywhere. I have unhid the files in my home folder but I see nothing. Where would the esword file be to paste to?

Jesse

---

### Post by david_kt on 2008-05-30
> **jesse100 said:**
> I used the deb for the esword and used it to install the modules from exe files. I have some others and wanted to try this way... but I do not see a wine file anywhere. I have unhid the files in my home folder but I see nothing. Where would the esword file be to paste to?

Jesse

I guess the folder is here:

/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword

But I not sure about the permision. If using normal nautilus file browser you could not paste the modules there, you need to open terminal and run
```
gksudo nautilus
```

and after key in your password, nautils browser will appear. 

But I suggest you re-install it manually using this instruction

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

as the deb file has not been maintain yet.

DK

---

### Post by jesse100 on 2008-05-30
Thats exactly where it was at and it worked beautifully. I had some mods I payed for previously that the Module Manager would hang up trying to install. Pasting them directly was the trick. Thanks again!

Jesse

---

### Post by jesse100 on 2008-05-31
Why can't I cut and paste scripture from esword to my word processor?

Jesse

---

### Post by david_kt on 2008-05-31
> **jesse100 said:**
> Why can't I cut and paste scripture from esword to my word processor?

Jesse

Sure you could not cut and paste from e-Sword. Wht you should do is copy (ctrl+c) and paste (ctrl+v). It work for me.

By the way, my wine version is rc2

DK

---

### Post by jesse100 on 2008-06-13
I will try it again. Thanks.

Jesse

---

### Post by jesse100 on 2008-06-13
I have also added some step books from other programs (WS5) and the esword step reader opens them fine. Very nice.

Jesse

---

### Post by zippytex on 2009-02-25
[COLOR="Red"]Did I read that this was going to be included in the 6 month Ubuntu update?  Then we can just install it like the gnomesword program?  Thanks.[/COLOR]

---

### Post by david_kt on 2009-02-25
> **zippytex said:**
> [COLOR="Red"]Did I read that this was going to be included in the 6 month Ubuntu update?  Then we can just install it like the gnomesword program?  Thanks.[/COLOR]

It is not included yet, but could download the installer here:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

DK

---

### Post by jonathonblake on 2009-02-26
> **zippytex said:**
> Did I read that this was going to be included in the 6 month Ubuntu update? 

For licensing reasons, the e-Sword installation files, binary, resource files,and most documentation can not be included an OS repository, or as a part of an OS that is commercially distributed. 

This does not apply to the scripts that David created for Ubuntu Christian Edition. e-Sword_portable251008.tar.gz, Create_Desktop_Launcher.tar.bz2, and e-Sword_installer_120109.tar.gz can be included in a distro, or shipped with any OS.

jonathon

---

### Post by zakhooi on 2009-03-09
> **twowheeler said:**
> Hmm, well, I spoke too soon.  Upon start up I am getting:



One of these messages pops up for each downloaded file.  E-sword then starts but with no files open.  The bible files and commentaries etc. have been written into the e-sword folder, under ~/.esword/drive_c/Program Files.  The permissions are 644 with my user name as owner.  So I don't see anything wrong.

Any ideas?

I have exactly the smae problem.
My .bbl files worked fine with 7.x but on 8.0.6 I get this error too.

Does anyone have a solution for this please? I'dd appreciate.

Thanks in advance

---

### Post by asmotj on 2009-04-05
[http://ubuntuforums.org/showthread.php?t=404042&highlight=e-sword&page=38](http://ubuntuforums.org/showthread.php?t=404042&highlight=e-sword&page=38)

Ubuntu 9.04 with Wine 1.1.7
seems to be working just fine  .\

---

### Post by joker77 on 2009-06-02
xiphos is the new version of gnomesword. Jaunty users (and older) must add the repositories (and the key) from 
[http://xiphos.org/download/debian-ubuntu/](http://xiphos.org/download/debian-ubuntu/)
or be content with gnomesword. (I didn't try gnomesword)
Xiphos is very refined. Its great.
Don't any of you like it?

---

### Post by BestResveratrol on 2009-06-02
Awesome, thanks.  I'll have to check that out.

---

### Post by zakhooi on 2009-06-04
> **joker77 said:**
> xiphos is the new version of gnomesword. Jaunty users (and older) must add the repositories (and the key) from 
[http://xiphos.org/download/debian-ubuntu/](http://xiphos.org/download/debian-ubuntu/)
or be content with gnomesword. (I didn't try gnomesword)
Xiphos is very refined. Its great.
Don't any of you like it?

That's kewl but I couldn't find any dutch bibles.
So I'm looking for such a tool that supports dutch bibles.
Any suggestions (preferable not something like running esword in wine).

---

### Post by Eutaw on 2009-06-05
Bible Desktop has a (one) Dutch Bible and commentary through Crosswire. I don't read Dutch, but my impression is that it's the 1618 version - SVV? - I get it through Churchpup 3.02, a Puppy Linux distro.

---

### Post by cglamboy on 2009-06-21
Jeremy:
I am Carlos, from North Carolina in the USA.  I had been questioning my desire to have e-sword in Ubuntu, I am a newly in Ubuntu and I do not know anything about it, even-though I am loving it.  I wish I knew about it before I went in to Windows System (which I am desperate to get rid off, because I think is a complete waste of time and energy).  So please help me to get e-sword on my computer if you could, but please be kind to my ignorance in the field because I do not know anything at all on how to do any programing at all in this system and for that matter in any system period.  I will like to thank you for your diligence and desire on making this great program as is e-sword, available to evryone.  Thank you again and please let me know.  God Bless You!

---

### Post by david_kt on 2009-06-21
> **cglamboy said:**
> Jeremy:
I am Carlos, from North Carolina in the USA.  I had been questioning my desire to have e-sword in Ubuntu, I am a newly in Ubuntu and I do not know anything about it, even-though I am loving it.  I wish I knew about it before I went in to Windows System (which I am desperate to get rid off, because I think is a complete waste of time and energy).  So please help me to get e-sword on my computer if you could, but please be kind to my ignorance in the field because I do not know anything at all on how to do any programing at all in this system and for that matter in any system period.  I will like to thank you for your diligence and desire on making this great program as is e-sword, available to evryone.  Thank you again and please let me know.  God Bless You!

I have made it very easy to install e-Sword now. Just download [e-sword-installer]("http://ubuntuforums.org/attachment.php?attachmentid=118516&stc=1&d=1245626623") to you computer, remember where you put it.

Double click on e-sword installer, it will be installed on you computer including the necessary packages. After that got to:

Application > System tools > e-Sword-installer

Read the instruction on the menu and you are done. Please let me know if you have any questions.

DK

---

### Post by jonathonblake on 2009-06-24
> **david_kt said:**
> I have made it very easy to install e-Sword now. Just download [e-sword-installer]("http://ubuntuforums.org/attachment.php?attachmentid=118516&stc=1&d=1245626623") to you computer, remember where you put it.

Can you put that Deb in a PPA?

My thinking is that everything in Ubuntu Christian Edition, that isn't currently in an official Ubuntu Repostiory should be in a single PPA.

jonathon

---

### Post by david_kt on 2009-06-24
> **jonathonblake said:**
> Can you put that Deb in a PPA?

My thinking is that everything in Ubuntu Christian Edition, that isn't currently in an official Ubuntu Repostiory should be in a single PPA.

jonathon

I would to do it, but it require more administration job that I have not completed yet. The main issue for me is to study the code of conduct to be followed, i.e. I must follow the documentation standard, naming standard, and other things that I am not sure of yet.

I have just completed (well, nearly) the dansguardian-gui, now inlcude a slide bar to choose filter setting ( from 50(strict) to 160 (less strict) and you could choose any number in between just slide the slider.

I have also added advance menu to edit blacklist and white list.

I recently found webstrict, dansguardian gui for Ubuntu ME. I thought I want to use it instead of creating new one. But webstrict run on java, and it pull more than 100MB of packages and that put me of. No wonder there is no live cd for ubuntu ME, only live DVD.

I will line up the comparison of webstrict and dansguardian-gui in other post.

DK

---

### Post by forrest charnock on 2009-10-17
Sorry to bother you but I am new to Linux. I had version 8 of Esword working save some less than clear fonts and my graphics viewer would not display .
When I installed the latest esword it won't load but for some reason the training works very well. My luck:}

Will this script work with Wine 1.31 and Ubuntu 9.04?

Thanks 
God Bless

---

### Post by david_kt on 2009-10-17
> **forrest charnock said:**
> Sorry to bother you but I am new to Linux. I had version 8 of Esword working save some less than clear fonts and my graphics viewer would not display .
When I installed the latest esword it won't load but for some reason the training works very well. My luck:}

Will this script work with Wine 1.31 and Ubuntu 9.04?

Thanks 
God Bless

Yes it is. You should check it below:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

Or convert to Ubuntu CE which provide e-Sword installer:

[http://distrowatch.com/ubuntuce](http://distrowatch.com/ubuntuce)

DK

---

### Post by octotom on 2009-10-22
I just installing Ubuntu 9.04 from Kubuntu 9.04 because I saw that there was an installer for e-Sword.  When I downloaded the installer and went to install the .deb file, it couldn't install because it said something is wrong with the dependencies, even after I installed wine.  HEre is what the thing says:

Error: Dependency is not satisfiable: wine (>= 1.1.6)

What should I do?  Go to an older version of wine?  Also, this should work, in theory, on Kubuntu, too, right?  Thanks!

ETA:  I found a site with a walkthrough for how to install e-sword in wine.  I ran this two lines that it said:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

~and~

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list

When I tried to open e-Sword after that, it didn't work (lol).  I tried to use the installer again, and I guess the dependencies were met!  So, the installer should work now.

---

### Post by david_kt on 2009-10-22
> **octotom said:**
> I just installing Ubuntu 9.04 from Kubuntu 9.04 because I saw that there was an installer for e-Sword.  When I downloaded the installer and went to install the .deb file, it couldn't install because it said something is wrong with the dependencies, even after I installed wine.  HEre is what the thing says:

Error: Dependency is not satisfiable: wine (>= 1.1.6)

What should I do?  Go to an older version of wine?  Also, this should work, in theory, on Kubuntu, too, right?  Thanks!

ETA:  I found a site with a walkthrough for how to install e-sword in wine.  I ran this two lines that it said:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

~and~

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list

When I tried to open e-Sword after that, it didn't work (lol).  I tried to use the installer again, and I guess the dependencies were met!  So, the installer should work now.

Yes, e-Sword could not work with wine 1.0.1 which is the default wine in ubuntu, that is why I put wine 1.1.6 as a minimum version requirement.

After you have upgrade to newer wine, the installer should work, and e-Sword should work also.

Yes you are right, the installer would also work in Kubuntu. In fact I have another version that should work on any linux distro:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

Basically it is the same script. 

DK

---

### Post by cwmoser on 2009-12-02
Error: Dependency is not satisfiable: wine (>= 1.1.6)

$  wine  --version
wine-1.1.33

The E-Sword installer fails with wine-1.1.33   -- the latest version.

Carl

---

### Post by david_kt on 2009-12-02
> **cwmoser said:**
> Error: Dependency is not satisfiable: wine (>= 1.1.6)

$  wine  --version
wine-1.1.33

The E-Sword installer fails with wine-1.1.33   -- the latest version.

Carl

I think you use e-Sword installer deb package for Karmic, which use wine 1.0.1 In order to use this installer, you have to remove wine repository, and remove wine beta.

But if you use other than karmic, you could use the script downloaded from below post:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

DK

---

### Post by Mickeyj4j on 2010-01-12
> **mhancoc7 said:**
> I have packaged the whole thing as a .deb package for a super easy installation. It should be considered "beta" for now. So USE AT YOUR OWN RISK!

sp where si the .deb for ubuntu 9.10 karmic your 2 links are not actually ubuntu versions that i know of.

---

### Post by dave-knuckle on 2010-07-27
worked great on the Gos issue of hardy,thanks

---

### Post by GlennW on 2010-11-02
Hi David,

I've just done a fresh install of Ubuntu 10.10. I found your E-Sword installer only after messing around for a while. I know that previous installs required a wine of an earlier vintage. However, after reading your posts here, it appears that the latest should be the best. But, after following your instructions I end up with this error message (see screenshot).

Suggestions?

---

### Post by david_kt on 2010-11-02
> **GlennW said:**
> Hi David,

I've just done a fresh install of Ubuntu 10.10. I found your E-Sword installer only after messing around for a while. I know that previous installs required a wine of an earlier vintage. However, after reading your posts here, it appears that the latest should be the best. But, after following your instructions I end up with this error message (see screenshot).

Suggestions?

Please follow the first post of below thread:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

DK

---

### Post by GlennW on 2010-11-04
Thanks David. Worked without a hitch.

---

### Post by Mickeyj4j on 2010-12-01
Awesomw worked for em great good work on things. see how easy windows applications that shoud not work do. 

whome ever the creater of this installer actually is should contact the e-sword team and see if they would like to put it on there site. as an option. they could put a disclamer stating its not there application.

---

### Post by jonathonblake on 2010-12-02
> **Mickeyj4j said:**
> 
whome ever the creater of this installer actually is should contact the e-sword team and see if they would like to put it on there site. as an option.

e-Sword.net currently has a page that explains how to install e-Sword on Mac and *Nix boxes using CrossOver.

eStudySource.com has a page that provides a coupon for purchasing Crossover.

e-Sword-users.org has a page that points people to [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042) for instructions on how to install e-Sword on a Linux box.

jonathon

---

