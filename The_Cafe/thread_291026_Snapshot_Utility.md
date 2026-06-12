---
title: "Snapshot Utility"
date: 2006-11-01
forum: The Cafe
---

### Post by metiosarius on 2006-11-01
The snapshot utility that ships with Ubuntu is very primitive; and it always shows "starting snapshot" in every screenshot which is annoying.

I have been taking numerous screenshots using the utility for a presentation that I am doing on Linux (particularly focusing on Ubuntu) and have found it to be lacking.

Ubuntu should strive to make a default gnome utility similar to KSnapshot which is far more advanced...

Any one else agree?

---

### Post by meng on 2006-11-01
One *could* remove the window list from the bottom panel or hide the panel altogether, then there it wouldn't say "starting snapshot" (GNOME by default announces whenever an application is starting, be it snapshot, firefox or evolution). Otherwise, what problems do you have with it?

---

### Post by metiosarius on 2006-11-01
Alright;

_Ubuntu "Take Screenshot";_

[LIST]
[*]It ONLY takes snapshots of the ENTIRE screen.
[*]It takes snapshots ONLY when first STARTING the application.
[/LIST]
_KSnapshot;_
[list]
[*]Can take snapshots of just a window. (with or without decorations)
[*]Can take snapshots of only a particular region (which saves time because you can avoid cropping snapshots)
[*]Has a time delay feature (which is useful for getting snapshots of menus)
[*]Can take multiple shots instead of only on startup.
[/list]

As you can see, KSnapshot is a far more advanced application.

---

### Post by aysiu on 2006-11-01
Is there a command where you can launch KSnapshot to take only the window? Or do you have to wait until it's already loaded and then specify the option? This is a genuine question, and if you have an answer, I'd be glad to know it, as I use KSnapshot in KDE and Gnome Screenshot in IceWM, XFCE, and Gnome.

One of the great things I love about Gnome Screenshot is that I can have separate commands for different keyboard shortcuts, so I don't have to wait until the application loads in order to specify different types of screenshots to take:
 
**Full screen** ```
gnome-screenshot
``` **Active window** ```
gnome-screenshot --window
``` **Time delay screenshot** ```
gnome-screenshot --delay 5
```

---

### Post by metiosarius on 2006-11-02
I have always used it from the GUI (after the program loads)- I've never tried taking shots from the CLI; so, I dont have an answer. I attempted to look in the documentation for KSnapshot on my system, but, I dont have the KDEHelpCenter installed, so - I dont have that info...

Maybe a quick web search could answer your question.

Another thing that interested me about your post is that you CAN use things such as the --window option from the CLI - these features should be included in the GUI...so, it seems to me that the functionality is already there, just not revealed through the GUI. 

The reality is that I wont ever use a CLI to take a screenshot - I feel this is something the GUI handles quicker. (And I do enjoy my CLI; just not for screenshots :) )

---

### Post by aysiu on 2006-11-02
I don't use the CLI.

I just associate the commands with a keyboard shortcut--much faster than waiting for the GUI to come up to choose my option.

Two of them you don't even have to know the command for. You can just define them in System > Preferences > Keyboard Shortcuts

The last (*gnome-screenshot --delay 5*) you'd have to associate the command manually, but after that you could just press the key combination--no terminal necessary.

