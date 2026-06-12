---
title: "Programmer needed"
date: 2008-04-27
forum: The Cafe
---

### Post by cartisdm on 2008-04-27
I know I've seen them but I don't remember how I came across it.  How do I find a person to put together a program for me (quickly) if I give them a list of specifications?  I know I've seen people say "I need someone to transfer X number of data into this excel spreadsheet.  I'll give you $x.xx via paypal".  I have a project my roommate and I are stuck on and I really need the core of it put together.  It's pretty basic VB but I'm not a programmer by any means...could someone point me in the direction to find a place where I could get this done?

---

### Post by blithen on 2008-04-27
Here would be a good place I'm pretty sure. Just post the specifications.
If it's not the right spot the Mods can move it. ^^

---

### Post by blastus on 2008-04-27
You've stated nothing about this project so I can only assume that it is either a student project or a work-related project. If this is a student project then do it yourself. If it is a work project then go somewhere else--no one is going to do your work for you.

---

### Post by cartisdm on 2008-04-27
> **blastus said:**
> You've stated nothing about this project so I can only assume that it is either a student project or a work-related project. If this is a student project then do it yourself. If it is a work project then go somewhere else--no one is going to do your work for you.

Student related - and yea I kinda figured that was coming:rolleyes: but I still could use the help

---

### Post by blastus on 2008-04-27
> **cartisdm said:**
> Student related - and yea I kinda figured that was coming:rolleyes: but I still could use the help

Why do you need to do such a project without any background knowledge or experience in the subject matter? You should talk to your instructor/professor.

---

### Post by cartisdm on 2008-04-27
> **blastus said:**
> Why do you need to do such a project without any background knowledge or experience in the subject matter? You should talk to your instructor/professor.

Because my professor believes that posting old (basic) projects online so we can figure out the last three chapters and not holding class the last two weeks before the final is teaching class.....

---

### Post by blastus on 2008-04-27
> **cartisdm said:**
> Because my professor believes that posting old (basic) projects online so we can figure out the last three chapters and not holding class the last two weeks before the final is teaching class.....

Let me give you a tip about professors; don't rely on them to teach you. It's really up to you to learn the subject matter and do whatever it takes to learn it. Perhaps what you are asking for is a tutor?

---

### Post by cartisdm on 2008-04-27
Tutors are great (have them for accounting haha) but they aren't much good during crunch time;)

---

### Post by blastus on 2008-04-27
> **cartisdm said:**
> Tutors are great (have them for accounting haha) but they aren't much good during crunch time;)

I would be prepared to stay up all night every night until it is done then. I know what it is like to spend 10 hours a day studying every day. I also know what it is like to have a professor that doesn't have answers. You've got to start somewhere...

Edit: If you need some general direction about this then I can certainly provide it. If you can provide some details then I can try to point you in the *right* direction.

---

### Post by cardinals_fan on 2008-04-27
Virginia Tech?

---

### Post by cartisdm on 2008-04-27
> **cardinals_fan said:**
> Virginia Tech?

James Madison

---

### Post by cartisdm on 2008-04-27
This is what I have so far:

```
        Using reader As New StreamReader(OpenFileDialog1.FileName)
            readString = reader.ReadToEnd()
            reader.Close()
        End Using

Dim splitString() as String = readString.Split(new Char { "," } )

        For Each currentString As splitString
            sportListBox.Items.Add(currentString)
        Next

    End Sub
```

I'm getting an error on **splitstring**.  It's saying it's not defined

---

### Post by LaRoza on 2008-04-27
> **cartisdm said:**
> I know I've seen them but I don't remember how I came across it.  How do I find a person to put together a program for me (quickly) if I give them a list of specifications?  I know I've seen people say "I need someone to transfer X number of data into this excel spreadsheet.  I'll give you $x.xx via paypal".  I have a project my roommate and I are stuck on and I really need the core of it put together.  It's pretty basic VB but I'm not a programmer by any means...could someone point me in the direction to find a place where I could get this done?

[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

