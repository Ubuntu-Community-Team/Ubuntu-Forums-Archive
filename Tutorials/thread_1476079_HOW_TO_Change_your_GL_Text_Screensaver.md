---
title: "HOW TO: Change your GL Text Screensaver"
date: 2010-05-07
forum: Tutorials
---

### Post by theozzlives on 2010-05-07
As we all know, the GL Text displays: Host-Name, Kernel Version. You can change it Quite easily. Go to terminal, CD to /usr/share/applications/screensavers The do ```
sudo nano gltext.desktop
``` Then change the line that reads ```
Exec=gltext -root
``` to ```
Exec=gltext -root -front -text 'your text here\n %l:%M:%S %p'
``` and there you have it, a custom text screensaver.

---

### Post by bapoumba on 2010-05-11
T&t :)

---

### Post by SoFl W on 2010-06-22
I see this has come up several times so I will post my changes. This displays the time on the screen in the format:
[CENTER][B]Tuesday
June 22, 2010
7:00:00 pm
[/B][/CENTER]

First I changed to the screensaver directory:

[COLOR=Blue]cd /usr/share/applications/screensavers [/COLOR]

Then I copied the text screen saver
[COLOR=Blue]sudo cp gltext.desktop gltime.desktop[/COLOR]

Then I edited the time screen saver, deleting everything and replacing it with the text below.
[COLOR=Blue]sudo nano gltime.desktop[/COLOR] 

```
[Desktop Entry]
Encoding=UTF-8
Name=GLTime
Comment=Displays a few lines of text spinning around in a solid 3D font. The text can use strftime() escape codes to display the current date and time. Written by Jamie Zawinski; 2001.
TryExec=gltext
Exec=gltext -root -front -text '%A%n%d %b %Y%n%l:%M:%S %p'
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME;
Name[en_US]=xxGLTime.txt
```

Control-O to save and Control-X to exit out of the editor.  Then go to Preferences->screensaver->GLtime should be listed.

For more options you can type
[COLOR=Blue]man gltext[/COLOR]
":q" to exit out of that.

