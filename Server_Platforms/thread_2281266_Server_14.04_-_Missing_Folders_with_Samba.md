---
title: "Server 14.04 - Missing Folders with Samba"
date: 2015-06-05
forum: Server Platforms
---

### Post by motobeats on 2015-06-05
I setup a samba share in Ubuntu Server 14.04 and in general it works well. However I have a folder with lots (1000s) of subfolders that does not always display every available folder. Here is what my testing has found.

1. From Mint desktop, connect over smb. Result: Missing some folders (most of them in fact)
2. From Mint desktop, mount the smb share. Navigate to the folder through the mount point. Result: All folders available
3. From Windows 7 desktop, connect over smb. Result: Missing some folders. In fact the same ones as were missing from Mint, so it does not appear random.
4. From Android using ES Explorer, connect over smb. Result: All folders available (this one surprised me).

Any thoughts on what is going on here? I have triple checked over ssh that the folders are in fact there.

---

### Post by cariboo on 2015-06-05
Check the directory permissions. On my home server, not connected to the internet, they are 755.

---

### Post by motobeats on 2015-06-06
I double checked and the permissions for all the folders are 775. Inside some of the sub folders are sub-sub folders with identical permissions but that do not uniformly show up via smb.

Again, all of the folders show up when I mount the cifs share and on my phone so I wouldn't think it is a permissions issue (admitting of course my knowledge on this is limited).

---

### Post by cariboo on 2015-06-06
Could you shows how you setup the shares in /etc/samba/smb.conf

---

### Post by motobeats on 2015-06-06
Some more investigation.

First, here is the share in question from the smb.conf

[samba]
   comment = Webserver File Share
   path = /srv/samba
   browsable = yes
   guest ok = no
   read only = no
   create mask = 0755
I connected to the share using smbclient and I found this error when I list the directory in question

> smb: \music\> ls
cli_list: Error: unable to parse name from info level 260


The client then proceeds to list about 200 of the ~1000 of available folders

Compare to using the mount point:
> inspiron ~/Music $ find -type d -maxdepth 1|wc -l
1141




And this looks like something that could be messing up SMB. It is not reproducing but the terminal is displaying a character that looks like a box with text inside. Image attached.
> @inspiron ~/Music $ ls -l|more
ls: œ: No such file or directory
ls: €: No such file or directory
ls: ˆ: No such file or directory
ls:  : No such file or directory
ls: „: No such file or directory
ls: ´: No such file or directory
total 0
drwxrwxr-x  3 a a 0 May  5 16:31 ´
drwxrwxr-x  3 a a 0 May  5 19:15 €
drwxrwxr-x  4 a a 0 May  5 18:46 „
drwxrwxr-x  3 a a 0 May  5 17:47 ˆ
drwxrwxr-x  3 a a 0 May  5 19:24 œ

---

### Post by motobeats on 2015-06-07
Looking at an sdiff of a backup of the data on another machine and the current folder exhibiting smb issues, I noticed at least one missing folder. Right now I am blaming Björk and the need for an umlaut in her name.

---

### Post by SeijiSensei on 2015-06-07
What filesystem is being used here?  Ext4?  NTFS?  Something older like FAT32?  If all your systems use Unicode, and the filesystem is using ext4 (or NTFS, I believe), there shouldn't be a problem with character encodings.

---

### Post by motobeats on 2015-06-07
I am mounting the file system locally as cifs. The fs on the remote server is ext4
> /dev/mapper/webserver--vg-samba on /srv/samba type ext4 (rw)

I tried remounting the volume with iocharset=utf8 
> $ sudo mount -t cifs //webserver/samba/music ~/Music -o noexec,iocharset=utf8

But I still have folders that can't display
> $ ls -l ~/Music/|wc -l
ls: /home/Music/&#339;: No such file or directory
ls: /home/Music/&#8364;: No such file or directory
ls: /home/Music/&#710;: No such file or directory
ls: /home/Music/ : No such file or directory
ls: /home/Music/&#8222;: No such file or directory
ls: /home/Music/´: No such file or directory
1141


Here are my locale settings
> $ locale
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

---

### Post by motobeats on 2015-06-07
I still think this is some encoding thing. Using ls -b helps with being able to grep the "offending" folders. Without -b I get a question mark. 

This is the output when I ssh into the fileserver (no comments about music tastes please)
> $ ls -lbR /srv/samba/music |grep "/srv/samba"|grep 366
/srv/samba/music/Bj\366rk:
/srv/samba/music/Bj\366rk/Army of Me - EP:
/srv/samba/music/Dr\366mhus:
/srv/samba/music/Dr\366mhus/Dr\366mmar:
/srv/samba/music/M\366tley Cr\374e:
/srv/samba/music/M\366tley Cr\374e/Dr. Feelgood:
/srv/samba/music/M\366tley Cr\374e/Motley Crue - Greatest Hits:
/srv/samba/music/R\366yksopp:
/srv/samba/music/R\366yksopp/Melody A.M_:


