---
title: "Possible Cyber Attackon my netbook?"
date: 2011-06-08
forum: Security
---

### Post by tuebinger on 2011-06-08
This afternoon I came home from work and found my computer was awake.  Also, the following programs were running:

-Cheese
-Screensaver Changer (and my screensaver was changed)
-Firefox

And two empty folders were created on my desktop.

All my files seem to be present, and there doesn't seem to be anything malicious that was done.

My question is: Was this a cyberattack?  And if so, how was it accomplished?  I have WPA-TSK (TKIP) security enabled on my router and a very long alphanumberic password.  I also have the usual password required to make any changes to the system and to wake up the computer from sleeping.

I'm perplexed.  I know these programs couldn't have opened themselves randomly, right?  If it was a cyberattack, how do I prevent it from happening again?   Should I change all my passwords?  Is there a way to find out how they got past my security?

I would appreciate anyone who knows about security and hacking giving me their thoughts on this.

Thanks!

---

### Post by Thewhistlingwind on 2011-06-08
Check your log files, especially the networking stuff.

Do you use firewall?

No, that's not normal, at least, to my knowledge it isn't.

EDIT: Cheese? Oh yeah, now I have no doubt that was a break-in. Do you know what services your running? Did you leave VNC on?
EDIT2: If theres any other explanations, please post for the OP's sake!

---

### Post by collisionystm on 2011-06-08
> **tuebinger said:**
> This afternoon I came home from work and found my computer was awake.  Also, the following programs were running:

-Cheese
-Screensaver Changer (and my screensaver was changed)
-Firefox

And two empty folders were created on my desktop.

All my files seem to be present, and there doesn't seem to be anything malicious that was done.

My question is: Was this a cyberattack?  And if so, how was it accomplished?  I have WPA-TSK (TKIP) security enabled on my router and a very long alphanumberic password.  I also have the usual password required to make any changes to the system and to wake up the computer from sleeping.

I'm perplexed.  I know these programs couldn't have opened themselves randomly, right?  If it was a cyberattack, how do I prevent it from happening again?   Should I change all my passwords?  Is there a way to find out how they got past my security?

I would appreciate anyone who knows about security and hacking giving me their thoughts on this.

Thanks!


Installed any third party software? Added any apt sources lately? Any kind of malicious script could have loaded a key logger of some sort. 

Prbly had cheese loaded so they could look at your house through the web cam

---

### Post by collisionystm on 2011-06-08
Install gufw firewall. Take your computer off the internet. Change your password's. Set the firewall to block all outbound traffic and look at the logs.

---

### Post by tuebinger on 2011-06-08
I do have Ubuntu One running in the background. Could that be the cause of any of this?  I haven't downloaded any third party software, but I did download some files from a sharing site about a week ago.  Could that also be a cause?  Thanks for you suggestions.  I will install the firewall and change my password.  I appreciate your help.

---

### Post by hackertarget on 2011-06-09
Sometimes the most obvious can be missed.  

Do you have a flatmate?  :D

---

### Post by doas777 on 2011-06-09
> **hackertarget said:**
> Sometimes the most obvious can be missed.  

Do you have a flatmate?  :D
my thoughts exactly.

op, could you please run 
```
netstat -ntlup
```so we can see if any network services are running? if not, then it is not likely a remote attack. could be malware but it doesn't sound right for a trojan. too interactive.

[WPA with TKIP is broken]("http://arstechnica.com/tech-policy/news/2009/08/one-minute-wifi-crack-puts-further-pressure-on-wpa.ars"). if you can, reconfigure for WPA2 aes only.

---

### Post by Irihapeti on 2011-06-09
Have you played with remote desktop? 

It's very easy to turn it on and forget that you have done so. You wouldn't the first person who's got into trouble this way.

---

### Post by tuebinger on 2011-06-10
> **doas777 said:**
> my thoughts exactly.

op, could you please run 
```
netstat -ntlup
```so we can see if any network services are running? if not, then it is not likely a remote attack. could be malware but it doesn't sound right for a trojan. too interactive.

[WPA with TKIP is broken]("http://arstechnica.com/tech-policy/news/2009/08/one-minute-wifi-crack-puts-further-pressure-on-wpa.ars"). if you can, reconfigure for WPA2 aes only.

I did this and it doesn't like any network services are running, but I'm not sure.  Is it safe to post this data here?

---

### Post by tuebinger on 2011-06-10
> **Thewhistlingwind said:**
> Check your log files, especially the networking stuff.

Do you use firewall?



How do I check my log files?  No, I wasn't using a firewall.  I am now.

---

### Post by tuebinger on 2011-06-10
> **hackertarget said:**
> Sometimes the most obvious can be missed.  

Do you have a flatmate?  :D

No, no flatmate!

---

### Post by tuebinger on 2011-06-10
> **Irihapeti said:**
> Have you played with remote desktop? 



No, I haven't played with remote desktop.

---

### Post by dFlyer on 2011-06-10
> **tuebinger said:**
> This afternoon I came home from work and found my computer was awake.  Also, the following programs were running:

