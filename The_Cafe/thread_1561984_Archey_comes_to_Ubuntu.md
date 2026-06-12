---
title: "Archey comes to Ubuntu"
date: 2010-08-27
forum: The Cafe
---

### Post by Dj Melik on 2010-08-27
I originally wrote Archey for Arch Linux, I'm sure most of you have  ran into that popular little command line tool that displays basic system information and the Arch Linux logo in many Arch Linux screenshots.

Just recently, I decided to add support for Debian and Ubuntu. 

Archey is written in Python, and depends on lsb-release and scrot. 

Here is a screenshot of Archey:
[http://omploader.org/vNWNxNw/2010-08-26-183003_1920x1080_scrot.png](http://omploader.org/vNWNxNw/2010-08-26-183003_1920x1080_scrot.png)

You can find a .deb package on Archey's official Github page.
[http://github.com/djmelik/archey/downloads](http://github.com/djmelik/archey/downloads)

---

### Post by HappinessNow on 2010-08-27
> **Dj Melik said:**
> I originally wrote Archey for Arch Linux, I'm sure most of you have  ran into that popular little command line tool that displays basic system information and the Arch Linux logo in many Arch Linux screenshots.

Just recently, I decided to add support for Debian and Ubuntu. 

Archey is written in Python, and depends on lsb-release and scrot. 

Here is a screenshot of Archey:
[http://omploader.org/vNWNxNw/2010-08-26-183003_1920x1080_scrot.png](http://omploader.org/vNWNxNw/2010-08-26-183003_1920x1080_scrot.png)

You can find a .deb package on Archey's official Github page.
[http://github.com/djmelik/archey/downloads](http://github.com/djmelik/archey/downloads)Cool...but upon quickly scanning the forums I at first thought your post read:

Anarchy comes to Ubuntu

:p

---

### Post by Kdar on 2010-08-27
Cool. Thanks!

---

### Post by Dj Melik on 2010-08-27
> **HappinessNow said:**
> Cool...but upon quickly scanning the forums I at first thought your post read:

Anarchy comes to Ubuntu

:p
Haha :P 

Are you guys running into any bugs or is everything running along smoothly?

---

### Post by drawkcab on 2010-08-27
nice, thanks!

---

### Post by richs-lxh on 2010-08-27
Nice, I used Archey when I ran Arch. I just installed it on Ubuntu and Debian..... any chance of a Crunchbang Statler (Debian based) version?

I just added it to Ubuntu, Debian and Crunchbang. Would love a Crunchbang logo though :)

---

### Post by Dj Melik on 2010-08-27
> **richs-lxh said:**
> Nice, I used Archey when I ran Arch. I just installed it on Ubuntu and Debian..... any chance of a Crunchbang Statler (Debian based) version?

I just added it to Ubuntu, Debian and Crunchbang. Would love a Crunchbang logo though :)
Yes, of course :)

All popular distros will soon be supported by archey.

---

### Post by Spice Weasel on 2010-08-27
Doing ASCII art for all major distros logos sounds painful. I wish you good luck sir! :D

Especially with the OpenSUSE logo...

---

### Post by richs-lxh on 2010-08-27
> **Dj Melik said:**
> Yes, of course :)

All popular distros will soon be supported by archey.

Great news, i'll see you on #! forums when you have it sorted.

PS: Good luck with the Xubuntu logo, that little mouse is going to be a killer in ascii :)

---

### Post by KdotJ on 2010-08-27
Very nice... Well done sir lol

---

### Post by Shpongle on 2010-08-27
cool , thanks for sharing

---

### Post by Dj Melik on 2010-08-27
> **richs-lxh said:**
> Great news, i'll see you on #! forums when you have it sorted.

PS: Good luck with the Xubuntu logo, that little mouse is going to be a killer in ascii :)

I just ported archey to Crunchbang and Fedora. Feel free to grab it from the Git, i'll update the .deb package later today.

edit: .deb and .rpm for archey 0.2.6 can now be found in the downloads page.

---

### Post by gutterslob on 2010-08-28
Installed the new version after reading a thread (that richs-lxh started) the #! forums. 
Totally pointless, but still pretty fun to look at, I guess. Will probably install it on my Arch system later as well.

Thanks for sharing :)

Here's a screenie;
I run #! Openbox, but it listed my DE as Xfce (probably because I have Thunar and xfconfd), so I made a slight change to your script. 
Hope you don't mind :P

[[IMG]http://omploader.org/tNWRnMQ[/IMG]]("http://omploader.org/vNWRnMQ")

---

### Post by Dj Melik on 2010-08-29
> **gutterslob said:**
> Installed the new version after reading a thread (that richs-lxh started) the #! forums. 
Totally pointless, but still pretty fun to look at, I guess. Will probably install it on my Arch system later as well.

Thanks for sharing :)

