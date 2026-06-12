---
title: "HOWTO: Run a particular program but prevent it from accessing the Internet"
date: 2009-06-15
forum: Tutorials
---

### Post by amac777 on 2009-06-15
**Rational:**

Some programs like to access the Internet on their own. For example, many Windows programs I run in wine "call home", and Rhythmbox accesses Amazon each time I play a new MP3 in order to try and download cover art. For privacy purposes, you may want to run a program but ensure it *cannot* access the Internet.

**Howto: (6 steps) - Tested and works with Ubuntu 9.04 to 10.04 (see below for 10.10 adjustments)**

[COLOR=DarkRed]Step 1[/COLOR]. Create a group called "no-internet" and add your user as a member of this new group. 
(System->Administration->Users and Groups)

[COLOR=DarkRed] Step 2[/COLOR]. Create a script (somewhere in your PATH) called "ni" (stands for No Internet) as follows:

```
sudo nano /usr/bin/ni
```with this contents:

```
#!/bin/bash 
sg no-internet "$1"
```And make it executable:

```
sudo chmod +x /usr/bin/ni
```

[COLOR=DarkRed]Step 3[/COLOR]. Create a script called iptables_no-internet_rule as follows:

```
sudo nano /etc/network/if-pre-up.d/iptables_no-internet_rule
```

with this contents:

```
#!/bin/bash
iptables -A OUTPUT -m owner --gid-owner no-internet -j DROP
```

And make it executable:

```
sudo chmod +x /etc/network/if-pre-up.d/iptables_no-internet_rule
```

[COLOR=DarkRed] Step 4[/COLOR]. Enable the new firewall settings you made above in step 3 by running the following command:

```
sudo /etc/network/if-pre-up.d/iptables_no-internet_rule
```

[COLOR=DarkRed]Step 5[/COLOR]. Logout and then log back in again to make the group permissions take effect.

[COLOR=DarkRed]Step 6[/COLOR]. Finished. You can now run any program without allowing that program to access the network by using this command:

```
ni "program_name"
```

**Examples:**

- Note: the quotes around the program name are only there to allow you to enter commands needing parameters.

```
ni "ping www.google.com"
ni "wine install.exe"
ni firefox
```

will all run but fail to access the Internet because ping, wine, and firefox are run using the ni script as the group no-internet, which has been barred from outputting anything to other networks. Note: if you are just running a single word command like firefox you don't need the quotes. Also note, for testing, make sure firefox isn't already running because then it will already have Internet access. Close it first and then run it preceeded by ni.

**Options:**

_Local network access_

The above will actually prevent _all_ outgoing network access by the programs run with ni; however, sometimes this may not be what you want. For example, certain local network access for games in wine might be acceptable. If you want to allow only local network access but still keep the Internet in general blocked, you can change the iptables config line in the file mentioned in Step 3 to the following:

```
iptables -A OUTPUT -m owner --gid-owner no-internet -d ! 192.168.0.0/24 -j DROP
```

change the 192.168.0.0 to match your local network as required.

_Preventing the need for the quotes_
_Ubuntu 10.10_
_Uncomplicated Firewall (UFW)_

In post #30 of this thread, user zzarko posted a technique that prevents the need for the quotes around the command run by ni, which may be useful when you want to have a script update the parameters of the command. He also described some adjustments for running this on Ubuntu 10.10, which user Jack Brown later confirmed also helps use the same idea with UFW (see post #40).

**Revert all changes:**

The above changes will persist even after system reboot so you can always run any program with the "ni" script to prevent it from getting out on the network. However, if you no longer want to have this feature enabled, you can uninstall the above by simply removing the two files created like this:

```
sudo rm /usr/bin/ni
sudo rm /etc/network/if-pre-up.d/iptables_no-internet_rule
```

and then remove the group "no-internet" from (System->Administration->Users and Groups).

I hope this helps others.

---

### Post by Nareto on 2009-06-20
beautiful, thank you very much

---

### Post by SeanHodges on 2009-06-24
Very useful, thanks for that.

---

### Post by XCan on 2009-09-19
Thanks amac777, especially liked the part describing how to unblock local access. Came in handy for my server. :)

---

### Post by Voorhees1979 on 2009-09-22
A very long winded way of doing it. Say I have doom 3 installed on linux and I want it to stop the constant key checks on line I open /etc/hosts as root and add this to the bottom of the file:

```
127.0.0.1 q4master.idsoftware.com idnet.ua-corp.com
```

Will block doom 3 checking anything online. Quick and easy

---

### Post by SeanHodges on 2009-09-22
> **Voorhees1979 said:**
> A very long winded way of doing it. Say I have doom 3 installed on linux and I want it to stop the constant key checks on line I open /etc/hosts as root and add this to the bottom of the file:

```
127.0.0.1 q4master.idsoftware.com idnet.ua-corp.com
```

Will block doom 3 checking anything online. Quick and easy

That's a good strategy, though quite limited in practice. It will only work if you know exactly which servers the program is intending to contact.

I wouldn't want to write the /etc/hosts entry for blocking Firefox from accessing HTTP servers on the Web, for example.

---

### Post by amac777 on 2009-09-22
> **Voorhees1979 said:**
> A very long winded way of doing it. 

I guess it depends on what you mean by "it", since what you described and what I described do different things. Different solutions for different problems. :P

---

### Post by johnbrod on 2009-11-28
Hi, I'm having no luck with this and can't figure out why. The ni script seems ok: ```
ni "id" 
``` reports the no-internet group ID correctly. I can also see the new OUTPUT rule from iptables -L. Any ideas anyone?

---

### Post by Cypher1101 on 2009-11-28
I can't get the script to block anything other than ping. I closed firefox then ran it with ni, and it went through to the internet just fine. I tried it with xchat - same results

---

### Post by amac777 on 2009-12-01
> **johnbrod said:**
> Hi, I'm having no luck with this and can't figure out why. The ni script seems ok: ```
ni "id" 
``` reports the no-internet group ID correctly. I can also see the new OUTPUT rule from iptables -L. Any ideas anyone?

Does "sudo iptables -L" look like this:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            owner GID match no-internet
```

> I can't get the script to block anything other than ping. I closed firefox then ran it with ni, and it went through to the internet just fine. I tried it with xchat - same results

I wrote these instructions using Jaunty and am still running that version of Ubuntu. Are you on a newer version? Maybe there is something different about the way iptables works on the new version?

---

### Post by quickzilver on 2009-12-02
Thanks a lot for this post. 
I hope this should work. 
Yet to try it out.

---

### Post by six-geek on 2009-12-02
> **amac777 said:**
> [...] Maybe there is something different about the way iptables works on the new version?

I guess that is the reason why i get the password question
> $ ni "ping www.google.com"
Password:
Invalid password.
Isn't it weird that I get asked to identify myself by password? Am I the only person with this issue? I am running kubuntu 9.10.

---

### Post by amac777 on 2009-12-02
> **six-geek said:**
> I guess that is the reason why i get the password question

Isn't it weird that I get asked to identify myself by password? Am I the only person with this issue? I am running kubuntu 9.10.

Getting asked for a password seems to indicate that your user is not a member of the "no-internet" group like it should be. See "Step 1" and make sure you add your user to the no-internet group. I normally use the SYSTEM-ADMINISTRATION-USERS AND GROUPS tool to do this, but if you prefer the command line, you can also use this command:

```
sudo usermod -a -G no-internet username
```

where username should be your username. Then you need to logout / log in again to make the new groups take effect. Once your user is a member of the group, you should not get that password prompt anymore.

---

### Post by six-geek on 2009-12-02
Cheers for this tip. But I am still in the group **no-internet**. This shows me the command
> $ id
uid=1000(six) gid=1000(six) groups= *[...]* 1002(no-internet)

Any further ideas?

---

### Post by johnbrod on 2009-12-02
> **amac777 said:**
> Does "sudo iptables -L" look like this:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            owner GID match no-internet
```

This is what I've got

```
Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  10.0.1.3             10.0.1.1            tcp dpt:domain 
ACCEPT     udp  --  10.0.1.3             10.0.1.1            udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 
DROP       all  --  anywhere             anywhere            owner GID match no-internet
```Is the ```
ACCEPT all -- anywhere anywhere
``` overriding everything else? How do I remove that?

>  I wrote these instructions using Jaunty and am still running that version of Ubuntu. Are you on a newer version? Maybe there is something different about the way iptables works on the new version?Hmmmm, I'm on 9.10 netbook remix. Thanks for the help.

---

### Post by Cypher1101 on 2009-12-16
> **amac777 said:**
> 
I wrote these instructions using Jaunty and am still running that version of Ubuntu. Are you on a newer version? Maybe there is something different about the way iptables works on the new version?

