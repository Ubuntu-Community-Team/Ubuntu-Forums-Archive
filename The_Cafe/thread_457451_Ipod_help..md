---
title: "Ipod help."
date: 2007-05-28
forum: The Cafe
---

### Post by Narutolinspire on 2007-05-28
I have a 30gig apple ipod video brand new and well i don't quite know how i can use it on linux and i have until next week to get songs on it.

---

### Post by Andrewie on 2007-05-28
[http://amarok.kde.org/](http://amarok.kde.org/)

Amarok 

just open your package manager and install Amarok

or 'alt + F2' then paste this command in the window 'sudo apt-get install amarok'

---

### Post by Narutolinspire on 2007-05-28
yeah but i have had it installed.

I had my ipod mounted and it showed up on my desktop. 

I went to media device and it said "could not find device. Re-mount it and try again."

---

### Post by reclusivemonkey on 2007-05-28
Have you created the directories on the iPod already?

---

### Post by Narutolinspire on 2007-05-28
i honestly don't know :-D 

can i do it with a linux computer?

---

### Post by reclusivemonkey on 2007-05-28
I'm not *completely* sure you can. If you plug in your iPod and it shows up on your desktop, you may be able to do it through GTKPod. Its on the file menu.

If you can, I would advise you to plug it into a Windows PC/Mac and use iTunes to initialise the iPod. From there, it will work fine in Linux.

---

### Post by Narutolinspire on 2007-05-28
well i don't have current access to a mac or pc atm. 

I been trying to get gtkpod all day and i cant seem to be able to download....

When i download it, it goes to ark and i dont know what to do from there

---

### Post by reclusivemonkey on 2007-05-28
```
sudo apt-get install gtkpod
```

Should do it.

---

### Post by Narutolinspire on 2007-05-28
do i type that in a terminal?

---

### Post by reclusivemonkey on 2007-05-28
Yep, that's right.

---

### Post by Narutolinspire on 2007-05-28
i sounded stupid there. i did like 100 times.

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

thats what i keep getting

---

### Post by reclusivemonkey on 2007-05-28
You might find this link useful as well;

[http://ubuntuforums.org/showthread.php?t=430350&highlight=ipod+gtkpod](http://ubuntuforums.org/showthread.php?t=430350&highlight=ipod+gtkpod)

---

### Post by reclusivemonkey on 2007-05-28
> **Narutolinspire said:**
> i sounded stupid there. i did like 100 times.

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

thats what i keep getting

You must have Synaptic open. Close that and try again.

---

### Post by Narutolinspire on 2007-05-28
indeed i did but i also got this before that.\

Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package gtkpod

---

### Post by Narutolinspire on 2007-05-28
btw when u download something on the internet it goes to ark.. What do u do for there?

---

### Post by reclusivemonkey on 2007-05-28
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

---

### Post by Narutolinspire on 2007-05-28
very very confusing. I dont get what the link was for?

---

### Post by hanzomon4 on 2007-05-28
You need to enable the universe and multi-verse repositories, I guess that's what the link was for. 

The easy gui way to do this is to open synaptic>click on _settings_ in the menubar>click on _repositories_>and tick *"community maintained open source software(universe)"* and *"Software restricted by copyright or legal issues (multiverse)"* Then install gtkpod as explained in the other post.

---

### Post by Narutolinspire on 2007-05-28
when i click on repositories it looks like this. (pic below)

[[IMG]http://img257.imageshack.us/img257/8484/wowyj4.png[/IMG]](http://imageshack.us)

---

### Post by Narutolinspire on 2007-05-28
thanks you guys were almost no help at all :)

---

### Post by hanzomon4 on 2007-05-29
Are you using Debian sid?

---

