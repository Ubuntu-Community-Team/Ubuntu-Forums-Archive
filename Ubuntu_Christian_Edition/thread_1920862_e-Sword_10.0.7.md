---
title: "e-Sword 10.0.7"
date: 2012-02-05
forum: Ubuntu Christian Edition
---

### Post by jonathonblake on 2012-02-05
All:

e-Sword 10.0.7 was released on 2 February.
I have it installed on my Linux desktop.
It more or less works with WINE 1.2.x.
It did not work with WINE 1.3.x.

I'm in the process of compiling WINE 1.4.x, to see how that works.

jonathon

---

### Post by forrestcupp on 2012-02-08
In case anyone has struggled with the standard search, dictionary, and Strongs tool tip problems, I found a solution by Silverhair on [this web site](http://www.biblesupport.com/topic/1316-useing-e-sword-in-linux-with-wine/) that gets everything to work perfectly. I've tried the installer script floating around here without success, but this solution made everything work like a charm. You have to do a few things before you install e-Sword, though, so read through it *before* you install. After performing these steps, I just installed e-Sword 10.0.7 using Wine v1.2.3, and I'm pretty pleased.

I just wish it weren't so darned slow. Anyway, here is the solution that is listed by Silverhair on that web site:

> Hi Dave

I have been running mint 11 and ubuntu 11.10. I am running wine 1.2.3 stable on both systems. The following has worked for me with both systems.

Do this before installing E-sword:

Set oleaut32 to builtin in winecfg

In winetricks install

msls31
msxml3 *
vbrun6
vcrun6
wsh57

Once these are installed you can install E-sword and it should work.

* To install msxml3 winetricks will open an MS download site where you can get the file. Once downloaded put it in: home/user-name/.cache/winetricks/msxml3

To find the .cache type ctl-h while in your home dir to show the hidden files. You my have to reselect the files to have winetricks install them 

---

### Post by Murphy-10332 on 2012-03-09
Thank You for re-posting the write up. I works Great!

---

### Post by ubume2 on 2012-04-30
The fix posted by forrestcup [post #2] does work if instructions are followed closely. I can now utilize a full search.

I installed e-Sword 10.10 from the e-Sword site on Ubuntu 11.10.  I have not tried it yet using the e-Sword installer script. Edit: Using the installer script the search function does not work properly.

I made sure all of the dlls recommended by forrestcup showed up in winecfg library.  I installed wine 1.2 first and then later 1.3.

Edit: This fix works under Ubuntu 12.04.  You may have to run winetricks a couple of times.

Thanks forrestcupp!

Thanks.

---

### Post by GeorgeMat on 2012-05-04
Hi All,

I tried to set Esword on 12.05.

I followed instructions on this website which mentions the following - 
quote-----------------------------------------------------
Do this before installing E-sword:

Set oleaut32 to builtin in winecfg

In winetricks install

msls31
msxml3 *
vbrun6
vcrun6
wsh57

Once these are installed you can install E-sword and it should work.

* To install msxml3 winetricks will open an MS download site where you  can get the file. Once downloaded put it in:  home/user-name/.cache/winetricks/msxml3
Unquote-----------------------------------------------------

the installation goes thru, but when I try to run esword as follows from the command line, I get the following response.

wine setup951.exe 
fixme:storage:create_storagefile Storage share mode not implemented.

Pls assist. God bless

George

---

### Post by ubume2 on 2012-05-04
> **GeorgeMat said:**
> 

the installation goes thru, but when I try to run esword as follows from the command line, I get the following response.

wine setup951.exe 
fixme:storage:create_storagefile Storage share mode not implemented.

Pls assist. God bless

George

Are you using the e-Sword installer script?
If you are it is an old one. 

If you are installing it manually through the wine windows program loader, try rebooting and see if it works.

My e-sword is now fully functional on Ubuntu 12.04. I am using the latest exe file from the e-Sword website. E-Sword 10.10 which is a 50 mb file.

If the install does not work, try this in this order:

delete all instances of e-Sword in /home. These are usually hidden files.

Follow forrestcupp's tutorial. You may have to run winetricks twice.  The second time you will get access to microsoft's dll files.  It will ask you for your name and company.

check winecfg to see if all the files appear in libraries.

Make sure the exe file is marked executable under permissions.

Right click on the exe file and chose to install with wine windows program loader.  You may get an error message at the end of the install, but e-Sword works (for me) in spite of the error message.

Hope this works. Good luck

Edit: oops. didn't realize I had already posted on this thread.  This post may be somewhat redundant.

---

### Post by forrestcupp on 2012-05-05
> **GeorgeMat said:**
> 
the installation goes thru, but when I try to run esword as follows from the command line, I get the following response.

wine setup951.exe 
fixme:storage:create_storagefile Storage share mode not implemented.

Which setup is it that goes through, the winetricks one, or the e-Sword one? If the e-Sword setup has gone through, then you don't need to run setup951.exe again. But if you're talking about the Winetricks part working, but then you're having trouble installing e-Sword, maybe you could try **cd**'ing to the folder that has the setup951.exe file and try this slightly different command:
```
wine ./setup951.exe
```
But honestly, it's easier to just find the file in Nautilus and double click on it.

---

### Post by padeco on 2012-09-05
i have installed e-sword 10.1. greek and hebrew fonts, cpopying paste etc. all well.

there is one things that does not work. and that is 'search'. for some reason, i cannot search. also, i was not able to install msxml3, any ideas?
many thanks

---

### Post by jonathonblake on 2012-09-05
> **padeco said:**
> 
there is one things that does not work. and that is 'search'.

Does Regex search work?

> i was not able to install msxml3, any ideas?

What error message are you getting?
That file can take half a dozen, if not more attempts to install, before it sucessfully and correctly installs.

jonathon

---

### Post by padeco on 2012-09-07
many thanks,
regex works just fine! what is the difference?
great hint!
cheers

> **jonathonblake said:**
> Does Regex search work?



What error message are you getting?
That file can take half a dozen, if not more attempts to install, before it sucessfully and correctly installs.

jonathon

---

### Post by geo316 on 2012-10-03
ok... all went well following the instructions here.

e-Sword installed, runs, and searches just fine. I'm using 10.1.0 under Ubuntu 12.04.

One annoyance though, the verses in the left pane do not highlight when I click on them, and most (maybe even all) of the verse links clicked in the right pane commentaries do not cause the left pane to go to the verse -it goes to the book and chapter, but not to the verse. 

If I click a verse and then switch translations the left pane does not stay on the verse. 

If I click a verse, the icons in the commentary tabs change (indicating available content) as they should, but the open commentary won't scroll to the text pertaining to the verse. 

It's as if the little "chain" icon were not clicked.

Any ideas anyone?

George

---

### Post by jonathonblake on 2012-10-10
> **padeco said:**
> many thanks,
regex works just fine! what is the difference?


Rick uses different libraries for "normal" search, and Regex search.
There are a couple of aggravating things about the Regex implementation he uses, but it isn't too bad.  

jonathon

---

### Post by ubume2 on 2013-07-08
Edit: I find that the script at:
[http://ubuntuforums.org/showthread.php?t=404042&page=83&p=12576234#post12576234](http://ubuntuforums.org/showthread.php?t=404042&page=83&p=12576234#post12576234)
post 823 works great!

The fix mentioned in post #2 had worked famously for me on all versions of Ubuntu, Mint, Debian, whether 32 or 64 bit, until now.  I did a reinstall of 12.04 and the search results no longer worked.  I've tried it three times on 12.04 32 and 64 bit, and Xubuntu 64 bit.  I am using wine 1.4.

Anybody having this problem?

---

