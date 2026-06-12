---
title: "Shell script help: change to root mid script"
date: 2009-10-13
forum: Server Platforms
---

### Post by djbon2112 on 2009-10-13
Hello. I'm having a bit of an issue getting this working.

I want a script that basically replaces sudo, asking for a bit of information and writing it to a log file, then executing the command. I've got the first part (collecting the data) down, but I'm having problems with the second part.

What I need to happen is the user enters the sudo password (every time the command is run), then it executs a bunch of commands as root (i.e. writing to the log file), then finally executes all the commands that were passed to it.

I tried just adding "sudo" to every command but it ran into problems when it goes to execute the commands. I was trying to use 'sudo `$*`' but that doesn't work. It needs to run any possible command sent to it, with a diffeing number of args each time (i.e. for running complex commands, like 'shellscript1 apt-get install  pidgin'). Also, the problem of sudo staying authorized for a set time (versus asking each time this is run) is a problem.
 
So, I propose, how would *you *script this?

```
PSEUDOCODE:

<do stuff that I already have worked out>

Ask for root password, every time (not like sudo where once lasts 10 minues)

Write to log file using root password authentication

Execute the entire list of commands passed to this script using root password authentication

Exit

```

---

### Post by amingv on 2009-10-14
Maybe this helps?

```

<do stuff that you already have worked out>

#sudo -k will make it ask for the password on the next command
sudo command1 && sudo -k
sudo command2 && sudo -k

sudo echo $DATE $LOG_INFO >> myfile.log && sudo -k

#will ask password once for every argument
for foo in $@; do sudo $foo && sudo -k; done

```

If you want it to skip asking the password for a command, just remove the '&& sudo -k' from the command before. Bear in mind though that if the execution of the command surpasses 10 minutes it may ask the password again.

---

### Post by scorp123 on 2009-10-14
> **djbon2112 said:**
>  I want a script that basically replaces sudo  Isn't that a bit like reinventing the wheel and the fire?

And if you have to use "sudo" inside your script to make things work, then your script can't really be a "replacement".

As for your troubles .... Why not add the few commands you need to execute into **/etc/sudoers**? Beware: You have to use the **"visudo"** command to edit that one. Trying to edit the file with anything else without applying the proper steps may cause strange side effects.

visudo tutorial:
[http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/](http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/)

sudoers tutorial:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

So the goal here would be that you add a few commands to /etc/sudoers so you don't need to enter the password every time ... and thus your script wouldn't stop in the middle, it would run through.

And yes, in theory you could edit /etc/sudoers in such a way and disable passwords completely ... **_[COLOR="Red"]I strongly advise against that because it's a really great way of hosing your system.[/COLOR]_**

So please: Only really add the "NOPASSWD" where it is really really needed.

---

### Post by djbon2112 on 2009-10-14
> **scorp123 said:**
> Isn't that a bit like reinventing the wheel and the fire?

And if you have to use "sudo" inside your script to make things work, then your script can't really be a "replacement".

As for your troubles .... Why not add the few commands you need to execute into **/etc/sudoers**? Beware: You have to use the **"visudo"** command to edit that one. Trying to edit the file with anything else without applying the proper steps may cause strange side effects.

visudo tutorial:
[http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/](http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/)

sudoers tutorial:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

So the goal here would be that you add a few commands to /etc/sudoers so you don't need to enter the password every time ... and thus your script wouldn't stop in the middle, it would run through.

And yes, in theory you could edit /etc/sudoers in such a way and disable passwords completely ... **_[COLOR="Red"]I strongly advise against that because it's a really great way of hosing your system.[/COLOR]_**

So please: Only really add the "NOPASSWD" where it is really really needed.
It's not to reinvent the wheel, it's basically so I can give my game server admins the password to an account with sudo priviledges, but at least have some way to track if they do things to the system at large.

It would "replace" sudo in the user's shell using an alias, but that's one of the reasons I didn't want to use "sudo" within the command itself. However, I was also thinking I could eliminate the alias at the start of the script and replace it at the end, however I don't know if I need to do that.

Also, writing to the files is about 5 lines, and the file they're writing to is owned by root and has 700 permissions.

I'm going to give some of amingv's tips a shot, and see how it goes.

