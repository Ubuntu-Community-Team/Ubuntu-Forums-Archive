---
title: "Adobe Tools"
date: 2010-02-23
forum: The Cafe
---

### Post by sandyd on 2010-02-23
This utility aids in the installation/removal of flash (32bit/64bit) and the installation of Adobe AIR.

Currently, it

[LIST]
[*]Installs / Removes Adobe Flash Player
[/LIST]
[_**[Download]**_]("http://code.google.com/p/adobe-flash-tools/downloads/list")  

[B]Files
[/B]
[LIST]
[*][Adobe Tools for Ubuntu (32-bit)]("http://adobe-flash-tools.googlecode.com/files/adobe_tools-ubuntu")
[*][Adobe Tools for Ubuntu (64-bit)]("http://adobe-flash-tools.googlecode.com/files/adobe_tools-ubuntu-64bit")
[*][Adobe Tools for Kubuntu (32-bit)]("http://adobe-flash-tools.googlecode.com/files/adobe_tools-kubuntu")
[*][Adobe Tools for Kubuntu (64-bit)]("http://adobe-flash-tools.googlecode.com/files/adobe_tools-kubuntu-64bit")
[/LIST]
 [B]Downloads
[/B]The number of downloads is recorded each time I upload new files, cause it resets when I do that.
Currently: **6305**

[B]How To Run
[/B]
[LIST]
[*]Right click on the file you downloaded
[*]Select "Properties"
[*]Click on "Permissions"
[*]check the "Execute" box
[/LIST]
[[More Info / Source Code]]("http://dolphinaura.com/projects/")
Bug reporting can be done through [https://launchpad.net/adobe-flash-plugin-tools](https://launchpad.net/adobe-flash-plugin-tools)

And if you like it, please click "Like" at [http://bit.ly/9jzUcr](http://bit.ly/9jzUcr)

---

### Post by lovinglinux on 2010-02-23
That is interesting. You could team up with [michael37](http://ubuntuforums.org/showthread.php?t=1358591) to provide the option to install the 64bit, if you do not already provide this functionality (I haven't tested your tool). This would save a lot of time for lots of users.

---

### Post by lovinglinux on 2010-02-23
Now I see in the pic that you provide an option to install the 64bit. Nice work.

---

### Post by sandyd on 2010-02-24
bump

---

### Post by NoaHall on 2010-02-24
Why don't you get it to only display the right architecture button?

---

### Post by Majorix on 2010-02-24
> **carlee said:**
> 
The removal hacks I included were.
```

gksudo rm /var/lib/dpkg/info/flashplugin* & gksudo rm /var/lib/dpkg/info/adobe-flashplugin* & gksudo dpkg --remove --force-remove-reinstreq adobe-flashplugin & gksudo apt-get purge flashplugin-installer gnash mozilla-swfdec & gksudo rm /usr/lib/mozilla/plugins/libflashplayer.so & gksudo rm ~/.mozilla/plugins/libflash* & gksudo rm /usr/lib/firefox-3*/plugins/libflash* & gksudo apt-get remove --purge flashplugin-installer & gksudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash & gksudo apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin & gksudo apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin & gksudo apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin & gksudo rm -f ~/.mozilla/plugins/*flash* & gksudo rm -f /usr/lib/firefox-addons/plugins/*flash* & gksudo rm -f /usr/lib/firefox/plugins/*flash* & gksudo rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so & gksudo rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so & gksudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so & gksudo rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so & gksudo rm -f /usr/lib/mozilla/plugins/*flash* & gksudo rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so & gksudo rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so & gksudo rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

```if im missing any, let me know ;)


Correct me if I am wrong - I do not do any shell coding - but isn't gksudo used to start graphical applications that would require root rights? Like say
```
gksudo synaptic
```
?

This is a nice idea of yours, hope it helps newbies. Speaking of which, why don't you post this in the beginners section?

---

### Post by sandyd on 2010-02-24
> **Majorix said:**
> Correct me if I am wrong - I do not do any shell coding - but isn't gksudo used to start graphical applications that would require root rights? Like say
```
gksudo synaptic
```
?

This is a nice idea of yours, hope it helps newbies. Speaking of which, why don't you post this in the beginners section?

cause it still in testing. (I just noticed I named a window wrong... which made the removal button not work)
im using gksudo, becasue theirs no way for the user to enter their password other than gksudo.
still works though :)

however, if a mod sees these words and would like to move this to the beginners section, ill be more than happy for it to reside there :)

---

### Post by sandyd on 2010-02-24
> **NoaHall said:**
> Why don't you get it to only display the right architecture button?

some people prefer nspluginwrapper. still wanna give them some choice if they really wanna install it 32 bit, since x64 is still a bit buggy.

however, if the plugin matures, I shal consider making only one button.

---

### Post by NoaHall on 2010-02-24
> **carlee said:**
> some people prefer nspluginwrapper. still wanna give them some choice if they really wanna install it 32 bit, since x64 is still a bit buggy.

however, if the plugin matures, I shal consider making only one button.

If they don't know how to install it anyway, they won't know about the wrapped version. :)

---

### Post by sandyd on 2010-02-24
> **NoaHall said:**
> If they don't know how to install it anyway, they won't know about the wrapped version. :)

theyl ask me why their firefox is segfaulting when using flash then....

---

### Post by lovinglinux on 2010-02-25
Seems to be working fine here. Nice job.

I have included a link to this thread on my tutorial and will start to link it on flash installation/fix threads.

---

### Post by sandyd on 2010-02-26
> **lovinglinux said:**
> Seems to be working fine here. Nice job.
 
I have included a link to this thread on my tutorial and will start to link it on flash installation/fix threads.
 thanks!

---

### Post by lovinglinux on 2010-02-26
EDIT: never mind, it seems it was a problem with YouTube Annotation system.

---

### Post by uRock on 2010-02-27
I haven't needed to use it yet, but I wanted to say thanx for putting that app together. I am sure it will help people. So, that said,

Thank you!:D

Ronnie

---

### Post by Flake Remix on 2010-02-28
```
adobe_flash_installer-kubuntu$ ./adobe_flash_installer-kubuntu
bash: ./adobe_flash_installer-kubuntu: cannot execute binary file
```

What do I do wrong? I use Kubuntu 9.10

---

### Post by sandyd on 2010-02-28
your supposed to double click on it.

---

### Post by forbidenpasionfruit on 2010-03-01
Hi, I just noticed the date on this, but I thought I'd reply anyway. I'm looking to install Flash on 9.10 and found this post first. I'm still a complete noob at Linux and still can't get my network to run properly so please feel free to point me in the direction of a more suitable post instead of wasting time replying yourself!  Anyway, I downloaded your file, and couldn't work out how to install it. I tried the terminal and stuff then I saw the note to double click on it, but nothing happened (yes I extracted it first). 

Any ideas?

Cheers,
pasion.

---

### Post by 3rdalbum on 2010-03-01
I appreciate the effort you've put into this program, but the best (and graphical) solution is to either install the 32-bit player in Synaptic, or install the 64-bit plugin from the PPA. Both of these options are easy.

---

### Post by forbidenpasionfruit on 2010-03-01
Hi again, found the answer in another thread.

This link [apt:adobe-flashplugin?channel=$distro-partner](apt:adobe-flashplugin?channel=$distro-partner) seems to do it all by itself!

Excellent!

---

### Post by hansheijmans on 2010-03-01
Maybe a stupid question after reading millions of threads: if I use the flashplugin-installer from the standard repositories, do I get a 32-bit flash plugin?

If that's the case, could someone tell me why? Are there stability issues with 64-bit flash?

---

### Post by sandyd on 2010-03-01
> **hansheijmans said:**
> Maybe a stupid question after reading millions of threads: if I use the flashplugin-installer from the standard repositories, do I get a 32-bit flash plugin?

If that's the case, could someone tell me why? Are there stability issues with 64-bit flash?
yup.

