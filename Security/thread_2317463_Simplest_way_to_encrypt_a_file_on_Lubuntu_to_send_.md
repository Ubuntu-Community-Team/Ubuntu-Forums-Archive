---
title: "Simplest way to encrypt a file on Lubuntu to send to a Windows computer?"
date: 2016-03-16
forum: Security
---

### Post by olie2 on 2016-03-16
Hey all, 

So I was wondering what is the simplest way (for a computer illiterate person) to encrypt a file (a pdf specifically) in Ubuntu/Lubuntu and send it over the internet to a Windows computer to be decrypted? I'm trying to help out a friend and an accountant who are both pretty illiterate when it comes to computers. 

Thanks

---

### Post by papibe on 2016-03-16
Hi olie2.

This a easy way:
[LIST]
[*]open Nautilus (the file manager),
[*]look for the file you want to send,
[*]right-click the file, and select 'Compress...',
[*]select the '.zip' format,
[*]expand 'Other Options',
[*]type the password you want to set to protect the file.
[*]
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by ajgreeny on 2016-03-16
The context option in pcmanfm, Lubuntu's file-manager may be **Create Archive** not **Compress** but some of the archive types, though not all, allow password protection so I agree with papibe's basic idea.

---

### Post by Dennis N on 2016-03-16
> Simplest way to encrypt a file on Lubuntu to send to a Windows computer

Password protection of a file is not encryption. You would use gpg to encrypt a file.

Ubuntu has a plugin (or had one in 12.04, which is the last Ubuntu I used) called seahorse-nautilus that allows you to right click on a file in the file manager window and encrypt it using gpg. You must have previously set up your public/private key pair for gpg and have the public key of the recipient. I think Thunderbird email can encrypt, but on this I'm not sure. If necessary, you can attach the encrypted file to an email. 

On Lubuntu, you have to rely on terminal commands to encrypt the file. No gui in Lubuntu to do this that I know of. You can then attach the encrypted file to an email.  You can find numerous tutorials on the internet that will teach you how to use gpg from the terminal to encrypt and decrypt files.

---

### Post by HermanAB on 2016-03-18
Pkzip encryption is the best way for a non-geek.  It will protect the file against casual inspection, but not against a laboratory attack.

---

### Post by bashiergui on 2016-03-20
7-zip is available on Windows and Linux. When you password-protect a file with 7-zip it encrypts it with AES-256.
[http://www.7-zip.org/7z.html](http://www.7-zip.org/7z.html)

---

### Post by coldraven on 2016-03-20
I agree with papibe, the OP asked for simple and every Windows user, however illiterate, should be able to unzip a file. I've done it myself, just zip it up and telephone them with the password. This will not hinder spooks but will defeat your common criminal.

---

### Post by bashiergui on 2016-03-21
> **coldraven said:**
> I agree with papibe, the OP asked for simple and every Windows user, however illiterate, should be able to unzip a file. I've done it myself, just zip it up and telephone them with the password. This will not hinder spooks but will defeat your common criminal.If the requirement is to use encryption (which is what the OP said), then a common zip won't work.

---

### Post by fugu2 on 2016-03-22
Remeber that windows has WinRAR?  ```
 $ sudo apt-get install rar unrar 
$ rar a -hp encrypted_file.rar secret.txt 
Enter password (will not be echoed):  
Reenter password:  
$  

```  and you can open your rar file with a nice gui   ```
 $ file-roller encrypted_file.rar 
```

---

### Post by bashiergui on 2016-03-24
> **fugu2 said:**
> Remeber that windows has WinRAR?  ```
 $ sudo apt-get install rar unrar 
$ rar a -hp encrypted_file.rar secret.txt 
Enter password (will not be echoed):  
Reenter password:  
$  

```  and you can open your rar file with a nice gui   ```
 $ file-roller encrypted_file.rar 
```
Yes, and winRAR uses AES 256 encryption.

---

