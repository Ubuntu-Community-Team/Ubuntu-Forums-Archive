---
title: "Easy Crypt  True Crypt"
date: 2009-12-28
forum: Security
---

### Post by dontgetshocked on 2009-12-28
I am not familiar with this software and could use some help setting it up.I have both True and Easy Crypt installed.I have a netbook that I want make secure so that no one can view or hack it.

---

### Post by gradinaruvasile on 2009-12-28
Its only TrueCrypt. EasyCrypt is only a wrapper for it, i dont see its purpose, its redundant - i suggest use only TrueCrypt, it has all the options you need.

With TrueCrypt you can create virtual volumes that are encrypted. Basically its a big file, and truecrypt mounts it as a partition. It uses high grade encryption, so that there are few chances to decrypt them if you dont know the passwords for them. It can encrypt whole partitions, but only for Windows. 

Easiest is to create a virtual volume, you can use it on any computer that has truecrypt installed, regardless of OS. Put your sensitive data on it and mount it only when you are using the computer, dismount it when you are away.

Use strong passwords - more than 15 characters, with uppercase/lowercase characters, numbers and a few special characters. But be warned that if you forget the password, you are toast because there is no lost password recovery option for security reasons.

---

### Post by dontgetshocked on 2009-12-28
So like encrypt my documents folder and mount it? Could you be a little more specific? I am a little scaredx of messing up.

---

### Post by gradinaruvasile on 2009-12-28
Not that way.
You will have a separate partition (named truecrypt1 by default) that is actually a file (like a iso or something) that is mounted through TrueCrypt. There is nothing changed on your existing files or partitions. Its like you insert an USB stick and write to it and pull it out. Only its done at software level. Make a small test partition first and dont put important files in it.

Also - if you really want security, never use passphrase caching in memory, always type your password and memorize it, dont write it down anywhere. But make sure you remember it.

---

### Post by Soul-Sing on 2009-12-29
You have to read this outstanding documentation: [http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/)

Easycrypt was a frontend/shell for truecrypt when it was a terminal-based prog. It is not needed anymore because truecrypt for linux has a graph. interface like the windows versions.

---

### Post by BkkBonanza on 2009-12-29
While I like Truecrypt and use it for various sets of files in specific cases I don't think it's your best choice for a simple, transparent, basic encryption setup. The problem is that if you're worried about your notebook being stolen/lost then you really want your home directory to be encrypted and it's not as easy to set that up on boot with TC.

The easiest way is to install with the encrypted home option but given that you are already installed and running you can convert your home to encrypted home using the tutorial below. It takes a bit of command line work but it does work. After that you have an encrypted home that uses your normal login password (and a key file that you can place on a usb key if you like) to mount and use.

The main advantage to this is that all your various settings, email, passwords, bookmarks and keys (.ssh, .gnupg) etc. resting in your home will be taken care of by default. A system that works by default is more functional then one where you have to remember things and take special action to use. 

Some people complain about it using your login password but this is an option. You can use a second password if you like or keep the key on a usb thumbdrive for 2-factor authentication.

[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

---

