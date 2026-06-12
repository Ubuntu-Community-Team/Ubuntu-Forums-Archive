---
title: "use Skype with Jaunty notifcations (notify-osd)"
date: 2009-05-02
forum: Tutorials
---

### Post by Lightbreeze on 2009-05-02
I wrote a python script to use the new notification system introduced in Jaunty and now I have updated it use work with later releases of Ubuntu.

 * Notifies when a contact comes online, when they have a birthday soon or when a file transfer is completed.. And when they send you a message new text is appended in the notification bubble. Of course, message notifications are only shown if the conversation doesn't have focus.
 [COLOR="Green"]*[/COLOR] We now support the Messaging Menu, simply run skype-dbus-service.py. Although for some reason (?) the envelope doesn't go green.[IMG]http://imgur.com/rczxJ.png[/IMG]

Hope someone finds it useful and this is how to install the script:
 * Download the files by typing into a terminal
```
bzr branch lp:skype-notify
```
 * open Skype -> menu (the Skype icon in the lower left) -> Options
 * Press 'Notifications' then 'Advanced View'
 * [x] Mark 'Execute the following script on _any_ notification'
 Paste```
python ~/skype-notify/skype-notify.py -e"%type" -n"%sname" -f"%fname" -p"%fpath" -m"%smessage" -s%fsize -u%sskype
```
 * you can enable and disable individual notifications: just uncheck "Display pop-up notification"
[IMG]http://imgur.com/UUd4Zl.png[/IMG]
 * Press 'Apply'

---

### Post by jpeddicord on 2009-05-11
Approved; thank you for your tutorial contribution. :)

---

### Post by Tibuda on 2009-05-12
Thanks, I'll try it now.

---

### Post by valerie-23 on 2009-06-11
Nice work!

I'm not a Python developer, but I'm wondering if there's scope for detecting if a particular Skype chat has focus, and suppressing the notifications if so? It's kind of distracting seeing the notification pop up when you're already in the chat window. I'd personally only like to see a chat notification if I was in another application. 

Is this info sent in the variables sent in the events?

---

### Post by Lightbreeze on 2009-06-11
valerie-23: I have a rough script working to do what you ask. If the window is unfocused it will notify and add an indicator - which will disappear if the chat gains focus before the indicator is clicked.  I'll re-look over the code and clean it up a bit then post it here in a few days.

Glad that someone else finds it useful :D

---

### Post by valerie-23 on 2009-06-11
Awesome! I tend to miss the default Skype notifications that pop up (they're too small!), so using the new notifier is really useful.

I'll look forward to your updated script :)

---

### Post by RD1 on 2009-06-11
Could someone please do this for Thunderbird? Please!?

---

### Post by asilvan on 2009-06-15
it works perfect for me

thank you!!!

[CENTER] =D>=D>=D>=D>=D>[/CENTER]

---

### Post by Pate_Toni on 2009-06-27
> **RD1 said:**
> Could someone please do this for Thunderbird? Please!?

hi,

here you can find an experimental version of a notify for thunderbird. check it out:

[https://launchpad.net/libnotify-mozilla]("https://addons.mozilla.org/de/thunderbird/addon/11530")

it works very well and i don't have any trouble with that add-on.

cu
Pate

---

### Post by mirhciulica on 2009-06-27
thank you! :popcorn: =D>=D>=D>=D>

---

### Post by RD1 on 2009-06-27
Thanks, Pate  I'll give it try. :)

---

### Post by Lightbreeze on 2009-06-28
So now I have 2 files
1) skype-dbus-service.py
2) skype-notify.py **modified**

#1 (skype-dbus-service.py) runs in the background and waits for #2 to send it notifications. This means we can use the indicator-applet and append messages to an existing notification bubble.

Major Changes
[COLOR="Purple"]*[/COLOR] Notifications are now not shown if the chat window has focus
[COLOR="Purple"]*[/COLOR] New messages are added to the indicator-applet until clicked or the chat window is clicked

**Instructions**

 * Download the attachments and save to your Home Folder
 * open Skype -> menu (the skype icon in the lower left) -> Options
 * Press 'Notifications' then 'Advanced View'
 * [x] Mark 'Execute the following script on _any_ notification'
 Paste```
python /home/*your-ubuntu-login-name*/skype-notify.py -e"%type" -n"%sname" -f"%fname" -p"%fpath" -m"%smessage" -s%fsize -u%sskype
```
 * you can enable and disable individual notifications: just uncheck "Display pop-up notification"
 * Press 'Apply'

**Now**
 * In the panel, open System > Preferences > Startup Applications
 * Click 'Add'.
 * For 'Command' enter: ```
python ~/skype-dbus-service.py
```
 * For 'Name' enter "Skype Nice Notifications"
* Press 'Save'

**Make sure to install the package [COLOR="Purple"]python-indicate[/COLOR]**

Now skype-dbus-service.py will run when your computer starts, adding 'Skype' to the indicator-applet and awaiting messages from your friends!!!!

---

### Post by sensimilla on 2009-06-29
Thanks for the script, it seems to be working well for me.

It took me a while to work out that I had to install the package **python-indicate** before it would work. Probably a good idea to mention it in the tutorial.

---

### Post by Pate_Toni on 2009-07-01
well. i have a problem with that script, it don't work. how can i find out, if the "skype-dbus-service.py" is running? maybe it isn't running and this is the solution for my problem. 

[UPDATE] and i installed the package "python-indicate" [/UPDATE]

thanks

---

### Post by lukeen on 2009-07-02
hey thank you so much for this script!

a little suggestion:
wouldn't it be better to start the dbus-service file on login and stop it on logout of skype? and not on login to the system.
you could add that where you check the event type. or it could be checked with every event if the service is running and if not start it...

oh, and i translated it into german and figured out the umlauts have to be escaped with there unicode hex and putting the u before the string like *u"Gespr\xE4ch beendet"*. this should work in a better way. maybe you could then also make all strings variables so they are easy to translate...

---

### Post by Lightbreeze on 2009-07-02
Sorry, I know this isn't prefect. I haven't put a lot of time into testing this or making it easy to use; it was just a personal annoyance I was trying to fix. I will put a lot more effort into making this seamless, especially focusing on what lukeen has suggested, but that might not be for a few weeks.

Now, Pate_Toni, if you run skype-dbus-service.py in the terminal - rather than at system startup - you might see what is wrong, possibly a package missing. If 'Skype' appears in the indicator-applet the script should be working.

Report any bugs you find and hopefully I'll get into fixing them soon, thanks!

---

### Post by Lightbreeze on 2009-07-02
Oh, thanks lukeen for the translation. I'll setup translations properly with variables in the near future.

Thank you all!

---

### Post by MastroPino on 2009-07-12
> **Lightbreeze said:**
> So now I have 2 files
1) skype-dbus-service.py
2) skype-notify.py **modified**

*[...]*

Now skype-dbus-service.py will run when your computer starts, adding 'Skype' to the indicator-applet and awaiting messages from your friends!!!!

Thanks =D :KS :guitar:

+1

---

### Post by mr_pitchfork on 2009-07-12
Well, shucks!  It works fine, but it won't stop saying there are unread messages, even when there are none.  How do I fix this?

---

### Post by Lightbreeze on 2009-07-18
mr_pitchfork.

Could you give me simple steps how to reproduce this issue? Thanks!

