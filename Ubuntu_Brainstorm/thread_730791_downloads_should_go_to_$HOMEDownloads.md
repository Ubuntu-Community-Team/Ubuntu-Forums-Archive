---
title: "downloads should go to $HOME/Downloads"
date: 2008-03-21
forum: Ubuntu Brainstorm
---

### Post by ubuntu_demon on 2008-03-21
downloads should go to $HOME/Downloads. XDG_DOWNLOAD_DIR should be set to "$HOME/Downloads" instead of "$HOME/Desktop" in the file ~/.config/user-dirs.dirs.

This Downloads folder should be the default download location for firefox and this folder should be bookmarked in nautilus by xdg-user-dirs-gtk (like Music,Videos,Pictures and Documents).

RATIONALE :
* less cluttered desktop
* still easy to access your downloads

launchpad :
[https://bugs.launchpad.net/bugs/204567](https://bugs.launchpad.net/bugs/204567)

ideastorm :
[http://brainstorm.ubuntu.com/idea/5281/](http://brainstorm.ubuntu.com/idea/5281/)

---

### Post by imT on 2008-03-21
i think it's fine just how it is right now, and if you want a different location you can specify yourself.

---

### Post by chrisccoulson on 2008-03-21
I have to admit, I set up my machine so that XDG_DOWNLOAD_DIR is set to ~/Downloads, as I prefer it that way. I don't know whether it should be default though, as it might not be immediately obvious where the downloaded file went (whereas it is probably more intuitive on the desktop).

---

### Post by Tyche on 2008-03-21
Ya know, I've never really thought about this.  I have simply been quietly setting up the preferences for Firefox whenever I do a new install.  And, of course, one of the first things is to create a downloads directory to store downloaded programs and etc.  The same with any other program that may be used for downloading.  And this all the way back to when I was still on a  Windows machine.  There are simply certain procedures that one does, certain housekeeping that one engages in whenever things change.  And too, I've found that not everyone wants a separate download directory.  They like having things right there, out in the open, on the desktop where they can be easily reached without having to think about it.  So, though this may be good for you, I'm not sure that it's right for everyone to be forced to use a downloads directory.  Perhaps the way it is now is better, allowing people to set up whatever arraingements they deem appropriate, and as they see fit.

---

### Post by Prosthetic Head on 2008-03-31
First thing I do on a new install is create a downloads folder in my home and point firefox there as its download location, so it would save me a job :)

---

### Post by whitewizardcoder on 2008-03-31
I think this would be an excellent idea because my desktop is always getting too cluttered with downloads...

---

### Post by xelapond on 2008-04-10
This should definately be implemented, you should make a page on the Ubuntu suggestions page, so we can upvote it.

---

### Post by CarpKing on 2008-04-10
I like the current way.  It makes me either delete files or move them where they belong.  If I had a downloads folder, it would just get full of unsorted files, many of which I didn't actually want to keep.

---

### Post by AZzKikR on 2008-04-11
I like it the way it is now. I like to configure my own destination where my downloads go, either by configuring or some other way.

---

### Post by smartboyathome on 2008-04-11
> **AZzKikR said:**
> I like it the way it is now. I like to configure my own destination where my downloads go, either by configuring or some other way.

I agree, I like to download everything to specific folders depending on what it is (ie, pictures go in Pictures, archives/packages go in Packages, music goes in Music, etc), and misc stuff goes in my home folder.

---

### Post by xelapond on 2008-04-11
You would still be able to change it, but a lot of us change it too downloads folder, so that would just save us a few seconds.  Let me also point out that Epiphany does this by defualt:)

---

### Post by CarpKing on 2008-04-12
> **xelapond said:**
> You would still be able to change it, but a lot of us change it too downloads folder, so that would just save us a few seconds.  Let me also point out that Epiphany does this by defualt:)

I thought Epiphany downloaded to the desktop by default.  Maybe I changed an option at some point, but I don't remember doing so.

