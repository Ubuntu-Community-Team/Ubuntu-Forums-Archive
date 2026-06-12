---
title: "Installing wine without sudo ??"
date: 2009-06-27
forum: Wine
---

### Post by acdragon101 on 2009-06-27
Hi,

 May I ask is it possible to compile the application wine on ubuntu without using any administrator priviledges ?

I have an idea but I'm not sure if it will work the idea is that I've heard about the portable ubuntu for windows, I would try to run that on linux but first I would to install wine on that portable ubuntu. Do you think it will work?

myReason: My purpose for this is that my school has all Ubuntu on it and I can't install anything without sudo I want to do this because I want to use MS Word not abi word or Open office 

Any Comments, Suggestions violent reactions are very much welcome !!!
To those who will reply thank you !!!

---

### Post by stimpak on 2009-06-27
if you can satisfy all the dependencies (sudo apt-get build-dep wine) wine needs to compile itself then
yep.. just [download the source]("http://www.winehq.org/docs/wineusr-guide/getting-wine") untar it and :

```

cd {wine-source-folder}

mkdir build && cd build && ../configure && make depend && make


```

(note it will take at least 20 mins to complete)

and you've installed wine inside the ~/{wine-source-folder}/build

or option 2(untested), get a pre-compiled (.deb) version and install it to your /home. I havent tried myself anything like that. I'd suggest mess with the dpkg command if it gives you an option where to install

---

### Post by ackanao on 2009-06-27
Maybe the easiest way is to just extract Wine deb package in a folder of your choice and use it from there:

1. Extract Wine deb package
2. Extract data.tar.gz

3. Use extracted Wine

---

### Post by acdragon101 on 2009-06-27
Thanks for the reply I will try it myself and tell you the results later  ^_^

---

### Post by philcamlin on 2009-06-27
ahh my scool uses windows 
id kill to see my school use ubuntu

thatd be the coolest thing ever!:popcorn:

---

### Post by acdragon101 on 2009-06-27
Yes my school has change from windows to ubuntu even our programming langauge Java is being compiled and run in ubuntu. Its easy and the same in windows but the downside is that you don't have enough freedom but the good thing is that no viruses on our flash drives ^^.

About the installation of wine um I've only found the data.tar.bz2 could you give me the link for the deb 

thanks again !!!:D

---

### Post by ackanao on 2009-06-27
@acdragon1010

Here you can download Wine deb packages:

