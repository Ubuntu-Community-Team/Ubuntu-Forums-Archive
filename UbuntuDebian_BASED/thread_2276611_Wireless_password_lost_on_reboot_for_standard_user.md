---
title: "Wireless password lost on reboot for standard user"
date: 2015-05-03
forum: Ubuntu/Debian BASED
---

### Post by abasel on 2015-05-03
Using the Elementary OS. Everything is working great and almost ready to deploy to the classroom but alas when the machine reboots, the standard users looses the wireless password (which then needs to be re-entered). If the administrator logs in, all is good and the connection remains.

I have set up the connection so that "All users may connect to this network.

---

### Post by howefield on 2015-05-03
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by abasel on 2015-05-03
Ok so using the following info from another post I got a little further

> . For me the problem was occuring  despite the "All users may connect to this network" checkbox being already checked. So what I did was to uncheck the box, save, check the box, then save again. I know this seems retarded, but it solved the problem for me.

Now when I the guest user logs in I get "Enter password to unlock your login keyring".

To give some background to the environment, I am auto-logging in with the Guest Session (which I have customised following: [https://help.ubuntu.com/community/CustomizeGuestSession#Special_purpose_user]("https://help.ubuntu.com/community/CustomizeGuestSession#Special_purpose_user"))

So now I need to know how to get rid of the keyring step. I can enter it but once the machine is rebooted I am required to enter it again.

---