EDIT: I also forgot to mention, that I don't want to just add the commands to sudoers because I need this to be very portable and deployable at a moment's notice with many different possible situations. Always adding the dozens of commands I may need will take forever.

EDIT 2: I've got the script working perfectly, except for what I ask in the next post! Here it is, if anyone is curious. I have the file as /sbin/sudoauth.sh and the user in question has an alias for sudo='/sbin/sudoauth.sh'.

```

#!/bin/bash

#
# This script replaces the standard "sudo" command on the public LanNET servers.
# It requests the full name of the user requesting the authorization, as well
# as who gave them permission to make this modification. The entered data,
# along with a record of who is logged in at the time and from where, is
# stored in a root-viewable text file at /var/lannet/sudoauth.log
#
# This script is hereby released under the GNU GPL v3. For details of the license,
# please see http://www.gnu.org/licenses/gpl
#

#
# FUNCTIONS
#

# Exits the script when the Ctrl+C interrupt is called
exit_script()
{
   clear
   exit 1
}

#
# MAIN SCRIPT
#

# Start: Trap Ctrl+C and display the warning message
trap exit_script 2
dialog --title "NOTICE! PLEASE READ BEFORE CONTINUING" --backtitle "LanNET 'sudo' Policy" --msgbox "Modification of this server requires express permission from a LanNET administrator. FAILURE TO OBTAIN THIS PERMISSION BEFORE MAKING ANY CHANGES TO THIS MACHINE, OR MAKING ANY MALICIOUS CHANGES TO THIS MACHINE, WILL BE PUNISHABLE BY EXPULSION FROM THE EVENT WITHOUT REFUND. ALL LOGIN AND SUDO ATTEMPS TO THIS MACHINE ARE LOGGED. If you wish to continue, press \"OK\"." 13 50

# Clear the screen and ask for the username
clear
echo "Please enter your full name as shown on your ID:"

# Get the first input, which is the name of the person making the change
read AUTHUSER

# Clear the screen again and ask for the administrator
echo ""
echo "Please enter the name of the authorizing administrator:"

# Get the second input, which is the name of the authorizing administrator
read AUTHADMIN

# Temporarially get rid of the 'sudo' alias to this script so it won't call itself
unalias sudo

echo ""

# Ask for the sudo password and clear the screen
sudo -k
sudo false # This command does absolutely nothing except ask for the sudo password here, instead of later
clear

# Log the information to /var/lannet/sudoauth.log, root viewable only
echo '------------------------' | sudo tee -a /var/lannet/sudoauth.log
echo 'LOGGED ATTEMPT AT SUDO' | sudo tee -a /var/lannet/sudoauth.log
echo 'User: ' `whoami` | sudo tee -a /var/lannet/sudoauth.log
echo 'Participant: ' $AUTHUSER | sudo tee -a /var/lannet/sudoauth.log
echo 'Authorization: ' $AUTHADMIN | sudo tee -a /var/lannet/sudoauth.log
echo '"who" data: ' `who --ips` | sudo tee -a /var/lannet/sudoauth.log
echo "" | sudo tee -a /var/lannet/sudoauth.log

echo "Authorization successful. Command executing."
echo ""

# Double-check/reset permissions of that log file, so that only root can see it
sudo chown root:root /var/lannet/sudoauth.log
sudo chmod 700 /var/lannet/sudoauth.log

# Execute the command
sudo $@

# Reenable the 'sudo' alias and exit
alias sudo='/sbin/sudoauth.sh'
exit 0

```

---

### Post by djbon2112 on 2009-10-14
Also, something else I wanted to ask, also for the shell script.

The premise will be this will be run by a user SSH'd into the server, logged in as the "gameadmin" account (or something) and needing to "sudo" something to make his game server(s) work. BUT, I also need to be able to record the IP he's logged in from. Is there a command to print that?

---

### Post by scorp123 on 2009-10-14
> **djbon2112 said:**
> It's not to reinvent the wheel, it's basically so I can give my game server admins the password to an account with sudo priviledges, but at least have some way to track if they do things to the system at large.  OK, maybe I am not understanding this correctly. "sudo" does all that already. You can give someone a password to specific account, and thanks to "sudo" they can execute specific things that you define via "/etc/sudoers" ... So why the necessity for this script? You could write whatever commands needs to be executed straight into the script and then allow password-less execution of it via /etc/sudoers ... With this an admin wouldn't even need to know any password besides his own. And yet "sudo" would log each time it gets triggered by someone (you get an entry in the system log).

