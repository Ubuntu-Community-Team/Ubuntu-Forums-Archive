---
title: "HOWTO: Gracefully Shutdown VirtualBox VMs on Reboot or Shutdown of Ubuntu"
date: 2009-02-23
forum: Tutorials
---

### Post by Jose Catre-Vandis on 2009-02-23
**HOWTO: Gracefully Shutdown VirtualBox VMs on Reboot or Shutdown of Ubuntu**

I always forget I have a GUI virtual machine open when I go to shutdown, usually because it is on another desktop, out of sight. This howto will show you how to avoid the same thing, and to put any VMs you have open into a saved state, ready for a quick start up next time.

Before we go any further...

**What this howto will not do:**

1. Save VMs when you CTRL+ALT+BKSPACE.
2. Save VMS when you Log Out.
3. Save VMs from VMware, Xen, Qemu, etc.

That out of the way, all the work is done by a bash script and a bit of configuration on your system. As with all things, there are some caveats
to be mentioned. The script will work on headless as well as GUI virtual machines, however, there seems to be a bug in VirtualBox that will not allow a saved GUI VM open up as Headless. A saved Headless VM will happily open up as a GUI VM, but for some reason not around the other way. My focus is on sorting things out for desktop GUI VMs. 

The difficulties arise in using a script like vboxtool (which handles headless VMs well, is that all the work has to happen while the window and display managers (GDM/GNOME or GDM/XFCE) are still up and running, hence why you cannot simply write a script and pop it in "init.d" and then update-rc.d it. I know, I spent a week on it!

So we have to run the script from the desktop while the GUI is up, in order to safely close/save desktop VMs. Adding on the shutdown and reboot routines just adds to the fun :)

**Requirements:**

1. Virtualbox (tested on closed source version 2.1.4)
2. Installed virtual machines (do your own thing here)
3. Debian derivative distro with sudoers file (requires editing)
4. Zenity (for GUI dialogs)
5. Replacement of <!user!> with your username in the script and in the sudoers file

This username should be the logged on user and that of the creator /installer of  VirtualBox. (So take a default installation of Ubuntu where you create a user as a part of the install. Once complete you install VBox as that user, and so on)

**Setup:**

Assumes knowledge of installing VirtualBox and VMs

Copy the script to your home directory and make executable
```
chmod +x ~/shut.vm
```

Install zenity:  
```
sudo apt-get install zenity
```

Edit your sudoers file (in a terminal):

```
sudo visudo
```

scroll to the bottom of the file and add the following

```
<!user!> ALL = NOPASSWD: /sbin/shutdown
<!user!> ALL = NOPASSWD: /etc/init.d/vboxdrv
<!user!> ALL = NOPASSWD: /etc/init.d/preload
```

replacing <!user!> with your username
And save out the file. The effects are immediate.
These changes allow your user (you) to run the shutdown, vboxdrv stop
and preload stop commands without having to enter your password.


Look in the script for any lines that contain:
```
sudo -H -u -<!user!>
```
and replace <!user!> with your username (there are 4 lines!)
```
sudo nano ~/shut.vm
```

**Running the script:**

Assuming code is in your home directory and you have made it executable,
you can then run the script from a terminal:
```
~/shut.vm
```

An easier way is to set up a launcher and point the launcher
to the script. Because of the different ways of doing this in various
distros the actual process of adding a button to your taskbar will
not be covered here, but documentation is widely available.

**Comments:**

I found that I needed to close the vboxdrv and preload services on
my test machine, before shutdown/reboot. If you don't have preload
installed, the command doesn't appear to have any adverse effect.
If it does, then remove the lines with 
```
sudo /etc/init.d/preload stop
```
in them, or comment them out with a "#" at the beginning of the line.
```
sudo nano ~/shut.vm
```
to edit.

If you run the script from a terminal, apart from the zenity dialogs
you should get plenty of feedback about what is going on and where
you are in the process.

Also plenty of more info in the script about what is going on :)


