---
title: "Worried about Libre Office and extensions"
date: 2012-05-22
forum: The Cafe
---

### Post by Paddy Landau on 2012-05-22
Being an Ubuntu user, of course I am using Libre Office.

However, I depend greatly on a few extensions, especially [Alternative searching]("http://extensions.services.openoffice.org/project/AltSearch") and [Compose Special Characters]("http://extensions.services.openoffice.org/project/ComposeSpecialCharacters"), both of which I use daily.

But those extensions, naturally, are written for Open Office and not for Libre Office.

As LO has forked from OO, what happens if the two should split significantly and the OO extensions no longer work on LO?

Or what if OO closes down completely as [suggested in Linux Insider]("http://www.linuxinsider.com/story/75138.html")?

I am concerned about this possible lack of future compatibility.

---

### Post by forrestcupp on 2012-05-22
Most extensions are written by the community, and the community seems to be migrating from OOo to LO. I don't think there's anything to worry about, there.

I'd be more concerned that they are written in Java, and Oracle seems to be going after people who use Java without a license. I don't think there's anything to worry about there, either. I think the only reason they went after Google for that is because Google has tons of money they could sue them for.

---

### Post by Paddy Landau on 2012-05-22
Thanks for the reassurance.

> **forrestcupp said:**
> I think the only reason they went after Google for that is because Google has tons of money they could sue them for.
I am sick to death of this nonsense of patenting software. It's nonsense.

For example, Apple has patented its "slide switch" for on-and-off. Excuse me? Was Apple the company to invent a slide switch? It existed even before computers did! The infamous one, of course, was the idiotic "one-click" button with Amazon.

I would like a movement to develop that would boycott companies patenting software. Copyright is one thing, but patenting software is just ridiculous.

---

### Post by vasa1 on 2012-05-22
> **Paddy Landau said:**
> ...
But those extensions, **naturally**, are written for Open Office and not for Libre Office.
...
[http://extensions.libreoffice.org/extension-center](http://extensions.libreoffice.org/extension-center)

---

### Post by Paddy Landau on 2012-05-22
> **vasa1 said:**
> [http://extensions.libreoffice.org/extension-center](http://extensions.libreoffice.org/extension-center)
Thanks for pointing that out. Now to persuade the authors of my favourite extensions to port theirs to there...

---

### Post by vasa1 on 2012-05-22
I'm not sure about what I'm saying but is it really necessary to have the Compose Special Characters extension? Can't you set up something at the keyboard level that isn't limited to LibreOffice? I did it just the other day but then undid it because I rarely use special characters.

In case you're interested, this thread deals with setting things up:
[http://forum.xfce.org/viewtopic.php?pid=23726#p23726](http://forum.xfce.org/viewtopic.php?pid=23726#p23726)
This
```
setxkbmap -option compose:lwin
```
will make the super (Windows) key, to the left of the spacebar the trigger and just follow the instructions in post #12 (by a mod) in that thread. If you've assigned lwin already, you'll have to find an alternative. This procedure worked for me in gedit and in the terminal. I didn't think of trying it in LibreOffice Writer or Calc :(

Edit: I set it up again, logged out, logged in and it does work in LibO Writer.

---

### Post by Paddy Landau on 2012-05-22
> **vasa1 said:**
> I'm not sure about what I'm saying...
Actually, there is already a built-in method that Linux uses -- the compose keys. There are three types: dead keys, compose keys and Unicode keys.


[LIST]
[*]General overview
[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)
[/LIST]

[LIST]
[*]Dead keys
[https://help.ubuntu.com/community/GtkDeadKeyTable](https://help.ubuntu.com/community/GtkDeadKeyTable)
[/LIST]

[LIST]
[*]Compose keys
[https://help.ubuntu.com/community/GtkComposeTable](https://help.ubuntu.com/community/GtkComposeTable)
[http://hermit.org/Linux/ComposeKeys.html](http://hermit.org/Linux/ComposeKeys.html)
[/LIST]

[LIST]
[*]Unicode keys
[http://www.unicode.org/charts/charindex.html](http://www.unicode.org/charts/charindex.html)
[/LIST]

However, remembering the combinations is not always easy, which is why I use the Libre Office extension. Look at the examples below to get an idea of the difficulty in remembering sequences.

[LIST]
[*]Dead key example (varies by keyboard): €
AltGr-4
[/LIST]

[LIST]
[*]Another dead key example: ¼
AltGr-Shift-4
[/LIST]

[LIST]
[*]Compose key: ê
Shift-AltGr; e; ^ (release the keys at each semi-colon)
[/LIST]

[LIST]
[*]Unicode: &#8470;
Shift-Ctrl-U; 2; 1; 1; 6; space (release the keys at each semi-colon)
[/LIST]
Note that order is important. AltGr-Shift begins the dead-key sequence, whereas Shift-AltGr is the Compose key.

---

### Post by vasa1 on 2012-05-22
> **Paddy Landau said:**
> Actually, there is already a built-in method that Linux uses -- the compose keys. There are three types: dead keys, compose keys and Unicode keys.
...

Thanks for that. But then why are people trying to do it the way that the Xfce link described?

I'll read your links now and post back if I don't get anything.

---

### Post by Paddy Landau on 2012-05-22
> **vasa1 said:**
> ... why are people trying to do it the way that the Xfce link described?
I don't know, but on reading the thread it seems to me that the OP wanted to change the Compose key. Changing it to the Super key (the Windows key) is not a good idea with Unity, as it is used for the dash and other combinations, but I'm sure it's OK for XFCE.

---

