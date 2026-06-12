---
title: "HOWTO: PPTP Client in an easy way"
date: 2010-03-31
forum: Tutorials
---

### Post by CyberAngel on 2010-03-31
Hello,

It has been many times that I searched for a command line pptp client howto (as sometimes the GUI apps doesn`t work very well) to send to some "new to ubuntu" friends  but always found some sites explaining the whole procedure making it more complicated with the extra scripts need to be created for routing the correct ip addresses through the tunnels.
That`s why today I took the decision to write a simple bash script to make it as easy as possible to create your tunnel using only one command and then run it using pon and poff.
I`m pasting my job here hoping to be helpful for others too.

Of course I`m taking no responsibility if this script blows up your computer or anything similar :P
I don`t think that it will do though as I have tested it on my PC and some more friends without problems.


Let`s begin....

Run the following to install pptp and pptpsetup:
```
sudo apt-get install pptp-linux
sudo sed -i 's/= "\$DOMAIN\\\\"/\= "$DOMAIN\\\\\\\\"/g' /usr/sbin/pptpsetup
```

The sed command replaces a buggy string in the pptpsetup with the correct one.

Then download the attached script (cyberpptp.sh) and put it under your /bin/ directory. After that, make it executable using:
```
chmod +x /bin/cyberpptp.sh
```

Then run the script as follows for each of your tunnel:
```
sudo cyberpptp --add <TUNNEL> <SERVER> <USERNAME> <PASSWORD> <IPs_TO_ROUTE_THROUGH_THE_TUNNEL>
```
<TUNNEL> is just and identification name of your tunnel.
<SERVER> is the host name or IP address of the pptp server.
<DOMAIN> is the domain name of the company you are connected. (This is optional but you are strongly encouraged to use it, as if you do have similar usernames in different domains, you will not be able to connect to them without this option being set for each of them.)
<USERNAME> the username of the pptp user to connect (put it in quotes)
<PASSWORD> the password of the pptp user (put it in quotes again)
<IPs_TO_ROUTE_THROUGH_THE_TUNNEL> the iprange of the remote network that it will be routed through the tunnel

An example of the above command follows:
```
sudo cyberpptp.sh --add testtunnel 86.12.34.123 'myuser' 'myP@ssw0rd' 192.168.0.0/24
```
Run the tunnel using 
```
sudo pon <TUNNEL>
```
And disconnect the tunnel using
```
sudo poff <TUNNEL>
```

You can use
```
plog
```
to check the status of the connection after running the pon command.

Use the cyberpptp.sh script with --delete option, if you want to totally delete the tunnel.
```
cyberpptp.sh --delete <TUNNEL>
```

---

### Post by rkillcrazy on 2011-08-15
Couple questions:
[LIST]
[*]Does your script work with 11.04?
[*]Do we still need to use the sed command to fix the bug or was that bug addressed after you wrote the script?
[*]Say someone wanted to route several IP ranges like: 10.224.208.0/24, 10.224.209.0/24, 10.224.214.0/24... How does one handle that?
[INDENT]* Could we just add * to route all traffic?[/INDENT]
[INDENT]* Could we just add 10.0.0.0/16 (or whatever the slash-notation is for the whole range)?[/INDENT]
[/LIST]

---

### Post by CyberAngel on 2011-08-16
> **rkillcrazy said:**
> Couple questions:
[LIST]
[*]Does your script work with 11.04?
[*]Do we still need to use the sed command to fix the bug or was that bug addressed after you wrote the script?
[*]Say someone wanted to route several IP ranges like: 10.224.208.0/24, 10.224.209.0/24, 10.224.214.0/24... How does one handle that?
[INDENT]* Could we just add * to route all traffic?[/INDENT]
[INDENT]* Could we just add 10.0.0.0/16 (or whatever the slash-notation is for the whole range)?[/INDENT]
[/LIST]

Haven't tried the script recently but it should work!
As I just see the pptpsetup script, you still need to run the sed command. I have never addressed the problem...

---

### Post by CyberAngel on 2011-08-16
As for the multiple routes, everytime you create a new tunnel, the script will create a file in **/etc/ppp/ip-up.d/<name_of_tunnel>** and put the route commands in there.
This file should have a line similar to this one:

```
/sbin/route add -net <network range> dev $PPP_IFACE
```

Copy this line and paste it exactly below as many times as the routes you want to add.
Then change the <network range> to your static routes.
If you want to pass all the traffic from the pptp tunnel, just use 0.0.0.0/0 instead of the * you mentioned.

---

### Post by rkillcrazy on 2011-08-16
> **CyberAngel said:**
> As for the multiple routes, everytime you create a new tunnel, the script will create a file in **/etc/ppp/ip-up.d/<name_of_tunnel>** and put the route commands in there.
This file should have a line similar to this one:

```
/sbin/route add -net <network range> dev $PPP_IFACE
```

Copy this line and paste it exactly below as many times as the routes you want to add.
Then change the <network range> to your static routes.
If you want to pass all the traffic from the pptp tunnel, just use 0.0.0.0/0 instead of the * you mentioned.

Understood.  I'll give all that a try.

---

### Post by Asitaka on 2012-10-01
This is a really old thread and I just hope someone checks it.

I'm trying to set up a pptp client on my 12.04 server and I can't for the life of me get it to work so I thought I'd try your script but I'm getting this:

/bin/bash: set -x: No such file or directory

could you please help? Cheers

---

