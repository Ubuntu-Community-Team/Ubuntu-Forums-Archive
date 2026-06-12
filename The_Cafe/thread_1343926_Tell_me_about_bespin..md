---
title: "Tell me about bespin."
date: 2009-12-02
forum: The Cafe
---

### Post by Cam42 on 2009-12-02
What is it?
Why would I want it?
How do I get it?

---

### Post by scottuss on 2009-12-02
> **Cam42 said:**
> What is it?
Why would I want it?
How do I get it?

Is this some kind of weird troll?

---

### Post by RiceMonster on 2009-12-02
1) A Qt theme
2) You would want it if you think it looks good, you use KDE, and because you can customize it to make it look as you like
3) [http://kde-look.org/content/show.php/Bespin?content=63928](http://kde-look.org/content/show.php/Bespin?content=63928). Follow the download link to get the svn sources

> **scottuss said:**
> Is this some kind of weird troll?

No. Not everyone is a troll.

---

### Post by Dougie187 on 2009-12-02
Lol, I first thought he was talking about the famous cloud city planet...

Second I thought he was talking about this. [https://mozillalabs.com/bespin/](https://mozillalabs.com/bespin/)

And then after I read the rest of the thread it seems other people thought something completely different.

---

### Post by Cam42 on 2009-12-02
> Lol, I first thought he was talking about the famous cloud city planet...
I was waiting for someone to say that. :D


No, I'm not a troll. Asking a few questions, and I was trying to get them asked before I had to restart Firefox.

---

### Post by scottuss on 2009-12-02
> **RiceMonster said:**
> 1) A Qt theme
2) You would want it if you think it looks good, you use KDE, and because you can customize it to make it look as you like
3) [http://kde-look.org/content/show.php/Bespin?content=63928](http://kde-look.org/content/show.php/Bespin?content=63928). Follow the download link to get the svn sources



No. Not everyone is a troll.

I'm confused.

---

### Post by scottuss on 2009-12-02
> **Cam42 said:**
> I was waiting for someone to say that. :D


No, I'm not a troll. Asking a few questions, and I was trying to get them asked before I had to restart Firefox.

I don't mean to be rude, your post just read very oddly.

It seemed like you couldn't be bothered to Google it, that's all.

---

### Post by Skripka on 2009-12-02
> **scottuss said:**
> I'm confused.

Drink more coffee.

---

### Post by RiceMonster on 2009-12-02
> **scottuss said:**
> I don't mean to be rude, your post just read very oddly.

It seemed like you couldn't be bothered to Google it, that's all.

That's not a valid reason in the slightest to consider the OP a troll.

---

### Post by scottuss on 2009-12-02
> **Skripka said:**
> Drink more coffee.

Good idea! :)

---

### Post by Cam42 on 2009-12-02
> **scottuss said:**
> I don't mean to be rude, your post just read very oddly.

It seemed like you couldn't be bothered to Google it, that's all.
Did Google it, I was still quite tired when I read the info Google gave me, and was hoping someone could explain it better.

---

### Post by scottuss on 2009-12-02
Edit: Just read above post, made mine defunct.

OK, fair point. Let's leave this alone now eh? :)

Coffee all round!? :)

---

### Post by Tibuda on 2009-12-02
It is a gas planet. They have made a city in the clouds there.
[img]http://venturalandcorp.com/bespin.jpg[/img]

---

### Post by Excedio on 2009-12-02
> **Cam42 said:**
> Did Google it, I was still quite tired when I read the info Google gave me, and was hoping someone could explain it better.
 
What bespin are you talking about?
 
Bespin - KDE Theme
Bespin - Mozilla Labs
Bespin - The Planet

---

### Post by Cam42 on 2009-12-02
KDE. Again, Firefox was 'bout to restart.

---

### Post by Cam42 on 2009-12-02
> **scottuss said:**
> Edit: Just read above post, made mine defunct.

OK, fair point. Let's leave this alone now eh? :)

Coffee all round!? :)
Yes. *gives coffee*

---

### Post by Excedio on 2009-12-02
> **Cam42 said:**
> KDE. Again, Firefox was 'bout to restart.
 
Then I assume RiceMonster has solved the riddle.
 
/thread

---

### Post by doas777 on 2009-12-02
> **Dougie187 said:**
> Lol, I first thought he was talking about the famous cloud city planet...

my first thought was the same. oh Lando Calrissian, what hath thou wrought!

---

### Post by Cam42 on 2009-12-02
It doesn't seem to like openSUSE. Help?

---

### Post by LinuxFanBoi on 2009-12-02
One cool thing came of this thread,  I learned about lmgtfy.com, so I can be a sarcastic *** to people who come to a forum to ask questions they should have Googled first!:D

---

### Post by RiceMonster on 2009-12-02
> **Cam42 said:**
> It doesn't seem to like openSUSE. Help?

Provide more information

---

### Post by Cam42 on 2009-12-02
> **RiceMonster said:**
> Provide more information
I open up Konsole, it first tells me that access is denied to ./configure (in the cloudcity folder), and then it tells me that make/make install are invalid commands.
EDIT: I should probably run Konsole in super user mode, right?

---

### Post by Cam42 on 2009-12-02
Oh, and I had to download the tarball, instead of going the svn route, Konsole told me that svn was not installed.

---

### Post by RiceMonster on 2009-12-02
> **Cam42 said:**
> I open up Konsole, it first tells me that access is denied to ./configure (in the cloudcity folder), and then it tells me that make/make install are invalid commands.
EDIT: I should probably run Konsole in super user mode, right?

No, you should only run make install as root. did you run svn as root to get the source? Don't do that; get the source as a normal user somewhere in your home folder. You can probably fix the problem as is by doing
```
chown -R user_name /path/to/source/dir/
```

Also, it says make and make install are not commands because you don't have make installed. I don't know what the package would be called, or if there's some build tools group package you can install in OpenSuSE. You're probably going to have to install gcc and g++ as well.

> **Cam42 said:**
> Oh, and I had to download the tarball, instead of going the svn route, Konsole told me that svn was not installed.

Install it then. It's probably called subversion or something like that.

---

### Post by Excedio on 2009-12-02
> **LinuxFanBoi said:**
> One cool thing came of this thread, I learned about lmgtfy.com, so I can be a sarcastic *** to people who come to a forum to ask questions they should have Googled first!:D
 
Careful using that. I just got a Mod Warning for it. :|

---

