---
title: "Launchpad PPA help and a call for volunteers!"
date: 2010-06-24
forum: The Cafe
---

### Post by tom.swartz07 on 2010-06-24
Hi all,

I have a small project hosted on Launchpad that I am working on, and I was wondering how to create a PPA for it. 

There are a small handful of us from the forums here that are involved with the project, and between us, we cannot for the life of us figure out how to get our code into a PPA.




Also, (shameless self plug)
We are still looking for people that are interested in helping with our project. You could join our Dev group here: [https://edge.launchpad.net/~codemonkeydevs](https://edge.launchpad.net/~codemonkeydevs) 
The project is hosted here: [https://edge.launchpad.net/codemonkey](https://edge.launchpad.net/codemonkey)

Thanks for the help!

---

### Post by madjr on 2010-06-24
i think these posts could help or request help here (directly from the community manager):
[http://www.jonobacon.org/2010/05/21/why-launchpad-rocks-just-enough-goodness-for-my-project/](http://www.jonobacon.org/2010/05/21/why-launchpad-rocks-just-enough-goodness-for-my-project/)

good luck on your project it looks interesting and useful

---

### Post by Legendary_Bibo on 2010-06-24
I could help, but I only know how to make launchers with terminal commands. I haven't fully learned python yet.

Also I looked at some of the ones you guys made, and I have a question about the bing wallpaper downloader script. Will this give me automatically transitioning wallpapers like what Windows 7 has? I always liked that feature but could never figure out how to do it on Ubuntu.

---

### Post by tom.swartz07 on 2010-06-24
> **Legendary_Bibo said:**
> I could help, but I only know how to make launchers with terminal commands. I haven't fully learned python yet.

Also I looked at some of the ones you guys made, and I have a question about the bing wallpaper downloader script. Will this give me automatically transitioning wallpapers like what Windows 7 has? I always liked that feature but could never figure out how to do it on Ubuntu.

Thats perfectly fine! I wasn't too spectacular when I first started either. Personally, I would love to have you join the team, we could always use an extra hand on the bug reports and managing new ideas (YOURE WAY AHEAD ON THAT ALREADY!) 


*That actually is a neat idea to put in for our next major update to that program! Would you like to join and help advise the progress of this?*

Technically, you could create changing wallpapers like in Windows 7, but you need to draft up an XML file with filenames, durations, and other information. This fits perfectly with the whole premise of our project; to create applications and programs that make difficult or tedious tasks so much easier!

---

### Post by VH-BIL on 2010-06-24
On the code monkey site there was a comment for a sleep timer. I thought I might whip one up for you.

```
#!/bin/bash
echo "Sleep Timer."
TimeMinutes=$(zenity --entry --title "Sleep Timer" --text "How long before shutdown? (minutes)" --entry-text "30");
TimeSeconds=$(($TimeMinutes * 60))
if [ $TimeMinutes = 1 ]
  then
    echo "System power off in 1 minute. ($TimeSeconds seconds)"
  else
    echo "System power off in $TimeMinutes minutes. ($TimeSeconds seconds)"
fi
sleep $TimeSeconds
echo "powering off now..."
poweroff
```
This is assuming the script is run as a administrator

---

### Post by Legendary_Bibo on 2010-06-25
> **tom.swartz07 said:**
> Thats perfectly fine! I wasn't too spectacular when I first started either. Personally, I would love to have you join the team, we could always use an extra hand on the bug reports and managing new ideas (YOURE WAY AHEAD ON THAT ALREADY!) 


*That actually is a neat idea to put in for our next major update to that program! Would you like to join and help advise the progress of this?*

Technically, you could create changing wallpapers like in Windows 7, but you need to draft up an XML file with filenames, durations, and other information. This fits perfectly with the whole premise of our project; to create applications and programs that make difficult or tedious tasks so much easier!

I'd love to!

Wait I just realized something, aren't terminal commands actually bash?

---

### Post by VH-BIL on 2010-06-25
> **Legendary_Bibo said:**
> Wait I just realized something, aren't terminal commands actually bash?
Check out [_Advanced Scripting Guide_]("http://tldp.org/LDP/abs/html/") for information on bash scripting. There are heaps of other sites as well!

---

### Post by tom.swartz07 on 2010-06-25
> **Legendary_Bibo said:**
> I'd love to!

Wait I just realized something, aren't terminal commands actually bash?

yep, theres a minute difference between bash and shell, but you could pretty much get away with using them interchangeably.

Join our Dev team (Here:[https://edge.launchpad.net/~codemonkeydevs](https://edge.launchpad.net/~codemonkeydevs)) and introduce yourself with a message to the other users. The link is on the top right when you join the team.

We could get started as soon as you want!



Anyone else is welcome to join too! Just shoot us an email from the Dev Team page!


Also, madjr, I didn't get a chance to dig into the PPA link that you had posted, but it didnt have any immediate information on creating a ppa. It just talked about how Launchpad was great for that person's project needs. Perhaps you inadvertently posted the incorrect link?

VH-Bil, Thanks for that script! Would you be interested in giving permission to our project to use it? We could licence it under Creative Commons Attribution licence, so you will get recognized for your work. :D

---

### Post by 23meg on 2010-06-25
Have you read [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA) and [https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading) ?

---

### Post by tom.swartz07 on 2010-06-25
> **23meg said:**
> Have you read [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA) and [https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading) ?

Yes, I have.
I found it very difficult to sort through the numerous articles. It would say that you could do it in 3 or 4 steps, but you needed to read 5 or 6 man pages for each subpoint of every step, and I couldn't understand it much.

Im looking for a simple, concise how-to on making a PPA.

---

### Post by VH-BIL on 2010-06-25
> **tom.swartz07 said:**
> VH-Bil, Thanks for that script! Would you be interested in giving permission to our project to use it? We could licence it under Creative Commons Attribution licence, so you will get recognized for your work. :D

Yeh of cause, as I said I just whipped that up quickly for you as there was a request for one on your project page. Do you need any others? I don't know python but I can do bash. I am a C# developer by trade.

---

### Post by 23meg on 2010-06-25
> **tom.swartz07 said:**
> Yes, I have.
I found it very difficult to sort through the numerous articles. It would say that you could do it in 3 or 4 steps, but you needed to read 5 or 6 man pages for each subpoint of every step, and I couldn't understand it much.

Im looking for a simple, concise how-to on making a PPA.

Creating a PPA and publishing packages to it is usually the easy part. You still need to do the actual packaging, which is where the [packaging guide]("https://wiki.ubuntu.com/PackagingGuide/Complete") comes in, and which I infer is where you're lost. Is that correct?

If the more problematic part for you is the publishing part, you might be interested in [an upcoming Launchpad feature]("http://micknelson.wordpress.com/2010/06/10/build-from-branch-coming-soon/") that will let you create PPA packages straight from a branch.

---

### Post by tom.swartz07 on 2010-06-25
> **23meg said:**
> Creating a PPA and publishing packages to it is usually the easy part. You still need to do the actual packaging, which is where the [packaging guide]("https://wiki.ubuntu.com/PackagingGuide/Complete") comes in, and which I infer is where you're lost. Is that correct?

If the more problematic part for you is the publishing part, you might be interested in [an upcoming Launchpad feature]("http://micknelson.wordpress.com/2010/06/10/build-from-branch-coming-soon/") that will let you create PPA packages straight from a branch.

It seems that the packaging is the tough part, we couldn't even figure out how to get past that part, so I wouldn't know about the publishing part.
Thanks for the link, ill see how that helps!


Is this upcoming feature you were talking about related to the Recipes that were popping up all over Launchpad beta?

---

### Post by castrojo on 2010-06-26
You'll still need packaging to use the lp recipe things. I recommend finding a package that exists that is similar to yours (ubuntu-dev-tools might be a good start) and then see how the debian/ directory is set up, and modify it to your needs.

(There are ubuntu packaging sessions on IRC at regular intervals throughout the cycle just for people like you: [https://wiki.ubuntu.com/Packaging/Training](https://wiki.ubuntu.com/Packaging/Training))

---

