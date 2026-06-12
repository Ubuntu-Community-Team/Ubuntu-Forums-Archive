---
title: "[Tutorial] Manually installing the JDK 6 Update 13"
date: 2009-04-01
forum: Tutorials
---

### Post by James_Lochhead on 2009-04-01
**_[CENTER][SIZE="5"][Tutorial] Manually installing the JDK 6 Update 13[/SIZE][/CENTER]_**

[B][U][SIZE="4"]1) Introduction[/SIZE]
[/U][/B]
This tutorial is meant to help someone install the latest version of the JDK, currently the JDK 6 Update 13. Included in the tutorial is the installation of the JDK itself, as well as installation of the included JRE and Java Web Plugin for Firefox. The instructions may work for other versions of the JDK. Please use your own discretion when deciding whether to use this tutorial with other versions of the JDK. It should be noted that this tutorial also deals with the installation of the new 64 bit Java Web Plugin.

Also please note that this tutorial is meant to be very user friendly. If you are an advanced user you should be able to skim through in five minutes and get everything working.

If you have anything to add please post away.

_**[SIZE="4"]2) Uninstallation of the current JDK/JRE/Web Plugin[/SIZE]**_

**_[SIZE="2"]2.1)Uninstallation of the current Sun JDK/JRE/Web Plugin[/SIZE]_**

If you have the currently have the Sun JDK installed you need to remove it. Use the following command in the terminal:

**Note: If you are currently using some or all of these packages please note down which ones so you can revert if need be.**

```

sudo apt-get remove sun-java6-jre sun-java6-jdk sun-java6-bin

```

If you installed the Sun Java Web Plugin and made it default you will have to remove it as well using the terminal command:

**Note: If you are currently using this package please note it down so you can revert if need be.**

```

sudo apt-get remove sun-java6-plugin

```[B]
Note: If you made the Sun Java Web Plugin default you will either have to make the IcedTea Java Web Plugin default (not covered here) or make the new Sun Java Web Plugin default (covered in the optional section "Setting up the Java Web Plugin").[/B]
[SIZE="2"][B][U]
2.2) (Optional) Uninstallation of the OpenJDK/JRE/IcedTea Web Plugin[/U][/B][/SIZE]

By default Ubuntu comes with the OpenJDK JRE, IcedTea Java Web Plugin and a few other dependant packages. If you leave these packages and do not complete any of the optional sections these packages will still be used by default in everything but the terminal. However, if you are like me and do not want multiple versions of Java lying around taking up hard disk space then you can remove them using the following terminal command:

**Note: You will not necessarily have all these packages installed. If you are missing some please note down which ones so you can revert properly if need be.**

```

sudo apt-get remove openjdk-6-jre openjdk-6-jre-headless icedtea-6-jre-cacao icedtea6-plugin default-jre default-jre-headless icedtea-gcjwebplugin

```
[B][U][SIZE="2"]
2.3) Removal of unnecessary packages[/SIZE][/U][/B]

Everything should have been uninstalled correctly. However, to make sure we do not have any additional unused packages around that we no longer need, type the following in the terminal:

```

sudo apt-get autoremove

```
[B][U]
[SIZE="4"]3) Download of the correct JDK bin file[/U][/B][/SIZE]

Go to [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) in your browser. On this page the current JREs and JDKs are listed along with some other tools. This tutorial was built for the the JDK 6 Update 13. However, it will probably work for newer/older updates of the 6 series as well. If there is a newer JDK available you may want to grab it and adapt the tutorial.

After choosing the appropriate JDK click on the download link next to it. If you use i386 (32 bit) Ubuntu you will want to download the &#8220;Linux&#8221; version on the next page, however if you are on amd64 (64 bit) Ubuntu you will want to download the &#8220;Linux x64&#8221; version.

Once the JDK file (jdk<something>.bin) has finished downloading you need to move it to your home directory.

_**[SIZE="4"]4) Extract and install the bin file[/SIZE]**_

Open a terminal and type the following commands:

```

chmod +x jdk*.bin
sudo ./jdk*.bin

```

Before the bin file will extract you have to agree to the terms and conditions (by typing yes or no). To skip through the agreement simply press q.

Now you have an extracted JDK directory (with root ownership) in your home directory. Now we need to move it to somewhere a little more appropriate. I moved mine to /usr/local/. If you are an advanced user you can pretty much put in anywhere you want. Just make sure you adapt the tutorial accordingly.

