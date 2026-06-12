---
title: "Secure Empty Trash bin"
date: 2010-09-09
forum: Security
---

### Post by twzg on 2010-09-09
Hi. Is there a way to securely empty the trash bin without the need to type some shred command into consoles. My intentions is to be able to securely delete files when the 'Empty Trash' is used so to save the trouble of going to a console and doing some commands using shred.

---

### Post by steve161 on 2010-09-09
Maybe not exactly what you are looking for, but the cleaner program "bleachbit" will empty your trash and has an option to use a one pass zero overwrite. You could also install wipe and add it to your context menu  using nautilus action configuration.

---

### Post by twzg on 2010-09-09
Thanks. Looking into bleachbit. But I think it would be good if ubuntu's trash could have some settings to switch into secure deletion mode if the user wants.

---

### Post by steve161 on 2010-09-09
I don't think it is high on their list since there is inbuilt shred commands.  If you want to add wipe to the context menu, it is very simple, and you don't need to send the file to the trash.  Just right click on it and select wipe from the menu.  However, there is a danger of having this in your context menu since there is no turning back once clicked

---

### Post by BkkBonanza on 2010-09-10
This is fairly easy to setup as a  Nautilus Action.
First install the secure-delete package in Synaptic.
Then select the System, Prefs, Nautilus Action Config menu item.
This tools lets you add/edit actions that are attached to Nautilus menus including the right click context menu.

Click New Action.
Check "Display item in Context Menu".
Enter "Secure Empty Trash" as Context Label.
Enter whatever tool tip you like and select an icon you like.

Now click on the Command tab to set the action.
For profile enter Main. 
For Command Path enter the path to a script you will make, eg.
/usr/local/bin/srm-trash
For Parameter enter, %m
Click Conditions tab and choose "Both"
Lastly click on Advanced Conditions tab and click + to add a new item called "trash", select it after.

Repeat this all for another Action called "Secure Delete".
with the command path, srm and parameters "-rlz %M" (no quotes).
On Advanced Conditions select Local Files.
Now click Save to save your new actions.

Finally, paste this small script into a file /usr/local/bin/srm-trash 
and **sudo chmod 755 /usr/local/bin/srm-trash**

> #!/bin/bash
if [ $# -eq 0 ]; then
  srm -lrz ~/.local/share/Trash/*/*
else
  for f in "$@"; 
  do
    srm -lrz ~/.local/share/Trash/files/"$f"
    srm -lrz ~/.local/share/Trash/info/"$f".trashinfo
  done
fi

Hopefully I didn't forget something. I've been using this for at least a year and it's been working well.

---

### Post by cariboo on 2010-09-10
If you are worried about files in trash, why use it at all, you can set the delete options in Nautilus->Edit->Preferences-> Behaviour.

---

### Post by light-vessel on 2012-02-20
I have problems emptying my rubbish bin. Nautilus freezes and I have to kill it. I have tried various things:

sudo rm -Rfv ~/.local/share/Trash/*

This deleted a load of files, but there's still a lot that it didn't delete.

I then tried the nautilus-actions script, but it doesn't work for me. When I looked at it, there were two problems. Firstly, I don't seem to have a command srm. I only have either rm for regular file removal or shred. Secondly, the parameter %m looks wrong. According to the Nautilus-Actions Configuration Tool, %m means MIME type, whereas I would expect the parameter needed to be file name, which is %d or %D. However, none of these things empty my rubbish bin.

I tried changing srm to rm in the script and I also tried playing with the parameter, but with no luck.

Any advice on command line methods or nautilus-actions would be greatly appreciated

I'm currently using Ubuntu 11.04

---

