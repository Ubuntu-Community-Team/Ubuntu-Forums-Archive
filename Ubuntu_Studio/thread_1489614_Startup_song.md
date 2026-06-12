---
title: "Startup song"
date: 2010-05-21
forum: Ubuntu Studio
---

### Post by ramirobh on 2010-05-21
Hey guys, how are you all? Well, i need some help, i tried to change my ubuntu-studio startup song following this tutorial.

[http://titotheman.wordpress.com/2009/11/06/changing-startup-sound-in-ubuntu-9-10-karmic/](http://titotheman.wordpress.com/2009/11/06/changing-startup-sound-in-ubuntu-9-10-karmic/)

But i was stupid, cause i followed even this...

Change &#8220;desktop-login&#8221; to the name of the sound file you want, without file extension.
Click Save and close the startup dialog.

Just after i did that, that i realized that would be more simple to just change the name of the original song to another name, and the name of the song that i wanted to "desktop-login".
However, now its not working any song anymore, the song that i chose just works when i enter as root, cause i tried to do it with root using the way i said up there, changing the song that i wanted to "desktop-login". Well, what i wanna know is if that is a way to restore my &#8220;GNOME Login Sound&#8221; in the list "System -> Preferences -> Starup Applications" without losing any data, or file. Thanks guys!

---

### Post by byStanderone on 2010-05-21
...the default sound files are located in: /usr/share/sounds/ubuntu/stereo
they are name specifics, you have to change the filename of the sound you want to use into that of the default so as the system will use it...substitute the sound clip that you want.

---

### Post by ramirobh on 2010-05-21
I know that man, but i just thought about that after i did what i explain in this topic, so what i wanna know is if i can restore the “GNOME Login Sound”  in Go to System -> Preferences -> Starup Applications... if there is a way to restore it to the original config or to restore the system to the day before yesterday without losing data.

---

### Post by ramirobh on 2010-05-21
Hey guys, i got it, so i will share with the community! Hehe
After i did the mistake that i told before in this topic, i tried many times to recreate the file, “GNOME Login Sound” in System -> Preferences -> Starup Applications, and it didn't work, however in a last shot, i tried to enter as root, since it was working the startup sound that i chose, and copy the properties from the file to a .txt file that i did with gedit, and save in my user home folder. 
After that i did login with my user, pasted the properties, and guess what? Problem solved, now when i startup my system, i hear the sound that i chose!
Like Bill & Ted would do...

:guitar: hehe

---

### Post by byStanderone on 2010-05-21
...nice, and don't forget to mark your thread as solved.

---

