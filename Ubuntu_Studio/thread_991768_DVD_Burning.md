---
title: "DVD Burning"
date: 2008-11-24
forum: Ubuntu Studio
---

### Post by Bofur on 2008-11-24
I feel like a noob asking this but I want to burn a couple .avi files to disc so I can play them at my friends and family's house. What is the best software for this and do I have to convert them to .iso's before I burn them and if I do how do I go by doing that? Thank you!

---

### Post by TenPlus1 on 2008-11-24
Pop into [www.getdeb.net](www.getdeb.net) and look for DeVeDe, this will let you convert your .avi files to DVD Video format and create an .iso file that you can burn to DVD using Brasero...

---

### Post by AgentZ86 on 2008-11-24
Yes, DeVeDe is very good, Just go to Applications/Add / Remove and you can select it from the list, and install it.

Just open start the program and select either Video DVD,VCD,or SuperVCD etc. in your case most likely a DVD, however you can decrease the quality and convert to VCD also

Anyhow, then just click properties to change the Title1 or add titles and then click properties to create your titles

Then to the right select your avi files and put them in for each title that you want.

Select Create ISO and it's very simple to operate.

You will have to decide on video properties such as: Default or weather you want to expand the screen to fill in the black bars at the top or bottom.

You may want to play with those settings a bit. on 32 bit Ubuntu it will take longer to convert then on 64bit ubuntu, but in anycase if your not doing zillions of them it should be fast enough.

I hope this helps

---

### Post by Mountford D on 2008-11-24
I used to convert them to DVD format but found that most DVD players are capable of playing MPG files anyway. I now just convert my AVI files to MPG using avidemux and burn the MPG files to DVDs (as data DVDs) using k3b (Brasero is as good). I can get 2 or 3 films on a DVD and the process is a lot quicker.

If you want "proper" DVDs then you will need to do what the other posters suggest.

---

### Post by Zaraphrax on 2008-11-24
> **TenPlus1 said:**
> Pop into [www.getdeb.net](www.getdeb.net) and look for DeVeDe, this will let you convert your .avi files to DVD Video format and create an .iso file that you can burn to DVD using Brasero...


Hey thanks, buddy. This helps me too. :)

---

### Post by Bofur on 2008-11-26
Okay well basically I made the .iso file and burned it to a dvd+r but whenever i try playing the dvd it just says the title of the movie with a cd in the background and thats all it plays. Any ideas?

---

### Post by Bofur on 2008-11-26
Also if I run the .iso with vlc it runs fine, however there is no sound lol.

---

### Post by Bofur on 2008-11-26
Bump

---

### Post by AgentZ86 on 2008-11-26
DeVeDe will simultaneously convert and create the ISO for you, then use Brasero and select burn ISO, and I've never had any problems using this. And it's easy, and all can be installed from the GUI Applications/Add/Remove

---

### Post by ja4 on 2008-12-03
Thanks, the DeVeDe .iso solution worked great to get around this stupid bug in Brasero [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497226](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497226)


@ Bofur:  Since I had only one title on the menu, I just had to press "enter" or "play" on the DVD's remote to start the video.

---

