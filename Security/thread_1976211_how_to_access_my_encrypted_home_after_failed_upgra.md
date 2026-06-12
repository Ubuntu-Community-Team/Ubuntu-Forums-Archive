---
title: "how to access my encrypted home after failed upgrade and unbootable system"
date: 2012-05-08
forum: Security
---

### Post by PfromD on 2012-05-08
How can I either achieve what's described in the title or complete the failed upgrade. The upgrade ended up shutting off the computer on its own due to lacking free space.

There's more information on exactly what went wrong and how here:
[http://ubuntuforums.org/showthread.php?t=1975862]("http://ubuntuforums.org/showthread.php?t=1975862")

---

### Post by cryptotheslow on 2012-05-08
This should help:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory)

---

### Post by PfromD on 2012-05-09
Damnit! The response from the terminal is this:
cant' find /dev/sda5 in /etc/fstab or /etc/mstab.
I followed the manual in the link exactly, and are 100% that sda5 is what I'm after. Might it be because I'm using a 12.04 live disc where the manual covers a version much prior to that?

---

### Post by cryptotheslow on 2012-05-09
Those instructions should work fine.

Can you post up the output to these two commands (from the LiveCD environment):

sudo blkid

sudo fdisk -l

That's a lowercase L :)

---

### Post by PfromD on 2012-05-09
BOTH outputs?
The fdisk -l is pretty extensive

Aren't there a 'print to file' possibility for those outputs?

---

### Post by cryptotheslow on 2012-05-09
Either or both :)

And are you able to use Nautilus to access the old partition and see your encrypted home directory?

---

### Post by PfromD on 2012-05-09
Yes, I can see the SEE the directory, but not access it :(

---

### Post by cryptotheslow on 2012-05-09
That's odd. I've used those instructions before just fine. Which method are you trying? The long or the short way as they are described there?

---

### Post by PfromD on 2012-05-09
The long .. except not so long when it comes with the mentioned reply after the first step :-/

---

### Post by cryptotheslow on 2012-05-09
Hmm. I'm going to give it a run through now and see how it goes.

---

### Post by PfromD on 2012-05-09
But can't I 'print to file' the output you mentioned?
It's just that I can't get the internet to work on the live Ubuntu for some reason, so it's pretty lengthy having to switch between Live and WinXP all the time

---

### Post by cryptotheslow on 2012-05-09
Yes you should be able to put the output to file.

e.g. 
sudo blkid > outfile.txt

will create outfile.txt with the results of the command in it.

I just ran through the short way from those instructions (as that is what I have used before) and it fails on the very last stage of mounting the encrypted directory. :(

Just going to run through the long way now.

---

### Post by cryptotheslow on 2012-05-09
OK - give me a little time. I get the same problem with that mount command.

I'll work through it then post up a walkthrough here once I've got it done :)

---

### Post by PfromD on 2012-05-09
You'll rise to the level of 'my new hero' if you can make it work, that's for sure .. I'm starting to panic and already sick of having to use XP. It re-ensures me that Ubuntu is the right choice though. Guess it's like never knowing the power of love until you loose a loved one.

---

### Post by cryptotheslow on 2012-05-09
OK. Started getting a headache so I took a different approach :)

This will work if on your previous install your user was the only (or first user) i.e. userid 1000

I pieced this approach from here:
[http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/](http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/)

It basically involves booting up from the LiveCD and creating a user account with the same ID as the old install user then mounting the home dir.

I hope the below makes sense. I have added comments with the >>> in front.

So boot up from the 12.04 Ubuntu Desktop Live CD, take the "Try Ubuntu" option, open a Terminal and away we go.....

cryptotheslow is my username - substitute it for your own wherever it appears.

