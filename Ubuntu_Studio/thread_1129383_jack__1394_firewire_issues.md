---
title: "jack / 1394 firewire issues"
date: 2009-04-18
forum: Ubuntu Studio
---

### Post by mypetjaws on 2009-04-18
Hi! My name´s Erik. I´ve been running Ubuntu Studio now for a few months and I am very happy thus far (bye bye windows!) I actually kind of enjoy puzzling out the few bugs. That said: This one is stumping me. 

I am attempting to use a Presonus Firepod, which connects thru a 1394. When I run jack, it immediately crashes. The message window in jack asks me if my 1394 drivers are installed:

[B]Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: No such file or directory
Is ieee1394 and raw1394 driver loaded?[/B]

However, when I go into the terminal and run the command
**lspci -v**, I get this listing:

[B]01:00.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10 [OHCI])
	Subsystem: Adaptec Unknown device 0034
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at ff8fd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>[/B]

So is is Ubuntu or more specifically qjackctl detecting it, but unable to utilize the firewire port?
Do I somehow have to unlock access, or is the adaptec firewire card I have incompatible?

Also, when i run jack I get this message, which is a separate issue altogether:


[B]Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.[/B]

Any help would be great! Thanks!

---

### Post by babarosa on 2009-04-18
Hi mypetjaws,

welcome to the club.

Please visit "www.ffado.org", there is a lot of information how to set up a firewire audio interface with gnu/linux. Some files have to be adjusted and some settings have to be made.

Post your question there in the forum, the guys and gals are very helpful and will guide you through your problems. Once set up correctly, firepod works very fine with ubuntu.

Best wishes, Michael

---

### Post by mypetjaws on 2009-04-18
Wow! that was quick. Thanks! I like this community idea.

---

### Post by kayosiii on 2009-04-18
there are a few things... Make sure that you are allowed to use the raw firewire device... The easiest way to do this is via the ubuntustudio control panel. If you don't have ubuntu studio then you can install just this panel by loading in the package ubuntustudio-control.

Second check your firewire cables. Make sure they are making a good connection. That should hopefully give you a spot to get started.

---

### Post by mypetjaws on 2009-04-19
Hmm yeah the raw1394 is enabled, connections are secure. I registered at ffado.org but I cant seem to find an actual forum. Is it more of a mailing list? I think this ones gonna take some patience.
Thanks,
-Erik

---

### Post by babarosa on 2009-04-19
@mypetjaws, 

sorry, you are correct: it is a mailing list, not a forum; an answer can take some time.
After compiling or installing ffado from the repo at [www.ffado.org](www.ffado.org), generate the following file in /etc/udev/rules.d:

40-linux1394.rules 

with the content:
KERNEL="raw1394", NAME="%k"
KERNEL="dv1394*", NAME="dv1394/%n" 
KERNEL="video1394*", NAME="video1394/%n" 

Then allow your user access to the groups:
audio, disk, video, plugdev

Additional settings have to be made in etc/security/limits.conf to get jackd properly to work.

Regards, Michael

---

### Post by mypetjaws on 2009-04-20
Thanks, Micheal. Just a couple of questions- I´m in no way a code guru... since ffado is a beta would I be safer sticking to freebob in terms of bugs I´m going to have to work out? I have no problems installing ffado if it´s resonably safe, I just don´t really know its reputation at all. Again, thanks for all your help with this.

-Erik


edit: then again, freebob isnt working for me at all so I guess that would just keep me at square 1

---

### Post by babarosa on 2009-04-20
Erik,
you don't have to be a linux/gnu guru - me is no either, I only struggled already through the (sadly still necessary) tinkering.

"Freebob" is an old firewire driver model, superseded by the actual "ffado", which is a firewire driver plus a mixing console with buttons and level controls for your special hardware.
Of course you are to use "ffado" ;-), in the applications it will appear as "firewire".

At "www.ffado.org" your device is listed as "reported to work". This immediately leads me once again to the advice to seek help primarily at the ffado mailing list. Users with a Presonus Firepod and the programer himself, Pieter, will help you with competent advice.

The ffado from the repo works fine although it is beta, just give it a try. Later, when you are more experienced, you can start to compile ffado, jackd and qjackctl by yourselves with the benefit of an even better performance (e.g. debug mode off, ...).
In the meantime I usually compile all softwares by myselves.
Once set up properly, a gnu/linux system offers a very stable audio workstation (e.g. I record 5 tracks of 32bit/44.1 KHz at "4.31 ms" latencies without any xruns for hours on a 2GHz Celeron notebook!)

Just prepare yourself to do some tinkering, mainly