The folders above are all missing from the cifs mount on my local machine (laptop running Mint).

---

### Post by SeijiSensei on 2015-06-08
If you're mounting an ext4 file system onto a Linux client, use NFS, not CIFS.  NFS should show you the exact same file names on the client as on the server.  CIFS only makes sense if you need to share files on a Linux server to Windows clients.

[https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html)

That said, it looks like the file names were scrambled in the process of writing them to the server.  I share directories with Japanese file names using NFS that appear correctly on both the server and the client. For instance,
```
&#25993;&#34276;&#24658;&#33459; - 03 - &#26263;&#40658;&#12398;&#34903;&#12363;&#12425;&#12398;&#33073;&#20986;.ogg
```
These were ripped from the CD using KDE's native "kio-slave" technology that creates virtual folders in the Dolphin file manager each representing the CD in the available formats like FLAC, Ogg, and MP4.  Howver I'm pretty sure any Linux ripper would preserve the original file names.

---

### Post by motobeats on 2015-06-08
Point taken on CIFS v. NFS. That said, I do have a Windows box on the network to use with some software. And Samba doesn't seem to be able to support NFS mounts without some extra work which I choose to avoid.

However, when I ssh into the file server, the offending directories appear with question marks in them. So this is a problem local to the box, not just a smb/NFS/CIFS conflict.

I did try changing my language to de_DE but that didn't help. Maybe I should have tried de_DE.iso88591? Short of it is these characters are messing up the standard filesystem commands (mv, find, etc). Using ls -b I can see they map to umlauts (374,326,366)

[http://www.pjb.com.au/comp/diacritics.html](http://www.pjb.com.au/comp/diacritics.html)

I was able to rename the folders and files with this command

> $ find -inum (NUMBER HERE) -exec mv {} "NEW FILE/FOLDERNAME HERE" \;

Despite the error messages it throws it worked for me.

Doing another sweep by and to make sure I them all and then I will see if all the folders appear.

---

### Post by volkswagner on 2015-06-09
I can't remember for sure, but I think you could have filesystem corruption or a bad disk.
I say this based on the question marks you see when running ls command.

Run smartmontools/smartutil.

You could try creating the files/directories with similar names/characters on an ext4 formatted USB drive to see if the
problem can be reproduced.

---

### Post by motobeats on 2015-06-09
Definitely not any type of corruption. After renaming the offending folder/filenames, I am able to navigate them and play the music files without issue.

I'm pretty sure the question mark is just signifying that the terminal does not know how to handle that character. When I use ls -b, the terminal prints the unicode for the character instead of the question mark.

---

### Post by motobeats on 2015-06-09
All fixed! Here is a quick recap of the issue, failed attempts to fix, and the workaround.

Problem: My music folders, when moved from my Windows laptop (note that my folders were managed by iTunes) to my Ubuntu server contained unicode characters that my terminal could not display (here is a list: [http://www.ssec.wisc.edu/~tomw/java/unicode.html](http://www.ssec.wisc.edu/~tomw/java/unicode.html)). Specifically, my terminal had an issue with characters that used an accent over vowels (umlauts, etc.). At best, this caused the folders to be unreadable (locally could not manipulate them or import the music within the folder into Banshee). At worst, it caused other folders with "safe" names to not appear (this happened when navigating to the folder over smb from my Mint 17 laptop or my Windows 7 desktop). My phone handled the situation better and simply skipped the ~6 offending folders as opposed to Mint/Windows which ended up skipping ~1,000 of the 1,140 folders because those clients didn't know how to handle the 6 offending folders.

Failed attempts: Manipulating the folders in a traditional manner was not possible as I could not type the name with my settings and the terminal would not have recognized it anyway. Changing my LANG variable did not help either.

Solution: Using ls -b I was able to display the offending folders with printable characters. I then renamed them by hand using this command.

> First, cd to the directory then ls -lib to find the inode number then find -inum (NUMBER) -exec mv {} "(NEW_NAME" \;

I get error messages when I run the command but it seems to work. Having the folder/file to be changed within the pwd is important.

After renaming all of the folders and files, all music is now visible and importing into Banshee. Additionally, Mint is now able to see all 1,140 folders over smb.

Thanks all for your help on things to look into.

---

### Post by motobeats on 2015-06-09
Would be great if the client side handled this situation more like my phone and skipped the folders as needed instead of the behavior exhibited. Maybe not a bug but certainly a place for improvement.

Thoughts?

---

