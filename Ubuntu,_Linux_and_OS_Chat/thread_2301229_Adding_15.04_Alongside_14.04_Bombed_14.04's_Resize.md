---
title: "Adding 15.04 Alongside 14.04 Bombed 14.04's Resized Partition"
date: 2015-10-31
forum: Ubuntu, Linux and OS Chat
---

### Post by oldefoxx on 2015-10-31
I used the LiveCD of Ubuntu 15.04 and had it install on my internal drive behind 14.04.  This meant it split a single partition in two, and I could use a slider to decide how much space to give to each partition.  My first partition is 14,04, and I divided the partitions roughly 46:44, as the rest of the drive is used for swap or overhead.

So the LiveCD had a big job of restructuring the first partition to a smaller size and adding a second, where it proceeded to add 15.04.  But into the process it reported a problem where it was trying to add new features to go with new hardware, and these conflicted with my initial install of 14.04.  I could either Stop or Continue.  Well, obviously I did not want to mess up 14.04, so I chose Stop.  But apparently the process was not stopped soon enough, because the LiveCD had already stamped the drive partition table with the faxt that a new ext2 partition was being added.  So anyway, the 15.04 install completed.

But when I tried to reboot, the drive was hosed.  Neither LiveCD would deal with it properly.  I got to the "Something Else" stage and tried a Reset. and that appeared to clear the problem.  But I got all sorts of wierd errors about links that were read only when I tried to access folders or files on the first partition and it still would not boot.  I decided to use gparted, which fortunately is on the LiveCDs.

It's not apparent when using gparted that it has a means of checking an existing partition for problems, and of course with gparted, picking an option does not mean that it does it:  You have to go under Edit and pick Apply All Operations.  I watched the process bar for a bit, until it rutted down at one point and quit advancing.  I went off to do other things for awhile, and when I came back, it was completed.  Under Details, there were none.  But now the partition could be accessed.

I decided to take no chances, so I have since reinstalled 14.04.  But I was able to save /home and my account's contents.  LiveCD still messed up the boot process because running "sudo update grub" followed by "sudo grub-install /dev/sda" encountered ext2 errors, and it took booting the cd of boot-repair-disk to clean that up.

Obviously LiveCD needs some touch-up work to prevent such things from happening.  LiveCD should also give you something else:  If you elect to just install the operating system, it should fire up the desktop anyway.  Sitting there waiting for the install to complete is a great time waster, so I make a point of picking Try, beginning the install from there, then picking a game or getting on the internet while the install takes place.

---

### Post by TheFu on 2015-11-01
Is there a question?

---

### Post by oldefoxx on 2015-11-01
This is maybe a case of an answer before the question,  I had a LiveCD install of 15.04 blow up in my face.   It did things wrong, and it caught me flat-footed.  To recover, I had to  try everything I could come up with.  It worked.  That could be useful to someone else.  It might also tell them that maybe they should not completely trust the LiveCD.  It hosed my hard drive, and it took gparted and boot-repair-disk to unhose it.  Maybe they should make sure that have boot-repair-disk downloaded and on CD before they try an install with LiveCD that seeks to repartition their hard drive.

Yes, it warrants a bug report.  But I'm done with trying to file those things myself.  They make it too hard because you are suppose to even know what package is at fault.  What;s the package for LiveCD?  How's that for a question?

Besides, a bug report is not going to be of any use to someone that just got hosed.  I don't read bug reports before or after an event.  I could care less who does what to fix it.  If it needs fixing, it should be enough that I've told you what happened and what I think caused it.  I'm not expert enough to take it further.

Now you don;t have to have this as a live thread.  But somewhere out there, someone is going to want an answer to help them, and I've done that.  I've answered their questions.  I solved the problem.  I can't mark it SOLVED because it won't be solveed until the LiveCD is corrected.  I'm just offering a patch-workaround for when the LiveCD tears a hole in your PC setup.

The thing to do is let google, bing, and other search engines send their spyders and crawlers to find my answer so that they can use a search engine either here or outside to find my answer when they need it.  That can take several weeks to happen, because there is a lot of internet to crawl and map.  And here you want to kill off the answer because you don't see a question in it.  So here is another question for you:  That doesn't make you very bright, does it?  I bet there are a lot more like you where you come from.  Seriously.

Serious, because you people wirh UbuntuForums.org always want the question first. but you wan to encourage people to see if the question has been asked and solved previously, and maybe join the thread if there is still no answer.  How about simply beginning a thread with an answer in place, and the question implied in the title?  Doesn't that work for you?  See, another question.

What you ought to do is encourage people to contribute answers in threads specific to that purpose.  I have and am working on scripts that can the following tasks that can then be copied and pasted into text files that can then be marked for execution just by clicking on them.  I'm about ready to offer these script files up online for others to download, modify, and use to help themselves.  Here is an idea of what these script files will do:

