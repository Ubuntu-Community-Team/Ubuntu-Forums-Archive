---
title: "no &quot;add computer&quot; webpage"
date: 2009-09-14
forum: Ubuntu One (CLOSED)
---

### Post by Findarato on 2009-09-14
Hello everyone,

I have installed ubuntu one on my desktop and my laptop, both running ubuntu jaunty 9.04. The installation went flawless, but the last step is giving me a lot of trouble : adding a computer to start sharing files...

On the website, it is said that, once you have ubuntu-one installed, when you launch it the first time, you automaticaly get taken to a website to add your computer. The problem is that this does not happen with me and I cannot find ANY manual way to get to that page (no reference on the web I could find whatsoever).

I would appreciate it if someone knows the answer to this one.

Findarato

---

### Post by joshuahoover on 2009-09-15
> **Findarato said:**
> Hello everyone,

I have installed ubuntu one on my desktop and my laptop, both running ubuntu jaunty 9.04. The installation went flawless, but the last step is giving me a lot of trouble : adding a computer to start sharing files...

On the website, it is said that, once you have ubuntu-one installed, when you launch it the first time, you automaticaly get taken to a website to add your computer. The problem is that this does not happen with me and I cannot find ANY manual way to get to that page (no reference on the web I could find whatsoever).

I would appreciate it if someone knows the answer to this one.

Findarato

Hi Findarato,

I'm sorry to hear Ubuntu One isn't installing properly for you. Did you recently install the client? Please make sure you have the latest release, as that contains some important fixes. If you have the latest release, can you quit the client by right-clicking on the Ubuntu One applet and select quit, then try starting the client from a terminal session with: ubuntuone-client-applet

If there is an error, you should receive some info from starting the client there. If you don't, can you right-click on the Ubuntu One applet and select report a problem to file a bug report that will also attach some debug info.

Thanks!

Joshua

---

### Post by Findarato on 2009-09-15
Problem has been reported already, this is what my terminal says:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/dbus/connection.py", line 578, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 251, in got_state
    self.acquire_access_token(description, store)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 317, in acquire_access_token
    callback=callback_url)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/storageprotocol/oauth.py", line 286, in from_token_and_callback
    parameters['oauth_token'] = token.key
AttributeError: 'NoneType' object has no attribute 'key'

---

### Post by Findarato on 2009-09-15
To be clear, I have not even been able to link my client to my on-line subscription.

---

### Post by mnorwood154 on 2009-09-15
I have the exact same problem.

Ubuntu 9.04

Linux Ubuntu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

---

### Post by Findarato on 2009-09-16
I am also under a 64 bit ubuntu, is that any indication ?

---

### Post by Findarato on 2009-09-17
Bump

---

### Post by Findarato on 2009-09-17
This is what the terminal gives me :

Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/dbus/connection.py", line 578, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 251, in got_state
    self.acquire_access_token(description, store)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 317, in acquire_access_token
    callback=callback_url)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/storageprotocol/oauth.py", line 286, in from_token_and_callback
    parameters['oauth_token'] = token.key
AttributeError: 'NoneType' object has no attribute 'key'

---

### Post by Findarato on 2009-09-18
I went for a remove / purge / reinstall and now it works :)

---

### Post by joshuahoover on 2009-09-18
My apologies for the delay in getting back to everyone here. We released an update on Wednesday that should remedy this problem. If you are still have trouble after updating to the latest client, please right-click on the Ubuntu One icon and select "Report a Problem". Thank you all for your patience and for the interest in Ubuntu One!

-Joshua

---