**The script in all its glory:**
> #!/bin/bash
# /shut.vm
# Author: Jose Catre-Vandis  (Joe90)
# Web:    [www.bimma.me.uk](www.bimma.me.uk)

# Tested on XUBUNTU 8.10 with VirtualBox 2.1.4 (2.1_2.1.4-42893)

########################################################################

# Requirements

# Virtualbox
# Installed virtual machines
# Debian derivative distro with sudoers file (requires editing)
# Zenity
# Replacement of <!user!> with your username in the script and in
#+the sudoers file
# This username should be the logged on user and that of the creator
#+/installer of VirtualBox. (So take a default installation of Ubuntu
#+where you create a user as a part of the install. Once complete you
#+install VBox as that user, and so on)

########################################################################

# Setup

# Assumes knowledge of installing VirtualBox and VMs
# Install zenity:  "sudo apt-get install zenity"
# edit your sudoers file (in a terminal):

# sudo visudo
# scroll to the bottom of the file and add the following
#+(don't include the #'s in the sudoers file!):

# <!user!> ALL = NOPASSWD: /sbin/shutdown
# <!user!> ALL = NOPASSWD: /etc/init.d/vboxdrv
# <!user!> ALL = NOPASSWD: /etc/init.d/preload

# replacing <!user!> with your username
# And save out the file. The effects are immediate.

# Look in the script for any lines that contain:
# sudo -H -u -<!user!>
# replace <!user!> with your username

########################################################################

# Running the script

# Script Location. you can put it anywhere you like. I run it out of
#+my home directory. You will need to make it executable:
# chmod +x ~/shut.vm

# You can then run the script from a terminal:
# ~/shut.vm

# An easier way is to set up a launcher and point the launcher
#+to the script. Because of the different ways of doing this in various
#+distros the actual process of adding a button to your taskbar will
#+not be covered here, but documentation is widely available.

########################################################################

# Lists running VMs and puts in array RUNVMLIST

# Here we first iterate through a list of any VMs that
#+are running, then we extract the names of the VMs and
#+add them to an array.
# Then we report (in a terminal if run that way), which
#+VMs are running and how many there are.

########################################################################

