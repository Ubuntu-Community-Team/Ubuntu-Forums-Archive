---
title: "Virus found and not removed"
date: 2008-05-23
forum: Security
---

### Post by shay1 on 2008-05-23
My computer started to refuse downloading updates to Ubuntu Hardy Heron and so I employed a Windows reflex. I checked for viruses. I know we don't generally suffer from them but I had been doing a lot of networking to the other windows and ubuntu computers in the house and file swopping by USB memory stick.

The Clam antivirus program found 11 viruses after an extremely slow search  and AVG for linux found 7 but neither removed them. 

I have tried ticking the box in Clam to quarantine them but it somehow does not stay clicked and there seems to be no post-search way to quarantine them. 

Similarly AVG for windows automatically quarantined them but there seems to be no way to so this in the Linux version?

Any help on this matter would be gratefully received as I can not update Ubuntu until I solve this problem (if indeed the viruses are causing the download failure)

Shay

---

### Post by ASULutzy on 2008-05-23
What happens when you try and get updates?

---

### Post by shay1 on 2008-05-23
Thanks for your reply.

The notification window appears and then when instructed to download/install the process just hangs...and hangs.

---

### Post by Tomatz on 2008-05-23
You need to start the apps with root privelages.

In a terminal type:

```
gksu avg
```

Oblioulsy to run clam as root change the avg part ;)


P.s you can edit your menu entries so avg and clam start with gksu from the menu.

---

### Post by shay1 on 2008-05-23
Thanks Tomatz,
I am currently running ClamTk and have changed teh settings after it started running to quarantine the viruses and that seems to be having the effect of quarantining them.

As I am new to Ubuntu (<1yr) I am curious to know why running as Root should make a difference to Anti-virus packages quarantining the virus or is this a general precaution? (Or is so obvious I should not ask the question?:))

Shay

---

### Post by Tomatz on 2008-05-23
> **shay1 said:**
> Thanks Tomatz,
I am currently running ClamTk and have changed teh settings after it started running to quarantine the viruses and that seems to be having the effect of quarantining them.

As I am new to Ubuntu (<1yr) I am curious to know why running as Root should make a difference to Anti-virus packages quarantining the virus or is this a general precaution? (Or is so obvious I should not ask the question?:))

Shay

To update (virus def's) and remove viruses in clam you have to run it with root privileges. This is because clam needs to have root privileges to remove viruses if they are located on another drive or in the root of the primary drive.

Quarantining viruses in clam without root privileges is probably just copy
ing the viruses (into quarantine) rather than removing them.

Also as said you need to run clam as root to update your virus def's ;)

---

### Post by shay1 on 2008-05-23
Hello,
Thanks again for that reply
I need to learn more about Linux / Ubuntu to get all these protocols into my mind. Generally I am happy with Ubuntu and want to stick with it but it is very different to Windows and my mind needs to get around these little problems. One of my obstacles was to learn the terminal concept better. So far I have avoided it and tried to use Ubuntu out of the box (fairly successfully, it has to be said) and only gone to root or terminal when necessary.

I will try this again when it has stopped running its present scan and report back. Realistically this is going to be tomorrow as it has taken several hours to plough through my hard disk already!

Thanks again,
Shay

---

### Post by shay1 on 2008-05-28
Update
OK after setting clam to quarantine viruses and letting it run for 8 hours through 230,000 files it did the job. The viruse(s) was/were in old windows files which I have stored for members of my family. Have taken them into windows to get them healed.

(Incidentally, I was able to get clam to work in terminal but not avg and with a different command to the one offered?)

The other problem was with the downloading of updates which was hanging - and still is unless I go to terminal and issue the command there, when it works fine. I have noted quite a few respondents, on a different thread, noting they are reporting problems updating, on the same day as me. So perhaps there is a bug to be fixed? At least I can now make progress again.

So, I have mixed two problems together, apologies for that confusion but many thanks to those that helped me get solutions to them.

---

### Post by blore on 2008-11-16
> **Tomatz said:**
> To update (virus def's) and remove viruses in clam you have to run it with root privileges. This is because clam needs to have root privileges to remove viruses if they are located on another drive or in the root of the primary drive.

Quarantining viruses in clam without root privileges is probably just copy
ing the viruses (into quarantine) rather than removing them.

Also as said you need to run clam as root to update your virus def's ;)
Thanks Tomatz, using your advice above i was able to update clam for the 1st time.
One minor but important variation however:
                                          # gksu clamtk
does the trick.
                 thanks

---

### Post by Tomatz on 2008-11-16
> **blore said:**
> Thanks Tomatz, using your advice above i was able to update clam for the 1st time.
One minor but important variation however:
                                          # gksu clamtk
does the trick.
                 thanks


Cool :)

BTW avscan is quite a good front end for clamav. You can install it like this:

```
sudo apt-get install avscan
```

Run it as root with **gksu** or **sudo** ;)

---

### Post by cariboo on 2008-11-16
Could you post the list of files that are supposedly infected, as they are probably either windows viruses or false positives. Your update problems are more then likely due to some other problem.

If you don't know which files have been flagged as being infected, have a look at the log file which is located in /var/log.

Jim

---

### Post by shay1 on 2008-11-17
Thanks for the reply, just wanted to say my problems have been sorted. The first was infected window files, the second was updates that had to be completed by using terminal rather than the automatic system I had been using which caused package manager to hang. This second problem eventually went away on its own and I have been using it happily until recently. I think it is caused by some kind of dislocation between hte computer/software/update information. At present it just thinks it has not updated when it has but it still updates ok.

---

### Post by tqzxzjhu on 2008-11-18
[&#25329;&#22661;&#21306;&#31649;&#36947;&#30095;&#36890;&#30005;&#35805;](http://classad.dahangzhou.com/223685.html)[&#19978;&#22478;&#21306;&#31649;&#36947;&#30095;&#36890;&#20844;&#21496;&#30005;&#35805;](http://classad.dahangzhou.com/223685.html)[&#19979;&#22478;&#21306;&#31649;&#36947;&#30095;&#36890;&#20844;&#21496;&#30005;&#35805;](http://classad.dahangzhou.com/223685.html)[&#27743;&#24178;&#21306;&#31649;&#36947;&#30095;&#36890;&#20844;&#21496;&#30005;&#35805;](http://classad.dahangzhou.com/223685.html)[&#35199;&#28246;&#21306;&#31649;&#36947;&#30095;&#36890;&#20844;&#21496;&#30005;&#35805;](http://classad.dahangzhou.com/223685.html)

---

