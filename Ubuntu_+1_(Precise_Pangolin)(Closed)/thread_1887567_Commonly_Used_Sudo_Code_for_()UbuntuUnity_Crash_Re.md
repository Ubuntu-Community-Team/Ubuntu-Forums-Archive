---
title: "Commonly Used Sudo Code for (*)Ubuntu/Unity Crash Recovery"
date: 2011-11-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-11-27
*suggestion*

Commonly Used Sudo Code for (*)Ubuntu/Unity Crash Recovery:

This thread is best utilized for the submission of sudo codes and other terminal codes that help end_users who are beta testing Precise Pangolin during the next several months. The purpose of this forum is to help advanced beta testers to deposit  and reference commonly used sudo codes that they may offer as a crash recovery suggestion and for the use of newer beta testers and new_users in general so that they may benefit from that research.

    It may also  be edited in a Q&A form - ie;

Q. How do I do a simple check of my hardware environment?
A. Enter the code <**[COLOR=Blue]lspci[/COLOR]**> without the brackets at the terminal and then hit <Enter>
     [B]Here is an example and how it should appear:
[/B]```
ventrical@ventrical-P4M266A-8237:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)
ventrical@ventrical-P4M266A-8237:~$ 
```Q. How do I get to the terminal if  I have only verbose desktop?
A. Press the keys <**Ctrl+Alt+F1**> for a terminal and enter the command required at the prompt.

                               or in this format 

To refresh your grub boot.log enter this command at the terminal prompt:

**sudo update-grub**

After installing the Precise repositories it is always best to update and upgrade your system from the terminal with these commands:

[B]sudo apt-get update
sudo apt-get upgrade

[/B]and then
**sudo update-grub**

--------------------------------------------------------------------


  This is only a suggestion. I would just think that it would save a lot of down time if beta testers could centralize sudo recovery codes.

Regards,
Ventrical

---

### Post by effenberg0x0 on 2011-11-27
IMHO, the people and questions we see right now at "General Help" are a small sample of what we'll see after the release of PP. We'll see people migrating to PP from MM and previous versions.

Things we take as pretty much answered and established among the majority of this sample, like the absence of a way to move the launcher, do some customizations, some features present in previous features of Nautilus and other software that are gone, etc will be in focus again. Also, we do see some forum helpers are a couple steps behind us, sometimes offering support that is unrelated/ineffective to users problems. 

I believe we'd have to "explain" PP/Grub/Lightdm/Greeters/Unity/Gnome-Shell/etc. What they are. What they are not. What PP can do now, what it still can't. Why doesn't it have the default GUI with traditional panels anymore. Questions like "Why won't Unity run in my PC, what is a VGA driver and how to get one, what is the Dash, what are Lenses, how to add/remove Lenses, what is a PPA, how to add/purge a PPA, how to reset Compiz, how to activate/deactivate Compiz Plugins, how to configure the Unity Launcher bar, how to reset Unity", etc. How to do things in PP. If we can put the correct answers to all of these in one same and organized place, we will be creating a good "library" on PP for helpers and users.

Obviously some of this (a lot, actually) is and has been the same as previous versions (e.g. managing sources.list and PPAs). But new users will look to info targeted at PP, not at pages, guides, wikis and threads that refer to OO, MM and previous versions. We can use some content from previous guides and wikis and update them where needed.    

As I said in the other other thread,** somethings are not bugs but need some workarounds to be activated/deactivated**, while the UI is still not handling them. Safe scripts and "one-liners" to fix sources, PPAs, Unity, etc should be a part of it.

A work that puts together all this info in an organized fashion is valid and may help new PP users when it is released. If it's really organized enough, it could also easily be ported to a wiki on PP later and improved by others. I would enforce that it's content and approach should be less-technical and succinct than the bug thread: It's targeted at a different audience.

Since, in theory, we are the ones using PP daily and before other users, and we share a commitment to the community, maybe it is our job to create such a content. It makes sense to me that we are the ones who can organize bugs and also some sort of updated guide/documentation on the new release.  

You can count on me on this. If you take this project on, I suggest you have a look at other guides and wikis, not only Ubuntu ones, to see what topics/structure was used, draft the main sections/areas we should collaborate to, and keep it running clean in here.

---

### Post by ronacc on 2011-11-27
and also a list of commonly used things that have moved and where to , people coming from anything before NN are going to be lost for awhile . The difference between Unity and/or Gnome-shell and classic Gnome will be a shock .

---

### Post by effenberg0x0 on 2011-11-27
> **ronacc said:**
> and also a list of commonly used things that have moved and where to , people coming from anything before NN are going to be lost for awhile . The difference between Unity and/or Gnome-shell and classic Gnome will be a shock .

+1 on that, totally.

---

### Post by ventrical on 2011-11-27
> **effenberg0x0 said:**
> 

Since, in theory, we are the ones using PP daily and before other users, and we share a commitment to the community, maybe it is our job to create such a content. It makes sense to me that we are the ones who can organize bugs and also some sort of updated guide/documentation on the new release.  

