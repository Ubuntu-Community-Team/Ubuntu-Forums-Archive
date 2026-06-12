---
title: "how to mount a network harddisk"
date: 2009-01-05
forum: Server Platforms
---

### Post by brallan on 2009-01-05
SOLVED: Please have a look at this [guide to mounting a remote network drive using smbmount]("http://ubuntuforums.org/showthread.php?t=1032394")
********************************************************
Just bought a nifty Conceptronic CHD3NET "Grab'n'Go" Network Harddrive, which is a tiny linux-run case into which you install a SATA 3.5" drive. 

It works as a USB external drive, as well as a 10/100 network drive. Though the drive must be FAT32 (?) for the box to read it, it comes with both Samba and FTP servers, both of which I can get to work for file transfers. 

But I would like to mount this drive on my local filesystem (in order to do backups using grsync). I cannot find a good guide to mounting such a disk onto a local mount point, like /mnt/networkdisk/. Can anyone help?

---

### Post by eldaria on 2009-01-05
You can mount a samba drive by using smbmount

---

### Post by deltaromeo on 2009-01-05
I do this:

sudo mount -t cifs -o user=[username] //[servername]/[sharename] /media/mydisk

replace the three [] entries with your username, servername (or IP) and samba share name

---

### Post by brallan on 2009-01-05
> **deltaromeo said:**
> I do this:

sudo mount -t cifs -o user=[username] //[servername]/[sharename] /media/mydisk

replace the three [] entries with your username, servername (or IP) and samba share name

Thanks Deltaromeo for your response!

It's just a generic drive with an admin login and its at 10.35.230.103. Usually i connect to the server using nothing more than this info (please excuse the Catalan language):

[IMG]http://www.canmasdeu.net/brian/Captura-Connecta%27t%20al%20servidor.png[/IMG]

which takes me to:

[IMG]http://www.canmasdeu.net/brian/Captura-Recursos%20compartits%20de%20Windows%20a%2010.35.230.103%20-%20Navegador%20de%20fitxers.png[/IMG]

OK, I am trying:
# mount -t cifs -o user=admin //mediateca/PUBLIC /mnt/mediateca

and it gives me this error:
mount error 20 = Not a directory

hmmmm. any ideas?

---

### Post by koenn on 2009-01-05
does the directory /mnt/mediateca exist ?

---

### Post by brallan on 2009-01-05
> **koenn said:**
> does the directory /mnt/mediateca exist ?

yes, it does, and ownership should not be an issue, as I am trying to mount as root.

```
$ ls /mnt
disk1  disk2  mediateca
```

any other ideas?

---

### Post by brallan on 2009-01-05
found an answer!

looking at [this thread]("http://www.linuxquestions.org/questions/linux-networking-3/mount.cifs-mount-error-20-not-a-directory-443693/") gave me the following command:

```
sudo echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled

```

I have no idea what that command does, but now I can get it to mount! but on reboot, of course, i have to run the command again, and adding the following entry to my fstab, 

//10.35.230.103/public /mnt/mediateca smbfs rw,userid=admin,passwd=admin,exec 0 0

then i can mount it using sudo mount -a

now the only problem is the awful FAT32 file system, which means doing backups from rsync is giving me endless errors on any non-english characters in the filenames. if I'd known that the stupid disk was going to require me to format a 1000G drive as FAT32, I wouldn't have bought it....

---

