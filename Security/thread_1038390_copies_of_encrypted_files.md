---
title: "copies of encrypted files"
date: 2009-01-12
forum: Security
---

### Post by grimey44 on 2009-01-12
i was wondering if there is a way to encrypt a file without it making a copy the encrypted one? 
id like to encrpyt the actual file so i dont have to delete the original.

---

### Post by teddks on 2009-01-12
If the data is already written to disk, then you **need** to wipe the original plaintext copy for the encryption to have any effect. If the file is just a text file, you could copy the text, encrypt it with the  Seahorse applet, and then paste it back into the file and save, but even after that you should run sfill to make sure traces of the original plaintext are destroyed.

The best thing to do is to use the encrypted ~/Private folder in 8.10 or use full-disk encryption.

---

### Post by grimey44 on 2009-01-13
alright thanx
im not to familiar with encryption. im reading up on it.
so i would just put the files in the private folder and it encrypts them? and theres no original traces?

and how does whole disk encryption work? i assume that encrypts the whole hard drive and then i unlock it all at once?

---

### Post by tubbygweilo on 2009-01-14
grimey44, a couple of links covering the functioning of the  PrivateDirectory [help]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") & [https://wiki.ubuntu.com/EncryptedPrivateDirectory](https://wiki.ubuntu.com/EncryptedPrivateDirectory) - I will let others more knowledgeable than I comment on full disk encryption.

---

### Post by hyper_ch on 2009-01-14
moving a file to the encrypted folder will not eradicate all traces of that original file as you very likely use a journaling file system.

---

### Post by grimey44 on 2009-01-14
thanx for the help, 
i just not to sure what all the terms are. not sure what a journaling file system is.

So what would be the best way to encrypt a file or folder and not have traces of it on the system somewhere else? 

as of now i right click it the encrpyt, but then it makes a copy of the file and im not sure which ones to delete.

and that brings me to the second question is securly deleting something. Ive read a bunch of guides, but am unfamiliar with a lot of terms.

---

### Post by hyper_ch on 2009-01-15
> **grimey44 said:**
> So what would be the best way to encrypt a file or folder and not have traces of it on the system somewhere else? 

and that brings me to the second question is securly deleting something. Ive read a bunch of guides, but am unfamiliar with a lot of terms.

full encryption of the system is IMHO the saftest way.

---

### Post by Tubes6al4v on 2009-01-15
A journaling file system (as far as I understand it) is a FS where a general map of the files is created so the system can take less time to seak for the information.

However, you could create an encrypted file (archive, folder, whatever), then overwrite the old file, and maybe everything else you don't need, with random data. I don't know if it would take multiple overwrites to securely erase the data though. But you are still left with the journal, which can say that there was or is a file where there is apparently random data. So "they" can surmise that you have something there.

As hyper_ch said, the safest and easiest way is just to use full drive encryption.

---

### Post by hyper_ch on 2009-01-15
point is: in a journaling files you never know for sure if there aren't fragements left and overwriting just doesn't work (as well) there as it does on non-journaling systems.

---

### Post by uabros on 2009-01-15
might just be easier to use [http://crypo.com]("http://crypo.com")

---

### Post by grimey44 on 2009-01-15
alright than again.

what about files on a memory stick? would the best way to encrypt them be to right click the file then click encrypt?


also what does the full drive encryption entail?
i assume, encrypting everything as one. and then having to de-crypt everything befor each use? wouldnt that take a long time to do?

---

### Post by Tubes6al4v on 2009-01-15
Take a look at some of the threads around here on full drive encryption. It is very simple. The data is stored on your hard drive always as encrypted data. You must leave your /boot directory unencrypted so that it can be booted into by the bios. What happens after you provide the passphrase is that the encrypted data from your HD is sent to the CPU, which, using the passphrase supplied, decrypts the data and loads it to RAM. From RAM, the data can be used as normal. 

When you decrypt an encrypted file, you are not actually changin what it looks like on the HD, just transformind that data to someting readable on RAM.

I hope that makes sense, please correct me if I am wrong.

---

### Post by hyper_ch on 2009-01-15
if you have a fully encrypted system you can use truecrypt to encrypt (portably) your stick... so you can access data on it from windows, mac, linux...

but what do you want to do? How much "protection" do you want?

---

