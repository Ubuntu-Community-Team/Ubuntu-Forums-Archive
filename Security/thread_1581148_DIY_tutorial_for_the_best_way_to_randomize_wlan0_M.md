---
title: "DIY tutorial for the best way to randomize wlan0 MAC &amp; hostname on every bootup?"
date: 2010-09-24
forum: Security
---

### Post by rocksockdoc on 2010-09-24
New to Linux, on Windows I ran easily found freeware to pseudo-randomize the wireless MAC address and hostname on every bootup (the hostname uses a lookup table).

[COLOR=DarkRed]**What are the corresponding ways in Ubuntu 10.04 to randomize the wlan0 MAC and laptop Hostname?**[/COLOR]

**Q: Why would anyone want to randomize the hostname & wlan0 MAC address?**
*A: Simple privacy. Access points, e.g., at hotspots, log those two items. Why not change them since they serve no useful purpose to the user otherwise.*

**Q: Why not randomize the wlan0 MAC & hostname manually?**
*A: I can. But it would be so much nicer to find a program that does this on every boot.*

**Here's what I do manually to randomize the hostname:**
```

sudo vi /etc/hosts

Change the contents of /etc/hosts from:
127.0.1.1      ubuntu      ubuntu

Change the contents of /etc/hosts to:
# 127.0.1.1 ubuntu ubuntu
127.0.0.1 foo foo 
    
sudo echo foo > /etc/hostname
sudo reboot

```**Here's what I do manually to randomize the MAC:**
```

Right click on the "wireless networking" to uncheck "Enable Networking"
Open a terminal window.
ifconfig -a | grep HWaddr
sudo ifconfig wlan0 down hw ether DE:AD:BE:EF:CA:FE
sudo ifconfig wlan0 up
!ifconfig
Right click on the "wireless networking" to check "Enable Networking"

```I searched and found macchanger on Ubuntu, but it only simplifies slightly the task of changing the MAC address and does not randomize the MAC automatically upon every reboot:
```

sudo apt-get install macchanger
macchanger -s wlan0
sudo /etc/init.d/networking stop
macchanger --another wlan0
sudo /etc/init.d/networking start

```Since anyone who cares about privacy at hotspots would care about randomizing the data stored at the hotspot (i.e., the hostname and the MAC address), there must already be a better solution out there than what I've found so far.

[COLOR=DarkRed]**[SIZE=3]What's the best way to randomize the MAC and hostname upon reboot?[/SIZE]**[/COLOR][SIZE=1]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182582&stc=1&d=1296683540[/IMG]
[/SIZE]

---

### Post by cariboo on 2010-09-24
If you use the same Access points frequently you've got a lot more to worry about than your host name or MAC address. Unless you are using ssh tunneling, you're open to man-in-the-middles attacks, it's pretty trivial to find your spoofed mac address and host name.

If you've got more than one system with a wireless device and a wireless router, you can use one of the systems running Backtrack to find what your spoofed MAC address and host name. Do try this at home, and not anywhere else

---

### Post by rocksockdoc on 2010-09-24
> **cariboo907 said:**
> it's pretty trivial to find your spoofed mac address and host name.

I don't fully understand your point but I appreciate your advice.

I definitely understand the need for VPN-style encryption (but that's a whole 'nuther topic altogether - which I'll tackle at a later point). And, I certainly realize the wlan0 MAC address and laptop hostname are "out there" in the packets (open to man-in-the-middle-attacks); and, more importantly, they're definitely LOGGED by the access point router ... So that's why it's a "good thing" to change the MAC & hostname randomly upon every reboot (pseudo randomly is OK for my purposes).

> Backtrack to find what your spoofed MAC address and host name.

I'll look up this "Backtrack", but, I already know that the MAC address and hostname can be found (it's logged in the access-point router and it's in every packet I think). So, I'm not sure what Backtrack will tell me that I don't already know (but I'll look it up to see if it has a MAGICAL way, perchance, of finding the original hostname and/or wlan0 MAC address even when changed daily). 

Assuming Backtrack doesn't magically find your entire history of old MAC addresses and old hostnames, it's still a "good thing" to randomly (a large lookup table is fine) assign a new MAC to the wlan0 and a new hostname to the laptop upon all reboots.

[COLOR=DarkRed]**I'm sure someone has scripted a hostname change and MAC address change upon boot; so I'd like to stand on the shoulders of giants & find that before I resort to writing my own (and publishing the results back here for others to benefit).**[/COLOR]

