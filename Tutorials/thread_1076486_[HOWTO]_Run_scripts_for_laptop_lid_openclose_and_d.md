---
title: "[HOWTO] Run scripts for laptop lid open/close and dock/undock events"
date: 2009-02-21
forum: Tutorials
---

### Post by lunatico on 2009-02-21
What this little tutorial shows is:
1. How to catch the lid open and close events.
2. How to catch the laptop dock and undock events.
3. How to run a script for each of those events.

I will show a specific example which consist in:
- When the lid closes -> play a "closing" sound and set my Pidgin status to away with a message saying "My laptop lid is closed..."
- When the lid is opened -> play an "opening" sound and set my Pidgin status to available with a message saying "I am here..."
- When I undock my laptop from the docking station -> play a "undock" sound
- When I dock my laptop into the docking station ->  play a "docked" sound

**NOTES:**
- This was tested on a Lenovo Thinkpad T61 and a T61p both running Ubuntu 8.10. Things might slightly change depending on the laptop or linux distribution. But the main idea will be the same. This tutorial is just to point people towards the right solution.
- 20/07/09: I just tested this on a T61p with Ubuntu 9.04 and it work fine, there is one minor thing to look, stated below.
- Make sure throughout the tutorial you change your_user with your actual user on the scripts and also feel free to save scripts on different paths updating the paths on the scripts of course.
- 27/02/10: If you want to implement the lid solution on a laptop with multiple users then look at posts 32, [33]("http://ubuntuforums.org/showpost.php?p=8889393&postcount=33") and [40]("http://ubuntuforums.org/showpost.php?p=8897657&postcount=40") from airtonix. I haven't tested these myself.
- 14/04/10: Tested this on a Thikpad W500 with Ubuntu 9.10. The script part works fine, the dock part needs a slight change, see [post 48]("http://ubuntuforums.org/showpost.php?p=9121642&postcount=48") for details.
- 15/07/10: 14/04/10: Tested this on a Thikpad W500 with Ubuntu 10.04. The above change is also necessary.

***I am not responsible if you mess things up, please be careful!***

It is important to understand that these events will be catched by processes owned by root. So we need to do a little hack so that root can run commands on our user's X environment. Many thanks to Earl Ruby for pointing me on how to do this [http://earlruby.org/2008/08/update-pidgin-status-using-cron/](http://earlruby.org/2008/08/update-pidgin-status-using-cron/)

In order to make the environment variables available for root:

```
gedit ~/export_x_info
```

and paste the following in:

```
#!/bin/bash
# Export the dbus session address on startup so it can be used by any other environment
sleep 5
touch $HOME/.Xdbus
chmod 600 $HOME/.Xdbus
env | grep DBUS_SESSION_BUS_ADDRESS > $HOME/.Xdbus
echo 'export DBUS_SESSION_BUS_ADDRESS' >> $HOME/.Xdbus
# Export XAUTHORITY value on startup so it can be used by cron
env | grep XAUTHORITY >> $HOME/.Xdbus
echo 'export XAUTHORITY' >> $HOME/.Xdbus
```

Save and close. Then make it executable:

```
chmod 700 ~/export_x_info
```

Now put it on your startup scripts. System -> Preferences -> Sessions and click Add.

```
Name: X Environment Variables
Command: /home/your_user/export_x_info
```

Click Add and close.

This will execute every time you start your computer and the call to source ~/.Xdbus loads the DBUS_SESSION_BUS_ADDRESS and XAUTHORITY environment variables before executing the purple-remote command for Pidgin.

Ubuntu makes it easy to catch the laptop lid open and close events. There is a file /etc/acpi/lid.sh which runs every time your lid open or closes. So run:

```
gksudo gedit /etc/acpi/lid.sh
```

and right after line #!/bin/bash paste /home/your_user/lid_event

Save and close.

Now create the file that will call different scripts according to open or close events.

```
gedit ~/lid_event
```

and paste the following into the file:

```
#!/bin/bash
grep -q closed /proc/acpi/button/lid/LID/state
if [ $? = 0 ]
then
        /home/your_user/close;
else
        /home/your_user/open;
fi
```

Save and close and make it executable.

```
chmod +x ~/lid_event
```

And finally lets create the files open and close.

```
gedit ~/open
```

and paste the following into the file:

```
#!/bin/bash
#This runs so that root can run the following command under the user's environment
source /home/your_user/.Xdbus
#play a open sound
DISPLAY=:0.0 su your_user -c "aplay /usr/lib/openoffice/basis3.0/share/gallery/sounds/sparcle.wav"
#change Pidgin status
DISPLAY=:0.0 su your_user -c "purple-remote 'setstatus?status=available&message=I am here...'"
```

Save and close. Make it executable:

```
chmod +x ~/open
```

Now the close file:

```
gedit ~/close
```

and paste the following into the file:

```
#!/bin/bash
#This runs so that root can run the following command under the user's environment
source /home/your_user/.Xdbus
#play a close sound
DISPLAY=:0.0 su your_user -c "aplay /usr/lib/openoffice/basis3.0/share/gallery/sounds/falling.wav"
#change Pidgin status
DISPLAY=:0.0 su your_user -c "purple-remote 'setstatus?status=away&message=My laptop lid is closed...'"
```

Save and close. Make it executable:

```
chmod +x ~/close
```

Now you need to restart ACPI. Run:

```
sudo /etc/init.d/acpid restart
```

Now you can test that it works by opening and closing your laptop lid.
Notes:
- Make sure that the gnome power management option for laptop lid closed is set to do nothing.
- The sounds used are from OpenOffice 3.0, the path changes for previous versions.
- Make sure you have libpurple-bin installed -- sudo apt-get install libpurple-bin

