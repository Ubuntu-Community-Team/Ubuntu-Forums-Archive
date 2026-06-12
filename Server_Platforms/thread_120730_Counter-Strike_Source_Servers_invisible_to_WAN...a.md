---
title: "Counter-Strike Source Servers invisible to WAN...and then LAN..wait a minute here.."
date: 2006-01-23
forum: Server Platforms
---

### Post by Chris9450 on 2006-01-23
Alright, first off I'd like to say hello to everyone. I've lurked through this forum for about a week  now. After ~13 years of windoze I finally took the plunge and now have a dual boot of winxp/Ubuntu. I also have a second computer that is used only for LAN get togethers(webserver & various dedicated game servers), that I finally ditched the win platform on and decided to go with Ubuntu server install because at this point this is the version I am most comfortable with. I haven't set apache up yet so I dunno how that will pan out yet. Enter the wonderful Source Dedicated Server (Hereafter SRCDS). I've been doing various dedicated servers for about 2 years so I can navigate my way through them fairly well until now. I'll go through this with as much detail as I can possibly muster up, bear with me. I have searched and searched to no avail have I come up with a viable solution to my problem.

This is a DHCP server hooked to a cable line. All needed SRCDS ports are opened and forwarded correctly to the inside server ip. I can verify this by giving a windows box the ip and it will run a server fine(no, both boxes are not on at the same time).

The SRCDS server is fully updated as of about 15 minutes ago. I use a screen script to launch the various mods, I'll use the script to launch a counter-strike server as an example:

```

#!/bin/sh
echo "Starting CS:Source Server"
sleep 1
screen -A -m -d -S CS:S-Server ./srcds_run -console -game cstrike +map de_dust +maxplayers 16 -port 27015 -autoupdate -tickrate 100
```
 
With this script when the server launches, I can see the server in the server list on my main computer since I'm on the LAN, but no one from the outside can see the server(I used 2 friends to verify this). I also used a web based custom port probe to check the outside status of my ports and while the rest of the ports register as "Stealth", port 27015 registers as "Closed". I didn't understand that because the server is running on 27015 and since I can connect to it via my lan connection it's obviously not closed. Switching the router to DMZ and sticking in the server ip address does nothing. "Ok,something's wrong with the ip settings or port settings" I think, so I start tinkering with the setup. Nothing seemed to have an effect until I added a "+ip 192.168.0.150" to the string to make it bound to the static ip issued by the DHCP(I've set the DHCP with the server's MAC address, it gets the same ip everytime). After a quick restart, I can no longer see the dedicated server in my window, but my friends can happily play on it now, and the web based port scanner reads port 27015 as being "open" . Wait a minute...just not showing up in the server window..lets try "connect 192.168.0.150" ...times out. Ok..let's try the ssh..The SSH works, ping works. The fact that my friends can now get on my server from the outside means that atleast the router forwarding is doing what it's supposed to do, but I absolutely do not understand how binding the server to an ip that it had already obtained from the DHCP makes me unable to connect to it while making it wide open to the outside, and the opposite happens when I leave "+ip 192.168.0.150" out. I'm assuming this is not a firewall issue because it's this one command that seems to change everything. I'm sure this is a simple fix but I'm afraid my knowledge of Linux is mediocre at best and I have not the slightlest clue of how to fix or troubleshoot this. ANY help at all would be greatly appreciated. All other network-oriented services thus far work fine, it's this roadblock(and at this point, this is a biga** roadblock) that's really making me want to pull my hair out.

Mods feel free to move this to the appropriate section if needbe. I put it in the 'servers' section because that was what the majority of this post is pertaining to.

---

### Post by Glut on 2006-01-23
I suspect that this is neither firewall or linux related, but simply SRCDS is not binding to both ip addresses.  I have no idea about SRCDS, but can you add a second +ip1.2.3.4 argument?

---

### Post by haircut on 2006-01-24
As Glut has mentioned.

Add the +ip to the command line, don't use your LAN IP but use your WAN IP. The IP your ISP has given you.

I was just going through the same thing with a DoD:S Server last night. Adding this allowed me to see the server in the Steam Server list.

