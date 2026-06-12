---
title: "Ubuntu CE 64bit still missing"
date: 2007-05-08
forum: Ubuntu Christian Edition
---

### Post by redlabour on 2007-05-08
Hi,

i get several Problems if converting Feisty 64bit to CE.

Anything new about a 64bit CE Script ?

DansGuardian is crashing so i cant start e-Sword and some other Problems under 64bit.

---

### Post by mhancoc7 on 2007-05-08
> **redlabour said:**
> Hi,

i get several Problems if converting Feisty 64bit to CE.

Anything new about a 64bit CE Script ?

DansGuardian is crashing so i cant start e-Sword and some other Problems under 64bit.

I would be willing to put together a convert_me script for x64. I would need someone to test the existing convert_me script and report what does not work and why. I do not have an x64 system to test so I would need very detailed info and someone willing to test and re-test the script.

Jereme Hancock

---

### Post by mysticrider92 on 2007-05-09
I'll test the x64 convert_me script (and iso's when you do them). I just put Feisty 64bit on my machine, so that would be awesome.

---

### Post by mhancoc7 on 2007-05-09
> **mysticrider92 said:**
> I'll test the x64 convert_me script (and iso's when you do them). I just put Feisty 64bit on my machine, so that would be awesome.

Thanks, would you be willing to test the current convert_me script and report what did not work?

Thanks, Jereme

---

### Post by mysticrider92 on 2007-05-10
> **mhancoc7 said:**
> Thanks, would you be willing to test the current convert_me script and report what did not work?

Thanks, Jereme

Ok. I won't be able to test it until around Saturday, but I will try it as soon as possible and let you know.

---

### Post by mhancoc7 on 2007-05-10
> **mysticrider92 said:**
> Ok. I won't be able to test it until around Saturday, but I will try it as soon as possible and let you know.

Great! Thanks!

Jereme

---

### Post by mysticrider92 on 2007-05-16
Okay, I just tested the convert_me script (sorry it took so long). I tried everything except the Virtual Roasary and it all seemed to work. I already had Automatix2 on there, so that might have changed it a bit. The only problems I had were it erased my Firefox settings and my usplash screen isn't displayed anymore (it just gives a list of what is starting). Otherwise, everything worked fine.

---

### Post by mhancoc7 on 2007-05-16
> **mysticrider92 said:**
> Okay, I just tested the convert_me script (sorry it took so long). I tried everything except the Virtual Roasary and it all seemed to work. I already had Automatix2 on there, so that might have changed it a bit. The only problems I had were it erased my Firefox settings and my usplash screen isn't displayed anymore (it just gives a list of what is starting). Otherwise, everything worked fine.

Thanks for letting me know. The convert_me script has been updated to make backups of your personal settings such as the firefox stuff. I am not sure about the usplash issue.

Did you use the e-Sword Installer? Did it work?

Thanks so much, Jereme

---

### Post by mysticrider92 on 2007-05-17
Okay, an update. I found that the Dansguardian GUI would not load. I get the gksu screen asking for a password, but nothing after that. I have the same problem with the e-Sword, The Word, and IE6 installers. I already installed IE4Linux on this Ubuntu, so you could set it up to use the same installer I used for that (i'll have to dig up the site I used).

I am trying the e-Sword install script from a terminal to see if that works, i'll tell you how that goes later.

[edit] I found the problem. The launchers in /usr/local/apps/* don't seem to work. Running the scripts in a terminal does work. I have done the e-Sword script successfully and am trying The Word script.

---

### Post by redlabour on 2007-05-28
> **mysticrider92 said:**
> Okay, an update. I found that the Dansguardian GUI would not load. I get the gksu screen asking for a password, but nothing after that. I have the same problem with the e-Sword, The Word, and IE6 installers. I already installed IE4Linux on this Ubuntu, so you could set it up to use the same installer I used for that (i'll have to dig up the site I used).

I am trying the e-Sword install script from a terminal to see if that works, i'll tell you how that goes later.

[edit] I found the problem. The launchers in /usr/local/apps/* don't seem to work. Running the scripts in a terminal does work. I have done the e-Sword script successfully and am trying The Word script.


Same for me after trying the 32bit ConvertScript after the Release on a 64bit Kubuntu.  ;)

---

### Post by mcnairl on 2007-06-20
Greetings and Salutations,

I have the 64 bit feisty (AMD 64) with the CE upgrade and I cannot get e-sword to launch either.

I have the same issue with Configure Parent controls.  I do get an error on the latter, gbx closed unexpectedly.

Any suggestions would be great.  This is my first forum so I hope I am posting correctly.

In JESUS's Service,

Larry

---

### Post by mysticrider92 on 2007-06-22
I believe (not certain) that the problem is GAMBAS (kind of a specialized language) is not working quite right with the 64 bit arch. All that we need to do is get the program built on a 64 bit system (which I can probably do when I get back from a trip tomorrow), then compile all of the CE-specific packages with that (the easy part). 

I will try to make a 64 bit .deb of GAMBAS for doing this, so if there is any one with 64 bit Ubuntu that could help test the packages (they should be fine, but just to make sure the 32-64 bit conversion went well).

---

### Post by mysticrider92 on 2007-06-23
After a bit of looking, it appears that GAMBAS will not work with 64bit pointers (see [here]("http://gambas.sourceforge.net/distribution.html")). So the GUI will need to be rewritten in a new language. Is there anyone who would want to help?

---

### Post by mhancoc7 on 2007-06-24
> **mysticrider92 said:**
> After a bit of looking, it appears that GAMBAS will not work with 64bit pointers (see [here]("http://gambas.sourceforge.net/distribution.html")). So the GUI will need to be rewritten in a new language. Is there anyone who would want to help?

You might want to have a look at the UbuntuME web content filtering GUI. I believe it is done with Python.

Jereme

---

### Post by beta.tester on 2007-06-24
> **mhancoc7 said:**
> I would be willing to put together a convert_me script for x64. I would need someone to test the existing convert_me script and report what does not work and why. I do not have an x64 system to test so I would need very detailed info and someone willing to test and re-test the script.

Jereme Hancock

Hi Jeremy

Please count me in on this and where I can get the 64 bit script please.

Pax et bonum

john

---

### Post by mhancoc7 on 2007-06-24
> **beta.tester said:**
> Hi Jeremy

Please count me in on this and where I can get the 64 bit script please.

Pax et bonum

john

Thanks for your interest in helping with this.

There isn't a 64 bit script yet. It appears that one of the main issues is that Gambas is used to build the filtering GUI. 

The problem is that the 64 bit Ubuntu has some areas that need work apparently.

Jereme

---

### Post by mysticrider92 on 2007-06-24
I think I can probably help write the GUI so you can keep working on the 32 bit CE. We could use either Java or Python.

Also, I was looking at modifying the UbuntuME script like you suggested, but apt is not cooperating and I can't find a download link for it.

---

