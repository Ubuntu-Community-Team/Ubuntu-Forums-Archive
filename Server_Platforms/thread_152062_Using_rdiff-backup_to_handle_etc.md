---
title: "Using rdiff-backup to handle /etc"
date: 2006-03-29
forum: Server Platforms
---

### Post by savage on 2006-03-29
I have been using rdiff-backup over the last week and have been extremely happy with it. The reason for happiness is that it has some features that make backing up /etc very easy. For my purposes I wanted something that would work well with me fiddling with config files and possibly breaking things. The idea is that I should be able to replace a screwed up file, no matter how long ago I messed it up.

When I first started out I would just copy any config file to a configfile.conf.bak in the same directory. Make my changes, and if things broke I could always compare the new and old file. Then I tried using RCS, which felt like doing the .bak thing but with lots more complicated commands. I looked at CVS and read some online howtos about backing up /home with CVS or Subversion.

The problem with trying to use version control for the /etc directory is that VCS (Version Control Systems) are not built to handle /etc they are made primarily for handling programming projects. Often symlinks are not supported, or file permissions aren't handled with version control. The other problem with version control on a directory like /etc is that when you install software it adds files here. Version control products may or may not deal with this well. The usual workaround is to make a copy of /etc and then put that under version control, adding files as you need to, or as new programs are installed. Of course you could also just manually add single conf files to a VCS when you were going to change one. This is probably a method that would work well for many people.

Rdiff-backup handles permissions, symlinks, and is like rsync in that it can copy only the increments of changed files. This makes backups quick, especially over a limited network connection. The one thing rdiff-backup doesn't do is log what you have done, which VCS's do. Basically the idea is that when you commit a change you put in a note explaining what you have done. What I did is create a subdirectory under /etc and I have a text file here for each file/application I edit and I put notes about the changes I have made along with the increment file information (using rdiff-backup -l).

After modifying /etc my command is as simple as
$ sudo rdiff-backup /etc /var/archive/etc

Restoring files can be as simple as copying them (for the last backed up) or you can specify out of the increments with rdiff-backup -r 'date' /var/archive/etc

If you are interested in using this product some excellent places to learn more are. [http://www.nongnu.org/rdiff-backup/]("http://www.nongnu.org/rdiff-backup/")

Good introductory article
[http://arstechnica.com/articles/columns/linux/linux-20060202.ars]("http://arstechnica.com/articles/columns/linux/linux-20060202.ars")

Automated backups with rdiff-backup
[http://www.howtoforge.com/linux_rdiff_backup]("http://www.howtoforge.com/linux_rdiff_backup")

Gnome utility for GUI interface
[https://sucs.org/~davea/trac]("https://sucs.org/%7Edavea/trac")

---

### Post by Patsoe on 2008-01-18
I know this is an old thread, but I really want to thank you for sharing that!

It's a brilliant solution, not in the least because, in a situation in which you will need that backup most, you may be looking at a completely borked system - perhaps too broken to get your vcs running to restore files from diffs. In such a situation rdiff-backup shines because the main backup is just a mirrored file system, and thus simply accessible.

One thing I would like to add: it might be useful to set root-only read-permission on the backup directory, just to be safe. It's not strictly necessary since rdiff-backup should preserve permissions, but it's not much work either: "sudo chmod 700 /var/archive/etc" should do.

Just last week, I put my /etc directory under version control using bazaar (a Canonical-sponsored cvs, see [http://bazaar-vcs.org/](http://bazaar-vcs.org/) ). This is not to hard to do either, but I like your solution better!!

---

### Post by HermanAB on 2008-01-18
You can use RCS for /etc:
[http://aeronetworks.ca/rcs-howto.html](http://aeronetworks.ca/rcs-howto.html)

---

