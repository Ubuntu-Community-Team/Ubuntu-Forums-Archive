---
title: "Automatix2 beta (only for Dapper) has been released"
date: 2006-10-03
forum: The Cafe
---

### Post by arnieboy on 2006-10-03
[B]Automatix2 beta for Dapper has been released. 
[/B]Its in the AX Dapper repository. If you have the AX repository added, all you need to do on Ubuntu/Kubuntu/Xubuntu 6.06 (Dapper) is the following:
```
sudo apt-get update
sudo apt-get install automatix2
```
and AX2 will appear in Applications --> System Tools
From terminal, you can run it as
```
automatix2
```

We are in the process of updating our website ( [http://www.getautomatix.com](http://www.getautomatix.com) ) with a comprehensive list of features in AX2. The following is an incomplete list:
> **1)** AX2 is written in pygtk and works on a bash backend.
**2)** It has an uninstall feature for all options.
**3)** Completely reworked UI and design
**4)** Categorization of all applications (by no means complete, we intend to add more apps and move some apps to more appropriate categories)
**5)** Uninstallation and Installation (obviously not of the same app) can work simultaneously with uninstallation preceding installation to keep the whole process as safe as possible
**6)** AX2 will not overwrite your sources.list unless you explicity tell it to do so.
**7)** if AX2 crashes for some reason during its operation, your sources.list is no means gone and you do not have to manually restore it. Just run AX2 again and click on File --> Restore Sources and your old sources.list will be restored.
**8)** If you click on cancel at any time of AX2's operation, it will finish running the script its currently on and then exit gracefully after the usual question about restoring your sources.list.
**9)** If you do not agree to the legalities involved in downloading proprietary audio and video codecs at the startup, AX2 will disable the AUD-DVD codecs option.
**10)** Your Password for running AX2 will now be asked only once and never again.

Further things being worked on:
> We will log everything from the AX2 terminal in one file with time and date based timestamps for easy debugging and troubleshooting.


[B][SIZE="3"]Please ask all support questions, submit bug reports and feedback here:
[http://www.getautomatix.com/forum](http://www.getautomatix.com/forum) and look for subforum "Automatix2 on Ubuntu 6.06"[/SIZE][/B]
Attached is a screenshot:

---

### Post by TheRingmaster on 2006-10-03
does this replace the automatrix I already have?

---

### Post by arnieboy on 2006-10-03
> **jpazindustries said:**
> does this replace the **automatix** I already have?

not right now. A month from now or slightly earlier it will.

---

### Post by jtbl on 2006-10-03
Here is the order we plan on releasing the versions:
6.06 i386
6.10 i386
6.06 AMD64
6.10 AMD64
6.06 PowerPC
6.10 PowerPC

Note the AMD64 and PowerPC versions will now have Kubuntu specific options.

---

### Post by Zweih on 2006-10-03
I go to install it but I couldn't find the automatix2 package. And yes, I do have the automatix repository.

---

### Post by arnieboy on 2006-10-03
> **Zweih said:**
> I go to install it but I couldn't find the automatix2 package. And yes, I do have the automatix repository.
```

sudo apt-get update
sudo apt-get install automatix2
```

---

### Post by maniacmusician on 2006-10-03
does this not work for kubuntu yet? i have the automatix kubuntu repo enabled and it cant find automatix2.

---

### Post by arnieboy on 2006-10-03
> **maniacmusician said:**
> does this not work for kubuntu yet? i have the automatix kubuntu repo enabled and it cant find automatix2.

This is an integrated package which works on on all versions of Ubuntu 6.06. 
Let me update the kubuntu repositories as well.

---

### Post by maniacmusician on 2006-10-03
okay, thank you. 


nice avatar. he's got quite a serious look to him in that one though. i prefer him playful.

---

### Post by arnieboy on 2006-10-03
AX Kubuntu repositories updated. 
do an apt-get update and AX2 should be there for the pull.

---

### Post by maniacmusician on 2006-10-03
a few notes; 
-in KDE, for some reason, there's two entries in the KDE menu for automatix2 for some reason. 
-Also, it uses gksudo by default. i think kde users will prefer kdesu. i don't know, i had gotten used to  not seeing gksudo lol, it looks kind of ugly after all this time.
-why is OO clipart under Internet?
-in Automatix, you had guarddog for the Kubuntu script, and firestarter for gnome/xfce. now, i only see firestarter as an option (unless i somehow didnt see guarddog). is guarddog gone?

I can't really test installation of stuff, because I have everything that I want installed already installed from AX1. but the GUI is really nice, and it's a really nice upgrade. Much more comfortable for users. My mother was complaining about AX1, but i dont think her complaints would be valid anymore.

nice release.

---

### Post by arnieboy on 2006-10-03
> **maniacmusician said:**
> a few notes; 
1) in KDE, for some reason, there's two entries in the KDE menu for automatix2 for some reason. 
2) Also, it uses gksudo by default. i think kde users will prefer kdesu. i don't know, i had gotten used to  not seeing gksudo lol, it looks kind of ugly after all this time.
3)_why is OO clipart under Internet?
4) in Automatix, you had guarddog for the Kubuntu script, and firestarter for gnome/xfce. now, i only see firestarter as an option (unless i somehow didnt see guarddog). is guarddog gone?

