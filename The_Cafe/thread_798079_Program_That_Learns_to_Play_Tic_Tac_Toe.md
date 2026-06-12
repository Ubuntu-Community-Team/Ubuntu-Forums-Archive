---
title: "Program That Learns to Play Tic Tac Toe"
date: 2008-05-17
forum: The Cafe
---

### Post by dr.silly on 2008-05-17
This is a little project of mine that will learn to play Tic Tac Toe the more you play against it. It won't even know the rules. I wrote it in Java as a kind of just for fun thing in my spare time. It is not fully documented and doesn't have a GUI but it still gets the general idea ;) . 

NOTE: This should work on other operating systems.

**Installation**

Download the attached zip file and extract it. You will need java for this to work. To see if you have java, open a Terminal and type

```
java -version
```

If you get something resembling

```
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
```

you're good. If not, get the Java Runtime Environment (there are plenty of guides; google it).

Now if Java is all go, cd into the directory that you extracted the files and run

```
java ConsoleMain
```

When it prompts you for a position you can type a number 1-9 which correspond to the board as follows

7 8 9 
4 5 6 
1 2 3 

Notice how this is the same as a numpad arrangement. Sorry laptopers.

To quit type 

```
exit
```

at any point.

**How**

The program store past games played and their outcomes in the file games.txt. It then uses this to determine the route from the current position with the greatest probability of a win. To demonstrate how this works play a game and beat then try and play the same game again and it will choose a different position.

**How to Compile Yourself**

All the source is in the zip just use javac. I compiled this with javac version 1.6.0_06 source version 6.0 on a 32 bit processor.

**Uninstall**

Just delete the folder you extracted.



Tell me watcha think!

---

### Post by Frak on 2008-05-17
Could I get the file?

---

### Post by dr.silly on 2008-05-17
woops sorry about that

---

### Post by Frak on 2008-05-17
> **dr.silly said:**
> woops sorry about that
Thanks :D

---

### Post by Vorian on 2008-05-17
(wargames)

---

### Post by dr.silly on 2008-05-17
yep kinda vital isn't it?

---

### Post by Sporkman on 2008-05-17
> **Vorian said:**
> (wargames)

I wrote a learning tic tac toe program (on a TRS80 Model IV) myself back in the 80's after being inspired by that movie.

---

### Post by Frak on 2008-05-17
How long do I have to play until it can hack the Pentagon?

---

### Post by teet on 2008-05-17
nevermind.

---

### Post by dr.silly on 2008-05-18
hm i've never heard of it i was inspired by ... just kinda doing it for fun

---

### Post by frup on 2008-05-18
On windows 3.1 I believe (maybe early 95 otherwise) I had a game of 3d tic tac toe which I was terrible at because I was between the ages of 7 and 11 when I was trying to play it but recently while bored my girlfriend and I played 3 tic tac toe (or naughts and crosses) on paper and it was a lot of fun.

Is there a version like this available (I am searching the repos for existing games but otherwise that might be a cool feature to add, results in a lot less ties :P )

---

### Post by LinuX-M@n1@k on 2008-07-24
> **Frak said:**
> How long do I have to play until it can hack the Pentagon?

About 546 years... :lolflag:
Man, I can barely lose in this game! For example, the digits are my moves and I am first to move:

|1|4|O|
|O|_|O|
|O|3|2|
:lolflag:

It seems that your game doesn't want to win for some reason?! :lol:

---

### Post by RATM_Owns on 2008-07-24
It's failing. I won 9 out of 9 times by using "5 2 8"

The EXACT same game EVERY time.

EDIT: If the game is already in games.txt, it won't write it again. So I copied and pasted it another 10 or so times.
So can somebody make a perfect (or near-perfect) games.txt file?

---

