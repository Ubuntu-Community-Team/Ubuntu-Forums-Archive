---
title: "Encryption for online backup services"
date: 2009-12-16
forum: Tutorials
---

### Post by manosx on 2009-12-16
This is a guide on how to use encryption with the encfs in online backup services like dropbox and Ubuntu one. I guess it can be used for other online backup services.
Encfs is used because it is pass through. This means that the encryption is happening per file, allowing us to change files without the need to upload the hole block device.
The block device is represented as a file. When using this method, of one block device,  the online backup service sees only that file, resulting uploading the hole file again for a small change (changing a file of some KB for example).
(I am not aware if a service does this 'byte wise' or 'block wise', that is to upload only the changes.

**The instructions:**
**1.** Set up the online back up service, I will use as example Ubuntuone.
Create the account in ubuntuone website and install the client.
```
sudo apt-get install ubuntuone-client
```
**2.** Install encfs and fuse-utils (fuse-utils allows userspace programs to export a virtual filesystem).
```
sudo apt-get install encfs fuse-utils
```
**3.** Create the directory that you want to be encrypted in the online backup service directory and the directory you want to see the unencrypted data. (the second will not be in the backup service directory of course!)
```
cd ~
mkdir Ubuntu\ One/encrypted/ 
mkdir Ubuntu_secure/

```
**4.** Create the partition.
```
encfs /home/[your username]/Ubuntu\ One/encrypted/ /home/[your user name]/Ubuntu_secure
```
Change [your username] with your username!
The first time it will create the filesystem and it will ask you for a password (twice). 
Every other time, this command will mount your partition asking you your password (once).
You can now see a new device. Copy you data there and see the folder ~/Ubuntu One/encrypted/ to fill with encrypted data!

**5.** To unmount the volume you do:
```
fusermount -u /home/[your username]/Ubuntu_secure
```

In any other system you go and set up the online backup service, you will have your files encrypted. You need to have encfs and fuseutils installed. Encfs will see the encfs6.xml (maybe other name in other systems), and mount the partition providing the correct password.

**Do it automatic with a script!** 
You can mount/unmount the encrypted data automaticly with a script!
The script:
```
#!/bin/bash
volume="/home/[your username]/encrypted"
if [ -d $volume ]; then
	if mount | grep "on $volume type" > /dev/null; then
		fusermount -u /home/[your username]/Ubuntu_secure
		echo "Drop Box encrypted partition unmounted"
		sleep 1
	else
		encfs /home/[your username]/Ubuntu\ One/encrypted/ /home/[your username]/Ubuntu_secure
		echo "Drop Box encrypted partition mounted"
		sleep 1
		fi
else
	echo "Directory doesn't exist, do: mkdir $volume"
	sleep 2
fi

```
Copy this code in a file ubuntuone.sh in your home directory for example. Change it to your needs. Make the script executable:
```
cd ~
chmod +x ubuntuone.sh

```
The script checks if the volume is mounted. If it is, it unmounts it. If it's not, it mounts it (will ask you for password).
If the mount point doesn't exist, it will tell you how to create it.
You run it by double clicking and selecting 'Run in terminal', or from the console with
```
cd ~
sh ubuntuone.sh
```

**Call the script from a launcher**
You can also make an application launcher in gnome panel to run your script. The command of the launcher can be:
```
xterm -geometry 45x3+0+0 -bg black -fg red /home/manos/ubuntuone.sh
```
The option -bg is the background colour and -fg the characters colour. In the -geometry is the placement/size of the window, this is top left.
For more information on how to run xterm the way you like it:
```
man xterm
```

---

### Post by pascal91 on 2009-12-17
This can be done with a GUI tool like cryptkeeper. First, install it :
```
sudo apt-get install cryptkeeper
```Then, launch cryptkeeper (in system tools category) or add it to started up applications.
Finally, use the cryptkeeper icon displayed in the notification area ("system tray") to define some encrypted folders and mount/unmount them.

---

### Post by manosx on 2009-12-17
With cryptkeeper you can do the hole thing through a GUI!
Very nice tool :)

---

### Post by thebear78 on 2009-12-17
Interesting. My concern is how have you found synchronization to other computers functioning with this method? Is the encrypted data usable if you encrypt on computerA, sync up to Ubuntu One, and sync down to computerB? What about sharing folders with others? Seems like this only gives you an encrypted backup in the cloud for a single computer. I could be wrong though. Thanks.

---

