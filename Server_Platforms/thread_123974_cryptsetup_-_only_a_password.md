---
title: "cryptsetup - only a password???"
date: 2006-01-31
forum: Server Platforms
---

### Post by timw on 2006-01-31
Hello there. I was wondering if one of you knowledgeable types could clarify for me why cryptsetup only asks for a password at startup to allow access to the encrypted devices?

I understand that the encyrption itself is done using AES (or other algorithm) but to my mind at the end of the day if a hacker can guess/brute force you password then the strength of AES as an encryption algorithm is redundant.

I've only just setup my encrypted drive using cryptsetup so I've not delved too deeply but when I started looking into creating a transparent encrypted drive for my PC I imagined that I would be asked (on mount) for my private key file (not a password). 

Does the cryptsetup program support this type of setup? Am I missing something fundamental about the nature of the encryption that cryptsetup uses?

Thanks in advance!

Tim

---

### Post by tcwitte on 2006-02-06
It only asks for a password and I don't know whether it could also use a key: you can choose a pretty long password but whether bytes higher than 100 bytes would be used I don't know. I'm sure that if it's possible somebody's written how to construct a system with encrypted filesystems mounted by key on USB stick or something.

BTW it doesn't ask the password on mount but when it sets up the loop device (the virtual device which seems to contain the filesystem). If you only umount, your data is still accessible from the virtual device.

---

### Post by imagine on 2006-02-07
[QUOTE=timw]I was wondering if one of you knowledgeable types could clarify for me why cryptsetup only asks for a password at startup to allow access to the encrypted devices?[/QUOTE]Umm, because passwords are handy for authentication.
In general it can be asked for two things: Something you know (password) and/or something you have (key). Ignore biometric authentication here, dm-crypt cannot handle that AFAIK and it's not secure anyway.

[QUOTE=timw]I understand that the encyrption itself is done using AES (or other algorithm) but to my mind at the end of the day if a hacker can guess/brute force you password then the strength of AES as an encryption algorithm is redundant.[/QUOTE]Right. That's why you should chose a good password.

[QUOTE=timw]I've only just setup my encrypted drive using cryptsetup so I've not delved too deeply but when I started looking into creating a transparent encrypted drive for my PC I imagined that I would be asked (on mount) for my private key file (not a password).[/QUOTE]Depends on how you configured it. If you added your encrypted partitions to /etc/crypttab or hacked them into the init-scripts manually, then cryptsetup gets called on boot. And if no keyfile was specified then cryptsetup asks for a password.
What else should the poor thing do.

[QUOTE=timw]Does the cryptsetup program support this type of setup? Am I missing something fundamental about the nature of the encryption that cryptsetup uses?[/QUOTE]Maybe you missed reading the man page : ) 
There are various ways to create and store keyfiles and passing them to cryptsetup - at boot or manually from the command line. Eg have a look at the -d switch of cryptsetup.
$ man cryptsetup
$ man crypttab
[http://www.saout.de/tikiwiki/tiki-index.php](http://www.saout.de/tikiwiki/tiki-index.php)

If you don't already have a keyfile, you can also search for one of the various guides about how to create keyfiles. People came up with an unlimited amount of weird stuff, like grabbing the data from a tv-tuner, converting it to ASCII, mixing it up with the input from their mouse and piping it multiple times through head, tail and uuencode until something which looks like Perl code comes out. If you have no time you can of course also do a boring $ echo "my secret password" > ~/keyfile


Since you didn't wrote what exactly you have in mind I can't give anymore details. But you should avoid to secure your partitions only with a key and no password, maybe with the exception of swap or /tmp. If anyone gets hold of this file by stealing or copying the usb stick (or whereever the key is stored) then your encryption becomes useless. Better encode the keyfile with gpg.

---

