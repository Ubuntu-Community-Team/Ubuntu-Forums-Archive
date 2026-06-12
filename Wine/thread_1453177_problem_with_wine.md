---
title: "problem with wine"
date: 2010-04-12
forum: Wine
---

### Post by CheAmr on 2010-04-12
Hello , 
I think that wine is not working at all with me 

I tried to run dozen of portable softwares ( less than 1 MB ) and its not working....

any suggestions . please ?

---

### Post by asdfoo on 2010-04-12
> **CheAmr said:**
> Hello , 
I think that wine is not working at all with me 

I tried to run dozen of portable softwares ( less than 1 MB ) and its not working....

any suggestions . please ?

what does "its not working" mean?

---

### Post by CheAmr on 2010-04-12
> **asdfoo said:**
> what does "its not working" mean?
means it gives me error .. that error report " send or don't send " that appears on windows 
as u see in this pic 

and as i told its portable softwares  less than 1 MB

---

### Post by asdfoo on 2010-04-13
> **CheAmr said:**
> means it gives me error .. that error report " send or don't send " that appears on windows 
as u see in this pic 

and as i told its portable softwares  less than 1 MB

First upgrade to Wine 1.1.42.


This app in your screenshot uses the .NET framework, you will probably need to install it with winetricks.

eg:  wget kegel.com/wine/winetricks && sh winetricks dotnet20

---

### Post by CheAmr on 2010-04-13
> **asdfoo said:**
> First upgrade to Wine 1.1.42.


This app in your screenshot uses the .NET framework, you will probably need to install it with winetricks.

eg:  wget kegel.com/wine/winetricks && sh winetricks dotnet20

I tried it and .NET installed ...

but now after restarting my pc 

and I tried to open the .exe software 
and this message in the pic appeared

---

### Post by CheAmr on 2010-04-13
any solutions ... please

---

### Post by dino99 on 2010-04-14
if you have not any important work or configs made with wine, and you might not have as you can use it, only and simply remove/purge wine with synaptic.

into your /home you have an hidden .wine: wipe it

be sure that you install from 
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

install it again with synaptic
goto menu: apps -- wine -- wine config, and validate without any modifications.

now, try to start your windows apps as you do with windoz. If thats dont work, view your logs: log inside .wine and linux logs (/var/log), you should learn from the errors.

you can learn too by searching about your apps with wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

---

### Post by CheAmr on 2010-04-14
why everything is hard with UBUNTU !!!!??

thanks for reply but truely I got nothing from it 
i went to that site [https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")

as you said and there is nothing to download 
no download button 

i find wine on ubuntu software center 
and this is the one i had before

no changes 
same errors

I downloaded more than 500MB to run a 1 MB portable software and after all it didnt run...

...dunno what to say

really disappointed..

---

### Post by dino99 on 2010-04-14
> **CheAmr said:**
> why everything is hard with UBUNTU !!!!??

thanks for reply but truely I got nothing from it 
i went to that site [https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")

as you said and there is nothing to download 
no download button 

i find wine on ubuntu software center 
and this is the one i had before

no changes 
same errors

I downloaded more than 500MB to run a 1 MB portable software and after all it didnt run...

...dunno what to say

really disappointed..

i agree with you but i you are able to read and understand what the link above says, so then it's easy. The latest line on that page give you tha last wine release, not so complicated dont you ?

You can find here lot of folks ready to help you but you have yourself to do a little effort.

---

### Post by CheAmr on 2010-04-14
thank you for your reply , u r talking about little effort from me :) ? i've been awake for two days to just let it runs my 1 MB software and it didnt work..
u know what ?
now i'm talking to you from windows XP , because my pc rebooted itself suddenly and ubuntu is not working with me anymore...
so i'll reinstall it again ( third time ) 

windows XP is really terrible

and I'm afraid that ubuntu is the same..

---

### Post by hikaricore on 2010-04-14
> **CheAmr said:**
> thank you for your reply , u r talking about little effort from me :) ? i've been awake for two days to just let it runs my 1 MB software and it didnt work..
u know what ?
now i'm talking to you from windows XP , because my pc rebooted itself suddenly and ubuntu is not working with me anymore...
so i'll reinstall it again ( third time ) 

windows XP is really terrible

and I'm afraid that ubuntu is the same..

So your opinion of Linux is low because your Windows software won't run on it.
Good luck with that...

I firmly believe that if you properly attempted to get this software running instead of being vague with us and barely bothering to try and understand what you're doing that you'd get it running.  However that is obviously not going to be the case any time soon.
You should probably consider mentioning what this software is and what it does.
There is probably a native alternative.

---

### Post by CheAmr on 2010-04-14
no there is isnt alternative software because this one and the others related to it created by a coder to help me with my work..

I'm not trying to bother any , but I really disappointed because I looked in everywhere for my problem and nobody solved it to me and the others are calling me that I don't make even a little effort 

I want it to run to help me doing my work , its a matter of life or death to be honest to me

that's it guys and thank you again

---

### Post by lavinog on 2010-04-14
> **CheAmr said:**
> no there is isnt alternative software because this one and the others related to it created by a coder to help me with my work..

I'm not trying to bother any , but I really disappointed because I looked in everywhere for my problem and nobody solved it to me and the others are calling me that I don't make even a little effort 

I want it to run to help me doing my work , its a matter of life or death to be honest to me

that's it guys and thank you again

Do you have access to the source code then?  Maybe it can be compiled for linux.

---

### Post by CheAmr on 2010-04-15
Thanks all of you 

I've fixed it ...finally :)

---

### Post by lavinog on 2010-04-15
What was the problem?

Don't forget to mark the thread as solved from the Thread tools menu.

---

### Post by CheAmr on 2010-04-15
the problem was with the wine itself it didnt install the .NET framework 100% so i removed it and tried to download/install it again with " sh winetricks " 
dontnet20
vcrun2003 and 2005

and it works .. 

but now there is two of them not working at all , no error message , nothing
but I have no clue about the software , so any suggestions ?

---

### Post by CheAmr on 2010-04-15
I thought it was solved but it isn't really 

the software just opened with me but I can not use it 
as long as it needed .NET framework to run .. what should I install to make it work ??

---

### Post by hikaricore on 2010-04-15
You're still being impossibly vague here and with that it's hard to offer anything at all.
Perhaps as was suggested you'd be better off having your software ported to linux instead of trying to do it all backasswards.
If this software was written for you to help with your work surely it can be ported by the same person.

---

### Post by CheAmr on 2010-04-15
> **hikaricore said:**
> You're still being impossibly vague here and with that it's hard to offer anything at all.
Perhaps as was suggested you'd be better off having your software ported to linux instead of trying to do it all backasswards.
If this software was written for you to help with your work surely it can be ported by the same person.
ok:)
thanks

---

