---
title: "Questions about connecting audio and studio upgrade"
date: 2012-01-12
forum: Ubuntu Studio
---

### Post by emkooi on 2012-01-12
What i'm trying to do is run my guitar through my mic input on my laptop.  I'm curious if it is at all possible to use the effects that i have on Rakarrack and record them into Ardour.  I've read alot on Jack but must not be comprehending how its all linked. 

I'm a long time windows user who just deleted windows 7, and need to remember how to learn this kind of stuff. 

also kind of off topic, i installed studio through synaptic, downloaded all the packages for studio, but the themes don't show up in the appearance menu, there is a purple screen prior to the new ubuntu studio boot sequence, and the login sound is now non existant...did i mess something up or is that something i can fix?

thanks

---

### Post by jejeman on 2012-01-12
> also kind of off topic, i installed studio through synaptic, downloaded all the packages for studio, but the themes don't show up in the appearance menu, there is a purple screen prior to the new ubuntu studio boot sequence, and the login sound is now non existant...did i mess something up or is that something i can fix?I guess you are using ubuntu 11.10. For this release it's not recommended to mix ubuntu and ubuntustudio because ubuntustudio uses Xfce. You can see if there are different sessions tat you can choose on login.
> What i'm trying to do is run my guitar through my mic input on my laptop. I'm curious if it is at all possible to use the effects that i have on Rakarrack and record them into Ardour. I've read alot on Jack but must not be comprehending how its all linked. Of course it's posible, thats the whole point. You need to use jack for that.
Read this for start
[http://ubuntuforums.org/showpost.php?p=11604550&postcount=4](http://ubuntuforums.org/showpost.php?p=11604550&postcount=4)

---

### Post by emkooi on 2012-01-12
Yes I am using 11.10. So should I go down to 11.04 would that remedy the little issues I'm having?  And like I said I've read a lot on jack, that website included. I'm just having trouble connecting each program. Every time I tried no effects were recorded  in ardour so I'm positive I'm not connecting them properly.

---

### Post by jejeman on 2012-01-12
You don't need to change the version or reinstall if you don't mind cosmetic issues.

First, is jack running, and is it stable? This means without any frequent xruns.

---

### Post by sgx on 2012-01-12
[http://www.guitar.com/articles/recording-guitars-get-signal](http://www.guitar.com/articles/recording-guitars-get-signal)

[http://www.bedroom-recording.com/audio-signal.html](http://www.bedroom-recording.com/audio-signal.html)

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

You'll want to know and implement these things. :popcorn:

Once Rakarrack is connected, it is still off, tickbox is in the upper left corner.

It may also start in mono, best to change that to stereo in its preferences.
Cheers

---

### Post by BcRich on 2012-01-13
> **emkooi said:**
> I'm just having trouble connecting each program. Every time I tried no effects were recorded  in ardour so I'm positive I'm not connecting them properly.
Hi emkooi
This tutorial, I make a while back is on making connections between various audio software in ubuntu studio. JACK, Ardour and Rakarrack are discussed so I hope it helps?
[http://www.lyndondaniels.com/2010/learn/music/OSSDAW/](http://www.lyndondaniels.com/2010/learn/music/OSSDAW/)

EDIT:You might want to skip ahead to here [http://www.lyndondaniels.com/2010/learn/music/OSSDAW/03recGuitar.html](http://www.lyndondaniels.com/2010/learn/music/OSSDAW/03recGuitar.html) section titled "Ardour Setup" if JACK and Rakarrack are up and running

---

