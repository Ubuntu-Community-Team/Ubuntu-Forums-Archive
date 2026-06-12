---
title: "AutoKey Text Expander for Linux"
date: 2022-04-03
forum: Ubuntu, Linux and OS Chat
---

### Post by thedoor on 2022-04-03
Something I saw earlier today prompted me to do a search for the phrase "text expanders in Linux". **[AutoKey]("https://en.wikipedia.org/wiki/AutoKey") seems to be the most advanced and most prominent text expander in the Linux community. I'm sure glad I found it when I first began to use Linux! There are some others, but they are far less user-friendly and helpful than AutoKey.** So I decided to create this post about AutoKey, since using a text expander can be a time- and effort-reducing application that can save countless keystrokes, time, and effort when it's set up for words and phrases which you frequently use but wouldn't have to completely type every time you use them, if you were using a text expander. **I suspect that people who aren't using one have no clue how much *wasted time and unnecessary frustration they would avoid *if they were using one.** My purpose in creating this post is to help show them that.

There is a similar forum topic at [https://ubuntuforums.org/showthread.php?t=2325415](https://ubuntuforums.org/showthread.php?t=2325415), but it is closed. So I decided to create this post to provide relevant information about AutoKey. **I believe that AutoKey needs to be easily found and recognized for its valuable contribution to the Linux community.** All of that post's entries date back to 2016. And I didn't readily find any other posts about using AutoKey. Two of those posts mentioned AutoKey, but both authors were discouraged by it. I've also seen elsewhere that others said it couldn't do scripts. It can, indeed, do scripts, but you have to tell AutoKey that it's a script when you create it. And then you have to run the script when you want to use it. From my experience of using AutoKey for some 5-6 years now, I suspect those authors didn't fully understand how to use AutoKey well. Creating the shortcut is *slightly tricky*, but I'll covert hat in the **Creating a Shortcut** section below. **AutoKey has been a tremendous help to me since I discovered it, after moving from Windows to Linux!** I want you to have the experience of seeing how much time and frustration you can avoid by using AutoKey, if it makes sense to you to use it.

I constantly used the **Smart Type Assistant app** in Windows and really wanted to find a good replacement for it when I came to Linux. **I'm really glad I found out about Linux, and now I can see *how far better it is than using Windows*, after many years of using Windows.** ***I found a replacement in AutoKey.*** There are two versions available: autokey-gtk and autokey-qt. I normally use autokey-gtk. It's been readily available in the many Debian/Ubuntu distros I've used or tried. I've never had a problem with it. I use it continuously through my days, for so many things.

I currently have 249 shortcuts saved, so you can see that I'm an avid user of this wonderful utility. **If I notice that I'm starting to use something frequently, I'll make a shortcut for it. I pick the first thing that pops into my mind as the shortcut, since it just makes sense to me to use that shortcut** (like using la- for Los Angeles; the hyphen prevents the expander from playing out Los Angeles in any words that us "la" within the word). **It can be words or phrases or even multiple paragraphs of text!**

I use shortcuts for my first name, last name, street address, apt. number, city, phone number, words I commonly use, other peoples' names I frequently use, phrases I often use, words I often mistype (so they are automatically corrected if I type them wrong), usernames I use, email addresses I use, various numbers I frequently use, urls, or generally any words and/or phrases I find myself typing frequently.

You can set up shortcuts that are automatically triggered as soon as you type them, or you can set up shortcuts that are only used if you type a hyphen after them. If I want to use a shortcut but not use it all of the time, I'll put a hyphen (-) behind the shortcut, so I have to enter both the shortcut and the hyphen in order for it to be triggered. Also, when the shortcut is one or more letters that are commonly used or are often part of common words, I'll add the hyphen so the shortcut isn't triggered when I'm typing those letters or words. For example, I've set ar- as my shortcut for "autoresponder". Since "ar" is a frequent part of other words, I need to type the hyphen only when I want the word "autoresponder" to play out, and ***not*** whenever "ar" is part of another word, like "part." I just type those words as I've always done.

**If you plan to use AutoKey, I suggest that you print out this post so you'll have it handy when you're setting up and using AutoKey. It's a lengthy explanation, but I wanted to provide you here with the main details about how to use AutoKey so it's easy to work with right away, without having to figure it all out on your own.**

**It's really an easy app to use, once you learn some necessary steps you must take to set up your abbreviations and how to execute them. But it does require that you take those exact steps to ensure that it works for you.** So learning about those steps ahead of time will save you frustration in having to figure it out by yourself.

There are some other options you can use with the program, but these below are the ones most people will need to know right away to begin using it effectively. Be sure to study the program as you're working in it, to see if there are other features it has which would also benefit you.

**Installing AutoKey**

**Before beginning to use AutoKey, you must first install it.** You can use your distro's software center or use the command line in a terminal to install it. To use the command line, open your terminal program and tell it whether you want the gtk or the qt version. To use the command line, enter: sudo apt install autokey-gtk (or autokey-qt) and then press the Enter key. Then type your sudo password, when prompted, to process the command. The terminal should install the application. When it's done, close the terminal.

**Setting AutoKey to Start up at Boot and Automatically save your changes**

Once installed, if you know you'll be using AutoKey frequently, you'll want to add it to your autostart programs. You can do that by opening the running AutoKey program by using it's shortcut, Super+k. If AutoKey isn't running, then start it by using your menu system. Typing "auto" in your menu system's search box is likely enough to display its name, AutoKey, so you can just press Enter or click on it to start up.

When AutoKey is open, go to its Edit menu and click on Preferences, at the bottom of the menu. Under the **General** tab, and under **Application**, click the check box beside "Automatically start AutoKey at login". You can also click the checkbox beside "Automatically save changes without confirmation" so AutoKey won't ask you to confirm that you want to save the changes, when you click "Save" at the upper left of the screen, below the menu bar, to save the new or edited shortcut, before you close AutoKey. Then click OK to save your changes and exit AutoKey, if you have nothing else to do there at that time. Of course, since it may be your first time to use AutoKey, that's a good time to look through the menus to see what all is available and begin learning how to use AutoKey.

If you didn't tell AutoKey to start itself at boot time, you can tell your distro to autostart AutoKey when you boot up. As mentioned above, you can do that by typing **start** in your distro's search field. That will likely find your session startup program and let you enter AutoKey there. That usually involves entering the application's name, AutoKey, and the location of the executable file. **It's a lot easier to do that in AutoKey, as described above, instead of having to do it manually.**

**[B]Creating a Shortcut**[/B]

Here are the basic steps for creating a shortcut.

**Use the shortcut, Super+k, to open the running AutoKey program, or use your distro's menu system to open it.**

**Type the name of the shortcut, including the hyphen, if you're planning to use one, and press the OK button.** (For example, you might use "la-" for "Los Angeles", being sure to add the hyphen, since other words can contain the letters "l" and "a" together, such as "land", and you don't want "Los Angeles" automatically typed every time you start typing the word "land" or other affected words.)

