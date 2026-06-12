---
title: "HOWTO: Apple Wireless Keyboard (Bluetooth)"
date: 2006-07-28
forum: Tutorials
---

### Post by naag on 2006-07-28
[B][COLOR="Red"][SIZE="5"]This guide was previously written for Ubuntu 6.06. However, these instructions have been updated to work on Ubuntu 7.04 (Feisty Fawn).[/SIZE]

Changes made:
Replaced "hidd --search" by "hidd --connect BD_ADDR"
Replaced "/etc/init.d/bluez-utils" by "/etc/init.d/bluetooth"
Added "HIDD_ENABLED=1"
Added package "bluetooth" and "bluez-gnome"
[/COLOR][/B]

Hello guys,

I lately had some trouble using my Apple Wireless Keyboard with Ubuntu 7.04 so I'd like to share my experiences with you. So this is a small guide on pairing your Apple Wireless Keyboard with your Bluetooth Dongle of choice. Okay, so let's get started.

First of all, install the package bluez-gnome:

```

user@ubuntu:~$ sudo apt-get install bluetooth bluez-gnome

```

Restart your desktop session by logging out and logging in again. This will automatically start the bluetooth applet which will help you enter the PIN during the bluetooth pairing process.

Now we need to find out the Bluetooth Hardware Device Address (BD_ADDR) of our Apple Keyboard. Unfortunately, this is not written anywhere on the keyboard itself. So we need to turn on the keyboard (or restart it) using the switch on the bottom and run the following command:

```

user@ubuntu:~$ hcitool scan
Scanning ...
        BD_ADDR       Apple Wireless Keyboard
user@ubuntu:~$

```

Okay, there we got the BD_ADDR and the name of our device.

[COLOR="Red"]This seems to be the crucial piece of the bluetooth puzzle![/COLOR]

Now copy that BD_ADDR to your clipboard and edit the file /etc/bluetooth/hcid.conf to enable authentication and encryption for this very BD_ADDR.

```

user@ubuntu:~$ sudo gedit /etc/bluetooth/hcid.conf

```

Enter the following stanza at the end of the file, replacing BD_ADDR with your BD_ADDR from the clipboard:

```

device BD_ADDR {
    name "Apple Wireless Keyboard";
    auth enable;
    encrypt enable;
}

```

When you're finished, save the file and close gedit.

We're now going to enable HID-support by default:

```

user@ubuntu:~$ sudo gedit /etc/default/bluetooth

```

Change "HIDD_ENABLED=1" to "HIDD_ENABLED=0". Take care that using this how-to you do not need any "--connect BD_ADDR" parameters to hidd. So you can remove them from HIDD_OPTIONS. "HIDD_OPTIONS='--master --server'" is just fine.

Save the file, close gedit and restart the Bluetooth subsystem using the following command:

```

user@ubuntu:~$ sudo /etc/init.d/bluetooth restart
 * Restarting Bluetooth services... [ ok ]

```

Notice that this will terminate any active bluetooth connections. However, reconnecting should not be a problem ;-)

Finally, we're ready to do the actual pairing. Restart the keyboard again using the switch on the bottom to make it discoverable. Do not hit any keys on your Apple Keyboard unless this tutorial says so. It might cause all sorts of strange trouble during the pairing procedure. Okay, so, right after restarting the keyboard, run the following command (replacing BD_ADDR by the actual address, of course :-) ):

```

user@ubuntu:~$ sudo hidd --connect BD_ADDR
user@ubuntu:~$

```

Ubuntu will now try to connect to the keyboard without showing any progress bar or other output. It will just sit there and wait. Okay, enter a PIN consisting of 4 digits and hit the enter key (both on your Apple Keyboard). Right after hitting enter, a notification window should pop up on your desktop asking you for the PIN you just entered. Enter it. "hidd" should finish without further outputs. You should now be set up.

I hope that this will be useful to some people out there. Feel free to correct me or ask questions :-)

---

### Post by glug101 on 2006-07-29
Thank you very much for this.  I have to tell you that I was slightly disappointed that my bluetooth keyboard didn't 'just work' after I updated to Dapper, but then I was really disappointed when following the same steps that got it working under Breezy didn't work.  While I don't remember the precise steps I took in Breezy, I do remember that they were way simpler than this.  

Anyhow, thanks again for the great howto.  This worked perfectly (after I had properly charged batteries in the keyboard).  Now all I have to do is find a bluetooth mouse that I can afford,  There must be a grand total of 3 mice that are bluetooth and are not made by Apple.  (Like the keyboards, hate the mice.)

---

### Post by nakko on 2006-08-18
I followed these instructions to the T, but if I turn my keyboard off, it is never automatically recognized again.

Every time I want to use it, I have to manually (and with another keyboard) type "sudo hidd --search".

What might I be doing wrong?

---

### Post by oswaldkelso on 2006-11-09
[/QUOTE]

Okay, now we're ready to do the actual pairing. Restart the keyboard again using the switch on the bottom. Do not hit any buttons on your Apple Keyboard unless this tutorial says so. It might cause all sorts of strange trouble during the pairing procedure. Okay, so, right after restarting the keyboard, execute the following command:

```

user@ubuntu:~$ sudo hidd --search
Searching ...
        Connecting to device BD_ADDR
user@ubuntu:~$

```

As soon as it prints out "Connecting to device BD_ADDR", you should enter a PIN consisting of 4 digits and hit the Return key (on your Apple Keyboard). Right after hitting Return, a window should pop up on your computer asking you for the PIN you just entered. Enter it. You should now be set up.

I hope that this will be useful to some people out there. Feel free to correct me or ask questions :-)[/QUOTE]

works thus far the I get

 "Searching ...
        Connecting to device 00:0A:95:3F:75:17
Can't get device information: File descriptor in bad state"

Any help received with thanks. It would really be nice if we could make a sticky out of this as I like many I suspect are using cheapo usb keyboards,mice and headsets with our good gear sat in a cupboard.

I think there is a bluez file that stores the code for your seperate bluetooth devices. I seem to remember editing it a while back for my phone or headset but I knew the codes to enter.

---

### Post by skindog on 2006-12-20
What a great howto - it worked flawlessly the first time! Thanks so much for the info. 

However, similar to nakko above, I'm struggling to understand how to make the pairing automatic in the case of either the keyboard or computer falling asleep or restarting. Is it simply a matter of putting the "hidd --search" command in a startup script somewhere?

Any help is much appreciated.

---

### Post by morphet on 2006-12-31
Or you can just uninstall bluez-utils. It worked like an instant charm for me. System -> Administration -> Synaptic Package Manager.

Search for bluez, uncheck (check for removal) bluez-utils. Apply. :o

---

### Post by skindog on 2006-12-31
As it turns out, I found the information I needed here: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) Now my Apple Wireless Keyboard will work after reboot, and also wake the machine up from sleep. Brilliant! Now if I could just figure out how to get the Apple Wireless Mighty Mouse input to be interpreted properly...

---

### Post by zalberico on 2007-01-30
Thanks morphet!
Removing the bluez utils mad both the keyboard and mouse pair instantaneously
What an easy fix!

zman

---

### Post by Graybeard on 2007-01-30
This thread gives me hope. I don't have a bluetooth keyboard but I've been hoping that there's a way to get my usb rf keyboard/mouse to work on Ubuntu.  (It works fine on a windows box and I like it.) The Ubuntu box recognizes it as shown by the following info in the Device Manager:

Device Manager "Advanced" tab gives the following:

button.has_state	Bool	false
button.type		strlist	
info.addons		list	hald-addon-keyboard
info.capabilities	list	input, input.keyboard, button
info.category		strlist	input
info.parent		strlist	/org/freedesktop/Hal/devices/usb_device_195d_7777_noserial_if1
info.product		strlist	Itron Powerful Receiver
info.udi		strlist	/org/freedesktop/Hal/devices/usb_device_195d_7777_noserial_if1_logical_input
input.device		strlist	/dev/input/event3
input.physical_device	strlist	/org/freedesktop/Hal/devices/usb_device_195d_7777_noserial_if1
input.product		strlist	Itron Powerful Receiver
linux.device_file	strlist	/dev/input/event3
linux.hotplug_type	int	2(0x2)
linux.subsystem	strlist	input
linux.sysfs_path	strlist	/sys/class/input/input3/event3

Any suggestions???????

---

### Post by Bealer on 2007-03-06
Arghh, this guide used to work for me.

Now when I follow the above steps, upon running "sudo hidd --search", it says it's connecting to the device. 

I then input my PIN, but just get 

Searching ...
        Connecting to device 00:0B:94:42:39:66
Can't get device information: Permission denied


Any ideas???

---

### Post by jrsoft on 2007-03-31
Why do I get the following response from search

jack@jack-desktop:~$ sudo hidd --search
Searching ...
        Connecting to device 00:0A:95:3B:56:75
HID create error 14 (Bad address)