---

### Post by mr_pitchfork on 2009-07-19
Here's an in-depth, comprehensive guide to reproducing my issue:

Get any notification from Skype.  Any at all.

No matter what I do, I can't get it to stop saying I have a new Skype message even if I check the message. : /

This is why I'm trying (but am too lazy) to learn Python.  Sometimes a dev-bro could use help appeasing the masses.

---

### Post by Lightbreeze on 2009-07-27
@mr_pitchfork OK try going to the Skype Options > Chat > 'Create a minimised chat window'.

The script uses libwnck to look for _open_ chat windows. If the chat window isn't listed then it won't open :/

Tell me if that works for when you click on the message in the indicator-applet, thanks!

---

### Post by mr_pitchfork on 2009-07-27
Darn, it didn't work.  I'll do some poking around the .py files.

---

### Post by Lightbreeze on 2009-07-27
Go for it, but it's a mess :P

I'm fixing it up though. The plan is to provide a setup.py file which configures things properly, a skype-notify.sh file which receives the notifications and passes them onto skype-dbus-server.py, or run the server if it needs to.

Dive into it :D

---

### Post by six-geek on 2009-08-07
I am using kubuntu 9.04 and after using ```
python skype-dbus-service.py
``` I get the message: ```
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Traceback (most recent call last):
  File "skype-dbus-service.py", line 20, in <module>
    import wnck
ImportError: No module named wnck
```
I don't really know what the GTK error occurs. Btw if someone know how to fix it please let me know.
But the main problem is the import of wnck. I have already installed the packages  ***libwnck-common*** and ***libwnck22***. Does someone have e hint for me to solve the problem?

---

### Post by Lightbreeze on 2009-08-07
Hmm, try [installing]("apt:python-gnome2-desktop") python-gnome2-desktop.

[update] Sorry, missed you were using Kubuntu. Does Kubuntu even have notify-osd or indicator-applet currently?

---

### Post by six-geek on 2009-08-07
> **Lightbreeze said:**
> [update] Sorry, missed you were using Kubuntu. Does Kubuntu even have notify-osd or indicator-applet currently?
Yeah, there is an osd-notifier-system in kubuntu. Actually I don't know the name but it looks like the ubuntu notifier system. Beyond the error I get the skype notifier osd system working - hopefully.
I got the message that a friend went online. I couldn't test the osd-system whether all notification are working.

---

### Post by six-geek on 2009-08-07
All right, I did some tests. The result is, that I don't get any text message notifications from Skype via ubuntu notifications osd. I guess the text message notification works in ubuntu (GNOME)?

[update] Please let me know if there is something I can edit / install / or do for a further test of the skype-osd-notification in kubuntu.

---