No, I'm still running jaunty because of my gfx card not playing nicely with karmic the last time i tried upgrading to it. Oddly enough I tried the script again today and it worked perfectly. I know I logged out and rebooted before trying it last time I posted, so I really don't know why it decided to start working.

It really is a nice script - thanks for posting it

---

### Post by amac777 on 2009-12-17
> **johnbrod said:**
> Is the ```
ACCEPT all -- anywhere anywhere
``` overriding everything else? How do I remove that?

To delete that rule, you can use:

```
sudo iptables -D OUTPUT 3
```

The 3 is because the rule you want to delete is the third one in the OUTPUT chain.

---

### Post by bj0 on 2009-12-20
This is pretty cool, but is there a way to make this sort of thing able to toggle?

Like if you are running a program and you want it to have network access for a certain event or time, then block (or vice versa).

---

### Post by amac777 on 2009-12-20
> **bj0 said:**
> This is pretty cool, but is there a way to make this sort of thing able to toggle?

Like if you are running a program and you want it to have network access for a certain event or time, then block (or vice versa).

Yes, you can. Basically, the iptables rule that blocks the internet can be deleted or added dynamically, as required. I'm not sure of the exact nature of what you need, but basically here's how you could give a "program" some limited internet time:

First, start the program using the ni script:

```
ni program &
```
That will start the program without internet access and the & allows you to keep typing more commands without waiting for the program to terminate first. 

When you are ready to give the program internet access, delete the iptables rule:

```
sudo iptables -D OUTPUT -m owner --gid-owner no-internet -j DROP
```

Now the program can access the internet. When you want to block it again, just re-include (ie, add) the iptables rule to cutoff the internet for that program again:

```
sudo iptables -A OUTPUT -m owner --gid-owner no-internet -j DROP
```

If you wanted the inverse (ie, only block a portion of time for the program but allow the rest), you could delete the rule before you run the program (but still use the ni script to run it) and then add the rule just for the time you want to block the program.

---

### Post by FrankyG on 2010-07-08
amac777, this HOWTO really rocks! excactly what I needed to prevent some win(e) programs from "calling home"... thanks a lot!
frank

---

### Post by fireandspike on 2010-10-25
I did the steps outlined but it does not work. Running with ni firefox still gives it net access.

here is my ip.tables output

> 
Chain OUTPUT (policy DROP)
target     prot opt source               destination         
blockcontrol_out  all  --  anywhere             anywhere            state NEW mark match !0x14 
ACCEPT     tcp  --  192.168.0.183        192.168.0.1         tcp dpt:domain 
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 
DROP       all  --  anywhere             anywhere            owner GID match no-internet 


EDIT:

Ok removing OUTBOUND   all  --  anywhere  anywhere   
gave me no net connection at all for anything

I reinserted it with command 
sudo iptables -A OUTPUT -p all  --goto  OUTBOUND

and for some now ni firefox works!  
Maybe it was the ordering of the rules.

---

### Post by amac777 on 2010-10-26
> **fireandspike said:**
> 
and for some now ni firefox works!  
Maybe it was the ordering of the rules.

It seems at least one poster before you had that OUTBOUND rule in there and it didn't work for him right away either. Then he rebooted and it worked. Maybe just a coincidence but I'm not sure.

Anyway, glad you got it working.

---

### Post by amac777 on 2010-11-05
[QUOTE=arapaho]Can you help me
following your how to
I created no-internet group with ID 1001. I added myself to that group.

#!/bin/bash
iptables -A OUTPUT -m owner --gid-owner no-internet -j DROP
Do I have to replace owner with arapaho and --gid-owner with --1001?
[/QUOTE]

No, you don't need to replace anything, just copy that text verbatim into the file.

[QUOTE=arapaho]Do I have to use terminal and ni program_name
every time I want to use the program or is it a permanent block?[/QUOTE]

You have to run the program using ni program_name every time. If you don't run it with the ni script, the program will be able to access the Internet.

Let me know if you have any more questions. You can post in this thread rather than PM in case other people later have the same questions.

---

### Post by markp1989 on 2010-11-05
thats a pretty cool idea, 

I would quite like the opposite, blocking Internet access for every  program except those ran using the script, that way only things i give permission get online.

---

### Post by amac777 on 2010-11-05
> **markp1989 said:**
> thats a pretty cool idea, 

