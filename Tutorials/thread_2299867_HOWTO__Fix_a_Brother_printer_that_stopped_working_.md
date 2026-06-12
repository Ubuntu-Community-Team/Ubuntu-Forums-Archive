---
title: "HOWTO:  Fix a Brother printer that stopped working after an Ubuntu upgrade"
date: 2015-10-21
forum: Tutorials
---

### Post by ubu5 on 2015-10-21
I have a Brother laser printer, a network printer, attached to my local network with an Ethernet cable.  (This printer also has wireless, but I have never used that feature.)  It is several years old, and every computer here -- linux and otherwise -- can talk to it, no problems.  Over the years, various successive versions of Ubuntu, on both i386 and AMD64 platforms, have been used to send jobs to this printer, with great success.

I just upgraded this computer from Ubuntu 12.04 to 14.04.  The printer immediately stopped working from this computer.  Other computers can still print to it without problems.

I tried lots of things suggested by the Internet.  I found this excellent thread: [http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793) and tried many things suggested there.  Nothing worked for me.

I sometimes could get the printer to respond, but when sent a test page it would emit a piece of paper that said something non-helpful like "Unable to open the initial device" or "#PDF-Banner" or "you are using the wrong driver".

After trying many things for many hours, I finally found a procedure that worked for me.  It is only slightly different than the procedure given on the Brother website.  It is simpler than many of the other things that have been suggested.  This worked on an Ubuntu 14.04 AMD64 machine, but I don't know if it will work on anything else.

It is assumed that you have already eliminated all of the dumb things that could be wrong.  Make sure the printer has paper.  Turn it off and then turn it back on.  Print to it from another computer, if you can, to make sure it still works.


(1) Go to the Brother website, find your printer, find the Downloads page for that printer, read any relevant notes you may find along the way.  At some point you should select Linux (deb) from a list.  Hopefully you will find a file called something like "Driver Install Tool", and hopefully it won't be ancient;  download it.  If it shows you some instructions for its use, read them, but don't do them yet;  the ones I found were incomplete.  (If you don't find a file like this, then you can probably skip the rest of this;  instead try the thread mentioned earlier.)

(2) Go to System Settings, Printers, look for the balky printer.  Delete it.  If there are multiple icons that point to that same printer, delete them all.

(3) Create a folder on your Desktop, called Brother.  It must be named that;  the installer I was given is apparently hardcoded to look for things in ~/Desktop/Brother and fails if it can't find that folder.  This step is missing from the instructions I found on Brother's website.

(4) Copy that installer file into the Brother folder.

(5) Open a terminal, and cd into that folder  ( cd Desktop/Brother ).  Then issue the following commands:

   ```

   sudo apt-get install lib32stdc++6                #   Brother doesn't mention this step, but it seems necessary on my machine, and probably won't hurt anyway

   # the commands below are from Brother's instructions

   gunzip linux-brprinter-installer-*.*.*-*.gz          #   if the file you downloaded has a different name, substitute that, here and below

   sudo bash linux-brprinter-installer-*.*.*-*  <printer-model>           #  substitute your printer model name for <printer-model>  -  no spaces please!
```

If you have gotten this far without errors, you are doing well.  Don't be alarmed it if says it's going to install an i386 file and you have an AMD64 machine instead.

At some point, it may ask:

   Will you specify the Device URI? [Y/n] ->

Say Y if you will connecting through the network, N if you will be connecting the printer to your local machine via USB.

At some point, it gave me a list of destination Device URIs, and asked me to select one.  I chose the last one, the one that said "Auto".

It worked.

---

### Post by kurt18947 on 2015-10-22
Good writeup. You don't have to use Desktop for a destination but it's an excellent idea to give the installer and its downloads a separate folder regardless of destination. It will make your desktop or whatever destination a cluttered mess if you don't. Care to guess how I know that? :oops:

---

