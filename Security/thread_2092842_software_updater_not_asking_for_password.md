---
title: "software updater not asking for password"
date: 2012-12-09
forum: Security
---

### Post by flipflip47 on 2012-12-09
Hi everyone,

Hopefully someone can help me with this.  I noticed recently that the software updater is not asking for a password.   It does not ask for a password when i click on the "install now" button, nor does it ask for a password when I click on the settings button.   The settings button brings up the software sources window.   I, for one, see this as a security risk especially the settings.   I am aware that the install now button will ask for a password for new updates but I would like to be able to put a password for all updates.  Is there any way of making the software updater ask for a password for both the "settings" button and the "install now" button everytime I click them.  I am running Ubuntu 12.10 32 bit. Thank you for any advise you may share.  ):P

---

### Post by johnycsf on 2012-12-09
That is an interesting point. 
I think that they eliminated it because a lot of people found it annoying having to put a password when updating it with GUI. Specially since updates don't harm your system in any way as opposed to installing or uninstalling software.
I really don't think there's a way to add password to it because your account is already password protected but if you must insist in typing a password just update your system in the terminal!

---

### Post by flipflip47 on 2012-12-09
> **johnycsf said:**
> That is an interesting point. 
I think that they eliminated it because a lot of people found it annoying having to put a password when updating it with GUI. Specially since updates don't harm your system in any way as opposed to installing or uninstalling software.
I really don't think there's a way to add password to it because your account is already password protected but if you must insist in typing a password just update your system in the terminal!

johny, although I appreciate your input, it is not the answer I was looking.  I am aware that I can use the terminal but it does not get rid of the issue I am having.  As you know, the updater shows up when you first log into the system.  Let say I walk away from the pc and a family member starts to use my pc.  They accidently update a piece of software like firefox, which i do not want to update due to it breaking some add ons.  Well, that situation could be avoided by the password prompt.  I know that this scenario is highly unlikely, but you get the idea.

---

### Post by Bucky Ball on 2012-12-09
You could use the lock screen function in Screensaver I think it is. You need the password to unlock the screen and therefore no-one could even use the computer while you are away from it, let alone update Firefox or anything else ...

There may be a way of achieving what you are after but it wouldn't be regulation and may require jumping through some hoops ...

---

### Post by thnewguy on 2012-12-09
Bringing up the settings in the update manager doesn't request a password, but _changing_ the setting does require a password. Anyone can see which repositories you are using, but it takes admin access to actually make any changes.

As for applying the updates, I think that is a function of the "adm" group. If the user is not a member of this group then they should not be able to apply the updates without providing a password.

Basically, the solution to your problem is:
A) Don't leave your computer logged into an admin account and then walk away without locking it. This should be pretty obvious.
B) Don't give people admin accounts unless you want them to be able to perform admin functions, such as updating packages.

---

### Post by flipflip47 on 2012-12-09
Thanks again for the responses.  I do see your points of locking the screen and admin priveleges.  I was not aware that it would ask for a password before making changes to the setting via updater, so at least that helps with one issue.  I'll have to test that for myself to be sure.  Now for the other issue, is there a way to have the updater ask for password for every update install.  I know that I can lock my screen and not leave my pc unattended.  That was just an example I used to better understand what I mean.  Not that I am having issue with or worried about that.  I just want a way to have updater ask me for a password for each and every update and to access the settings if possible.

---

### Post by flipflip47 on 2012-12-09
I just tested the settings portion and it does indeed ask for a password before making any changes.  That is great news as that solves one issue.  Thanks again :D

---

### Post by Cheesemill on 2012-12-09
The way that package and update management is handled was changed in 11.10.

You now don't get prompted for a password to update any packages that are ***already*** installed on your system, you only get asked for your password to install ***new*** packages (like a new kernel).

The reasoning behind this is that you are expected to always be running the most up to date version of a package available in the repositories, this is more likely to happen if a user doesn't need to use their password. There is no real security risk as no new packages can be installed, only updates which are always bug fixes and security patches.

