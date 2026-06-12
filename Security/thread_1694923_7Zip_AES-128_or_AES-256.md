---
title: "7Zip: AES-128 or AES-256?"
date: 2011-02-25
forum: Security
---

### Post by Nfabio on 2011-02-25
I started using Ubuntu 10.10 one month ago as my first linux experience, coming from many years on windows systems, and I find it to be a real and affordable alternative to windows.
Quite soon I need to open and modify the content of zip archives created on windows platform, so I installed 7zip, which worked immediately without problems, but when encrypting files (which I do selecting the 'Compress' option from the file manager) I noticed that it was not possible to select the encryption method to be used. The possibility to select the encryption method is present on the windows version of the 7zip interface, where I used to select the AES-256. So I wanted to check which encryption method was actually used by 7zip under linux to encrypt my files. Searching on the web I found PeaZip (available in the portable version for both windows and linux) which provides an 'info' function which reports several information data on a selected file. And here comes the problem:
Looking at the information available over the internet everyone says that 7zip under linux uses AES-256 to encrypt Zip files, but PeaZip provides me a different information: it correctly detects AES-256 on Zip files encrypted on the windows platform, while it reports AES-128 on Zip files encrypted under linux!
My Ubuntu is installed on a 32-bit machine (AMD AthlonXP 2600+ processor).
Can anyone confirm which encryption method is really used by 7zip, and how can I check it?
Is PeaZip returning a wrong information or is it correct?
 
Thanks

---

### Post by Giorgio tani on 2011-02-25
Hi, .7z format uses its encryption scheme based on AES256 in CBC mode, while creating .zip 7z/p7zip (and consequently PeaZip that is based on the same technology) it can use either legacy ZipCrypto (featured only for compatibility with older archivers) or WinZip's Advanced Encryption based on AES128, 192 and 256, AES256 is the default for PeaZip.
To verify the method used on each object inside an archive you can use PeaZip's context menu "Info", I don't know if this is available in Fileroller or Ark but in any case if you have p7zip installed in your system from the console you can use it with the command "list" (l) with "show technical details" option (-slt) - you can see example of the syntax from PeaZip's console tab, or in 7-Zip and p7zip documentation.

---

### Post by Nfabio on 2011-02-25
Giorgio, many thanks for your reply.
I checked the 'technical details' of the archive using the following command from the terminal:
7z l -slt <filename.zip>
This confirmed the information produced by PeaZip. The encryption method used is:
AES-128 Deflate
Do you have any idea why 7Zip is using AES-128 instead of what I understand should be the 'default' AES-256 encryption method?
Is there any way to configure 7Zip and to use AES-256?

Thanks,
Fabio

---

