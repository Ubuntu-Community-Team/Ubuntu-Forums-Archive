---
title: "VirtualBox OSE Critical Error"
date: 2010-08-03
forum: Virtualisation
---

### Post by xEsCx 1nSaN1Ty on 2010-08-03
Hi! This is my first post on the forums, and I am having a problem. I decided to try out Ubuntu 10.4 yesterday and I like it a lot, although I am a complete noob. I installed VirtualBox OSE from Synaptic Package Manager earlier and started to set it up, but had to exit it because I had to go do something else. After arriving back I tried to open it again and now it is giving me this error:

[http://img295.imageshack.us/f/screenshotci.png/](http://img295.imageshack.us/f/screenshotci.png/)

I searched up on google, and it said to look for VirtualBox.xml, but I can't seem to find that file...Maybe thats the problem? Sorry for being a complete noob.

---

### Post by Maverick_Meerkat on 2010-08-03
Greetings,

There's probably several other solutions but...

I would suggest using Package Manager to completely remove the present installation. Then go to: 

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

You will see a listing for:

Ubuntu 10.04 ("Lucid Lynx") i386 | AMD64

Click the appropriate link (i386 for Intel or AMD64 for AMD) to download and install the software directly from there.

---

### Post by xEsCx 1nSaN1Ty on 2010-08-03
Hi, I tried your suggestion earlier, but the same error resulted.

---

### Post by Maverick_Meerkat on 2010-08-03
Hmmm... Did you double check that 

/home/dylan/.VirtualBox/VirtualBox.xml 

was removed? Have you tried manually deleting the .VirtualBox directory? That is where the config file is stored.

BTW it will be a hidden folder.

---

### Post by fladnaG1 on 2012-02-21
Hi all ! I do not know what to do      o_O 
-----------------------------
VirtualBox-Critical Error

NS_ERROR_FAILURE (0x80004005)

Failed to create the VirtualBox COM object

Location'/home/mycomput/.VirtualBox/VirtualBox.xml',line 46 (8),column 26.

/home/vbox/vbox-4.1.8/src/VBox/Main/src-server/VirtualBoxlmpl.cpp[485](nsresult VirtualBox::init()).
------------------------------

Am using my main host system Ubuntu 11.4 , were just some time ago I did run 
VirtualBox 4.1.8 
In that (among other's) I was working today on my "XP pro SP2 ,32bit"
Did dedicate 8Gb fixed size vdi for my xp , did run 
some driver download for my logitech and ,this whole thing got frozen ,with this error message .I forced it to quit. And then I could not even in the graphical interface restart my host 11.4 needed to "shutdown -h now"

Then it did , but upon booting up it got stuck.So I pressed the powerbutten till it went down again. After the seconnd try to boot my main sys ,it did boot up , like before , but shoutet at me with this error message and I can not even open up my virtual box. I have snapshot of the message , but on top I did also write what it silently showed to me :/

I do not know. Either I did download the logitech driver for 64bit on my 32bit (but I checked and there was not much info anyway in wankdows xp)
Maybe that crashed? But most likely I think I have run out of space there
and it just froze         
                              x_X 


And I see now , adding ,especially on Wankdows xp in virtualBox additional
hardware drivers is not the best thing to do, but on the other hand ,how do you want to test out something.

And yes I see it is lethal to VBox if powering it down by force....
I should have take 5 and come back to it ,approach this with issue ,by trying opening up new VBox to see if it boots up parallel one, but this whole thing was way to frozen as I remember.

Now it is what it has become 

I did have 3 snapshots done from my xp. I also did have many other systems set up there. Do I have to lose everything again @_@  ?

Is there any way to fix this, please ????

------------------------------------------
link to the snapshot pic:
[http://dl.dropbox.com/u/63368090/ViB-Error-Ubuntu11.4-Xp%20pro%20caused%20this32bit.png](http://dl.dropbox.com/u/63368090/ViB-Error-Ubuntu11.4-Xp%20pro%20caused%20this32bit.png)
------------------------------------------

1)  Is there any way to run Corrupt VBox in safe mode ?
I did run my main Hostsys ubu11.4 in recovery mode, but this did not help , Vbox not responding.

2)  Should I delete the Vbox (but not the files) and install it ? If yes 
would it be correct to just go to Package manager remove it and back install it (not selecting the total removal of siles)

3)  Ubuntu software Center is showing me the option of reinstalling it - But this would delete all my basic configurations or not ?

4)  Or should I just delete (not the files) the GUESTADDITIONS of the VBox ?

Any useful help , written in understanding details is greatly appreciated

Thank you
Best regards


------------------------------------------------------

---

