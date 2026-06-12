---
title: "Clocworkmod Tether on Ubuntu 13.04 (Guide)"
date: 2013-10-29
forum: Tutorials
---

### Post by inexplikibled on 2013-10-29
Hello all,

This is my first post on Ubuntu Forums and is intended to be a Guide/Notes for myself and others to refer to.
It is about the procedure I had to go through to install and use Clockworkmod Tether Android app with Ubuntu 13.04. I may update this later once I have upgraded to 13.10. I am writing this guide so that if other people have had the same trouble as me finding a way to install and use Clockworkmod Tether with Ubuntu 13.04, then they can apply this solution. I can't say this will work for everyone, or that anyone else has had this trouble though. I have gotten this to work with the help of several posts on various websites and will be reposting some code that helped.

The main reason I had trouble is that the included adb file with the linux app would not work. Period. Nothing I tried would execute it, ./adb devices for example would return adb: No such file or directory, even after changing it to executable with chmod or with the properties dialog...

I am not an expert Linux user, but I'd say I know my way around it pretty well. Anyway, on with the guide...

1. Download and install the Clockworkmod Tether Android app on your phone.
2. Open a terminal in Ubuntu, and enter: ```
sudo apt-get install android-tools-adb
```
3. Open a browser E.g. Firefox and search for Clockworkmod Tether. Go the the google play website for the app, scroll down and click to download for the Linux version.
4. You should have a .tgz file now. Extract it to wherever you want. I just kept mine in the Downloads folder. You should now have a folder named Tether.
5. Open the Tether folder and navigate to the linux sub-dir. Here you should have 2 files: adb and run.sh. Open run.sh with a text editor.
6. Replace the line that looks like ```
../linux/adb start-server
``` with```
 adb start-server
```. Save and exit run.sh.
7. Now go back to the Tether dir and go to node-tuntap dir. Open adb.js in a text editor.
8. Replace the line that looks like ```
adbPath = '"' + path.join(process.cwd(), adbPath) + '"';
``` with ```
adbPath = '/usr/bin/adb' 
```Save and exit adb.js.
9. Go back to the terminal and enter: ```
sudo gedit /etc/udev/rules.d/70-android.rules
``` then paste in this: ```
SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
``` Save and exit 70-android.rules.
10.You need to compile Clockworkmod Tether before running run.sh. To do so, make sure you have  the proper dependencies installed like g++ then go to Tether/node dir in  terminal and enter ```
./configure
``` then enter ```
make
```If everything went  well, you should be able to run run.sh.
11. Plug in your phone to the computer via usb, make sure it's not set to mass storage mode. Set it to something else like camera mode or something. Start the tether app on your phone.
12. Disconnect from all networks (ethernet, wifi, etc.) on Ubuntu.
13. Back in your Ubuntu terminal change directory to the Tether dir, then enter: ```
sudo linux/run.sh
```
14. If necessary, in another terminal enter: ```
sudo ifup tun
```
Done. 
If all went well, you should be able to load web pages in your browser, as well as do other things online so long as you have good cell reception. On my Droid razr I was able to search google and partly load a youtube video with only 3 gray bars of signal, I think thats less than 4g connection or something.

If you have any questions, I'll do my best to answer them but remember, I didn't write this app, I just changed some script files.

EDIT: This app and method also work on Ubuntu 13.10!

---

### Post by papibe on 2013-10-29
Thread moved to **Tutorials**.

---

### Post by rolandas-kol on 2013-12-06
In the end 
I have an error on Ubuntu 13.10
roll@roll721:~/Desktop/Tether$ sudo linux/run.sh
**Please compile the included node.js package before running Tether!**

I am quite new to this... what should I do next?

---

### Post by inexplikibled on 2013-12-06
I edited my original post to somewhat explain how to compile it. Basically, in a terminal change directory the Tether/node directory and enter ```
./configure
```If no error messages show then enter ```
make
```If you get errors with make, it usually means you have to install another package (dependency) for Tether to compile. I found that the only extra package I needed was g++. So I opened Ubuntu Software Center and installed it. After that Tether compiled just fine.

---

### Post by mtcondie on 2014-01-31
I followed the tutorial and it worked for me with no problems.  Thanks!

The only difference that I did from the tutorial is use: 
[COLOR=#0000FF]
gksudo leafpad [/COLOR]/etc/udev/rules.d/70-android.rules

and not

sudo gedit /etc/udev/rules.d/70-android.rules


Ubuntu 13.10

Droid x running CyanogenMod-7.1.0-DROIDX-KANG

Android 2.3.7

---

### Post by barryww1956 on 2014-02-05
Worked for me as well.  Thanks for the tutorial.

---

### Post by inexplikibled on 2014-06-23
To all that this guide helped: You're very welcome! I will unfortunately not be updating this anymore because I've finally got myself a new phone - the Moto G on Straight Talk with the unlimited $45.00/month plan. So, now that I can tether with no ploblems via wifi on my new phone, I have no need for my old one. If anyone else wants to take up on this thread with advice in the future for others, feel free to do so!

---

