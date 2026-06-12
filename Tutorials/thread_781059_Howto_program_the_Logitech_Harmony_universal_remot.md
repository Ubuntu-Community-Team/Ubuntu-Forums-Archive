---
title: "Howto program the Logitech Harmony universal remote control on Hardy with Concordance"
date: 2008-05-03
forum: Tutorials
---

### Post by marcw on 2008-05-03
****Updated and tested with Intrepid Ibex 8.10****
The Logitech Harmony universal remote control is the finest I have ever bought, and I've had a few of them.  I currently own model 880 but I think this howto should apply to any of the more recent Harmony Advanced models.

As nice as the Harmony is, it requires Windows to run the application that accesses Logitech's extensive online component database.  What I used to do was have a Windows virtual machine (via Virtualbox) available on my Ubuntu workstation just so I could have access to the Harmony software.  A whole Windows environment for one lousy application!  Well, it's not really lousy.  What it does is one of the things that makes a Harmony remote so special in the first place.  I just don't like the idea of running Windows for anything.  A little research showed that the Harmony software does not run at all under Wine, so that was out.  And then I read about Concordance and Congruity.  These two utilities, along with Logitech's web interface, allow me to do everything natively on Linux that used to require Windows.  Not quite as elegantly perhaps but very servicably.  This is how I did it.

First off, you'll need some extra software from the Hardy repositories.  Follow the instructions at [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) to enable the Universe repository (my personal preference is to also enable the Multiverse and Restricted repositories).  Afterward, this should get you everything you're going to need.  From a terminal (just copy/paste):```
sudo apt-get install build-essential libusb-dev python-wxversion python-wxgtk2.8 libwxgtk2.8-0 libwxbase2.8-0 python-ctypes python-wxtools python-wxaddons
```If you are told that other software needs to be installed as well, just say Yes.  Then get the latest Concordance and Congruity.  As of this writing, and what I used, was Concordance 0.20 and Congruity 7.  Back to the terminal (execute one line at a time):```
cd
mkdir source
cd source
wget http://downloads.sourceforge.net/concordance/concordance-0.21.tar.bz2
wget http://downloads.sourceforge.net/congruity/congruity-10.tar.bz2
```Or you can manually get the files from [[COLOR="Cyan"]here[/COLOR]]("http://sourceforge.net/projects/concordance/") and [[COLOR="Cyan"]here[/COLOR]]("http://sourceforge.net/projects/congruity/") .  Anyway, once you have your files we'll uncompress them and process them, again in the same terminal (some of these commands might take a couple minutes each to complete):

```
tar -xvjf congruity-10.tar.bz2
tar -xvjf concordance-0.21.tar.bz2
cd concordance-0.21/libconcord
./configure
make
sudo make install
cd ../concordance
./configure
make
sudo make install
cd ../libconcord/bindings/python
sudo python setup.py install
cd ../../../../congruity-10
sudo make install
sudo ldconfig
```
Next you'll be creating a permissions file.  Again from your terminal (after connecting your remote to your computer):

```
lsusb |grep -i logitech
```You should see something similar to this:
> Bus 002 Device 007: ID [COLOR="Red"]046d[/COLOR]:[COLOR="Red"]c110[/COLOR] Logitech, Inc.

The 2 numbers you want to pay attention to are the ones (in red) that make up the ID.  In this example, they are 046d and c110.  Your 2 numbers may be different.  Alter and then run the following command replacing the 046d and c110 with your 2 numbers, but leave the quotation marks in place:

```
echo 'SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c110", MODE="666"' |sudo tee /etc/udev/rules.d/custom-concordance.rules

```

Now do one more thing to your browser.  Change your preferences to ask what you should do with downloads.  In Firefox you would select the button in Preferences -> Main -> Downloads -> Always ask...

There, it's all built and installed.  You'll now do all of your Harmony configuring through the Logitech web site and the new software you've just installed.  From your browser go to [http://members.harmonyremote.com](http://members.harmonyremote.com).  You might be told your software needs updating.  Skip past that screen.  It doesn't know that you aren't using their Windows software.  Next you'll need to login to their site which will require registering if you already haven't.  Once registered and logged in you're taken to the main Harmony configuration pages.  This howto isn't for teaching you how to use this page.  Use the "Support" link or the Logitech forums for that.  After you've configured some Devices and Activities on this page you can then click the "Update my Remote" link.  The next page that appears will tell you to make sure that your Harmony is connected to your computer via your USB cable.  Ignore the rest of the screen and click next.  This will bring up a download dialog.  Select "Open With" and choose "other".  In the selection screen that follows type in /usr/local/bin/congruity and press "Open".

With any luck at all this will open your new Congruity screen which will be your interface for all of the  communications between your Harmony and the Logitech web site.  There will be at least two times you will be asked to download a file (each time will open Congruity): the first time will be to merely confirm communication with the remote.  Subsequent downloads will be to perform the actual data transfers that update your remote.  Both the Logitech screens and the Congruity screens take time to refresh.  Sometimes up to a minute or more.  Be Patient!

---

### Post by kurtpete on 2008-05-10
Just FYI for anyone reading the above useful post...  My harmony 676 shows up as:

```
Bus 001 Device 012: ID 0400:c359 National Semiconductor Corp.
```

when doing lsusb.

'lsusb -v' gave it away, though:

```
Bus 001 Device 012: ID 0400:c359 National Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0400 National Semiconductor Corp.
  idProduct          0xc359 
  bcdDevice            7.0c
  iManufacturer           4 HarmonyRemote.com!
  iProduct                4 HarmonyRemote.com!
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 HarmonyRemote.com!
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      33
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered
``` :)

---

### Post by rockstar_ on 2008-06-18
Congruity now has a Sourceforge project at [https://sourceforge.net/projects/congruity/]("https://sourceforge.net/projects/congruity/")

Paul

---

### Post by beoba on 2008-06-19
Thanks for the help. It's a shame the Concordance and Congruity sites don't explain any of this.

---

### Post by CarlWalters on 2008-06-25
I'm afraid I've fallen over at the first step 

```
carl@carl-laptop:~$ sudo apt-get install build-essential libusb-dev python-wxversion python-wxgtk libwxgtk libwxbase python-ctypes python-wxtools python-wxaddons
[sudo] password for carl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package python-wxgtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-wxgtk has no installation candidate
carl@carl-laptop:~$ 


```

I'm very new to Ubuntu and Linux so I'm guessing I need to get a different Python package from somewhere?

---

### Post by marcw on 2008-06-25
> **CarlWalters said:**
> 
I'm very new to Ubuntu and Linux so I'm guessing I need to get a different Python package from somewhere?

Nope, but you did nail a flaw in my instructions, since fixed.  Follow the instructions at [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) to enable the Universe repository (at a minimum) and then try again.

---

### Post by CarlWalters on 2008-06-25
no luck so far. I tried enabling the universe/multivers using the instructions at "http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html" but I still get the same error.

---

### Post by shawnrgr on 2008-07-01
*bump*

Having the same issue. Please don't post a how-to and let it go stale on here. This is something I'm sure many of us would love to get working. Including myself! :)

---

### Post by marcw on 2008-07-01
> **shawnrgr said:**
> Having the same issue. Please don't post a how-to and let it go stale on here. This is something I'm sure many of us would love to get working. Including myself! :)

I assume the issue you are referring to is repository enablement.  I am not an expert on other methods of enabling repositories.  I followed the same instructions that I recommended.  If you're having an issue of not being able to get the Universe and/or Multiverse repositories enabled and have followed the instructions on the posted help page, you might want to ask in another forum.  Or alternately, search the forums for the similar issue.

---

### Post by shawnrgr on 2008-07-01
No not really the issue, repositories are enabled.

---

### Post by marcw on 2008-07-01
Made a correction in the version of python-wxgtk.  Should be python-wxgtk2.8.  It has been corrected in the original posting.

---

### Post by CarlWalters on 2008-07-03
I'm afraid I'm still getting an error. I've definitely got all the reposotories enabled (main, universe, restricted and multiverse) but

```

carl@carl-laptop:~$ sudo apt-get install build-essential libusb-dev python-wxversion python-wxgtk libwxgtk2.8 libwxbase python-ctypes python-wxtools python-wxaddons
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-wxgtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-wxgtk has no installation candidate
carl@carl-laptop:~$ 

```

anyone else had the same issue?

---

### Post by marcw on 2008-07-03
> **CarlWalters said:**
> I'm afraid I'm still getting an error. I've definitely got all the reposotories enabled (main, universe, restricted and multiverse)

Once again I seem to have left a version number off of one of the packages, python-wxgtk.  It's now been fixed.

I find it difficult to believe that I would've done that, not once but twice in the same posting that I tested beforehand.  I'm inclined to think that the package maintainers switched naming convention on me.  Try it again please.

---

### Post by CarlWalters on 2008-07-04
Excellent :) Thank you

The first step now seems to work OK for me. Got to dash off to a conference now though so I'll continue on Tuesday.

---

### Post by iitywygms on 2008-07-06
This is just what I have been waiting for.  Now if I could only get it to work! lol
I tried using congruity 7 but all I got was a blank screen when trying to open the hex file.
So I tried it using congruity 8.  Now when I try to run congruity I get this.
"Could not load libconcord; please ensure it, and the Python bindings, are installed and in the relevant search paths."

Any ideas?


I read this in the congruity 8 release notes.

Provide a GUI message if libconcord can't be loaded, in case congruity 
wasn't run from a terminal. 

Don't know if that is any help.

---

### Post by marcw on 2008-07-06
I haven't tried ver8 yet and so can't speak to it or it's installation.  I'll try to get to that within a couple weeks.  But I know ver7 does work having installed it with the posted instructions more than once on different machines.  Indeed, I'm currently using ver7 on my main workstation.

Have you tried it running congruity from a command line after having generated a file from having run concordance?  Depending on your results or error messages, you might be better off asking technical questions in the concordance forums since this thread covers mainly just the installation of those two utilities.

---

### Post by iitywygms on 2008-07-06
I would like to start over.  How can I completely remove what I installed?

---

### Post by marcw on 2008-07-06
To uninstall, you should be able to cd to each dir that you originally ran "sudo make install" and instead run "sudo make uninstall".  After that just delete the contents of each of those dirs.

I haven't tried this myself but this is pretty standard stuff and so should work.  Let me know if that doesn't work.

---

### Post by iitywygms on 2008-07-06
Traceback (most recent call last):
  File "/usr/bin/congruity", line 30, in <module>
    import libconcord
  File "/usr/lib/python2.5/site-packages/libconcord.py", line 30, in <module>
    _dll = cdll.LoadLibrary('libconcord.so.0')
  File "/usr/lib/python2.5/ctypes/__init__.py", line 431, in LoadLibrary
    return self._dlltype(name)
  File "/usr/lib/python2.5/ctypes/__init__.py", line 348, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: libconcord.so.0: cannot open shared object file: No such file or directory
kevin@ubuntu:~/source/congruity-7$ concordance
concordance: error while loading shared libraries: libconcord.so.0: cannot open shared object file: No such file or directory
kevin@ubuntu:~/source/congruity-7$ 


I removed everything I could find.  Reinstalled it using your recommended version.
This is the output.  I will give the concordance forums a try.
This looks really promising and I hope it works.  Thank you for posting a how to!

---

### Post by iitywygms on 2008-07-08
For some reason I had issues but it is now fixed!

FYI

I had to do this

kevin@ubuntu:~$ sudo ldconfig /usr/local/lib
then:
kevin@ubuntu:~$ ldd $(which concordance) 

Then to make permanent 

kevin@ubuntu:~$ sudo gedit /etc/ld.so.conf
and add /usr/local/lib to the end of that file. Then run:
kevin@ubuntu:~$ sudo ldconfig 

Special props to those who helped.

Now it works.  Thank you so much!!!!!!

:guitar:

---

### Post by marcw on 2008-07-08
Interesting.  I didn't have to do that because /usr/local/lib was already a shared library.  What is your output of:
cat /etc/ld.so.conf.d/libc.conf
?

