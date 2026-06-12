---
title: "Little big annoyances"
date: 2006-12-07
forum: The Cafe
---

### Post by Peturrr on 2006-12-07
Hi everybody,

I just found out that my biggest annoyance when using Ubuntu is easily solved. I was wondering about it. Am I the only one that gets irritated about it?

My frustration was about the firefox URL bar behaviour. Sometimes you need to edit a URL and I am used to do this by clicking on the url and using the CTRL key and the arrowkeys or the backspace key to navigate through the URL. 
On Ubuntu however when using CTRL + Left-key this results in jumping from the end to the beginning of the URL or deleting it completely when using backspace.

How many times didn't I got so frustrated with this usability thing...
Turns out the solution was easy. change layout.word_select.stop_at_punctuation in about:config from false to true.

So, please tell me: Was I alone in this frustration?
Would also love to know what little stupid things frustrates **you **in Ubuntu? 

It's not about whining about Ubuntu, I love it ! Just share your pain, sort a group therapy. ;)

---

### Post by rfruth on 2006-12-07
Web sites that 'require' IE get my goat [https://www.oprah.com/membership/member_faq.jhtml#6](https://www.oprah.com/membership/member_faq.jhtml#6) :confused:

---

### Post by drphilngood on 2006-12-07
> **rfruth said:**
> Web sites that 'require' IE get my goat [https://www.oprah.com/membership/member_faq.jhtml#6](https://www.oprah.com/membership/member_faq.jhtml#6) :confused:

Shockwave gets mine.

---

### Post by Frak on 2006-12-07
> **drphilngood said:**
> Shockwave gets mine.
Same, but I just gave up and bought Crossover to use flash and shockwave, sorry.

---

### Post by maniacmusician on 2006-12-07
> **Frak said:**
> Same, but I just gave up and bought Crossover to use flash and shockwave, sorry.
how does that work? aren't they plugins? so wouldn't you have to "crossover" a whole browser to get that to work?

---

### Post by wieman01 on 2006-12-08
It's funny, but when I think about it... Nothing really. Windows freak me out every time I have to use it. But Ubuntu with the KDE environment is customizable to such a degree that I don't miss anything at all. I am surprised myself that I would ever say something like that.

---

### Post by Frak on 2006-12-08
> **maniacmusician said:**
> how does that work? aren't they plugins? so wouldn't you have to "crossover" a whole browser to get that to work?
No you don't, it emulates to the program that Firefox, Konqueror, and Opera are Netscape 6.0 browsers and installs a special registry, in firefox it comes up in the extension menu as "Crossover Media" and has the description "Don't miss out on what Windows can do", and enables Window's plugins within native Linux browsers, and whatever else uses shockwave and flash.

EDIT
By flash I mean the more stable Windows version. Wine is nothing compared to this, exept for the $40.00 price tag.
You can get the beta [here]("http://www.codeweavers.com/beta/cxlinux/download/") for 60days of "testing" for free. I think everybody should at least try this, you don't have to compile from source (+ for me), just enter the code below.

```
sh install-crossover-standard-prerelease-6.0.0beta3a.sh
```

And thats it, it's packed with all its dependencies.

---

### Post by commonplace on 2007-01-30
> **Peturrr said:**
> Hi everybody,

I just found out that my biggest annoyance when using Ubuntu is easily solved. I was wondering about it. Am I the only one that gets irritated about it?

My frustration was about the firefox URL bar behaviour. Sometimes you need to edit a URL and I am used to do this by clicking on the url and using the CTRL key and the arrowkeys or the backspace key to navigate through the URL. 
On Ubuntu however when using CTRL + Left-key this results in jumping from the end to the beginning of the URL or deleting it completely when using backspace.

How many times didn't I got so frustrated with this usability thing...
Turns out the solution was easy. change layout.word_select.stop_at_punctuation in about:config from false to true.

So, please tell me: Was I alone in this frustration?



Oh. My. Gosh. I've been trying to fix that FOREVER. I can't believe it was so simple! Thank you thank you thank you! I always hit Ctrl+Backspace to delete one word at a time in the URL, and for whatever reason, the Linux version of Firefox deletes the whole URL by default. Always hated that and now it's fixed!!!

/Kevin

---

### Post by Brunellus on 2007-01-30
funny, I get annoyed in the opposite direction.  I'm constantly trying to middle-click-paste in Windows, and wondering why it won't work.

---

### Post by commonplace on 2007-01-30
> **Brunellus said:**
> funny, I get annoyed in the opposite direction.  I'm constantly trying to middle-click-paste in Windows, and wondering why it won't work.

Heh, I haven't gotten used to middle-click pasting with scroll wheel mice, so I rarely do it. (I have a hard time clicking the wheel rather than scrolling it.)

/Kevin

---

### Post by chickengirl on 2007-01-30
> **rfruth said:**
> Web sites that 'require' IE get my goat [https://www.oprah.com/membership/member_faq.jhtml#6](https://www.oprah.com/membership/member_faq.jhtml#6) :confused:

I hate that too. Webmasters who do that are completely, utterly clueless.

---

### Post by xmastree on 2007-01-30
> **commonplace said:**
> Oh. My. Gosh. I've been trying to fix that FOREVER. 
Fix what? :confused: 

Selecting part of a url (or even text in this window I'm typing), click one end of the selection, then use shift (not control) and the arrows to select text between where you first clicked and where the cursor is now. Or shift-click the other end if you prefer.

Ctrl-Shift selects text word by word, Shift on its own selects one character at a time.

Or did I miss the point somewhere?

---

### Post by commonplace on 2007-01-30
> **xmastree said:**
> Fix what? :confused: 

Selecting part of a url (or even text in this window I'm typing), click one end of the selection, then use shift (not control) and the arrows to select text between where you first clicked and where the cursor is now. Or shift-click the other end if you prefer.

Ctrl-Shift selects text word by word, Shift on its own selects one character at a time.

Or did I miss the point somewhere?

I know how to shift+click, etc. The point is that I type 100+ wpm and I don't like taking my hands off the keyboard to use my mouse for anything. I use Alt+D to jump to the URL bar, press End to jump to the end of the line, then Ctrl+Backspace to delete backwards one 'word' (section, really) at a time. It's what I'm used to and it sucked without it. :)  Obviously, it's not important to everyone, or even most people, but to me (and the person who found this fix), it's critical!

/Kevin

---

### Post by Brunellus on 2007-01-30
> **commonplace said:**
> I know how to shift+click, etc. The point is that I type 100+ wpm and I don't like taking my hands off the keyboard to use my mouse for anything. I use Alt+D to jump to the URL bar, press End to jump to the end of the line, then Ctrl+Backspace to delete backwards one 'word' (section, really) at a time. It's what I'm used to and it sucked without it. :)  Obviously, it's not important to everyone, or even most people, but to me (and the person who found this fix), it's critical!

/Kevin
One word:

[Ratpoison](http://www.nongnu.org/ratpoison/)

---

### Post by Minyaliel on 2007-01-30
After changing back from Elive, I find myself trying to right- click my desktop to make the programs menu appear, or loosing the mouse pointer in the screen edges because I'm used to that doing such a thing in Elive would get you onto a new virtual desktop. Arrgh, annoying...

> **Brunellus said:**
> One word:

[Ratpoison]("http://www.nongnu.org/ratpoison/")

Or Conkeror... 

(sorry bout the double post)

---

### Post by prizrak on 2007-01-30
Alt+S opening history instead of submitting posts in Firefox 2.0. Really damn annoying. Even more so since someone posted how to fix this somewhere on the forum a while ago but I've been unable to find it :(

---

### Post by Minyaliel on 2007-01-30
If you do find it, link please... it drives me insane...

---

### Post by niko7865 on 2007-01-30
Sweet, I've been looking for a solution to this too.

You can use middle click to paste?

---

### Post by Brunellus on 2007-01-30
> **niko7865 said:**
> Sweet, I've been looking for a solution to this too.

You can use middle click to paste?
best thing about xwindows.

click & highlight text.

point to where you want to paste highlighted text.

middleclick.

Windows can't do this, and is thus obviously not ready for the desktop.

---

### Post by shining on 2007-01-30
> **Brunellus said:**
> funny, I get annoyed in the opposite direction.  I'm constantly trying to middle-click-paste in Windows, and wondering why it won't work.

Same here

---

### Post by Frak on 2007-01-30
> **Brunellus said:**
> funny, I get annoyed in the opposite direction.  I'm constantly trying to middle-click-paste in Windows, and wondering why it won't work.
Yep, Same here, still figuring out why some things don't work in Windows. :P

---

### Post by prizrak on 2007-02-02
Found the solution for that Alt + S issue. Go to about:config and change ui.key.contentAccess to 4

---

### Post by newtonfn on 2007-12-01
Peturrr, with your solution for ctrl+backspace you are a lifesaver for me. I was so frustated with that.. and now a saw the light.

Thanks

---

