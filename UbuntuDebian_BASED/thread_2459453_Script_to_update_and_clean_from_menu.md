---
title: "Script to update and clean from menu"
date: 2021-03-19
forum: Ubuntu/Debian BASED
---

### Post by Disabled20241022 on 2021-03-19
Hey fellow ubuntu loving people!

I wanted to create a script that i can run with a 2 clicks but i do not know how to do this.
Start menu > Update.sh (clickable and then auto run script without asking for a password)

In this script i would like to have the following:
- Check for updates of software, kernel (no beta), firmware etc.
- Install them but first show me a customizable list of what to install.
- Remove all of the messaging (noise).
- Then clean the entire system.

So far i could only make this but i am not really sure what it all does:
```
#!/bin/bashset -e


sudo apt-get update
echo -e $TEXT_YELLOW
echo 'Updates checked.'
echo -e $TEXT_RESET


sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt full-upgrade
echo -e $TEXT_YELLOW
echo 'Upgrades finished.'
echo -e $TEXT_RESET


sudo apt clean -y
echo -e $TEXT_YELLOW
echo 'Cache cleared.'
echo -e $TEXT_RESET


sudo apt autoclean -y
sudo apt autoremove -y
echo -e $TEXT_YELLOW
echo 'Packages removed.'
echo -e $TEXT_RESET


sudo apt purge -y $(dpkg -l | awk '/^rc/ { print $2 }')
sudo apt-get purge $( dpkg --list | grep -P -o "linux-image-\d\S+"| head -n-4 )
echo -e $TEXT_YELLOW
echo 'What does this do?'
echo -e $TEXT_RESET


if [ -f /var/run/reboot-required ]; then
echo -e $TEXT_RED_B
echo 'Reboot required!'
echo -e $TEXT_RESET
fi
```

I would love to get some help on this one.

---

### Post by TheFu on 2021-03-19
```
#!/bin/bashset -e
```
is wrong.
You probably want 
```
#!/bin/bash
set -e
```
Details matter.

Any commands you call inside a script should always point to the exact program you want. NEVER trust the PATH. set is a built-in for bash, to there's no path to the program.

Rather than using sudo on separate lines, just the entire program using sudo. This will be faster.
```
$ which sudo
/usr/bin/sudo
```
Any sudo in the program, if you don't change it, should be /usr/bin/sudo. This is important for security.
```
$ which apt-get
/usr/bin/apt-get
```
says that all apt-get uses should be /usr/bin/apt-get. Use the full-path to all programs. the which tool can locate where they are.

apt shouldn't be used inside any scripts.  The apt program warns against this. Heed that warning. Use apt-get instead.

You should look up the full paths for dpkg, awk, grep and other tools in this script.

