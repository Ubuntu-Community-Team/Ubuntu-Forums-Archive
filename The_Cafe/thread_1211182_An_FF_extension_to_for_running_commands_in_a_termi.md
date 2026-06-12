---
title: "An FF extension to for running commands in a terminal"
date: 2009-07-12
forum: The Cafe
---

### Post by andrew-sayers on 2009-07-12
I've been helping out lately with a Firefox extension called [TerminalRun]("http://addons.mozilla.org/en-US/firefox/addon/9738").  It's designed to let absolute beginners know that the terminal exists, and to make it really really easy to run terminal commands:

[ATTACH]120808[/ATTACH]

Actually, I reckon it's pretty handy even if you were born on a command-line.  But I'm biased, so what do you guys think?  It's still experimental right now, so feedback is very welcome :)

	- Andrew

---

### Post by stwschool on 2009-07-12
As someone who is growing to love the terminal, I can tell you that this is useful :)

---

### Post by Marlonsm on 2009-07-12
That's nice.
Just an idea: if possible, make it filter all malicious commands, so it won't erase important files.

---

### Post by lovinglinux on 2009-07-12
I have been using TerminalRun before andrew-sayers stepped in to help the developer and must say this new version is awesome. The integration with ubuntuforums.org is excellent, you can save a script with the command automatically and the status bar displays all commands in a page. This is a must have for any Ubuntu user.

EDIT: screenshots

---

### Post by monsterstack on 2009-07-12
This looks fun. I'll just throw in some random terminal commands so I can test this baby out.

Print "Hello" over and over.
```
while true; do echo -en "Hello "; sleep 0.5; done
```

Write some text to a file and display contents of file.
```
echo "Hello.\nHow's life?" > randomtext.txt
cat randomtext.txt

```

Get the easter-egg.
```
apt-get moo
```

Futurama quote.
```
curl -Is slashdot.org | egrep '^X-(F|B|L)' | cut -d \- -f 2;
```

Gogogogo!

---

### Post by andrew-sayers on 2009-07-12
> **monsterstack said:**
> ```
while true; do echo -en "Hello "; sleep 0.5; done
```

Ooh, that's interesting.  For those of you not playing along at home, TerminalRun didn't think that was a terminal command because "while" isn't a program.  You can force it with:

```
#!/bin/bash

while true; do echo -en "Hello "; sleep 0.5; done
```

I'll have a think about the best way to handle this.

	- Andrew

---

### Post by lovinglinux on 2009-07-12
> **andrew-sayers said:**
> Ooh, that's interesting.  For those of you not playing along at home, TerminalRun didn't think that was a terminal command because "while" isn't a program.  You can force it with:

```
#!/bin/bash

while true; do echo -en "Hello "; sleep 0.5; done
```

I'll have a think about the best way to handle this.

	- Andrew

There is another situation that might cause some problems, when the code does not include the real command but something to be replaced by the user, like <programname>.

---

### Post by monsterstack on 2009-07-12
Hrmm, that's odd. It's telling me that there aren't any scripts at all on this page. I can still right-click and run them, though. Erk. What could be causing this meddlesome behaviour?

---

### Post by lovinglinux on 2009-07-12
> **andrew-sayers said:**
> Ooh, that's interesting.  For those of you not playing along at home, TerminalRun didn't think that was a terminal command because "while" isn't a program.  You can force it with:

```
#!/bin/bash

while true; do echo -en "Hello "; sleep 0.5; done
```

I'll have a think about the best way to handle this.

	- Andrew

The status bar feature just recognizes the first line with **#!/bin/bash**

---

### Post by andrew-sayers on 2009-07-12
> **lovinglinux said:**
> There is another situation that might cause some problems, when the code does not include the real command but something to be replaced by the user, like <programname>.

Hmm, that's a tough one.  Adding "open a terminal" to the menu would save some clicks, and letting the user edit the command in the status bar popup could work.  Forgetting practicality for a moment (I'm gonna regret saying that...), what would you like to happen in that situation?