Pressing the OK button in the step above automatically opened the area (on the right of the abbreviation) where you'll enter the words you want automatically played out when you press the shortcut combination. **To enter that text, click in the text area and select the instructional phrase, "Enter phrase contents", to remove it, since it won't automatically disappear when you enter that area. To remove it, position your mouse anywhere over that phrase and simply triple-click the left mouse button, which will select the entire phrase. Then press the Delete key to remove it. ** *TIP: The triple-click technique can be used in any situation where you want to select a line of text. Triple-clicking is quicker and easier than swiping across the entire line.)[/B] [B]Then type the word or phrase that you want the shortcut to play out.*

**Then, below that area, click the "Set" button, beside "Abbreviations".** That will pop up the **Set Abbreviations** dialog box.

In the Set Abbreviations dialog box, **click the "+Add" button at the bottom**. That creates an empty text box area above, right below the word "Abbreviations". **Type the same character or phrase you used before** (la-, in our example above), and press Enter, to enter the name of the abbreviation for the new shortcut. **Then press the Tab key**, which will take you into the section on the right of that abbreviation you just entered. **If you used a hyphen, click the check box beside "Remove typed abbreviation" so the abbreviation is removed when playing out the shortcut. Also click the check box beside "Omit trigger character" so the hyphen disappears once you press the hyphen, when playing out the shortcut.** When done, click OK.

**Then be sure to click the "Save" button at the top left of AutoKey, below the menu bar, before you close the program, to save your changes.** When you're done, you can close the app. Closing it puts it back in the system tray, but leaves it running the background.

**Using a Shortcut**

To use AutoKey, ensure that you have AutoKey running. If AutoKey isn't running, you'll need to start it first. Again, simply typing "auto" in the search box of your menu system will likely find AutoKey and you can just press Enter to start it. If more than "AutoKey" shows up, select AutoKey and press Enter to start it.

**To use an abbreviation, once AutoKey is running, put your computer's *insertion point* (which usually looks like an "I", frequently called an I-beam) where you want the abbreviation to be played out, and then type the abbreviation you assigned to the abbreviation (la-, in our example above).** The text will expand exactly as you set it to do. (Hopefully you typed it all correctly. If not, this will be your opportunity to make a correction.)