### Post by Capt.Klondyke on 2009-08-26
I downloaded the scripts today & tried them immediately. However, it seems I can't get a notification if I'm receiving a chat message. :(
Can anybody help & point me the direction. What am I doing wrong?

Tks, Klondyke

---

### Post by six-geek on 2009-08-26
Which (k/x)ubuntu are you using?
Did you followed the instructions from post [#12]("http://ubuntuforums.org/showpost.php?p=7530321&postcount=12")?

---

### Post by etapombas on 2009-09-01
put this script in ppa
and make it update from repository

---

### Post by Lozz on 2009-09-04
I can't seem to get this working with the new 2.1 beta. I'm guessing there's a compatibility issue. Has anyone else got it going with Skype 2.1? There's a chance I'm being a real idiot.

---

### Post by six-geek on 2009-09-04
> **Lozz said:**
> [...] Has anyone else got it going with Skype 2.1? [...]
It works with Skype 2.1.0.47 beta with no issues. Before I installed the Skype beta deb from the official website I just removed the previous version of Skype with apt-get. The notification system worked out-of-the-box in combination with Skype 2.1.0.47 beta.

---

### Post by Lozz on 2009-09-04
So I am being a real idiot. Fantastic! I'll give it another go later. Thanks.

---

### Post by SQuark on 2009-09-04
Wow! A new version of Skype for Linux. :o
I never thought I'd see the day...

---

### Post by dc2447 on 2009-09-04
> **SQuark said:**
> Wow! A new version of Skype for Linux. :o
I never thought I'd see the day...

It now has feaytures the mac doesn't :)

Anyways, back on topic.

Anyone know how to change the location of the libnotify popups on the screen?

---

### Post by Tibuda on 2009-09-04
> **dc2447 said:**
> Anyone know how to change the location of the libnotify popups on the screen?

It depends on your notification daemon. If you are using the old notification-daemon you can tweaking gconf-editor (I don't know where, probably /apps/notification-daemon), but if you are using the new notify-osd you can't.

---

### Post by dc2447 on 2009-09-04
> **danielrmt said:**
> It depends on your notification daemon. If you are using the old notification-daemon you can tweaking gconf-editor (I don't know where, probably /apps/notification-daemon), but if you are using the new notify-osd you can't. Yeah _ I am on Jaunty so I guess I am stuck with not being able to change it, which isn't great on dual screens.

Thanks for the info

---

### Post by fragestunde on 2009-09-05
Great Script! Thank you very much for the work!


> **lukeen said:**
> 
oh, and i translated it into german
May I have your translation? Would be more easy than translating it for myself :)
Wirklich!

---

### Post by playmaker on 2009-09-07
Nice work, Lightbreeze, really appreciate it. Notifications are working very nice, only the new message notification, as described by mr_pitchfork, doesn't work as it should, but anyway, your script is just great.

Thank you very much and keep on the good work.

playmaker

---

### Post by _sebastian_ on 2009-09-21
hi all,
seems like the script(s) have evolved since I installed the first version.

Is the code on launchpad by now, any plans. would be much easier to follow up and colaborate/translate :-)

last but def not least: **thank you lightbreeze for the script!**

btw: there are quite a few blogs out there selling the script without giving credit to lightbreeze :-(

---

### Post by mirko_3 on 2009-10-12
Doesn't work in karmic, i understand there's bin an API change... i modified skype-dbus-service.py, substituning indicate.IndicatorMessage() with indicate.Indicator() and now the script runs, but no notifications.

---

### Post by mirko_3 on 2009-10-12
> **mirko_3 said:**
> Doesn't work in karmic, i understand there's bin an API change... i modified skype-dbus-service.py, substituning indicate.IndicatorMessage() with indicate.Indicator() and now the script runs, but no notifications.

My bad, my fix works. I'm so good :)

---

### Post by lukeen on 2009-10-15
so is there any update on that script???
the launchpad pages don't provide anything, no download, no translation posibilities...

** would be awesome if someone could maintain this script.**

---

### Post by _sebastian_ on 2009-10-16
> **lukeen said:**
> so is there any update on that script???
the launchpad pages don't provide anything, no download, no translation posibilities...

** would be awesome if someone could maintain this script.**

I've put the script including earlier versions into a launchpad branch:

[SIZE="3"]**[https://code.launchpad.net/~sebastian-s/+junk/skype-notify]("https://code.launchpad.net/~sebastian-s/+junk/skype-notify")**[/SIZE]

Now you can branch the script with all the earlier versions and we have the option to merge the translation suggestion in post #15

As Jono would say lets make this script more awesome :guitar:

> **mirko_3 said:**
> My bad, my fix works. I'm so good :)

Mirko, I've included your little fix as *version 4* currently the last. So If I understand this right people with the older skype should branch *version 3*.

---

### Post by _sebastian_ on 2009-10-16
Well as I've noticed right now Lightbreeze has registered 
[https://launchpad.net/skype-notify](https://launchpad.net/skype-notify)
already.

So the next step would be to merge my branch into the proper project... *how to do that I must learn...*

---

### Post by Lightbreeze on 2009-10-16
Sorry people, I have been inactive here for too long. I won't be able to do much for a few days, either :(

_sebastian_, that would be great. I've made you a member of the skype-notify-team so that you have permission to push to the main branch.
[SIZE="3"]bzr push lp:skype-notify[/SIZE] should work.

---

### Post by _sebastian_ on 2009-10-17
Done!
code is now in lp:skype-notify

---

### Post by Lightbreeze on 2009-10-17
Care to work on translations? :P

---

### Post by mirko_3 on 2009-10-17
> **_sebastian_ said:**
> 
Mirko, I've included your little fix as *version 4* currently the last. So If I understand this right people with the older skype should branch *version 3*.

No, it's people with karmic who should use "my" fix i believe.

---

### Post by mirko_3 on 2009-10-17
So I believe you should have two versions, one for Karmic and one for previous ubuntus. Also, there are two instances indicate.IndicatorMessage(), and you only changed one.

---

### Post by Lightbreeze on 2009-10-17
_sebastian_, just find "indicate.IndicatorMessage()" and replace with "indicate.Indicator()".

indicate.Indicator() should work on both Karmic and Jaunty.

[SIZE="1"]I'm having some problems with bzr and feeling a little frustrated :(. Thanks for your help[/SIZE]

---

### Post by Lightbreeze on 2009-10-17
> **Lightbreeze said:**
> indicate.Indicator() should work on both Karmic and Jaunty.

Ah, scratch that :/

---

### Post by _sebastian_ on 2009-10-17
once we know what works where we can create versions or branches...

I would be happy to work on a translation but ... I'cant code (much) :-/

---

### Post by dasnarr on 2009-10-23
in karmic everything is working for now, only the new message stuff is still displayed as a standard skype popup, did anybody fix this?

---

### Post by lukeen on 2009-10-23
> **dasnarr said:**
> in karmic everything is working for now, only the new message stuff is still displayed as a standard skype popup, did anybody fix this?
you have to disable that in the skype options yourself.

---

### Post by wgradkowski on 2009-10-29
Hi,

you could add the missing event handling for SMS notifications in skype-notify.py

here is the code:

```

elif o.type == 'SMSSent': self.showNotification(o.sname,"SMS sent","skype")
elif o.type == 'SMSFailed': self.showNotification(o.sname,"SMS failed","error")

```

Cheers :)

---

### Post by _sebastian_ on 2009-10-30
thx, will try to include/merge this one

---

### Post by riseringseeker on 2009-11-02
> **Lightbreeze said:**
> 
 * For 'Command' enter: ```
python /home/*your-ubuntu-login-name*/skype-dbus-service.py
```
 * For 'Name' enter "Skype Nice Notifications"
* Press 'Save'

**Make sure to install the package [COLOR="Purple"]python-indicate[/COLOR]**

Now skype-dbus-service.py will run when your computer starts, adding 'Skype' to the indicator-applet and awaiting messages from your friends!!!!

Wouldn't it be easier to make the line:
```
python ~/skype-dbus-service.py
```
instead of ```
python /home/*your-ubuntu-login-name*/skype-dbus-service.py
```

just a thought...

---

### Post by Lightbreeze on 2009-11-02
corrected.

---

### Post by kehan on 2009-11-03
Thanks so much for this - works like a charm as far as I can tell on 9.04 with skype(Beta) 2.1.047

---

### Post by Lightbreeze on 2009-11-03
Apparently the Skype people are working on an open source client. Which means even if they don't start using proper notifications we can release a patched version.

... but if they actually do open source then we should eventually see Empathy / Pidgin use the Skype protocol directly.

---

### Post by Lightbreeze on 2009-11-03
> **kehan said:**
> Thanks so much for this - works like a charm as far as I can tell on 9.04 with skype(Beta) 2.1.047
kehan: glad to be of service

---

### Post by MattMOnkey on 2009-11-03
Getting following error if running skype-dbus-service.py:

```

** (skype-dbus-service.py:11559): WARNING **: Trying to register gtype 'WnckWindowState' as flags when in fact it is of type 'GEnum'

** (skype-dbus-service.py:11559): WARNING **: Trying to register gtype 'WnckWindowActions' as flags when in fact it is of type 'GEnum'

** (skype-dbus-service.py:11559): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as flags when in fact it is of type 'GEnum'
Traceback (most recent call last):
  File "/home/mr/.Skype/skype-dbus-service.py", line 197, in <module>
    dummy()
  File "/home/mr/.Skype/skype-dbus-service.py", line 180, in dummy
    indicator = indicate.IndicatorMessage()
AttributeError: 'module' object has no attribute 'IndicatorMessage'

```Using Karmic, package python-indicate is installed. Any idea?

My fault. Didn't changed IndicatorMessage to indicate.Indicator() . Sorry!

---

### Post by Vermind on 2009-11-13
search and replace in skype-dbus-service.py:
IndicatorMessage -> Indicator
or just do this
```
cat skype-dbus-service.py | sed -e "s/IndicatorMessage/Indicator/g" > skype-dbus-service-fixed.py
```
It seems that the name of the thing that you add into the indicator applet is now Indicator instead of IndicatorMessage, which is sort of a more appropriate name...
Also, for Pidgin users, there is [The Skype Plugin for Pidgin]("http://eion.robbmob.com/").

---

### Post by _sebastian_ on 2009-11-14
OK, so I've updated the branch to include recent comments/additions

**get it from [launchpad.net/skype-notify]("https://launchpad.net/skype-notify") by**

```
bzr branch lp:skype-notify
```

---

### Post by ruru on 2009-11-21
Many thanks, the new notifications work great!
But is there a way to turn the OLD ones off? Did I miss something when I set it up? I now get both sets of notifications, which is a bit superfluous! 
I'm running Ubuntu Karmic.

---

### Post by _sebastian_ on 2009-11-21
Hi ruru,
not sure which notifications you are reffering to as old ones but if you mean the Skype native notifications its easy.
You can turn the native Skype notifications off. You have to do this for each type of notification.

Just remove the tickbox 'Display Popup notification'
[[IMG]http://img694.imageshack.us/img694/8933/screenshotoptions.th.png[/IMG]](http://img694.imageshack.us/i/screenshotoptions.png/)

---

### Post by dc2447 on 2009-12-18
I am going to try and use this script as the basis for XMPP / Jabber notification integration.

It looks pretty easy to convert showNotification to either squirt the message to XMPP or do a notification

---

### Post by Lightbreeze on 2009-12-18
I'm a little confused what you're planning to do...?

---

### Post by dc2447 on 2009-12-19
> **Lightbreeze said:**
> I'm a little confused what you're planning to do...?

I use XMPP as my IM of choice.

I use XMPP transports fopr MSN etc, so I can talk to people on other networks.  For various reasons this is better for me than using pidgin with multiple accounts enabled.

Unfortunately there is no skype transport for XMPP.  I was going to run a copy of skype somewhere and modify the script to send all incoming chat messages to my google talk account

~/notify.py %type %sskype %message

Now I realise that I wouldn't be able to reply to messages pushed to my Google talk account but I would know someone messaged me (I have google talk on my phone) and also have a web archive of incoming messages in gmail.

Still struggling with getting anything working though.

if I have a simple script to just do

sendxmpp [email]myname@googletalk.com[/email] $1 $2

I get nothing 

if I put 

sendxmpp [email]myname@googletalk.com[/email] %sskype %message

in my script I get %sskype %message in the message, the variables aren't expanded.

Need to look at the script again

---

### Post by ashcroft3000 on 2010-01-24
Hey guys!

I'm running the latest Skype Beta 2.1.0.81 under Karmic. I grabbed and configured the latest bazaar version, also patched the service script ("IndicatorMessage" -> "Indicator"). Now everything works nicely, except for notifications on new (and sent) messages. Nothing happens on these events. That is, Skype's own popups still work if activated but skype-notify remains silent.

Anybody facing the same issues?

---

### Post by paulinchen on 2010-01-25
Yes me too. I don't know why, seems like it depends on the new skype beta

---

### Post by paulinchen on 2010-01-25
does no one have a hint to solve this problem?

---

### Post by flanaganboy on 2010-01-26
IT works fine :-)
is it possible to show the avatare of the skype contakt instead of the skype logo?
LG F.

---

### Post by paulinchen on 2010-01-26
> **flanaganboy said:**
> IT works fine :-)
is it possible to show the avatare of the skype contakt instead of the skype logo?
LG F.

You really can see the textmessage itself in the osd? Do you use 32bit or 64bit? Cause I'm using 64bit of the new skype 1.0.81 beta and I don't get the text notify.

---

### Post by flanaganboy on 2010-01-26
ohohhoohhohoho.....
Well i'm using 64 bit and 
and you can make an uptdate...

[http://www.skype.com/go/getskype-linux-beta-ubuntu-64](http://www.skype.com/go/getskype-linux-beta-ubuntu-64)

---

### Post by paulinchen on 2010-01-26
thats the skype version I already have installed, don't know what the probelm is, cause all the other notifications like if a conatct goes on or offline does show up correct.

this is the notfication command i use to start the script:

```
python /home/xxx/.Skype/skype-notify.py -e"%type" -n"%sname" -f"%fname" -p"%fpath" -m"%smessage" -s%fsize -u%sskype
```Maybe there is the problem?

---

### Post by paulinchen on 2010-01-26
got it working now, changed the service-script back to original.
Reboot.
Changed the Indicator in the script reboot again and now it works. 

Strange...

---

### Post by paulinchen on 2010-01-26
I was so happy got the notify-osd working, that I translated it into german. ( I read that someone else wants to have it);)

---

### Post by dmakreshanski on 2010-02-20
I have modified a bit the skype-dbus-service.py file so that it doesn't show notifications for incoming messages when the chat window with the corresponding user is active.

Cheers

**edit: ** This has issues when there's a group conversation, because the name of contact is not displayed in the window's title, and I don't know about the Skype API enough to figure out another way to get the window of the originating event.
By the way, this also affects the case for getting the window in focus with the indicator.

---

### Post by Lightbreeze on 2010-02-22
Yes, the window matching is terrible :/

---

### Post by Lightbreeze on 2010-02-22
Maybe you would all like to follow this Skype bug: [https://developer.skype.com/jira/browse/SCL-502](https://developer.skype.com/jira/browse/SCL-502)

---

### Post by paede on 2010-03-22
> **six-geek said:**
> I am using kubuntu 9.04 and after using ```
python skype-dbus-service.py
``` I get the message: ```
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Traceback (most recent call last):
  File "skype-dbus-service.py", line 20, in <module>
    import wnck
ImportError: No module named wnck
```I don't really know what the GTK error occurs. Btw if someone know how to fix it please let me know.
But the main problem is the import of wnck. I have already installed the packages  ***libwnck-common*** and ***libwnck22***. Does someone have e hint for me to solve the problem?

Same Problem:

patrick@patrick-laptop:~$ /opt/skype-notifiy/skype-dbus-service.py 
Traceback (most recent call last):
  File "/opt/skype-notifiy/skype-dbus-service.py", line 20, in <module>
    import wnck
ImportError: No module named wnck

---

### Post by nexus_dublin on 2010-03-23
**paede**, did you try
```
sudo apt-get install python-wnck
``` 

**Lightbreeze**, thank you so much for your excellent work! Keep it up!

---

### Post by Kooster on 2010-04-13
The only time the chat osd comes up is when I typed in a terminal python skype-dbus-service.py. Then it reads "Listening" without errors and all works great. But after I close the terminal all goes haywire again. To rely on Skype's small osd is useless. I followed every step and still no good.

PLEASE HELP!!!

---

### Post by manoriax on 2010-04-26
Great script, thanks.

---

### Post by Gondlar on 2010-05-15
I just found this via Google and tried to install it... but for some reason its not working.
skype-dbus-service.py exits instantly with the message:
```
** (skype-dbus-service.py:6798): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (skype-dbus-service.py:6798): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (skype-dbus-service.py:6798): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/home/<my_name>/bin/skype-notify/skype-dbus-service.py", line 197, in <module>
    dummy()
  File "/home/<my_name>/bin/skype-notify/skype-dbus-service.py", line 180, in dummy
    indicator = indicate.IndicatorMessage()
AttributeError: 'module' object has no attribute 'IndicatorMessage'
```I am running Ubuntu Lucid. I hope someone can help me

EDIT: OK, I forgot to change the indicate.IndicatorMessage() thing... by the way in [this bug]("https://answers.launchpad.net/gm-notify/+question/89861") for gm-notify it is suggested to use the following Code: ```
indicator = getattr(indicate, 'IndicatorMessage', indicate.Indicator)()
``` I do not "speak" python so I just wanted to tell you.
And it seems that server_display and display get a second argument on my system

---

### Post by xyepblra on 2010-05-28
Worked almost like a charm for me, but:
1. notification doesn't show text of a message; should I edit the Skype settings to make the message text displayed in the notification?
2. is there any way to make userpics displayed in the notifications?

---

### Post by _sebastian_ on 2010-06-07
> **RD1 said:**
> Could someone please do this for Thunderbird? Please!?

hi have a look at the [Gnome Integration]("https://addons.mozilla.org/en-US/thunderbird/addon/123887/") Add-on

There is a [Gnome Open]("https://addons.mozilla.org/en-US/thunderbird/addon/12523/") Add-on as well

---

### Post by _sebastian_ on 2010-06-07
Hi all,

I've updated the launchpad branch to include the German translation y [Paulinchen]("http://ubuntuforums.org/showpost.php?p=8728041&postcount=80") and the patch from [dmakreshanski]("http://ubuntuforums.org/showpost.php?p=8856752&postcount=81")

**[COLOR="SeaGreen"]to all the other rockstars[/COLOR]** :guitar: 
if you've got coding/python skills and have suggestions for modifications **bring 'em on**

please provide a diff file, [use]("http://stephenjungels.com/jungels.net/articles/diff-patch-ten-minutes.html") ```
diff -u original.py new.py > original.patch
```

---

### Post by _sebastian_ on 2010-06-07
> **Gondlar said:**
> I do not "speak" python so I just wanted to tell you.
And it seems that server_display and display get a second argument on my system

neither do I but I hope someone will help !

---

### Post by yolandi on 2010-06-15
thx! very useful!

---

### Post by yolandi on 2010-06-16
> **yolandi said:**
> thx! very useful!
is it possible to switch out the notification when i am sending  messages? 
maybe with deleting something from the python code or from the script? 

need help, me is a newbee....

---

### Post by xyepblra on 2010-06-16
> **yolandi said:**
> is it possible to switch out the notification when i am sending  messages?

need help, me is a newbee....
No need to edit the code, just turn off the unnecessary notifications for each event you don't want to be notified on by editing the notifications settings in Skype.

---

### Post by xyepblra on 2010-07-08
Guys, could somebody please tell me how should I mark up the Cyrillic text of Russian version of the script to enable notifications in Russian?
I tried direct translation, but the script stopped working at all.

---

### Post by _sebastian_ on 2010-07-09
> **xyepblra said:**
> Guys, could somebody please tell me how should I mark up the Cyrillic text of Russian version of the script to enable notifications in Russian?
I tried direct translation, but the script stopped working at all.

from what I know you only need to modify skype-notify.py
If you look at the bzr repository at [http://bazaar.launchpad.net/~skype-notify-team/skype-notify/trunk/files](http://bazaar.launchpad.net/~skype-notify-team/skype-notify/trunk/files)

have a look and compare **skype-notify.py** and **skype-notify.DE_de.py**

you should be able to figure out which are the locations to replace with you language. you should use an editor with code highlighting to easily go through the code

---

### Post by TairKZ on 2010-07-17
Guys, I am using Ubuntu Lucid. It doesnt work at all. I did everything as said. Installed python-indicate and python -wnck. Got the branch by: bzr branch lp:skype-notify
Also when I run "python skype-dbus-service.py" it shows:
** (skype-dbus-service.py:2390): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (skype-dbus-service.py:2390): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (skype-dbus-service.py:2390): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Listening

What am I doing wrong? Please Help!

---

### Post by shinzo on 2010-07-19
Having the same problem like poster before. When trying to run skype-dbus-service.py in console, I just receive th following error:

[I]** (skype-dbus-service.py:2381): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (skype-dbus-service.py:2381): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (skype-dbus-service.py:2381): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/home/user/skype-dbus-service.py", line 197, in <module>
    dummy()
  File "/home/user/skype-dbus-service.py", line 180, in dummy
    indicator = indicate.IndicatorMessage()
AttributeError: 'module' object has no attribute 'IndicatorMessage'[/I]


Would appreciate if someone could explain it. I'll try to figure out a work-around solution (the trial&error-way) but since I'm new to Ubuntu I have to get used to it first.

And of course, thanks for the scripts so far. Although they don't run till now, I think they're pretty close ;)

---

### Post by sfarbota on 2010-08-11
Same issue as the above two posters..is this an issue with Ubuntu 10.04 perhaps?

EDIT: Nevermind, forgot to fill in my user name in the script line!

---

### Post by mbonera on 2010-09-23
I wrote a quick'n'dirty solution for Lucid Lynx. It's not written in python, it's just a bash script and it's not handling all events, but it seems to works well. 

You have just to save the script in /usr/local/bin/ and change some settings in Skype:
# Open Skype menu (the skype icon in the lower left) 
# Choose Options
# Press 'Notifications' then 'Advanced View'
# Flag 'Execute the following script on any notification' 
# In the field enter this (all in one line): /usr/local/bin/skype-notify.sh -e "%type" -n "%sname" -f "%fname" -p "%fpath" -m "%smessage" -s %fsize -u %sskype
# Press Apply and enjoy it!

Please let me know if it works for you.

---

### Post by numberX on 2010-09-26
Hey mbonera,
thank you for that script.
For me (Lucid Lynx) it's working very well. But I had to install libnotify-bin first.

Thank you.

---

### Post by ziocane1 on 2010-10-23
Hi everybody,

I launched the script under lucid, and I've got two questions:

1- I've got a launcher on the notifications-applet, but I have another icon on the panel... How can I remove it?

2- if I close skype with X it will resize as icon, but if I click in the icon of the notifications-applet it will launch another instance of the program...it shouldn't restore the full screen window?

Tnx!

---

### Post by markoer on 2010-10-24
```
1- I've got a launcher on the notifications-applet, but I have another icon on the panel... How can I remove it?

2- if I close skype with X it will resize as icon, but if I click in the  icon of the notifications-applet it will launch another instance of the  program...it shouldn't restore the full screen window?

Tnx!
                                                                                                  [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                                                                                                                      [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=10015046")
```1. you can't remove skype icons from notification-applet, there is no way to that right now

2. you can solve this issue by downloading this skype API plugin from here, which will allow only one skype instance

```
http://forum.skype.com/index.php?showtopic=332401
```and then if you use nitify-OSD scripts posted in this thread you need to write bash script to exicute all of them in some order.

hope this helps

---

### Post by ziocane1 on 2010-10-24
Thank you!

---

### Post by klikka on 2010-11-09
Hi mbonera

I tried to test your script on Maverick (10.10) but couldnt get it to work. I have installed the libnotify-bin, copied the skpe-notify.sh to /usr/local/bin and entered the line in the skype options.

Could it perhaps be something I have missed?

---

### Post by klikka on 2010-11-09
It works fine if I use the "execute the following script" option and writes in the notify-send command I want.

For example on "chat message received":
notify-send "%sname: %smessage" -i skype

The only problem is if someone sends multiple messages fast it will not display the second messages before the first has timed out. If it were possible to "clear" the notify-send window before every send I think it would solve it, but I don't know if this excist.

---

### Post by markoer on 2010-11-23
when massages arrives indicator doesn't remove them from applet list. clicking on arrived massage doesn't have any function at all. this is the exact output which i get when trying to click on arrived massages. 

```
TypeError: server_display() takes exactly 1 argument (2 given)
```

with this scripts, I use two more scripts, one is to take status from pidgin, and another one is to allow only one instance of skype.

everything else runs smoothly.

anyone?

---

### Post by Lightbreeze on 2010-11-29
@markoer: That's fixed in the latest script. You can get it by typing into a terminal:
```
bzr branch lp:skype-notify
```

---

### Post by markoer on 2010-12-01
Lightbreeze:

now i recive this when activating recived msg window through indicator massages applet,
```
File "skype-dbus-service.py", line 101, in display_cb
    window.activate(int(time.time()))
AttributeError: 'NoneType' object has no attribute 'activate'

```

and another thing is that skype-notify.py display recived chat msg if chat windows is focues or closed, so it always diplay notification, in skype-dbus-service.py, version before this was fixed.

thx in advance

---

### Post by ledzpg on 2011-01-12
Hi,

I'm new to Ubuntu 10.10, the last version I've used was the 6.06, after that I've been using the OpenSuSE, but now I've switched back to Ubuntu.

I wasn't able to make it work here.
I've made the following:

1) Created the OpenPGP and the SSH keys at launchpad
2) Ran "bzr branch lp:skype-notify" on terminal
3) Put the code on skype

Didn't worked, so...

4) Installed the package libnotify-bin

