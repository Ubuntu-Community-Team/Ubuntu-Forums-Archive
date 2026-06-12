---
title: "Make a Dongle to access my Linux install"
date: 2011-04-26
forum: Security
---

### Post by ehime on 2011-04-26
I'm a little security paranoid, there are a lot of times that my terminal is available to prying eyes and listless fingers. As a security minded individual, I would like to make sure to lock down my Ubuntu (11.04b3) install in one of the best ways I can think of, and require a dongle to access my box. Is this something any of you other security minded people have done?

What are other great ways to lock my terminal? I would like to make sure that not only the "average" user, but also the ABOVE average user will not be able to penetrate my system without a key. Let me know what you think, and other measures I can take.

-jd

---

### Post by uRock on 2011-04-26
Encrypt your system and log out when not sitting in front of it.

You can also install a card reader, but I am not sure of the pricing for such toys.

---

### Post by cbowman57 on 2011-04-26
Encrypting your home directory and installing grub & /boot on a usb drive is a step in the right direction but not sure if that meets your needs.

---

### Post by FatalMessenger on 2011-04-26
If I understand what your asking correctly, you're looking for some form of multi-factor authentication that requires a USB key to be plugged in to use your computer, and then when you leave, you remove the USB key, causing you're computer to be unusable until you plug said key back in. Am I correct?

If so, I believe there's a way to do this in ubuntu, but, if I remember correctly, it's added on top of regular login so you would have to remember to log off when you left anyway.

---

### Post by BkkBonanza on 2011-04-27
If you use an encrypted home you can copy the wrapped-passphrase (key) onto a usb dongle and replace the original with a symlink to the dongle location. This requires you know the login password and have the dongle to login. 

The only tricky bit at all is you should add a uuid mount to your /etc/fstab for the dongle so that it always mounts at the same fixed location as otherwise removable media have a tendency to move around when other mounts occur first.

The relevant key file to move and symlink is,

/home/.ecryptfs/<user>/.ecryptfs/wrapped-passphrase

See this tutorial if you need help to convert to an encrypted home,

[http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html](http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html)

-------
If you make your dongle mount at /media/key then the commnds to replace the wrapped passphrase would be,

cd /home/.ecryptfs/`whoami`/.ecryptfs/
mv wrapped-passphrase /media/key
ln -s /media/key/wrapped-passphrase wrapped-passphrase

While the key is mounted type, **blkid** to see  a list of UUIDs. Then assuming the UUID found is eg. b1cab75a-4fcf-4178-a0b0-c01256d785fd add the following mount to your /etc/fstab using nano or whatever editor,

UUID=b1cab75a-4fcf-4178-a0b0-c01256d785fd /media/key ext3 defaults 0 0

(assuming filesystem is ext3 and default options but these can be changed as needed of course)
(you may want the nofail option added so it doesn't give errors if the key isn't there)

---

### Post by bonfire89 on 2011-06-18
> **BkkBonanza said:**
> If you use an encrypted home you can copy the wrapped-passphrase (key) onto a usb dongle and replace the original with a symlink to the dongle location. This requires you know the login password and have the dongle to login. 

The only tricky bit at all is you should add a uuid mount to your /etc/fstab for the dongle so that it always mounts at the same fixed location as otherwise removable media have a tendency to move around when other mounts occur first.

The relevant key file to move and symlink is,

/home/.ecryptfs/<user>/.ecryptfs/wrapped-passphrase

See this tutorial if you need help to convert to an encrypted home,

[http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html](http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html)

-------
If you make your dongle mount at /media/key then the commnds to replace the wrapped passphrase would be,

cd /home/.ecryptfs/`whoami`/.ecryptfs/
mv wrapped-passphrase /media/key
ln -s /media/key/wrapped-passphrase wrapped-passphrase

While the key is mounted type, **blkid** to see  a list of UUIDs. Then assuming the UUID found is eg. b1cab75a-4fcf-4178-a0b0-c01256d785fd add the following mount to your /etc/fstab using nano or whatever editor,

UUID=b1cab75a-4fcf-4178-a0b0-c01256d785fd /media/key ext3 defaults 0 0

(assuming filesystem is ext3 and default options but these can be changed as needed of course)
(you may want the nofail option added so it doesn't give errors if the key isn't there)


This is a really neat idea! Thanks!

I'm not so sure it would work in my situation because this would require you to log off in order lock the machine. Ideally I would be able to lock the screen and then remove the usb key then come back later, plug back in the usb key, then login. But maybe this idea could be applied some other way... Interesting concept, very cool, it's got me thinking. I like this.

---

### Post by crispy_420 on 2011-06-22
Paranoid enough to buy hardware for the task that is OS independent:
[http://www.addonics.com/products/cipher/cipherchain.asp](http://www.addonics.com/products/cipher/cipherchain.asp)

They have a whole ton of similar products:
[http://www.enovatech.net/solutions.htm](http://www.enovatech.net/solutions.htm)

They look promising and you can daisy chain to add layers of AES 256 if you want to go all out.

---

### Post by BkkBonanza on 2011-06-22
> **bonfire89 said:**
> This is a really neat idea! Thanks!

I'm not so sure it would work in my situation because this would require you to log off in order lock the machine. Ideally I would be able to lock the screen and then remove the usb key then come back later, plug back in the usb key, then login. But maybe this idea could be applied some other way... Interesting concept, very cool, it's got me thinking. I like this.

I know when I suspend it locks the folder. Also I think when the screen saver kicks in too but not 100% sure about that as I haven't really tested it fully. But i do notice when the screen saver kicks in you have to provide the password to unlock again (that option is enabled in settings). I would expect the encrypted folder gets locked when the session is locked. You can lock the screen manually with Ctrl-Alt-L (default keybinding). I didn't try switch user to see if the underlying home is truly locked, nor did I try with a usb key to see how it behaves. If implemented correctly it should do the right things.

---

### Post by spynappels on 2011-06-22
Depending on how comfortable you are with PAM, and whether you can get hold of a Yubikey cheaply (they're not expensive even to buy one) you could use it to do what you want to do.

[http://blog.rootshell.be/2009/03/27/yubikey-authentication-on-linux/](http://blog.rootshell.be/2009/03/27/yubikey-authentication-on-linux/) shows how to set it up for authentication and the Youtube video at the bottom of the blog shows it doing exactly what you want it to using udev scripts to lock a Gnome session when the Yubikey is removed and unlock it when re-inserted.

I've not used Yubikey for this application, but have found that the Yubikey OTP works very well.

---

### Post by BkkBonanza on 2011-06-22
Those [udev rules]("http://forum.yubico.com/viewtopic.php?f=11&t=246") mentioned in the article above should also work fine for forcing a lockdown if you removed a usb stick associated with ecryptfs. You would just need to change the rule to match on the uuid of your key instead of vendor id/product id.

---

### Post by Dave_L on 2011-06-22
> **BkkBonanza said:**
> You can lock the screen manually with Ctrl-Alt-L (default keybinding). I didn't try switch user to see if the underlying home is truly locked, nor did I try with a usb key to see how it behaves. If implemented correctly it should do the right things.

[Ubuntu 10.04]

I have an encrypted home directory.  I just locked the screen with Ctrl-Alt-L, switched to another user, and had full access to the first user's home directory with "gksudo nautilus".

That seems to be a limitation of ecryptfs. Once the encrypted directory is mounted (i.e. decrypted), it tends to stay mounted. Even logging out can leave the directory mounted.

---

