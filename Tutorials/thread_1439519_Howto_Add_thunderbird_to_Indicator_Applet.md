---
title: "Howto: Add thunderbird to Indicator Applet"
date: 2010-03-26
forum: Tutorials
---

### Post by shortcut144 on 2010-03-26
This has worked for me to far on Karmic.  I think it would be the same if any other versions use the indicator applet.  If you would also like to have notification from libnotify, follow this <a href="http://www.theopensourcerer.com/2010/02/09/indicator-applet-libnotify-support-for-thunderbird/"]http://www.theopensourcerer.com/2010/02/09/indicator-applet-libnotify-support-for-thunderbird/">post</a> 

1.  Add a Desktop file for Indicator Applet 
```
sudo touch /usr/share/applications/thunderbird.desktop
```

2.  Add new text to this file.

```
sudo nano /usr/share/applications/thunderbird.desktop
```

```
[Desktop Entry]
Encoding=UTF-8
Name=Mozilla Thunderbird Mail/News
Comment=Read/Write Mail/News with Mozilla Thunderbird
GenericName=Mail Client
Exec=thunderbird-3.0 %u		#Change according to your Thunderbird command
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=thunderbird
Categories=Application;Network;Email;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;
StartupWMClass=Thunderbird-bin
StartupNotify=true

```

3. Add another new file for indicator Applet.

```

sudo touch /usr/share/indicators/messages/applications/thunderbird

```

4. Add text to the file.

```

sudo nano /usr/share/indicators/messages/applications/thunderbird
```

```
/usr/share/applications/thunderbird.desktop

```

Close and exit the Terminal.

Now Logout and Login and Thunderbird should be in your indicator applet.

---

### Post by sambita on 2010-04-01
Awesome thanks!

---

### Post by Kaobear on 2010-04-02
Worked awesome, thanks!

---

### Post by OzzyFrank on 2010-05-04
At step 3 after **sudo touch /usr/share/indicators/messages/applications/thunderbird** I get this error:

**[COLOR="Purple"]touch: cannot touch `/usr/share/indicators/messages/applications/thunderbird': No such file or directory[/COLOR]**

Any ideas?

---

### Post by stanna on 2010-05-21
thank god for this little hack, cheers dude. worked like a charm. should be easier to add/remove things to the inficator.. for people like me who dont know all that much.

---

### Post by albinootje on 2010-05-21
> **OzzyFrank said:**
> At step 3 after **sudo touch /usr/share/indicators/messages/applications/thunderbird** I get this error:

**[COLOR="Purple"]touch: cannot touch `/usr/share/indicators/messages/applications/thunderbird': No such file or directory[/COLOR]**


The touch command is not even needed here, just continue with :
sudo nano /usr/share/indicators/messages/applications/thunderbird

Perhaps the directory /usr/share/indicators/messages/applications/ is not there on your computer for some reason ?

---

### Post by sayantandas on 2010-05-25
> **shortcut144 said:**
> This has worked for me to far on Karmic.  I think it would be the same if any other versions use the indicator applet.  If you would also like to have notification from libnotify, follow this <a href="http://www.theopensourcerer.com/2010/02/09/indicator-applet-libnotify-support-for-thunderbird/"]http://www.theopensourcerer.com/2010/02/09/indicator-applet-libnotify-support-for-thunderbird/">post</a> 

1.  Add a Desktop file for Indicator Applet 
```
sudo touch /usr/share/applications/thunderbird.desktop
```

2.  Add new text to this file.

```
sudo nano /usr/share/applications/thunderbird.desktop
```

```
[Desktop Entry]
Encoding=UTF-8
Name=Mozilla Thunderbird Mail/News
Comment=Read/Write Mail/News with Mozilla Thunderbird
GenericName=Mail Client
Exec=thunderbird-3.0 %u		#Change according to your Thunderbird command
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=thunderbird
Categories=Application;Network;Email;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;
StartupWMClass=Thunderbird-bin
StartupNotify=true

```

3. Add another new file for indicator Applet.

```

sudo touch /usr/share/indicators/messages/applications/thunderbird

```

4. Add text to the file.

```

sudo nano /usr/share/indicators/messages/applications/thunderbird
```

```
/usr/share/applications/thunderbird.desktop

```

Close and exit the Terminal.