Now lets catch the docking event. Thanks to Steven King on pointing me how to go about this [http://www.nabble.com/How-does-a-uevent-work-for-dock-undock-on-thinkpads--tt21898641.html#a21898641](http://www.nabble.com/How-does-a-uevent-work-for-dock-undock-on-thinkpads--tt21898641.html#a21898641)
This is done by using a udev event.

**Note:** For Ubuntu 9.10 and 10.04 you need to do this slightly different as explained in [post 20]("http://ubuntuforums.org/showpost.php?p=7874459&postcount=20").

```
gksudo gedit /etc/udev/rules.d/80-thinkpad-T61.rules
```

and paste the following:

```
KERNEL=="dock.0", ATTR{docked}=="1", RUN+="/etc/thinkpad/dock.sh 1"
KERNEL=="dock.0", ATTR{docked}=="0", RUN+="/etc/thinkpad/dock.sh 0"
```

Save and close.

```
sudo mkdir /etc/thinkpad

gksudo gedit /etc/thinkpad/dock.sh
```

and paste the following:

```
#!/bin/sh
# wait for the dock state to change
sleep 1
DOCKED=$(cat /sys/devices/platform/dock.0/docked)
case "$DOCKED" in
	"0")
	#undocked event
	/home/your_user/undocked
	;;
	"1")
	#docked event
	/home/your_user/docked
	;;
esac
exit 0
```

Save and close. Make it executable:

```
sudo chmod -x /etc/thinkpad/dock.sh
```

NOTE: For some reason on Ubuntu 9.04 the above command will not work, the file will not be made executable. The workaround is to become root and execute the chmod command.

Now lets create the undocked file:

```
gedit ~/undocked
```

and paste the following:

```
#!/bin/bash
#This runs so that root can run the following command under the user's environment
source /home/your_user/.Xdbus
#play a sound
DISPLAY=:0.0 su your_user -c "aplay /usr/lib/openoffice/basis3.0/share/gallery/sounds/falling.wav"
```

Save and close. Make it executable:

```
chmod +x ~/undocked
```

then the docked file:

```
gedit ~/docked
```

and paste the following:

```
#!/bin/bash
#This runs so that root can run the following command under the user's environment
source /home/your_user/.Xdbus
#play a sound
DISPLAY=:0.0 su your_user -c "aplay /usr/lib/openoffice/basis3.0/share/gallery/sounds/sparcle.wav"
```

Save and close. Make it executable:

```
chmod +x ~/docked
```

Now finally we need to restart hal:

```
sudo /etc/init.d/hal restart
```

That's it, you should be able to dock and undock and hear a sound each time you do. From here the options for you are endless, you can basically do anything you want.

:D

---

### Post by e64462 on 2009-03-04
Hey, thanks for the guide, honestly i think this is what i was looking for, it just didnt work for me.

A brief outline of my problem...

i have a thinkpad x61 tablet who's screen i would like to rotate when i rotate my lid. I have a button on my laptop screen that executes a program I wrote to rotate the screen. If i rotate the screen using this method, all is fine... its just inconvenient... I'd  like acpi to do it for me....

I used acpi_listen to find the rotate event, created a file in /etc/acpi/events/ called "ibm-clockwise.sh". Then I made this file executable and had it call a script in /etc/acpi called "ibm-clockwise". This file is also executable. If i just put "rotate" (the name of my program) in "ibm-clockwise", compiz crashes on rotation. 

So I did some testing and found that when I execute rotate as root, the same behavior is observed, i assume this is the problem, since the scripts in /etc/acpi are executed as root.

I screwed around with "su nick -c rotate" for a while, both while logged in as root, using "sudo su", and placing this command in the /etc/acpi/ibm-clockwise file. That was fun, all time wasting aside.

Everytime compiz crashes, I lose half of my workspaces... All of my special keys are unbound, and obviously desktop effects are gone... I have to go to the fusion-icon and do "reload window manager" ...

it seems this problem could be fixed by having acpi execute rotate as my user (nick). This brings me to your guide.

I followed parts of it, but i didnt really want my home directory cluttered with a bunch of scripts. 

I created ~/export_x_info and pasted your info in directly. Then i made it executable. I also added it to my startup using your method, but I didnt feel like restarting for it to take effect, so i executed it with a ./export_x_info ... 

I skipped all the linking and just went directly to pasting the source ~/.Xdbus stuff into the action script since i only need it to do one thing... my /etc/acpi/ibm-clockwise file looks like 

#!/bin/bash
source /home/nick/.Xdbus
DISPLAY=:0.0 su nick -c "rotate"

Though im not even sure if the "DISPLAY=:0.0" is necessary, i tried removing it and things still didnt work.

i restarted acpi and tested, and compiz still crashes, i assume because the file is still not being executed as my user (nick).

Any help would be so great, i appreciate it...

---

### Post by lunatico on 2009-03-04
> **e64462 said:**
> Any help would be so great, i appreciate it...

Right... let's see what we can do.

First, for troubleshooting purposes I recommend running stuff yourself as root. This way you will determine when, where and why it is not working. The idea is something like:

"su -" and:

```
env | grep DBUS_SESSION_BUS_ADDRESS
env | grep  XAUTHORITY
```

Probably this didn't returned anything. That's fine. If you run your "rotate" script now it will most likely crash as you described. Try and see. You probably will see where it is failing.

Now:

```
source /home/daniel/.Xdbus
```

And again:

```
env | grep DBUS_SESSION_BUS_ADDRESS
env | grep  XAUTHORITY
```

This time you should get your session's values. So now you should be able to start running stuff from root as your user on your current session.
What I suspect is happening is that there is a lot of stuff inside your rotate script that is still just been run as root. See, what happens is that when you do "source /home/nick/.Xdbus" the env variables are been imported just to that environment, if you run a script from there you are creating a new bash environment just for that script.
You should call "source /home/nick/.Xdbus" again within your rotate script and stuff that you do there that uses your session's env variables should be run as DISPLAY=:0.0 su nick -c "etc....."
Do you see my point?

I hope this helps.... let me know how you get on.

---

### Post by e64462 on 2009-03-04
hey, thanks for the reply!

so im not sure i fully understand what's happening... do you want me to run 

env | grep DBUS_SESSION_BUS_ADDRESS
env | grep  XAUTHORITY

as root? like.. type "sudo su" and then enter those?

When I do that, i get

nick@notebook:~$ sudo su
root@notebook:/home/nick# cd
root@notebook:~# env | grep DBUS_SESSION_BUS_ADDRESS
root@notebook:~# env | grep  XAUTHORITY
XAUTHORITY=/home/nick/.Xauthority

Then i source /home/nick/.Xdbus and rerun those env commands

root@notebook:~# source /home/nick/.Xdbus
root@notebook:~# env | grep DBUS_SESSION_BUS_ADDRESS
root@notebook:~# env | grep  XAUTHORITY
XAUTHORITY=/home/nick/.Xauthority

the output is the same both times, the first returns nothing, the second returns ~/.Xauthority

I tried rotating the screen before and after both of those blocks... compiz crashed all 4 times... the output of my rotate program was pretty much the same in each case... the only instruction that really returns anything is the

system("compiz --replace"); 

which returns

nick@notebook:~$ sudo rotate
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

I dont see too much of interest there... 

In regards to your final comment about adding 

source /home/nick/.Xdbus 

to my rotate program and then executing anything that uses the env variables using su nick -c <do-stuff> ... I don't know which statements pertain to the env variables... how do i identify them (im lost needless to say)

---

### Post by e64462 on 2009-03-04
hmm... perhaps you should mostly ignore my last post. I did some searching in hopes of gaining a better understanding of what your scripts were doing.

Playing with the sample export_x_info file you provided, i realized that it wasn't placing the output of 

```
 env | grep DBUS_SESSION_BUS_ADDRESS 
```

in /home/nick/.Xdbus

is the line in your sample file supposed to read:

```
 env | grep DBUS_SESSION_BUS_ADDRESS **>>** $HOME/.Xdbus 
```

i made that correction, then did

```

nick@notebook:~$ rm -f .Xdbus 
nick@notebook:~$ ./export_x_info 
nick@notebook:~$ cat .Xdbus 

DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-YX3A7vUW9N,guid=b59d1b4c84bf031c1e65c1a549aecaa7
export DBUS_SESSION_BUS_ADDRESS
XAUTHORITY=/home/nick/.Xauthority
export XAUTHORITY


```

then logged in as root using "sudo su"

```

root@notebook:~# env | grep DBUS_SESSION_BUS_ADDRESS
root@notebook:~# env | grep  XAUTHORITY
XAUTHORITY=/home/nick/.Xauthority

```

DBUS_SESSION_BUS_ADDRESS is still empty anyways... so i:

```

root@notebook:~# source /home/nick/.Xdbus 
root@notebook:~# env | grep DBUS_SESSION_BUS_ADDRESS
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-YX3A7vUW9N,guid=b59d1b4c84bf031c1e65c1a549aecaa7
root@notebook:~# env | grep  XAUTHORITY
XAUTHORITY=/home/nick/.Xauthority

```

which i think is what you expected... 

at this point i think I've narrowed down the segment of code in my program that is causing all the problems. when i comment out this line, the screen rotates just fine, but the keys that i need reassigned after rotation aren't recognized (which is why it's there). But this is the troublesome line.
		
system(compiz --replace);

So i need to somehow give root the ability to restart compiz... playing with this idea, i started issuing compiz --replace every odd way i could think of (after assigning the environment variables) which didnt work =(

any ideas?

---

### Post by lunatico on 2009-03-05
> **e64462 said:**
> then logged in as root using "sudo su"

Well, first thing is just to say that "sudo su" it's not the same as "su -". They both make you root alright but with the first you are still on your user's home directory, whereas the second makes you root and places you on root's home directory. That's why you are getting something for your xauthority value but not for your bdus session value.
When running scripts as root it is on root's home directory. So if you just call your "rotate" script root is not even able to find it. Probably the first problem you have in the line. You should use the full path of your script.

> **e64462 said:**
> But this is the troublesome line.
		
system(compiz --replace);
any ideas?

It sure is a troublesome line. I just tried
```
DISPLAY=:0.0 su user -c "compiz --replace"
```
And it crashed....
Compiz is a very complicated piece... you may want to ask on their forums to see what you need to do to restart it as root but for your users session. Sorry I can't be of more help.

---

### Post by e64462 on 2009-03-05
its all good... stupid compiz... thanks for the help though! atleast i learned something!

---

### Post by lunatico on 2009-03-05
> **e64462 said:**
> stupid compiz...

I agree! But we can't live without it can we? It's so beautiful...
Anyway, I hope you sort this out, post back if you do.
Cheers!

---

### Post by binbash on 2009-03-05
Good howto, i will try this in an hour ;)

---

### Post by DougEdey on 2009-04-21
Firstly, let me say a big thankyou for this! It makes my life far easier at work when moving between my desk and our test floor.

I was wondering if there's some way to link this into emesene (or amsn) to change my status? emesene has a dbus plugin so i thought it should be ok!

---

### Post by lunatico on 2009-04-21
> **DougEdey said:**
> Firstly, let me say a big thankyou for this! It makes my life far easier at work when moving between my desk and our test floor.

Your welcome. Sound like we have similar jobs... ;)

> **DougEdey said:**
> I was wondering if there's some way to link this into emesene (or amsn) to change my status? emesene has a dbus plugin so i thought it should be ok!

To be honest I have never used amsn, but if you say it has a dbus interface then you should be fine. May be the same rules for running stuff as root or as the user would apply but it's a matter of figuring out what the commands are and how they work.

---

### Post by DougEdey on 2009-04-28
> **lunatico said:**
> 
To be honest I have never used amsn, but if you say it has a dbus interface then you should be fine. May be the same rules for running stuff as root or as the user would apply but it's a matter of figuring out what the commands are and how they work.

The problem is that I can't find anywhere that documents the DBUS interface :(

---

### Post by lunatico on 2009-04-28
> **DougEdey said:**
> The problem is that I can't find anywhere that documents the DBUS interface :(

Same happened to me with Pidgin so I joined their mailing list and started asking questions until a developer gave me the answers. Try that.

---

### Post by BoBaH32 on 2009-08-19
Awesome howto, thank you! I'll try it on my dell laptop.

---

### Post by nhmtnbkr on 2009-08-24
Hey, thanks for the tutorial.  I implemented it and it worked just fine ... until I went to log out. 

When I shut down, the computer went through it's normal shutdown screens, the screen went blank, then stayed power up.  I waited 5 mins and nothing.  I had to hold down the power button for seven seconds to turn it all the way off.  Then the next time I went to power up and log in, instead of the normal 30-45 seconds or so that it takes to get to the login screen, it took over 5 minutes.  Once in, I did a little poking around in the forums about these problems, starting with the shutdown problem.  I found this thread:

[http://ubuntuforums.org/showthread.php?t=1198992](http://ubuntuforums.org/showthread.php?t=1198992)

Talking about udev events and such, and I remembered going through your tutorial and entering the 80-thinkpad-T61.rules file.  As an experiment, I moved the file out of /etc/udev/rules.d up one level, and what do you know, shutdown and power were back to normal.  I repeated several times and sure enough, everything is fine and repeatable now.

So, my question is, what is magical about this file that is causing my powerup/shutdown issues.  Looking at the README in /etc/udev/rules.d, there is something about that number at the beginning of the file name, but by their description, 80 seems fine. 

Any ideas or tips you can offer?

Thanks,
Jim

---

### Post by lunatico on 2009-08-24
> **nhmtnbkr said:**
> So, my question is, what is magical about this file that is causing my powerup/shutdown issues.  Looking at the README in /etc/udev/rules.d, there is something about that number at the beginning of the file name, but by their description, 80 seems fine. 

Any ideas or tips you can offer?


Well as you could see 80 should be fine, the definition says:

```
  80   rules that run programs (but do not load modules)
```

But I have just checked on the computer I am at the moment (Thinkpad T61) and I have it down as /etc/udev/rules.d/60-thinkpad-T61.rules

I can't remember from when I wrote the tutorial if the 80 was a mistake or what, but again, from that README file 80 seems ok.

I'm assuming you are doing this on a Thinkpad right... not too sure what the behavior would be on other hardware.

Hope this helps, sorry I don't have a more specific answer...

---

### Post by nhmtnbkr on 2009-08-24
Hey there, I'm running this on a T61p.  I just changed the file name from an 80 to a 60 and the results are the same, slow boots and incomplete shutdowns.

I'll do some research and if I find a solution, I'll post it here on the thread.  

Thanks for our help.

---

### Post by lunatico on 2009-08-25
> **nhmtnbkr said:**
> 
I'll do some research and if I find a solution, I'll post it here on the thread.  


Me too! Lets make this a contest, the one who finds the solution first wins!!! HAHA

Anyway, I just tried this on a T61p and same story... :( So something changed from Ubuntu 8.10 to 9.04 because it was working fine on the T61p on 8.10.

Do not despair, we shall fix this!

---

### Post by nhmtnbkr on 2009-08-28
Well, I've played around with this a little bit.  I turned off the splash screen during bootup so I could see where things get hung up.  I booted into 3 different kernels from grub:

2.6.28-15 (default)
2.6.28-14
2.6.27-11

For all three, the boot hung for several minutes at the following lines:

[26.xxxxxx] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[26.xxxxxx] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input12

Without the 80- (or 60-) rule file in place in /etc/udev/rules.d, the boot up sequence moves through this step with no problem.

That's as much as I've had time to do, just putting it out there to see if it sparks any ideas.

---

### Post by lunatico on 2009-08-31
Found the solution to the startup delay! :P

Delete the file 80-thinkpad-T61.rules by:

```
sudo rm /etc/udev/rules.d/80-thinkpad-T61.rules
```

And instead of that we will catch the dock/undock with the following udev rule by:

```
gksudo gedit /lib/udev/rules.d/85-thinkpad-T61.rules
```

And paste the following:

```
KERNEL=="dock.0", ACTION=="change", RUN+="/etc/thinkpad/dock.sh"
```

The rest should be the same as we are still calling the dock.sh script.

Restart hal to immediately see the changes.

---

### Post by nhmtnbkr on 2009-08-31
Thanks man, that worked perfectly!

A couple of things.  First, would you mind shooting me an explanation as to why this works and the previous incarnation did not (or was slow).  

Second, I've run into another problem.  Just curious, but while you're docked, do you have an external monitor setup?  If so, is it configured in Xinerama mode?  I just set this up, and when I do lid open/close or dock/undock, my computer locks up tight.  No access whatsoever.  I have to hold down the power button for 7 secs to turn it off then power on.  Just for grins, I went back and tried it with the old rule (80-...) and it did the same thing.  I've done a cursory search and it seems folks run some scripts to change enabled screens, etc. when docking and undocking, I was just wondering if you've run into this before I dive deeper.  

Thanks again.

---

### Post by lunatico on 2009-08-31
> **nhmtnbkr said:**
> Thanks man, that worked perfectly!

You're very welcome.

> **nhmtnbkr said:**
> ... First, would you mind shooting me an explanation as to why this works and the previous incarnation did not (or was slow)... 

Don't you think I did it by myself, I had some help. Have a look at [this thread.]("http://www.nabble.com/A-new-udev-rule-gives-me-3min-startup-delay-tt25131831.html")

That lead me to read more about how udev works and stuff.

You should join that mailing list, people is very helpful and they know a lot.

> **nhmtnbkr said:**
> ... I've run into another problem.  Just curious, but while you're docked, do you have an external monitor setup?  If so, is it configured in Xinerama mode?  ....

I do have an external monitor...

Not familiar with xinerama sorry... My video card is an Nvidia, and the way I have it configured is that my external monitor is a clone of my laptop screen, and for the lid event I have it to do nothing from Power Management options. I use clone and not extended desktop because I already have 4 workspaces which is virtually 4 desktops.

Wish I could help more....

---

### Post by SlickRick on 2009-09-18
I'm trying to make sounds play when opening/closing and i can't get this to work. I've tried this guide as well as [http://ubuntuforums.org/showthread.php?t=563687](http://ubuntuforums.org/showthread.php?t=563687)
are there some commands that can detect problems?
i tried running cat /proc/acpi/button/lid/LID/state and it detects the lid state as open.

---

### Post by lunatico on 2009-09-18
> **SlickRick said:**
> are there some commands that can detect problems?

Well the easiest way is to try each part separately. You can also put some output with echo on your scripts so that when you run them you can see where they are failing. Are you getting errors?

If you run your ~/open and ~/close scripts do they work?
If yes, then is your ~/lid_event script running properly and calling them?

---

### Post by SlickRick on 2009-09-19
I tried running each script separately and I always get the sound playing with no errors, although I do have to put my password in to run them.
I tried echo after each line in the scripts and it seems the lid_event script is wrong since it made the closing sound play when I ran it

---

### Post by lunatico on 2009-09-19
> **SlickRick said:**
> I tried running each script separately and I always get the sound playing with no errors, although I do have to put my password in to run them.
Yes because they are meant to be run by root. The lid events are generated by kernel event owned by root. Try running them as root and they should work fine without even asking for password.

I tried echo after each line in the scripts and it seems the lid_event script is wrong since it made the closing sound play when I ran it[/QUOTE]

Mmm what hardware are you on?

---

### Post by SlickRick on 2009-09-19
Still get asked the password if i run them as root and still the lid gets detected as closed

I've got a Toshiba satellite L300-18E
Here are the full [specs]("http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&toshibaShop=false&com.broadvision.session.new=Yes&PRODUCT_ID=1056299")

---

### Post by lunatico on 2009-09-19
> **SlickRick said:**
> I've got a Toshiba satellite L300-18E

This was written for Thinkpads (T61 and T61p)...
You will have to find out what's going under the hood on your toshiba, I don't have one, sorry I can't help you.

---

### Post by SlickRick on 2009-09-19
maybe theres a way i can periodically run cat /proc/acpi/button/lid/LID/state and then open and close the lid and see if the computer is detecting the change?
also, what do you mean 'find out what's going under the hood on your toshiba'? I posted a link to my specs if that's what you mean, although I hardly see how my hardware would make any difference.

btw, BUMP

---

### Post by lunatico on 2009-09-19
> **SlickRick said:**
> also, what do you mean 'find out what's going under the hood on your toshiba'?
Hardware and hardware events are exposed to the OS in many different ways...

> **SlickRick said:**
> I posted a link to my specs if that's what you mean, 
Well but that's something you'll have to do by yourself. I don't have such hardware to test on... nor the time.

> **SlickRick said:**
> although I hardly see how my hardware would make any difference.
It will be different. When you install an OS it is installed to match your hardware, the best way possible...


Are you sure you have the /etc/acpi/lid.sh script? Was it there already? Is it running each time you open and close your lid? 

Try:

```
touch test
```

```
gksudo gedit /etc/acpi/lid.sh
```

and right after line #!/bin/bash put this

```
echo 1 >> test
```

Save and close.

Open and close your lid, for each time you do it it should be adding a 1 to the test file. If 1s are been added then you did something wrong when following the steps in this tutorial, if not then Ubuntu uses a different way to capture your lid event.

---

### Post by SlickRick on 2009-09-19
the test file just remains blank
If alter the permissions for the lid.sh file to not allow it to run, the screen is still blanked which leads me to believe that closing the screen doesn't run the lid.sh file, like you said. However, it was there, I didn't just create it myself.

I've managed to make my laptop play a sound when I click the power button by editing the powerbtn.sh file in the same folder as lid.sh

---

### Post by airtonix on 2010-02-26
Hi,

I notice that in your initial edits of lid.sh, you hardcode the path to the users home folder....

This means that for every new user on the laptop, you'd need to enter yet another line..which would end up calling many scripts and doing many things...

not good.

any way to dynamically call the user that is logged in ?

update : 04:46 PM

After some discussion on #wowuidev about the problem of multiple users, the scripts they would have and hardcoding paths to such scripts in each user on a system, it was concluded that using dbus would be a far better approach.

**Get the signal**
So, first... test that opening and closing the laptop lid fires off a dbus signal. Using dbus-monitor to get results while i closed and opened the laptop lid resutled in : 
```

$ dbus-monitor
...
signal sender=:1.19 -> dest=(null destination) serial=233 path=/org/gnome/PowerManager/Backlight; interface=org.gnome.PowerManager.Backlight; member=BrightnessChanged
   uint32 50
method call sender=:1.19 -> dest=:1.20 serial=234 path=/; interface=org.gnome.ScreenSaver; member=UnThrottle
   uint32 707299091
method return sender=:1.20 -> dest=:1.19 reply_serial=234
signal sender=:1.19 -> dest=(null destination) serial=235 path=/org/gnome/PowerManager/Backlight; interface=org.gnome.PowerManager.Backlight; member=BrightnessChanged
   uint32 50
...

```confirmed.

**Act on it**
This part requires a script to run when the user logins in.

It's purpose will be to watch for dbus events.

when *org.gnome.PowerManager.Backlight *fires off a signal that interests us, we act on it.

So far all i have is this (i have no experience with python what so ever, so this will take me a while to conjour up)

This file i created : ~/bin/laptop-lid/event-listener
```

#!/usr/bin/env python
import dbus, gobject
from dbus.mainloop.glib import DBusGMainLoop

def cb_func(message,sender=None):
    print "got signal ({0})  from {1} " .format(message,sender)
    # determine if lid is closed or open:
    # if open {
    # run bash script in ~/bin/laptop-lid/open 
    # }elseif closed {
    # run bash script in ~/bin/laptop-lid/closed
    # }

dbusSystemObject = "org.gnome.PowerManager.Backlight"
dbusSystemObjectPath = "/org/gnome/PowerManager/Backlight"

dbus.mainloop.glib.DBusGMainLoop(set_as_default=True)
bus = dbus.SessionBus()
bus.add_signal_receiver(cb_func,
                        dbus_interface=dbusSystemObject,
                        path=dbusSystemObjectPath,
                        sender_keyword='sender')

loop = gobject.MainLoop()
loop.run()

```So far i have it printing the following when i close and open the laptop lid : 
```

got signal (50)  from :1.19 
got signal (50)  from :1.19 

```

---

### Post by airtonix on 2010-02-27
More improvements (working version)

1. Create the following three files at these locations (next version i'll include ability to specify your open/close script locations as parameters[B]

~/bin/laptop-lid/open[/B]
```

 #!/bin/bash
notify-send "lid opened"
#play a open sound
aplay /usr/lib/openoffice/basis3.1/share/gallery/sounds/sparcle.wav
#change Pidgin status
purple-remote 'setstatus?status=available&message=I am here...'

```**~/bin/laptop-lid/close**
 ```

#!/bin/bash
aplay /usr/lib/openoffice/basis3.1/share/gallery/sounds/falling.wav
#change Pidgin status
purple-remote 'setstatus?status=away&message=My laptop lid is closed...'

```[B]

~/bin/laptop-lid/event[/B]
 ```

#!/usr/bin/env python
import os
import dbus, gobject
from dbus.mainloop.glib import DBusGMainLoop

class LaptopLid:

    def __init__(self):
        self.dbusSystemObject = "org.gnome.PowerManager.Backlight"
        self.dbusSystemObjectPath = "/org/gnome/PowerManager/Backlight"
        self.acpiLIDstatePath = "/proc/acpi/button/lid/LID0/state"                            #this may vary dending on your system
        self.scriptPath="~/bin/laptop-lid"
        self.state="closed"

        dbus.mainloop.glib.DBusGMainLoop(set_as_default=True)
        self.bus = dbus.SessionBus()
        self.bus.add_signal_receiver(self.cb_func, dbus_interface=self.dbusSystemObject, path=self.dbusSystemObjectPath)

        self.loop = gobject.MainLoop()
        self.loop.run()

    def cb_func(self,message,sender=None):
        #    if(laptopLidState==)
        f = open(self.acpiLIDstatePath, 'r').read()
        if f.count("open") > 0 : #and self.state=="closed" :
            print "opened"
            os.system('sh '+self.scriptPath+'/open')
            self.state = "open"
        elif f.count("closed") > 0 : # and self.state=="open":
            print "closed"
            os.system('sh '+self.scriptPath+'/close')
            self.state = "closed"

l = LaptopLid()

```**Make it run after login..**
1 open : system > preferences > startup applications
2. click add
3. name : DBUS Laptop Lid Event Detector
4. command : python ~/bin/laptop-lid/event

**Testing...**
Test it by opening terminal and typing : 
```
python ~/bin/laptop-lid/event
```

---

### Post by lunatico on 2010-02-27
Excellent contribution airtonix!

When I wrote this I never thought about a multi-user scenario, this was done on my personal work laptop, no one else will ever use it other than me.

I'll edit the main post to guide users wanting multi-user support for the lid event to come to your post.

---

### Post by SlickRick on 2010-02-27
when running dbus-monitor I do get some output but nothing when I open and close the lid.
This is the output I get
```
signal sender=org.freedesktop.DBus -> dest=:1.97 serial=2 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.97"
method call sender=:1.97 -> dest=org.freedesktop.DBus serial=3 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=AddMatch
   string "type='method_call'"
method call sender=:1.97 -> dest=org.freedesktop.DBus serial=4 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=AddMatch
   string "type='method_return'"
method call sender=:1.97 -> dest=org.freedesktop.DBus serial=5 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=AddMatch
   string "type='error'"
```

---

### Post by airtonix on 2010-02-27
> **SlickRick said:**
> when running dbus-monitor I do get some output  but nothing when I open and close the lid.

But i assume you do have a lid entry in : 
```
/proc/acpi/button/lid
```

This is what mine looks like : 
```

$ tree /proc/acpi/button
/proc/acpi/button
|-- lid
|   `-- LID0
|       |-- info
|       `-- state
|-- power
|   |-- PWRB
|   |   `-- info
|   `-- PWRF
|       `-- info
`-- sleep
    `-- SLPB


```

Not sure that it matters, but i have my lid event in gnome-power-manager set to blank the screen.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=148461&stc=1&d=1267317733[/IMG]
I assume you are running gnome ?

---

### Post by airtonix on 2010-02-27
I just discovered something else that might cause problems : 

In the above python dbus event listener, I am sniffing for an event signal sent by "org.gnome.PowerManager.Backlight", but this only fires when i close/open the lid if my power cable is plugged in.

Only org.gnome.Screensaver fires regardless of whether or not the power cable is plugged in.

problem is that I need a service : 
```

        self.dbusSystemObject = "org.gnome.PowerManager.Backlight"

```And a path : 
```

        self.dbusSystemObjectPath = "/org/gnome/PowerManager/Backlight"

```however if you look at the output from dbus-monitor when i close/open the laptop lid : 
```

method call sender=:1.19 -> dest=:1.20 serial=571 path=/; interface=org.gnome.ScreenSaver; member=Throttle
   string "Power screensaver"
   string "Laptop lid is closed"
method return sender=:1.20 -> dest=:1.19 reply_serial=571
   uint32 526562257
signal sender=:1.19 -> dest=(null destination) serial=572 path=/org/gnome/PowerManager/Backlight; interface=org.gnome.PowerManager.Backlight; member=BrightnessChanged
   uint32 50
method call sender=:1.19 -> dest=:1.20 serial=573 path=/; interface=org.gnome.ScreenSaver; member=UnThrottle
   uint32 526562257
method return sender=:1.20 -> dest=:1.19 reply_serial=573
signal sender=:1.19 -> dest=(null destination) serial=574 path=/org/gnome/PowerManager/Backlight; interface=org.gnome.PowerManager.Backlight; member=BrightnessChanged
   uint32 50

```org.gnome.ScreenSaver, does not have a valid path that i cant use in the above python dbus event listener.

---

### Post by SlickRick on 2010-02-27
> **airtonix said:**
> But i assume you do have a lid entry in : 
```
/proc/acpi/button/lid
```

This is what mine looks like : 
```

$ tree /proc/acpi/button
/proc/acpi/button
|-- lid
|   `-- LID0
|       |-- info
|       `-- state
|-- power
|   |-- PWRB
|   |   `-- info
|   `-- PWRF
|       `-- info
`-- sleep
    `-- SLPB


```

Not sure that it matters, but i have my lid event in gnome-power-manager set to blank the screen.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=148461&stc=1&d=1267317733[/IMG]
I assume you are running gnome ?

Mine looks like this:
```
$ tree /proc/acpi/button
/proc/acpi/button
|-- lid
|   `-- LID
|       |-- info
|       `-- state
`-- power
    |-- PWRB
    |   `-- info
    `-- PWRF
        `-- info
```

And yes, I am using gnome and I have the power manager set to blank screen

I tried running this a thousand times and closing the lid quickly and it seems the lid state changes to closed when I close it
```
cat /proc/acpi/button/lid/LID/state
```

So the event is detected but I have no idea where to go from here

---

### Post by airtonix on 2010-02-28
SlickRick, after trying to work out a better way to sniff the actual laptop lid dbus event, i found that by default dbus-monitor only listens to the session bus.

you should try running : ```
dbus-monitor --system
```Also, i've since changed aspects of the python event listener to look at the actual dbus lid objects signals ... you can check your dbus hal exposes such an object with : 

```

hal-find-by-property --key info.product --string "Lid Switch"

```My output from this looks like : 
```

/org/freedesktop/Hal/devices/computer_logicaldev_input_4

```
If you don't get any output, then try browsing through the output of : 
```

lshal > ~/lshal.txt && gedit ~/lshal.txt

```
See if you can find anything to do with a laptop lid switch/button.

still cleaning up the code i'm making then i'll post it here.

---

### Post by airtonix on 2010-02-28
[SIZE=5]Download[/SIZE]
[LIST]
[*]v0.03 [dbus-laptop-lid-listener.py](http://georgia.ubuntuforums.org/attachment.php?attachmentid=148640&stc=1&d=1267423990) 
[*]v0.02 [dbus-laptop-lid-listener.py]("http://ubuntuforums.org/attachment.php?attachmentid=148640&stc=1&d=1267409568")
[/LIST]

[SIZE=5]Install/Setup[/SIZE]
[LIST=1]
[*]download it somwhere to your homefolder (ie : ~/bin )
[*]make it exectuable :```
chmod +x ~/bin/dbus-laptop-lid-listener.py
```
[*]add it to your session startup applications :[LIST=1]
[*]system > preferences > startup applications
[*]click "add"
[*]Name : DBUS Laptop Lid Event Listener
[*]command : ```
~/bin/dbus-laptop-lid-listener.py listen
```
[*]click close.
[/LIST]
[*]Create a script to run when laptop lid OPENS : [LIST=1]
[*]```
gedit ~/bin/laptop-lid-opened.sh
```
[*]paste in the following  : ```

#!/bin/sh
notify-osd "lid open"
```
[*] make it executable : 
```
chmod +x ~/bin/laptop-lid-opened.sh
```
[/LIST]
[*]Create a script to run when laptop lid CLOSES : [LIST=1]
[*]```
gedit ~/bin/laptop-lid-closed.sh
```
[*]paste in the following  : ```
 
#!/bin/sh
# do stuff.
# like change awway status on empathy or pidgin,
# or pause rhythmbox, etc, etc. 
```
[*]make it executable : ```
 chmod +x ~/bin/laptop-lid-closed.sh
```
[/LIST]
[/LIST]

Script won't take effect till you either : 
[LIST]
[*]run it manually, or
[*]restart your current session by logging out and back in again.
[/LIST]
[SIZE=5]Syntax[/SIZE]

```
dbus-laptop-lid-listener.py mode openScript closeScript
```[SIZE=4]mode[/SIZE]
[LIST]
[*]**listen**
what you'd be interested in... sits in memory listening for dbus signals and runs your openScript when the acpi laptop lid state changes to "open" and your close script when it changes to "closed"
[*][B]test
[/B]prints out the hal address of your laptop lid switch.
[/LIST][SIZE=4]openScript[/SIZE], [SIZE=4]closeScript[/SIZE]
Any script, terminal commands, etc that can be executed under your users account.

---

### Post by SlickRick on 2010-03-01
running this
```
dbus-monitor --system
```
doesn't detect the lid event

I went through your tutorial and it doesn't work for me. When running the script manually I get this.
With the listen option
```
DBUS Laptop Lid Event Listener : Open Script Found
DBUS Laptop Lid Event Listener : Close Script Found
DBUS Laptop Lid Event Listener : Laptop Lid Hal Address << found laptop switch : /org/freedesktop/Hal/devices/computer_logicaldev_input_3 >>
DBUS Laptop Lid Event Listener : Listening << waiting for laptop lid events... >>
```
and the test option
```
DBUS Laptop Lid Event Listener : Laptop Lid Hal Address << found laptop switch : /org/freedesktop/Hal/devices/computer_logicaldev_input_3 >>
/org/freedesktop/Hal/devices/computer_logicaldev_input_3
```

---

### Post by airtonix on 2010-03-01
I had another idea, that you could use : 
```
inotifywait /proc/acpi/button/lid/LID/state --monitor
```while running that open/close the lid, see if that gives you a response (i think it will based on your previous encounter with this file)

if that works, i'll modify my script above to optionally work with inotify.

---

### Post by SlickRick on 2010-03-01
inotifywait didn't detect the event either. However, it did give a response if I try to otherwise use the state file like with cat or grep

---

### Post by airtonix on 2010-03-01
I seem to have same problem with inotify, initially on my first try it was printing out state changes in that file...

further attempts print nothing...

I'l Look at this more tomorrow.

---

### Post by airtonix on 2010-03-15
I'd like to continue with this project (even though i feel it's something that should be addressed by the existing window in gnome-power-manager), however I have assignments to deal with before I can give this serious attention.

There are a few things that need to be addressed based on lucids lack of hal : 

1. detect that a laptop lid is present without hal.
2. work out how to listen for a laptop lid dbus signal that does not rely on hal.
3. create a gui which has an accompanying notification-tray icon to activate a list of scripts for both closing and opening events.

---

### Post by lunatico on 2010-03-15
> **airtonix said:**
> even though i feel it's something that should be addressed by the existing window in gnome-power-manager

I agree. Unfortunately current gnome-power-manager lacks a lot of functionality. The way you can only choose pre-defined times is a big usability problem for example. Try to choose 'put computer to sleep' after 3 hours... you can't. You will have to go into gconf-editor and set the time manually.

Thanks for taking the time to look into this, I wish I was more skilled in Linux to give you a hand. If there's anything I can help with let me know.

---

### Post by airtonix on 2010-04-13
I've picked this up again and moved the idea in a direction that encompasses more than laptop lid open and close events(although by default this will be one of the default profiles provided).

[IMG]http://ubuntu-ky.ubuntuforums.org/attachment.php?attachmentid=153153&stc=1&d=1271176212[/IMG]

So far I plan on having it work like this : 


[LIST=1]
[*]user creates an 'object', which describes a DBUS interface, path and signal(s) to monitor.
[*]user then creates action(s) to be used by the object when it's signals fire
[*]actions can be grouped so you can have multiple actions running from each signal event. each action is executed in turn.
[/LIST]
I think it would be good to have a dbus object interface explorer included, but then we are approaching what d-feet already does... 

I also understand the author of d-feet plans to include the ability to associate scripts with signals being fired

---

### Post by lunatico on 2010-04-14
I just installed Ubuntu 9.10 on a Thinkpad W500 and applied these scripts. The lid still works as per the first post. The dock event needs a few changes.

Sorry I don't have time to properly edit the first post so I'll just add it here.

Basically follow the step on the first post, but then apply the changes mentioned in [post 20]("http://ubuntuforums.org/showpost.php?p=7874459&postcount=20") and then make sure that the /etc/thinkpad/dock.sh script is executable. I wasn't able to make it executable with chmod not even when logged in as root. What worked for me was launching nautilus from a root terminal and navigating to the dock.sh script, right-click -> properties and make it executable there.

Hope this helps. If not post here.

---

### Post by pete78 on 2011-06-05
The above described doch/undock events are not generated on my Lenovo W510 under Ubuntu 11.04. The content of /sys/devices/platform/dock.0/docked is also fixed to 0.
Is this a bug of udev, Ubuntu, the w510 or should that not work when I press the undock button of the docking station? The docking station is a "Lenovo ThinkPad Mini Dock Series 3 - Mini-Dock".

---

### Post by lunatico on 2011-06-09
> **pete78 said:**
> The above described doch/undock events are not generated on my Lenovo W510 under Ubuntu 11.04. The content of /sys/devices/platform/dock.0/docked is also fixed to 0.
Is this a bug of udev, Ubuntu, the w510 or should that not work when I press the undock button of the docking station? The docking station is a "Lenovo ThinkPad Mini Dock Series 3 - Mini-Dock".

I haven't tried this with 11.04 and I don't think I ever will because I just don't like it and find it very buggy.

To debug this run the bellow command and undock to see what you get:
```
udevadm monitor --environment
```

And see if the event you get when pressing the undock button matches your rule.

In my case when I press the undock button I get:
```
KERNEL[1307629733.862912] change   /devices/platform/dock.0 (platform)
UDEV_LOG=3
ACTION=change
DEVPATH=/devices/platform/dock.0
SUBSYSTEM=platform
EVENT=undock
MODALIAS=platform:dock
SEQNUM=2711
```

And you can see how this matches the rule:
```
KERNEL=="dock.0", ACTION=="change", RUN+="/etc/thinkpad/dock.sh"
```

Bear in mind I'm doing this on 10.04 and a Thinkpad W500.

I hope this helps.

---

### Post by apos on 2011-08-14
Hello out there,

Can confirm - according to the origninal first post - still works for Ubuntu Natty / 11.04.
I am on a T61 with a  nvidia graphics card (should also run on intel).

Only hal is removed, so **restart of udev** is required:

```
 sudo service udev restart
```

Furthermore, i changed the udev-script to /etc/udev/rules.d/80-thinkpad-T61.rules to

```
SUBSYSTEM=="platform", KERNEL=="dock.0", ACTION=="change", RUN+="/etc/thinkpad/dock.sh"
```

Due to the fact, that */etc/thinkpad/dock.sh* reads the /sys/.../docked file this is enough.

A list of the actual logged in user(s) you will get with the *last* command. BUT, if you are logged into another tty, you might be added twice (or more to that list). *uniq* assures that only one appearance of a user will be in the list. On a multiuser system you "could" run into trouble, but *grep -v ":0.0"* assures you'll only get the ones of the actual display (no remote ones).

That way a variable defined you can write in your */etc/thinkpad/dock.sh*:

```

#!/bin/sh
sleep 1
THEUSER="$(last | head | grep -v ":0.0" | grep -v pts | grep -v system | grep still | cut -d" " -f1)"
DOCKED=$(cat /sys/devices/platform/dock.0/docked)
case "$DOCKED" in
        "0")
        #undocked event
        /home/${THEUSER}/bin/thinkpad_undocked
        ;;
        "1")
        #docked event
        /home/${THEUSER}/bin/thinkpad_docked
        ;;
esac
exit 0

```

and in your *~/wherever/(docked|undocked)*:

```

#!/bin/bash
# Get the actual logged in user (TESTED). If there is a chance that more 
# than one user(name) is logged in, you have to sorround the 
# rest of the code with 
# for user in "${THEUSER}"; do [... the rest of code ...]; done
# and change all accurrences of ${THEUSER} with ${user}
# The latter is NOT TESTED
THEUSER="$(last | head | grep -v ":0.0" | grep -v pts | grep -v system | grep -m1 still | cut -d" " -f1 | uniq)"

# Rest of code
#This runs so that root can run the following command under the user's environment
source /home/${THEUSER}/.Xdbus
DISPLAY=:0.0 su ${THEUSER} -c "aplay /whereever/docked.wav"
# Next only for nvidia cards
DISPLAY=:0.0 su ${THEUSER} -c "/usr/bin/disper -i < /home/${THEUSER}/.disper/mySettings.settings"
DISPLAY=:0.0 su ${THEUSER} -c "notify-send  \"Thinkpad Docked\" -i /wherever/process-stop.png \"Thinkpad succesfully docked. Do not remove the device without pressing the undock button at the dock.\""
logger "$0 - lenovo pc docked for user ${THEUSER} ..."

```

Be aware, that in the latter i added the code for showing notify messages and using **disper** to add a second monitor (**only works with nvidia cards**). The settings-file for disper was simply exported on the commandline with *disper -p >  mySetting.settings* and found the dot-disper directory a good place to store it (see *disper --help*). To revert to single monitor mode simply use *disper -s*. Logger logs everything to syslog. I found the *process-stop.png* (Faenza icon theme) and *streamtuner.png* files very convenient, because they match the led icons on the dock.

Another tip: I had to reinstall tp-smapi due to a compilation error during a linux kernel install (this runs dkms again):

```
apt-get install --reinstall tp-smapi-dkms
update-initramfs -k all -c

```

Greets and have fun
Axel

---

### Post by Rob___ on 2011-10-10
Thanks to lunatico for the clue:
> **lunatico said:**
> I haven't tried this with 11.04 and I don't think I ever will because I just don't like it and find it very buggy. To debug this run the command below  and undock to see what you get:
```
udevadm monitor --environment
```And see if the event you get when pressing the undock button matches your rule..
I'm running a Dell Latitude E6400 with Ubuntu 11 and the earlier pieces helped but udev wasn't firing into my log file.  Monitoring udevadm monitor --environment by running 
[FONT=Courier New]sudo udevadm monitor --environment >> device_event.log [/FONT]
found I didn't have those events. So I followed the examples and rewrote the rules.  The end result is a reconfiguration of the display when I dock or undock.  It merges the technique from [http://morgancollett.wordpress.com/2008/11/25/nvidia-twinview-and-xrandr/](http://morgancollett.wordpress.com/2008/11/25/nvidia-twinview-and-xrandr/) to setup the xorg.conf with multiple modes.  Then I use the event to change the modes.
====================================================================
  **Configuration of docking to change the Nvidia Twinview settings**
[SIZE=2]1. First configure the system for dual monitors (usually ```
sudo nvidia-settings
```), then use **sudo gedit /etc/X11/xorg.conf** go to the     Screen section it will appear like the example [/SIZE]

```
Section "Screen"  
     Identifier     "Screen0"  
     Device         "Device0"  
     Monitor        "Monitor0"  
     DefaultDepth    24  
     Option         "TwinView" "1"  
     Option         "TwinViewXineramaInfoOrder" "DFP-1"  
     Option         "metamodes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0
     SubSection     "Display"  
         Depth       24  
     EndSubSection  
 EndSection

```[SIZE=2]2. Modify the line for the metamodes     by adding a deliminator ; and duplicating the settings for the     primary (laptop monitor).  The secondary monitor will be set to null     as below.[/SIZE]
```

     Option         "metamodes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0;DFP-0: nvidia-auto-select +0+0, DFP-1: null" 

```[SIZE=2]3. Next open a terminal  and test the alternate monitor settings.
     a) In a command prompt type[/SIZE]
```
   xrandr -s     1 
```[SIZE=2]       and press enter to change to single monitor.  
        The system will change to a single monitor without restarting the X environment.
     b) Type ```
xrandr -s 0 
```to change back to dual monitors

With this configured we just need to capture the change of the docking status using the techniques in this thread.[/SIZE]
[SIZE=3]**Capture Docking Event**[/SIZE]
[SIZE=2]1)  Hardware environments vary so you will need to determine the events to monitor
    a) type sudo [/SIZE][FONT=TlwgMono][SIZE=2]**udevadm monitor &#8211;environment >> ~/device_eventlog.log**[/SIZE][/FONT][SIZE=2]     at a command prompt. I prefer the file becasue it's easier to parse.
    b) Change the hardware you wish to monitor     (undock, unplug, depower..)
    c) In the terminal press CTRL+c to     terminate the udevadm monitor &#8211;environment command.
