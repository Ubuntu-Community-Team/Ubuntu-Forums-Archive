---
title: "Ubuntu One disappears from notification area, stops syncing"
date: 2009-08-16
forum: Ubuntu One (CLOSED)
---

### Post by infinitejones on 2009-08-16
Anyone else noticing this? I've just done a fresh re-install of Jaunty, upgraded everything and installed Ubuntu One as per the instructions on [https://ubuntuone.com/support/installation/](https://ubuntuone.com/support/installation/).

The first sign of trouble is when I get to step 4 of those instructions - it doesn't launch a web browser. However my computer is already authorised so I just skipped over that bit.

Anyway it starts OK, the Ubuntuone logo appears in my notification area and starts spinning round, to show it's syncing. Then the logo disappears from the notification area.

If I do "ps aux | grep ubu" I get this:
```

matt      5419  0.2  1.2  51404 24880 ?        Sl   18:30   0:01 /usr/bin/python /usr/bin/ubuntuone-client-applet
matt      5421  0.3  0.8  37864 17648 ?        Sl   18:30   0:01 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
```
so Ubuntu says it's still running, but it's not syncing any more, and I get "permission denied" if I try to copy anything into the folder.

If I click on the icon under Applications->Internet, nothing happens, and if I type "ubuntuone-client-applet" into the terminal, it tells me it's already running. 

But then if I kill the processes given above and do "ubuntuone-client-applet" again, I get no response - no error messages, nothing. I have to do ctrl-C to get the cursor back.

I think this has only started happening in the last couple of days... anyone else finding the same thing and/or solved this? I can't really find anything useful in the support area of Ubuntuone.com or on Launchpad...

---

### Post by balaknair on 2009-08-16
It's not a bug, it's a "feature" :D

[https://bugs.launchpad.net/bugs/413661](https://bugs.launchpad.net/bugs/413661)

> #4   	 Elliot Murphy  wrote on 2009-08-15:

Hi! This is by design, the icon is now only shown during periods of activity (scanning or downloading) or if there is an error. We realize it may be surprising at first (as is any change in behavior). In the next couple of weeks, we'll be adding integration with the notification system so you'll have a better indication that Ubuntu One is happy, all files have synced.


Had me confused too.
Though now I find that it doesn't sync as often. So after I modify/delete or add files, the changes are not synced for quite a while.

---

### Post by infinitejones on 2009-08-16
OK... but I still can't actually move any files into the folder! In nautilus it has an orange circle with an icon of a padlock on it, as if I'm not the owner of the folder, and I'm not allowed to drag or copy anything into it. It seems like I'm no longer actually connected to the remote server. 

Nautilus doesn't give me the option to connect, either in the right-click menu or as a button above the main Nautilus window (like the button that appears to write files to a CD). And because the icon isn't in the notification area, I can't right click on that to connect either!

Am I missing something obvious here?

---

### Post by balaknair on 2009-08-16
That does look bad. I'm guessing it's some sort of authentication issue. You will need to confirm that this computer can access your UbuntuOne account, and going through your first post again, it seems that might not have happened(since it's a fresh OS install, it's possible that your previous authorisation may no longer apply).

Maybe a reinstall of UbuntuOne is needed. Try completely removing UbuntuOne(including configuration) and reinstalling.

I'll try going through the UbuntuOne bugreports in Launchpad in the meantime.

Edit: This might be relevant
[https://bugs.launchpad.net/bugs/380795](https://bugs.launchpad.net/bugs/380795)

Especially these comments on this bugreport ( [https://bugs.launchpad.net/ubuntuone-client/+bug/363243](https://bugs.launchpad.net/ubuntuone-client/+bug/363243) )
[https://bugs.launchpad.net/ubuntuone-client/+bug/363243/comments/1](https://bugs.launchpad.net/ubuntuone-client/+bug/363243/comments/1)
[https://bugs.launchpad.net/ubuntuone-client/+bug/363243/comments/3](https://bugs.launchpad.net/ubuntuone-client/+bug/363243/comments/3)

Basically, delete the old key from the Gnome keyring, then authorize UbuntuOne on the computer again with the command *u1sync --authorize*

---

### Post by Merovius on 2009-08-16
This "feature" had me going a little nuts too. Guess thats the price of beta testing..:)

---

### Post by andrea000 on 2009-08-17
I found this out the hard way and i don't care for it
but maybe if enough of us speak up about it they will
revert back to the previous method i hope anyway.

---

### Post by balaknair on 2009-08-17
> **Merovius said:**
> This "feature" had me going a little nuts too. Guess thats the price of beta testing..:)

> **andrea000 said:**
> I found this out the hard way and i don't care for it
but maybe if enough of us speak up about it they will
revert back to the previous method i hope anyway.


Yes, I know just what you mean. I'd just gotten used to clicking on the Systray icon to open the Ubuntu One folder or Web UI, and it's a bit irritating to have to navigate to it via Places>Bookmarks>Ubuntu One(not a lot more difficult, but irritating nonetheless). 

Apparently someone felt it was against the GNOME human interface guidelines
[https://bugs.launchpad.net/ubuntuone-client/+bug/396772](https://bugs.launchpad.net/ubuntuone-client/+bug/396772)

So instead of adding the option of disabling/enabling the icon when idle, they just disabled it.

I hope they fix this, maybe a 'configure Ubuntu One' applet which opens via 
Applications> Internet or Accessories or System Tools > Ubuntu One Configuration
System>Preferences>Ubuntu One Configuration where you can
1) Enable/Disable the notification icon
2) View the free space in your Ubuntu One account, Upgrade
3) Sync Now option, frequency of sync attempts, automatically connect
4) Configure or Troubleshoot connection or authentication errors

A good example for a layout would be the Preferences menu for Mozilla Weave- not too complicated but full featured.

Another item on my wish list is that users be able to specify a name for individual computers they have synced with their Ubuntu One accounts.

---

### Post by anechoic on 2009-08-18
> **balaknair said:**
> 

I hope they fix this, maybe a 'configure Ubuntu One' applet which opens via 
Applications> Internet or Accessories or System Tools > Ubuntu One Configuration
System>Preferences>Ubuntu One Configuration where you can
1) Enable/Disable the notification icon
2) View the free space in your Ubuntu One account, Upgrade
3) Sync Now option, frequency of sync attempts, automatically connect
4) Configure or Troubleshoot connection or authentication errors

A good example for a layout would be the Preferences menu for Mozilla Weave- not too complicated but full featured.

Another item on my wish list is that users be able to specify a name for individual computers they have synced with their Ubuntu One accounts.
yes a config panel would be very handy! and I like the icon being in the notification area where I can click on it and open the directory

how does one share the shared directory?

---

### Post by balaknair on 2009-08-18
> **anechoic said:**
> yes a config panel would be very handy! and I like the icon being in the notification area where I can click on it and open the directory

how does one share the shared directory?

Log in to the Web UI for UbuntuOne with your browser--> View Files--> Select a file or folder to be shared--> Click on the 'Share' button--> Enter the e-mail ID of the person you want to share it with

---