Still very disappointed with the lack of a simple screen saver in Linux. Even the xscreensaver package has a ton of great choices but nothing simple.  I have seen several requests for the Windows marque type of screen saver. I just want something that displays the time or some text and moves it in different positions on the screen.  This bounces it all over the place. ("-no-spin" didn't seem to help)

---

### Post by kenfry13 on 2010-06-22
wow cool tip :guitar:

---

### Post by Stigmata13 on 2010-06-23
will this work with gksudo gedit?

---

### Post by Piro ko on 2010-07-31
> **SoFl W said:**
> I see this has come up several times so I will post my changes. This displays the time on the screen in the format:
[CENTER][B]Tuesday
June 22, 2010
7:00:00 pm
[/B][/CENTER]

First I changed to the screensaver directory:

[COLOR=Blue]cd /usr/share/applications/screensavers [/COLOR]

Then I copied the text screen saver
[COLOR=Blue]sudo cp gltext.desktop gltime.desktop[/COLOR]

Then I edited the time screen saver, deleting everything and replacing it with the text below.
[COLOR=Blue]sudo nano gltime.desktop[/COLOR] 

```
[Desktop Entry]
Encoding=UTF-8
Name=GLTime
Comment=Displays a few lines of text spinning around in a solid 3D font. The text can use strftime() escape codes to display the current date and time. Written by Jamie Zawinski; 2001.
TryExec=gltext
Exec=gltext -root -front -text '%A%n%d %b %Y%n%l:%M:%S %p'
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME;
Name[en_US]=xxGLTime.txt
```

Control-O to save and Control-X to exit out of the editor.  Then go to Preferences->screensaver->GLtime should be listed.

For more options you can type
[COLOR=Blue]man gltext[/COLOR]
":q" to exit out of that.

Still very disappointed with the lack of a simple screen saver in Linux. Even the xscreensaver package has a ton of great choices but nothing simple.  I have seen several requests for the Windows marque type of screen saver. I just want something that displays the time or some text and moves it in different positions on the screen.  This bounces it all over the place. ("-no-spin" didn't seem to help)

Even after following these directions to the letter I haven't been able to get things working. It's quite strange. I agree that a simple marque type screen saver is a somewhat simple oversight, but would be so helpful, when I was still working in Windows I often used it to keep a long-term to-do list so I would keep it memorized from constantly reading it whenever I wasn't using my laptop.

---

### Post by Hunnicutt on 2010-09-16
Some how this doesn't work for me on 10.04. The GLTime doesn't show up in the list of screensavers, and when I make the edit to GLText it doesn't change.  Anyone have any idea what could be missing? Worked great on 9.10.

---

### Post by theozzlives on 2010-09-18
> **Hunnicutt said:**
> Some how this doesn't work for me on 10.04. The GLTime doesn't show up in the list of screensavers, and when I make the edit to GLText it doesn't change.  Anyone have any idea what could be missing? Worked great on 9.10.

Drag gltime.desktop to the screen saver properties page. Then close the properties and open back up. gltime should be there.

---

### Post by clockworkpc on 2010-09-21
> **theozzlives said:**
> Drag gltime.desktop to the screen saver properties page. Then close the properties and open back up. gltime should be there.

I've done that and it works.  However, I wanted to tweak "GLTime" even further and now I have two instances of GLTime in the Screensaver properties.  Any idea how I can get rid of the first one?  I only have one copy of gltime.desktop in /usr/share/applications/screensavers

I tried killing the gnome-screensaver process, but when I restarted it, there were two instances of GLTime in the Screensaver Properties window.

It looks to me as if dragging GLTime into the Screensaver Properties window causes gnome-screensaver to record a copy in a separate file of its own.  Is there possibly a configuration file somewhere in /etc?

---

### Post by DDemir on 2010-11-27
I was able to use the instructions from SoFL (post #3) and I had a small problem running Ubuntu 10,10
Using [COLOR=Blue]sudo cp gltext.desktop gltime.desktop [COLOR=Black]only made a second copy of gltext without even changing the name.
So my next step was to sudo gedit the last GLtext file and changed name, and pasted the code from SoFL.
Only after that I could correctly use it 

I haven't messed around by dragging files through properties, etc since I am fresh user of ubuntu...

I hope this helps 


[/COLOR][/COLOR]

---

### Post by kermorweb on 2011-01-09
Hi, 
I wanted to customize Gltext screen saver to display the Rhythmbox current song infos.
Thanks for the help I got from this forum, it helped me much to findout how to do it.

I simply copied the /usr/share/applications/screensavers/gltext.desktop to /usr/share/applications/screensavers/glrb.desktop, edited it and now it's ok.
Here are the commands :

sudo cp /usr/share/applications/screensavers/gltext.desktop /usr/share/applications/screensavers/glrb.desktop
sudo gedit /usr/share/applications/screensavers/glrb.desktop

#I modified the line starting with "Name"
Name=GlRb 
#I modified the line starting with "Exec" :
Exec=/usr/lib/xscreensaver/gltext -root -program "rhythmbox-client --print-playing-format '%ta - %at\n%tt\n(%ag)'|iconv -fUTF-8 -tISO8859-15"

#Save and go to your screensavers settings panel. It should work fine!

You can check the rhythmbox-client man page for formats if you want to display some other infos. My format displays :
Artist - Album
Title
(Genre)

I have piped the output of rhythmbox-client to iconv as I'm french and have a lot of unicode chars in my id3 tags. Maybe you'll have to adapt to your own language. 

Hope it will help someone :D

---

### Post by skywatcher55 on 2011-01-09
LINUX SUCKS!!!! All that just to change your text?? My neighbor gave me this computer with Linux in  it!! It's awfull!!! NEVER AGAIN!!!! Long live windows!!!!!

---

### Post by ricardisimo on 2011-03-18
> **kermorweb said:**
> Hi, 
I wanted to customize Gltext screen saver to display the Rhythmbox current song infos.
Thanks for the help I got from this forum, it helped me much to findout how to do it.

I simply copied the /usr/share/applications/screensavers/gltext.desktop to /usr/share/applications/screensavers/glrb.desktop, edited it and now it's ok.
Here are the commands :

sudo cp /usr/share/applications/screensavers/gltext.desktop /usr/share/applications/screensavers/glrb.desktop
sudo gedit /usr/share/applications/screensavers/glrb.desktop

#I modified the line starting with "Name"
Name=GlRb 
#I modified the line starting with "Exec" :
Exec=/usr/lib/xscreensaver/gltext -root -program "rhythmbox-client --print-playing-format '%ta - %at\n%tt\n(%ag)'|iconv -fUTF-8 -tISO8859-15"

#Save and go to your screensavers settings panel. It should work fine!

You can check the rhythmbox-client man page for formats if you want to display some other infos. My format displays :
Artist - Album
Title
(Genre)

I have piped the output of rhythmbox-client to iconv as I'm french and have a lot of unicode chars in my id3 tags. Maybe you'll have to adapt to your own language. 

Hope it will help someone :D

Thanks! It helped me. This is exactly what I was looking for. I'm most likely going to get rid of the movement, but the text is perfect.

---

### Post by ricardisimo on 2011-03-18
> **skywatcher55 said:**
> LINUX SUCKS!!!! All that just to change your text?? My neighbor gave me this computer with Linux in  it!! It's awfull!!! NEVER AGAIN!!!! Long live windows!!!!!

So, someone gave you a free computer with a free system on it, and this is your response? You strike me as someone who likes paying for sex as well, and enjoys the viruses caught in the process.

---

### Post by JDailey on 2011-05-05
If you are afraid of the command line, then you can try a little different track to get virtually the same result.  
1. Navigate to your filesystem (Click on your home screen and then the left arrow next to your user name near the top.  Do it until it says file system or just click on it in the left hand list)
2. Now click on view "Show hidden items"
3. Now click on "usr" and then "share" and then "applications" and then "screensavers"
4. Right click on GLText and select copy to desk top.
5. Minimize the window.
6. on the desktop, right click and rename the file to GLTime.
7. Right click on GLTime and select properties.
8. delete everything in the "command" line
9. copy and paste this into the command line: gltext -root -front -text '%A%n%d %b %Y%n%l:%M:%S %p'
10. delete everything in the "Comment" line
11. Paste the following into the Comment line: Displays a few lines of text spinning around in a solid 3D font. The text can use strftime() escape codes to display the current date and time. Written by Jamie Zawinski; 2001.
12. Click on "Close"
13. Cut the GLTime file and paste it in the screen saver folder.
14. it should appear in the list of screen savers.

Warning: The Preceding directions are for recovering Windows users.  Long term Linux users should not attempt to follow them.

---

### Post by maan81 on 2011-06-22
> **JDailey said:**
> If you are afraid of the command line, then you can try a little different track to get virtually the same result.  
1. Navigate to your filesystem (Click on your home screen and then the left arrow next to your user name near the top.  Do it until it says file system or just click on it in the left hand list)
2. Now click on view "Show hidden items"
3. Now click on "usr" and then "share" and then "applications" and then "screensavers"
4. Right click on GLText and select copy to desk top.
5. Minimize the window.
6. on the desktop, right click and rename the file to GLTime.
7. Right click on GLTime and select properties.
8. delete everything in the "command" line
9. copy and paste this into the command line: gltext -root -front -text '%A%n%d %b %Y%n%l:%M:%S %p'
10. delete everything in the "Comment" line
11. Paste the following into the Comment line: Displays a few lines of text spinning around in a solid 3D font. The text can use strftime() escape codes to display the current date and time. Written by Jamie Zawinski; 2001.
12. Click on "Close"
13. Cut the GLTime file and paste it in the screen saver folder.
14. it should appear in the list of screen savers.

Warning: The Preceding directions are for recovering Windows users.  Long term Linux users should not attempt to follow them.


Just to change the text we need to make a copy of the file 'GLText' & rename it ? 

I think it would be better if we could be able to change the text and its properties without directly modifying the files.

---

### Post by JohnSpartan0311 on 2011-07-04
> **JDailey said:**
> Warning: The Preceding directions are for recovering Windows users.  Long term Linux users should not attempt to follow them.

HAHAHA! Indeed! - It worked for me lol :oops:

Being new to all of this, to display a 24 hour time, do I simply use the ISO 8601 format?

What I would like to do, is alter the format for DTG (Date Time Group). It's format is DDHHMMZMonYY. Currently the DTG is (at the time of this posting): 042331ZMON11

I hope all that makes sense!

---

### Post by geazzy on 2011-07-06
great threads :)

---

### Post by baz.g on 2011-09-01
> **JohnSpartan0311 said:**
> HAHAHA! Indeed! - It worked for me lol :oops:

Being new to all of this, to display a 24 hour time, do I simply use the ISO 8601 format?

What I would like to do, is alter the format for DTG (Date Time Group). It's format is DDHHMMZMonYY. Currently the DTG is (at the time of this posting): 042331ZMON11

I hope all that makes sense!

@JohnSpartan - you would need this code in the gltext file:

%d%H%M%S%b%y

all the codes can be found [here]("http://www.intricatenetworks.com/ihtmlbook/strftime_Escape_Characters.html")

---

### Post by baz.g on 2011-09-01
what would be really nice is to be able to display the weather symbol and temp (same as gnome panel) in the screensaver, alongside the date and time :)

but i havent been able to find the code for that yet :(

---

### Post by JohnSpartan0311 on 2011-09-01
Awesome! Thanks for the information!

Yeah that would be great. I havent found anything like that at all either.

---

### Post by baz.g on 2011-09-01
> **JohnSpartan0311 said:**
> Awesome! Thanks for the information!

Yeah that would be great. I havent found anything like that at all either.

No problem mate, it's nice to be of some help to someone else on here for a change :-) lol

---

### Post by forestwalkerjoe on 2011-11-20
> **JDailey said:**
> If you are afraid of the command line, then you can try a little different track to get virtually the same result.  
1. Navigate to your filesystem (Click on your home screen and then the left arrow next to your user name near the top.  Do it until it says file system or just click on it in the left hand list)
2. Now click on view "Show hidden items"
3. Now click on "usr" and then "share" and then "applications" and then "screensavers"
4. Right click on GLText and select copy to desk top.
5. Minimize the window.
6. on the desktop, right click and rename the file to GLTime.
7. Right click on GLTime and select properties.
8. delete everything in the "command" line
9. copy and paste this into the command line: gltext -root -front -text '%A%n%d %b %Y%n%l:%M:%S %p'
10. delete everything in the "Comment" line
11. Paste the following into the Comment line: Displays a few lines of text spinning around in a solid 3D font. The text can use strftime() escape codes to display the current date and time. Written by Jamie Zawinski; 2001.
12. Click on "Close"
13. Cut the GLTime file and paste it in the screen saver folder.
14. it should appear in the list of screen savers.

Warning: The Preceding directions are for recovering Windows users.  Long term Linux users should not attempt to follow them.
Ok.. that sounded all NICE until we got to the ' user , share , application - Screen saver.. then PICK GL Text , RIGHT CLICK. which mine does not allow. I get the same pop up after clicking on Screen saver as I do if I just used the ICON for screen saver. the LIST of Screen Savers but no ability to Right Click anything.

---

### Post by pjd99 on 2011-11-20
I remember when xscreensaver was used. There was a button to change the settings for screensavers that had them (gltext, photo slideshows etc).

Bug I've been subscribed to for as long as I can remember:
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/22007](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/22007)

Small program for accessing settings:
[http://whenimbored.xfx.net/2011/05/i-want-my-screensaver-settings/](http://whenimbored.xfx.net/2011/05/i-want-my-screensaver-settings/)

---

### Post by F35 on 2012-04-23
I attempted the copy and edit suggestions above.  I can not get the xscreensaver (5.14) "Screensaver Preferences" to show my added gltext file.  I specified the name as GlRb.  I expected it to show up.  I have re-booted the machine, stopped the Daemon, but I can't get it to show GlRb as an optional screensaver.  I also tried to drag and drop the GlRb from nautilus into the Screensaver Preferences list.  So far, nothing is working.  I even tried just making a copy of the gltext.desktop, renaming it glrb.desktop and changing only the Name= parameter inside the glrb.desktop file without any other modifications.  

How can I get my new copied version of the gltext (now GlRb) to show up in as a selectable optional screensaver in xscreensaver?

Running Ubuntu 11.10.

---

### Post by F35 on 2012-04-25
Had access to a Linux Mint computer and followed the instructions.  They worked perfectly, just as advertised.  So, I am more confident I know how to make the changes, so, I am now a little more concerned there may be some issue with Ubuntu 11.10.  One thing though, Linux Mint already had xscreensaver installed as part of the Mint, so I did not install the .deb file I used for Ubuntu 11.10.  

Anyone else had success making a copy and revising GLTEXT using Ubuntu 11.10?

---