(1)  Completely automate the job of getting software updates whenever you want.  If I can solve the problem of doing this on starting up, you can skip the step of just requiring a password to become super user first.

(2)  Completely automate the job of installing and using any cursor theme that you want to add.  You just download it, pick it out of a lineup, and say what size you want it to be.  Only your password is required because you have to effect some system changes.

(3)  Completely automate the job of not only setting your background wallpaper, but making it apply to the Login screen as well.  It just has to be a .png file instead of a .jpg or .jpeg file.  But it explains how to search for new backgrounds online, download the full size instead of a thumbnail, and get the ,jpg files converted online for free, even to specifying size of image, sharpness, and added effects (if any).  It even explains how easy it is to change backgrounds whenever it suits you, and the advantage of dark backgrounds giving better contrast to desktop icons if used in place of light ones.

(4) For the visually impaired, how simple it is to set a minumum font size, make it is bold, and even use one consistent font everywhere if they want.  That they might get more readability if they make it fixed-spaced, meaning the font they want might include the word "Mono" in it.  And then applies these changes uniformly across the system using gsettings so that only individual applications might need tweaking.  Or it could just rescale the scaling factor for text in all the places that need the tweaking.  There are several.  All this handled by script files.

(5) Some interfaces allow user preferences to be displayed and tweaked.  Dash doesn't, and Metacity does under 14.04, but not under 15.04.  The difference there is that you can use apt-get to install gnome-session-fullback under 14.04, but you have to install the lesser gnome-session-flashback under 15.04.  A script file  takes care of this with the magic of gsettings.  Now you can change it so that executable files are either run in terminal, displayed (actually editable), or run without the terminal.  This without the maze of finding your way around in the File Manager.

(6)  A bug in 14.04 means the screen brightness settings is not saved, so the screen keeps coming back to full brightness every time you start Ubuntu, and sometimes when you just log out and log in.  A small utility named xbacklight can be installed and made part of another script where you can have it so that a "**sudo xbacklight -set %%**", where "%%" represents some percentage of the light output.  I have mine set at 50 on one laptop. and 65 on the other.

Screen brightness is normally across the board for all users, but with xbacklight installed, each user can have their own individual setting.  Again, a part of another script file, such as the one for daily update checks.  Or just A "Do 1st" text file on the Desktop where the user can cluster everything they want to do first on logging in.  Like adjust fonts, font sizes, text scaling, cursors, and so on.

That would be the purpose of this one individual thread, or multiple threads if you had one for each flavor of Ubuntu, possibly more if you looked at how one release varies from the next:  Scripts to make whatever version of Ubuntu you pick better suited to the individual wants and needs.  People come to the forums for only a few reasons:

(1)  To get answers to their questions

Now you have a chance to add two new reasons for coming:

(2)  To post answers to questions that others may ask later

(3)  To post scripts that give the individual lots of control over his/her experience without first expecting them to become experts themselves. 

You go by the name "forum".  That is an important distinction.  It means open discussion.  It does not mean you have the right to police that discussion to the point of removing or jailing anything that you don't see as directly question-related.  Now in some categories, yes.  If people want help in a specidic area that your experts prowl to help with, some posts or threads are a hinderance, so move them somewhere that they will still be part of what is going on, but trim your sails where you need to in order to keep things tidy.  And anything where Ubuntu is the base should be acceptable.

For instance, there can be issues about which VM is the best choice, and the why, the how, and the use of a complex package like gimp as has been resolved by others.  Ubuntu is more than an operating system that is pretty much complete, but it is a stable platform for going much further.

The whole matter of alternatives and add-ons in the form of .deb files is a very important one, because there is much out there that is not specific to Ubuntu that can be installed, tried, and removed if not to taste.  With Ubuntu, they just have Firefox, Brassero, and gedit.  Firefox is not top dog anymore, Brassero only get 3 stars, and gedit does not let you change line numbering, syntax highlighting, font or size directly.  Better choices would be Slimjet, and for ISO burning, Xfburn, and Cream as the editor.   