2) Examine the [/SIZE][FONT=TlwgMono][SIZE=2]**~/device_eventlog.log**[/SIZE][/FONT][SIZE=2]      it will display all the add, change and removes with details for each device.
[/SIZE][INDENT] [FONT=Lohit Tamil][SIZE=1]KERNEL[1318277278.266250]  add       /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/0003:413C:2101.0017/hidraw/hidraw2  (hidraw)[/SIZE][/FONT]
 [FONT=Lohit Tamil][SIZE=1]UDEV_LOG=3 [/SIZE][/FONT]
[FONT=Lohit Tamil][SIZE=1]ACTION=add [/SIZE][/FONT]
[FONT=Lohit Tamil][SIZE=1]SUBSYSTEM=block [/SIZE][/FONT]
[FONT=Lohit Tamil][SIZE=1]DEVNAME= [FONT=Courier 10 Pitch][SIZE=2]hidraw2[/SIZE][/FONT] [/SIZE][/FONT]
[FONT=Lohit Tamil][SIZE=1]DEVTYPE=disk [/SIZE][/FONT]
[FONT=Lohit Tamil][SIZE=1]SEQNUM=2585 [/SIZE][/FONT]
[FONT=Lohit Tamil][SIZE=1]MAJOR=8 [/SIZE][/FONT]
[FONT=Lohit Tamil][SIZE=1]MINOR=16[/SIZE][/FONT]
[/INDENT][SIZE=2]3) Hook the docking event by writing     a rule in the /lib/udev/rules.d folder as  such as
/lib/udev/rules.d/85-Latitude-E6400.rules with a content     of:[/SIZE]
[LEFT]```

KERNEL=="hidraw2",     DEVNAME=="hidraw2",ACTION=="add",     RUN+="/etc/dell/dock.sh 1" 
KERNEL=="hidraw2",     DEVNAME=="hidraw2",ACTION=="remove",     RUN+="/etc/dell/dock.sh 0"
```[/LEFT]
[FONT=Arial][SIZE=2]4) Finally create the event to handle docking and undocking     /etc/dell/dock.sh script[/SIZE][/FONT]
                           ```
#!/bin/sh 
 # wait for the dock state to change 
 sleep 1 
 # Get the actual logged in user (TESTED). If there is a chance that more  
 # than one user(name) is logged in, you have to sorround the  
 # rest of the code with  
 # for user in "${THEUSER}"; do [... the rest of code ...]; done 
 # and change all accurrences of ${THEUSER} with ${user} 
 # The latter is NOT TESTED 
 THEUSER="$(last | head | grep -v ":0.0" | grep -v pts | grep -v system | grep -m1 still | cut -d" " -f1 | uniq)" 
  
 #This runs so that root can run the following command under the user's environment 
 source /home/${THEUSER}/.Xdbus 
  
 case "$1" in 
     "0") 
     #undocked event 
     DISPLAY=:0.0 su ${THEUSER} -c "xrandr -s 1" 
     # Removed  echo 'undocked event' >> /etc/dell/docking.log 
     logger 'undocked event'
     ;; 
     "1") 
     #docked event 
     DISPLAY=:0.0 su ${THEUSER} -c "xrandr -s 0" 
     # removed echo 'docked event' >> /etc/dell/docking.log 
     logger 'docked event'
     ;; 
 esac 
 exit 0

```Again thanks to lunatico and everyone for this information

