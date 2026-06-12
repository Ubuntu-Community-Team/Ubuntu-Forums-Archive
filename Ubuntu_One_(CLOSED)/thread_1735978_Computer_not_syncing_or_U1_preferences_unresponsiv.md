---
title: "Computer not syncing or U1 preferences unresponsive"
date: 2011-04-22
forum: Ubuntu One (CLOSED)
---

### Post by DGINSD on 2011-04-22
I've followed these instructions:

> Setup instructions for Ubuntu 10.10 (Maverick)

Before setting up Ubuntu One, you should ensure your system is up to date. Run Update Manager to install any necessary updates by going to System » Administration » Update Manager. You may need to restart your system. Once it's up to date, you can begin this setup process.

Already have an Ubuntu One account

Open Ubuntu One Preferences from the "Me" menu (your username in the upper right corner) or from System » Preferences » Ubuntu One

The Ubuntu One SSO window will open prompting you to either sign up for an account or login with an existing account. Click on the Already have an existing account? Click here to sign in link at the bottom of the window. 

Enter your email address and password. Click the Connect button. 

A success message should appear. Click the Close button to close the Ubuntu One SSO window. 

In Ubuntu One Preferences click on the Devices tab and then the Connect button to connect to the service. Use Ubuntu One Preferences to monitor current synchronization activity and manage your Ubuntu One preferences. Review the Ubuntu One features or use our support resources if you have questions. 

 

I've gone through it a few times and it always seems to be successful, but I keep getting the same results; all fields in the Ubuntu One Preferences app. say unknown, the field under the window title is blank and next to it, it says unknown, Name, E-mail, and Current plan all say unknown. It also says Synchronization in progress and will seem to say that indefinitely.

I'm getting rather frustrated and don't know why its not working like its supposed to. I can log in to my Ubuntu One account just fine on line but for what ever reason it will not recognize my computer. I really like the idea behind Ubuntu one and I can see how this could be extremely helpful but it proving difficult to get up and running, please help.

FWIW I also ran this command: u1sdtool -s which produced the following output:
State: QUEUE_MANAGER
 connection: With User With Network
 description: processing queues
 is_connected: True
 is_error: False
 is_online: True
 queues: WORKING_ON_CONTENT

---

### Post by DGINSD on 2011-04-22
OK an update my Ubuntu One Preferences finally finished syncing, I just left it alone for a long period, however all the fields still say unknown It did seem to sync up the Documents I told it to, but it also synced one I didn't a rather large one which I deleted. No harm no foul, but I am kind of curious how it got there.

If I click on the manage account in the U1 preferences it will now open a browser window to my U1 account, which is progress, but while I was poking around on U1 I found there are two computers listed as connected to my account, both are mine (the exact same computer)but oddly the long string of digits under the computer name (what is that anyway?) on each were different. I deleted the first one so that should be all good now as well.

Also aren't the files I have on U1 supposed to also show up in the U1 folder on my computer? If so for some reason thats not happening. So now this and why in Ubuntu One Preferences everything is listed as unknown are my two concerns I'd like help with. So anyone that can shed some light on these two issues I'd really appreciate the help and or clarification.

---

### Post by duanedesign on 2011-04-23
Looks like you might be affected by [bug 657850]("https://bugs.launchpad.net/ubuntuone-client/+bug/657850"). Could you please open A Terminal (Applications > Accessories > Terminal) and  run the following command with the Ubuntu One Preferences Window open.
```

dbus-send --print-reply \
                    --dest=com.ubuntu.sso \
                    /credentials \
com.ubuntu.sso.ApplicationCredentials.login_to_get_credentials \
                    "string:Ubuntu One" "string:Workaround for LP:657850" int64:0
```

---

### Post by DGINSD on 2011-04-23
> **duanedesign said:**
> Looks like you might be affected by [bug 657850]("https://bugs.launchpad.net/ubuntuone-client/+bug/657850"). Could you please open A Terminal (Applications > Accessories > Terminal) and  run the following command with the Ubuntu One Preferences Window open.
```

dbus-send --print-reply \
                    --dest=com.ubuntu.sso \
                    /credentials \
com.ubuntu.sso.ApplicationCredentials.login_to_get_credentials \
                    "string:Ubuntu One" "string:Workaround for LP:657850" int64:0
```


OK, I ran that command and it gave me this output

```
method return sender=:1.79 -> dest=:1.229 reply_serial=2

```

Sorry it took me so long to get back. 

So what now, check to see it the problem is fixed or is that command just to confirm the bug?

---

### Post by DGINSD on 2011-04-23
Ok I think I did it correctly  had to login to ubuntu one and remove the connected devices and remove ubuntu one from my passwords and encryption keys, then run the scipt, everything went ok but the problem still persists.

---