declare -a RUNVMLIST
vmnum=0

   for running in $(VBoxManage -nologo list runningvms)
    do
    	name=$(VBoxManage -nologo showvminfo $running | grep "Name:" | awk 'BEGIN{FS="Name:            "}{print $2}')
	    RUNVMLIST=( "${RUNVMLIST[@]}" "$name")
	    vmnum=$(($vmnum + 1))
    done



   if [ ! "$running" ] 
    then
	 echo "No VMs running"
    else
     echo "Running VMs = "${RUNVMLIST[*]}
	 echo "Number of VMs Running = "${#RUNVMLIST[*]}
   fi

########################################################################

# Takes all this info and uses it as you shut down or reboot 
# to gracefully close and save any open VMs

# First off you get a Zenity dialog asking if you want to
#+Shutdown or Reboot, or Cancel the closedown. If you click
#+OK, you then are provided with a second Zenity dialog asking
#+if you want to Shutdown (OK) or Reboot (Cancel).
# If you choose OK (the Shutdown routine) the script then has a
#+look at the array to see if there are any running VMs. If there
#+are no running VMs, the script will proceed directly to Shutdown.
# If there are running VMs, the script will first save the state of 
#+each VM in turn, putting up a Zenity progress dialog which you
#+can leave alone as it auto closes, then we proceed to Shutdown. 
# A similar thing happens if you choose Cancel (the Reboot routine)
#+only that after the save of states, you go to Reboot.

# I found that I needed to close the vboxdrv and preload services on
#+my test machine, before shutdown/reboot. If you don't have preload
#+installed, the command doesn't appear to have any adverse effect.
#+If it does, then remove the lines with "sudo /etc/init.d/preload stop"
#+in them, or comment them out with a "#" at the beginning of the line.  

########################################################################

	zenity  --text="Click OK if you want to Shutdown or Reboot. Click Cancel to resume." --title="Shutdown or Reboot?" --width="320"  --height="150" --question
	closeorcancel=$?
		if [ "${closeorcancel}" == "0" ]
	     then
		    echo "You chose to Shutdown or Reboot"
		 else
		    echo "You chose to Cancel and resume your work"
		    exit
		fi
	zenity  --text="Click OK if you want to Shutdown. Click Cancel to Reboot." --title="Shutdown or Reboot?" --width="320"  --height="150" --question
	shutorboot=$?
		if [ "${shutorboot}" == "0" ]
		 then
		    echo "You chose to Shutdown"
		    if [ ! ${RUNVMLIST[*]}]
		 	 then
			  echo "No VMs open, straight to shutdown"
			  sudo -H -u <!user!> /etc/init.d/vboxdrv stop
			  sudo /etc/init.d/preload stop
			  sudo /sbin/shutdown -h now
		     else
		      echo "All open VMs will be closed to a saved state"
		      for vm in ${RUNVMLIST[*]}
	            do
	  		      (VBoxManage controlvm $vm savestate) | zenity --progress --pulsate --width="320"  --height="150" --title="Please Wait while VMs are Saved" --auto-close
	  		      echo "$vm was closed to a saved state"
		        done
			 echo "Shutting down now"
			 sudo -H -u <!user!> /etc/init.d/vboxdrv stop
			 sudo /etc/init.d/preload stop
		     sudo /sbin/shutdown -h now
		    fi
		else
		    echo "You chose to Reboot"
		    if [ ! ${RUNVMLIST[*]}]
		     then
			  echo "No VMs open, straight to reboot"
			  sudo -H -u <!user!> /etc/init.d/vboxdrv stop
			  sudo /etc/init.d/preload stop
			  sudo /sbin/shutdown -r now
		     else
		      echo "All open VMs will be closed to a saved state"
		      for vm in ${RUNVMLIST[*]}
		        do
			      (VBoxManage controlvm $vm savestate) | zenity --progress --pulsate --width="320"  --height="150" --title="Please Wait while VMs are Saved" --auto-close
			      echo "$vm was closed to a saved state"
		        done	
		     echo "Rebooting Now"
		     sudo -H -u <!user!> /etc/init.d/vboxdrv stop
		     sudo /etc/init.d/preload stop
		     sudo /sbin/shutdown -r now
		     fi
		 fi

exit

I have also attached the script in a zip file for downloading.

**Undoing what you have done:**

1. Delete the script!
2. Reverse the changes made in your sudoers file
3. Uninstall zenity (though not necessary)
```
sudo apt-get remove zenity
```

Happy to help with questions, comments, problems, etc, and will probably add some simpler scripts for just saving VMs or gathering info. Will also welcome any suggestions for improvements or developments of the script. I would particularly like to know how to link this up with the standard shutdown/reboot buttons in Ubuntu/Xubuntu to avoid having to create a new shortcut to the script, and streamline things...

Credits to the writer/s of **vboxtool**, the best starter-stopper of headless VMs there is (imho), for a couple of snippets of code here and there, and to markba on Ubuntuforums, and TerryE on virtualbox forums for help and pointers

---

### Post by woodenfox on 2009-03-29
I'm getting errors when running the script:

$ sh shut.vm
shut.vm: 74: declare: not found
shut.vm: 80: Syntax error: "(" unexpected (expecting "done")

---

### Post by Jose Catre-Vandis on 2009-03-30
> **woodenfox said:**
> I'm getting errors when running the script:

$ sh shut.vm
shut.vm: 74: declare: not found
shut.vm: 80: Syntax error: "(" unexpected (expecting "done")

Hmmm, that appears to be related to this part of the code:
```
declare -a RUNVMLIST
vmnum=0

   for running in $(VBoxManage -nologo list runningvms)
    do
    	name=$(VBoxManage -nologo showvminfo $running | grep "Name:" | awk 'BEGIN{FS="Name:            "}{print $2}')
	    RUNVMLIST=( "${RUNVMLIST[@]}" "$name")
	    vmnum=$(($vmnum + 1))
    done



   if [ ! "$running" ] 
    then
	 echo "No VMs running"
    else
     echo "Running VMs = "${RUNVMLIST[*]}
	 echo "Number of VMs Running = "${#RUNVMLIST[*]}
   fi
```(lines 74 through to 92)

Open a terminal and try typing:
```
declare -a RUNVMLIST
``` to see what happens (you should just get taken back to a command prompt.

If this works OK, copy the above code into a text file, add a "#!/bin/bash" to the top of the file save it and make it executable. then try running it in a terminal to see what you get?

---

### Post by jnylen on 2009-05-19
You have to run that script with bash - i.e.:
```
$ bash shut.vm
```
Instead of:
```
$ sh shut.vm
```

A better way is to just do:
```
chmod +x shut.vm
```
then:
```
./shut.vm
```

---

### Post by Jonners59 on 2010-11-30
Hi I tried this, following step by step - bearing in mind I am not a techie, so just copied, but it did not work.  I tried a couple of reboots but the virtual machine would not start.

No adverse effects, just did not work.  Any ideas?

---

### Post by CharlesA on 2010-12-01
Hi there,

I wrote up a quick and dirty script to do what you want.

Only hitch is that you need to add this to the sudoers file with ***sudo visudo***

```
<username> ALL = NOPASSWD: /sbin/shutdown
```

Here's the scripts:

stopvmgui.sh
```

#!/bin/bash

###
### stopvmgui.sh
### Saves state on any running VM and prompts to shutdown or restart
### Created by CharlesA
### Tested 12/01/2010
###

USR=/usr/bin/

${USR}zenity --question --text Shutdown? --title Shutdown?
if [[ $? = 0 ]]
then
  if [[ -n $(${USR}VBoxManage -nologo list runningvms) ]]
  then
  for runningvms in $(${USR}VBoxManage -nologo list runningvms | ${USR}awk -F \" '{ print $2 }';)
  do
  ${USR}VBoxManage -nologo controlvm $runningvms savestate && sudo shutdown -h now
  done
  else
  echo "No VMs running" && sudo shutdown -h now
  fi
else
${USR}zenity --question --text Reboot? --title Reboot?
if [[ $? = 0 ]]
  then
    if [[ -n $(${USR}VBoxManage -nologo list runningvms) ]]
    then
    for runningvms in $(${USR}VBoxManage -nologo list runningvms | ${USR}awk -F \" '{ print $2 }';)
    do
    ${USR}VBoxManage -nologo controlvm $runningvms savestate && sudo shutdown -r now
    done
    else
    echo "No VMs running" && sudo shutdown -r now
    fi
  else
    exit
    fi
fi
# eof

```

startvmgui.sh
```
#!/bin/bash

###
### startvm.sh
### Script to start saved VMs
### Created by CharlesA
### Tested 12/01/2010
###

BIN=/bin/
USR=/usr/bin/

for vms in $(${USR}VBoxManage -nologo list vms | ${USR}awk -F \" '{ print $2 }';)
do
if [[ -n $(${USR}VBoxManage showvminfo $vms | ${BIN}grep saved) ]]
then
${USR}VirtualBox --startvm $vms &
fi
done
# eof

```

Place both scripts in yer home directory and create a launcher on the desktop to stopvmgui.sh.

Add startvmgui.sh to System > Preferences > Startup Applications.

Double click on the launcher and it'll run the script. :)

Thanks to Jose Catre-Vandis, for giving me a base to work with for zenity. :)

---

### Post by Jonners59 on 2010-12-02
thanks Charles.
I assumed that to create a launcher on the desktop you meant make a link, which I have done and added it to the Startup apps.

I also assume all I need do is wait until I need to reboot and the scripts will take care of starting up my virtual machine.

---

### Post by CharlesA on 2010-12-02
You'd just have to launch the stopvm script and it'll ask you if you want to shutdown, hit no and it'll ask you if you want to reboot.

---

### Post by Jonners59 on 2010-12-02
> **CharlesA said:**
> You'd just have to launch the stopvm script and it'll ask you if you want to shutdown, hit no and it'll ask you if you want to reboot.

Did that, and yes it did, so that kinda does what you'd expect.

I did a reboot, but again, whilst the virtualbox ap opened, as it did before, the virtual machine within it still does not - wife gave me a ticking off, she was mid call to her mother.  Oh, err....!   I'll check next time! :redface:

---

### Post by CharlesA on 2010-12-02
Did it save the state of the VM at least?

Also where did you put the scripts? They are meant to be run from the home directory, but I could modify them to run from anywhere without much difficulty.

---

### Post by Jonners59 on 2010-12-02
> **CharlesA said:**
> Did it save the state of the VM at least?

Also where did you put the scripts? They are meant to be run from the home directory, but I could modify them to run from anywhere without much difficulty.

I could not tell.  When the Virtual machine starts it automatically starts my WIndows7, within which I have all the apps I want to start at startup in the startup folder, so they load automatically anyway.

I saved it here.  Would not allow me to save in home itself, so assumed thatw as where you wanted it.  Bad boy?
/home/server/

---

### Post by CharlesA on 2010-12-02
> **Jonners59 said:**
> I could not tell.  When the Virtual machine starts it automatically starts my WIndows7, within which I have all the apps I want to start at startup in the startup folder, so they load automatically anyway.

I saved it here.  Would not allow me to save in home itself, so assumed thatw as where you wanted it.  Bad boy?
/home/server/
That's the right place to put it, since it goes in the user's home directory. :)