With bluez-utills installed I get this type of response from both my Apple Wireless Keyboard and Wireless Mighty Mouse. If I de-install it the keyboard is visable from boot. I want both mouse and keyboard. I have not been able tomake that work. All I can get is keyboard but only without using bluez-utils. This is with the 6.10 DVD installed.

Any ideas of what I can try? I have been reading posts for weeks and found nothing that works. My system is a Dual 2Gz G5 Power Mac.

---

### Post by naag on 2007-04-02
Finally I got time to comment on your replies:

[LIST=1]
[*]Some people had trouble getting automatic reconnect to work. In my first version of this howto, I forgot to tell you to enable HID-support by default. I edited my howto in this regard. Check the updated version! Hopefully this solves these tedious reconnect problems.

[*]Someone suggested removing the package "bluez-utils". Since this package provides the very basic linux bluetooth support, it didn't make any sense to me at first. Without bluez-utils, nothing should work at all!

I just realized that anyone who had success removing "bluez-utils" might not actually be using a standard bluetooth dongle, but some kind of HID-proxy bluetooth device (don't know how you call it actually). I also used to have such a device as it came with my Logitech MX900 mouse. This device connects to the PC via USB and acts as a standard USB mouse. In this case, the mouse is not paired directly with the PC, but with this proxy base station.

Try running "hcitool dev" (from "bluez-utils") to determine if you have a real bluetooth dongle or just some kind of proxy device. This command should output something like the following if you have a real bluetooth dongle:

```

user@ubuntu:~$ hcitool dev
Devices:
        hci0    BD_ADDR
user@ubuntu:~$

```

The device list will be empty if you use a proxy device.

Maybe someone who had success removing "bluez-utils" can comment on this? :-)

