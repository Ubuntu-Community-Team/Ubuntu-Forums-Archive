---
title: "Firefox User Profiles No Longer work in encrypted folders or partitions??"
date: 2010-08-08
forum: Security
---

### Post by StewartM on 2010-08-08
I've just upgraded my desktop from 8.04 to 10.04. I'm using Scramdisk 2.02.

Previously, I had placed my firefox user profile in an encrypted Truecrypt  container file created under Scramdisk. I had done so by creating a new profile in firefox's profile manager. This had worked in previous versions (and it still works with 9.10 on my laptop).

But when I tried to access my previous profile when first opening firefox, I got the error message "cannot use profile 'x' because it is in use".

I have tried the following workarounds:

a) creating a new profile in an encrypted container;
b) creating a new profile in an encrypted container with a different filesystem (FAT32 instead of ext3);
c) dragging an existing and working firefox profile created under the ./mozilla/firefox default directory into an encrypted container and linking back to it;
d) dragging the entire ./mozilla/firefox folder into an encrypted container and linking back to it on the main directory tree;
e) creating an EncFS folder instead of a TrueCrypt container and creating profile inside of it.
f) draging an already-created and working firefox profile  (created under ./mozilla/firefox) into an ecrypted EncFS folder and linking back to it.

And yet, each time I get the same error message.

Note, if I create a new profile under the ./mozilla/firefox directory and replace all the default files with those from a profile folder from an encrypted folder, it starts normally. But there I lose the advantages of encryption.

I also have tried my other programs that I have linked to encrypted folders--Pan, Pidgin, Evolution, plus other folders I have moved (./thumbnails, ./gnupg, ./openofficeorg, ./wine, ./yahoorc). These all work as they did previously. I can open my containers, view and create new files in them, so it's not obviously a permissions issue.

So is there anything about Firefox that doesn't like encrypted folders or partitions? I also note that firefox takes a lot longer to start than it used to.

StewartM

---

### Post by bodhi.zazen on 2010-08-08
Firefox works fine with the default encryption tools, LUKS for whole disk encryption and ecryptfs for an encrypted home.

Is there some reason you do not want to use the default tools ?

Otherwise the tools you mention are both third party, you may need to try the mailing lists or forums for those projects (if no one here knows an answer).

---

### Post by StewartM on 2010-08-08
> **bodhi.zazen said:**
> Firefox works fine with the default encryption tools, LUKS for whole disk encryption and ecryptfs for an encrypted home.

Is there some reason you do not want to use the default tools ?

Otherwise the tools you mention are both third party, you may need to try the mailing lists or forums for those projects (if no one here knows an answer).

To answer your first question--I have been using Scramdisk, using Truecrypt containers, since 7.04. This is the first time it's broken. Everything else but firefox running from inside the container works as normal. 

Scramdisk has been well maintained. The only problem so far with 10.04 is that Scramdisk currently requires 2.6.32-22 generic, and it is broken by the kernel that came by default with with the new upgrade--2.6.32-24 generic. When Scramdisk was installed, it installed the earlier kernel, but going back a step degrades my video performance (so I run in low-graphics mode). I've emailed the developer about this, and if past experience is any guide he'll respond by issuing a recompiled version that works with 2.6.32-24.

To answer you second question--both Truecrypt and EncFS *are* supported by Ubuntu--or at least they are supported by the community, as these programs are all found in the repositories. Truecrypt is implement by Easy Crypt and GDecrypt, where EncFS folder encryption is implemented using Cryptkeeper. I was using Cryptkeeper to create the encrypted EncFS folder in this instance.

I would have thought that someone would be doing something similar, as I asked as a raw newbie 3 years ago how to direct mail and other folders to an encrypted container on this same forum, and received answers how to do it.

