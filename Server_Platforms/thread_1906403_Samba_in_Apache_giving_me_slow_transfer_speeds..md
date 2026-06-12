---
title: "Samba in Apache giving me slow transfer speeds."
date: 2012-01-09
forum: Server Platforms
---

### Post by Johndo1 on 2012-01-09
I've had a fileserver running off of an old box I pieced togeather for a while now. I recently finished uploading at least a 100gb's worth of crap at around 300kb/s. Slow, but it got the job done, and it would even stream avi's out of the samba shares at a decent enough speed. 

I wanted to be able to access all of these files over the net, so I installed a LAMP setup and I basically just got Apache working. I've tested it over the internet, and it's working. The problem is, instead of getting the already slow 300kb/s, I'm barely getting around 30kb/s, and it freezes up even with that. Basically useless for anything besides a webpage. 

The samba shares are in the var/www directory, although I can still connect to them via the network folder on my ubuntu laptop. FTP, GUI network shares, and downloading them through [http://myip](http://myip) : port/files all garner the same speeds. 

Got any ideas?

---

### Post by elliotbeken on 2012-01-09
More information on the internet connection would be nice !

A common home bband connection will not be fast enough to stream an AVI movie.

---

### Post by Johndo1 on 2012-01-10
^ I don't mean stream them over the internet, I mean locally. I've done it before with no problems from a samba share, but now that the shares are located in apache everything is really slow. 

According to speedtest.net I'm getting 8.15 Mbps download and 2.99 Mbps upload. Not the fastest, but 30kb/s? Networking issues are generally hard to diognose, but I'll test and rule out anything you guys can guess at... I'm thinking apache has something to do with it due to the timing, though.

Also, streaming isn't really my main concern. Just ftping or sftping from the server is just as slow.


Edit again: 

Nope, nevermind. What happened was when I upload to the server I get 300KB/s, but when I download from it I get 30-50 KB/s. Weird. Any ideas on this?

---

