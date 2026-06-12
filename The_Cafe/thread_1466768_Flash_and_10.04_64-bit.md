---
title: "Flash and 10.04 64-bit"
date: 2010-04-30
forum: The Cafe
---

### Post by samalex on 2010-04-30
Hi,

For those running 64-bit Lucid, did it come preinstalled with NSPlugin wrapper and 32-bit Flash or the Alpha version of 64-bit Flash for Linux?  My system is still running Jaunty and I'm using the Alpha 64-bit version of Flash which works quite well, so just curious which one they included in 64-bit Lucid.

Sam

---

### Post by alket on 2010-04-30
Me, just download the Linux x64 Flash from [http://labs.adobe.com](http://labs.adobe.com) unzip it and put it as root at /usr/lib/mozilla/plugins

---

### Post by chessnerd on 2010-04-30
Installing through the repos will give you NSPlugin wrapper and plethora of other packages along with the installer.

---

### Post by brian183 on 2010-04-30
If you install the package "ubuntu-restricted-extras" or "flashplugin-installer" it will install the 32bit flash with nspluginwrapper.  I downloaded the adobe 64bit flash from their site instead.

---

### Post by LowSky on 2010-04-30
> **babaroga said:**
> Me, just download the Linux x64 Flash from [http://labs.adobe.com](http://labs.adobe.com) unzip it and put it as root at /usr/lib/mozilla/plugins

I just put mine in the /home/*user*/.mozilla/plugins folder
seems to work fine their too. Then again I'm the only user on my machine.

---

### Post by swoll1980 on 2010-04-30
If your the only user just create a folder in .mozilla called plugins, and stick the 64bit  player from adobe's site in there. It works great.

---

### Post by mihai.ile on 2010-04-30
> **babaroga said:**
> Me, just download the Linux x64 Flash from [http://labs.adobe.com](http://labs.adobe.com) unzip it and put it as root at /usr/lib/mozilla/plugins

did the exact same thing after noticing that flash from synaptic wants to download ia32libs and such...

---

### Post by EMVirostek on 2010-04-30
I'm trying to do this and am getting the following error message...in LL-LTS...

"You don't have the right permissions to extract archives in the folder "file:///usr/lib/mozilla/plugins"

Any ideas?  I'm the only user...

---

### Post by clancymf on 2010-04-30
you probably need root priviledges

---

### Post by bedhead75 on 2010-04-30
You have to have root access to copy files to that folder.  Use "sudo".

---

### Post by EMVirostek on 2010-04-30
can you tell me how to use sudo?  I'm kind of a linux newb...

I assume I need to do it in a terminal...but I dont know the command...

Thanks!

---

### Post by BigSilly on 2010-04-30
As a newcomer, it's probably easier for you to just type ```
gksudo nautilus
``` then enter your password. That will give you full permissions to do what you like with the filesystem. Be careful though! :D

---

### Post by samalex on 2010-04-30
Hi everyone,

So I guess Flash isn't installed by default, but yeah I'll grab the 64-bit alpha version from Adobe either way since I really hate using the wrapper.  I just wasn't sure what Canonical included outta the box, if anything.

Sam

---

### Post by half-life on 2010-04-30
i already put the flash player 64bits in usr/lib/mozilla and now how do i turn it to default player when i have the wrapper as default?

---

### Post by EMVirostek on 2010-04-30
So I tried the gksudo nautilus command and still can't get it to let me relocate the plugin.

I downloaded the tar.gz file from adobe and guess i don't know how to get the .so to the right place...

Also, I'm getting an error on some webpages that there is a missing plug in and i am guided to click on a button to locate that plug in.  hen it takes me there and there are no available plugins...

So confused!

---

### Post by EMVirostek on 2010-04-30
Found this link...

[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Seems to work fine now!

Thanks for all the help!

---

### Post by swoll1980 on 2010-04-30
> **BigSilly said:**
> As a newcomer, it's probably easier for you to just type ```
gksudo nautilus
``` then enter your password. That will give you full permissions to do what you like with the filesystem. Be careful though! :D

As a newcomer having GUI root access to the file system is probably not a great idea.

---

### Post by VastOne on 2010-04-30
> **LowSky said:**
> I just put mine in the /home/*user*/.mozilla/plugins folder
seems to work fine their too. Then again I'm the only user on my machine.

This does not work for me...Gonna try it in the usr ....Plugins when I get back home

---

### Post by BigSilly on 2010-04-30
> **swoll1980 said:**
> As a newcomer having GUI root access to the file system is probably not a great idea.

No, but then it's not permanent is it?

---

### Post by zipperback on 2010-04-30
> **samalex said:**
> Hi,

For those running 64-bit Lucid, did it come preinstalled with NSPlugin wrapper and 32-bit Flash or the Alpha version of 64-bit Flash for Linux?  My system is still running Jaunty and I'm using the Alpha 64-bit version of Flash which works quite well, so just curious which one they included in 64-bit Lucid.

Sam

It looks like it is still installing the 32 bit version with the wrapper.

It's pretty simple to install the 64 bit version though.

- zipperback
:popcorn:

---

### Post by bro on 2010-04-30
can you help me out? The default install doesn't work for me because my mouse buttons don't interact with the flash player. 

So I copied the 64-bit version to ~/.mozilla/plugins/
I've also tried /usr/lib/mozilla/plugins/

I uninstalled all other flash stuff. It still doesn't recognize it and firefox says 'you need to upgrade your flash player to see this video' if I visit youtube. I restarted firefox. I logged in and out. 

I've been searching forums but can't find what I'm doing wrong.

(I'm doing this in Lucid)

---

### Post by DougieFresh4U on 2010-04-30
Not sure if this is correct, but I also put the libflashplayer.so file in my firefox plugins

---

### Post by bro on 2010-04-30
I found a solution that works for me. The script attached comes from underneath this [youtube video]("http://www.youtube.com/watch?v=KzshA3GKqyM").

Download the file, shutdown firefox and in a terminal navigate to the Download folder and type:

```
sudo ./installfl.sh
``` 

Don't know why someone made a youtube video for people who can't watch them :confused: but thank him nevertheless for the script. 

It did not kill my firefox in lucid. The line in the script should probably be killall -9 firefox-bin or something. If someone would like to improve on it...

---

### Post by Lensman on 2010-04-30
All I have ever done is to download and extract the 64 bit libflashplayer.so to my home directory.

Open a terminal, sudo and then type-

[CENTER]```
cp libflashplayer.so /usr/lib64/mozilla/plugins
```[/CENTER]

And you are good to go. Never failed me yet. Yes, you can do the same with Root privilege in Nautilus, but unless you know _exactly_ what you are doing, you could be in for a world of hurt.

Hope this helps.

---

### Post by oldos2er on 2010-04-30
> **bro said:**
> can you help me out? The default install doesn't work for me because my mouse buttons don't interact with the flash player. 


Sounds like this bug: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

---

### Post by Lightstar on 2010-04-30
> **bro said:**
> can you help me out? The default install doesn't work for me because my mouse buttons don't interact with the flash player. 
(I'm doing this in Lucid)

I had the same problem, was ready to go back to 32bit

Used this to fix it up, probably similar to the solution you found
[http://ubuntuforums.org/showthread.php?t=1358591]("http://ubuntuforums.org/showthread.php?t=1358591")

---

### Post by _0R10N on 2010-04-30
> **EMVirostek said:**
> Found this link...

[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Seems to work fine now!

Thanks for all the help!


It's works great on Lucid!!! One less problem!:guitar:

---

### Post by mamamia88 on 2010-04-30
removed flash plugin non free from synaptic then copied the file into the directory listed.  i still have restricted extras installed.  flash was still working even after i removed the flash plugin non-free from synaptic.  is there a way to tell which version of the plugin firefox is using?

---

### Post by oldos2er on 2010-04-30
Open a new tab in Firefox, location about:plugins

It should show Shockwave Flash, with a path to libflashplayer.so. Mine says "File: /usr/lib/flashplugin-installer/libflashplayer.so". If I run the command "file /usr/lib/flashplugin-installer/libflashplayer.so" I get the output "libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped"

---

### Post by WinterRain on 2010-04-30
> **LowSky said:**
> I just put mine in the /home/*user*/.mozilla/plugins folder
seems to work fine their too. Then again I'm the only user on my machine.

It also works in /usr/lib64/mozilla/plugins

---

### Post by WinterRain on 2010-04-30
> **oldos2er said:**
> Open a new tab in Firefox, location about:plugins

It should show Shockwave Flash, with a path to libflashplayer.so. Mine says "File: /usr/lib/flashplugin-installer/libflashplayer.so". If I run the command "file /usr/lib/flashplugin-installer/libflashplayer.so" I get the output "libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped"

That means you need to uninstall flashplugin-installer. That is the 32bit flash with the wrapper. Mine has no path. 

After installing non-free-codecs, (which includes ubuntu-restricted-extras) I had to remove flashplugin-installer and manually install 64bit libflashplayer.so

---

### Post by oldos2er on 2010-04-30
> **WinterRain said:**
> That means you need to uninstall flashplugin-installer. 

I don't have flashplugin-installer installed.

---

### Post by WinterRain on 2010-04-30
> **oldos2er said:**
> I don't have flashplugin-installer installed.

That's weird that it's showing up then. But it also says dynamically linked, and stripped, so maybe the 64bit flash overrode it.

---

### Post by garba on 2010-05-01
Just downloaded the following tar.gz package from adobe:

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc2_linux_041910.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc2_linux_041910.tar.gz)

after unzipping it I moved the library to the /usr/lib/mozilla/plugin folder, restarted firefox but flash doesn't work. Nice.

---

### Post by garba on 2010-05-01
Looks like there's something wrong with the flash version the adobe download center page links to, I can't get it to work on the Lynx. On the other hand, tried this one (this is the URL the script posted on this thread downloads the plugin from), and it works flawlessly:

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

---

### Post by Viva on 2010-05-01
I just downloaded the 64bit rc from adobe and copied it to ./mozilla/plugins directory in my home folder. Working perfectly so far.

---

### Post by garba on 2010-05-01
can't understand why the 10.1 rc release is not working for me :(

---

### Post by shuttleworthwannabe on 2010-05-01
Guys, here is a excellent HOWTO for dummies: [http://www.sucka.net/2010/04/proper-install-of-flash-for-x64-ubuntu/](http://www.sucka.net/2010/04/proper-install-of-flash-for-x64-ubuntu/)

I think we should give this guy a =D>

---

### Post by DougieFresh4U on 2010-05-01
Forum member carlee has provided anice little [installer]("http://ubuntuforums.org/showthread.php?t=1414595") for 64 bit flash

Thanks to carlee

---

### Post by mamamia88 on 2010-05-01
here is what mine looks like is that correct?

---

### Post by WinterRain on 2010-05-01
> **garba said:**
> can't understand why the 10.1 rc release is not working for me :(

You downloaded the 32bit version.  
[IMG]http://ccounty.files.wordpress.com/2009/08/doh1.jpg[/IMG]
[Here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz") is the one you want.

Edit: I just noticed you fixed it. The first link you tried *was* 32bit though.

---

### Post by oldos2er on 2010-05-01
> **WinterRain said:**
> That's weird that it's showing up then. But it also says dynamically linked, and stripped, so maybe the 64bit flash overrode it.

Just to clarify, I do have flashplugin64-installer installed.

---

### Post by markyb73 on 2010-05-01
i have used the ppa for a while  in the link shuttleworthwannabe has posted...works a treat :)

---

### Post by mbz99 on 2010-05-01
> **babaroga said:**
> Me, just download the Linux x64 Flash from [http://labs.adobe.com](http://labs.adobe.com) unzip it and put it as root at /usr/lib/mozilla/plugins

the current flash player plug-in here

/usr/lib/flashplugin-installer/

---

### Post by legolas_w on 2010-05-01
How I can understand whether I have the real 64 bit flash or the wrapper one?
I used ubuntu-tweak to install flash and actually I installed anything named flash available in the list of applications along with ubuntu extras :d

thansk

---

### Post by dartdog on 2010-05-01
I prefer Chrome on 64 (Chromium to be precise,,) any one have 64 bit flash configured, if so care to share info on what to do?

---

### Post by garba on 2010-05-01
> **WinterRain said:**
> You downloaded the 32bit version.  
[IMG]http://ccounty.files.wordpress.com/2009/08/doh1.jpg[/IMG]
[Here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz") is the one you want.

Edit: I just noticed you fixed it. The first link you tried *was* 32bit though.

oh my that's true, now I feel dumb, I got there looking for "linux 64bit flash download" on google but didn't realize that stuff was meant for 32bit platforms.

---

### Post by oldos2er on 2010-05-01
> **legolas_w said:**
> How I can understand whether I have the real 64 bit flash or the wrapper one?
I used ubuntu-tweak to install flash and actually I installed anything named flash available in the list of applications along with ubuntu extras :d

 On Ubuntu tweak (running Lucid), Click Application Center, Other, and you should see Flashplugin64-installer. I would uninstall other versions of flash, if I were you.

---

### Post by legolas_w on 2010-05-02
> **oldos2er said:**
> On Ubuntu tweak (running Lucid), Click Application Center, Other, and you should see Flashplugin64-installer. I would uninstall other versions of flash, if I were you.



I removed the other flash and installed the 64 bit one but I am facing a problem.

After doing this and restaring firefox it does not show any flash content and instead it shows a message that I need a plugin to view the flash enabled pages correctly.

Any idea?

thanks.

---

### Post by WinterRain on 2010-05-02
> **legolas_w said:**
> I removed the other flash and installed the 64 bit one but I am facing a problem.

After doing this and restaring firefox it does not show any flash content and instead it shows a message that I need a plugin to view the flash enabled pages correctly.

Any idea?

thanks.

Download [this]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz") and extract it and put it in /usr/lib/mozilla/plugins. Uninstall the other one first though.

---

### Post by Linuxforall on 2010-05-02
Alpha working fine here using the sudo mv libflashplayer.so /usr/lib/mozila/plugins method.

---

### Post by WinterRain on 2010-05-02
> **Linuxforall said:**
> Alpha working fine here using the sudo mv libflashplayer.so /usr/lib/mozila/plugins method.

Been working great for me.

---

### Post by moleschott on 2010-05-02
sudo mv libflashplayer.so /usr/lib/mozila/plugins

it says no such folder. How can i install flash player on my 64 bit system. Please tell me

---

### Post by Viva on 2010-05-02
> **moleschott said:**
> sudo mv libflashplayer.so /usr/lib/mozila/plugins

it says no such folder. How can i install flash player on my 64 bit system. Please tell me

Just create a folder called plugins in ./mozilla directory in your home folder and move the file there. Make sure you don't have any other flash plugins installed.

---

### Post by Goldenlight on 2010-05-03
Very easy to do and I know nothing about using Terminal

1) Step one download latest version f__rom [http://labs.adobe.com](http://labs.adobe.com) navigate to 64 bit flash

2)Download and **EXTRACT** file to Desktop, or any folder you can remember

3)Open Terminal Screen and navigate to where file was downloaded.  Example *cd Desktop*. This is where I extracted it at.  Folder directories are case sensitive in Linux. Make sure you type the folder exactly as it appears. [FONT=Arial Narrow][I]Ex.. Documents and documents are completely different folders.

[/I][/FONT]Should look  similar to this user@user-desktop:~$

4)Last step type    	 	 	 	 	 	   **sudo cp ~/libflashplayer.so /usr/lib64/mozilla/plugins**
Enjoy 64 bit flash...
:popcorn::popcorn::popcorn:

Credit goes to WinterRain..
   [URL="http://labs.adobe.com/"]
[/URL]
 []("http://labs.adobe.com/")

---

### Post by oldos2er on 2010-05-03
> **moleschott said:**
> sudo mv libflashplayer.so /usr/lib/mozila/plugins

it says no such folder. How can i install flash player on my 64 bit system. Please tell me

There's a typo in your command; should be sudo mv libflashplayer.so /usr/lib/mozilla/plugins

---