I re-check that the packages python-indicate and python-wnck were installed, but still not working.

Also, I have tried the script created by **mbonera**, but it didn't worked too. :(

Any ideas?

Thanks,
Luiz

---

### Post by markoer on 2011-01-13
ledzpg, you need to install python-skype

---

### Post by ledzpg on 2011-01-13
Thanks!
I'll try here.

---

### Post by ledzpg on 2011-01-13
Still not working :(

Any other idea? :confused:

---

### Post by markoer on 2011-01-14
you need to apt-get install python-skype python-wnck python-indicate to be installed

maybe you need python-gnome-desktop or python-gnome2-desktop, tray searching on google for exact name in apt repos and install it

---

### Post by ledzpg on 2011-01-14
Thank you, **markoer**.

The packages python-skype, python-wnck, python-indicate are installed. I'll check the others tonight when I come home. ;)

---

### Post by Whoopie on 2011-01-14
Hi,

I'm also running Maverick and tried skype-notify. It works great, thanks for it!

I had a look at the way how the dbus service is started. Dbus now offers a way to autostart services:
```

$ cat /usr/share/dbus-1/services/skype-notify.service 
[D-BUS Service]
Name=org.skypenotify.Service
Exec=/path/to/skype-dbus-service.py

```This works somehow, but only for the second notification as skype-notify.py doesn't wait until the service is started properly. I'm not that experienced with dbus, so maybe someone knows a way to fix it.
Perhaps, the connection to the dbus service could be established earlier so that it's available as soon as the first notification shall be sent.

Please find attached a patch to update the German version to the latest original version. I also added a German skype-dbus-service.DE_de.py although it just a minor change.

Best regards,
Whoopie

---

### Post by stephanboy2030 on 2011-02-16
> **numberX said:**
> Hey mbonera,
thank you for that script.
For me (Lucid Lynx) it's working very well. But I had to install libnotify-bin first.

Thank you.

Thank also to you for your advice about libnotify-bin.

It works

---

### Post by paulinchen on 2011-04-06
@Whoopie

Can you tell me please how to activate the changes in your patch.
I just took a look at the patch file and found both .py files, but its seems to be they are a kind of incomplete and wrong formated.

Please tell me what I'm doing wrong.

---

### Post by MastroPino on 2011-04-06
Hello mates, 
for make it works I modify the this line 

```
python **/home/m7p/**.skype-notify/skype-notify.py -e"%type" -n"%sname" -f"%fname" -p"%fpath" -m"%smessage" -s%fsize -u%sskype
```

after that I specify the full path it works! 
:popcorn:

---

### Post by not_insane on 2011-04-30
Hi,
I downloaded this script, and it was great but a bit buggy. The  messaging menu didnt light up and the messages didnt show up on the menu  like "echo123 0min" for some reason, and it didnt work if the skype  window was closed and running in the background. So, I tried to improve  it - now the messaging menu lights up, and it uses the cruddy skype dbus  api to integrate better with skype. It also sorta works for group convos, just set the chat topic to include everyone's names as they are on skype. It works for me in both maverick and in natty (after I upgraded).
Please do tell me if it works for you. (attached) See the file called INSTALL for how to install my version. Do not use ~ when replacing the /path/to's, you must use the full path, i.e. /home/username/whatever

What is more, if you are on natty, you can remove skype from unity's top bar completely! All you need to do is open terminal and enter "gsettings get com.canonical.Unity.Panel systray-whitelist" - this will get this current whitelist for the notification tray. You can remove skype from it by doing:

gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'hp-systray']

