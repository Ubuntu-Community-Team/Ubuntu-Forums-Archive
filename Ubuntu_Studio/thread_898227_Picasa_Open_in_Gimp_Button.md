---
title: "Picasa: Open in Gimp Button?"
date: 2008-08-23
forum: Ubuntu Studio
---

### Post by computergee on 2008-08-23
Hi,
I use Picasa to organize and view my photo collection, but I often edit them using GIMP. I found this custom button for Picasa to send the selected picture to GIMP, but it is windows only.

[http://www.swadling.com.au/index.php/blake/blake-projects/gimp-picasa-button](http://www.swadling.com.au/index.php/blake/blake-projects/gimp-picasa-button)

Can anyone figure out how to edit the script to launch the native GIMP in linux? Adding the button is no problem, simply copy the pbz file to the buttons folder in the picasa directory (~/.picasa/drive_c/Program Files/Picasa/buttons). Editing the script is easy as well, just open the pbz file with an archiving program, and use a text editor to edit the pbf file. I can't figure out how to direct the script to launch the linux gimp binary. Any help guys?

---

### Post by mixersoft on 2008-11-25
Did you ever figure this out? I'm trying to get a picasa button to launch a shell script in linux. Would love some help here.

I've tried to modify the .pbz script to 

[INDENT]
[LIST]
[*]run a .bat file in wine with the path set to 'c:\' and the .bat file in "/opt/google/picasa/3.0/wine/drive_c", and also

[*]run a shell script with chmod 777 in a normal linux folder.
[/LIST] 
[/INDENT]

I don't really know much about wine, but neither seemed to work. But I can launch a .bat script from a picasa button in Win32 no problem.

m.

---

### Post by Wisp2006 on 2008-11-26
I don't think that a wine emulated application can call an Unix installed executable. You can try to install them both in Wine.

---

### Post by jakobb on 2009-10-14
I think I have the solution, I have copied from the picflick pearlscript.
It is not quite done yet, but as I don't know any pearl, I have to experiment to get it. 

I will tell you when I get it working

---

### Post by jakobb on 2009-10-15
My button is sort of working now.
It outputs the wine directory of the picture to a pearlexecutable named gimpopen.
gimpopen is supposed to convert the wine directory to a native linux direcory. (right no it gives something that involves the z:/ drive from wine)

gimpopen can then execute "gimp /the/folder/of/the_picture.jpg"
(or /the/wine/directory/z/the/folder/of/the_picture.jpg )

I made this only by modifying already existing scripts/buttons, so it might have some copyright issues.
This also means, that atm, it can only open the first, if multiple images is selected. However, it does that very clean

---

### Post by Mr_Bumpy on 2009-11-16
jakobb, would you mind sharing your script with us?  I am interested to try it out.  TIA :)

---

### Post by jakobb on 2009-11-21
Hi, I have zipped the files and you can get them here: [http://jbergj.dk/ubuntu/gimpopen.7z]("http://jbergj.dk/ubuntu/gimpopen.7z") 

I modyfied the PBZ from the windows version to open a excecutable script within the Wine C-drive the picasa is installed under.

My Picasa is installed under the Cdrive of ies4linux (this allows me to use the facebookuploader which is using internet explorer)

the file called gimpopen is made by modifying "picflick" that changes the wine path to a native linux path.
It does not get the filelink from your home folder, but a long link through the wine directory. You will notice this when you succesfully opens a file in gimp.

If you select more than more file and press the button, only one will be opened, this can be fixed, but I wont fix it in the nearest future, so if any of you guys feels like improving it, then go for it.

Anyway, I hope some of you find this useful.
Jakob

---

### Post by jakobb on 2009-11-22
instead of usin ies4 linux I reccomend this solution
```
wget http://www.kegel.com/wine/winetricks
sh winetricks ie6

```

---

### Post by Mr_Bumpy on 2009-11-27
I was unable to get this to work with the Linux version of Picasa, and I think it's because Google's WINE implementation for Picasa doesn't map the C: drive, only a my Documents folder and "/" (at least that's only what it shows when I try to add a new file through Picasa).  I could put the gimpopen script somewhere else, but I don't know what I should change "c:\\gimpopen" to in the button config file.  Also, should I assume that specifying PICASA_WINE_DIR="/opt/google/picasa/3.0/wine/drive_c" in gimpopen will work for the rest of the script?

---

### Post by jakobb on 2009-11-30
I don't know how about the linux version.
I don't use it because it is only version 3.0 and the win version is 3.5

So that is why I use the windows version under WINE

You should unzip the gimp button and point it to the script that opens gimp (make sure it is excecutable) and zip the the files back to the picasa button

---

