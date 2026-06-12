---
title: "Gedit , the ultimate IDE for linux"
date: 2010-04-05
forum: The Cafe
---

### Post by Viva on 2010-04-05
I've used geany before, but started searching for another IDE because I couldn't customize geany enough. I've tried netbeans, eclipse, bluefish and a few more until I found [this article]("http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html") from Micah Carrick. Gedit with plugins beats any IDE I've used before and it is considerably faster too:guitar:

---

### Post by chris200x9 on 2010-04-05
what does it have over geany?

---

### Post by denver on 2010-04-05
Tried to use it, but it kept adding \r at the end of every line. It showed up ad ^M in vim. Wasnt much of a problem until PHP threw a fit and gave an internal server error. Good olf vim to the rescue.

```
:%s/\r//g
```

If you know how to prevent it from adding a \r, I would be greatfull.

---

### Post by LeifAndersen on 2010-04-05
Well, at least you'll have newlines in MS notepad. :)

(At least, I though /n/r was the newline symbol in notepad).

---

### Post by MaxIBoy on 2010-04-05
I agree with the OP. Gedit is a great editor. It packs plenty of power without having too much baggage in the UI. 

@Denver: For me at least, Gedit has always left the existing carriage returns in without adding new ones. So when I move some code into MS Visual Studio to test on Windows, it offers to "normalize" the text file by converting it to all one newline convention.

---

### Post by Tibuda on 2010-04-05
I have used gedit for much time, but have switched to GVim. I agree Gedit is underrated, with the "external tools" plugin it becomes really powerful.

---

### Post by madjr on 2010-04-05
i was using gedit, but am now using **kwrite**

it has everything gedit has and more, no need for hacking, everything is in the options

some gedit stuff got screwed in karmic. the highlight with mouse and pasting with middle mouse button/wheel doesnt work on the same opened document (worked well in jaunty...). maybe someone should file for a papercut?

this feature works well on every other text editor, so i switched to **kwrite** and discovered how much powerful it becomes

i still use gedit sometimes, but not for dev

---

### Post by dragos240 on 2010-04-05
> **madjr said:**
> i was using gedit, but am now using **kwrite**

it has everything gedit has and more, no need for hacking, everything is in the options

some gedit stuff got screwed in karmic. the highlight with mouse and pasting with middle mouse button/wheel doesnt work on the same opened document (worked well in jaunty...). maybe someone should file for a papercut?

this feature works well on every other text editor, so i switched to **kwrite** and discovered how much powerful it becomes

i still use gedit sometimes, but not for dev

kate is good as well. It even has a built in terminal.

---

### Post by Simian Man on 2010-04-05
If I want a plain text editor, I'll use vim because it's just so efficient at editing text.  If I want to use an IDE, I want one with the ability to automate builds, an integrated debugger, VCS, and refactoring support.

Gedit Geany, and Kate are kind of a useless middle ground in my opinion.  Though I can see how others would find them useful.

---

### Post by Mr. Picklesworth on 2010-04-05
Gedit in Lucid has a really nice Word Completion plugin, too. It's like Scribes (an awesome Python-centric editor) in that it just completes words that are already written in documents you have open. 

That works way better in practise than it may sound, and for me is a fine alternative to the over-complicated autocomplete feature in lots of big IDEs :)

---