flash 64 bit is still beta.
see : 
[http://labs.wip3.adobe.com/technologies/flashplayer10/64bit.html](http://labs.wip3.adobe.com/technologies/flashplayer10/64bit.html)

---

### Post by hansheijmans on 2010-03-01
> **carlee said:**
> yup.

flash 64 bit is still beta.
see : 
[http://labs.wip3.adobe.com/technologies/flashplayer10/64bit.html](http://labs.wip3.adobe.com/technologies/flashplayer10/64bit.html)

Thanks Carlee!

By reading this article I get the feeling it won't take too long before Adobe releases the final stable version (maybe in 6 months or so?). What would be the benefit of installing 64-bit alpha release?

Actually I do have some problems with flash, especially when my kids want to play online games. Works like a charm on 32-bit laptop,  doesn't work at all on 64-bit desktop... And the funny thing is: does work when connecting to my desktop computer thru freenx client :confused:, but that could be a topic for another thread I suppose.

---

### Post by uRock on 2010-03-01
> **hansheijmans said:**
> Thanks Carlee!

By reading this article I get the feeling it won't take too long before Adobe releases the final stable version (maybe in 6 months or so?). What would be the benefit of installing 64-bit alpha release?

Actually I do have some problems with flash, especially when my kids want to play online games. Works like a charm on 32-bit laptop,  doesn't work at all on 64-bit desktop... And the funny thing is: does work when connecting to my desktop computer through freenx client :confused:, but that could be a topic for another thread I suppose.

Using the testing version should fix your issues. I was doing good with the version that came with ubuntu-restricted-extras until one website changed their software, which in turn required me to change mine. Sadly, I found this thread a few days late.

---

### Post by blur xc on 2010-03-02
> **3rdalbum said:**
> I appreciate the effort you've put into this program, but the best (and graphical) solution is to either install the 32-bit player in Synaptic, or install the 64-bit plugin from the PPA. Both of these options are easy.

What PPA is there for 64 bit flash?  I have a few computers running 64 bit 9.10, and ubuntu-restricted-extras installs the 32bit flash.  I had to manually remove it, find the 64 bit plugin from adobe's website (wasn't easy) and then install that.  Finding the folder to install it to was a challenge as well.  90% of instructions on the forums have you stick it in your ~/.mozilla/yadda/yadda folder, but I wanted it to be globally installed for all users.  It wasn't hard once I found out all the information I needed, but finding it was a pain.

BM

---

### Post by hansheijmans on 2010-03-02
Probably due to my poor knowledge, I wasn't able to compile Carlee's c-program so I tried something else.

This is my experience so far:

I ran the following script (which I obtained from another thread, I forgot which one) to make sure there would be nothing left of any installed flashplugin

```
#!/bin/bash
apt-get remove --purge flashplugin-installer
apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash
apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin
apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin
apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
rm -f ~/.mozilla/plugins/*flash*
rm -f /usr/lib/firefox-addons/plugins/*flash*
rm -f /usr/lib/firefox/plugins/*flash*
rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so
rm -f /usr/lib/mozilla/plugins/*flash*
rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so
rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

```Then I downloaded the Alfa 3 release of the 64-bit flashplayer from

_[COLOR=Red][http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)[/COLOR]_

I extracted the libflashplayer.so file from the archive and copied it to

***/usr/lib64/firefox-addons/plugins***

and I got a working 64-bit flashplugin !!

No more trouble for my kids playing flash games online.

There is only one thing to keep in mind. As soon as Adobe releases a new version, you have to go though this procedure again.

---

### Post by sandyd on 2010-03-02
> **hansheijmans said:**
> Probably due to my poor knowledge, I wasn't able to compile Carlee's c-program so I tried something else.

This is my experience so far:

I ran the following script (which I obtained from another thread, I forgot which one) to make sure there would be nothing left of any installed flashplugin

```
#!/bin/bash
apt-get remove --purge flashplugin-installer
apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash
apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin
apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin
apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
rm -f ~/.mozilla/plugins/*flash*
rm -f /usr/lib/firefox-addons/plugins/*flash*
rm -f /usr/lib/firefox/plugins/*flash*
rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so
rm -f /usr/lib/mozilla/plugins/*flash*
rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so
rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

```Then I downloaded the Alfa 3 release of the 64-bit flashplayer from

_[COLOR=Red][http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)[/COLOR]_

I extracted the libflashplayer.so file from the archive and copied it to

***/usr/lib64/firefox-addons/plugins***

and I got a working 64-bit flashplugin !!

No more trouble for my kids playing flash games online.

There is only one thing to keep in mind. As soon as Adobe releases a new version, you have to go though this procedure again.
you dont need to compile it, just download the tar.gz for ubuntu

---

### Post by dcstar on 2010-03-02
> **hansheijmans said:**
> 
........
Then I downloaded the Alfa 3 release of the 64-bit flashplayer from

_[COLOR=Red][http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)[/COLOR]_

I extracted the libflashplayer.so file from the archive and copied it to

***/usr/lib64/firefox-addons/plugins***

and I got a working 64-bit flashplugin !!

No more trouble for my kids playing flash games online.

There is only one thing to keep in mind. As soon as Adobe releases a new version, you have to go though this procedure again.

The only "procedure" is a download and copy, not really a big impost.

Anyway, here is a script that I just created that goes to that Abobe web site and fetches and installs the latest version of the 64-bit plugin (I have tested it on my 9.04 64-bit system). It incorporates the "clean-up" code used earlier in this thread:

```
#!/bin/bash
# Get-Flash-64
# Fetch latest Linux 64-bit development Flash Player from Adobe site and extract and install automatically
# 03/03/2010 David Clayton
#
# Run as sudo!
#
#If not 64-bit then abort
if [ `uname -m` != 'x86_64' ]
then
 echo 'Not 64-bit system, exiting!'
 exit
fi
#
# First get rid of any old Flash stuff (this code taken from Ubuntu forums post):
#
apt-get remove --purge flashplugin-installer
apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash
apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin
apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin
apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
rm -f ~/.mozilla/plugins/*flash*
rm -f /usr/lib/firefox-addons/plugins/*flash*
rm -f /usr/lib/firefox/plugins/*flash*
rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so
rm -f /usr/lib/mozilla/plugins/*flash*
rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so
rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
#
#
# Now fetch the latest (delete any old web pages previously downloaded):
rm flashplayer10_64bit.html
wget http://labs.adobe.com/downloads/flashplayer10_64bit.html
Latest_File=$(grep "Download 64-bit Plugin for Linux" flashplayer10_64bit.html | awk -F 'href="|">' '{print $2}')
wget $Latest_File
tar -xvf libflashplayer* --directory /usr/lib/firefox-addons/plugins
# Clean up now
rm flashplayer10_64bit.html
rm libflashplayer*
```

You can run it as a root cron job every week or so to ensure that the latest 64-bit plugin is always on your system (until Adobe release the official version).

---

### Post by musicman10489 on 2010-03-02
Carlee thank you so much! The installer worked beautifully :]

---

### Post by nikef on 2010-03-06
Hi Carlee 

You directed me to your post about how to un-install flashplayer 10.1 beta 

Could you guide me through this if at all possible please ?

The trouble is i do need flashplayer 10.1 beta to play Yoville on Facebook but 

I wanted to also download Frostwire and there is where the error starts 

Now i know i can have both because i have this setup on my laptop ,it just does not want to work on my pc 

I would be very grateful for any help Thanks

---

### Post by sandyd on 2010-03-06
> **nikef said:**
> Hi Carlee 

You directed me to your post about how to un-install flashplayer 10.1 beta 

Could you guide me through this if at all possible please ?

The trouble is i do need flashplayer 10.1 beta to play Yoville on Facebook but 

I wanted to also download Frostwire and there is where the error starts 

Now i know i can have both because i have this setup on my laptop ,it just does not want to work on my pc 

I would be very grateful for any help Thanks
you mean running on different browsers right?

if your meaning that... then click the uninstall button.
wait a while...
click the x64 button...
install chromium-browser...
```

sudo mv /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/chromium-browser/plugins/libflashplayer.so

```
install flash (flashplugin-installer)
```

sudo rm /usr/lib/mozilla/plugins/flashplugin-nonfree*
```
chromium will now have x64 bit flash, firefox will have 32 bit flash.

the bug report seems to hint that its a problem with ndiswrapper, so try clicking the "remove" button, then the "install(x64)" button. Close the browser and try using yoville.
if it doesnt work... well... follow the instructions above... (after clicking the remove button again..)

---

### Post by nikef on 2010-03-06
Thanks Carlee for all your help , i am sorry but its very confusing 

here is my problem i have copied the libflshplayer.so into the firefox pluggins and this works great but.......

When i try to install frostwire it will not let me because it says it can not un-install flashplayer 10.1 beta 

I have tried your suggestions , how long do i have to wait for the installer button to come up ? as i waited 20 mins

I have tryed your other suggestios in the above post and i get this 
cannot stat `/usr/lib/mozilla/plugins/libflashplayer.so': No such file or directory

Also for the install flash (flashplugin-installer) i get this 
sudo rm /usr/lib/mozilla/plugins/flashplugin-nonfree*
rm: cannot remove `/usr/lib/mozilla/plugins/flashplugin-nonfree*': No such file or directory


I am not sure if i am doing this right sorry 

Thanks again for all your help 

Trish

---

### Post by sandyd on 2010-03-06
> **nikef said:**
> Thanks Carlee for all your help , i am sorry but its very confusing 

here is my problem i have copied the libflshplayer.so into the firefox pluggins and this works great but.......

When i try to install frostwire it will not let me because it says it can not un-install flashplayer 10.1 beta 

I have tried your suggestions , how long do i have to wait for the installer button to come up ? as i waited 20 mins

I have tryed your other suggestios in the above post and i get this 
cannot stat `/usr/lib/mozilla/plugins/libflashplayer.so': No such file or directory

Also for the install flash (flashplugin-installer) i get this 
sudo rm /usr/lib/mozilla/plugins/flashplugin-nonfree*
rm: cannot remove `/usr/lib/mozilla/plugins/flashplugin-nonfree*': No such file or directory


I am not sure if i am doing this right sorry 

Thanks again for all your help 

Trish
do you mean the installer button or the uninstaller button?

---

### Post by sandyd on 2010-03-06
> **nikef said:**
> Thanks Carlee for all your help , i am sorry but its very confusing 

here is my problem i have copied the libflshplayer.so into the firefox pluggins and this works great but.......

When i try to install frostwire it will not let me because it says it can not un-install flashplayer 10.1 beta 

I have tried your suggestions , how long do i have to wait for the installer button to come up ? as i waited 20 mins

I have tryed your other suggestios in the above post and i get this 
cannot stat `/usr/lib/mozilla/plugins/libflashplayer.so': No such file or directory

Also for the install flash (flashplugin-installer) i get this 
sudo rm /usr/lib/mozilla/plugins/flashplugin-nonfree*
rm: cannot remove `/usr/lib/mozilla/plugins/flashplugin-nonfree*': No such file or directory


I am not sure if i am doing this right sorry 

Thanks again for all your help 

Trish
nvm. lets do this simple.

click the remove button. that will force-remove flash 10.1 beta.
install frostwire.
reinstall 10.1 plugin.

---

### Post by nikef on 2010-03-06
Thanks Carlee 

But where is this remove button ?

Thanks for your help i really appreciate it :D

---

### Post by nikef on 2010-03-07
Thanks for all your help Carlee 

I know this may seem abit extreeme but i messed up my ubuntu last night 

So i put a new fresh install on my pc and downloaded frostwire and the flashplayer 10.1 and everything is working ok :p

---