```

**>>> check you know which partition you want**

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x496b9619

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    52430847    26214400   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    52430848   536088575   241828864    7  HPFS/NTFS/exFAT
/dev/sda3       536089050   556569831    10240391    7  HPFS/NTFS/exFAT
Partition 3 does not start on physical sector boundary.
/dev/sda4       556572670  1465147391   454287361    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1311547392  1459984383    74218496   83  Linux
/dev/sda6      1459986432  1465147391     2580480   82  Linux swap / Solaris
/dev/sda7       556572672   863772671   153600000   83  Linux
/dev/sda8       863774720   867678207     1951744   82  Linux swap / Solaris

Partition table entries are not in disk order

[B]>>> I have an old 12.04 install in /dev/sda5 with an ecrypted home user.
>>> Mount /dev/sda5 somewhere handy:[/B]
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt

**>>> Add the replacement / dummy user _**NB Make sure to use the same username and passsword as on the install you are trying to rescue files from**_**
ubuntu@ubuntu:~$ sudo adduser --no-create-home --home /mnt/home/cryptotheslow cryptotheslow
Adding user `cryptotheslow' ...
Adding new group `cryptotheslow' (1000) ...
Adding new user `cryptotheslow' (1000) with group `cryptotheslow' ...
Not creating home directory `/mnt/home/cryptotheslow'.
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for cryptotheslow
Enter the new value, or press ENTER for the default
    Full Name []: 
    Room Number []: 
    Work Phone []: 
    Home Phone []: 
    Other []: 
Is the information correct? [Y/n] y

**>>> Put a link to to the newly mounted .ecryptfs config file in the LiveCD's home directory**
ubuntu@ubuntu:~$ sudo ln -s /mnt/home/.ecryptfs /home/.ecryptfs

**>>> Make a directory for the user's files you are rescuing. The unencrypted home dir will end up here. Also make sure the permissions are correct:**
ubuntu@ubuntu:~$ sudo mkdir /home/cryptotheslow
ubuntu@ubuntu:~$ sudo chown cryptotheslow:cryptotheslow /home/cryptotheslow

**>>> Switch user to the user you are recovering files for:**
ubuntu@ubuntu:~$ sudo su - cryptotheslow
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'

**>>> Unencrypt the home dir for the user - enter the login password that you used on the original install for this user when prompted:**
cryptotheslow@ubuntu:~$ ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [fa0516369a9d60dd] into the user session keyring
cryptotheslow@ubuntu:~$ ls
Access-Your-Private-Data.desktop  README.txt

[B]>>> UH-OH! Where's my files?
>>> Here:
[/B]cryptotheslow@ubuntu:~$ cd /home/cryptotheslow
cryptotheslow@ubuntu:/home/cryptotheslow$ ls
Desktop    Downloads         Music     Pictures  skipfish   Ubuntu One          Videos
Documents  examples.desktop  pathping  Public     Templates  ubuserver_shared
cryptotheslow@ubuntu: YAY o/

```

At this point, leave that terminal exactly as it is and open another Terminal session (Ctrl-Alt-T) and run **gksu nautilus**

With that browse to /home/cryptotheslow and copy the files you need off to whatever removable drive / other partition etc. as you wish.

---

### Post by PfromD on 2012-05-09
neat. going to give it try so it won't be the messy 'outfile.txt' as windows doesn't recognize/accept the linux line shifts and so on.
I assume the password need to be the same as on the now wrecked install.

---

### Post by cryptotheslow on 2012-05-09
Yes the password should be the same as on the wrecked install - both when creating the user (with adduser) and when unencrypting the home dir (ecryptfs-mount-private).

Good luck - let us know how you get on :)

---