[http://www.ge.ubuntuforums.org/showthread.php?t=554741&](http://www.ge.ubuntuforums.org/showthread.php?t=554741&)


As for using the default tools, as I understand it, requires moving everything off the drive and doing a clean install to set up an encrypted /home directory using the Alternative CD. Is that right? 

Also, when this idea was being floated in development, I recall that the passphrase to one's /home directory encryption would be the same as the login passphrase. *If* that was so it seemed to me that someone could walk up to your machine, boot from a live CD, then force a change of one's login passphrase as root in recovery mode. Then one has complete access to everything as one would be able to log in as that user. That would defeat the whole purpose of having any encryption would it not?

With an encryption passphrase with a separate program that's separate from the login, by contrast, there's no way for such an attacker to access the materials inside the encrypted folders or containers. They can delete the account and all the files, to be sure, but they can't access anything. That seemed to me the safer route.

Please correct me if my perceptions are wrong about this. It was these concerns, plus the additional work that doing an installation from scratch involved, which kept me from going the encrypted /home route.

As for the whole-disk encryption option--that defeats the purpose of having a multi-user system. Either it becomes a single-user system, or you share a passphrase with someone (bad idea).

StewartM

---

### Post by bodhi.zazen on 2010-08-08
If you wanted to use LUKS, yes you would need to back up your data and perform a fresh install with the alternate CD.

LUKS supports up to 8 passwords (if you have multiple users and do not want to share a password).

If you use ecryptfs to encrypt your $HOME directory , by default, it uses you login to decrypt $HOME.

BUT, you can not simply change a users password as root or with a live CE and access the data, that is a misunderstanding on your part. Try it in a VM or a test installation and see for yourself ;)

With ecryptfs a user has to change his or her password with the graphical tools or via the commmand line via an additional step. There are several page on an encrypted home on Ubuntu if you wish.

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

You can access the encrypted $HOME from a live CD, if you have the information you need :

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

Hope that helps your understanding. I do not know the answer to your original question / problem with firefox.

I have not used truecrypt in a while but my impression is that it is less and less compatible with Ubuntu over time, and your post re kernel and video problems reinforce that impression.

FYI, if your issue is somehow one of cross platform, there are applications to mount a LUKS partition in Windows and I believe OSX.

[FreeOTFE - Windows LUKS]("http://www.freeotfe.org/") 

As you can probably guess, I use LUKS and have not run into any problem with kernels, video, or really any problem at all.

---

### Post by FuturePilot on 2010-08-08
> **StewartM said:**
> 
As for using the default tools, as I understand it, requires moving everything off the drive and doing a clean install to set up an encrypted /home directory using the Alternative CD. Is that right? 
No [http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html]("http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html")

> Also, when this idea was being floated in development, I recall that the passphrase to one's /home directory encryption would be the same as the login passphrase. *If* that was so it seemed to me that someone could walk up to your machine, boot from a live CD, then force a change of one's login passphrase as root in recovery mode. Then one has complete access to everything as one would be able to log in as that user. That would defeat the whole purpose of having any encryption would it not?
No [http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html]("http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html")

---

### Post by StewartM on 2010-08-08
Thanks to both of you for clearing up my misunderstanding.