---

### Post by n~kf)}BW% on 2010-09-24
Here is an alternative way to generate a random mac address without macchanger.


```
echo $RANDOM$RANDOM | md5sum | sed -r 's/(..)/\1:/g; s/^(.{17}).*$/\1/;'
```Enter it in your bash terminal and see for yourself :popcorn:

We still have to integrate it in a startup script! I don't have a solution, but perhaps this could help.

```
oldmac=`ifconfig -a | grep HWaddr | grep wlan0 | awk '{print $NF}'`
echo "Old mac adress: $oldmac"
newmac=`echo $RANDOM$RANDOM | md5sum | sed -r 's/(..)/\1:/g; s/^(.{17}).*$/\1/;'`
sudo ifconfig wlan0 down hw ether $newmac
sudo ifconfig wlan0 up
echo "New mac adress: $newmac" 
```

---

### Post by rocksockdoc on 2010-09-24
> **slovenia said:**
> alternative way to generate a random mac address

```
echo $RANDOM$RANDOM | md5sum | sed -r 's/(..)/\1:/g; s/^(.{17}).*$/\1/;'
```

ooooh. Nice!

Let's take this apart ... (looking up the bits I don't understand) ... 

- echo $RANDOM -> outputs a random integer in some shells such as bash, ksch, sh, etc.
- echo $RANDOM$RANDOM -> outputs a bigger random integer ?
- | md5sum -> this is a nice way, I think, to force an always-32-bit long result
- | sed -r -> use extended regular expressions
- 's/ -> search for
- (..) -> any two characters
- /\1: -> replace it with what you found first in the parenthesis and then add a colon
- /g -> then do that again globally for each set of two characters
- ; -> begin a new command
- s/^ -> search for the beginning of the line
- (.{17}) -> **[COLOR=DarkRed]the magic here is a mystery to me[/COLOR]** ?
- .*$ -> then search for any character, any number of them, until the end of the line
- /\1/; -> and replace it with what you found first in the parenthesis

I'm confused about how the "(.{17})" does its magic. Looking up curly braces in sed, which I've never used before, I see they "group commands", but I don't understand the command "17" at all. 

**[COLOR=DarkRed]This clearly works ... but can you explain the magic to me of "(.{17})" in sed?[/COLOR]**

---

### Post by n~kf)}BW% on 2010-09-24
> - echo $RANDOM -> outputs a random integer in some shells such as bash, ksch, sh, etc.
- echo $RANDOM$RANDOM -> outputs a bigger random integer ?
- | md5sum -> this is a nice way, I think, to force an always-32-bit long result
- | sed -r -> use extended regular expressions
- 's/ -> search for
- (..) -> any two characters
- /\1: -> replace it with what you found first in the parenthesis and then add a colon
- /g -> then do that again globally for each set of two characters
- ; -> begin a new command
- s/^ -> search for the beginning of the line
- (.{17}) -> **[COLOR=DarkRed]the magic here is a mystery to me[/COLOR]** ?
- .*$ -> then search for any character, any number of them, until the end of the line
- /\1/; -> and replace it with what you found first in the parenthesisHere is my explanation: :P

- echo $RANDOM -> outputs a random integer such as 1233
- echo $RANDOM$RANDOM -> outputs two random integers joined such as 12335577
- | md5sum -> fixed 128bit length and force HEX numbers (from 0 to f) for MAC
- | sed -r -> use extended regular expressions
- 's/ -> s stands for substitute
- (..) -> any two characters
- /\1: -> replace it with what you found first in the parenthesis and then add a colon
- /g -> then do that again globally for each set of two characters
- ; -> begin a new command
- s/^ -> search for the beginning of the line
- (.{17}) -> . is any character, {17} repeats 17 times. so it's 17 of any characters
- .*$ -> all what is left (from 17th character to the end)
- /\1/; -> and replace what is left with \1

I hope that explains it to you :)

---

### Post by rocksockdoc on 2010-09-24
> **slovenia said:**
> 
We still have to integrate it in a startup script! 


I tried and failed but will keep at it until I can figure it out.