Here's a screenie;
I run #! Openbox, but it listed my DE as Xfce (probably because I have Thunar and xfconfd), so I made a slight change to your script. 
Hope you don't mind :P

[[IMG]http://omploader.org/tNWRnMQ[/IMG]]("http://omploader.org/vNWRnMQ")
Haha :P

Yeah if xfconfd is detected, then archey will assume your desktop enviornment is Xfce.

---

### Post by cra1g321 on 2010-08-30
hey noticed you added linux mint into archey. Thanks :D
i wouldnt mind learning to code, so il maybe use archey for fiddling around with code

Changed the colours a bit 

[[img]http://omploader.org/tNWU2NQ[/img]](http://omploader.org/vNWU2NQ)

---

### Post by renkinjutsu on 2010-08-30
> **gutterslob said:**
> Installed the new version after reading a thread (that richs-lxh started) the #! forums. 
Totally pointless, but still pretty fun to look at, I guess. Will probably install it on my Arch system later as well.

Thanks for sharing :)

Here's a screenie;
I run #! Openbox, but it listed my DE as Xfce (probably because I have Thunar and xfconfd), so I made a slight change to your script. 
Hope you don't mind :P

[[IMG]http://omploader.org/tNWRnMQ[/IMG]]("http://omploader.org/vNWRnMQ")

Your Terminal is awesome.. How did you get your prompt (PS1) to look like that?

---

### Post by gutterslob on 2010-09-01
> **renkinjutsu said:**
> Your Terminal is awesome.. How did you get your prompt (PS1) to look like that?

Pretty simple stuff, really

```
PS1="&#9484;&#9472;[\d][\u@\h:\w]\n&#9492;&#9472;> "
```

---

### Post by llawwehttam on 2010-09-01
thanks mate.

---

### Post by NCLI on 2010-09-01
Neat little application!

Are you going to try to get it into the repos? That would be very nice.

---

### Post by Dj Melik on 2010-09-02
> **NCLI said:**
> Neat little application!

Are you going to try to get it into the repos? That would be very nice.
If an ubuntu dev wants to create an official package and maintain, that'd be nice. But I don't think I will. So go ahead and suggest it to devs if you want it.

---

### Post by v1ad on 2010-09-02
tx works great

---

### Post by Dj Melik on 2010-09-08
You're welcome everyone :]

---

### Post by Dj Melik on 2010-10-06
Did lots of work on archey and re-packaged it. If anyone uses archey, I'd suggest you upgrade to the new version.

Archey 0.2.8.deb upoloaded to Github.

[http://github.com/djmelik/archey/downloads](http://github.com/djmelik/archey/downloads)

---

### Post by maxfact on 2010-10-26
I have a little problem, when archey on terminal have this error
```
beowulf@beowulf:~$ archey -s
Traceback (most recent call last):
  File "/usr/bin/archey", line 304, in <module>
    func()
  File "/usr/bin/archey", line 288, in disk_display
    usedpercent = float(re.sub("[A-Z]", "", used)) / float(re.sub("[A-Z]", "", size)) * 100
ValueError: invalid literal for float(): 7,5

```
I use ubuntu maverick with archey 0.2.8

---

### Post by Glenn nl on 2010-10-26
> **maxfact said:**
> I have a little problem, when archey on terminal have this error
```
beowulf@beowulf:~$ archey -s
Traceback (most recent call last):
  File "/usr/bin/archey", line 304, in <module>
    func()
  File "/usr/bin/archey", line 288, in disk_display
    usedpercent = float(re.sub("[A-Z]", "", used)) / float(re.sub("[A-Z]", "", size)) * 100
ValueError: invalid literal for float(): 7,5

```
I use ubuntu maverick with archey 0.2.8

Same :(

---

### Post by alexan on 2010-10-26
> **HappinessNow said:**
> Cool...but upon quickly scanning the forums I at first thought your post read:

Anarchy comes to Ubuntu

:p

Here the same, I was worried for the health of our SABDFL's Mark :(

---

### Post by Spice Weasel on 2010-10-26
[[IMG]http://imgur.com/nupfEl.jpg[/IMG]]("http://imgur.com/nupfE.png")

Thanks! Works great. :)

---

### Post by Dj Melik on 2010-11-07
> **maxfact said:**
> I have a little problem, when archey on terminal have this error
```
beowulf@beowulf:~$ archey -s
Traceback (most recent call last):
  File "/usr/bin/archey", line 304, in <module>
    func()
  File "/usr/bin/archey", line 288, in disk_display
    usedpercent = float(re.sub("[A-Z]", "", used)) / float(re.sub("[A-Z]", "", size)) * 100
ValueError: invalid literal for float(): 7,5

```
I use ubuntu maverick with archey 0.2.8
Yeah, I'm getting ready to rewrite Archey in python3. This whole python2>3 transition has really caused archey to break over all distros.

---

