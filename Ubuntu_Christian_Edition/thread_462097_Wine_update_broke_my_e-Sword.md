---
title: "Wine update broke my e-Sword"
date: 2007-06-02
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2007-06-02
I have the regular e-Sword installed not the nice deb version that Jeremy put together.  When I just updated wine to version 0.9.38 it broke e-Sword and the text now doesn't display right.  I don't know if this will do the same thing to the deb version, or not.  I have the budgetdedicated repo in my sources.  If you don't have this in your repos, then you probably don't have to worry about this update.  If anyone finds a fix to this please post it here.  If you see the wine upgrade, I would leave it for now until someone finds a fix for this.  If you did upgrade and didn't have a problem, please post it here so others can know.  Thanks!

Shane

**EDIT:**  It also broke my two other Bible Programs installed that use wine.  The word, didn't display everything correctly and PowerBible didn't display things correctly either.  I downgraded to the 0.9.37 version [found here.]("http://wine.budgetdedicated.com/archive/index.html")  You need to uninstall your current wine version then download the deb and install it.

---

### Post by evaldas on 2007-06-02
it broke for me too.

is there a way to install he previous version of wine with aptitude? I mean I don't want to install it by downloading manually .deb file, cause it may brake aptitude's dependencies history, I mean right now I'm uninstalling everything with 'aptitude purge --purge-unused package' and I don't have to worry about orphaned packages. So I don't want to install it by hand.

I tried 
> sudo aptitude install wine=0.9.37\~winehq0\~ubuntu\~7.04-1
and
> sudo aptitude install wine=0.9.37
but instead it installed the latest version 0.9.38.

---

### Post by shane2peru on 2007-06-02
> **evaldas said:**
> it broke for me too.

is there a way to install he previous version of wine with aptitude? I mean I don't want to install it by downloading manually .deb file, cause it may brake aptitude's dependencies history, I mean right now I'm uninstalling everything with 'aptitude purge --purge-unused package' and I don't have to worry about orphaned packages. So I don't want to install it by hand.

I tried 

and

but instead it installed the latest version 0.9.38.

