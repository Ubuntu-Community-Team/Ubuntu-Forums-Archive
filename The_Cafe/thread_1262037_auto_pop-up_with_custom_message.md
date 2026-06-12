---
title: "auto pop-up with custom message"
date: 2009-09-09
forum: The Cafe
---

### Post by Dragonbite on 2009-09-09
Ok, can anybody help me.

I am trying to set up a pop-up, similar to what pops up when you start an application, which comes up with a message from a list of messages when the user logs in.  The message can be randomly selected, or go through in order but only one each time.

It also has to be easy to remove if it annoys them too much.

What is the easiest method?  IT doesn't have to be fancy, just a basic alert box would suffice.

---

### Post by Bodsda on 2009-09-09
> **Dragonbite said:**
> Ok, can anybody help me.

I am trying to set up a pop-up, similar to what pops up when you start an application, which comes up with a message from a list of messages when the user logs in.  The message can be randomly selected, or go through in order but only one each time.

It also has to be easy to remove if it annoys them too much.

What is the easiest method?  IT doesn't have to be fancy, just a basic alert box would suffice.

I would suggest using a combination of zenity and python. Hack up a small script that contains a list of messages saved in a text file. It should then randomly select one message and run zenity with this message, it should then write the list of messages back to the file excluding the used message. Add the script to the sessions dialog in the menu's (The ones that run when you log in)

If you need a hand with the script just send me a pm.

Hope this helps,
Bodsda

---

### Post by mcduck on 2009-09-09
I agree about Zenity.

But here's an idea: why not create a fortune file from the messages you want, and then use fortune with Zenity to display them. That would save you from the trouble of creating a program to display random messages.. ;)

---

### Post by Bodsda on 2009-09-09
> **mcduck said:**
> I agree about Zenity.

But here's an idea: why not create a fortune file from the messages you want, and then use fortune with Zenity to display them. That would save you from the trouble of creating a program to display random messages.. ;)

Is fortune installed by default? I am running #! at the moment so cant tell.. it is not installed on #! at least anyway. If it is not installed then people would have to install another piece of software to run this.

---

### Post by mcduck on 2009-09-09
> **Bodsda said:**
> Is fortune installed by default? I am running #! at the moment so cant tell.. it is not installed on #! at least anyway. If it is not installed then people would have to install another piece of software to run this.

No, I don't think it's installed by default. But Dragonbite didn't really tell much details where the messages would be used, so using fortune might still be a viable choice.

But I agree that if this intended for something that would be distributed to many people fortune would be unnecessary, although very small, dependency. In that case using something that's included by default would be better option to avoid the extra dependency. But if the purpose is more for personal use I don't see having to install fortune as a big drawback. Why code a program to display messages when somebody else has already done that.. ;)

edit: Anyway, to do this with Zenity & fortune you'd create a fortune file in /usr/share/games/fortune, and then simply run something like the following command to display random messages in a window:

```
fortune messages | zenity --text-info --width=520 --height=320 --title='message'
```
(replace the "message" with the actual name of your fortune file. And of course you can use whatever title you want..)

---

### Post by Dragonbite on 2009-09-09
Thanks for the quick returns. I'll tell you my plan, if you promise not to laugh.

I am going to take a list or "Romantic sayings" and secretly set it up so when my wife logs in a message box with one of these messages pops up. She clicks "OK" (or whatever) and it goes away until the next time she logs in.

I'm unfamiliar with zenity or fortune and haven't done much with Python so additional (specific) details would help.  After getting a working system, then  I can go through and "tweak" a copy to learn the technology better.

---

### Post by Bodsda on 2009-09-09
> **mcduck said:**
> No, I don't think it's installed by default. But Dragonbite didn't really tell much details where the messages would be used, so using fortune might still be a viable choice.

But I agree that if this intended for something that would be distributed to many people fortune would be unnecessary, although very small, dependency. In that case using something that's included by default would be better option to avoid the extra dependency. But if the purpose is more for personal use I don't see having to install fortune as a big drawback. Why code a program to display messages when somebody else has already done that.. ;)

edit: Anyway, to do this with Zenity & fortune you'd create a fortune file in /usr/share/games/fortune, and then simply run something like the following command to display random messages in a window:

```
fortune messages | zenity --text-info --width=520 --height=320 --title='message'
```
(replace the "message" with the actual name of your fortune file. And of course you can use whatever title you want..)
What is a fortune file supposed to look like?

```

bod@bod-usb:~/examples$ cat /usr/share/games/fortune
Message 1
Message 2
Message 3

bod@bod-usb:~/examples$ fortune /usr/share/games/fortune | zenity --text-info --width=520 height=320 --title="I am a title"
fortune:/usr/share/games/fortune not a fortune file or directory
fortune:/usr/share/games/fortune not a fortune file or directory
No fortunes found
bod@bod-usb:~/examples$

```

---

### Post by Bodsda on 2009-09-09
> **Dragonbite said:**
> Thanks for the quick returns. I'll tell you my plan, if you promise not to laugh.

