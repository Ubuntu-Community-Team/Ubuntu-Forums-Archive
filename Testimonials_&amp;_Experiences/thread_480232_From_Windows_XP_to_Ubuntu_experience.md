---
title: "From Windows XP to Ubuntu experience"
date: 2007-06-21
forum: Testimonials &amp; Experiences
---

### Post by th_11 on 2007-06-21
I have now used Ubuntu 7.04 (Feisty) a week or so and I would like to share few experiences.

Installing Ubunto from a live cd went smooth and no problems at all. Then I had an empty desktop and first of all I wanted to get my Windows disk show up on Ubuntu. I attached the disk to my computer and followed instructions at [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
Everything went fine and I had /media/windows volume ready to use!

Next I wanted to get network shares automatically mounted everytime I use my computer, I found an tutorial [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite") and I thought that it was all set up good. But well, problems came up everytime I rebooted my machine ([here]("http://ubuntuforums.org/showthread.php?t=477195") is more details about that). As this is not a major big problem, I decided to live with it (and bang my head a wall a bit).

Then it was time to get my mp3's and Shoutcast radio to work. First I had to find a music player. It got a bit tricky to find one that was somewhat what I was looking for (I'm a hardcore Winamp Classic user!). I tried Amarok, Beep Media Player, Rhythmbox, VLC, XMMS and so on... None of them was usable for me, either they were ugly looking or couldn't handle Shoutcast radios or just stopped responding after a while! I was about to get mad 'cause of that it seemed so hard to find a decent media player, BUT lucky me I was reading some Ubuntu discussion and someone there suggested [Exaile!]("http://www.exaile.org/") That player was enough to satisfy my needs for a mediaplayer. I was able to get all my mp3's played and even better it had integrated Shoutcast browser! Of course I had to install the mediacodecs first, [here]("https://help.ubuntu.com/community/RestrictedFormats") is the guide I followed (and got the job done). And I realized that the Exaile! got from Synaptic wasn't the most recent version, so I just went to exaile.org and followed instructions there to get the most recent version (it was an easy job, just added a new repository and Installed with apt-get).

Now it was time to get my mail from Windows Thunderbird to Ubuntu Thunderbird. I don't remember was Thunderbird already preinstalled or did I had to use Synaptic to get it but anyway, I was thinking it would be no problem as I would just copy the mail box files from Windows disk to Ubuntu disk (of course to a right place replacing the default Thunderbird files). I created an account to the Thunderbird and found the mailbox files from  /home/myusername/.thunderbird/profileblabla/Mail. Now I closed Thunderbird and replaced the files with my Windows Thunderbird mailbox files. I was a bit excited and started Thunderbird again, BUT the messages were not there! Dang! I was looking a bit further and realized that the Thunderbird on Ubuntu was old version and as I had used the most recent version on Windows the mailbox files couldn't just be plain copied (at least I think that was the reason). Well, thank god I found [Ubuntuzilla]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla") python script that automatically fetched and installed the most recent version of Thunderbird to my Ubuntu! Now I recopied the mailbox files and all the messages were there, job done!

I still wanted to find a good php editor and tried various programs but none of them really did the job well (right text encoding, working auto indent/outdent, color syntax, line numbers etc.), untill I found [ActiveState Komodo Edit]("http://www.activestate.com/products/komodo_edit/"). That was even better than Crimson Editor that I had used on Windows!

Lastly I was looking for an ftp client, a GUI ftp client!! (I would rather die than use those command line monsters). That become a very hard operation, there just doesn't seem to be good graphical ftp client for Ubuntu (for linux at all I guess). Of course I tried gFTP and it was actually average client, but I wouldn't use it as it was somehow too slow for my liking. I don't mean transfers too slow but the gui was too slow (hmm it's hard to explain).

Well thank god again, I accidently tried [Wine]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Install_Wine") AND under Wine, my old work horse WS FTP got running good! Even better it had all the connection information in place and I was able to connect to the sites I had added during years! That was very pleasant :D Then I actually did a little guru operations and created a start_wsftp.sh to my home folder and added a "shortcut" to my desktop which starts the WS FTP with Wine:

```
#!/bin/bash

cd /media/windows/Program\ Files/WS_FTP
wine WS_FTP95.exe
exit 0
```