I have no idea what settings are in $TEXT_YELLOW and  $TEXT_RESET. They aren't set in the script. They aren't standard.
More scripting hints to avoid problems: [https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

If you need to know more about bash and that language, there are beginning, intermediate and advanced bash scripting guides. Google finds them easily.  "absg bash" is a search term, for example.

---

### Post by Impavidus on 2021-03-19
```
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt full-upgrade
```
apt full-upgrade does everything that apt-get upgrade does, and more. apt-get dist-upgrade does everything that apt full-upgrade does, and more. Running all three of them is redundant.

```
sudo apt clean -y
sudo apt autoclean -y
```
apt clean does everything that apt autoclean does, and more. Running both is redundant.

You use a line to purge packages that have remaining config files. The only command here that's going to remove any packages is the apt autoremove command (and apt-get dist-upgrade, once in a million years). You can give that the --purge option, so that your current purge line will never have anything to do.

The second purge line (above the "What does this do" — BTW, make sure you understand every bit of it. A script can do a lot of things automatically in a very short time, so if there's an error, it can do a lot of damage) removes old kernels. They turn autoremovable, so the autoremove command already handles this. It's redundant.

BTW, the features you want are already available in the upgrade manager. Reinventing wheels can be fun, but I would prefer something that really adds something new.

---

### Post by ActionParsnip on 2021-03-19
Which bit is confusing you? This is all pretty simple stuff

---

### Post by TheFu on 2021-03-19
I thought 
```
sudo apt-get dist-upgrade
sudo apt-get full-upgrade
sudo apt dist-upgrade
sudo apt full-upgrade
```
were all the same. 

The manpage for aptitude can shed some light:

```
       full-upgrade
           Upgrades installed packages to their most recent version, removing
           or installing packages as necessary. It also installs new Essential
           or Required packages. This command is less conservative than
           safe-upgrade and thus more likely to perform unwanted actions.
           However, it is capable of upgrading packages that safe-upgrade
           cannot upgrade.

           If no <package>s are listed on the command line, aptitude will
           attempt to upgrade every package that can be upgraded. Otherwise,
           aptitude will attempt to upgrade only the packages which it is
           instructed to upgrade. The <package>s can be extended with suffixes
           in the same manner as arguments to aptitude install, so you can
           also give additional instructions to aptitude here; for instance,
           aptitude full-upgrade bash dash- will attempt to upgrade the bash
           package and remove the dash package.

               Note
               [B]This command was originally named dist-upgrade for historical
               reasons, and aptitude still recognizes dist-upgrade as a
               synonym for full-upgrade.
[/B]
```

dist-upgrade was deprecated for full-upgrade in aptitude, but still works. Aptitude was pushed as the preferred CLI package front-end for APT for at least 5 yrs.  apt-get has been around longer, but thankfully, they also support the common option/aliases for full-upgrade == dist-upgrade to limit confusion.  Same for apt.

BTW, there is also a "safe-upgrade" option in aptitude. If you upgrade from distro release to new distro release the Debian way, calling it "dist-upgrade" makes perfect sense.  Ubuntu created a little tool - do-release-upgrade  - which handles the manual steps recommended by Debian prior to running a dist-upgrade.

Regardless, apt shouldn't be used in any scripts.  There is a warning about this whenever we use apt in a script.  Initially, apt was just a script wrapped around apt-get and dpkg commands. I don't know when that changed.  In a shell, I use apt.  In scripts, I use apt-get.

There are times when the extra brains inside aptitude is very helpful towards solving complex dependency issues.  If the first solution presented isn't to our liking, we can reject it and another will be determined and displayed. This can be rejected too.  I've seen 10 different dependency solutions from aptitude when really complex software with lots of dependencies were on a system.  aptitude has a TUI, so there is a "menu", that works in a terminal on any debian/ubuntu system.  If we don't feel like looking up the apt-mark syntax, aptitude will let us mark packages to hold, which is sometimes helpful.  It is also great at backup-restore time when hundreds of packages are being installed to bring a system back as quickly as possible, but not cause dependency issues.

History can be fun.

---

### Post by DuckHook on 2021-03-19
Though I might get a flag for piling on, my question is similar to Impavidus's: why are you doing this at all?

The functionality that you are trying to automate is already automated&#8212;as part of Upgrade Manager. And while, as Impavidus states, reinventing wheels can be fun, they can also be dangerous. Upgrade Manager has been so thoroughly tested by now that it is pretty much foolproof. Self&#8209;built scripts for something as critical as system upgrades is&#8212;shall we say&#8212;a bit like playing with fire?

Those of us who disable Update Manager and resort to CLI methods are doing so precisely because we want to see all the nitty&#8209;gritty details as they fly by. Moreover, many of us go even futher and install apt-listchanges to pause the upgrade process so that we can pick through intended upgrades to see how they will be monkeying with our system. If you ***don't*** want to see these details, then why aren't you using the also already built&#8209;in auto upgrading feature whereby you won't even know you've been upgraded?

---

### Post by Disabled20241022 on 2021-03-20
The reason for me wanthing this is that i am on popOs (ubuntu based) and the software manager there is slow and i do not like it. CLI is faster and easier however i am lazy and do not like to type it everytime so i wanted to automate the searching for updates + saying what to update + updating it + cleaning everything.

Right now i have made this based upon your suggestions.
```
#!/bin/bash

/usr/bin/sudo /usr/bin/apt-get dist-upgrade -qq
echo 'Updates finished.'
/usr/bin/sudo /usr/bin/apt-get clean -y -qq
echo 'Cache cleared.'
/usr/bin/sudo /usr/bin/apt-get autoremove --purge -y -qq
echo 'Packages removed.'
```

Is this all that i need?
how do i display what has been updated in a neat list?

And how do i launch this from my start menu (with a click of a button)?

---

### Post by deadflowr on 2021-03-20
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by TheFu on 2021-03-20
> **ayudha said:**
>  Right now i have made this based upon your suggestions.
```
#!/bin/bash

/usr/bin/sudo /usr/bin/apt-get dist-upgrade -qq
echo 'Updates finished.'
/usr/bin/sudo /usr/bin/apt-get clean -y -qq
echo 'Cache cleared.'
/usr/bin/sudo /usr/bin/apt-get autoremove --purge -y -qq
echo 'Packages removed.'
```

Is this all that i need?
how do i display what has been updated in a neat list?

And how do i launch this from my start menu (with a click of a button)?

Can't help with the button, but I'd do it this way, if you insist:
```
!/bin/bash

apt_get=/usr/bin/apt-get
log=/var/log/my-apt-get.log

if [ "0" != $(/usr/bin/id -u) ] ; then
  echo "ERROR: Must run with sudo!"
  exit 1;
fi

# Shift old log files and compress
/bin/mv $log $log.1
/bin/gzip $log.1

$apt-get update 2>&1 | tee -a $log

$apt-get dist-upgrade -y 2>&1 | tee -a $log
echo "INFO: Updates finished."

$apt-get autoremove --purge -y  2>&1 | tee -a $log
echo "INFO:Packages removed."

$apt-get **auto**clean -y 2>&1 | tee -a $log
echo "INFO: Cache cleared."

exit 0;

```
Then be certain you always review the logs, since you are forcing a -y.
Really, my script loops over all the systems I manage and runs a bash subroutine on each:
```
sudo_update(){
   ssh $D "sudo $CMD1; sudo $CMD2;"
#  .... and some specific commands are added here after checking the hostname. One system 
# doesn't use a dkms kernel update, so if the kernel has changed, I need to rebuild a driver 
# and install it.
}
```
D gets set to the current hostname-deploy alias
CMD1 is the update
CMD2 is the full-upgrade
In my ~/.ssh/config file, connections to systems use a deploy account for this purpose, which has keybased authentication and sudo access to apt-get without a password.

The entire script is called weeklyupdates. I run it ... er ... weekly like this:
```
$ weeklyupdates | tee ~/log.weekly
```
I'm lazy, but not so lazy that I can't quickly review the proposed updates and hit <enter> to accept. It is just one terminal running. I'm actually running it now as part of my Saturday morning patch ritual.  I see that kernel module is being built now.  Takes about 20 minutes ... which is about the time reading email, doing a few posts here will take.

Everyone does this sort of simple scripting.

weeklyupdates is doing the 2nd physical server now ... looks like a new kernel for that machine too.

Now doing the pihole inside an lxd container.... also updating the pihole software and pulling fresh block lists.

---

### Post by oldfred on 2021-03-20
TheFu left a few typos, I will leave it for OP to resolve.

If you want colors, looks bit better with black background that is default in my konsole/terminal using Kubuntu:

You can do this:

```
YELLOW="\033[1;33m"
RED="\033[0;31m"
ENDCOLOR="\033[0m"

if [ $USER != root ]; then
  echo -e $RED" Must run with sudo!"
  echo -e $YELLOW"Exiting..."$ENDCOLOR
  exit 1;
fi
```

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ bash fu_clean.sh  [/COLOR]
[COLOR=#b21818] Must run with sudo![/COLOR]
[COLOR=#ffff54]**Exiting...**[/COLOR]

[/FONT]
```

---

### Post by deadflowr on 2021-03-20
If you use apt instead of apt-get then the clean commands would be moot,
as apt automatically clears out the package caches upon successful package installation.
(apt-get does not do that)

---

### Post by Disabled20241022 on 2021-03-20
Thanks guys!
Right now i have this working:
```
#!/bin/bash

apt_get=/usr/bin/apt-get
BWhite='\033[1;37m'


sudo apt-get update -qq 2>&1 | tee -a


sudo apt-get dist-upgrade -qq -y 2>&1 | tee -a
echo -e $BWhite"> Updates zijn gedaan."


sudo apt-get autoremove --purge -qq -y 2>&1 | tee -a
echo -e $BWhite"> Pakketten zijn verwijderd."


sudo apt-get autoclean -qq -y 2>&1 | tee -a
echo -e $BWhite"> Cache is opgeschoond."


exit 0;
```

What i actually wanted was silence in the terminal which i have now but i wonder when there are updates if it tells me what the updates will be??

And how do i launch this script from my arcmenu (startmenu)?
I have it in there but ```
/mnt/878b409f-e397-4323-a3b9-21bb5c1e1489/upgrade.sh
``` does nothing

---

### Post by Disabled20241022 on 2021-03-20
I just checked for updates and there are 2 but this script does not find them and install them.

---

### Post by DuckHook on 2021-03-20
> **ayudha said:**
> I just checked for updates and there are 2 but this script does not find them and install them.
> **oldfred said:**
> TheFu left a few typos, I will leave it for OP to resolve.
This is a good learning moment. You were already alerted by oldfred. It is never a good idea to just cut and paste scripts handed to you without understanding what they are meant to do, followed by a basic syntax/error/sanity check.

---

### Post by Disabled20241022 on 2021-03-20
well.. when i put in sudo apt update it runs the command but when i input sudo apt-get update it does not.

```
[FONT=inherit]So, in short... [/FONT]2>[FONT=inherit] redirects stderr to an (unspecified) file, appending [/FONT]&1[FONT=inherit] redirects stderr to stdout.[/FONT]
```
Not sure what that means. perhaps it has to do with the log files that i removed?

And then there is ```
tee -a
``` which i can't find on google.

---

### Post by TheFu on 2021-03-20
> **oldfred said:**
> TheFu left a few typos, I will leave it for OP to resolve.

Purely by accident, but the one I see now is consistently made 3+ times.

Hint: $apt-get is wrong in my script. This error is typical that can be made by anyone. ;)

Every command in unix has a local manpage that explains how to use it.  **man  tee**

Not having a log is a beginner mistake. Please don't do that. 1 of 100 times, you'll need that logfile.

---

### Post by oldfred on 2021-03-20
The update part of my script partially copied from someone else & partly just my own commands, now includes a lot of housecleaning.
And to monitor sizes, I include these
```

DISK_USAGE_BEFORE_CLEANUP=$(df -hT -x squashfs -x tmpfs -x devtmpfs)
.... Various find (so older only) & rm commands of older info, logs, trash,  caches, thumbnails, Firefox & Thunderbird vacuums. 
echo "==> Disk usage before cleanup"
echo "${DISK_USAGE_BEFORE_CLEANUP}"

echo "==> Disk usage after cleanup"
df -hT -x squashfs -x tmpfs -x devtmpfs
echo -e '\E[34;47mMoooo'; tput sgr0
apt-get moo
```

---

### Post by Disabled20241022 on 2021-03-24
And still how to launch it from the startmenu?

---

### Post by TheFu on 2021-03-24
> **ayudha said:**
> And still how to launch it from the startmenu?

Is that a trick question?  Doesn't a dbl-click work after you place it into the menubar?  Perhaps this question is release and DE dependent?

---

### Post by Disabled20241022 on 2021-03-26
I just pointed it to the sh file but nothing is happening.

---

### Post by TheFu on 2021-03-26
> **ayudha said:**
> I just pointed it to the sh file but nothing is happening.

What do you expect to happen?
Did you set the script file permissions to allow execute?
Did you setup sudo to allow the userid NOT to need a password for apt-get commands with the options above?
Above, I posted a script that doesn't use sudo, which is how I'd do it - if I insisted on something like this. The sudo would be outside the script for a number of reasons.

You can add an option for detailed output from a script.  The beginner, intermediate and advanced bash scripting guides explain how.

---

### Post by Disabled20241022 on 2021-03-28
I 'm expecting it to open the terminal and run the script.
I have set it to execute.
I have sudo in the script.

---

### Post by mikewhatever on 2021-03-28
Here you go: [https://askubuntu.com/questions/38661/how-do-i-run-sh-scripts](https://askubuntu.com/questions/38661/how-do-i-run-sh-scripts)

Not sure if it works in Pop, but worth a try.

---

### Post by TheFu on 2021-03-28
If a terminal is desired, it needs to part of the command calling the script. Pick which terminal carefully.
Be certain the /full/path/to/the/script in the call.

I'd probably create a .desktop file for the script to be run with the Exec= line something like
```
/usr/bin/xterm -e  /usr/bin/sudo  /usr/bin/top
```
Note the that running sudo and top have the full path. These happen inside an xterm. Another options like geometry, fonts, colors, need to be before the -e option.
```

       -e program [ arguments ... ]
               This option specifies the program (and its command line
               arguments) to be run in the xterm window.  It also sets the
               window title and icon name to be the basename of the program
               being executed if neither -T nor -n are given on the command
               line.

               NOTE: This must be the last option on the command line.
```

---

### Post by Disabled20241022 on 2021-03-29
Does nothing for me.
This is what i have.

```
#!/bin/bash

BWhite='\033[1;37m'


/usr/bin/xterm -e /usr/bin/sudo /usr/bin/top
apt_get=/usr/bin/apt-get


sudo apt-get update -qq 2>&1 | tee -a


sudo apt-get dist-upgrade -qq -y 2>&1 | tee -a
echo -e $BWhite"> Updates zijn gedaan."


sudo apt-get autoremove --purge -qq -y 2>&1 | tee -a
echo -e $BWhite"> Pakketten zijn verwijderd."


sudo apt-get autoclean -qq -y 2>&1 | tee -a
echo -e $BWhite"> Cache is opgeschoond."


exit 0;
```

Clicking START > LINK (which opens the file at /mnt/878b409f-e397-4323-a3b9-21bb5c1e1489/upgrade.sh)

---

### Post by Disabled20241022 on 2021-04-01
But this does nothing.

---

### Post by deadflowr on 2021-04-01
> Clicking START > LINK (which opens the file at /mnt/878b409f-e397-4323-a3b9-21bb5c1e1489/upgrade.sh)
Do you mean it opens the file, like in a text editor or something?

---

### Post by TheFu on 2021-04-01
> **ayudha said:**
> But this does nothing.

Do you understand bash variable substitution?  
I though you did since $BWhite is used correctly, but then $apt_get is not.

The tee command requires an output file. For some reason, that has been removed and for some reason -qq was added to the apt-get lines.

[https://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](https://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)

```
/usr/bin/xterm -e  /usr/bin/sudo  /usr/bin/top
```
was just an example so you could see how to have a new terminal open and run a command.  top is just an example command.  It isn't needed in your script.  The intention is for the command to be this script filename.  Also the intention is for the script not to need sudo **inside** at all.

A week ago, I posted a script with 1 accidental typo that was made consistently - so it was really 1 error. The problem was spelled out in another post, so ... 

We are obviously having miscommunications. I apologize. Hopefully, someone else can be clearer than I've been.

---

### Post by Disabled20241022 on 2021-04-01
no it does just nothing.
I have a start menu and in there i create a link to [COLOR=#000000][I]/mnt/878b409f-e397-4323-a3b9-21bb5c1e1489/upgrade.sh)
which needs to contain the script, it has to open up a terminal.[/I][/COLOR]

---

### Post by Disabled20241022 on 2021-04-01
i do not understand that. bit of a noob to all of this.

---

### Post by CelticWarrior on 2021-04-01
> **ayudha said:**
> i do not understand that. bit of a noob to all of this.

You can't be a noob and expect to be able to pull this one out. One has to give, either you evolve past the noob stage or you don't do it.
And really [there isn't a good reason for doing what you intend]("https://ubuntuforums.org/showthread.php?t=2459453&p=14027302#post14027302") but there are, of course, plenty of reason to evolve irrespective of goals and motivations.

---

### Post by Disabled20241022 on 2021-04-02
There are alwasy reasons and they are as good as they are for that person at that specific time.
I thought it was easy, make a script, have it run by pressing the button from the start menu but it seems that it is much harder then i thought.

---

