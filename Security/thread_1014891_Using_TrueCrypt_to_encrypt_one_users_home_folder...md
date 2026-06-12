---
title: "Using TrueCrypt to encrypt one users home folder..."
date: 2008-12-18
forum: Security
---

### Post by ragtag on 2008-12-18
Hey,

 This was something handy I discovered yesterday that I thought I might share. I'm running Ubuntu 8.10, but it might work fine with other versions too.

 If you have a user on your laptop, such as one you use for work related material, that you want to secure...but you don't want to encrypt the whole drive, this is for you.

 Quickly and not in too much detail you can do the following:
  - create a new user (let's call him or her 'work')
  - download and install [TrueCrypt]("http://www.truecrypt.org/"). There is a .deb package for it that's easy to install.
  - create an encrypted file/disk image (not partition). You'll find the instructions for how to on the web. Make it ext3.
  - in my case I called the file workimage.tc and placed it in /home, but you can place it anywhere as long as the 'work' user owns it and can read and write to it.
  - edit /etc/gdm/Init/Default  after:
```

#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH=/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH
OLD_IFS=$IFS

```
...add the line:
```
truecrypt /home/workimage.tc /home/work
```

 Now when you boot the computer, just before the login screen you'll get a popup asking you for the password for workimage.tc (it also asks when switching users...or complain that it's already mounted if it is). Pressing Cancel on the password prompt will go on to the login screen, letting you use the other users without mounting the truecrypt image.

 It's pretty easy to setup, and lets you run a mix of encrypted and non-encrypted users on the same machine.

 It is not 100% secure though, as you're only encrypting that users files and settings, and not your logs or swap space. For that you would need whole drive encryption. The 'work' folder itself should be 99.99% secure provided you've used a long random password (and nobody captures you and tortures the password out of you). :evil:

 Hope someone finds this usefull...

):P

---

### Post by deadtom on 2008-12-18
Sweet!
I was messing with this idea a few months ago and couldn't make it work.
Thanks for the tip!

---

### Post by yogo on 2008-12-18
How does this differ from requiring a password at login?

---

### Post by deadtom on 2008-12-18
> **yogo said:**
> How does this differ from requiring a password at login?
The password is not for authentication, it's needed to decrypt the "work" user directory. If you don't want to log in as that user, simply don't put in that password and the work user directory remains encrypted while you log in as a different user.

---

### Post by hyper_ch on 2008-12-18
why not just simply use full disk encryption?

---

### Post by ragtag on 2008-12-18
If you have an installed and configured system and don't want to install the whole thing again, encrypting just the user folder could be a way to do it. That was my reason for trying it anyway, that and curiosity.

Other reasons might be perforamnce, doing it this way lets you pick between security and performance. Log in as the encrypted user for the secure stuff, and as an ordinary user for performance. And if you share the computer with others, and you want to keep your stuff private I guess. :)

---

### Post by hyper_ch on 2008-12-18
> **ragtag said:**
> Other reasons might be perforamnce, doing it this way lets you pick between security and performance. Log in as the encrypted user for the secure stuff, and as an ordinary user for performance.
only problem is that there will be parts saved that are unencrypted...

---

### Post by ragtag on 2008-12-18
Yes, that's true. If you want high security, you should encrypt the whole drive, swap and all.

---

### Post by jasreca on 2009-05-20
I did exactly the same thing and it serves my purporse, however, I would like tc to unmount after I log off or on shutdown (seems kinda messy to leave volumes mounted during shutdown).

Does anyone know where to put "truecrypt -d" to do this? 

PostSession folder in /etc/gdm doesn't work, as it gets executed while the user is still logged in...

---

### Post by khelben1979 on 2009-05-20
I'm still not sure if TrueCrypt is safe to use. Is it?

---

### Post by jasreca on 2009-05-22
> **khelben1979 said:**
> I'm still not sure if TrueCrypt is safe to use. Is it?

Depends on what you mean by "safe"? :) I think with a right encryption algorithm and a strong password/keyfile, it should offer a decent amount of security...

---

### Post by Minn3h on 2010-09-27
I'm trying to do this on 10.04 and it's not working. I've added the "truecrypt ..." line to the Default file per the directions, but I get no prompt or any sign that anything is different when restarting. 

Any ideas?

---

