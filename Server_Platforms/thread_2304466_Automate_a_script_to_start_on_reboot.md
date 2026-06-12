---
title: "Automate a script to start on reboot ?"
date: 2015-11-27
forum: Server Platforms
---

### Post by soamz on 2015-11-27
Hi, i have a ubuntu server and I have a script in it at /usr/softwareWhenever the server reboots, I have to goto the above path and then manually start this command every time  ./ooklaserver.sh start

is there a way I can automate this process, so this automatically works ?

---

### Post by Lars Noodén on 2015-11-27
If you want it to run as root, just add it to /etc/rc.local right before the line "exit 0"
If you want it to run as a particular user, then precede it with sudo 

```

sudo -i -u *soamz* */usr/software/somescript*

```

However, that way it will run when the machine itself boots, not necessarily when a user has logged in or anything like that.  Nor can that method be used to launch a graphical program.

---

### Post by soamz on 2015-11-27
yes, I need it to auto run, when the machine boots due to power failure. 
So, the above works ?

---

### Post by Lars Noodén on 2015-11-28
Yes, it is one method that works.  Another is to use a cron job with the @reboot shortcut.

---

### Post by soamz on 2015-11-28
Okay added this, 
[FONT=Avenir Next]sudo -i -u soamz /usr/software/./ooklaserver.sh start[/FONT]

Im on Mac terminal. 
Did vi /etc/rc.local , but the esc doesnt save the file.

---

### Post by ian-weisser on 2015-11-28
> **soamz said:**
> Did vi /etc/rc.local , but the esc doesnt save the file.

