---
title: "Firefox 4 And Dark Themes Fix"
date: 2011-03-26
forum: Tutorials
---

### Post by bagy on 2011-03-26
This fix dark text boxes

1. Create "chrome" folder in ~/.mozilla/firefox/yourprofile/

```
cd ~/.mozilla/firefox/yourprofile/
``````
mkdir chrome
```   ```
cd chrome
```2. Create "userContent.css" file:
```
gedit userContent.css
```
You can replace gedit with your text editor.

Paste this and save:

```
input {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

textarea {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

select {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

input[type="radio"],
input[type="checkbox"] {
border: 2px inset white ! important;
background-color: white ! important;
color: ThreeDFace ! important;
-moz-appearance: none !important;
}

*|*::-moz-radio {
background-color: white;
-moz-appearance: none !important;
}

button,
input[type="reset"],
input[type="button"],
input[type="submit"] {
border: 2px outset white;
background-color: #eeeeee;
color: black;
-moz-appearance: none !important;
}

body {
background-color: white;
color: black;
display: block;
margin: 8px;
-moz-appearance: none !important;
}
```Restart firefox. :)

---

### Post by Henns Wörst on 2011-03-27
Thank you for sharing!  ):P

---

### Post by Dngrsone on 2011-03-31
... oops, wrong thread.

---

### Post by keplenk on 2011-04-02
Thanks for the tip.

I just have a quick question before I do anything.

When I go to  ~/.mozilla/firefox/

I don't have any other folder after that.  The contents of my  ~/.mozilla/firefox/   are two files named:

"ffkmaa8o.default" and "profiles.ini" -- no folders

Are you saying that I should create a "yourprofile" folder - naming it with what I want?

Thanks!

---

### Post by wojox on 2011-04-02
ffkmaa8o.default should be a folder.

---

### Post by bent12 on 2011-04-02
great post, thanks for shearing

---

### Post by bagy on 2011-04-02
> **keplenk said:**
> Thanks for the tip.

I just have a quick question before I do anything.

When I go to  ~/.mozilla/firefox/

I don't have any other folder after that.  The contents of my  ~/.mozilla/firefox/   are two files named:

"ffkmaa8o.default" and "profiles.ini" -- no folders

Are you saying that I should create a "yourprofile" folder - naming it with what I want?

Thanks!
ffkmaa8o.default is "yourprofile" folder...

---

### Post by keplenk on 2011-04-02
> **bagy said:**
> ffkmaa8o.default is "yourprofile" folder...

You're right .. my bad ... i thought it was a file and not a folder.

Sorry.  Thanks for your reply.

---

### Post by MysteryMetal on 2011-04-07
This fix is exactly what I was looking for

Thank you!!

---

### Post by Henns Wörst on 2011-04-14
The only flaw ist, that the bullets and checkmarks are still white though, I tried to play a litte with colors, but I did not achieve anything. Is this a problem just I happen to have?

---

### Post by ChrisEiffel on 2011-08-01
Check Marks and Radio Buttons still have a black background. I can't easily find a css fix.

---

### Post by ajaykumarb on 2011-08-08
It is very helpful tip.I was looking for a long time for this .

Thanks a lot for sharing

---

### Post by jutt69 on 2011-08-24
Confirmed working on FF6.

Thank you very much, was really bugging me!

---

### Post by atarixle on 2012-08-14
is there any chance to fix this in Opera too?

---

### Post by uRock on 2012-08-14
Old thread. Please start a new thread on this topic.

Thread Closed

---