If you notice a mistake, just go back into AutoKey (press Super+k to activate it, if you left it set that way), then find that shortcut, and then move your insertion into the right pane, beside that abbreviation, where the text to be expanded is located. Make any corrections and then click "Save" to save your changes. Then close AutoKey to the system tray again.

Though it takes a bit of careful attention to set up an abbreviation, it's a quick and easy task to do, once you understand each step in the process. Taking a few moments to create an abbreviation and then remembering to use it when you need it, will save you time from then on out. Type it once, and let your computer type it from then on.

**NOTE: You can use AutoKey for "boilerplate text" as well as for words and phrases. Your shortcut can include paragraphs of text, if needed, so you can simply type your shortcut and AutoKey will play out those paragraphs automatically for you, from then on. Imagine the wasted time you'll save by typing it once and then letting your pc type it from then on!**

Now you can appreciate the wasted time, effort, and needless frustration you'll have saved yourself by letting AutoKey do a lot of your typing for you!

---

### Post by coffeecat on 2022-04-03
Not a support request. *Thread moved to **Ubuntu, Linux & OS Chat**.*

---

### Post by thedoor on 2022-04-03
This article was submitted as an informative and tutorial post, **not as a request for assistance**. It was submitted because of the lack of significant information about AutoKey and because the only post I found *here* about AutoKey was one that was Closed in 2016. Being an avid and enthusiastic user of AutoKey, I wanted to shed light and assistance for people who might benefit from this great app. I thought that creating a new post on this topic was appropriate for doing that. I had no clue that it would be listed as just a chat post. I didn't enter it for just chatting. I entered it for teaching people about an awesome way to save themselves enormous time, effort, and frustration by learning about and learning how to use the AutoKey app.

Please feel free to move the post wherever it's best suited, so people are likely to find it. I don't know where that should be. And please notify me of its final resting place, if it's moved again, so I can refer others to its proper home.

---

### Post by QIII on 2022-04-03
Your thread was moved here because you are neither asking for help nor answering another's request for help.

If you would like it to be a tutorial, it can go in the [tutorials section]("https://ubuntuforums.org/forumdisplay.php?f=100"), ***provided you follow the guidelines found [here]("https://ubuntuforums.org/showthread.php?t=2143602").***  Non-conforming tutorials will be removed from public view.

For a good example of what we would like to see in tutorials, have a look at [this one]("https://ubuntuforums.org/showthread.php?t=2426633").  LHammonds composes his tutorials off line and splits them into digestible chunks before posting them in quick and immediate succession for context and continuity.  He does not start, post, compose another later, post, compose another later ...

We will not be notifying you of our actions with regard to any of your threads that may be moved.  You can find them easily by clicking "Quick Links" and then "Find all my posts".  We are far too busy with our volunteer duties here to provide notifications for every administrative action we take.

---

### Post by thedoor on 2022-04-03
This is obviously not the place for this post. I'm amazed at how little interest you have in providing detailed information to your community. AutoKey is available for Ubuntu as well as its derivatives and Debian derivatives, and likely other Linux distros as well.

This post doesn't obviously doesn't meet your forum's guidelines for tutorials, and it seems a bother to post anywhere here. So just delete the post. Sorry for the intrusion into your gated city. I'll post it elsewhere.

---

### Post by QIII on 2022-04-04
And yet ... your post is still here and still available to the community.  There is no gate keeping anyone away from your post.  It has simply been moved to the appropriate location.  If you want it to be in the Tutorials section, make sure it complies.

This is not a difficult thing.

---

### Post by coffeecat on 2022-04-04
Just to add to what QIII has stated:

> **thedoor said:**
> This article was submitted as an informative and tutorial post, **not as a request for assistance**.

And yet it was posted in the [General Help]("https://ubuntuforums.org/forumdisplay.php?f=331") sub-forum, whose tagline clearly states:

> All your general support questions for Ubuntu, Kubuntu, Edubuntu, Xubuntu, Lubuntu, Ubuntu Mate, Ubuntu Budgie, Ubuntu Studio and Ubuntu Kylin.

Which is why it was moved here to ULOS Chat, a popular sub-forum, where you are more, not less, likely to get the attention you seek, and where it might stimulate useful discussion.

---

### Post by dragonfly41 on 2022-04-04
Let me throw in some support of the idea/chat.  It may be that your contribution landed in the wrong theatre but the general idea of desktop automation is of interest to me, at least. AutoKey is just one tool that falls into that category. 

I was not aware of a Tutorials forum and I now see that it is buried away here. Perhaps more ideas should be posted there. Thanks for indirectly pointing to Tutorials subforum.

