---
title: "Graphical front-end to verify a GPG signature?"
date: 2008-10-25
forum: Security
---

### Post by Calimo on 2008-10-25
Hello !

Let's say I've downloaded a file named SHA1SUM.txt together with its signature SHA1SUM.asc. Now I want to verify that the signature is valid.

**Solution 1** : ```
gpg --verify SHA1SUMS.asc SHA1SUMS.txt
```
The signature *is* valid. But it is painful to always open a terminal, cd to the directory and then man gpg because I never remember the bloody syntax. Therefore, I'm looking for a front-end allowing me to do it in a few clicks!

**Solution 2** : Seahorse. If I right-click on a file (nautilus), there is a "decrypt file" option, but as it is a signature, it's worthless here. If I launch seahorse with file name in argument ("seahorse SHA1SUM.txt" or "seahorse SHA1SUM.asc" in a command-line), it opens "normally" and I couldn't find any option to verify the signature.

**Solution 3** : GPA (GNU Privacy Assistant). I can click on the "Files" button to open the file (txt or asc) (or just launch gpa with the file as argument), and I have a "Verify" button. But it doesn't ask which file to verify and tells me the signature is BAD (of course, SHA1SUM.asc isn't its own signature) or that no signature was found (of course SHA1SUM.txt doesn't contain any signature information).

**Solution 4** : I tried playing with nautilus actions, but I failed miserably in: (1) getting it work correctly with 2 files in a specific order and (2) displaying the console.

I think I'm not far from the solution, but I'm definitely missing something here...


So my question is (are): how can I do to verify signatures "easily" (best with Seahorse)? How do you usually do yourself? Do you use command line? Is there another frontend I missed that perform all I need seamlessly?

Thanks in advance,
Xavier

---

### Post by Dr Small on 2008-10-25
Most of the signatures are included with the text, but I always verify them via the command line. It makes life much simpler.

---

### Post by Gamma746 on 2008-10-25
KGPG can do that, but I'm not sure if you'd want to install all the needed KDE libraries.

---

### Post by Calimo on 2008-10-26
Thanks for your answers. KGPG isn't really a problem as I've most KDE libraries already installed.

So concerning KGPG, if I open the SHA1SUM.txt or asc file with it, I get a message saying that decryption failed.
I found I need to use the -V argument, but there again I get a message saying "No signature found" and when I open the details I see basically the same GPG output that I got with the command-line when only one file was give... KGPG doesn't give me the opportunity to give information about the other file :(

I searched the web for a good tutorial, but I found nothing... I'm sure it must exist somewhere :)

---

### Post by Calimo on 2008-11-02
Finally this seems to work with nautilus-actions:```
#!/bin/bash
cd $2
FILE=`zenity --file-selection --title="Chooose a file to verify with signature $1" --window-icon=/usr/share/icons/Human/16x16/status/stock_open.png`
case $? in
  0)
    gpg --verify $1 $FILE 2> /tmp/gpg.output
    zenity --text-info --title=$FILE --filename=/tmp/gpg.output --window-icon=/usr/share/pixmaps/seahorse.png --width=600 --height=170;;
  ?)
    zenity --error --text="No file selected.";;
esac
```Quite ugly to use a temporary file, but I couldn't do better.
Then I created a new nautilus action "Verify signature" for *.asc files as condition and "%f %d" (without quotes) in the "Parameters" field (under executable path).

I think it will fail if it needs to import a new signature, though, but we will see.

PS : thanks to [geckozone]("http://www.geckozone.org/forum/viewtopic.php?t=70416")

---

