---
title: "Visual Basic 2005 Help Needed!"
date: 2007-09-29
forum: The Cafe
---

### Post by giambrone on 2007-09-29
This being the only forum I'm signed up to its worth a shot...

Basically I'm creating a relatively simply dice game for my AS level Computing course. I've done a "select case" statement to change the colours of the dots so as to make them appear or disappear. Instead of making it have a background colour I want it to have an image (so that the dots appear round, not square). Just to make it good really.

The picture I want to use is simply a .jpg, but I've got it as Gif and Bmp also.

I'm wondering what I need to put in my existing code to achieve this.

Below I'll post what I've got for the dice so far.

Thank you so much guys.

Matt:KS

>             'Player1's Dice Number 1's Colouring
            Select Case Die1
                Case 0
                    GoTo ReRoll
                Case 1
                    spt12.BackColor = Color.Black
                Case 2
                    spt11.BackColor = Color.Black
                    spt13.BackColor = Color.Black
                Case 3
                    spt11.BackColor = Color.Black
                    spt12.BackColor = Color.Black
                    spt13.BackColor = Color.Black
                Case 4
                    spt11.BackColor = Color.Black
                    spt17.BackColor = Color.Black
                    spt14.BackColor = Color.Black
                    spt13.BackColor = Color.Black
                Case 5
                    spt11.BackColor = Color.Black
                    spt17.BackColor = Color.Black
                    spt14.BackColor = Color.Black
                    spt13.BackColor = Color.Black
                    spt12.BackColor = Color.Black
                Case 6
                    spt11.BackColor = Color.Black
                    spt17.BackColor = Color.Black
                    spt14.BackColor = Color.Black
                    spt13.BackColor = Color.Black
                    spt18.BackColor = Color.Black
                    spt19.BackColor = Color.Black
            End Select

P.S. I also know that GoTo is obselete, it is just easier ;)

---

### Post by thisllub on 2007-09-29
Why wouldn't you just index 6 complete dice images?

---

### Post by giambrone on 2007-09-29
Because I don't know how to reference images at all...
I started learning vb about 6 lessons ago lol.

Steep learning curve. Eh?

---

### Post by giambrone on 2007-09-29
Aha!
           >  Panel1.BackgroundImage = Image.FromFile _
                    (System.Environment.GetFolderPath _
                    (System.Environment.SpecialFolder.Personal) _
                    & "Path/To/Picture/In/My/Documents.jpg")

---

