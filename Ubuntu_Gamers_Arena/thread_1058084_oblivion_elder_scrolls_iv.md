---
title: "oblivion elder scrolls iv"
date: 2009-02-02
forum: Ubuntu Gamers Arena
---

### Post by thibbit on 2009-02-02
So, i'm finding myself in need of a bit of help here.

hardware 
  amd 64bit 3200
  2.7 gig ram (wont see the whole 3) 
  nvidia gforce le 6600
  2 monitors, a dell e770s and a compac ev700 (running in twin view)

OS
  dual booting (shouldn't make a difference and they are on separate hard drives)
  ubuntu 8.10 (kernel linux 2.6.27-7-generic
  and 
  windows xp sp3

I have the nvidia accelerated graphics driver version 177 installed and running with nvidia x server.
I have compiz config settings manager 0.7.8 for all the shiny bits.


I am trying to run “oblivion elder scrolls IV”
	did some searching/reading

I have installed wine 1.0.1

	installed oblivion but would not run 
		did more searching/reading

added mscoree into the wine library file and disabled it
	installed directx 9c from the oblivion disk
		game starts and fails to identify graphics card. It gives a generic setting of 
“adapter = direct3d hal”
“resolution = 2560x1024”
“antialiasing = none”
	it is spanning both monitors and running at the speed of dirt while in the character selection.
		Back on line search/read/repeat.. shutdown go to bed reboot... return loop.

Shutting off one of the monitors in xserver I have oblivion search for a graphics card, it still wont see it but it now gives me a total of 4 options for my resolutions, one being “1280x1024” (the other options are all higher and try and use both of my monitors).

I try and run it under the 1280x1024 it runs but again, slow as dirt. 
	 search/read/repeat.. fiddle with every graphic option I have, search through the game logs and try and find a resolution setting (fail fail fail).

I have looked into every forum that I can google on the subject and have yet to find a solution.

So now I turn to the great collective ubuntu community brain in a plee for help.  
I just switched to using ubuntu and while I can follow some of the baser ideas, please keep the instructions simple enough for a chain smoking monkey (that would be me) to follow.

---

### Post by 0bso on 2009-02-03
Are you disabling compiz? It doesn't play nice with 3d apps. 

Try running it after putting "metacity --replace" in the terminal. Then "compiz --replace" to reenable it when you're done. Make sure to disable the second monitor, I always have resolution problems when I don't.

---

### Post by thibbit on 2009-02-03
thanks for the reply.
tried that, dosn't seem to help. 
i think the base problem is that oblivion is not seeing the proper graphics card and i have no idea how to force it to. 
the rest of my system can see it just fine so im not sure where to start here.

---

### Post by 0bso on 2009-02-03
> &#8220;adapter = direct3d hal&#8221;

I think that is just how wine represents your graphics card. That's what my 6600gt shows up as in HL2 and other games played over wine and they still run at full speed.

You would probably be better served asking this in the wine subforum. There are way more knowledgable people than I, and it gets lots more traffic.

---

### Post by thibbit on 2009-02-03
And thank you, 
That actually is a help knowing that we have much the same graphics card and it is showing the same thing.
I put a post up over at wine hq and got some good feedback there too.
I have got it running in a windowed version with the latest game patch and a bit of tweaking in wine... and honestly thats enough for now. I think I have spent more time fiddling with this thing than I will get in game play, But hey im learning my way around the os while I do. :)

---

### Post by DarkW0lf on 2009-04-25
How did you get oblivion to install in wine ?
Is it the Game of the Year edition ?
Mine just quits, setup.exe and dxsetup.exe from both dvd and iso I made won't run.

I been following these instructions:
[http://ubuntuforums.org/showthread.php?t=349764](http://ubuntuforums.org/showthread.php?t=349764)

---

