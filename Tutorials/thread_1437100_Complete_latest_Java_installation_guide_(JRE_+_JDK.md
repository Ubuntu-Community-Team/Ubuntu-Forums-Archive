---
title: "Complete latest Java installation guide (JRE + JDK)"
date: 2010-03-23
forum: Tutorials
---

### Post by EarthMind on 2010-03-23
This thread is an up-to-date compilation of what's mentioned in [this thread]("http://ubuntuforums.org/showthread.php?p=7488823").

> *Placeholders:*

**TYPE**: stands for i586 (32 bit) or x64 (64 bit)

*Notes:*

- I'll be using /home/user/Downloads as the default directory where the Java installation file is located and 6 update 21 ("6u21" and "1.6.0_21") as the Java version for this guide. Change these accordingly.

- This guide requires you to download the .bin Java installation file from the Java website at [http://www.java.com](http://www.java.com)

[SIZE="4"]**[COLOR="RoyalBlue"][SIZE="5"][B]J**[/SIZE]ava [SIZE="5"]**R**[/SIZE]untime [SIZE="5"]**E**[/SIZE]nvironment installation[/COLOR][/B][/SIZE]

[COLOR="DarkOliveGreen"]Step 1:[/COLOR] **Browse to the directory where you want to install java and create it if it doesn't already exist, for example /opt/java**

```
sudo mkdir /opt/java
cd /opt/java
```

[COLOR="DarkOliveGreen"]Step 2:[/COLOR] **Now make sure the file is executable**

```
chmod a+x /home/user/Downloads/jre-6u21-linux-**TYPE**.bin
```

[COLOR="DarkOliveGreen"]Step 3:[/COLOR] **Start the installation process**

```
sudo sh /home/user/Downloads/jre-6u21-linux-**TYPE**.bin
```

This displays the Java license agreement. Read through the agreement by pressing the Return button to display the next lines. At the end, enter **yes** to proceed with the installation.

This should've created the "/opt/java/jre1.6.0_21" directory.

[COLOR="DarkOliveGreen"]Step 4:[/COLOR] **Now copy all the files to the main /opt/java directory**

```
sudo cp -R /opt/java/jre1.6.0_21/* /opt/java
```

[COLOR="DarkOliveGreen"]Step 5:[/COLOR]** Lastly, delete the jre1.6.0_21 sub-folder**

```
sudo rm -r /opt/java/jre1.6.0_21
```

[COLOR="DarkOliveGreen"]Step 6:[/COLOR]
To install the plugin in your web browser we need to create a symbolic link in the Mozilla plugins folder. 

**32 bit JRE**

```
sudo ln -s /opt/java/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins
```

**64 bit JRE**

```
sudo ln -s /opt/java/lib/amd64/libnpjp2.so /usr/lib64/mozilla/plugins
```

This should have created a symbolic link in the chosen Mozilla plugins directory. Restart Firefox and/or Opera (or any other Java supported web browser) and test it out at: [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)

[COLOR="Green"][SIZE="3"]Congratulations, now you've successfully installed Java on your system but hold on as we're not done yet.[/SIZE][/COLOR]


[COLOR="DarkOliveGreen"]Last-and-optional-but-also-important step:[/COLOR]
To enable Java system-wide you'll have to add the directories to the PATH variable. Create a new shell file as the super user (for example java.sh):
```

sudo gedit

```
and add the below lines to the file and save it in the "/etc/profile.d" directory.

```
PATH=$PATH:/opt/java/bin
export PATH
```

[SIZE="4"][COLOR="Orange"]Next time you want to upgrade Java you just have to remove the existing Java directory
```
sudo rm -r /opt/java
```

And repeat steps 1 to 5.[/COLOR][/SIZE]

[SIZE="4"]**[COLOR="RoyalBlue"][SIZE="5"][B]J**[/SIZE]ava [SIZE="5"]**D**[/SIZE]evelopment [SIZE="5"]**K**[/SIZE]it installation[/COLOR][/B][/SIZE]

[COLOR="DarkOliveGreen"]Step 1:[/COLOR] **Browse to the directory where you want to install java and create it if it doesn't already exist, for example /opt/java**

```
sudo mkdir /opt/java
cd /opt/java
```

[COLOR="DarkOliveGreen"]Step 2:[/COLOR] **Now make sure the file is executable**

```
chmod a+x /home/user/Downloads/jdk-6u21-linux-**TYPE**.bin
```

[COLOR="DarkOliveGreen"]Step 3:[/COLOR] **Start the installation process**

```
sudo sh /home/user/Downloads/jdk-6u21-linux-**TYPE**.bin
```

This displays the Java (JDK) license agreement. Read through the agreement by pressing the Return button to display the next lines. At the end, enter **yes** to proceed with the installation.

This should've created the "/opt/java/jdk1.6.0_21" directory.

[COLOR="DarkOliveGreen"]Step 4:[/COLOR] **Now copy all the files to the main /opt/java directory**

```
sudo cp -R /opt/java/jdk1.6.0_21/* /opt/java
```

[COLOR="DarkOliveGreen"]Step 5:[/COLOR]** Lastly, delete the jdk1.6.0_21 sub-folder**

```
sudo rm -r /opt/java/jdk1.6.0_21
```

[COLOR="DarkOliveGreen"]Step 6:[/COLOR]
To install the plugin in your web browser we need to create a symbolic link in the Mozilla plugins folder. 

**32 bit JDK**

```
sudo ln -s /opt/java/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins
```

**64 bit JDK**

```
sudo ln -s /opt/java/jre/lib/amd64/libnpjp2.so /usr/lib64/mozilla/plugins
```

This should have created a symbolic link in the chosen Mozilla plugins directory. Restart Firefox and/or Opera (or any other Java supported web browser) and test it out at: [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)

[COLOR="Green"][SIZE="3"]Congratulations, now you've successfully installed Java (JDK) on your system but hold on as we're not done yet.[/SIZE][/COLOR]


[COLOR="DarkOliveGreen"]Last-and-optional-but-also-important step:[/COLOR]
To enable Java system-wide you'll have to add the directories to the PATH variable. Create a new shell file as the super user (for example java.sh):
```

sudo gedit

```
and add the below lines to the file and save it in the "/etc/profile.d" directory.

```
PATH=$PATH:/opt/java/jre/bin
export PATH
```

[SIZE="4"][COLOR="Orange"]Next time you want to upgrade Java (JDK) you just have to remove the existing Java directory
```
sudo rm -r /opt/java
```

And repeat steps 1 to 5.[/COLOR][/SIZE]

---

### Post by camn on 2010-09-16
This isn't working for me... Just saying I don't have Java installed.

---

### Post by TheSodicleOne on 2010-09-25
The JRE install doesn't work for me either. When I restart firefox and click the link I get "Verifying Java Version
Oops! You don't have the recommended Java installed.
Your Java version is Version 6 Update 20".
I had to do the following after using the above JRE instructions. I have only tested this on a 32 bit system, but should work on 64 bit.

1. Open a terminal window and copy and paste one line at a time...
Code:
sudo apt-get remove icedtea6-plugin sun-java6-jre
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/bin/java" 1
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/bin/java" 1
sudo update-alternatives --set java /opt/java/bin/java

2. Now check your java version...
Code:
java -version

3. Now install your Firefox plugin. This step can be repeated for additional users. The "mkdir" and "rm" commands may give an error depending on what java plugins you have installed, but won't hurt. Copy and paste...
Code:
mkdir ~/.mozilla/plugins
rm ~/.mozilla/plugins/libjavaplugin_oji.so
rm ~/.mozilla/plugins/libnpjp2.so

For 32 bit
Code:
ln -s /opt/java/lib/i386/libnpjp2.so ~/.mozilla/plugins/

For 64 bit
Code:
ln -s /opt/java/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

4. To check restart Firefox and type in the URL Bar...
Code:
about:plugins

I now get...
Java(TM) Plug-in 1.6.0_21

Hope this helps someone.

---

### Post by EarthMind on 2011-04-29
That's probably because you didn't follow the steps exactly. Make sure to remove the previous java installation first and then install the new one by following the steps above. Make sure you don't remove any essential directories afterwards.

---

### Post by schmoken on 2012-04-29
Firefox 3.6 and newer uses **libnpjp2.so** and not the old **libjavaplugin_oji.so**

---

