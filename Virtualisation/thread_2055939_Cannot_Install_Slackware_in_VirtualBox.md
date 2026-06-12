---
title: "Cannot Install Slackware in VirtualBox"
date: 2012-09-10
forum: Virtualisation
---

### Post by PremiumG on 2012-09-10
Cannot create the machine folder Slackware 64-13.37 in the parent folder /home/brian/VirtualBox VMs.

Please check that the parent really exists and that you have permissions to create the machine folder.


...

This is the pop-up that appears when I try the first step in installing Slackware on VB. I had to go into terminal to make the directory using sudo... It seems that i'm not allowed to edit any files in the file manager, but only if I go to terminal and use "sudo" before everything. Also, how do I delete directories in terminal, since I now have "VirtualBox" and "VMs" in my efforts to create "VirtualBox VMs"

Also, is there a way where I can permanently edit folders without having to go to the terminal and use "sudo" before everything?

---

### Post by muteXe on 2012-09-10
```

sudo -i

```
will give you root rights until that terminal session is closed.

Sounds like your read/write settings might be screwed on your home folder?

navigate to the home folder (/home not /home/brian) and do a 
```

ls -l

```

edit:
have a quick look here too:
[http://ubuntuforums.org/showthread.php?t=1872706](http://ubuntuforums.org/showthread.php?t=1872706)

---

### Post by PremiumG on 2012-09-10
This happened


[B]brian@brzan:/home$ ls -l
total 4
drwxr-xr-x 32 1016 1016 4096 Sep 10 10:18 brian
brian@brzan:/home$[/B] 

I am not really sure what that means.

As for that link, even though I input my username correctly, brian.brzan, it couldnt recognize it.

---

### Post by d3v1150m471c on 2012-09-10
> 
Also, is there a way where I can permanently edit folders without having to go to the terminal and use "sudo" before everything?


```

man chown
man chmod

```

---

### Post by PremiumG on 2012-09-10
Thank you for those commands :D

Now how about this issue with VB?

---

### Post by marinara on 2012-09-10
are you logged in as brian?

---

### Post by PremiumG on 2012-09-10
> **marinara said:**
> are you logged in as brian?

That is the only way to be on my desktop. I boot, login on the welcome screen, and that IS what you mean, right?

I am starting to suspect that every time I get to my desktop, I must "sudo -i" in the terminal to allow me to run any program. I do not like this at all, and there must be a way to never have to give  permission to anything. Im not just talking about "sudo -i" until the terminal is closed, I mean **permanently**.

---

### Post by muteXe on 2012-09-11
did you actually read my link? Those commands were in there!

And you should NOT need to be root. You should try and get it working how  it should, rather than trying to give yourself root privs all the time.

---

### Post by nothingspecial on 2012-09-11
*Thread moved to **Virtualization**.*

---

### Post by coffeecat on 2012-09-11
> **PremiumG said:**
> I do not like this at all, and there must be a way to never have to give  permission to anything. Im not just talking about "sudo -i" until the terminal is closed, I mean **permanently**.

If we go back to your original post:

> **PremiumG said:**
> I had to go into terminal to make the directory using sudo...

By using sudo when creating a directory in your home folder, you created a root owned directory - in fact, two. **Nothing** should be owned by root in your home. If you were unable to create a folder in the file manager in your home then, as muteXe indicated earlier, something is wrong somewhere inside your home. You need to find out what that is and fix it before even thinking of installing something in VirtualBox.

Having said all that, it's not clear from your OP whether the /home/brian/VirtualBox VMs folder was not there, or whether it was owned by root. You made a mistake when you tried to create /home/brian/VirtualBox VMs in the terminal by not escaping the space character which is why you ended up with the two folders /home/brian/VirtualBox and /home/brian/VMs. Post the output of this so we can see where you are now:

```
 ls -l /home/brian
```

> **muteXe said:**
> 
And you should NOT need to be root. You should try and get it working how  it should, rather than trying to give yourself root privs all the time.

+1

**EDIT:** the output you posted in post #3 tells us that the permissions in your home folder - /home/brian - are correct and that you should be able to create sub-folders with the file manager.

Going back to your OP:

> Cannot create the machine folder Slackware 64-13.37 in the parent folder /home/brian/VirtualBox VMs.

Please check that the parent really exists and that you have permissions to create the machine folder.

I'm beginning to suspect that the sole problem was that /home/brian/VirtualBox VMs did not exist yet - one of the two possible conditions the error tells you - and that you focussed on the second possibility.

---

### Post by PremiumG on 2012-09-11
Here is what I got:


```
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Desktop
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Documents
drwxrwxr-x 3 brian brian     4096 Sep 10 21:06 Downloads
drwxrwx--- 6 brian brian     4096 Sep 11 12:44 Dropbox
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Music
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Pictures
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Public
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Templates
-rwxrwxr-x 1 brian brian 36336614 Dec 16  2010 veetle-0.9.17-linux-install.sh
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Videos
drwxr-xr-x 2 root  root      4096 Sep 10 10:17 VirtualBox
drwxr-xr-x 2 root  root      4096 Sep 10 10:18 VirtualBox VMs
drwxr-xr-x 2 root  root      4096 Sep 10 10:17 VMs
```

Oh, and I did read your link muteXe, but I am VERY new to linux and that kind of stuff I do not understand how to use correctly.

---

### Post by coffeecat on 2012-09-11
First thing - I've added code tags around your terminal output. It makes it easier to read and it preserves formatting which is lost in bare text in posts. You might find this useful:

[http://ubuntuforums.org/showpost.php?p=12231647&postcount=8](http://ubuntuforums.org/showpost.php?p=12231647&postcount=8)

Second thing:

> **PremiumG said:**
> I am VERY new to linux

I mean this kindly, but installing and maintaining Slackware is far from easy for newcomers to Linux. It's not a beginners' distro. Installing it in a virtual machine adds another layer of complexity. Your unfamiliarity with a Unix-like environment is causing you to make mistakes (no criticism intended - we all had to learn this), which just makes things more difficult for you. I'm not trying to put you off - just warning you that you are jumping into the deep end before you've learnt to swim fluently. But good luck anyway.

To your problem:

> **PremiumG said:**
> ```
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Desktop
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Documents
drwxrwxr-x 3 brian brian     4096 Sep 10 21:06 Downloads
drwxrwx--- 6 brian brian     4096 Sep 11 12:44 Dropbox
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Music
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Pictures
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Public
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Templates
-rwxrwxr-x 1 brian brian 36336614 Dec 16  2010 veetle-0.9.17-linux-install.sh
drwxrwxr-x 2 brian brian     4096 Sep  6 13:46 Videos
drwxr-xr-x 2 root  root      4096 Sep 10 10:17 VirtualBox
drwxr-xr-x 2 root  root      4096 Sep 10 10:18 VirtualBox VMs
drwxr-xr-x 2 root  root      4096 Sep 10 10:17 VMs
```

The reason you have separate VirtualBox and VMs folders is that you would have run something like "sudo mkdir VirtualBox Vms" without escaping the space. What was needed was "sudo mkdir VirtualBox\ VMs", but that's not needed now and, as I said, using sudo with mkdir in your home folder is a recipe for trouble - you make root owned folders.

Open a terminal and delete the two unnecessary folders with this:

```
sudo rmdir /home/brian/VirtualBox
sudo rmdir /home/brian/VMs
```

Now you need to change ownership of the Virtualbox Vms folder with:

```
sudo chown brian:brian /home/brian/Virtualbox\ Vms
```

Yes, you do need sudo with those commands because you are working on root-owned folders. 

Now you should be able to do whatever it was you were referring to at the beginning of your first post when you got the "cannot create..." message.

---

### Post by Habitual on 2012-09-11
> **PremiumG said:**
> Cannot create the machine folder Slackware 64-13.37...

Try naming it something else, say without the - and . ?

---

### Post by PremiumG on 2012-09-11
Thank you for the assistance and advice. I know Slackware isn't easy, but I require minimalism. Even Lubuntu comes with too much unnecessary programs and packages. I want to get my hands dirty and learn how it works so I can create my own, minimalistic distro, for personal use of course.

As for my directory issue, it is solved! Thank you for the help. Since I am new, I will utilize the internets to hold my hand through learning Slackware as well. VirtualBox will be easier than just installing it on a new partition.

---

### Post by muteXe on 2012-09-12
> **PremiumG said:**
> Thank you for the assistance and advice. I know Slackware isn't easy, but I require minimalism. Even Lubuntu comes with too much unnecessary programs and packages. I want to get my hands dirty and learn how it works so I can create my own, minimalistic distro, for personal use of course.

Well, you're certainly doing the right thing by experimenting with it all in a VM. Slackware is my main distro nowadays, so I guess I'll see you on the forums over there :)

---

### Post by Bas Roufs on 2012-09-19
> **coffeecat said:**
> 

Now you need to change ownership of the Virtualbox Vms folder with:

```
sudo chown brian:brian /home/brian/Virtualbox\ Vms
```

Yes, you do need sudo with those commands because you are working on root-owned folders. 

Now you should be able to do whatever it was you were referring to at the beginning of your first post when you got the "cannot create..." message.

When trying to install a Win7 guest OS, I had the same permission problem along with the same "Cannot create..." message. The message cited above clarified for me how to solve the problem. Thanks! 
I managed to solve the problem as follows:
I opened a terminal and gave in the command "sudo -i". 
As root, I gave in the command "mc" with a view to starting "Midnight Commander". From there, I selected the file "/home/bas/VirtualBox VMs".
Then I used the menu option FILE > chown. Both "owner" and "group" I changed from "root" to "bas". After this, I started again VirtualBox. From that moment onwards, everything worked flawlessly.
Respectfully yours,
Bas Roufs.

---

