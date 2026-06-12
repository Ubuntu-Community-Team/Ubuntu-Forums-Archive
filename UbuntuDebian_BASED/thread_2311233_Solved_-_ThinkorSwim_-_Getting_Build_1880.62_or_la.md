---
title: "Solved - ThinkorSwim - Getting Build 1880.62 or later to run on Ubuntu 14.04 or later"
date: 2016-01-25
forum: Ubuntu/Debian BASED
---

### Post by optionstraderdan on 2016-01-25
Jan 25, 2016

On January 23, 2016 TD Ameritrade / ThinkorSwim was updated to Version 1880.62 and part of that update was to require ThinkorSwim to run on Java Version 8.x on Linux Operating Systems.

I'm currently running Linux Lite 2.6 (based on Ubuntu 14.04 LTS) on my machine, and this morning when I fired up ThinkorSwim, it just hung at the "Updating Software" screen and never progressed any further.  After going to the ThinkorSwim Support Site, I found that part of the update was a new requirement for Linux to have Java 8.x installed on the PC, and to tell ThinkorSwim to use it from now on.

Here is the link to the ThinkorSwim Technical Document for January 23, 2016.  Scroll to the bottom of the page and click on "Open the Technical Notes" to see the full document and instructions.  The full Linux instructions can be found at the bottom of the page, and I have also pasted them below for your convenience.

In short, I performed these steps and the ThinkorSwim Trading Platform came immediately back to life!!

[https://tlc.thinkorswim.com/center/release/rel-1-23-2016.html](https://tlc.thinkorswim.com/center/release/rel-1-23-2016.html)

**Switching to Java 8 on Linux Ubuntu and Linux Mint**

**To install Java 8 on Linux for the first time, please follow steps 1 and 2 only.** 

**To configure an existing installation of Java 8, please use step 3.**


**1. Java 8 (New Installation)**


For Ubuntu and Mint, add the PPA and install Oracle Java 8 (the package provides both JDK8 and JRE8) using the following commands in the terminal adding them one at a time:

Linux terminal:~$
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer



**2.Java 8 Set Default (New Installation)**


To automatically set up the Java 8 environment variables, install the following package using the terminal:

Linux terminal:~$
sudo apt-get install oracle-java8-set-default


[B]
3. Switching Java Environments (if Java 8 is already installed on your computer)[/B]


To switch between the Java 7 and Java 8 environment variables, run the following command


Linux terminal:~$
sudo update-java-alternatives –s java-8-oracle


[B]
4. Verifying that Java 8 is the Primary System Java[/B]


To verify which version of Java is currently the system default, please run the following command: “java –version”. You should see a result that looks like the image below.
Linux terminal:~$
java-version


This should return:
Java version “1.8*****”


Note: thinkorswim may be a bit slower to update when you log in to the platform for the first time after this change.

---

### Post by hazelnut on 2016-01-25
In my case, I already had Java 8 installed and was a bit miffed that the last update didn't include support for Java 8. I've been impatiently waiting for TOS to get with the program.  Would have been nice if there was a popup error message telling me that the new TOS required Java 8 to run. Instead it just sat there spinning its wheels making me wonder. I had to snoop the logs to discover the problem. 

If you already have Java 8 installed, you only need to run:

[FONT=Courier New]sudo update-alternatives --config java[/FONT]

And select Java 8 from the list.

---

### Post by Bucky Ball on 2016-01-25
*Thread moved to **Ubuntu/Debian BASED**.*

---

