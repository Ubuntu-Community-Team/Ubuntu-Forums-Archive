---
title: "Making Ubuntu Desktop More Private"
date: 2009-04-18
forum: Security
---

### Post by nowhere@cox.net on 2009-04-18
Using gnome and nautilus to navigate and manage the files on your system generates a number of privacy leaks that others with read access to your home folder can use to learn a lot about your activities. If you have changed the default read permissions on your home folder to no access for others, the root user can still look in your home folder. Also, booting the machine from a LiveCD or USBdrive and mounting your hard drive gives anyone with the desire root access to you folders.

Even if you have the sense to use an encrypted folder, the contents of which even a root user cannot see,  there are still other risks for someone to learn things about the nature of your system use.

Some examples:
[LIST]
[*]If you work on sensitive documents/information in pdf format, then the thumbnails could give hints of the contents of the files. They also show the nature of all the pictures and videos at which you may have just pointed nautilus and not even opened.
[*]A list of the recent videos played is stored in a text file in your home folder.
[*]A list of recently accessed documents is stored in a text file in your home folder.
[*]Your web surfing history, complete with cached images is stored in a folder in your home folder.
[/LIST]

To plug up these leaks you can take some very simple actions. First create an encrypted folder to store your sensitive information. Although there are other ways, the simplest and most convenient method is to use ecryptfs built into the latest ubuntu kernels. Please search for a howto for your version of ubuntu if you don't have it already.
A shortcoming as of 8.10 is that the names of files inside your encrypted folder are still visible to someone peeking in, though the contents are still encrypted.  This is scheduled to change with 9.04.

Here is a list of hole you can plug up by moving the config/log files/folders and using simple symbolic links```
mv ~/.some_sensitive_file ~/Private/.some_sensitive_file
ln -s ~/Private/.some_sensitive_file ~/.some_sensitive_file
```
Do this to the following files/folders:
[LIST]
[*].thumbnails
[*].recently-used - Lists recently accessed docs in OpenOffice
[*].recently-used.xbel - Lists recently accessed documents on the Places Menu
[*].mozilla - Stores surfing history and image caches
[*].mozilla-thunderbird - email and calendar data
[*].evolution - email and calendar data
[*].gtk-bookmarks - lists bookmarked computer systems you've connected to if you saved a bookmark
[*].xine - folder has a file with recently viewed videos if you use xine
[/LIST]

Obviously, any data files or pictures can be placed inside the Private folder but this how to is focused on highlighting those hidden privacy leaks that most users don't know about.

Experts please feel free to add others I have missed and I will keep this top post up to date.

Happy Hunting!

---

### Post by bodhi.zazen on 2009-04-18
root is all powerful. I know of only 3 ways to restrict root :

In your case , encryption is the way to go.

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

You can also restrict root with selinux and apparmor, but those 2 tools are not the best for your case.

You can probably also do this with acl as well.

---

### Post by nowhere@cox.net on 2009-04-19
Thanks bodhi,

I had your howto already bookmarked. I do have a question. Did the commands change between 8.10 and 9.04 really change?

8.10```
sudo apt-get install ecryptfs-util
```
9.04```
sudo apt-get install Ecryptfs-utilizes
```

8.10```
ecryptfs-setup-private
```
9.04```
Ecryptfs-setup-private
```

Thanks!

---

### Post by bodhi.zazen on 2009-04-19
No, they did not. I updated the page, thanks.

---

### Post by nowhere@cox.net on 2009-04-21
No problem. Very nice page and very complete info. One feature suggestion if you have the time and inclination is maybe add a section on how to use ecryptfs to encrypt and entire drive/partition...

Once again, very nicely done!

---

### Post by Kobalt on 2009-04-22
> **nowhere@cox.net said:**
> No problem. Very nice page and very complete info. One feature suggestion if you have the time and inclination is maybe add a section on how to use ecryptfs to encrypt and entire drive/partition...

Once again, very nicely done!

That's actually done very easily during the install process (using an Alternate CD, I don't know about the Live CD procedure) : select "encrypted LVM" in the file-system type for your partition.

---

### Post by tubbygweilo on 2009-04-22
Nowhere,
A few more thoughts about the Private directory as how to use it as provided via [Community EncryptedPrivateDirectory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") might be of use to you.

---

