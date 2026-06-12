---
title: "Display Manager Question"
date: 2006-05-07
forum: The Cafe
---

### Post by nalmeth on 2006-05-07
Does anyone know of a display manager that allow's a graphical selection of the Desktop Environment?
For Example,
GDM allows you to graphically select your user, and allow's you to select a picture for that user.
Selecting your Desktop Evironment, however, is done with the Session Menu.
I have always liked the idea of advancing to another page where you can pick your DE graphically, and being able to denote a screenshot, or other picture (such as the gnome foot for gnome) to your Desktop Environment.
Is there a Display Manager with this type of feature? Or is it possible to do this with GDM?

---

### Post by Monster_user on 2006-05-07
I don't think there is one that will do that at all.
Then again, I only know of three Desktop Managers, XDM, GDM, and KDM.

I would look for that in KDM, in the far future. I doubt GDM will change much.

---

### Post by nalmeth on 2006-05-07
Yeah, those are the only three I know of aswell.
I don't see what the difficulty of doing this would be..
Any more knowledgeable people know what might make this impractical at this point?

---

### Post by Parkotron on 2006-05-07
I'm quite confident that none of the current generation DMs could handle this, but it's a very interesting idea.

It would be really slick if it could be set up so that a desktop screenshot could be taken automatically on logout, especially if the screenshot was taken after all windows have been closed, so that only the desktop and panels are visible. Then a thumbnail of the last used desktop could be shown for each user on the DM.

Of course, this would require setting up a standard between all the desktop environments for how/where the screenshot would be saved, but I'm sure that'd be possible with a little work.

---

### Post by nalmeth on 2006-05-07
I like the auto-screenshot idea. Ideally, this would be a configurable function.
I'm really interested in finding out how this could work.
It would make the log-in screen much nicer and guie, without adding clutter (dapper has stripped down GDM, because people thought it was too cluttered :rolleyes: )

---

### Post by ComplexNumber on 2006-05-07
[quote=nalmeth]Does anyone know of a display manager that allow's a graphical selection of the Desktop Environment?
For Example,
GDM allows you to graphically select your user, and allow's you to select a picture for that user.
Selecting your Desktop Evironment, however, is done with the Session Menu.
I have always liked the idea of advancing to another page where you can pick your DE graphically, and being able to denote a screenshot, or other picture (such as the gnome foot for gnome) to your Desktop Environment.
Is there a Display Manager with this type of feature? Or is it possible to do this with GDM?[/quote] an unconventional way of going about it it is to have several different user accounts each representing a different DE. for example, you could have 'users' - "Gnome" and "KDE". attach a pic of the gnome's foot and the KDE gears to the respective 'users'.

---

### Post by nalmeth on 2006-05-07
hmm intersting idea
though it may get a little complicated with many users. 
perhaps it would simplify things if you also created a /data partition that all the users could share.

that may be the best tmp solution so far!

---

### Post by Monster_user on 2006-05-09
If it wasn't for permission issues, you could just link the user account folders to the original. You would have to do some User Group account managing. Making sure that the files can be read, and written by all users in the group. I do not know how to make this automatic, when creating new files.

For now, just linking the most commonly used folders, and files, seems to be the best solution. 

Having your '.mozilla' and '.xmms' folders shared between accounts.

Assuming you have already moved, or copied your profile folders to the '/data' folder, then you can use the 'ln -si' command, to link them to the right folder. '-i' is not needed, but I always prefer to have a confirmation. If it asks if you want to overwrite anything, then either you have already linked that file, or your doing it backwards. It could also meant that you logged into the account from the GUI, rather than the terminal, and you have run a few programs.

Here are a couple of examples. This will link the '/data/' file to the account your logged into. There should not be a response, except for your original account.

ln   -si   /data/.mozilla   ~/.mozilla
ln   -si   /data/.xmms  ~/.xmms

---

