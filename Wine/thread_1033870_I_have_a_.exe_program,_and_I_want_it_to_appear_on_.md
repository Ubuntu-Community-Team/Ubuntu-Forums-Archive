---
title: "I have a .exe program, and I want it to appear on the applications menu"
date: 2009-01-07
forum: Wine
---

### Post by tegnoto89 on 2009-01-07
How do I do this?  I think I'm running it with wine, since it is a windows executable file (though I don't click open with wine very time and it still runs).  It doesn't appear under wine applications.  How can I make it?

---

### Post by jgoguen on 2009-01-07
> **tegnoto89 said:**
> How do I do this?  I think I'm running it with wine, since it is a windows executable file (though I don't click open with wine very time and it still runs).  It doesn't appear under wine applications.  How can I make it?
If you right-click the main menu (the Applications/Places/System part) you can choose **Edit Menus** and get a menu editor.  In here, you can browse to where you want this application to appear.  It can be in the Wine folder, or anywhere else.  Once you've gotten to where you want the application to show up, click the **New Item** button.  Leave **Type** as *Application*, put whatever you want for the **Name** (this is what appears in the menus) and **Comment** fields.  For the **Command** field, put **wine "/path/to/program.exe"**.  Include the quote marks if there are spaces in the path (which is very likely because most Windows programs install to Wine's C:\Program Files\...).  Click the wineglass icon if you want to search for and change the icon, and click **OK** when you're done.  The application will now appear in the menus wherever you put it.

HTH

---

### Post by tegnoto89 on 2009-01-07
Alright, I moved the program to my documents folder, and it opens there.  I added it to the wine menu, but when I try to open it from there, it says:

"Could not launch menu item

Failed to execute child process "/home/tom/Documents/Gameboy Roms/NO$GBA.EXE" (Permission denied)"

---

### Post by joshmuffin on 2009-01-08
You need to run it as root.

So you know, you there are GBA emulators for ubuntu, that would probably be easier.

---

### Post by tegnoto89 on 2009-01-08
How do I run it as root (besides from the terminal)?


I tried VBA express, but I couldn't run NDS files on any of them...

Any recommendations are still welcome, though.  I'll try something else.

---

### Post by Drubie on 2009-01-08
> **joshmuffin said:**
> 
So you know, you there are GBA emulators for ubuntu, that would probably be easier.

I use mednafen for both nes and gba - I found it in the repositories today actually.  so far it has worked like a charm!  of course, it is a command line thing, you have to open from the terminal, but it works great.
[color=white]blarg[/color]

---

### Post by joshmuffin on 2009-01-08
There are no nds emulators on ubuntu:'( i know, i tried.

I'm pretty sure that NO$GBA doesn't work through wine either but if you want to run it as root to try:

Press Alt + F2 and type

```
sudo /home/tom/Documents/Gameboy Roms/NO$GBA.EXE
```

And your good to go.

---

### Post by joshmuffin on 2009-01-08
I FOUND IT!

DeSmuME and it works on ubuntu. I haven't tried it but I think you should give it a go.

---

### Post by joshmuffin on 2009-01-08
Also google 'iDeaS nds emulator' I'm pretty sure it has a Linux candidate.

---

### Post by joshmuffin on 2009-01-08
Oh one last thing:

If you have some money:

Crossover Games
or
Cedega

May are like wine and may help you get it working.

---

### Post by tegnoto89 on 2009-01-08
Desmume didn't work for me - when I open and run a rom it doesn't do anything.

I think I'm alright with NO$GBA; I was just being OCD about being able to open it from the menu.

---

### Post by Drubie on 2009-01-08
> **Drubie said:**
> I use mednafen for both nes and gba - I found it in the repositories today actually.  so far it has worked like a charm!  of course, it is a command line thing, you have to open from the terminal, but it works great.
[color=white]blarg[/color]

wow, mednafen is great!  I can play nes games (mednafen is built off of FCEU) and GBA (built from VisualBoy) and others too!  check it out

However, if NO$GBA works for you, dont fix it if it aint broke.
[color=white]blarg[/color]

---

