---
title: "Installing Sibelius 5"
date: 2008-08-27
forum: Ubuntu Studio
---

### Post by fetimo on 2008-08-27
Hi there,
I have managed to install Sibelius 3 on my friends Ubuntu computer via Wine but have not been able to upgrade it to Sibelius 5 because of the .Net things and C++ requirements. Is there any way to get round this? I have searched the forums and a couple of users have the same problem but still no definite resolution it seems.

Hope someone can help as it was my idea to install Ubuntu on there!

Tim

---

### Post by Stochastic on 2008-08-27
It's not a direct solution to your problem, but I might suggest you try to learn a open source alternative to Sibelius.  I personally use Lilypond (and find its scores much prettier that those from Sibelius), but others enjoy MuseScore, Denemo (though newer versions are more stable), and Rosegarden just to name a few.  Sibelius is a very powerful program though and none of these have all of it's features, but they do work quite well - which is more than I can say of Sibelius 5 in Ubuntu.

---

### Post by fetimo on 2008-08-27
Yeah I have looked at some of them but she's going to be using Sibelius at Sixth Form and so needs to transfer the files from and to. I was going to try VirtualBox and see if there was any difference - has anyone had any luck with it at all? I know it's not an ideal setup but don't think the others have Sibelius file support.

---

### Post by fetimo on 2008-08-28
Okay well for those that want to know I've had some luck with using winetricks. The code I used is as follows:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) && sh winetricks dotnet20 vcrun2008 msxml3

Not sure if the vcrun2008 was necessary but either way it got the job done!

---

### Post by jazzvibes on 2008-09-24
Hi fetimo
I'm interested to know how well your Sibelius 5 works under wine using winetricks?

---

### Post by demios on 2008-09-29
likewise, interested. Sibelius is the reason vista is on my system.

---

### Post by JJoel on 2008-10-05
I'm interested in running Sib 5 as well,
I'm currently installing it, I stumbled across this if any one is interested.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10843](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10843)

---

### Post by demios on 2008-10-05
just tried sib 4 and it works with the newer .net framework and couple other things (I forget which) from winetricks, also I'm using timidity, if that helps. haven't tried sib 5 yet, not sure if I need to -- though that ideas panel looks pretty sweet.

---

### Post by tnd on 2008-10-31
I've got Sibelius 5 installed with VST support, the only thing I've found so far that doesn't work is key signature display (when selecting it, it's fine once it's on the score).

I've put up [a guide on the Wine appDB](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10843), but the formatting has left it rather jumbled so here it is cleaned up a little:


> 
1) Install wine and wine-dev 

2) Get winetricks: in terminal enter 'wget [http://www.kegel.com/winetricks](http://www.kegel.com/winetricks)' (without quotes, and assume the same for all terminal entries below) 

3) In terminal enter 'sh winetricks' and select corefonts, dotnet11, dotnet20, gdiplus, msxml3, msxml4 and msxml6. I also selected vcrun2008, but I'm not sure if this makes a difference to Sibelius. 

4) Install wineasio. If not in the repositories, the source is available here [http://sourceforge.net/projects/wineasio](http://sourceforge.net/projects/wineasio) 

You may need the JACK audio server and its development files - if there is an error during the installation of wineasio, this could be why. I'm not sure whether this step was necessary for me or not. If you do, get qjackctl as well, it's a GUI control for the JACK server. 

Check the readme as well, it asks for a DLL and an asio.h file, both of which are freely downloadable from the internet.

5) Copy msvcp60.dll from a Windows installation (or download it, it can be found on Google) to ~/.wine/drive_c/windows/system32 

6) Enter the Sibelius 5 DVD, and find the location of the installer msi - on mine it's /Windows/Sibelius/SibeliusEnglishInstaller.msi In terminal enter 'wine msiexec /i /SibeliusEnglishInstaller.msi and wait for install. 7) Find the "Other Applications" section of the Sibelius DVD and install Sibelius Sounds Essentials (SSE_Setup.exe) 

8) Run Sibelius, register... and I hope it works for you. 


For what it's worth, the installation was very much trial and error so feel free to correct me on any unneccessary steps you spot.

Also, I don't use these forums as much as I should, but I'll try and subscribe to email alerts for the thread, so if anyone needs any of the dlls and whatnot you can *try* posting it here.

(Annoyingly, after some recent changes GNUDenemo works really well on my computer for the first time ever, so I may take some time getting to know that instead)

Hope my ramblings help
 - Owen

---

### Post by pietgrijs on 2009-01-20
Hi tnd,

