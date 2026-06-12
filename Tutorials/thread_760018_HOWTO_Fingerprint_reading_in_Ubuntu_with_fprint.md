---
title: "HOWTO: Fingerprint reading in Ubuntu with fprint"
date: 2008-04-19
forum: Tutorials
---

### Post by master_kernel on 2008-04-19
[COLOR="DarkOrange"][CENTER]**[SIZE="5"]Getting your fingerprint reader to work in Ubuntu[/SIZE]**[/CENTER][/COLOR]
[B]
Project fprint homepage: [http://reactivated.net/fprint/wiki/Main_Page]("http://reactivated.net/fprint/wiki/Main_Page")[/B]
Packages for fprint: [http://www.madman2k.net/comments/105]("http://www.madman2k.net/comments/105")
> The fprint project aims to plug a gap in the Linux desktop: support for consumer fingerprint reader devices.

Previously, Linux support for such devices has been scattered amongst different projects (many incomplete) and inconsistent in that application developers would have to implement support for each type of fingerprint reader separately. For more information on where we came from, see the project history page.

We're trying to change that by providing a central system to support all the fingerprint readers we can get our hands on. The software is open source and in the long term we're shooting for adoption by distributions, integration into common desktop environments, etc. 

Note: These instructions are intended for Ubuntu Jaunty.
[B]
First off, remember that fprint is not entirely stable, and may not work all the time. A list of supported devices is [here]("http://reactivated.net/fprint/wiki/Supported_devices"), and the list of unsupported devices is [here]("http://reactivated.net/fprint/wiki/Unsupported_devices").[/B]


[COLOR="Blue"]
1. Next, update your sources and install fprint:[/COLOR]
```
sudo apt-get update
sudo apt-get install fprint-demo libfprint-dev libfprint0 libpam-fprint aes2501-wy
```

[COLOR="Blue"]2. Now you can enroll your fingers using _either_ the terminal _or_ a graphical user interface.[/COLOR]
*Terminal:*
```
pam_fprint_enroll
```
*GUI:*
```
fprint_demo
```

[COLOR="Blue"]3. Last thing to do is configure PAM so that the fingerprint reader can be useful. Open up your PAM authentication file and edit it:[/COLOR]
```
sudo gedit /etc/pam.d/common-auth
```
[COLOR="Blue"]4. If you want the fingerprint to be sufficient, add this at the top of the commands (do it multiple times for however many attempts you want to allow):[/COLOR]
> auth    sufficient    pam_fprint.so
Use this if you want to require the fingerprint and the password.
> auth    required    pam_fprint.so

[COLOR="Blue"]5. For programs using gksudo/gksu, you should get the wrapper attached to this post and to add fingerprint support and enter the following code:[/COLOR]
```
sudo mv ./gksu.py /usr/local/bin/gksu
sudo chmod 755 /usr/local/bin/gksu
sudo apt-get install python-gnome2-extras python-pexpect
```


[COLOR="Blue"]7. Enjoy your fingerprint reader support![/COLOR]

Steps 4 and 5 tell Ubuntu to check your fingerprint, and if that fails, then ask your password. This rule has some exceptions, one that I have encountered is on the login screen. I have to scan my fingerprint before typing my password. One thing I did notice is that when you use sudo in the terminal, it asks for your fingerprint, which I thought was pretty cool. One disadvantage is that anything using gksu does not seem to work properly, specifically because it does not tell you to scan your finger when needed.
[COLOR="Green"]
**Troubleshooting:**[/COLOR]
The one problem I ran into when using fprint was that I could not run fprint_demo without sudo. It failed with the error message below:
> uru4000:error [dev_init] interface claim failed
fp:error [fp_dev_open] device initialisation failed, driver=uru4000
I decided to post my[ problem here on the forums]("http://ubuntuforums.org/showthread.php?p=4743675").
Here is the solution. You have to add yourself to the plugdev group and then change the permissions of the usb folder to allow access to the plugdev group. You can verify you are in the plugdev group by using groups:
```
sudo usermod -a -G plugdev $USER
groups | grep plugdev       # Make sure there is output from this
sudo chgrp -R plugdev /dev/bus/usb/
```
Then try running fprint_demo, and hopefully it will work:
```
fprint_demo
```

---

### Post by Evil Wayz on 2008-04-24
Everything works fine for me UNTIL i try to enroll, and then it tells me no device found.  I knwo it's there because it shows up in verbose mode bootup.  Help?

---

### Post by Gotterdammerung on 2008-04-24
> **Evil Wayz said:**
> Everything works fine for me UNTIL i try to enroll, and then it tells me no device found.  I knwo it's there because it shows up in verbose mode bootup.  Help?

Same problem here...

---

### Post by JSorrell on 2008-04-24
Everything worked great for me, except I had to change
```
fprint_demo
```
to
```
sudo fprint_demo
```

Otherwise, fprint_demo couldn't open the fingerprint reader (a Microsoft reader, btw). Works great, last time I tried this it couldn't recognize the device.

[EDIT] After a reboot I've got some strange behavior. Anything that requires a password now requires a password, a fingerprint scan, then the password again before anything can continue. Any ideas?

[EDIT2] Fixed it. Reordering the entries in /etc/pam.d/common-auth to list the fingerprint reader first eliminated the multiple password entries.

---

### Post by master_kernel on 2008-04-26
> **Evil Wayz said:**
> Everything works fine for me UNTIL i try to enroll, and then it tells me no device found.  I knwo it's there because it shows up in verbose mode bootup.  Help?
Try following the steps in troubleshooting to fix this.

---

### Post by Nurionn on 2008-04-28
Thanks, that worked almost perfect for me.

I have only one problem: Since I installed my fingerprint reader, I cannot change network or user settings using the GUI.
If I click on "Unlock" the window freezes for ~20sec and then it shows an error message saying approximately: "authentification failed! an unexpected error has occurred." (German version: "Authentifizierung fehlgeschlagen! Es ist ein unerwarteter Fehler aufgetreten.")

Has anyone an idea?

---

### Post by master_kernel on 2008-04-28
> **Nurionn said:**
> Thanks, that worked almost perfect for me.

I have only one problem: Since I installed my fingerprint reader, I cannot change network or user settings using the GUI.
If I click on "Unlock" the window freezes for ~20sec and then it shows an error message saying approximately: "authentification failed! an unexpected error has occurred." (German version: "Authentifizierung fehlgeschlagen! Es ist ein unerwarteter Fehler aufgetreten.")

Has anyone an idea?
This is just one of the bugs in fprint; I get this error too. If you find a fix, let me know.

---

### Post by moob on 2008-04-29
> **master_kernel said:**
> Try following the steps in troubleshooting to fix this.

I have similar problem like **Evil Wayz** has. I was googling in I-mess. But i still can't find reason. 
I know that my fprintreader is working propertly (i used it in Vista).
When I type su:
```
Could not locate any suitable fingerprints matched with available hardware.
```
pam_fprint_enroll:
```
No devices detected.
```

What kind of information do you need from my side?
Thank you.

---

### Post by Gotterdammerung on 2008-05-07
up

---

### Post by moob on 2008-05-07
> **Gotterdammerung said:**
> up
What do you mean by this? You mean your fprint is working? How did you solved it?

---

### Post by Gotterdammerung on 2008-05-08
> **moob said:**
> What do you mean by this? You mean your fprint is working? How did you solved it?

No, my fingerprint is not working. This "up" means that I wanted the thread to go up on the forum and call attention to somebody who may have the solution.

---

### Post by Gotterdammerung on 2008-05-08
> **moob said:**
> What do you mean by this? You mean your fprint is working? How did you solved it?

I have the same problem as you do.

---

### Post by stillka on 2008-05-09
Hello, 

it works without problems on my HP Compaq 6710b with AuthenTec AES2501 device. Now I login to Linux with my finger :-)

Thank you.

p.s: isn't possible to use it also for keyring manager?

---

### Post by rogosh55 on 2008-05-10
hi, i followed this thread to get the fingerprint reader working. which it did. however, i didnt read all the posts that describe exactly what it did.
so i thought it was going to just replace the login rather than now require name fingerprint and password.

i deleted the stuff that was originally in common-auth and inserted the stuff from the post. i was just wondering if anyone could help me out with replacing that original content so i could remove the fingerprint section. 

i basically want to turn the fingerprint reading requirement off because other people use my computer frequently and i dont want  to have to register all their fingerprints. so yeah. thx if anyone can help.

---

### Post by rjgii on 2008-05-22
Original content of your common-auth file woulda/shoulda been:

auth	requisite	pam_unix.so nullok_secure
auth	optional	pam_smbpass.so migrate

---

### Post by honeydew on 2008-05-22
This is unrelated.. and probably shouldnt be in this thread.. however I came across this recently..

People that are using there finger print reader... here is some food for thought on security.
[http://www.ccc.de/biometrie/fingerabdruck_kopieren.xml?language=en](http://www.ccc.de/biometrie/fingerabdruck_kopieren.xml?language=en)
[http://www.ccc.de/updates/2007/umsonst-im-supermarkt?language=en](http://www.ccc.de/updates/2007/umsonst-im-supermarkt?language=en)

now.. many of you will be using your finger print reader on your laptop.. how secure is you device that has your finger prints all over it?  If your using your fingerprint for novelity or bragging rights.. awesome I did for a few months.. but anything that needs to be secured should not be done with your finger prints.

---

### Post by louisli on 2008-05-23
Thanks for the guide, I'm an idiot in linux so your guide helped me a lot.  It worked for my Fujitsu S6310 with AES2501.

I'm using Ubuntu 8 and Gnome, just some problems... I don't know when do I need to scan the fingerprints.  I enrolled all my fingers with fprint_demo, and I also enrolled with pam_fprint_enroll, I edited common_auth and appended the 2 lines below what I have in the file.

While login (with GUI), I cannot see anything prompt for my fingerprint, so I typed my lengthy password and then the login seems stucked, I swiped my fingerprint and then it prompted my for the password again (OMFG, I screwed the installation), I typed the password again, luckily I logged on the system.

And then I have problem in updates, I can see 1 update available.  I clicked download on the update window and typed my password, the system frozen (seems waiting for something), I swiped my fingerprint, it came back to life and goes back to the update window with 1 update available, I clicked download again and the process just looped (click -> password -> frozen -> fingerprint -> back to life)

I just can't do any updates, any workarounds?

---

### Post by rplancius on 2008-05-25
Works like a charm. I just followed exact instructions on my HP 8710W with the Authentec AES2501 reader. I didn't need the extra permissions. I can now use it to log in, unlock my screen. Great! I enrolled four fingers on both hands. When unlocking my screen it consistently asks for the same finger. Is there a way of changing this?

---

### Post by rplancius on 2008-05-27
Edit May 27, 2008. Since the installation of the fingerprint reader, the Update Manager hangs. It doesn't show the password pop-up screen, nor does it ask for a fingerprint. The only way of ending this, is killing the process. There are some posts saying the hosts file is incorrect. I changed the /etc/pam.d/common-auth file back to it's original state and the update manager works like before. Perhaps needless to say that fingerprint authentication is now disabled. Hope this helps someone.

---

### Post by pieeater3142 on 2008-05-29
Hi There,
I'm relatively new to Ubuntu (8) although messing with linux distros for years.
I have an HP Compaq 6710b and have got the fingerprint reader working - sort of.

Hears the deal - theres no message box asking for my finger print, if i'm quick enough then i can get a fingerprint logon instead. Is this as it should be or should i have a pop up box requesting a fingerprint first before the password. 
Is there any way of determining when a fingerprint is needed as synaptics and a few other things don't open atm unless i intuatively swipe my finger at the right time.

my current  /etc/pam.d/common-auth reads:

auth	sufficient	pam_fprint.so
auth	required	pam_unix.so try_first_pass likeauth nullok
auth	required	pam_deny.so

Any info would be appreciated. Especially on how to get Ubuntu to tell me when it wants a fingerprint read (incidentally it asks for one in the terminal - although the time out is ridiculous)

Also can the timeout on the fingerprint reader be changed?

Thanks

PieEater :D

---

### Post by moob on 2008-05-29
Hi PieEater,
I wanted to use my fingerprint reader too. I was searching an discovering. I've found few projects dealing with this. The bigges (I think) is fprint. I'm subscribed in fprint mailing list and I can tell it is still in developement mode and it can provide you just logging into system. There are no more other special program supporting it yet. But during last month it has few devel-jumps and this fprint project is growing up. We have to be patient.

BTW: Trust that finger print method isn't as secure as you think. Everyone can make copy of your fingermark. I will try it too in close future and I will tell you if my girlfriend can log into my pc throught fingerprint reader.
There is little HOWTO: [How to fake fingerprints?]("http://www.ccc.de/biometrie/fingerabdruck_kopieren.xml?language=en")
Interesting. Isn't it?

---

### Post by Nurionn on 2008-06-03
> **rplancius said:**
> Edit May 27, 2008. Since the installation of the fingerprint reader, the Update Manager hangs. It doesn't show the password pop-up screen, nor does it ask for a fingerprint. The only way of ending this, is killing the process. There are some posts saying the hosts file is incorrect. I changed the /etc/pam.d/common-auth file back to it's original state and the update manager works like before. Perhaps needless to say that fingerprint authentication is now disabled. Hope this helps someone.
That is normal at the moment, I suppose. It does work, even if it doesn't show any message.
But you might have only one try... ;)

---

### Post by csocci on 2008-06-11
Working, sort of, with HP 6910 Ubuntu Hardy 64-bit,  2.6.24-18-generic

Freezes trying to configure users via gui.

Logon requires finger scan as well as password.

The two issues above kind of defeat the purpose for me, as I'd like to scan and not type. It is an extra step. I guess it is more secure.

But thanks to the folks responsible for writing and testing this. Hopefully the bugs can get worked out.

Cheers,

CS

---

### Post by master_kernel on 2008-06-19
Thread updated.

---

### Post by z3r0-421 on 2008-06-30
Great Tutorial. Works perfect for me and my Microsoft Fingerprint Reader :) .

It even works better than under Vista.

z3r0

PS: Sorry 4 my bad English :(

---

### Post by pieeater3142 on 2008-07-08
Hi guys,

Any news on updates on displaying scan requests in gui?

Cheers

PieEater

---

### Post by Paresh on 2008-07-16
This worked for me, if I ran ```
sudo fprint_demo
``` but if I ran just ```
fprint_demo
``` It would not work.

I tried the workaround of adding my user to the plugdev group and the I got ```
error loading enrolled prints
```

This turned out to be because the /home/user/.fprints directory was owned by root, so I did ```
sudo chown -R $USER /home/user/.fprints
``` it started working.

Is this correct, or have I opened a security hole?


Although fprint_demo works on my Tecra A9, it does report a couple of errors while scanning or verifying
```

upekts:error [read_msg] non-zero bytes in cmd response
upekts:error [read_msg28] expected response, got -1 seq=0

```
Both messages are produced for each action.

I get this every time the scanner is used, eg verifying your finger and enrolling your finger produce this error, but deleting a fingerprint file does not.  Also on enrolling, I only get the error once, not three times.

---

### Post by zanelightning on 2008-07-31
I followed the directions as posted, and they seem to work, but sadly I get a segfault whenever sudo is used. However, the fingerprint auth works when logging in. I can't seem to figure this out, any suggestions?

---

### Post by chase809 on 2008-08-15
> **Nurionn said:**
> Thanks, that worked almost perfect for me.

I have only one problem: Since I installed my fingerprint reader, I cannot change network or user settings using the GUI.
If I click on "Unlock" the window freezes for ~20sec and then it shows an error message saying approximately: "authentification failed! an unexpected error has occurred." (German version: "Authentifizierung fehlgeschlagen! Es ist ein unerwarteter Fehler aufgetreten.")

Has anyone an idea?

I was having the same problem until I realized that I can insert the 

auth	sufficient	pam_fprint.so

into any pam.d file.  So instead of entering this into the common-auth which is pulled by most files/auth methods I insert this line into the functions I wish to have my finger reader.  For example if I want my finger reader to unlock my screensaver I inserted it into the gnome-screensaver (above the include common-auth section).  The final product looks like this.

auth	sufficient	pam_fprint.so
@include common-auth
auth optional pam_gnome_keyring.so

Now my finger reader works for just my gnome-screensaver and doesn't cause my policy kit to lock up.  I have a feeling the pam_fprint.so has not been developed for the new policy kit in 8.04.  Hope this helps, you can explore with different pam.d files and turn the finger reader on or off.

---

### Post by simo on 2008-10-06
I have a problem

```

fbrun_demo
** Message: now monitoring fd 4
upeksonly:error [dev_init] could not set configuration 1
async:error [fp_async_dev_open] device initialisation failed, driver=upeksonly
** Message: no longer monitoring fd 4

```

And message in fprint_demo "Could not open device."

Using libfprint-20080810-6b8b17f5 and fprint_demo-20080319-5d86c3f7
libusb is 0.9.2

lsusb
```
147e:2016
``` 

it is UPEK TouchStrip

---

### Post by shaunarman on 2008-10-18
> **moob said:**
> I have similar problem like **Evil Wayz** has. I was googling in I-mess. But i still can't find reason. 
I know that my fprintreader is working propertly (i used it in Vista).
When I type su:
```
Could not locate any suitable fingerprints matched with available hardware.
```
pam_fprint_enroll:
```
No devices detected.
```

What kind of information do you need from my side?
Thank you.

I get the same responce in the terminal. I cant use my passwords at all to unlock any admin rights, I am not able to save the common-ath file. I just want this off my computer, PLEASE HELP total noob

---

### Post by pajarraco on 2008-10-20
> Thanks, that worked almost perfect for me.

I have only one problem: Since I installed my fingerprint reader, I cannot change network or user settings using the GUI.
If I click on "Unlock" the window freezes for ~20sec and then it shows an error message saying approximately: "authentification failed! an unexpected error has occurred." (German version: "Authentifizierung fehlgeschlagen! Es ist ein unerwarteter Fehler aufgetreten.")

Has anyone an idea?

anything about this, i have the same problem. 
I do not know much about ubuntu but maybe there is anyway to disable the figerprint on this "unlock" and use regular password.

---

### Post by beercz on 2008-10-21
Thanks master_kernel :-)
 
Using your guide I have managed to get the Authentec 2501 fingerprint sensor working on my Lenovo 3000 N200 laptop running Intrepid!
 
Thanks once again.

---

### Post by micdhack on 2008-10-26
for me worked fine.
This is my device Bus 002 Device 003: ID 08ff:1600 AuthenTec, Inc. AES1600
Everything worked fine until the point password chceks on menus such as network user and groups etc.
Also i could find the file gksu.py

---

### Post by CosminGC on 2008-11-05
> **micdhack said:**
> 
Also i could find the file gksu.py

mee too, fresh install 8.10 and couden't boot after following the #1 post
but I changed the files back, but how do I use the fingerprint reader in gdm and in gksu?

---

### Post by alexvd on 2008-11-08
Hi I have a motion m1400 tablet and it uses a authentec 2501. I actually contacted the fprint developers and they were able to add support for this device.  I have the latest release version but I cannot figure out how to get the cvs or devel release that incorporates the code update to get the fix.   Can anyone tell me how to get this for hardy heron.  I dont know how to compile or build a deb.  I can add a software source and follow directions.

---

### Post by wooju86 on 2008-11-10
hello,

i am trying to install fprint on my laptop. at the moment i've got problem with placing the two lines in the common.auth file. this is the file:

```

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-5, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure

# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

can somebody tell me where should i place those two lines? 

```
auth sufficient pam_fprint.so
auth required pam_unix.so nullok_secure.
```

thank you

---

### Post by cybrsrce on 2008-11-11
Intrepid doesn't seem to like pam_unix.so, at least not in my tests.

Add the auth sufficient pam_fprint.so above the auth required pam_permit.so line.  I added the nullok_secure to the existing required line:

auth required pam_permit.so nullok_secure

On occasion, it will ask for a password and then the fingerprint instead of one or the other...

Thinkfinger worked perfectly in Hardy but has a known bug in Intrepid where you have to press enter after a finger swipe.  With that fixed, ([http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger)) thinkfinger works much better than fprint.  The only thing it is missing is a cool fingerprint enrollment gui.

---

### Post by beercz on 2008-11-12
I think I have a problem with the finger print reader after I resume from hibernation.

When I run fprint-demo I get the following message:

> Status: could not open device

Also if I try to run a command using sudo I get this:

> sudo synaptic
aeslib:error [do_write_regv] bulk write error -2
fp:error [fp_dev_open] device initialisation failed, driver=aes2501

If I reboot then everything is fine.

Any ideas anyone?

Thanks in advance.

---

### Post by Vadi on 2008-11-12
The packages are included in Ubuntu 8.10, I guess the guide should be updated for that.

---

### Post by speedisso on 2008-11-12
the program is working great for me, the bad thing is that i can my fingerprint and after that i want to verify it...and guess what ? doesn´t recognized it

---

### Post by camofish on 2008-11-23
Trying to use the versions in the Intrepid repo of both fprint and thinkfinger results in hardware not found, even using sudo, on my Vaio VGN-TZ130N.  Any ideas?  

Everything else works splendidly with minimal effort which says a lot about the impact of this thread! :)

---

### Post by camofish on 2008-11-23
Trying to use the versions in the Intrepid repo of both fprint and thinkfinger results in hardware not found, even using sudo, on my Vaio VGN-TZ130N.  Any ideas?  

Everything else works splendidly with minimal effort which says a lot about the impact of this thread! :)

---

### Post by emecas on 2008-12-22
Hey thanks chase809

I was looking long time for the causes about that problem

A real help that appear like a surprise and in a place looking for other subject.. 

[http://ubuntuforums.org/showthread.php?p=6307354#post6307354](http://ubuntuforums.org/showthread.php?p=6307354#post6307354)


> **chase809 said:**
> I was having the same problem until I realized that I can insert the 

auth	sufficient	pam_fprint.so

into any pam.d file.  So instead of entering this into the common-auth which is pulled by most files/auth methods I insert this line into the functions I wish to have my finger reader.  For example if I want my finger reader to unlock my screensaver I inserted it into the gnome-screensaver (above the include common-auth section).  The final product looks like this.

auth	sufficient	pam_fprint.so
@include common-auth
auth optional pam_gnome_keyring.so

Now my finger reader works for just my gnome-screensaver and doesn't cause my policy kit to lock up.  I have a feeling the pam_fprint.so has not been developed for the new policy kit in 8.04.  Hope this helps, you can explore with different pam.d files and turn the finger reader on or off.

---

### Post by campo85 on 2009-01-01
I have an ASUS F6A with this fingerprint reader :

```
Bus 002 Device 002: ID 04f2:b029 Chicony Electronics Co., Ltd
```

The first time I have used the reader, it worked well :

```
campo@enterprise:/usr/src/fprint_demo-0.4$ sudo pam_fprint_enroll
This program will enroll your finger, unconditionally overwriting any selected print that was enrolled previously. If you want to continue, press enter, otherwise hit Ctrl+C

Found device claimed by AuthenTec AES1610 driver
Opened device. It's now time to enroll your finger.

You will need to successfully scan your Right Index Finger 1 times to complete the process.

Scan your finger now.
Enroll complete!
Enrollment completed!


```

but the second time it didn't work :

```
campo@enterprise:/usr/src/fprint_demo-0.4$ sudo pam_fprint_enroll
This program will enroll your finger, unconditionally overwriting any selected print that was enrolled previously. If you want to continue, press enter, otherwise hit Ctrl+C

Found device claimed by AuthenTec AES1610 driver
aeslib:error [do_write_regv] bulk write error -2
fp:error [fp_dev_open] device initialisation failed, driver=aes1610
Could not open device.

```

Someone can help me ? Thanks in advice for the answer and sorry for my english.

P.S. I have a Kubuntu 8.04 with custom kernel ( 2.6.28 ) 
P.P.S. I think that the reader remains locked so fprint_demo couldn't open device.

---

### Post by john5898 on 2009-01-05
i did that, first i couldnt log on, and then the X server failed on me!

---

### Post by washakie on 2009-01-15
Nicely done... seems to (almost) work. I have a AES1610, supposedly support. I use sudo to execute both pam_fprint_enroll and/or fprint_demo:

$ sudo pam_fprint_enroll 
This program will enroll your finger, unconditionally overwriting any selected print that was enrolled previously. If you want to continue, press enter, otherwise hit Ctrl+C

Found device claimed by AuthenTec AES1610 driver
Opened device. It's now time to enroll your finger.

You will need to successfully scan your Right Index Finger 1 times to complete the process.

Scan your finger now.
Segmentation fault
$

The segmentation fault occurs in both the gui and with pam when I swipe my finger. Any ideas?

Ubuntu 8.10:
$ uname -a
Linux server 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

---

### Post by pmontrasio on 2009-01-16
I can't run aes2501 on my HP nc8430, ubuntu 8.10 amd64.
Here are the details:

$ lsusb
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor

$ sudo apt-get install aes2501-wy
$ sudo apt-get install libfprint0 libpam-fprint fprint-demo

All went fine.

$ sudo aes2501 
argc=1 Initializing, please standby...
No device found

$ sudo fprint_demo
aeslib:error [do_write_regv] bulk write error -2
fp:error [fp_dev_open] device initialisation failed, driver=aes2501

It shows the device with a status message "Could not open the device".
Any idea? Thanks!

---

### Post by markus.meetr.de on 2009-01-22
> **washakie said:**
> Nicely done... seems to (almost) work. I have a AES1610, supposedly support. I use sudo to execute both pam_fprint_enroll and/or fprint_demo:

$ sudo pam_fprint_enroll 
This program will enroll your finger, unconditionally overwriting any selected print that was enrolled previously. If you want to continue, press enter, otherwise hit Ctrl+C

Found device claimed by AuthenTec AES1610 driver
Opened device. It's now time to enroll your finger.

You will need to successfully scan your Right Index Finger 1 times to complete the process.

Scan your finger now.
Segmentation fault
$

The segmentation fault occurs in both the gui and with pam when I swipe my finger. Any ideas?

Ubuntu 8.10:
$ uname -a
Linux server 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
same problem here with AES1610 on Intrepid 64 bit :(

---

### Post by heinzisoft on 2009-02-10
I didn't read all the posts here and don't know if anyone already has mentioned it. I think that in point 5 of the Howto it should be
```
auth sufficient pam_fprint.so
auth requisite pam_unix.so nullok_secure
```
instead of auth required in the second line.
When there is auth required, my computer asks me always to enroll my finger AND to insert a password. When I change it to auth requisite, it only asks me my password if the fingerprint authentication failes.

---

### Post by Vadi on 2009-02-10
Thanks a bunch

---

### Post by bond17_007 on 2009-02-13
Hi, 
I just installed Ubuntu 8.10 64bit on my Dell Studio 1735.
I am trying to configure my finger print reader for authentication. I tried fprint, thinkfinger 0.3 etc..but i am not able to get it working :(.

When i did fprint_demo, it says "No Device Found".. 
can anyone who have successfully configured it .. plz share your solution.. 
thanks,

---

### Post by moob on 2009-02-13
Hi,
type:
```
sudo lsusb
```
and visit this pages: [Unsupported devices]("http://reactivated.net/fprint/wiki/Unsupported_devices") and [supported devices]("http://reactivated.net/fprint/wiki/Supported_devices"). And even more try to explore [Fprint wiki]("http://reactivated.net/fprint/wiki/Main_Page"). ;)

With regards.

---

### Post by bond17_007 on 2009-02-13
Thanks Moob, 
   This is what i get with sudo lsusb

Bus 007 Device 002: ID 05ca:18a1 Ricoh Co., Ltd 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 08ff:2810 AuthenTec, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

My computer does have,
5 usb ports, 1 hdmiii, 1 vga and 1394 port... 
i did see AuthenTec in unsupported page that u had.. 
its using AES 2810

i wonder if there is something I can do to make it work coz i did see in some other thread that people did have it working on their Dell Studio.. 
(perhaps diff driver?)

---

### Post by AzazelTAP on 2009-02-24
Heh

I had only the one problem - my fingerprints doesn't match to enrolled samples 9 out of 10 times :)))

---

### Post by bond17_007 on 2009-02-25
r u using Dell 1735? the hardware manufacturer is Ricoh.

---

### Post by biasquez on 2009-03-01
Hi,
I just installed Ubuntu 9.04 32bit on my acer 6930
I am trying to configure my finger print reader for authentication. I tried fprint, thinkfinger 0.3 etc..but i am not able to get it working .

When i did fprint_demo, it says "No Device Found"..

lsusb:
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 005: ID 5986:0105 Acer, Inc 
Bus 007 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 007 Device 002: ID 07ca:a309 AVerMedia Technologies, Inc. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 147e:1000  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

in vista, fingerprint works fine and it's called uptek touchstrip (so supported by fprint)..any solution?

---

### Post by ickyb0d on 2009-03-04
I also receive a segmentation fault on my Samsung X360, the print device appears to be a "AuthenTec AES1610".  Not sure if this helps, but this was found in dmesg:

```

[ 2235.737874] fprint_demo[7918]: segfault at 21e3000 ip 00007fc97e5c6830 sp 00007fff898ae2e0 error 4 in libfprint.so.0.0.0[7fc97e5b8000+29000]
[ 2287.678945] pam_fprint_enro[7928]: segfault at 1290000 ip 00007fd3a999e830 sp 00007fffb4c85af0 error 4 in libfprint.so.0.0.0[7fd3a9990000+29000]
[ 2296.288041] pam_fprint_enro[7929]: segfault at 2357000 ip 00007fe2c2282830 sp 00007fffcd56b3d0 error 4 in libfprint.so.0.0.0[7fe2c2274000+29000]
[ 2394.992738] fprint_demo[7932]: segfault at 197e000 ip 00007f51e253d830 sp 00007fffed825260 error 4 in libfprint.so.0.0.0[7f51e252f000+29000]
[ 2446.427221] pam_fprint_enro[7942]: segfault at 2117000 ip 00007f2502134830 sp 00007fff0d41d280 error 4 in libfprint.so.0.0.0[7f2502126000+29000]

```

---

### Post by ickyb0d on 2009-03-07
So I think I found out why the segmentation faults were happening.  My friend actually has the exact same computer (and print reader) as well as the same version of ubuntu, but he didn't experience any seg faults.  Anyways the conclustion we came to was this:

When scanning a print, you absolutely **have to** *swipe your finger* across the reader.  Place the bottom of your "print" at the top of the reader, and drag it across (top to bottom) until the top of your "print" passes over the reader.  Think of it like a scanner that scans from one end of a page to the other.

The way I was getting the seg faults was just putting my finger on the reader and removing it.  I have no idea why it seg faulted, but apparently using the print reader correctly fixed it :).  So all in all, everything is working fine for me now.

---

### Post by Vadi on 2009-03-07
What a harsh teacher, eh :)

---

### Post by akuhon on 2009-03-22
> **biasquez said:**
> Hi,
I just installed Ubuntu 9.04 32bit on my acer 6930
I am trying to configure my finger print reader for authentication. I tried fprint, thinkfinger 0.3 etc..but i am not able to get it working .

When i did fprint_demo, it says "No Device Found"..

lsusb:
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 005: ID 5986:0105 Acer, Inc 
Bus 007 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 007 Device 002: ID 07ca:a309 AVerMedia Technologies, Inc. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 147e:1000  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

in vista, fingerprint works fine and it's called uptek touchstrip (so supported by fprint)..any solution?

That's the same case to me (same ID address 147e:1000).
Till I see this step-by-step howto.
It works great ... check this out :

[http://rvshiro.wordpress.com/2009/01/14/fingerprinting-under-ubuntu-810-on-asus-n10jc/](http://rvshiro.wordpress.com/2009/01/14/fingerprinting-under-ubuntu-810-on-asus-n10jc/)

---

### Post by deepspring on 2009-03-22
Great How-To guide. Followed it to the letter and it worked perfectly for me first go.

I noticed a few small problems with it though...

The fprint_demo allows you to enroll all your digits, but the PAM module only allows you use one of the digits for authentication. For example: if the left thumb is the very first digit enrolled through the fprint_demo interface, it becomes the default digit for authentication. All other enrolled digits are ignored.

Is there anyway to force the PAM module to cross reference the scanned digit against all enrolled digits?

Also, because only one digit is accepted for authentication, it leaves the possibility of being locked out of the system should anything happen to the required digit (such as: cuts, burns, amputation, etc).

Is there anyway to fall back to logging in using a password should something like this occur (like a hot-key or something)?


**-- Edit 23/03/09 @ 3:11am --**

Another problem has turned up in the form of "gksudo" and other privilege escalation / authentication dialogs (like the one used by Services applet) no longer appearing for applications that require root access.

I have the "gksu.py" script installed as per the instructions in the How-To.

Here is my "/etc/pam.d/common-auth" file:
```

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-5, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# Fingerprint reader
auth	sufficient			pam_fprint.so
# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

---

### Post by FAJALOU on 2009-04-19
Interesting thing happening:

The first time I use a terminal screen, it will ask me to scan finger.  But after that all I got was segfaults.... :(

```
louie@lrc-laptop:~$ sudo ifup wlan0
Scan right index finger on AuthenTec AES4000

Ignoring unknown interface wlan0=wlan0.
louie@lrc-laptop:~$ sudo ifup wlan0
Segmentation fault
louie@lrc-laptop:~$ sudo test
Segmentation fault
louie@lrc-laptop:~$ sudo test
Segmentation fault
louie@lrc-laptop:~$ sudo gedit
Segmentation fault
louie@lrc-laptop:~$ 

 
```

Right now my /etc/pam.d/common-auth looks like so:
```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#

#auth sufficient pam_fprint.so
#auth required pam_unix.so try_first_pass likeauth nullok
#auth required pam_deny.so
#auth sufficient pam_fprint.so
#auth requisite pam_unix.so nullok_secure 
auth	requisite	pam_unix.so nullok_secure
auth	optional	pam_smbpass.so migrate missingok

```

What I have been doing is commenting those two lines, and then uncommenting the two middle lines, then commenting them and uncommenting the first three lines.  So far, same result:
The first time this will work but any time after that, segfault.

So I have my common-auth open and I am trying different things.... so far nothing seems to be working.  Any help would be appreciated!

---

### Post by Jonas_Z on 2009-04-26
Hi,
ic installed fprint like it is said in the first post and it works fine, but now everythings needs a password AND the Fingerprint. What do I have to do that the Fingerprint is sufficient?

thx
Jonas

---

### Post by Manetheran on 2009-04-30
Hi I am running Debian 5.0 (all problems i've had so far have been solvable with ubuntu answers, and the ubuntu community seems far more developed especially in this issue), and cannot get my laptop to find enrolled fingerprints.
I used to use vista so i know my fingerprint scanner works and how to use one.

So far I've been having issues with not being able to open the device;  I have configured my common-auth file to look like:

auth    sufficient       pam_fprint.so
auth    required        pam_unix.so nullok_secure

which makes the login screen try to use the scanning first.  However it says it cannot find any enrolled fingerprints, so i have to login via password.  Also any system setting i try to access through the gui in gnome that requires root password crashes - i get the same cannot open device error and then it doesnt ask for my password.  I can work around this with su root in my terminal, which give me an error message then asks for my password.

I cannot seem to find where i need to enroll my fingerprint,  i need to be root to do it, but so far i have enrolled my fingerprint in: /, /root, /home/manetheran, /home/manetheran/Documents.  The last one being a test, i have discovered i cannot override any enrolled fingerprints - it says it cannot open the device, but i can enroll a fingerprint in each folder i desire. 

I suspect the locking up of the fingerprint scanner might have something do with it.

So for starters, where should i be enrolling my fingerprint that it will access it at the login screen?  How do i override enrolled fingerprints and unlock the device? How do i get around the gui asking for a fingerprint and failing?

Thanks,
Manetheran

---

### Post by Master One on 2009-05-08
It would be nice to have this howto updated and corrected. The packages are now in main repo, I guess the pam stuff needs fixing, as well as the permission fix for plugdev group.

---

### Post by Tuxmaniak on 2009-05-16
I am used this howto to make the fingerprint reader in my "HP TX2650ED" work... its just fine now.

I can login and unlock the computer from the screensaver... i can use it to install software and update the computer without needing a password... but 2 things do not work at all..

- when i wish to change to time&date settings and wish to unlock the interface with the "unlock" button... everything hangs and minutes later it fails and says "unable to authenticate" eventhough i swiped my finger 10 times or more.

- The same happens with the gnome network manager, whenever i need to authenticate myself as the root it hangs for minute on end an doesn't unlock the interface at all.

I am using the 64bit version of Ubuntu 9.04... any suggestions ?

---

### Post by baily-jane on 2009-06-24
sudo_fprint_demo works grrrrrreat, but when i try fprint_demo it goes to the screen where i would enroll my prints, but it won't let me enroll them, the buttons are just gray...

What did i do wrong? i tried the troubleshoot directions that were given in the beginning, but that didn't work either... and it says 

[COLOR=Red]Error opening directory in my home folder...

Permission DENIED!

[COLOR=Black]and then after that is won't let me do anything in terminal. 

Any help would be greatly appreciated. 
[/COLOR][/COLOR]

---

### Post by andreselsuave on 2009-06-26
Ok, this is driving me crazy.. 

I enroll my fingers with fprint_demo, but when I try to validate any of them, even though the program detects ~20-30 minutiae, validation fails 19 out of 20 times. What am I doing wrong?

Edit:

Nevermind, I think I figured it out

---

### Post by tgeer43 on 2009-06-29
> **andreselsuave said:**
> Ok, this is driving me crazy.. 

I enroll my fingers with fprint_demo, but when I try to validate any of them, even though the program detects ~20-30 minutiae, validation fails 19 out of 20 times. What am I doing wrong?

Edit:

Nevermind, I think I figured it out

Well, gee... thanks for sharing the solution with us. :sad:

---

### Post by andreselsuave on 2009-06-29
Oh! Sorry, I forgot to post the solution, yeah ^_^. For sure I will share it with you. But it is not a software problem. 

The problem is that it is difficult to validate the fingers. My fingerprint reader is Authentec. The problem was that fprint recognized it 1 out of 20 times, and it was driving me mad.

Now I have improved it to 1 out of 4-5 times. The thing is that when u scan your finger you have to try to swipe it in the same angle, with the same speed, and applying the same pressure as you did when you enrolled it. It is a bit annoying, but I imagine that with practice I will be able to succeed validating it everytime.

Thats it =)

---

### Post by tgeer43 on 2009-07-03
Is it an Authentec AES2501? That's a fairly common model and what I have in my HP notebook. But in my case the validation is extremely accurate and I wasn't even fussy about how I enrolled my digits and I don't have to be particular when swiping them day to day.
This may sound overly simple but have you tried cleaning the scanning surface? I don't think it's any inherent problem with the design of the reader.

tgeer

---

### Post by andreselsuave on 2009-07-05
Hmm, I haven't :/

Do you know what to clean it with? Maybe alcohol or distilled water?

thankyou

---

### Post by master_kernel on 2009-07-22
Updated the post. Added aes2501-wy driver requisite.

---

### Post by master_kernel on 2009-07-22
> **baily-jane said:**
> sudo_fprint_demo works grrrrrreat, but when i try fprint_demo it goes to the screen where i would enroll my prints, but it won't let me enroll them, the buttons are just gray...

What did i do wrong? i tried the troubleshoot directions that were given in the beginning, but that didn't work either... and it says 

[COLOR=Red]Error opening directory in my home folder...

Permission DENIED!

[COLOR=Black]and then after that is won't let me do anything in terminal. 

Any help would be greatly appreciated. 
[/COLOR][/COLOR]
I need the exact output.

---

### Post by Zuke24 on 2009-08-03
This is awesome, and seems to be working great for me!

I only have two issues;
1) In the Gnome GUI, it's not always prompting me for a fingerprint.  This wouldn't be an issue, except it's no longer prompting me for a password either.  This isn't an issue in Terminal where it prompts for a fingerpring from Upek FingerPrint Reader (how exact it is!).  If I can remember everything I need privileges for, it's not a huge issue; "Hmm, Synaptics isn't opening, and I know it usually asks for a password, so I'll scan the next time I open it."

How can I get this prompt back?

2) The keychain doesn't seem to go off the common-auth.  When I first start up, I'm immediately met with a prompt to unlock the keychain.  My fingerprint doesn't cut it.  Is there a way to bypass this?

I'm using 64-bit Jaunty with the latest daily builds.  I have a Lenovo X61 and a Upek Finger Scanner.  Thanks!

---

### Post by pitbullthe1st on 2009-10-11
Hi,

I have a question, I have installed this and it all seams to work fine but is there a way to get the finger prints to save in a different place? As I have an encrypted home dir and therefore when I login it says it can't find a finger print image.  However after login it works from stand by and in terminal and like it should in everything else that I have tried if in. 

Is there a work around for this?

P.S. I'm using Ubuntu 9.10 alpha6 on a dell XPS M1530

---

### Post by emilianbogatu on 2009-10-16
run as root ("sudo -s" in terminal): chown -R $your_username:$your_username /home/$your_username/.fp*

---

### Post by pitbullthe1st on 2009-10-16
How will this work?   From what I understand this will change the permission of any file/folder starting with '.fp' but before I log in, this is encrypted and therefore not accessible until it is decrypted.

Am I right in this assumption and if not then how will it work?

---

### Post by emilianbogatu on 2009-10-16
Indeed. The files should be available before decryption.
To my knowledge you can (1) use a whole encrypted partition (probably mounted in $HOME=/home/yourusername only after succesfull login) or (2) use directory/files encryption.
(1) I'll asume the mounting point is $HOME=/home/yourusername. Before proper auth, $HOME probably is empty. Just copy .fp* directory (and maybe other needed files) from mounted encrypted fs elsewere, unmount this fs and copy .fp* under $HOME (should be empty if encrypted fs is not mounted) and give proper rights. Dirty but should work; after auth encrypted fs is mounted other existent files, before auth the needed files will be available on the same path.
(2)If some kind of directory encryption is used (not a whole encrypted partition mounted on $HOME) you should not encrypt the entire $HOME.
But ... if you are using encryption - really sensitive information I guess - looks like you are giving direct access to your files based on fingerprint?!

---

### Post by bjo101 on 2009-10-20
Is there a way to configure fprint so that it asks me for my password if I can't provide a fingerprint.  I tend to login to my laptop remotely when I'm not home and their is no fingerprint device on the remove computer,.  Please tell me what lines to add to common auth and where to add them.

Thanks in advance.

Using Ubuntu 9.10 Karmic beta.

---

### Post by yknivag on 2009-10-20
> **bjo101 said:**
> Is there a way to configure fprint so that it asks me for my password if I can't provide a fingerprint.  I tend to login to my laptop remotely when I'm not home and their is no fingerprint device on the remove computer,.  Please tell me what lines to add to common auth and where to add them.

The answer is in the first post of this thread at point 4.

---

### Post by bjo101 on 2009-10-20
Thank you for the response, however the post you refer to only defaults to the password if the attempt fails with the fingerprint like entering the wrong fingerprint.  Is there a way to send a signal though the keyboard to bypass the fingerprint attempt and ask for the password,  Possibly a timeout for finger scan.  As I said I want to be able to get full access from remote machines with VNC that don't have a fingerprint reader on them.

Thanks in advance.

---

### Post by yknivag on 2009-10-20
If you set ```
auth required pam_fprint.so
``` then you can only log on with a fingerprint. If you use ```
auth sufficient pam_fprint.so
``` then the system will allow you to use a password instead.

---

### Post by bjo101 on 2009-10-24
Plese disregard my last post I have since configured thinkfinger, which gace me the desired features.

Thanks for the help.

---

### Post by ioio82 on 2009-11-14
Hello@all

this is what happened to me:

I set up fingerprint with a digitalpersona device.
Everything went fine, till I had difficulties at my finger getting recognized.

I edited /etc/pam.d/common-auth and commented out all references to auth sufficient pam_fprint.so.

Now my system won't let me login anymore with the password.

Not with the new login manager, neither through the terminal.

Does anybody have a solution? I did not change my user password.

Thank you.

---

### Post by xyepblra on 2009-12-05
Good day to everyone!
I followed the installation instructions and this process went nice and smooth untill```
xyepblra@hp:~$ pam_fprint_enroll
This program will enroll your finger, unconditionally overwriting any selected print that was enrolled previously. If you want to continue, press enter, otherwise hit Ctrl+C

No devices detected.
```
But device IS THERE, because:
```
xyepblra@hp:~$ lsusb
Bus 003 Device 002: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader

```Any suggestions?

---

### Post by xyepblra on 2009-12-07
> **xyepblra said:**
> But device IS THERE, because:
```
xyepblra@hp:~$ lsusb
Bus 003 Device 002: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader

```Any suggestions?Device is not supported...

---

### Post by Nakebod on 2009-12-08
Maybe a stupid question, but I haven't found the answer in this tread:
Is it possible to change the finger in the login screen?
So far it is always asking me for my left middle finger, and I'd prefer to (always) use my right index finger for authentication.

---

### Post by nikhilbhardwaj on 2009-12-17
great howto

works with karmic x64 too

but now it asks me for the fingerprint scan
and then the password

i'd like it to not ask for the password if the fingerprint scan is successful

here's my pam.d/common-auth

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth    sufficient                      pam_fprint.so 
auth    [success=1 default=ignore]      pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
```

---

### Post by nikhilbhardwaj on 2009-12-18
> **Nakebod said:**
> Maybe a stupid question, but I haven't found the answer in this tread:
Is it possible to change the finger in the login screen?
So far it is always asking me for my left middle finger, and I'd prefer to (always) use my right index finger for authentication.

you can swipe any finger that you have enrolled
not necessarily the one it says

---

### Post by nikhilbhardwaj on 2009-12-19
ok
got it
had to comment out the default line

---

### Post by RedHand on 2009-12-22
Hi.
I have a problem with fprint.
Generally it works fine. But!
In gdm screen I click on my username and there is a text: "Could not locate any suitable fingerprints matched with available hardware."
So I followed troubleshooting and... it didn't work... :/
But! :-)
When I login with my password and do something that requires fprint it works fine /sudo something/.
Weird.
But! :D
I login in console /ctrl+alt+f1/ with my username and password /again could not locate fingerprint/ and switched to gdm. Clicked on my username and wow! "Scan right index finger on AuthenTec AES1610"
I swiped and logged on.

Could someone help me? :-)

/sorry for my english/

---

### Post by richwillal on 2010-01-08
> **RedHand said:**
> Hi.
I have a problem with fprint.
Generally it works fine. But!
In gdm screen I click on my username and there is a text: "Could not locate any suitable fingerprints matched with available hardware."
So I followed troubleshooting and... it didn't work... :/
But! :-)
When I login with my password and do something that requires fprint it works fine /sudo something/.
Weird.
But! :D
I login in console /ctrl+alt+f1/ with my username and password /again could not locate fingerprint/ and switched to gdm. Clicked on my username and wow! "Scan right index finger on AuthenTec AES1610"
I swiped and logged on.

Could someone help me? :-)

/sorry for my english/

Is it possible that you installed with an encrypted home directory?  If so this make sense as nothing has allowed the decryption of your home until you have logged in once.  (I may have misunderstood your issue, though.)  If that's the case, I'm not sure what the resolution is, but that might help identify a work-around.

---

### Post by richwillal on 2010-01-08
Thanks for the HOWTO.  It worked for me on Karmic x86_64 with an AES2501.

I'm fairly new to configuring PAM, and I'm having one issue I haven't resolved yet.  Is there a way to specify that fprint should only be allowed to authenticate a local user?  I ssh into my box over a local network sometimes, and it doesn't make much sense to have to walk into the room to scan my finger.

I believe I've seen this before, and I could add a copy of common-auth named common-auth-no-fingerprint with fprint removed for inclusion in the /etc/pam.d/sudo file, but it would make more sense to force fprint authentication to always fail for a remote user.

Thanks for any suggestions.

---

### Post by defaria on 2010-01-31
> **xyepblra said:**
> Device is not supported...

Any idea of when it will be supported. I also have a DigitalPersona but the codes aer 138a and 0005.

---

### Post by theadictspunk on 2010-02-06
> **nikhilbhardwaj said:**
> you can swipe any finger that you have enrolled
not necessarily the one it says

I tried swiping a different finger... no luck. has to be the one it says...

---

### Post by Tompalaz on 2010-02-09
Thank you for this guide, it worked great.:p

I've got a somewhat off topic question.
If I would like to integrate this in a python program, what should I do.
What files are needed?

I looked at the gksu.py file to find out but it didn't give me much.

---

### Post by faizyunus on 2010-02-18
Thanks. It really works. Even for login, sudo and i must say it is impressive. Great job. I followed every instruction carefully and hooray it works!!:D:D:D!. TQ SO MUCH. Here is one of the screenshots.
[IMG]http://i375.photobucket.com/albums/oo196/faizyunus/Screenshot.png[/IMG]

---

### Post by flair-kun on 2010-02-21
Thanks for this guide it works great!

But i have a problem, i HAVE to use a fingerprint authentication now to login. Is there no way where i can use either the fingerprint authentication or the password?

---

### Post by webbuddy on 2010-04-05
> **Paresh said:**
> This worked for me, if I ran ```
sudo fprint_demo
``` but if I ran just ```
fprint_demo
``` It would not work.

I tried the workaround of adding my user to the plugdev group and the I got ```
error loading enrolled prints
```This turned out to be because the /home/user/.fprints directory was owned by root, so I did ```
sudo chown -R $USER /home/user/.fprints
``` it started working.

Is this correct, or have I opened a security hole?


Although fprint_demo works on my Tecra A9, it does report a couple of errors while scanning or verifying
```

upekts:error [read_msg] non-zero bytes in cmd response
upekts:error [read_msg28] expected response, got -1 seq=0

```Both messages are produced for each action.

I get this every time the scanner is used, eg verifying your finger and enrolling your finger produce this error, but deleting a fingerprint file does not.  Also on enrolling, I only get the error once, not three times.

Thanks for the tip, I had the same issue
 
```
error loading enrolled prints
```

and I fixed it using your tip 

 ```
sudo chown -R $USER /home/user/.fprints
``` 
 but found what I think was a typo and it should read
 ```
sudo chown -R $USER /home/user/.fprint
``` 

I also found that I had a better success verifying with a lesser used (worn) finger

I too however am concerned about security issues with chown of that folder.

---

### Post by Melk79 on 2010-05-10
There are some threads, like this one, I keep referring back to get things working the way I like.  These instructions still held true for Kubuntu Lucid with a little help from [here]("http://knowledge76.com/index.php/Fingerprint_Reader_Usage") to find the right spot to add the change to common-auth using the directions under Ubuntu 9.04.  You still don't really get a dialog, except in the terminal, but it works! Software Management just asked for my password and instead I swiped the finger... it worked.  Security flaws aside, the laziness in me likes the fingerprint reader.

---

### Post by ubun7u on 2010-06-23
hello everyone.
fprint worked for me fine but the thing gksu.py screwed my gksu
plz help.here is i get
```
gksu update-manager
Traceback (most recent call last):
  File "/usr/local/bin/gksu", line 26, in <module>
    import gtk, gksu2
ImportError: No module named gksu2

```

---

### Post by Tech2077 on 2010-06-26
I set this up, it worked perfectly for a few boot-ups, then when I logged in once, i could log in through scanning, but everything once i log in stops working with it and i get this error message:

```

Found device claimed by AuthenTec AES1610 driver
aes1610:error [dev_init] could not claim interface 0
fp:error [fp_dev_open] device initialisation failed, driver=aes1610
Could not open device.

```

---

### Post by anotherlinuxuser on 2010-08-04
this worked like a charm  :)

---

### Post by BryanFRitt on 2010-08-05
Definitively back up the original [FONT="Courier New"]/etc/pam.d/common-auth[/FONT] file BEFORE messing with it. You might not be able to log in after reboot, if something is messed up. (and have to find/restore the file from a 'live-cd'... like I did, even though it seemed to work before reboot (tested with `[FONT="Courier New"]qdbus org.kde.krunner /ScreenSaver Lock[/FONT]`*)) *fprint* is only version number [FONT="Courier New"]0.2-3[/FONT] with some parts that are [FONT="Courier New"]0.0.6-2[/FONT], ...

*Not a safe way to test, could get locked out and not be able to log in! It might be better to use a `[FONT="Courier New"]sudo visudo[/FONT]` and add '[FONT="Courier New"], timestamp_timeout=0[/FONT]' to the '[FONT="Courier New"]Defaults[/FONT]' line, and pick a different command to try `[FONT="Courier New"]sudo[/FONT]` with.
[http://ubuntuforums.org/showthread.php?p=113137](http://ubuntuforums.org/showthread.php?p=113137)

---

### Post by Kixtosh on 2010-08-06
My main laptop is a Toshiba Portégé R205. This uses an Authentec AES2501 fingerprint reader. I think there may have been an "a" version and a "b" version of this:

[http://www.authentec.com/products-pcsandperipherals-aes2501b-spec.cfm](http://www.authentec.com/products-pcsandperipherals-aes2501b-spec.cfm)

Anyway, the Portégé is not listed in the link to "supported devices" at the start of this thread. In fact, there's only one Toshiba in that list, but, the AES2501 is listed more than any other device (in a couple of Fujitsu-Siemens machines, a Lenovo, and a whole bunch of HP machines). Can anyone tell me whether this means:

A) It is likely the AES2501 in my Toshiba will work with Ubuntu.
B) It's impossible to say whether the AES2501 in my Toshiba will work with Ubuntu or not.

I'd love to install some flavour of Xubuntu, Lubuntu or Peppermint on that R205, since it's by far the laptop I use the most.

Any help would be greatly appreciated (and you'll probably also get straight into heaven for being nice to me when the time comes)!

---

### Post by BryanFRitt on 2010-08-06
Software review...

I got my finger print reader working following advice from the thread you're reading now ([http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)) and [https://launchpad.net/~fingerprint/+archive/fprint](https://launchpad.net/~fingerprint/+archive/fprint) etc... 

Installed:
fprint-demo 1:0.4+git20080303-0~ppa2~lucid1 (lucid)
fprintd 0.0.0+git20090124-0~ppa3~lucid1
libfprint-dev 0.1.0~pre2-1ppa1~lucid1
libfprint-doc 0.1.0~pre2-1ppa1~lucid1
libfprint0 0.1.0~pre2-1ppa1~lucid1
libpam-fprint 0.2+git20080330-0~ppa2~lucid1
libpam-fprintd 0.0.0+git20090124-0~ppa3~lucid1
aes2501-wy 0.1-5 (lucid)
python-pexpect 2.3-1build1 (lucid)
gksu-polkit 0.0.2+git20100506-0~ppa1~lucid1 (lucid)
polkit-kde-1 0.95.1-2ubuntu1 (lucid)
libgksu-polkit0 0.0.2+git20100506-0~ppa1~lucid1 (lucid)
etc... 
Dell Latitude D830
fingerprint reader: UPEK Eikon 0483 2016 upekts
[http://reactivated.net/fprint/wiki/Supported_devices](http://reactivated.net/fprint/wiki/Supported_devices)
lsusb
ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
I was/am a member of the plugdev group

It seams weird for login/log back in to session, sometimes I could just enter my password, sometimes I had to do both, and other times all I needed was my fingerprint. It's definitely less secure now, than before, and not any easier to use. *Is there any way to change this behavior?* So I can control if I need to use both, or one or the other, for login, and/or doing commands that require sudo/kdesudo, etc...? Being able to chose which finger(s) need to swiped for use with login/sudo/kdesudo/etc... would be nice, or being able to set it to randomly pick one(or more).

Occasionally it would freeze the password box, and I'd have to hit 'Esc' and try again. Also after a successful login I have to hit 'Esc' a few times which is kinda weird.

Sometimes kdesudo items don't work the first time now, 2nd time starting them they'll work and when using them I'd get a prompt asking for my password again, even though I can continue using the software. (?related to first thing in this paragraph?)

---

### Post by BryanFRitt on 2010-08-07
Another safety tip for installing this software...

Before you start installing and messing with this software, you might want to open everything that you might need to open to repair things if things go wrong. (like if you can't use sudo, required to fix things)
Before starting run:
[FONT="Courier New"]kdesudo kate /etc/pam.d/common-* [/FONT]& # remember to backup /etc/pam.d/common-auth
[FONT="Courier New"]kdesudo synaptic &
kdesudo dolphin &
sudo su
[/FONT]... adjust for your version of Ubuntu, preferred apps, etc...

see also my other post
[http://ubuntuforums.org/showthread.php?p=9681014](http://ubuntuforums.org/showthread.php?p=9681014)

---

### Post by BryanFRitt on 2010-08-07
> **Kixtosh said:**
> 
Anyway, the Portégé is not listed in the link to "supported devices" at the start of this thread. In fact, there's only one Toshiba in that list, but, the AES2501 is listed more than any other device (in a couple of Fujitsu-Siemens machines, a Lenovo, and a whole bunch of HP machines). Can anyone tell me whether this means:

A) It is likely the AES2501 in my Toshiba will work with Ubuntu.
B) It's impossible to say whether the AES2501 in my Toshiba will work with Ubuntu or not.


Try `[FONT="Courier New"]lsusb[/FONT]` and look at the device code section for your fingerprint reader, and compare those numbers to the 'USB Vendor ID' and 'USB Product ID' columns on [http://reactivated.net/fprint/wiki/Supported_devices](http://reactivated.net/fprint/wiki/Supported_devices) to see if your device is 'supported'. My _*guess*_ is that as long as those values match, you're 'supported'.

---

### Post by kitor on 2010-08-07
Well I have Lenovo 3000 N100 notebook with AuthenTec AES2501 fingerpint reader (08ff:2580). I'm using Debian Squeeze amd64, but hope that it's similar to Ubuntu.

The problem is that fprint_demo and pam_fprint_enroll doesn't read my fingerprint. They just stop on finger scanning dialog. Sensor is working - aes2501 demo program shows me my fingerprint. Any ideas what is the problem?

---

### Post by Kixtosh on 2010-08-07
> **BryanFRitt said:**
> Try `[FONT=Courier New]lsusb[/FONT]` and look at the device code section for your fingerprint reader, ...Thanks Bryan, I'll do that later (I'm not quite ready to try even a LiveCD on this laptop yet, since I don't want anything to get messed up).
 
I'm a bit concerned by the problems you are having, since I rely a lot on my fingerprint reader with Windows for security AND convenience, including booting up, logging on and managing sensitive website accounts. If it's going to be as quirky as what is happening to you, then I won't be keeping it for long, and there would be no point in me installing Ubuntu at all on this particular machine.

---

### Post by BryanFRitt on 2010-08-07
> **Kixtosh said:**
> Thanks Bryan, I'll do that later (I'm not quite ready to try even a LiveCD on this laptop yet, since I don't want anything to get messed up).
 
I'm a bit concerned by the problems you are having, since I rely a lot on my fingerprint reader with Windows for security AND convenience, including booting up, logging on and managing sensitive website accounts. If it's going to be as quirky as what is happening to you, then I won't be keeping it for long, and there would be no point in me installing Ubuntu at all on this particular machine.

It's that weird, I suspect a lot of the problem I had, had to do with the /etc/pam.d/common-auth, and maybe other files in /etc/pam.d/*. 

At least it didn't cause any problems with my 'pre-boot' fingerprint reader. I don't think this software has any effect on that. In fact, I think that part still has to be set up from Windows.(but I could be wrong)

After seeing your post I decided to try out the fingerprint reader in my Windows Vista partition. I hardly ever use it. I think it wasn't working before I started messing with this Linux fingerprint reader software.(aka this Linux software had no effect) The fingerprint reader in Windows didn't work, and I couldn't get it working. I remember a long time ago trying to get it working in Windows, and I actually gave up on it, and one day, I randomly decided I try again, and with not much effort it started working, and I set up the fingerprints for the BIOS etc... This time I tried doing Windows 'program' repair feature, and it didn't work. This seams to be the same problem I had when I first tried to install the Windows version finger print reader. I'm not going to try to get it fixed anymore. I don't use Windows that much anymore, and if I do I use 'Wine' or 'VirtualBox' (maybe even DosBox, or DosEMU). *In summary the 'pre-boot' fingerprint reader can still work, if it's set up, even if Linux/Windows use of the finger print reader is messed up.*

p.s. Running 'Live CD' won't mess anything up, unless you decide to install, or mess with the partitions on the harddrive(s), etc...

p.s.2. I decided to uninstall my Linux's fingerprint reader software. Since I still have use of my BIOS's 'pre-boot' fingerprint reader, I set up my computer to ask for a fingerprint everytime the computer gets shutdown, rebooted, suspended, hibernated, etc...  This way someone has to cheat my fingerprint reader, and know my OS password, to use my computer setup in those cases, and the OS won't be so awkward with passwords, and fingerprints.

---

### Post by Kixtosh on 2010-08-08
> **BryanFRitt said:**
> ... At least it didn't cause any problems with my 'pre-boot' fingerprint reader. I don't think this software has any effect on that. In fact, I think that part still has to be set up from Windows.(but I could be wrong) ...Bryan, I just use the BIOS enabled password for that (when I travel) ... which protects only the laptop itself, I suppose, in case of theft, since you could still remove the hard drive and access any unprotected data. I've always assumed the BIOS pre-boot password is difficult to reset when activated ... hopefully impossible without proof of purchase! In any case, it doesn't need any O.S. at all to be activated.
 
> After seeing your post I decided to try out the fingerprint reader in my Windows Vista partition. ...Bryan, I'm really only stuck with Windows because of TomTom and Garmin at the moment (and the fingerprint reader, if it turns out it doesn't work properly), but if I can get this to work, I'll use them on a different dual boot machine. 
 
Just for your information: my newer Portégé uses WinXP, but Windows doesn't manage my fingerprint reader at all (I'm not sure that XP ever could do this). I currently use software within XP from Softex Inc. called OmniPass.
 
_[COLOR=#810081][http://www.softexinc.com/category.asp?category=secsolutions](http://www.softexinc.com/category.asp?category=secsolutions)[/COLOR]_
 
> ... p.s. Running 'Live CD' won't mess anything up, unless you decide to install, or mess with the partitions on the harddrive(s), etc... I know that this is the theory, but on my older Portégé, I first tried Knoppix in 2004. When I first set it up, it would show the CPU correctly as 700MHz, but after a second or third try from LiveCD, it suddenly started to show it as 500MHz, and it's been stuck there ever since, regardless of O.S.
 
I don't know if there could have been a problem with Knoppix not controlling the fan correctly and causing the CPU to malfunction as a consequence or something, but I don't want to risk it again until I have bought a new replacement.

---

### Post by dinomight on 2010-08-25
The tutorial is great. but i'm having the problem where it still asks for a password even if it successfully authenticates with the fingerprint. I'm sure it has something to do with the pam but i can't figure it out. Any help?```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.
auth sufficient pam_fprint.so
# here are the per-package modules (the "Primary" block)
auth	[success=2 default=ignore]	pam_unix.so nullok_secure
auth	[success=1 default=ignore]	pam_lsass.so try_first_pass
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

---

### Post by Kixtosh on 2010-09-08
I finally got Ubuntu 10.04, Lucid Lynx installed on my R205-S209 as mentioned earlier. The instructions in the first post in this thread worked perfectly (thank you!). I have not implemented usage for logging in, however, since it seems to take too many tries to verify the print after enrolling as described in step 2. I used the GUI method, where a specific tab allows you to verify your prints and see if they match up to the initial scan. In Windows, using Softex OmniPass software, a scan is usually recognized on the first attempt for logging in. 

OmniPass also allows you to use the reader to remember user ID's and passwords for browsing, such as the ones used for this forum. I have not seen where Ubuntu and fprint-demo would allow one to do this. Perhaps it's not really needed, since Ubuntu is more secure by reputation in the first place, and a browser such as Firefox will encrypt remembered profiles information (unlike Chromium, which does not encrypt the information, apparently). In this way, the fingerprint reader could function simply to enable ease of access when starting up, or returning from standby, and everything else to do with internet logon information could be saved by Firefox instead.

I'm going to practice some more swiping later, and post back.

The model used in this laptop is the AuthenTec AES2501, by the way.

A new application entry, "fprint-demo", is now present in the "Accessories" section of the main "Applications" menu in Ubuntu (accessible with ALT+F1, for new users such as myself).

---

### Post by Kixtosh on 2010-09-09
> **dinomight said:**
> The tutorial is great. but i'm having the problem where it still asks for a password even if it successfully authenticates with the fingerprint. I'm sure it has something to do with the pam but i can't figure it out. Any help? ...There have been a few posts about similar problems in this thread (and yes, I've read the whole thing at least twice!). Did you notice this earlier post? **[http://ubuntuforums.org/showpost.php?p=6709538&postcount=50](http://ubuntuforums.org/showpost.php?p=6709538&postcount=50)**. Here's an excerpt:

> When there is auth required, my computer asks me always to enroll my finger AND to insert a password. When I change it to auth requisite, it only asks me my password if the fingerprint authentication failes.You seem to have both the "requisite" and "required" lines. Could this be your issue? Maybe you can see if the author's solution can work for you too. He also posted ```
auth requisite pam_unix.so nullok_secure
```where you have ```
auth	requisite			pam_deny.so
```
If I ever get that far, I'll post my working configuration later.

---

### Post by Kixtosh on 2010-09-09
> **BryanFRitt said:**
> Try `[FONT="Courier New"]lsusb[/FONT]` and look at the device code section for your fingerprint reader, and compare those numbers to the 'USB Vendor ID' and 'USB Product ID' columns on [http://reactivated.net/fprint/wiki/Supported_devices](http://reactivated.net/fprint/wiki/Supported_devices) to see if your device is 'supported'. My _*guess*_ is that as long as those values match, you're 'supported'.I think Bryan was bang on target here: now that I have Ubuntu installed on my newer Portégé, and was able to type  "*lsusb*" in Terminal, the AuthenTec **AES2501** is listed as **08ff:2580**, which is an identical value for this reader for every device in the list of supported hardware/laptops. The laptop brand doesn't actually matter, as explained in the document that Bryan pointed to earlier with this link.

[https://launchpad.net/~fingerprint/+archive/fprint](https://launchpad.net/~fingerprint/+archive/fprint)

---

### Post by mmmiiikkkeee on 2010-09-21
for the people having trouble getting this guide to work with only only fingerprint or only password (not BOTH) please read this page the packages on it got it working for me :) :

[https://launchpad.net/~fingerprint/+archive/fprint?field.series_filter=maverick](https://launchpad.net/~fingerprint/+archive/fprint?field.series_filter=maverick)

it also explains why pam has to ask for fingerprint first, and then a password if that fails

---

### Post by Kixtosh on 2010-09-21
Well, I'm still in the test phase of using this, so I have not enabled it at all so far (I don't use it to log in, or for anything else at present).

Scanning can be very tricky, much more quirky than when using OmniPass with Windows XP, but here is how I seem to have found a working method:

- Your fingerprint is read by a swipe over the reading device (you do NOT just place your finger on it and wait for a reading to happen).

- The angle and method of approach seems crucial to accurate reads, far more so that I am used to with Windows XP and OmniPass.

- Start with your knuckle hovering over the device, but not on it, nor with your finger too close to the reader (I mean the big knuckle joint nearest to your hand, not the little one nearest the finger nail).

- Swipe your finger toward you, but not too quickly, and let whole length of the tip slide across the surface of the reader and right off the reader completely. The whole read, for knuckle to tip, should take about two seconds.

- The best angle seems to be about 10° or so. If the angle is too steep, such as 45°, you _will_ get a good reading, but you _will probably not_ be able to verify it afterwards, not even with ten or more tries, so it's basically useless to you! If the angle is too shallow, such as 5° or less, your finger may be too close and may sometimes prompt an error message before you even finish your swipe movement.

- With a little practice, first enrolling your finger, then verifying the scan, you should get a verified read that matches at least 90% of the time.

_Note:_ From what I have read (somewhere from a trusted source, but I can't hunt down the reference just now), there is no point in using more than one finger, since for the moment, only the first finger enrolled will be used for authentication.

Edit: adding some images of the process!

---

### Post by Kixtosh on 2010-09-21
And here, for good measure, is the verification process, as well as the location in the Applications Menu:

---

### Post by Mikafar on 2010-11-22
Thank you, I came here because I had the same segfault with my X360, and your
hint was very helpful. It actually takes some training until scanning works, especially when your suffer from dry hands (like me); even when my fingers were scanned for an official ID card, it took a while, and I had to moisture them to make it work.

The Segfault, however occurs delayed if you are within identify tab; hence I could imagine that it is an error in the demo software, when the data is processed (some division by zero for all-white images or so). Is there a bug report on this so far?

I have to find further instructions to test fprint from other applications before using it for PAM. (And while typing I would be glad if I could auto deactivate the touchpad)...

CHeers!
MF:popcorn:

> **ickyb0d said:**
> So I think I found out why the segmentation faults were happening.  My friend actually has the exact same computer (and print reader) as well as the same version of ubuntu, but he didn't experience any seg faults.  Anyways the conclustion we came to was this:

When scanning a print, you absolutely **have to** *swipe your finger* across the reader.  Place the bottom of your "print" at the top of the reader, and drag it across (top to bottom) until the top of your "print" passes over the reader.  Think of it like a scanner that scans from one end of a page to the other.

The way I was getting the seg faults was just putting my finger on the reader and removing it.  I have no idea why it seg faulted, but apparently using the print reader correctly fixed it :).  So all in all, everything is working fine for me now.

[EDIT]I tried to trace the segfault using "strace". It was very hard then, to cause a segmentation fault - maybe a timing problem? After several trials, I triggered one, resulting in these lines of output:

ioctl(4, USBDEVFS_REAPURBNDELAY, 0x7fff59ae7058) = -1 EAGAIN (Resource temporarily unavailable)
select(5, NULL, [4], NULL, {0, 1000})   = 1 (out [4], left {0, 269})
ioctl(4, USBDEVFS_REAPURBNDELAY, 0x7fff59ae7058) = 0
write(2, "aes1610:warning [capture] ", 26aes1610:warning [capture] ) = 26
write(2, "swiping finger too slow?", 24swiping finger too slow?) = 24
write(2, "\n", 1
)                       = 1
mremap(0x7ff28ca9d000, 540672, 4096, MREMAP_MAYMOVE) = 0x7ff28ca9d000
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

[/EDIT]

P.S.: My versions used
fprint-demo 20080202-2ubuntu1
libfprint0     0.0.6-2ubuntu2
kernel         2.6.31-22-generic #63-Ubuntu SMP Thu Aug 19 00:23:50 UTC 2010 x86_64 GNU/Linux

---

### Post by Naaktgeboren on 2011-04-23
Packages with fprintd, adding seamless fingerprint authentication integration into Ubuntu, can be found in this PPA:

[https://launchpad.net/~fingerprint/+archive/fprint]("https://launchpad.net/~fingerprint/+archive/fprint")

---

### Post by defaria on 2011-04-24
'Cept, last time I checked it doesn't work with my hardware so it's basically useless.

---

### Post by joel.markshalayenka on 2011-04-24
lsusb shows my fingerprint reader to be a Digital Persona Inc. device.

After following install routine outlined above, fprint_demo displays: Status: No Device Found.

Reader is in the palm rest of an HP ProBook 4520s (Intel i3).

Very sad :( I really hoped this would work...
...and it looks like fprint is not developing drivers since 2008. I really wish Canonical would take this issue up. Corporate laptops often use fingerprint readers and it would be a huge feather in Ubuntu's cap to have good fingerprint support!

---

### Post by aeronutt on 2011-05-09
> **joel.markshalayenka said:**
> lsusb shows my fingerprint reader to be a Digital Persona Inc. device.

After following install routine outlined above, fprint_demo displays: Status: No Device Found.

Reader is in the palm rest of an HP ProBook 4520s (Intel i3).

Very sad :( I really hoped this would work...
...and it looks like fprint is not developing drivers since 2008. I really wish Canonical would take this issue up. Corporate laptops often use fingerprint readers and it would be a huge feather in Ubuntu's cap to have good fingerprint support!

Agreed. Same problem, digitalpersona on my laptop. No workie.

---

### Post by Rikki123s on 2011-07-13
I am getting a rather unusual error on my computer for fprint. I have just install 11.04 and when I try to enroll using fprint_demo, the awaiting finger swipe window appears and the bar moves from left to right (as it should do), but when I attempt to enroll on my reader, it continues to display same attempt (1 of 3), does not acknowledge that I have swiped and continues to wait for me to swipe.

After doing this, I decided to use the command pam_fprint_enroll, I get this error:

  rik@rik-VGN-TX3XP-B:~$ pam_fprint_enroll
  This program will enroll your finger, unconditionally overwriting any selected print that was enrolled previously. If you want to continue, press enter, otherwise hit Ctrl+C

  Found device claimed by UPEK TouchStrip driver
  Opened device. It's now time to enroll your finger.

  You will need to successfully scan your Right Index Finger 3 times to complete the process.

  Scan your finger now.
  Enroll failed with error -22

does anybody else get this Error -22? how do I fix it, I'm guessing this is what is breaking the application and stopping me from enrolling.

I may add that upon first installing fprint, the first attempt at enrolling worked, but I accidentally enrolled my right index finger as my left thumb, so I deleted it and it has not worked since

---

### Post by pitbullthe1st on 2011-07-13
> **Rikki123s said:**
> I am getting a rather unusual error on my computer for fprint. I have just install 11.04 and when I try to enroll using fprint_demo, the awaiting finger swipe window appears and the bar moves from left to right (as it should do), but when I attempt to enroll on my reader, it continues to display same attempt (1 of 3), does not acknowledge that I have swiped and continues to wait for me to swipe.

After doing this, I decided to use the command pam_fprint_enroll, I get this error:

  rik@rik-VGN-TX3XP-B:~$ pam_fprint_enroll
  This program will enroll your finger, unconditionally overwriting any selected print that was enrolled previously. If you want to continue, press enter, otherwise hit Ctrl+C

  Found device claimed by UPEK TouchStrip driver
  Opened device. It's now time to enroll your finger.

  You will need to successfully scan your Right Index Finger 3 times to complete the process.

  Scan your finger now.
  Enroll failed with error -22

does anybody else get this Error -22? how do I fix it, I'm guessing this is what is breaking the application and stopping me from enrolling.

I may add that upon first installing fprint, the first attempt at enrolling worked, but I accidentally enrolled my right index finger as my left thumb, so I deleted it and it has not worked since

Not sure but it could be priverlage try using sudo as Pam is protected by root.  Just an I dear not to sure if it will work but that's what I would try first. Hope it helps

---

### Post by o771 on 2011-11-02
@Kixtosh: You've considerably more patience than I. Although fprint installs and integrates nicely with 11.10 on my Samsung X360 with an aes1610, I found the recognition rate to be so poor as to make it unusable; so I've disabled fprint.

My previous experience of fingerprint recognition is under XP on a Thinkpad where recognition worked flawlessly every time, so my expectations of fprint were high. 

I was surprised that fprint enrollment only required a single swipe. Is there some way to enroll using multiple samples so it has better data against which to perform recognition? Or can someone suggest some other reason why the recognition rate is so poor? 

I'd be interested to know if anyone is using fprint for real? Especially if it's on an X360. I'd love to get this working but, as things stand, it doesn't seem to me to be ready for production use.

---

### Post by fat yak on 2011-11-02
Followed link above [https://launchpad.net/~fingerprint/+archive/fprint]("https://launchpad.net/%7Efingerprint/+archive/fprint") and it worked perfectly. Although it said in 11.10 you would have to use terminal, mine scanned in GUI.

---

### Post by dog-soldier on 2012-04-13
i just installed this on my Fujitsu t4210 and it works great. thanks=D>

i followed the instructions on this page [http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html](http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html)

---

### Post by dog-soldier on 2012-04-15
ok so after adding another account on my tablet pc is there away to add a 2nd set of prints to make it more secure ?

---

### Post by phinpup on 2012-12-26
OMG Thanks for this, had some trouble at first, had to reboot into recovery mount drives then drop to shell to undo the changes to the file and reset password then tried again and realized I was only supposed to put the command above all of the other code in the auth config file, now it works fine!

Also did the gksu patch successfully and I am on Linux Mint 12 64-bit.

---

### Post by JonDeen on 2012-12-26
> **pmontrasio said:**
> I can't run aes2501 on my HP nc8430, ubuntu 8.10 amd64.
Here are the details:

$ lsusb
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor

$ sudo apt-get install aes2501-wy
$ sudo apt-get install libfprint0 libpam-fprint fprint-demo

All went fine.

$ sudo aes2501 
argc=1 Initializing, please standby...
No device found

$ sudo fprint_demo
aeslib:error [do_write_regv] bulk write error -2
fp:error [fp_dev_open] device initialisation failed, driver=aes2501

It shows the device with a status message "Could not open the device".
Any idea? Thanks!

I have the same computer model but running Ubuntu 12.10 x86.

aes2501 command:
```

***@jdeen-hp:~$ aes2501 
argc=1 Initializing, please standby...
aesSetup()...
aesStartScan()...
READY (touch the sensor to stop)
Scanning...
Assembling...
Segmentation fault (core dumped)

***@jdeen-hp:~$ sudo aes2501 
argc=1 Initializing, please standby...
aesSetup()...
aesStartScan()...
READY (touch the sensor to stop)
Scanning...
Assembling...
[COLOR="SeaGreen"](-finger print shows up in LXDE-)[/COLOR]
READY (touch the sensor to stop)

```

fprintd-enroll command:
```
***@jdeen-hp:~$ fprintd-enroll
Using device /net/reactivated/Fprint/Device/0
Enrolling right index finger.
[COLOR="DarkRed"](-no response from fingerprint reader-)[/COLOR]

***@jdeen-hp:~$ sudo fprintd-enroll
Using device /net/reactivated/Fprint/Device/0
Enrolling right index finger.
[COLOR="DarkRed"](-no response from fingerprint reader-)[/COLOR]
```

Gui versions act the same (as does the fingerprint-gui package from David Jurenka [https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui) ).

Please help me rescue my love for biometrics (;

//JDeen

---

### Post by layr on 2013-04-13
I understand fprint isn't quite up to being a proper authentication mechanism yet, but how come anyone could enroll his fingerprint using ```
fprintd-enroll
```

For instance - an unauthorised person finds computer in logged-in state and enrolls his prints granting him all sudo rights.

---

### Post by closer2 on 2013-04-24
can some show me exactly where to place auth    sufficient    pam_fprint.so? I've tried a few times i either get failed attempt 3 times without doing anything or don't need a fingerprint or password or it keeps asking for password.

---

### Post by JHGould5607 on 2014-02-19
I'm on Ubuntu 13.10 64bit with fingerprint reader 05ba:000a DigitalPersona, Inc. The fprint_Demo does see the device however I am unable to enroll.  It does not seem to save fingerprint images. It remains at enroll left thumb.  The enroll from the terminal seems to do the same thing.  Any ideas?  Or does anyone know where the log is?[http://i.imgur.com/86r7amb.png]("http://i.imgur.com/86r7amb.png")

---

### Post by mariusz-ciszewski on 2014-03-19
Hello all

There was a lot of time ago when this topic was created. Could someone summarize how it looks in Ubuntu 13.10:

1 Logging into Ubuntu using fingerprint ( multiple users, each with its own fingerprint ) .
The logon manager installed by default in Ubuntu 13.10 , gives you the opportunity ?


2 Where can I find information about which log manager is installed by default in Ubuntu 13.10 / 13.10 Lubuntu / Xubuntu 13.10 ?


3 Is it possible to omit entering the user name ? ( I would like Ubuntu only based on the scanned finger recognize the user and log on him )


4 Where in the most correct way I can define / execute automatically run the script /home/user/scripts/accepted.sh when you log in to the system ( the same behavior for each newly added user )


5 Where in the most correct way I can define / implement automatic start of script /home/scripts/declined.sh when your try to log on was unsuccessful ?


6 How to gather (collect fingerprints) people who have tried to authorize and were not entitled to it ?



Please also check my topic about using fingerprint in bash script:

[http://ubuntuforums.org/showthread.php?t=2211888&p=12960498#post12960498](http://ubuntuforums.org/showthread.php?t=2211888&p=12960498#post12960498)

I'm still searching for sollution for multiple users

Thank you for a feedback
Best reagrds

---

### Post by bahubali on 2014-04-14
hi i followed all steps ...when i open fprint_demo it shows No device connected..what could be the reason???and i checked my device using lsusb..my device is there in the list[IMG]http://ubuntuforums.org/;base64,iVBORw0KGgoAAAANSUhEUgAAAu4AAAH7CAIAAAAcjI0oAAAAA3NCSVQICAjb4U/gAAAAGXRFWHRTb2Z0d2FyZQBnbm9tZS1zY3JlZW5zaG907wO/PgAAIABJREFUeJzsXXecVcX1/56595XtnS20pUsXFBAVC5bYNZaosZtmii3GNBN/KZpqL7HERI0aazTYu1jAgoiACNI7y7K9v3Ln/P6Y2997uwtSFnO/n1XumzvlzJy5c86cOTND5 9zggQACAAAEcELBhORBMB2mLCfCBIZEqYFA/DGVHm5aWBmAGABgASjR7BFD8lUMnwhREQqewIAg9mOYJaemoMVxyTMIpKIiEhAvTLsPCSTu9DUtEQEM74TwU0Vm6klIAGhsmVJqjXc8YnIRxWESuw0BVv023X3tIbFWCYrT/UTKXA1L1tp7ZjEgoiYpCuBm7eumqbm7II7Z3ebOFy2slLhqT2QGIL9fGdmSQAgVL8iYmYWxMxEJisBMEv1zN32O3feRGn6sPSS5CHdqpIkJiLzu1NRyNNJiAjS6VdmfdN9aP5Onkq8UH1GAoDQ7DgSht032PUtqAcBpwu581Fd3FNuyqdH0FLpdBehapVSHZWPa4RRfBEMwD0Y2CT5ejWR5svHqqM0ezszSCMiSRJWfwAkMxNp9tcqhCAiSKcUkz44IZ4WY080OxNPm6SMRWZFSLoqIdJHdn3vxIBwlZ4uWwFiZmskEQQGSVj9yjdu GBGkP5BrBu4ujrZo5B76Oux0B5L8Q2q7tz8/dA9VnhlF6WU4RoCCQBL1W3SjJ/2mN8jeQ5rJEMNra5 QkQsJOAZ09TwK1JGR7s/d1NWaoOklkjM0ho2zYqwX3ykZu6GOf6wP6Y33D/UWZDpg1WfTBkrrH5NBKcHq1zsEFVHVa4AdDdZHqHokmXMpkLDlpZh9w2RTuR1AwmQN2dFtN0lpWRXXGC78mezaazMCJYqZhXHzCZrAWIwyKmpKdGZbKFu5ysl xmsEjKxysdilRoofa2XjlC21BRHc2GLTxYjpPqimJOWWFE8IiGEytenxzCzlZtUkd2jibvt3eFsV99LagrhUn3tQggpzWcnHwZAnKbLmgOoojxdtg6sPkbk qIsvkjPyGixiDz5gxhwiTb7O1esgq2as2RmKWFJN7a EKcNfXLXXVmCPfw5n5a75tJFkkj9jlVSQZJZApoV064jAAJYSmJJpKmuYXaqdCOXTTpZam7qQM/MwuSUosot6qyewOZn7hvM7HBFgiBiU71iq2pmElcT9fDlmrxOkUa 0iVLAklWH0K6jJg9agQrpQTOMCUYzEQgWytmBrNSj1gq5RVshat8DCmRbuC2q2omtN9a3dQd35BeDc/71tKrpFW2tyBvbd11JAZJSFjUpkp0i35LpDE7gwmr6QJSJhVCCLsbgEHQ7M9HSunL38sBU/NTMZmsXmqNZu7OkwndKDreQQzu3HyvmA0hBFz93 xlroT OqiBj8hqDwEYKi93De0HStE2BAnJknwZmy2gBhTYb0k9q3HOXQKBGNISiK66q397VmV8NDlDvSXspTuc0/dtq0HSwK2yKJ6qDuNVZTLxuHtVJiVYSWgh7C7MbHUnYgCC/FqfDkBzqZwWOZbGYuoZamiXkp05p4dyku5em6EyVkrPlBbMAoCABGC4xTOroTKl31glqjiqOCmlJoSSWHa3tqfm7u/QmotLd4 U1lyaiCQYboHM7LEVqcJdDSVNGU52c1iy1mkes1nIHhxtuc7u9lAdXDq9gQGCKSwMIs0eaKRhkNKk1LRPWiMOTLMIuz4sZySyO5w9/LHr02E4OjI77LVECJM1QqncLDZZ2pJZsItVSqgIEEHaxaXruDaddp62XmUKGQAQfr3NfJRkkaj0GCmlJI8kFSY7BSnyWRkamc0JpGD/CGWPjKbIFmz1DetbMhVikgxz0Jfm/E Do 441Crbj6UAMBHBYEkgQtLusW4KDAkiVh1ATRzZoYx8H5prqBVCMJuC1qyLrUQymE3bjBSWvLTFFam2UsUosWQ4pSieqFkmBADD3cSmVca0haj6Ih1IWcWsCa4zp5QON6V3QsKqXCtHyw7q6gxOL/W3h8oSAIQ1i2M26ZQAYJi1Tp8z3GOaNZ6QqX3AnPdkgGBy8kyJZWYlnJkUmx3GgGNTFMwsXHMSF6PtfDQAqndJxXQVR7I5ZWVm87t2FDVTnXVlSUTSMLyEJgGAmFgxVHPbkn1NxOQiya6yypmBFCtpulw8E1F7bLcra1fQUfddnzlZ0yQpWekiloh1vmWLfZ6fdlZW33DVkdPYGIjIGopNsSLT6hnS24usV5Y6pv6VrmFMyUHXwGXKC/935FZe7RYjeHuiJKcQAE6tVAu4ZJk5nU6tqKc6vo9CtZWUSZtya/RK10OIAKlkjU9hZUMSEci1RmHOkEGWdklEAqSmzkwgJhJqXueW4F6rjCn41Ugn2eK7Uh8ZgLTMq44 yXbLOZOqjK1iKkGePm01d8rElZW8TPkAXPEJVrsQpNIBhLsjsMd0YX1OLB2x6slSKUJ2oCpZMqebFviIcs Z2Pq04e4hbJqRiZ2ifQq1LSwteC1MyjZjD4ImdVINdnaNTGWOLBFljmDms7WElGmmqHJIqsoTQbL95XsW2jJMNb0wlVHpNnJl jAyZAHLRgNwSg B36ZCNjX2PAxgZs37DbFqETK7OsueVXBlL7Es7hbX2DTam7LDNG7bdgpH2kD1ZPUNAWCyFQiD/EqJIsaui1tIwHoUlNHqIaU1QbT1QTMXCGXaYSdEfbkMJrZr58gPYpm2FHsB1NFFBEMpG YHl749bdnjcMoKV1qmalWTfJ8931H40nHK1OHY9005AsxSxP06AQDAMEdn/7IvlOLC1uSNrTb0SsG0/Vl9OpZm6H9rtYPVJa343tIZgKFMwo6y6mkW81u2eh1Zy15KgZBgIYSaSJiLXQxBZGrzZg9x6HETSs53x4AglgxmNtJy1qPkkH9eYLGgh1UttgQhZe7ePv3DF IOtwZZx17uHjnhHwbdXcX8v5SGOyHMXgRLiTHFip8GS0vphniGJH83Zn8iWwFNA3LHUTl7RKU5YXDKtWxjKrFLsthTL4s2tSqaqtCn1sIyKDh9OH1lM09sXMntVIoqIQSRobo6JAmdCGCDoQkBCaXNuNtQ9 ZCSiFQ5kWQkopqeJDWeoqncEM1mak0uL0F0oOIpOHINQCCDVi6nFf8M5v6jDm/kWmGoKS/H1tqu8vk6Ahgk0mElKHWgD3o2M1pFSSsZ6evS7Mu8PHYZbRXviPSM1VUhauEbsOGZ3RjZqR4CFk8M1yEOdo0K1OwnYqc6Q0JkizVUhbZHyEj5UNSrQePTumTbdKcVViCx66XWeG02fkmZLYc8coY851nwuHkn75HuWa0GcSbnYFJg EKYZCp5ElSSxKZ q2VylURDR6voKQzBDvxycrRcHwO/Jo5WSMV2bxRuZjLoGBLNfItekoSsHqFdzVT d8QWQtSBAKkmjl5Zky2xdvRz9REgwAQG hGxXSLB3Otk1WzEJGhypECgEZgNj3S1OcirIVjNbcCBJOEZXMhqWYUFi8s8S7BwoyfwVRNll8ReSc5qpkBMtziX2Xu88hxZjRuwZCqlnkEm90krgfN3RvtLu0IAJh1IlJNRS5VhjxUpU7wWC2g2GQwGfB fD5hbxjSZ58A1FzcqaJNlkv2WXU0O6YaBa2lVTK9/VzDiGEaiZVSm LZZtOfVvNw2609qdgRq56ELhEOexpjhgAskHYksdP6pmLp MvMqf551qOaUrra09tnAFsrcXliacIlQbwTFMDTr6Vbeep51uepjflsEJGZD9mzF38kV6jTJmR0N5amQxpLjJvO7ieKbjHqqFNEauKvkSAiTUMSRCSEaQpgIUEawxH4pLvLkCyVAcZSKy09hs2xilna0y6zDew5mWoOp2ky0K1mKvYvryufV5VROZqjnZ1KWJ x2UAOe9RwyeAUEhiKn2w5YXVDpnQJIfXTq53CsRLamodNv3s2kE4rd0VzVBnflCuVuAxzFKd/SFbMseK7m5SlhOmQYVXI9hZKzZId2shsN1vPcOjyJc6oytj0puasemAu6SpbYPkI8qWBy3M2HLymEaFTKpMsykVlxdo4MgSjL7PsDu5g1WLdRSjwZKAhCwrCYegUZE5jBqiWHPCOfTl8xJEgGSLT82szjVuwhwVkjcxKhlBbN5iMw2US3kHYDVP16PIiJwqtekY6wm68HXCG7XeGuZTKla0prl2 OkBnOJAvbMXwCSYPlWS7eJStkMzPmiS62028E7lbT7DPsDSXqqaX2yQgi2fXjNxH7nYqcZCP6qu/WDlGZxizHy9qzUD83yX3FXx6PKdC ukkmDyPtRpSPMdnxxl gTxjBNLI4qY2Xrb3 nzRjC3FjgWEPt4sEGjFSpnlknTqegeEIsHrmVITumGe61taRjHlzyHO6RsweYxmlKEcZ VcacSgkXkV5VBlCjh62gdEeAZyjyq1np4rv1BivEsdanKMReFc1xrkjNMK0W0qMN209SGk3UvUbm/rJUFVgTmiASJFgzF0s0TSNikBCmJ4lyJ4DQTNcoxyrjWJ6JYCkxEswsTZ1GkmWhcY8gBgByiW0JAz1ZZhzrgVfip oY5lDuno 6G8sVLkz5kboMocZIw7YldC yJEDsDKUMlqbW7 4unKrLu7P2 w174ljS3JkFpuRjOAtxqppk71xwwtn2T7J3DSgmpSmQKMmOG2MG3cgkht2qpr2PzHQWJMtPOmW4SR2GUpoFvo/Ebdk2621rw2qMFW6Xag dMO0VGdUyAEr8k7kLyN2eSNVBMzHMztxSMk3XFWnt7PPFUmJDutrIzV9To3KER9pZl6OfmT2W4Zr72E7HnsFB9QHvJ RqGRXftb KnZ0RruVRM2eLPpdoNKuSvqnVZMa2RjCzhPSQxyCCPd9zmb5NVcZa nSJVWu27SJDeGwHTu4egzkRS1jOYRnmmq6xlMjfkK7Xmepr6pzWJKsbJ0oTTr0Ypo UOSvzx9TcWrudoceKmZEkl9A1TaIuR3Jz6mDrhmm1IcGevmYyzk0SM9wt5ohM1dNNTzLhzjKlMdSIYRNmZuv mVo7hyDfK chzaa5NBA2473tzAIufw63tUAIj8uKQ4tPzzDMHmtnK9XoC4cFtlzvZq3Nqk56ddC7WJmBEs70IyWLlPw9 XZLUiq6m1W6Skmj3FjFquSGkIKINGgQGoWkYGmwJjTlvSyE8iliYmKwIAHfAhNgKyvMzFJN6Jkly/KD87uvQ4AA/2MgoJuxM9P3TClv08Q0bZ8Z1CsGm46NvSHTAyPDc4AAAfZmdDMW9HKY4AzPew77RcZJFgZBZw1Cg23nksroCGXDVPqTqcpYk25W1gLD0WNk UF5AFrieuYSAwQIECBAgAABdhrm4zMA 4UnSMHQlAcUEZEgSHNnsWA2SBBY8ywwWU6oLNUfy/KD8ho6AIAomMMFCBAgQIAAAXYHlO4xH4smhcaZG76JQBBEGgkGud2edOWOQKROz5IMMJubkssPytvWmuFkmwABAgQIECBAgF2Jba1YkPfZfhhPREnlyaT2oEkIYfkNktS9PqjqvEHlKMMApAyMMQECBAgQIECAPQURTyat1SUhhWRWh0iRaZchx 3X9JJhy u34uDcLQ2xTBlrusffsb6hob6uvqO9y5BSbdUzDMMwjGQymUz2rAzpuqbruqZpmqZ9ybRSsiZEdk60pLSkpLjYHdPoRW4BAgQIECBAgL6DLQ0xFC dZIw1hGYIaTCTlCAdTEI5 TL7nXnZ5bxsdGOSsXY2JhKJVatXJxJJ5TlMBMlMgKZpuq5Ho1FzV2k3ICYIa58hAdB1HerUAsjtTav8fbq64hs2bKqp2Tps6NBQKNRzdQIECBAgQIAAfRWGNAxpSKkZUqrbZqzzMVw7mGCuMVl2GajVpW4cZQwAzc0t69Zt0EMhacickH7ZkfvtP2Fs9cjRbBirl302f9Hnd769qMNwH6SRCtKElpub982zz5o4ad9xY8cB GzJZwsXfPrvRx9ra2s1DP8Zdb1Pm0zIzz5bOnjwwIKC/J6q4wIb7S1tbV0GA6BwcVluuHfHKblySLbUtXRI6LmFpTndnbCzu7H7CeNk07aWLkYor6Aku3enPgQIECBAgABeJKXUpJQs1XU95uluUkAIJqILR5/CYCklA2oDtsFGUhoVM/LWbGnJlKkQIpk0vvhiha5pBsvpVQXXn354xYh9tJJKyi2GTMrmuuS2TTUrlv5q1px5tR3KrTglGwqHw1P23/93v//dgAH9fe82btx07a vnffxx/F4/MukTSQSo0aN0HWtV6oMGx2J4iMuvuCMKeVZADrm/d9l/96UnR3qvTbDRlt7yTk3XX1MATY 9tufvdmVn9WN0sCx5uaWBCicU5K/HYXsCLaPsIy5bAfBnGzpqLzktitmZGPtg9f cm6iINqXFLsAAQIECLA3YEhl/j5yeEQPR0LhrHAkrId0oemapgtNCAFBainHPumT7LsW0a3PLzPX1m6LZkWSSWNKYfjO48ZFinI0SCHjlGiHlGBD11BenH/HUSMveeGzxW0gQcJ1HrlkqWv6lKlT7rnrbveZ4jb6V1X9/e/3fu/7l8z7aF7SSO5wWk0XtbXbysvLOOUg4FQYnV35R5x7/pRyoGP1whW1DavbhIB03aLTI9jwHCDJhsx4gwHHW SYX9x59T6Qn9190Q0rI3n6LtRmtoOwjFlsH8G Bt REgMECBAgQAAYbFjHxJgX3xARQzALoXxllJeJVBefArC2LxlGRtmfTMalNDShZUXEtRPzQrJL44TIzhEs0dEIKTUiysljJCQSvxqTffGCrgTpQhPOBXiMoqKi31x7LREyKRlE M21115w4UWNjY2wjjTegbRSGl1dXcoFp/u26uwS/QcVAsDa5/56wzvbWMvNCyeaWmMMLRIJyUQsIRkiHA1nhTV1fH1na2eMISKRsJGIJTmcm50Vqnnw8ssfBEDh7CwykkknjpVDKBrJjnBX0tHPONHZ0KBl50XDbsuFlf92lK4BLOOxeCxuGAwQ6aFQNBLSBUV9hBkSkImuRFciaUiARCgUyorq1kUiMt6ViMUNgxkgoes52VrPBAOQRmdnLJZkCCEi7qpIw0DGEt11kYmuhITQsrIjIU50dCSSTEIPZWeHTNUpfQV7Ym AAAECBNg7oTZW224wyp1W3X5EJNw7mABAEqR1O0c3KzJJw4hEokTxM8p5QI7Qkp2duSVvfb5lSPXg8QUGwJ 16GvWbTu0tCK89rOBeeLUSu2/jRGybi5hZl3Xzzj99MqKCu523aeyouKM009/ JFHkslkN2m7umJz3/ ABE2fNi0ajaSmTRqGEN3LOo53Zs 8/vffGgwAqD7zrofOxJpHv3vdxrPuvPqYAmx56Ym5FYcdP6lftGvL3CcfuufNGgohnqw8X719/pF3qo4 ZXJZ26t/uexRuuBWcx3n6lebCFVmnBcemV12 MlTq7Lj2z568v47Xk efssvTysDADHukn89AmDdXZfeODcWDpkX3siuhJV/r0u//N9bWC eevpppx4yemAuId64/KPZjzw6e1VCk8lKF2EtWWGOJfInnXLaNw4dM6hAQ e2Re 8 MBTC qErpOMJfImnfz10w8bW10QAndu/fztm2/9ZEr3BAOQRiwy8oxLzzpxbBEaV770 Pshp4GllDJ9iSSSyaqL//aTI/Ox dkH36o89owp/bB10WN/e2RO3vHXXDxzfLGsXfjy7X97cz00DTJmFKWrYMivVAUIECBAgK8EmAms7l0CYDv2GiCNmfWUK7XY/r9hZFxgEtD0EDPz IKk0EggoXc0xFr42VmfxI8 CuBXXn19xJBqPQeaYC2kTyhIvNAWUndaAmDmUCg8buwYZllf3/DBh/PGjh1dPXiQnf/ades/W7J0 rQpJSXF48aOiUSiQsRT06rIbW1tr785e9my5QCampqOnHlYbm6uemWnFRDdVMesuZDNmzY1DOhfrAHoqK1pbd/UZi8tVR77jaPXfP7F2pyJ1ZUHnnepqP/trQu77PtzKk8450wkWts6E4b3Uh1mew9W5fHnfKN 48YmDC4sm3rOhScu/Xvjhi3NZZUFALi1pqZDxra2SWJpGM7FbdtdOsvcgy776Q8mRABurWsKlRaNPPjrvx2ef82vZq30VFfGunKmXfbzyyZHwU2rljZmDxsy4WsX/KFCu Lmj1qQP/3yX1w6KQpAttbXJnIrRg8v1T/skeBEsvjYX15ySjUB6NSqjrvkPNe6oIx15WYqscmKV3XSBeeop/IJ518z4Ovh4jwA0PpNPPGKU5Ze9timJPIPuip9BdexFrgWBwgQIMBXD9Z JPNOa3VNJ5mnzaRsxjbTAOjWKhMKRWAQQPvkGSQEEaKbPz9 8IR4vOLhhx4kov0mTTp UChrwyKpCaFpo/I0PRQSQmhCADCkjETCI4YPZylDul6ztXbFqlUzDztk3JjRAD77fOmbs9/Jy80L6TpLOWL48EgkzODUtADqGxpeeuX1mq21hx82A8A7773f2tp27NeOVIfK2GkFUSKR8ZgcBSFaP/rbjS30h99Mj2LNrF9d 14TCaGZChavfOxnv3uvlouP/e3vvjU064CT9n1gwZwmW3K2zb/xFw9 0CC1qAYMcDKVku04G5 7 tcvb4xO c2dF44R/SZXd/zyxpsaf/3Xq/eBXPLIT/ 0uBMUCmsa2S4ljirT69KJBn39rAkRILno3t/ 4Z2m8KhTb/714SUVh52572vXf KqrZHkgYd/c3IUqJ917fUPrY7pVV 74a8nDZh43HH95z1GM8 ZFAWwYdaNv/rP6g5J2eX9cxJ19d0TzJIGHHJ8NQHGsgd /5vX6nKnfOvWKyblmE2R5AEZS3x4i0XYtjevvea/NVOuvOc7QyhcHH/j9ose3LLvT393 Ti9ZNywIl5fP jwTBX84/wOErvWeTpAgAABAuwJ2KtK6oc61leCCO7N2NuFUCik6UIIYu60jgrmaGdjRWl5PBYDUFFaHI1vAxikrp9HOBzSNE1570qWekg3ZDyZjGdlhU847qhXX3/rldfeaG9rA/De x9WlPc7 sjDs7LCyWTckHE9pEesu7zdaVtaW5 Z9Xx7e8dRMw8ZM3oUgEg4NPudOc88 /ypJx fn5dnpwWjR1UGgOaWg0KEdUpa2sTWRauaSISpeeniegwtQfmQftp7jVbcxvff KQZ0agG5kSGzGvnL66RgmINNR0Yk4twbpgo7rwmEQlnlMO9LJ2TnDVwaDEAbJi9oElEKLbmk0 aDz qQBs4skRzqTIMyh00rBQASk7 /U0nO2 KR1Zm5YWHFQPAuudeWxvX9SjBaNzSQkJzr CkEiwRrRpUDAAb35pfTxHR8vn7yxKT9lOLTEw5GUuMwlJltn344cpOFps2t2JIPprnvb2qA7xxXQvGFSOSExEiN3MFxbwOBGtMAQIECPAVBNk3LqVC98Yijak3u0wEUSgcBeKru0S5YchkEgWD3431e/mNt2YcNpOZX3r9Tf2omTMK4rxlNUu5qkuPRqOCnAUmErRixcrJkyYAyM/LOvZrh7397gez350DYOSIoYfOOCAnOyuZjAFYsWKl0oFS03Z1dfQrKxk944CBA6oMIw5g1Mgh2dmRpctWdHV1ZGeF7bSJeLy7 vQCQhdKMROhNNKyvaFLEgkAmc/QiXcm1NURytq1XdaD7SjdBKO3V7W3zH9jfo2jfyVrag23XYms/2/P7iOZSIIIZBjJNMnSlEhWtFhbnIlZqrOZY80xwPJM9zZZ7ysYIECAAAH2fpCELSqIQRIw1yZ20CrDxNFoFhgrE9Gp8c5kItmS1X/hoo0HHHzIsaMrAIRCkflfrN1nv8GFyZUyaaxKRKORqK1UMYMlr1yxcuL40SrDaDg085DpudlZRDRlv4mhkG4kTVm3csVKXQtRKE3agrycIw47EIAdGUBVRVlVRZkKtNPGe2GS6R79pk4eOOu51Rg0fXIRAGxds80g2Es83CupmqIQsJFkgEQ4ojO3JmRYF2ktM70snUi2b1jdgOpiDDp8UuF7bzdGRk2eVADA2LC83kCJixJu37C6HtUlEK3zX3pwUQeDIXKHTB7JW7paeVUDBhdj8AlHDH7/6TVdLKL9KvPbapq6J1iga/P6BgwtRvnkIdF3F3aGh wzNGwXmbnErfFea3bdVVCKwCgTIECAAP9zMFUZv/NvT0jE45FIGIz3DG1m58b UVnUsuHcg/fNDlNW40aAjx9V0TG0pGDjolhSbu3iObJfOBx2 zGw5LfenXvwQVNLS8ybkgThgCkT1UtbNamrb3jr3bmRSA9p08KdtrHhy1plUPG1P991YDPyCsIAuj587tMmkdna1UtQsn5tI8YVY SFt9xwTMPmubfeObuW02kzvSxdCGx467FFB/1gQmT8d39739ebQ2VFWQBqZj/ aTtcqgxI8Ia3Hvv0oB/um3vYT387fOmaOuT1HzawLLz2jh8s3LD rUcWHHjppOigr//kwSPqahO5FUUbbrjk1vndE0wkN7z70rrDzhmcffBVPy1cuC1/zJiy3pW4PtOyXEqTceYK9rRJLUCAAAEC7JUQlh1AQArY9hh12ZJalPDKRCJ/SCri8XhnZ1duXg6Hsx7uqownZKKlNXfzktDWtYbBhoHQtvV5W5bG29oSCflAa3k4LzccCXsQCQtBDz7yRDIRN5KJtH/JRPzBR54Qgr5k2s7OrviXXmDaPOufD3zcGgoDXVs/eOS2uz7t0L603CQhN7785Esr2xiUX1FZXV0c5vQrT70unTSt6d1b/3Lri59vbKP8sqKseNOKOf/9v9/PWi39TNX1lndv 9ONzy5a2xIaMHrMvqMrwnUr5z43e2Wcdb157h1/umHWorUthsgvrShB7bLVdZKE1j3BpGu1z99wz7NLm6RWNm5UwbpZT8/v6lWJvVUKCUJkqmCgyAQIECDAVxTmXYvKF8YvMejisadKZoaUzIaFwVR/AAAgAElEQVQ0JMskG0lpVM7IX7xiczfZCiGGDR9JRLFY1zDRcV6FUVZSouXkUjhCRDIek13tdfVND27ijXqhpmmp6pGUsqOjc9CAirPPOKmkuMj3tr6h8dEnn12/sSY7Oyt1tt37tIYhV61c3tsLmMAybsQkIEQ0LAic4IEX3myexfKTF7YZkplI00VIM9e7EjEjyRC6HnHdZ UN7PYncyIhk8pBiUQk4q7qjpUOMBtJmTTM3epCEyFdCDY6tdE/ueOHB0Sx6h/XXPNuW0gDACNpJJMqJhFBaBQyD8ljIymtVyAhwiEhqHuCLbLjMikZRJpGSEoDECEtYvlUZyjRWxdpdMWZQXpYCwnIZDKWNB2NFQ1pKhhsXQoQIECAryLGj6gaHh8ciYSzwtFsPRwOhUOhkK5pGglNaJomdtBXBoCUcvOmDdVDhkYiBZvi0Ru2JWbGuqrzjP55UQja3Bpb05p4uy2fc6JZ1nEyqQiHw1u3Nf71lnunT51UPbj/oAGVANZv3LJ23ab3P1oQCkcKCwsyrRr0Jq1hGBvWr u1HgOARFjPyvhOi4b9YaGIHkqJ6A3s9idRKKyl5PBlSgeItJDmyVTK6JiTLz/joP2jALbOW95uM0TTNS19L6D0r3om2Bsh5RTeDCV66yK0aNR5J3Q9y50ktYIBAgQIEOArDXa8Qq2tINaTR6QQ0XbtCWlvb1 29PPqIUNKS0sTieQ7hjG7Qco6KYQQIkfTtGi TtSDR2xWVjQeT3yyaOn78xYmEgkAoVAoEgkXFReHw6Evk7aurm7tmjU9nYz3PwFmilSN3b86Gx2b33ns/he3Sk0LjBgBAgQIEGAvAYGsqxiZmSUJTQcTWIDJs8AkWRrS6OUCkxt5eXn9yisKCgqi0eiOuV4yexa/fD97n1ZK2dnZ1dLSXLu1prW1dQcoSc0 /SLObsJOK52NZFcCAGkhe30qQIAAAQIE6OsYP6JqpDEkqofDkXC2Fg6HwiE9rGu6LjRNaELQzrmKubW1dSfpDX0QGRZx9rbSSdOzglP9AwQIECDAXggpwSDBQkIwyL3YBGQ4hqPHHUwBAgQIECBAgAC7E7YGI1w uGSvPNm/dzddAQIECBAgQIAAvYDSUtxKjHrwW2XsywF2I20BAgQIECBAgAA9IJNyojMAkoAkCGYGSRJQG5me/T7a2NjbUbY13te1y5IaJIVk5R2YCcPP8pMgECBAgQIECAryp cfXlgHk5tbAUGiYwQYJJ3YytLmgkEiwZcPZjd7a31G1ZW1U9Nq onxDaduwp2ulgltJobazdvHaJEFpWTv4eoyRAgAABAgQIsNvBlhLj1kXMc2WISJBgSLABto5gYUFE9VvX9x8yNq owkjGjS99HeOXBAktv7iCCDUblg8YOm7PEhMgQIAAAQIE2D3wOPJa5 IRW38kM55VQoRYZ1tOQWkyGWO550 ZY5nkJOcUlMaWf1Kz4QtpJPc0RSaEpheWVAFoqt/cd6jqDfZeyvsCVOtFs/P2NCEBAgQI8BUHEVIP2xUu1xlzgQnmxmyGZLDpIczMQuh73B5jg42k0CPMbCQToUh0D695wVz2SsS6GmrXAcTMfYKq3mDvpbwvwGm99aUV1eFozp4mKECAAAG yiAiCMEAE4HI/r8mBBERhA6AoDGSPsde64YD8HbdZbCrQQAQCmfFutqNZGJPUwNND0UiOfFYOxGFwtl9hKreYO lvC/Abr2GbRsrBo7a0 QECBAgwFcZPZ4Uo5NSD1j4VBYzHaNPaTKKmFhnq9E3FkSMRDwmZTiabSQTfYeq3mDvpbwvwN16e5qWAAECBPiKI5MiY3rNCKmDyaOtWDdKWkpQX9Rlkn1J7iaNZERoQKJPUdUb7L2U9wXYrbenCQkQIECArziICOTcg22D2XSQ0dVVBmzrLM69Bk7U3UtzL9DXSFL09DWqeoO9l/K gKDdAgQIEGDXgwiCzRN9yXW2r7CeM95i7bXK7Po/o/a5y8/43n82JX3Paf52I1W9/UOfpOqrTXlf AsQIECAALscRASS3UTQfeOxJEg7JcCcYpXh1nd/ceGfPveEDbzg9jtOq8q4sbs3sMwDCs5z lhfpqRdhb5JVW w91IeIECAAAG 8jCvXgIEpDoMD8SABDQA5mm/Kh4BBBJMGoidBSn2CzpmgLQxF//h26OiVimR0jKtV/JQJhIIhdKZgtQqlyrO/ZwSz/X/nQTZ8u6d/3hnwoU/P7RIA2THxpcfee6V1e0cGvH9a04eHek5A2a5fVTF1t73x fDF3zv/CGhHaYa2BOUB3DBar0AAQIECLALYe6oJiYQAMlSYwJgMAsCAbogYsA8TEbdcWA dLf3ScutHDpsaLY7KLHp8cuvevugb01b9ewLC7d0RocedclPvj jXyix6fHLr5o99ZyJy194dUl92Vk33X5S7KW773ns3TUtHC7f99jv/Ojs6WXbZ9DxGGu47cN7//5E PjfXDAyz9GREmuf/efNK8b//IoDK7Ues9P77TNmQnmImBmyYcGbr9WP O7VB1Zn6dFwrzyFbCuSN7Rzwb13PZx96vXnVUdTEjBMs1PPubshm2bf8cAHky 6 uACbY9QvtfB12I7FYE1K0CAAAF2A0gdkkcwwBKGhAA0IhIaQEwkevKVYXvNxw0gTTAYyXXPvaWf vtHnnzk7ouK3rv9nrmNhgpf//w7odOve zpR289MTrnpt/eu3TAedffeu/Nlx/a dJ1v3lyVYwtQ4ydVboSON0ZN5Qz5sBBWLNgaZvrXWzr3EXtlVNG9 tZfHFSRkceefQJo3IIAGTbtg4qrR5alJUdTWs Sp9JbyPuXIisvZXyPg1OJnvZLEHrBQgQIMAuBxFJZV0R5kYmZahRN0pCnfZr /d6U8IK9vurABz/6PpvnGKH5Bx /V1XjWQAhTPOO21svg5UHXjcpH/eMm9j7JBRDCD7gHPPmlQcAoz2j5/5RDv8/751zJhsQuU3rzjrwx/897lVJ18 kl3FcYaiLTK90 HcofuOFrPeXdqy/9R8JcK71n26qLPfCePytXjjgtdef 6j9fUJZJePPPKkI2ZWZ1Gy4dXbH5o/ uCRGz/5YE1b4WGnHPTFs3MnnP zGdFFf7/rgXUA/vuzX0IffcqVQ fc9N6gK688dGAIALhj9T9vfJHP Pa39on6NoSlUmX9NJfJZMfG15969ZUvmpLZ5QceNS4JRNSrRFMmCj8Zf/i4TfPfW9UYC/ebdtKJp0/IWv6v 5 pkXjxvh /CGSPveyq6Zvvu//dXUq5omTi1yZvmvPqsmYuHHrs2cceJD5/4sk5n9TG86qnnn/OQSOzCTC2vP/q43NXrWmIg7IHTpx 9kkT kcIALevf Wp115b3pzMLp9 5LimV bknP d86pD6SvuY3ai6dPX33hh3rptMeh5FdNOOOn0cVlb0xaUbHj19oc 3ufAERsWLtjSHguXTz/huFPGR/0tdsXET257fOspl/xILb/F1t33lxezz//2N/u3errEzPN doi uCfyArNMgAABAuwGWKoLyDvoqjuYGNzNHUzK7TftYE3a6Iv 8O2RpjMG6QVVYQCAXjioyMxRRAvCiZoulVwrG95PxUjWrapF1SmWVNCLR40taFuxsUOO7FV9LIuQNzRrwIzR4bs XFE/eb9SDeDOFR sTgyeOTYvvnTWE//ePOz0C2YOL0huXjD74QdfzL381Kk5AIyauUvHnHvWHy7KkfGWD78AAEbWvt 59Ipn/3lH3VHXXTw0CnBz 6BX3n9/84EDBoUAblv16Rc07OLBUXjNQ mdkT3OP 3zn3zmxfp9zvn qUNFzZv/eW1pTOzPYKNr2bMZKdwyd8nE88687rxwwyfP3/T06yOHnDrp3AtP duDH0668CcHFWgAZMsm7GrKARhb5nyw9cijrjhKW/vms0/ 67 fF WOP/bMoyO1bzz2ysNvDL/mhIowpEElB5w4 ZtlWbJp3VvPvHnvK2W/OLEqwq0fPTHrlZZx5/1w8mBsfWfWa0tj6K7iBS5tQXYunfXYA8vKjj3tnMlVkfi2TevAkjMVBMDYOnfZhIvPua463Pz56zc//kx22bnH losXvOJq K25qyq6XSJRNeKZx/ugbxAkwkQIECA3QIico 3Qt1XYAEZN2OzZZXJcFqwllcxZNjQ4epv6KCyqLXh2xPfXhAioYudc7tP i3ioeqpI3NrFi2oTwIsO9a/t4qHHzAkr33ly4v1w884dGp1UXFR2bhDjziicNOcVe3KVzM6dsbRI3J1QeGw8ObpPFPe0BnVsYUf18TAkO3LPtwYHju OpppX27GQNm0YvYKfdrXD9m/f0Fx5aiTThqTBwKY27qjMG/CITOrszTSysZNGqXVLtlmn8bm2wy8CylXBURHHnb6AQP7l1dNmzm pL0269DDDx1RWjFon6MPKm1ftb7ZYEDvP23KtBH9ygrzyqvHnXJ8dWzZF1sTLJtWvr06fNCpB02qzC uHHH8iWMLe6i4QwO3rnh5obHv6ccdPaZfWWFB/xFjDhyRq2UoSNEZGT1jZnWUIApHH3hc/6a5H26N 5sotb5wqml1iVBsdY/kZbAaBggQIECAnQyfJuIYWVioFaYerDI7/XZBvXRYP8xfsK7r8AlZAJINXyxpzh05IFugrTfJTUUmZTocqhw/uWDx wsbDjuypG3ZpytF9YVDI8naTdsSTWtvv 0VV8yyxg4DGkMUVeXrbiOP5Yzj/AJA0VEHDDb s3B1Z/9RsVXvrY9O lq/VIda23vIG2q/5ERzTaMoPrJfSMUJlQ6q0JYxc7yhGwq1vLJszSQjlBNK1sekf5v6rqecwQxRNKBAkS7CuVEtd0BxSKWJ5oaR6IpJZsGtq c99dKCJTWd5i3qoeEdBieatjZS8Yhis6X14oEV pLuKs7ZdpeLN26u4 IZVWGfm3faglhXdOabTYxIeUW0fUtjl8zytBi8Dtf2L1VNq0v0hrw07RYgQIAAAXYB0h3y64AIzmZst7mcnB1M6ZUZo7VmzarV1m5fChVUDizoFUFa6dRTJz/y1zv Oe7HX58Q3fTq3Y t63/CVcOi6J0qk1G5CpVMm1Tw9oIlW2ZMXv/RlvA pwzLIoCZKs6syped5URiNApPXmGmjKrp44Vjw/Z21HSeOijfljzqhIq/z1JNIYgKbZ5ZHQTDNWNxSmmsS2S3DuJMoVHTYlBAAW8TCPHgJk 6rHHvmwbfqJV1/Yv192KL7u5d89nOg26wwV7wndF8SGo6uzTL9T2v9FuN9orjOue0VeoMoECBAgwC6HpZBoBA0s7P TYBIgIl2JKZlyQoa5gSn9SM7G0n/ 7Crnd/6Rv7//e3m9okgUzbjy181333v/z69oRajfhGOuufb0oWHA6FVqRU 62bAomziu4u0F7y2JbNgcnXhsRYSZCyrLsOLTtR37jcv2LKSl2DZMfwlni5Q9bQfC5QeNDd09d/Gc1obi/Y4tE2kKZwZRqm3DMZNo f0KsWldU3JsuQYg2by1PoEcZr2wtxTaNAmAWe42yn1PKb9MKoymzZuMfidNH9QvmwCjbXN9h8wHs1bQr0iuW14XHzcgBCBRv74miWHdVNwFvaCylFYt3tg1aZTjqpypIGYGZP3q2o4ZhXkEGG2rN3TlDCoIw9tipGWHEWtPGBwWgGxvaoxzdkqF9Uw9J13rBQgQIECAXQrb7ReWciKEbQ9gEOl f2AiYoIwo1OqzkB5M/74xIx0hZ1557/PtH9ERnz//ocAANmecEDkjDjpqr edJU3sVZ6ws3/PiH12Ve4tfaR korGjG9cu4zz36AvElnV oAU/6wYyZ9cM8zL7zIB08bmM3tDSs/X8f7HnxQsc8XxO8a4n3W83Kueu999G2cnj8vX0E3EGKIUqJ1tROOzQoXOeeXXJ/meNK0PT/NcXbAMGbR FDDBEuKhANK7aWDM XBjSsyK7nPKUxkn/SsstKaHPF69pmzA2x9j2 ay3twH5AIv8IYcMee/xWXOGnDppMG2b8/znTUB3rClzds9T/rCjJsy97 mXX//6gZMqw7Ftm9fxwKnl6QtSxCTXvff0RznH7ROtX/DWK1sLDz21LCySnhbLyh85OPLmvKU14ydXoumT1 dtYuqfUs3ekOdqvQABAgQIsCthKjLSvr5AzT8FC40EWOjeyGQLte7dfvcYyF7TSH2VN35K5axZm4snjynXVZzoyBPOuCj37Reee LNLiCUM2D42GOi5LJgKKsC7G0spiizDxwGAGhlo6eVzn85OmFCoUhbNDP7/KuhMnFKyZl86okNT79 0x/fC2XnD5s8efiqBQB4uygEmMPDD5s69PHZN97wBrJG//CKA3Y55V5KvBvMXf/PG/mNEzb 69kHfzkrnF044MAZw1bPBjOY8vY748T6/7zx6F0Lk1ll02YeMHzrRzpRNxV3IbrPCaefG33rhScffSkBPbd86vGDKFNBDIZWedCU4s9f tML7ZxdfuDpJx1ZoTELT4tdddSQI48 9InXbrnuAz23dMLB 41cPi 1mt30nNTWS9OsAQIECBBg58E67dc/3pJ1xgx9Z/zpkpkhWbIEJ9kwpJHg5JgTKk8 8fhxU4/p6mjaA4RnQDS78LOPXjaMRM9RdyISm5 8ZVbd0ed/b2JO2uWGnLwiIURrc/1upao36GOUJ2s//Ovdqw9MwZRb0 w6 XMBpf/9ujC6eee W0/J2ddUao1quqHru7CgwQIECA/0Xc MdfldaXh0OhrHAkOxSJhsJ6KBTS9LAIaUJAuHYw T1/TS1o99PcLTL6yuwasIx1tm/99INPkoPPHZ5FGQpOvw9oz6KvUM5dm5Yt7CgdWZmL1k1znp/fVHnQ6LxM5HyZcpSByHZ72R3oWxwPECBAgK8olEKiwTlIxgfdCjali3JGIbZ0mL42Vu9meuIbH7352c9kweSTjxyVnVmt64Mirc9QzvG6D2fNfrLNAEKlIyZdcOK4kp1 GdKeQh/ke4AAAQJ85WDeo Ty3xUMwQAkAOHzlfGk7MNOALtvNhweeMEvf9hjqdzD z2BPkN5tPrgS6862FPorihOFM784SUzd1Xu6dGX B0gQIAAX1l0o5AoO42urjBAyrhsXlywS6nbfrDv374C5VPd16jqDfZeyvsC0h9dEyBAgAABdiIyqTKS2AB3fwcT0EddZfqcXV8dytPXqOoN9l7K wJSDmMKECBAgAA7H6kXF/js735VhglgMNlWmb4l5ew9s3uYjvTom1T1Bnsv5QECBAgQ4CsOdeCd 6dlpzFDPaoMuw5LI4LQ9FhHS58yzcQ6WgCEw1l7mhAPEvGuRLyrr1HVG y9lPcFqNZb dn7e5qQAAECBPiqgYjC0ZzifgNy8orIo8dYG5lcoToAJueANVjnsRFIGslIVl6ss3U3V6B7jJ1y9J4mIUCAAAECBAiwC9HV3tzWUle3ZY0QGoFS7x4gIg2kgQQoxVdGqTqcfut2X0BfU60CBAgQIECAADsXJER2biGRqN 6Pq1C4naX0UkTJKUdYq8 9VVNJkCAAAF2H5LJhJFM9K2jFgKkgIg0Xdf1sB0SMG4vhZuVmh4OhSOxzjbXXZLpVRPdzWlyucX0WatMgAABAuwexGNdTY3btmxY297eyjLYsdZHQULk5OZVDqguKx oBFfAuL0UqawkInXbXfc6STcXF wyYgMECBCgz8NIJtpamtavXjF01PiCwmISmjMoshoibQ9DmIdXuGOwe2Zo/uvdE0qef yL1l3p4DOYezZhMKkSPcdtkf0vuVPaxfo8DtgTy6kR26HuaqhNpL4L4b3nkpGfILte7EsCm0x1fYorS2JPq1gvndZhdr9naTQ3Naz YnF2bmFBYUm8q707xqEn3rGngjvKO wQ 2C2spMZ V73xEE4bclWbt4 tX1MxJfgI9jRJPx8hNM mVlpJOMORRksLOYRefYPnyEusMoECBDgfxnJZGLT lXDR0/IKygGwL5zhEwRYktE7 gPss8dIgJ7IrMZCnYdT6oiSLfoIWf4twWPT9qwO8Svh5jZ sj21dInSMku0NaA2JZfbP9gf0bMptBwBIldN4IrvtUS6oVbP/CuENhkm9nY 2utdnAXQ1RQVDJ89IQ1yxdPnn5kD4xzNAxTsDJ8ikpPvFOEO4l8vIMleXvDPleguyCPpuFram9tesFBkLu9yGrSFGOVi4mwG97J3OGjr 9n5COR5/Qtqwt4v5fuWOlSZXpQSDIfkdeX9mAHCBAgwG4GM7e1tebkFqT3tyC33YVNQ4EjgawnVhNg73RUjfee6HZ89a/0xbcknCMArDmyPXVnT2T2n LezYCebp7ttXs4b6S3Lci1sYTtS13NAp3ZvFszcswKHlnOpiQD4Mg/djJiWxvw2kfsx5zcgrbWFiKRyjiPYqBycqQxO6R6eGcpbCm8g9/04K0vscWd7WKfuyrs0j52mINwTC/ujM2 6kY3TISrk0ubCFMZ6Y6PcGuEHqLMXDLyES5WOiQ6ipQdUQBOBD2TV1RglAkQIMD/OlgCMJ0tTFFF5BYxrl8ECZB3Pg1zscQ1UXVlDoDYo4UQ4KgxjlCAd6Qndxgzp5Tq12z8GfQKHtHAnDoxZvbF8gos76XEqir FE4iS9nxTOKtIHJ s3sST3Dzwp3cyzgVmVwpXXYTwLRU FrRbMTueAd4l3vsc01s9nl7ixlrR9iXPqhH7AgTfa3KHnoYHsNaCnUupdXRYyz9x15ZYsCjFfsKJcB3mHo6hUQCEtDUrEA3fWpSahgsMAUIEOB/HURk3u5hiSxylvcdwWXfWGcN7876kDURNmWVKf5s0eW88ZjcYcl Z9XIocl8R66yfNgRodc92LNG4TFHuegCPOT6ovnEqleZsJ/sFSxYbWC 9WgwnkCCJR3dG11MxjnxLXLIxTirAItsmxXsoszDO7B7fcWdSTr2ca/Zx57HnQ beOt3Riayt8 R673vlerK3fHRG2S1j0fJ8fQNstnl1UDcCglBnZLnBDKzriKl2mYCVSZAgAD/4yCQlFLJJHNEl3DJNFhiNEU0wrbHkz1xZ8DreKKGa3JbGqyCLdHozGRdUVxGflh5prz3VKNXSDvL9uSTPoZtZPC89i9iqP9cosZyWHGtuhFbTjROGZbXisss4Jr7m2YsglRZ2aqIzTjznTIneItUctOSq QqpRe8sxaQvjT74OdgGnbtEAfTBKQeM7djTLQTup564CN7WeezwWRmpVmy5fcr1LTB7jwWRJrYnpoF2D5w 8pn/nz5N04544RTzjjhnNsWd21/FrEVd114xgmnnPH9pzcndz6Buz7/AP9TMOqev/Jssy 5n3uJzoXXnX3RjUt24DvZLSB1cZ1kKaVkKVkyJBiQYAmWkOqVlMySWUqw9cQs2YxhhrFkSAazmdZMKaW0EoHVaxekE8nKxorNMDOUrj9PaglpktibP0gJaaVsr/3kuc82tDJLyLbaT577bEOLKpFdhJhV9VBowa6n1R4qjodUySyd/KRqHTYbmhVNVhkmgSqtemKzbmwV7YitjIyzeGcldkrvmXfS3dpWzt2wL7Vx0rHPw0Ev81M5KNtq5j 3eEOL0SMHHSa48rdK7ImJ0p0 hYlmY7nylL3lI7NNpuIjzPwzs9JiqJpPGACgVBdyjGhqB5NJMbO9e7vHPdxffSS3/OfKy 7fAAz73oN/PbJE9JwCAGBsefVv/3h/M5AzbNLYirJ9CvX296 58PolEBN /tjv9stOk6THCAH J8Gt7/7y4j8vDe9/1R3XzigSAND56Z / 5v2K/7dTT8xts768RWvzrzl1pPLM7r0B g1CKkWa/bPXMlZolDzfmc qraE2AnV1JW90017sYk8eftmy64ntn8xACQaF7 ypsVDYnTwYaMH5Hg9Lnocz73lSoMByhlQmNva2CIZoJyBhbmtja0JX3y76laY9BbmWX1g92KFvULkWkZysnWWg9j h9lfmA9uq0xPjLP8RpwdVz7e V1j2LVqCHcau1j2EedltIdsAhINLsaRlpWV36 k//CS/KhwJ/AvQzEAyh5YlOPmhZdO7qj99O268kNHV2YT0vUgb3xXxu4w6XM5cbJ3s9R89PARblb6 QiApCrP19O9SGuV8bskO8RzNzuYAuwAEvVrGwBg6NnX/Ppr/QSA9o17mKQAey8IiH/80HMrp54/MrJnKZGJBEKh3mr0XxkQUcpW3hSkjqw n1J7YYKccZt8gz55JIGTkRmJ4Dn2Cy4BkGQGFR82Zb8qzQrSsksiXevrW KuLNKT7ncEZfcb9a9kaT8bLG2LmzdfNmWVs zgy1TVzlkl8ioVZpbsBNiKR3pJlx52XXaYcdaakv2fSyEkVyQnD/t9hnUha49SCvuSzKCSI6ZN6a/JeLx9W92aeWs e6dl5IwhJZGMubK0 SLZSF8vKRkQuYOLchsaWhNercq/EubNXIVxOibCai fNupw1MnOpbVYymeatu4ePmOK qH2LBE0994l2FaZ3mQUwA2O18x9/IF/v/7pumYD2RUTZ57xvXNnDArVP/ T79 9BgCw r6LT70Pg4 Z2fHym9sAQC760zdOATDssn/84WjbyJNc968f/OSJWm Euy4y33auf W2Wx5 c01ruOKAcy7/8UnDs7sWXnfBdR/EMfLSe284okh0mj/3ueK v0yvufM7v3qlBQNOu/SITU89 sEWVEw598eXHNLy7E13P7 ojvpNPv0nP/76mFynB3DHmhduvumRt9d1ZA2Ycc6PLj1uWPb/nKjq4xDZk44e8cUrD7x33HVHlPqYI9tXPn/PvY 9u6aFw X7HvudH551QFli3vWX/32dgft/dMr9QN5hf77vh2PdOlC85t2H733wlcU1MeQOPuCM733362PyRGLz41dc9faB3zpg1VSrSFYAACAASURBVLMvLNrSGR1y1Pd csmMfiEVPvWcictfeHVJfdlZN952Yuxlf4ndmn7SFgfIls fvO1vj3 8NZ4/7JhvzkwAffdmdkLK5L434HRqh7n32usp4ZLuHiuK7W1h5eDYJvzCjQEKF Vlc0tjh4qViLV3Juu3LpjbWLJPQfvauuYOqeUXV 87oDSbuG3rwrmNRSNz29c2tHSFBhw8uiq5bdWSmvpWA1q4YGD/YSPywwKO/iLduoz0T95dO9K983SPRcilorjryE5UX4odaHOVpfOwY4xLkbkehcJiirPHzIzkrZcrput//k3dzACF8nMi8eaGDtbySvc5Mi/y6qJVK2MVEyLxBGRH04Ylm2sb4ga07Iry6jFl SGyjRmsloo6mjZ85o1Drcve2dTBWPzAm4sBvf/wSeNyqKNxw5ItVrR Kiundp7jHL3KCVL4aOssTnV2Ph/h7 Y hcRzBpF9RB4Rgcn0B2YQEaXZsxXAglH31l9/etO8TlDxiHGl7cuXL3z 9is3GXdfs2/BwMHFG9Y1JAHkllcV5AwoKY8NKNq2sREAFVRV5YpI/3z34M/hkuoBRbXeCNbcasNTN96lvPzjNR/cf9sz 950Tr eqdv4n9sfVE818/75qzVPxeuUCbP2k8f 8sS 9148zL6kZONTt/w9nF8YRkfnxnfv 51RctvPpxcEykyfgijY7/xTFl/97/8uO/DbY9wCXza e/Pv7l23/w vv2Ji1sbX7771ut/qt9101pRrbv1OpgUm2fbJPf93y6opP/i/b40via9564Ebf3dL4R3XHFEAILnbcO/tXvH/l1Vu2bN115x70Tx//ykBwV/s7 v7zusd8Xys7GuTdfk1riUA3pkam44ua3b/njw1sOvvKGX48VK56 9Z75ndrhu6TxdgIIvZjcbxe6mZ1a03e/FLRpgee4O0v6GEq6sdEZ62q3xAsp94OurY1Vk48cVl5BW1778NM1peXjo3EVXl8 6Wsjq6qy9FjNe//a1FoxdPpxlXkdW a/tHp57rhxVUJaO2VZsjR8z5RCVxpSUyUcvpRo6w28C0w7 76C7njnFJ6RfezV9shmXFc8ZuqgnD8gy1hRZxw2FOtr13y0vr1y8H5HVJWGO9a9vfiLZTn7j8 ShlkrNqTR1br2w9Q4uSMOHrRsbsOw8w8cWUAAjK2r35m9ob1i8H4zq0ojVrRx2YZ0U dQnTaIAbddaRfzEekXmJRRRkiWSj8hIiEEAGYWqSqL0ncCTSYT4utefGheJ9DvtL/cevN119950zcHArEFTz63PnfGj6/7yfQsABh2zl/uuOW2q08551fX/WAsAIjx37/lzlvuvunSA9zaQqjy F9mjlB4xG8efPTpv10wFAC2fLy8xe563Sma/U748yOPPfijkQQgXhc65tf/furen0zUAdQtXFrvNkn2P 3mf9330EN/OrMKQMfc/3xYH9xV0tdAoUHHnHdw/I37Z9e6WWfUffj0J9rhP/r2MWOqqoZM/eYVZw3e9Npzq7pznpWN8x59L3zqlRceMaZ/v/Ih007/7ully15c2Kx4Xjjj/NPGFugUrjrw En66nkbzUM2sw8476xJJSGh6e0fP7M9JWYqLlH34X8/jRz1o/NnDi8vH3rwxd8/pGgnNNMuAxG7fSR37Z9kKdmQ0vlj15 UhnSDDesP4Jpn3nz v4s en3xR68v/mj2 uaElBJAaMCMoYMq0LiuVRblobZZ7xchCUCrmjF8aCU1raldOWd1HZVOPn5EZZbRYeQP3ienbVVjuFCDNCWvNE0xzIBVqAeZSFW0Scf3czf8uTdj70bGWewztpN9ilRmNsw/aNlhzehsF2Fs21qvVUw ZkRVNNnSyHnDKyK1tcmSqLCVQub41gxxZCLJhsGJ i82r168ceWnm q18snHjqjKSjQ3yNzh5ZHabcnS7WCisVuZ6GelyU9HkxTWdiXlFa/cfF13MLHzh8DtNyNk29pl2wCg9j9Xn/cfJ3zbsk2dPDScKdkOoPSQr00o0ELRYUPysLoVsdYuR5URGbnT7 BDRuRoPGBQPpY3o jAmfvk6zRoSBEWbkNXa8ylTZdPn14dJcKgg6aVPv5MHbYur00cXbaHfTIC CHyJ55z2oAfPvbUZ4dcZAcm61bVov8p1VmqH jFo8YWtK3Y2CFHZswnUbt0U6xm6eVnP oKrKptNaADeuGgInMsENGCcKKmS3UUrWx4v/AOlZipuK66VdtE/28MMk1MkQETB lzet8auxmE1GPv xqY4fOVEeG8QlkzbxtEKD8XbZtaOmIsQZSMGeGIzgyKFBVQ26aW9q5krDmO/KHl4Y7ala0dBmQ4Eupq6ciuDsHy5jSYpWVkUEKm78K1vrR3MA4AIMGW3UsazGAmSjTFZMfm9 7e7EoQbaWsCrK2JRlGZ Y4ZgmSpSE7m2KyY8t7d2/xRuOcPt0 /g1M5rVQEpCgNNDdt0gSgUDWMtPuJ37vQuGUYw6sdFTBcFVlaOcWkFUQEQAgdLcPoTIzK9ugEetK2fYayY0IQIqQBgDR/CwBtUcNfqtgwOG9BFrVUecf sz1/3j9mPM84dspU5hZjLjyH9cdUeRdRUxsht/OZy/Ik9DdWvP2lJihuNgSAJpuh5Gu9 FFzb1mRhcuystKNG4zF5i62uqMuLlkYcQTDtskCUHKeG/E4la4EOjqijlWP5ZaKNyHuZIZbrffPUvJjoETbXEpsnOj1Mmg0nEnntM/6qlIst69jSRTnA1 b9500Tau3LSzyd Z8Lv9EphsJyQJF6NNVUZprmR53AuGMN169squsPPByVgiEbe2x m6njt4VClW1EHmTz3925PzBIBky6p5S0T/KCGWkp40XQBSxjsTqR57vYrggojmh4EYmjY2JVHQueS9FV9Csa754MP1ZwwaivVzPqwDgPKRZTtZGQuwc0A5Y7555vBLHn3808GsPPf10uH9MH/Buq7DJ2QBSDZ8saQ5d SAbIFWQenno6F o6rw/rtLWg8/eEc8ojKX2JY2fqbi9LKhpbT0i7rktBwdQKJ 1ZY48refnt2EdMeH9jGY 2DZ6Ip3tTuMZ2cPErPr/kcnXEpmhHLD2FDXlOivwuNNHYlQfn7EqbZ5vkjKc9 Ee4Gpb1NqMw4OT5IdtRu7RL/hJbrckh/Gii3b6qPJDR2e WqXzQuE8sNYlS5OTK0MmhlnjNa34d/BRAAgIAlMkDAkCUkwoBY/WSeidFvw91atdudj9Te Y/rB9V59954zeqjztvv9dvnt/yxu9 tHzsyDJq3rh8TW18xJUPTBuSZidGqHRYMRbWYdltP/jBf0oGHHn1z44fqHcb4fLMiwThyv1HRV79OFb7zG uWFLatHx9 5ep2sYnLz//1UJubooDyJp 6jT/JpkAfQVa eHnHvXUr2d9BjEBALTSqadOfuSvd/xj3I9PnRDd9Ordj63rf JVw6LQjPJSfdvCJetn5JSGwzl5UdsrVxQfcM7hT1x7 w3/4vOOGlXEzRsWffApH3b 8RW9oyBTiRlUmYzF9Z92yrhH73nwrcN/duQA2vzWwy9sBkbtjDbaFbAusevLYABINLY2G50dltuvnhUOubca2X9wVYcBplBpccG6TR9/kDO0gBKtjRvWdkVHTSgRic2GN3nqc1 E2 23j5NqkpdsaW8zYp0t8Vhbe8OGumYjf8wRlZH2RllcVhJaP /N7OFVYU0g2dHR1MDFQ4ujDi8oVFpWsj5dHC0covi2je2FyaSRFBmj9enhPtXtl0gd9pve 0UnMDEIJMFEZBAkIVhg6g5a2cyf/jnyxMOPv7FgzZJPN0AvHDB6xtSjRqXfyhwafOLFJ3529/PLW5q3bGyO13b5J8ypETKrMpQ/9Xs/Or7l3heWt26qyzrmuxdtvv/ BannJPUOA06/4tjapx95pxnRqoPOvvSyA4LtS30YWSO cc7YV29fYnYfUTTjyl83333v/T /vBWhfhOOveba04eGAWRPOPu0sX/ x2Xfuse/GVvkTv7 9b8q seDd1/zVDsQKR4 aeY5ub3 zjOVmOFsi4zFieLDfvzTrTffdeW5D4Xzy8YfddKEhc99mYbZtej7AhEAwA2z573n/NTLpo0eZH3NnKKNuMMRzh 4r6hfs27xsgREuGDIyANnFhl1Ne5xyt0Cfbw1PM4ye5KQXoLr3/jwbQAgEc0q6F897aARgwvitcs6DT23/ Rh ZtrVn3cngBEJKtg8MCyAbmdaxqc1BnidG2RldU562d/NMeAXjlk/Ki00dCyORNVfQL zdjK/GI7wxBBI2hqHUmA6Qf7niVZHSbMhjQMlklpJGTyiG/ts9 U6WOnHB3rbN0D1QgQIECAPYquzvali YNHTFmTxPSI/TsgRNLvSZh2fzFptpk3uAx2U2f1fw/e18eJ1Vx7X/q9u2e6Zmenn1hZmBgGEB2QQTCY5RFjAma4BKjorw8jbtRcf ImjyDP6NGRXDBhYjGNdGIT0ziiltwQWUdZRsGZph9X3rvW f3x92qbnfPxgA9UN/PwHRX1a06Vd87dU6d2trUs/KSM0aMluu3NXjtbjYcAKTklNyi1BSnBDTsbWyrr/aGEIgjZdgEV cPdS1 ZD8f6dr1Afv2/DDj1DM7WusHJXE0GPS1e1pru7z68ibicGYOS0tLtUsAGAp6mtoban2KneMiapowksS8rCH5TjsBpbm Yn8ArcnqauLalFGpDPq7gv6uyr3bv9v0ZXCnI9GR4HQkOB2JCXaHQ7bbbbJDstkkSYp1RJ4kzpUREBAQsB5UH58Ieyu/q4wW0VHxvXmlAXpayjcDAIDChQOA4ums cE6ZsVg5/7vOyM/xzXYM/KOphy9Q0ziNGDQ17jX12gJ5bmIngbQV9e4r459KmqyOIZ1ggn1LUwMDJdjd6f9Hib5BAQEBAYH2NMsBOIfzKpfQdzgBomYYAIAwh3PyB34G92UoUTsYBIQEDjeEXn1kUA8g1v2K4gbzLAu wUigWQDyQZEPf1O321NAEi310kKS0ZAQOA4ByFCIQ4mcJuxj6okAoeIiHNloNurI6KbMrH2OwkICAgcP5AkgvqFLwJxDkSU9AMdBXGDGiyVKvTTfrkw7eZOQiTJJm7GFhAQEIgCQogzKSUUCNgTxHUegwChYDAp2a1aMIK4QQ2DSiMkqkFi FwQ0XqSiATEpu1gOqyiCggICMQ1bLKcnZff2tYcDPjj/ujY4xqIGAz4W1ubCoaPouGQIG7wwkKlEU6IvuCXuXeJfZC5TlLd78QcQXME5BYQEBCIT8iyw52WLTucdVX7fI11QinGLQghziTXsOITUtwZoaBPEDd4YaGSDVf/gX5QXpTrJNVdTmo0EqAEKIGa ubxR6cuAgICAnEBQsCdmpGWkUOIOAo7roFIqRI2lJ8gbvDCQqWKmvpmN2QTiYBEUCJIQAGUAIlxB9PREldAQEAg/qGEg0o42HM6gTiDIO7YgxLjPlMkIEnMbdg6xNSSgICAgICAQLyAWhe9aLeIISKhUhSvjFglIyAgICAgIBD/kCSJEJQooeriGGOXtlgkJSAgICAgIBDH4CwWsSRKQEBAQEBAYJCB2ZWNMoCkH6KHABh1x7aAgIDA8YlwOKSEQ8JXHecghNhkWZYdRoggbpAikkodxj3Y7FcNsvGwegiNuIJLQEBAQEUw4G9rbayt2u/xdCKlPT8gcDRAJCnZlTKkcHh27lB1GC6IG6SIpLKX0M6VQUTjhsnDJqSAgIDAoIESDnV1tFXu21M8ZmJqWgaRbGbXiuoFdwj6wFA9nQvYFGh 0Ttlwt HR7hfgEY2ZgKjQ7akBQBAopaI5vNgfDdlIUacJgIL5FKZNUIjlK2GeqEfWsTg87cKZNQLLY AIaa6D4XJkiDXKnqk2TqIbDxSpb2tZd u7UmutNS0zKDf0x1x0BN3yFWwv9xBv gDrZXNzIgluicGwWxL1HPj36m kQiHwCMw9wZYeQSzfWJTyW6ntxzzq88dqb4ZYt3BRAiJffekgICAwPGCcDhUXVleMnZSSmoGALA3wgAYKsTQiJbr7gjo6QkB5BKjFgpITA2iJqCs6iFm928oHou2YX3sxGqHaNlaxLbU0qJIiVGgYQGhob/Q ILWjBD1K/ Qy9HUpro JEZ6IJx9wI6jGbG1bJBwDYWc4ISkpmeWjJ1UsXv71J c1gNxpoWhKVYEi6HSE3dA Ics3IF5kXPP9DGBbEGcpWFpar42vWAQCNteRG/SCGcVQyIYDW9mbvJoefdj8kjMlmQyM wXvfqxqez ZCDutF 98ky ka pgICAwHEGROzq6kx2pUb3VRPW74Kao8DUQPonVAfA/HBU7e 55EZ69Te1pNc1nNlR62NkY iOXGLWTIrIy1rTKB95v4cZQ/m2IIRYdZip783RPGsZmW4FTpejpskAwNR/aGaEhjXA 0eMj8mu1K7ODkKkSOI4w0DNydTGaIrKcacbbBHcgdX1wNeXoM5On hjq4KM9dFvBsF0vbAZa 8qi25IBOYlp4YQmjHSHY/AWoScUFouMXkEhsoY1SVW9xeJ8MoICAgICGhACgDaYgtNVRHCqhjmGwEKQPjxNGiTJcxAlckcAAhyVggBMM0YUykA39MTNgwRI0q1WjbWDHoFTt8hRp44hmhJxSss5ERXq2J9wnxIN3a4QbweRMzvyA7iCbBcsI/zxKmJCfMk4zcB0DwVllbUGrE77gD46R5i gE0 vi3RUvVH/qiB/WI/pBoaVXk5EHgHGsR0jFGq2nH6PaPMbOEAJxVbCmUAP8m9AKyIZ0e0o3lJyAgIHA8gRCidqmoqyxiTu biovonb1xHa8ebQyEta5VU3 G6jJjeNe4rvvNWSNTJi2OMGVZ0B l1z2Qm6Pg3FGMXACcuJZkFrXKGxPGJ2MGC/Q20GI5C4YLJKBrR0NRm8SZ6XVxCEOcXoAutkEFMpJx3AGy8ytsJtHow17Th9zHgYchvP49JonIv3PsmhNLlPoqd8cjH6S3D2fkcO8GMeiKWPSLfIMRIjE zeh3MAlrRkBAQAAIEEqpqpO0Hp0Co9NAV6MRqhEMfzwxBu4IwC88Ubtrwnoa9IJ11WiOZJkkjJMf9Dwj4rlq9ApRR9lcPtFTGE4GLto6iaH Yybr9AUrzKwbQX0RjVmGvmqFcQswY3/NjUWAqlkZpohBnBanuhP4IlW9qetVwpTSC 70CaRDpg sDEahq18MRgkgMVP0jUTjQeZTDzwiT53FBxObSrNw/W7sqMfFyHppuqmIKAHYjtej89Czd93jq179ssYLAMml96 5fmJitw8E9jx15Z3vtsHQJY tOie/D9N1/rI/X/aHTzww4vInVyzMth2a2AbQV/HOqlWvbKzqAoDkaReOLXv1Wx8U/ea5RxbmDVQZAgIslKb1t/zu3dKHV52TL7Ofe/m4b vyS1c473rq5vHd/6UdJRBV9yLTxetmjd6BIzucR2MWQ3MSsE9q3TXjrqd8fw/E1CjGMxHzG8Sqfjjtw01ORCyY6UWNVZWE3oYtHzdkzxlfmEzQ27BlQ0P2qeMLXcSaGQKr70z/BJhajtN5yNUWAVnvgDFAZ7wx7KidNzb0S5HZGhpZxSQOdLWqqWTGN9EjdwiscYOMU8EogalHtMaBaPQx8kfMLVkZRG/D5g2NOaeOK3TFMm8IRsZgjN/dymlEGQ/EMFysLdkNjwCMd0wNIVSNjEVllIoY/5v1iLKDCWn0yycHE8K1by69/vkqgJFXvvDQaZm9NcyU2vefXPNlDUDyyCnj87JPSJM9Xy77zX1lIE2647V7T0o6rDIPAJS6D596ZmMVQGLRiRMLckantpcdbZEE gvs/PzOSx/40THt5sfvKU2XAAB8Wx644g eG1/p5lVU6t6cb356147Je5Yh3coYNEOZ CU3BaItA7Yqtlg4yjXB/Y85rGnGwiXN6RPTpvuBgaItS6/b2KDk7ExKI5YwuTea3Y47ieL5cqCECSC9Ncna0dFAFI8tA0V2drZ8iS3qi6Hkb5wrjZB2QnKwCZwXrPCk9TdnxhFrBemZ6I09eNmDuuLNxZTQ3UXGhcnpqDTqebF44nmhObAIRaGOKIzel052QWlGS6EyX2AbQ8jQBAkoamJ7Nc8HKit2HLp025p44dksTZllHegVgkAqi3GVnEV7NnKdU cjwCS6WVR9Btl4g3nUdUr0w3MLs7CYEACWnSHJ9emVDz/hYAgOILl9390xwJADwHu38ioeSK5165DIHY5DjQHKGWiiYAgIKz71h2zlA70PCZpyMC2OxHyCVDg0F0OIT/Z6BAAILf/vWdvdOXjE44upLQUAjs9uOuWyCERGzljUDE9AJY1pQaExPMGJ5YOn3CaQIzIy1R5PGlxpcwIpCMOSeflG/84dmSMhP8lc0dQSaL6KJbF4IiG6P pkiNzwrSsEU080HCj94tmaq1M70CvFGhZYlmgGF49GVYbdSl38TpbhfjH2MQEiaRmYcRH2NeSN jFEFfGBFI5vwZJxfYaDDoaWyq2FSx47OO0aUjMhNi5orU4IWiEr1elCKA5CpKd7W0dIZ4q8pS4wgSAYx1zhGNgxYSgW1CthTGatGNzyht3T0i55C6dbAQ87Rf5GzKYxkYrNv4 tpXPtxyoF2BpLzJ83515cWlw zN62 5enUFAADse 7Sc56DojPmef/9cSMAAN32p/MXAcDI69f8v9NZJ09g7zPsBJM 31Sw6Kq5De/ Y2OV15E3c/ENN/2iJIlAuOX7l1Y8u25bE2aMPfPiecHeSJVImz956MoV3/lh G9W3X9eYejHtbfc nYDpM75/eNXn5zCSEJbP7zjihW7AQCg tWrf/WqGaVOMIW7k01p3fzyimff2tpIM8YuvHhe05onNjKTXzFkI8b8WsHZV82pXvfGN3Wuhfc/e3lJ5InTAv2ClDTl9FG73lv7xc Xz8 y2BHUs3f908 89nlFBzpyT/zZ5ddeMDM7tOm G549oMDz1y16HiBlzgPPXTuetYGCdZ /9MwL722vC4CraOavrrzi7HEpUqjm9Rtv/nTWZTPL/ /dbbW xBELrrzlqtIcuxo ffHk3eX9acfcHDK88K/NtaYrcGfNTiAGjHD39f eTr39YH3SPPuGheCMB5GNpuYED61ytiNLNDn6BQE5gF6Ik4L4p5/pf22/RNWJUbAhBHekoSdrR61VShgMcXbq7fvLE184RUz/6mdi 1uTOGn1iYlUSwq37rxtb00S7P/pYOv71w9tj8cGN5WV1zpwI2R rQgpGj3A4JTPuFsrYMtQ7emR3p/Did8wgxJgpbRzSTWp7oryayTjD1FREuN96g0Ekx95hpifh6MSmZ/6ybuhEBiN2dnBBsb/GiLSXrhNNSEt7fVr43kDcpIRgC6m2rKqtpaAkqYEvKyx0 LtttJ4YzAxEoAvW2Ve3g05DOnZ9VexG2r/14O4BcUDJlQjLxtlaV1erJctSszNpxxznyxglE8GjYLGZ1Bp5HiHjNe/TKqM4Yaj3a dg96Vlp2vDQbY9s8gHJGDUhy7N799b1q5ZWK6uXnZg6tCij6kBLGABcufmpyYWZuYHC9MaDrQBAUvPzXVJCgbt3vpfqdatfyx5RmA77W u en7lWyc sji/4e3lf3pjHwJAEq18Z UTXBPHkuquudmnXPG7jTc 9M3 vz7xwbTftD32dgNA6mk3LjkphVdtxOYuHJ5Rsb8lBABJOfnpDqJ46 tawmBBNNnq377v/r/tRQBw0cr1vZfNyPOt1S Dw 1OSjjuxu2HF1LqSUsWbb/1lXU7Z/12HKvwaevnj977zIFp195342TnwQ9XP7b8f WVj1xw8rLHLo81wUS7vn/69yvKT77m95dNzAxWbFj78L0r0h5fNj8VAMKV6zfMvuuPL9/tbPj4kaWPPzN54p2nJKvhn027c/lrf0yjvtaNjy6LLLE4lg8uVnEZ7Z uuP l2tlL/3z3eGnPPx57 jufbe5habwBAIFeDO77hG5Gp/rw3aoFDVmA65h17aOo2g0VX8Dv0dULAaQI1F/fmj/1tJG5eaT2g6 3VGTlTkwMquHNuVN Ojo/3ykH6r54sbozr/gnPx S4q397l/7drsmTMiXqL5TFilSxfKZRMgVRdRIDQeHpNp6A36CaaC1WHfcmYXHpA95a48YxPmDAc0GRXehU9nTpMwphsqGim8qPUOKTpqfn XwHvh0 66dydMmOqmi1QoVqvg7938dmcY1avawnRtbRi6ZNTqVAIBSvzT6o8eUUnzcvPStCTTUhSKCudKXXUIATOLXL4nR6RE0zWCTsOIBFyfF1WEDzwz79u8gHknPvgY48uvJRy4aChDY/Pd3Kl2lNy2/5SdOAICRix98fMXKWxctvmv5NeMBAKSJV694YsXqR343M7V3unroBY89 eDKR6 fIAFA7be7OwL7//32PgSwjbty1ctr//LC7TOTeyPVgRBIGaVXXTUzCZSdf7n5rn8cBEg/7XeXTU6xykHc06//4 2zkwEAhp69fOWK1U88pFWnZ9nee3svAsgTr3nipbVr1t4209VL2Qy4Z93x3IuvvLj2yf8uFi6ZgQSxDzvjktnBj57/pIH1JitNX//je9vc6357xrj8/BHTL7rxgqLqD94p93eTE23d9OoXjnOW/mb uIKc3BEzzrvivOyd/9zarvZnaaVLzh2fKhNH/qyFU R9mw5qTsOkmZdcMCXTLtlkz7dv9aXEWMWFmr5etyVhwXVL5pXk5hbPvvTqU9IHoJkOG9S1g0fohyKlqFBq/iDzQ6lCWaCi/wBg3Vsfr1 37ZsPt3/z4fZvPqlsD6mjU3thafGwPGg90EnTU6ChXc5JIBQAbPmlJcVDSFtFw97/7GsiWVMXjhriVLyKu iE5K7yVkeaDaimPSgp9gAAIABJREFUeanmikEE0AvlEEtUVTa1UkeqDdnN2EeQOJ0 pY/0qaIioqL9gC3JYVN8HskBjfXNtrypZ4zKTwx3tGJKSV5CQ0M4M1EyjELEYH2MNDQURkXBUPOumn3bD 7dUt1sy536s1H5zlB7C3WV5CY0NIaz kCickRJtFJp/C0CUV0zJMrsE8hR7ZjIHVvHCmjX/p2NAAANb956yZtmeOPOah8OnBbOnTEt3w6SMzvPBTs6INDp66re1wIAMPy06Tl2kNInzR0nf7Up3Bup7FLGzGuunbHtoa 9YYC0 Tf998QIQ ZQZWsGABg b1qWDFLGifPH2b/6JtQL2Qq0LxmlZ03PsgGALPe4ulCgb5DckxefW3jta2/sOOV/jMBwU3kDFCwa7lSbW84YMz61a89BLx0dM59Qw4/Vgbofb7iQmXqE/IZOBWQAOW1YuubFkRJTHaE6v9oF2LJLchz9KjFWcf6m8kap4PxhmpGdUDh5mPyf3rfGEQaByGPv4w2IYFkrIzlS0mjdpkaQ7G4XdFV3eANIgZBwQHEkyIhAEtJTSVd1h8cfDrQHwV2c6/A27O30KkAdCXZ/hzdpuB301ZwKItWdDKqSiV8w80uDgzgAAKCAut LKoiASEioLUC9NV srmEeSOwkzjyCCIiAqCi 2Gm0EihShfraAtRb 8XqWj4ZJsd1 0RTJIxXCLUkhEjqATNxsFb16CDt5DNmDTFr78gfYh/A3B1J6kwkUTsX5o/fJqtXm0mybAOwzv7Ekop2NTRp49 uulofTkk5HLLFWhrWvWwAAMkZTjGzdNhgy1 w5NS37lvz4RmXcOF91CmIKI1aumb5/HSeq1ANWBfZGRPyRJKlaItC 19coAwAbLIRRmQ5jl dKKO/ IQjPcUZam3UJpj8XU1KUJuyUIIhkzZKJEkd1oISCOrhkgR f8D0 iG12R1xzEpssMt j64k/QOGuoJUSnIlEh8CyZpw1uKCRK4i4WZ2I0qsNFXW1bzRkh3cWz3Q4g8kumfQ2HyGqG24jmbKHEvzTRgOhEJBfXObLMuuojFZsKcJqHv6eb dmiIBQLijfFOZVJBIIBDxPLHJEgClQV8ocr1dH0CcBcUZsKsFqr r8M6dkhys2VZuliZ1KxUEK9c//GI5hYQhWaHaprJnV3409Q n5w2YFUqchSMzYVczHNiwuWXO/PSOLR XmXNHPcim5zEoO47BApI87qJfl1z16utbilDdXChnleTAd5sP OdOcgJAuGVXWbtrdGGSBJ0SiT4eteeMyYcvPy/rnDu7l7OkHGKX2BU1fazi5OziLPLjrqbwjGQZAELN5bVBcPddniOEQTD/ru2DRcUf9HtM4tHcg4TI3P9ohlOKCHaXA6qa2kIFaniwzRuyu90JZrUNXWH5HJ9gJ5jiW1KDODA5CXsbDvqlnJJMmda6HbCntrE5MVzl5Ua8foMLsLsdUB4tTUCdGdQyjpksvhG5g4kLQAnNjdaEMKYMIYSo5 lJUl vP4hf7Ftzxa/X6F/ylzzx8PnDf37JSR8l3HR/det3v86GzSfnB3RUNw1NK1M0ZEWVhizxqZAVubYOfKa655M7PwtFtvXzi0XzaEY/hPzxrxrxcqPJ/ed0fr1Lz2bVsauNjYUslV6x59uRzB9V/X/ nitgevf7Zsx/MrPpi8/GcDdnCIo j0X5b86y97Q1tXXX3Ri05fu4/tA7qTLX53nhxjsOXOvXjBG3e/vQOkSQAAtqzp50x9 aHH10y46ZxJidXvr37tQMFZN49MBJuSmyU3bi2rLE3OcjiSUxKNVblSxszFc/92z6o/v4iXLBiTju1V277agnOWLMzrnQSxSoxhysQsrmDGogmvPv3Chrm3n1ZIaja89G4NwJiBaKPDAWI5Ay0egQAAodbOdsXn1Zf9yk6Hnd1qZPwAUx0EQGLPykg9UP3tV8nFqSTU2Vq13584ZlKmFKpR McjP8cj2GW/cS6qJl64w9OlBHwdwUCXp6WqqV1xj5s/JMHTSjOyM 2Vmz5OKsl32CQIe71tLZhRnJFockHsWdmZldHS2Bx2Emw86EkLh5WwFDNZXDveoi377Q4yaL4abtt7zAspjwHYsufd9kDC3156/aPNFWVbqkBOKxxbOn3BmKSodbYXnXXpWTtWr9/d0V57sD3Y4O 3jWcvOHvZbZ0rnlu3o27bDwlzfrUk940Xv/H1KFV4/7pVL1YAOKddc9m0zAx6w39/evVzu3f85cn3pt6zMHeATnCxF/xy2R2djz771rYmPxl65nVz6559elMA7Iky6U42Kd77imMJzlHnLx7//qoy7QWU0kuX3t2pnn77ihE w5k3627J7zih0AkDTpwnPHP7Dm suetm7GllxTr77vrvQ1L6xe9oYHICGjZMq8xTGPDI1ArBJjnG0RszgpY85Nt9U/ tTSi//qcGdPXPCLSVvfOZSGObyIf4UIAADY8smmL8yvcvaMscP0Dg0jrBE2HBzuoSdKzRUHtu8MgeRIHTF61rx0pamO7enYFojz1uAWyxxNQXoJbP7o608BAIiU6EwtGD7jv0YVpQYbdvoU2VUwdaS7pq78W08IQEpwphYNzS50 SpazKdjpPHX0iHDkys/ eY/CshDRkwcEzUZdNTEkiou0G3PRAhBCVAC3QFDyA1TL6aICKhQhSINoxKmioLh8YtyFyz46fiTTw/4Oo U7AJHC9TX2KxkZLtsAEA7Nj997f9 3AppP3/g8WvGHOWj2QQEjhb8Ps P2zYVjxp3tAXpEXLS0MlZvIuUtu qbginFI1LattR16aelZecMWK0XL twWt3s EAICWn5BalpjgloGFvY1t9tTeEQBwpwya4On oa/Ej /lI164P2LfnhxmnntnRWj8oiaPBoK/d01rb5dWXNxGHM3NYWlqqXQLAUNDT1N5Q61PsHBdR04SRJOZlDcl32gkozfUV wNoTVZXE9emjEpl0N8V9HdV7t3 wQfvuZtynfYEpyPB6UhMdDgS7A7ZZrPbZJskSUTS5yis93WLpQ/HFZSa9fcs/UAeVZKXFGz4cWeNH8Ax8byzRwo7RuA4BxkMg/uwt/K7ymgRHRXfm1caoKelfDMAAChcOAAons6aH6xjVgx27vM/JzXIM9I 9oytE7xCROAwZ9jXt9jZZQnovoaQB9dY376tinoiaLY0RsxjaWqQOoe9IJIQSoBECkaDuYjt2d2AKxILlLJo/ cuOubXUI4MgYPnPOov/ NbtfSUDgeAQx740UGARgVv0K4gY3ou4kMbY1oQ7tuGHEiOskBfvHI2zZpVf9ufSqoy2GgEB8IfLqI4F4BrfsVxA3mBHlOknQLqNQIwhhHG8oiXG3gICAQAwQIhTiYAK3GfuoSiJwiIh22q/13CDm3F9mMzZqLhlCiCReAgEBgeMekkQQ6SA9b 14AyJK oGOgrhBDZZKCwghKBGq3WJAECQkkkSO39N BQQEBLoDIcSZlBIKBOwJYv37IEAoGExKdqsWjCBuUMOgMlaCSCNV0pwxxnpgYcYKCAgIANhkOTsvv7WtORjwx/3Rscc1EDEY8Le2NhUMH0XDIUHc4IWFysgEsUwU7rRfwbqAgICACll2uNOyZYezrmqfr7FOdI9xC0KIM8k1rPiEFHdGKOgTxA1eWKi0xsV2tchEO vXtGMIGSQHJQoICAgcThAC7tSMtIwcciyfgH4sAJFSJWwoP0Hc4IWFSjM86mXZRAuPslZG2LACAgICKpRwUAkHe04nEGcQxB0/IIbFajFfUFiyAgICAgICAnEJ1R jLfYlVDNZ2EP0QDhmBAQEBAQEBOIPFvtEtV6s3hei48jJJSAgICAgICDQLSggEpBsQCSUJHUDtrbMN4opczQkFBAQEBAQEBCIDkLARiTTREEjnEDUZb9cKgEBAYHjGOFwSAmHxJx7nIMQYpNlWXYYIYK4QYpIKnUgACXAn5tHKBIA4O9g4u5nEhAQEDi EQz421oba6v2ezydSGOePSpwdEEkKdmVMqRweHbuUHXQLogbpIik0oyK9QghhBAZCBJ9GTCi o K69EFBASOcyjhUFdHW W PcVjJqamZRDJZnamqF53h6B7sPXb7ZgUzDkYxi14fNdKuF ARjZmAsOpYEkLAIBELRHN58H4bspCjDhNBBbIpTJrhEYoWw0ABDTkZIs187cKZNQLLY AIaa614TJkiDXKnqk2TqIbDxSpb2tZd u7UmutNS0zKDf0x1x0BN3yFWwv9xBv gDrZXNzKzzKT0xCGZbop4b/071jUQ4BB4BgcTiEcz2iU0lu52egATqKXhgA5QACaAE6pF4JNoEEyEk8n5tAQEBgeMK4XCourK8ZOyklNQMALDeCKOpEEMjWk4WJaCnJwSQS6xdEwOAxNQgagLKqh5idv G4rFoG2RDrHaIlq1FbEstLYqUGAUaFhAa guNL2jNCFE/XRW5HE1tqutDYqQHwtkH7FwQI7aWDRKuoZATnJDU9MySsZMqdm f pPTeiDOtDA0xYpgMVR64k4V3HzIwh3o9k9v6GMC2YI4S8PS1HxtesEgELa9iN6kEc4qhkQwGt7M3OTR8u7H5JGYLclkZtgvevVjU8maMhQQEEH7X82eGP9bTRnhjxEQEBAAAETs6upMdqVGX29BWL8Lao4CUwPpn1AdAPPDUbW/55Ib6dXf1JJe13CmAtDHyMbQHbnErJkUkZe1plE 8n4PM4bybUEIseowU9 bo3nWMjLdCpwuR02TAYCp/9DMCA1rgPePGB TXaldnR2ESJHEcYaBmpOpjdEUleNON9giuAOr64GvL0GdnT7Rx1YFGeuj3wyC6XphM9beVRbdkAjMS04NITRjpDsegbUIOaG0XGLyCAyV1moiAbBpU0o2AEIJSJJqyiD/Z2qTbJSi2MckICAgoPbF2mILTVURwqoY5hsBCkD48TRokyXMQJXJHAAIclYIATDNGFMpAN/TEzYMESNKtVo21gx6BU4zIEZub0W0pOIVFnKiq1WxPmE pBs73CBeDyLmd2QH8QRYLtjHeeLUxIR5kvGbAGieCksrao3YHXcA/HQP0d0WBn3826Kl6g990YN6RH9ItLQqcvIgcI61COkYo9W0Y3T7x5hZQgDOKrYUSoB/E/THiMQPBvQPhBDZLtmCVDHTUiS0Py0mICAgcKyBEKJ2qairLGJO75uKi idveH61qONgbCmqzT1Z6guM4ZzuYOu 81ZI1MmLY4wZVkw8F04cnMUnDuKkQuAE9eSzKJWeWPC GTMYIHeBlosZ8FwgQR07WgoapM4M70uDmGI0wvQxTaoQEYyjjtAdn6FzSQafdhr pD7OPAwhNe/xyQR XeO3QxkiVJf5e545IP09uGMHO7dIAZdkf4UouZEgVAgFMDGRsqqRcNVR xjEhAQEAAgQCilqk7SukUKjE4DXY1GqEYw/PHEGLgjAL/wRO2uCetp0AvWVaM5kmWSME5 0POMiOeq0StEHWVz URPYTgZuGjrJIb6j5kF0BesMANtgvoiGrMMfdUK4xZgxv6aG0vdoovGnA5DnBanuhP4IlW9qetVwpTSC 70CaRDpg sDEahq18MRgkgMVP0jUTjQeZTDzwiT53FBxObyl5CRkTJzJAEgFLA42cvPnr2rnt81atf1ngBILn0/jXXT0wcoKwDe5668s5322DoksdWnZNvXZTkL/vzZX/4xAMjLn9yxcJsW/ex3WfVLdBX8c6qVa9srOoCgORpF44te/VbHxT95rlHFuZZSxUQ6DuUpvW3/O7d0odXnZMvs597 bhv6/JLVzjveurm8QP1hzegIKruRaaL180avQNHdjiPxkBQcxKwT2rdNeOup3x/D8TUKMYzEfMbxKp OO3DTU5ELJjpRY1VlYTehi0fN2TPGV YTNDbsGVDQ/ap4wtdxJoZAqvvTP8EmFqO03nI1RYBWe AMUBnvDHsqJ03NlTfCtPabOExiQNdrWoqmfFN9MgdAmvcIONUMEpg6hGtcSAafYz8EXNLVgbR27B5Q2POqeMKXbFUPYlyhTTG N2tnEaU8UAMw8Xakt3wCMB4x9QQQtXIWFRyBcW8kEDrcCjVNmBLRKKD0ScTrn1z6fXPVwGMvPKFh07L7O1tmErt 0 u bIGIHnklPF52SekyZ4vl/3mvjKQJt3x2r0nJR1WmY8ElLoPn3pmYxVAYtGJEwtyRqe2lx1tkQR6B z8/M5LH/jRMe3mx 8pTZcAAHxbHrjiD54bX nmzVTq377pxvfnrXjsl7l9MnkFooIAiRjXcQpOSwR6R2y1bJBxlOsDe17TmJNNhMs7skfnDRdDQ4Rat79X0cGJmFg0Z2xhMq8Vexzj8uVSBQFIcmGaq7O1gyIASR6a5ups7QxZ0htV18MoXxg3 4Ccxx ZwXrPCk9TdnxhFrBemZ6I09eNmDuuLNxZTQ3UXGhcnpqDTqebF44nmhObAIRaGOKIzel052QWlGS6EyX2AbQ8jQBAkoamJ7Nc8HKit2HLp025p44dksTZltGsA/OTtV0pn9rgEZGlVPvI8QgslVYeQbddIt50HpFeGQm4lT4Wm0YmhKhzTMePJ4ZBqHl/CwBA8YXL7v5pjgQAnoMDlXdCyRXPvXIZArHJR0 phFoqmgAACs6 Y9k5Q 1Aw2eejghgsx8hlwwNBtHhEP6f/oEABL/96zt7py8ZnXB0JaGhENjtvR0iHDMghERs5Y1AlG2fxKrAjX6ecRHoTwOYw/sYU0NIgDmjxHwOACCMCCRjzskn5Rt/ZrakzAR/ZXNHkMkiuujWhaDIxqi/KVLjs4I0bBHNfJDwo3dLpmrtTK8Ab1RoWaIZYBgefdFLRl36TZzudjH MQYhYRKZeRjxMeaF9D1KEfSFEYFkzp9xcoGNBoOexqaKTRU7PusYXToiMyFmrkgNXigqEBWUIoDkKkp3tbR0hnirylLjCBIBjHXOEY2DFhKBbUK2FMZq0Y3PPu NjvS7oMS3ILMlmxAiq0GsHXPs2TQYrNv4 tpXPtxyoF2BpLzJ83515cWlw zN62 5enUFAADse 7Sc56DojPmef/9cSMAAN32p/MXAcDI69f8v9NZJ09g16rL73qvAwrP/d386jde/aoW8k6KarTun4v0dWr9/WRHKmnnfLTWePc0kQ2PsMPysUbvn pRXPrtvWhBljz7x4XpAXsvvYXtUokeeetn54xxUrdgMAQPWrV//qVTNKnWAKa/NWBYuumtvw7j82VnkdeTMX33DTL0qSCCitm19e8exbWxtpxtiFF89rWvPERmY6LKYA lxYwdlXzale98Y3da6F9z97eUnkGdQCvYCUNOX0UbveW/vFz5fPz7LYEdSzd/3Tz7z2eUUHOnJP/Nnl114wMzu06b4bnj2gwPPXLXoeIGXOA89dO561gYJ1n7/0zAvvba8LgKto5q uvOLscSlSqOb1G2/ dNZlM8v/791ttb7EEQuuvOWq0hy7Gj598eTd775f1px9wcMrzwr821pit1Z61OIAaMcPf1/55Ovf1gfdI8 4aF4IwHkY2m5gQPrXH2I0s0OfoFATmAXoiTgvirHaQs/B9E1YlRsCEEd6ShJ2tHrVVKGAxxdurt 8sTXzhFTP/qZ2L7W5M4afWJiVRLCrfuvG1vTRLs/ lg6/vXD22PxwY3lZXXOnAjZH6tCCkaPcDglM 4Wytgy1Dt6ZHen8OJ3zCDEmCltHNJNanuivDrJOMPUVES433qDQSTH3mGmJ HoxKZn/rJu6EQGI3Z2cEGxv8aItJeuE01IS3t9WvjeQNykhGALqbasqq2loCSpgS8rLHT4u220nhjMDESgC9bZV7eDTkM6dn1V7Ebav/Xg7gFxQMmVCMvG2VpXV6sly1KzM2nHHOfLGCUTwaNgsZnUGnkeIeM0jwectA2hn4oWRIqDqoZGkHrMZPFCaNjx02yObfEAyRk3I8uzevXX9qqXVyuplJ6YOLcqoOtASBgBXbn5qcmFmbqAwvfFgKwCQ1Px8l5RQ4I7RVx98c9UL6qe6TX 5q KNYJPqKWz4/rUH/3biM5eOtCrvUM3by//0xj4EgCRa c7KJ2jvY3tZo7vmcotuiM1dODyjYn9LCACScvLTHUTx1te1hK35Va9b/Vr2iMJ02N9a99XzK9868ZHF fVv33f/3/YiALho5XqLPN0IYOT51uqXweF2JyUcdyP5gYSUetKSRdtvfWXdzlm/HccqfNr6 aP3PnNg2rX33TjZefDD1Y8t/1955SMXnLzssctjTTDRru f/v2K8pOv f1lEzODFRvWPnzvirTHl81PBYBw5foNs /648t3Oxs fmTp489MnnjnKclq GfT7lz 2h/TqK9146PLIkssjuVxi1VcRvunK 5/qXb20j/fPV7a84/Hnv7OZ5t7WBpvAECgF4P7PqGb0ak fLdqQUMW4I6707WPomo3VHwBv0dXLwSQIlB/fWv 1NNG5uaR2g3lKRlTsxMaiGN dO eno/HynHKj74sXqzrzin/x8SIq39rt/7dvtmjAhX6L6RlakSBXLZxIhVxRRIzUcHJJq6w34CaaBvq gO 7MwmPSh7y1Rwzi/MGAZoOiu9Cp7GlS5hRDZUPFN5WeIUUnzc/PcngPfLp9187kaROdVNFqhQpV/J37v45M4xo1e9jOjS0jl8wanUoAQKnf99knVZ68opPm5Wcl6MkmJCmUlc6UOmoQArB pcPv7uhx2S/hrRRTz7AH5x1LCB745183 QByzn3wsUeX3/fEIxcNBQhs/vs7la7Sm5bf8hMnAMDIxQ8 vmLlrYsW37X8mvEAANLEq1c8sWL1I7 bmRpDFeec cDLr71w3WgCAMEm xl3v/LGM7dMlgGgaeuPzRGev D f7 9DwFs465c9fLav7xw 8zkXsf2tkYH KlT4p5 /R9vn50MADD07OUrV6x 4iGtvhYMveCxJx9c ej1EyQAqP12d0dg/3tv70UAeeI1T7y0ds3a22a6 iqAe9Ydz734yotrn/zvYuGS6T IfdgZl8wOfvT8Jw3sO6U0ff2P721zr/vtGePy80dMv jGC4qqP3in3N9NTrR106tfOM5Z pv54wpyckfMOO K87J3/nNru9qfpZUuOXd8qkwc bMWTpH3bTqouQWTZl5ywZRMu2STPd1ZcSYxUXavp63ZaEBdctmVeSm1s8 9KrT0kfgGY6bCAEKR6pH4qUokKp YPMD6UKZYGK/gOAdW99vH7dtm8 3P7Nh9u/ aSyPUQpBQB7YWnxsDxoPdBJ01OgoV3OSSAUAGz5pSXFQ0hbRcPe/ xrIllTF44a4lS8irvohOSu8lZHmg2opnmp5opBBNAL5RBLVFU2tVJHqg3ZzdhHkDidPqWP9KmiIqKi/YAtyWFTfB7JAY31zba8qWeMyk8Md7RiSkleQkNDODPRmGRBxGB9jDQ0FEZFwVDzrpp92w/u3VLdbMud rNR c5Qewt1leQmNDSGs/pAonJESbRS2TvIjBeOqivzCWLkjq1BC9q1f2cjAEDDm7de8qYZ3riz2oeHoGRzZp8yKtmGhcPcsLsd0mfNO8Etk2Ej0mFrI/g7A9YGRE/1vhYAgOGnTc xg5Q ae44 atN4d7E9qlG9n6YorkzpuXbQXJm57lgRwcEOn1d1fuaAQCGz5uWJYOUceL8cfavvgn1QoAC7UtG6VnTs2wAIMvHmnF8hCG5Jy8 t/Da197Yccr/GIHhpvIGKFg03Kk2rpwxZnxq156DXjo6Zj6hhh rA3U/3nAhM9EI Q2dCsgActqwdM2LIyWmOkJ1fvUNtmWX5Dj6VWKs4vxN5Y1SwfnDNJM6oXDyMPk/vW NIwwCkcfexxsQwbJWRnKkpNG6TY0g2d0u6Kru8AaQAiHhgOJIkBGBJKSnkq7qDo8/HGgPgrs41 Ft2NvpVYA6Euz Dm/ScDvoqzkVRKo7GVQlE79g5pcGB3EAAEABdb8XVRABkZBQW4B6a75YXcM8kNhJnHkEERABUVF8sdNoJVCkCvW1Bai39ovVtXwyTI7r9umr2tDWygCADQjVPILH3moZAEg7 YxZQ0yfuyN/iP1QsktwJUgAVFKXzya6nRIYm9i7az2brF5tJsmyDcBqrHQfa8GA1ciRpBpARO0KozgZo1epOwGSM5xiZmmAYMtfsOTUt 5b8 EZl3DhffwrRURp1NI1y en88yEasDqjjUm5Ikks27cvpQYo7hAGQDYZCOMyHIcvyiDxkvtSE9xhlobtQkmf1eTEtSmLJRgyKSNqosHCBBQAkE9XJLA7w YXj kNrsjjlmJDXbZ79GVpH/AUFeQSkmuROJDIFkTzlpcwK ADDez 1JipamyruaNluzg3uqBFn8g0VcGZUIkAhQRASQJASkSlMjgdctgOBAKBfXdbLIsu4rGZMGeJqDu6ef9dmqKBADhjvJNZVJBIoFAxPPEJksAlAZ9ocgFdv0HSS4ozoBdLVD9XYV37pTkYM228kAvYy2Quq3RwEjrLByZCbua4cCGzS1z5qd3bPm4zJw76p0Ag7MriU Q5HEX/brkqldf31KE6pywnFWSA99tPuCfO8kJAOGWXWXtrtGFSRJ0SiT6eNSeMyYfvvy8rHPu7FiTpt0hdoldUdPHKk7OLs4iP 5qCs9IlgEg1FxeGwR33 U5QhgEWzu1fbCo IN j0k8mnuQEJn7H81wShHB7nJAVVNbqEAND7Z5Q3a3O8GsNrsrxLJDJA7BTjDFt6QGcWByEvY2HPRLOSWZMq11O2BPbWNzYrjKy41p/QYXYHc7oDxamoA6M6hlHDNZfCNyB1O3yc1lv0DNeaW4fwliY9 aK369Rv Sv SJh88f/vNLTvrw0e86Prr3ut3jR2eT9oO7KxqCo5aunTEiyroRe9bIDNjaBDtXXnPNm5kV89v2AAAgAElEQVSFp916 8KhA7GX2jH8p2eN NcLFZ5P77ujdWpe 7YtDb2OjciqmxoNjAHhKDr9lyX/ sve0NZVV1/0otPX7mNfiG4FGJDyBSyw5c69eMEbd7 9A6RJAAC2rOnnTH35ocfXTLjpnEmJ1e vfu1AwVk3j0wEm5KbJTduLassTc5yOJJTEo1VuVLGzMVz/3bPqj /iJcsGJOO7VXbvtqCc5YszOudBLFKjGHKxCyuYMaiCa8 /cKGubefVkhqNrz0bg3AmIFoo8MBYjkDLR6BAACh1s52xefVl/3KToed3Wpk/ABTHQRAYs/KSD1Q/e1XycWpJNTZWrXfnzhmUqYUqlH4xyM/xyPYZb9xLqomXrjD06UEfB3BQJenpaqpXXGPmz8kwdNKM7Iz7ZWbPk4qyXfYJAh7vW0tmFGckWhyQexZ2ZmV0dLYHHYSbDzoSQuHlbAUM1lcO976fNqvuUI5ymUfxwRs2fNueyDhby 9/tHmirItVSCnFY4tnb5gTFJUIu1FZ1161o7V63d3tNcebA82 AdqPtFecPay2zpXPLduR922HxLm/GpJ7hsvfuPrXewh1aif0v5y2R2djz771rYmPxl65nVz6559elMA7Iky6V6AY /9iRM4R52/ePz7q8q091FKL116d/vqZ56/44ZOsOdM tmye84rdgBA0qQLzx3/wJrrL3vauhlbck29 r670te8sHrZGx6AhIySKfMWxzwyNAKxSoxxtkXM4qSMOTfdVv/oU0sv/qvDnT1xwS8mbX3nUBrm8CL FSIAAGDLJ5u ML/K2TPGDtN7A4ywRthwcLiHnig1VxzYvjMEkiN1xOhZ89KVpjq242NbIM5bg1ssczQF6SWw aOvPwUAIFKiM7Vg Iz/GlWUGmzY6VNkV8HUke6auvJvPSEAKcGZWjQ0u9Dlq2gxn46Rxl9LhwxPrvzkm/8oIA8ZMXFM1GTQURNLqrhARM/UfVdFbjnpEoqIgBRpmCoUaQiVkBI YVH2ggU/HX/y6QFf52ETViBuQX2NzUpGtssGALRj89PX/u/HrZD28wcev2bMUT6sTUDgyMDv8/y4bVPxqHFHW5AeIScNnZzFO0Rp 67qhnBK0bikth11bepZeckZI0bL9dsavHY3Gw4AUnJKblFqilMCGvY2ttVXe0MIxJEybIKr84e6Fj yn4907fqAfXt mHHqmR2t9YOSOBoM to9rbVdXn15E3E4M4elpaXaJQAMBT1N7Q21PsXOcRE1TRhJYl7WkHynnYDSXF xP4DWZHU1cW3KqFQG/V1Bf1fl3u0ffPBeRtsQpyPR6UhwJiQk2h0O2W6XZVmSZZskEUnWjrhB9dhHCdSTf492NQSONpSa9fcs/UAeVZKXFGz4cWeNH8Ax8byzRwo7RuC4wqC4WzfsrfyuMlpER8X35pUG6Gkp3wwAAAoXDgCKp7PmB uYFYOd 7/vjPwc12DPyDuacvQOMYnTgEFf415foyWU5yJ6GkBfXeO OvapqMniGJEnXxNCtPUw7K0F5mm/BtQlMoN3nYzAwEFyl0we/eXGXdvqEMCRMXzmnEX//Wt2v5KAwLEPYt4bKTAIwKz6FcQNbvR134iMhKib89Qf7VRisf3keIctu/SqP5dedbTFEBA4moi8 kggnsEt xXEDWb0edkvovVGcMG/gICAAIC6p/doyyDQe3CbsY qJAKHiN75U8ybsSUAiggAVP8REBAQEAAASSKIVHipBwUQ0bg9UBA3qMFSGTMNgHYbGCFAiKyunOHuyx7Ak EEBAQEBicIIc6klFAgYE8Qq90HAULBYFKyW7VgBHGDGgaVPaY0rFXzJBJJ/xF2jICAgIBNlrPz8lvbmoMB/yA NfQ4ACIGA/7W1qaC4aNoOCSIG7ywUNn7B7kdKYSQ L4sTEBAQOAIQZYd7rRs2eGsq9rna6wTSjFuQQhxJrmGFZ Q4s4IBX2CuMELC5W9f1C9uAAAgSAAItFmnwQEBASOdxAC7tSMtIwcQuL6lHcBREqVsKH8BHGDFxYqI2I1A0UyFsMgEqLdjH3EhBQQEBAYTFDCQSUc7DmdQJxBEHdMInIpNyFEQmatDBIgNklbDywgICAgICAgEJdg5w0pAckSRwgRhyQKCAgICAgIxCe0CwwYaKaMeouBWB4lICAgICAgEJ9QDRgEZA/CQ0IlPpGYWhIQEBAQEBCIL3D3R4J5kaR5nSTRb6tQr5wU80sCAgICKsLhkBIOCY91nIMQYpNlWXYYIYK4QYpIKrVw5BKBRJAAEooECEhy1Hkl4Z4REBAQCAb8ba2NtVX7PZ5OpOJalzgFkaRkV8qQwuHZuUNV3SWIG6SIpNKMIswSGUSgCDY1XPfKGJYMIoqd2QICAgIAoIRDXR1tlfv2FI ZmJqWQSSb2bWifh6Xfv8uUf9jUzAX9eqdsmVTBeF ARrZmAmMDtmSFkDddQrEvAEYtQTIy0KMOE0EFsilMmuERihbDXWRAlrE4PO3CmTUCy2PgCEmguVMEIJcq iRZusgsvFIlfa2ln27tie50lLTMoN T3fEQU/cIVfB/nIH/aIPtFY2MyOW6J4YBLMtUc Nf6f6RiIcAo A5oZoK49gtk9sKtnt9CrnhOpTSMQmgY2gBJSAZYJJQEBAQEBFOByqriwvGTspJTUDAKw3wmgqxNCIfO8PBPT0hKiHjxqJtb4YAImpQdQElFU9xOz DcVj0TbIhljtEC1bi9iWWloUKTEKNCwgNPQXGl/QmhGi5s03nfxG3dQq6fqQGOmBcPYBOz3AiK1lg4RrKOQEJyQ1PbNk7KSK3dun/uS0HogzLQxNsSJYDJWeuFMFNx ycAfm4tSe6WMC2YI4S8PS1HxtesEgELa9iN6kEc4qhkQwGt7M3OTR8u7H5JGYLclkZtgvevVjU8mZMoAECBo3hiIQap4nw11coLeEOB9RQEDgeAcidnV1JrtSo6 3IKzfBbVBo6mB9E oDoD54aja33PJjfTqb2pJr2s4UwHoY2Rj6I5cYtZMisjLWtMoH3m/hxljudqGEGLVYaa N0fzrGVkuhU4XY6aJgMAU/ hmREa1gDvHzE JrtSuzo7CJEiieMMAzUnUxujKSrHnW6wRXAHVtcDX1/14HzeR9cL tiqIGN99JtBMF0vbMbau8qiGxKBecmpIYRmjHTHI7AWISeUlktMHoGh0iImBTQ4pQQoAQklQAlINFNGQEBAQABA06naYgtNVRHCqhjmGwEKQPjxNGiTJcxAlckcAAhyVggBMM0YUykA39MTNgwRI0q1WjbWDHoFTt8hRi6hRLSk4hUWcqKrVbE YT6kGzvcIF4PIuZ3ZAfxBFgu2Md54tTEhHmS8ZuA7qmwtKLWiN1xB2BZjKq7LQz6 LdFS9Uf qIH9Yj kGhpVeTkQeAcaxHSMUaracfo9o8xs4QAnFVsKZQA/yaYyRAxSjsgoqxmKwGhYO5gouJSSQEBAQFCiNqloq6yiDm9byouonf2evduzg/pA2FNV2nqz1BdZgzncgdd95uzRqZMWhxhyrJg4Ptv5OYoOHcUIxcAJ64lmUWt8saE8cmYwQK9DbRYzoLhAgno2tFQ1CZxZnpdHMIQpxegi21QgYxkHHeA7PwKm0k0 rDX9CH3ceBhCK9/j0ki8u8cu6nZEqW yt3xyAfp7cMZOdy7QQy6IvceEQCCxAYSG0VUQ1dbK0PUc37N7MQOJgEBgeMeBAilVNVJWo9OgdFpoKvRCNUIhj eGAN3BOAXnqjdNYHIkSYxV4REUTiMkx/0PCPiuWr0ClFH2Vw 0VMYTgYu2jqJof5jJuv0BSvMrBtBfRGNWYa aoVxCzBjf82NRYCqWRmmiEGcFqe6E/giVb2p61XClNIL7vQJpEOmD6wMRqGrXwxGCYi8LLp/JBoPMp964BF56iw mNhUcuWrV0gabi3GYpEB9GVAaKamh8csHIxAz951j6969csaLwAkl96/5vqJiX3PJbDnqSvvfLcNhi55bNU5 QM4q4e indWrXplY1UXACRPu3Bs2avf qDoN889sjDPNnDFCAjEgtK0/pbfvVv68Kpz8mX2cy8f921dfukK511P3Ty H39Xhx9E7S6R6eJ1s0bvwJEdzqMxi6E5Cdgnte6acddTvr8HYmoU45mI Q1iVT9cd81NTkQsmOlFjVWVhN6GLR83ZM8ZX5hM0NuwZUND9qnjC13EmhkCq 9M/4QeZZSufUKutgjIegeMATrjjWFH7byxofpWmNZmC49JHOhqVVPJjG iR 4QWOMGGaeCUQJTj2iNA9HoY SPmFuyMojehs0bGnNOHVfoimXeEIyMwRi/u5XTiDIeiGG4WFuyGx4BGO YGkKoGhmLSrMcVFfKIKFAKAAlREJCQSJAUN2MbXCj21LHnlcmXPvm0uufrwIYeeULD52W2duFzUrt 0 u bIGIHnklPF52SekyZ4vl/3mvjKQJt3x2r0nJR1WmXshXt2HTz2zsQogsejEiQU5o1Pby46yRAIDBez8/M5LH/jRMe3mx 8pTZcAAHxbHrjiD54bX nmxVPq377pxvfnrXjsl7liHdyhg0DksVucgtMSgd4RWy0bZBzl sCe1zTmZBPh8o7s0XnDxdAQodbt71V0cCImFs0ZW5jMa8Ueu3S XKogAEkuTHN1tnZQBCDJQ9Ncna2dIUt6o p6GOUL42YfkJ2sAGQG6z0rPE3Z8YVZwHpleiJOXzdi7riycGc1NVBzoXF5ag46nW5eOJ5oTmwCEGphiCM2p9Odk1lQkulOlNgH0PI0AgBJGpqezHLBy4nehi2fNuWeOnZIEmdbRnkHYpEIAJRPbfCIyFKqfeR4BJZKK4 g2y4RbzqPqF4ZJto8 VcNkK2xQMSBQgxCzftbAACKL1x2909zJADwHOxbDjQYREdCyRXPvXIZArHJA6pgQi0VTQAABWffseycoXag4TNPRwSw2Y QS4YGg hwCP/PYQIBCH7713f2Tl8yOuHoSkJDIbDbj7utjYSQiK28EYiyDpFYFbjRzzMuAv1pAHN4H2NqCAlYj8wwvoQRgWTMOfmkfOPv0JaUmeCvbO4IMllEF926EBTZGPU3RWp8VpCGLaKZDxJ 9G7JVK2d6RXgjQotSzQDDMMjuqaLDqMu/SZOd7sY/xiDkDCJzDyM BjzQvoepQj6wohAMufPOLnARoNBT2NTxaaKHZ91jC4dkZkQM1ekBi8Ulej1ohQBJFdRuqulpTPEW1WWGkeQCGCsc45oHLSQCGwTsqUwVotufPb5lupIf4rpPkMERAoKSJKRUiYRNxUYFxwcP8Bg3cbX177y4ZYD7Qok5U2e96srLy4dZm9ef8vVqysAAGDfc5ee8xwUnTHP PGwEA6LY/nb8IAEZev b/nc46efS5pIKzr5pTve6Nb pcC 9/dgmuYSeYjDSLrprb8O4/NlZ5HXkzF99w0y9KkggorZtfXvHsW1sbacbYhRfPa1rzxEYPjLj8yRULszmTgbZ eMcVK3YDAED1q1f/6lUzSp1gCve/lOgNkkii1 7yEusR0wIDAylpyumjdr239oufL5 fZbEjqGfv qefee3zig505J74s8uvvWBmdmjTfTc8e0CB569b9DxAypwHnrt2PGsDBes f mZF97bXhcAV9HMX115xdnjUqRQzes33vzprMtmlv/fu9tqfYkjFlx5y1WlOXY1fPriybvffb sOfuCh1eeFfi3tcRuLfOoxQHQjh/ vvLJ17 tD7pHnnHRvBCA8zC03cCAQPSd2D0Ao5kd gSFmsAsQE/EeVGM1RZ6DqZvwqrcEIA40lOSsKPVq6YKBTy cHP95o2tmSekevY3tXupzZ0x/MTCrCSCXfVbN7amj3Z59rd0 O2Fs8fmhxvLy qaOxWwOVKHFowc5XZIYNovlLVlqHXwzuxI58fpnEeIMVHYOqKZ1PJEP9pczdL80D/iInQuZ1DopJh7zLREfL2YlMx/1k3diADE7k5OCLa3eNGWknXCaSkJ728r3xvIm5QQDAH1tlWV1TS0BBWwJeXlDh X7bYTw5mBCBSBetuqdvBpSOfOz6q9CNvXfrwdQC4omTIhmXhbq8pq9WQ5alZm7bjjHHnjBCJ4NGwWszoDzyNEvOZRoPWI6kpf2cq3RIAeZ9cwKU0bHrrtkU0 IBmjJmR5du/eun7V0mpl9bITU4cWZVQdaAkDgCs3PzW5MDM3UJjeeLAVAEhqfr5LSihwx jMq99a/TI43O6khNhD2ep1q1/LHlGYDvtb6756fuVbJz6yOL/ 7fvu/9teBAAXrVy/8omYIwticxcOz6jY3xICgKSc/HQHUbz1dS1ha8I lxKrQe6am92X2gkcOqTUk5Ys2n7rK t2zvrtOFbh09bPH733mQPTrr3vxsnOgx ufmz5/8orH7ng5GWPXR5rgol2ff/071eUn3zN7y bmBms2LD24XtXpD2 bH4qAIQr12 YfdcfX77b2fDxI0sff2byxDtPSVbDP5t25/LX/phGfa0bH10WWWJxLJdcrOIy2j9dcf9LtbOX/vnu8dKefzz29Hc 29zD0ngDAAK9GNz3Cd2MTvXhu1ULGrIAd9ydrn0UVbuh4gv4Pbp6IYAUgfrrW/OnnjYyN4/UfvD1loqs3ImJQTW8OXfKT0fn5zvlQN0XL1Z35hX/5OdDUry13/1r327XhAn5krGLFSlSxfKZRMgVRdRIDQeHpNp6A36CaaCnF7rjziw8Jn3IW3vEIM4fDGg2KLoLncqeJmVOMVQ2VHxT6RlSdNL8/CyH98Cn23ftTJ420UkV/TJohSr zv1fR6ZxjZo9bOfGlpFLZo1OJQCg1O/77JMqT17RSfPysxL0ZBOSFMpKZ0odNQgBWL/S4bcQovlTtFklAjb9o6l NFOGEIIUIz00xwOCB/75100 gJxzH3z4f0Ylhg6 df11r1Rt/vs7lbMvvWl5Kl5x5 c GLn4QW2FzYJida3MxKtXdL9Wxj3rjkeun50lhcMoK XR0wy94LFHzh3q fzOS1fuoLXf7u44L/je23sRQJ54zWN/PD2zY OKax78qivqs8Q9/fo/3o5X3b7BA0PPXv7oonzZv 3hK 783HeIpcRskAOzLy2IVrteNrRAP0Dsw864ZPY7Dz3/yS/ 9LMUI1hp vof39vm/v63Z4xLIpB/0Y0XfH3NunfKF90wOmZOtHXTq184znnwN/OLZADIOe K8/5z2z 3ts89BQAgrXTJueNTZYD8WQun/OXRTQeDp4wBAEiaeckFUzLtAIrn27f6UmKs4k6Z PW6LQkL/rhkXokTIPfSq3/ceMd/Bq69BhqE4JE7mQK5XzFiI0ARAOve ni9ESKnjZld6KIAYC8sLR6W5q070EnTU6CsXc5JDbUAgC2/tKQ4x19X0dBWsa JZM1YOGpIoL2h0110QvL35a2OcTm Lk3zUs0VgwhAKSoUe1ZkR0 LMJuxjyBxKvpKn2EsIiq6lWBLctgUn0dyJDbWN9vyZp0xKsvT3tSMKSV5CV80hDPH2PR GhGD9bHShMKoKBhq3tXUHqShmupmW 6sn43K8rQ1NlFXSW7CF43hrKFY15vqHDV0v2AXrWNoWZ1nooiSJCnqsUL98csNXtCu/TsbAQAa3rz1kjfN8Mad1T4s7v/MSUbpWdOzbAAgywRizGnmzpiWbwfJmZ3ngh0dEOj0dVXvawYAGD5vWpYMUsaJ88fZv/omcnVXX9DHUrptEN2U4WoncDghuScvPrfw2tfe2HHK/xiB4abyBihYNNyptr6cMWZ8ateeg14a25QJNfxYHaj78YYLmZlIyG/oVEAGkNOGpWsmqZSY6gjV dVOwJZdkuPoV4mxivM3lTdKBecP01xMCYWTh8nxa8oQiDz2Pt6ACJa1MpIjJY3WbWoEye52QVd1hzeAFAgJBxRHgowIJCE9lXRVd3j84UB7ENzFuQ5vw95OrwLUkWD3d3iThttB9SIgKIhUdzJQPOIGQp/AzC8NDuIAAIAC6n4vqiACIiGhtgD11nyxuoZ5ILGTOPOIujkHUVF8sdNoJVCkCvW1Bai39ovVtXwyTI7r9umlXjEMa9k4VMZwzxyfvhmAtJPPmDXE9DA48ofYDyW75Axnj3MvjiR1wpKofVAU795AMNHfUrprkN7UTmCAYMtfsOTUt 5b8 EZl3DhfXw3EFEatXTN8vnpPHWhGrAusjMm5IkkS0xEX0qMUVygDABsshFGZDmO36RBs5fTkZ7iDLU2ahNM/q4mJahNWSjBkEkbJZJEVOe9Egjq4ZIEfn/AHG8htdkdccxKbLDLfo uJP0DhrqCVEpyJRIfAsmacNbigkSuIuFmdttJrDRV1tW80ZId3Fs90OIPJKIxaLjcohhh1smBY98lg FAKBTUt7vJsuwqGpMFe5qAuqef99upKRIAhDvKN5VJBYkEAhHPE5ssAVAa9IUiV BxCfvxt0SchSMzYVczHNiwuWXO/PSOLR XHZpLpu lSN02iJHHoOwpBilI8riLfl1y1auvbynSrk Ts0py4LvNB/xzJzkBINyyq6zdNbowSYJOiUQfj9pzxuTDl5 Xdc6dndoPNRW7xOjzn7GKk7OLs8iPu5rCM5JlAAg1l9cGwd13eY4QSOSe3niDtg8WFX/Q7zGJR3MPknbYO1rCKUUEu8sBVU1toQI1PNjmDdnd7gTCHtER9XN8gp1gim9JDeLA5CTsbTjol3JKMmVa63bAntrG5sRwlZdb/ug3uAC72wHl0dIE1JlBLeOYyeIb0VQMUuOMZEqITAiRCJEI0Y7IO76wb80Vv16jf8lf8sTD5w// SUnffjodx0f3Xvd7vGjs0n7wd0VDcFRS9fOGBFlZ4U9a2QGbG2CnSuvuebNzMLTbr194dCBa0VH0em/LPnXX/aGtq66 qIXnb523 H4c y FEffGkTgCMCWO/fiBW/c/fYOkCYBANiypp8z9eWHHl8z4aZzJiVWv7/6tQMFZ908MhFsSm6W3Li1rLI0OcvhSE5JNFblShkzF8/92z2r/vwiXrJgTDq2V237agvOWbIwr3cSxCoxhikTs7iCGYsmvPr0Cxvm3n5aIanZ8NK7NQBjBqKNDgeI5Qy0eAQCAIRaO9sVn1df9is7HXZkEhg/wFQHAZDYszJSD1R/ 1VycSoJdbZW7fcnjpmUKYVqFP7xyM/xCHbZb5yLqokX7vB0KQFfRzDQ5WmpampX3OPmD0nwtNKM7Ex75aaPk0ryHTYJwl5vWwtmFGckmlwQe1Z2ZmW0NDaHnQQbD3rSwmElLMVMFteOt9in/UpEP1SGhXlxwZGQLj5hy5532wMJf3vp9Y82V5RtqQI5rXBs6fQFY5KiMm0vOuvSs3asXr 7o732YHuwwT wE472gl8uu6Pz0Wff2tbkJ0PPvG5u3bNPbwqAPXFA16R0X0o3DXIcvyZHGc5R5y8e//6qMu11k9JLl97dvvqZ54oRPsOZN tuye84odAJA06cJzxz w5vrLnrZuxpZcU67670NS sXvaGByAho2TKvMUxjwyNQKwSY6wDi1mclDHnptvqH31q6cV/dbizJy74xaSt7xxKwxxexL9CBAAAbPlk0xfmVzl7xthheveFEdYIGw4O99ATpeaKA9t3hkBypI4YPWteutJUx/ZrbAvEeWtwi2WOpiC9BDZ/9PWnAABESnSmFgyf8V jilKDDTt9iuwqmDrSXVNX/q0nBCAlOFOLhmYXunwVLebTMdL4a mQ4cmVn3zzn//P3nfHSVWd77/nzp3ZPtsLuwsLywLSFQuEgFLEboI1Koq9GxVjjB9RkxhIYoxKsSBKsJfEiAbI72vDGiyodKUv7LKF2T6z0 ee9/fHbefcmdnGArNwns/Czpz73nPec567933Pe5oCcr9Bo4fFFAN3bTytEgJRbyZ1CR8BClRdiI5EAqAIBIkE5P7x11GkFFGhCgUMKxEFlTCNDDk/Z8aMM0eefEbQ7zn8tTiGQf0NTUpOfroNAKh7/XO3/3FNC2Sd8 hTtw3rxV3SDk8pAgJ9GAG/96dN68qHjDjSinQKObX/2Dw Ykrbtte4IhllI1Jbt9S3qnvlpeUMGiof2OTy2Z1sOgBIaRmFZZkZKRLQiK h9UCNL4xAHBkDRqV7fqxvDiD7 XDXrhvYs/PH8aed52450CeJo6GQv83bUtfu06c3EUdK7oCsrEy7BIDhkLexzVXnV wcFzFlIkiSi/L6FafYCShNByr3BtEqVl b0K6MSmUo0B4KtFft2vzhh /ne0pSHEmpSUkpjuQkuyPJbrfbZLtsl22SRCRzXxn1OElJkhRF6aNzpo4KKLWrHp7zoTykoig15PppW20AwDH64gsG966HcXhKERDo6 gTayAivqrvq2JdcFf YB5pgN7m3esBAEDh0gFA8Xpqf7T2WTHk2fuDJ/pzQoPdI 9I6tE1xCVOA4b8Dbv8DZZUnovYMoDoY97HLr2GIJDKsTIjHT1wGoZZhJtowu6UdkH2otBeJBclaMHfrV2u2b6hHAkTNwwpSZV/ KXUnUh0oREOjbIOa5kQJ9AMysX0Fc30Z0OIUyC5dizpVBACT6iWiEAHdSqcDhhi1/8i1/n3zLUVGKgEDfRvTRRwKJDG7aryCuLyPWtF8JtBlQEoCEhCKhSAAkAuwKJm5HGfEQCAgICBAi3oV9Cdxi7COqicBBItZxkkSKsXxJ3WxANo9aQAQACQgRT4CAgIAAgCQRRCrmDvYJIKKkb goiOvTYKk0E/lTsIgOVZ5bjC2IFxAQEFBBCElJzQgHg/YkMR2 DyAcCqWmOVUPRhDXp2FQySaq21QTw4dBiRAbABBCbJJNIqjJqPEY1L8ekQoICAgIJAhsspxfVNzS2hQKBo7pnbcSHogYCgZaWhpLBg6hkbAgru/CQmWMyyXG6YMAACAASURBVCyhFAkCQQCK6nGS5rbUh0thAQEBgYSGLDucWfmyI6W eo /oV68HhMWhJCU1PQB5cdlOHPCIb8gru/CQmVMGZ1QCUBC7TANlKm golSYI5rElEZAQGBYx2EgDMzJyungJCE3uVdAJFSJWIYP0Fc34WFSv6S6sRQRAVRQSTqhjIQfZwkiNiMgICAgA4lElIioc7lBBIMgrijD x0XnbOr3quJAEgiH3 eHQBAQEBAQGBoxLEhE2d8MsmSqD7LtwJBgICAgICAgICfQESABBEYvoxR1QdAQEBAQEBAYEYoMwPB3NKlAjGCAgICAgICPQ5cNN 9YMLxLRfAQEBAQCASCSsRMJiMUSCgxBik2VZdhgpgrg imgqdXREpazfSxCRECBEDDIJCAgIAACEgoHWloa66r1erwepNaYtkCAgkpSWntGvdGB YX/VfAni iiiqewijKgMQVTMbWV6VzsBAQGBvgYlEm53t1bt2Vk bHRmVg6RbOaLEdUunxnEJup/rASyC0e138j1LAn3C9DIxhQwggoWWQAAJGqJaN4PxnfCv86NYi1n7KHlpY/A1goIcNVQT8FBixp8/laFjHqh5RYw1ESwHGFMkGsV/aLZOojsdaRKW2vznu2bU9OzMrNyQwFvR8RBZ9whV8Gecgc9og 0VjYzI5bLnTEIZluinhv/THWPRDgIHgHNyIiVRzDbJz6V/HJ6om6LB7GgncFEACRJUpACgCRJoMQUFhAQEDhWEImEa6p2Vwwfk5GZAwCWE2F0E2JYRP7tDwR0eUIAOWHUUgGJaUFUAcqaHmK /g3DY7E2yKZY/RAtW4vallpaDCkxCjQ8IDTsFxpf0JoRojbf0hzRMepGgJHXW0K9wPoH7FgQo7aWDRKuoZBTnJDM7NyK4WMqd2we97PTOyHO9DA0w4pgcVQ6405V3LzJwh3o/k9X6GMS2YI4T8PS1HxtusAgELa9iN6kUcEqhkQwGt7M3OTR8uzH5ZGYLclkZvgvevXjU9n1nYFkCYgCFCQw3Bd1pElAQEDgWAYitrd70tIzY8 3IGzcBbVAgWmB9E odoD57qj6vufEDXn1N7XI6xbONAB6H9nouiMnzLpJUXlZaxrjIx/3MK9Qvi0IIVYbZtp7szfPekZmWIGz5ahZMgAw7R aGaHhDfDxEeNjWnpmu8dNiBRNHOcYqDmZ1hhNVTnudIctijuwhh74 hLU2ekWfWxVkPE eswgmKEXNmPtWWXRAYnAPOTUUEJzRjriEViPkFNKyyUuj8BQGae6MWIzsqG9PufXemCTgICAwDEKpACgTbbQXpDGixIs3whQAML3p0EbLGE6qkzmAECQ80IIgOnGmEYB Dc9YdMQMapUq2djzaBL4MwAu4sqJ4AxrRHre5jNxYSZom7SnR2uE68nEfM7sp14AiwX7O08caowYe5k4iYAWqTC0opaI3bEHQA/3EP0sIVBH/ 0aFI9oS92UqfoCYmWVkVOHwQusBalHeO0mn6M7v8YI0sIwHnFlkIJ8E9CFyCrHgwiAiqEIEgEmOEtAQEBgWMXhBD1lYq6ySLm8L5puIj sjc26NIvGx1hzVZp5s8wXeYVLuQOuu2PsahUH4IiTFkW9H5fFLkxCi4cxegFwKlrEbOYVd6ZMD4ZI1igt4F2lfNguEQCunU0TJdJnCmvq0MY4vQCdLUNKpDRjOMOkB1fYTOJRR92mT7kPvY DOX173FJRP6ZI8x1yyX1Ue6IRz5Jbx/OyeGeDWLQ1U0vRDZDcIgI jGTAgICAsc8CBBKqWqTtDc6BcamgW5Go0wjGPF4YnTcEYCfeKK rgkbadALNmeExDA4TJAf9DyjrnPV6BJi9rK5fGJLGEEG7rJ1EEP9x5gXfcIKM pGUJ9EY5ahz1phwgJM318LYxGgalaGK2IQp11Twwl8kard1O0qYUrpAnf6ANJB0wdWBmPQ1SMGYySQuBLdI9G4kfnUCY/IU2eJwcSnsisghMjm4J1kQ6SAVOyVBwDo3fXuU4vf KrWBwBpk/ y7M7RyR3eENz57M0PrG6F/rMXLr6wWLZ87UqRPbjF0NZfuXLx4tfXVrcDQNpJlw/f sZ3fii75oUnzi2ydScjAYHuQmlcde vV09 fPGFxTL7uYu3 zfOu25ByoPP/mZkx39gRwhEtb3IvOJ1t0Z/gSPbnUdjFEMLErB3aq9rJlxP fc9ENOiGPdEjW8Qq/nhrA83OBE1YaYLNVZNEvpcG9a48qeMLE0j6HNt MSVf9rI0nRizQyBtXdmfAJMK8fZPORqi4BsdMDooDPRGLbXzjsbamyFaW228LjEgW5WNZPMxCY65Q6BdW6QCSoYJTD1iNU4EIs Rv osSUrg hzrf koeC0EaXp8ew0wegrGOd3h3oal4wb4jgu1pbsgEcAJjqmphCqXoxHZXQtOKieqE174aj7ysSS6 OI1P17zp3LqwEG3/zSY6fndvW8d6Xug2eWfVULkDb4hJFF cdlyd6v5l4zfytIY 5/85ETU7utR/TtB5khp239R88uXVsNkFx2/OiSgqGZbVsPKj BRAB6vnjgukd/cpz0m6cenpwtAQD4Nzx60x 8d7/ewQOjHHjvnrs/mLZg4S8Lu UNC8QEgegXI2fgNCHQX8RWzwaZQLnesectjTnYRLi8o9/ovONiWIhwy b3K92cisllU4aXpvFWsdMOKl8uVRCApJVmpXta3BQBSFr/rHRPiydskTeqrqdRvjBu9AHZwQpAprPeucHTjB1fmAVsVKYz4vR5I aKKwt3VlcDtRAal6cWoNPp5pXjiebUJgDhZoY4YktJcRbkllTkOpMl9ga03I0AQFL7Z6exXPB6os 14bPGwtOG90vlfMsYz0A8EgGA8tIGj4gspdpHjkdgqbTyCLrvEvWk84gRlVH/SqyhFm0KsGzkTwhqE21EVAbCTXubAQDKL5/70JkFEgB493crg6SKm154/XoEYpMPvUUJN1c2AgCUXHD/3Av724FGzjsDEcBmP0whGRoKocMh4j 9DgIQ u6VlbtOmT006chqQsNhsNu72hU4akAIiVrKG4Wo4QWwzCk1BiaYPjyxvPQJZwnMjDQhAsweJeZ9AAARRCA5U04 sdj4C7Sl5iYFqprcISaL2KpbJ4Iie0X9TZEanxWkEYtq5o2E771bMlVrZ0YFeKdCyxLNBMPx6E4X26hLj4nTwy7GP8YhJIyQmYdxPc64kL5GKYq CCKQ3OnjTy6x0VDI29BYua5yy fuoZMH5SbFzRWpwQvFOJumUIoAUnpZdnpzsyfMe1WWGkeRCGDMc45qHLSQCGwTsqUwXovufMZo644RPTpEKBAEoJQgSAg2IBKTp2lnEfFYG1rCUP3at158/aMN 9oUSC0aO 2Sm6 cPMDetOreW5dUAgDAnheuu/AFKDtrmu//1jQAANBNf710JgAMvnPZn8/oIMgT3LXUGC36Rfj12 79p4u9Xc6yR1rDfIbPXtsl9ZJ5jmjLR/fftGAHAADUvHHrJW Yl9QBpog2blUy85aprtXvrK32OYomzLrrnl9UpBJQWta/tuD5FRsbaM7wc6 c1rjs6bVeGHTjMwvOzbd1oIA FlZywS1Tat59 9v69HP/8vyNFdEbTQscHKTUE84Ysv39F788Z970PMvTRr27Vj239M0vKt3oKDz 7Btvv2xCfnjd/Lue36fA8jtmLgfImPLoC7ePZH2gUP0Xry596f3N9UFIL5twyc03XTAiQwrXvnX3bz6beP2E3f9ZvanOnzxoxs333jK5wK6mnzJr7I7VH2xtyr/s8UXnB//PWmKHjnrM4gCo 8d/LXrmre8OhJyDz7piWhgg5RC0Xe AQI/C1RjL7dAHKFQBswBdiIuiGLMt9BzM2ITVuCEAcWRnpKK7xadKhYNef6TpwPq1LbnHZXr3Nrb5qM2ZM/D40rxUgu0HNq5tyR6a7t3b7A7YSycNL4407N5a3 RRwObI7F8yeIjTIYHpv1DWl6HWzjuzIp3vp3MRIcZFYeuIpqjljh60uZql aFnxEXZXM6h0Ekx15hpQny9GEnmP uibkQAYnemJYXamn1oy8g77vSMpA827d4VLBqTFAoD9bVWb611NYcUsKUWFQ4cke 0EyOYgQgUgfpaq7fwMsSz7fMaH8LmF9dsBpBLKk4YlUZ8LdVb63SxAjUrs3bcdo68cwJRPBo i1md3ucRoh5zM5kQAoQQSinKMgDRozLEiMVJAJQQybI7z1ELpfGTx 57Yp0fSM6QUXneHTs2rlo8p0ZZMvf4zP5lOdX7miMAkF5YnJlWmlsYLM1u2N8CACSzuDhdSipxdj3Ygo7cgaXZLuZ2W1p Svve7bVchpagRjz1Hpyaz0oSm7N0YE7l3uYwAKQWFGc7iOI7UN8cAQtq3l3yZv6g0mzY21L/9fJFK45/Ylbxgffm/ WfuxAA0mnVqkVPc72YDhQw8lyx5DVwOJ2pScdcd/0wQco8cfbMzb99/d1tE28YwRp82vLFk48s3XfS7fPvHpuy/6MlC f9UV70xGUnz114Y7wBJtr w3O/X7D75Nt f/3o3FDlJy8 /siCrKfmTs8EgEjVqk8mPfin1x5Kca15Ys5TS8eOfuDUNDX985MemPfmn7Kov2Xtk3OjSyyPF4yLV1xO22cL/vJq3aQ5f39opLTznYXPfe 3TT0kjdcLINCFzn230EHvVOW62goQtw293p1kdRrRsq/mDAq5sXAkgRaOBAS/G40wcXFpG6D7/ZUJlXODo5pKY3FZ5w5tDi4hQ5WP/lyzWeovKfndMvw1f3/f/bsyN91KhiieorZZEiVSyfSZReMVSNtnBwUKatK AHmHr7vIKOuDMLj0sf8t4eMYgLhIKaD4rO0hRlZ6MypRyqXJXfVnn7lZ04vTjP4dv32ebt29JOGp1CFa1WqFAl4Nn7TbRM pBJA7atbR48e LQTAIAyoE9n39a7S0qO3FacV6SLjYqVaGsdqbWMZMQgI0rHWIeIeYAk 7EaHrYJEqpbNMeRpmwi 0PvX6Jg9C /76yzg9QcNHfHr92SHJ4/4o773i9ev2/VlZNuu6eeZl40wNf GHwrL9pM2xmlKtTW0bfuqC7U1vs/c59YF6O9XZ9royREty5vivq7Zt0XbndlCPOU 780 /wlt994oX F8x7cmaxHNj0 E0PfOG3qtH/soVPXNTf 8UD1y3aQuu 2 G OPT e7sQQB5928I/nZHrXrvgtr993d4VBUp0IefE 5 4c1KeFImgmJlxSEDsA866atLKx5Z/ ou/np1hJCuN37zzg23q7284a0QqgeIr7r7sm9veXbl75l1D4 ZEW9a98aXjwr9dM71MBoCCi2 6 H/3/Xdj29RTAQCyJsaGSmDFA88dwT/vHkuv2hU4cBAKROuOqyE3LtAIr3uxXdKTFecaeO/ubdDUkz/jR7WkUKQOF1t/609v7/9V579TYIQXrYXovI/YpzNQoUAbB xZpVRoqcNWxSaToFAHvp5PIBWb76fR6anQFb2 SCzHAzANiKJ1eUFwTqK12tlXsaSd74c4f0C7a5PM6y49J 2N3iGFHgb9csL9VCMYgAlKJCsXNDduQMCbMY zASp6K79BnOIqKi215bqsOm L2SI7nhQJOtaOJZQ/K8bY1NmFFRlPSlK5I7zKa/oRExdCCeTDiCioLhpu2NbSEarq1pshVOPHtInre1oZGmVxQmfdkQyeuP9V2pzhFDh2NE6lJrySaBPhTFGiAKQEFzHY90NQ45aPvebQ0AAK5///aqf5vpDdtq/Fh xIdKOlbP3oOgWeH4k4rtIKXkF6XDFjcEPf72mj1NAAADp52UJ4OUc/z0Efavvw13QQHdlcmZfP4peTYAkOVjIIx3hCA5x866qPT2N9/ecqo5BBlp3O2CkpkDU9R2l3OGjcxs37nfR O7MmHXTzXB p/uupwZg4Ril0cBGUDOGpCtvQuk5ExHuD6gdXzyKwocPSoxXnGBxt0NUsmlA7QQU1Lp2AFy4royBKK3vU80IIJlrozkyMii9esaQLI706G9xu0LIgVCIkHFkSQjAknKziTtNW5vIBJsC4GzvNDhc 3y BSgjiR7wO1LHWjX7ACCgkj1IAPFw 4gdAvM FLfIA4AACigHveiCiIgEhJuDVJf7ZdLapkbkj0kpYggAiIgKoo/voxWAkWqUH9rkPrqvlxSx4thWkK3T0yLou3pRIAQYgOCiNrDSWzmvjKE2ABBPb/gWJo0k3XyWRP7mR6do7ifvQPpw45eU8 RqjpARH3fxYgkxvZfO1IgLSdFjCwdetiKZ8w bcX8ZR ddRWX3k2bgojSkDnL5k3P5kkL14L1T94YkCeSLMWaFNrz4oJbAcAmG2lElhP4Geozb0JHdkZKuKVBG2AKtDcqIW3IQgmFTdookSSiBu VYEhPlyQIBILmHFKkNrsjgVmJD3ba75HVpGfAcHuISqnpycSPQPJGnT rhJ8cGWli15/Ek6m2zuaNJbZ/V01vq9 biMcgMjvg2YCoAABzXxlt2i8Scwbz0QSMBMPhkL7KTZbl9LJhebCzEajzlItvGJchAUDEvXvdVqkkmUAw6n5ikyUASkP cE mEkXf3nGGUofq9QpISungXNjeBPs Wd88ZXq2e8Oarebivq4p0DffF30OJG3EFb quOWNtzaUoXr2iJxXUQDfr98XmDomBQAizdu3tqUPLU2VwCOR2P1Re8GwYvjqi62eqZMye2Cm4pfYHlM XnFyfnke Wl7Y2R8mgwA4abddSFwdl fw4Q sEuFtg4WlUAo4DWJR3MNEiJz/qOZTiki2NMdUN3YGi5R00OtvrDd6Uwyq83umpr4O6iyA0yJralBHJicRHyu/QGpoCJXpnVOB ysa2hKjlT7uImPAYMLsDsdsDuWTFAdGdQyjiuW2IhlXJAASgQJUAIoEQXQeLeY 8pIxEZpBPTozWFS97Bhz7KbfrVM/1I8nHLx14zlUnfvTk9 6PH7ljx8ih aRt/45KV2jInBfHD4qxoMKeNzgHNjbCtkW33fbv3NLTf/u7c/t3Y3pI9O1nWFP4SQeOjtTrHXYcZWf8suL//WNXeOPiW694OcXf5mf/9DtUoFfKF g6bIVTr5zx9kPvbQFpDACALe UC8e99thTy0bdc GY5JoPlry5r T83wxOBptSmCc3bNxaNTktz FIy0g2ZuVKORNmTf3nw4v//jJeNWNYNrZVb/p6A06ZfW5R1zSIV2IcVyZucSXjZ45647mXPpn6u9NLSe0nr66uBRjWG210KEAse6AlIhAAINziaVP8Pn3ar5zisCMjwE4b4NKJPS8nc1/Nd1 nlWeSsKelem8gediYXClcq/C3R39ORLDTfhNcVU29iNvbrgT97lCw3dtc3dimOEdM75fkbaE5 bn2qnVrUiuKHTYJIj5fazPmlOckm1wQe15 blUsGZvDTkIN 71ZkYgSkeKKJXTgLXrar7afDSIQNvymRWZk7S59ZFGSCCg9W8bW12DLn3bfo0n/fPWtj9dXbt1QDXJW6fDJp8wYlhqTYHvZ dedv2XJqh3utrr9bSFXoHvjjNG328utKfykg 6p1yPYS345937Pk8 v2NQYIP3Pu2Nq/fPPrQuCPVkmHStwDDwdCYeUIZfOGvnB4q3acydlT57zUNuSpcvvv8sD9oIxZ899 OJyBwCkjrn8opGPLrvz uesi7Gl9HG3zn8we9lLS a 7QVIyqk4YdqsuFuGRiFeiXH2tohbnJQz5Z77Djz57JwrX3E480fP MWYjSsPpmEOLRLfIAIAADZ/uu5L86ucP374AP1FgVHeCJsODmf/46Wmyn2bt4VBcmQOGjpxWrbSWM4NgWSPDW4CbLHElFughs vibzwAAiJScklkycPzPh5Rlhlzb/IqcXjJusLO2fvd33jCAlJSSWdY/vzTdX9ls3h1HJlBH w1Mq/r02/8pIPcbNHpYTDFw18bTKiEQewETgDriLQFIhNhMa0jmTrwBtVnqVEFFQSWkRCKRyKBzM2fMOHPkyWcE/Z7DprzA4QX1NzQpOfnpNgCg7vXP3f7HNS2Qdc6jT9027AjvyCYgcMQR8Ht/2rSufMiII61Ip5BT 4/N42OltG17jSuSUTYitXVLfau6V15azqCh8oFNLp/dyaYDgJSWUViWmZEiAY34GloP1PjCCMSRMWBUuufH uYAsp8Pd 26gT07fxx/2nnulgN9kjgaCvnbvC117T59ehNxpOQOyMrKtEsAGA55G9tcdX7FznERUyaCJLkor19xip2A0nSgcm8QrWL1tQntyqhUhgLtoUB71a7NH374fqG3f2pyckpScoojKdnhSLI77DZZJjbZJtkkmzlGIgEggKItY0ro0JNAL0GpXfXwnA/lIRVFqSHXT9tqAwCO0RdfMFj4MQICKkhf6NxHfFXfV8W64K78wTzSAL3Nu9UNHxQuHQAUr6f2R2ufFUOevT94oj8nNNg98o6kHl1DXOI0YMjfsMvfYEnluYgtA ivb9jDLreOLZbAiDvtF5gZW8Z8GFk9fcncdqbPzv0W6D4kZ8XYoV t3b6pHgEcOQMnTJl59a/Y9UoCAsc0iHlupEAfADPrVxDXtxHPDTH8E9WdMfwWGYwFS0ggodeZC/Q6bPmTb/n75FuOtBoCAgmK6KOPBBIZ3LRfQVxfRqzdftUZvephlCgRSZKMrSKorG4FnPiL7AQEBAQON8jRuDPFUQxuMfYR1UTgINHB6BAhkkS0cSZ9ZxmZqIvbUT9 nUqQ6JskCggICBwOSBJBpGLMvU8AEY1euiCuT4OlkgUhEoBEEAiyh5VRACn2tAjxBAgICBzjIISkpGaEg0F7kpgI3wcQDoVS05yqByOI69MwqGQTY7olRqIE2sQZgpQYC5fEYJOAgMAxDpss5xcVt7Q2hYIB8UpMZCBiKBhoaWksGTiERsKCuL4LC5X8JQXQPJWdACWmryPJ jRg7X8xaUZAQEAAAGTZ4czKlx0p9dV7/A314sWYsCCEpKSmDyg/LsOZEw75BXF9FxYqOxCzpMgxwzZieElAQECAEHBm5mTlFBAittpKaCBSqkQM4yeI67uwUGmAEJs6M4aQGAdoyABAKWWkiZgoIyAgIKBCiYSUSKhzOYEEgyDuKEPHfokUM/gm4nECAgICAgICCQIECgRQ3zCIAiIBAKJO RXzfAUEBAQEBAT6DNg5viokAACUCNh4IeHZCAgICAgICCQEiL6VjHrukvafDuuUKPU8pph7BgsICAgICAgIHCnEc05kQAnE2UsCAgICsRCJhJVIWAzBJzgIITZZlmWHkSKI66OIptK8hOzR5xJBMxbD7farLV8S1AsICAgAhIKB1paGuuq9Xq8HqejyJSiIJKWlZ/QrHZhf2F8dcxDE9VFEU9lFyPoYk a/EFDE2JKAgICAEgm3u1ur9uwsHzY6MyuHSDbz3YjqcXcI qtTHcQHVgLNL/pLWT3yzkzmfgEa2ZgCiLFlAQBQmz2A5v1gfDd1IcY1TQUWyEmZNTIMAlcNAAQ09GSLNfO3KmTUCy23gKGmOoWTyZIg1yr6RbN1ENnrSJW21uY92zenpmdlZuWGAt6OiIPOuEOugj3lDnpEH2itbGZGLJc7YxDMtkQ9N/6Z6h6JcBA8ApqnQlp5BLN94lPZ4XJ69ZRsdZpvnDOYBAQEBI5xRCLhmqrdFcPHZGTmAIDlRBjdhBgWkX/7AzHO5SVEWzaqC6OWCkhMC6IKUNb0EPP1bxgei7Vhl2gQqx iZWtR21JLiyElRoGGB4SG/ULjS9TSEERtt1VzRMeom1ol3R4SQx4I5x wY0GM2lo2SLiGQk5xQjKzcyuGj6ncsXncz07vhDjTw9AMq3pyD2eXO ZOVdy8ycId6P5PV hjEtmCOE/D0tR8bbrAIBC2vYjepFHBKoZEMBrezNzk0fLsx WREO50av0R4P9eOqKyyzsDUdOVkQhGUS4gICBwjAIR29s9aemZsedbEDbuglqgwLRA idUO8B8d1R933Pihrz6m1rkdQtnGgC9j2x03ZETZt2kqLysNY3xkY97mFco3xaEEKsNM 292ZtnPSMzrMDZctQsGQCY9g/NjNDwBvj4iPExLT2z3eMmRIomjnMM1JxMa4ymqhx3usMWxR1YQw98fQnq7HSLPrYqyHgfPWYQzNALm7H2rLLogERgHnJqKKE5Ix3xCKxHyCml5RKXR2CotFaTcFXRnWwKxlwZQoiYHSUgICDAASkAaJMttNcoIayJYb4RoACE70 DNljCdFSZzAGAIOeFEADTjTGNAvBvesKmIWJUqVbPxppBl8CZBMToI24QLVK8wUJOdbUq1jvMm3Rnh vE60nE/I5sJ54AywV7O0 cKkyYO5m4Cegm0tKKWiN2xB0AP9xD9LCFQR//tGhSPaEvdlKn6AmJllZFTh/dg iMR2DjatZBQbXRGK/YUigB/kmID6M6snqiQfSGMwICAgLHOgjRTt9F3WQRc3jfNFxEf9nrr1BzfEjvCGu2SjN/hukyr3Ahd9BtvzlqZOqkXSNMWRb0/oscuTEKLhzF6AXAqWsRs5hV3pkwPhkjWKC3gXaV82C4RAK6dTQsm0mcKa rQxji9AJ0tQ0qkNGM4w6QHV9hM4lFH3aZPuQ 9j4M5fXvcUlE/pljVwJZLqmPckc88kl6 3BODvdsEIOuWJNRVMQFDzzgixWVcwHZpGFBAQEOh7IEAopapN0l6OFBibBroZjTKNYMTjidFxRwB 4on6uiZspEEv2JwREsPgMEF 0POMus5Vo0uI2cvm8oktYQQZuMvWQQz1H9Nf1iesMKNuqm1iFTbMHjOaAUzfXwtjEaBqVoYrYhCnXVPDCXyRqt3U7SphSukCd/oA0kHTB1YGY9nw6KRY1t/G8gAAIABJREFUiOLMmkDiSnSPRONG5lMnPCJPnSUGE5/KDsCeGCl1sYmOdQR3PnvNJefNvOTWd2ojvSt8mHM7/PkLHN1QGlfNuVx7eNjPXYR/47zLr318a CQ6XdwIICIiBQppRQpRYpAAQEoIAWkQNVLlCJSREoB9U IFDUJLQ0pAkVA1O7V7qSU6jcBqpcZUFNIz0aXRtAypMwPdzcFqqnYlR gFKh p9f1w8ot1R5ECrTd9cPKLdVutURkFNGqymmow6in3h6qDKcqRaRmflRtHdQaGlWd9DI0BdV71U o1Q31otk exzidO70m83SO eOsq2t59wBfdGNE4s jkGe/GgGaXv99ys3V7uVThk0SWDy10vsjETK3h9FotZYTJ60qzwiGmqqPIKWf3wqo/4mibaNrxFkI9y032Mdkbp/z7lzebWZYHeWjJo884arTitL7kV/z/vV3GvmbwVpzP1vPnJiak8EBI4NoOeLB6579CfHSb956uHJ2RIAgH/Dozf9wXv36x08GMqB9 65 4NpCxb slD8bR88CJCoYXe09lyJOUSh9vvN/qi6JMS4Ue26Ivc MQebCJe3pbfMfELjGwIAhFs2v1/p5lRMLpsyvDSNn3HR6UuML5cqCEDSSrPSPS1uigAkrX9WuqfFE7bIG1XX0yhfGDf6gFzcH5nOOh/wAHY4CI1fiNbCLGCjMp0Rp88bMVdcWbizTo1BZtQQ2HuMYtGiHE80pzYBCDczxBFbSoqzILekIteZLLE3WIehEABIav/sNJYLXk/0uTZ81lh42vB qQRiPUG8PJMxm0Z5aYNHjZgOeASWSiuPAECoWp7lSecRIyrDBmH0BADtiAJZLZzEy 8YRthds3710w T0udvqHAkVdz0wuvXIxCbLCyEwOECAQh998rKXafMHpp0ZDWh4TDY7dYFBUc9CCGdr uMGl4Ay5xSY2CCec8Sy0ufcJbAzEgTIsDsUWLeBwAQQQSSM XkE4uNg/RsqblJgaomd4jJIrbq1omgyF5Rf1OkxmcFqRFx4/NFzVaZww6WTNXamaNEvFOhZYlmguF4dMcyGXXpMXH6mJLxj3EICSNk5mFcjzMupK9RiqIvgggkd/r4k0tsNBTyNjRWrqvc8rl76ORBuUlxc0Vq8EJRiV0vShFASi/LTm9u9oR5r8o6EsZnrqZhLBJBby LN2oyambHeC268xmjrTtG1PzkGDBcR82VEbN9OQyaXHTs9yf7/wzr ucUPTj3vaaEV eNfSmx9Y3Qr9Zy9cfGGxDKC0rH9twfMrNjbQnOHnXjmtcdnTa70w6MZnFpybb57M6a96f9GCV9dUehxFE2bddc859rdvv/efLgAAuumvl84EgMF3LvvzGbm6hYjse/m2KIFnr42d2y8qUgMb51097 sQDP310r9Pz5b82tfj7n7hbz rf/rGB993Q lFv55e8/YbX9dB0clX3nPLqe7/PLFk1aZGUjDu4nvvuWBEummc0Fe5 sknXvtsny ldPKsO359zuDUY85yJRqk1BPOGLL9/Re/PGfe9DwLG9S7a9VzS9/8otKNjsLjz77x9ssm5IfXzb/r X0KLL9j5nKAjCmPvnD7SNYHCtV/8erSl97fXB E9LIJl9x80wUjMqRw7Vt3/ aziddP2P2f1Zvq/MmDZtx87y2TC xq imzxu5Y/cHWpvzLHl90fvD/rCV26NjHLA6Aun/816Jn3vruQMg5 KwrpoUBUg5B2/UOSM9ejxjL7dDWXvMzJRjrzkVRjNkWeg5mbMJq3BCAOLIzUtHd4lOlwkGvP9J0YP3altzjMr17G9t81ObMGXh8aV4qwfYDG9e2ZA9N9 5tdgfspZOGF0cadm tb/IoYHNk9i8ZPMTpkMD0Xyjry1Br551Zkc7307mIEOOisHVEU9RyR09NEj/A1P37o0JuvEOhk2KuMdOE Hoxksx/1kXdiADE7kxLCrU1 9CWkXfc6RlJH2zavStYNCYpFAbqa63eWutqDilgSy0qHDgi32knRjAD1aEiX2v1Fl6GeLZ9XuND2Pzims0AcknFCaPSiK lemudLlagZmXWjtvOkXdOIIpHw2cxq9P7PELUYx59nQEYi7HNoTUBAACQktLS7AAAyUUFadEWPVzz3vy//HMXAkA6rVq16OmY/n/1248/q07TD9V/vXzRilH35g4szXbtbwEAkllcnC4llThZW4COGAK2OLkd/8Ssgs4rsv/fi19SP9Wv 8eDlW HGtWIpuuHN//2z OXXjfYOOhi/9sLnnc4sxzg8 //4oVHlNxF9/8sUzgzRxZS5omzZ27 7evvbpt4wwjW4NOWL558ZOm k26ff/fYlP0fLVk474/yoicuO3nuwhvjDTDR9h e /2C3Sff9vvrR eGKj958fFHFmQ9NXd6JgBEqlZ9MunBP732UIprzRNznlo6dvQDp6ap6Z f9MC8N/ URf0ta5 cG11iuQ1iI15xOW2fLfjLq3WT5vz9oZHSzncWPve93zb1kDReL4BAFzr33UIHvVO9 261goYuwG13p1sfRbVuqPiDAa9uXog6/SBwoKV43OmDC4tI3YffbKjMKxydHFLTmwpPOHNocXGKHKz/8uUaT1H5z87pl Gr /7/7dmRPmpUsUT1lbJIkSqWzyRKrxiqRls4OCjT1hXwA0y9vU1aR9yZhcelD3lvjxjEBUJBzQdFZ2mKsrNRmVIOVa7Kb6u8/cpOnF6c5/Dt 2zz9m1pJ41OoYpWK1SoEvDs/SZaJn3IpAHb1jYPnj1xaCYBAOXAns8/rfYWlZ04rTgvSRcblapQVjtT65hJCMDGlQ69pxBv2i8xpsowKRB9MrYA7P7HHddcd kVD61sAnvZ9DuvHR09LyG09/33diGAPPq2p199cdmL901Ij5lV1vQ/vPTGO89cXQ4AUPfdnvSzH5h320gAAGn0rQueXrDkiV9PYL0Fe79zOxCw5LbDbTyJHcXiCs579LU3X7pjKAGAUKP9rIdef3vpvWNlAGjc FMTG6EsuejJl1945ZW//qoYAHxr//1Nk9gx8YiD2AecddWk0MfLP3WxXCmN37zzg23qHTecNaK4eNApV9x9WVnNhyt3dzR5lrase NLx4Vzrpk oqSgcND4i2 6OH/bfze2qSRnTZ590chMmTiKJ557grxn3X5tk83UCVdddkKuXbLJ3u9WdKfEeMWFG795d0PSjDtmT6soLCyfdN2tp2b3QjMdMhCC7BzJQ/tDkVJUKDV/kPmhVKEsUNF/ALB xZpV72769qPN3360 dtPq9rClFIAsJdOLh9QBC37PDQ7A1xtckESoQBgK55cUd6PtFa6dv1vTyPJG3fukH4pik9xlh2X1r67xZFlA6pZXqqFYhAB9EI5xFNV1Y2acz8Pww 7GPswEqfTp3STPlVVRFS0H7ClOmyK3ys5oOFAk61o3FlDipMj7hbMqChKcrkiucmS4RQihg7EkaHhCCoKhpu21 7ZvH/XhpomW G4s4cUp4Tbmml6RWGSqyGS1w0SlcNKopXKzqCGYMTEj2iEPW51OpVUVDF6eHZ0rxO9NXuaAAAGTjspTwYp5/jpI xffxs1Byvv1DPHZNrsyYMHZcAeDwQ9AQo9n/IQKzcNJP5CtIJJpw5Js2HpACfsaIPsidOOc8pkwKBs2NgAAU Qca4Lf/azgcmEwICfj897a0UjHNjhCp Rf4SnaAiA5Bw766LS2998e8up1xqJkcbdLiiZOTBFJV7OGTYys33nfh8dGjefsOunmmD9T3dd/gaTWOzyKCADyFkDsrV3gZSc6QjXB9Qnw5ZfUeDoUYnxigs07m6QSi4doIWYkkrHDpD/1/XWOMwgEL3tfaIBESxzZSRHRhatX9cAkt2ZDu01bl8QKRASCSqOJBkRSFJ2JmmvcXsDkWBbCJzlhQ6fa5fHpwB1JNkDbl/qQDvoszkVRKoHGVQjk7hgxpf6BnEAAEAB9bgXVRABkZBwa5D6ar9cUsvckOwhKUVEX5akKP74MloJFKlC/a1B6qv7ckkdL4ZpCd0 MU1azE47N8BkJiXyc3p4MPjm5X8 ueE/j819bXv1x4sfP27o/Bn58YLoceZSaUjJTJIAACTZOuW7J4idmxp1VkOFSjAQtQo2KT1JAqCS3QYAkOxMkdThxGiFxLL8RIWteMbs01bMX/bRWVdx6d18oBBRGjJn2bzp2XwsNlwL1neEMSBPJJl1k7tTYpziglsBwCYbaUSWEzg03JW5hwkBR3ZGSrilQRtgCrQ3KiFtyEIJhU3aKJEkogbvlWBIT5ckCASCZtQPqc3uSGBW4oOd9ntkNekZMNweolJqejLxI5C8UefPKuHXz0aa9rPicWSqrbN5Y4nt31XT2 r3JrrOoLmCScACyZ454oKbL/3sntf2K1veXLnr1OuGcddJWungXNjeBPs Wd88ZXq2e8OardHL4mKD2GQJgNKQPxw9ga9LAqyiyU4HQBBa97dGINO/9cudB Fn13/9TdUlA8qh6n/fNAIAFA7Nt/c8N4FeBEkbccWvKm55460NZaiOCct5FQXw/fp9galjUgAg0rx9a1v60NJUCTwSid0ftRcMK4avvtjqmTqpJ1Og4pfYHlM XnFyfnke Wl7Y2R8mgwA4abddSFwdl fwwQSvaY30aCtg0UlEAp4TeLRXIOEyJz/aKZTigj2dAdUN7aGS9T0UKsvbHc6k8xqs5MoE39CJTvAlNiaGsSByUnE59ofkAoqcmVa53TAzrqGpuRItY/roAYMLsDudMDuWDJBdWRQyziuWGKjm85on3S9DwfkkjMvGW0HgKY1b33vtlgGR9kZv6wgAOGNi2 94uprr/7b196u5mvPG5wDALBt0W23zblz/upq67MVJdCBk Tod9KwJABwrfjD3ff99ta/fNVlNWJh/7/umn3jVVfd/1YtAKT87MLx1jUzAkcMtsKpV86w//DelqD6KNryTrlwXGTNU8s 2FZbv3fd6wvf3Fcy4/zByWBLLcyTGzZurWpyuz0BdnqNlDNh1tTU7xb//eUvdtS4Gvbv/OG/r/wj vmLq0G8EuMgXnG2vPEzR7lXv/RJdRAxVPPJq6tr42WRACDaIukE/wEIt3jaWv0 T8DnCfg8wVCEPamYk TTiT0vJ5PWffd1azAQ9je49u0NJA8emCuFQwp/e3RWifjDTvs94sp0ibiI29vuCfrd3tZa157v9zYozuOm90vy mlOfq69ad2aAx5vMOQP ppaanc2BxSWC2LPiyNjc9hJqGG/NxiMKBGIK3bEq98lKs0/xg59Gy4qk/Bu7OGElHPKxdMyN7/fFvz2rU/qxo7gLtpLfjn3fs Tz6/Y1Bgg/c 7Y2r988 tC4I9We7Mk7SXnX/d VuWrNrhbqvb3xZyBaz952iB NMfiPOUm 8417109Q5PTWPKWTddW7t8 fquxoesKL347rNd77z2eRskF//88l/fOUEsX0okpAy5dNbIDxZv1Z4XKXvynIfalixdfv9dHrAXjDl77sMXlzsAIHXM5ReNfHTZndc/Z12MLaWPu3X g9nLXloy920vQFJOxQnTZqV3uesTr8Q4e1vELU7KmXLPfQeefHbOla84nPmjZ/xizMaVB9MwhxZ9ZMctbP503ZfmVzl//PAB p8vYze1r2w6OJz9j5eaKvdt3hYGyZE5aOjEadlKYz37YmJbIMFbg5sscyQV6SKw6eNvPgMAIFJySmbJwPE/H1KWGXJt8ytyesm4wc7a t3fecMAUlJKZln//NJ0f2WzeXccmUAd7TcwrerTb/ ngNxv0OhhMcXAncidiG7PeCAPTbhZ2y8YqYJKhCphGolQZeB5GTNmnDny5DOCfs h0bRPg/obmpSc/HQbAFD3 udu/ OaFsg659GnbhsmJsoKCBwNCPi9P21aVz5kROeiRxhyav xefzmPLRte40rklE2IrV1S32ruldeWs6gofKBTS6f3cmmA4CUllFYlpmRIgGN BpaD9T4wgjEkTFgVLrnx/rmALKfD3ftuoE9O38cf9p57pYDfZI4Ggr527wtde0 fXoTcaTkDsjKyrRLABgOeRvbXHV xc5xEVMmgiS5KK9fcYqdgNJ0oHJvEK1i9bUJ7cqoVIYC7aFAe9WuzR9H5xYEBqUnKKIzk1KSnZ7kiyO yyLNtsdlmWiGSdKyMhSIn8qCYKlNpVD8/5UB5SUZQacv20rTYA4Bh98QWDhR8jIHA0oU shIj4qr6vinXBXfmDeaQBept3rwcAAIVLBwDF66n90dpnxZBn7w e6M8JDXaPvCOpR9cQlzgNGPI37PI3WFJ5LmLLAPrrG/bUs3fFFEtgdB6WMfbHAwCZHVQSA0xdhuSsGDv0q7XbN9UjgCNn4IQpM6/ 1cR Yha1gMBRBKJuoC/QR8DM hXE9W10MuuXEIuEdTG2QoD2kVHGIwpb/uRb/j75liOthoCAwCFE9NFHAokMbtqvIK4vI95uv/EgwggCAgICcUCIMIh9Cdxi7COqicBBopuLsYUrIyAgIBAbkkQQaR/db 1YAyJK oaOgrg DZbKLiKGKyPoFxAQECCEpKRmhINBe5KYzt8HEA6FUtOcqgcjiOvTMKhkE9VTJLV/URBbhwgICAjEgE2W84uKW1qbQsGAWBKRyEDEUDDQ0tJYMnAIjYQFcX0XFipjCxEKxLohmxhgEhAQEIgBWXY4s/JlR0p99R5/Q70wigkLQkhKavqA8uMynDnhkF8Q13dhoZK9pB7Aof8D7RgN7TANtLoy4kRJAQEBARWEgDMzJyungBARwE5oIFKqRAzjJ4jru7BQGUtC0hwaHeI4SQEBAYGOoERCSiTUuZxAgkEQdxSDaNvjEWOXPCnmDBox81dAQEBAQECgD4BQSYwjCggICAgICPRdaFEZ9iwDEZIREBAQEBAQSBwQQghBIqEkSUAISKgtZSIULIuxDSdGhGoEBAQEBAQEEgScWxLlosiGEEEgwoEREBAQYBCJhJVIWPTuEhyEEJssy7LDSBHE9VFEU6lf0KhEUECygTmaRAiJta M4F5AQEAAAELBQGtLQ131Xq/Xg9S6K5dAgoBIUlp6Rr/SgfmF/dWhBUFcH0U0leYl4E7DJh2cjC0gICAgoEKJhNvdrVV7dpYPG52ZlUMkm/nuRPW4O1Q/AqjH LKn SIg 9rVfiO3bRfhfgEa2ZgCRsfSIgsAgEQtEc37wfhu6kKMa5oKLJCTMmuERipbDQAENPRkizXztypk1Astt4ChJoJlxIAg1yr6RbN1ENnrSJW21uY92zenpmdlZuWGAt6OiIPOuEOugj3lDnpEH2itbGZGLJc7YxDMtkQ9N/6Z6h6JcBA8AprOh5VHMNsnPpXW5fR67lGTYcS MgICAgKxEImEa6p2Vwwfk5GZAwCWE2F0E2JYRP7tDwR0eUIAOWHUUgGJaUFUAcqaHmK /g3DY7E2yKZY/RAtW4vallpaDCkxCjQ8IDTsFxpf0JoRomZfzKi UTe1Sro9JIY8EM4/4PY8M9XWskHCNRRyihOSmZ1bMXxM5Y7N4352eifEmR6GZgURLI5KZ9ypips3WbgD3f/pCn1MIlsQ52lYmpqvTRcYBMK2F9GbNCpYxZAIRsObmZs8Wp79uDwSsyWZzAz/Ra9 fCpj7gzErlIyIJvNIhGkAFQCFNsjCggIHOtAxPZ2T1p6Zuwxd8LGXVALFJgWSP kbrJO O6o r7nxA159Te1yOsWzjQAeh/Z6LojJ8y6SVF5WWsa4yMf9zCvUL4tCCFWG2bae7M3z3pGZliBs WoWTIAMO0fmhmh4Q3w8RHjY1p6ZrvHTYgUTRznGKg5mdYYTVU57nSHLYo7sIYe PoS1NnpFn1sVZDxPnrMIJihFzZj7Vll0QGJwDzk1FBCc0Y64hFYj5BTSsslLo/AUBldU9WJYRxmSdXQjMqIKTICAgICHJACgDbZQjNVhLAmhvlGgAIQvj8N2mAJ01FlMgcAgpwXQgBMN8Y0CsC/6QmbhohRpVo9G2sGXQJnERCjt lAtEjxBgs51dWqWO8wb9KdHa4TrycR8zuynXgCLBfs7TxxqjBh7mTiJgBapMLSilojdsQdAD/cQ/SwhUEf/7RoUj2hL3ZSp gJiZZWRU4fBC6wFqUd47Safozu/xgjSwjAecWWQgnwT4IOIknWCTREm0Ajs1FRRIx55qSAgIDAsQhCiPpKRd1kEXN43zRcRH/ZG2P5 mWjI6zZKs38GabLvMKF3EG3/eaokamTdo0wZVnQ 91S5MYouHAUoxcAp65FzGJWeWfC GSMYIHeBtpVzoPhEgno1tEwdCZxpryuDmGI0wvQ1TaoQEYzjjtAdnyFzSQWfdhl pD72PswlNe/xyUR WeOPZbRckl9lDvikU/S24dzcrhngxh0xdrfTj06ki3JqISIyggICAjEBgFCKVVtkvZGp8DYNNDNaJRpBCMeT5hFpMBPPFFf14SNNOgF66bR7MkyIkyQHwCsljXauelgZIJFzF42l09sCSPIwF22DmKo/xg7o09YYUbdCOqTaMwy9FkrjAlj v5aGIsAVbMyXBGDOO2aavf4IlW7qdtVwpTSBe70AaSDpg sDMagq0cMxkiI3nClZyQaNzKfOuEReeosMZj4VMYCfwATIYSAdSwKWbfnqEFw57PXXHLezEtufac20rvCvXVvYOvfZ11y3sxLfr26QeluofGB/sr//O2ey2Zect7MS86b9ehr82afN/OS8 5aXd LZQgc41AaV825XHvg2c9dhH/jvMuvfXxr4JDpd3Ag6iuRIqWUIqVIESggAAWkgBSoeolSRIpIKaD CZGiJqGlIUWgCIjavdqdlFL9JkD1MgNqCunZ6NIIWoaU eHupkA1FbvyA5QC1e/0un5YuaXag0iBtrt WLml2q2WiIwiWlU5DXUY9dTbQ5XhVKWI1MyPqq2DWkOjqpNehqageq/6CbW6oV60af7iEqdzp99slt45d5RtbT3nDuiLbpxY9HEM8uRHM0jb679fubnarXTKoEkCk79eYmckUvb KBK1xmLypF3lEdFQU URtPzjU8n8MQIhRgyImMOxFI exdiRun/PuXN5tZlgd5aMmjzzhqtOK0vuokPbFXi/mnvN/K0gjbn/zUdOTO29fA8NlPqPnl26thoguez40SUFQzPbth5plQS6DPR88cB1j/7kOOk3Tz08OVsCAPBvePSmP3jvfr2DZ0858N49d38wbcHCXxYeLX/bRxIESFTXDq09V2IOUaj9frM/qi4JMW5Uu67IvZHMwSbC5W3pLTOf0PiGAADhls3vV7o5FZPLpgwvTeNnXHT6GuTLpQoCkLTSrHRPi5siAEnrn5XuafGELfJG1fU0yhfGjT4gO1hhjBAxw0hmtuZwEBq/EK2FWcBGZTojDo0ZpHqChTvr1BhkRg2BvccoFi3K8URzahOAcDNDHLGlpDgLcksqcp3JEnuDdRgKAYCk9s9OY7ng9USfa8NnjYWnDe XSiDWE8TLMxmzadQyKcXMnqVU 8jxCCyVVh4B1CksGPWk84iOyhDCP9E8jtrXXdhds3710w T0udvqHAkVdz0wuvXIxCbfGgrfNgK6hLCzZWNAAAlF9w/98L dqCR885ABLDZbYdHARoKocNxmAo7GkEAQt 9snLXKbOHJh1ZTWg4DHb7Mbe2kRAStZQ3ClHDC2CZU2oMTDAzE4nlpU84S2BmpAkRYPYoMe8DAIggAsmZcvKJxcZfmi01NylQ1eQOMVnEVt06ERTZK pvitT4rCA1Im58vqjZKnPYwZKpWjtzlIh3KrQs0UwwHI/uDBKwJwn2jDh9TMn4x5hPwgiZeRjX44wL6WuUouiLIALJnT7 5BIbDYW8DY2V6yq3fO4eOnlQblLcXJEavFCME12nFAGk9LLs9OZmT5j3qqwjYXzmahrGIhH09rJ4oyajZnaM16I7nzHaumPEOgsS2X4AEkSCemzm6HNlBt/80mOnZ7m/X3jnX9e4oenHPW20Ij 8a nND6xuhf6zFy6 sFgGUFrWv7bg RUbG2jO8HOvnNa47Om1Xhh04zMLzs03Da /6v1FC15dU lxFE2Yddc959jfvv3ef7oAAOimv146EwAG37nsz2fkMu/3IF9QcOezNz wuhVKZt4y1bX6nbXVPjWrX1SkEog0//Dqguff3dSIOcPPu3KaZfk8hurXvvXi6x9t2NemQGrR2GmX3Hzl5AHJtOnTx25e8H0ABl6z C8Xl4Z/evHe377ngswpv3/q1pMzGE1oy0f337RgBwAA1Lxx6yVvmJfKrnnhiXOLIh3p1nH7xNGNgFHfC26ZUvPu29/Wp5/7l dvrIjagFqgi5BSTzhjyPb3X/zynHnT8yx BPXuWvXc0je/qHSjo/D4s2 8/bIJ eF18 96fp8CyYuRwgY8qjL9w kvWBQvVfvLr0pfc31wchvWzCJTffdMGIDClc 9bdv/ls4vUTdv9n9aY6f/KgGTffe8vkAruafsqssTtWf7C1Kf yxxedH/w/a4kdvkBiFgdA3T/ a9Ezb313IOQcfNYV08IAKYeg7XoHpGeTCDGW26GtveZnSjDWnetzGrMt9BzM2ITVuCEAcWRnpKK7xadKhYNef6TpwPq1LbnHZXr3Nrb5qM2ZM/D40rxUgu0HNq5tyR6a7t3b7A7YSycNL4407N5a3 RRwObI7F8yeIjTIYHpv1DWl6HWzjuzIp3vp3MRIcZFYeuIpqjljh60uZql aFnxEXZXM6h0Ekx15hpQny9GEnmP uibkQAYnemJYXamn1oy8g77vSMpA827d4VLBqTFAoD9bVWb611NYcUsKUWFQ4cke 0EyOYgepQka 1egsvQzzbPq/xIWx cc1mALmk4oRRacTXUr21ThcrULMya8dt58g7JxDFo GCX5WkAAAgAElEQVSzmNXpfR4h6jFX02JsKKM5PdY3kYRgA9LXp1JISWlpdgCA5KKCtOieZLjmvfl/ ecuBIB0WrVq0dMxvffqtx9/Vp1kH6r/evmiFaPuzR1Ymu3a3wIAJLO4OF1KKnF2zRWseXfJm/mDSrNhb0v918sXrTj iVnFrvfm/fXtPQgAqbRqpUUHpfGTx 57Yp0fSM6QUXneHTs2rlo8p0ZZ8uDU/FNv vXaux/7du8rT3940jWtC99zAWSefvfsEzP4ehKbs3RgTuXe5jAApBYUZzuI4jtQ3xw1iyGWbgc6ap8OdDPyXLHkNXA4nalJx1w3vpchZZ44e bm377 7raJN4xgDT5t eLJR5buO n2 XePTdn/0ZKF8/4oL3rispPnLrwx3gATbf/hud8v2H3ybb /fnRuqPKTFx9/ZEHWU3OnZwJApGrVJ5Me/NNrD6W41jwx56mlY0c/cGqamv75SQ/Me/NPWdTfsvbJudEllscLusUrLqftswV/ebVu0py/PzRS2vnOwue 99umHpLG6wUQ6ELnvlvooHeqd9 tVtDQBbjt7nTro6jWDRV/MODVzQtRpx8EDrQUjzt9cGERqfvwmw2VeYWjk0NqelPhCWcOLS5OkYP1X75c4ykq/9k5/TJ8dd//vz070keNKpaovlIWKVLF8plE6RVD1WgLBwdl2roCfoCpt5fidsSdWXhc pD39ohBXCAU1HxQdJamKDsblSnlUOWq/LbK26/sxOnFeQ7fvs82b9 WdtLoFKpotUKFKgHP3m iZdKHTBqwbW3z4NkTh2YSAFAO7Pn802pvUdmJ04rzknSxUakKZbUztY6ZhABsXOkQ8wixBpjYNiQABIm2kwGiFGMLmlgroPoSdv/jjmuuu/SKh1Y2gb1s p3Xjo6eVRDa /57uxBAHn3b06uOzF yakx8wqa/ofXnrjnWeuLgcAqPtuT/rZD8y7bSQAgDT61gVPL1jyxK8nZHbNVve/bOEzf1v05J2jJACo 26HO7j3/97bgwC2ETcvfu3Ff7z0uwlprIb7/vvKOj9AwUV/W/jkvPlPP3FFf4Dg n t3BcGKWfyLbdMSAVl2z9 8 A7 wGyT//19WMzrHoQ5yl3/ul3k9IAAPpfMG/RgiVPP3bvz2L1fmPo1lH7dKSbAefE 194 fWXX3zm6nIRkjkoEPuAs66aFPp4 acutoOhNH7zzg 2qXfccNaI4uJBp1xx92VlNR u3N3R5Fnasu6NLx0Xzrlm oiSgsJB4y6eL8bf/d2Ka z7Imz75oZKZMHMUTzz1B3rNuvxYlTJ1w1WUn5Nolm z9bkV3SoxXXLjxm3c3JM24Y/a0isLC8knX3Xpqdi800yEDIcjOkTy0PxQpRYVS8weZH0oVygIV/QcA61esWfXupm8/2vztR5u//bSqLUwpBQB76eTyAUXQss9DszPA1SYXJBEKALbiyRXl/UhrpWvX//Y0krxx5w7pl6L4FGfZcWntu1scWTagmtWgWigGEUAvlEM8VVXdqDn38zD8sIuxDyNxOn1KN lTVUVERfsBW6rDpvi9kgMaDjTZisadNaQ4OeJuwYyKoiSXK5KbLBlOIWLoQBwZGo6gomC4aXvtns37d22oabIVjjt7SHFKuK2ZplcUJrkaInndIFE5rCRaqYwPdpWS2nOjjJdFD4fHdQgR9rhVmyoVVYwenh3dZ0RvzZ4mAICB007Kk0HKOX76CPvX30bNoMo79cwxmTZ78uBBGbDHA0FPgEIPJywUjj p2A5SSn5ROmxxQ9Djb6/Z0wwAMPD0UwrsIGWPmTpC/nqdFjKh7Xu3NQAAuP7926v bWbTsK3Gj V2KWfCbbeP3/TYN74IQNb0e64eHeXIHKxu8dunQ91KtC85k88/Jc8GALLcxz3jBIDkHDvrotLb33x7y6nXGomRxt0uKJk5MEUbJ84ZNjKzfed Hx0aN5 w66eaYP1Pd13OjDVCscujgAwgZw3I1qI4UnKmI1wfUF8CtvyKAkePSoxXXKBxd4NUcukAzatOKh07QP5f11vjMINA9Lb3iQZEsMyVkRwZWbR XQNIdmc6tNe4fUGkQEgkqDiSZEQgSdmZpL3G7Q1Egm0hcJYXOnyuXR6fAtSRZA 4fakD7aDP5lQQqR5kUI1M4oIZX obxAEAAAXU415UQQREQsKtQeqr/XJJLXNDsoekFBF9WZKi OPLaCVQpAr1twapr 7LJXW8GKYldPvEtBy642IYPK2ithhnMPX1ldiDb17 55Mb/vPY3Ne2V3 8 PHjhs6fkR8vBB5nJpSGlEx1eESSrRO2uw1HqjowSWzW8myyetKZJMs2AOvoT9bJZ03sZ1LkKO5nBwAA2u5q1LrD7fV1fjwh41Do1nH7xNMNACAtJ0WMLPUebMUzZp 2Yv6yj866ikvv5iOJiNKQOcvmTc/myQnXgnWSnTEgTyRZijUptOfFBbcCgE020ogsJ/CzEmvuYULCkZ2REm5p0AaYAu2NSkgbslBCYZM2SiSJqMF7JRjS0yUJAoGgGfVDarM7EpiV GCn/R5ZTXoGDLeHqJSankz8CCRv1PmzSvgVuJGm/ax4HJlq62zeWGL7d9X0tvq9iZgMWhLVfWXU2MxRN 0XQLJnjrjg5ks/u e1/cqWN1fuOvW6Ydx1klY6OBe2N8G T9Y3T5me7d6wZmv0orbYIDZZAqA05A9HT7/rBkhKSXkObG Gmu8rfVNPSAvVbtodNGuQXjYsD3Y2AnWecvEN4zIkAIi4d6/bKpUkE4BQ1arHX95NIalfXriucevziz4e94czinqNSZLSUft0opueR598jyQsSNqIK35Vccsbb20oQ7VDIudVFMD36/cFpo5JAYBI8/atbelDS1Ml8Egkdn/UXjCsGL76Yqtn6qQuDotyiF9ie0z5eMXJ eV55KftjZHxaTIAhJt214XA2X19DhNI9JreRIO2DhaVQCjgNYlHcw0SInP o5lOKSLY0x1Q3dgaLlHTQ62 sN3pTDKrzQbx2c JCXaAKbE1NYgDk5OIz7U/IBVU5Mq0zumAnXUNTcmRah/XxQ0YXIDd6YDdsWSC6siglnFcscRGzN1 tQYzHnMCAIQQGr1F3lFihOSSMy8ZbQeApjVvfe 2vNcdZWf8soIAhDcuvvWKq6 9 m9fe7uarz1vcA4AwLZFt9025875q6t7 mQ4Bp55/iAA8H42//65f55/z9z3XNzVc646MRnA/fEjd9w d/7DD9533RXX3/Xoyj1BhHDVu0thsh/ed3/vVP14 0Q3jL8gUfHujFR7Tj9ulIN4FDBVvh1Ctn2H94b0tQfZhteadcOC6y5qllH2yrrd 77vWFb 4rmXH 4GSwpRbmyQ0bt1Y1ud2eADu9RsqZMGtq6neL//7yFztqXA37d/7w31f 0fUnOG6JcRCvOFve Jmj3Ktf qQ6iBiq eTV1bXxskgAEG2RdIL/AIRbPG2tfp8n4PMEfJ5gKMKeVMxJ8unEnpeTSeu7o1GAj7G1z79gaSBw/MlcIhhb89OqtE/GGn/R5xZbpEXMTtbfcE/W5va61rz/d7GxTncdP7JXn9NCc/1960bs0BjzcY8gd9TS21O5sDCssFsefFkbE57CTUsN8bDEaUCMQVO LV7xKVHUD1ANXYjBy9kfFRASnnlIunZW5 vy347Vuf1I0dwV20l/xy7v2eJ59fsakxQPqfd8fU uefWxcEe3KnMzvsZedfd/6WJat2uNvq9reFXIEejzbaSy6Ye59nwQvvbqnf9GPSlEtmF7798rd /aotf9p9jyb989W3Pl5fuXVDNchZpcMnnzJjWGpk77uLX64ESDnptutPys2hd1392a0v7Njyj2feH/fwuYW9tINLx 0TVzcJjs5nKTGQMuTSWSM/WLxVe Kk7MlzHmpbsnT5/Xd5wF4w5uy5D19c7gCA1DGXXzTy0WV3Xv cdTG2lD7u1vkPZi97acnct70ASTkVJ0ybld7lrku8EuMtd4xXnJQz5Z77Djz57JwrX3E480fP MWYjSsPpmEOLZidYBIZ2Pzpui/Nr3LOED9G4qYze1r2w6OJz9j5eaKvdt3hYGyZE5aOjEadlKYz37amNbIMFbg5sscyQV6SKw6eNvPgMAIFJySmbJwPE////sfXl8VNXZ/3Pu3Jkkk8lkX0gCYQkgu6IC5QfKImoVW1ywVhR3cXtRrLV xNrWQlu0KosLbkVbF2ytaIG rxu4larsS5QtCRCy7zOZfe55fn/c7dw7M9kIZALn wlk5tznnvOc8725z3Oe85x7hxalBuv2 yTRUTB iLOqpnSbJwQgJCSlFvXPLnT4ypv0s2PI Ktpv4HJxz7/7j8SiP0GjRkeVQxc8TyJiLEZ21CM6jPzEADI4xMXSBCWs7koUEkKhakUlMJFVzhnzbpk1PkXB3zuU6T6qQP11TdKGdkOCwBQ186X7v3dpmZIu2zZc/cM7 UnkcUH PhwcIDf5/lhz9bBQ0d2LNrLEO39x2UZtyfS1gOVdeGUopH2ln01LfKz8pIzBg0Ta/fUea1OthwAhOSU3KLUlCQBaNhb31Jb6Q0hEFvKgNEO9/c1TX5kP5/q3nUBZYe n3jhbFdzbZ8kjgaDvlZPc3WbV01vIrakzAFpaalWAQBDQU9Da121T7IauIgqE0aSmJfVLz/JSkBqrC0/EkCzWE1VXLsyMpVBf1vQ33bs8N5PPvmoMFRkT0i0JyQk2RKTEhISrFabKIoWi0WwWASLSAERCQAhVNKf HN6LDPFhFS14fFFn4hDi/Pswbof9lf5AWxjrrlyCLfTMvj4cHDIIH1hch/2Htt LNoBV/kO/ZUG6Gkq3QkAAJKhHAAkj7vqe/OcFYPuIzvckZ/jGuwz8npTj84hJnEKMOirP yrN5UauYguA irqS rYc KKhbHiHBC1Je2RnuBAYqgPOMZifLm83jP6 oJCM7iccP u XAnhoEsGUMnDRtzk0/Y/fjnOHg48PBAQBA5Afoc/QRMFm/nLi jSjhlCglepFoKEX5d5/wZ08Eluypd/156l29rUbcgo8PBweA8tjc0/xueDrBkPbLievLiJX2q5cKuggS1pXhxHNwcHCwIITfF/sSDJuxe1UTjhNER1kuypMBVCmRmPffC4iUnu5hGQ4ODo4OIQgEkfbR562daUBEQX2gIyeuT4OlMhYI6u8CI3j6vRmbg4ODoydACEmyp4QCAWsCT3jvAwgFg/Zkp zBcOL6NDQqTeWRq06at3qaPiKPg4OD48RgEcXsvPzmlsZgwH8GbIbow0DEYMDf3NxQMHAoDYc4cX0XJirZQ 0/NE/UmVZ3MJ08LTk4ODj6CkTR5kzLFm1JNRVlvvoabhTjFoSQJLtjwOCzUpwZoaCPE9d3YaKyfWE2Xca8wMRZ5 Dg4JBBCDhTM9Iycgjpk69XPHOASKkU1owfJ67vwkRlOyCCTq55B9MZsBObg4ODo7OQwkEpHOxYjiPOwIk7vSFnybC5MlQ7ogudwEufOTg4ODg4ODhOAeTXSTLBN/Zd7jwyw8HBwcHBwRGXMCXDyK4MBaCyb6OUck Gg4ODg4ODIz6gPfRQQNVFYbwZATTvhif8cnBwcHBwcMQfoj7wEFWIJtlTpBQHBwdHX0A4HJLCIb61M85BCLGIoijatBJOXB9FJJUyzM/LY6C7MojIU305ODg4WAQD/pbm uqKIx6PG2k791KO3gQRhGRHSr/Cgdm5/eX5OCeujyKSyk6dRYgov26JEAJAgHIHloODgwMAQAqH2lwtx8oODR4 JjUtgwgW/daKcgwb5Y gvLCXnQ8iILMnVH1hs3FHBTH8AtSq0QX0R5gaZQEAkMgton4 aN91XYh2TFGBBRqk9B6hVsp2Q94SgiY1jPWbFdL6haZTQFMTwZTgQNAwKupBfXSY9wgiAFKptaWp7MBeuyMtNS0z6Pe0Rxx0xB0aOthd7qBb9IEyynplxHS4IwZBH0tUazNeU10jEU6AR0B9qcfMI jjE5tKdju9oMpRQilR3FMLCBYQLECYqAx3Yzg4ODhUhMOhymOlxSPGpqRmAID5jTCKCdEsovHuDwRUeUIADcKolIJy12Vu55Q1PUS//WuGx2RtkC0x yFKtSa1Tb00GVKiNah5QKjZL9S oLkiRGVGrK/oaH2Tu6TaQ6LJAzH4B xaEKO2Ug0Sw0ChQXFCUtMzi0eMLT 4d/yPLuqAON3DUAwrgslR6Yg7WXH9JBN3oPo/naGPKWQbMngapqE29qYTDAJhx4uoQxoRrGJIBG3g9cp1Hk3XfkweiT6STGWa/6J2PzaVxicDtZMro74ZGxEpACUAQCOHioODg NMAyK2tbmTHanR8y0IG3dBJVCgWyD1E8oTYON0VL7fG8Q1efk3NcmrFk43AOocWZu6o0GYdZMi6jL3NMpHY9xDP2IK3RNCzDZMt/f6bJ71jPSwgsGWo2LJAEC3f6hXhJo3YIyPaB THaltbhchQiRxBsdArkm3xqirauBOddgiuANz6MHYX4IqO12ij 0KMt5HtxkEPfTCVqxcqyzaIRGYi5xqSijOSHs8AusRGpRSaonJIzBUslpS3fcSAAQLEAEIIUAIgEXgb8bm4ODgiAGkAKAkWyimihDWxDDfCFCQd4waVxkQ9H2kJpMKQNDghRAA3Y3RjQIY7/SELUPEiFbNno25gk7BYO8QI3eQIJqkjAYLDarLXTGfoZ kOjuGSbxaRPTvyE7iCbBcsKcbiZOFCXMmEzcBUCIVplFUBrE97gCMyz1EDVto9BmvFkWqO/RFL oQ3SHRNKpo0AfBEFiL0I5xWnU/RvV/tJUlBDB4xaZGCRivhHZBCQjKiwsEovwZcnBwcHBoIITIt1RtBZ7oy/u64SLqzV69vevrQ pEWLFVivnTTJd xBByB9X266tGuk7KMcK0ZUJ3jF77QMMahSEcxegFYFDXJGYyq0ZnQvukrWCBOgbKUYMHYygkoFpHzVDrxOnyqjqEIU5tQFVbowIZzQzcAbLrK2wl0ejDTtOHho89D0159XtMEtF4zbHvMjIdki/l9ng0FqnjY3ByDNcG0ejqKOlXArQQoAQsoO5g0qNwfN8aBwcHhwoChFIq2yTljk6BsWmgmtEI0whaPJ5oE3cEMCaeyLdrwkYa1Ib1jJAoBocJ8oNaZ8RxQzc6haizbEM90SW0IIPhsHkRQ/7HGBk1YYVZdSOoJtHobahZK0xYgJn7K2EseSqu78NliFOn6aj7o5pPA8hM4gnTSie4UxeQTpg MDMYha5uMRilIDIltnskaicynzrgEY3UmWIwsamMCsI80VcG84i80ylLJnDoxZvnzp4z9 73q8I9K3ySVPKX/Hne3Nlz5v7Pxnqpw6MnoDD6yv/15IPXzZk7e87c2fOWvbVk/uw5c2ffv7EmSqscHJ2A1LBh0c VS5H93En4di/5 S1Pl/hPmn4nBiLnFVKklFKkFCkCBQSggBSQApUPUYpIESkFVD8hUlQklDKkCBQBUTlXOZNSqp4EKB9mQHUhtRpVGkGpkDI/hrMpUEXFzvwApUDVMz11O9bvq3AjUqBtdTvW76twyS0io4jSVYOGWiKm2k91PGQZg6oUker1UXl0UBlolHVS21AUlM VP6HSN1Sb1s1fTOJU7tST9dY75o6yo63W3A59kYMTjT4Dg0byIxmkbTXb1tcEkdMqiTwNSvttgRiZQ9P4JEZbCYOmlneUTU1JR5BKX 2FTqYKJDEWGXPpsrE67 56KFayr0AquzYPTUObffeGFRYic92M7A89/FNy8tAWHsI2ufONfec/X2EqSaT198eUsFQGLR2WMKcoaltpb0tkocMYDurx69ddkPtvN 8dzjU9MFAADfrmV3/tbzwNvtXIpS7YcPPvDxjOUrfprbZ/ 24wgESMRNE80zV6IvUcjzfn0 Km8J0U6Up65ouEHpi03EULdptsx8Qu0bAgCEmvd VO4yqJhYNG1EYbIx46LDu6KxXSohAEkuTHO4m10UAUhy/zSHu9kdMslrXVfLqLExw oDsosV2goRs4ykV6svB6H2C9HcmAlsVKYj4tS8EX3HlYk7c2oMMquGwJ6jNYsm5YxEG9QmAKEmhjhiSUpy5mQWFGc6EwX2BPMyFAIAsfdPT2a5MOqJ3rpdXzTkXjiin51AtCvIKM9UzJZRo7TGo0JMOzwCS6WZRwAgVG7PdKUb0eGD7hRHS4WIiPImJu1wH11mCrkqd258/nFS MrtxbaE4jtfffs2BGIR4 WGHhcqhZrKGwAACq58ZPFV/a1Aw7MvRgSwWC2nRgEaDKLNdooa6/sgAMFtf1t/eML8YQm9qwkNhcBqFToWPL1ACInYyhuBKG/fJWYDrt3ndQ/FeNMnBkugV6QIESBgvDFrX8KIQDKmnX9uvvZ3ZbFnJviPNbqCTBXRVTcngiJ7RP5NkWqfJaRaxM1YLyq2Sl92MFUq905fJTI6FUqVqBdojkdXzJHWl24Tp64paf8Yh5AwQnod2vEY60LqHqUI sKIQDJnTjy/wEKDQU99Q/nW8n1fuoZNHZSZELNWpBovFGPE0ilFAMFRlO5oanKHjF6VeSXMWLlchtFIBHW8TN6ozqheHeO1qM5nl19RHfmaAkGwENXb1IUoCgQAqMj6MUwVPRjYOMkYsuCNpy5Kc21fsfBPm1zQ H1ZKy3ODh1 ecGjG1ug//wVq67KFwGk5p1vLX9l3e56mjHi8htmNLz2/BYPDLrjheWXZ t21Xfso5XL39xU7rblTZp3/4OXWd 796G/1wEA0D1/unYOAAxZ NofLs5kbuiBA6vueOwjFxRe/T8zK99755tqyDv/hgfvusD1r2dWb9jTQHLGX/PQg1eOdAgQMKsUbtrx5vJXPtjTgBkjZt8wI2jsVvtHTcBgzZZ3X3/7011HWyWw542bMXfBDVMHmKJTtPnTR 5cfhAAACrfuXvuO/qhoptffebyvPChFxc8urEFCubcNb1u4/tbKrzyOPyk2E46GMCYCgTUOq 8a1rlB 99V O4/I v3FFsfiQ1R3QI9nMuHnrgo9e/vmzJzCyTH0E9hze89PLar8pdaMs9 8d33HvdpOzQ1qX3v3JUgjX3zVkDkDJt2av3jmJ9oGDNV2/MZHe2sC4CiaNHfBnVeOTBFCVe8 8IsvJt82qfRfG/dU xIHzVrw0F1Tc6xy YR54w5u/LikMfu6p1deEfg/c4vtuuVRmwOgru//sfKFd7fVBp1DLr1 Rggg6SSMXc AdC DEKO5Hcrea2OmBGPdDVEULdtCrUGPTZiNGwIQW3qKHV3NXlkqFPD4wo21O7c0Z56V6jnS0OqlFmfGwLMLs wE22p3b2lOH bwHGly a2FU0bkh tLS2oa3RJYbKn9C4YMddoE0P0Xyvoy1Dx5Z3akG fphogQ46KwfURd1HRGd6fTxgWmrp8fEXIzOhQqKfoeM0XI2C9GkvnPvKkbEYBYnckJwdYmL1pSss66KCXh4z2lhwN5YxOCIaDeloqSqrqmoAQWe17uwJHZTivRghkoLxV5Wyr2GWWIe/ XlV6Eva9v2gsgFhSfMzqZeJsrSqpVsRy5Kr13hsc5Gp0TiOBR81n07vQ8jxDFB1EINWbJaJ9F7bvcJiUgIVLoY6kTQkJyshUAIDEvJzly6hiq/HDpH/9 GAHAQY9tWPl8VHe94r2nX5Sz6oM136xZuW70Q5kDC9PrjjcDAEnNz3cICQXOGLfu4/9c9Yb8qWbrXx4rfy/YIAcO63asffLvZ7986xCz8Q5VfbjkTVIQDY6bH1JpXaP2qC1LD5qYef2eoDkjF0dJbn4MHdG1YtqpRWPzY9mw1/EIuzcGBG ZGmEADYc/LTbUTy1tY0ReQ1VH6wem32oMJ0ONJc882alevOfmZefm17A9iOAlqd61a/BTan055wxk3sTwhC6rnz5 z95dsf7J98 0jW4NPmr5594uWj59279IFxScc/Xb1iye/Elc9cd/7iFXfEWmCibTte s3y0vPv c1tYzKD5Ztff/qJ5WnPLZ6ZCgDhYxs2T3ns92/9Oqlu0zOLnnt53JhHL0iWy78879Ela3 fRn3NW55dHNni4FghtljNZbR sfyPb1ZPWfTnX48SDr2/4qXtPsv0kzJ4PQACnZjcdwntzE7V6bvZCmq6gOFxd6r1kWTrhpIv4Peo5oXI6Qf 2ub88RcNyc0j1Z98u6s8K3dMYlAub8w955Jh flJYqDm679WuvMG/ iyfine6u3/W3bQMXp0vkDVnbJIkUqmzyRCryiqRlo4OCHT1hkYF5h6elNue9zpjcekzxhQQKIR5w8GFB8UnYVJ0qEGadpgOFZX/t0xT7 ic2fmZ9m8R7/Ye2B/8nljkqik9AolKvndR76NlHEMnTJg/5amIfMnD0slACDVln35eYUnr jcGflZCarYaLtEWe10raMWIQAbVzrJPELMBSZB9lbkHwBKCREEQSCCYlj66KISAEDpX 67 dZrr//1 kawFs1ceMuYyDSC4JGPPjyMAOKYe55/8/XXXn94kiNqVWkzf/vGO/cNNgAIDqbWWOHz 65J5RAADCmLuXP7989TP/Myk1hinOmb3srbVv3DeMAECwwXrpr99 7 WHxokA0LD7h8YIzzB45P8 LEMAy8gFq956/S9v/GpScqePmqs6 u /bfUB5Fz95Ipnlyx9/pnr wMEdv5j/VHjSipxTlj4 19NSQYA6H/lkpXLVz//1EM/ijYf7n/diheeXPnswtECAFRvO gKtDuAnVLAOfmRV//69l9ff GmwTwk0wUQ64BLb5wS/GzN53XsRSQ1fPv Dsv0 26/dGR /qAJ1z9wXVHlJ tL20uepc1b3/nadtWim2eOLMjJHTTxmjuvyd7/792t8v0sber8q5GaGzUAACAASURBVEelisSWP/nyc8SyrceVOKB90o3XnZNpFSyiZ9u6rrQYq7lQw7cf7EqYdd/8GcW5uYOn3Hr3Bek9MEwnDYQgmyN5cn8oUooSpfoPMj USpQFSuoPANas27Thgz3ffbr3u0/3fvf5sdYQpRQArIVTBw/Ig ajbpqeAnWtYk4CoQBgyZ9aPLgfaSmvO/yfsgaSNf7yof2SJK/kLDorua202ZZmAapYXqqEYhAB1EYNiKWqrBvVcz9PwQ 7GfsUEqfSJ3WRPllVRJSUH7DYbRbJ5xFsUF/baMkbf nQ/MSwqxlTivMS6urCmYmC5hQiBmtjyNBQGCUJQ40Hqsr2Hj 8q7LRkjv x0Pzk0KtTdRRnJtQVx/O6gKJ0ikl0Uxl9L9LM0SgzEMd 6RDE3K7ZJMp5BWPGZEeOUlET2VZIwDAwBnnZYkgZJw9c6T1m 8iUqayLrhkbKrFmjhkUAqUuSHg9lPobIZCzpQLhiZbsHCAEw62QvrkGWc5RTJgUDrsrge/O2AeV/RUljUBAAy8aEKOFYT0sdNHit9sDXfmqAm07cj egCAun/ 8sZ/6uX1 yt9ONjajZXC3Inn5VtBSMrOc8A FwTcvrb2BrBdBQqULxlTr5iQZQEAUew7a5fxAcE5bt7VhfeufW/fBbdoheGG0joomDMwSR5NMWP4qNS2Q8e9dFjMekJ1P1QGan64/ fMyiLk17klEAHEtAHpShRHSEy1hWr88iVryS7OsXWrxVjN RtK64WCawcoPnRC4bgB4n86PxqnGAQiH3sfb0AEU66MYEtJozVb60GwOh3QVunyBpACIeGAZEsQEYEkpKeStkqXxx8OtAbBOTjX5q077PZKQG0JVr/Lax9oBTWbU0KkapBBNjLxC2Z9qW8QBwAAFFCNe1EJERAJCbUEqLfq69VVzAmJbpKUR9RtSZLkiy2jtECRStTXEqDe6q9XVxvFMDmux6djO0EoEApgkRN8lefKyE4M0Z5MGM9XqwlDFqz5w/n1/3pq8VsHKj5b9fRZw5bOyo4V846R qQgKVVe/RBEc4Z2x0hwJAgAVJDTZxOdSYI8rh1VZBHlN50JomgBMDsr7R81Ie38Syf30xcVbPn9rF3pgQ6bXXaAiDyMUWKO0bvUngLJGUl8Zam7sOTPmn/huqWvfXrpjYbyLv6VIqIwdNFrS2amG6kIVYE5yU5bkCeCKERLCu1 c4ESALCIWhkRxTi MiJzD MUtvSUpFBzvbLA5G9rkILKkoUUDOm0USLID0QlIAWCarkggN8f0KN SC1WWxyzEhts2m/vatI9YKgtSAW7I5H4EEjW6CvmFRhTHsONx1nxGDIV5mzeaGLHD1f2tPo9iUgG5ZJYzMbL/p4TgWBNHXnlgmu/ePCt49K tesPX3DrcMNxklw4JBMONMLRzTubps1Md 3aVBK5iy06iEUUACgN kKR XbdB0kuGJwBB5qgcnu5d/o5ycGqPaWBTh41QXAUDc CQw1AnROuuX18igAAYVfp1hKhoKd2pZOk9gawcwr0zTtLnIAkj7z Z8V3vfPuriIEAQBAzCrOge07j/qnj00CgHDTgZJWx7BCuwBugUSfj1pzhufDf78qcU fEmuVtD3EbrEtqnys5sTswVnkhwMN4YnJIgCEGkurg Dsuj6nCBG7IuIPyj5YlPxBv0cnHvU9SIjM x/1ckoRweqwQUVDS6hALg 2eENWpzMh qbW N/gyi4wxbemGnGgcxL21h33CznFmSKtdtrgUHV9Y2K4wmuYxPo1LsDqtEFpNJmAvDKoVBxTLL4RxWRQIMi8D0EAFJAoSWN90vWOArHgkrljrADQuOnd7S7TjdxWdPFPiwlAaPequ6 /6ZabnvzG09l6rVlDMgAA9q 8555FC5durOihS8E28JIrBgGA54uljyz w9IHF39Y1 mjEVVdduO5iQCuz564797FSx9/7OFbr7/t/mXryyKWtbqvbbsDeAoUOONhyZ1 wyzrjg/3BeRr25I14arx4U3Pvfbx/qqaI1vfXrH2aMGsK4YkgsWemyXW7y451uhyuf1seo2QMWnedPu2VX/ 61cHK vqjx/a8e //aXzF3TMFmMgVnOWrIlzRrs2vrG5IoAYrNz85saqWFXEAYiySTrOfwBCze7WFp/X7fe6/V53IBhm31RskDSWE2tWRiqt3vZNS8Af8tXXHT3iTxwyMFMIBSXj6ZFVxeMPm/bb68p0iriwy9PmDvhcnpaqurLtR ol51kz yV4fDQjO9PauHVTrdsTCPoC3sbmqkNNfonlglizYshYbFYSrD/uCQTCUhhiivV69ztFZSchyq/qZLdk983QnJAx4ZoZqXs/ag189 7m6nEjDQetBT9d/Ij72VfW7Wnwk/6z75te88pLWwNgTewwccNadMWtV xbveGgq7X6eGuwzt9Ty4vWgisXP xe/uoH 2r2fJ8wbe783Pfp2vc0dNsGTPeHhZwt/ffPezneUluypATCscMXXCrOH2nvNT2x/AdhTADqvm6ByShl47b9THq0qUC1BIn7ro162rX17zyP1usOaM/fHix68ZbAMA 9ifXz1q2WsLb3vJvBlbcIy/e lj6a 9sXrxex6AhIzic2bMc3T6jz1Wi7E2O8ZqTsiY9uDDtcuOiGv9mc2WNm/WTs7vUnMjAnF8yTYOIZ2PT51q/1r2L2xBED1D9/xm4qX9lysDn7ny00lh/duz8Egi110LDJM9Klhhr2TseOQJyPhiFZpjcV6SSw8bNvvwAAIEJiUmrBwIn/b2hRarBuv08SHQXjhzirakq3eUIAQkJSalH/7EKHr7xJPzuGjL a9huYfOzz7/4jgdhv0JjhUcXAFc TiBhrIARAIFokBgCI/IJtAcijE2 jSBEAKZWQhmk4jDREQ4Nmp82adcmo8y8O NynUP2TBOqrb5Qysh0WAKCunS/d 7tNzZB22bLn7hney48e6yPgA8hxxsHv8/ywZ vgoSM7Fu1liPb 47KMmxFp64HKunBK0Uh7y76aFvlZeckZg4aJtXvqvFYnWw4AQnJKblFqSpIANOytb6mt9IYQiC1lwGiH /uaJj yn09177qAskPfT7xwtqu5tk8SR4NBX6unubrNq6Y3EVtS5oC0tFSrAIChoKehta7aJ1kNXESVCSNJzMvql59kJSA11pYfCaBZrKYqrl0Zmcqgvy3obzt2eO8nn3xUJBUlJSYmJSTYExITbbZE0WYVRavFYhEsgkUQQXkwomE9tFe7cDIgVW14fNEn4tDiPHuw7of9VX4A25hrrhzCzXAnwQeQ48wE6QuT 7D32PZj0Q64ynforzRAT1PpTgAAkAzlACB53FXfm esGHQf2eGO/BzXYJ R15t6dA4xiVOAQV/9YV 9qdTIRXQZQF9NfVkNe1ZUsThG1LAMJcTwLklmM/bp6buYIDiLxw3775YDe2oQwJYxcNK0OTf9jN1uw9EABynIkg8gP0OfoImKxfTlzfRod5LqaXY4uyH4OIIBDTluzTCJbsqXf9eepdva1G3wUfQI4zEZGvPuKIZxjSfjlxfRmx0n7Nu gIBUIICnxazcHBwREDhHCD2Jdg2Izdq5pwnCBih2WML0AVCFgAQFRKtUQZAvH 5AAODg6OUwJBIIi0b27qPOOAiIL6QEdOXJ8GS6URAgBBVH4ABABBfr27kivDZv5yT4aDg4ODEJJkTwkFAtYEnt7eBxAKBu3JTtmD4cT1aWhURj2qeaiq02IhhJgfPYKovyWbg4OD44yFRRSz8/KbWxqDAT f4MUzEDEY8Dc3NxQMHErDIU5c34WJSuMhAkgICkCR9VEQkVIqst9BXp/i1HNwcJzxEEWbMy1btCXVVJT56mu4UYxbEEKS7I4Bg89KcWaEgj5OXN FicrOn6i4Mua9S5x7Dg6OMx6EgDM1Iy0jJzKAzRFXQKRUCmvGjxPXd2GiUkOMzCeKCAAWkd16zb1XDg4ODhZSOCiFgx3LccQZOHGnHwgh usk1RJBEAghgsl9QQQ5H/jUasjBwcHBwcHBEQsUUXs5NgWgbFqv2ZWBvvo6SQ4ODg4ODo7TF4Qq/xPz5iZ9HZH1afgWJg4ODg4ODo44AgqAhICFgMUUcxGAzfnl4ODg4ODg4Ig/mN67xELfwSQ/KE/epI3cq Hg4OAACIdDUjjEt0TEOQghFlEURZtWwonro4ikUjvQzlmGdzBRGv3hehwcHBxnIIIBf0tzfXXFEY/Hjfz2GK8ggpDsSOlXODA7t79s7zhxfRSRVHYSIpqfiUeAv1OUg4PjjIcUDrW5Wo6VHRo8fExqWgYRLPqtFfXHicr3SiL/x0owwW31pkzQcLclhl AWjW6gHYrNskCACCRW0T9fNC 67oQ7ZiiAgs0SOk9Qq2U7QYAAmp6ss3q9ZsV0vqFplNAU1N YQ5TJUHDqKgH9dFBZI8jlVpbmsoO7LU70lLTMoN T3vEQUfcoaGD3eUOukUfKKOsV0ZMhztiEJhXKqq1Ga prpEIJ8AjMLuhzTyCPj6xqez8dnoR5PUnVSueMMPBwcEBAOFwqPJYafGIsSmpGQBgfiOMYkI0i2iaFBJQ5QkBNAhrt1rl evM7Zyypofot3/N8JisDbIlZj9EqdaktqmXJkNKtAY1Dwg184DaFzRXhKjkW orOlrf5C7pbyxW5YEY/APDzhNdbaUabdKtjgPbDCGp6ZnFI8aWH9w7/kcXdUCc7mEohhXB5Kh0xJ2suH6SiTtQDWln6GMK2YYMnoZpqI296QSDQNjxIuqQRgSrGBJBG3i9cp1H07Ufk0eijyRTmea/qN2PTWXXXBnDdWYeJg4ODo4zEYjY1uZOdqRGz7cgbNwFlUCBboHUTyhPgI3TUfl bxDX5OXf1CSvWjjdAKhzZG3qjgZh1k2KqMvc0ygfjXEP/Qg1jgX7yj5lnHR7r8/mWc9IDysYbDkqlgwAdPuHekWoeQPG Ij2MdmR2uZ2yQ9LMxFncAzkmnRrjLqqBu5Uhy2CO7OdRGN/CarsdIk tivIeB/dZhD00AtbsXKtsmiHRGAucqopoTgj7fEIrEdoUEqpJSaPwFAZu8fmDoi67mo/eJ4UBwcHB4BiU5VkC8VUEcKaGOYbAQpAjPNpUBZLmIkqUzkAEDR4IQRAd2N0owDGOz1hyxAxolWzZ2OuoFMwGAL5RcNRBDCqNWJ9D324mDBTxEmqs2OYxKtFRP O7CSeAMsFe7qROFmYebA9GzcBUCIVplFUBrE97gCMyz1EDwso9BmvFkWqO/RFL oQ3SHRNKpo0AfBEFiL0I5xWnU/RvV/tJUlBDB4xaZGCRivhHYhd0kEACQECAGeG8XBwcHBghAi31K1d/ESfXlfN1zaEr16e9fXh9SJsGKrFPOnmS79iCHkDqrt11eNdJ2UY4Rpy4Sen42iYY3CEI5i9AIwqGsSM5lVozOhfdJWsEAdA WowYMxFBJQraNmqHXidHlVHcIQpzagqq1RgYxmBu4A2fUVtpJo9GGn6UPDx56Hprz6PSaJaLzmCHPcdEi lNvj0Vikjo/ByTFcG0Sjq6NkF6JC/mrYjK3rywMzHBwcZzwIEEqpbJOUOzoFxqaBakYjTCNo8XiiTdwRwJh4It uCRtpUBvWM0KiGBwmyA9qnRHHDd3oFKLOsg31RJfQggyGw ZFDPkfY1vUhBVm1Y2gmkSjt6FmrTBhAWbur4SxCFC5Ks0V0YhTjsnhBGOTst1U7SphWukEd oC0gnTB2YGo9DVLQajFEQ /bZ7JGonMp864BGN1JliMLGpNLVv8mA0iJQq0TtCiKrhGeDHBA69uODRjS3Qf/6KVVfliz0o3OOtdwXoK1 /atXbWyraACD5vJ PKHlnmw Kbn71mcvzLD3XDAeHBqlhw0P/s3Hq06uuyhfZz5083bd7ya3Lkx578RejEk qmt0EkW0vMrdF1a1Rb DITudRW8VQggTsmcrtmgnXU P9HohuUbRzItY3iNn8GO7YhsWJiISZTvRYNknordu1qS572qjCZILeul2b67IvHFXoIObKEFh7p8cnQLdyBpuHht4iIBsd0CboTDSGnbUbnQ05tsKMNtt4TOJANauKSWZiEx1yh8A6N8gEFbQWmH5EGxyIRh jf8TakplB9Nbt3Fyfc HIQkcs94ZEeS4cxvjdrp7aIe2EGI6LeSTb4RGAiY7JJYTKB2NRGaUbWk3qQBMQCSEI6vPxWF zryNc/c9FC9dU6AVWZ8HoqXNuv/HCosQe7KDnv4tvXloCwthH1j5xrr3n6u0WpJpPX3x5SwVAYtHZYwpyhqW2lvSyRhzdBrq/evTWZT/YzvvFc49PTRcAAHy7lt35W88Db7dzpUm1Hz74wMczlq/4aW4PushnLAiQiBC1wcApQqDeiM2eDTKBcnVib7Q0 mITMdQdeUc3Oi6ahQg17/2o3GVQMbFo2ojCZKNV7PCmZ2yXSghAkgvTHO5mF0UAktw/zeFudodM8lrX1TJqbMyw oDsYgUgM1nv2OApxs7YmAlsVKYj4tS8EX3HlYk7s6uBSgjNUKcSoFPpNipnJNqgNgEINTHEEUtSkjMns6A405kosCeg6WwEAGLvn57McmHUE711u75oyL1wRD 7wbeMcg3EIhEAqFFa4xGRpVT5aOARWCrNPILqu0Rc6UZE iHEuOakPtRXidOIhBBKJV2h0xchV XOjc8/Tgpfub3YllB856tv34ZALOKpvePTYBBPWuuhpvIGAICCKx9ZfFV/K9Dw7IsRASzWUxSSocEg2mw8/tNTIADBbX9bf3jC/GEJvasJDYXAau3shoLTBoSQiK28EYgSxyZmA67d55kQgXo2gD69j7E0hATMT/vSvoQRgWRMO//cfO0Pz2LPTPAfa3QFmSqiq25OBEX2iPybItU S0jDJtX0E4lx9m6qVO6dHhUwOhVKlagXaI5HV4yS1pduE6eGXbR/jENIGCG9Du14jHUhdY9SBH1hRCCZMyeeX2ChwaCnvqF8a/m L13Dpg7KTIhZK1KNF4pS9H5RigCCoyjd0dTkDhm9KlOPI0gE0PKcIwYHTSQCO4RsK4zXojqfXV7sifGCAkF7caQmIKfHiKd/WsyQBW88dVGaa/uKhX/a5ILG78taaXF26PDLxiUeqXnnW8tfWbe7nmaMuPyGGQ2vPb/FA4PueGH55dm6ZfYd 2jl8jc3lbtteZPm3f/gZdb37n3o73UAAHTPn66dAwBDFr72h4szmTu upZUcOVd0yo/eO 7Gsflf3xlPr7Gtq7JzLlret3G97dUeOX6f1JsJ51TDABo86eP3Ln8IAAAVL5z99x39EPyAlO4 61gsGbLu6 //emuo60S2PPGzZi74IapAxJJ9N7dURzxxGmO7kGwn3Px0AMfvf71ZUtmZpn8COo5vOGll9d Ve5CW 7ZP77j3usmZYe2Lr3/laMSrLlvzhqAlGnLXr13FOsDBWu evPlNz7aWxMAR9GkuQvuvHJkihCqeveBX3wx bZJpf/auKfalzho1oKH7pqaY5XLJ8wbd3DjxyWN2dc9vfKKwP ZW2zXFY/aHAB1ff PlS 8u6026Bxy6fUzQgBJJ2Hsegake4mDGM3tUBcoZAG9AVXIEEXRsi3UGvTYhNm4IQCxpafY0dXslaVCAY8v3Fi7c0tz5lmpniMNrV5qcWYMPLswy06wrXb3lub0YQ7PkSaX31o4ZUR uL60pKbRLYHFltq/YMhQp00A3X hrC9DzZN3Zke6cZ5uiAgxLgrbR9RFTWd01yqZF5i6ioiQm9GhUEnR95gpQsZ MZLMf ZN3YgAxOpMTgi2NnnRkpJ11kUpCR/vKT0cyBubEAwB9bZUlFTVNQUlsNjzcgeOzHZaiRbMQASKQL0tFfuMMsS9/8tKL8Le1zftBRALis8ZnUy8zRUl1apYjlyV3jvD4xyNzglE8Kj5LHp3ep5HiLjMO4KobVZDglGW2E4XCAnJyVYAgMS8nOTIuWWo8sOlf/z7YQQABz22YeXzUf35iveeflFOuw/WfLNm5brRD2UOLEyvO94MACQ1P98hJBQ4Y9zbK9etfgtsTqc9IfbMtvKD1WuzBxWmw5Hmmm/WrFx39jPz8ms7oxgAALE4CwdmlB9pCgGAPSc/3UYkb21NU9gs2OVWpIbNTz38zFYfkIyho7M8Bw/u3rBqUaW0 rHp2V3pHUc3IKSeO3/O3l/cH ybePZA0 bf7q2SdePnrevUsfGJd0/NPVK5b8Tlz5zHXnL15xR6wFJtq246XfLC89/57f3DYmM1ifWnn1ie9tzimakAED62YfOUx37/1q T6jY9s i5l8eNefSCZLn8y/MeXbL292nU17zl2cWRLQ6OFYOL1VxG6xfL//hm9ZRFf/71KOHQ yte2u6zTD8pg9cDINCJyX2X0M7sVJ2 m62gpgsYHnen3q4l2bqh5Av4Pap5IYAUgfprm/PHXzQkN49Uf/LtrvKs3DGJQbm8MfecS4bl5yeJgZqv/1rpzhv8o8v6pXirt/9v2UHH6NH5AlV3yiJFKpk kwi9oqgaaeHghExbZ2BcYOrpPbntcac3HpM 47IHEo04fzCg KDoLEySDjVI0wbDsbry7455 hWdOzM/y Y9 sXeA/uTzxuTRCWlVyhRye8 8m2kjGPolAH7tzQNmT95WCoBAKm27MvPKzx5RefOyM9KUMVG2yXKaqdrHbUIAdi40skPgMRIdKHmRz6q5brloZSeni/HLv3LfTffeu31v17fCNaimQtvGROZZxA88tGHhxFAHHPP82/trrD09yRK0qbeZv33jn/RduGgwAUL2tzPHjR5fcMwoAQBhz9/Lnl69 5n8mpcYw5s7Jj7z617f/ voLNw2OGbTof92KF55c ezC0QIAVG876Ap0UjEAIM4JC3//qynJAAD9r1yycvnq55966EfRprtdbCV49N9/2 oDyLn6yRXPLln6/DPX9wcI7PzH qPMSm1nesfRDRDrgEtvnBL8bM3ndWw0WWr49v0dlun33X7pyPz8QROuf C6ospP1pf626mJNm9952vbVYtunjmyICd30MRr7rwme/ /d7fKN4a0qfOvHpUqElv 5MvPEcu2HlcesmmfdON152RaBYvo2bauKy3Gai7U8O0HuxJm3Td/RnFu7uApt959QXoPDNNJAyFI8VT9UKQUJUr1H2R KJUoC5TUHwCsWbdpwwd7vvt073ef7v3u82OtIfmFetbCqYMH5EHzUTdNT4G6VjEngVAAsORPLR7cj7SU1x3 T1kDyRp/ dB SZJXchadldxW2mxLswBVLC9VQjGIAGqjBsRSVdZN7tSpGkN2M/YpJE6lT oifbKqiCgpP2Cx2yySzyPYoL620ZI3/tKh YlhVzOmFOcl1NWFMxMFzSlEDNbGkKGhMEoShhoPVJXtPX54V2WjJXf8j4fmJ4Vam6ijODehrj6c1QUSpVNKopnKjv9IKbCbsQkRKFIkqCU/nS4IuV2y0RXyiseMSI cRaKnsqwRAGDgjPOyRBAyzp450vrNdxE5VVkXXDI21WJNHDIoBcrcEHD7KXQ2hSFj6hUTsiwAIIoEYixx5k48L98KQlJ2ngP2uSDg9rV1TrEuoYut0LYjsBAOrcsb/6lXU7 /0ocF0XrH0aMQnOPmXV1479r39l1wi1YYbiitg4I5A5Pk4RYzho9KbTt03EuHxawnVPdDZaDmh/t/ziw9Qn6dWwIRQEwbkK7cC4TEVFuoxi/fASzZxTm2brUYqzl/Q2m9UHDtAMXJTigcN0D8T dH4xSDQORj7 MNiGDKlRFsKWm0Zms9CFanA9oqXd4AUiAkHJBsCSIikIT0VNJW6fL4w4HWIDgH59q8dYfdXgmoLcHqd3ntA62gZnNKiFQNMshGJn7BrC/1DeIAAIACqnEvKiECIiGhlgD1Vn29uoo5IdFNkvIIIiACoiT5YssoLVCkEvW1BKi3 uvV1UYxTI7r8YllSFB5pp/6 BhC5Sf9iiYh TCJ3H3edzFkwZo/nF//r6cWv3Wg4rNVT581bOms7FhB8Ri5UQqSUuX1E0E0p3B3jOSMpA7XXmx2ef2SWCKUaF xLqG7raSdf nkfvr1YsvvZ9W dKZ3HN2FJX/W/AvXLX3t00tvNJR38WJARGHooteWzEw3chWqAnOSnbYgTwRRiJYU2v3mAiUAYBG1MiKKcXzp9JlAtS09JSnUXK8sMPnbGqSgsmQhBUM6bZQIApGD91IgqJYLAvj9AX2ChdRitcUxK7HBpv32ribdA4baglSwOxKJD4Fkjb5iXoFxv2248TgrHkOmwpzNG03s OHKnla/JxHJICobAgkACEQQBEETIwKKRJA9QkSkzK2qT17HsSBYU0deueDaLx5867i0b 36wxfcOtxwnCQXDsmEA41wdPPOpmkz0127NpV0NvJBLKIAQGnQF4pMyDMIduNPiyR1X7GeakVwFA3PgkMNQJ0Trrl9fIoAAGFX6dYSgf3L6Js3jr4Ckjzy p8V3/XOu7uKUP7TFLOKc2D7zqP 6WOTACDcdKCk1TGs0C6AWyDR56PWnOH58N vStzTp8RaBG0PsVtsiyofqzkxe3AW eFAQ3hisggAocbS6iA4u67PKQKJ3NMbb1D2waLkD/o9OvGo70FCZN7/qJdTighWhw0qGlpCBXJ5sMUbsjqdCXq32cenxv97bdgFpvjWVCMOdE7C3rrjfiGnOFOk1U4bHKqub0wMV3gN Y5 jQuwOm1QGk0mIK8MKhXHFItvRLEp2n4 SkFCQoEIyhAi49ewH L Iug6xIJL5o6xAkDjpne3u0x3elvRxT8tJgCh3avuvv6mW2568htPZ u1Zg3JAADYv/KeexYtXLqxokevlRNQrMdasQ287MZzEwFcnz1x372Llz7 2MO35KLsAgAAIABJREFUXn/b/cvWlwVOu4skfmHJnX7DLOuOD/cF5EvXkjXhqvHhTc 99vH qpojW99esfZowawrhiSCxZ6bJdbvLjnW6HK5/exKppAxad50 7ZVf/7rVwcr6 qPH9rx77/9pfPXa8wWYyBWc5asiXNGuza sbkigBis3PzmxqpYVcQBiLJJOs5/AELN7tYWn9ft97r9XncgGDY83I2VNJYTa1ZGKq3e9k1LwB/y1dcdPeJPHDIwUwgFJePpkVXF4w b9tvrynSKuLDL0 YO Fyelqq6su1H6iXnWTP7JXh8NCM709q4dVOt2xMI gLexuaqQ01 ieWCWLNiyFhsVhKsP 4JBMJSGGKK9Xr3O0Ul89cov04cCBAQzEdFQlEiQAkAgpwphtrS6GkFIWPCNTNS937UGvju3c3V40YaDloLfrr4Efezr6zb0 An/WffN73mlZe2BsCa2GHqh7Xoiluv2Ld6w0FXa/Xx1mCdv2fXH7uvWM 1Ysme8fCyhL / e5nO8tLdlWAmFY4YuqEWcPtwml4mcQtkoZeO2/Ux6tKlOtLSJ 66Netq19e88j9brDmjP3x4sevGWwDAPvYn189atlrC297ybwZW3CMv3vpY mvvbF68XsegISM4nNmzIv5yNAIxGoxRuJXzOaEjGkPPlz77IuLbvibzZk9ZtZPxu5efyIDc3LBPAkmnoFNn2/9Wv8qZk8cMUCNhTF2U/nKloPN2f9sobH86N79IRBsqYOGTZ6RLjXUsDcydgTifDQMyTK9qUgngY2fffsFAAAREpNSCwZO/H9Di1KDdft9kugoGD/EWVVTus0TAhASklKL mcXOnzlTfrZMWT81bTfwORjn3/3HwnEfoPGDI8qBq54nkREWeIgqG yjkyBIb acLNEkCKiJMmZy2EaDtHw0CsyZ826ZNT5Fwd87pOudO D uobpYxshwUAqGvnS/f blMzpF227Ll7hvfus8lOjWJx230Ojl6D3 f5Yc/WwUNHdizayxDt/cdlGXcr0tYDlXXhlKKR9pZ9NS3ys/KSMwYNE2v31HmtTrYcAITklNyi1JQkAWjYW99SW kNIRBbyoDRDvf3NU1 ZD f6t51AWWHvp944WxXc22fJI4Gg75WT3N1m1dNbyK2pMwBaWmpVgEAQ0FPQ2tdtU yGriIKhNGkpiX1S8/yUpAaqwtPxJAs1hNVVy7MjKVQX9b0N927PDeTz75aCAdlJSYkJyYZE wJdpsCTab1SJaRYtFsFgEQQQANdWXyM85lPqEN9vDkKo2PL7oE3FocZ49WPfD/io/gG3MNVcO6XVDfmoUi9vuc3D0LkhfuB2Gvce2H4t2wFW Q3 lAXqaSncCAIBkKAcAyeOu t48Z8Wg 8gOd TnuAb7jLze1KNziEmcAgz66g/76k2lRi6iywD6aurLatizoorFMaIGjDHGc2WYzdjK1jDlrRR94CroUQjO4nHD/rvlwJ4aBLBlDJw0bc5NP2M37JzeisVt9zk4ehNEf28kRx8Ak/XLievbiLqTpJ2NaSKi8gIMCZACIqXtn3CawpI99a4/T72rt9WIxKlRLG67z8HRm4h89RFHPMOQ9suJ68uIlvZLAUis7dUiyI4LIiGEnIlODAcHB0cMEMINYl CYTN2r2rCcYKI5oq08zQAkRKgzAOUgXszHBwcHAAAIAgE8TR9o8tpB0QU1D26nLg DZZKFgSQAAVAAmD6iZ4NceblynBwcHAYQAhJsqeEAgFrAs9/7wMIBYP2ZKfswXDi jQ0KiMPyfuTIsuVZSctbsMDMxwcHBwAYBHF7Lz85pbGYMDPZ3fxDEQMBvzNzQ0FA4fScIgT13dhojLiMAGMnSvD1hL/T6bm4ODgOAUQRZszLVu0JdVUlPnqa/iNMW5BCEmyOwYMPivFmREK jhxfRcmKjt/oihgxDZtBCnG1m0ODg6OMweEgDM1Iy0jh5DT6rV0px8QKZXCmvHjxPVdmKg0gCCChBAl5hLjySHcjeXg4OAAkMJBKRzsWI4jzsCJO41BCBGMTqpAeVYMBwcHBwcHR18AAQSg2iMQ5fAMD75xcHBwcHBwxDWIIBBCIvckySXRXRn9BZQcHBwcHBwcHL0KBAkJRYIAAuu6KK5M1C1LfC82BwcHBwcHR5xDdmBECxAKCAACAiJIva0WBwcHR/wgHA5J4RDf0BvnIIRYRFEUbVoJJ66PIpJK41EAQoAQBOZ9oYSIACAIRFLfXcAfjsfBwcEhIxjwtzTXV1cc8Xjc8qt2OeIQRBCSHSn9Cgdm5/aXLRgnro8ikkoTENUH QLRAPJmbEoRUdmqHe2JwBwcHBxnHKRwqM3Vcqzs0ODhY1LTMohg0e OKE8PEdSpIZH/YyWYjEP1pkwQ2CABMfwC1KrRBbSggkkWAACJ3CLq54P2XdeFaMcUFVigQUrvEWqlbDcAEFDTk21Wr9 skNYvNJ0Cmpryg aZKgkaRkU9qI8OY6oQAKnU2tJUdmCv3ZGWmpYZ9HvaIw464g4NHewud9At kAZZb0yYjrcEYOgjyWqtRmvqa6RCCfAI6CerWLmEfTxiU0lu51e9V0MARclNkOo8mZsog4PD8dxcHBwAEA4HKo8Vlo8YmxKagYAmN8Io5gQzSIa7/5AQJUnRNtIIQujUgpIdAsiC1DW9BD99q8ZHpO1YaPsxOyHKNWa1Db10mRIidag5gGhZr9Q 4LmihCVmL5uQrS EWDk1ZFQJtaMf8AaH0ZtpRokhoFCg KEpKZnFo8YW35w7/gfXdQBcbqHoRhWBJOj0hF3QIwnmbgD1f/pDH1MIduQwdMwDbWxN51gEAg7XkQd0ohgFUMiaAOvV67zaLr2Y/JI9JFkKtP8F7X7sans/JOBREl9cJ4ESJXIDPdnODg4znQgYlubO9mRGv2GSNi4CyqBAt0CqZ9QngAbp6Py/d4grsnLv6lJXrVwugFQ58ja1B0NwqybFFGXuadRPhrjHvoRahwLQojZhun2Xp/Ns56RHlYw2HJULBkA6PYP9YpQ8waM8RHtY7Ijtc3tIkSIJM7gGMg16dYYdVUN3KkOWwR3qjE2fdMqQZWdLtHHdgUZ76PbDIIeemErVq5VFu2QCMxFTjUlFGekPR6B9QgNSim1xOQRGCpjdFYCQoFQIiAQCoQgCCJ/7xIHBwdHdCAFACXZQjFVhLAmhvlGgAIQ43walMUSZqLKVA4ABA1eCAHQ3RjdKIDxTk/YMkSMaNXs2Zgr6BQMRgExMpES0SRlNFhoUF3uivkM/STV2TFM4tUion9HdhJPgOWCPd1InCxMmDOZuAmokQrTKCqD2B53AMblHqKGLTT6jFeLItUd qIXdYjukGgaVTTog2AIrEVoxzituh9jXhSUB43xik2NEjBeCYqMIk8IYd9 LUNUu2P4I Xg4ODgAEKIfEtF1WQRfXlfN1xEvdmr91Z9fUidCCu2SjF/munSjxhC7qDafn3VSNdJOUaYtkzo ds4GtYoDOEoRi8Ag7omMZNZNToT2idtBQvUMVCOGjwYQyEB1TpqhlonTpdX1SEMcWoDqtoaFchoZuAOkF1fYSuJRh92mj40fOx5aMqr32OSiMZrjvUKTIfkS7k9Ho1F6vgYnBzDtUE0uiIfhcc2azxKNFdGc3PAHBbj4ODgOENBgFBKZZuk3NEpMDYNVDMaYRpBi8driYiyFWDv8PLtmrCRBrVhPSMkisFhgvyg1hlx3NCNTiHqLNtQT3QJLchgOGxexJD/MRNpNWGFWXUjqCbR6G2oWStMWICZ ythLAJUrkpzRTTilGNyOMHYpGw3VbtKmFY6wZ1qKU YPjAzGIWubjEYpYDElOgaidqJzKcOeEQjdaYYTGwqOwkh8nqNoOU0QuDQizfPnT1n7t3vV4V7Vrj9c7tR1Qm0jr7yfz354HVz5s6eM3f2vGVvLZk/e87c2fdvrOFPDeLocUgNGxb9XLlK2c dhG/3kp/f8nSJ/6Tpd2Igcv4gRUopRUqRIlBAAApIASlQ RCliBSRUkD1EyJFRUIpQ4pAERCVc5UzKaXqSfJWU0AGVBdSq1GlEZQKKfNjOJsCVVTszA9QClQ901O3Y/2 CjciBdpWt2P9vgqX3CIyiihdNWiopSyo/VTHQ5YxqEoRqV4flUcHlYFGWSe1DUVB Vz5Eyp9Q7Vp3fzFJE7lTj1Zb71j7ig72mrN7dAXOTjR6DMwaCQ/kkHaVrN9/d4Kl9QhgzoJTP1qix2RSNnzI0hUBoupk3aWR0RNTZlHUOqPTWXnEOPN2H0X4ep/Llq4pkIvsDoLRk dc/uNFxYl9mC0yfPfxTcvLQFh7CNrnzjX3gOnn2CFLKSaT198eUsFQGLR2WMKcoaltpacUH0cvQJ0f/Xorct sJ33i cen5ouAAD4di2787eeB95u5wqRaj988IGPZyxf8dPc0 5vuxdAQA9Xq0DzbI/oSxTyvF fj8pbQrQT5amr8bUw mITMdRtmi0zn1D7hgAAoea9H5W7DComFk0bUZhszLjo8O5nbJdKCECSC9Mc7mYXRQCS3D/N4W52h0zyWtfVMmpszLD6gIYUBnWFiFlG0qvVl4NQ 4VobswENirTEXFq3oi 48rEnTk1BplVQ2DP0ZpFk3LmRRBGbQIQamKII5akJGdOZkFxpjNRYE8wL0MhABB7//Rklgujnuit2/VFQ 6FI/rZCUS7gozyTMVsmelN0xqPCjHt8AgslWYeAYBQuT3TlW5E1KhMO0m9p//tLuSq3Lnx cdJ4Su3F9sSiu989e3bEIhFPKU9P6XthprKGwAACq58ZPFV/a1Aw7MvRgSwWC0nvW0AAKDBINpsp6ix0xoEILjtb sPT5g/LKF3NaGhEFitZ9zbZwkhEVt5IxAljk3MBly7z seivGmTwyWQK9IESLAPKNEPw8AIIwIJGPa efma39yFntmgv9YoyvIVBFddXMiKLJH5N8UqfZZQqpF3Iz1omKr9GUHU6Vy7/RVIqNToVSJeoHmeHRlkUDrS7eJU9eUtH MQ0gYIb0O7XiMdSF1j1IEfWFEIJkzJ55fYKHBoKe oXxr b4vXcOmDspMiFkrUo0XijHC7JQigOAoSnc0NblDRq/KvBJmrFwuw2gkgjpeJm9UZ1SvjvFaVOezy4s9sZ7WG GgCvKPaJI6fbYyDVnwxlMXpbm2r1j4p00uaPy rJUWZ4cOv7zg0Y0t0H/ ilVX5YsAUvPOt5a/sm53Pc0YcfkNMxpee36LBwbd8cLyy7N1U w79tHK5W9uKnfb8ibNu//By6zv3fvQ3 sAAOieP107BwCGLHztDxdnxr7RB5h2fxJ6 x7T6WKaNdwSMlb44i2mOjBYs Xd19/ dNfRVgnseeNmzF1ww9QBplATbf70kTuXHwQAgMp37p77jn6o6OZXn7k8L3zoxQWPbmyBgjl3Ta/b P6WCq/cqZ8U20kHoxFTgYBa55V3Tav84L3vahyX//GVO4qjP3eaowsQ7OdcPPTAR69/fdmSmVmmy4t6Dm946eW1X5W70JZ79o/vuPe6SdmhrUvvf WoBGvum7MGIGXaslfvHcX6QMGar958 Y2P9tYEwFE0ae6CO68cmSKEqt594BdfTL5tUum/Nu6p9iUOmrXgobum5ljl8gnzxh3c HFJY/Z1T6 8IvB/5hbb9cyjNgdAXd//Y UL726rDTqHXHr9jBBA0kkYu54B6d6jKTCa26HsvTZmSjDW3RBF0bIt1Br02ITZuCEAsaWn2NHV7JWlQgGPL9xYu3NLc ZZqZ4jDa1eanFmDDy7MMtOsK1295bm9GEOz5Eml99aOGVEfri tKSm0S2BxZbav2DIUKdNAN1/oawvQ82Td2ZHunGebogIMS4K20fURU1ndNcMGReYun5 RMjN6FCopOh7zBQhY78YSeY/86ZuRABidSYnBFubvGhJyTrropSEj/eUHg7kjU0IhoB6WypKquqaghJY7Hm5A0dmO61EC2agvFTkbanYZ5Qh7v1fVnoR9r6 aS AWFB8zuhk4m2uKKlWxXLkqvTeGR7naHROIIJHzWfRu9PzPELEZc4gKrOirhEhhAI5vTYxCQnJyVYAgMS8nORITyNU eHSP/79MAKAgx7bsPL5qG58xXtPvyhn2wdrvlmzct3ohzIHFqbXHW8GAJKan 8QEgqcnQ 2oM18uiU5O6ntyIEqQ4WmoIbUsPmph5/Z6gOSMXR0lufgwd0bVi2qlFY/Nj2blSQWZ HAjPIjTSEAsOfkp9uI5K2taYpIXqj8YPXa7EGF6XCkueabNSvXnf3MvPza9kajHQW0OtetfgtsTqc94YybvZ8sCKnnzp z95dvf7B/8u0jWYNPm7969omXj55379IHxiUd/3T1iiW/E1c c935i1fcEWuBibbteOk3y0vPv c3t43JDJZvfv3pJ5anPbd4ZioAhI9t2Dzlsd /9eukuk3PLHru5XFjHr0gWS7/8rxHl6z9fRr1NW95dnFki4NjRd9iNZfR sXyP75ZPWXRn389Sjj0/oqXtvss00/K4PUACHRict8ltDM7VafvZiuo6QKGx92p1keSrRtKvoDfo5oXIqcf Gub88dfNCQ3j1R/8u2u8qzcMYlBubwx95xLhuXnJ4mBmq//WunOG/yjy/qleKu3/2/ZQcfo0fkCVXfKIkUqmT6TCL2iqBpp4eCETFtnYFxg6un3FbTHnd54TPrQ6O0RjTh/MKD4oOgsTJIONUjTBsOxuvLvjnn6FZ07Mz/L5j36xd4D 5PPG5NEJaVXKFHJ7z7ybaSMY iUAfu3NA2ZP3lYKgEAqbbsy88rPHlF587Iz0pQxUbbJcpqp2sdtQjBEBA5 U5C 2m/Jm G6JuxO11Fn0HpX 67 e2w2 1DsBbNXHjLmMj0guCRjz48jADimHtW/P7iTNeW5fc8 U1bZFVpM3 7/I5xnv/9xT1vlEH1tjLH048uyZBTW8bcvbyrqS3WfpdHOV3NldFKAod2sqoe/ffftvoAcq5 8ulbhiaGjq9beN/bFTv/sf7olFsHW3U54pyw8Pe/wrt tdkD/a9c8uycfNG/5 k7H/3KZ1aj/3Urnrm6v erR29duY9WbzvouibY3mi0p0CBKuSc/MgzC6dkCeEwnv4rl6cGxDrg0hunrH9qzec/ dOPU7RiqeHb93dYpv/m9ktH2gnkX//Add/e88H60jn3D4tZE23e s7XtquevHlmkQgAOdfcec1/Hv737tbpFwAApE2df/WoVBEgf/Ll5/zl2a3HgxcMBwCwT7rxunMyrQCSZ9u6rrQYq7kLxnz7wa6EWb fP6M4CSD31rt/2PLIf3puvHoahKgR/VMANPyKcTQCFAGwZt2mDVqJmDZ8SqGDAoC1cOrgAWnemqNump4CJa1iTmqoCQAs VOLB f4a8rrWsrLGkjWxMuH9gu01rmdRWcl7yhtto3M8bUplpcqoRhEAEpRotixIeu92TCzGfsUEiejq/RpziKipFpmi91mkXwewZZYX9toyZt86dAsT2tDI6YU5yV8XRfOHG5Rb8mIGKyNJRMKoyRhqPFAQ2uQhqoqGy25k388NMvTUt9AHcW5CV/Xh7P6Y01nutNriLbAFCvShgCiBBIBQRZCgQDt qJWnCLkdslZUUJe8ZgR6ZGTR/RUljUCAAyccV6WCELG2TNHWr/5LiKVKuuCS8amWqyJQwalQJkbAm4/hVOcuUDbjuyvBwCocvb/ynXl6/v9KHg63d8D1zJ56XbwUhKTvPAftcEHD72tobjXYVUF2ZjKlXTMiyAIAonhbecHxAcI6bd3XhvWvf23eBvuYYbiitg4I5A5PkgRYzho9KbTt03EtjuzKhuh8qAzU/3P9zZtER8uvcEogAYtqAdMX7FBJTbaEav3wTsGQX59i61WKs5vwNpfVCwbUDlBBTQuG4AWL8ujIEIh97H29ABFOujGBLSaM1W tBsDod0Fbp8gaQAiHhgGRLEBGBJKSnkrZKl8cfDrQGwTk41 atO z2SkBtCVa/y2sfaAU5ioAgIVI1yCBvvIlfMOtLfYM4AACggGrci0qIgEhIqCVAvVVfr65iTkh0k6Q8om5LkiRfbBmlBYpUor6WAPVWf7262iiGyXE9PlFNiCAIRHsVkyJHgRAg0dJ T5N0mSEL1vzh/Pp/PbX4rQMVn616 qxhS2dlx4qFx0iJUpCUKi YCKI5c/vUI 38Syf300mz5feztiPdDmx22QEi8phECSxG72h7CiRnJPGVpZMAS/6s ReuW/rap5feaCjv4pWIiMLQRa8tmZluZClUBeYkO21BngiiEC0ptPvNBUoAwCJqZUQU4/iiiZV7GHewpackhZrrlQUmf1uDFFSWLKRgSKeNEkEgcuRdCgTVckEAvz g55AitVhtccxKbLBpv72rSfeAobYgFeyOROJDIFmjr5hXYMyGDDceZ8VjyFSYs3mjiR0/XNnT6vckojAYm1MEEC2EUKCgbLlX0n7paeHNCNbUkVcuuPaLB986Lu1bu/7wBbcONxwnyYVDMuFAIxzdvLNp2sx0165NJZG726KDWEQBgNKgLxSZh9ed09uvUHAUDc CQw1AnROuuX18igAAYVfp1hKhoKe2mJOk9kajcwr0zdtH/IMkj7z Z8V3vfPuriIEAQBAzCrOge07j/qnj00CgHDTgZJWx7BCuwBugUSfj1pzhufDf78qcU fktoNMxW7xShLsu00J2YPziI/HGgIT0wWASDUWFodBGfX9TlFIJF7euMNyj5YlPxBv0cnHvU9SIjM x/1ckoRweqwQUVDS6hALg 2eENWpzNB7zYym0HYz/EJdoEpvjXViAOdk7C37rhfyCnOFGm10waHqusbE8MVXkOmo1/jAqxOG5RGkwnIVlypOKZYfKMr1oQA9EnXuwsQCy6ZO8YKAI2b3t3uMt3gbUUX/7SYAIR2r7r7 ptuuenJbzydrdeaNSQDAGD/ynvuWbRw6caKrl0ikadHlBidKtvAy248NxHA9dkT9927eOnjjz186/W33b9sfVmgx/5c2x NU6AAR2xYcqffMMu648N9AfkatmRNuGp8eNNzr328v6rmyNa3V6w9WjDriiGJYLHnZon1u0uONbpcbj 7WVPImDRvun3bqj//9auDlXX1xw/t Pff/tL5CzdmizEQqzlL1sQ5o10b39hcEUAMVm5 c2NVrCriAETZJB3nPwChZndri8/r9nvdfq87EAyzbyo2SBrLiTUrI5VWb/umJeAP errjh7xJw4ZmCmEgpLx9Miq4vGHTfvtdWU6RVzY5WlzB3wuT0tVXdn2I/WS86yZ/RI8PpqRnWlt3Lqp1u0JBH0Bb2Nz1aEmv8RyQaxZMWQsNisJ1h/3BAJhKQwxxXq9 52ispMQNdeVIjIDfNpAyJhwzYzUvR 1Br57d3P1uJGGg9aCny5 xP3sK v2NPhJ/9n3Ta955aWtAbAmdpjrYS264tYr9q3ecNDVWn28NVjn79qyY Tp1sHmEmMOgiV7xsPLEv7 5ruf7Swv2VUBYtr/b /MA woqv3/PdV9ZybJZJJMkgnZQwiELYGwKyKyCgq PAQUENzeQ3EFn/jjuS 46wMVBaMICoqID1FBFBDkAbIoBJAQ9i1AwmQh2zDrrfP7o6q6q7e7zNwJGXI hKRvd3VtXcupU6eqZuxy0H5HzB/dOGG0cm5UiMBrq8RspYza8cRTdrvhB8tsQVMTDjrrcxsuWnLJOR/fhFLHwqM/8/nj5zYBGL3wpLfv9s2LP/b H6cXY6vWvc746mcnXPzziz7z2y6guX3eokNPaa25vSgKsWgL6aLgVPubPvGpl8678Kx3XdbUNnnBEW9b MAfh5IxwwuNjAaR1/3tH7fHP8PJ8yy7UMqWbdv2AATW0z91Rrn372X4/0QzWN236n1x86obxmld i TmwledGwljm1YxIjfDav959KwCQahk1bvqc/Q/ccfa4vs5Husth6/S9dmh7cdWT/ zqB1TzqHGzZ06e0dr99Lr47QI3PSv11DljnvvbPXeUEU7dfsH8XGfYuDUPIuqe66Az9zmZAc1aa2jWA7o8wOX 8sBuizuOOOLNu 17ZG/3puGJ6daA7l69ttw uTUAoDcu/fGHv3Tzyxj/lm9e8KH5r/KWZK8GkhuCENPT3bX8wX/M3XHX6k5fZcLRM/eYlNycR2949IXOgbGzdx29/qFV681eeWPat98pfOnBzldKbf59AGrM2Cmzx40dpaAHXlm9/qUXXulnUNPYWbu3bnp41boe9q 3dOrq4KnHH97/4GM2vvzSiPxwuq ve0PXyys3v LMm6hp1MRZ48ePKymA /u61mzoXNldLiW Ra6bAaaW7SZNnTaqRCivfenpZ3o57WzVi1u1KGM ZV/P5r6ezc898a8bb/zL9jR7dEvL6Obm0c0tLU1NzaWmUhiWwiBQQaBUCFZsBlakAc0og7TZWXgboPzitZ8/68Zwx3nbje7rXP7Iiz1A04Lj/32HbbPnltwQhBQjYp tgVeeu/e5vAcbn74vPtKAu9Y9aXZ4KCfuAyh3bXrx4fSYlfs2PXPfpuz1Vo2/R96rGY/aKPxwFu7rXv1E9 rU3eS3yHcD7l61 il/uXW s62YCnvk5RyLGQIAK8bA1m/RNQyotnl77HTn3x99cBUDTe1zDnjT4ne/w1 hs00huSEICchsoC MEDyrX/lwI5t615C4boqVmzo1ZtWvdXNgSzD5oA9 56APvtrR2EqQ3BCEBNmjj4StmYTZr3y4kUy 2W xMW/IKGtzTqW/4E7kWUEQBCLpEEcSicXYr2pMhCGSUcsoTjxNbTwTmptsp5e2wTkmQRCEfJQiZj1C91vb1mBm5TZ0lA83ovE/ZYSmSCfDABObySNm1oAKwco8phGwp5AgCMIWgohGjR7b39tbahbfqMi AAAgAElEQVTL9xFAf1/f6DFtRoKRDzeiiT5lLY6NwGptYtjtDuHE2G1kBZMgCEI QRhO3m7ay vX9vX2yDBva4aZ 3p7Xn55zfQ5O qBfvlwI5fUp0w dCq35N6 TAA4JCIwE9mla9vkOiZBEIQ0YdjUNn5y2DRq1YqnulevkoZxq4WIRo1unTV357Ft7f193fLhRi6pT5l9ai7M2UoaHJ2r6Hb7ZWU1McSkGGVlXuvp2kBqG1nNJAiCkIAIbePax7d3EEkzuFXDrHV5IOr85MONXFKfko2qBVBsF6Vpd984IAaBQnZo1swMgjH/BdA8qrVr07pRY9qCsOlVSJAgCMKrTXmgrzzQV92dsJUhH 41QHmgr7 vt3lUa/YRJ82CoxVMYCIN1iCG0qQBTJwyq/OFJ9onz2hqGSWm4IIgCIIgbBmYua ne93q5zumzwOgCXYFE0GDAQ1oIADAxCE8RY193wkto8a0TZq6/cudz/f2dMl0oyAIgiAIWwYiam4ZM2nq9qPGtAHw9zzM6lZyNqX3TzcYM3bCmLEThiOWgiAIgiAINUOAPYOJWBErcucxKVG3CIIgCIKwtZMUV8gjtu5WDMV2NfYWj6AgCIIgCEIBZFUy7lc8x0QMhYytjCAIgiAIwlZKjq0MaXeKgaxREgRBEARhq4TMgdnk/bHEZr MeM9fn4GB/vJAv2huBEEQBGHbgYiCMAzzNpYrl7XWA6wBYjCxPS4AIDMHxGYpNCVUJAT/8PL4ORF5M0bmInmvajxD1lSGBsDgMmt75qS2gktfb8 6tZ3PPfNk16aNWsvBTIIgCIIwYghLpYH /uruMiilWse2zZyzw5Sps1ISxcDAwPp1a558bNnG9eu01u68I7O9bvy/OwjJf8jI/GOdJa VUu0TJ57 unTJ2eE7lYt0IAMbPdIi8SU3ztS3mgf P6l596bPlOuy0a3z5JJU4wyCppKPFPjeR4k/WgUCFUQVNEuZcFNyr57S1lr W1dFCVXko/40oJqsOfOl0UfspBBZXjOipTOUq/ oIY3BxoOtB4oFBHWavsJDdiGYc1lcSa01g1qtRQTSpXi1gdHycdsZyI5tyqKZNrG8QVepNXBxtT6mp54jmJBqj1vFaT2zoSWFuQgylmVE/dG yUQNzuIHNV9aXsrdq6mxoeZtNTTxHj3MvCsHDLX353yFH/Huk5OCpT9pbRopARNzzdCpe1Xr929aPLlo5uHT hfVK0dXK5XF67etVjD98/eXLHpPYJYGbWusyay5rLWpu/LKzLms2FNkJPJNNEJH9FEg/r/q7bb75 /zccOmP2Djn5kMxGs0UeAcrphlR0svbAQP zTz 284K9x02YmH2zODeHRn2VMP2AMndiKj2rIdDa3krJLgWVkKr6WEmsSddMT9oqeKkeCYKjHRWH6FGFO162cNrdYHOs9vjEnfLg2sj8xi4nv5ILB3Oa1rzg69V9FreCDa6aFbzjKs/T1NZ3potGNoC8L1FLr1ChdcjzcggZWaNAkxZcKKfZqd6h1hyXVAGs28u8TK7eTvriS3H7Vj0ytX6PqDXkQTX9uW1U8ndFfys8zNwZpJhaQ0TY7ObvJcY1pQQCmG3bpaPzpG3hYyaiCRMn77xwr8cfvv Ag4 KRBmt9bNPPtoxuaO5uUXrMgCtnWCkaxqu1giBW5qCB5feM2NOjiiTchsCUAydTK1NM/OmjRvGjh3HRmdTpY1I1LTBmxDHH2WQbZJ7kPm6vtvBaBdSYaW9tY7yO7XKXtWHp1qr05 65LvC7KoUKCXi1IBCzezn2NA9NH0iZ 8NjRrKVs35Umd0Gj2WGGbqlXq8t3J/5QxDB V1Qe0efP56A47q9dRFolY1SM0lKN9hDZ1rZUVusQcV3qtH61xdBMwRzFKBx1 25nArOsz20plxWEW/KBv1 qhRLs7ec8t6GLZnJHJSC3F036lkookeAIyxY8dv2rg cSon8 ZNG6ZMmczMIGLNRGANAjT5Q7YGoIjXrV1Ti0s7wUScGAvqaIhiDqXkiu1PXuHNK9hc7DznzTw/Koycsk9ySnA0LEhMtFWnppRXHT4VjCzr7kirqJzdyK5qw1EQn8jzag1i/nfPdVq9p6eCUBLNR2FW1fYV2Q9jCBJXUvM25L600e9Xp3J2jSzZKGcENgTffPkjc6sgAgW3qxew2nqmQUw4FnhcUaKq0Eu7eMS9QgOE/8qBVdFz5DqtR2QpCMwb2OU01BV9z/ZWmQJQq5yaCDT/dvELWWwPTjZVFCkbiJz84okfzLB6GY5ez6o5tNYEYmZigKCZQMyayQoPjSwgRvFTlZwzmDI4jzJicEGXnXKVhgueFWqmCv2vPHDIvZeje6jSrg/mo S/UyF5VKjLqD/4mrOrpppZycngymvVcWJNMyb16THTXg6tpqXOLBuSX8a/KvEZvNK2UU3K4PuIaklrrEHPUIlbcK6n 3Ev15jddSW5EZqM Hk9BaKR5Ty/ftcpFNX/SUyANbd0VRxW6SoqDvhr9W6QIkvOuNO/pTXIqGDIhMxs gNiJiLNTESMSBVjhR5nsVsQJoGYmNkqdohIu3mrhgozNRGWwRrxcNVEnJyOxkQuBVWezo/HvRXUBzmiZ/GXylUgcq3DryL1YzYq1RQK1b9ORulTS7QqvpBR7Qx62m1wo9VK4TmxvWbPMqJkPZU5V3lc7aXk0/QQZ7iqWwO655qn9Crz6ssJXPFn/aWy4RoB42uN91JUHh3Ul7TUCKbWZNYayCBEs1xqiFeVb1pJQKoSvSoK6QKP8t1WTwin/q0h85KD/CqvVRd98tu8StMgnhAROScCNLNiI6kTgaP5JSuwAMzab5/dmiQA0EUros17xKS9FpUBJq7b5G8wsJ/u0N0zscpuLUOcWYOdl/k52liqvQgkQsiWBk/YqFmayPOotspcPHtQ5U2uXNhST7iWDi/rwj8ctOrrRWFXezsxbir4FJXv1RKbKpOqdSmRaiPdiNbh5SBGj0OihlZzeDr1QcNbSL9Sn56kdgaTm42NS8IYfmiZWamq1zTur3lsVdOz2iaAc6wRUuR1FDWSSVs9bU/GeUXppOB57XJJ0lFeP1Zp/J29Q5oB1kaLosmoQokATQwGMZnKG20Ow xUMpViaQQjsFHOJFJKVIc0PkicgGWyg0KjEopjx8wc28oQgbke aqWypCMT aSUfTVizwtaNPz413V3iKZH0Wua63TFbQatYz6MkqZwvdrELpyh0MZp3UUwPrnbVJCUiWqtB1DF0Pquv3qqzfSbHUx2uoilE9hLzSo3jtBftFp5Dxs0fOMsqsO/ uMX22tY/KZHmKvlvttcu7Vrmkp9KLodnG/UTWv444tpwXmijFpBERgXSaCZkXExKTtsibvUCMGAM0AwUwYaau20czFnRgBbCxxjI8UJ3ZYFDOVhp hW1ZeMCeWZ/LTUPLFlDqDNM6zUlHqEjWNdopHl0l1VU0xG8JINSpgWU8rahjroeroo/I7BQ3oINM89PnVgvfrm5WuICEKI5bB1sM6Orv67g5h0Wq1Mlm9Cg9BPVldxqogdgyyNtWqo6pRZV1To5yeyypo22qJ2qst4xMZDQVRmVmxUcKQBlHGVomhGUza6me0NS8pkGWIoSPNgzGwITbzOmRUM1sQuxjbdJtRSYjEFwIhayyzlVJPQ1KHP5T/i7PP6moQCj9zDfMGlXWjdRSgwlanQm0f9HBuUNGpYapuWOGKPxvLtiY2jeDMLBSaa747hMTXNNQqcNKAbBnC5JedxSik4FlV/Wk1AWMQER4pvV51ok6cAaKyM8w1goZOdmlGhNGsjXbG8yHfY7u8iUAgTWykCKubIWOWM2zpYitF2biFFR0bdZOcV Ax5CqSR0YiqtbgZJ5zzlUdL1ViaK1fzstbzuykyvBrWxMdhMpULC1byjKpLjVQjdSphqgr0HqsCZErBw1eGy/UhNeJm9mi/v6BZx6/P twp90P4LJmMIETGowCScbJOmYzNdJkhRsQwyxuGurMYiHJySICEJYBJjCgoTVr50I7J8M9wSRgEIYgg/okg3gpmkpN3ytwWlOgPMjIFAdSGFRlMmO5kSbbDLtlXc0M1Ux1i1P/zG/mhSp5PwwlvMYA8puTYWlTRPrY kl14sxQKpwweVpvd1fL6LHmZnfXxrYJHUFQKg 8wtHZkJ4POd567oigNYhBgIZRzGiz rvxqTF/qVSUKPQ3wIl3w/NeFFFmG6bCtHeNtxvLMAdSeeKuXhonZhT5tPULEI2M32D8qr27b6DfW52nwjZNTifOY8dO3LCuM2xqISLWurfnlY5pO2xev9o8zfqQhe2abgBm7bMVYsi6t3NMW6xAh978kT19iZkBu0ux2cNvS0VGEF5DNK4SS/8mCMLgyO3EVRCMmzC5u2tzU8uo3p6uSVNm9fVsLurrC7QycJIM2V32EN0BEYOosRs0qEhtnreTiUJ62ikZ3S1rhCwIgiAIQqMo6sRb29r7 l4pD/T39/VMmTGvt7urLh/M8QbR1i7uwl7aHYU9s9yhkzC8IUrFKlQMMMpmDZM5eoG8YSAVLK4TBEEQBGErp6ATD1Q4bnzHy2tXdkyb29e9uVJHnyeNGFHFnHtA8UbCZj8ZIisAETV2kqk4kvEKJu0H6C3GFkFGEARBEEYiFTrxMW3tL69dOX37Xda99HxlH7I32ZjIwBwiyUZqYWvrq529DDf47FFjipOnJQo1aW0WMOVulSRaGUEQBEEYoRR34oEKZs9b2LVhXZVePlcrQ3AHUZq32e4rY55BM4OJuJHLLNnth8PZP4l9ZdjhJWFL2iALgiAIgtAwqnTijJ7uzVV9yHnPrMV2K6DN8mtrG6OdLYsGAbpBihmza03R09BuKhOvx2ZAa8RHY4skIwiCIAgjkqF34nkCBDl1D1nFCBnpxkwskYbRoHjnMg0jRBRGV 6o79TeOCNg7wpBEARBELIMvRPPP8LOHllg1B5ExAA0gc0BBtHR2DyU48bqIOfggsQqJ9HKCIIgCMIIZXi0Mkbnos2KZ2JzUgDBzDgZexZ7oEGjtlFX7k8uVc5gIhKtjCAIgiCMSIbeiecbqJDRuJC2y5comtQhYwJMRCA9DBNMudJMCM2kyJ9WSh/UJJKMIAiCIIxIht6J52pl7BMCsT15O57NceYyFXfgrRNGvCYplmZIg4hZhQC01pHUZuaWosCVCpi17PkrCIIgCCMOoy8Z9OvMrFSQ563ZVobBDGs3Y6eYON6YjofjyIDcfXLiCabkGmwTVxrT2trb09Pc0tLguAiCIAiCMPwMRTPS29s7pnVs9ngmdloZt5MMszu22vxjjGjIWuo0UpxJ2N6wAitQctaJwVrHMQ7CcOr0WZ2rX rpfkXOxxYEQRCEkcWgtSLM3NPd3dm5as68XfRAf9bj OxI89NoSziWZqy807ht8orSwswhR3Na3m1ziEEYNo1v7whLLSueefyVF1 QI7IFQRAEYWTx5BOPDuItIjV6TOvcnXYfN35if1935nEkydiNXOwKbAJrdic6wlxQIw4NIMAdS6AB7a9mIqIwtbcvEflrt4gwvn1STtiIrWQAmCIAiCsDWiy2UV5Bi71AKz1uWBHDkGiI6QNKuy7fkF7JQyVlPj/m7sSUypmBDB2MpoEwVjIZxZOlUe6CsP9A1fPARBEARBGC6ys0NDxggtZI4lYIKZtCHAbjWDyOa20aYy8PeXMVcBcaxrYY/GBisIgiAIwmsGd6yjEWrY6GEIThdiNpjh Hq48UQZexCUWbwt0owgCIIgCDkwR9a 9sRKa IbLZUmzl82PXista45KTL5p3AXYEEQtm26Hzj3pPd d1lP3S W11x71klnXP3iwDBESm96 JefO/1ti0845sRv35czg98IBp1wQdhmIII9SpI5WrbEkUqG3JrppNlMQ8hVtYRuWgvEsSKowbKUIIxY9KbHrrv0st/d8UhnD4BwbMeMeQsPP/0Db55ZAtB152fe89VlUAvP fWX9x5dxae6HNcPb7rt0 /75vKmff7rgs8fNEEBQPf93zz9i11n/mo4gqsANc3c9 DXzR49DOOk8upbL71q5f6fW3LCLmOaR41qfACCINQCs91Mxq4TIoY2c05mLxk7/9RQI5l0i0LegZEKw7EbnyC8NiivufnbX/jxX40cA2BgU czS2Z VWagdPQN8/L/vjE72vaixU2x4nf/C0vccPhyiz/oX1atoeu3W0tY5pHuSqDEEQhgx5C6wTIgtzrnVMjiZFv7L0f65IFNg9zlhfwwOf84yeFcOSUIIwbueuKvDw0Aaqf3fOPct20/mgY2rnxs6f1rpjYBA8/ 4kOf/E0nAOgHv3HiYgA7fOwnn2z97XmX/P3plZv6Aaix0/Y85PjTT3nDjOC5HMcXvOOeT3ztrj7s9NEl3zlsgup 4Nx3n3tXH3Y 86ffOrjpmRsuvfCqO5av6QWopX3G/Nef9F/v3bc96H/yko99/PdrMPlt3//RqXNLqfiq0YuO3PHRv1x6 1vOPWxSSpLQXU9cMlv77t6Y3cNGXPo//zw 88YHK6 uuND1/1/R9d c X tp2OOrkQ/sBq/joW3Xb5Ut /pd/repF6 wDTvjA6f6 hV15x9xp/2Pu Hp5hocNfSb5x Xv/Hfvi5fXqvRHrzvouz84bloIcN q23/508tueODFbpQmzDv8P8/ 4OvbgxwPxyruee6vl5x/ a2PrS8jaJ2574mf eTRM6I4WrUTgG euBhN 33m8k/v2ZKbqN7HL/zA51d86OKv7TcaALofOPf932/93A/PnLfuyjP/69bXv/ AJ/9w3YMru1u2P IDn/zgQR2lCgkXBCGPWDRx80x9ax7 8/V33vPkmq4ymsZP233v/Y7ca oY4yZXXULBxNmzd2wvEQDuuu am5btcNhJu42qRfqI9C/MmhmkSgqNPO9JEF5TUBA2BQD0hheffXZ11wDCtmm7HvyWN84sAdw0cc6MCdbduGnTp8 YO72NelYsf2pj6 wFixbttfPU0qYX7/vD9z972eO9uY7Dwjo78Nw1X7/w5uVrBrbbeY 9F86bNPD8A/c s7mGaqrG7X3a4o6HfnXNIyk7Ev3ybed9ecnyGad 9XtLzvv4wd3Xn/ul3z7Vl3Zz6/lfv/yFBR/5zgUXf/GY4PrL7u1mANCb7/vxF85/cNpJXzj/Zz/ 1lmv23jll8 /ZQ11HHDorHW3/22FWejJXcv/ulTv9uZdWxOp0pvuveiz37wZh5z5zSVLfvDdj7157ijmfA91ufOW71x037R3fWnJxUt 9j9nn7JvR1PiZNuxB3398u8cNb5p4Tm/ueaqqz 95 haEpXN2mtvCd/ lV9e9cuL3ttwVL7lyvCxMuCEIBlDymsnfV3Rde8Me7 rc/5uSTzjr9hHfsPXbFzdf86PqnN1dQuVDzrH32fsPMlno1J0aOMbNLSlFiX5l45z5BECJG73L8kVPuve6ll2744dk3AOG42Qv2O3Lx29 yx8RSaepbP31uuzF/WXDG cYehQcWfu0XJ4xG18svb rreeGPX//Sn9asufOO5057b47j7gduApA3w9u/7tm1ACYdedZn37NbqwIGNnZuag4A0OiZuy/afTVNmZE/eKHSrKNOfcMfv33J3972jaPHRrfLa 6r7gkC/8x1G7jiZMO/nMd979oWvOTij /S4ru55v7mI75y2qHzRgFT3nfG8r fcwcA/fI/rri96bhvveew2SGAjuNPP/6OT/3pgQ2HvGnfI2Zd/rv/e/5dc7dv4q6Hb3wQCzWyvBa7z0uruvuLX/Df995jv3aSUAHdvNBfTaW3I9fMOczk1qyh577jhtosLECR2zq3ycwkTNrfTW INOe/tu40Jg2uvfuuhn5/3j b4DO/ITLghCEWz2xSOAmPX6u6 59ZnJB519yv5TwrLWeruOKTMnlM/77d9u2u0dx055 fqfXrv60ONPnh0CQP qq39xZ8tb3nrU5N6lV1 /dIfD372w Zkbbrp1nca6G3/wD6B55kffuUduoP6iqKjZNDJNaK5YBBlByEJjFrz/2z9aeMOf/vbP 5c9 vzGDc8uvfEnS 956gvfO3PRmBxZgrse f33f3D1g6vL3s3NazeXs069QFTap6bpwY3rtszfX/713Xl8ZO3WHXPQ8 9rijOwCEUw//8FcOr SbatvjlLfP PCvf/vQG98b3RxY82Qnpi eY WfsH3 buM2P/78K3qXFuW5Wa2mnzjLTq00z9hjVngHgP7O5S/0rlr 8ZOu8EKZ1rmpHEw/4LDZl1xz24pTtp/b88hf/kV7/tfOqUzp73x0Jc88Zl7idpGH6g0HHzXnz9/7wIdv2G vRXvt/6aDFkyrOGArTFQlUSYcP2uCnbNSLeOa lf1cFHCBUEohAG3MR5veOqeFbTjiXtuVzLb7AKg1rl77T32iXuXrTtqir1T7Fdp yMPPzieYKppOxitNYKA7e4xzlYm86Ys0hYEAIAaNWv/f/vg/v8G6K6nb/jGORcv7d1w5y3PnLFot x58d3LfvGtqx7cjHDHo055665tr9z/qyU3r600g2uOFSlrACj39rjly0HHoZ//VvPvr7vj/ieee27FykfuXvnI3Y/jx ceO6UWU9dg2hGnHfy7r15801GnJu5Xax0YQBDG55qE9pqZ1Y5nXXzuYRPSzcLEfQ dc k1Nz/3jslrbnqQ9jgnLckUBVTo4Tu /tPXPXj3Xffe/49ffeVXVx7 5fP c6 xlduivERRcmo 2TBS6pnZtjQ34YIgFOAmcpiB/o2d69G676TmxOxO2DZrPN2 dmMvxjUqUA1GcuDHCmWwUqRke19BKKT3scvP/9nv73r8pa4ygLBUCggAgtDUJzIdoO7r7mcAevMLKzYDaFp06mnHHH7QPjO1v5Qo5RhQLW1NALDfUD0BuW3f64m5rRXas3THrdyR8951vf 9EVl35y7xDA8/9a2QcMrLzph5/77Bc//4NbVhZv20Jjdj35HfNW/PbK zfZqh1OmteBlUufdQux1j26bEPrnBmJ9dLh5LmTqPPRNdbf/rVPmoVapY750/DcbctyFhoEk/Y6cvv1t9 y/L4blwWLDttlTNpBqWP VFpx9xNdnLxZ5CGCMbMWHXrif3zim efuXD9HTc XcnypTBRqnlsC3o29Rr/y5tXru6p1MQVJVwQhEIos2lL5tSjLbDZL7MdnNimzI5UmNnOdMsh2IIA6O5n/n79T77x6fef8s5jFr/j7R 56J89ANr2O3hWEwCUJu3QDgCPfP9DHzrrY1 9fv30eRMA9N37kx/ 4tILvvaNv232/Eo5vm6FmrrP/GYAnb/74pmfOvuMr9/Z5ZyWX7junNNOOfWjn/3Ml7/26c9deO8AgI75k0sAv7LioaUPLbvvwecrWqYGUw551xGl 37/kO3Og0n7HbfXwM0XXHzDIy ueuYfv/rer5 dfsSxOyT0SsGk/RfvvvG6n9 yope574VbLr/uRQCAaj/glENG//MH3/nFbY 90Ln6 cfv 9NlP7tuxQAAqIn7Hj53400X/2xpuM8RO2V3r1Ht 7/zjaXbv/e9K 95euXql55a rfr71urCzzse/q6S66 /aFnV69bt rRu 95Tk I5oLyE1mUqLBjz93GPPPnW5/tZe594dbLfvdUxTWZRQkH p 66mtnf/fWzorzg4KwLcLxSudSW8c4bF6xti hFRnYtGI9j2pva8loSQct3TiVanw NgCjpymaYBIEAWias/i9x5Ruv3/ZE8 v6wUQtM1ccMjx7zltoZlJKc0 9n3HPnTRtY9t3LDy Q19ndjp5P9 17r/ufLeFXdc373w6FNP6L7oquecX2nHPdy23wc 8taNS657bNMLa0Yddfp7X7zkkqX9AKAm7HzgouV3Pfb4Ays0QK3T9zjspP84dnpYx7lwo3Y88ZTdbvjBMjsoURMOOutzGy5acsk5H9 EUsfCoz/z ePnNiVfUe1v sSnXjrvwrPedVlT2 QFR7xt4QN/BADVutcZX/3shIt/ftFnftsFNLfPW3ToKXahkmrf67B5F164fMwbj9wpb/2yGrvPGV8xc/ fl3PnV5H0oT5h1x kIq8JC6wnV3X/HlyzpfYTRN2vnwj3zquBmVRJniRLXscurHFn/7gk cdGVp/OwDj1u86J//W9GfgoSj3P3iY8uf2rlXA7KJjSB4xNa3YGrbfv8ZfPX/Pdi50z6TrXqEu55eet/GUbsumFiiDS0l9HeXGQEA3bN54wAys/Ok7BGVlSBf7ZOcUKL37b5YMzM0GJr1APSALpfLA/ueOOeMs744tMQKgiAIgvDaob v79Yb/7DT/J1ZM8CstWbuefGOH/7o1jVzDvi3N86bNqp/zRMP/umm5T27H33GETNGoe/pv/zml6t3fvfinSfxxmW33Hzt43rB4rceNbn3PruCqZW478kb/ny93v34A7drDVRzk4oOuF7z8qZTTz/zwv/5wjyaNaalZXRLy jmUktTc0upVArDsKkpUEGgVDzosUYzop4RBEEQBKEYYgCs7SGSaJpywIc PPbPf7nr9z /q0sDoKkHLv7IgVNH6YEyBzMPPGj/a2 7dMkD4ejx8xftMueZZRn/wpl7zZ/21wd/9Zv7KyzGTu3w62tlQgDMZQYzayJAN/bQBEEQBEEQXlOw2 bXiBNE1Nyx67GnzH r1rp39e2//s21y55Ysdd2O7UADBo97U3Hvf2NWht1CS/YkZmZg0VvP25PcwdUmrjj4hPmWYVKrkqFoj2GFUCggCie91X O1prhlEXiW5GEARBEIQcYv2I2/SXmRhkpJLXnXDC8QubO5/faJcFNlSiIA9m1loDCKPFSmwiJDKMIAiCIAjFxCdjA SveSYCEzVN3PPAA/2F85oAABi8SURBVMq6DF0uu9tDDZGgCRoog8tgzVRmUkguxvaRg7IFQRAEQSgiPhnbHIXN1nzG7dVrrrecbkSxIiPsAApQDGiwFuWMIAiCIAh5MJuZJbNpjDkb2801GRGGrEUwR7sCNzYCpJncnBKzYqMnysRSEARBEAQhC5FbvGT s7M5xNHGeUyouDVlY1FAjuQiU0yCIAiCIOTCdgbJ7FtH4GieiaPzC5ickmYYSB2TIMemCYIgCIJQB2TXRrvlQuTOWyKziilyyIQtYTITizKatCZttEQywSQIgiAIQi5sNTJm/TWitUzWasZZ/sI8Sp882XjSWhmzo4xMMAmCIAiCkE8knDC5eSYnwxABxLBrnNhcDz3AiuKQcgcdGAmGtOwsIwiCIAhCJSKbmMj 14o07lhItoubaPBHYWfQ/hY2ABRDMZDSysgmv4IgCIIgVMZO3ViRwUkziOUYc0iTEyq2yARTQoIhDdIywSQIgiAIQi7MZE9hMtv7uiOZjBVNtIRp DQkxhhH213xoACYgwz8mSZRzwiCIAiCkI/TyrBbr0Se Uw03WT2m9kCypHEBJM5n0lrrUUrIwiCIAhCLgkDmUgNYm6SU8cwcbzh75BJWMnk7yvjn7tE8eEKgiAIgiAISYjtJjIA2KhBwNHEkzvRgLElVmIjWsFkfphrItoiQQuCIAiCMPIgax8Dp5Wx28cQsVmKze48poasxAagGMSkoAKQ4vim/RO58w1l5HBsQRAEQRByiQ6/NkKFkVjYKmbMtBPZffKGyew3OXcUm/36d VkbEEQBEEQcjHaF7jTI 1J2NERTEYzYs7ObtwsD8GEyQACChUrQAFKgRKLsUUZIwiCIAhCZZjBxi7GiQ9mEbY7 YiIQMzUMJtfINqzxkYgca38U7hlDbYgCIIgCJUhM5 DyLQ2OhrbqmVgdppptOGtJ6Xo6A9Tdos8QRAEQRCEYtiZxzBTZC4TyTHsRBvmxk/15EosSoH8eSVGvFGeIAiCIAhCCivI2OvogmJrYDJnLzVQlohWKSlmMlYy7jq5GFsQBEEQBKEyHG/uy w2k4m3 2UCMw2DSsaLQWLBtcrZqw8Y1ggIgiAIgjByIW/rOyKym8rYqSVYW5lhFiR8oSX/ZGxZyiQIgiAIQi5MTudCYDZnSlpLGSL2N8kb9pgww4oyitjEg xqcGiZchIEQRAEIY9oE1 77S TWZ/N9uwC4uE6NyCramEmFR9WQPHmM2I9IwiCIAhCAVZwgTsI2x28xNHs0jDJEfkrmPwfkUAjCIIgCIJQBJsTI91ZSwQyqhlE 8s0Njhn1MtcTp2SjUiUcS7k9CVBEARBEKphpnAAYy/jL70mbvzmeKiobVGREBPFTZYvCYIgCIJQDNntYzIaGDZ75TVekmFCABBRACgr17Am1khNMEHWLgmCIAiCUA2COVUy1n7YjfKYMDxyREI cioYu69MImaRHCMCjSAIgiAI VjVSzST5DbKi7aVaTAERVZK0ZGtDBM0GNCeKMPQmpk1MEwSlSAIgiAIIxullJFizDIlMjKN20 msYKMUoG7IJg1Us5ixjedsaKMWyDO9lqJMCMIgiAIQhKi1rHjerp7jCBDZtG12R v0RYymql94mT7g 3EEUEBioyU4sJT/hJtIrKTUbKtjCAIgiAISZRSs3eY37m6s7evxy18dkuliRs5p6PCnr7ygr32MwKJAimnhVFWKxPvMRMC3rmWsL Ga2sbQRAEQRBGLEEQTJy83S4L9nnqsWUb1q/TWrtF0Gar3/h/d7ij/5CR cdtBpO4Vkq1T5r8hkMPnTJ1uhFQlCIiKIJSADRYA5ooAMDMIVJHLzFFahxBEARBEASfMAwnTOxYtH87azOr5GaWONKMsFnXlFzLZFUp8Q/7nIi8ZUeRIUxySXWglFKklFLkzGU8lUto/rHHQTGIQIqgcduvH5u 3QVvO kjw5APgiAIgiCMVIJABUHTlgnrD1dcsHMwJwxUiYIApKACEJH937gJI9fM5oAoUiAmJTNMgiAIgiC86pSCMAzCIAjCIFBEREZBE6lvEOw cYdIB8TurmYG8K 7niu1rpy/YL9XMQGCIAiCIGyb/OGKC8ataWsulZrDsKlUaiqVmsIwDAIVUBiEBEWkmNhqZUgRa7bCjFHMgANSvz7/78aBzDQJgiAIgrBl MMVFwAYv7atqanUXCo1lUqlIAiVsZkhRYrdUqYAFAKaEDAzQIqU5jLARKyAMpMi9evz/65lQZMgCIIgCFuKsatHl8KwVGpqCsOmMCwFQVgKSZGRZQIExIqgrX3wO cfASi7DAoMYmbWrDWYGWVmBmvWzKyZGdousLJhMezxBxTdM1Y2nNhkL30eN5zhMoMVomPCEwcmKCYA2u6JnF5RFRSuXtcAQIELJXLnrdLKRCU2hPYPk0g5ZEVEIA2zft5ZWUfeps4VV8bfOHhWBMXQxgdSsFv9mCMrwNrulhjHizIHlXP6zKxcGO4MDPOX2y0IditGECUPrEgmNRWGzYlkhlDBddaNNWQHewHFB2cw2fJEioyIrbTnyGRs3qdORZLyIme ETNnD KInAA2U8y3SIRFZufrIHVH2a gY2 ZSaWyNJUZyL1BRATthWtyRkWOydYdz3NKAyWhPH8U UxPTLfn3kaDNNgOwWEXn7ffs57BdLe03aeJa4dq4UI/oI3rsUlSpTfdIhupveyobEYxN/ZO/F6Ymil6pHJjbsNkF3NdHEOFm2Co6TIXhH/ au LQlPGoWsoUQyXQpMJgydTx3PWnUfgKaiMiLtFn3YeOWt9mpecjMKvMdNYy5pD0okMhrHGPHcb0gZZaKAIBSpuhqIqJAkXImDURQSilQECgiBEQqIEVMrIzdg1K2nmpi19tAsy6XoWH7HzCX3cJeZmh7DQDaXQAAvOquAFfEvJY1UXqTeRp7QqlsJ1PrXX8E8ouJyyX7xRNtEQOU31uZxim1zCf7rc0X1HFf4OoVp/qLlO p/sgSJIMDiImZke1rbCozZEpUutJ5HSoRrKKEvIpgDVhAWa9ASpEpOkqpplCFQVBSpTAMzexSEAahUiUVhkGgVEiAUlBEUGQmmDQBTExsj1EgIsXQxIHNw4CJiTUzgfxTLz0RwMueVCXJObTSNakMBMbi2KXKy1AFIMg25Z4vecbJgeeJ27w4 6prZcw1qUxL6hdlJsT5HsA1fy7RUVVPxN/V79hbBQYQIHBeproEhbgI6NTTXMzieVt17Z6LaRcATI QLm95bXR8Lldy00byux3jralE7ESB2Kes OWJC2zjA7gvzirusdxe2Mqropwq7p704CchEh0IMFJFbtcYhaUJlKpKftNvvYvLj5FdmcvkZCuydaegiTQ5nypT6UqfKtvZKgDbbTjR064xjDoYgiKlWYMoJeZGXV0kinm puPMzMaAzusGKI6Q8zAlW QttvTSZcUa 1f0NZSKBSYXY0 MsEs64xWVKf 9Y JMAivVFEq12kR KMmXPIfpEudyxP aKvl980QlSgeQiR7F0pDZBwMAcZBxlnnTBRP742RYUoq8Psx9KWZm5fVC7Ja7ktvYLNsCs/ TOM55JyBq8xHJekxgUla0piCAMcskMv wIhUGBFAYkCKQUmEAIFBxiLoMrcumtOgBTSXmsmbWKEOzRsjQzOUy4PYkKSPauiSvhzCijKkzsfieFGX84hG/qZOiDMX1S0e30kMEsmuD2feIfBHEQ5upEdPQczos32f/EfvxJMAcP1TcU3DGK9OmEcdynnFoOxGk3WfJEWWKKpKO10vbveyScgER234hugHFTppRKghUKQwDFZTCoCkIwyAIVRDY2SUyQzAjz5G/ggm2/yIzntJg5boec19ZAY6hvEXkLvqpU74rd8PuqYLp68kUnUyexbmbU1CJyJdVUwM7ZlZxW5oKN8enqPH07kZ qdid9ywSmNLii3 tOIqb8tpCb/QcNZSmaTY/VMq3vFj7HnkdcCqxpK3GyEtapFSCOU0jueMzRee222RaBQR7BS4SZcgVRxt dpxgBUHv2hNl3OQmbFQZge1TGQArMyHq5VsmA2B6WXeHirONlILdm5JcK2z NqKPTRCiTaPyJi84LZbVJ7blJFPRm0yotKtJGCaYmtL2xPGHGOyBMr7DZQSR9sF05E2sRBp/QTNhtNk5vUEKSl9tRbRfFPjR0ZXjFKuIvFXE OTQZBTBRpawIbGmC7CvOZzIA 5Xe6lOeLMrEoGYkutnOyGgdONfPuo8QRKUgWPDe5g LinjIvkqaMJV6ppDHNi1D8lk11Mjgiq0tQHKdR2/wg8hu RLMW1wUC SKjsr0ESJEZ IJApIwW2Y34KAhCJigjtShiRYEKSBECUiqggEgFUOQmCACAAzLTAGAgYK01Aq2ZUWYwQ2utmUI7bwCYbdKcbOHvjmbv2JZNKRv/7LdIfqyYbH9kNsv3NZpJnVbsh/YLHUVjj1Rpofg1KxvaXjUju8ffUTk5P9K7s8opVzEFokxURnJeKBaqXLJz7hWU ViUcW14skYTsZXlYn8UzCDTyDIqNEuWlAqgAqUiUQamS1VxsY9FmUjFwCBiVlAa2tgGM0Mxmc3zQHb/Gz jlCKj TMdIYNVnmIzk/JYIlN5okzOdaqptbftyJXdl2BmUmTH3jYkNiHE1Sal CXTn QXIyBulYkALgGJZtTrqV3XaEubNmIjyEoVCf/93QjJxFMxgWyKOJMPfnrtLoeAFbby2konfZN2TaRCesolNTmTWoivGVCBYpc55IkOtgCouBGxIoLR zqtA9ksSDaysTImagZ09C5bzR6lvleqa0xNQChbVdITmuTaaGbWBOXUNgHF6WeKRbqo9bE/lSeuUfSVTUw8DVOUn 7bJb5vMjIAgICZyR2/lhncBKBYPPHEZbg0aqKAiMqsFamsitIXgLwOHRlRhuDGIuR1/lHWm6lP61iZ0m6a7DLZ3tBqYVOfI/I2MfHklTbFyut9rSjjj48i3 Lm3Pztib/wHyGWo6KPTuxV9kQLoJVpOb38YbBycneUXos/JvbuV9C9pZp4v/Sa72iacmSlWO2JJlHXnJoptQFrogCemMLQBCijjVMcpZ28VkLbbiOhF3S5a71yX4tikStqNolIMxGxMp6bTcuYQDCdawCljGKGiNxkU6BUqJgoCMy6k9CUMVeI2B6ko1mzpoC5rM0RxwhYs51gIm26cm1lHq2dxtdlc6QHMN Mc6TO3G/k560vytivZgcwYZyfXstv67ypXTrPf3Kl3EUkaqRIpctJNqoKcZnXXuPrDxET2h2j 9R ufL zgslrryUI1HFFExZ5l07UcaJy wNqxCLyNo/C9IUFzOMDZQKgkCpoBSECqQUBYoCZfPLNVDaDIcSWhkCsVP5EFipgJmVkblBLjONhTCQUMqQayPZKcEKMiKBBhB4VSuVZy51yHbnTFCIVHymIHkzklGzn 4ecuKWLcqVdDMUixH ICYOOdna2rbePHL6jzjETFfnRJm4O8wTZVxrGjXKOo5Jwp2tNxoI3By8cnJeThpNuCpxKJgyHtgRmIuzr2xlX0PgVVdNcTxVRpRh9zuOtucGAUWNpu8mO8r3CRD4okyiAzNZqkhHs7aEwKve0SQZEQGcKA2UMJiJ8oWIiK2li5f5prrGzWvOd/ElbE USRYFBQpzumr7y8zCKa11EJbgvktSwZbQJnplL5F9iojZZJrJLtdSemXaLyKICrTTmjDHo7 U0GB/shHuregTPaWy/3ETCvwigcCOlyLVXdyDJfKH/VKd/Aqeb3F6XYn1HdjRml9b4wwpEGWikaIzp/NTkSi9ymQxMVFi8GyD83LGk71SKkDNzEQhKQVWsWaFNJw1ofa0lMpowY1Ab0UZv9f3grMdj/eTEsMDikQZYiIiskK5Um40oUBKQVEYhiYKym07T0GglGLFFAS2wVEKMGkJoFkrTVoxmImhNYOt3YyZpDCaeNZaa9ZxGUhG0G9VFDP7w8iq7T8Qz2tTZKtXTrv3BXAAgVJlMDOTm6KP9K/WuTL5BvhyjC0DcdhZNTmASBy3bSxHY9RYAwriuLwlZ8MQVRDffVE3TXHPlX2YsSJKMV17KtC2VtEpUQZWyscjTE8X6 oEApUkFAKrA/ySjXo8hF2RVGcpvrbMicCMVMYGvpymCQMnJllMsMKKOoZV8HYwSfTOXPJ05YgLTGwndTNMGkOB5VmJ5aJSwGFBFpM9b3GoIiG5FIBWasyCL3KhKrAWOLYz M7TjjwJxviNxHVh/u0wBcTlUG J8/6skjASgnT4LMW35rqrw4cOQ 6leYWTFMlUh19oEToTy7bpBREBAZMchXq/qjOdMZh5m8MrPOvsrAaQuyuhP/mvy7RAkrDX98kxh4UBDLTGTROtE7BgDshKaNhykPZb/zI79CpjQNNleVlXacUOuGzNHMG1y/n0yjib92KSIrEdn8DNLdVUZN6EQZa/THgf0ICraqej4ovzH1dE6RgBtFyVee 5otU6m8YSZR lskahYQDYpNTQyICFw2BS ISoKtpiEy/gTMHKbM0qP4M6sgSBYUzwYioV2MohMNR/NlI7vkITCWef5Tr8g6y5ioElXWykS2X TEOGREGbhuDJ4QEseTvL990gbmbhThJmqJKCA2Sk0/sczsarcvles4RdbsncgbqEQVwQpopk/1057orXUYhmyEhsBpYwLTYNqDc4yhTBAE7Dafhw0latNYa8VkbYBZKWvwC8Wm0WUj5ChWzE6Fx2x3dU13IuanyQ4VfYhknUqq/KyHirycMXc4/bo/qCOO25OERxTlv81CfxUBORGkQHCP7kTiOIHKVntoBhhJFVT0ujLtfEYqymqnvNJoHVNU nJsh61O2p/096Zu/SRosv2jlXoj8SvpzPPfmJOTUsZH2/napddmCp4CApGy1hgEcBkAQSVtZWwA5kwFQmRSSkSaoyG0/TBxXXMlMvsZcmUTINmDFsjISQpEGe na4bjIZFxw24aS/kCV15xYfcRmRImo5SRfghESmk7ERvrWvwy7seLElmUtV2Io5SyoeHiPExF3vvlK/E8S4Joto2MRiFKif m32G5xMSmpoo5T vmelfv3VgaMrcDr/9LrZ9KeZNOUfbCfQ6VFMWiJ6Edr0QNZbqOEZEmaK0DIwfY0Y5nBh6V9YwkBIAUG3Ewuu XATND4ip8umxHc2rs9UkUia1u1U/cgGZsQaJug5Jru6KwtNZRv5POHOMlTAto21Rv BgQ2TUVLtNUFG3lCaxIFtrITY4oY4SAIJ7UtFpYihtKP5JGZeiv PAmghHFIe4YEt2Gn29x9KL1lbkdRmrFpVeiOCoAZMqJjmNL3tC5qIbaFYje4Mr0Pr4ow4qVIq2TpqJEQDqHM56b 4HVN3j2fMpaNHIsPZmUwsgGQdKbyqKMa/CVVk59xSru4XxRxmllQiIjOdiX7WommJVKBDIzBIqI2Nut1X4Is9W8ZieRMZc1CNoZaGpdVrDzkLrsiTLZIUd jhVep0SZlAOvQYtaRtvSEZH2NCKJOHgTfzlPzR2VfpR1o7yy7VYm5Ghlotdt 5PqyVxYRNC2MCOhErSOkvYHeaIMsY6yxYgyRpDzVUpEXAYrBgVRj1Bg82qxogxcy0Wu/FGKPGPnHFEGTpqJ2g6kbUg0PDk6ihB5HZhdkqcCAFweMEmNn2ZzL6N6Qlahaokqms1DO6lh/LFzB/GqDWPbTqkVBy7OXpL9lSQmN41/Vv fXbgYqsisTJWtyo8yYSWKMhE5y4w407JRsobWkTSWLI9RthTkj18fAsA28aTi2qgQC3lxxMisrCTmciIy8fKuuGD5dSdSGxJRGWW22mWltY6bRQKc/1FnR0TaW95Mfnfiqq5SSns2VQlrg5zEm7G1N8j1L/wODKAgtKpURQACT/Ao21YKRGSGlenFxp6eiYjKZu2GqwRRDFMRMD6y1kS5K8qIjLBoO2wmJ5KwF3PzDwWxpVRUZsiawkXKQhXF2ZtqNPW0TGTHLH7uueJpu2HTlZjOLxJTckusiZk1Xbc54JVz4yNzVMascKIyTZttFGMNYtaNit53adQ8oNxslxGhmDx9g aAVHJNSjwJGOn2/ErqC JhGLKXnS6DYKxJC qgedkuk84ZsTgZzsSTlNHU moDjuOf63d8P2BmFRAA0myk8 hFnekmzbUrvQHH5tWxKBPlkVLK6b1seQvCgLkMImPnpE387SukFLGTWZR1QorMihOrmIHZ3IyhksZwICOgmK9CxKy1NnaXrhgwM4cqYNYUKGYOTDWz89zJWl8pxzIiuBNeo0d2qjGt50v7A7ciVWcWMxcFZy58expjb5QQAjg9zeQL3FF9YGabsX64do7ClO2EJ0BsWxMEcDYxGVsiWzbzF2m7BkObpo4jG0rXCoHin6FrY1LSgodnsOHuUJRXVlw2bZaZiORcOYYY/x9FFlDuA2ORZQAAAABJRU5ErkJggg==[/IMG][IMG]http://ubuntuforums.org/;base64,iVBORw0KGgoAAAANSUhEUgAAApkAAAH0CAIAAAD5T6EcAAAAA3NCSVQICAjb4U/gAAAAGXRFWHRTb2Z0d2FyZQBnbm9tZS1zY3JlZW5zaG907wO/PgAAIABJREFUeJzsnXd4FEUbwN Z3b279N4boYfQe5cqXTqISLWBClhQlA9RVBRQFMWGqICAgkqV3kmAEHpCSOgE0ntP7rbMfH/cJbkkd5dGjfN77kl2Z6e8M7O778w7MzvoekzU10s/SMsjwGAwGAwG40nDzQ7zoiwBACHKoxaGwWAwGAxGDcBo5tSRSZk6c9c5njM zcjMzEjPKCzQKoRgjABAURRFUWRZluXKWwM8z/E8z3Ecx3G1DEsI5TC2ttG4uLq4ODsb 1SqEBuDwWAwGHUGHgAUC51yBen/S5J06/ZtSZKBAgWKEBBKEQDHcTzPazQaQBQospQUoggwQggA9H95ngcASikFUt2wlFIA0GrFuLiE5OSUBvXrC4JgEJnZGBgMBoPxX4IHAEIsDJYrAJCTk3v3bhwvCEQhNgI/u1 79i2D6zUOoopy 2rU cjo749HFioUIQRAzcSDOMzZ2to9N HZVm1aNw9uDgBRV6IiLl76489N fl5ikJqHFaWSFRUTECAn4ODfWXZKYbKuem5hQR4W0dXG1yrq5ZPq0jNQj24eBgMBoPx5IBmTh15JynX3GWMsSwr167d4DlOoaSLt8PiMb09GzXlXLyQrTMQmeSky2kJyTdiFuw4eTa1ECFsSiUjlUrVoX37jz/52NfXp9y1 PiEhR8sPHvunCiKtQkrSVKTJo14nqtcl1Mlv8Bl4lfvDHSA E2L5h3R2lvhGl49XICJm9lTo7CUyNoinVYnKcAhogDPqzVW1hoOV5pi1TERD9Ll5ORKgFQ2LvaCRdMHg8FgMJ5U9P1ys0ZpSmlqaprGSi3LSgdH1feDm6udbDggmIhIKgBCgCo8Bx7O9t/1bzxjd9TlfEAYYVSqigglPMd36Nhh1Y8/YYwpKa tfby9V6/ZWZM86eOSsrco3DcjxOTU3z8HCjtHJdTo1iolQhxjFX7yqxeKoPS4moK AD jw7YECXZn42AKDk3I0OPbR/W0gisVOpwGKKVaeC5Nps2uz9799pCiTqp2lf3lTb8UydMxgMRt2DBwBFMav8ZFkkROEwZ6XGC1vZCUTLUQlb22BKoDALCOEQQjZ2FCQC0oJm1tMvaiXEYw4jQAD6sXVwcnL6aOFChMCclkUIPlq4cMrUaVlZWYCgxmEJUbRarX4Y3hLUWOUB1RVlFhIKWKVRWak4BBavIqQRktfNmbMOAJDKWgNandmYgVBFIVSUSL2nP3x3cOPc6P0712 Ky5HUToEtOw1 YW6fTlsWfn0iXSWUidMKKYpUkKOVADhra1sBIVD0p7y1tQ1PtXlFOgqcWi0QSSdZkI0UFpY2jKhUlJnJWdtpVJhIWkkryQoBQFgQBCsNjxEAJUV5RToKWK1WKZJOpipbaysOFG1hno4CFuzsVGVmQjIYDAbj8aCS8XJZUdRqDULiWA/qa4M5uajI1uVodFJgvYAWDgoAjcrl79xNe8rVUxUb5WeHR3lx27PUCKGSGWo8z48dM8bL05NaNH17eXqOHTNmw8aNsixbCKvV6k6FnUYYdenUSaNRVwwrKwrGlRmojTr42MpvwCsvjuvmY61NOvX3 lVHkpEAlq KsteUbwx27HcOZBv3dMs1OCglRCZFNu3ee2ewa/hvr/12MV2igBBFKCri/KHDXWbNH/v c/Fvr79TgH2M46SowVtrXu ogls/z/9feBGA4fT6j 8tPOsy9ft3BjpA0t6/Tnn2GtLGXWNGtrn7hbEr5o92AwDAzWf8vhEA7v44a3lIgXO7EaPHPdXM34GDorTIkD1r/7mYjrAse03Wx7xrY4j30yPauuUfWDZnfaL3hE/WDHaCjEPvvPNvmkpgg/AMBoPxuKHvl5u1sWPgeIFSSls4yJhDGCS MFOXS3fuuCA 3R A7j9wqFFgPd4GOEw5gW/pIO3OFzDGJfpYEFTNg5tRSjIyMk Hnw0ODqoX4F8Sf zde1FXYrp06uDi4tw8uJlarcFYrBhW7zk/P//QkWNXr14HgOzs7H59etna2uovlYTFgC1kp5jS3rP38OlTxfwcEUDj1XXSLJyx6JsILaAqXdXHRC2dElHHNXl RIv0Pe uuZjt2mXO3Ge7eeDMqPNZTdqp/lr08Q/nv35jWOcdK47mlwlVEgkFAKJQ4/H64gOvQeOevhN9LdamVT1zsklZcUk5bl4OAEDzkpMLiS4lnzp0ef292W01QLNvxWRZNwhsOWDKZ57cG1 fyS5OxWvoxPEg5eUXSQpQVNZqrygVrf9UIZJCKGCex1zx9ABZphyPmUmfwWAwHgKV9MsFQQ0KAkBN7RSEMUKgSYweEtBSFD03rF HEGrXps0Qf8EqLpJwGHNcEzuOFwSMMYcxACiEqNWqRg0bUkIEnk9OSb1x61afXj2bNwsCgKjomCPHQuxs7QSep4Q0athQrVZRoBXDAkBGZube/YeSU1J79 oBACEnwvLy8gcN6KdfXF4SFiMkSWaXyxdjZAlP2jdvwa7b1P/Zz94d7WnV ZnWay ezOaqdhX069wtnCoSH9C3nSZ6TUic4jLo1ee62Ub/ d1p0m38RAHigORePXlJN7OTv pwtHEoCsVqlRJqbnY/vblp3scnUqnzoEUfv1DfhGyIZhxc/lXWB1 80xTIlY3vLrlcBCAEjPq2rQYgY8fCxetv63jvAV9 8Yxvq8GDfc5uSCoOmX9fvrTmcSTsPzCGsTr0XGuNDUZB1QWuFeUWTkGNTt6Y7 dtrkyNPh4bfzCAbgXNt2drwdfrtQ3y5jMBgMxoOkkqFlQRA4HmOMKC0CqtcrVFOU5enqIep0AODp6qwR0wAoIACEEAKVSuA4Tj FjVDCC7xCRFkWraxUQwf3P3Do6P6Dhwvy8wHgRFi4p4f70/16W1mpZFlUiMgLvBpoxbC5eXnbduwqKCjs36dns6AmAKBWCcdCTm7buWvU8CH2dnYlYYFCFXR5KalnLtyTsQCJp89ljh7qDB6B7tyJrKpdrQIU23n7qTPD44qoTZPOgZC0ZevO8GR6x7lnmxEAAEphlha5W/PInMKmZifBpUTeykZYhXJiLmdAfRdTsiHO2CCOsJpDVv4NXAEAXIZ/8tXw0mvOjb00UKzLs8IOX8gBjYYDSoGnmSc2fnqcAkIqoXw/m8jg czc5aN99e59B4/QJdkii6Nmnqn7Z55slbwObOMxgMxoOnEl2OERJUGgDxthZ7KAqRZXAICNW57zt8tEevPpTSvYeO8P379HAQadJtSsgtLa/RaDAqtbEjjG7cuNm2TUsAsLezGjSg1/HQ08dCTwJA40b1n rR2cbaSpZ1AHDjxk19I6BiWK220N3NJahHZz9fb0URAaBJ40Bra3XM1RtabaG1laokrCSK1co/BbCgbSxfrQoEcxwQSQYEPAcgiwoFQIqoAHAAWOMeYKdLyhTNaWzMYaBAOZVVhYrCPNa3oHBNhrBzzx8 nyyVnMrJqUpJe6IgU0sQwlBp5imlgr191oFfNm8Ni9M5Bnbq/dTAHi3btiUZMcdXrg3P4RGbK8dgMBgPgUp0OUVUo7ECCjclTUexSJbkXCufiMj4zt17DgryBABBUJ /Ftu0XYCjfJPIyi1Jo1FrwDD1DSgFSujNGzdbtQjSR6hRCX16drG1tkIIdWjXShB4RTaolJs3bvKcgAQTYR3sbPr26goAJZ4BwNvTzdvTTe9YElasTqccADw6tPbdsecO HZu7wwAkHInTUHAVelqFUA0Py2NODXyUJGY Oh0GN67R4tzIbRPz3oASXYB/aaMCc48Nf 2xJXXmro8HYAKHLztkZJn27R9/Qr62r1jW78d/94G/y5tnczLRhWZAiCsUvOU5imUxN3OgHougPPO710XWUiBArYNbNuYpoilmtvIGEAV7Nx9wovdXGhq K9rwzOxcdcccYJ0c PqqwA8hyDzVshfN49uIoQCwkgQMMfs6wwGg/FQqESXS6KoVquAwgmF61MU76MhTrlxz3dvba1CVlnxAHRIE8/C i4O8ZE6maRo6UnirlKpkNELnxJ6NPRU924dXV0MX03HCDp3aKW/WKKb0zMyj4aeUqsrCWsS47BZmdXrl4P34GU/9cgBOwcVAGjD/72UjY1UkOWrlYN47d3Q69yrw1o5R4XvXBPa8Z0 /1veB3Li0wh4PTP9uduh336xO658/xdxUurFm2LfNiq3oXOWNc1ybOhtUzFuzwFLf xqWTaE5IzYLGjuDI2nrvhyYGbiqRXfH910qdtrrW17vbuoYcyddLDzaeDnpor97tWIe1LFNIBSovFu0jLICdzvqk0YKhDiwPDtXIx4jHhg89wZDAbjYVOJLhdFsahIa29vV1TEbdB6vSllodw828QrnJWtolIBgJB2z64oX8zPlySyNs9DZWcLxZ9M10MplWV53ca/5sycbm4iFKV03ca/MEY8L9QmbG5unlhNG3vijt8OuA0c19UOtCmnt6z76VIhh0GmVbpaFTCXf 7v45mLnn1zUPyneza9 fKRAE8uIz7XysdVXZSTnJZDOI5DUO7bMBxfdGHN7/vsJwxsYOPtknRw3T/ez41pKVRDckPqPInf9/fephMHNrS19/SyVzmraXbIt0u0I0aO7tWsXlAzX5ByEm eOn/ipmj5g/gMBoPBeHxBM6eOvHwj0YIPjHGDho0RQjqdtgEunOSpuLm4cDa2SKVGCBFRR7QF6RnZ6xJoPO/IcVxFpUsIKSws8vf1nDD2GRdnp3JXMzKz/vx75734ZGtrq4pLw6seVlHIrZvXq/QxdgAAKukUmQLiOZ4SWaEUIY7HgsEuXKWrmOfVfKWnQGTOve Ln0wOKjy//6/956Pj8xRbj6btuo0c1vDG8sW/3pYFUIq4oLnfvdZZA7d /d//QvMFDoBSSdQbyBHPISITAoAFDmO/qV8XryDfnaYQy7IBUCpJRNY3FhBWqzEGUGRFlvVL/RBCgDkk8BhVDKuvAlnWyaVhGQwGg/G4Udkn0gAIIYkJcfUC66vVDgmi5ss0qY9OW89O8bHTAEaJebo7edLxfHtqo7EqXlZeEZVKlZKW9cWKn7t0bFMvwMff1wsA7sUnxd5NCDtzUVCpHR0dzH3jpSphFUWJu3e3yoocAJCg5os7uhwv1PhqpaeAeSX18Kq3EnpPmTjw9fkDDa5y oU9W3felTkgmmbD54zt1l4DAClnrxcYihCVjYfXFw6VjHreCHMalWXZABASVFy5HHA8x5mo QphDfLzFWfeMRgMBuPxoUov6YKCgqsx0fUCA11dXSVJDlGUY5mEpBOMMcY2HMdp7HlU7tunFbCy0oiidCEyJuxshCRJACAIglqtcnJ2VqmE2oRNT0 PvXOnCp IeWRgHgqvH/n2f4d/dHD3cbPldFnxcRlazAk8QhSpvYPb17OGwsSQTWv2pBCuwkQ4BoPBYDAsULmN3Rg7Ozt3D08HBweNRlP5p1JNQSkYd93LnVY9LCGkqEibm5uTmpKcl5dXA0keCZQaVowjo3lqVJG1EgAgTigxlVuKw6QlnMFgMBj/WaqnDfLy8p4gxfkYUvyh rKOHG9VnXVuJi3hDAaDwfjPwiYzMRgMBoPxZMN0OYPBYDAYTzZMlzMYDAaD8WTDdDmDwWAwGE82TJczGAwGg/FkY/brLgwGg8FgMJ4IqrdVCIPBYDAYjMcN1i9nMBgMBuPJhulyBoPBYDCebDDT5AwGg8FgPNFUuV Onfp/uHzpIHeu3PEDRdP0je8/n9lY9UBSfGi5eHDUJgsPIvu8 /DFyxf3dX5kqyPqQJ0yGAxG9eFNqHJk02neZ683MnLJC/t43q7EiLPnErQW9zOrMhWTAEj8Z/H8valmNjuTSlPHrgM/fP pU58t2J9R6c5oPd/7aqr4 xsrLuWW7oaqajhxwYfBYe9/FHo/c2SKhb9 08iEc/a jz/deFe6HylIDzoL8DByYQpk02ne4lcKVr22MqbI4KRq9vIn77ltnf15eHbV97ZlMBiM/wC8mX45VW5s fzPWFF/IucnSfm67Zuu3M kyyQBQHRZGWZf0ST/So1Sv3T4BrzYs6V9xInsYn2n8evd0T5 7/kkMT/ PueoPKsWfWmNAEBVf8zMqc7Hlv8SkUMAQMpOki2GwzwPslwFfVXTYqkWNc0Fg8FgMB4S5nQ5kIL0e3fjikrOsVP/Dxf0O7PURNdZ5dpp5LhxvZq4q6Ag4dK/G/7ae72gKh2n8kno07FtOGz6hOGtXIX8e0e3nRYAdPrUP9Cnntti9vyJvhyMW7h2HEBB KTZf1hIIi86JFJ5qX9rx1PHsvQiWTXs0d467u9z6UppnKmK6VwUWreZ8fXE1M/nb7ktYseus799wfvs8oUro7Vg3fztL57N/vrjX2 KFlJPuRenLyCrPIXaZN69G5dF9AnNLF9cvPvwRfO6XNoVHfhUzyaOmbvXhLeb3D78j9P1hjzTygVnXNny0/ojSodpLw7p7K3JvX7wh 93X8mnYJwF3n34onmdz225ENCnXzM3jS4 ZP1v685kyMD79p0wvX/zRm4aIPl3wvf uuHk3er05E3lgvftO2HWTNNxYrsmo98eMKSZE8q9c/iP3/84mykjtW/3US N6ljfHgMpTLy0d8WqkNq2BCq963j34YvmdY3YE1O/R0d/Oytd3FG9MLVLlsFgMB5DTNnYqwW2bjFx9ksBl9d9vSUmS/DvMmrGG1NyF/wYmlkjuy 27/LiK6Pdz6/65MfrJGDwC NbasipMj60l779bGOVbey04NbBi9p5vVq7hR5NUQCQTVDvYNXNvy9klm1smMnFyXtRKbZdmzpyt1MFv1YeVOQCW7gK0fHYK6geSlibVH0Ls7niygUA3qdf 4iVK2Z8mctZeQxsx/v2H i1bfOiLXKj4dOnzn65dXrO c3f7ijyGTJz4ivDL7 z8a6ufOy8b7 OZ7755tVvtK7dpn48bdyVq6tO52KOJh3fcGxVUj7n2nTQlDFvjUl4d8OdCmGrlw3zcfK gwYkbt4wb22 R9dxs16ZUZC0bJuu04xJzRLWf/tDVIZi7VY/UFNb07y5Yswu54/37t/u3Bdfvn5d69h23IevvFKQ9MWWeKbNGQxGXYNHYFKZI6H1jJ9/NZwkb//s/d2mO6DYocXIjtLeT7eGJigAkL57864O7/RtZhd6IreypMskAVB4aumHqzJbDQwWQ77cdjJWB5C aX39Du 3rX6mjNHePHYx972unT1CdyTK2K5xv2Yo5rfobFLm87XmcnEy/PaVnGdaB1rtzXJq4V90am9cqzaBjjiJa9zINjn0blG12ytmEzoNAFB0Ycf2qGwZQNYpAFB0ecu6I9eKABJ3nhq8qFfhul/2RRVQSN5 oHfnHo2cuLvJFdLPDd x53qeApBy7njU KmtvfjTueLdI4fu6i9nhP3xZ3DHyW18/rpzu1YazUycBABAvrpj3bGbuQRSdm/c0u6Dob1994c42yoZ0VdiU7IoZOWmJ1QxlXJ3CAAA3AawUIynykehvbhz9/V8ApB5afeWuwvH9fbdsj62xtlmMBiMx5OqjJcTXVa6AvYmwwuuDTxVro0 /mqEkWOKiy1Apbq87Hg5lXNTZCHAz4Wm7Iw3dBp1idfi5XbVyY4JdHdPhWV2faqz6tSfYtegSR6G iyw8BmMsFltIj7yg9WnpZ3fIK0iRsOXfFs2 bejYRQgvn7JjbOdWfgWU2IZABlIzYDKMWk5JxJ11fEKQop0jOvp2iowAApDBHB2prNQYob5eQcxJzDV1eosuVeHcNBkD2Qf2njn qrZ tYXa3GGFd24nmZuIkAEBSryUaypfk3bqdb vvxiWfPRrf48WlHz51Kfry5YhT4dcNWamEcjMqVPXHzJyiAbBUjOVGbJT02xmGm4kUJtwrtA1wA4itaa4ZDAbjMcWsjb3CeLmZCBAgcvfnuStCq6/ZKo6XqxEAlZXS97yi1H7Gsph4/GTGwG6d/PYcq987UHvpp2sFFRSJ2Vzg Igk9fCm9Rr4uqZeuJseF5U3qHWgn Ar39qVXhNDsbmEeHcASmRqJBklpNgPpQBQegYAZqqNGkcACAHCdi1fmjXA/uCv85ffTM4XhUaTVsxR1XZcpbpxSgk7Pl9wvlmrti2CWo94ddSwsGUf/XW5CnMqyt4hKqs8BTT6nJkpRuxUNgKEuZKSQhizpWoMBqNuUtvvvknpd1LAq1MTm/uypFjKiM8ElwbOhncu7 jnoarYgSMKhers8KYkhZ2Kd2zXr12nvgEFZ4/GFlXwYT4XpCA2Jt2xZc/uXjnR9/LEjCt3UFDPbk2FpIvxNVHl97e4qgLnHOjPxe09GJOYJxKK7f29bGudtsU4sXsTb0P2sH2D rb599K1BIAUxUed3vnnmk8/Whdt3 Ypf742AlS5GLF7U1 DJ86hUUOr/HvptUmXwWAwHk9qu7cKyY7Ycqqo1bTpYzvV83Rx9gps1nf06H7eVeoAYRtX/wC/QMPP19dZDZkRe6/a9RvT2VuFkMqjheHiaSLErPVFybNfR1srW1UVUlISXt4pE4m56TB/llnz96z8SsLwu5kDOuXy9y79aMuxWdKYOYEJni1CbYKSPmTmFNLAa1Ka6aoeQmplH39k0dOEBq707PDfN50HHyTYdPfqq h7NHi8ETRvulHjseR/17PTuoXVMfZydH1watW/ri3PgajE8YUfVi5BsPm9KrgYezR8shz47ySTt2PK426TIYDMbjidk1aVWFFF5ev2JFzuhxz7851BpAzLkTdXprRSO2CRDXaMyChaXn aEr3lh7J2z1arcXJyz6driUn3k19HB0sz4VAmqjdxy49tqYT798ttI1acVCZp4/Evv8tPppJ8LjTM7hs5ALKfXiXblXs4RLSSIALbx7JRkaO1y/nlGzuWM1L64aQrIu/LK 4awpH/w8RZefcePInsgmwx5onHL8vgPp7acte94e5987vOrn7fdk8JKd2g55a7SLFQIp83bIml/21nJFWlWLUY7fdzC13dRlE42EYTAYjDoHmj/7 ZDzNx61GAzG/YZ3H75oXscjiz84nMk E8dgMOo2bP9yBoPBYDCebLC5GdEMBoPBYDCeCGr93TcG4/FETt3xv7d3PGopGAwG4yFQ2zVpDAaDwWAwHi1MlzMYDAaD8WSDmSZnMBgMBuOJhvXLGQwGg8F4smG6nMFgMBiMJxseIdi1/e9HLQaDwXiAFORlZaXG67QFZXffYTAYTzAIIbWVjZObr42dU62/4cpgMB5vigpy05NivesF2zm5Y8yxT0owGHUBSglR8rJSE2OvYMyx9eUMRh0nI WeT2CwnZOnIouKZGJvIQaD8SSCMGfv7IkQJMdd5xEgANAW5mVnJBKF7TzBYNQpMMfrivJtHFxlWUeJ8qjFYTAY9w1KZCpTGwdX3fULPEJI1BZkpt6jlApqDTPBMRh1BEoJUSSdllKKMc965AxG3YMqMubVlFIeIchMiydEUaltdNoCRZYetWwMBuP wPGCWm1TVJAHCCiwWW8MRl0EAej3LyeKLKg0uqI8hdnYGYw6hCKJOkIAACgwVc5g1E0oQMneKghzMlPkDEado/i5ZsqcwairUND3ywEAKAW28JTBqLuwleUMRh3GMI8dAFizncGou7B OYPxBCCKokqlKueo0 nUarX5QBQAuAG92jdq0hRzvKgrepASMhiMRwOl1N2nkWw8j11K2Pzaiz/SngMa25RZtWLOXUnb9ea0rwq6Dgyyw aOS5LTJpz6 9fvVv7w7c8bNvy9 2hEgs7Or4G3LVcxqurmpDZhGYzHnuyc3FdefVun0zUPDipxXP/H3yu /alvn57qCjpeD8erUxNuGr7HTikpbrlTAApyxoGvvlp6KocYO1pwJzmhK79afDxTsXBc/KNiRsShXd98ufKN97 YvWDlJ6v3HorJEqmpqKr7q01Y9mO/J EnSVJFR9GUo9Gv1iC1X4deXQKsK9WgYtLRZa /93u839C3vtj4z Yta5bM6e94 ae5b646n0WqF1UlYigp22ePf217Cpvmw6gbpKdnLPxoSaNGDU Hn/9n60694z9bd547d6l g/oLFy3Nys6xEJwv1uVlh8uL16/QcgtZzLoL7k2btfRQIVoaFS13DAAAcsaVjb8eSfDvOGhctxc97ThdbvyNqEM7fj97fehrw rbobJRVbcwjMOS7GPfrTnddvo73R246sbDYDyW5BcUffnj3107BD/9VLsSx31Hz4ZfiJk7c5yNtcZ80LJPuOGxhPKzZMy5I7tWz81oBSVPdXGExscANP/y6g836sZ /k1/H7W Xy94Nu/1XLMObdcv HLZvsWfDPLgjaOqLuXEgIpvLssQSQJBYF16xmOHTqd7Y 6CwMB6Pr4 7p7uIaGnAYDD3PGQsKDgIJVKVVhQNHfewl9 /NrUZ9cpAPClw VAy10z1ag34441jfs93bjMJVrhGGjRvW1rQsXez73T3lkwPOqODdp0Dwyqv eXnevOPDuzkyNXJqpqYlaMKkJlGXiefSqH8TiSnZv/258HGjZsEHMjXuBx726tAeDIyYhrtxLrN6i/euOeFyYMtLO1Mhe8QrMcSG7Ehg//2XopnTg0GfzynBe6uwnm3JX0XW/P2t1z cpR3rzhiTJoUaNj d6uNeeazlzRz1uFyihYZNPkuXefeXfh5ss9Z7XWGEWlu/HjywvjXvv1s47WAABFEZ9O/9b2g /faJS5ec7bxzo82 L6vhO3s4s0DQa8VE4Mp4uLZ6 OVWDNa8PXANj1Wvrra8EoOXTDz v2XU7WgW1A57EzXh7ZzA5LiZvnvH2848RW13cfuJLh9uzylRP8hPtfOQxGrVCpVVMmjd yfbdMZFtb24aNG 4/eEySpNZtW2fnZOfl5mVnZb01Z4aFD0WUzGMn5ZvtFEh 7J7fTh 5mUdtvbv1W6FYAAAgAElEQVQNHTyihT1vzp3khv6wJrTl5Hk9nTjTvXIKoCSfOhrt//Tcdk5CWXmw2mvQs 2/ e3UzZaDmqiMohKT/16 OWXEjNeD1AAAuru/LNtjPfnF53zyDqxcf65p10ZxEReTCnQqjy7lxbC59vuabckE9vzy1h4A6 DZ7w5oANkXDx7698y9DAmsPRr3e6Zvn3pWSM48sHL9 aDujeMvnL6T79hn0ry rvwDqi4Go6aIkrzi5231Auv5 vl6eHlEREYBBYxxRHRscPNglUpVVKj99tft82eNN71bEq3YL5fvbvnHb9rrP7xqn3Tsl8 /XGznu2yitxl3XzMPtfGxFHc4FPrPa26PqBh/9Ltla47c1do37j3A/eqlRvO/GNZ1oPO o7FFrZuYez U9NT1p3Lcv6FdPl6yIdg68/Tqt5d/Zue71EgMTYf5K156680Dfb7 ZrgHDwAk78L3H6641eHVD6e3cJHuHF27fNEKx /m93WgAPK9Xcfbz/9k0yeORJTTtr/18pi9e82cpss6cshFCMWQOf8aDp17uHLEvbduyRZVmW5KZBTSnQvLzc3NzcrIzsKc Pa9a0sWkrFKUAYOiEmuq9Kkkh4R6DB7030ir94uG1m7dau00a5GrG3d1sZ7z0WM44EwmdnvOzRiCmX/nrz6Nnk0Ubv AuTonXfUbN6daki/2lc8lSY38THWpTxgEl5dTVli9M/LSeKif60Nebt1m7PW8khipo0tQR368LbzN1rt7GTrUx2/76I6HBmKl9GtrLiZeObVi3x/aNUR1tAEBJDotp9vyzn71gQyQl88Tviw87v/re0MYWpg2WLUfKNptjPGAEgR/ct Px05cVItva2jZu2iT80mVJktq0a6NvtmdmZkwY0QsQMtloN7kgTWgxacagZo4YvEfPnHRqzj97Y8e8YGPa/SWnSiUk bExSuNp7jzISbuXr7nRYtbPi5uhq1s XZwEjQCwtY83HEkXaZOqZlnTceLoYHsM4Npx/KQGr6 zKAbJOvvnCdWoZVP6BvAA4D7m5TEn390TkdO7JwCAdedJz7ZxEQBAg9QugUFN3awrDLzJ2VHbf/l9W1hsnsa7Vfd Qwb2aOunSo/cu GI07Q3e7uxgTrGg2dg/z6KTDb9vd3Ty0ORFcxx fn5aalpz44d3r1rR3OhqEGXm1xfTgEA Po9RnfwscPg1vPpQVFrDoen9B2sMe0 1NYQrHQgvfwxKUyLJV7DHDDIWSc2Hb0XOPB/L/iie G/bsgCHwqgcnOFszkSLRPcuJ1ePOpeHK06qEefAA2i4Ni062Dv33ZZEAOA5t7cF8n3nvFURw8OAJx79u17eePJmwXtWwIAaJr1eLqhLQ8AAifYu9Xzt9dUGK5X8uOO7Q45eiW1UOXcqEXz7h2Dgtz5rFuX9l60GTY22ImNwTEeMB1aNVIU5fjpy/pme1CzoJJme2ZaxqA 7QP9PMwMHiNTmyxwns0DbPX3LefYuIld7p2kQmho2p1UQZdrc0SNsw0Gmn8rLLX hI/ae9siaD9qUuujGwAAQJGIoOKq3Orl3Bt7GJrT2NYv0Db3tiUxpNSrCbrkmDnP/Wnk6J2apwAPwLk1dC eAYxdur/ RfeKEWhj1q89a99/zqf1NZnXTh7av zN30UAsGs64rXZjkyRMx4WRUVFGiuNo6NjdnY2ADg6OuXl5uXlFVgKgxCU6nITYJdAV8NkU2wd4GdVkJStA0/T7sS2UhGpWCCpbK0w0KLkyGz3Ab3qu1khaNJxcIMrewEAgMiE56tuy8JOvg6G5xNpPD01lsWQshLSpOzYld/uN3J0yyoiwAFgJx H4iE05Nhi4BstTERw5 CxaOuWE15wV UlRpyLWPd9iAwAVj69Rg5i62MYD4fObZsSQg4ev Dp7VnSbE9NSe3fo02rZvUtBn3gliOstldpbxUQ0HcFit8rxf/FxHOxdi2fVQMYrX0t18agZcwHVCk5o0QhlSRPKcWN3vz1k77lmtVSIgDClb9YVI2nfPKZvRUHANCoZbehLxVkpuYhZ3cnDXu6GQ LLdt3Hw05VS8gID8/XxRFSml fp6Pr/fx0DCEYMyoYWbCGXQ5gP4hKjuRnZY4A5RYyktOy7tDqbOxF NjJFjxYkoRMTiiErMfokApFTOjk60a9ubKBAcKyDg1Qg3PO6UAVCGEUgwAQAghlsTQ/0eeE94Z39Gu7EOtZFFACJuxQpbC fUf96qNCgMAeDYMbjtCm59ZiOydbNSo0rAMxn1DqxU11mWa7bk5uQVFWgv3IEImW xKctTd/JHejhhAyb5 Lcqae1Ofcq6DNsG9AI7bmcJgd5Nujs/suff19o Gyw ua/GyMKlCYJJ9b GRY4dpkXX8bchdV2GtDm6QhYYwAlPzlNS 1KxLt8J3 UtxMGkDNjruXbB5UTA2OkX0wLACC4N/GGsNAreb27O9RI WK1fZnxc97G2dumJhExGDVjy/bdh4 GOru4ZOdka4u02dk5AEAIkWXZycXpyPGTCKHRI4dWDKh/unHxU04r/EjGnfRC/UxVUnA3rsjG00GNLLgbR2LiGGtc/SHpZraMrNxbOKXuP34nXSfm3D6/76ZOETMu7T942bNDJxdcJjjmrFWgK5T0y9lJYXaWaCxeapFeDCX/Tpy2ghiAASgY1s0Ljl5ukHEptrD8yvjy0pr7gcpGwEYunMbGzdlajSoNyH7sd99 x8IiL0bH1guop2 263S6/Pw8Xz fiJjYoycjzAc0/CmHdHn9qv1XE9MSLmz9cX2s54ABgWqL7pWg8uvbVdq77Uo 5z30zSkNLn7z0nOTX/s9s11395Rd649rRn88q2P5oSjevXWwTey kLs6SnWJx9dvu01LGx1S9Maf9sYkpiWc37Jq490KYnDWHq58WkT0vYzc3Dwtde40sbf1uZXLfw 9kZCaFn/j4p71a3bHVVx8TjJOfPfOR5tviFXJEoPxkJAkafvOvQCQn59XUFBQVKR9cdrEGS9O1hbpCgoK8/LyAGD7v/skydRGphTAqF9efn05AMi3Q7eesRnURJN56ejeZMeeI90FmmvGvdDw2igeqjZxzLu0D5Z/OxHfdXhAt9E9EzbtXXxKsvYJ6tLCPiTsxIV2nV8e0NAWygbBDo0D1EfOxCQ1b cF2ecPnk2gyAcMosqxJ7eE2wxuapVx8ci FMenRpUVA6mdHHDWzfik5mpHgbeyaziwzelV23bvpj06 VnTgsyb0Xdp6 7dnA35LenU50QdXHfebuRzXdjKFcZjxfGwy ejbru6uVVstru4ul64cgcQ6tXFxPiQmWE0PmDkKPdTX89YlUXsGg5/3xgQJIZtyVqggo1Bs peWbP3x7dNHcPn3eXtnn7eILU4hCMGequ6wJmjRrxBffvzVhs AY0G3U8DbntpaKN2KU5 kVM1abE8O65YTRwUt/nf3CKrDrtfSXV9vO/HSB02/rfvrfPwUAaueGbXpPtDWxElfMuBNzVSqsUo4YjIeEIAgrv/5s0adf5uXlA6AxI4c81aMLABQWFf21ZYeoE21trL/7 jNBMKuWir/HXrJS1AAF4Ly6d3C6smfJrgJq7dF17DP9vTAoZtwJLQ5VEk/FY zVtUfDHw5uvjTm TbNJs5qNrE4sSGUEIRxqeeSIHxg/6d7bT644tPTvK1rqx7tmlw/W3yJ8 re3jl675Ld5sQQGvbuWH/TseVfHgaroNfn9m8ybOx02 O7/t18RAsg2Pg2DB6oKZccABApNzU2TtYSUx0ZBuMRIctKSHiUnZ1Nfn6eKIq6Iu3Q/h05jPceOUcIlSQJYxQaHtW9QxDPV2GmluA9/vs/xgMA9JtWFXfOdejXfwy1fAyA7Vq/ sHoZYvefztq9PNDOzf3c SLUm9eCNn6z2nXmUtmBGsQAICiEMCCYRIcdmg5 dNVk0sSGjoYAEACAMCOrSZ/Yl4MQJoGwz/6ebjRZbfOz8/r/Hy5rJbkyBCF1/Dlu4YDg/G44ehgv2jhu6/NeW/o4P4Dn 6jd zf96nCIu0/W/9dvuRDBwd7C8HRj0vmPNV3ICGkIC/rwUtLxdSoDb HZTXoMLBzw/pu1pyYF3/j6rGQm47Dxo sJyAAIDkhP20MbzPx7S7mx72UrEM//BnR8fk3O9mziSmM/wj5Bdo1mw9pRZES lSX5p3aNAGAcxE3jpyKRAhrVPy0Z/vbmvr0G8cJwZ0G6gqyH46cpCD2 JZ//g2JvJ6uBWzrG9yh/4hRw9p6qBBQuTDzdsjyhZvt5v3wfhvz67ulxM1vzD0x JsVQ9haMMZ/C5PbqFjeW0Vt43glfB//cFdGI5V7i6mve14MPXvoz/B7ORIgjXu9 h0HDOseICAAquhyk 5eyeLd3ayYkmYwjLG10bwwof9XP2/v2r6pXpEDQPtWjbQ66VjY5ZmTB5lU5HpMrzp/MGCber0nz 092cQl8ca62e fsOk27bXmVfxQC4Px38Kkzra4SZrh6S75Hjt5aHOxkdq1bb9BbfuVc6aUghgfuvy361bBPUcHCJbkKZ5ET9kEcsZ/CSuN6t2ZowSBN77xu3UI6ti6UTnH8jweHzNSB83cuH1m5f6EcoZxBoNhHgRg9K2YRyuLAZV/30Uf9a3cH fU9/WZVfDHYNQ1BMHEJ4ZNOjIYjP8OfIkqZ11cBqPOwh5uBqOuYrCxG6xvhD3uDEZdhT3bDEZdRf908ya3SWMwGHWJx2O4nMFg3H/0T7fx99iZMmcw6ibm9jxmMBhPOvqnm0cIaYsKiSKrVGyVCINRN9EV5rLOOYNRJ9EV5oLexk4UObjD049aHgaD8QDRFeU9ahEYDMaDotTGzh51BoPBYDCeLERtPgDwiSkZwcVOA4OGPEKBGAxGXYdSCvrtFxACZvZ/jDHUFMYYEGIV99DYF7O7ZgHZl1IZDMbDg1KCsX6rZaYPHmcQQghjTCgx7IrNKu7xhn0uisFgPEQoBQzmV82UW1bD1MYDolzxmqkOBFCyY2QlFVcSG6u4R0OFfjnvM/zohb9n 5RX8ubcDQh c/eEHhruUbyrEbXtvvheZFhaZFja7teCSgOZc68U5D95XfyWyYG1NCSUl/ORwzV5acm7DS19OB8AalFuVaWS mUwHg7GeyUbn1b9ZzKeOsbjWUq1FMlk2DqMuYzXkPtlYycFlw/tO3BPWywJyj/xP/ WXZr 75KujD9z7gAA2K7hxAUrz54 lRZ54sr6BRMCrIzbdgW3Tv5z9Gb fZZTD99mwc741b3sHs2tg6pQCZbKjcFglFLuhVh1FVLR80OQs1IZqiJwnaFidmpTfQ 5BmtciXBfpL1fulzJ3P/V4mUXc0hNI0DWjef 9uMszfHZI5/2bj9s2lHXj36a3aG0v0ozTv78xnen0mqcwH2S8/6BHFqPX71lV8isnm9vPRC97avZ9SvtnTMYjAeAuVd/zTqX1eqDVioDo1IsFN3DrEHLkjxwTOpyJASOmH/8dFjapX173unjzVl2txqw9lRaZFhaZJjBdk1kUafVarVarU4nVVEOrtGk ZMTV4xa E9YUr4kZp1Zt/Trwu6TmlgB8EFv/K2PP23Lcz6SVqvVyQQ4zyGHLmyd6y8AACC7kX EXJzdALRa2W3U8Us7Vy344tSJIwlndY081dn0ci9FltJCeRdFqtVqs0fHVzWmTogXFu6k6f374clhYZdmComz6E2qfnR6v/uRsZlnZh17/v9vcvMT9bt//jzN7vBgxaumFvWmRYWuh3L3gqOpkCAHA27h7u7jZVsFTbtPh05ateW94a/N2xL8aNeuaLAzd1NbwF7ILHrNqyNzUyLC3iUPgPLzZXAYDJ8mmqMe8fwHy9Mx4yVNFpdTKpcFxFFFGrlcijeaEwLEAVhRATx4xHC1WUOvC4mNTlnMfEp6UVk0d1fHkzjF 06hkv3th9ytjus/7GEz5ZPdybBwAo2j 1q1u7cUvjZQAASmVJJhQAEMaYwwBgUJuiYl4Mdb1nn7H7Z WhRGTf49VlJ47uu/DbK01lwduBB5BjVox1a9m13ZfXq2pexm6DA85P69svcOTXWeM//X6AOwcAULhnUlu74FGf6 U0IF/9brxbyx5P/5WmC3 /fosubi27PL0rjQAg2xYfr/l0YNz6ccNGdp7 493 H2yc0kBtyCAFzvGZd4ZmfDfNv3WvFq/8frHA8FSq64/ddXDH3imVd7E5x3rBNqkHQ 7kU6BS/s1T /YkiFXMXxkE3xeXvNU9 vsBg4a1HvnWklMZFoq5Ev m67cOQRVRfyeWPLiUiJbvTCjWpk/ s86oMpQoRCn7u196FyFUMi/M JhxPyhfcYRUeZ RSuriket7bWElA8ymbezK4S9/2H417mrIb 9tze4wrocXNnK/Fn8t9PcFOzPbje3uZSK4Ye9UxKtUKoGvWt8OOzbqrLl2KE507Tf/lxHi96 9OPH3tHZBDnz5wuVVao1GreYrGRrQ7v7x32s6IsYf/2ZPbpfxnVyr/8A4dZ/2LL9/9tId4XeTb13as2hllP8zfetxxRnEkPDHlytOJxcRXfKVMxdyBXUFWQEAgPPuO3ProZC0yEMhy2eOaupiZe3 1NRXR3nySvqVY2k r81/cXgDB42qFg 04FDPGWLDwiMS0hNuR27bsC3GcpPAkv q1G8dgMhMMzMqA3GY441P5pXWrmmHE/KK04DgGlpOo6uFJ/6FG1vGRJvHElnBBLvQ6TPS SdvFeIQUAkOIik2m/Bu48JJVxl MvJ9Oe/k5Ee0MLgDCH9Rpc0ekMnRwq67QyEiUAkPRNWiJptRIAEtTqshqeSLLK3Tr7TqrINe7XPO7nKRsupaAraxefGvoS0Wq1OswLxY0CWdRptQriVYYoKJVFnZaAWjLubCvpMak6AKCKNj4qDXf3c6JyYuX1SWRJp9XXO9J4BAdYu3bZfXZo6fWsZEdOEQskIgDIBRHn7 ZqtSUXEa9W80h3bXWrxj9RQDzPUUVWsFf3fu4hn89ZnOPYadi4z/6avAogN/z74Ru0iu7qoufm5Mx9cdqAlj6DD40I3TB3waqDKVrZIADmeEHgkL58dKJCAfE8L kAQCxjcS26vXHHnV1LNp8YeerEhYv7/t1zNL7IUl4t Deu36hk2rOBOw9xNTIWPM5gDhNFUngVV/HBJIokSYreqsQJAo8REFEnUQBZp5UBgFNphLINHKpIkqwYLFG8PgwQWScqHM8RRSYUAHGCSuBK3TFRFEIRr1LzUCFFy68Lk8kBUCJLUnFaj/3gyP3VXxULjJq/VJ14ESrumYChCU8VhSKMwNDbQ5gz7DNp7I44jCilxT1ChBCqrFZrgIU8PrjmwX2P YHUXWnFIcwjKhNCgMP6yCkltKRisKl6MeWHEoUCAJGVEkeoQlRVoWr5TU2MBYC0pHsePoHm/FTFimpimgaRRABKKcIYUUKJIhkaPxghMLqHy34iCCEEYLJ5SykgIDKhQCVRJkRWRF2 1tAqILIkY5PvJ6IY3pUIA1Ba3GhBnIAREFmUCGAOIQRUliyP3FMAkBSFQkmOZJCjv 743F9xxoqTGrIEVMoX9fkxetyN/MmyjBBCSsofb8 XKadW8efPHFz5sZOvg5iQlCPpN7ZJCF36Zvju17 YHLunYPpH65bcaj3t30QoKVIdBbWRwqGybGrYlBadWTal2b dBnTr0H/I65tfGPjO0Jlrk WynoxeJlXyX1ImdRCEeZ6Isky4ClpZFCWKBZWAEVUkSRRBrRawSi3odDKnNmV5oUTSSYQTVCqMgCqyKEqouM6orIBKpcFAFUknSRiXuiOVSoMBABRRVzFF8w 1ueSoIoky5QQVj4HIkkQAHnt9fv wcJ/W9hYut70cBQCgFDCHOQzEoCQQLeOOgFJFoRSh4n4hpRQhZLY3Xkshn jH9EHVXUnFUQAMQCjo9btCKUKYRwiAKsXVVzacST IA1Ao4outM5QociVRVV9kc8iSmJWRaOvgkp5yz83LH5tWhqZt7Nittb81AgAQ/Fp6QvINw6u 2J3IyKeFJyTfygCVSq1/yVFCKAAnqAy9AsSr1GoBE5ny1moEAIAFtVqtVgsYAVVEmfKqkreWnJ2Q41Dfy1q5deyq/3Mj29phq8CnZ3V14ZH dauPvAxELNRSzlqFAbBg49rA2ehNi93bBlhTRaGgDmjlCclx2VgtWDIXIyJTQBxGvEqtz5GcGHFXrtexhW3ZYAiXZhCr1Gq1WlW2F8Tbefl4e9vxiNdfBJlQoIQAEEWRCtLuJOZRlUatNpaH5N0JHnSNy0XYCmRAAEAEQuax7CPIdkyttala9LOT3m5MZfVkydOPsPbfCoZrb68tEhwUaFAQB4e387zrJ/4/oF4H2bG9V7HQNhTm81KXtPUUUmwAkChzFCHC/wiCqyZfMcJbKCeBXPYYwQxjzPo1KLHuL0nWaEOJ4Do4G7Yvdqp2guOUM8PIcRwlyxOYdRO6isyAohxb8Sd8RhjIESAARAS7sqxe6UEEIBcQaLCUIYKKEGz6WxP8Sc/PeoULqUgr6vjjge6794gzACSmm5UXLzfvRxUkIJoYSY9vZgSE2KVWusVSqNWmOVlnTXnDfTGo7r99aMZ5r4Nu0x7fOR9qc3n0ghRu6NfZp0n/r5SPvTm47fK9JqtcXzgkxskYyKYi8mefae1D3Qx83VWYPLuvea2Lmet5uLkxqTnCsHMoPGNLNL2/fZ7NNtfzt8OGJF75wbKfkKKm4HlY aFtwNT3Mb/HRDW6zy6j5 kj8yWqfN9Z87c0QT36De0z8bahP2V3gaRRxnQZnLqTdSuUb9 wdYcUCJqNXJJOPkLxtyu61cOn1gEx /gKb9Jsz5YXYr68qeQHXg L1Hd 9/oYE1RmAwRAAApZRSg/Gc07/fVd59P3pnfP8mbnYcFhwbjBobpFy7cFdrWAJQXKTGL3bE8Zy2bLkBAGgavPzG5BGt6/u6e7bsM7C7fVZUQhEA0IJ7Z9JdBvRrYAOcR7fxk/yLbzQz/svW76RPhjme etkSh2daIswzyMilTVzUEqN7RcI4xITkzkoIUBlnWHVhlYrytTITGNsdDPqlaFSE0k1UzSXHKUUiq29AIDu48juf5iy4 VciREVAVCir04EQEvqs9SdGiqZ0lJvRkqf8WigFACoIimyrJ8ZZ7Afl/VUBT9mvT0IZEnMSIkrKsjLTEsoKshLTbxjbtTcpI1dSfnjsNXcjduaqjNPr5n34o4kGSG xH3DP3r3F7amUI6zaTbr3JYpvvqAn2xP/gTgxopWz6y7AwAAuht/vfFb219 2voSwKUFIwbuTFGM3H/9/s/pABELhjz1V/zmtbGh7z3XfMrqg1 8snsJBcSrVbylV5vuzveL/uz2xfqE6Rkxx7ZvuaGMKSlxJen3Q7bv/b2zIZ956tf5M/amKACaZrMu/D3Vr7ycv98DACCJe7/6ctDSnw G8AAX3h/Ub3saKYz43 R3tYtm/fT3CzZAs26f3/rTFhndtwY1KUhJdZ2wbOO8hvYIoGt82Mapc/ckEsyV6VSVeSujcuX2wYgBO1IUIopePRf NNPPGkjWze1L3l2invu/3Dp392 /yX21MzY45t23JDGWNI2Ix/MK7f7DPrFsz4N6lOdssBABDiBU4WJZkTah2VoFZX6AgTAPPv7toN4ppITv9slw5l1SZ RgllxsspNdFXsUj5sTcEtTLBMmoKBUNdgqEVX/56uWqpih/T3ugDmOnOC6rWnQcgzBWrHkSJoigmXs3o8/nT /cfENzhaV1RXtl90oisE2Wqn9XFleliGCZjAadSC8X9ZqoQ4DgElEg6USmeC6bPoKgTCQAWNCrTo96SVlSA9564cu3nLscXLFmzPSJZdvL1UNKTChVJ1CkUEGcV/NqGY322th218R5BvErN4/Ji6E95v dO7h /acjE7 8VVLxa i4smVBmKqoyOSpHuQyWOy0brSFrgHiVGiv6JLCgVnH6MVQCAOqWb3wx6tAHn8XkmhWgXJyMGkMVUSch/fQ1qj/hMZFB0Kg4oLJOJ OS8i89BUWnkzlThU9lUSeDoK4wjY7IOlEpfW6IpBOpoFZhWsa9SinS0mNzyVFZp1M4tYpHpqJ9vKBEIRg/7rcxJfrB0XL6mFJCKOY5pHenlBDKCRwoRDF2J4RQxPGGcXTDqYCBEEUp9lYuqscXQgjHcfSJrTj9 DfmeUQUhRCjeikNZFQXlFTuBwDMebsP7Lu6p7pBRG3 vZuXq1A3VNZpdVrDT5QpBczzxTN3dKIoijqdVqeTzI70GWx RNLpdPrmgSnkpM1vTZ5ygB /5M97MedTjv/4fks7BACclYurm1e9tuOGBORevpphZBYt7sMqoiiKok4sa iwfLUc1cxRTSiWh0g6rVanM0zuB6oUFRYq9CEIwCgDQpzAIVJqZ0ccj0GRZIUQShVZkmnxmCdCQAnRW7PLxsHxHBBJlBVCKaVEUWRJqfrjbT5Fs/5NJoc4HlNZPxseiCKxFXe1xDA0SvVzoaBixVsGIQRUIYaAhBqmBLMx8gdOuYojlCqUAmBOb FFCKiilNapqX60WT/IYGqhlr09Omr2NRDEqVQgy7JC9LPSEMIcZ24BJkIczxFJIcZFYRIlO2zD0pFrPtb3QtUqHgGo6k04sGdWY4C8qK0zf7hcaOwf8yoBJEkmlBDgeJ6Wmeht WptclQz9PLIMqH6IqGSTADk62s/uoUeigCMciCex4pkpMxVKpAkSVQAAGFOpdIblhDmeSzJOp1cYU0awoJahSRJEg2zQzFfxU8qWEzRrH8zySFOUFFJ0mllQIjjeEzq7OjIw4MqZcYlq7GuDBnW1RhmyCCk1yWP/GX/H8G44hBCHKdfVWaoF0RpyXd/EEao3DiuOT AEKJEHzMCjKsQ1cPGgo2dcb htFpsCycAACAASURBVHQ lAmrPoNR53kyTLUAALjCY6lfMq5fM0qNvJl0B2P1b9RtM/ZWMcjjx5NlYweoUHH6mQ7l9LXx/FN9BZSrC5N Sh2NGmoVvdWOGtvY69pXOh9jKJVFnaK/04oX2WHekk2VwWA8KiqugzXpXnJa0b9JPW3szVwSjNpQaamaVLrlQpn0U9HxPunv wLT5Q8RjDFRSHGDDnO8wLOlwIz/GOyOf7Jg6yOeEJ4Em8mjRPCbuyfUsP9bLUGIE1RqjQG1WlX3FTnn/uK20BOT/C0s/OJ9hh 98Pdsnye8UXkf75PHkCrUYyXU7fJ5AHCeQw5f3DI3oKpFzvsMP3bxr9m T/hzxChDctzNK ePnQv99/TRreFHt54/sfva5dNZGckmPZfX5dSm48Lb g1GI8PSzu3ev2h0sNV9Vjlq/75f/rE7NTIs7fjarwf5ayy723XaUiJPZFha2Oc9LO1BhgNf2GDweX7P8W9mj/DX1Ep6UnD50L4D97QPwo5SvXJAVu1f nD79l1JkWFpWyYH1rQRhhyf2mVcnpFhewc4oxqUW/XlQTYNnl 0KvJCWFpk2I2/PxjkVMM8VK/c7ld5Wrf6 UzpfrjleZD3iWlUAe/tL1OPaSEfdqp0e74HC99mwc741b3sTFiWjcuH3s8fsurw0oc7tu9KvhyWvnVyIL7f/u/nj2 7YGfCL73saFU866l65NX1X61oH1Dk7GeuwAvysy6F7UtLvuddL6hjr9G9hk7vNmBi6y6D3D3rpSbGxlw6IYnltw013YxLWD593rYs7BDYbd5nc//IvdZ5eVSRSY81QOX/ spPxmasmTDmsNJzzpqlXyVfnbj0js6sOwAoRbsXvvn1LR0AUCnnVqW7feSGznxpdaxLkyHTX1 9qb7qmbf/Sq9kI1CzKJn7v1q8v4aBLVLdckC8rVXRpe2/He88c75bzZOleedmjZtmb9fiy1/f4pe9/saFvLy4HMMdVK1yq648nPMzS378qvHFz e9HppCnP3dM2tWJ9UttwdcngYe3H1ikfQdiyb9ESvpl5WLWTcf241wypUPteC1miDe1qrw4o5fj3V 9X9uVYi8uv4fEJUmSisc3F//NeORlNV/joLczOiLoX4NWwY2bUcUiSiypCuQRC0lso29Q32HNnk5WVHnjzVr 5RaXdJlMWNj1yXF3rl268aZQ5u O6fzbhVoh4DzHHLowta5ejMbshv5R8jF2U318dgFj1m1ZW9qZFhaxKHwH15srrIkpqbx0EmB6asXrzt8/faxdV9 F fz/JhGVubdAQComH7rWkT01Yjoq5E3kgoqu5 olBN768a5E7s nvPeJtrpvQmN9HKqfXp tPqfu5FhaRd2/ftuf38eAISW87bGrR1RvLkn8hjxXdyh99urAMBqwNpT h5PedsgZ9d5 qIjx0 mRYbFH1i9rJ XYDb1cOJO/Yt8s WrvzmMlt0Dgbdw93d5sqWNiUgjtXr0ZcvZcLkHvvekT09dt5iuVyM41ZeZBbj5e3HTmRFnns5GejGhdv56oKGPhO95ylL3/w9cHz5yIvHti1/1xuyXoOIXDE/OOnw9Iu7dvzTh9v47KukK/qllsNy7MamL5POM8hhy7uXPHKe/uPHkuLPH7yk0F uNjdxHOEHLu/Gxm 5hVfAQBA8H75z2PRn/R0qcympE2LjYq5ang0bqYUUgBAdsGjV23dnxYZlnZy06/PN7dHFtI1K6e5egTBa/yH350 eTItMiw1ZMPqSa0cEQBwTV7bnBYZemCcm7rT57cvh6VFltgwypVPSZawXfPRq7YdSI86nR626ddJLewN5TP0cMTOFTPfP3DseHpUyKnFg/0s2 VJ7tFvln3027/H46pWj9X1DwC2HTedP/DjkGHLN 9LjzqdfnLVDD/BnPxm3Pkmr/ VHhV6YLybutPnd6JOp0edPjDMjI2nFOTc5aWtR0 lR4WWlAPnOfTwpa1z6xnqcdSfoZfeaFpsahICR/wv5Mzp9Mj9e97t631/zO1suPwhQym9GnnKt36zBkEdKSXl1rlRSmRJq7HS DdocfPKGeOrlu4mbO3faXRzddz5W7kW7nrB98Ulb3WP/n7AoGGtR7615FSGxe4WcmjU2rvw2okEEQBASg27kufRupEjMucOAAC8w QNR9Miw25v/2peZ7eq36I079qOKNGvWys3DMi2xcdrPh0Yt37csJGdp/94t/8HG6c0UIN0Y8/RzOChPRwxAAB26Dqiee7RvdE6ACjaP7WrW7txS PLrdXlGk7 asvrjc8ve7XroLFDPj c527Pg7n472s5mEddf yug/9n77rDojq 9pl7t4CwiCIgIihiCwrYuylKVOy9fHajxoIlkdhr0IhoLBFbNFETewXFgtEoCq4aFFiIiBQFRJBFUOqWe2e P 7S9y67iMbktzDw87O/fMmfdMn7lzAq9MblIji6xleTMUtK3H7m1TrC6u mzgjM35n04pboktXLo7ZkTmDd1wX3o79fbJY7O72pRen287vo96RRPeadpsb57B9S2gpVypehvFWTT0PAV04AaOvB7kkLPXs5Dt R0997dXtzbY9zIG/Cds29Yrnsh9FNBbTTmFUrbELm YW NnyUgSza/rDPu2vsbs BI/tuiW6/eNumThZVZFebnnx2BNpUkhu ecHkjn1HeviEOX zxbeDOQI2btcYa7eefU7JlfeXNXHtau3WtU QHGvhByGKEALIos0PP3/X7cluzwEj 26O6bBka6metM0Q96QFnl84DN2R7blIJ28fCrTFwEUDs3bOdGrfu 28I1FFmE9/nnAmzn90vdY9 5yUK 8vc2rdpV7rLn0uyqtwdyCwGz9CcnzBRI/F5wVDdJcfTsn6E/qotk8a1d3rNDXO58CQd /NOVeYXCnUGM6I94wXz/6mKEFz15463lbHmDWXWFA0/fbN65JA7Y11ky1/hsllYclBvp5x ybvi1VojcVBWLtxXXguvR VlpWWJDt/5HysroU ysLWHPLlBbZ9ToRdPzXItkieBxJrC4ovHECdeX6r78QZM/rPXL33ZTPvn3 a56hz4l8OTHZaLtSxr0tDnR5TxwqC528KvJ ckRh5ed3OGMfBvRvTUJRw7Wp s7Ht6lAAqHbrca2Uf1yIK9TR Jk4T5/UOsV/xYpLUfFpL6JunvA5FlcEvPJrjIcPilLeDASq1214D8XNlXtvPk6JD/xpx1VNYaAs7euY2vdb5Jqwdvq0EX73HGdt bW0rWFvbNkdEPci7s5vKy9ktx/Vw443v4by9s/yWXBp38VYBS56FnIiSeTqZqOr4JKC0B/XnKw/fd8ir73zHc8v23ozr2rPNg2nH0wt3i9/OKe5GIi52/BBtaLXbb4YnpL2KMB/Tbi4/1g38yqa4Mp68tkRQJF0YNuhs EJz9PTZH8c2R4j6tS1oQEjSAQIURRFzNxGDK4VtXZT4IPnqeHnflr9wGTAOFczzeV6 UF7Ax8XsoVJN08kiV3drIWkamACAHrEq1Z8oCDtmO WO8m5ivyUh7fvytVmrlr1xzzhZRPFBOtMrDhNAoobW/xPRSVEXP19X3wJD5p7xkqiFecCCDDXN 86F5vyJOTwisDs9qO710f6ZlC7AoSiqGI/YhrDGUKxEdXB61cvGrdoW WgSaUqsnNo/vpVakmIzv1yC8f2X6 Ye3BBTK9N4QV8MouSjgY C/I9GTrsbuijiKsXL9/UZ9FSXZiZngG56ooxK4crnh059AwAAGL kr20uXJg4pAme3Y 0TW8KEWJGKG9W6Na9bpe mtg6Y85GZYCgKKk0yG5Z4a1rXP9OttuUIcC6finus4GIPNGbawK/vorvfyIhV7l1h/XnQCWX8oU5uh/SLqw qPfwW2Davj17efq4AACAFLx6m4yYAxc7B0v3X/HIljYG/967o3f/U8M7WgeflAIDlESmFBACAeRGTQT51thFAqgpAR74M5c1APmsGbF5KDgMAgFUFaiI2E1E6iwPJk61fceHuL2PpM9 MfvBWHx91ZfbLcVFmsgoom8YNTeRR8QUYAIAUJj6Wizs3sqJCC3VI0aInnx0BKPOOk7w3Tu7lbqU5Yp0VZ2Lw0AgJ6jZpaCKXJRYhiqYBlM eyMWdm9gIpSk0IJyf pZQNA2IKWKIibmpgKarusiOoinury5/iNWMTyPEKmIi5Uyps0Vk5axV/3us9nBpASlJlKb0uNCRogGxb IyGYqmASnfKDHHA6EBIURRNEVjQNzlLTRF0xQNCGdFvlAimkaAXz7OIJ83txPTae90hIJUbAoQn/NsI2oKKmWRjX0zANC9rUEwNjE1f5vzqiREe1 uTH/ LC4LQ2J8gqhzzIYp3fzD/ygXocyFhqTogd9kl4ud 3bv OUAr5Nf9ftu4OxDvI6vcW5mPphbm2WHzh8ZCiDuNkACefJcjLH28PJPK17 lQ6jHGsLiJ7bN8K6DSwgJy2bAUsA5vH2Tv93MrViG6l6fPFOgf gjpJ7zNB2qtvLoxXV3Bvika8V78bDe0cpb4aDEMwSjUM5oi72L5GXVQCMMvY1J1Gd TwHmtrWpkCuRYAO4Yby9o/ySapckqxwMaiggbuLFQDV2q2h6N5bPVphbr 8zLhWW8HVcvdo XS166nVjkTSeeHRha7nF00Zfed5tsqk38Gr26pWU4twTRKl/wCUXFlOCCm 7ZloIld9VIyUE1i1AobFJ0yBCpdVo/zjpfrzhZdNVN xMuGulNLGg4Yf7taxyuGa/9/DFfDGRfb3DYyxiak5IVW3UTRFqxSlg/QqBqWEVamJyMJSTGFVoRIJzUQUAIDAwlFSdnjGZMWGHT2wfcr4 ccUrYa76NoXfPs08mWt5t0biAAAhNZdWkleRca/IXzh5Z82qd uPrxOecvo19ciSYshrqLUu1Fyon4pS2Yad3Uzr5xhVBh75YbadXy3DmPaw83A2Hydwkl cuRrs44d7cqvl qQr13MO/FQGQJzO3s7O0kNHXcp5c3QR5lXcRm4XhNrrnSIrD6px/1HchNjMwU2zepwGgrqOVhCbqamT6Ws2zjWQgAAgoat60NGfOlQsGK DOWtuny N ioR6Ytxu6ZZXtk9vz9kgn7vvqkVnWUxG S0xTWnzQzowAAkKmzSz1lanI21pWuNvDZkbZ1czGLO73rz6RsFQaRdZsGwrIuFAkhgPSZGfPqWcOo0XpRBnz6686X/vzwJ6zDjjrqkRH/Juh9Vy4pOwzX/ozYrrFTiybObboNWr2wuzjhTsRbTApSHmRZ9fVwNgPatvuYiY7FVdjEeebCSUPbNGloU9 tV78eFjkxabrWqBVPg448t5m5fMIXTZt8NmnRPIe0I2fii3jDkdWnczZNH/hlu1btO/b65oeN0yyTDgcm6l5gR8LajZ2btus YNW2jWOpB77H4xUA2WGHThR0/mnTV/1a2Ds0aukxbsHu e6a5rIw/pRU8YX3gr5M MnH VXQp0g88HtMI68N6we4N7Vr4NJ92OIxzU11y68BHgAAmdk5u7l80sJKhExtWrq0dHWqKy42gthpZOCVc0ET9Tj7Rps5tWzp3tLRAsDCsbm7S/Mmxc2BVt500KxNH5IlPRdm0Xt rwYiJGwycOrg4nFdYezF0xkO3638v8 dHVw9pqz1MI8IeJCpaeNoj29nDW5u36LHRJ9Blg9Ohb0qbtMr58tQ3qrHJx/M7J3dXVpqPi0d6xi 3shbj0yd522aYXlyrU/YX5uWnxTPWL/IpZbhy0MoX3buksJ1jfeg9g72bYd4re3AXDsdnYf40 VRk8eO HVCqtKhaxdrASBxyxFeM zKPsVkJWbSzTx6O0hMxWKRrvaIV0/DYWi9qI7d9dZfd77054cXOu3IW4 M B A9gGr/aJfjywCAJIfH3Zqms9vcSwAm7R7/fHuGw8kTcmOvXX bDw7kouLVSq7T1fvne1QC3BOQoDvYt nFV9iLwdViv 81Xa 3546NwPePD2y9Nsd3EvkPOFqBbiMXjB1vjkCeJtwZ9NMv10p6ioyZdFzz8mewL6NvXNl5tifA QsAJA82copSwtWzt17epoZkJykh f2ni2e3xdFBdxTenqiK34PCzXrlCYus6QnJjfkfvcJyPABiN/TadRvzzCbcPjbEcj7hyW7p1pSbNaToxvvMVXIrwEeAETu3 wJ7CcBAIARvx0bAYn7u478NcHAt7SRpMPOU76duS L/a8DhH83oH/wGz7e MGjz6sbXoua/rz2aMIaZbosJPgVduGiKxL85vhYrvc6dX42YrLCDq Ye 4FwxVA9tWxG6beR860FL95cHjlrIvpuqYThvJWo3w2n7vt2tySb0nevSaetJmptZyk8IlQaq1H4jZff79AfGnkrog8AIj8Zc6pzwP9Zl4dteMvA6 fIW8fLZu1bauP19VL5lCQcmnLt97SN4Q3XV6wPHbMCflxweUNfldu BbkJoed2R3daXqZxF9e3bmj7/pdl68JACKWD 4XJBfx1SM PQ2GoXasmXrEy7OufGnhx DeVocdDapHRvzXYPSTZoQRRhhhhBEfBdbumtZ31AKWZQhmWawmLIMxi1lGrVJglmFZpuSvaS2Lh2GXu/QaYfSTZoQRRvwjMJ6g heh7OKi0XAfL4x9uRFGGPEhoXmPVsdVGEZ8FEAaFH83Gu7Dw4CTHMa 3AgjjPhgIIQAwQRRFKLAeDHoRwzOUhhRBBAyGu7jh9HnqRFGGPHhQAimKAohZOwPPm4ghBBFUZhgzk5Gw31YGEyycV5uhBFGfEAQAhTw77yWruiW/2pEzaICvTzmQAC4zD00ugxXIs1ouH8Gxnm5bggdvC/fqegnzQg9QdtMP38ndKKjkD KwH7IzUen59v/yweV/ 1yoocdq4D /FTw41ylu fKH61y/m3g/Not4qO8UmYFDYbcfHR6nr3gn2TpHQ2n9dn/MPgyXk1U7MuJWafVScXeGuThl4LXjWhlWsNDLLFj7y3HLmXKpPKQQ9s8HU2qCudg0nTcdZlUfmqczlsuKKevjmiUf3g5ZMf8oY4m76Q9Loi fvVaioEv eoHw3hAph1mrAkICEqXSeVnJzlVdxCGLD8LKrGvTCqXSa/0rYuqwZvh iAz5wnr9skeSeUyafzpVZ51qpkHQ8tPzfBZy/3nByV PCvhfZYT7RA1Whpczo7y22s614ibvOpD0HblhRf7P5dUZuH98YNMO8xcExAYlB4tlZ b5ERXahAr9haV7K4rcs2iPD98aekzmqkQ T DytnRfwSgNfIH0FZPTXTrVgPaam Z0n6cNqHHsEkDlp7O9/Q NqeV6TumUhYiR6 dPqMUAeNGjh/1 9uhm7YucBLrCucgdpyxdiR6pvMWmhLk3pk9ZpLngt1/SvrvP E7qt47TJbY7OCtG/wi9HJ0YRgM5QEJzE2LIgN 9btb1c10OkHywueNnurx1dZIgBg/L4 xk fefaspRQbxZqg dN3Bvnu2dnlzcImX54Q5cw8/qOIqGj4Yytt75lOD91dOdCIrcJ3nmKkeY6d6jJ3ae9re6HdypPE 8f74QQJz06KIgF836WlHrfH5mv7qTS717HX40jLCUOigrsYtqHug8E8aUXtfrkx//iwuMf7B9RP 4coG7k4SpFnz8ebWfJBk2LHbEfNbclMcSauR 85eyZRJ5VHX7e3lqnS1KT5gMnOmXu/X7fJdnjq/s2bk 2nzCymakmPGv/hsM3nibdOrzFP1UTDgAAwhaTVo5P9N8UVVDKElYrFQqFQslUah6I u3zxPjw0KDvFyw9QTovHdeM01Ns/ na/WeSZVL5o6CLi790FACA0G3JudRDQ4udbCLbof6p15e0QQqFgu61/y4347k2qDbDlLEPLekybd2fIWFymfTFtf1 HnZCXvm6edCSX14ecN6tn/zWHrpwS6sbOtrMxtbGxkyPlWq24NmTJ1FPUnIBclOeRj1 mpTH6uZNO3j1QdY9Z57/M1QuuxX2w/DmIs30XtSo33c93m6auWrbHw/DZRHXgoLDSzycIKHT0OUh96TyyKuXv vVoOwQolK DOWtmnwaANO hzTlpOwaMl1/wPWIC9u/Xhp885ZcFhLm4 lAFYdrqUfIssdi2f2DXzcUAgAI6n/1 83HPp9aIQDCKrUVcg6cb5Wox0 iHj RJbwqJACAJJ8M2306WC6TysNO/DKhNecVnK/ 8unJZ0cQ2o1Z438vLEwuk2bePrJ/orslAgC6xdyTctmda6OtxZ03JkVL5bKSNQzt/AAgSasR 84Fy6Ol8rvl9Yy8sG3W0uBbt TRIWHrPR10D8Vx3q0dfusOXgjR046GxgcA844nHl7b03/QlhNX5NFSeejerx2EfPrzhNMtvE7Ko8vwEy0NHmhVVcKobtfpZ2 GyaNvl/BA1x9wPeLcokacHc2HHb8dsaBl8VKT0Gno8pD7UnnU1cuLy9cjI3SBsCz Z/rfmoSupUWqlmPnEa3FqQ8Tc7VnlFEqFArWdsrGb3s83tXXc1CbYd/63n2tc7qFajdr06Dw75AUFQCiWPm9mDzbNs61lCoThzYNCuNCORd96kzp33m2bZpZctepNh3108ic9duk2QZmjuTFBcaoHLq7W1OAzF2/P7i X rvowcN6zJtT/KXq45OdhaDOv7yzexWA3taUgAAVO1uQ1vn/nkhuhAACq9O7mjpPvKH5xUmO3TTSVvPejV/6Denm eoARtv5NlYCIBPvm4eKueXL7yKnIqbjAr6I/DKZD3uY9cDZXkzFLStx 5tU6wurvps4IzN Z9OKW6JLVy6O2ZE5g3dcF96O/X2yWOzu9pQpc M76PePnlUj3mnqXE0v9mlfOl6G8lQ9XZdyJyLNt09iiNKuEqXIuy/WmvHW9KHhKN v2oze9qHRjJm092D1poWcvx E7cvp7r26vy fQm7Bdc69YLvthdFMB7TRmzSq7G3M2hb42vIFBFm037F/cPe6nfgNH9t0S3X7xtk2dLKooPtr05LMj0KaS3PDNCyZ37DvSwyfM Zstvh3MEbBxu8ZYu/Xsc0quvL siWtXa7eufTQXlGrnB1m03fCzd9cnuz05PZeU0ZO2HuKetLBfL8dhO3L6e69up4O39wSCWcyWfgihJAMWDcjaObNJ 97t5h2JKsJ8 vOEs3H Y6xde3oclyvvL2/i2tXatYtHoJwgpOuMmKDBGS4wsmfrnkvGDId1XzQNtO6KPaPnlUD6/T1Dif/UMb/MsPoVQDFQyHMdb7ZXjdtvgX9PfaG smW/4Mk8vCkoN8PeP2Td4Xq8vHhtDSqS48l96PSstKS5KdP3I VlfjSFnYmkO vMB24LnwOwEj7FXZeSCxrk1TFvW58D4nwq6fGmRbJM8DibUFBSB2nLl fPaOrVfelBkkEABKKBabmIjFAl39DZOdlgt17OvSUKfH1LGC4PmbAu8nZyRGXl63M8ZxcO/GNBQlXLua32xsuzoUAKrdelwrxdWAJwUIkEAkEgmFAooSUBRlIhaU pKZPql1iv KFZei4tNeRN084XMsrgh45VfFQ4X88oXryOP7QClvBgLV6za8h Lmyr03H6fEB/6046qmMFCW9nVM7fstck1YO33aCL97jrO2/FraZ7M3tuwOiHsRd e3lRey24/qYcebX0N5Kx8 2LYwMw8kVrU 0G0XBZf2XYxV4KJnISeSRK5uNrpWrEhB6I9rTtafvm R1975Dc8u2fKnHp5ZG04/mFq8X/5wTnMxEHO34YNrRazaeOGv5LRHAf5rwsX9x7qZV5Hdynry2RFAkXRg26Gz4QnP09NkfxzZHiPq1LWh4SNITk/Zus0Xw5PTHp3fuSZc3H9ciZ4Fl/Zy tw6kSRyddfJW0XBhirC wuiKVrAfRCi4eXxzVvDUvNUhakRofeyGB79dedLW2K6FFb uWX3GVlSZPCRnxPK8sD3DHtj856AJ/rUo/8ySg1HIyAE698HVxlPi/vgjwfaR25pP05bcj6HsnBs//WKuQcXxPTaFF7AJ6Eo4feAZ8G J0OH3Q19FHH14uWb3OIVwYxazXA0IooWCIU0AsKquS1vdX5G2gvIyVcxAKAubrRUqoLcl2kv6Vx1Mat0swmrZ Xv7xWYXMCasBgAVEqlUi0QC4laqWIJIIFILKAAMPdVwLAAoFKpFAolJRAWZw9TNi0b1arX9dJfA0s1z8mwFAAUJZ0OyT0zrG2d69fZtoPa59/eFFsEAIRRKhgAVs0wGGOFkiECAQKsVgkc3Ork3n QWqBUsAQAUQKhSEAJ7d0qy0 phZUsEdOaVzXKEiJiuJGJuvBV ks2J1 hBABWrVIxGn4KM9MzoJSHKqCMP9TJ7ZB cfVBtbs6gW3z ujl7ecKAABS8OJhOm4CAMDdHpXuv aXK2kM/L13Re/ p4Z3tg48LwcALI9IKSQAAMyLmAzyqbONAFJVADryxcePXuEUsGqWFtGVKyZm1Wo1SwAAUbRQKKAQYJVSTQAYJcuygHHlHR1WrWZYVq1mCCEMJtx7PIxSQQjz5llWvkKhBqowT0XEZiIKM4UKQgjLsAqFghGIzYEAIQqFQqEARKkjfVZckP4ylj4zf jdt1go1tIUc8lhAphhMGQFrpt47LkaAWB17suEXIXa0b6hiTz8aT4GoIEUJj6Wizs3sqJCCyuLKgGbl5LDAABgVYGaiM1EFK8dASjzjpO8N07u5W6lOWKdFWdiaJdBgLJs3NBEHhWfjwkAkKLEv XiLo2sqNACAGBzk98wpIw SGeJRMVCy8gv/1P1gBCCYkfqjCL6UboKCMsSRCHAYOHY0EQe TQfAwCQwvhoubibYx0A1pHLF4tZQqAgPlou7tbIigrNq7BZro9mbHbsKyUAAC7KVmCxmYgCKJnQaCEEZz5KLSQABiu UAAAIABJREFUBJgX0Zp6lFKjRyhqfAhcmYYasF2J4QBRAkQYjDFwjmYJEIKL/YQiRFFaOmdtcQhmCQBgrtVGiKIQ6CFKH9RMWQXg68uV6c fxWVhSIxPEHWO2TClm3/4H UioFLNScE938kulzr37d7xywFeJ7/q993A2YfSlSol10NTFCKYYFatJCAWUZArzwdza7PsW3OGhCBk2nOABPLkuSzGr/LB3MY8J2TusLsioWl3LhybtP 8lbV7q jYJcVJe8fE9JnjMft0llbNCcuAZvhEMKOm6jSwgJyUV0WMBQHm8Sb3ESdSNLUBCcVcL6t6fPFOgf gjpJ7zNB2qtuLZBpXadytCFoZJhgzGLgSgxk1Q4uEwMkffiIFQ5mmBwnFGr3KE8LkpHE8hC4YflOpEnXvJ4G89DcsizM14fNHhgKIu2l4qMqONQxh3QYWkJOWXR1HS4RglmgoIGpNYcd5WQXAKGNfcxLVmc9zoKltbQrkWgToEI5ztfODeXgrH06Enb6UQF5OPsEMg2lh T6IsCqVmlBCkZBChFWrVSoQi4WUSCxUKhlaTNN0JcfCBKuVakwLRSKBQAAAjErNCjSDBAIEEG1iIqZYBrOli0qEAFC0iYlYDQgwCwBCkUhMCKtWE tWLlYAVGs3B1HoYy3Ho0qSo5CIQoQUZSZGx8YrCatSqgktFIrFQhrKvBIMAFrLMCrX8hCtyxRa7UgknRceXeh6ftGU0XeeZ6tM h28uk2HuQxCaZNi2LIJ4f qSw7RK47mV8zkqzVqEQIUTdECTlECgEobdJriWlSMCUGIpmmKBkCEswefYnyHqIAQTCrGrHA2hbNj2XAClf/7eKFDx3dSv4Q3AkABYKJprVlCEKIECAEQluvjUXmGtcdBNABLkICmiidmLFOFKMNVfkdUMaImrEpNRBaWYgqrCpVIaMY53RVYOErKLr qs2LDjh7YPmX8/GOKVsNdzDHDYABAApFYJBKLuQVqzLAYUOGzyLRaLXo0FCGBSGzeoIeb5FXk87cEv3kakVbL5fNGErGQQkLrLq0kryLj35DCm4vH9hg8upPniI6e/zf9jzx4fnT0qLVX3/B2bkgAAEKhgAIAZN5isKsoNexhBla/lCUzjT/raGUqrJhlVBh75YbadXy3DmM6wK3AhEIEGt3FYrGIrhCd5D97lGXRpXNjiVgs4mQRjEGdFpHMNO7WprZAKDYRi8UVUqlECHnzNCKtlnO3BiIAAKFNV1fzjIhnhUKRIjnyZa3m3TXhJTzoNhOAwNzO3s5OUjMbZEjSYoirKPVulNzg8sW8isvA9ZpYc6VDZPWJ5jA8yU2MzRTYNKvDaSio52AJuZmaMQpl3caR89UtaNi6PmTEZ5SMISrmi7x9qpUfvcNdzTMiE/IomrAMWz53hGUw0EIhTVEI0QKhABGW0b08RzDDIoFIQFMUQoAQEqDSFb3ikSBCtIAqucMaqwqVSCwRUYCAIHOH2jRCmhQtWk3aP9f699nz90sm/TLLxUx3chRF0QiAxaRYcwFNIfw2NU1Rz6WFOQUAgEydXeopU5OzMeisv/rbkbZ1czGLO73rz6RsFQaRdZsGwjKDAkQIAVSxymgDzklOU1i3bKbR08S5VT1lavLrGh zvkO9IAzLsBizGLOkbJeKaIqicM6zNIX1J83MKEAAyLSpSz1lamoO4cJbNDOnaQGFkAnH/2uWAAIgZfipbsuNVYVKKLWjQ1k7UjZtHMrVo/9Zp6eV2CUEuLk6ogUUxz iEBBCKuyS88fRDGYxwZhgrD3aPwrt1U5s19ipRRPnNt0GrV7YXZxwJ ItJgUpD7Ks no4mwFt233MxJK3vE2az/l20tA2TRra1Hfr1a HRU5MWmHxQJRRac6ac18xAVA8vfhbQoM5qyb1bu782aRF8xzSjpyJLwJQPA04/Mx25vIJXzRtUiacFKQnxyUlPUlMepL4LCVfTRSvE5PS8/i7cpoCJKzduGmLjj0Hr93p93/U/R OPFUAeR326/GCLj9tmj6gtWOjxi59JyzaO9 9FmefwvhTUsUX3gv6MuEnY6t6s0XxdN/BvxvP 2H9APdmDRq27jFy2fhmJoRk3T5wJLfn7h9nDmhp79D4k76Tvtu/qI1Z8eCwMiGKpwGHEup/vXzCF82afjFlyTeNU347k6RAoHgadOS5TSUeAACZ2Tm7uXzSwkqETG1aurR0daorLjaC2Glk4JVzQRP1OPtGmzm1bOne0tECwMKxubtL8ybFzQES1m7s3LRd9wGrtm0cSz3wPR6v65yEdn1IlvRcmEXv b0aiJCwycCpg4vP6xTGXjyd4fDdyv/73NnB1WPKWg/ziIAHmRo70h7fzhrc3L5Fj4k gywfnAp7VWzfyvni40ev8MnfLWyc8tvpeAUlECAQWzdxa9WyZT0RMrVu6dLS1amOuMxKGaIoVMmLhJm9s7tLS82npaMlwkAYpVKhUKjVDMaYIWUnldoWdUjB8wev63H1yKbb/00tebHd1Hnelpl1Tq5cF/rXpmUnxTN 8G5Vq8LzBJckp1Ao1AxDuLaHEAIUzQ0c8mXnghTtfZYO7uBo33aI19oOzLXT0XkIeOuvdvDZEb9OSFU6dO1iLQAkbjnCa4Zd2aeYrMRMuplHbweJqVgs0tWlo3zZuaAitzXegzo42LcbMm9tByb4VHSejiVXflFmds7uLi1bWGns6Fa Xly4eu7SpLL1Qlf8cnLL7peXcTKCAAhGebJzQUXu6xYPau/YsN3Qees6q4NPR eSkvDBHRzs2wz2WtuBCT4VkweEACBgshIy6Wa9eztWyQ8vD6Qg f7rev00dhw7qZwd6S8XfT2kuX1Lrh6dLK1HRgC3IAaEVbMMoznSCAAV17b1icMb7Z F9gGr/aJfjywCAJIfH3Zqms9vcSwAm7R7/fHuGw8kTcmOvXX bDw7kouLVSq7z1bvneNQC3BOQoDvYt nJW BU3S5PUkKAYAq afZK r/uPh8wFx48/TI0m93JCkBAFTPfpq72mHzt6fOzdCE6/k2eWVY9NxzqiewOX HXJw 5tfzGSwAkLyolVOWFq6cu/fMNDPA2Yl/nd0XwGi0K4oKuKf09ERX/B4WnwswcZn96MzkhtyXDVdzNgDE7 k04pcnwMQfmjdUvGzTkt1TLSk2K bw rsMAMl7tHT8ovx1C/eenmEGJCfpwaldx9UVy0AZQtgUf69VDj96nzo/A948PrR4wfYkJVAAqhT/eavtfCvzIHL/Zk9gPwkAAIz47dgISNzfdeSvCQa pY0kHXae8u3MfVnsfx0g/LsB/YPfaHg72RPYt7F3rswc 3NAFS A8 jz6obXoqY/rz2asEaZLgsJfoVduOiKBL85PpbrvU6dn42YrLDDK aee8FwBZB9deyGqfeRMy3Fbx4cXjnros7pBB8/eoXHHV48f1uSEigkEJq2Xbj38mBO/5G/HRsJibvaDTmcojPPzeduuza35Fvios9G/1Z3fsT50nLyhisnI3 N5xOhTNjlc7yn74GkKdmxN0 ffMKOAwAQt/n6 4UmF4Zsj8gDIR15YOaxLy77zbw2asdfReUfL9kaEgmFAoSQWECBitvFAwAA8vbR8q9/3Pz9wuBL5lCQcmnLt97SNwQAlDz1lwcsjx1zQn5ccHmD35UbvgW5yWFndkd3ml76EHl5deeOvut3Xb4mAIhYPrhfkFzkMkt6opgfn4AMH46f35LePlo2a9tWH6 rl82hICVoc7GeBkPU5ps9gZ7Fdjw EhL3dx3xazxv4dU7ftn98uL19NKsvn207OutW33mXQ0yh4LkIL9vOP3J20fLZm7dusHrSlBxvu6 IQAIECCcdvWn7QM3cPw8Wjaw36Vsg7OsfLbb53gP3wPPpmTH3jp3Jp4dVfITm3H0Ri3vo2dait88OLTya9316H8HBDS2BABECQQVG WKA3Z94miPRmrwpDsq81fPJzYun/bll31bdeyjLMrr98kAQ1LDjFLFEAAkEIvL9tmo CAa0CKxsHiDgbAYaBoBwWqliuWe4rggWKVUYQBKaCLSuvKHyx9z0xpY6auCS0QkplhOGUooFtFAWDW3cV3SKJZHBfUqfK1uKroI0Zo7I94HCKtSqpHIREgBEO6LgMIMCE1ENBBGqWSoEgOVfgVWqWRobdYhjErJgFBc6RgdZpQqtrRaYLVSRYRiEUXKheuVIin9ny85wiiVLC0WCZA2sR8XCGZxxVMHHx8I5jZHK zcE4IxoQQ04sIJwZjQQhpYzJYNxxgTRAuK99G5r0IKMGbZ4mgVRH28wBjTNE3 tYbj9r8pgQBhlsW4jF1KHypjC4KrjgMAfNFqAGt3f9V31AIWs4RlWMIQRo0xi1lGrVJglmFZpuSvaS2Lh2GXu/QaoVLkpyRE18QGq bINwckEIsElEBAsWoMrEqJuaVKTAggYYV5eskzFAJMAKuVSgYQLRJVGha9CyiaRixDAKuVCnUNyjUkFQMJMeL9AyFaSDMqBhdvNCFaQDFqNUMJaQoRVs0QRAsoBEAQAsKdZoLyC eIFtCMSq1iQEhTCAjGGAMt0Nem/CnyxteeHCeHpUUCBJhV878Lb4Re0GyNkjJnqAx5HwkhRAiLNeUKEwCq5GS1Ee8TFQxHNKspFM1tlyEEhGWhZIxLuK3ucuCNg4DbEyfFR2GqFPWB8Z5uE0C0SAQMw7CYYEy4I540zZNXhGgBjdUsLrOiVZOgBCIhqBkGEy4pomZwDbwCYFAqBhFixIcB0oywir/SIhGo1WoVCwCIKhlTIkogoNSMUskA0NykvuQRSigWIbVareIGsxQlEBjwTj5firzxeZJDtFBE1GqlggGEaFpAYePq6juDsLjsujvS/6UjhBBVekgGIcT1Jcau/MOgrOEQQjTNvVWmsQsipOTFUkRx yhlHuaLAwghgjnJCChKD1E1AN0vY1bAu/TllEBswv88RQtEtJafESU0Mang/QfRQhHN74SJEoorPlEpsNLXcolQApFYowvWvOHOUzMrqFfh67ukwkeI1twZ8T6AaJFJ2VtEK3wHoGihWEtBLGPYyjK1/YjKVw1KKDbRFs6XIqLFJXqV/Z8vuUrBgv 9G79qEghRNPcOcTkQDBSNSo9EIsSdOCRc/LJNOeK8fxdXf65fLxut8iNGvDu0GY4QQnBxl4gQIESXnGPUnFtHFcyqJQ4AUFRpICEYeKL9Y/hfqPOEMColC9z7/ZgbLFMCQQ1Pij9MKkYYYcQHAeY5yFQhvORr5fhE2wWiZaPxJWHEu6BKVgnR0u1WeEprnMqBWqP9Q/hf6MsBKIrCLC5e8qJogVDvPc2PLhUjjPhXw1gl/l1Alf4x4oNCX94/9nOJNQGEaKFIbKKBWCwyoIsVOnhfvlPev9N7SOW/Ctpm vk7oRMddWwhCOyH3Hx0er79v3xQqX85 TdCDztWgf82P 8BdP0BNyLOejfSl3KB/ZBbEafmN/yX1yMjqo KfTkx67Q6qdhbgzz8UvC6Ea1Ma7hPEjv23nLsUqZMKg85tM3T0URnOG3T/YdfT8RFSOUyacqVfX4DmtTSmR nr45olH94OWTH/KGOJu kPS6Ivn71WorifayjGMQDINMOM9YEBASly6Tys5OcqjsIQ5afBZXYVyaVy6RX tZF1eDNcH2QmfOEdftkj6RymTT 9CrPOtXMg2G81RSftdx/flDix7MS3mc50Q5Ro6XB5ewov72mc424yas BG1XXnix/3OJlpXlsvyQmvwg044z1gQGBGVES7POTXKiajp TX4E7VZeSDvwuYToE5mD/sINjW Q2Pck3PjRTbhB0N4ypf04bUKPYZMGLD2d7 l9bE4rU62xqgeRo9dOn1GKgHEjx4/6/e3QTVsXOIl1hCOE06VnFs d1W/CvG vMWM27lrXWmdvDgC5d2aPmeS5YPefkv77T/iOqvcOkwE2O3jrBr ItzV/gZKBPAASmJsWRQb86ne3qpvpdILkhc8bPdXjq62RADF Xh5jJ8 9 1ZTggzizVB96LqDffds7fLm4BIvzwlz5h5 UMVVNHwwlLf3zKcG76 c6ERW4DrPMVM9xk71GDu197S90TXqSKMmUYGfmmz6BOamhRGBv2wqsWPNxn9PDbX kQ0V/l47lw/J1f/sp5rQ3pcr058/i0uMf3D9hH 4soG7kwQBXX/A9UfnvLllNiQZdux2xPyW3BRH0mrkvrNXMmVSedT1 7unt9bpodCk cCJTln7Nxy 8TTp1uEt/qn2E0Y2M UPZ15Jd 4/E3g36qEs/MyeHcezLbu2qad74Ymo3z5PjA8PDfp wdITpPPScc04PcX2n67dfyZZJpU/Crq4 EtHAQAI3ZacSz00tNg5ILId6p96fVkHEQCY9j10l5vxVFwbpCVdpq37MyRMLpO uLbfz8NOyCu/xngAnHfrJ7 1hy7c4tzQVQBtZmNrY2OmxwobW/DsyZOoJym5ALkpT6MeP03KY3Xzph28 iDrnjPP/xkql90K 2F4c5Fmei9q1O 7Hm83zVy17Y H4bKIa0HB4SUeY5DQaejykHtSeeTVy9/1alCW60r5MpS3avJpALSXE7r gOsRF7Z/vTT45i25LCTMx9OBKg7XUo QZY/FsvsHv24oBAAQNph5/NZjn0 tqlpTUsifx8Q iXr8JOrxE1nCq0ICAEjSasS c8FymVQeduKXCa05r B89ZdPTz47gtBuzBr/e2Fhcpk08/aR/RPdLREA0C3mnpTL7lwbbS3uvDEpWiqXlaxhVOCnJEuUpPWIfeevZcXcy5Ke GWiq4WGn4E3oi5sn73s2q2QrJjbdzf0d9A9FMe5N3f4rf31YkiqfnY0ND4AmHc68fDangGDfjx5NSvmXlbYvlkOQj79ecIFLbxOZcXcuTbGWtx547OYe1kx964N4lnjKQWq23XGuZt3s2LulPBA1x94I/Kcd2ONHYcfvxO5sGXxUpPQaeiK2w/uZcmCLy/uXUPey43b5f8W6CpNVC3HziNai1MfJubqKPXChtN9v 3xeFdfz0Fthn3re/e1zukWqt2sTYPCuNA0FQCAOlP6d55tm2aWiC 8zKN0LefPBn9ZJ/tuZJaeV76QvLjAGJVDd3drCpC56/cH1/dL/X30oGFdpu1J/nLV0cnOYlDHX76Z3WpgT0sKAICq3W1o69ybVx4rAaAoeEo36/ajN72o8K4u3XTS1rNezR/6zenmOWrAxht5NhYC4JP/HnjQBnGTUUF/BF6ZrMd97HqgLG Ggrb12L1titXFVZ8NnLE5/9MpxS2xhUt3x4zIvKEb7ktvp94 eWx2Vxuq9JnxfdTbJ4/qMe80Nc5nf6lf88r5MpS3avJpCPjKCQBtPdg9aaFnL8fhO3L6e69ub67tcQ7kTdiuuVcsl/0wuqmAdhqzaoVNyDy/0NeGjzKQRdsf9nl3jd3tOXBk3y3R7Rdv29TJoorsatOTz45Am0pywzcvmNyx70gPnzDnb7b4djBHwMbtGmPt1rPPKbny/rImrl2t3br2CZJjLfwgRBFCAFm0 eHn77o92e05YGTfzTEdlmwt1ZO2GeKetMDzC4ehO7I9F nk7UOBthi4aGDWzplO7Xu3nXckqgjz6c8TzsT5j67Xumefk3Ll/WVOrbvUa92lz0V5Fas4ArvxIyTHF0z0WHxeMER3 eGUrD hj2r7pFHdvU5T43wODHn33pwQgiiKK4UawxnxsUJ7Y91ky59hcllYcpCvZ9y yftidfnYENZuXBeeS 9HpWWlJcnOHzkfq2uhj7KwNYd8eYFtnxNh108Nsi2S54HE2oLiCwcAANpm2lmpPOLGvc29ZKtmr47R5Yu5PJjstFyoY1 Xhjo9po4VBM/fFHg/OSMx8vK6nTGOg3s3pqEo4drV/GZj29WhAFDt1uNaKf 4EFeoo/EzcZ4 qXWK/4oVl6Li015E3TzhcyyuCHjl1yQPHw6lvBkIVK/b8B6Kmyv33nycEh/4046rmsJAWdrXMbXvt8g1Ye30aSP87jnO2vJraVvD3tiyOyDuRdyd31ZeyG4/qocdb34N5e2f5bPg0r6LsQpc9CzkRJLI1c1G14oVKQj9cc3J tP3LfLaO9/x/LKtN/k9CJWg4fSDqcX75Q/nNBcDMXcbPqhW9LrNF8NT0h4F K8JF/cf62ZeRRNcWU8 OwIokg5sO3Q2POF5eprsjyPbY0SdujY0YASJACGKooiZ24jBtaLWbgp88Dw1/NxPqx YDBjnaoY5VzH5QXsDHxeyhUk3TySJXd2shaRqcI7Q9YdB8YGCtGO W 4k5yryUx7evitXm7lq1R/zhJdNFBOsM7HiNAkobmzxPxWVEHH1933xJTwA502nJFpxLoAAc33zrnOxKU9CDq8IzG4/unt9pG8GtStAKIpCJTeDI0RRlCEUG1Ed6F XKkD7yC3tx2lLzudQFo7tv14x9 CCmF6bwgu0RgSAoqSjgc CfE GDrsb iji6sXLN/VZtFQXZqZnQK66Ykyt4ezrcwsnPLCs4 IxacOqDfNiZ26Or Bxgg8lYoT2bo1q1et66a BpT/mZFgKAIqSTofknhnWts7162y7QR0KpOOf6hKOzBu1sSr466/08iMWfvm6d4UN4oEfyvhDndwO6RdXH1S7QAlsm9dHL28/VwAAkIIXD9NxEwDOtwFAuv aX66kMfD33hW9 58a3tk68LwcALA8IqWQAAAwL2IyyKfONgJIVQHoyJehvBnIZ82AzUvJYQAAsKpATcRmIkpncSB5svUrLtz9ZSx95pvRD/Taes8KXDfx2HM1AgBclJmsAsqmcUMTeVR8AQYAIIWJj Xizo2sqFBd418tevLZEYAy7zjJe PkXu5Wmp2urDgTg4dGSFC3SUMTuSyxCFE0DaB89kQu7tzERihNoQHh/NS3hKJpQEwRQ0zMTQU0XdVFdhRNcX/18bhqYHwaIVYREyln6JLIyMpZq/73WO3h0gJSkihN6XHjI0UDYt/EZTIUTQNSvlFijgdCA0KIomiKxoC4C9JpiqYpGhDOinyhRDSNAL98nEE b24nptPe6QhFpf1bRFHGVxE EAxdPNTelyvTnz Ly8KQGJ8g6hyzYUo3//A/yidTeqEhKXrgN9nlYue 3Tt OcDr5Ff9vhs4 1AGX9XDuZn5YG5tlh06f2QogLjbAAnkyXMxxtrDuafYN6mJb1Ih5u9E6BC06SvX3UseFOiVU2HdBhaQk5bNgCUA83h7p/87mVqxjVQ9vninwH9QR8k9Zmg71e3l0Ypq7g3xyNeK6vHwwVDKm EgBLNEc/kgURf7l8jLKgBGGfuak6jOfJ4DTW1rUyDXIkCHcEN5 0f5rHqQXeFiUEEDdxcrAKq1W0PRvbd6tMLcfnmZZTOt7g4qB5ZPV7ueWu1IJJ0XHl3oen7RlNF3nmerTPodvLqtajW1CNckUfoPAALNV830hBTH0 dEECHlBFatgGHxCVOgwmXVKP94qf584WUT1XesTLg7p7TxoOGHu3Wscrjmf73Z0B/GRfaPFlUMSgmrUhORhaWYwqpCJRKacU53BRaOkrLDMyYrNuzoge1Txs8/pmg13EXXvuDbp5EvazXv3kAEACC07tJK8ioy/g3hC6/wOKIoJDbXdx6AJC2GuIpS70bJifqlLJlp3NXNvPKjqDD2yg216/huHca0h5uBsfk6O3KSnxz52qxjR7vy66U65GsX8248VILA3M7ezk5SQ8ddSnkz9FHmVVwGrtfEmisdIqtPNIfhSW5ibKbAplkdTkNBPQdLyM3U9KmUdRtHzle3oGHr pARXzoUrJgvQ3mrLp/vDTrqkWmLsXtm2R6ZPX /ZMK rz6pVR0l8ZvkNIX1J83MKAAAZOrsUk ZmpyNdaWrDXx2pG3dXMziTu/6MylbhUFk3aaBsKyvGUIIIH1mxrx61jBqtF6UAZ/ uvOlPz/8Ceuwo456ZMR/H9qLldiusVOLJs5tug1avbC7OOFOxFtMClIeZFn19XA2A9q2 5iJjsVV2MR55sJJQ9s0aWhT361Xvx4WOTFputaoFU Djjy3mbl8whdNm3w2adE8h7QjZ KLeMMp /7fbJk1xLND63ZtOo9dsPaHVmxoUKyu/WwAJKzd2Llpu 4DVm3bOJZ64Hs8XgGQHXboREHnnzZ91a FvUOjlh7jFuye765pLgvjT0kVX3gv6MuEn3xc1RtKisQDv8c08tqwfoB7U7sGLt2HLR7T3FS3/BrgAQCQmZ2zm8snLaxEyNSmpUtLV6e64mIexE4jA6 cC5qox9k32sypZUv3lo4WABaOzd1dmjcpbg608qaDZm36kCzpuTCL3vN7NRAhYZOBUwcXj sKYy eznD4buX/fe7s4OoxZa2HeUTAg0xNG0d7fDtrcHP7Fj0m gyyfHAq7FVxm145X4byVj0WBm7 zu0lLzaelYx/D1Rt56ZOo8b9MMy5NrfcL 2rT8pHjG kUutQxfHkL5snOXFK5rvAe1d7BvO8RrbQfm2unoPMSfLo aPHbErxNSlQ5du1gLAIlbjvCaYVf2KSYrMZNu5tHbQWIqFot0dVm8ehoOQ tFdeyut/6686U/P7zQaUfeemTEvw1Iy39VQPuA1X7Rr0cWAQDJjw87Nc3ntzgWgE3avf54940HkqZkx946fzaeHcnFxSqV3aer9852qAU4JyHAd7HvU6WuFFUp/vNW2/l e rcDHjz9MjSb3c8U/KHo8Ls/AZffbV3jnUtAFXmk0Bfr XBVb2ZbNFzz8mewL6NvXNl5tifA QsAJA82copSwtWzt17epoZkJykh f2nmU0PBVFBdxTenqiK34PCzXkmbjMkp6Y3JD73Scgwwcgfk nUb89w2zC4W9HIO8fluyeakmxWU ObrzHVCH/3XkAAJH7N3sC 0kAAGDEb8dGQOL riN/TTACYUdwAAAgAElEQVTwLW0k6bDzlG9n7sti/ sA4d8N6B/8ho83fvDo8 qG16KmP689mrBGmS4LCX6FXbjoigS/OT6W671OnZ NmKywwyvmnnvBcAWQfXXshqn3kTMtxW8eHF4562K6rumEobzVKJ/N5267NrfkW5J3r4knbWZqLScpfCKUWuuRuM3X3y8QXxq5KyIPACJ/mXPq80C/mVdH7fjLwOtnyNtHy2Zt2 rjdfWSORSkXNryrbf0DeFNlxcsjx1zQn5ccHmD35UbvgW5yWFndkd3ml4m8ZdXd 7ou37X5WsCgIjlg/sFyUV89YhPT4NhqB1rph7x8qwrX1r4Mbi31WFHg qREf81oI3Lp335Zd9WHfsoi/L6fTLgn9bHCCOMMMIII/5HsXbXtL6jFmDMEpZhCYNZzUetUmCWYVmm5K9pLYuHYZe79BqhUuSnJEQbr 81wggjPjCMJ6j RSi7uGg03McLY19uhBFGfEgUv0drvHjkIwfSoPi70XAfNYx9uRFGGPHBQAgBggmiKESB8WLQjxicpTCiCCBkNNzHj/8Fn6dGGGHExwJCMEVRCCFjf/BxAyGEKIrCBHN2MhruI4dxXm6EEUZ8QBACFPDvvJau6Jb/akTNogK9POZAALjMPTS6DFcizWi4fwbGebluCB28L9 p6CfNCD1B20w/fyd0oqMOv3YC yE3H52eb/8vH1T t8uJHnasAvrzU8HzY7VdRr6rB8l/GJxfu0V8lFfKrKDBkJuPTs zF/yTLL2j4bQx8GX8ariYp9OTHrtDqp2FuDPPxS8LoRrUxreIglduy95dilTJlUHnJom6ejic5wgW23JVsPRP0llcukzy/5f9/bQZcjTqCcvjqiUf7h5ZAd84c6mryT9rgg vrVaykGvuSrHwziAZBphxlrAgKC0mVS dlJTtUdhCHLz4JK7CuTymXSK33romrwZrg yMx5wrp9skdSuUwaf3qVZ51q5sEw3mqKz1ruPz8o8eNZCe znGiHqNHS4HJ2lN9e07lG3ORVH4K2Ky 82P 5pDIL748fZNph5pqAwKD0aKn83CQnulKDWLG3qGR3XZFrFuX54UtLn9FMhcj/GVTOjv4jAK2RP4C2emqiW7ca0FZ7y5T247QJPYZNGrD0dL6n97E5rUzfMZWyEDl67fQZpQgYN3L8qN/fDt20dYGTmD ciBt160r/vWvF/AGTFq56YDlz267lLXT25gCQe2f2mEmeC3b/Kem//4TvqHrvMFlis4O3bvCL0MvRhWEwjAcAJDA3LYoM NXvblU30 kEyQufN3qqx1dbIwFi/Lw8xk6ee/etphQZxJuh tB1B/vu2drlzcElXp4T5sw9/KCqG394YChv75lPDd5fOdGJrMB1nmOmeoyd6jF2au9pe6PfyZHG 8T74wcJzE2LIgJ 3aSnHbXG52v6qze51LPX4UvLCEOhg7oat6DugcI/aUTtfbky/fmzuMT4B9dP IcrG7g7SZBmzcebW/NBkmHHbkfMb8l1qpJWI/edvZIpk8qjrt/fPb01n2dHzKiUCnAcMMEpfY/PwRtPk24d3uKfaj9hZDNTAJPmAyc6Ze3fcLhMeGNKoXx9e8PAedt vvbXg0ehB3x OPnW kvN5dq8IOq3zxPjw0ODvp 3 CjTeclYRwEGABDbf7p2/5lkmVT KOji4i8dBQAgdFtyLvXQ0GInm8h2qH/q9WUdRABY5HHgLjfj WOwFatQKBQKJUMAAGhJl2nr/gwJk8ukL67t9/Ow4xbCtMnnhbb88vHQzBQAcN6tn/zWHrpwS6sbOtrMxtbGxkyPlWq24NmTJ1FPUnIBclOeRj1 mpTHVuRtwdITpPPScc10DZp49UHWPWee/zNULrsV9sPw5iLN9F7UqN93Pd5umrlq2x8Pw2UR14KCw0s8nCCh09DlIfek8sirl7/r1aDsEKJSvgzlrZp8GgDTvoc05aTsGjJdf8D1iAvbv14afPOWXBYS5uPpQBWHa6lHyLLHYtn9g183FAIACOp/9fvNxz6fWiEAwioVSoanD R8q0Q9fhL1 Iks4VUhAQAk WTY7tPBcplUHnbilwmtOa/gfPWXT08 O4LQbswa/3thYXKZNPP2kf0T3S0RANAt5p6Uy 5cG20t7rwxKVoql5WsYWjnBwBJWo3Ydy5YHi2V3y2vZ SFbbOWBt 6JY8OCVvv6aB7KI7zbu3wW3fwQoiedjQ0PgCYdzzx8Nqe/oO2nLgij5bKQ/d 7SDk058nnG7hdVIeXYafaGnwQKuqEkZ1u04/ezNMHn27hAe6/oDrEecWNeLsaD7s O2IBS2Ll5qETkOXh9yXyqOuXl5cvh4ZoQuEZfE/0//WJHQtLVK1HDuPaC1OfZiYWzajmFEqVGp1sRMeYcPpvt/2eLyrr egNsO 9b37Wvt0ixBGzWBCWTZva1/4NCxNDQSr8l6EROTZtmlmiVDtZm0aFMaFci761JnSv/Ns2zS3rLDOKxCbCfHr9DwGAAhWKRQKhUJVkh7BKoVSWeYCWZL35HyUyrFHGxsakLnr9wfX90v9ffSgYV2m7Un ctXRyc5iUMdfvpndamBPSwoAgKrdbWjr3JtXHisJo84NmtBO0mr4Dynq8gc56KaTtp71av7Qb043z1EDNt7Is7EQAJ98PmjNLx8PzSryUAniJqOC/gi8MlmP 9j1AMmLC4xROXR351lQ1gXa1mP3tilWF1d9NnDG5vxPpxS3xBYu3R0zIvOGbrgvvZ16Sx2V1tqNJnxvdRb588qse809Q4n/2lfs0r58tQ3sqHqzLuROTZtmlsUZpVwlQ5l V6U966XhQ8pZt1 9GbXlS6MZO2HuyetNCzl PwHTn9vVe31 Vz6E3YrrlXLJf9MLqpgHYas2aV3Y05m0JfG97AIIu2G/Yv7h73U7 BI/tuiW6/eNumThZVFB9tevLZEWhTSW745gWTO/Yd6eET5vzNFt8O5gjYuF1jrN169jklV95f1sS1q7Vb1z6aC0q184Ms2m742bvrk92enJ5LyuhJWw9xT1rYr5fjsB05/b1Xt9PB23sCwSxmSz EUJIBiwZk7ZzZpH3vdvOORBVhPv15wtk4/zHWrj09jsuV95c3ce1q7drFI1BOENJ1RkxQf/wIyfEFE79ccl4w5LuqeaBtJ/RRbZ88qofXaWqcz/6hDf7lh1CqgQqGwxjr/TK8blv8Y/29/lvE2hvrJlv DJPLwpKDfD3j9k3eF6vLx4awduO68Fx6PyotKy1Jdv7I VjtjSPnWJGytDeH/ByFXd8Td2 cG2FTmJkHEmsLirKwNYd8eYFtnxNh108Nsi2S54HEunbZoSVVy33KvH4Ff/wY lrvlTomOy0X6tjXpaFOj6ljBcHzNwXeT85IjLy8bmeM4 DejWkoSrh2Nb/Z2HZ1KABUu/W4Vso/LsQVFruBRAKaohBCtEhsYiI2EQsQmDhPn9Q6xX/FiktR8Wkvom6e8DkWVwS88nmgPb98PFh86COKpbwZCFSv2/Aeipsr9958nBIf NOOq5rCQFna1zG177fINWHt9Gkj/O45ztrya2mfzd7Ysjsg7kXcnd9WXshuP6qHHW9 DeWtfPhg28LMPJBY1fpAt10UXNp3MVaBi56FnEgSubrZ6FpPIgWhP645WX/6vkVee c3PLtky596eGZtOP1gavFcM5zcVAzN2GD64VsWrjhb S0x4F K8JF/cf62ZeRXYr68lnRwBF0oFth86GJzxPT5P9cWR7jKhT14aGjyA5PWXrNl8MT057dH7nmnBx/3ElehZc2svpc tEksjVXSdvFQUbqgjvL4imaAH3QYiGl8c3bw1LzVMVpkaE3stiePTXnS9tielSWPnnlt1nZEmRwUd TijLA98z7I3NewKe6FOP/ssoNRyNgBCsfx9cZTwt7oPfMwxIUPvILe3HaUvO51AWju2/XjH34IKYXpvCC/gkFCUdDXwW5HsydNjd0EcRVy8E/fEsV82xhyhaIBTSCAirVKo5ojADACp1UV76izTylgtUKpVKrAYAAHVhZnoG5KorsYrq9Zz/ zTBzikbrr/FNDBKlWamhNUKhZrLNAHgOh VSqVQKIXiUn MQnu3RrXqdb3018BSkTkvJBSBoqTTIblnhrWtc/06225QhwLp Lh8lVLNtaOEYRgGY6xQKBUsABKITcwbtambJ733LFehFAhowjIsAUCm9VtXlp9mQakVBSwAEorFtOaFDcyo1QymlUoAYFhlwav0DJSrJpjjQYVYAFCpCvIy0jMoLTxohzL UCe3Q/rF1QfV7uoEts3ro5e3nysAAEjBi4fpuAkAAHd7VLr/ml upDHw994VvfufGt7ZOvC8HACwPCKlkAAAMC9iMsinzjYCSFUB6MgXXznRK5wCVs3SIrpyPcGsWq1mCQAgihYKBRQCrFKqCQCjZFkWMK7UvxJWrWZYVq1mCCEMJtx7PIxSQQjz5llWvkKhBqowT0XEZiIKM4UKQgjLsAqFghGIzYEAIQqFQqEARKkjfVZckP4ylj4zf jdt1go1tIUc8lhAphhMGQFrpt47LkaAWB17suEXIXa0b6hiTz8aT4GoIEUJj6Wizs3sqJCC3UYjc1LyWEAALCqQE3EZiKK144AlHnHSd4bJ/dyt9Icsc6K09cHcWkmgLJs3NBEHhWfjwkAkKLEv XiLo2sqNACAGBzk98wpIw SGeJRMVCy8gv/1P1gBCCYkfqjCL6UboKCMsSRCHAYOHY0EQe TQfAwCQwvhoubibYx0A1pHLF4tZQqAgPlou7tbIigrNq7BZro9mbHbsKyUAAC7KVmCxmYgCKF2FrBwfZz5KLSQABJgX0Zp6lFKjRyhqfAhcmYYasF2J4QBRAkQYjDFwjmYJEII18zRAiKK0dM7a4hDMEgDADFsSCHqI0gc1U1YB PpyZfrzZ3FZGBLjE0SdYzZM6eYf/ke5CKhUc1L0wG yy8XOfbt3/LK/18mven/Tb aBF5hCBBPMqpUExCIKKIRYQgBwbmY mNuY59yZO/QWJiY9 kkgLyuPEJyZD bWZtmh80eGAoi7DZBAnvytpuQii/bTT23ueWfRxA2R SAScxcZlBKJgBsyFQ/AEEIIUQhAWLeBBeSkZTNgBcA8/rHtiCPPWQCgKES41RdKSB5fvFPgP6ij5B4ztJ3q9vJoBeIKQ6ko7WYiDMNoohKWYYB5vL3TuKMJRZpBhpYGiLDFowSSJ88HcyuTzBuzh4WKaJNu/SWQJ89lWZyWD Y25tm35g6XCikND3rM0GoWpbwZDkIwSzSZJ2oNjTgvqwAYZexrTqI683kONLWtTYFciwAdwrnyU7Gc5GKstfxUDCfCTl9KIC8nn2CGwbSwfB9EWJVKTSihSEghwqrVKhWIxUJKJBYqlQwtpmkaKKrCI1itVGNaKBIJBAIAYFRqVqAZJBAggGgTEzHFMpgt3XkiBICiTUzEakCAWQAQikRiQli1mli3crECoFq7OYhCH2s5HlWSHIVEFCKkKDMxOjZeSViVUk1ooVAsFtJQ5pVgANA6mUDlWh6idZlCqx2JpPPCowtd/5 98w6L4mgD DuzDaSIBVERVLAgRjRqYk35LFFjjT3FEmOJEUuUGDUaNcRYYiyxJhqjsYs1Yo3GikRjRaMiRQGxHaJS7253Z74/9u44jrvjDlEx2d/Dw8MOszPvvO/0mZ3ZMW5g7xO30vUu7X/dP9 OuZwir0pxbtqE2n60Fw51yI/hv0TKEg1iUQqYwQyrCEoBUF6FzmClRiWEUoQYhsEMAKKKPWwJZmsTFVBKqKVPi70pih3N3SkU/KvkYkfGpxLfpDcKgAEIBUM9TSlCmEUIgMpKG4/ya9i6H8QAyBSxDDYOyWSpkKCcF/kpKaRHTWW9SHlPLwETfY4OcW7KpbtsaX9P8 lXKe1a1PqVC/r3GfFbdkjPV7x4gecFQWARABBJJsBwPMcAAJAnCRfvlKr7ll8pnucwV6FZPfd7F5NyOC735sU7pWoZtrVx3k3rety/eOMxBQDkXveDjUt7JH8z9PPDGkPjghmeN9TEmBMEQRAE3uQCwHGcIHAYewR1a8AnR118QMQ7MUlStSYhnhgQm188knV132Gx3ofNG/dpBEd2XcvC2CgtIJZhGIQQZ0otzUq6kO7R9PVKPABiBUEQeA4DiHcuJknVmtYzzN5iTnARBMGisSCSRAAAsbzA5d66eKdUUMsqPJFkwno3qetx78KNR5Q8jr94p1Tdt6t5cNikh7jCL4Nk3Sv5VqrkUTwLZMijdtd6fMqpSxqn85d0P/YeKR/greiLL1fHsBmeZiRce8BWqFlGkZAt7 cFGQ8MfRTs3cBfuaubrfJKRbgXd8/Uh7BMF31yo2A iXtMHXav537vYnwmNk6omEFliQDDcQzGCDEsxyIqS/an5yiRZMTyykIMIIRYlDejhwytE0IMi01nWBN9jg4JHjwGBBS5 5VmEDLE6Fm3/4oR3muHj1rh0f XT4Pd7EeHMWYQgEyoUXKWwYg8SUnVlg u7Y4BAJBrYHB5XUpSOoH85dfT38P 8oktOzI IcFusRFL/kxM1xPgvRtU5sw6BYhSCohxYJhOHiWlar2DahrkdAmsW16XkuT44pmjPEW5oJIsyYTIhMjUvElFDMaYPLqZqvWuU9MNAwJArjWCy tSUh5Rxb12TXeGYTFCLor H8oUEAA1009Ra26iz9FBnh39zO2IKzTwy1eO/rOXnhbQLqWgjNURw2JF/wgjoJRarJLb9mPozBJKCCXEurcXivViJ1SqVr12QGCD5p2/HtNCiD9x4Qmh2cln0sq1axPohtiKLT78OMD4pkvg0DH9uzUIqFKhYkirDm WfhhzO1OvM9v1TfPVh9obu9feqjB00kf/qxnwv4Fffl4taU1EXC6A9kbkOsW9RsBb/ceN9EtdGxGXC8BX7b7m19AKkQuXJXoG163ToG5QnYqu9isLxHlWC6zRsEXHyQtmf8Sd/HZtnBYgPerXDZktl/4wpGOdihUrBbzVM3Tx6PpuFIASmhO3JVr7v7DR7aSzm68W9mWLNuGXNVeqjZo9q9urQVV8g1u8N/792q5AH0b9siG76aLvB3cMruIfULfdB6OXjm7gka9ao8b uaTXaR/H7Pg1vtJnU/q3rhnwVv9xo/yT12yOywUkJlrqYd3WuFwAAORWKTAkuE7tcjxyrRAUHFSvelnBmHuE6j137dse2c BvW MW/WgoPpB/p4Anv616gfXCjBWB4grrehtyvyZffGZWRvj7O2TsC4PTYveHuXZelSryjziAjp93MW4Xyfn2u6Ie35fTP7g7UC/em0GTmvjfmHnmQeGuptpM/bTLrV8a7fsF97Z68yWqPvGOr1gugrmE0U/DrkP GJMteTfIuK0mGURCN4BIXWDgsrzyNU7KDioXvUygtlMGcLYNDljws03sH5wkOEnyN8LEaCSTqfVakVRIoRI1HxQaW06h2bfOvOwfLs2gW7AVGj wcemD9tdA0fOHVpm8 TpJ/ ePXGzMOS7sLqlLN6nxBSdVqsVJYkqdQ lFDCjdByyYrZHahuFT jS2N/31a6h0xpLByMuZyLIK7/A LTo08/ffsVjy47kYXyKzq9ZU28WkBDUI3RIJfO3pLSEB0zNNq39PFwFgbdXSlFWzPbI3JCpYZ0b /k27DpyWmPpwJbLmXamXG0H5VYpsH5wUO1yBjuG5C8Xv /fvqe/ebmw5z9fuObr5WazcwiAEpQZsz0yt/708Z0b Vdp2G3k9CbigYjLGdTk3qWxn2 DLqHTGksHtlzJBEoBEEhp8Q Ymq1b xeqH5t6oNlJpx Wb2 wY9/ezItB03rGst3yClHG3OK0cqoEyIAZVFWZIMWxoBwHJu2xE/Nr0VN851Dqx3WH3HrVo3DgBoVlzUlkHhv8XKAHLi0m83tpi5MnHgw6t/Rmy JvVV/BK9vtKbXy8f7lcKyKPYbTPHzbgqMky TWv5RNInLxn5deVZY7dsHwKPr64eP3p gg4YAH3y4pFfVzK431g3YeyPiToAcKvToVUpgF5fR/YyBPBw8/CGMy7aW//zfHPZ5jdBfnLt O6Peyzddk9meJZmxnz14biMqaNX7vzUHeijxL 3LosgLMMARpB7aedfug4d0L4553IMGnQJHv33zoF SoDhvz8MB4hb8Gr3TbdBjl8zuov8xewJK4eUxXLa9XUzT0gANPP8pP5fZn81whj ue3Lt9noFmOGQSAnLw6dUmVu2M7IEfD4xtoJY bF6QAQKqCHhTeVrfl8/c X7WrvAQAAPX7b0AMSVjTruSreya 0kUfjRVtmNVEexi8 BHD2i47vHngMAOD5xrLNb4D85NqJfUP7/ryzkA/Abchz/3DouBo/T1sfP1V3N bYgfskWPGujZ/zWbjXt6FbdgxHUlrUmq9GbL8tKRlQvr/hsGvYuq1BwuMzayZ/utvucMKWfhxyj10zftT8RB1gxHKur45ZvreLIn/P3zb0hIQlDbuuSbab5loj5h8cYXpKGPdW79/KjrqwY0AVxWHG/sczAOKWvd5zVZytIHTxS8I3vjFrZeLA9GtHIjZfl98HABAaDPtmjMvvXRdcyASOubhy6Ib/7Z0z9GCvhX/n5n/dtPWC5zgWISSwGJRPOQyTf0/OTxr2w/ffjDmwxx2yk/fMHRsW/ZgCgM5UftOvHd2xLU7uaTelsg07Pjr2w i9M bsOzwrOyMpauvSy68PznuJ3tm/aGG7b5fsPcgCXJjUpX2khg/ NHqTUT/hOFK/r5LfHJ Ymfzp8XHrp/rztkJ0d b5TTafgGny/b1cFox409IWFFsx6r4mxmXof9m6 XG fT85L65PzEYfPmhY/cH kO2UmRcz5X5KdPzk8cOm/ejNB9kcZ0nXpMARAgQCR1/48LOs1Q9HN Yqf2e9KdTrLu5tLwjS1nrbw5MP3a0e1b4 Repn/J99YfLhW2fmuQ8PjM6snD7Jej/w4UDLYEAIRZ1rKFtOywO LHujf6Qr9sQzMnDWrbtl3d197R5Wa2r9PRgVeIYd8ZYk0bupSggIg6vUwBGF7gjOsKVCbAMAgoEXV6ZfuYMrkNlOh1egKAORfe6oSfITjE8gKLCzwWfL2gS/5X7IlngYW0Fo8FBNMq/ QFLCtRYE7gGaCyqCyPGypgewJYhKnyLKCyXici3oXDAFR5YDGRgHPhGaCSTidhk2nyHkHW6STGml2opNdJwAkFttERSaeX88oHEXV6ygk8pvncHYqR5v1tKzoq6XQyI/AsshZsyYISmVjuOih5UKIsjlqs3FNKCMUsY9iqQykhlOEYkIls7k4IoYhhjevoyiOHgRBZNnqzCKrkQghhGIa tIZT1r8xyyIiy4SY2SXvJTNbUFK4HwCw5a0YmLb0k3a9RhMiU1mWqURlUZYlIkuiXktkSflb e1ayvNc1N6mrXrotVnJ8ZefYoGVSjqtqeOHWIFnMctiWSQg63VEmaEklALisJXWEgAQRkAoEFGnkwAxPF gN2SXAq8zli4Wy9VOilcUMMMgWaJARJ1WLPjfZy AiqMgxHCMpJeIcaEJMSyWRFHCHIMRlUWJIobFCIAiBFTZzQT5J84RwzKSXtRLwDEYASWEEGBYR61pO0ab/q1Hp4QjMzyLgMii7W/hVRzCsDRKzfZQOfM9EkKIUpkY8hWhANi0s1rlWWJhOGqYTcGMslyGEFBZzpsopspSdz5s kGgrIlT41aYQoN6zhTvaQKI4XmQJEkmlBCq7OxkGBtJRIhhGSLKxGwiy5m4CrxeaIBOiVc0MMtzIEoSoYo4VJRI3rrHcxBAxXGQoW9lfGR4HkRR1MsAgLCpc4kwy2JR0ukkAEYZ1JtewZzAI1EU9UqvFmOWdeKbfFsx2vRvIzrEcDwVRZ1WAoQYhsVEnV19aqhMzOfdkeMfHSGEcN72GISQ0paoTfnzwdxwCCGGUb4qM9gFUWr6sBRhsy WTC9Y9QMIIUqUkBFg7EBQz5sitOWYFVxsv4YZlmes/BthzsXF4tIfxHA8Y/vuJcwJ5m9YPFp7vYCL5Ss2xbMvrcVjAcHypQyzvGCIgYjKUrdZLWBLgAKpUyl EMO7mJ8iavEMgBlOsJIjzUxaMExr/0T5ywjmBBdr7rZiRIxgksv8b1vRFXBm/3snfhUnCGFG YY4H5QAZhA2 15V2XFIFf/mVbnyVayp VfadXNvBV9ReXqsGY5SSolxZIcQIMSYfWVMKbW0hVU/AIBxniOlBGx4e2GoZb54oVTS62RQzhIgSsccs6w69FZRebkgNjYyWbibHgv6p9YOEDX3ZisKlaehUK1SaqXZtXjLqp Cjla9vSDUtry4wRgTmRin1zDDcg6vn6qo/PtRC8PLBSrwh8rzxiHVl/R9iS8azi9s74n89zvZBSGG4wUXA4LAqw25ikohMN5Ddp6I6u vLjKpqBQVy7acur3 daLxtgbN2T0Hpveo61rMrZHg33ruhj0PYqI1x1bP7 DvYt8duTYeMnXnzsi7MdGabf2rF9L5wNU/WWcQ/tzeYwtHdfN3eSrpSfblQ/sPJmufxTyKc3oAQG6BH03/KeZ8tCYmOi5iSocyRemIIa 3Ik32jYnWxETva1cWFUlvtuS0Aev3zmdb9/ piYnWnN65I6yN6U5YZ9PlbD5xVs/WQP7912hioo9/pFw2ydYZE3Fvx6AajHV94gKOyo9yDSj2qD3wm WXzkVrYk5d3/xdaEjpYu5RM15vDAk/cjxKExN9/9j6lX2K5/a8QihV/ czpntOLWBfnfz77RVve Sdq2nxY8td/XnhP a8cGH Cz9Fxu7dKqWrt/jyu7ANGbFNf7iSa9VjEeD9QxeF93r46/s9D8tvjv519rx71z cfVNn0x2x7q65F3euOtZ0 CRvx6LIOM T5r4AACAASURBVDF8yIpb5Wp3HBS6YlMA32XcljQnT1QxIacfmDfjQBFftouzemDKdpm1bF6tCzO/DD1xn5T1r5BepDTRzLMje3/s6VFv7i9j2TmhY85nZqY8MeQgp/RmS04bsL7v/jy3n/uvE9/ceJUEdVu2MHxl0vV3I25LzqbL2XzirJ7tUueDbkGbF142 9zQqj5JztmRvT/2xACl6s5eFSbMCR1zPhuAZN5OJ1zlIct /q5c1NefDz56D3zrt3izRlku5kkhETuB8OqYJds RGvDx47555FHzRbvBXiyFHQlanqoYBth1V2lpKEaqORifUSgu3vrZmxC3JlDmxaf1VWuX90DAVOx46Hz28OUaTDk8d6G4xdGBSlDGY 6PX/atu9BTLTm0qHTSwe/YveGQpdanfpVT1sxY83hG4lH18xdnOL7Uc arrbdgWQe/XHOtNW/H72d62BGouKTWwlxZ09GfjN6wibaZML7NRU5Bd83p63YmhQTrTkfuXt8W38WALiQL7enrO5mvBwQ XRbnHJoYmMeAFzbrT6lDKcs59gZj6aDpv95LEoTE3374Io5bSpxNsMvNj3wVdt/0fLJ7KFT5v9x7mzMhYORB86a37jCuFXwqVDBzYHtD3L2zevXL11PzgDISL5x6eqNxEzZvt6ckh 4Sn2mLv4rKkoTE/3g LoV/ep7IQCgfMXgQLj56/rj1 49iD0eseI6DQzx4anT6XI2nzid3 xoLv3Cabd3PgkuVbg Fcer1y9dT35MFffrl67eSMyQPJoMnRCSPnfE9GXH/7l2459DET9/vd3Qg7Caf5iKHQ9d H3BsAkHjhzVxByLCu/gZ3cUjyu8 XW/gHPfhn254/SlGzdO7vl13KKL2QgAkEfdHj9tP6CJidZEbfrlo1cKu9W8WGBqj9isiTlxsLe30GRm4uVozeXTf3RRxu7Y 81hO49EpV05dmpW95p8ieprqJhQl8tfNI4q3l69gEv5N nxipByLiHDTivKVRk8a2zLq0vadejc4L2xs049tDusQqVrNqicE3syVQ8AID6I/ifTp0FNL2TL3cFkWIdmxu66ovdrUd8bA3Kv982v37ZPWdu783tNBy1Lajtl/YBAAcS4vUfS63Z6w0upXko37/ZKxpF9V3UAkHtgYHPvRr1n37b4Vpep0X/ettBa5 Z81rxDr44zD2dW8GTBVvjFpgfP4Bb 9y5mdptxOvp4yvHNG4Y3q2A jRzQK/KPXfsGFM9sqrnenJQfgHH1yDj7/egBr7Xr2SY8KvDzubMauyNA2oQjfz6p2OntADeESlVv2c0vgfiVqn0 VsPinO/EZzE9fsfNKuf2MvB/VoBb5W60aet4/sSbEch9vLP4x3l/qJYzq08u8NG7YV83ci8QbJ6MbkGtGuGbESfvWeRa5Pnqdz FNbu2tEOnnu3mXm40fv7s159Day7HLunjHfLGO1s0utMTA o1867X7J3IBzIFxqfN0vkDy0VOebPj4O8z3/rYz4nP8lWeF5RShLFS yNkeQyeSonCemUdMPfPKE1MVFLkrA6xPw346Zq9Oza40tXKwq3o05dS01ITY3as23HN3o252NPHHbI02T7vbIo6tKWzT64mEzy8PbEt96dKHICUnpoBZXzLMlCm5cd92QOjZu86nXQv4eLe6Yuu HdpXY2B3PiD 7Nq9m1YBgOg0q 8X1f3xxOXYqOZfAwf1fSV781Vd7LsWl3r50ZFP4hthcsBl MekBe/mWcfVtP65e/LTBg3rM cv/07mrulZ Zl8h5OnNSfkBtIkr56/edjb 1t3UmD/WLbjCv96sigBAHp8eN2wV 8XaW5dOJe34wuPXz8ccf0TA2XQ5m0 KN7 J8bu2JDf9sF25IudLtny1svAwSSMB8FXH743WxERr9n1en7Off7L3/LT7mpbk3jy2KZGvF1LB9swXLu3r4yqmJWVa3KpB3UO6dy51efr3u88mp57fuXjqWeHdviHuz79qRoAQxhiVa979Dd2fk5Ye/ufWjR0LFuzTKZ/3qJQcgFKMsfEeMYPhVDM9a4pctOyul3v6Nxr21YhfR19pNftstq0QchPX77oZOWvzyfdOnTx/Yf/uvUccmQwXcx7cvQcZoqVPW 5FxBQM5xtStVT5Znv 7pT3z0f3vFiA3MSIYxlb33u1zKFDcsPOjbOjP7xhb28Acq/aoFz233/fzd9jsR2 /dVfR/WgnEhwd/HUX/alSvDP8q9av7ulexPvXTvuEgAAXdzq10NW243JKRxWf0H5sftr/cNmDmhVv5xhV3JarAsGYMq3/GHpJ26bpnfaHQ 13p05dd6ipI8GH3xYxHQ5m0 KKb JqceWXxs oq3vOAfjtRfWnVXD 5/tHr6xAwZkO/8AgJyZ/EgCACD6bJEKbs7dsAUAANirWhUXzaW4bAIAQHMSrmqEJlXL4ZOZL2SkhfhKQRXRnRMpegYzANrU8/dJIGIw48h9qSrPjQK7sRDG6gRKCcV6W667e tmbBqBhLh4vsmVGQObLz77Rz4PZgca0twzcwYE727SrsVrbTuGbv6k/Redhq 2nOEzQTIeZIG7t1v6yVE9TwIIzTt6QKYmgxBi3f0pk8eVrewJj1LTJfACkK4ueP2DzSmWYeqv7j6Rvbjzax5/Sd0a6o9Puqwt4tqQjfCt4qweCE3LBkl37aGiWPHBrUdQw6c0hrvP5FrDPL05KT/1aDpm/Zh6O8YN7H3iVrrepf2vcDACCfVgO64WPvLd5/WgdwY/nEph12f9K68h bMp1Ll614nZWzqPmNPDq8JvrbsC41TxTm0zpSWtIjeM2vHAP3JTEtKf7G/VxTnFbzDwPgzIFS5EnqAy3nX9UDQ25hiXH8gPHihwJQSiSClAPPqUiefh vynNANdDzoEgls5BuMJX1IuU9vQRM9Dk6xBmGBKynv4d590xKuxa1fuWCgR O2qCt2z3Y3nrekxsX75Sq1aIyDwDAeTet63H/Ytxjasu9KGkygTxqd63Hp5y6pKHinZgkqVqzEPeCCUY51/YdFut92Lxxn0ZwZNe1LPuLpllJFx 6vfZapfzznHbCtx6Mk3qgGQnXHrAVapZROl9seT8vyHiQ1/aw7pV8K1XyKJ5JdzO9OSs/4xMS7BYbseTPxHQ9Ad67QWVOOdPcxcOVyTuwksqEIFcPV xsupzNJ8Wf3zLObd5Tqv2gOvb3ydlCjDt8LtPvrXaVLT6ldjb/2ALlxP55gVbv2dwnf1Ygj5NStd51arphAADkGhhcXpeSlF5o/mGE8j4 FT25p2v2EaUUkPmYW7ofe4 UD/BWahG XJ3y6nBPReVpsF51CJWqVa8dENigeeevx7QQ4k9ceEJodvKZtHLt2gS6AePTok8/f2PpdgkcOqZ/twYBVSpUDGnVvqXnoyup9uaotTci192qMHTSR/ rEfBW/3Ej/VLXbY3Lte0OgNwqBYYE16ldjkeuFYKCg pVLyvYv4GCK10tsEbDFh2nzJ/ZF5 ZtTFOC5AetXpTdpMfZ3/SvravX9WgNu PXjqqfiml7s6J2xKt/V/Y6HbS2c1XswrRmDZh5dorVUNnfNuxfo1KlYNbvDe Ty1XEXhx5yru2OuOf3xeQP3g70q9dm4LQ27hd2nnlgrIuF6j137dse2c BvW MW/WgoPpB/p4Anv616gfXCjB2y6zqzUn5ycP4FJ1fs6beLCAhqEfokEqKd3L39Mlkr7bfDGtV379KSOuB4Z3K3jnxV4rsdLqczSfO57fCyIlbtTvjtdfKMYXp0yoZp3 Zd63ihEVffdKsTlBQww7NK7GUAnU6/9hCfnB8 rrk16Z8/12310Nq1mzRYcDc0AZuFGXFbN jrTc1rHMjP99Xu4ZOaywdjLicaSxHtvIP491m0x87T4x7xdUxSdx8A sHBxl gvzLGDQhpSU8YGq2ae3n4SoIPAYAmha9Pcqz9ahWlXnEBXT6uIud/r Kyn8bx3rS1gdyvuNWrRsHADQrLmrLoPDfYmUAOXHptxtbzFyZODD92tEd2 LknopfotdXevPr5cP9SgF5FL9z1vhZN x K6tPXjzy60qzxm7ZPgQe31g3YexC5ZMcW 7A1/982a72HgAA0OO3DT0gYUWznqvi7axDe76xbPMbID 5dmLf0L4/79TIAEAzYyYPnJA9ecTyiEFuQB8lntu fJtkUFLupZ1/6Tp0QPvmnMsxaM4l NPoTQOqKP8P33kvHCBu2eu9frtJ5Pg1Y3ugsOXPqxF5bTrq f ZdUSPjFoQdt/JzPwr2 Dd2yYziS0qLWfDViu UOe0dAHo0XbZnVRHkYv/gQwNkvOr574LEtvTkr/6NjP4zeO2POvsOzsjOSorYuvfz6YEXF/6zqO7nU3NCvDw0WQJd2Zvt3vRddzilCupzNJ07nt0KR4ndsujR4fH17 ky32fbpk5cO 1ScMHbcslWzMH147eiMSWv EYGKTuYfW1DtufnDe2eNmx624GNPRB4l/r70hISAPjk/8dP588JD9 9xh zkPXPHhkUXPg2BS5V2BdAkZTgoSa0R8w OMD0lhrXqtyaNANA7 xctbPftkr0HWYALk7q0j9TI9w Hjqvx87T18VN1d2OOHbhPgp1Pq4qKihE0c9Kgtm3b1X3tHV1uZvs6HV 0PCoqKiWG8h1/jJnKjGo/cmv6M9mXoaKikp9pSwa16z2ayDKVZZlKVJZkIhFJFPVaIkuyLJl u5byPBe1t2mrHnptVnL8ZfVuFRUVFesIQW8H3t385d6HpJhPClF3UL1EmJteNVzJRW3LVVRUrKM7 UXHRlDcR34Zv6NVDx4p4SADxmfVcCUatS1XUVF5blBKgRKKMEYY1INBSzCKpQjCFBBSDVfyUY9mUFFReX5QSjDGCCG1PSjZIIQQxphQothJNVwJRx2Xq6ioPEcoBQy2V17zZnTzP6oULxbqtWEOBEBMh0LYN5wpNNVwLwZ1XG4fzi9s7wnLe9JUHISpMHjHiZP9/DnbXljfrkfOR4zyfck7lf/ufOKAHQvBcf1YnP9W5AugX/Jz5JR7KcfZUnmBxLKVux45HzHSl32RWnpKw1l991 MrYQXEcu2nLq9/nViTLRy16fm7J4D03vUdS3mLpbg33ruhj0PYqI1x1bP7 DvYt8duTYeMnXnzsi7MdGabf2rF9L5wNU/WWcQ/tzeYwtHdfN3eSrpSfblQ/sPJmufRaZ6lnqwCfJ6K9Jk35hoTUz0vnZlURH05rw8yC3wo k/xZyP1sREx0VM6VCmiGlwTm823Fmf5l/OW3np72hNTPStPYu/ae1n54JXAIBS9X8 E32wk42r455lPrEOX3XCgXx21Byf2qRYrskrOuyrk3 /veJtj4JaeGb6YX2aj5 /8tLZaM3l6Ft7F09v4 diUSEWaDAEv/z5wY7n4hY2n35sxeVIb8bC87 GgslxvAdg1fNzkNZBSezLZk1aJ1su6zVT6g DPmr5Xv OEyKyOoRt Kxu0c6rtA7vH7oovJd25/s9P y19km32fNGVxfsuSPW3TX34s5Vc04VdiKbiYwTw/v07zB66Z8e767YNKvX0xwPKacfmDdjzoUnxf917XPQgzVo5tmRvT9u88m8iwBX5oS26TtgxKknhlzklN6clYcp22XWsnlNH//6ZWiHjz4bseaM/aNobOKs3qy7U6Fq82bMP0u GtWx/5gpZ7yGzl8yqXYhrbk9nl0 sUvarukd nzcpu/Hbfp 3HrQ8sv2rih8oTwr/VChavPmzJUlX43q2H/0lDNew YvmRhk1468/4jF fLDqADBZtVftMGlg62OrbhUnMWO6ordgvY7Cs/EiA626dbbct3dWzdjE LOHNq0 Kyucv3qHsgw5xOmzPkgj/c2HL8wylBoPOr2/Gnbvgcx0ZpLh04vHfyK7RsZAcClVqd 1dNWzFhz HrsgZ9mzr9Z aOeNV3N3W8kHl0zd3GKr IOJPPoj3OmrdrxR2IuBb3sgJqo ORWQtzZk5HfjJ6wiTaZ8H5NRU7B981pK7YmxURrzu/eFfamj6yTCBfy5faU1d0qGfSAfLotTjk0sTEPAK7tVp9SRjyWc4OMR9NB0/88FqWJib59cMWcNpU4m E7oIf86S1ED6t/P2r1GjrGrYJPhQpuDsxUy9k3r1 /dD05AyAj calqzcSM2X7erOOTXmQ9xtDd/x5UhNzNOq77rV4Q0bkq7b/ouWT2UOnzP/j3NmYCwcjD5w1nbqOuOrdJh37K1pzcf/eL1pVNtd1gXQ5qzcb7ij7zNxuo f/fPDvMxdPr/1 9tYs73cMh7M7i/V8wlTseOjC7wuGTThw5Kgm5lhUeAc/bHS3Uo6QV8vxMad/HVaFAwBgK36y9sjV8DfLIQAq67Q2M5JWc vKteuXrl6/dPV6TPz9HAoAyKPOe0sjDmhiojVRm3756BXllnJb5deWnLbsCFylPlMX/xUVpYmJfnB83Yp 9b0QADC1R2zWxJw42NtbaDIz8XK0JsY0h2GrHCGPuj1 2n5Aczlacyq/nBd/n//phANHj2ouH4v6toPdm81R9pm53UYt PnA32cunFk7Z/bWTO92du3oUqtT/ ppP89Yczg28ejquYtSfPsp5csO7q9tOndw2bud527ap7kcrTm5fJgfZ0t G 5M7dDNmstm rkcfaBTOfvRAqCyzQZvOxKluXzcpAemYsdDF7aPq6rY0f29jccvjDZ2XpRydDpac2n/3vH5y5GKPagsk2Juf18A9qY5cSn/Jj1eEVLOJWTYSShXZfCssS2vLmnXoXOD98bOOvUwb7hFJJ02PzrJLaBB5ZzYk6l6AADx/qnLWT4NanohVLqmufuD6H8yfRrU9HKkR0KJXqvVarX6AuM8mhm764rer0W90nqtjq0zddW37VPW9u78XtOBS2 1 WbL4EABxLi9R9LrdnrDCwMA4NLNu72ScWTfVR0A5B4Y2Ny7Ue/ZlieKMjX6z9sWWuvcnM ad jVcebhzAqeLAByr/fNrwXDt4Wt9BZRD0JAr8g/du0b4MB57A5g1Ft9GxPK9mB82iydP7Dc7ilvdRryfdabA401sWdwC/97FzO7zTgdfTzl OYNw5tVwHnvfPiOuGBAr5YjI/D74SvM7i8vkC5n9ZbfXX/vxIVMnwbVPPOSSvRarR4Jbhw8vJdp/exYpTW1WQRs5RMAxrtL/cQxHVr5d1/46N2wrxvZu3PocdSSEfu8Jn7XuwbLVO8zdUqlw5/NPvnQ QoGeb46Y8X4FrE/tu/Us93cy43Gz5/9umch2ceanLbsCIyrR8bZ70cPeK1dzzbhUYGfz53V2B2BHLukj3fIG 9s0ehOTwyo18w7pNk7kRpiWz/I89UZP4c1u760gyLnl2ZyMt5d6yeOad/K/72Fj94N 7qhw2e1s3btCGDKP1HGfPKX9fJFiUzkvB9KsUfHcR3TFg0NaNS64ch1l3KJLfltuMuxi/t413ujzUaN7vSkgHrNvOs1bbNLQxGyN hiK37Yw2Pj6H5tv9zBdv2icD0wPh 9o18woFfL0Aj8fviKbpVf8k0oRcDCcIQQhz Gt2 Ll6C9t15ZB8z9M0oTE5UUOatD7E8Dfrpm544N4EpXKwu3ok9fSk1LTYzZsW7HNTsTfRTcyrlDlibb551N0cd29fKTn2SCh7cnxp4 RveoQ1s6RqFPenSx1I6akZUMa3HIvKthz8AXdg1Oxdp5PuJVyMnDLvarVubaqzkBt/cH9Wzb4Ny2AAVPqV9 vq/vg9NseOUV0CB/d/JXnxV1/tuRSXevvSkU3hG2JzAcq0/LgvayV8G9hK7zPSg7MY9FbW6a49Kt 8e0vtkcnLj1xNjtv148L9hsyAvXzLuPq2H1cvftrgQT3m/OX/6dxVeW22fHju0p2xt2NP/Db59/RGvVpWspleZ/WW372LT86DTPAoVypfARfqvP9Z24wDc088LO4Z4Ow9P 2 piW5N49tSuTrhVSwN 6n2Sd/mLq54uCfxoUuH1Vl25dz/3Tgxt8qg39NMa6Xn/uslgDUPaR7l1IXpsz8/e k1PM7F089K7zbN8S9kEqooJy27AigTVw5f/W2s/G37qbG/LFuwRX 9WZVnO9BKnLGTP9 99mk1PM7Fk09K7z7vknO7D3LFXmObkrk69W3q7c8uKC n7XNtG9Hs/xw6tCWLj65D2yWL8RghlV EGLgzsbv50WlZOpzUi6c/CtNsiG//XRZM4M90 j nLt0a0zixQPrfo4314Otd TD3y/bed2RcvRvJs9wDAJKieNtcKH XuQ1wYVivbFJ/WHQlzseYU//RsO GvHr6CutZp/NthVCbuL6XTcjZ20d6pk cv7N 990iBSWDECgKLqCzqRKOTmHP/7h35UZY2330WspSTcef2bfQ4V5YBQKfT6WRGYPIdIiiLOlGmAAizHM CpNMbhkxE1GpFJi8KAADldmSRAOdbv5pb eZ7/u6U989HKV6MLD6OXf/Hk13dXvE8eAwadm6cfaLXlUdaLeYEnkEAsixJhBC9TAGoqNXLyN2vftnMv07fzNBqEWY5jgFJFGW2fO2qpco3sxJ riItw3IcW7BoiTkP7t6DDNEyF9lyt4EubvXrIasd8 sIRe6Asj61KqI7x29pAQBo9u1zd0kAAIByetTdxVN/2ZcqwT/Lv2r97pbuTbx37dAAANFcSM6hAADS7Sv36JuBFVhI0QPYSZezesvnjkEWZYZnEAAg77fHbRrisvyTuUczCRBZFEWZAgDCDMexGAHR60QKIOlkWQZCCjQTVBZFSZZFUaKUSoQq3/FIOi2l0uObaVlarQg4J1NPBTceEylHSymVJVmr1Uqs4A4UKNVqtVotICxeDP/q9 hf jJbR3U79YRwgpWqWImOUCCSRCBt1/R G26JCICIGXfiM7Siv28VF83ZG1kEgAGak3BVIzSpWg6fzLFjNDkz ZEEAED02SIV3Hhs044A2P21/mEzB7SqX86wxTot1sXZJoMC9qpWxUVzKS6LUACguQn/aISmVcvhk9kAIGckPZaomTzIbo5ULtUt/9bodUNclg2aezQjr 62WfWKOfcLLV8IIeXqeAogaS fv6sHKssUYQQEPP2ruGgu3sgiAAA0J 6yRmjuXwZA9lfSJROZUsiOu6wRmlcth09mWiyWO9IoyOnX7usAAEhuupYIbjwGME0 WpGcPDifkkMBKEi3LxvKUXKxbqEo9oFpQTUUbrvCAzUaDhBmEZUIIaBcuEuBUkINPXmEMLbSOFvzQ4lMAYBIsskRHAjKEYohvQast W6u7duxqYRSIiL55tcmTGw eKzf TzgPIkp7ln5gwI3t2kXYvX2nYM3fxJ y86DV99z8osF0KAgGTczwJ3b7f0k6O7H9Hp RbtPSBTk0EIuZ8F7mVdHx79rOtRBK4t2nlApiZDBsg3NKSSoaoFoEQSJcwhhFCeRhHC VTCla3sCY/upEvgBSBdndOg56ZkyvGMrM9beRf/2XUie0WnRm5noFtD/fEvYnIK0SulhokbSiS9XjJZQ7o6u2HfnXcBgIi6vPARAAUqS3pAAmfsl5CMBwY9jOp5EkBo3tGoB vu9uR5Bih6S00vwkVsQCmRqaH2paLBNCQzLRsk3bWHSojig1uPoIZPaQwaKwHYCdxZveV3p9zrbT0g81EWJZJEGI7xbDRk /yWJ8OGzbqSRams14sUczyHEZVFUa8HQeAwL3A6ncQIDMMAxvmbLUpEnUgYjudZlgUASS/KrNJJAAoUEOPiImBZInLeAhClAJhxcRFEQEBkAOB4XqBUFkXqXTe4HAB JcSPP3nVyvYoU3QY8RhRmvsg4fK1OB2V9TqRMhwnCBwDZp8EA4DVwQTKV/NQq/OQVu1IPZqMWT m3o5xA3ufuJWud2n/6/75dszlFHlVinOHhFJApRsN3vL9G1Fhg2ddziL5/mWBMf88PDmqx0kAocW7hvJlPUZqdCdSlmgQi1LADGZYRVAKgPIqdAYrNSohlCLEMAxmABBV7GFr65utTVRAKaGWPi32pih2NHenUPCvkosdGZ9KfJPeKAAGIBSU9l2mFCHMIgRAZaWNR/k1bN0PYgBkiljG0L5QIkuFBOW8yE9JIT1qKutFynt6CZjoc3SIc MxAADr6Z/vkmYp7VrU pULBn44aoO2bvdgy3Udqqyb62UK5EnCxTulahm2p3AVmtVzv38x7jGlj65eSC1Vu2UVF05wEdwrt6zvfu/CjUcF0ocYXhBcBFapLQlFDM9zSiIwJwgCz5n1TpBH7a4hfMqpf9KIeOdSklTtzcZlXQUur7lXQpPi9hzUNejX4rU DeHIzquZ9hvyrJsX0ks3a1rNzWBUxHAuLgLci0mSqjUPcc/3MmIEFxfBhVfElaW8nXv0yQ1zPXg3reuh6MGGuz2RAABY90q lSp5FM8CGfKo3bUen3Lqksbp/CXdj71Hygd4K7mDL1fHsBmeZiRce8BWqFlGkZAt7 cFGQ8MfRTs3cC/FAIAYKu8UhHuxeV1BS3T5azeCrjXc793MT4TM1SWXOp8sHFZ96TpQz4/qpEAqCwRYDiOwRghhuVYRGXJ/vQcJZKMWJ5lMEYIEEIsypvRQ4bWCSGGxaYzrIk R4cEDx4DAorc/UozCBli9Kzbf8UI77XDR63w6P/Lp8Fu9qPDGDMIQCbUKDnLYESepKRqywfXdscAAMg1MLi8LiUpnYDd8uu4HRmfkGC32Iglfyam6wnw3g0qc2Y5HlFKATEODNPJo6RUrXdQTYOcLoF1y tSkoq2yOEW/MHGpT2Spn8Wdkxj2fkskH8e37h4p1TN5r5Kfijf5BWP xfjCtYzAEAlWZIJkQmRqXmTihiMMXl0M1XrXaemGwYEgFxrBJfXpaQ8oop77ZruDMNihFwU/T U/RfkjwAAIABJREFUKSAAaqafotbcRJ jgzw7 pnbEVdo4JevHN0tSl/830AB7VIKylgdMSxW9I8wAkqpxSq5bT/GISQlhBJi3dsLxXqxEypVq147ILBB885fj2khxJ 48ITQ7OQzaeXatQl0A8anRZ9 /kbBXQKHjunfrUFAlQoVQ1q1b n56Epqru34kD5 99pbFYZO uh/NWv8b CXn1dL/m1rXC7Q3Os7V8dX/mzKwDY1A94aEDa6asrqzXG5AADIrVJgSHBQ7fI8cq1Yt15wSEBZF0N1Yb0Dj7jS1QJrNGzRccr8mX3xmVkb47RAH0atXJ/V9MfZn7Sv7etXtc47H4WtGNfAQ6mDtTc2nxTbfPl5e/ns5n8K 8JKG7dy7ZWqod991 3VmpV9677Ra9IHtVwBPYpauS7jjSXfm4f/qofSbUCMYaRmJq72RuQ6RQ81At7qP26kX q6rXG5tt2NeqhTuxyPXCsEBQfVq15WMBpBqN5z177tkf0c2PvGuFUPCqof5O8J4Olfq35wrQBjdWBNb3awKg9Ni94e5dl6VKvKPOICOn3cxdivy7m2O Ke3xeTP3g70K9em4HT2rhf2HnmgaHuZtqM/bRLLd/aLfuFd/Y6syXqvrFOL5guZ/WWz33AF2OqJf8WEafFbKlq3VevCq0QuXBJXOngukH1g2sH bhgs/EqwhgVuEXCzTewfnCQ4SfI3wsRoJJOp9VqRVEihEjU3MjWZt1o9q0zD8sr5ahC8w8 Nn2Y7xo4cu7QMpsnTz/59 yJm4Uh34XVLWXxPiWm6LRarShJVMlTlFLAjNJxyIrZHqltFD6hS2N/31e7hk5rLB2MuJyJwGb5tY4tO5KH8Sk6v2ZNvVlAQlCP0CGVzN S0hIeMDXbtPbzcBUE3l6TjrJitkfmhkwN69zYz7dh15HTGksHtly20o0urM3jq3ZZ/WtohT0Llyd6BAcHNQiuXcfH1RSzUL3n7/u37 lvnn92r73lM2zSR61qBLzdP2yU3 21hvJVQETz9XKzS0YQACUoM2Z7ZG796eM7N/Kv0rDbyOlNxAMRlzOoyb1LYz/fBl1CpzWWDmy5kgmUAiCQ0uIfMDVbt/YvVD829UCzk04/LN/eYMe /fPZkWk7bljXWr5BSjnanFeOVECZEAMqi7IkGbY0AoDlHKwjfmx6e7FYH8j5jlu1bhwA0Ky4qC2Dwn LlQHkxKXfbmwxc2XiwPRrR3dsi5N7Kn6JXl/pza XD/crBeRR/M5Z42fd0FkEh1hBYKik10uUytkJP4Z XXn22C07hsDjq6vHj56foAMMoL 5cPhXleeN37J9GDy sfbL0fPidAAIgK// bJd7T0AAKDv o19IWFFs 4/PbGTKM83lm1 A Qn107sG9r3550PZACgmecn9v9SOzV0ecQgN6DpCacjlm6WDDbKvbA9Wtv1XbxvzjnjuqJL8KdnNg oojzM2KuZARC3qEGXVQmyFLd6bA8c9t2ElefLYDnt6rqZf0sAJPP8hA/HZX8zZnnEJwXCt4Y efHIryvNGrtl xB4fGPdhLELb rsuefTQ4/fNvSAhBXNeq6Kd/IrbeTReNGWWU2Uh/GLDwGc/aLjuwceW9FbIR A25Dn/uHQcTV nrY fqrubsyxA/dJsOJdGz/ns3Cvb0O37BiOpLSoNV N2H5bUjKgfH/DYdewdVuDhMdn1kz dLfd4YSzesvnHrtm/Kj5iTrA4BnSobUbQK p 3sZAn646ePgqf/YT3OtEfMPjjA9JYx7q/dvZUdd2GHKJ/sfzwCIW/Z6z1VxtoLQxS8J3/jGrJWJA9OvHYnYfF1 HwBAaDDsmzEuv3ddcCETOObiyqEb/rd3ztCDvRb bdHOIE5QNpDwHMcihAQWg/IFh2Ge6Mn5ScNP6bMQf2uEN28p65Y8OiH1MA0NkovzaQbdjx0bEfRu dMWff4VnZGUlRW5defn1w3kv0zv5FC9t9u2TvQRbgwqQu7SM1fPCn0ZuM gnfeS9c0c9viU/OT/x0/rzw0P173SE7OfJ7o5zOQUvVafe/UgC9vo402XHz8Fe/vWhzf4A ZXHolEqzx23ZMQQex66dMG5homV9ZcB8vdw4n54X8ZPzE4fNmxc cn kO2QnRc75XJGfPjk/cei8eTNC90Ua03XqMQVAgACR1P0/Lug0Q9HP Ymd2u9JdzrJuptLwze2nLXy5sD0a0e3b42Te5n Jd9bf7hU2PqtQcLjM6snD7Nfjv47UDDYEgAQZtkCHy1Ybu9ywI91b/SF7nRHMycNatu2Xd3X3tHlZrav07FYAyeGjWnK3re8R4YXOGxcVEYsL7CmJ8CcwDPKDjcCeVVXfs9ARK1eBuUREb1OTwAw58JbnTikBTzYCQ3M/sYg67UiAYNUNN /TGEIPIuAinqdTAExgsAhU2IsE648qrwoqKzXiYh34TAAVR5YTCTgXHgGqKTTSZg3rsHkPYKs00mMklUswpP0OgkM2yTNIZJOL7OCcdsmEXV6ygk8pvncHYqR5v1tKzoq6XQyI/AsshZsyYISmVjuOih5UKIsjlpM/FFKCMUsY9ihQykhlOEYkIls7k4IoYhhjevoyiOHgRBZNnqzCKrkQghhGIa tIZT1r8xyyIiy4SY2SXvJTNbUFK4HwCw5a0YmLb0k3a9RxNZpkSWiURliRBJlkRRryWyJMuS6bdrKc9zUXubtuqh12Ylx19 nrbBjFIbUvOF47x/KhUUEXVarU5pyB3EsN NiDqdzrSr3Z4Hu5tXDRseJb1Or9M6I4YVqKTTanVag0wMa1nlq7w4EGI4BpG8U1gQw2KQRUkmhFJZEiWKGBYrK95ACbFyczNiWAaIqJdkQimlRJYlUXa8eNuO0aZ/q9EhhsVUMmwKJbJo 1t4FYcwLI1SZS8UOHtlN0IIqEwMLxIKgBEC lJsRnu5sTAcoVRWtpoqy2UIAZXlPJtaG0fb9GO49xWofW8vjud6mgBiWEbUywBEkqnlDhnM8hyIkkQoIMSwDBUl4tBGfYQYliGiTMxV7ZSHfJ4xxzGi4hkYjlXEKBqI5VhDHYsYluPUprxkgVgWy6JZY87zIIqiXgYAhBnesGcRYZbFoqTTSQCMMqg3vYI5gUeiKOqV6UyMWdaJb/JtxWjTv43oEMPxVBR1WgkQYhgWE3V29amhMjFfcEGOf3SEEMKGXeiGJ8b4kZTKs8fccAghhlG KjPYBVFq rAUYWUdxexlW34AIUSJEjICjB0I6nnzTNtyzAou SPAnIuL6eYfTnDhLPzzgsE/EZVFLGP5wfk95wsHEMPxjL07nAp4cCI0xpQClM9bfolQvifz/zF2JVN5niCGdzE/RdTiGQAznGDFXmYZs2CY1v6J8ud8zAku1txtxYgYwSSX d 2oivgzP73TvwqThDCjPINcT4oAcygvC2RCCk7Dqni37wqR8rt38bqS2nXzb0VfEXl6bFmOEopNX1ziBAgxJj2MRr2rSMLs1rxAwAY5zlSSsCGtxdGySnzlEp6nQzKV/hE6dJi1t6U43 JaE2MVfdm3iHPWRIVlf8ExMasqYW76bGgf2rtAFFzb7aiUHkaCtUqpVaaXYu3rPop6GjV2wui5LTlABhjIhPjxBRmWE5dYFZR ZehFumXC1TgD5XnhjM6L7D3jfXteuR8xChfy0belrsBzi9s7wmze5Coe8sZycpJ0XtG1Ml7yZa7sheJF1wMCAKfvyFH/v3X3H6Ke7ttyPnCYWoPmTW xgu d1pFRUVF5WWmuPaxk zLh/YfTNYa5xtQ1smv/EOaBX11Mf/Hm7bcAQCwR40PJy/6 69TmpiT/6yd/H5VV/PGPDshauuR Ke6u9uKnArsq5N/v73ibY8XM1uCSvqHHioqxQlVf16eH9VwL1DhTlFcc xy oF5Mw48RQCoVK2wVUu6x/406r2JZx9yr340de3yUQndZp8xtPn0YdTPY6JevJzFByrdoPfcKQO71PTCIw/2Tzi3fNzEH20dW6Gi8m/iaaoslReIariSi9UhoXKn/V/Rmov7935hdqe9dXfXdqtPKbcuPsXcNVOz36T dxZ0/3pr9N0sUf/ozJrZ83Na9qvtCsDWGROhhK8xm2NnKnY8dH57mD8HAIA83ttw/MKoIBcA1q/H8Yu//zT5 1Mn/0z9e8 u0S2M92RblZOpPWKzJubEwd7eQpOZiZejNTHRBzsZru0WfN ctmJrUky05nzk7vFt/U39HvfXNp09uOzdzj9s3KeJidac GlYFdOudbcKPhUquDnQRXKr9 2izyptG/vu4qPf9 7e5fuD8Tq1oKj861FXXV8u1OXylwWrbTnj8 E74oIBvVqOjMDvh68w3TNt3T33wMDm3o16z779FN 0CtX6dvHYuujQHeT5xmdzTh7Zf37VsCCJq1yaBZCuLejlHdK80dwCZ8PaTJT3u1XPfdy6TfX35j/q8 2SdhUYm3LKsUv6eIe88c4Wje70xIB6zbxDmr0TqSEAyL3eN79 2z5lbe/O7zUdtCyp7ZT1AwLzlrUZj45jO6UtGhrQuHXDUWsv5Ro MxQCekX sWvfgMLPRWe8qtV1e/DH8ZtZFKiYFX9q/97UYr2eUEWlJIKQ5WlqKiUWSinCWLGWargSjvWlWvnw3KU7YwveaW/L/aml8KrZ1CX2UIq fJtJK7vpl4wY/OFvmkZ1Shf1wFPtnmW7Y3VEf/vYwr0Zzfo0Ke98OGVaftyXPTBq9q7TSfcSLu6dvuiKf5fW1UzTDhjubJz9w6mUTH1OyoWTfz20dYw3U7n18O2HjmtiDh3/YXj3oHKupSq8NfCz7hVZOe2foxrfEZMGdw0s7cKrfV6V/wYIEMIYKx/zqJRkgFKMsfEeMdVwzwnL8uIwVieDieZCcg4FAJBuXzHcaX/XhntKcQwmWc K7hmpD2U uEO91JVDI66mSlfXfHe6y9CiBSenXXugjOGl 3Ea3LKGDwv3RaeC4HxDqpYq32zP353y3B7d82IBlFZb0l6 cK9g0nVxq18PWZ33zJR7u32lk7NGz3js1aRz729P8JIPPMih6bZdAlzB4UljNm4Efv1PN991C3E vCpqw4ku7kTSkqKi8jCOMS8yWJim0K7MZSDffccbg1d2Tvm615lWKcb1EO3wGEEIiG08tlneh4w5b/gEXEmK6VwAzj8NGLlkhXF7z weYUq0e4Uilb70D65bQtX05VLsE d/bIz3PKV/EU79x7oryqSz0194vTu4d89 HNvTmDpq2ZebvJ8Mi76jWFKv9 1LnalxTVcCUWq5Pk2LuBf7477e9Jdt1tQmW9RFmeK3AYooW79Dj1SenqPrzu2sGrVd7v2sANuwa0/vS1Mnam8Ik R4c4N USYNbT38Osu4grNKyqyMn716sI9xIeFCInopQab1VREO/EJEnVmoW4O7mKwLpX8q1UycPURSKS2XFCUnbarbtPCvQBSObN6KWrYnBQQ3/1uFcVFRUVFaeHoNabKqbN2E 71PKtrdxpv8V0p70td5vi5N66cLfi2x82rVbZu1wZAdtyJ0 uH35c670gN83 maPP1Pv5wN4zs//3JO5 lu073ml28pm0cu3aBLoB49OiTz9/86QzbcM 61arStDb/b9p5x695bSmkN6klJbwgKnZprWfh6sgKN2D9KjVm7Kb/Dj7k/a1ff2qBrV5f/TSUfVLFdYrFar33LVve2Q/B/abw55fNerWt6uzOY86rRvWcdOfZCsnMLASoqKioqKmBjjl2 v Gwa9i6rUHC4zNrJn 6 66keLTm7hL8afSmAVWUF8N33gsHiFv2eq/fbhIAAF3cljGrGv6yZOMggEtTurXbdV ZNy/gfidiXeKhLz94ZcCKQz MbPSDA5LrEpd u7HFzJWJA9OvHd2xLU7umSf/3d8OuX25KSKQefzXr18N33dfLkROemf/ooXtvl2y9yALcGFSl/aRGpIZM3nghOzJI5ZHDHID ijx3Pbl26Ti26NGsh/cL9/3uzWfB7gjgOa3/4oYMnGfOsGuoqKiouI8aOakQW3btqv72ju63Mz2dTq OElYn15zV8woe3zK9 v3Xr0ve/l45dy/k2tq3HCNoWuPtvq9ma0FbFMwfj3 3NVnY8cPlt19Ke59ZOsM/67rH1Nmxdv/4E69W0VFRUXlX8 0JYPa9R5NZEKJJFOZyiKRJVkSRb2WyJIsS6bfrqU8z0Xtbdqqh16blRx/ueTcrSLdjxjX//b7w76YuXqhvycj3tv02cBRp59QxqVsGXfBrVqfjlUzzsQ /LeNXKmcm5NjeylBReVfiJrfXyLMJyNVw5VcSk5bDgDy4 h1s7uvm23uxlfruWfHiBoAmVe2D192OedFyfaskG snnbjRQuhovL8MH5Hqx48UsJBBozPquFeFA6t7Zaottwa oR1zULWOe5fStn2ZsNtz04eFRWVokMpBUoowhhhUA8GLcEoliIIU0BINVzJp8S35SoAoK6Lq/xboJRgjKHIpz6oPCcQQoAwJpQwiKGq4Uo8aluuoqLyHKEUMNheec2b0c3/qFK8WKjXhjkQgOmAjEIMZwpNNdyLQW3LVVRUSg7U7qMjmLco8C9tVCxSV QF7OJd aY2/nacgsn5V5pPoWAyn8ocaluuoqLyb6IIvQFbw9Nn2pDYisupCv1ftg2tYHKexnzwfC1oXxJngyoYZiGobbmKisp/nOdw5USRZVApFDuqe85afZFGLHJbTkSdXqaAWF5gCz2z3CnPxfUuEbV6GQBxgsAUYMyKIoGj4IxywmEgFArCAU9X5WFRVLqKzTSYyS4c3/dhBZrxURL5guGFIpIVBZpojB2PJvlRcLlWWKmZe9uNhpy4mkM1xZZgRhhuW44mwYASjR6/QEAHMufMm/TY9SydCQI4wxwoj 286u VdDZb1OJIA5gTfkYkr0Oj3Yz3tKa6r21v5DUCIXuEi6mNpdhBAAVQZw5n rFAeWhkMI5b9D0zaF2OKFtPfImZG U NySmRRD0jgMADmBIEzRPdMeW4ROYThrnjE8rxStTMMwPOVjZYQVby8EEmiTIHL 1RUzEEMNq 5EUKUFFOr /R7xFRsk2c4SolMieNtcKG2QKgEH5TjQFuuTCBTWdSJMgAlhAJGBae qSyJkkQoIMywDIiitfltJRQKgDDL8SzkDf2JqNWK1mbELSIyPbIMlaW8oCxlYNmCIy1KJFE0XEJqmmOgVBZ1ojJRzrMIiKjXyxSAKTBJaRjVAQBQSac1O 7dMMfuqGzW9GNVNsiXXiJLhCKGF9Rm6GnADCayKLO8lQmmvAUUhBmOYzECoteJFMBgcIZ34fIPz6gsipJMlHdY5R0gkk4vMwaTASCG4zkmzx0TWSYUsbzAQoEY7RvXanTm2QcxXImf3yre6rCgwopnDztCyNh3B0MvnsoyRRgBocaCqpgrnztiMKKUGvw4MzR0BjtpfHatTbGH/Exsl2c4hFlEJUIIKBdaU6CUUJNhsDW7WPNDiUwBgEiyyREcCMoR7KXXuRAdHpcjZBjwW5eZSHrROCFPZNH6zDOVROOlnpRIooQ5hBDK0wcCcHQOg0qShAw2I5IoMTyLqLkMkqUMeS0xxogSSmRRR0HgGcRwnKwTCZVEmWGpUrEyPFtQFEOEedKCWVl3QrYC rEtm3mYjmlGpRAQZlmilyTCFGiV9XqRYo7nMKKyKOr1IAgc5gXO5hw7JaJOJAzH8xgBlSW9XkRGs1FJBp53wUoHVsQ4zx3xvAsGAJD1uoIx2i4CtqKjsqiXKMPxLAYiiSIBKPHtefHxDHc Wcy5UgDlM2sGMxiIoZFANJ87AkplmVKEGAYpQ0NKEUI2R NPKWSJHSc6wrOynclwFAADEKoMqalMKUKYRQiAykbz5X/Pqh/EAMgUscYBPiWyVEhQzov8lDiwBEQlnVar1eplpdNvdQ8OkZXdYJgTXARB4GwEixheEFwMlSIlFDE8b/CLOUEQBMf36yBWEATB8DYlxEIGF0sZiCQRAEAsL/C8YKiYiTLCQQzHYTCMmozPBeVAmOMNYx7E8kr0VqvMQmQroB97spnAnCC4uBRIl4rTIMyYJk7MoLJEgOE4BmOEGJZjEZUl 7OqlEgyYnmWwRghjFmWRcRkNcQog2aEGJYBQky9PqO70zHais4QDstghDBT3Dta/qtQSZZkQow/JnfEYIyBEuNqJrJwp4QQCogxDAYQwkAJtVz6fKlb4BJPAe1SCspYHTEsVk68QRgBpRTlH/3a9qOESQklhBJi3dsLxbl97Ahbn0qghpUkpHRbEMNgkRQcmyPMYIQAMAaQDWPaIqbfGBMyLoxQCvZkMEpIJb3ObIBrXAEzjs0Nf1uZn39xshnCZBn19MTiAmGWRTpRIoxZ/qeUgtlkKMK40MUxSghQojO3GiDTO b2MhuV5V1W4WyMtqKjlAJmzMJBINuVW8UB8q XI4SAKmshAJQY9q6ZKvJ87tS4q43meaPq4acvGkoBgMqiRdnI38lyxI9Nby8WB9fLGSrp9RKlstlcYRF47psAC4KZfNIbS6vZ5T9UKYIvoOTZkA0A1O1uxQtCLMdIelFiuKcOyto3j0qn0NYbxR0dkfMFq2aV4iHfejmlzu43t1x Q/BUU7AqRYWCwZZg6MVb/t/yiwUH/Fj3VmybI4uEg NyhFmOlfUSBWJloREQwghkClQmlGGAyvLz/1TLJAOhlEEISL6JAeN/ATGscf6cUpkYGkwqK3vwEAJKiSjKmC/OL5Ds68eubGrxf0YglkM6USKmrIwQMmUeyNvkacRa9w4hbLBpkTJLITFa8W89OoQQEEIpNtvDUYIb9BIsmglqHE0XsfxRSk3ppKZxerGJ91x5qTqJBbI zVM/AiDW7mw1f3TEjx1vLxLH59gxw2JJJEBlSWYtP8fFDINkicL/23u/n3me5b6rqrpn5jk dvyDc JjcuzI UEiGQKSpSDgxleIK 75H/hz/D E61wiIQRcROECQUCxArFigY3BFiHGds4z091VXMzs7vzemd3Z2Znneb/0Oee7O09Pd3VXT1d3VfeshvIzjN8/Rb39kzSUZSR2 cNG9CJDqioTNu3OkcR7SUEpVaXWvkw1I87EOdZYW3KX5d5CGVVjSO5x98O0bOPtMyfbZiKALswuc7GKetk0ws5LDCFK5oQthWhNzNOYyVTNuA6dtPJw3sUqVJEyJ0ymqkrOL9XadImT6ceLq/NJLvdMmkI80ABzSprQqHU2vy33kTNzPRcnovq3SaSzJR68ip7irA5wkjhuZlRkKd3my3WMq5vFZBqmOiZezxaWZLUzK Ll7LwLVSLSmMz1Vubi84yaM1fsvLMQddFEjtl5pyFpc hjnfgjMoSopkrOe6u3lF3Fz3OKMSatzTyzOOeEzWI9 EnmHbNlPpWxXptn24Wo59tnSraNCgfjcDOHunx1eU4hhCoREct1WsnivYRYlnFwJo0lK3IOIVR1DFtGz0JOCzBR4mT6ieLYZbmFUH5GYnbOi LQw9NY0nY4dMW5MmaW1iYi5tqWwJTvQ1txzOxcfaqs0QubXT22LK2TSdcbRtPU7xeoc2YSWZDV3szYcvHFR/fPkn18XOOLWfGR9dLnRZNeQ0lEt6msdBN38iF2WT4TthzcO5uVz1vbmXyvdtL98zVZu57Mg2q34F553a zss21z7Rs/TzBM7DLP1qmlnvficRlxUhfbKlumOfYH3udSLLiY z6VInsiqtc7c9TxQ0u93s WAWzOJbBXNqUxPFtgyI358utTt8eypm5fea4tuvtZMNbwPOMKc7MLnsViZiJ2XFv/yn31DqShohEbhfNlCaSvY2tnnmzWJWJ6jP0jXtb/MgZ7W8K2geAU6ETG5l6169fh lNR0b3drKpIsAz3G1VsxGz27trNM3w4miyl3DfUmw3fxcRTXpxK4nz2eK44bcA7QMAnWMHFbhxqq1v35mtbDnf8ZR/d9A AAAAXgXiagCAXYFj aRAcUcGthwAsDMwCicFijsueLk3AGA/EHU9FwiXnwXYcgDAfjDLuw/vgKWYGYtcT BBcUcGPnYAwG4wMQlL/7WM4HgwkYhcXiMPxR0d2HIAwM6wyDf6gfXzMngTJxR3XGDLAQB7g7XdSYHiDgvi5QAAAMC5gS0HAAAAzg1sOQAAAHBuYMsBAACAc4O9bwCAncEOqhPRfkkMFHdcYMsBAHtiNfjp7qPDDZfvUNyhgS0HAOyGmZGpsQgL4cWgB6bWlLIYMUNxxwfxcgDAfpipiDAz7MGxYWYWETWt9QTFHRysywEAO2JGQtOR15tHt/sVbEuveSfUwUTXd7beUdw1NyjuPcCWAwCOg81 XULbotAXNSq92j0cwN428m0Tn5czrM6XVF/NsJpPqQO2HADwlXhgNjC1PH2pIZkqa9WA/sW2oQ2r84z6aF8NzkuyNqvVwJYDAL45UyPpnpbyi1nlPZlpup1bdbvi1k9ClttyDWWVjNjnhb 7Y25V4oeZL0XDZ5WIOCsKN2yY3l fEVhTCCHVWhQvGpWIfVH4L weAq/EUllGV3fF9ueFpOozcF5kgg54LCwlYyfS/wzei6Vk4s7 uHRseSw/Y2diweJ8lo1YwicwrcpKiST7yL/Az eZxcaQs4iwsOm7RQJTWKrKoCRZkTed2rQqK5rvirU1xdzsG2Ga oeot7K7zExk9QKu/RlsQV9xzMzCix7cO7o4vr2fX5ebplARF5kQSVYUGdGRNiMcQiSr w77PK8He f2FsmOpJQToDGay9BkYA520h65mdl0I6v7/B4xMM1NcWaaTJfb4Lu6YD7wi3LGbHntH7YUypCITNVIeOiFthRDjGrE4ryjEMYc2nUuRsTis9xTLKtm6a/h8zOMucAv3m fOW3y91nmKIaQLt 8MI04xlsieT9Yac3/dZBaYwixfnoVOQeXAAAgAElEQVSn/BPNOo IyGL5GftteJPQO0vx1g5LGnBKgFaemqIau7yAYVqOONEUks/HIi/XcAmLq7uZVmWw2mdFRC7/yLrLM0shxKT1PZeuqbGskmsURMQuyzN3uy6akhr7vPA0KHFelaPFtTsLu zw7q5th8Nhg22zh52ZLzN1aubslpKxMKldHstaXZ3r7ITNrEmzZmm4hpk6vs7abJ7zS3R3UxyLZ4uqSq4ecslM7aoYGdPLWBrTZESkMV0v0oKslrDdeYvpdTkzMZERjQupsQoXh7ymMO5YthjC5aPGECVjZr41ABNNTpgshni9taripdJ1RkU2EiBvixT7Is3/tV/41UiLsKlpCqVRMRj mW8zteZlhzYycbMYY5PUNIbocs8224D3BbAYI4H1sHivVYzqBla5qoJJlmfClkKoKiqKTPIim/Sxm4YyqMvyXJgsxaoKfFGSxUR5/iH1fDaI3K5znn8IEVGqymGJ0w/1VHGWQhXNZbkX0hiCEh3enm/HC3c 9XyuRlQfs3bihLQxEmyd60xmKZkxO8f10tCMmSdX408Kedh14hJepbur4oxIiNTqJbUlM2bxzESWLurr3jeahh1RMvaXBb5pineyWi/yk4yFgCyWn5 fn1WqZ/mjm2401Zu9JCs imLMshIREbu8KD6aUdDU2OV5k1ayoiiKmQ067PKP68hm7LKPj6Yc0zFnV0ekj75I83/tZxWjEhH7vMjzohnFtVkOtUWULG9WQezzoiiKfHxRxL7 40X8ew24SADJiuLj415dQB8Wd3WTtLAUlVyWORFm5zPPluK8V9U0Jva5dyLMIt571quO2NWLZmbnHale53iX66tLnCquycc7YRa39QaX74rFFJPq5d/1OjsRIVNq1jrcu26qasSu8ZgwC5lak/iW 441 X4MWteM6rU6Oy/1G29YmMyMuwvi6TR1nqamaqrjyd7KnX3sLOO A2tCR1zPU9g5CTpc6rI4YSYSIUrNknVphdk5ISYWpmRE4oSIRJjURp EeZEWCtxNbLEqW2vfx8Nll1L5EsYxoyXSzgnAzrvtPXffAxbvuQxRXav/mxm1nKEscjc4ZqpkWrZ1RHy9p62d1qrs9mMVa0ucKs7MSFwrH6Y0KzdYQDdezsxkdSyEyLTZu3YdyDvX7bKrzW7JjPCwvhkzIrIUes9Gd5K1JM1ksvcyFS93FqsqmqWWc/ABNuu VzO4WeFLRBPXqfn mxjnBMDQ8DjMPnOxCtFlT2c1duZRiaYV9FwQd6Q4TZ1s0TG2oRMvN1u737wfbGN6ygULHsWo0SU1s/j 3wfe1vtpxpNttjnyIabW5Sw 86mKRjoSWSRulsuW1JwjS ntJ7GuIqmZYybtLLvn/zqRFbHzlxiAWdINjfl8A84KgAFhE9hnXIao157NzNfuQbc9nxfGXErM0mjwoY5xp8SR9OPFMTOpmklrx8aBDfqBRbtil9X0g0 bmV3radd1 mbi7cqpJomDrm 35mciHfvN1vbXJWlmkr2MBW0/42MX5yUGJUsx f75W3GOUzTSUH6G8fsnpar95BrKMhK7y1Gup7mIlKrKhPsx9fm/9rPyXlJQSlWpteNTzYgzeXDQnpF2vAF3EOC7w wyF6uol00j7LzEEKJkTthSiNbEPI2ZTNWM60BJKw/nXaxCFSlzwmSqquT8Uh1NlziZfry4Op/kcs kKcSTGo3D0IRGrbP5bbmPnJnrmTcR1b9NIp0t8eBV9BRndTiTxHEzoyJL6TZfrmNc3Swm0zDVMfF6trAkq52Zi5ez8y5UiUhjMtdbmYvPM2qOVLHzzkLURbMHZuedhqTNKY nxB8RKUQ1VXLeW72BbNFf 0K6PKcYY9La6jOLc9u KGC AXcQAHAzY7p8dXlOIYQqERHLdZbJ4r2EWJZxcCaNJStyDiFUdQxblpx2bN0 UeJk oni2GW5hVB RmJ2zoviiMPTWNJ2OHTFuTJmltYWHebalsCU70NbcczsXH2qrNELm119siytc0jXG0bT1O8XqHNmElmQ1d50bLkvPrq2XbKPj2tAMSs usFF8XnRpNdQEtFt7irdxJ18iF2Wz8Qpu4m7OXHnm/RFYufz1nYm363N3F8HWZF0U0/BvbrNSd r2lwDzggwFBUshF3 0TK13PtOJC4rRrpmS1HDPMf yN1HSbLiY z6VInsiqtc7c9TxQ0ue/zOwjMwi2MZzJxNSRzfNihyc77c6vTtoZzrX/PM61XW8nG94CnmdMcWZ22atIxEzMjnv7T7mn1pE0RCRyu2imNJHsbTz8zJvFqkxUH5pvPNbiPVaOS0EDAnBgpsJwvevXr8P0piOjezvZfKQPPMbdVjUbMbu9u0bTDC OJnsTT8zfRUSTXvxI4ny2OFAIiNCA4FuCLn4uTrX17TvzsC3nO55ycAc0IAAAgG1AXA0AsCtHcUqClUBxRwa2HACwMzAKJwWKOy54lTcAYD8QdT0XCJefBdhyAMB MMtxtv6CecyMRa4n8KC4IwMfOwBgN5iYhOXOixfBAWAiEbm8Rh6KOzqw5QCAnWGRb/QD6 dl8GJOKO64wJYDAPYGa7uTAsUdFsTLAQAAgHMDWw4AAACcG9hyAAAA4NwgXg4AAAAckX/yj//L3pVf/82/O5oSthwAsDPYQXUi2i JgeL25u/9 / xpphSCOXPNMWUoqY4mhK2HACwJ1aDn 4 Otxw Q7FHRrYcgDAbpgZmRqLsBBeDHpgak0pixEzFPcu4GMHABwRMxURYhiDg8PMxCJq6tgZFPcm4GMHABwSMxKajrzePLrdr2Bbes07oQ4mur6z9Y7irrlBce8BthwAcBxs9usS2haFvqhR6dXu4QD2tpFvm/i8nGF1vqT6aobVHGk0 NgBAN TB2YDU8vTlxqSqbJWWcEvtg1tWJ1n1Ef7anBekrVZNcDHDgAAC5kaSfe0lF/MKu/JTNPt3KrvVOKGtlxDWSUj9nnh775OblXizUtfl3MKIaRaSeJFoxKxLwr/hb0/4K1YKsvo6p7c/ryQVH0GzotM0EOPhaVk7ET6n8F7sZRM3Nkfl1W2XGNZxc7Mg8X5LHObNoJpVVZKJNlH/vbf1zOLjSFnEWFh03eLBB7GUlUGJcmKvOmzplVZ0XxPq60pJm/fCNPUP0S9ld1lZiKrF3Dtz2AL opjZpZlW /v6OL49v7JdblpChVxkQmRZEWREb1jt4K9rnSruwb7PK/HcudeUMq8CF96A8gb0BjNZWhTMAc7aY/czGy6kdV9fo8YmOamODNNpstt8F1dMB/4RTkP2fLaw2wplCERmaqR8NDLbSmGGNWIxXlHISQizoqis4yvczEiFp/lnm5Lfw2fn2HkjltB3mmKauzyIrNu6a00luIt/ WC0XUZR0Rksfxs7ThofOzPlGIaQ4j16NB2b4zWDnZnO8SJppB8PuJOusVTWFyWeWHSqgxG1Ojf5R9Zd3lmKYSYtL7H1/eQxrJKrtEgEbssz9ztumhKauzzwtOgxHldjxbX7k3ssrd7s 6x7XA4bLBt9rAz82UqT82k3lIyFia1y3Nbq6tznZ2wmTVp1iwN1zBTx9dZm81zfonubopj8WxRVcnVYzKZqV0VI2N6GUtjmoyINKbrRVqQ1RK2O2/xxLqcmbheEo/WQmMVLg55TWHcNW0xhMtHjSFKxsx8ayEmmpxRWYzj /l6abhRrcYQXe7Zlgh2qeJtIta8y9BG5mXrS7nNEkTY1DSF0qhomZcltQOPwOK9VjGqG1jlqgomWZ4JWwqhqqgoMsmLbNLHbhrKoC7Lc2GyFKsq8EWLFhPl YfU09UgcrvOef4hRESpKoclTj/UU8VZClU0l VeSGMISnR4e74dL9z51PO5GlF9zNqJE9LGSLB1rjOZpWTG7BzXS0MzZp5cjT8p5GHXiUt4le6uijMiIVKrl9SWzJjFMxNZuqive99oGnZEydhfFvimKd7Jar3IT/KQLW8vUtllo7tyNNXbxSQrclcPZ2NWk12ee6FUlrF RWCe53yJlxd34uWSFVkzMaYJk3xxIVRlUDJVIl4mGBERS5ZnVFaJ6vU k2koq/R0KRqjUuO4FyaLZRlNY1JptWW7dmBDWJx3McTkO/3LUlRyeVY/rj6zVMaoPpuJkprGxL7wtZrYe5 qpNaEYVyzaGbnXajUrJmpuetiOq4rcao4qSWvBxqXZaojfRSsxGLn7I 4Ri3sRNhM6xepULOguV03MzVi54XNjJjFVI08d8aoU1vgwzNoXTMSbuvFiIUpmTF3jblNpWlUXbtbJpKdeh87y7hzwZrYErtmOHMSdGgzWZwwE4kQpWbRu9R6sfN3Td2leL7ET8xokWCrWFvKpXEsVmVruOiE45bUDjwIi/dchqiu1f bh5KvaeRucMxUybRsK5H4ek9bfa2n/PZjFWtLnCrOzEhcKx8m2PKn6cbLmZmsjoUQmTbmm6geyLvX7bKrzW7JDC8/fTe1EU6h92xwx/QvSTOZ7L08HC93FqsqmqWW9/CRrB6879l7j4G4TsN1wgnnr92BYfaZi1WILns6q5GNFvUKbEqDzwVxR4rT1MkWPWcbOvFys7X7zfvROKanXLDgUYwaXVIzi //vX9iYUGa8WSbbY58iIfX5Sw 86mKRjoSeiSu3Q5ktcvRUjrIWa59BJsv5fJXYucvh4DNkpIM5n/gVbDPuAxRrx2XmcnU7LKdqdnSeWHMY8QsjYofsp93ShxJP14cM5OqmbS2dBzYoB9YtCt2WU0/ Dia2bWedl2nbyberpxqkjjo nZrfibSsd9s7RxiW5BmJtk7ecbHLs5LDEqW qFHqpecKRppKD/D P1T1BtCSUNZxjqgvmUnekKwzUoR7yUFpVSVWjtW1Yw4kweNAlgPs8tcrKIS1eacnZcYQpTMCVsK0dh5YSJjJlM1q8PUbc 58y5WoYqUOWEyVVVyfqkSp0ucTD9eXJ1Pcrln0hTigQaYU1K3n1ln89tyHzkz11NzIqp/m0Q6W LBq gpzup4J4njZkZFltJtvtyEujtMpmEiM NmtrAkq515Kl5eb pJRBqTud7KXHyeUXMoi513FqIumtoxO 80JG2OgTwj4RgPC7ZhKezynGKMSU3ViJjFuUO/iOArws2U6vLV5TmFEKpERCzXSSSL9xJiWcbBmTSWrMg5hFDVMWwR71fsIJ8qcTL9RHHsstxCKD8jMTvnRXEG4mksaTscuuJcGTNLa8sQc21LYMr3oa04ZnauPlXW6IXNrjuXWFoHla43jKap3y9Q58wksiCrvVlly8UXH90bJPv4uEYcs Ij66XPiya9hpKIbpNb6Sbu5EPssnwmkCmDgsYynMl/TrAe3JOs /WZUsT53I00/2jtwCawyz9appZ734nEZcVIz2tpcpjn2B 5 6RIVnyMXZ8qkV1xlav9eaq4wWWP31l4BmZxLIOptSmJ49sGRW7Ol1udvj2UM3P7zHFt19vJhreA5xlTnJld9ioSMROz497 U 6pdSQNEYncLpopTSR7G6975s1iVSaqT9VrPUUV79 /9txHsMNWHwCwAJ3YyNS7fv06TH99XczU7VNFgGe426pmI2a3d9domuHF0WRv4pXzdxHRpBdHkzifLY4kvpZ9BDts9QF4I3gGzsWptr59Z15ny/mOp/xt7CPYYasPAADgq4G4GgBgV47ilAQrgeKODGw5AGBnYBROChT3JhY0/CY/yQsAAItA1PVcIFx FmDLAQD7wSzH2foL5jEzFrmewIPijgx87ACA3WBikuanw8ChYSIRubxGHoo7OrDlAICdYZFv9APr52Xw3k0o7rjAlgMA9gZru5MCxR0WxMsBAACAcwNbDgAAAJwb2HIAAADg3MCWAwAAAEdi/cYE7H0DAOwMdlCdiPZLYqC44wJbDgDYE6vBT3cfHW64fIfiDg1sOQBgN8yMTI1FWAgvBj0wtaaUxYgZijs iJcDAPbDTEWEmWEPjg0zs4ioaa0nKO7gYF0OANgRMxKajrzePLrdr2Bbes07oQ4mur6z9Y7irrlBce8BthwAcBxs9usS2haFvqhR6dXu4QD2tpFvm/i8nGF1vqT6aobVfEodsOUAgK/EA7OBqeXpSw3JVFmrBvQvtg1tWJ1n1Ef7anBekrVZrQa2HADwzZkaSfe0lF/MKu/JTNPt3KrvVOLztlxDWSUj9nnh7 6kW5V4/t4Hsnqq9BRCSLWqxItGJWJfFP4L 4DAm7BUltHVvbT9eSGp gycF5mgbx4LS8nYifQ/g/diKZm4sz8uS2y5xrKKnQkHi/NZ5jatu2lVVkok2Uf wM/qDW9/MsNO5hYbQ84iwsKmz2UI3oKlqgxKkhV503lNq7Ki R5SW1NM274Rpql/iHoru8vMRFYv4NqfwRb0FcfMLLzowb2ji Pb 8fW5aYpVMRFJkSSFUVGtPsmhV3LtbqDsM/zekR3bq iryJ86W0gu6IxmsvQmmAOdtIeuZnZdCOr /weMTDNTXFmmkyX2 C7umA 8Ity1tjy2qVsKZQhEZmqkfDQcW0phhjViMV5RyEkIs6KorOMr3MxIhaf5Z5uS38Nn59h5I4 7XKHtxNfNXPLMBtkYhpDiPUjOuVsaBZzREQWy8/Yb5CbJN5ZirdKLWmNKQFaeWqKauzyAtZnE8SJppB8PtK9bpEUFpdlXpi0KoMRNZp3 UfWXZ5ZCiEmre/x9T2ksaySa3RHxC7LM3e7LpqSWt11ByXOa3m0uHY/Ypc96YV6PdsOh8MG22YPOzNfJvHUTOctJWNhUrs8sbW6OtfZCZtZk2bN0nANM3V8nbXZPOeX6O6mOBbPFlWVXD0ak5naVTEyppexNKbJiEhjul6kBVktYbvzFuvX5cyNnRwXXmMVLg55TWHcF20xhMtHjSFKxsx8axgmWufMGNxOzEQ6n HNSIuwqWkKpVExGOOZb9Ox5o2GNjI7sxhjk9Q0huhyzzbbGvcFsBgjgU1h8V6rGNUNrHJVBZMsz4QthVBVVBSZ5EU26WM3DWVQl W5MFmKVRX4oj LifL8Q p5axC5Xec8/xAiolSVwxKne/5UcZZCFc1luRfSGIISHd6eb8cLdz71fK5GVB zduKEtDESbJ3rTGYpmTE7x/XS0IyZJ1fjTwp52HXiEl6lu6vijEiI1OoltSUzZvHMRJYu6uveN5qGHVEy9pcFvmmKd7JaL/KTrLHl7VUpu2x0M46men YZEXu6lFszJyzy3MvlMoy1m8GzPOcL HtYnV4W9zI7bd4 eWKpo6oMSo1fnNhsliW0TQmFd x yxZnlFZJaqdAEymoaw6edUJG79FVQYlUyXi2daYE BWtazI3Paz u8Mi/Muhph8p6NZikouz rH1WeWyhjVZzNRUtOY2Be VhB771OV1JoAjGsWzey8C5WaNXM0d11Mx3UlThUnteT1QOOyTHWkd4KVWEztebS4Ri3sRNhM6xep3DyAl tmpkbsvLCZEbOYqpFnao Ep7bAh2fQumYk3NaLEQtTMmPuGnObStOoul4gTiQ74z52lnGfgjUhJXbNKOYk6NCYszhhJhIhSs0qd29zdRHVYlW2ntnHY2KXOvMlVmNGc62xRAB2HoZ8e1i85zJEda3 3zyUfE0jd4NjpkqmZVt9xNd72oprPeW3H6tYW JUcWZG4lr5MMGWP003Xs7MZHUshMi0Md9E9UDevW6XXW12S2aE5/jN1EY4hd6zwR3TvyTNZLL3sjZe7ixWVTRLLafhAxypW4vrVGP/nYpzAhypob4QzD5zsQrRDfdQrM1qbGOHEk3r7rkg7khxtb/pehF9Zhs68XKztfvN 3E4pqdcsOBRjBpdUjOL7/ 9f2JhQZrxZJttjnyItetyFp/5VEUjHYk4EtfeBrLa02gpHfbw1kVUYucvJ3HNkm5ozOdbY1YAPPWvhn3GZYh67cHMTKZml 1Mzd7OC2OuI2ZplPtQn7lT4kj68eKYmVTNpLWZ48AG/cCiXbHLavrBB9HMrvW06zp9M/F25VSTxEHXt1vz11uohr/Z2jnEtiDNTLJ38oCPXZyXGJQs9SOOVK8xUzTSUH6G8funqPeBkoayjHVAfd32t/7trn lN/EQ7yUFpVSVWns31Yw4kwdH5hHmW2MHAcAkzC5zsYp6 bFAdl5iCFEyJ2wpRGPnhYmMmUzV7Lqp8pqH8y5WoYqUOWEyVVVyfqn6pkucTD9eXJ1Pcrln0hTigQaYU1K3n1ln89tyHzkz15NyIqp/m0Q6W LBq gpzupIJ4njZkZFltJtvtyEujtMpmEiM NmtrAkq515JF5e7 VJRBqTud7KXHyeUXMKi513FqIumtExO 80JG1Of6wVanD73QzZ5TnFGJOaqhExi3Pbvg1gvjV2EADMwM1k6vLV5TmFEKpERCzX2SSL9xJiWcbBmTSWrMg5hFDVMWwR71ds3JwqcTL9RHHsstxCKD8jMTvnRXH64WksdfbKrjhXxszS2jvEXNsSmPJ9aCuOmZ2rT5U1emGz654lltYRpesNo2nq9wvUOTOJLMhqb5bYcvHFRzedZB8f10BjVnxkvfR50aTXUBLRbU4r3cSdfIhdls/ELwf39sod3j64MhTV dzdbwPuCdr9OlupudaYEWBQO7AB7PKPlqnl3ncicVkx0gVbOhzmOfZH7j4ykhUfY9enSmRXXOVqf54qbnDZ43cWnoFZHMtgUm1K4vi2QZGb8 VWp28P5Vz/ vflSa/tejvZ8BbwPGOKM7PLXkUiZmJ23Nt/yj21jqQhIpHbRTOliWRvY/Nn3ixWZaL6ML3WM1Px/psuNtEaAJwTndjI1Lt /TpMf31dzNTtU0WAZ7jbqmYjZrd312ia4cXRZC/hfikvmL LiCa9 JfE WxxAPELgtYAoA16/7k41da378zmtpzveMq/F2gNAAAALwdxNQDArsCxfFKguCMDWw4A2BkYhZMCxR2XTX6SFwAAFoGo67lAuPwswJYDAPaDWd59eAcsxcxY5HoCD4o7MvCxAwB2g4lJmp8OA4eGiUTk8hp5KO7owJYDAHaGRb7RD6yfl8H7MqG44wJbDgDYG6ztTgoUtyPrGrtny6EpAAAA4GR0bPntTfEAAAAAeB r1tYdW86IhQAAAABnA2fSAAAAgHMDWw4AAAAck6WOdthyAAAA4NzAlgMAAADnBmfSAAAAgD2Zer394ya4Y8tTSg9nBAAAAIAZmJiFmYe23MzI9HET3LHlzuE1cAAAAMAkKcWHbaWZmSYWpo45NzNT1TEbTwsX64iXAwAAAHvAzCxOVXtG21RHV vLGU4uZqYA AVbAAAAW/GkuXnjBi972CAykw4kt6cX1qv2vu3QcPOts1AAzDkAAN ZTYbK926FPv5G7KuECy3O3RrxZnvfDsAm jt J9iZrbra80WAb8gO/QqP/GOg3Tah3Yx93/luQhzNloNXsEN/wqAAXgH6FTgXW/XY1flg7xsAAABwSBbbdNhyAAAA4NzAlgMAAAAHZIWnvRsvf0twaqtdUzhMBwD4huww9GHfQo 1e9h7d72AA x9w8asE4FZEdgKPJU7gEZ NZcWVht5/aqI200FB7Dl4ERgaAAAgAHMQma3N7O2P 8C4uUAAADAUzCxEZE1/6yx7vsJAFsOAAAAPAvz9cVt1vq8E7DlAAAAwFKmXOfN0pzs7qJ8qfN9zWQAthwAAADYACa2dyzKCbYcAAAA2AZm2j1SXoN97AAAAMAGMBGze8uBH6zLAQAAgO14x9ld2HIAAADg3MCWAwAAAOcGthwAAAA4N529b3hBJwAAADDPAW0l1uUAAADAuemdSTvgbAMAAAA4Ds /Cmb63XGPgnU5AAAAsCMv AU12HIAAABgJ8xMRCbW9Y8v97t73xQ dgAAAGCOx20lk7BcfoVlSzq23Dm3df4AAADA18Ge85HbytX3wsQ4kwYAAACs4GW2sjVJWFkG4uUAAADAEXh8kgBbDgAAAJwb2HIAdiNVn5/hkV0zlsrPMur2EhGRaaw Pz8/Pz r1xRAT1QcgG/F44F4/H452B3TFENM1gztzCIuyzzXf6vKSokk 8jv7sRclfgRQVNVBiXJitzxrUR6UXFzsHNOXnAolcxSiObywr8kewDALmBdDnbGUqjC1ZATkZmmQy/ZNMZ3i8fisxcZWzMjFmF yQssAAC7gHU52BfTpERE4vPcC5GRWVJjIiKNZdWYTQ2fn4GIsyLn2Lb9LM5nmePxxD6VQem6kk7V5/UrWYohXmYNzCJ1PmahKpMRu6LIRqyZONEUkr8szdtoCiEkq8XKMi88SGMaQ4hqROyy9mreUriIw KzzAtZrMokLTFS AyWFbmjVJbR5YWXwb3sfJ45HsuQiaxdaxaf5769U7Z2PBCFz89wcW MVkpDWVlW5M18IlWfgfMiE4tllZx3mi51rIWZqTgAYHtgy8G XCyJmamZMBPz9b0GzMxmF2vLRMJkqmbMwkxkqqYpVMRFNpp4GotVSEbEIkxmarrQF8DivVYxqsu6XixLVRVMsjwTthRCVdFgNmApVNFclnshjSEokSMiMg1lUJfluTBZilUVuMidcxxTUmuW4JoSSS69lz bhjIk8Vnu6uaZyZBSFZJkeSFN6/Xq5vKCQ1nZNWqwpFLDpk2U5x9ClkIZgkjueKriAIAZNnrvGwCvR7zjKpmlUCWieqHtvRMmEpfnfAmBFxfrInnhmcjIyCyGKplpMsrGEqfJYmurzy7LMmGqs7tIJGJGPBVvYnHexRCTz7vr6qjk8qwOY/vMUhmj kx4kKauncsy1brOpjGxL7xjJiL23qcqqTnnPMfY2HLTqCRZf4ZiKSZy cXlXk ELI1nyPXspfYX8P13QU1Wau4mdo0w7LwLlZo5mqg4AGAO7H0Dp4ElywtJMSVVMyLTFKqkeTGwWg2aGl/tDbPVr15iEbvXZXIAABOTSURBVFK1VJWpNm/Oe8dExOyyO1vZWLznMkR1reeljjNfnerNer97o5mRuFYapsaWK5mWZWwXYkbE4tliMi9sGpVcPrCiZkqc9Zz5Uxk65ySFskwi4sS5kTjBQOB7lRrSFobJZioOAFjLsrU6bDnYH2bns9ouWqzKqEQp2bgt11hFJSJx3gmThrDcKLSfAfZ5zvUEQs1Uk1ZKRe6GEe5RgX3mYhWiyxYX3rp78IGIiLOiGJpWFieWkpq3pI2DfWkxoxn6vHCqKSWNIUbN86kp0xPc/f1GbKoD4MVgHzvYGY0hpKS2bLZpVp95Fp/5BaeyGsvchNGbbXaXnFh8ludF8VHUPuP69xHMUqiqqo6mz TsM7bYOuLNzGR6XbSaqlF/YtBP0zqGRza eZ9dbcxTUnJu5PlklnaedzMkZnE y/M8E0tpfpU9Xak6LtGvyNJ87q/tAQANDz0tWJeDnTFNSVOi0Ll69f6yMKmRhrKMxC73wpSMNITgSGN3Ud5PnDsnlJQsVqVy57eMNFZVIubayihRs2GOiFQvJmvG1c7sMlf7CGoDy85LDCFK5oQthWjs sfGmjTJ5Z5JU7icbWPnXaxCFSlr9q pkquj3SyOLcRIYw72671V4Ny7pi7iZCJDSjGxuDr8noz4zmxoulIiFFMy55k03T2kN1VxMoshmMuye95 AMAaYMvBzojPXEqq11Ubi/f YgWZnXcaktZrOSPxmbcQ1VJK4jKvN7swTEwsWeZCfYVcfeelFBGtHeyXQjPPvGYOzN5LCteVObs8pxDqLXwsrnvc65Imyy2E8jMSs3NeNDbSZEXOIYSq/i7i/XUzv3ihoDTlhmDJ8oxirKrYtEHupjM0jc3RPWaX1VWeq NEpVh85tsVoXgnn/GKk5mqwh0IwMbAloOdYXGZzC2AXZZ3wtLs86LVT9v7z4aJ 1duqad2uDFnxcd4GJxd/uHaKbvficRlxZ0QOktHfO8n/jBdbH2paF SQbWnMvRZ7mcFZMk PjpXJirFzuduUBH2xUerTMmKS2YTFR8UBwDYAEyQAQAAgCMwdBMudRzClgMAAABH4PFtJLDlAAAAwLmBLQcAAAAOyyI3O2w5AAAAcG5gywEAAIAj8PhLlWDLAQAAgHMDWw4AAAAcAexjBwAAAM4NfOwAAADAdwW2HAAAADg3sOUAAADAEWjHy9f522HLAQAAgHMDWw4AAAAcAex9AwAAAL4rsOUAAADAAVmxTIctBwAAAI7IcmMOWw4AAACcG9hyAAAA4NzAlgMAAADnBrYcAAAAODew5QAAAMC5gS0HAAAAzg1sOQAAAHBuYMsBAACAcwNbDgAAAJwb2HIAAADg3MCWAwAAAAfigZ9Lgy0HAAAADsliqw5bDgAAAJwb2HIAAADg3MCWAwAAAMdibcgcthwAAAA4N7DlAAAAwLmBLQcAAADezgMn0W7AlgMAAADvhJ 05LDlAAAAwHthETN7xpzDlgMAAABvhJlZxNET1txvKA4AAAAA1sPMxM4Nri 17j1b/qTHHgAAXgq/WwAAXsfj3btry2HKAYCxODQYpAAYoWPLD/KUYCwF7 QgjwEAU2w RJ6iz9e1tm9kIVap5Yg 9q2FuGreul8f5jv1puOBpgffneEQueSpOMTo/gQ2 ABadGx5ivFdcgBwRrabWAxzak89t5qGfjPQYODUrJm1dGx5jLrkHjwgp6NnEEZ7yLNqHbl/3j4Nr1jXifKtOtpNJzxx/VjrkZ5yDq2utZKNV ZuLlu2wf2MePjfuwJY5z8jX84CH6e3TQ1yo39aznq1dGz5YZoHdFivl4u97tptvvyH 4lrdlj8DTPnBZ93ZX6uc0SbtXAUX5LsGRlelvq1uWyX8dLbHpebb7eOZXI3Y 78h4iIbPSmKUsynIUvLHlf3ivOm0rH fLt4b45WLjWnDKlE8GxO87X/rR9AQd7IMfYR8SZUlYL8B6JB6VyPbd7gfPl 7Bl5XnCEzNbxh0BePjQDxbig8Fk6F9ZUNLiNI8nfx1vFeSFhX81Wz41yXxoaTvPfK6jf5rPc qJfubx3pvxkeFwYk7zBkFHIw7X3rXOWTKd7jQaeJZdV vPFLaBLeTu/03edLPtfSvfxtYLNVfoIPM9HYBdjt35N5LuOLa8PXLdvvc/NmnmeuTsImV 7ct3Mu7c2s11m5Dc4XhSxuNVkZsV6vL02/kSF9zM0xOlMVnX5S BGrcDcUsSTZjoyPgxNRsuW5dVzrTQBmt ja0Gv0ypIXwAPNv2C68epK7mHLmdi6tnF658Ja386a4XEu/XO96wEt7dJ73/2I7EO9LlkS4Zu6cvvDmN3mk8y7jgIPZsJPufZ5mOXohHoT3rBWZOtY0XsSrB6phuoYXOWxjOYfqIMerHi8p/Hs1zOwxJZflTeyaF3YCd z7fCE hhl9CE7fOXWPPNM3R8V6PaXRXks/fN8Zg ERr4XV4fubDveCwvZ2KiyoOAzwIOx8s5q4v7gyCMNtcamj1vpOz7IeaFepY7XTdOOxFQU4imW2HJj4nbxdsxmPqRQo6zy29rgOT5wRYdez8VDzsyM t5fVq2bD9x6b2PYJnZ3idP/62OOrBNoY2q5utB2brTd8LmZ7HTiWtFmE8v37Qo9g6qn2Ef0Z0sZseW9iOIJVHBgEZ JJaxN SYWO6eeqMnYwmSTjL8L8w3YSseX9MMx4Hix5K3hBZUcWTiui8HMGM3FU9Olfs77BrqZKdTulg2Pmp mj5xG0Lv0bfn4DP1emvdwFDnmOIk/fJ4lQ9yyPB66e9HCBNxjzh2 qHG/jgaWu6MXpXiw9XozpHXZLWOlcX5gbd67/XA84Ll7oRxr/rCa4bqc6amBd0eObSeH7uZzspF3/wT96csy4Q4f6MOs6xH IgrbrBqrM5oaR4c2c926/kBP00HEaJhadbxEyset5GsaTXqFnMmPdp1yHfIthDb4cE5s9ut Epy8Gd9JZ6vqzTNs3f2Gw9CuHffpWsO1/zxYn154 cGSe/c/Pr4OXv8Crlj385ZtxBvaxNfoTu4nOSw28fkMnMfS9zfKdP 6k/iHb6XTYneb9gSz rsMJ6SP9KiX9EJ wLV9M dPivTsNOdbP5kbOEfmWm91y57Zlp HmcfkbCPlTA 71/mefuy/8bixBe29WtdxiGliIOdtlyKHYl2ttul2Gy8TbeTTyvu/r79rXZ2vs63tm2rTx2uFLbcTqf3Akp5nRT7F1DR Qcd82mv7FXy x FrWupx3r2B926Bq/t1x5y/8cE49AM5JdxbhV7R VbIueK9bwf6mblRDn QbrgV7jhbWAbw4nm7rdvnd9QKf32MrI6JX84TT6Yj6u6y/go6e7fFmW/JB1u4n lMOP5MO6E24e7Zv6W8reesLPj uvzdz8BznFD6E4pM0wdsXsI5m hA8IzTEI37BbDBv96fNi/ucBxRppdy35Yfdxo3I1m7Bx9Mp3ZvinyMBl/VatflQXs1P5HDRuo4mFZPyEg03IiuC/avHM14X8XarTozmbqb5sYxhguwhic2Hc2weu/bgZ7v5aIcSOgRbOLzqVg/e3pm9yx4lOFJNLCOg7lc8Rh9KZ6YmvXi5db87 vN9o4dmh79fE6W7YBbeQfYkDsvG7l5jZ58DdhxearHvfDVM/Otjedkb3YNHLZQ1WUJmVvvhBhdly/qNOeLtR1PuOEy9ngyrmVxDXpHpNbX/PxtdTy TZu taLPFD537zsrdVzPwAsl2zhfIzISkc f/fmS5ElT/vHD69fHz5cfONZ7Jtq7wL8K92rDlxcMcvvKBiV9rWbcnvvNzK1/X7Q5ufX/7 PuBNYuY8O6w3RLjp28Vq HM qPvI2nZkoHGzAqDhMx5cUP/uSP/vl0oktakc f/eUv/vJfvV4ZteWv2OZ4LPUeinu7xc7IbFVuIb4vVONjs2jSs1AbZ9Za2xn01P1vYKnI7wmfX/3RR3zD0PaN8boq/uhXf/oH/ x/uJt/nv/gj//3/ 1XfvWn1yv997G3Pm/ozDmieg/FV2ydJcE/vn28x0x495DnFQ5H01CXXzO9WuSbaZ5s4u5 uad/kfsg9Azeov7zQmftzJ72RySdyvpVY7ENPhyFZwUa1Y3N/nVpvmP89Dd/SzX9s3/y3848aCLuL/78z1TTL/3Sj24XHynta9qed3K4/r8Zq7r6XOL5XI47khyMtlGubfRS01ynPvOi/ErPMF5dqWdgRft/LVffk5xEvUTE/Hf/3f/oj/7F7/3 P/3HzNJ7Ppklyz5 9rOf/R //7/87d/62/juxjn6VOMNkuRnb018PR0R/cu8uk89DuLWON3r/AUwmn4EEZQwnO34yvZYU5Pz/zAWp6Q2 Z779Dvo2qNubazi8ZEoaZPlPMD3/hl3/rt3/nf/2f/9Gf/vG/ Onf Ld/5ce/Xvzg51h8 bO/ It/9Sd/ sd/oKq/9du/k VF 66pd7iOrnOub5EwJrbGY3eqvjVXrcPxpsFlN zm8B0ey9voifu6rfd6VrtyT9/Yb63AkuZ vJG/ mCynFe1gY0NY vuafFzP/ L/95/8J/8X3/4 //nH/ze7//T/z7GwEQ K37hF3/0qz/9G7/0K786vOXu 9h5YACvO1w7W10v8c8T9pZjj0JnmHXMMzVIcadnrduu288avsTHmPGwrbzhrLRXxO8bCWb6b28P9lMy7lTB445ZD05phmvu QRb8ZOf/s2f/PRvLkx890zaTNQfgOWsPBbyRC8bboVDl13OgoC4fb3Y e0g3sIb9uPuCHxfoPbZz6 gs/PyypnNit9JW8Kxl7jgUHR9OreuUzt9nupH1l1voU/OY60m73vb7huOGe/KCXhE4vdX1AZ7Re6k7n343mzjN3iw57yMx94VM/5AW sDOg1YzDVic V8JgGs2cB1IB4cr95fy/dLcB88x3fZTo0Pv/dt3VTv6P3u6PI12FmnSr33FgxrUO k3LJmvbxO2GivYtSZfPWD1Dtam YabbK5d8OdeAW4tIfsap/uFnZsa3mCXrBI7b1EF0fiFmynwMff4Xq3Fdor9RNo9fACnpm1Q/zGyoBur8wPHfcj4HMR1 NueVrOonF9V 5o7JQ hXPS7d8b9fDtFmcbx8uHXIQ867N9WM42cN7rrdya8jULvjNU62xMqWH49rfx1odaruzRFOc3u1 lw3QPdB3xNSrPrMuvLHWzH71jHl2 L017P3HnEngtU370b0t7389JOJ6kZ pAK44vtN qcjTn4evW5V9iPvYlKnFmoIDXMrqLtd/o3E39nXRynro Imn7uMfG1Tz0AZIHxbqe83gqlxnG1BBD9Xv/43/XvvJbv/07Im5491a2fKi63nan9nkjotbs5hBwa5yi7nnMM3CeEWeWqWosrN6CZF koY7OoQfyr8uK3m1dF9g3U9UgnrToFm5Nfe772B8cagaTa5/lP/rJb/zln/ rH/zcL/zsX/9/v/CLP/ZZoSkOb93Ex94WZPTf8E8Hozf4HFjSL85IsxvxMk18swHpRfB1ZjvTnkujauC47KGe446iaweLdw4uP/7JXy8//3VVfZafP/vJr/ tUUNOW9vyddjRlHwwce7yNY3X16zV ej9otrgzzuK8g649f/n4atrZRt6i7YVvGVm4rP8V378b/7Fn/0/P/rVX eZH0LdU6Yey33s77T6B346bOLzuZnbevRgLYevU/46zbU1ncapD9IOw Sr33d6vvY sOvh7im1pZxPKy9hRTMMT5ZfbdPQSG3YvD/ yV8nol/7jb8ztSint6/L6393Ux4osn54vtDzefcXDerL7TjORJLu56WWCNjE168 G5oK G83vTwKJxf/MR6v9NByX23TqJHaqnl9lv9bf 8/nM/vnbb8NJykv4/atJPIPsqo7L0QnC3fWMqtYPCZm2U/rg31xNvxz7oPbvhC2kVTxT3YrLz9tHK4521qlnqX20Jgobd4q6oXxQ9mFuV0EFs mOwcTvMHlGgh5xtE2wz3zljvb49k2c8J3GP8fXBPNf/RGc5BzuPOWfpo9LYlg8cYNer7d5WXv/dtId3mqE/i3/b92xGeop6 3i3QKX/I4nn652Hn3inau28m3SE62FEZtvTNzi1tuOsdp2nm0wgKNuCxbe19N/uTmT7JIdblbZYH0d/MAQQ8gAh7MTmRWuTCHf75 iye1QV8HO6v6c7dT4/qKjwb374FX90AR1mXX2HioSFvz4LeOeweaci/tsZ3eUaMb 9sv/O2qr6Pp/1pakvBUfrY8bDOf4hG2 dLN1y7z5yniqudTd/YO/VY1dfd8uq2FSJi5s //LMXF7SU RX5m7vacMPEAQzpt3n8rN/gndX5qCZ6bxu842Y/22D9Ph5so6nmP8aD1AXL8Y3pvQn4cIzuylm0RW7mWNo mBkzeyIqfvDzf/nn//IHP/wr//Uf/FdvEQUAAAAAa0mxClVZ/ODnPRH9G7/6G3/yR//8V3780/zjBzOvlQEAAADAQTCz6vNn//JP//Cv/rW/5YnoBz/8Kz/6td/8f//kD8vPv7Tx0ycAAAAAOBDMXHz88Ee/9ps/ OFf8f/Nf/F7f 0nv/uf/mf/ Q9/4ZffLRgAAAAA1vEP/8HvysRrIAAAAABwDtzf/uXf J/ 0R8Uv/B//51/5/WxgAAAAArOAf/oPf/bk//vj/AUgtbkJQZoo9AAAAAElFTkSuQmCC[/IMG]

---