### Post by PfromD on 2012-05-10
Ok, you're really really close to the elevation of super-mega-über-hero :) BUT :(
I was able to browse to, and see all the files I don't want to loose, but neither open nor copy :confused:
Everything just fine until the very last step where some error message came out:
```

ubuntu@ubuntu:~$ gksu nautilus
Initializing nautilus-gdu extension
Shutting down nautilus-gdu extension
Error: Expected the default config, but wasn't able to find it, or it isn't a Dictionary
Error: May not be a PDF file (continuing anyway)
Error (193): Illegal character '{'
Error (202): Illegal character '}'
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table
Error: May not be a PDF file (continuing anyway)
Error (193): Illegal character '{'
Error (202): Illegal character '}'
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table

(nautilus:4131): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9Y8PDW': No such file or directory

(nautilus:4131): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
Warning: failed to read path from javaldx

(nautilus:4131): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.ZCA8DW': No such file or directory

(nautilus:4131): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```
First I was thinking that this could be due mistakes in First letter of new (and old) user being capital letter, but I guess if that where the case I wouldn't be able to see the files in the first place .. and what's the message terminal is trying to deliver with what I copied into the code field?
This is like having the worlds best candy dangling just ½ an inch out of reach :´(

---

### Post by cryptotheslow on 2012-05-10
The GTK warnings are nothing to worry about.

The messages at the top are indicating the pdf file you are trying to open is damaged in some way.

What errors / messages / problems do you have when trying to copy the files off?

---

### Post by PfromD on 2012-05-10
basically just that I can't do it. can't remember the exact wording right now.
But it's not only the PDF, it's every file in the directory that I can't open :(
Going to go through it again and come back with the messages but I'm about to get some sleep now

---

### Post by cryptotheslow on 2012-05-10
In that case the file table may be damaged, which would probably be fixed with a fsck (file-system check before you think that was a typo!).

What format is /dev/sda5? (ext2, ext3, ext4 etc.?) That will determine what command to use to run the fsck.

Let's see what those errors you are getting are first.

---

### Post by PfromD on 2012-05-11
Ok, a little update:
I was able to copy a file within/to another folder in the drive/folder opened with 'gksu nautilus', but not open :(
Also I can't see any other drives in the nautilus opened.

The command also starts with this message:
"Nautilus could not create the required folder &#8220;/root/.config/nautilus&#8221;
Before running Nautilus, please create the following folder, or set permissions 
such that Nautilus can create it&#8221;
 and attempts to open a file returns this:
"Read error
unknown error has ocurred"

sda5 is in ext4

edit: sorry, ext3 (according to partition magic)

---

### Post by bodhi.zazen on 2012-05-11
Actually you are all going about this the hard way =)

Use ```
sudo ecryptfs-recover-private 
```

See : [http://bodhizazen.net/Tutorials/Ecryptfs#Live](http://bodhizazen.net/Tutorials/Ecryptfs#Live) for details.

---

### Post by PfromD on 2012-05-11
At what stage? Instead of the 
">>> Unencrypt the home dir for the user - enter the login password that you used on the original install for this user when prompted:
cryptotheslow@ubuntu:~$ ecryptfs-mount-private" part?

---

### Post by PfromD on 2012-05-11
Ok. I ran through the process bodhi.zazen mentioned, and it apparently works ... to some extend :(
I'm able to open and view several files, but of course not the most important one where I still get a response of:
"Read error
unknown error has occurred"
ARG!

---

### Post by cryptotheslow on 2012-05-11
That's annoying :(

I'd recommend running a filesystem check. Boot into the Live CD and before mounting the partition:

sudo e2fsck -fpv /dev/sda5

It would also be worth opening Disk Utility via the dash and have a look at the SMART data for the drive and see if it is showing any amber or red warnings.

---

### Post by PfromD on 2012-05-11
will do, except that I don't quite know what you mean by "via the dash"
The weird part is, that it's apparently only the all-important .ods files and their parent .ots files that are 'infected' with this "unknown error" problem

---

### Post by cryptotheslow on 2012-05-11
"from the dash" - click on the top icon of the launcher bar called "Dash Home" and search for Disk Utility in there.

If it is just ods / odt files having problems that may simply be some odd problem with LibreOffice opening from a gksu nautilus session.

That shouldn't stop you copying them to a usb stick or whatever and then opening them with LibreOffice or OpenOffice once you've rebooted into Windows.

---

### Post by bodhi.zazen on 2012-05-11
> **PfromD said:**
> will do, except that I don't quite know what you mean by "via the dash"
The weird part is, that it's apparently only the all-important .ods files and their parent .ots files that are 'infected' with this "unknown error" problem

"unknown error" is an unknown problem, most likely a sign of hardware failure or perhaps the file is corrupt in some way. You may not be able to recover it.

---

### Post by PfromD on 2012-05-11
here's the output from e2fsck
```

  472704 inodes used (64.37%) 
    2633 non-contiguous files (0.6%) 
     743 non-contiguous directories (0.2%) 
         # of inodes with ind/dind/tind blocks: 0/0/0 
         Extent depth histogram: 438263/541 
 1652384 blocks used (56.36%) 
       0 bad blocks 
       1 large file 

  364746 regular files 
   70067 directories 
       0 character device files 
       0 block device files 
       0 fifos 
       1 link 
   37882 symbolic links (33890 fast symbolic links) 
       0 sockets 
-------- 
  472696 files 

```

And the thing is, that so far I haven't been able to copy the files anywhere except for 'inside' the nautilus session opened in both your and bodhi.zazen's methods.
I'll try again just to make sure but bodhi.zazen method takes about ½ an hour and starting windows about 10 min, so it'll be a while before I can come back with the result

---

### Post by PfromD on 2012-05-11
> **bodhi.zazen said:**
> "unknown error" is an unknown problem, most likely a sign of hardware failure or perhaps the file is corrupt in some way. You may not be able to recover it.
I just don't see why it is only a couple of .ods and .ots files that are affected then ...
And I've done absolute no changes in partitions sine the faulty upgrade where they worked perfectly fine before.

---

### Post by bodhi.zazen on 2012-05-11
> **PfromD said:**
> I just don't see why it is only a couple of .ods and .ots files that are affected then ...
And I've done absolute no changes in partitions sine the faulty upgrade where they worked perfectly fine before.

Guess that is why it is an "unknown" error.

---

### Post by PfromD on 2012-05-11
The Disk Utility didn't return any errors, although the test seemed to go awfully fast, so I'm not to sure I did it right. Could only see one way of doing it though.
> 
Guess that is why it is an "unknown" error. 

Isn't it possible to check individual files for errors and hopefully remake them that way?

---

### Post by cryptotheslow on 2012-05-11
Where are you trying to copy the files to?

---

### Post by PfromD on 2012-05-11
Either to the 1.5 GB space I made before attempting the update, but didn't manage to incorporate into the existing 'main' Linux partition, or the NTFS drive that WinXP is on. The latter is probably the easiest in terms of getting support from here while -hopefully- making the files work again .. though I don't seem to be able to copy them anyway as is now. This is a real nuisance.

---

### Post by cryptotheslow on 2012-05-11
OK.

Presuming you know what partition your WinXP drive is (as in /dev/sda1 or /dev/sda2 etc.)

Once you have gone through the process and have the **gksu nautilus** window open......

Open another Terminal window and mount your WinXP drive thus:

```

sudo mkdir /media/windrive
mount -t ntfs /dev/sda1 /media/windrive

```

Obviously use the correct sda number in that mount command!

At that point you will see **windrive** appear in the Devices list in the open Nautilus window. Right click on it and select "Open In A New Window". Now you have two Nautilus windows running with admin privilege and you should be able to copy / paste the files from one window to the other.

I have just tested this myself from a LiveCD and it works fine. :)

GL

---

### Post by cryptotheslow on 2012-05-11
If the ods / odt files are completely corrupt or unrecoverable you may want to have a read of this:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=17&t=16040](http://user.services.openoffice.org/en/forum/viewtopic.php?f=17&t=16040)

Apparently OpenOffice keeps backups of files - I've no idea if that is just when they are being edited, I've also no idea if LibreOffice does the same if that is what you use. Just another avenue of possible exploration :)

---

### Post by PfromD on 2012-05-12
> **cryptotheslow said:**
> If the ods / odt files are completely corrupt or unrecoverable you may want to have a read of this:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=17&t=16040](http://user.services.openoffice.org/en/forum/viewtopic.php?f=17&t=16040)

Apparently OpenOffice keeps backups of files - I've no idea if that is just when they are being edited, I've also no idea if LibreOffice does the same if that is what you use. Just another avenue of possible exploration :)

