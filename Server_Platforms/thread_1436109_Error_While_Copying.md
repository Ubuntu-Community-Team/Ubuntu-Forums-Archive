---
title: "Error While Copying"
date: 2010-03-22
forum: Server Platforms
---

### Post by BULLIT22 on 2010-03-22
Hello All,
 
I'm very new to Ubuntu. So please dumb things down a bit for me. I installed Ubuntu 9.10 server edition and everything went well when I found everything I needed. I currently have 4TB of storage on a FreeNAS server that I need copied over to my New Ubuntu server. I enabled the Ubuntu Desktop so it is a little easier for me to work with. 
 
Anyway, I open 2 windows on my desktop. 1 is a drive on the Network from my FreeNAS machine. The other is a drive on my Ubuntu server. When I go to copy files from my freeNAS machine to a drive on Ubuntu I get this error,
 
"Error While Copying"
The Folder "folder name" cannot be copied because you do
not have permissions to create it in the destination.
 
Anyone know how to go about getting my stuff copied over? 
 
Also, I don't want to have to enter a password to enter my Samba shared drives on my network when all is said and done. Any way of doing that? 
 
Anyway, thanks for any help in advance.
 
*Edit* Don't know if it will make a difference or not, but I have all the extra drives in my Ubuntu Server auto mounting with a program called "Storage Device Manager". I think that's what its called. I'm at work at the moment, I'll check later.

---

### Post by mizar001 on 2010-03-22
Hi. 

What's the exact destination of the files ?

Anyway you should use only your home folder (usually /home/username) or subfolders, in order to have rights to copy.

Any other external folder in the system is protected by user write access, it's a security organization. 

If you still have problems there's a fast solution (that i don't recommend) : 
  - open terminal
  - digit 'sudo nautilus&'
  - digit your user password and you will open the folder browser
    with root superuser privileges.


For the other response : the samba share works the same as between two windows machines. So you can avoid password digiting only if you share directly the folder from windows and the two machines are set within the same DOMAIN/WORKGROUP. For this you may take a look in the file /etc/smb/smb.conf and make your variations (you must be a privileged user).

---

### Post by BULLIT22 on 2010-03-22
I assume you are talking about the exact location as in, sda1?
 
I am talking about 3.5TB worth of Data. So my home folder doesn't seem to be reasonable unless I can mount those drives in that location. 
 
All my PC's are on the the default "Workgroup". I will check again to see if the Ubuntu server is. 
 
I'm not too worried about security because my Ubuntu server, Ubuntu desktop w/XBMC and freeNAS are on a Closed Network with no internet connectivity unless I manually plug into my modem.

---

### Post by mizar001 on 2010-03-22
You in the first post wrote :
> 
'When I go to copy files from my freeNAS machine to a drive on Ubuntu I get this error'

I assume that freeNAS is mounted in the /media folder of ubuntu server, but that's not a problem. The problem is the destination of your copy. If you are not a privileged user, you only can copy inside your home folder (for example the folder /home/user/Desktop).

Furthermore you should have success in coping from ubuntu to freeNAS also, but that depends on the author of the mount. If the mount is done by administrator user you probably can't write on NAS.

Long story short, if you want to solve most of things without thinking on security more than necessary , use the privileged user to do anything whenever you have permission problem (e.g. with sudo command).

---

### Post by BULLIT22 on 2010-03-22
FreeNAS drives are located in the Network folder of Ubuntu, Not Media. is there a problem with this? I am using the GUI in ubuntu to copy things over, So how would I go about issueing the command to copy in the Terminal? Sorry for all the Q's, as I said I am fairly new and thanks for the help so far.

---

### Post by BULLIT22 on 2010-03-22
Is this what you mean?
 
If you still have problems there's a fast solution (that i don't recommend) : 
- open terminal
- digit 'sudo nautilus&'
- digit your user password and you will open the folder browser
with root superuser privileges.

---

### Post by mizar001 on 2010-03-22
yes ! As security admin i would not recommend that, but as private user not connected to potential threats, i can say that this is the fastest solution.
Furthermore if you have permission problems again, you can change them right clicking on the destination folder.

---

### Post by BULLIT22 on 2010-03-22
OK, got home for lunch. Tried the "sudo nautilus&" command and got the same result. No go on the files being copied over. Furthermore, I don't have the smb.conf in the directory you mentioned above. Don't know what is going on here????
 
When I enter the said command I get this output,
 
deadpool@universe:~$ sudo nautilus&
[1] 4067
deadpool@universe:~$
 
 
 
Any suggestions?

---