I would quite like the opposite, blocking Internet access for every  program except those ran using the script, that way only things i give permission get online.

That should be possible too. Basically, you'd set the firewall to block all network access for programs run by your user's group, and then use a script to change the group ID to something else for the programs you want to have access. Might only need a small change to the firewall and a reboot but I'm at work now so will have to test it later.

---

### Post by arapaho on 2010-11-05
> **amac777 said:**
> You can post in this thread rather than PM in case other people later have the same questions.
Sorry about PM. I just needed a quick answer and I wasn't sure if you subscribe to this topic. Thank you.

---

### Post by amac777 on 2010-11-05
> **arapaho said:**
> Sorry about PM. I just needed a quick answer and I wasn't sure if you subscribe to this topic. Thank you.

No problem. Did you see my answer above and get it working?

---

### Post by zappal on 2010-12-20
It seems good, but it stops working when UFW is active. I would like to know how to add this rule with UFW

or what line to add in which file?

---

### Post by Grey Rider on 2011-02-03
Let me first beg your pardon, I'm a Debian user, not Ubuntu.  If I'm being inappropriate by posting here, I apologize.

An internet search lead me to this thread and I found it extremely helpful.  But my system is a little different because I am running a Firestarter firewall.  So I thought I'd update this HOWTO with a slight modification for Firestarter users.

Rather than putting the iptables script in /etc/network, if you are running Firestarter you want to put the line:

```
iptables --append OUTPUT --match owner --gid-owner no-internet -j DROP
```

into the file:
/etc/firestarter/user-pre

According to the /etc/firestarter/firewall script, the user-pre script is run before most of the chains are set in iptables.  By placing the new iptables rule in user-pre, you ensure its inclusion early in the chain list, thereby ensuring it will be applied when operating as the no-internet group.  There is no need to write the iptables_no-internet_rule script and put it in /etc/network if you run Firestarter, and doing so won't have any effect on the ability of no-internet to access the outside world.

---

### Post by zzarko on 2011-02-13
I made a few modifications to original poster's HOWTO, to make it work well in Ubuntu 10.10 (32-bit):

1. Since putting **iptables_no-internet_rule** script in **if-pre-up.d** didn't work for me (it wasn't executed after system restart, I had to manually start it every time I booted the machine), I put it in **if-up.d**.

2. Because rule for iptables was put at the end of OUTPUT rules, and because of rules that precedes it, it was never executed. To solve this, I changed the rule to ```
iptables -I OUTPUT 1 -m owner --gid-owner no-internet -j DROP
```so it would be placed at the top of OUTPUT rules (and applied first).

3. Original **ni** script required quotes around command if there were any arguments, ie: ```
ni "command arg1 arg2 arg3"
```This was very troublesome if you wanted to alter parameters from the script (especially if they contain spaces). I changed the **ni** script to ommit necessary quotes around such commands:```
#!/bin/bash
COMMAND="$1"
shift
for arg; do
COMMAND="$COMMAND \"$arg\""
done
sg no-internet "$COMMAND"
```Now it can be invoked with:
```
ni command arg1 arg2 arg3
```which is much better for scripts.

---

### Post by user_21 on 2011-03-20
> **Grey Rider said:**
> 
Rather than putting the iptables script in /etc/network, if you are running Firestarter you want to put the line:

```
iptables --append OUTPUT --match owner --gid-owner no-internet -j DROP
```into the file:
/etc/firestarter/user-pre

According to the /etc/firestarter/firewall script, the user-pre script is run before most of the chains are set in iptables. By placing the new iptables rule in user-pre, you ensure its inclusion early in the chain list, thereby ensuring it will be applied when operating as the no-internet group. There is no need to write the iptables_no-internet_rule script and put it in /etc/network if you run Firestarter, and doing so won't have any effect on the ability of no-internet to access the outside world.


Greetings,

your modification, Grey Rider worked for me like a charm. I use Firestarter, and after adding the rule to "user-pre" file and restarting the firewall "ni" does indeed work as expected. At last.

And thanks, zzarko for your suggestion on modifying "ni" script itself.
Can I suggest a shorter alternative to your version:
```

#!/bin/bash
sg no-internet $@

```or is it somehow different in execution?

Ok, but now I've got another question.

How to modify the iptables rule so that the Firestarter could report the existence of an outgoing packet?

I'm quite a noob at handling iptables, so please, help me with this one.

