---
title: "Risky or not??"
date: 2010-06-04
forum: Server Platforms
---

### Post by HunterAnderson on 2010-06-04
Hey guys. I was looking into setting up a server at my home but there were a few security things i wasn't sure about. We have 2 computers(one desktop and one to be server) running of the same router in our house. If i set up the server would it put the other computer at risk at all. And if it does how much of a risk is it?
Also, on the computer i wish to set the server up onto im dualbooting windows and ubuntu and i wanted to overwrite the regular ubuntu os with the server edition. Since the files on the windows os are in a separate partition would they be at risk at all? I knew there probably was some way for them to be at risk but i wasn't sure how big of a problem it would be.
Any input at all would be good. Thanks in advance.

---

### Post by garfonzo on 2010-06-04
What kind of "risk" are you referring to?

---

### Post by HunterAnderson on 2010-06-04
just any kind. mainly as far as viruses.  i no the linux server wouldnt be to much at risk simply because there arnt many linux viruses even out there but i wasnt sure if the server would make the other computer or the other partition on the hard drive more vulnerable.

---

### Post by sites on 2010-06-04
Sounds like the only threat will be from the user \\:D/

But seriously, there shouldn't be any problems.  What do you want to use the server for?  You might want to look into FreeNas.  It's a cinch to setup.

---

### Post by HunterAnderson on 2010-06-04
alright thanks. at first im just gonna try and use it as a web server and just kinda go from there to see what i can do with it. its not as much that i really need a server at my house but more so just i just wanna try it out. i never have really work with servers and such things before so i was gonna give it a go. i guess its just that drive to learn.

---

### Post by sites on 2010-06-05
Have you thought about installing the server OS as a virtual machine?

---

### Post by HunterAnderson on 2010-06-05
umm not really. why would you. im just not to familiar with virtual machining and what not

---

### Post by wojox on 2010-06-05
See my signature. I run a web server from my place and just use the Router and enable port forwarding.

---

### Post by HunterAnderson on 2010-06-05
nice. it seems to run like any other commercial site as far as speed and all. I don't think id be able to run that dependable of a site right now because of financial reasons. For now I'm just gonna have it on my laptop so anytime I have to move my laptop it would cut access. just wondering but do you think that if you cut the servers access from the router would it be much trouble to set it back up or would it be kind of like a plug and play type thing?

---

### Post by littlepeon on 2010-06-06
all computers connected to the internet are at risk!
the best way to eliminate risk is to not connect them to the internet.

that being said, adding a server to your network should not add too many risks.

if your system is compromised then yes, any files on any partitions can be re-written/corrupted and any other computers on the same network can be attacked.(whether or not they will be compromised depends on their security and how they are setup) 
that being said, as long as you don't open up unnecessary ports, check your logs regularly for suspicious behavior, use reasonable security for this server (firewall, host deny/host allow lists, password security), it can securely interface with your network and the internet without problems.

---