That's right, <esc> doesn't do that in vi.
See [http://www.colorado.edu/oit/services/web-content-applications/www-basic-content-management/help/unix-guide/vi-commands](http://www.colorado.edu/oit/services/web-content-applications/www-basic-content-management/help/unix-guide/vi-commands)
Look under 'file management commands'

---

### Post by soamz on 2015-11-29
ALL DONE. 
But the script wont start automatically. 
I had to manually type it in.

I asked a friend and he said have to do cron. 
So, whats the command to run the cron for this script ?

[COLOR=#000000][FONT=Avenir Next]sudo -i -u soamz /usr/software/./ooklaserver.sh start[/FONT][/COLOR]

---

### Post by ian-weisser on 2015-11-29
> **soamz said:**
> I asked a friend and he said have to do cron.

I'm sure your friend is a nice person, but I think that's bad advice.

The *reason* for failure is important now.
Maybe your script relies upon environment variables that are unavailable.
Maybe your script relies upon services that aren't up yet.
Maybe your script is working just fine, but sending your output to /dev/null.
Maybe lots of possible causes.
If your job fails under rc.local, it may (or may not) fail under cron, too.

There are many ways to run a job at startup before login, or after login, or pretty much any other time you choose.
rc.local is one, and it works very well.
cron is another, and it also works very well.

---

### Post by soamz on 2015-11-29
Okay since rc.local has failed. 
What shall I do now ?

---

### Post by Lars Noodén on 2015-11-29
By what symptoms does it show that it has failed to run?

---

### Post by soamz on 2015-11-29
> **Lars Noodén said:**
> By what symptoms does it show that it has failed to run?

If the script would have run, my page would have opened which is dependent on it. 
But it failed. 

And I had to start it manually with the same command. 
So, I said, it failed.

---

### Post by ian-weisser on 2015-11-29
> **soamz said:**
> my page would have opened which is dependent on it.

If you want a script that (for example) opens a web page, that is a *post-login *task, not a *boot* task. Very different. 

All boot tasks (including rc.local and cron @reboot) *must* be headless - no display. Boot output is logged instead of displayed.
Any display-related actions or scripts before login will always fail, regardless of how you initiate them. Including rc.local and cron.
Reason: The display server isn't started until *after* login is successful.

Instead, try putting your script in your ~/.config/autostart/ directory.
Items in ~/.config/autostart/ are run after login, after the display server and Desktop Environment are up and running.
The script should run without sudo. Items run as your user, since they are within your user's environment.

When troubleshooting startup scripts of any kind, outputting debug messages to logfiles (instead of the screen) can be a very handy technique to find the problem.

---

### Post by soamz on 2015-11-29
Is basically, the script has to run and thats it. 
Because, if it runs successfully automatically, then the job is done. 

When it runs, then the process starts. 
I test it by going to a URL. If it opens, that means the process is running. If its not, that means its not working. 

So where to place finally ?

---

### Post by Lars Noodén on 2015-11-29
> **soamz said:**
> 
I test it by going to a URL. If it opens, that means the process is running. If its not, that means its not working. 

So where to place finally ?

That kind of test will only work from an active graphical log in.  What you might do is put something in your script that does not need a graphical login to see if it has run.  Try adding at the end of your script, something like this:

```

/bin/date > /tmp/foo.txt

```

and then see if there is a file called /tmp/foo.txt after you boot.

---

### Post by soamz on 2015-11-29
Here is what I do now :
When the server reboots, i do this :

cd /usr/software

then 
./ooklaserver.sh start 


Then it says, starting daemon and it starts and when I refresh the page on browser, its opening. 


So, which file shall I paste this exact code ?

---

### Post by Lars Noodén on 2015-11-29
It would go in the file ooklaserver.sh

but can you run the script as /usr/software/ooklaserver.sh directly instead of using cd?  Or must it be in the same working directory?

---

### Post by soamz on 2015-11-29
You mean edit [COLOR=#000000]ooklaserver.sh using sudo nano and enter what ? [/COLOR]

---

### Post by ian-weisser on 2015-11-29
> **soamz said:**
> So, which file shall I paste this exact code ?
It's hard for us to answer that question...because it's entirely the wrong question.

Did you try ~/.config/autostart?

---

### Post by ian-weisser on 2015-11-29
> **soamz said:**
> So, which file shall I paste this exact code ?
It's hard for us to answer that question...because it's entirely the wrong question.

Are you running an Ookla server?
Or are you querying an Ookla server for ping or speedtest data?

---

### Post by soamz on 2015-11-29
> **ian-weisser said:**
> It's hard for us to answer that question...because it's entirely the wrong question.

Did you try ~/.config/autostart?


Okay will sudo nano /.config/autostart

and paste this, 

/usr/software/./ooklaserver.sh start

---

### Post by soamz on 2015-11-29
> **ian-weisser said:**
> It's hard for us to answer that question...because it's entirely the wrong question.

Did you try ~/.config/autostart?


Okay will sudo nano /.config/autostart

and paste this, 

/usr/software/./ooklaserver.sh start

> **ian-weisser said:**
> It's hard for us to answer that question...because it's entirely the wrong question.

Are you running an Ookla server?
Or are you querying an Ookla server for ping or speedtest data?

I have applied to become a speedtest host, so this is the host server. 
Thats why the Ookla server has to always on and running, or the host wont work.

---

### Post by ian-weisser on 2015-11-29
Ah. We really needed to know that in Post #1 to help you better,

You have installed the ookla service into a non-standard location, and are trying to control it in a non-standard way, for a Debian-based system. Those are not fatal mistakes, but do indicate that you haven't done proper research before starting the project. It will also make maintaining and troubleshooting the server harder in the future.

It's your system - you can build it whatever way you wish
Building  it the correct way takes a bit longer up front, but makes ongoing maintenance and support *much* easier for you.

You really should be using the system's init (Upstart or systemd) to supervise the service instead of script. init will happily start, restart, respawn in case of crash, and stop the service based upon any criteria you like, and it's the expected way to manage services. For example, network services (like ookla server) are typically started upon network-up, and respawn automatically in case of crash. init service/config files replaced cumbersome scripts long, long ago.

Are you skilled in Debian/Ubuntu security practices? An internet-accessible server, even for such simple services, will be a primary target for perhaps thousands of break-in attempts daily. Your system...*and perhaps everything else on your company's LAN*...may be at risk of compromise.

---

### Post by soamz on 2015-11-30
> **ian-weisser said:**
> Ah. We really needed to know that in Post #1 to help you better,

You have installed the ookla service into a non-standard location, and are trying to control it in a non-standard way, for a Debian-based system. Those are not fatal mistakes, but do indicate that you haven't done proper research before starting the project. It will also make maintaining and troubleshooting the server harder in the future.

It's your system - you can build it whatever way you wish
Building  it the correct way takes a bit longer up front, but makes ongoing maintenance and support *much* easier for you.

You really should be using the system's init (Upstart or systemd) to supervise the service instead of script. init will happily start, restart, respawn in case of crash, and stop the service based upon any criteria you like, and it's the expected way to manage services. For example, network services (like ookla server) are typically started upon network-up, and respawn automatically in case of crash. init service/config files replaced cumbersome scripts long, long ago.

Are you skilled in Debian/Ubuntu security practices? An internet-accessible server, even for such simple services, will be a primary target for perhaps thousands of break-in attempts daily. Your system...*and perhaps everything else on your company's LAN*...may be at risk of compromise.


Okay!
So, whats the final file where I should be placing this to start ?

And no, Im a beginner at Ubuntu server. 
But if you tell what exactly I should secure, then I will hire someone and get all the 5 new servers properly secured. 
All 5 servers are installed with Ubuntu server only. 

Let me know please!

---

