---
title: "firestarter and knetworkmanager question"
date: 2006-04-07
forum: Server Platforms
---

### Post by sal on 2006-04-07
i hope im posting in the right place on the forums.

i run firestarter on kubuntu dapper 6.0 6 with knetworkmanager to handle my wireless on my laptop. so, when i boot the machine i notice that firestarter fails to start. i have to wait untill knetworkmanager connects to the wireless network, then i open firestarter and start it manually every time.

is there a way/setting i could do to make firestarter start automaticly as soon as the wifi connection comes up, or maybe even before hand.

thanks in advance for any help.

---

### Post by John.Michael.Kane on 2006-04-07
when you setup firestarter there should have been an option to [Start the Firewall on dial-out] if this was not checked then this could be why FS is working automatic. 

On a side note since your running kubuntu you may want to try this [http://www.simonzone.com/software/guarddog/#introduction](http://www.simonzone.com/software/guarddog/#introduction)

---

### Post by sal on 2006-04-07
[QUOTE=SD-Plissken]when you setup firestarter there should have been an option to [Start the Firewall on dial-out] if this was not checked then this could be why FS is working automatic. 

On a side note since your running kubuntu you may want to try this [http://www.simonzone.com/software/guarddog/#introduction](http://www.simonzone.com/software/guarddog/#introduction)[/QUOTE]


i like firestarter. it's simple. and im going to add that option to my settings within it that you mention. thanks for the quick responce.

---

### Post by sal on 2006-04-08
[QUOTE=SD-Plissken]when you setup firestarter there should have been an option to [Start the Firewall on dial-out] if this was not checked then this could be why FS is working automatic. 

On a side note since your running kubuntu you may want to try this [http://www.simonzone.com/software/guarddog/#introduction](http://www.simonzone.com/software/guarddog/#introduction)[/QUOTE]


i tried it this morning and i still have to do an /etc/init.d/firestarter start to get it to start. is there another way i could go about automating it that you know of?

thanks.

---