---

### Post by apos on 2011-10-10
@Rob____

Thanks for your article, just for note there're some common rules for log files on *nix systems:

[LIST=1]
[*]log files should  be placed in */var/log/wherever*, not in */etc/*. */etc/* should only be for configuration files.

[*]There is a very handy tool for creating logging entries called "logger" (see logger --help or man logger). Messages created with it go into /var/log/syslog by default. This file won't grew up until forever, but will be zipped from time to time. And, no hassle with rights about log files.
[/LIST]

So 
```
logger test
```

comes to
```

tail -f /var/log/syslog
[...]
# Oct 10 23:07:12 panama logger: test
```

Cool, or? Saves a lot of *echo "..." >>'s*  ;)

---

### Post by Rob___ on 2011-10-11
> **apos said:**
> @Rob____

Thanks for your article, just for note there're some common rules for log files on *nix systems:

[LIST=1]
[*]log files should  be placed in */var/log/wherever*, not in */etc/*. */etc/* should only be for configuration files.
[*]There is a very handy tool for creating logging entries called "logger" (see logger --help or man logger). Messages created with it go into /var/log/syslog by default. This file won't grew up until forever, but will be zipped from time to time. And, no hassle with rights about log files.
[/LIST]

So 
```
logger test
```comes to
```

tail -f /var/log/syslog
[...]
# Oct 10 23:07:12 panama logger: test
```Cool, or? Saves a lot of *echo "..." >>'s*  ;)

Sorry about that, bad form on my part.  I'll give it a fix.  The other item I found is the 

System Setting -> Log File Viewer includes UDEV so that can be used as a reference too.

---

### Post by Rob___ on 2011-10-11
Change/Addition:

I added ;DFP-0: null, DFP-1: nvidia-auto-select +0+0 to the options and set the lid close event when docked to run xrandr -s 2 to disable the laptop monitor and organize the desktop.  


Option         "metamodes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0;DFP-0: nvidia-auto-select +0+0, DFP-1: null;DFP-0: null, DFP-1: nvidia-auto-select +0+0"

---

### Post by lunatico on 2012-07-25
> **pete78 said:**
> The above described doch/undock events are not generated on my Lenovo W510 under Ubuntu 11.04. The content of /sys/devices/platform/dock.0/docked is also fixed to 0.
Is this a bug of udev, Ubuntu, the w510 or should that not work when I press the undock button of the docking station? The docking station is a "Lenovo ThinkPad Mini Dock Series 3 - Mini-Dock".

Hey! Did you ever got around this?

---

### Post by lunatico on 2012-09-19
> **lunatico said:**
> Hey! Did you ever got around this?

I'm using a ThinkPad W520 with a ThinkPad Mini Dock Plus Series 3 - 170W now and the lid open/close still works the same way but the dock/undock events has changed.
I don't have time to write down specific steps but I have attached the necessary scripts. Just unzip the files and place them on same path as source.

Open the files and change paths to match <user> with your username (for home directory).

Make the following files executable:
/etc/thinkpad/dock.sh
/etc/thinkpad/undock.sh
/home/<user>/scripts/dock/docked
/home/<user>/scripts/dock/undocked

Read the first post of this tutorial to understand user's environment so that 'source /home/<user>/.Xdbus' works.

Note: On the .../undocked file the command to change the display to laptop monitor is commented out because I've chosen to run that when I do laptop lid open. Your choice.

---

