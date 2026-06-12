---
title: "locked myself out"
date: 2005-09-09
forum: Server Platforms
---

### Post by luke.stanbra on 2005-09-09
i am a very new user to ubuntu (got a friend to install in for me) and i think i have done something a bit silly. when he was installing ubuntu for me i gave him a password to use for my account so he didn't have to keep getting me to type it in for him, with the intention of changing it when he was done. i changed it using the users and something option in the security tools menu, and i gave root the same password as well (hey, seemed like a good idea at the time). now neither my account nor the root account respond to the new password or the old one and i dont what to do :(

i am using xp atm btw (is a dual-booter), so please i beg you, save me ;)

thanks,
luke

PS thought you ought to know, am running hoary amd64 version using gnome, hope that info helps somehow :s
PPS one more thing, tried rebooting into recovery mode, it just asks for a root password (which i dont know/cant guess) or continues to the login screen (which i cant get past)

---

### Post by macgyver2 on 2005-09-09
[https://wiki.ubuntu.com/LivecdRecovery](https://wiki.ubuntu.com/LivecdRecovery)

Hope this helps...if you have any more questions, just ask!

---

### Post by luke.stanbra on 2005-09-09
um, i have no idea what the partition with root on is called, but the only thing in /dev that looked like it could be it was /dev/hda, and when i mounted that it said that it was read only, then when i tried the chroot /mnt thing it gave an error message along the lines of "chroot: cannot find /bin/bash" so i dont know what to do now, any help would be appreciated :)

i did notice that the live cd couldn't find the hardware clock when it booted, thought id mention it jic.

---

### Post by macgyver2 on 2005-09-09
/dev/hda is your overall drive.  There should also be other hda* devices in /dev...hda1, hda2, hda3, and so on, depending on the number of partitions you have.  If you type
```
sudo fdisk -l /dev/hda
```
It will list your drive's partition table...from that you'll be able to tell which partition(s) is/are your Linux partition(s).  If you have more than one try mounting the first Linux partition.  It should default to read-write.  When you find the right partition, you shouldn't get that /bin/bash error either.

Let us know if that helps.

---

### Post by luke.stanbra on 2005-09-09
my god that must be one of the most futile hour and a halves i ahve ever spent...

anyway, what you said to do worked kinda, most of the problem was in that i didn't realise sda also meant hard drive  ](*,) anyhoo, i finally get in and lo and behold the GUI tells me that i cant log in as root from there

so i go to the text imput thing that you get when you press ctrl-alt-1. can login as root fine from there..only trouble is got no idea how to either find out, or change the password for my other account, so i spent an hour and half trying to dig my way through info and man files (not assisted by the fact that i cant make anything not a specific man file not scroll off the top of the screen, including ls and man -k searches, and believe me i spent a looong time looking for an optiong that would just let me see all of the frigging output ARGH!!!  ](*,) )

ahem, oh yes, well, i managed to find userdel, useradd and usermod so played around deleting and remaking the account, but the password option with it seems to set the imput for that option as not the password but the output from crypt(3)...which has no info file, yippeee.......so you can make i account so long as i can encrypt/decrypt passwords in my head, which is terribly useful.

i realise im rambling now, but thats cause its 3:20am and i haven't been able to make this work for the last 4 hours or so.....god, what a mess

if anyones got any cluse wth is going on i beg you, please help  :???:  :-x

---

### Post by codejunkie on 2005-09-09
[QUOTE=luke.stanbra]my god that must be one of the most futile hour and a halves i ahve ever spent...

anyway, what you said to do worked kinda, most of the problem was in that i didn't realise sda also meant hard drive  ](*,) anyhoo, i finally get in and lo and behold the GUI tells me that i cant log in as root from there

so i go to the text imput thing that you get when you press ctrl-alt-1. can login as root fine from there..only trouble is got no idea how to either find out, or change the password for my other account, so i spent an hour and half trying to dig my way through info and man files (not assisted by the fact that i cant make anything not a specific man file not scroll off the top of the screen, including ls and man -k searches, and believe me i spent a looong time looking for an optiong that would just let me see all of the frigging output ARGH!!!  ](*,) )

ahem, oh yes, well, i managed to find userdel, useradd and usermod so played around deleting and remaking the account, but the password option with it seems to set the imput for that option as not the password but the output from crypt(3)...which has no info file, yippeee.......so you can make i account so long as i can encrypt/decrypt passwords in my head, which is terribly useful.

i realise im rambling now, but thats cause its 3:20am and i haven't been able to make this work for the last 4 hours or so.....god, what a mess

if anyones got any cluse wth is going on i beg you, please help  :???:  :-x[/QUOTE]
i believe if your can login as root you can change your user account password with 
```
passwd yourusername
``` and the reason you cant login as root through 
gdm it's for security but you can change that by going to System/Administration/Login Screen Setup and under the security tab check the box that says allow root to login through gdm hope this helps.

---

### Post by luke.stanbra on 2005-09-09
squee! it worked!!!!! you have no idea how much i love you right now!

*squees some more*

ahem....calm has returned....anyhoo im off to try and do whatever the hell it was i was trying to do before all this mess started

thanks once again everyone who helped  :)  :grin:

EDIT: although it probs dont belong in this bit of the forum, i thought id ost this here jic it had something to do with my previous problem, when i try to run things that require me to enter my password, no matter what i enter into the box, the return an error of "Failed to run XXX: Child terminated with 1 status"....these things include the synaptic doodah and most things in the system menu etc so i am a little concerned

---

### Post by codejunkie on 2005-09-09
[QUOTE=luke.stanbra]squee! it worked!!!!! you have no idea how much i love you right now!

*squees some more*

ahem....calm has returned....anyhoo im off to try and do whatever the hell it was i was trying to do before all this mess started

thanks once again everyone who helped  :)  :grin:

EDIT: although it probs dont belong in this bit of the forum, i thought id ost this here jic it had something to do with my previous problem, when i try to run things that require me to enter my password, no matter what i enter into the box, the return an error of "Failed to run XXX: Child terminated with 1 status"....these things include the synaptic doodah and most things in the system menu etc so i am a little concerned[/QUOTE]

if the apps are terminating after you enter your password it could be because your name is not in the sudoers file. test this by opening a terminal and typing
```
sudo su
```that should log you in as root you will see something like this in the terminal 
```
root@ubuntu:/home/username#
``` if you get an error when trying that there's the problem. what you have to do is make sure you have the root account enabled you can do that by rebooting your computer and at the grub menu choose recovery mode this will give you temp root access to the computer here you can enable the root account with ```
passwd root
``` enter a new password for the root user and reboot your computer with ```
init 6
```login like you normally do and open a terminal and type ```
su
``` when it ask's for the password use the one you just set for the root user now you can add your name to the sudoers file with this command 
```

export EDITOR=gedit && visudo

```

and add this to the bottm of the file 
yourusername ALL=(ALL) ALL
save and exit gedit and test your apps again hope this helps.

---

### Post by luke.stanbra on 2005-09-10
it worked :) thankyou very much....you people are awesome :D

---

