---
title: "headless ubuntu server 11.04 pausing with menu"
date: 2011-08-04
forum: Server Platforms
---

### Post by dwanders on 2011-08-04
I have a headless install of Ubuntu Server 11.04. Everything runs perfectly as I want, however sometimes it seems that if the server reboots it will present the menu to select a kernel - not always but sometimes. Which becomes extremely annoying - as the times it happens, I need to find a head and a keyboard, and press enter. Other times it boots just perfectly. The only way I know is if I cannot ping it, then I verify by hooking up a head. 

Any advice on making it always bypass the menu would be greatly appreciated. Am a pretty new to this version of the OS and running headless so I will be sshing to the server to make these changes - step by step would be awesome!

---

### Post by Entilza on 2011-08-05
Check your grub settings it should be set to timeout and select the first one by default.

Check:

/etc/default/grub

You should try and experiment with this to test it out.  By default to get the menu to appear hold down shift when the computer is booting.   I personally disabled this feature so I can choose a different kernel if there was a problem with the last one by commenting out #GRUB_HIDDEN_TIMEOUT=0 but that's me.  My Timeout is set to 10 seconds.

after you make any changes run update-grub2

---

### Post by dwanders on 2011-08-05
Thanks for the reply!

checking out my /etc/default/grub it contains:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

And normally the computer boots just fine right into the correct kernel (most recent from update). But intermittently it will sit at the menu screen and not auto load the top (most recent) kernel. Maybe changing the GRUB_TIMEOUT=2 to =10 would always pause for a 10 second count down and would eliminate this intermittent issue? 

Will try changing that in the file (sudo nano /etc/default/grub) and then running sudo update-grub2 and will post back here. 

Thanks again for the reply and information.

---

### Post by Entilza on 2011-08-05
You mentioned you removed the keyboard from this computer, I wonder if that's triggering something at the boot menu.

Actually if you uncomment the #GRUB_HIDDEN_TIMEOUT=0 in your situation it may work better for you since somehow you are getting triggered in the boot menu.  IF you uncomment this then the grub menu won't display at all.

Your timeout was set to 2 seconds changing it to 10 won't really help but try uncommenting it and see... I think it's related to the menu being displayed and perhaps you not having a keyboard on this computer.

---

### Post by sblandford on 2011-08-08
I have a similar problem. Grub stalls on the kernel selection menu if it believes the previous boot failed.

This can be reset with the command.

```
grub-editenv /boot/grub/grubenv unset recordfail
```

---

### Post by andy_kc on 2011-08-08
The grub-editenv command did not work for me.
 
I edited the /etc/grub.d/00_header file and changed the timeout if a previous boot failed from -1 to 5 (5 seconds rather than not timeout).  It's near the bottom of this file, and looks like this after the change...
 
make_timeout ()
{
cat << EOF
if [ "\${recordfail}" = 1 ]; then
set timeout=[COLOR=red]5[/COLOR]
else
set timeout=${2}
fi
EOF
}
 
This is a template file that is used to create the grub.cfg file that is actually used during boot.  Why change this and not grub.cfg?  Well fingers crossed this change will survive updates to grub where as grub.cfg sometimes gets overwritten.  Not sure until I get an update.
 
So to make the template change affect the grub.cfg you have to run the gurb update command...
 
sudo update-grub2
 
I double checked the files had updated and rebooted.  Then did a few power outage tests.
 
In one of my tests it found error bad enough to ask for a manual file system check.  Again on a headless server this would be awkward.  So I edited /etc/default/rcS file and changed FSCKFIX=no to FSCKFIX=yes

---

### Post by dwanders on 2011-08-08
Thanks everyone for your replies - I am going to set it back to 2 seconds (just so it is default) and uncomment the #GRUB_HIDDEN_TIMEOUT=0 as suggested. 

After reading the new posts, I believe that is the case - during a normal shutdown (e.g. after update or if I manually run shutdown/reboot) I think things work most of the time. I seem to think it happens mainly after an unexpected power outage. so I will keep those other suggestions on hand, if this does not clear things up for me!

Thanks again everyone.

---

### Post by imnlfn on 2011-08-23
I installed 11.04 on a headless server recently and have had two power outages since then, resulting in a situation very similar to the OP, where I had to drag out a monitor and keyboard to figure out why it wasn't fully restarting.

I ended up making the change suggested by andy_kc and imagine that should work. It looked to me initially like the suggestion from sblandford should have worked, too, but when I tried [FONT=Courier New]grub-editenv list[/FONT] to see what the setting for "recordfail" was, it returned nothing at all, so I decided to cut my losses. It seems it should be possible to unset "recordfail" and set some value for the timeout to use, but I couldn't find any documentation describing how that's done. It's especially interesting that the Ubuntu Grub2 Wiki states that it's necessary to edit the script, rather than change the values of any variables.

Anyway, thanks for the solution to my problem!

---

### Post by dwanders on 2011-08-23
Ya know, I ended up changing the GRUB_Hidden_timeout, but honestly don't know if that has done anything or if we just have had a good run with the power. I think ultimately, the thing to do is to put it on a UPS! But up to now it has been a "test" thing.

---

