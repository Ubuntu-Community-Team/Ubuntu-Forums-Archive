---
title: "National instruments circuit design 10 with wine"
date: 2009-09-18
forum: Wine
---

### Post by drled on 2009-09-18
Hello,

I want to install the national instruments circuits design suite 10(multisim and ultibord) on my ubuntu laptop.

When the setup's load via wine i got this error:
```
Fatal error !!Required Nipathsdir property FIREFOXVERSION is undefined.

```

Screenshot: [http://img10.imageshack.us/img10/838/fatalerror.png](http://img10.imageshack.us/img10/838/fatalerror.png)

Can someone help me with this ?
Thanks

---

### Post by NM-GH057 on 2009-09-26
I'am having the same problem, if anyone knows a solution please let us know.

---

### Post by RainMan002 on 2010-04-08
Well I installed windows firefox with wine and I stopped getting that error.  Now it complains about LOGOSVERSION.  I have no clue what it's talking about.

---

### Post by asdfoo on 2010-04-08
you haven't told us which version of Wine you are using...

Update to 1.1.42 and retry if you are not using it already.

---

### Post by Das Goat on 2010-07-24
I can get Mutisim portable to install with Wine after futzing with wine extras to get the MSVCP60.dll loaded. It looks like it wants to run, but I can't get the NI License manager to load because it can't find the helpasst.dll. I can find this dll on my Windows partition, but I don't know how to cram this into Wine 1.1.42 

Anybody got an idea?

---

### Post by asdfoo on 2010-07-24
> **Das Goat said:**
> I can get Mutisim portable to install with Wine after futzing with wine extras to get the MSVCP60.dll loaded. It looks like it wants to run, but I can't get the NI License manager to load because it can't find the helpasst.dll. I can find this dll on my Windows partition, but I don't know how to cram this into Wine 1.1.42 

Anybody got an idea?

are you starting the application from the correct directory? you will need to cd to where it is installed and then run the main executable.  If you don't "cd" then it may fail to find its own files.

You shouldn't need to copy this "helpasst.dll" file from windows if you installed the application in Wine.  It should come with the program.

---

### Post by Das Goat on 2010-07-26
I'm not sure what you man about cd to the directory. I am launching the NI Licensing file with Wine.

Just to clarify, this is the Multisim portable edition. It has all of the things the regular edition does, but it doesn't install a bunch of the Windows crap. This means it can be used on a computer where you don't have the admin rights to install software.

But If I cant get the license manager to run, I can't apply the licenses, hence the need to figure out why it gets stuck on the Helpasst.dll file.

:arrow:](*,)

---

### Post by Das Goat on 2010-07-26
I installed Wine 1.2

Now the License manager doesn't give an error, but it just hangs and you have to restart the PC.

Anyone know of a way to apply the license without running the license manager?

:confused:

---

### Post by Das Goat on 2010-07-26
I ran the application for the command line. This is the error message I get:

wine: Unhandled stack overflow at address 0x7ed23338 (thread 0009), starting debugger...
err:seh:setup_exception_record stack overflow 1260 bytes in thread 0009 eip 7bc59361 esp 00230e44 stack 0x230000-0x231000-0x330000

I also loaded all the vbasic stuff from winetricks.

---

### Post by Das Goat on 2010-08-11
I have given up on Multisim 10. No one else seems interested and Multisim 11 is now out.

So far, it wants to install on Wine, but comes up with an error saying that "Internet Explore 4 can not be found" and exits the install. I have seen this error before with other programs, so hopefully some one has a simple answer.

I have tried:
U 10.04 64 and 32 versions
Wine is 1.3 (even though it reports 1.2 in About)
Installed IE6, IE7, and IE8 with Winetricks (only IE7 workes without errors, the others crashed on install) but the multisim installation program does not recognize these IE's as installed.
Fedora 13 w/ Wine 1.1.3 (I think) w/ wine-gecko just to see if it was an Ubuntu thing. I get the same error.

I am going to try Crossover later today. I really want to avoid that, but if it works, then maybe I can get approval to buy crossover.

If anyone knows how to fix this IE 4 thing, I know many people would be grateful.

;)

---

### Post by Dragoncracker on 2010-09-14
have you tried running winetricks and using fakeie6, I ask not because i have experience but because i am also interested in getting this up and running (student)

---

### Post by Dragoncracker on 2010-09-16
never mind it appears they took that function off the winetricks list

---

### Post by Dragoncracker on 2010-09-27
Ok so I'm looking for help/ideas.  The installer wouldn't run under wine because it said I needed IE4. SO I've Installed IE 6,7,8 with winetricks. It still won't install. So I have a Doner box with a fresh win xp install and installed it to that then copied the program folder from doner machine, program files to wine Program Files, then tried to run the program with no luck... what am I missing? I also didn't get any error message when i tried to run the copied edition

---

### Post by Das Goat on 2010-10-15
No one seems to love us :-P

What i have read, here and about, is that there are numerous ways that a program can check for IE, and Wine can't cover them all. Whining to WINE will not help. We need someone who loves to crack to maybe find it for us. On a related note, is there a fake registry in the wine bottle? Maybe it could be set there.

---