I can't really test installation of stuff, because I have everything that I want installed already installed from AX1. but the GUI is really nice, and it's a really nice upgrade. Much more comfortable for users. My mother was complaining about AX1, but i dont think her complaints would be valid anymore.
nice release.
1, 3 and 4 will be fixed in the next release.
if the team decides on adding kdesu instead of gksu for KDE we will go with that.(that takes care of 2)

---

### Post by maniacmusician on 2006-10-04
Well, then. Fantastic.

I remember you saying in another thread that there will soon be an enourmous selection of programs to install (i think it was over 100). will that be for edgy or dapper as well?

---

### Post by arnieboy on 2006-10-04
> **maniacmusician said:**
> Well, then. Fantastic.

I remember you saying in another thread that there will soon be an enourmous selection of programs to install (i think it was over 100). will that be for edgy or dapper as well?
For both.
We will keep adding more categories and apps. The beta release is for ironing out any remaining bugs like the couple you pointed out. 
ON a side note:
Why dont u join us on IRC and help us with KDE (none of our team members are KDE users)?

---

### Post by maniacmusician on 2006-10-04
hmm, i've never used IRC. but i could try it.
I dont really know what i'd have to offer. I can't code to save my life or anything. what would you be looking for from me?

---

### Post by arnieboy on 2006-10-04
> **arnieboy said:**
> 1, 3 and 4 will be fixed in the next release.
if the team decides on adding kdesu instead of gksu for KDE we will go with that.(that takes care of 2)
1,3 and 4 fixed.

---

### Post by ubuntu-geek on 2006-10-04
> **arnieboy said:**
> 1,3 and 4 fixed.
So I am confused. You request your support forum be removed from here, however this thread is basically starting it again.

---

### Post by Stone123 on 2006-10-04
I see no problem with that.

---

### Post by TheMono on 2006-10-04
Surely the whole support forum thread thing doesn't need to be brought up again...

Thankyou for the announcement, I'm trying out the release now Arnie. I haven't done anything yet.... But the splash screen looks sweet lol.

---

### Post by TheMono on 2006-10-04
OK, only two things - the opening dialog where is says Thanks to everyone.... to this effort." has a randon " at the end of it.

Only other thing is, I don't suppose there is any way to hide what is going on in the terminal window when it is updating the sources.list? Just that the terminal emulator is extremely slow and looks like it is being typed very fast, with a noticeable lag between each letter - looks odd.

Otherwise, awesome release, looks great in py.

---

### Post by arnieboy on 2006-10-04
> **ubuntu-geek said:**
> So I am confused. You request your support forum be removed from here, however this thread is basically starting it again.

This is not a support thread/forum. Its just an announcement and in any case we would have diverted all support questions/bug reports etc to our forum. So, no, you should not have been confused.

---

### Post by maniacmusician on 2006-10-04
[braces] lets not start this again.

---

### Post by arnieboy on 2006-10-04
[B]First post updated. Please post all support questions, bug reports and feedback in
[http://www.getautomatix.com/forum/index.php?showforum=32](http://www.getautomatix.com/forum/index.php?showforum=32)[/B]

---

### Post by JimmyJazz on 2006-10-04
> **TheMono said:**
> 
Only other thing is, I don't suppose there is any way to hide what is going on in the terminal window when it is updating the sources.list? Just that the terminal emulator is extremely slow and looks like it is being typed very fast, with a noticeable lag between each letter - looks odd.

Otherwise, awesome release, looks great in py.

I fixed this today and the new version is in the repo.

---

### Post by Zyzzyx on 2006-10-05
Just reinstalled Dapper this evening. Went ahead and put on AX2. Everything worked just fine and dandy.

---

### Post by beerorkid on 2006-10-10
installed it by accident, works great, loving the uninstall option and it looks neato.

great job as usual.

---

