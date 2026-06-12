---
title: "please help - need to send very big file quickly/easily"
date: 2007-08-12
forum: The Cafe
---

### Post by daverich on 2007-08-12
hi.

I've got to send a 350meg file to the states from england.

MSN is getting around 6kbs, IRc DCC connection wont work 'cos we're both relative newbies and both computers are running behind routers.

Is there nothing that can easily setup a connection between my linux box and my m8s windows box in america so I can beam him this file at a reasonable transfer rate?

I've looked at ftp server programs but tbh they're not user friendly enough for someone like me who just wants to send a file.

any suggestions?


Kind regards

Dave Rich

---

### Post by daverich on 2007-08-12
ok.

It seems AIM is the way to go.

I'm getting 44KBs out of that.

Kind regards

Dave Rich

---

### Post by Ultra Magnus on 2007-08-12
It might seem like overkill but When I had to send some files for my girlfriend I set up and ftp server with filezilla [http://filezilla.sourceforge.net/](http://filezilla.sourceforge.net/) - its quite straight forward and it'll be allot quicker than doing it through a chat thing

---

### Post by daverich on 2007-08-12
well the chat thing didn't work.

I think he's got anti-virus, firewall, router with firewall etc etc.

I'll try the filezilla thing .

Kind regards

Dave Rich

---

### Post by Old Pink on 2007-08-12
Quickly set up apache, host it in /var/www and have him [http://your.ip.address/file.extension](http://your.ip.address/file.extension) it out of your system. Pretty easily done.

---

### Post by daverich on 2007-08-12
ok.

I have that half-working.

My IP address is only bringing up my routers configuration page and the file doesn't exist at that address.

Any ideas?

It's a zyxel router.

Kind regards

Dave Rich

---

### Post by handy on 2007-08-12
This may help you:

[http://whatismyipaddress.com/](http://whatismyipaddress.com/)

---

### Post by daverich on 2007-08-12
no.,

I needed to setup port forwarding on the router.

Once that was done it's working very well

Apache is SOOO simple!

Great stuff. Thanks all.

Kind regards

Dave Rich

---

### Post by M$LOL on 2007-08-12
Why not just use megaupload?

---

### Post by handy on 2007-08-12
> **M$LOL said:**
> Why not just use megaupload?

I think they are spy ware.

---

### Post by ltk5 on 2007-08-12
better use[ in.solit.us]("http://in.solit.us"), they were quite nice hosting service :)

but for transferring between two PC-s?, I don't know :(

---

### Post by cdiem on 2007-08-12
You may want to try [qnext]("http://www.qnext.com/file_sharing.shtml"), it creates a p2web link.

---

### Post by M$LOL on 2007-08-12
> **handy said:**
> I think they are spy ware.

No they're not, but if you don't trust them then just use rapidshare or any of the other ones.

---

### Post by hartdg on 2007-08-12
> **daverich said:**
> no.,

I needed to setup port forwarding on the router.

Once that was done it's working very well

Apache is SOOO simple!

Great stuff. Thanks all.

Kind regards

Dave Rich

It sounds like your problem has been solved. I'll have to give Apache a try some time. 

For the record I've used Skype file transfer to sucessfully transfer a couple of 70MB  & 30MB files (available at [www.skype.com](www.skype.com)). Although it's primarily a voice over internet phone the software has it's roots in file sharing applications.

Downside - compared to Apache - is both users need the software installed (but installation is quite easy). You do also need to look out for problems with fire wall settings that can prevent a direct peer-to-peer (p2p) connection. 
With direct p2p connections the transfer will proceed at a rate close to your maximum bandwidth. If the connection is not direct p2p the transfer rate is really slow.

On the up-side, the Skype file transfer will survive one of the machines going off-line (or even being rebooted) and picks up the transfer where it left off when the connection is restored (as long as the transfer has not been cancelled).

Out of idle curiosity, how long did the 350MB transfer take?

Dave

---

### Post by Matt Yun on 2007-08-12
How about enabling your ssh server on your linux box, telling your American friend to download [puTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") or [SSH for Windows]("http://sshwindows.sourceforge.net/"), and have him/her transfer the file by **scp**?

---

### Post by handy on 2007-08-12
> **M$LOL said:**
> No they're not, but if you don't trust them then just use rapidshare or any of the other ones.

They look to be spy ware, by their [***_Privacy Policy_***]("http://www.megaupload.com/privacy/"), they make their money out of tracking where you go, so as to advertise to suit you the user as specifically as possible.  Your information is ***only*** given to associated companies!

---

### Post by M$LOL on 2007-08-13
That's not spyware.

---