---

### Post by Redrazor39 on 2008-04-12
you don't understand; there's too much windows left in your mind (same for me, but still). The reason downloads go straight to the desktop is so you can easily access them because then it's easier to move them, run them, etc. without opening a file browser and navigating and all that. Since you don't need launcher icons on your desktop with the easy to use menus and the panel icons you can make, you can use the desktop space for downloads and other stuff. Think of it this way. You go to the office and you get a file. Then you come home to your desk and read it or file it where you need to. In essence, you take it to your desktop to use it. It would be fairly silly to take it home, put it in a special folder, close the cabinet, then open the cabinet, open the folder, take out the file, and THEN use it.

I hope you get what I'm trying to communicate to you (hopefully my analogy makes sense)

---

### Post by xelapond on 2008-04-13
> you don't understand; there's too much windows left in your mind (same for me, but still). The reason downloads go straight to the desktop is so you can easily access them because then it's easier to move them, run them, etc. without opening a file browser and navigating and all that.

The only reason we want a download folder is because imagine what would happen if you brought a bunch of stuff home from work and dumped it on the floor.  That would get annoying.  Some of us download a lot of stuff, so we want it to go in one spot where its easy to get to, and doesn't clutter everything else up.

I cool idea for even better orginization would be to allow rules, so different file types go to different folders.  JPGs go to pictures, ODT goes to documents...

---

### Post by smartboyathome on 2008-04-13
> **xelapond said:**
> I cool idea for even better orginization would be to allow rules, so different file types go to different folders.  JPGs go to pictures, ODT goes to documents...

I already do this by setting Firefox to ask where I want to save my files. It would be cool if it could have it do it itself.

---

### Post by Mr. Picklesworth on 2008-04-13
> **Redrazor39 said:**
> you don't understand; there's too much windows left in your mind (same for me, but still). The reason downloads go straight to the desktop is so you can easily access them because then it's easier to move them, run them, etc. without opening a file browser and navigating and all that. Since you don't need launcher icons on your desktop with the easy to use menus and the panel icons you can make, you can use the desktop space for downloads and other stuff. Think of it this way. You go to the office and you get a file. Then you come home to your desk and read it or file it where you need to. In essence, you take it to your desktop to use it. It would be fairly silly to take it home, put it in a special folder, close the cabinet, then open the cabinet, open the folder, take out the file, and THEN use it.

I hope you get what I'm trying to communicate to you (hopefully my analogy makes sense)

Then set XDG_DOWNLOADS_DIR to ~/Desktop. The problem is not where downloads are going per se, but that they are going to an arbitrary location and Firefox is not fitting with the standards. Needs a fix :)


...Besides that, I think it is safe to say that the desktop and folders analogy is flawed. People hate desk clutter, so why should computers, with all their potential for organization tools, try to duplicate it?
The analogy doesn't even make sense to begin with. How is somebody's desk a folder, and have you *ever* seen a person with layers of folders placed inside each other?

In terms of downloading files, I think the ideal situation is where content in a web browser is just like in a file manager, with the same sort of interaction, where one drags that to the place he wants it. No middle step involved. After all, following the folders and files analogy, the thing is just a file when it is in the web browser and is no different from something stored locally thanks to the VFS. Why should it behave so very differently?

---

### Post by CarpKing on 2008-04-13
> **Mr. Picklesworth said:**
> In terms of downloading files, I think the ideal situation is where content in a web browser is just like in a file manager, with the same sort of interaction, where one drags that to the place he wants it.

That's already possible, at least in some situations.  Click on an image (say, the smilie in your post) and drag it onto your desktop.  The file will be placed there.  Same goes for any file browser window (This is using Nautilus so I can't guarantee it will work for other file browsers, but it does work with both Firefox and Epiphany).

---