I can't make head or tails of these instructions for KSnapshot. What's DCOP? ```
Chapter 3. DCOP Interface
KSnapshot can be scripted using its DCOP interface. This chapter explains the various DCOP calls that you can use, and provides some examples of how you can use them.
As with all DCOP calls, you need to specify the application you want to interface with, and the particular interface. With KSnapshot you need to identify which particular application, which is ksnapshot- followed by the process number.
To start KSnapshot and obtain the right argument, use dcopstart ksnapshot, which returns the argument (such as ksnapshot-20594) on standard output.
You can get a list of the available DCOP interfaces, use the right arguments, as shown in this example: 
$ dcop `dcopstart ksnapshot` interface
QCStringList interfaces()
QCStringList functions()
QString url()
void slotGrab()
void slotPrint()
void slotSave()
bool save(QString filename)
void slotSaveAs()
void slotCopy()
void setTime(int newTime)
int timeout()
void setURL(QString newURL)
void setGrabMode(int grab)
int grabMode()
void slotMovePointer(int x,int y)
void exit()


 In the examples following, the process is always ksnapshot-23151. 
DCOP Access to Settings
For each of the settings that you can control with the GUI, you can both obtain the current status of that setting, and modify the setting, using DCOP. 
You can obtain the current capture mode using grabMode, as shown below: 
$ dcop ksnapshot-23151 interface grabMode

 This will return 0 for full-screen capture, 1 for window capture, and 2 for region capture. 
You can set the capture mode using setGrabMode, which requires an argument to identify the mode required (as for grabMode). So you can set window capture mode (1), using: 
$ dcop ksnapshot-23151 interface setGrabMode 1

You can obtain the current timeout setting (the Snapshot delay: GUI item) using timeout, as shown below: 
$ dcop ksnapshot-23151 interface timeout

 This will return the timeout setting in seconds, or zero if there is no delay (capture on click). 
You can set the timeout using setTime, which requires an argument to identify the timeout duration. So you can set a delay of 4 seconds using: 
$ dcop ksnapshot-23151 interface setTime 4

You can obtain the path that the snapshot will be saved to using url, as shown below: 
$dcop ksnapshot-23151 interface url

 This will return the filename, as a URL (eg as file:///home/bradh/test2.png). 
You can set the path using setURL, which requires a string argument to identify the new path. So you can set the path to file:///home/bradh/snapshot.jpg using: 
$ dcop ksnapshot-23151 interface setURL file:///home/bradh/snapshot.jpg

Taking Screenshots with DCOP
 The key to taking screenshots with DCOP is use of slotGrab, as shown below: 
$ dcop ksnapshot-23151 interface slotGrab

 This will take a snapshot using the current snapshot mode and timeout settings (as described above). If you want to save the snapshot image, there are a number of calls you can use. If you just want to save the image to the current path (as returned by url or changed by setURL), you can use slotSave, as shown below: 
$ dcop ksnapshot-23151 interface slotSave

 If you want the user to be able to specify a filename (and path), you can use slotSaveAs, which will bring up a standard KDE file save dialog.
 If you want to save the image to a different name (or path) without changing the path with setURL, you can use save, providing the URL to save to as an argument. So if you want to save the snapshot to file:///tmp/tempshot.png, you can do the following: 
$ dcop ksnapshot-23151 interface save file:///tmp/tempshot.png

 Note that this will return true if the snapshot was successfully saved, and false otherwise. Also, you should be aware that if the file already exists, the user will get a standard KDE dialog that requires the user to decide whether to overwrite or not. 
 In addition to saving the snapshot, you can also copy it to the clipboard, using slotCopy, as shown below: 
$ dcop ksnapshot-23151 interface slotCopy

 If you need to select a window that may not be under the mouse cursor, you can use slotMovePointer, passing the x position (in screen pixels) and the y position (also in screen pixels) as arguments. So to move the mouse to the top left hand corner of the screen (0,0), you can do the following: 
$ dcop ksnapshot-23151 interface slotMoveMouse 0 0

Printing Screenshots with DCOP
 You can print the current screenshot (which may or may not have been saved) using printSlot, as shown below: 
$ dcop ksnapshot-23151 interface slotPrint

 Note that this will bring up the normal KDE print dialog, which may require user interaction. 

DCOP Application control
 You can cause KSnapshot to exit by using exit, as shown below. 
$ dcop ksnapshot-23151 interface exit
``` And the *man* page doesn't offer much: ```
DESCRIPTION
This manual page documents briefly the KSnapshot KDE Application. This manual page was written for the Debian GNU/Linux distribution because the original program does not have a manual page. KSnapshot is a simple applet for taking screenshots. It is capable of capturing images of either the whole desktop or just a single window. The images can then be saved in a variety of formats.

KDE Screenshot utility This program is part of the official KDE graphics module.  
Generic options:

--help
    Show help about options 
--help-qt
    Show Qt specific options 
--help-kde
    Show KDE specific options 
--help-all
    Show all options 
--author
    Show author information 
-v, --version
    Show version information 
--license
    Show license information 
--
    End of options 

 
SEE ALSO
The full documentation for KSnapshot is maintained as a docbook manual. If the khelpcenter program is properly installed at your site, the command

    khelpcenter help:/ksnapshot 

