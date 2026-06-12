---
title: "is firestarter running in the background?"
date: 2007-06-12
forum: Server Platforms
---

### Post by spamalot on 2007-06-12
hi everyone,

how can i check if firestarter is running in the background? it does not show in system monitor>processes even if i manually start if from system>firestarter, so i need another way to check...

thanks!

---

### Post by AlexThomson_NZ on 2007-06-12
Try this in a terminal window:

ps -A | grep firestarter

---

### Post by netlogic on 2007-06-12
firestarter starts during the boot.
you can manually start the service by

sudo /etc/init.d/firestarter start
other options {start|stop|restart|force-reload|lock|status}

---

### Post by spamalot on 2007-06-13
thanks AlexThomson_NZ  and netlogic!

ps -A | grep firestarter (logged as root) produces nothing, neither does ps ux show anything related to firestarter *even* after i manually start it...

---

### Post by deanjm1963 on 2007-06-13
Firestarter is only a "front-end" to the inbuilt firewall called IPTABLES which is always on. So yes, your firewall is running but there is actually no need to be running Firestarter unless you are constantly changing firewall rules, etc.

---

### Post by netlogic on 2007-06-13
In case, I wasn't clear. 
Firestarter is only an iptable script frontend.
it launches the script at the boot.
Launch firestarter to change your script.

If it makes you happier to monitor your firewall during the login.
[URL="http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html"]
Firestarter howto[/URL]

file in etc/init.d/firestarter controls the /etc/firestarter/firestarter.sh

---

### Post by spamalot on 2007-06-15
thank you all for clarifying. 

what if i'm still a little paranoid ;) and i want to be sure that iptable is acting as directed by the preferences in firestarter. for example, my prefs show IMCP filtering for echo request etc. how can i verify that? i'm guessing 
$iptables -t filter -L something
correct? what would that something be?

---

### Post by netlogic on 2007-06-15
i think you want to spend some time reading the files in the following folder
/etc/firestarter

I think that will help you understand more. :)

---