At this point please note down the name of the JDK folder in your home folder, you will need to type it in for later commands. For me the name of the folder is :

```

jdk1.6.0_13 

```

Henceforth the folder will be refered to as <JAVA_FOLDER>. If you see <JAVA_FOLDER> in any of the commands replace it with the folder name.

To move the JDK folder to /usr/local/ type the following in the terminal. 

```

sudo mv <JAVA_FOLDER>/ /usr/local/

```

**_[SIZE="4"]5) Setting up the JAVA_HOME and PATH variables[/SIZE]_**

In order to use the various Java terminal commands (such as java & javac) with the JDK that we just installed the JAVA_HOME and PATH variables need to be set. This involves editing a text file, however, you have to edit a different text file depending on whether you want to set up the variables system wide or just for an individual user.

**Please note down which file you edited in case the settings need to be removed.**

**_[SIZE="2"]5.1) Settings the variables up system wide[/SIZE]_**

To set the variables up system wide either the /etc/profile file or the /etc/bash.bashrc need to be edited. The difference between these files is that the former is loaded once when you log in, whereas the latter is loaded every time time you start a new terminal.

**Please be careful when adding the PATH line. If you execute the command without the $PATH: part then your terminal will stop working properly.**

To edit the /etc/profile file type the following in the terminal:

```
 
sudo -i
echo "export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java" >> /etc/profile
echo "export PATH=$PATH:/usr/local/<JAVA_FOLDER>/bin" >> /etc/profile
exit

```
**Note: It is important to type exit here.**

Alternatively, to edit the /etc/bash.bashrc file type the following in the terminal:

```
 
sudo -i
echo "export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java" >> /etc/bash.bashrc
echo "export PATH=$PATH:/usr/local/<JAVA_FOLDER>/bin" >> /etc/bash.bashrc
exit

```
**Note: It is important to type exit here.**

**If you accidentally added an incorrect PATH variable press alt+f2, type: gksudo nautilus, navigate to the /etc directory and remove the offending line (at the bottom of the file) using a text editor.**

**_[SIZE="2"]5.2 Settings the variables up for a single user[/SIZE]_**

To set the variables for a single user the $HOME/.profile file or $HOME/.bashrc file need to be edited. The difference between these files is that the former is loaded once when you log in, whereas the latter is loaded every time time you start a new terminal.

To edit the $HOME/.profile file type the following in the terminal: 

```
 
echo "export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java" >> $HOME/.profile
echo "export PATH=$PATH:/usr/local/<JAVA_FOLDER>/bin" >> $HOME/.profile

```

Alternatively, to edit the $HOME/.bashrc file type the following in the terminal:

```
 
echo "export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java" >> $HOME/.bashrc
echo "export PATH=$PATH:/usr/local/<JAVA_FOLDER>/bin" >> $HOME/.bashrc

```

**If you accidentally added an incorrect PATH variable open your home folder, press ctrl.h and remove the offending lines (at the bottom of the file) using a text editor.**

[SIZE="2"]**_5.3) Testing the changes_**[/SIZE]

Depending on the file that you edited you will either have to start a new terminal or log in and out for the changes to take effect. Once you have either logged in and out or started a new terminal test the java commands that you use to see if they are working. If they are not something has gone wrong with the installation.   

[SIZE="2"]**_5.4) A point of interest_**[/SIZE]

If you complete the (optional) section "Setting up the default JRE" this section may not actually be necessary for use of the java command. However, it is necessary for any other commands you want to use, such as javac.

**_[SIZE="4"]6) (Optional) Setting up the default JRE[/SIZE]_**

**If you decided to remove the default JRE (OpenJDK JRE) this section is necessary for Java applications to run correctly. However, if you want to keep the OpenJDK as default do not do this section.**

To set up the new JRE as default type the following in the terminal:

```

sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/<JAVA_FOLDER>/jre/bin/java" 1
sudo update-alternatives --set java /usr/local/<JAVA_FOLDER>/jre/bin/java

```
[B][U][SIZE="4"]
7) (Optional) Setting up the Java Web Plugin
[/SIZE][/U][/B]
[B]
If you removed the OpenJDK JRE and the IcedTea Java Web Plugin you need to complete this section for Java applets to work in your browser. However, if you left the OpenJDK JRE and IcedTea Java Web Plugin you may want to skip this section.[/B]