BTW, I found what seems to be a good random hostname upon reboot script here:
[http://cryptoanarchy.org/wiki/Random_hostname_on_boot](http://cryptoanarchy.org/wiki/Random_hostname_on_boot)

It picks the random hostnames out of /usr/share/dict/words

I wonder if we can modify it to also change the wlan0 MAC address?

That web page has only been accessed 400 times since it was written (according to the web counter at the bottom of the page), so, just in case it goes away, I'll reproduce it here.

Two files are needed:
/etc/init.d/hostname.sh runs before the filesystem has mounted
/etc/init.d/hostname-rewrite-files runs just after the filesystem has mounted

```

#!/bin/sh ### BEGIN INIT INFO # Provides:          hostname # Required-Start: # Required-Stop: # Should-Start:      glibc # Default-Start:     S # Default-Stop: # Short-Description: Sets a random hostname # Description:       Read /usr/share/dict/words, pick a random word #                    and update the kernel value with this value. #                    If /etc/hostname is empty, it is created. #                    The old hostname in /etc/hosts is also replaced #                    If everything fails, the value 'localhost' is used. ### END INIT INFO # INSTALLING: # sudo cp hostname.sh /etc/init.d/hostname.sh # sudo chmod u+x /etc/init.d/hostname.sh # sudo update-rc.d hostname.sh start 02 S . # reboot & pray # WRITTEN BY Pragmatk, May 2010   PATH=/sbin:/bin  . /lib/init/vars.sh . /lib/lsb/init-functions  do_start () { 	# either current name or /etc/hostname (/etc/hostname shouldn't be missing) 	[ -f /etc/hostname ] && OLD_HOSTNAME="$(cat /etc/hostname)"  	# Keep current name if /etc/hostname is missing. 	[ -z "$OLD_HOSTNAME" ] && OLD_HOSTNAME="$(hostname)"  	# below we pick a random word and filter it for special chars (and make sure we still have string) 	# could be approached cleaner (ie rejecting a word with special chars instead of filtering, 	# but that'd give us fewer pretty names to pick from!) 	HOSTNAME=`cat /usr/share/dict/words |/usr/bin/perl -e '@w=<>;$g="";while($_!~/\A[a-z]+\Z/i){@good=$w[int rand $#w]=~/([a-z]+)/ig;$_=join("",@good);}print'`  	#default to localhost (we do not want to use a previously stored value) 	[ -z "$HOSTNAME" ] && HOSTNAME=localhost  	log_action_begin_msg	"$HOSTNAME is now the new hostname :-)" 	[ "$VERBOSE" != no ] && log_action_begin_msg "Setting hostname to '$HOSTNAME'" 	hostname "$HOSTNAME" 	ES=$? 	[ "$VERBOSE" != no ] && log_action_end_msg $ES 	exit $ES }  case "$1" in   start|"") 	do_start 	;;   restart|reload|force-reload) 	echo "Error: argument '$1' not supported" >&2 	exit 3 	;;   stop) 	# No-op 	;;   *) 	echo "Usage: hostname.sh [start|stop]" >&2 	exit 3 	;; esac 
```

```

#!/bin/sh ### BEGIN INIT INFO # Provides:          hostname-rewrite-files # Required-Start:    mountall # Required-Stop: # Should-Start:      glibc # Default-Start:     S # Default-Stop: # Short-Description: Writes the current hostname to disk # Description:       Writes the current hostname to disk when the #                    filesystem has been remounted (to enable permanent #                    name change). ### END INIT INFO # Written by Pragmatk, May 2010 ## INSTALLING: # sudo cp hostname-rewrite-files /etc/init.d/hostname-rewrite-files # sudo chmod u+x /etc/init.d/hostname-rewrite-files # sudo update-rc.d hostname-rewrite-files start 36 S . # hope it works # ??? # PROFIT!   PATH=/sbin:/bin  . /lib/init/vars.sh . /lib/lsb/init-functions  do_start () { 	HOSTNAME=$(hostname) 	OLD_HOSTNAME=`cat /etc/hostname` 	if [ ! -z "$OLD_HOSTNAME" ] && [ ! -z "$HOSTNAME" ] && [ "$OLD_HOSTNAME" != "$HOSTNAME" ]; then 	for file in /etc/hostname /etc/hosts; do 		log_action_begin_msg "replacing ${OLD_HOSTNAME} with $HOSTNAME in file $file" 		sed s:${OLD_HOSTNAME}:${HOSTNAME}:g $file > ${file}.new && mv ${file}.new $file && log_action_begin_msg "done: replacing ${OLD_HOSTNAME} with ${HOSTNAME}" || log_action_warning_msg "failed when replacing ${OLD_HOSTNAME} with ${HOSTNAME} in $file" 	done 	fi 	exit 0 }  case "$1" in   start|"") 	do_start 	;;   restart|reload|force-reload) 	echo "Error: argument '$1' not supported" >&2 	exit 3 	;;   stop) 	# No-op 	;;   *) 	echo "Usage: hostname.sh [start|stop]" >&2 	exit 3 	;; esac 
```

---

### Post by n~kf)}BW% on 2010-09-24
Yes, we could easily integrate a wlan0 mac change script into this one but I think this startup script is way too big. It should be small, fast and easy to understand.

But anyway, if you want to integrate our script put it in the second file where do_start() function is:

```

do_start () {
        HOSTNAME=$(hostname)
        OLD_HOSTNAME=`cat /etc/hostname`
        if [ ! -z "$OLD_HOSTNAME" ] && [ ! -z "$HOSTNAME" ] && [ "$OLD_HOSTNAME" != "$HOSTNAME" ]; then
        for file in /etc/hostname /etc/hosts; do
                log_action_begin_msg "replacing ${OLD_HOSTNAME} with $HOSTNAME in file $file"
                sed s:${OLD_HOSTNAME}:${HOSTNAME}:g $file > ${file}.new && mv ${file}.new $file && log_action_begin_msg "done: replacing ${OLD_HOSTNAME} with ${HOSTNAME}" || log_action_warning_msg "failed when replacing ${OLD_HOSTNAME} with ${HOSTNAME} in $file"
        done
        fi
#start of mac changing script
        oldmac=`ifconfig -a | grep HWaddr | grep wlan0 | awk '{print $NF}'`
       log_action_begin_msg "Old mac adress: $oldmac"
        newmac=`echo $RANDOM$RANDOM | md5sum | sed -r 's/(..)/\1:/g; s/^(.{17}).*$/\1/;'`
        sudo ifconfig wlan0 down hw ether $newmac
        sudo ifconfig wlan0 up
        log_action_begin_msg "New mac adress: $newmac"
#end of mac changing script
        exit 0
}

```

---

### Post by rocksockdoc on 2010-09-24
> **slovenia said:**
> 
- (.{17}) -> . is any character, {17} repeats 17 times. so it's 17 of any characters


Oh, duh! < slaps head >. It's my fault. I should have realized "17" was not a "command" per se, but, the number of characters. Sorry about that. It's so clear now. 

Now the trick will be to insert this wonderful random wlan0 MAC address changer into some startup script.

I did try the two hostname changer scripts, but, they didn't change the hostname. I need to figure out what makes a script execute in /etc/init.d first, I guess. 

Thanks ... I'll keep digging until we have at least one way of having a new MAC and new hostname on every reboot.

---

### Post by n~kf)}BW% on 2010-09-24
[http://cryptoanarchy.org/wiki/Random_hostname_on_boot](http://cryptoanarchy.org/wiki/Random_hostname_on_boot):
>  I've had to modify one script (/etc/init.d/hostname.sh) and write my own (/etc/init.d/hostname-rewrite-files). These are experimental scripts - do not use them if you do not understand them and feel confident they won't screw stuff up :-) Did you also modify the original /etc/init.d/hostname.sh and put hostname-rewrite-files in /etc/init.d/? Try to check your boot log messages to check if there were errors or if it didn't run at all.

---

### Post by rocksockdoc on 2010-09-24
> **slovenia said:**
> Did you also modify the original /etc/init.d/hostname.sh and put hostname-rewrite-files in /etc/init.d/?

No and yes.

I'm sure I did something wrong so here's a log of what I did.

First, I looked to see what was already there:
```

ls /etc/init.d/host*
Reported initially only:
lrwxrwxrwx 1 root root   21 2010-09-10 02:12 hostname -> /lib/init/upstart-job

```

Notice there was no 'hostname.sh" ... there was just "hostname".

I copied the files from 
[http://cryptoanarchy.org/wiki/Random_hostname_on_boot](http://cryptoanarchy.org/wiki/Random_hostname_on_boot)
to /tmp so that I could add the mac-changing code.

I then copied the /tmp hostname.sh & hostname-rewrite-files (with the additional MAC-changing code) to the /etc/init.d directory.
```

sudo cp /tmp/hostname.sh /etc/init.d/.
sudo cp /tmp/hostname-rewrite-files /etc/init.d/.
sudo chmod u+x /etc/init.d/hostname-rewrite-files

```Then I ran the suggested update command suggested at 
[http://cryptoanarchy.org/wiki/Random_hostname_on_boot](http://cryptoanarchy.org/wiki/Random_hostname_on_boot)

```

# sudo update-rc.d hostname-rewrite-files start 36 S .

```Which reported the following two lines:
--> Adding system startup for /etc/init.d/hostname-rewrite-files ...
--> /etc/rcS.d/S36hostname-rewrite-files -> ../init.d/hostname-rewrite-files

And then I rebooted.

Unfortunately, you're right in that I don't understand this complex script. (looking in the logs now).

My main question (I'm digging now) is whether I should have DELETED the original /etc/init.d/hostname (which was a symbolic link to /lib/init/upstart-job) or if I should have overwritten the /etc/init.d/hostname with the new /etc/init.d/hostname.sh ???

---

### Post by n~kf)}BW% on 2010-09-24
Firstly delete hostname.sh from /etc/init.d/.

I think you should modify **(overwrite) the upstart-job** script like you would modify hostname.sh.

So, rename your hostname.sh to upstart-job and then replace original upstart-job. **But c**[B]heck if ubuntu 10.04 has same upstart-job script as 9.04 first because i think we have to modify our new script a bit! I'll check it tomorrow!
[/B]

---

### Post by BkkBonanza on 2010-09-25
On recent Ubuntus upstart uses the **/etc/init/network-interface.conf** file to "up" the network interfaces. You can add a step there that calls your scripts in the "pre-start script" section. Your script would add a hwether value to the interface config so that when it starts up it already has the new mac.

You'll see there this is where **if-up** is run. You want to add your mac-mod script call before that line.

It may be slightly different for you if you use network-manager as that program will handle the normal if-up process, but same idea. You want to set the mac value before network manager brings up the interface. I don't use network manager so I can't have a look on my system which file it uses to config the interface, but it's the one you want to add the "hwether de:ad:be:ef:ca:fe" value to.

You can also add your script as a new upstart job and then mod /etc/init/network-interface.conf to depend on it so yours runs first. Instead of the line,

start on net-device-added

you would want,

start on net-device-added and started my-job-name

This makes sure the interfaces aren't raised until after your mod job has been done. More info [here]("http://upstart.ubuntu.com/getting-started.html") (not installing, but writing jobs section; admittedly pretty **** poor docs for such an important topic).

Regarding being hacked at cafes and threats there - much more interesting than being "logged" I'd say, read up on **arp spoofing**. That will show you how other wifi users can MITM your traffic and start viewing it very easily. I would configure a ssh tunnel or vpn long before I'd worry about some cafe having your mac on file.

---

### Post by el_heffe on 2010-09-25
> **rocksockdoc said:**
> I don't fully understand your point but I appreciate your advice.

I definitely understand the need for VPN-style encryption (but that's a whole 'nuther topic altogether - which I'll tackle at a later point). And, I certainly realize the wlan0 MAC address and laptop hostname are "out there" in the packets (open to man-in-the-middle-attacks); and, more importantly, they're definitely LOGGED by the access point router ... So that's why it's a "good thing" to change the MAC & hostname randomly upon every reboot (pseudo randomly is OK for my purposes).

I'll look up this "Backtrack", but, I already know that the MAC address and hostname can be found (it's logged in the access-point router and it's in every packet I think). So, I'm not sure what Backtrack will tell me that I don't already know (but I'll look it up to see if it has a MAGICAL way, perchance, of finding the original hostname and/or wlan0 MAC address even when changed daily). 

Think of Backtrack as a security auditing tool.  With it you can pen test just about any "secure" network, in the right hands of course.  That having been said, changing your MAC will indeed do very little in the way of adding security, but if it makes you feel better or more secure, by all means, have at it.  If nothing else, the discussion can be applied the other way around- this seems to be a pen testers dream.  If you have a router at home running DD-WRT you can create a SOCKS proxy via SSH and then you will be 100% more secure than just by changing your MAC.

Have a good one, and thanks for all the thread! :D

---

### Post by rocksockdoc on 2010-09-25
> **slovenia said:**
> delete hostname.sh from /etc/init.d/. ... rename your hostname.sh to upstart-job and then replace original upstart-job.

It still did not change the hostname nor MAC address, but, it didn't hose the system either! :)

Here's what I have so far:
a) I moved /etc/init.d/hostname.sh to /lib/init/upstart-job
b) I left the MAC-modified /etc/init.d/hostname-rewrite-files
c) I left the "sudo update-rc.d hostname-rewrite-files start 36 S ." settings (as I don't know how to undo that anyway)

But when I rebooted, I still had the old DE:AD:BE:EF:CA:FE wlan0 MAC address and the old "foo" hostname. :(

Here is the content of the original Ubuntu 10.94 /lib/init/upstart-job:
[ATTACH]170528[/ATTACH]
Here is the content of the new /lib/init/upstart-job:
[ATTACH]170527[/ATTACH]
Here is the content of the MAC-updated /etc/init.d/hostname-rewrite-files:
[ATTACH]170529[/ATTACH]

Note: The "txt" extension was only added to facilitate the upload here (not in my file system).

---

### Post by rocksockdoc on 2010-09-25
> **el_heffe said:**
> changing your MAC will indeed do very little in the way of adding security

I don't fully disagree as I did say in the beginning changing the wlan0 MAC and PC hostname are only the first (baby) steps to increased anonymity at public wireless hotspots. 

Changing the wlan0 MAC merely makes it harder for the wireless hotspot to identify you uniquely on your second day at the same hotspot; or for two wireless hotspots to identiy you as the same person (since the wlan0 MAC address is stored in the router logs).

I guess it also hinders a persistent observer from realizing you're the same machine.

Likewise with the hostname of the machine, which is also logged by the router. In addition, the hostname change has general use even at home because web sites can also log your hostname along with your username.

> **el_heffe said:**
> If you have a router at home running DD-WRT you can create a SOCKS proxy via SSH and then you will be 100% more secure than just by changing your MAC

I'm not sure I understand; but that's probably a more advanced topic for another day anyway. BTW, I have a Linksys WRT-54G at home but this thread isn't for home anonymity - it's specifically for better anonymity at wireless hotspots (NOT at home). :)

> **BkkBonanza said:**
> add a hwether value to the interface config
Unfortunately, since I'm brand new to Ubuntu 10.04, this may be more difficult than what I can achieve at the first pass. I am reading up on this but I was hoping I wasn't the first person to want a random'ish MAC and hostname upon every reboot.

In a non-corporate network, I can't imagine why the MAC & hostname would matter all that much anyway ... so since they're definitely unique to your machine (initially anyway) and logged, we may as well change them up.

What's surprising to me is that there isn't a working Ubuntu 10.04 tutorial out there existent. So, I guess I'll write it once/if I get it working. As I said, the fact I can do it manually with ease means there MUST be a way to do it with scripts. :(

> **BkkBonanza said:**
> I would configure a ssh tunnel or vpn long before I'd worry about some cafe having your mac on file.

You're the second person to state that. You know more than I, but, seems to me it makes no sense to come in day after day with the same MAC & hostname if you don't have to. 

For example, let's say I wanted to send a whistle-blower email to the FBI about the mafia activities my employer is engaged in. I would NOT wish my MAC address and hostname logged and associated with that email. Right?

From the "real" MAC address, the mafia, for example, can identify the exact PC serial number associated with that wlan0 card, and from that, they can identify you directly. All from your "real" wlan0 MAC address. Now, I'm not saying I'm THAT worried; but the point is why broadcast and log exactly who you are every single time you visit a hotspot. 

Makes no sense from a privacy standpoint. You may as well put your full name and address on your mailbox, on your car, on your shirt, and on the bottom of your shoe soles. :)

---

### Post by BkkBonanza on 2010-09-26
I don't think there's any reason not to do what you want. It sounds like a good idea if you want to protect your identity at cafes.

You should revert things back to normal before proceeding because IMO you have changed incorrect files. If you were on an older system not using upstart then an init.d script may have been suitable.

First, to undo the init scripts,

sudo update-rc.d hostname-rewrite-files remove 

And change /lib/init/upstart-job back to original state and remove any links you made to it. Altering that file is not the way to go. First, it's a system lib location and should not be customized, and second it is part of the scripting to convert the old init.d style method to the new upstart method.

What you want to do is either add a new job that will run before networking and make networking wait for it to finish, OR just add a line to call your script in the current networking init. Either way sounds fine to me. How would I do it?

Like this,

Create one script file named **/usr/local/bin/random-host-mac** and edit it do to have the needed random hostname and mac code. Then make sure it is executable,

**sudo chmod +x /usr/local/bin/random-host-mac**

Then add one line to call it from **/etc/init/network-interface.conf**. This upstart job is in charge of getting the interfaces up and you want to do your step just before the interfaces are raised, so it's a good spot that won't mess up other system files and is a single line edit to enable/disable.

On my system in that file there is a line that says "mkdir -p /var/run/network". You want to add a line just before that that reads,

**/usr/local/bin/random-host-mac**

This will call your script just before the interfaces are raised.

Now in your script file you want code that creates a new hostname and calls the hostname command. Looking at the example file you linked shows it's designed for an init.d style system, and you really only need a small part of it in your script,

```
HOSTNAME=`cat /usr/share/dict/words |/usr/bin/perl -e '@w=<>;$g="";while($_!~/\A[a-z]+\Z/i){@good=$w[int rand $#w]=~/([a-z]+)/ig;$_=join("",@good);}print'`
```

I find that a bit over done and needing an external word list. I would use this as my random-host-mac script,

```

#!/bin/bash
RNDHOST=`cat /dev/urandom |tr -dc A-Za-z | head -c 8`
hostname $RNDHOST

RNDMAC='de:ad'
for n in {1..4}; do
  RNDMAC+=":"`cat /dev/urandom |tr -dc a-f0-9 | head -c 2`
done
ifconfig wlan0 hw ether $RNDMAC
```
That gives you a truly random 8 char hostname and mostly random MAC.
Note I use prefix de:ad because some values are not accepted as valid by ifconfig. This way seems to work but I didn't research in more depth which MAC values work/don't work (some fully random ones don't). This has to be done when the interface isn't brought up yet. Replace wlan0 with your correct interface if need be.

So, in summary, one line in the init job calls the script to set things up before the interface is raised by if-up.

If you find that cafe's won't accept "de:ad" prefixed MACs (apparently some don't), then change that to an Intel prefix like "00:13:e8" (or whatever) and set the count to 3 to give an acceptable random id.

---

### Post by rocksockdoc on 2010-09-26
> **BkkBonanza said:**
> I don't think there's any reason not to do what you want. It sounds like a good idea if you want to protect your identity at cafes.

So far, nothing has worked. So, for now at least, I'm giving up.

But, I am surprised there isn't any Ubuntu 10.04 tutorial for changing the hostname and mac address upon reboot. 

In theory (which is all we have that works), the randomized hostname can come from a file of names and the randomized MAC address either from the algorithm provided above for generating a random MAC or from a file list of legitimate MAC addresses).

It's too bad this random hostname/MAC DIY does not exist as it would enhance coffee-shop anonymity.

:(

I'm resigned to changing the hostname and MAC address manually whenever I go to a coffee shop.

I still don't have all the steps in a single script. 

Manually I must uncheck the "Enable Networking" and then after changing the MAC address, I must recheck "Enable Networking".

```

1. Right click on the "wireless networking" to uncheck "Enable Networking"
2. Open a terminal window.
3. ifconfig -a | grep HWaddr
4. sudo ifconfig wlan0 down hw ether DE:AD:BE:EF:CA:FE
5. sudo ifconfig wlan0 up
6. !ifconfig
7. Right click on the "wireless networking" to check "Enable Networking"

```To eliminate mouse actions, is there at least a way to disable & enable networking via a terminal command?

---

### Post by HermanAB on 2011-01-27
Howdy,

My tuppence worth:
If I go to Starbucks for my daily caffeine and slashdot, then the last thing I would worry about is my MAC and hostname.  It is more important to shield everything I do, than to shield who I am and leave everything I do open.  Therefore I always use a SSH socks proxy running on one of my servers and tunnel to that.

---

### Post by bodhi.zazen on 2011-01-27
> **hermanab said:**
> howdy,

my tuppence worth:
If i go to starbucks for my daily caffeine and slashdot, then the last thing i would worry about is my mac and hostname.  It is more important to shield everything i do, than to shield who i am and leave everything i do open.  Therefore i always use a ssh socks proxy running on one of my servers and tunnel to that.

+1

---

### Post by BkkBonanza on 2011-01-27
> **rocksockdoc said:**
> To eliminate mouse actions, is there at least a way to disable & enable networking via a terminal command?

You might try,

/etc/init.d/networking stop

... other cmds

/etc/init.d/networking start

I'm not sure (and didn't test) but it may achieve the same as the gui method.

---

### Post by CharlesA on 2011-01-27
> **BkkBonanza said:**
> You might try,

/etc/init.d/networking stop

... other cmds

/etc/init.d/networking start

I'm not sure (and didn't test) but it may achieve the same as the gui method.
That might work, but it's better to tunnel yer traffic if you are using public wifi as opposed to trying to use security thru obscurity.

---

### Post by BkkBonanza on 2011-01-28
I've always been a proponent for using an ssh tunnel. I even posted about it above and have many times. 

But it is polite to answer the question asked rather than just ignore what someone wants to know... and it's not an either/or situation. You can use a tunnel and a random mac address if you like.

---

### Post by CharlesA on 2011-01-28
That's true. :)

MAC addresses can be spoofed, so you won't get all that much added 
"security" by doing so.

---

### Post by Jive Turkey on 2011-01-30
For the theoretical use case presented by the OP, (i.e. anonymous wistleblowing) using a tunnel would not save you unless there was an anonymous tunnel.  Evildoers might correlate the exit point of a non-anonymous tunnel to the wistleblower.  Along the same vein, attempts to increase your privacy with randomized hostname and MAC is thwarted if you tunnel to the same IP every day from the same coffee shop.

Its an interesting excersise though.  I think it would be preferable to call the script from /etc/network/interfaces (instead of boot time and disable network manager) something like this:
```

auto wlan0
iface wlan0 inet dhcp
pre-up randomize-scan-and-prompt-for-essid.sh
post-down offer-to-rm-the-evidence.sh

```

---

### Post by rocksockdoc on 2011-02-02
> **Jive Turkey said:**
> using a tunnel would not save you unless there was an anonymous tunnel

Thanks for explaining that. This thread isn't about SSH tunneling (never was) so I'm not sure why anyone would repeatedly try to make this simple (yet apparently unique) remaining stumbling block of how to turn off "enable networking" in a script into (yet another) SSH tunneling discussion.

> **Jive Turkey said:**
> it would be preferable to call the script from /etc/network/interfaces

I had tried (and previously given up on) setting the MAC address from the /etc/network/interfaces script upon reboot ... but it never seems to take! :(

Obviously I'm doing something wrong ... but I don't know anyone else (so far) that has shown how THEY can set the MAC address upon reboot by the /etc/network/interfaces script.

Actually, I just realized, when I went to post my /etc/network/interfaces, that I've messed with it so much that I forgot what the original looks like. But, I tried and tried and tried to get the MAC address to be set upon boot from /etc/network/interfaces, and failed every time.

Certainly just putting a MAC address in the script (as shown below) will not set the MAC address (ask me how I know).

Here's my current /etc/network/interfaces file:

```

#/etc/network/interfaces loopback network interface
auto lo
iface lo inet loopback
iface eth0 inet dhcp
# These will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0
# hwaddress ether 00:01:02:03:04:05
# hwaddress ether AA:BB:CC:DD:EE:FF
# hwaddress ether 00:00:00:00:00:01
hwaddress ether DE:AD:BE:EF:CA:FE
auto eth0 

```I'm beginning to think ALL these methods fail to set the MAC upon reboot simply because of the toggle that is needed to unset and then set "Enable Networking".

**Can anyone unset & reset their Ubuntu 10.04 "Enable Networking" from a script?**

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182582&stc=1&d=1296683540[/IMG]

---

### Post by BkkBonanza on 2011-02-02
Actually I do set my MAC address at boot in the interfaces file. Not for anonymity but because the apartment building I live in uses the MAC address to prevent unauthorized access (silly!). And I changed my LAN card so needed to force the old MAC so it would work without having to go update the details. Mine isn't random but it does set the fake MAC upon boot without any problem.

Here is my interfaces file, for reference,

```

# The loopback network interface
auto lo
iface lo inet loopback

# The WAN network interface
auto eth0
iface eth0 inet dhcp
    hwaddress ether 00:1D:7E:40:12:8F
    address 192.168.1.250
    gateway 192.168.1.241
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255

```

If you're using "Network Manager" you may want to remove it with Synaptics and install **Wicd** instead. I had terrible problems using it while also wanting manual control over some aspects. With Wicd it doesn't mess with the interfaces file like Network Manager. You are most likely getting interference from that program as it likes to re-write the file to it's own liking. I use Wicd because it doesn't interfere and has better support for some things (or it did, I don't know if they have added new things to NM now).

I can run the **/etc/init.d/networking restart** command to re-init the network and set a new MAC address.

---

