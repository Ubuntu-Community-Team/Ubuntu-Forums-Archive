---
title: "Hydrogen with freebob"
date: 2008-05-05
forum: Ubuntu Studio
---

### Post by nalmeth on 2008-05-05
Has anybody been able to get Hydrogen working with JACK using FREEBOB? I'd really like to use it with Ardour and the JACK transport, but Hydrogen is unable to connect using freebob. 

The only information I could find is from this thread: [http://www.hydrogen-music.org/forum/?action=show_thread&fid=4&thread=594&page=1](http://www.hydrogen-music.org/forum/?action=show_thread&fid=4&thread=594&page=1)
The solution was to edit hydrogen.conf to output to the freebob line in, but this doesn't seem to work in Hardy.

Its tricky in hardy, because the device appears under a different name in the connections window. 
I tried starting jack via command line, which will give you the actual name of the freebob input, but using this didn't work either (I'm not at my PC right now, but its something similar to freebob_pcm:dev1p_LineOut 1+2 left)

Anybody have any luck with this? Any ideas? 
BTW, I'm using a Firepod in this case, but I'm sure its the same with any firewire device using freebob.

EDIT: OK, just found this thread: [http://ubuntuforums.org/showthread.php?p=4750224](http://ubuntuforums.org/showthread.php?p=4750224)
But I'm hoping there is another way besides compiling the development version. Hydrogen can be shaky as it is :)

---

### Post by Stochastic on 2008-05-05
yeah, it's working fine for me out of the box on hardy with my firepod.

Freebob version 1.0.7, Hydrogen 0.9.3
I tried it with both Auto and Jack audio settings in Hydrogen and both work fine, though I had already de-selected "Connect to Default Output Pair" as that option had caused troubles for me in the past.

What seems to be happening with yours?

---

### Post by nalmeth on 2008-05-06
Sweet!
After disabling "Connect to Default Output Pair" it connects to Jack. 

Thanks Stochastic

---

