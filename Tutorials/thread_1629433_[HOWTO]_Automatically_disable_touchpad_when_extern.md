---
title: "[HOWTO] Automatically disable touchpad when external mouse connected"
date: 2010-11-23
forum: Tutorials
---

### Post by brennydoogles on 2010-11-23
[SIZE="4"]**Introduction:**[/SIZE]
If you're like me, you hate using your touchpad when you could be using an external mouse. If you're like me you also have a habit of disabling your touchpad when using a mouse, and forgetting to re-enable it until after you unplug your mouse. If you're like me, this tutorial is exactly what you need.

[SIZE="4"]**What you need to get started:**[/SIZE]
You will need to make sure that you have xinput and halevt installed. You almost certainly already have xinput, but the following command will make sure you have what you need:
```
sudo apt-get install xinput halevt
```

I also recommend that you create a folder for scripts (if you haven't already), and add it to your $PATH. I created a "bin" folder in my home directory for this. Create the folder with:
```
mkdir ~/bin
```
and add it to your path by issuing the following commands:
```

echo "PATH=\$PATH:~/bin" >> ~/.bashrc
echo "export PATH" >> ~/.bashrc

```

[SIZE="4"]**Configure the script:**[/SIZE]
First we need to create and configure the script which will actually toggle the touchpad:
```

cd ~/bin
touch toggleTouchpad
gedit toggleTouchpad

```

The script should now be open in gedit (feel free to replace gedit with your favorite text editor). Paste the following into the script:
```

# toggleTouchpad by Brendon Dugan
# Toggles a touchpad on or off depending on it's current state or CLI argument
#
# To configure, run the command 'xinput list' in terminal and identify your touch pad.
# Using the output of the above command, change the touchpadString variable to a substring
# of your touchpad's description that is unique to that device.
#
# To run, simply type 'toggleTouchpad' to toggle your touchpad on or off, or
# 'toggleTouchpad on' to explicitly turn your touchpad on, or
# 'toggleTouchpad off' to explicitly turn it off.
#
# Enjoy!


# A function for logging
safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod +rw $1; 
fi
}
logdir=/home/$USER/.toggleTouchpad
touchpadString="TouchPad"
touchpadID=$(xinput list | grep $touchpadString | awk -F " " '{print $6}' | awk -F "=" '{print $2}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')
sleeptime=1

# Create the logging directory
safemk $logdir
touch $logdir/errorLog.txt

# Check for arguments on the command line
if test $# -eq 1
then
	# Change the argument to lowercase
	arg1=$(echo $1 | tr [:upper:] [:lower:])
	cliArg=1
else
	# There is no argument.
	cliArg=0
fi

if [ $cliArg -eq 1 ]
then
	# If there's an argument, check to see whether it is on, off, or junk
	if [ $arg1 = 'on' ]
	then
		# The argument was 'on', so turn the touchpad on
		xinput --set-prop $touchpadID "Device Enabled" 1
		if [ $(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}') -eq 0 ]
		then
			echo "Something went wrong\n" >> $logdir/errorLog.txt
		fi
	elif [ $arg1 = 'off' ]
	then
		# Sleep for a short time to fix a bug that re-enabled the touchpad immediately after disabling it
		sleep $sleeptime
		# The argument was 'off', so turn the touchpad off 
		xinput --set-prop $touchpadID "Device Enabled" 0
		if [ $(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}') -eq 1 ]
		then
			echo "Something went wrong, perhaps \$sleeptime needs to be greater than $sleeptime ?\n" >> $logdir/errorLog.txt
		fi
	else
		# The argument was junk, so log the error and go on 
		echo "Invalid argument \""$arg1"\" was supplied\n" >> $logdir/errorLog.txt
	fi
else
	# There was no argument, so just toggle the touchpad to the opposite
	# of the state it has now.
	if [ $touchpadEnabled -eq 1 ]
	then
		xinput --set-prop $touchpadID "Device Enabled" 0
	else
		xinput --set-prop $touchpadID "Device Enabled" 1
	fi
fi

```

Now make the script executable by running:
```

 chmod +x ~/bin/toggleTouchpad

```

Ok, we're almost configured. We need to make sure that your touchpad will be affected by the script. Run the following command to get a list of all current input devices:
```

xinput -list

```
It should have an output something like this:
```

brendon@brendon-lappy-linux:~$ xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech BT Mini-Receiver      	id=15	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M             	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]
    &#8627; Logitech Logitech BT Mini-Receiver      	id=14	[slave  keyboard (3)]
brendon@brendon-lappy-linux:~$ 

```
If your touchpad has the word "TouchPad" (case sensitive) in it, the script is ready to go. If it doesn't, edit the variable "touchpadString" in the script to match your touchpad... but remember everything is case sensitive. For now, your script is configured. Next step is testing.

[SIZE="4"]**Test the script:**[/SIZE]
Make sure your touchpad is working, and then open a new terminal window. We are going to do four tests. Before and after each test, try your touchpad.

Test 1:
```
toggleTouchpad
```
Did your touchpad stop working? Good!

Test 2:
```
toggleTouchpad
```
Did your touchpad start working again? Good!

Test 3:
```
toggleTouchpad off
```
Wait at least one second...
Did your touchpad stop working? Good!

Test 4:
```
toggleTouchpad on
```
Wait at least one second...
Did your touchpad start working again? Good!

[SIZE="4"]**Making the magic happen automatically:**[/SIZE]
We're almost there! Now we need to set the script to run automatically when your mouse is plugged in. Making sure your mouse is unplugged, run the following command:
```
halevt -i >>~/connectedDevices.txt
```
While the command is running, plug in your mouse, and then unplug it. Now press Ctrl +c to kill the process. Open ~/connectedDevices.txt, and you should see something that looks like:
```

New Device: /org/freedesktop/Hal/devices/usb_device_46d_b02_noserial
New Device: /org/freedesktop/Hal/devices/usb_device_46d_b02_noserial_if0
New Device: /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023
New Device: /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023_if0
New Device: /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023_if0_logicaldev_input
New Device: /org/freedesktop/Hal/devices/usb_device_46d_c70a_00076142E023
New Device: /org/freedesktop/Hal/devices/usb_device_46d_c70a_00076142E023_if0
New Device: /org/freedesktop/Hal/devices/usb_device_46d_c70a_00076142E023_if0_logicaldev_input
Device removed: /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023_if0_logicaldev_input
Device removed: /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023_if0
Device removed: /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023
Device removed: /org/freedesktop/Hal/devices/usb_device_46d_c70a_00076142E023_if0_logicaldev_input
Device removed: /org/freedesktop/Hal/devices/usb_device_46d_b02_noserial_if0
Device removed: /org/freedesktop/Hal/devices/usb_device_46d_c70a_00076142E023_if0
Device removed: /org/freedesktop/Hal/devices/usb_device_46d_c70a_00076142E023
Device removed: /org/freedesktop/Hal/devices/usb_device_46d_b02_noserial

```

All of those devices are your mouse. Since each of those events will trigger every time you plug in your mouse, we only need to handle one of them. Pick one that ends in seemingly random numbers, and copy and paste everything after the ":" into a text file. We will be using it in a moment. Now, let's create our halevt config file:
```
touch ~/.halevt.xml && gedit ~/.halevt.xml
```
Paste the following into the file:
```

<?xml version="1.0" encoding="UTF-8"?>
<halevt:Configuration version="0.1" xmlns:halevt="http://www.environnement.ens.fr/perso/dumas/halevt.html">
	<halevt:Device match="hal.info.udi = /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023">
		<halevt:Insertion exec="toggleTouchpad off"/>
		<halevt:Removal exec="toggleTouchpad on"/>
	</halevt:Device>
</halevt:Configuration>

```
We are almost done! Remember the bit I had you paste into another file?? We are going to use that to identify your device. In the config file, change the line that says:
```

<halevt:Device match="hal.info.udi = /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023">

```
to say :
```

<halevt:Device match="hal.info.udi = /org/freedesktop/Hal/devices/the_rest_of_what_you_copied_into_the_file">

```
Theoretically, we're done!

[SIZE="4"]**Test the Magic:**[/SIZE]
From terminal run:
```

sudo killall halevt
halevt -c ~/.halevt.xml

```
Now, connect your mouse. If all is going well, about ~1.5 seconds after you plug in your mouse your touchpad should stop working. Now, disconnect your mouse. Your touchpad should start working again.

[SIZE="4"]**Making it permanent:**[/SIZE]
If all went well in the tests, you will want to make this happen automatically forever. Go to "System->Preferences->Startup Applications", and add a new startup program. Name it something you will remember, and for the command put "halevt -c ~/.halevt.xml". You're done!!

[SIZE="4"]**Didn't work? Undo it!:**[/SIZE]
Undoing this configuration is fairly straightforward. Start out by going to "System->Preferences->Startup Applications" and removing the entry we added in the step above. Now let's remove halevt and the files we created:
```

sudo apt-get remove halevt
rm ~/.halevt.xml ~/bin/toggleTouchpad

```

Optionally you can also remove the ~/bin folder (it's still a good idea to have in my opinion) and the configuration for it:
```

rmdir ~/bin
gedit ~/.bashrc 

```
and remove the lines 
```

PATH=\$PATH:~/bin
export PATH

```
from the end. You should be set back to your normal state!

[SIZE="4"]**Special Thanks:**[/SIZE]
While writing this script I [received a great deal of help from]("http://ubuntuforums.org/showthread.php?t=1628329") the user [Arndt]("http://ubuntuforums.org/member.php?u=106064"), so you should go leave him lots of love and thanks.

---

### Post by brishu on 2010-11-26
Wow, thank you so much, this worked perfectly, even better it gave me a way to turn off my touchpad easily :). 

One tiny little thing in your tutorial though: In the **Undo the Changes** section: the *rm ~/bin* line.
rm doesn't remove directories and rm -r could be problematic
[I]rm ~/bin/toggleTouchpad
rmdir ~/bin[/I]
removes the toggleTouchpad, and only removes ~/bin if its empty.

Also, is there a way to turn the touchpad on/off (automatically) when you turn the on/off the mouse's power.

---

### Post by brennydoogles on 2010-11-26
> **brishu said:**
> Wow, thank you so much, this worked perfectly, even better it gave me a way to turn off my touchpad easily :). 