### Post by JaspSoft on 2009-10-17
I've just downloaded this following the instructions here:
[https://one.ubuntu.com/support/installation/](https://one.ubuntu.com/support/installation/)

I'm on 9.04 and I can find no way at all to add a computer.

---

### Post by Psyphre on 2009-10-17
Same, Jaunty 64 bits, cant add my computer because no webpage comes up.

:(

I installed in within the past hour, so its as up to date as you can get.

Here's my terminal output:
```

Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/dbus/connection.py", line 578, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 276, in got_state
    self.acquire_access_token(description, store)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 336, in acquire_access_token
    self.request_token = self.make_token_request(oauth_request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 229, in make_token_request
    fp = opener.open(oauth_request.http_url, oauth_request.to_postdata())
  File "/usr/lib/python2.6/urllib.py", line 205, in open
    return getattr(self, name)(url, data)
  File "/usr/lib/python2.6/urllib.py", line 437, in open_https
    h.endheaders()
  File "/usr/lib/python2.6/httplib.py", line 868, in endheaders
    self._send_output()
  File "/usr/lib/python2.6/httplib.py", line 740, in _send_output
    self.send(msg)
  File "/usr/lib/python2.6/httplib.py", line 699, in send
    self.connect()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 58, in _connect_wrapper
    if self._tunnel_host:
AttributeError: HTTPSConnection instance has no attribute '_tunnel_host'
```

---

### Post by Xavier Oddmon on 2009-10-18
Same issue, on jaunty, 32 bit. no add computer web page. What's more, I checked the FAQs, and they mention not being able to connect to [http://127.0.0.1:35782/](http://127.0.0.1:35782/). I also cannot connect to this URL, in firefox or opera, and don't have any firewall configured. I'm not even sure this is related though. If that's not the URL to go to, why can't there just be a button to add the computer :confused:

---

### Post by Psyphre on 2009-10-19
This bug was filed on launchpad.

[https://bugs.launchpad.net/ubuntuone-client/+bug/451670](https://bugs.launchpad.net/ubuntuone-client/+bug/451670)

They claim its been fixed in the new revision, though I don't know how to update to the latest revision so can't test it out.

If anyone knows how please let me know.

---

### Post by joshuahoover on 2009-10-20
> **Psyphre said:**
> This bug was filed on launchpad.

[https://bugs.launchpad.net/ubuntuone-client/+bug/451670](https://bugs.launchpad.net/ubuntuone-client/+bug/451670)

They claim its been fixed in the new revision, though I don't know how to update to the latest revision so can't test it out.

If anyone knows how please let me know.

We did put out a release yesterday that fixes bug 451670. In order to get this release, you can normally go to System->Administration->Update Manager. In Update Manager click on the "Check" button and once the update is done, click "Install Updates".

On the command line you can update by running: sudo apt-get update && sudo apt-get upgrade

Thank you, 

Joshua

---

### Post by Psyphre on 2009-10-21
> **joshuahoover said:**
> We did put out a release yesterday that fixes bug 451670. In order to get this release, you can normally go to System->Administration->Update Manager. In Update Manager click on the "Check" button and once the update is done, click "Install Updates".

On the command line you can update by running: sudo apt-get update && sudo apt-get upgrade

Thank you, 

Joshua

Hi, thanks alot I tried again shortly after my post and the update was there, I guess it just took a while for the update to appear :)

Got it working now!

Thanks again.

---

### Post by honzasvasek on 2009-11-18
ubuntuone needs networkmanager installed and running.

---

### Post by sites on 2009-12-21
> **honzasvasek said:**
> ubuntuone needs networkmanager installed and running.

Since I'm using wicd, which removes network-manager upon installing, I suppose my hopes of running UbuntuOne are hosed.

Are there any plans to make this service work through wicd?

---

### Post by can0ne on 2010-02-01
> **sites said:**
> Since I'm using wicd, which removes network-manager  upon installing, I suppose my hopes of running UbuntuOne are hosed.

Are there any plans to make this service work through wicd?

same problem.

---

### Post by joshuahoover on 2010-02-01
> **can0ne said:**
> same problem.

For those not using NetworkManager, we have a fix in. 

Karmic (9.10) users should follow this FAQ: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/930](https://answers.edge.launchpad.net/ubuntuone-client/+faq/930)

Jaunty (9.04) users should just do an update via Update Manager and install the latest Ubuntu One updates

Thanks,

Joshua

---

### Post by RavanH on 2010-02-05
> **joshuahoover said:**
> For those not using NetworkManager, we have a fix in. 

Karmic (9.10) users should follow this FAQ: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/930](https://answers.edge.launchpad.net/ubuntuone-client/+faq/930)

Jaunty (9.04) users should just do an update via Update Manager and install the latest Ubuntu One updates

Thanks,

Joshua

WOOOT ! !

Thanks Joshua, the proposed version did the trick :)

Even though the error ```
ERROR:dbus.proxies:Introspect error on org.freedesktop.NetworkManager:/org/freedesktop/NetworkManager: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
``` still shows, the client connects and syncs using Wicd like it used to with NM.

THANKS!

---

### Post by ralpyka on 2010-03-16
I have a similar problem. (Sorry for my english)
I use Ubuntu 9.04. I recently reinstalled ubuntu and I installed ubuntuone. Was a problem with libhttp2, but i installed it, and ubuntu one started, but the sync did not worked. After i made a mistake, because on the ubuntuone webpage i removed all computers from the account. I reinstalled ubuntuone, but there is no "add computer" webpage. Can you give me some advice to what to do now?

---

### Post by joshuahoover on 2010-03-16
> **ralpyka said:**
> I have a similar problem. (Sorry for my english)
I use Ubuntu 9.04. I recently reinstalled ubuntu and I installed ubuntuone. Was a problem with libhttp2, but i installed it, and ubuntu one started, but the sync did not worked. After i made a mistake, because on the ubuntuone webpage i removed all computers from the account. I reinstalled ubuntuone, but there is no "add computer" webpage. Can you give me some advice to what to do now?

Did you follow the latest instructions found at [https://one.ubuntu.com/support/installation/](https://one.ubuntu.com/support/installation/) ? If so, you might want to try starting the the Ubuntu One preferences from a terminal session (Applications->Accessories->Terminal): ubuntuone-preferences

If you get an error there, please let me know. Also, make sure you have your preferred browser set in System->Preferences->Preferred Applications

Thank you,

Joshua

---

### Post by ralpyka on 2010-03-27
I followed the latest instructions, to reinstall the client. The window appears, but the Name, Username, E-mail are all empty. I got an error message too: 
```

DBusException(dbus.String(u'Traceback (most recent call last):\n  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1068, in set_throttling_limits\n    aq.writeLimit = upload\n  File "/usr/lib/python2.6/dist-packages/ubuntuone/storageprotocol/client.py", line 1451, in _set_write_limit\n    raise ValueError(\'Write limit must be greater than 0.\')\nValueError: Write limit must be greater than 0.\n'),)

```I hope, that this is useful.

---

### Post by joshuahoover on 2010-03-29
> **ralpyka said:**
> I followed the latest instructions, to reinstall the client. The window appears, but the Name, Username, E-mail are all empty. I got an error message too: 
```

DBusException(dbus.String(u'Traceback (most recent call last):\n  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1068, in set_throttling_limits\n    aq.writeLimit = upload\n  File "/usr/lib/python2.6/dist-packages/ubuntuone/storageprotocol/client.py", line 1451, in _set_write_limit\n    raise ValueError(\'Write limit must be greater than 0.\')\nValueError: Write limit must be greater than 0.\n'),)

```I hope, that this is useful.

This sounds like you need to remove ~/.config/ubuntuone/syncdaemon.conf and then restart the client. The best way to do this right now is to open a terminal session (Applications->Accessories->Terminal):

killall ubuntuone-syncdaemon
killall ubuntuone-login

Then open System->Preferences->Ubuntu One and see if you get the same error.

Thanks!

Joshua

---

### Post by ralpyka on 2010-03-31
I deleted that file, what you said(~/.config/ubuntuone/syncdaemon.conf). When I start the client, I hasn't any error message, but the "add computer" webpage doesn't apper, everything is the same, as before(Name, Username, E-mail are still empty).
There is no other way to manually add my computer to the service?

EDIT: I solved my problem. Thank you for all the help.
I installed ubuntuone-client-tools, and with the u1sync --authorize command I could add my computer to the service. Now everything is going ok.

---

### Post by joshuahoover on 2010-03-31
> **ralpyka said:**
> I deleted that file, what you said(~/.config/ubuntuone/syncdaemon.conf). When I start the client, I hasn't any error message, but the "add computer" webpage doesn't apper, everything is the same, as before(Name, Username, E-mail are still empty).
There is no other way to manually add my computer to the service?

EDIT: I solved my problem. Thank you for all the help.
I installed ubuntuone-client-tools, and with the u1sync --authorize command I could add my computer to the service. Now everything is going ok.

I'm happy to hear Ubuntu One is working for you now. You shouldn't have had to use u1sync to get things working. Based on the error you reported, it seemed like it didn't like the bandwidth throttling settings so deleting the ~/.config/ubuntuone/syncdaemon.conf and restarting Ubuntu One should have taken care of this problem. Strange.

Joshua

---

### Post by alpha-buntu on 2010-04-02
> **ralpyka said:**
> I deleted that file, what you said(~/.config/ubuntuone/syncdaemon.conf). When I start the client, I hasn't any error message, but the "add computer" webpage doesn't apper, everything is the same, as before(Name, Username, E-mail are still empty).
There is no other way to manually add my computer to the service?

EDIT: I solved my problem. Thank you for all the help.
I installed ubuntuone-client-tools, and with the u1sync --authorize command I could add my computer to the service. Now everything is going ok.

kind of lame - but that worked here!

---

### Post by mindaslab on 2010-04-06
Have the same problem. I have stopped using Ubuntu one. I have got a thumb drive into which I backup every day! Life now seems so simple. Looks like Ubuntu one is a total failure.

---

### Post by flomar on 2010-04-15
Same behavior on 10.04 Beta on my Thinkpad X200. I think maybe it has to do something with the fact that I was playing around with Ubuntu One on my Windows machine before.

Removal and Reinstalling Ubuntu One in the Software-Center solved the problem for me!

---

### Post by filister on 2010-04-25
Hey guys, I'm using the new Ubunu 10.04 Beta II, and I found that there is not an add computer button in the ubuntu one ccount page. There is only remove selected computers from the list. So if for some reason you miss to click on authorize the computer to the account you won't benefit from this service. I tried to reinstall the client, I removed all the packages associated with ubuntu one in the Ubuntu Software Center, and reinstall it through the terminal with the command sudo aptitude install ubuntuone-client and now there is not an ubuntu one menu entry. I was not able to start it with the console either.

---

### Post by joshuahoover on 2010-04-27
> **filister said:**
> Hey guys, I'm using the new Ubunu 10.04 Beta II, and I found that there is not an add computer button in the ubuntu one ccount page. There is only remove selected computers from the list. So if for some reason you miss to click on authorize the computer to the account you won't benefit from this service. I tried to reinstall the client, I removed all the packages associated with ubuntu one in the Ubuntu Software Center, and reinstall it through the terminal with the command sudo aptitude install ubuntuone-client and now there is not an ubuntu one menu entry. I was not able to start it with the console either.

I'm sorry this process isn't as streamlined as it could be. We're working on fixing that, but in the time being, you should be able to open System->Preferences->Ubuntu One and then get prompted in a web browser window to add your computer to your Ubuntu One account. If this never happens, can you do the following?

[LIST=1]
[*]Open Applications->Accessories->Passwords and Encryption Keys
[*]If you have an UbuntuOne token (under Passwords: default), right-click and select delete
[*]Open a terminal session (Applications->Accessories->Terminal) and run:
killall ubuntuone-login ubuntuone-syncdaemon
[*]Open System->Preferences->Ubuntu One
[*]A browser window should open and you should be prompted to add your computer
[/LIST]
Thank you,

Joshua

---

### Post by gyterpena on 2010-04-28
Hi Joshua

Your fix is not working there is no ubuntu-one menu item in system -> preferences.
Also tried to remove purge and install again. 

Running 10.04 upgraded from 9.10

Thanks
Peter

Edit: Never mind above post managed to fixed it. When installing from CLI there was no menu entry but from software centre it worked. Only think missing at the moment is the tray icon.

---

### Post by heatpumpcontrol on 2010-04-28
[QUOTE=

[LIST=1]
[*]Open Applications->Accessories->Passwords and Encryption Keys
[*]If you have an UbuntuOne token (under Passwords: default), right-click and select delete
[*]Open a terminal session (Applications->Accessories->Terminal) and run:
killall ubuntuone-login ubuntuone-syncdaemon
[*]Open System->Preferences->Ubuntu One
[*]A browser window should open and you should be prompted to add your computer
[/LIST]
Thank you,

Joshua[/QUOTE]

This worked! thanks

---

### Post by joshuahoover on 2010-04-29
> **gyterpena said:**
> Hi Joshua

Edit: Never mind above post managed to fixed it. When installing from CLI there was no menu entry but from software centre it worked. Only think missing at the moment is the tray icon.

Right, the tray icon is no more. :( You now can access Ubuntu One Preferences from the Lucid "Me menu" (your username in the task bar) or via System->Preferences->Ubuntu One

Thank you,

Joshua

---

### Post by technodenbow on 2010-04-29
Same issue here as well. No option to select computer and sync. Ubuntu/Linux newbie so be gentle!

---

### Post by thebear78 on 2010-04-30
> **technodenbow said:**
> Same issue here as well. No option to select computer and sync. Ubuntu/Linux newbie so be gentle!

Just added some info about this issue and some instructions on how to resolve it to add your computers to Ubuntu One. It involved opening Terminal but it's only 1 command so don't be scared. [http://bit.ly/caHbOf](http://bit.ly/caHbOf)

---

### Post by catxk on 2010-04-30
> **thebear78 said:**
> Just added some info about this issue and some instructions on how to resolve it to add your computers to Ubuntu One. It involved opening Terminal but it's only 1 command so don't be scared. [http://bit.ly/caHbOf](http://bit.ly/caHbOf)

This did it for me with Ubuntu 10.04, thanks.

---

### Post by jonny163 on 2010-04-30
> **joshuahoover said:**
> I'm sorry this process isn't as streamlined as it could be. We're working on fixing that, but in the time being, you should be able to open System->Preferences->Ubuntu One and then get prompted in a web browser window to add your computer to your Ubuntu One account. If this never happens, can you do the following?

[LIST=1]
[*]Open Applications->Accessories->Passwords and Encryption Keys
[*]If you have an UbuntuOne token (under Passwords: default), right-click and select delete
[*]Open a terminal session (Applications->Accessories->Terminal) and run:
killall ubuntuone-login ubuntuone-syncdaemon
[*]Open System->Preferences->Ubuntu One
[*]A browser window should open and you should be prompted to add your computer
[/LIST]
Thank you,

Joshua

Thanks Joshua, this worked a treat for me in 10.04

---

### Post by joshuahoover on 2010-04-30
> **jonny163 said:**
> Thanks Joshua, this worked a treat for me in 10.04
 
Good to hear! And thank you for following up here as it's helpful to others to know when something works (as well as when it doesn't.) :)

Joshua

---

### Post by essial on 2010-04-30
> **joshuahoover said:**
> I'm sorry this process isn't as streamlined as it could be. We're working on fixing that, but in the time being, you should be able to open System->Preferences->Ubuntu One and then get prompted in a web browser window to add your computer to your Ubuntu One account. If this never happens, can you do the following?

[LIST=1]
[*]Open Applications->Accessories->Passwords and Encryption Keys
[*]If you have an UbuntuOne token (under Passwords: default), right-click and select delete
[*]Open a terminal session (Applications->Accessories->Terminal) and run:
killall ubuntuone-login ubuntuone-syncdaemon
[*]Open System->Preferences->Ubuntu One
[*]A browser window should open and you should be prompted to add your computer
[/LIST]
Thank you,

Joshua

I created my Ubuntu one account via my laptop with a clean x86 install of Ubuntu 10.04, and the process went flawlessly. When I then tried to add my cleanly installed x86_64 Ubuntu 10.04 desktop to Ubuntu one I had the same issue (no add button). Doing the above fixes the problem. I truly hope you guys fix this issue ASAP as Ubuntu One will be a great way for you to get even more revenue to continue developing such an amazing Linux distribution!

---

### Post by pope1701 on 2010-05-01
After a clean install of 10.04 it didn't work with my standard browser set to opera. 

After resetting standard browser to Firefox and following [this guide]("http://https://wiki.ubuntu.com/UbuntuOne/FAQ#How do I add my computer?") it worked. Maybe this should be mentioned somewhere. :)

Thank you!

---

### Post by Fuchur777 on 2010-05-01
> **joshuahoover said:**
> This sounds like you need to remove ~/.config/ubuntuone/syncdaemon.conf and then restart the client. The best way to do this right now is to open a terminal session (Applications->Accessories->Terminal):

killall ubuntuone-syncdaemon
killall ubuntuone-login

Then open System->Preferences->Ubuntu One
Thanks!

Joshua

This worked perfectly for me with my error not getting add computer page in Lucid Lynx!

---

### Post by lotharmat on 2010-05-01
> **joshuahoover said:**
> I'm sorry this process isn't as streamlined as it could be. We're working on fixing that, but in the time being, you should be able to open System->Preferences->Ubuntu One and then get prompted in a web browser window to add your computer to your Ubuntu One account. If this never happens, can you do the following?

[LIST=1]
[*]Open Applications->Accessories->Passwords and Encryption Keys
[*]If you have an UbuntuOne token (under Passwords: default), right-click and select delete
[*]Open a terminal session (Applications->Accessories->Terminal) and run:
killall ubuntuone-login ubuntuone-syncdaemon
[*]Open System->Preferences->Ubuntu One
[*]A browser window should open and you should be prompted to add your computer
[/LIST]
Thank you,

Joshua

This worked for me! - Thanks Joshua

Now - If only it would synch my files!

---

### Post by emagine on 2010-05-01
> **joshuahoover said:**
> I'm sorry this process isn't as streamlined as it could be. We're working on fixing that, but in the time being, you should be able to open System->Preferences->Ubuntu One and then get prompted in a web browser window to add your computer to your Ubuntu One account. If this never happens, can you do the following?

[LIST=1]
[*]Open Applications->Accessories->Passwords and Encryption Keys
[*]If you have an UbuntuOne token (under Passwords: default), right-click and select delete
[*]Open a terminal session (Applications->Accessories->Terminal) and run:
killall ubuntuone-login ubuntuone-syncdaemon
[*]Open System->Preferences->Ubuntu One
[*]A browser window should open and you should be prompted to add your computer
[/LIST]
Thank you,

Joshua
The above instructions worked for me.  Although for me, I did not have an ubuntuone token, so there was no need for me to delete the key.  But still check!

---

### Post by pfnorris on 2010-05-03
> **emagine said:**
> The above instructions worked for me.  Although for me, I did not have an ubuntuone token, so there was no need for me to delete the key.  But still check!

I have followed these instructions on a fresh build Lucid machine. It gets as far as launching the web browser, and asking me to log in so that I can authorize the machine, but then rejects my credentials with "password didn't match".

I know the credentials are correct 'cause they are working fine with two other upgraded machines. Grateful for any suggestions to solve this little issue.

Phil

---

### Post by pfnorris on 2010-05-03
> **pfnorris said:**
> I have followed these instructions on a fresh build Lucid machine. It gets as far as launching the web browser, and asking me to log in so that I can authorize the machine, but then rejects my credentials with "password didn't match".

I know the credentials are correct 'cause they are working fine with two other upgraded machines. Grateful for any suggestions to solve this little issue.

Phil

Oh....I feel silly now. "I know the credentials are correct...." Damn those capital letters!!

---

### Post by duanedesign on 2010-05-03
> **lotharmat said:**
> This worked for me! - Thanks Joshua

Now - If only it would synch my files!

The Ubuntu One Team deployed a whole new infrastructure and server farm to cope with the increasing load. They are in the process of fine-tuning things to take advantage of the new capacity.
Everything should be improving shortly.

---

### Post by BetterWang on 2010-05-04
How come this is not working at all from a new install?

---

### Post by joshuahoover on 2010-05-04
> **BetterWang said:**
> How come this is not working at all from a new install

I'm sorry to hear Ubuntu One isn't working properly for you now. Without more information, I'm not sure how to help you. If your web browser is not opening after opening Ubuntu One Preferences, please see this FAQ: [https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?](https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?) 

If you are using the Opera web browser, Ubuntu One will not work.

Thank you,

Joshua

---

### Post by mocabrera on 2010-05-05
Hi, I did this:

[https://wiki.ubuntu.com/UbuntuOne/FA...my%20computer?]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?")  

Not working, I have lucid now and I never could add my computer since karmic.
The web page to add computer never shows.

---

### Post by joshuahoover on 2010-05-05
> **mocabrera said:**
> Hi, I did this:

[https://wiki.ubuntu.com/UbuntuOne/FA...my%20computer?]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?")  

Not working, I have lucid now and I never could add my computer since karmic.
The web page to add computer never shows.

If you run the following commands in a terminal session, can you tell me what they output?

ubuntuone-preferences

xdg-open [https://one.ubuntu.com/](https://one.ubuntu.com/)

Thank you,

Joshua

---

### Post by mocabrera on 2010-05-06
Thanks for your answer, this is the output:
u1sdtool -q
ubuntuone-syncdaemon stopped.

killall ubuntuone-login
ubuntuone-login: process not found

u1sdtool -c
Nothing happens

Now the others commands:
ubuntuone-preferences: opens the preferences window

xdg-open [https://one.ubuntu.com/](https://one.ubuntu.com/): open the ubuntu one page, I can sign in ( I have an account) goes directly to the dashboard. In account -> view machines connected:
You haven't added any computers or devices to your Ubuntu One account.

Tell me if you need something else to help solve the problem.

---

### Post by joshuahoover on 2010-05-06
> **mocabrera said:**
> Thanks for your answer, this is the output:
u1sdtool -q
ubuntuone-syncdaemon stopped.

killall ubuntuone-login
ubuntuone-login: process not found

u1sdtool -c
Nothing happens

Now the others commands:
ubuntuone-preferences: opens the preferences window

xdg-open [https://one.ubuntu.com/](https://one.ubuntu.com/): open the ubuntu one page, I can sign in ( I have an account) goes directly to the dashboard. In account -> view machines connected:
You haven't added any computers or devices to your Ubuntu One account.

Tell me if you need something else to help solve the problem.

I'm sorry this still isn't working for you. It would be helpful to see some log files. Can you file a bug following these steps:

   1.  [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)  - Be sure to include the steps you're taking and the results you're seeing
   2. At a terminal session (Applications->Accessories->Terminal) run the following command (replacing ###### with the bug number from step 1): apport-collect -p ubuntuone-client ######

Can you make sure you don't have an "Ubuntu One token" in Applications->Accessories->Passwords and Encryption Keys? If you do, can you right-click and select "Delete", then try running the commands you ran previously. 

After all that, you can try to run the following script and see if it helps: [http://pastebin.ubuntu.com/429028/](http://pastebin.ubuntu.com/429028/) To do this, you need to save the script (u1_force_auth.py) to a file and then in a terminal session run the script in the directory where you saved it: python u1_force_auth.py

Thank you,

Joshua

---

### Post by mocabrera on 2010-05-06
Hi I made a bug report #57663, and apport-collect -p ubuntuone-client.

I have not any "Ubuntu One token" in Applications->Accessories->Passwords  and Encryption Keys
and if I run [http://pastebin.ubuntu.com/429028/](http://pastebin.ubuntu.com/429028/)  nothing happens, but I have to Ctrl C, to get a prompt.

---

### Post by beameup on 2010-05-07
I'm having a problem with 1 machine getting authenticated.

I get this when I select add this computer. "Firefox can't find the server at localhost."

Thought it might be a firewall issue but it's turned off.
Yes I have a working network connection.
Running 32bit 10.04
I have no U1 token in my keyring
works fine on 2 other machines on the same connection.

Any advice on what to look for?

---

### Post by duanedesign on 2010-05-07
Are you using a proxy or a script blocking application like noScript?

---

### Post by beameup on 2010-05-07
Only Adblock and I turned that off.

OK, I get this in my FF error console.

> Bindwood: Error creating database:  message: 'Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIXMLHttpRequest.send]', reason: 'undefined', description: 'undefined', error: 'undefined', raw error: '{}'

---

### Post by joshuahoover on 2010-05-07
> **beameup said:**
> Only Adblock and I turned that off.

OK, I get this in my FF error console.

It sounds like the local Ubuntu One http server process isn't running. Have you tried this in a terminal session?
u1sdtool -q; killall ubuntuone-login; u1sdtool -c

Thanks!

Joshua

---

### Post by beameup on 2010-05-07
OK solved it. There was no entry in my hosts file for "localhost" only the name of my machine, so I added 127.0.0.1 localhost,  and when I retried it all worked.

---

### Post by beameup on 2010-05-07
> **joshuahoover said:**
> It sounds like the local Ubuntu One http server process isn't running. Have you tried this in a terminal session?
u1sdtool -q; killall ubuntuone-login; u1sdtool -c

Thanks!

Joshua

Yes Joshua thanks, thats what I've been trying, but see my last post for how i solved it.

---

### Post by mocabrera on 2010-05-07
Hi Joshua, I deleted syncdaemon.conf and  the output was:
ubuntuone-syncdaemon stopped.
ubuntuone-login: process not found
 And then, the prompt.
 Regards


We are following this at [https://bugs.launchpad.net/ubuntuone-client/+bug/576636](https://bugs.launchpad.net/ubuntuone-client/+bug/576636)

---

### Post by dafri on 2010-05-13
thank you for this perfekt hint, JOSHUA. this problem is now fixed ;). i take your answer in the german forum ([http://forum.ubuntuusers.de/topic/ubuntu-one-probleme-beim-computer-zuordnen/#post-2483037](http://forum.ubuntuusers.de/topic/ubuntu-one-probleme-beim-computer-zuordnen/#post-2483037)). have i nice evening. greatings from BERLIN! dafri

---

### Post by User Abuser on 2010-07-05
> **joshuahoover said:**
> This sounds like you need to remove ~/.config/ubuntuone/syncdaemon.conf and then restart the client. The best way to do this right now is to open a terminal session (Applications->Accessories->Terminal):

killall ubuntuone-syncdaemon
killall ubuntuone-login

Then open System->Preferences->Ubuntu One and see if you get the same error.

Thanks!

Joshua
That worked for me. Thanks Josh :KS This is just great!

---

### Post by duanedesign on 2010-07-06
If you are having trouble adding your computer see:

[https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?")

---

### Post by sffvba[e0rt on 2011-10-19
Back to sleep thread...


404

---