I haven't tried or used LibreOffice besides via live CD.

I also came in to a problem the method cryptotheslow described for copying the homefolder to my windows drive.
From my understanding I should end up with having three terminal sessions open at once, but in the last terminal I got this error:
"Mount: only administrator allowed to do this"
I might be paraphrasing the actual wording a bit as I'm catching up on some recorded Simpsons while doing this :) and switching between LiveCD and Win takes about 10-15 minutes :)

---

### Post by cryptotheslow on 2012-05-12
Ooops - my fault. That should of course have been:

```

sudo mount -t ntfs /dev/sda1 /media/windrive

```

---

### Post by PfromD on 2012-05-12
my fault as well .. I ought to have seen that my self :)
well .. going through the endlessly long alley again ;)

---

### Post by PfromD on 2012-05-12
You know .. I've read somewhere, that men don't take backups- they cry.
Yet I haven't cried during this ordeal, just been seriously frustrated, especially when the .ods's wouldn't open in LiveCD despite no logical reason for not doing so.
But now .. now I've shed a tear. A tear of rejoice and utter happiness .. IT WORKED! IT WORKED!
I rally can't thank you enough for getting me through this damn misery. I'm not even sure it's proper to only elevate, as initially mentioned, to super-mega-über-hero.
You seriously have no idea how happy this has made me .. I've opened every one of the critical documents several times, just because I can't believe it finally worked.
Hand me an (bank)account I can thank you personally on or at least let me buy you a pint  if in UK. Or go to the UK, just for that reason. Happy Happy Happy =D> =D>

