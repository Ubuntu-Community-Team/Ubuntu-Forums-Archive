---
title: "DreamWeaver 8 on Wine under 10.04 does not work"
date: 2010-08-14
forum: Wine
---

### Post by twola on 2010-08-14
I installed wine. I then clicked on the Dreamweaver 8 executable that installed with no problems. After than when I try starting DreamWeaver, I can see a small tab on my task bar saying "Starting Macromedia" but then it goes away and nothing ever happens.


Please suggest.

---

### Post by cogadh on 2010-08-14
Run the app from the terminal and post Wine's error output here. Please use the forum "[CODE]" tags to make it readable.

---

### Post by twola on 2010-08-14
```

scott@scott-casa:~/.wine/dosdevices/c:/Program Files/Macromedia/Dreamweaver 8$ wine Dreamweaver.exe
err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Macromedia\\Dreamweaver 8\\Dreamweaver.exe" failed, status c0000005


```

---

### Post by cogadh on 2010-08-14
Nice! Short and informative. Looks like you need to install MDAC to get a Windows native version of odbc32.dll. The best way to do that is via [winetricks]("http://wiki.winehq.org/winetricks").

---

### Post by twola on 2010-08-14
I see:

mdac25
mdac27
mdac28

Any one in particular?

---

### Post by cogadh on 2010-08-14
Honestly, I don't know, but you might want to check [Wine's Dreamweaver page]("http://wiki.winehq.org/AdobeDreamweaver") for more information.

---

### Post by twola on 2010-08-14
I made a leap of faith and got the most latest version of mdac and now dream weaver started. Thank you for your help and assistance. It was greatly appreciated.

---

### Post by fromgi on 2010-08-27
Can you please tell me what you did to get and install the latest version of mdac?  Thank you.

---

### Post by fromgi on 2010-08-27
Never mind.  I got it to work.

---

### Post by twola on 2010-08-27
Cool.

---

### Post by mh2ack on 2010-09-18
I may have missed something, but my install of Dreamweaver 8 worked fine on my install of Ubuntu 10.04 until recently. Today I found it would try to launch Dreamweaver and then end. I assume some update broke it. So a search got me here and the info eventually got me to the solution, but just so others don't have to go pounding their head or clicking links...
the link to winetricks [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) gives some nice info only when I typed sh winetricks in a terminal as instructed there I got an error 
Cannot find wineprefixcreate (wineprefixcreate) 
Which led via a google search to
[http://wiki.jswindle.com/index.php/Wineprefixcreate](http://wiki.jswindle.com/index.php/Wineprefixcreate)
Which to summarize says that wineprefixcreate is deprecated, ie you do not want to use it. To put it bluntly this should not be the result of entering sh winetricks so someone needs to fix something with winetricks so that it gives a more informative error. Since I knew that I needed to launch winetricks and sh winetricks did not work, what to do? Just out of blind stupidity of just trying something in terminal I typed in 
winetricks
Yep just winetricks! It launched a nice GUI where you can scroll down to mdac28 and checkbox it and it installs after asking you to agree to a MS eula. And Dreamweaver 8 works now. 
I hope that helps some others who are less technically inclined and just want the answer.

---

### Post by wandalalakers on 2010-09-19
Thx!

---

### Post by fabrizioprocopio on 2010-10-24
Hi everybody
I'm new to ubuntu forum. Please to meet you all.

I got the same problem with DW.
I did not succeed to solve.

- I restore DW
- Then I unistalled it
- Then I re-installed it

I did the some procedure with (well working) Fireworks (just to be sure...)
No result.

So:
- I unistalled wine
- I deleted .wine folder
- I re-installed wine
- I re-installed DW (and poor working Fireworks too)
No result


So:
I went to microsoft website and I download MDAC 2.8
from the following URL
[http://www.microsoft.com/downloads/thankyou.aspx?familyId=6c050fe3-c795-4b7d-b037-185d0506396c&displayLang=it](http://www.microsoft.com/downloads/thankyou.aspx?familyId=6c050fe3-c795-4b7d-b037-185d0506396c&displayLang=it)

and then I ran the downloaded file under wine
I wrote in terminal winboot (to simulate a reboot)

I googled a lot.

Nothing, no result.

I don't know more how to proceed.
When i click on my old friend icon of Dreamweaver 8 on my ubuntu desktop, DW appears and then, after some second vanishes from bottom bar.

I ask for your help, I need a lot DW 8.

thanks in advance for your time

---

### Post by FrankyG on 2010-11-03
In response to post #5 and #6 and just to confirm for others in trouble (and for searches via google):

I had the same problem of DW8 not starting anymore after upgrading from wine 1.1 to 1.2 or even to wine 1.3 (current development release). So, I chose to install mdac28 via winetricks simply like so:

```
$ winetricks mdac28
```Finally, DW8 (Dreamweaver 8.x under wine 1.3) is up and running, yay! Thx everybody!

Btw, shouldn't we tag this thread as SOLVED?

Frank

---

### Post by fabrizioprocopio on 2010-11-08
I don't know what means

```
$ winetricks mdac28
```

Sorry

---

### Post by FrankyG on 2010-11-08
> **fabrizioprocopio said:**
> I don't know what means

```
$ winetricks mdac28
```

Sorry
It simply means to open a terminal, type "winetricks mdac28" and hit the ENTER-Key. This installs a missing component for DW8 to run under wine 1.2/1.3.

---

### Post by fabrizioprocopio on 2010-11-08
Ok, I got it!


Little howto for dummies like me:
(just a dummy can catch a dummy and explain to a dummy)
:)

(to paste click on momdify menu in terminal and then click on paste: control+V doesn't work - works instead control+shift+V))

- I open a terminal (I HATE IT)
- I pasted this ```
wget http://www.kegel.com/wine/winetricks
```
- then I pasted this  ```
chmod +x winetricks
```
- then I pasted this ```
./winetricks
```
- a window comes out
- find and flag mdac28
- click on OK

some windows come out, and I clicked on like a normal windows installation.
I clicked on -close- at the end of process.

Now my Dreamweaver 8 works perfectly.

[I found this link in italian (my language) tha helped me a lot]("http://tailot8.blogspot.com/2009/11/winetricks-installare-librerie-su-wine.html")

Hope my dummy explanation can help someone else
:)

---