There may be a way to install it via aptitude however I don't know how.  You would probably have to add the directory of your deb file to your sources and then install.  I really am not sure.  However I ran ```
sudo dpkg -i wine......deb
```  and I believe it officially installs it and registers it with aptitude.  Afterwards I ran ```
sudo aptitude show wine
``` and it reported it was package .9.37  next I ran ```
sudo aptitude hold wine
```  so when using aptitude it won't upgrade that package (I think).  Hope that helps a little.  I know that if you install it will dpkg you can still remove it with aptitude.  I have been down that road a few times.  Hope that helps.

Shane

---

### Post by koz-man on 2007-06-02
broke mine too.

Can some list detailed instructions for a guy like me (really new to Linux/Ubuntu) to remove the new version of wine and reinstall the old so I can get my eSword back?

Thus far I have entered the Synaptic Package Manager and marked the Wine 9.38 for removal but it says it will also remove eSword for Ubuntu.  I dont' want that.
Help!
THANKS

---

### Post by shane2peru on 2007-06-02
> **koz-man said:**
> broke mine too.

Can some list detailed instructions for a guy like me (really new to Linux/Ubuntu) to remove the new version of wine and reinstall the old so I can get my eSword back?

THANKS

Ok, here it is.  I will even give you the graphical way of doing it.  :)

1. Open synaptic **System -> Administration -> Synaptic**  Click on the search button at the top, and type wine in the window that pops up.  
2. Scroll down till you find wine and right click on it, and select Remove (it isn't necessary to completely remove, just remove is sufficient).  
3. Now click on the apply button at the top.  It may remove some dependent programs, I don't have a solution for this, tell them bye!  
  **Note:** You can re-download them from Jeremy's page just remember what ones they are.  
4.  [Now go here]("http://wine.budgetdedicated.com/archive/index.html") and download the .9.37 i386 (unless you have the 64 bit machine) deb.  5.[COLOR="Red"]Remember where you saved it!!![/COLOR]  
6. Now open nautilus and double click the wine deb you just downloaded to install it.  You don't even need the command line.  :)  
Hope that helped.  :popcorn:  If you need more help just ask.

Shane

---

### Post by mhancoc7 on 2007-06-03
To avoid uninstalling the esword program while doing this you can just do the following:

1. Download  the 0.9.37 i386 ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html))
2. Open Terminal
3. cd Desktop (or location of download)
4. sudo dpkg -i wine_0.9.37~winehq0~ubuntu~7.04-1_i386.deb
5. Enter password
6. Open synaptic **System -> Administration -> Synaptic**  Click on the search button at the top, and type wine in the window that pops up.
7. Highlight wine
8. Click [B]Package -> Lock Version

[/B]Keep in mind that this issue will probably be fixed with a future release of wine.

Jereme

---

### Post by dakotadare2b on 2007-06-03
> **mhancoc7 said:**
> To avoid uninstalling the esword program while doing this you can just do the following:

1. Download  the 0.9.37 i386 ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html))
2. Open Terminal
3. cd Desktop (or location of download)
4. sudo dpkg -i wine_0.9.37~winehq0~ubuntu~7.04-1_i386.deb
5. Enter password
6. Open synaptic **System -> Administration -> Synaptic**  Click on the search button at the top, and type wine in the window that pops up.
7. Highlight wine
8. Click [B]Package -> Lock Version

[/B]Keep in mind that this issue will probably be fixed with a future release of wine.

Jereme

Thanks, Jereme and Shane! This fixed the issue for me, as I was experiencing the same problem.

God Bless,
Randy

---

### Post by david_kt on 2007-06-03
I do not know how you all install e-sword. My e-sword is still running well using any version of wine. Now I am using 0.9.38. I remember one of previous wine (0.9.36 if I not wrong) also broke somebody's e-sword, but not mine. Why don't you try the installation method I use so as to have stable e-sword:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

I have edited that how to to use separate bottle in order not to interfere with other program.

DK

---

### Post by mhancoc7 on 2007-06-03
> **david_kt said:**
> I do not know how you all install e-sword. My e-sword is still running well using any version of wine. Now I am using 0.9.38. I remember one of previous wine (0.9.36 if I not wrong) also broke somebody's e-sword, but not mine. Why don't you try the installation method I use so as to have stable e-sword:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

I have edited that how to to use separate bottle in order not to interfere with other program.

DK

They used the eSword Installer built in to Ubuntu CE, I believe. I think the issue is with the riched20.dll and riched32.dll. The eSword Installer uses the built in ones. I will see if this can be fixed.

Jereme

---

### Post by Enverex on 2007-06-03
Something I posted in another thread;

As you're testing beta software I'm sure you'd have no problem in taking the time to do the following:

Regression testing is when you use the GIT program to sort through patches between versions of Wine to find the exact patch that cause the bug or breakage that didn't used to exist on an older version of Wine but has now appeared. See [http://wiki.winehq.org/GitWine?highlight=%28git%29#head-fc6d68a85d32bb6a8f4ea0485f50dbb6409ab6f4](http://wiki.winehq.org/GitWine?highlight=%28git%29#head-fc6d68a85d32bb6a8f4ea0485f50dbb6409ab6f4)

If you want it fixed then this is the only way it's going to happen. Check for bug reports pertaining to this issue first though.

---

### Post by david_kt on 2007-06-03
> **mhancoc7 said:**
> They used the eSword Installer built in to Ubuntu CE, I believe. I think the issue is with the riched20.dll and riched32.dll. The eSword Installer uses the built in ones. I will see if this can be fixed.

Jereme

Is it violating copyright if you use native riched20.dll and riched32.dll? If not, you should make it uses native dll as it proved (so far) that using them is much more stable.

DK

---

### Post by shane2peru on 2007-06-03
> **mhancoc7 said:**
> To avoid uninstalling the esword program while doing this you can just do the following:

1. Download  the 0.9.37 i386 ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html))
2. Open Terminal
3. cd Desktop (or location of download)
4. sudo dpkg -i wine_0.9.37~winehq0~ubuntu~7.04-1_i386.deb
5. Enter password
6. Open synaptic **System -> Administration -> Synaptic**  Click on the search button at the top, and type wine in the window that pops up.
7. Highlight wine
8. Click [B]Package -> Lock Version

[/B]Keep in mind that this issue will probably be fixed with a future release of wine.

Jereme

So if I understand this I could have just installed wine .9.37 overtop of .9.38 version?  That is a nice trick and keeps people from uninstalling those applications.  Very nice!  Good fix!  And I forgot the locking version, actually I don't know that I knew how to do that with the GUI.  Good work.

Shane

---

### Post by koz-man on 2007-06-05
thanks that fixed my eSword problem.  so glad that i did not have to remove the program.  i had to many modified files and addons to backup and that would have been time consuming for me.

---

### Post by shane2peru on 2007-06-05
> **koz-man said:**
> thanks that fixed my eSword problem.  so glad that i did not have to remove the program.  i had to many modified files and addons to backup and that would have been time consuming for me.

Glad to be of help.

Shane

---

### Post by Enverex on 2007-06-06
I have a feeling you must own a legal copy of Windows to be able to legally use those DLLs files (the main reason Wine doesn't come with any "original" dlls for things that aren't implemented yet).

---

### Post by shane2peru on 2007-06-06
> **Enverex said:**
> I have a feeling you must own a legal copy of Windows to be able to legally use those DLLs files (the main reason Wine doesn't come with any "original" dlls for things that aren't implemented yet).

Actually I do.  However they are available for download as well at find dll's.com or something like that.  Many people are dual booting and this is a good solution for them.  I have since quit dual booting and am only using Ubuntu.  [Here is that dll download web page.]("http://www.dll-files.com/")  Thanks to David_kt for the link.

Shane

---

### Post by mhancoc7 on 2007-06-06
> **shane2peru said:**
> Actually I do.  However they are available for download as well at find dll's.com or something like that.  Many people are dual booting and this is a good solution for them.  I have since quit dual booting and am only using Ubuntu.  [Here is that dll download web page.]("http://www.dll-files.com/")  Thanks to David_kt for the link.

Shane

If I could find a direct download link then I could add these to the Installer.

Jereme

---

### Post by shane2peru on 2007-06-06
> **mhancoc7 said:**
> If I could find a direct download link then I could add these to the Installer.

Jereme

This is straight from david_tk's how to thread [which you can see here]("http://ubuntuforums.org/showthread.php?t=404042&highlight=bottle"):
> 
Or you could go to direct link below:
Riched20:
[http://www.dll-files.com/dllindex/dl...shtml?riched20](http://www.dll-files.com/dllindex/dl...shtml?riched20)

Riched32:
[http://www.dll-files.com/dllindex/dl...shtml?riched32](http://www.dll-files.com/dllindex/dl...shtml?riched32)

oleaut32:
[http://www.dll-files.com/dllindex/dl...shtml?oleaut32](http://www.dll-files.com/dllindex/dl...shtml?oleaut32)


Download msls31.dll to your ~/.wine_Esword/drive_c/windows/system32 from here:

[http://www.dlldump.com/](http://www.dlldump.com/)

Or from direct link here:

[http://www.dlldump.com/cgi-bin/testw...s/M/msls31.dll](http://www.dlldump.com/cgi-bin/testw...s/M/msls31.dll)


Hope that helps.  Ask and ye shall receive, seek and ye shall find, knock and it shall be opened unto you.  :)

Shane

---

### Post by mhancoc7 on 2007-06-06
> **shane2peru said:**
> This is straight from david_tk's how to thread [which you can see here]("http://ubuntuforums.org/showthread.php?t=404042&highlight=bottle"):


Hope that helps.  Ask and ye shall receive, seek and ye shall find, knock and it shall be opened unto you.  :)

Shane

Thanks, but unfortunately the links expire. So they can not be used. :(

Jereme

---

### Post by shane2peru on 2007-06-06
> **mhancoc7 said:**
> Thanks, but unfortunately the links expire. So they can not be used. :(

Jereme

Just a thought, would it be considered illegal to download them and then host them your self on your web site?  I don't know you would probably have to contact the web site, or read their legal statement, but just a thought.

Shane

---

### Post by mhancoc7 on 2007-06-06
> **shane2peru said:**
> Just a thought, would it be considered illegal to download them and then host them your self on your web site?  I don't know you would probably have to contact the web site, or read their legal statement, but just a thought.

Shane

I am not sure, but I will check into it.
Jereme

---

### Post by david_kt on 2007-06-07
> **Enverex said:**
> I have a feeling you must own a legal copy of Windows to be able to legally use those DLLs files (the main reason Wine doesn't come with any "original" dlls for things that aren't implemented yet).

On the contrary, please see the discalimer on this [link]("http://www.dll-files.com/disclaimer.shtml")
> 
As far as we know, these files have been presented to us as being _**free for distribution**_. If you find any that should not be generally distributed, please let us know. We created this site for your convenience, and _**do not wish to violate any copyright laws**_. 


DK

---

### Post by Enverex on 2007-06-07
> **david_kt said:**
> On the contrary, please see the discalimer on this [link]("http://www.dll-files.com/disclaimer.shtml")


DK

Distributing files on their own is different from distributing files as part of another software package though.

---

### Post by david_kt on 2007-06-07
> **Enverex said:**
> Distributing files on their own is different from distributing files as part of another software package though.

Well, I don't see any clause saying that "but you are _**not**_ free to distribute it as part of another software package". But if you are still in doubt, just put it on separate link and give instruction how to use it (like what I did in my how to).

DK

---

### Post by mhancoc7 on 2007-06-19
This seems to have been fixed with the latest wine update (0.9.39)

jereme

---

### Post by peterbrewer on 2007-06-19
Why not use gnome sword or bibletime?

---

### Post by mhancoc7 on 2007-06-19
> **peterbrewer said:**
> Why not use gnome sword or bibletime?

Freedom of Choice! ;)

Jereme

---

### Post by shane2peru on 2007-06-19
> **mhancoc7 said:**
> This seems to have been fixed with the latest wine update (0.9.39)

jereme

Thanks Jereme for the update!

Shane

> **peterbrewer said:**
> Why not use gnome sword or bibletime?

If you have ever used e-Sword going to Gnomesword or Bibletime is really hard.  Check it out and see for yourself. :)  

Shane

---

### Post by Enverex on 2007-06-20
One (or more) of you could apply to be maintainers for the App in the AppDB and that way people would actually know that it works or not.

---

### Post by shane2peru on 2007-06-20
> **Enverex said:**
> One (or more) of you could apply to be maintainers for the App in the AppDB and that way people would actually know that it works or not.

Perhaps you could explain that a little bit.  I don't know what a maintainer is, or what his job would be.  :)

Shane

---

### Post by Enverex on 2007-06-20
An application (or version) maintainer has complete control over an application (or version of an application respectively) in the Wine Application Database. This means you can alter any part of it such as description, versions, links, notes, howtos, delete comments, etc. You can also add screenshots and test data without having to wait for it to be authorised, this also means that you become one of the people responsible for authorising or processing test data, new versions and screenshots for that app.

---

### Post by ElEdwards on 2007-06-30
In case anyone is interested, I installed Ubuntu CE 3.2 and left that version of Wine intact until yesterday, when I updated Wine to 9.40.... and everything that ran with Wine before runs now, too, including e-Sword and Adobe Audition 1.5.

:)

---

