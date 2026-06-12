---
title: "Places --&gt; Home Folder equals (by mistake) Places --&gt; Desktop"
date: 2010-06-06
forum: System76 Support
---

### Post by watchpocket on 2010-06-06
Suddenly, my "Places --> Desktop" folder is identical to my "Places --> Home Folder".

This somehow happened by mistake, and the folders and files in my Home Folder "/home/rj" are displayed on my desktop, and I don't want them to be.

When I click on "Places --> Desktop" it's as if I've clicked on "Places --> Home Folder" (the "File Browser" directory opens, the location is set at "/home/rj", and the title at the top is "File Browser").

This may seem like elementary stuff to a lot of you, but I'm blanking on how the Desktop folder can be restored to what I'd like it to be (basically empty, except for a "Downloads" folder), and my folders and files kept off the actual desktop (except for the "Downloads" folder).

---

### Post by PatrickVogeli on 2010-06-07
in gconf-editor:

apps > Nautilus > Preferences > desktop_is_home_dir

---

### Post by watchpocket on 2010-06-07
> **PatrickVogeli said:**
> in gconf-editor:  apps > Nautilus > Preferences > desktop_is_home_dir

Thanks for the response, but the only thing I have in 

 .gconf/apps/nautilus/preferences/

is a file named %gconf.xml, and it doesn't have a "desktop_is_home_dir" entry. . . .

---

### Post by isantop on 2010-06-07
Here, to clarify:

Press Alt-F2 and type gconf-editor.

On the left, navigate to Apps/Nautilus/Preferences.

Then, on the right, look for an entry called "desktop_is_home_dir". It has a checkbox next to it. Make sure that the check box is not checked.

That should clear your problem. You may need to log out then log back in again to make the change effective, but the two should now be separate.

---

### Post by watchpocket on 2010-06-09
> **isantop said:**
> Then, on the right, look for an entry called "desktop_is_home_dir". It has a checkbox next to it. Make sure that the check box is not checked.

Thanks for the tip.  "desktop_is_home_dir" was already UN-checked and remains so, but I still have some of the files and folders (from my home dir) displayed on the desktop.

---

### Post by isantop on 2010-06-10
If you make a change to one of the folders on the desktop, is it reflected in the folder in the home folder?

---

### Post by watchpocket on 2010-06-11
> **isantop said:**
> If you make a change to one of the folders on the desktop, is it reflected in the folder in the home folder?

Looks like it is:  From the desktop, I put a file that appeared on the desktop into one of the folders on the desktop.

I also changed the name of another folder.

Both things were done on the desktop, then I opened the home folder and what I'd done on the desktop had been done there as well.

---

### Post by isantop on 2010-06-11
It sounds like a problem with symlinks. Is there an entry in your home folder named "Desktop"?

Is it also mirrored on your desktop?

---

### Post by doas777 on 2010-06-11
It may be easier to track this via the command line
try running 
```

ls -al ~
ls -al ~/Desktop

``` and compare the two. that should show you what is there, and what is symlinks, as well as taking any uncertianty about the places menu out of the equation.

---

### Post by watchpocket on 2010-06-11
> **isantop said:**
> It sounds like a problem with symlinks. Is there an entry in your home folder named "Desktop"

No there isn't.  Not with any similar name, either (i.e., no ".Desktop" or ".desktop" or "desktop".

> Is it also mirrored on your desktop?No such entry or name on the desktop itself either.

About all I can say about this is that I first noticed it after an hour or so of scanning images with a new scanner where, instead of naming the images directly into a pix folder in my home folder (which would have saved me time, just hadn't thought of it yet) I was creating names in xsane in a directory path putting the image file in my home dir.

So I had one file browser window open to the home dir, and a second file browser window open to the pix folder, and was moving each image as it was created from the home folder into the pix folder (which was inside my home dir)  in the other file browser window.   (Later a light bulb went off illuminating how dumb & unneccessary  that was.)

(Edit: Actually I was moving images into a few different "pix-category" folders, so it wasn't as dumb as I just said having all the image-files go into the home folder and moving them from there into a more specific "pix"-type subfolder.)

Then I went back to my desktop and suddenly saw the files & folders there.  What's there are all the NON-dot folders and non-dot files from my home dir.

---

### Post by watchpocket on 2010-06-11
> **doas777 said:**
>  . . . try running 
```

ls -al ~
ls -al ~/Desktop

``` and compare the two. that should show you what is there, and what is symlinks, as well as taking any uncertianty about the places menu out of the equation.

```
--> ls -al ~/Desktop
ls: cannot access /home/rj/Desktop: No such file or directory
```Further to my previous post, although just the non-dot files and folders actually appear (as icons) on the desktop, when I open the file browser to either "Places --> Home Folder" or "Places --> Desktop", they are identical in that they both contain ALL files and folders (dot and non-dot).

---

### Post by doas777 on 2010-06-12
well, it sounds like the system is using your home for your desktop, even though the setting in gconf editor says otherwise. weird.
so is there a folder on your desktop called 'Desktop'?
if not, try creating one 
```
mkdir ~/Desktop
```
and reboot (theoretically a logout would do it)
just a hunch. prolly not right, but worth a try.

---

### Post by watchpocket on 2010-06-12
So I created a "Desktop" subdirectory with ```
mkdir ~/Desktop
``` and that put a "Desktop" folder icon on the desktop, but everything else is the same, i.e., same problem with the non-dot files & folders appearing on the desktop where I don't want them to.

I don't have -- and haven't had -- any symbolic links at all in my home dir.

---

### Post by watchpocket on 2010-06-14
Still trying to resolve this.

For now I've put a folder named "Desktop" in my home dir, and I've put all the files and folders that were appearing on the desktop itself (they're the non-dot files & folders only) in that folder, and I'm reading through

<http://library.gnome.org/users/user-guide/stable/index.html.en>

And xdg-user-dirs (which I had to re-install) hasn't help much yet.

---

### Post by isantop on 2010-06-14
[COLOR="Gray"]Hmm. There should be an entry there, at least in the file browser. I suspect that something xsane did on accident was to move your desktop to your home folder and Delete your desktop folder. Now, Nautilus is only using your home folder as a fallback, since your ~/Desktop folder doesn't exist.

Try opening your home folder in Nautilus and making a new folder called "Desktop". It may be case-sensitive. You may need to log out and log back in again for the change to register.[/COLOR]

EDIT: I see the other replies. I'll look in to that too. You might try checking that Gconf Key again, too.

---

### Post by watchpocket on 2010-06-19
Turns out that putting all those non-dot files and folders that were on  the desktop into a** folder** on the desktop (which is a subdir of my  home dir) messes up certain programs (like slrn and sipie) that need to  find those files/folders in the home dir, and not in a subdirectory  thereof.

So for now I've put all the files/folders [COLOR=Black]**back**[/COLOR]  on the desktop and will just have to leave them there until I figure  out how to keep them **off** the desktop while still keeping them**  in** the home directory.

---

### Post by isantop on 2010-06-22
This should work to solve this problem more effectively:

Make sure you have a folder called "Desktop" (Case Sensitive) in your home folder. Then, run this command:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

That should get you fixed up. you may need to log out then back in for the change to fully register.

---

### Post by watchpocket on 2010-06-22
That fixed it.  I also have, in .config/user-dirs.dirs, this line:

XDG_DOWNLOAD_DIR="$HOME/Desktop/Downloads"

since I want my Downloads folder to show up on the desktop.

---

