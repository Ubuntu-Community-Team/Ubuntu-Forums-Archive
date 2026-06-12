---
title: "ftp error"
date: 2006-01-30
forum: The Cafe
---

### Post by GabrielWolff on 2006-01-30
I have somefiles on a website, which I uploaded via gftp.
When trying to access them through gftp, everything is OK.
But when simply klicking some files in the browser, I get an error message, and when right clicking them and chosing "Save link as", I get the error message: "The link could not be saved. The website migh have been removed or had it's name changed".
Others, in the same format (pdf) load OK

The page is: [http://www.majikstreet.org/GabrielWolff/](http://www.majikstreet.org/GabrielWolff/)

Does anyone have an idea why?

G

---

### Post by majikstreet on 2006-01-30
I see the beep errors -- I really don't know why that is.. My idea would be to re-upload the stuff that gives you errors.. My other idea would have to do with changing permissions which I could do for you.... 

I may be wrong, btw.. Hopefully someone will look here and say, oh man he's stupid! I know the answer and reply..

majikstreet

---

### Post by GabrielWolff on 2006-01-31
[QUOTE=majikstreet]I see the beep errors -- I really don't know why that is.. My idea would be to re-upload the stuff that gives you errors.. My other idea would have to do with changing permissions which I could do for you.... 

I may be wrong, btw.. Hopefully someone will look here and say, oh man he's stupid! I know the answer and reply..

majikstreet[/QUOTE]

Hey Majik

You say the beep errors are not *your *invention? Funny... like: in the first place, didn't *you *write that text "beep, you shouldn't bee here, go away"?
I uploaded them once more, but it didn't help much.
What do you mean by "changing permissions"? What permissions?

Thanx

G

---

### Post by majikstreet on 2006-01-31
Yeah, I did make the beep errors.. I mean I dunno why you are getting them.. it's a access denied type error.

---

### Post by GabrielWolff on 2006-02-01
[QUOTE=majikstreet]Yeah, I did make the beep errors.. I mean I dunno why you are getting them.. it's a access denied type error.[/QUOTE]

And who would get those messages? Who's denied access? Certain IPs?
I mean: I didn't type in no pass or user when trying to *access* the files, and some of them *did* open. So you don't need no permission to access any files on that page.

Or am I getting it all wrong?

G

---

### Post by majikstreet on 2006-02-01
nvm.
hold on I will try something..

I just changed permissions (chmod) on the files... it should work now!

---

### Post by GabrielWolff on 2006-02-02
OK, this worked, thank you :-)
Next question (should be easy ;-))
I want the whole filenames to be displayed. If you look at the page, only the first half of the names are visible.
Can I change that?

G

---

### Post by majikstreet on 2006-02-02
I dunno...

---

### Post by imagine on 2006-02-02
Have a look at the IndexOptions NameWidth setting.

[http://www.debian-administration.org/articles/195](http://www.debian-administration.org/articles/195)



Of course there are like lots of different ways to change directory listings.

---

