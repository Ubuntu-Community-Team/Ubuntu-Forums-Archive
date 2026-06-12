---
title: "Minecraft Java 7 Problem"
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by RocketPenguin on 2012-04-05
I am no expert to ubuntu so please explain answers carefully. I can not get minecraft to work with openjdk 7 and can't get openjdk 6 either. What can I do to be able to play minecraft???? If you have any questions, just reply!

---

### Post by Sworddragon on 2012-04-05
Try to start Minecraft in a terminal and post the error message here.

---

### Post by kaldor on 2012-04-05
It works for me after a slight adjustment. I'll just start from scratch. I'm assuming you're using the 64 bit version of Ubuntu 12.04.

Make sure OpenJDK 7 JRE is installed: ```
sudo apt-get install openjdk-7-jre
```

If you get a black screen or errors on login, try this...

1- Open a terminal.

2- Run this command: ```
export LD_LIBRARY_PATH="/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64"
```


3- Change to the directory that *minecraft.jar* is located. Run the *java -jar minecraft.jar* command. If you're unsure how to change directory via the terminal, post back.


This does it for me :)

---

### Post by RocketPenguin on 2012-04-05
> **Sworddragon said:**
> Try to start Minecraft in a terminal and post the error message here.
please tell me how. i do not know.

---

### Post by RocketPenguin on 2012-04-05
unsure how....

---

### Post by kaldor on 2012-04-05
Okay, I'll guide you through it :)

The terminal is the Linux command line interface. You can type commands in it similar to that on Terminal.app on OS X or the Command Prompt on Windows. It's not really as scary as it sounds.

Assuming you're using the default Ubuntu desktop, click on the Ubuntu logo on the top left to bring up the "dash". Type *terminal* and press enter. You should get a little purple window with something like *yourname@yourPC:~$* 

Post back if you need any more explanations!

---

### Post by RocketPenguin on 2012-04-05
> **kaldor said:**
> Okay, I'll guide you through it :)

The terminal is the Linux command line interface. You can type commands in it similar to that on Terminal.app on OS X or the Command Prompt on Windows. It's not really as scary as it sounds.

Assuming you're using the default Ubuntu desktop, click on the Ubuntu logo on the top left to bring up the "dash". Type *terminal* and press enter. You should get a little purple window with something like *yourname@yourPC:~$* 

Post back if you need any more explanations!
i know that much. i know my terminal and sudo-apt and all that i didn't get the change the minecraft.jar directory.

---

### Post by kaldor on 2012-04-05
> **linux junkie said:**
> i know that much. i know my terminal and sudo-apt and all that i didn't get the change the minecraft.jar directory.

Okay, good. Which directory (folder) is your minecraft.jar located in?

To change directories in a Terminal, you use the *cd *command. So, if your Minecraft.jar is in your "Downloads" folder, then type *cd Downloads* 

cd means "Change Directory" and you literally just tell your PC "change directory to Downloads".

---

### Post by RocketPenguin on 2012-04-05
> **kaldor said:**
> Okay, good. Which directory (folder) is your minecraft.jar located in?

To change directories in a Terminal, you use the *cd *command. So, if your Minecraft.jar is in your "Downloads" folder, then type *cd Downloads* 

cd means "Change Directory" and you literally just tell your PC "change directory to Downloads".
  The jar that i would start the game with or the one in the bin?

---

### Post by kaldor on 2012-04-05
> **linux junkie said:**
> The jar that i would start the game with or the one in the bin?

Yep, the one you start the game with. I'm assuming you simply grabbed the .jar from minecraft.net

---

### Post by RocketPenguin on 2012-04-05
> **kaldor said:**
> Yep, the one you start the game with. I'm assuming you simply grabbed the .jar from minecraft.net
ok. so just tell me a the commands that i would have to type in. I tried cd desktop (thats were it is saved) and it brought up an error or something like that.

---

### Post by kaldor on 2012-04-05
> **linux junkie said:**
> ok. so just tell me a the commands that i would have to type in. I tried cd desktop (thats were it is saved) and it brought up an error or something like that.