1.) install a rt-kernel (I prefer hardy)
1a.) install all the audio softwares you need/want
then
2.) install ffado from ffado's repository (jackd comes with it)
3.) generate 40-linux1394.rules
4.) give access to the groups
5.) adjust etc/limits.conf as recommended on ffado's wiki or in many threads in this forum
6.) install qjackctl
7.) adjust the settings in qjackctl as recommended in many threads in this forum

Good luck,
Michael

---

### Post by mypetjaws on 2009-04-21
Thanks for all your help, I´m about to get cracking on this. Kind of exciting, the idea of trying the successor to the freebob software before it´s released. Thanks again!
I&#314;l let you know how it all works out.

Best,

-Erik

---

### Post by Stochastic on 2009-05-01
Hmm, babarosa, I think you're over-complicating the setup process in Jaunty.  It used to require many steps to get firewire working, but now it should be fairly simple.

Assuming you've got the ubuntustudio-audio package and the ubuntustudio-controls package installed, the setup should be:
1) Open System->Administration->Ubuntu Studio Controls, check the 'enable raw1394' checkmark box, and click apply
2) Open System->Administration->Users & Groups, click Unlock, then click 'add group', title the group "video" (without quotes) and make yourself a member (tick the checkbox).  Click okay, close that.
3) Reboot your system with the firepod plugged into the firewire port and turned on.
4) Start jack with the 'firewire' driver.

If you've created the 40-linux1394 file that Babarosa talked about then you may want to rename it to backup40-linux1394 before step 3.

The other settings in Ubuntu Studio Controls are also recommended for better performace with audio (except the Ctrl+Alt+Backspace one, that's just for convenience).

---

### Post by babarosa on 2009-05-01
**@ stroboscopic** ;-)

my nickname is "babarosa", not "barbosa" nor "barbosoa" as you wrote earlier. Please read more carefully.

Erik aka mypetjaws wrote "... I´ve been running Ubuntu Studio now **for a few months** and I am very happy thus far (bye bye windows!)" exactly one week ago. So why I am to assume he is using v9.04 which was published exactly one week ago?

Keeping this in my mind I think my advices were not too complicated, and they work on v8.10 and v8.04, I use them on my system successfully too.

If they are actually too complicated, I apologize for that :guitar:

---