---

### Post by cryptotheslow on 2012-05-12
Glad you got it sorted eventually :D I think most people go through a trial like this before they take the hassle of keeping regular backups as a necessary evil rather than just hope for the best and go without :D

I am in the UK but no need for any payment or pint. God knows how many times these forums have helped me out - I'm just glad to be able to give a little back. :guitar:

---

### Post by PfromD on 2012-05-12
Well .. one COULD say that a backup was/isn't necessary anyway when you can get primo help here ;-)
But ok then .. I'll swallow the tiny pill and go through the minimal hassle of actually doing it from now on.
Now I just need to find, if possible, the bookmarks of the now wrecked install and find the way to install 12.04 without the dash, or in other words; to make it more like the UI I had gotten familiar with. The dash thing seems to hide far to many thing somewhere way less intuitive than what I'd grown accustomed to.
Somewhat like going from bicycle to car with no steps in between.

---

### Post by PfromD on 2012-05-12
And apart from that .. the file reading issue turned out to be not an issue of file corruption or harddrive failure;
I tried to open one of the failing .ods via LibreOffice from LiveCD and the rescued folder on the Windows drive ..
"file couldn't get opened; unknown error", in other words some sort of incompatibility between OpenOffice and LibreOffice as it works flawlessly in OpenOffice.
It's a rather complex spreadsheet and there has apparently been made a change somewhere in some of the deeper functionality.

---

### Post by cryptotheslow on 2012-05-12
No matter how good the help anywhere - if your hard drive physically fails you will be completely unable to recover anything. That has happened to me before - not good.

Now my laptop and desktop backup to my little home server which is turn is backed up to an external USB drive which is kept in a safe place between backups. On top of that, my really critical files I copy into strongly encrypted containers and store them in various cloudy online backup places. Belt and braces for sure :)

If by bookmarks you are referring to Firefox, then they are contained somewhere in a directory called .mozilla (note that starts with a dot) within your home directory. You can copy off that folder in the same way as you did the other stuff. Just be aware that when you browse to your home directory using Nautilus that folder will be hidden - just press Ctrl H to display hidden files/folders.

You can drop that whole .mozilla directory into the home directory of your user on the new installation when you get to that point and firefox will use it next time you run it.

As for the UI changes - have a look around these forums for threads about Gnome Classic desktop. There is a sticky around somewhere (probably the Desktop Environments section) with details on how to get that working. It gives a desktop that is almost identical to the one we were used to with 10.04, 10.10 etc.

It maybe worthwhile taking a copy of your entire home directory from the wrecked insta;l;l to an external drive before doing the reinstall - you can then copy in whichever settings you find you need after reinstallation.