I just want to have some realtime visual feedback (while using Firestarter) in case the blocked application actually will try to make a connection.

If I use 2 rules like so:
```

iptables --append OUTPUT --match owner --gid-owner no-internet -j LOG
iptables --append OUTPUT --match owner --gid-owner no-internet -d 192.168.0.0/24 -j DROP

```then the Firestarter will indeed log the outgoing packet in the "events" tab, but what happens to that packet afterwards? Is it dropped after it's been logged or does fall through to the 2nd rule?

Btw. In the "events" tab, there is no indication what process sent the blocked packet. I know that, but I would like to deal with that later. 

Now, I only want to have the same packet logged and then droped silently by the fw.
Is this the way I should accomplish that?
Maybe there is a way to tweak Firestarter so that it could indicate dropped packet as an event as well.

Regards,

---

### Post by atanu1 on 2011-04-01
[FONT=Arial Black]Thank you [/FONT]amac777 and others (from other fora and websites) for your ideas.

A quick script:
I am currently using it as a backend for Nautilus Actions to select a prog. from context menu and fire it without any Internet access.

All changes and generalizations welcomed.


[FONT=Courier New]#!/bin/bash
# block internet access for any prog during execution
##(cl) Atanu-AT-mandals-DOT-net, 1/Apr/2011
##Based on: amac777 ([http://ubuntuforums.org/showthread.php?t=1188099](http://ubuntuforums.org/showthread.php?t=1188099)) and others' ideas. 
##CHANGES: 
##WARNING: This Script has been casually tested on Ubuntu 10.xx
##REQUIRE: invoking user needs sudo rights to root

#command required on command line, else fart out
if [ ! $1 ]; then echo "Command/program to run required"; exit 1; fi

GRP=no-internet ## change to your taste

##comment/uncomment as per your requirements
#disable ALL net access
    IPT="iptables -A OUTPUT -m owner --gid-owner $GRP -j DROP" 
#disable Only Internet and allow local LAN
#IMPORTANT: adjust local LAN as per your needs
    #IPT="iptables -A OUTPUT -m owner --gid-owner $GRP -d ! 192.168.1.0/24 -j DROP"

##create group
grep -q "^$GRP:" /etc/group > /dev/null || sudo groupadd $GRP

##add invoking user to the group GRP
#sudo iptables -L -n | grep "owner GID match $GRP"
usr=$(whoami)
id $usr | grep -q "$GRP" || sudo usermod -aG $GRP $usr

## set iptable rule
#l8r: chk for a common method
#l8r: chk how to avoid multiple rule additions

##For firestarter folks
# add your chosen $IPT to /etc/firestarter/user-pre
#chk if rule already added
if ! sudo grep -q "$IPT" /etc/firestarter/user-pre; then
    sudo echo $IPT >> /etc/firestarter/user-pre
    sudo service firestarter restart
fi

#For direct firewalls - follow amac777's example (on ubuntu)
#sudo $IPT

##run the no-internet access command
sg no-internet "$1"[/FONT]

---

### Post by zzarko on 2011-04-02
> **user_21 said:**
> Can I suggest a shorter alternative to your version:
```

#!/bin/bash
sg no-internet $@

```or is it somehow different in execution?

Yes, it is different in how it handles names with spaces (which are very common if you try to run something with wine, for example). The script above will treat each part of the name with spaces (for example ni command "path with spaces") as separate arguments ("ni" "command" "path" "with" "spaces"), while mine will treat it as the whole name (I guess, the problem is sg and how it interprets parameters after the command).

---

### Post by Jack Brown on 2011-06-29
what great work guys.
this is repository material. (add a GUI and even new users would start downloading it)
or atanu's idea of putting it in nautilus right click menu.

