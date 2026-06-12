---
title: "Installing to multi partitions / boot manager."
date: 2012-05-12
forum: Server Platforms
---

### Post by rjmorawski on 2012-05-12
I have done some searches and have found answers pertaining to the dual boot options of running windows / ubuntu on the same box. 
 
What I am looking for is a bit different. I would like to create 4 primary partitions on one drive using something like "Boot-US" which allows only one partition to be seen at a time and the other three are hidden from the active partition. 
 
I would like to install ubuntu on each primary partition as follows:
 
1. ubunto and a standard AMP stack.
2. ubuntu and everything needed for a Wordpress server.
3. ubuntu and everything needed for a Joomla server.
4. ubuntu and everything needed for a Drupal server.
 
Each time the server starts, a boot manager like GAG is then used to choose which partition to start.
 
Does anyone have any suggestions on how to configure this?
 
Thanks!
-RM

---

### Post by darkod on 2012-05-12
I know it's not an answer to your question, but do you have any reason you want the partitions literary hidden?

Unless you make a manual entry in fstab, since you will be using only linux OSs, to the best of my knowledge it ignores the other partitions the same as if they don't exist. It will just boot the OS selected and that's it.

---

### Post by rjmorawski on 2012-05-14
Thanks Darko. Actually you did help. I am new to ubuntu and while I still remeber the days of TRS-80's and MS-DOS, I've spent too many years "sheeping" along with standard default installations of OS's.
 
I've got to teach myself all about the ubuntu partitioning system and mount points etc. I can tell it is going to be possible to do, but I just don't know the details on how... yet.
 
In the end I do want to have 4 independant sets of ubuntu available to boot as described before. Lamp, Wordpress, Joomla, and Drupal.
 
So if anyone can point me to tutorials, examples, etc on grub and setting mount points and such....
 
thanks!
-RM

---

### Post by oldfred on 2012-05-14
I do not know any of the specific apps or groups of apps you want.

With MBR you can only have 4 primary partitions, you may want to have more and Ubuntu boots just as well from logical partitions in an extended partition. Only one primary can be an extended.

If drive is only going to be Linux you can use the newer gpt partitioning and all (up to 128 ) partitions are primary. But you have to have a bios_grub partition for grub to install correctly.

Which every install you install last will be the one with grub2's boot loader in the MBR. But you can reset easily if you want. Grub2 has an os-prober that will add all your installs to the grub menu.

Not sure how much additional space you may need for the configurations you want but for normal desktops I suggest 25GB for / (root) including /home and having all user data from /home in a separate data partition that you can mount in all the installs. Then /home only has the specific user configurations and is tiny ( about 250KB).

Plan your partitions and set those up first. Then install and get first Ubuntu working, then you should be able to easily install the rest. In all cases you use manual install and choose which partition to install to. Just remember which is which as I have many partitions and have installed to the wrong one (fortunately empty). 

Installer differences are not great between versions. Manual install is now Something Else.
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by SeijiSensei on 2012-05-15
> **rjmorawski said:**
> I would like to install ubuntu on each primary partition as follows:
 
1. ubunto and a standard AMP stack.
2. ubuntu and everything needed for a Wordpress server.
3. ubuntu and everything needed for a Joomla server.
4. ubuntu and everything needed for a Drupal server.
 
Each time the server starts, a boot manager like GAG is then used to choose which partition to start.

I'll just say this is entirely unnecessary.  You can run the server with a single Apache instance that directs requests to one or the other of these services depending on the URL entered.  Besides, how would this possibly work in production where you'd almost never reboot?

Whatever partitioning you do, I'd just use two primary partitions, one for /boot and one for swap, and create an extended partition in the rest of the drive.  You don't want to be constrained by the four-partition limit using primaries.

---

