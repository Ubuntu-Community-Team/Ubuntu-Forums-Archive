---
title: "Wifi security - I don't want the password remembered"
date: 2012-08-01
forum: Security
---

### Post by MarcellaFL on 2012-08-01
Call me crazy but I want to have to key in the password every time I connect. I have a house full of children and want them to have to ask me to log in if they want access. Is there anyway to STOP Ubuntu from remembering the password?

---

### Post by Ms. Daisy on 2012-08-01
You can go to Network Manager applet and click on "edit connections". Then you can delete the wireless connection.  That will work immediately until you figure out how to prevent Ubuntu from remembering the password.  
 
I'm sure there's a way to do it but I'm on Windows right now. Once I get back to Ubuntu I'll check it out (if no one else has).

---

### Post by MarcellaFL on 2012-08-03
I figured that out right away but really wish I could deactivate Ubuntu from remembering the password.

---

### Post by Ms. Daisy on 2012-08-04
Here's how I made it happen on my system.

1. You have to turn Automatic Login off for the administrator account.  That will require your sudo password to log in to the administrator account.

2. Go to the network manager applet, "edit connections".  Edit the home connection and go the Wireless Security tab, uncheck the "Connect Automatically" and "Available to all users" boxes.

[ATTACH]222241[/ATTACH]

3. Make the kids use the guest account.  When the guest account logs in it will NOT automatically connect to your wireless.  They can choose the wireless account and it will ask for the sudo password, then it will ask for the wireless password.

You can probably play around with these settings to obtain what you're looking for.

---

### Post by hakermania on 2012-08-04
Also, another solution, in case every child has its own computer or you have one and they another one, would be to ban every mac address except yours. And, when your kids want to access the network to ask you unban their mac address.

By the way, this is a quite (not awesome) good way to protect your network from being stolen by third party!

---

### Post by uRock on 2012-08-04
Another great way of preventing the PC from connecting is by installing GUFW and setting it to block outgoing, which will get it done. Once this is done, you can open GUFW and turn off the firewall or change the setting to allow outgoing to be able to connect and run updates or whatever you need to do.```
sudo apt-get install gufw
```To change the firewall settings the admin password will be needed.

---

### Post by MarcellaFL on 2012-08-06
Thanks for the ideas. Just seems needlessly complicated. Shouldn't there be a way to ask Ubuntu to NOT remember the password? (I am being rhetorical here)

---

