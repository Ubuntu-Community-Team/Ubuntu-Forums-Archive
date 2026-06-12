---
title: "How to program Chess?"
date: 2008-05-13
forum: The Cafe
---

### Post by ColonelKlink on 2008-05-13
Hey all,

I'm new to this forum and I was wondering if any of you have had experience ever programming a chess game.  

I'm writing it in java was hoping that someone knows some generic rules or strategies that would apply to most situations that the AI could use.  

I'm thinking at the moment of simply it looking at every possible move, (in order of importance of piece) and then if a move doesn't put the king in check, do the same thing again (this time checking the other player's pieces as well) incrementing a counter for every piece that would allow you to take and decrementing it for every one you would lose.  So basically it "thinks" one turn ahead.

The problem with this idea, is that besides its sheer brute force method, it really doesn't take anything else into account.

Any suggestions or criticism would be greatly appreciated.


Thanks.

---

### Post by maniacmusician on 2008-05-13
Google is your friend. "programming chess" got me a bunch of hits that looked useful at a first glance.

As an aside; C++ (or any other language, really) with the Qt4.4 toolkit destroys Java in terms of cross-compatibility.

---

### Post by chick on 2008-05-14
There are basically two parts: generating all legal board positions after a certain depth/ply, and then evaluating them with respect to the current player. After that, pick the move branch that leads to the board position with highest score.

You would want to read about Minimax and AlphaBeta algorithm.

---

### Post by cardinals_fan on 2008-05-14
The Fruit engine is pure evil.  It used to be open source; you can probably grab some old code to look at.

---

### Post by graabein on 2008-05-14
It's like Chick says. Generate and evaluate. It's pretty easy to get it up and running but to get a really good computer player you'll need a lot of tweaking. You have to know when to stop searching and how to see what board positions are better than others. 

I suggest you try the forum for [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39").

---

