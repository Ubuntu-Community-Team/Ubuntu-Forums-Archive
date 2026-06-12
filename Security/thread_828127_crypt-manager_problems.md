---
title: "crypt-manager problems"
date: 2008-06-13
forum: Security
---

### Post by cwfdx on 2008-06-13
I have some personal files in my computer,but people may use my account,so I found "crypt-manager" which can give the folder a password.But when I installed it,there was some problems.I installed it as follow:

[COLOR="RoyalBlue"]sudo addgroup your-login fuse

sudo apt-get install encfs python2.4-dev python-nautilus subversion

svn checkout [http://crypt-manager.googlecode.com/svn/trunk/](http://crypt-manager.googlecode.com/svn/trunk/) crypt-manager

cd crypt-manager[/COLOR]

[COLOR="red"]sudo ./install.sh[/COLOR]



There was something with the red part,when I input it in the termial,it doesn't work and the response was "sudo: crypt-manager/install.sh: command not found"


Can anybody help me? I'm very appreciate it!

or you can tell me another method and how to remove the programme  I've installed,thank you!


the URL:[http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html](http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html)

---

### Post by kevdog on 2008-06-13
Do you read the README in the directory:

[http://crypt-manager.googlecode.com/svn/trunk/README](http://crypt-manager.googlecode.com/svn/trunk/README)

Again the trunk doesnt specifically have an install.sh file but the subdirectories have a setup.py file:

conceal
  * Depends of:
    - Python
    - EncFS

conceal-gtk
  * Depends of:
    - Python
    - GTK
    - PyGTK

nautilus-conceal:
  * Depends of:
    - Python
    - Nautilus
    - Nautilus Python binding

conceal-kde
  * Depends of:
    - Python
    - KDE devel
    - PyQT
    - PyQT tools
    - PyKDE
    - PyKDE extensions
    - libpythonize

To install a component just go into the appropriate directory and type as:
# sudo python setup.py install

---

### Post by cwfdx on 2008-06-13
> **kevdog said:**
> Do you read the README in the directory:

[http://crypt-manager.googlecode.com/svn/trunk/README](http://crypt-manager.googlecode.com/svn/trunk/README)

Again the trunk doesnt specifically have an install.sh file but the subdirectories have a setup.py file:

conceal
  * Depends of:
    - Python
    - EncFS

conceal-gtk
  * Depends of:
    - Python
    - GTK
    - PyGTK

nautilus-conceal:
  * Depends of:
    - Python
    - Nautilus
    - Nautilus Python binding

conceal-kde
  * Depends of:
    - Python
    - KDE devel
    - PyQT
    - PyQT tools
    - PyKDE
    - PyKDE extensions
    - libpythonize

To install a component just go into the appropriate directory and type as:
# sudo python setup.py install

Followed what you told me,I've installed it,but it doesn't work properly.After I encrypted a folder,it can be open as normal,here is the screenshot.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=73980&stc=1&d=1213411942[/IMG]

Thank you for your help,my country is not English-speaking and I have searched a lot information and I really didn't know how to do this.

With your instruction,I installed the setup.py in conceal/conceal nautilus/conceal-gtk,did I do right?Thank you again!

---

### Post by cwfdx on 2008-06-14
It works now,this time when I started my computer,the folder content was empty,and after I unlocked it in Encrypted directories,the content appeared.But when I wanted to lock it again,it didn't work at once.Will it encrypt when I close the computer?I want to know why it doesn't work when I click "close" button.Thank all the readers!

---

### Post by lngndvs on 2008-06-16
I just posted to another thread that appears to be defunct.  I notice that this thread is up to date.

When I installed conceal (crypt-manager?) I have gotten buggy results. After a briefly interesting time last evening, everything has failed today.  I have most recently been getting the following message.  In this case, I started from a terminal; the gui just seems to hang or do nothing.  I am wondering whether one of the dependencies has gotten hosed.
> 
eclectico@moseley:~$ conceal -d enc3
Password:
Unmounting...
Traceback (most recent call last):
  File "/usr/bin/conceal", line 224, in <module>
    Main()
  File "/usr/bin/conceal", line 84, in __init__
    self.decrypt()
  File "/usr/bin/conceal", line 201, in decrypt
    conceal.Manage(folder).decrypt(password)
  File "/usr/lib/python2.5/site-packages/conceal.py", line 428, in decrypt
    self.unmount()
  File "/usr/lib/python2.5/site-packages/conceal.py", line 418, in unmount
    self.encfs.unmount()
  File "/usr/lib/python2.5/site-packages/conceal.py", line 309, in unmount
    subprocess.Popen([FUSERMOUNT, "-z", "-u", self.folder.path])
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1147, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory


Does this ring any bells?  I have been getting this both with ubuntu debs and when I installed (with several hangups) from source.

---

### Post by cwfdx on 2008-06-17
My only question about this software is why didn't it work at once after I clicked the "close" button.And it seems that the crypt manager can't encrypt the folders or files which name is ".*".

---

### Post by lngndvs on 2008-06-17
I am concerned to find a way to open a directory that was encrypted with conceal.  A friend has lost an entire directory of important files.

Alan

---

### Post by cwfdx on 2008-06-17
Oh,it's terrible!I don't want to lose anything,and now I use it to a unimportant folder:)

---

### Post by lngndvs on 2008-06-17
I have found a tentative solution here:

    [http://code.google.com/p/crypt-manager/issues/detail?id=7](http://code.google.com/p/crypt-manager/issues/detail?id=7)

Specifically, in /usr/lib/python2.5/site-packages/conceal.py

  change /usr/bin/fusermount to /bin/fusermount

This is tentatively working, however, I am uncertain it will help recover from previous issues.

---

### Post by cwfdx on 2008-06-20
What should I do when I didn't want to encrypt the dictionary anymore?How can I remove the folder from encrypt manager's list ?

The reason it doesn't work properly maybe that my file system is not for linux,it's FAT32,I should try it on ext3 file system.

But I have learned how to use "chown" and "chmod",and now I think they're enough for my personal files.If you know other better method,share it:)

Paladin

---

### Post by lngndvs on 2008-06-20
I cannot help you with M$ windows issues, or, to be sure, even GNU/Linux filesystems.  I do not know how to remove the folders from your list.  I found some files in the home directory (~/) like .conceal and at least one other, that may contain the encrypted versions of the files.  Perhaps you can copy the files to another directory when the encrypted dir is open, then not worry anymore.  If  you have done this with all encrypted directories, you could delete those files (one of them is called "cache".)

I wasn't able to decrypt, but perhaps if that was working (it might be, but I was not successful the first few times, and now I am frightened to try) it would do something with the encrypted file and put the directory back in order.  At least in a perfect world.  It didn't work for me.

Good luck.  

Alan

---