If the script is working, it should say something like "restoring machine state" and everything will be exactly the way you left it before you did the reboot.

---

### Post by Jonners59 on 2010-12-02
> **CharlesA said:**
> That's the right place to put it, since it goes in the user's home directory. :)

If the script is working, it should say something like "restoring machine state" and everything will be exactly the way you left it before you did the reboot.

That's, but no it did not come up with any messages, certainly not "restoring machine state".

---

### Post by CharlesA on 2010-12-02
Try running the vmstartgui.sh script in a terminal and post the output. I tested it with virtualbox-ose but it should work with the non-free edition, as they startvms the same way.

---

### Post by Jonners59 on 2010-12-02
> **CharlesA said:**
> Try running the vmstartgui.sh script in a terminal and post the output. I tested it with virtualbox-ose but it should work with the non-free edition, as they startvms the same way.

It just made the screen flicker...

---

### Post by CharlesA on 2010-12-02
> **Jonners59 said:**
> It just made the screen flicker...
Ok. When you open VirtualBox, does it say "saved" under status?

---

### Post by Jonners59 on 2010-12-02
No, sorry....

---

### Post by Jose Catre-Vandis on 2010-12-16
@ Jonners59

Are you still stuck?

---

### Post by Jonners59 on 2010-12-16
> **Jose Catre-Vandis said:**
> @ Jonners59