So .... what am I missing? Why the need to "replace" sudo? (Sorry but I am really slloooooow tonight ...)

> **djbon2112 said:**
>  It would "replace" sudo in the user's shell using an alias  Again ... why the need for this?

> **djbon2112 said:**
>  and the file they're writing to is owned by root and has 700 permissions.  Yes, and that would make it a candidate for handling via "sudo", wouldn't it?

> **djbon2112 said:**
>  EDIT: I also forgot to mention, that I don't want to just add the commands to sudoers because I need this to be very portable and deployable at a moment's notice with many different possible situations. Always adding the dozens of commands I may need will take forever.  Well, "sudo" certainly is "very portable and deployable" as it pretty much exists for every Linux, BSD and commercial Unix variant out there.

> **djbon2112 said:**
>  I have the file as /sbin/sudoauth.sh and the user in question has an alias for sudo='/sbin/sudoauth.sh'.  I think I should go to bed. I am really not getting this e.g. why you need to do that instead of using "sudo" directly? Never mind. I am too sloow tonight it seems. :)

---

### Post by amingv on 2009-10-14
Seeing the larger picture now, I must say I agree with scorp123.
Giving root access to someone you don't entirely trust is a bad idea, logging script or not.
Just give them access to the game server files: create a "gameadmin" group and give it permission to work with the game files only. Most other setups will compromise security.

Even if you used an alias, it's pretty easy to use the command underneath:

```
/usr/bin/sudo <potentially_dangerous_command>
```

---

### Post by scorp123 on 2009-10-15
> **amingv said:**
>  Giving root access to someone you don't entirely trust is a bad idea, logging script or not.
Just give them access to the game server files: create a "gameadmin" group and give it permission to work with the game files only. Most other setups will compromise security.

+1

My thoughts exactly.

---

### Post by djbon2112 on 2009-10-15
EDIT: Well, damn, being able to use /usr/bin/sudo directly kinda puts a damper on this. I did think of it before, which is why I wanted to use su, but that wasn't working. This is a pain in the ***...

> **amingv said:**
> Just give them access to the game server files: create a "gameadmin" group and give it permission to work with the game files only. Most other setups will compromise security.

