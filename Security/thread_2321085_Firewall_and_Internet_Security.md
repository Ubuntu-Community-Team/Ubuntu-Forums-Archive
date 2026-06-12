---
title: "Firewall and Internet Security"
date: 2016-04-20
forum: Security
---

### Post by jantaro2 on 2016-04-20
I managed to compile bitcoin-qt by myself, because I was told that it was safer than running a lightweight wallet, and, by the way, it works fine. I mean, I´m using my computer for dealing with money. I use as well my browser to connect to my local bank account. So I m little concerned about what kind of safety measures should I run to stay as safe as possible when connected to the internet.

I m connected to the internet using a Router VG 8050 Comtrend that was provided by my phone company. ( Optical Fiber ).The connection was like automatic, nothing was configured neither on the modem or computer, the technician just came to my house and... "plug and play".

Gathering some information I learned about a firewall called UFW, that would block incoming connections, so I suppose I should run it on to stay safer.

Little do I know about internet configuration and security but these are the ports I need to keep opened.

Default Bitcoin network protocol listen port is 18333 (testnet) and 8333 (standard bitcoin network ).

Default RPC connection port 18332 (testnet) and 8332 ( standard bitcoin network ).

I need as well the torrent client Transmission and Thunderbird working fine. I don´t know if I should keep any other ports opened apart from the ports above. Of course I need Firefox  working fine and loading all kind of websites.

Should I block all the incoming connections running

sudo ufw enable?. And then, unblock the desired ports with?

sudo ufw allow 18333

sudo ufw allow 8333 etc...

Is there any ports I have to keep opened for Transmission and Thunderbird?.

Browsers will keep on loading pages after doing this?.

Do you recommend UFW or is there any other firewall I should know about?.

Should I configure something else on my router or O.S to stay as safe as possible when connecting my computer to the 

internet for moneytransfer?.

What kind of things should I check from my internet connection and how?.

Thanks in advance to those who could say something back. Kind Regards!.

---

### Post by ajgreeny on 2016-04-20
Please use the default font for posts, not the difficult to read grey colour that you chose.

---

### Post by danbosse1 on 2016-07-03
This is my method: Allow only    

```
sudo ufw default deny incoming  
sudo ufw default deny outgoing 
``` 

internet  
```
sudo ufw allow out 53  
sudo ufw allow out http  
sudo ufw allow out https  
sudo ufw allow out 8080
```  
 

gmail  
```
sudo ufw allow proto tcp from 173.194.0.0/16 
sudo ufw allow out to 173.194.0.0/16 port 993  
sudo ufw allow out to 74.125.0.0/16 port 465 proto tcp 
``` 

hotmail  
```
sudo ufw allow proto tcp from 207.46.0.0/16 
sudo ufw allow out to 207.46.0.0/16 
sudo ufw allow out to 65.52.0.0/14 port 587 proto tcp  

```
qbittorrent (I can't get transmission to work) (use peerguradian as well)
```
sudo ufw allow in 6969  
sudo ufw allow out 6969  
```
I delete this rule when not in use. Peerguardian will show a barrage of attacks. I reject the port to stop it!
```
sudo ufw reject 6969
```

You need to apply this to your needs.  

To find the subnet you have to ping (ctrl c to stop ping) the address (?bitcoin.com) then whois  the IP from your terminal and retrieve the CIDR (subnet)  

Hope this helps!

---

### Post by DuckHook on 2016-07-04
Please refrain from using formatting for posts.

Also, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Lastly, please note that OP started this thread months ago and is unlikely to still be monitoring for a response. Though not quite a necropost, it is advisable to address help towards more current posts. ;)

---

