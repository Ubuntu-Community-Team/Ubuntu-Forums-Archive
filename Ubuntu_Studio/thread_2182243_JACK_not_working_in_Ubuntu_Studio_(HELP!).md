---
title: "JACK not working in Ubuntu Studio (HELP!)"
date: 2013-10-20
forum: Ubuntu Studio
---

### Post by db2k on 2013-10-20
I can't figure this one out. I have Ubuntu Studio 12.4 on a couple other computers and Jack works just dandy. I can not for the life of me make it work on my desktop. Here's the errors I'm running into:
 > [COLOR=#999999]15:30:48.180 Patchbay deactivated.[/COLOR]

 [COLOR=#999999]15:30:48.205 Statistics reset.[/COLOR]
 [COLOR=#cccc99]15:30:48.218 ALSA connection change.[/COLOR]
 [COLOR=#999999]15:30:48.226 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]15:30:48.243 ALSA connection graph change.[/COLOR]

 [COLOR=#ff0000]15:30:51.435 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Sun Oct 20 15:30:51 2013: Starting jack server...
 Sun Oct 20 15:30:51 2013: JACK server starting in realtime mode with priority 10
 Sun Oct 20 15:30:51 2013: control device hw:0
 Sun Oct 20 15:30:51 2013: control device hw:0
 Sun Oct 20 15:30:51 2013: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
 Sun Oct 20 15:30:51 2013: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
 Sun Oct 20 15:30:51 2013: [1m[31mERROR: Cannot initialize driver[0m
 Sun Oct 20 15:30:51 2013: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Sun Oct 20 15:30:51 2013: [1m[31mERROR: Failed to open server[0m
 Sun Oct 20 15:30:52 2013: Saving settings to "/home/dann/.config/jack/conf.xml" ...

 [COLOR=#ff0000]15:30:53.508 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket

 jack server is not running or cannot be started


Default settings, or tweaking everything- it always yields the same result.  It also pops up with "D-BUS: JACK Server could not be started   Sorry" and "Could not connect to JACK Server as client, -Overall operation failed -Unable to connect to server"

I'm using a USB sound card (which is installed properly and gives me no issues when using anything else). Said soundcard works perfectly on my laptop running the same OS and configuration (however it won't run in KXStudio(?). But I'm unable to get JACK running when using my onboard Soundcard or anything other changes you can think of.

I did some Googling (for days...) trying to figure this out. A lot of people have run into this problem. Most people's stems from pulseaudio, however turning off pulseaudio entirely (and even removing it completely) doesn't help.

Oddly enough, I CAN get JACK running in KXStudio with Claudia, but NOT with my USB Soundcard. The USB Soundcard isn't the biggest deal. I'd be happy to have JACK running AT ALL in my Ubuntu install. But I know for a fact that Ubuntu Studio 12.4 can run JACK with this soundcard as it gives me no issues at all on my laptop. 

I'm tearing my hair out here. I've been working on this around a week now. I've installed Ubuntu a few dozen times in different ways trying to make this work. Can anyone help? At this point I'd even be willing to pay someone to make this work.

---

### Post by su:bhatta on 2013-10-21
Have you tried changing the Interface in Jack Settings ? It is currently hw:0, are there any dropdown options? Please try them if there are any.

All I can point out are some help pages which have worked for me: 

[This link should help you:   https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.Starting_Jack]("https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.Starting_Jack")

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

[http://www.64studio.com/quickstart_jack](http://www.64studio.com/quickstart_jack)

[http://jackaudio.org/faq](http://jackaudio.org/faq)

---

### Post by fred-lorrain on 2013-11-03
Don't forget to add your username to the "audio"group,     In terminal type    sudo usermod -a -G audio username         (where *username* is your log-in name)

and check to make sure that  */etc/security/limits.d/audio.conf*.   isn't  */etc/security/limits.d/audio.conf*.disabled 
 if so simply rename it w/out the disabled part. (in your file manager press ctrl+h to show hidden files)

For more info have a lookk at:  [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by su:bhatta on 2013-11-05
> **fred-lorrain said:**
> Don't forget to add your username to the "audio"group,     In terminal type    sudo usermod -a -G audio username         (where *username* is your log-in name)

and check to make sure that  */etc/security/limits.d/audio.conf*.   isn't  */etc/security/limits.d/audio.conf*.disabled 
 if so simply rename it w/out the disabled part. (in your file manager press ctrl+h to show hidden files)

For more info have a lookk at:  [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Hi fred-lorrain,

With an Ubuntu Studio installation you don't have to add user to the audio group, both user addition & audio.conf is enabled by default.

That guide is for installing Ubuntu Studio packages on top of an standard Ubuntu installation, as mentioned in the first line of the page.

The OP uses Ubuntu Studio 12.04. so those might not be the issue.

---

