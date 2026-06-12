---
title: "Just switched, my experience"
date: 2007-09-27
forum: Testimonials &amp; Experiences
---

### Post by expert01 on 2007-09-27
After the Winsock stack died on my computer, I decided that it was time to move to something my little sister wouldn't break so easily (:lolflag:).

Started off with the Ubuntu Gutsy Gibbin Tribe 5 CD. Problems right away: I didn't have the ability to back up everything and do a fresh install, and I couldn't find a free way to convert my NTFS partition to a linux compatible one (The latest Norton PartitionMagic can convert between FAT32/NTFS/ext2/ext3/reiser and a few others, but it's $60. Someone also recommended gparted, but I couldn't find info as to whether it would actually convert an NTFS partition). I ended up deleting some stuff off of my drive and using an illegit copy of Norton PartitionMagic (not the latest one) to add a ext3 and swap partition at the beginning of the drive.

Criticism: Ubuntu (and linux in general) need to support converting Windows (and other) partition types to a linux compatible one. "Go buy some CD's and back up" is not an excuse.

Popped in the CD and booted to the live distro (no problems). Started the install. Fairly straightforward, although when it came to selecting the partition to use, it had already mounted the partition I made to /media/hda1. I hit next on the installer, and it said "No partition is set as root" (or something to that effect). Had to google for a bit to find out I had to open that partition and change it to "/"

Criticism: That's a bug; Other than the error message, it should give clear details on how to fix it, and instructions should have been in that window in the first place.

Went on a few screens (going off memory here), and it came to an Import user accounts screen. It didn't find my XP installation, and didn't give me an option to specify the location.

Criticism: It should look harder for a windows installation, and it should give you an option to specify a location manually for it to search.

Finally at the desktop. This is actually my first time really using Ubuntu. A message popped up about restricted drivers being available. I clicked and it showed one driver checked, but then it said "Not used" (or something like that) next to it. I also wanted to make sure that all my devices were working properly and had updated (and full capable) drivers. I opened the device manager, but couldn't easily find that info.

Criticism: The device manager is not as detailed as XP, which can at least get the amount of RAM for any video card connected. It also shows devices with no drivers, and is more user friendly, with detailed help and some options for the device inside the device manager.

Now assuming my drivers are fine, I decide to add OpenDNS. I go ahead and change the DNS info, but OpenDNS tells me that it might not keep the changes, and gives me some commands to run.

After getting that set up, I go about changing the look. I find gnome-look, and start downloading themes and such. One problem: I have no idea how to install them. Took me a few hours to find out how (couldn't just drag and drop the tarballs, or even select the tarballs. Also tried extracting the files and dropping the folder, and then tried selecting every non image file inside the tarballs.

Criticism: The appearance preferences program seems to be a great thing, if it would work right. Granted this is still alpha, but I would expect to at least have: A link to download more themes, working help, ability to drag and drop archives (more than one) onto this pane, ability to select more than one archive in the Install screen, or a file extension just for these themes that will let me open them straight from the net and have them installed into the theme CP.

Now I try to add my backgrounds. For some reason, the first time I tried I could only do one background at a time. Finally figured out I can do ctrl or shift in the add screen.

Criticism: When I go to add a background, I can't view thumbnails, only a list. Also, I can't drag and drop pictures onto the Backgrounds screen. I also couldn't find a folder where I could dump all my pictures to have them available to everyone on my PC.

Now I went to change the login window skin. Instead of being under the Appearance Preferences screen, it's under the Login Window Preferences screen, under "Local" (which is quite a descriptive name).

Criticism: Again, need archives with file extensions associated with the control panel that will automatically import them, so I don't have to download them all into one folder, then add them one by one. This should also be in the Appearance Preferences program. Additionally, I wanted to change the GRUB boot screen (the animated ubuntu one). It's not too hard in XP (just visit [http://www.themexp.org/listings.php?type=boot&view=date&proddesc=XP%20Boot%20Screens](http://www.themexp.org/listings.php?type=boot&view=date&proddesc=XP%20Boot%20Screens) and there's plenty to find). Never found any animated ones, and I have to install a program through apt-get to change them. IMHO, this should be with the Appearance Preferences, but this isn't standard on Windows either.

Now I go to install any application I might need with Add/Remove Programs (always thought that A/R programs on windows should just drop the "Add" part). I selected all the programs I wanted, then went to install. It asked for confirmation, I hit OK. It said it would take 4 hours. I let it go for a while, then came back. It said it was downloading a game (which was apparently several hundred MB). I hit cancel, figuring I could just deselect the game and continue. Nope.

Criticism: The Add/Remove Programs app should let you change your mind while you're downloading/installing the programs. It would also be nice if it displayed the download size in the description.



Over all, I'm pretty happy with how I've set it up. I wish some stuff was more user friendly, but I'm sure that will change over time. The biggest complaint I have is over associated file extensions. I downloaded the HP printer driver (which ended in .run) and I hav to go into the terminal to run it. I should have been able to open it from firefox, or been able to double click it on the desktop. Additionally, there should be an option to right click on a program and "Run Elevated" (sudo or gksu). It's a pain to have to go to terminal every time I need elevated privileges to install a program. Or, it could just tell me I need elevated privileges and ask for a pass (kind of like Vista).

---

### Post by wolfen69 on 2007-09-27
um, this may come as a shock, but you dont need to convert an ntfs partition ahead of time. ubuntu will convert it automatically during install. second thing, dont use a beta OS. wait til it officially comes out before complaining. i couldnt bring myself to read the rest. good luck.

oh btw, criticizing and complaining on these message boards amounts to nothing. you need to grab the attention of the developers to make a difference. otherwise you're just venting.

---

### Post by expert01 on 2007-09-27
um, this may also come as a shock, but [Searching for Ubuntu automatically converting NTFS during installation]("http://www.google.com/search?q=ubuntu+automatically+convert+ntfs+installation&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") doesn't bring up anything. Nor did I find anything on the wiki. Second thing, I'm using a beta OS so that I can jump in on the latest technology, and I'm not complaining. I am posting my experience, and offering **constructive** criticism. I assume that some developers read the Experiences forum occasionally for feedback on their work. All criticism in the topic was about minor improvements that should be done before it's declared final, from the viewpoint of someone who hasn't installed Ubuntu before (The only distro I've used is CentOS for Trixbox). And lastly, if you can't be bothered to read a full post, then you really shouldn't even respond to a topic. That's akin to reading the first page of a book and writing a review about the book for a newspaper.

---

### Post by agurk on 2007-09-27
You have some valid points there. It's always valuable to get feedback from users' first impressions. Oh, and Ubuntu doesn't convert any NTFS partitions upon installation; however, you can mount NTFS partitions just like you can mount Ext3 ones. I use the ntfs-3g driver from the repositories myself, never had a problem with it.

---

### Post by expert01 on 2007-09-27
I also installed the ntfs-3g driver once I finished installing, so I could access all my files on the unconverted partitions. I suppose at some point I'll get them converted, but it works right now.

---

### Post by adamonduty on 2007-09-28
I also think you should be Feisty and not Gutsy. There are all kinds of weird things that can go wrong in a beta OS. You can try Gutsy when it comes out in the next couple of weeks. Plus, fewer people are familiar with the changes so you'll have less people to help you if you run into a problem.

You should probably try using Synaptic to install programs.... Add/Remove programs is a bit basic. Choose System -> Administration -> Synaptic Package Manager.

---

