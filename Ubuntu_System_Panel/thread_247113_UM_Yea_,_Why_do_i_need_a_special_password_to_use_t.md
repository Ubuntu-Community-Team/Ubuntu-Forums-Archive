---
title: "UM Yea , Why do i need a special password to use these things..??"
date: 2006-08-30
forum: Ubuntu System Panel
---

### Post by jason.b.c on 2006-08-30
When i try to do:

System tools / Printers  

i'm told this:

[I]To run the program "/usr/bin/foomatic-gui"
you need to enter the root password..[/I]

WHY..???   What the heck is the password to this..???   My login password..? , Cause that don't work.!

ROOT..???   That dosen't work..!

What gives here..??  What is it thats locked out..??   :confused:

---

### Post by jrib on 2006-08-30
It *should* be the same as your first user's login password.  But something may have gone wrong.

Did you do a regular install? (not expert)

Open a terminal (applications > accessories > terminal).  What does the command ```
sudo echo hi
``` return after entering your password?

---

### Post by bernied on 2006-08-30
Have you tried the command:
sudo /usr/bin/foomatic-gui
then enter your user password.
That should start the utility as root.

Does this work, or should it be a different command for X applications? In kubuntu it's kdesudo.

---

### Post by PWill on 2006-08-30
This doesn't have anything to do with the USP, it will occur any time you run that program. Are you an administrator on this computer?

---

### Post by jason.b.c on 2006-08-30
> **xiamcitizen said:**
> This doesn't have anything to do with the USP, it will occur any time you run that program. Are you an administrator on this computer?

Well i kind of assume that it does , Because this **only happens** when i try to launch these things through the U.S.P.   ..:confused: 

I'll try the other suggestions above and let you all know...

---

### Post by chanders on 2006-08-31
I dont seem to have a /usr/bin/foomatic-gui *scratches head*

---

### Post by pyros on 2006-08-31
> **bernied said:**
> In kubuntu it's kdesudo.
in ubuntu it's gksudo

---

### Post by jason.b.c on 2006-08-31
> **_jason said:**
> It *should* be the same as your first user's login password.  But something may have gone wrong.

Did you do a regular install? (not expert)

Open a terminal (applications > accessories > terminal).  What does the command ```
sudo echo hi
``` return after entering your password?

```
jason@Hp-Vectra-VL:~$ sudo echo hi
Password:
hi
jason@Hp-Vectra-VL:~$


```

OK , What the h*ll was that supposed to do..?? :confused:

---

### Post by jason.b.c on 2006-08-31
> **chanders said:**
> I dont seem to have a /usr/bin/foomatic-gui *scratches head*


Well it's in your programing..!?

I'm scratching my head too..:-&

---

### Post by jrib on 2006-08-31
> **jason.b.c said:**
> ```
jason@Hp-Vectra-VL:~$ sudo echo hi
Password:
hi
jason@Hp-Vectra-VL:~$


```

OK , What the h*ll was that supposed to do..?? :confused:

That was just to make sure sudo was working ok.  Are things like synaptic launching ok and accepting your password?  foomatic-gui is the only thing that is giving you problems?

What version of ubuntu are you using?

System > Administration > Printing opens gnome-cups-manager by default in Dapper which is the reason I ask

---

### Post by jason.b.c on 2006-08-31
> Are things like synaptic launching ok and accepting your password? 

No , there are several others as well..

> What version of ubuntu are you using?

Signature..     Breezy...

---

### Post by jrib on 2006-08-31
Ah I didn't realize what USP meant until now...

If 'gksudo synaptic' in a terminal is working ok and accepting your password but the USP shortcut doesn't, then that is a little strange and I'm not sure what to suggest

---

### Post by jason.b.c on 2006-08-31
You've got it , The shortcut isn't working correctly....

---

### Post by beskyddaren on 2006-09-04
Why not upgrade to dapper while you're waiting for a reply?

---

### Post by jason.b.c on 2006-09-05
> **beskyddaren said:**
> Why not upgrade to dapper while you're waiting for a reply?
Nope..!!, Never again...

[Why would i want to do that when i had so many problems and didn't get any real help....???]("http://www.ubuntuforums.org/showthread.php?t=207014")

---

### Post by jason.b.c on 2006-09-16
So i guess no-one knows huh..? #-o 

Thats great..:roll: 

It does this on the following:

[B]Computer

Network[/B]

and

**Date and Time**

Why... can't i access these with my normal password...??? ](*,)

---

### Post by Anduu on 2006-09-16
Remember the old joke about the guy that goes to the doctor and says "Hey doc it hurts when I do this..."

And the doctor says "Well don't do that..."

Sorry I couldn't resist :P

Anyways maybe try uninstalling/reinstalling USP.Maybe USP just won't work properly with Breezy?

---

