---
title: "Howto: Easily encrypt individual folders"
date: 2011-03-05
forum: Tutorials
---

### Post by Dreamsorcerer on 2011-03-05
**Howto: Easily encrypt individual folders**

                               **Original**: [http://blog.sambull.org/easily-encrypt-folders](http://blog.sambull.org/easily-encrypt-folders)[]("http://blog.sambull.org/linux/tips/easily-encrypt-folders/")


Encfs is a program that can be used to encrypt folders, unlike  other encryption methods this doesn&#8217;t require a file of a fixed size, so  you can use the decrypted folder in the same way as a regular folder  without worrying about space.
 This tutorial will explain a convenient way to use this tool.
 This method can both be used from the GUI and the command line.
To understand if this is what you want please read the example in the usage section at the bottom before going through the setup.

 **Pre-installation**

 First, you will of course need to install the encfs program, the  easiest way to do that (on Ubuntu) is to try clicking this link:

 [apt:encfs](apt:encfs)

 or copy this into a terminal:

 sudo apt-get install encfs -y

 In addition to this we will be using gnome-encfs, a small program  that allows you to use the gnome-keyring to store encryption passwords.  This program by Oben Sonne can be found [here]("https://bitbucket.org/obensonne/gnome-encfs/"), after downloading it, extract the gnome-encfs file to your home folder.

 Then to install it run:
 sudo install gnome-encfs /usr/local/bin

 **Installation**

 To do this, we will be using a couple of scripts, that can be used in Nautilus (the file manager) or from the command line.

 **Scripts**

 To install these scripts just save them into ~/.gnome2/nautilus-scripts/ (that is the folder nautilus-scripts in the .gnome2 hidden folder in your home folder):

 You can download the first script [here]("http://sambull.org/scripts/emount") (or attached to this post).  Right-click > Save as, then save it in the above folder (Ctrl+H  shows hidden folders). Save it with whatever name you want to appear in  the menu.

 Repeat this for the unmount script, found [here]("http://sambull.org/scripts/eumount") (or attached to this post).

 In order to allow them to run, you need to make them executable, in the terminal this can be done by copying and pasting:
 chmod +x ~/.gnome2/nautilus-scripts/emount ~/.gnome2/nautilus-scripts/eumount

 Don&#8217;t forget to change the emount and eumount names if you&#8217;re using different names.

 Now if you right-click on a folder, go to scripts, you should see emount and eumount (or whatever you named them). Read the usage section to find out how to use them.

 **Command Line**

 To use the scripts from the command line, we need to make symlinks, just run:

 sudo ln -s ~/.gnome2/nautilus-scripts/emount /usr/local/bin/emount &&
sudo ln -s ~/.gnome2/nautilus-scripts/eumount /usr/local/bin/eumount

 Change the first emount to the name you saved for the GUI, and the second emount to the name you want to use for the command. Repeat with eumount.

 **Usage**

 I&#8217;ll give a little example here to demonstrate usage. Let&#8217;s  say your Pictures folder contains some naughty images and you&#8217;d like to  encrypt the entire folder. Let&#8217;s also say we want to do this from the  GUI without using the command line.

 [[IMG]http://blog.sambull.org/wp-uploads/2010/12/usage0.png[/IMG]]("http://blog.sambull.org/wp-uploads/2010/12/usage0.png")
The contents of my Pictures folder.

 **Encrypting**

 Simply right-click and emount the folder you want to  encrypt. A window will now pop-up asking for the name of the folder  where the decrypted contents will be displayed, I&#8217;ll use pictures-decrypted for this, you can use any name you like.

 [[IMG]http://blog.sambull.org/wp-uploads/2011/02/screenshot1.png[/IMG]]("http://blog.sambull.org/wp-uploads/2011/02/screenshot1.png")
Naming the decrypted folder.

 It will then ask if you want to have it automatically mount at login,  this will allow you to have it always decrypted for you, but make sure  nobody else will be able to see the contents without logging in.  Finally, it asks you for a password, this is the password you want it to  use for decrypting the folder (not your login).

 You will then see a new folder has been created, in my case it&#8217;s  called pictures-decrypted. This new folder is the decrypted contents of  the Pictures folder. If you add any new files, you need to save them into this decrypted folder, they will then automatically be encrypted.
 [[IMG]http://blog.sambull.org/wp-uploads/2011/02/usage2.png[/IMG]]("http://blog.sambull.org/wp-uploads/2011/02/usage2.png")
The folders after decrypting.

 **Unmounting**

 Simply right-click pictures-decrypted and select eumount. The decrypted folder should now have vanished.

 If you look in the Pictures folder you will see that the contents are  all encrypted and you will be unable to view any of the files.

 [[IMG]http://blog.sambull.org/wp-uploads/2010/12/usage3.png[/IMG]]("http://blog.sambull.org/wp-uploads/2010/12/usage3.png")
With the contents encrypted nobody will be able to view them anymore.

 **Command Line**

 This works similarly to the GUI, but used from the command line:
 emount foo/
 will decrypt (or encrypt if it&#8217;s not encrypted yet) the foo folder. While:
 eumount bar/
 will unmount the bar folder.

 **Auto-mount tip**

 If you are going to auto-mount the folder on login, then you could rename the encrypted folder to something like .pictures-encrypt  (the . makes it a hidden folder). Then when you make it encrypted, you  can name the decrypted folder Pictures, so the encrypted folder remains  hidden, and the decrypted folder acts like your normal pictures folder.

 **Decrypting**

 Now in future all you have to do is right-click the Pictures folder  and select emount. It will then retrieve your password from  gnome-keyring and the decrypted folder will appear there with all your  pictures in, and right-clicking and eumount will make them disappear  again, so nobody will be able to view them without your password.

 **Extension**

 I&#8217;ve written a follow-up post to this one that explains how this can  be used to encrypt Firefox data seamlessly. You can read it [here]("http://blog.sambull.org/linux/tips/encrypt-firefox/").

---

### Post by Dreamsorcerer on 2011-03-21
21/3/2011 - Updated the scripts, so you no longer need to move around files. Simply right-click a folder and click emount, and it will encrypt your folder.
26/3/2011 - Fixed a bug in the script if you cancel unlocking the keyring.
28/3/2011 - Fixed GUI/CLI check. Fixed issue creating mount with full path.
4/7/2011 - Fixed a bug when folder names contain spaces.

---

### Post by ugm6hr on 2011-03-27
Gave this a try, and can't get the GUI to work....
Not sure where the problem is at all.

When trying CLI:
```
emount ~/Documents/Files
/usr/local/bin/emount: line 28: 1: command not found
mkdir: cannot create directory `': No such file or directory
No matching EncFS items in keyring.
Use option --list to show available items or option --add to add items.

```

The shortcut usr/local/bin/emount exists, so uncertain why the 1st error comes up. Same output whether command ends with / or not.

---

### Post by dot2kode on 2011-03-28
Very nice...Thanks for sharing! :D

---

### Post by Dreamsorcerer on 2011-03-28
> **ugm6hr said:**
> Gave this a try, and can't get the GUI to work....
Not sure where the problem is at all.

When trying CLI:
```
emount ~/Documents/Files
/usr/local/bin/emount: line 28: 1: command not found
mkdir: cannot create directory `': No such file or directory
No matching EncFS items in keyring.
Use option --list to show available items or option --add to add items.

```The shortcut usr/local/bin/emount exists, so uncertain why the 1st error comes up. Same output whether command ends with / or not.

The first error occurs due to the line: ```
if ! $?; then
```It's actually trying to run $? as a command, classic case of fixing one bug and introducing another :P. I've fixed this by making it "echo $?".

I also realised that my checks for running from the GUI were crap, that's fixed as well.

Finally, from your example I realised there was a bug in creating a new mount point when using a full path name, also fixed.

It's also worth noting, that in your example the decrypted mount point would be created in the working directory, probably your home folder, rather than in the Documents folder. I'm not sure if it would be a better design to put it in the same folder by default or not, so for the moment I will leave it with this behaviour. (This obviously isn't an issue when using it from the GUI, as the working directory will always be the same place as the folder.)

EDIT: Woops, actually it needs to be changed to "if [[ `echo $?` == "0" ]];".

---

### Post by ugm6hr on 2011-03-28
I'll give the updated scripts a go later this week.
I don't expect to be using CLI - so not that worried about the default behaviour.
But perhaps just mention the default behaviour in the main How-To, and include a brief description of cd to alter the destination location?
Thanks again.

---

### Post by Enigmapond on 2011-03-28
Well I've done everything, checked it thrice and still I get no GUI... I'll keep at it...thanks for the How-To though!

Cheers!

---

### Post by Dreamsorcerer on 2011-03-29
> **Enigmapond said:**
> Well I've done everything, checked it thrice and still I get no GUI... I'll keep at it...thanks for the How-To though!

Cheers!

What exactly do you mean you get no GUI? If you right-click on a folder, do you see emount and eumount under scripts? Do you mean that nothing happens after you click emount?

I find that if there's a problem with the GUI, the command line version will be broken as well, in which case try running it from the command line and pasting the output.

---

### Post by ugm6hr on 2011-04-02
Given the updated scripts a trial, and it seems to work OK (from nautilus GUI).
I'll continue to use it for a while and report problems back.
Thanks. This is a nice solution that allows encryption after the fact.

PS: I presume there is no problem with using this to encrypt folders on USB / SD cards?
If so - as long as I install encfs and your scripts, I should be able to decrypt on any Ubuntu computer, right?
Does it matter what format the drives are? I use ext4 for HD, but ext3 or fat32 for SD / USB.

PPS: Maybe you should include a list of Ubuntu variants it works on? This ensures tutorials remain up-to-date. Both mine are Ubuntu 10.10 (32-bit).

---

### Post by Dreamsorcerer on 2011-04-03
> **ugm6hr said:**
> PS: I presume there is no problem with using this to encrypt folders on USB / SD cards?
If so - as long as I install encfs and your scripts, I should be able to decrypt on any Ubuntu computer, right?
Does it matter what format the drives are? I use ext4 for HD, but ext3 or fat32 for SD / USB.

I don't believe there to be any problems with this, it's simply using an EncFS mount, so look at they're documentation for any limitations. Technically, you should be able to use EncFS directly to mount it. Using gnome-encfs allows you to use a password saved into your gnome-keyring to mount, and my script allows you to do it easily from the GUI, but you should still be able to mount it with only EncFS installed.

> **ugm6hr said:**
> PPS: Maybe you should include a list of Ubuntu variants it works on? This ensures tutorials remain up-to-date. Both mine are Ubuntu 10.10 (32-bit).
I'm using 10.10 (64-bit). I would expect it to work on any system that can run EncFS, and using Nautilus (the scripts will probably need a small modification to run in other file browsers).

---

### Post by ugm6hr on 2011-05-24
Been using this a while - it works well.
Although, folders on my SD card appear not to effectively decrypt on a different computer from the one on which it was encrypted.
Not sure why.

---

### Post by Dreamsorcerer on 2011-05-30
> **ugm6hr said:**
> Been using this a while - it works well..
Thanks, nice to know.
> **ugm6hr said:**
> Although, folders on my SD card appear not to effectively decrypt on a  different computer from the one on which it was encrypted.
Not sure why.
Not sure what the problem is there, I would expect it's something to do with EncFS. Random speculation, but maybe it could be a limitation of the filesystem? I'm guessing your SD card is formatted to FAT32, maybe you could try creating an ext2 partition and see if it works then?

---

### Post by ugm6hr on 2011-05-30
OK - my mistake....
My SD is ext2 (or maybe ext3 - I can't recall!)
The problem is if when you first run "emount" on the 2nd computer. If you fail to give the correct name to the decrypted folder - it then won't allow you to change it - perhaps ever?
I've just re-installed and overwritten my old /home
Having done so - I tried again - and it appears to work OK.
PS: After running emount script on 2nd computer, and adding correct decrypted folder and password, a restart is required.

---

### Post by Dreamsorcerer on 2011-05-31
> **ugm6hr said:**
> The problem is if when you first run "emount" on the 2nd computer. If you fail to give the correct name to the decrypted folder - it then won't allow you to change it - perhaps ever?

Ah, in that case it may be a limitation of my script. For now, if you go to System>Preferences>Passwords & Encryption Keys, you will find all the details are stored in a password keyring. If you make a mistake just manually delete the appropriate password from there and then emount again. I think you can edit these from the CLI using gnome-encfs ("man gnome-encfs") if you can be bothered, personally I just delete the key and repeat (which I had to do a lot when debugging :P).

---

### Post by ugm6hr on 2011-08-18
One more problem...
The "Cancel" option needs to actually work.
If you "enount" a folder accidentally, and then select cancel - it appears that you lose the entire folder contents.
I can't see any way to recover this, which is less than ideal!

---

### Post by Dreamsorcerer on 2011-08-18
> **ugm6hr said:**
> One more problem...
The "Cancel" option needs to actually work.
If you "enount" a folder accidentally, and then select cancel - it appears that you lose the entire folder contents.
I can't see any way to recover this, which is less than ideal!

Hmm, that is an issue. It should have copied all your files over to another folder first (named emount-temp-[random no.]). So, if that does happen you should be able to just copy the files back from that folder. I'll have to look into handling cancelling properly though.

---

### Post by ugm6hr on 2011-08-19
> **Dreamsorcerer said:**
> Hmm, that is an issue. It should have copied all your files over to another folder first (named emount-temp-[random no.]). So, if that does happen you should be able to just copy the files back from that folder. I'll have to look into handling cancelling properly though.

Apologies... I posted without looking. Yes - it does copy to a temp folder. Perhaps a comment in a troubleshooting section in Post 1 to let people know this?

But - I have an encrypted folder within the folder I accidentally encrypted. Can I just move that back to the prior location - and it will decrypt? Selecting ecrypt from the current location goes through trying to re-encrypt it again...

EDIT: Just copied back the copied encrypted folder to the original location - and it appears to be behaving normally.... Thankyou.

---

### Post by Dreamsorcerer on 2011-08-20
> **ugm6hr said:**
> But - I have an encrypted folder within the folder I accidentally encrypted. Can I just move that back to the prior location - and it will decrypt? Selecting ecrypt from the current location goes through trying to re-encrypt it again...
If you do want to move/rename an encrypted folder, you have two options. Either edit the keyring information with gnome-encfs, run 'gnome-encfs --help' to work out how.

Or, you can just emount it again, as long as you enter the correct decryption password in the creation process, it will simply save a new keyring item and then it can decrypt the existing folder.

---

