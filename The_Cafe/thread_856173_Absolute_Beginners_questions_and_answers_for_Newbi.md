---
title: "Absolute Beginners questions and answers for Newbies"
date: 2008-07-11
forum: The Cafe
---

### Post by sharks on 2008-07-11
This is a thread where we should answer Absolute Beginners questions. Only basic problem questions.

Q: How do i update and Upgrade?
A: For update , type in terminal sudo apt-get update , for upgrade sudo apt-get upgrade.

Q: Ubuntu Microphone Problems and solutions
A: Open your terminal and just copy and paste the following code to get latest ALSA drivers which can fix.

wget
[ftp://ftp.alsa-project.org/pub/driver](ftp://ftp.alsa-project.org/pub/driver)
/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install


But before trying above trick you can try one more trick.Double click on the volume icon on the panel.Then Edit>Preferences.Then make sure you selected Microphone,Mic boost,Capture.Once you do this you can find new capture tab in volume control panel.Here make sure nothing is muted(no red x on microphone icon).In options tab make sure you selected Microphone as input source.

Q : Permission Denied
A : Open the terminal and type sudo in-front-of-the-command

Q: Cannot access internet (ethernet)
A: type in terminal sudo pppoeconf and configure it

Q: Installing Files
A: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Q: Cant play videos in Websites like youtube and many other.
A: type in terminal sudo apt-get installl flashplugin-nonfree

Q: All codecs and Flash Player
A: sudo apt-get install ubuntu-restricted-extras


I hope this helps some of the members here and please contribute some here.

---

### Post by beercz on 2008-07-11
> **sharks said:**
> This is a thread where we should answer Absolute Beginners questions. Only basic problem questions.

Q: How do i update and Upgrade?
A: For update , type in terminal sudo apt-get update , for upgrade sudo apt-get upgrade.

Q: Ubuntu Microphone Problems and solutions
A: Open your terminal and just copy and paste the following code to get latest ALSA drivers which can fix.

wget
[ftp://ftp.alsa-project.org/pub/driver](ftp://ftp.alsa-project.org/pub/driver)
/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install


But before trying above trick you can try one more trick.Double click on the volume icon on the panel.Then Edit>Preferences.Then make sure you selected Microphone,Mic boost,Capture.Once you do this you can find new capture tab in volume control panel.Here make sure nothing is muted(no red x on microphone icon).In options tab make sure you selected Microphone as input source.

Q : Permission Denied
A : Open the terminal and type sudo in-front-of-the-command

Q: Cannot access internet (ethernet)
A: type in terminal sudo pppoeconf and configure it

Q: Installing Files
A: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Q: Cant play videos in Websites like youtube and many other.
A: type in terminal sudo apt-get installl flashplugin-nonfree

Q: All codecs and Flash Player
A: sudo apt-get install ubuntu-restricted-extras


I hope this helps some of the members here and please contribute some here.
Don't we have a [forum]("http://ubuntuforums.org/forumdisplay.php?f=326") for this already?

---

### Post by barbedsaber on 2008-07-11
whats that command that removes all the packages that were no longer needed (the were dependency's for programs that have been uninstall ed)

uh, I know, but, you say it first. :)

---

### Post by MasterXandrex on 2008-07-11
I think there should be some explanation. It is a terrible idea to tell a user any time they get "Permission Denied" to just prepend it with sudo. People who do not know what that does should probably not be sudoing commands. There's a reason you need to use that command explicitely.


Xan

---

### Post by Masoris on 2008-07-11
Why every answers need terminal? Many absolute beginner has fear such CUI stuff, doesn't it?

---

### Post by Sealbhach on 2008-07-11
> **Masoris said:**
> Why every answers need terminal? Many absolute beginner has fear such CUI stuff, doesn't it?

Because it's quick.

Copy and paste.

Much less chance of directions not being followed properly.



.

---

### Post by fatality_uk on 2008-07-11
> **beercz said:**
> Don't we have a [forum]("http://ubuntuforums.org/forumdisplay.php?f=326") for this already?

Agreed. No need to re-invent the wheel!

---

### Post by intimatewipe on 2008-07-11
I tried to reinvent the wheel so I put corners on it so it wouldn't roll away if you left it,never took off:)

---

### Post by fatality_uk on 2008-07-11
:lol: That joke is almost as old as the wheel ;)

---

### Post by cardinals_fan on 2008-07-11
> **masterxandrex said:**
> i Think There Should Be Some Explanation. It Is A Terrible Idea To Tell A User Any Time They Get "permission Denied" To Just Prepend It With Sudo. People Who Do Not Know What That Does Should Probably Not Be Sudoing Commands. There's A Reason You Need To Use That Command Explicitely.


Xan
+1

---

