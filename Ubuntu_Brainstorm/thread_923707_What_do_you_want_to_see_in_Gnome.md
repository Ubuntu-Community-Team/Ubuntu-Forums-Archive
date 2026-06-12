---
title: "What do you want to see in Gnome?"
date: 2008-09-18
forum: Ubuntu Brainstorm
---

### Post by legolas_w on 2008-09-18
Please enter what you want to see in Gnome, maybe we can create a list and Gnome developers can take a look at it for adding them into the next version of Gnome.

- I want to be able to configure the desktop icon size, icon spacing (horizontal, vertical)

- When I am in the middle of dragging some files with the mouse  need to be able to use ALT+TAB to bring a window to the front.


Thanks

---

### Post by flatland2d on 2008-09-18
I'd definitely like to see adjustable icon spacing.  You just can't fit enough files/folders on screen at once.

---

### Post by jpeddicord on 2008-09-18
Your best bet is to file bugs at:
[http://bugzilla.gnome.org/](http://bugzilla.gnome.org/)
and Launchpad if you like.

Developers don't really read these forums, but they definitely listen to their bugtrackers. :)

---

### Post by QwUo173Hy on 2008-09-21
I'm quite happy with Gnome. If I was to pick on something, it would be performance. Sometimes I notice that nautilus can get a little slow as can a few other aspects of the system. Sometimes when I'm performing an operation like restoring a window from the sys-tray / taskbar, I find there can occasionally be a slight lag.

It's hard to quantify or describe, which is probably why it won't get fixed via bug reports. But nautilus on my machine (2GB ram, E6600 dual core processor) should be as fast as explorer on windows ME / 98.

---

### Post by lswb on 2008-09-21
Gnome developers? Looking at _user_ suggestions? Surely you must be joking!

---

### Post by gregphil on 2008-09-21
Until seemless peer-to-peer (no servers !) file sharing and browsing with Windows machines is working again, Nothing else matters!  Simple connectivity with the vast majority of personal computers MUST work.

Another words fix these bugs (which apply to all types of authenticated share browing of Windows file shares):

[Bug #207072 in gvfs (Ubuntu Hardy): “nautilus does not display samba shares for machines inside an ADS network.”]("https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072") 

[Bug 524485 - nautilus does not display samba shares for machines inside an ADS network. (gvfs)]("http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26")

---

### Post by rossjman1 on 2008-09-22
For the sake of discussion, I'll throw my 2 cents into the pile.
* A simple search bar in the applications menu. Something like this is perfect (2nd & 3rd screenshot: [http://gnome-look.org/content/show.php/Search+Menu?content=81923](http://gnome-look.org/content/show.php/Search+Menu?content=81923)
* I want to be able to go into Nautilous and try to move/delete/rename a file that is owned by root. If I do that right now, Nautilous throws an error at me saying that I don't have permissions. If Nautilous can detect that I'm trying to edit a root file it should tell me that the file is owned as root and prompt me for my password (and a cancel button that is "recommended"). I hate having to "sudo/gksudo nautilous" to do this, and users shouldn't have to create special shorcuts to do this.
* AisleRiot Solitaire should have the right click functionality like Windows. See Screenshot. I should be able to right click and have the game finish for me, so I don't have to double click each card.

---

### Post by cardinals_fan on 2008-09-22
A bullet.

To be a bit more serious, they could lighten it up a little - or a LOT.

---

### Post by Ub1476 on 2008-09-23
Integrate Gnome-Do

Power profiles (you just really can't believe the power options in Gnome right now)

Clean up, but this will come in 3.0 = 2.30

Nautilus could also do some improvements.. Check out KDE4 Dolphin for instance.

Rhythmbox (and probably several other apps) could do a small GUI fix, using space smarter and such.

---

### Post by smartboyathome on 2008-09-23
Gnome-Do is not going to happen. It uses Mono (some people are picky about that), and personally I don't see a need for it.

Power profiles would be nice, but not really GNOME-y. GNOME devs shy away from anything with extensive customizability, since they say it makes the UI harder to use.

Nautilus is outdated imo, its bloated and doesn't have many worthwhile features other file managers don't. Instead I think that GNOME should build Nautilus from scratch with 3.0, as that will at least speed it up.

I don't know about Rhythmbox, I didn't have a problem with it. But then again, I usually use MPD + one of it's numerous backents, so I don't use Rhythmbox much.

---

### Post by gnomeuser on 2008-09-23
> **smartboyathome said:**
> Gnome-Do is not going to happen. It uses Mono (some people are picky about that), and personally I don't see a need for it.


Upstream GNOME already ships Tomboy which is based on Mono. This is not a blocker.

---

### Post by smartboyathome on 2008-09-23
> **gnomeuser said:**
> Upstream GNOME already ships Tomboy which is based on Mono. This is not a blocker.

Didn't know that. I thought Tomboy was just GNOME's recognized official note taking application, not that it was included by default with GNOME.

---

### Post by 73ckn797 on 2008-09-23
I would like to see multiple file renaming in the Nautilus file browser (Places/Computer...). I guess that is not actually a part of Gnome. 

Is there a specific Gnome file browser/manager besides Nautilus?

I use Thunar with all available plugins (renamer being one)but it does not let me see other drives so I have to switch back and forth.

---

### Post by DarkDancer on 2008-09-23
Gnome Commander?

---

### Post by megamanXplosion on 2008-09-23
**Character Map**

Include common punctuation characters like the Em Dash, En Dash, Interpunct, and so on. Most monoglots would only open Character Map if they're looking for such characters, so their absence will likely frustrate them.

**Gedit**

Include in the document statistics the number of sentences, number of passive sentences, and the average number of words per sentence. Article and blog writers would find that information useful.

Let the user change the line-height of text. It is irritating to sort through fonts, find one that looks good, apply it, and then learn it gives a half-inch space between lines, which looks horrible; then, you hunt for another font, apply it, and the problem arises again; then, again; then, again. It can make you want to scream.

**Keyboard Functionality**

Add alt-code support for common Unicode characters. To type an Em Dash on Windows, you use <Alt+0151>; on Linux, you use <Shift+Ctrl+U+2014>, which is more difficult. The hexadecimal system is useful for uncommon characters, but for common ones, alt-codes are preferable. The alt-code support should complement, not replace, the hexadecimal approach. The alt-codes support should match that on Windows so people can transition to Linux from Windows without learning a new way of typing common Unicode characters.

---

### Post by irrdev on 2008-09-24
**1.** Update Nautilus - compared to Konqueror, or even the new KDE4 Dolphin file manager, Nautilus has to be the worst file manager included with any modern OS. Split windows, new interface, editable toolbar, smaller size, GTK+ 2... these are all necessary features and upgrades.

**2.** More modern GUI interface to compete with Mac, Vista and now KDE 4. The panels should support gradient colors. Metacity should support transparency and "highlights". The Appearance Window should be redesigned, the Control Centre should become more functional and the Main Menu should be far more eye-pleasing - not just a menubar applet.

**3.** Return Gnome Screensaver Settings option. How many other desktops don't include this necessary feature? I seriously can't believe that Gnome ever dropped this...

---

### Post by bruce89 on 2008-09-24
> **megamanXplosion said:**
> **Character Map**

Include common punctuation characters like the Em Dash, En Dash, Interpunct, and so on. Most monoglots would only open Character Map if they're looking for such characters, so their absence will likely frustrate them.


They are in there somewhere.


> **megamanXplosion said:**
> **Gedit**

Include in the document statistics the number of sentences, number of passive sentences, and the average number of words per sentence. Article and blog writers would find that information useful.

Let the user change the line-height of text. It is irritating to sort through fonts, find one that looks good, apply it, and then learn it gives a half-inch space between lines, which looks horrible; then, you hunt for another font, apply it, and the problem arises again; then, again; then, again. It can make you want to scream.


gedit isn't that kind of text editor. It is meant for simple text files, configuration files or programming.

> **megamanXplosion said:**
> **Keyboard Functionality**

Add alt-code support for common Unicode characters. To type an Em Dash on Windows, you use <Alt+0151>; on Linux, you use <Shift+Ctrl+U+2014>, which is more difficult. The hexadecimal system is useful for uncommon characters, but for common ones, alt-codes are preferable. The alt-code support should complement, not replace, the hexadecimal approach. The alt-codes support should match that on Windows so people can transition to Linux from Windows without learning a new way of typing common Unicode characters.

> **irrdev said:**
> **1.** Update Nautilus [...], GTK+ 2... these are all necessary features and upgrades.

Nautilus has been using GTK+ 2.0 since it begun.

> **irrdev said:**
> **2.** [...] Metacity should support transparency and "highlights".

It already does. Enable compositing mode in gconf.

> **irrdev said:**
> **3.** Return Gnome Screensaver Settings option. How many other desktops don't include this necessary feature? I seriously can't believe that Gnome ever dropped this...

They didn't drop this. *xscreensaver* was the program used in the past which had all the options. The GNOME people decided to write their own one, *gnome-screensaver*. It has never had configurable screensavers (thankfully).

---

### Post by megamanXplosion on 2008-09-25
> **bruce89][quote=megamanXplosion]**Character Map**

Include common punctuation characters like the Em Dash, En Dash, Interpunct, and so on. Most monoglots would only open Character Map if they're looking for such characters, so their absence will likely frustrate them.[/quote]

They are in there somewhere.[/quote]

If the Character Map does have those characters, it doesn't show them in the Latin or Greek sections&#8212 said:**
> [quote=megamanXplosion]**Gedit**

Include in the document statistics the number of sentences, number of passive sentences, and the average number of words per sentence. Article and blog writers would find that information useful.

Let the user change the line-height of text. It is irritating to sort through fonts, find one that looks good, apply it, and then learn it gives a half-inch space between lines, which looks horrible; then, you hunt for another font, apply it, and the problem arises again; then, again; then, again. It can make you want to scream.

gedit isn't that kind of text editor. It is meant for simple text files, configuration files or programming.[/quote]

Gedit is a general purpose text editor. Considering this, it should make itself useful to more than just programmers and IT personnel. It should help those who would like to use it to write forum posts, blog entries, wiki articles, emails, and more.

To an extent, it already does. It includes automated spell-check and it includes word-count in the document statistics dialog. I think the developers should extend its functionality for the group who finds those features useful. If they find particular fonts easy on the eyes but the line-height needlessly pushes text off the screen, let the user to change the line-height. If they find that they have used too many words, tell them the number of passive sentences (or verbs) to inform them that they can reduce the word-count without removing information. In short, extend the functionality to help them accomplish their tasks.

---

### Post by angustia on 2008-09-26
something i just have in mind:

something like a global hidden console (maybe displayable by a key combination like tilda), that shows the stderr of any program started by the application menu or launchers or .desktop files in nautilus.

This is because many times i have launched programs (usually things downloaded and compiled by me) and those programs crashed. If i launched them by nautilus, i just see the program disappear and i'm forced to open a terminal and relaunch the program just to see what the error was.

So, this hidden console could act like the stdout/stderr of every program, if i launch a program and i see it dissapear, i can just check this console to see if there was something bad without having to repeat the whole step to reproduce the crash*.

(even the console can show a notification if there was some stderr output)

excuse my english

* the common thing is some missing library

---

### Post by mmcmonster on 2008-09-27
How about keeping high scores and other statistics in gnome-sudoku?

---

### Post by wildman4god on 2008-09-30
In windows XP explorer you can arange items in separate and labeled groups, this makes it much easier to find a file you just downloaded, I would like to see this in nautilus or whatever file manager they decide to use in the future. 

Also in XP you can hide files by selecting an option rather and putting a dot in front of the file name, which makes the file unrecognized by its application, I have found a script to do this with the right click menu, but it should be included in the file manager.

---

### Post by bruce89 on 2008-09-30
> **wildman4god said:**
> In windows XP explorer you can arange items in separate and labeled groups, this makes it much easier to find a file you just downloaded, I would like to see this in nautilus or whatever file manager they decide to use in the future.

Surely folders do much the same thing?

> **wildman4god said:**
> Also in XP you can hide files by selecting an option rather and putting a dot in front of the file name, which makes the file unrecognized by its application, I have found a script to do this with the right click menu, but it should be included in the file manager.

That would be fairly easy to implement (probably as a nautilus extension), but not really useful.

---

### Post by Merk42 on 2008-09-30
> **bruce89 said:**
> Surely folders do much the same thing?

No, you can easily change how the items are grouped in Windows XP, the same way you can change how something is arranged in Nautilus when in list view by clicking on the "name" "size" "type" etc at the top.

---

### Post by wildman4god on 2008-10-01
> **bruce89 said:**
> Surely folders do much the same thing?



That would be fairly easy to implement (probably as a nautilus extension), but not really useful.

It would be useful as mainly an asthetic option, because i am a neat freak, I don't like my home folder clutered with system files that i don't need to access outside its program any way, and I want to hide them from normal site. I know you could do this with the "put a dot in front of file name" option but that makes it unrecognixed by its program. And in xp if you right click in the arange items group there is a "show in groups" option, so if you have the items aranged by type and then you select this option all the jpegs will be in a labled field the all the bmps and pngs, etc. this makes it eaiser for manual searching of a file.

---

### Post by bruce89 on 2008-10-01
> **wildman4god said:**
> It would be useful as mainly an asthetic option, because i am a neat freak, I don't like my home folder clutered with system files that i don't need to access outside its program any way, and I want to hide them from normal site. I know you could do this with the "put a dot in front of file name" option but that makes it unrecognixed by its program. And in xp if you right click in the arange items group there is a "show in groups" option, so if you have the items aranged by type and then you select this option all the jpegs will be in a labled field the all the bmps and pngs, etc. this makes it eaiser for manual searching of a file.

There's a good reason why the dot file approach has been used for all these years - All programs know to hide them.

Any programs that have settings etc. in non-dot folders are broken.

---

### Post by wildman4god on 2008-10-02
No they all don't, because I have a N64 emulator and it puts a system file in my home folder, and when I went to hide it with the dot method, the emulator no longer recognized it. So again I want to hide a file without changing the file name.

---

### Post by smartboyathome on 2008-10-02
> **wildman4god said:**
> No they all don't, because I have a N64 emulator and it puts a system file in my home folder, and when I went to hide it with the dot method, the emulator no longer recognized it. So again I want to hide a file without changing the file name.

You want Gobohide then (no, not the filesystem structure, the program used to hide the symlinks :p). It will allow you to hide the folder with a simple command, but requires patching the kernel and installing a program.

---

### Post by junior aspirin on 2008-10-02
> **wildman4god said:**
> No they all don't, because I have a N64 emulator and it puts a system file in my home folder, and when I went to hide it with the dot method, the emulator no longer recognized it. So again I want to hide a file without changing the file name.

you can also hide a file by creating a file called ".hidden" in the same directory and entering the file name.

eg. if i want to hide "/home/me/somefile.txt" i can create "/home/me/.hidden". open it up and enter "somefile.txt". then nautilus will hide said file.

---

### Post by smartboyathome on 2008-10-02
> **junior aspirin said:**
> you can also hide a file by creating a file called ".hidden" in the same directory and entering the file name.

eg. if i want to hide "/home/me/somefile.txt" i can create "/home/me/.hidden". open it up and enter "somefile.txt". then nautilus will hide said file.

Cool, I didn't know that. :)

---

### Post by cmay on 2008-10-03
i like gnome very much. i always use gnome on linux. but on bsd and some linux live cd i found some tings could be included in a gnome desktop. 
1 i would like a download button for wall papers  like  kde4 can do.
2 some mouse control menu in gnome. 
other than that i like gnome very much and i do not miss the features so much i am going to switch desktop.

---

### Post by davbren on 2008-10-03
I would like to see more previews of files in Gnome. Using the mouse to roll-over, it shows a big version of what you're rolling-over. I think this would be pretty cool. This includes movies too...

The main problem with this I can see is that it might bloat the file manager...

---

