---
title: "HOWTO : copy commonly pasted text with keyboard shortcuts"
date: 2013-06-02
forum: Tutorials
---

### Post by playful_geometer on 2013-06-02
Do you ever get tired of typing out the same old text over and over again ?  There's a relatively easy way to assign keyboard shortcuts which will copy your commonly used text to the clipboard for pasting. 
First, make sure xclip is installed:
> sudo apt-get install xclip

Then create a script with the following: 
> #!/bin/bash
echo $1 | xclip -selection "clipboard" 

and save as "copytoclipboard" in your home directory.  Then ensure file is executable by right-clicking file in your file explorer -> Properties -> Permissions 

Then, in CompizConfig -> Commands you should be able to assign a command such as: "./copytoclipboard iwannapastethis" and assign it to a keyboard shortcut if you are using Unity, then when you paste anywhere the text should show up.  (This worked for me versions back, but it needs testing).

If you, like me, are using Gnome3 based systems, then instead of using Compiz you will need to use the System Settings->Keyboard->Shortcuts to assign the command.  I found creating multiple entries and using Ctrl+Alt+Shift+F1,  Ctrl+Alt+Shift+F2, etc. to be useful, then I wrote which text is which onto my keyboard. 




Hope you find this useful :)

---

### Post by ohnonot on 2013-06-02
Ctrl+C, Ctrl+V ???
):P

---

### Post by ajgreeny on 2013-06-02
Or what about aliases?  Only work in terminal, I agree, but your examples were both for terminal.

---

### Post by ohnonot on 2013-06-04
is OP talking about something like parcellite or glipper?

---