I am going to take a list or "Romantic sayings" and secretly set it up so when my wife logs in a message box with one of these messages pops up. She clicks "OK" (or whatever) and it goes away until the next time she logs in.

I'm unfamiliar with zenity or fortune and haven't done much with Python so additional (specific) details would help.  After getting a working system, then  I can go through and "tweak" a copy to learn the technology better.

Sweet, I did exactly the same thing. I'll work on a script, gimme a bit o time

---

### Post by mcduck on 2009-09-09
> **Bodsda said:**
> What is a fortune file supposed to look like?

```

bod@bod-usb:~/examples$ cat /usr/share/games/fortune
Message 1
Message 2
Message 3

bod@bod-usb:~/examples$ fortune /usr/share/games/fortune | zenity --text-info --width=520 height=320 --title="I am a title"
fortune:/usr/share/games/fortune not a fortune file or directory
fortune:/usr/share/games/fortune not a fortune file or directory
No fortunes found
bod@bod-usb:~/examples$

```
Here's a guide to making fortune files: [http://www.jason.mock.ws/wordpress/2007/07/10/creating-fortune-files]("http://www.jason.mock.ws/wordpress/2007/07/10/creating-fortune-files")
(The short version is that you need to create a text file with the messages, using a line with "%" to separate the messages from each other. Then run "strfile messages messages.dat" to create a .dat file that fortune uses for selecting random messages)


Also, you are not supposed to add the actual file path to the command, just the name of the file. Fortune will automatically look for fortune files in /usr/share/games/fortunes. Spo if you put your messages in a file /usr/share/games/fortunes/mymessages, the fortune command do display messages from that file would be "fortune mymessages".

---

### Post by mcduck on 2009-09-09
Just to sum the process up:

1. Install fortune if you haven't got it already.

2. Create the fortune file:

```
gksudo gedit /usr/share/games/fortunes/mymessages
```

3. Add your messages, like this:
```

Message 1
%
Message 2

This message has many lines..
%
Message 3
```

4. Create the .dat file:
```
sudo strfile /usr/share/games/fortunes/mymessages /usr/share/games/fortunes/mymessages.dat
```

5. Add the following command to your desktop startup, make a script out of it or whatever you want:
```
fortune mymessages | zenity --text-info --width=520 --height=320 --title='message'
```

---

### Post by Dragonbite on 2009-09-09
Awesome! I'll have to see about setting it up tonight while she's out! *mischevious grin*

Thank you so much.. now I need to work on getting as many "sayings" as I can!

---

### Post by Bodsda on 2009-09-09
Ok, here we go. Python version

[B]_Prerequisites_
[/B]
You need the packages python and zenity, but they are installed by default so I think we are ok there. Next you need a file called .romance in the home dir, so ~/.romance  fill this file with one message per line

Save the code at the end to a file called romance and place it in /usr/bin then run 
```
sudo chmod a+x /usr/bin/romance
```
Add the command ```
romance
``` to the sessions dialog. Log out and in and voila. It will remove the messages as and when they are used, when they are all gone it will print File empty to the terminal, which she wont have open due to it running at login so no issue there.

```

#! /usr/bin/env python
import os
import random

if os.path.isfile(os.path.expanduser("~/.romance")):
        file = open(os.path.expanduser("~/.romance"), 'r')
        messages = file.readlines()
        file.close()
        file = open(os.path.expanduser("~/.romance"), 'w')
        if len(messages) == 0:
            print "File empty"
            exit()
else:
    print "File does not exist"

os.system(["zenity", "--info", "--text=%s" % messages.pop(random.choice((range(len(messages)))))])

for i in messages:
    file.write(i)

```

If you get any problems or errors please let me know.

Hope this helps,
Bodsda

EDIT: Gotta love that line! return statements are amazingly useful

---

### Post by Dragonbite on 2009-10-16
Alright, I finally got fortune installed and put together a romantic.dat file and all (takes a while to get on the computer without my wife being able to detect what I'm doing ;) )

I've gotten the line of code that runs it alright```
fortune romantic | zenity --text-info --width=260 --height=160 --title='message'
```

I added an entry to Startup applications with the above line in the command executed but it doesn't work.  If I take that line and manually run it in a terminal then it pops right up.

Do I have to make it into an executable shell script?  

If I do so, I know I have to put something in the top to tell it to run it as a shell script, but I don't know what it is (**#! /bin/bash** ?).

I think I have to then make it executable with 
```
chmod +x ~/.RunRomantic
```

And then have the startup application run that shell script.  Does the shell script have to have an extension (like **.sh**?)

Or do I have to look at adding it to her profile init file?

There are 5 users on this computer, so I want to make sure she is the only one that gets it (I'm sure the kids won't fully appreciate it :) ).

Thanks for all your help so far.  And Thanks for the Python script, I'm keeping that one for reference!

---

### Post by Dragonbite on 2009-10-18
Update: It works like a charm.  We'll see how long until it begins to annoy her, but she's got about 48 entries to go. :)

Thanks guys!

---

