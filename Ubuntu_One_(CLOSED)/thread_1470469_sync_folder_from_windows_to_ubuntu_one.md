---
title: "sync folder from /windows to ubuntu one"
date: 2010-05-02
forum: Ubuntu One (CLOSED)
---

### Post by froanas on 2010-05-02
Hi,

I'm dual-booting Windows 7 and Lucid, and I want to sync my documents folder from /windows (a mounted ntfs partition) to Ubuntu One. I right-click and it lets me click on sync with Ubuntu One, but then it does nothing. I've checked and I am able to sync other folders from my ext4 filesystem. Any ideas?

Joe

---

### Post by joshuahoover on 2010-05-03
> **froanas said:**
> Hi,

I'm dual-booting Windows 7 and Lucid, and I want to sync my documents folder from /windows (a mounted ntfs partition) to Ubuntu One. I right-click and it lets me click on sync with Ubuntu One, but then it does nothing. I've checked and I am able to sync other folders from my ext4 filesystem. Any ideas?

Joe

Hi Joe,

Right now we're experiencing some issues on the server side. If you run the following command it should show your /windows folder listed:

u1sdtool --list-folders

If it does, then it's likely an issue on the server side that we're working on fixing right now. If the folder is not listed then you might want to try running these commands:

u1sdtool -d
u1sdtool -c

And then in a few minutes run the --list-folders command again.

To see stay up on Ubuntu One and the status of the service, you can check out the following links:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

My apologies for the inconvenience and thank you for your patience.

Joshua

---

### Post by willsomebody on 2011-05-08
I am trying to do the same thing and having similar problems. Did anyone ever figure this out?

---

### Post by pnaegele on 2011-07-16
Doesn't work with me! Waited about half an hour now, rebooted, run the command again and waited again.

Maybe I got it wrong? Where do I run the command? I think as usual in the terminal/console.

---

### Post by willsomebody on 2011-07-16
Apparently Ubuntu One prefers things in your home folder, so I changed my fstab to mount my Windows partition to $HOME/windows and then told it to sync the folders in there instead of the links that I made in my home directory. Hope that helps.

---

### Post by wcorrer on 2011-09-05
Hi there, 

changing *fstab* file was enough. It seems like U1 only recognizes folders in /home/... I'm not sure. But now I'm syncing the files of a entire ntfs partition. 

BTW.. thanks for the tip!

---

