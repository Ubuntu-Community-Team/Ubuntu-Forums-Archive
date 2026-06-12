---
title: "Ecryptfs remount after reinstallation"
date: 2011-10-23
forum: Security
---

### Post by hacor on 2011-10-23
Hello,

I wanted to post a question here about the encrypted home folder in Ubuntu. I installed a Ubuntu 10.10 system two years ago and chose to place the home folder on a (hardware) RAID 5 partition (Just the options suggested by the Ubuntu installer). Because the upgrade to 11.10 didn't work out correctly, I had to reformat my whole system again. And now I want to mount the RAID 5 partition again as my home folder, because it still contains all my data. After looking around on the Internet I found solutions like 'ecryptfs-recover-private' (which work perfectly), but I was wondering if I could just 'reuse' the same partition in my new installation without having to copy and paste everything out of the tmp directory created by 'ecryptfs-recover-private'. So can I just edit fstab or something to automatically reuse that partition? I tried already a lot but nothing seems to work.

I'm also wondering if anyone has a good link or overview on all the different passwords/passphrases used by an encrypted folder/partition? I know I used my login password somewhere, and that I got a very long key from Ubuntu which I had to note. But all this tools ask for a 'passphrase' and I'm always wondering which one it is they're asking.

Sorry for the noob question!

Thanks for your time and help!

Best regards

Hans

---

### Post by Paddy Landau on 2011-10-23
Hans, it is possible to simply mount it, but I have not found a satisfactory explanation of how it works.

When I install a new version of Ubuntu, I take a full backup of my disk, reformat, then restore the data onto the newly-encrypted disk.

Here is a summary of what I found -- but please beware that I am _not_ certain of every aspect of my documentation!

[SIZE=3]How the data is stored[/SIZE]

*fnek:* File name encryption key (to encrypt the file names).
*fekek:* File encryption key, encryption key (the encrypted encryption key to encrypt the file contents)

[FONT=Fixedsys] /home/.ecryptfs/foo/.ecryptfs/[/FONT] holds encryption information. This contains the following files:

[LIST]
[*]*[FONT=Fixedsys]     auto-mount[/FONT]:*            Empty file instructing PAM to automatically mount the ecryptfs directory.
[*]*[FONT=Fixedsys]     auto-umount[/FONT]:*            Empty file instructing PAM to automatically unmount the ecryptfs directory.
[*]*[FONT=Fixedsys]     Private.mnt[/FONT]:*            File containing the mount point in a single line, i.e. "/home/foo".
[*]*[FONT=Fixedsys]     Private.sig[/FONT]:*            The fekek and fnek signatures without the key.
[*]*[FONT=Fixedsys]     wrapped-passphrase[/FONT]:*        The required key, encrypted with the user's password.
[/LIST]
 Also:

[LIST]
[*][FONT=Fixedsys] /home/.ecryptfs/foo/.Private/[/FONT] - The encrypted home directory.
[*][FONT=Fixedsys] ~/.ecryptfs/[/FONT] - A symbolic link to [FONT=Fixedsys]/home/.ecryptfs/foo/.ecryptfs/[/FONT]
[*] [FONT=Fixedsys]~/README.txt[/FONT] - A symbolic link to [FONT=Fixedsys]/usr/share/ecryptfs-utils/ecryptfs-mount-private.txt[/FONT]
[/LIST]
 eCryptfs encrypts the contents of the files. Optionally, it also encrypts the names of the files. Ubuntu does both; so when you decrypt, you need to decrypt **both** the contents **and** the file names.

With the file [FONT=Fixedsys]wrapped-passphrase[/FONT], you can use the commands:

[LIST]
[*]     [FONT=Fixedsys]ecryptfs-wrap-passphrase[/FONT]
[*][FONT=Fixedsys]     ecryptfs-rewrap-passphrase[/FONT]
[*][FONT=Fixedsys]     ecryptfs-unwrap-passphrase[/FONT]
[/LIST]
 
When logged in, you can use the following to find your passphrase:
[FONT=Fixedsys]         ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase[/FONT]
    When it prompts for "Passphrase", enter your login password.

[SIZE=3]Mounting your home directory when logging in[/SIZE]

