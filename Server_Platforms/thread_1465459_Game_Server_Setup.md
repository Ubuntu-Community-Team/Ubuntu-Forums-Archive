---
title: "Game Server Setup"
date: 2010-04-29
forum: Server Platforms
---

### Post by www.com.au on 2010-04-29
Hey people, I've managed to get a server running on my home network with Ubuntu Home Edition.

I was following the step-by-step here: [http://www.urbanterror.info/docs/texts/123/](http://www.urbanterror.info/docs/texts/123/)
when I got to step 5 and it wouldn't download the file (authentication refused or something of the like). I'm not sure if i've missed a detail or what but a mirror or solution would be much appreciated.

My other question is if I do get that running how do I allow people to connect to the server? Like I said I can connect to the server within the network, I just don't know how to get others to join outside of my intranet. (Does it require a DNS setup?)

I am fairly inexperienced so I am still even learning the basic commands of server ed., but we all have to start somewhere right?

---

### Post by arrrghhh on 2010-04-29
Perhaps try downloading the file on your workstation, it appears to be an FTP so it may require authentication...  Which doesn't appear to be provided in that tut you're using.

Connections from the outside *can* be tricky - if your ISP doesn't block any of the traffic, it's not a big deal.  You need to open ports in two locations - the firewall within Ubuntu (which by default leaves all ports CLOSED) and the firewall on your router.  Just punch a hole thru for any IP address on a particular port, 80 if you're doing web traffic, 21 for FTP, etc.  You can use non-standard ports, however if you are setting up a website I wouldn't recommend straying from port 80 unless you want it to be semi-difficult to just "stumble" on...

---

### Post by www.com.au on 2010-04-29
Just like to say firstly, insta-reply thanks for that ;D

With the ftp authentication, I forgot to mention then when downloading in a browser in normal Ubuntu (seperate comp to server) it allowed me to download it.

So allowing people to connect to me is as easy as port forwarding? (Who knew gaming would ever come in useful)
What is the address likely to be? my IP followed by the routers IP on my network?

---

### Post by arrrghhh on 2010-04-29
Yes, really is as easy as forwarding a port.

Your ISP probably does dynamic addressing, so use a service like dyndns.org or the like, it'll update your IP automatically (just need a client running on your Linux box, I use ddclient.)

So if you can get the file on another machine, just copy it over to the server...?

---

### Post by www.com.au on 2010-04-29
Righto, I'll look into how to run them.

Yeah I have literally no idea how to do that.

I'll google that though, thanks for the help :D

---

### Post by www.com.au on 2010-04-29
This is actually proving more difficult then I originally had planned.
So I still need to buy a domain name online to have my server open to the web?

According to all I can find that's the only option.

---

### Post by mushroomblue on 2010-04-29
> **www.com.au said:**
> This is actually proving more difficult then I originally had planned.
So I still need to buy a domain name online to have my server open to the web?

According to all I can find that's the only option.

go to [http://www.dyndns.org]("http://www.dyndns.org"), and sign up for a free host. it'll be something like yourbox.ath.cx or something, but it'll point to your system, and should be sufficient for connecting people to your machine.

should you want to register a domain, the price is higher, but you could then just point the A and MX records to your IP address, should you have a static IP.

hope this helps.

---

### Post by arrrghhh on 2010-04-29
> **www.com.au said:**
> This is actually proving more difficult then I originally had planned.
So I still need to buy a domain name online to have my server open to the web?

According to all I can find that's the only option.

You *can* buy a domain name, it'll make it easier because you'll have more options as to what you name it...

BUT if you don't care what the domain name is, dyndns has a free service.  I use 'em, and I just got a domain "yourname.gotdns.com" - they have several to choose from, and you get to pick the first part but the last two pieces of the domain are relatively undesirable - but it's free.

---

### Post by www.com.au on 2010-04-30
I've got a new problem now, I get the message ".../ioUrTded.i386 permission denied" when trying to run start.sh, as mentioned in the link posted in my first post.

Anyone know anything about this?

---

### Post by ICEB3AR on 2010-04-30
That means that your user (from which you executed the command) is not allowed to execute the file which is called by start.sh. 
I'm pretty sure, that you have only typed in
```
sh start.sh
```
run this with administrator rights
```
sudo sh start.sh
```
or with the appropriate user (the user who is able to execute the files which are needed).

---

### Post by www.com.au on 2010-04-30
Still getting the permission access error.

I'm trying to add the Urban Terror user to the visudo root list at the moment but I can't even use the arrow keys in the editor.

---

### Post by arrrghhh on 2010-04-30
Yea, vi is a little difficult to use... there's a way to switch it to nano, that's what I did because I didn't want to take the time to learn vi :P

---

### Post by www.com.au on 2010-04-30
Yeah thing is it's screwing up in nano and vi.. nano it says "unknown command" when i move with the arrow keys and vi just goes nuts. Thinking I might have to completely reinstall teh server.

---

### Post by arrrghhh on 2010-04-30
> **www.com.au said:**
> Yeah thing is it's screwing up in nano and vi.. nano it says "unknown command" when i move with the arrow keys and vi just goes nuts. Thinking I might have to completely reinstall teh server.

No... don't do a complete reinstall.  You'll get back to this point and hit the same wall.  Vi is notoriously difficult to use for beginners (but has amazing potential if you dig into it).  Let me see if I can find that documentation that talked about changing visudo to nano...


```
EDITOR=/path/to/nano visudo
``` is the answer!

```
man visudo
``` also has the solution in the 2nd paragraph. ;)

> Just changing the symlink of the vi executable to nano will system default to nano. - from Arch forums.  Yet another solution, probably a more complete one at that.

---

