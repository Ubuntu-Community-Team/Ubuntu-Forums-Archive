---
title: "MX4 Ubuntu Gold : Connect to network with static IP"
date: 2015-08-06
forum: Ubuntu Phone and Tablet
---

### Post by stefan_bahrens on 2015-08-06
My home network uses static IPs not DHCP. Could someone tell me how to configure the MX4 so that I can connect to my network? I can't see any way to enter IP numbers. Thanks for any assistance.

---

### Post by howefield on 2015-08-07
Post moved out of the unrelated thread into its own.

Have a look here... [http://ubuntuforums.org/showthread.php?t=2279427](http://ubuntuforums.org/showthread.php?t=2279427)

---

### Post by stefan_bahrens on 2015-08-07
Thanks for this tip howefield. The examples in the thread discuss opening a console on the MX4 and then using command line applications like vi to edit or create configuration files. Does the MX4 come with vi installed? I can see no way to open a console. Does anyone know how to open a console on the MX4? Thanks.

---

### Post by howefield on 2015-08-07
> **stefan_bahrens said:**
> Thanks for this tip howefield. The examples in the thread discuss opening a console on the MX4 and then using command line applications like vi to edit or create configuration files. Does the MX4 come with vi installed? I can see no way to open a console. Does anyone know how to open a console on the MX4? Thanks.

To get a console on the phone you need to install the terminal app.

But be careful.. there be dragons.. and such :)

---

### Post by stefan_bahrens on 2015-08-07
Very helpful. Thanks howefield. To download anything I'll have to go to a wifi hotspot that uses DHCP as at the moment I cannot download at home on my static IP network. Assuming I can connect to a wifi hotspot are there any other Ubuntu apps that you would recommend? Clearly the terminal app is a must since the OS seems somewhat incomplete if it is impossible to connect to a wifi network with static IPs. Are there other apps that fill gaps that I've noticed, a native email client being one. What happened to Thunderbird? I'd also like to be able to use my work push email. Am I being a bit optimistic? Thanks again.

---

### Post by Bucky Ball on 2015-08-07
You could set up your router/AP to serve DHCP outside the range you have your static IPs set. If you are using, say, 192.168.0.1 to 4 as static, for instance, allow the router to serve within the range 192.168.5 to 7. That way it won't serve a clash with your statics. ;)

---

### Post by howefield on 2015-08-07
> **Bucky Ball said:**
> You could set up your router/AP to serve DHCP outside the range you have your static IPs set. If you are using, say, 192.168.0.1 to 4 as static, for instance, allow the router to serve within the range 192.168.5 to 7. That way it won't serve a clash with your statics. ;)

That's the way I'd want to do it. But presumably there is a reason preventing the OP from doing this ? Don't have the Meizu but do have a BQ phone, might have a play later.

---

### Post by stefan_bahrens on 2015-08-07
howefield and Bucky Ball, you are right. This would  be a perfectly reasonable work around. But I am puzzled that setting static ips seems so awkward on the MX4. I'll try to use the command line and vi (as described in the link that howefield posted). I'm wondering if I've just missed something like “Network Manager“ somewhere in the phones settings.

---

### Post by handaxe on 2015-08-07
I would guess it falls under "wishlist" of functionality yet to be implemented.

---

### Post by stefan_bahrens on 2015-08-07
Having had a close look at [http://ubuntuforums.org/showthread.php?t=2279427](http://ubuntuforums.org/showthread.php?t=2279427) ,the link that howefield posted, I believe this method was used to solve the problem (of not being able to configure a wifi network with static IPs) on a BQ Aquaris which has vi installed. I can't see how the same method would work on the MX4. But I have a very basic grasp of anything linux and it could be that I'm just messing up the steps the OP described in the link.

---

