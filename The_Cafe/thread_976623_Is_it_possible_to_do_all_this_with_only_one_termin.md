---
title: "Is it possible to do all this with only one terminal command?"
date: 2008-11-09
forum: The Cafe
---

### Post by diablo75 on 2008-11-09
[COLOR="Red"]**Edit:**[/COLOR]  I've pulled this off and have edited this first post so people won't assume I still need help.  I wanted to share my final results.

Here's the list of things I wanted to do with a script:


[LIST=1]
[*]Customize the appearance of Ubuntu (wallpaper, theme, fonts, dockbars, etc.)
[*]Run Update Manager.
[*]Install Flash, Java, Windows Media Codecs and MS fonts with just 4 clicks!
[*]Install Compiz Fusion Advanced Settings Manager with one more click.
[*]Install WINE with one more click and use it to run Windows based software.
[*]Reveal Archive Manager in the Accessories menu and use it to create zip archives.
[*]Install the libdvdcss2 decoder so you can watch DVD&#8217;s.
[*]Install Skype from a *.deb file.
[*]Install Google Earth using Terminal.
[*]Install Virtualbox.
[/LIST]

The first item on the list was skipped (that can't be done with a script, at least no for everyone).

The "Reveal Archive Manager" was also skipped.  That left me with a lot.

So, here's a copy and paste from my most recent post about 3 pages in which contains my final results:

Just wanted to check back in with this and let you all know that this is what I ultimately came up with:

```
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get install -y ubuntu-restricted-extras compizconfig-settings-manager wine libqt4-core libqt4-gui && sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get -y --force-yes install medibuntu-keyring && sudo apt-get update && sudo apt-get install -y libdvdcss2 && sudo apt-get update && sudo apt-get upgrade && wget http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb && sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb && wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin && sh GoogleEarthLinux.bin && wget http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb && sudo dpkg -i virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb* && sudo adduser $USER vboxusers && echo &#8220;none /proc/bus/usb usbfs devgid=46,devmode=666 0 0? | sudo tee -a /etc/fstab
```

And here is the code for 64-bit (which uses medibuntu as the source for the skype install... this is based upon the instructions found [here]("http://ubuntuforums.org/showthread.php?t=432295")).

```
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get install -y ubuntu-restricted-extras compizconfig-settings-manager wine libqt4-core libqt4-gui && wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p bluez-alsa && sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get -y --force-yes install medibuntu-keyring && sudo apt-get update && sudo apt-get install -y libdvdcss2 skype && sudo apt-get update && sudo apt-get upgrade && wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin && sh GoogleEarthLinux.bin && wget http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_amd64.deb && sudo dpkg -i virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_amd64.deb* && sudo adduser $USER vboxusers && echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" | sudo tee -a /etc/fstab
```

I've attached scripts that can be used instead of copying and pasting the above code.  One for 32, and one for 64 bit.  To use them, save them to your home folder, open a terminal window and type:

```
chmod +x megascript.sh
```
For 64-bit:
```
chmod +x megascript64bit.sh
```
Then to run the script type:
```
sudo ./megascript.sh
```
OR
```
sudo ./megascript64bit.sh
```

I don't have a computer with a 64-bit processor so I can't test this out myself, but it SHOULD work.

The only other snag that I wish I could solve is:

1.  When the Java license question comes up and asks you to select Yes (so as to agree to the license)... I wish I could automate that so I wouldn't have to sit next to the PC for that question to be answered.

2.  About the same thing with the Google Earth install, except this has to do with "Where do you want it to be installed" basically.  I wish there were a way to have it automatically go with the default location, as well as click "Quit" when it's finished installing to that the rest of the script/code can continue and finish.

---

### Post by cardinals_fan on 2008-11-09
> **diablo75 said:**
> 
I'm not too sure about item 8.  I know how to use wget to download a file, but I've not yet checked the exact path to the deb file that needs to be downloaded and I don't know how to install a deb from the terminal...

```
dpkg -i <package>
```

---

### Post by diablo75 on 2008-11-09
Okay, let me work that in....

So we have steps 2-5:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install ubuntu-restricted-extras compizconfig-settings-manager wine
```

Step 6, still not sure about...

Step 7:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list &#8211;output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 && sudo apt-get update && sudo apt-get upgrade
```

Now the new step 8:

```
wget http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb && sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb
```

And step 9:

```
wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin && sh GoogleEarthLinux.bin
```

And the new step 10 (without the addition to fstab; haven't come up with that just yet):

```
wget http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb && sudo dpkg -i virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb && sudo adduser $USER vboxusers
```

So from the looks of it, what need to figure out is how to add this text:

> none /proc/bus/usb usbfs devgid=46,devmode=666 0 0

...to the bottom of the fstab file.  What's the best way to do that?

Edit:  Combining together what I've got so far, I've got this whopper of a command:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install ubuntu-restricted-extras compizconfig-settings-manager wine && sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list &#8211;output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 && sudo apt-get update && sudo apt-get upgrade && wget http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb && sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb && wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin && sh GoogleEarthLinux.bin && wget http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb && sudo dpkg -i virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb && sudo adduser $USER vboxusers
```

---

### Post by cardinals_fan on 2008-11-09
```
echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" >> /etc/fstab
```

---

### Post by keithweddell on 2008-11-09
Why not put all of these commands into a bash script?  Then you could call the script with just one simple command.

Keith

---

### Post by chris4585 on 2008-11-09
I second the script idea..

e.g. this is my script that I run when I first install ubuntu

```
#!/bin/bash
sudo apt-get update
sudo apt-get remove --purge rhythmbox tomboy gnome-games gnome-games-data pidgin pidgin-data gnome-utils ekiga example-content evolution evolution-common evolution-data-server evolution-webcal tracker f-spot eog
echo Done removing unneeded packages
sleep 3;
sudo apt-get install alien serpentine qps compizconfig-settings-manager emerald beagle gwenview quodlibet thunderbird xchat ksnapshot emesene amsn bmpx apturl ubuntu-restricted-extras lastfm startupmanager htop bitlbee cowsay toilet ud irssi conky youtube-dl ffmpeg audacious audacity
sleep 3;
sudo apt-get upgrade
sleep 3;
echo Done upgrading
sleep 3;
echo Now making a desktop icon of your home
gconftool-2 --set /apps/nautilus/desktop/home_icon_visible --type boolean "true"
sleep 3;
echo Everything is removed and installed, have a good day


```

---

### Post by decoherence on 2008-11-09
> **cardinals_fan said:**
> ```
echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" >> /etc/fstab
```

note that there are two greater than signs. this is VERY IMPORTANT. one greater than sign will blow away the user's fstab and their system will be broken on next reboot

> = write to file
>> = append to file

---

### Post by diablo75 on 2008-11-09
> **cardinals_fan said:**
> ```
echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" >> /etc/fstab
```

Okay, I've added this into the big one I had at the bottom of my previous post....

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install ubuntu-restricted-extras compizconfig-settings-manager wine && sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list –output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 && sudo apt-get update && sudo apt-get upgrade && wget http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb && sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb && wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin && sh GoogleEarthLinux.bin && wget http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb && sudo dpkg -i virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb && sudo adduser $USER vboxusers && sudo echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" >> /etc/fstab
```

Something else I'm wondering about...

If I were to make the first command in this long string of commands "sudo -s", could I remove the all the other repeat sudo's in the rest of the string?

And I don't really object to using a script... but I'm trying to put something together that brand new users will feel just a little more comfortable with doing.  Copying and pasting one long command seems pretty easy to me, but I can see where people might mess things up (perhaps they fail to copy all the text into the terminal or something).

How do you create and execute a script?

---

### Post by cardinals_fan on 2008-11-09
> **diablo75 said:**
> 
And I don't really object to using a script... but I'm trying to put something together that brand new users will feel just a little more comfortable with doing.  Copying and pasting one long command seems pretty easy to me, but I can see where people might mess things up (perhaps they fail to copy all the text into the terminal or something).

How do you create and execute a script?
Open a new file in your favorite text editor.  Put the following (comments in red; don't enter those):
```

#!/path/to/shell [COLOR="Red"]#!/bin/bash for a bash script[/COLOR]

command1
command2
etc.
```
Save the file.  Enter the following:```

chmod +x file
./file
```

---

### Post by diablo75 on 2008-11-09
> **cardinals_fan said:**
> Open a new file in your favorite text editor.  Put the following (comments in red; don't enter those):
```

#!/path/to/shell [COLOR="Red"]#!/bin/bash for a bash script[/COLOR]

command1
command2
etc.
```
Save the file.  Enter the following:```

chmod +x file
./file
```

So would this work?

```
#!/bin/bash

sudo -s
apt-get update
apt-get upgrade
apt-get install ubuntu-restricted-extras compizconfig-settings-manager wine
wget http://www.medibuntu.org/sources.list.d/intrepid.list &#8211;output-document=/etc/apt/sources.list.d/medibuntu.list
apt-get update
apt-get install medibuntu-keyring
apt-get update
apt-get install libdvdcss2
apt-get update
apt-get upgrade
wget http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb && sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb && wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin 
sh GoogleEarthLinux.bin
wget http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb
dpkg -i virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb
adduser $USER vboxusers
echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" >> /etc/fstab
```

---

### Post by cardinals_fan on 2008-11-09
> **diablo75 said:**
> So would this work?

```
#!/bin/bash

sudo -s
apt-get update
apt-get upgrade
apt-get install ubuntu-restricted-extras compizconfig-settings-manager wine
wget http://www.medibuntu.org/sources.list.d/intrepid.list –output-document=/etc/apt/sources.list.d/medibuntu.list
apt-get update
apt-get install medibuntu-keyring
apt-get update
apt-get install libdvdcss2
apt-get update
apt-get upgrade
wget http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb && sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb && wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin 
sh GoogleEarthLinux.bin
wget http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb
dpkg -i virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb
adduser $USER vboxusers
echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" >> /etc/fstab
```
Looks okay to me, although I didn't check all your commands :)

---

### Post by diablo75 on 2008-11-09
I have a test system I'm installing in Virtualbox I'm going to try these out on later today.

The only item left on the list is #6:  Reveal the Archive Manager (which you would normally do through the Main Menu thing via System>Preferences).  Is there a way to do that from terminal?  Seems pretty tricky, but I bet someone knows how.  :D

---

### Post by cardinals_fan on 2008-11-09
> **diablo75 said:**
> I have a test system I'm installing in Virtualbox I'm going to try these out on later today.

The only item left on the list is #6:  Reveal the Archive Manager (which you would normally do through the Main Menu thing via System>Preferences).  Is there a way to do that from terminal?  Seems pretty tricky, but I bet someone knows how.  :D
What do you mean by "reveal"?

---

### Post by diablo75 on 2008-11-09
> **cardinals_fan said:**
> What do you mean by "reveal"?

Well, unless mistaken, a fresh install of Ubuntu does not show "Archive Manager" inside of the Applications>Accessories menu by default.

---

### Post by cardinals_fan on 2008-11-09
> **diablo75 said:**
> Well, unless mistaken, a fresh install of Ubuntu does not show "Archive Manager" inside of the Applications>Accessories menu by default.
*shrugs*

I don't use GNOME.

---

### Post by decoherence on 2008-11-09
No it won't work. sudo -s starts up a new root shell which would just sit there. The next command in the list wouldn't be executed until that new shell exited.

If you are doing it as a script, you would probably just have the user run it with sudo rather than putting it inside the script.

I just want to point out that new users should not be encouraged to copy/paste complex commands they don't understand. It would be really easy for someone down the line to slip something malicious in there (like removing one for those greater-than signs, for example.)

Still, it's an interesting exercise and potentially convenient for anyone who knows enough to look over it first.

---

### Post by xravexheavenx on 2008-11-09
Don't believe it shows on fresh install.

And I second the bash script idea.

Your script you wrote up looks fine to me.

---

### Post by xravexheavenx on 2008-11-09
> **decoherence said:**
> 
I just want to point out that new users should not be encouraged to copy/paste complex commands they don't understand. It would be really easy for someone down the line to slip something malicious in there (like removing one for those greater-than signs, for example.)


I'll second that.
Seen a lot of machines broken by a friend of mine not typing in commands properly.

---

### Post by diablo75 on 2008-11-09
> **decoherence said:**
> I just want to point out that new users should not be encouraged to copy/paste complex commands they don't understand. It would be really easy for someone down the line to slip something malicious in there (like removing one for those greater-than signs, for example.)

Still, it's an interesting exercise and potentially convenient for anyone who knows enough to look over it first.

For users who don't feel comfortable: the original guide I've already written is for them.  It does as much as possible via the GUI instead of terminal so the learning curve is minimized.  The goal here was to write a blog that would demonstrate how easy it is to do all of these things via the terminal using a pre-written command (or via script).

Doing this via a script does appear to be the best way to go, simply because it's cleaner looking.  You can easily see each command on one line after another, instead of stringed back to back.  But most importantly, I can comment out a description for what each command actually does.  So I think I'll go ahead and pursue doing it that way instead.

---

### Post by cardinals_fan on 2008-11-09
> **decoherence said:**
> No it won't work. sudo -s starts up a new root shell which would just sit there. The next command in the list wouldn't be executed until that new shell exited.

Interesting.  I don't use sudo, but now I know :D

---

### Post by Lord Xeb on 2008-11-09
> **diablo75 said:**
> I was wondering...

I've seen how you can daisy-chain commands together in the Terminal using &&.  (By the way... is there a proper name for "&&"?).  Shortly after Ubuntu 8.10 was released I wrote a blog called 10 Things To Do After You Install Ubuntu (see my sig).  The list of things goes as follows:


[LIST=1]
[*]Customize the appearance of Ubuntu (wallpaper, theme, fonts, dockbars, etc.)
[*]Run Update Manager.
[*]Install Flash, Java, Windows Media Codecs and MS fonts with just 4 clicks!
[*]Install Compiz Fusion Advanced Settings Manager with one more click.
[*]Install WINE with one more click and use it to run Windows based software.
[*]Reveal Archive Manager in the Accessories menu and use it to create zip archives.
[*]Install the libdvdcss2 decoder so you can watch DVD’s.
[*]Install Skype from a *.deb file.
[*]Install Google Earth using Terminal.
[*]Install Virtualbox.
[/LIST]

Now, as a challenge, I wanted to see if it's possible to do all of these things in the list (with the exception of the first item, because that's really up to the users) with only **one **long command in Terminal.  That way, after installing Ubuntu, a new user could just open a terminal window, paste in a command, and then let the computer do the rest of the work.

I've gone ahead and tried to knockout as much as I think I can and here's what I've gotten so far:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install ubuntu-restricted-extras compizconfig-settings-manager wine
```I think that should take care of items 2 through 5 in the list.  I don't know if there is a way to do item 6 from the terminal or not...

Item 7 can be &&'ed on to the end of the above code:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list –output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 && sudo apt-get update && sudo apt-get upgrade
```I'm not too sure about item 8.  I know how to use wget to download a file, but I've not yet checked the exact path to the deb file that needs to be downloaded and I don't know how to install a deb from the terminal...

I'm not sure if the medibuntu repositories allow you to simply apt-get install Google Earth, but it's probably easier to stick with downloading the .sh file and running it from terminal, I suppose.... so (I think)....

```
wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin && sh GoogleEarthLinux.bin
```As for Virtualbox... again, not sure how to install from a deb file from terminal... and I've not looked it up yet, but I'm thinking the additional text that needs to be added to the fstab file to enable USB can be done using the cat command.  I figured someone else out there might know.

Okay, so I think I've got a few bits and pieces here to start with, but am missing a little bit and would really love it if you guys could help put everything together.  I don't know if doing something like this will even work (whether or not it's even possible to create a command that's so long that terminal will reject it).  But I'd like to find out and hopefully save myself a lot of clicking when it comes to adding all of these goodies to Ubuntu after a fresh install.


You could just do this: 
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install ubuntu-restricted-extras compizconfig-settings-manager wine | sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list –output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 && sudo apt-get update && sudo apt-get upgrade | wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin && sh GoogleEarthLinux.bin
```

---

### Post by diablo75 on 2008-11-09
In this script, is there a way to automatically answer "yes" to questions like "such and such packages will take up X amount of hard drive space.  Do you want to install?"  I'd like to try and get this so that after you execute the script, you can just walk away and not have to babysit it?  Along those same lines, could something like this also be done to automatically agree to the Terms of Use that come along with the installation of Java?

I think I'm going to end the script with an "init 6" so it will reboot the PC after everything else has finished.

---

### Post by cardinals_fan on 2008-11-09
> **diablo75 said:**
> In this script, is there a way to automatically answer "yes" to questions like "such and such packages will take up X amount of hard drive space.  Do you want to install?"  I'd like to try and get this so that after you execute the script, you can just walk away and not have to babysit it?  Along those same lines, could something like this also be done to automatically agree to the Terms of Use that come along with the installation of Java?

I think I'm going to end the script with an "init 6" so it will reboot the PC after everything else has finished.
```
apt-get -y
```
[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

---

### Post by diablo75 on 2008-11-11
> **cardinals_fan said:**
> ```
echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" >> /etc/fstab
```
When I type:

```
sudo echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" >> /etc/fstab
```

I get:

bash: /etc/fstab: Permission denied.  It doesn't even ask me for my admin password.

---

### Post by diablo75 on 2008-11-25
Just wanted to check back in with this and let you all know that this is what I ultimately came up with:

```
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get install -y ubuntu-restricted-extras compizconfig-settings-manager wine libqt4-core libqt4-gui && sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get -y --force-yes install medibuntu-keyring && sudo apt-get update && sudo apt-get install -y libdvdcss2 && sudo apt-get update && sudo apt-get upgrade && wget http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb && sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb && wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin && sh GoogleEarthLinux.bin && wget http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb && sudo dpkg -i virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb* && sudo adduser $USER vboxusers && echo “none /proc/bus/usb usbfs devgid=46,devmode=666 0 0? | sudo tee -a /etc/fstab
```

And here is the code for 64-bit (which uses medibuntu as the source for the skype install... this is based upon the instructions found [here]("http://ubuntuforums.org/showthread.php?t=432295")).

```
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get install -y ubuntu-restricted-extras compizconfig-settings-manager wine libqt4-core libqt4-gui && wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p bluez-alsa && sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get -y --force-yes install medibuntu-keyring && sudo apt-get update && sudo apt-get install -y libdvdcss2 skype && sudo apt-get update && sudo apt-get upgrade && wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin && sh GoogleEarthLinux.bin && wget http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_amd64.deb && sudo dpkg -i virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_amd64.deb* && sudo adduser $USER vboxusers && echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" | sudo tee -a /etc/fstab
```

I've attached scripts that can be used instead of copying and pasting the above code.  One for 32, and one for 64 bit.  To use them, save them to your home folder, open a terminal window and type:

```
chmod +x megascript.sh
```
For 64-bit:
```
chmod +x megascript64bit.sh
```
Then to run the script type:
```
sudo ./megascript.sh
```
OR
```
sudo ./megascript64bit.sh
```

I don't have a computer with a 64-bit processor so I can't test this out myself, but it SHOULD work.

The only other snag that I wish I could solve is:

1.  When the Java license question comes up and asks you to select Yes (so as to agree to the license)... I wish I could automate that so I wouldn't have to sit next to the PC for that question to be answered.

2.  About the same thing with the Google Earth install, except this has to do with "Where do you want it to be installed" basically.  I wish there were a way to have it automatically go with the default location, as well as click "Quit" when it's finished installing to that the rest of the script/code can continue and finish.

---

### Post by doorknob60 on 2008-11-25
> **diablo75 said:**
> When I type:

```
sudo echo "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" >> /etc/fstab
```

I get:

bash: /etc/fstab: Permission denied.  It doesn't even ask me for my admin password.

I actually never figured that out TBH, I just went to root and did it. Doesn't make sense, but it does at the same time. The ehco is getting root privilages, but the >> telling it to append to fstab isn't getting privileges, but I remember trying to put the sudo in different spots without success, but experiment I guess. EDIT: Looks like you figured that one out...two weeks ago XD

Easier way would be to simply run the script as root/sudo though. And the user could still do the whole copy/paste thing (again looks liek you might have figured that out lol)

```
wget http://site.com/files/script.sh && chmod +x script.sh && sudo ./script.sh
```

Would that work? And for the archive manager thing, can you find the default .desktop file for file roller in /usr/share/applications and tell me what's in it, I have a feeling that there's an option in the desktop file telling it to hide itself, and removing or disabling the option will make it show up.

---

### Post by Outlit on 2008-11-25
Are you interested in making absolutely free money?

Nothing better then Bux.to!

Click here and join today -----V

[[IMG]http://i423.photobucket.com/albums/pp318/Outlit/banner.png[/IMG]]("http://bux.to/?r=Outlit")

---

### Post by diablo75 on 2008-11-25
> **doorknob60 said:**
> I actually never figured that out 

If you read my previous post, I did figure it out (using the tee command).

---