### Post by Mr. Picklesworth on 2008-04-13
Indeed, drag and drop works nicely. One of my favourite things in Linux land, actually.
Sorry, bad example. Other behaviour is completely unlike conventional file management; what if we could copy and paste those, right click and choose Open With, etc?
Could be an interesting experiment...

---

### Post by xelapond on 2008-04-14
KDE4 Kind of takes an approach at your fix, and instead lets you have stuff like calculators and clocks on your desktop, like you would in real life.

---

### Post by Nirro on 2008-04-25
+1

Putting all downoladed files in the Desktop is just not logical.
The Desktop should be clean and include only the most used shortcuts, it is not the dump of the computer.

If you want an easy access to your files, firefox's download manager has a quick link to the destination folder.

---

### Post by hyper_ch on 2008-04-25
> **ubuntu_demon said:**
> RATIONALE :
* less cluttered desktop

Dream on... no matter how clean you try to keep your desktop it will become cluttered anyway ;)

---

### Post by chrisccoulson on 2008-04-25
> **Nirro said:**
> +1

Putting all downoladed files in the Desktop is just not logical.
The Desktop should be clean and include only the most used shortcuts, it is not the dump of the computer.

If you want an easy access to your files, firefox's download manager has a quick link to the destination folder.

Actually, this is what people use the Desktop for in the Windows world (shortcuts / launchers). In Ubuntu, we have a good menu structure, launchers on panels etc which leaves the Desktop free to be used as a desktop - and these are usually covered in piles of paper, notes, dust, coffee mugs etc and generally aren't very tidy. A desktop in the traditional sense is a working space, and a PC desktop can be used in the same way.

---

### Post by Nirro on 2008-04-25
> **chrisccoulson said:**
> Actually, this is what people use the Desktop for in the Windows world (shortcuts / launchers). In Ubuntu, we have a good menu structure, launchers on panels etc which leaves the Desktop free to be used as a desktop - and these are usually covered in piles of paper, notes, dust, coffee mugs etc and generally aren't very tidy. A desktop in the traditional sense is a working space, and a PC desktop can be used in the same way.

So why do you have "Document" folder ? and "Music" and "Pictures" if you can put them all in piles on your desktop ?
Your computer shouldn't encourage you to be disorganized, I would prefer to separate between things I work on regularly (documents), and things I've just downloaded once. That's why folders were invented so why not to use them ?
Educate the users to be organized, they will appreciate you for that.

---

### Post by smartboyathome on 2008-04-25
I think the desktop is organised. Personally, I don't want a ~/Downloads folder. I download stuff to my desktop, and move them to the correct folder OR save it to the correct folder off the bat. I think encouraging users to do THIS would be better, not to make a separate folder which would be cluttered anyway.

---

### Post by caryb on 2008-04-25
I personally think this is a great idea! coming from a KDE4 perspective having apps on the desktop is a pain as it does not show up as a application but a icon & KDE4 wont recognise it as a executable (or text or whatever) file. In order to make the file useful it has to be moved of the desktop anyway. I'm a firm believer of keeping Ubuntu/Kubuntu as seamless as possible & if KDE4 (will be the std in intrepid) it would be good for standardization to move in this direction.


My 2 bobs worth Cary

---

### Post by Mr. Picklesworth on 2008-04-25
I have noticed that the existing functionality is broken, anyway, if someone changes his Desktop directory to be ~ (thereby deleting Desktop and having his home folder displayed on the desktop), or tells Nautilus to display home folder as desktop. Firefox creates a Desktop folder, anyway.

I probably don't want to know what happens with localization...

Therefore, the fix mentioned here is important for technical reasons, too.

---

### Post by chrisccoulson on 2008-04-26
> **Mr. Picklesworth said:**
> I have noticed that the existing functionality is broken, anyway, if someone changes his Desktop directory to be ~ (thereby deleting Desktop and having his home folder displayed on the desktop), or tells Nautilus to display home folder as desktop. Firefox creates a Desktop folder, anyway.

I probably don't want to know what happens with localization...