Ah the joys of open source ^_^

---

### Post by Tekmoor on 2011-05-03
This seems to be working for me so far! I'll let you know if I run into any issues.

I rely on Skype a lot, so thanks not_insane!

---

### Post by paulinchen on 2011-05-04
Can someone tell me, how to remove Skype from the messaging menu?
Tried to delete the .config/applications/ but skype remains the memenu evn now useless.

I'm sorry, it didn't work as expected, don't know why, but no other script notifies me, beside the original one of the thread. I think it has todo with the dbus script, but can't find the error.

---

### Post by syb3ria on 2011-05-09
> **not_insane said:**
> Hi,
I downloaded this script, and it was great but a bit buggy. The  messaging menu didnt light up and the messages didnt show up on the menu  like "echo123 0min" for some reason, and it didnt work if the skype  window was closed and running in the background. So, I tried to improve  it - now the messaging menu lights up, and it uses the cruddy skype dbus  api to integrate better with skype. It also sorta works for group convos, just set the chat topic to include everyone's names as they are on skype. It works for me in both maverick and in natty (after I upgraded).
Please do tell me if it works for you. (attached) See the file called INSTALL for how to install my version. Do not use ~ when replacing the /path/to's, you must use the full path, i.e. /home/username/whatever

What is more, if you are on natty, you can remove skype from unity's top bar completely! All you need to do is open terminal and enter "gsettings get com.canonical.Unity.Panel systray-whitelist" - this will get this current whitelist for the notification tray. You can remove skype from it by doing:

gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'hp-systray']

Ah the joys of open source ^_^

Have you tested it on natty > gnome classic no effects? I followed the install notes but... no success here :confused:

---

### Post by not_insane on 2011-05-10
> **paulinchen said:**
> Can someone tell me, how to remove Skype from the messaging menu?
Tried to delete the .config/applications/ but skype remains the memenu evn now useless.

I'm sorry, it didn't work as expected, don't know why, but no other script notifies me, beside the original one of the thread. I think it has todo with the dbus script, but can't find the error.
  Any specifics? Remember, it wont show up if your status is set to do not disturb. Also, if the original script worked it isnt connecting to the dbus service properly. It should be removed from the messaging menu once you reboot if you deleted the .config/applications directory recursively. Run skype from the command line and when you are meant to get a notification (when the conversation window isn't selected), check the console window and it will tell you if it can connect.
> **syb3ria said:**
> Have you tested it on natty > gnome classic no effects? I followed the install notes but... no success here :confused:
Please give more details - what exactly did you do, and which bits work and which bits dont? Does skype launch when you click the item in the messaging menu? If you run ps aux|grep python|grep -v grep what comes up? Again, try running skype from the command line and check for any messages when you are supposed to get a notification.

---

### Post by bmbaker on 2011-05-21
does anyone know if this will wk in gnome-shell or if anyone knows how to adjust the script to make it wk :-) cheers

---

### Post by Zilvador on 2011-05-22
It works great for me. Good work and thank you! :)

I was wondering if it was possible to make a chat window appear when clicking on the name of contacts that I have chatted with earlier in the message menu. Actually I'm not sure if this was the intention, since the message envelope icon stays blue even after I have opened and read the chat message. It suppose that it should turn white again when nothing is pending.

Edit: Oh..Andrewin of Wedupd8 wrote an installation script and a guide for it which makes it a bit easier to set up btw. See [http://www.webupd8.org/2011/05/skype-ubuntu-messaging-menu-notifyosd.html](http://www.webupd8.org/2011/05/skype-ubuntu-messaging-menu-notifyosd.html)

//Zilvador

---

### Post by not_insane on 2011-05-23
> **bmbaker said:**
> does anyone know if this will wk in gnome-shell or if anyone knows how to adjust the script to make it wk :-) cheers
I don't know, but I dont see why it shouldn't. Do try it and let us know if it works or not!

> **Zilvador said:**
> It works great for me. Good work and thank you! :smile:

I was wondering if it was possible to make a chat window appear when  clicking on the name of contacts that I have chatted with earlier in the  message menu. Actually I'm not sure if this was the intention, since  the message envelope icon stays blue even after I have opened and read  the chat message. It suppose that it should turn white again when  nothing is pending.

Edit: Oh..Andrewin of Wedupd8 wrote an installation script and a guide for it which makes it a bit easier to set up btw. See [http://www.webupd8.org/2011/05/skype-ubuntu-messaging-menu-notifyosd.html](http://www.webupd8.org/2011/05/skype-ubuntu-messaging-menu-notifyosd.html)

//Zilvador
It is meant to only show unread messages, and due to a limitation in the skype api I can't fully support group conversations. If the chat window opens, then is it a group conversation? If so, it is a known limitation. A quick and dirty workaround is to edit the group conversation topic and set it to the full names of everyone in the conversation. e.g. you might set the topic to "Echo Test Service John Middle-Name Smith" (careful to use the full name as shown in the skype main window and not the skype username!). 

This will make the script work properly, i.e. notification turns message icon blue, you switch to conversation or click the indicator in the messaging menu and the indicator disappears and the message icon turns white again. It works fine for one-on-one conversationsI would work on it a bit more to try and workaround these bugs but I'm currently busy with other things so I will try and improve the script when I have some free time for it!

I also saw that, thanks for the link, I posted in the comments there to help a few people out with problems. I do appreciate that my instructions may be slightly confusing, so I recommend the script there if anyone is struggling with my instructions!

---

### Post by morgengenuss on 2011-05-24
> Actually I'm not sure if this was the intention, since the message envelope icon stays blue even after I have opened and read the chat message. It suppose that it should turn white again when nothing is pending.

i'm also experiencing what zilvador mentions here (envelope stays blue even after reading messages, not group conversations)
i'm not entirely sure whether it's related to your script or the xfce4-indicator-plugin i'm using along with the xfce4-panel. is there any way to test/debug the python script?

---

### Post by bmbaker on 2011-06-03
> **not_insane said:**
> I don't know, but I dont see why it shouldn't. Do try it and let us know if it works or not!


It is meant to only show unread messages, and due to a limitation in the skype api I can't fully support group conversations. If the chat window opens, then is it a group conversation? If so, it is a known limitation. A quick and dirty workaround is to edit the group conversation topic and set it to the full names of everyone in the conversation. e.g. you might set the topic to "Echo Test Service John Middle-Name Smith" (careful to use the full name as shown in the skype main window and not the skype username!). 

This will make the script work properly, i.e. notification turns message icon blue, you switch to conversation or click the indicator in the messaging menu and the indicator disappears and the message icon turns white again. It works fine for one-on-one conversationsI would work on it a bit more to try and workaround these bugs but I'm currently busy with other things so I will try and improve the script when I have some free time for it!

I also saw that, thanks for the link, I posted in the comments there to help a few people out with problems. I do appreciate that my instructions may be slightly confusing, so I recommend the script there if anyone is struggling with my instructions!

well i tried in gnome-shell using Andrew from webupd8's instructions, and No it didn't wk for me , a shame really !

---

### Post by not_insane on 2011-06-04
> **bmbaker said:**
> well i tried in gnome-shell using Andrew from webupd8's instructions, and No it didn't wk for me , a shame really !
Oh, does gnome-shell have a messaging menu? Or are you starting skype from wherever gnome3 lets you start programs from? The script doesnt actually run if you dont use the messaging menu because clicking on the messaging menu item launches it. What you need to do is open up skype-dbus-service.py and find the line that reads 'server_display_cb("startup", 1)' and remove it. This stops skype from starting with the script, and now skype will only start when you start it yourself. Then make the script start on startup (in gnome 2 its by going to system>preferences>startup applications). Now when you launch skype and start talking to someone it should work.

---

### Post by bmbaker on 2011-06-04
> **not_insane said:**
> Oh, does gnome-shell have a messaging menu? Or are you starting skype from wherever gnome3 lets you start programs from? The script doesnt actually run if you dont use the messaging menu because clicking on the messaging menu item launches it. What you need to do is open up skype-dbus-service.py and find the line that reads 'server_display_cb("startup", 1)' and remove it. This stops skype from starting with the script, and now skype will only start when you start it yourself. Then make the script start on startup (in gnome 2 its by going to system>preferences>startup applications). Now when you launch skype and start talking to someone it should work.

coolio thanks i try that next :-)
on another (but related) note John Stowers also did some wk in this direction andrew @ webupd8 posted this today ....
[http://www.webupd8.org/2011/06/gnome3-notifications-for-skype.html#more](http://www.webupd8.org/2011/06/gnome3-notifications-for-skype.html#more)

---

### Post by OakRaider4Life on 2011-06-29
Hi,

I've successfully set up this script with Natty, but for some reason when I minimize my Skype window to the messaging menu, I can't restore it, although it continues to run in the background. Is anyone else having this problem?

---

### Post by Zilvador on 2011-06-29
Yes, it seems to be a known issue. Clicking on the names in the messaging menu doesn't do anything.

---

### Post by not_insane on 2011-07-02
> **OakRaider4Life said:**
> Hi,

I've successfully set up this script with Natty, but for some reason when I minimize my Skype window to the messaging menu, I can't restore it, although it continues to run in the background. Is anyone else having this problem?

> **Zilvador said:**
> Yes, it seems to be a known issue. Clicking on the names in the messaging menu doesn't do anything.

That's not meant to happen. Has the script been authorized by skype to access its api? You should have gotten a popup asking for permissions. Under Options>Public API there should be listed "mySkypeController" under the allowed applications. The script certainly works for me (though I guess I dont count since I developed it :P) and on a clean natty install on using andrew from webupd8's script or my instructions if followed correctly.

---

### Post by Zilvador on 2011-07-03
Yes, it did ask and was approved. The rest also seems to work without trouble, but clicking the names in the menu does nothing.

Edit: Just made a new experiment. It actually does work when there is an unseen conversation, but when the conversation is closed and you try to reopen without any unseen messages, it does not work. Oh...and on a second note...I have tried to rename the conversation into both the user-name and the shown name of the one, I'm chatting with, but the messaging menu icon stays blue no matter what I do.

---

### Post by ianmaciel on 2011-07-06
> **not_insane said:**
> Hi,
I downloaded this script, and it was great but a bit buggy. The  messaging menu didnt light up and the messages didnt show up on the menu  like "echo123 0min" for some reason, and it didnt work if the skype  window was closed and running in the background. So, I tried to improve  it - now the messaging menu lights up, and it uses the cruddy skype dbus  api to integrate better with skype. It also sorta works for group convos, just set the chat topic to include everyone's names as they are on skype. It works for me in both maverick and in natty (after I upgraded).
Please do tell me if it works for you. (attached) See the file called INSTALL for how to install my version. Do not use ~ when replacing the /path/to's, you must use the full path, i.e. /home/username/whatever

What is more, if you are on natty, you can remove skype from unity's top bar completely! All you need to do is open terminal and enter "gsettings get com.canonical.Unity.Panel systray-whitelist" - this will get this current whitelist for the notification tray. You can remove skype from it by doing:

gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'hp-systray']

Ah the joys of open source ^_^

Hi not_insane,

