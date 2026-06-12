---
title: "Easily encrypt folders 2"
date: 2012-09-05
forum: Tutorials
---

### Post by Dreamsorcerer on 2012-09-05
**Original**: [blog.sambull.org]("http://blog.sambull.org/easily-encrypt-folders-2")

Encfs is a program that can be used to encrypt folders, unlike other encryption methods this doesn't require a file of a fixed size, so you can use the decrypted folder in the same way as a regular folder without worrying about space.

This tutorial will explain how you can use a plugin as a convenient way to use this tool.

**Pre-installation**
In order to use this plugin you will of course need to install the encfs program first, the easiest way to do that (on Ubuntu) is to try clicking this link:
[apt:encfs](apt:encfs)

or copy this into a terminal:
```
sudo apt-get install encfs -y
```In addition to this we will be using gnome-encfs, a small program that allows you to use the gnome-keyring to store encryption passwords. This program by Oben Sonne can be found [here]("https://bitbucket.org/obensonne/gnome-encfs/"); after downloading it, extract the gnome-encfs file to your home folder.

Then to install it run:
```
sudo install gnome-encfs /usr/local/bin
```[B]

Installation[/B]
To install the actual plugin simply open a terminal and copy & paste these commands (the plugin can also be found attached to this post):
```
sudo apt-get install python-nautilus
mkdir -p ~/.local/share/nautilus-python/extensions/
cd ~/.local/share/nautilus-python/extensions/
wget http://sambull.org/downloads/encrypt-nautilus.py
chmod a+x encrypt-nautilus.py
```If you want to try this out immediately, press Alt+F2 and enter "nautilus -q", then repeat and enter "nautilus", otherwise it will be available next time you login.

**Usage**
I'll give a little example here to demonstrate how this is used. Let's say your Pictures folder contains some naughty images and you'd like to encrypt the entire folder.

[[IMG]http://blog.sambull.org/wp-uploads/usage0.png[/IMG]]("http://blog.sambull.org/wp-uploads/usage0.png")[INDENT]*The contents of my Pictures folder.*
[/INDENT]**Encrypting**
Simply right-click and select 'Encrypt folder using EncFS'. A window will now pop-up asking for the name of the folder where the decrypted contents will be displayed, I'll use *pictures-decrypted* for this, but you can use any name you like.

[IMG]http://blog.sambull.org/wp-uploads/usage1.png[/IMG][INDENT]*Naming the decrypted folder.*
[/INDENT]It will then ask if you want to have it automatically mount at login, this will allow you to have it always decrypted for you, but make sure nobody else will be able to see the contents without logging in.

You will then see a new folder has been created, in my case it's called pictures-decrypted. This new folder is the decrypted contents of the Pictures folder. If you add any new files, you need to save them into this decrypted folder, they will then automatically be encrypted.

[IMG]http://blog.sambull.org/wp-uploads/usage2.png[/IMG][INDENT]*The folders after decrypting.*
[/INDENT]**Unmounting**
Simply right-click *pictures-decrypted* and select 'Unmount EncFS folder'. The decrypted folder should now have vanished.

If you look in the Pictures folder you will see that the contents are all encrypted and you will be unable to view any of the files.

[IMG]http://blog.sambull.org/wp-uploads/usage3.png[/IMG][INDENT]*With the contents encrypted nobody will be able to view them anymore.*
[/INDENT]**Auto-mount tip**
If you are going to auto-mount the folder on login, then you could rename the encrypted folder to something like *.pictures-encrypt* (the . makes it a hidden folder). Then when you make it encrypted, you can name the decrypted folder Pictures, so the encrypted folder remains hidden, and the decrypted folder acts like your normal pictures folder.

**Extension**
I've written a follow-up post to this one that explains how this can be used to encrypt Firefox data seamlessly. You can read it [here]("http://blog.sambull.org/encrypt-firefox/").

---

