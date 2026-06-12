---
title: "request: Wesnoth 0.9.0"
date: 2005-04-11
forum: Ubuntu Backports
---

### Post by Corey on 2005-04-11
Wesnoth 0.9.0 is out! Wesnoth is my favorite game and has been since aroun 0.6. Wesnoth 0.9.0 is a huge step forward. Lots of new grahics, balance, and multiplayer code.

---

### Post by cdhotfire on 2005-04-11
[http://people.debian.org/~isaac/wesnoth/](http://people.debian.org/~isaac/wesnoth/)

u can get it there if ud like.:razz:

o and thanks for telling me about this new update, i couldnt wait.;-)

---

### Post by sethmahoney on 2005-04-11
[QUOTE=cdhotfire][http://people.debian.org/~isaac/wesnoth/](http://people.debian.org/~isaac/wesnoth/)

u can get it there if ud like.:razz:

o and thanks for telling me about this new update, i couldnt wait.;-)[/QUOTE]
 Any idea what I can do about the following requirement?  I'm guessing there's some repository somewhere that can fulfill it, but I've got no idea where to look.

  libsdl-mixer1.2 (>=1.2.6)

---

### Post by cdhotfire on 2005-04-12
[http://packages.debian.org/unstable/libs/libsdl-mixer1.2]("http://packages.debian.org/unstable/libs/libsdl-mixer1.2"):p

---

### Post by jdong on 2005-04-12
Guys, cool down and wait for the backport.

The least wise thing you'd want to do is to mix Debian and Ubuntu libraries ;)

---

### Post by Raven-sb on 2005-04-12
[QUOTE=jdong]Guys, cool down and wait for the backport.

The least wise thing you'd want to do is to mix Debian and Ubuntu libraries ;)[/QUOTE]

*smiles and puts on best little kiddy voice* but I want to play nowwwwwwwwwwwww (j/k):-\"

Seriously I'm prepared to wait for the backport of wesnoth, but I'm curious as to how long it will take to for the backport to be added. 

Warmest Regards,

Raven

---

### Post by jdong on 2005-04-14
[https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114395&group_id=125877&group_project_id=42440](https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114395&group_id=125877&group_project_id=42440)

Ok, your request has been accepted and is currently being satisfied. Subscribe/check the task above to monitor its progress.

---

### Post by humanity_to_others on 2005-04-15
sudo gedit /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted universe multiverse

sudo apt-get install wesnoth wesnoth-music wesnoth-ei wesnoth-sotbe wesnoth-tdh wesnoth-trow

---

### Post by jdong on 2005-04-15
Ok, Wesnoth fully packaged and uploaded into the Staging area.

---

### Post by poofyhairguy on 2005-04-15
[QUOTE=jdong]Ok, Wesnoth fully packaged and uploaded into the Staging area.[/QUOTE]


I tried it and it was real buggy for me. But I must have done something wrong (or I didn't do enough) because it was REALLY buggy. Unplayable.

EDIT: I'm more sure it was a mistake of mine. It seems to be a video card issue.

---

### Post by oracledarren on 2005-04-15
[QUOTE=jdong]Ok, Wesnoth fully packaged and uploaded into the Staging area.[/QUOTE]

Maybe a silly question but what is the staging area and how do i get to it ?

---

### Post by jdong on 2005-04-15
This is around the 5th time this week this question is asked.

Please search this forum for "hoary-backports-staging", or go to [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

I'm not trying to be mean; it's just that I don't like repeating myself too many times!

---

### Post by jdong on 2005-04-15
[QUOTE=poofyhairguy]I tried it and it was real buggy for me. But I must have done something wrong (or I didn't do enough) because it was REALLY buggy. Unplayable.

EDIT: I'm more sure it was a mistake of mine. It seems to be a video card issue.[/QUOTE]

Well, the last wesnoth backport crashed GNOME (?), so I wouldn't be surprised with stability issues. However, I just installed this one, and it works fine on my GeForce4 MX440.

---

### Post by Raven-sb on 2005-04-16
I also have installed mine and it works perfectly with my Nvidia 5800fx card.

Thanks jdong for gettings this to the backport so promptly.:)

---

### Post by humanity_to_others on 2005-04-16
It is nicer than 0.8

[[img]http://xs24.xs.to/pics/05156/wesnoth09.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs24&d=05156&f=wesnoth09.png)

---

### Post by fromoze on 2005-04-16
And there're some news about amd64 version? I'm looking on Breezy. Wesnoth 0.9 is there, but not all the dependecyes :( there're problems with sound :'(

Will it be backported when it works on breezy?

---

### Post by jdong on 2005-04-16
Currently, I only package for i386. This may change in the future...

---

### Post by Spif on 2005-04-17
I added Backports to my sources.list as described on Ubuntuguide.org, but Wesnoth 0.9.0 is not available from Synaptic. What am I doing wrong?

---

### Post by panabar on 2005-04-17
[QUOTE=Spif]I added Backports to my sources.list as described on Ubuntuguide.org, but Wesnoth 0.9.0 is not available from Synaptic. What am I doing wrong?[/QUOTE]

Have you added the staging area ? To add it open synaptic, then settings->repositories and click add button then click the Custom button.

the source line is :

```

deb http://backports.ubuntuforums.org/backports hoary-backports-staging main universe multiverse restricted

```

you should also check
Backports Page...

---

### Post by Spif on 2005-04-17
Thanks! :grin:

---

### Post by jordanau on 2005-04-17
thank you!

---

### Post by jdong on 2005-04-17
Ok, I'm ready to mark this one stable :)

---

