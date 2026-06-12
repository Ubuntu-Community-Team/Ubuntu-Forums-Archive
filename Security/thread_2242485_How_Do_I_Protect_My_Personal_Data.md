---
title: "How Do I Protect My Personal Data?"
date: 2014-09-02
forum: Security
---

### Post by Quarkrad on 2014-09-02
My requirement is to protect personal data on my laptop should it get physically stolen and also have that data protected on the backup memory stick.  I have installed 12.04 on a friends machine for which this is required and been testing, with little sucess so far, on my 14.04 laptop (e.g. each time I encrypt my swap space it screws up my touchpad - but that is another issue).  I thought encrypting **/home** would protect my data but have been told in another thread that **When you copy files to another drive, they are not encrypted. That is normal.**  So perhaps encryption is not my answer (I hoped using rsync to copy **/home** to the backup stick would maintain the encryption).  Assuming I keep my sensitive data in **Documents** what is the best methodology to pertect this data on the laptop and memory stick?

---

### Post by Quarkrad on 2014-09-02
I have read some info on this forum (but not all!) and it looks like protecting a memory stick is not that secure (unless perhaps if you buy an expensive dedicated device).  Certainly, my first requirement is not to be able to use the memory stick on other machines, purely a backup for the dedicated ubuntu laptop - not sure if this is relevant.

---

### Post by markodd on 2014-09-02
You should encrypt your whole partition (you can do it easily when installing ubuntu) in case your laptop gets stolen.

About the USB flashdrive, the only way for you to be safe is to encrypt it as well.

---

### Post by Quarkrad on 2014-09-02
Can I use tools within Ubuntu to encrypt the whole partition and flashdrive or do I have to use 3rd party tools like Truecrypt?

---

### Post by fidelis2 on 2014-09-02
In case it sufficient for you to "just" have encrypted container partitions (or files), where all the sensitive files are being stored (i.e. not an entirely encrypted boot system), you could use the Kernel-built-in LUKS system. Only two GUI tools from Ubuntu's Software Center are necessary to achieve this.

1) With "gparted" you can create an empty partition on your desired drive or memory stick. This partition will be used as encrypted volume. With external drives I usually use the entire space for one (encrypted) partition. For just an additional (encrypted) partition on the main drive, I shrinked the main one and added a new partition to the end.
2) With "gnome-disks" select that new partition, hit the gear icon, select the "Format" menu entry and go for the "Encrypted, compatible with Linux (LUKS + EXT4)" option. A few moments later you enter your new pass-phrase and the container's name, and that's it.

Now to use that encrypted container in the future, just click on this LUKS partition (it has a yellow lock symbol in the drive icon) in your file explorer, like Thunar in my case. Then for each new login session you're asked once to enter your pass-phrase, and then you can use it like any other drive; i.e. also create a link to it inside your home folder, for example.

This is a nice and a fast and OpenSource equivalent to, for example, Truecrypt containers. Of course the same safety measures apply then, in contrast to an entirely encrypted system.
For example when you directly edit files in a LUKS container without encrypted main system, you need to ensure that the editor's temp files stay in that container, which is easy for many programs like Openoffice, and so on. Or use the encrypted container as an archive for sensitive files.


P.S. When you use an ecrypted boot system, also LUKS is being used, but with different steps than the ones I outlined and use for myself.

---

### Post by Quarkrad on 2014-09-02
This sounds just what I'm looking for - can you help me in setting this up?  I can set up the partitions but what software or commands do I need to set everything up?  Also, is there any documentation on how an end user (me(!)) uses this once it is all set up?

---

### Post by fidelis2 on 2014-09-02
> **Quarkrad said:**
> This sounds just what I'm looking for - can you help me in setting this up?  I can set up the partitions but what software or commands do I need to set everything up?  Also, is there any documentation on how an end user (me(!)) uses this once it is all set up?
You just need to install in Ubuntu's Software-Center the package "gnome-disk-utilities", which contains the GUI tool "gnome-disks": You can either start the latter from Xubuntu's Configuration Center (its symbol is a drive with a tool), or via terminal.

With the "[gnome-disks]("https://en.wikipedia.org/wiki/GNOME_Disks")" program you should be able to do what I tried to outline in my previous posting, i.e. :
- Select your new free partition which you want to use as encrypted container;
- Then in the icon bar below the partition(s) which is for partitions, click the symbol with the two gears (i.e. not the icon bar on the top of the window which is for an entire drive, and which has an icon with one gear meaning operations for the entire drive);
- In the newly opened menu click "Format" (i.e. format partition) and now the format window opens;
- In the format window go to the 3rd line "Type" and select "Encrypted, compatible with Linux Systems (LUKS + EXT4)";
- Give the partition a logical name (just for your memory) and then click the Format button. At some time the tool would ask you for a new password to open the encrypted volume later.