### Post by gfi on 2010-03-10
Running 64-bit Karmic..
Unfortunately, Carlee's installer didnt work here.
So, I followed post #25 ([http://ubuntuforums.org/showpost.php?p=8906177&postcount=25](http://ubuntuforums.org/showpost.php?p=8906177&postcount=25)) to completely get rid of all flash plugins and then copied the downloaded '.so' as directed.

Flash works well in FF now.

For Chrome, I just copied the 'so' to /opt/google/chrome/plugins/ (NOTE: Create the 'plugins'folder, if it doesnt exist).

Now, have flawless flash player in FF and Chrome.
Thankz

---

### Post by sandyd on 2010-03-10
> **gfi said:**
> Running 64-bit Karmic..
Unfortunately, Carlee's installer didnt work here.
So, I followed post #25 ([http://ubuntuforums.org/showpost.php?p=8906177&postcount=25](http://ubuntuforums.org/showpost.php?p=8906177&postcount=25)) to completely get rid of all flash plugins and then copied the downloaded '.so' as directed.

Flash works well in FF now.

For Chrome, I just copied the 'so' to /opt/google/chrome/plugins/ (NOTE: Create the 'plugins'folder, if it doesnt exist).

Now, have flawless flash player in FF and Chrome.
Thankz

thats cuz your supposed to click the "remove" button first... the remove button actually runs the same commands in the post you mentioned. in fact, I copied the removal button scripts from there.

---

### Post by lidex on 2010-03-16
Nice job carlee! Was using sevenmachine ppa for x64 on lucid A3 with stuttering issues. Smooth as silk now. Removal/install was seamless. O:)

---

### Post by ElectroDruid on 2010-03-16
carlee: Thank you very much! I'm a newbie and while I want to learn it all eventually, it was nice to have your tool make my initial setup easy.

---

### Post by wjm on 2010-03-19
I'm no newbie, but this just made my life so damn easy.  Are you accepting marriage proposals?

---

### Post by fjf on 2010-03-20
Thankyou.  It works.  I just installed the i386 version to my AMD64 karmic firefox.

---

### Post by fotis_utmost on 2010-03-22
Thanks! It worked great!

---

### Post by Swagman on 2010-03-22
I am testing out Lucid Lynx on a USB stick.

Do I need to first install ubuntu-restricted-extras then remove flash and install via your app ?

---

### Post by sandyd on 2010-03-22
> **Swagman said:**
> I am testing out Lucid Lynx on a USB stick.

Do I need to first install ubuntu-restricted-extras then remove flash and install via your app ?

just click the remove button first, before installing.

---

### Post by Swagman on 2010-03-23
> **carlee said:**
> just click the remove button first, before installing.

Well it worked. :D

But I've got no sound.  This seems to be a core problem though as I have no sound on anything !!

Sound prefs/output shows that "Dummy output" is selected.

This is not your problem though Carlee as your proggie clearly has worked.

ok.. This is all running 64 bit Lucid on a "Live USB stick" Just to test out if 64 bit is worth installing when 10:04 is released.

Looks like it IS worth it now.

Sold.

---

### Post by sonofjefferson on 2010-04-01
Very 'newbie' and struggling with installing.  Carlee's program sound perfect, but w/o simple install (simple=idiot proof), I am lost.  Namoroka blasted my system, as everything was working fine before, then BOOM.

---

### Post by basily on 2010-04-02
What am I missing? I double click on the extracted file (adobe_flash_installer) and nothing happens. If I try to run it from the terminal I get an error.:confused:

---

### Post by williammanda on 2010-04-02
Does this install the latest Flash 10.1 beta 3?

---

### Post by sandyd on 2010-04-02
there is no 10.1 beta 3 support cause I initially designed it for the x64 plugin, but now that you say it, I will think about it once I get home from work.

---

### Post by williammanda on 2010-04-02
Here's the link for the 10.1 beta 3

[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

---

### Post by williammanda on 2010-04-03
Here is the link for 10.1 alpha 64 bit.

[http://labs.adobe.com/downloads/flashplayer10_64bit.html]("http://labs.adobe.com/downloads/flashplayer10_64bit.html")

---

### Post by niceguy123 on 2010-04-05
carlee,

I tried opening the  	adobe_flash_installer-ubuntu.tar.gz and got this:


> /tmp/adobe_flash_installer-ubuntu.tar-1.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences.


What should I do now?

Thanks,

---

### Post by williammanda on 2010-04-05
Save it then extract it! Then run the adobe_flash_installer.

---

### Post by Nevyn on 2010-04-05
This should be put in the instructions :-)
> **williammanda said:**
> Save it then extract it! Then run the adobe_flash_installer.

Very smooth and nice little uninstaller/installer. Makes it very easy for newbies. :KS
After I pressed the remove-button the window became grey and would not respond. I waited for 25 minutes and force closed it since it did not respond. The second try it worked like a charm. It may be because I had FF running the first time I tried. Thanks for making Linux Life easier :-)

---

### Post by niceguy123 on 2010-04-05
OK, I downloaded the file, extracted and did the uninstall and installed flash 64. Restarted FF and tried youtube. But have the same problem I had before. Some youtube clips are coming up as a black screen with no option to play others come up OK.

---

### Post by J V on 2010-04-05
Incorperate this? Makes it a nice single button app for the poor windows users :)

Use it myself on new installs```
sudo apt-get --force-yes install flashplugin-nonfree
if [ `uname -m` = "x86_64" ]
then
    sudo apt-get --force-yes remove flashplugin-nonfree
    wget "http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz" # Needs something to find most recent version, haven't the time or energy to make this lol
    tar -xzf "libflashplayer-*.so.tar.gz" --directory "~/.mozilla/plugins"
    rm -f "libflashplayer-*.so.tar.gz"
fi
```

---