Ubuntu decrypts your home directory automatically when you log in. That depends on your passphrase being correctly wrapped with your login password.

I suspect that you would need to use either [FONT=Fixedsys]ecryptfs-wrap-passphrase[/FONT] to [FONT=Fixedsys]ecryptfs-rewrap-passphrase[/FONT], but I do not know how to do this. Maybe my previous comments combined with the [FONT=Fixedsys]ecryptfs-wrap-passphrase[/FONT] and [FONT=Fixedsys]ecryptfs-rewrap-passphrase[/FONT] manuals will let you find out.

Presumably you need to recreate  [FONT=Fixedsys]/home/.ecryptfs/foo/.ecryptfs/wrapped-passphrase[/FONT].

As you can see, I find it easier to just back up before installation, and restore afterwards!

---

### Post by hacor on 2011-10-24
Hi Paddy,

Thanks for the quick reply. I'll give you some more background info about what I want to do. I have a hardware RAID controller on my motherboard, splitting my 4 hard drivers into two RAID partitions: one RAID 1 (Ubuntu installation) and all the rest RAID5 (home partition). The problem is that the Ubuntu installer doesn't recognize RAID 5. I have to setup it manually afterwards.

After investigating some more in the problem I think I'm getting quite close on how to 'remount' an encrypted partition after a fresh installation. I must confess that it has become a focus on 'just wanting to know if it's possible'. And I must say, I think I'm almost there. It's a matter of creating a new user who can change the directory of the 'master' user, using usermod. Then I need to mount the partition in fstab using ecryptfs type and add the necessary keys to the keyring.

If I know more I'll post a short tutorial, because I think it can be handy to others as well.

Thanks again!

Best

Hans

---

### Post by Paddy Landau on 2011-10-24
Good luck, Hans. Sorry I can't help you on the RAID; I have never dealt with it.

A tutorial may be a good idea.

---

### Post by hacor on 2011-10-27
Paddy,

After a few days of troubles and misery, I can give a tutorial on how to reuse your encrypted home partition on Ubuntu 11.10 on a x64 RAID system. The combination of this elements seemed quite difficult for one LiveCD ;-)

**Install Ubuntu reusing your dedicated /home partition**
- Create a LiveCD and install Ubuntu 
- During the installation, choose manual partitioning and create the same layout, so choose your old encrypted home partition again as /home (remember to NOT check format)
- During the credentials page, choose the SAME name, login and password as used for the previous install. If everything went well, you will see that the option "encrypt home directory" is already selected for you.
- Continue the installation

**Now the second problem: Grub on RAID**
- If you get a GRUB install error, just choose to continue without a bootloader
- We will use boot-repair to install the GRUB bootloader

```
 sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update && sudo apt-get install -y boot-repair

```

- Install pastebinit:
[http://pkgs.org/download/pastebinit](http://pkgs.org/download/pastebinit)
- Choose the right distribution and follow the GUI instructions to install
- Install gawk:

```
sudo apt-get install gawk
```

- Time to run boot-repair:

```
boot-repair
```

- Wait some time for it to boot (if you have a hardware RIAD, you can click NO on every question)
- Choose advanced settings
- Select the right options in the GRUB tab (dedicated /boot partition? Where to install Grub?,...)
- Click Apply and wait some time

- Time to reboot

I hope this can help for some,

Regards,

hans

---

### Post by Paddy Landau on 2011-10-28
That's great, Hans, and thank you. Encryption is great, but it has terrible user documentation.

If you [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), it will help others find this thread.

---

### Post by Erulisseuiin on 2012-02-27
I must say I'm rather glad I found this :D I set up an encrypted directory in  11.10 and I was worried about the time it would take to restore if ubuntu didn't deal a fresh install properly. Thank you for alleviating my anxiety!

---

### Post by kevdog on 2012-02-27
This thread is old -- too bad he didn't post it to the Tutorials and Tips section.

---

### Post by hacor on 2012-02-28
@kevdog: Sorry, for the wrong posting location. I'll keep that in mind for the next posts!

Regards

Hacor

---

### Post by kevdog on 2012-02-28
Just a tip -- I would just summarize your findings and solutions in a new thread and post to the Tutorials Section.  Good work you have done here.

---