I am a new user to Ubuntu; I installed Wine and Sibelius to see if it would work, since running Sibelius is an absolute necessity for me (there being no good Ubuntu alternative...). It didn't work of course. The I found your manual and applied it (with Sibelius already installed), but now I keep getting a MS Visual C++ Runtime error, R6034. Thing is, I can't uninstall Sibelius somehow, the install package won't do it. 
Any tips?

---

### Post by demios on 2009-01-20
I also had trouble removing sib and even wine itself from my previous install. luckily I got it right the first time on this install. I'm thinking of getting a persitent live usb install to test bigger things like that.

that being said, I'd also like to know methods for removing stubborn programs from wine, if you come across a way

---

### Post by OboeNerd on 2009-01-21
How does Kontakt Player 2 run on Wine?  Does Sib 5 run with Kontakt and the Garritan Personal Orchestra?

---

### Post by tnd on 2009-02-21
OK, sorry I've left this alone for a while.

For those having the C++ runtime error, I have just experienced this with my new laptop and succeeded in fixing it by removing wine completely, then starting from scratch. 

The method at the Wine AppDB entry for Sibelius should be updated soon, but basically I replaced installing "vcrun2008" using winetricks with installing the following:
```
vcrun6
vcrun2005
vcrun2005sp1
``` 

Installing vcrun6 provides msvcp60.dll, so there's no need to take that from a windows install either :)

Hope that helps.

To uninstall wine (demios, I have the same problem, no other solution yet that I know of) - 

```

sudo apt-get remove wine wine-dev
sudo rm -rf .wine
rm winetricks

```

---

### Post by demios on 2009-02-22
for people having trouble getting the audio to work, sometimes you have to break the ice: open a project, play > playback and input devices, then hit the test button for whichever device you're using (TiMiDiTy port 0 usually works for me).

failing that, restarting timidity often helps: from a terminal, run

```
/etc/init.d/timidity restart
```

then try again. hope this helps someone.

---

### Post by StephenOK on 2009-02-24
The most crucial problem probably being the V.S.T. integration into Sibelius 5. Although I never ran Sib 4, I just hated that green environment, I upgraded from Sib 3 and have it installed on both my macs. 
Instead of trying to port it through wine, I would like to check out some of the other applications mentioned earlier on in the post that run natively on linux - sound like some pretty cool stuff. As long as you can create rhythmically complicated scores with layers upon layers of nested-tuplets, it would be something cool for me to check out.

---

### Post by Bucky Ball on 2009-04-22
I hate to say it; nothing in the Linux world comes close to Sibelius (at this point) regarding flexibility and ease of use, I wish it did. It really depends on what you need your notation software to do, though. Tuplets are one thing; ornamentation, expression, technique, lyrics, part writing, part printing and viewing options, formatting functions, ... are another.

---

### Post by Stochastic on 2009-04-22
> **Bucky Ball said:**
> I hate to say it; nothing in the Linux world comes close to Sibelius (at this point) regarding flexibility and ease of use, I wish it did. It really depends on what you need your notation software to do, though. Tuplets are one thing; ornamentation, expression, technique, lyrics, part writing, part printing and viewing options, formatting functions, ... are another.

Yes, however once you learn how to code lilypond, using frescobaldi is quite flexible in all those areas.  It does however lack in the ease of use region (due mostly to the sharp learning curve).

One thing you could do to help is talk with the developers of Denemo and describe the issues you have with their software (possibly even suggest new ideas for them).  It's one thing to complain about the state of notation software in Linux, it's another thing entirely to do something about it.

---

### Post by Bucky Ball on 2009-04-22
I ain't complaining and also understand the deeper reasons for this situation ... money. Unfortunately, I don't have much time or the particular desire to code anything, let alone lilypond. And yes, I have used it and it looks the most promising, although there are others. As I say, when I have an orchestra score with all markings, hidden bars, technique markings and a huge assortment of other requirements, for the moment I shall be booting Sibelius. Last time I looked at Lilypond, ease of use and functions were the issues, nothing else. For what it is at the moment it is a great piece of software that can only get better. I far from have complaints and no problem whatsoever with the project or developers.

No complaints but I'd love a Linux alternative and use Windows only for Sibelius and pro multi-media stuff. Let's not start on Pro Tools, Cubase, Reason, Premiere Pro (Cinelerra is also great but at this point no match) and a bunch of others. Glazing over just thinking about the pointlessness of the exercise. We need to look deeper at why this situation exists and why software development has been stymied by it. If we always had open-source and nothing else, computing would be at a level of sophistication that makes what we do now look like baby steps. :)

---

### Post by GabrielWolff on 2009-11-02
The thing with Linux alternatives is always the sharing issue. Other than if you write for yourself alone and have never send scores to driends and colleges, you have to use sib compatible programs.

---

