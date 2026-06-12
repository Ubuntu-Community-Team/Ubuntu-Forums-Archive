---
title: "Double Login Stopped?"
date: 2015-05-17
forum: Security
---

### Post by jonathan81 on 2015-05-17
When I first installed lubuntu a few weeks ago, I had to type my login credentials in twice, presumably once to login, and another time because I used the installation option of encrypting my hard drive.

For some reason, I no longer need to add my credentials twice.

How could this have happened?

How can I check that my home folder is still encrypted?

---

### Post by sudodus on 2015-05-17
- Did you install Lubuntu with both 'Encrypted disk' and 'Encrypted home', like what is described in this link?

[http://iso.qa.ubuntu.com/qatracker/milestones/338/builds/92394/testcases/1439/results](http://iso.qa.ubuntu.com/qatracker/milestones/338/builds/92394/testcases/1439/results)

- Which version of Lubuntu did you install? Is it updated and upgraded to so that it is up to date with security updates and other updates?

-o-

- Which of the logins is still there? The passphrase, when you have the primitive screen with 'Lubuntu' and the five dots, or the password, when you have the login screen with the Lubuntu wallpaper?

If you run the following command in a terminal window and copy & paste the output to a reply (and put it within [noparse]```
tags
```[/noparse]), it will be easier to help you.

```
sudo lsblk -fm
```

---

### Post by jonathan81 on 2015-05-17
hello sudodos,

Thanks for the help.

I installed Lubuntu using a burned DVD. It is a dual boot system, but I can't remember which option I used exactly. I remember having to go the the partition screen to tell it which partitions to use.

I do not have the login with the primitive screen with 5 dots. I have the login with the Lubuntu wallpaper.

The output is:

[FONT=courier new]```
NAME   FSTYPE LABEL    UUID                                 MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                                                    sda    931.5G root  disk  brw-rw----
&#9500;&#9472;sda1 ntfs   WINRE    CA8C3F888C3F6DD7                                &#9500;&#9472;sda1   650M root  disk  brw-rw----
&#9500;&#9472;sda2 vfat            EA50-6959                            /boot/efi  &#9500;&#9472;sda2   260M root  disk  brw-rw----
&#9500;&#9472;sda3                                                                 &#9500;&#9472;sda3   128M root  disk  brw-rw----
&#9500;&#9472;sda4 ntfs   Windows  5AA25291A252718D                                &#9500;&#9472;sda4 456.4G root  disk  brw-rw----
&#9500;&#9472;sda5 ntfs   RECOVERY 705E3DB65E3D75C6                                &#9500;&#9472;sda5  18.8G root  disk  brw-rw----
&#9500;&#9472;sda6 ext4            97affe0e-a703-46cc-aad9-5f6dcb41bc46 /          &#9500;&#9472;sda6 443.2G root  disk  brw-rw----
&#9500;&#9472;sda7 swap            912b50ef-1229-4277-9b5f-4af1d28de7c4            &#9500;&#9472;sda7    12G root  disk  brw-rw----
&#9474; &#9492;&#9472;cryptswap1 swap    fea88d0a-49fa-4b47-8c9c-0838dbda01ad [SWAP]     &#9474; &#9492;&#9472;cryptswap1
                                                                                 12G root  disk  brw-rw----
&#9492;&#9472;sda8                                                                 &#9492;&#9472;sda8    96M root  disk  brw-rw----
sr0                                                                    sr0     1024M root  cdrom brw-rw----
```
[/FONT]
Have a good evening!

Jon.

---

### Post by sudodus on 2015-05-17
1. You have encrypted home and not encrypted disk. And there is cryptswap (encrypted swap, which is good).

2. Boot from the DVD drive. Mount the root partition of the internal drive, **/dev/sda6**.

```
sudo mount /dev/sda6 /mnt
```

```
sudo ls -la /mnt/home/*
```

You should find hidden files in the home folder and your user's home folder with something like crypt in the name. And you should ***not*** see your directories and files in clear text (because they are created when you are using them).

3. I don't understand why you had two logins before. It should have been only one login, as far as I can understand.

-o-

- Which version of Lubuntu did you install (15.04)? Is it updated and upgraded so that it is up to date with security updates and other updates?

---

### Post by jonathan81 on 2015-05-18
Thanks for the advice. I'm not confident enough to run those commands without a full backup first though.;{

I might try rebuilding my PC as Ubuntu anyway to see if I like it.

---

### Post by sudodus on 2015-05-18
A full backup is a good idea :-)

I suggest that you [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing]("http://ubuntuforums.org/showthread.php?t=2230389") what works best for you in that particular computer,

---

