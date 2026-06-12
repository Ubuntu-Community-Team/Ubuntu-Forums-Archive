---
title: "sudo in crontab"
date: 2011-01-02
forum: Server Platforms
---

### Post by ingeva on 2011-01-02
I need to run a sudo command in a script run by crontab.
Crontab must be run under a user account because it needs the user environment.

I have looked around the forum and many other places, and I have tried several methods without finding a working solution.
I've seen someone use "gksudo echo" before sudo commands in scripts, but that doesn't work in a server environment (no Gnome etc).

I've tried placing the password in a file (mypaswd) and done something like this:

sudo command <mypaswd

but the password is not read. Besides, placing the password in a plain-text file doesn't seem to be very smart ... :)

Any better ideas?
(The rest of the crontab script runs just fine, but I suspect the script above to be waiting for input from tty1, because after the script is supposed to run, communication from tty1 is almost hopeless).

---

### Post by matt_symes on 2011-01-02
Hi

I don't like this technique, but this is one way of doing it. Add the command to the sudoers file allowing the command to be run without a password.

Edit the sudoers file

```
sudo visudo
```

and add entries such as.

```
your_username ALL=NOPASSWD: /path/to/command
```

replacing your_username and /path/to/command.

Another way to do it is to run the script root but just make sure the script contains the environment of the user.

What does the script do?

Kind regards

---

### Post by ingeva on 2011-01-02
> **matt_symes said:**
> Hi

```
your_username ALL=NOPASSWD: /path/to/command
```replacing your_username and /path/to/command.

Another way to do it is to run the script root but just make sure the script contains the environment of the user.
What does the script do?
Kind regards
I tried something like that but I guess I misunderstood the description because it didn't work.

The script makes backup of some protected files.
I've made a temporary solution: Hard-coding some of the command lines by using
```
echo "command lines with $variables" >>scriptfile
```
because once the command is established, it need not be changed until the
next system generation.

I'll see how that works, and if not I'll use your tip. Thank you!

---

### Post by CharlesA on 2011-01-02
Hi there,

If I'm going to be running scripts in cron, I try to use the full path to each command.

I also define variables in each script, so I don't have to rely on the user environment variables for the script to work.

---

### Post by ingeva on 2011-01-02
> **CharlesA said:**
> Hi there,
If I'm going to be running scripts in cron, I try to use the full path to each command.
I also define variables in each script, so I don't have to rely on the user environment variables for the script to work.
My script contains the PATH= definition so that's not necessary for me.
The problem is the same if the variables actually vary according to the user, because then you'll need one script for each user.
Right now that's not a problem for me since I'm the only user, but I wouldn't like to have to modify all my scripts just because my son came by. :)

Anyway, now I have extracted the commands needing "sudo" to a new script that is hardcoded and will only have to be re-written after a major system upgrade, and then it's done automatically. :)

---

### Post by CharlesA on 2011-01-02
Ah I see.

Thanks for the info. :)

---

### Post by CharlesA on 2011-01-02
Doublepost.

---