-Cheese
-Screensaver Changer (and my screensaver was changed)
-Firefox

And two empty folders were created on my desktop.

All my files seem to be present, and there doesn't seem to be anything malicious that was done.

My question is: Was this a cyberattack?  And if so, how was it accomplished?  I have WPA-TSK (TKIP) security enabled on my router and a very long alphanumberic password.  I also have the usual password required to make any changes to the system and to wake up the computer from sleeping.

I'm perplexed.  I know these programs couldn't have opened themselves randomly, right?  If it was a cyberattack, how do I prevent it from happening again?   Should I change all my passwords?  Is there a way to find out how they got past my security?

I would appreciate anyone who knows about security and hacking giving me their thoughts on this.

Thanks!

My first question would be does anybody live with you that may have used your computer. I have 2 grandkids living with me and if I step away from the computer for a few minutes it's not unusual for thing like what you described to happen.

---

### Post by Rasa1111 on 2011-06-10
*If* you know for sure that no one was in your home..
then it (to me) actually does sound like someone was trying to activate your webcam to have a possible 'look around'.  It's happened. 

Usually though, an empty , un-named folder or two created on the desktop (in my experience) is usually the work of someone else in my home that has used my computer and are not quite sure what they are doing..
Happens often whenever i see my mother or my sister, and let them use my computer for a minute. lol

Whenever either of them are around, Im always deleting unnamed/empty folders from the desktop, and closing multiple programs that they seemed to open and had no use at all for. 

So, you positive no one at all was in your home?

---

### Post by tuebinger on 2011-06-10
> **Rasa1111 said:**
> *If* 

So, you positive no one at all was in your home?

Pretty sure.  My next door neighbor has a key for emergencies, but I doubt he would come over just to play around on my computer.

---

### Post by CVGH on 2011-06-11
```
cat /var/log/auth.log
``` 
See what/who has been logging in...

---

### Post by mr-woof on 2011-06-11
Do you have SSH installed on the netbook?

---

### Post by doas777 on 2011-06-12
> **tuebinger said:**
> I did this and it doesn't like any network services are running, but I'm not sure.  Is it safe to post this data here?

if you don't have any network services running, then you do not likely have an interactive hacker, unless they cleaned up after themselves. 

in the interest of a full dialog I'll mention that it is possible that an attacker could have planted a rootkit that is hiding a network backdoor, but I think it is probably unlikely. it is equally possible that you downloaded a script that is performing these unauthorized actions.

if you are behind a router, it is quite safe to post your netstat, but if you want, you can obscure your IP addresses. if you are not behind a router, it would make you slightly more vulnerable to anyone with both your IP and that info (if there are any accessible services). this is a little unlikely unless someone really wants you, and has enough info to ID you by forum name and IP.  your call. it may help, or it may not. if you feel confident in your reading of the output, don't worry about it.

if you do have a router, do you have upnp enabled on it?

---

### Post by pcarlos853 on 2011-06-13
Sorry to hear about that. IMO I would copy the HD to an external HD and reinstall the OS. Im not a Ubuntu guru, but reinstall the OS, secure it, and then look through the appropriate logs to determine what happened.

Carlos

---

### Post by tuebinger on 2011-06-14
> **CVGH said:**
> ```
cat /var/log/auth.log
``` 
See what/who has been logging in...

Thanks!  But this only goes back a couple of days.  Is there a way to get the login info on the day of the supposed attack (6 days ago)?

---

### Post by tuebinger on 2011-06-14
> **mr-woof said:**
> Do you have SSH installed on the netbook?

I think I do.

---

### Post by conradin on 2011-06-14
```
w
```
see who is doing what currently.
Get that firewall up and dont respond to any echo requests!

if you want older loging info I believe its auto archived.
```
ls /var/log/au*
```
should have what you're looking for. you may have to uncompress one of the older logs

---

### Post by tuebinger on 2011-06-14
> **doas777 said:**
> 

op, could you please run 
```
netstat -ntlup
```so we can see if any network services are running? 

Results are attached.

---

### Post by conradin on 2011-06-14
Alternatively..
do you have any scheduled tasks,
boot scripts,
roomates, siblings, 
or any other method to explain said behavior?
Is snort installed by chance?
is your password something someone could guess if they had a tiny bit of info about you?


Does the "cheese worm" have anything to do with the program cheese?
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

Also, look at your router logs. WPA takes a bit more to crack, basicaly it leaves a trace when someone cracks it. Now you could be suspicious your logs have been tampered with..

was the admin router setup accessible via the net and was its password something other than the default?

try using the service shields up! from grc.com 
and what were the folder names of the folders created?

---

### Post by doas777 on 2011-06-15
> **tuebinger said:**
> Results are attached.
I don't see anything serious, but I am curious why you have a ipv6-only apache instance. do you have an apache site running on the box, or any apps that use an http interface? if not, consider uninstalling apache. 

I'm not seeing any remote control process listening, so it doesn't look like service exploitation.

ps, you do not appear to have ssh listening, which is good.

---

