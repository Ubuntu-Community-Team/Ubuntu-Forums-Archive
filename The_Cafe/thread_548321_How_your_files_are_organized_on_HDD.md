---
title: "How your files are organized on HDD"
date: 2007-09-11
forum: The Cafe
---

### Post by gary4gar on 2007-09-11
I really found difficult to manage my files as my data is increasing day by day . So looking for some suggestions from your guys movies, music, Linux, torrents,Picture files & various other application packages are very poorly organized.  

Often I waste my time just for searching for particular file in huge garbage heap. Sometimes I find some movies which I download months back just lying which I haven’t watched, I sure this problem may be with some of you two so share how you manage your data and most important small text files of countless tutorials ,pdf e-books ,documents ,blog entries etc..


I have one stranger requirement; i always change my OS as try newest Linux distros.


Please list how you organize your data
bwt i am looking for a setuo which helps me keep at least 3-4 os at same time installed



i have one 80gb hdd(internal) & one 320gb hdd(external)


one question how to manage to chnage our distro every 6 months, i mean does act bad for  HDD??

---

### Post by Tautoa on 2007-09-11
Are you asking what kind of folder structure we use? So, what does our /home directory look like?

4 OSs? Like, a quad boot system? Best of luck to you, it sounds like an organisational nightmare to me :)

---

### Post by gary4gar on 2007-09-11
i am asking for entire partion table
>  4 OSs? Like, a quad boot system? Best of luck to you, it sounds like an organisational nightmare to me :smile:

for me too but i can't stop my self from trying new things

---

### Post by the_darkside_986 on 2007-09-11
If you want to often switch Linux distros, but keep all your personal files, then put your /home folder on a separate partition, that is, there should be a partition mounted on /, another partition mounted on /home, and of course, a swap partition. You can put all these in one big "extended" partition since there is probably a limit of how many primary partitions you have. The extended partition will be such a size that won't fill up the hard drive, so you could then boot other non-Linux OS like a *BSD or Windows, or whatever, or even another Linux distro.

Anyway, this is what I did to save my files between upgrading from openSUSE to Ubuntu Dapper, and from Dapper to Feisty (can't directly upgrade from Dapper to Feisty). Of course, I became annoyed at the clutter and did a fresh install. 

AFAIK, Ubuntu's installer cannot make decent partition tables like this but the GParted CD and Suse Linux installer CD can. I had to use GParted before installing Ubuntu Feisty because Feisty didn't want to let me make an extended partition, but instead it tries to fill up the whole drive even though I needed to save room for others like FreeBSD and Windows Vista (which is mostly useless now).

Now I have a 500 GB IDE drive. I organize my home files in folders according to category. I have a downloads, Projects, software, and a media folder. Those are disorganized in each one though. I'll have to make sub-category directories later.

---

### Post by eentonig on 2007-09-11
\home\<username> (off course)
And then subfolders
- ~\Documents\
- ~\Movie\
--------~\Movie\<Movie Title 1>\
--------~\Movie\<Movie Title 2>\
...
- ~\Music
--------~\Music\A\
------------~\Music\A\<Artist Name>\
-------------------~\Music\A\<Artist Name>\<Album>\
....
- ~\Images\
--------~\Images\<Year>\
------------~\Images\<Year>\<Month>\
----------------~\Images\<Year>\<Month>\<Day>\
...
- ~\bin\     # Where I keep my personal scripts and programs
- ~\dev\   # Where I keep scripts and progs I'm working on.
- ~\download\    #Everything that get's downloaded.
-~\Torrents\      # Where I download torrents

Those are the most used. Then I have two nfs exports to my home folder on the other two pc's.
~\tigra
~\camel

And some links to (mostly duplicate) folders on an external HD.


EDIT/
And I just realized I responded too fast.

All of these are on the same 400G HD
/dev/sda1             9.7G  273M  8.9G   3% /
/dev/sda2             241G  139G   90G  61% /home
/dev/sda3             9.7G  151M  9.0G   2% /media/sda3
/dev/sda5             9.7G  151M  9.0G   2% /media/sda5
/dev/sda6              49G  3.3G   43G   8% /usr
/dev/sda7              47G   15G   29G  35% /var

This is an external 400G HD for BU
/dev/sdb1             367G  185G  164G  53% /media/disk

---

### Post by wersdaluv on 2007-09-11
> **eentonig said:**
> \home\<username> (off course)
And then subfolders
- ~\Documents\
- ~\Movie\
--------~\Movie\<Movie Title 1>\
--------~\Movie\<Movie Title 2>\
...
- ~\Music
--------~\Music\A\
------------~\Music\A\<Artist Name>\
-------------------~\Music\A\<Artist Name>\<Album>\
....
- ~\Images\
--------~\Images\<Year>\
------------~\Images\<Year>\<Month>\
----------------~\Images\<Year>\<Month>\<Day>\
...
- ~\bin\     # Where I keep my personal scripts and programs
- ~\dev\   # Where I keep scripts and progs I'm working on.
- ~\download\    #Everything that get's downloaded.
-~\Torrents\      # Where I download torrents

Those are the most used. Then I have two nfs exports to my home folder on the other two pc's.
~\tigra
~\camel

And some links to (mostly duplicate) folders on an external HD.

Amazing!! :guitar:

---

### Post by jdong on 2007-09-11
I use a similar-to-OSX hierarchy (even before I started to use OS X and knew what OS X did):

~/Documents: All kinds of documents; /docs is a special bzr repository that helps me roam certain documents across the 5 or so machines I use regularly. It is organized by course number and archived every year to avoid clutter.

~/video: My movie / TV show collection. 1st level subdir is series name, 2nd level is season.

~/Desktop/Incoming: The unsorted bin. Stuff that I want to keep but haven't sorted goes in here.

~/tmp: The temporary storing location. Most commonly stuff that I downloaded like driver installer or source tarballs. I keep it in here when I have extra space (so I don't have to go out and fetch it again). When I am running short on space, it's a folder that's safe to just rm -rf without thinking.

~/src: My sourcecode collection. First sublevel are all bzr repositories that are the names of the particular code I'm working on; second sublevel are bzr branches of the specific branch I am working on. I manage almost all, if not all, of my code in a VCS of some sort. Over the years I've learned how much this helps me.

My torrents are done actually in /var/torrents, which is a separately mounted XFS volume. It helps keep the fragmentation and hectic nature of torrents from affecting the filesystem health of the rest of the system. AFter they are done, I'll move it at once into my correct directory.

---

### Post by Erik Trybom on 2007-09-11
I don't think it matters much HOW you organize your /home directory. Just pick a structure that makes sense to you. The important thing is THAT you do it.

In a similar thread some months back, I read a very good quote. It read: "Either you make it easy to put in, or you make it easy to get out".

That is, if you spend 5-10 seconds every time you download a new file on choosing the right directory for it, then you can easily find it again in roughly the same amount of time. If on the other hand you just send it to ~/downloads (or, God forbid, ~/Desktop), then you gain a few seconds in the downloading process but you risk spending minutes trying to find the file again.

---

### Post by urukrama on 2007-09-11
There is already a thread on this: [http://ubuntuforums.org/showthread.php?t=423137&highlight=organise+files](http://ubuntuforums.org/showthread.php?t=423137&highlight=organise+files)

---