[*]Someone had a problem getting "permission denied" errors. You might try resetting your bluetooth subsystem by removing /var/lib/bluetooth/*.

[COLOR="Red"][SIZE="4"]**Warning: this will remove all bluetooth pairings!**[/SIZE][/COLOR]

```

user@ubuntu:~$ sudo rm -rf /var/lib/bluetooth/*

```

You should now follow the howto from the beginning to see if you're lucky this time...

[/LIST]

Have some luck!

---

### Post by Bealer on 2007-04-26
Hmmm, I tried what you said (resetting the bluetooth subsystem) but it didn't work.

I've actually just freshly installed Feisty, and it doesn't work. I still get the "Can't get device information: Permission denied" message when trying to connect to the device (the final step). 

Any ideas what it could be? Is it the keyboard, maybe my dongle (it's a D-Link DBT-120). It all worked before in Edgy, then for some reason has stopped working and won't let me access the device.

---

### Post by Bealer on 2007-04-27
Ok weird. It's working now.

I moved the dongle about and rebooted a few times. It's currently back in the usb port it was in before. Now though, the Bluetooth Manager is showing along the task bar. When I connected and entered a pin, a popup message appeared from it, and I was able to pair the keyboard.

Any idea why the Bluetooth Manager wasn't properly showing? Ah well, not exactly a solution but it seems to have worked.

---

### Post by oswaldkelso on 2007-05-02
Is anyone here dual booting? If so are you choosing your os via the alt/option key or via X L C. I would like to use the latter as it auto boots linux but beggers cant be choosers.

---

### Post by rdn2fst on 2007-05-30
i am having a slightly similar problem that may fall under the category of this post.  I am attempting to pair my motorola v3xx RAZR to my Fiesty Fawn in high hopes of using it as an internet connection.

i know that i can use the phone as an internet connection because i have zero problems doing that now with a USB cable.  while the USB cable has its perks, it's still a cable and i like to be free and unbounded at times, which is why i am so set on getting this Bluetooth connection (pairing) to work.

[list]
[*]i can scan for devices and receive the 'bdaddr' or what looks to be a MAC address and the name of my phone.  ```
hachenbeak@Warsteiner:~$ hcitool scan
Scanning ...
        00:1B:52:CF:D8:5E       Aaron's Phone
```
[*]when i enter ```
hachenbeak@Warsteiner:~$ hidd --connect 00:1B:52:CF:D8:5E
``` the blue light flashes on my phone for a moment and then i receive ```
Can't get device information: Success
```
[*]My /etc/bluetooth/hcid.conf looks like:
```

root@Warsteiner:/home/hachenbeak# more /etc/bluetooth/hcid.conf 
#
# HCI daemon configuration file.
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security auto;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # Default PIN code for incoming connections
        passkey "1234";
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        class 0x3e0100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;
        discovto 0;

        # Default link mode
        #   none   - no specific policy 
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;
}
device 00:1B:52:CF:D8:5E {
    name "Aaron's Phone";
    auth enable;
    encrypt enable;
}
root@Warsteiner:/home/hachenbeak# 

```
[/list]

help!  :)

---

### Post by calinb on 2007-06-03
> Some people had trouble getting automatic reconnect to work. In my first version of this howto, I forgot to tell you to enable HID-support by default. I edited my howto in this regard. Check the updated version! Hopefully this solves these tedious reconnect problems..

Okay, but I think you got it backwards.

> Change "HIDD_ENABLED=1" to "HIDD_ENABLED=0". Take care that using this how-to you do not need any "--connect BD_ADDR" parameters to hidd. So you can remove them from HIDD_OPTIONS. "HIDD_OPTIONS='--master --server'" is just fine.

My Bluetooth connections were not sticky after reboot until I set

HIDD_ENABLED=1

Still couldn't have made it work without ya',  naag!  

Thanks,

-Cal

---

### Post by .bashrc on 2007-07-24
Hey, thanks for the great guide. It worked pretty much "as advertised," however I was never asked for a pin ... strange. Does that mean whatever I'm typing someone else might be viewing? 

So ... is there any safeguard for the security of this?

Oh, and one other thing. I noticed that the number pad of my Apple Keyboard doesn't seem to be working. Any hints?

Thanks,
bash

---

### Post by twocargar on 2007-08-26
Thanks for the info.  I used this to pair my Apple Bluetooth Keyboard & Mouse!

---

### Post by Doctor J. on 2007-09-09
> **zman14321 said:**
> Thanks morphet!
Removing the bluez utils mad both the keyboard and mouse pair instantaneously
What an easy fix!

zman

Same here [mouse anyway, i don't have a bluetooth keyboard].  I makes me wonder why it was even part of the installation when the system works better without it.

---

### Post by olliecampbell on 2007-09-18
Great instructions. Worked first time for me,  although I never had to use a PIN it just worked....

---

### Post by olliecampbell on 2007-09-20
Worked great for me and now that ive set HID_Enabled=1 it works after a reboot too!

---

### Post by lhommemagique on 2007-09-24
I am having trouble getting this to work. Everything looks like it is working fine. It pairs and everything. Well at least I think it  does, it askes me for the pin I entered on my apple keyboard, and after I put it in it says something like bonding created with Jacob's keyboard. 

[IMG]http://www.personal.ecu.edu/jdp0814/applekey.png[/IMG]

But then instead of hidd finishing out without saying anything it always says  
> 
Can't get device information: Connection timed out
if I run
> sudo rm -rf /var/lib/bluetooth/*

I can pair it again but it always the same.

---

### Post by toasterofirony on 2007-09-27
I'm trying to follow this guide to get my Apple BT keyboard to pair to my Gutsy box, but it won't play ball.

If I try doing it through the system tray utility, it tell me that the BT address "isn't valid" (even though it can see it and identify it happily enough). And if I try and use the guide, I get told, at the final step,  "Connecting to device **:**:**:**:**:** Can't get device information: Function not implemented"

Now I know the keyboard works fine and I can get my 'phone to connect to my computer with this set-up, so I'm guessing I'm doing something wrong, or gutsy is just demonstrating one of its *hilarious* bugs. Any ideas?

---

### Post by toasterofirony on 2007-10-02
Ah ha! I've figured it out.

When you type the --connect command, straight after THAT is when you type the PIN of your choice on the BT keyboard. Then click on the pop-up that appears on your sys-tray and repeat with the keyboard that is plugged.

So, in retrospect, the guide works perfectly. So does Gutsy. And I am a bit of a spaz.

Hurrah! Business as usual.

---

### Post by lhommemagique on 2007-10-02
bump

---

### Post by eric2701 on 2007-10-08
Has anyone gotten this to work with the new wireless keyboard (the aluminum one)? 

 I got the old one working, But with the new one I'm getting a connection timed out error or connection refused error.

---

### Post by LESLIEx317537 on 2007-10-08
> **eric2701 said:**
> Has anyone gotten this to work with the new wireless keyboard (the aluminum one)? 

 I got the old one working, But with the new one I'm getting a connection timed out error or connection refused error.

Yes, today my apple store just got the keyboard in.
I just picked it up.

I installed Bluetooth Applet in System Package manager.  I'm running Fiesty.

I ran hcitool scan to get the mac address of my wireless mighty mouse and new aluminum keyboard.

The mouse was easy.  I slide the on off switch on the bottom on, and typed sudo hidd --connect (mac address) and while its connecting tap the mouse just to make sure and it should pop up a password popup and you click it and enter 0000.
It should say in the popup, bonding created etc......

The keyboard I kept trying and trying...but then I tried what someone mentioned above.  While trying to connect to the wireless keyboard, press 0 four times on the mac keyboard.  Only when I did that did a password popup like the mouse pop up, in which I entered 0000 as the passkey and it then the popup said created bonding with keyboard etc.....

I just typed this post using the keyboard.  But I know when I reboot, or something it might not be paired up.  I will enter some changes in the boot up files to change that and see what happens later.

---

### Post by ky13 on 2007-10-09
To XFCE Users:

You probably want to run gnome-panel to get this to work.  The pin popup will not happen unless you are running gnome-panel.  At least it didn't for me until I ran it.  Once you pair it once, you no longer need the panel.

---

### Post by matthew.lns1 on 2007-10-12
You have to do

```
 sudo hidd --connect BDADDR
```

---

### Post by LESLIEx317537 on 2007-10-13
They seem to connect at boot without editing some sort of startup file.

---

### Post by enzomedici on 2007-10-18
I have to say this is pretty hilarious. How am I supposed to type anything IF THERE IS NO FREAKIN' KEYBOARD TO TYPE WITH?

That is about as retarded as the same thread about how to get the airport wireless card working...just download this driver...blah blah. THERE IS NOT NETWORK CONNECTION SKIPPY!

Ubuntu 7.1 still doesn't recognize the wireless keyboard and mouse? Dude....it's the same old problems with Linux. I've been using Linux since Slackware 1.0 and it is always the same ****. Monitor doesn't work, only supports those crappy resolutions,  maybe the printer, how about the USB card? What about the EVDO card? Hmmm....let's see if I can get my wireless mouse and keyboard to work. Great now if only I could just get the RAID card recognized. SSDD.

I'm a technical guy, but it is always a battle just to get Linux up and running and doing basic tasks.

---

### Post by GingaNinja on 2007-11-01
I've been trying out Gutsy with the new Aluminium Wireless Keyboard.  It is working perfectly in terms of getting it recognised, and when I reboot it remembers the settings, so I can log in using the keyboard.

However, a couple of things that I would still like to sort out:

[LIST=1]
[*]when I reboot into windows xp (dual boot), it doesn't recognise the keyboard, and then I have to go through a pairing process with xp.  This works, but then when I restart back into ubuntu, even though the settings say ubuntu should always trust the keyboard connection, it has actually lost it, and I have to "untrust" the connection and delete it before I can reconnect by typing in a pin on the keyboard and pair it again.
[*]The fn key doesn't seem to work.  I've run xev to see what keycodes get pressed, and everything generates a keycode except the fn key.  I've also tried pressing combinations like fn + F4 for example, and this still generates the F4 keycode.  Because the keyboard doesn't have a delete key (just a backspace), the idea (I believe) is to press fn+backspace to get a delete key.  I'd like to allow some sort of remapping to enable this (and the media keys, home, end etc), but obviously can't do anything if the fn key isn't recognised in the first place.
[*] I've read something about HID proxy in this thread and in other posts, and about being able to update the firmware on bluetooth dongles that use a CSR chip in order to get HID proxy working.  This is meant to enable you to somehow pair the keyboard with the dongle, rather than the operating system.  I'm thinking this might solve problem 1, and also enable me to select operating systems, etc with the wireless keyboard.
[/LIST]

Anyone had any success with these questions?

---

### Post by Tristan Schmelcher on 2007-12-01
Question: will this procedure work even if the computer that Ubuntu is installed on is not a Mac? I am thinking of buying the (original) Apple wireless keyboard for my Dell because it is the only wireless keyboard that anyone makes a Dvorak cover for ([http://www.kbcovers.com/servlet/Detail?no=43](http://www.kbcovers.com/servlet/Detail?no=43)).

Thanks.

---

### Post by toasterofirony on 2007-12-01
Yup. Mine is a home-baked affair and it works fine :)

---

### Post by buddhaguy on 2007-12-14
Hi there,

I have been using the new aluminium apple bluetooth keyboard for a month now and its been brilliant. Feisty and pairing was not a problem and it comes on automatically when I start typing on boot up at the login prompt.

The main annoyance is its power saving mode! Although its great it saves batteries after a break it doesn't reconnect and I have to power it off by holding down the power button for 5 secs and then powering it on again. Its still seen as connected in the os.

Has anyone else encountered this. Any advice?
Cheers
G

---

### Post by Octagonal on 2008-01-12
Thank you for the excellent how-to.  Worked like a champ and still there after reboots.

---

### Post by stevenjoseph on 2008-01-26
hi, i got the sleek apple bt kbd working with kubuntu . everything was working fine until a recent upgrade then it started acting weird, it was not reconnecting ... cant seem to figure out what has changed ... does anyone have any ideas how to fix it ...?? 
Thanks
steve

---

### Post by stevenjoseph on 2008-01-29
FIXED: found the solution to keyboard not reconnecting 
remove the --master option from the hidd options in /etc/default/bluetooth 

:guitar:

Cheers

---

### Post by costre on 2008-02-02
I found the details in this thread helped me, check it out:
[http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)

I got my Microsoft bluetooth-keyboard and -mouse working, without trouble.

---

### Post by stevenjoseph on 2008-02-06
damn, its not working again ... broke after another upgrade, this time the previous fix is not working ... anyone experiencing the same problem.

:confused:

---

### Post by ScottKinkade on 2008-03-04
I have the new apple bluetooth keyboard (aluminum) and i am typing on it right now, so it's connected, but apparently the keyboard has an automatic sleep feature meaning it goes to sleep and thus, disconnects with my computer and therefore i have to go to teminal and type: sudo hidd --connect 00:1E:52:F8:63:40 every time i come back to my computer. This is quite an issue since i have to TYPE that in to connect the device i need to type it with... Is there some way to make it automatically connect? Or is there some way to make a little executable file that does that command for me??? I have Gutsy and I need some help...

---

### Post by xr2 on 2008-03-04
I'm trying to get this to work with the new slim keyboard I just picked up, but every time I try to use hid --connect xxx.. I get the following message:

Can't create HID control channel: Connection refused

I run the command from the terminal, hit 0000 <enter> on the apple keyboard, and then I get that message.  I get the impression that I supposed to see some form of pop up in which to enter the pin, but I see nothing of the sort.

---

### Post by click170 on 2008-03-08
Thanks!  This was exactly what I needed to get my Apple bluetooth keyboard to work!

Much appreciated.

---

### Post by stevenjoseph on 2008-03-15
finally got the keyboard working perfectly..... here is my hcid.conf  
--------------------------hcid.conf------------------------
options {
        autoinit yes;
        security auto;
        pairing multi;
        passkey "1234";
}
device {
        name "%h-%d";
        class 0x100100;
        iscan enable; pscan enable;
        discovto 0;
        lm accept;
        lp rswitch,hold,sniff,park;
}
device 00:1B:63:FB:2E:97 {
    name "Apple Wireless Keyboard";
    auth disable;
    encrypt disable;
}
-----------------------end--------------------------------
----------------------default/bluetooth------------
BLUETOOTH_ENABLED=1

HIDD_ENABLED=1
HIDD_OPTIONS="--master --server --connect 00:1B:63:FB:2E:97"
----------------------end----------------------------

---

### Post by Oliver_U on 2008-03-17
I've been trying things left and right for hours now, but always get stuck at the same place.

When I type in sudo hidd --connect XX:XX[...], it sits there waiting for the pin to be entered on the wireless keyboard. Whatever I enter, I get the error message: "Can't create HID control channel: Connection refused"

I've tried with and without --master, using auth/encrypt disable aswell as auth/encrypt enable. No deal.

I do see that others have the same problem, so any help would be appreciated by more people than just me.

Oh, it should also be noted that I can't get the bluetooth icon to show up in my systray, even when manually trying to make it always show up in bluetooth-properties. Nevertheless, I am able to do hidd --search and find the keyboard, so the bluetooth dongle works fine. It's just this last thing that is somehow botched up.

---

### Post by Chokkan on 2008-03-18
My dongle is never detected. I had to start bluetooth-applet from the command line. It would often crash saying out of memory but after a few tries it worked and I never have to start it again. My new keyboard and Microsoft mouse are detected every time now without fail at boot.

So in short, don't give up.

---

### Post by Oliver_U on 2008-03-18
That worked perfectly, big thanks! (typing this with my new keyboard) :D

---

### Post by Chokkan on 2008-03-19
Great :) It's a fantastic keyboard, isn't it? I even set up the eject button ;)

I'm using xfce so maybe that was why I had trouble with the applet.

---

### Post by xale on 2008-04-16
voilà, i'm a (un)happy owneer of a nice bluetooth alu keyoboard.

i've tried to use it with hardy (8.04) beta. well it kind of works, now.

i followed several howtos and several of them lead to no working keyboard...

however i've done the steps listed in here:

[https://help.ubuntu.com/community/MacBookPro#head-8f09010d78f375fd2a731ce6a70fef309975855d](https://help.ubuntu.com/community/MacBookPro#head-8f09010d78f375fd2a731ce6a70fef309975855d)

i don't know if the changes to the /etc files are necessary to bring it to work. i will try at the next clean install.


then i've found a bug report with a link to a fedora post

[http://ubuntuforums.org/showpost.php?p=3907738&postcount=22](http://ubuntuforums.org/showpost.php?p=3907738&postcount=22)

that fedora post ([http://forum.fedoraforum.org/showthread.php?p=908776](http://forum.fedoraforum.org/showthread.php?p=908776)) says:

>> Thats a bad UI case. Do NOT right-click -> Browse Device for input devices.

Right-click on the bluetooth applet and select "Preferences", go to the "Services" tab, left-click on "Input service", click the "Add" button, select your input device & connect. <<

that way i brought it work.


still, it doesn't work with the bios and grub (the first it ouf the reach of ubuntu, the second.. well... it could work...)

for gdm i haven't find a pattern yet: it doesn't work at a first (and second and co try) but if you press enough times (and maybe enough long ) on the power button of the keyboard, you will be able to enter you username and password with it!

voilà. and, then, it works well!

ciao
a.l.e

---

### Post by aztechclan on 2008-04-16
Hi,
I just got my bluetooth apple keyboard (the small kind) working.  At first I kept getting connection refused..  Follow the instructions, Install blueman, change /etc/default/bluetooth to HIDD_ENABLED=1..

Then, run blueman and pair with the keyboard by clicking 'bond', entering 0000<enter> on the wireless keyboard, which will then pop up the dialog to enter 0000 again locally.  After which you can run the --connect command and it will work.

This was on edgy.  Glad it's working yay!

---

### Post by 23meg on 2008-04-27
Do the arrow key combinations that emulate Home, End, Page Up and Page down work with this keyboard under Hardy?

---

### Post by midtoad on 2008-05-07
> **23meg said:**
> Do the arrow key combinations that emulate Home, End, Page Up and Page down work with this keyboard under Hardy?


Yes, they seem to work in Hardy if you use the arrow keys with the fn key.

---

### Post by ounas on 2008-05-12
> **skindog said:**
> As it turns out, I found the information I needed here: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) Now my Apple Wireless Keyboard will work after reboot, and also wake the machine up from sleep. Brilliant! Now if I could just figure out how to get the Apple Wireless Mighty Mouse input to be interpreted properly...

Thanks for that link, works perfectly now
:guitar:

---

### Post by click170 on 2008-05-25
So yeah... I posted here previously with thanks for help getting this to work... except for the bluetooth keyboard powersaving mode.

After awhile of inactivity, as at least one other person on this thread has noticed, the keyboard goes to sleep.  Now I believe normal functionality on a Mac is that the keyboard reconnects as soon as a key is pressed, and the Mac allows this because it uses the same time-out length for the bluetooth connection as the keyboard uses as a trigger to go to sleep after so long of inactivity.

Therefor, I believe the problem being experienced with the keyboard going to sleep and not automatically reconnecting to Ubuntu is because Ubuntu does not automatically disconnect the device after a period of inactivity, or at least the same period of inactivity.  I notice that even after the bluetooth keyboard has gone to sleep, the Bluetooth Manager Preferences window shows the device as still connected.  If one disconnects the device manually in this window, and then presses a key on the keyboard after doing so, the keyboard should reconnect and you can resume as normal.

At least this way people who rely only on the bluetooth keyboard and still have a corded mouse have a chance at getting the keyboard reconnected without the paradox of needing the keyboard to connect the keyboard.

I wonder if there is a way to script the bluetooth keyboard's automatic disconnection from the machine after X inactivity, or for that matter if there is a way to enable some kind of timeout in the bluetooth preferences themselves?

---

### Post by click170 on 2008-05-25
I found a pitiful workaround which may still be of use to those without another keyboard or mouse to fall back on.

by running the command

'hcitool dc X'

where X is the mac address of the bluetooth keyboard, you can tell the computer to disconnect from the keyboard.  If they keyboard is asleep, then after you do this, you can press any key and the keyboard should wake up and reconnect.

The nasty work around would be to script the command to run every X period of time.  It would be nasty as it would auto-disconnect the keyboard at each interval, but it will work for leaving the machine for some time and then coming back and having a working keyboard.  

Still working on a way to detect when the keyboard is idle.

---

### Post by Urinemachine on 2008-05-25
Sorry to bump this thread

I have a *wired* mac keyboard and its great, except for the fact that the command key on the keyboard I want to be the ALT key, but its the Super key, and the alt/option keyboard functions as the ALT key, and I want it to be the Super key - any idea on how to flip flop the functionality of these two keys?

---

### Post by click170 on 2008-05-25
> **Urinemachine said:**
> Sorry to bump this thread

I have a *wired* mac keyboard and its great, except for the fact that the command key on the keyboard I want to be the ALT key, but its the Super key, and the alt/option keyboard functions as the ALT key, and I want it to be the Super key - any idea on how to flip flop the functionality of these two keys?

System > Preferences > Keyboard Shortcuts ?

---

### Post by stevenjoseph on 2008-05-29
Hi right from the start there has been problems with the keyboard reconnecting after a period timeout. I seem to have stumbled upon a way to do this ... but it may not be the best practice ... anyways .. i found that the hidd was not running as a daemon as it was supposed to after a little mucking around this seems to work 

chmod +s `which hidd`

i havent experienced much problems after this ... some i feel this is not the best solution because u r setting it to suid, :confused: but it works for me ... 

also in here is the configuration in /etc/default/bluetooth

HIDD_OPTIONS=" -t 1000 --server --connect=XX:XX:XX:XX:XX:XX"

---

### Post by incubus on 2008-06-01
I got the same problem.  Here's what I found:

[https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/175743](https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/175743)

Right now I'm patching bluez-utils to see if it works.  Disabling time out doesn't seem to be the best idea in the world, however.

---

### Post by kobayashimaru on 2008-06-02
About the powersaving issue: Add the option "lm master;" to the device section of your keyboard in the /etc/bluetooth/hcid.conf. So it should look like this:

device YOUR_MAC {
	name "Apple Wireless Keyboard";
	auth enable;
	encrypt enable;
	lm master;
}

With this option, the keyboard will be detected by the system, if it wakes up from sleep.

---

### Post by matthewcraig on 2008-06-15
> **xr2 said:**
> I'm trying to get this to work with the new slim keyboard I just picked up, but every time I try to use hid --connect xxx.. I get the following message:

Can't create HID control channel: Connection refused

I run the command from the terminal, hit 0000 <enter> on the apple keyboard, and then I get that message.  I get the impression that I supposed to see some form of pop up in which to enter the pin, but I see nothing of the sort.


xr2 - I am having exactly the same problem.  Is there supposed to be a pop-up with GNOME or something?  I posted my efforts [here]("http://ubuntuforums.org/showthread.php?t=830383").  Let me know if you ever get this resolved.  I have been working on this for four hours with no resolution.  (Got it to work on my Linux tablet running Maemo in 5 minutes!)

... ... ... ...
... (UPDATED) ...  I have it fixed.  One MUST have "bluetooth-applet" running, in order to enter the pairing code on the desktop, otherwise, the "hidd --connect" command will immediately fail when the code is entered on the keyboard.

I am not sure why "bluetooth-applet" was not configured to run at login, but I do hope these error messages improve for this problem.

---

### Post by stevenjoseph on 2008-06-18
[This]("http://stevenjoseph.blogspot.com/2008/05/howto-apple-wireless-keyboard-bluetooth.html") works for me perfectly ... the keyboard reconnects also

---

### Post by matthewcraig on 2008-06-26
Anyway to get Page Up / Page Down functions working?  Suppose there is always key remapping, but would be nice if done by default.

---

### Post by Ches Martin on 2008-08-08
> **matthewcraig said:**
> Anyway to get Page Up / Page Down functions working?  Suppose there is always key remapping, but would be nice if done by default.

Hey Matthew,

Page up/down functions work just fine for me with no extra setup, just use the fn key+up/down arrows like on a Mac.

Other function key stuff works too, like the volume control and mute buttons. This is all with kubuntu and kbluetoothd, but I'd imagine that at least the page up/down should work in any X environment, though maybe not.


Thanks to naag for the original article, and others in this thread for contributions. With a little fiddling it's all been working smoothly for me in Hardy. Keyboard sleeps for battery saving, reactivates, works after a system restart, etc.

I added 'lm master;' to the device section of hcid.conf as suggested above, and in /etc/default/bluetooth I simply have 'HIDD_OPTIONS="--server"' -- no master or anything else. The keyboard was working for awhile after reboots, but then stopped for some reason. Adding 'hidp' to /etc/modules as suggested in [BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup") seems to have fixed it for good.

---

### Post by aranad on 2008-08-20
I spent quite some time going through these various forums to find a solution to my new Apple wireless keyboard not working, but the solution turned out to be simple!

I'm on Ubuntu Hardy and the device would come up in the list fine but it wouldn't connect. Sometimes I've noticed I have to use hidd --connect xx:xx:xx:xx from a root prompt to get things to connect, but in the case of the Apple keyboard it would just time out.

I then found (by reading the instruction manual!) that you must set a 4 digit pin number before it will connect and bond properly. To do this, turn it on, run the connect command and then type the PIN into the Apple keyboard followed by Enter. This should then bring up a dialogue box allowing you to confirm the code (with the existing functional keyboard). The connection should then be made and the keyboard will be present automatically after reboot or keyboard on/off.

---

### Post by orion603 on 2008-08-20
It works for me and don't really have any problem reconnecting the keyboard after reboot, lock, and etc with some key strokes to wake it up and bond it with the computer. However, the keyboard is lagging after the keyboard is turned off and re-connect. Does anybody else have the same problem?

It sometimes, skips what I typed or prints same key twice and so on.

---

### Post by gamajeal on 2008-10-07
> **morphet said:**
> Or you can just uninstall bluez-utils. It worked like an instant charm for me. System -> Administration -> Synaptic Package Manager.

Search for bluez, uncheck (check for removal) bluez-utils. Apply. :o

Thanks man this worked like a charm :lolflag:

---

### Post by driven1 on 2008-10-18
After running the ```
sudo hidd --connect [MAC ADD]
``` and entering the pass key, I get the following message

```
Can't create HID control channel: Connection refused
```

Please tell me where I went wrong

---

### Post by olavjunior on 2008-10-19
The bluetooth keyboard connects perfectly in Intrepid, no fuzz at all. But fn doesn@t do anything! So no fn up/down, neigther volume-control ect. (And as you can see I@m missing the `)

---

### Post by driven1 on 2008-10-21
Found a typo in my hicd.config. once that was cleared up, keyboard recognized and working, but not fully tested.

---

### Post by light0 on 2008-10-30
For all those desperately trying to get their Apple Wireless Keyboard to work:

I spent hours trawling the internet and stumbled upon this forum. I don't think there is enough information on it to get a fully working setup and to save people a lot of time trying out different things, I thought I'd offer my (FULLY) working solution. I am using a DBT-122 dongle (I wish I'd bought the DBT-120 because that contains a superior CSR chipset and also has the advantage of you being able to install apple's firmware so that the keyboard gets presented as a USB keyboard). 

The bluetooth support seems a little buggy under Hardy Heron. I experienced quite a few hard crashes whilst I was getting it to work, but this is under specific situations and I don't get them now. 

By fully working I mean working after reboot, switching keyboard on and off or keyboard going to sleep. 

Files:

**/etc/init.d/bluetooth**