### Post by manosx on 2009-12-17
Actually the encfs is checking the file .encfs6.xml in the encrypted directory. I have three computers that i share data between. One of them have no access to fast Internet.
I encrypted the data in one computer.
The second computer synchronized. It took also the file .encfs6.xml, then i encfs-mount it correctly.
I copy the hole encrypted dir to the computer with the slow Internet with other means(external hard disk). When it went online it synchronized without downloading the files.

I also checked having it mounted to two locations (I mean dropbox working and mounted with encfs). I could write/delete files from one point and the other synchronized.

---

### Post by micdhack on 2010-03-30
> **manosx said:**
> With cryptkeeper you can do the hole thing through a GUI!
Very nice tool :)

I configured everything through the gui although there is one problem. I don't know how i can change the mount directory to be outside the Ubuntu one directory.

Update: i found a way. At first you use the commandline encfs to create the folder and then you import it. The cryptkeeper will prompt you to enter the mount directory.

---

### Post by Nisal on 2010-03-30
nice in4 thanks:)

---

### Post by Despot on 2010-04-06
Thanks for the tutorial. As noted by micdhack, if you use cryptkeeper, it's important to define things manually first so that things end up in the right spots. Maybe an update to the original tutorial would be worthwhile?

This might help somebody else: I've been messing around with the folder structure in Ubuntu One a bit (particularly, I've been experimenting with whole-folder encryption by replacing the Ubuntu One folder with a symlink to an encrypted folder), and occasionally it seems to get the sync daemon a bit confused. Logging out and logging in again seems to fix things right up, and I imagine restarting the daemon would have the same affect.

---

### Post by duanedesign on 2010-04-24
This is a very interesting thread. Thanks manosx and others who have contributed to this thread. :)

---

### Post by igorlopez on 2010-06-05
Thanks for the good explanations.
I have a question on how it is supposed to work.

Scenario:
I have two PC that I would like to share encrypted files between using Ubuntu One.

What I did was to create an encrypted folder with encfs inside the Ubuntu One folder as explained by manosx. This was done on both computers.
Both PC's folders (encrypted) are synced as expected but I do not understand how to set it up such that the Ubuntu_secure folder is automaically updated, i.e I would like to work with the decrypted file in Ubuntu_secure.

Sorry for such a dumb question.

---

### Post by micdhack on 2010-06-07
> **igorlopez said:**
> Thanks for the good explanations.
I have a question on how it is supposed to work.

Scenario:
I have two PC that I would like to share encrypted files between using Ubuntu One.

What I did was to create an encrypted folder with encfs inside the Ubuntu One folder as explained by manosx. This was done on both computers.
Both PC's folders (encrypted) are synced as expected but I do not understand how to set it up such that the Ubuntu_secure folder is automaically updated, i.e I would like to work with the decrypted file in Ubuntu_secure.

Sorry for such a dumb question.

As far as the encrypted folders go they are automatically updated when they are in the Ubuntu one, but the mounted unencrypted versions of these directories i dont know if they are dynamically updated or you have to umount and mount them again in order to see the changes in the files.

Personally i use the encrypted directory as a backup directory and even though i sync files with a second computer too, i always work on the main computer and i never make changes from the second computer to the encrypted directory.

---

### Post by mdwy62 on 2011-03-29
It doesn't work. If you try to open the encrypted folder on the second machine, cryptkeeper will trash your password and you will not be able to access your encrypted files on either machine. DO NOT USE encfs/cryptkeeper with ubuntu one if trying to sync encrypted files (and view them) between two machines.

---

### Post by manosx on 2011-03-31
This is very weird, I am using this with dropbox and i guess it is usable in any similar service.. Because it doesn't have to do with the service..

That is to say, if you have and NFS mounted and inside an encrypted directory all the users that have mounted the NFS can mount it with cryptkeeper and the same password and do changes..

With cryptkeeper you should 'Import EncFS folder' and not create a new one obviously. Importing the folder will not trash your password.

---

### Post by mdwy62 on 2011-04-01
I think the problem I am having is that one machine is running lucid and the other is running meerkat. The .encfs6.xml file create by meerkat has the header:
```
<?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
<!DOCTYPE boost_serialization>
<boost_serialization signature="serialization::archive" version="7">
<config class_id="0" tracking_level="1" version="20" object_id="_0">
	<version>20100713</version>
	<creator>EncFS 1.6</creator>
```

When I use encfs to import this on the lucid machine, I get an error that says something to the effect that while there is a .encfs6.xml file, it cannot be read/decoded or something and it tries to create a new encrypted folder.

