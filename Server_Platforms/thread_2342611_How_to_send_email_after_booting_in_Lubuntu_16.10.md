---
title: "How to send email after booting in Lubuntu 16.10?"
date: 2016-11-08
forum: Server Platforms
---

### Post by ianmanning on 2016-11-08
I have Lubuntu 16.10 installed on an HP Microserver Gen8, primarily for use as a headless disk server.  I want to receive an email whenever the machine reboots, so have added the necessary commands to /home/myuser/.config/lxsession/Lubuntu/autostart, but am not receiving the email. The full autostart file is below:

```
postfix start
/usr/bin/x11vnc -xkb -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -forever -bg -rfbport 5900
tightvncserver
echo "HP Microserver has rebooted" | mail -s "HP Microserver reboot" myemail@myemailcom

```

If I execute the last line manually from the Terminal immediately after the system has booted the email gets sent, so my mail setup seems fine.

Have I misunderstood how I should be trying to do this?

---

### Post by howefield on 2016-11-08
Moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by SeijiSensei on 2016-11-08
Try specifying the full path, /usr/bin/mail, in the command.  Any better?

Also, you can't start Postfix as an ordinary user.  You have to be root to do that since it binds to a port < 1024.  You should be starting Postfix at boot and letting it run as a daemon in the background.

---

### Post by ianmanning on 2016-11-08
> **SeijiSensei said:**
> Try specifying the full path, /usr/bin/mail, in the command.  Any better?

Also, you can't start Postfix as an ordinary user.  You have to be root to do that since it binds to a port < 1024.  You should be starting Postfix at boot and letting it run as a daemon in the background. 

Hmm...that's strange - Postfix does seem to be starting up at boot time ...????

---

### Post by darkod on 2016-11-09
Even before you continue playing with this server, let me warn you that using non-LTS release (like 16.10) is not really recommended. Linux servers (and all servers in general) are for stability and long time running. You decided to install a version that has only 9 months of support starting from 2016.10 which means the support ends 2017.07. Just about when you have finished tweaking it, it will not have any security or bug fixes any more.

For servers use only LTS releases, the current one being 16.04. They come out every 2 years and have 5 years of support.

And about using Lubuntu (with GUI) as opposed to Ubuntu Server (no GUI), that's not the standard way to run linux servers, but I assume you are aware of that too... You can try running ubuntu server instead of lubuntu.

---

### Post by ianmanning on 2016-11-09
> **darkod said:**
> Even before you continue playing with this server, let me warn you that using non-LTS release (like 16.10) is not really recommended. Linux servers (and all servers in general) are for stability and long time running. You decided to install a version that has only 9 months of support starting from 2016.10 which means the support ends 2017.07. Just about when you have finished tweaking it, it will not have any security or bug fixes any more.

For servers use only LTS releases, the current one being 16.04. They come out every 2 years and have 5 years of support.

And about using Lubuntu (with GUI) as opposed to Ubuntu Server (no GUI), that's not the standard way to run linux servers, but I assume you are aware of that too... You can try running ubuntu server instead of lubuntu.

Thanks for the feedback. This is a home setup. I'm a Windows man looking for a sensible solution for a secondary backup server, and Lubuntu was recommended to me as it was lightweight and had a decent GUI. Since this will not be internet-facing the security patches are not quite so important as they might otherwise be, and given the limited nature of its role I hope that support won't be either. 


I was hoping that getting something as simple as this to work, in ANY Linux distro, wouldn't cause too many problems!

---

### Post by darkod on 2016-11-09
If what you are looking for is running a script on boot, I usually put that in /etc/rc.local (above the exit 0 line).

Create your script (for example simple bash script), make it executable, and put the full path in /etc/rc.local. That will run as root at the end of each boot process.

Since you are using this on headless server (where by default you don't login after boot), I'm not sure that autostart thing in your home folder is working as you expect it. It might be, i don't know, but it might not... The rc.local always works and runs the commands as root which is what you need.

---

### Post by ianmanning on 2016-11-09
> **darkod said:**
> If what you are looking for is running a script on boot, I usually put that in /etc/rc.local (above the exit 0 line).

Create your script (for example simple bash script), make it executable, and put the full path in /etc/rc.local. That will run as root at the end of each boot process.

Since you are using this on headless server (where by default you don't login after boot), I'm not sure that autostart thing in your home folder is working as you expect it. It might be, i don't know, but it might not... The rc.local always works and runs the commands as root which is what you need.

Many thanks - creating an /etc/rc.local file did the trick!

---

### Post by bearlake on 2016-11-09
Lots of good info in this thread.

Hope you mark it as solved to help other folks.

Select Thread tools above your 1st post and select solved.

---

### Post by ianmanning on 2016-11-11
Hmmm....maybe I spoke too soon...I just rebooted the server for the first time in headless mode (no monitor or keyboard connected), which is how I plan to use it. I didn't get the email at startup. Is there any reason why rc.local wouldn't execute if no keyboard and monitor are connected?

---

### Post by darkod on 2016-11-11
Nope... I have a HP Microserver with no monitor or keyboard and it has a script in rc.local, and it executes on each boot. It never missed even one boot since I configured it.

Double check BIOS settings because there are option to stop boot if there is no keyboard present (remains of ancient times when it was assumed you would have KB on the machine). If that option is active, the BIOS will stop your boot, not ubuntu. Check any BIOS settings that might relate to something like that.

Also, try booting it only with monitor, no KB, to check how it acts (you can at least see something on the monitor).

PS. And did you make the script executable, I believe that is necessary:
```
sudo chmod +x /path/filename
```

PPS. On the other hand, I am running ubuntu server with no gui, and you lubuntu with a gui. So it might act differently when there is no monitor and KB...

---

### Post by SeijiSensei on 2016-11-11
Reboot the server, then run 
```
ps ax | grep postfix | grep -v grep
```  
If that turns up empty, then Postfix isn't being started at boot.  In 16.10, with systemd, you might need to run the command
```
sudo systemctl enable postfix
```
to have Postfix start up at boot though usually Postfix is automatically enabled if installed from the repositories.  You can then start the server manually with
```
sudo systemctl start postfix
```

Also, you do know that 16.10 has only nine months of support, right?  If you're building a server, use a release with long-term support like 16.04.

---

