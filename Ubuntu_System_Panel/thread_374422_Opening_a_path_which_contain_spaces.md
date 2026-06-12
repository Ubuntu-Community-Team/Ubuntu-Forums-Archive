---
title: "Opening a path which contain spaces"
date: 2007-03-02
forum: Ubuntu System Panel
---

### Post by Prism on 2007-03-02
Hi there,

I have a Shortcuts plugin which has one shortcut to the path "/media/sda4/My Documents". When I try to open it via the plugin, I get two error messages saying "Couldn't find "/home/tomer/Documents"." and "Couldn't find "/media/sda4/My"."

Is that a known bug?

Thanks.

---

### Post by steve101101 on 2007-03-02
> **Prism said:**
> Hi there,

I have a Shortcuts plugin which has one shortcut to the path "/media/sda4/My Documents". When I try to open it via the plugin, I get two error messages saying "Couldn't find "/home/tomer/Documents"." and "Couldn't find "/media/sda4/My"."

Is that a known bug?

Thanks.

I dont know of any bug. But I believe that if you type this it might work. its worth a try....

/media/sda4/"My Documents"

that it how it used to be done in windows.

---

### Post by Malac on 2007-03-02
> **Prism said:**
> Hi there,

I have a Shortcuts plugin which has one shortcut to the path "/media/sda4/My Documents". When I try to open it via the plugin, I get two error messages saying "Couldn't find "/home/tomer/Documents"." and "Couldn't find "/media/sda4/My"."

Is that a known bug?

Thanks.
This is due to the split() command being used in the plugin, so it is being divided into "/media/sda4/My" and "Documents" [SIZE=1](which is then looked for in your user directory)[/SIZE].
As a temporary workaround try putting the quotes round it as mentioned above or replace the space with the characters "**%20**"[SIZE=1](without the quotes)[/SIZE]. 
N.B. This has been fixed in the latest SVN version of USP alpha.

Hope this helps.

---

### Post by Prism on 2007-03-03
I'm actually using the latest svn version, and it isn't fixed...

Oh, and I tried now both options, %20 and /media/sda4/"My Documents", and both don't work.

---

### Post by Malac on 2007-03-03
> **Prism said:**
> I'm actually using the latest svn version, and it isn't fixed...

Oh, and I tried now both options, %20 and /media/sda4/"My Documents", and both don't work.
Weird I thought we'd got round to this but then it may have only been in the recent, places/bookmarks and applications plugins.
Having double checked in the Shortcuts plugin my shortcut to my old Windows98 "My Documents" folder looks like this in gedit.
```
[Desktop Entry]
Encoding=UTF-8
Name=My Documents
Comment=
Exec=nautilus file:///mnt/C_Win98/My%20Documents
Icon=gnome-fs-directory
GenericName=
Terminal=False
```

And if you check the edit item in the Shortcuts right-click menu.
It should look something like this:[ATTACH]26557[/ATTACH]
How did you create the shortcut as the drag'n'drop method should give you something like these.

---

### Post by Prism on 2007-03-04
Adding the "file://" prefix helped, thanks. I'm not sure how I've created the original shortcut, probably by nautilus.

---