### Post by Minn3h on 2010-09-27
I solved the first problem. The trouble was that I installed the command-line only package, obviously nothing was going to pop up. So I passed the answers to all the mount questions as parameters.

Now some odd things are happening (like the gnome panel not functioning) when using the encrypted home folder. I suspect some permission issues, I'll be doing some more investigating.

---

### Post by Minn3h on 2010-10-05
I booted a live cd and mounted the partition containing /home and the truecrypt container. Then rsync'ed my existing home folder to the encrypted volume. On restart the previous strangeness was gone. I guess running rsync on an in-use home folder doesn't work (who woulda guessed).

---

### Post by ragtag on 2010-10-05
Ubuntu 10.04 supports encrypted home folders out of the box (though not using TrueCrypt). All you need to do is pop open System>Users and Groups, hit the Add button, enter your name and check "Encrypt home folder to protect sensitive data". You can also during the initial install of Ubuntu 10.04, when you create the first user.

I don't know if you can convert an existing users account to encrypted, but it wouldn't be to hard to copy files across afterwards and chown them.

I don't know how secure this is compared to the TrueCrypt method, but as has been pointed out in this thread neither method is 100% secure, as swap and other parts of the system are not encrypted. If you want that, you're better of encrypting the whole drive, which I believe you can still do with the alternate cd (only tried it with earlier versions of Ubuntu).

 Cheers.

---

### Post by Minn3h on 2010-10-05
A little step-by-step tutorial for the process I used (Ubuntu 10.04 x64):

Download the appropriate Standard Linux package for TrueCrypt from: [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)

This process can be done using the console package, but requires saving the encryption password in plaintext nullifying any improvement in security. (Of course there's probably a way to pass the password not in plaintext that I didn't discover.) 

Extract the archive:
```
tar -xzvf truecrypt-7.0a-linux-x64.tar.gz
```

For some reason I had to make the file executable:
```
chmod u+x truecrypt-7.0a-setup-x64
```

Run the installer
```
./truecrypt-7.0a-setup-x64
```

Follow the simple installation procedure, then create your encrypted volume:
```
truecrypt -c
```

Now we need to copy your existing home folder into the encrypted volume, but we can't do that while you're logged in. If you already have another admin user you can log in to skip this step. Otherwise let's make a new user and allow it to sudo.
```
adduser tempuser
adduser tempuser admin
```

Log out and log back in as the new user or hit ctrl+alt+f1 to go straight to the commandline. 

Next we'll relocate your home folder and then recreate it, but now empty (to serve only as a mountpoint for the encrypted volume).
```
sudo mv /home/<user> /home/backup
sudo mkdir /home/<user>
```

Now we need to copy your home folder data into the encrypted volume. First mount the encrypted volume.
```
sudo mkdir /mnt/tmp
truecrypt –mount
```
Now copy the data.
```
rsync -aHv /home/backup/ /mnt/tmp
```

Unmount the encrypted volume.
```
truecrypt -d
```

Almost there, now we add the instructions for your encrypted volume to be mounted when gdm starts. Edit the gdm init script
```
sudo vi /etc/gdm/Init/Default
```

Insert the following code with your username and path to your encrypted container inserted. I've added a check to make sure the volume isn't already mounted, otherwise gdm was hanging on startup for me when it crashed or I had to restart it. (I put these lines directly above "exit 0".)
```
if !(echo `mount` | grep -q "/home/<user> type")
then
        truecrypt <path to encrypted volume> /home/<user>
fi
```