Now you should have an encrypted container, aka the LUKS partition. You can then quit the gnome-disks program and in your file manager (Thunar in my case), you should see the encrypted drive symbol of this new encrypted container in your left drive/partitions list. And every time you click it for the first time during a new login session, you would have to enter the LUKS password once in order to open (aka unlock) it for your  session, and then you can use the opened encrypted container like a normal Linux partition. It's under "/media/YOURNAME/logical_name/".


P.S. In case your first try to write and read from this opened partition results in a file permission error, you would have to give Read-Wright rights once to your normal user for that opened encrypted partition, either via your file manager or via the "sudo chown" command.

P.P.S. With the same "gnome-disks" program you can later also change your encrypted partition's password, in case it would be needed.

P.P.P.S. There's a lot of documentation about LUKS, but this simple combination guide of "gnome-disks" with LUKS in a few steps I just found for my local language.

P.P.P.P.S. Now I see you use Ubuntu 13? Maybe, but I don't remember, the program has been called back then "palimpsest".

---

### Post by fidelis2 on 2014-09-02
> **Quarkrad said:**
> I thought encrypting **/home** would protect my data but have been told in another thread that **When you copy files to another drive, they are not encrypted. That is normal.**  So perhaps encryption is not my answer (I hoped using rsync to copy **/home** to the backup stick would maintain the encryption).
I too use RSYNC to backup all the important files, including an encrypted container (partition) on my main machine to some external drive (like your mentioned USB memory stick). But since the LUKS encryption is "transparent" for us normal users (i.e. happens on the fly), I need to have that external drive of mine encrypted, too.

So, before RSYNC can start, I just unlock/open the encrypted source partition (on the main drive) and then the encrypted destination partition (on the USB drive), and then everything i.e. every disk accessing tool works like with normal partitions.

If you're new to encryption, you just have to understand this transparent on-the-fly encryption once, and you'll love it forever.

---

### Post by Quarkrad on 2014-09-02
Thanks - this is great. I'm just building a clean 12.04 (ubuntu) machine to duplicate my friends.  It is possible to automount the encripted partitions (HD and stick) when the laptop first boots?

---

### Post by fidelis2 on 2014-09-03
> **Quarkrad said:**
> It is possible to automount the encripted partitions (HD and stick) when the laptop first boots?
I would assume it is, but I haven't figured out yet how to achieve it.

Somebody knows this?

---

### Post by Quarkrad on 2014-09-03
Im running 12.04 now and having typed **sudo apt-get install gnome-disk-utility** I'm told it is already at the newest version - but where is it?  When you say "...Select your new free partition which you want to use as encrypted container;
- Then in the icon bar below the partition......"  what do I launch?  Sorry for this but it is not obvious in the menus I have what to launch.

---

### Post by Quarkrad on 2014-09-03
I think I may have done this - see attached.  I will continue and come back if I get into any trouble.

---

### Post by Quarkrad on 2014-09-03
Spoke too soon.  During the setup (re the Passphrase) I opted for **Remeber forever**.  Is it possible to change this to **Forget password immediately** and/or **Remember password until you logout **so I can see the 'real world' difference?

---

### Post by fidelis2 on 2014-09-04
Well, your screenshot looks very promising. Congratulations, it looks like you did it!
Now concerning this:
> **Quarkrad said:**
> Spoke too soon.  During the setup (re the Passphrase) I opted for **Remeber forever**.  Is it possible to change this to **Forget password immediately** and/or **Remember password until you logout **so I can see the 'real world' difference?
Yes; in my Xubuntu which should be the same as Ubuntu in our case, it's the keyring manager which stores these passwords "forever": the program's name is "seahorse" and you can either start it via terminal or via the GUI way (don't remember the Ubuntu-Unity way; in Xubuntu there's the XFCE configuration center and there's the "seahorse" as an icon with two keys. Btw, in Xubuntu I had to add "seahorse" manually from the software center, but you're using normal Ubuntu so I think it's already there.)

Anyway, in the keyring manager (seahorse) you can browse through all your entered keys and delete those for your encrypted containers, for example. That should do the trick, I hope. It does here for me.

---

