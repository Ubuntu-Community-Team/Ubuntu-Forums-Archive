---
title: "Directx8.1 failed to initialize - warcraft 3"
date: 2009-12-17
forum: Wine
---

### Post by loketar on 2009-12-17
As title suggests i am getting this error when attempting to launch warcraft 3, i found a list of compatible games for linux 9.1 and warcraft 3 was listed so im assuming something is wrong on my end, I have my gfx card updated with it's drivers and i have updated wine but still to no avail, any help would be gratefully appreciated.

---

### Post by n0glu3 on 2009-12-17
Add " -opengl" to the end of the launch command, and make sure you add a  space between the end of the command already there and -opengl (like xxx/xxx/xxx/war3.exe -opengl).

---

### Post by loketar on 2009-12-17
where would one find this command? very very new to linux, took a break from it for about 6 months so just getting back into it, feels very 2 steps forward 1 step back if im perfectly honest

*edit* do you mean the actual war3.exe file?

---

### Post by n0glu3 on 2009-12-17
lol sorry. Do you have a Warcraft III shortcut on your desktop?

---

### Post by loketar on 2009-12-17
yup, got the shortcut to war3.exe on desktop, so do i just rename that file and put -opengl at the end of it?

*edit* found out what you meant, i right clicked on file, went to properties and there was a command line, im assuming thats where i change it?

---

### Post by n0glu3 on 2009-12-17
No!

Right click the shortcut and select Properties, then look for Command, there will be a box next to it (third down). Click once in the box and hold down right until you're at the end of the command (which should end with war3.exe). Then press space once then type the -opengl. Now click Close and try to launch the game.

---

### Post by loketar on 2009-12-17
done that the game launches as soon as it goes past the initial load screen i get left hanging on a black screen with a cursor to move (standard linux cursor not the warcraft 3 one) and i cant get out of this screen at all just had to hold power button down to shut my comp down.

---

### Post by n0glu3 on 2009-12-17
Sounds like WINE has screwed up or maybe a graphics driver issue. What version of WINE and which driver and card are you using?

---

### Post by loketar on 2009-12-17
I'm using a Geforce 210 gfx card with 185 graphics there is a 190 driver set but i can't get it to run when i attempt to i get three options:

1:run in terminal (this gives me an error message saying it needs to be run as root)
2:display (does nothing)
3:run (does nothing)

im using up to date wine according to updates. (V1.1.34)

---

### Post by n0glu3 on 2009-12-17
> **loketar said:**
> I'm using a Geforce 210 gfx card with 185 graphics there is a 190 driver set but i can't get it to run when i attempt to i get three options:

1:run in terminal (this gives me an error message saying it needs to be run as root)
2:display (does nothing)
3:run (does nothing)

im using up to date wine according to updates. (V1.1.34)

Sorry I don't understand;

> 
1:run in terminal (this gives me an error message saying it needs to be run as root)
2:display (does nothing)
3:run (does nothing)
Could you please explain a little clearer what you mean?

---

### Post by loketar on 2009-12-17
I have a file called this:

NVIDIA-Linux-x86-190.53-pkg1.run

when i double click on it, i get a box with 3 different options. (4 but im ignoring cancel)

Do you want to run "NVIDIA-Linux-x86-190.53-pkg1.run", or display its contents?
"NVIDIA-Linux-x86-190.53-pkg1.run" is an executable text file.

The first option is:

Run in Terminal

when i press this it runs the file in the terminal, after about 5 seconds it gives me an error message in the terminal saying:

"error: Nvidia installer must be run as root"



the second option is

display

when i click this, the linux cursor changes to the loading cursor (the equivalent of the windows hourglass when something is loading)
then when it is finished doing whatever it is doing it goes back to the arrow.



the third option is cancel (i didn't mention this as it is obvious as to what it does and it does work)




the fourth option is

run 

when i click this the linux cursor changes to the loading cursor the same as display.

---

### Post by n0glu3 on 2009-12-17
Ohhhhhhhhh, yes, that was very stupid of me :( 

The Nvidia driver is pretty hard to install manually if you don't have much experience. I doubt that it is a driver issue anyway, but you never know.

---

### Post by loketar on 2009-12-17
do you know of any links to anywhere i can try and install it?

---

### Post by n0glu3 on 2009-12-17
Not a good idea, you can seriously mess up your system if you don't know what you're doing.

I can help you if you have a 2nd PC with MSN, but otherwise it's just not worth the trouble.

---

### Post by loketar on 2009-12-17
ye i can get on msn, but only if you don't mind, you have been extremly helpful already I'd hate to impose anymore :/

---

### Post by n0glu3 on 2009-12-17
I'm on MSN right now so it's no problem. Send me your address and I'll add.

---