One tiny little thing in your tutorial though: In the **Undo the Changes** section: the *rm ~/bin* line.
rm doesn't remove directories and rm -r could be problematic
[I]rm ~/bin/toggleTouchpad
rmdir ~/bin[/I]
removes the toggleTouchpad, and only removes ~/bin if its empty.

I'm glad to help! You are absolutely right about the rmdir, I was not thinking when I wrote that section, and it has been edited to be correct now.

> **brishu said:**
> 
Also, is there a way to turn the touchpad on/off (automatically) when you turn the on/off the mouse's power.

It would depend on the mouse and what kinds of events occur when you turn on/off your device. Running
```
halevt -i
```
after your mouse is connected and then turning it on and off should print to the screen any events triggered. For my mouse (Logitech MX1000) I seem not to get anything. If you do get something, post the output and I will try my best to help you rewrite your rule for that even instead of the "connected" event.

---

### Post by brishu on 2010-11-26
No output (Logitech M305) :(, but thanks anyway :) (Plus, now I can turn the touchpad on/off with a shortcut so its not that big of a deal. :) thanks)

---

### Post by deafiant on 2010-11-28
Wonderful! Works with my AlpsPS/2 ALPS GlidePoint touchpad. (Changed touchpadString="GlidePoint")

This is a great example of what I like about linux:
[LIST=1]
[*]That it is possible for you can control your computer as well as this.
[*]Someone in the community will figure out how it is done and then shares what they learnt with others.
[*]It is not just a program to download - I learn more about computing each time.
[/LIST]