Just for the sake of simplicity, would it be possible to set up the ./Private directory using Ecryptfs, and then try syslinking the ./mozilla/firefox/user profile directory to that? I assume that was the original purpose of such the ./Private folder in 8.10. (Although I can't see why that would be so different than what I had been doing with my earlier attempts).

I should also say that this is not a sudo user (I adhere to the habit of only using my sudo user for administration and not ordinary work). I assume that the command ecryptfs-setup-private does not need sudo privileges?

As for the encrypted /home option, that would require freeing up more disk space than I currently have, even after doing a lot of disk cleaning. There's probably a workaround for that, but that would be second choice. 

Once again, thanks.

StewartM

---

### Post by FuturePilot on 2010-08-08
> Just for the sake of simplicity, would it be possible to set up the ./Private directory using Ecryptfs, and then try syslinking the ./mozilla/firefox/user profile directory to that? I assume that was the original purpose of such the ./Private folder in 8.10.

Yes, that is indeed how it originally worked with 8.10. It was later expanded to be able to encrypt your entire /home/$USER directory.

> I should also say that this is not a sudo user (I adhere to the habit of only using my sudo user for administration and not ordinary work). I assume that the command ecryptfs-setup-private does not need sudo privileges?

No, it can be run as a non-sudo user.

> (Although I can't see why that would be so different than what I had been doing with my earlier attempts).

The problem with scramdisk is that it's a third party kernel module which is precompiled against a certain kernel version. When the kernel ABI changes, it breaks scramdisk. You would have to recompile the kernel module whenever the ABI changes. It would be better if scramdisk used DKMS to automatically recompile it whenever the kernel ABI changes. You wouldn't run into this problem using built-in tools like ecryptfs or LUKS.

---

### Post by rookcifer on 2010-08-08
> **StewartM said:**
> Also, when this idea was being floated in development, I recall that the passphrase to one's /home directory encryption would be the same as the login passphrase. *If* that was so it seemed to me that someone could walk up to your machine, boot from a live CD, then force a change of one's login passphrase as root in recovery mode. Then one has complete access to everything as one would be able to log in as that user. That would defeat the whole purpose of having any encryption would it not?

That's the case for EncFS, but not for the better LUKS option.  LUKS will do whole disk encryption, which means that, obviously, the password used will be different from that of the user account.  (LUKS will also do container encryption if you need that).  LUKS is a better option for Linux than Truecrypt since Truecrypt was specifically written with Windows in mind.  Truecrypt still cannot do WDE on Linux, plus TC has that weird home brew license.

> As for the whole-disk encryption option--that defeats the purpose of having a multi-user system. Either it becomes a single-user system, or you share a passphrase with someone (bad idea).


Hmm, well obviously if you trust someone enough to use your system you should trust them enough to decrypt it in order to use it.  Or, if you prefer, you can create separate partitions and encrypt them with different passphrases.  BTW, LUKS will allow 8 different passwords to be used for the same container.  This is so that if someone should no longer need access you can delete their password without having to change your own.  This is good in work environments where there might be turnover.

---

### Post by FuturePilot on 2010-08-08
> **rookcifer said:**
> That's the case for EncFS,

You mean Ecryptfs? That's not the case with Ecryptfs. Even if someone changed your login password with say the root account, that's all they can change. They still couldn't access your encrypted data because it will still be encrypted with the salted passphrase created from your old password.

---

### Post by rookcifer on 2010-08-08
> **FuturePilot said:**
> You mean Ecryptfs? That's not the case with Ecryptfs. Even if someone changed your login password with say the root account, that's all they can change. They still couldn't access your encrypted data because it will still be encrypted with the salted passphrase created from your old password.

I should have been more specific.  I was only responding to this statement:

> *Also, when this idea was being floated in development, I recall that the passphrase to one's /home directory encryption would be the same as the login passphrase.*

It's true that ecryptfs uses the user password as the volume key.  It's also true that the developers aren't stupid and don't allow the volume password to change each time the user password changes.

As for encryptfs and [EncFS]("http://en.wikipedia.org/wiki/EncFS"), they are essentially the same thing except ecryptfs runs in kernel mode while EncFS runs in userspace.  But, yes, you're right, I should have said ecryptfs since that is what Ubuntu uses.  I also happen to hate it and never recommend such encryption techniques.  Block device encryption is much cleaner, imo.

---

### Post by StewartM on 2010-08-09
> **FuturePilot said:**
> 

No [http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html]("http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html")

Reading this, and if I understand correctly--so the actual key is stored in the kernel keyring and the login passphrase is hashed. The actual key itself is very strong, but wouldn't everything in the end still depend on the strength of the user login passphrase? That's what is used to access the key.

There's something else I don't understand (from your blog)

[http://blog.dustinkirkland.com/2008/12/ubuntu-jaunty-encrypted-home.html](http://blog.dustinkirkland.com/2008/12/ubuntu-jaunty-encrypted-home.html)

"It handles your password changing just fine. Basically, your login passphrase and your mount passphrase are two different entities. The mount passphrase is "wrapped" or encrypted using your login passphrase. When you login to the system, your login passphrase is then used to "unwrap" or decrypt your mount passphrase, and then perform the mount. If you change your login passphrase, pam_ecryptfs simply unwraps, and then re-wraps your mount passphrase. That way, we don't have to go through the excruciating process of re-encrypting every file."

So what's to stop an attacker from walking up to your computer, and booting in recovery mode to a root shell and changing your login passphrase? 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Maybe I'm just not getting it. "Magic" is right, I've been using encryption for over a decade now, but this process is baffling.

StewartM

---

### Post by StewartM on 2010-08-09
> **rookcifer said:**
> That's the case for EncFS, but not for the better LUKS option.  LUKS will do whole disk encryption, which means that, obviously, the password used will be different from that of the user account.  (LUKS will also do container encryption if you need that).  

Is there a tutorial on creating LUKS containers? That is one of the options I'm pondering, to replace my Scramdisk containers with LUKS containers.

> LUKS is a better option for Linux than Truecrypt since Truecrypt was specifically written with Windows in mind.  Truecrypt still cannot do WDE on Linux, plus TC has that weird home brew license. 

The Scramdisk developer, Hans-Ulrich Juettner, has been very diligent about issuing recompiled versions of Scramdisk shortly after being notified of a kernel breakage (usually within 1-2 days). I started using Scramdisk back in 2007 because I had used it in Windows in my pre-Linux days, and it seemed the best choice for a Linux box (back then there were "brew your own" encryption tutorials for Ubuntu and no official support). It has worked well up until this point, which has earned my loyalty, and it has incorporated new features like encrypted swap and a variety of hash and encryption algorithms. 

There is also a feature in Scramdisk that I like that has been missing from all other Linux encryption tools I've tried (from Seahorse to Cryptkeeper, etc)--and that is the "display passphrase" feature. I don't know about you, but I can and will use stronger passphrases when I can see what I'm typing and not some string of *****s. When you can see what you're typing, you can and will use passphrases 20 or 30 or more characters long which are resistant to dictionary attacks. When you get a string of *****s, you tend to stick to the 6-15 character strings that are more easily entered in and remembered.

To me, that's an important point. I suppose there's a danger of someone setting up a mini-camera in your room to see you typing in your passphrase, but the real threat nowadays comes from hardware keyloggers--these have really come down in price. The real value of encryption has thus become that of protecting one's data from either the theft of one's computer or (in a civil or criminal proceeding) the seizure of it after-the-fact as kind of an afterthought. In the latter cases, the difference between trying to crack a 30-character passphrase and an 8 character passphrase is very real. OTH, if an attacker suspects or wants something from you and has time to plan an attack, he will try to get access to your machine in your absence and install a hardware keylogger.

Sorry for the rant, but it seems that only giving users strings of *****s to me, at least, offer no real protection and actually are a deterrence to better security practices.

>  Hmm, well obviously if you trust someone enough to use your system you should trust them enough to decrypt it in order to use it.  Or, if you prefer, you can create separate partitions and encrypt them with different passphrases.  BTW, LUKS will allow 8 different passwords to be used for the same container.  This is so that if someone should no longer need access you can delete their password without having to change your own.  This is good in work environments where there might be turnover.

Most of the users on my system use the guest account--I created one just for walk-up users, and didn't want to bother them with encryption (nor did I figure they would need it). I did have a regular user once but no more. I was also concerned about the increased difficulty I might experience during upgrades. And of course, there would be the additional work of having to do a clean installation. All these have deterred me from going that route, until now at least.

StewartM

---

### Post by StewartM on 2010-08-09
> **bodhi.zazen said:**
> 
If you use ecryptfs to encrypt your $HOME directory , by default, it uses you login to decrypt $HOME.

BUT, you can not simply change a users password as root or with a live CE and access the data, that is a misunderstanding on your part. Try it in a VM or a test installation and see for yourself ;)

With ecryptfs a user has to change his or her password with the graphical tools or via the commmand line via an additional step. There are several page on an encrypted home on Ubuntu if you wish.

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

You can access the encrypted $HOME from a live CD, if you have the information you need :

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

Thank you.

It seems to me--and I was looking over Dustin's tutorial about migrating a non-encrypted /home/user directory to an encrypted one--why couldn't I:

a) Create a new encrypted user account with Ecryptfs--/home/newuser;

b) "Dump" all my data in my current encrypted Scramdisk containers under /home/olduser into cleartext data onto  remote external hard drive;

