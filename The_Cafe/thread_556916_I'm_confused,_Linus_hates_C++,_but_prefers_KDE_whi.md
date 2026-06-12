---
title: "I'm confused, Linus hates C++, but prefers KDE which is Qt/C++"
date: 2007-09-21
forum: The Cafe
---

### Post by loell on 2007-09-21
can someone alleviate my confusion? ;)

Edit: the link to the article [http://emonk.debianuruguay.org/?p=42]("http://emonk.debianuruguay.org/?p=42")

the original thread [http://www.spinics.net/lists/git/msg41567.html]("http://www.spinics.net/lists/git/msg41567.html")

---

### Post by loell on 2007-09-21
oops, a typo, i mean **prefers**

---

### Post by p_quarles on 2007-09-21
Because Linus likes to say things that cause controversy. He's admitted as much on several occasions. 

In my limited understanding of these things, C++ is just too high-level a language for coding something fundamental like a kernel. My best guess at an explanation would be that it's useless to Linus, so he decides to insult it. Kinda like the "real men don't back up their data" comment. Half of his public comments seem to be an in-joke that he shares with himself.

---

### Post by loell on 2007-09-22
> **p_quarles said:**
>  Half of his public comments seem to be an in-joke that he shares with himself.

i'm doubtful that this is one of those.. as he stated,

> infinite amounts of pain when they don’t work (and anybody who tells me
that STL and especially Boost are stable and portable is just so full
of BS that it’s not even funny

---

### Post by jrusso2 on 2007-09-22
Linux and C go together.  C and Unix go together.  Linus coded the kernel in C, so I guess that is what he likes.

---

### Post by Jucato on 2007-09-22
I think you should try to put it within the context of the discussion (not to mention a link to the mailing list thread).

Linus was basically reacting to someone telling him that his choice of C for Git is terrible and that it should have been made from C++. On the other hand, his statements about KDE versus GNOME was made not on grounds of whether it was C or C++, but on the ways development was handled.

So Linus is basically saying that C++ for Git, and for some purposes, is inappropriate. It had nothing to do with KDE or Qt. About STL or Boost, well, I think there are even C++ programmers who do not like STL either.

And yes, Linus does make very emphatic statements. He admits to it, and sometimes says that he intends it, if only to spark discussion, which he likes.

---

### Post by p_quarles on 2007-09-22
> **loell said:**
> i'm doubtful that this is one of those.. as he stated,
Well, like I said, that was my best guess. Not saying it was necessarily a good guess. :)

---

### Post by daxumaming on 2007-09-22
I'm sure you mean this [this post]("http://www.spinics.net/lists/git/msg41567.html")!

Actually, he just doesn't want his git coded in c++... c++ isn't really suitable for git. Besides, git's already working well, why would anyone want to mess it up.

---

### Post by loell on 2007-09-22
> **daxumaming said:**
> I'm sure you mean this [this post]("http://www.spinics.net/lists/git/msg41567.html")!

Actually, he just doesn't want his git coded in c++... c++ isn't really suitable for git. Besides, git's already working well, why would anyone want to mess it up.

yeah, thanks dax for posting the original thread :)

is it just just really the git that he's concerned about? i mean he does talk of several things in there not related to git

---

### Post by 23meg on 2007-09-22
Linus' sympathy for KDE is rooted in his dislike of GNOME (mostly interface and politics-wise), not in the technical superiority of KDE. I've heard him criticize KDE on technical grounds quite a few times.

---

### Post by loell on 2007-09-22
> **23meg said:**
> Linus' sympathy for KDE is rooted in his dislike of GNOME (mostly interface and politics-wise), not in the technical superiority of KDE. I've heard him criticize KDE on technical grounds quite a few times.


I see, now I'm somewhat enlightened,  I have not seen/read Linus criticizing KDE on technical grounds, maybe thats the missing link that I am looking for.

---

### Post by Crashmaxx on 2007-09-22
While we are on the topic of C++, I'm surprised that it makes for this much of an issue versus C. From my understanding, C++ is just C with stuff added to it to make it able to do more. So why couldn't you code something in C++ the same way as you would in C? And therefore why is there much debate about something like this at all?

---

### Post by Bothered on 2007-09-22
> **Crashmaxx said:**
> So why couldn't you code something in C++ the same way as you would in C?

You could, but that would be missing the point. C++ allows you to design the program in a completely different way to how it would be created in C.

---

### Post by vegittoss15 on 2009-02-13
His problem is with the idea of the "object-model crap" and STL/Boost. The latter with which I agree with.

---

### Post by bapoumba on 2009-02-13
Old thread, not much to add. Closing.

---

