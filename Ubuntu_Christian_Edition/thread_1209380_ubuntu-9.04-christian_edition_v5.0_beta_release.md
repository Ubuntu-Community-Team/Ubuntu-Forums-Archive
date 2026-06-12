---
title: "ubuntu-9.04-christian_edition_v5.0 beta release"
date: 2009-07-10
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-07-10
Finally I could release ISO file for Ubuntu CE based on Jaunty. You could see direct download link at the end of this post, or donwload through torrent using [attached torrent file]("http://ubuntuforums.org/attachment.php?attachmentid=120558&d=1247223582").

Some people complaint:

Why we need another iso file? Is it not a waste of bandwidth and effort?

Well, for people that just need to add the applications from ubuntu ce, they could do:

sudo apt-get install ubuntu-ce after adding 3 repository:

Wine repository, xiphos repository, and ubuntu-ce repository:

deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) binary/

For Wine and Xiphos repository please check their websites.

But I still have not answer the question of "Why another iso?" 

Below is my opinion:
1. So far I could not find any live cd with webfiltering enable by default. The best I could get is live DVD, ie. Ubuntu Muslim Edition, which provide websctrict (dansguardian gui).

2. If you want to install only one computer, that would be easy to configure. But for church or organisation that need to install many computers, that would be a tall order to customize each computer one by one. With Ubuntu CE, there is no customization, or very minimum customization needed.

At first I want to keep openoffice, but it is very difficult to make it below 700MB. After do a lot of trial and run, finally I gave up openoffice, and change it to gnome-office. The problem with gnome-office is we do not have powerpoint replacement.

I am considering to add "powerpoint viewer" installer, to complement gnome-office. But may be I would defer it until Karmic so as not to delay this release.

As such, below is the software I remove from default jaunty:

1. Openoffice suite
2. Fspot
3. tomboy
4. gnome-games

And as replacement, below is the applications that I added:

1. dansguardian gui (complete with dansguardian, tinyproxy and firehol, all are enabled by default)

2. xiphos (I think it is the best bible in linux so far)
Xiphos (formerly known as GnomeSword) is a Bible study tool written for Linux, UNIX, and Windows under the GNOME toolkit, offering a rich and featureful environment for reading, study, and research using modules from The SWORD Project and elsewhere. It is open-source software, and available free-of-charge to all.
[http://xiphos.org/](http://xiphos.org/)

3. OpenSong:
OpenSong is a free, open-source software application created to manage lyrics, chords, lead sheets, overheads, computer projection, and more.
[http://www.opensong.org/](http://www.opensong.org/)

4. e-sword installer : to bring e-sword (one of the best bible software) to linux easily.
e-Sword is a fast and effective way to study the Bible. e-Sword is feature rich and user friendly with more capabilities than you would expect in a free software package. The fact that e-Sword is free is just one of the blessings and does not speak of the quality of the software. I make my living writing software and I believe I have put forth my best effort in this endeavor. The real work, however, was put in by the godly men and women who devoted countless years creating the texts that have been made available for our benefit.
[http://www.e-sword.net/](http://www.e-sword.net/)

5. gnucash
GnuCash is personal and small-business financial-accounting software, freely licensed under the GNU GPL.

Designed to be easy to use, yet powerful and flexible, GnuCash allows you to track bank accounts, stocks, income and expenses. As quick and intuitive to use as a checkbook register, it is based on professional accounting principles to ensure balanced books and accurate reports.
[http://www.gnucash.org/](http://www.gnucash.org/)

6. wine (latest release)
To facilitate people converting from Microsoft Windows to linux.
[http://www.winehq.org/](http://www.winehq.org/)

7. encfs-gui (encryption directory management)
Easily create, and manage encrypted directory.
 EncFS provides an encrypted filesystem in user-space. It runs without any special permissions and uses the FUSE library and Linux kernel module to provide the filesystem interface. EncFS is open source software, licensed under the GPL.

As with most encrypted filesystems, Encfs is meant to provide security against off-line attacks; ie your notebook or backups fall into the wrong hands, etc.
[http://www.arg0.net/encfs](http://www.arg0.net/encfs)

8. linbread
Daily bible verse, launch at login, one verse per day.

9. Bible trivia
Daily question and answer about bible facts, one question per day.


Known issue:
1. OpenSong default directory is non existent, you have to choose default directory when first time launch it.
2. I still use old version of Desktop background as I still could not install the new one, may be size/resolution issue?
3. Live CD greeter is also use old version ubuntu ce, I thought should not be a problem.. But for usplash and gdm login theme, I have changed it to Jaunty with christian edition imprint.
4. UFW is still included, should be removed as we already have firehol.
5. There is no ubuntu_ce repository in the sources.list

Download link:
ISO file:
[http://thuygiang.homelinux.com/Ubuntu_CE/iso/ubuntu-9.04-christian_edition_v5.0.iso](http://thuygiang.homelinux.com/Ubuntu_CE/iso/ubuntu-9.04-christian_edition_v5.0.iso)

md5sum:
[http://thuygiang.homelinux.com/Ubuntu_CE/iso/ubuntu-9.04-christian_edition_v5.0.iso_md5sum.txt](http://thuygiang.homelinux.com/Ubuntu_CE/iso/ubuntu-9.04-christian_edition_v5.0.iso_md5sum.txt)

---

### Post by david_kt on 2009-07-12
After hosting and seeding for a few days, my computer suddenly off and could not on again. I will repair it and hopefully will up again in a couple of hours. If any if you has download it, please help to host it.

DK

---

### Post by david_kt on 2009-07-12
My server is already up again.
DK

---

### Post by mhancoc7 on 2009-07-12
I could not get the Ubuntu CE repos to work? I sent you an email about getting all of this setup on the ubuntuce servers. I look forward to hearing from you.

Thanks for all your hard work.

God Bless, Jereme

---

### Post by david_kt on 2009-07-12
> **mhancoc7 said:**
> I could not get the Ubuntu CE repos to work? I sent you an email about getting all of this setup on the ubuntuce servers. I look forward to hearing from you.

Thanks for all your hard work.

God Bless, Jereme

Thank you very much, finally I could turn off my computer. I have setup the repos there and I have updated my first post

DK

---

