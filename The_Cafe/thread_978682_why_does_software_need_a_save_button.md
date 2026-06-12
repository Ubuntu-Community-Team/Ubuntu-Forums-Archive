---
title: "why does software need a save button?"
date: 2008-11-11
forum: The Cafe
---

### Post by daverich on 2008-11-11
[http://www.techradar.com/news/computing/why-does-software-need-a-save-option--483797](http://www.techradar.com/news/computing/why-does-software-need-a-save-option--483797)

this really is quite interesting.

I can see the point of a Save AS button,- but using Open Movie Editor,- which doesn't have a save button, it just saves as you go - seems to be rather more sensible.

What say you?

Kind regards

Dave Rich

---

### Post by dustman on 2008-11-11
Well, I use Eclipse IDE a lot, and Ctrl+S (Save) it's already in my blood. I can't help saving after each 2-3 lines of code. Why? Because it's very convenient to have all your code the way you had it after a power breakdown, or a software bug, or whatever.
It happened to me a lot of times that I deleted the whole content of a file, then just switched to another window, then to another window, and forgot that I've deleted text in the file. When I close the editor window, the message window that saves the day is: "Do you want to save the modifications made to Foo.doc? " - Hell no!

Regards,

Radu

---

### Post by tuxsheadache on 2008-11-11
Save buttons can mean you can save your data in a certain state. You may overwrite some data you thought was not good anymore, but later decided it was useful. For example, some games save as you go along, which can be incredibly annoying if it saves the game at a point where you have low health and low ammunition. If you had saved it yourself, you would probably die at that part of the game, reload your old save, and know what to expect, so know when to use the big gun etc. Automatic saves stop this.
 It's also the reason why some people backup their systems on different DVDs depending on the date, so if they realise they are missing some data from a while back they know they have a copy of it somewhere.
 Personally, I save only when I need to, because I have a reliable machine. Many years of using an old unreliable computers has also taught me to save as often as possible though =D

---

### Post by billgoldberg on 2008-11-11
I didn't read the article, but one thing I find useful in gnome that isn't so in Windows and KDE is that when you save a setting, you don't have to "apply" or "save" anything.

As soon you change something, it's done.

---

### Post by tuxsheadache on 2008-11-11
I suppose it's just a control thing. I don't want everything automatic, I want to make sure there is still a human decision in my computing decisions :D

---

### Post by miggols99 on 2008-11-11
> **billgoldberg said:**
> I didn't read the article, but one thing I find useful in gnome that isn't so in Windows and KDE is that when you save a setting, you don't have to "apply" or "save" anything.

As soon you change something, it's done.
Personally, I don't really like this feature. Like when I go to change some settings, and I forget what was there before...I can't undo it so that means I'll have to look it up, guess or leave it..

---

### Post by jespdj on 2008-11-11
> **miggols99 said:**
> Personally, I don't really like this feature. Like when I go to change some settings, and I forget what was there before...I can't undo it so that means I'll have to look it up, guess or leave it..
Me too! Because changes go into effect immediately, you can't easily undo those changes. That's annoying. I'd rather have Apply / Ok / Cancel buttons instead of the way it works now.

---

### Post by klange on 2008-11-11
Because sometimes people go in to make changes, then decide everything they did was worthless. It takes more disk space (and more read/writes) to make a backup when you open a file than it does to just let the user save when they feel like it.

---

### Post by daverich on 2008-11-11
> **WindowsSucks said:**
> Because sometimes people go in to make changes, then decide everything they did was worthless. It takes more disk space (and more read/writes) to make a backup when you open a file than it does to just let the user save when they feel like it.

true,- but as stated in that link,- isn't this the job of undo?

Kind regards

Dave Rich

---

### Post by insane_alien on 2008-11-11
from reading the article it appears the author is asking for everything you do to be written to disk WHEN you do it. you type a letter, it gets saved to disk, you press back space, it gets saved to disk and so on.

appart from the excessive read-modify-write cycles this will produce it probably wouldn't do much for fragmentation either.

that said, you can set up some software to save every few minutes/*insert arbitrary number of character* or something along those lines.

the save button is just a manual 'write changes to disk' button.

---

### Post by forrestcupp on 2008-11-11
> **tuxsheadache said:**
> Save buttons can mean you can save your data in a certain state.
+1

I don't want the software deciding at which state to save my work.  I'm bound to really screw something up and find out the software saved my work *after* I screwed it up.

You might say, what about undo?  Well, what if I screw my work up and decide to just close the program knowing that I have a good version saved, only to open it back up later to find out that the software saved it after I messed up and right before I closed it?  Then undo doesn't mean squat.

Automatic save is **bad**.

---

### Post by MaxIBoy on 2008-11-11
> **dustman said:**
> 
It happened to me a lot of times that I deleted the whole content of a file, then just switched to another window, then to another window, and forgot that I've deleted text in the file. When I close the editor window, the message window that saves the day is: "Do you want to save the modifications made to Foo.doc? " - Hell no!

Regards,

Radu

You wouldn't *believe* the number of times that's saved my butt.

---

### Post by koenn on 2008-11-11
> **daverich said:**
> [http://www.techradar.com/news/computing/why-does-software-need-a-save-option--483797](http://www.techradar.com/news/computing/why-does-software-need-a-save-option--483797)

this really is quite interesting.

I can see the point of a Save AS button,- but using Open Movie Editor,- which doesn't have a save button, it just saves as you go - seems to be rather more sensible.

What say you?

Kind regards

Dave Rich
If you think this is interesting, you're easily impressed.
The author wants every change saved instantaneously.
Normally, files are loaded into RAM, edited there, and written back when you save. Originally, this was because disks (or even tapes) were incredibly slow. Even now, when disks are faster, I wonder what the effect would be if every letter you type in a file, every modification to a picture, ... would have to be written to disk _immediately_ (while, in a multitasking system, other programs might be writing to other files also, so the write heads of the disks would be moving all over the disk all the time). 
Maybe it's different with solid state disks ? 

I'm not familiar with video editing, but I would guess your program does some sort of periodic save - which is something the author objects against as well. He wants it instantaneous.

To cover the 'I don't want to save this massive edit I just did by accident' case, the author refers to 'undo'. In fact, he says "the file should preserve every edit so that I can roll back to any previous point indefinitely". Disk space may be relatively cheap, yet we're all always running out of space. And then you want to retain all previous versions of every file you ever edited ? Even with an intelligent system that only keeps the differential, that could easily become a lot of bits.

As  for his rant about dialog boxes, it's true that they can be annoying, especially the endless confirmations : you basically have to say everything twice. "Save this file." "Are you sure ?" "Yes. now, save it". 
On the other hand, There aren't many ways to communicate with a user in a GUI environment. You can't just put some text on screen and let it stay there until it scrolls of the top of the screen, the way you do in a console.

The author claims he's was a developer, and that he knows how to create user interfaces that don't need all these dialogs and OK's. So, where are they? Why isn't he writing them?

---

### Post by tuxsheadache on 2008-11-11
All in all it would be a waste of computer resources, considering all it takes is a person to press CTRL + S on most programs. I would much rather keep the remaining power and control over such a command, leaving the computer to do more important things and making sure i get a copy of what I want. At least if something went wrong you can only blame yourself instead of a machine.

---

### Post by ericmc783 on 2008-11-11
I agree with the majority of the replies here. I PREFER the software ask me to save, as well as having to hit CTRL+S. That way I can make revisions and "versions" of the file as I go. In case one of them gets messed up, go back to the other.

---

### Post by clanky on 2008-11-11
I like the idea that I can open a document, edit it, decide that I don't like the edits and close it without saving any changes.

An auto save option is OK, but IMO it should not be the default setting.

---

### Post by jimi_hendrix on 2008-11-11
best idea is probably to combine the two...have one file that it will autosave to and one file that it will save to when you hit the button...screw up a lot of stuff? open the last time you hit save...power outage? open up your autosave

---

### Post by pp. on 2008-11-11
This thread names issues which ought to be separate but which are rarely even perceived as such.

One: persistence. It is not an intuitive notion that whatever I do to a document is subject to being saved at a later time. Paper does not behave that way. Neither does clay. Neither does stone. It is absurd that I lose a day's, an hour's, a minute's or a second's worth of work through a malfunction of the hardware, software or wetware (aka inattention). This applies to desktop publishing just as well as to messaging, doodling or whatever kind of input I am trusting my computer with.

Two: rolling back. Because not every change is an improvement, I need the capability to roll back my changes by any number of changes or over an arbitrary time span. While we're at it, I also want to selectively redo the changes I've undone.

Three: committing or taking checkpoints, aka versioning. There are several reasons why I want to establish named and fixed version which existed at a known point in time. 

Four: serializing. The document has to be presented as a serial stream of data elements so that other programs can use the same document. It'd be just too much to expect that a program stores just the changes, and stores them in a way which was perfectly acceptable to all other programs which had to process the same document for entirely different purposes.

Five: speed of execution. Traditionally, computers used to be so feeble and slow that they could not usefully accept any more input while the program tried to save what i'd written to a more or less permanent medium. Also, the technology to save and use the changed parts only had to develop a good deal until it became useable. That's at the root of the explicit saving command.

I might have missed a few. 

On the whole, I'd rather have my software instantly save my work after the shortest possible delay while still being able to revert in a manner as flexible as possible.

---

### Post by koenn on 2008-11-11
> **pp. said:**
> This thread names issues which ought to be separate but which are rarely even perceived as such.

...

You make a better point that the article the OP refers to :)

---

### Post by tuxsheadache on 2008-11-11
I am personally impressed by how much thought has been put into a situation I would never have thought off until it was raised.

---

### Post by mssever on 2008-11-11
Two thoughts:

First, there exists an editor that autosaves: scribes (in the repos).

Second, some devices have a finite number of writes before wearing out. Autosave wouldn't bee good on such devices.

---

### Post by Tomosaur on 2008-11-11
Ok:

1: Saving after every single keystroke requires opening the previous file, making the required changes, and closing the file again. If you are doing this at every keystroke, be prepared to buy a new hard drive in a few months time (This would not be a particularly big problem on solid-state drives, but the vast, vast majority of people use hard disks).

2: Modern operating systems and applications generally buffer all I/O. Just because you have pressed a key does not mean the target application is aware of it, or will receive that input. Sure, it's not a huge problem having one or two characters missing the next time you open the file, but the point still remains that a regular auto-save is a much better solution than just constantly saving after every single modification!

---

### Post by aysiu on 2008-11-11
Why not provide the option?

I can see pros and cons to either approach, and I know some people like instantaneous saves and others like manual saves.

Why can't we just leave it up to the user?

---

### Post by handy on 2008-11-11
[***_eToys_***]("http://waveplace.com/resources/tutorials/") automatically saves your work when you quit, it also has the option to save/save as, at any time.

I think the option to save/save as, is great, I also like to be able to set a save time, from  every minute to whatever.

It all depends on what you are doing.

---

### Post by pp. on 2008-11-12
> **Tomosaur said:**
> 1: Saving after every single keystroke requires opening the previous file, making the required changes, and closing the file again.

No, it doesn't. The concept of the change log has been invented decades ago. The original file remains unchanged for some time and all changes are logged to a serial data stream. That data stream is usually implemented as a straightforward file where new data is appended to the end.

> **Tomosaur said:**
> If you are doing this at every keystroke, be prepared to buy a new hard drive in a few months time (This would not be a particularly big problem on solid-state drives, but the vast, vast majority of people use hard disks).

What you are saying is that some very basic needs of practically every computer user can not be fulfilled because the computer industry is unable or unwilling to provide the needed hardware capabilities. Adding some persistent solid state memory to a motherboard or to the cache of a disk drive can not be that great a challenge for the hardware industry. Presuming a user to type at a rate of 20 characters per second at a sustained rate, and assuming a ratio of overhead to data of 10:1, you could store one hour's worth of typing in 720'000 bytes.

How many megabytes of cache RAM does your typical HDD carry?

Besides, such a capability would be a boon even to users who only wanted their stuff saved after klicking on the diskette icon. Spinning the disk up and down is one of the major power drains and performance stoppers in a great many mobile computers.


> **Tomosaur said:**
> 
2: Modern operating systems and applications generally buffer all I/O. Just because you have pressed a key does not mean the target application is aware of it, or will receive that input.

That happens not to be the case. It has been a long time since I last used a word processing program where the display remained unchanged while I typed. Or a property editor which did not display what I entered/clicked on the very instant I did so.

Hence, in the typical setting the application does receive the user's input within a very short time frame.

> **Tomosaur said:**
> 
the point still remains that a regular auto-save is a much better solution than just constantly saving after every single modification!

"Better" for whom and for which purpose? And which interval for the "regular auto save" would be the best one?

---

### Post by pp. on 2008-11-12
> **aysiu said:**
> 
Why can't we just leave it up to the user?

I'd be perfectly happy with that. However, currently available software does not usually offer the option for saving your work instantly.

---

### Post by SupaSonic on 2008-11-12
> **tuxsheadache said:**
> Save buttons can mean you can save your data in a certain state. You may overwrite some data you thought was not good anymore, but later decided it was useful. For example, some games save as you go along, which can be incredibly annoying if it saves the game at a point where you have low health and low ammunition. If you had saved it yourself, you would probably die at that part of the game, reload your old save, and know what to expect, so know when to use the big gun etc. Automatic saves stop this.
 It's also the reason why some people backup their systems on different DVDs depending on the date, so if they realise they are missing some data from a while back they know they have a copy of it somewhere.
 Personally, I save only when I need to, because I have a reliable machine. Many years of using an old unreliable computers has also taught me to save as often as possible though =D

Speaking about eclipse, it has a feature called 'Local History'. You can view previously saved versions of any text file. That came in handy quite a few times. This info isn't stored in the file itself though, but within a special hidden folder.

---

### Post by forrestcupp on 2008-11-12
> **jimi_hendrix said:**
> best idea is probably to combine the two...have one file that it will autosave to and one file that it will save to when you hit the button...screw up a lot of stuff? open the last time you hit save...power outage? open up your autosave

This is already how most software that autosaves works.  It saves your current work every couple of minutes to a temporary backup file.  Then if something happens, you can restore to that autosave.

I don't have a problem with autosave in this way, as long as it's not saving to my main file.  Just don't take away my option to manually save.

---

### Post by Tomosaur on 2008-11-12
> **pp. said:**
> No, it doesn't. The concept of the change log has been invented decades ago. The original file remains unchanged for some time and all changes are logged to a serial data stream. That data stream is usually implemented as a straightforward file where new data is appended to the end.
That is not saving the file after every keystroke - that is preparing a file for a save to the 'master' file at a future point (ie: autosave at some interval, which is what I suggested is the better option).

> 
What you are saying is that some very basic needs of practically every computer user can not be fulfilled because the computer industry is unable or unwilling to provide the needed hardware capabilities. Adding some persistent solid state memory to a motherboard or to the cache of a disk drive can not be that great a challenge for the hardware industry. Presuming a user to type at a rate of 20 characters per second at a sustained rate, and assuming a ratio of overhead to data of 10:1, you could store one hour's worth of typing in 720'000 bytes.
Who, exactly, is 'the hardware industry'? It is not some unified, over-arching corporate entity. People use hardware for years and new changes take years to trickle down and become the standard. I have no doubt that such changes WILL take place, but they will not take place tomorrow.

> Besides, such a capability would be a boon even to users who only wanted their stuff saved after klicking on the diskette icon.
I never said it wouldn't be, just why it's not such a great idea considering the current ecosystem of machines.

> Spinning the disk up and down is one of the major power drains and performance stoppers in a great many mobile computers.
Yes, it is. We do not disagree. But since the majority of machines in use, and machines which will be in use for the foreseeable future use disk drives for persistent storage, you'll just have to put up with it. Most technology that makes its way into our homes is imperfect but 'good enough' to do what you need it to do. Getting it to do what you WANT it to do is a whole different ball-game.


> 
That happens not to be the case. It has been a long time since I last used a word processing program where the display remained unchanged while I typed. Or a property editor which did not display what I entered/clicked on the very instant I did so.

Hence, in the typical setting the application does receive the user's input within a very short time frame.

And the light you see from a car headlights when they're switched on still takes time to travel to you, even though it looks instantaneous. A 'very short time frame' is not 'instant' - and thus leaves room for changes to be missed off in the event of a power failure. As I said, for word processing, it's not such a big deal if one or two characters were to get left off from the end of your file if your power fails - but for anything which requires large amounts of CPU time to reflect changes (professional image processing, 3d rendering etc etc), then saving every change as it happens suddenly becomes both impractical and risky (file-saving in itself introduces another point-of-failure which could in fact cause you to crash your system and lose your work). It is best to minimise risky behaviour wherever possible.

Perhaps I'm not explaining myself very well, so think of it like this: Just because you assume your computer will do something automatically does not mean it actually will. It is not possible to guarantee a successful file-save which after every change. This is just how computers work. What you perceive to be instant is just 'very, very quick'. At the speeds your computer works, typing looks instant. That doesn't mean it actually is.


> 
"Better" for whom and for which purpose? And which interval for the "regular auto save" would be the best one?
Everybody without money to burn on new hard drives, perhaps? And for the regular auto save, I would suggest just a few minutes. Humans are more than capable of remembering the steps they took a few minutes before their computer died on them. Indeed, MOST people use a rather erratic, trial-and-error approach to writing. Unless you are absolutely flawless and type everything in a fluent, coherent, and correct manner every time you write - then saving your work after every single keystroke is just adding needless wear and tear.

I'm all for having it as an option - but don't come crying to me when your hard drive dies and you lose all the work you wanted to save so badly :P

---