Thanks very much! :)

---

### Post by brennydoogles on 2010-11-28
> **deafiant said:**
> Wonderful! Works with my AlpsPS/2 ALPS GlidePoint touchpad. (Changed touchpadString="GlidePoint")

This is a great example of what I like about linux:
[LIST=1]
[*]That it is possible for you can control your computer as well as this.
[*]Someone in the community will figure out how it is done and then shares what they learnt with others.
[*]It is not just a program to download - I learn more about computing each time.
[/LIST]

Thanks very much! :)

Glad it works! I agree about why you like Linux so much, the community and ability to share my work (as well as reaping the benefits of everyone else's work) is one of the main things that keeps renewing my interest.

---

### Post by Shadowgamon on 2010-11-28
killer script dude! it works a heck of a lot easier than the SMHcofing hullabaloo. 

I just cant get it to shut off when my mouse is plugged in. Since deafient seems to have an identical touch pad to me that' doesn't seem to be the problem. 

I think it might be at 

halevt -i >>~/connectedDevices.txt

cause I get 
```
New Device: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial
New Device: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial_if0
New Device: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial_if0_logicaldev_input
Device removed: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial_if0_logicaldev_input
Device removed: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial_if0
Device removed: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial
Got signal 2

```As you can see none of them have "seemingly random numbers" Which should I use?

---

### Post by deafiant on 2010-11-28
> **Shadowgamon said:**
> I just cant get it to shut off when my mouse is plugged in. Since deafient seems to have an identical touch pad to me that' doesn't seem to be the problem.
> **Shadowgamon said:**
> As you can see none of them have "seemingly random numbers" Which should I use?

"usb_device_[random number]_noserial_if0" worked for me. Here's my .halevt.xml:
```

<?xml version="1.0" encoding="UTF-8"?>
<halevt:Configuration version="0.1" xmlns:halevt="http://www.environnement.ens.fr/perso/dumas/halevt.html">
	<halevt:Device match="hal.info.udi = /org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0">
		<halevt:Insertion exec="toggleTouchpad off"/>
		<halevt:Removal exec="toggleTouchpad on"/>
	</halevt:Device>
</halevt:Configuration>

```

I'm guessing ```
<halevt:Device match="hal.info.udi = /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial_if0">
``` should work for you.

It is being turned off and on using only the script?

---

### Post by deafiant on 2010-11-29
Scratch that. A reboot and I have lost the triggering of the script when the mouse is inserted. Trying halevt -i again and I am getting a different number! I'll try a few things and get back to you.

---

### Post by brennydoogles on 2010-11-29
> **deafiant said:**
> Scratch that. A reboot and I have lost the triggering of the script when the mouse is inserted. Trying halevt -i again and I am getting a different number! I'll try a few things and get back to you.

Interesting. What kind of mouse is it? It shouldn't be changing addresses as far as I'm aware. I am attempting to work out a way to identify all pointing devices so that the configuration will be much easier, and that should solve the problem if all else fails.

---

### Post by cobra11 on 2010-12-04
After restart or suspend or hibernate script dont work, it only works again if i put in terminal halevt -c ~/.halevt.xml. I have ubuntu 10.10 i put in Startup programs this command but like i said doesnt work,any ideas how to fix it?

---

### Post by Navalio on 2010-12-04
> **Shadowgamon said:**
> killer script dude! it works a heck of a lot easier than the SMHcofing hullabaloo. 

I just cant get it to shut off when my mouse is plugged in. Since deafient seems to have an identical touch pad to me that' doesn't seem to be the problem. 

I think it might be at 

halevt -i >>~/connectedDevices.txt

cause I get 
```
New Device: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial
New Device: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial_if0
New Device: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial_if0_logicaldev_input
Device removed: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial_if0_logicaldev_input
Device removed: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial_if0
Device removed: /org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial
Got signal 2

```As you can see none of them have "seemingly random numbers" Which should I use?
I had exactly the same absence of the serial numbers, but i pasted almost all string without _if0, so "/org/freedesktop/Hal/devices/usb_device_15d9_a4d_noserial".

And just wanted to add, that before making "toggling" testing the login/logout should be done (at least in mine maverick box :)).

To the author: After reboot, if the external mouse inserted, the script not working, then i should done re-inserting of the pointer, as i understood, the script is only catching events of the insertion, but not the initial state. But anyway thanks, because for me on rather old laptop with buggy touchpad it made life easier.

---

### Post by cobra11 on 2010-12-05
I get it work from boot with: /bin/sh -c 'DISPLAY=:0 halevt -c ~/.halevt.xml' in Startup programs.
I create script which works when mouse is pluged in:

sudo gedit /etc/init.d/touchpad
> #! /bin/sh
DEVICE_ID=`xinput -list | grep -i mouse | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `
if xinput -list | grep -i mouse | grep id=$DEVICE_ID  > /dev/null
then
   echo "je notr"
/bin/sh -c `DISPLAY=:0 gconftool-2 --set "/desktop/gnome/peripherals/touchpad/touchpad_enabled" --type boolean "false"`
else
  echo "ni notr"
/bin/sh -c `DISPLAY=:0 gconftool-2 --set "/desktop/gnome/peripherals/touchpad/touchpad_enabled" --type boolean "true"`
fi
sudo chmod +x  /etc/init.d/touchpad

And than i add in startup programs /etc/init.d/touchpad that gets work from reboot now from suspend,hibernate i add:
sudo gedit /etc/pm/sleep.d/99-touchpad.sh
> #!/bin/bash
case "$1" in
    thaw|resume)
        /etc/init.d/touchpad 2>/dev/null
        ;;
    *)
        ;;
esac
exit $?
sudo chmod +x /etc/pm/sleep.d/99-touchpad.sh

Now everything seems to work but i have to add in toggleTouchpad after # The argument was 'on', so turn the touchpad on 
/bin/sh -c `DISPLAY=:0 gconftool-2 --set "/desktop/gnome/peripherals/touchpad/touchpad_enabled" --type boolean "true"`
and after # The argument was 'off', so turn the touchpad off 
/bin/sh -c `DISPLAY=:0 gconftool-2 --set "/desktop/gnome/peripherals/touchpad/touchpad_enabled" --type boolean "false"`

If anybody know better solution pleasse post it, because this script turn off in gconf-editor not in xinput soo xinput than doesnt work.

---

### Post by monoxide.tryst on 2011-01-02
I get :  
 toggleTouchpad: command not found

I have copy and pasted everything in the guide twice now

Any ideas???

---

### Post by brennydoogles on 2011-01-03
> **monoxide.tryst said:**
> I get :  
 toggleTouchpad: command not found

I have copy and pasted everything in the guide twice now

Any ideas???

It sounds like either toggleTouchpad is not in your path, or possibly named slightly differently. In terminal try
```
echo $PATH
```
and make sure that the directory you have placed toggleTouchpad in shows up. If you're not sure, post the results here and we'll take a look for you.

---

### Post by WarrenSH on 2011-01-05
Working fine on my Compaq Presario  V5101US & running Ubuntu 10.10 32bit

---

### Post by dpschramm on 2011-01-05
I had some problems with the script in Karmic (9.10). 

It appears that I might be running an older version of xinput (1.4.2) that does not support --set-prop, so instead I have to use the (now deprecated) --set-int-prop command.

I have also modified line 24 to change the way AWK is used - the previous version always assumed that there would be a fixed number of spaces in the device name.

```
# toggleTouchpad by Brendon Dugan
# Toggles a touchpad on or off depending on it's current state or CLI argument
#
# To configure, run the command 'xinput list' in terminal and identify your touch pad.
# Using the output of the above command, change the touchpadString variable to a substring
# of your touchpad's description that is unique to that device.
#
# To run, simply type 'toggleTouchpad' to toggle your touchpad on or off, or
# 'toggleTouchpad on' to explicitly turn your touchpad on, or
# 'toggleTouchpad off' to explicitly turn it off.
#
# Enjoy!


# A function for logging
safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod +rw $1; 
fi
}
logdir=/home/$USER/.toggleTouchpad
touchpadString="TouchPad"
touchpadID=$(xinput list | grep $touchpadString | awk -F '"' '{print $3}' | awk -F " " '{print $1}' | awk -F "=" '{print $2}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')
sleeptime=1