The commands are different for the i386 and amd64 architectures. Please follow the 32 bit section if you have Ubuntu i386 and the 64 bit version if you have Ubuntu amd64.  

**Just in case the following does not work please write down the original settings in the about:config section.**

**_[SIZE="2"]7.1) 32 bit[/SIZE]_**

```

sudo mkdir /usr/lib/mozilla/plugins
sudo ln -s /usr/local/<JAVA_FOLDER>/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/


```

Now restart Firefox, Open Tools > Add-ons > Plugins and enable libjavaplugin_oji. **If you are still having problems with Java applets complete the following steps:**

Type the following into the Firefox URL input box:

```

about:config 

```

Next click agree. In the search box at the top on the next page type in java. Somewhere in this list is an entry for java.java_plugin_library_name. You must change this to:

```

libjavaplugin_oji

```

In the same list there is an entry for java.default_java_location_others. You must change this to:

```

/usr/local/<JAVA_FOLDER>/jre/

```

**_[SIZE="2"]7.2) 64 bit[/SIZE]_**

```

sudo mkdir /usr/lib/mozilla/plugins
sudo ln -s /usr/local/<JAVA_FOLDER>/jre/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/

```

Now restart Firefox, Open Tools > Add-ons > Plugins and enable libnpjp2. **If you are still having problems with Java applets complete the following steps:**

Type the following into the Firefox URL input box:

```

about:config 

```

Next click agree. In the search box at the top on the next page type in java. Somewhere in this list is an entry for java.java_plugin_library_name. You must change this to:

```

libnpjp2

```

In the same list there is an entry for java.default_java_location_others. You must change this to:

```

/usr/local/<JAVA_FOLDER>/jre/

```

_**[SIZE="4"]8) Reversion[/SIZE]**_

In order to revert to the please follow the following steps.

**_[SIZE="2"]8.1) Uninstallation of the new Sun JDK[/SIZE]_**

To remove the folder for the new Java Sun JDK you need to type the following in the terminal:

```
sudo rm -r /usr/local/<JAVA_FOLDER>/
```

**_[SIZE="2"]8.2) Removal of the PATH and JAVA_HOME variables[/SIZE]_**

You now need to remove the settings from the file you edited when you set these variables. If you edited one of the files in your home folder you need to do the following:

Open the home folder in the file browser, press ctrl.h (reveal hidden files) and open the correct file in a text editor. Then remove the lines that you added (down the bottom of the file).

If you edited one of the files in the /etc directory you need to press alt+f2, type gksudo nautilus and press enter. Now navigate to the /etc directory, open the correct file in a text editor and remove the lines that you added.

**_[SIZE="2"]8.3) Install the previous versions of the JDK/JRE/Web Plugin[/SIZE]_**

To install the versions of the JDK/JRE/Web Plugin that you had before you need to complete the section "2) Uninstallation of the current JDK/JRE/Web Plugin" in reverse. Rather than typing:

```
sudo apt-get remove <package1> <package2>...
```

In the terminal. You need to type:

```
sudo apt-get install <package1> <package2>...
```

Please do not simply copy and paste the commands from the uninstallation section and change remove to install. If you remember I said note down the packages that you actually had installed in that section. Please only install the packages that you actually had before.

**_[SIZE="2"]8.4) (Optional) Set up the previous JRE as default[/SIZE]_**

If you set up the new Sun Java JRE as default you will need to complete this step to revert.

To complete this step type the following in the terminal:

```
sudo update-alternatives --config java
```

You will now see a list of options for JREs to use. You need to choose the option that maps to the previous version of the JRE you were using (likely to be the OpenJDK).

**_8.5) (Optional) Set up the previous Java Web Plugin_**

If you set up the new Sun Java Web Plugin you will need to complete this step to revert.

**If you are using 32 bit Ubuntu type the following in the terminal:**

```
sudo rm /usr/lib/mozilla/plugins/libjavaplugin_oji.so
```

**If you are using 64 bit Ubuntu type the following in the terminal:**

```
sudo rm /usr/lib/mozilla/plugins/libnpjp2.so
```

If you had to set up any of the settings in the about:config section (you should have noted the originals down) please change these back to the originals.

---

### Post by James_Lochhead on 2009-04-01
This is an updated version of the tutorial I posted yesterday.

---

### Post by slavik on 2009-04-01
it's a decent tut but be careful in case you want to revert.

---