After all that as a bonus I installed [Opera web browser]("http://www.opera.com/download/") also, their web page suggested me the right installation file and the setup went very easily. I was then even a little suprised as a day or two later Ubuntu notified me that there is an update for the Opera available, even thought I didn't even install it using Synaptic. point to Ubuntu for that!

But now a few words about the "pissing me off" things:

Firstly, as described earlier, my network shares doesn't get mounted on reboot.

Secondly, I really can't use the eye candy features (Beryl) as I have only 64 meg Radeon. Well it works, but when I get more programs running on my desktop, rotating the cube doesn't go smooth at all anymore. And the desktop environment in general becomes a bit slow. Not acceptable in my opinion (especially when my Komodo Editor gets slower too!).

Thirdly (and lastly), I had major problems with sound! They just disappeared. I did everything on earth following guides and guides, but no, no sound in anyway. (I have Sound Blaster Live). But then after one reboot suddenly the sound came back as quickly as it disappeared! Hooray! Now I'm afraid to reboot the computer as I fear I may lose the sound again. But well, I continue with Ubuntu and lets see what happens... ;)

**Forgot to mention** First time I attached the second disk (Windows disk) to my computer and started Ubuntu, Gnome was screwed up. Luckily I found by google that I should delete .gconf folder from my home folder (I actually renamed it) and rebooted the machine, all good again! :)

**Forgot to mention #2** I tried Winamp from Wine and it actually started up! Direct Sound problem was easily fixed from Winamp options (I changed output plugin to another one), but after a while I decided go back to Exaile! Winamp on Wine is a bit buggy, at least the playlist window and the main player window won't stay "together" and they show up as two different applications in my panel. Big plus to Winamp and Wine thought about that Winamp has my playlist just as it was on Windows side, all mp3 files from the Windows disk played and the network streams played (it didn't even complain missing mp3 files) :)

---

### Post by vexorian on 2007-06-21
> Thirdly (and lastly), I had major problems with sound! They just disappeared. I did everything on earth following guides and guides, but no, no sound in anyway. (I have Sound Blaster Live). But then after one reboot suddenly the sound came back as quickly as it disappeared! Hooray! Now I'm afraid to reboot the computer as I fear I may lose the sound again. But well, I continue with Ubuntu and lets see what happens...
Eventually we'll have openal.  I remember than on breezy, sound sometimes didn't work, it was because another program was reserving the sound channel and I had to try multiple times, it doesn't happen to me anymore on Feisty but I have to accept that I no longer use sound so much, I just use it sometimes to play some music but you won't be seeing me playing prboom again.

So I guess patience would work.

> my network shares doesn't get mounted on reboot Actually you don't have to, afaik I just made a launcher in the desktop to point out to "nautilus smb://compname/whateverfolder" and then I have to double click,  I don't think it ever gets mounted on reboot, but doing smb: would try to mount it seems.

If not you can always make an script that mounts it to you and opens the folder.

Yes, beryl won't work with such low graphic cards, it is meant to exploit the power of strong cards thus it is not acceptable on the rest.

VLC got masks, but I seriously think skins on multimedia players are overrated, but it is your taste. Please tell winamp not to promote monopolies, that they should begin making cross platform software which is what serious companies do.

---

### Post by th_11 on 2007-06-25
I have now rebooted my machine and sound is working, looks good!...

I can get along with doing the network shares mount by hand every time I boot the machine. But this seems to be a common problem with (at least) Feisty so I was thinking maybe I should do some kind of bug report if it is not alredy reported (I really couldn't quickly find if it was reported as a bug etc.)?

Yeah I realized it too that those eye candy features requires a powerfull graphics card, maybe I'll get one someday and can use Beryl.. :D

I have now started to like Exaile! and maybe I won't miss Winamp that much anymore. It looks like it won't be available for Linux any time (soon). But maybe I'll send some feedback and ask them to make it for Linux also, who knows...

P.S. I have found a new littele annoyance, everytime I log out (I really don't ever log out thought), the login screen gets all screwed up. If I log in again the screwed up screen comes to my desktop also and I really couldn't figure out any other solution than a reboot. It's a little hard to explain this "screwed up", but the screen just gets full of "lines" and on the login screen I can't access the options menu where I could choose different session etc. Maybe this is a bug on Feisty? I haven't had time to search for such problems yet, I'll look on that later.

---

