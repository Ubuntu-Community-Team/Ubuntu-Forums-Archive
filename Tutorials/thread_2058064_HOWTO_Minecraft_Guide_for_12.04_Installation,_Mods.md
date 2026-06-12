---
title: "HOWTO: Minecraft Guide for 12.04: Installation, Mods, and Troubleshooting"
date: 2012-09-14
forum: Tutorials
---

### Post by IWantFroyo on 2012-09-14
**Installing Minecraft**

*Step One:*

You have to purchase Minecraft from Minecraft.net, and make an account before you can install it. If you have an account, you can select to download the "Other Systems" file, which works with anything that can run Java. This is the version that we'll be using. It should be called "minecraft.jar" when it downloads.

*Step Two:*

Open your terminal, and run:
```
cd /home/<username>/<pathtominecraft>
```
```
chmod +x minecraft.jar
```

This allows you to run the .jar file. You are now able to do so. Right click, and select to open with a Java JRE. OpenJDK-6-JRE is the default, or you can install OpenJDK-7-JRE or use a PPA to get the official proprietary version.

*Step Three:*

You can create a startup script for Minecraft. This isn't necessary, but this will allow you to do things such as have Minecraft as a desktop icon, and customize how you start it up later on.

A hassle-free startup script. Just put it somewhere and save it as a BASH script (.sh).
```
java -jar /home/<username>/<pathtominecraft>
```

Congratulations! You're done installing!

**Conventional Mods:**

This is the simple and old-fashioned way to install Minecraft mods. No tools are needed other than a web browser, a file manager, a text editor, and the Archive Manager tool, all of which are already on your system.

This, of course, does not include mods that are only available through third-party tools, or rely on third party tools.

*Step One:*

Download the mod you're going to use. You should get a .zip file, which you can then extract (unless it's a texture pack, more on those later in the tutorial).

You should now have a folder full of Java files.

*Step Two:*

Now navigate to "/home/<yourusername>/.minecraft/bin"

In this folder, there is a file called "minecraft.jar"

This isn't the file that you run to start the game, and should not be confused with it. Make a copy of it, and keep the copy somewhere where you will remember it. This will come in handy if you mess up a mod install.

Now right click on the minecraft.jar file, and select "Open with Archive Manager".

Select "Edit->Add Files..."

Navigate over to the folder containing the mod, go inside it, "Select All" (Ctrl+A), and hit "Add".

Now, still in the Archive Manager, find the META-INF file, right click it, and select "Delete."

You can now exit the Archive Manager. The mod should now be installed. Start the game normally, and the mod should be active (although you may not see any immediate clues).

**Texture Packs:**

These aren't treated as normal mods, because you keep them in the .zip file after you download them (unless it's a set), and treat them differently.

*Step One:*

Download the texture pack, keeping them in the .zip format.

Move it into "/home/<yourusername>/.minecraft/texturepacks"

*Step Two:*

Open Minecraft, and go to Texture Packs. It will be in there, and all you do now is click on it.

**Troubleshooting and Tips**

*Black box:*

If you're using a 64 bit installation, and you just get a black box when you try to log in, change your minecraft.sh script to be:

```
#!/bin/bash
export LD_LIBRARY_PATH="/usr/lib/jvm/java-6-openjdk-amd64/jre/lib/amd64/"
java -jar /home/<yourusername>/<pathtominecraft>/minecraft.jar
```

Change the script for whatever version of Java you're using.

*FPS Is Really Low:*

Make sure that your graphics card driver is installed. Run the "Additional Drivers" application:
```
gtk-jockey &
```

Another option is to install the [OptiFine Mod](http://www.minecraftforum.net/topic/249637-132-optifine-hd-b3-fps-boost-hd-textures-aa-af-and-much-more/). It drastically improves your FPS. I used it myself and got tremendous success (gain of 2x).

If you think of anything I've missed, or want me to add something, please post or send me a message.

Happy Minecrafting!

---

### Post by iPyrOi on 2013-02-24
Hey, thanks for the guide! Just thought I'd share something I made. It's a simple Python script that lets you choose how much memory you want to allocate to Minecraft when you run it.
```
import os
os.system("clear")
y = 0;
x = raw_input("Would you like to launch Minecraft? [Y/N] ")
if(x == "N"):os.system("exit"),os.system("clear")
if(x == "Y"):y = input ("How much memory(gb) would you like to allocate to Minecraft? [1/2] ")
if(y == 1):os.system("java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame")
if(y == 2):os.system("java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame")
```

---

### Post by bannesen on 2013-04-20
How do you run the python script?

---

### Post by fluctuatinganomaly on 2014-03-26
Just want to comment on this, I don't get how to install mods as I do not have a ".minecraft" folder.

or ".Minecraft" or any format that folder does not exist.

in /home/usrname I have:

Desktop
Documents
Downloads
Minecraft (where I keep the minecraft.jar for running the game)
Music
Pictures
Public
Templates
Videos
Examples

There is no .minecraft folder. or at least none that I can see / acccess.

I don't get it :/

~Matt

-------------------EDIT

I apologise, I figured out how to get the location bar up so I can type /home/matt/.minecraft 
diredctly into the gui file browser :) forgive my stupidity

~Matt

-----------------EDIT 2

I'm sorry, I didn't realise this until just now, but how do I install forge on minecraft using the forget.jar

---

### Post by texaswriter on 2014-04-13
You can also type Control-H from Ubuntu [unity] file browser to show/hide hidden files and directories.

---

### Post by texaswriter on 2014-07-05
Sorry for the double post. I remember this thread after months and I had solved that problem. 

So, I actually had best luck installing minecraft to WINE (Codeweavers CROSSOVER, actually, but WINE should work as well). Then installing forge (easy executable), then all my addons. I was also able to run Minecraft from this bottle, but what I did to improve performance was copy that folder to where it would be installed in Linux (it was already installed in Linux, backed up, then overwrote)... This is how I have been using Forge with about 9 addons on Minecraft 1.7.2 for about 4 months now. Works beautifully. Let me know if this is not detailed enough (I can post more detailed instructions if needed)

---

