---
title: "No Flash,..is there a real solution?"
date: 2012-04-26
forum: The Cafe
---

### Post by ptolemy9 on 2012-04-26
I'll cut to the chase. I have no flash after update of 10.04. I have seen this problem all over the net. I have seen this happen to three different computers. It all seems to be the last update.  (Maybe we should not update?) I have seen and tried numerous "solutions"  that DO NOT WORK. Is there a real solution to this problem?

PS Sadly Ubuntu seems to be going the way of Mandrake right before it became Mandriva.

---

### Post by QIII on 2012-04-26
If one of the things that was updated was Firefox (Mozilla has dropped support for 3.x and 11.x was ported to the 10.04 repo), then you may also have an old version of Flash.

Do you use Firefox?

Flash works just fine for me with the latest version of FF and the latest Flash.

---

### Post by Version Dependency on 2012-04-26
> **ptolemy9 said:**
> PS Sadly Ubuntu seems to be going the way of Mandrake right before it became Mandriva.

Yea...Ubuntu.com has been going down all morning as their servers are melting from the demand for 12.04.  Yea...they are clearly dying like Mandriva.  What an outstanding first post to these forums!

As for a recent Flash upgrade not working on your computer, these things do happen (more frequently it seems these days) but hey, Ubuntu is not the maker of Flash.  But why not try going back to the previous version of Flash that worked.  Fire up Synaptic and search for your previous version.

---

### Post by TBABill on 2012-04-26
We need to know which solutions you tried that did not work in order to not waste your time with suggestions. Simplest way is to go into the repo and reinstall the flash plugin via terminal, Synaptic or Software Center.

---

### Post by neu5eeCh on 2012-04-26
Have you tried [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")?

Also, what's your Mandrake comparison based on? I'm not seeing it.

---

### Post by ptolemy9 on 2012-04-26
...Yes, I have tried via the terminal, software center, Flash-aid, etc. Nothing appears to work. Any other bones to throw me?

PS The Mandrake comment>  It seemed that after Mandrake 9 and 10 that everything started to simply not work anymore, just very buggy. It was downhill from there.

---

### Post by CharlesA on 2012-04-26
> **ptolemy9 said:**
> ...Yes, I have tried via the terminal, software center, Flash-aid, etc. Nothing appears to work. Any other bones to throw me?

Yet you give us no info for us to help you.

You said you were running 10.04 and updated it, to what? Normal upgrade or upgrade to 12.04?

---

### Post by ptolemy9 on 2012-04-26
Update (not upgrade,) as in Update Manager, running 10.04 LTS

---

### Post by MasterNetra on 2012-04-26
> **ptolemy9 said:**
> Update (not upgrade,) as in Update Manager, running 10.04 LTS

Could back up and try uprading to 12.04, if you don't like Unity you could always go with KDE, Cinnamon, Gnome, Gnome Classic, or whatever. On 12.04 (been on sense beta 2) and using Gnome Classic and aside from having to alt+right click to get panel properties and System Menu being shoved into system tools, it pretty much handles like Gnome 2.

---

### Post by Gremlinzzz on 2012-04-26
Firefox update was a upgrade to Firefox 12.
the plugin needs to be reinstalled

just checked Java plugin needs to be reinstalled too

Did them no problem

---

### Post by Johnny3 on 2012-04-26
Ubuntu 12.04 and I am still on Firefox 11. But I have been using Nightly too and no problems with flash. Try uninstalling flash in Software Center then completely in SPM and reinstalling. 
Good Luch and God Bless Johnny3 65+++

---

### Post by Gremlinzzz on 2012-04-26
This is the update i received today:popcorn:

---

### Post by Johnny3 on 2012-04-26
> **Gremlinzzz said:**
> This is the update i received today:popcorn:

Maybe Xubuntu got it befor Ubuntu does?
Thanks Johnny3 65+++

---

### Post by mips on 2012-04-26
> **Gremlinzzz said:**
> This is the update i received today:popcorn:
I could live with that ;)

---

### Post by QIII on 2012-04-26
> **Gremlinzzz said:**
> This is the update i received today:popcorn:

Gotta love it when you get an updated Angelina Jolie.  Wife gets a little bent out of shape, though.

