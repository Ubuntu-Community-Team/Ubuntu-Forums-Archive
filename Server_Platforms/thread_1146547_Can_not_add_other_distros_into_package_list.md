---
title: "Can not add other distros into package list"
date: 2009-05-02
forum: Server Platforms
---

### Post by jaunty09 on 2009-05-02
Using Server version.  I am trying to add Xubuntu into the apt-get package list.

"sudo apt-cdrom add"

Checked /etc/apt/sources.list to see if it is added, and it is.

"sudo apt-get update"

Tried to "sudo apt-get install" something off the disc and it does not work.  I am positive the package is in the disc.

Is there something I missed?

---

### Post by cariboo on 2009-05-02
Ae you trying to add the Xubuntu cdrom to sources.list? Otherwise youy aren't going to get the XUbuntu desktop.

---

### Post by jaunty09 on 2009-05-02
> Ae you trying to add the Xubuntu cdrom to sources.list? What was the point of asking something that has been stated?  > Otherwise youy aren't going to get the XUbuntu desktop.  I never mentioned I wanted XFCE.  I just want the packages in the Xubuntu disc added to the repository.

---

### Post by wirelessmonkey on 2009-05-02
> **jaunty09 said:**
> What was the point of asking something that has been stated?   I never mentioned I wanted XFCE.  I just want the packages in the Xubuntu disc added to the repository.

I don't know the answer, since I do all my updating online, but...

Be nice, he was just trying to clarify what you were doing, so he could best help you.



Best of Luck

---

### Post by jaunty09 on 2009-05-03
> I don't know the answer This is a support forum...  > Be nice, he was just trying to clarify what you were doing, so he could best help you. Jesus Christ!  You got to be kidding me.  How much clearer can it be?  In the original post, line 1 and 3 have stated that I was and have added it to sources.list.  And then cariboo907 asks if I am trying to do that?  Which part of that was so confusing?  The topic was about how I can get the packages in the Xubuntu disc added to the repository.  cariboo907 then thinks that I was trying to install XFCE.  I never mentioned anything about XFCE.  Not sure if English is his/her first language or not.  But what I said was nowhere near complicated to understand.

---

### Post by gombadi on 2009-05-03
> **jaunty09 said:**
> This is a support forum...  

That is correct.

This is a support forum where people like myself offer there support for free to help others to use and learn about Ubuntu.

We are under on obligation to help people we do not wish to.

Thank you
Good Bye.

---

### Post by jaunty09 on 2009-05-03
> That is correct.
Good that you recognize.

> This is a support forum where people like myself offer there support for free to help others to use and learn about Ubuntu.
Good declaration.  However, this post of yours is not helping.  Neither was the previous 2.

> We are under on obligation to help people we do not wish to.
Then you should not have replied at all.

> Thank you
Good Bye.
gombadi, your post is purely useless.  It served absolutely no purpose other than to show off.  If you do not wish to help, fine.  But did you need to add another spam to the topic?  There is already 1 person practicing English.  Another 1 chatting.  Now you showing off.

---

### Post by gombadi on 2009-05-03
> **jaunty09 said:**
> 
Tried to "sudo apt-get install" something off the disc and it does not work.  I am positive the package is in the disc.


If you are wanting people to help then may I suggest you provide more information.

"it does not work"

"it does not work" - because it gives an error message saying...
"it does not work" - the CD does not even spin up to find the package.
"it does not work" - it says syntax error in sources.lst
"it does not work" - for some other reason we have not been told about.

What do you mean by "it does not work"?



> **jaunty09 said:**
> 
Is there something I missed?

Yes - You will get a lot more help by being nice to others.

---

### Post by overdrank on 2009-05-03
I would like to remind users of the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")
> Be respectful of all users at all times. This means please use etiquette and politeness. Treat people with kindness and gentleness. If you do this the rest of the code of conduct won't need more than a cursory mention.

As for the issue at hand I believe the use of the alternate cd is in need.

---

### Post by jaunty09 on 2009-05-03
> because it gives an error message saying...
```
no such package but referred to by another
```
> Yes - You will get a lot more help by being nice to others.
I was fine.  Until cariboo907 choose to irritate me with bad English.

---

### Post by gombadi on 2009-05-03
Good we are making some progress. I will ignore the second quote. Someone recently told me that if a comment does not help with the problem then it should not be made - or something to that effect :-)

Now can you provide even more information - yes I know it is a pain but the more information we have the better we can help you.

Can you post your /etc/apt/sources.lst file and the command you are entering so we can see that packages you are trying to install. I am interested to know what xubuntu package you are trying to install that is not already part of ubuntu.

With that information someone reading may go "oh I had problems with that package and fixed it by doing..."

---

### Post by koenn on 2009-05-03
> **jaunty09 said:**
> ```
no such package but referred to by another
```

apt can't find the package you're trying to install.

post your /etc/apt/sources.lst file and the command you are entering so we can see what packages we're talkinh about.

---