These are all great suggestions. They certainly would help the Ubuntu community as a whole. Perhaps, if I may, try to define my pseudo_template a little clearer. I was implying something a little simpler to comprehend To the effect of "the top 25  sudo codes used in beta test crash recovery" etc. Personally I call it "blackboarding" Einstien called them "thought experiments" but this is just an example of what I am trying to communicate on this subject.

  I will often forget exactly how to  change the sources.list to set them for Precise and how to upgrade them and update them after I have the list changed over. In my past practices with malware removal and virus theory I would often make hand written notes, use a manual or have a second terminal (which was prerequisite for anti-virus research.) However, during beta testing Oneiric Ocelot I found that I was able to flag a few threads and be able to return back there (on_line) when needed. So , as with Precise I find it much more convenient to go to these mini-repos and use those repos as a memory peg.

  Ok.. so I want to  change my sources.list so I can convert my Oneiric Ocelot system so as to be able to use the new Precise kernel(s).

  First I would visit here: [http://ubuntuforums.org/showthread.php?t=1859235](http://ubuntuforums.org/showthread.php?t=1859235)

then I would have to scroll down to here: [http://ubuntuforums.org/showpost.php?p=11343629&postcount=3](http://ubuntuforums.org/showpost.php?p=11343629&postcount=3)


paste the command in terminal>-
**sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list**
go back here :  [http://ubuntuforums.org/showpost.php?p=11338561&postcount=1](http://ubuntuforums.org/showpost.php?p=11338561&postcount=1)

and paste this command  in terminal: 
**sudo apt-get update && sudo apt-get dist-upgrade**

After this you would enter the commands:
[B]sudo apt-get update
[/B]and then:
[B]sudo apt-get upgrade

[/B]To **verify **that you have the Precise kernel installed you can enter one of these 2 commands:

**lsb_release -a**

or

**uname -a**

which will produce:

$ uname -a
  3.2.0-1-generic #3-Ubuntu SMP Tue Nov 22 11:17:48 UTC 2011 i686 i686 i386 GNU/Linux

and

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu precise (development branch)
Release:    12.04
Codename:    precise

respectively.


  Now, if I am a new user and just want to really get on the PP bandwagon and I see everybody else with the new kernels  etc.. I'm going to try and use google  or some other search engine or skip through the forums looking for something but won't immediately assume to look in FAQ (although I would say that the thread in question is very well written) but it is not the first place I would look to edit my sources list.

 So I have to put myself in the shoes of a noob.  I just downloaded the most recent alpha .iso and Boom .. nothing works - I get verbose characters  on my screen that mean nothing to me. I just want to get my screen up. I want to log on and start surfing and  experimenting.  So , as a noob , I am assuming  I have a crash and I just want to get my system up and running in a reasonable facsimile.  So I would be more drawn to *crash recovery* sudo codes. "Hey!" I tell myself. "I may be a noob but I'm not stupid!" Right ! :)

  If I am a more senior or advanced user and are sick of notepads or where I left my last todo then such a sticky would come in handy for me as I could more efficiently dispense advice to others , new and old alike. The crash recovery tips 'n tricks would be more centralized.

----

   So It is mid-Feburary and the Precise updates are causing breakage everywhere. I haven't got time to re-boot or emulate - I need to dispense some code real quick (or give myself a refresher) and so I can 'click' over to "PP crash-recovery"  and it's mostly all there. No muss, no fuss.

  I am only speaking in IMHO. Some ITs are more comfortable with their own personal stickies (who isn't) but more and more I am finding that it is more organized  and proper to harvest code in the mother forum.

 Regards,

ventrical

---

### Post by ventrical on 2011-11-27
> **ronacc said:**
> and also a list of commonly used things that have moved and where to , people coming from anything before NN are going to be lost for awhile . The difference between Unity and/or Gnome-shell and classic Gnome will be a shock .

This is exactly it.   The jump from NN to OO  was already a real shocker. effenberg0x0 and many others were a great help with sophisticated code to help me out more than a few times. I mean to say everybody pulls really hard here in these forums to provide expert and comprehensive help as it is. It's just a great place to be, especially during beta testing. I am going to do my best to source mine what I can and put it up here. 

  Then , there is no telling really what type of shockers lay in wait as PP develops along to it's release date. as effen had pointed out .. it would be good to be prepared for the influx.

---

### Post by grahammechanical on 2011-11-27
I like both of these ideas. Are they mutually exclusive?

I am confident about using a development release because I do not use it as my working ubuntu OS. I am not so confident about being a useful tester.

The only problem I had with 11.10 alpha 1 (apart from a few things closing unexpectedly as far as the OS was concerned) was the lightDM unable to log in problem and I found the code to get around that in this part of the forum. As well as the code to switch back to LightDM a few days later when it was fixed. So, I like the code library idea.

I decided to install 11.10 alpha 1 because I wanted to get a head start on the 11.04 updaters who were bound to ask "where's this gone" and "how do I do that." So, I also like the Here Is How you Do it manual idea.

@ventrical I was waiting until alpha 1 was released before I installed Precise because the daily build download that I tried a couple of weeks ago did not work. The DVD did not install. Now I think that I will try out the links that you have provided to turn my Oneiric into a Precise. I was wondering how you lot did it.

I guess I am someone who will benefit from both of these ideas.

Regards.

---

### Post by ventrical on 2011-11-27
Thanks grahammechanical.

 A few times through different installs (of precise while updating) I would loose my internet connenction or some other anomoly would happen. This failed update would crash the lightdm and only give me the terminal. However, during one session I noted that it advised me to:

sudo dpkg -i --configure -a

in the terminal and the downloading/updating process would pick up where it left off and literally repair the broken system. I had occasion to use this a few times. However .. there were a few times where I was just drawing blanks, asking myself, 'Where did I see that little .... code?"  so it was really frustrating. I tried  taking screenshots of code and pasting code to Gedit and even turn those into cascading wallpapers .. but there is something more dynamic about being on line and checking the library that way, centralized in the same echo.

---

### Post by effenberg0x0 on 2011-11-27
I can help with some shell code to check / fix some things, which I normally offer to people when I help them here. Some basic code that sometimes can be helpful, like:

- Checking for and reinstalling critical packages for X/Lightdm/Unity
- Checking / fixing environment vars
- Checking / Fixing permissions / ownership of critical files 
- Checking basic Unity config files fixing them
- Auto-Detect VGA vendor, auto-download VGA driver, install and start session
- Fixing sources, fixing apt-cache and managing PPAs (auto-ppa detection, parsing, interactive removal)
- Auto-download / install flashplugin && java
- Resetting Compiz plugin / Profile / Unity session
- Start Ethernet / Grab IP from DHCP / insert DNS / activate Internet connection wo one can easily use APT while in Console.
- Solving some punctual problems, like avoiding the PC suspend/hibernation, etc
 

I've got a lot of those in my Eclipse bash-snippets folder... Some are less friendly than others. A few of them are coded into long interactive scripts which makes it hard to cut&paste. I'll try to simplify them into copy&paste-viable "one-liners" you can use here if you consider it valid.  But just ask me for shell code to do whatever you need when you think of something specific and I write it to you, no problems.

---

### Post by ronacc on 2011-11-27
if you already have the shell scripts written couldn't you just attach them as .txt files ?

---

### Post by ventrical on 2011-11-27
> **effenberg0x0 said:**
> I can help with some shell code to check / fix some things, which I normally offer to people when I help them here. Some basic code that sometimes can be helpful, like:

- Checking for and reinstalling critical packages for X/Lightdm/Unity
- Checking / fixing environment vars
- Checking / Fixing permissions / ownership of critical files 
- Checking basic Unity config files fixing them
- Auto-Detect VGA vendor, auto-download VGA driver, install and start session
- Fixing sources, fixing apt-cache and managing PPAs (auto-ppa detection, parsing, interactive removal)
- Auto-download / install flashplugin && java
- Resetting Compiz plugin / Profile / Unity session
- Start Ethernet / Grab IP from DHCP / insert DNS / activate Internet connection wo one can easily use APT while in Console.
- Solving some punctual problems, like avoiding the PC suspend/hibernation, etc
 

I've got a lot of those in my Eclipse bash-snippets folder... Some are less friendly than others. A few of them are coded into long interactive scripts which makes it hard to cut&paste. I'll try to simplify them into copy&paste-viable "one-liners" you can use here if you consider it valid.  But just ask me for shell code to do whatever you need when you think of something specific and I write it to you, no problems.


Sounds great effenberg. You are very adept with sudo codes and they work a great percentage of the time.  When you have time just post away my friend. Perhaps the mods will eventually make a sticky out of it for all of us beta testers.
 I was just reading one of your posts here : [http://ubuntuforums.org/showpost.php?p=11302769&postcount=5](http://ubuntuforums.org/showpost.php?p=11302769&postcount=5)

 so this is the stuff I'm talking about.. but you see how it is scattered all over - even from closed threads ?

---

### Post by ventrical on 2011-11-27
> **ronacc said:**
> if you already have the shell scripts written couldn't you just attach them as .txt files ?


Thats a great idea ronacc. There is a large well of info out there in the closed forums. at least in a local sticky we can link to them and therefore centralize them. I see you rescue quite a few systems also. Mind you we try to stay focused on Precise P - but it would be a great general helper also.

---

### Post by ventrical on 2011-11-27
> **effenberg0x0 said:**
> I can help with some shell code to check / fix some things, which I normally offer to people when I help them here. Some basic code that sometimes can be helpful, like:

- Auto-Detect VGA vendor, auto-download VGA driver, install and start session


  I think that this is probably the most common of all fresh install bork ups and the one which end_users need the most guidance on. And even on stable installed systems. I am typing this message from a 64bit system with the 3.2 Precise kernel but the ATi  driver is borked .. so here I have a  problem already (as adressed in another thread).

video vs monitor detection problems are systemic for the most part from what I have observed.

---

### Post by effenberg0x0 on 2011-11-27
> **ventrical said:**
> I think that this is probably the most common of all fresh install bork ups and the one which end_users need the most guidance on. And even on stable installed systems. I am typing this message from a 64bit system with the 3.2 Precise kernel but the ATi  driver is borked .. so here I have a  problem already (as adressed in another thread).

video vs monitor detection problems are systemic for the most part from what I have observed.

Getting people to use a proper vga driver and thus see Unity was a killer one on the week after OO release. It won't be different for PP. 

I always selected the users that were receiving no help or those where help was failing to solve his problem, just because I had more fun with interesting cases. Many times I helped users in PM or even posted something to help that specific case, maybe even wrote some code, but never really kept track of it as something that could be useful for others. You'll find some of these thrown all over. 

I understand your point, to gather us to collaborate on creating a place for such things to be all together and at hand. 

I'm just wondering how to simplify some things. This piece of code, for example, fixed the install of many users during OO launch, but it's kind of huge / impossible to be in one line:

```

#!/bin/bash
##################################################
# fix_oneiric.sh
# Attempts to fix a broken OO Install for NVidia 173 users
# Effenberg0x0@Launchpad.net
#
##################################################
#
# Save this file to a known location, such as your Home Folder
# Execute it with sudo chmod +x fix-oneiric.sh && sudo bash ./fix-oneiric.sh
#
##################################################
# Assume the env vars we need may be wrong and get them
# from safer sources
ROOT_PARTITION=$(mount | grep -i "on / type" | awk '{ print $1}')
ROOT_FS=$(mount | grep -i "on / type" | awk '{ print $5}')
ROOT_WRITE=$(mount | grep -i "on / type" | awk '{ print $6 }')
FIX_USER=$(cat /etc/passwd | grep 1000 | awk 'BEGIN { FS=":" }; {print $1}')

##################################################
# Checks for a rw filesystem and remounts if needed
if [ $ROOT_WRITE == "(ro)" ]; then 
   mount -f -o remount,rw -t $ROOT_FS $ROOT_PARTITION /
fi

##################################################
# Make sure GUI sessions are stopped
service stop lightdm
service kill -s KILL $(pidof lightdm)
service stop gdm
service kill -s KILL $(pidof gdm)
killall -s KILL /usr/bin/X

##################################################
# Fixes user home permissions and ownership
chown $FIX_USER:$FIX_USER /home/$FIX_USER -R && sudo chmod 750 /home/$FIX_USER -R

##################################################
# Fixes Xauthority bug
mv /home/$FIX_USER/.Xauthority /home/$FIX_USER/.Xauthority.backup

##################################################
# Removes all nvidia remains
cd /home/$FIX_USER
mkdir nvidia_driver
cd nvidia_driver
apt-get remove --purge gdm nvidia-173 nvidia-96 nvidia-cg-toolkit nvidia-current-updates nvidia-173-dev nvidia-96-dev nvidia-common nvidia-current-updates-dev nvidia-173-updates nvidia-96-updates nvidia-current nvidia-settings nvidia-173-updates-dev nvidia-96-updates-dev nvidia-current-dev nvidia-settings-updates

##################################################
# Downloads nvidia 173 driver 
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.31/NVIDIA-Linux-x86-173.14.31-pkg1.run

##################################################
# Exports needed and correct environment variables
export DISPLAY=:0.0
export XDG_CURRENT_DESKTOP=Unity
export XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/
export COMPIZ_CONFIG_PROFILE=ubuntu
export GDMSESSION=ubuntu
export DESKTOP_SESSION=ubuntu
export PATH=/home/$USER:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
export XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
export XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
export DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path

##################################################
# Run nvidia installer
chmod +x NV*
./NV*

##################################################
# Reinstalls all critical DM/DE packages
apt-get install --reinstall --fix-broken --allow-unauthenticated lightdm lightdm-gtk-greeter unity unity-2d unity-2d-launcher unity-2d-panel unity unity-2d-places unity-greeter unity-lens-music unity-services unity-2d unity-2d-spread unity-lens-applications unity-place-applications unity-2d-launcher unity-asset-pool unity-lens-files unity-place-files unity-2d-panel unity-common unity-lens-gwibber unity-scope-musicstores compiz compiz-dev compiz-kde compiz-plugins-main-default compizconfig-backend-gconf compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev compizconfig-backend-kconfig compiz-fusion-plugins-extra compiz-plugins-default compizconfig-settings-manager compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome compiz-plugins-main

##################################################
# Makes sure lightdm was not started
service lightdm stop

##################################################
# Fixes lightm config bug (if needed)
if [ ! -f /etc/lightdm/lightdm.conf ]; then sudo touch /etc/lightdm/lightdm.conf
echo -e "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter" | tee /etc/lightdm/lightdm.conf

##################################################
# Fixes default-display-manager bug (if needed)
if [ ! -f /etc/X11/default-display-manager ]; then touch /etc/X11/default-display-manager
echo -e "/usr/sbin/lightdm" | tee /etc/X11/default-display-manager

 ##################################################
# Makes sure compiz/compiz-config settings are resetted
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1

##################################################
# Backup of compiz/configconfig settings
mv $FIX_USER/.config/compiz-1/compizconfig $FIX_USER/.config/compiz-1/compizconfig.old
mv $FIX_USER/.config/compiz-1 $FIX_USER/.config/compiz.old
mv $FIX_USER/.compiz-1 $FIX_USER/.compiz-1.old
mv $FIX_USER/.cache/compizconfig-1 $FIX_USER/.cache/compizconfig-1.old

##################################################
# Update/upgrade the system and reboot
apt-get update && apt-get upgrade
reboot now

```There's an even larger version that detects ATI/Nvidia/Intel automatically, doing different things depending on the hardware and driver version needed. Another one does the same but first makes sure there's an IP connection, or creates one. There's still another that downloads a proper sources.list setup from the web (sources.list generator) and puts it into the user sources. I have scripts with 10 pages here, that check and fix every bug I know off in one single run... I'll have to think a little on how to break that into something smaller and more viable.

---

### Post by ronacc on 2011-11-27
while as I suggested a large script that does many things could be uploaded as an attachment , it might do those needing the help more good if it was in single fix pieces to make it easier for them to learn from if they are so inclined , and for us to benefit from your knowledge also .

---

### Post by effenberg0x0 on 2011-11-27
> **ronacc said:**
> while as I suggested a large script that does many things could be uploaded as an attachment , it might do those needing the help more good if it was in single fix pieces to make it easier for them to learn from if they are so inclined , and for us to benefit from your knowledge also .

Ok, it's just that, they way my scripts now, some procedures / steps are connected, dependent from previous ones, so they can't be separated (wouldn't make sense / work). But I'll try to break some interesting / usable shell code down to smaller chunks of functional pieces that deal with punctual problems.

I hosted some of these larger scripts in my domain temporarily during OO release chaos, so I would tell users to just paste this into a terminal: [B]
export SCRIPT="fix-oneiric.sh" && cd && mkdir $HOME/${SCRIPT%.*}" && cd $HOME/${SCRIPT%.*}" && wget short/url $SCRIPT && sudo chmod +x $SCRIPT && sudo bash ${SCRIPT}"[/B]. At that point, it was interesting to have an omnibus support script as I was dealing with 4 or more support requests at the same time.

---

### Post by ventrical on 2011-11-28
@effenberg,

This one here is an example of an important crash recovery code.
```

################################################## # Reinstalls all critical DM/DE packages apt-get install --reinstall --fix-broken --allow-unauthenticated lightdm lightdm-gtk-greeter unity unity-2d unity-2d-launcher unity-2d-panel unity unity-2d-places unity-greeter unity-lens-music unity-services unity-2d unity-2d-spread unity-lens-applications unity-place-applications unity-2d-launcher unity-asset-pool unity-lens-files unity-place-files unity-2d-panel unity-common unity-lens-gwibber unity-scope-musicstores compiz compiz-dev compiz-kde compiz-plugins-main-default compizconfig-backend-gconf compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev compizconfig-backend-kconfig compiz-fusion-plugins-extra compiz-plugins-default compizconfig-settings-manager compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome compiz-plugins-main
```  In security  with windows it was an often used process to uninstall/reinstall the security program and 8 times out of 10 it would work. It would overwrite or remove config files and unbork the registry.

  If fact I tried the above code once on a busted system and it worked just swell.

  Great work.!

---

### Post by ventrical on 2011-11-28
> **ronacc said:**
> while as I suggested a large script that does many things could be uploaded as an attachment , it might do those needing the help more good if it was in single fix pieces to make it easier for them to learn from if they are so inclined , and for us to benefit from your knowledge also .


I absolutely agree with this ronacc. Step by step.  Often, during Oneiric testing, I felt as if I was walking through broken glass, trying to employ a complex proceedure. Having step by step instructions more or less settled things down a bit.

---

### Post by lisati on 2011-11-28
Maybe the pedantic part to my makeup is making a nuisance of itself, but I think what we're talking about here are **commands** that are useful for recovery, not necessarily *codes* or other stuff that uses *sudo*.

Doesn't have to be a big deal...... :D

/me wanders off to find something other than terminology to fuss over

---

### Post by ronacc on 2011-11-28
without the context provided by the full lines of code the commands by themselves would be useless to most newbe's and most need to be invoke with sudo ( or as root ) unless they are simple information requests like "ls..." .

---

### Post by effenberg0x0 on 2011-11-28
> **lisati said:**
> Maybe the pedantic part to my makeup is making a nuisance of itself, but I think what we're talking about here are **commands** that are useful for recovery, not necessarily *codes* or other stuff that uses *sudo*.

Doesn't have to be a big deal...... :D

/me wanders off to find something other than terminology to fuss over

Yes, you're completely right. For me, what I do in large scripts is shell code. Normally I use a structured code, cmd-line args (getopts), functions, arithmetics, local and global variables, loops, if-then-else conditions, etc. Sometimes I call it Bash code, cause I work with Bash specifics, like (("C-like" *for* loops)), that sometimes are not properly run on Dash, but that's another story. It may require suid or not.

What Ventrical wants me to do is to cut scripts into smaller command pipes with punctual purposes. It is totally doable. It takes out the logic for <check-if-needed-before-applying> processes and replaces it for a brute-force fix, which also works, in exchange for the possibility to have them in cut&past-able one-liners.

But, at any rate, the best definition for what will come out of it (if we were to be definition purists) would be something like:

- CLI-based workaround for system recovery (people seem like the term CLI, to define something that is not GUI - I personally don't.) :)  
- Shell-based solutions for system recovery (may contain commands and/or script - So it's a "solution")
- Smashing the Bash for fun and profit
- Etc.

---

### Post by ventrical on 2011-11-28
> **lisati said:**
> Maybe the pedantic part to my makeup is making a nuisance of itself, but I think what we're talking about here are **commands** that are useful for recovery, not necessarily *codes* or other stuff that uses *sudo*.

Doesn't have to be a big deal...... :D

/me wanders off to find something other than terminology to fuss over


  I think that keeping it simple is a good theme and then there are times for more comprehensive code which should be welcomed.

 For example  here is a simpler idea:

---------------------------------------

  Ubuntu (Precise) has a built it recovery mode at the Grub Bootloader. If you have just installed PP side by side with another system , have no screen or terminal, but have grub then you can choose the  **Recovery Option from the Grub Bootloader.  **You will see a lot of  top down , verbose code scrolling past and then come up to a **Recovery GUI.** Here you will be presented with 4 options but the most commonly used for quick recovery (and to get a desktop) is to **Resume Normal Boot.** These simple tools and commands already built into Ubuntu have worked on several occasions and twice with crashed Precise Installs with systems that I have worked on.

---

### Post by ventrical on 2011-11-28
> **effenberg0x0 said:**
> Yes, you're completely right. For me, what I do in large scripts is shell code. Normally I use a structured code, cmd-line args (getopts), functions, arithmetics, local and global variables, loops, if-then-else conditions, etc. Sometimes I call it Bash code, cause I work with Bash specifics, like (("C-like" *for* loops)), that sometimes are not properly run on Dash, but that's another story. It may require suid or not.

What Ventrical wants me to do is to cut scripts into smaller command pipes with punctual purposes. It is totally doable. It takes out the logic for <check-if-needed-before-applying> processes and replaces it for a brute-force fix, which also works, in exchange for the possibility to have them in cut&past-able one-liners.

But, at any rate, the best definition for what will come out of it (if we were to be definition purists) would be something like:

- CLI-based workaround for system recovery (people seem like the term CLI, to define something that is not GUI - I personally don't.) :)  
- Shell-based solutions for system recovery (may contain commands and/or script - So it's a "solution")
- Smashing the Bash for fun and profit
- Etc.

 Defintive and comprehensive code is good because it is 'precise' - or it deals precisely with a complex matter. Perhaps most of  us with a year or two are still  in Linux immersion. We get the drift but are still trying to develop new PC habits that require a different venacular than required by VAXUNIX, Turing, C or BASIC, and yes, even DOS .bat files :)  I mean I can only speak for myself. 25 years as data entry using UNIX and DOS based systems has made it a little tough at times to appreciate the terminal  commands presented in Ubuntu/Linux .. but I'm getting there :)  Once a consultant told me over 2 decades ago that I had to learn how to make my computer walk before I could make it dance. This really peeved me off.. but he was right ya know . :)

---

### Post by effenberg0x0 on 2011-11-28
An example: This is one of the things I used a lot in General Help and feel like I'm gonna use 10x more now. It allows to:

- Not rely on any inaccurate information from the user as to whether he has (or not) added PPAs to his install. We just get the PPAs and read them. 
- Than we parse the PPAs (from ppa-file-name.list to PPA:ppaname/package format - which is the format required by the command ppa-purge)

(this need no suid)
for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat $PPA_FILE | grep "deb http" | sed -e 's|deb [http://||]("http://%7C%7C")' | sed -e 's|.launchpad.net/|\:|' | sed -e 's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e 's|main||' | tee -a /$HOME/ppa-sources.list; done

(just run the above in a terminal. It won't change anything, I swear :P. It will output your current PPAs, parsed in a more useful form. )

Now, normally, the rest of the code would present the user with the list of his PPAs on screen and ask him "Remove PPA:Somewhere/Something?" [Y/N], one by one. If I add such a logic in the above code, the thing will become too big and unreadable, not copy&paste friendly. So the alternative would be to drop proper logic and scripting and just go for the bulk-fix tactic, using only a loop to remove everything that is a PPA (non-standard anyway). Ok, then that can be added to the above lines, not increasing the "one-liner" too much...

(this need suid, because of ppa-purge - don't run this)
for PPA in $(cat /$HOME/ppa-sources.list); do /usr/sbin/ppa-purge $PPA; done 

What I meant is that it's just a matter of strategy. We can go with bigger shell code, that has more logic, checks and conditions, but will GENERALLY BE MORE COMPLETE AND present friendly options on screen, do backups, allow to revert the changes made, etc, or go for command-pipes that simply do the thing. Either one is valid. 


**Food for thought:**
It's PP release week. General Help is on fire. 
You stop, look at the threads, think what you are gonna do. 
IMHO, there's a clear difference between:

**A)** Someone whining that Unity doesn't work and that he will migrate to Mint, etc (needs a quick working fix, incapable or learning anything, won't even look at what I tell him to run). They rarely run things you ask them too in a proper order, exactly the way they should, etc. This is like 95% ([SIZE=1]JUST GUESSING, DON'T ASK ME FOR STATISTICS[/SIZE])
**B)** Someone that wants to learn: Will read, Google, browse the forum, probably fix basic things on his own and come with higher-level questions and real problems. These are rare, say 5%.

This is how I look at it: 

- Individuals of the 'A' type are the majority. We can easily take like 4 or 5 of them simultaneously (selecting opened threads that relate to the same problem) and close them in up to 10 minutes. None of them will ask what sed|awk etc does. 

- Individuals of the 'B' type come with interesting, fun to help issues. This is where I learn and find out interesting things, new bugs, etc. These ones I work on PM, because their threads get destroyed quickly by people that post unrelated issues.

When we're out of the release-week fever, percentages of A's and B's change to 85%/15%, respectively. So, for any strategy to develop a cut&paste workarounds reference, I would consider this two very different audiences, with an emphasis on A's.

**EDIT: **A totally different strategy, for example, would be if we gather our knowledge of current bugs and workarounds and add it to a larger script. This is something that we can do together here as a group over the next months and the final results will be of use to many users when PP is released (the "A's") becoming also a valuable tool to support General Help helpers. Anyone who wants to learn, will have a better chance of doing so by looking at each of the code's functions, seeing our discussion and improvements, etc. We could make it very modular, like 'one function=one bug'. One could copy paste that specific function and apply if he wants to... E.g. funtion fix_ppas {...}. We'd just have to avoid globals and code-reutilization (nested functions). Maybe we could go for a GUI interface (basic stuff, like zenity, etc). It'd be fun to work together with the guys here on that anyway.

---

### Post by sudodus on 2011-11-28
Thank you effenberg0x0 for interesting posts, last but not least the post above mine :-)

---

### Post by ventrical on 2011-11-29
[COLOR=SeaGreen]Here are some common codes of interest to help with Precise recovery in the event of a crash.

**H**ow to find your souces.list- this list is used to set repositories and can be done manually. It is also informative to have on hand if you decide to do a transitional upgrade from Oneiric Ocelot to Precise Pangolin.
```
[COLOR=Blue]/etc/apt/sources.list[/COLOR]
```[/COLOR][COLOR=YellowGreen]
[COLOR=SeaGreen]Precise Pangolin will not install: From initial boot screen from LiveCD or LiveUSB you may receive verbose characters or only purple or black  screen: 
- check here: [/COLOR][/COLOR][http://ubuntuforums.org/showpost.php?p=11518947&postcount=5](http://ubuntuforums.org/showpost.php?p=11518947&postcount=5)[COLOR=YellowGreen]

[COLOR=Green]Your beta version of Firefox is Broken- here are two possible fixes:
[/COLOR][/COLOR][http://ubuntuforums.org/showpost.php?p=11530599&postcount=18](http://ubuntuforums.org/showpost.php?p=11530599&postcount=18)
[http://ubuntuforums.org/showpost.php?p=11530670&postcount=19](http://ubuntuforums.org/showpost.php?p=11530670&postcount=19)
[COLOR=YellowGreen] 
[/COLOR] Here is a list of commonly used Ubuntu/Linux terminal Codes (not neccessarily in order and open to interperetation) of PP Crash Recovery Codes -[COLOR=Navy]To be updated:[/COLOR]

1. This command is used to auto edit the sources.list file on an install of Oneiric Ocelot and could be considered as a first step to converting to Precise Pangolin. However this and other commands may be moot after Alpha .iso are released. You can still play it safe and test the kernels but breakage may occur nonetheless. ```
**sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list**
```[COLOR=Blue]2.[/COLOR] This command will update your repositories to PP.```
**sudo apt-get update && sudo apt-get dist-upgrade**
```[COLOR=Navy]3.[/COLOR]This command is inclusive in #2. but is always good to run after removing or purging stuff.```
**sudo apt-get update**
```[COLOR=Navy]4.[/COLOR]This command is also included in #2. and upgrades any new files that are set in the repositories.```
**sudo apt-get upgrade**
```[COLOR=Navy][COLOR=Blue]4.(a)[/COLOR][/COLOR]Update-manager is a fairly important component of the Ubuntu  distribution. As we are supposed to be testing during the development  phase, this application would be helped by testing and bug reporting as  well.You can always make a judgement call as to whether the changes proposed  by update-manager seem safe or not. If in doubt I think the best way to  proceed is with aptitude:```
aptitude update && aptitude safe-upgrade
```This alleviates the concern when packages/dependencies may not be fully  synced in the repos. They will be held back until dependencies are  satisfied.

[COLOR=Navy]5.[/COLOR]This command is an essential command if you are a elementary beta tester as it will upgrade the GRUB bootloader after changes to the system using other commands, are made (like upgrading a kernel). If you have tried to carry out a proceedure and wonder why it had not taken effect on the next boot, it is likely that you did not  sudo update-grub.```
**sudo update-grub**
```[COLOR=Navy]6.[/COLOR]This command will give you simple information about your system, most commonly used to discover your video adapter.```
**lspci**
```[COLOR=Navy]7.[/COLOR]This command  will display  version information of the kernel you are using.```
**uname -a**
```[COLOR=Navy]8.[/COLOR]This command will tell you what Version of Ubuntu you are using. It will help validate  and document that the prior commands have worked properly.```
**lsb_release -a**
```[COLOR=Navy]9.[/COLOR]This command will continue to install packages that may have been broken during download or if your download unexpectedly terminated or if you have had a power-failure.```
**sudo dpkg -i --configure -a**
```[COLOR=Navy]10.[/COLOR]These two commands can be used separately if you are at the terminal prompt from startup. You can get to the terminal (if you have no desktop) by pressing the keys <Crtl+Alt+F1>   It makes booting and restarting quicker and more efficient than if you were in a desktop shell.```
**sudo reboot -sudo poweroff** 
```[COLOR=Navy]11.[/COLOR]One that I have found helpful for fixing broken packages is .```
sudo apt-get -f install
```[COLOR=Blue]12.[/COLOR]Will install any packages necessary to fix the broken package if they  are  available . If some necessary packages are not available you can  use this to remove the broken one .```
sudo apt-get -f remove
```[COLOR=Blue]13.[/COLOR]Do not rely on any inaccurate information from the user as to whether he  has (or not) added PPAs to his install. We just get the PPAs and read  them. Then we parse the PPAs (from ppa-file-name.list to PPA:ppaname/package  format - which is the format required by the command ppa-purge)```
**if [[ -d /etc/apt/sources.list.d && $(ls -l  /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir  exists and is not empty\n\n"; **for PPA_FILE in $(ls  /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed  -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e  's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e  's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list; done;  echo "PPA list saved at $HOME/ppa-sources.list"; **else echo -e "\n\nEmpty or inexistent PPA directory\n\n";** fi
```[COLOR=Blue]14.[/COLOR]Attempts to fix a broken OO Install for NVidia 173 users # [EMAIL="Effenberg0x0@Launchpad.net"]Effenberg0x0@Launchpad.net[/EMAIL]```

#!/bin/bash
################################################## 
# fix_oneiric.sh 
# Attempts to fix a broken OO Install for NVidia 173 users 
# Effenberg0x0@Launchpad.net 
# 
################################################## 
# 
# Save this file to a known location, such as your Home Folder # Execute it with sudo chmod +x fix-oneiric.sh && sudo bash ./fix-oneiric.sh 
# 
################################################## 
# Assume the env vars we need may be wrong and get them 
# from safer sources 
ROOT_PARTITION=$(mount | grep -i "on / type" | awk '{ print $1}') 
ROOT_FS=$(mount | grep -i "on / type" | awk '{ print $5}') 
ROOT_WRITE=$(mount | grep -i "on / type" | awk '{ print $6 }') 
FIX_USER=$(cat /etc/passwd | grep 1000 | awk 'BEGIN { FS=":" }; {print $1}') ################################################## 
# Checks for a rw filesystem and remounts if needed 
if [ $ROOT_WRITE == "(ro)" ]; then     
  mount -f -o remount,rw -t $ROOT_FS $ROOT_PARTITION / 
fi 
################################################## 
# Make sure GUI sessions are stopped 
service stop lightdm 
service kill -s KILL $(pidof lightdm) 
service stop gdm 
service kill -s KILL $(pidof gdm) 
killall -s KILL /usr/bin/X  
################################################## 
# Fixes user home permissions and ownership 
chown $FIX_USER:$FIX_USER /home/$FIX_USER -R && sudo chmod 750 /home/$FIX_USER -R  
################################################## 
# Fixes Xauthority bug 
mv /home/$FIX_USER/.Xauthority /home/$FIX_USER/.Xauthority.backup
 
################################################## 
# Removes all nvidia remains 
cd /home/$FIX_USER mkdir nvidia_driver cd nvidia_driver apt-get remove --purge gdm nvidia-173 nvidia-96 nvidia-cg-toolkit nvidia-current-updates nvidia-173-dev nvidia-96-dev nvidia-common nvidia-current-updates-dev nvidia-173-updates nvidia-96-updates nvidia-current nvidia-settings nvidia-173-updates-dev nvidia-96-updates-dev nvidia-current-dev nvidia-settings-updates  
################################################## 
# Downloads nvidia 173 driver  
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.31/NVIDIA-Linux-x86-173.14.31-pkg1.run  
################################################## 
# Exports needed and correct environment variables
export DISPLAY=:0.0 export XDG_CURRENT_DESKTOP=Unity export XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/ export COMPIZ_CONFIG_PROFILE=ubuntu export GDMSESSION=ubuntu export DESKTOP_SESSION=ubuntu export PATH=/home/$USER:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games export XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0 export XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0 export DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path ################################################## 
# Run nvidia installer 
chmod +x NV* 
./NV* 
################################################## 
# Reinstalls all critical DM/DE packages
apt-get install --reinstall --fix-broken --allow-unauthenticated lightdm lightdm-gtk-greeter unity unity-2d unity-2d-launcher unity-2d-panel unity unity-2d-places unity-greeter unity-lens-music unity-services unity-2d unity-2d-spread unity-lens-applications unity-place-applications unity-2d-launcher unity-asset-pool unity-lens-files unity-place-files unity-2d-panel unity-common unity-lens-gwibber unity-scope-musicstores compiz compiz-dev compiz-kde compiz-plugins-main-default compizconfig-backend-gconf compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev compizconfig-backend-kconfig compiz-fusion-plugins-extra compiz-plugins-default compizconfig-settings-manager compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome compiz-plugins-main ################################################## 
# Makes sure lightdm was not started 
service lightdm stop 
################################################## 
# Fixes lightm config bug (if needed) 
if [ ! -f /etc/lightdm/lightdm.conf ]; then sudo touch /etc/lightdm/lightdm.conf echo -e "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter" | tee /etc/lightdm/lightdm.conf  
################################################## 
# Fixes default-display-manager bug (if needed) 
if [ ! -f /etc/X11/default-display-manager ]; then touch /etc/X11/default-display-manager echo -e "/usr/sbin/lightdm" | tee /etc/X11/default-display-manager   ################################################## 
# Makes sure compiz/compiz-config settings are resetted
gconftool-2 --recursive-unset /apps/compiz-1 gconftool-2 --recursive-unset /apps/compizconfig-1  
################################################## 
# Backup of compiz/configconfig settings 
mv $FIX_USER/.config/compiz-1/compizconfig $FIX_USER/.config/compiz-1/compizconfig.old mv $FIX_USER/.config/compiz-1 $FIX_USER/.config/compiz.old mv $FIX_USER/.compiz-1 $FIX_USER/.compiz-1.old mv $FIX_USER/.cache/compizconfig-1 $FIX_USER/.cache/compizconfig-1.old  
################################################## 
# Update/upgrade the system and reboot 
apt-get update && apt-get upgrade reboot now
```[COLOR=Blue]15.[/COLOR]Unsolvable weird crash messages at most init procedures, ending in a  "black screen" (or a console screen), no DM/DE after many attempts to  fix a user setup (video driver, env vars, packages, etc).
A: Check for missing /run, or lack of permissions to write to it.  Happens when users upgrade from old releases (that used /var/run and  /var/lock instead of /run and /run/lock). Somehow the new install misses  the creation of /run and /run/lock. 
Check/Fix:```
if [ ! -d /run -a -d /var ]; then sudo ln -s /var/run /run && sudo mkdir -p /run/lock; fi
```[COLOR=Blue]16.[/COLOR]Unable to run apt-get. "Archive directory /var/cache/apt/archives/partial is missing"
Check/Fix:```
if [ ! -d /var/cache/apt/archives/partial ]; then sudo mkdir -p /var/cache/apt/archives/partial && sudo touch /var/cache/apt/archives/partial/lock && sudo chmod 640 /var/apt/cache/archives/lock && sudo apt-get clean; fi
```[COLOR=Blue]17.[/COLOR]System mounted in "Read Only" mode. User is unable to edit config files  or install any package, so no one can help him. All requested procedures  will fail until it is set rw again. Happens when user has  errors=remount-ro in fstab.
Check/Fix:```
if [ $(sudo mount | grep -i "on / type" | awk '{ print $6 }') == "(ro)" ]; then sudo mount -f -o remount,rw -t $(sudo mount | grep -i "on / type" | awk '{ print $5}') $(sudo mount | grep -i "on / type" | awk '{ print $1}') /; fi
```[COLOR=Blue]18.[/COLOR]Just tried installing Precise for the first time today, using Alpha 1. I have an nvidia gs7600 card.
Installation went fine but on reboot the system repeatedly hung without  booting to the Desktop. The 'nomodeset' option did not help.
Updating the packages from the recovery mode terminal didn't work  either, nor did trying to start lightdm after a terminal log in.
What finally allowed booting to the Desktop was removing all nvidia packages and then reinstalling *nvidia-current* (which also installed nvidia-settings).```
sudo apt-get purge nvidia*
 sudo apt-get install nvidia-current
```

---

### Post by arpanaut on 2011-11-29
Could you Please put these code snippets into code tags!
They would be much easier to read, cut/paste etc.
It would separate the explanation and make the presentation much nicer.
That list just looks awful as it is now...

---

### Post by cariboo on 2011-11-29
> **arpanaut said:**
> Could you Please put these code snippets into code tags!
They would be much easier to read, cut/paste etc.
It would separate the explanation and make the presentation much nicer.
That list just looks awful as it is now...

You should have seen it before I removed all the bolding. :)

---

### Post by arpanaut on 2011-11-29
LOL I did, hence my comments.
Your edit works better, I just prefer code tags for clarity and separation.

---

### Post by ventrical on 2011-11-29
> **cariboo907 said:**
> You should have seen it before I removed all the bolding. :)


You're right .. it is ugly.

  I'll try a different set.

apologies.

---

### Post by sudodus on 2011-11-29
Thanx 4 a nice list!
This should be my territory, but there are always things to learn ;-)

> **ventrical said:**
> Here is the Top Ten Codes (not neccessarily in order and open to interperetation) of PP Crash Recovery Codes -[COLOR=Navy]To be updated:[/COLOR]
...
[COLOR=Navy]8.[/COLOR]**lsb_release -a**  #This command will tell you what Version of Ubuntu you are using. It will help validate  and document that the prior commands have worked properly.

[COLOR=Navy]9. [/COLOR]**sudo dpkg -i --configure -a**  #This command will continue to install packages that may have been broken during download or if your download unexpectedly terminated or if you have had a power-failure.

These two were new to me. Finally a command line to printout the nickname! I have been lucky so far, no power-failure during upgrading ...
> 
[COLOR=Navy]10.[/COLOR]**sudo reboot -sudo shutdown**  
...I would suggest
```

sudo reboot    # or
sudo poweroff
``` instead, ***poweroff*** is equivalent to ```
sudo shutdown -P now
```

---

### Post by ventrical on 2011-11-29
> **arpanaut said:**
> LOL I did, hence my comments.
Your edit works better, I just prefer code tags for clarity and separation.

Done..

---

### Post by ventrical on 2011-11-29
> **sudodus said:**
> Thanx 4 a nice list!
This should be my territory, but there are always things to learn ;-)


These two were new to me. Finally a command line to printout the nickname! I have been lucky so far, no power-failure during upgrading ...
I would suggest
```

sudo reboot    # or
sudo poweroff
``` instead, ***poweroff*** is equivalent to ```
sudo shutdown -P now
```


Thanks .. done.

 I apologize for my non-ambiance format ;) I'm just trying to get some stuff up while I have some time . I do intend to add a little ambiance as it progresses.

---

### Post by arpanaut on 2011-11-29
I understand this is a "Work in Progress"
Just trying to give a nudge in the right direction.

You have to admit that it looks and reads much better now.
Thanks!

---

### Post by ronacc on 2011-11-29
one that I have found helpful for fixing broken packages is .

```
sudo apt-get -f install 
```

will install any packages necessary to fix the broken package if they are  available . If some necessary packages are not available you can use this to remove the broken one .

```
sudo apt-get -f remove 
```

---

### Post by ventrical on 2011-11-29
> **ronacc said:**
> one that I have found helpful for fixing broken packages is .

```
sudo apt-get -f install 
```will install any packages necessary to fix the broken package if they are  available . If some necessary packages are not available you can use this to remove the broken one .

```
sudo apt-get -f remove 
```


Thanks for  your help ronacc. Those are up there now. I'll just keep putting them up , then hope to organize or index them and bring them current as the list get larger.

---

### Post by ventrical on 2011-11-29
> **arpanaut said:**
> I understand this is a "Work in Progress"
Just trying to give a nudge in the right direction.

You have to admit that it looks and reads much better now.
Thanks!


Thank you for the nudge. :)

---

### Post by effenberg0x0 on 2011-11-29
Not sure if you consider these to be relevant for this list, but I think they are quite frequent:

1) Unsolvable weird crash messages at most init procedures, ending in a "black screen" (or a console screen), no DM/DE after many attempts to fix a user setup (video driver, env vars, packages, etc).
A: Check for missing /run, or lack of permissions to write to it. Happens when users upgrade from old releases (that used /var/run and /var/lock instead of /run and /run/lock). Somehow the new install misses the creation of /run and /run/lock. 
Check/Fix:
```
if [ ! -d /run -a -d /var ]; then sudo ln -s /var/run /run && sudo mkdir -p /run/lock; fi
```2) Unable to run apt-get. "Archive directory /var/cache/apt/archives/partial is missing"
Check/Fix:
```
if [ ! -d /var/cache/apt/archives/partial ]; then sudo mkdir -p /var/cache/apt/archives/partial && sudo touch /var/cache/apt/archives/partial/lock && sudo chmod 640 /var/apt/cache/archives/lock && sudo apt-get clean; fi

```3) System mounted in "Read Only" mode. User is unable to edit config files or install any package, so no one can help him. All requested procedures will fail until it is set rw again. Happens when user has errors=remount-ro in fstab.
Check/Fix:
```
if [ $(sudo mount | grep -i "on / type" | awk '{ print $6 }') == "(ro)" ]; then sudo mount -f -o remount,rw -t $(sudo mount | grep -i "on / type" | awk '{ print $5}') $(sudo mount | grep -i "on / type" | awk '{ print $1}') /; fi
```

---

### Post by ronacc on 2011-11-29
perhaps when the list gets more complete it can be stickied to general help or where it is thought most useful , even now it's too good to get buried when this forum closes , too few people think to look back through the forum archives .

---

### Post by ventrical on 2011-11-29
> **ronacc said:**
> perhaps when the list gets more complete it can be stickied to general help or where it is thought most useful , even now it's too good to get buried when this forum closes , too few people think to look back through the forum archives .

The older, closed forums, are so voluminous that it makes it difficult to centralize a search. I have worked on fragmented databases before. It's one of the things I do.  I looked at the old Lucid forum.  A real mountain to tackle there.

  I hope too that the mods will sticky this both here and in general help perhaps.. After all it is a group effort.

Thanks ronacc.

---

### Post by ventrical on 2011-11-29
> **effenberg0x0 said:**
> Not sure if you consider these to be relevant for this list, but I think they are quite frequent:

1) Unsolvable weird crash messages at most init procedures, ending in a "black screen" (or a console screen), no DM/DE after many attempts to fix a user setup (video driver, env vars, packages, etc).
A: Check for missing /run, or lack of permissions to write to it. Happens when users upgrade from old releases (that used /var/run and /var/lock instead of /run and /run/lock). Somehow the new install misses the creation of /run and /run/lock. 
Check/Fix:
```
if [ ! -d /run -a -d /var ]; then sudo ln -s /var/run /run && sudo mkdir -p /run/lock; fi
```2) Unable to run apt-get. "Archive directory /var/cache/apt/archives/partial is missing"
Check/Fix:
```
if [ ! -d /var/cache/apt/archives/partial ]; then sudo mkdir -p /var/cache/apt/archives/partial && sudo touch /var/cache/apt/archives/partial/lock && sudo chmod 640 /var/apt/cache/archives/lock && sudo apt-get clean; fi

```3) System mounted in "Read Only" mode. User is unable to edit config files or install any package, so no one can help him. All requested procedures will fail until it is set rw again. Happens when user has errors=remount-ro in fstab.
Check/Fix:
```
if [ $(sudo mount | grep -i "on / type" | awk '{ print $6 }') == "(ro)" ]; then sudo mount -f -o remount,rw -t $(sudo mount | grep -i "on / type" | awk '{ print $5}') $(sudo mount | grep -i "on / type" | awk '{ print $1}') /; fi
```

 Thanks effenberg. Yup .. I'll put those up. for sure.

edit .. done !

---

### Post by ventrical on 2011-11-29
ok... tried somthing but did not work :) I tired to forward(paste) the list  to current msg.

---

### Post by effenberg0x0 on 2011-11-29
> **ventrical said:**
> The older, closed forums, are so voluminous that it makes it difficult to centralize a search. I have worked on fragmented databases before. It's one of the things I do.  I looked at the old Lucid forum.  A real mountain to tackle there.

  I hope too that the mods will sticky this both here and in general help perhaps.. After all it is a group effort.

Thanks ronacc.

Last development cycle we had no centralized topics like this, the bug one, it became impossible to preserve our content, point users to threads dealing with bugs we already had discussed / developed workarounds. Won't happen this time... I'll also save both threads locally, just to be sure, April 15th. It's in my agenda.

---

### Post by ventrical on 2011-11-29
> **effenberg0x0 said:**
> Last development cycle we had no centralized topics like this, the bug one, it became impossible to preserve our content, point users to threads dealing with bugs we already had discussed / developed workarounds. Won't happen this time... I'll also save both threads locally, just to be sure, April 15th. It's in my agenda.


 I think that the bug_forum you concepted has a good format. It is going to look good after a while. Less chaos! :)

---

### Post by effenberg0x0 on 2011-11-29
> **ventrical said:**
> I think that the bug_forum you concepted has a good format. It is going to look good after a while. Less chaos! :)

I hope its potential users can understand it and benefit from it. As soon as it has some volume, I plan on contacting some helpers, developers, triagers, etc to let them know this is being done for them.

---

### Post by seeker5528 on 2011-11-30
> **ventrical said:**
> @effenberg,

This one here is an example of an important crash recovery code.
```

################################################## # Reinstalls all critical DM/DE packages apt-get install --reinstall --fix-broken --allow-unauthenticated lightdm lightdm-gtk-greeter unity unity-2d unity-2d-launcher unity-2d-panel unity unity-2d-places unity-greeter unity-lens-music unity-services unity-2d unity-2d-spread unity-lens-applications unity-place-applications unity-2d-launcher unity-asset-pool unity-lens-files unity-place-files unity-2d-panel unity-common unity-lens-gwibber unity-scope-musicstores compiz compiz-dev compiz-kde compiz-plugins-main-default compizconfig-backend-gconf compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev compizconfig-backend-kconfig compiz-fusion-plugins-extra compiz-plugins-default compizconfig-settings-manager compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome compiz-plugins-main
```  In security  with windows it was an often used process to uninstall/reinstall the security program and 8 times out of 10 it would work. It would overwrite or remove config files and unbork the registry.

At what point does the temption to do....
```
sudo /lib/recovery-mode/options/dpkg
```
instead come into play. This is the script that runs if you boot to the recovery menu and choose 'dpkg', if you hadn't guessed already. ;)

If you are using btrfs for your file system and have apt-btrfs-snapshot installed, this might be of interest...
```
sudo /lib/recovery-mode/options/apt-snapshots
```

Later, Seeker

---

### Post by ventrical on 2011-11-30
> **seeker5528 said:**
> At what point does the temption to do....
```
sudo /lib/recovery-mode/options/dpkg
```instead come into play. This is the script that runs if you boot to the recovery menu and choose 'dpkg', if you hadn't guessed already. ;)

If you are using btrfs for your file system and have apt-btrfs-snapshot installed, this might be of interest...
```
sudo /lib/recovery-mode/options/apt-snapshots
```Later, Seeker

  I chose the first line of code , ran it, chose No and got this:

```

dale1@ubuntu:~$ sudo /lib/recovery-mode/options/dpkg
[sudo] password for dale1: 
rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory
rm: cannot remove `/var/cache/apt/archives/partial/*': No such file or directory

Reading cache
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 

Calculating the changes

Do you want to start the upgrade? 


1 package is going to be removed. 27 packages are going to be 
upgraded. 

You have to download a total of 7357 k. This download will take about 
56 seconds with a 1Mbit DSL connection and about 17 minutes with a 
56k modem. 

 Continue [yN]  Details [d]N

Ign http://extras.ubuntu.com precise InRelease
Ign http://archive.canonical.com natty InRelease
Ign http://archive.ubuntu.com precise InRelease
Ign http://archive.ubuntu.com precise-updates InRelease
Ign http://archive.ubuntu.com precise-security InRelease
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://archive.canonical.com natty Release.gpg
Ign http://archive.ubuntu.com precise-proposed InRelease
Ign http://archive.ubuntu.com precise-backports InRelease
Hit http://archive.ubuntu.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release   
Hit http://archive.canonical.com natty Release                        
Hit http://archive.ubuntu.com precise-updates Release.gpg             
Hit http://archive.ubuntu.com precise-security Release.gpg           
Hit http://archive.ubuntu.com precise-proposed Release.gpg           
Hit http://extras.ubuntu.com precise/main i386 Packages              
Hit http://archive.canonical.com natty/partner i386 Packages         
Hit http://archive.ubuntu.com precise-backports Release.gpg
Ign http://extras.ubuntu.com precise/main TranslationIndex           
Ign http://archive.canonical.com natty/partner TranslationIndex      
Hit http://archive.ubuntu.com precise Release  
Hit http://archive.ubuntu.com precise-updates Release                          
Hit http://archive.ubuntu.com precise-security Release                         
Hit http://archive.ubuntu.com precise-proposed Release                         
Hit http://archive.ubuntu.com precise-backports Release                        
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://archive.ubuntu.com precise/restricted Sources             
Hit http://archive.ubuntu.com precise/universe Sources               
Hit http://archive.ubuntu.com precise/multiverse Sources             
Hit http://archive.ubuntu.com precise/main i386 Packages             
Hit http://archive.ubuntu.com precise/restricted i386 Packages       
Hit http://archive.ubuntu.com precise/universe i386 Packages         
Hit http://archive.ubuntu.com precise/multiverse i386 Packages       
Hit http://archive.ubuntu.com precise/main TranslationIndex          
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex    
Hit http://archive.ubuntu.com precise/restricted TranslationIndex    
Hit http://archive.ubuntu.com precise/universe TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/main Sources           
Hit http://archive.ubuntu.com precise-updates/restricted Sources     
Hit http://archive.ubuntu.com precise-updates/universe Sources       
Hit http://archive.ubuntu.com precise-updates/multiverse Sources     
Hit http://archive.ubuntu.com precise-updates/main i386 Packages     
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages 
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex  
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://archive.ubuntu.com precise-security/main Sources          
Hit http://archive.ubuntu.com precise-security/restricted Sources    
Hit http://archive.ubuntu.com precise-security/universe Sources      
Hit http://archive.ubuntu.com precise-security/multiverse Sources    
Hit http://archive.ubuntu.com precise-security/main i386 Packages    
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages
Hit http://archive.ubuntu.com precise-security/universe i386 Packages
Hit http://archive.ubuntu.com precise-security/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-security/main TranslationIndex 
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex
Hit http://archive.ubuntu.com precise-proposed/restricted i386 Packages
Hit http://archive.ubuntu.com precise-proposed/main i386 Packages    
Hit http://archive.ubuntu.com precise-proposed/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-proposed/universe i386 Packages
Hit http://archive.ubuntu.com precise-proposed/main TranslationIndex 
Hit http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-proposed/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-proposed/universe TranslationIndex
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://archive.ubuntu.com precise-backports/main i386 Packages   
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Ign http://extras.ubuntu.com precise/main Translation-en_CA          
Ign http://archive.canonical.com natty/partner Translation-en_CA     
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://archive.ubuntu.com precise/main Translation-en_CA         
Hit http://archive.ubuntu.com precise/main Translation-en            
Hit http://archive.ubuntu.com precise/multiverse Translation-en      
Hit http://archive.ubuntu.com precise/restricted Translation-en      
Hit http://archive.ubuntu.com precise/universe Translation-en        
Hit http://archive.ubuntu.com precise-updates/main Translation-en    
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en             
Ign http://archive.canonical.com natty/partner Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Hit http://archive.ubuntu.com precise-security/main Translation-en
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise-security/universe Translation-en
Hit http://archive.ubuntu.com precise-proposed/main Translation-en
Hit http://archive.ubuntu.com precise-proposed/multiverse Translation-en
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en
Hit http://archive.ubuntu.com precise-proposed/universe Translation-en
Hit http://archive.ubuntu.com precise-backports/main Translation-en
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Reading package lists... Done
N: Ignoring file 'ppa_file.txt' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ppa_file.txt' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ppa_file.txt' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libx264-116 libgnomeui-common libbonoboui2-common libbonoboui2-0
  libgnome2-vfs-perl libgnomecanvas2-0 libgnomeui-0 libmagickcore3
  libgnomecanvas2-common libmagick++3 libmagickwand3 libmagickcore3-extra
  libmatroska4 libgnome2-canvas-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
N: Ignoring file 'ppa_file.txt' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ppa_file.txt' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bluez bluez-alsa bluez-cups bluez-gstreamer command-not-found
  command-not-found-data iptables libbluetooth3 libmission-control-plugins0
  libmono-cairo4.0-cil libmono-corlib4.0-cil libmono-csharp4.0-cil
  libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-posix4.0-cil
  libmono-security4.0-cil libmono-sharpzip4.84-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-drawing4.0-cil libmono-system-security4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil mono-4.0-gac mono-gac
  mono-runtime telepathy-mission-control-5
27 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,357 kB of archives.
After this operation, 326 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main libbluetooth3 i386 4.96-3ubuntu2 [63.3 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise/main command-not-found-data i386 0.2.44.1ubuntu1 [964 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise/main command-not-found all 0.2.44.1ubuntu1 [7,338 B]
Get:4 http://archive.ubuntu.com/ubuntu/ precise/main iptables i386 1.4.12-1ubuntu3 [361 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ precise/main bluez i386 4.96-3ubuntu2 [620 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ precise/main bluez-alsa i386 4.96-3ubuntu2 [44.4 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ precise/main bluez-cups i386 4.96-3ubuntu2 [24.4 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ precise/main bluez-gstreamer i386 4.96-3ubuntu2 [61.4 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ precise/main telepathy-mission-control-5 i386 1:5.10.1-0ubuntu2 [192 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ precise/main libmission-control-plugins0 i386 1:5.10.1-0ubuntu2 [17.6 kB]
Get:11 http://archive.ubuntu.com/ubuntu/ precise/main libmono-system-xml4.0-cil all 2.10.5-1ubuntu1 [440 kB]
Get:12 http://archive.ubuntu.com/ubuntu/ precise/main libmono-system-security4.0-cil all 2.10.5-1ubuntu1 [61.3 kB]
Get:13 http://archive.ubuntu.com/ubuntu/ precise/main libmono-system-configuration4.0-cil all 2.10.5-1ubuntu1 [58.9 kB]
Get:14 http://archive.ubuntu.com/ubuntu/ precise/main libmono-system4.0-cil all 2.10.5-1ubuntu1 [664 kB]
Get:15 http://archive.ubuntu.com/ubuntu/ precise/main libmono-security4.0-cil all 2.10.5-1ubuntu1 [126 kB]
Get:16 http://archive.ubuntu.com/ubuntu/ precise/main mono-runtime i386 2.10.5-1ubuntu1 [1,521 kB]
Get:17 http://archive.ubuntu.com/ubuntu/ precise/main mono-gac all 2.10.5-1ubuntu1 [13.9 kB]
Get:18 http://archive.ubuntu.com/ubuntu/ precise/main mono-4.0-gac all 2.10.5-1ubuntu1 [19.8 kB]
Get:19 http://archive.ubuntu.com/ubuntu/ precise/main libmono-corlib4.0-cil all 2.10.5-1ubuntu1 [1,008 kB]
Get:20 http://archive.ubuntu.com/ubuntu/ precise/main libmono-cairo4.0-cil all 2.10.5-1ubuntu1 [29.9 kB]
Get:21 http://archive.ubuntu.com/ubuntu/ precise/main libmono-posix4.0-cil all 2.10.5-1ubuntu1 [84.2 kB]
Get:22 http://archive.ubuntu.com/ubuntu/ precise/main libmono-system-core4.0-cil all 2.10.5-1ubuntu1 [280 kB]
Get:23 http://archive.ubuntu.com/ubuntu/ precise/main libmono-csharp4.0-cil all 2.10.5-1ubuntu1 [415 kB]
Get:24 http://archive.ubuntu.com/ubuntu/ precise/main libmono-i18n4.0-cil all 2.10.5-1ubuntu1 [19.7 kB]
Get:25 http://archive.ubuntu.com/ubuntu/ precise/main libmono-i18n-west4.0-cil all 2.10.5-1ubuntu1 [27.9 kB]
Get:26 http://archive.ubuntu.com/ubuntu/ precise/main libmono-sharpzip4.84-cil all 2.10.5-1ubuntu1 [65.8 kB]
Get:27 http://archive.ubuntu.com/ubuntu/ precise/main libmono-system-drawing4.0-cil all 2.10.5-1ubuntu1 [167 kB]
Fetched 7,357 kB in 28s (257 kB/s)                                             
(Reading database ... 392708 files and directories currently installed.)
Preparing to replace libbluetooth3 4.96-3ubuntu1 (using .../libbluetooth3_4.96-3ubuntu2_i386.deb) ...
Unpacking replacement libbluetooth3 ...
Preparing to replace command-not-found-data 0.2.44ubuntu1 (using .../command-not-found-data_0.2.44.1ubuntu1_i386.deb) ...
Unpacking replacement command-not-found-data ...
Preparing to replace command-not-found 0.2.44ubuntu1 (using .../command-not-found_0.2.44.1ubuntu1_all.deb) ...
Unpacking replacement command-not-found ...
Preparing to replace iptables 1.4.12-1ubuntu2 (using .../iptables_1.4.12-1ubuntu3_i386.deb) ...
Unpacking replacement iptables ...
Preparing to replace bluez 4.96-3ubuntu1 (using .../bluez_4.96-3ubuntu2_i386.deb) ...
 * Stopping bluetooth                                                    [ OK ] 
Unpacking replacement bluez ...
Preparing to replace bluez-alsa 4.96-3ubuntu1 (using .../bluez-alsa_4.96-3ubuntu2_i386.deb) ...
Unpacking replacement bluez-alsa ...
Preparing to replace bluez-cups 4.96-3ubuntu1 (using .../bluez-cups_4.96-3ubuntu2_i386.deb) ...
Unpacking replacement bluez-cups ...
Preparing to replace bluez-gstreamer 4.96-3ubuntu1 (using .../bluez-gstreamer_4.96-3ubuntu2_i386.deb) ...
Unpacking replacement bluez-gstreamer ...
Preparing to replace telepathy-mission-control-5 1:5.10.1-0ubuntu1 (using .../telepathy-mission-control-5_1%3a5.10.1-0ubuntu2_i386.deb) ...
Unpacking replacement telepathy-mission-control-5 ...
Preparing to replace libmission-control-plugins0 1:5.10.1-0ubuntu1 (using .../libmission-control-plugins0_1%3a5.10.1-0ubuntu2_i386.deb) ...
Unpacking replacement libmission-control-plugins0 ...
Preparing to replace libmono-system-xml4.0-cil 2.10.5-1 (using .../libmono-system-xml4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-system-xml4.0-cil ...
Preparing to replace libmono-system-security4.0-cil 2.10.5-1 (using .../libmono-system-security4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-system-security4.0-cil ...
Preparing to replace libmono-system-configuration4.0-cil 2.10.5-1 (using .../libmono-system-configuration4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-system-configuration4.0-cil ...
Preparing to replace libmono-system4.0-cil 2.10.5-1 (using .../libmono-system4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-system4.0-cil ...
Preparing to replace libmono-security4.0-cil 2.10.5-1 (using .../libmono-security4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-security4.0-cil ...
Preparing to replace mono-runtime 2.10.5-1 (using .../mono-runtime_2.10.5-1ubuntu1_i386.deb) ...
Unpacking replacement mono-runtime ...
Preparing to replace mono-gac 2.10.5-1 (using .../mono-gac_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement mono-gac ...
Preparing to replace mono-4.0-gac 2.10.5-1 (using .../mono-4.0-gac_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement mono-4.0-gac ...
Preparing to replace libmono-corlib4.0-cil 2.10.5-1 (using .../libmono-corlib4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-corlib4.0-cil ...
Preparing to replace libmono-cairo4.0-cil 2.10.5-1 (using .../libmono-cairo4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-cairo4.0-cil ...
Preparing to replace libmono-posix4.0-cil 2.10.5-1 (using .../libmono-posix4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-posix4.0-cil ...
Preparing to replace libmono-system-core4.0-cil 2.10.5-1 (using .../libmono-system-core4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-system-core4.0-cil ...
Preparing to replace libmono-csharp4.0-cil 2.10.5-1 (using .../libmono-csharp4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-csharp4.0-cil ...
Preparing to replace libmono-i18n4.0-cil 2.10.5-1 (using .../libmono-i18n4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-i18n4.0-cil ...
Preparing to replace libmono-i18n-west4.0-cil 2.10.5-1 (using .../libmono-i18n-west4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-i18n-west4.0-cil ...
Preparing to replace libmono-sharpzip4.84-cil 2.10.5-1 (using .../libmono-sharpzip4.84-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-sharpzip4.84-cil ...
Preparing to replace libmono-system-drawing4.0-cil 2.10.5-1 (using .../libmono-system-drawing4.0-cil_2.10.5-1ubuntu1_all.deb) ...
Unpacking replacement libmono-system-drawing4.0-cil ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 changed doc-base files...
Registering documents with scrollkeeper...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up libbluetooth3 (4.96-3ubuntu2) ...
Setting up command-not-found-data (0.2.44.1ubuntu1) ...
Setting up command-not-found (0.2.44.1ubuntu1) ...
Setting up iptables (1.4.12-1ubuntu3) ...
Setting up bluez (4.96-3ubuntu2) ...
 * Starting bluetooth                                                    [ OK ] 
Setting up bluez-alsa (4.96-3ubuntu2) ...
Setting up bluez-cups (4.96-3ubuntu2) ...
Setting up bluez-gstreamer (4.96-3ubuntu2) ...
Setting up libmission-control-plugins0 (1:5.10.1-0ubuntu2) ...
Setting up telepathy-mission-control-5 (1:5.10.1-0ubuntu2) ...
Setting up libmono-security4.0-cil (2.10.5-1ubuntu1) ...
Setting up mono-4.0-gac (2.10.5-1ubuntu1) ...
Setting up mono-gac (2.10.5-1ubuntu1) ...
* Installing 3 assemblies from libappindicator0.1-cil into Mono
* Installing 1 assembly from libdbus1.0-cil into Mono
* Installing 1 assembly from libdbus-glib1.0-cil into Mono
* Installing 6 assemblies from libgconf2.0-cil into Mono
* Installing 14 assemblies from libgdata1.7-cil into Mono
* Installing 14 assemblies from libgdata1.8-cil into Mono
* Installing 1 assembly from libgkeyfile1.0-cil into Mono
* Installing 1 assembly from libglib2.0-cil into Mono
* Installing 1 assembly from libgmime2.4-cil into Mono
* Installing 5 assemblies from libgtk2.0-cil into Mono
* Installing 1 assembly from libgudev1.0-cil into Mono
* Installing 1 assembly from liblaunchpad-integration1.0-cil into Mono
* Installing 15 assemblies from libmono-addins0.2-cil into Mono
* Installing 5 assemblies from libmono-addins-gui0.2-cil into Mono
* Installing 5 assemblies from libmono-zeroconf1.0-cil into Mono
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono
* Installing 1 assembly from libnotify0.4-cil into Mono
* Installing 2 assemblies from libtaglib2.0-cil into Mono
* Installing 1 assembly from libubuntuone1.0-cil into Mono
* Installing 1 assembly from policy.2.10.atk-sharp into Mono
* Installing 1 assembly from policy.2.10.gdk-sharp into Mono
* Installing 1 assembly from policy.2.10.glib-sharp into Mono
* Installing 1 assembly from policy.2.10.gtk-dotnet into Mono
* Installing 1 assembly from policy.2.10.gtk-sharp into Mono
* Installing 1 assembly from policy.2.10.pango-sharp into Mono
* Installing 1 assembly from policy.2.4.atk-sharp into Mono
* Installing 1 assembly from policy.2.4.gdk-sharp into Mono
* Installing 1 assembly from policy.2.4.glib-sharp into Mono
* Installing 1 assembly from policy.2.4.gtk-dotnet into Mono
* Installing 1 assembly from policy.2.4.gtk-sharp into Mono
* Installing 1 assembly from policy.2.4.pango-sharp into Mono
* Installing 1 assembly from policy.2.6.atk-sharp into Mono
* Installing 1 assembly from policy.2.6.gdk-sharp into Mono
* Installing 1 assembly from policy.2.6.glib-sharp into Mono
* Installing 1 assembly from policy.2.6.gtk-dotnet into Mono
* Installing 1 assembly from policy.2.6.gtk-sharp into Mono
* Installing 1 assembly from policy.2.6.pango-sharp into Mono
* Installing 1 assembly from policy.2.8.atk-sharp into Mono
* Installing 1 assembly from policy.2.8.gdk-sharp into Mono
* Installing 1 assembly from policy.2.8.glib-sharp into Mono
* Installing 1 assembly from policy.2.8.gtk-dotnet into Mono
* Installing 1 assembly from policy.2.8.gtk-sharp into Mono
* Installing 1 assembly from policy.2.8.pango-sharp into Mono
Setting up mono-runtime (2.10.5-1ubuntu1) ...
Setting up libmono-corlib4.0-cil (2.10.5-1ubuntu1) ...
Setting up libmono-system-xml4.0-cil (2.10.5-1ubuntu1) ...
Setting up libmono-cairo4.0-cil (2.10.5-1ubuntu1) ...
Setting up libmono-i18n4.0-cil (2.10.5-1ubuntu1) ...
Setting up libmono-i18n-west4.0-cil (2.10.5-1ubuntu1) ...
Setting up libmono-system4.0-cil (2.10.5-1ubuntu1) ...
Setting up libmono-posix4.0-cil (2.10.5-1ubuntu1) ...
Setting up libmono-system-core4.0-cil (2.10.5-1ubuntu1) ...
Setting up libmono-csharp4.0-cil (2.10.5-1ubuntu1) ...
Setting up libmono-sharpzip4.84-cil (2.10.5-1ubuntu1) ...
Setting up libmono-system-drawing4.0-cil (2.10.5-1ubuntu1) ...
Setting up libmono-system-security4.0-cil (2.10.5-1ubuntu1) ...
Setting up libmono-system-configuration4.0-cil (2.10.5-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
N: Ignoring file 'ppa_file.txt' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ppa_file.txt' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ppa_file.txt' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

Finished, please press ENTER

dale1@ubuntu:~$ 
```

  I thought it was going to go to the recovery console?

---

### Post by seeker5528 on 2011-12-01
> **ventrical said:**
> I thought it was going to go to the recovery console?

I tried to figure out how to get the recovery menu, 'sudo /lib/recovery-mode/recovery-menu', but that doesn't give you the full menu of options you have when you boot using the recovery option on the grub menu.

Doing 'sudo /lib/recovery-mode/options/dpkg' should do the same thing as if you booted using the recovery option and then chose 'dpkg' from the menu.

If I remember correctly, when I ran it in the past it rewrote my sources.list file with the default sources, disabled any additional sources in '/etc/apt/sources.list.d/*.list' files, did it's best to get some base level of default apps installed, relative to the desktop metapackages installed, and dumped obsolete/locally installed packages.

If there is some kind of transition where some stuff is not installable due to version conflicts or whatever or are temprarily unavailable, you probably don't want to use it. 

If you know what you are doing and have installed stuff from this PPA and that PPA, you probably don't want to run it, or would want to do some PPA purge voodoo before hand. 

The more stuff you run from outside the official repositories the more chance for adding/removing stuff to fail. Or even a single PPA if the combination of packages provided result in a situation where it's more difficult to get back to the official packages.

Outside of that, it shouldn't do anything too drastic, so it makes for an easy thing to tell people to do in some cases where the alternative may be less drastic, but significantly more difficult to lead someone through with significant additional potential for human error to creep in.

Later, Seeker

---

### Post by ventrical on 2011-12-01
Thanks for your clarification.

---

### Post by ventrical on 2011-12-01
Here is a list of commonly used Ubuntu/Linux terminal Codes (not  neccessarily in order and open to interperetation) of PP Crash Recovery  Codes -[COLOR=Navy]To be updated:[/COLOR]

1. This command is used to auto edit the sources.list file on an install  of Oneiric Ocelot and could be considered as a first step to converting  to Precise Pangolin. However this and other commands may be moot after  Alpha .iso are released. You can still play it safe and test the kernels  but breakage may occur nonetheless. ```
**sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list**
```[COLOR=Blue]2.[/COLOR] This command will update your repositories to PP.```
**sudo apt-get update && sudo apt-get dist-upgrade**
```[COLOR=Navy]3.[/COLOR]This command is inclusive in #2. but is always good to run after removing or purging stuff.```
**sudo apt-get update**
```[COLOR=Navy]4.[/COLOR]This command is also included in #2. and upgrades any new files that are set in the repositories.```
**sudo apt-get upgrade**
```[COLOR=Navy]5.[/COLOR]This  command is an essential command if you are a elementary beta tester as  it will upgrade the GRUB bootloader after changes to the system using  other commands, are made (like upgrading a kernel). If you have tried to  carry out a proceedure and wonder why it had not taken effect on the  next boot, it is likely that you did not  sudo update-grub.```
**sudo update-grub**
```[COLOR=Navy]6.[/COLOR]This command will give you simple information about your system, most commonly used to discover your video adapter.```
**lspci**
```[COLOR=Navy]7.[/COLOR]This command  will display  version information of the kernel you are using.```
**uname -a**
```[COLOR=Navy]8.[/COLOR]This  command will tell you what Version of Ubuntu you are using. It will  help validate  and document that the prior commands have worked  properly.```
**lsb_release -a**
```[COLOR=Navy]9.[/COLOR]This  command will continue to install packages that may have been broken  during download or if your download unexpectedly terminated or if you  have had a power-failure.```
**sudo dpkg -i --configure -a**
```[COLOR=Navy]10.[/COLOR]These  two commands can be used separately if you are at the terminal prompt  from startup. You can get to the terminal (if you have no desktop) by  pressing the keys <Crtl+Alt+F1>   It makes booting and restarting  quicker and more efficient than if you were in a desktop shell.```
**sudo reboot -sudo poweroff** 
```[COLOR=Navy]11.[/COLOR]One that I have found helpful for fixing broken packages is .```
sudo apt-get -f install
```[COLOR=Blue]12.[/COLOR]Will  install any packages necessary to fix the broken package if they  are   available . If some necessary packages are not available you can  use  this to remove the broken one .```
sudo apt-get -f remove
```[COLOR=Blue]13.[/COLOR]Do  not rely on any inaccurate information from the user as to whether he   has (or not) added PPAs to his install. We just get the PPAs and read   them. Then we parse the PPAs (from ppa-file-name.list to PPA:razz:paname/package   format - which is the format required by the command ppa-purge)It will  output your current PPAs, parsed in a more useful form. )```
for  PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat $PPA_FILE | grep  "deb http" | sed -e 's|deb [http://||]("http://%7c%7c/")'   | sed -e 's|.launchpad.net/|\:|' | sed -e 's|/ubuntu||' | sed -e   's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e   's|main||' | tee -a /$HOME/ppa-sources.list; done
```[COLOR=Blue]14.[/COLOR]Attempts to fix a broken OO Install for NVidia 173 users # [EMAIL="Effenberg0x0@Launchpad.net"]Effenberg0x0@Launchpad.net[/EMAIL]```

#!/bin/bash ################################################## #  fix_oneiric.sh # Attempts to fix a broken OO Install for NVidia 173  users # Effenberg0x0@Launchpad.net #  ################################################## # # Save this file to  a known location, such as your Home Folder # Execute it with sudo chmod  +x fix-oneiric.sh && sudo bash ./fix-oneiric.sh #  ################################################## # Assume the env vars  we need may be wrong and get them # from safer sources  ROOT_PARTITION=$(mount | grep -i "on / type" | awk '{ print $1}')  ROOT_FS=$(mount | grep -i "on / type" | awk '{ print $5}')  ROOT_WRITE=$(mount | grep -i "on / type" | awk '{ print $6 }')  FIX_USER=$(cat /etc/passwd | grep 1000 | awk 'BEGIN { FS=":" }; {print  $1}')  ################################################## # Checks for a  rw filesystem and remounts if needed if [ $ROOT_WRITE == "(ro)" ]; then      mount -f -o remount,rw -t $ROOT_FS $ROOT_PARTITION / fi   ################################################## # Make sure GUI  sessions are stopped service stop lightdm service kill -s KILL $(pidof  lightdm) service stop gdm service kill -s KILL $(pidof gdm) killall -s  KILL /usr/bin/X  ################################################## #  Fixes user home permissions and ownership chown $FIX_USER:$FIX_USER  /home/$FIX_USER -R && sudo chmod 750 /home/$FIX_USER -R   ################################################## # Fixes Xauthority  bug mv /home/$FIX_USER/.Xauthority /home/$FIX_USER/.Xauthority.backup   ################################################## # Removes all nvidia  remains cd /home/$FIX_USER mkdir nvidia_driver cd nvidia_driver apt-get  remove --purge gdm nvidia-173 nvidia-96 nvidia-cg-toolkit  nvidia-current-updates nvidia-173-dev nvidia-96-dev nvidia-common  nvidia-current-updates-dev nvidia-173-updates nvidia-96-updates  nvidia-current nvidia-settings nvidia-173-updates-dev  nvidia-96-updates-dev nvidia-current-dev nvidia-settings-updates   ################################################## # Downloads nvidia  173 driver  wget  http://us.download.nvidia.com/XFree86/Linux-x86/173.14.31/NVIDIA-Linux-x86-173.14.31-pkg1.run   ################################################## # Exports needed  and correct environment variables export DISPLAY=:0.0 export  XDG_CURRENT_DESKTOP=Unity export  XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/  export COMPIZ_CONFIG_PROFILE=ubuntu export GDMSESSION=ubuntu export  DESKTOP_SESSION=ubuntu export  PATH=/home/$USER:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games  export XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0 export  XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0 export  DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path   ################################################## # Run nvidia  installer chmod +x NV* ./NV*   ################################################## # Reinstalls all  critical DM/DE packages apt-get install --reinstall --fix-broken  --allow-unauthenticated lightdm lightdm-gtk-greeter unity unity-2d  unity-2d-launcher unity-2d-panel unity unity-2d-places unity-greeter  unity-lens-music unity-services unity-2d unity-2d-spread  unity-lens-applications unity-place-applications unity-2d-launcher  unity-asset-pool unity-lens-files unity-place-files unity-2d-panel  unity-common unity-lens-gwibber unity-scope-musicstores compiz  compiz-dev compiz-kde compiz-plugins-main-default  compizconfig-backend-gconf compiz-fusion-bcop compiz-plugins  compiz-plugins-main-dev compizconfig-backend-kconfig  compiz-fusion-plugins-extra compiz-plugins-default  compizconfig-settings-manager compiz-fusion-plugins-main  compiz-plugins-extra compiz-core compiz-gnome compiz-plugins-main   ################################################## # Makes sure lightdm  was not started service lightdm stop   ################################################## # Fixes lightm  config bug (if needed) if [ ! -f /etc/lightdm/lightdm.conf ]; then sudo  touch /etc/lightdm/lightdm.conf echo -e  "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter"  | tee /etc/lightdm/lightdm.conf   ################################################## # Fixes  default-display-manager bug (if needed) if [ ! -f  /etc/X11/default-display-manager ]; then touch  /etc/X11/default-display-manager echo -e "/usr/sbin/lightdm" | tee  /etc/X11/default-display-manager    ################################################## # Makes sure  compiz/compiz-config settings are resetted gconftool-2 --recursive-unset  /apps/compiz-1 gconftool-2 --recursive-unset /apps/compizconfig-1   ################################################## # Backup of  compiz/configconfig settings mv $FIX_USER/.config/compiz-1/compizconfig  $FIX_USER/.config/compiz-1/compizconfig.old mv  $FIX_USER/.config/compiz-1 $FIX_USER/.config/compiz.old mv  $FIX_USER/.compiz-1 $FIX_USER/.compiz-1.old mv  $FIX_USER/.cache/compizconfig-1 $FIX_USER/.cache/compizconfig-1.old   ################################################## # Update/upgrade the  system and reboot apt-get update && apt-get upgrade reboot  now
```[COLOR=Blue]15.[/COLOR]Unsolvable weird crash messages  at most init procedures, ending in a  "black screen" (or a console  screen), no DM/DE after many attempts to  fix a user setup (video  driver, env vars, packages, etc).
A: Check for missing /run, or lack of permissions to write to it.   Happens when users upgrade from old releases (that used /var/run and   /var/lock instead of /run and /run/lock). Somehow the new install misses   the creation of /run and /run/lock. 
Check/Fix:```
if [ ! -d /run -a -d /var ]; then sudo ln -s /var/run /run && sudo mkdir -p /run/lock; fi
```[COLOR=Blue]16.[/COLOR]Unable to run apt-get. "Archive directory /var/cache/apt/archives/partial is missing"
Check/Fix:```
if [ ! -d /var/cache/apt/archives/partial ]; then sudo  mkdir -p /var/cache/apt/archives/partial && sudo touch  /var/cache/apt/archives/partial/lock && sudo chmod 640  /var/apt/cache/archives/lock && sudo apt-get clean; fi
```[COLOR=Blue]17.[/COLOR]System  mounted in "Read Only" mode. User is unable to edit config files  or  install any package, so no one can help him. All requested procedures   will fail until it is set rw again. Happens when user has   errors=remount-ro in fstab.
Check/Fix:```
if [ $(sudo mount | grep -i "on / type" | awk '{ print  $6 }') == "(ro)" ]; then sudo mount -f -o remount,rw -t $(sudo mount |  grep -i "on / type" | awk '{ print $5}') $(sudo mount | grep -i "on /  type" | awk '{ print $1}') /; fi
```[COLOR=Blue]18.[/COLOR]Just tried installing Precise for the first time today, using Alpha 1. I have an nvidia gs7600 card.
Installation went fine but on reboot the system repeatedly hung without   booting to the Desktop. The 'nomodeset' option did not help.
Updating the packages from the recovery mode terminal didn't work   either, nor did trying to start lightdm after a terminal log in.
What finally allowed booting to the Desktop was removing all nvidia packages and then reinstalling *nvidia-current* (which also installed nvidia-settings).```
sudo apt-get purge nvidia*
 sudo apt-get install nvidia-current
```

---

### Post by ventrical on 2011-12-11
> **effenberg0x0 said:**
> An example: This is one of the things I used a lot in General Help and feel like I'm gonna use 10x more now. It allows to:

- Not rely on any inaccurate information from the user as to whether he has (or not) added PPAs to his install. We just get the PPAs and read them. 
- Than we parse the PPAs (from ppa-file-name.list to PPA:ppaname/package format - which is the format required by the command ppa-purge)

(this need no suid)
for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat $PPA_FILE | grep "deb http" | sed -e 's|deb [http://||]("http://%7C%7C")' | sed -e 's|.launchpad.net/|\:|' | sed -e 's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e 's|main||' | tee -a /$HOME/ppa-sources.list; done




@effenberg

  I ran this code on a Precise install that has no PPAs and got the following output:

ventrical@ventrical-P4M266A-8237:~$ for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat $PPA_FILE | grep "deb http" | sed -e 's|deb [http://||](http://||)' | sed -e 's|.launchpad.net/|\:|' | sed -e 's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e 's|main||' | tee -a /$HOME/ppa-sources.list; done
ls: cannot access /etc/apt/sources.list.d/*: No such file or directory
ventrical@ventrical-P4M266A-8237:~$ 

So my question is : Is this essentially the output expected for a system with no PPAs?

regards , ventrical

---

### Post by effenberg0x0 on 2011-12-11
> **ventrical said:**
> @effenberg

  I ran this code on a Precise install that has no PPAs and got the following output:

ventrical@ventrical-P4M266A-8237:~$ for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat $PPA_FILE | grep "deb http" | sed -e 's|deb [http://||]("http://%7C%7C")' | sed -e 's|.launchpad.net/|\:|' | sed -e 's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e 's|main||' | tee -a /$HOME/ppa-sources.list; done
ls: cannot access /etc/apt/sources.list.d/*: No such file or directory
ventrical@ventrical-P4M266A-8237:~$ 

So my question is : Is this essentially the output expected for a system with no PPAs?

regards , ventrical

Hi Ventrical,

This line is part of a much larger script. The script does some checking somewhere in its beginning  to determine if a few default directories exist before calling specific functions like this one. AFAIK, as a default, /etc/apt/sources.list.d should exist in Ubuntu, even when the user hasn't ever added a PPA. But I might be wrong or, who knows, maybe the user might have removed/renamed it. 

So it would be nice to add some checking for the existence of the directory before proceeding. I have added an additional condition at the beginning, to see if the directory exists AND is not empty, before proceeding:

**if [[ -d /etc/apt/sources.list.d && $(ls -l /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir exists and is not empty\n\n"; **for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e 's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list; done; echo "PPA list saved at $HOME/ppa-sources.list"; **else echo -e "\n\nEmpty or inexistent PPA directory\n\n";** fi

---

### Post by ventrical on 2011-12-11
> **effenberg0x0 said:**
> Hi Ventrical,

This line is part of a much larger script. The script does some checking somewhere in its beginning  to determine if a few default directories exist before calling specific functions like this one. AFAIK, as a default, /etc/apt/sources.list.d should exist in Ubuntu, even when the user hasn't ever added a PPA. But I might be wrong or, who knows, maybe the user might have removed/renamed it. 

So it would be nice to add some checking for the existence of the directory before proceeding. I have added an additional condition at the beginning, to see if the directory exists AND is not empty, before proceeding:

**if [[ -d /etc/apt/sources.list.d && $(ls -l /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir exists and is not empty\n\n"; **for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e 's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list; done; echo "PPA list saved at $HOME/ppa-sources.list"; **else echo -e "\n\nEmpty or inexistent PPA directory\n\n";** fi


Ok.. I'll try that also. I was just going through some messages so I can update the sudo list.

  I do have the /sources.list.d directory but no file is in there.

---

### Post by effenberg0x0 on 2011-12-11
> **ventrical said:**
> Ok.. I'll try that also. I was just going through some messages so I can update the sudo list.

  I do have the /sources.list.d directory but no file is in there.

Exactly, this situation must return false, which is why I put both condition (dir exists AND has files) into the same test brackets in new shell script.

---

### Post by ronacc on 2011-12-11
not just ppa's show up int /etc/apt/sources.list.d  , any 3rd party software that has its own repo even if it is not an Ubuntu one shows up there . see attached entry from my sources.list.d for Opera browser .

---

### Post by ronacc on 2011-12-11
oops had to rename it from opera.list to opera.txt to get it to attach .

---

### Post by ventrical on 2011-12-11
> **effenberg0x0 said:**
> Hi Ventrical,

This line is part of a much larger script. The script does some checking somewhere in its beginning  to determine if a few default directories exist before calling specific functions like this one. AFAIK, as a default, /etc/apt/sources.list.d should exist in Ubuntu, even when the user hasn't ever added a PPA. But I might be wrong or, who knows, maybe the user might have removed/renamed it. 

So it would be nice to add some checking for the existence of the directory before proceeding. I have added an additional condition at the beginning, to see if the directory exists AND is not empty, before proceeding:

**if [[ -d /etc/apt/sources.list.d && $(ls -l /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir exists and is not empty\n\n"; **for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e 's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list; done; echo "PPA list saved at $HOME/ppa-sources.list"; **else echo -e "\n\nEmpty or inexistent PPA directory\n\n";** fi


That's precisely it !
ventrical@ventrical-P4M266A-8237:/usr$ if [[ -d /etc/apt/sources.list.d && $(ls -l /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir exists and is not empty\n\n"; for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e 's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list; done; echo "PPA list saved at $HOME/ppa-sources.list"; else echo -e "\n\nEmpty or inexistent PPA directory\n\n"; fi
ls: cannot access /etc/apt/sources.list.d/*: No such file or directory


Empty or inexistent PPA directory


ventrical@ventrical-P4M266A-8237:/usr$

---

### Post by ventrical on 2011-12-11
> **ronacc said:**
> oops had to rename it from opera.list to opera.txt to get it to attach .


Thanks ronacc.

---

### Post by effenberg0x0 on 2011-12-11
The important things are:
[LIST]
[*]It tells you whether the user has added or hasn't added something there.
[*]Tells you what was added
[*]Converts from a useless format...
[/LIST]
```
[10:04 PM][ahsl:AL-DESK:~/dev/unity/unity]
$ cat /etc/apt/sources.list.d/vincent-c-nevernote-precise.list
[B]deb http://ppa.launchpad.net/vincent-c/nevernote/ubuntu oneiric main
deb-src http://ppa.launchpad.net/vincent-c/nevernote/ubuntu oneiric main[/B]
```To a useful format...
```
[12:19 AM][ahsl:AL-DESK:~/dev/unity/unity]
$ cat ~/ppa-sources.list | grep -i nevernote
**ppa:vincent-c/nevernote** 
```...that fits what ppa-purge expects to receive:
```
[12:21 AM][ahsl:AL-DESK:~/dev/unity/unity]
$ sudo ppa-purge **ppa:vincent-c/nevernote **
[sudo] password for ahsl: 
```The alternative: To ask the user...

[LIST]
[*]If he has added an alternative source
[*]Which source / package / software
[*]From what PPA
[*]To locate, read files at /etc/apt/sources.list files and find out the correct syntax for ppa-purge
[*]Run ppa-purge for each found ppa
[/LIST]
... is impossible: Such a user would not need / ask for help. An average user will not be able to perform the steps above without consuming 1 hour of your day at the very least. Given the amount of other people in need of help in release week, it is too much to waste more than 5 minutes with such a basic issue. That's where this script is useful.

The full version reads the first block output ($HOME/ppa-sources.list) and ppa-purges all entries automatically. Then it sudo update/upgrade and reboots.

---

### Post by ventrical on 2011-12-22
Here are some common codes of interest to help with Precise recovery in the event of a crash.

**H**ow to find your souces.list- this list is used to set  repositories and can be done manually. It is also informative to have on  hand if you decide to do a transitional upgrade from Oneiric Ocelot to  Precise Pangolin.
```
[COLOR=Blue]/etc/apt/sources.list[/COLOR]
```
Precise Pangolin will not install: From initial  boot screen from LiveCD or LiveUSB you may receive verbose characters or  only purple or black  screen: 
- check here: [/COLOR][http://ubuntuforums.org/showpost.php?p=11518947&postcount=5](http://ubuntuforums.org/showpost.php?p=11518947&postcount=5)

[COLOR=Green]Your beta version of Firefox is Broken- here are two possible fixes:
[/COLOR][http://ubuntuforums.org/showpost.php?p=11530599&postcount=18](http://ubuntuforums.org/showpost.php?p=11530599&postcount=18)
[http://ubuntuforums.org/showpost.php?p=11530670&postcount=19](http://ubuntuforums.org/showpost.php?p=11530670&postcount=19)
[COLOR=YellowGreen] 
[/COLOR] Here is a list of commonly used Ubuntu/Linux terminal Codes (not  neccessarily in order and open to interperetation) of PP Crash Recovery  Codes -[COLOR=Navy]To be updated:[/COLOR]

1. This command is used to auto edit the sources.list file on an install  of Oneiric Ocelot and could be considered as a first step to converting  to Precise Pangolin. However this and other commands may be moot after  Alpha .iso are released. You can still play it safe and test the kernels  but breakage may occur nonetheless. ```
**sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list**
```[COLOR=Blue]2.[/COLOR] This command will update your repositories to PP.```
**sudo apt-get update && sudo apt-get dist-upgrade**
```[COLOR=Navy]3.[/COLOR]This command is inclusive in #2. but is always good to run after removing or purging stuff.```
**sudo apt-get update**
```[COLOR=Navy]4.[/COLOR]This command is also included in #2. and upgrades any new files that are set in the repositories.```
**sudo apt-get upgrade**
```[COLOR=Navy][COLOR=Blue]4.(a)[/COLOR][/COLOR]Update-manager  is a fairly important component of the Ubuntu  distribution. As we are  supposed to be testing during the development  phase, this application  would be helped by testing and bug reporting as  well.You can always  make a judgement call as to whether the changes proposed  by  update-manager seem safe or not. If in doubt I think the best way to   proceed is with aptitude:```
aptitude update && aptitude  safe-upgrade
```This alleviates the concern when  packages/dependencies may not be fully  synced in the repos. They will  be held back until dependencies are  satisfied.

[COLOR=Navy]5.[/COLOR]This command is an essential command if you  are a elementary beta tester as it will upgrade the GRUB bootloader  after changes to the system using other commands, are made (like  upgrading a kernel). If you have tried to carry out a proceedure and  wonder why it had not taken effect on the next boot, it is likely that  you did not  sudo update-grub.```
**sudo update-grub**
```[COLOR=Navy]6.[/COLOR]This command will give you simple information about your system, most commonly used to discover your video adapter.```
**lspci**
```[COLOR=Navy]7.[/COLOR]This command  will display  version information of the kernel you are using.```
**uname -a**
```[COLOR=Navy]8.[/COLOR]This  command will tell you what Version of Ubuntu you are using. It will  help validate  and document that the prior commands have worked  properly.```
**lsb_release -a**
```[COLOR=Navy]9.[/COLOR]This  command will continue to install packages that may have been broken  during download or if your download unexpectedly terminated or if you  have had a power-failure.```
**sudo dpkg -i --configure -a**
```[COLOR=Navy]10.[/COLOR]These  two commands can be used separately if you are at the terminal prompt  from startup. You can get to the terminal (if you have no desktop) by  pressing the keys <Crtl+Alt+F1>   It makes booting and restarting  quicker and more efficient than if you were in a desktop shell.```
**sudo reboot -sudo poweroff** 
```[COLOR=Navy]11.[/COLOR]One that I have found helpful for fixing broken packages is .```
sudo apt-get -f install
```[COLOR=Blue]12.[/COLOR]Will  install any packages necessary to fix the broken package if they  are   available . If some necessary packages are not available you can  use  this to remove the broken one .```
sudo apt-get -f remove
```[COLOR=Blue]13.[/COLOR]Do  not rely on any inaccurate information from the user as to whether he   has (or not) added PPAs to his install. We just get the PPAs and read   them. Then we parse the PPAs (from ppa-file-name.list to PPA:razz:paname/package  format - which is the format required by the command ppa-purge)```
**if  [[ -d /etc/apt/sources.list.d && $(ls -l   /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir   exists and is not empty\n\n"; **for PPA_FILE in $(ls   /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed   -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e   's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e   's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list;  done;  echo "PPA list saved at $HOME/ppa-sources.list"; **else echo -e "\n\nEmpty or inexistent PPA directory\n\n";** fi
```[COLOR=Blue]14.[/COLOR]Attempts to fix a broken OO Install for NVidia 173 users # [EMAIL="Effenberg0x0@Launchpad.net"]Effenberg0x0@Launchpad.net[/EMAIL]```

#!/bin/bash
################################################## 
# fix_oneiric.sh 
# Attempts to fix a broken OO Install for NVidia 173 users 
# Effenberg0x0@Launchpad.net 
# 
################################################## 
# 
# Save this file to a known location, such as your Home Folder # Execute  it with sudo chmod +x fix-oneiric.sh && sudo bash  ./fix-oneiric.sh 
# 
################################################## 
# Assume the env vars we need may be wrong and get them 
# from safer sources 
ROOT_PARTITION=$(mount | grep -i "on / type" | awk '{ print $1}') 
ROOT_FS=$(mount | grep -i "on / type" | awk '{ print $5}') 
ROOT_WRITE=$(mount | grep -i "on / type" | awk '{ print $6 }') 
FIX_USER=$(cat /etc/passwd | grep 1000 | awk 'BEGIN { FS=":" }; {print $1}') ################################################## 
# Checks for a rw filesystem and remounts if needed 
if [ $ROOT_WRITE == "(ro)" ]; then     
  mount -f -o remount,rw -t $ROOT_FS $ROOT_PARTITION / 
fi 
################################################## 
# Make sure GUI sessions are stopped 
service stop lightdm 
service kill -s KILL $(pidof lightdm) 
service stop gdm 
service kill -s KILL $(pidof gdm) 
killall -s KILL /usr/bin/X  
################################################## 
# Fixes user home permissions and ownership 
chown $FIX_USER:$FIX_USER /home/$FIX_USER -R && sudo chmod 750 /home/$FIX_USER -R  
################################################## 
# Fixes Xauthority bug 
mv /home/$FIX_USER/.Xauthority /home/$FIX_USER/.Xauthority.backup
 
################################################## 
# Removes all nvidia remains 
cd /home/$FIX_USER mkdir nvidia_driver cd nvidia_driver apt-get remove  --purge gdm nvidia-173 nvidia-96 nvidia-cg-toolkit  nvidia-current-updates nvidia-173-dev nvidia-96-dev nvidia-common  nvidia-current-updates-dev nvidia-173-updates nvidia-96-updates  nvidia-current nvidia-settings nvidia-173-updates-dev  nvidia-96-updates-dev nvidia-current-dev nvidia-settings-updates  
################################################## 
# Downloads nvidia 173 driver  
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.31/NVIDIA-Linux-x86-173.14.31-pkg1.run  
################################################## 
# Exports needed and correct environment variables
export DISPLAY=:0.0 export XDG_CURRENT_DESKTOP=Unity export  XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/  export COMPIZ_CONFIG_PROFILE=ubuntu export GDMSESSION=ubuntu export  DESKTOP_SESSION=ubuntu export  PATH=/home/$USER:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games  export XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0 export  XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0 export  DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path  ################################################## 
# Run nvidia installer 
chmod +x NV* 
./NV* 
################################################## 
# Reinstalls all critical DM/DE packages
apt-get install --reinstall --fix-broken --allow-unauthenticated lightdm  lightdm-gtk-greeter unity unity-2d unity-2d-launcher unity-2d-panel  unity unity-2d-places unity-greeter unity-lens-music unity-services  unity-2d unity-2d-spread unity-lens-applications  unity-place-applications unity-2d-launcher unity-asset-pool  unity-lens-files unity-place-files unity-2d-panel unity-common  unity-lens-gwibber unity-scope-musicstores compiz compiz-dev compiz-kde  compiz-plugins-main-default compizconfig-backend-gconf  compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev  compizconfig-backend-kconfig compiz-fusion-plugins-extra  compiz-plugins-default compizconfig-settings-manager  compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome  compiz-plugins-main ################################################## 
# Makes sure lightdm was not started 
service lightdm stop 
################################################## 
# Fixes lightm config bug (if needed) 
if [ ! -f /etc/lightdm/lightdm.conf ]; then sudo touch  /etc/lightdm/lightdm.conf echo -e  "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter"  | tee /etc/lightdm/lightdm.conf  
################################################## 
# Fixes default-display-manager bug (if needed) 
if [ ! -f /etc/X11/default-display-manager ]; then touch  /etc/X11/default-display-manager echo -e "/usr/sbin/lightdm" | tee  /etc/X11/default-display-manager    ################################################## 
# Makes sure compiz/compiz-config settings are resetted
gconftool-2 --recursive-unset /apps/compiz-1 gconftool-2 --recursive-unset /apps/compizconfig-1  
################################################## 
# Backup of compiz/configconfig settings 
mv $FIX_USER/.config/compiz-1/compizconfig  $FIX_USER/.config/compiz-1/compizconfig.old mv  $FIX_USER/.config/compiz-1 $FIX_USER/.config/compiz.old mv  $FIX_USER/.compiz-1 $FIX_USER/.compiz-1.old mv  $FIX_USER/.cache/compizconfig-1 $FIX_USER/.cache/compizconfig-1.old  
################################################## 
# Update/upgrade the system and reboot 
apt-get update && apt-get upgrade reboot now
```[COLOR=Blue]15.[/COLOR]Unsolvable  weird crash messages at most init procedures, ending in a  "black  screen" (or a console screen), no DM/DE after many attempts to  fix a  user setup (video driver, env vars, packages, etc).
A: Check for missing /run, or lack of permissions to write to it.   Happens when users upgrade from old releases (that used /var/run and   /var/lock instead of /run and /run/lock). Somehow the new install misses   the creation of /run and /run/lock. 
Check/Fix:```
if [ ! -d /run -a -d /var ]; then sudo ln -s /var/run /run && sudo mkdir -p /run/lock; fi
```[COLOR=Blue]16.[/COLOR]Unable to run apt-get. "Archive directory /var/cache/apt/archives/partial is missing"
Check/Fix:```
if [ ! -d /var/cache/apt/archives/partial ]; then sudo  mkdir -p /var/cache/apt/archives/partial && sudo touch  /var/cache/apt/archives/partial/lock && sudo chmod 640  /var/apt/cache/archives/lock && sudo apt-get clean; fi
```[COLOR=Blue]17.[/COLOR]System  mounted in "Read Only" mode. User is unable to edit config files  or  install any package, so no one can help him. All requested procedures   will fail until it is set rw again. Happens when user has   errors=remount-ro in fstab.
Check/Fix:```
if [ $(sudo mount | grep -i "on / type" | awk '{ print  $6 }') == "(ro)" ]; then sudo mount -f -o remount,rw -t $(sudo mount |  grep -i "on / type" | awk '{ print $5}') $(sudo mount | grep -i "on /  type" | awk '{ print $1}') /; fi
```[COLOR=Blue]18.[/COLOR]Just tried installing Precise for the first time today, using Alpha 1. I have an nvidia gs7600 card.
Installation went fine but on reboot the system repeatedly hung without   booting to the Desktop. The 'nomodeset' option did not help.
Updating the packages from the recovery mode terminal didn't work   either, nor did trying to start lightdm after a terminal log in.
What finally allowed booting to the Desktop was removing all nvidia packages and then reinstalling *nvidia-current* (which also installed nvidia-settings).```
sudo apt-get purge nvidia*
 sudo apt-get install nvidia-current
```

---

### Post by Ibidem on 2011-12-23
For ATI users:
fglrx uses xorg.conf, but syntax has changed in the past year (a 10.10 xorg.conf will get you a black screen).
So after upgrading, run:
```
 sudo rm /etc/X11/xorg.conf
sudo aticonfig --initial 
```

---

### Post by ventrical on 2011-12-24
I tried and tried and tried  and tried on my AMD 64bit Acer Extensa with ATI Radeon Express 1250 and it keeps saying <not supported> but works great with 32bit.

Thanks for the code. I'll insert it in there on the next  refresh :)

Going slow here for Christmas.

---

### Post by ventrical on 2012-01-31
Yep .. #18 is a good one.

[COLOR=Blue]18.[/COLOR]Just tried installing Precise for the first time today, using Alpha 1. I have an nvidia gs7600 card.
Installation went fine but on reboot the system repeatedly hung without    booting to the Desktop. The 'nomodeset' option did not help.
Updating the packages from the recovery mode terminal didn't work    either, nor did trying to start lightdm after a terminal log in.
What finally allowed booting to the Desktop was removing all nvidia packages and then reinstalling *nvidia-current* (which also installed nvidia-settings). 	Code:
 	sudo apt-get purge nvidia*  sudo apt-get install nvidia-current

---

### Post by ventrical on 2012-03-05
Bump! :)

---

### Post by ventrical on 2012-03-21
[COLOR=Blue]14.[/COLOR]Attempts to fix a broken OO Install for NVidia 173 users # [EMAIL="Effenberg0x0@Launchpad.net"]Effenberg0x0@Launchpad.net[/EMAIL]     
```

     #!/bin/bash ##################################################  # fix_oneiric.sh  # Attempts to fix a broken OO Install for NVidia 173 users  # [EMAIL="Effenberg0x0@Launchpad.net"]Effenberg0x0@Launchpad.net[/EMAIL]  #  ##################################################  #  # Save this file to a known location, such as your Home Folder # Execute  it with sudo chmod +x fix-oneiric.sh && sudo bash  ./fix-oneiric.sh  #  ##################################################  # Assume the env vars we need may be wrong and get them  # from safer sources  ROOT_PARTITION=$(mount | grep -i "on / type" | awk '{ print $1}')  ROOT_FS=$(mount | grep -i "on / type" | awk '{ print $5}')  ROOT_WRITE=$(mount | grep -i "on / type" | awk '{ print $6 }')  FIX_USER=$(cat /etc/passwd | grep 1000 | awk 'BEGIN { FS=":" }; {print $1}') ##################################################  # Checks for a rw filesystem and remounts if needed  if [ $ROOT_WRITE == "(ro)" ]; then        mount -f -o remount,rw -t $ROOT_FS $ROOT_PARTITION /  fi  ##################################################  # Make sure GUI sessions are stopped  service stop lightdm  service kill -s KILL $(pidof lightdm)  service stop gdm  service kill -s KILL $(pidof gdm)  killall -s KILL /usr/bin/X   ##################################################  # Fixes user home permissions and ownership  chown $FIX_USER:$FIX_USER /home/$FIX_USER -R && sudo chmod 750 /home/$FIX_USER -R   ##################################################  # Fixes Xauthority bug  mv /home/$FIX_USER/.Xauthority /home/$FIX_USER/.Xauthority.backup   ##################################################  # Removes all nvidia remains  cd /home/$FIX_USER mkdir nvidia_driver cd nvidia_driver apt-get remove  --purge gdm nvidia-173 nvidia-96 nvidia-cg-toolkit  nvidia-current-updates nvidia-173-dev nvidia-96-dev nvidia-common  nvidia-current-updates-dev nvidia-173-updates nvidia-96-updates  nvidia-current nvidia-settings nvidia-173-updates-dev  nvidia-96-updates-dev nvidia-current-dev nvidia-settings-updates   ##################################################  # Downloads nvidia 173 driver   wget [http://us.download.nvidia.com/XFree86/Linux-x86/173.14.31/NVIDIA-Linux-x86-173.14.31-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.31/NVIDIA-Linux-x86-173.14.31-pkg1.run)   ##################################################  # Exports needed and correct environment variables export DISPLAY=:0.0 export XDG_CURRENT_DESKTOP=Unity export  XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/  export COMPIZ_CONFIG_PROFILE=ubuntu export GDMSESSION=ubuntu export  DESKTOP_SESSION=ubuntu export  PATH=/home/$USER:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games  export XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0 export  XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0 export  DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path  ##################################################  # Run nvidia installer  chmod +x NV*  ./NV*  ##################################################  # Reinstalls all critical DM/DE packages apt-get install --reinstall --fix-broken --allow-unauthenticated lightdm  lightdm-gtk-greeter unity unity-2d unity-2d-launcher unity-2d-panel  unity unity-2d-places unity-greeter unity-lens-music unity-services  unity-2d unity-2d-spread unity-lens-applications  unity-place-applications unity-2d-launcher unity-asset-pool  unity-lens-files unity-place-files unity-2d-panel unity-common  unity-lens-gwibber unity-scope-musicstores compiz compiz-dev compiz-kde  compiz-plugins-main-default compizconfig-backend-gconf  compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev  compizconfig-backend-kconfig compiz-fusion-plugins-extra  compiz-plugins-default compizconfig-settings-manager  compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome  compiz-plugins-main ##################################################  # Makes sure lightdm was not started  service lightdm stop  ##################################################  # Fixes lightm config bug (if needed)  if [ ! -f /etc/lightdm/lightdm.conf ]; then sudo touch  /etc/lightdm/lightdm.conf echo -e  "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter"  | tee /etc/lightdm/lightdm.conf   ##################################################  # Fixes default-display-manager bug (if needed)  if [ ! -f /etc/X11/default-display-manager ]; then touch  /etc/X11/default-display-manager echo -e "/usr/sbin/lightdm" | tee  /etc/X11/default-display-manager    ##################################################  # Makes sure compiz/compiz-config settings are resetted gconftool-2 --recursive-unset /apps/compiz-1 gconftool-2 --recursive-unset /apps/compizconfig-1   ##################################################  # Backup of compiz/configconfig settings  mv $FIX_USER/.config/compiz-1/compizconfig  $FIX_USER/.config/compiz-1/compizconfig.old mv  $FIX_USER/.config/compiz-1 $FIX_USER/.config/compiz.old mv  $FIX_USER/.compiz-1 $FIX_USER/.compiz-1.old mv  $FIX_USER/.cache/compizconfig-1 $FIX_USER/.cache/compizconfig-1.old   ##################################################  # Update/upgrade the system and reboot  apt-get update && apt-get upgrade reboot now

```

---