zzarko post, item 2 works with UFW (zappal's question):
> 2. Because rule for iptables was put at the end of OUTPUT rules, and  because of rules that precedes it, it was never executed. To solve this,  I changed the rule to   	Code:
 	iptables -I OUTPUT 1 -m owner --gid-owner no-internet -j DROP 
 so it would be placed at the top of OUTPUT rules (and applied first).


so create 'ni' script in /usr/bin as per OP
create iptables script in /etc/network/if-pre-up.d as per OP but using zzarko's entry
chmod + x the iptables script
execute the iptables script
check if your entry is in "sudo iptables -L"
reboot (might not be necessary)
and you're good to go. 

thanks amac and zzarko!

---

### Post by d3v1150m471c on 2011-06-29
you are a genius. love the tutorial

---

### Post by z@ch on 2011-09-25
Hi Everyone

I'm running Ubuntu 10.04 and did exactly as you wrote (copy&paste the commands to make sure there were no mistakes) but right after Step 4 "sudo /etc/network/if-pre-up.d/iptables_no-internet_rule" 

I get the following error:

iptables v1.4.4: owner: Bad value for "--gid-owner" option: "no-internet"
Try `iptables -h' or 'iptables --help' for more information.

Am I missing something or doesn't this work in Ubuntu 10.04?

Thank you in advance!
Dominic

---

### Post by amac777 on 2011-09-25
Hi Dominic,

I am still running 10.04 so I know it works on that version. From your error message it looks like you don't have the "no-internet" group. Did you do "step 1"?

Edit: and don't forget to logout/login after you do step 1 to make sure the group changes take effect.

---

### Post by pkg9991 on 2011-09-25
nice tutorial.. thank u

---

### Post by z@ch on 2011-09-25
Oops!
Oh my, I started with step 2...
I was obviously too focused on the quoted commands.

Next time I know that it's always good to start with step 1 ;-)

thanks for your help,
now it works.

---

### Post by z@ch on 2011-10-23
For those of you who want to open a filetype in a WINE Program,
running in no-internet mode, try this:

go to ~/.local/share/applications/

there you will find files called smth. like "wine-extension-doc.desktop"

Search for the filetype you want to start in no-internet mode, right click on it and go to "properties". 
(I choose .DOC, so I click on "wine-extension-doc.desktop")

Now add 'ni' and the ""-signs to the command:

BEFORE: wine start /ProgIDOpen Word.Document.8 %f

AFTER: ni "wine start /ProgIDOpen Word.Document.8 %f"

and the filetype will be opened without internet-connection :D.

greetings
Dominic

---

### Post by crossedout on 2011-10-26
Thanks to everyone, it really is important to deny access sometimes.

---

### Post by rockorequin on 2011-10-30
Great tutorial, thanks, a small improvement I have to suggest is to make the /usr/bin/ni script like so:

```
#!/bin/bash
CMD=$@
sg no-internet "$CMD"

```

and then you don't need to add the quotes around your command when you use it, eg you can just do:

```
ni ping google.com
```

instead of

```
ni "ping google.com"
```

---

### Post by zzarko on 2011-10-31
> **rockorequin said:**
> Great tutorial, thanks, a small improvement I have to suggest is to make the /usr/bin/ni script like so:

```
#!/bin/bash
CMD=$@
sg no-internet "$CMD"

```Someone already suggested something like this, but the problem with this solution is that it doesn't handle arguments with spaces as one argument. For example, if you try this script with:```
ni program_name arg\ with\ spaces
```program_name will get three arguments instead of one ("arg", "with" and "spaces"). The more complex solution that handles situations like this can be found in post #30.

---

### Post by gunwald on 2011-12-02
Greetings to all of you!

I am using this tutorial since a while to block wine applications internet access but I have one big problem:
This method does not work with SSH and X-forwarding. Some times I am using this to bring a big wine application from my desktop pc to my small Netbook.
This works well with:
   ```
ssh -CX user@server wine /path/to_application

```But obviously it does not using the »ni« script
   ```
ssh -CX user@server ni "wine /path/to_application"
```Seems that the IP-table blocks the programs access to the forwarded X. I don't know much about TCP/IP, so anybody has an idea how to get that working.

---

### Post by matt_symes on 2011-12-03
Hi

@gunwald.

I suspect you will need to adjust the rules to allow ssh on port 22. That's what i would try first.

> **gunwald said:**
> Greetings to all of you!

I am using this tutorial since a while to block wine applications internet access but I have one big problem:
This method does not work with SSH and X-forwarding. Some times I am using this to bring a big wine application from my desktop pc to my small Netbook.
This works well with:
   ```
ssh -CX user@server wine /path/to_application

```But obviously it does not using the »ni« script
   ```
ssh -CX user@server ni "wine /path/to_application"
```Seems that the IP-table blocks the programs access to the forwarded X. I don't know much about TCP/IP, so anybody has an idea how to get that working.

Kind regards

---

### Post by gunwald on 2011-12-05
Ok, thank you, but does anybody know how? I tried this, but did not work either:

```
iptables -A OUTPUT -m owner --gid-owner no-internet -d ! 192.168.1.0/24 -j DROP
iptables -A OUTPUT -m owner --gid-owner no-internet -p tcp --dport 22 --sport 22 -j ACCEPT
```

---

### Post by zzarko on 2011-12-05
I'm not quite sure, but I think that the order of rules is important, and that first one to match will be executed. So, I guess you'll just need to reverse the order:```
iptables -A OUTPUT -m owner --gid-owner no-internet -p tcp --dport 22 --sport 22 -j ACCEPT
iptables -A OUTPUT -m owner --gid-owner no-internet -d ! 192.168.1.0/24 -j DROP
```Again, I'm not an iptables expert, but you could try...

---

### Post by matt_symes on 2011-12-06
Hi

 > I think that the order of rules is important, 

You are correct. The order of the rules is very important.

Kind regards

---

### Post by gunwald on 2011-12-06
Thank you, zzarko and matt_symes,

with your help I got it working:

```
#!/bin/bash
iptables -A OUTPUT -m owner --gid-owner no-internet -p tcp --dport 22 --sport 22 -j ACCEPT
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A OUTPUT -m owner --gid-owner no-internet ! -d 192.168.1.0/24 -j DROP
```

It actually makes sense, that ACCEPT hat to be before DROP. How to accept a package, that is already dropped?

Tanks again,
Gunwald

---

### Post by ochampao on 2012-01-31
Hello, great post and very nicely explained.

I ve tried your method and works however for not all of my programs. e.g. ni "firefox" works. But for another program I am trying it seems that it doesn't like the fact that I am running it using the no-internet group i.e. I get the same problem when I try ni "myProgram" and sg no-internet "myProgram". The program starts loading and then it freezes. If I run the same program using sg myGroup "myProgram" it works. The permissions of myProgram are set like this: <lrwxrwxrwx 1 root root myProgram>. Unfortunately, I don't get any useful error messages to quote here. Do you have any idea what might be causing this behaviour? Thanks a lot for your help.

---

### Post by amac777 on 2012-02-01
> **ochampao said:**
> I get the same problem when I try ni "myProgram" and sg no-internet "myProgram". The program starts loading and then it freezes. If I run the same program using sg myGroup "myProgram" it works. The permissions of myProgram are set like this: <lrwxrwxrwx 1 root root myProgram>.

It's hard to tell from your description what you have done and what is happening. One thing that leaps out to me is that it appears myProgram is owned by root but you don't mention using sudo. Are you running these tests as root? If yes, did you run all the steps of the HOWTO as root too? If no, what is myGroup in your example? If myProgram does require sudo to run then that could be why things aren't working. There's probably a solution though so let me know if sudo involved.

Another possibility is that everything is working fine and your myProgram just freezes when it does not have access to the Internet. From your description it appears it only freezes when you run it without Internet. Are you sure it's not frozen due to having no Internet? :p

If you can provide more details of what you are trying to run I might be able to help more.

---

### Post by amac777 on 2012-02-01
Thanks **zzarko**, I just updated the HOWTO to mention your post #30 in the options section. (I had meant to do this before but then forgot)

Also thanks **Jack Brown** for you post 40 about UFW, I mentioned this too since some people use that.

**All** - Let me know if there is anything else I've missed in the comments that I should add to the options section.

---

### Post by ochampao on 2012-02-02
Hello and thanks a lot for the quick response.

I have followed the HOWTO and used sudo wherever you specified using it. The program I am trying to run works without any problem if I just disable the internet connection. myGroup is the group in which my default user account belongs to, so yes it can use sudo. If I understand correctly from <lrwxrwxrwx 1 root root myProgram> "others" are allowed to read/write/execute myProgram so this shouldn't be a problem right? I have tried <sudo ni myProgram> but still no luck. Also <sg no-internet myProgram> does not work but <sg myUsername myPrgram> works. Do you think changing all the files of myProgram to myUsername:myGroup instead of root:root may help?

Thanks again for your help :)

_Update_: I have changed the file permissions for all the program's executables using:

```
sudo chmod -R a+rwx myProgram/
```

and now the script works fine. Initially the executables had the permissions:

```
drwxr-xr-x 7 root root [...] myProgram
```

It seems the fact that "others" had only execute privileges did not allow the 'ni' script to work properly.

To verify which applications access the internet I have used:

```
lsof -i -n -P
```

---

