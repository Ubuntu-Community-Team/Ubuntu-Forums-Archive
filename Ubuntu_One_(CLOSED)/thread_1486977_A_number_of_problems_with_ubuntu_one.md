---
title: "A number of problems with ubuntu one"
date: 2010-05-18
forum: Ubuntu One (CLOSED)
---

### Post by theophiles on 2010-05-18
I am having two problems with ubuntu one with which I need help.

[LIST=1]
[*]Ubuntu one does not appear in "me menu." I have "set up email,""chat" and "broadcast," but no ubuntu one. 
[*]When I got to preferences to get ubuntu one, I click "connect" and the box goes gray, but nothing happens. It does not connect.
[/LIST]

I had ubuntu one working fine before upgrading to 10.04

---

### Post by joshuahoover on 2010-05-18
> **theophiles said:**
> 1. Ubuntu one does not appear in "me menu." I have "set up email,""chat" and "broadcast," but no ubuntu one.

Hmmm... I haven't seen this problem. I'm assuming it remains even if you reboot? If you try to remove and re-install ubuntuone via the following commands, does the problem remain?

```
 sudo apt-get remove ubuntuone-client-gnome; sudo apt-get install ubuntuone-client-gnome
```>  2. When I got to preferences to get ubuntu one, I click "connect" and the box goes gray, but nothing happens. It does not connect.First, can you try deleting the following file? ~/.config/ubuntuone/syncdaemon.conf  Then try running the following in a terminal session and let me know what the output is? 

```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```If the problem persists, please file a bug so we can get some debug files and other helpful info that we can follow up on:

   1.  [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)  - Be sure to include the steps you're taking and the results you're seeing
   2. At a terminal session (Applications->Accessories->Terminal) run the following command (replacing ###### with the bug number from step 1): apport-collect -p ubuntuone-client ######

Thank you,

Joshua

---

### Post by theophiles on 2010-05-18
I have rebooted many times (just using the computer) and tried uninstalling and reinstalling ubuntuone's client a few times. I tried it again here and nothing.

Here is the output from```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```

```
ubuntuone-syncdaemon stopped.

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1

```

---

### Post by theophiles on 2010-05-18
And thank you for responding so quickly!

---

### Post by theophiles on 2010-05-18
Now it won't open from preferences at all.

---

### Post by duanedesign on 2010-05-19
The only time I have seen this is when using root as your user. Is this the case?

---

### Post by theophiles on 2010-05-20
No, I am not using as root. I had to use root to delete the .conf file, but otherwise I am just a normal user.

---

### Post by joshuahoover on 2010-05-20
> **theophiles said:**
> No, I am not using as root. I had to use root to delete the .conf file, but otherwise I am just a normal user.

OK, were you able to file a bug report? If you post it here I'll be sure to follow up on it ASAP.

Thanks,

Joshua

---

### Post by theophiles on 2010-05-20
I haven't posted the bug report yet because I wanted to see what worked. After I deleted the .conf file, I couldn't even get the client to start. Using synaptic I did a "complete remove" and got rid of everything that had anything to do with ubuntu one. Then I reinstalled it all. I now have it connecting and syncing, but it is still not in the me menu. I have restarted the computer three or four times since I did that. It is definitely not in the me menu. Should I still post a bug about that?

---

### Post by joshuahoover on 2010-05-21
> **theophiles said:**
> I haven't posted the bug report yet because I wanted to see what worked. After I deleted the .conf file, I couldn't even get the client to start. Using synaptic I did a "complete remove" and got rid of everything that had anything to do with ubuntu one. Then I reinstalled it all. I now have it connecting and syncing, but it is still not in the me menu. I have restarted the computer three or four times since I did that. It is definitely not in the me menu. Should I still post a bug about that?

Yes, if you don't mind, please file a bug report specifically for Ubuntu One not showing up in the Me menu.

Thank you,

Joshua

---

### Post by theophiles on 2010-05-22
I filed a bug here:
[https://bugs.launchpad.net/ubuntuone-client/+bug/584038](https://bugs.launchpad.net/ubuntuone-client/+bug/584038)

I received this message from Mitch Towner:
> Mitch Towner said 10 hours ago:
Hi Benjamin. It sounds like you may be looking in the wrong area. The "me menu" has "chat", "mail" & "broadcast" (see [http://imgbin.org/images/1663.png](http://imgbin.org/images/1663.png)). The "session menu" (on the far left corner of the top panel) contains IM Client Status (Available, Away, Busy, etc), "Chat Accounts", "Broadcast Accounts" & "Ubuntu One" (See [http://imgbin.org/images/1664.png](http://imgbin.org/images/1664.png)).

I hope this help. Kind Regards - Mitch Towner

So I do not think I have a "session menu." How do I get that?

---

### Post by joshuahoover on 2010-05-24
> **theophiles said:**
> I filed a bug here:
[https://bugs.launchpad.net/ubuntuone-client/+bug/584038](https://bugs.launchpad.net/ubuntuone-client/+bug/584038)

I received this message from Mitch Towner:


So I do not think I have a "session menu." How do I get that?

I followed up on the question: [https://answers.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+question/111907](https://answers.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+question/111907) 

I'm not sure how the me menu didn't get installed or configured but I provided some steps to try to get it back.

Thanks,

Joshua

---

### Post by theophiles on 2010-05-24
Thank you,

The problem is now solved.

---

