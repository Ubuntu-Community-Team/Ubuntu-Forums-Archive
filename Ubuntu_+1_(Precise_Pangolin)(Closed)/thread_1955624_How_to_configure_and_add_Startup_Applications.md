---
title: "How to configure and add Startup Applications?"
date: 2012-04-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by emarkay on 2012-04-09
I want to add Conky, and BOINC. 
Where is this now in 12.04?

---

### Post by alphacrucis2 on 2012-04-09
> **emarkay said:**
> I want to add Conky, and BOINC. 
Where is this now in 12.04?

In the repos. Enable universe for both.

Edit. Whoops. I read what you were asking again. Click the cog at the upper right. You will see startup applications there.

You know you could easily find a lot of this stuff yourself with a quick search.

---

### Post by emarkay on 2012-04-09
Did search, found: 
[http://ubuntuforums.org/showthread.php?t=1909157](http://ubuntuforums.org/showthread.php?t=1909157)
[http://ubuntuforums.org/showthread.php?t=1919301](http://ubuntuforums.org/showthread.php?t=1919301)

Nothing specifically shows how to do this graphically in a basic, initial 12.04 installation.

Now, yes this does allow you to ADD as I requested. but what about he default programs ALREADY started; where/how to disable them?

---

### Post by cariboo on 2012-04-09
When you go to System Settings->Startup Applications, how to add items at startup is pretty self-evident, see the screenshot

---

### Post by emarkay on 2012-04-09
I see that, but this is what I have; a pink box.
Where are the "Syatem" startups?  Printing, update, bluetooth, security programs, etc.?

---

### Post by cariboo on 2012-04-09
What happens when you click the add button?

---

### Post by mc4man on 2012-04-10
> **emarkay said:**
> I see that, but this is what I have; a pink box.
Where are the "Syatem" startups?  Printing, update, bluetooth, security programs, etc.?

Answers to most of your recent questions are in previous pages of this subforum or elsewhere in the forum
As far as default Startup apps, most are hidden, one of a dozen or so threads
[http://ubuntuforums.org/showthread.php?t=1919301](http://ubuntuforums.org/showthread.php?t=1919301)

For convenience I use a google site search bookmarklet, like available here
[http://www.imilly.com/bm.htm](http://www.imilly.com/bm.htm)

---

### Post by keithpeter on 2012-04-10
Hello All

[http://ubuntuforums.org/showpost.php?p=11659810&postcount=5](http://ubuntuforums.org/showpost.php?p=11659810&postcount=5)

I chose to just edit the one desktop file relating to bluetooth in Unity.

@cariboo907

[http://ubuntuforums.org/showpost.php?p=11660004&postcount=6](http://ubuntuforums.org/showpost.php?p=11660004&postcount=6)

A dump of that Zim file would come in handy when the 12.04 multitudes start asking these questions :twisted:

---

### Post by jerrylamos on 2012-04-10
I looked at the "gear" and selected Startup Applications>Add

Every time I boot (a lot) on this Acer Aspire 5253 Pangolin comes up in FULL BRIGHT! BANG!  So I go off into Brightness and Lock, change it to about 33%.  Boot up again, FULL BRIGHT! BANG!

Failing ubuntu capability to "remember settings" I couldn't see any way to at least start "Brightness and Lock" when I boot.  Couldn't even see how to put it on the launcher.

An ankle biter.

Any clues anyone?

Thanks, Jerry

---

### Post by cariboo on 2012-04-10
> **keithpeter said:**
> Hello All

[http://ubuntuforums.org/showpost.php?p=11659810&postcount=5](http://ubuntuforums.org/showpost.php?p=11659810&postcount=5)

I chose to just edit the one desktop file relating to bluetooth in Unity.

@cariboo907

[http://ubuntuforums.org/showpost.php?p=11660004&postcount=6](http://ubuntuforums.org/showpost.php?p=11660004&postcount=6)

A dump of that Zim file would come in handy when the 12.04 multitudes start asking these questions :twisted:

Up until this point, I hadn't restored my Notes directory, since the last fresh install. Here is the command:

```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

---