Insert this BEFORE exit 0 at the end of the script:

```

sleep 1 && /usr/sbin/hciconfig hci0 reset
sleep 1 && /usr/sbin/hciconfig hci0 reset

```

This is necessary because in some dongles like mine, the keyboard will try and connect upon reboot but you get messages about ACL packets etc. I personally found that adding hciconfig eth0 down && hcicofig eth0 up as suggested didn't work. This put my hci0 in a bad state and I got timeout errors and weird effects. 

The next file **/etc/default/bluetooth**

```

HIDD_ENABLED=1
HIDD_OPTIONS="-timeout 8 --master --server --connect 00:0A:95:46:E9:9F"

```

Obviously replace 00:0A:95:46:E9:9F with your keyboard's address. You can usually run sudo hcitool inq or look inside /var/lib/bluetooth/XX:XX:XX:XX:XX:XX/lastseen. The timeout is supposed to prevent the keyboard from going to sleep and associated problems. 

Next file **/etc/bluetooth/hcid.conf**

```

      lm master;
      lp rswitch,hold,sniff,park;

}

device 00:0A:95:46:E9:9F {
name "Apple Wireless Keyboard";
auth enable;
encrypt enable;
}

```

Again, replace address with yours. 

**$hcitool con**

```

Connections:
        > ACL 00:0A:95:46:E9:9F handle 6 state 1 lm MASTER AUTH ENCRYPT

```