> **monsterstack said:**
> Hrmm, that's odd. It's telling me that there aren't any scripts at all on this page. I can still right-click and run them, though. Erk. What could be causing this meddlesome behaviour?

That is indeed odd.  Just to be clear, are you saying that the in-page menus don't appear, or that the status bar icon says there are no scripts, or both?

> **lovinglinux said:**
> The status bar feature just recognizes the first line with **#!/bin/bash**

Use the first non-empty, non-comment line in the status bar popup, gotcha :)

	- Andrew

---

### Post by monsterstack on 2009-07-12
> **andrew-sayers said:**
> That is indeed odd.  Just to be clear, are you saying that the in-page menus don't appear, or that the status bar icon says there are no scripts, or both?

Very both! I am running Firefox 3.5 if that makes any difference. :s

---

### Post by lovinglinux on 2009-07-12
> **andrew-sayers said:**
> Hmm, that's a tough one.  Adding "open a terminal" to the menu would save some clicks, and letting the user edit the command in the status bar popup could work.  Forgetting practicality for a moment (I'm gonna regret saying that...), what would you like to happen in that situation?

It's not an issue for me, but most newcomers will probably not understand why they click the "Run in terminal" and the command doesn't work. I bet lot's of people will click without paying attention to the command itself. Maybe you could send the command to a zenity dialog, asking to confirm if the command is correct, then sending it back to the terminal. It would be less practical for experienced users, but safer for newcomers.

---

### Post by lovinglinux on 2009-07-12
> **monsterstack said:**
> Very both! I am running Firefox 3.5 if that makes any difference. :s

I'm running 3.5 and it works.

---

### Post by lovinglinux on 2009-07-12
> **andrew-sayers said:**
> Use the first non-empty, non-comment line in the status bar popup, gotcha :)

That makes sense :)

---

### Post by andrew-sayers on 2009-07-12
> **monsterstack said:**
> Very both! I am running Firefox 3.5 if that makes any difference. :s

Hmm.  One last obvious thing then - can you check that you've got TerminalRun 0.4 installed, not 0.3?  Assuming it's 0.4, would it be okay if I went away and wrote up some tests, then PMed you tomorrow about running the tests?  Tracking this down is likely to take more time than I have tonight, and more posts than it's reasonable to expect everyone else to sit through.

> **lovinglinux said:**
> It's not an issue for me, but most newcomers will probably not understand why they click the "Run in terminal" and the command doesn't work. I bet lot's of people will click without paying attention to the command itself. Maybe you could send the command to a zenity dialog, asking to confirm if the command is correct, then sending it back to the terminal. It would be less practical for experienced users, but safer for newcomers.

Hmm also :)

It might be possible to autodetect some simple examples of this (like text in italics or angle brackets), or to print a special message if the command fails.  I'll get back to you when I've had a look at what really is practical.

	- Andrew

---

### Post by monsterstack on 2009-07-12
> **andrew-sayers said:**
> Hmm.  One last obvious thing then - can you check that you've got TerminalRun 0.4 installed, not 0.3?  Assuming it's 0.4, would it be okay if I went away and wrote up some tests, then PMed you tomorrow about running the tests?  Tracking this down is likely to take more time than I have tonight, and more posts than it's reasonable to expect everyone else to sit through.
	- Andrew

Yeah, 0.4 running here. I'd be glad of the tests. Fire your PMs away!

---

### Post by monsterstack on 2009-07-13
A false alarm. I noscripted it by mistake. Doh. Looks like I'm going back to noob school. On the other hand, I did get a 0.5 Alpha out of it. *Just as planned*. Everything works great. Really good stuff.

---

### Post by andrew-sayers on 2009-07-13
> **monsterstack said:**
> A false alarm. I noscripted it by mistake. Doh. Looks like I'm going back to noob school. On the other hand, I did get a 0.5 Alpha out of it. *Just as planned*. Everything works great. Really good stuff.