c) Use my sudo account to reset the ownership and privileges on the cleartext data on that external drive to the newuser account;

d) copy the cleartext data into the relevant places in /home/newuser and set it up for the relevant programs. Now it is encrypted.

e) Shred the cleartext data on the external drive;

f) Delete the /home/olduser account (this would include the Scramdisk container volumes, no shredding necessary).

Wouldn't that work?

>  Hope that helps your understanding. I do not know the answer to your original question / problem with firefox.

I have not used truecrypt in a while but my impression is that it is less and less compatible with Ubuntu over time, and your post re kernel and video problems reinforce that impression.


The problem with Firefox is weird--all the other programs function as normally. Looking at the Firefox help, the "profile is in use" usually indicates problems lock or parentlock or sessions.js files or whatnot--not the problem here (as new profiles won't work either).

It is possible, that since running in low-graphics mode is breaking my webcam in all programs but cheese, that it's affecting Flash, a plugin for firefox (it won't work in flash either). I can test that hypothesis today by booting into the latest kernel, creating a Cryptkeeper EncFS folder (or some other compatible encryption) and trying to create a profile there. If it works with the latest kernel but not with the earlier one it could be that it's all my graphics card problem.

I'm looking at the wiki--and it does mention that you *DO* have to remember the mount passphrase if you want to access your data if the login one was changed (either you, or by an attacker). That's more understandable. 

