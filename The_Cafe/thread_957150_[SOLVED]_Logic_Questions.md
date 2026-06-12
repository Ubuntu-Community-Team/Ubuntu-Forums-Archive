---
title: "[SOLVED] Logic Questions"
date: 2008-10-24
forum: The Cafe
---

### Post by hanzj on 2008-10-24
Nestor, Portia, Romeo, Sebastian, Tybalt, and Walter are all cast members of a Shakespearean play. They meet every week to practice.

[FONT=Book Antiqua]Last week Romeo arrived after Walter but before Portia.

Tybalt arrived after Sebastian but before Portia.

Nestor arrived after Sebastian but before Romeo.[/FONT]


Question 1: What is the minimum number of people who could have arrived after Sebastian?

Question 2: What is the maximum number of people who could have arrived before Romeo?

In stating your answer, please indicate how you reached your answer. Diagrams or text explanations would be great.


Thanks.

---

### Post by -grubby on 2008-10-24
[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

### Post by hanzj on 2008-10-24
Nathan, this is not a homework problem. 8-)

---

### Post by schauerlich on 2008-10-24
Write each of their names on a piece of paper and then shuffle them around until it makes sense.

---

### Post by -grubby on 2008-10-24
> **hanzj said:**
> Nathan, this is not a homework problem. 8-)

What is it then? Sounds like one to me, sorry

---

### Post by hanzj on 2008-10-24
Puzzle.

---

### Post by schauerlich on 2008-10-24
> **hanzj said:**
> Puzzle.

Well it's not much fun if we do it for you, then, is it?

Here's another one.

There are 18 people at a dance. Each of them is given a number, 1 through 18. #1 realizes at some point during the dance that everyone is paired off such that the numbers of the two dancers add up to a perfect square. Who is #1 dancing with?

---

### Post by scragar on 2008-10-24
> **hanzj said:**
> **Nestor**, **Portia**, **Romeo**, **Sebastian**, **Tybalt**, and **Walter** 
...
Question 2: What is the maximum number of people who could have arrived before **Ray**?
...

Who's ray? :p



And the phrasing sounds like a homework question to me as well.

---

### Post by hanzj on 2008-10-24
Friends,
This is not a homework assignment. I'm going through some logic puzzles and the answer is in the back of the book but it seems to be wrong to me. 
So I wanted to confirm my suspicion with the help of the Ubuntu Community.

---

### Post by hanzj on 2008-10-24
I have scribbled diagrams to help me.

---

### Post by tylerspaska on 2008-10-24
I'll bite, homework or not. If this is your homework you're lucky to only have one problem.

4 and Ray wasn't invited

---

### Post by scragar on 2008-10-24
> **EDavidBurg said:**
> Well it's not much fun if we do it for you, then, is it?

Here's another one.

There are 18 people at a dance. Each of them is given a number, 1 through 18. #1 realizes at some point during the dance that everyone is paired off such that the numbers of the two dancers add up to a perfect square. Who is #1 dancing with?
My workings, pair on left, number in col 2, and numbers making squares to the right of them(numbers paired up marked with a hash). The bit after the dashes was just me listing squares in range(36+ not listed because it's impossible for 18 to be paired with himself/herself)
```
	1	3#	8#	15
14 ####	2	7#	14
13 ####	3	1#	6#	13
12 ####	4	5#	12
11 ####	5	4#	11
10 ####	6	3#	10
18 ####	7	2#	9#	18
17 ####	8	1#	17
16 ####	9	6#	16
 6 ####	10	6	15#
 5 ####	11	5	14#
 4 ####	12	4	13#
 3 ####	13	3	12#
 2 ####	14	2	11#
	15	1	10
 9 ####	16	9
 8 ####	17	8
 7 ####	18	7
-------------------------------
	4	9	16	25
```
if I worked it out right it's 15...

---

### Post by kartoshka on 2008-10-24
> **scragar said:**
> Who's ray? :p

Lol where the hell did you get Ray? :D Or did i completely miss something?

---

### Post by LaRoza on 2008-10-24
> **kartoshka said:**
> Lol where the hell did you get Ray? :D Or did i completely miss something?

He wasn't invited.

---

### Post by scragar on 2008-10-24
Read the quote, it's taken directly out of your question. Ray isn't in the people invited listed above it, so where does he come from?

EDIT:
well that's not fair, you edit the question to replace "ray" with "romeo", and don't say so in the thread. :p

---

### Post by hanzj on 2008-10-24
The thread has been taken over with another puzzle.

---

### Post by tylerspaska on 2008-10-24
@EDavidBurd

15

---

### Post by kartoshka on 2008-10-24
> **hanzj said:**
> Nestor, Portia, Romeo, Sebastian, Tybalt, and Walter are all cast members of a Shakespearean play. They meet every week to practice.

[FONT=Book Antiqua]Last week Romeo arrived after Walter but before Portia.

Tybalt arrived after Sebastian but before Portia.

Nestor arrived after Sebastian but before Romeo.[/FONT]


Question 1: What is the minimum number of people who could have arrived after Sebastian?

Question 2: What is the maximum number of people who could have arrived before Romeo?

In stating your answer, please indicate how you reached your answer. Diagrams or text explanations would be great.


Thanks.

Oh thanks for clearing that up LaRoza... :p

Was "Romeo" in Question 2 "Ray" before the edit? Or am I hallucinating? Bedtime, I think...

---

### Post by hanzj on 2008-10-24
Oops. Reason for edit is now in OP.

---

### Post by kartoshka on 2008-10-24
Thank you for putting my mind at ease :)

