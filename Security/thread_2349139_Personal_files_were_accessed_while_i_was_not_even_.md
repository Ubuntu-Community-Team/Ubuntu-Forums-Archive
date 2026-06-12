---
title: "Personal files were accessed while i was not even at computer"
date: 2017-01-11
forum: Security
---

### Post by gjcu on 2017-01-11
I had a zip file containin personal files, i used ubuntu purely to import images and videos from camera and then zipped and tried to upload to Microsoft onedrive via dropping down the zip file to browser. I browsed internet a bit, and then left pc for like 30 hours.

When i got back, i noticed the upload was not succesful because for some reason "no permission to upload files to this folder". Now we get to the actual worrying part: **I noticed that while inspecting the properties of that zip file, that it was accessed a day later from its modification date and at a time I was not at pc at all.**

I already erased my ssd, but was it for nothing? Or was that really indication of malware?

---

### Post by Zebracomputers on 2017-01-11
Unfortunately, if you have erased the SSD, I assume that held the zip file, then there is no evidence to look at?  Or am I getting this wrong, and you erased something else besides the volume that held your data?

---

### Post by gjcu on 2017-01-11
I erased the whole thing. I just wonder if there would have been other explanations than malware.

---

### Post by TheFu on 2017-01-11
Welcome to the forums.

Wiping probably not needed.  Is the file different from the backup?  Being "accessed" is ambiguous.  There are many daemons running that scan file systems for new files.  full text search indexing, locate, updatedb for example.  On Unix systems, atime doesn't mean "mtime."  mtime is when bits were altered.  

If your system is patched, backed up, and you don't perform high risk operations like using a web browser with flash, java, or javascript enabled, then you have little for worry about.

Don't know anything about 1-drive, but I've had issues connecting to any Windows services using non-Windows systems. Perhaps that has changed? I dunno, haven't used any online anything from MSFT in many years. Just find I prefer to use other services.

---

### Post by gjcu on 2017-01-11
I didnt install anything on that ubuntu system, only downloaded system updates and then started to upload these images and videos after zipping them. Browsed internet on some known to be safe sites.

I did not have firewall enabled, because i had no idea it was disabled by default. Also i accidentally opened amazon from amazon button before any system updates were downloaded(amazon button is next to system icon), also at that time I did not have even noscript or adblock on firefox. So this might have exposed me to malware.

---

### Post by TheFu on 2017-01-11
> known to be safe sites.
No such thing.

Most firewalls only help if there are services running -i.e. listening for inbound connections. For a home or small business, most firewall open ports based on in-to-out requests.  Ubuntu doesn't enable a firewall by default, because it doesn't enable any daemons/listeners by default either.

I've never heard of amazon shipping bad images or javascript out.  OTOH, I have heard of multiple MSFT websites doing that - actually, some of my websites have been attacked by corporate MSFT IPs. At the time, I just figured those machines were hacked. Ended up blocking half of MSFTs corporate network - that was easier.

I really doubt anything bad happened.  Was the system behind a router running a firewall?

---

### Post by gjcu on 2017-01-11
I used modemrouter which had firewall

---

### Post by TheFu on 2017-01-11
You never said (or I missed it), was it access time or modified time?

---

### Post by gjcu on 2017-01-11
I did mentiin, it was roughly 24 hours later after modification time, which apparently was time of zip creation.

---

### Post by TheFu on 2017-01-11
Access time for files can be from anything running on the system.  There are lots of processes that scan file systems. 
[https://www.unixtutorial.org/2008/04/atime-ctime-mtime-in-unix-filesystems/](https://www.unixtutorial.org/2008/04/atime-ctime-mtime-in-unix-filesystems/)

---

### Post by gjcu on 2017-01-11
It would have to be some default ubuntu thing, i didnt install anything.

One troublesome thing also is that my Microsoft account was also succesfully logged in during time when I wasnt at pc, from the same ip as this linux pc.

---

### Post by TheFu on 2017-01-11
> **gjcu said:**
> It would have to be some default ubuntu thing, i didnt install anything.

One troublesome thing also is that my Microsoft account was also succesfully logged in during time when I wasnt at pc, from the same ip as this linux pc.

Did you have the system/browser store your login credentials?  It could have been required to provide the re-login by MSFT and didn't want to stop the upload.  But I honestly don't know.  I've never seen that behavior.  Is there a login password set for your system? Is there a screen lock setup?  Is that password used on any other systems?  How many devices do you have that could login to your MSFT account?  A phone? another PC?  A game console? A media player?

I don't know much about the "default" ubuntu stuff.  Haven't run a default Ubuntu in many years. I'm not a normal user.

---

### Post by gjcu on 2017-01-11
I didnt use that ms account anywhere during that time. I didnt store log in credentials on browser, and someone still needs to log in. Either it was malware, or system does some auto login during upload for some reason.

---

### Post by Habitual on 2017-01-12
> **gjcu said:**
> I didnt use that ms account anywhere during that time. I didnt store log in credentials on browser, and someone still needs to log in. Either it was malware, or system does some auto login during upload for some reason.

"from the same IP" sounds like the connection at the Microsoft Onedrive was left "ESTABLISHED" excessively before shutting down the connection.
You probably have no control over this except to reboot, or pull the internet plug.

---

### Post by gjcu on 2017-01-12
What does that mean?

---

### Post by Habitual on 2017-01-12
> **gjcu said:**
> What does that mean?

It means Microsoft kept the connection open for you.
The error message about "no permission" likely caused a cycle of retries.

My Best Guess.

---

### Post by gjcu on 2017-01-12
But why would it create another session for that? Also if it was like that, wouldnt it make more sense if there was multiple log in sessions as opposed to just one? The upload process took several hours before it encountered that permission issue, perhaps it even attempted to upload whole zip of 10gb(yes, my upload bandwith is really slow)

And by "one" i refer to session that happened while i was away. The session when i logged in for upload was previous session and it was like 36 hours later.

---

### Post by Habitual on 2017-01-12
I don't know. Sorry. 

I'm done here.

---