*edit - *Ahh - that explains the error messages - Libre and Open Offices have diverged a bit since being forked.

---

### Post by PfromD on 2012-05-12
As my comment indicated I don't really see it as any hassle doing the proper backup .. just never done it. 
Well, did it in WinXP, but that's because of an overall bad user experience when opposed to Ubuntu. Loads of problems with WinXP vs. literally years of Ubuntu with not a single problem. 
Well ... no problems until the updater 'lied' to me.

Concerning the read error I see it as a case of seriously bad or 'egoistic' programming when Libre runs in to a case of "no, I don't want to read that, because THAT was made by my 'mother' and I really don't agree with her", and not even letting the user know that this is the case and offer to change whatever is wrong to "our new and MUCH better way of doing it". See my point?
From what I understand the reason for the fork to be, it's something about OOo not being, or soon not being, as both free speech AND free coke as the Libre folks would like it, or something with impending payment for some of the functionality. right?
But with the underlying problem here being that Libre won't read something that has diverged since OOo, who the f*** are Ubuntu (AND Libre) to say that this is the way it's going to be, and whatever problems arise -such as this- is just too sad for you .. not our problem. I mean .. WTF

---

### Post by cryptotheslow on 2012-05-12
I can't say I'm up to speed on the Libre fork politics beyond reading a few ranty opinions I stumbled across while doing other stuff.

As you say your spreadsheets are complex it may well be that you have utilised functionality introduced to OOO since the Libre fork - so when Libre tries to open the file it baulks on that particular element as it simply doesn't understand it, rather than some deliberate "my mother made that so I won't play" conspiracy. I doubt there would be any problem opening a pre-fork OOO file with Libre.

Anyway - kinda irrelevant as you can always uninstall Libre and install OOO on Ubuntu12.04 as far as I know. 

Ubuntu has always steered away from _anything_ non-free but tries to make it relatively easy for users to use such things e.g. their approach to mp3 codecs during install.

Neither Ubuntu or Libre are saying anything like "this is the way it's going to be" - Ubuntu bundle Libre now sure, but nothing stops you using OOO on Ubuntu. There's also no onus on Libre to support post-fork additions to OOO. It does bring the whole concept of open file formats into doubt - if two projects using the same file formats have to expend energy coding converters for files produced by the other it's not really that productive - the more they diverge the more effort gets wasted working on the converters that could be used on enhancing the functionality of the actual software.

Anyways - if you've managed to live with Ubuntu since 7.10 with no issues at all then that's pretty impressive. But regardless how flawless the OS may be there's no excuse not to take backups, hardware will fail at some point. At least this time it was just a software foobar and you recovered your stuff.

Oh - have you filed a bug on Launchpad about the updater not checking for sufficient disk space to perform an upgrade?

---

### Post by PfromD on 2012-05-13
It's even prior to 7.10 .. Gutsy Gibbon is just when I came on this forum :)
No, I didn't mean it as in any kind of remotely conspiratorial reason for the file not being able to open up in Libre, but since the coding it self is pretty much standard, except for maybe *one* function that I'm kind of suspecting might the the one that's garbles up the whole thing for Libre. If it's the complexity it self then it really doesn't speak to Libres advantage.

And I haven't filed any bug reports on this failed upgrade, but it might be a good idea. The update was literally like 95% done when problems started arising, so in the end it couldn't have been much more than maybe 50-100 MB that made it all go haywire. Initially it complained about needing 680MB more to complete the update, so I freed up about a gig .. and STILL this happened :mad:
But 'launchpad'?

---

### Post by cryptotheslow on 2012-05-13
Launchpad is the system that Ubuntu use to track bugs in packages.

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Although I'm not sure what package you would file the bug against :confused: Probably update-manager I suppose.

From a running system you could just do a 
```

ubuntu-bug update-manager

```

However, with a wrecked install you'd need to manually gather all the information and logs required to attach to a bug report. Not fun :(

---

### Post by PfromD on 2012-05-13
And since I have no running system except for LiveCD, and haven't had much luck in getting the internet to work on *that* -haven't tried hard though- I guess a bug report is kind of never-mind.

---

