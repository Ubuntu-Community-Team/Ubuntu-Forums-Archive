---
title: "efs baypass"
date: 2008-04-22
forum: Security
---

### Post by mentes on 2008-04-22
Hi,

I recently format my c drive on my laptop and install ubuntu 7.04 but I forget to get the encryption key backup on windows:confused:. I can see my encrypted files on the other hdd but I can not access them I tried lots of staff to save my files but I did not success. I found out that if I can move the files to fat file system or if I convert file system to fat efs can be removed but I do not know how can I do it. Does anybody know how can I move encrypted files to fat file system? or convert file system to fat without lost my data?

Thanks for your time

---

### Post by Monicker on 2008-04-23
> **mentes said:**
> Hi,

I recently format my c drive on my laptop and install ubuntu 7.04 but I forget to get the encryption key backup on windows:confused:. I can see my encrypted files on the other hdd but I can not access them I tried lots of staff to save my files but I did not success. I found out that if I can move the files to fat file system or if I convert file system to fat efs can be removed but I do not know how can I do it. Does anybody know how can I move encrypted files to fat file system? or convert file system to fat without lost my data?

Thanks for your time


Do you have a usb port and a usb flash drive?  Flash drives are usually formatted as fat32, so you could try copying the files to one.

---

### Post by /etc/init.d/ on 2008-04-23
> **mentes said:**
> I can see my encrypted files on the other hdd but I can not access them
That's sort of the point of encryption.

> **mentes said:**
> I found out that if I can move the files to fat file system or if I convert file system to fat efs can be removed
You need the decryption key to be able to do this.  Otherwise, you will simply copy an encrypted file.

> **mentes said:**
> but I forget to get the encryption key backup on windows
This was your mistake.

---

### Post by mentes on 2008-04-25
the thing is I have usb hdd but I couldn't move the files when I try to move them it's says "Error Access denied while copying filename" do you have any idea about how to save my files
thanks for your reply

---

### Post by Monicker on 2008-04-26
I did a little digging around.  You are probably SOL.

[http://en.wikipedia.org/wiki/Encrypting_File_System#Recovery]("http://en.wikipedia.org/wiki/Encrypting_File_System#Recovery")

---

### Post by mentes on 2008-04-26
do you know how to regenerate efs key using encrypted files. because I know the password but I dont have the key

---

### Post by Monicker on 2008-04-26
AFAIK, that is not possible.

---

### Post by mentes on 2008-04-26
do you know how to convert file system ntfs to fat without loosing data?

---

### Post by hggdh on 2008-04-28
> I have usb hdd but I couldn't move the files when I try to move them it's says "Error Access denied while copying filename"

Huh. You have not provided much detail (only your interpretation), but it sounds like you can see the files on a NTFS USB disk, you just cannot access them.

If this is the case, its probably a result of the mount not giving you this access.

Easiest way, then, would be to 'sudo cp' the files you need in:

mkdir temp && cd temp
sudo cp /media/usbdisk/where/ever/this/are .
sudo chown <myself> *

where <myself> is your logged-in id.

And go from there.

---

### Post by /etc/init.d/ on 2008-05-06
> **mentes said:**
> do you know how to convert file system ntfs to fat without loosing data?
If you do this, you will lose the encrypted data.

---