Finally you can restart gdm and see if it worked. (If you don't get any errors then it worked, the idea is that everything SHOULD look the same.)
```
sudo service gdm restart
```

There's some final cleanup worth doing. 
1.	If everything is working you should “sudo rm -rf /home/backup” since having an unencrypted copy of files you've just encrypted is silly. If you're really worried you could copy those files off to some other secured backup medium. 
2.	We also have created an extra admin account which you might want to remove (though it's generally a good idea to have a backup admin account).

---

### Post by Minn3h on 2010-10-05
> **ragtag said:**
> Ubuntu 10.04 supports encrypted home folders out of the box (though not using TrueCrypt). All you need to do is pop open System>Users and Groups, hit the Add button, enter your name and check "Encrypt home folder to protect sensitive data". You can also during the initial install of Ubuntu 10.04, when you create the first user.

I would have just done that but I wanted cross-platform compatibility for the encrypted volume.

Also, thanks for the inspiration from your initial post!

---

### Post by BkkBonanza on 2010-10-05
Ideally there would be a pam module for handling the password/login. If the pam_ecryptfs one could be modified or used as is for Truecrypt then you could achieve the same integration at login.

Also, potentially gpg could be used to wrap the Truecrypt password with your normal login password so that the login process uses gpg to unwrap the Truecrypt password and open the volume. 

By integrating with pam it would allow unmounting at logout as well. I don't have time today to look into this but I'm pretty sure it's doable.

I've been running swap-less for a while now and as long as you have  ample memory it seems to work just fine. This removes the potential for data being left behind in swap.

I don't know that Truecrypt offers better encryption than ecryptfs but it does have the deniability factor and perhaps that could even be integrated with pam so that dual login passwords result in differing home mounts. And it does work a bit differently in that ecryptfs encrypts file by file with encrypted filenames, whereas Truecrypt would use a volume that is a bit more opaque regarding contents.

---

### Post by Minn3h on 2010-10-06
> **BkkBonanza said:**
> Ideally there would be a pam module for handling the password/login. If the pam_ecryptfs one could be modified or used as is for Truecrypt then you could achieve the same integration at login.

By integrating with pam it would allow unmounting at logout as well. I don't have time today to look into this but I'm pretty sure it's doable.

I've seen some discussions to that effect, but none that were particularly recent or clear enough for someone like me who knows nothing about pam authentication. 

> Also, potentially gpg could be used to wrap the Truecrypt password with your normal login password so that the login process uses gpg to unwrap the Truecrypt password and open the volume.

I hadn't thought of that. I'll look into it and see if I can incorporate it.

> I've been running swap-less for a while now and as long as you have  ample memory it seems to work just fine. This removes the potential for data being left behind in swap.

I as well, swap is such a relic.

> I don't know that Truecrypt offers better encryption than ecryptfs but it does have the deniability factor and perhaps that could even be integrated with pam so that dual login passwords result in differing home mounts. And it does work a bit differently in that ecryptfs encrypts file by file with encrypted filenames, whereas Truecrypt would use a volume that is a bit more opaque regarding contents.

Between cross-platform support and the significant additional paranoia factor in TrueCrypt's design it's a no-brainer for me.

---

### Post by KegHead on 2010-10-06
Hi!

I've used truecrypt for about a year and feel very safe.

It would take years to crack open my file.

KegHead

---

### Post by ionutt on 2012-10-11
This above tutorial is not working anymore since ubuntu 11.10 and above uses lightdm instead gdm. I am posting this tutorial for Ubuntu 12.04 and for anyone who needs ubuntu + truecrypt + home folder encrypted.

My home folder is /home/ionut
My truecrypt drive is /home/drive

Install truecrypt. 

```

sudo apt-add-repository ppa:michael-astrapi/ppa && sudo apt-get update && sudo apt-get install truecrypt

```Start truecrypt and create your volume.

I created my volume in /home. The name of my volume is drive. This is my path for drivecrypt volume: /home/drive.

Mount your new created volume

```

sudo mkdir /mnt/tmp
truecrypt /home/drive /mnt/tmp

```Copy all our data from your home profile, mine is /home/ionut to mnt/tmp

 
```

rsync -aHv /home/ionut/ /mnt/tmp

```Delete everything in your home folder
```

rm -rf * .*

```Then we need to create this script

```

sudo nano /usr/share/truecrypt.sh

```Add these lines to your truecrypt.sh

```

if !(echo `mount` | grep -q "/home/ionut type")
then
        truecrypt /home/drive /home/ionut
fi

```Replace /home/drive and /home/ionut with your own volume and home directory paths.

Don't forget to add permisions for your truecrypt.sh file

```

chmod a+x /usr/share/truecrypt.sh

```Now we edit lightdm.conf

```

sudo nano /etc/lightdm/lightdm.conf

```Under 
```

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu

```we add this line
```

display-setup-script=/usr/share/truecrypt.sh

```If you want to disable guest account, as I did add also the following line to the lightdm.conf

```

allow-guest=false

```So /etc/lightdm/lightdm.conf should look like this:

```

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
allow-guest=false
display-setup-script=/usr/share/truecrypt.sh

```

Restart and test.

Now if you did everything as above you should be asked for truecrypt password before logon screen. Feel free to correct me if I'm wrong.

Hope it helps.

---