Now Logout and Login and Thunderbird should be in your indicator applet.

a fantastic post!! I am going to link this to my blog. thanks again.

---

### Post by hellblazer on 2010-05-27
yeah! thanks! :)

---

### Post by OzzyFrank on 2010-05-31
I can't do the 2nd part:

**[COLOR="Red"]touch: cannot touch `/usr/share/indicators/messages/applications/thunderbird': No such file or directory[/COLOR]**


I don't even have **/usr/share/indicators**. I'm running Lucid 64-bit. Any ideas? Cheers.

---

### Post by OzzyFrank on 2010-06-01
Oh... OK, hehe... **/usr/share/indicators** was no longer on my system (and hence any subfolders) because while trying to get rid of the Evolution notifier and get my volume button back, I uninstalled **[COLOR="Red"]indicator-messages[/COLOR]**. Actually, I think I did that after I realised I didn't have to put up with **indicator-applet** since all I needed was the old **gnome-volume-control-applet**. Anyway, just successfully added Thunderbird to the Indicator Applet... (now I just have to figure out what happened to my system tray, and why adding a new *notification area* gives me nothing but its drag bar thingy!).

So anyone else who had the same error:
[B][COLOR="Red"]
sudo apt-get install indicator-messages[/COLOR][/B]

If your system tray is missing afterwards, as with me, just logout and back in, or reboot.

While I actually won't be displaying Indicator Applet all the time, not until they let me customise away that horrifically large spacing between icons, I'll leave it installed so I can play with cool tips like this. Hopefully one day we won't need hacks, but it will have a config GUI app. But I must say I'm both impressed and surprised that of the apps I have running, besides Rhythmbox the only other app using this notifier is KAlarm, a KDE app, hehe.

---

### Post by EddieNYC on 2010-06-19
Does this hack also give you other options from the envelope such as Compose Mail etc?

Also, does Thunderbird need to be running for this indicator applet mod to work ?

---

### Post by OzzyFrank on 2010-06-19
Not sure if those options were available for Evolution from the menu, but no, all you get is access to Thunderbird (ie it brings it to the front if open, or opens it if not... which answers the second question).

---

### Post by vonkemp on 2010-07-06
For the record, you can turn on the compose and contact links for tb in the panel by adding this to the bottom of the .desktop entry mentioned above.

```
X-Ayatana-Desktop-Shortcuts=Compose;Contacts

[Compose Shortcut Group]
Name=Compose New Message
Exec=thunderbird mailto:
OnlyShowIn=Messaging Menu

[Contacts Shortcut Group]
Name=Contacts
Exec=thunderbird -addressbook
OnlyShowIn=Messaging Menu
```

---

### Post by asensio on 2010-07-21
I sucessufuly added TB to the indicator applet, but now I have a question: is there any way to hide thunderbird from the panel but keeping it running? I want to use the indicator panel as if it was a system tray icon for TB.

Thank you and cheers

p.s. - what about emesene? Can we add it and use it like empathy, changing status and receiving notifications?

---

### Post by piterhansel on 2010-08-11
Just add Mozilla Notification Extensions (libnotify_popups-0.2.1-tb.xpi) from thunderbid add-ons website for this to work.
You'll still need to have thunderbird opened to get that message icon to work... Can allways install thunderbird minimize to tray to have it closed and the message icon working I guess.

---

### Post by carlos-alberto-teixeira on 2010-08-19
Dear shortcut144, greetings from Rio!

1,000 thanks for your perfect instructions.

On service,

- [c.a.t.]("http://catalisando.com")

---

### Post by Crucias on 2010-09-08
This is a guide to add emesene to the indicator applet. It is adapted from the OP

1.  Add a Desktop file for Indicator Applet 

```

sudo touch /usr/share/applications/emesene.desktop
```

2.  Add the bottom two lines (below) to this file.

```
sudo gedit /usr/share/applications/emesene.desktop
```

```
[Desktop Entry]
Name=Emesene
GenericName=Emesene
Comment=MSN Messenger Client
Terminal=false
Type=Application
Icon=emesene
Categories=Network;InstantMessaging;
StartupWMClass=Emesene-bin
StartupNotify=true

```

3. Add another new file for indicator Applet.

```

sudo touch /usr/share/indicators/messages/applications/emesene