What's that you say?  The statusbar popup should warn you when the extension has been disabled?  That's a good point, I'll see the bug gets fixed in 0.5 :)

	- Andrew

---

### Post by andrew-sayers on 2009-07-14
> **Marlonsm said:**
> That's nice.
Just an idea: if possible, make it filter all malicious commands, so it won't erase important files.

This comment got a bit lost in the traffic before, but I was paying attention :)

The problem with filtering is that malicious people are so sneaky - viruses wouldn't exist if it was that easy to filter out bad stuff.  But *warning* people about potential badness is pretty easy, and it makes them better at spotting traps that are too clever to detect automatically.

> **lovinglinux said:**
> It's not an issue for me, but most newcomers will probably not understand why they click the "Run in terminal" and the command doesn't work. I bet lot's of people will click without paying attention to the command itself. Maybe you could send the command to a zenity dialog, asking to confirm if the command is correct, then sending it back to the terminal. It would be less practical for experienced users, but safer for newcomers.

I mentioned editing before as a solution, and I sort of ran with that because it lets you actually fix the problem.

How would you both feel about a solution like this:

Say you have a command like [FONT="Courier New"]sudo rm -rf <directory you can't usually delete>[/FONT].  Instead of "Run in terminal", TerminalRun would say "Edit script...", which takes you to a window that looks something like this mock-up I made with The GIMP:

[ATTACH]121047[/ATTACH]

[ATTACH]121048[/ATTACH]

[ATTACH]121049[/ATTACH]

The "previous issue" and "next issue" buttons would change to "run in terminal" and "save script" after you passed the last issue.

I'm not promising I can actually do this, but I don't expect it'll be too impossible to put something together.

	- Andrew

---

### Post by lovinglinux on 2009-07-14
> **andrew-sayers said:**
> This comment got a bit lost in the traffic before, but I was paying attention :)

The problem with filtering is that malicious people are so sneaky - viruses wouldn't exist if it was that easy to filter out bad stuff.  But *warning* people about potential badness is pretty easy, and it makes them better at spotting traps that are too clever to detect automatically.



I mentioned editing before as a solution, and I sort of ran with that because it lets you actually fix the problem.

How would you both feel about a solution like this:

Say you have a command like [FONT="Courier New"]sudo rm -rf <directory you can't usually delete>[/FONT].  Instead of "Run in terminal", TerminalRun would say "Edit script...", which takes you to a window that looks something like this mock-up I made with The GIMP:

[ATTACH]121047[/ATTACH]

[ATTACH]121048[/ATTACH]

[ATTACH]121049[/ATTACH]

The "previous issue" and "next issue" buttons would change to "run in terminal" and "save script" after you passed the last issue.

I'm not promising I can actually do this, but I don't expect it'll be too impossible to put something together.

	- Andrew

Looks good. What about the options above the code tags, will they update as well?

---

### Post by andrew-sayers on 2009-07-14
> **lovinglinux said:**
> Looks good. What about the options above the code tags, will they update as well?

Yeah, I suppose they'll have to.  Users that get into that "click anything that moves" state need to be kept safe, so TerminalRun should make "Edit script..." the default action for dodgy-looking scripts.

I think "Edit script..." should normally be below "Save as..." in the menu, then swap with "Run in terminal" for dodgy-looking scripts.  What do you think?

	- Andrew

---

### Post by lovinglinux on 2009-07-14
> **andrew-sayers said:**
> Yeah, I suppose they'll have to.  Users that get into that "click anything that moves" state need to be kept safe, so TerminalRun should make "Edit script..." the default action for dodgy-looking scripts.

I think "Edit script..." should normally be below "Save as..." in the menu, then swap with "Run in terminal" for dodgy-looking scripts.  What do you think?

	- Andrew

I think is great.

---

