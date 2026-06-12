---
title: "OpenGL: ChoosePixelFormat failed"
date: 2009-12-12
forum: Wine
---

### Post by fester225 on 2009-12-12
I'm trying to run Sketchup7 under WINE 1.1.34 and Ubuntu Karmic. I'm getting a diagnostic on startup which says;


Sketchup was unable to initialize OpenGL!
Please make sure you have installed the correct drivers for your graphics card.

Error: ChoosePixelFormat failed.


What does this error mean? 
How do I fix it?
Where does OpenGL come from? 
Is there a specific version I'm supposed to use?
Do I need Python to make OpenGL work?

---

### Post by noriegafam on 2010-04-23
This post is a little old but I decided to add some input to it since it might help some else trying to run Sketchup7 on Karmic Koala 9.10.

It is always better to download the last version of wine from their site since the Ubuntu repository is a little outdated. 

The version wine version that is working for me is 1.1.43.

The fix is real simple:

Fix:
Open your wine menu and open the C drive (/home/user/.Wine)
Open the Windows Folder
Find Regedit.exe and run it with Wine
Find: HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConf ig\Display
There are three entries - Look at the bottom one, name 'HW_OK"
Double click it and change the data from a 0 to a 1
Run Sketchup7

that should do it. I read some postings mentioning problems with black screens, which are related to compiz; in that case just disable compiz.

I hope this can help someone. I've been trying get Sketchup running for the longest time, I finally got it working with this little trick.

good luck

---

### Post by elphaba on 2010-07-10
I have Wine version 1.2 rc6  with karmic 9.10 and your regedit solution worked great.  I too got the OpenGL error along with the "choosePixelFormat" until I put in your fix.  THANKS!  
(though also have a print problem - the picture is totally black when printed but on the screen it looks great - another problem to investigate...)

---

### Post by gazm81 on 2010-07-18
Woohoo

thanks so much noriegafam, working perfectly

I love Sketchup, another reason I don't have to turn my windows box back on. 

I tried this with Ubuntu 10.04 with Google Sketchup 7.1.

also wine from the Ubuntu Software center version 1.1.42

---

### Post by newbymick on 2010-08-05
Your fix worked for me - brilliant.  Now all I have to do is work out how to use Sketchup ;)

---

### Post by nermaljcat on 2010-08-11
Thanks noriegafam! I've been trying everything to try get this working :)

---

### Post by davekenny on 2010-08-17
I wish it worked for me :(

I'm using a Dell 1545 running 10.04, wine 1.1.42.

it still crashes with the same message

maybe some day I get my dual boot working so I can run 9.04 or 9.10 and try it under that.

-DaveKenny

---

### Post by grey1beard on 2010-11-05
Thanks noriegafam, that solved my problem running Sketchup8 in Meerkat.
John

---

### Post by Tanasqui on 2010-12-19
Excellent Fix. 
Worked with my current config of Ubuntu 10.10 running SketchUp version 7.1.6860 in Wine 1.2.1

---

### Post by Randomredshirt on 2011-03-30
Hi All,

I've tried this fix but when i open the regedit.exe and work thru the menu I get only as far as ;
HKEY_CURRENT_USER\Software\Google\SketchUp7

\GLConf ig\Display are missing. 

Can anyone suggest why?  Is it something to do with the graphics card?

Thanks

---

### Post by karlhutt on 2012-02-23
thanks a lot! it worked! ujuuu!

---

### Post by madeinwales on 2012-04-11
> **noriegafam said:**
> This post is a little old but I decided to add some input to it since it might help some else trying to run Sketchup7 on Karmic Koala 9.10.

It is always better to download the last version of wine from their site since the Ubuntu repository is a little outdated. 

The version wine version that is working for me is 1.1.43.

The fix is real simple:

Fix:
Open your wine menu and open the C drive (/home/user/.Wine)
Open the Windows Folder
Find Regedit.exe and run it with Wine
Find: HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConf ig\Display
There are three entries - Look at the bottom one, name 'HW_OK"
Double click it and change the data from a 0 to a 1
Run Sketchup7

that should do it. I read some postings mentioning problems with black screens, which are related to compiz; in that case just disable compiz.

I hope this can help someone. I've been trying get Sketchup running for the longest time, I finally got it working with this little trick.

good luck


Can I just add that this solution also works for SU8 on Linux Mint 12 with Wine 1.3.28.

many thanks

---

### Post by pg-rugby on 2012-08-06
A thousand thanks for this tip.  Worked like a charm.  I am running Wine 1.4 on lubuntu 12.04, with SketchUp 8.

---

### Post by Vitos&#322;aw on 2012-08-27
Thank you [noriegafam]("http://ubuntuforums.org/member.php?u=92456"). I used your advice with Wine 1.4 and Sketchup 8.0. 
It works!

---

### Post by Cicer on 2012-10-13
Worked for me, too, thanks! In case you need everything spelled out (like I did), here's how to run regedit.exe from terminal.

```

cd ~/.wine/drive_c/windows
wine regedit.exe

```

---

### Post by boris_1981 on 2013-03-29
Thanks!!  

FYI to all, im running:
Wine 1.4.1
Google Sketchup 8 
Ubuntu 12.10

---

### Post by justb13 on 2013-06-10
Thank you. Much appreciated.
This worked for me as well.
I am using Ubuntu version 12.04
Wine 1.5
Sketchup 8
Amd 64 bit processor.

---

### Post by Elaphe on 2013-06-29
Hello everyone!

I know this is digging up an old thread, but I'm having the same problem as the OP, but can not seem to get through the fix, and I'm hoping someone here will be able to help me. To summarise, I am trying to install and run Google SketchUp 8 under Wine (not sure the Wine version) on my HP ProBook 4430s laptop with a Intel HD Graphics 3000 GPU and Ubuntu 13.04 64 bit. I have SketchUp installed, and it launches, but when I try to use SketchUp it fails and gives the error, "SketchUp was unable to initialize OpenGL....." I'm trying to follow the fix posted here, but when I run the regedit.exe file I cannot find a directory called "Google" under \HKEY_CURRENT_USER\Software, so I can go no further. Can someone help me with this please?

Thank you for your help!

-Elaphe

---