```

4. Add the second code into the gedit you open with the command below.

```

sudo nano /usr/share/indicators/messages/applications/emesene
```

```
/usr/share/applications/emesene.desktop

```

Close and exit the Terminal.

Now Logout and Login and Emesene should be in your indicator applet.

---

### Post by piggyslasher on 2010-09-19
There's a much more up to date guide here, complete with how to integrate it your desktop like Evolution.

[Replace Evolution with Thunderbird completely in Ubuntu]("http://www.techgarten.com/ubuntu/replace-evolution-thunderbird-completely-ubuntu/")

---

### Post by oldmankit on 2010-12-09
> **asensio said:**
> I sucessufuly added TB to the indicator applet, but now I have a question: is there any way to hide thunderbird from the panel but keeping it running? I want to use the indicator panel as if it was a system tray icon for TB.

Thank you and cheers

p.s. - what about emesene? Can we add it and use it like empathy, changing status and receiving notifications?
+1
I also am looking for a way to do this.  I've successfully got thunderbird to appear in the indicator applet, but it only gives me notifications when thunderbird is running.  

I can use alltray but I don't want a second icon in my notification area!  I cannot see an option for alltray that uses no tray icon at all.

---

### Post by ebcovert3 on 2011-02-05
Great post. Thank you.

---

### Post by oldmankit on 2011-02-05
I found a solution (a real solution) which I posted elsewhere:

> I've found a  way of getting notifications through indicator-applet (in the little  mail icon) without having to have thunderbird running.  Credit goes to [http://www.techgarten.com/extensions...erick-cloudsn/]("http://www.techgarten.com/extensions/thunderbird/integrate-messaging-applet-thunderbird-maverick-cloudsn/")

Add the private repository as follows, update, and then install cloudsn

```