Yeah, it's case-sensitive. Desktop is not the same as desktop. 

so, it should be like this (highly recommend you copy and paste instead of typing yourself):

Change to desktop:
```
cd Desktop
```

Check to be sure that OpenJDK is installed:
```
sudo apt-get install openjdk-7-jre -y
```

Hopefully fix Black Screen issue:
```
export LD_LIBRARY_PATH="/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64"
```

Mark minecraft.jar as executable:
```
chmod +x minecraft.jar
```

Launch Minecraft:
```
java -jar minecraft.jar
```

You shouldn't need to use the Terminal too much while using Ubuntu. It's just much easier to have you copy/paste commands than to guide you through a load of menus that I can't remember off-hand :)

---

### Post by RocketPenguin on 2012-04-06
> **kaldor said:**
> Yeah, it's case-sensitive. Desktop is not the same as desktop. 

so, it should be like this (highly recommend you copy and paste instead of typing yourself):

Change to desktop:
```
cd Desktop
```Check to be sure that OpenJDK is installed:
```
sudo apt-get install openjdk-7-jre -y
```Hopefully fix Black Screen issue:
```
export LD_LIBRARY_PATH="/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64"
```Mark minecraft.jar as executable:
```
chmod +x minecraft.jar
```Launch Minecraft:
```
java -jar minecraft.jar
```You shouldn't need to use the Terminal too much while using Ubuntu. It's just much easier to have you copy/paste commands than to guide you through a load of menus that I can't remember off-hand :)
thank you!!! it worked. now one more question. can i make minecraft an icon? some reason i cannot open it without haveing to type in the commands. (via open with.... java 7 runtime)

---

### Post by RocketPenguin on 2012-04-06
And to me, terminal is my favorite. everything is done in there, everything can be done in there. It tells you the error in there. And all you have to do is copy and paste! though i can only open minecraft at the moment like that.....

---

### Post by RocketPenguin on 2012-04-18
I have tried to install minecraft many ways now, all from the Internet. But i always get the black screen. Could someone tell me how to, run, install and never have problems with minecraft again???

---

### Post by jfernyhough on 2012-04-18
1) Install Java. I'd recommend trying OpenJDK 7 first:
$ sudo apt-get install openjdk-7-jre

2) Download the Minecraft launcher and save it somewhere sensible:
[https://s3.amazonaws.com/MinecraftDownload/launcher/minecraft.jar](https://s3.amazonaws.com/MinecraftDownload/launcher/minecraft.jar)

3) Right-click on the .jar file you just downloaded and select "Open with OpenJDK 7 runtime"

4) Wait for the launcher to log and then log in.

If OpenJDK doesn't work you can try Oracle's Java 7.
$ sudo apt-add-repository **ppa:webupd8team/java**
$ sudo apt-get update
$ sudo apt-get install[B][B] oracle-java7-installer

[/B][/B]Then try step 3 again but select "Oracle Java 7 runtime" instead.

---

### Post by mörgæs on 2012-04-18
Threads merged.

---

### Post by pbrane on 2012-04-18
minecraft runs perfectly fine with Openjdk-7. A better command line to run minecraft is

```

java -Xms512M -Xmx1G -cp /path/to/minecraft/minecraft.jar net.minecraft.LauncherFrame

```

the minecraft.jar here is the launcher, NOT the minecraft binary itself. Do you have any mods installed? If you do, did you delete the META-INF directory in the minecraft binary?

---

### Post by RocketPenguin on 2012-04-18
> **mörgæs said:**
> Threads merged.
I have tried all of those. Ubuntu soots me best. Though Ubuntu is the first i have tried to install Minecraft on.

---

### Post by RocketPenguin on 2012-04-18
> **pbrane said:**
> minecraft runs perfectly fine with Openjdk-7. A better command line to run minecraft is

```

java -Xms512M -Xmx1G -cp /path/to/minecraft/minecraft.jar net.minecraft.LauncherFrame

```the minecraft.jar here is the launcher, NOT the minecraft binary itself. Do you have any mods installed? If you do, did you delete the META-INF directory in the minecraft binary?
no mods yet. And i might not be using the command correctly, but it brought up an error Error: Could not find or load main class net.minecraft.LauncherFrame

