---
title: "Wine and Guildwars"
date: 2009-02-20
forum: Wine
---

### Post by Sojurner on 2009-02-20
I have recently installed Guildwars and im having a few issues. Yes the game is running fine for the most part, however it is not rendering 3d like it would in windows. Its choppy even with the lower specs

Even in windows using an older driver would still work just fine with the  3d rendering. I am now having to lower my specs in the game to get it to run good for the most part. Any idea why i am having this issue or what i could do to fix it?

Graphics Card: 8800GTS Nvidia 640MB
Processor: AMD 6000+
Ram: 2GB

---

### Post by binbash on 2009-02-20
are you starting guildwars with -opengl ? which version of wine are you using? go to appdb.winehq.org and look for the wine version which runs guild wars flawless(you will also find some tricks at comments of guild war entry) and install it.OR you can use playonlinux , it has a guild war install script, which i tried and works perfectly

---

### Post by Sojurner on 2009-02-20
im not quite sure how to tell if im  starting it with openGL or not. Im kinda noob at this but take instructions very well. I am currently downloading the dev version of wine 1.1.12 that says is good for GuildWars. Do i just add the -opengl to the commandline and ifso where?

I have just downloaded and installed playonlinux. Do you know if i will need to reinstall GW or if i will be able to update and run it now with this installed?

---

### Post by binbash on 2009-02-20
Dude, you are starting a wine application with this way : 

you are navigating to the exe and : 

wine asdadasd.exe

you will add -opengl at the end : 

wine asdadads.exe -opengl

EXample : 

cd .wine 
cd Program Files etc etc
wine Guildwarsblabla.exe -opengl

---

### Post by Sojurner on 2009-02-20
I have it installed through the playonlinux installer but whenever i launch it all i get is a black screen in the upper left of my monitor. i hear all the sounds but no picture. I can Alt-Enter and put it in a window and its all screwy looking. Any idea how i can get it to work right???

---

