---
title: "Truecrypt GUI"
date: 2007-02-18
forum: Server Platforms
---

### Post by magisterludi on 2007-02-18
Hi,

Forcefield is a GUI frontend(gnome tray icon) for truecrypt written in pygtk.
I have build a new ubuntu package for feisty.
You can download it [here]("http://bockcay.de/forcefield/wiki")

Install it with:
```

sudo apt-get install python-pexpect
dpkg -i forcefield_0.17-1_all.deb

```

Of course you need to have truecrypt installed.

Hints:
Get source from [http://www.truecrypt.org/downloads.php]("http://www.truecrypt.org/downloads.php")
Extract it.
For >2.6.18 kernels use [this patch]("http://bockcay.de/stuff/programs/patches/Dm-target.c_2.6.18+2.6.19rc2.diff").
For 2.6.20 kernels use [this patch]("http://bockcay.de/stuff/programs/patches/truecrypt4.2a-2.6.20.patch").
```

mv Dm-target.c_2.6.18+2.6.19rc2.diff $SOMEDIR/truecrypt-4.2a/Linux/Kernel
cd $SOMEDIR/truecrypt-4.2a/Linux/Kernel
patch < Dm-target.c_2.6.18+2.6.19rc2.diff
cd ..
./build.sh

```

16.April 2007: truecrypt 4.3 should work fine with the newest 0.17 version of forcefield. 4.3 seems to compile with out hassle against new kernel source ( >2.6.18 )


Please give feedback. 
If someone would help I welcome it.
I want to implement several other features like:

plug and play (like usb stick with no readable data on it, popping up a dialog-IMPLEMENTED). Easy Home partition encryption, etc.

---

### Post by PurplePenguin on 2007-02-18
Great!  I played around with truecrypt a while back, but couldn't find a gui for the life of me.  It's not hard to use on the command line, but still...

I don't use feisty, but I'll definitely download the source and check it out.  Ah, no need... there's an Edgy .deb on [the site]("http://bockcay.de/forcefield")!

---

### Post by likeatim on 2007-02-23
> **PurplePenguin said:**
> I don't use feisty, but I'll definitely download the source and check it out.  Ah, no need... there's an Edgy .deb on [the site]("http://bockcay.de/forcefield")!
it's gone....

---

### Post by Neckbreaker on 2007-02-25
No, its not gone.
They have only moved it.
Here is the link for the edgy version.
[http://bockcay.de/stuff/programs/forcefield/forcefield_0.1-1_i386.deb](http://bockcay.de/stuff/programs/forcefield/forcefield_0.1-1_i386.deb)

---

### Post by mael on 2007-03-02
on feisty (kubuntu) i only get this before it crashes:

Traceback (most recent call last):
  File "/usr/bin/forcefield", line 7, in <module>
    import egg.trayicon
ImportError: No module named egg.trayicon


does it need any special packages besides python-gnome2 python-crypto gconf2 python-pexpect? or does it not run at all under KDE?

---

### Post by gaten on 2007-03-03
I'd really like a dapper .deb of this. Seeing as dapper is long term support, it's going to be around for a while. I'd be willing to help out with the testing, thanks for this.

---

### Post by gb5757870 on 2007-03-03
This is really great but it always seems to mount as root 'cos I need to open the mounted folder as root to view the files.

Would the fact that the TrueCrypt volume is on a NTFS partition be the reason?

---

### Post by Angry penguin on 2007-03-27
I would love to help out with testing on this, but i cant seem to get the program to build and the .deb file doesnt work, i'm in edgy.

When I try ./configure it tells me:

configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."

any ideas?

---

### Post by pesobs on 2007-04-01
> When I try ./configure it tells me:

configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."
Installing the package *automake* should solve this problem.

additionally you should have installed the following packages:
(see section *Build Dependencies* on [http://bockcay.de/forcefield/wiki]("http://bockcay.de/forcefield/wiki"))

autoconf
automake
libgconf2-dev
python-all-dev (>= 2.3.5-11)
python-setuptools (>= 0.6b3-1) 
python-gtk2-dev 
python-gnome2-dev

---

### Post by magisterludi on 2007-04-01
hi,

will fix that in svn.

for now run:
```

aclocal
autoconf
automake --add-missing


```

it might complain about versioning because I used feisty versions

---

### Post by pesobs on 2007-04-02
Hi,

has someone already compiled *forcefield* using Dapper and could write a short *howto* in this thread? I still wasn't successful by compiling it right now.

---

### Post by alaaji on 2007-04-03
Thanks for creating forcefield.  I just installed it using Automatix and it works great!

---

### Post by CyborgMax on 2007-04-07
erm, how do i use forcefield? i have installed it on edgy and typing "forcefield" does not work or start anything.

---

### Post by Angry penguin on 2007-04-08
It gets installed to Applications>Accessories.

---

### Post by Flop on 2007-04-10
Hi All,
The preface: After years and years of using the OS originating from Richmond, I decided it is the time to try something fresh. After few days of research I decided to try the great and mighty Ubuntu and I must say, for a Windows addict I am pleasantly surprised thus far. I’m just sorry I hadn’t tried it earlier. You can ignore said above as this has little do to with the topic, I just wanted to share my appreciation for Linux especially Ubuntu distro.

Nevertheless as my adventure keeps on going I am facing some bumps. Hence I humbly ask for your help and expertise and at the same time I apologize for any questions you may find ignorant.

The case is like this: Back in old Windows I was using TrueCrypt to secure my confidential information. I was thrilled to find out that some wise person created GUI to support TC in Linux. Although the installation went smoothly and the program looks brilliant, I have some trouble using it. To be more precise, I have problems with mounting the volumes. As I am a newbie, I’m bit lost in the dark, so perhaps someone could help me:
In the volume path field :
What info I should provide? Is it the path to the encrypted partition? Does it make any difference if the device already has been mounted? 
The mount directory:
This is the path where I want TC to mount and decrypt my data, correct?

Is there any information if the passwd is incorrect in case I put it wrong?
The problem is that I can’t mount my encrypted partition although I’m pretty sure the pass is correct. It simply does nothing when I put the information above and try to mount the volume

I’d be grateful for any input.
Cheers
Flop

---

### Post by magisterludi on 2007-04-10
Hi flop, forcefield should give you feedback if the password is wrong.

volume path is a partition, harddrive or file, some examples:

Partition
```
/dev/sda1
```
Whole Harddisk
```
/dev/sdb
```
File
```
/home/user/my_encrypted_file
```

mount directory is the directory where you want to mount the volume, examples:

```
/mnt/my_encrypted_point
```
this directory must exist

if you get no feedback, try running forcefield from the command line using the -d option line this:

```
forcefield -d
```

this will give some debugging output, please send me the pasted output and I will look into it.

---

### Post by Flop on 2007-04-11
Thanks a bunch!

Didn't realize the mount directory should exist. Unfortunately I'm away and will not be able to check if that was the problem till Friday but will give you a shout how the whole thing ended.

Thanks again
cheers
Flop

---

### Post by Polygon on 2007-04-12
hey, im trying to  use this program, but every time i tried to create a volume, it would ask me for my root password, id enter it, it would sit there for like 10 seconds and then the password box would dissapear and then the progress window would appear and just sit there at 0%,, even after like 5 minutes

so i ran it from the terminal and this is what i got:

> 
mark@ubuntu:~$ forcefield 
Attached schema `/schemas/apps/forcefield' to key `/apps/forcefield/command'
Installed schema `/schemas/apps/forcefield' for locale `C'
Attached schema `/schemas/apps/forcefield/dev_history' to key `/apps/forcefield/dev_history'
Installed schema `/schemas/apps/forcefield/dev_history' for locale `C'
Attached schema `/schemas/apps/forcefield/mount_history' to key `/apps/forcefield/mount_history'
Installed schema `/schemas/apps/forcefield/mount_history' for locale `C'
Attached schema `/schemas/apps/forcefield/suppressSuidWarning' to key `/apps/forcefield/suppressSuidWarning'
Installed schema `/schemas/apps/forcefield/suppressSuidWarning' for locale `C'
Attached schema `/schemas/apps/forcefield/cache_history' to key `/apps/forcefield/cache_history'
Installed schema `/schemas/apps/forcefield/cache_history' for locale `C'

hello
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/forcefield/create_volume.py", line 256, in handle_create
    pwp.enterSudoPassword(sudoPassword)
  File "/usr/lib/python2.4/site-packages/forcefield/texpect.py", line 173, in enterSudoPassword
    answer = self.tc.expect([truecryptResponse.SUDO_ENTER_PASSWORD, pexpect.EOF])
  File "/usr/lib/python2.4/site-packages/pexpect.py", line 1064, in expect
    return self.expect_list(compiled_pattern_list, timeout, searchwindowsize)
  File "/usr/lib/python2.4/site-packages/pexpect.py", line 1143, in expect_list
    raise TIMEOUT (str(e) + '\n' + str(self))
pexpect.TIMEOUT: Timeout exceeded in read_nonblocking().
<pexpect.spawn object at 0xb6ea87ec>
version: 2.1 ($Revision: 395 $)
command: /usr/bin/sudo
args: ['/usr/bin/sudo', 'truecrypt', '--size', '1M', '--encryption', 'AES', '--hash', 'RIPEMD-160', '--type', 'normal', '--filesystem', 'FAT', '-c', '/home/mark/albums/test']
patterns:
    Password:
    pexpect.EOF
buffer (last 100 chars): 
before (last 100 chars): 
after: pexpect.TIMEOUT
match: None
match_index: None
exitstatus: None
flag_eof: False
pid: 4279
child_fd: 16
closed: False
timeout: 30
delimiter: pexpect.EOF
logfile: <open file '/tmp/pexpect.log', mode 'w' at 0xb6e9b3c8>
maxread: 2000
ignorecase: False
searchwindowsize: None
delaybeforesend: 0.1
delayafterclose: 0.1
delayafterterminate: 0.1




any suggestions?

---

### Post by charlieMOGUL on 2007-04-12
I'm not familiar with that problem, but maybe installing TrueCrypt with the option to run the program as non-root user would help ? That way, you don't have to enter the root password but only the TrueCrypt password.

Hope this helps,

charlieMOGUL

---

### Post by Flop on 2007-04-13
Hi,
Back again. Still the same problem – can not mount encrypted partition. I tried to create the mount directory first and it didn't help. Following your advice, I'm posting the  output after running 
forcefield -d:

> hello
auto
3
3
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/forcefield/mountfile.py", line 300, in handle_mount_clicked
    self.wmount_directory.get_active_text(), self.protect_hidden)
  File "/usr/lib/python2.4/site-packages/forcefield/texpect.py", line 52, in mount
    return self.mountInteractive( volume, mountDir, protected, keyfiles, password)
  File "/usr/lib/python2.4/site-packages/forcefield/texpect.py", line 57, in mountInteractive
    self.tc.expect(truecryptResponse.ENTER_MOUNTPATH)  
  File "/usr/lib/python2.4/site-packages/pexpect.py", line 1064, in expect
    return self.expect_list(compiled_pattern_list, timeout, searchwindowsize)
  File "/usr/lib/python2.4/site-packages/pexpect.py", line 1143, in expect_list
    raise TIMEOUT (str(e) + '\n' + str(self))
pexpect.TIMEOUT: Timeout exceeded in read_nonblocking().
<pexpect.spawn object at 0xb6dc148c>
version: 2.1 ($Revision: 395 $)
command: /usr/bin/truecrypt
args: ['/usr/bin/truecrypt', '-i']
patterns:
    Enter mount point.*
buffer (last 100 chars): 
before (last 100 chars): Enter volume path: /dev/hdb1
Enter mount directory [none]: 
after: pexpect.TIMEOUT
match: None
match_index: None
exitstatus: None
flag_eof: False
pid: 5664
child_fd: 14
closed: False
timeout: 30
delimiter: pexpect.EOF
logfile: <open file '/tmp/pexpect.log', mode 'w' at 0xb6db4380>
maxread: 2000
ignorecase: False
searchwindowsize: None
delaybeforesend: 0.1
delayafterclose: 0.1
delayafterterminate: 0.1

Does it make a difference that the partition I am trying to mount was encrypted under Windows and has primary NTFS file system (FAT32 after decryption)?
Would be grateful for any hints.
Thanks,
Flop

---

### Post by magisterludi on 2007-04-14
Hi Flop and Polygon,

you seem to be edgy users judging from the output. The edgy deb is outdated and many of the (sudo) bugs described above are fixed in the feisty deb and the svn source. The texpect backend was totally rewritten. I think the feisty package won't work for you since the trayapp calls used aren't in the egg library but in gnome library now which only exists in feisty. But you can give the feisty package a try anway. I'm sorry, I have no edgy build environment anymore. If anyone got one patching and then building a deb for edgy from the svn source would be very much appreciated.

---

### Post by Polygon on 2007-04-15
> **magisterludi said:**
> Hi Flop and Polygon,

you seem to be edgy users judging from the output. The edgy deb is outdated and many of the (sudo) bugs described above are fixed in the feisty deb and the svn source. The texpect backend was totally rewritten. I think the feisty package won't work for you since the trayapp calls used aren't in the egg library but in gnome library now which only exists in feisty. But you can give the feisty package a try anway. I'm sorry, I have no edgy build environment anymore. If anyone got one patching and then building a deb for edgy from the svn source would be very much appreciated.

oh ok. That makes sense. I can compile it fine (i tried compling when i got that bug), but can i just use checkinstall to produce the deb? or do it the offical way?

---

### Post by Flop on 2007-04-15
Hi again,
so I've updated my edgy to feisty but I'm still facing problems. When mounting volume everything seamed working fine until I got the following "unknown exit code". Launching forcefield from the terminal with -d doesn't help much as it stops at 
> forcefield -d
No volumes mapped
Enter volume path: /dev/hdd5
/dev/hdd5
Enter mount directory [none]: 


Any guess what might be the problem? 
Thanx.
Flop

---

### Post by magisterludi on 2007-04-16
I think you are using truecrypt 4.3 which has another string for asking the mount directory

```
"Enter mount point"
```

was changed to:

```
"Enter mount directory"
```

forcefield uses pexpect to parse and react to the truecrypt commandline since there is no truecrypt api at the present.

I did fix this but didn't upload the fixed deb, so [now here is the fixed version.]("http://bockcay.de/stuff/programs/forcefield/forcefield_0.17-1_all.deb")

Sorry for that.

---

### Post by Flop on 2007-04-28
Hi,
It's been a while but I've finally managed to get  forcefield up and running, many thanks for your help.  Other issue has arisen though - How do I mount the encrypted partition to be writable? 

I did change the file where the decrypted partition is mounted to be writable but as soon I mount the content it gets back to not writable.
Please advise 
Thanks
Flop

---

### Post by rmfought on 2007-05-01
Hi,

I'm trying to use forcefield to create and mount an entire USB hard disk truecrypt volume, but I must be thickheaded.

When I create the volume, I select "/dev/" as the location, "sdb" as the file name, and I have tried both "FAT" and "none" as the filesystem type (the only two choices) - and the volume appears to be created successfully.  But when I try to mount the volume using forcefield, I get the following error from forcefield:

mount: wrong fs type, bad option, bad superblock on /dev/mapper/truecrypt0,
       missing codepage or other error

and messages such as follows from dmesg:

[187095.538143] VFS: Can't find ext3 filesystem on dev dm-0.
[187095.539818] FAT: invalid media value (0xb1)
[187095.539823] VFS: Can't find a valid FAT filesystem on dev dm-0.
[187095.541699] NTFS-fs warning (device dm-0): is_boot_sector_ntfs(): Invalid boot sector checksum.
[187095.541706] NTFS-fs error (device dm-0): read_ntfs_boot_sector(): Primary boot sector is invalid.
[187095.541710] NTFS-fs error (device dm-0): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[187095.541714] NTFS-fs error (device dm-0): ntfs_fill_super(): Not an NTFS volume.
[187095.613821] UDF-fs: No VRS found
[187095.657131] Unable to identify CD-ROM format.
[187095.658549] VFS: Can't find an ext2 filesystem on dev dm-0.

What am I doing wrong here?

Update:  I got truecrypt working with the command line, and it is pretty straightforward so I'm sticking with that.

---

### Post by Mack1 on 2007-05-03
Hi!

!st of all i'm loving the idea that finally someone took it upon him/her
to get a working gui for truecrypt. truecrypt is heaven!

However, i hear all these great things about forcefield but i cannot get it to start.

When i enter 'forcefield' in the console it exactly does......nothing :confused: 

Can someone help me with what i am doing wrong?

Hopefully yes.....

Keep up the good work!

---

### Post by dustigroove on 2007-05-05
[COLOR=Black]Have been using [SD4L]("http://www.scramdisklinux.org/") previously with success, will take a look at Forcefield.
[/COLOR]

---

### Post by WishMaster on 2007-05-07
the commandline of truecrypt works for me, but:
- I have to ***guess*** which volume it is in /dev  (using usb-stick or external harddrive)
- I first have to create a(n extra) mountpoint in /mnt

Forcefield doesn't work at all :-?
- It doesn't give a list of devices
- I still have to type and guess which volume it is (by looking in /dev )
- When I click "mount", nothing happens

---

### Post by Mack1 on 2007-05-07
Is there anyone who can answer my question as to get forcefield to start?

Just typing forcefield in the konsole after install does nothing, not even a message
on the screen as to what went wrong :(

---

### Post by WishMaster on 2007-05-08
try "sudo forcefield"

---

### Post by Mack1 on 2007-05-08
funny....i could've sworn i'd tried that before asking here......
i'm fealing dumb :( 

Thx for the help, i really appreciate it!

---

### Post by Neo@NHNG on 2007-07-27
Hi I just downloaded Truecrypt and Forcefield via .deb-packages but it doesn't seem to work. (I'm using Feisty on x86)
[edit]reinstalled via Automatix, now it works [/edit]

Here's what I got:```
Neo@NHNG:~$ forcefield -d
/usr/lib/python2.5/site-packages/forcefield/texpect.py:6: RuntimeWarning: Python C API version mismatch for module zero_out: This Python has API version 1013, module zero_out has version 1012.
  import zero_out
Password:xxxxx

No volumes mapped
Traceback (most recent call last):
  File "/usr/bin/forcefield", line 404, in <module>
    hwg = TApplet(debug)
  File "/usr/bin/forcefield", line 178, in __init__
    mounted= self.mountedVolumes()
  File "/usr/bin/forcefield", line 355, in mountedVolumes
    result = TApplet.volumes_obj.refresh()
  File "/usr/lib/python2.5/site-packages/forcefield/volumes.py", line 71, in refresh
    volume_to_mountpoint = mtpython.FileSystemInfo(mounted_only=1).get_fuzzy(spec='/dev/mapper/truecrypt')
  File "/usr/lib/python2.5/site-packages/forcefield/mtpython.py", line 29, in __init__
    self.refresh()
  File "/usr/lib/python2.5/site-packages/forcefield/mtpython.py", line 41, in refresh
    device, txt1, mount_point, txt2, filesystem, options = parts
ValueError: too many values to unpack

```What I see is the following:
A password box in which I typed my password (which is replaced by xxxxx in the code above) and dialogue box behind it which is about using a truecrypt group with root privileges to avoid being asked for your password everytime. When I click OK in the password box it crashes.
Afterwards I tried again, but now I don't even get to that point, all I see is a dialogue box which disappears before I can hardly see it and I get the following output:```
Neo@NHNG:~$ forcefield -d
/usr/lib/python2.5/site-packages/forcefield/texpect.py:6: RuntimeWarning: Python C API version mismatch for module zero_out: This Python has API version 1013, module zero_out has version 1012.
  import zero_out
No volumes mapped
Traceback (most recent call last):
  File "/usr/bin/forcefield", line 404, in <module>
    hwg = TApplet(debug)
  File "/usr/bin/forcefield", line 178, in __init__
    mounted= self.mountedVolumes()
  File "/usr/bin/forcefield", line 355, in mountedVolumes
    result = TApplet.volumes_obj.refresh()
  File "/usr/lib/python2.5/site-packages/forcefield/volumes.py", line 71, in refresh
    volume_to_mountpoint = mtpython.FileSystemInfo(mounted_only=1).get_fuzzy(spec='/dev/mapper/truecrypt')
  File "/usr/lib/python2.5/site-packages/forcefield/mtpython.py", line 29, in __init__
    self.refresh()
  File "/usr/lib/python2.5/site-packages/forcefield/mtpython.py", line 41, in refresh
    device, txt1, mount_point, txt2, filesystem, options = parts
ValueError: too many values to unpack

```

[edit]reinstalled via Automatix, now it works [/edit]

---

### Post by NewLamer on 2007-07-28
Hi, I've been using Ubuntu Feisty 7.04 i386 for several days. I have installed truecrypt and forcefield through Automatix and i have the following two problems:

1.To start forcefield I write sudo forcefield -d in terminal window. The application starts and I start creating a new volume. I input all the necessary data and click "Create". The window for random mouse movement capture appears and i make the neccesasery movements. At the same time, the progress of capturing is also visible in the terminal window. When i reaches 100% nothing happens, neither in the GUI, nor in the terminal. The file that should be created appears in the file browser, but with 0 bytes size. In the terminal the cursor goes to a blank line and nothing more happens. Where is the problem? The same task is performed without problems through the command-line truecrypt (but I don't like it as it is much slower to write all the commands and options)
2.I have some volumes created by truecrypt 4.2 for Windows, which are with NTFS and FAT file systems. They are written as HIDDEN files on DVD-R disks. When i try to mount them, the file browser says that the DVD-R disk could not be mounted (the error it shows is "invalid mount option"). I have enabled showing of hidden files but that is of no help. Trying to mount the volumes is impossible with forcefield or command-line truecrypt either, as they cannot be found. Any idea? As on Windows i used to encrypt >90% of my data and now it is unusable, I am going to give up Ubuntu if i cannot solve this problem.

---

### Post by NewLamer on 2007-07-29
After I burned an encrypted by command line truecrypt volume of 4.38 GB on a DVD-R, and after spending a lot of time just to find out that only Nero for Linux could burn files larger that 4 GB, the file browser returns the same mistake and cannot mount the DVD-ROM. It seems to me that the problem in point 2 in neither in truecrypt, nor in the Filesystem, but rather somewhere in the Linux OS or some hardware standards implemented in it, that cannot recognize files larger than 4 GB on an optical media. Is that really the problem and how can that be overcome?

Also, could anyone tell me how can I allow a user different from the root to write files on a mounted encryupted volume? Truecrypt allows only the root to do that, and when I log in as a root and try to give permissions to the root group (the other user needed to write is added to that group), it says says that it could neither change the group nor the permissions.

---

### Post by Palmyra on 2007-09-03
Could someone post a thorough Forcefield guide?  It's not available on the Forcefield website either, which is located here:

[http://bockcay.de/forcefield/wiki](http://bockcay.de/forcefield/wiki)

---

### Post by pcecconi on 2007-11-21
> **gb5757870 said:**
> This is really great but it always seems to mount as root 'cos I need to open the mounted folder as root to view the files.

Would the fact that the TrueCrypt volume is on a NTFS partition be the reason?

you have to mount using the -u option, like this:

> truecrypt -u /asdf/asdf /media/asdf

---