---

### Post by iitywygms on 2008-07-08
kevin@ubuntu:~$ cat /etc/ld.so.conf.d/libc.conf
# libc default configuration
/usr/local/lib
kevin@ubuntu:~$ 

I wonder if this had been messed up for some time?  A while back I was trying to install jhmo and had a heck of a time.  I finally got it to run but I always have to do it as sudo. Odd??????

---

### Post by pudding on 2008-08-10
Ive followed the steps in the first post and I think everything seemed to work ok. I logged into the logitech site, made a few changes to my remote then went to update, and selected to open the file with congruity, but nothing happened. I have a .EZhex file on the desktop and opening this with congruity has no effect. Any ideas?

---

### Post by mrtomservo on 2008-08-22
Thanks so much for this how to!  I can confirm flawless installation on Hardy Heron,  with kernel 2.6.24-19-generic.  Harmony remote version 628, usb id 0400:c359.  

Also, Congruity is on version 8 now.  Concordance is still 0.20.

---

### Post by m-k-h on 2008-08-31
Here's what I had to do differently in order to get my 525 working (Ubuntu 8.04)
1) reboot was needed in order to device rights to change as configured (without this sudo was needed). Perhaps there's a special command for this?
2) I had to modify library search path as instructed (a new include line in the file mentioned) (without this, I got an error about library not found)

And it works! After this I only need Windows virtual machine for RAW photo work flow. I'll keep my thumbs up for proper replacements!

I wonder why Logitech does not support Linux officially as they already have a server side cross platform web site.

Thanks for the great tutorial. The projects used really could use some documentation contributions.

---

### Post by MarkRobert on 2008-09-05
Thanks, this worked for me with my 895.

---

### Post by HoldSteady on 2008-09-24
> tar -xvjf congruity-7.tar.bz2
tar -xvjf concordance-0.20.tar.bz2
cd concordance-0.20/libconcord
./configure
make
sudo make install
cd ../concordance
./configure
make
sudo make install
cd ../libconcord/bindings/python
sudo python setup.py install
cd ../../../../congruity-7
sudo make install

What directory am I supposed to untar these into?  I tried my home directory, but after running ./configure, it returned errors during make.

Also, I got **E: Couldn't find package python-wxaddons** after running the copied apt-get string.

---

### Post by marcw on 2008-09-25
> **HoldSteady said:**
> What directory am I supposed to untar these into?  I tried my home directory, but after running ./configure, it returned errors during make.

Also, I got **E: Couldn't find package python-wxaddons** after running the copied apt-get string.

Sounds like maybe you didn't follow the instructions in the first codebox:
```
cd
mkdir source
cd source
```

According to my Synaptic, python-wxaddons is located in the Universe repository which you were told to enable.

---

### Post by noremacyug on 2008-10-20
> **pudding said:**
> Ive followed the steps in the first post and I think everything seemed to work ok. I logged into the logitech site, made a few changes to my remote then went to update, and selected to open the file with congruity, but nothing happened. I have a .EZhex file on the desktop and opening this with congruity has no effect. Any ideas?

i have the same issue. any help?

(edit) - post 20 by iitywygms solved the issue.  thanks

---

### Post by slogger on 2008-10-28
once I get to set permissions "lsusb |grep -i logitech" I dont get the required response of "Bus 002 Device 007: ID 046d:c110 Logitech, Inc. "In other words no response.
What am I doing wrong?

---

### Post by marcw on 2008-10-28
> **slogger said:**
> once I get to set permissions "lsusb |grep -i logitech" I dont get the required response of "Bus 002 Device 007: ID 046d:c110 Logitech, Inc. "In other words no response.
What am I doing wrong?

It looks like I forgot to mention in the instructions that you have to have your Logitech plugged in to your computer prior to executing this step.

---

### Post by slogger on 2008-10-28
My remote is'nt being recognized at all by my computer even after setting permission. Is there a way to force this to happen?

---

### Post by marcw on 2008-10-28
> **slogger said:**
> My remote is'nt being recognized at all by my computer even after setting permission. Is there a way to force this to happen?

Aside from checking the obvious - bad cable, bad USB port, etc - I have no idea.  Do other USB devices e.g. thumb drive, camera, mp3 player, etc get recognized using that USB port and cable?  If so, it makes me wonder if maybe the port on your remote is bad.

---

### Post by slogger on 2008-10-28
I can get the remote to work on my winxp computer. 
Tested the usb port with another device which conncted with no problem.

Is it possible Im out of "sequence" when I set permission?

---

### Post by marcw on 2008-10-28
Sorry, I don't know.  Yours is a 8.04 (Hardy) computer, right?  You might want to try asking over in the hardware forum why your remote doesn't seem to register with lsusb when you plug it in.

---

### Post by stir-crazy on 2008-11-08
Think the install all went fine, but I don't seem to have (or am overlooking) the option to skip past the software update section on the website ([http://members.harmonyremote.com](http://members.harmonyremote.com)).

Is there an updated address?

---

### Post by marcw on 2008-11-08
No, that address is still valid.  When I go there I get the Logitech "Software Update Available" page which is the one you should ignore.  If you don't get that page then there is nothing to ignore, I guess.

---

### Post by Surfrock66 on 2008-12-03
> **iitywygms said:**
> For some reason I had issues but it is now fixed!

FYI

I had to do this

kevin@ubuntu:~$ sudo ldconfig /usr/local/lib
then:
kevin@ubuntu:~$ ldd $(which concordance) 

Then to make permanent 

kevin@ubuntu:~$ sudo gedit /etc/ld.so.conf
and add /usr/local/lib to the end of that file. Then run:
kevin@ubuntu:~$ sudo ldconfig 

Special props to those who helped.

Now it works.  Thank you so much!!!!!!

:guitar:

I was getting this error, when you get to the (which concordance) part, what goes there?  I'm kind of n00b at this, thanks.

---

### Post by pormogo on 2008-12-03
I've been considering the logitech harmony 550 remote for my house. The only thing holding me back from getting it is the worry that I won't be able to program my new remote without a windows install. I have virtualbox installed on my laptop for a few applications (I use the non-free ed with alleged USB support). I say alleged because I have never gotten it to function. The only thing I have tried is my phone, it sees the device ID however active sync just can't connect to the phone... It refuses to see it (and since MS thinks no one needs any kind of logging...) explorer seems to see my phone as does the device manager, but nothing can see the folders on the phone etc etc. 

I was worried about running into a similar issue with the harmony remote. I'm pretty sure that's something specific with my phone. Just wanted to see if anyone had run into issues with running the logitech software inside virtialbox.

---

### Post by kernelhaxor on 2008-12-04
Interesting.  THanks for the How-to!

---

### Post by Bauldrick on 2008-12-19
I've had this setup for agaes and it's always worked brilliantly. Just lately it's saying that my Harmony 525 has firmware 2.6 and latest is 3.0 and tries to update the firmware, but ofcourse fails at it's not supported yet... anyone else have this issue or has a recent update broken something, or have I just forgotten how to do it?  ?

dmesg |tail shows:

[ 1137.616723] sd 8:0:0:3: [sdf] Attached SCSI removable disk
[ 1137.617241] sd 8:0:0:3: Attached scsi generic sg6 type 0
[ 1597.176056] usb 2-2: new full speed USB device using ohci_hcd and address 3
[ 1597.406068] usb 2-2: configuration #1 chosen from 1 choice
[ 1631.253152] congruity[7839]: segfault at ffffffffc619e840 ip 00007f51d02f66b0 sp 00007fffd90a8ba8 error 4 in libc-2.8.90.so[7f51d0274000+169000]
[ 2620.946365] congruity[8659]: segfault at ffffffff84b1f840 ip 00007f568ec776b0 sp 00007fff97a2a708 error 4 in libc-2.8.90.so[7f568ebf5000+169000]
[ 2645.640514] usb 2-2: USB disconnect, address 3
[ 2648.880077] usb 2-2: new full speed USB device using ohci_hcd and address 4
[ 2649.110486] usb 2-2: configuration #1 chosen from 1 choice
[ 2710.810110] congruity[8706]: segfault at 10046840 ip 00007f231a19e6b0 sp 00007fff22f4fc38 error 4 in libc-2.8.90.so[7f231a11c000+169000]

---

### Post by Jepser on 2008-12-26
This HOWTO was very helpful, everything works well except when I am supposed to check the connection between my Harmony One and my computer. My computer can't find the remote. I have tried with the tip in post #20 but it didn't work and I was doing wrong. 

I have used concordance 0.2 and booth congruity 7 and 9 with the same result. When i try to connect is the browser blank and congruity says that it couldn't find my remote. I have done everything in the HOWTO without any errors.

---

### Post by marcw on 2008-12-26
lsusb doesn't find your remote?  You might want to ask over in the hardware forum about that.  Whether Concordance works or not is a seperate issue.  lsusb should always report on your USB devices correctly.

---

### Post by Jepser on 2008-12-26
I have had contact with Phil Dibowitz, the developer of concordance. Concordance hasn't support for my remote, Harmony One. The command lsusb found my remote so that wasn't the problem, the problem where that conginity didn't find my remote.

I hope that there gonna be support for Harmony One soon.

---

### Post by hanslinux on 2008-12-30
I get the following error in congruity (version 8 and 9):

ERROR: Precisely one filename argument is required

Traceback (most recent call last):
  File "/usr/bin/congruity", line 1219, in main
    raise CmdLineException("ERROR: Precisely one filename argument is required")
CmdLineException: ERROR: Precisely one filename argument is required


Anybody any idea?
I'm using Hardy amd64.

---

### Post by hanslinux on 2009-01-03
The error 
ERROR: Precisely one filename argument is required

was caused by the fact that I didn't start congruity from the Logitech website but as an application. I'm sorry I've not read the howto completely.

---

### Post by tpeerd on 2009-01-04
When I use Congruity 9 the first time, the Congruity window comes up and disappears. The second time opening the Update.EZHex file it works, untill nearly the end, where it reads 'Reconnect to remote', it disappears again, but the updating of my Harmony 525 is done anyway. Am I the only one with this problem?
I use Intrepid Ibex 64-bit.

---

### Post by stoggy on 2009-01-11
I am also getting the segfault in libc-2.8.90...  I get this just trying to upload the file after editing the remote settings on the website.

Jan 11 01:16:12 PC kernel: [ 8820.556407] congruity[27067]: segfault at fffffffff772a5c0 ip 00007f74018826b0 sp 000000004162aba8 error 4 in libc-2.8.90.so[7f7401800000+169000]

---

### Post by stoggy on 2009-01-11
I figured out my segfault problem.  If I used root no error msgs, so it had to be permissions.

In this HOW-TOS instructions it says to echo 'yada yada' | sudo tee /etc/udev/rules.d/custom-concordance.rules

This didnt work for me.  I had to follow the destructions in the udev rules.d files.  In the readme /etc/udev/rules.d/README it says that the rules files should start with a number which indicates when rules should be loaded, sort of like sysVinit init scripts S[0-9]*someinitscipt, minus the "S" and "K" in this case.

so i had to do this instead: (* I am using ubuntu 8.10 w/ udev version 124-9 *) (* note I have a 676 so my Vendor and Product IDs are different. *)

echo 'SYSFS{idVendor}=="0400", SYSFS{idProduct}=="c359", MODE="666"' |sudo tee /etc/udev/rules.d/40-concordance.rules


I chose 40 because it is supposedly for udev rules that change permissions, and that sounded like what i needed.

As soon as i did this and replugged in the remote, I was able to update my remote's configuration from the website w/ congruity.

You might want to add a part to the initial post for 124-9 udev or maybe it is just ubuntu 8.10.

Thanks for the howto this rocks!!!  WOW i just saw how old this thread is...

---

### Post by Peepsalot on 2009-01-14
Have any of you successfully had your remote learn a new IR command?  I have a Harmony 550 and when I go through the steps on the Logitech site to learn a command, it gives me a file to download called LearnIR.EZTut

