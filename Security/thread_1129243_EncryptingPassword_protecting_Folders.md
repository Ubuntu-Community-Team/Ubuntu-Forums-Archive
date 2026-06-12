---
title: "Encrypting/Password protecting Folders"
date: 2009-04-18
forum: Security
---

### Post by Psyphre on 2009-04-18
Hi,

I have seen this asked countless times, but I have yet to see a good solution. 
Say you have a folder you want to password protect; how would you do it?

The main response I've seen is to encrypt it. But unfortunately its so unpractical.
I tried encrypting a test folder which contained a few files and you can either:

1) Encrypt each file. This means you now have a folder with 2 of each file inside. ! unencrypted and 1 encrypted. So now you've got to delete all the unencrypted files. Its fine if you have a few, but what if you've got hundreds of files? Furthermore you have to unencrypt each file individually to view them. Totally unpractical.

2) Encrypt the whole thing in a package (usually zip or something similar). This is better than encrypting the files individually but still not practical at all. It mean's im essentially zipping and unzipping everytime I want to view the folder. Its ok if its just a small file, but what if I'm encrypting gigabytes worth of files?


Is there no simple solution to simply password protect a folder? So that everytime I want to view the contents I just input a password. No compressing/uncompressing/encrypting/decrypting where youll spend more time accessing it than actually viewing the contents.

Anyway, thanks for reading, and I'm eager to see any suggestions. Please correct me If I've got anything wrong.

Thanks.

---

### Post by cubeist on 2009-04-18
There is a solution... true crypt.  In my opinion one of the best open source pieces of software.  The usage is fairly simple, but the theory and depth of the program is complex, so you will have to do some reading... here is a good place to start

[http://ubuntuforums.org/showthread.php?t=990331&highlight=truecrypt](http://ubuntuforums.org/showthread.php?t=990331&highlight=truecrypt)

and

[http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/)


post back if you have specific questions!

---

### Post by Psyphre on 2009-04-18
cubeist, thank you very much for your reply. I took a look at truecrypt and I'm very impressed with its security. 

However, upon trying it, unfortunately you have to specify the size of the volume/file to be encrypted - not practical for me. 

I have just found an applet called cryptkeeper, which is similar to truecrypt (though not as advanced or secure), but its practicality is really appealing. I can mount/unmount really easily and it just asks for a password to be mounted. Also it doesnt ask for a size, so i assume it only takes up as much as the files in the folder.

---

### Post by bodhi.zazen on 2009-04-18
encryption is probably the best way to go.

See this for some suggestions on how to do it :)

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

---

### Post by kevdog on 2009-04-19
bodhi

Good reference page.  Nice explanations!  Not a big fan of the black background, but the information was an A+.  The ability however not to have the home directory on a separate partition however is somewhat disappointing.  Its probably a matter of time until this is fixed however.

---

### Post by bodhi.zazen on 2009-04-19
Kevdog : thank you for your kind words :)

sorry 'bout the ugly css :lolflag:

---

### Post by cubeist on 2009-04-19
> **bodhi.zazen said:**
> encryption is probably the best way to go.

See this for some suggestions on how to do it :)

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

Thanks, I somehow have not heard of this program, and it looks like it integrates with linux better than truecrypt, which I think was designed for windows first and then ported back to work on linux and macs...

---

### Post by kevdog on 2009-04-19
bodhi

Can the source of this encfs be added to older kernels or other kernel versions?  Just wondering how integrated it is with a specific kernel version or Ubuntu in general.

---

### Post by bodhi.zazen on 2009-04-19
ecryptfs has been in rapid development and there have been issues with compatibility moving forward, particularly when updating versions of Ubuntu.

more and more features have been added in 9.04 as well ...

So, IMO, if you like ecryptfs I would go with 9.04.

---

### Post by kevdog on 2009-04-19
I plan on using 9.04 once its finally released.  I used to do the alpha, beta thing a long time ago, but after many a release, it kind of grew old on my.  With patience in hand now, I just wait until the release is finalized and then I upgrade.

With what you are saying however, would that mean I should worry about compatibility with future versions of ubuntu like 9.10 and encfs?  I guess I always install after wiping the hard drive so compatibility for me might not be a specific issue, however for users trying the upgrade route, could this be a potential problem?

---

### Post by bodhi.zazen on 2009-04-19
Compatibility moving forward looks good, IMO.

Yes there are issues for users upgrading. The advice is to delete and re-create the crypt.

---

### Post by kevdog on 2009-04-19
anymore technical sites that give info on how the encryption is performed? aes, blowfish, serpent, etc?  dual algorithms?

---

### Post by bodhi.zazen on 2009-04-19
You have several options, yo will see them when you set up an encrypted directory , example :

[http://www.devx.com/opensource/Article/39337/0/page/2](http://www.devx.com/opensource/Article/39337/0/page/2)

---

### Post by kevdog on 2009-04-20
I was hoping for double encryption options similar to Truecrypt.  I only saw aes, and des variants.  Either way with the Jaunty install I will try this feature out.  Thanks for the information and the link.  I like the feature of protecting the folder via a USB password.

---

### Post by The Cog on 2009-04-20
Ecryptfs loos interesting, but it's not quite what I was after. I wanted a directory that I could unlock and relock at will, not to automatically happen wherever I log in, and not my whole home. I find that encfs does just what I want.

I added these two scripts to /usr/local/bin:
/usr/local/bin/crypton:
> #!/bin/sh
encfs ~/.crypt ~/crypt
/usr/local/bin/cryptoff:
> #!/bin/sh
fusermount -u ~/crypt

The encrypted files are held in ~/.crypt. The command **crypton** makes the unencrypted content visible in ~/crypt and **cryptoff** makes crypt appear empty again.

First time you use crypton, the directories are created and you are promoted to give the passphrase that will be needed later whenever you unlock the crypt. Even when unlocked, only the logged on user can see the crypt contents (root gets access denied).

This is an ideal solution for me, as I keep just a few documents that I only want to access occasionally.

---

### Post by bodhi.zazen on 2009-04-20
Ecryptfs will do the same thing. You are confusing the "private home" (which is not the greatest of names) with encrypting a single directory.

See the section under an encrypted directory on this page : [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by The Cog on 2009-04-21
Thanks for the correction. I should read more carefully. However, I don't like having to use sudo in order to mount the encrypted partition. It means that normal users have no option but to allow th auto-mount at login to do it for them.

Still, both solutions have their niches.

---

### Post by bodhi.zazen on 2009-04-21
Simply add your users with visudo (you do not need to give full root access).

But yes, it is nice to have options with encryption.

---