[https://ubuntuforums.org/showthread.php?t=2143602](https://ubuntuforums.org/showthread.php?t=2143602)

I agree with the rationale that there is much wasted time in writing and validating text snippets.  Just look at the volume of commands in this forum which have to be repeatedly copied and pasted. And I will not venture into the learning model where instructions are given by video fuzzy screenshots accompanied by running commentary.

I do have AutoKey running in my top bar .. but I do not use it as often as I might. I use Actiona.

250 shortcuts is too many for my old brain to remember. On top of that we have hot keys for various applications to remember.

My interest is in expanding strings to run commands in terminals.

I have studied the field for some time and I favour Actiona for UI emulation. That is, expanding variables to run in terminal or searching for content (images) in a screen. But there is also

xdotool
Python
Albert

In Actiona, using javascript notation you can create nested arrays holding all manner of content and actions.

But staying with AutoKey since you can invested much time in writing it up.

First make a directory for experiments.

cd $HOME
mkdir AUTOKEY

Also run this command in ~/AUTOKEY

man autokey > manual.txt

    autokey-gtk  AutoKey  is  a desktop automation utility for Linux and X11
    
    So note it will not work for wayland users

Enable &#8220;view hidden files&#8221; in your File Manager (I use Krusader but there is Nautilus) and go to $HOME/.config/autokey

In autokey.json

set

 "userCodeDir": "~/AUTOKEY",
 
 and
 
  "folders": [
        "~/AUTOKEY/scripts/Accounts"
    ],

Now in the launcher [A] which appears in top bar select 
&#8220;Show Main Window&#8221;

Here we can add our collections of scripts organised into different categories. We can assign hot keys to each script.

Note that the top bar [A] dropdown menu seems to refer to ~/.config/AutoKey and NOT to custom project folder ~/AUTOKEY.  I will figure that out later.
   [Added note: I figured out why the topbar menu is not fully populated. Each folder or file in the main AutoKey GUI should have ticked &#8220;Show in notification menu&#8221; for it to be displayed in topbar launcher menu. This is why the topbar menu can be shorter.] 

...

It was not made clear in your writeup that AutoKey can do much more than text expansion.  For example Python and other scripts can be run. I have created a folder

~/AUTOKEY/Sample Scripts/

and Abbreviations and Hotkeys can be configured for each script.

There are of many commands and scripts scattered throughout this forum (and in cloud cli) which can be so configured. Of course the equivalent is running bash scripts. And aliases can be attached to bash (or other) scripts.

But AutoKey allows scripts to be managed through a GUI.

I will give one example.
I use CherryTree as my main notes editor (although I use others).
I can create a codebox embedded in any CherryTree node. That is I can run commands from within my notes rather like Jupyter note books.

I created a simple test Python script thus to go into my ~/AUTOKEY/Sample Scripts/ folder:

```

#!/usr/bin/env python3

# cherrytree.py is the script in folder

# Enter script code below

import subprocess 

# three clicks on left button mouse
# to highlight command string in CodeBox
cmd = ["xdotool", "click", "--repeat", "3", "1"]
subprocess.Popen(cmd)

# copy highlighted string
cmd = ["xdotool", "key", "--clearmodifiers", "shift+ctrl+c"]
subprocess.Popen(cmd)

text = clipboard.get_selection()
# keyboard.send_key("<delete>")
keyboard.send_keys("The text %s was here previously" % text)

```

I set [F6] button as script hot key.

Now I highlight text in CherryTree codebox and it is changed when F6 is pressed.

Conclusion: AutoKey can interwork with other desktop tools such as Python, xdotool and so on in a toolchain.

In closing, I point out that there are many other tools to help in desktop automation.

Albert allows python extensions.

Also emmet

[https://emmet.io/](https://emmet.io/)


I will now browse through the Tutorials sub-forum.
It is quite an art to turn a workflow description into an elearning module with feedback from learners.

---

### Post by vanadium on 2022-04-04
For sure I also am interested in keyboard automation, and I appreciate your efforts to highlight the Autokey tool.

> **thedoor said:**
> From my experience of using AutoKey for some 5-6 years now, I suspect those authors didn't fully understand how to use AutoKey well.
Wrong suspicion. I was using Autokey in a time where development had stalled. It stopped working reliably. I moved on using a custom system based on xdotool, heavily inspired by [this post by Dmitri Popov](https://www.linux-magazine.com/index.php/layout/set/print/Issues/2014/162/Workspace-Text-Expander/(tagID)/92). It worked so well that I never tried Autokey again, even when I noticed that it started moving forward again.

Another very promising tool, and cross platform, is [Espanso](https://espanso.org/). They are doing major effort to also support Wayland despite the fact that that protocol makes creating such utilities extremely difficult.

---