### Post by James_Lochhead on 2009-04-02
Updated with a section on how to revert.

---

### Post by James_Lochhead on 2009-04-02
Just updated to Jaunty. Update 13 is installed by default. This tutorial should be applicable to future releases of the 6 series though.

---

### Post by binbash on 2009-04-02
Excellent howto, jaunty comes with latest but works great on my intrepid box.

---

### Post by Wickedone on 2009-04-08
Thanks James,

You saved me some time looking up the system wide variables.  I just setup a simple server and wanted to have Java without all the baggage installing it through the repos brings.  I didn't want to install X11, or any other junk, just Java.  

Your timing couldn't have been better.  

Wicked

---

### Post by OGpmpdog on 2009-04-12
Thank you very much for the knowledge.

However, as a Linux beginner, those step by step instructions are VERY intimidating.

The biggest obstacle to total linux conversion: software installation, which is far easier to do in Windows.

Dont get me wrong...I finally mastered joining video files in Linux - without having to jump to **Shitsa**.:lolflag:

I'm slowly evolving to the Linux world...

When is Jaunty Jackolope gonna be released?

---

### Post by James_Lochhead on 2009-04-12
It is not really a process for a beginner, although I tried to make it as easy as possible. Jaunty will be released on the 23rd so there is hardly much point doing this process now if you are planning to upgrade.

---

### Post by OGpmpdog on 2009-04-12
> **James_Lochhead said:**
> It is not really a process for a beginner, although I tried to make it as easy as possible. Jaunty will be released on the 23rd so there is hardly much point doing this process now if you are planning to upgrade.

Thanks for replying.

Dont wanna derail the thread but is Jaunty a significant upgrade or just a sequel?

Peace

---

### Post by James_Lochhead on 2009-04-13
Jaunty is more of a sequel. A new version of Ubuntu comes out every 6 months, with all the latest applications and a few new features.

The changes are not as dramatic as say an upgrade from Windows XP to Windows Vista. In my opinion, this is a better way of working things as you can iron out annoying features and bugs better this way.

---

### Post by FailureToLoad on 2009-04-16
Wow, I could have saved myself a lot of woes by just using this earlier lol. Will going through this installation give me the option of opening a jar file with the SUN JDK 6?

---

### Post by James_Lochhead on 2009-04-16
Yes it will. At this point I would recommend just upgrading to Jaunty though (only a week till it comes out).

---

### Post by andreicostache1986 on 2009-04-26
Hello, I have just upgraded from Ubuntu 8.10 to 9.04 and I have a problem. My Eclipse IDE is not able to see my JDK Root and I do not know where to find it. I have trying every sun-java6 folder in /usr/share/doc, but no luck. I would appreciate any help on this.
(I have I am posting where I should, because this I have just registered and have never posted before, excuse any mistakes please :-) ).

Thanks in advance.

---

### Post by James_Lochhead on 2009-04-26
Hi,

It would have been better from your perspective to post in the general help or programming sections as you would have got a lot faster response (I only check this thread every few days). Posting here is not a problem though.

I have looked in to this and I believe the directory you want is:

/usr/lib/jvm/java-6-sun-1.6.0.13

That is where the JDK is installed from the package. 

I am not an expert on Eclipse by any means, however, I do use it for a Java course that I do and I do not think it should be necessary to put in the directory if everything is set up properly. It should just be a case of clicking the launcher (if using the old Eclipse in the repos) or launching a script (if using a new manually installed version).

If entering the path to the JDK does not help you may want to make a thread specifically about the problem in the general help or programming sections.

---

### Post by MadCatmkII on 2009-12-28
Thanks for this. Now I can finally install the javaEE SDK!

ps.

Does anyone understand why Sun supplies an installation-program for the SDK but not for the JRE or JDK? After all, this is almost 2010, not 1995!

---

### Post by tnagya on 2012-09-28
Hi, I had to use the following line I found on [this link]("http://www.java.com/en/download/help/linux_install.xml#enable") to enable Java in my Firefox on a clean Ubuntu 12.04 install:

```
sudo ln -s /usr/local/jdk1.6.0_35/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/

```

instead of:

```
sudo ln -s /usr/local/jdk1.6.0_35/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
```

I am not sure if the older one is still needed.

Thanks for the tutorial btw.
Cheers

---

### Post by Toz on 2012-09-28
This thread is almost 3 years old. I'm certain the posters have moved on.
Closing.

---