If nothing else, threads and posts can point to specific links that can guide users to other forums and support sites.  People do not instinctively know or understand the concept of doing web searches and how to start finding answers on their own using a computer, network connection, and accessing a search site like google,com, bing.com. duckduckgo.com, ixquick.com, and many more.  A list of the top 15 search engines appears here:  [http://www.ebizmba.com/articles/search-engines](http://www.ebizmba.com/articles/search-engines)

Also listed is Ask,com, which I have found to be very disappointing.  It shows up in the searches by other search engines, but merely reframes the question asked and gives no useful links itself.  

I finally found something that google was terrible at and bing got right.  I was trying to find an extended list of the digits that make up the constant natural e, and google not only failed to find a list, it got stuck at one point because of how I phrased the search.  I had to kill it.  One search with bing found me a posted list of the first 10.000 digits of natural e, and I used exactly the same search terms with it as I had with google.

Point I am making is, there is a lot that goes into getting the best possible experience with a personal computer.  The operating systems Ubuntu, debian. or any flavor of linux all take precidence over Windows in my experience, and it's all (or almost all) free to be downloaded and installed by anyone that can get pn the internet.  If you don't have a direct internet connection, you can still order the operating system on CD or DVD from an online source, including eBay.com, or get a friend to download it and burn it to a CD or DVD for you.  There are even flavors of Linux that work on portable devices. 

I know all this, you know all this, but have you considered the many people that don't know this?  There are many, and just like Linux itself, the facts should be freely available as well.  Only most experts don;t stop to jot it down for others to learn from as they go along.  That makes online forums an essential place for beginners to come to mingle with those that know more than they do, about many things, not all specific to one flavor of Linux.

Most beginners have no idea of using bash and scripts to automate many tasks, even to the point of making these available to others by posting them online.  You get them use to using scripts. they may venture into learning basic bash commands and utilities, such as dir, cd, pwd, ls, cp, mv, rm, mkdir, rmdir, man, chmod, chown, adduser,  deluser, addgroup, delgroup, sudo, su, and much, much more. and they learn about things like find, grep, awk, echo, cat, for f in, while, if, do, done, break, exit, sort, locate, $variables, and piping from one process to another using <, >, >>, |, the use of more or less, and the use of temporary files to hold temporary results. 

You can manage many processes more effectively from a terminal or script file than you can achieve from the GUI.  For instance, if you wanted to rid yourself of a lot of trash files on your drive, you could run a composite command like this:  "**rm -r ~ *~; rm -r ~ *.tmp; rm -r ~ *.log; rm -r ~ tmp.***".

If you wanted to copy all your ,htm and .html files to a new folder under Documents named HTML, you are advised not to use the "cp" command.  You don't want to try or move or copy a file to itselt, which is what would happen when your copy command ran the HTML folder.  The "cp" command does not allow you to exclude a folder, but some commands do allow for this.  Two are "grep" and "tar".  Another problem is if you are copying  files from multiple sources that have the exact same name.  With flag options, you might force an overwrite of an existing file, but only if the file to be copied is newer.  a combination of flags might lead to using "cp -purf" as a way to skirt these problems:

**mkdir ~/HTML 2>tmpfile; cp -purf ~/*.[hH][tT][mM] ~/HTML  2>tmpfile; cp -purf ~/*.[hH][tT][mM][lL] ~/HTML  2>tmpfile; rm tmpfile**

Looks complicated, but it is just four commands, stacked together with semi-colons between each, into one line for an easier copy & paste into a terminal window.  Spread out in a script file, they might look more like this:

**mkdir HTML 2>tmpfile **    # create the folder named HTML in the $HOME (~/) folder.  The " 2>tmpfile" sends any complaint that the folder already exists to tmpfile.  If it already exists, no harm is done.

**cp -purf ~/*.[hH][tT][mM] ~/HTML  2>tmpfile**  # copies and keeps permissions, only if newer, repeatedly, and with force if necessary.  Again, errors go to tmpfile.

Note the *.[hH][tT][mM] filter.  the [] brackets means any character inside is allowed at that position.  This is a method allowing for the extention to be .htm, .HTM, .Htm, or any other combination of upper and lower case letters h,t,m in that exact order.

**cp -purf ~/*.[hH][tT][mM][lL] ~/HTML  2>tmpfile**   # Like the previous cp -purf command, but with [lL] added to the filter.  This is because  some people use four letters, and others shorten them to three, which is the normal 8,3 format for MSDOS and Windows.  Its possible to use one command for bothm but that means adding * after the last []. and that would include backups with "~" or tagg-on extensions like ".old", ",hold", ",new", or ".tmp", which we might not want.

**rm tmpfile **  #remove tmpfile.  If you want to see its contents first, do a "**cat tmpfile | more**"

This is just one example of collecting copies of files into a single directory.  You can do similar things for all ,jpg and .jpeg files, .png files, but maybe put their folders under ~/Pictures.  Same again for .doc, .txt, .sh, and other files that have known extensions.  If you want the system level files as well, you need to begin the "cp" commands with "sudo " to have the permissions needed.  So you would use "sudo cp -purf" in place of "cp -purf"


  
;

---

### Post by Bucky Ball on 2015-11-02
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request and doesn't fit the criteria for a tutorial.

---

### Post by oldefoxx on 2015-11-03
After LiveCD went too far by trying to impose LVM on my existing ext4 hard drive, and did not back down enough. when the error was recognized from its end, I was apparently left with a corrupted partition table on the hard drive.  That's my best guess, but it also messed up the guts of the existing ext4 partition when it resized it, as external access to it via a LiveCD found what I think were links that were not working.  Only on refelction that does not seem right, so it had to be just a screwed-up partition table where references to folders and files were wrong in some cases..

I performed several steps to try and deal with this:

(1) used another install effort and went under "Something Else" and had the Partition Table Reset.  How this might help I didn't know, but it is one of the things I did.  Then I quit the install process, rebooted into the Try Ubuntu mode, and ran gparted.  I learned it could check a partition, so I ran the check process on both partitions.  It found a problem area on the 14.04 partition and took a long time wih it before completing, but the new 15.04 partition got a clean bill of health.  Only the laptop would still not boot up.  And gparted does not offer tools for dealing with the partition table, where my primary problems seem to be.

(2)  So I used my Boot-Repair-Disk (B-R-D or BRD for short) CD that I had made to restore the original failed 14.04 install, and again. Presto!, my laptop was bootable again.  The B-R-D iso was found online and burned to CD using my old laptop, less someone think I made it myself.  I merely downloaded it and used Brassero to burn it.  Now I use Xfburn in place of Brassero for iso burning, as it gets a fourth star and is more straightforward.

This is were I was at when I began this thread.  I thought I was home free.  I was wrong.  I just didn't have all the facts yet.  When I tried to run "sudo grub-install /dev/sda" to make my 14.04 my primary boot choice again, it failed to update the MBR, reporting problems with trying to use old technology and an ext2 partition.  But I didn't have an ext2 partition. and have never used ext2. 

Ext2 is a lowest common denominator when trying to make a linux partition compatable with DOS  and Windows, and is used for that purpose as part of the LVM project.  This is how I  identify that the LiveCD was trying to convert my hard drive over before it recognized its error and stopped.  So I had two bootable partitions, but no means to update grub to recognize and use new releases.  So this was the next challenge, and I had no answers.  So I began an New Topic for that purpose.  This time I had a question.

But as I was writing my lead post, I asked myself a question:  This isn't the first time a hard drive partition table has gotten messed up.  I mean everything fails at one point or another, right?  So how has it been fixed under Linux before?  And I began some online searches.  Turns out I found a link where some guy was trying to upgrade his system, and was talking about having two LVMs as set up by Virtualbox in an existing partition.  He was looking at setting up an LVM for the partition itself.  He likes LVM, while I have a less than favorable impression of them now.

But in his efforts, he was showing hard data that he got from using two tools:  fdisk and df.  I vaguely remember fdisk, but have never heard of df.  So I stopped to run both on my hard drive to see what they had to say.  Then I ran upgrade-grub and grub install /dev/sda again, and this time grub worked with no errors.  So I wanted to report this.  And more than that, I wanted to pass on my version of using these four commands together in a script:  There are a couple of warnings in there, but they sre only warnings, nothing serious.  I will include the results and highlight the two warnings.```
#!/bin/bash

sudo fdisk -l > tmpfile
sudo df -h >> tmpfile
sudo update-grup >> tmpfile
sudo update-grub >> tmpfile | tee tf0; cat tf0 >> tmpfile; rm tf0
# cat tmpfile | less     # Remove leading '#' if you want to see the results first hand
# rm tmpfile             # Remove leading '#' if you want to automatically remove tmpfile
```

What is in tmpfile and appears on the screen is this in my case:```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000337e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1021523532   510760742+  83  Linux
/dev/sda2      1916930048  1953523711    18296832   82  Linux swap / Solaris
/dev/sda3      1021523966  1916930047   447703041    5  Extended
**Partition 3 does not start on physical sector boundary.**
/dev/sda5      1021523968  1916930047   447703040   83  Linux

**Partition table entries are not in disk order**
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       480G  269G  187G  60% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            5.9G   12K  5.9G   1% /dev
tmpfs           1.2G  1.3M  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            5.9G   33M  5.9G   1% /run/shm
none            100M   52K  100M   1% /run/user
/dev/sr0        614M  614M     0 100% /media/oldefoxx/Boot-Repair-Disk 64bit
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-51-generic
Found initrd image: /boot/initrd.img-3.16.0-51-generic
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 15.04 (15.04) on /dev/sda5
done
Installing for i386-pc platform.
Installation finished. No error reported.
```

What was most important here was the final line:  "**Installation finished. No error reported.**".  I ran fdisk by itself when I was trying to learn how to use it, and I didn't see it do anything, so how just having it list the partition table would have helped is something I don't understand.  Nor what df did in the backgound.  But something got rid of the ext2 error, and grub was able to install again.  So this was worth passing along.

---