The may be some way to change this behaviour by editing the correct policykit action file but I can't look now as I don't have a Ubuntu Desktop machine handy at the moment (but it's probably somewhere in /usr/share/polkit-1/actions/).


Edit - The answer can be found [here]("http://askubuntu.com/questions/86773/update-manager-doesnt-ask-for-a-password").

---

### Post by flipflip47 on 2012-12-09
Thank you cheesemill for giving me a direction to start.  I looked at it, but since I am fairly new to Linux, less than a year using it, I dont feel quite comfortable making changes there.  Probably because I have no idea which file to even start with. I'll will be getting a new machine in a few months.  Then I'll play around with, most likely break, ubuntu with no fear.:lolflag:

---

### Post by Bucky Ball on 2012-12-09
Always:

```
sudo cp /file/you/are/tweaking /file/you/are/tweaking.bak
```... then tweak to your heart's content. If it breaks something:
```

sudo cp /file/you/are/tweaking.bak /file/you/are/tweaking
```... will copy the original back to where it was and all will be the same as before you started messin'.

For instance:

```
sudo cp /usr/share/polkit-1/actions/ /usr/share/polkit-1/actions.bak/

```... will save the original as /usr/share/polkit-1/actions.bak/ ;)

---

### Post by flipflip47 on 2012-12-09
Oh my goodness, you are a genius Bucky!  Thank you for that info.:D

---

### Post by Bucky Ball on 2012-12-09
Not sure about genius but no probs ... ;)

You can also use mv to move the file back. I use cp though as that keeps the original .bak in case you tweak the copy and break again. 

```
sudo mv /file/you're/tweaking.bak /file/you're/tweaking

```

Handy cos even if you break it so bad you can't get back in the system you can still boot from the liveCD and copy the original file back, reboot and all should be as it was.

---

### Post by flipflip47 on 2012-12-10
Bucky, thanks again for the assit.  Very much appreciated.  Now, if only someone could find the way to help me with issue of password for each update, I would be very happy.  It would avoid me having to mess something up. I'll keep looking around to see if google has an answer to my question.  For now, I'll leave it unsolved. Someone might have the answer, just a matter of waiting. ):P

---

### Post by Cheesemill on 2012-12-10
I linked to the answer in my post earlier, but here's the concise how-to:

Create the new required file and open it for editing by hitting ALT+F2 and entering the following command:
```
gksudo gedit /var/lib/polkit-1/localauthority/50-local.d/require-password-to-update.pkla
```
Copy and paste the following text into the file:
```
[Require password to upgrade already installed software]
Identity=unix-group:admin
Action=org.debian.apt.upgrade-packages
ResultActive=auth_admin

```
Save the file and quit the text editor and you're all done.

Thanks for the backup commands BuckyBall (I always do this as well) but in this case you don't even need them, all you are doing is creating a new file rather than editing an existing configuration. If it doesn't work as expected you can simply delete the file you've just created.

---

### Post by flipflip47 on 2012-12-10
> **Cheesemill said:**
> I linked to the answer in my post earlier, but here's the concise how-to:

Create the new required file and open it for editing by hitting ALT+F2 and entering the following command:
```
gksudo gedit /var/lib/polkit-1/localauthority/50-local.d/require-password-to-update.pkla
```Copy and paste the following text into the file:
```
[Require password to upgrade already installed software]
Identity=unix-group:admin
Action=org.debian.apt.upgrade-packages
ResultActive=auth_admin

```Save the file and quit the text editor and you're all done.

Thanks for the backup commands BuckyBall (I always do this as well) but in this case you don't even need them, all you are doing is creating a new file rather than editing an existing configuration. If it doesn't work as expected you can simply delete the file you've just created.

You sure did, sorry I missed that.  Thank you as well for the information.  I found that just adding auth_admin to the original file did the trick.  There was no need for me to create a new file.  I want to thank you both for your assistance on the issue.  I learned quite a bit just on this alone.  Thanks again, I will mark this thread solved.

---

### Post by Cheesemill on 2012-12-10
Just be aware that your solution may not be permanent.

When there is an update to the package that the file /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla belongs to the file may be overwritten with a new version that doesn't contain your changes.

This is the reasoning behind creating a separate override file instead, it is guaranteed to survive package updates.

---

### Post by flipflip47 on 2012-12-10
I had thought of that, just waiting to see if it does overwrite the file.  If it doesn't, then i'll keep it as is.  If it does, then I will create the override file. Thank you for the information.

---

### Post by mc4man on 2012-12-10
> **Cheesemill said:**
> 
Identity=unix-group:admin
Action=org.debian.apt.upgrade-packages
ResultActive=auth_admin

```

In 12.10 & onward one would want to use sudo instead of admin group as there no longer is an admin group (in fresh installs

Identity=unix-group:sudo

---

