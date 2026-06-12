---
title: "Questions regarding RAM wiping using Sdmem on logout"
date: 2015-03-05
forum: Security
---

### Post by squirrel2003 on 2015-03-05
I have a few questions regarding the thread.  
1) Would executing sdmem before i log out wipe rests of my encryption key out of the RAM of my laptop so that i can let the camera record and be secured against a cold boot attack? I am no sure if this only makes sense when powering off the system.  

2) I am trying to put the sdmem script i created in the correct folder so it will be executed when i am logging out following the instructions given in the first answer in the  thread in the following link.

[http://askubuntu.com/questions/293312/execute-a-script-upon-logout-reboot-shutdown-in-ubuntu](http://askubuntu.com/questions/293312/execute-a-script-upon-logout-reboot-shutdown-in-ubuntu)

  However the file lightdm.conf does not exist in the path /etc/lightdm/ on my Ubuntu 14.04 64 Bit system.  

Please tell me where to the script so everything will work.  I found this answer on ubuntuforums.org but am still not sure what to do in my case.  

3) How will i be able to check if the script is really running on logout. I guess if you give me the correct answer how to do it and i implement it right it should suffice but will there be some graphical Display or is there any other way to check?

---

### Post by squirrel2003 on 2015-03-06
Can someone answer my question please?
Especially where to put the line to execute the script since the lightdm.conf file is missing.

---

### Post by bashiergui on 2015-03-07
> 1) Would executing sdmem before i log out wipe rests of my encryption key out of the RAM of my laptop so that i can let the camera record and be secured against a cold boot attack? I am no sure if this only makes sense when powering off the system.Your question doesn't really make sense. The encryption key would be in the memory while the computer is on. When you turn it off the volatile RAM is cleared, so there would be no point in wiping it then.

---

### Post by cogset on 2015-03-08
I'm surely offtrack here, but wasn't a relatively recent flaw in Tails exactly about not  wiping the RAM completely at shutdown? Is there a chance of something similar happening in this case as well?

---

### Post by squirrel2003 on 2015-03-08
Afik upon shutdown RAM gets wiped automatically if you wait 2 minutes.
I want to wipe the free RAM which could contain my login password (could it contain my login password orthe home encryption key?) upon LOGOUT.
Impov Ubuntu should implement some feature like tresor which keeeps RAM encrypted.
However tell me where i can put scripts that get executed upon logout please i will need it for other stuff too.

---

### Post by bashiergui on 2015-03-08
> **squirrel2003 said:**
>  Ubuntu should implement some feature like tresor which keeeps RAM encrypted.You can't encrypt RAM. Tresor runs encryption outside of RAM so that the key can't be recovered from volatile memory. [http://en.m.wikipedia.org/wiki/TRESOR](http://en.m.wikipedia.org/wiki/TRESOR)> However tell me where i can put scripts that get executed upon logout please i will need it for other stuff too. [http://askubuntu.com/questions/293312/execute-a-script-upon-logout-reboot-shutdown-in-ubuntu](http://askubuntu.com/questions/293312/execute-a-script-upon-logout-reboot-shutdown-in-ubuntu)

---

### Post by squirrel2003 on 2015-03-08
[http://askubuntu.com/questions/29331...down-in-ubuntu](http://askubuntu.com/questions/29331...down-in-ubuntu)
Does not work because the file does not exist anymore in Ubuntu 14.04.
I've got another thread running regarding the same matter  
[http://ubuntuforums.org/showthread.php?t=2268201](http://ubuntuforums.org/showthread.php?t=2268201)
but still have got no solution, help please i just need the right file where i can paste in the dependance pointing to the script so it gets executed upon logout.

Another question: Would sdmem not show if there are rests of some encryption key stored in RAM?

I have read the info on the Tresor homepage and for a noob to programming and such like me it seems a bit complicated to implement, so i guess i will stick to sdmem for now until Ubuntu has managed to implement something like Tresor in their OS.

---