sudo add-apt-repository ppa:chuchiperriman/cloudsn && sudo apt-get update && sudo apt-get install cloudsn 
```Set-up the details for your mail server; go into preferences and select 'indicate status with: indicator applet'.

In your account details, you can go to 'advanced' and tell it to execute command 'thunderbird'.

I had to log-out and log-in again before it integrated with the indicator-applet mail icon.

If anyone tests this please give feedback.  I tried a number of things  to get this to work yesterday, and I might have forgotten one of the  steps. I will probably make it a little how-to since so many people want  this feature.

(I wasn't happy with mail-notification because it had such a large  number of dependencies, and put a bunch of evolution stuff that I didn't  want.)


---

### Post by Subito Piano on 2011-02-06
Hmm -- i saw that about CloudSn yesterday, too -- after frogging around for like 6 hours (for a notifier applet?!?!?!  NOT a good use of time!)

Anyway, i'd like to just do the Mozilla plug-in but it's not working in my 10.04 (Ubuntu Studio based on 10.04).  I saw yesterday that i am not alone in this.  Anyone else using 10.04 with success?  Or anyone know of a fix?

Thanks!

---

### Post by ebcovert3 on 2011-02-07
I got the same error about the Thunderbird XPI. What I noticed was that it was trying to load it under Firefox, not Thunderbird. I downloaded it and then manually installed it in Thunderbird via the ADD-ONS > INSTALL button. 

After that it worked like a champ.

---

### Post by Subito Piano on 2011-02-07
Thanks, but i did install through T-bird the first time, but it does not work...?!?!?

---

### Post by Subito Piano on 2011-02-08
Say, i got thinking -- i have Ubuntu Studio and i never had a "green" envelope -- mine always was white but when i got mail the envelope had a number in it -- the number of unread mails.  Perhaps i need to uninstall some Ubuntu Studio package or some custom package, and install an equivalent Ubuntu package to get that green envelope that doesn't look for a number to work -- ???!?!

---

### Post by BenB1 on 2011-02-14
> shortcut144**Howto: Add thunderbird to Indicator Applet** 			
 			 			 		   		 		 		This has worked  for me to far on Karmic.  I think it would be the same if any other  versions use the indicator applet.  If you would also like to have  notification from libnotify, follow ...

Works fine on Lucid. :cool::) Thank you.

---

### Post by kuriosity on 2011-04-30
Thanks!, 'needed this. I now have thunderbird on my indicator applet :)

But, is there a way to add "Compose New Message" option under thunderbird? so that i can directly jump to composing a new email message via thunderbird.

---

### Post by Subito Piano on 2011-04-30
You mean in your tray?

---

### Post by kuriosity on 2011-05-01
> **Subito Piano said:**
> You mean in your tray?

Well, more like a drop down indicator applet.. which notifies the number of unread mails on thunderbird.. and also an option wherein i can jump directly to composing a new TB email..

thanks..

---

### Post by Rodney9 on 2011-05-01
Thank You, this worked perfectly in Xubuntu 11.04

---

### Post by danjaredg on 2011-05-09
May be you can try this addon [ThunderUbuntu]("http://danjared.wordpress.com/proyectos/ubuntu-thunderbird/")

[IMG]http://danjared.files.wordpress.com/2011/05/thunderubuntu.png[/IMG]

---

### Post by geazzy on 2011-05-09
great tips...
I'll try it :D

---

### Post by beegary on 2011-05-09
> **danjaredg said:**
> May be you can try this addon [ThunderUbuntu]("http://danjared.wordpress.com/proyectos/ubuntu-thunderbird/")
 
 
Looks great
Is there a 32bit 11.04 version aavailable/planned?

---

### Post by danjaredg on 2011-05-09
of course, today or tomorrow, I need install Ubuntu 11.04 32 bits on virtual machine, to make the addon

---

### Post by beegary on 2011-05-09
Ideal, thank you very much, Ill give it a shot as soon as you have it.

---

### Post by danjaredg on 2011-05-09
The [ThunderUbuntu]("http://danjared.wordpress.com/proyectos/ubuntu-thunderbird/") Addon for Ubuntu 11.04 is now in 32 bit.

[IMG]http://danjared.files.wordpress.com/2011/05/thunderubuntu.png[/IMG]

---

### Post by beegary on 2011-05-10
I have installed the 32bit 11.04 version and it is working very well thank you [danjaredg]("http://ubuntuforums.org/member.php?u=626397").
I have one minor correction in your instructions: the terminal commands for removing evolution have a capitalised S for Sudo - it should all be lower case for those copy and pasting (Lazy people like me!)

---

### Post by dave0109 on 2011-08-11
I finally got this working on Ubuntu 11.04 and Thunderbird 5. Note that I'm running the Ubuntu Classic desktop, not Unity, but I have added the "Indicator Applet Complete" to the panel.

1) Run Thunderbird, if not already.
2) Go to Tools -> Add-ons
3) Click on Get Add-ons, if not already selected
4) Enter 'Messaging Menu' into the search box and install the "Messaging Menu integration" extension.  At this time of writing, it's at v0.6
5) Restart Thunderbird

At this point, the Message applet menu shows:
* Thunderbird Mail/News
* Contacts
* Compose New Message

The envelope icons turns blue when a new mail arrives and the applet menu indicates how many new messages I have in a given folder.

Just what I wanted. :)

---

### Post by Z06Gal on 2011-08-14
> **dave0109 said:**
> I finally got this working on Ubuntu 11.04 and Thunderbird 5. Note that I'm running the Ubuntu Classic desktop, not Unity, but I have added the "Indicator Applet Complete" to the panel.

1) Run Thunderbird, if not already.
2) Go to Tools -> Add-ons
3) Click on Get Add-ons, if not already selected
4) Enter 'Messaging Menu' into the search box and install the "Messaging Menu integration" extension.  At this time of writing, it's at v0.6
5) Restart Thunderbird

At this point, the Message applet menu shows:
* Thunderbird Mail/News
* Contacts
* Compose New Message

The envelope icons turns blue when a new mail arrives and the applet menu indicates how many new messages I have in a given folder.

Just what I wanted. :)


Thank you so much for posting this!  I have been searching for something like this and didn't even think about the how to section of the forum.  Lol


Robin

---

### Post by tx99h4 on 2012-03-20
Thanks, it worked for me :-)

(ubuntu 10.10)

---

### Post by WorldsEndless on 2012-05-17
I'm hoping for a solution to this problem in 10.04 (gnome) so that my messaging icon in the Indicator App will show properly. The ThunderUbuntu looks like what I want, except that I would like English. All of the old solutions seem to apply to Thunderbird <=5 , and i am now running Thunderbird 12. I've been searching for quite a while; can anybody point me in the right direction? 

(ubuntu 10.04)

---