### Post by mypetjaws on 2009-05-01
No luck. Started Jack with the firewire driver setting, with also the presets for Intrepid posted on the ffado wiki ([[COLOR="Blue"]**http://subversion.ffado.org/wiki/StepByStepUbuntuStudio8.10RT**[/COLOR]]("http://subversion.ffado.org/wiki/StepByStepUbuntuStudio8.10RT")) 

Jack still said it couldn't get the 1394 handle in the message window.

Anyways, when I follow the directions for detecting modules/permissions on the ffado wiki [[COLOR="Blue"][COLOR="Blue"]**http://subversion.ffado.org/wiki/KernelModuleAndPermissions**[/COLOR][/COLOR]]("http://subversion.ffado.org/wiki/KernelModuleAndPermissions")

 lsmod | grep 1394

produces the following:

dv1394                 26044  0 
raw1394                33116  0 
ohci1394               38832  1 dv1394
ieee1394               95932  4 sbp2,dv1394,raw1394,ohci1394

So I'm assuming the module is there.

ls -al /dev/raw1394

produces:

crw-rw---- 1 root root 171, 0 2009-05-01 15:01 /dev/raw1394

So I see that I nor any groups have read/write permission even after enabling raw 1394, creating group 'video' etc.
I'm assuming that is a problem.

I did also realize that there is no rules file whatsoever in etc/udev/rulesd. pertaining to firewire- it's in lib/udev/rulesd. Does this path difference matter?




Thanks everyone for your help, I really appreciate it.

-Erik

---

### Post by mypetjaws on 2009-05-01
No babarosa, your instructions weren't too complicated. I infact was using 8.04 up until 2 days ago when I found out that ffado was going to be included out of the box with Jaunty, I just upgraded instead of installing it manually in Hardy. You are and have been very helpful, thank you for turning me onto ffado.

---

### Post by babarosa on 2009-05-01
Hi erik,

I had to give access not only to group **video**, but also to 
[LIST]
[*]audio
[*]disk
[*]plugdev
[*]yourname
[*]video
[/LIST]

additionally give all rights to the user yourname, look here
[LIST]
[*][http://www.servimg.com/image_preview.php?i=14&u=12842335](http://www.servimg.com/image_preview.php?i=14&u=12842335)
[*][http://www.servimg.com/image_preview.php?i=15&u=12842335](http://www.servimg.com/image_preview.php?i=15&u=12842335)
[*][http://www.servimg.com/image_preview.php?i=16&u=12842335](http://www.servimg.com/image_preview.php?i=16&u=12842335)
[*][http://www.servimg.com/image_preview.php?i=17&u=12842335](http://www.servimg.com/image_preview.php?i=17&u=12842335)
[/LIST]

Try this, and if does not help, we try the next!

Regards, Michael

---

### Post by fedexnman on 2009-05-01
thx stochastic . i followed ur directions on page1 and things worked perfectly. i used syntac pkg mgr ,  i also downloaded ffado mixer... i bought an echo audiofire4 n got i everything working with ffado mixer an jackd the launched ardour. im lovin ffado. ubuntu9.04 jj  this is so exciting.  i couldnt get rt kernal to work though got nvidia driver error.  thx stochastic):P

---

### Post by Stochastic on 2009-05-02
Yes, sorry I should have mentioned that the 9.04 thing came from a private message that Erik sent me requesting my help.  I looked through his past posts and started troubleshooting here.  

Babarosa, (is it okay if it's capitalized?) I've edited the post above where I've misquoted your name - sorry about that.  In general, I hope I haven't directed my critiques at you but rather toward the advice.  I think a casual quip has hurt more than was intended, my apologies.

Erik, can you post the output of the following commands:
```
grep -H -n raw1394 /etc/udev/rules.d/*
```
```
grep -H -n raw1394 /lib/udev/rules.d/*
```

---

### Post by mypetjaws on 2009-05-02
Oddly enough there is no output. Just another blank command line. I haven't done anything to modify either of those files, I'm not sure why nothing came up. Here are the contents of lib/udev/rules.d/50-udev-rules.default pertaining to firewire when I access via file browser. 

# Firewire
KERNEL=="dv1394[0-9]*",		NAME="dv1394/%n", GROUP="video"
KERNEL=="video1394[0-9]*",	NAME="video1394/%n", GROUP="video"

---

### Post by mypetjaws on 2009-05-02
Also before this post I had already changed the group permission for dev/raw1394 to incclude group 'video', but after rebooting, 

ls -l /dev/raw1394 tells me its been reset back to group 'root':

erik@scout:~$ ls -l /dev/raw1394
crw-rw---- 1 root root 171, 0 2009-05-02 11:03 /dev/raw1394



Oh- and Michael I followed your instructions for groups and group properties, still no luck. I'm stumped. But I know theres a way.

---

### Post by Stochastic on 2009-05-02
mypetjaws, please post the output of the commands listed in post #16.

If Ubuntu Studio controls is up to date, the permissions line should be at the bottom of the file (not in the firewire group), but please post the output of those commands.

---

### Post by mypetjaws on 2009-05-03
```
erik@scout:~$ grep -H -n raw1394 /etc/udev/rules.d/*
erik@scout:~$ 

```
```
erik@scout:~$ grep -H -n raw1394 /etc/udev/rules.d/*
erik@scout:~$ 
```

there is no output. just another command line. Forgive me but I'm not following here, I don't know why there would be no output besides that something is missing. But I haven't modified any files either.

---

### Post by Stochastic on 2009-05-03
Okay, I just needed to make sure what the output of that was (i.e. maybe you had too many rules lines, maybe none).

Can you try the following: 
- open Ubuntu Studio Controls
- if 'enable raw1394' is checked, uncheck it then click apply
- check 'enable raw1394'
- click apply
- click close
- reboot
- run: grep -H -n raw1394 /lib/udev/rules.d/*
- post the output here

If there is an output to that command, then give jack a try too, hopefully that fixed it.
If there's no output to that command, chances are you have not updated your system in a while (that or there's a bug in Ubuntu Studio Controls that I'm not aware of).

---

### Post by mypetjaws on 2009-05-03
After refreshing the enable raw1394 in Ubuntu Studios:


```
erik@scout:~$ grep -H -n raw1394 /lib/udev/rules.d/*
erik@scout:~$
```


Is there a possibility it's my fireiwre card? I don't know, it's listed when I run 
```
erik@scout:~$ lspci -v
01:00.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10)
	Subsystem: Adaptec Device 0034
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at ff8fd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394
```

Maybe I should reinstall ubuntu studio controls from synaptic?


Oh and I double checked system update just to be sure, my system is fully up to date.

---

### Post by rafafredd on 2009-05-03
Hey, you are lucky, I just posted my tutorial today... you might want to check that:

[http://ubuntuforums.org/showthread.php?p=7206780#post7206780](http://ubuntuforums.org/showthread.php?p=7206780#post7206780)

I've tried Ubuntu Studio many times, and I don't like it. I prefer a fresh Ubuntu Hardy install for audio. If you follow the hints, you will surely have it working.

---

### Post by Stochastic on 2009-05-04
> **mypetjaws said:**
> 
Maybe I should reinstall ubuntu studio controls from synaptic?


Oh and I double checked system update just to be sure, my system is fully up to date.

Hmm, that's very strange, it doesn't look like Ubuntu Studio Controls is adding the line it should be adding.

First, could you help with a couple steps to pinpoint where Controls is going wrong:
- can you run "sudo ubuntustudio-controls" from a terminal, and attempt to re-enable raw1394, and post the output from the terminal
- what do the outputs of these commands say: ```
apt-cache policy ubuntustudio-controls
ls -l /usr/bin/ubuntustudio-controls
sudo grep -n raw1394 /usr/bin/ubuntustudio-controls

```


Second, (and we need to do this second as to not affect the results of the first part) let's manually take care of what Ubuntu Studio Controls should have automatically done:
- run ```
sudo gedit /lib/udev/rules.d/50-udev-default.rules
```
- add this line anywhere in that file (though under the #Firewire line is probably nicest) ```
KERNEL=="raw1394",              GROUP="video"
```
- save the file and close the program
- run ```
sudo gedit /etc/modules
```
- add this line to the bottom of the file ```
raw1394
```
- save the file and close the program

That's what Ubuntu Studio Controls in Jaunty should have done for you.  Reboot your computer and see if the settings now work.

---

### Post by mypetjaws on 2009-05-04
Alright- 


First:

```
erik@scout:~$ sudo ubuntustudio-controls

__main__
/usr/bin/ubuntustudio-controls:33: GtkWarning: Ignoring the separator setting
  self.wTree = gtk.glade.XML(self.gladefile)

(ubuntustudio-controls:3378): libglade-WARNING **: could not find a parent that handles internal children for `vbox'
{'raw1394_checkbutton': False}
Showing warning
Nice toggled
True
False
Removing settings
@audio - memlock 

Traceback (most recent call last):
  File "/usr/bin/ubuntustudio-controls", line 99, in apply_settings
    instanceName.rm_setting()
  File "/usr/lib/python2.6/dist-packages/changesettings.py", line 80, in rm_setting
    self.rm_list.remove(self.remove_string)
ValueError: list.remove(x): x not in list

```

2nd

```
erik@scout:~$ apt-cache policy ubuntustudio-controls
ubuntustudio-controls:
  Installed: 0.4.4ubuntu1
  Candidate: 0.4.4ubuntu1
  Version table:
 *** 0.4.4ubuntu1 0
        500 cdrom://Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4) jaunty/universe Packages
        500 http://us.archive.ubuntu.com jaunty/universe Packages
        100 /var/lib/dpkg/status
```

3rd

```
erik@scout:~$ ls -l /usr/bin/ubuntustudio-controls
-rwxr-xr-x 1 root root 8812 2009-04-16 15:32 /usr/bin/ubuntustudio-controls
erik@scout:~$ sudo grep -n raw1394 /usr/bin/ubuntustudio-controls
38:    self.raw1394Warning = self.wTree.get_widget("raw_dialog")
47:            "on_raw1394_checkbutton_toggled" : self.check_raw1394_enabled,
64:        self.newlines = [self.regex.sub('KERNEL==\"raw1394\",\t\t\tGROUP=\"disk\"', item) for item in self._open_file()]
69:  raw1394 = ChangeSettings("/lib/udev/rules.d/50-udev-default.rules", r"KERNEL==\"raw1394\",\t\tGROUP=\"video\"", "KERNEL==\"raw1394\",\t\tGROUP=\"video\"")
70:  load_raw1394_module = ChangeSettings("/etc/modules", r"raw1394", "raw1394")
86:                             self.wTree.get_widget('raw1394_checkbutton') : [self.raw1394, self.load_raw1394_module], 
115:  def check_raw1394_enabled(self, toggled_button):
116:    print self.settings_value['raw1394']
117:    first = self.settings_value['raw1394']['raw1394_checkbutton']
119:      self.show_raw1394_warning(toggled_button)
125:  def show_raw1394_warning(self, toggled_button):
127:      self.raw1394Warning.run()
128:      self.raw1394Warning.hide()
160:    self.settings_value['raw1394'] = { 'raw1394_checkbutton' : self.wTree.get_widget('raw1394_checkbutton').get_active() } 
```



/lib/udev/rules.d/50-udev-default.rules did not have that line in the file until I added it.

/etc/modules already had the raw1394 line in the file

Another thing that was weird- when opening ubuntu studio controls through the desktop gui,  'enable raw1394' was checked off.

 Running it with a command from the terminal cause the control box to pop up, but nothing was selected in it.

---

### Post by mypetjaws on 2009-05-04
HOLY CRAP stochastic YOU ARE SOME KIND OF WIZARD

Jack running!

beautiful blue light glowing on the Firepod!

you RULE
THANK YOU!!!!!!



thank God I didn't follow post #23 (no offense rafafredd but I wasn't about to downgrade)


Also thanks for all your time and help  babarosa!

---

### Post by Stochastic on 2009-05-04
> **mypetjaws said:**
> HOLY CRAP stochastic YOU ARE SOME KIND OF WIZARD<snip>
beautiful blue light glowing on the Firepod!

My name is stroboscopic for a reason!
Glad to see it's working.

Oh, and one last thing, I should note that I messed up a bit, the code to run ubuntustudio-controls from the terminal should have been gksudo rather than sudo.  If you don't mind, could you run that to see if the same error comes up?

---

### Post by mypetjaws on 2009-05-04
```
erik@scout:~$ gksudo ubuntustudio-controls
__main__
{'raw1394_checkbutton': True}
Toggle button active, not running warning
Nice toggled
@audio - nice -19

(ubuntustudio-controls:3603): libglade-WARNING **: could not find a parent that handles internal children for `vbox'
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS

```


There it is. Should I file a bug report about all this?

---

### Post by Stochastic on 2009-05-04
wow. now that's a meaningful error output ;)
"SSSSSSSSSSSSSSSSSSSSSSSS"

Try re-installing Ubuntu Studio Controls, 
```
sudo apt-get purge ubuntustudio-controls
sudo apt-get install ubuntustudio-controls
```
see if the problem goes away, if not, file a bug report.  I'd mention in the bug report how you installed ubuntustudio-controls (i.e. was it an upgrade from 8.10, 8.04, or a fresh install).

---

### Post by mypetjaws on 2009-05-04
```
erik@scout:~$ gksudo ubuntustudio-controls
__main__
/usr/bin/ubuntustudio-controls:33: GtkWarning: Ignoring the separator setting{'raw1394_checkbutton': True}
Toggle button active, not running warning
Nice toggled
@audio - nice -19
  self.wTree = gtk.glade.XML(self.gladefile)

(ubuntustudio-controls:3684): libglade-WARNING **: could not find a parent that handles internal children for `vbox'
erik@scout:~$
```

---

### Post by trulan on 2009-06-08
> **Stochastic said:**
> Let's manually take care of what Ubuntu Studio Controls should have automatically done:
- run ```
sudo gedit /lib/udev/rules.d/50-udev-default.rules
```- add this line anywhere in that file (though under the #Firewire line is probably nicest) ```
KERNEL=="raw1394",              GROUP="video"
```- save the file and close the program.
I had to manually do this step as well on my fresh install of Jaunty Studio amd64.

By the way, thanks a bunch. I only installed ubuntu a few days ago and already I am recording multiple tracks, full duplex on a firepod. It's much easier than all the how-to's indicate as most of the work is already done in this version.

---

### Post by mypetjaws on 2009-09-01
now 50-udev-default.rules has a message that says do not edit this file it will be overwritten on update. And the same bs is happening before where the permissions for raw1394 are not being recognized. But i'm not supposed to edit the file. WTF?

---

### Post by trulan on 2009-09-01
I think I would ignore the warning and edit the file - I mean, you know what is supposed to go there, and it's not being put there, so, edit it.  There ought to be a way to make the system get things right automatically.  But if that part is obviously not working...

---

### Post by Stochastic on 2009-09-02
> **mypetjaws said:**
> now 50-udev-default.rules has a message that says do not edit this file it will be overwritten on update. And the same bs is happening before where the permissions for raw1394 are not being recognized. But i'm not supposed to edit the file. WTF?

You're quite right about that warning, and good on you for spotting it and not just blindly copying commands into your computer.  However, all the warning is saying is that upon certain updates to the UDev system that file will be overwritten, so you'll loose those edits.

It is safe to edit that file as described.  If you'd rather not, you can place the same rules into a file in /etc/udev/rules.d/ that begins with any number greater than 50 (the udev docs suggest 60 or 70) and this will override the rules already in the /lib/udev/rules.d/ folder.  That file will always stay on your system, and won't get overwritten - most people call it 60-raw1394.rules but I think the name can be anything.  I have seen mixed results with this method though, so it's up to you.

I hope that clarifies things.  Did it?

---

### Post by mypetjaws on 2009-09-03
Yes. It clarified things perfectly. Thanks very much stochastic and trulan

---