### Post by Giorgio tani on 2011-02-25
With .zip format PeaZip (both for Windows and for Linux) always uses option 
-mem=AES256
in order to explicitly set 7z 9.20 / p7zip 9.13 (latest available) to use AES256.
I don't know with different GUI frontend, but from system's console you can use the same option (you can find syntax examples in PeaZip's console tab) to set 7z/p7zip to use AES256.
If you refer to 7-Zip's documentation please note that 9.13 has some minor differences in syntax with 9.20 (available for Windows only so far).

---

### Post by rookcifer on 2011-02-25
In reality the difference between AES-128 and AES-256 is like saying swimming across the Atlantic is "easier" than swimming across the Pacific.  Both are practically impossible.  If there is someone out there that can break AES-128 (extremely doubtful), I will bet they can break AES-256 as well.

---

### Post by Giorgio tani on 2011-02-26
> **rookcifer said:**
> In reality the difference between AES-128 and AES-256 is like saying swimming across the Atlantic is "easier" than swimming across the Pacific.
I agree, that is a good analogy.

For most final users differences between AES128 and 256 does not matter too much as the encryption is probably the strongest element in user's data security.
Both should be, as for what cryptographers knows, unbreakable for anyone from a practical point of view, at least for decades.
And on the other side, a lot of more practical attacks (cheaper than running multi-billion systems for decades...) could recover the user data: pick-locking, rubber-hosing, bribing, social engineering the password, software bugs, TEMPEST attack against hardware not designed for such grade of security, etc.

However, in an high security scenario (and on dedicated systems built on secure hardware in a secure place), it is relevant to know what AES algorithm is being used, as NIST in 2003 defined AES128 suitable for secret documents, and AES192 and 256 also suitable for top secret documents: [http://csrc.nist.gov/groups/ST/toolkit/documents/aes/CNSS15FS.pdf](http://csrc.nist.gov/groups/ST/toolkit/documents/aes/CNSS15FS.pdf)
Probably this is not relevant for most users from a practical point of view, however technically AES128 and 256 were credited of being appropriate for handling different security situation.

---

### Post by Nfabio on 2011-02-26
Again thanks to Giorgio and rookcifer for their hints.
I successfully tried the manual creation of a zip file from the Terminal window using the following command:
7z a -p<password> -mem=AES256 -tzip <zipname> <sourcefilename>
I verified the encryption method used to create the zip file using the command:
7z l -slt <zipfilename>
which correctly returned the Method=AES-256 Deflate.

The problem is that it only works when creating the zip file manually.
When I create the zip file from Nautilus (the default Ubuntu file explorer) it is always encrypted using the AES-128, and there is no option accessible from the graphical interface to set the default encryption method to be used.
Is there any way to set this parameter when using the "Compress" function in Nautilus?

Thanks,
Fabio

__

---

### Post by asmoore82 on 2011-02-26
7zip is great but it should never be used in a long-term archiving strategy on Linux!

From the `7z` manpage:
[quote=7zip]**Backup and limitations**
       DO NOT USE the 7-zip format for backup purpose on Linux/Unix because :
        - 7-zip does not store the owner/group of the file.[/quote]

"*.tar.lzma" is the proper Linux equivalent of 7zip, with the same compression algorithm.

Likewise, if you desire encryption, this is already solved by other utilities.
It would be unnecessary bloat to do so at the archive management level.

10 years down the road, a filename like "*.tar.lzma.pgp" is much more
useful than an encrypted archive tersely named "*.zip"
"*.zip" leaves all questions unanswered:
Which version number of zip?
Which vendor extensions to zip?
Which compression algorithm?
Which encryption algorithm?

GNU Privacy Guard also opens up the possibility of encrypting files for specified
recipients. No password will open them &#8212; only the recipients' private keys.

Welcome to Linux!
It is infused with the philosophy of real longevity.
By comparison, the philosophy of other OS's is "take the money and run."

---

### Post by rookcifer on 2011-02-26
> **Giorgio tani said:**
> However, in an high security scenario (and on dedicated systems built on secure hardware in a secure place), it is relevant to know what AES algorithm is being used, as NIST in 2003 defined AES128 suitable for secret documents, and AES192 and 256 also suitable for top secret documents: [http://csrc.nist.gov/groups/ST/toolkit/documents/aes/CNSS15FS.pdf](http://csrc.nist.gov/groups/ST/toolkit/documents/aes/CNSS15FS.pdf)
Probably this is not relevant for most users from a practical point of view, however technically AES128 and 256 were credited of being appropriate for handling different security situation.

Yeah that is only because classified data may have to be stored for very long periods of time.  It's possible (likely even) that in the future someone will discover an attack that reduces the complexity of AES significantly.  When that happens, a 128 bit cipher may not be strong enough anymore, but a 256 bit cipher would still hold up.

---

### Post by Nfabio on 2011-02-27
I agree with all of your observations.
For long term storage more reliable encryption algorithms may be used.

Nevertheless for short term storage (or everyday use) I think that encryption algorithms based on passwords which can be remembered and typed without needing additional supports, which allows easy exchange between different platforms using commonly available and easy-to-use tools (i.e. with a graphical interface), I think that today 7zip and AES may still represent a good choice. I think this is the target of this kind of tools.

Anyway apart from those considerations, I started this thread because I'm basically curious: I like to learn how things work, and I would like to learn more about linux rather than being a blind user. Since I know that 7zip allows the use of different encryption algorithms, and since Nautilus obviously made a choice among them, I would like to know where this option is set and how I can change it to better suit my taste - because I would like to be free to choose the algorithm I like and not to be forced to use the one that someone else chosen for me. Don't you like to know more about this?

So, can anyone help and explain me more on this?


Thanks,
Fabio

---