---

### Post by BigCityCat on 2012-04-26
I would assume when it becomes neccessary that someone will find a way to system link Firefox to Chromes version of Flash on Linux. Not sure if possible but just a guess.

---

### Post by samalex on 2012-04-26
My laptop is still 10.04 LTS, and one of the last big updates for me killed Firefox all together, it opens but does nothing.  I've been using Safari since, which I like as well, so no biggie.  I haven't spent any time researching the FF problem though since I planned on reinstalling with 12.04 this weekend anyway.

---

### Post by mamamia88 on 2012-04-26
One of the main reasons I love chrome built in flash and pdf support two fewer things to worry about on a fresh install

---

### Post by samalex on 2012-04-26
> **mamamia88 said:**
> One of the main reasons I love chrome built in flash and pdf support two fewer things to worry about on a fresh install

I agree.  Though browser plugins are far better than they were 5-10 years ago they're still a PITA.  Having this type of support built in is a huge plus.

---

### Post by ptolemy9 on 2012-04-26
UPDATE:   Tried as I may, I could not get Flash to work on FireFox 12  / Ubuntu 10.04 LTS.   I finally gave up and installed Chrome. Flash works on Chrome. (Unfortunately I hate Chrome. but what can you do?)  So, what's the issue? Has FireFox been snubbed, left in the dark by....______?

---

### Post by mamamia88 on 2012-04-26
> **ptolemy9 said:**
> UPDATE:   Tried as I may, I could not get Flash to work on FireFox 12  / Ubuntu 10.04 LTS.   I finally gave up and installed Chrome. Flash works on Chrome. (Unfortunately I hate Chrome. but what can you do?)  So, what's the issue? Has FireFox been snubbed, left in the dark by....______?

have you tried purging flash completely from your system and then downloading the plugin directly from adobe and copying the .so file to your mozilla plugins folder?

---

### Post by alphacrucis2 on 2012-04-26
> **BigCityCat said:**
> I would assume when it becomes neccessary that someone will find a way to system link Firefox to Chromes version of Flash on Linux. Not sure if possible but just a guess.

The Chrome one is supposed to use the pepper API. Mozilla have said they don't plan to support Pepper so no joy I suspect.

---

### Post by |{urse on 2012-04-26
Gnash perhaps?

---