---

### Post by hanzj on 2008-10-24
Ahem, OP here. Let's go back to the main post please. 

:)

---

### Post by scragar on 2008-10-24
> **hanzj said:**
> Nestor, Portia, Romeo, Sebastian, Tybalt, and Walter are all cast members of a Shakespearean play. They meet every week to practice.

[FONT=Book Antiqua]Last week Romeo arrived after Walter but before Portia.

Tybalt arrived after Sebastian but before Portia.

Nestor arrived after Sebastian but before Romeo.[/FONT]


Question 1: What is the minimum number of people who could have arrived after Sebastian?

Question 2: What is the maximum number of people who could have arrived before Romeo?

In stating your answer, please indicate how you reached your answer. Diagrams or text explanations would be great.


Thanks.

```
	W	S
	N	T?
	R	T?
	P
```Q1: 4: N, T, R and P. W is possible, but not counted in min
Q2: 4(again?): W, S, N and T(possible, so count in max)


Honestly, is there nothing Gedit can't solve?

---

### Post by kartoshka on 2008-10-24
#1 is 4. Walter is the only one who could have arrived before Sebastian. Portia was after Tybalt who was after Sebastian. Romeo was after Nestor who was after Sebastian. Ergo, only Walter remains. Though he could also have arrived after Sebastian (it says minimum though).

#2 is also 4. Portia definitely arrived after Romeo, but that is the only definite conclusion you can reach.

> **scragar said:**
> 
Honestly, is there nothing Gedit can't solve?


Exactly what I did lol.

---

### Post by kartoshka on 2008-10-24
Oh btw hanzj, just out of curiosity, did the book say something different?

---

### Post by hanzj on 2008-10-24
Earlier  <----------------> Later


S ------- T--------- P


W ----------- R ---- P

S ---- N----- R

My answers are **4**...**4**, too. The book says 1...3.

---

### Post by hanzj on 2008-10-24
Thanks for confirming my answer. Looks like the book is wrong.

---

### Post by rzrgenesys187 on 2008-10-24
Hmm... I seem to agree with the book.  For the minimum number of people after Sebastian I got 3 and for the max before Romeo I got 1.

```
Earlier -- Later
1: WRP
2: STP
3: RSN

Combine 1 and 3: WRPSN
Combine this and 2: WRSNTP

```

The order of WRS is correct.  The only ones that wouldn't be sure of the exact ordering would be NTP.  However the exact ordering isn't needed to answer the questions.

Using WRSNTP it is pretty easy to see that NTP came after Sebastian and W came before Romeo. (Providing I didn't screw up somewhere)

Please let me know if you find a problem in my logic since I'm finding it interesting that my answer differs with previous posts

---

### Post by kartoshka on 2008-10-24
> **rzrgenesys187 said:**
> 

```
Earlier -- Later
1: WRP
2: STP
**3: RSN**

Combine 1 and 3: WRPSN
Combine this and 2: WRSNTP

```



3. Is supposed to be SNR (Nestor after Sebastian, but before Romeo)

---

### Post by rzrgenesys187 on 2008-10-24
Thanks, that was bugging me.  I figured I had to have made some simple mistake somewhere and it turns out I did :)

---

