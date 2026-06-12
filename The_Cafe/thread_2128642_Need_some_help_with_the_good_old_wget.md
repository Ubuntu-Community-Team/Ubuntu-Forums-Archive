---
title: "Need some help with the good old wget"
date: 2013-03-23
forum: The Cafe
---

### Post by kahrkunne on 2013-03-23
What I want to do: download either the whole 4chan directory or everything in this directory of [http://www.malakim.org/stuff/](http://www.malakim.org/stuff/)
(Little explaination here... Found a cool python script that looks for hidden stuff in images. Now scanning my own 4chan folder for hidden stuff, and also looking for other people's 4chan folder. Found this one using a google dork.)
If I do wget [http://www.malakim.org/stuff/4chan](http://www.malakim.org/stuff/4chan) it gives me the html file or whatever. Not what I want anyways.

EDIT: for those interested, the python script just started raking in some results.
I got 3 results so far which are not 
A. A sequence of somewhere between 5 and 10 numbers and
B. 1 byte files
The biggest of these is 1.3mb
EDIT2: And it's done. Out of the 36gigs of pictures I had it managed to give me 3 files which I don't know what they are and are unreadable, and one picture that was (apparently) hidden in a .gif file (which was actually unreadable, so that's kinda funny)
EDIT3: Turns out the .gif that wasn't working IS working as a .jpg. The .jpg is the image the script gave me. So that's cool I geuss.

---

### Post by schragge on 2013-03-23
```
wget -r -np http://www.malakim.org/stuff/
```

---

### Post by kahrkunne on 2013-03-23
I can see it downloading a whole lot of jpg's now, thanks man.
OOOH ****...
I did 

wget -r -np [http://www.malakim.org/stuff/4chan](http://www.malakim.org/stuff/4chan)

but now it's downloading the entirety of blalba/stuff/ (and probably everything on the page)
How is this happening?

---

### Post by schragge on 2013-03-23
Hmm, strange. *-np* means *--no-parent*, so this shoudn't happen. However, you can try
```
wget -r -l1 http://www.malakim.org/stuff/4chan/
```

---

### Post by kahrkunne on 2013-03-23
I've tried a couple of others and it hasn't occured again (I think)
I might have screwed up. Thanks for all the help.
God I'm turning into some kind of maniac that spends his day downloading archives of image boards and searching for hidden files in the images 0.o

---

