---
title: "Wine update"
date: 2010-09-29
forum: Wine
---

### Post by EpicFai1 on 2010-09-29
I am trying to update my Wine from 1.1.4 to 1.1.43 so I can get my version of Rosetta stone to work properly. I have downloaded the 1.1.43 update of wine and it will not find the file or update. Cannot update my Wine, assist please? Running Ubuntu 10.04.

---

### Post by NightwishFan on 2010-09-29
Add the Wine Team PPA:
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

Here is how via command line:
```
sudo apt-add-repository ppa:ubuntu-wine/ppa
```

Then:
```
sudo apt-get update
```

Finally:
```
sudo apt-get upgrade
```

You will have Wine 1.2.

---

### Post by EpicFai1 on 2010-09-29
Wine 1.2 is not compatible with that version of Rosetta Stone. It's the issue I've been having all morning, finding the right version that works. Any other possibilities?

---

### Post by NightwishFan on 2010-09-29
I do not see a way myself, but that does not mean there is not one.

---

### Post by EpicFai1 on 2010-09-29
While trying to manually install the update this is what I get:

sudo apt-get install wine-1.1.43.tar.bz2
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package wine-1.1.43.tar.bz2

I have tried to place the file in different locations for my computer to find but it has still not detected this file for the update. I cannot use Wine 1.2, I need Wine1.1.43 for the program I am attempting to use on Ubuntu10.04 and it is just not working.

Assist please?

---

### Post by Half-Left on 2010-09-29
Why are you asking apt for the tar.bz2 file? That's a source tarball. The only way I can see you doing that is if you compile that version of Wine manually.

---

### Post by EpicFai1 on 2010-09-29
> **Half-Left said:**
> Why are you asking apt for the tar.bz2 file? That's a source tarball.

because it won't find the wine-1.1.43 file itself. Any steps or assistance would be better than questions and criticism. Am still beginner Linux user.

---

### Post by Half-Left on 2010-09-29
It wasn't a criticism and I was just asking why you were doing it but clearly it's just that you're new and that's fine.

Source tarballs are for compiling, they're not binary packages. You'll have to learn how to compile manually if you cannot find a binary package for Ubuntu with that version of Wine. You can make your own packages from tarballs but you'll need to find a tutorial on that.

---

### Post by t.rei on 2010-09-29
go into synaptics package manger (system -> administration, I think)

search for wine 

select it

look in the menu "package" for the option to install(force) a specific version. (should be there, haven't used it in a loooong time)

---

### Post by EpicFai1 on 2010-09-29
> **Half-Left said:**
> It wasn't a criticism and I was just asking why you were doing it but clearly it's just that you're new and that's fine.

Source tarballs are for compiling, they're not binary packages. You'll have to learn how to compile manually if you cannot find a binary package for Ubuntu with that version of Wine. You can make your own packages from tarballs but you'll need to find a tutorial on that.

--Oh, thank you. Sorry, been at this most the day and still can't get what I want to work. Being a beginner is difficult, but what makes it difficult helps you learn. 
Any good places to find tutorials?

---

### Post by mocoloco on 2010-09-29
According to [this page]("http://appdb.winehq.org/appview.php?appId=1867") most version of Rosetta will run under wine 1.3.  If you added the wine ppa you can just do ```
sudo apt-get install wine1.3
```

If you have it on good source that only 1.1.43 will run it (or you've already tried 1.3) then I apologize.

---

### Post by EpicFai1 on 2010-09-29
> **t.rei said:**
> go into synaptics package manger (system -> administration, I think)

search for wine 

select it

look in the menu "package" for the option to install(force) a specific version. (should be there, haven't used it in a loooong time)

--It will only give me the option to "force version" the same version I have or version 1.2 which I cannot use, not other options. But thank you for the info.

---

### Post by EpicFai1 on 2010-09-29
> **mocoloco said:**
> According to [this page]("http://appdb.winehq.org/appview.php?appId=1867") most version of Rosetta will run under wine 1.3.  If you added the wine ppa you can just do ```
sudo apt-get install wine1.3
```If you have it on good source that only 1.1.43 will run it (or you've already tried 1.3) then I apologize.

--might as well try 1.3 - it's not tested as of yet for Rosetta v3, so I will try anyway. Thank you. If not then I can always backdate to 1.1.42 and try to compile/config to 1.1.43

---

### Post by EpicFai1 on 2010-09-29
Version 1.3 of Wine appears to not be compatible, but v1.3.1 is, but I cannot appear to get a hold of a copy of that version. Just have to wait I guess.

---

### Post by Half-Left on 2010-09-29
That Wine repo has the latest Wine, which is 1.3.3.

---

### Post by Bachstelze on 2010-09-29
I think with playonlinux you can install any WINE version. It's a bit of a hack, because it uses its own packaging format, but you should be able to get it to work.

---

