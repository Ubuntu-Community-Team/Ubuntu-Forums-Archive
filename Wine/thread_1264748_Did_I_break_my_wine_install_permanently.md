---
title: "Did I break my wine install permanently?"
date: 2009-09-12
forum: Wine
---

### Post by jasonditz on 2009-09-12
I think I may have gone a little too far with the winetricks shell when trying to get IE6 working well enough to order my Windows 7 disk from HP's website. Now everything Wine related I try to run, even winecfg, results in the following error: 

MSVCRT.DLL for Win32
Error: MSVCRT.DLL is not compatible with Win32s

This followed me doing "sh winetricks ole2"

This seems to have Wine trying to run everything as though it was Windows 3.1, and the "Version"="Win31" is set in user.reg. However even editing user.reg by hand and changing that line to Win98 or Win2k doesn't do any good, as soon as I run wine for anything it edits user.reg and sets it back to Win31 and returns the same errors.

I don't have tons of apps installed right now, but the World of Warcraft client is over 7 GB of downloads which I'd rather not repeat if at all possible. Anyone got any idea how to fix this or am I basically stuck uninstalling and reinstalling wine and all its apps?

---

### Post by jasonditz on 2009-09-12
Since this was my day off I figured I'd take a crack at fixing this myself (in the most ***-backwards way imaginable). I guess this is how we learn, hopefully my example here can prevent other people from making the same mistake. 

Recap: The Problem:

I used winetricks to install a bunch of stuff, including OLE2, which ultimately broke my wine install.

I didn't want to lose my World of Warcraft install, because that's like 7.2 GB of downloads and Charter's probably going to complain about the download cap if I do that again. 

So what I did:

I made a copy of the World of Warcraft directory in ~/wow/
I deleted ~/.wine/ and all its contents
I uninstalled wine in synaptic
I deleted all the old links with System>Preferences>Main Menu

So its totally clean I figure, right? Probably overkill

Then I reinstall wine in synaptic.

And Guess What?

World of Warcraft runs just fine in ~/wow/ 

but... 

For some reason reinstalling it the exact same way didn't restore that Wine folder in Applications>, which isn't a deal breaker because hell... at least Wine is working again. 

But it's non-obvious how to make links in Main Menu that will wine properly. Take a look at the ones you have up there now (I did this on my laptop where I didn't totally ruin my first wine install)... I would've never guessed that in a thousand years.

What I'm doing instead: 

Though at some point I guess I could physically replace all the links by hand in Main Menu using the laptop as an example, since it's got materially all the same stuff installed, I just created a directory called ~/.wine/scripts and started putting shell scripts in there for everything I install. Then I can link to the shell script and put it wherever I want in applications. This is probably a needlessly complicated way of doing things, but what can I say, I have endless time today.

What I would suggest: 

If you go my route, for the love of god don't delete that wine directory in System>Preferences>Main Menu. Make parts of it invisible or something if you want, but leave them there... trust me it's a pain in the *** to put them back.

---

### Post by tudor117 on 2009-09-12
I had the same problem with the menu.
I uninstalled wine because it wasnt working.
Than I got angry that the menu was still there so I deleted it.
When I reinstalled wine there was no menu.

Easier way out is to "Revert" the wine menu (or if possible everything).
It worked for me but it may get rid of some shortcuts and such.

---

### Post by jasonditz on 2009-09-12
> **tudor117 said:**
> I had the same problem with the menu.
I uninstalled wine because it wasnt working.
Than I got angry that the menu was still there so I deleted it.
When I reinstalled wine there was no menu.

Easier way out is to "Revert" the wine menu (or if possible everything).
It worked for me but it may get rid of some shortcuts and such.

Maybe someone more in the loop knows if there is some script or something that wine runs to set up that menu system when it's first installed. Then we could just re-run that to get it back.

---

### Post by jasonditz on 2009-09-13
Oh man, that was easier than I thought.

Here's how you fix the stupid thing I/we did:

edit the following file:

~/.config/menus/applications.menu

It's a simple XML file (you can look at the dtd included for more details), and right below <Name>wine-wine</Name> there's a <Delete/> key. Just delete the <Delete/> and automagically it reappears.

---

### Post by Raugturi on 2009-11-07
I recently had this same issue after installing ole2 through winetricks and found what was (for me at least) a quicker and simpler solution.

First, delete the msvcrt.dll file:
```
rm ~/.wine/drive_c/windows/system32/msvcrt.dll
```Next, run winecfg and on the "Applications" tab make sure "Windows Version" is set correctly.  For me it was changed to Windows 3.1.

Finally, install "MS Visual C++6 sp4 libraries" to restore a working msvcrt.dll file.
```
cd <folder where you have winetricks>
./winetricks vcrun6
```Note: Some of the other MS Visual C++ versions may have a more recent version of msvcrt.dll, I didn't check them.

---

### Post by oedipuss on 2009-11-08
> **jasonditz said:**
> 
So what I did:

I made a copy of the World of Warcraft directory in ~/wow/
I deleted ~/.wine/ and all its contents
I uninstalled wine in synaptic
I deleted all the old links with System>Preferences>Main Menu

So its totally clean I figure, right? Probably overkill


Check out the WINEPREFIX variable. Basically, you can create a new wine environment, without uninstalling/reinstalling wine, or even deleting your old prefix in '~/.wine' .
Just run 
```
WINEPREFIX=/some/folder wine file.exe
```
or any other wine command, and it will run file.exe in that new prefix, creating it if it doesn't exist. Same goes for winetricks.

It's a quick way to try out something in a clean wine environment without messing with the old one at all. 

The menus, however, will still be a problem... I think wine just adds entries for applications without taking WINEPREFIX into consideration at all, so you'd either have to edit each launcher manually, or run everything from the command line with WINEPREFIX=....

---

