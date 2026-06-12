---
title: "Notifying user via stdout from a Python daemon script"
date: 2015-02-02
forum: Ubuntu Application Development
---

### Post by veddox on 2015-02-02
I am currently working on a Python script that is designed to warn the user when his computer's battery is getting low while he is working in terminal/tty. (See the Launchpad [home page]("https://launchpad.net/comp").) It is started via an entry in /etc/rc.local, and is supposed to print out a warning message to every terminal window/tty when the battery level gets critical. Unfortunately, it doesn't do that ;-)

Here's the code:
```
def check_battery():
    global sleep_time
    try:
        os.system("comp battery > /tmp/battery")
        batt_file = open("/tmp/battery", "r")
        batt_state = batt_file.read()
        batt_file.close()
        os.remove("/tmp/battery")
        print("Checking battery state...") #Debugging statement
        if "critical" in batt_state:
            print("ATTENTION: battery state is critical!")
            sleep_time = 30
    except IOError:
        print("battery-warning-daemon: IO error, killing task!")
        exit()
```

I know that the script is running, because it regularly prints to a logfile. However, its messages do not appear anywhere. I simply used print() here, because I thought that would be sufficient. It obviously isn't, so how do I make sure that the relevant messages are actually outputted?

---

### Post by veddox on 2015-02-02
Update: I just realised the print() does actually work - sort of. Whenever I log out of Unity (or i3, another window manager I use), the X sessions seems to be temporarily suspended while Unity hands over to LightDM. Within that half second, I see the screen covered with a load of "Checking battery state..." debug messages.

My X session is on tty7. No other tty sees anything, neither does any terminal emulator window I have open. But that is where it would be most needed, of course. How do I get Python to print to every tty instead of just the one?

---

### Post by veddox on 2015-02-06
In a classical case of "GIYF" (or rather DIYF - DuckDuckGo is your friend ;-) ) I have managed to solve this on my own. The trick is to redirect stdout to the various ttys available, which I do with the following method:
```
'''
Print a warning message to every tty available
'''
def warning(message):
    message = "\n"+message
    available_devs = os.listdir("/dev")
    for t in range(1, 102): #Presumably there won't be more than 100 ttys...
        tty = "tty"+str(t)
        if t == 101:
            tty = "/dev/tty" #Don't forget to reset it to the default...
        if tty in available_devs:
            tty = "/dev/"+tty
            try:
                sys.stdout = open(tty, "w")
                sys.stdout.write(message)
            except (IOError, OSError):
                pass


```
Perhaps somebody will find this useful at some point.

---

### Post by ian-weisser on 2015-02-06
Rather than redirect output to a specific TTY, did you consider using the 'wall' command to send to all ttys?

Usually the power manager emits battery updates on dbus. Perhaps all you need is a listening service for that? Then your service need not be a daemon at all.

---

### Post by veddox on 2015-02-09
I didn't know about the wall command - thanks for the comment!

I'll also have a look into dbus, I've never worked with that before.

---

