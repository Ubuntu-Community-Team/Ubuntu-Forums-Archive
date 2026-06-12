---
title: "Irfanview problems"
date: 2011-03-08
forum: Wine
---

### Post by Scunnered on 2011-03-08
I am experiencing difficulty in having Irfanview working.

I firstly downloaded the current version of Wine via Synaptic and see that it is available in the applications menu.  I then downloaded version 1.2.2 of Irfanview and was advised that it was not executable.  After a bit of messing about I opened up the folder and ticked the execute box in permissions.

At this point in time I am unable to see anything anywhere in Wine to indicate that Irfanview is installed.

Can someone please advise where I am going wrong as I am at my wits end.  I have little or no understanding of how things work so please work on the KISS basis for me as this is my level.

Thanking you for your kind assistance.

---

### Post by howefield on 2011-03-08
Just to clarify first, isn't the current version of Irfanview 4.28 ?

---

### Post by howefield on 2011-03-08
Ah, you probably mixed up the version numbers of Irfanview with the Wine version number.

To install irfanview, try installing the winetricks package, then load it up (Application > Wine > Winetricks).

Scroll down and select mfc42 and press the OK button.

You should now be able to right click on the irfanview executable and select Open with Wine Windows Program Loader and install it.

The Wine application database page for irfanview can be found here..

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834)

---

### Post by Scunnered on 2011-03-08
My thanks for your kind reply.

Firstly my apologies for the confusion with version numbers. That is how bad it is getting.

Googled Winetricks and from the Wine Wiki section Getting Winetricks used the code :

"get http://winetricks.org/winetricks"

which was accepted.  However when I look at Applications > Wine there is no sign of wine tricks.

Can you please offer further assistance ?

---

### Post by howefield on 2011-03-08
> **Scunnered said:**
> Googled Winetricks and from the Wine Wiki section Getting Winetricks used the code :

"get http://winetricks.org/winetricks"

Apologies I should have been clearer, I installed winetricks via Synaptic Package Manager after adding the Wine PPA to my sources list with the command.

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

and then reloading the package lists.

```
sudo apt-get update
```

---

### Post by Scunnered on 2011-03-08
That was quick.

Followed your sudo instructions but still no show on Wine Menu.

When I use Applications > Wine I am offered four options.

1. Programmes > Applications > Notepad
2.Browse C Drive
3.Configure Wine
4.Uninstall

I have been unable to find any mention of winetricks in any of the first 3 options.

Where do I go from here ?

---

### Post by howefield on 2011-03-08
Have you installed winetricks ?

Either via Synaptic or the command line ?

```
sudo apt-get install winetricks
```

---

### Post by Scunnered on 2011-03-08
Well done, you have saved a life - mine.

I should now be in the happy position where I can convert my partner to Ubuntu.  Up till now she has said that she will not change as she can't get her beloved Irfanview.

Now she can so no more excuses.

My sincere thanks for all your kind assistance and patience with me.

---

### Post by howefield on 2011-03-08
Thanks for the update, glad you got it figured out.  :)

---

