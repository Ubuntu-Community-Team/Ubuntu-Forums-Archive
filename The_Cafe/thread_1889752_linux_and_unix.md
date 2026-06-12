---
title: "linux and unix?"
date: 2011-12-02
forum: The Cafe
---

### Post by Matrix01 on 2011-12-02
is linux based on unix?

---

### Post by Dangertux on 2011-12-02
> **Matrix01 said:**
> is linux based on unix?

[Minix]("http://en.wikipedia.org/wiki/MINIX") and BSD

---

### Post by lykwydchykyn on 2011-12-02
Define "based on".  It aims to comply more or less with Unix specifications.

---

### Post by Telengard C64 on 2011-12-02
Linux is a branch of the Unix family tree.

[http://www.freebsdnews.net/wp-content/uploads/unix_family_history_tree_1600x1200.jpg](http://www.freebsdnews.net/wp-content/uploads/unix_family_history_tree_1600x1200.jpg)

**_EDIT_**

Here's a more complete answer:
[http://www.linuxinsider.com/story/32719.html](http://www.linuxinsider.com/story/32719.html)

---

### Post by 3rdalbum on 2011-12-02
Short answer: No. Linux is not based on Unix.

Less short answer: Linux is a kernel that aimed to be compliant with many of the common traits between Unix kernels. GNU is a set of userspace programs that attempt to reimplement the common Unix userspace programs; not a drop-in replacement, but being similar in function.

Linux isn't much use on its own. GNU isn't much use on its own. When you put them together, you get GNU/Linux which forms the basis of all Linux distributions today.

There's still no Unix code, but there are many shared traits, and you mostly find that Unix systems run very similar software to Linux systems. It's also quite common to be able to take some source code to a Linux program and compile it on Unix, and vice-versa.

---

### Post by Valpskott on 2011-12-02
I'm no kernel developer, but I'd say Linux started out as a Unix/Minix clone, and I'm somewhat sure it was said in that Linux documentary that Linus wrote all the code himself from scratch without borrowing code from either Unix or Minix. So if we are going to use the analogies words as "related" and "family" (as of in biology), I'd state the Linux kernel was it's own distinct lifeform ("specially created" to borrow a Biblical phrase), as in life arising and evolving on another planet.

But the biological analogie fails here, cause if there are life on other planets, it sure does not draw influence from life on our planet.

Now, as far as I know, thats how the relationship between Linux and Unix started out to be, but sinse then I bet there has been "horizontal gene transfer" between the two.

And to be clear, I'm not even talkning about GNU here. Both Unix and Linux runs GNU, which in itself "completes" both families of kernels in becomming Operating Systems.

---

### Post by oldos2er on 2011-12-02
Not an Ubuntu support question; moved to Community Cafe.

---

### Post by Lars Noodén on 2011-12-02
You can look at the [UNIX Timeline](http://www.levenez.com/unix/) to put its development into perspective.

---

### Post by haqking on 2011-12-02
Linux or GNU/Linux is Unix-Like.

GNU's Not UNIX

---

### Post by Prospero2006 on 2011-12-02
[Great Biography of Linux Torvalds]("http://www.amazon.com/Just-Fun-Story-Accidental-Revolutionary/dp/0066620732/ref=sr_1_2?ie=UTF8&qid=1322851855&sr=8-2")

There's your answer for sure. It's an awesome book.

---

### Post by 3Miro on 2011-12-02
When you say Unix you can talk about either overall design (like everything is a file) or specific standard. All Unix systems have high level of cross compatibility and many of them share common code. Linux does not share common code with any Unix system, however, Linux uses the Unix design.

Linux is Unix-like. For many practical purposes, you can say "Linux is Unix", but this would be inaccurate in the strictest sense of the word Unix.

---

### Post by BrokenKingpin on 2011-12-02
> **Dangertux said:**
> [Minix]("http://en.wikipedia.org/wiki/MINIX") and BSD
Um... no. Unless by "based on" you mean inspired by. Linux was written from the ground up, but it is a unix-like system.

---

### Post by haqking on 2011-12-02
> I'm doing a (free) operating system (just a hobby, won't be big and professional like gnu) for 386(486) AT clones. This has been brewing since April, and is starting to get ready. I'd like any feedback on things people like/dislike in minix, **as my OS resembles it somewhat (same physical layout of the file-system **(due to practical reasons) among other things).
A quote from Linus Torvalds on Aug 25 91, where he posted his first announcement of Linux in comp.os.minix newsgroup

Minix being a Unix-Like OS and inspired Linus to create Linux

---

### Post by Telengard C64 on 2011-12-02
> **haqking said:**
> GNU's Not UNIX

Thought of that, too. The GNU programs common to all Linux distributions try to do the same jobs as traditional Unix programs, but they don't always work the same. You could call them *work-alikes* I suppose. Based on what I've read the GNU programs are more generally flexible. But again based on my reading, variety in implementations might be considered a hallmark of Unix systems as well.

[http://en.wikipedia.org/wiki/Unix-like#Categories](http://en.wikipedia.org/wiki/Unix-like#Categories)

> Dennis Ritchie, one of the original creators of Unix, has expressed his opinion that Unix-like systems such as Linux are de facto Unix systems.

^implying that trade marks and source code are not the definition of *Unix systems*.

If you read further into the article you find reference to Open Group certification. I don't think that applies to GNU/Linux.

[http://www.slackbook.org/html/introduction-slackware.html](http://www.slackbook.org/html/introduction-slackware.html)

> There are many reasons why Slackware is Linux's oldest living distribution . . . it tries to be as Unix-like as possible.

^implying that GNU/Linux distributions can be considered *Unix-like*.

Given the broad way OP has phrased the question I think a definitive answer is impossible. Given the history of the GNU/Linux operating system family, I think it is impossible to deny the strong connections between the two.

Linus didn't create Linux by compiling Unix source code. He wrote his own kernel and, with some help, added the GNU suite to make a more complete operating system. *GNU's Not Unix* and neither is Linux, but put them together and you get something which can be made to work much like Unix.

---

