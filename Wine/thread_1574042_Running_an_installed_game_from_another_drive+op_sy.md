---
title: "Running an installed game from another drive+op system in wine."
date: 2010-09-13
forum: Wine
---

### Post by eimhin85 on 2010-09-13
Hi all, Im having problems trying to run a game in wine that has been installed (successfully) in win XP. 
The game is Baldur's Gate II and has had mods applied from the [COLOR=Blue]_[BWP]("http://www.shsforums.net/topic/44661-big-world-project-bwp-v90/")_[/COLOR] program. The game was installed via win XP (which is installed on a separate physical hard drive to linux) under F:/Games/BGII - SoA. In win it works fine. 
the steps i have taken are pretty much as follows:-

[LIST]
[*] In Ubuntu I have edited /etc/fstab so that the harddrive is automatically mounted here:- ```
/home/250gbwinxp
```
[/LIST]
  
[LIST]
[*] then i went to 'Configure Wine' and to the 'Drives' tab and added a new with the letter 'F:' and has the drive mapping of /home/250gbwinxp too.
[/LIST]
  
[LIST]
[*] ive been trying to run in terminal variations of:-
[/LIST]
[INDENT]```
gksudo wine "f:/Games/BGII - SoA/baldur.exe"
```But have had no luck so far as it simply states > wine: cannot find 'f:/Games/BGII - SoA/baldur.exe'(Running the exe directly brings up an error message stating > An Assertion failed in Chitin.cpp at line number 1628 Programmer says:Error initializing key table, bad key file. which i assume is because it is looking for a file it cant find too.)
[/INDENT]anyone know anything im doing wrong?

---

### Post by weblordpepe on 2010-09-13
Hi dude.

When you are typing out files or directories (folders) that have a space in the name, you gotta put \ in front of the space.

Its so when you're typing out long complex stuff, it can tell the difference between a new command or something and just a file name with a space. It also saves ya from having to put file names into speech marks or something like that. Here's an example:

**/home/toiletmonster/Documents/My\ porno\ pictures/weblordpepe\ on\ toilet.jpg**



When you run the exe directly, the error could be talking about the registry: You may very well need to run the game's setup or installer so the registry keys can be put into wine's 'windows registry'.

---

### Post by eimhin85 on 2010-09-13
> **weblordpepe said:**
> Hi dude.

When you are typing out files or directories (folders) that have a space in the name, you gotta put \ in front of the space.
Hiya, thanks, but as far as I am aware, placing the directory in between the "" has the same effect as using the \. correct me if i'm wrong though.
either way, i also tried doing:
```
gksudo wine "f:/Games/BGII\ -\ SoA/baldur.exe"
```and
```
gksudo wine f:/Games/BGII\ -\ SoA/baldur.exe
```but both give the same 'cannot find directory' error above.

> **weblordpepe said:**
> When you run the exe directly, the error could be talking about the registry: You may very well need to run the game's setup or installer so the registry keys can be put into wine's 'windows registry'.

I thought of this too so I also installed the game through wine on linux (vanilla, without mods) in the [wineprefix]C:/Games/BGII - SoA directory, then renamed the folder 'Games' to 'Gamesbkup' and made a symbolic link to the modded 'Games' folder from XP, but still no luck.

Secondly, to check whether it was a registry issue, i installed a 3rd win7 operating system on another separate hard drive, and tried to run from there, which worked successfully there too, so dont think its a registry thing. (the only thing i had to change in win7 to make it work was in the .ini file of the game. there is a section in the game's ini file that has: ```
[Alias] 
HD0:=F:\Games\BGII - SoA\ 
CD1:=F:\Games\BGII - SoA\CD1\ 
CD2:=F:\Games\BGII - SoA\CD2\;F:\Games\BGII - SoA\CD2\ 
CD3:=F:\Games\BGII - SoA\CD3\ 
CD4:=F:\Games\BGII - SoA\CD4\ 
CD5:=F:\Games\BGII - SoA\CD5\
```

And i had to change the Drive letters from F to H since the win7 install called it that.)

:S

---

### Post by weblordpepe on 2010-09-13
aha!

try typing:
**winepath /something/something/filename.jpg**

where filename.jpg is actually a file that exists. it will tell you the wine-version of that url. 
you could go:

**cd `winepath /windowsdrive/something\ something\something.exe`**
**wine something.exe**

sorry im just a little confused about what ya did with the registry. But anyways the Chitin.cpp error seems to be occuring in other situations on just windows machines. Ya might want to hit google and search for Chitin.cpp and have a look through those pages.

---

### Post by eimhin85 on 2010-09-14
Ok cool, Thanks!

That helped. that wine path thing helped show the problem.
 I can do 
cd /home/paul/.wine/dosdevices/f:/Games/BGII\ -\ SoA/ 
then
wine BGMain.exe

but i have to go through that directory, not the other one, .wine/drive_f

a launcher with
```
wine start /Unix "/home/paul/.wine/dosdevices/f:/Games/BGII - SoA/BGMain.exe" 
```works for me

cheers dude :)

---

