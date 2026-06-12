---
title: "How to encrypt a directory...but not decrypt on start-up"
date: 2006-08-17
forum: Server Platforms
---

### Post by Shane10101 on 2006-08-17
Hey,

I've been googling my eyes out for two days trying to find a way to encrypt a single directory in my filesystem (/home/this_user/crypt) so that it's only decrypted when I need to access it.  I've come across plenty of "how-to's" involving dm-crypt, and have successfully encrypted the partition that this directory resides on...

...but the problem is, they all ask for a password & decrypt the partition at boot-up, & since my computer is on all the time, my "encrypted" directory is exposed all the time!

Could somebody here please point me in the right direction?  Please keep in mind that I'm still very much a n00b @ linux, & though I'm learning quickly, I'm going to need something more like a step-by-step, and less like an "in theory" discussion.

Thanks!

Shane

---

### Post by wieman01 on 2006-08-18
The right direction is "Truecrypt":

[http://www.truecrypt.org/downloads.php]("http://www.truecrypt.org/downloads.php")

I am using it in the exact way like you have described... I am only decrypting when I need the files and usually close the archive/container when I go online, etc.

---

### Post by bergersau on 2006-08-18
I use gpg and seahorse and just right click the file/folder to encrypt/decrypt as required.

Suits my needs.

---

### Post by Shane10101 on 2006-08-18
Thanks!  I'd actually just started playing with Truecrypt before I checked back here.  I can't seem to find any linux-centric documentation for it, though.  I have it installed; just can't figure out exactly what to do with it now!  ;)  

If you know of a good "beginner's guide", I'd appreciate a link!

Thanks Again,

Shane

---

### Post by wieman01 on 2006-08-18
I have something for you, but it's in German. I think you would be able to figure it out:

[http://wiki.ubuntuusers.de/TrueCrypt]("http://wiki.ubuntuusers.de/TrueCrypt")

That's the best I can offer. However, should you have problems with the particular commands (e.g. creation of container), let us know. I can help.

---

### Post by wieman01 on 2006-08-18
Perhaps this thread is a good start:

[http://www.ubuntuforums.org/showthread.php?t=228497]("http://www.ubuntuforums.org/showthread.php?t=228497")

---

### Post by mannheim on 2006-08-18
An alternative is EncFS, which is in the repositories. There's a HowTo in the Ubuntu forums [here]("http://www.ubuntuforums.org/showthread.php?t=148600").

---

### Post by 454redhawk on 2006-08-22
> **Shane10101 said:**
> Thanks!  I'd actually just started playing with Truecrypt before I checked back here.  I can't seem to find any linux-centric documentation for it, though.  I have it installed; just can't figure out exactly what to do with it now!  ;)  

If you know of a good "beginner's guide", I'd appreciate a link!

Thanks Again,

Shane

This is how I do it on Mepis. It should be the same for Ubuntu.

Basic install and use of Truecrypt on MEPIS 6

[http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/)

TrueCrypt is a software system for establishing and maintaining an on-the-fly-encrypted volume (data storage device). On-the-fly encryption means that data are automatically encrypted or decrypted right before they are loaded or saved, without any user intervention. No data stored on an encrypted volume can be read (decrypted) without using the correct password/keyfile(s) or correct encryption keys. Entire file system is encrypted (e.g.., file names, folder names, contents of every file, free space, meta data, etc).

Truecrypt now has a .deb that you can directly install on mepis. Use the Ubuntu 6.06

Download and install at.

[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

This is really easy and anyone of you can do it.

Ok, so you just installed it and want to know what it is and how it works.

If you have used Truecrypt in windows you know it has a GUI. As of yet we dont have that in linux so its command line interface for us. No big deal as it requires very little interaction.

1.TrueCrypt requires administrator (root) privileges. If you intend to
use TrueCrypt from a user account, you should execute the following command
as root in a terminal. This will only have to be done once. Use sudo in ubuntu

```
chmod u+s /usr/bin/truecrypt
```

2.Next we want to create a TrueCrypt volume (contanier for our encrypted files)
you can make this container any size you want.

	```
truecrypt -c /home/454redhawk/filename
```

	Replace 454redhawk and filename with what ever you want. In windows I used to stash the 	container in the service pack files DIR and give it a name that looked like a windows system 	file (system.sys). You can name it and place it where ever you want.

	You can just follow the prompts from here or continue along if you want.
	If you follow the prompts on your own skip down after you finish making the volume
	to see how I made it easy to mount and unmount the Volumes.
	

	TrueCrypt will now ask what kind of volume you want to create. Just hit the enter key to accept  	the default normal volume.
	It will then ask what type of file system to create. again just hit the enter key to accept the 	default FAT.
	Now it wants to know whast size volume you want to make. For example type 200K or 100M 	or 5G
	 Its just the number of (K)kilobytes, (M)megabytes or (G)gigabytes.
	
	Now it will ask for the Hash algorithm. You can pick your own or hit enter to accept the default.
	
	Next it asks for the Encryption algorithm. Again pick your own or hit the default enter.

	Now it wants the password for the container. This can be any word or phrase you want.
	You can also include spaces in the phrase. Example &#8220;John has a long mustache&#8221; or &#8220;The chair is against the wall&#8221;

	Ok after you have entered your pass phrase 2 times to confirm the pass phrase it will ask
	for the keyfile path. Hit enter unless you plan to use one. Default is none so hit enter.

	Next you will create some random data by moving your mouse around so hit enter to the prompt
	&#8220;Is your mouse connected directly to computer where TrueCrypt is running?&#8221;
	Now move your mouse wildly all over the screen in a random manner until you reach 100%

	Ok we are almost done don't get discouraged. All of this you could have done without my help 	due to the prompts. I hope I have not insulted you intelligence.

**EASY WAY TO MOUNT AND UNMOUNT**	

I am just a linux beginer and its possible I have done it the hard way but this is what I did and it seems easy to me.
For all I know there is some way that all this is done automagically and I just made it harder for myself. If you know of a better way please let me know.

	The next several steps is what I have done to make it easy to mount and unmount to use your 	newly encrypted container.
	Create a mount point(directory) for the mounted volume. Example /home/454redhawk/your-	mount-	point
	I then created a text file in my /home/454redhawk and called it tcmount
	place this inside of the text file.
	```
#!/bin/sh
truecrypt -u /home/454redhawk/your-trucrypt-file /home/454redhawk/mount-point
```

	Replace 454redhawk and your-trucrypt-file and mount-point with whatever it should be for you.
	Note the space between the word file and /home.

	Save and exit.
	Now right click on that file you just made and choose proerties. Click the permissions tab and 	click &#8220;is Executable&#8221;. Click OK to exit.

	Now make one more text file for the unmount called tcumount. Use the same method as above 	except put this in the file. Don't forget to make it executable.
	
	```
#!/bin/sh
truecrypt -d
```

	
	Now go to your desktop and right click and choose Creat new link to application.
	At the General tab call it TC mount. In the application tab click browse and navigat to your
	tcmount file and select it. Then click on advanced options and select &#8220;run in terminal&#8221;
	Select ok to finish.
	Do the same thing for the tcumount file execpt you don't need to make it run in the terminal.
	

	Now you are ready to mount and use you encrypted container.
	Click the link you made on your desktop for the mount. It will ask for your password and close 		after you type it in. It should now be mounted and you can copy and delete files to that location 	just like from any other folder.

	When you are finished working on that volume click the umount link on the desktop and the 	volume will be unmounted. You can navigate to that location after you do this to verify nothing 	is there.

	Just to make it even eaiser I created a link to URL on my desktop to the trucrypt volume mount point and gave it a nice looking drive icon.

---

### Post by Shane10101 on 2006-08-24
Excellent -- thank you all for the replies.  I've been side-tracked with a couple other projects (finishing up an Ubuntu box for my dad, among them), but I'll be getting back to the encrypted partition stuff this weekend.  (Expect more questions to come ;)  

I'm wondering whether TrueCrypt will let me share an encrypted partition between Dapper & XP on my dual-boot box.  I'm sure that info is on their website; I'll go take a look & let you all know how it goes.

:)

Shane

---

