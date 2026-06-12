---
title: "CD rippers"
date: 2007-04-08
forum: The Cafe
---

### Post by smbm on 2007-04-08
Hi

Does anyone know of any GTK2 CD rippers that don't depend on Gnome?

GRIP and Sound Juicer seem to need to pull in loads of Gnome libs when I try and install them on Xubuntu.

At the moment I'm using abcde but would like a GUIfied ripper if possible.

Thanks

---

### Post by tbroderick on 2007-04-08
Why? adcde is great.

---

### Post by smbm on 2007-04-08
I know, I really like it but I'm not the only one using the computer and some other people "can't figure out that stone age technology where you have to type things" sadly.

---

### Post by aysiu on 2007-04-08
Try Goobox

---

### Post by smbm on 2007-04-08
Cheers for the suggestion.

I checked it out, sadly Goobox tries to pull in all the aforementioned Gnome dependencies.

Thanks anyway.

---

### Post by aysiu on 2007-04-08
If you don't want *any* Gnome dependencies, why do you want a GTK application? Why not something like KAudioCreator? Is it bad to have one Gnome-related library on a Xubuntu installation?

---

### Post by aysiu on 2007-04-08
How about [Asunder?](http://ericlathrop.com/asunder/)

There's no .deb, but you may be able to *alien* the SuSE RPM.

```
wget -c http://ftp.gwdg.de/pub/linux/suse/apt/SuSE/9.2-i386/RPMS.suser-oc2pus/Asunder-0.1.0-0.oc2pus.2.i586.rpm
sudo apt-get update
sudo apt-get install alien
sudo alien -i Asunder-0.1.0-0.oc2pus.2.i586.rpm
```

---

### Post by smbm on 2007-04-08
> **aysiu said:**
> If you don't want *any* Gnome dependencies, why do you want a GTK application? Why not something like KAudioCreator? Is it bad to have one Gnome-related library on a Xubuntu installation?

I see where you're coming from. It's not the end of the world I guess. I'm just not too keen on installing a whole (or half an) other desktop environment just for a cd ripper. 

If I have to I will though I'm not *that* opposed to it.

Grip seems to have the least Gnome dependencies.

---

### Post by smbm on 2007-04-08
Asunder looks perfect.

You're the best.

I'll let you know how I get on.

---

### Post by aysiu on 2007-04-08
Yes, please do report back.

By the way, just because you see some Gnome-related libraries doesn't mean you're installing a huge chunk of an entire desktop environment. Most GTK-based applications have some Gnome-related dependencies.

---

### Post by smbm on 2007-04-08
Alien doesn't seem to like this rpm.

```
tom@destroyer:~/Desktop$ sudo alien -i Asunder-0.1.0-0.oc2pus.2.i586.rpm 
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
argument is not an RPM package
argument is not an RPM package
cpio: premature end of archive
chmod: invalid option -- /
Try `chmod --help' for more information.
error: open of <!DOCTYPE failed: No such file or directory
error: open of <!DOCTYPE failed: No such file or directory
mkdir: invalid option -- /
Try `mkdir --help' for more information.
-/debian/changelog: No such file or directory at /usr/share/perl5/Alien/Package/Deb.pm line 330.
find: invalid predicate `-'
```


I might try building it from source tomorrow.

It's a little to here late at the moment for that kind of antics.

I see what you're saying about the Gnome libs. I just want to see if there's a more light weight alternative but which still has a gui.

If I can't get Asunder working I'll most likely install GRIP.

Personally I'm starting to get really into command line apps. Am already using abcde and ncmpc myself and am investigating mutt. 

I really appreciate your help though.

---

### Post by tbroderick on 2007-04-08
Try gnormalize. There is a debian package linked from their homepage. It's a gtk2-perl frontend to cdparanoia, lame, oggenc, faac, flac, etc. So there are no gstreamer or gnome-libs depends.

[http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)

---

### Post by andrew.46 on 2007-08-17
Hi,

 Saw a passing reference to mutt:

> **smbm said:**
>  Am already using abcde and ncmpc myself and am investigating mutt. .

 You may be interested in a guide that I have written for Ubuntu and mutt at:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

               Andrew

---

