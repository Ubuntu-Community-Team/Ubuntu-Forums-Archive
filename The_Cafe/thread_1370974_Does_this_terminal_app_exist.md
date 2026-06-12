---
title: "Does this terminal app exist?"
date: 2010-01-02
forum: The Cafe
---

### Post by HyperHacker on 2010-01-02
I had an idea for a terminal app, but this being Linux, I figured someone has probably already made it, and I should ask before making an attempt at doing it.

The idea is a terminal with a separate, dedicated input area. Some mainframes had this, but for some reason Linux does not. So if your terminal is being flooded with messages (just try to access a faulty flash memory card), you can't see what you're typing. With a dedicated input area you can still enter a command to try to stop the madness.

Of course, a graphical frontend can't exactly change how the terminal works, but it can have a textbox, where every keystroke you type, including backspace and enter, is sent to the terminal, and enter also clears the box. That would be about the same effect.

Additionally, if it's possible, the app could detect if the command has finished executing yet, and if not, any additional commands you enter would execute as soon as the current one is finished. You can already do that with Ctrl+Z, but this would be a more convenient method that doesn't require you to stop the current process.

---

### Post by Warpnow on 2010-01-03
Most Mud clients work like this, and I used to use them to telnet into servers. Nowadays, though, everything is SSH.

---

### Post by toupeiro on 2010-01-03
If I'm understanding you right, you can use the screen utility to accomplish something similar to this.  The effect is ultimately the same, you can manage your content at a local terminal.

---

### Post by RiceMonster on 2010-01-03
You mean you want something like ISPF on Z/OS for Linux? It would be possible to do it, with curses.

I spent a lot of time working with Z/OS, so I got really used to ISPF and wanted to see if there was anything similar for Linux, just for the heck of it. I ran into a clone of the editor, but that's about it. I didn't bother to try the editor, because the actually thing is not all that great.

---

### Post by Warpnow on 2010-01-03
It seems people think he wants to build a CLI app when he's talking about a terminal emulator. One with a separate input box that separates sent from recieved. This would be very useful. For instance, lets set you want to do a very complex apt-get install after an apt-get update...as is you wouldn't really be able to type it in until the end, because the update would flood you making it hard to see what you've typed. If you had a separate input box you could type it, and then send it when the update was complete.

I like the idea. But I wouldn't advise making your own emulator, I'd just fork an existing one. XFCE4-terminal is my favorite terminal emulator, so I'd use it. ;)

---

### Post by Warpnow on 2010-01-22
Any news on this? I'd like this kind of thing...

---

### Post by HyperHacker on 2010-01-22
I haven't actually worked on it. I tend to come up with a program idea, stash it in a todo list, and not actually do it for quite a while. It's in there, though.

I did mean a terminal emulator. You're probably right that it'd be easier to add to Xfce4-terminal than to make a new program. <3 open source.

---

### Post by lswb on 2010-01-22
How about simply opening another terminal?

---

### Post by HyperHacker on 2010-01-22
There are cases where that won't do. For example I want to run another command after the current one is done, but don't want to stop it using Ctrl+Z (maybe a time-sensitive program or something that shouldn't be interrupted). Or, I've had a few cases where trying to read a faulty flash memory card has spammed the terminal with error messages, making it impossible to see what I type. This idea would also make it easy to copy the command line you entered, even after the program has started.

---

### Post by schauerlich on 2010-01-22
So basically have two windows, one which has stdout and stderr, and another buffer for stdin? Seems simple enough.

---

### Post by MaxIBoy on 2010-01-22
I have rigged this kind of thing together with GNU screen and the exec command. You could probably rig up a script to set this up for you all at once.

See screenshot for instructions.

If they don't need to be splitscreen in the same window, you can do this with two terminal windows as well.

---