### Post by alphacrucis2 on 2012-04-26
> **|{urse said:**
> Gnash perhaps?


Or better still, flash gets killed off by an open standard like html 5.

---

### Post by |{urse on 2012-04-26
Yeah, there is the html5 version of youtube also.

[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by ptolemy9 on 2012-04-26
Yes, I purged, etc., to no avail. (By the way I don't believe FireFox makes a "plug-in" folder anymore.)

---

### Post by lovinglinux on 2012-04-26
> **mamamia88 said:**
> One of the main reasons I love chrome built in flash and pdf support two fewer things to worry about on a fresh install

Firefox 14 will have PDF support as well. Currently they are testing a HTML5 renderer as an extension, but the browser is installing the extension automatically. Google on the other hand is using the Pepper API instead of promoting HTML5.

[https://addons.mozilla.org/en-US/firefox/addon/pdfjs/](https://addons.mozilla.org/en-US/firefox/addon/pdfjs/)

> **ptolemy9 said:**
> UPDATE:   Tried as I may, I could not get Flash to work on FireFox 12  / Ubuntu 10.04 LTS.   I finally gave up and installed Chrome. Flash works on Chrome. (Unfortunately I hate Chrome. but what can you do?)  So, what's the issue? Has FireFox been snubbed, left in the dark by....______?

Google and Adobe made a deal. Google will be distributing Flash with Chrome using their Pepper API, which nobody wants. Other brwsers will get stuck with the current buggy version of Flash.

> **ptolemy9 said:**
> Yes, I purged, etc., to no avail. (By the way I don't believe FireFox makes a "plug-in" folder anymore.)

Have you tried to..

[LIST]
[*]use a clean Firefox profile? 
[*]disable hardware acceleration in Flash? 
[*]purge cookies and browser cache? 
[*]create a new Ubuntu user just for testing?
[/LIST]

Does the problem persist on a clean UBuntu user account?

---

### Post by smellyman on 2012-04-26
Google also said they wouldn't support h.264 and instead use *their* open standard webm.  so FF only supported webm too.

Unfortunately google is a "do as I say and not as I do" company and continued to support H.264, leaving Mozilla high and dry.

Mozilla tried to be the good cop, but they finally said screw you to google and decided to support h.264

---

### Post by stchman on 2012-04-26
I have the 64 bit flash plugin from Adobe's website and Flash stopped working after Firefox 12 was installed.

I have the Flash .so file installed in the /usr/lib/firefox-addons/plugins directory.  This setup worked fine for Firefox 11.0 and older.

---

### Post by CharlesA on 2012-04-26
> **stchman said:**
> I have the 64 bit flash plugin from Adobe's website and Flash stopped working after Firefox 12 was installed.

I have the Flash .so file installed in the /usr/lib/firefox-addons/plugins directory.  This setup worked fine for Firefox 11.0 and older.
Running Lucid? Flash works fine for me on Lucid x64 and Firefox 12.

---

### Post by Gremlinzzz on 2012-04-27
In show hidden files delete .mozilla folder then click Firefox to create new .mozilla folder.open .mozilla put libflashplayer.so into plugins folder,if plugins folder doesn't exist create one :popcorn:

when you delete .mozilla you clean out all old Firefox settings like your bookmarks and stuff
get libflashplayer.so from here extract in downloads folder copy and paste


[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

get the one with tar.gz on the end

---

### Post by wolfen69 on 2012-04-27
> **Gremlinzzz said:**
> In show hidden files delete .mozilla folder then click Firefox to create new .mozilla folder.open .mozilla put libflashplayer.so into plugins folder,if plugins folder doesn't exist create one :popcorn:

when you delete .mozilla you clean out all old Firefox settings like your bookmarks and stuff
get libflashplayer.so from here extract in downloads folder copy and paste


[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

get the one with tar.gz on the end
Exactly. Always works. If the Op still has problems, maybe a reinstall is in order. Considering I've reinstalled **several**  times with windows, if you have to do it once in a while whith linux, Oh well. Life goes on, and nothing is perfect.

Ubuntu has been perfect *for me*, but I realize for others it might not be so. Just like *any* other operating system..........

To be honest, 11.10 has been as perfect as an OS can be. But I always have linux friendly computers. :guitar:

---

### Post by stchman on 2012-04-27
> **CharlesA said:**
> Running Lucid? Flash works fine for me on Lucid x64 and Firefox 12.

Where do you have the plugin stored?  Your home directory or the /usr/lib/firefox-addons/plugins/ directory?

Thanks.

---

### Post by stchman on 2012-04-27
> **Gremlinzzz said:**
> In show hidden files delete .mozilla folder then click Firefox to create new .mozilla folder.open .mozilla put libflashplayer.so into plugins folder,if plugins folder doesn't exist create one :popcorn:

when you delete .mozilla you clean out all old Firefox settings like your bookmarks and stuff
get libflashplayer.so from here extract in downloads folder copy and paste


[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

get the one with tar.gz on the end

That method doesn't make Flash available to other users on the machine.  You then have to put the plugin in EACH users home folder.

---

### Post by Gremlinzzz on 2012-04-27
> **stchman said:**
> That method doesn't make Flash available to other users on the machine.  You then have to put the plugin in EACH users home folder.

Good to know:popcorn:
installing 12.04 works too

---

### Post by CharlesA on 2012-04-27
> **stchman said:**
> Where do you have the plugin stored?  Your home directory or the /usr/lib/firefox-addons/plugins/ directory?

Thanks.

I had the ubuntu-restricted-extras package installed. The plugins folder in both /use/lib/firefox-addons and .mozilla/firefox are empty or don't exist.

I only found the .so file here:

```
charles@Lucid:~$ locate libflashplayer.so 
/usr/lib/flashplugin-installer/libflashplayer.so

```

---

### Post by lovinglinux on 2012-04-27
For a single user put in ~/.mozilla/plugins (create the folder if necessary)

For all users, put in /usr/lib/mozilla/plugins

If you put in /usr/lib/flashplugin-installer/ or /usr/lib/adobe-flashplugin/ it will be overwritten with the next update.

Flash-Aid can do that for you automatically. See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by Meneer Jansen on 2012-04-27
> **lovinglinux said:**
> 
For all users, put in /usr/lib/mozilla/plugins

Does not work. Did this and it does not work:
```

sudo ln -s /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so

```
I use Ubuntu 10.04 Lucid and did not have any probs w/ Flash until an update yesterday. WTF????? Pulling my hair out getting crazy! Firefox and Chrome say I do NOT have the Flash plugin any more. Not true. I installed it using Synaptic and the proper .so file exists. Why do updates always seem to break something that worked perfectly before? :(

---

### Post by lovinglinux on 2012-04-27
> **Meneer Jansen said:**
> Does not work. Did this and it does not work:
```

sudo ln -s /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so

```
I use Ubuntu 10.04 Lucid and did not have any probs w/ Flash until an update yesterday. WTF????? Pulling my hair out getting crazy! Firefox and Chrome say I do NOT have the Flash plugin any more. Not true. I installed it using Synaptic and the proper .so file exists. Why do updates always seem to break something that worked perfectly before? :(

Don't waste more time copying plugins manually. Use [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/). Is much easier than wasting time copying files and dealing with such issues, that's why I created it. It will remvoe conflicting plugins and install the version you want in the proper location.

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) for instructions on how to use Flash-Aid to downgrade a flash version.

---

### Post by Meneer Jansen on 2012-04-27
> **lovinglinux said:**
> Don't waste more time copying plugins manually. Use [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/"). Is much easier than wasting time copying files and dealing with such issues, that's why I created it. It will remvoe conflicting plugins and install the version you want in the proper location.

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) for instructions on how to use Flash-Aid to downgrade a flash version.
Thank you for the help and the tips. Unfortunately no matter what I try with *Flash Aid* it won't work. Neither the 'stable' one (that seems to install '/etc/**alternatives**/mozilla-javaplugin.so') nor the beta (seems to install '/usr/lib/adobe-flashplugin/libflashplayer.so' from the tar ball from the Adobe website).

Maybe it's because I use Firefox from the zip file that you have to extract yourself to your harddisk (i.e. '~/firefox').

P.S. Flash does not work in Chrome anymore either...

Where in '~/firefox' might I copy the .so library to test if it works?

---

### Post by lovinglinux on 2012-04-27
> **Meneer Jansen said:**
> Thank you for the help and the tips. Unfortunately no matter what I try with *Flash Aid* it won't work. Neither the 'stable' one (that seems to install '/etc/**alternatives**/mozilla-javaplugin.so') nor the beta (seems to install '/usr/lib/adobe-flashplugin/libflashplayer.so' from the tar ball from the Adobe website).

Maybe it's because I use Firefox from the zip file that you have to extract yourself to your harddisk (i.e. '~/firefox').

P.S. Flash does not work in Chrome anymore either...

Where in '~/firefox' might I copy the .so library to test if it works?

You could have mentioned that earlier.

You need to make a symlink from your default plugin folder or put the plugins manually in the ~/firefox/plugins folder.

```
sudo ln -s /usr/lib/mozilla/plugins ~/firefox/plugins
```

Anyway, if that stil doesn't work, click Flash-Aid Help menu, generate a report and paste it here.

---

### Post by ptolemy9 on 2012-04-27
> **lovinglinux said:**
> You could have mentioned that earlier.

You need to make a symlink from your default plugin folder or put the plugins manually in the ~/firefox/plugins folder.

```
sudo ln -s /usr/lib/mozilla/plugins ~/firefox/plugins
```Anyway, if that stil doesn't work, click Flash-Aid Help menu, generate a report and paste it here.
   Tried that too, didn't work for me.
 And for those asking about purging, cleaning, etc...I've done a complete reinstall with no luck.  I think it seems to be a break in Firefox 12.

---

### Post by ptolemy9 on 2012-04-27
> **lovinglinux said:**
> You could have mentioned that earlier.

You need to make a symlink from your default plugin folder or put the plugins manually in the ~/firefox/plugins folder.

```
sudo ln -s /usr/lib/mozilla/plugins ~/firefox/plugins
```Anyway, if that stil doesn't work, click Flash-Aid Help menu, generate a report and paste it here.
   The report:

---

### Post by lovinglinux on 2012-04-27
> **ptolemy9 said:**
> Tried that too, didn't work for me.
 And for those asking about purging, cleaning, etc...I've done a complete reinstall with no luck.  I think it seems to be a break in Firefox 12.

First, let's really cleanup the house:

Run these on a terminal:

```
rm -f /home/mojo/.adobe/libflashplayer.so
rm -f /home/mojo/.local/share/Trash/files/libflashplayer.so
rm -f /home/mojo/.local/share/Trash/info/libflashplayer.so.trashinfo
rm -f /home/mojo/Downloads/libflashplayer.so
rm -f /home/mojo/Downloads/reallystupid/libflashplayer.so
sudo apt-get remove flashplugin-installer
sudo apt-get remove adobe-flashlugin
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/flashplugin-installer/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so

```

Then run the following exactly in sequence:

> [COLOR="Red"]These commands are assuming you have a default Firefox installed on your system. If you only have firefox in ~/firefox location, then use **~/firefox/firefox** instead of **firefox** in the first and last commands.[/COLOR]


```
firefox -no-remote -CreateProfile troubleshoot
PROFILE=$(ls /home/${USER}/.mozilla/firefox/ | grep troubleshoot)
cd ~/.mozilla/firefox/${PROFILE}
mkdir ~/.mozilla/firefox/${PROFILE}/plugins
cd ~/.mozilla/firefox/${PROFILE}/plugins
wget https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz
tar xvf flashplayer11_1r102_63_linux.i386.tar.gz
rm flashplayer11_1r102_63_linux.i386.tar.gz
rm -r usr
cd
firefox -no-remote -safe-mode -P troubleshoot
```

You will be prompted with the Safe Mode dialog. Click the button to "Continue is Safe Mode". 

Once Firefox is open, type **about:config** in the address bar, then type **plugin.expose_full_path** in the filter, double click the resulting preference to make it **true**. 

Then type **about[noparse]:p[/noparse]lugins** in the address bar and look for Shockwave Flash. Make sure there is only one of it, that the location is something like **/home/mojo/.mozilla/firefox/*****.troubleshoot/plugins/libflashplayer.so** and the version is 11.1 r102.

If that is correct, test flash opening a youtube video.

Report back.

---

### Post by ptolemy9 on 2012-04-27
> **lovinglinux said:**
> First, let's really cleanup the house:

Run these on a terminal:

```
rm -f /home/mojo/.adobe/libflashplayer.so
rm -f /home/mojo/.local/share/Trash/files/libflashplayer.so
rm -f /home/mojo/.local/share/Trash/info/libflashplayer.so.trashinfo
rm -f /home/mojo/Downloads/libflashplayer.so
rm -f /home/mojo/Downloads/reallystupid/libflashplayer.so
sudo apt-get remove flashplugin-installer
sudo apt-get remove adobe-flashlugin
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/flashplugin-installer/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so

```Then run the following exactly in sequence:




```
firefox -no-remote -CreateProfile troubleshoot
PROFILE=$(ls /home/${USER}/.mozilla/firefox/ | grep troubleshoot)
cd ~/.mozilla/firefox/${PROFILE}
mkdir ~/.mozilla/firefox/${PROFILE}/plugins
cd ~/.mozilla/firefox/${PROFILE}/plugins
wget https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz
tar xvf flashplayer11_1r102_63_linux.i386.tar.gz
rm flashplayer11_1r102_63_linux.i386.tar.gz
rm -r usr
cd
firefox -no-remote -safe-mode -P troubleshoot
```You will be prompted with the Safe Mode dialog. Click the button to "Continue is Safe Mode". 

Once Firefox is open, type **about:config** in the address bar, then type **plugin.expose_full_path** in the filter, double click the resulting preference to make it **true**. 

Then type **about[noparse]:p[/noparse]lugins** in the address bar and look for Shockwave Flash. Make sure there is only one of it, that the location is something like **/home/mojo/.mozilla/firefox/*****.troubleshoot/plugins/libflashplayer.so** and the version is 11.1 r102.

If that is correct, test flash opening a youtube video.

Report back.

Hmmn,..seems to work but not with everything. I can watch porky pig, etc. and most of youtube. BBCnews says:" You do not have the correct version of the flash player." I will try again later. ( Got kids , easy to to miss a line.) Thanks for the effort !

---

### Post by lovinglinux on 2012-04-27
> **ptolemy9 said:**
> Hmmn,..seems to work but not with everything. I can watch porky pig, etc. and most of youtube. BBCnews says:" You do not have the correct version of the flash player." I will try again later. ( Got kids , easy to to miss a line.) Thanks for the effort !

There are reports that BBB is not working recently.

Now that we know it works, you need to test this with your regular Firefox profile. Do you have multiple accounts on your computer or just one?

---

### Post by ptolemy9 on 2012-04-27
Just one.

---

### Post by lovinglinux on 2012-04-27
> **ptolemy9 said:**
> Just one.

Please post the output of:

```
ls ~/.mozilla/firefox/
```

---

### Post by ptolemy9 on 2012-04-27
OK back.    output:     5z4f4rp.troubleshoot  Crash Reports  f6a479fj.default  profiles.ini

Hmn..shockwave does not appear in Manage Content plug-ins

---

### Post by lovinglinux on 2012-04-27
> **ptolemy9 said:**
> OK back.    output:     5z4f4rp.troubleshoot  Crash Reports  f6a479fj.default  profiles.ini

Hmn..shockwave does not appear in Manage Content plug-ins

Close Firefox, run these:

```
mkdir ~/.mozilla/plugins
mv ~/.mozilla/firefox/5z4f4rp.troubleshoot/plugins/libflashplayer.so ~/.mozilla/plugins/
rm ~/.mozilla/firefox/5z4f4rp.troubleshoot
```

Start Firefox and check if it works.

---

### Post by ptolemy9 on 2012-04-27
stumped here......

mojo@naughty:~$ mv ~/.mozilla/firefox/5z4f4rp.troubleshoot/plugins/libflashplayer.so ~/.mozilla/plugins/
mv: cannot stat `/home/mojo/.mozilla/firefox/5z4f4rp.troubleshoot/plugins/libflashplayer.so': No such file or directory

---

### Post by lovinglinux on 2012-04-27
> **ptolemy9 said:**
> stumped here......

mojo@naughty:~$ mv ~/.mozilla/firefox/5z4f4rp.troubleshoot/plugins/libflashplayer.so ~/.mozilla/plugins/
mv: cannot stat `/home/mojo/.mozilla/firefox/5z4f4rp.troubleshoot/plugins/libflashplayer.so': No such file or directory

Run these instead:

```
cd  ~/.mozilla/plugins
wget https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz
tar xvf flashplayer11_1r102_63_linux.i386.tar.gz
rm flashplayer11_1r102_63_linux.i386.tar.gz
rm -r usr
cd
```

Restart Firefox and test it.

---

### Post by ptolemy9 on 2012-04-27
OK, appears to have stuck this time .Shockwave appears in plugins and Youtube works, BBCnews,etc. 

GOOD WORK! THANKS!  going to sleep now.

---

### Post by lovinglinux on 2012-04-27
> **ptolemy9 said:**
> OK, appears to have stuck this time .Shockwave appears in plugins and Youtube works, BBCnews,etc. 

GOOD WORK! THANKS!  going to sleep now.

You are welcome.

Keep in mind you are using an old version of the flash plugin manually installed in the ~/.mozilla/plugins folder. It won't be updated automatically and it probably is a security risk. So use NoScript extension to block flash from sites you don't trust and check regularly for Adobe updates and test them to see if they work. You can do that by copying the libflashplayer.so file you download from Adobe and placing it under ~/.mozilla/plugins.

---

### Post by smellyman on 2012-04-28
Lovinglinux,

Just want to say you rock.....

---

### Post by lovinglinux on 2012-04-28
> **smellyman said:**
> Lovinglinux,

Just want to say you rock.....

Thanks. :guitar:

---

### Post by Meneer Jansen on 2012-04-28
> **lovinglinux said:**
> Keep in mind you are using an [SIZE=3]**old**[/SIZE] version of the flash plugin 
I found out too that the latest version of Flash is not exactly the greatest version. See [this topic]("http://ubuntuforums.org/showthread.php?p=11883815#post11883815") reply No. 9.

The latest version of Flash (11.2.202.233) HAS issues. The question is: why doesn't it work for some people and why does it for others? To be continued I think...

---

### Post by lovinglinux on 2012-04-28
> **Meneer Jansen said:**
> I found out too that the latest version of Flash is not exactly the greatest version. See [this topic]("http://ubuntuforums.org/showthread.php?p=11883815#post11883815") reply No. 9.

The latest version of Flash (11.2.202.233) HAS issues. The question is: why doesn't it work for some people and why does it for others? To be continued I think...

Mostly because of issues with nVidia driver. But who knows, flash is proprietary and no longer supported by Adobe.

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by bartos on 2012-04-28
Google Chrome( maybe Chromium) has flash built in now so you don't need separate flash plugin.

---

### Post by lovinglinux on 2012-04-28
> **bartos said:**
> Google Chrome( maybe Chromium) has flash built in now so you don't need separate flash plugin.

Chromium doesn't have because flash is proprietary. Only Chrome 32bit has flash bundled with it. The 64bit doesn't. The development version of Chrome 64bit is shipping with the new PepperFlash at this moment, but it is unusable.

---

### Post by jmore9 on 2012-04-28
Went from 11.10 to 12.04 with no problems.  Firefox ver 12 seems a little sluggish to me.  Flash worked just fine when firefox updated.  Don't know why.

---

### Post by Meneer Jansen on 2012-04-29
> **lovinglinux said:**
> Mostly because of issues with nVidia driver. But who knows, flash is proprietary and no longer supported by Adobe.

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)
That's not it. I get the error message that the Flash plugin can't be found. So I cannot even adjust the settings like you wrote in the mentioned topic.

There is something else wrong with the current 'libflashplugin.so' library. It just doesn't work.

---

### Post by Meneer Jansen on 2012-04-29
OK. Here's what I tested until now. I installed a version of Flash via Synaptic and replaced 'libflashplayer.so' in the directory '/usr/lib/flashplugin-installer/' every time with one of these versions:

1. Version 10.0 r45 from the Lucid repo's (old version).
2. Version 10.3 r183 From Adobe's site (see explanation below).
3. Version 11.1 r102 from (Lovinglinux, thank you for the link!): ```
wget https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz
```4. Version 11.2 r202 from Adobe's site (see picture below).

  See picture below. From Adobe's site you can choose to download the YUM version and the .tar.gz version of that (this turns out to be version 11.2 r202) OR the APT version for Ubuntu in its tar.gz form which turns out to be version 10.3 r183. Adobe offers two completely different versions depending on which Linux distro you use! Adobe is not  very clear on this. Synaptic's version is version 11.2 r202 (which don't work!).

***See attached picture***

The ony version that works in Firefox as well as in Chrome is number 3: the version that Lovinglinux offered us!

Shame on you Adobe! :(

---

### Post by lovinglinux on 2012-04-29
> **Meneer Jansen said:**
> OK. Here's what I tested until now. I installed a version of Flash via Synaptic and replaced 'libflashplayer.so' in the directory '/usr/lib/flashplugin-installer/' every time with one of these versions:

1. Version 10.0 r45 from the Lucid repo's (old version).
2. Version 10.3 r183 From Adobe's site (see explanation below).
3. Version 11.1 r102 from (Lovinglinux, thank you for the link!): ```
wget https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz
```4. Version 11.2 r202 from Adobe's site (see picture below).

  See picture below. From Adobe's site you can choose to download the YUM version and the .tar.gz version of that (this turns out to be version 11.2 r202) OR the APT version for Ubuntu in its tar.gz form which turns out to be version 10.3 r183. Adobe offers two completely different versions depending on which Linux distro you use! Adobe is not  very clear on this. Synaptic's version is version 11.2 r202 (which don't work!).

***See attached picture***

The ony version that works in Firefox as well as in Chrome is number 3: the version that Lovinglinux offered us!

Shame on you Adobe! :(

I can't tell you why one version works and others don't, but Adobe have been struggling with hardware acceleration recently and they turned it off on some versions. So, I suspect version 11.1 r102 is one of the old versions that was released without the hardware acceleration issues.

This is one of the reasons I say it doesn't matter that Adobe will provide security patches for 5 years. Sooner or later flash will stop working and we will have to move to Google Chrome.

---

### Post by Meneer Jansen on 2012-04-29
> **lovinglinux said:**
> I can't tell you why one version works and others don't, but Adobe have been struggling with hardware acceleration recently and they turned it off on some versions. So, I suspect version 11.1 r102 is one of the old versions that was released without the hardware acceleration issues.

This is one of the reasons I say it doesn't matter that Adobe will provide security patches for 5 years. Sooner or later flash will stop working and we will have to move to Google Chrome.
[semi off topic] Are you sure its the hardware accel. that causes the problems? I mean: Firefox and Chrome show me a black frame which says "Plugin not found". If its the hw. accel. I'd sooner expect laggy playback, weird color probs etc. It seems to be a software prob to me. But I may be mistaken...

And about Chrome: at the moment Chrome uses the plugin that I put in '/usr/lib/flashplugin-installer/'. To me Chrome does not seem to install some sort of Flash plugin itself... Is that going to change in the future?

I hope that Flash is going to be discontinued by Adobe very, very, soon so that developers can not use some sort of "new" features of Flash that the current working Linux Flash libray does not support... [Flash is not going to be updated for Linux anymore]

---

### Post by lovinglinux on 2012-04-29
> **Meneer Jansen said:**
> [semi off topic] Are you sure its the hardware accel. that causes the problems? I mean: Firefox and Chrome show me a black frame which says "Plugin not found". If its the hw. accel. I'd sooner expect laggy playback, weird color probs etc. It seems to be a software prob to me. But I may be mistaken...

No I am not sure. I am just speculating, based on the most common issues I have seen in the forums.

However, this is not the first time that hardware acceleration causes SMURF effect and in some cases it also made flash stop working entirely on some machines. So, I think it must be related.

However,  the issue with plugin not found could be a different thing indeed. For instance, that happens when you try to use a 32bit plugin on a 64bit browser.

> **Meneer Jansen said:**
> And about Chrome: at the moment Chrome uses the plugin that I put in '/usr/lib/flashplugin-installer/'. To me Chrome does not seem to install some sort of Flash plugin itself... Is that going to change in the future?

The only Chrome version that comes with flash is the 32bit build. Neither all Chromium builds and Chrome 64bit has it. However, the development build of Chrome 64bit already has PepperFlash. It is unusable at this moment, but it is there. I doubt Chromium will ever have a bundled flash plugin, Pepper or not.

> **Meneer Jansen said:**
> I hope that Flash is going to be discontinued by Adobe very, very, soon so that developers can not use some sort of "new" features of Flash that the current working Linux Flash libray does not support... [Flash is not going to be updated for Linux anymore]

Me too. However, I don't think that will happen. If they decide to drop flash entirely, then most likely they will transfer the development to Google and make some deal to keep monetizing on it. We need to keep in mind that PepperFlash doesn't work only on Linux. Although there won't be any good reason for Windows users to switch at the moment, Pepper is cross-platform. So, as soon as Google succeed in implementing PepperFlash, Adobe has an easy way out. I don't doubt if this is the intention Google from the beginning, because the whole thing smells fishy to me. I don't understand why one of the major browser vendors, video streaming providers and developer of WebM would invest in Flash at this point if they don't have an agenda. That is my personal view of this situation. But I might be too paranoid at this point, suffering with the idea of using Chrome.

---

### Post by Meneer Jansen on 2012-04-30
@Lovinglinux: I agree w/ everything you said! And thank you very much for all the info and the help. :)

---

### Post by lovinglinux on 2012-04-30
> **Meneer Jansen said:**
> @Lovinglinux: I agree w/ everything you said! And thank you very much for all the info and the help. :)

You are welcome.

---