When I run this file with congruity, it tells me the error message:
> Unrecognized file type '3' returned by libconcord

---

### Post by yadster on 2009-01-16
Hi
I am new to Linux and like it a lot but get fustrated when things that work stop working!  I have a logitech remote and had configured it using the methods discribed in this forum.  I went to update some changes I wanted to make to the remote and now constantly getting the following error message -
Unknown error

Traceback (most recent call last):
  File "/usr/bin/congruity", line 64, in program
    program_body_connect(program_callback, handler, need_deinit)
  File "/usr/bin/congruity", line 93, in program_body_connect
    handler_f
  File "/usr/lib/python2.5/site-packages/libconcord.py", line 57, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

I am not able to update the remote due to this.  I have gone back to the first post and followed the instructions and still not having any luck.  Can anyone help?

Thanks

---

### Post by outofthenorth on 2009-01-22
Im in ubuntu 8.10 and after following the instructions in this thread i am still having the problem with congruity-9 where it pops up the message 'could not load libconcord; please ensure it, and the Python bindings, are installed and in the relevant search paths'.

I used strace to confirm that it was finding libconcord and loading it, and I do believe that I have installed the python bindings, and I have set up the udev rule with the correct data from lsusb.  Anyone have any ideas what else to look at?

concordance -i works and returns the following:

~$ concordance -i
Concordance 0.20
Copyright 2007 Kevin Timmerman and Phil Dibowitz
This software is distributed under the GPLv3.

Requesting Identity: 100%                 done
  Model: Logitech Harmony 550 (Mocha Grande)
  Firmware Version: 2.6
  Hardware Version: 3.0
  Config Flash Used: 15% (62 of 384 KiB)

Success!
~$

---

### Post by jeffreylammers on 2009-02-22
> **yadster said:**
> Hi
I am new to Linux and like it a lot but get fustrated when things that work stop working!  I have a logitech remote and had configured it using the methods discribed in this forum.  I went to update some changes I wanted to make to the remote and now constantly getting the following error message -
Unknown error

Traceback (most recent call last):
  File "/usr/bin/congruity", line 64, in program
    program_body_connect(program_callback, handler, need_deinit)
  File "/usr/bin/congruity", line 93, in program_body_connect
    handler_f
  File "/usr/lib/python2.5/site-packages/libconcord.py", line 57, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

I am not able to update the remote due to this.  I have gone back to the first post and followed the instructions and still not having any luck.  Can anyone help?

Thanks

Yadster - I'm having the same issue.  I'm digging into it, but no solution yet. I'm thinking either the contents of the custom-concordance.rules file are incorrect or perhaps the permissions on that file are not correct.  I'll post back with any findings.

Thanks to markw for the instructions and iitywygms for the hints on getting the dynamic modules to link properly.  Would not have gotten this far otherwise...

Update....
I'm still not able to get this to work.  I have a Harmony One remote and I could not find any info to say that this device either is or is not supported.  Has anyone gotten concordance to work with a Harmony One?

I ran an strace on concordance with switches to print remote info (strace sudo concordance -v -i) and at a couple of points in the dump I saw the following message:

ioctl(3, USBDEVFS_IOCTL, 0xbf801ecc)    = -1 ENOTTY (Inappropriate ioctl for device)

This leads me to believe that the Harmony One is using some different i/o protocol (possibly the same as the 1000?) that is not supported.

Anyone have any info on this?

Thanks.

---

### Post by dirklc on 2009-03-02
Followed the instructions on post #1 followed by post #20.  I'm a complete noob and still worked like a charm (Harmony 880 on Ubuntu 8.10).

Also, followed the instructions here to update Congruity & Concordance packages via apt:
[http://blog.cyphermox.net/2008/07/update-congruity-concordance-packages.html]("http://blog.cyphermox.net/2008/07/update-congruity-concordance-packages.html")

Thanks, guys.  Really appreciate the step-by-step instructions.

---

### Post by AmbiguousOutlier on 2009-03-18
I've just bought a harmony one and I'm getting the following error. I've tried uninstalling version 10 and installing 7 but that didn't work, and other than doing that my knowledge of Ubuntu is limited.

Can anyone help?

```

Error connecting or finding the remote
    (libconcord function init_concord error 11)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 521, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 132, in worker_body_connect
    libconcord.init_concord()
  File "/usr/lib/python2.5/site-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'init_concord' failed with error code 11 ('Error connecting or finding the remote')

```

This error is in the congruity GUI when trying to detect the remote.

---

### Post by marcw on 2009-03-18
> **RhysGM said:**
> I've just bought a harmony one and I'm getting the following error. I've tried uninstalling version 10 and installing 7 but that didn't work, and other than doing that my knowledge of Ubuntu is limited.

I recall a post earlier in this thread from someone saying they had contacted the author and was told that Congruity doesn't yet support Harmony One.  You probably want to read through this thread just to make sure I haven't lost my marbles.

---

### Post by AmbiguousOutlier on 2009-03-20
> **marcw said:**
> I recall a post earlier in this thread from someone saying they had contacted the author and was told that Congruity doesn't yet support Harmony One.  You probably want to read through this thread just to make sure I haven't lost my marbles.

I did see that, I was just hoping it wasn't true or that it had now been resolved.

---

### Post by daxdog on 2009-03-24
Whenever I do the install for Concordance 0.21 I get "Error, libusb is missing!"  I have libusb-0.1-4 installed.  If I try to uninstall it a lot of things want to uninstall.  What can I do?

---

### Post by marcw on 2009-03-24
> **daxdog said:**
> Whenever I do the install for Concordance 0.21 I get "Error, libusb is missing!"  I have libusb-0.1-4 installed.  

Yeah, but do you have libusb-dev installed like it says in the instructions?

---

### Post by tpeerd on 2009-05-04
I have the same problem, but I own a Harmony 525. It did work earlier, in Ubuntu 8.04, but now in 9.04 the 525 isn't being detected anymore.

Failure
No remote could be found
See below for details

Error connecting or finding the remote
    (libconcord function init_concord error 11)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 521, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 132, in worker_body_connect
    libconcord.init_concord()
  File "/usr/local/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'init_concord' failed with error code 11 ('Error connecting or finding the remote')

---

### Post by PowerRanger on 2009-05-05
I have the same problem as TPEERD.  Updated to 9.04, now I can't program the remote.  Same error. only difference is mine is a 550.

TIA 

edit>> Marc-- I saw you post to the concordance-devel list, it's good to know you're on working on the solution.


Mike

---

### Post by smet_dk on 2009-05-05
I got it working in Jaunty. I had to do:

```
echo 'SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c111", MODE="666"' |sudo tee /etc/udev/rules.d/custom-concordance.rules
```For my 525.... It didn't work when using 40-concrodance.rules ad filename.

Not sure if "sudo chmod -s" is necessary on the executables...

---

### Post by smet_dk on 2009-05-05
> **smet_dk said:**
> Not sure if "sudo chmod -s" is necessary on the executables...

It's not

---

### Post by PowerRanger on 2009-05-05
That fix worked for me.  Thanks.  :)

---

### Post by marcw on 2009-05-05
> **smet_dk said:**
> I got it working in Jaunty. I had to do:

```
echo 'SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c111", MODE="666"' |sudo tee /etc/udev/rules.d/custom-concordance.rules
```For my 525.... It didn't work when using 40-concrodance.rules ad filename.

Not sure if "sudo chmod -s" is necessary on the executables...

Thanks smet_dk!  This change was tested and included in the original post.

---

### Post by jtratcliff on 2009-05-09
I also had to do (for Jaunty):

  make policykit
  sudo make install_policykit

