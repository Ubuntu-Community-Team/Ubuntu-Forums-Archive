---
title: "Gedit plugin: multi-edit"
date: 2009-02-19
forum: The Cafe
---

### Post by shadow_code on 2009-02-19
Hi,

I've just finished writing a new plugin for Gedit and was wondering if people would like to try it out! :D

[Multi-edit]("http://jon-walsh.com/journal/multi-edit/")

It allows you to edit multiple sections of a document simultaneously. Similar to E-TextEditor/TextMate or column editing in some text editors.

0.9 at the moment, but very stable.

Love to get some feedback, Cheers!

**Edit**: [SIZE="3"][1.1 released]("http://jon-walsh.com/journal/multi-edit/")[/SIZE]

---

### Post by binbash on 2009-02-19
Works good here

---

### Post by Merde on 2009-02-21
hello, and thank you for your plugin !

I tested it, it works fine.

I noticed that specific letters such as é à ê and so on do not work
cause the column mode to stop, but that's not an issue since I do not code in french.

A suggestion that I have for you :
For the moment, your plugin works this way : if you have a long line followed by a short one, the cursors will appear at the end of the line, so that there may be a big distance between the cursors.
The editor I use on Windows (ultra edit) behaves another way :
spaces are added at the end of the shortest line so that cursors are always on the same columns.
This is nice, because the language I use needs to have the comments ended by */, and it is nice to have them aligned.

Juste a suggestion....

Thank you again for your plugin !
Sylvain, France

---

### Post by shadow_code on 2009-02-21
> **Merde said:**
> hello, and thank you for your plugin !

I tested it, it works fine.

I noticed that specific letters such as é à ê and so on do not work
cause the column mode to stop, but that's not an issue since I do not code in french.

A suggestion that I have for you :
For the moment, your plugin works this way : if you have a long line followed by a short one, the cursors will appear at the end of the line, so that there may be a big distance between the cursors.
The editor I use on Windows (ultra edit) behaves another way :
spaces are added at the end of the shortest line so that cursors are always on the same columns.
This is nice, because the language I use needs to have the comments ended by */, and it is nice to have them aligned.

Juste a suggestion....

Thank you again for your plugin !
Sylvain, France

Hi, I'm glad you like it :)

I initially restricted the plugin to ASCII only as a precaution. But the next update will support all unicode chars hopefully. (coming in 1-2 days)

Thanks for the suggestion, that sounds like a good idea. I'll definately try to implement it as an option.

Cheers,
Jon

---

### Post by Merde on 2009-02-22
I'm happy you enjoy my suggestion !

for french characters, as I told you, it's not an issue since I do not code in french ! ;)

Anyways, I'll be happy to test you future releases.

Bye
Sylvain

---

### Post by tom66 on 2009-02-22
Thank you for this plugin, I find it very useful :D.

---

### Post by shadow_code on 2009-02-27
Hi guys,

Looks like those "1-2 days" some how managed to turn into a week! 8-[
But luckily those extra days have been well spent, fixing lots of bugs and adding some new features.

So I'm happy to present the [**1.0 release**]("http://jon-walsh.com/journal/multi-edit/")!

See [what's changed here]("http://jon-walsh.com/journal/2009/02/multi-edit-1-0/")

Hope you like it :D

Cheers,
Jon

---

### Post by Merde on 2009-03-01
great improvements !

I'm very happy you implemented my suggestion :P

Promise, I'll test your plugin extensively, but for the moment all is OK !

Regards,
Sylvain

---

### Post by shadow_code on 2009-03-02
Way of ahead of you :P, New release 1.1 is now available

[SIZE="3"][COLOR="DarkRed"]**It is important you update**[/COLOR][/SIZE]

There's a redraw bug in 1.0.x that causes a delay when working with large files. But there's also [a few other cool changes detailed here]("http://jon-walsh.com/journal/2009/03/multi-edit-1-1/").

Cheers,
Jon

;)

---

### Post by shadow_code on 2009-05-01
[1.2 released]("http://jon-walsh.com/journal/2009/05/multi-edit-1-2/") :D

cheers

---