# Create the logging directory
safemk $logdir
touch $logdir/errorLog.txt

# Check for arguments on the command line
if test $# -eq 1
then
	# Change the argument to lowercase
	arg1=$(echo $1 | tr [:upper:] [:lower:])
	cliArg=1
else
	# There is no argument.
	cliArg=0
fi

if [ $cliArg -eq 1 ]
then
	# If there's an argument, check to see whether it is on, off, or junk
	if [ $arg1 = 'on' ]
	then
		# The argument was 'on', so turn the touchpad on
		xinput --set-int-prop $touchpadID "Device Enabled" 8 1
		if [ $(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}') -eq 0 ]
		then
			echo "Something went wrong\n" >> $logdir/errorLog.txt
		fi
	elif [ $arg1 = 'off' ]
	then
		# Sleep for a short time to fix a bug that re-enabled the touchpad immediately after disabling it
		sleep $sleeptime
		# The argument was 'off', so turn the touchpad off 
		xinput --set-int-prop $touchpadID "Device Enabled" 8 0
		if [ $(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}') -eq 1 ]
		then
			echo "Something went wrong, perhaps \$sleeptime needs to be greater than $sleeptime ?\n" >> $logdir/errorLog.txt
		fi
	else
		# The argument was junk, so log the error and go on 
		echo "Invalid argument \""$arg1"\" was supplied\n" >> $logdir/errorLog.txt
	fi
else
	# There was no argument, so just toggle the touchpad to the opposite
	# of the state it has now.
	if [ $touchpadEnabled -eq 1 ]
	then
		xinput --set-int-prop $touchpadID "Device Enabled" 8 0
	else
		xinput --set-int-prop $touchpadID "Device Enabled" 8 1
	fi
fi
```

I would be glad to hear your thoughts.

Cheers.

---

### Post by JWFoxJr on 2011-02-07
I had to do the same thing with the awk statement on line 24. Mine wound up being:

```

touchpadID=$(xinput list | grep $touchpadString | awk -F " " '{print $7}' | awk -F "=" '{print $2}')

```

Thanks for a great script!

Joe

---

### Post by faifas on 2011-03-29
Ubuntu 10.10
[PHP]
sudo nano /etc/init.d/touchpad
[/PHP]

I ended up with this script:
[PHP]
touchpadID=$(xinput list | grep TouchPad | awk -F "=" '{print $2}' | awk -F " " '{print $1}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')
mouseId=$(xinput list | grep Mouse | awk -F "=" '{print $2}' | awk -F " " '{print $1}')
mouseEnabled=$(xinput list-props $mouseId | grep "Device Enabled" | awk -F ":" '{print $2}')

if [ $mouseEnabled -eq 1 ]
then
        xinput --set-int-prop $touchpadID "Device Enabled" 8 0
else
        xinput --set-int-prop $touchpadID "Device Enabled" 8 1
fi
[/PHP]

[PHP]
sudo chmod +x /etc/init.d/touchpad
update-rc.d touchpad defaults
[/PHP]

Enjoy!

---

### Post by cantru on 2011-04-07
Hi Faifas

I tried your script and I got the following response.
[I]
cantru@mobile-UL50VT:~$ sudo chmod +x /etc/init.d/touchpad
cantru@mobile-UL50VT:~$ update-rc.d touchpad defaults
update-rc.d: warning: /etc/init.d/touchpad missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/touchpad already exist.
Died at /usr/sbin/update-rc.d line 57.
[/I]
Any advice

Thanks.

---

### Post by faifas on 2011-04-08
Hi,

my script wasn't following rules described at [debian wiki]("http://wiki.debian.org/LSBInitScripts")

here's a quick fix
[PHP]
#!/bin/bash
### BEGIN INIT INFO
# Provides:          touchpad
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFO

touchpadID=$(xinput list | grep TouchPad | awk -F "=" '{print $2}' | awk -F " " '{print $1}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')
mouseId=$(xinput list | grep Mouse | awk -F "=" '{print $2}' | awk -F " " '{print $1}') 
mouseEnabled=$(xinput list-props $mouseId | grep "Device Enabled" | awk -F ":" '{print $2}')

if [ $mouseEnabled -eq 1 ]
then
        xinput --set-int-prop $touchpadID "Device Enabled" 8 0
else
        xinput --set-int-prop $touchpadID "Device Enabled" 8 1
fi
[/PHP]

Error message saying ```
System start/stop links for /etc/init.d/touchpad already exist.
``` means you already have touchpad script added to run-time. If it is the same script you can

```

sudo update-rc.d -f touchpad remove
sudo update-rc.d touchpad defaults

```

Hope this helps!

---

### Post by Votti on 2011-07-05
Hey [brennydoogles]("http://ubuntuforums.org/member.php?u=258498"), thanks for your script! After the "touchpad-indicator" did not work on my laptop this was a neat solution for my problems!

However, in order to get the script (the version of the first post) running properly i had to do some minor adjustment:

This part of your code:

```
touchpadString="TouchPad"
touchpadID=$(xinput list | grep $touchpadString | awk -F " " '{print $6}' | awk -F "=" '{print $2}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')
sleeptime=1
```I had to change to:

```
[COLOR=#000000][COLOR=#FF8000]
[COLOR=Black]touchpadString="[COLOR=Red]PS/2 Mouse[/COLOR]"
touchpadID=$(xinput list | grep [COLOR=Red]"PS/2 Mouse"[/COLOR] | awk -F " " '{print [COLOR=Red]$[/COLOR][/COLOR][SIZE=4][COLOR=Red]5[/COLOR][/SIZE][COLOR=Black]}' | awk -F "=" '{print $2}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')
sleeptime=1[/COLOR]
[/COLOR][/COLOR]
```Due to the fact that 
a) my mouse name was [COLOR=#000000][COLOR=#FF8000]"PS/2 Mouse"
[/COLOR][/COLOR]b) depending on the name of your mouse, the number after print has to be changed. Best try the command:
```
xinput list | grep "PS/2 Mouse" | awk -F " " '{print $5}'
```
with always different numbers, until it gives you something like "id=12"

---

### Post by Imnotroot on 2011-09-29
Thanks a lot, however the auto start did not work for my for some strange reason so i created a keyboard shortcut to turn on/off the touchpad. 

Thanks a lot for your work!

---

### Post by veko on 2011-10-11
Here's a sript I've used. It's essentially the same as above, but it should figure out the mouse id automatically and it toggles touchpad off only is usb/bluetooth/wireless mouse is connected.

Now if I only got this to run automatically when mouse is (dis)connected...

I had it in startup applications, and Karmic it worked fine. But in Lucid some other application enables touchpad right away again.


```

#!/bin/sh

DEVICE_ID=`xinput -list | grep -i touchpad | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then 
    if xinput -list | grep -i mouse | egrep -i 'usb|bluetooth|wireless' > /dev/null
    then
        xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
    fi
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi

```

---

### Post by cobra11 on 2011-10-22
Is there anyway that i could hide or move this script? Because it is in home folder and goes on my nervous, when i open home map?

---

### Post by Imnotroot on 2011-10-29
Thanks! works fine for me

---

### Post by gnomicon on 2012-02-06
The proposed "touchpadToggle" script was not working for my MacBook, so I did rewrite it.

If it doesn't works, you may have to add the proper value for RECEIVER_ID or TRACKPAD_ID. You can find them running xinput -list (please post them here)


```
# !/bin/sh
sleep 1

# uncomment the following line and the last line to enable logging
#(

RECEIVER_ID='mouse|ps.2|usb|bluetooth|wireless|receiver'
TRACKPAD_ID='appletouch|glidepoint|trackpad'

TRACKPAD_DEVICE_ID=`xinput -list | egrep -i $TRACKPAD_ID | grep id= | sed -e 's/.*id=\([0-9]*\).*/\1/' -e T -e q`

if [ -z "$TRACKPAD_DEVICE_ID" ]
then
        echo "Device not found !"
        xinput -list | egrep -r "slave +pointer"
        echo "Edit $0 and add the required string to TRACKPAD_ID='$TRACKPAD_ID'"
        exit 1
fi

TRACKPAD_DEVICE_NAME=$(xinput -list-props $TRACKPAD_DEVICE_ID | grep Device.\' | cut -d "'" -f 2)
echo Device detected: $TRACKPAD_DEVICE_NAME

DEVICE_ENABLED=$(xinput -list-props $TRACKPAD_DEVICE_ID | grep "Device Enabled" | grep "1$")

trackpad_enable() {
        if [ -z "$DEVICE_ENABLED" ]
        then
                echo "enabling device"
                xinput set-int-prop $TRACKPAD_DEVICE_ID "Device Enabled" 8 1
        else
                echo "already enabled"
        fi
}

trackpad_disable() {
        if [ -z "$DEVICE_ENABLED" ]
        then
                echo "already disabled"
        else
                echo "disabling device"
                xinput set-int-prop $TRACKPAD_DEVICE_ID "Device Enabled" 8 0
        fi
}

trackpad_auto() {
        RECEIVER_DETECTED=$(xinput -list | egrep -r "slave +pointer" | egrep -i $RECEIVER_ID)

        if [ -z "$RECEIVER_DETECTED" ]
        then trackpad_enable
        else trackpad_disable
        fi
}

usage() {
        echo "usage: `basename $0` [ on | off ]"
        exit 1
}

case "$1" in
        on) trackpad_enable ;;
        off) trackpad_disable ;;
        *) if [ -z "$1" ]
           then trackpad_auto
           else usage
           fi ;;
esac

#) >> /tmp/touchpadToggle.log

```

---

### Post by emagar on 2012-06-29
Neat code! Mega thanx 2 brennydoogles, works fine in Dell XPS 13 corei5 running 64bit Precise (12.04) Ubuntu.

---

### Post by Mr.Samurai on 2013-01-25
Hi.

The script is not working for me. xinput command shows that I have two touchpads, here's the output from terminal window:

```
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Gaming Mouse G400              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; X10 WTI RF receiver mouse               	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Bison Webcam                            	id=9	[slave  keyboard (3)]
    &#8627; X10 WTI RF receiver                     	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
```

Can somebody please explain or point how can I delete one of two touchpads? Or maybe put some changes to the script so it can work with my configuration.

---

### Post by Mr.Samurai on 2013-02-07
bump

---

### Post by CharlesA on 2013-02-07
It would be a good idea to create a new thread about your problem. This thread is from 2010 and the last reply was last year.

---

### Post by stonis on 2013-02-18
It worked with the few exception:
1) I need to disable halevt from starting by default
2) start it as user
3) check is mouse connected at the login to dissable touchpad
I wrote what worked for me in [http://www.stonis.info/wiki/index.php/Linux_configuration_tips#Configure_touchpad](http://www.stonis.info/wiki/index.php/Linux_configuration_tips#Configure_touchpad)

---

