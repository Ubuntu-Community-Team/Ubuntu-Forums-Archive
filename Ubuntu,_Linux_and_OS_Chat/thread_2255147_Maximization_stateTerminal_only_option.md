---
title: "Maximization state/Terminal only option"
date: 2014-12-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Gustaf_Alhll on 2014-12-02
So I checked around on Linux to see what it's really capable of and see if I can learn something new about Linux. Then I confronted this:
[ATTACH=CONFIG]258336[/ATTACH]
Notice the marked option that says "Toggle Mazimization State"? You can find it in System Options > Keyboard > Shortcuts > Windows.
Upon activating, the screen goes black for a second and then a prompt pops up on the screen that looks like MS-DOS (Not completely, but the same basic elements (Black and white text, text only, etc.)).
I've not been digging too deep in that option, since I don't know how to get back other than restarting the computer. If you are curious, however, feel free to try it. I know it isn't dangerous since it's technically just the terminal and nothing else.
I also came to the thought that maybe it allows only one task at a time? Never tried to run a program through it, so it would be interesting to see what happens.

Right now, my curiosity is a bit towards the option above, "Toggle Fullscreen Mode". I might be checking that out later, and I can inform you about what it is when I have checked it out.

---

### Post by deadflowr on 2014-12-02
Toggle maximize should still let you revert back.
(By pressing the same keyboard command)

You can also look to see if the min,max,close buttons are hiding on the screen's top left corner.
Use your mouse and drag it up to that corner.

And also
> Upon activating, the screen goes black for a second and then a prompt  pops up on the screen that looks like MS-DOS (Not completely, but the  same basic elements (Black and white text, text only, etc.)).

That sounds like you're pressing F5, instead of 5.
If so, press F7.

I note this isn't really a support thread since your not asking for help, but my original intention was to state that this is not what happens to me on multiple installs. I figured though, that stating what I see happens, or should happen, might help you regardless...

Edit:Oh, to add most windows will go full screen with F11. Toggle back again with same.

---

### Post by Gustaf_Alhll on 2014-12-03
> **deadflowr said:**
> [COLOR=#000000]Toggle maximize should still let you revert back.[/COLOR]
[COLOR=#000000](By pressing the same keyboard command)[/COLOR]

[COLOR=#000000]You can also look to see if the min,max,close buttons are hiding on the screen's top left corner.[/COLOR]
[COLOR=#000000]Use your mouse and drag it up to that corner.[/COLOR]

[COLOR=#000000]And also
[/COLOR][COLOR=#000000]That sounds like you're pressing F5, instead of 5.[/COLOR]
[COLOR=#000000]If so, press F7.[/COLOR]

[COLOR=#000000]I note this isn't really a support thread since your not asking for help, but my original intention was to state that this is not what happens to me on multiple installs. I figured though, that stating what I see happens, or should happen, might help you regardless...[/COLOR]

[COLOR=#000000]Edit:Oh, to add most windows will go full screen with F11. Toggle back again with same.[/COLOR]
Thanks for the information. I'm sure I will find it helpful.
Why I posted this was just to inform people about discoveries on the system people may or may not know. It's always nice to learn something new.
Still, I already know what F11 does. I use it on the terminal pretty frequently (And on most programs in general). But thanks anyway.

---

### Post by mastablasta on 2014-12-03
crtl+alt+F1 to F6 are virtual consoles, Crtl+Alt+F7 brings you back from those to desktop.

when in virtual console you can login to it and then issue linux commands. 

i doubt you really pressed F5 as the virtual console should have a short message about the OS. not just blank screen with terminal input cursor.

---

### Post by mc4man on 2014-12-03
> **mastablasta said:**
> crtl+alt+F1 to F6 are virtual consoles, Crtl+Alt+F7 brings you back from those to desktop.

when in virtual console you can login to it and then issue linux commands. 

i doubt you really pressed F5 as the virtual console should have a short message about the OS. not just blank screen with terminal input cursor.
He definitely did hit F5, don't see any reference to blank screen with just cursor

---

### Post by Gustaf_Alhll on 2014-12-12
I've found something useful with the Ctrl + Alt + F5 combination.
If Unity (If the graphical part is called that) ever freezes or something happens to it, the Linux kernel is still going. Using this combination will allow you to access the prompt and restart the system even though Unity has frozen/malfunctioned.
Just wanted to update with this information.

---

### Post by grahammechanical on 2014-12-12
Since we are passing on information ...

I have Ubuntu Desktop Next installed. Linux loads in tty1 (Ctrl+Alt+F1). The Lightdm login screen runs on tty7 but the phone OS running on Mir is on tty8. At the moment the only way to update is to switch to a tty (I use tty2), run apt-get update/upgrade and then switch back to tty8 to try the Phone OS again. Can only shut down from a tty as well.

Regards

---