**$hciconfig -a **

```

hci0:   Type: USB
        BD Address: 00:15:E9:7B:B7:EB ACL MTU: 377:10 SCO MTU: 16:0
        UP RUNNING PSCAN ISCAN
        RX bytes:107268 acl:5419 sco:0 events:102 errors:0
        TX bytes:1308 acl:8 sco:0 commands:87 errors:0
        Features: 0xff 0xfe 0x0d 0x38 0x08 0x08 0x00 0x00
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: MASTER
        Name: 'kubuntu-0'
        Class: 0x180100
        Service Classes: Capturing, Object Transfer
        Device Class: Computer, Uncategorized
        HCI Ver: 1.2 (0x2) HCI Rev: 0x2788 LMP Ver: 1.2 (0x2) LMP Subver: 0x309
        Manufacturer: Broadcom Corporation (15)

```


Good luck. I spent hours upon hours to get this working instead of studying as I should have been. Please take the time to post and say if this has fixed your problems (it would make me think the 20 mins typing this up was worthwhile). If you have problems try:

**$sudo rm -rf /var/lib/bluetooth/***

Sometimes bad info can get retained there it seems. 

If you want to see all my config files I've uploaded them here:

[http://www.srcf.ucam.org/~aes52/bluetooth/]("http://www.srcf.ucam.org/~aes52/bluetooth/")

---

### Post by eindgebruiker on 2008-11-06
> **light0 said:**
> I spent hours trawling the internet and stumbled upon this forum. I don't think there is enough information on it to get a fully working setup and to save people a lot of time trying out different things, I thought I'd offer my (FULLY) working solution. I am using a DBT-122 dongle (I wish I'd bought the DBT-120 because that contains a superior CSR chipset and also has the advantage of you being able to install apple's firmware so that the keyboard gets presented as a USB keyboard). 

Unfortunately the DBT-120 is not available in Europe.

Do you know if the DBT-122 works with *both* the Apple wireless keyboard and wireless mouse *at the same time*? Or do you know of any other bluetooth dongle that does the job?

I tried with several bluetooth dongles with different CSR chipsets, but so far had no luck. Either they do not work at all, or they work with either the keyboard or the mouse but not both.

---

### Post by dharanpdeepak on 2008-12-25
[http://nextdoornerd.blogspot.com/2008/08/ubuntu-setup-your-bluetooth-keyboard.html](http://nextdoornerd.blogspot.com/2008/08/ubuntu-setup-your-bluetooth-keyboard.html)

check this link for a relatively simple how to on setting up your apple bluetooth keyboard...

---

### Post by vickoxy on 2009-03-13
Hi,
i described my problem here:
[http://ubuntuforums.org/showthread.php?t=1094309](http://ubuntuforums.org/showthread.php?t=1094309)

but i will repeat it here. So, on my dell mini 9 i installed full version (non dell) of ubuntu 8.04. Followed instructions here how to pair bluetooth devices, but there is one problem:
Apple Wireless Keyboard and Bluetooth Mice are working if i shut down computer, and then turn it on.
BUT, if i restart/reboot it -then it doesn´t work. So, hoping to hear some suggestions...

On dell mini 9 Ubuntu (dell lpia version) keyboard and mice were workin after restart too-didn´t need to shut down computer every time.

Hope someone will tell me that is minor bug and how to fix it....
Regards

---

### Post by vickoxy on 2009-03-14
UPDATE:
i reinstalled original dell mini 9 Ubuntu 8.04, and i noticed that you don´t need to do any extra job to pair you apple wireless keyboard. But you have to carefully pair it with your dell:
1) right click on bluetooth icon-choose "setup" or "settings" (i use german so i don´t know exact order´s names)
2) go to middle tab and press once or twice input device/eingabedienst (see picture 1)-there should open "add" field
3) make sure that your apple keyboard is visable, and add it to your devices

Then keyboard will try to pai with computer AND NOW:

4) TYPE four digits (eg 1111) and ENTER on your Apple Keyboard
5) then will pop up another message in your bluetooth applet-type again on your netbook /dell mini keyboard 1111 and enter/ok

And the keyboard should work. After restart, reboot, hibernation...
No need to go to Terminal, or change some .conf files...
Of course, i don´t know hot to set up FN keys, but for regular typing is keyboard fully operational....

---

### Post by fouriergr on 2009-03-24
I have a mocbook 3.1 santa roza and an apple bluetooth keyboard (the first generation not the aluminum one)

The problem and the rationel:
I have a triple boot setup and i use rEFIt as the boot loader.
I noticed that both rEFIt and grub where aware of my wireless keyboard and so was ubuntu during the boot process but once gdm came up the keyboard became iresponcive and i had to open a terminal and type from an other keyboard  hidd --search aa:bb:cc:dd:ee
in order to get it to work.
I realised that apple has some firmware that emulates some sort of USB emulation.

The solution:
1)I paired the keyboard in leopard
2)I disabled the bluetooth service totaly in ubuntu. (i dont realy need it for anything else)
It just works as a wired keyboard would
Disabling all bluetooth services should be a good solution for anybody 
who has his keyboard working in the bootloader and doesnt care about connecting other devices.



My configuration
Macbook 3.1
Apple wireles keyboard(first generation)
Leopard 10.5.6
Ubuntu 9.04 Jaunty Jackalope
rEFIt

---

### Post by Bealer on 2009-03-26
Excellent guide and updates. Many thanks. Mine all works perfectly now. Just it seems to eat up batteries faster than normal.

---

### Post by tyce on 2009-11-06
has anybody got this working in 9.10?  It was working flawlessly until I upgraded and now 24 hours later it's still not functioning right. 

Any help greatly appreciated.

---

### Post by torstein on 2009-11-16
I managed to get the apple wireless keyboard up and running in Ubuntu 9.10 after much work. I'm not really sure what fixed it but I think this was it.

- installed "blueman"
- used blueman to bond (right click) the keyboard, entering 1234 in the box and typing 1234+return/enter on the keyboard.
- right-clicked on the keyboard in blueman and selected "trust" and "connect input service"


it finally works, but I'm not yet sure if it will after a reboot :)

update: works nicely after reboot and suspend :)

---

### Post by bobbertrailer on 2009-11-17
> **torstein said:**
> I managed to get the apple wireless keyboard up and running in Ubuntu 9.10 after much work. I'm not really sure what fixed it but I think this was it.

- installed "blueman"
- used blueman to bond (right click) the keyboard, entering 1234 in the box and typing 1234+return/enter on the keyboard.
- right-clicked on the keyboard in blueman and selected "trust"


it finally works, but I'm not yet sure if it will after a reboot :)

Thank you for this post.

It  works for me !

---

### Post by alwyn.schoeman on 2009-12-03
Did you do anything special to have it work on reboot?  I must always run /usr/init.d/bluetooth start or my bluetooth fails.

---

### Post by pfeoora on 2009-12-09
Doesn't work for me at all. Do I have to do something else before installing blueman? I'd really love to be able to use Karmic on my Mac without having to use my old and clunky USB Keyboard. Why do theUbuntu developers always have to "make things better" even though they worked just fine before. Same thing with Pidgin (Empathy is a pain and ugly as f**k) but that's another story.

---

### Post by Gemba on 2009-12-24
> **light0 said:**
> For all those desperately trying to get their Apple Wireless Keyboard to work:

I spent hours trawling the internet and stumbled upon this forum. I don't think there is enough information on it to get a fully working setup and to save people a lot of time trying out different things, I thought I'd offer my (FULLY) working solution. I am using a DBT-122 dongle (I wish I'd bought the DBT-120 because that contains a superior CSR chipset and also has the advantage of you being able to install apple's firmware so that the keyboard gets presented as a USB keyboard). 

The bluetooth support seems a little buggy under Hardy Heron. I experienced quite a few hard crashes whilst I was getting it to work, but this is under specific situations and I don't get them now. 

By fully working I mean working after reboot, switching keyboard on and off or keyboard going to sleep. 

Files:

**/etc/init.d/bluetooth**