---

### Post by RocketPenguin on 2012-04-18
> **jfernyhough said:**
> 1) Install Java. I'd recommend trying OpenJDK 7 first:
$ sudo apt-get install openjdk-7-jre

2) Download the Minecraft launcher and save it somewhere sensible:
[https://s3.amazonaws.com/MinecraftDownload/launcher/minecraft.jar](https://s3.amazonaws.com/MinecraftDownload/launcher/minecraft.jar)

3) Right-click on the .jar file you just downloaded and select "Open with OpenJDK 7 runtime"

4) Wait for the launcher to log and then log in.

If OpenJDK doesn't work you can try Oracle's Java 7.
$ sudo apt-add-repository **ppa:webupd8team/java**
$ sudo apt-get update
$ sudo apt-get install[B][B] oracle-java7-installer

[/B][/B]Then try step 3 again but select "Oracle Java 7 runtime" instead.
It gave me the same old black screen.

---

### Post by pbrane on 2012-04-19
> **linux junkie said:**
> no mods yet. And i might not be using the command correctly, but it brought up an error Error: Could not find or load main class net.minecraft.LauncherFrame

Sounds like the file you are trying to run is not the minecraft launcher.
This link might help: [http://www.minecraft.net/download]("http://www.minecraft.net/download")

---

### Post by RocketPenguin on 2012-04-19
> **pbrane said:**
> Sounds like the file you are trying to run is not the minecraft launcher.
This link might help: [http://www.minecraft.net/download](http://www.minecraft.net/download)

that is where i got it from. twice.

---

### Post by pbrane on 2012-04-20
> **linux junkie said:**
> that is where i got it from. twice.

Not sure why it won't run. I use that command line everytime I run minecraft. (every day). Make sure the path is correct. for example, if you have minecraft.jar in /home/linuxjunkie/bin the command line would be **java -Xms512M -Xmx1G -cp /home/linuxjunkie/bin/minecraft.jar net.minecraft.LauncherFrame**

I did a **mkdir bin** in my home directory. I have the launcher in that directory because **/home/bin** is in the search path by default. Once you run the minecraft jar file successfully it will build the **~/.minecraft** directory and populate it with the necessary files and sub-directories.

---

### Post by RocketPenguin on 2012-04-21
> **pbrane said:**
> Not sure why it won't run. I use that command line everytime I run minecraft. (every day). Make sure the path is correct. for example, if you have minecraft.jar in /home/linuxjunkie/bin the command line would be **java -Xms512M -Xmx1G -cp /home/linuxjunkie/bin/minecraft.jar net.minecraft.LauncherFrame**

I did a **mkdir bin** in my home directory. I have the launcher in that directory because **/home/bin** is in the search path by default. Once you run the minecraft jar file successfully it will build the **~/.minecraft** directory and populate it with the necessary files and sub-directories.
when i typed the command, I got this: Error: Could not find or load main class net.minecraft.LauncherFrame

---

### Post by pbrane on 2012-04-21
> **linux junkie said:**
> when i typed the command, I got this: Error: Could not find or load main class net.minecraft.LauncherFrame

I don't think you are using the correct path to the minecraft jar file. You **have to** use the correct path or this won't work. As an alternative, in a terminal, you can ***cd*** into the directory where you have downloaded the minecraft jar file and type
```

java -Xms512M -Xmx1G -cp minecraft.jar net.minecraft.LauncherFrame

```

---

### Post by RocketPenguin on 2012-04-21
> **pbrane said:**
> I don't think you are using the correct path to the minecraft jar file. You **have to** use the correct path or this won't work. As an alternative, in a terminal, you can ***cd*** into the directory where you have downloaded the minecraft jar file and type
```

java -Xms512M -Xmx1G -cp minecraft.jar net.minecraft.LauncherFrame

```
So if I have it on my desktop, is this not correct; cd Desktop ?

---

