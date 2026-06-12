---
title: "Encrypted Ubuntu Home Directory Question"
date: 2012-08-22
forum: Security
---

### Post by samiux on 2012-08-22
I wonder to know if the home directory is encrypted and the system is online as well as the user of the directory is logged in, when there is an intruder who break into the system, does the intruder see the content of the files inside the said encrypted directory?

This question has been asked to my friends.  Some of them stated that the intruder cannot see the content of the files but the others disagreed.

I know that when the system is offline or boot from Live CD/DVD, nobody can read your content of the files inside the hard drive without your passphrase.

When the system is online, if the intruder can see the content, what is the point to implement this technique to the system?

Samiux

---

### Post by na5h on 2012-08-22
If the computer for instance gets stolen, it is very easy to gain access to the files in the Home folder unless it has been encrypted.

---

### Post by tubbygweilo on 2012-08-22
Encrypting the home directory, using full disk encryption or indeed using both will offer some protection by making the intruder work hard to gain access to you data. Try full disk encryption as it6 protects more than just the home directory - just make sure you don't forget the long, hard and strong passphrase.

---

### Post by Cheesemill on 2012-08-22
No matter whether you just encrypt the home directory or use full disk encryption, when the machine is powered up and you are logged in then your data is just as susceptible to online attacks than if encryption wasn't used as the data is present on your system in a decrypted state.

---

### Post by thnewguy on 2012-08-22
If someone breaks into your account while you are on-line then they can see your files because they are accessing them as you. Encryption protects your data when your machine is stolen, not from intrusion attacks.

---

### Post by Ms. Daisy on 2012-08-23
Data is encrypted when it's not mounted.  As soon as you mount it (i.e. when you can access it yourself), then it's no longer encrypted.

So if the home directory is encrypted, you mount and decrypt it when you log in to the operating system.  That means it's plain text.  When you log out, it is encrypted again.

---

### Post by samiux on 2012-08-23
> **Ms. Daisy said:**
> Data is encrypted when it's not mounted.  As soon as you mount it (i.e. when you can access it yourself), then it's no longer encrypted.

So if the home directory is encrypted, you mount and decrypt it when you log in to the operating system.  That means it's plain text.  When you log out, it is encrypted again.

When the encrypted home directory is mounted and the user is logged in, the data is accessible to the user.  

How about the intruder who break into the system by exploit (not by ssh or similar method) and not knowing the login password of the user and/or the encrypted passpharse?

Samiux

---

### Post by Ms. Daisy on 2012-08-24
If home is encrypted, then it is always mounted as long as the user is logged in, right?   An intrusion could go a lot of ways.  But if he exploited the user  that's logged in, then he could gain access to everything the user can access. 
[QUOTE=samiux]When the system is online, if the intruder can see the content, what is the point to implement this technique to the system?[/QUOTE] The point of encryption is not to protect your data while you're using it.  The point is to protect your data when you're NOT using it.  It protects your data from being usable if someone steals your computer when it's turned off.  But if someone steals it when it's on and you're logged in, encryption will not protect your data at all because it's decrypted.

It really is that simple- when an encrypted file is mounted and decrypted, it's plain text. Period.

---

### Post by kevdog on 2012-08-27
However isn't the /home partition usually encrypted?  So if there are two users on the system, and user #1 is logged in and obviously has his home directory mounted and unencrypted by default, I assume user #2 home directory is also unencrypted as well?

---

### Post by Cheesemill on 2012-08-27
> **kevdog said:**
> However isn't the /home partition usually encrypted?  So if there are two users on the system, and user #1 is logged in and obviously has his home directory mounted and unencrypted by default, I assume user #2 home directory is also unencrypted as well?
Nope.
If you are using home directory encryption then decryption takes place when the user logs on. User #2's home directory only gets decrypted when user #2 logs on.

---

### Post by Dave_L on 2012-08-28
In earlier versions, there was an issue with deciding when to unmount the home directory. For example, a stray process could prevent the home directory from being unmounted on logoff, so that it would remain unencrypted.

I don't know if that was ever completely resolved.

---

### Post by rjbl on 2012-08-29
> **samiux said:**
> I wonder to know if the home directory is encrypted and the system is online as well as the user of the directory is logged in, when there is an intruder who break into the system, does the intruder see the content of the files inside the said encrypted directory?

This question has been asked to my friends.  Some of them stated that the intruder cannot see the content of the files but the others disagreed.

I know that when the system is offline or boot from Live CD/DVD, nobody can read your content of the files inside the hard drive without your passphrase.

When the system is online, if the intruder can see the content, what is the point to implement this technique to the system?

Samiux

Basically an external intruder, or other User on the system can *only *see the contents of your encrypted Home directory, or encrypted sub-directory, if you have shared that H dir, or sub-Dir, with him/her/them. 

Access permissions are, by default, set Owner exclusive (In Ubuntu there isn't even Root access on them). If another User has your your logon credentials then they can get at your encrypted files, of course, just by opening a session as You.

Your encrypted Home, or encrypted sub-dir, isn't actually decrypted the moment you logon. Encryption / decryption is done on the fly - as and when you access the encrypted area - and then only the files you need to access are decrypted to read, or encrypted to write back. 

Hope this helps.

rjbl

---

### Post by rjbl on 2012-08-29
> **Dave_L said:**
> In earlier versions, there was an issue with deciding when to unmount the home directory. For example, a stray process could prevent the home directory from being unmounted on logoff, so that it would remain unencrypted.

I don't know if that was ever completely resolved.

I cannot remember such an issue arising with eCryptFS and, since the whole directory / Home dir is never actually totally decrypted I cannot understand why such an issue should ever arise. You will recall that in encrypting file systems, such as eCryptFS, files are stored individually encrypted and are decrypted only when the allowed User requests each's opening, if the User writes to the opened file the entire file is encrypted afresh, usually with a newly generated session key. 

I cannot recall, offhand, any encrypting FS, virtual disk encryptor or whole disk encryptor which decrypts the entire ciphered space ab initio. On the fly encrypt/decrypt of only the bits of the cypher space the User needs to access to do his stuff with the file(s) has been very much the rule since the original PGPdisk all those years ago.

The main risk with encrypting file systems, like eCryptFS, Microsoft EFS etc, is that file names, sizes, time-stamps and other metadata are not encrypted. The Feds may not be able to ogle your skin flix / dirty pix etc but They sure know what you have been drooling over. 

The other big hazard is sharing your encrypting file system's contents over a network. An intruder / non-allowed local User could run a sniffer and capture the files as they are read by the allowed, but remote, users. Most encrypting file system send requested files in clear across the network to the requesting remote User.

Hope this helps

rjbl

---

### Post by Dave_L on 2012-08-29
rjbl:

The issue to which I referred, if I recall correctly, involved having a file open when logging off, so the file system remained mounted.

Ecryptfs *does* encrypt file names, so that's not an issue.

---

