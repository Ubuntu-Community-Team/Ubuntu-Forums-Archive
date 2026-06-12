---
title: "Localization?"
date: 2006-09-02
forum: Ubuntu System Panel
---

### Post by SlugO on 2006-09-02
I know Ubuntu System Panel is still quite a new project but are there any plans of adding localizations?

I think it would be quite useful because it's meant to replace the application/system menus which are an integral part of the desktop and localization is a high priority in Gnome. Or so is my understanding.

Would be a very nice feature for everyone who isn't a native English speaker.

Thanks for this great app btw :D

---

### Post by chanders on 2006-09-02
> **SlugO said:**
> I know Ubuntu System Panel is still quite a new project but are there any plans of adding localizations?

I think it would be quite useful because it's meant to replace the application/system menus which are an integral part of the desktop and localization is a high priority in Gnome. Or so is my understanding.

Would be a very nice feature for everyone who isn't a native English speaker.

Thanks for this great app btw :D

The early versions had localization thanks to one of our developers Vonpmg. Due to the extensive changes tha USP is going through I wouldn't advise doing any localization at the moment but as long as it settles down it will definitely be implemented...

---

### Post by garak on 2007-01-11
I vote for localization, too.
Its lack is the only thing that keep me from using USP

---

### Post by chanders on 2007-01-11
This is definitely planned but we wanted the app to be working properly and with not many cosmetic changes to be done, before doing any localization

---

### Post by Spin Doctor on 2007-02-13
Why not include the options to do your own localization, setting up the main strings in gconf-editor, where you can replace the default english ones to your own language?. Kind of how you can change the System meny text. Must be an easy solution for those who want to localize USP.

---

### Post by Malac on 2007-02-13
Hi,
I have another Python app called GITOI(**G**lade** I**nterface** T**ranslation** I**nput** O**utput) which reads in the Glade files translatable labels and outputs a text file with them listed with a .gitioi extension. You can then add the translations to the text file load it back into GITOI and have it output a translated glade file.
E.G. usp2.glade becomes usp2_gitoi.glade, computer.glade becomes computer_gitoi.glade.
You can then replace the Glade files for usp and the plugins with these by renaming the originals then removing the "_gitoi" from the translated file. You would need to do this each time you updated though. However the previous .gitoi text file would only need adding to.
As a temporary solution this might help.

Here is the link:
[http://www.ubuntuforums.org/showthread.php?t=262139](http://www.ubuntuforums.org/showthread.php?t=262139)

---