Insert this BEFORE exit 0 at the end of the script:

```

sleep 1 && /usr/sbin/hciconfig hci0 reset
sleep 1 && /usr/sbin/hciconfig hci0 reset

```

This is necessary because in some dongles like mine, the keyboard will try and connect upon reboot but you get messages about ACL packets etc. I personally found that adding hciconfig eth0 down && hcicofig eth0 up as suggested didn't work. This put my hci0 in a bad state and I got timeout errors and weird effects. 

The next file **/etc/default/bluetooth**

```

HIDD_ENABLED=1
HIDD_OPTIONS="-timeout 8 --master --server --connect 00:0A:95:46:E9:9F"

```

Obviously replace 00:0A:95:46:E9:9F with your keyboard's address. You can usually run sudo hcitool inq or look inside /var/lib/bluetooth/XX:XX:XX:XX:XX:XX/lastseen. The timeout is supposed to prevent the keyboard from going to sleep and associated problems. 

Next file **/etc/bluetooth/hcid.conf**

```

      lm master;
      lp rswitch,hold,sniff,park;

}

device 00:0A:95:46:E9:9F {
name "Apple Wireless Keyboard";
auth enable;
encrypt enable;
}

```

Again, replace address with yours. 

**$hcitool con**

```

Connections:
        > ACL 00:0A:95:46:E9:9F handle 6 state 1 lm MASTER AUTH ENCRYPT

```

**$hciconfig -a **

```

hci0:   Type: USB
        BD Address: 00:15:E9:7B:B7:EB ACL MTU: 377:10 SCO MTU: 16:0
        UP RUNNING PSCAN ISCAN
        RX bytes:107268 acl:5419 sco:0 events:102 errors:0
        TX bytes:1308 acl:8 sco:0 commands:87 errors:0
        Features: 0xff 0xfe 0x0d 0x38 0x08 0x08 0x00 0x00
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: MASTER
        Name: 'kubuntu-0'
        Class: 0x180100
        Service Classes: Capturing, Object Transfer
        Device Class: Computer, Uncategorized
        HCI Ver: 1.2 (0x2) HCI Rev: 0x2788 LMP Ver: 1.2 (0x2) LMP Subver: 0x309
        Manufacturer: Broadcom Corporation (15)

```


Good luck. I spent hours upon hours to get this working instead of studying as I should have been. Please take the time to post and say if this has fixed your problems (it would make me think the 20 mins typing this up was worthwhile). If you have problems try:

**$sudo rm -rf /var/lib/bluetooth/***

Sometimes bad info can get retained there it seems. 

If you want to see all my config files I've uploaded them here:

[http://www.srcf.ucam.org/~aes52/bluetooth/]("http://www.srcf.ucam.org/~aes52/bluetooth/")


Thanks Light0, I followed your instructions exactly as you posted them and a testament to your knowledge I'm thanking you from my shiny new bluetooth keyboard which is working very nicely in Karmic Koala. :)

---

### Post by davidmaxwaterman on 2010-01-31
I don't think anyone here has mentioned [this]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/434007?comments=all") bug; specifically comment # 16 :

> To solve this I put "hid_apple" in my /etc/modules.conf

For me, this solves the issue where I have to power cycle my keyboard in order to type my password on the login screen.

Unfortunately, I still have to power cycle it again after I log in since it seems to think my keyboard is in 'number' mode. By 'number' mode, I mean this :

The Apple keyboard I have is basically like a laptop one - ie it has no number keypad. Well, often, such keyboards have the numbers on the letter keys and are accessed using some meta key or other. My Apple keyboard doesn't have them labeled like this but perhaps this is just because they like to keep it simple. However, after I log in, it seems my keyboard is in this number mode - ie no keys work apart from these 'numbers' which are on the right hand side of the letter rows.

Anyone seen this and have an idea how to fix it properly?

---

### Post by vickoxy on 2010-02-16
> **davidmaxwaterman said:**
> I don't think anyone here has mentioned [this]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/434007?comments=all") bug; specifically comment # 16 :



For me, this solves the issue where I have to power cycle my keyboard in order to type my password on the login screen.

Unfortunately, I still have to power cycle it again after I log in since it seems to think my keyboard is in 'number' mode. By 'number' mode, I mean this :

The Apple keyboard I have is basically like a laptop one - ie it has no number keypad. Well, often, such keyboards have the numbers on the letter keys and are accessed using some meta key or other. My Apple keyboard doesn't have them labeled like this but perhaps this is just because they like to keep it simple. However, after I log in, it seems my keyboard is in this number mode - ie no keys work apart from these 'numbers' which are on the right hand side of the letter rows.

Anyone seen this and have an idea how to fix it properly?

Can nothing say about your problems-i added "hid_apple" in my /etc/modules.conf and now my apple bt alu keyboard-finally-works perfect...

---

### Post by vickoxy on 2010-02-17
Ha-not so perfect because i have dell mini 10v-now after restart only external apple keyboard is working and internal not.
Is there fix for it? I mean, that i can use both?

---

### Post by vickoxy on 2010-02-27
Bump

---

### Post by ikus060 on 2010-03-19
May someone get this post updated with a new procedure for the latest version of Ubuntu. With Jaunty and Karmik, installing apple wireless keyboard is still a problem. It's get pair but not working on reboot.

Thanks for any help provided.

---

### Post by vickoxy on 2010-03-21
> **ikus060 said:**
> May someone get this post updated with a new procedure for the latest version of Ubuntu. With Jaunty and Karmik, installing apple wireless keyboard is still a problem. It's get pair but not working on reboot.

Thanks for any help provided.

If you use desktop computer: add "hid_apple" in /etc/modules.conf 

But if you use laptop-you won´t be able to use internal keyboard.

Before that you have to connect with bluetooth-manager or blueman your apple keyboard for the first time. Be careful, you have to repeat connecting procedure at least 2 times to actually connect keyboard to computer. After that it should work...

---

### Post by lancest on 2010-03-31
My Apple bluetooth keyboard is up and working in Lucid thanks to this thread (and the great Ubuntu developers.) 
 Just follow previous post instructions

---

### Post by untmdsprt on 2010-04-22
I'm so glad all you people can read whatever directions and get this thing working. I've not been able to get my computer to recognize my keyboard at all. NOW I can't get the bluetooth services to come back on so I can use my mouse again.

What do I need to do to get bluetooth re enabled again?

Can someone rewrite this thread for v9.10?


Ok, this is annoying me. Now I've lost the mouse again, and never can get the computer to pair with the computer. :(

I've reinstalled Ubuntu 10.04 from a live CD and everything is working out of the box. I find it odd, but hell it's working. Even the mouse is working. Now if I could assume I could close my Mac's lid, and just run off the external monitor, I might start switching more.

---

### Post by lancest on 2010-04-22
Keep the faith. 
Desktop
Just add: add "hid_apple" in /etc/modules.conf 
as mentioned. 
I'm using Gnome Bluetooth manager. (not Blueman)
Go through it's configuration. (setup new device)
9.10 same as 10.04 setup.

---

### Post by Gemba on 2010-05-02
> **vickoxy said:**
>  Be careful, you have to repeat connecting procedure at least 2 times to actually connect keyboard to computer. After that it should work...

I'm not sure if you're referring to the same problem I have. Actually it's more of a minor annoyance than a problem.

After upgrading to Lucid I find that at the login screen when I turn my keyboard on I cannot get a connection. I have to turn the keyboard off and then on again to get it to work. Seems slightly strange why it only connects on the 2nd attempt!

---

### Post by lancest on 2010-05-02
> **Gemba said:**
> 
After upgrading to Lucid I find that at the login screen when I turn my keyboard on I cannot get a connection. I have to turn the keyboard off and then on again to get it to work. 
 Mine works on Lucid with no such issue. When I arrive at the login screen the keyboard is ready to go. No power cycling on/off hassle.

---

### Post by DoubleX667 on 2010-05-14
> **Gemba said:**
> 
After upgrading to Lucid I find that at the login screen when I turn my keyboard on I cannot get a connection. I have to turn the keyboard off and then on again to get it to work. Seems slightly strange why it only connects on the 2nd attempt!

I have the same problem here...very strange...
Anyone an idea what could cause this problem?

Thanks a lot for any input...

DoubleX

---

### Post by lancest on 2010-05-14
Not sure if this will help.

Clean install of 10.04 (64 bit)

Gnome Bluetooth manager

My Keyboard is latest model with (2 batteries).

At login screen there is a slight 1-2 second lag with indicator light showing progress.

$ lsusb  
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

Follow other thread config instructions

---

### Post by Michael Eitelwein on 2010-09-13
Just solved a nasty bug with the Apple Wireless Keyboard (Bluetooth): It works to log-in, but after log-in it shows very strange behaviour: Most keys do not work and only some few keys on the right side produce numbers.

Reason: Numlock is switched on after log-in which disables most keys and some alpahnumeric keys get numeric (even if the keyboard does not have a numpad).

Solution: Press fn-F6 twice to disable numlock. To switch numlock off permanently after log-in go to System -> Preferences -> Keyboard -> Layout -> Layout Options -> Miscellaneous compatibility options -> turn on "Default numeric keypad keys"

This setting takes effect after logging in and does not affect the graphical login screen or local consoles.

---

### Post by HeinekenPissr on 2010-10-02
After fresh install of Ubuntu 10.04 64-Bit I can use the default gnome blue-tooth manager to pair with my apple wireless keyboard.  I successfully enter in the PIN with the Apple keyboard and press enter and it reports that it paired successfully.  However when i go to use the keyboard after that nothing happens when i press any of the keys.

Am i missing something here?  of course i also tried that hid_apple trick but that didn't do anything and several reboots and repairing don't do anything either.  

It's strange to me that i can type in the PIN with the Apple wireless keyboard during the pair and then immediately after i can't type any numbers/letters in a text document.

Help please

---

### Post by HeinekenPissr on 2010-10-02
ok I went over the entire posting again trying everything once more with SOME SUCCESS.

I installed BLUEMAN and after i open up BLUEMAN and right click on my device and choose "Input Service" twice in a row very quickly it says "connecting" and is followed by "success" with a nicely working keyboard that i am typing on right now.

However when i reboot i have to manually right click on "input services" twice in a row quickly before my keyboard will work again

I have tried everything in this posting so far but nothing seems to do anything more.

---

### Post by lancest on 2010-10-02
Put this:

hid_apple

in

/etc/modules

and reboot. 

(You can use gedit if you aren't comfortable with VIM)

From experience- just play with it a little.


Sometimes Blueman works better depending on hardware.

---

### Post by HeinekenPissr on 2010-10-04
thanks Lancest, that worked

One source of confusion was that your prior post (post #93 in this forum) suggested to add hid_apple to the etc/modules.**conf** file.  That's why it wasn't working for me.

Anyway, working well now

So to be clear for others out there just place

hid_apple  

in your etc/modules file

Now i must tackle getting the function keys to work. :)

---

### Post by HeinekenPissr on 2010-10-04
hmmm. actually the function keys work fine but the media keys don't seem to do anything except for flashing a graphic on screen.

For example the eject key flashes an eject graphic on the screen but the cd tray does not eject.  the volume keys also flash a graphic on the screen suggesting the volume is muted or increased or decreased but in reality the volume stays the same.  The pause and fast forward/rewind keys don't do a thing.

I have selected the apple keyboard iso under the keyboard layout but this doesn't solve the problem.

Anyone else run into this?

---

### Post by HeinekenPissr on 2010-10-04
It's starting to seem that every solution leads to a new problem.  pffffffff!

now my apple wireless keyboard works in ubuntu after reboot as long as i reboot back into ubuntu.  But i am dual  booting and when i boot into Win7 the keyboard no longer works there until i pair the device again and enter in a new security code but then i will have to pair again in ubuntu when i go back.

finally i paired them both with the same pin number but that didn't solve the problem either.  Anyone else dualboot with a bluetooth keyboard have this problem or a solution?

---

### Post by webnickko on 2010-10-07
Hi all,
 
I've got the same problem with Apple Magic Mouse w/ Ubuntu 10.10 & W7 (x64).
Every time I switch the OS, I must pair the mouse... 
 
I've set the same "Friendly name" for the BT radio for Windows and Ubuntu. The passkey is the same : 0000
 
Any idea?
 
Many thanks!

---

### Post by HeinekenPissr on 2010-10-07
@Webnickko:  I solved the problem with dual booting with blue tooth and not having to pair the device every time i switch operating systems.

What you need to do is pair the device in windows  and then look at the hex key for the pair in the windows registry and then copy that hex key to your /var/lib/bluetooth/linkkeys

this thread saved me ( [http://ubuntuforums.org/showthread.php?t=1479056](http://ubuntuforums.org/showthread.php?t=1479056) ) but i'll walk you through exactly as i did.

First pair the device in Ubuntu and then open the following file:

> sudo gedit /var/lib/bluetooth/00:00:00:00:00:00/linkkeys  

***NOTE*** 00:00:00:00:00:00 is the address of your bluetooth pc/dongle (receiver) not your keyboard.  Use your file browser and look into the /var/lib/bluetooth/ directory. There is probably only one folder which is the address of your bluetooth pc/dongle

Notice that within the linkkeys file it shows something like this:

11:11:11:11:11:11 xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 6 6

****NOTE**** 11:11:11:11:11:11 is the address of your bluetooth device and xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx is the 16 bit hex key that you are going to get from your windows registry and copy in its place.  If you have more than one line in this file then you have more than one bluetooth device with a pairing key.  You will have to figure out which is which. Blueman easily tells you which device is which.

Ok i just wanted to familiarize you with what we will be doing in ubuntu and since i'm not sure if that linkkeys file would be created without an initial pairing I had us start there.

Now for the real work!

Boot into windows and Pair the device again and make sure it is working.  Now reboot windows **was an important step for me**

NOW WE NEED TO RUN REGEDIT UNDER THE SYSTEM ACCOUNT so nothing is hidden from us

to do this download this tool from here: [http://technet.microsoft.com/en-us/sysinternals/bb897553.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897553.aspx)  

unzip that file into a directory of your choice and run  cmd.exe and change into the directory

type:

>  psexec -s -i regedit.exe 



You will then run regedit as SYSTEM, and be able to find the link key entry from windows.

now go to: >  [HKEY_LOCAL_MACHINE\SYSTEM\ControlSet002\services\BTHPORT\Parameters\Keys\ 

There will be one more subfolder whose name i think is system specific.  In that subfolder will be the hex key for your device. The name of the hex key will be the address of your keyboard ( 11:11:11:11:11:11 )  and the value of the hex key will be 16 pairs of numbers looking like this:
 xx xx xx xx xx xx xx xx xx xx xx xx xx xx xx xx

This is the 16 bit Hex key.  It doesn't let you copy and paste from here so export this specific registry file somewhere on your computer and then open up that exported file and copy  and paste it into a text file and then remove all the the spaces so that it looks like: 

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Now go into ubuntu

> sudo gedit /var/lib/bluetooth/00:00:00:00:00:00/linkkeys 


and replace the old hex key with the one you copied from windows registry into a text file  and leave the rest the same.  REMEMBER YOU NEED TO HAVE REMOVED THOSE SPACES in the hex key

11:11:11:11:11:11 xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 6 6


All i had to do after that was unplug and reinsert by bluetooth dongle

CHEERS!!! and thanks to mbehensky and harbulot for solving this in the original post located here:  [http://ubuntuforums.org/showthread.php?t=1479056](http://ubuntuforums.org/showthread.php?t=1479056)


***on a side note my eject key on the keyboard still doesn't do anything, haven't figured that one out yet***

---

### Post by webnickko on 2010-10-08
Many THANKS HeinekenPissr!!!
It works great! :P
 
You are like my mouse... Magic! ^_^

---

### Post by markitoxs on 2011-01-13
I managed to make this work, by updating bluez to a newer version found in Brian Rogers repository.

```
add-apt-repository ppa:brian-rogers/ppa
apt-get update
apt-get install bluez
```

After this it paired at first time, however it looked like there ware multiple keypresses. After a reboot, it is working flawlessly.

---

### Post by daanieo on 2011-01-31
Hi folks,

Like everyone here I've got the Apple Wireless Keyboard. Everything was working in Ubuntu 10.04, but I thought I was supposed to have a newer version: 10.10. When I was upgrading the keyboard was still working, but when I rebooted and logged on it didn't work anymore. 
It does connect, but there only appears something on the screen when I'm typing numbers. To me it looks like Ubuntu says it's a number pad. Of course, I didn't buy it to use it as a number pad, so I asked you guys for some help.

Thanks in advance :-)

---

### Post by lancest on 2011-01-31
I've had success using Blueman bluetooth manager in machines where Gnome bluetooth (included with Ubuntu) did not seem to work. 

You can install it along side and remove the one not needed. 

Otherwise follow the instructions of this thread.

---

### Post by mattewong on 2011-02-02
daanieo, 

I had the same problem and it took me several days to familiarize myself with the bluez and how it works-- or is supposed to work (linux/ubuntu community: why is there no documentation whatsoever on this, other than old outdated documentation for versions of bluez that are no longer supported and whose instructions don't work for the new version?). 

the problem I had was that bluez was buggy: it was not saving the linkkeys in /etc/../bluetooth/../linkkeys. 

I posted the solution that worked for me at [http://askubuntu.com/questions/12502/how-do-i-get-the-apple-wireless-keyboard-working-in-10-10](http://askubuntu.com/questions/12502/how-do-i-get-the-apple-wireless-keyboard-working-in-10-10) (entry starting with "OK folks") and at [https://prodigyone.com/in/doc/docs.php?nid=333&view=1](https://prodigyone.com/in/doc/docs.php?nid=333&view=1).

basically, to get this garbage to work, I had to rebuild it from the latest source code. But thankfully, it's worked without the slightest flaw since.

Hope it helps

---

### Post by bemental on 2011-02-10
> **daanieo said:**
> Hi folks,

Like everyone here I've got the Apple Wireless Keyboard. Everything was working in Ubuntu 10.04, but I thought I was supposed to have a newer version: 10.10. When I was upgrading the keyboard was still working, but when I rebooted and logged on it didn't work anymore. 
It does connect, but there only appears something on the screen when I'm typing numbers. To me it looks like Ubuntu says it's a number pad. Of course, I didn't buy it to use it as a number pad, so I asked you guys for some help.

Thanks in advance :-)

There was a poster before who solved this problem earlier in the thread:

"Just solved a nasty bug with the Apple Wireless Keyboard (Bluetooth): It works to log-in, but after log-in it shows very strange behaviour: Most keys do not work and only some few keys on the right side produce numbers.

Reason: Numlock is switched on after log-in which disables most keys and some alpahnumeric keys get numeric (even if the keyboard does not have a numpad).

Solution: Press fn-F6 twice to disable numlock. To switch numlock off permanently after log-in go to System -> Preferences -> Keyboard -> Layout -> Layout Options -> Miscellaneous compatibility options -> turn on "Default numeric keypad keys"

This setting takes effect after logging in and does not affect the graphical login screen or local consoles."


Hope this helps!

---

### Post by bemental on 2011-02-13
Found another solution that worked for the most part.

[http://askubuntu.com/questions/12502/how-do-i-get-the-apple-wireless-keyboard-working-in-10-10](http://askubuntu.com/questions/12502/how-do-i-get-the-apple-wireless-keyboard-working-in-10-10)

I went with the poster's first method (A) and am now only trying to figure out how to have the bluetooth daemon start on login (then I think I'd be set).  Haven't given his second method a try yet.

---

### Post by mhope on 2011-03-01
Hey everyone,
I have a Toshiba Satellite R25 with Ubuntu 10.10 installed on it. I use it primarily as a drawing tablet, so I got one of the newer aluminum Apple bluetooth keyboards to use with it. I am attempting to pair it with a Targus USB bluetooth dongle.

When I try to "Set Up A New Device" using gnome-bluetooth, I will sometimes receive a message saying that the pairing failed, sometimes it will succeed but then require me to enter "the pin mentioned on the device," and other times it will say the pairing is successful, but I still can't enter any characters using the Apple keyboard. 

I know it's not the dongle, because on the same machine I've been able to connect with the Apple keyboard when using Windows 7. I've also tested pairing it with my CR-48 which is running the same version of Ubuntu, and that worked without a hitch.

Has anyone encountered the problem I'm having and solved it? I'm trying to move away from Win7/Photoshop, but these kinds of little bumps in the road keep coming up. Any advice would be greatly appreciated!

Thanks
-M

---

### Post by Quarkrad on 2011-10-01
Can anybody help me?  I have tried 10.10 and 11.04 and I get the same problem.  I have the wireless keyboard and mouse.  The mouse works OK on both although in 10.10 I have to manually pair each boot but on 11.04 it pairs automatically each boot.  The problem is the keyboard.  The bluetooth manager window 'see's' the keyboard but when it asks me the enter the (pairing) password the keyboard is totally unresponsive.  I have tried all the suggestions in this thread but noting seems to work.  I know the kb is OK because it works on a mac.

---

### Post by HeinekenPissr on 2012-02-25
I recently installed a fresh copy of ubuntu 11.10 and paired my keyboard as previously described by my earlier post but after the pairing the apple keyboard would only output numbers (when pressing only some of the letter keys).

**** When you are doing the initial pairing of the apple keyboard make sure your num Lock key is not turned on in any of the other keyboards that may be attached to your system.  That is what happened to me and then when my apple keyboard was paired it thought it was a number pad keyboard and not an actual keyboard.

I had to remove the device and re-pair for it to finally work properly

---

### Post by slayer66 on 2012-09-16
> **HeinekenPissr said:**
> I recently installed a fresh copy of ubuntu 11.10 and paired my keyboard as previously described by my earlier post but after the pairing the apple keyboard would only output numbers (when pressing only some of the letter keys).

**** When you are doing the initial pairing of the apple keyboard make sure your num Lock key is not turned on in any of the other keyboards that may be attached to your system.  That is what happened to me and then when my apple keyboard was paired it thought it was a number pad keyboard and not an actual keyboard.

I had to remove the device and re-pair for it to finally work properly


I had the same issue. On an apple keyboard "mini" no keypad on this keyboard, however if you simply click on the fn control keys the keyboard jumps out of numlock. 

If you have a long keyboard  I think it is control clear keys to get out of numlock.

I hope this helps someone, it was driving me mad.. lol

---

### Post by TheLastWilson on 2012-10-12
> **Michael Eitelwein said:**
> Just solved a nasty bug with the Apple Wireless Keyboard (Bluetooth): It works to log-in, but after log-in it shows very strange behaviour: Most keys do not work and only some few keys on the right side produce numbers.

Reason: Numlock is switched on after log-in which disables most keys and some alpahnumeric keys get numeric (even if the keyboard does not have a numpad).

Solution: Press fn-F6 twice to disable numlock. To switch numlock off permanently after log-in go to System -> Preferences -> Keyboard -> Layout -> Layout Options -> Miscellaneous compatibility options -> turn on "Default numeric keypad keys"

This setting takes effect after logging in and does not affect the graphical login screen or local consoles.


Thank-you, I'm running 12.04 and was baffled. :)

---

