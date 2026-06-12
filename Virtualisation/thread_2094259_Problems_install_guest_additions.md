---
title: "Problems install guest additions"
date: 2012-12-13
forum: Virtualisation
---

### Post by rmcellig on 2012-12-13
I have never had so many problems installing Guest Additions in Linux. I'm sure I am doing something wrong.

I am using Virtualbox 4.1.18.

As you can see from the attached I am able to see the Guest Additions CD but am unsure where to go from here.

Really appreciate the help!

---

### Post by haqking on 2012-12-13
> **rmcellig said:**
> I have never had so many problems installing Guest Additions in Linux. I'm sure I am doing something wrong.

I am using Virtualbox 4.1.18.

As you can see from the attached I am able to see the Guest Additions CD but am unsure where to go from here.

Really appreciate the help!

command line, change to the virtual CD and then run

```
sudo sh VBxxxxxxxx.run
```

---

### Post by rmcellig on 2012-12-13
I tried that and this is what I get. See attached. This seems so straight forward to do but for some reason it is not working for me.

---

### Post by haqking on 2012-12-13
> **rmcellig said:**
> I tried that and this is what I get. See attached. This seems so straight forward to do but for some reason it is not working for me.

run the correct file ;-)
```

sudo sh VBoxLinuxAdditions.run
```

you are trying to run the name of the CD

---

### Post by rmcellig on 2012-12-13
OK. When I look at the contents of the CD, I see a file called VBoxLinux Additions.run. Is this not the file you are asking me to use? As you can tell from the Terminal screenshot, this is the file that I tried as you mentioned in your post (sudo sh VBoxLinuxAdditions.run).

If I am totally off base here please let me know but I think I am using the right file. :) Here is what I see when I view the contents of the CD.

---

### Post by haqking on 2012-12-13
> **rmcellig said:**
> OK. When I look at the contents of the CD, I see a file called VBoxLinux Additions.run. Is this not the file you are asking me to use? As you can tell from the Terminal screenshot, this is the file that I tried as you mentioned in your post (sudo sh VBoxLinuxAdditions.run).

If I am totally off base here please let me know but I think I am using the right file. :) Here is what I see when I view the contents of the CD.

according to your terminal output you changed to the CD, correct.

You listed the contents, correct.

You then typed sudo sh <name of the cd> incorrect

you are supposed to type ```
sudo sh VBoxLinuxAdditions.run
```at no time in your terminal output did you type that.

---

### Post by rmcellig on 2012-12-13
You're right. I thought I typed sudo sh VBoxLinuxAdditions.run. I will try it again and see what happens.

Embarassed!

---

### Post by haqking on 2012-12-13
> **rmcellig said:**
> You're right. I thought I typed sudo sh VBoxLinuxAdditions.run. I will try it again and see what happens.

Embarassed!

No problem, I do it all the time, I try not to make it public though LOL ;-)

Remember to use tab complete to make sure you get the name correct, though this can often assure you get it incorrect aswell

If it works, remember to mark the thread as solved.

Peace

---

### Post by rmcellig on 2012-12-13
I do use tab complete. This time it worked!! I came across a couple of errors so I installed the Make and Gcc utilities. Worked fine after that.

After all of this, I have to say that I feel really good because I am a newbie to Linux and I figured it out!! (Except for all the stuff at the begining) :). Next time I will try and keep my mistakes out of the public :)..

Thanks for your patience!

---

### Post by haqking on 2012-12-13
> **rmcellig said:**
> I do use tab complete. This time it worked!! I came across a couple of errors so I installed the Make and Gcc utilities. Worked fine after that.

After all of this, I have to say that I feel really good because I am a newbie to Linux and I figured it out!! (Except for all the stuff at the begining) :). Next time I will try and keep my mistakes out of the public :)..

Thanks for your patience!


NO problem you are welcome.

As a newbie, read my signature....LOL

Peace

---

### Post by rmcellig on 2012-12-13
:)

---

