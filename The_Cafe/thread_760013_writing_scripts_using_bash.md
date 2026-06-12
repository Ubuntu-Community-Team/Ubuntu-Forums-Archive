---
title: "writing scripts using bash"
date: 2008-04-19
forum: The Cafe
---

### Post by markp1989 on 2008-04-19
im looking to write a few scripts using bash , to help me learn, and to pass time.

 i have writen a few simple scripts before 

1: script to move files from my camera to my pc when it was pluged in
2: to make an iso from a cd in the drive 
3: same as above except it ejected the cd, and asked for a blank disk then burnt the riped iso to that disk, then delete the iso so a copying script

i dont know what kind of script to make, any ideas of simple scripts i could make that will help day to day use?

---

### Post by LaRoza on 2008-04-19
Try using zenity in the scripts you made, make them "pretty".

If you like bash, you can continue programming with other languages. If you want to stick with bash, you can learn the other *nix tools. awk, sed, etc (Note: etc isn't one of them)

Python may be interested, as it will allow you to use an easy to use language, but make bigger programs.

---

### Post by markp1989 on 2008-04-19
I have used zenity for prompts , how do you go about sending the output of commands to zenity?

---

### Post by LaRoza on 2008-04-19
> **markp1989 said:**
> I have used zenity for prompts , how do you go about sending the output of commands to zenity?

Just capture results from the command. The backtics `` are used, not quotes.
```

#!/bin/bash
 
here=`pwd`;
zenity --info --text=$here

```

---

### Post by ghostdog74 on 2008-04-19
> **markp1989 said:**
> im looking to write a few scripts using bash , to help me learn, and to pass time.

 i have writen a few simple scripts before 

1: script to move files from my camera to my pc when it was pluged in
2: to make an iso from a cd in the drive 
3: same as above except it ejected the cd, and asked for a blank disk then burnt the riped iso to that disk, then delete the iso so a copying script

i dont know what kind of script to make, any ideas of simple scripts i could make that will help day to day use?
before that, head down to the link in my sig, learning bash. Read the whole document. Next is to get in depth and learn the tools available. Some  common shell tools you will encounter are
1) [awk/sed]("http://www.unix.org.ua/orelly/unix/sedawk/index.htm")
2) grep
3) cut
4) wc, paste,join
5) those in /usr/bin and /usr/sbin

Read their man pages if you have time.

---

### Post by markp1989 on 2008-04-20
> **ghostdog74 said:**
> before that, head down to the link in my sig, learning bash. Read the whole document. Next is to get in depth and learn the tools available. Some  common shell tools you will encounter are
1) [awk/sed]("http://www.unix.org.ua/orelly/unix/sedawk/index.htm")
2) grep
3) cut
4) wc, paste,join
5) those in /usr/bin and /usr/sbin

Read their man pages if you have time.

Thanks for the links, il start reading now :D

---

### Post by %hMa@?b&lt;C on 2008-04-20
well, what are everyday tasks that you do?

---

### Post by markp1989 on 2008-04-22
im in the middle of writing a script that i will run on my fresh install of Hardy, to install my programs, themes etc. Here is what i have so far 

```
#!/bin/bash
#
##Instaling most used programs 
echo "instaling programs using apt (conky devede xchat emerald compizconfig-settings-manager gparted k3b music-applet ubuntu-restricted-extras gtk2-engines-pixbuf)"
sudo apt-get install conky devede xchat emerald compizconfig-settings-manager gparted k3b music-applet ubuntu-restricted-extras gtk2-engines-pixbuf
echo "installing nvidia drivers"
sudo apt-get install nvidia-glx-new
#
#
##instaling folding at home 
echo installing folding at home
#installing dependencies 
sudo aptitude install ia32-libs
#Downloading the tar ball
#wget -O fah.tar.gz --no-check-certificate "https://help.ubuntu.com/community/FoldingAtHome/fah_install?action=AttachFile&do=get&target=fah_install-20080207.tar.gz"
#tar xvf fah.tar.gz
cd fah_install
#tell me the information for fah conf
echo 	"user markp1989
	team number 45104"
sudo ./install.sh install
cd ~/Desktop/install
#instaling themes
echo instaling themes 
echo instaling gtk theme slickness black 
mkdir ~/.themes
cp -rf SlicknesS-black ~/.themes
echo slickness was installed
echo installing icon theme black white 2 neon 
mkdir ~/.icons
cp -rf black-white_2-Neon ~/.icons
echo installing emerald theme 
mkdir -p ~/.emerald/themes
cp -rf blackrounded ~/.emerald/themes
#set black rounded as default 
rm -rf ~/.emerald/theme
mkdir ~/.emerald/theme
cd blackrounded 
cp * ~/.emerald/theme
#cd to working dir
cd ~/Desktop/install
echo adding theme slickblack
cp -rf slickblack ~/.themes
#set desktop back ground
rm ~/.gnome2/backgrounds.xml
cp backgrounds.xml ~/.gnome2
#copying startup and conky config files
cp -rf conky ~/
cp -rf .startup ~/
# setting up bash_rc
cp .bashrc  ~/
#setting panel fonts 
cp .gtkrc-2.0 ~/
#setting up firefox fonts
sudo mv /usr/lib/firefox/res/forms.css /usr/lib/firefox/res/forms_backup.css
sudo cp forms.css /usr/lib/firefox/res/forms.css
sudo cp html.css /usr/lib/firefox/res/html.css
#set up gnome panel
rm -rf /home/mark/.gconf/apps/panel
cp -rf panel /home/mark/.gconf/apps
#setup terminal 
rm -rf /home/mark/.gconf/apps/gnome-terminal/profiles/Default
cp -rf Default /home/mark/.gconf/apps/gnome-terminal/profiles
#add nautilus scripts
cd nautilusscripts
cp * ~/.gnome2/nautilus-scripts
cd ~/Desktop/install
#make system links 
##UN COMMENT THIS SECTION AFTER!! INSTALL 
#rm -rf ~/Music
#rm -rf ~/Videos
#rm -rf ~/Pictures
#ln -s /media/data/Music /home/mark/Music
#ln -s /media/data/Videos /home/mark/Videos
#ln -s /media/data/Pictures /home/mark/Pictures
```

i tested it , and it installs the themes fine, but then i have to set them as the default theme, then i have to add ~/.startup/start to the sesions preferences section so it will auto start my conkys, how would i add them to the script?

---

### Post by phrostbyte on 2008-04-22
Just think of actions you would benefit from being automated.

A good thing to do would be to read the popular How-To guides here on Ubuntuforums, and try to convert the howtos into Bash scripts. I did that a few times. After doing that I researched some bash features and added stuff like error checking and user friendly prompts to my scripts.

Another thing to do is to just think of actions you would benefit from being automated and make a script to do that action.

IMO, there should be some kind of repo for all these scripts so people can share and improve them.

---