in the libconcordance directory and 
then reboot (I didn't try just a logout to see if that was enought)
in order to make concordance not require sudo to work.

Once that was done, worked like a charm for my 550

---

### Post by Huntly on 2009-05-16
> **jtratcliff said:**
> I also had to do (for Jaunty):

  make policykit
  sudo make install_policykit

in the libconcordance directory and 
then reboot (I didn't try just a logout to see if that was enought)
in order to make concordance not require sudo to work.

Once that was done, worked like a charm for my 550

Cheers Jtratcliff, the policykit bit worked like a charm for me.

---

### Post by rperkins on 2009-05-28
I didnt have to do this with jaunty amd64
I did have to unplug and replug in the usb cable for the remote to get the updated permissions.

I just wanna say thanks so much.
this how to worked perfectly and I appreciate the effort to keep it updated as ubuntu moves forward.  When I first got my harmony remote , using it in linux was just a dream, and now it worked flawlessly when I changed cable providers and needed to update my settings.  I also sucessfully updated my firmware .  i have a harmony 880 ( i think)


> **jtratcliff said:**
> I also had to do (for Jaunty):

  make policykit
  sudo make install_policykit

in the libconcordance directory and 
then reboot (I didn't try just a logout to see if that was enought)
in order to make concordance not require sudo to work.

Once that was done, worked like a charm for my 550

---

### Post by racerraul on 2009-06-01
Great Tutorial...
I have a Harman TC-30 (Harmony 880 rebranded) and was sad to find out HK broke their windows app with the latest update and have since stopped support for the remote...

But tried this tutorial, and Linux see it with the same USB ID as the 880, did the update and it worked... freaking awesome.

My remote gets a new life in Linux...

---

### Post by rthmchgs on 2009-06-10
I have recently installed the netbook version of Jaunty on a dell mini 9 and while this set of instructions worked with 8.10, I am still having trouble.  I can get the website to recognize the remote and change stuff, but the programming on the remote does not change after I disconnect it.

I think I tried the policykit stuff, but I am not sure.  Where is the libconcordance directory?  Thanks.

Pat

---

### Post by Cuba71 on 2009-06-21
First of all, thanks to Marc and the others that are making this possible. Today, I decided to give it a try and this is the outcome. I have checked and the 610 is supposed to be working

Jaunty 9.04
concordance-0.21
congruity-12
Logitech Harmony 610
===========================

I went through the installation following the instrucciones at the beginning of the thread, and adding the 'policykit' commands.
The software fails to find the remote, even it's recognized by the system.

Here are the messages:

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c111 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
and these are the messages from congruity:
```

Error connecting or finding the remote
    (libconcord function init_concord error 11)
Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 524, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 135, in worker_body_connect
    libconcord.init_concord()
  File "/usr/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'init_concord' failed with error code 11 ('Error connecting or finding the remote')

```

Any help will be appreciated.

**(update)  Problem was caused by an extra character "}" in the common-concordance.rules file** Now it works great with my Harmony 610.

Thanks to all !!!

---

### Post by rthmchgs on 2009-07-11
Update: I tried again with Ubuntu 9.04, concordance 0.21 and congruity 12, with the policykit change and everything works great.  Thanks.

---

### Post by lingenfr on 2009-07-11
I just got mine label H688. When I plug it in, dmesg says:

[ 1533.832077] usb 2-1: new full speed USB device using uhci_hcd and address 6
[ 1534.065018] usb 2-1: configuration #1 chosen from 1 choice

but it doesn't show up with lsusb. I ran through the instructions up to that point. When lsusb did not show the remote I rebooted and have plugged/unplugged several times. Any ideas? I am running Jaunty.

---

### Post by Robbyx on 2009-07-14
Harmony 680 on Intrepid

I have got as far as logging into the HarmonyRemote web site. It informs me that there is an upgrade in the software that is available. I click next and there is only the option to download connectivity.ezhex.  If I cancel and do not download there is no follow on screen. Just an empty tab that occasionally says LOADING in the tab bar, but nothing appears below.

So I decided to exit from the browser and run congruity from the command line. The following is the failure error:

ERROR: Precisely one filename argument is required

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 1932, in main
    raise CmdLineException("ERROR: Precisely one filename argument is required")
CmdLineException: ERROR: Precisely one filename argument is required


What should I do next?

---

### Post by marcw on 2009-07-14
> **Robbyx said:**
> I have got as far as logging into the HarmonyRemote web site. It informs me that there is an upgrade in the software that is available. I click next and there is only the option to download connectivity.ezhex.  If I cancel and do not download there is no follow on screen. Just an empty tab that occasionally says LOADING in the tab bar, but nothing appears below.

Do you have a pop up blocker turned on in your browser?  I allow pop ups from both harmonyremote.com and members.harmonyremote.com.  Alternately, just turn it off altogether, at least for testing.

---

### Post by Robbyx on 2009-07-15
> **marcw said:**
> Do you have a pop up blocker turned on in your browser?  I allow pop ups from both harmonyremote.com and members.harmonyremote.com.  Alternately, just turn it off altogether, at least for testing.

I both allowed and turned off the popups.  I still can not see a way to skip to the setup mode of the Harmony. In Ubuntu I still get the searching but not finding tab. It may be to do with the Harmony freezing following a firmware upgrade.


I went to a friends winxp computer and installed the software on it and upgraded the firmware. This happened automatically.  So I know that the Harmony was working.Since the upgrade I get a screen message that the Firware upgrade was successful and the machine does not react to any button pushes. It does not reset when  I take the batteries out. Is there a reset button?

What should  I do next.

---

### Post by Zvarri on 2009-07-15
> **jtratcliff said:**
> I also had to do (for Jaunty):

  make policykit
  sudo make install_policykit

in the libconcordance directory and 
then reboot (I didn't try just a logout to see if that was enought)
in order to make concordance not require sudo to work.
Could you explain a bit better exactly how and where to do this? I've found a libconcord directory, but no libconcordance, and I can't convince Terminal to navigate to the libconcord dir, much less install anything there.

---

### Post by Robbyx on 2009-07-15
> **Robbyx said:**
> I both allowed and turned off the popups.  I still can not see a way to skip to the setup mode of the Harmony. In Ubuntu I still get the searching but not finding tab. It may be to do with the Harmony freezing following a firmware upgrade.


I went to a friends winxp computer and installed the software on it and upgraded the firmware. This happened automatically.  So I know that the Harmony was working.Since the upgrade I get a screen message that the Firware upgrade was successful and the machine does not react to any button pushes. It does not reset when  I take the batteries out. Is there a reset button?

The supplier says that I should not worry about the screen freeze. I should go ahead and program the remote via the logitech site. Great if I could do it. Please see my last posting above. Could I please have some further advice on how to avoid the software upgrade demand from the logitech web site? 

What should  I do next.

---

### Post by Robbyx on 2009-07-16
Could someone help me enable Ubuntu to see the Harmony remote. I now realise this is the problem I have been having.

From the first post in this topic:
> lsusb |grep -i logitech

You should see something similar to this:
Quote:
Bus 002 Device 007: ID 046d:c110 Logitech, Inc. 


The above command only shows the logitech mouse not the Harmony remote.

Is there a way to enable it to see the remote and report its device details.

---

### Post by Cuba71 on 2009-07-17
Run "lsusb" before and after plugin in the remote, you should get something like this:

```

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c111 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Let's know what you get

---

### Post by Robbyx on 2009-07-17
I can see from the below that the Harmony is being picked up as:

Bus 003 Device 010: ID 0400:c359 National Semiconductor Corp.

I therefore did the following:

> rob@rob-desktop:~$ echo 'SYSFS{idVendor}=="0400", SYSFS{idProduct}=="c359", MODE="666"' |sudo tee /etc/udev/rules.d/custom-concordance.rules
[sudo] password for rob: 
SYSFS{idVendor}=="0400", SYSFS{idProduct}=="c359", MODE="666"


I have then gone to [http://members.harmonyremote.com/](http://members.harmonyremote.com/)

If I refuse to download the update software the tab clears and the tab name flashes to show it is trying to access the remote. Nothing happens. Popups are not being blocked for members.harmonyremote.com

Robin


Before:

rob@rob-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 058f:6335 Alcor Micro Corp. 
Bus 001 Device 003: ID 03eb:0902 Atmel Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
After:

rob@rob-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 010: ID 0400:c359 National Semiconductor Corp. 
Bus 003 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 058f:6335 Alcor Micro Corp. 
Bus 001 Device 003: ID 03eb:0902 Atmel Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Cuba71 on 2009-07-17
I'm not sure if this has anything to do with your problem, but I have configured Firefox to run "congruity" automatically when downloading files of type "ezhex".

This is a pix of all the steps the software goes to update the remote, as you can see there's a lot of interaction between the remote and the web page

---

### Post by Robbyx on 2009-07-17
> **Cuba71 said:**
> I'm not sure if this has anything to do with your problem, but I have configured Firefox to run "congruity" automatically when downloading files of type "ezhex".

This is a pix of all the steps the software goes to update the remote, as you can see there's a lot of interaction between the remote and the web page

I assume this is not a response to my last  posting above?

---

### Post by Cuba71 on 2009-07-18
I was only trying to describe how I process the files being downloaded from the Harmony web site.  I think it's possible to start congruity manually from Terminal but I have never done it.

---

### Post by Robbyx on 2009-07-18
> **Cuba71 said:**
> I was only trying to describe how I process the files being downloaded from the Harmony web site.  I think it's possible to start congruity manually from Terminal but I have never done it.

Congruity starts from the terminal's command line, however I get an error message when I type just the name, as follows:

ERROR: Precisely one filename argument is required

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 1932, in main
    raise CmdLineException("ERROR: Precisely one filename argument is required")
CmdLineException: ERROR: Precisely one filename argument is required

It looks as if I need to add something to the command line. Any ideas what?


I have also tried some other lsusb commands as follows:

lsusb -D 0400  
       Can not open 0400              
lsusb -d 003
       Useage is wrong and gives help list

lsusb -v
       It does not show the harmony bus entry.

```
bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.27-14-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc051 G3 (MX518) Optical Mouse
  bcdDevice           30.00
  iManufacturer           1 Logitech
  iProduct                2 USB-PS/2 Optical Mouse
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      77
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.27-14-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0303 lowspeed power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x051d American Power Conversion
  idProduct          0x0002 Uninterruptible Power Supply
  bcdDevice            0.06
  iManufacturer           3 American Power Conversion
  iProduct                1 Back-UPS CS 500 FW:808.q5.I USB FW:q5
  iSerial                 2 BB0526019467  
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength    1216
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0006  1x 6 bytes
        bInterval             100
Device Status:     0x0001
  Self Powered

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.27-14-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0303 lowspeed power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 004: ID 058f:6335 Alcor Micro Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x6335 
  bcdDevice            1.02
  iManufacturer           1 Generic
  iProduct                2 Mass Storage Device
  iSerial                 3 058F011111B1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              250mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 003: ID 03eb:0902 Atmel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0         8
  idVendor           0x03eb Atmel Corp.
  idProduct          0x0902 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
        ** UNRECOGNIZED:  09 29 04 09 00 32 64 00 1e
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0x1e
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.27-14-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled
rob@rob-desktop:~$ 


```

---

### Post by LilYoda on 2009-07-19
I have a question

My existing remote sends multiple IR codes for each action.  When I created my custom lircd.conf file, I had to specify several sequences of codes received for each action

Now what I'd like to do, is to be able on my harmony 525 to send each of these codes individually.  Why?  Because that woudl allow me to create more combinations of codes, and therefore more actions than I have on my original remote

Does that sound feasible to you guys?  It might require editing some of those files before they are posted back to the harmony website, or something of the sort.  Either that or understanding the "Pronto Hex" thingy that congruity talks about when I try to learn an IR code.

Anyone has a clue?

---

### Post by Robbyx on 2009-07-19
I hope I am going to get a reply to my posting #85, failing that does anyone know of a support forum for congruity?

---

### Post by Robbyx on 2009-07-22
I could not get Virtualbox to communicate with the Harmony. I have had to install windows on a seperate drive, install the video driver and then log into the Logitech upgrade site via their software. First I had to wipe the handset of the previous installation:

Re Harmony 680

Remove batteries
initiate Logitech software
Hold OFF button down whilst connecting to USB
Wait 15 sec until "safe mode requested" on remote screen
Allow update of handset

Whist in the Logitech site set up a device. This makes all the difference because with the batteries back in and a revisit to the site I was able to skip the sofware upgrade. There were much more options.

---

### Post by Robbyx on 2009-07-22
Having saved to my Ubuntu desktop the Connectivity.EZHex file I have assumed this is needed by congruity. I therefore entered into the terminal:

rob@rob-desktop:~$ congruity Connectivity.EZHex

It does not work proprely 

```
OS-level error related to file operations
    (libconcord function read_file error 14)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 376, in _WorkerFunction
    byref(xml_size)
  File "/usr/lib/python2.5/site-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'read_file' failed with error code 14 ('OS-level error related to file operations')

```

Any ideas how to upgrade the remote?

At least now I can use VirtualBox. Since the software upgrade I was able to get VB to recognise the USB. It needed the driver installed from the Windows upgrade centre.

---

### Post by Cuba71 on 2009-07-27
> **Robbyx said:**
> I hope I am going to get a reply to my posting #85, failing that does anyone know of a support forum for congruity?

There's a support site for Concordance at [concordance-devel]("https://lists.sourceforge.net/lists/listinfo/concordance-devel")

In the Concordance tarball there's a README file on how to run from Terminal.

Hope this helps

---

### Post by Robbyx on 2009-07-27
Thank you for your last comment. I will investigate it further.

---

### Post by Robbyx on 2009-07-27
```

rob@rob-desktop:~$ whereis libconcord
libconcord: /usr/local/lib/libconcord.la /usr/local/lib/libconcord.so /usr/local
rob@rob-desktop:~$ concordance
bash: concordance: command not found

```

In order to run concordance from the terminal should I change directory. If so can you please indicate to which one I switch?

---

### Post by Robbyx on 2009-07-28
I have gone over the instructions again and am now using congruity successfully. The repository did not work for me. I would prefer to use that method. The entries are in my software updates including the verification code and there are no error messages on exit. I think it is not updating concordance. Is there a way to test it?

---

### Post by Robbyx on 2009-07-28
Is there a way of training the harmony with my original remote?

---

### Post by Robbyx on 2009-08-01
> **Robbyx said:**
> Is there a way of training the harmony with my original remote?

Does anyone know the answer?  It looks like I will have to train the Harmony with my original remote because the TV is not turning on. I would prefer to use Ubuntu.

---

### Post by Cuba71 on 2009-08-06
I have installed concordance-0.21 and congruity-10 according to the instructions on this thread and working properly with my Harmony 610.

My question is:  how do I upgrade to congruity-13?  I've already downloaded contruity-13.tar.bz2.

Thank you

---

### Post by marcw on 2009-08-06
> **Cuba71 said:**
> My question is:  how do I upgrade to congruity-13?  I've already downloaded contruity-13.tar.bz2.Thank you

First off, if your current setup is working correctly, I would advise you to **not** upgrade.  That said...

I haven't tried this yet but this is probably how to proceed:
1) uninstall the old one first - from a terminal, change to your old congruity-10 directory and run the following
   sudo make uninstall
2) back up one directory to the parent of where you had congruity-10 and place your new conruity archive here.
3) extract your new congruity from here.  It should create a directory called congruity-13.
4) finish the installation following the original instructions.

---

### Post by Cuba71 on 2009-08-07
Thnank you marcw, I'll follow your advice of not upgrading.

---

### Post by joutsen on 2009-09-27
The instructions on the first post worked perfectly for me in Jaunty and with congruity-13, with the change that I used this for HAL:

```

echo 'SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c111", MODE="666"' |sudo tee /etc/udev/rules.d/custom-concordance.rules

```

Request updating the original post accordingly.

Thanks for the howto!

---

### Post by Cuba71 on 2009-09-27
I tried the installation on Karmic Alpha 6 and python-wxaddons is not there.

Don't know how to proceed.

---

### Post by marcw on 2009-09-27
> **Cuba71 said:**
> I tried the installation on Karmic Alpha 6 and python-wxaddons is not there.

Don't know how to proceed.

Me neither.  But then again, I haven't tried.  I'm not going to put any effort into altering the original instructions until sometime after the real release of Karmic.

---

### Post by agibby5 on 2009-09-28
This tutorial worked great! In fact, I got so tired of waiting the windows Harmony software on my Windows PC to become unfrozen just to update my remote config.  I followed this tutorial, downloaded, built, installed, ran, used the software and programmed my remote in less time (about 5 minutes) than it took the Harmony software to become unfrozen and usable!!  Great stuff!  PS. it went without a hitch!

---

### Post by KMSMD on 2009-09-30
I've tried everything in these posts and I can't get anything to work.  The computer won't recognize my remote.  USB port works for everything else, but not my Harmony Remote (I have 3 and none of them are recognized).  I have Congruity and Concordance installed, yet still nothing.

---

### Post by Robbyx on 2009-10-02
I am running congruity via firefox. I would like to create a desktop Icon that auto loads firefox and goes immediately to the members.harmony web site as if it was a standalone  program. I think there is a program that does this but I have forgotten its name. I used it once to run a google translate program from the desktop. 


Does anyone recall a program that will run firefox in this manner?

Robin

---

### Post by Cuba71 on 2009-10-03
You could create a launcher on your desktop with the command:

*firefox -url [http://yoururlname.com](http://yoururlname.com)*

---

### Post by Robbyx on 2009-10-03
> **Cuba71 said:**
> You could create a launcher on your desktop with the command:

*firefox -url [http://yoururlname.com](http://yoururlname.com)*

Thanks

---

### Post by mycroft616 on 2009-10-12
Hi to all,

I'm new with Ubuntu and with this forum. I found this great thread. As I learned concordance do not support the Harmony 895 and 900. One User posted that he had success in getting the Harmony 895 working with concerdance. Can anybody confirm this. 
For me it would be important to get the 895 running. 

Have anybody some more information about the new models from Logitech. 900/1100.


Thank you.
Best Regards
mYCROFT

---

### Post by incywebb on 2009-10-19
Hi all,

I'm reasonably new to this all too.  I followed the very clear tutorial, thanks for that.

I've got a Harmony one; lsusb | grep -i logitech shows it thusly:

Bus 004 Device 003: ID 046d:c121 Logitech, Inc.

I added these details to the rules file correctly, I believe:

$cat /etc/udev/rules.d/custom-concordance.rules
SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c121", MODE="666"

When I try to update my remote via the members.harmonyremote.com site it successfully kicks off congruity version 10, but then fails to detect my remote, with the following log:

Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 521, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 137, in worker_body_connect
    None
  File "/usr/local/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

I'm quite prepared to believe this is error-occurred-between-chair-and-keyboard :-) but how do I rearrange the furniture to make it work?

Thanks.

(longer output of sudo strace concordance -v -i can be given, but I think the relevant bit is:

open("/dev/bus/usb/004/003", O_RDWR)    = 4
ioctl(4, USBDEVFS_CONNECTINFO, 0xbfc3ea44) = 0
read(4, "\22\1\0\2\0\0\0\10m\4!\301T\20\1\2\0\1"..., 18) = 18
read(4, "\t\2)\0\1\1\1\300"..., 8)      = 8
read(4, "2\t\4\0\0\2\3\0\0\0\t!\0\1\0\1\"!\0\7\5\201\3@\0\1\7\5\2\3@\0\1"..., 33) = 33
close(4)                                = 0


this certainly appears to be attempting to read where the remote is connected but I can't dephier if it's reading it wrong or interpreting it wrong)

---

### Post by marcw on 2009-10-20
> **incywebb said:**
> 
I've got a Harmony one; lsusb | grep -i logitech shows it thusly:

When I try to update my remote via the members.harmonyremote.com site it successfully kicks off congruity version 10, but then fails to detect my remote, with the following log:

Unknown error
    (libconcord function get_identity error 1)


iirc, someone posted earlier in this thread that libconcord did not yet support the Harmony One.

I'll be updating this how-to for Karmic in a few weeks and will check to see if libconcord has updated their supported products at that time.

---

### Post by incywebb on 2009-10-20
> **marcw said:**
> iirc, someone posted earlier in this thread that libconcord did not yet support the Harmony One.

I'll be updating this how-to for Karmic in a few weeks and will check to see if libconcord has updated their supported products at that time.

Sorry, you're quite correct. I read the posting in question but the error code was different and I must have skimmed it.

---

### Post by iamgeniusrnti on 2009-10-24
Well install worked like a charm and everything did as it was supposed to... that is all the way up till the program launches and apparently can't find the remote.  Here is the feedback:

Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 521, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 137, in worker_body_connect
    None
  File "/usr/local/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

I am a newb, but I think I covered my bases.  I checked lsusb and it shows the remote along with making sure it matches the file created in the udev directory.

This is the same as the last guy wrote about so I guess I am wondering if they ever made support avail for Harmony One.  Thanks!

---

### Post by iamgeniusrnti on 2009-11-07
Still no dice?

---

### Post by Cuba71 on 2009-11-07
Just to double check, please type the following commands after connecting the remote, and post the results, and also, indicate the remote model

```

lsusb
cat /etc/udev/rules.d/custom-concordance.rules

```

---

### Post by iamgeniusrnti on 2009-11-07
Mom went to hospital so I am away from that laptop right now.  I will post again when I get back next week.

---

### Post by Giantmundo on 2009-11-08
Firstly a great HOWTO.  Just thought I would let others know that I could not get Congruity 10 working.  However as soon as I upgraded to Congruity 13 ... bang ...worked like a charm.  I suggest it might be time to update the HOWTO to Congruity 13.

---

### Post by schelf on 2009-11-21
Received my 895 today, so went ahead with the how-to.
Installation went smooth but then also got the connection error.
If I run concordance -i as a normal user I also get the same error.
If I run concordance -i as root I do get a connection.
So it seems the udev rules file is ignored.
For which version of udev is this written?
BTW I'm using Ubuntu 9.10

---

### Post by Cuba71 on 2009-11-21
> **schelf said:**
> 
BTW I'm using Ubuntu 9.10

Last time I tried the install on Karmic 9.10, the module python-wxaddons was not found.  Have this been corrected?

---

### Post by schelf on 2009-11-27
> **Cuba71 said:**
> Last time I tried the install on Karmic 9.10, the module python-wxaddons was not found.  Have this been corrected?

No, I did not install that package.
And I did not ran into any trouble doing so.
Now the only thing is to hope for is that the 895 gets supported soon...

---

### Post by CuBone on 2009-12-07
I have a harmony 555 nut I cant get Congruity to detect my remote. 

Congruity version is 13

When I try to update my remote I get 

```
Error connecting or finding the remote
    (libconcord function init_concord error 11)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 524, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 135, in worker_body_connect
    libconcord.init_concord()
  File "/usr/local/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'init_concord' failed with error code 11 ('Error connecting or finding the remote')

```

---

### Post by Solarisphere on 2009-12-07
> **Cuba71 said:**
> I tried the installation on Karmic Alpha 6 and python-wxaddons is not there.

Don't know how to proceed.

I had the same issuse in the final release of karmic. Apparently the packages have changed names. Using Synaptic Package Manager I searched for "wxpython" and then installed python-wxtools, python-wxversion, and
python-wxgtk2.8. I haven't got it working yet, but I don't think it has anything to do with packages not being installed.

> **iamgeniusrnti said:**
> Well install worked like a charm and everything did as it was supposed to... that is all the way up till the program launches and apparently can't find the remote.  Here is the feedback:

Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 521, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 137, in worker_body_connect
    None
  File "/usr/local/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

I am a newb, but I think I covered my bases.  I checked lsusb and it shows the remote along with making sure it matches the file created in the udev directory.

This is the same as the last guy wrote about so I guess I am wondering if they ever made support avail for Harmony One.  Thanks!

Try running Congruity with superuser priveleges:

Go to the website and choose to save the .EZHex file rather that open it in congruity. Then open a terminal and type

```
gksudo congruity /path/to/your/EZHex/file/here
```

Replace the last bit with your file obviously. See if that gets you anywhere. If that solves it I believe you can fix the problem permanently with some "policykit" changes or something. I'm having that problem right now and I haven't figured out how to mess with the policykit yet, but I'll update if I figure it out. It's a few pages back in this thread but it was never explained very well.

**Update:** I got it working by downloading the EZHex file and then opening congruity with superuser priveleges (I was pointing it to a file that didn't exist before...). I believe the policykit bit makes the gksu unnecessary, but I can't figure it out and (hopefully) I won't be reprogramming the remote very many times. So it should be tolerable.

---

### Post by jjdarling on 2009-12-09
So, I've been trying to follow this thread to the best of my ability, but I'm a bit tripped up by this last comment. You say:

> I had the same issuse in the final release of karmic. Apparently the packages have changed names. Using Synaptic Package Manager I searched for "wxpython" and then installed python-wxtools, python-wxversion, and
python-wxgtk2.8. I haven't got it working yet, but I don't think it has anything to do with packages not being installed.

Yet you were still able to get it working in your update? How did you do this?

I am having similar problems. I'm using the Harmony 880 and Ubuntu 9.10. Everything seemed to work except I got an error when installing the initial packages, it wouldn't install wxaddon.

When I try to sync my remote through the members.harmony website, it fails to load congruity. When I try to run congruity from command line it tells me 

```

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 28, in <module>
    import wxversion
ImportError: No module named wxversion

```

---

### Post by shadowfoxx on 2009-12-15
for everyone on Karmic having a problem with wxversion: the following worked for me

in terminal type: sudo apt-get install python-wxversion 

I then cleared out the cookies in my browser and rebooted.

this worked for me on ubuntu 9.10.. 

hope this helps.

---

### Post by jjdarling on 2009-12-16
> **shadowfoxx said:**
> for everyone on Karmic having a problem with wxversion: the following worked for me

in terminal type: sudo apt-get install python-wxversion 

I then cleared out the cookies in my browser and rebooted.

this worked for me on ubuntu 9.10.. 

hope this helps.
Worked beautifully. Thank you so much!

---

### Post by Cuba71 on 2010-01-07
Today I upgraded to Karmic 9.10.
My Harmony 610 was working correctly with Jaunty 9.04 and Congruity-13.

Now I followed the installation procedure, using **congruity-14 and concordance-0.21.**

```

lsusb |grep "Logitech"
Bus 002 Device 003: ID 046d:c111 Logitech, Inc. 
```

```

cat /etc/udev/rules.d/custom-concordance.rules
SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c111", MODE="666" 
```

And I get this error message

```

Error connecting or finding the remote
    (libconcord function init_concord error 11)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 524, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 135, in worker_body_connect
    libconcord.init_concord()
  File "/usr/local/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'init_concord' failed with error code 11 ('Error connecting or finding the remote') 
```

Any ideas anyone?

**Problem solved doing:**

```

make policykit
sudo make install_policykit

in the libconcordance directory and 
then reboot (I didn't try just a logout to see if that was enought)
in order to make concordance not require sudo to work.

As posted by **jtratcliff** on 5/9/09

```

---

### Post by cKGunslinger on 2010-01-10
See a few posts up.  Save the file and run congruity with 'sudo' privileges.

> **Cuba71 said:**
> Today I upgraded to Karmic 9.10.
My Harmony 610 was working correctly with Jaunty 9.04 and Congruity-13.

Now I followed the installation procedure, using **congruity-14 and concordance-0.21.**

And I get this error message

```

Error connecting or finding the remote
    (libconcord function init_concord error 11)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 524, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 135, in worker_body_connect
    libconcord.init_concord()
  File "/usr/local/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'init_concord' failed with error code 11 ('Error connecting or finding the remote') 
```

Any ideas anyone?

---

### Post by xjason8 on 2010-01-15
I was wondering if anyone has been successful in programming a Harmony 900 with Ubuntu 9.10.  

I have read through this thread and found some mention of the 900 but no definite confirmation on anyone that has done it... or specifically how to go about it.

Anyone?

---

### Post by deanerk on 2010-02-01
Well, I saw this thread when I was considering a new Harmony remote, but I didn't read all the posts thoroughly and went out and bought a Harmony One today.  Congruity is up to ver 14 and still no support for the One.  Makes me sad...  Don't have a Windows machine anywhere in the house any longer.  Guess I'll have to borrow a WinXP laptop from work tomorrow or something.  

I hate it when I get all pumped about something like this cool gadget but then get the finger from it.  Same thing happened with the tomtom.  Oh well...

---

### Post by xjason8 on 2010-02-02
Success!!!!
 
I installed virtualbox (install it from the website - not the OSE version in synaptic manager)
 
installed and ran windows xp through that
 
then i programmed the remote
 
easy as pie (yeah right, that process took me weeks to figure out)
 
hope that helps!

---

### Post by isTHEr3mOr3 on 2010-02-28
Great tutorial, works like a charm (Logitech 525). Thanks.

---

### Post by airheadjb on 2010-03-10
Great tutorial.  I found it last night and set it up on a Toshiba 
Satellite today.  Works like a charm - 2 880s for two completely different systems.  My only regret is that I didn't find it two years ago.

---

### Post by gewitty on 2010-03-18
I got all the software set up and working and managed to get my first two Activities loaded on my Harmony 555. However, I ran into a problem with the TV settings which I can't fix:

When the TV is turned on it then needs to be switched to the AV1 input. The first time I tried the Harmony, everything worked perfectly. The TV turned on, waited a few seconds for warm-up, then switched to AV1, then switched on the satellite box. The next time I tried, the TV turned on, but despite an apparent IR command being sent, the input failed to switch to AV1 (nothing happened at all).

I went back to the Logitech site and checked all the settings, then downloaded to the Harmony again. As previously, it worked perfectly the first time I tried, but failed on every attempt after that.

If I use the Help button, it fixes the problem temporarily, but the problem still re-occurs next time I switch on.

The only thing I've noticed is that when I run the update to the Harmony using Congruity, everything gets a green tick in the Congruity panel, but the Logitech site shows a red warning saying 'The remote did not respond to the remote software.'

I also tried to teach the Harmony to emulate the TV/AV key on my TV's original remote, but that doesn't work as the Congruity 'Learn' application only asks for the power button, the play button and the #1 button. So how do I get it to learn the TV/AV button?

By the way; I agree with the comments about complexity of the Harmony web site. It's appalling. I pity anyone with no technical knowledge who tries to use it.

---

### Post by gewitty on 2010-03-18
As an update on my last post:

I've been persevering without success. It looks now as if the Congruity apps are no longer updating the Harmony.

I tried removing all of my devices and activities on the Logitech web site, then ran an update. Congruity appeared to wipe the flash OK, then load in the update and verify it, but when I checked the remote afterwards, everything was still as it had been; all the devices and activities were unchanged.

This probably accounts for the web site message saying that the update had failed.

So now I'm even deeper in the doodoos. Not only am I unable to sort out the AV switching problem, but it seems that I've lost communication with the remote itself (although it seems to respond to Congruity and behaves as if an update has occurred).

I know I can get the unit into Safe Mode, but have no idea what I can do there, nothing seems to happen when I press various keys. Is there a factory reset option, so I can clear everything out and start again?

---

### Post by Thav on 2010-04-08
> **Solarisphere said:**
> 
Try running Congruity with superuser priveleges:

Go to the website and choose to save the .EZHex file rather that open it in congruity. Then open a terminal and type

```
gksudo congruity /path/to/your/EZHex/file/here
```

Replace the last bit with your file obviously. See if that gets you anywhere. If that solves it I believe you can fix the problem permanently with some "policykit" changes or something. I'm having that problem right now and I haven't figured out how to mess with the policykit yet, but I'll update if I figure it out. It's a few pages back in this thread but it was never explained very well.

**Update:** I got it working by downloading the EZHex file and then opening congruity with superuser priveleges (I was pointing it to a file that didn't exist before...). I believe the policykit bit makes the gksu unnecessary, but I can't figure it out and (hopefully) I won't be reprogramming the remote very many times. So it should be tolerable.

I have the same get_identity error. Harmony 650, Concordance .21, Congruity 14. Ubuntu Karmic. I have followed the original instructions, had to install wx run the make policiykit and make install_policykit. I have tried running concordance/congruity as sudo and through su, no luck. Any thoughts on how to proceed? Relevant outputs pasted below.

Congruity Error
```
Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 524, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 140, in worker_body_connect
    None
  File "/usr/local/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

```

```
concordance -i
Concordance 0.21
Copyright 2007 Kevin Timmerman and Phil Dibowitz
This software is distributed under the GPLv3.

ERROR: failed to requesting identity
Requesting Identity: Failed with error 1

```

```
lsusb | grep -i logitech
Bus 006 Device 002: ID 046d:c30a Logitech, Inc. iTouch Composite
Bus 006 Device 003: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 003 Device 002: ID 046d:c122 Logitech, Inc. 
```

```
cat /etc/udev/rules.d/custom-concordance.rules
SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c122", MODE="666"
```

---

### Post by Thav on 2010-04-09
So it looks like the Harmony 700 and 650 are in the same boat from what I see over on the concordance developers list. These devices identify themselves differently, and they're working on figuring out what that means.

Thanks again for all the helpful information in this thread.

---

### Post by Cuba71 on 2010-07-19
**_[SIZE="3"]Harmony Remote Installation on Ubuntu 10.04 LTS Lucid Lynx[/SIZE]_**

[B]Concordance 0.21-5
Congruity 13+dfsg-1

Tested on a Harmony 610 on 07/19/2010[/B]

```

sudo apt-get install build-essential libusb-dev python-wxversion python-wxgtk2.8 libwxgtk2.8-0 libwxbase2.8-0 python-ctypes python-wxtools concordance congruity


```

---

### Post by sularus on 2010-07-22
Hi guys and girls,

I only have one quick question.

Background---I purchased a Logitech Harmony 900 series remote (ya the cool touch screen one) at a yard sale. the battery was exploded inside and the seller told me it did not work and Logitech had replaced it for him.

Long story short I fixed it but Logitech has the remote disabled and I cannot program it from there site. Is there a open source site or another way I can program this thing. Thanks for your help.

---

### Post by Zadek on 2010-07-27
Hello,

today I received my Harmony 600.

I would like to connect this Remote Control to my netbook Samsung n130 (with Ubuntu 10.04 Lucid)

The Software/Repositories I installed like it's decribed in post #135 and I did nothing else.

So far I get these informations when i type this in the terminal:

```

lsusb |grep -i logitech
Bus 004 Device 003: ID 046d:c122 Logitech, Inc.

```and
```

cat /etc/udev/rules.d/custom-concordance.rules
SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c122", MODE="666"

```It seems correctly done...

When I try to open the site [http://members.harmonyremote.com](http://members.harmonyremote.com) there is an information that there's "Software Update Available". I click on "next"(two times everytime) and then reach to the USB Connection Page. Click on "next", too. The third page offers me to open a file named "Connectivity.EZhex" by Congruity. If I do so, it opens the Congruity (Version 13) Page.

Unfortunality the Remote Control couldn't be found. The Error Message:
```

Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/bin/congruity", line 524, in _WorkerFunction
    False
  File "/usr/bin/congruity", line 140, in worker_body_connect
    None
  File "/usr/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

```Could somebody please help me?

Thanks

**EDIT:**

Maybe this could help?!

> 
```


make policykit
sudo make install_policykit

in the libconcordance directory


```


But where can I find the "libconcordance directory"? Maybe /usr/lib/python2.6/dist-packages? Donno..


Zadek

---

### Post by Zadek on 2010-07-28
The problem is still there.

I'm afraid threre is no solution to this problem.

_[Here]("http://www.phildev.net/concordance/supported_models.shtml")_ it is described that all 6xx Harmonys are supported by concordance. But this page was apparently last updated in 2009, and the "new" 600 model was released in march 2010. 
When I type

```

concordance -i

```or 

```

sudo concordance -i

```I get this error message:

```

Concordance 0.21
Copyright 2007 Kevin Timmerman and Phil Dibowitz
This software is distributed under the GPLv3.

ERROR: failed to requesting identity
Requesting Identity: Failed with error 1

```Any idea?

Regards

Zadek

---

### Post by rg1980 on 2010-09-17
Hi Everyone

I'm a real newbie here and was hoping someone can help me out please.  I have a harmony 880 remote that has been disabled from logitech and was wanting to know what program can I use to still program and update it.  Will this Concordance program help me? 

Thanks in advance for everyone's help

FYI.  I bought this remote from ebay and was never told it was disabled and logitech indicated they cannot reactivate for me and that I'm out of luck.  No money back from the seller either or ebay.  Please help me if you can.

---

### Post by miles916 on 2010-10-22
> **Zadek said:**
> 

```

Concordance 0.21
Copyright 2007 Kevin Timmerman and Phil Dibowitz
This software is distributed under the GPLv3.

ERROR: failed to requesting identity
Requesting Identity: Failed with error 1

```

hi everyone!

i tried to set up my harmony 300 using the steps described in this thread, but i get the same error as zadek... 

guess i shouldve checked the supported models first, haha. 

hope someone will manage to make this remote compatible with linux some time soon. 

regards,
m.

---

### Post by bobbes on 2010-12-15
Hi,
i had the same problem.
I bought a Harmony 650, and concordance (0.21) doesnt detect it.
Easy solution: install concordance 0.23 :)

PPA available at [http://blog.cyphermox.net/2008/07/update-congruity-concordance-packages.html](http://blog.cyphermox.net/2008/07/update-congruity-concordance-packages.html)

If congruity complains about a missing libconcord.so.1.1.0:

open libconcord.py
Change Line 35 from ABI_VERSION = "1.1.0" to ABI_VERSION = "2"

and it should work...so it does on my system.

Regards.

PS: you may have to add a new udev rule
(from congruity readme)
> You may need to set up udev/similar rules so that the USB device nodes used
by the application are accessible without running congruity as root. Note that
distribution packages of libconcord typically provide these rules, so they may
already be set up for you.

If you need to manually set up udev rules, the following file should work:

----- /etc/udev/rules.d/custom-concordance.rules:
SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c110", MODE="666"
-----

Note that your vendor and product ID may be different. Use lsusb to verify:

-----
[swarren@esk ~]$ lsusb
...
Bus 005 Device 011: ID 046d:c110 Logitech, Inc.

---

### Post by sukkel67 on 2010-12-18
Hello everyone,

Same problem for me, using a Harmony 600.

---

### Post by DistantDave on 2010-12-28
Does this do the job for anyone ?

[https://launchpad.net/~yavdr/+archive/unstable-vdr/+build/2048014](https://launchpad.net/~yavdr/+archive/unstable-vdr/+build/2048014)

---

### Post by mcglnx on 2010-12-30
> **miles916 said:**
> hi everyone!

i tried to set up my harmony 300 using the steps described in this thread, but i get the same error as zadek... 

guess i shouldve checked the supported models first, haha. 

hope someone will manage to make this remote compatible with linux some time soon. 

regards,
m.

I have the same issue here. Pity. Logitech seems to have issues with Linux development since ages. Recently they fired Engineers, so I'm afraid there is no hope from them.

---

### Post by svenw1973 on 2011-01-06
> **DistantDave said:**
> Does this do the job for anyone ?

[https://launchpad.net/~yavdr/+archive/unstable-vdr/+build/2048014]("https://launchpad.net/%7Eyavdr/+archive/unstable-vdr/+build/2048014")

Hi,
this solved the problem 
> concordance -i -v
Concordance 0.21
Copyright 2007 Kevin Timmerman and Phil Dibowitz
This software is distributed under the GPLv3.

ERROR: failed to requesting identity
Requesting Identity: Failed with error 1


Now i get 
>  concordance -i -v
Concordance 0.23
Copyright 2007 Kevin Timmerman and Phil Dibowitz
This software is distributed under the GPLv3.

Requesting Identity: 100%                 done
  Model: Logitech Harmony 700 (Molson)
  Skin: 71
  Firmware Version: 0.2
  Firmware Type: 0
  Hardware Version: 1.1
  External Flash: 4 MiB - 15:1C EON F16-100HIP
  Architecture: 14
  Protocol: 14
  Manufacturer: Harmony Remote 0-0.2.0
  Product: Harmony Remote 0-0.2.0
  IRL, ORL, FRL: 64, 64, 0
  USB VID: 046D
  USB PID: C122
  USB Ver: 1071
  Serial Number: {EEEEEEEE-EEEE-EEEE-EEEE-EEEEEEEEEEEE}
    {46397565-05E8-484F-96AE-9388FFF7EF8E}
    {A2AFC4FB-18DB-B947-A5DE-8626649285DA}
  Config Flash Used: 19% (760 of 3904 KiB)

Success!


I am wondering why my Harmony is detected as 700. The windows software from Logitec detects this one as 605.
Regards,
Sven

---

### Post by Dave_NY on 2011-01-15
Running Ubuntu 10.10 I managed to get my Logitech Harmony 700 working, This is how I did it:

type this command first:

```
sudo apt-get install build-essential libusb-dev python-wxversion python-wxgtk2.8 libwxgtk2.8-0 libwxbase2.8-0 python-ctypes python-wxtools
```

The 700 series remote is only supported in Concordance .22 and higher but the latest version in the Ubuntu Software Center is .21 so you have to compile Concordance and Congruity from source.

Download Concordance .23 here: [http://sourceforge.net/projects/concordance/files/concordance/0.23/concordance-0.23.tar.bz2/download]("http://sourceforge.net/projects/concordance/files/concordance/0.23/concordance-0.23.tar.bz2/download")

Download Congruity 15 here: [http://sourceforge.net/projects/congruity/files/congruity/15/congruity-15.tar.bz2/download]("http://sourceforge.net/projects/congruity/files/congruity/15/congruity-15.tar.bz2/download")

Extract the Congruity and Concordance bz2 files into a temp directory (Doesn't matter where)

In terminal cd into the temp directory where the bz2 files were extracted and cd into the /Concordance-0.23/libconcord directory

Enter this:
```
./configure --prefix=/usr/
make PREFIX=/usr/
sudo make install
sudo make install_policykit
```

After that is complete cd into the Concordance-0.23/libconcord/bindings/python directory

Enter this:
```
python setup.py install
```

After that is complete cd back into the temp directory where you extracted the Concordance bz2 file

cd into the /concordance-0.23/concordance directory

Enter this:
```
./configure
make install PREFIX=/usr/
```

After that you should be all set. Plug in the remote and log into the Harmony Remote website [http://members.harmonyremote.com/]("http://members.harmonyremote.com/") and make whatever changes to the remote setup you want. Save the Connectivity.EZhex file and change your file browser settings to always open .EZhex files with '/usr/bin/congruity'

The Congruity GUI should appear on the screen and will detect the remote. Follow the on-screen instructions and the remote will update from the Harmony website.

Thanks for putting this HOWTO together, I can finally stop using my backup laptop with Windows to configure my remote :)

---

### Post by mcglnx on 2011-01-17
Thanks for the method. Looks promissing, but for me it does not work with Harmony 300.

---

### Post by owiknowi on 2011-01-26
same with the 785: congruity is complaining about:
"File "/usr/bin/congruity", line 1932, in main
    raise CmdLineException("ERROR: Precisely one filename argument is required")"

contacted logitech several times and (more or less):
a: 'use windos and you can program it just fine'
q: 'but i don't have windos. do you perhaps provide it with the remote?'
a: you can guess the answer on that.

logitech has no actual plans on supporting linux for their remotes.
that's what they told me.

anyone perhaps know a programmable universal remote that works under linux?

btw. with 'wine' the logitech software neither worked (test installed windos).

wished i had some of those marketing skills...

---

### Post by Dave_NY on 2011-01-26
Sounds like you need to specify the path and filename for the file you downloaded off the Harmony website. Try typing congruity <path-to-filename.EZHex> in terminal (minus the <> symbols)

---

### Post by highflyr on 2011-03-01
Running Ubuntu 10.10 with Logitech Harmony 720. 

All went well until the end- > cd into the /concordance directory

Enter this:
Code:
make install PREFIX=/usr/

This returns > make: *** No rule to make target 'install'. Stop.

Any ideas? Thanks for the post Dave!

---

### Post by Dave_NY on 2011-03-01
> **highflyr said:**
> Running Ubuntu 10.10 with Logitech Harmony 720. 

All went well until the end- 

This returns 

Any ideas? Thanks for the post Dave!

Made a mistake in my how-to post. You need to cd into the /concordance-0.23/concordance directory then type:

```
./configure
make install PREFIX=/usr/
```

Try that and tell me if it works. I have modified my original post to reflect these changes

---

### Post by highflyr on 2011-03-03
Got it! Thanks for the reply and easy to follow tutorial. Had to ```
./configure
sudo make install PREFIX=/usr/
```
But not sure if that's because of a logout while searching around for compiling instructions... Thanks again Dave =D>

---

### Post by Dave_NY on 2011-03-03
> **highflyr said:**
> Got it! Thanks for the reply and easy to follow tutorial. Had to ```
./configure
sudo make install PREFIX=/usr/
```
But not sure if that's because of a logout while searching around for compiling instructions... Thanks again Dave =D>

Great glad it worked

---

### Post by Thav on 2011-03-13
> **Thav said:**
> I have the same get_identity error. Harmony 650, Concordance .21, Congruity 14. Ubuntu Karmic. I have followed the original instructions, had to install wx run the make policiykit and make install_policykit. I have tried running concordance/congruity as sudo and through su, no luck. Any thoughts on how to proceed? Relevant outputs pasted below.

Congruity Error
```
Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 524, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 140, in worker_body_connect
    None
  File "/usr/local/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

```

```
concordance -i
Concordance 0.21
Copyright 2007 Kevin Timmerman and Phil Dibowitz
This software is distributed under the GPLv3.

ERROR: failed to requesting identity
Requesting Identity: Failed with error 1

```

```
lsusb | grep -i logitech
Bus 006 Device 002: ID 046d:c30a Logitech, Inc. iTouch Composite
Bus 006 Device 003: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 003 Device 002: ID 046d:c122 Logitech, Inc. 
```

```
cat /etc/udev/rules.d/custom-concordance.rules
SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c122", MODE="666"
```

> **DistantDave said:**
> Does this do the job for anyone ?

[https://launchpad.net/~yavdr/+archive/unstable-vdr/+build/2048014](https://launchpad.net/~yavdr/+archive/unstable-vdr/+build/2048014)


Yes, installing the 0.23 package's from DistantDave's builds worked for me!

---

### Post by sabersong on 2011-03-15
I followed Dave_NY's instructions, and all seemed to go well, but when I tried to use congruity I got the following error:

```

File "/usr/local/bin/congruity", line 1945, in main     raise CmdLineException("ERROR: Precisely one filename argument is required")

```

I tried to install the debian package from the yaDVR site, but I can't use it, it's i386 and I'm on an AMD64 machine. Is there maybe a way to make it work?

---

### Post by Dave_NY on 2011-03-15
> **sabersong said:**
> I followed Dave_NY's instructions, and all seemed to go well, but when I tried to use congruity I got the following error:

> 
File "/usr/local/bin/congruity", line 1945, in main     raise CmdLineException("ERROR: Precisely one filename argument is required")


I tried to install the debian package from the yaDVR site, but I can't use it, it's i386 and I'm on an AMD64 machine. Is there maybe a way to make it work?

Don't forget this part:

> 
After that you should be all set. Plug in the remote and log into the Harmony Remote website [http://members.harmonyremote.com/](http://members.harmonyremote.com/) and make whatever changes to the remote setup you want. Save the Connectivity.EZhex file and change your file browser settings to always open .EZhex files with '/usr/bin/congruity'

When you start congruity you need to specify the filename of the .EZhex file if you are using the command line. If you want congruity to auto-start the GUI then you must have your browser auto-open .EZhex files with /usr/bin/congruity

---

### Post by sabersong on 2011-03-15
I missed the browser setting. Works fine now! Thanks!

---

### Post by Iateabee on 2011-04-08
_Hardy_ Universe:

Put this in for your source:

 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe'

---

### Post by kaza7 on 2011-08-17
Hi,

when i  try to install python-wxaddons, i have an error : package not found.
please how to install the first command in this how-to?
each repository to add for that?
i have ubuntu 11.04.

thanks.

---

### Post by honeybear on 2011-08-21
I have the i300 harmony 

```
# lsusb |grep -i logitech
Bus 003 Device 003: ID 046d:c124 Logitech, Inc.
```

```
echo 'SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c124", MODE="666"' |sudo tee /etc/udev/rules.d/custom-concordance.rules
```

```
 apt-get install build-essential libusb-dev python-wxversion python-wxgtk2.8 libwxgtk2.8-0 libwxbase2.8-0 python-ctypes python-wxtools

apt-get install concordance congruity

```

until now fine, then congruity /usr/bin/congruity runs the HEX file.



I got until an error occured 

```
Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/bin/congruity", line 524, in _WorkerFunction
    False
  File "/usr/bin/congruity", line 140, in worker_body_connect
    None
  File "/usr/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

```

> 
# concordance -v -i
Concordance 0.22
Copyright 2007 Kevin Timmerman and Phil Dibowitz
This software is distributed under the GPLv3.

ERROR: failed to requesting identity
Requesting Identity: Failed with error 1




End ... Please help.

Happy Tux

(I tried Vista, buuuu, man, Linux rocks !!)

---

### Post by kafkaian on 2011-08-23
Harmony 300.

Seemed to work well using congruity until:

> Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/bin/congruity", line 535, in _WorkerFunction
    False
  File "/usr/bin/congruity", line 150, in worker_body_connect
    None
  File "/usr/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')


lsusb gives > Bus 002 Device 004: ID 046d:c124 Logitech, Inc.

---

### Post by honeybear on 2011-08-28
> **kafkaian said:**
> Harmony 300.

Seemed to work well using congruity until:



lsusb gives

better to give this i300 remote control back to the shop, and check before buying anything what is compatible with Linux. 

I go to buy an MCE. It works simply

---

### Post by kafkaian on 2011-08-28
> **honeybear said:**
> better to give this i300 remote control back to the shop, and check before buying anything what is compatible with Linux. 

I go to buy an MCE. It works simply Yes I'm beginning to agree, but I did buy knowing that I could always fall back on a friend's W7 box.

---

### Post by kafkaian on 2011-08-30
Used a W7 machine in the end.

---

### Post by honeybear on 2011-08-31
> **kafkaian said:**
> Used a W7 machine in the end.

I also tried with Vista and XP, and I also never managed to make it work. It does even not work under microsoft OS. It hangs during install. What a piece of ... this remote control i300? Burn it ;)

---

### Post by hazaduz on 2011-10-02
Hi there, 
my harmony one remote is not being detected at all following the steps. 

congruity and concord installed correctly. 

@ubuntu:~/congruity-10$ lsusb
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 002: ID 046d:08c5 Logitech, Inc. QuickCam Pro 5000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by smile-on on 2011-10-17
Concordance Error: "failed to requesting identity. Failed with error 1"
Means that concordance does not recognize id of your remote.
Example, concordance v0.21 does not know 2010 Harmony remotes like 600, 700 etc.

1) You need to install patched version 0.23 or newer:
[https://launchpad.net/~yavdr/+archive/unstable-vdr/+build/2048014]("https://launchpad.net/%7Eyavdr/+archive/unstable-vdr/+build/2048014")

2) enable access to usb dev by custom policy 
$ lsusb|grep -i logitech
Bus 006 Device 002: ID 046d:c122 Logitech, Inc.

Note ID 046d and c122
Do next step as root
# cat > /etc/udev/rules.d/40-concordance.rules
SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c122", MODE="666"

3) unplug and plug remote and type 
$ concordance -i -v

:D

---

### Post by muemarco on 2011-10-19
> **marcw said:**
> ****Updated and tested with Intrepid Ibex 8.10****
The Logitech Harmony universal remote control is the finest I have ever bought, and I've had a few of them.  I currently own model 880 but I think this howto should apply to any of the more recent Harmony Advanced models.

As nice as the Harmony is, it requires Windows to run the application that accesses Logitech's extensive online component database.  What I used to do was have a Windows virtual machine (via Virtualbox) available on my Ubuntu workstation just so I could have access to the Harmony software.  A whole Windows environment for one lousy application!  Well, it's not really lousy.  What it does is one of the things that makes a Harmony remote so special in the first place.  I just don't like the idea of running Windows for anything.  A little research showed that the Harmony software does not run at all under Wine, so that was out.  And then I read about Concordance and Congruity.  These two utilities, along with Logitech's web interface, allow me to do everything natively on Linux that used to require Windows.  Not quite as elegantly perhaps but very servicably.  This is how I did it.

First off, you'll need some extra software from the Hardy repositories.  Follow the instructions at [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) to enable the Universe repository (my personal preference is to also enable the Multiverse and Restricted repositories).  Afterward, this should get you everything you're going to need.  From a terminal (just copy/paste):```
sudo apt-get install build-essential libusb-dev python-wxversion python-wxgtk2.8 libwxgtk2.8-0 libwxbase2.8-0 python-ctypes python-wxtools python-wxaddons
```If you are told that other software needs to be installed as well, just say Yes.  Then get the latest Concordance and Congruity.  As of this writing, and what I used, was Concordance 0.20 and Congruity 7.  Back to the terminal (execute one line at a time):```
cd
mkdir source
cd source
wget http://downloads.sourceforge.net/concordance/concordance-0.21.tar.bz2
wget http://downloads.sourceforge.net/congruity/congruity-10.tar.bz2
```Or you can manually get the files from [[COLOR=Cyan]here[/COLOR]]("http://sourceforge.net/projects/concordance/") and [[COLOR=Cyan]here[/COLOR]]("http://sourceforge.net/projects/congruity/") .  Anyway, once you have your files we'll uncompress them and process them, again in the same terminal (some of these commands might take a couple minutes each to complete):

```
tar -xvjf congruity-10.tar.bz2
tar -xvjf concordance-0.21.tar.bz2
cd concordance-0.21/libconcord
./configure
make
sudo make install
cd ../concordance
./configure
make
sudo make install
cd ../libconcord/bindings/python
sudo python setup.py install
cd ../../../../congruity-10
sudo make install
sudo ldconfig
```Next you'll be creating a permissions file.  Again from your terminal (after connecting your remote to your computer):

```
lsusb |grep -i logitech
```You should see something similar to this:


The 2 numbers you want to pay attention to are the ones (in red) that make up the ID.  In this example, they are 046d and c110.  Your 2 numbers may be different.  Alter and then run the following command replacing the 046d and c110 with your 2 numbers, but leave the quotation marks in place:

```
echo 'SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c110", MODE="666"' |sudo tee /etc/udev/rules.d/custom-concordance.rules

```Now do one more thing to your browser.  Change your preferences to ask what you should do with downloads.  In Firefox you would select the button in Preferences -> Main -> Downloads -> Always ask...

There, it's all built and installed.  You'll now do all of your Harmony configuring through the Logitech web site and the new software you've just installed.  From your browser go to [http://members.harmonyremote.com](http://members.harmonyremote.com).  You might be told your software needs updating.  Skip past that screen.  It doesn't know that you aren't using their Windows software.  Next you'll need to login to their site which will require registering if you already haven't.  Once registered and logged in you're taken to the main Harmony configuration pages.  This howto isn't for teaching you how to use this page.  Use the "Support" link or the Logitech forums for that.  After you've configured some Devices and Activities on this page you can then click the "Update my Remote" link.  The next page that appears will tell you to make sure that your Harmony is connected to your computer via your USB cable.  Ignore the rest of the screen and click next.  This will bring up a download dialog.  Select "Open With" and choose "other".  In the selection screen that follows type in /usr/local/bin/congruity and press "Open".

With any luck at all this will open your new Congruity screen which will be your interface for all of the  communications between your Harmony and the Logitech web site.  There will be at least two times you will be asked to download a file (each time will open Congruity): the first time will be to merely confirm communication with the remote.  Subsequent downloads will be to perform the actual data transfers that update your remote.  Both the Logitech screens and the Congruity screens take time to refresh.  Sometimes up to a minute or more.  Be Patient!

Everything worked perfect by doing the step by step installation as described above.
However, after loging in to myharmony site an connecting the remote to my computer to update it the congruity application showed the following message:
Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 521, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 137, in worker_body_connect
    None
  File "/usr/local/lib/python2.7/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

Any Idea how to resolve this issue?

---

### Post by smile-on on 2011-10-19
To continue my post  on concordance. Now concordance is able to identify your remote. Next is how to setup your harmony remote under Ubuntu. Initial I felt into assumption that **Congruity** is a GUI that may be used instead of crazy Logitech wizard program that runs only on windows. It is NOT. Instead congruity is a write helper that was used in old Logitech web wizard. If you need to program your remote here are steps:

1) Make sure concordance is able to identify your remote. See my post above.
2) Register at [http://members.harmonyremote.com/](http://members.harmonyremote.com/) and login there.
3) Web wizard will kill you by stupid questions that almost make no sense but those how mange to survive through at the end will get** Update.EZHex file** downoaded with all settings you programmed.
4) In "Open or save" dialog in your browser select **Open with Congruity**.
Than congruity will write the program from Update.EZHex file into your remote. Obviously the remote must be plugged in USB cable.

The only challenge I have - can not have direct access to program commands in "activity" mannualy. "The help" of wizard is meant to be used by complete dam person and really hard to use to any normal human. Shame on that person who was a  project leader for that "wizard"!
Does anyone know how I can manually specify commands and delays in initial IR sequence for activity? :confused:

Just in case, I used **Ubuntu 10.04 **LTS - the Lucid Lynx - released in April 2010.
And Harmony 600 remote also released in 2010.
**Congruity v13, concordance v0.23 .**

---

### Post by smile-on on 2011-10-19
I found **very good page** that allows you to understand **"[concept]("http://bevhoward.com/Misc/IR/HarmonyAdvFaq.html")" **behind harmony  and Logitech way of doing business.  [http://bevhoward.com/Misc/IR/HarmonyAdvFaq.html](http://bevhoward.com/Misc/IR/HarmonyAdvFaq.html)

Well at least I am back to normal, it is not me crazy it is ugly "corporate culture" :(

---

### Post by ksarauer on 2011-10-30
Hi, I'm hoping someone can help me. I've been able to install the packages per the instructions in the first post.
I have a harmony one remote
Concordance version 23
Congruity version 15

The error occurs after the first download when it's trying to detect the remote.

Thanks


Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 535, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 150, in worker_body_connect
    None
  File "/usr/local/lib/python2.7/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

---

### Post by mfincken on 2012-02-19
> **ksarauer said:**
> Hi, I'm hoping someone can help me. I've been able to install the packages per the instructions in the first post.
I have a harmony one remote
Concordance version 23
Congruity version 15

The error occurs after the first download when it's trying to detect the remote.

Thanks


Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 535, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 150, in worker_body_connect
    None
  File "/usr/local/lib/python2.7/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

I'm having the exact same problem, all the packages were installed fine, no errors. I created the custom rule for congruity. The congruity window comes up detecting remote and it fails with the error code above.

Harmony Remote 520
Concordance version 23
Congruity version 15
Ubuntu 11.10

Does anyone have any ideas how I could fix this?

Thanks!


EDIT:
After reading and trying a few things, I found out that "concordance -i" only completed successfully with "sudo concordance -i" So I opened my browser with sudo and it works!

Does anybody know what permission I need to change for concordance to work without sudo?

---

### Post by mfincken on 2012-02-19
Boooo, when I try to update now, I get:

Error while erasing flash
    (libconcord function erase_config error 6)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 702, in _WorkerFunction
    self._WorkerFunctionBody()
  File "/usr/local/bin/congruity", line 838, in _WorkerFunctionBody
    py_object((self._DgUpdate, self.dg_erase))
  File "/usr/local/lib/python2.7/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'erase_config' failed with error code 6 ('Error while erasing flash')

:(

Ideas?

---

### Post by thedemon13666 on 2012-04-01
I am currently trying to set up my logitech harmony 300i with ubuntu  11.10 x64 however when running congruity it fails to detect the remote  (I have been on the harmony website and downloaded the file which opens  congruity)

Is it possible to set this remote up on ubuntu?

---

### Post by mastermindg on 2012-05-21
I'm running 11.10 x64 with Congruity and my Harmony 300i. It is working fine for me.

---

### Post by SuperFreak on 2012-07-09
@mastermindg
I realize your post is dated awhile ago, but how did you program your Harmony 300i with congruity? I can't even see how to download the appropriate files as Logitech will not allow Linux OS to work with the 300i

edit: I downloaded the installer from [http://members.harmonyremote.com](http://members.harmonyremote.com) but it refuses to recognize my remote

Get this output from Congruity:
```
Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/bin/congruity", line 535, in _WorkerFunction
    False
  File "/usr/bin/congruity", line 150, in worker_body_connect
    None
  File "/usr/lib/python2.7/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')

```

---

### Post by SuperFreak on 2012-07-13
It seems it doesn't work with the Harmony 300i; at least I wasn't  able to make congruity work.
I tried a Harmony 650 and was able to configure online as directed on this post but when I try to download the programmed setup to my remote it brings up Congruity again and Congruity fails to update remote. Get this output like with 300i:

```
Error connecting or finding the remote
    (libconcord function init_concord error 11)

Traceback (most recent call last):
  File "/usr/bin/congruity", line 535, in _WorkerFunction
    False
  File "/usr/bin/congruity", line 145, in worker_body_connect
    libconcord.init_concord()
  File "/usr/lib/python2.7/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'init_concord' failed with error code 11 ('Error connecting or finding the remote')

```

Found the problem. Had to download Update.EZHex file then open it with Congruity. Seems to work now

---

### Post by Bramkaandorp on 2012-08-27
@SuperFreak: I use the Harmony 300 (not i), and upon running the "Connectivity.EZHex" file in Congruity, I get a very similar error message to yours.

Where can I find the "Update.EZHex" file? Or is it the same as the "Connectivity.EZHex" file?

---

### Post by SuperFreak on 2012-08-27
Off hand I am not sure where the file is but if you sign in at [http://members.harmonyremote.com/EasyZapper/UserHome.asp](http://members.harmonyremote.com/EasyZapper/UserHome.asp)
I believe it is in there somewhere

---

### Post by Bramkaandorp on 2012-08-28
> **SuperFreak said:**
> Off hand I am not sure where the file is but if you sign in at [http://members.harmonyremote.com/EasyZapper/UserHome.asp](http://members.harmonyremote.com/EasyZapper/UserHome.asp)
I believe it is in there somewhere

No dice. I get the Connectivity.EZHex file again.

Running it in sudo didn't help the connectivity, neither did gksudo.

By the way, do I need to get a message when I plug my remote into the USB port (like the one you get when you plug in a hard disk or flash drive)? Because I don't get that.

---

### Post by SuperFreak on 2012-08-28
I get a pop up saying connect with Congruity followed by a congruity interface. But I never got the Harmony 300i to work with Linux only Windows. I ended up buying a Harmony 650 which does work with Linux and has a backlight and enables more devices.

---

### Post by Bramkaandorp on 2012-08-28
Too bad, I really hoped it was just a minor issue.

I guess I'll just stick to the conventional remotes for now.

Thanks anyhow, at least now I have closure.

*stumbles away into the darkness*

---