should give you access to the complete manual.  
AUTHOR
KSnapshot was written by Richard J. Moore <rich@kde.org>, Matthias Ettrich <ettrich@kde.org> and Aaron J. Seigo <aseigo@olympusproject.org>.
Please use http://bugs.kde.org to report bugs, do not mail the authors directly.
This manual page was prepared by Karolina Lindqvist <pgd-karolinali@algonet.se> for the Debian GNU/Linux system (but may be used by others).
```

---

### Post by metiosarius on 2006-11-02
Alright - I can handle the keyboard shortcuts :)

Even though I still think a better GUI for the snapshot utlity should be developed; i really need to learn how to program better....lol

---

### Post by kuja on 2006-11-02
Aysiu: ksnapshot --current

---

### Post by metiosarius on 2006-11-02
Im not exactly sure what DCOP does - I think it has something to do with window management in KDE.

So, no help from me there....sry.

---

### Post by aysiu on 2006-11-02
> **kuja said:**
> Aysiu: ksnapshot --current
Cool! That's exactly what I need.

Can I ask how you know that?

---

### Post by kuja on 2006-11-02
Edit: I was going to say something, but I like maniacmusician's explanation better :mrgreen:

---

### Post by maniacmusician on 2006-11-02
> **aysiu said:**
> Cool! That's exactly what I need.

Can I ask how you know that?
he has the blessed K in his name is how ;)

---

### Post by argie on 2006-11-02
Hmm, in Windows, the screenshot would go to the clipboard. Sometimes, that's nice. Is it possible to make it act like this without popping up that "Save Screenshot" box?

---

### Post by kuja on 2006-11-02
> **argie said:**
> Hmm, in Windows, the screenshot would go to the clipboard. Sometimes, that's nice. Is it possible to make it act like this without popping up that "Save Screenshot" box?
I believe, at least in Kubuntu, that the clipboard screenshot option is set to ctrl + printscreen for the fullscreen, and left_alt + printscreen for the current window.

---

### Post by Roger Mudd on 2006-11-02
I've always used the following:

Print Screen = Full Screen Screenshot
ALT-Print Screen = Active Window Screenshot

Simple, yet it works for me. And you won't have an instance of a screenshot utility in your panel.

---

### Post by maniacmusician on 2006-11-02
> Edit: I was going to say something, but I like maniacmusician's explanation better 

I think what you were going to say was very helpful too (I like my explanation as well...but people probably want a serious answer, haha)

You were saying "ksnapshot --help", correct? if my memory serves.

---

### Post by kuja on 2006-11-02
Your memory serves you well indeed.

---

### Post by argie on 2006-11-02
> **kuja said:**
> I believe, at least in Kubuntu, that the clipboard screenshot option is set to ctrl + printscreen for the fullscreen, and left_alt + printscreen for the current window.

Thanks! :)

---

### Post by spockrock on 2006-11-02
btw if you are to lazy to do ksnapshot -current, ksnapshot -c does the same thing.

---

### Post by henriquemaia on 2006-11-02
To the OP:

I agree. One of the first things I installed on my dapper was ksnapshot (I'm on gnome). gnome-screenshot should offer the same options as they are time saving (and not difficult to understand). Not having the region selection screenshot is very annoying.

---

### Post by Ramses de Norre on 2006-11-02
Seems you're looking for a gui app, but if you don't mind cli: scrot is the best screenshot app I know, look in it's man page for all options.

---

### Post by nesimi on 2010-11-26
> **metiosarius said:**
> Alright;

_Ubuntu "Take Screenshot";_

[LIST]
[*]It ONLY takes snapshots of the ENTIRE screen.
[*]It takes snapshots ONLY when first STARTING the application.
[/LIST]
_KSnapshot;_
[LIST]
[*]Can take snapshots of just a window. (with or without decorations)
[*]Can take snapshots of only a particular region (which saves time because you can avoid cropping snapshots)
[*]Has a time delay feature (which is useful for getting snapshots of menus)
[*]Can take multiple shots instead of only on startup.
[/LIST]

As you can see, KSnapshot is a far more advanced application.

You can do with gsnapshot (written with gtk) what you can do with ksnapshot. If you change print key command in "gnome-keybindings-settings" you can also run the program by pressing the print key. I have been using KDE for 2 years. But I decided to use GNOME at home.

---

### Post by cariboo on 2010-11-26
This is a four year old thread, gnome-snapshot has changed quite a bit since this thread was started. Closed.

---

