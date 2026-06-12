---
title: "CryptKeeper and encfs"
date: 2010-02-24
forum: Security
---

### Post by hamamelis on 2010-02-24
I could not find details of what CryptKeeper was doing and I worked this out. It shows how to open and close CryptKeeper files using encfs form the command line. I hope this helps others.
Ubuntu karmic 9.10. CryptKeeper 0.9.4-1 encfs 0.5.2-1ubuntu1   also works in Mint8. Tom Morton author of CryptKeeper site: [http://tom.noflag.org.uk/cryptkeeper.html](http://tom.noflag.org.uk/cryptkeeper.html) 

How Gnome Cryptkeeper works with encfs 

In CryptKeeper create a new encrypted folder:
/home/ian/aaaaaaxxxxTestCryptKeeper   give is a password (I used "password" for this test.)

The directory above is created and also another hidden one called: /home/ian/.aaaaaaxxxxTestCryptKeeper_encfs which contains one hidden file called .encfs6.xml.  As you create additional folder and files in the /home/ian/aaaaaaxxxxTestCryptKeeper additional folders and files with encrypted names are created in /home/ian/aaaaaaxxxxTestCryptKeeper 4L9KBI4IeoAKOoZ,IwzVyn2VPGysXt-JCbStUej5Ewnn90. These mirror any files and folders which you create in the encrypted directory except that there names and contents are totally encrypted.

The above CryptKeeper directory can be created anywhere within the Linux file system, for example, on another partition. In each case two directories are created within the parent (in this example /home/ian/), one with the original directory name, the other preceeded with a "." and followed by "_encfs".

*** How to open a directory created with CryptKeeper using encfs. ***
Provided you copy the directory like .aaaaaaxxxxTestCryptKeeper_encfs and all its contents, it can be opened anywhere using the following command. (Note that full path names are needed.)

encfs /home/ian/.aaaaaaxxxxTestCryptKeeper_encfs /home/ian/aaaaaaxxxxTestCryptKeeper
The mount command will then show:
encfs on /home/ian/aaaaaaxxxxTestCryptKeeper type fuse.encfs (rw,nosuid,nodev,default_permissions,user=ian)
(NB If /home/ian/aaaaaaxxxxTestCryptKeeper does not exist you will be asked, answer yes. If /home/ian/.aaaaaaxxxxTestCryptKeeper_encfs does not exist you will asked if you wish to create it and you will be asked for a password twice. In this case it will not be in CryptKeeper unless you then import it.) 

If it is a CryptKeeper file then it appears in CryptKeeper file list as opened and can be closed from there. To close from the command line type:
fusermount -u /home/ian/aaaaaaxxxxTestCryptKeeper.
Note unmount will not work for these files.

---

### Post by badSheep8 on 2010-03-24
Thanks, exactly what I was looking for!

**encfs /home/ian/.aaaaaaxxxxTestCryptKeeper_encfs /home/ian/aaaaaaxxxxTestCryptKeeper**

**fusermount -u /home/ian/aaaaaaxxxxTestCryptKeeper**


(Not related: why does this site use [http://yui.yahooapis.com/](http://yui.yahooapis.com/) :???:)

---