[http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html")

After you extract deb package, you'll see data.tar.lzma file; extract it and there you'll see "**data**" folder - you can rename it and place it wherever you want.

Here's how to use it:

To create a new wineprefix in a "folder of your choice", type this:
```
WINEPREFIX=$HOME/folder/of/your/choice /full_path_to/extracted_wine_folder/usr/bin/wineboot
```

To configure new wineprefix, type this in terminal:
```
env WINEPREFIX=/folder/of/your/choice /full_path_to/extracted_wine_folder/usr/bin/winecfg
```

To install an application with extracted Wine in a wineprefix you've created, type this:
```
env WINEPREFIX=/folder/of/your/choice /full_path_to/extracted_wine_folder/usr/bin/wine /path/to/Setup.exe
```

To start installed application use this:
```
env WINEPREFIX=/folder/of/your/choice /full_path_to/extracted_wine_folder/usr/bin/wine "C:\Program Files\App Folder\App.exe"
```


Hope this helps... sorry for my bad english... :(

---

### Post by acdragon101 on 2009-06-28
Thankyou very much it work like a charm !!!!

I have a problem about this error 

"Could not load wine-gecko. HTML rendering will be disabled."

it needs the gecko as far as I know this is the same as the internet explorer that other application needs is there a way to install this ??

 


Most of the application like office 2003 WORKED !!! HOray !!!! THANKYOU SO MUCH !!! ^_^:D:D

Thanks again !!!

Sorry for my wrong gramming / grammar ^^

---

### Post by ackanao on 2009-06-28
Hi acdragon101, I'm glad we solve your problem. :P

About wine-gecko:

You could use winetricks to install wine-gecko for your wineprefix - here's the link:

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

There you'll find everything you need to know about winetricks and how to use it...

To install wine-gecko for your wineprefix, type something like this:

```
env WINEPREFIX=~/folder/of/your/choice sh winetricks gecko
```



Cheers

---

### Post by acdragon101 on 2009-06-28
Um there is an error message 
  
    "Cannot find wine (wine)"

I've type 

 "env WINEPREFIX=~/win sh winetricks gecko"

Please help again !!
Sorry I'm really new to this .. ^^

---

### Post by ackanao on 2009-06-28
OK. I think I can explain this better if I show you an example:

First, use this command to download winetricks:
```
wget http://www.kegel.com/wine/winetricks
```

You'll find winetricks script in your "home" folder when download completes.

I extracted Wine and copied "data" folder on my Desktop; Then I use this command to create new wineprefix called "Example" on my Desktop:

```
WINEPREFIX=~/Desktop/Example /home/ackanao/Desktop/data/usr/bin/wineboot
```

Then I use this command to install wine-gecko:

```
WINEPREFIX=~/Desktop/Example sh winetricks gecko
```

Maybe you missed something or made a typo - it's pretty straightforward, try again and let me know if you manage to install it or not.

---

### Post by acdragon101 on 2009-06-28
Thanks the problems is fix i've run the winetricks but when I try to install others beside font codecs and other simple installation most of them have errors and won't continue.
Could you send me a copy that has almost complete winetricks or is there a site that provides the compiled one ? I specially need the MSI Installer and the MXML 6 and IE6 I've tried installing but it just wont error I forgot the error but I will tell you tomorrow.

Thanks again !!

---

### Post by xavierp94 on 2009-06-28
I'd wish our school used Ubuntu. We still use Windows XP.

---

### Post by ackanao on 2009-06-29
@acdragon101

I think I know why you're having difficulties configuring your "portable Wine" setup, so I'll start from begining...

First, install Wine on your home computer - it is needed if you want to use winetricks for your "portable Wine" configuration. 

If you don't want to use winetricks, then you don't have to install Wine on your system - In this case, you can install different Microsoft runtime libraries for your wineprefix manually but you need to know which "overrides" to implement.

I think it's best to have "extracted" Wine and your wineprefixes placed in one folder (ex: Wine-Portable folder) - it's much easier to manage your extracted Wine versions and different wineprefixes.

So, create "Wine-Portable" folder (name it whatever you want) and inside that folder you'll have one folder for your extracted Wine (or maybe more if you want to use different Wine versions) and different folders for each wineprefix you create - Here's an example:

Wine-Portable
|
|
|-wine folder
|
|-wineprefix folder for Microsoft Office 2003
|
|-wineprefix folder for Adobe Photoshop
|
|-wineprefix folder for some other application
|
|-etc.

If you have Wine installed on your system and then try to use winetricks to install "stuff" for your wineprefix, the installation will complete successfully. When you're finished with configuring your wineprefixes, you can copy your "portable Wine" folder to another computer - i've already described how to use it in my previous posts.

Some applications works better with wine-gecko 0.9.1 and newer Wine versions (Wine 1.1.14 and later) use wine-gecko 0.9.1. Older versions of Wine works with wine-gecko 0.1.0.

If wine-gecko is only thing you need for your wineprefix, you can install it even if you don't have Wine installed on your system:

```

WINEPREFIX=~/Desktop/Example /home/ackanao/Desktop/data/usr/bin/wine iexplore [http://www.winehq.org](http://www.winehq.org)

```

This command will install appropriate wine-gecko version for your extracted Wine.

Now, try again and report your results - I hope you'll be successful this time...


Cheers.

---

### Post by acdragon101 on 2009-06-30
Thanks it really works !!!

Cheers !!

---

### Post by ackanao on 2009-07-01
I'm glad I was able to help - Cheers acdragon101!

---

