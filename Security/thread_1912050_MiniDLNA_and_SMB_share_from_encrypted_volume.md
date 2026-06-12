---
title: "MiniDLNA and SMB share from encrypted volume"
date: 2012-01-19
forum: Security
---

### Post by murder_face on 2012-01-19
I currently have a laptop set up to stream video to my Sony SMPN100 and my Wii.  I use MiniDLNA to stream to the sony box and samba to stream to my Wii.  I would like to transfer most of my stuff to an enycrypted volume and can't seem to find any information on if I can stream from an encrypted volume.  I have already tried google and no matter how I word the question I only get stuff about DVDs and their encryption.  Any help or a kick in the right direction would be greatly appreciated.  Thank you.

---

### Post by cariboo on 2012-01-20
Any of the encryption packages will do what you want, but you'll have to decrypt the directory when you want to watch any media.

---

### Post by murder_face on 2012-01-20
What about writing a script or small program to decrypt the file as it is requested?  The only problem I see is getting the initial list of files.

---

### Post by cariboo on 2012-01-20
You usually need a pass-phrase to decrypt a directory, by creating a script with that pass-phrase in it, you are essentially defeating the purpose of encrypting the directory, as all someone would have to do is read the script you created to have access to your media directory.

---

### Post by murder_face on 2012-01-21
I understand that part.  My main concern is being able to unplug the drive and have everything remain encrypted.  I guess I could just encrypt the rest of the directories on the drive and leave the ones with media alone. Or possibly use some kind MAC filter.  That one actually just came to me so I am going to look it up right now.  I'm pretty sure that coming up with some kind of secure option on the Wii wont be a problem, it's the Sony box that I wonder about.

---

### Post by cariboo on 2012-01-21
If you remove you external drive safely, it should automagically be encrypted on removal.

---