If I create an encrypted folder under the lucid machine, the .encfs6.xml header is:
... I don't have it. Apparently u1 needed more than 3 hours to upload the .encfs6.xml file. Anyway I had a look at it and it and the boost serialization version was different.  I gather from other posts that this is the issue, though I haven't found a description of a way to synchronize boot serialization versions.

---

### Post by manosx on 2011-04-04
So it's version incompatibility?

I run new versions of encfs and cryptkeeper and the encrypted dir was created on 12/06/2009 and i have no issues..

The beginning of encfs6.xml is like this 
 
<?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
<!DOCTYPE boost_serialization>
<boost_serialization signature="serialization::archive" **version="5"**>
<config class_id="0" tracking_level="1" **version="20080816"** object_id="_0">
	<**creator>EncFS 1.5**</creator>

---

### Post by lovinglinux on 2011-08-03
Thanks for this tutorial.

EDIT: nevermind, it seems my problem was due to cryptkeeper. I followed the command-line tutorial and things looks normal now.

---

### Post by jmp88 on 2011-08-18
Does anyone have experience with Truecrypt filesystems stored in Ubuntu One? How does ubuntu one figure out when changes have been made and so forth? Is it based on the timestamp or on the actual contents of the file? WIll the entire encrypted 'volume' be uploaded every time one small thing in it changes?

I don't expect to have the encrypted FS mounted on two computers at the same time but I would hope that the data will synchronize correctly so it can be mounted at home and then later at work too. It would also be preferable to not be constantly transferring enormous volumes at once.

---

### Post by fabio.hipolito on 2011-10-16
Hello,

after a very unpleasant upgrade from Ubuntu 11.04 to 11.10, I moved from Ubuntu to Xubuntu and I'm really happy with it, except with a problem with my encrypted folder.

Sometime back (a few years) I followed manosx instructions and created my encryption script. This has served me very well until I changed to Xubuntu, now when I run it I get the following message:
```
nebulosa@strix:~/Documents/Pessoal$ sh mount_pessoal_secure.sh 
EncFS Password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message
Secure backup encrypted partition mounted at
/home/nebulosa/Documents/Pessoal/encrypted
nebulosa@strix:~/Documents/Pessoal$
```

From the message seems clear, that I'm trying to mount in a used point. But, because I know nothing about using fuse and mounting devices I request some help with this.

My script is a slight variation of what manosx proposes, it is written as follows:
```
#!/bin/bash
#this comes from the ubuntu encrypted partition
#make sure that you have created the following folders:
#	/path/to/Pessoal/encrypted/
#	/path/to/Pessoal/Pessoal_secure/
#if not
#	mkdir /path/to/Pessoal/encrypted/
#	mkdir /path/to/Pessoal/Pessoal_secure/
homefolder=~
secfolder=$homefolder"/Documents/Pessoal/Pessoal_secure"
encfolder=$homefolder"/Documents/Pessoal/encrypted"
if [ -d $secfolder ]; then
    if mount | grep "on $secfolder type" > /dev/null; then
        fusermount -u $secfolder
        echo "Secure backup partition unmounted"
        sleep 1
    else
        encfs $encfolder $secfolder
        echo "Secure backup encrypted partition mounted at"
	echo $encfolder
        sleep 1		
        fi
else
    echo "Directory doesn't exist, do: mkdir $secfolder"
    sleep 2
fi
```

---

### Post by manosx on 2012-03-12
this thread is still alive?, ouao!

fabio.hipolito:
Since the problem seems to be that the mountpoint is not empty, this is what you have to change (either empty it or make a new dir)
In the script this is: 
secfolder=$homefolder"/Documents/Pessoal/Pessoal_secure"
that translates to:
~/Documents/Pessoal/Pessoal_secure
To make sure that you haven't mounted it already for something else, you can run:
mountpoint ~/Documents/Pessoal/Pessoal_secure

jmp88:
Since for any online service this is one file, it will be treated as one. Adding a file will result in changing the file and thus, uploading the whole file.. There are technologies that allow to upload only the changes of the file, but i don't know if that would work in a file that is an encrypted volume.

---

### Post by gecka on 2012-03-13
Truecrypt does the job really well.

---

### Post by Holdolin on 2012-03-14
Good stuff here.  I have servers that i keep backed up locally, but would never drop the backups to a cloud for security's sake.  For reasons I don't yet know, it never occurted to me to encrypt it.  Would make me a lot happier having my server backups in both a local and remote location.  Thanks to all who have contributed to this thread :)

---