There might be a way of setting Ubuntu but at the moment when I start a SRCDS it binds to 127.0.0.1. Setting it to my WAN IP worked find.

I've tested SHH and FTP and apart from default config giving access to everything they work fine.

So much to learn ... but for now I think I need to get FTP secure :)

Have you installed iptables or firestarter?

I know my 1M ADSL line isn't suitable for a server like this but I'm just testing it out with respect to possible co-location of a server.


EDIT: I lie ... I put the LAN IP from the DCHP Server in and it was that that worked ... sorry for the confusion.

---

### Post by Chris9450 on 2006-01-24
[QUOTE=Glut]I suspect that this is neither firewall or linux related, but simply SRCDS is not binding to both ip addresses.  I have no idea about SRCDS, but can you add a second +ip1.2.3.4 argument?[/QUOTE]


I do not *think* you can bind it to two seperate ips. I know this is a little off base but I've posted on the steam forums also and no one has tried to help at all. I have tried the sv_lan 0/1 commands and those do nothing. trying +ip <wan ip> causes an error of "WARNING: NNET_OpenSocket: bind: Cannot assign requested address" . I'm not sure what that means. It's not really of that much importance to use this right now on the wan, as it's just for lans. My friends are all away at college so that's the only option we have to mess with it right now, and we wanted to see if there was a performance boost. 

As far as firestarter or any other linux firewall, if a software firewall installs with the "server" ubuntu install then I have one, and need to remove it for the time being, any suggestions on that would be nice, thanks for the help guys, it's more than I have received from others.

---

### Post by haircut on 2006-01-25
Steam forums rox .... as you know :rolleyes: 

Get yourself on the Valve mailing list, it's a lot better then their forums:  [http://list.valvesoftware.com/](http://list.valvesoftware.com/)

I didn't use "screen" when I tested mine, being new to all this I woudn't know what benifit it has when running game servers like this.

I didn't install the "server" version of Ubutu as I wanted the GUI to help me get things working, no firewall is installed as standard when you install this way.

I know this isn't helping much but if I can help I will try.

---

### Post by Chris9450 on 2006-01-25
[QUOTE=haircut]Steam forums rox .... as you know :rolleyes: 

Get yourself on the Valve mailing list, it's a lot better then their forums:  [http://list.valvesoftware.com/](http://list.valvesoftware.com/)

I didn't use "screen" when I tested mine, being new to all this I woudn't know what benifit it has when running game servers like this.

I didn't install the "server" version of Ubutu as I wanted the GUI to help me get things working, no firewall is installed as standard when you install this way.

I know this isn't helping much but if I can help I will try.[/QUOTE]


I just did that I'll search through there. I have a 64-bit 10/100/1000 Nic card..could that have anything to do with it? It gets the dhcp information fine so I'm guessing not. Anyhow, thinking maybe something was wrong with the ubuntu installed, I tried slackware 10.2 and got the same exact problem. I'm Not really sure what's causing it, but I can't see me as being the ONLY person to have a problem like this. I believe for whatever reason Linux is not opening the port, but unfortunately I do not have the knowledge needed(yet) to troubleshoot this whatsoever :-? . 

I also use screen because as I mentioned this is a headless server so I control it through ssh and without starting them in a screen when I end the ssh session my server dies. I've tried running it outside of the screen with no success. Is there a port config file hiding somewhere that I could edit to leave the needed ports open full time?

---

### Post by haircut on 2006-01-26
Strange you should mention ports.

I re-booted my PC last night and guess what ... it didn't work. I could see it on LAN no problem but the Steam Server list didn't show the server.

I did a quick port change (27015 to 27035) and it looked like it was fine, I could now see the server on the Steam Server list. I then changed it back again (27015) and it still didn't want to show on the Steam server list. Back to port 27035 and it showed up.

I need to do a bit more reading up on it but I believe iptables can do the port stuff. This would more then likely mean hiding any ports more then opening ports though. As far as my router is concerned I put this PC in a DMZ to test it, so I don&#8217;t see why changing the port effected it.

I think a bit more testing is required O:)

---