I apologize to Dustin for my earlier misunderstanding.

StewartM

---

### Post by bodhi.zazen on 2010-08-09
You can move / encrypt your home directory without re-installing.

You can not encrypt the entire system with LUKS without re-installing.

Either way the general process of backing up and restoring your data would be the same.

Personally I have been happy with LUKS (encrypt the entire system). I tend to encrypt only some data and not all of my home directory. cryptkeeper is a nice tool to maintain an encrypted directory.

---

### Post by StewartM on 2010-08-09
> **StewartM said:**
> Reading this, and if I understand correctly--so the actual key is stored in the kernel keyring and the login passphrase is hashed. The actual key itself is very strong, but wouldn't everything in the end still depend on the strength of the user login passphrase? That's what is used to access the key.

There's something else I don't understand (from your blog)

[http://blog.dustinkirkland.com/2008/12/ubuntu-jaunty-encrypted-home.html](http://blog.dustinkirkland.com/2008/12/ubuntu-jaunty-encrypted-home.html)

"It handles your password changing just fine. Basically, your login passphrase and your mount passphrase are two different entities. The mount passphrase is "wrapped" or encrypted using your login passphrase. When you login to the system, your login passphrase is then used to "unwrap" or decrypt your mount passphrase, and then perform the mount. If you change your login passphrase, pam_ecryptfs simply unwraps, and then re-wraps your mount passphrase. That way, we don't have to go through the excruciating process of re-encrypting every file."

So what's to stop an attacker from walking up to your computer, and booting in recovery mode to a root shell and changing your login passphrase? 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Maybe I'm just not getting it. "Magic" is right, I've been using encryption for over a decade now, but this process is baffling.

StewartM

Dustin: I just wanted to follow up and tell you in doing more digging I had found this:

[http://blog.dustinkirkland.com/2009/03/ubuntu-encrypted-home-with-2-factor.html](http://blog.dustinkirkland.com/2009/03/ubuntu-encrypted-home-with-2-factor.html)

"For obvious reasons, it's important that your login passphrase is strong. This is the passphrase that "guards" your wrapped-passphrase file, if your attacker has access to that too."

So your login password should be strong enough to protect your wrapped passphrase file. That makes sense. Sorry to misunderstand, and thanks for all the advice.


StewartM

---

### Post by FuturePilot on 2010-08-09
I'm not Dustin ;)

---

### Post by StewartM on 2010-08-10
> **FuturePilot said:**
> I'm not Dustin ;)

Ooops. :redface:

My bad.

I'm thinking that since I'm also having a problem with flash:

[http://ubuntuforums.org/showthread.php?t=1549477](http://ubuntuforums.org/showthread.php?t=1549477)

That this a problem with firefox, or a problem with flash that is affecting firefox. 

Last night I downloaded and installed Truecrypt, which does work with the 2.6.32-24 generic kernel. It could open my container files just fine. But firefox could not create or access any profiles inside of them. 

When this machine was running 8.04, I had upgraded flash to the most recent version. Perhaps since it *was* the most recent version, Flash was not replaced during the upgrade and is not working properly? And perhaps that is causing other problems with firefox giving strange behaviors when creating user profiles?

I could try removing firefox and flash and then re-install them. But I am thinking the best path forward now for both issues is to wipe the drive and take a step backwards to 9.10. In 9.10 (on my laptop) everything works. It might be that if I did a clean install of 10.04 instead of the upgrade (from 8.04) that this might fix these things too (but Scramdisk would still not work, not without degrading my video performance). With an everything-working system, I could also create a ecryptfs user account and start playing with that functionality and migrating things over to that to make the future upgrade to 10.04 less problematic.

Doing a fresh install of 9.10 would also allow me to do one other thing, which is to partition my disk to have a separate /home directory, to simplify any potential problems with upgrades going bad.

But what I would love to know is whether or not someone can take a non-encrypted user account in 10.04, create a Truecrypt partition with it, and then have Firefox create a user profile within that. That would tell me whether the problem is specific to my machine or is something generic to Ubuntu 10.04 and Firefox 3.6.8. Not having found anything in google, I suspect it's the former.

StewartM

---

### Post by StewartM on 2010-08-13
Well, well, well. It seems that completely removing the adobe flash plugin and removing firefox (using the --purge command) did solve the problem of not being able to direct firefox to use profiles in encrypted disk space. So I'll mark this thread solved.

I have another question about encryptfs, but I'll pose that in another thread. Thanks for the replies.

StewartM

---

### Post by StewartM on 2010-08-15
I'd just like to update this post with something I found after I posted. This post is thus to make this thread complete, so no one gets misled.

With the 2.6.32-22 generic kernel, with the version 173 NVIDA driver, everything works (except there is a problem with black screen hangups when switching between users, perhaps the reason that NVIDA released a new driver on 8/02). Firefox can access user profiles as before.

However, with the 2.6.32-24 generic kernel, using the newest version NVIDA driver, firefox will NOT access user profiles inside encrypted space (other than the kind officially supported by Ubuntu)--just like the problem I had before. So it's a "feature" of the 2.6.32-24 kernel. Re-installing firefox, however, did fix my problem with flash on this kernel.

Where do I file a bug report on this?

StewartM

---

### Post by cariboo on 2010-08-15
To file a bug you need to create an account at [, once you have an account bugs are reported on [URL="https://bugs.launchpad.net/"]bugs.launchpad.net/]("https://launchpad.net/"launchpad.net/[/URL), do a search to make sure your bug hasn't been reported already. If your bug hasn't, press Alt-F2 and type:

```
ubuntu-bug <packagename>
```

where <packagename> is the name of the package you are reporting a bug.

---

