---
title: "how to turn off keyring password entering when connecting to wlan?"
date: 2009-02-02
forum: Security
---

### Post by kaiwan on 2009-02-02
hi!

I have ubuntu 8.10 on my toshiba laptop. 
When I had conneceted to my wlan network for the first time I was asked for a password for the keyring and I had put my login password. 
So now, every time I start buntu I have to enter keyring password.
How can I turn this off?

---

### Post by nacho87 on 2009-02-02
you can change password or disable it from "system->preferences->network configuration"
then go o the wireless tab and there select your network and click on edit. There you can chnge the passs. if you want to make it ask you for the pass again when you try to conect just delete it.
Hope it helps and sorry about my bad english!!

---

### Post by kaiwan on 2009-02-02
> **nacho87 said:**
> you can change password or disable it from "system->preferences->network configuration"
then go o the wireless tab and there select your network and click on edit. There you can chnge the passs. if you want to make it ask you for the pass again when you try to conect just delete it.
Hope it helps and sorry about my bad english!!

No, I don have a problem with my wlan password, I dont want to change or remove it. The keyring password bothers me...

---

### Post by Bimme on 2009-08-15
Did you find a solution for this problem?
I have the same issue.

---

### Post by kaiwan on 2009-08-15
Well..I think I did..try not to use automatic login and use manual login...

---

### Post by edbucks on 2009-08-16
At the Create Default Keyring dialog, leave both boxes blank and click Create, then click Use Unsafe Storage.

---

### Post by quinnten83 on 2009-08-16
I tried that and now my wireless asks for password every time I log in.

---

### Post by edbucks on 2009-08-16
Have you enabled automatic login? 

System > Admin > Login Window, enter your password and it's under the Security tab in the Login Window Prefs dialog.

---

### Post by bingotailspin on 2009-11-04
The keys are kept here:

```
~/.gnome2/keyrings/
```

You can remove it/them and get new prompt.  If you enter no password and accept unsafe storage, the prompts will stop.

---

### Post by scaine on 2009-11-04
> **bingotailspin said:**
> ```
rm -rf ~/.gnome2/keyrings
```will stop the keyring service from prompting, on samba shares anyway.

Think that command will just delete the keyrings in question, won't it?  Should probably explain that before posting delete commands, particularly since you seem quite new to the forums.  Also, not sure why deleting the keyrings would help this issue, even for samba shares?

The easiest way I've found to stop a WLAN connection in Network Manager from prompting me for the password each time (apart from using unsafe storage which should also work nicely, albeit unsecurely), is to make the connection "available to all users".  This seems to force the Network Manager to use a different keyring to store your WEP/WPA password in and it won't prompt again.

---

### Post by Bartender on 2009-11-14
I just ran into this keyring problem last night at a friend's house after setting up their new DSL modem & router.  

We got the modem and router working on their Windows PC's.  

I fired up my Ubuntu 9.04 lappy.  It's set up to auto-login when turned on.  The wireless network was detected.  I entered the WEP key.  Got the keyring message.  If I clicked "Deny", I got online but had to re-enter WEP key after a restart.  If I typed in my sudo password, the connection failed!

Everybody's saying, go to Network Connections, click on the connection, Edit, click on the "Make available to all users" box, then "Apply".  

I'm trying that from home this morning, not connected to any network.  The friends' new wireless network that I was on last night is listed. but when I try to edit, "Apply" is grayed out.  Do you have to be connected to that network when you "Edit" the connection?  Maybe that explains why "Apply" is grayed out for me?

Also, the directions I'm finding in some of the posts for deleting keyring passwords don't seem to be applicable for 9.04.  Anyone have some up-to-date ideas?  This has got to be something which has been dealt with numerous times!!

---

### Post by Pjotr123 on 2009-11-18
Restart with a clean slate: wipe the current keyring and start a new one. Then leave the password blank (simply click OK and agree to unsafe storage).

Wipe the current one as follows:

Locations - Personal Folder

toolbar: View - Show Hidden Files

Double-click the folder .gnome2

Double-click the folder keyrings

Delete the file default.keyring and / or the file login.keyring

Restart your computer.

When prompted for a password, leave the password field blank (simply click OK and agree to unsafe storage).

The warning you get, is largely unjustified: there is hardly any risk involved. None if you are the only user of your machine.

---

### Post by mahershi on 2010-05-22
> **scaine said:**
> The easiest way I've found to stop a WLAN connection in Network Manager from prompting me for the password each time ... is to make the connection "available to all users".  This seems to force the Network Manager to use a different keyring to store your WEP/WPA password in and it won't prompt again.

This works as stated ... in Ubuntu 10.04. Thanks for this suggestion.

---

### Post by stewartb on 2010-06-16
Hi, Im using Ubuntu netbook remix 10.04 on an Acer Aspire one ZG5, I disabled the keyring prompt by going to System\Preferences\Startup Applications\Startup programs and unticked the 3 gnome keyring programs -

Certificate & Key storage
Secret Storage Service
SSH Key Agent

reboot and keyring prompt has gone with no noticed side effects plus easily reversable if needed.


edit - popped up again using evolution so maybe not the way to go

---

### Post by AlanRick on 2011-01-24
> **scaine said:**
> 
The easiest way I've found to stop a WLAN connection in Network Manager from prompting me for the password each time (apart from using unsafe storage which should also work nicely, albeit unsecurely), is to make the connection "available to all users". 
So simple.
So perfect.
Thank you.

---

