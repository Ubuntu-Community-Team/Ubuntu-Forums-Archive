---
title: "Set permissions for NEW files and folders"
date: 2011-03-14
forum: Security
---

### Post by teocomi on 2011-03-14
Hello, I'm sorry if this is a stupid question but I've been googling it for a long time and I did not find it out..

Well I have a shared partition on Ubuntu, 'dm-6', if I create a new folder in it, it has 'teocomi' as owner.

If I create the folder from another (windows) PC the owner is 'nobody' and from Ubuntu I have to chmod/chown it in oredr to edit its content...

Is there a way to set automatically permission and owner for newly created folders and directories?

I tryed with:

```
sudo chmod u+s -R  /media/dm-6
```

But it did not work...
Thanks!

---

### Post by Morbius1 on 2011-03-14
Although you never actually stated this it sounds like you created a Samba share and are allowing guest access. A remote guest user will save a file with owner:group = nobody:nogroup.

If you're the only user then the easiest thing to do is add a line to /etc/samba/smb.conf:
```
force user = teocomi
```Where you put that line depends on what samba method you used to create the share - there are two methods.

If you only have one share then add the line in the [global] section of smb.conf. If you have multiple shares with different authentication schemes then post the output of the following commands so we can see how you are set up:
```
net usershare info --long
testparm
```

---

### Post by teocomi on 2011-03-14
Great THANKS! That was the point ;)

---

### Post by doas777 on 2011-03-14
but as an aside, you attempted to setUID on the folder, no? 
I recommend using setGID instead, so that users can own their own files and I can use sticky, but still get all the benifets of group ownership (except delete/rename of course)

---

### Post by Morbius1 on 2011-03-14
But he wants to edit the contents of the remotely saved files so he would have to change the umask to 002 in order for every new file to save as 664 instead of 644. Can be done with little effort of course.

Had he used classic-samba he could also have forced the group and permissions of the saved files without any modification to the Linux permissions. I always assume for some reason that most users use Nautilus to share directories.

---

### Post by teocomi on 2011-03-14
Yeah I tried both setUID and setGID but the when I created a new folder the owner was still "nobody".. 

Excuse me if I wasn't clear enough but this is just my second day with Linux (I just have a vague idea of what Nautilus is)! :D

And BTW if you have any better idea on how to share files to Window PCs in my network, they are welcome! ;)

---