### Post by TMachado on 2010-04-07
Removed flash and then installed for x64... but still now working :(

Any ideas ?

---

### Post by lidex on 2010-04-07
> **TMachado said:**
> Removed flash and then installed for x64... but still now working :(

Any ideas ?

Yes
[http://ubuntuforums.org/showthread.php?t=1441327]("http://ubuntuforums.org/showthread.php?t=1441327")
[http://ubuntuforums.org/showthread.php?t=1435349]("http://ubuntuforums.org/showthread.php?t=1435349")

---

### Post by sandyd on 2010-04-07
alright. until the devs decide to fix  [https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/554935](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/554935)

I wont be able to do any more mods to this program. I unfortunately cannot see what the heck im typing.

---

### Post by uRock on 2010-04-10
Has anyone tested this awesome app on Lucid yet?

Cheers,
Ronnie

P.S. Carlee, I hope they get that fixed for ya. I don't use KDE, so i can't add to it.

---

### Post by lovinglinux on 2010-04-10
> **uRock said:**
> Has anyone tested this awesome app on Lucid yet?

Cheers,
Ronnie

P.S. Carlee, I hope they get that fixed for ya. I don't use KDE, so i can't add to it.

Yes. It didn't work. Nevertheless, I haven't tried to debug. I was in a hurry and already had installed Lucid 3 times.

---

### Post by uRock on 2010-04-10
Kool, I tried to install a few minutes ago and realized I was still in Windows, oops. I'll give it a try in the morning.

---

### Post by lidex on 2010-04-11
> **uRock said:**
> Has anyone tested this awesome app on Lucid yet?

Cheers,
Ronnie

P.S. Carlee, I hope they get that fixed for ya. I don't use KDE, so i can't add to it.

Yeah. It worked for me.

---

### Post by hermitical on 2010-04-11
> **williammanda said:**
> Save it then extract it! Then run the adobe_flash_installer.

any help on why when I double click on the extracted adobe_flash_installer nothing happens?

---

### Post by nilarimogard on 2010-04-11
> **hermitical said:**
> any help on why when I double click on the extracted adobe_flash_installer nothing happens?

Same here, both on Karmic and Lucid.

---

### Post by lidex on 2010-04-11
Some people are having this issue, though not sure why. Right-click on it and select properties, on the permissions tab, make sure you are owner and have read, write and execute privileges.

---

### Post by hermitical on 2010-04-11
aye, checked that and still no go, I've made sure that it is executable but it tells me that it 'cannot execute binary file'

---

### Post by lidex on 2010-04-11
> **hermitical said:**
> aye, checked that and still no go, I've made sure that it is executable but it tells me that it 'cannot execute binary file'

Can you post a screenshot of "System>Preferences>File Management" - the "Behavior" tab, please?

---

### Post by hermitical on 2010-04-11
:(

no, because it isn't listed! Alphabetically it goes from 'Display' to 'Ibus Preferences'

---

### Post by lidex on 2010-04-11
Just open a nautilus window. Look in the "Edit>Preferences" window.

---

### Post by chappajar on 2010-04-11
> **hermitical said:**
> aye, checked that and still no go, I've made sure that it is executable but it tells me that it 'cannot execute binary file'

On a noexec partition?

This looks nice.
Does it display the 64 bit option on 32 bit hardware?
Could it automatically detect pre-installed flash and alter it's behaviour based on that?
Maybe a message to help newbs with 64 bit hardware make the choice between 32 and 64 bit flash would be helpful?
I'm going to bookmark this for helping people having trouble installing flash in the future.

BTW, what is that window border/buttons/etc?  I want it ;)

---

### Post by sandyd on 2010-04-11
i guess its time for me to look at these...
> **nilarimogard said:**
> Same here, both on Karmic and Lucid.
could you try running it from the terminal, then posting the error?
if it just segfaults, run
```

dpkg -l > ~/Desktop/dpkg_list.txt

```
and upload it.

> **hermitical said:**
> any help on why when I double click on the extracted adobe_flash_installer nothing happens?
see above
> **chappajar said:**
> On a noexec partition?

This looks nice.
Does it display the 64 bit option on 32 bit hardware?
**yup. thats one of the issues that im planning to work on...**
Could it automatically detect pre-installed flash and alter it's behaviour based on that?
Maybe a message to help newbs with 64 bit hardware make the choice between 32 and 64 bit flash would be helpful?
I'm going to bookmark this for helping people having trouble installing flash in the future.
**That was one of the parts we were at war about. The 64-bit plugin works for some people, and doesnt work for some, so Im attempting to provide a backup plan for them incase they find their flash unusable.**
BTW, what is that window border/buttons/etc?  I want it ;)
**thats kde + qtcurve GTK**

yeah. ill begin the stuff hopefully on wednesday.
you can see a todo list [here]("http://www.carleedolphinaura.co.cc/software/adobe-flash-plugin-installer-uninstaller-linux")

---

### Post by hermitical on 2010-04-12
this is the result when I tried running it from terminal

> *****:~/Downloads$ ./adobe_flash_installer
bash: ./adobe_flash_installer: cannot execute binary file


---

### Post by hermitical on 2010-04-12
> **lidex said:**
> Just open a nautilus window. Look in the "Edit>Preferences" window.

here it is,,,

---

### Post by sandyd on 2010-04-12
New update, see : [http://www.carleedolphinaura.co.cc/programming/adobe-flash-player-installer-uninstaller/added-flash-10-1-beta-support](http://www.carleedolphinaura.co.cc/programming/adobe-flash-player-installer-uninstaller/added-flash-10-1-beta-support)
for details

---

### Post by lidex on 2010-04-12
> **hermitical said:**
> this is the result when I tried running it from terminal

OK, I think i figured it out. It's a 64bit executable:
```
file adobe_flash_installer
adobe_flash_installer: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, not stripped

```
My guess is you're install is x32 so it's not going to work. Wonder how carlee overlooked that.

---

### Post by sandyd on 2010-04-12
> **lidex said:**
> OK, I think i figured it out. It's a 64bit executable:
```
file adobe_flash_installer
adobe_flash_installer: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, not stripped

```My guess is you're install is x32 so it's not going to work. Wonder how carlee overlooked that.
my appologies.:oops:
its compiled in 32 bit now, so have another try...:-\"

---

### Post by hermitical on 2010-04-14
looking good so far - thanks!

---

### Post by egalvan on 2010-04-15
> **carlee said:**
> 

> 
**to completely get rid of all flash plugins**


thats cuz your supposed to click the "remove" button first...
 the remove button actually runs the same commands in the post you mentioned.
 in fact, I copied the removal button scripts from there.

So this could be used to purge a system of all flash plug-ins?

I click "remove"
exit the program
and all flash is gone?

That would be cool, one more tool in my box of goodies.

---

### Post by sandyd on 2010-04-15
> **egalvan said:**
> So this could be used to purge a system of all flash plug-ins?

I click "remove"
exit the program
and all flash is gone?

That would be cool, one more tool in my box of goodies.
I still have one plugin that it doesnt remove.. yet
now that you reminded me, ill commit it to git as soon as I got some time...

---

### Post by jord9308 on 2010-04-22
> **carlee said:**
> I noticed that newbies were having trouble installing x64 bit flash, and having problems removing/reinstalling screwed up versions of flash player, so I created this.
 
Its a simple GtK window.
 
 P.S. After clicking the button, it will **appear** that the window is frozen, but it really isnt. its just processing stuff in the background.

[COLOR=Red]p.p.s. IMPORTANT: make sure you click the removal button first!!!
[/COLOR] **CHANGELOG**
12/4/2010
*Added Flash 10.1
*Updated Binaries, Should work on Lucid now & 32-bit systems
25/2/2010
*Added (K)ubuntu support
24/2/2010
*Fixed Remove Button
*Fixed the "&&" commands by replacing them with separate system calls
*Fixed the gksudo problem by adding single quotes around the commands.
*Removed the need to the tmp directory, the installer just downloads to its current location and deletes it after installation.
*Cleaned up codes.
*Adding Comments.
----------------
23/2/2010
*Initial Release
----------------

[_**Download**_]("http://github.com/carleedolphinaura/Flash-Plugin-Tools/downloads")

_**Source Code**_
Source code is available at [http://github.com/carleedolphinaura/Flash-Plugin-Tools](http://github.com/carleedolphinaura/Flash-Plugin-Tools)

and can be compiled using
```

gcc -o adobe_flash_installer *filename* `pkg-config --libs --cflags  gtk+-2.0`
```or

```

gcc -m32 -o adobe_flash_installer-ubuntu adobe_flash_installer-ubuntu.c `pkg-config --libs --cflags gtk+-2.0`

```for 32 bit
Bug reporting can be done through [https://launchpad.net/adobe-flash-plugin-tools](https://launchpad.net/adobe-flash-plugin-tools)

Hi- ijust started using Ubuntu for my netbook and my desktop, and i don't have much knowledge about working in this environment. I need to clean flash off my system and install a version that will work with firefox, specifically to run flash with games, youtube and especially with facebook/yoville. your post looks like it's going in the right direction. Where is the remove button? I clicked on 32-bit Ubuntu flash installer in your list, and my choice is to install using another application. What application should i choose?
sorry, but I am a noob in the linux environment. Any help would be appreciated. Thank you.

---

### Post by flatlinebb on 2010-04-22
Thank you so much for your utility!!!! I finally got flash-based videos working in Boxee.

---

### Post by sandyd on 2010-04-22
> **jord9308 said:**
> Hi- ijust started using Ubuntu for my netbook and my desktop, and i don't have much knowledge about working in this environment. I need to clean flash off my system and install a version that will work with firefox, specifically to run flash with games, youtube and especially with facebook/yoville. your post looks like it's going in the right direction. Where is the remove button? I clicked on 32-bit Ubuntu flash installer in your list, and my choice is to install using another application. What application should i choose?
sorry, but I am a noob in the linux environment. Any help would be appreciated. Thank you.
save the file to your desktop and double click on it.
if you get the "open with another application" dialog after you downloaded it, right click on the file, click properties, and there should be an option to make it executable.

ty.

---

### Post by creamyhorror on 2010-04-23
Thanks for the handy installer. I hope the new Flash Player RC2 will improve performance on Youtube, because it's been pretty terrible.

---

### Post by bark50 on 2010-05-02
Thanks!  Made my life easier.

---

### Post by hermitical on 2010-05-02
> **hermitical said:**
> looking good so far - thanks!

unfortunately it didn't last - oh well!

---

### Post by BULLIT22 on 2010-05-03
Thanks, this app worked awsome. Ran it in 10.04 it worked.

---

### Post by sandyd on 2010-05-05
updated to 10.1 flash RC2 :guitar::guitar:

---

### Post by bark50 on 2010-05-05
It worked fine for me 3 days ago, but now it doesn't.  I downloaded your newest version, clicked to allow execution as a program, but when I double-click on the icon, nothing happens.  :(  Did the recent kernel upgrade mess up something?

---

### Post by sandyd on 2010-05-05
~removed post to prevent confusion

---

### Post by bark50 on 2010-05-06
tom@tom-desktop:~$ wget -c [http://github.com/downloads/dolphinaura/Flash-Plugin-Tools/adobe_flash_installer-ubuntu](http://github.com/downloads/dolphinaura/Flash-Plugin-Tools/adobe_flash_installer-ubuntu)
--2010-05-05 22:25:09--  [http://github.com/downloads/dolphinaura/Flash-Plugin-Tools/adobe_flash_installer-ubuntu](http://github.com/downloads/dolphinaura/Flash-Plugin-Tools/adobe_flash_installer-ubuntu)
Resolving github.com... 207.97.227.239
Connecting to github.com|207.97.227.239|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://cloud.github.com/downloads/dolphinaura/Flash-Plugin-Tools/adobe_flash_installer-ubuntu](http://cloud.github.com/downloads/dolphinaura/Flash-Plugin-Tools/adobe_flash_installer-ubuntu) [following]
--2010-05-05 22:25:09--  [http://cloud.github.com/downloads/dolphinaura/Flash-Plugin-Tools/adobe_flash_installer-ubuntu](http://cloud.github.com/downloads/dolphinaura/Flash-Plugin-Tools/adobe_flash_installer-ubuntu)
Resolving cloud.github.com... 216.137.43.63, 216.137.43.32, 216.137.43.35, ...
Connecting to cloud.github.com|216.137.43.63|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 21686 (21K) [binary/octet-stream]
Saving to: `adobe_flash_installer-ubuntu'

100%[======================================>] 21,686      36.9K/s   in 0.6s    

2010-05-05 22:25:11 (36.9 KB/s) - `adobe_flash_installer-ubuntu' saved [21686/21686]

tom@tom-desktop:~$ chmod 777 adobe_flash_installer-ubuntu
tom@tom-desktop:~$ sh ./adobe_flash_installer-ubuntu

The utility installed into my home directory after running that.  It works!  Thanks!

---

### Post by sandyd on 2010-05-06
Updated to Adobe Flash 10.1 RC4 !!:guitar::guitar:

---

### Post by WinterRain on 2010-05-06
Can I ask why one needs to fool around with permissions and scripts to install 64bit flash? All you need to do is download the .tar.gz flash file to your desktop, right click **extract here**, then
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Done.  

It doesn't get any easier than that.

---

### Post by oldguysrule on 2010-05-09
Running 10.04 - 64bit
I have tried all of the above actions and still cannot get the adobe beta version to work. 
I downloaded carlee's installer and it removes the old flash version. When I click on the beta button it pauses then comes up with the 10.1 successfully installed notice but when I go to any site that requires flash they say I need to download adobe flash I eve went to the adobe site for a version check and  it is not recognized - just gives me the same 10.0 download options.
So I tried the wget script and it appears to work except the sh ./ last line returns this error message:
desktop:~$ sh ./adobe_flash_installer-ubuntu
./adobe_flash_installer-ubuntu: 1: Syntax error: "(" unexpected

I then used the remove button, downloaded the tar.gz and sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
Still no joy.
I confirmed that the libflashplayer.so is there.
So what am I doing wrong - :confused:- wouldn't be the first time (btw I did confirm the permissions on Carlee's flash installer and it does successfully re-install 10.0 every time:)

Thanks in advance for any help

---

### Post by jimbo12345 on 2010-05-09
Forgive my stupidity, but how do you run this installer?  I've downloaded it, but when i try clicking it, it comes up as if no program is associated with it.

---

### Post by bark50 on 2010-05-09
> **oldguysrule said:**
> Running 10.04 - 64bit
I have tried all of the above actions and still cannot get the adobe beta version to work. 
I downloaded carlee's installer and it removes the old flash version. When I click on the beta button it pauses then comes up with the 10.1 successfully installed notice but when I go to any site that requires flash they say I need to download adobe flash I eve went to the adobe site for a version check and  it is not recognized - just gives me the same 10.0 download options.
So I tried the wget script and it appears to work except the sh ./ last line returns this error message:
desktop:~$ sh ./adobe_flash_installer-ubuntu
./adobe_flash_installer-ubuntu: 1: Syntax error: "(" unexpected

I then used the remove button, downloaded the tar.gz and sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
Still no joy.
I confirmed that the libflashplayer.so is there.
So what am I doing wrong - :confused:- wouldn't be the first time (btw I did confirm the permissions on Carlee's flash installer and it does successfully re-install 10.0 every time:)

Thanks in advance for any help

Maybe try the "Install Flash (x64)" option on the program instead of the "install Flash Beta" option.  

The "Install Flash Beta" option on this utility doesn't install a version of flash that works for me either.  The "Install Flash (x64)" gives me a version that works with 90% of the sites I visit.  However, it does not work with hulu.com and for that site I have to use the Adobe flash plugin from Ubuntu's software center (which works well with Hulu but not much else).  It'll be nice when we get a flash version that "just works".

---

### Post by bark50 on 2010-05-09
> **jimbo12345 said:**
> Forgive my stupidity, but how do you run this installer?  I've downloaded it, but when i try clicking it, it comes up as if no program is associated with it.

Right-click on the blue diamond icon, and choose "Properties" from the context menu.  In the box that opens up, click on the "Permissions" tab.  Put a check mark where it says "Allow executing file as program".  Click "Close" and double-click on the blue diamond.

---

### Post by tekkidd on 2010-05-09
im running jaunty x64 on my laptop and all i have to do to install flash is 

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by oldguysrule on 2010-05-09
bark50
Thanks for the suggestion - I had already given that a try and it simply installs the 10.0.45 version again not the 10.1 release.

tekkid
thanks also but it installs the same 10.0.45 version as well.

:popcorn:

---

### Post by sandyd on 2010-05-09
> **oldguysrule said:**
> Running 10.04 - 64bit
I have tried all of the above actions and still cannot get the adobe beta version to work. 
I downloaded carlee's installer and it removes the old flash version. When I click on the beta button it pauses then comes up with the 10.1 successfully installed notice but when I go to any site that requires flash they say I need to download adobe flash I eve went to the adobe site for a version check and  it is not recognized - just gives me the same 10.0 download options.
So I tried the wget script and it appears to work except the sh ./ last line returns this error message:
desktop:~$ sh ./adobe_flash_installer-ubuntu
./adobe_flash_installer-ubuntu: 1: Syntax error: "(" unexpected

I then used the remove button, downloaded the tar.gz and sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
Still no joy.
I confirmed that the libflashplayer.so is there.
So what am I doing wrong - :confused:- wouldn't be the first time (btw I did confirm the permissions on Carlee's flash installer and it does successfully re-install 10.0 every time:)

Thanks in advance for any help
eh. my bad.
forgotta add nspluginwrapper strings.

[s]will b fixed in the next few minutes...[/s]

done.
new downloads are up.

---

### Post by ACGilbert on 2010-05-09
Carlee,
Thanks for your Flash installer.
My only problem following upgrading from Karmic to Lucid was the inability to view Flash videos from some sites -- others would work fine(?).
Using your installer, I was able to remove 10.0.45 and install 10.1.53.
Flash is working on sites it formerly wouldn't.
:)AC

---

### Post by mister_playboy on 2010-05-09
> **WinterRain said:**
> Can I ask why one needs to fool around with permissions and scripts to install 64bit flash? All you need to do is download the .tar.gz flash file to your desktop, right click **extract here**, then
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Done.  

It doesn't get any easier than that.

That worked for me on Ubuntu 9.04, but it simply won't work on Kubuntu 10.04.  It's apparently a problem with the 10.0.45 build of Flash.  I tried the version from the repos, the version from Adobe, and the "Install Flash (x64)" version from the program in this thread, and all I get is a blank spot where the video/animation ought to be.  The plugin is active, but it doesn't do anything.

The "Install Flash Beta" option in Carlee's program worked for me... I can finally use sites such as Megaupload, Youtube, etc.

Thank you so much for your installer! :KS

EDIT: Turns out it's only working in Opera.  Neither Firefox nor Konqueror can make use of it. :(

---

### Post by sandyd on 2010-05-09
this installer installs the 10.1 rc4 version of the plugin.

anything after rc2 has had some serious issues, and im now considering rolling back the download to rc2

---

### Post by oldguysrule on 2010-05-09
Okay so I tried the wget script again and still get the same syntax error. Downloaded and tried the installer again and still wouldn't install the 10.1 flash. 
Maybe I'm just doomed to old flash plug in limbo....:)

---

### Post by mister_playboy on 2010-05-09
The beta is actually 32bit, isn't it?  I started Firefox from the command line and saw: ```
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

``` Maybe Opera can use it because it's actually a 32bit program.

If I install the 64 bit 10.0.45.2 from Adobe in /usr/lib/mozilla/plugins, Firefox actually crashes on any Flash page, which I've never seen before.  If Firefox uses the 10.0.45.2 Flash that KPackageKit installs into /usr/lib/flashplugin-installer, it just shows a blank space.

Both of those plugins are called 10.0.45.2, but they are different sizes.  Adobe's is 9.1MiB and KPackageKit's is 9.8MiB.

Well, I can just stick with Opera for Flash content for now, I guess... :P

---

### Post by sandyd on 2010-05-09
> **mister_playboy said:**
> The beta is actually 32bit, isn't it?  I started Firefox from the command line and saw: ```
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

``` Maybe Opera can use it because it's actually a 32bit program.

If I install the 64 bit 10.0.45.2 from Adobe in /usr/lib/mozilla/plugins, Firefox actually crashes on any Flash page, which I've never seen before.  If Firefox uses the 10.0.45.2 Flash that KPackageKit installs into /usr/lib/flashplugin-installer, it just shows a blank space.

Both of those plugins are called 10.0.45.2, but they are different sizes.  Adobe's is 9.1MiB and KPackageKit's is 9.8MiB.

Well, I can just stick with Opera for Flash content for now, I guess... :P
hmm... at this moment. I don't think its my fault, but instead nspluginwrapper's fault.

nspluginwrapper should "wrap" the plugin, and place it in ~/.mozilla/plugins
32-bit wrapped plugins should run in 64bit programs

ill look into it.

meanwhile, can affected users please go to firefox, type in "about: plugins" and copy the output here?(and yes, theirs no space between the colon and plugins)

thanks.

---

### Post by mister_playboy on 2010-05-09
> **oldguysrule said:**
> Okay so I tried the wget script again and still get the same syntax error. Downloaded and tried the installer again and still wouldn't install the 10.1 flash. 
Maybe I'm just doomed to old flash plug in limbo....:)

You can try getting the 10.1 RC4 directly from Adobe:

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc4_linux_050510.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc4_linux_050510.tar.gz)

Extract it into /usr/lib/mozilla/plugins and see what happens.

---

### Post by sandyd on 2010-05-09
alright.
I finally pinpointed it. RC4, RC3, RC2 don't seem to work. They all give black screens, and load sporadically when run through nspluginwrapper.

[s]so, for the time being (until I wake up and fix it), don't run the flash installer to install 10.1. (I mean for 64-bit users, 32-bit users should not be affected)

instead,
```

sudo apt-get remove --purge flashplugin-nonfree flashplugin-installer
sudo rm /usr/lib/mozilla/plugins/libflash*
sudo rm /usr/lib/mozilla/plugins/flashplugin*
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc_linux_040510.tar.gz
tar xvfz flashplayer10_1_rc_linux_040510.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so

```rm  flashplayer10_1_rc_linux_040510.tar.gz[/s]

I stayed up a bit later so you guys could re-test it.

binaries updated now, and all 10.01 beta flash issues should be fixed by this commit: [http://is.gd/c22sU](http://is.gd/c22sU)

---

### Post by nicoulaj on 2010-05-10
Hi all, I had not heard about carlee's work and in the meanwhile I had started my own script too, and it seems to work with last beta version on 64 bits Ubuntu.
[http://github.com/nicoulaj/flash-utils](http://github.com/nicoulaj/flash-utils)

To try it, install the package:
```
sudo add-apt-repository ppa:flash-utils/ppa
sudo apt-get update
sudo apt-get install flash-utils
```

And then run:
```
sudo flash-apt-get install plugin-beta
```

Please fill issues in the project if it does not work for you !

---

### Post by sandyd on 2010-05-10
> **nicoulaj said:**
> Hi all, I had not heard about carlee's work and in the meanwhile I had started my own script too, and it seems to work with last beta version on 64 bits Ubuntu.
[http://github.com/nicoulaj/flash-utils](http://github.com/nicoulaj/flash-utils)

To try it, install the package:
```
sudo add-apt-repository ppa:julien-nicoulaud/flash-utils
sudo apt-get update
sudo apt-get install flash-utils
```

And then run:
```
sudo flash-apt-get install plugin-beta
```

Please fill issues in the project if it does not work for you !

carlee=dolphinaura

---

### Post by oldguysrule on 2010-05-10
Carlee 
Thanks for all your help. I tried your latest scripts and still no joy (syntax error again - sorry thought I'd saved them but it dissapeared into the ether). 
I was successful using nicoulaj's scripts.
So thank you both it was fun trying new things and it ended positively.
Keep up the good work.
Ogr

---

### Post by oldguysrule on 2010-05-10
Since my last post I installed Lucid Lynx on a friends laptop and ran the latest script to see if I got the same error message:
bash: syntax error near unexpected token `"rm flashplayer*tar.gz"'

Don't know if that helps - also would it make a difference being a clean install over an upgrade from 9.10.

---

### Post by Exüberance on 2010-05-14
**Thank You**

This installer is extremely helpful. Just switched over from Ubuntu 9.10 to 10.4 and I couldn't remember how to fix flashplayer. This worked perfectly. BOOKMARK'D!

---

### Post by sbelz79 on 2010-05-15
OK so I'm still kinda green.  What do I do with the file "adobe_flash_intaller-ubuntu-64bit" once I've downloaded it?  I'm running Ubuntu 10.04 64-bit.

---

### Post by bark50 on 2010-05-15
> **sbelz79 said:**
> OK so I'm still kinda green.  What do I do with the file "adobe_flash_intaller-ubuntu-64bit" once I've downloaded it?  I'm running Ubuntu 10.04 64-bit.

Sbelz:  The first thing you do is right-click on the installer and chose "Properties" from the menu.  Then in the box that opens, click on the "Permissions" tab.  Next put a check where it says, "Allow executing file as program".  Close the box and double-click on the installer to get the options to remove flash and install flash.  Sorry, but at this point I can't be any more help since I went back to 32 bit, but maybe you can figure the rest out on your own -- or ask for more help here for someone else's response.

---

### Post by 12_String on 2010-05-15
So, what is it with the "removal" button that we should click first? I do not see one.

---

### Post by sandyd on 2010-05-15
> **12_String said:**
> So, what is it with the "removal" button that we should click first? I do not see one.

once you run the app, youll see a "remove flash" button in the window that appears.

---

### Post by Greblok on 2010-05-18
Thank you carlee! 
Finally, flash works like a charm. :)

---

### Post by Danmalone72 on 2010-05-19
Great work , didn't have any problems with this - it was straightforward and flawless.

---

### Post by GentleInferno on 2010-05-19
I second that. straightforward and flawless. thanks a ton.:KS

---

### Post by sandyd on 2010-05-22
* CHanged name of program
* Added Adobe AIR support

---

### Post by Eskorpio on 2010-05-24
Adobe Flash 10.1 RC5 is out: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by sandyd on 2010-05-24
> **Eskorpio said:**
> Adobe Flash 10.1 RC5 is out: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
[http://github.com/dolphinaura/Adobe-Tools/commit/cd1b4256a318410b0d8659de0c244a2d90414f36](http://github.com/dolphinaura/Adobe-Tools/commit/cd1b4256a318410b0d8659de0c244a2d90414f36)

---

### Post by floydsp on 2010-05-25
Thanks Carlee worked first time for me ubuntu lucid 64 bit

floyd

---

### Post by Danno2468 on 2010-05-29
Thank you it work great.

---

### Post by lovinglinux on 2010-05-30
Carlee, I have noticed that some users trying my flash installation extension couldn't make it work because Firefox was using a Windows version of flash installed using Wine.

I'm not sure how they managed to make Firefox use it, because I couldn't reproduce the problem by simply installing flash for Windows. But you might want to consider adding the following to your tool, if it doesn't take care of that already:

```
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
```

---

### Post by sandyd on 2010-05-31
> **lovinglinux said:**
> Carlee, I have noticed that some users trying my flash installation extension couldn't make it work because Firefox was using a Windows version of flash installed using Wine.

I'm not sure how they managed to make Firefox use it, because I couldn't reproduce the problem by simply installing flash for Windows. But you might want to consider adding the following to your tool, if it doesn't take care of that already:

```
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
```
is there an "a" at the end of Macromed, or is it just like that?

---

### Post by sandyd on 2010-05-31
> **lovinglinux said:**
> Carlee, I have noticed that some users trying my flash installation extension couldn't make it work because Firefox was using a Windows version of flash installed using Wine.

I'm not sure how they managed to make Firefox use it, because I couldn't reproduce the problem by simply installing flash for Windows. But you might want to consider adding the following to your tool, if it doesn't take care of that already:

```
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
```
in other words,
[http://github.com/dolphinaura/Adobe-Tools/commit/2190a0b59d7d1c305c482275237fdc24db5ad497](http://github.com/dolphinaura/Adobe-Tools/commit/2190a0b59d7d1c305c482275237fdc24db5ad497)

is what your looking for I believe ;)

---

### Post by lovinglinux on 2010-05-31
> **carlee said:**
> is there an "a" at the end of Macromed, or is it just like that?

I admit is weird, but when I install Windows flash here, the created folder is Macromed not Macromedia.

---

### Post by sandyd on 2010-05-31
> **lovinglinux said:**
> I admit is weird, but when I install Windows flash here, the created folder is Macromed not Macromedia.
oops...
**quickly rolls back bad git commit...**

---

### Post by sandyd on 2010-06-06
hmm. looks like I fixed all the bugs so far
no complaints! :D

---

### Post by browndl30 on 2010-06-09
Great tool. Thank You

---

### Post by volodymyr on 2010-06-26
I tried these tools, but they did not helped me. I run Kubuntu 10.04 x64. I have sound with Amarok, but not in flash. I was able to solve my problem with the following solution: [http://www.shcherbyna.com/?p=866](http://www.shcherbyna.com/?p=866)

---

### Post by Jasman on 2010-07-08
I made the ubuntu-64bit file an executable, then the only way I can get it to do anything is at the command line, sudo ./adobe_tools-ubuntu-64bit, and that results in a segmentation fault error. Any ideas? Thanks.

---

### Post by sandyd on 2010-07-08
> **volodymyr said:**
> I tried these tools, but they did not helped me. I run Kubuntu 10.04 x64. I have sound with Amarok, but not in flash. I was able to solve my problem with the following solution: [http://www.shcherbyna.com/?p=866](http://www.shcherbyna.com/?p=866)

thats not really a problem w/flash. its more of a "developers of apps cant decide wether to use the sound card directly(amarok), or through pulseaudio/alsa". You see, amarok accesses the sound card directly, which causes other apps (in this case flash) not to be able to use the card through alsa. however, kde has pulseaudio support built in. KDE DEVELOPERS, MAKE A SOLID DECISION PLEASE. If you going to build Kde w/ pulseaudio support, then include pulse by default, not alsa....

---

### Post by RageLtMan on 2010-07-09
> **Jasman said:**
> I made the ubuntu-64bit file an executable, then the only way I can get it to do anything is at the command line, sudo ./adobe_tools-ubuntu-64bit, and that results in a segmentation fault error. Any ideas? Thanks.


same boat, except it ran the first time without a seg fault, installed flash, which doesnt work correctly, and now i cant get the bloody tool to run again in order to remove it. I run 10.04 x64 with Trinity KDE3.

---

### Post by sandyd on 2010-07-09
meh. blame it on the guys who just pushed some updates to the repos. Ill compile it in gentoo, and hopefully, ubuntu will always have a lower library version than it. and the fact that the x64 plugin not working is no suprise -since adobe isnt maintaining it anymore

---

### Post by RageLtMan on 2010-07-09
Thank you ma'am, any chance you could post/mail the source? I can compile it on a build VM i have @ the data center and deb package it. BTW, define "not supporting it anymore??" Shouldnt they have plenty of free devs now that apple has told them they're the red headed stepchild of online video?

As for versioning in repositories - there's always the off chance some PPA will have something with a messed up version number, we could just as well package it with a name nobody else is likely to use - without installing another package with --force-overwrite it should just conflict, fail, and leave the (hopefully) working rev on the system.

---

### Post by FuturePilot on 2010-07-09
> **carlee said:**
> then include pulse by default, not alsa....

PulseAudio does not replace ALSA.

---

### Post by sandyd on 2010-07-09
> **RageLtMan said:**
> Thank you ma'am, any chance you could post/mail the source? I can compile it on a build VM i have @ the data center and deb package it. BTW, define "not supporting it anymore??" Shouldnt they have plenty of free devs now that apple has told them they're the red headed stepchild of online video?
** adobe has stopped development of the x64 version of flash for now, and they havent given us anything else... yet. although the funny thing is that nspluginwrapper works flawlessly on gentoo...**
As for versioning in repositories - there's always the off chance some PPA will have something with a messed up version number, we could just as well package it with a name nobody else is likely to use - without installing another package with --force-overwrite it should just conflict, fail, and leave the (hopefully) working rev on the system.the program was origionally compiled against the dev version of lucid, back when it was still beta, which means something must have been updated or changed. the src code is avalible on a link (in the main post)

---

### Post by RageLtMan on 2010-07-13
> **carlee said:**
> the program was origionally compiled against the dev version of lucid, back when it was still beta, which means something must have been updated or changed. the src code is avalible on a link (in the main post)


I pulled the sources and recompiled on the build VM. No dice, still being a PITA. Interestingly enough though it doesnt seg-fault me on that machine, but its not running X presently. Should probably set up NX on it and test there, may well be a dependency problem.

Any chance you happen to have a list of the dependencies for this thing? Maybe i can figure out what went south - it ran on my machine prior, just decided to not run after it installed the bloody plugin.

---

### Post by sandyd on 2010-07-14
> **RageLtMan said:**
> I pulled the sources and recompiled on the build VM. No dice, still being a PITA. Interestingly enough though it doesnt seg-fault me on that machine, but its not running X presently. Should probably set up NX on it and test there, may well be a dependency problem.

Any chance you happen to have a list of the dependencies for this thing? Maybe i can figure out what went south - it ran on my machine prior, just decided to not run after it installed the bloody plugin.

the libgtk libraries (including dev), the c libraries, and nothing else. segfault fixed, but I havent updated the binaries yet. (the git tree is though)

---

### Post by RageLtMan on 2010-07-19
Looks like there's a competing approach called flash-aid, same type of deal - automates the CLI installation of a proper flash plugin (due to no support for x64 they nspluginwrapper-ed the current 32bit ver). Interestingly enough this works with amazon's VOD, which has always been a massive PITA for me on linux.  These types of projects should be put in the main canonical repos - save a ton of trouble for users trying to do the most basic of things. Felt like a damned iphone user for a while there (i'm an EVO4g owner). Adobe needs to get their act together.  I'll take a look at whats in the git tree when i have a bit of time, this week isn't looking too hot for that with a new SAN deployment, exch migration, and a pen test proposal for a client.

---

### Post by sandyd on 2010-07-19
> **RageLtMan said:**
> Looks like there's a competing approach called flash-aid, same type of deal - automates the CLI installation of a proper flash plugin (due to no support for x64 they nspluginwrapper-ed the current 32bit ver). Interestingly enough this works with amazon's VOD, which has always been a massive PITA for me on linux.  These types of projects should be put in the main canonical repos - save a ton of trouble for users trying to do the most basic of things. Felt like a damned iphone user for a while there (i'm an EVO4g owner). Adobe needs to get their act together.  I'll take a look at whats in the git tree when i have a bit of time, this week isn't looking too hot for that with a new SAN deployment, exch migration, and a pen test proposal for a client.
yeah, I actually know the developer of that plugin. hes known as lovinglinux here on the forums :).

He also contributed to this plugin :)

and no rush. im officially sticking my feet on the table until adobe gets a new beta flash out, so the git tree ain't goin anywhere.

---

### Post by lovinglinux on 2010-07-19
> **carlee said:**
> yeah, I actually know the developer of that plugin. hes known as lovinglinux here on the forums :).

He also contributed to this plugin :)

and no rush. im officially sticking my feet on the table until adobe gets a new beta flash out, so the git tree ain't goin anywhere.

Yeah, we help each other sometimes. ;)

BTW, Adobe Tools is more feature reach than my extension, which only removes some common flash files and alternative plugins, then install the official version from the repositories. It had an option to download the 64bit version, but I decided to remove it completely after latest Adobe flash fiasco. 

Is a different approach indeed. I do as an extension because is easier for me, since I develop other Firefox extensions as well. Plus I can distribute updates easily.

---

### Post by lovinglinux on 2010-07-20
> **carlee said:**
> and no rush. im officially sticking my feet on the table until adobe gets a new beta flash out, so the git tree ain't goin anywhere.

I just saw the notice on the first post. I hope you get back soon.

---

### Post by sandyd on 2010-07-20
> **lovinglinux said:**
> I just saw the notice on the first post. I  hope you get back soon.

Revised Edition up :)

don't use github, use [http://code.google.com/p/adobe-flash-tools/source/checkout](http://code.google.com/p/adobe-flash-tools/source/checkout)

I still have to work on the adobe air thingy, as it seems that the wget zenity progress bar downloads the file, but it vanishes shortly afterwords O_o

---

### Post by lovinglinux on 2010-07-20
> **carlee said:**
> Revised Edition up :)

don't use github, use [http://code.google.com/p/adobe-flash-tools/source/checkout](http://code.google.com/p/adobe-flash-tools/source/checkout)

I still have to work on the adobe air thingy, as it seems that the wget zenity progress bar downloads the file, but it vanishes shortly afterwords O_o


Cool. What made you change from  github to Google Code? I have been using Google Code for all my extensions and I like it. I had a SourceForge account before, but Google code is a lot cleaner.

---

### Post by sandyd on 2010-07-21
> **lovinglinux said:**
> Cool. What made you change from  github to Google Code? I have been using Google Code for all my extensions and I like it. I had a SourceForge account before, but Google code is a lot cleaner.

I didnt really like using git. github also had some major problems for my project.

---

### Post by peace.gangsta on 2010-07-23
I had been struggling to get flash plugin to work.This thread did the magic.
Thanks a lot.

---

### Post by A4orce84 on 2010-08-21
Not sure if this really fits here, but it looks like I'm having issues with specific flash players lately.

Youtube, and other flash websites I visit work correctly. However the following site:
[http://thatguywiththeglasses.com/videolinks/thatguywiththeglasses/nostalgia-critic/27517-the-flintstones-movie](http://thatguywiththeglasses.com/videolinks/thatguywiththeglasses/nostalgia-critic/27517-the-flintstones-movie)


Clicking their flash player (and similar players) to make it full screen, only blows up a freeze frame and the video doesn't actually move / play. The audio works, and you can hear the video playing, but nothing plays per say.


Can anyone else reproduce this issue?

Thanks.


--Asif

---

### Post by lovinglinux on 2010-08-21
> **A4orce84 said:**
> Can anyone else reproduce this issue?

Nope.

---

### Post by sandyd on 2010-08-23
Ive uploaded new binaries, because some people have been unable to see the progress bar majiggy.

test them out here (yes, I need testers. and testers who will be able to restore their computers back to normal if something happens...)
[http://adobe-flash-tools.googlecode.com/svn/branches/unstable/binaries/](http://adobe-flash-tools.googlecode.com/svn/branches/unstable/binaries/)

---

### Post by sandyd on 2010-08-24
bump

---

### Post by sandyd on 2010-08-25
bump.

---

### Post by Zorgoth on 2010-08-25
If all I ever did was install the flash from the Ubuntu repositories is that insecure?

And also unless they've fixed it 64-bit flash is *extremely* buggy in Ubuntu regarding receiving mouse clicks (making some movies and virtually all flash games unplayable) unless you use "export GDK_NATIVE_WINDOWS=1" (which can be put in some file or other related to npviewer).

---

### Post by sandyd on 2010-08-25
> **Zorgoth said:**
> If all I ever did was install the flash from the Ubuntu repositories is that insecure?

And also unless they've fixed it 64-bit flash is *extremely* buggy in Ubuntu regarding receiving mouse clicks (making some movies and virtually all flash games unplayable) unless you use "export GDK_NATIVE_WINDOWS=1" (which can be put in some file or other related to npviewer).

the version in the repos is automatically updated to the newest version

---

### Post by Zorgoth on 2010-08-25
btw I looked at the source code.  That's sure some advanced C you're using :lolflag:

---

### Post by FatherDale on 2010-09-14
> **sandyd said:**
> This utility aids in the installation/removal of flash (32bit/64bit) and the installation of Adobe AIR.


Thank you so much. This worked when all the manual apt-getting I've been doing wouldn't. It's good to have Firefox showing video again!

---

### Post by snodrion on 2010-09-15
in my pc those binaries doesnt work.!!!help me.i have tried everything from this post.from the first page until the last one!:P

---

### Post by sandyd on 2010-09-16
> **sandyd said:**
> This utility aids in the installation/removal of flash (32bit/64bit) and the installation of Adobe AIR.

Currently, it

[LIST]
[*]Installs / Removes Adobe Flash Player
[*]Installs Adobe AIR (still workin on this)
[/LIST]
[_**[Download]**_]("http://code.google.com/p/adobe-flash-tools/downloads/list")  

[B]Files
[/B]
[LIST]
[*][Adobe Tools for Ubuntu (32-bit)]("http://daura.tk/IAqWcv")
[*][Adobe Tools for Ubuntu (64-bit)]("http://daura.tk/FQkYZt")
[*][Adobe Tools for Kubuntu (32-bit)]("http://daura.tk/vcjOlu")
[*][Adobe Tools for Kubuntu (64-bit)]("http://daura.tk/vEuCsr")
[/LIST]
 [B]Downloads
[/B]The number of downloads is recorded each time I upload new files, cause it resets when I do that.
Currently: 5436

[B]How To Run
[/B]
[LIST]
[*]Right click on the file you downloaded
[*]Select "Properties"
[*]Click on "Permissions"
[*]check the "Execute" box
[/LIST]
[[More Info / Source Code]]("http://dolphinaura.com/programming/adobe-tools/adobe-flash-plugin-installer-uninstaller-linux")
Bug reporting can be done through [https://launchpad.net/adobe-flash-plugin-tools](https://launchpad.net/adobe-flash-plugin-tools)

And if you like it, please click "Like" at [http://bit.ly/9jzUcr](http://bit.ly/9jzUcr)
new binaries uploaded with new flash.
have fun...

---

### Post by razorbuzz on 2010-09-21
Just downloaded and ran for 64bit "Square" Flash...failed.

The script it downloads has ```
wget -c 'http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p1_64bit_linux_091510.tar.gz'
tar xvfz libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz > /dev/null
```

Shouldn't it be ```
tar xvfz flashplayer_square_p1_64bit_linux_091510.tar.gz
```??

Went ahead and changed it, and works fine... you're still trying to unTar the previous version of 64bit that your script downloaded, not the current one it downloads.

Also, you're removing the (same) old version that didn't get downloaded.  ```
 rm libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
 should be 
rm flashplayer_square_p1_64bit_linux_091510.tar.gz
```

-Raze

---

### Post by sandyd on 2010-09-22
> **razorbuzz said:**
> Just downloaded and ran for 64bit "Square" Flash...failed.

The script it downloads has ```
wget -c 'http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p1_64bit_linux_091510.tar.gz'
tar xvfz libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz > /dev/null
```Shouldn't it be ```
tar xvfz flashplayer_square_p1_64bit_linux_091510.tar.gz
```??

Went ahead and changed it, and works fine... you're still trying to unTar the previous version of 64bit that your script downloaded, not the current one it downloads.

Also, you're removing the (same) old version that didn't get downloaded.  ```
 rm libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
 should be 
rm flashplayer_square_p1_64bit_linux_091510.tar.gz
```-Raze
**cries**
thanks for noticing, must have been a broken commit cause it synced right back up after running svn commit...

---

### Post by nilarimogard on 2010-09-24
The Ubuntu 32 bit version install doesn't work:


```
--2010-09-24 17:53:47--  http://adobe-flash-tools.googlecode.com/svn/branches/unstable/scripts/adobe_flash_beta-ubuntu.sh
Resolving adobe-flash-tools.googlecode.com... 209.85.135.82
Connecting to adobe-flash-tools.googlecode.com|209.85.135.82|:80... connected.
HTTP request sent, awaiting response... 200 OK

    The file is already fully retrieved; nothing to do.

sh: konsole: not found
```

---

### Post by sandyd on 2010-09-24
> **nilarimogard said:**
> The Ubuntu 32 bit version install doesn't work:


```
--2010-09-24 17:53:47--  http://adobe-flash-tools.googlecode.com/svn/branches/unstable/scripts/adobe_flash_beta-ubuntu.sh
Resolving adobe-flash-tools.googlecode.com... 209.85.135.82
Connecting to adobe-flash-tools.googlecode.com|209.85.135.82|:80... connected.
HTTP request sent, awaiting response... 200 OK

    The file is already fully retrieved; nothing to do.

sh: konsole: not found
```
fixed

---

### Post by nilarimogard on 2010-09-25
> **sandyd said:**
> fixed

It has not been fixed. Note that it only occurs for the Flash beta!

---

### Post by sandyd on 2010-09-25
> **nilarimogard said:**
> It has not been fixed. Note that it only occurs for the Flash beta!
did you download the installer again?

---

### Post by nilarimogard on 2010-09-25
> **sandyd said:**
> did you download the installer again?

Obviously :)

And I've also tried the latest one (I see you've uploaded yet another new version: [http://code.google.com/p/adobe-flash-tools/downloads/list](http://code.google.com/p/adobe-flash-tools/downloads/list) ) and this one doesn't work either with the Beta version of Flash - same error.

---

### Post by drdos2006 on 2010-09-25
And then there is this..........

[http://www.adobe.com/support/security/advisories/apsa10-03.html](http://www.adobe.com/support/security/advisories/apsa10-03.html)

regards

---

### Post by drdos2006 on 2010-09-25
Here is what worked for me...
```

Installing Adobe FlashPlayer 10 in Ubuntu 9.10 64 bit
Close the browser
Downloaded  latest libflashplayer .tar.gz from here
http://labs.adobe.com/downloads/flashplayer10.html

Extracted into /home/temp by double-click on downloaded file.
Copied /home/temp/libflashplayer.so to /usr/lib/mozilla/plugins/  in terminal with
sudo cp /home/temp/libflashplayer.so /usr/lib/mozilla/plugins/

Went to /usr/lib/mozilla/plugins/ via Terminal with 
cd /usr/lib/mozilla/plugins/

Executed these commands from /usr/lib/mozilla/plugins/ via Terminal.
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

Run Firefox
Check plugins with Firefox, about:plugins

```

Sorry sandyd.
Your script did not work for my installation....

regards

---

### Post by sandyd on 2010-09-25
> **nilarimogard said:**
> Obviously :)

And I've also tried the latest one (I see you've uploaded yet another new version: [http://code.google.com/p/adobe-flash-tools/downloads/list](http://code.google.com/p/adobe-flash-tools/downloads/list) ) and this one doesn't work either with the Beta version of Flash - same error.
should be working because there is no konsole in the command, i switched it to gnome-terminal
-> [http://code.google.com/p/adobe-flash-tools/source/diff?spec=svn29&r=28&format=side&path=/branches/stable/adobe_tools-ubuntu.c&old_path=/branches/stable/adobe_tools-ubuntu.c&old=26](http://code.google.com/p/adobe-flash-tools/source/diff?spec=svn29&r=28&format=side&path=/branches/stable/adobe_tools-ubuntu.c&old_path=/branches/stable/adobe_tools-ubuntu.c&old=26)

---

### Post by nilarimogard on 2010-09-26
Well it doesn't :)

Try it for yourself (in virtualbox if you can't on your desktop).

Btw see this:

```
void install_32bit(GtkWidget *widget, gpointer adobe)
{
  system("wget -c http://adobe-flash-tools.googlecode.com/svn/branches/unstable/scripts/adobe_flash_x86-ubuntu.sh");
  system("chmod 777 adobe_flash_x86-ubuntu.sh");
  system("gnome-terminal -e /bin/bash $PWD/adobe_flash_x86-ubuntu.sh");
  system("zenity --info --text 'Flash Plugin Installed Successfully'");
}
void install_beta(GtkWidget *widget, gpointer adobe)
{
{
  system("wget -c http://adobe-flash-tools.googlecode.com/svn/branches/unstable/scripts/adobe_flash_beta-ubuntu.sh");
  system("chmod 777 adobe_flash_beta-ubuntu.sh");
  system("gnome-terminal -e /bin/bash $PWD/adobe_flash_beta-ubuntu.sh");
  system("zenity --info --text 'Flash Plugin Installed Successfully'");
}
}
```

What's up with the double "{" for the Flash beta install?

---

### Post by nilarimogard on 2010-09-26
Yes, the double "{" for the beta Flash was the issue. I've just compiled it without the double "{" and it worked. It seems it interprets "{" as a command and tries to run in in the terminal.

---

### Post by sandyd on 2010-09-26
> **nilarimogard said:**
> Yes, the double "{" for the beta Flash was the issue. I've just compiled it without the double "{" and it worked. It seems it interprets "{" as a command and tries to run in in the terminal.
yeah, but that wasn't the same problem you had earlier, which you said you had. I was looking at where it said I was mixing up konsole with gnome-terminal

---

### Post by nilarimogard on 2010-09-26
> **sandyd said:**
> yeah, but that wasn't the same problem you had earlier, which you said you had. I was looking at where it said I was mixing up konsole with gnome-terminal

That was the problem. The gnome terminal probably thinks "{" is a command for Konsole ... which is not installed. I've noticed this kind of errors a few times...

---

### Post by nilarimogard on 2010-09-26
By the way, I see you fixed this in the source, but the updated file (uploaded 18 minutes ago) in the downloads section still has this bug.

You should really test these before making them public... I wanted to post this on WebUpd8 a few times and each time there's a bug and I cannot post it.

---

### Post by sandyd on 2010-09-26
> **nilarimogard said:**
> By the way, I see you fixed this in the source, but the updated file (uploaded 18 minutes ago) in the downloads section still has this bug.

You should really test these before making them public...
I did, except for the beta since I don't have 32 bit ubuntu.

---

### Post by nilarimogard on 2010-09-26
> **sandyd said:**
> I did, except for the beta since I don't have 32 bit ubuntu.

It's not that big of a deal as it doesn't break anything but it just doesn't work. 

Waiting for the fixed version :D

---

### Post by nilarimogard on 2010-09-26
Btw I think I know why you can't upload the fixed version on Google Code download section. When you upload a new version but with the exact file name as before, the old file is used - so you cannot actually replace the files.

You must rename them each time you upload a new version. You can use something like: "adobe_tools-ubuntu-v3.5" or whatever version number each has...

---

### Post by sandyd on 2010-09-26
> **nilarimogard said:**
> Btw I think I know why you can't upload the fixed version on Google Code download section. When you upload a new version but with the exact file name as before, the old file is used - so you cannot actually replace the files.

You must rename them each time you upload a new version. You can use something like: "adobe_tools-ubuntu-v3.5" or whatever version number each has...
you can delete the old file first, which I did...

---

### Post by nilarimogard on 2010-09-26
I give up :)

---

### Post by grey1beard on 2010-10-15
Hi Sandy,
As an aged newbie, I've been having great difficulty in getting the flash player to install/run on my amd64 bit machine.
I've downloaded the 64 bit adobe from the link on your first posting, run through the following instructions, double clicked on the file on the desktop, and up pops your Adobe tools window.:)

I then click on the "Install Flash(x64)" button, and I'm then given a terminal window, but I've no idea what to do next.
If I close it, an info window says that the flash plugin has been installed successfully.
Unfortunately I still can't open anything in Firefox that requires flash player.
I suspect I've left out a set of actions to be taken in the terminal, but as a nearly brain dead newbie, I've no way of guessing what.
Regards
John

---

### Post by sandyd on 2010-10-15
> **grey1beard said:**
> Hi Sandy,
As an aged newbie, I've been having great difficulty in getting the flash player to install/run on my amd64 bit machine.
I've downloaded the 64 bit adobe from the link on your first posting, run through the following instructions, double clicked on the file on the desktop, and up pops your Adobe tools window.:)

I then click on the "Install Flash(x64)" button, and I'm then given a terminal window, but I've no idea what to do next.
If I close it, an info window says that the flash plugin has been installed successfully.
Unfortunately I still can't open anything in Firefox that requires flash player.
I suspect I've left out a set of actions to be taken in the terminal, but as a nearly brain dead newbie, I've no way of guessing what.
Regards
John
[http://code.google.com/p/adobe-flash-tools/source/detail?r=33](http://code.google.com/p/adobe-flash-tools/source/detail?r=33)

try again.

---

### Post by grey1beard on 2010-10-18
Thanks Sandy. I had managed to load it by going another route.
Regards
John

---

