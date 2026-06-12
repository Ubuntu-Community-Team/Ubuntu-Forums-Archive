---
title: "I think nautilus has a bug"
date: 2012-01-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shuttleworthwannabe on 2012-01-15
I use Opera  browser and evince a lot to read pdf. What I have noticed is that when I download pdf file in Opera and want to save in my document folder--the file name assigned in browser changes to an existing file name in the document folder, forcing me to change the file name to not clash with existing document file name.

I have noticed this behavior in evince as well--so if I want to save a copy of the document in a folder, nautilus defaults a file name to a document that already exists in that folder.

Firefox behavior fortunately is not like this and does the job just fine.

Anyone also experienced this?

---

### Post by nick_stokie on 2012-01-15
Yep, I've seen the same behaviour.

I'm away from my machine at the moment so can't confirm nautilus verson numbers, I'll try to do so later and will confirm if you raise a bug.

---

### Post by t1497f35 on 2012-01-15
Want a funny Nautilus bug?
Open your terminal (say) in the home dir.
Then
ln -s 1 2
Then
ln -s 2 1
Then try to browse the home dir with Nautilus. Cool eh?

---

### Post by fjgaude on 2012-01-15
> **t1497f35 said:**
> Want a funny Nautilus bug?
Open your terminal (say) in the home dir.
Then
ln -s 1 2
Then
ln -s 2 1
Then try to browse the home dir with Nautilus. Cool eh?

Pray tell, if you try this how do you revert back to normal?

---

### Post by CharlesA on 2012-01-15
> **t1497f35 said:**
> Want a funny Nautilus bug?
Open your terminal (say) in the home dir.
Then
ln -s 1 2
Then
ln -s 2 1
Then try to browse the home dir with Nautilus. Cool eh?

This isn't a bug. You are using symlinks the wrong way and causing problems.

> **fjgaude said:**
> Pray tell, if you try this how do you revert back to normal?

Just remove the symlinks via the terminal.

---

### Post by ronacc on 2012-01-15
if you are opening the file in evince via opera and then saving it , that is what is causing the problem . instead just right click on the link and select "save linked content as" or "save link to download folder" and it will save with the original file name not one assigned by evince .

---

### Post by t1497f35 on 2012-01-15
> **CharlesA said:**
> This isn't a bug. You are using symlinks the wrong way and causing problems.

It is a bug. Every reasonable app should take into consideration that a link might be broken or infinite, regardless, one must only try to read the first few chain links (not until you find the target, that's silly), so it is a bug in Nautilus. It's like division by zero in math - every reasonable mathematician must remember it and handle it gracefully.

Here's a screenshot of another file browser that handles this situation properly (doesn't crash).

---

### Post by MacUntu on 2012-01-15
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/914356](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/914356)

---

### Post by lucazade on 2012-01-15
> **t1497f35 said:**
> It is a bug. Every reasonable app should take into consideration that a link might be broken or infinite, regardless, one must only try to read the first few chain links (not until you find the target, that's silly), so it is a bug in Nautilus. It's like division by zero in math - every reasonable mathematician must remember it and handle it gracefully.

Here's a screenshot of another file browser that handles this situation properly (doesn't crash).

OT: what filemanager is in the screenshot??

---

### Post by t1497f35 on 2012-01-15
> **lucazade said:**
> OT: what filemanager is in the screenshot??
It's mine, it's not ready yet. There are also other file browsers that handle circular links properly. Here's a screenshot of pcmanfm (i.e. it doesn't crash either).

---

### Post by fjgaude on 2012-01-15
> **t1497f35 said:**
> It's mine, it's not ready yet. There are also other file browsers that handle circular links properly. Here's a screenshot of pcmanfm (i.e. it doesn't crash either).

That's the one I use and considered one of the best, if not the best.

---

### Post by ronacc on 2012-01-15
> **t1497f35 said:**
> It's mine, it's not ready yet. There are also other file browsers that handle circular links properly. Here's a screenshot of pcmanfm (i.e. it doesn't crash either).


when you get yours ready for testing setup aPPA if you haven't got one already and let us know , we'll put it through the wringer .:p

---

### Post by ombra on 2012-01-17
according to launchpad a fix has been released

---