I have just installed it on Natty and it was "almost there". What I was looking for was just a script to highlight the message icon. It does it - later I would try to disable the messages displayed and keep only the icon highlighted.

But I've got and issue:
It does highlight the icon and let me open the chat by clicking on it. But it never turn back to the default icon (the white icon) after the first event. So if I receive any alert from Skype it turns highlighted forever..

Do you you know how to fix it?

Thanks,
Ian

---

### Post by Zilvador on 2011-07-07
> **ianmaciel said:**
> 
But I've got and issue:
It does highlight the icon and let me open the chat by clicking on it. But it never turn back to the default icon (the white icon) after the first event. So if I receive any alert from Skype it turns highlighted forever..

Do you you know how to fix it?


> **not_insane said:**
> 
It is meant to only show unread messages, and due to a limitation in the  skype api I can't fully support group conversations. If the chat window  opens, then is it a group conversation? If so, it is a known  limitation. A quick and dirty workaround is to edit the group  conversation topic and set it to the full names of everyone in the  conversation. e.g. you might set the topic to "Echo Test Service John  Middle-Name Smith" (careful to use the full name as shown in the skype  main window and not the skype username!). 

This will make the script work properly, i.e. notification turns message  icon blue, you switch to conversation or click the indicator in the  messaging menu and the indicator disappears and the message icon turns  white again. It works fine for one-on-one conversationsI would work on  it a bit more to try and workaround these bugs but I'm currently busy  with other things so I will try and improve the script when I have some  free time for it!


He answered it already (: . It is because of an unfortunate limitation in the API.

---

### Post by ianmaciel on 2011-07-08
oh... okay

I missed this answer..


sorry about that...

---

### Post by Comissar on 2011-07-12
On my Natty, for fix problems with "Always blue icon" i changed line 161 in /usr/share/skype-notify-improved/skype-dbus-service.py
in function display_cb() from 
[FONT="Courier New"]if contactsIndicated[i] is contact:[/FONT]
to
[FONT="Courier New"]if contactsIndicated[i] == contact:[/FONT]
And now, if I use username from message system for come to chat window, username disapeared from message menu, and letter icon can be unhilighted. It is not full fix for author's idea, but now it is usable.
Thanks to **not_insane** for this great script and sorry for my bad English and python. I see to python code first time...

---

### Post by n1k0z on 2011-08-31
The script is awesome!

I can confirm that changing the "is" to "==" works.

However, do you know how I can add the skype icon in all notifications?

Thank you!

---

### Post by n1k0z on 2011-09-01
Almost all notifications have the skype icon, or another icon, except incoming chat messages if I am not mistaken.

To correct this (and answer my previous question) go on and replace ling 57 with

```

n = pynotify.Notification(skypename, skypemessage, "skype")

```

which adds a skype icon to the incoming-messages notifications.

Finally, logout and login (or restart service in general) for the changes to take effect.

great script guys! (not_insane++)

---

### Post by Harmageddon on 2011-09-08
I've installed the script by not_insane and it works, but it only works for messages, not if somebody goes online or offline or anything other.

---

### Post by montini on 2011-09-18
Hello everyone, I wanted to figure out if the script is working on oneiric, because when I install it, it says:

```

montini@insecticide:~$ ./skype-notify-messaging
1) Install Skype Messaging Menu / Notifications support
2) Remove Skype Messaging Menu / Notifications support
3) Quit
Please enter an option (1, 2 or 3): 1
[sudo] password for montini: 
--2011-09-18 10:39:39--  http://webupd8.googlecode.com/files/skype-notify-improved.tar.gz
Resolving webupd8.googlecode.com... 74.125.39.82
Connecting to webupd8.googlecode.com|74.125.39.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 117583 (115K) [application/x-gzip]
Saving to: `skype-notify-improved.tar.gz'

100%[======================================>] 117,583      156K/s   in 0.7s    

2011-09-18 10:39:40 (156 KB/s) - `skype-notify-improved.tar.gz' saved [117583/117583]

skype-notify-improved/skype-notify.py
skype-notify-improved/skype-dbus-service.py
skype-notify-improved/skype.desktop
skype-notify-improved/skype
skype-notify-improved/message-new-instant.wav
skype-notify-improved/INSTALL
skype-notify-improved/
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-skype' has no installation candidate
Done. Remember to log out and log back in or else this wont work.
montini@insecticide:~$ sudo apt-get install python-skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-skype' has no installation candidate
montini@insecticide:~$ 

```

It misses 'python-skype'. Is it ok, or a showstopper?

---

### Post by Spaced on 2011-10-12
> **montini said:**
> Hello everyone, I wanted to figure out if the script is working on oneiric, because when I install it, it says:

```

montini@insecticide:~$ ./skype-notify-messaging
1) Install Skype Messaging Menu / Notifications support
2) Remove Skype Messaging Menu / Notifications support
3) Quit
Please enter an option (1, 2 or 3): 1
[sudo] password for montini: 
--2011-09-18 10:39:39--  http://webupd8.googlecode.com/files/skype-notify-improved.tar.gz
Resolving webupd8.googlecode.com... 74.125.39.82
Connecting to webupd8.googlecode.com|74.125.39.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 117583 (115K) [application/x-gzip]
Saving to: `skype-notify-improved.tar.gz'

100%[======================================>] 117,583      156K/s   in 0.7s    

2011-09-18 10:39:40 (156 KB/s) - `skype-notify-improved.tar.gz' saved [117583/117583]

skype-notify-improved/skype-notify.py
skype-notify-improved/skype-dbus-service.py
skype-notify-improved/skype.desktop
skype-notify-improved/skype
skype-notify-improved/message-new-instant.wav
skype-notify-improved/INSTALL
skype-notify-improved/
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-skype' has no installation candidate
Done. Remember to log out and log back in or else this wont work.
montini@insecticide:~$ sudo apt-get install python-skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-skype' has no installation candidate
montini@insecticide:~$ 

```

It misses 'python-skype'. Is it ok, or a showstopper?
'python-skype' is necessary for the script to work. I downloaded the package from here ([http://packages.ubuntu.com/natty/all/python-skype/download](http://packages.ubuntu.com/natty/all/python-skype/download)) and it seems to work.

By the way, although I have removed Skype from the whitelist of the Ubuntu panel, the icon still shows up every time I launch the programme. :confused:

---

### Post by EgoGratis on 2011-10-15
In Ubuntu 11.10 sni-qt package is used for Qt applications indicators and they are not "systray indicators" anymore so if u "whitelist" Skype as "systray indicator" it does not affect Skype anymore! If u remove sni-qt package there will be no Skype indicator, but you will not be able to use other Qt indicators like the one for VLC, but i guess you could "whitelist" them and use them as "systray indicators" if u want, the same way u did it in Ubuntu 11.04.

I manually downloaded and installed package python-skype and used instructions and python script from not_insane and it does work! I just don't get "blue envelope" in Ubuntu 11.10 and i was wondering if this is normal behavior and if there is a "fix" available for this!

---

### Post by EgoGratis on 2011-10-15
Update:

Icon does change color! Basically everything i need is working OK! Thanks to all the people involved that made this work.

---

### Post by Harmageddon on 2011-11-23
The script by not_insane doesn't work anymore for me on Ubuntu 11.10. 

Edit: It works, but still only for chat messages, as I wrote ~2 months ago.

---

