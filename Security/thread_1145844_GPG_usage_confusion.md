---
title: "GPG usage confusion?"
date: 2009-05-02
forum: Security
---

### Post by dryder on 2009-05-02
Hi,
Ubuntu 8.04

I set up a private key using Ubuntu's Encryption GUI tool. Then I tried encrypting a folder containing jpgs.

What I got was a zip file. When I clicked on it I could see the contents.

What I was hoping for were files (one for each image) that looked like absolute text garbage or some other meaningless files.

I must be missing something here but when I encrypt the folder I don't want to see its contents in their original form nor do I want a zip folder where I can see the contents as normal.

This is for my computer so prying eyes can not determine what they are looking at. Leaving the original data intact defeats the point as does being able to view the contents of the encrypted files, jpgs or confidential business documents.

I don't want to hide the with '.' nor chmod them - that is not encryption and is poor security.

Any ideas please?

David

---

### Post by Vinno on 2009-05-02
gpg -c filename

You might have to zip all the images up though first.

---

### Post by dryder on 2009-05-03
Thanks but the results were the same. I got a filename.zip.pgp file but the original remained.

I really want to alter the original without having to manually delete it so it only exists in pgp form.

David

---

### Post by rileinc on 2009-05-04
I don't think GPG obfuscates the file names. You might be better off creating a Truecrypt container and throw your pictures in it.

---

### Post by hashi856 on 2009-05-04
> **dryder said:**
> Hi,
Ubuntu 8.04

I set up a private key using Ubuntu's Encryption GUI tool. Then I tried encrypting a folder containing jpgs.

What I got was a zip file. When I clicked on it I could see the contents.

What I was hoping for were files (one for each image) that looked like absolute text garbage or some other meaningless files.

I must be missing something here but when I encrypt the folder I don't want to see its contents in their original form nor do I want a zip folder where I can see the contents as normal.

This is for my computer so prying eyes can not determine what they are looking at. Leaving the original data intact defeats the point as does being able to view the contents of the encrypted files, jpgs or confidential business documents.

I don't want to hide the with '.' nor chmod them - that is not encryption and is poor security.

Any ideas please?

David

To be honest I don't know much about the linux encryption possess, how ever I would recommend True Crypt. It's an excellent, free, open source, encryption program, and from the sound of it, will give you exactly what you want.

unless you have some specific reason for not using it.

[truecrypt.org]("http://www.truecrypt.org/")

---

### Post by dryder on 2009-05-04
> You might be better off creating a Truecrypt container and throw your pictures in it.


> unless you have some specific reason for not using it.

Thanks.

I don't have anything against TrueCrypt. I was using the tool that was in Ubuntu. Which, for the life of me, I can't see has any purpose unles i) emailing the .pgp file, or ii) being prepared to manually delete the original - which still leaves it on the disk for possible recovery unless or until it's disk space is eventually overwritten. 

I'll try it - thanks for your replies :-)

David

---

