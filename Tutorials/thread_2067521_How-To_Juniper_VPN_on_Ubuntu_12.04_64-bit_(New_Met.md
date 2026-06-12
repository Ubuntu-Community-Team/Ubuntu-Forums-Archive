---
title: "How-To: Juniper VPN on Ubuntu 12.04 64-bit (New Method)"
date: 2012-10-07
forum: Tutorials
---

### Post by nyteryder79 on 2012-10-07
*Note: This guide uses Oracle Java 7.  This also may not work if you use SecureID.  I have tested this with standard username and password only.*

**Summary:**
[INDENT]Basically, the way I got this to work was to install Oracle Java 7 both 64bit and 32bit versions.  Then I install a second Firefox which I am dubbing as 32bit with the 32bit Java plugin soft-linked.  I then set the 64bit version of Java as default system-wide and then create a new icon for what I'm calling the 32bit version of Firefox in the launcher.  So now, when the 32bit version of Firefox is launched, I'll log into my Juniper VPN website like normal and the 32bit version of Java is used allowing the Juniper client to install and run properly.  This probably isn't the best way to do this, but it works quite well.[/INDENT]

**Preparation:**
[INDENT]If using OpenJava, I recommend that you purge your current java install:
```
sudo apt-get purge openjdk-\* icedtea-\* icedtea6-\*
```

Next, install Oracle Java 7:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

Now, download the following:
[LIST][*]Go to **[http://java.com/en/download/manual.jsp?locale=en](http://java.com/en/download/manual.jsp?locale=en)**
  [LIST][*]Download the Oracle Java Runtime Environment packages listed as:
    [LIST][*]Linux[/LIST]
  [/LIST]
[*]Go to **[http://www.mozilla.org/en-US/firefox/new/](http://www.mozilla.org/en-US/firefox/new/)**
  [LIST][*]Download the current firefox[/LIST][/LIST]

You should have the following 2 files (versions of course may vary):
[LIST][*]jre-7u7-linux-i586.tar.gz
[*]firefox-15.0.1.tar.bz2[/LIST]

[INDENT]** Note: The following instructions should work with either JDK or JRE.  Just make sure to change my commands below appropriately with the correct versions.*[/INDENT]

Move these two files to a new temp directory on your desktop to make this easier (modify filenames as needed):
```
mkdir $HOME/Desktop/temp
cd $HOME/Downloads && mv jre-7u7-linux-i586.tar.gz firefox-15.0.1.tar.bz2 $HOME/Desktop/temp/
cd $HOME/Desktop/temp
```

Extract Java package and rename each folder appropriately:		
```
tar -zxvf jre-7u7-linux-i586.tar.gz && mv jre1.7.0_07 jre1.7.0_07_x86
```

Extract Firefox and rename this appropriately:		
```
tar -jxvf firefox-15.0.1.tar.bz2 && mv firefox firefox_x86
```
[/INDENT]

**Installation:**
[INDENT]Install the new Oracle Java package and update alternatives:
```
sudo mkdir /usr/lib/jvm
sudo mv jre1.7.0_07_x86 /usr/lib/jvm/
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jre1.7.0_07_x86/bin/java 10
sudo update-alternatives --install /usr/bin/javaws javaws /usr/lib/jvm/jre1.7.0_07_x86/bin/javaws 10
sudo update-alternatives --install /usr/lib/mozilla/plugins/libnpjp2.so libnpjp2.so /usr/lib/jvm/jre1.7.0_07_x86/lib/i386/libnpjp2.so 10
```

*Note: You want your original 64bit Java to be the current and best alternatives used.  Check this by running the following:*
```
update-alternatives --display java
update-alternatives --display javaws
update-alternatives --display libnpjp2.so
```

[INDENT]If the link currently points to [FONT="Courier New"]**/usr/lib/jvm/jre1.7_07_x86/*/***[/FONT] as current or best, you want to run the following to make your original 64bit Java the current link:
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-7-oracle/bin/java 12
sudo update-alternatives --install /usr/bin/javaws javaws /usr/lib/jvm/java-7-oracle/bin/javaws 12
```
[INDENT]* The higher the priority, the more likely it will be automatically selected as the default Java system-wide[/INDENT][/INDENT]

Install Firefox which we'll be using as a 32bit version:
```
sudo mv firefox_x86 /opt/
sudo cp /usr/share/applications/firefox.desktop firefox_x86.desktop
sudo gedit /usr/share/applications/firefox_x86.desktop
```

[INDENT]Copy and paste the following and save:
```
[Desktop Entry]
Version=1.0
Name=Firefox Web Browser (32-bit)
Comment=Browse the World Wide Web
GenericName=Web Browser
Keywords=Internet;WWW;Browser;Web;Explorer
Exec=/opt/firefox_x86/firefox %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=firefox
Categories=GNOME;GTK;Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;x-scheme-handler/chrome;video/webm;application/x-xpinstall;
StartupWMClass=Firefox
StartupNotify=true
Actions=NewWindow;
Name[en_US]=Firefox Web Browser (32-bit)

[Desktop Action NewWindow]
Name=Open a New Window
Exec=/opt/firefox_x86/firefox -new-window
OnlyShowIn=Unity;
```[/INDENT]

Press your SUPER key (Windows Key) and search for "Firefox".  
[LIST][*]You should see 2 entries now, "Firefox Web Browser" & "Firefox Web Browser (32-bit)"
[*]Grab the icon for the 32bit version and place it in the Unity Launcher.  Now you have a quicklink to launch the 32-bit version of Firefox.[/LIST]

All that's left is to associate the 32bit version of Java with the 32bit version of Firefox:
```
sudo ln -s /usr/lib/jvm/jre1.7.0_07_x86/lib/i386/libnpjp2.so /opt/firefox_x86/plugins/
```
[/INDENT]

**Testing:**
[INDENT]If you'd like to test this, just go to this site: **[http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)**
[LIST][*]Open up your normal Firefox and go to the link.  You should see the version is 64bit.
[*]Test the other browsers you have as well.
[*]Now, open up the 32bit version of Firefox and go to the link.  You should now see the version is 32bit.[/LIST]

To use Juniper VPN now, just log into your VPN website like normal with the 32bit version of Firefox and you should get a prompt to install the Juniper client.  
[LIST][*]Click "Yes"
[*]Type your password when prompted in a separate Terminal window.
[*]If everything was successful, you should now have Juniper VPN running and connected.[/LIST]
[/INDENT]
**Troubleshooting Tips:**
[INDENT]If when you log in to your VPN website and the Juniper client pops up very briefly and closes instantly, try the following:
[LIST][*]Sign out of your VPN website and close all versions of Firefox.
```
rm -rf $HOME/.juniper_networks
```
[*]If that didn't work, do the following:
[LIST][*]Sign out of your VPN website and close all versions of Firefox.
```
rm -rf $HOME/.juniper_networks
sudo dpkg-reconfigure resolvconf
sudo reboot
```
[/LIST][/LIST]
[/INDENT]

---

### Post by n00d13 on 2013-04-28
Thank you very much. Your method is working. But if somebody will use it - he have to know that current version of java is another and he have to change paths in comand line. It is not dificult but important

---

### Post by _0R10N on 2013-06-08
Hi! Thanks for this tutorial!

When trying to run firefox (32-bits) I'm getting this error

XPCOMGlueLoad error for file /opt/firefox_x86/libxpcom.so:
libxul.so: cannot open shared object file: No such file or directory
Couldn't load XPCOM.


any clue?

BTW the file is there.

Thanks!

---

### Post by ushpiy on 2013-06-10
Just wanted to say thanks for this tutorial :)

---

### Post by ischuyt on 2013-07-17
It's worth noting that in Firefox 22 the plugin folder has moved to [firefox]/browser/plugins/

So the last step should be something like this (depending on your Java version and directory names):

```
sudo ln -s /usr/lib/jvm/jre1.7.0_25_i586/lib/i386/libnpjp2.so /opt/firefox_x86/browser/plugins/
```

Other than that, this procedure is still working OK with Java 1.7.0.25 and Firefox 22.

---

### Post by _0R10N on 2013-07-17
I got it working on Ubuntu 13.04 (64 bits) with Google Chrome. This is a [link to the article]("http://arecordon.blogspot.com.ar/2013/07/ubuntu-junipers-network-on-ubuntu64.html") in my blog.

---

### Post by darkmas on 2014-02-21
Following your chrome instructions I was able to get it working with the 32 bit version of firefox, pretty much as described here. At this point, I'm not sure which version of the jdk it's using ;-)

$ sudo apt-get install ia32-libs openjdk-7-jdk:i386 icedtea-plugin

---

