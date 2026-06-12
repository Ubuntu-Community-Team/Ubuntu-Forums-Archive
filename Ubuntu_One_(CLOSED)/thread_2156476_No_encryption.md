---
title: "No encryption?"
date: 2013-06-21
forum: Ubuntu One (CLOSED)
---

### Post by Absolute Terror on 2013-06-21
I want to use Ubuntu One to store my contacts. Other than that, nothing personal.

If there's no encryption in my contacts list then what does that mean for the safety and privacy of my contacts?

---

### Post by Cheesehead on 2013-06-23
What do you want it to mean?
Ubuntu One promises convenience, not guaranteed security.

You could rephrase your question as "I upload my data to a shared server someplace on the internet that I do not own nor control. I rely on somebody else's promise of data storage safety and privacy."  That answers your direct question.

Is your list of contacts valuable to you...and nobody else?
If so, then proper backup is important. Encryption has little benefit.

Is your list of contacts valuable to anyone else?
If so, then encryption (including proper key management) and proper secure backup are important. A server you do not fully control is obviously inappropriate for secure backup.

---

### Post by ragtag on 2013-06-24
You can always use encfs with Ubuntu One, just make sure you mount encfs outside Ubuntu One.

---

### Post by GrimJa on 2013-06-26
My humble opinion is, that in light of recent revelations surrounding the NSA the ubuntu team could reasonably consider encryption for use with this service.

I myself will be looking into ragtag's suggestion.

---

### Post by ragtag on 2013-09-24
It's really simple to do. First install encfs

```
sudo apt-get install encfs
```

Create an empty folder where you want to mount your encrypted files.

```
mkdir -p ~/MySecretFiles
```

Create an encfs encrypted disk in the Ubuntu One folder and mount it (giving it a name starting with a dot makes it invisible so it doesn't display in the file browser...not for security reasons).

```
cd ~/Ubuntu\ One
encfs ~/Ubuntu\ One/.MySecretFiles ~/MySecretFiles
```

If you now create or copy files to ~/MySecretFiles/ they will be encrypted in Ubuntu One/.MySecretFiles, and you'll see messages about Ubuntu One uploading strange files like fhBPbcQvx79w39j1U2KKwhrC

To unmount it simply run:

```
fusermount -u ~/MySecretFiles
```

The ~ is shorthand for /home/YOU, and you can of course name your encfs volume anything you want other than MySecretFiles.

I've made a simple script for mounting and unmounting, saving me to remember all these commands. It looks like this:

```
#!/bin/sh
if [ -f /home/ragtag/Projects/.mounted ]
then
    fusermount -u /home/ragtag/Projects
else
    encfs /home/ragtag/Ubuntu\ One/.projects /home/ragnar/Projects
fi
```

Call it something you like and make it executable "chmod a+x scripname", and copy it to /usr/local/bin. That way it will be in path. Then mount it, and add an empty file to your share called .mounted

It's a simple hack the script uses to detect if it should unmount or mount your encfs disk (yes there is probably a better and more proper way to do this, but it works). :)

---