### Post by joshmuffin on 2009-01-08
OK

Then right click applications -> click edit menu's.

Find where you want it and click new item.\

Make the command 
[CODE]gksudo wine "/home/tom/Documents/Gameboy Roms/NO$GBA.EXE"CODE]

Click ok, and your good to go.

Give it a name (and comment if you wish)

Btw if you click the picture of the spring thing you can change its icon.

Hope that post was helpful:)

---

### Post by jocko on 2009-01-08
> **joshmuffin said:**
> OK

Then right click applications -> click edit menu's.

Find where you want it and click new item.\

Make the command 
```
sudo /home/tom/Documents/Gameboy Roms/NO$GBA.EXE
```Click ok, and your good to go.

Give it a name (and comment if you wish)

Btw if you click the picture of the spring thing you can change its icon.

Hope that post was helpful:)

That would never work.
1. You need wine to run a windows .exe file.
2. You can't use sudo in a starter (as sudo will ask for a password, but can't do so if it's not run in a terminal. gksudo will open up a gui password prompt).
3. You can't have spaces in a path, unless you put quotes around the entire path.

So, the command would be:
```
gksudo wine "/home/tom/Documents/Gameboy Roms/NO$GBA.EXE"
```But why and how would a windows program require root access in linux?
That sounds like very unlikely, and very unsafe if it was true.
And if it's working by just double-clicking the .exe file, why would it require different permissions to run it from a starter or command line?

---

### Post by joshmuffin on 2009-01-08
I don't know why but he gets a "Permission denied" error, running as root wont get that error. And yeah sorry about that last post. I was writing it for comand line and then changed it, the gksudo slipped past. And with the space thing, wow never new that trick.

---

### Post by tegnoto89 on 2009-01-08
To be honest, I'm not sure how I ended up with the exe file...  I was tinkering with several different emulators last night, and was having problems extracting and opening with wine, etc...

Anyway, it is a DOS/windows executable file -it says so under the properties.  And I just checked the "open with" tab, and wine program loader is selected, so I suppose that's why I can just click it to open.


Also, the gksu command didn't work either.. it gave me the message:

```
wine: cannot find '/home/tom/Documents/Gameboy Roms/NO.EXE'
```

---

### Post by Tim Sharitt on 2009-01-08
You may need to escape the space out of the folder name.
```
wine /home/tom/Documents/Gameboy\ Roms/NO.EXE
```

I see no reason to run as root, and would strongly advise against it.

---

### Post by joshmuffin on 2009-01-08
I know this file and I know its not dangerous.
The whole reason sudo or root came up is because of a permision denied error.
As for the file, change the directory and the filename. Move it to /home/tom/Documents and rename it to gba.exe ajust the code to 

```
gksudo wine "/home/tom/Documents/GBA.EXE"
```

And try again

---

### Post by jgoguen on 2009-01-08
The permission error is probably because it's not marked executable, not because he needs to run it as root.  Run this command to mark the file as executable:
```
chmod +x "/path/to/file"
```If you'd rather a graphical method:

[LIST]
[*]Open Nautilus and browse to the file
[*]Right-click the file, choose **[B]Properties**[/B]
[*]In the **[B]Permissions**[/B] tab, check the box labelled **Allow executing file as program**
[*]Push the **Close** button
[/LIST]

Another option, instead of marking it executable, is to explicitly run it through Wine:
```
wine "/path/to/file"
```Don't run it as root.  It's not necessary, and doing anything as root should be avoided unless it's actually necessary.

---

### Post by SeanHodges on 2009-01-08
Please read jgoguen's post.

Also, there is a dollar ($) sign in the filename. This character is reserved in file paths and you will get spurious errors until you rename it. Remove the $ from the name and adjust your launcher path accordingly.

```
mv "/home/tom/Documents/Gameboy Roms/NO\$GBA.EXE" "/home/tom/Documents/Gameboy Roms/NOGBA.EXE"
wine "/home/tom/Documents/Gameboy Roms/NOGBA.EXE"
```

---

### Post by jgoguen on 2009-01-08
Thanks, I completely missed that :)

---