Are you still stuck?
Jose
Thank you....  I am having a nightmare actually.  The DNLA issue I have out has still not been reolved (a different thread) and now the VM is behaving like a pig, or at least the OS/App I run in it...  I am at the stage where something is going to fly out the window soon!

I am off to Italy tomorrow at 4AM to pick up and bring back the mother-in-law, so will not be doing anything over the next 24hrs.  Just had to go out and buy a new printer as our packed up today and I can't print the boarding passes.  Just managed to get it working.  GGrr

So if you are offering to help, thank you, but please forgive my rudeness, bu not for 48 hrs please

---

### Post by Jose Catre-Vandis on 2010-12-17
No problems. Get in touch when ready either via thread or a pm.

---

### Post by Jose Catre-Vandis on 2011-01-14
We got Jonners sorted out in the end I believe. Here's a transcript of requirements:


1. Test the creation of a saved state of an open VM, and then successfully open it up again (using the GUI) ?

2. Next stage will be to do this via the command line. Once that works we can look at how to close VMs down when we ask Ubuntu to closedown (can't do anything about Ubuntu crashing I am afraid!), then on how we start a VM when we start Ubuntu (either from fresh, or from a saved state)

Right, now, as it seems your VM is happy to savestate and resume, we can move onto the next stage. I am going to give you fish as well as teach you how to fish, this is why I am doing it in stages.

You need to now learn how to save and resume your VM from a terminal. Get your VM up and running.

1. Open a terminal
2. Type the following:

VBoxManage -nologo list runningvms

You should get back something like this:

"XP" {afa231b5-397f-4b34-ad33-249c82cb1579}

("XP" is the name of the vm I am using, replace XP with the name of your vm, but keep the "")

3. Then type as follows:

VBoxManage -nologo controlvm XP savestate

You should see dots and percentages going up from 10%, and your vm will close. You have saved your vm. You can close your Virtualbox application!

4. Now type this (replacing XP with the name of your vm and make sure you put the & at the end!:

VirtualBox --startvm "XP" &

Your vm should now start up where you left off. You will also notice that you have no main application - more screen real estate! You can always open it up if you need it.

Right with all this working OK, you know that your vm is happy being saved and resuming from the cli. Now we need a script to start it up when Ubuntu starts. Let's assume your vm is the only vm you want to start.

Back to the terminal:

sudo nano /usr/bin/startvm.sh

Enter or copy/paste the following into the terminal/nano window

#!/bin/bash
sleep 60
/usr/bin/VirtualBox --startvm XP &

Then press CTRL+X, Y, and Enter.
Make it executable:

sudo chmod 755 /usr/bin/startvm.sh

Now you need to add this script to your startup.

I use Xubuntu so I go to Xfce Settings Manager -> Sessions and Startup, there is a similar place in Ubuntu where you can add a program you want to start on boot (after login!)

the command you want to enter is:

/usr/bin/startvm.sh


Right that should be it. I have set the timer at 60 seconds, which should ensure your desktop has set itself up and that the vboxdrv driver is in place. You might try editing the script to sleep 30 or less and see if it starts?

OK close your vm (you have the command now!), and reboot. With any luck your vm should start, just where you left off.

You can use CharlesA's shutdown script (a few posts above this one) to gracefully close down your vm's.

---

### Post by Jonners59 on 2011-01-20
Problems, Problems...
I had to do a reboot after an Ubuntu update.
The auto start we created would not work, it came up with an error message saying "3cx server" did not exist, so I tried to start using the Gui, and got the enclosed message....  See screenshot.

I then decided to start from scratch and rebuild the whole thing again.

Just saved the image following the instructions, which shut it down...  I then restarted it with the command [HTML]VirtualBox --startvm "3cx server" &[/HTML] and ended up with the same error message.  I tried again with the Gui, see attached.

Help.  I don't want to rebuild again.  Can this be saved and what is going wrong?

---

### Post by CharlesA on 2011-01-20
It sounds like you had a snapshot or something and it's not accessible.

Make sure the VHD file is in ~/.VirtualBox

---

### Post by Jonners59 on 2011-01-21
There is no file *.VHD  I searched the "File System" too.
How do I re-create it?

This is a bummer, just when I thought I had it licked!

---

### Post by CharlesA on 2011-01-21
well, it should be a .vdi or a .vmdk file, but if you are using Virtualbox 3.x, they'll be in ~/.VirtualBox/HardDisks IIRC.

---

### Post by Jonners59 on 2011-01-21
> **CharlesA said:**
> well, it should be a .vdi or a .vmdk file, but if you are using Virtualbox 3.x, they'll be in ~/.VirtualBox/HardDisks IIRC.

OK, CHarles
I found 3cx server.vdi in the "Hard Disks" folder in .VirtualBox

What do I do now???????

---

### Post by CharlesA on 2011-01-21
It would probably be better to post over on the virtualbox forums.

See here: [http://forums.virtualbox.org/viewtopic.php?f=1&t=23617&start=0](http://forums.virtualbox.org/viewtopic.php?f=1&t=23617&start=0)

---

### Post by Jonners59 on 2011-01-22
Solution
In the Gui, go to the "Machines Manager".
Look for the faulty machine in the list.  You should notice it has sub images.  Delete the last one...  And keep doing so until it works.  As long as you do not delete the base image it will work.

---

### Post by Jonners59 on 2011-01-22
Bingo, many thanks

The answer lay in "File" - "Virtual Media Manager" - "Hard Disks"

Then just delete the last "Child" to the hard disk causing the probs...

---

### Post by Jonners59 on 2011-03-22
I had a hard drive failure on my PC that we set up and had to rebuild everything from scratch.  I tried to set up the scripts you gave but I noticed on reboots and yesterday I had a an auto restart in my absence, the scripts did not work.  The VM did not restart.  Virtual Box started, but a message, "could not start 3CX Server" comes up.

Any help, please?  I am sure I have just not ticked a box some-where.

---

### Post by CharlesA on 2011-03-22
Hi,

Does it work if you start it up manually?

---

### Post by Jonners59 on 2011-03-22
Yes, that is why I have been slow in getting it fixed.  I kinda sat on it....

PS it is the same machine we worked on a few months back, called "server"

---

### Post by CharlesA on 2011-03-22
Hrm. It's got a space in the machine name right?

---

### Post by Jonners59 on 2011-03-23
> **CharlesA said:**
> Hrm. It's got a space in the machine name right?

Yes, it is "3cx server"

I may well have installed all the stuff you and Jose gave me, which worries me a little.

PS.  Sorry for the delay in getting back.  Been manic.

---

### Post by Jose Catre-Vandis on 2011-03-23
So compare the commands you use for the bootup version against your manual one - is there any difference?

---

### Post by Jonners59 on 2011-03-23
> **Jose Catre-Vandis said:**
> So compare the commands you use for the bootup version against your manual one - is there any difference?

OK, you lost me!  Can you explain idiot proof.  I.e. Me, step by step.

Just tried reinstalling the scripts again...  This is what I got on restarting my PC...  see enclosed

PS as per Jose's suggestion I did not use Charle's shutdown script...  does that matter?

---

### Post by Jose Catre-Vandis on 2011-03-26
The whole point of this thread was to ensure a graceful shutdown of VM's. If you don't shut them down gracefully (this would be the same/similar to a power failure or pulling the plug) you may encounter boot up errors next time around. So use a shutdown script in order to (hopefully) eliminate these problems.

Re your query, you must be using a startup script somewhere, and in there will be the command you have to start a vm. Compare this with the command you input manually to get the vm started, just to check there are no differences

You also might have a problem that vboxdrv has not fully loaded before you try to run the vm, so you might need to put some wait/sleep time in the script.

---

### Post by Jonners59 on 2011-03-26
Sorry, I was meant to say startup, not shutdown...

I shall take another look, but so far I have seen no differences in what was done before.

---

### Post by miatawnt2b on 2011-10-19
I'm looking for some way of doing an acpi shutdown automatically when logging out of gnome.  From the command line I can issue the 'vboxmanage controlvm Windows7 acpipowerbutton' which works great, so I had thought that I'd just put this in a script that's placed in /etc/GDM/PostSession

Unfortunately, it doesn't work and I think that Gnome doesn't even get as far as running scripts when the VM is running... I still will get the virtualbox dialog saying it's keeping gnome from logging out.

So is there any way to issue the vboxmanage command when using the stock gnome logout/shutdown dialog? 

-J

---

### Post by CharlesA on 2011-10-19
You'd have to have it running as a startup/shutdown script.

Check out the thread [here]("http://ubuntuforums.org/showthread.php?t=1844885").

---

### Post by miatawnt2b on 2011-10-19
> **CharlesA said:**
> You'd have to have it running as a startup/shutdown script.

Check out the thread [here]("http://ubuntuforums.org/showthread.php?t=1844885").

Isn't gnome still going to puke when trying to logout? Doesn't Gnome try to close all programs before the OS even gets to the init.d scripts?

Also, I really don't want my VM's to run on every startup.  I would like the control of starting manually, but automatically shutting down when I log out of gnome.

Thanks!
-J

---

### Post by CharlesA on 2011-10-19
I'm not sure, as I don't run any VMs on a box with Gnome.

---

