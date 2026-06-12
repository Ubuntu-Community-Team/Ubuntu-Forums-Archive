---
title: "Configuring Print/Scan Server"
date: 2011-06-13
forum: Server Platforms
---

### Post by zer010 on 2011-06-13
I recently installed Ubuntu 10.04.2 Server on a small desktop to use as a print server.  During installation I marked the sSH, Print, and Samba services.  I can ssh into it just fine and that's how I'm configuring it.  I have a hp Deskjet F2210 connected to it.
My end goal is to be able to use the scanner from my *buntu desktop and from a desktop running XP. All of these being connected via ethernet router. 
I've run 
```
sudo hp-setup -i
```
and that went ok. Testprint came out fine. 

Now I'm looking over how to get CUPS configured.  Looking [here]("https://help.ubuntu.com/10.04/serverguide/C/cups.html"), I don't really see much that needs to be done except for the "Listen" options.  Tell me if I'm correct in assuming that I can replace everything with
```
Port 631  # Listen on port 631 on all interfaces
```
I'm sure there's gotta be more to it, or that it's not the most secure way of doing it. I'm just a little stuck at this point.

---

### Post by cariboo on 2011-06-14
I can't help with your scanner problem, but it you configure cups to listen on all interfaces, that means that anyone can access the cups interface, even from the internet.

---

### Post by zer010 on 2011-06-14
Even though it's behind the router's firewall?  I will eventually open a port or two in my router's firewall for remote administering and such so I will need to know what is the best way to set it all up.  

Most of the documentation that I've found on configuring these services are pretty vague and the few How-Tos I've found are sorely outdated and all but forgotten.

---

### Post by zer010 on 2011-06-14
Ok, after some more searching I found one [COLOR=Red][how-to]("http://lifeonubuntu.com/setting-up-cups-and-installing-local-printer-in-ubuntu-server/")[/COLOR] that kind of meshes with another [COLOR=Red][how-to]("http://ubuntuforums.org/showthread.php?t=310450")[/COLOR] here on the forums.  I'll give it a whirl. I'd really like some advice as to whether there are any glaring issues with the first how-to.

---

### Post by zer010 on 2011-06-14
WooHoo! I'm glad to say that I was able to print my first test from my desktop to the networked printer successfully! :D d  

Now I need to get the scanner going and then get all of this to work with Windows....

---

### Post by demonipuch on 2011-06-14
Hi

Here is a howto share your scanner over a network : [https://help.ubuntu.com/community/ScanningHowTo#Sharing%20a%20Scanner%20Over%20a%20Network](https://help.ubuntu.com/community/ScanningHowTo#Sharing%20a%20Scanner%20Over%20a%20Network)

Here is another interesting link : [http://sanetwain.ozuzo.net/](http://sanetwain.ozuzo.net/)

Hope it helped

---

### Post by zer010 on 2011-06-14
Thanks for the links. I really appreciate it! 
As it's getting late/early, I'll check them out later. If I have any questions, I'll be sure to post back in this thread.

---

### Post by zer010 on 2011-06-14
Wow, I followed this [how-to]("https://help.ubuntu.com/community/ScanningHowTo#Sharing%20a%20Scanner%20Over%20a%20Network") and I ran into one issue with restarting inetd, which probably comes from the fact that it's not installed. The how-to does say that it doesn't actually need to be installed.  After going through all of the steps, I decided to try to scan something. Success!  The scanner was detected and I was able to scan a random piece of paper.  However, when I went to try it again, I couldn't detect the scanner again. I've tried restarting sane, rebooting the server, and restarting the scanner.  Insofar, I haven't been able to detect the scanner again. Talk about a bummer!

Could this be an issue of not having inetd installed?  Through looking in Synaptic, I've found that there are quite a few iterations of inetd. inetutils-inetd looks to be the general, all-around version.

---

### Post by bab1 on 2011-06-14
> **zer010 said:**
> Wow, I followed this [how-to]("https://help.ubuntu.com/community/ScanningHowTo#Sharing%20a%20Scanner%20Over%20a%20Network") and I ran into one issue with restarting inetd, which probably comes from the fact that it's not installed. The how-to does say that it doesn't actually need to be installed.  After going through all of the steps, I decided to try to scan something. Success!  The scanner was detected and I was able to scan a random piece of paper.  However, when I went to try it again, I couldn't detect the scanner again. I've tried restarting sane, rebooting the server, and restarting the scanner.  Insofar, I haven't been able to detect the scanner again. Talk about a bummer!

Could this be an issue of not having inetd installed?  Through looking in Synaptic, I've found that there are quite a few iterations of inetd. inetutils-inetd looks to be the general, all-around version.

Did you miss this? > Set (x)inetd

**Only needed for 10.04 and _*previous*_ distributions. You don't need this step if running 10.10, jump to step four.** 

---

### Post by zer010 on 2011-06-14
No, I didn't miss that. As my server is running 10.04, I included those instructions. Also, I don't have X installed so I didn't use xinetd.
I do appreciate your suggestion. Can't be too careful in rechecking everything! ^.^d

---

### Post by zer010 on 2011-06-14
I was about to post a large amount of stuff, but I just found something, and now it seems that my scanner issue is solved!
The solution can be found [here]("http://ubuntuforums.org/showthread.php?t=1519201&highlight=howto+scanner+network").  It seems that there needs to be a small change made on the client side. 

> [SIZE=3][COLOR=Sienna]Client-side setup:[/COLOR][/SIZE]

On each client computer you want to give access to the scanner, open the /etc/sane.d/net.conf with a text editor:```
 gksudo gedit /etc/sane.d/net.conf 
```> and add the ip-address or hostname to the end of the file.
it should look something like this:```
## saned hosts 
# Each line names a host to attach to. 
# If you list "localhost" then your backends can be accessed either 
# directly or through the net backend.  Going through the net backend 
# may be necessary to access devices that need special privileges. 
# localhost 
192.168.1.1 
```> You should now be able to access the scanner using Simple Scan, XSane, etc.Such a small change, but it has made all the difference!  Awesome! ^.^d

Now to get all of this working on XP....:\   

Since having the scanner networked to both *buntu AND Windows is my end goal, I'll just keep posting problems/progress in this thread until I have everything working.

Edit: I just realized that this info was at the bottom of the first how-to! #-oDOH!#-o

---