Therefore, the fix mentioned here is important for technical reasons, too.

This is not what we're talking about. We're talking about changing XDG_DOWNLOAD_DIR from ~/Desktop to ~/Download. You're talking about making your desktop be your home folder. In this case, Firefox *will* still create a ~/Desktop folder because XDG_DOWNLOAD_DIR=$HOME/Desktop, so the functionality is not broken.

---

### Post by Mr. Picklesworth on 2008-04-26
Ah, I forgot that the default download dir was Desktop. In that case, I guess my rambling makes little sense. I'll clear that up: Presently, Firefox does not seem to obey the XDG download dir, instead going with its own arbitrary directory. (Epiphany does, mind). So... there are two issues here!

---

### Post by eye208 on 2008-04-27
> **imT said:**
> i think it's fine just how it is right now
Are you telling us you keep all your downloads on the desktop all the time?

Screenshot please! :lolflag:

---

### Post by Gina on 2008-05-05
I always set up Firefox to my Download directory/folder.  But this is often in a large data partition shared by all OSs and the network rather than in the Home folder.  Sometimes I change the Firefox default download destiation to suit what I'm doing - like set to a Download/Hardy folder when testing the development releases.  I can see the logic of using the Desktop as default too.

To sum up...  I can see the virtue in using ~/Download and the virtue in using ~/Desktop - so IMO not worth changing the status quo (since it's easy to change anyway).

---

### Post by Saint Angeles on 2008-05-05
actually incoming downloads should go to the desktop... once they are done they should be moved to the appropriate folder (video, music...). this way i can see whats being downloaded and what needs to be organized (just like a real desktop on a real desk).

what is a "download"? is it not music or videos or documents? most likely it is one of those and not a separate thing. by this logic, everything is a download and everything should go into this new download folder.

if it were changed, me and everybody i know would have to change it right back to make it logical and usable.

---

### Post by Saint Angeles on 2008-05-05
> **eye208 said:**
> Are you telling us you keep all your downloads on the desktop all the time?

Screenshot please! :lolflag:
ummm... incoming downloads are kept there... then they finish. a "download" as you guys call it becomes something like "music" or "videos" and so you would use your little mouse cursor to drag it into "music" or "videos".

i really don't get how this is so dificult to understand. why create another category called "download" when everything you get is a download?

why expand the bureaucracy?

---

### Post by Terry Jones on 2009-01-30
I am a system administrator and programmer that deals Linux,Mac, and Windows. I can't tell you how many times I have had to reinstall operating systems for family, friends and on the job. It helps the user in keeping the desktop clean and regularly backing programs and data downloaded from the internet. Also it helps the administrator when reinstalling software not having to waste time downloading software or looking for a specific version of software. When I do a reinstall I always create a Downloads folder with the following structure.

Downloads(Top level directory in the Home folder or the My Documents Folder.)

Inside the Downloads directory I create the following directories

1. Bit Torrent Downloads (Downloads directory for current Bit Torrent downloads.)

2. FTP Downloads (Downloads directory for current FTP downloads.)

3. Web Browser Downloads (Downloads directory for current Web Browser downloads.)

4. Saved Programs and Installation Files (Folder used to save Programs/Applications downloaded from the sources listed above that the user wants to keep.)

---

### Post by unityofsaints on 2009-02-05
I'm sorry but I don't think this proposal makes any sense. Any novice not experienced enough to be able to change the download folder in firefox probably wants downloads to show up on the desktop anyway and anyone who knows how to change it does so. /home/downloads/ is likely to be just as satisfactory/unsatisfactory as using the desktop.

Just my 2cents tho..

---

### Post by megamanXplosion on 2009-02-05
I think of the desktop as a more logical default. The download folder setting would confuse new users, increase the learning curve, and serve as another potential roadblock in transitions from Windows to Linux. The desktop setting avoids these problems and experienced users can change the setting easily.

---

