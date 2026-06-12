---
title: "File server"
date: 2010-01-30
forum: Server Platforms
---

### Post by jeffrey2009 on 2010-01-30
I am looking to install a file server to store my photos, music, etc.  I have a mix of windows and linux machines.;  Should I use ubuntu or kubuntu I am not sure if I should use (k)ubunut server or regular (k)ubuntu.  I would also like a step by step walk through or tutorial if anyone is aware of anything.

Your help is greatly appreciated.

Regards,

Jeffrey

---

### Post by artheus on 2010-01-30
Hey there Jeffrey!

Is the server just going to stand there, or are you going to use this machine for anything more?

Cause if it's just going to stand there all alone, you can install Ubuntu Server, And you will not really need KDE or GNOME.
But if you're going to use it as a Desktop computer and want a Desktop/window manager you can install either one.. It's just a matter of personal taste.

It's more of a visual difference than anything else.

You can google for images on KDE or GNOME and see which one you like the most. KDE = Kubuntu, GNOME = Ubuntu.

Then after installing the server OS, go to the terminal window and follow theese instructions:

write
```
sudo apt-get install samba
```

You will have to enter password!
When the installation has finished you write

```
sudo nano /etc/samba/smb.conf
```

then press 'Page Down' until you're at the bottom of the document.

And there you input something like this

```
[export]
	path = /export/data
	comment = Export
	browseable = yes
	read only = no
	guest ok = no
	create mask = 775
```

At least that is my configuration for the path /export/data.

the [export] part is the name of the shared folder, so you can call it whatever you want. Like [mysharedfoler] or something.

And the settings under there, I feel is quite self-explaining.

Ctrl+X to exit, Y to save and N to exit without saving.

then run this command

```
sudo /etc/init.d/samba restart
```

And then you should be all set.

Try finding your shared folder on the network. I should have the name you put in to the []-brackets.

Cheers,
Artheus

---

### Post by jeffrey2009 on 2010-01-30
Awesome, thank you.  I already have an ubuntu with gnome so this one is purely a server.  So I will go ahead with the server install instead of a normal ubuntu install.  I guess there would be no difference between ubuntu and kubuntu in that case since no front end.  I should have figured that one out.  Thanks for the instructions, I will go through them and reply if there are any questions of issues.

---

