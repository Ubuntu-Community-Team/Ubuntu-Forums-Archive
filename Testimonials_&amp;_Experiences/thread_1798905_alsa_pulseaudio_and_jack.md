---
title: "alsa pulseaudio and jack"
date: 2011-07-06
forum: Testimonials &amp; Experiences
---

### Post by dimas869 on 2011-07-06
i particulary think that audio configuration in ubuntu is a very good example of how ubuntu could frustrate the user.

ubuntu offer a wide variaty of application but if you install one then it will remove the configuration of the other one and then wont work anymore

and then no body want to explain the true about it

so i think it would be better if you try unify the service and when you offer an application then make sure it wont distroy another or at least let us know what it will do

konquering users? or trying to make a friendly evironment?

sad we have to go throw this disagreement between developers

---

### Post by zero244 on 2011-07-07
Occasionally my sound in Lucid stops working.
I figured out how to fix it, but it was a matter of trial and error.
I installed Alsa mixer......on two occasions my sound stopped working completely.
If I go into alsamixer and uncheck the wrong sound card that got checked on its own.
My sound starts working again.

If I were a new first time user I might just say to heck with it and move to something else.

---

### Post by dimas869 on 2011-07-08
hey zero244, thank you for the advise

in my case i even reinstalled the whole ubuntu platform and still had the same problem so i digged out all over and found a repository and then i was able to use jack and properly configure it

this is what i did:

[PHP]sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update

sudo apt-get install linux-alsa-driver-modules-$(uname -r)
[/PHP]

---