### Post by KB1JWQ on 2010-03-22
For a really quick and dirty way to solve this, (since you're in the terminal anyway, and this IS the server platform section of the forum, why not rsync -av SOURCE DESTINATION and call it a day?  If it still throws the error, you could prepend sudo to that.

---

### Post by BULLIT22 on 2010-03-22
I would if I knew how to do that. Any help accomplishing this would be app.

---

### Post by Vegan on 2010-03-22
I suggest buying a book or 3 on Linux and start reading to get schooled. Trying to run without learning to walk is what you're doing.

---

### Post by BULLIT22 on 2010-03-22
My first post asked people to please dumb it down. Did it not? I know a few things, not a lot at the moment. I am int the process of reading a e-book. If you have any suggestions that may be a better way of posting. Yeah?

---

### Post by mizar001 on 2010-03-22
sorry BULLIT22 for late reply...

sudo nautilus & won't work because nautilus is a graphic application and sudo is not. I suggest you this workaround :

sudo echo 
(digit your password)
sudo nautilus &

(this time sudo will work because the password is stored into memory for about 15 minutes, so it will not stop nautilus to start).

---

### Post by BULLIT22 on 2010-03-22
OK, I managed to get the command "sudo nautilus" without the "&" symbol. But I get an error when trying to open FreeNAS in the network. Here that is,

Could not display "networ:///"
Nautilus cannot handle "network" locations.

So that looks like it will not work.

---

### Post by BULLIT22 on 2010-03-22
OK, let me try that. Thanks.

---

### Post by BULLIT22 on 2010-03-22
Mizar001, Thanks for all the help so far. the nautilus still isn't opening network.

---

### Post by BULLIT22 on 2010-03-22
I can't do anything on the drives. I created them via Gparted, I can't even creat a new folder on them.

---

### Post by nix4me on 2010-03-22
Correct, because you need to apply some permissions to them.  So if your Ubuntu server drive is mounted to something like /mnt/drive, then apply permissions to it from the terminal.

sudo chown username:groupname /mnt/drive
sudo chmod 755 /mnt/drive

so if your username is bullit22, then:

sudo chown bullit22:bullit22 /mnt/drive
sudo chmod 755 /mnt/drive

That will allow you to write to the drive/folder
then just fire up nautilus and copy

---

### Post by nix4me on 2010-03-22
Second answer to your second question:

Yes, it is possible to make samba not ask for username/pass.
In the /etc/samba/smb.conf file, change the security=user to security=share

---

### Post by BULLIT22 on 2010-03-22
I get this in terminal,

/mnt/drive': No such file or directory

---

### Post by nix4me on 2010-03-22
The drive has to be mounted, that was an example.

In the gparted or disk utility, you must specify a mount point for the drive.

Or you must mount it manually.

---

### Post by BULLIT22 on 2010-03-22
I did, I used sdb1

Nothing shows up in /mnt

also tried /media

When I try in /media/sdb1 I get this 

operation not permitted

---

### Post by KB1JWQ on 2010-03-23
Can you paste the output of "mount" without the quotes?

---

### Post by BULLIT22 on 2010-03-23
No can do, sorry guys. I got fed up last night and did a reinstall of Ubuntu server 9.10 and installed everything I had. Mounted my drives, and things are copying over from my FreeNAS machine to my Ubuntu Server just fine now. Sorry guys, i have no idea what it was or what I did. but thanks for all your help.

---

### Post by mizar001 on 2010-03-24
For me it was only a permission problem, get used to face it often in Ubuntu for many other things, and i hope you are not forced to reinstall everytime ;)
Anyway the permission are correctly set with the new install, and you solved the problem.

---

### Post by BULLIT22 on 2010-03-24
Yeah, I'm not sure what was going on there. I had the server installed on a 250gb hard drive about 2 1/2 weeks ago. everything was copying to my drives just fine, then the 250gb drive went out. Ubuntu told me it was failing so I ran a boot cd and the hard drive tool I used found nothing wrong. So I did some research and found a couple things on it and people were saying it was a bug in Ubuntu server. So I ignored it and it ended up failing anyway. so i had to reinstall Ubuntu Server and the only thing different I did was use a program called "PySDM" to auto mount my drives on start up. With this new and recent install I left that out and have had no problems. Thanks for the help though.

---

### Post by jrssystemsnet on 2010-03-24
> **mizar001 said:**
> sudo echo 
(digit your password)
sudo nautilus &While it's not relevant to the OP's problem (and sudo nautilus wasn't ever the right answer to that problem anyway), if you want a GUIfied version of sudo, **gksudo** is precisely that.

Though typically, the reason to use **gksudo** instead of **sudo** is if you want a script to ask a user for elevation in the GUI where they're more comfortable with it.  For example, say you made a backup script that needed elevation, and you wanted a user to be able to double-click an icon to run that script, you'd want the script to use **gksudo** so that the user got the same kind of elevation prompt s/he was already used to from things like system updates, etc. rather than one in a text window which might confuse the user (or the user might ignore).

---

