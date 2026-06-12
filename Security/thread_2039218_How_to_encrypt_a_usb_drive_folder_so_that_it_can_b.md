---
title: "How to encrypt a usb drive folder so that it can be opened in Windows and GNU/Linux"
date: 2012-08-08
forum: Security
---

### Post by yeehi on 2012-08-08
I would like to keep some important files on a USB Flash drive / pen drive. I want to encrypt their folder in case I lose the USB drive. I might need to be able to open the folder on a windows machine, at an Internet cafe, for example.

What is a good way of locking access to a folder with a password that can later be opened in Windows or GNU/Linux? Would I need to install a program onto the USB drive itself, too?

My best idea at the moment is Truecrypt, but maybe there is something simpler/better. Truecrypt needs admin rights, so that might rule it out at the internet cafe. Maybe free [otfe ]("http://www.freeotfe.org/index.html")explorer is the way to go... I don't know.

Thanks for your help.

---

### Post by tubbygweilo on 2012-08-08
yeehi, Would you feel safe decrypting your much loved files upon a machine where you did not have admin rites? 

Could be made to work using truecrypt with admin rights if say a friend you trust grants you admin rights on their machine be it windows or Ubuntu, but again a level of trust in required.

---

### Post by HeinS5 on 2012-08-08
You can use a program named disk utility.
I suggest that you first delete the present partition on the stick.
After that you can make one, two or a lot partitions.
Some possible solutions for your problem :
- Make one NTFS partition, but encrypted, if you want to have access to the secret files on a windows machine.
- Make two partitions, an unencrypted NTFS partition. For use on a windows computer.
And an encrypted ext4 partition for use on linux machines.

As far as I know apple computers are also able to read/write encrypted ext4 partitions. If the password is available off coarse.
Be aware, older versions of windows like vista are not able to read/write encrypted NTFS partitions.

---

### Post by C.S.Cameron on 2012-08-08
How about 7Zip encrypted archive?

---

### Post by HeinS5 on 2012-08-09
It is possible to maken an encrypted zip archive. But to my experience working with files in this kind of archives is tricky. Tricky in such a way that you need software on the computers in use.
And usually the file list is still visible in encrypted zip files.
For my back-ups I have an encrypted partition on an external harddrive. In linux it works really well. I tried this for a relative of me on a windows computer. And of coarse in windows it is ****.

---

### Post by ottosykora on 2012-08-09
sure you can use truecrypt, but only with admin rights you have the file manager integration.

No admin rights, you can still decrypt all contents and use them anywhere.
It only does not show as extra drive.

In fact when used this way, the truecrypt file behaves pretty much like an encrypted zip file. You have to decrypt all to an empty place and then you can delete the decrypted files again.

The only time truecrypt needs admin rights is when it has to install the drivers to appear as separate drive under windows.

All other operations can be done under restricted user.

BTW it is quite similar with the OTFE, for this there is the so called explorer which will allow you copy single files out of the 'container'.
There used to be similar for truecrypt, but AFAIK it does not work with the current version (was a 3rd party product)

---

### Post by ottosykora on 2012-08-09
> **HeinS5 said:**
> It is possible to maken an encrypted zip archive. But to my experience working with files in this kind of archives is tricky. Tricky in such a way that you need software on the computers in use.
And usually the file list is still visible in encrypted zip files.
For my back-ups I have an encrypted partition on an external harddrive. In linux it works really well. I tried this for a relative of me on a windows computer. And of coarse in windows it is ****.

no, all you need is some portable zip software, many of them around and have it on the same usb media with you.
7zip or what ever will do the job.

---

### Post by C.S.Cameron on 2012-08-09
> **HeinS5 said:**
> 
And usually the file list is still visible in encrypted zip files.


7Zip will also encrypt file names.

---

### Post by HermanAB on 2012-08-15
Here are a couple of guides to do exactly what you want, complete with little Perl wizards to do it for you:
[http://www.aeronetworks.ca/howtos/luks-usb-howto.html](http://www.aeronetworks.ca/howtos/luks-usb-howto.html)
[http://www.aeronetworks.ca/howtos/LUKS-Mount-FreeOTFE.pdf](http://www.aeronetworks.ca/howtos/LUKS-Mount-FreeOTFE.pdf)

---

### Post by rookcifer on 2012-08-16
> **HeinS5 said:**
> You can use a program named disk utility.
I suggest that you first delete the present partition on the stick.
After that you can make one, two or a lot partitions.
Some possible solutions for your problem :
- Make one NTFS partition, but encrypted, if you want to have access to the secret files on a windows machine.
- Make two partitions, an unencrypted NTFS partition. For use on a windows computer.
And an encrypted ext4 partition for use on linux machines.

As far as I know apple computers are also able to read/write encrypted ext4 partitions. If the password is available off coarse.
Be aware, older versions of windows like vista are not able to read/write encrypted NTFS partitions.


No need to do all that.  Linux can read FAT just fine and can read NTFS with a kernel module (which most distros include by default).

I say make one FAT partition and be done with it.  It should work in Linux or Windows.

---

