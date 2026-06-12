---
title: "ubuntu 10.04 LTS hang on unpacking"
date: 2011-12-07
forum: Sudan Team
---

### Post by suspect x on 2011-12-07
hey there how are you all? 

I wanted to say that my ubuntu 10.04 LTS lucid lynx is having some troubles when I try to install packages from the web or through any software utility  

when the packages are downloaded successfully and ready to be unpacked the system hang and does not respond at all even the keyboard stops working ,so I force the system to restart "using ALT+SysRq+S then ALT+SysRq+B".

and when the system is up and running again it continues smoothly until i try to begin !

please help me ,,it sucks :(

---

### Post by matt_symes on 2011-12-07
Hi

Open a terminal and type

```
sudo apt-get update
```

Enter your password. It will not be echoed to the screen. 

If there are any errors then copy and paste then from the terminal into your next post.

If there are no errors type

```
sudo apt-get install htop
```

Post back the results.

Kind regards

---

### Post by BC59 on 2011-12-07
Did you run

```
sudo dpkg --configure -a
sudo apt-get -f install
```

to ensure all necessary packages are completely installed and configured?

---

### Post by suspect x on 2011-12-09
Thank you [matt_symes]("http://ubuntuforums.org/member.php?u=1067998") for your time but when I installed htop and launched it from Application > System tools > Htop it opened a new terminal window with a bunch of info about the CPU,RAM and etc... I didn't know what to do with it :confused:

---