Problem is, every game server is different, it uses different files in different places, some require root to start the service, etc., and I'm trying to do this precisely so I don't have to worry about setting this stuff up myself; I can just let another (somewhat-untrusted; I trust them with a log, but not without) user do it, and I can worry about more important stuff (like keeping my guests who DON'T want to play that game happy).

Basically all I need to do is log to a custom place the IP of the user, who they're logged in as, and who gave them the authorization, every time a user tries to do something sudo, as well as display a prompt with my warning (easy enough by itself). If there's an easier way to do that, besides this script, please let me know!

---

### Post by amingv on 2009-10-15
> **djbon2112 said:**
> Problem is, every game server is different, it uses different files in different places, some require root to start the service, etc., and I'm trying to do this precisely so I don't have to worry about setting this stuff up myself; I can just let another (somewhat-untrusted; I trust them with a log, but not without) user do it, and I can worry about more important stuff (like keeping my guests who DON'T want to play that game happy).

Basically all I need to do is log to a custom place the IP of the user, who they're logged in as, and who gave them the authorization, every time a user tries to do something sudo, as well as display a prompt with my warning (easy enough by itself). If there's an easier way to do that, besides this script, please let me know!

Even in this scenario, creating a group would work. All server files (regardless of where they are or what server they belng to) would be owned by root and the "gameadmin" group. I know setting this sounds tedious, but believe me when I tell you it takes less than five minutes with a small recursive command.
Every one of this files would have the read/write/execute bit enabled for their group members.

In case I'm misunderstanding you and you really can't do it that way, there is yet another option you have:
Create a program to control any possible routine your helpers would have to perform (python/perl/bash may be good languages for this), it doesn't have to be very complicated, in fact since it will be used through SSH it can be a very simple console program. Then give your helpers the ability tu run only THAT program with root capabilities by using visudo.

The downside, of course, is that you'd have to know at least some very basic programming (or know someone who does), but your helpers would be limited to the tasks the program offers, thus achieving a relatively decent setup security-wise...

If you give some examples of some of the things they would be doing on the server (edit config files, restart the connections, IP-banning players?), maybe we can come up with something more concrete.

---

### Post by djbon2112 on 2009-10-15
> **amingv said:**
> Even in this scenario, creating a group would work. All server files (regardless of where they are or what server they belng to) would be owned by root and the "gameadmin" group. I know setting this sounds tedious, but believe me when I tell you it takes less than five minutes with a small recursive command.
Every one of this files would have the read/write/execute bit enabled for their group members.

In case I'm misunderstanding you and you really can't do it that way, there is yet another option you have:
Create a program to control any possible routine your helpers would have to perform (python/perl/bash may be good languages for this), it doesn't have to be very complicated, in fact since it will be used through SSH it can be a very simple console program. Then give your helpers the ability tu run only THAT program with root capabilities by using visudo.

The downside, of course, is that you'd have to know at least some very basic programming (or know someone who does), but your helpers would be limited to the tasks the program offers, thus achieving a relatively decent setup security-wise...

If you give some examples of some of the things they would be doing on the server (edit config files, restart the connections, IP-banning players?), maybe we can come up with something more concrete.

The problem with the first idea is that I don't know which game servers we'll be running, and all of them tend to be different (have config files in different places, different binaries, need to access different things). I can't write a script to control an application and its files if I don't know what application it will be ;) And it comes back to me not wanting to do this myself AT the event, which is the time the games to play is usually proposed (as I said, we're kinda free-for-all). I hope that makes sense! I can do basic programming in a bunch of languages so that's not a problem for me.

What any given game server admin might need to do:

* Install the game server software
* Start/stop/restart the game server service(s)
* Modify config files for the game server
* Execute any binaries for the game server (this usually takes care of banning players, modifying maps, etc.)

Thanks for your help amingv, I do appreciate it!

EDIT: I also crossposted this on [H]ardforum (I frequent there too), so [here's]("http://www.hardforum.com/showthread.php?t=1460228") that thread. Having to rewrite it all in one post makes my reasons and such a bit clearer, I think ;)

---

### Post by amingv on 2009-10-15
> **djbon2112 said:**
> The problem with the first idea is that I don't know which game servers we'll be running, and all of them tend to be different (have config files in different places, different binaries, need to access different things). I can't write a script to control an application and its files if I don't know what application it will be ;) And it comes back to me not wanting to do this myself AT the event, which is the time the games to play is usually proposed (as I said, we're kinda free-for-all). I hope that makes sense! I can do basic programming in a bunch of languages so that's not a problem for me.

What any given game server admin might need to do:

* Install the game server software
* Start/stop/restart the game server service(s)
* Modify config files for the game server
* Execute any binaries for the game server (this usually takes care of banning players, modifying maps, etc.)

Thanks for your help amingv, I do appreciate it!

EDIT: I also crossposted this on [H]ardforum (I frequent there too), so [here's]("http://www.hardforum.com/showthread.php?t=1460228") that thread. Having to rewrite it all in one post makes my reasons and such a bit clearer, I think ;)

OK, now we're speaking plain english! :)
I though you were going to host a permanent game server (I once did this with eAthena, so my mind went right there when I read your problem.), that's why I though the other people using them would be your "helpers" or "subordinates"

Asuming the server machine has some decent memory, you could run several Virtual Machines, that way each can have their own IPs (no server stealing each other's ports), and if somebody screws up (unintentionally or otherwise) it will not affect the other VMs at all.

You could also run sandboxes, but the servers may not get all the resources they need.

You could also create a queue list, have them write the path to their server executable there, and have another routine (like cron) execute everything on the list every minute as root and flush it (can provide a hole to security, unless you filter malicious commands in the list) If they install the games in their home folders (which is doable) they will also be able to edit config files. It may be tricky to make it work well, though.

I know there must be smarter ways to do this, I'll see if I can offer you anything else tonight (after I come back from college).

---

### Post by djbon2112 on 2009-10-15
> **amingv said:**
> OK, now we're speaking plain english! :)
I though you were going to host a permanent game server (I once did this with eAthena, so my mind went right there when I read your problem.), that's why I though the other people using them would be your "helpers" or "subordinates"

Asuming the server machine has some decent memory, you could run several Virtual Machines, that way each can have their own IPs (no server stealing each other's ports), and if somebody screws up (unintentionally or otherwise) it will not affect the other VMs at all.

You could also run sandboxes, but the servers may not get all the resources they need.

You could also create a queue list, have them write the path to their server executable there, and have another routine (like cron) execute everything on the list every minute as root and flush it (can provide a hole to security, unless you filter malicious commands in the list) If they install the games in their home folders (which is doable) they will also be able to edit config files. It may be tricky to make it work well, though.

I know there must be smarter ways to do this, I'll see if I can offer you anything else tonight (after I come back from college).

I was originally thinking VMs too, but then I got this idea and figured "hey, that's easier!". Well, I guess not! :p I managed to solve the IP logging issue, but for what it's worth I think I may just abandon this and do the VMs thing. Should be easy enough to script their creation (so I only have to type in my password once, if at all), let the person doing it set their own root password, and go from there. It will be a pretty powerful server so that's not an issue!

Thanks again amingv, I'll leave this thread open if anyone else has suggestions/improvements. I did GPL the script and publish it ;)

---

### Post by scorp123 on 2009-10-15
> **djbon2112 said:**
>  I may just abandon this and do the VMs thing. Should be easy enough to script their creation  With VirtualBox, Xen, and I think KVM too you can certainly do that.

VirtualBox has the "VBoxManage" command. If you just type "VBoxManage" without giving any options it will spit out all the options it knows, and amongst these are things like "createvm", "modifyvm", "startvm", "controlvm" ... So given the right arguments and parameters you can easily script and automate all the VM creation steps.

---

### Post by djbon2112 on 2009-10-15
> **scorp123 said:**
> With VirtualBox, Xen, and I think KVM too you can certainly do that.

VirtualBox has the "VBoxManage" command. If you just type "VBoxManage" without giving any options it will spit out all the options it knows, and amongst these are things like "createvm", "modifyvm", "startvm", "controlvm" ... So given the right arguments and parameters you can easily script and automate all the VM creation steps.

I've yet to use VirtualBox for server virtualization (only desktop w/GUI): how well does it perform, assuming everything is Linux (host and VMs), versus Xen? I'd probably use one master virtual disk image and just copy it for each VM needed, then delete the modified copy when done. I know I can do this fine with both.

---

### Post by scorp123 on 2009-10-15
> **djbon2112 said:**
>  I've yet to use VirtualBox for server virtualization (only desktop w/GUI): how well does it perform, assuming everything is Linux (host and VMs), versus Xen?  Xen clearly has the speed advantage on its side. No argument. If you run Linux-on-Linux then Xen is the clear winner performance-wise. What VirtualBox has in its favour is the ease-of-use ... e.g. you could prepare a VM on your laptop, then just export it and import it again on your server. Done. It will work. And I don't know if Xen is able to take snapshots of VM's? VirtualBox certainly can. If anything goes wrong you go back to the last working snapshot. So if ever anyone hoses their setup ... you go back to the snapshot. Done. As I said: no idea if Xen has such mechanisms too?

---

### Post by amingv on 2009-10-15
> **djbon2112 said:**
> I was originally thinking VMs too, but then I got this idea and figured "hey, that's easier!". Well, I guess not! :p I managed to solve the IP logging issue, but for what it's worth I think I may just abandon this and do the VMs thing. Should be easy enough to script their creation (so I only have to type in my password once, if at all), let the person doing it set their own root password, and go from there. It will be a pretty powerful server so that's not an issue!

Thanks again amingv, I'll leave this thread open if anyone else has suggestions/improvements. I did GPL the script and publish it ;)

I'm glad you found a suitable solution to this dilemma :).
If you need any further help, please do not hesitate to ask ;), we'll all see what we can do.

P.D. Where did you publish the script, by the way? I'd like to have a look, if it's OK.

---

### Post by djbon2112 on 2009-10-16
On the first page, 3rd or 4th post I think. I updated it so it's in the "done" state right now.

---

